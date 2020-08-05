---
title: Tutorials zu Holographic Remoting am PC – 1. Erste Schritte mit Holographic Remoting am PC
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie Mixed Reality Remoting von Ihrem PC zu HoloLens 2 ausführen.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/29/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 4929634d70a082e835eb7bd6b5680719338a5e92
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476972"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a><span data-ttu-id="6355c-105">1. Erste Schritte mit Holographic Remoting am PC</span><span class="sxs-lookup"><span data-stu-id="6355c-105">1. Getting started with PC Holographic Remoting</span></span>

## <a name="overview"></a><span data-ttu-id="6355c-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="6355c-106">Overview</span></span>

  <span data-ttu-id="6355c-107">Willkommen bei den HoloLens 2-Tutorials.</span><span class="sxs-lookup"><span data-stu-id="6355c-107">Welcome to the HoloLens 2 tutorials.</span></span> <span data-ttu-id="6355c-108">In dieser zweiteiligen Tutorialreihe erfahren Sie, wie Sie eine Mixed Reality-Demo und eine PC-App für Holographic Remoting erstellen.</span><span class="sxs-lookup"><span data-stu-id="6355c-108">In this two-part tutorial series, you will learn how to create a mixed reality experience demonstration and how to create a PC app for Holographic Remoting.</span></span>

   <span data-ttu-id="6355c-109">In diesem Tutorial, [Erstellen einer Mixed Reality-Erfahrung](mr-learning-pc-holographic-remoting-01.md), erfahren Sie, wie Sie eine Mixed Reality-Erfahrung erstellen können.</span><span class="sxs-lookup"><span data-stu-id="6355c-109">In this tutorial, [Create mixed reality experience](mr-learning-pc-holographic-remoting-01.md), you will learn how to create a mixed reality experience.</span></span> <span data-ttu-id="6355c-110">Es werden Benutzeroberflächenelemente, 3D-Modellbearbeitung, Modellclipping und Funktionen für Eye-Tracking veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="6355c-110">It will demonstrate UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span>

  <span data-ttu-id="6355c-111">Im zweiten Tutorial, [Erstellen einer Holographic Remoting-Anwendung](mr-learning-pc-holographic-remoting-02.md), erfahren Sie, wie Sie eine PC-App für Holographic Remoting erstellen.</span><span class="sxs-lookup"><span data-stu-id="6355c-111">In the second tutorial, [Create a Holographic Remoting application](mr-learning-pc-holographic-remoting-02.md), you will learn how to create a PC app for Holographic Remoting.</span></span> <span data-ttu-id="6355c-112">Stellen Sie jederzeit eine Verbindung mit HoloLens 2 her, um 3D-Inhalte in Mixed Reality visuell darzustellen.</span><span class="sxs-lookup"><span data-stu-id="6355c-112">And connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="6355c-113">Ziele</span><span class="sxs-lookup"><span data-stu-id="6355c-113">Objectives</span></span>

* <span data-ttu-id="6355c-114">Importieren von Assets und Einrichten der Szene</span><span class="sxs-lookup"><span data-stu-id="6355c-114">Import assets and set up the scene</span></span>
* <span data-ttu-id="6355c-115">Interagieren mit Hologrammen über Elemente und Schaltflächen der Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="6355c-115">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="6355c-116">Konfigurieren von 3D-Objekten für das Clippingfeature</span><span class="sxs-lookup"><span data-stu-id="6355c-116">Configure 3D objects for the clipping feature</span></span>
* <span data-ttu-id="6355c-117">Weitere Informationen zum Aktivieren von QuickInfos mit Eye-Tracking</span><span class="sxs-lookup"><span data-stu-id="6355c-117">Learn about activating tooltips with eye-tracking</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6355c-118">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="6355c-118">Prerequisites</span></span>

* <span data-ttu-id="6355c-119">Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](install-the-tools.md) ist</span><span class="sxs-lookup"><span data-stu-id="6355c-119">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="6355c-120">Gundkenntnisse der C#-Programmierung</span><span class="sxs-lookup"><span data-stu-id="6355c-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="6355c-121">Ein für die [Entwicklung konfiguriertes](using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät</span><span class="sxs-lookup"><span data-stu-id="6355c-121">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="6355c-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.3.X und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform</span><span class="sxs-lookup"><span data-stu-id="6355c-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.X mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="6355c-123">Wir **empfehlen dringend**, die Tutorialserie [Erste Schritte](mr-learning-base-01.md) durchzuarbeiten, oder dass Sie bereits einige grundlegende Erfahrung mit Unity und MRTK besitzen, bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="6355c-123">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="6355c-124">Die empfohlene Unity-Version für diese Tutorialserie ist Unity 2019.3.X.</span><span class="sxs-lookup"><span data-stu-id="6355c-124">The recommended Unity version for this tutorial series is Unity 2019.3.X.</span></span> <span data-ttu-id="6355c-125">Sie ersetzt alle Anforderungen oder Empfehlungen bezüglich der Unity-Version, die in den oben verknüpften Voraussetzungen genannt werden.</span><span class="sxs-lookup"><span data-stu-id="6355c-125">It supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>
> * <span data-ttu-id="6355c-126">Holographic-Remoting mit MRTK-Projekten funktioniert nur mit Legacy XR.</span><span class="sxs-lookup"><span data-stu-id="6355c-126">Holographic Remoting with MRTK projects will only work with legacy XR.</span></span> <span data-ttu-id="6355c-127">Das XR SDK wird derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6355c-127">XR SDK is not supported at this time.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="6355c-128">Erstellen und Vorbereiten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="6355c-128">Creating and preparing the Unity project</span></span>

<span data-ttu-id="6355c-129">In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die MRTK-Entwicklung vor.</span><span class="sxs-lookup"><span data-stu-id="6355c-129">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="6355c-130">Befolgen Sie zu diesem Zweck zunächst die Anweisungen unter [Initialisieren des Projekts und der ersten Anwendung](mr-learning-base-02.md), jedoch ohne die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihrem Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2), die die folgenden Schritte beinhalten:</span><span class="sxs-lookup"><span data-stu-id="6355c-130">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="6355c-131">[Erstellen eines neuen Unity-Projekts](mr-learning-base-02.md#creating-the-unity-project), das mit einem passenden Namen bezeichnet wird, beispielsweise *MRTK-Tutorials*</span><span class="sxs-lookup"><span data-stu-id="6355c-131">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

1. [<span data-ttu-id="6355c-132">Wechseln der Buildplattform</span><span class="sxs-lookup"><span data-stu-id="6355c-132">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. [<span data-ttu-id="6355c-133">Importieren der TextMeshPro Essential-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="6355c-133">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [<span data-ttu-id="6355c-134">Importieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="6355c-134">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [<span data-ttu-id="6355c-135">Konfigurieren des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="6355c-135">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. <span data-ttu-id="6355c-136">[Erstellen und Festlegen der Szene](mr-learning-base-02.md#creating-and-configuring-the-scene) und Bezeichnen der Szene mit einem passenden Namen, z. B. **PC Holographic Remoting**</span><span class="sxs-lookup"><span data-stu-id="6355c-136">[Creating and setting the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, **PC Holographic Remoting**</span></span>

<span data-ttu-id="6355c-137">Befolgen Sie dann die Anweisungen unter [Ändern der Anzeigeoption der räumlichen Wahrnehmung](mr-learning-base-03.md#changing-the-spatial-awareness-display-option), um das **DefaultHoloLens2ConfigurationProfile** als MRTK-Konfigurationsprofil für Ihre Szene festzulegen.</span><span class="sxs-lookup"><span data-stu-id="6355c-137">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile**.</span></span> <span data-ttu-id="6355c-138">Legen Sie die Anzeigeoptionen für das Gittermodell für räumliche Wahrnehmung auf **Occlusion** (Verdeckung) fest.</span><span class="sxs-lookup"><span data-stu-id="6355c-138">Change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="6355c-139">Importieren der Tutorialressourcen</span><span class="sxs-lookup"><span data-stu-id="6355c-139">Importing the tutorial assets</span></span>

<span data-ttu-id="6355c-140">Laden Sie [MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage) herunter, und **importieren** Sie das Paket.</span><span class="sxs-lookup"><span data-stu-id="6355c-140">Download and **import** the [MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage).</span></span>

>[!TIP]
> <span data-ttu-id="6355c-141">Wenn Sie eine Auffrischung zum Importieren eines benutzerdefinierten Unity-Pakets benötigen, lesen Sie die Anweisungen unter [Importieren des Mixed Reality-Toolkits](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="6355c-141">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="6355c-142">Nach dem Importieren der Tutorialressourcen sollte Ihr Projektfenster ähnlich wie die folgende Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="6355c-142">After importing the tutorial assets, your Project window should look similar to this:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section2-Step1-1.png)

## <a name="configuring-and-preparing-the-scene"></a><span data-ttu-id="6355c-144">Konfigurieren und Vorbereiten der Szene</span><span class="sxs-lookup"><span data-stu-id="6355c-144">Configuring and preparing the scene</span></span>

<span data-ttu-id="6355c-145">In diesem Abschnitt bereiten Sie die Szene vor, indem Sie einige der Tutorial-Prefabs hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6355c-145">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="6355c-146">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs**.</span><span class="sxs-lookup"><span data-stu-id="6355c-146">In the Project window, navigate to **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** folder.</span></span> <span data-ttu-id="6355c-147">Klicken Sie mit gedrückter STRG-Taste auf die folgenden sechs Prefabs.</span><span class="sxs-lookup"><span data-stu-id="6355c-147">While holding down the CTRL button, click on the below six prefabs.</span></span>

* <span data-ttu-id="6355c-148">ButtonParent</span><span class="sxs-lookup"><span data-stu-id="6355c-148">ButtonParent</span></span>
* <span data-ttu-id="6355c-149">ClippingObjects</span><span class="sxs-lookup"><span data-stu-id="6355c-149">ClippingObjects</span></span>
* <span data-ttu-id="6355c-150">HandSpatialMapButton</span><span class="sxs-lookup"><span data-stu-id="6355c-150">HandSpatialMapButton</span></span>
* <span data-ttu-id="6355c-151">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="6355c-151">Instructions</span></span>
* <span data-ttu-id="6355c-152">ModelParent</span><span class="sxs-lookup"><span data-stu-id="6355c-152">ModelParent</span></span>
* <span data-ttu-id="6355c-153">Platform</span><span class="sxs-lookup"><span data-stu-id="6355c-153">Platform</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

<span data-ttu-id="6355c-155">Ziehen Sie diese Modelle mithilfe von Drag & Drop aus dem Ordner „prefabs“ in das **Hierarchiefenster**.</span><span class="sxs-lookup"><span data-stu-id="6355c-155">Drag-and-drop these models from the prefabs folder into the **Hierarchy window**.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

<span data-ttu-id="6355c-157">Um sich auf die Objekte in der Szene zu konzentrieren, können Sie auf das **ModelParent**-Objekt doppelklicken und die Ansicht dann etwas verkleinern:</span><span class="sxs-lookup"><span data-stu-id="6355c-157">To focus in on the objects in the scene, you can double-click on the **ModelParent** object, and then zoom slightly in again:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> <span data-ttu-id="6355c-159">Wenn Sie die großen Symbole in Ihrer Szene, beispielsweise die mit großen Rahmen umgebenen 'T'-Symbole, irritierend finden, können Sie diese ausblenden, indem Sie <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">die Gizmos umschalten</a> (in die Position „Aus“).</span><span class="sxs-lookup"><span data-stu-id="6355c-159">If you find the large icons in your scene, such as, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="6355c-160">Konfigurieren der Schaltflächen zum Betreiben der Szene</span><span class="sxs-lookup"><span data-stu-id="6355c-160">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="6355c-161">In diesem Abschnitt fügen Sie in der Szene Skripts hinzu, um Schaltflächenereignisse zu erstellen, die die Grundlagen von Modellwechsel und Clippingfunktionalität veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="6355c-161">In this section, you will add scripts into the scene to create button events demonstrating the fundamentals of model switching and clipping functionality.</span></span>

### <a name="1-configuring-the-interactable-script-component"></a><span data-ttu-id="6355c-162">1. Konfigurieren der Komponente „Interactable (Script)“</span><span class="sxs-lookup"><span data-stu-id="6355c-162">1. Configuring the Interactable (Script) component</span></span>

<span data-ttu-id="6355c-163">Klappen Sie im Hierarchiefenster das **ButtonParent**-Objekt auf, und wählen Sie dann **NextButton** aus.</span><span class="sxs-lookup"><span data-stu-id="6355c-163">In the Hierarchy window, expand the **ButtonParent** object and select the **NextButton**.</span></span> <span data-ttu-id="6355c-164">Suchen Sie im Inspektor-Fenster nach der Komponente **Interactable (Script)** , und klicken Sie unter dem **OnClick ()** -Ereignis auf das Symbol **+** .</span><span class="sxs-lookup"><span data-stu-id="6355c-164">In the Inspector window, locate the **Interactable (Script)** component and click on **+** icon under **OnClick ()** event.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

<span data-ttu-id="6355c-166">Klicken Sie bei immer noch im Hierarchiefenster ausgewähltem **NextButton**-Objekt auf das **ButtonParent**-Objekt, und ziehen Sie es auf das leere **None (Object)** -Feld des Ereignislisteners, den Sie soeben hinzugefügt haben, um das ButtonParent-Objekt auf Geklickt-Ereignissen für diese Schaltfläche lauschen zu lassen:</span><span class="sxs-lookup"><span data-stu-id="6355c-166">With the **NextButton** object still selected in the Hierarchy window, click-and-drag the **ButtonParent** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

<span data-ttu-id="6355c-168">Klicken Sie auf die Dropdownliste **No Function** des gleichen Ereignisses.</span><span class="sxs-lookup"><span data-stu-id="6355c-168">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="6355c-169">Wählen Sie dann **ViewButtonControl** > **NextModel ()** aus, um die **NextModel ()** -Funktion als die Aktion festzulegen, die ausgelöst wird, wenn das Ereignis „Schaltfläche gedrückt“ von dieser Schaltfläche ausgelöst wird:</span><span class="sxs-lookup"><span data-stu-id="6355c-169">Then select **ViewButtonControl** > **NextModel ()** to set the **NextModel ()** function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a><span data-ttu-id="6355c-171">2. Konfigurieren der verbleibenden Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="6355c-171">2. Configuring the remaining buttons</span></span>

<span data-ttu-id="6355c-172">Führen Sie für jede der verbleibenden Schaltflächen den oben beschriebenen Vorgang aus, um den **OnClick ()** -Ereignissen Funktionen zuzuweisen:</span><span class="sxs-lookup"><span data-stu-id="6355c-172">For each of the remaining buttons, complete the process outlined above to assign functions to the **OnClick ()** events:</span></span>

* <span data-ttu-id="6355c-173">Weisen Sie für das PreviousButton-Objekt die Funktion **ViewButtonControl**l > **PreviousModel ()** zu.</span><span class="sxs-lookup"><span data-stu-id="6355c-173">For PreviousButton object, assign the **ViewButtonContro**l > **PreviousModel ()** function.</span></span>

* <span data-ttu-id="6355c-174">Wählen Sie für ClippingButton die Funktion **ToggleButton** > **ToggleClipping ()** aus.</span><span class="sxs-lookup"><span data-stu-id="6355c-174">For ClippingButton select **ToggleButton** > **ToggleClipping ()** function.</span></span>

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a><span data-ttu-id="6355c-175">3. Konfigurieren der Komponenten „View Button Control (Script)“ und „Toggle Button (Script)“</span><span class="sxs-lookup"><span data-stu-id="6355c-175">3. Configuring the View Button Control (Script)  and Toggle Button (Script) components</span></span>

<span data-ttu-id="6355c-176">Nun sind Ihre Schaltflächen so konfiguriert, dass Sie die Modellwechsel- und Clippingfunktionen veranschaulichen können.</span><span class="sxs-lookup"><span data-stu-id="6355c-176">Now your buttons are configured to demonstrate the model switching and clipping functionality.</span></span> <span data-ttu-id="6355c-177">Es ist an der Zeit, dem Skript 3D-Modelle und die Clippingobjekte hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="6355c-177">It is time to add 3D models and the clipping objects to the script.</span></span>

<span data-ttu-id="6355c-178">Wir haben sechs verschiedene 3D-Modelle zur Demonstrationszwecken bereitgestellt. Erweitern Sie das ***ModelParentobject***, um diese 3D-Modelle anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="6355c-178">We have provided six different 3D models for demonstration, expand the ***ModelParentobject*** to expose these 3D models.</span></span>

<span data-ttu-id="6355c-179">Während das ButtonParent-Objekt weiterhin im Hierarchiefenster ausgewählt ist, suchen Sie im Inspektor-Fenster nach der Komponente **View Button Control (Script)** , und erweitern Sie die Variable **Models**.</span><span class="sxs-lookup"><span data-stu-id="6355c-179">With the ButtonParent object still selected in the Hierarchy window, in the Inspector window, locate the **View Button Control (Script)** component and expand the **Models** variable.</span></span>

<span data-ttu-id="6355c-180">Geben Sie im Feld **Size** (Größe) die Anzahl der 3D-Modelle ein, die Sie in Ihrer Szene verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="6355c-180">In the **Size** field, enter the number of 3D models you would like to have in your scene.</span></span> <span data-ttu-id="6355c-181">In diesem Fall sind es sechs Modelle.</span><span class="sxs-lookup"><span data-stu-id="6355c-181">In this case, it would be six.</span></span> <span data-ttu-id="6355c-182">Es werden Felder zum Hinzufügen neuer 3D-Modelle erstellt.</span><span class="sxs-lookup"><span data-stu-id="6355c-182">It will create fields for adding new 3D models.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

<span data-ttu-id="6355c-184">Verschieben Sie jedes untergeordnete Objekt des ModelParent-Objekts mithilfe von Drag & Drop in diese Felder.</span><span class="sxs-lookup"><span data-stu-id="6355c-184">Drag and drop each child object of ModelParent Object into these fields.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

<span data-ttu-id="6355c-186">Ziehen Sie das **ClippingObjects**-Objekt mithilfe von Drag & Drop aus dem Hierarchiefenster in das Feld **Clipping Object** der Komponente **Toggle Button (Script)** .</span><span class="sxs-lookup"><span data-stu-id="6355c-186">Drag and drop the  **ClippingObjects** object from the Hierarchy window to the  **Toggle Button (Script)** component **Clipping Object** field.</span></span>
>[!NOTE]
><span data-ttu-id="6355c-187">Bleiben Sie die ganze Zeit ausschließlich im übergeordneten Objekt der Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="6355c-187">Stay in button parent object only.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

<span data-ttu-id="6355c-189">Wählen Sie im Hierarchiefenster das Prefab **ClippingObjects** aus, und aktivieren Sie es im Inspektor-Fenster, um die Clippingobjekte zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="6355c-189">In the Hierarchy window, select the **ClippingObjects** prefab and enable it in the Inspector window to turn on the Clipping objects.</span></span>

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a><span data-ttu-id="6355c-190">Konfigurieren der Clippingobjekte, um das Clippingfeature zu aktivieren</span><span class="sxs-lookup"><span data-stu-id="6355c-190">Configuring the clipping objects to enable clipping feature</span></span>

<span data-ttu-id="6355c-191">In diesem Abschnitt fügen Sie den Renderer für untergeordnete Objekte des MarsCuriosityRover-Objekts einem einzelnen Clippingobjekt hinzu, um das Clipping des MarsCuriosityRover-Modells zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="6355c-191">In this section, you will add MarsCuriosityRover object's child objects renderer into an individual clipping object to demonstrate the clipping of the MarsCuriosityRover model.</span></span>

<span data-ttu-id="6355c-192">Erweitern Sie im Hierarchiefenster das **ClippingObjects**-Objekt, um die drei unterschiedlichen Clippingobjekte verfügbar zu machen, die Sie in diesem Projekt verwenden.</span><span class="sxs-lookup"><span data-stu-id="6355c-192">In the Hierarchy window, expand the **ClippingObjects** object to expose the three different clipping objects that you will be using in this project.</span></span>

<span data-ttu-id="6355c-193">Um das **ClippingSphere**-Objekt zu konfigurieren, klicken Sie darauf, und suchen Sie dann im Inspektor-Fenster nach der Komponente **Clipping Sphere (Script)** .</span><span class="sxs-lookup"><span data-stu-id="6355c-193">To configure the **ClippingSphere** object, click on it, and in the Inspector window, locate the **Clipping Sphere (Script)** component.</span></span> <span data-ttu-id="6355c-194">Geben Sie die Anzahl der Renderer, die Sie für das 3D-Modell hinzufügen müssen, in das Größenfeld ein.</span><span class="sxs-lookup"><span data-stu-id="6355c-194">Enter the number of renderers in the size field that you need to add for your 3D model.</span></span> <span data-ttu-id="6355c-195">Fügen Sie in diesem Fall 10 Renderer für untergeordnete MarsCuriosityRover-Objekte hinzu.</span><span class="sxs-lookup"><span data-stu-id="6355c-195">In this case, add 10 for MarsCuriosityRover child objects.</span></span> <span data-ttu-id="6355c-196">Er werden Felder zum Hinzufügen von Renderern erstellt. Ziehen Sie untergeordnete Modellobjekte des MarsCuriosityRover-Objekts mithilfe von Drag & Drop in diese Felder.</span><span class="sxs-lookup"><span data-stu-id="6355c-196">It will create fields for adding renderers, drag and drop MarsCuriosityRover Object's child model objects into these fields.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

<span data-ttu-id="6355c-198">Führen Sie den gleichen Vorgang aus, und fügen Sie den **ClippingBox**- und **ClippingPlane**-Objekten Renderer für untergeordnete Objekte von MarsCuriosityRover hinzu.</span><span class="sxs-lookup"><span data-stu-id="6355c-198">Follow the same process and add MarsCuriosityRover's child objects renderers to the **ClippingBox** and **ClippingPlane** objects.</span></span>

<span data-ttu-id="6355c-199">In diesem Tutorial wird nur das MarsCuriosityRover-Modell verwendet, um das Clippingfeature zu demonstrieren.</span><span class="sxs-lookup"><span data-stu-id="6355c-199">In this tutorial, only the MarsCuriosityRover model will be used for demonstrating the clipping feature.</span></span> <span data-ttu-id="6355c-200">Es wurden Clippingfeatures zu weiteren Modellen hinzugefügt, die Größe des Renderers wurde vergrößert, und es wurden individuelle Gittermodellrenderer hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="6355c-200">They were adding clipping features to more models, increasing the size of the renderer, and adding their individual mesh renderers.</span></span>

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a><span data-ttu-id="6355c-201">Konfigurieren von Eye-Tracking zum Hervorheben von QuickInfos</span><span class="sxs-lookup"><span data-stu-id="6355c-201">Configuring eye-tracking to highlight tooltips</span></span>

<span data-ttu-id="6355c-202">In diesem Abschnitt wird erläutert, wie Sie Eye-Tracking in Ihrem Projekt aktivieren.</span><span class="sxs-lookup"><span data-stu-id="6355c-202">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="6355c-203">Beispielsweise implementieren Sie eine Funktionalität zum Hervorheben von QuickInfos, die an die Teile von MarsCuriosityRover angefügt sind, während Sie sich diese ansehen. Sie werden ausgeblendet, wenn Sie sie nicht mehr ansehen.</span><span class="sxs-lookup"><span data-stu-id="6355c-203">For example, you will implement the functionality to highlight tooltips attached to MarsCuriosityRover's parts while looking at them and hiding them, while you are looking away from them.</span></span>

### <a name="1-identify-target-objects-and-associated-tooltips"></a><span data-ttu-id="6355c-204">1. Identifizieren von Zielobjekten und zugehörigen QuickInfos</span><span class="sxs-lookup"><span data-stu-id="6355c-204">1. Identify target objects and associated tooltips</span></span>

<span data-ttu-id="6355c-205">Wählen Sie im Hierarchiefenster das ModelParent-Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="6355c-205">In the Hierarchy window, select the ModelParent object.</span></span> <span data-ttu-id="6355c-206">Erweitern Sie ***MarsCuriosity > Rover***, um fünf Hauptbestandteile von MarsCuriosityRover zu ermitteln: **POI-Camera**, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer**, **POI-RUHF Antenna**.</span><span class="sxs-lookup"><span data-stu-id="6355c-206">Expand the ***MarsCuriosity -> Rover*** to find five main parts of the MarsCuriosityRover: **POI-Camera**, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer**, **POI-RUHF Antenna**.</span></span>

* <span data-ttu-id="6355c-207">Beachten Sie die fünf entsprechenden QuickInfo-Objekte, die mit MarsCuriosityRover-Teilen im Hierarchiefenster verknüpft sind.</span><span class="sxs-lookup"><span data-stu-id="6355c-207">Observe five corresponding tooltip objects associated with MarsCuriosityRover parts in the Hierarchy window.</span></span>
* <span data-ttu-id="6355c-208">Sie konfigurieren diese Objekte so, dass sie hervorgehoben werden, wenn Sie sich die MarsCuriosityRover-Teile ansehen.</span><span class="sxs-lookup"><span data-stu-id="6355c-208">You will be configuring these objects to highlight the experience when you look at the MarsCuriosityRover parts.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a><span data-ttu-id="6355c-210">2. Implementierung von While Looking At Target ()- und On Look Away ()-Ereignissen</span><span class="sxs-lookup"><span data-stu-id="6355c-210">2. Implement While Looking At Target ()  &  On Look Away () events</span></span>

<span data-ttu-id="6355c-211">Wählen Sie im Hierarchiefenster das ***POI-Camera***-Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="6355c-211">In the Hierarchy window, select the ***POI-Camera*** object.</span></span> <span data-ttu-id="6355c-212">Suchen Sie im Inspektor-Fenster nach der Komponente **Eye Tracking Target (Script)** , und konfigurieren Sie die **While Looking At Target ()**  & **On Look Away ()** -Ereignisse wie folgt:</span><span class="sxs-lookup"><span data-stu-id="6355c-212">In the Inspector window, locate the **Eye Tracking Target (Script)** component and configure the **While Looking At Target ()** & **On Look Away ()** events as follows:</span></span>

* <span data-ttu-id="6355c-213">Weisen Sie dem Feld **None (Object)** das **POI-Camera ToolTip**-Objekt zu.</span><span class="sxs-lookup"><span data-stu-id="6355c-213">To **None (Object)** field, assign the **POI-Camera ToolTip** object</span></span>
* <span data-ttu-id="6355c-214">Wählen Sie in der Dropdownliste **No Function** des **While Looking At Target ()** -Ereignisses **GameObject** > **SetActive (bool)** aus.</span><span class="sxs-lookup"><span data-stu-id="6355c-214">From **No Function** dropdown of **While Looking At Target ()** event, select **GameObject** > **SetActive (bool).**</span></span> <span data-ttu-id="6355c-215">Aktivieren Sie das **Kontrollkästchen** darunter, um die QuickInfo als Aktion hervorzuheben, die ausgelöst wird, wenn Sie das Zielobjekt betrachten.</span><span class="sxs-lookup"><span data-stu-id="6355c-215">Select the **Checkbox** under it to highlight the tooltip as the action that is triggered when you look at the target object.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* <span data-ttu-id="6355c-217">Führen Sie den gleichen Vorgang aus, und klicken Sie auf die Dropdownliste **No Function** des **On Look Away ()** -Ereignislisteners.</span><span class="sxs-lookup"><span data-stu-id="6355c-217">Follow the same process and click on the **No Function** dropdown of the **On Look Away ()** event listener.</span></span> <span data-ttu-id="6355c-218">Wählen Sie dann **GameObject** > **SetActive(bool**) aus, und lassen Sie das **Kontrollkästchen** leer, um die QuickInfo als Aktion auszublenden, die ausgelöst wird, wenn Sie vom Zielobjekt wegschauen.</span><span class="sxs-lookup"><span data-stu-id="6355c-218">Then select **GameObject** > **SetActive (bool**) and leave the **Checkbox** empty to hide the tooltip as the action that is triggered when you look away from the target object.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

<span data-ttu-id="6355c-220">Führen Sie den gleichen Vorgang aus, und weisen Sie entsprechende QuickInfo-Objekte denselben **MarsCuriosityRover**-Teilen für **While Looking At Target ()**  & **On Look Away ()** -Ereignisse zu.</span><span class="sxs-lookup"><span data-stu-id="6355c-220">Follow the same process and assign respective tooltip objects to their same **MarsCuriosityRover** parts **While Looking At Target ()** & **On Look Away ()** events.</span></span>

<span data-ttu-id="6355c-221">Um Eye-Tracking zu aktivieren, befolgen Sie diese [Richtlinien](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).</span><span class="sxs-lookup"><span data-stu-id="6355c-221">To enable eye tracking, please follow these [guidelines](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).</span></span>

## <a name="congratulations"></a><span data-ttu-id="6355c-222">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="6355c-222">Congratulations</span></span>

<span data-ttu-id="6355c-223">In diesem Tutorial haben Sie gelernt, eine Mixed Reality-Erfahrung zu entwickeln, die Benutzeroberflächenelemente, 3D-Modellbearbeitung, Modellclipping und Funktionen für Eye-Tracking zeigt.</span><span class="sxs-lookup"><span data-stu-id="6355c-223">In this tutorial, you learned to build a mixed reality experience demonstrating UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span> <span data-ttu-id="6355c-224">In diesem Tutorial wurden NextButton und PreviousButton vorgestellt, mit denen Sie die Erfahrung des 3D-Modellbetrachters untersuchen können.</span><span class="sxs-lookup"><span data-stu-id="6355c-224">The tutorial provided you with NextButton and PreviousButton that let you explore the 3D model viewer experience.</span></span> <span data-ttu-id="6355c-225">Mit ClippingObjectButton haben Sie die Möglichkeit, Clippingobjekte zu aktivieren und das Clippingfeature zu erleben.</span><span class="sxs-lookup"><span data-stu-id="6355c-225">The ClippingObjectButton made you turn on clipping objects and experience clipping feature.</span></span> <span data-ttu-id="6355c-226">Das Tutorial hat Ihnen auch ein Element für Eye-Tracking vorgestellt, mit dem Sie die QuickInfos in der Darstellung hervorheben können.</span><span class="sxs-lookup"><span data-stu-id="6355c-226">The tutorial also provided you with an eye-tracking element to enable highlighting the tooltips in the experience.</span></span>

<span data-ttu-id="6355c-227">In der nächsten Lektion erfahren Sie, wie Sie eine Anwendung für Holographic Remoting für den PC erstellen, um HoloLens 2 zu einem beliebigen Zeitpunkt zu verbinden. Auf diese Weise können Sie 3D-Inhalte in Mixed Reality visualisieren.</span><span class="sxs-lookup"><span data-stu-id="6355c-227">In the next lesson, you will learn how to create a Holographic Remoting application for PC to connect HoloLens 2 at any point, providing a way to Visualize 3D content in mixed reality.</span></span>

[<span data-ttu-id="6355c-228">Nächste Lektion: 2. Erstellen einer Anwendung für Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="6355c-228">Next Lesson: 2. Create Holographic Remoting application</span></span>](mr-learning-pc-holographic-remoting-02.md)
