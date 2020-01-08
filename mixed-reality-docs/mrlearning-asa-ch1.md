---
title: Tutorials zu Azure Spatial Anchor-1. Ersten Einstieg in Azure Spatial Anchor
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: e62d3626ec6f2dbf8b66378212afab7db2f56422
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334451"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="5afae-105">1. Einstieg in Azure Spatial Anchor</span><span class="sxs-lookup"><span data-stu-id="5afae-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="5afae-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="5afae-106">Overview</span></span>

<span data-ttu-id="5afae-107">Willkommen bei der zweiten Reihe der hololens 2-Tutorials.</span><span class="sxs-lookup"><span data-stu-id="5afae-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="5afae-108">In dieser dreiteiligen tutorialreihe erfahren Sie mehr über die Grundlagen von räumlichen Azure-Ankern.</span><span class="sxs-lookup"><span data-stu-id="5afae-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="5afae-109">In diesem ersten Tutorial, den ersten Schritten [mit räumlichen Azure-Ankern](mrlearning-asa-ch1.md), werden die verschiedenen Schritte erläutert, die zum Starten und Beenden einer Azure-Sitzung sowie zum Erstellen, hochladen und Herunterladen von Azure-Ankern auf einem einzelnen Gerät erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="5afae-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="5afae-110">Im zweiten Tutorial zum [speichern, abrufen und Freigeben von räumlichen Azure-Ankern](mrlearning-asa-ch2.md)erfahren Sie, wie Sie räumliche Azure-Anker in mehreren App-Sitzungen speichern, indem Sie Anker Informationen im Speicher von hololens 2 speichern und diese Anker Informationen für eine Anker Ausrichtung mit mehreren Geräten an andere Geräte weitergeben.</span><span class="sxs-lookup"><span data-stu-id="5afae-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="5afae-111">Im dritten Tutorial, in dem das [Azure Spatial Anchor-Feedback angezeigt](mrlearning-asa-ch3.md)wird, erfahren Sie, wie Sie Benutzern Feedback zu Anker Ereignissen und-Status bei der Verwendung von räumlichen Azure-Ankern bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="5afae-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="5afae-112">Ziele</span><span class="sxs-lookup"><span data-stu-id="5afae-112">Objectives</span></span>

* <span data-ttu-id="5afae-113">Erfahren Sie mehr über die Grundlagen der Entwicklung mit räumlichen Azure-Ankern für hololens 2</span><span class="sxs-lookup"><span data-stu-id="5afae-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="5afae-114">Erstellen, hochladen und herunterladen räumlicher Anker</span><span class="sxs-lookup"><span data-stu-id="5afae-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5afae-115">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="5afae-115">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="5afae-116">Wenn Sie die Reihe "erste Schritte" noch nicht abgeschlossen haben, empfiehlt es sich, [diese Tutorials zuerst](mrlearning-base.md) abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="5afae-116">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="5afae-117">Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md) konfiguriert ist</span><span class="sxs-lookup"><span data-stu-id="5afae-117">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="5afae-118">Windows 10 SDK 10.0.18362.0 oder höher</span><span class="sxs-lookup"><span data-stu-id="5afae-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="5afae-119">Grundlegende C# Programmier Fähigkeit</span><span class="sxs-lookup"><span data-stu-id="5afae-119">Some basic C# programming ability</span></span>
* <span data-ttu-id="5afae-120">Ein hololens 2-Gerät, das [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode) ist</span><span class="sxs-lookup"><span data-stu-id="5afae-120">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="5afae-121">Vervollständigen Sie den Abschnitt [Create a Spatial Anchor Resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) des [Schnellstarts: Erstellen einer Unity hololens-APP, die Azure Spatial](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) Anchor-Tutorial verwendet.</span><span class="sxs-lookup"><span data-stu-id="5afae-121">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>

>[!IMPORTANT]
><span data-ttu-id="5afae-122">Diese tutorialreihe erfordert <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Unity 2019,1</a> und die empfohlene Version ist Unity 2019.1.14.</span><span class="sxs-lookup"><span data-stu-id="5afae-122">This tutorial series requires <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Unity 2019.1</a> and the recommended version is Unity 2019.1.14.</span></span> <span data-ttu-id="5afae-123">Dadurch werden alle Unity-Versions Anforderungen oder-Empfehlungen ersetzt, die in den oben genannten Voraussetzungen angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="5afae-123">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="5afae-124">Erstellen des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="5afae-124">Creating the Unity project</span></span>

<span data-ttu-id="5afae-125">In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und konfigurieren es für Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="5afae-125">In this section, you will create a new Unity project and configure it for Windows Mixed Reality.</span></span>

1. <span data-ttu-id="5afae-126">Erstellen Sie ein Unity-Projekt, und geben Sie ihm einen passenden Namen, z. b. ein _Tutorial für räumliche Azure-Anker_.</span><span class="sxs-lookup"><span data-stu-id="5afae-126">Create a Unity project and give it a suitable name, for example, _Azure Spatial Anchors tutorial_.</span></span>

2. <span data-ttu-id="5afae-127">Konfigurieren Sie das Unity-Projekt für Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="5afae-127">Configure the Unity project for Windows Mixed Reality.</span></span>

    >[!TIP]
    ><span data-ttu-id="5afae-128">Eine Erinnerung zum Erstellen eines Unity-Projekts und zum Konfigurieren des Projekts für Windows Mixed Reality finden Sie in den Abschnitten [Erstellen eines neuen Unity](mrlearning-base-ch1.md#create-new-unity-project) -Projekts und [Konfigurieren des Unity-Projekts für Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) des Tutorials [initialisieren Ihres Projekts und der ersten Anwendung](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) , das Teil [der Reihe "](mrlearning-base.md) erste Schritte" ist.</span><span class="sxs-lookup"><span data-stu-id="5afae-128">For a reminder on how to create a Unity project and configure it for Windows Mixed Reality, you can refer to the [Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and the [Configure the Unity project for Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) sections of the [Initializing your project and first application](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) tutorial which is part of the the [Getting started tutorials](mrlearning-base.md) series.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="5afae-129">Hinzufügen von integrierten Unity-Paketen</span><span class="sxs-lookup"><span data-stu-id="5afae-129">Adding inbuilt Unity packages</span></span>

<span data-ttu-id="5afae-130">In diesem Abschnitt fügen Sie von den Toolkits und SDKs, die Sie im Projekt verwenden werden, integrierte Unity-Ressourcen und Pakete hinzu, die benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="5afae-130">In this section, you will add inbuilt Unity assets and packages required by the toolkits and SDKs you will be using in the project.</span></span>

1. <span data-ttu-id="5afae-131">Importieren Sie wichtige tmp-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="5afae-131">Import TMP Essential Resources.</span></span>

    >[!NOTE]
    ><span data-ttu-id="5afae-132">Wir fügen dieses Paket hinzu, da es für das Mixed Reality Toolkit erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="5afae-132">We are adding this package because it is required by the Mixed Reality Toolkit.</span></span>

    <span data-ttu-id="5afae-133">Wählen Sie im Unity-Menü **Fenster** > **textmeshpro** > **importieren Sie wichtige Ressourcen für tmp**.</span><span class="sxs-lookup"><span data-stu-id="5afae-133">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-2-1.1.png)

    <span data-ttu-id="5afae-135">Vergewissern Sie sich, dass im Popup Fenster des Unity-Pakets importieren zunächst alle Ressourcen ausgewählt werden, indem Sie auf die Schaltfläche **alle** klicken, und importieren Sie dann die Assets, indem Sie auf die Schaltfläche **importieren** klicken.</span><span class="sxs-lookup"><span data-stu-id="5afae-135">In the Import Unity Package pop-up window, first make sure all the assets are selected by clicking the **All** button, then import the assets by clicking the **Import** button.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-2-1.2.png)

2. <span data-ttu-id="5afae-137">Installieren Sie ar Foundation.</span><span class="sxs-lookup"><span data-stu-id="5afae-137">Install AR Foundation.</span></span>

    >[!NOTE]
    ><span data-ttu-id="5afae-138">Wir fügen dieses Paket hinzu, da es für das Azure Spatial Anchor SDK erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="5afae-138">We are adding this package because it is required by the Azure Spatial Anchors SDK.</span></span>

    <span data-ttu-id="5afae-139">Wählen Sie im Unity-Menü die Option **Window** > **Package Manager**aus.</span><span class="sxs-lookup"><span data-stu-id="5afae-139">In the Unity menu, select **Window** > **Package Manager**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-2-2.1.png)

    <span data-ttu-id="5afae-141">Wählen Sie im Fenster Paket-Manager die Option **AR Foundation** aus, und installieren Sie das Paket durch Klicken auf die Schaltfläche **Installieren** .</span><span class="sxs-lookup"><span data-stu-id="5afae-141">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button.</span></span>

    >[!IMPORTANT]
    ><span data-ttu-id="5afae-142">Es kann einige Sekunden dauern, bis das AR Foundation-Paket in der Liste angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="5afae-142">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-2-2.2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="5afae-144">Importieren der tutorialassets</span><span class="sxs-lookup"><span data-stu-id="5afae-144">Importing the tutorial assets</span></span>

<span data-ttu-id="5afae-145">In diesem Abschnitt laden Sie alle tutorialassets herunter und importieren Sie.</span><span class="sxs-lookup"><span data-stu-id="5afae-145">In this section, you will download and import all the tutorial assets.</span></span>

1. <span data-ttu-id="5afae-146">Laden Sie die Assets herunter.</span><span class="sxs-lookup"><span data-stu-id="5afae-146">Download the assets.</span></span>

    * <span data-ttu-id="5afae-147">[Azurespatialanchor. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (Version 2.0.0)</span><span class="sxs-lookup"><span data-stu-id="5afae-147">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (version 2.0.0)</span></span>
    * [<span data-ttu-id="5afae-148">Microsoft. mixedreality. Toolkit. Unity. Foundation. 2.1.0. unitypackage</span><span class="sxs-lookup"><span data-stu-id="5afae-148">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)
    * [<span data-ttu-id="5afae-149">Mrtk. HoloLens2. Unity. Tutorials. Assets. GettingStarted. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="5afae-149">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)
    * [<span data-ttu-id="5afae-150">Mrtk. HoloLens2. Unity. Tutorials. Assets. azurespatialanchor. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="5afae-150">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

2. <span data-ttu-id="5afae-151">Importieren Sie die Objekte.</span><span class="sxs-lookup"><span data-stu-id="5afae-151">Import the assets.</span></span>

    <span data-ttu-id="5afae-152">Wählen Sie im Unity-Menü die Option **Assets** > **Paket** > **benutzerdefiniertes Paket importieren...** aus.</span><span class="sxs-lookup"><span data-stu-id="5afae-152">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-3-2.1.png)

    <span data-ttu-id="5afae-154">Im Paket importieren... Popup Fenster, wählen Sie **azurespatialanchor. unitypackage** aus, und klicken Sie auf die Schaltfläche **Öffnen** .</span><span class="sxs-lookup"><span data-stu-id="5afae-154">In the Import package... pop-up window, select the **AzureSpatialAnchors.unitypackage** and click the **Open** button.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-3-2.2.png)

    <span data-ttu-id="5afae-156">Vergewissern Sie sich, dass im Popup Fenster des Unity-Pakets importieren zunächst alle Ressourcen ausgewählt werden, indem Sie auf die Schaltfläche **alle** klicken, und importieren Sie dann die Assets, indem Sie auf die Schaltfläche **importieren** klicken.</span><span class="sxs-lookup"><span data-stu-id="5afae-156">In the Import Unity Package pop-up window, first make sure all the assets are selected by clicking the **All** button, then import the assets by clicking the **Import** button.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-3-2.3.png)

    <span data-ttu-id="5afae-158">Wiederholen Sie diese Schritte, um die restlichen Asset-Pakete zu importieren.</span><span class="sxs-lookup"><span data-stu-id="5afae-158">Repeat these steps to import the remaining asset packages.</span></span> <span data-ttu-id="5afae-159">Nach Abschluss des Vorgangs sollte der Ordner " **Assets** " Ihres Unity-Projekts diese Unterordner enthalten.</span><span class="sxs-lookup"><span data-stu-id="5afae-159">Once complete, your Unity project's **Assets** folder should contain these sub-folders.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-3-2.4.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="5afae-161">Erstellen und Vorbereiten der Szene</span><span class="sxs-lookup"><span data-stu-id="5afae-161">Creating and preparing the scene</span></span>

<span data-ttu-id="5afae-162">In diesem Abschnitt erstellen und bereiten Sie die Szene vor, indem Sie das Mixed Reality Toolkit und einige der Prefabs für das Tutorial hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5afae-162">In this section, you will create and prepare the scene by adding the Mixed Reality Toolkit and some of the tutorial prefabs.</span></span>

1. <span data-ttu-id="5afae-163">Erstellen Sie eine neue Szene.</span><span class="sxs-lookup"><span data-stu-id="5afae-163">Create a new scene.</span></span>

    <span data-ttu-id="5afae-164">Klicken Sie im Unity-Menü auf **Datei** > **neue Szene**.</span><span class="sxs-lookup"><span data-stu-id="5afae-164">In the Unity menu, select **File** > **New Scene**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-1.1.png)

    <span data-ttu-id="5afae-166">Wählen Sie im Unity-Menü **Datei** > **Speichern unter...** aus.</span><span class="sxs-lookup"><span data-stu-id="5afae-166">In the Unity menu, select **File** > **Save As...**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-1.2.png)

    <span data-ttu-id="5afae-168">Navigieren Sie im Popup Fenster Szene speichern zum Ordner **Szenen** Ihres Projekts, geben Sie Ihrer Szene einen passenden Namen, z. b. _asatutorialscene_, und speichern Sie die Szene, indem Sie auf die Schaltfläche **Speichern** klicken.</span><span class="sxs-lookup"><span data-stu-id="5afae-168">In the Save Scene pop-up window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _ASATutorialScene_, and save the scene by clicking the **Save** button.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-1.3.png)

    >[!TIP]
    ><span data-ttu-id="5afae-170">Sie können die Szene beliebig speichern, solange Sie sich im Ordner "Assets" des Projekts befindet.</span><span class="sxs-lookup"><span data-stu-id="5afae-170">You can save the scene anywhere you like as long as it is inside the project's Assets folder.</span></span> <span data-ttu-id="5afae-171">Um Ihr Projekt jedoch weiterhin zu organisieren, empfiehlt es sich im Allgemeinen, es im Ordner "Szenen" des Projekts zu speichern.</span><span class="sxs-lookup"><span data-stu-id="5afae-171">However, to keep your project organized, it's generally recommended to save it in the project's Scenes folder.</span></span>

2. <span data-ttu-id="5afae-172">Fügen Sie das Mixed Reality Toolkit hinzu.</span><span class="sxs-lookup"><span data-stu-id="5afae-172">Add the Mixed Reality Toolkit.</span></span>

    <span data-ttu-id="5afae-173">Wählen Sie im Unity-Menü **Mixed Reality Toolkit** aus, > **zu Szene hinzufügen und konfigurieren...** .</span><span class="sxs-lookup"><span data-stu-id="5afae-173">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-2.1.png)

    <span data-ttu-id="5afae-175">Klicken Sie im Popup Fenster mixedrealitytoolkitconfigurationprofile auswählen auf **DefaultHoloLens2ConfigurationProfile** , um es als mrtk-Konfigurations Profil für die Szene festzulegen.</span><span class="sxs-lookup"><span data-stu-id="5afae-175">In the Select MixedRealityToolkitConfigurationProfile pop-up window, click the **DefaultHoloLens2ConfigurationProfile** to set it as the scene's MRTK configuration profile.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-2.2.png)

    <span data-ttu-id="5afae-177">Wählen Sie im Unity-Menü **Datei** > **Speichern** aus, um die Szene zu speichern.</span><span class="sxs-lookup"><span data-stu-id="5afae-177">In the Unity menu, select **File** > **Save** to save the scene.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-2.3.png)

    >[!TIP]
    ><span data-ttu-id="5afae-179">Mit der Tastenkombination STRG + s (Command + s unter macOS) können Sie Ihre Szene schnell speichern, während Sie dieses Tutorial durcharbeiten.</span><span class="sxs-lookup"><span data-stu-id="5afae-179">You can use the keyboard shortcut CTRL+S (command + S on macOS) to quickly save your scene as you are working through this tutorial.</span></span>

3. <span data-ttu-id="5afae-180">Fügen Sie das Tutorial "Prefabs" hinzu.</span><span class="sxs-lookup"><span data-stu-id="5afae-180">Add the tutorial prefabs.</span></span>

    <span data-ttu-id="5afae-181">Navigieren Sie im Projekt Panel zu **Assets** > **mrtk. Tutorials. azurespatialanchor** > Ordner " **Prefabs** ".</span><span class="sxs-lookup"><span data-stu-id="5afae-181">In the Project panel, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="5afae-182">Wenn Sie die STRG-Taste gedrückt halten (command on macOS), klicken Sie auf " **buttonparent**", " **debugWindow**" und " **Parser** ", um die drei präfabs auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="5afae-182">While holding down the CTRL button (command on macOS), click on **ButtonParent**, **DebugWindow**, and **ParentAnchor** to select the three prefabs.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-3.1.png)

    <span data-ttu-id="5afae-184">Wenn die drei präfabs noch ausgewählt sind, ziehen Sie Sie in den Hierarchie Bereich, um Sie der Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="5afae-184">With the three prefabs still selected, drag them into the Hierarchy panel to add them to the scene.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-3.2.png)

    <span data-ttu-id="5afae-186">Um sich auf die Objekte in der Szene zu konzentrieren, können Sie auf das Objekt "Objektanchor" doppelklicken und dann wieder etwas vergrößern.</span><span class="sxs-lookup"><span data-stu-id="5afae-186">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-3.3.png)

    >[!TIP]
    ><span data-ttu-id="5afae-188">Wenn Sie die großen Symbole in Ihrer Szene finden, z. b. die großen Symbole, die Sie nicht ablenken, können Sie diese ausblenden, indem Sie <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">die Gizmos</a> an der Position ausschalten.</span><span class="sxs-lookup"><span data-stu-id="5afae-188">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="5afae-189">Konfigurieren der Schaltflächen zum Betreiben der Szene</span><span class="sxs-lookup"><span data-stu-id="5afae-189">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="5afae-190">In diesem Abschnitt fügen Sie Prefabs und Skripts in die Szene ein, um eine Reihe von Schaltflächen zu erstellen, die die Grundlagen der Art und Weise, wie sowohl lokale Anker als auch räumliche Azure-Anker sich in einer Anwendung Verhalten.</span><span class="sxs-lookup"><span data-stu-id="5afae-190">In this section, you will add prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

1. <span data-ttu-id="5afae-191">Konfigurieren Sie die Druck Bare Schaltfläche Holo Lens 2 (Skript).</span><span class="sxs-lookup"><span data-stu-id="5afae-191">Configure the Pressable Button Holo Lens 2 (script) component.</span></span>

    <span data-ttu-id="5afae-192">Erweitern Sie im Hierarchie Panel das **buttonparent** -Objekt, und wählen Sie das erste untergeordnete Objekt mit dem Namen **startazuresession**aus.</span><span class="sxs-lookup"><span data-stu-id="5afae-192">In the Hierarchy panel, expand the **ButtonParent** object and select the first child object named **StartAzureSession**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-1.1.png)

    <span data-ttu-id="5afae-194">Scrollen Sie im Inspektor-Panel nach unten zur **druckbaren Schaltfläche Holo Lens 2 (Script)** , und fügen Sie einen neuen Ereignislistener zum **gedrückten Ereignis ()** hinzu, indem Sie auf das **+** -Symbol klicken.</span><span class="sxs-lookup"><span data-stu-id="5afae-194">In the Inspector panel, scroll down to the **Pressable Button Holo Lens 2 (script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-1.2.png)

    <span data-ttu-id="5afae-196">Wenn das startazuresession-Objekt im Hierarchie Panel noch ausgewählt ist, klicken Sie auf-und ziehen Sie das Objekt " **Objektanker** " aus dem Hierarchie Panel in das leere Feld " **None" (Objekt)** des Ereignislistener, den Sie soeben hinzugefügt haben, um das Objekt "Objektanchor" über diese Schaltfläche zu lauschen.</span><span class="sxs-lookup"><span data-stu-id="5afae-196">With the StartAzureSession object still selected in the Hierarchy panel, click-and-drag the **ParentAnchor** object from the Hierarchy panel into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-1.3.png)

    <span data-ttu-id="5afae-198">Klicken Sie auf die Dropdown Liste **keine Funktion** des gleichen Ereignislistener, und wählen Sie dann **anchormodulescript** > **startazuresession ()** aus, um die startazuresession ()-Funktion als Aktion festzulegen, die ausgelöst wird, wenn die Schaltfläche gedrückte Ereignisse von dieser Schaltfläche ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="5afae-198">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-1.4.png)

2. <span data-ttu-id="5afae-200">Konfigurieren Sie die interactable-Komponente (Skript).</span><span class="sxs-lookup"><span data-stu-id="5afae-200">Configure the Interactable (script) component.</span></span>

    <span data-ttu-id="5afae-201">Wenn das startazuresession-Objekt im Bereich Hierarchie weiterhin ausgewählt ist, Scrollen Sie im Inspektor-Panel nach unten zur Komponente **interactable (Script)** , und wiederholen Sie den gleichen Prozess wie in Schritt 1 oben für das **OnClick ()** -Ereignis.</span><span class="sxs-lookup"><span data-stu-id="5afae-201">With the StartAzureSession object still selected in the Hierarchy panel, in the Inspector panel, scroll down to the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-2.1.png)

3. <span data-ttu-id="5afae-203">Konfigurieren der verbleibenden Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="5afae-203">Configure the remaining buttons</span></span>

    <span data-ttu-id="5afae-204">Schließen Sie für jede der verbleibenden Schaltflächen den in Schritt 1 und 2 beschriebenen Prozess ab, um sowohl den Schaltflächen gedrückten () als auch dem OnClick ()-Ereignis Funktionen zuzuweisen:</span><span class="sxs-lookup"><span data-stu-id="5afae-204">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the Button Pressed () and OnClick () events following:</span></span>

    * <span data-ttu-id="5afae-205">Weisen Sie für das **stopazuresession** -Objekt die **stopazuresession ()** -Funktion zu.</span><span class="sxs-lookup"><span data-stu-id="5afae-205">For the **StopAzureSession** object, assign the **StopAzureSession()** function.</span></span>
    * <span data-ttu-id="5afae-206">Weisen Sie für **das Objekt "das Objekt** " "die Funktion" "die Funktion" Funktion " **()** zu, und ziehen Sie dann die **Komponente" ankeranchor** "erneut in das leere Feld" **None "(Spielobjekt)** .</span><span class="sxs-lookup"><span data-stu-id="5afae-206">For the **CreateAnchor** object, assign the **CreateAzureAnchor()** function, then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
    * <span data-ttu-id="5afae-207">Weisen Sie für das **nach Anker Objekt gesuchte** die **findazureanchor ()** -Funktion zu.</span><span class="sxs-lookup"><span data-stu-id="5afae-207">For the **Start Looking for Anchor** object, assign the **FindAzureAnchor()** function.</span></span>
    * <span data-ttu-id="5afae-208">Weisen Sie für das **Azure Anchor** -Objekt löschen die **deleteazureanchor ()** -Funktion zu.</span><span class="sxs-lookup"><span data-stu-id="5afae-208">For the **Delete Azure Anchor** object, assign the **DeleteAzureAnchor()** function.</span></span>
    * <span data-ttu-id="5afae-209">Weisen Sie für das Objekt **lokalen Anker löschen** die **removelocalanchor ()** -Funktion zu, und ziehen Sie dann den Objektanchor erneut in das leere Feld **None (Game Object)** .</span><span class="sxs-lookup"><span data-stu-id="5afae-209">For the **Delete Local Anchor** object, assign the **RemoveLocalAnchor()** function, then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>

4. <span data-ttu-id="5afae-210">Verbinden der Szene mit der Azure-Ressource</span><span class="sxs-lookup"><span data-stu-id="5afae-210">Connect the scene to the Azure resource</span></span>

    <span data-ttu-id="5afae-211">Wählen Sie im Bereich Hierarchie das Objekt **Objektanker** aus, und Scrollen Sie im Inspektor-Panel nach unten zur Komponente **räumlicher Anker-Manager (Skript)** .</span><span class="sxs-lookup"><span data-stu-id="5afae-211">In the Hierarchy panel, select the **ParentAnchor** object and in the Inspector panel, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

    <span data-ttu-id="5afae-212">Fügen Sie dann im Abschnitt **Anmelde** Informationen Ihre Konto-ID und den Schlüssel für räumliche Anker in die entsprechenden Kontoschlüssel Felder **Konto-ID** und **räumlichkeits** Felder des räumlichen Ankern ein.</span><span class="sxs-lookup"><span data-stu-id="5afae-212">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields.</span></span>

    >[!NOTE]
    ><span data-ttu-id="5afae-213">Sie haben Ihre Konto-ID und den Schlüssel für räumliche Anker im Rahmen der [Voraussetzungen](mrlearning-asa-ch1.md#prerequisites)dieses Tutorials erstellt.</span><span class="sxs-lookup"><span data-stu-id="5afae-213">You created your Spatial Anchors Account Id and Key as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites).</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-4.1.png)

    >[!CAUTION]
    ><span data-ttu-id="5afae-215">Stellen Sie sicher, dass Sie Ihre Szene speichern.</span><span class="sxs-lookup"><span data-stu-id="5afae-215">Make sure you save your scene.</span></span>

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="5afae-216">Grundlegendes Verhalten von räumlichen Azure-Ankern</span><span class="sxs-lookup"><span data-stu-id="5afae-216">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="5afae-217">Nachdem Ihre Szene nun so konfiguriert wurde, dass Sie die Grundlagen von räumlichen Azure-Ankern veranschaulicht, ist es an der Zeit, die APP bereitzustellen, damit Sie Azure Spatial Anchor (erste Schritte) nutzen können.</span><span class="sxs-lookup"><span data-stu-id="5afae-217">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

1. <span data-ttu-id="5afae-218">Fügen Sie zusätzliche erforderliche Funktionen hinzu.</span><span class="sxs-lookup"><span data-stu-id="5afae-218">Add additional required capabilities.</span></span>

    <span data-ttu-id="5afae-219">Wählen Sie im Unity-Menü **Bearbeiten** > **Projekteinstellungen...** aus, um das Fenster mit den Player Einstellungen zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="5afae-219">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings panel.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-6-1.1.png)

    <span data-ttu-id="5afae-221">Wählen Sie im Bereich Player Einstellungen die Option **Player** und dann **Veröffentlichungs Einstellungen**aus.</span><span class="sxs-lookup"><span data-stu-id="5afae-221">In the Player Settings panel, select **Player** and then **Publishing Settings**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-6-1.2.png)

    <span data-ttu-id="5afae-223">Führen Sie in den **Veröffentlichungs Einstellungen**einen Bildlauf nach unten zum Abschnitt **Funktionen** durch, und überprüfen Sie, ob **spatialperception**, das Sie beim Erstellen des Projekts am Anfang des Tutorials aktiviert haben, aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="5afae-223">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that **SpatialPerception**, which you enabled when you created the project at the beginning of the tutorial, is enabled.</span></span> <span data-ttu-id="5afae-224">Anschließend wurden die Funktionen **Internetclient**, **internetclientserver**, **privatenetworkclientserver**, **removablestorage**, **Webcam**und **Mikrofon** aktiviert.</span><span class="sxs-lookup"><span data-stu-id="5afae-224">Then, enabled the **InternetClient**, **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, **Webcam**, and **Microphone** capabilities.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-6-1.3.png)

2. <span data-ttu-id="5afae-226">Stellen Sie die APP auf den hololens 2 bereit.</span><span class="sxs-lookup"><span data-stu-id="5afae-226">Deploy the app to your HoloLens 2.</span></span>

    >[!TIP]
    ><span data-ttu-id="5afae-227">Eine Erinnerung zum Erstellen und Bereitstellen Ihres Unity-Projekts in hololens 2 finden Sie in den Abschnitten Erstellen der [Anwendung auf Ihren Geräten](mrlearning-base-ch1.md#build-your-application-to-your-device) des Tutorials [initialisieren Ihres Projekts und der ersten Anwendung](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) , die Teil der Reihe erste Schritte mit [Tutorials](mrlearning-base.md) ist.</span><span class="sxs-lookup"><span data-stu-id="5afae-227">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) sections of the [Initializing your project and first application](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) tutorial which is part of the the [Getting started tutorials](mrlearning-base.md) series.</span></span>

3. <span data-ttu-id="5afae-228">Führen Sie die APP aus, und befolgen Sie die Anweisungen in der app.</span><span class="sxs-lookup"><span data-stu-id="5afae-228">Run the app and follow the in-app instructions.</span></span>

    >[!CAUTION]
    ><span data-ttu-id="5afae-229">Azure Spatial Anchor verwendet das Internet zum Speichern und Laden der Anker Daten, damit sichergestellt ist, dass Ihr Gerät mit dem Internet verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="5afae-229">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

    <span data-ttu-id="5afae-230">Wenn die Anwendung auf Ihrem Gerät ausgeführt wird, befolgen Sie die Anweisungen auf dem Bildschirm, die im **Azure Spatial Anchor Module instructions** -Panel angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5afae-230">When the application is running on your device, follow the on-screen instructions displayed on the **Azure Spatial Anchor Module Instructions** panel.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-6-3.1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="5afae-232">Verankern eines Erlebnisses</span><span class="sxs-lookup"><span data-stu-id="5afae-232">Anchoring an experience</span></span>

<span data-ttu-id="5afae-233">In den vorherigen Abschnitten haben Sie die Grundlagen von räumlichen Azure-Ankern kennengelernt.</span><span class="sxs-lookup"><span data-stu-id="5afae-233">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="5afae-234">Wir haben einen Cube verwendet, um das übergeordnete Spielobjekt mit dem angefügten Anker darzustellen und zu visualisieren.</span><span class="sxs-lookup"><span data-stu-id="5afae-234">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="5afae-235">In diesem Abschnitt erfahren Sie, wie Sie eine vollständige-Funktion verankern können, indem Sie Sie als untergeordnetes Element des Objektanchor-Objekts platzieren.</span><span class="sxs-lookup"><span data-stu-id="5afae-235">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

1. <span data-ttu-id="5afae-236">Fügen Sie das Launcher-Start Programm hinzu.</span><span class="sxs-lookup"><span data-stu-id="5afae-236">Add the Rocket Launcher experience.</span></span>

    <span data-ttu-id="5afae-237">Navigieren Sie im Projekt Panel zu **Assets** > **mrtk. Tutorials. GettingStarted** > Ordner " **Prefabs** ", und wählen Sie die **Launcher_Complete** vorfab aus.</span><span class="sxs-lookup"><span data-stu-id="5afae-237">In the Project panel, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder and select the **Rocket Launcher_Complete** prefab.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-7-1.1.png)

    <span data-ttu-id="5afae-239">Ziehen Sie bei aktivierter aufruppe Launcher_Complete die Option "Prefab" auf das Objekt " **Objektanchor** " im Hierarchie Panel, um es zu einem untergeordneten Element des Objekts "Objekt Anker" zu machen.</span><span class="sxs-lookup"><span data-stu-id="5afae-239">With the Rocket Launcher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy panel to make it a child of the ParentAnchor object.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-7-1.2.png)

2. <span data-ttu-id="5afae-241">Positionieren Sie das Launcher-Start Programm neu.</span><span class="sxs-lookup"><span data-stu-id="5afae-241">Reposition the Rocket Launcher experience.</span></span>

    <span data-ttu-id="5afae-242">Verschieben Sie das Modul mit dem **Launcher_Complete** Objekt, damit das **Objekt (der** Cube) noch verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="5afae-242">Move module **Rocket Launcher_Complete** object so that the **ParentAnchor** (the cube) is still exposed.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-7-2.1.png)

    <span data-ttu-id="5afae-244">In der Anwendung kann es sein, dass Benutzer die gesamte Benutzeroberflächen-Start Programm Darstellung neu positionieren, indem Sie den Cube verschieben.</span><span class="sxs-lookup"><span data-stu-id="5afae-244">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

    >[!TIP]
    ><span data-ttu-id="5afae-245">Es gibt eine Vielzahl von Benutzeroberflächen Abläufen für die Neupositionierung, einschließlich der Verwendung eines neu positionierenden Objekts (z. b. des in diesem Tutorial verwendeten Cubes), der Verwendung einer Schaltfläche zum Umschalten eines umgebenden Felds, das die Oberfläche umgibt, der Verwendung von Position und Drehung. Gizmos und mehr.</span><span class="sxs-lookup"><span data-stu-id="5afae-245">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="5afae-246">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="5afae-246">Congratulations</span></span>

<span data-ttu-id="5afae-247">In diesem Tutorial haben Sie die Grundlagen von räumlichen Azure-Ankern kennengelernt.</span><span class="sxs-lookup"><span data-stu-id="5afae-247">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="5afae-248">In dieser Lektion haben Sie mehrere Schaltflächen zur Verfügung gestellt, mit denen Sie die verschiedenen Schritte zum Starten und Beenden einer Azure-Sitzung sowie zum Erstellen, hochladen und Herunterladen von Azure-Ankern auf einem einzelnen Gerät untersuchen können</span><span class="sxs-lookup"><span data-stu-id="5afae-248">This Lesson provided you with several buttons that let you  explore the various steps required to start and stop an Azure session and create, upload and download azure anchors on a single device.</span></span>

<span data-ttu-id="5afae-249">In der nächsten Lektion erfahren Sie, wie Sie Azure-Anker-IDs für den Abruf in den hololens 2 speichern, auch nachdem die Anwendung neu gestartet wurde, und wie Anker-IDs zwischen mehreren Geräten übertragen werden, um eine räumliche Ausrichtung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="5afae-249">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="5afae-250">Nächste Lektion: 2. speichern, abrufen und Freigeben von räumlichen Azure-Ankern</span><span class="sxs-lookup"><span data-stu-id="5afae-250">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
