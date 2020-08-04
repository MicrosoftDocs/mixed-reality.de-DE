---
title: 'Tutorials zu Azure Spatial Anchors: 2 Erste Schritte mit Azure Spatial Anchors'
description: In diesem Kurs erfahren Sie, wie Sie Azure Spatial Anchors in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: d117839e51e586f4b905a20510fffc670d34cd4e
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376492"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="f247f-105">2. Erste Schritte mit Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="f247f-105">2. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="f247f-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="f247f-106">Overview</span></span>

<span data-ttu-id="f247f-107">In diesem Tutorial erkunden Sie die verschiedenen Schritte, die zum Starten und Beenden einer Azure Spatial Anchors-Sitzung und zum Erstellen, Hochladen und Herunterladen von Azure Spatial Anchors auf einem Einzelgerät erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="f247f-107">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="f247f-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="f247f-108">Objectives</span></span>

* <span data-ttu-id="f247f-109">Erlernen der Grundlagen des Entwickelns mit Azure Spatial Anchors für HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f247f-109">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="f247f-110">Erfahren, wie Raumanker erstellt und aus Azure abgerufen werden</span><span class="sxs-lookup"><span data-stu-id="f247f-110">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="f247f-111">Erstellen und Vorbereiten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="f247f-111">Creating and preparing the Unity project</span></span>

<span data-ttu-id="f247f-112">In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die MRTK-Entwicklung vor.</span><span class="sxs-lookup"><span data-stu-id="f247f-112">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="f247f-113">Befolgen Sie zu diesem Zweck zunächst die Anweisungen unter [Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung](mr-learning-base-02.md), jedoch ohne die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihrem Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2), die die folgenden Schritte beinhalten:</span><span class="sxs-lookup"><span data-stu-id="f247f-113">For this, first follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="f247f-114">[Erstellen eines neuen Unity-Projekts](mr-learning-base-02.md#creating-the-unity-project), das mit einem passenden Namen bezeichnet wird, beispielsweise *MRTK-Tutorials*</span><span class="sxs-lookup"><span data-stu-id="f247f-114">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
1. [<span data-ttu-id="f247f-115">Wechseln der Buildplattform</span><span class="sxs-lookup"><span data-stu-id="f247f-115">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. [<span data-ttu-id="f247f-116">Importieren der TextMeshPro Essential-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="f247f-116">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [<span data-ttu-id="f247f-117">Importieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="f247f-117">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [<span data-ttu-id="f247f-118">Konfigurieren des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="f247f-118">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. <span data-ttu-id="f247f-119">[Erstellen und Konfigurieren der Szene](mr-learning-base-02.md#creating-and-configuring-the-scene) und Bezeichnen der Szene mit einem passenden Namen, z. B. *AzureSpatialAnchors*</span><span class="sxs-lookup"><span data-stu-id="f247f-119">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="f247f-120">Befolgen Sie dann die Anweisungen unter [Ändern der Anzeigeoptionen für räumliche Wahrnehmung](mr-learning-base-03.md#changing-the-spatial-awareness-display-option), um die folgenden Aufgaben auszuführen:</span><span class="sxs-lookup"><span data-stu-id="f247f-120">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="f247f-121">Ändern des **MRTK-Konfigurationsprofils** in **DefaultHoloLens2ConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="f247f-121">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="f247f-122">Ändern der **Anzeigeoptionen für das Gittermodell für räumliche Wahrnehmung** in **Occlusion** (Verdeckung).</span><span class="sxs-lookup"><span data-stu-id="f247f-122">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="f247f-123">Installieren von integrierten Unity-Paketen</span><span class="sxs-lookup"><span data-stu-id="f247f-123">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="f247f-124">Wählen Sie im Unity-Menü **Fenster** > **Package Manager** (Paket-Manager) aus, um das Fenster „Package Manager“ zu öffnen, wählen Sie **AR Foundation** aus, und klicken Sie auf die Schaltfläche **Install** (Installieren), um das Paket zu installieren:</span><span class="sxs-lookup"><span data-stu-id="f247f-124">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="f247f-126">Sie installieren das AR Foundation-Paket, da es für das Azure Spatial Anchor SDK erforderlich ist, das Sie im nächsten Abschnitt importieren.</span><span class="sxs-lookup"><span data-stu-id="f247f-126">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="f247f-127">Importieren der Tutorialressourcen</span><span class="sxs-lookup"><span data-stu-id="f247f-127">Importing the tutorial assets</span></span>

<span data-ttu-id="f247f-128">Laden Sie die folgenden benutzerdefinierten Unity-Pakete herunter, und **importieren** Sie sie **in der Reihenfolge, in der sie aufgelistet sind**:</span><span class="sxs-lookup"><span data-stu-id="f247f-128">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="f247f-129">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (Version 2.2.1)</span><span class="sxs-lookup"><span data-stu-id="f247f-129">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (version 2.2.1)</span></span>
* [<span data-ttu-id="f247f-130">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="f247f-130">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="f247f-131">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="f247f-131">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)

<span data-ttu-id="f247f-132">Nach dem Importieren der Tutorialressourcen sollte Ihr Projektfenster ähnlich wie die folgende Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="f247f-132">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="f247f-134">Wenn Sie eine Auffrischung zum Importieren eines benutzerdefinierten Unity-Pakets benötigen, lesen Sie die Anweisungen unter [Importieren des Mixed Reality-Toolkits](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="f247f-134">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="f247f-135">Vorbereiten der Szene</span><span class="sxs-lookup"><span data-stu-id="f247f-135">Preparing the scene</span></span>

<span data-ttu-id="f247f-136">In diesem Abschnitt bereiten Sie die Szene vor, indem Sie einige der Tutorial-Prefabs hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f247f-136">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="f247f-137">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs**, klicken Sie auf die folgenden Prefabs, und ziehen Sie sie in das Hierarchiefenster, um sie Ihrer Szene hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="f247f-137">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="f247f-138">**ButtonParent**-Prefabs</span><span class="sxs-lookup"><span data-stu-id="f247f-138">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="f247f-139">**DebugWindow**-Prefabs</span><span class="sxs-lookup"><span data-stu-id="f247f-139">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="f247f-140">**Instructions**-Prefabs</span><span class="sxs-lookup"><span data-stu-id="f247f-140">**Instructions** prefabs</span></span>
* <span data-ttu-id="f247f-141">**ParentAnchor**-Prefabs</span><span class="sxs-lookup"><span data-stu-id="f247f-141">**ParentAnchor** prefabs</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="f247f-143">Wenn Sie die großen Symbole in Ihrer Szene, beispielsweise die mit großen Rahmen umgebenen ‚T‘-Symbole, irritierend finden, können Sie diese ausblenden, indem Sie <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">die Gizmos umschalten</a> (in die Aus-Position), wie in der Abbildung oben dargestellt.</span><span class="sxs-lookup"><span data-stu-id="f247f-143">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="f247f-144">Konfigurieren der Schaltflächen zum Betreiben der Szene</span><span class="sxs-lookup"><span data-stu-id="f247f-144">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="f247f-145">In diesem Abschnitt fügen Sie Skripts in die Szene ein, um eine Reihe von Schaltflächenereignissen zu erstellen, mit denen die Grundlagen des Verhaltens beider lokaler Anker und der Azure Spatial Anchors in einer Anwendung veranschaulicht werden.</span><span class="sxs-lookup"><span data-stu-id="f247f-145">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="f247f-146">Klappen Sie im Hierarchiefenster das **ButtonParent**-Objekt auf, und wählen Sie im Inspektorfenster das erste untergeordnete Objekt mit dem Namen **StartAzureSession** aus. Konfigurieren Sie dann das **On Click ()** -Ereignis der **Button Config Helper (Script)** -Komponente wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f247f-146">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**, in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="f247f-147">Weisen Sie das **ParentAnchor**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu.</span><span class="sxs-lookup"><span data-stu-id="f247f-147">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="f247f-148">Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **AnchorModuleScript** > **StartAzureSession ()** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen.</span><span class="sxs-lookup"><span data-stu-id="f247f-148">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="f247f-150">Wählen Sie im Hierarchiefenster die nächste Schaltfläche mit dem Namen **StopAzureSession** aus, und konfigurieren Sie dann im Inspektorfenster das **On Click ()** -Ereignis der **Button Config Helper (Script)** -Komponente wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f247f-150">In the Hierarchy window, select the next button named **StopAzureSession**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="f247f-151">Weisen Sie das **ParentAnchor**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu.</span><span class="sxs-lookup"><span data-stu-id="f247f-151">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="f247f-152">Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **AnchorModuleScript** > **StopAzureSession ()** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen.</span><span class="sxs-lookup"><span data-stu-id="f247f-152">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="f247f-154">Wählen Sie im Hierarchiefenster die nächste Schaltfläche mit dem Namen **CreateAzureAnchor** aus, und konfigurieren Sie dann im Inspektorfenster das **On Click ()** -Ereignis der **Button Config Helper (Script)** -Komponente wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f247f-154">In the Hierarchy window, select the next button named **CreateAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="f247f-155">Weisen Sie das **ParentAnchor**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu.</span><span class="sxs-lookup"><span data-stu-id="f247f-155">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="f247f-156">Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **AnchorModuleScript** > **CreateAzureAnchor ()** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen.</span><span class="sxs-lookup"><span data-stu-id="f247f-156">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="f247f-157">Weisen Sie das **ParentAnchor**-Objekt dem leeren Feld **None (Game Object)** (Ohne (Spielobjekt)) zu, um es als Argument für die Funktion „CreateAzureAnchor ()“ festzulegen</span><span class="sxs-lookup"><span data-stu-id="f247f-157">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="f247f-159">Wählen Sie im Hierarchiefenster die nächste Schaltfläche mit dem Namen **RemoveLocalAnchor** aus, und konfigurieren Sie dann im Inspektorfenster das **On Click ()** -Ereignis der **Button Config Helper (Script)** -Komponente wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f247f-159">In the Hierarchy window, select the next button named **RemoveLocalAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="f247f-160">Weisen Sie das **ParentAnchor**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu.</span><span class="sxs-lookup"><span data-stu-id="f247f-160">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="f247f-161">Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **AnchorModuleScript** > **RemoveLocalAnchor ()** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen.</span><span class="sxs-lookup"><span data-stu-id="f247f-161">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="f247f-162">Weisen Sie das **ParentAnchor**-Objekt dem leeren Feld **None (Game Object)** (Ohne (Spielobjekt)) zu, um es als Argument für die Funktion „RemoveLocalAnchor ()“ festzulegen</span><span class="sxs-lookup"><span data-stu-id="f247f-162">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="f247f-164">Wählen Sie im Hierarchiefenster die nächste Schaltfläche mit dem Namen **FindAzureAnchor** aus, und konfigurieren Sie dann im Inspektorfenster das **On Click ()** -Ereignis der **Button Config Helper (Script)** -Komponente wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f247f-164">In the Hierarchy window, select the next button named **FindAzureAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="f247f-165">Weisen Sie das **ParentAnchor**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu.</span><span class="sxs-lookup"><span data-stu-id="f247f-165">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="f247f-166">Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **AnchorModuleScript** > **FindAzureAnchor ()** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen.</span><span class="sxs-lookup"><span data-stu-id="f247f-166">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="f247f-168">Wählen Sie im Hierarchiefenster die nächste Schaltfläche mit dem Namen **DeleteAzureAnchor** aus, und konfigurieren Sie dann im Inspektorfenster das **On Click ()** -Ereignis der **Button Config Helper (Script)** -Komponente wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f247f-168">In the Hierarchy window, select the next button named **DeleteAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="f247f-169">Weisen Sie das **ParentAnchor**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu.</span><span class="sxs-lookup"><span data-stu-id="f247f-169">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="f247f-170">Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **AnchorModuleScript** > **DeleteAzureAnchor ()** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen.</span><span class="sxs-lookup"><span data-stu-id="f247f-170">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="f247f-172">Verbinden der Szene mit der Azure-Ressource</span><span class="sxs-lookup"><span data-stu-id="f247f-172">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="f247f-173">Wählen Sie im Hierarchiefenster das **ParentAnchor**-Objekt aus, und suchen Sie dann im Inspektorfenster die Komponente **Spatial Anchor Manager (Script)** .</span><span class="sxs-lookup"><span data-stu-id="f247f-173">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="f247f-174">Konfigurieren Sie den Abschnitt **Credentials** (Anmeldeinformationen) mit den Anmeldeinformationen aus dem Azure Spatial Anchors-Konto, das Sie im Rahmen der [Voraussetzungen](mr-learning-asa-01.md#prerequisites) für diese Tutorialreihe erstellt haben:</span><span class="sxs-lookup"><span data-stu-id="f247f-174">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="f247f-175">Fügen Sie in das Feld **Spatial Anchors Account ID** die **Konto-ID** Ihres Azure Spatial Anchors-Kontos ein</span><span class="sxs-lookup"><span data-stu-id="f247f-175">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="f247f-176">Fügen Sie in das Feld **Spatial Anchors Account Key** (Spatial Anchors-Kontoschlüssel) den primären oder sekundären **Zugriffsschlüssel** aus Ihrem Azure Spatial Anchors-Konto ein</span><span class="sxs-lookup"><span data-stu-id="f247f-176">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="f247f-178">Testen der grundlegenden Verhaltensweisen von Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="f247f-178">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="f247f-179">Azure Spatial Anchors können nicht in Unity ausgeführt werden, daher müssen Sie das Projekt erstellen und die App auf Ihrem Gerät bereitstellen, um die Azure Spatial Anchors-Funktionalität zu testen.</span><span class="sxs-lookup"><span data-stu-id="f247f-179">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="f247f-180">Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer Anwendung für das HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="f247f-180">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="f247f-181">Wenn die App auf Ihrem Gerät ausgeführt wird, befolgen Sie die Anweisungen auf dem Bildschirm, die im Anweisungsbereich des Azure Spatial Anchor-Tutorials angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="f247f-181">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="f247f-182">Bewegen Sie den Würfel an einen anderen Ort</span><span class="sxs-lookup"><span data-stu-id="f247f-182">Move the cube to a different location</span></span>
1. <span data-ttu-id="f247f-183">Starten Sie die Azure-Sitzung</span><span class="sxs-lookup"><span data-stu-id="f247f-183">Start Azure Session</span></span>
1. <span data-ttu-id="f247f-184">Erstellen Sie einen Azure-Anker (erstellt einen Anker an der Position des Würfels).</span><span class="sxs-lookup"><span data-stu-id="f247f-184">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
1. <span data-ttu-id="f247f-185">Beenden Sie die Azure-Sitzung</span><span class="sxs-lookup"><span data-stu-id="f247f-185">Stop Azure Session</span></span>
1. <span data-ttu-id="f247f-186">Entfernen Sie den lokalen Anker (ermöglicht es dem Benutzer, den Würfel zu bewegen)</span><span class="sxs-lookup"><span data-stu-id="f247f-186">Remove Local Anchor (allows the user to move the cube)</span></span>
1. <span data-ttu-id="f247f-187">Bewegen Sie den Würfel an eine andere Stelle</span><span class="sxs-lookup"><span data-stu-id="f247f-187">Move the cube somewhere else</span></span>
1. <span data-ttu-id="f247f-188">Starten Sie die Azure-Sitzung</span><span class="sxs-lookup"><span data-stu-id="f247f-188">Start Azure Session</span></span>
1. <span data-ttu-id="f247f-189">Suchen Sie einen Azure Anchor (positioniert den Würfel am Ort aus Schritt 3)</span><span class="sxs-lookup"><span data-stu-id="f247f-189">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
1. <span data-ttu-id="f247f-190">Löschen Sie den Azure Anchor</span><span class="sxs-lookup"><span data-stu-id="f247f-190">Delete Azure Anchor</span></span>
1. <span data-ttu-id="f247f-191">Beenden Sie die Azure-Sitzung</span><span class="sxs-lookup"><span data-stu-id="f247f-191">Stop Azure session</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="f247f-193">Azure Spatial Anchors verwendet das Internet zum Speichern und Laden der Ankerdaten, achten Sie also darauf, dass Ihr Gerät über eine Internetverbindung verfügt.</span><span class="sxs-lookup"><span data-stu-id="f247f-193">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="f247f-194">Verankern eines Benutzererlebnisses</span><span class="sxs-lookup"><span data-stu-id="f247f-194">Anchoring an experience</span></span>

<span data-ttu-id="f247f-195">In den vorherigen Abschnitten haben Sie die Grundlagen von Azure Spatial Anchors kennengelernt.</span><span class="sxs-lookup"><span data-stu-id="f247f-195">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="f247f-196">Wir haben einen Würfel verwendet, um das übergeordnete Spielobjekt mit dem angefügten Anker dazustellen und zu visualisieren.</span><span class="sxs-lookup"><span data-stu-id="f247f-196">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="f247f-197">In diesem Abschnitt erfahren Sie, wie Sie ein gesamtes Benutzererlebnis verankern, indem Sie es als untergeordnetes Objekt des ParentAnchor-Objekts platzieren.</span><span class="sxs-lookup"><span data-stu-id="f247f-197">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="f247f-198">Wählen Sie im Hierarchiefenster das **ParentAnchor**-Objekt aus, und konfigurieren Sie dann im Inspektorfenster die **Transform**-Komponenten (Transformieren) wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f247f-198">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="f247f-199">Ändern Sie die **Scale X** (X-Skalierung) in 1,1</span><span class="sxs-lookup"><span data-stu-id="f247f-199">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="f247f-200">Ändern Sie die **Scale Z** (Z-Skalierung) in 1,1</span><span class="sxs-lookup"><span data-stu-id="f247f-200">Change **Scale Z** to 1.1</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="f247f-202">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** (Medienobjekte > MRTK.Tutorials.GettingStarted > Prefabs > Rover), klicken Sie dann auf das Prefab **RoverExplorer_Complete**, und ziehen Sie es auf das Hierarchiefenster, um es der Szene hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="f247f-202">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="f247f-204">Ziehen Sie das noch im Hierarchiefenster ausgewählte neu hinzugefügte RoverModule_Complete-Objekt auf das **ParentAnchor**-Objekt, um es zu einem untergeordneten Objekt des ParentAnchor-Objekts zu machen:</span><span class="sxs-lookup"><span data-stu-id="f247f-204">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="f247f-206">Wenn Sie das Projekt jetzt neu erstellen und die App auf Ihrem Gerät bereitstellen, können Sie jetzt die gesamte Rover Explorer-Erfahrung neu positionieren, indem Sie den in der Größe veränderten Würfel bewegen.</span><span class="sxs-lookup"><span data-stu-id="f247f-206">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="f247f-207">Es gibt eine Vielzahl von Benutzererlebnisabläufen für die Neupositionierung von Erlebnissen, einschließlich der Verwendung eines Neupositionierungsobjekts (wie des Würfels, der in diesem Tutorial verwendet wird), der Verwendung einer Schaltfläche zum Umschalten eines Begrenzungsrahmens, der das Erlebnis umgibt, der Verwendung von Gizmos für Position und Drehung und mehr.</span><span class="sxs-lookup"><span data-stu-id="f247f-207">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="f247f-208">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="f247f-208">Congratulations</span></span>

<span data-ttu-id="f247f-209">In diesem Tutorial haben Sie die Grundlagen von Azure Spatial Anchors kennengelernt.</span><span class="sxs-lookup"><span data-stu-id="f247f-209">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="f247f-210">Dieses Tutorial hat Ihnen verschiedene Schaltflächen an die Hand gegeben, um die verschiedenen Schritte zu erkunden, die zum Starten und Beenden einer Azure-Spatial Anchors-Sitzung erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="f247f-210">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="f247f-211">Ferner zum Erstellen, Hochladen und Herunterladen von Azure Spatial Anchors auf einem Einzelgerät.</span><span class="sxs-lookup"><span data-stu-id="f247f-211">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="f247f-212">Im nächsten Tutorial erfahren Sie, wie Azure Anchor-IDs für den Abruf auf Ihrer HoloLens 2 gespeichert werden, auch nach einem Neustart der App, und wie Anchor-IDs zwischen mehreren Geräten übertragen werden, um räumliche Ausrichtung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="f247f-212">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="f247f-213">Nächstes Tutorial: 3. Speichern, Abrufen und Freigeben von Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="f247f-213">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
