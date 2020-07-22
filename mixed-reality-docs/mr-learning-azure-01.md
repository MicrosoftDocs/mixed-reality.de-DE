---
title: Azure-Cloudtutorials – 1. Azure Cloud Services für HoloLens 2
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie verschiedene Azure-Dienste innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Azure, Mixed Reality, Unity, Tutorial, HoloLens, HoloLens 2, Azure Blob Storage, Azure Table Storage, Azure Spatial Anchor, Azure Bot Framework
ms.localizationpriority: high
ms.openlocfilehash: 649046f9416c880d6e69b544866fba60d3e43f4c
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304979"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a><span data-ttu-id="f4eed-105">1. Azure Cloud Services für HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f4eed-105">1. Azure Cloud Services for HoloLens 2</span></span>

## <a name="overview"></a><span data-ttu-id="f4eed-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="f4eed-106">Overview</span></span>

<span data-ttu-id="f4eed-107">Willkommen zu dieser Reihe von Tutorials, die sich darauf konzentrieren, **Azure Cloud Services** in eine **HoloLens 2** Anwendung einzubinden.</span><span class="sxs-lookup"><span data-stu-id="f4eed-107">Welcome to this series of tutorials focused on bringing **Azure Cloud** services into a **HoloLens 2** application.</span></span> <span data-ttu-id="f4eed-108">In dieser fünfteiligen Tutorialserie erfahren Sie, wie Sie mehrere **Azure Cloud Services** in ein **Unity**-Projekt für **HoloLens 2** integrieren können.</span><span class="sxs-lookup"><span data-stu-id="f4eed-108">In this five-part tutorial series, you will learn how to integrate several **Azure Cloud** services into a **Unity** project for **HoloLens 2**.</span></span> <span data-ttu-id="f4eed-109">Mit jedem weiteren Kapitel fügen Sie neue **Azure Cloud Services** hinzu, um die Anwendungsfunktionen und die Benutzererfahrung zu erweitern, während Sie die Grundlagen jedes **Azure Cloud Service** kennenlernen.</span><span class="sxs-lookup"><span data-stu-id="f4eed-109">With each consecutive chapter, you will add new **Azure Cloud** services to expand the application features and user experience, while teaching you the fundamentals of each **Azure Cloud** service.</span></span>

> [!NOTE]
> <span data-ttu-id="f4eed-110">Diese Tutorialserie konzentriert sich auf **HoloLens 2**, aber aufgrund des plattformübergreifenden Charakters von Unity gelten die meisten Lerninhalte auch für Desktop- und Smartphoneanwendungen.</span><span class="sxs-lookup"><span data-stu-id="f4eed-110">This tutorial series will focus on the **HoloLens 2** but due the cross-platform nature of Unity, most of your learnings will also apply for Desktop and Smartphone applications.</span></span>

<span data-ttu-id="f4eed-111">In diesem ersten Tutorial, [Einführung in Azure Cloud Services für HoloLens 2](mr-learning-azure-01.md), erläutern Sie zunächst die Ziele der Anwendung, machen sich kurz mit den einzelnen Azure Cloud Services vertraut und richten das Unity-Projekt ein.</span><span class="sxs-lookup"><span data-stu-id="f4eed-111">In this first tutorial, [Introducing Azure Cloud Services for HoloLens 2](mr-learning-azure-01.md), you begin by explaining the goals of the application, briefly introduce you to each Azure Cloud service and set up the unity project.</span></span>

<span data-ttu-id="f4eed-112">Im zweiten Tutorial, [Integrieren von Azure Storage](mr-learning-azure-02.md), beginnen Sie mit der Integration von Azure Storage als Persistenzlösung für die Demoanwendung, lernen die Unterschiede zwischen Blob Storage und Table Storage kennen, bereiten die benötigten Projektressourcen vor, richten die Szene ein und überprüfen die Vorgänge zum Lesen, Aktualisieren und Löschen von Daten.</span><span class="sxs-lookup"><span data-stu-id="f4eed-112">In the second tutorial, [Integrating Azure Storage](mr-learning-azure-02.md), you start off by integrating Azure Storage as the persistence solution for the demo application, learn the differences between Blob Storage and Table Storage, prepare the needed project resources, setup the scene and verify the read, update and delete data operations.</span></span>

<span data-ttu-id="f4eed-113">Im dritten Tutorial, [Integrieren von Azure Custom Vision](mr-learning-azure-03.md), verwenden Sie Azure Custom Vision zum Trainieren und Erkennen von Bildern in der HoloLens 2-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="f4eed-113">Continuing with the third tutorial, [Integrating Azure Custom Vision](mr-learning-azure-03.md), you will use Azure Custom Vision to train and detect images in the HoloLens 2 application.</span></span> <span data-ttu-id="f4eed-114">Das Kapitel beginnt mit dem Einrichten Ihrer eigenen Azure Custom Vision-Ressource, dem Vorbereiten der Szenekomponenten und der Umsetzung durch Trainieren und Erkennen Ihrer eigenen Bilder aus der Anwendung heraus.</span><span class="sxs-lookup"><span data-stu-id="f4eed-114">The chapter starts off with setting up your own Azure Custom Vision resource, preparing the scene components and getting into action by training and detecting your own images from inside the application.</span></span>

<span data-ttu-id="f4eed-115">Im vierten Tutorial, [Integrieren von Azure Spatial Anchors](mr-learning-azure-04.md), fahren Sie fort, indem Sie den Azure Spatial Anchors-Dienst erkunden, um Positionen zu speichern und zu finden. Sie lernen die grundlegenden Konzepte kennen, bereiten die erforderlichen Ressourcen vor, richten die Szene ein und verwenden das neue Feature in der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="f4eed-115">Next you advance in the fourth tutorial, [Integrating Azure Spatial Anchors](mr-learning-azure-04.md), with exploring Azure Spatial Anchors service to save and find locations, learn the core concepts, prepare necessary resources, setup the scene and start using the new feature in the application.</span></span>

<span data-ttu-id="f4eed-116">Im fünften Tutorial, [Integrieren von Azure Bot Service mit LUIS](mr-learning-azure-05.md), finalisieren Sie die vorherigen Schritte, indem Sie der Anwendung eine neue Methode für die Benutzerinteraktion zur Verfügung stellen: natürliche Sprache!</span><span class="sxs-lookup"><span data-stu-id="f4eed-116">With the fifth tutorial, [Integrating Azure Bot Service with LUIS](mr-learning-azure-05.md), you finalize by giving the application a new method of user interaction: natural language!</span></span> <span data-ttu-id="f4eed-117">Diese Funktion wird durch die Verwendung von Azure Bot Framework und Language Understanding (LUIS) umgesetzt.</span><span class="sxs-lookup"><span data-stu-id="f4eed-117">This feature will be realized by using the Azure Bot Framework together with Language Understanding (LUIS).</span></span> <span data-ttu-id="f4eed-118">In diesem letzten Kapitel werden die Grundlagen von Azure Bot Service erläutert, und Sie erfahren, wie Sie den Prozess beschleunigen können, indem Sie Bot Framework Composer als codefreie Lösung verwenden.</span><span class="sxs-lookup"><span data-stu-id="f4eed-118">This final chapter teaches you the basics of Azure Bot Service and to speed up the process you will be using the Bot Framework Composer as a zero code solution.</span></span> <span data-ttu-id="f4eed-119">Nachdem der Bot erstellt wurde, integrieren Sie ihn in die Szene und führen ihn mit der letzten Phase der HoloLens 2-Anwendung aus.</span><span class="sxs-lookup"><span data-stu-id="f4eed-119">Once the bot is created, you will integrate it into the scene and give it a run with the final stage of the HoloLens 2 application.</span></span>

## <a name="application-goals"></a><span data-ttu-id="f4eed-120">Anwendungsziele</span><span class="sxs-lookup"><span data-stu-id="f4eed-120">Application goals</span></span>

<span data-ttu-id="f4eed-121">In dieser Tutorialserie erstellen Sie eine **HoloLens 2** Anwendung, mit der Objekte aus Bildern erkannt und die räumliche Position gefunden werden kann.</span><span class="sxs-lookup"><span data-stu-id="f4eed-121">In this tutorial series, you will build a **HoloLens 2** application that can detect objects from images and find its spatial location.</span></span> <span data-ttu-id="f4eed-122">Um einen Fachbegriff festzulegen, nennen wir diese Entitäten von nun an **nachverfolgtes Objekt**.</span><span class="sxs-lookup"><span data-stu-id="f4eed-122">To set a domain language, you call such entities from now **Tracked Object**.</span></span>
<span data-ttu-id="f4eed-123">Der Benutzer kann ein **nachverfolgtes Objekt** erstellen, indem er entweder eine Reihe von Bildern über maschinelles Sehen und/oder eine räumliche Position zuordnet.</span><span class="sxs-lookup"><span data-stu-id="f4eed-123">The user can create a **Tracked Object** to either or both associate a set of images via computer vision and/or a spatial location.</span></span> <span data-ttu-id="f4eed-124">Alle Daten müssen in der Cloud persistent gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="f4eed-124">All data must be persisted into the cloud.</span></span> <span data-ttu-id="f4eed-125">Darüber hinaus werden einige Aspekte der Anwendung optional durch natürliche Spracheingaben gesteuert, die über einen Bot unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="f4eed-125">Furthermore some aspects of the application will be optionally controlled by natural language assisted through a bot.</span></span>

### <a name="features"></a><span data-ttu-id="f4eed-126">Features</span><span class="sxs-lookup"><span data-stu-id="f4eed-126">Features</span></span>

* <span data-ttu-id="f4eed-127">Grundlegende Verwaltung von Daten und Bildern</span><span class="sxs-lookup"><span data-stu-id="f4eed-127">Basic managing of data and images</span></span>
* <span data-ttu-id="f4eed-128">Bildtraining und -erkennung</span><span class="sxs-lookup"><span data-stu-id="f4eed-128">Image training and detection</span></span>
* <span data-ttu-id="f4eed-129">Speichern einer räumlichen Position sowie zugehörige Anleitungen</span><span class="sxs-lookup"><span data-stu-id="f4eed-129">Storing a spatial location and guidance to it</span></span>
* <span data-ttu-id="f4eed-130">Bot-Assistent, um einige Features über natürliche Sprache zu nutzen</span><span class="sxs-lookup"><span data-stu-id="f4eed-130">Bot assistant to use some features via natural language</span></span>

## <a name="azure-cloud-services"></a><span data-ttu-id="f4eed-131">Azure Cloud Services</span><span class="sxs-lookup"><span data-stu-id="f4eed-131">Azure Cloud services</span></span>

<span data-ttu-id="f4eed-132">Um die erforderlichen Features für die Anwendung bereitzustellen, verwenden Sie die folgenden **Azure Cloud** Services:</span><span class="sxs-lookup"><span data-stu-id="f4eed-132">To solve the required features for the application, you will use these **Azure Cloud** services:</span></span>

### <a name="azure-storage"></a><span data-ttu-id="f4eed-133">Azure Storage</span><span class="sxs-lookup"><span data-stu-id="f4eed-133">Azure Storage</span></span>

<span data-ttu-id="f4eed-134">Sie verwenden [Azure Storage](https://azure.microsoft.com/services/storage/) für die Persistenzlösung.</span><span class="sxs-lookup"><span data-stu-id="f4eed-134">You will use [Azure Storage](https://azure.microsoft.com/services/storage/) for the persistence solution.</span></span> <span data-ttu-id="f4eed-135">Der Dienst ermöglicht es Ihnen, Daten in einer Tabelle zu speichern und große Binärdateien wie Bilder hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="f4eed-135">It allows you to store data on a table and upload large binaries like images.</span></span>

### <a name="azure-custom-vision"></a><span data-ttu-id="f4eed-136">Azure Custom Vision</span><span class="sxs-lookup"><span data-stu-id="f4eed-136">Azure Custom Vision</span></span>

<span data-ttu-id="f4eed-137">Mit [Azure Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (Teil von [Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)) können Sie *nachverfolgten Objekten* eine Gruppe von Bildern zuordnen, ein Machine Learning-Modell für diese Gruppe trainieren und das *nachverfolgte Objekt* erkennen.</span><span class="sxs-lookup"><span data-stu-id="f4eed-137">With [Azure Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (part of the [Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)) you can associate to *Tracked Objects* a set of images, train a machine learning model on the set and detect the *Tracked Object*.</span></span>

### <a name="azure-spatial-anchors"></a><span data-ttu-id="f4eed-138">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="f4eed-138">Azure Spatial Anchors</span></span>

<span data-ttu-id="f4eed-139">Um die Position eines *nachverfolgten Objekts* zu speichern und eine Anleitung zur Suche zu erhalten, verwenden Sie [Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/).</span><span class="sxs-lookup"><span data-stu-id="f4eed-139">To store a *Tracked Object* location and give a guided directions to find it, you use [Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

### <a name="azure-bot-service"></a><span data-ttu-id="f4eed-140">Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="f4eed-140">Azure Bot Service</span></span>

<span data-ttu-id="f4eed-141">Die Anwendung wird hauptsächlich durch herkömmliche Benutzeroberfläche gesteuert, sodass Sie [Azure Bot Service](https://azure.microsoft.com/services/bot-service/) verwenden, um etwas mehr Persönlichkeit hinzuzufügen und eine neue Interaktionsmethode einzuführen.</span><span class="sxs-lookup"><span data-stu-id="f4eed-141">The application is mainly driven by traditional UI, so you use the [Azure Bot Service](https://azure.microsoft.com/services/bot-service/) to add some personality and act as a new interaction method.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f4eed-142">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="f4eed-142">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="f4eed-143">Wenn Sie die Reihe [Tutorials zu den ersten Schritten](mr-learning-base-01.md) noch nicht abgeschlossen haben, empfiehlt es sich, zunächst diese Tutorials abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="f4eed-143">If you have not completed the [Getting started tutorials](mr-learning-base-01.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="f4eed-144">Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](install-the-tools.md) ist</span><span class="sxs-lookup"><span data-stu-id="f4eed-144">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="f4eed-145">Windows 10 SDK (10.0.18362.0 oder höher)</span><span class="sxs-lookup"><span data-stu-id="f4eed-145">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="f4eed-146">Grundlagenkenntnisse in der C#-Programmierung</span><span class="sxs-lookup"><span data-stu-id="f4eed-146">Some basic C# programming ability</span></span>
* <span data-ttu-id="f4eed-147">Ein für die [Entwicklung konfiguriertes](using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät</span><span class="sxs-lookup"><span data-stu-id="f4eed-147">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="f4eed-148">Eine verbundene Webcam, wenn Sie über den Unity-Editor testen möchten</span><span class="sxs-lookup"><span data-stu-id="f4eed-148">A connected webcam if you like to test from Unity editor</span></span>
* <span data-ttu-id="f4eed-149"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.3.X und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform</span><span class="sxs-lookup"><span data-stu-id="f4eed-149"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="f4eed-150">Die empfohlene Unity-Version für diese Tutorialreihe ist Unity 2019.3.X.</span><span class="sxs-lookup"><span data-stu-id="f4eed-150">The recommended Unity version for this tutorial series is Unity 2019.3.X.</span></span> <span data-ttu-id="f4eed-151">Diese übertrifft alle Versionsanforderungen oder -empfehlungen, die in den oben verlinkten Voraussetzungen angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="f4eed-151">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="f4eed-152">Erstellen und Vorbereiten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="f4eed-152">Creating and preparing the Unity project</span></span>

<span data-ttu-id="f4eed-153">In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die MRTK-Entwicklung vor.</span><span class="sxs-lookup"><span data-stu-id="f4eed-153">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="f4eed-154">Befolgen Sie zu diesem Zweck zunächst die Anweisungen unter [Initialisieren des Projekts und der ersten Anwendung](mr-learning-base-02.md), jedoch ohne die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihrem Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2), die die folgenden Schritte beinhalten:</span><span class="sxs-lookup"><span data-stu-id="f4eed-154">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="f4eed-155">[Erstellen des Unity-Projekts](mr-learning-base-02.md#creating-the-unity-project), das mit einem passenden Namen bezeichnet wird, beispielsweise *Azure-Cloudtutorials*</span><span class="sxs-lookup"><span data-stu-id="f4eed-155">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *Azure Cloud Tutorials*</span></span>
2. [<span data-ttu-id="f4eed-156">Wechseln der Buildplattform</span><span class="sxs-lookup"><span data-stu-id="f4eed-156">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
3. [<span data-ttu-id="f4eed-157">Importieren der TextMeshPro Essential-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="f4eed-157">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="f4eed-158">Importieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="f4eed-158">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="f4eed-159">Konfigurieren des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="f4eed-159">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
6. <span data-ttu-id="f4eed-160">[Erstellen und Konfigurieren der Szene](mr-learning-base-02.md#creating-and-configuring-the-scene) und Bezeichnen der Szene mit einem passenden Namen, z. B. *AzureCloudServices*</span><span class="sxs-lookup"><span data-stu-id="f4eed-160">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureCloudServices*</span></span>

<span data-ttu-id="f4eed-161">Befolgen Sie dann die Anweisungen unter [Ändern der Anzeigeoption der räumlichen Wahrnehmung](mr-learning-base-03.md#changing-the-spatial-awareness-display-option), um das **DefaultHoloLens2ConfigurationProfile** als MRTK-Konfigurationsprofil für Ihre Szene festzulegen, und ändern Sie die Anzeigeoptionen für das Gittermodell zur räumlichen Wahrnehmung in **Occlusion** (Verdeckung).</span><span class="sxs-lookup"><span data-stu-id="f4eed-161">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="f4eed-162">Installieren von integrierten Unity-Paketen</span><span class="sxs-lookup"><span data-stu-id="f4eed-162">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="f4eed-163">Wählen Sie im Unity-Menü **Fenster** > **Package Manager** (Paket-Manager) aus, um das Fenster „Package Manager“ zu öffnen, wählen Sie **AR Foundation** aus, und klicken Sie auf die Schaltfläche **Install** (Installieren), um das Paket zu installieren:</span><span class="sxs-lookup"><span data-stu-id="f4eed-163">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![mr-learning-azure](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="f4eed-165">Sie installieren das AR Foundation-Paket, da es für das Azure Spatial Anchor SDK erforderlich ist, das Sie im nächsten Abschnitt importieren.</span><span class="sxs-lookup"><span data-stu-id="f4eed-165">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="f4eed-166">Importieren der Tutorialressourcen</span><span class="sxs-lookup"><span data-stu-id="f4eed-166">Importing the tutorial assets</span></span>

<span data-ttu-id="f4eed-167">Laden Sie die folgenden benutzerdefinierten Unity-Pakete herunter, und **importieren** Sie sie **in der Reihenfolge, in der sie aufgelistet sind**:</span><span class="sxs-lookup"><span data-stu-id="f4eed-167">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="f4eed-168">Azure Storage für Unity</span><span class="sxs-lookup"><span data-stu-id="f4eed-168">Azure storage for Unity</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureStorageForUnity.unitypackage)
* [<span data-ttu-id="f4eed-169">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="f4eed-169">Azure Spatial Anchors</span></span>](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage)
* [<span data-ttu-id="f4eed-170">MRTK.Tutorials.AzureCloudServices</span><span class="sxs-lookup"><span data-stu-id="f4eed-170">MRTK.Tutorials.AzureCloudServices</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/MRTK.Tutorials.AzureCloudServices.unitypackage)

> [!TIP]
> <span data-ttu-id="f4eed-171">Wenn Sie eine Auffrischung zum Importieren eines benutzerdefinierten Unity-Pakets benötigen, lesen Sie die Anweisungen unter [Importieren des Mixed Reality-Toolkits](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="f4eed-171">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="f4eed-172">Nach dem Importieren der Tutorialressourcen sollte Ihr Projektfenster ähnlich wie die folgende Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="f4eed-172">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section4-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="f4eed-174">Erstellen und Vorbereiten der Szene</span><span class="sxs-lookup"><span data-stu-id="f4eed-174">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="f4eed-175">In diesem Abschnitt bereiten Sie die Szene vor, indem Sie einige der Tutorial-Prefabs hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f4eed-175">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="f4eed-176">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**.</span><span class="sxs-lookup"><span data-stu-id="f4eed-176">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span> <span data-ttu-id="f4eed-177">Klicken Sie mit gedrückter STRG-Taste auf **SceneController**, **RootMenu** und **DataManager**, um die drei Prefabs auszuwählen:</span><span class="sxs-lookup"><span data-stu-id="f4eed-177">While holding down the CTRL button, click on **SceneController**, **RootMenu** and **DataManager** to select the three prefabs:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-1.png)

<span data-ttu-id="f4eed-179">**SceneController (Prefab)** enthält zwei Skripts: **SceneController (Script)** und **UnityDispatcher (Script)** .</span><span class="sxs-lookup"><span data-stu-id="f4eed-179">The **SceneController (prefab)** contains two scripts, **SceneController (script)** and **UnityDispatcher (script)**.</span></span> <span data-ttu-id="f4eed-180">Die **SceneController**-Skriptkomponente enthält mehrere UX-Funktionen und ermöglicht die Fotoerfassungsfunktionalität, während **UnityDispatcher** eine Hilfsklasse ist, um Execute-Aktionen für den Unity-Hauptthread zuzulassen.</span><span class="sxs-lookup"><span data-stu-id="f4eed-180">The **SceneController** script component contains several UX functions and facilitates the photo capture functionality while **UnityDispatcher** is a helper class to allow execute actions on the Unity main thread.</span></span>

<span data-ttu-id="f4eed-181">**RootMenu (Prefab)** ist das primäre UI-Prefab, das alle Benutzeroberflächenfenster enthält, die über verschiedene kleine Skriptkomponenten miteinander verbunden sind und den allgemeinen UX-Fluss der Anwendung steuern.</span><span class="sxs-lookup"><span data-stu-id="f4eed-181">The **RootMenu (prefab)** is the primary UI prefab that holds all UI windows that are connected to each other through various small script components and control the general UX flow of the application.</span></span>

<span data-ttu-id="f4eed-182">**DataManager (Prefab)** ist für die Kommunikation mit Azure Storage zuständig und wird im nächsten Tutorial ausführlicher erläutert.</span><span class="sxs-lookup"><span data-stu-id="f4eed-182">The **DataManager (prefab)** is responsible for talking to Azure storage and will be explained further in the next tutorial.</span></span>

<span data-ttu-id="f4eed-183">Ziehen Sie die drei noch ausgewählten Prefabs nun auf das Hierarchiefenster, um sie der Szene hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="f4eed-183">Now with the three prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-2.png)

<span data-ttu-id="f4eed-185">Um sich auf die Objekte in der Szene zu konzentrieren, können Sie auf das **RootMenu**-Objekt doppelklicken und die Ansicht dann etwas verkleinern:</span><span class="sxs-lookup"><span data-stu-id="f4eed-185">To focus in on the objects in the scene, you can double-click on the **RootMenu** object, and then zoom slightly out again:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> <span data-ttu-id="f4eed-187">Wenn Sie die großen Symbole in Ihrer Szene, beispielsweise die mit großen Rahmen umgebenen 'T'-Symbole, irritierend finden, können Sie diese ausblenden, indem Sie <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">die Gizmos umschalten</a> (in die Aus-Position).</span><span class="sxs-lookup"><span data-stu-id="f4eed-187">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-scene"></a><span data-ttu-id="f4eed-188">Konfigurieren der Szene</span><span class="sxs-lookup"><span data-stu-id="f4eed-188">Configuring the scene</span></span>

<span data-ttu-id="f4eed-189">In diesem Abschnitt verbinden Sie *SceneManager*, *DataManager* und *RootMenu*, um eine funktionierende Szene zu erhalten, die für das folgende Tutorial [Integrieren von Azure Storage](mr-learning-azure-01.md) bereit ist.</span><span class="sxs-lookup"><span data-stu-id="f4eed-189">In this section, you will connect *SceneManager*, *DataManager* and *RootMenu* together to have a working scene to be ready for the following [Integrating Azure storage](mr-learning-azure-01.md) tutorial.</span></span>

### <a name="connect-the-objects"></a><span data-ttu-id="f4eed-190">Verbinden der Objekte</span><span class="sxs-lookup"><span data-stu-id="f4eed-190">Connect the objects</span></span>

<span data-ttu-id="f4eed-191">Wählen Sie im Hierarchiefenster das **DataManager**-Objekt aus:</span><span class="sxs-lookup"><span data-stu-id="f4eed-191">In the Hierarchy window, select the **DataManager** object:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-1.png)

<span data-ttu-id="f4eed-193">Suchen Sie im Inspektor-Fenster die Komponente **DataManager (Script)** . Sie sehen einen leeren Slot für das Ereignis **On Data Manager Ready ()** .</span><span class="sxs-lookup"><span data-stu-id="f4eed-193">In the Inspector window, locate the **DataManager (Script)** component and you will see an empty slot on the **On Data Manager Ready ()** event.</span></span> <span data-ttu-id="f4eed-194">Ziehen Sie nun das **SceneController**-Objekt aus dem Hierarchiefenster in das **On Data Manager Ready ()** -Ereignis.</span><span class="sxs-lookup"><span data-stu-id="f4eed-194">Now from the Hierarchy window drag the **SceneController** object into the **On Data Manager Ready ()** event.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-2.png)

<span data-ttu-id="f4eed-196">Sie werden feststellen, dass das Dropdownmenü des Ereignisses aktiviert wurde. Klicken Sie auf das Dropdownmenü, navigieren Sie zu **SceneController**, und wählen Sie im Untermenü die Option **Init ()** aus:</span><span class="sxs-lookup"><span data-stu-id="f4eed-196">You will notice that the dropdown menu of the event became active, click on the dropdown menu and navigate to **SceneController** and in the sub menu select the **Init ()** option:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-3.png)

<span data-ttu-id="f4eed-198">Wählen Sie im Hierarchyfenster das **SceneController**-Objekt aus. Im Inspektor finden Sie dort die Komponente **SceneController (Script)** .</span><span class="sxs-lookup"><span data-stu-id="f4eed-198">From the Hierarchy window, select the **SceneController** object, there in the Inspector you will find the **SceneController** (script) component.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-4.png)

<span data-ttu-id="f4eed-200">Sie werden feststellen, dass es mehrere nicht mit Daten aufgefüllte Felder gibt. Ändern Sie dies nun.</span><span class="sxs-lookup"><span data-stu-id="f4eed-200">You will see that there are several unpopulated fields, let's change that.</span></span> <span data-ttu-id="f4eed-201">Verschieben Sie das **DataManager**-Objekt aus der Hierarchie in das Feld *Data Manager*, und verschieben Sie das **RootMenu**-GameObject aus der Hierarchie in das Feld *Main Menu* (Hauptmenü).</span><span class="sxs-lookup"><span data-stu-id="f4eed-201">Move the **DataManager** object from the Hierarchy into the *Data Manager* field and move the **RootMenu** GameObject from the Hierarchy into the *Main Menu* field.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-5.png)

<span data-ttu-id="f4eed-203">Ihre Szene ist nun für die bevorstehenden Tutorials bereit.</span><span class="sxs-lookup"><span data-stu-id="f4eed-203">Now your scene is ready for the upcoming tutorials.</span></span> <span data-ttu-id="f4eed-204">Vergessen Sie nicht, sie in Ihrem Projekt zu speichern.</span><span class="sxs-lookup"><span data-stu-id="f4eed-204">Don't forget to save it into your project.</span></span>

## <a name="prepare-project-build-pipeline"></a><span data-ttu-id="f4eed-205">Vorbereiten der Projektbuildpipeline</span><span class="sxs-lookup"><span data-stu-id="f4eed-205">Prepare project build pipeline</span></span>

<span data-ttu-id="f4eed-206">Obwohl das Projekt noch mit Inhalt gefüllt werden muss, müssen Sie einige Vorbereitungen treffen, damit das Projekt für den Buildvorgang für **HoloLens 2** bereit ist.</span><span class="sxs-lookup"><span data-stu-id="f4eed-206">While the project yet has to be filled with content, you have to perform some preparations, so the project is ready for building for **HoloLens 2**.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="f4eed-207">1. Hinzufügen zusätzlicher erforderlicher Funktionen</span><span class="sxs-lookup"><span data-stu-id="f4eed-207">1. Add additional required capabilities</span></span>

<span data-ttu-id="f4eed-208">Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen...) aus, um das Fenster „Project Settings“ (Projekteinstellungen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="f4eed-208">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-1.png)

<span data-ttu-id="f4eed-210">Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) die Option **Player** und dann **Publishing Settings** (Veröffentlichungseinstellungen) aus:</span><span class="sxs-lookup"><span data-stu-id="f4eed-210">In the Project Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-2.png)

<span data-ttu-id="f4eed-212">Scrollen Sie in den **Publishing Settings** nach unten zum Abschnitt **Capabilities** (Funktionen), und vergewissern Sie sich, dass die Funktionen **InternetClient**, **Microphone** und **SpatialPerception**, die Sie im Rahmen der Erstellung des Projekts zu Beginn des Tutorials erstellt haben, aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="f4eed-212">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone** and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="f4eed-213">Aktivieren Sie dann die Funktionen **InternetClientServer**, **PrivateNetworkClientServer** und **Webcam**:</span><span class="sxs-lookup"><span data-stu-id="f4eed-213">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, and **Webcam** capabilities:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="f4eed-215">2. Bereitstellen der App auf Ihrer HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f4eed-215">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="f4eed-216">Nicht alle Funktionen, die Sie in dieser Tutorialreihe verwenden werden, können innerhalb des Unity-Editors ausgeführt werden. Dies bedeutet, dass Sie mit der Bereitstellung der Anwendung auf Ihrem HoloLens 2-Gerät vertraut sein müssen.</span><span class="sxs-lookup"><span data-stu-id="f4eed-216">Not all features that you will use in this tutorial series can run inside the Unity editor, this means that you need to be familiar with deploying the application to your HoloLens 2 device.</span></span>

> [!TIP]
> <span data-ttu-id="f4eed-217">Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie in den Tutorials mit den ersten Schritten die Anweisungen unter [Erstellen Ihrer Anwendung auf Ihrem Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="f4eed-217">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Getting started tutorials - Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="f4eed-218">3. Führen Sie die App auf Ihrer HoloLens 2 aus, und folgen Sie den Anweisungen in der App</span><span class="sxs-lookup"><span data-stu-id="f4eed-218">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="f4eed-219">Alle Azure-Dienste verwenden das Internet. Stellen Sie daher sicher, dass Ihr Gerät mit dem Internet verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="f4eed-219">All Azure Services uses the internet, so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="f4eed-220">Wenn die Anwendung auf Ihrem Gerät ausgeführt wird, stimmen Sie dem Zugriff auf die folgenden angeforderten Funktionen zu:</span><span class="sxs-lookup"><span data-stu-id="f4eed-220">When the application is running on your device, accept access to the following requested capabilities:</span></span>

* <span data-ttu-id="f4eed-221">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="f4eed-221">Microphone</span></span>
* <span data-ttu-id="f4eed-222">Kamera</span><span class="sxs-lookup"><span data-stu-id="f4eed-222">Camera</span></span>

<span data-ttu-id="f4eed-223">Diese Funktionen sind für Dienste wie *Chat Bot* und *Custom Vision* erforderlich, damit diese ordnungsgemäß funktionieren.</span><span class="sxs-lookup"><span data-stu-id="f4eed-223">These capabilities are required for services like *Chat Bot* and *Custom Vision* to function properly.</span></span>

## <a name="congratulations"></a><span data-ttu-id="f4eed-224">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="f4eed-224">Congratulations</span></span>

<span data-ttu-id="f4eed-225">In diesem Tutorial wurde Ihnen die Tutorialreihe vorgestellt, Sie haben erfahren, welche Funktionen Sie implementieren und wie **Azure Cloud** Services an die Realisierung Ihrer *HoloLens  2*-Anwendung anknüpfen.</span><span class="sxs-lookup"><span data-stu-id="f4eed-225">In this tutorial, you were introduced to the tutorial series, learned about the features you will implement and how **Azure Cloud** services tie in to making your *HoloLens 2* application happen.</span></span> <span data-ttu-id="f4eed-226">Sie haben dem Projekt die erforderlichen Komponenten hinzugefügt und die Szene für diese Tutorialreihe vorbereitet.</span><span class="sxs-lookup"><span data-stu-id="f4eed-226">You added the required components into the project and prepared the scene for this tutorial series.</span></span>

<span data-ttu-id="f4eed-227">In der nächsten Lektion verwenden Sie Azure Storage als cloudbasierte Persistenzlösung zum Speichern von Daten und Bildern.</span><span class="sxs-lookup"><span data-stu-id="f4eed-227">In the next lesson, you will use Azure storage as a cloud based persistence solution for storing data and images.</span></span>

[<span data-ttu-id="f4eed-228">Nächstes Tutorial: 2. Integrieren von Azure Storage</span><span class="sxs-lookup"><span data-stu-id="f4eed-228">Next tutorial: 2. Integrating Azure storage</span></span>](mr-learning-azure-02.md)
