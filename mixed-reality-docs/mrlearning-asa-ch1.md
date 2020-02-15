---
title: Tutorials zu Azure Spatial Anchor-1. Ersten Einstieg in Azure Spatial Anchor
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 21883e95e92f8808bcf270e6d8091f31933ab6fa
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250851"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="4af2b-105">1. Einstieg in Azure Spatial Anchor</span><span class="sxs-lookup"><span data-stu-id="4af2b-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="4af2b-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="4af2b-106">Overview</span></span>

<span data-ttu-id="4af2b-107">Willkommen bei der zweiten Reihe der hololens 2-Tutorials.</span><span class="sxs-lookup"><span data-stu-id="4af2b-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="4af2b-108">In dieser dreiteiligen tutorialreihe erfahren Sie mehr über die Grundlagen von räumlichen Azure-Ankern.</span><span class="sxs-lookup"><span data-stu-id="4af2b-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="4af2b-109">In diesem ersten Tutorial, den ersten Schritten [mit räumlichen Azure-Ankern](mrlearning-asa-ch1.md), werden die verschiedenen Schritte erläutert, die zum Starten und Beenden einer Azure-Sitzung sowie zum Erstellen, hochladen und Herunterladen von Azure-Ankern auf einem einzelnen Gerät erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="4af2b-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="4af2b-110">Im zweiten Tutorial zum [speichern, abrufen und Freigeben von räumlichen Azure-Ankern](mrlearning-asa-ch2.md)erfahren Sie, wie Sie räumliche Azure-Anker in mehreren App-Sitzungen speichern, indem Sie Anker Informationen im Speicher von hololens 2 speichern und diese Anker Informationen für eine Anker Ausrichtung mit mehreren Geräten an andere Geräte weitergeben.</span><span class="sxs-lookup"><span data-stu-id="4af2b-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="4af2b-111">Im dritten Tutorial, in dem das [Azure Spatial Anchor-Feedback angezeigt](mrlearning-asa-ch3.md)wird, erfahren Sie, wie Sie Benutzern Feedback zu Anker Ereignissen und-Status bei der Verwendung von räumlichen Azure-Ankern bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="4af2b-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="4af2b-112">Ziele</span><span class="sxs-lookup"><span data-stu-id="4af2b-112">Objectives</span></span>

* <span data-ttu-id="4af2b-113">Erfahren Sie mehr über die Grundlagen der Entwicklung mit räumlichen Azure-Ankern für hololens 2</span><span class="sxs-lookup"><span data-stu-id="4af2b-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="4af2b-114">Erstellen, hochladen und herunterladen räumlicher Anker</span><span class="sxs-lookup"><span data-stu-id="4af2b-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4af2b-115">Erforderliche Komponenten</span><span class="sxs-lookup"><span data-stu-id="4af2b-115">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="4af2b-116">Wenn Sie die Reihe "erste Schritte" noch nicht abgeschlossen haben, empfiehlt es sich, [diese Tutorials zuerst](mrlearning-base.md) abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="4af2b-116">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="4af2b-117">Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md) konfiguriert ist</span><span class="sxs-lookup"><span data-stu-id="4af2b-117">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="4af2b-118">Windows 10 SDK 10.0.18362.0 oder höher</span><span class="sxs-lookup"><span data-stu-id="4af2b-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="4af2b-119">Grundlegende C# Programmier Fähigkeit</span><span class="sxs-lookup"><span data-stu-id="4af2b-119">Some basic C# programming ability</span></span>
* <span data-ttu-id="4af2b-120">Ein hololens 2-Gerät, das [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode) ist</span><span class="sxs-lookup"><span data-stu-id="4af2b-120">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="4af2b-121"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity-Hub</a> mit installiertem Unity 2019.2. X und dem hinzugefügten universelle Windows-Plattform Build-Unterstützungs Modul</span><span class="sxs-lookup"><span data-stu-id="4af2b-121"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="4af2b-122">Vervollständigen Sie den Abschnitt [Create a Spatial Anchor Resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) des [Schnellstarts: Erstellen einer Unity hololens-APP, die Azure Spatial](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) Anchor-Tutorial verwendet.</span><span class="sxs-lookup"><span data-stu-id="4af2b-122">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4af2b-123">Die empfohlene Unity-Version für diese tutorialreihe ist Unity 2019.2. X.</span><span class="sxs-lookup"><span data-stu-id="4af2b-123">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="4af2b-124">Dadurch werden alle Unity-Versions Anforderungen oder-Empfehlungen ersetzt, die in den oben genannten Voraussetzungen angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="4af2b-124">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="4af2b-125">Erstellen des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="4af2b-125">Creating the Unity project</span></span>
<!-- TODO: Consider renaming to 'Creating and preparing the Unity scene and project'-->

<span data-ttu-id="4af2b-126">In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die mrtk-Entwicklung vor.</span><span class="sxs-lookup"><span data-stu-id="4af2b-126">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span> <span data-ttu-id="4af2b-127">Befolgen Sie hierzu die Anweisungen unter [initialisieren Ihres Projekts und der ersten Anwendung](mrlearning-base-ch1.md), und schließen Sie die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihr Gerät](mrlearning-base-ch1.md#build-your-application-to-your-device) ab. Hierzu gehören die folgenden Schritte:</span><span class="sxs-lookup"><span data-stu-id="4af2b-127">For this, please follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="4af2b-128">[Erstellen Sie ein neues Unity-Projekt](mrlearning-base-ch1.md#create-new-unity-project) , und geben Sie ihm einen passenden Namen, z. b. *mrtk-Tutorials*.</span><span class="sxs-lookup"><span data-stu-id="4af2b-128">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*.</span></span>

2. [<span data-ttu-id="4af2b-129">Konfigurieren des Unity-Projekts für Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4af2b-129">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="4af2b-130">Importieren von "textmesh pro Essentials"-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4af2b-130">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="4af2b-131">Importieren des Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="4af2b-131">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="4af2b-132">Konfigurieren des Unity-Projekts für das Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="4af2b-132">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="4af2b-133">[Fügen Sie der Unity-Szene das Mixed Reality Toolkit hinzu](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) , und geben Sie der Szene einen passenden Namen, z. b. *azurespatialanchor* .</span><span class="sxs-lookup"><span data-stu-id="4af2b-133">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

> [!CAUTION]
> <span data-ttu-id="4af2b-134">Wie im Abschnitt [Konfigurieren des Unity-Projekts für die Anweisungen für das gemischte Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) erläutert, unterstützt MSBuild für Unity möglicherweise nicht alle sdcs, die Sie verwenden werden, und kann nach der Aktivierung der Deaktivierung schwierig sein.</span><span class="sxs-lookup"><span data-stu-id="4af2b-134">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="4af2b-135">Daher wird dringend empfohlen, MSBuild für Unity nicht zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="4af2b-135">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="4af2b-136">Hinzufügen von integrierten Unity-Paketen</span><span class="sxs-lookup"><span data-stu-id="4af2b-136">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="4af2b-137">In diesem Abschnitt Installieren Sie das in Unity integrierte AR Foundation-Paket, da es für das Azure Spatial Anchor SDK erforderlich ist, das Sie im nächsten Abschnitt Importieren werden.</span><span class="sxs-lookup"><span data-stu-id="4af2b-137">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="4af2b-138">Wählen Sie im Unity-Menü die Option **Window** > **Package Manager**aus:</span><span class="sxs-lookup"><span data-stu-id="4af2b-138">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="4af2b-140">Es kann einige Sekunden dauern, bis das AR Foundation-Paket in der Liste angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="4af2b-140">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="4af2b-141">Wählen Sie im Fenster Paket-Manager die Option **AR Foundation** aus, und installieren Sie das Paket durch Klicken auf die Schaltfläche **Installieren** :</span><span class="sxs-lookup"><span data-stu-id="4af2b-141">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="4af2b-143">Importieren der tutorialassets</span><span class="sxs-lookup"><span data-stu-id="4af2b-143">Importing the tutorial assets</span></span>

<span data-ttu-id="4af2b-144">Herunterladen und **importieren** der folgenden benutzerdefinierten Unity-Pakete **in der Reihenfolge, in der Sie aufgelistet sind**:</span><span class="sxs-lookup"><span data-stu-id="4af2b-144">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="4af2b-145">[Azurespatialanchor. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (Version 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="4af2b-145">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="4af2b-146">Mrtk. HoloLens2. Unity. Tutorials. Assets. GettingStarted. 2.2.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="4af2b-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.2.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.1.unitypackage)
* [<span data-ttu-id="4af2b-147">Mrtk. HoloLens2. Unity. Tutorials. Assets. azurespatialanchor. 2.2.0.0. unitypackage</span><span class="sxs-lookup"><span data-stu-id="4af2b-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.2.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.2.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.2.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="4af2b-148">Eine Erinnerung zum Importieren eines benutzerdefinierten Unity-Pakets finden Sie in den Anweisungen zum [Importieren von Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) .</span><span class="sxs-lookup"><span data-stu-id="4af2b-148">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="4af2b-149">Nachdem Sie die tutorialassets importiert haben, sollte Ihr Projektfenster etwa wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="4af2b-149">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="4af2b-151">Erstellen und Vorbereiten der Szene</span><span class="sxs-lookup"><span data-stu-id="4af2b-151">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="4af2b-152">In diesem Abschnitt bereiten Sie die Szene vor, indem Sie einige der Prefabs hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="4af2b-152">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="4af2b-153">Navigieren Sie im Projektfenster zu **Assets** > **mrtk. Tutorials. azurespatialanchor** > Ordner " **Prefabs** ".</span><span class="sxs-lookup"><span data-stu-id="4af2b-153">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="4af2b-154">Wenn Sie die STRG-Taste gedrückt halten, klicken Sie auf " **Button Parent**", " **debugWindow**", " **instructions**" und "Parameter **Anchor** ", um die vier präfabs auszuwählen:</span><span class="sxs-lookup"><span data-stu-id="4af2b-154">While holding down the CTRL button, click on **ButtonParent**, **DebugWindow**, **Instructions**, and **ParentAnchor** to select the four prefabs:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section4-step1-1.png)

<span data-ttu-id="4af2b-156">Wenn die vier präfabs noch ausgewählt sind, ziehen Sie Sie in das Hierarchie Fenster, um Sie der Szene hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="4af2b-156">With the four prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section4-step1-2.png)

<span data-ttu-id="4af2b-158">Um sich auf die Objekte in der Szene zu konzentrieren, können Sie auf das Objekt "Objektanchor" doppelklicken und dann wieder etwas vergrößern:</span><span class="sxs-lookup"><span data-stu-id="4af2b-158">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> <span data-ttu-id="4af2b-160">Wenn Sie die großen Symbole in Ihrer Szene finden, z. b. die großen Symbole, die Sie nicht ablenken, können Sie diese ausblenden, indem Sie <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">die Gizmos</a> an der Position ausschalten.</span><span class="sxs-lookup"><span data-stu-id="4af2b-160">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="4af2b-161">Konfigurieren der Schaltflächen zum Betreiben der Szene</span><span class="sxs-lookup"><span data-stu-id="4af2b-161">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="4af2b-162">In diesem Abschnitt fügen Sie Skripts in die Szene ein, um eine Reihe von Schaltflächen Ereignissen zu erstellen, die die Grundlagen der Verhalten beider lokaler Anker und räumlicher Azure-Anker in einer Anwendung veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="4af2b-162">In this section, you will add scripts into the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a><span data-ttu-id="4af2b-163">1. Konfigurieren der druckbaren Schaltfläche "Holo Lens 2 (Skript)"</span><span class="sxs-lookup"><span data-stu-id="4af2b-163">1. Configure the Pressable Button Holo Lens 2 (Script) component</span></span>

<span data-ttu-id="4af2b-164">Erweitern Sie im Fenster Hierarchie das **buttonparent** -Objekt, und wählen Sie das erste untergeordnete Objekt mit dem Namen **startazuresession**aus:</span><span class="sxs-lookup"><span data-stu-id="4af2b-164">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step1-1.png)

<span data-ttu-id="4af2b-166">Suchen Sie im Inspektor-Fenster die **Druck Bare Schaltfläche Holo Lens 2 (Script)** , und fügen Sie dem Button-Ereignis **()** einen neuen Ereignislistener hinzu, indem Sie auf das **+** -Symbol klicken:</span><span class="sxs-lookup"><span data-stu-id="4af2b-166">In the Inspector window, locate the **Pressable Button Holo Lens 2 (Script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step1-2.png)

<span data-ttu-id="4af2b-168">Wenn das startazuresession-Objekt noch im Fenster Hierarchie ausgewählt ist, klicken Sie auf-und ziehen Sie das Objekt " **Objektanker** " aus dem Fenster "Hierarchie" in das leere Feld " **None" (Objekt)** des Ereignislistener, den Sie soeben hinzugefügt haben</span><span class="sxs-lookup"><span data-stu-id="4af2b-168">With the StartAzureSession object still selected in the Hierarchy window, click-and-drag the **ParentAnchor** object from the Hierarchy window into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step1-3.png)

<span data-ttu-id="4af2b-170">Klicken Sie auf die Dropdown Liste **keine Funktion** des gleichen Ereignislistener, und wählen Sie dann **anchormodulescript** > **startazuresession ()** aus, um die startazuresession ()-Funktion als Aktion festzulegen, die ausgelöst wird, wenn die Schaltfläche gedrückte Ereignisse von dieser Schaltfläche ausgelöst wird:</span><span class="sxs-lookup"><span data-stu-id="4af2b-170">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a><span data-ttu-id="4af2b-172">2. Konfigurieren der interactable-Komponente (Skript)</span><span class="sxs-lookup"><span data-stu-id="4af2b-172">2. Configure the Interactable (Script) component</span></span>

<span data-ttu-id="4af2b-173">Wenn das startazuresession-Objekt noch im Fenster Hierarchie ausgewählt ist, suchen Sie im Inspektor-Fenster die Komponente **interactable (Script)** , und wiederholen Sie den Vorgang wie in Schritt 1 oben für das **OnClick ()** -Ereignis:</span><span class="sxs-lookup"><span data-stu-id="4af2b-173">With the StartAzureSession object still selected in the Hierarchy window, in the Inspector window, locate the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a><span data-ttu-id="4af2b-175">3. Konfigurieren der verbleibenden Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="4af2b-175">3. Configure the remaining buttons</span></span>

<span data-ttu-id="4af2b-176">Vervollständigen Sie für jede der verbleibenden Schaltflächen den Prozess, der in Schritt 1 und 2 oben beschrieben ist, um sowohl den **gedrückten ()** als auch den **OnClick ()** -Ereignissen Funktionen zuzuweisen:</span><span class="sxs-lookup"><span data-stu-id="4af2b-176">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the **Button Pressed ()** and **OnClick ()** events:</span></span>

* <span data-ttu-id="4af2b-177">Weisen Sie für das **stopazuresession** -Objekt die anchormodulescript-> **stopazuresession ()** -Funktion zu.</span><span class="sxs-lookup"><span data-stu-id="4af2b-177">For the **StopAzureSession** object, assign the AnchorModuleScript > **StopAzureSession ()** function.</span></span>
* <span data-ttu-id="4af2b-178">Weisen Sie für das Objekt " **kreateazureanchor** " die Funktion "anchormodulescript" > die Funktion "-Funktion **()** " zu,</span><span class="sxs-lookup"><span data-stu-id="4af2b-178">For the **CreateAzureAnchor** object, assign the AnchorModuleScript > **CreateAzureAnchor ()** function,</span></span>
  * <span data-ttu-id="4af2b-179">Ziehen Sie dann den **para Anker** erneut in das leere Feld **None (Game Object)** .</span><span class="sxs-lookup"><span data-stu-id="4af2b-179">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="4af2b-180">Weisen Sie für das **removelocalanchor** -Objekt die anchormodulescript-> **removelocalanchor ()** -Funktion zu.</span><span class="sxs-lookup"><span data-stu-id="4af2b-180">For the **RemoveLocalAnchor** object, assign the AnchorModuleScript > **RemoveLocalAnchor ()** function,</span></span>
  * <span data-ttu-id="4af2b-181">Ziehen Sie dann den **para Anker** erneut in das leere Feld **None (Game Object)** .</span><span class="sxs-lookup"><span data-stu-id="4af2b-181">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="4af2b-182">Weisen Sie für das **findazureanchor** -Objekt die anchormodulescript-> **findazureanchor ()** -Funktion zu.</span><span class="sxs-lookup"><span data-stu-id="4af2b-182">For the **FindAzureAnchor** object, assign the AnchorModuleScript > **FindAzureAnchor ()** function.</span></span>
* <span data-ttu-id="4af2b-183">Weisen Sie für das **deleteazureanchor** -Objekt das anchormodulescript-> **deleteazureanchor ()** -Funktion zu.</span><span class="sxs-lookup"><span data-stu-id="4af2b-183">For the **DeleteAzureAnchor** object, assign the AnchorModuleScript > **DeleteAzureAnchor ()** function.</span></span>

### <a name="4-connect-the-scene-to-the-azure-resource"></a><span data-ttu-id="4af2b-184">4. Verbinden Sie die Szene mit der Azure-Ressource.</span><span class="sxs-lookup"><span data-stu-id="4af2b-184">4. Connect the scene to the Azure resource</span></span>

<span data-ttu-id="4af2b-185">Wählen Sie im Fenster Hierarchie das Objekt Objektanker aus, und führen Sie im Inspektor-Fenster einen **Bildlauf** nach unten bis zur Komponente **räumlicher Anker-Manager (Skript)** aus.</span><span class="sxs-lookup"><span data-stu-id="4af2b-185">In the Hierarchy window, select the **ParentAnchor** object and in the Inspector window, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

<span data-ttu-id="4af2b-186">Fügen Sie dann im Abschnitt **Anmelde** Informationen Ihre Konto-ID und den Schlüssel für räumliche Anker, die Sie im Rahmen der [Voraussetzungen](mrlearning-asa-ch1.md#prerequisites)für dieses Tutorial erstellt haben, in die entsprechenden Konto- **ID** und die **Kontoschlüssel** Felder für räumliche Anker ein:</span><span class="sxs-lookup"><span data-stu-id="4af2b-186">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key, which you created as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites), into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="4af2b-188">Grundlegendes Verhalten von räumlichen Azure-Ankern</span><span class="sxs-lookup"><span data-stu-id="4af2b-188">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="4af2b-189">Nachdem Ihre Szene nun so konfiguriert wurde, dass Sie die Grundlagen von räumlichen Azure-Ankern veranschaulicht, ist es an der Zeit, die APP bereitzustellen, damit Sie Azure Spatial Anchor (erste Schritte) nutzen können.</span><span class="sxs-lookup"><span data-stu-id="4af2b-189">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="4af2b-190">1. zusätzliche erforderliche Funktionen hinzufügen</span><span class="sxs-lookup"><span data-stu-id="4af2b-190">1. Add additional required capabilities</span></span>

<span data-ttu-id="4af2b-191">Wählen Sie im Unity-Menü **Bearbeiten** > **Projekteinstellungen...** aus, um das Fenster "Player Einstellungen" zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="4af2b-191">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section6-step1-1.png)

<span data-ttu-id="4af2b-193">Wählen Sie im Fenster Player Einstellungen die Option **Player** aus, und veröffentlichen Sie dann die **Einstellungen**:</span><span class="sxs-lookup"><span data-stu-id="4af2b-193">In the Player Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section6-step1-2.png)

<span data-ttu-id="4af2b-195">Führen Sie in den **Veröffentlichungs Einstellungen**einen Bildlauf nach unten zum Abschnitt " **Funktionen** " durch, und überprüfen Sie, ob die Funktionen " **Internetclient**", " **Mikrofon**" und " **spatialperception** ", die Sie beim Erstellen des Projekts am Anfang des Tutorials aktiviert haben, aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="4af2b-195">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="4af2b-196">Anschließend wurden die Funktionen " **internetclientserver**", " **privatenetworkclientserver**", " **removablestorage**" und " **Webcam** " aktiviert:</span><span class="sxs-lookup"><span data-stu-id="4af2b-196">Then, enabled the **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, and **Webcam** capabilities:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="4af2b-198">2. Stellen Sie die APP auf den hololens 2 bereit.</span><span class="sxs-lookup"><span data-stu-id="4af2b-198">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="4af2b-199">Räumliche Azure-Anker können nicht in Unity ausgeführt werden. Daher müssen Sie das Projekt auf Ihrem Gerät bereitstellen, um die Azure Spatial Anchor-Funktionen zu testen.</span><span class="sxs-lookup"><span data-stu-id="4af2b-199">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="4af2b-200">Eine Erinnerung zum Erstellen und Bereitstellen Ihres Unity-Projekts in hololens 2 finden Sie in den Anweisungen zum [Erstellen Ihrer Anwendung auf Ihr Gerät](mrlearning-base-ch1.md#build-your-application-to-your-device) .</span><span class="sxs-lookup"><span data-stu-id="4af2b-200">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="4af2b-201">3. führen Sie die APP auf den hololens 2 aus, und befolgen Sie die Anweisungen in der app.</span><span class="sxs-lookup"><span data-stu-id="4af2b-201">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="4af2b-202">Azure Spatial Anchor verwendet das Internet zum Speichern und Laden der Anker Daten, damit sichergestellt ist, dass Ihr Gerät mit dem Internet verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="4af2b-202">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="4af2b-203">Wenn die Anwendung auf Ihrem Gerät ausgeführt wird, befolgen Sie die Anweisungen auf dem Bildschirm, die im Tutorial zum Azure Spatial Anchor-Tutorial angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="4af2b-203">When the application is running on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="4af2b-205">Verankern eines Erlebnisses</span><span class="sxs-lookup"><span data-stu-id="4af2b-205">Anchoring an experience</span></span>

<span data-ttu-id="4af2b-206">In den vorherigen Abschnitten haben Sie die Grundlagen von räumlichen Azure-Ankern kennengelernt.</span><span class="sxs-lookup"><span data-stu-id="4af2b-206">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="4af2b-207">Wir haben einen Cube verwendet, um das übergeordnete Spielobjekt mit dem angefügten Anker darzustellen und zu visualisieren.</span><span class="sxs-lookup"><span data-stu-id="4af2b-207">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="4af2b-208">In diesem Abschnitt erfahren Sie, wie Sie eine vollständige-Funktion verankern können, indem Sie Sie als untergeordnetes Element des Objektanchor-Objekts platzieren.</span><span class="sxs-lookup"><span data-stu-id="4af2b-208">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

### <a name="1-add-the-rocket-launcher-experience"></a><span data-ttu-id="4af2b-209">1. Hinzufügen der Funktion für das Raketenstart Programm</span><span class="sxs-lookup"><span data-stu-id="4af2b-209">1. Add the Rocket Launcher experience</span></span>

<span data-ttu-id="4af2b-210">Navigieren Sie im Projektfenster zu den **Assets** > **mrtk. Tutorials. GettingStarted** > **Prefabs** > **RocketLauncher** -Ordner, und wählen Sie die **RocketLauncher_Complete** Prefab aus:</span><span class="sxs-lookup"><span data-stu-id="4af2b-210">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder and select the **RocketLauncher_Complete** prefab:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section7-step1-1.png)

<span data-ttu-id="4af2b-212">Wenn die RocketLauncher_Complete Prefab noch ausgewählt ist, ziehen Sie Sie über das Objekt " **Objektanker** " im Hierarchie Fenster, um es als untergeordnetes Element des Objekts "objeanchor" zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="4af2b-212">With the RocketLauncher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy window to make it a child of the ParentAnchor object:</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a><span data-ttu-id="4af2b-214">2. Neupositionieren der Funktion für das Raketenstart Programm</span><span class="sxs-lookup"><span data-stu-id="4af2b-214">2. Reposition the Rocket Launcher experience</span></span>

<span data-ttu-id="4af2b-215">Positionieren, drehen und Skalieren Sie das **RocketLauncher_Complete** -Objekt in eine geeignete Skala und Ausrichtung, während Sie gleichzeitig sicherstellen, dass das Objekt " **Objektanker** " weiterhin verfügbar gemacht wird, z.b.:</span><span class="sxs-lookup"><span data-stu-id="4af2b-215">Position, rotate, and scale the **RocketLauncher_Complete** object to a suitable scale and orientation, while also ensuring the **ParentAnchor** object is still exposed, for example:</span></span>

* <span data-ttu-id="4af2b-216">Transformations **Position** X = 1, Y = 0, Z = 3,75</span><span class="sxs-lookup"><span data-stu-id="4af2b-216">Transform **Position** X = 1, Y = 0, Z = 3.75</span></span>
* <span data-ttu-id="4af2b-217">Transformations **Drehung** X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="4af2b-217">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="4af2b-218">Transformations **Skala** X = 10, Y = 10, Z = 10</span><span class="sxs-lookup"><span data-stu-id="4af2b-218">Transform **Scale** X = 10, Y = 10, Z = 10</span></span>

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section7-step2-1.png)

<span data-ttu-id="4af2b-220">In der Anwendung kann es sein, dass Benutzer die gesamte Benutzeroberflächen-Start Programm Darstellung neu positionieren, indem Sie den Cube verschieben.</span><span class="sxs-lookup"><span data-stu-id="4af2b-220">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

> [!TIP]
> <span data-ttu-id="4af2b-221">Es gibt eine Vielzahl von Benutzeroberflächen Abläufen für die Neupositionierung, einschließlich der Verwendung eines neu positionierenden Objekts (z. b. des in diesem Tutorial verwendeten Cubes), der Verwendung einer Schaltfläche zum Umschalten eines umgebenden Felds, das die Oberfläche umgibt, der Verwendung von Position und Drehung. Gizmos und mehr.</span><span class="sxs-lookup"><span data-stu-id="4af2b-221">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="4af2b-222">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="4af2b-222">Congratulations</span></span>

<span data-ttu-id="4af2b-223">In diesem Tutorial haben Sie die Grundlagen von räumlichen Azure-Ankern kennengelernt.</span><span class="sxs-lookup"><span data-stu-id="4af2b-223">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="4af2b-224">Das Tutorial bot Ihnen mehrere Schaltflächen, mit denen Sie die verschiedenen erforderlichen Schritte zum Starten und Beenden einer Azure-Sitzung für räumliche Anker und zum Erstellen, hochladen und Herunterladen von räumlichen Azure-Ankern auf einem einzelnen Gerät untersuchen können.</span><span class="sxs-lookup"><span data-stu-id="4af2b-224">The tutorial provided you with several buttons that let you explore the various steps required to start and stop an Azure Spatial Anchors session and create, upload and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="4af2b-225">In der nächsten Lektion erfahren Sie, wie Sie Azure-Anker-IDs für den Abruf in den hololens 2 speichern, auch nachdem die Anwendung neu gestartet wurde, und wie Anker-IDs zwischen mehreren Geräten übertragen werden, um eine räumliche Ausrichtung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="4af2b-225">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="4af2b-226">Nächste Lektion: 2. speichern, abrufen und Freigeben von räumlichen Azure-Ankern</span><span class="sxs-lookup"><span data-stu-id="4af2b-226">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
