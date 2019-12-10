---
title: Tutorials zu Azure Spatial Anchor-1. Ersten Einstieg in Azure Spatial Anchor
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 861c42f9449fcb3cf038258af91088fc927941e5
ms.sourcegitcommit: f4812e1312c4751a22a2de56771c475b22a4ba24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2019
ms.locfileid: "74940978"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="23443-105">1. Einstieg in Azure Spatial Anchor</span><span class="sxs-lookup"><span data-stu-id="23443-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="23443-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="23443-106">Overview</span></span>

<span data-ttu-id="23443-107">Willkommen bei der zweiten Reihe der hololens 2-Tutorials.</span><span class="sxs-lookup"><span data-stu-id="23443-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="23443-108">In dieser dreiteiligen tutorialreihe erfahren Sie mehr über die Grundlagen von räumlichen Azure-Ankern.</span><span class="sxs-lookup"><span data-stu-id="23443-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="23443-109">In diesem ersten Tutorial, den ersten Schritten [mit räumlichen Azure-Ankern](mrlearning-asa-ch1.md), werden die verschiedenen Schritte erläutert, die zum Starten und Beenden einer Azure-Sitzung sowie zum Erstellen, hochladen und Herunterladen von Azure-Ankern auf einem einzelnen Gerät erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="23443-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="23443-110">Im zweiten Tutorial zum [speichern, abrufen und Freigeben von räumlichen Azure-Ankern](mrlearning-asa-ch2.md)erfahren Sie, wie Sie räumliche Azure-Anker in mehreren App-Sitzungen speichern, indem Sie Anker Informationen im Speicher von hololens 2 speichern und diese Anker Informationen für eine Anker Ausrichtung mit mehreren Geräten an andere Geräte weitergeben.</span><span class="sxs-lookup"><span data-stu-id="23443-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="23443-111">Im dritten Tutorial, in dem das [Azure Spatial Anchor-Feedback angezeigt](mrlearning-asa-ch3.md)wird, erfahren Sie, wie Sie Benutzern Feedback zu Anker Ereignissen und-Status bei der Verwendung von räumlichen Azure-Ankern bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="23443-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="23443-112">Ziele</span><span class="sxs-lookup"><span data-stu-id="23443-112">Objectives</span></span>

* <span data-ttu-id="23443-113">Erfahren Sie mehr über die Grundlagen der Entwicklung mit räumlichen Azure-Ankern für hololens 2</span><span class="sxs-lookup"><span data-stu-id="23443-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="23443-114">Erstellen, hochladen und herunterladen räumlicher Anker</span><span class="sxs-lookup"><span data-stu-id="23443-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="23443-115">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="23443-115">Prerequisites</span></span>

* <span data-ttu-id="23443-116">Erfüllen Sie die Anforderungen, die im Abschnitt " [Voraussetzungen](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#prerequisites) " des Tutorials [Schnellstart: Erstellen einer Unity hololens-APP, die Azure Spatial Anchor verwendet,](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="23443-116">Meet the requirements listed in the [Prerequisites](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#prerequisites) section of the  [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>
* <span data-ttu-id="23443-117">Vervollständigen Sie den Abschnitt [Create a Spatial Anchor Resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) des [Schnellstarts: Erstellen einer Unity hololens-APP, die Azure Spatial](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) Anchor-Tutorial verwendet.</span><span class="sxs-lookup"><span data-stu-id="23443-117">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>
* <span data-ttu-id="23443-118">Wenn Sie die Reihe "erste Schritte" noch nicht abgeschlossen haben, empfiehlt es sich, [diese Tutorials zuerst](mrlearning-base.md) abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="23443-118">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="23443-119">Erstellen des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="23443-119">Creating the Unity project</span></span>

<span data-ttu-id="23443-120">In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und konfigurieren es für Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="23443-120">In this section, you will create a new Unity project and configure it for Windows Mixed Reality.</span></span>

1. <span data-ttu-id="23443-121">Erstellen Sie ein Unity-Projekt, und geben Sie ihm einen passenden Namen, z. b. ein _Tutorial für räumliche Azure-Anker_.</span><span class="sxs-lookup"><span data-stu-id="23443-121">Create a Unity project and give it a suitable name, for example, _Azure Spatial Anchors tutorial_.</span></span>

2. <span data-ttu-id="23443-122">Konfigurieren Sie das Unity-Projekt für Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="23443-122">Configure the Unity project for Windows Mixed Reality.</span></span>

    >[!TIP]
    ><span data-ttu-id="23443-123">Eine Erinnerung zum Erstellen eines Unity-Projekts und zum Konfigurieren des Projekts für Windows Mixed Reality finden Sie in den Abschnitten [Erstellen eines neuen Unity](mrlearning-base-ch1.md#create-new-unity-project) -Projekts und [Konfigurieren des Unity-Projekts für Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) des Tutorials [initialisieren Ihres Projekts und der ersten Anwendung](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) , das Teil [der Reihe "](mrlearning-base.md) erste Schritte" ist.</span><span class="sxs-lookup"><span data-stu-id="23443-123">For a reminder on how to create a Unity project and configure it for Windows Mixed Reality, you can refer to the [Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and the [Configure the Unity project for Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) sections of the [Initializing your project and first application](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) tutorial which is part of the the [Getting started tutorials](mrlearning-base.md) series.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="23443-124">Hinzufügen von integrierten Unity-Paketen</span><span class="sxs-lookup"><span data-stu-id="23443-124">Adding inbuilt Unity packages</span></span>

<span data-ttu-id="23443-125">In diesem Abschnitt fügen Sie von den Toolkits und SDKs, die Sie im Projekt verwenden werden, integrierte Unity-Ressourcen und Pakete hinzu, die benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="23443-125">In this section, you will add inbuilt Unity assets and packages required by the toolkits and SDKs you will be using in the project.</span></span>

1. <span data-ttu-id="23443-126">Importieren Sie wichtige tmp-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="23443-126">Import TMP Essential Resources.</span></span>

    >[!NOTE]
    ><span data-ttu-id="23443-127">Wir fügen dieses Paket hinzu, da es für das Mixed Reality Toolkit erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="23443-127">We are adding this package because it is required by the Mixed Reality Toolkit.</span></span>

    <span data-ttu-id="23443-128">Wählen Sie im Unity-Menü **Fenster** > **textmeshpro** > **importieren Sie wichtige Ressourcen für tmp**.</span><span class="sxs-lookup"><span data-stu-id="23443-128">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-2-1.1.png)

    <span data-ttu-id="23443-130">Vergewissern Sie sich, dass im Popup Fenster des Unity-Pakets importieren zunächst alle Ressourcen ausgewählt werden, indem Sie auf die Schaltfläche **alle** klicken, und importieren Sie dann die Assets, indem Sie auf die Schaltfläche **importieren** klicken.</span><span class="sxs-lookup"><span data-stu-id="23443-130">In the Import Unity Package pop-up window, first make sure all the assets are selected by clicking the **All** button, then import the assets by clicking the **Import** button.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-2-1.2.png)

2. <span data-ttu-id="23443-132">Installieren Sie ar Foundation.</span><span class="sxs-lookup"><span data-stu-id="23443-132">Install AR Foundation.</span></span>

    >[!NOTE]
    ><span data-ttu-id="23443-133">Wir fügen dieses Paket hinzu, da es für das Azure Spatial Anchor SDK erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="23443-133">We are adding this package because it is required by the Azure Spatial Anchors SDK.</span></span>

    <span data-ttu-id="23443-134">Wählen Sie im Unity-Menü die Option **Window** > **Package Manager**aus.</span><span class="sxs-lookup"><span data-stu-id="23443-134">In the Unity menu, select **Window** > **Package Manager**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-2-2.1.png)

    <span data-ttu-id="23443-136">Wählen Sie im Fenster Paket-Manager die Option **AR Foundation** aus, und installieren Sie das Paket durch Klicken auf die Schaltfläche **Installieren** .</span><span class="sxs-lookup"><span data-stu-id="23443-136">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button.</span></span>

    >[!IMPORTANT]
    ><span data-ttu-id="23443-137">Es kann einige Sekunden dauern, bis das AR Foundation-Paket in der Liste angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="23443-137">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-2-2.2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="23443-139">Importieren der tutorialassets</span><span class="sxs-lookup"><span data-stu-id="23443-139">Importing the tutorial assets</span></span>

<span data-ttu-id="23443-140">In diesem Abschnitt laden Sie alle tutorialassets herunter und importieren Sie.</span><span class="sxs-lookup"><span data-stu-id="23443-140">In this section, you will download and import all the tutorial assets.</span></span>

1. <span data-ttu-id="23443-141">Laden Sie die Assets herunter.</span><span class="sxs-lookup"><span data-stu-id="23443-141">Download the assets.</span></span>

    * <span data-ttu-id="23443-142">[Azurespatialanchor. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (Version 2.0.0)</span><span class="sxs-lookup"><span data-stu-id="23443-142">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (version 2.0.0)</span></span>
    * [<span data-ttu-id="23443-143">Microsoft. mixedreality. Toolkit. Unity. Foundation. 2.1.0. unitypackage</span><span class="sxs-lookup"><span data-stu-id="23443-143">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)
    * [<span data-ttu-id="23443-144">Mrtk. HoloLens2. Unity. Tutorials. Assets. GettingStarted. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="23443-144">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)
    * [<span data-ttu-id="23443-145">Mrtk. HoloLens2. Unity. Tutorials. Assets. azurespatialanchor. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="23443-145">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

2. <span data-ttu-id="23443-146">Importieren Sie die Objekte.</span><span class="sxs-lookup"><span data-stu-id="23443-146">Import the assets.</span></span>

    <span data-ttu-id="23443-147">Wählen Sie im Unity-Menü die Option **Assets** > **Paket** > **benutzerdefiniertes Paket importieren...** aus.</span><span class="sxs-lookup"><span data-stu-id="23443-147">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-3-2.1.png)

    <span data-ttu-id="23443-149">Im Paket importieren... Popup Fenster, wählen Sie **azurespatialanchor. unitypackage** aus, und klicken Sie auf die Schaltfläche **Öffnen** .</span><span class="sxs-lookup"><span data-stu-id="23443-149">In the Import package... pop-up window, select the **AzureSpatialAnchors.unitypackage** and click the **Open** button.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-3-2.2.png)

    <span data-ttu-id="23443-151">Vergewissern Sie sich, dass im Popup Fenster des Unity-Pakets importieren zunächst alle Ressourcen ausgewählt werden, indem Sie auf die Schaltfläche **alle** klicken, und importieren Sie dann die Assets, indem Sie auf die Schaltfläche **importieren** klicken.</span><span class="sxs-lookup"><span data-stu-id="23443-151">In the Import Unity Package pop-up window, first make sure all the assets are selected by clicking the **All** button, then import the assets by clicking the **Import** button.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-3-2.3.png)

    <span data-ttu-id="23443-153">Wiederholen Sie diese Schritte, um die restlichen Asset-Pakete zu importieren.</span><span class="sxs-lookup"><span data-stu-id="23443-153">Repeat these steps to import the remaining asset packages.</span></span> <span data-ttu-id="23443-154">Nach Abschluss des Vorgangs sollte der Ordner " **Assets** " Ihres Unity-Projekts diese Unterordner enthalten.</span><span class="sxs-lookup"><span data-stu-id="23443-154">Once complete, your Unity project's **Assets** folder should contain these sub-folders.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-3-2.4.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="23443-156">Erstellen und Vorbereiten der Szene</span><span class="sxs-lookup"><span data-stu-id="23443-156">Creating and preparing the scene</span></span>

<span data-ttu-id="23443-157">In diesem Abschnitt erstellen und bereiten Sie die Szene vor, indem Sie das Mixed Reality Toolkit und einige der Prefabs für das Tutorial hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="23443-157">In this section, you will create and prepare the scene by adding the Mixed Reality Toolkit and some of the tutorial prefabs.</span></span>

1. <span data-ttu-id="23443-158">Erstellen Sie eine neue Szene.</span><span class="sxs-lookup"><span data-stu-id="23443-158">Create a new scene.</span></span>

    <span data-ttu-id="23443-159">Klicken Sie im Unity-Menü auf **Datei** > **neue Szene**.</span><span class="sxs-lookup"><span data-stu-id="23443-159">In the Unity menu, select **File** > **New Scene**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-1.1.png)

    <span data-ttu-id="23443-161">Wählen Sie im Unity-Menü **Datei** > **Speichern unter...** aus.</span><span class="sxs-lookup"><span data-stu-id="23443-161">In the Unity menu, select **File** > **Save As...**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-1.2.png)

    <span data-ttu-id="23443-163">Navigieren Sie im Popup Fenster Szene speichern zum Ordner **Szenen** Ihres Projekts, geben Sie Ihrer Szene einen passenden Namen, z. b. _asatutorialscene_, und speichern Sie die Szene, indem Sie auf die Schaltfläche **Speichern** klicken.</span><span class="sxs-lookup"><span data-stu-id="23443-163">In the Save Scene pop-up window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _ASATutorialScene_, and save the scene by clicking the **Save** button.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-1.3.png)

    >[!TIP]
    ><span data-ttu-id="23443-165">Sie können die Szene beliebig speichern, solange Sie sich im Ordner "Assets" des Projekts befindet.</span><span class="sxs-lookup"><span data-stu-id="23443-165">You can save the scene anywhere you like as long as it is inside the project's Assets folder.</span></span> <span data-ttu-id="23443-166">Um Ihr Projekt jedoch weiterhin zu organisieren, empfiehlt es sich im Allgemeinen, es im Ordner "Szenen" des Projekts zu speichern.</span><span class="sxs-lookup"><span data-stu-id="23443-166">However, to keep your project organized, it's generally recommended to save it in the project's Scenes folder.</span></span>

2. <span data-ttu-id="23443-167">Fügen Sie das Mixed Reality Toolkit hinzu.</span><span class="sxs-lookup"><span data-stu-id="23443-167">Add the Mixed Reality Toolkit.</span></span>

    <span data-ttu-id="23443-168">Wählen Sie im Unity-Menü **Mixed Reality Toolkit** aus, > **zu Szene hinzufügen und konfigurieren...** .</span><span class="sxs-lookup"><span data-stu-id="23443-168">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-2.1.png)

    <span data-ttu-id="23443-170">Klicken Sie im Popup Fenster mixedrealitytoolkitconfigurationprofile auswählen auf **DefaultHoloLens2ConfigurationProfile** , um es als mrtk-Konfigurations Profil für die Szene festzulegen.</span><span class="sxs-lookup"><span data-stu-id="23443-170">In the Select MixedRealityToolkitConfigurationProfile pop-up window, click the **DefaultHoloLens2ConfigurationProfile** to set it as the scene's MRTK configuration profile.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-2.2.png)

    <span data-ttu-id="23443-172">Wählen Sie im Unity-Menü **Datei** > **Speichern** aus, um die Szene zu speichern.</span><span class="sxs-lookup"><span data-stu-id="23443-172">In the Unity menu, select **File** > **Save** to save the scene.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-2.3.png)

    >[!TIP]
    ><span data-ttu-id="23443-174">Mit der Tastenkombination STRG + s (Command + s unter macOS) können Sie Ihre Szene schnell speichern, während Sie dieses Tutorial durcharbeiten.</span><span class="sxs-lookup"><span data-stu-id="23443-174">You can use the keyboard shortcut CTRL+S (command + S on macOS) to quickly save your scene as you are working through this tutorial.</span></span>

3. <span data-ttu-id="23443-175">Fügen Sie das Tutorial "Prefabs" hinzu.</span><span class="sxs-lookup"><span data-stu-id="23443-175">Add the tutorial prefabs.</span></span>

    <span data-ttu-id="23443-176">Navigieren Sie im Projekt Panel zu **Assets** > **mrtk. Tutorials. azurespatialanchor** > Ordner " **Prefabs** ".</span><span class="sxs-lookup"><span data-stu-id="23443-176">In the Project panel, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="23443-177">Wenn Sie die STRG-Taste gedrückt halten (command on macOS), klicken Sie auf " **buttonparent**", " **debugWindow**" und " **Parser** ", um die drei präfabs auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="23443-177">While holding down the CTRL button (command on macOS), click on **ButtonParent**, **DebugWindow**, and **ParentAnchor** to select the three prefabs.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-3.1.png)

    <span data-ttu-id="23443-179">Wenn die drei präfabs noch ausgewählt sind, ziehen Sie Sie in den Hierarchie Bereich, um Sie der Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="23443-179">With the three prefabs still selected, drag them into the Hierarchy panel to add them to the scene.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-3.2.png)

    <span data-ttu-id="23443-181">Um sich auf die Objekte in der Szene zu konzentrieren, können Sie auf das Objekt "Objektanchor" doppelklicken und dann wieder etwas vergrößern.</span><span class="sxs-lookup"><span data-stu-id="23443-181">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-3.3.png)

    >[!TIP]
    ><span data-ttu-id="23443-183">Wenn Sie die großen Symbole in Ihrer Szene finden, z. b. die großen Symbole, die Sie nicht ablenken, können Sie diese ausblenden, indem Sie <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">die Gizmos</a> an der Position ausschalten.</span><span class="sxs-lookup"><span data-stu-id="23443-183">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="23443-184">Konfigurieren der Schaltflächen zum Betreiben der Szene</span><span class="sxs-lookup"><span data-stu-id="23443-184">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="23443-185">In diesem Abschnitt fügen Sie Prefabs und Skripts in die Szene ein, um eine Reihe von Schaltflächen zu erstellen, die die Grundlagen der Art und Weise, wie sowohl lokale Anker als auch räumliche Azure-Anker sich in einer Anwendung Verhalten.</span><span class="sxs-lookup"><span data-stu-id="23443-185">In this section, you will add prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

1. <span data-ttu-id="23443-186">Konfigurieren Sie die Druck Bare Schaltfläche Holo Lens 2 (Skript).</span><span class="sxs-lookup"><span data-stu-id="23443-186">Configure the Pressable Button Holo Lens 2 (script) component.</span></span>

    <span data-ttu-id="23443-187">Erweitern Sie im Hierarchie Panel das **buttonparent** -Objekt, und wählen Sie das erste untergeordnete Objekt mit dem Namen **startazuresession**aus.</span><span class="sxs-lookup"><span data-stu-id="23443-187">In the Hierarchy panel, expand the **ButtonParent** object and select the first child object named **StartAzureSession**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-1.1.png)

    <span data-ttu-id="23443-189">Scrollen Sie im Inspektor-Panel nach unten zur **druckbaren Schaltfläche Holo Lens 2 (Script)** , und fügen Sie einen neuen Ereignislistener zum **gedrückten Ereignis ()** hinzu, indem Sie auf das **+** -Symbol klicken.</span><span class="sxs-lookup"><span data-stu-id="23443-189">In the Inspector panel, scroll down to the **Pressable Button Holo Lens 2 (script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-1.2.png)

    <span data-ttu-id="23443-191">Wenn das startazuresession-Objekt im Hierarchie Panel noch ausgewählt ist, klicken Sie auf-und ziehen Sie das Objekt " **Objektanker** " aus dem Hierarchie Panel in das leere Feld " **None" (Objekt)** des Ereignislistener, den Sie soeben hinzugefügt haben, um das Objekt "Objektanchor" über diese Schaltfläche zu lauschen.</span><span class="sxs-lookup"><span data-stu-id="23443-191">With the StartAzureSession object still selected in the Hierarchy panel, click-and-drag the **ParentAnchor** object from the Hierarchy panel into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-1.3.png)

    <span data-ttu-id="23443-193">Klicken Sie auf die Dropdown Liste **keine Funktion** des gleichen Ereignislistener, und wählen Sie dann **anchormodulescript** > **startazuresession ()** aus, um die startazuresession ()-Funktion als Aktion festzulegen, die ausgelöst wird, wenn die Schaltfläche gedrückte Ereignisse von dieser Schaltfläche ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="23443-193">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-1.4.png)

2. <span data-ttu-id="23443-195">Konfigurieren Sie die interactable-Komponente (Skript).</span><span class="sxs-lookup"><span data-stu-id="23443-195">Configure the Interactable (script) component.</span></span>

    <span data-ttu-id="23443-196">Wenn das startazuresession-Objekt im Bereich Hierarchie weiterhin ausgewählt ist, Scrollen Sie im Inspektor-Panel nach unten zur Komponente **interactable (Script)** , und wiederholen Sie den gleichen Prozess wie in Schritt 1 oben für das **OnClick ()** -Ereignis.</span><span class="sxs-lookup"><span data-stu-id="23443-196">With the StartAzureSession object still selected in the Hierarchy panel, in the Inspector panel, scroll down to the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-2.1.png)

3. <span data-ttu-id="23443-198">Konfigurieren der verbleibenden Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="23443-198">Configure the remaining buttons</span></span>

    <span data-ttu-id="23443-199">Schließen Sie für jede der verbleibenden Schaltflächen den in Schritt 1 und 2 beschriebenen Prozess ab, um sowohl den Schaltflächen gedrückten () als auch dem OnClick ()-Ereignis Funktionen zuzuweisen:</span><span class="sxs-lookup"><span data-stu-id="23443-199">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the Button Pressed () and OnClick () events following:</span></span>

    * <span data-ttu-id="23443-200">Weisen Sie für das **stopazuresession** -Objekt die **stopazuresession ()** -Funktion zu.</span><span class="sxs-lookup"><span data-stu-id="23443-200">For the **StopAzureSession** object, assign the **StopAzureSession()** function.</span></span>
    * <span data-ttu-id="23443-201">Weisen Sie für **das Objekt "das Objekt** " "die Funktion" "die Funktion" Funktion " **()** zu, und ziehen Sie dann die **Komponente" ankeranchor** "erneut in das leere Feld" **None "(Spielobjekt)** .</span><span class="sxs-lookup"><span data-stu-id="23443-201">For the **CreateAnchor** object, assign the **CreateAzureAnchor()** function, then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
    * <span data-ttu-id="23443-202">Weisen Sie für das **nach Anker Objekt gesuchte** die **findazureanchor ()** -Funktion zu.</span><span class="sxs-lookup"><span data-stu-id="23443-202">For the **Start Looking for Anchor** object, assign the **FindAzureAnchor()** function.</span></span>
    * <span data-ttu-id="23443-203">Weisen Sie für das **Azure Anchor** -Objekt löschen die **deleteazureanchor ()** -Funktion zu.</span><span class="sxs-lookup"><span data-stu-id="23443-203">For the **Delete Azure Anchor** object, assign the **DeleteAzureAnchor()** function.</span></span>
    * <span data-ttu-id="23443-204">Weisen Sie für das Objekt **lokalen Anker löschen** die **removelocalanchor ()** -Funktion zu, und ziehen Sie dann den Objektanchor erneut in das leere Feld **None (Game Object)** .</span><span class="sxs-lookup"><span data-stu-id="23443-204">For the **Delete Local Anchor** object, assign the **RemoveLocalAnchor()** function, then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>

4. <span data-ttu-id="23443-205">Verbinden der Szene mit der Azure-Ressource</span><span class="sxs-lookup"><span data-stu-id="23443-205">Connect the scene to the Azure resource</span></span>

    <span data-ttu-id="23443-206">Wählen Sie im Bereich Hierarchie das Objekt **Objektanker** aus, und Scrollen Sie im Inspektor-Panel nach unten zur Komponente **räumlicher Anker-Manager (Skript)** .</span><span class="sxs-lookup"><span data-stu-id="23443-206">In the Hierarchy panel, select the **ParentAnchor** object and in the Inspector panel, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

    <span data-ttu-id="23443-207">Fügen Sie dann im Abschnitt **Anmelde** Informationen Ihre Konto-ID und den Schlüssel für räumliche Anker in die entsprechenden Kontoschlüssel Felder **Konto-ID** und **räumlichkeits** Felder des räumlichen Ankern ein.</span><span class="sxs-lookup"><span data-stu-id="23443-207">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields.</span></span>

    >[!NOTE]
    ><span data-ttu-id="23443-208">Sie haben Ihre Konto-ID und den Schlüssel für räumliche Anker im Rahmen der [Voraussetzungen](mrlearning-asa-ch1.md#prerequisites)dieses Tutorials erstellt.</span><span class="sxs-lookup"><span data-stu-id="23443-208">You created your Spatial Anchors Account Id and Key as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites).</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-4.1.png)

    >[!CAUTION]
    ><span data-ttu-id="23443-210">Stellen Sie sicher, dass Sie Ihre Szene speichern.</span><span class="sxs-lookup"><span data-stu-id="23443-210">Make sure you save your scene.</span></span>

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="23443-211">Grundlegendes Verhalten von räumlichen Azure-Ankern</span><span class="sxs-lookup"><span data-stu-id="23443-211">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="23443-212">Nachdem Ihre Szene nun so konfiguriert wurde, dass Sie die Grundlagen von räumlichen Azure-Ankern veranschaulicht, ist es an der Zeit, die APP bereitzustellen, damit Sie Azure Spatial Anchor (erste Schritte) nutzen können.</span><span class="sxs-lookup"><span data-stu-id="23443-212">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

1. <span data-ttu-id="23443-213">Fügen Sie zusätzliche erforderliche Funktionen hinzu.</span><span class="sxs-lookup"><span data-stu-id="23443-213">Add additional required capabilities.</span></span>

    <span data-ttu-id="23443-214">Wählen Sie im Unity-Menü **Bearbeiten** > **Projekteinstellungen...** aus, um das Fenster mit den Player Einstellungen zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="23443-214">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings panel.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-6-1.1.png)

    <span data-ttu-id="23443-216">Wählen Sie im Bereich Player Einstellungen die Option **Player** und dann **Veröffentlichungs Einstellungen**aus.</span><span class="sxs-lookup"><span data-stu-id="23443-216">In the Player Settings panel, select **Player** and then **Publishing Settings**.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-6-1.2.png)

    <span data-ttu-id="23443-218">Führen Sie in den **Veröffentlichungs Einstellungen**einen Bildlauf nach unten zum Abschnitt **Funktionen** durch, und überprüfen Sie, ob **spatialperception**, das Sie beim Erstellen des Projekts am Anfang des Tutorials aktiviert haben, aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="23443-218">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that **SpatialPerception**, which you enabled when you created the project at the beginning of the tutorial, is enabled.</span></span> <span data-ttu-id="23443-219">Anschließend wurden die Funktionen **Internetclient**, **internetclientserver**, **privatenetworkclientserver**, **removablestorage**, **Webcam**und **Mikrofon** aktiviert.</span><span class="sxs-lookup"><span data-stu-id="23443-219">Then, enabled the **InternetClient**, **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, **Webcam**, and **Microphone** capabilities.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-6-1.3.png)

2. <span data-ttu-id="23443-221">Stellen Sie die APP auf den hololens 2 bereit.</span><span class="sxs-lookup"><span data-stu-id="23443-221">Deploy the app to your HoloLens 2.</span></span>

    >[!TIP]
    ><span data-ttu-id="23443-222">Eine Erinnerung zum Erstellen und Bereitstellen Ihres Unity-Projekts in hololens 2 finden Sie in den Abschnitten Erstellen der [Anwendung auf Ihren Geräten](mrlearning-base-ch1.md#build-your-application-to-your-device) des Tutorials [initialisieren Ihres Projekts und der ersten Anwendung](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) , die Teil der Reihe erste Schritte mit [Tutorials](mrlearning-base.md) ist.</span><span class="sxs-lookup"><span data-stu-id="23443-222">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) sections of the [Initializing your project and first application](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) tutorial which is part of the the [Getting started tutorials](mrlearning-base.md) series.</span></span>

3. <span data-ttu-id="23443-223">Führen Sie die APP aus, und befolgen Sie die Anweisungen in der app.</span><span class="sxs-lookup"><span data-stu-id="23443-223">Run the app and follow the in-app instructions.</span></span>

    >[!CAUTION]
    ><span data-ttu-id="23443-224">Azure Spatial Anchor verwendet das Internet zum Speichern und Laden der Anker Daten, damit sichergestellt ist, dass Ihr Gerät mit dem Internet verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="23443-224">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

    <span data-ttu-id="23443-225">Wenn die Anwendung auf Ihrem Gerät ausgeführt wird, befolgen Sie die Anweisungen auf dem Bildschirm, die im **Azure Spatial Anchor Module instructions** -Panel angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="23443-225">When the application is running on your device, follow the on-screen instructions displayed on the **Azure Spatial Anchor Module Instructions** panel.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-6-3.1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="23443-227">Verankern eines Erlebnisses</span><span class="sxs-lookup"><span data-stu-id="23443-227">Anchoring an experience</span></span>

<span data-ttu-id="23443-228">In den vorherigen Abschnitten haben Sie die Grundlagen von räumlichen Azure-Ankern kennengelernt.</span><span class="sxs-lookup"><span data-stu-id="23443-228">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="23443-229">Wir haben einen Cube verwendet, um das übergeordnete Spielobjekt mit dem angefügten Anker darzustellen und zu visualisieren.</span><span class="sxs-lookup"><span data-stu-id="23443-229">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="23443-230">In diesem Abschnitt erfahren Sie, wie Sie eine vollständige-Funktion verankern können, indem Sie Sie als untergeordnetes Element des Objektanchor-Objekts platzieren.</span><span class="sxs-lookup"><span data-stu-id="23443-230">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

1. <span data-ttu-id="23443-231">Fügen Sie das Launcher-Start Programm hinzu.</span><span class="sxs-lookup"><span data-stu-id="23443-231">Add the Rocket Launcher experience.</span></span>

    <span data-ttu-id="23443-232">Navigieren Sie im Projekt Panel zu **Assets** > **mrtk. Tutorials. GettingStarted** > Ordner " **Prefabs** ", und wählen Sie die **Launcher_Complete** vorfab aus.</span><span class="sxs-lookup"><span data-stu-id="23443-232">In the Project panel, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder and select the **Rocket Launcher_Complete** prefab.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-7-1.1.png)

    <span data-ttu-id="23443-234">Ziehen Sie bei aktivierter aufruppe Launcher_Complete die Option "Prefab" auf das Objekt " **Objektanchor** " im Hierarchie Panel, um es zu einem untergeordneten Element des Objekts "Objekt Anker" zu machen.</span><span class="sxs-lookup"><span data-stu-id="23443-234">With the Rocket Launcher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy panel to make it a child of the ParentAnchor object.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-7-1.2.png)

2. <span data-ttu-id="23443-236">Positionieren Sie das Launcher-Start Programm neu.</span><span class="sxs-lookup"><span data-stu-id="23443-236">Reposition the Rocket Launcher experience.</span></span>

    <span data-ttu-id="23443-237">Verschieben Sie das Modul mit dem **Launcher_Complete** Objekt, damit das **Objekt (der** Cube) noch verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="23443-237">Move module **Rocket Launcher_Complete** object so that the **ParentAnchor** (the cube) is still exposed.</span></span>

    ![mrlearning-ASA](images/mrlearning-asa-ch1-7-2.1.png)

    <span data-ttu-id="23443-239">In der Anwendung kann es sein, dass Benutzer die gesamte Benutzeroberflächen-Start Programm Darstellung neu positionieren, indem Sie den Cube verschieben.</span><span class="sxs-lookup"><span data-stu-id="23443-239">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

    >[!TIP]
    ><span data-ttu-id="23443-240">Es gibt eine Vielzahl von Benutzeroberflächen Abläufen für die Neupositionierung, einschließlich der Verwendung eines neu positionierenden Objekts (z. b. des in diesem Tutorial verwendeten Cubes), der Verwendung einer Schaltfläche zum Umschalten eines umgebenden Felds, das die Oberfläche umgibt, der Verwendung von Position und Drehung. Gizmos und mehr.</span><span class="sxs-lookup"><span data-stu-id="23443-240">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="23443-241">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="23443-241">Congratulations</span></span>

<span data-ttu-id="23443-242">In diesem Tutorial haben Sie die Grundlagen von räumlichen Azure-Ankern kennengelernt.</span><span class="sxs-lookup"><span data-stu-id="23443-242">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="23443-243">In dieser Lektion haben Sie mehrere Schaltflächen zur Verfügung gestellt, mit denen Sie die verschiedenen Schritte zum Starten und Beenden einer Azure-Sitzung sowie zum Erstellen, hochladen und Herunterladen von Azure-Ankern auf einem einzelnen Gerät untersuchen können</span><span class="sxs-lookup"><span data-stu-id="23443-243">This Lesson provided you with several buttons that let you  explore the various steps required to start and stop an Azure session and create, upload and download azure anchors on a single device.</span></span>

<span data-ttu-id="23443-244">In der nächsten Lektion erfahren Sie, wie Sie Azure-Anker-IDs für den Abruf in den hololens 2 speichern, auch nachdem die Anwendung neu gestartet wurde, und wie Anker-IDs zwischen mehreren Geräten übertragen werden, um eine räumliche Ausrichtung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="23443-244">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="23443-245">Nächste Lektion: 2. speichern, abrufen und Freigeben von räumlichen Azure-Ankern</span><span class="sxs-lookup"><span data-stu-id="23443-245">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
