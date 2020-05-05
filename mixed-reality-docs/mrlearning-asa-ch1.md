---
title: 'Tutorials zu Azure Spatial Anchors: 1 Erste Schritte mit Azure Spatial Anchors'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: d0fd22ad6fbefc6889373b00847721cfc0655ce3
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2020
ms.locfileid: "82605001"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="59a80-105">1. Erste Schritte mit Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="59a80-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="59a80-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="59a80-106">Overview</span></span>

<span data-ttu-id="59a80-107">Willkommen bei der zweiten Reihe der HoloLens 2-Tutorials.</span><span class="sxs-lookup"><span data-stu-id="59a80-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="59a80-108">In dieser dreiteiligen Tutorialreihe lernen Sie die Grundlagen von Azure Spatial Anchors kennen.</span><span class="sxs-lookup"><span data-stu-id="59a80-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="59a80-109">In diesem ersten Tutorial, [Erste Schritte mit Azure Spatial Anchors](mrlearning-asa-ch1.md), erkunden Sie die verschiedenen Schritte, die zum Starten und Beenden einer Azure-Sitzung und zum Erstellen, Hochladen und Herunterladen von Azure Anchors auf einem einzelnen Gerät erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="59a80-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="59a80-110">Im zweiten Tutorial, [Speichern, Abrufen und Freigeben von Azure Spatial Anchors](mrlearning-asa-ch2.md), erfahren Sie, wie Sie räumliche Azure-Spatial Anchors über mehrere App-Sitzungen hinweg speichern, indem Sie Ankerinformationen im Speicher von HoloLens 2 speichern, und wie Sie diese Ankerinformationen mit anderen Geräten teilen, um eine Ankerausrichtung auf mehreren Geräten zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="59a80-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="59a80-111">Im dritten Tutorial, [Anzeigen von Azure Spatial Anchors-Feedback](mrlearning-asa-ch3.md), lernen Sie, wie Sie beim Verwenden von Azure Spatial Anchors Feedback zu Ankerereignissen und -zuständen für Benutzer bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="59a80-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="59a80-112">Ziele</span><span class="sxs-lookup"><span data-stu-id="59a80-112">Objectives</span></span>

* <span data-ttu-id="59a80-113">Erlernen der Grundlagen des Entwickelns mit Azure Spatial Anchors für HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="59a80-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="59a80-114">Erstellen, Hochladen und Herunterladen von Raumankern</span><span class="sxs-lookup"><span data-stu-id="59a80-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="59a80-115">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="59a80-115">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="59a80-116">Wenn Sie die Reihe [Tutorials zu den ersten Schritten](mrlearning-base.md) noch nicht abgeschlossen haben, empfiehlt es sich, zunächst diese Tutorials abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="59a80-116">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="59a80-117">Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](install-the-tools.md) ist</span><span class="sxs-lookup"><span data-stu-id="59a80-117">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="59a80-118">Windows 10 SDK (10.0.18362.0 oder höher)</span><span class="sxs-lookup"><span data-stu-id="59a80-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="59a80-119">Grundlagenkenntnisse in der C#-Programmierung</span><span class="sxs-lookup"><span data-stu-id="59a80-119">Some basic C# programming ability</span></span>
* <span data-ttu-id="59a80-120">Ein für die [Entwicklung konfiguriertes](using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät</span><span class="sxs-lookup"><span data-stu-id="59a80-120">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="59a80-121"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.2.X und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform</span><span class="sxs-lookup"><span data-stu-id="59a80-121"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="59a80-122">Schließen Sie den Abschnitt [Erstellen einer Spatial Anchors-Ressource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) des Tutorials [Schnellstart: Erstellen einer Unity HoloLens-App, die Azure Spatial Anchors verwendet](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) ab.</span><span class="sxs-lookup"><span data-stu-id="59a80-122">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="59a80-123">Die empfohlene Unity-Version für diese Tutorialreihe ist Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="59a80-123">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="59a80-124">Diese übertrifft alle Versionsanforderungen oder -empfehlungen, die in den oben verlinkten Voraussetzungen angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="59a80-124">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="59a80-125">Erstellen des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="59a80-125">Creating the Unity project</span></span>
<!-- TODO: Consider renaming to 'Creating and preparing the Unity project'-->

<span data-ttu-id="59a80-126">In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die MRTK-Entwicklung vor.</span><span class="sxs-lookup"><span data-stu-id="59a80-126">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="59a80-127">Befolgen Sie zu diesem Zweck zunächst die Anweisungen unter [Initialisieren des Projekts und der ersten Anwendung](mrlearning-base-ch1.md), jedoch ohne die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihrem Gerät](mrlearning-base-ch1.md#build-your-application-to-your-device), die die folgenden Schritte beinhalten:</span><span class="sxs-lookup"><span data-stu-id="59a80-127">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="59a80-128">[Erstellen eines neuen Unity-Projekts](mrlearning-base-ch1.md#create-new-unity-project), das mit einem passenden Namen bezeichnet wird, beispielsweise *MRTK-Tutorials*</span><span class="sxs-lookup"><span data-stu-id="59a80-128">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. [<span data-ttu-id="59a80-129">Konfigurieren des Unity-Projekts für Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="59a80-129">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="59a80-130">Importieren von TextMesh Pro Essential-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="59a80-130">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="59a80-131">Importieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="59a80-131">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="59a80-132">Konfigurieren des Unity-Projekts für das Mixed Reality-Toolkit</span><span class="sxs-lookup"><span data-stu-id="59a80-132">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="59a80-133">[Hinzufügen des Mixed Reality-Toolkits zur Unity-Szene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit), die dann einen passenden Namen erhält, beispielsweise *AzureSpatialAnchors*</span><span class="sxs-lookup"><span data-stu-id="59a80-133">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="59a80-134">Befolgen Sie dann die Anweisungen unter [Konfigurieren der Mixed Reality-Toolkitprofile (Option zum Ändern der Anzeige der räumlichen Wahrnehmung)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option), um das **DefaultHoloLens2ConfigurationProfile** als MRTK-Konfigurationsprofil für Ihre Szene festzulegen, und ändern Sie die Anzeigeoptionen für das Gittermodell zur räumlichen Wahrnehmung in **Occlusion** (Verdeckung).</span><span class="sxs-lookup"><span data-stu-id="59a80-134">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="59a80-135">Wie bereits in den oben verlinkten Anweisungen zum [Konfigurieren des Unity-Projekts für das Mixed Reality-Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) erwähnt, wird dringend empfohlen, MSBuild for Unity nicht zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="59a80-135">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="59a80-136">Hinzufügen von integrierten Unity-Paketen</span><span class="sxs-lookup"><span data-stu-id="59a80-136">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="59a80-137">In diesem Abschnitt installieren Sie das integrierte Unity AR Foundation-Paket, da es vom Azure Spatial Anchors SDK benötigt wird, das Sie im nächsten Abschnitt importieren.</span><span class="sxs-lookup"><span data-stu-id="59a80-137">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="59a80-138">Wählen Sie im Unity-Menü **Window** > **Package Manager** (Fenster > Paket-Manager) aus:</span><span class="sxs-lookup"><span data-stu-id="59a80-138">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="59a80-140">Es kann einige Sekunden dauern, bis das AR Foundation-Paket in der Liste angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="59a80-140">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="59a80-141">Wählen Sie im Paket-Manager-Fenster die Option **AR Foundation** aus, und installieren Sie das Paket, indem Sie auf die Schaltfläche **Installieren** klicken:</span><span class="sxs-lookup"><span data-stu-id="59a80-141">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="59a80-143">Importieren der Tutorialressourcen</span><span class="sxs-lookup"><span data-stu-id="59a80-143">Importing the tutorial assets</span></span>

<span data-ttu-id="59a80-144">Laden Sie die folgenden benutzerdefinierten Unity-Pakete herunter, und **importieren** Sie sie **in der Reihenfolge, in der sie aufgelistet sind**:</span><span class="sxs-lookup"><span data-stu-id="59a80-144">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="59a80-145">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (Version 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="59a80-145">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="59a80-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="59a80-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="59a80-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="59a80-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)

> [!TIP]
> <span data-ttu-id="59a80-148">Wenn Sie eine Auffrischung zum Importieren eines benutzerdefinierten Unity-Pakets benötigen, lesen Sie die Anweisungen unter [Importieren des Mixed Reality-Toolkits](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="59a80-148">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="59a80-149">Nach dem Importieren der Tutorialressourcen sollte Ihr Projektfenster ähnlich wie die folgende Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="59a80-149">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="59a80-151">Erstellen und Vorbereiten der Szene</span><span class="sxs-lookup"><span data-stu-id="59a80-151">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="59a80-152">In diesem Abschnitt bereiten Sie die Szene vor, indem Sie einige der Tutorial-Prefabs hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="59a80-152">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="59a80-153">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs**.</span><span class="sxs-lookup"><span data-stu-id="59a80-153">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="59a80-154">Klicken Sie bei gedrückter STRG-Taste auf **ButtonParent**, **DebugWindow**, **Instructions** und **ParentAnchor**, um die vier Prefabs auszuwählen:</span><span class="sxs-lookup"><span data-stu-id="59a80-154">While holding down the CTRL button, click on **ButtonParent**, **DebugWindow**, **Instructions**, and **ParentAnchor** to select the four prefabs:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

<span data-ttu-id="59a80-156">Ziehen Sie die vier noch ausgewählten Prefabs auf das Hierarchiefenster, um sie der Szene hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="59a80-156">With the four prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

<span data-ttu-id="59a80-158">Um sich auf die Objekte in der Szene zu konzentrieren, können Sie auf das ParentAnchor-Objekt doppelklicken und die Ansicht dann etwas verkleinern:</span><span class="sxs-lookup"><span data-stu-id="59a80-158">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> <span data-ttu-id="59a80-160">Wenn Sie die großen Symbole in Ihrer Szene, beispielsweise die mit großen Rahmen umgebenen 'T'-Symbole, irritierend finden, können Sie diese ausblenden, indem Sie <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">die Gizmos umschalten</a> (in die Aus-Position).</span><span class="sxs-lookup"><span data-stu-id="59a80-160">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="59a80-161">Konfigurieren der Schaltflächen zum Betreiben der Szene</span><span class="sxs-lookup"><span data-stu-id="59a80-161">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="59a80-162">In diesem Abschnitt fügen Sie Skripts in die Szene ein, um eine Reihe von Schaltflächenereignissen zu erstellen, mit denen die Grundlagen des Verhaltens beider lokaler Anker und der Azure Spatial Anchors in einer Anwendung veranschaulicht werden.</span><span class="sxs-lookup"><span data-stu-id="59a80-162">In this section, you will add scripts into the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a><span data-ttu-id="59a80-163">1. Konfigurieren der Komponente „Pressable Button Holo Lens 2 (Script)“ (Drückbare Schaltfläche HoloLens 2 (Skript))</span><span class="sxs-lookup"><span data-stu-id="59a80-163">1. Configure the Pressable Button Holo Lens 2 (Script) component</span></span>

<span data-ttu-id="59a80-164">Klappen Sie im Hierarchiefenster das **ButtonParent**-Objekt auf, und wählen Sie das erste untergeordnete Objekt mit dem Namen **StartAzureSession** aus:</span><span class="sxs-lookup"><span data-stu-id="59a80-164">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

<span data-ttu-id="59a80-166">Suchen Sie im Inspektorfenster die **Pressable Button Holo Lens 2 (Script)** -Komponente, und fügen Sie dem Ereignis **Button Pressed ()** einen neuen Ereignislistener hinzu, indem Sie auf das **+** -Symbol klicken:</span><span class="sxs-lookup"><span data-stu-id="59a80-166">In the Inspector window, locate the **Pressable Button Holo Lens 2 (Script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

<span data-ttu-id="59a80-168">Klicken Sie bei immer noch im Hierarchiefenster ausgewähltem StartAzureSession-Objekt auf das **ParentAnchor**-Objekt, und ziehen Sie es auf das leere **None (Object)** -Feld des Ereignislisteners, den Sie soeben hinzugefügt haben, um das ParentAnchor-Objekt nach Gedrückt-Ereignissen für diese Schaltfläche lauschen zu lassen:</span><span class="sxs-lookup"><span data-stu-id="59a80-168">With the StartAzureSession object still selected in the Hierarchy window, click-and-drag the **ParentAnchor** object from the Hierarchy window into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

<span data-ttu-id="59a80-170">Klicken Sie auf die **No Function**-Dropdownliste des gleichen Ereignislisteners, wählen Sie dann **AnchorModuleScript** > **StartAzureSession ()** aus, um die StartAzureSession ()-Funktion als auszulösende Aktion festzulegen, wenn „Schaltfläche gedrückt“-Ereignisse von dieser Schaltfläche gesendet werden:</span><span class="sxs-lookup"><span data-stu-id="59a80-170">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a><span data-ttu-id="59a80-172">2. Konfigurieren der Interactable (Script)-Komponente</span><span class="sxs-lookup"><span data-stu-id="59a80-172">2. Configure the Interactable (Script) component</span></span>

<span data-ttu-id="59a80-173">Suchen Sie bei immer noch im Hierarchiefenster ausgewähltem StartAzureSession-Objekt im Inspektorfenster die Komponente **Interactable (Script)** , und wiederholen Sie den gleichen Prozess wie in Schritt 1 oben für das **OnClick ()** -Ereignis:</span><span class="sxs-lookup"><span data-stu-id="59a80-173">With the StartAzureSession object still selected in the Hierarchy window, in the Inspector window, locate the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a><span data-ttu-id="59a80-175">3. Konfigurieren der verbleibenden Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="59a80-175">3. Configure the remaining buttons</span></span>

<span data-ttu-id="59a80-176">Führen Sie für jede der verbleibenden Schaltflächen den in Schritt 1 und 2 beschrieben Vorgang aus, um den **Button Pressed ()** - und **OnClick ()** -Ereignissen Funktionen zuzuweisen:</span><span class="sxs-lookup"><span data-stu-id="59a80-176">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the **Button Pressed ()** and **OnClick ()** events:</span></span>

* <span data-ttu-id="59a80-177">Weisen Sie dem **StopAzureSession**-Objekt die AnchorModuleScript > **StopAzureSession ()** -Funktion zu.</span><span class="sxs-lookup"><span data-stu-id="59a80-177">For the **StopAzureSession** object, assign the AnchorModuleScript > **StopAzureSession ()** function.</span></span>
* <span data-ttu-id="59a80-178">Weisen Sie dem **CreateAzureAnchor**-Objekt die AnchorModuleScript > **CreateAzureAnchor ()** -Funktion zu,</span><span class="sxs-lookup"><span data-stu-id="59a80-178">For the **CreateAzureAnchor** object, assign the AnchorModuleScript > **CreateAzureAnchor ()** function,</span></span>
  * <span data-ttu-id="59a80-179">und ziehen Sie dann den **ParentAnchor** erneut auf das leere **None (Game Object)** -Feld.</span><span class="sxs-lookup"><span data-stu-id="59a80-179">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="59a80-180">Weisen Sie dem **RemoveLocalAnchor**-Objekt die AnchorModuleScript > **RemoveLocalAnchor ()** -Funktion zu,</span><span class="sxs-lookup"><span data-stu-id="59a80-180">For the **RemoveLocalAnchor** object, assign the AnchorModuleScript > **RemoveLocalAnchor ()** function,</span></span>
  * <span data-ttu-id="59a80-181">und ziehen Sie dann den **ParentAnchor** erneut auf das leere **None (Game Object)** -Feld.</span><span class="sxs-lookup"><span data-stu-id="59a80-181">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="59a80-182">Weisen Sie dem **FindAzureAnchor**-Objekt die AnchorModuleScript > **FindAzureAnchor ()** -Funktion zu.</span><span class="sxs-lookup"><span data-stu-id="59a80-182">For the **FindAzureAnchor** object, assign the AnchorModuleScript > **FindAzureAnchor ()** function.</span></span>
* <span data-ttu-id="59a80-183">Weisen Sie dem **DeleteAzureAnchor**-Objekt die AnchorModuleScript > **DeleteAzureAnchor ()** -Funktion zu.</span><span class="sxs-lookup"><span data-stu-id="59a80-183">For the **DeleteAzureAnchor** object, assign the AnchorModuleScript > **DeleteAzureAnchor ()** function.</span></span>

### <a name="4-connect-the-scene-to-the-azure-resource"></a><span data-ttu-id="59a80-184">4. Verbinden der Szene mit der Azure-Ressource</span><span class="sxs-lookup"><span data-stu-id="59a80-184">4. Connect the scene to the Azure resource</span></span>

<span data-ttu-id="59a80-185">Wählen Sie im Hierarchiefenster das **ParentAnchor**-Objekt aus, und scrollen Sie im Inspektorfenster zur Komponente **Spatial Anchor Manager (Script)** herunter.</span><span class="sxs-lookup"><span data-stu-id="59a80-185">In the Hierarchy window, select the **ParentAnchor** object and in the Inspector window, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

<span data-ttu-id="59a80-186">Fügen Sie dann im Abschnitt **Credentials** (Anmeldeinformationen) Ihr Raumankerkonto und den zugehörigen Schlüssel, die Sie im Rahmen der [Voraussetzungen](mrlearning-asa-ch1.md#prerequisites) dieses Tutorials erstellt haben, in die entsprechenden Felder **Spatial Anchors Account Id** und **Spatial Anchors Account Key** ein:</span><span class="sxs-lookup"><span data-stu-id="59a80-186">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key, which you created as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites), into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="59a80-188">Testen der grundlegenden Verhaltensweisen von Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="59a80-188">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="59a80-189">Jetzt, da Ihre Szene für die Veranschaulichung der Grundlagen von Azure Spatial Anchors konfiguriert ist, ist es Zeit, die App bereitzustellen, damit Sie Azure Spatial Anchors aus erster Hand erleben können.</span><span class="sxs-lookup"><span data-stu-id="59a80-189">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="59a80-190">1. Hinzufügen zusätzlicher erforderlicher Funktionen</span><span class="sxs-lookup"><span data-stu-id="59a80-190">1. Add additional required capabilities</span></span>

<span data-ttu-id="59a80-191">Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen...) aus, um das Fenster „Player Settings“ (Playereinstellungen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="59a80-191">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

<span data-ttu-id="59a80-193">Wählen Sie im Player Settings-Fenster **Player** und dann **Publishing Settings** (Veröffentlichungseinstellungen) aus:</span><span class="sxs-lookup"><span data-stu-id="59a80-193">In the Player Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

<span data-ttu-id="59a80-195">Scrollen Sie in den **Publishing Settings** nach unten zum Abschnitt **Capabilities** (Funktionen), und vergewissern Sie sich, dass die Funktionen **InternetClient**, **Microphone** und **SpatialPerception**, die Sie im Rahmen der Erstellung des Projekts zu Beginn des Tutorials erstellt haben, aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="59a80-195">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="59a80-196">Aktivieren Sie dann die Funktionen **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage** und **Webcam**:</span><span class="sxs-lookup"><span data-stu-id="59a80-196">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, and **Webcam** capabilities:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="59a80-198">2. Bereitstellen der App auf Ihrer HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="59a80-198">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="59a80-199">Azure Spatial Anchors können nicht in Unity ausgeführt werden, daher müssen Sie das Projekt auf Ihrem Gerät bereitstellen, um die Azure Spatial Anchors-Funktionalität zu testen.</span><span class="sxs-lookup"><span data-stu-id="59a80-199">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="59a80-200">Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer Anwendung auf Ihrem Gerät](mrlearning-base-ch1.md#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="59a80-200">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="59a80-201">3. Führen Sie die App auf Ihrer HoloLens 2 aus, und folgen Sie den Anweisungen in der App</span><span class="sxs-lookup"><span data-stu-id="59a80-201">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="59a80-202">Azure Spatial Anchors verwendet das Internet zum Speichern und Laden der Ankerdaten, achten Sie also darauf, dass Ihr Gerät über eine Internetverbindung verfügt.</span><span class="sxs-lookup"><span data-stu-id="59a80-202">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="59a80-203">Wenn die Anwendung auf Ihrem Gerät ausgeführt wird, befolgen Sie die Anweisungen auf dem Bildschirm, die im Anweisungsbereich des Azure Spatial Anchor-Tutorials angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="59a80-203">When the application is running on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="59a80-205">Verankern eines Benutzererlebnisses</span><span class="sxs-lookup"><span data-stu-id="59a80-205">Anchoring an experience</span></span>

<span data-ttu-id="59a80-206">In den vorherigen Abschnitten haben Sie die Grundlagen von Azure Spatial Anchors kennengelernt.</span><span class="sxs-lookup"><span data-stu-id="59a80-206">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="59a80-207">Wir haben einen Würfel verwendet, um das übergeordnete Spielobjekt mit dem angefügten Anker dazustellen und zu visualisieren.</span><span class="sxs-lookup"><span data-stu-id="59a80-207">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="59a80-208">In diesem Abschnitt erfahren Sie, wie Sie ein gesamtes Benutzererlebnis verankern, indem Sie es als untergeordnetes Objekt des ParentAnchor-Objekts platzieren.</span><span class="sxs-lookup"><span data-stu-id="59a80-208">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

### <a name="1-add-the-rocket-launcher-experience"></a><span data-ttu-id="59a80-209">1. Hinzufügen der Raketenstartbasis-Benutzererfahrung</span><span class="sxs-lookup"><span data-stu-id="59a80-209">1. Add the Rocket Launcher experience</span></span>

<span data-ttu-id="59a80-210">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher**, und wählen Sie das Prefab **RocketLauncher_Complete** aus:</span><span class="sxs-lookup"><span data-stu-id="59a80-210">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder and select the **RocketLauncher_Complete** prefab:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

<span data-ttu-id="59a80-212">Ziehen Sie das noch ausgewählte Prefab  „RocketLauncher_Complete“ auf das **ParentAnchor**-Objekt im Hierarchiefenster, um es zu einem untergeordneten Objekt des ParentAnchor-Objekts zu machen:</span><span class="sxs-lookup"><span data-stu-id="59a80-212">With the RocketLauncher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy window to make it a child of the ParentAnchor object:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a><span data-ttu-id="59a80-214">2. Neupositionieren der Raketenstartbasis-Benutzererfahrung</span><span class="sxs-lookup"><span data-stu-id="59a80-214">2. Reposition the Rocket Launcher experience</span></span>

<span data-ttu-id="59a80-215">Positionieren, drehen und skalieren Sie das **RocketLauncher_Complete**-Objekt auf einen passenden Maßstab und eine passende Ausrichtung, und stellen Sie zugleich sicher, dass das **ParentAnchor**-Objekt noch verfügbar ist, beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="59a80-215">Position, rotate, and scale the **RocketLauncher_Complete** object to a suitable scale and orientation, while also ensuring the **ParentAnchor** object is still exposed, for example:</span></span>

* <span data-ttu-id="59a80-216">**Transformationsposition** X = 0, Y = -0, Z = 3,75</span><span class="sxs-lookup"><span data-stu-id="59a80-216">Transform **Position** X = 0, Y = 0, Z = 3.75</span></span>
* <span data-ttu-id="59a80-217">**Transformationsrotation** X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="59a80-217">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="59a80-218">**Transformationsmaßstab** X = 10, Y = 10, Z = 10</span><span class="sxs-lookup"><span data-stu-id="59a80-218">Transform **Scale** X = 10, Y = 10, Z = 10</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

<span data-ttu-id="59a80-220">In der Anwendung können die Benutzer nun die gesamte Raketenstartbasis-Benutzererfahrung neu positionieren, indem sie den Würfel bewegen.</span><span class="sxs-lookup"><span data-stu-id="59a80-220">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

> [!TIP]
> <span data-ttu-id="59a80-221">Es gibt eine Vielzahl von Benutzererlebnisabläufen für die Neupositionierung von Erlebnissen, einschließlich der Verwendung eines Neupositionierungsobjekts (wie des Würfels, der in diesem Tutorial verwendet wird), der Verwendung einer Schaltfläche zum Umschalten eines Begrenzungsrahmens, der das Erlebnis umgibt, der Verwendung von Gizmos für Position und Drehung und mehr.</span><span class="sxs-lookup"><span data-stu-id="59a80-221">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="59a80-222">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="59a80-222">Congratulations</span></span>

<span data-ttu-id="59a80-223">In diesem Tutorial haben Sie die Grundlagen von Azure Spatial Anchors kennengelernt.</span><span class="sxs-lookup"><span data-stu-id="59a80-223">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="59a80-224">Das Tutorial hat Ihnen verschiedene Schaltflächen an die Hand gegeben, mit denen Sie die verschiedenen Schritte erkunden konnten, die zum Starten und Beenden einer Azure-Spatial Anchors-Sitzung und zum Erstellen, Hochladen und Herunterladen von Azure Anchors auf einem einzelnen Gerät erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="59a80-224">The tutorial provided you with several buttons that let you explore the various steps required to start and stop an Azure Spatial Anchors session and create, upload and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="59a80-225">In der nächsten Lektion erfahren Sie, wie Azure Anchor-IDs für den Abruf auf Ihrer HoloLens 2 gespeichert werden, auch nach einem Neustart der Anwendung, und wie Anchor-IDs zwischen mehreren Geräten übertragen werden, um räumliche Ausrichtung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="59a80-225">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="59a80-226">Nächste Lektion: 2. Speichern, Abrufen und Freigeben von Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="59a80-226">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
