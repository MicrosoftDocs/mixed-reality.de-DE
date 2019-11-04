---
title: Mr und Azure 301-Sprachübersetzung
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie die Azure-Textübersetzungs-API in einer Mixed Reality-Anwendung implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Translator Text, hololens, immersive, VR
ms.openlocfilehash: 012eb5522c866e9e0f1caf5e4024305af07e298c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438529"
---
>[!NOTE]
><span data-ttu-id="f2ef0-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="f2ef0-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="f2ef0-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="f2ef0-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="f2ef0-108">Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="f2ef0-109">Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-301-language-translation"></a><span data-ttu-id="f2ef0-110">Mr und Azure 301: Sprachübersetzung</span><span class="sxs-lookup"><span data-stu-id="f2ef0-110">MR and Azure 301: Language translation</span></span>

<span data-ttu-id="f2ef0-111">In diesem Kurs erfahren Sie, wie Sie mithilfe von Azure Cognitive Services Übersetzungsfunktionen zu einer gemischten Reality-Anwendung hinzufügen, mit der Textübersetzungs-API.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-111">In this course, you will learn how to add translation capabilities to a mixed reality application using Azure Cognitive Services, with the Translator Text API.</span></span>

![Endgültiges Produkt](images/AzureLabs-Lab1-00.png)

<span data-ttu-id="f2ef0-113">Der Textübersetzungs-API ist ein Übersetzungsdienst, der nahezu in Echtzeit funktioniert.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-113">The Translator Text API is a translation Service which works in near real-time.</span></span> <span data-ttu-id="f2ef0-114">Der Dienst ist cloudbasiert, und mit einem Rest-API-Befehl kann eine APP die Übersetzungstechnologie für neuronale Computer verwenden, um Text in eine andere Sprache zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-114">The Service is cloud-based, and, using a REST API call, an app can make use of the neural machine translation technology to translate text to another language.</span></span> <span data-ttu-id="f2ef0-115">Weitere Informationen finden Sie auf der [Seite Azure Textübersetzungs-API](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span><span class="sxs-lookup"><span data-stu-id="f2ef0-115">For more information, visit the [Azure Translator Text API page](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span></span>

<span data-ttu-id="f2ef0-116">Nach Abschluss dieses Kurses verfügen Sie über eine Mixed Reality-Anwendung, die Folgendes ausführen kann:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-116">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1.  <span data-ttu-id="f2ef0-117">Der Benutzer spricht in ein Mikrofon, das mit einem immersiven (VR)-Headset (oder dem integrierten Mikrofon von hololens) verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-117">The user will speak into a microphone connected to an immersive (VR) headset (or the built-in microphone of HoloLens).</span></span>
2.  <span data-ttu-id="f2ef0-118">Die APP erfasst die Diktat und sendet Sie an den Azure-Textübersetzungs-API.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-118">The app will capture the dictation and send it to the Azure Translator Text API.</span></span>
3.  <span data-ttu-id="f2ef0-119">Das Übersetzungsergebnis wird in einer einfachen Benutzeroberflächen Gruppe in der Unity-Szene angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-119">The translation result will be displayed in a simple UI group in the Unity Scene.</span></span>

<span data-ttu-id="f2ef0-120">In diesem Kurs erfahren Sie, wie Sie die Ergebnisse des Konvertierungs Dienstanbieter in einer Unity-basierten Beispielanwendung erhalten.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-120">This course will teach you how to get the results from the Translator Service into a Unity-based sample application.</span></span> <span data-ttu-id="f2ef0-121">Sie müssen diese Konzepte auf eine benutzerdefinierte Anwendung anwenden, die Sie möglicherweise aufbauen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-121">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="f2ef0-122">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="f2ef0-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="f2ef0-123">Natürlich</span><span class="sxs-lookup"><span data-stu-id="f2ef0-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="f2ef0-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f2ef0-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f2ef0-125"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="f2ef0-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="f2ef0-126">Mr und Azure 301: Sprachübersetzung</span><span class="sxs-lookup"><span data-stu-id="f2ef0-126">MR and Azure 301: Language translation</span></span></td><td style="text-align: center;"> <span data-ttu-id="f2ef0-127">✔️</span><span class="sxs-lookup"><span data-stu-id="f2ef0-127">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="f2ef0-128">✔️</span><span class="sxs-lookup"><span data-stu-id="f2ef0-128">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="f2ef0-129">Dieser Kurs konzentriert sich in erster Linie auf Windows Mixed Reality immersive (VR)-Headsets, aber Sie können auch das, was Sie in diesem Kurs lernen, auf Microsoft hololens anwenden.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-129">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="f2ef0-130">Wenn Sie den Kurs befolgen, finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise zur Unterstützung von hololens verwenden müssen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-130">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="f2ef0-131">Wenn Sie hololens verwenden, bemerken Sie möglicherweise bei der sprach Erfassung einen Echo.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-131">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f2ef0-132">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="f2ef0-132">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="f2ef0-133">Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-133">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="f2ef0-134">Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Mai 2018).</span><span class="sxs-lookup"><span data-stu-id="f2ef0-134">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="f2ef0-135">Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](install-the-tools.md) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-135">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="f2ef0-136">Für diesen Kurs empfehlen wir die folgende Hardware und Software:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-136">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="f2ef0-137">Einen Entwicklungs-PC, der [mit der Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for Immersive (VR)-Headset-Entwicklung kompatibel ist</span><span class="sxs-lookup"><span data-stu-id="f2ef0-137">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="f2ef0-138">Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="f2ef0-138">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f2ef0-139">Das neueste Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="f2ef0-139">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f2ef0-140">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="f2ef0-140">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f2ef0-141">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="f2ef0-141">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="f2ef0-142">Ein [Windows Mixed Reality-Headset (VR)](immersive-headset-hardware-details.md) oder [Microsoft hololens](hololens-hardware-details.md) mit aktiviertem Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="f2ef0-142">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="f2ef0-143">Eine Reihe von Kopfhörern mit einem integrierten Mikrofon (wenn das Headset nicht über eine integrierte Mic-und-Sprech Anwendung verfügt)</span><span class="sxs-lookup"><span data-stu-id="f2ef0-143">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="f2ef0-144">Internet Zugang für das Einrichten und Übersetzen von Azure</span><span class="sxs-lookup"><span data-stu-id="f2ef0-144">Internet access for Azure setup and translation retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="f2ef0-145">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="f2ef0-145">Before you start</span></span>

- <span data-ttu-id="f2ef0-146">Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).</span><span class="sxs-lookup"><span data-stu-id="f2ef0-146">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="f2ef0-147">Der Code in diesem Tutorial ermöglicht es Ihnen, vom Standard Mikrofon Gerät, das mit Ihrem PC verbunden ist, aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-147">The code in this tutorial will allow you to record from the default microphone device connected to your PC.</span></span> <span data-ttu-id="f2ef0-148">Stellen Sie sicher, dass das standardmäßige Mikrofon-Gerät auf das Gerät festgelegt ist, das Sie zum Erfassen Ihrer Stimme verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-148">Make sure the default microphone device is set to the device you plan to use to capture your voice.</span></span>
- <span data-ttu-id="f2ef0-149">Um dem PC das Schreiben von Diktat zu gestatten, wechseln Sie zu **Einstellungen > Datenschutz > Sprache, & eingeben,** und klicken Sie auf die Schaltfläche **Sprachdienste aktivieren und Vorschläge eingeben**.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-149">To allow your PC to enable dictation, go to **Settings > Privacy > Speech, inking & typing** and select the button **Turn On speech services and typing suggestions**.</span></span>
- <span data-ttu-id="f2ef0-150">Wenn Sie ein Mikrofon und Kopfhörer verwenden, die mit dem Headset verbunden sind (bzw. in das Sie integriert sind), stellen Sie sicher, dass die Option "Wenn ich mein Headset trage, zu Headset mic wechseln" in den **Einstellungen > Gemischte Realität > Audio-und sprachsprache**aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-150">If you're using a microphone and headphones connected to (or built-in to) your headset, make sure the option “When I wear my headset, switch to headset mic” is turned on in **Settings > Mixed reality > Audio and speech**.</span></span>

   ![Mixed Reality-Einstellungen](images/AzureLabs-Lab1-00-5.png)

   ![Mikrofon-Einstellung](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> <span data-ttu-id="f2ef0-153">Beachten Sie, dass bei der Entwicklung für ein immersives Headset für dieses Lab Geräte Probleme bei der Audioausgabe auftreten können.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-153">Be aware that if you are developing for an immersive headset for this lab, you may experience audio output device issues.</span></span> <span data-ttu-id="f2ef0-154">Dies liegt an einem Problem mit Unity, das in höheren Versionen von Unity (Unity 2018,2) behoben wird.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-154">This is due to an issue with Unity, which is fixed in later versions of Unity (Unity 2018.2).</span></span> <span data-ttu-id="f2ef0-155">Das Problem verhindert, dass Unity das standardmäßige Audioausgabegerät zur Laufzeit ändert.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-155">The issue prevents Unity from changing the default audio output device at run time.</span></span> <span data-ttu-id="f2ef0-156">Stellen Sie sicher, dass Sie die oben genannten Schritte abgeschlossen haben, und schließen Sie den Editor, und öffnen Sie ihn erneut, wenn sich dieses Problem selbst darstellt.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-156">As a work around, ensure you have completed the above steps, and close and re-open the Editor, when this issue presents itself.</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="f2ef0-157">Kapitel 1 – Azure-Portal</span><span class="sxs-lookup"><span data-stu-id="f2ef0-157">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="f2ef0-158">Um die Azure Translator-API zu verwenden, müssen Sie eine Instanz des-Dienstanbieter konfigurieren, die für die Anwendung verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-158">To use the Azure Translator API, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="f2ef0-159">Melden Sie sich beim [Azure-Portal](https://portal.azure.com)an.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-159">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="f2ef0-160">Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="f2ef0-161">Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="f2ef0-162">Wenn Sie angemeldet sind, klicken Sie in der oberen linken Ecke auf " **neu** ", und suchen Sie nach "Textübersetzungs-API".</span><span class="sxs-lookup"><span data-stu-id="f2ef0-162">Once you are logged in, click on **New** in the top left corner and search for "Translator Text API."</span></span> <span data-ttu-id="f2ef0-163">**Drücken Sie Eingabe**Taste.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-163">Select **Enter**.</span></span>

    ![Neue Ressource](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > <span data-ttu-id="f2ef0-165">Das Wort **New** wurde möglicherweise durch **Create a Resource**in neueren Portalen ersetzt.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-165">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="f2ef0-166">Auf der neuen Seite wird eine Beschreibung des *Textübersetzungs-API* Dienstanbieter bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-166">The new page will provide a description of the *Translator Text API* Service.</span></span> <span data-ttu-id="f2ef0-167">Klicken Sie unten links auf dieser Seite auf die Schaltfläche **Erstellen** , um eine Verknüpfung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-167">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Erstellen Textübersetzungs-API Dienstanbieter](images/AzureLabs-Lab1-03.png)

4.  <span data-ttu-id="f2ef0-169">Nachdem Sie auf **Erstellen**geklickt haben, klicken Sie auf:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-169">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="f2ef0-170">Fügen Sie den gewünschten **Namen** für diese Dienst Instanz ein.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-170">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="f2ef0-171">Wählen Sie ein entsprechendes **Abonnement**aus.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-171">Select an appropriate **Subscription**.</span></span>
    3. <span data-ttu-id="f2ef0-172">Wählen Sie den für **Sie geeigneten Tarif** aus. Wenn Sie zum ersten Mal einen *Textübersetzung Dienst*erstellen, sollte Ihnen ein Free-Tarif (mit dem Namen "F0") zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-172">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Translator Text Service*, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="f2ef0-173">Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** .</span><span class="sxs-lookup"><span data-stu-id="f2ef0-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="f2ef0-174">Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="f2ef0-175">Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Labs) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="f2ef0-176">Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="f2ef0-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="f2ef0-177">Bestimmen Sie den **Speicherort** für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen).</span><span class="sxs-lookup"><span data-stu-id="f2ef0-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="f2ef0-178">Der Speicherort wäre idealerweise in der Region, in der die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="f2ef0-179">Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="f2ef0-180">Außerdem müssen Sie bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="f2ef0-181">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-181">Select **Create**.</span></span>

        ![Wählen Sie die Schaltfläche erstellen.](images/AzureLabs-Lab1-04.png)

5.  <span data-ttu-id="f2ef0-183">Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-183">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="f2ef0-184">Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-184">A notification will appear in the portal once the Service instance is created.</span></span> 

    ![Benachrichtigung zur Azure-Dienst Erstellung](images/AzureLabs-Lab1-05.png)

7.  <span data-ttu-id="f2ef0-186">Klicken Sie auf die Benachrichtigung, um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-186">Click on the notification to explore your new Service instance.</span></span> 

    ![Wechseln Sie zum ressourcenpopup.](images/AzureLabs-Lab1-06.png)

8.  <span data-ttu-id="f2ef0-188">Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="f2ef0-189">Sie gelangen zu ihrer neuen Textübersetzungs-API Dienst Instanz.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-189">You will be taken to your new Translator Text API Service instance.</span></span> 

    ![Textübersetzungs-API Dienst Seite](images/AzureLabs-Lab1-07.png)

9.  <span data-ttu-id="f2ef0-191">In diesem Lernprogramm muss Ihre Anwendung Aufrufe an Ihren Dienst durchführen. Dies erfolgt über den Abonnement Schlüssel Ihres dienstanzschlüssels.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-191">Within this tutorial, your application will need to make calls to your Service, which is done through using your Service’s Subscription Key.</span></span> 
10. <span data-ttu-id="f2ef0-192">Navigieren Sie auf der Seite *Schnellstart* Ihres *Textübersetzung* Diensts zum ersten Schritt, rufen *Sie Ihre Schlüssel*ab, und klicken Sie auf **Schlüssel** (Sie können dies auch erreichen, indem Sie auf die blauen Hyperlink-Schlüssel im Navigationsmenü Dienste klicken. gekennzeichnet durch das Schlüsselsymbol).</span><span class="sxs-lookup"><span data-stu-id="f2ef0-192">From the *Quick start* page of your *Translator Text* Service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the Services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="f2ef0-193">Dadurch werden die Dienst *Schlüssel*angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-193">This will reveal your Service *Keys*.</span></span>
11. <span data-ttu-id="f2ef0-194">Erstellen Sie eine Kopie von einem der angezeigten Schlüssel, da Sie dies später in Ihrem Projekt benötigen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="f2ef0-195">Kapitel 2 – Einrichten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="f2ef0-195">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="f2ef0-196">Richten Sie Ihr immersives Headset mit gemischter Realität ein und testen Sie es.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-196">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="f2ef0-197">Für diesen Kurs benötigen Sie keine Bewegungs Controller.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-197">You will not need motion controllers for this course.</span></span> <span data-ttu-id="f2ef0-198">Wenn Sie Unterstützung bei der Einrichtung eines immersiven Headsets benötigen, führen Sie [die folgenden Schritte](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)aus.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-198">If you need support setting up an immersive headset, please [follow these steps](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

<span data-ttu-id="f2ef0-199">Folgendes ist ein typisches Setup für die Entwicklung mit gemischter Realität und eine gute Vorlage für andere Projekte:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-199">The following is a typical set up for developing with mixed reality and, as such, is a good template for other projects:</span></span>

1.  <span data-ttu-id="f2ef0-200">Öffnen Sie *Unity* , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-200">Open *Unity* and click **New**.</span></span> 

    ![Starten Sie ein neues Unity-Projekt.](images/AzureLabs-Lab1-08.png)

2.  <span data-ttu-id="f2ef0-202">Sie müssen nun einen Unity-Projektnamen angeben.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="f2ef0-203">Fügen Sie **MR_Translation**ein.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-203">Insert **MR_Translation**.</span></span> <span data-ttu-id="f2ef0-204">Stellen Sie sicher, dass Projekttyp auf **3D**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="f2ef0-205">Legen Sie den Speicherort auf einen geeigneten *Speicherort* fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind).</span><span class="sxs-lookup"><span data-stu-id="f2ef0-205">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="f2ef0-206">Klicken Sie dann auf **Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-206">Then, click **Create project**.</span></span>

    ![Geben Sie Details für ein neues Unity-Projekt an.](images/AzureLabs-Lab1-09.png)

3.  <span data-ttu-id="f2ef0-208">Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="f2ef0-209">Wechseln Sie zu **Edit > Preferences (Einstellungen bearbeiten** ), und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="f2ef0-210">Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="f2ef0-211">Schließen Sie das Fenster " **Einstellungen** ".</span><span class="sxs-lookup"><span data-stu-id="f2ef0-211">Close the **Preferences** window.</span></span>

    ![Skript-Editor-Einstellung aktualisieren.](images/AzureLabs-Lab1-10.png)

4.  <span data-ttu-id="f2ef0-213">Navigieren Sie als nächstes zu **Datei > Buildeinstellungen** , und schalten Sie die Plattform auf **universelle Windows-Plattform**, indem Sie auf die Schaltfläche **Plattform wechseln** klicken.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-213">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Fenster "Buildeinstellungen", Plattform zu UWP wechseln.](images/AzureLabs-Lab1-11.png)

5.  <span data-ttu-id="f2ef0-215">Wechseln Sie zu **Datei > Build-Einstellungen** , und stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-215">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="f2ef0-216">Das **Zielgerät** ist auf **ein beliebiges Gerät**festgelegt.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-216">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="f2ef0-217">Legen Sie für Microsoft hololens das **Zielgerät** auf *hololens*fest.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-217">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="f2ef0-218">Der **Buildtyp** ist auf **D3D** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="f2ef0-219">**SDK** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="f2ef0-220">**Visual Studio-Version** ist auf **neueste installierte** Version festgelegt.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="f2ef0-221">**Build und Run** sind auf **lokaler Computer** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="f2ef0-222">Speichern Sie die Szene, und fügen Sie Sie dem Build hinzu.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="f2ef0-223">Wählen Sie hierzu die Option **geöffnete Szenen hinzufügen**aus.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="f2ef0-224">Ein Fenster zum Speichern wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-224">A save window will appear.</span></span>

            ![Klicken Sie auf Schaltfläche "Open Szenen](images/AzureLabs-Lab1-12.png)

        2. <span data-ttu-id="f2ef0-226">Erstellen Sie einen neuen Ordner für dieses und jede zukünftige Szene, und wählen Sie dann die Schaltfläche **neuer Ordner** aus, um einen neuen Ordner zu **erstellen.**</span><span class="sxs-lookup"><span data-stu-id="f2ef0-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Neuen Ordner "Skripts" erstellen](images/AzureLabs-Lab1-13.png)

        3. <span data-ttu-id="f2ef0-228">Öffnen Sie den neu erstellten Ordner **Szenen** , geben Sie im Feld *Dateiname*: Text **MR_TranslationScene**ein, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_TranslationScene**, then press **Save**.</span></span>

            ![Benennen Sie neue Szene.](images/AzureLabs-Lab1-14.png)

            > <span data-ttu-id="f2ef0-230">Beachten Sie, dass Sie Ihre Unity-Szenen im Ordner " *Assets* " speichern müssen, da Sie dem Unity-Projekt zugeordnet werden müssen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="f2ef0-231">Das Erstellen eines Szenen Ordners (und anderer ähnlicher Ordner) ist eine typische Methode zum Strukturieren eines Unity-Projekts.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="f2ef0-232">Die restlichen Einstellungen in den *Buildeinstellungen*sollten vorerst als Standard belassen werden.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="f2ef0-233">Klicken Sie im Fenster *Buildeinstellungen* auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der *Inspektor* befindet.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Öffnen Sie die Player-Einstellungen.](images/AzureLabs-Lab1-15.png)

7. <span data-ttu-id="f2ef0-235">In diesem Bereich müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="f2ef0-236">Auf der Registerkarte **andere Einstellungen** :</span><span class="sxs-lookup"><span data-stu-id="f2ef0-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="f2ef0-237">Die **Lauf Zeit Version der Skript** Erstellung muss **stabil** sein (.NET 3,5-Entsprechung).</span><span class="sxs-lookup"><span data-stu-id="f2ef0-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="f2ef0-238">**Skript** -Back-End sollte **.net** sein</span><span class="sxs-lookup"><span data-stu-id="f2ef0-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="f2ef0-239">**API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten</span><span class="sxs-lookup"><span data-stu-id="f2ef0-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Aktualisieren Sie andere Einstellungen.](images/AzureLabs-Lab1-16.png)
      
    2. <span data-ttu-id="f2ef0-241">Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="f2ef0-242">**Internet Client deklarieren**</span><span class="sxs-lookup"><span data-stu-id="f2ef0-242">**InternetClient**</span></span>
        2. <span data-ttu-id="f2ef0-243">**Tritt**</span><span class="sxs-lookup"><span data-stu-id="f2ef0-243">**Microphone**</span></span>

            ![Veröffentlichungs Einstellungen werden aktualisiert.](images/AzureLabs-Lab1-17.png)

    3. <span data-ttu-id="f2ef0-245">Weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), **unterstützt Tick Virtual Reality**, stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Aktualisieren Sie die X R-Einstellungen.](images/AzureLabs-Lab1-18.png)

8.  <span data-ttu-id="f2ef0-247">Wieder in den **Buildeinstellungen**ist *Unity C# -Projekte* nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen neben this.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-247">Back in **Build Settings**, *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="f2ef0-248">Schließen Sie das Fenster mit den Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="f2ef0-249">Speichern Sie Ihre Szene und Ihr Projekt (**Datei > Speichern Sie Szenen/Dateien > Speichern**Sie das Projekt).</span><span class="sxs-lookup"><span data-stu-id="f2ef0-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="f2ef0-250">Kapitel 3 – Hauptkamera Einrichtung</span><span class="sxs-lookup"><span data-stu-id="f2ef0-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f2ef0-251">Wenn Sie die *Unity-Setup* Komponente dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie [dieses. unitypackage herunterladen](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), es als [*benutzerdefiniertes Paket*](https://docs.unity3d.com/Manual/AssetPackages.html)in Ihr Projekt importieren und dann aus [Kapitel 5](#chapter-5--create-the-results-class)fortfahren.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), import it into your project as a [*Custom Package*](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-results-class).</span></span> <span data-ttu-id="f2ef0-252">Sie müssen dennoch ein Unity-Projekt erstellen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-252">You will still need to create a Unity Project.</span></span>

1.  <span data-ttu-id="f2ef0-253">Im *Hierarchie Panel*finden Sie ein Objekt mit dem Namen " **Main Camera**". dieses Objekt stellt den "Head"-Punkt dar, sobald Sie die Anwendung "in" haben.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-253">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your “head” point of view once you are “inside” your application.</span></span>
2.  <span data-ttu-id="f2ef0-254">Wählen Sie mit dem Unity-Dashboard vor Ihnen das **Hauptkamera-gameobject**aus.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-254">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="f2ef0-255">Sie werden feststellen, dass im *Inspektor-Panel* (in der Regel auf der rechten Seite im Dashboard) die verschiedenen Komponenten dieses *gameobject*angezeigt werden, mit der *Transformation* am oberen Rand, gefolgt von der *Kamera*und einigen anderen Komponenten.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-255">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="f2ef0-256">Sie müssen die Transformation der Hauptkamera zurücksetzen, damit Sie ordnungsgemäß positioniert ist.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-256">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>
3.  <span data-ttu-id="f2ef0-257">Wählen Sie dazu das **Zahnrad** Symbol neben der *Transformations* Komponente der Kamera aus, und wählen Sie **Zurücksetzen**aus.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-257">To do this, select the **Gear** icon next to the Camera’s *Transform* component, and selecting **Reset**.</span></span> 

    ![Setzen Sie die Hauptkamera Transformation zurück.](images/AzureLabs-Lab1-19.png)
 
4.  <span data-ttu-id="f2ef0-259">Die *Transformations* Komponente sollte dann wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-259">The *Transform* component should then look like:</span></span>

    1. <span data-ttu-id="f2ef0-260">Die *Position* ist auf **0, 0, 0** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-260">The *Position* is set to **0, 0, 0**</span></span>
    2. <span data-ttu-id="f2ef0-261">*Drehung* ist auf **0, 0, 0** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-261">*Rotation* is set to **0, 0, 0**</span></span>
    3. <span data-ttu-id="f2ef0-262">Und die *Skala* ist auf **1, 1, 1** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-262">And *Scale* is set to **1, 1, 1**</span></span>

        ![Transformations Informationen für Kamera](images/AzureLabs-Lab1-20.png)

5.  <span data-ttu-id="f2ef0-264">Wenn das **Hauptkamera** Objekt ausgewählt ist, sehen Sie sich die Schaltfläche **Komponente hinzufügen** am unteren Rand des *inspektorbereichs*an.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-264">Next, with the **Main Camera** object selected, see the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span> 
6.  <span data-ttu-id="f2ef0-265">Wählen Sie diese Schaltfläche aus, und suchen Sie (entweder geben Sie *Audioquelle* in das Suchfeld ein, oder navigieren Sie in den Abschnitten) für die Komponente namens **Audioquelle** , wie unten dargestellt, und wählen Sie Sie aus.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-265">Select that button, and search (by either typing *Audio Source* into the search field or navigating the sections) for the component called **Audio Source** as shown below and select it (pressing enter on it also works).</span></span>
7.  <span data-ttu-id="f2ef0-266">Der **Hauptkamera**wird eine *audioquellkomponente* hinzugefügt, wie unten gezeigt.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-266">An *Audio Source* component will be added to the **Main Camera**, as demonstrated below.</span></span>

    ![Fügen Sie eine audioquellkomponente hinzu.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > <span data-ttu-id="f2ef0-268">Für Microsoft hololens müssen Sie auch die folgenden ändern, die Teil der **Kamera** Komponente auf der **Hauptkamera**sind:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-268">For Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component on your **Main Camera**:</span></span>
    > - <span data-ttu-id="f2ef0-269">**Flags löschen:** Voll Tonfarbe.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-269">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="f2ef0-270">**Hintergrund** ' Black, Alpha 0 ' – hexadezimal Farbe: #00000000.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-270">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

## <a name="chapter-4--setup-debug-canvas"></a><span data-ttu-id="f2ef0-271">Kapitel 4 – Setup-Debug-Canvas</span><span class="sxs-lookup"><span data-stu-id="f2ef0-271">Chapter 4 – Setup Debug Canvas</span></span>

<span data-ttu-id="f2ef0-272">Zum Anzeigen der Eingabe und der Ausgabe der Übersetzung muss eine grundlegende Benutzeroberfläche erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-272">To show the input and output of the translation, a basic UI needs to be created.</span></span> <span data-ttu-id="f2ef0-273">Für diesen Kurs erstellen Sie ein Canvas-UI-Objekt mit mehreren ' Text '-Objekten, um die Daten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-273">For this course, you will create a Canvas UI object, with several ‘Text’ objects to show the data.</span></span>

1.  <span data-ttu-id="f2ef0-274">Klicken Sie mit der rechten Maustaste auf einen leeren Bereich des Bereichs *Hierarchie*, und fügen Sie unter **Benutzeroberfläche**eine **Canvas**hinzu.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-274">Right-click in an empty area of the *Hierarchy Panel*, under **UI**, add a **Canvas**.</span></span>

    ![Hinzufügen eines neuen Canvas-UI-Objekts.](images/AzureLabs-Lab1-22.png)

2.  <span data-ttu-id="f2ef0-276">Wenn Sie das Canvas-Objekt ausgewählt haben, ändern Sie im *Inspektor-Panel* (innerhalb der Canvas-Komponente) den **Rendermodus** in den **Raum**.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-276">With the Canvas object selected, in the *Inspector Panel* (within the ‘Canvas’ component), change **Render Mode** to **World Space**.</span></span> 
3.  <span data-ttu-id="f2ef0-277">Im nächsten Schritt ändern Sie die folgenden Parameter in der *Rect-Transformation des inspektorpanels*:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-277">Next, change the following parameters in the *Inspector Panel’s Rect Transform*:</span></span>

    1. <span data-ttu-id="f2ef0-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span><span class="sxs-lookup"><span data-stu-id="f2ef0-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span></span>
    2. <span data-ttu-id="f2ef0-279">*Breite* -500</span><span class="sxs-lookup"><span data-stu-id="f2ef0-279">*Width* -    500</span></span>
    3. <span data-ttu-id="f2ef0-280">*Höhe* -300</span><span class="sxs-lookup"><span data-stu-id="f2ef0-280">*Height* -   300</span></span>
    4. <span data-ttu-id="f2ef0-281">*Skalieren* - **X** 0,13 **Y** 0,13 **Z** 0,13</span><span class="sxs-lookup"><span data-stu-id="f2ef0-281">*Scale* - **X** 0.13 **Y** 0.13  **Z** 0.13</span></span>

        ![Aktualisieren Sie die Rect-Transformation für den Zeichenbereich.](images/AzureLabs-Lab1-23.png)
 
4.  <span data-ttu-id="f2ef0-283">Klicken Sie **mit der rechten** Maustaste auf den Zeichenbereich im *Hierarchie Panel*unter **UI**, und fügen Sie ein **Panel**hinzu.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-283">Right click on the **Canvas** in the *Hierarchy Panel*, under **UI**, and add a **Panel**.</span></span> <span data-ttu-id="f2ef0-284">Dieser **Bereich** bietet einen Hintergrund für den Text, den Sie in der Szene anzeigen werden.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-284">This **Panel** will provide a background to the text that you will be displaying in the scene.</span></span>
5.  <span data-ttu-id="f2ef0-285">Klicken Sie im *Hierarchie Panel*mit der rechten Maustaste **auf den Bereich** **, und**fügen Sie ein **Text Objekt**hinzu.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-285">Right click on the **Panel** in the *Hierarchy Panel*, under **UI**, and add a **Text object**.</span></span> <span data-ttu-id="f2ef0-286">Wiederholen Sie den gleichen Prozess, bis Sie insgesamt vier UI-Textobjekte erstellt haben (Hinweis: Wenn Sie das erste "Text"-Objekt ausgewählt haben, können Sie einfach **"Strg +** d" drücken, um es zu duplizieren, bis vier vorhanden sind).</span><span class="sxs-lookup"><span data-stu-id="f2ef0-286">Repeat the same process until you have created four UI Text objects in total (Hint: if you have the first ‘Text’ object selected, you can simply press **‘Ctrl’ + ‘D’**, to duplicate it, until you have four in total).</span></span> 
6.  <span data-ttu-id="f2ef0-287">Wählen Sie für jedes **Text Objekt**die Option aus, und verwenden Sie die folgenden Tabellen, um die Parameter im *Inspektor-Panel*festzulegen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-287">For each **Text Object**, select it and use the below tables to set the parameters in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="f2ef0-288">Für die Komponente *Rect Transform* :</span><span class="sxs-lookup"><span data-stu-id="f2ef0-288">For the *Rect Transform* component:</span></span>

        | <span data-ttu-id="f2ef0-289">Name</span><span class="sxs-lookup"><span data-stu-id="f2ef0-289">Name</span></span>                   | <span data-ttu-id="f2ef0-290">Transformation- *Position*</span><span class="sxs-lookup"><span data-stu-id="f2ef0-290">Transform - *Position*</span></span>             | <span data-ttu-id="f2ef0-291">Breite</span><span class="sxs-lookup"><span data-stu-id="f2ef0-291">Width</span></span>      | <span data-ttu-id="f2ef0-292">Flugh</span><span class="sxs-lookup"><span data-stu-id="f2ef0-292">Height</span></span>    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | <span data-ttu-id="f2ef0-293">"Mikrophonestatus Label"</span><span class="sxs-lookup"><span data-stu-id="f2ef0-293">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="f2ef0-294">**X** -80 **Y** 90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="f2ef0-294">**X** -80 **Y** 90 **Z** 0</span></span>         | <span data-ttu-id="f2ef0-295">300</span><span class="sxs-lookup"><span data-stu-id="f2ef0-295">300</span></span>        | <span data-ttu-id="f2ef0-296">30</span><span class="sxs-lookup"><span data-stu-id="f2ef0-296">30</span></span>        |
        | <span data-ttu-id="f2ef0-297">Azureresponselabel</span><span class="sxs-lookup"><span data-stu-id="f2ef0-297">AzureResponseLabel</span></span>     | <span data-ttu-id="f2ef0-298">**X** -80 **Y** 30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="f2ef0-298">**X** -80 **Y** 30 **Z** 0</span></span>         | <span data-ttu-id="f2ef0-299">300</span><span class="sxs-lookup"><span data-stu-id="f2ef0-299">300</span></span>        | <span data-ttu-id="f2ef0-300">30</span><span class="sxs-lookup"><span data-stu-id="f2ef0-300">30</span></span>        |
        | <span data-ttu-id="f2ef0-301">"Ditationlabel"</span><span class="sxs-lookup"><span data-stu-id="f2ef0-301">DictationLabel</span></span>         | <span data-ttu-id="f2ef0-302">**X** -80 **Y** -30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="f2ef0-302">**X** -80 **Y** -30 **Z** 0</span></span>        | <span data-ttu-id="f2ef0-303">300</span><span class="sxs-lookup"><span data-stu-id="f2ef0-303">300</span></span>        | <span data-ttu-id="f2ef0-304">30</span><span class="sxs-lookup"><span data-stu-id="f2ef0-304">30</span></span>        |
        | <span data-ttu-id="f2ef0-305">Translationresultlabel</span><span class="sxs-lookup"><span data-stu-id="f2ef0-305">TranslationResultLabel</span></span> | <span data-ttu-id="f2ef0-306">**X** -80 **Y** -90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="f2ef0-306">**X** -80 **Y** -90 **Z** 0</span></span>        | <span data-ttu-id="f2ef0-307">300</span><span class="sxs-lookup"><span data-stu-id="f2ef0-307">300</span></span>        | <span data-ttu-id="f2ef0-308">30</span><span class="sxs-lookup"><span data-stu-id="f2ef0-308">30</span></span>        |


    2. <span data-ttu-id="f2ef0-309">Für die **Text-Komponente (Skript)** :</span><span class="sxs-lookup"><span data-stu-id="f2ef0-309">For the **Text (Script)** component:</span></span>


        | <span data-ttu-id="f2ef0-310">Name</span><span class="sxs-lookup"><span data-stu-id="f2ef0-310">Name</span></span>                   | <span data-ttu-id="f2ef0-311">Text</span><span class="sxs-lookup"><span data-stu-id="f2ef0-311">Text</span></span>               | <span data-ttu-id="f2ef0-312">Schrift Grad</span><span class="sxs-lookup"><span data-stu-id="f2ef0-312">Font Size</span></span>    |
        |:----------------------:|:------------------:|:------------:|
        | <span data-ttu-id="f2ef0-313">"Mikrophonestatus Label"</span><span class="sxs-lookup"><span data-stu-id="f2ef0-313">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="f2ef0-314">Mikrofon Status:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-314">Microphone Status:</span></span> | <span data-ttu-id="f2ef0-315">20</span><span class="sxs-lookup"><span data-stu-id="f2ef0-315">20</span></span>           |
        | <span data-ttu-id="f2ef0-316">Azureresponselabel</span><span class="sxs-lookup"><span data-stu-id="f2ef0-316">AzureResponseLabel</span></span>     | <span data-ttu-id="f2ef0-317">Azure-Webantwort</span><span class="sxs-lookup"><span data-stu-id="f2ef0-317">Azure Web Response</span></span> | <span data-ttu-id="f2ef0-318">20</span><span class="sxs-lookup"><span data-stu-id="f2ef0-318">20</span></span>           |
        | <span data-ttu-id="f2ef0-319">"Ditationlabel"</span><span class="sxs-lookup"><span data-stu-id="f2ef0-319">DictationLabel</span></span>         |   <span data-ttu-id="f2ef0-320">Sie haben soeben Folgendes gesagt:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-320">You just said:</span></span>   | <span data-ttu-id="f2ef0-321">20</span><span class="sxs-lookup"><span data-stu-id="f2ef0-321">20</span></span>           |
        | <span data-ttu-id="f2ef0-322">Translationresultlabel</span><span class="sxs-lookup"><span data-stu-id="f2ef0-322">TranslationResultLabel</span></span> |    <span data-ttu-id="f2ef0-323">Übersetzt</span><span class="sxs-lookup"><span data-stu-id="f2ef0-323">Translation:</span></span>    | <span data-ttu-id="f2ef0-324">20</span><span class="sxs-lookup"><span data-stu-id="f2ef0-324">20</span></span>           |

        ![Geben Sie die entsprechenden Werte für die Benutzeroberflächen Bezeichnungen ein.](images/AzureLabs-Lab1-24.png)

    3. <span data-ttu-id="f2ef0-326">Legen Sie außerdem den Schrift Schnitt auf **Fett**formatiert.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-326">Also, make the Font Style **Bold**.</span></span> <span data-ttu-id="f2ef0-327">Dadurch wird der Text leichter lesbar.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-327">This will make the text easier to read.</span></span>

        ![Fett Schrift.](images/AzureLabs-Lab1-25.png)

7.  <span data-ttu-id="f2ef0-329">Erstellen Sie für jedes *UI-Textobjekt* , das in [Kapitel 5](#chapter-5--create-the-results-class)erstellt wurde, *ein neues unter* geordnetes UI- **Textobjekt**.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-329">For each *UI Text object* created in [Chapter 5](#chapter-5--create-the-results-class), create a new *child* **UI Text object**.</span></span> <span data-ttu-id="f2ef0-330">Diese untergeordneten Elemente zeigen die Ausgabe der Anwendung an.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-330">These children will display the output of the application.</span></span> <span data-ttu-id="f2ef0-331">Erstellen *Sie* untergeordnete Objekte, indem Sie mit der rechten Maustaste auf das gewünschte übergeordnete Element klicken (z. b. " *mikrophonestatus Label*"), **und wählen Sie**dann **Benutzeroberfläche**</span><span class="sxs-lookup"><span data-stu-id="f2ef0-331">Create *child* objects through right-clicking your intended parent (e.g. *MicrophoneStatusLabel*) and then select **UI** and then select **Text**.</span></span>
8.  <span data-ttu-id="f2ef0-332">Wählen Sie für jedes dieser untergeordneten Elemente die Option aus, und verwenden Sie die folgenden Tabellen, um die Parameter im Inspektor-Panel festzulegen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-332">For each of these children, select it and use the below tables to set the parameters in the Inspector Panel.</span></span>

    1. <span data-ttu-id="f2ef0-333">Für die Komponente **Rect Transform** :</span><span class="sxs-lookup"><span data-stu-id="f2ef0-333">For the **Rect Transform** component:</span></span>

        | <span data-ttu-id="f2ef0-334">Name</span><span class="sxs-lookup"><span data-stu-id="f2ef0-334">Name</span></span>                  | <span data-ttu-id="f2ef0-335">Transformation- *Position*</span><span class="sxs-lookup"><span data-stu-id="f2ef0-335">Transform - *Position*</span></span> | <span data-ttu-id="f2ef0-336">Breite</span><span class="sxs-lookup"><span data-stu-id="f2ef0-336">Width</span></span>      | <span data-ttu-id="f2ef0-337">Flugh</span><span class="sxs-lookup"><span data-stu-id="f2ef0-337">Height</span></span>    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | <span data-ttu-id="f2ef0-338">"Mikrophonestatustext"</span><span class="sxs-lookup"><span data-stu-id="f2ef0-338">MicrophoneStatusText</span></span>  | <span data-ttu-id="f2ef0-339">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="f2ef0-339">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="f2ef0-340">300</span><span class="sxs-lookup"><span data-stu-id="f2ef0-340">300</span></span>        | <span data-ttu-id="f2ef0-341">30</span><span class="sxs-lookup"><span data-stu-id="f2ef0-341">30</span></span>        |
        | <span data-ttu-id="f2ef0-342">Azureresponabtext</span><span class="sxs-lookup"><span data-stu-id="f2ef0-342">AzureResponseText</span></span>     | <span data-ttu-id="f2ef0-343">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="f2ef0-343">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="f2ef0-344">300</span><span class="sxs-lookup"><span data-stu-id="f2ef0-344">300</span></span>        | <span data-ttu-id="f2ef0-345">30</span><span class="sxs-lookup"><span data-stu-id="f2ef0-345">30</span></span>        |
        | <span data-ttu-id="f2ef0-346">"Ditationtext"</span><span class="sxs-lookup"><span data-stu-id="f2ef0-346">DictationText</span></span>         | <span data-ttu-id="f2ef0-347">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="f2ef0-347">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="f2ef0-348">300</span><span class="sxs-lookup"><span data-stu-id="f2ef0-348">300</span></span>        | <span data-ttu-id="f2ef0-349">30</span><span class="sxs-lookup"><span data-stu-id="f2ef0-349">30</span></span>        |
        | <span data-ttu-id="f2ef0-350">Translationresulttext</span><span class="sxs-lookup"><span data-stu-id="f2ef0-350">TranslationResultText</span></span> | <span data-ttu-id="f2ef0-351">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="f2ef0-351">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="f2ef0-352">300</span><span class="sxs-lookup"><span data-stu-id="f2ef0-352">300</span></span>        | <span data-ttu-id="f2ef0-353">30</span><span class="sxs-lookup"><span data-stu-id="f2ef0-353">30</span></span>        |

    2. <span data-ttu-id="f2ef0-354">Für die **Text-Komponente (Skript)** :</span><span class="sxs-lookup"><span data-stu-id="f2ef0-354">For the **Text (Script)** component:</span></span>

        | <span data-ttu-id="f2ef0-355">Name</span><span class="sxs-lookup"><span data-stu-id="f2ef0-355">Name</span></span>                  | <span data-ttu-id="f2ef0-356">Text</span><span class="sxs-lookup"><span data-stu-id="f2ef0-356">Text</span></span>          | <span data-ttu-id="f2ef0-357">Schrift Grad</span><span class="sxs-lookup"><span data-stu-id="f2ef0-357">Font Size</span></span>    |
        |:---------------------:|:-------------:|:------------:|
        | <span data-ttu-id="f2ef0-358">"Mikrophonestatustext"</span><span class="sxs-lookup"><span data-stu-id="f2ef0-358">MicrophoneStatusText</span></span>  |      <span data-ttu-id="f2ef0-359">??</span><span class="sxs-lookup"><span data-stu-id="f2ef0-359">??</span></span>       | <span data-ttu-id="f2ef0-360">20</span><span class="sxs-lookup"><span data-stu-id="f2ef0-360">20</span></span>           |
        | <span data-ttu-id="f2ef0-361">Azureresponabtext</span><span class="sxs-lookup"><span data-stu-id="f2ef0-361">AzureResponseText</span></span>     |      <span data-ttu-id="f2ef0-362">??</span><span class="sxs-lookup"><span data-stu-id="f2ef0-362">??</span></span>       | <span data-ttu-id="f2ef0-363">20</span><span class="sxs-lookup"><span data-stu-id="f2ef0-363">20</span></span>           |
        | <span data-ttu-id="f2ef0-364">"Ditationtext"</span><span class="sxs-lookup"><span data-stu-id="f2ef0-364">DictationText</span></span>         |      <span data-ttu-id="f2ef0-365">??</span><span class="sxs-lookup"><span data-stu-id="f2ef0-365">??</span></span>       | <span data-ttu-id="f2ef0-366">20</span><span class="sxs-lookup"><span data-stu-id="f2ef0-366">20</span></span>           |
        | <span data-ttu-id="f2ef0-367">Translationresulttext</span><span class="sxs-lookup"><span data-stu-id="f2ef0-367">TranslationResultText</span></span> |      <span data-ttu-id="f2ef0-368">??</span><span class="sxs-lookup"><span data-stu-id="f2ef0-368">??</span></span>       | <span data-ttu-id="f2ef0-369">20</span><span class="sxs-lookup"><span data-stu-id="f2ef0-369">20</span></span>           |

9. <span data-ttu-id="f2ef0-370">Wählen Sie als nächstes die Option "Center" für jede Textkomponente aus:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-370">Next, select the 'centre' alignment option for each text component:</span></span>

    ![Text ausrichten.](images/AzureLabs-Lab1-26.png)

10. <span data-ttu-id="f2ef0-372">Um sicherzustellen, dass die Text Objekte der untergeordneten **Benutzeroberfläche** leicht lesbar sind, ändern Sie Ihre *Farbe*.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-372">To ensure the **child UI Text** objects are easily readable, change their *Color*.</span></span> <span data-ttu-id="f2ef0-373">Klicken Sie hierzu auf die Leiste neben *Farbe*(derzeit "schwarz").</span><span class="sxs-lookup"><span data-stu-id="f2ef0-373">Do this by clicking on the bar (currently ‘Black’) next to *Color*.</span></span> 

    ![Geben Sie entsprechende Werte für die Textausgaben der Benutzeroberfläche ein.](images/AzureLabs-Lab1-27.png)
 
11. <span data-ttu-id="f2ef0-375">Ändern Sie dann im neuen, kleinen *Farb* Fenster die hexadezimale *Farbe* in: **0032eaff**</span><span class="sxs-lookup"><span data-stu-id="f2ef0-375">Then, in the new, little, *Color* window, change the *Hex Color* to: **0032EAFF**</span></span>

    ![Aktualisieren Sie Farbe in blau.](images/AzureLabs-Lab1-28.png)
 
12. <span data-ttu-id="f2ef0-377">Im folgenden sehen Sie, wie die **Benutzeroberfläche** aussehen sollte.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-377">Below is how the **UI** should look.</span></span>
    1.  <span data-ttu-id="f2ef0-378">Im *Hierarchie Panel*:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-378">In the *Hierarchy Panel*:</span></span>

        ![Hierarchie in der bereitgestellten-Struktur.](images/AzureLabs-Lab1-29.png)

    2.  <span data-ttu-id="f2ef0-380">In den *Szenen* -und *Spiel Ansichten*:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-380">In the *Scene* and *Game Views*:</span></span>

        ![Die Szenen-und Spiel Ansichten in derselben Struktur haben.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a><span data-ttu-id="f2ef0-382">Kapitel 5 – Erstellen der Ergebnis Klasse</span><span class="sxs-lookup"><span data-stu-id="f2ef0-382">Chapter 5 – Create the Results class</span></span>

<span data-ttu-id="f2ef0-383">Das erste Skript, das Sie erstellen müssen, ist die *Ergebnis* Klasse, die für die Bereitstellung einer Möglichkeit zum Anzeigen der Ergebnisse der Übersetzung verantwortlich ist.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-383">The first script you need to create is the *Results* class, which is responsible for providing a way to see the results of translation.</span></span> <span data-ttu-id="f2ef0-384">Die-Klasse speichert und zeigt Folgendes an:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-384">The Class stores and displays the following:</span></span> 

- <span data-ttu-id="f2ef0-385">Das Antwort Ergebnis von Azure.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-385">The response result from Azure.</span></span>
- <span data-ttu-id="f2ef0-386">Der Status des Mikrofons.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-386">The microphone status.</span></span> 
- <span data-ttu-id="f2ef0-387">Das Ergebnis der diktierung (Voice-to-Text).</span><span class="sxs-lookup"><span data-stu-id="f2ef0-387">The result of the dictation (voice to text).</span></span>
- <span data-ttu-id="f2ef0-388">Das Ergebnis der Übersetzung.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-388">The result of the translation.</span></span>

<span data-ttu-id="f2ef0-389">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-389">To create this class:</span></span> 

1.  <span data-ttu-id="f2ef0-390">Klicken Sie mit der rechten Maustaste im *Projekt Panel*, und erstellen Sie dann **> Ordner**.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-390">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="f2ef0-391">Benennen Sie den Ordner mit **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-391">Name the folder **Scripts**.</span></span> 
 
    ![Erstellen Sie den Ordner Skripts.](images/AzureLabs-Lab1-31.png)

    ![Öffnen Sie den Ordner Skripts.](images/AzureLabs-Lab1-32.png)
 
2.  <span data-ttu-id="f2ef0-394">Wenn Sie den Ordner **Skripts** erstellen, doppelklicken Sie darauf, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-394">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="f2ef0-395">Klicken Sie dann in diesem Ordner mit der rechten Maustaste auf, und wählen **C#** Sie dann **> Skript erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-395">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="f2ef0-396">Benennen Sie die *Ergebnisse*des Skripts.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-396">Name the script *Results*.</span></span> 

    ![Erstellen Sie das erste Skript.](images/AzureLabs-Lab1-33.png)
 
3.  <span data-ttu-id="f2ef0-398">Doppelklicken Sie auf das neue *Ergebnis* Skript, um es in **Visual Studio**zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-398">Double click on the new *Results* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="f2ef0-399">Fügen Sie die folgenden Namespaces ein:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-399">Insert the following namespaces:</span></span>

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  <span data-ttu-id="f2ef0-400">Fügen Sie in der-Klasse die folgenden Variablen ein:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-400">Inside the Class insert the following variables:</span></span>

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  <span data-ttu-id="f2ef0-401">Fügen Sie dann die *Awa()* -Methode hinzu, die aufgerufen wird, wenn die-Klasse initialisiert wird.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-401">Then add the *Awake()* method, which will be called when the class initializes.</span></span> 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  <span data-ttu-id="f2ef0-402">Fügen Sie abschließend die Methoden hinzu, die für die Ausgabe der verschiedenen Ergebnisinformationen an die Benutzeroberfläche verantwortlich sind.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-402">Finally, add the methods which are responsible for outputting the various results information to the UI.</span></span> 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  <span data-ttu-id="f2ef0-403">Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-403">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-6--create-the-microphonemanager-class"></a><span data-ttu-id="f2ef0-404">Kapitel 6 – Erstellen der Klasse " *mikrophonemanager* "</span><span class="sxs-lookup"><span data-stu-id="f2ef0-404">Chapter 6 – Create the *MicrophoneManager* class</span></span>

<span data-ttu-id="f2ef0-405">Die zweite Klasse, die Sie erstellen, ist der *Mikro phonemanager*.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-405">The second class you are going to create is the *MicrophoneManager*.</span></span>

<span data-ttu-id="f2ef0-406">Diese Klasse ist für Folgendes zuständig:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-406">This class is responsible for:</span></span>

- <span data-ttu-id="f2ef0-407">Erkennen des Aufzeichnungs Geräts, das an das Headset oder den Computer angeschlossen ist (je nachdem, welches der Standard ist).</span><span class="sxs-lookup"><span data-stu-id="f2ef0-407">Detecting the recording device attached to the headset or machine (whichever is the default).</span></span>
- <span data-ttu-id="f2ef0-408">Erfassen Sie das Audiomaterial (Voice), und speichern Sie es als Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-408">Capture the audio (voice) and use dictation to store it as a string.</span></span>
- <span data-ttu-id="f2ef0-409">Nachdem die Stimme angehalten wurde, übermitteln Sie die Diktat an die Translator-Klasse.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-409">Once the voice has paused, submit the dictation to the Translator class.</span></span>
- <span data-ttu-id="f2ef0-410">Hosten Sie eine Methode, die die sprach Erfassung bei Bedarf abbrechen kann.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-410">Host a method that can stop the voice capture if desired.</span></span>

<span data-ttu-id="f2ef0-411">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-411">To create this class:</span></span> 
1.  <span data-ttu-id="f2ef0-412">Doppelklicken Sie auf den Ordner " **Scripts** ", um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-412">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="f2ef0-413">Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf  **C# > Skript erstellen**.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="f2ef0-414">Nennen Sie das Skript " *mikrophonemanager*".</span><span class="sxs-lookup"><span data-stu-id="f2ef0-414">Name the script *MicrophoneManager*.</span></span> 
3.  <span data-ttu-id="f2ef0-415">Doppelklicken Sie auf das neue Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-415">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="f2ef0-416">Aktualisieren Sie die Namespaces, sodass Sie am Anfang der Klasse " *mikrophonemanager* " dem folgenden entsprechen:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-416">Update the namespaces to be the same as the following, at the top of the *MicrophoneManager* class:</span></span>

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="f2ef0-417">Fügen Sie dann die folgenden Variablen in der Klasse " *mikrophonemanager* " hinzu:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-417">Then, add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  <span data-ttu-id="f2ef0-418">Der Code für die Methoden " *Awake ()* " und " *Start ()* " muss nun hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-418">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="f2ef0-419">Diese werden aufgerufen, wenn die-Klasse initialisiert:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-419">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  <span data-ttu-id="f2ef0-420">Sie können die *Update ()* -Methode *Löschen* , da Sie von dieser Klasse nicht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-420">You can *delete* the *Update()* method since this class will not use it.</span></span>
8.  <span data-ttu-id="f2ef0-421">Nun benötigen Sie die Methoden, die die APP verwendet, um die sprach Erfassung zu starten und anzuhalten, und Sie *an die* konvertiererklasse weiterzuleiten, die Sie bald erstellen werden.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-421">Now you need the methods that the App uses to start and stop the voice capture, and pass it to the *Translator* class, that you will build soon.</span></span> <span data-ttu-id="f2ef0-422">Kopieren Sie den folgenden Code, und fügen Sie ihn unterhalb der Methode " *Start ()* " ein.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-422">Copy the following code and paste it beneath the *Start()* method.</span></span>

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > <span data-ttu-id="f2ef0-423">Obwohl diese Anwendung diese Anwendung nicht nutzt, wurde auch die *stopcapturingaudio()* -Methode bereitgestellt, wenn Sie die Möglichkeit zum Beenden der Erfassung von Audiodaten in Ihrer Anwendung implementieren möchten.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-423">Though this application will not make use of it, the *StopCapturingAudio()* method has also been provided here, should you want to implement the ability to stop capturing audio in your application.</span></span>

9.  <span data-ttu-id="f2ef0-424">Nun müssen Sie einen Diktat Handler hinzufügen, der aufgerufen wird, wenn die Stimme angehalten wird.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-424">You now need to add a Dictation Handler that will be invoked when the voice stops.</span></span> <span data-ttu-id="f2ef0-425">Diese Methode übergibt dann den vorgeschriebenen Text an die *Translator* -Klasse.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-425">This method will then pass the dictated text to the *Translator* class.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. <span data-ttu-id="f2ef0-426">Stellen Sie sicher, dass Sie die Änderungen in Visual Studio speichern, bevor Sie zu Unity zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-426">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

> [!WARNING]  
> <span data-ttu-id="f2ef0-427">An dieser Stelle bemerken Sie einen Fehler, der im Konsolen Panel des *Unity-Editors* angezeigt wird ("der Name ' Translator ' ist nicht vorhanden...").</span><span class="sxs-lookup"><span data-stu-id="f2ef0-427">At this point you will notice an error appearing in the *Unity Editor Console* Panel (“The name ‘Translator’ does not exist...”).</span></span> <span data-ttu-id="f2ef0-428">Der Grund hierfür ist, dass der Code auf die *Translator* -Klasse verweist, die Sie im nächsten Kapitel erstellen werden.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-428">This is because the code references the *Translator* class, which you will create in the next chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-translator-service"></a><span data-ttu-id="f2ef0-429">Kapitel 7 – Anrufen von Azure und Translator-Dienst</span><span class="sxs-lookup"><span data-stu-id="f2ef0-429">Chapter 7 – Call to Azure and translator service</span></span>

<span data-ttu-id="f2ef0-430">Das letzte Skript, das Sie erstellen müssen, ist die *Translator* -Klasse.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-430">The last script you need to create is the *Translator* class.</span></span> 

<span data-ttu-id="f2ef0-431">Diese Klasse ist für Folgendes zuständig:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-431">This class is responsible for:</span></span>

-   <span data-ttu-id="f2ef0-432">Authentifizieren der APP mit *Azure*in Exchange für ein Authentifizierungs **Token**.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-432">Authenticating the App with *Azure*, in exchange for an **Auth Token**.</span></span>
-   <span data-ttu-id="f2ef0-433">Verwenden Sie das **auth-Token** , um Text (der von der Klasse " *mikrophonemanager* " empfangen wird) zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-433">Use the **Auth Token** to submit text (received from the *MicrophoneManager* Class) to be translated.</span></span>
-   <span data-ttu-id="f2ef0-434">Empfangen Sie das übersetzte Ergebnis, und übergeben Sie es an die *Ergebnis* Klasse, um Sie in der Benutzeroberfläche zu visualisieren.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-434">Receive the translated result and pass it to the *Results* Class to be visualized in the UI.</span></span>

<span data-ttu-id="f2ef0-435">So erstellen Sie diese Klasse:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-435">To create this Class:</span></span> 
1.  <span data-ttu-id="f2ef0-436">Wechseln Sie zum Ordner " **Scripts** ", den Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-436">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="f2ef0-437">Klicken Sie im **Projekt Panel**mit der rechten Maustaste, und **Erstellen Sie > C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-437">Right-click in the **Project Panel**, **Create > C# Script**.</span></span> <span data-ttu-id="f2ef0-438">Ruft *den Skript*Konvertierer auf.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-438">Call the script *Translator*.</span></span>
3.  <span data-ttu-id="f2ef0-439">Doppelklicken Sie auf das *neue* Konvertierungs Skript, um es in **Visual Studio**zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-439">Double click on the new *Translator* script to open it **with Visual Studio**.</span></span>
4.  <span data-ttu-id="f2ef0-440">Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-440">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="f2ef0-441">Fügen Sie dann die folgenden Variablen in die *Translator* -Klasse ein:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-441">Then add the following variables inside the *Translator* class:</span></span>

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - <span data-ttu-id="f2ef0-442">Die Sprachen, die in die Sprachen-Aufzählung **eingefügt werden,** sind nur Beispiele.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-442">The languages inserted into the languages **enum** are just examples.</span></span> <span data-ttu-id="f2ef0-443">Wenn Sie möchten, können Sie weitere hinzufügen. die [API unterstützt mehr als 60 Sprachen](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (einschließlich Klingonischer Sprache).</span><span class="sxs-lookup"><span data-stu-id="f2ef0-443">Feel free to add more if you wish; the [API supports over 60 languages](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (including Klingon)!</span></span>
    > - <span data-ttu-id="f2ef0-444">Es gibt eine [interaktive Seite, die die verfügbaren Sprachen abdeckt](https://www.microsoft.com/translator/business/languages/), aber beachten Sie, dass die Seite nur dann funktioniert, wenn die Website Sprache auf "" festgelegt ist (und die Microsoft-Website wahrscheinlich an Ihre native Sprache umgeleitet wird).</span><span class="sxs-lookup"><span data-stu-id="f2ef0-444">There is a [more interactive page covering available languages](https://www.microsoft.com/translator/business/languages/), though be aware the page only appears to work when the site language is set to '' (and the Microsoft site will likely redirect to your native language).</span></span> <span data-ttu-id="f2ef0-445">Sie können die Website Sprache am unteren Rand der Seite oder durch Ändern der URL ändern.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-445">You can change site language at the bottom of the page or by altering the URL.</span></span>
    > - <span data-ttu-id="f2ef0-446">Der **authorizationkey** -Wert im obigen Code Ausschnitt muss der **Schlüssel** sein, den Sie erhalten haben, als Sie das *Azure-Textübersetzungs-API*abonniert haben.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-446">The **authorizationKey** value, in the above code snippet, must be the **Key**  you received when you subscribed to the *Azure Translator Text API*.</span></span> <span data-ttu-id="f2ef0-447">Dies wurde in [Kapitel 1](#chapter-1--the-azure-portal)beschrieben.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-447">This was covered in [Chapter 1](#chapter-1--the-azure-portal).</span></span>

6.  <span data-ttu-id="f2ef0-448">Der Code für die Methoden " *Awake ()* " und " *Start ()* " muss nun hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-448">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> 
7.  <span data-ttu-id="f2ef0-449">In diesem Fall ruft der Code *Azure* mithilfe des Autorisierungs Schlüssels auf, um ein *Token*abzurufen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-449">In this case, the code will make a call to *Azure* using the authorization Key, to get a *Token*.</span></span>

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > <span data-ttu-id="f2ef0-450">Das Token läuft nach 10 Minuten ab.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-450">The token will expire after 10 minutes.</span></span> <span data-ttu-id="f2ef0-451">Abhängig vom Szenario für Ihre APP müssen Sie möglicherweise den gleichen Coroutine-Rückruf mehrmals durchführen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-451">Depending on the scenario for your app, you might have to make the same coroutine call multiple times.</span></span>

8.  <span data-ttu-id="f2ef0-452">Die Coroutine zum Abrufen des Tokens lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-452">The coroutine to obtain the Token is the following:</span></span>

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > <span data-ttu-id="f2ef0-453">Wenn Sie den Namen der IEnumerator-Methode **getdekencoroutine ()** bearbeiten, müssen Sie die " *startcoroutine* "-und " *stopcoroutine* "-aufrufzeichenfolgen-Werte im obigen Code aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-453">If you edit the name of the IEnumerator method **GetTokenCoroutine()**, you need to update the *StartCoroutine* and *StopCoroutine* call string values in the above code.</span></span> <span data-ttu-id="f2ef0-454">Um eine bestimmte *Coroutine*zu verhindern, müssen Sie gemäß der [Unity-Dokumentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html)die Zeichen folgen Wert-Methode verwenden.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-454">[As per Unity documentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), to Stop a specific *Coroutine*, you need to use the string value method.</span></span>

9.  <span data-ttu-id="f2ef0-455">Fügen Sie als nächstes das Coroutine-Objekt (mit einer "Support"-streammethode direkt unterhalb) hinzu, um die Übersetzung des von der Klasse " *mikrophonemanager* " empfangenen Texts zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-455">Next, add the coroutine (with a “support” stream method right below it) to obtain the translation of the text received by the *MicrophoneManager* class.</span></span> <span data-ttu-id="f2ef0-456">Dieser Code erstellt eine Abfrage Zeichenfolge, die an den *Azure-Textübersetzungs-API*gesendet werden soll, und verwendet dann die interne Unity unitywebrequest-Klasse, um einen get-Befehl mit der Abfrage Zeichenfolge an den Endpunkt zu senden.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-456">This code creates a query string to send to the *Azure Translator Text API*, and then uses the internal Unity UnityWebRequest class to make a ‘Get’ call to the endpoint with the query string.</span></span> <span data-ttu-id="f2ef0-457">Das Ergebnis wird dann verwendet, um die Übersetzung im results-Objekt festzulegen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-457">The result is then used to set the translation in your Results object.</span></span> <span data-ttu-id="f2ef0-458">Der folgende Code zeigt die-Implementierung:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-458">The code below shows the implementation:</span></span>

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. <span data-ttu-id="f2ef0-459">Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-459">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--configure-the-unity-scene"></a><span data-ttu-id="f2ef0-460">Kapitel 8 – Konfigurieren der Unity-Szene</span><span class="sxs-lookup"><span data-stu-id="f2ef0-460">Chapter 8 – Configure the Unity Scene</span></span>

1.  <span data-ttu-id="f2ef0-461">Klicken Sie im Unity-Editor auf die *Ergebnis* Klasse, und ziehen Sie Sie *aus* dem Ordner **Scripts** auf das **Hauptkamera** Objekt im Bereich *Hierarchie*.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-461">Back in the Unity Editor, click and drag the *Results* class *from* the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="f2ef0-462">Klicken Sie auf die **Hauptkamera** , und sehen Sie sich den Bereich *Inspector*an.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-462">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="f2ef0-463">Sie werden feststellen, dass in der neu hinzugefügten *Skript* Komponente vier Felder mit leeren Werten vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-463">You will notice that within the newly added *Script* component, there are four fields with empty values.</span></span> <span data-ttu-id="f2ef0-464">Dies sind die Ausgabe Verweise auf die Eigenschaften im Code.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-464">These are the output references to the properties in the code.</span></span> 
3.  <span data-ttu-id="f2ef0-465">Ziehen Sie die entsprechenden **Text** Objekte aus dem Bereich *Hierarchie* in diese vier Slots, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-465">Drag the appropriate **Text** objects from the *Hierarchy Panel* to those four slots, as shown in the image below.</span></span>

    ![Aktualisieren Sie die Ziel Verweise mit den angegebenen Werten.](images/AzureLabs-Lab1-34.png)
  
4.  <span data-ttu-id="f2ef0-467">Klicken und ziehen Sie anschließend die *Translator* -Klasse aus dem Ordner **Scripts** auf das **Hauptkamera** Objekt im Bereich *Hierarchie*.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-467">Next, click and drag the *Translator* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
5.  <span data-ttu-id="f2ef0-468">Klicken und ziehen Sie dann die Klasse " *mikrophonemanager* " aus dem Ordner " **Scripts** " auf das **Hauptkamera** Objekt im *Hierarchie Panel*.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-468">Then, click and drag the *MicrophoneManager* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
6.  <span data-ttu-id="f2ef0-469">Klicken Sie abschließend auf die **Hauptkamera** , und sehen Sie sich den Bereich *Inspector*an.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-469">Lastly, click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="f2ef0-470">Sie werden feststellen, dass Sie in dem von ihnen gezogenen Skript zwei Dropdown Felder haben, die es Ihnen ermöglichen, die Sprachen festzulegen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-470">You will notice that in the script you dragged on, there are two drop down boxes that will allow you to set the languages.</span></span>
 
    ![Stellen Sie sicher, dass die beabsichtigten Übersetzungs Sprachen eingegeben werden.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a><span data-ttu-id="f2ef0-472">Kapitel 9 – testen in gemischter Realität</span><span class="sxs-lookup"><span data-stu-id="f2ef0-472">Chapter 9 – Test in mixed reality</span></span>

<span data-ttu-id="f2ef0-473">An diesem Punkt müssen Sie testen, ob die Szene ordnungsgemäß implementiert wurde.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-473">At this point you need to test that the Scene has been properly implemented.</span></span>

<span data-ttu-id="f2ef0-474">Stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-474">Ensure that:</span></span>

- <span data-ttu-id="f2ef0-475">Alle in [Kapitel 1](#chapter-1--the-azure-portal) erwähnten Einstellungen sind richtig festgelegt.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-475">All the settings mentioned in [Chapter 1](#chapter-1--the-azure-portal) are set correctly.</span></span> 
- <span data-ttu-id="f2ef0-476">Die Skripts " *results*", " *Translator*" und " *mikrophonemanager*" werden an das **Hauptkamera** Objekt angefügt.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-476">The *Results*, *Translator*, and *MicrophoneManager*, scripts are attached to the **Main Camera** object.</span></span> 
- <span data-ttu-id="f2ef0-477">Sie haben ihren *Azure Textübersetzungs-API* Service- **Schlüssel** *innerhalb der Variablen* " **authorizationkey** " innerhalb des Konvertierungs Skripts platziert.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-477">You have placed your *Azure Translator Text API* Service **Key** within the **authorizationKey** variable within the *Translator* Script.</span></span>  
- <span data-ttu-id="f2ef0-478">Alle Felder im Hauptbereich der *Kamera Inspektor* sind ordnungsgemäß zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-478">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
- <span data-ttu-id="f2ef0-479">Ihr Mikrofon funktioniert beim Ausführen Ihrer Szene (wenn nicht, überprüfen Sie, ob Ihr angefügtes Mikrofon das *Standard* Gerät ist, und dass Sie [es in Windows ordnungsgemäß eingerichtet](https://support.microsoft.com/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)haben).</span><span class="sxs-lookup"><span data-stu-id="f2ef0-479">Your microphone is working when running your scene (if not, check that your attached microphone is the *default* device, and that you have [set it up correctly within Windows](https://support.microsoft.com/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span></span>

<span data-ttu-id="f2ef0-480">Sie können das immersive Headset testen, indem Sie die **Wiedergabe** Schaltfläche im *Unity-Editor*drücken.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-480">You can test the immersive headset by pressing the **Play** button in the *Unity Editor*.</span></span>
<span data-ttu-id="f2ef0-481">Die APP sollte über das angefügte immersive Headset funktionieren.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-481">The App should be functioning through the attached immersive headset.</span></span>

> [!WARNING]  
> <span data-ttu-id="f2ef0-482">Wenn in der Unity-Konsole eine Fehlermeldung angezeigt wird, dass das Standardaudiogerät geändert wird, funktioniert die Szene möglicherweise nicht wie erwartet.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-482">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="f2ef0-483">Der Grund hierfür ist die Art und Weise, wie das Mixed Reality-Portal mit integrierten Mikrofonen für Headsets umgeht, auf denen es sich befindet.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-483">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="f2ef0-484">Wenn dieser Fehler angezeigt wird, halten Sie die Szene einfach an, und starten Sie Sie erneut, und die Dinge sollten erwartungsgemäß funktionieren.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-484">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a><span data-ttu-id="f2ef0-485">Kapitel 10 – Erstellen der UWP-Lösung und querladen auf dem lokalen Computer</span><span class="sxs-lookup"><span data-stu-id="f2ef0-485">Chapter 10 – Build the UWP solution and sideload on local machine</span></span>

<span data-ttu-id="f2ef0-486">Alles, was für den Unity-Abschnitt dieses Projekts erforderlich ist, ist nun abgeschlossen, sodass es an der Zeit ist, Sie aus Unity zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-486">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="f2ef0-487">Navigieren Sie zu **Buildeinstellungen**: **Datei > Buildeinstellungen...**</span><span class="sxs-lookup"><span data-stu-id="f2ef0-487">Navigate to **Build Settings**: **File > Build Settings...**</span></span>
2.  <span data-ttu-id="f2ef0-488">Klicken Sie im Fenster " **Buildeinstellungen** " auf " **Erstellen**".</span><span class="sxs-lookup"><span data-stu-id="f2ef0-488">From the **Build Settings** window, click **Build**.</span></span>

    ![Erstellen Sie die Unity-Szene.](images/AzureLabs-Lab1-36.png)
  
3.  <span data-ttu-id="f2ef0-490">Wenn dies nicht bereits geschehen ist, Tick **Unity C# -Projekte**.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-490">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="f2ef0-491">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-491">Click **Build**.</span></span> <span data-ttu-id="f2ef0-492">Unity startet ein *Datei-Explorer* -Fenster, in dem Sie einen Ordner erstellen und auswählen müssen, in dem die App erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-492">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="f2ef0-493">Erstellen Sie diesen Ordner jetzt, und nennen Sie ihn " *App*".</span><span class="sxs-lookup"><span data-stu-id="f2ef0-493">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="f2ef0-494">Klicken Sie dann mit ausgewähltem *App* -Ordner auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-494">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="f2ef0-495">Unity startet das Projekt in den *App* -Ordner.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-495">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="f2ef0-496">Nachdem die Erstellung von Unity abgeschlossen ist (Dies kann einige Zeit in Anspruch nehmen), wird ein *Datei-Explorer* -Fenster am Speicherort des Builds geöffnet (überprüfen Sie die Taskleiste, da Sie möglicherweise nicht immer über Ihrem Fenster angezeigt wird, sondern Sie über das Hinzufügen eines neuen Fensters benachrichtigt).</span><span class="sxs-lookup"><span data-stu-id="f2ef0-496">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11--deploy-your-application"></a><span data-ttu-id="f2ef0-497">Kapitel 11 – Bereitstellen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="f2ef0-497">Chapter 11 – Deploy your application</span></span>

<span data-ttu-id="f2ef0-498">So stellen Sie die Anwendung bereit:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-498">To deploy your application:</span></span>

1.  <span data-ttu-id="f2ef0-499">Navigieren Sie zu Ihrem neuen Unity-Build ( *App* -Ordner), und öffnen Sie die Projektmappendatei mit *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-499">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
2.  <span data-ttu-id="f2ef0-500">Wählen Sie in der Projektmappenkonfiguration **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-500">In the Solution Configuration select **Debug**.</span></span>
3.  <span data-ttu-id="f2ef0-501">Wählen Sie auf der Projektmappenplattform die Option **x86**, **lokaler Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-501">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="f2ef0-502">Für Microsoft hololens ist es möglicherweise einfacher, dies auf den *Remote*Computer festzulegen, damit Sie nicht auf Ihren Computer über das Team verfügen.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-502">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="f2ef0-503">Allerdings müssen Sie auch die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="f2ef0-503">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="f2ef0-504">Informieren Sie sich über die **IP-Adresse** ihrer hololens. Sie finden diese in den *Einstellungen > Netzwerk & Internet > Wi-Fi-> Erweiterte Optionen*; die IPv4-Adresse ist die Adresse, die Sie verwenden sollten.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-504">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="f2ef0-505">Stellen Sie sicher, dass der *Entwicklermodus* **auf**dem in den *Einstellungen > Update & Sicherheits > für Entwickler*gefunden.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-505">Ensure *Developer Mode* is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Stellen Sie die Lösung aus Visual Studio bereit.](images/AzureLabs-Lab1-37.png)
    
 
4.  <span data-ttu-id="f2ef0-507">Wechseln Sie zum **Menü Erstellen** , und klicken Sie auf Lösung bereitstellen, um die Anwendung per querladen auf Ihren PC zu **verlagern** .</span><span class="sxs-lookup"><span data-stu-id="f2ef0-507">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>
5.  <span data-ttu-id="f2ef0-508">Ihre APP sollte nun in der Liste der installierten apps angezeigt werden, die gestartet werden können.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-508">Your App should now appear in the list of installed apps, ready to be launched.</span></span>
6.  <span data-ttu-id="f2ef0-509">Nach dem Start werden Sie von der APP aufgefordert, den Zugriff auf das Mikrofon zu autorisieren.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-509">Once launched, the App will prompt you to authorize access to the Microphone.</span></span> <span data-ttu-id="f2ef0-510">Stellen Sie sicher, dass Sie auf **Ja** klicken.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-510">Make sure to click the **YES** button.</span></span>
7.  <span data-ttu-id="f2ef0-511">Jetzt können Sie mit der Übersetzung beginnen!</span><span class="sxs-lookup"><span data-stu-id="f2ef0-511">You are now ready to start translating!</span></span>

## <a name="your-finished-translation-text-api-application"></a><span data-ttu-id="f2ef0-512">Die fertige Übersetzungs Text-API-Anwendung</span><span class="sxs-lookup"><span data-stu-id="f2ef0-512">Your finished Translation Text API application</span></span>

<span data-ttu-id="f2ef0-513">Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die die Text-API von Azure Translation zum Konvertieren von Sprache in übersetzten Text nutzt.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-513">Congratulations, you built a mixed reality app that leverages the Azure Translation Text API to convert speech to translated text.</span></span>

![Endprodukt.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="f2ef0-515">Bonus Übungen</span><span class="sxs-lookup"><span data-stu-id="f2ef0-515">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="f2ef0-516">Übung 1</span><span class="sxs-lookup"><span data-stu-id="f2ef0-516">Exercise 1</span></span>

<span data-ttu-id="f2ef0-517">Können Sie der APP Text-zu-Sprache-Funktionen hinzufügen, sodass der zurückgegebene Text gesprochen wird?</span><span class="sxs-lookup"><span data-stu-id="f2ef0-517">Can you add text-to-speech functionality to the app, so that the returned text is spoken?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="f2ef0-518">Übung 2</span><span class="sxs-lookup"><span data-stu-id="f2ef0-518">Exercise 2</span></span>

<span data-ttu-id="f2ef0-519">Ermöglicht es dem Benutzer, die Quell-und Ausgabesprachen ("from" und "to") innerhalb der APP selbst zu ändern, sodass die APP nicht jedes Mal neu erstellt werden muss, wenn Sie die Sprachen ändern möchten.</span><span class="sxs-lookup"><span data-stu-id="f2ef0-519">Make it possible for the user to change the source and output languages ('from' and 'to') within the app itself, so the app does not need to be rebuilt every time you want to change languages.</span></span>
