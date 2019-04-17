---
title: MR und Azure 301 - Übersetzung
description: Führen Sie diesen Kurs erfahren, wie Sie die Azure Textübersetzungs-API in einer mixed Reality-Anwendung zu implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorials, api, Translator-Text, Hololens, immersive vr
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596315"
---
>[!NOTE]
><span data-ttu-id="0debe-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="0debe-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="0debe-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="0debe-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="0debe-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="0debe-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="0debe-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="0debe-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="0debe-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="0debe-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="0debe-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="0debe-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-301-language-translation"></a><span data-ttu-id="0debe-110">MR und Azure 301: Übersetzung von Sprachen</span><span class="sxs-lookup"><span data-stu-id="0debe-110">MR and Azure 301: Language translation</span></span>

<span data-ttu-id="0debe-111">In diesem Kurs lernen Sie, wie eine mixed Reality-Anwendung mithilfe von Azure Cognitive Services, mit der Textübersetzungs-API beinhaltet hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="0debe-111">In this course, you will learn how to add translation capabilities to a mixed reality application using Azure Cognitive Services, with the Translator Text API.</span></span>

![Endprodukt](images/AzureLabs-Lab1-00.png)

<span data-ttu-id="0debe-113">Die Textübersetzungs-API ist eine Übersetzung Dienst, der nahezu in Echtzeit arbeitet.</span><span class="sxs-lookup"><span data-stu-id="0debe-113">The Translator Text API is a translation Service which works in near real-time.</span></span> <span data-ttu-id="0debe-114">Der Dienst ist Cloud-basierte, und, über einen REST-API-Aufruf, eine app kann der maschinellen Übersetzung neuronale verwenden, um Text in eine andere Sprache übersetzen.</span><span class="sxs-lookup"><span data-stu-id="0debe-114">The Service is cloud-based, and, using a REST API call, an app can make use of the neural machine translation technology to translate text to another language.</span></span> <span data-ttu-id="0debe-115">Weitere Informationen finden Sie auf die [Textübersetzungs-API von Azure-Seite](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span><span class="sxs-lookup"><span data-stu-id="0debe-115">For more information, visit the [Azure Translator Text API page](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span></span>

<span data-ttu-id="0debe-116">Nach Abschluss dieses Kurses verfügen Sie über ein mixed Reality-Anwendung die können die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="0debe-116">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1.  <span data-ttu-id="0debe-117">Der Benutzer wird in ein Mikrofon an eine immersive (VR) Kopfhörer angeschlossen (oder das integrierte Mikrofon von HoloLens) sprechen.</span><span class="sxs-lookup"><span data-stu-id="0debe-117">The user will speak into a microphone connected to an immersive (VR) headset (or the built-in microphone of HoloLens).</span></span>
2.  <span data-ttu-id="0debe-118">Die app wird das Diktieren erfassen und an den Azure Textübersetzungs-API senden.</span><span class="sxs-lookup"><span data-stu-id="0debe-118">The app will capture the dictation and send it to the Azure Translator Text API.</span></span>
3.  <span data-ttu-id="0debe-119">Die Verschiebung dazu wird in einer einfachen Benutzeroberfläche-Gruppe in der Unity-Szene angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="0debe-119">The translation result will be displayed in a simple UI group in the Unity Scene.</span></span>

<span data-ttu-id="0debe-120">In diesem Kurs erfahren Sie, wie zum Abrufen der Ergebnisse von der Translator-Dienst in eine Unity-basierten Anwendung.</span><span class="sxs-lookup"><span data-stu-id="0debe-120">This course will teach you how to get the results from the Translator Service into a Unity-based sample application.</span></span> <span data-ttu-id="0debe-121">Sie werden sich entscheiden, ob Sie diese Konzepte, die Sie erstellen eine benutzerdefinierte Anwendung zuweisen.</span><span class="sxs-lookup"><span data-stu-id="0debe-121">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="0debe-122">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="0debe-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0debe-123">Kurs</span><span class="sxs-lookup"><span data-stu-id="0debe-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="0debe-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0debe-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0debe-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="0debe-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="0debe-126">MR und Azure 301: Übersetzung von Sprachen</span><span class="sxs-lookup"><span data-stu-id="0debe-126">MR and Azure 301: Language translation</span></span></td><td style="text-align: center;"> <span data-ttu-id="0debe-127">✔️</span><span class="sxs-lookup"><span data-stu-id="0debe-127">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="0debe-128">✔️</span><span class="sxs-lookup"><span data-stu-id="0debe-128">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="0debe-129">Während dieser Kurs in erster Linie für immersive Windows Mixed Reality (VR)-Headsets ausgerichtet ist, können Sie auch anwenden, was Sie in diesem Kurs, Microsoft HoloLens lernen.</span><span class="sxs-lookup"><span data-stu-id="0debe-129">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="0debe-130">Wie Sie den Kurs halten, sehen Anmerkungen zu dieser Version auf Änderungen Sie möglicherweise zur Unterstützung von HoloLens einsetzen müssen.</span><span class="sxs-lookup"><span data-stu-id="0debe-130">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="0debe-131">Wenn Sie HoloLens verwenden zu können, werden Sie einige Echo während der Sprachaufnahme feststellen.</span><span class="sxs-lookup"><span data-stu-id="0debe-131">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0debe-132">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="0debe-132">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="0debe-133">In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#.</span><span class="sxs-lookup"><span data-stu-id="0debe-133">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="0debe-134">Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Mai 2018) überprüft wurde.</span><span class="sxs-lookup"><span data-stu-id="0debe-134">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="0debe-135">Sie können zur Verwendung der neuesten Software, wie in der [Installieren der Tools](install-the-tools.md) Artikel, obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt was finden Sie in der neueren Software entspricht als die unten Angaben aufgeführten .</span><span class="sxs-lookup"><span data-stu-id="0debe-135">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="0debe-136">Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:</span><span class="sxs-lookup"><span data-stu-id="0debe-136">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="0debe-137">Eine Entwicklungs-PC [kompatibel mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für immersive (VR) Kopfhörer-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="0debe-137">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="0debe-138">Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="0debe-138">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="0debe-139">Das neueste Windows 10-SDK</span><span class="sxs-lookup"><span data-stu-id="0debe-139">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="0debe-140">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="0debe-140">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="0debe-141">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0debe-141">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="0debe-142">Ein [immersive Windows Mixed Reality (VR)-Kopfhörer](immersive-headset-hardware-details.md) oder [Microsoft HoloLens](hololens-hardware-details.md) mit Entwicklermodus aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="0debe-142">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="0debe-143">Eine Reihe von Kopfhörer mit ein eingebautes Mikrofon verfügen (wenn der Kopfhörer nicht über eine integrierte mic und die Lautsprecher verfügt)</span><span class="sxs-lookup"><span data-stu-id="0debe-143">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="0debe-144">Zugriff auf das Internet für den Abruf von Azure-Setup und Übersetzung</span><span class="sxs-lookup"><span data-stu-id="0debe-144">Internet access for Azure setup and translation retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="0debe-145">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="0debe-145">Before you start</span></span>

- <span data-ttu-id="0debe-146">Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).</span><span class="sxs-lookup"><span data-stu-id="0debe-146">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="0debe-147">Der Code in diesem Tutorial können Sie aus dem Mikrofon-Standardgerät, die mit dem PC verbundenes aufzeichnen.</span><span class="sxs-lookup"><span data-stu-id="0debe-147">The code in this tutorial will allow you to record from the default microphone device connected to your PC.</span></span> <span data-ttu-id="0debe-148">Stellen Sie sicher, dass das Mikrofon-Standardgerät an das Gerät festgelegt ist, die Sie verwenden, um Ihre Stimme erfassen möchten.</span><span class="sxs-lookup"><span data-stu-id="0debe-148">Make sure the default microphone device is set to the device you plan to use to capture your voice.</span></span>
- <span data-ttu-id="0debe-149">Damit können Ihren PC Diktat zu aktivieren, wechseln Sie zu **Einstellungen > Datenschutz >-Sprache, Freihand & Eingabe** , und wählen Sie die Schaltfläche mit den **Aktivieren von Sprachdienste und Typisierung Vorschläge**.</span><span class="sxs-lookup"><span data-stu-id="0debe-149">To allow your PC to enable dictation, go to **Settings > Privacy > Speech, inking & typing** and select the button **Turn On speech services and typing suggestions**.</span></span>
- <span data-ttu-id="0debe-150">Wenn Sie ein Mikrofon und Kopfhörer angeschlossen, um (oder in integriert) verwenden Ihre Kopfhörer, stellen Sie sicher, dass die Option "Ich meine Kopfhörer wear, wechseln Sie zur Kopfhörer-mic" ist im aktiviert **Einstellungen > Mixed Reality > Audio- und Spracherkennung**.</span><span class="sxs-lookup"><span data-stu-id="0debe-150">If you're using a microphone and headphones connected to (or built-in to) your headset, make sure the option “When I wear my headset, switch to headset mic” is turned on in **Settings > Mixed reality > Audio and speech**.</span></span>

   ![Mixed Reality-Einstellungen](images/AzureLabs-Lab1-00-5.png)

   ![Mikrofon-Einstellung](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> <span data-ttu-id="0debe-153">Denken Sie daran, dass wenn Sie für eine immersive Kopfhörer für diese Umgebung entwickeln, Audioausgabe Geräteprobleme auftreten können.</span><span class="sxs-lookup"><span data-stu-id="0debe-153">Be aware that if you are developing for an immersive headset for this lab, you may experience audio output device issues.</span></span> <span data-ttu-id="0debe-154">Dies ist aufgrund eines Problems mit Unity, die in höheren Versionen von Unity (Unity 2018.2) behoben wird.</span><span class="sxs-lookup"><span data-stu-id="0debe-154">This is due to an issue with Unity, which is fixed in later versions of Unity (Unity 2018.2).</span></span> <span data-ttu-id="0debe-155">Das Problem wird verhindert, dass Unity das Standard-Audioausgabegerät zur Laufzeit ändern.</span><span class="sxs-lookup"><span data-stu-id="0debe-155">The issue prevents Unity from changing the default audio output device at run time.</span></span> <span data-ttu-id="0debe-156">Können dies umgehen stellen Sie sicher, dass Sie die oben genannten Schritte abgeschlossen haben, und schließen und erneut im Editor öffnen, wenn dieses Problem selbst präsentiert.</span><span class="sxs-lookup"><span data-stu-id="0debe-156">As a work around, ensure you have completed the above steps, and close and re-open the Editor, when this issue presents itself.</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="0debe-157">Kapitel 1 – Azure-Portal</span><span class="sxs-lookup"><span data-stu-id="0debe-157">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="0debe-158">Um die Translator-API von Azure zu verwenden, müssen Sie so konfigurieren Sie eine Instanz des Diensts, der für Ihre Anwendung verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="0debe-158">To use the Azure Translator API, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="0debe-159">Melden Sie sich bei der [Azure-Portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="0debe-159">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="0debe-160">Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen.</span><span class="sxs-lookup"><span data-stu-id="0debe-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="0debe-161">Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.</span><span class="sxs-lookup"><span data-stu-id="0debe-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="0debe-162">Sobald Sie angemeldet sind, klicken Sie auf **neu** in der oberen linken Ecke, und suchen Sie nach "Textübersetzungs-API".</span><span class="sxs-lookup"><span data-stu-id="0debe-162">Once you are logged in, click on **New** in the top left corner and search for "Translator Text API."</span></span> <span data-ttu-id="0debe-163">Wählen Sie **geben**.</span><span class="sxs-lookup"><span data-stu-id="0debe-163">Select **Enter**.</span></span>

    ![Neue Ressource](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > <span data-ttu-id="0debe-165">Das Wort **neu** wurden möglicherweise durch ersetzt **erstellen Sie eine Ressource**, in neueren-Portalen.</span><span class="sxs-lookup"><span data-stu-id="0debe-165">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="0debe-166">Die neue Seite bietet eine Beschreibung der *Textübersetzungs-API* Service.</span><span class="sxs-lookup"><span data-stu-id="0debe-166">The new page will provide a description of the *Translator Text API* Service.</span></span> <span data-ttu-id="0debe-167">Unten links auf dieser Seite die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="0debe-167">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Translator-Text-API-Dienst erstellen](images/AzureLabs-Lab1-03.png)

4.  <span data-ttu-id="0debe-169">Nachdem Sie auf geklickt haben **erstellen**:</span><span class="sxs-lookup"><span data-stu-id="0debe-169">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="0debe-170">Fügen Sie Ihre bevorzugte **Namen** für diese Dienstinstanz.</span><span class="sxs-lookup"><span data-stu-id="0debe-170">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="0debe-171">Wählen Sie einen geeigneten **Abonnement**.</span><span class="sxs-lookup"><span data-stu-id="0debe-171">Select an appropriate **Subscription**.</span></span>
    3. <span data-ttu-id="0debe-172">Wählen Sie die **Tarif** für Sie geeignet ist, ist dies die erste Zeit in die Erstellung einer *Translator-Text-Dienst*, freier-Tarif (mit dem Namen F0) für Sie verfügbar sein sollen.</span><span class="sxs-lookup"><span data-stu-id="0debe-172">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Translator Text Service*, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="0debe-173">Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="0debe-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="0debe-174">Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="0debe-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="0debe-175">Es wird empfohlen, alle zu bewahren, an die Azure-Dienste unter einer allgemeinen Ressourcengruppe mit einem einzelnen Projekt (z. B. z. B. diesen Labs) verknüpft ist).</span><span class="sxs-lookup"><span data-stu-id="0debe-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="0debe-176">Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, bitte [finden Sie im Artikel der Resource-Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="0debe-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="0debe-177">Bestimmen der **Speicherort** für Ihre Ressourcengruppe aus (Wenn Sie eine neue Ressourcengruppe erstellen).</span><span class="sxs-lookup"><span data-stu-id="0debe-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="0debe-178">Der Speicherort würde idealerweise in der Region sein, in dem die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="0debe-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="0debe-179">Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="0debe-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="0debe-180">Sie müssen auch bestätigen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.</span><span class="sxs-lookup"><span data-stu-id="0debe-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="0debe-181">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="0debe-181">Select **Create**.</span></span>

        ![Wählen Sie die Schaltfläche "erstellen".](images/AzureLabs-Lab1-04.png)

5.  <span data-ttu-id="0debe-183">Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.</span><span class="sxs-lookup"><span data-stu-id="0debe-183">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="0debe-184">Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0debe-184">A notification will appear in the portal once the Service instance is created.</span></span> 

    ![Benachrichtigung über Azure Service-Erstellung](images/AzureLabs-Lab1-05.png)

7.  <span data-ttu-id="0debe-186">Klicken Sie auf die Benachrichtigung, um Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="0debe-186">Click on the notification to explore your new Service instance.</span></span> 

    ![Wechseln Sie zur Ressource Popup.](images/AzureLabs-Lab1-06.png)

8.  <span data-ttu-id="0debe-188">Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="0debe-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="0debe-189">Sie werden auf die neue Instanz der Translator Text-API-Dienst weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="0debe-189">You will be taken to your new Translator Text API Service instance.</span></span> 

    ![Translator-Text-API-Dienst-Seite](images/AzureLabs-Lab1-07.png)

9.  <span data-ttu-id="0debe-191">In diesem Tutorial müssen Ihre Anwendung Aufrufe an Ihren Dienst, was durch die Verwendung von Subscription-Key Ihres Diensts erfolgt.</span><span class="sxs-lookup"><span data-stu-id="0debe-191">Within this tutorial, your application will need to make calls to your Service, which is done through using your Service’s Subscription Key.</span></span> 
10. <span data-ttu-id="0debe-192">Aus der *Schnellstart* auf der Seite Ihrer *Textübersetzungs* -Dienst navigieren, mit dem ersten Schritt *nehmen Sie Ihre Schlüssel*, und klicken Sie auf **Schlüssel** (Sie können auch erreichen Sie dies, indem Sie auf den blauen Link Schlüssel befindet sich im Navigationsmenü Dienste durch ein Schlüsselsymbol gekennzeichnet).</span><span class="sxs-lookup"><span data-stu-id="0debe-192">From the *Quick start* page of your *Translator Text* Service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the Services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="0debe-193">Dadurch wird angezeigt, den Dienst *Schlüssel*.</span><span class="sxs-lookup"><span data-stu-id="0debe-193">This will reveal your Service *Keys*.</span></span>
11. <span data-ttu-id="0debe-194">Erstellen Sie eine Kopie eines der angezeigten Schlüssel wird, da Sie dies später in Ihr Projekt benötigen.</span><span class="sxs-lookup"><span data-stu-id="0debe-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="0debe-195">Kapitel 2: Einrichten von Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="0debe-195">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="0debe-196">Richten Sie ein und Testen Sie Ihrer mixed Reality immersive Kopfhörer.</span><span class="sxs-lookup"><span data-stu-id="0debe-196">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="0debe-197">Sie benötigen für diesen Kurs nicht während der Übertragung Controller.</span><span class="sxs-lookup"><span data-stu-id="0debe-197">You will not need motion controllers for this course.</span></span> <span data-ttu-id="0debe-198">Wenn Sie die Einrichtung einer immersive Kopfhörer unterstützen müssen, wenden Sie [gehen Sie folgendermaßen vor](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="0debe-198">If you need support setting up an immersive headset, please [follow these steps](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

<span data-ttu-id="0debe-199">Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit mixed Reality und, daher ist eine gute Vorlage für andere Projekte:</span><span class="sxs-lookup"><span data-stu-id="0debe-199">The following is a typical set up for developing with mixed reality and, as such, is a good template for other projects:</span></span>

1.  <span data-ttu-id="0debe-200">Open *Unity* , und klicken Sie auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="0debe-200">Open *Unity* and click **New**.</span></span> 

    ![Starten Sie die neues Unity-Projekt.](images/AzureLabs-Lab1-08.png)

2.  <span data-ttu-id="0debe-202">Sie müssen nun einen Namen für die Unity-Projekt bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="0debe-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="0debe-203">Fügen Sie **MR_Translation**.</span><span class="sxs-lookup"><span data-stu-id="0debe-203">Insert **MR_Translation**.</span></span> <span data-ttu-id="0debe-204">Stellen Sie sicher, dass der Projekttyp nastaven NA hodnotu **3D**.</span><span class="sxs-lookup"><span data-stu-id="0debe-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="0debe-205">Legen Sie die *Speicherort* auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser).</span><span class="sxs-lookup"><span data-stu-id="0debe-205">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="0debe-206">Klicken Sie auf **projekterstellung**.</span><span class="sxs-lookup"><span data-stu-id="0debe-206">Then, click **Create project**.</span></span>

    ![Die Details für die neue Unity-Projekt.](images/AzureLabs-Lab1-09.png)

3.  <span data-ttu-id="0debe-208">Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="0debe-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="0debe-209">Wechseln Sie zu **Bearbeiten > Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**.</span><span class="sxs-lookup"><span data-stu-id="0debe-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="0debe-210">Änderung **externen Skript-Editors** zu **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="0debe-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="0debe-211">Schließen der **Voreinstellungen** Fenster.</span><span class="sxs-lookup"><span data-stu-id="0debe-211">Close the **Preferences** window.</span></span>

    ![Aktualisieren Sie die Skript-Editor-Einstellung.](images/AzureLabs-Lab1-10.png)

4.  <span data-ttu-id="0debe-213">Öffnen Sie als Nächstes **Datei > Buildeinstellungen** , und wechseln von der Plattform bereitgestellten **universelle Windows-Plattform**, durch Klicken auf die **Plattform wechseln** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="0debe-213">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Fenster "Einstellungen", Switch-Plattform für die UWP zu erstellen.](images/AzureLabs-Lab1-11.png)

5.  <span data-ttu-id="0debe-215">Wechseln Sie zu **Datei > Buildeinstellungen** und stellen Sie sicher, dass:</span><span class="sxs-lookup"><span data-stu-id="0debe-215">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="0debe-216">**Geräte** nastaven NA hodnotu **einem beliebigen Gerät**.</span><span class="sxs-lookup"><span data-stu-id="0debe-216">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="0debe-217">Legen Sie für Microsoft HoloLens, **Zielgerät** zu *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="0debe-217">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="0debe-218">**Buildtyp** nastaven NA hodnotu **D3D**</span><span class="sxs-lookup"><span data-stu-id="0debe-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="0debe-219">**SDK** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="0debe-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="0debe-220">**Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="0debe-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="0debe-221">**Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**</span><span class="sxs-lookup"><span data-stu-id="0debe-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="0debe-222">Die Szene speichern und mit dem Build hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="0debe-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="0debe-223">Hierzu **öffnen Szenen hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="0debe-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="0debe-224">Ein Speichern Fenster wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0debe-224">A save window will appear.</span></span>

            ![Klicken Sie auf, öffnen im Hintergrund-Schaltfläche "hinzufügen"](images/AzureLabs-Lab1-12.png)

        2. <span data-ttu-id="0debe-226">Erstellen einen neuen Ordner für, und alle zukünftigen, Szene, klicken Sie dann auf die **neuer Ordner** Schaltfläche zum Erstellen eines neuen Ordners, nennen Sie sie **Szenen**.</span><span class="sxs-lookup"><span data-stu-id="0debe-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Erstellen Sie neue Ordner "Scripts"](images/AzureLabs-Lab1-13.png)

        3. <span data-ttu-id="0debe-228">Öffnen Sie den neu erstellten **Szenen** Ordner, und klicken Sie dann in der *Dateiname*: Textfeld **MR_TranslationScene**, drücken Sie dann die **speichern**.</span><span class="sxs-lookup"><span data-stu-id="0debe-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_TranslationScene**, then press **Save**.</span></span>

            ![Geben Sie neue Szene einen Namen zu.](images/AzureLabs-Lab1-14.png)

            > <span data-ttu-id="0debe-230">Beachten Sie, speichern Sie Ihre Unity-Szenen in den *Assets* Ordner, wie sie mit der Unity-Projekt verbunden sein müssen.</span><span class="sxs-lookup"><span data-stu-id="0debe-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="0debe-231">Erstellen den Ordner im Hintergrund (und andere ähnliche Ordner), wird eine typische Möglichkeit Strukturieren eines Unity-Projekts ist.</span><span class="sxs-lookup"><span data-stu-id="0debe-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="0debe-232">Die Einstellungen im verbleibenden *Buildeinstellungen*, sollte jetzt als Standard bleiben.</span><span class="sxs-lookup"><span data-stu-id="0debe-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="0debe-233">In der *Buildeinstellungen* Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dadurch wird den entsprechenden Bereich geöffnet, im Bereich, in dem die *Inspektor* befindet.</span><span class="sxs-lookup"><span data-stu-id="0debe-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Öffnen der playereinstellungen.](images/AzureLabs-Lab1-15.png)

7. <span data-ttu-id="0debe-235">In diesem Bereich sind müssen einige Einstellungen überprüft werden:</span><span class="sxs-lookup"><span data-stu-id="0debe-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="0debe-236">In der **Weitere Einstellungen** Registerkarte:</span><span class="sxs-lookup"><span data-stu-id="0debe-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="0debe-237">**Scripting Runtime Version** muss **stabile** (.NET 3.5 entspricht).</span><span class="sxs-lookup"><span data-stu-id="0debe-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="0debe-238">**Back-End-Scripting** muss **.NET**</span><span class="sxs-lookup"><span data-stu-id="0debe-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="0debe-239">**API-Kompatibilitätsebene** muss **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="0debe-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Andere Einstellungen zu aktualisieren.](images/AzureLabs-Lab1-16.png)
      
    2. <span data-ttu-id="0debe-241">In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:</span><span class="sxs-lookup"><span data-stu-id="0debe-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="0debe-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="0debe-242">**InternetClient**</span></span>
        2. <span data-ttu-id="0debe-243">**Microphone**</span><span class="sxs-lookup"><span data-stu-id="0debe-243">**Microphone**</span></span>

            ![Veröffentlichungseinstellungen werden aktualisiert.](images/AzureLabs-Lab1-17.png)

    3. <span data-ttu-id="0debe-245">Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality-SDK**  hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="0debe-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Aktualisieren Sie die X-R-Einstellungen.](images/AzureLabs-Lab1-18.png)

8.  <span data-ttu-id="0debe-247">Im **Buildeinstellungen**, *Unity C# Projekte* nicht mehr abgeblendet ist, aktivieren Sie das Kontrollkästchen neben dieser.</span><span class="sxs-lookup"><span data-stu-id="0debe-247">Back in **Build Settings**, *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="0debe-248">Schließen Sie das Fenster "erstellen".</span><span class="sxs-lookup"><span data-stu-id="0debe-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="0debe-249">Speichern Sie Ihre Szene und das Projekt (**Datei > Speichern SZENE / FILE > Speichern Projekt**).</span><span class="sxs-lookup"><span data-stu-id="0debe-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="0debe-250">Kapitel 3 – Main Camera-setup</span><span class="sxs-lookup"><span data-stu-id="0debe-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0debe-251">Wenn Sie, überspringen möchten der *Unity einrichten* -Komponente dieser Kurs, und weiterhin direkt in Code, gerne [Herunterladen dieser .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), importieren Sie es in Ihr Projekt als eine [ *Custom Package*](https://docs.unity3d.com/Manual/AssetPackages.html), und klicken Sie dann eine Fortsetzung [Kapitel 5](#chapter-5--create-the-results-class).</span><span class="sxs-lookup"><span data-stu-id="0debe-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), import it into your project as a [*Custom Package*](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-results-class).</span></span> <span data-ttu-id="0debe-252">Sie müssen immer noch ein Unity-Projekt zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="0debe-252">You will still need to create a Unity Project.</span></span>

1.  <span data-ttu-id="0debe-253">In der *Hierarchie Bereich*, sehen Sie ein Objekt namens **Main Camera**, diesem Objekt dargestellten Ihr "Head" Sicht aus, wenn Sie "in" Ihrer Anwendung sind.</span><span class="sxs-lookup"><span data-stu-id="0debe-253">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your “head” point of view once you are “inside” your application.</span></span>
2.  <span data-ttu-id="0debe-254">Wählen Sie im Unity-Dashboard vor Ihnen die **Main Camera "gameobject"**.</span><span class="sxs-lookup"><span data-stu-id="0debe-254">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="0debe-255">Sie werden feststellen, dass die *Inspektor Bereich* (in der Regel nach rechts im Dashboard gefunden) zeigt die verschiedenen Komponenten, die *"gameobject"*, mit *transformieren* oben, gefolgt von *Kamera*, und einige andere Komponenten.</span><span class="sxs-lookup"><span data-stu-id="0debe-255">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="0debe-256">Sie müssen die Transformation der Main-Kamera, zurücksetzen, damit sie richtig positioniert ist.</span><span class="sxs-lookup"><span data-stu-id="0debe-256">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>
3.  <span data-ttu-id="0debe-257">Wählen Sie zu diesem Zweck die **Zahnradsymbol** Symbol neben der Kamera *transformieren* -Komponente, und wählen **zurücksetzen**.</span><span class="sxs-lookup"><span data-stu-id="0debe-257">To do this, select the **Gear** icon next to the Camera’s *Transform* component, and selecting **Reset**.</span></span> 

    ![Setzen Sie die Main Camera-Transformation zurück.](images/AzureLabs-Lab1-19.png)
 
4.  <span data-ttu-id="0debe-259">Die *transformieren* Komponente sollte dann wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="0debe-259">The *Transform* component should then look like:</span></span>

    1. <span data-ttu-id="0debe-260">Die *Position* nastaven NA hodnotu **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="0debe-260">The *Position* is set to **0, 0, 0**</span></span>
    2. <span data-ttu-id="0debe-261">*Drehung* nastaven NA hodnotu **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="0debe-261">*Rotation* is set to **0, 0, 0**</span></span>
    3. <span data-ttu-id="0debe-262">Und *Skalierung* nastaven NA hodnotu **1, 1, 1**</span><span class="sxs-lookup"><span data-stu-id="0debe-262">And *Scale* is set to **1, 1, 1**</span></span>

        ![Transformieren Sie die Informationen für Kamera](images/AzureLabs-Lab1-20.png)

5.  <span data-ttu-id="0debe-264">Als Nächstes mit der **Main Camera** Objekt ausgewählt haben, finden Sie unter den **Komponente hinzufügen** Schaltfläche am Ende der *Inspektor Bereich*.</span><span class="sxs-lookup"><span data-stu-id="0debe-264">Next, with the **Main Camera** object selected, see the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span> 
6.  <span data-ttu-id="0debe-265">Klicken Sie auf diese Schaltfläche, und suchen (entweder durch das eingeben *Audio Source* in das Suchfeld ein, oder Navigieren in den Abschnitten) für die Komponente mit dem Namen **Audio Source** wie unten dargestellt, und wählen Sie ihn (drücken Sie die EINGABETASTE auf Außerdem funktioniert).</span><span class="sxs-lookup"><span data-stu-id="0debe-265">Select that button, and search (by either typing *Audio Source* into the search field or navigating the sections) for the component called **Audio Source** as shown below and select it (pressing enter on it also works).</span></span>
7.  <span data-ttu-id="0debe-266">Ein *Audio Source* Komponente hinzugefügt werden wird die **Main Camera**, wie unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="0debe-266">An *Audio Source* component will be added to the **Main Camera**, as demonstrated below.</span></span>

    ![Fügen Sie eine Audio Source-Komponente hinzu.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > <span data-ttu-id="0debe-268">Für Microsoft HoloLens, müssen Sie auch Folgendes ändern die sind Teil der **Kamera** -Komponente auf Ihre **Main Camera**:</span><span class="sxs-lookup"><span data-stu-id="0debe-268">For Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component on your **Main Camera**:</span></span>
    > - <span data-ttu-id="0debe-269">**Flags zu löschen:** Volltonfarbe entspricht.</span><span class="sxs-lookup"><span data-stu-id="0debe-269">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="0debe-270">**Hintergrund** "Schwarz, Alpha 0" – Hex-Color: #00000000.</span><span class="sxs-lookup"><span data-stu-id="0debe-270">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

## <a name="chapter-4--setup-debug-canvas"></a><span data-ttu-id="0debe-271">Kapitel 4 – Setup-Debug-Canvas</span><span class="sxs-lookup"><span data-stu-id="0debe-271">Chapter 4 – Setup Debug Canvas</span></span>

<span data-ttu-id="0debe-272">Um die Eingabe und Ausgabe der Übersetzung anzuzeigen, muss eine einfache Benutzeroberfläche erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="0debe-272">To show the input and output of the translation, a basic UI needs to be created.</span></span> <span data-ttu-id="0debe-273">Für diesen Kurs erstellen Sie eine Canvas-UI-Objekt, mit mehreren 'Text'-Objekten, um die Daten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="0debe-273">For this course, you will create a Canvas UI object, with several ‘Text’ objects to show the data.</span></span>

1.  <span data-ttu-id="0debe-274">Mit der rechten Maustaste in einen leeren Bereich des der *Hierarchie Bereich*unter **UI**, Hinzufügen einer **Canvas**.</span><span class="sxs-lookup"><span data-stu-id="0debe-274">Right-click in an empty area of the *Hierarchy Panel*, under **UI**, add a **Canvas**.</span></span>

    ![Fügen Sie neue Canvas-UI-Objekt hinzu.](images/AzureLabs-Lab1-22.png)

2.  <span data-ttu-id="0debe-276">Mit dem Canvas-Objekt, das ausgewählt ist, in der *Inspektor Bereich* (innerhalb der Komponente "Canvas"), ändern Sie **Rendermodus** zu **Raum der Welt**.</span><span class="sxs-lookup"><span data-stu-id="0debe-276">With the Canvas object selected, in the *Inspector Panel* (within the ‘Canvas’ component), change **Render Mode** to **World Space**.</span></span> 
3.  <span data-ttu-id="0debe-277">Als Nächstes ändern Sie die folgenden Parameter in der *Inspektor Bereichs Rect Transformation*:</span><span class="sxs-lookup"><span data-stu-id="0debe-277">Next, change the following parameters in the *Inspector Panel’s Rect Transform*:</span></span>

    1. <span data-ttu-id="0debe-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span><span class="sxs-lookup"><span data-stu-id="0debe-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span></span>
    2. <span data-ttu-id="0debe-279">*Breite* – 500</span><span class="sxs-lookup"><span data-stu-id="0debe-279">*Width* -    500</span></span>
    3. <span data-ttu-id="0debe-280">*Höhe* – 300</span><span class="sxs-lookup"><span data-stu-id="0debe-280">*Height* -   300</span></span>
    4. <span data-ttu-id="0debe-281">*Scale* - **X** 0.13 **Y** 0.13  **Z** 0.13</span><span class="sxs-lookup"><span data-stu-id="0debe-281">*Scale* - **X** 0.13 **Y** 0.13  **Z** 0.13</span></span>

        ![Aktualisieren Sie die Rect-Transformation für die Canvas.](images/AzureLabs-Lab1-23.png)
 
4.  <span data-ttu-id="0debe-283">Klicken Sie mit der rechten Maustaste auf die **Canvas** in die *Hierarchie Bereich*unter **UI**, und fügen eine **Bereich**.</span><span class="sxs-lookup"><span data-stu-id="0debe-283">Right click on the **Canvas** in the *Hierarchy Panel*, under **UI**, and add a **Panel**.</span></span> <span data-ttu-id="0debe-284">Dies **Bereich** bieten einen Hintergrund auf den Text an, die Sie in der Szene anzeigen lassen.</span><span class="sxs-lookup"><span data-stu-id="0debe-284">This **Panel** will provide a background to the text that you will be displaying in the scene.</span></span>
5.  <span data-ttu-id="0debe-285">Klicken Sie mit der rechten Maustaste auf die **Bereich** in die *Hierarchie Bereich*unter **UI**, und fügen eine **Textobjekt**.</span><span class="sxs-lookup"><span data-stu-id="0debe-285">Right click on the **Panel** in the *Hierarchy Panel*, under **UI**, and add a **Text object**.</span></span> <span data-ttu-id="0debe-286">Wiederholen Sie den gleichen Vorgang aus, bis Sie insgesamt vier Benutzeroberflächentext-Objekte erstellt haben (Hinweis: Wenn Sie das erste 'Text'-Objekt, das ausgewählt haben, können Sie einfach eine drücken **"Strg" + hatte "**, duplizieren, bevor Sie vier insgesamt haben).</span><span class="sxs-lookup"><span data-stu-id="0debe-286">Repeat the same process until you have created four UI Text objects in total (Hint: if you have the first ‘Text’ object selected, you can simply press **‘Ctrl’ + ‘D’**, to duplicate it, until you have four in total).</span></span> 
6.  <span data-ttu-id="0debe-287">Für jede **Textobjekt**, wählen Sie ihn, und verwenden Sie die folgenden Tabellen die Parameter fest, der *Inspector-Bereich*.</span><span class="sxs-lookup"><span data-stu-id="0debe-287">For each **Text Object**, select it and use the below tables to set the parameters in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="0debe-288">Für die *Rect-Transformation* Komponente:</span><span class="sxs-lookup"><span data-stu-id="0debe-288">For the *Rect Transform* component:</span></span>

        | <span data-ttu-id="0debe-289">Name</span><span class="sxs-lookup"><span data-stu-id="0debe-289">Name</span></span>                   | <span data-ttu-id="0debe-290">Transformieren - *Position*</span><span class="sxs-lookup"><span data-stu-id="0debe-290">Transform - *Position*</span></span>             | <span data-ttu-id="0debe-291">Breite</span><span class="sxs-lookup"><span data-stu-id="0debe-291">Width</span></span>      | <span data-ttu-id="0debe-292">Höhe</span><span class="sxs-lookup"><span data-stu-id="0debe-292">Height</span></span>    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | <span data-ttu-id="0debe-293">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="0debe-293">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="0debe-294">**X** -80 **Y** 90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="0debe-294">**X** -80 **Y** 90 **Z** 0</span></span>         | <span data-ttu-id="0debe-295">300</span><span class="sxs-lookup"><span data-stu-id="0debe-295">300</span></span>        | <span data-ttu-id="0debe-296">30</span><span class="sxs-lookup"><span data-stu-id="0debe-296">30</span></span>        |
        | <span data-ttu-id="0debe-297">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="0debe-297">AzureResponseLabel</span></span>     | <span data-ttu-id="0debe-298">**X** -80 **Y** 30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="0debe-298">**X** -80 **Y** 30 **Z** 0</span></span>         | <span data-ttu-id="0debe-299">300</span><span class="sxs-lookup"><span data-stu-id="0debe-299">300</span></span>        | <span data-ttu-id="0debe-300">30</span><span class="sxs-lookup"><span data-stu-id="0debe-300">30</span></span>        |
        | <span data-ttu-id="0debe-301">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="0debe-301">DictationLabel</span></span>         | <span data-ttu-id="0debe-302">**X** -80 **Y** -30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="0debe-302">**X** -80 **Y** -30 **Z** 0</span></span>        | <span data-ttu-id="0debe-303">300</span><span class="sxs-lookup"><span data-stu-id="0debe-303">300</span></span>        | <span data-ttu-id="0debe-304">30</span><span class="sxs-lookup"><span data-stu-id="0debe-304">30</span></span>        |
        | <span data-ttu-id="0debe-305">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="0debe-305">TranslationResultLabel</span></span> | <span data-ttu-id="0debe-306">**X** -80 **Y** -90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="0debe-306">**X** -80 **Y** -90 **Z** 0</span></span>        | <span data-ttu-id="0debe-307">300</span><span class="sxs-lookup"><span data-stu-id="0debe-307">300</span></span>        | <span data-ttu-id="0debe-308">30</span><span class="sxs-lookup"><span data-stu-id="0debe-308">30</span></span>        |


    2. <span data-ttu-id="0debe-309">Für die **Text (Skript)** Komponente:</span><span class="sxs-lookup"><span data-stu-id="0debe-309">For the **Text (Script)** component:</span></span>


        | <span data-ttu-id="0debe-310">Name</span><span class="sxs-lookup"><span data-stu-id="0debe-310">Name</span></span>                   | <span data-ttu-id="0debe-311">Text</span><span class="sxs-lookup"><span data-stu-id="0debe-311">Text</span></span>               | <span data-ttu-id="0debe-312">Schriftgrad</span><span class="sxs-lookup"><span data-stu-id="0debe-312">Font Size</span></span>    |
        |:----------------------:|:------------------:|:------------:|
        | <span data-ttu-id="0debe-313">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="0debe-313">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="0debe-314">Mikrofon-Status:</span><span class="sxs-lookup"><span data-stu-id="0debe-314">Microphone Status:</span></span> | <span data-ttu-id="0debe-315">20</span><span class="sxs-lookup"><span data-stu-id="0debe-315">20</span></span>           |
        | <span data-ttu-id="0debe-316">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="0debe-316">AzureResponseLabel</span></span>     | <span data-ttu-id="0debe-317">Azure-Web-Antwort</span><span class="sxs-lookup"><span data-stu-id="0debe-317">Azure Web Response</span></span> | <span data-ttu-id="0debe-318">20</span><span class="sxs-lookup"><span data-stu-id="0debe-318">20</span></span>           |
        | <span data-ttu-id="0debe-319">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="0debe-319">DictationLabel</span></span>         |   <span data-ttu-id="0debe-320">Sie gerade gesagt haben:</span><span class="sxs-lookup"><span data-stu-id="0debe-320">You just said:</span></span>   | <span data-ttu-id="0debe-321">20</span><span class="sxs-lookup"><span data-stu-id="0debe-321">20</span></span>           |
        | <span data-ttu-id="0debe-322">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="0debe-322">TranslationResultLabel</span></span> |    <span data-ttu-id="0debe-323">Übersetzung:</span><span class="sxs-lookup"><span data-stu-id="0debe-323">Translation:</span></span>    | <span data-ttu-id="0debe-324">20</span><span class="sxs-lookup"><span data-stu-id="0debe-324">20</span></span>           |

        ![Geben Sie die entsprechenden Werte für die UI-Bezeichnungen.](images/AzureLabs-Lab1-24.png)

    3. <span data-ttu-id="0debe-326">Stellen Sie außerdem den Schriftschnitt **fett**.</span><span class="sxs-lookup"><span data-stu-id="0debe-326">Also, make the Font Style **Bold**.</span></span> <span data-ttu-id="0debe-327">Dadurch wird den Text leichter lesbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="0debe-327">This will make the text easier to read.</span></span>

        ![Fette Schriftart an.](images/AzureLabs-Lab1-25.png)

7.  <span data-ttu-id="0debe-329">Für jede *Benutzeroberflächentext Objekt* in erstellt [Kapitel 5](#chapter-5--create-the-results-class), erstellen Sie ein neues *untergeordneten* **Benutzeroberflächentext Objekt**.</span><span class="sxs-lookup"><span data-stu-id="0debe-329">For each *UI Text object* created in [Chapter 5](#chapter-5--create-the-results-class), create a new *child* **UI Text object**.</span></span> <span data-ttu-id="0debe-330">Diese untergeordneten Elemente werden die Ausgabe der Anwendung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0debe-330">These children will display the output of the application.</span></span> <span data-ttu-id="0debe-331">Erstellen Sie *untergeordneten* Objekte durch einen Rechtsklick auf die vorgesehene übergeordnete Element (z. B. *MicrophoneStatusLabel*) und wählen Sie dann **UI** und wählen Sie dann **Text**.</span><span class="sxs-lookup"><span data-stu-id="0debe-331">Create *child* objects through right-clicking your intended parent (e.g. *MicrophoneStatusLabel*) and then select **UI** and then select **Text**.</span></span>
8.  <span data-ttu-id="0debe-332">Für jedes dieser untergeordneten Steuerelemente, wählen Sie ihn, und verwenden Sie die folgenden Tabellen die Parameter im Bereich Inspector fest.</span><span class="sxs-lookup"><span data-stu-id="0debe-332">For each of these children, select it and use the below tables to set the parameters in the Inspector Panel.</span></span>

    1. <span data-ttu-id="0debe-333">Für die **Rect-Transformation** Komponente:</span><span class="sxs-lookup"><span data-stu-id="0debe-333">For the **Rect Transform** component:</span></span>

        | <span data-ttu-id="0debe-334">Name</span><span class="sxs-lookup"><span data-stu-id="0debe-334">Name</span></span>                  | <span data-ttu-id="0debe-335">Transformieren - *Position*</span><span class="sxs-lookup"><span data-stu-id="0debe-335">Transform - *Position*</span></span> | <span data-ttu-id="0debe-336">Breite</span><span class="sxs-lookup"><span data-stu-id="0debe-336">Width</span></span>      | <span data-ttu-id="0debe-337">Höhe</span><span class="sxs-lookup"><span data-stu-id="0debe-337">Height</span></span>    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | <span data-ttu-id="0debe-338">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="0debe-338">MicrophoneStatusText</span></span>  | <span data-ttu-id="0debe-339">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="0debe-339">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="0debe-340">300</span><span class="sxs-lookup"><span data-stu-id="0debe-340">300</span></span>        | <span data-ttu-id="0debe-341">30</span><span class="sxs-lookup"><span data-stu-id="0debe-341">30</span></span>        |
        | <span data-ttu-id="0debe-342">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="0debe-342">AzureResponseText</span></span>     | <span data-ttu-id="0debe-343">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="0debe-343">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="0debe-344">300</span><span class="sxs-lookup"><span data-stu-id="0debe-344">300</span></span>        | <span data-ttu-id="0debe-345">30</span><span class="sxs-lookup"><span data-stu-id="0debe-345">30</span></span>        |
        | <span data-ttu-id="0debe-346">DictationText</span><span class="sxs-lookup"><span data-stu-id="0debe-346">DictationText</span></span>         | <span data-ttu-id="0debe-347">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="0debe-347">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="0debe-348">300</span><span class="sxs-lookup"><span data-stu-id="0debe-348">300</span></span>        | <span data-ttu-id="0debe-349">30</span><span class="sxs-lookup"><span data-stu-id="0debe-349">30</span></span>        |
        | <span data-ttu-id="0debe-350">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="0debe-350">TranslationResultText</span></span> | <span data-ttu-id="0debe-351">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="0debe-351">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="0debe-352">300</span><span class="sxs-lookup"><span data-stu-id="0debe-352">300</span></span>        | <span data-ttu-id="0debe-353">30</span><span class="sxs-lookup"><span data-stu-id="0debe-353">30</span></span>        |

    2. <span data-ttu-id="0debe-354">Für die **Text (Skript)** Komponente:</span><span class="sxs-lookup"><span data-stu-id="0debe-354">For the **Text (Script)** component:</span></span>

        | <span data-ttu-id="0debe-355">Name</span><span class="sxs-lookup"><span data-stu-id="0debe-355">Name</span></span>                  | <span data-ttu-id="0debe-356">Text</span><span class="sxs-lookup"><span data-stu-id="0debe-356">Text</span></span>          | <span data-ttu-id="0debe-357">Schriftgrad</span><span class="sxs-lookup"><span data-stu-id="0debe-357">Font Size</span></span>    |
        |:---------------------:|:-------------:|:------------:|
        | <span data-ttu-id="0debe-358">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="0debe-358">MicrophoneStatusText</span></span>  |      <span data-ttu-id="0debe-359">??</span><span class="sxs-lookup"><span data-stu-id="0debe-359">??</span></span>       | <span data-ttu-id="0debe-360">20</span><span class="sxs-lookup"><span data-stu-id="0debe-360">20</span></span>           |
        | <span data-ttu-id="0debe-361">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="0debe-361">AzureResponseText</span></span>     |      <span data-ttu-id="0debe-362">??</span><span class="sxs-lookup"><span data-stu-id="0debe-362">??</span></span>       | <span data-ttu-id="0debe-363">20</span><span class="sxs-lookup"><span data-stu-id="0debe-363">20</span></span>           |
        | <span data-ttu-id="0debe-364">DictationText</span><span class="sxs-lookup"><span data-stu-id="0debe-364">DictationText</span></span>         |      <span data-ttu-id="0debe-365">??</span><span class="sxs-lookup"><span data-stu-id="0debe-365">??</span></span>       | <span data-ttu-id="0debe-366">20</span><span class="sxs-lookup"><span data-stu-id="0debe-366">20</span></span>           |
        | <span data-ttu-id="0debe-367">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="0debe-367">TranslationResultText</span></span> |      <span data-ttu-id="0debe-368">??</span><span class="sxs-lookup"><span data-stu-id="0debe-368">??</span></span>       | <span data-ttu-id="0debe-369">20</span><span class="sxs-lookup"><span data-stu-id="0debe-369">20</span></span>           |

9. <span data-ttu-id="0debe-370">Wählen Sie dann die Option zur Ausrichtung "Centre" für jede Textkomponente ein:</span><span class="sxs-lookup"><span data-stu-id="0debe-370">Next, select the 'centre' alignment option for each text component:</span></span>

    ![Ausrichten von Text.](images/AzureLabs-Lab1-26.png)

10. <span data-ttu-id="0debe-372">Um sicherzustellen, dass die **untergeordneten Benutzeroberflächentext** Objekte sind einfach zu lesen, ändern Sie ihre *Farbe*.</span><span class="sxs-lookup"><span data-stu-id="0debe-372">To ensure the **child UI Text** objects are easily readable, change their *Color*.</span></span> <span data-ttu-id="0debe-373">Zu diesem Zweck klicken Sie auf der Leiste (derzeit "Schwarz") weiter, um *Farbe*.</span><span class="sxs-lookup"><span data-stu-id="0debe-373">Do this by clicking on the bar (currently ‘Black’) next to *Color*.</span></span> 

    ![Geben Sie die entsprechenden Werte für die UI-Text-Ausgaben.](images/AzureLabs-Lab1-27.png)
 
11. <span data-ttu-id="0debe-375">Klicken Sie auf das neue, kleine, *Farbe* Ändern der *Hexadezimalfarbe* auf: **0032EAFF**</span><span class="sxs-lookup"><span data-stu-id="0debe-375">Then, in the new, little, *Color* window, change the *Hex Color* to: **0032EAFF**</span></span>

    ![Aktualisieren Sie die Farbe Blau.](images/AzureLabs-Lab1-28.png)
 
12. <span data-ttu-id="0debe-377">Im folgenden finden Sie die **UI** aussehen sollte.</span><span class="sxs-lookup"><span data-stu-id="0debe-377">Below is how the **UI** should look.</span></span>
    1.  <span data-ttu-id="0debe-378">In der *Hierarchie Bereich*:</span><span class="sxs-lookup"><span data-stu-id="0debe-378">In the *Hierarchy Panel*:</span></span>

        ![Hierarchie in der angegebenen Struktur aufweisen.](images/AzureLabs-Lab1-29.png)

    2.  <span data-ttu-id="0debe-380">In der *Szene* und *Ansichten von Spielen*:</span><span class="sxs-lookup"><span data-stu-id="0debe-380">In the *Scene* and *Game Views*:</span></span>

        ![Haben Sie die Szene und der Game-Ansichten in der gleichen Struktur.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a><span data-ttu-id="0debe-382">Kapitel 5 – Erstellen der Ergebnisse-Klasse</span><span class="sxs-lookup"><span data-stu-id="0debe-382">Chapter 5 – Create the Results class</span></span>

<span data-ttu-id="0debe-383">Ist das erste Skript, das Sie erstellen müssen die *Ergebnisse* Klasse, die für die Bereitstellung einer Möglichkeit, die Ergebnisse der Übersetzung finden Sie unter verantwortlich ist.</span><span class="sxs-lookup"><span data-stu-id="0debe-383">The first script you need to create is the *Results* class, which is responsible for providing a way to see the results of translation.</span></span> <span data-ttu-id="0debe-384">Die Klasse speichert, und es wird Folgendes angezeigt:</span><span class="sxs-lookup"><span data-stu-id="0debe-384">The Class stores and displays the following:</span></span> 

- <span data-ttu-id="0debe-385">Das Ergebnis der Antwort von Azure.</span><span class="sxs-lookup"><span data-stu-id="0debe-385">The response result from Azure.</span></span>
- <span data-ttu-id="0debe-386">Der Status des Mikrofons.</span><span class="sxs-lookup"><span data-stu-id="0debe-386">The microphone status.</span></span> 
- <span data-ttu-id="0debe-387">Das Ergebnis der Spracheingaben (Sprache in Text).</span><span class="sxs-lookup"><span data-stu-id="0debe-387">The result of the dictation (voice to text).</span></span>
- <span data-ttu-id="0debe-388">Das Ergebnis der Übersetzung.</span><span class="sxs-lookup"><span data-stu-id="0debe-388">The result of the translation.</span></span>

<span data-ttu-id="0debe-389">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="0debe-389">To create this class:</span></span> 

1.  <span data-ttu-id="0debe-390">Mit der rechten Maustaste den *Projekt Bereich*, klicken Sie dann **erstellen > Ordner**.</span><span class="sxs-lookup"><span data-stu-id="0debe-390">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="0debe-391">Nennen Sie den Ordner **Skripts**.</span><span class="sxs-lookup"><span data-stu-id="0debe-391">Name the folder **Scripts**.</span></span> 
 
    ![Erstellen Sie Ordner "Scripts" an.](images/AzureLabs-Lab1-31.png)

    ![Öffnen Sie den Ordner "Scripts" an.](images/AzureLabs-Lab1-32.png)
 
2.  <span data-ttu-id="0debe-394">Mit der **Skripts** Ordner erstellen, öffnen sie das Doppelklicken.</span><span class="sxs-lookup"><span data-stu-id="0debe-394">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="0debe-395">In diesem Ordner, die mit der rechten Maustaste und wählen Sie dann **erstellen >** dann  **C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="0debe-395">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="0debe-396">Nennen Sie das Skript *Ergebnisse*.</span><span class="sxs-lookup"><span data-stu-id="0debe-396">Name the script *Results*.</span></span> 

    ![Das erste Skript zu erstellen.](images/AzureLabs-Lab1-33.png)
 
3.  <span data-ttu-id="0debe-398">Doppelklicken Sie auf dem neuen *Ergebnisse* Skript öffnen Sie ihn mit **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="0debe-398">Double click on the new *Results* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="0debe-399">Fügen Sie die folgenden Namespaces ein:</span><span class="sxs-lookup"><span data-stu-id="0debe-399">Insert the following namespaces:</span></span>

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  <span data-ttu-id="0debe-400">Fügen Sie in der Klasse die folgenden Variablen:</span><span class="sxs-lookup"><span data-stu-id="0debe-400">Inside the Class insert the following variables:</span></span>

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

6.  <span data-ttu-id="0debe-401">Fügen Sie dann die *Awake()* -Methode, die aufgerufen wird, wenn die Klasse initialisiert.</span><span class="sxs-lookup"><span data-stu-id="0debe-401">Then add the *Awake()* method, which will be called when the class initializes.</span></span> 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  <span data-ttu-id="0debe-402">Schließlich fügen Sie die Methoden, die für die Ausgabe von des Ergebnissen Informationen auf der Benutzeroberfläche zuständig sind.</span><span class="sxs-lookup"><span data-stu-id="0debe-402">Finally, add the methods which are responsible for outputting the various results information to the UI.</span></span> 

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

8.  <span data-ttu-id="0debe-403">Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.</span><span class="sxs-lookup"><span data-stu-id="0debe-403">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-6--create-the-microphonemanager-class"></a><span data-ttu-id="0debe-404">Kapitel 6: Erstellen der *MicrophoneManager* Klasse</span><span class="sxs-lookup"><span data-stu-id="0debe-404">Chapter 6 – Create the *MicrophoneManager* class</span></span>

<span data-ttu-id="0debe-405">Die zweite Klasse, die Sie erstellen wollen ist die *MicrophoneManager*.</span><span class="sxs-lookup"><span data-stu-id="0debe-405">The second class you are going to create is the *MicrophoneManager*.</span></span>

<span data-ttu-id="0debe-406">Diese Klasse ist zuständig für:</span><span class="sxs-lookup"><span data-stu-id="0debe-406">This class is responsible for:</span></span>

- <span data-ttu-id="0debe-407">Erkennen das Aufnahmegerät, die an den Kopfhörer oder die Computer, die (je nachdem, was der Standardeinstellung ist) angefügt.</span><span class="sxs-lookup"><span data-stu-id="0debe-407">Detecting the recording device attached to the headset or machine (whichever is the default).</span></span>
- <span data-ttu-id="0debe-408">Das Audio (Sprache) und Diktat als Zeichenfolge zu speichern.</span><span class="sxs-lookup"><span data-stu-id="0debe-408">Capture the audio (voice) and use dictation to store it as a string.</span></span>
- <span data-ttu-id="0debe-409">Sobald die Stimme angehalten wurde, senden Sie die diktatfunktion, um die Translator-Klasse.</span><span class="sxs-lookup"><span data-stu-id="0debe-409">Once the voice has paused, submit the dictation to the Translator class.</span></span>
- <span data-ttu-id="0debe-410">Hosten Sie eine Methode, die der Sprachaufnahme kann bei Bedarf beenden.</span><span class="sxs-lookup"><span data-stu-id="0debe-410">Host a method that can stop the voice capture if desired.</span></span>

<span data-ttu-id="0debe-411">Diese Klasse zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="0debe-411">To create this class:</span></span> 
1.  <span data-ttu-id="0debe-412">Klicken Sie mit der Doppelklicken auf die **Skripts** Ordner, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="0debe-412">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="0debe-413">Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen > C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="0debe-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="0debe-414">Nennen Sie das Skript *MicrophoneManager*.</span><span class="sxs-lookup"><span data-stu-id="0debe-414">Name the script *MicrophoneManager*.</span></span> 
3.  <span data-ttu-id="0debe-415">Doppelklicken Sie auf das neue Skript aus, um ihn mit Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="0debe-415">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="0debe-416">Aktualisieren Sie die Namespaces, um Folgendes am Anfang entsprechen den *MicrophoneManager* Klasse:</span><span class="sxs-lookup"><span data-stu-id="0debe-416">Update the namespaces to be the same as the following, at the top of the *MicrophoneManager* class:</span></span>

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="0debe-417">Fügen Sie dann die folgenden Variablen in der *MicrophoneManager* Klasse:</span><span class="sxs-lookup"><span data-stu-id="0debe-417">Then, add the following variables inside the *MicrophoneManager* class:</span></span>

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

6.  <span data-ttu-id="0debe-418">Code für die *Awake()* und *Start()* Methoden jetzt hinzugefügt werden muss.</span><span class="sxs-lookup"><span data-stu-id="0debe-418">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="0debe-419">Diese werden aufgerufen, wenn die Klasse initialisiert:</span><span class="sxs-lookup"><span data-stu-id="0debe-419">These will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="0debe-420">Sie können *löschen* der *Update()* Methode, da diese Klasse nicht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="0debe-420">You can *delete* the *Update()* method since this class will not use it.</span></span>
8.  <span data-ttu-id="0debe-421">Jetzt Sie die Methoden, die die App zum Starten benötigen verwendet und Beenden der Sprachaufnahme und übergeben Sie sie an der *Translator* Klasse, die Sie in Kürze erstellen.</span><span class="sxs-lookup"><span data-stu-id="0debe-421">Now you need the methods that the App uses to start and stop the voice capture, and pass it to the *Translator* class, that you will build soon.</span></span> <span data-ttu-id="0debe-422">Kopieren Sie den folgenden Code ein, und fügen Sie ihn unterhalb der *Start()* Methode.</span><span class="sxs-lookup"><span data-stu-id="0debe-422">Copy the following code and paste it beneath the *Start()* method.</span></span>

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
    > <span data-ttu-id="0debe-423">Obwohl diese Anwendung nicht machen werden, verwenden die *StopCapturingAudio()* Methode auch bereitgestellt wurde, sollten Sie die Möglichkeit zum Anhalten, Erfassen von Audiodaten in Ihrer Anwendung implementieren möchten.</span><span class="sxs-lookup"><span data-stu-id="0debe-423">Though this application will not make use of it, the *StopCapturingAudio()* method has also been provided here, should you want to implement the ability to stop capturing audio in your application.</span></span>

9.  <span data-ttu-id="0debe-424">Nun müssen Sie einen Diktat-Handler hinzuzufügen, die aufgerufen wird, wenn die Stimme wird beendet.</span><span class="sxs-lookup"><span data-stu-id="0debe-424">You now need to add a Dictation Handler that will be invoked when the voice stops.</span></span> <span data-ttu-id="0debe-425">Diese Methode übergibt den diktierten Text, klicken Sie dann die *Translator* Klasse.</span><span class="sxs-lookup"><span data-stu-id="0debe-425">This method will then pass the dictated text to the *Translator* class.</span></span>

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

10. <span data-ttu-id="0debe-426">Achten Sie darauf, dass Sie Ihre Änderungen vor der Rückgabe an Unity in Visual Studio zu speichern.</span><span class="sxs-lookup"><span data-stu-id="0debe-426">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

> [!WARNING]  
> <span data-ttu-id="0debe-427">An diesem Punkt werden Sie feststellen, einen Fehler angezeigt werden, der *Unity-Editor-Konsole* Bereich ("der Name"Translator"ist … nicht vorhanden").</span><span class="sxs-lookup"><span data-stu-id="0debe-427">At this point you will notice an error appearing in the *Unity Editor Console* Panel (“The name ‘Translator’ does not exist...”).</span></span> <span data-ttu-id="0debe-428">Dies ist, da der Code verweist auf die *Translator* -Klasse, die Sie im nächsten Kapitel erstellen.</span><span class="sxs-lookup"><span data-stu-id="0debe-428">This is because the code references the *Translator* class, which you will create in the next chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-translator-service"></a><span data-ttu-id="0debe-429">Kapitel 7 – Azure und die Translator-Dienst</span><span class="sxs-lookup"><span data-stu-id="0debe-429">Chapter 7 – Call to Azure and translator service</span></span>

<span data-ttu-id="0debe-430">Ist das letzte Skript Sie müssen die *Translator* Klasse.</span><span class="sxs-lookup"><span data-stu-id="0debe-430">The last script you need to create is the *Translator* class.</span></span> 

<span data-ttu-id="0debe-431">Diese Klasse ist zuständig für:</span><span class="sxs-lookup"><span data-stu-id="0debe-431">This class is responsible for:</span></span>

-   <span data-ttu-id="0debe-432">Die App mit Authentifizierung *Azure*, in exchange für eine **Authentifizierungstoken**.</span><span class="sxs-lookup"><span data-stu-id="0debe-432">Authenticating the App with *Azure*, in exchange for an **Auth Token**.</span></span>
-   <span data-ttu-id="0debe-433">Verwenden der **Authentifizierungstoken** zum Übermitteln von Text (Empfangen von der *MicrophoneManager* Klasse) übersetzt werden.</span><span class="sxs-lookup"><span data-stu-id="0debe-433">Use the **Auth Token** to submit text (received from the *MicrophoneManager* Class) to be translated.</span></span>
-   <span data-ttu-id="0debe-434">Das übersetzte Ergebnis zu erhalten und übergeben es an der *Ergebnisse* Klasse, um in der Benutzeroberfläche visuell dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="0debe-434">Receive the translated result and pass it to the *Results* Class to be visualized in the UI.</span></span>

<span data-ttu-id="0debe-435">Zum Erstellen dieser Klasse:</span><span class="sxs-lookup"><span data-stu-id="0debe-435">To create this Class:</span></span> 
1.  <span data-ttu-id="0debe-436">Wechseln Sie zu der **Skripts** Ordner, die Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="0debe-436">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="0debe-437">Mit der rechten Maustaste den **Projekt Bereich**, **erstellen > C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="0debe-437">Right-click in the **Project Panel**, **Create > C# Script**.</span></span> <span data-ttu-id="0debe-438">Rufen Sie das Skript *Translator*.</span><span class="sxs-lookup"><span data-stu-id="0debe-438">Call the script *Translator*.</span></span>
3.  <span data-ttu-id="0debe-439">Doppelklicken Sie auf dem neuen *Translator* Skript, um ihn zu öffnen **mit Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="0debe-439">Double click on the new *Translator* script to open it **with Visual Studio**.</span></span>
4.  <span data-ttu-id="0debe-440">Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:</span><span class="sxs-lookup"><span data-stu-id="0debe-440">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="0debe-441">Klicken Sie dann fügen Sie die folgenden Variablen in der *Translator* Klasse:</span><span class="sxs-lookup"><span data-stu-id="0debe-441">Then add the following variables inside the *Translator* class:</span></span>

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
    > - <span data-ttu-id="0debe-442">Die Sprachen, die in den Sprachen eingefügt **Enum** sind nur Beispiele.</span><span class="sxs-lookup"><span data-stu-id="0debe-442">The languages inserted into the languages **enum** are just examples.</span></span> <span data-ttu-id="0debe-443">Können Sie mehr hinzufügen, wenn Sie möchten; die [-API unterstützt mehr als 60 Sprachen](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (einschließlich Klingonisch unterscheiden).</span><span class="sxs-lookup"><span data-stu-id="0debe-443">Feel free to add more if you wish; the [API supports over 60 languages](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (including Klingon)!</span></span>
    > - <span data-ttu-id="0debe-444">Gibt es eine [interaktiver Seite, die für verfügbaren Sprachen](https://www.microsoft.com/translator/business/languages/), jedoch bedenken, dass die Seite wird nur angezeigt, funktionieren, wenn die Websitesprache festgelegt ist "En-us (und der Microsoft-Website, die wahrscheinlich Umleitung an Ihre Muttersprache ist).</span><span class="sxs-lookup"><span data-stu-id="0debe-444">There is a [more interactive page covering available languages](https://www.microsoft.com/translator/business/languages/), though be aware the page only appears to work when the site language is set to 'en-us' (and the Microsoft site will likely redirect to your native language).</span></span> <span data-ttu-id="0debe-445">Sie können die Websitesprache am unteren Rand der Seite oder durch Ändern der URL ändern.</span><span class="sxs-lookup"><span data-stu-id="0debe-445">You can change site language at the bottom of the page or by altering the URL.</span></span>
    > - <span data-ttu-id="0debe-446">Die **"authorizationkey"** Wert in der oben stehenden Codeausschnitt muss die **Schlüssel** Sie empfangen wird, wenn Sie abonniert die *Textübersetzungs-API von Azure*.</span><span class="sxs-lookup"><span data-stu-id="0debe-446">The **authorizationKey** value, in the above code snippet, must be the **Key**  you received when you subscribed to the *Azure Translator Text API*.</span></span> <span data-ttu-id="0debe-447">Dies wurde im abgedeckt [Kapitel 1](#chapter-1--the-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="0debe-447">This was covered in [Chapter 1](#chapter-1--the-azure-portal).</span></span>

6.  <span data-ttu-id="0debe-448">Code für die *Awake()* und *Start()* Methoden jetzt hinzugefügt werden muss.</span><span class="sxs-lookup"><span data-stu-id="0debe-448">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> 
7.  <span data-ttu-id="0debe-449">In diesem Fall wird der Code einen Aufruf von stellen *Azure* verwenden die Autorisierung Schlüssel zum Abrufen einer *Token*.</span><span class="sxs-lookup"><span data-stu-id="0debe-449">In this case, the code will make a call to *Azure* using the authorization Key, to get a *Token*.</span></span>

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
    > <span data-ttu-id="0debe-450">Das Token läuft nach 10 Minuten.</span><span class="sxs-lookup"><span data-stu-id="0debe-450">The token will expire after 10 minutes.</span></span> <span data-ttu-id="0debe-451">Je nach Szenario für Ihre app müssen Sie möglicherweise stellen die gleiche Coroutine mehrmals aufrufen.</span><span class="sxs-lookup"><span data-stu-id="0debe-451">Depending on the scenario for your app, you might have to make the same coroutine call multiple times.</span></span>

8.  <span data-ttu-id="0debe-452">Die Coroutine aus, um das Token abzurufen, lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="0debe-452">The coroutine to obtain the Token is the following:</span></span>

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
    > <span data-ttu-id="0debe-453">Wenn Sie den Namen der Methode des IEnumerator bearbeiten **GetTokenCoroutine()**, müssen Sie aktualisieren die *StartCoroutine* und *StopCoroutine* Zeichenfolgenwerte in den obigen Code aufrufen.</span><span class="sxs-lookup"><span data-stu-id="0debe-453">If you edit the name of the IEnumerator method **GetTokenCoroutine()**, you need to update the *StartCoroutine* and *StopCoroutine* call string values in the above code.</span></span> <span data-ttu-id="0debe-454">[Gemäß der Unity-Dokumentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), um einen bestimmten beenden *Coroutine*, müssen Sie die Zeichenfolge-Value-Methode verwenden.</span><span class="sxs-lookup"><span data-stu-id="0debe-454">[As per Unity documentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), to Stop a specific *Coroutine*, you need to use the string value method.</span></span>

9.  <span data-ttu-id="0debe-455">Fügen Sie die Coroutine (mit einer "support" Stream-Methode direkt darunter) zum Abrufen der Übersetzung des Textes von empfangen die *MicrophoneManager* Klasse.</span><span class="sxs-lookup"><span data-stu-id="0debe-455">Next, add the coroutine (with a “support” stream method right below it) to obtain the translation of the text received by the *MicrophoneManager* class.</span></span> <span data-ttu-id="0debe-456">Dieser Code erstellt eine Abfragezeichenfolge an die *Textübersetzungs-API von Azure*, und klicken Sie dann die internen Unity UnityWebRequest-Klasse verwendet, um die ein 'Get' Aufruf an den Endpunkt mit der Abfragezeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="0debe-456">This code creates a query string to send to the *Azure Translator Text API*, and then uses the internal Unity UnityWebRequest class to make a ‘Get’ call to the endpoint with the query string.</span></span> <span data-ttu-id="0debe-457">Das Ergebnis wird dann verwendet, um die Übersetzung in Ihre "Results"-Objekt festzulegen.</span><span class="sxs-lookup"><span data-stu-id="0debe-457">The result is then used to set the translation in your Results object.</span></span> <span data-ttu-id="0debe-458">Der folgende Code zeigt die Implementierung:</span><span class="sxs-lookup"><span data-stu-id="0debe-458">The code below shows the implementation:</span></span>

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

10. <span data-ttu-id="0debe-459">Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.</span><span class="sxs-lookup"><span data-stu-id="0debe-459">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--configure-the-unity-scene"></a><span data-ttu-id="0debe-460">Kapitel 8 – konfigurieren die Unity-Szene</span><span class="sxs-lookup"><span data-stu-id="0debe-460">Chapter 8 – Configure the Unity Scene</span></span>

1.  <span data-ttu-id="0debe-461">Zurück im Unity-Editor, klicken Sie auf, und ziehen Sie die *Ergebnisse* Klasse *aus* der **Skripts** Ordner die **Main Camera** Objekt in der  *Hierarchie-Bereich*.</span><span class="sxs-lookup"><span data-stu-id="0debe-461">Back in the Unity Editor, click and drag the *Results* class *from* the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="0debe-462">Klicken Sie auf die **Main Camera** und sehen Sie sich die *Inspektor Bereich*.</span><span class="sxs-lookup"><span data-stu-id="0debe-462">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="0debe-463">Sie werden feststellen, dass in der neu hinzugefügten *Skript* Komponente, es gibt vier Felder mit leeren Werten.</span><span class="sxs-lookup"><span data-stu-id="0debe-463">You will notice that within the newly added *Script* component, there are four fields with empty values.</span></span> <span data-ttu-id="0debe-464">Hierbei handelt es sich um die Ausgabe-Verweise auf die Eigenschaften im Code.</span><span class="sxs-lookup"><span data-stu-id="0debe-464">These are the output references to the properties in the code.</span></span> 
3.  <span data-ttu-id="0debe-465">Ziehen Sie die entsprechende **Text** Objekte aus der *Hierarchie Bereich* für diese vier Slots, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="0debe-465">Drag the appropriate **Text** objects from the *Hierarchy Panel* to those four slots, as shown in the image below.</span></span>

    ![Aktualisieren Sie Target-Verweise mit angegebenen Werten.](images/AzureLabs-Lab1-34.png)
  
4.  <span data-ttu-id="0debe-467">Als Nächstes klicken und ziehen Sie die *Translator* -Klasse aus der **Skripts** Ordner, um die **Main Camera** -Objekt in der *Hierarchie Bereich*.</span><span class="sxs-lookup"><span data-stu-id="0debe-467">Next, click and drag the *Translator* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
5.  <span data-ttu-id="0debe-468">Klicken Sie dann auf, und ziehen Sie die *MicrophoneManager* -Klasse aus der **Skripts** Ordner, um die **Main Camera** -Objekt in der *Hierarchie Bereich*.</span><span class="sxs-lookup"><span data-stu-id="0debe-468">Then, click and drag the *MicrophoneManager* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
6.  <span data-ttu-id="0debe-469">Klicken Sie abschließend auf die **Main Camera** und sehen Sie sich die *Inspektor Bereich*.</span><span class="sxs-lookup"><span data-stu-id="0debe-469">Lastly, click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="0debe-470">Beachten Sie, dass in das Skript, die, das Sie auf gezogen haben, stehen die beiden Dropdownfelder, die Sie festlegen, die Sprachen ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="0debe-470">You will notice that in the script you dragged on, there are two drop down boxes that will allow you to set the languages.</span></span>
 
    ![Stellen Sie sicher, dass die beabsichtigte übersetzungssprachen eingegeben werden.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a><span data-ttu-id="0debe-472">Kapitel 9 – Testen in mixed reality</span><span class="sxs-lookup"><span data-stu-id="0debe-472">Chapter 9 – Test in mixed reality</span></span>

<span data-ttu-id="0debe-473">An diesem Punkt müssen Sie testen, ob die Szene ordnungsgemäß implementiert wurde.</span><span class="sxs-lookup"><span data-stu-id="0debe-473">At this point you need to test that the Scene has been properly implemented.</span></span>

<span data-ttu-id="0debe-474">Stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="0debe-474">Ensure that:</span></span>

- <span data-ttu-id="0debe-475">Alle Einstellungen, die im erwähnten [Kapitel 1](#chapter-1--the-azure-portal) ordnungsgemäß festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="0debe-475">All the settings mentioned in [Chapter 1](#chapter-1--the-azure-portal) are set correctly.</span></span> 
- <span data-ttu-id="0debe-476">Die *Ergebnisse*, *Translator*, und *MicrophoneManager*, Skripts werden angefügt, um die **Main Camera** Objekt.</span><span class="sxs-lookup"><span data-stu-id="0debe-476">The *Results*, *Translator*, and *MicrophoneManager*, scripts are attached to the **Main Camera** object.</span></span> 
- <span data-ttu-id="0debe-477">Platziert haben Ihre *Textübersetzungs-API von Azure* Service **Schlüssel** innerhalb der **"authorizationkey"** Variablen innerhalb der *Translator* Skript.</span><span class="sxs-lookup"><span data-stu-id="0debe-477">You have placed your *Azure Translator Text API* Service **Key** within the **authorizationKey** variable within the *Translator* Script.</span></span>  
- <span data-ttu-id="0debe-478">Alle Felder in der *Kamera Inspector-Hauptbereich* ordnungsgemäß zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="0debe-478">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
- <span data-ttu-id="0debe-479">Ihr Mikrofon arbeitet bei der Ausführung Ihrer Szene (nicht der Fall, überprüfen Sie, ob das angefügte Mikrofon ist die *Standard* Gerät, und dass Sie [richten sie sie ordnungsgemäß in Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span><span class="sxs-lookup"><span data-stu-id="0debe-479">Your microphone is working when running your scene (if not, check that your attached microphone is the *default* device, and that you have [set it up correctly within Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span></span>

<span data-ttu-id="0debe-480">Sie können die immersive Kopfhörer testen, indem Sie durch Drücken der **spielen** Schaltfläche der *Unity-Editor*.</span><span class="sxs-lookup"><span data-stu-id="0debe-480">You can test the immersive headset by pressing the **Play** button in the *Unity Editor*.</span></span>
<span data-ttu-id="0debe-481">Die App sollte über den angeschlossenen, immersive Kopfhörer funktionsfähig sein.</span><span class="sxs-lookup"><span data-stu-id="0debe-481">The App should be functioning through the attached immersive headset.</span></span>

> [!WARNING]  
> <span data-ttu-id="0debe-482">Wenn einen Fehler in der Unity-Konsole zum Ändern der Standard-Audiogeräts angezeigt wird, funktioniert die Szene möglicherweise nicht wie erwartet.</span><span class="sxs-lookup"><span data-stu-id="0debe-482">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="0debe-483">Dies ist aufgrund der Art, die das mixed Reality-Portal integrierte Mikrofone für Headsets behandelt, die sie verfügen.</span><span class="sxs-lookup"><span data-stu-id="0debe-483">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="0debe-484">Wenn Sie diese Fehlermeldung angezeigt, einfach die Szene zu beenden und neu zu starten und als funktionieren sollte erwartet.</span><span class="sxs-lookup"><span data-stu-id="0debe-484">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a><span data-ttu-id="0debe-485">Kapitel 10 – erstellen Sie die UWP-Projektmappe und das Sideloaden auf dem lokalen Computer</span><span class="sxs-lookup"><span data-stu-id="0debe-485">Chapter 10 – Build the UWP solution and sideload on local machine</span></span>

<span data-ttu-id="0debe-486">Alles, was Sie für den Unity-Abschnitt, der dieses Projekt wurde jetzt abgeschlossen daher ist es Zeit für die Erstellung von Unity.</span><span class="sxs-lookup"><span data-stu-id="0debe-486">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="0debe-487">Navigieren Sie zu **Buildeinstellungen**: **Datei > Buildeinstellungen...**</span><span class="sxs-lookup"><span data-stu-id="0debe-487">Navigate to **Build Settings**: **File > Build Settings...**</span></span>
2.  <span data-ttu-id="0debe-488">Von der **Buildeinstellungen** Fenster, klicken Sie auf **erstellen**.</span><span class="sxs-lookup"><span data-stu-id="0debe-488">From the **Build Settings** window, click **Build**.</span></span>

    ![Die Unity-Szene zu erstellen.](images/AzureLabs-Lab1-36.png)
  
3.  <span data-ttu-id="0debe-490">Falls noch nicht geschehen, aktivieren Sie **Unity C# Projekte**.</span><span class="sxs-lookup"><span data-stu-id="0debe-490">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="0debe-491">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="0debe-491">Click **Build**.</span></span> <span data-ttu-id="0debe-492">Unity startet eine *Datei-Explorer* Fenster, in denen man erstellen, und wählen Sie einen Ordner zum Erstellen der app in.</span><span class="sxs-lookup"><span data-stu-id="0debe-492">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="0debe-493">Erstellen Sie jetzt auf diesen Ordner, und nennen Sie es *App*.</span><span class="sxs-lookup"><span data-stu-id="0debe-493">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="0debe-494">Klicken Sie dann mit der *App* Ordner ausgewählt haben, drücken Sie **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="0debe-494">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="0debe-495">Erstellen Ihres Projekts zu Unity beginnt die *App* Ordner.</span><span class="sxs-lookup"><span data-stu-id="0debe-495">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="0debe-496">Einmal Unity wurde (es kann einige Zeit dauern) erstellen, öffnen ein *Datei-Explorer* Fenster am Speicherort des Builds (Überprüfen Sie Ihre Taskleiste aus, wie es unter Umständen nicht immer über Ihre Windows angezeigt und Sie über das Hinzufügen eines neuen benachrichtigt Fenster ").</span><span class="sxs-lookup"><span data-stu-id="0debe-496">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11--deploy-your-application"></a><span data-ttu-id="0debe-497">Kapitel 11: Stellen Sie die Anwendung</span><span class="sxs-lookup"><span data-stu-id="0debe-497">Chapter 11 – Deploy your application</span></span>

<span data-ttu-id="0debe-498">Um die Anwendung bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="0debe-498">To deploy your application:</span></span>

1.  <span data-ttu-id="0debe-499">Navigieren Sie zu Ihrem neuen Unity-Build (die *App* Ordner), und öffnen Sie die Projektmappendatei mit *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="0debe-499">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
2.  <span data-ttu-id="0debe-500">In der Projektmappenkonfiguration Select **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="0debe-500">In the Solution Configuration select **Debug**.</span></span>
3.  <span data-ttu-id="0debe-501">Wählen Sie in der Plattform für die Projektmappe **X86**, **lokalen Computer**.</span><span class="sxs-lookup"><span data-stu-id="0debe-501">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="0debe-502">Für die Microsoft HoloLens Umständen ist es einfacher, diese Einstellung auf *Remotecomputer*, sodass Sie nicht auf Ihren Computer angeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="0debe-502">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="0debe-503">Allerdings müssen Sie auch die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="0debe-503">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="0debe-504">Kennen der **IP-Adresse** von Ihrem HoloLens, die sich in befinden die *Einstellungen > Netzwerk und Internet > Wi-Fi > Erweiterte Optionen*; IPv4 ist die Adresse, die Sie verwenden sollten.</span><span class="sxs-lookup"><span data-stu-id="0debe-504">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="0debe-505">Stellen Sie sicher *Entwicklermodus* ist **auf**; gefunden in *Einstellungen > Update und Sicherheit > für Entwickler*.</span><span class="sxs-lookup"><span data-stu-id="0debe-505">Ensure *Developer Mode* is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Die Lösung in Visual Studio bereit.](images/AzureLabs-Lab1-37.png)
    
 
4.  <span data-ttu-id="0debe-507">Wechseln Sie zu **Menü "Build"** und klicken Sie auf **Projektmappe bereitstellen** zum querladen der Anwendung auf Ihren PC.</span><span class="sxs-lookup"><span data-stu-id="0debe-507">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>
5.  <span data-ttu-id="0debe-508">Ihre App sollte nun in der Liste der installierten apps, die zu startenden bereit angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="0debe-508">Your App should now appear in the list of installed apps, ready to be launched.</span></span>
6.  <span data-ttu-id="0debe-509">Nachdem gestartet, werden Sie von die App aufgefordert, den Zugriff auf das Mikrofon autorisieren.</span><span class="sxs-lookup"><span data-stu-id="0debe-509">Once launched, the App will prompt you to authorize access to the Microphone.</span></span> <span data-ttu-id="0debe-510">Achten Sie darauf, klicken Sie auf die **Ja** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="0debe-510">Make sure to click the **YES** button.</span></span>
7.  <span data-ttu-id="0debe-511">Sie können nun damit beginnen, übersetzen.</span><span class="sxs-lookup"><span data-stu-id="0debe-511">You are now ready to start translating!</span></span>

## <a name="your-finished-translation-text-api-application"></a><span data-ttu-id="0debe-512">Der fertigen Ausdrucksübersetzungs-Text-API-Anwendung</span><span class="sxs-lookup"><span data-stu-id="0debe-512">Your finished Translation Text API application</span></span>

<span data-ttu-id="0debe-513">Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die die Übersetzung Text-API von Azure konvertieren Sprache in übersetzten Text nutzt.</span><span class="sxs-lookup"><span data-stu-id="0debe-513">Congratulations, you built a mixed reality app that leverages the Azure Translation Text API to convert speech to translated text.</span></span>

![Das Endprodukt.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="0debe-515">Bonus-Übungen</span><span class="sxs-lookup"><span data-stu-id="0debe-515">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="0debe-516">Übung 1</span><span class="sxs-lookup"><span data-stu-id="0debe-516">Exercise 1</span></span>

<span data-ttu-id="0debe-517">Können Sie die Sprachausgabe-Funktion auf die app hinzufügen, damit der zurückgegebene Text gesprochen wird?</span><span class="sxs-lookup"><span data-stu-id="0debe-517">Can you add text-to-speech functionality to the app, so that the returned text is spoken?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="0debe-518">Übung 2</span><span class="sxs-lookup"><span data-stu-id="0debe-518">Exercise 2</span></span>

<span data-ttu-id="0debe-519">Ermöglichen Sie es dem Benutzer, die Quelle und die Ausgabe-Sprachen ("from" und "to") innerhalb der app selbst ändern, damit die app nicht muss neu erstellt werden, jedes Mal, wenn Sie Sprachen ändern möchten.</span><span class="sxs-lookup"><span data-stu-id="0debe-519">Make it possible for the user to change the source and output languages ('from' and 'to') within the app itself, so the app does not need to be rebuilt every time you want to change languages.</span></span>
