---
title: 'Tutorials zu Mehrbenutzerfunktionen: 1 Einrichten von Photon Unity Networking'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 2f5b55fe9c54e9e2c08177266c04a97d2302230e
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610777"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="f58fe-105">1. Einrichten von Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="f58fe-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="f58fe-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="f58fe-106">Overview</span></span>

<span data-ttu-id="f58fe-107">In diesem Tutorial erfahren Sie, wie Sie sich mithilfe des Photon Unity-Netzwerks (PUN) auf das Erstellen einer gemeinsamen Benutzeroberfläche vorbereiten.</span><span class="sxs-lookup"><span data-stu-id="f58fe-107">In this tutorial, you will learn how to prepare for creating a shared experience using Photon Unity Networking (PUN).</span></span> <span data-ttu-id="f58fe-108">Photon ist eine von mehreren Netzwerkoptionen, die Mixed Reality-Entwicklern zum Erstellen gemeinsamer Benutzererfahrungen zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="f58fe-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="f58fe-109">Sie erfahren, wie Sie eine Photon PUN-Anwendung erstellen, Photon PUN-Ressourcen in Ihr Unity-Projekt importieren und Ihr Unity-Projekt mit der Photon PUN-Anwendung verbinden.</span><span class="sxs-lookup"><span data-stu-id="f58fe-109">You will learn how to create a Photon PUN application, import Photon PUN assets into your Unity project, and connect your Unity project to the Photon PUN application.</span></span>

## <a name="objectives"></a><span data-ttu-id="f58fe-110">Ziele</span><span class="sxs-lookup"><span data-stu-id="f58fe-110">Objectives</span></span>

* <span data-ttu-id="f58fe-111">Erlernen des Erstellens einer Photon PUN-Anwendung</span><span class="sxs-lookup"><span data-stu-id="f58fe-111">Learn how to create a Photon PUN application</span></span>
* <span data-ttu-id="f58fe-112">Erfahren, wie die Photon PUN-Ressourcen gesucht und importiert werden</span><span class="sxs-lookup"><span data-stu-id="f58fe-112">Learn how to find and import the Photon PUN assets</span></span>
* <span data-ttu-id="f58fe-113">Erlernen, wie eine Verbindung Ihres Unity-Projekts mit der Photon PUN-Anwendung hergestellt wird</span><span class="sxs-lookup"><span data-stu-id="f58fe-113">Learn how to connect your Unity project to the Photon PUN application</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f58fe-114">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="f58fe-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="f58fe-115">Wenn Sie die Tutorialreihen [Tutorials zu den ersten Schritten](mrlearning-base.md) und [Azure Spatial Anchors-Tutorials](mrlearning-asa-ch1.md) noch nicht abgeschlossen haben, empfiehlt es sich, zunächst diese Tutorials abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="f58fe-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) and [Azure Spatial Anchors tutorials](mrlearning-asa-ch1.md) tutorial series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="f58fe-116">Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](install-the-tools.md) ist</span><span class="sxs-lookup"><span data-stu-id="f58fe-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="f58fe-117">Windows 10 SDK (10.0.18362.0 oder höher)</span><span class="sxs-lookup"><span data-stu-id="f58fe-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="f58fe-118">Grundlagenkenntnisse in der C#-Programmierung</span><span class="sxs-lookup"><span data-stu-id="f58fe-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="f58fe-119">Ein für die [Entwicklung konfiguriertes](using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät</span><span class="sxs-lookup"><span data-stu-id="f58fe-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="f58fe-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.2.X und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform</span><span class="sxs-lookup"><span data-stu-id="f58fe-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="f58fe-121">Schließen Sie den Abschnitt [Erstellen einer Spatial Anchors-Ressource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) des Tutorials [Schnellstart: Erstellen einer Unity HoloLens-App, die Azure Spatial Anchors verwendet](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) ab.</span><span class="sxs-lookup"><span data-stu-id="f58fe-121">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f58fe-122">Die empfohlene Unity-Version für diese Tutorialreihe ist Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="f58fe-122">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="f58fe-123">Diese übertrifft alle Versionsanforderungen oder -empfehlungen, die in den oben verlinkten Voraussetzungen angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="f58fe-123">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="f58fe-124">Erstellen und Vorbereiten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="f58fe-124">Creating and preparing the Unity project</span></span>

<span data-ttu-id="f58fe-125">In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die MRTK-Entwicklung vor.</span><span class="sxs-lookup"><span data-stu-id="f58fe-125">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="f58fe-126">Befolgen Sie zu diesem Zweck zunächst die Anweisungen unter [Initialisieren des Projekts und der ersten Anwendung](mrlearning-base-ch1.md), jedoch ohne die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihrem Gerät](mrlearning-base-ch1.md#build-your-application-to-your-device), die die folgenden Schritte beinhalten:</span><span class="sxs-lookup"><span data-stu-id="f58fe-126">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="f58fe-127">[Erstellen eines neuen Unity-Projekts](mrlearning-base-ch1.md#create-new-unity-project), das mit einem passenden Namen bezeichnet wird, beispielsweise *MRTK-Tutorials*</span><span class="sxs-lookup"><span data-stu-id="f58fe-127">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. [<span data-ttu-id="f58fe-128">Konfigurieren des Unity-Projekts für Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f58fe-128">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="f58fe-129">Importieren von TextMesh Pro Essential-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="f58fe-129">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="f58fe-130">Importieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="f58fe-130">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="f58fe-131">Konfigurieren des Unity-Projekts für das Mixed Reality-Toolkit</span><span class="sxs-lookup"><span data-stu-id="f58fe-131">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="f58fe-132">[Hinzufügen des Mixed Reality-Toolkits zur Unity-Szene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit), die dann einen passenden Namen erhält, beispielsweise *Mehrbenutzerfunktionen*</span><span class="sxs-lookup"><span data-stu-id="f58fe-132">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *MultiUserCapabilities*</span></span>

<span data-ttu-id="f58fe-133">Befolgen Sie dann die Anweisungen unter [Konfigurieren der Mixed Reality-Toolkitprofile (Option zum Ändern der Anzeige der räumlichen Wahrnehmung)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option), um das **DefaultHoloLens2ConfigurationProfile** als MRTK-Konfigurationsprofil für Ihre Szene festzulegen, und ändern Sie die Anzeigeoptionen für das Gittermodell zur räumlichen Wahrnehmung in **Occlusion** (Verdeckung).</span><span class="sxs-lookup"><span data-stu-id="f58fe-133">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="f58fe-134">Wie bereits in den oben verlinkten Anweisungen zum [Konfigurieren des Unity-Projekts für das Mixed Reality-Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) erwähnt, wird dringend empfohlen, MSBuild for Unity nicht zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="f58fe-134">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="f58fe-135">Konfigurieren der Funktionen</span><span class="sxs-lookup"><span data-stu-id="f58fe-135">Configuring the capabilities</span></span>

<span data-ttu-id="f58fe-136">Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen) aus, um das Fenster mit den Player-Einstellungen zu öffnen, und suchen Sie dann den Abschnitt **Player** >  **Publishing Settings** (Player > Veröffentlichungseinstellungen):</span><span class="sxs-lookup"><span data-stu-id="f58fe-136">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-1.png)

<span data-ttu-id="f58fe-138">Scrollen Sie in den **Publishing Settings** nach unten zum Abschnitt **Capabilities** (Funktionen), und vergewissern Sie sich, dass die Funktionen **InternetClient**, **Microphone** und **SpatialPerception**, die Sie im Rahmen der Erstellung des Projekts zu Beginn des Tutorials erstellt haben, aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="f58fe-138">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="f58fe-139">Aktivieren Sie dann die Funktionen **InternetClientServer**, **PrivateNetworkClientServer** und **RemovableStorage**:</span><span class="sxs-lookup"><span data-stu-id="f58fe-139">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, and **RemovableStorage** capabilities:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-2.png)

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="f58fe-141">Hinzufügen von integrierten Unity-Paketen</span><span class="sxs-lookup"><span data-stu-id="f58fe-141">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="f58fe-142">In diesem Abschnitt installieren Sie das integrierte Unity AR Foundation-Paket, da es vom Azure Spatial Anchors SDK benötigt wird, das Sie im nächsten Abschnitt importieren.</span><span class="sxs-lookup"><span data-stu-id="f58fe-142">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="f58fe-143">Wählen Sie im Unity-Menü **Window** > **Package Manager** (Fenster > Paket-Manager) aus:</span><span class="sxs-lookup"><span data-stu-id="f58fe-143">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="f58fe-145">Es kann einige Sekunden dauern, bis das AR Foundation-Paket in der Liste angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="f58fe-145">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="f58fe-146">Wählen Sie im Paket-Manager-Fenster die Option **AR Foundation** aus, und installieren Sie das Paket, indem Sie auf die Schaltfläche **Installieren** klicken:</span><span class="sxs-lookup"><span data-stu-id="f58fe-146">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="f58fe-148">Importieren der Tutorialressourcen</span><span class="sxs-lookup"><span data-stu-id="f58fe-148">Importing the tutorial assets</span></span>

<span data-ttu-id="f58fe-149">Laden Sie die folgenden benutzerdefinierten Unity-Pakete herunter, und **importieren** Sie sie **in der Reihenfolge, in der sie aufgelistet sind**:</span><span class="sxs-lookup"><span data-stu-id="f58fe-149">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="f58fe-150">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (Version 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="f58fe-150">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="f58fe-151">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="f58fe-151">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="f58fe-152">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="f58fe-152">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)
* [<span data-ttu-id="f58fe-153">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="f58fe-153">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="f58fe-154">Wenn Sie eine Auffrischung zum Importieren eines benutzerdefinierten Unity-Pakets benötigen, lesen Sie die Anweisungen unter [Importieren des Mixed Reality-Toolkits](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="f58fe-154">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="f58fe-155">Nach dem Importieren der Tutorialressourcen sollte Ihr Projektfenster ähnlich wie die folgende Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="f58fe-155">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="f58fe-157">Nach dem Importieren des Pakets mit den MultiUserCapabilities-Tutorialressourcen werden im Konsolenfenster mehrere [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246)-Fehler angezeigt, die besagen, dass der Typ oder Namespace fehlt.</span><span class="sxs-lookup"><span data-stu-id="f58fe-157">After importing the MultiUserCapabilities tutorial assets package, you will see several [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) errors in the Console window stating that the type or namespace is missing.</span></span> <span data-ttu-id="f58fe-158">Dies ist das erwartungsgemäße Verhalten, das im nächsten Abschnitt durch das Importieren der Photon-Ressourcen behoben wird.</span><span class="sxs-lookup"><span data-stu-id="f58fe-158">This is to be expected and will be resolved in the next section when you import the Photon assets.</span></span>

## <a name="importing-the-photon-assets"></a><span data-ttu-id="f58fe-159">Importieren der Photon-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="f58fe-159">Importing the Photon assets</span></span>

<span data-ttu-id="f58fe-160">In diesem Abschnitt importieren Sie die PUN-Ressourcen (Photon Unity Network) aus dem Unity Asset Store.</span><span class="sxs-lookup"><span data-stu-id="f58fe-160">In this section, you will import the Photon Unity Network (PUN) assets from Unity's Asset Store.</span></span>

<span data-ttu-id="f58fe-161">Wählen Sie im Unity-Menü **Window** > **Asset Store** (Fenster > Asset Store) aus, um das Asset Store-Fenster zu öffnen, suchen Sie unter „Exit Games“ **PUN 2 - FREE** aus, und klicken Sie dann auf die **Download**-Schaltfläche, um das Ressourcenpaket auf Ihr Unity-Konto herunterzuladen:</span><span class="sxs-lookup"><span data-stu-id="f58fe-161">In the Unity menu, select **Window** > **Asset Store** to open the Asset Store window, search for and select **PUN 2 - FREE** from Exit Games, and then click the **Download** button to download the asset package to your Unity account:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-1.png)

<span data-ttu-id="f58fe-163">Wenn der Download abgeschlossen ist, klicken Sie auf die **Import**-Schaltfläche, um das Fenster Import Unity Package (Unity-Paket importieren) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="f58fe-163">When the download is complete, click the **Import** button to open the Import Unity Package window:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-2.png)

<span data-ttu-id="f58fe-165">Klicken Sie im Import Unity Package-Fenster (Unity-Paket importieren) auf die Schaltfläche **All** (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Import** (Importieren), um die Assets zu importieren:</span><span class="sxs-lookup"><span data-stu-id="f58fe-165">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-3.png)

<span data-ttu-id="f58fe-167">Nachdem Unity den Importvorgang abgeschlossen hat, wird das Fenster des PUN-Assistenten mit geöffnetem PUN-Setupmenü geladen. Für den Augenblick können Sie dieses Fenster ignorieren oder schließen:</span><span class="sxs-lookup"><span data-stu-id="f58fe-167">Once Unity has completed the import process, the Pun Wizard window will appear with the PUN Setup menu loaded, you can ignore or close this window for now:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-4.png)

## <a name="setting-up-photon"></a><span data-ttu-id="f58fe-169">Einrichten von Photon</span><span class="sxs-lookup"><span data-stu-id="f58fe-169">Setting up Photon</span></span>

<span data-ttu-id="f58fe-170">In diesem Abschnitt erstellen Sie ein Photon-Konto, falls Sie noch keins besitzen, und erstellen eine neue PUN-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="f58fe-170">In this section, you will create a Photon account, if you don't already have one, and create a new PUN application.</span></span>

<span data-ttu-id="f58fe-171">Navigieren Sie zum Photon-<a href="https://dashboard.photonengine.com/account/signin" target="_blank">Dashboard</a>, und melden Sie sich an, wenn Sie bereits über ein Konto verfügen, das Sie verwenden möchten, oder klicken Sie andernfalls auf den Link **Create One** (Konto erstellen), und befolgen Sie die Anweisungen zum Registrieren eines neuen Kontos:</span><span class="sxs-lookup"><span data-stu-id="f58fe-171">Navigate to the Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> and sign in if you already have an account you want to use, otherwise, click the **Create One** link and follow the instructions to register a new account:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-1.png)

<span data-ttu-id="f58fe-173">Nachdem Sie sich angemeldet haben, klicken Sie auf die Schaltfläche **Create a New App** (Neue App erstellen):</span><span class="sxs-lookup"><span data-stu-id="f58fe-173">Once signed in, click the **Create a New App** button:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-2.png)

<span data-ttu-id="f58fe-175">Geben Sie auf der Seite „Create a New Application“ (Neue Anwendung erstellen) die folgenden Werte ein:</span><span class="sxs-lookup"><span data-stu-id="f58fe-175">On the Create a New Application page, enter the following values:</span></span>

* <span data-ttu-id="f58fe-176">Wählen Sie als Photon-Typ „Photon PUN“ aus</span><span class="sxs-lookup"><span data-stu-id="f58fe-176">For Photon Type, select Photon PUN</span></span>
* <span data-ttu-id="f58fe-177">Geben Sie als Namen einen passenden Namen ein, beispielsweise _MRTK-Tutorials_</span><span class="sxs-lookup"><span data-stu-id="f58fe-177">For Name, enter a suitable name, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="f58fe-178">Geben Sie als Beschreibung optional eine passende Beschreibung ein</span><span class="sxs-lookup"><span data-stu-id="f58fe-178">For Description, optionally enter a suitable description</span></span>
* <span data-ttu-id="f58fe-179">Lassen Sie das Feld „URL“ leer</span><span class="sxs-lookup"><span data-stu-id="f58fe-179">For Url, leave the field empty</span></span>

<span data-ttu-id="f58fe-180">Klicken Sie dann auf die Schaltfläche **Create** (Erstellen), um die neue Anwendung zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="f58fe-180">Then click the **Create** button to create the new application:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-3.png)

<span data-ttu-id="f58fe-182">Nachdem Photon den Erstellungsvorgang abgeschlossen hat, wird die neue PUN-Anwendung auf Ihrem Dashboard angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f58fe-182">Once Photon has finished the creation process, the new PUN application will appear on your dashboard:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a><span data-ttu-id="f58fe-184">Verbinden des Unity-Projekts mit der PUN-Anwendung</span><span class="sxs-lookup"><span data-stu-id="f58fe-184">Connecting the Unity project to the PUN application</span></span>

<span data-ttu-id="f58fe-185">In diesem Abschnitt verbinden Sie Ihr Unity-Projekt mit der PUN-Anwendung, die Sie im vorherigen Abschnitt erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="f58fe-185">In this section, you will connect your Unity project to the PUN application you created in the previous section.</span></span>

<span data-ttu-id="f58fe-186">Klicken Sie auf dem Photon-Dashboard auf das Feld **App-ID**, um die App-ID anzuzeigen, und kopieren Sie sie dann in die Zwischenablage:</span><span class="sxs-lookup"><span data-stu-id="f58fe-186">On the Photon dashboard, click the **App ID** field to reveal the app ID, then copy it to your clipboard:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-1.png)

<span data-ttu-id="f58fe-188">Wählen Sie im Unity-Menü **Window** > **Photon Unity Networking** > **PUN Wizard** (Fenster > Photon Unity-Netzwerk > PUN-Assistent) aus, um das Fenster des Pun-Assistenten zu öffnen, klicken Sie auf die Schaltfläche **Setup Project** (Projekt einrichten), um das PUN-Setupmenü zu öffnen, und konfigurieren Sie es wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f58fe-188">In the Unity menu, select **Window** > **Photon Unity Networking** > **PUN Wizard** to open the Pun Wizard window, click the **Setup Project** button to open the PUN Setup menu, and configure it as follows:</span></span>

* <span data-ttu-id="f58fe-189">Fügen Sie im Feld **AppId or Email** (AppID oder E-Mail) die PUN-App-ID ein, die Sie im vorherigen Schritt kopiert hatten</span><span class="sxs-lookup"><span data-stu-id="f58fe-189">In the **AppId or Email** field, paste the PUN app ID you copied in the previous step</span></span>

<span data-ttu-id="f58fe-190">Klicken Sie anschließend auf die Schaltfläche **Setup Project** (Projekt einrichten), um die AppID zu übernehmen:</span><span class="sxs-lookup"><span data-stu-id="f58fe-190">Then click the **Setup Project** button to apply the app ID:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-2.png)

<span data-ttu-id="f58fe-192">Nachdem Unity den PUN-Setupvorgang abgeschlossen hat, wird im PUN-Setupmenü die Meldung **Done!** (Fertig!) angezeigt</span><span class="sxs-lookup"><span data-stu-id="f58fe-192">Once Unity has finished the PUN setup process, the PUN Setup menu will display the message **Done!**</span></span> <span data-ttu-id="f58fe-193">und automatisch im Projektfenster die Ressource **PhotonServerSettings** ausgewählt, sodass deren Eigenschaften im Inspektorfenster angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="f58fe-193">and automatically select the **PhotonServerSettings** asset in the Project window so its properties are displayed in the Inspector window:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="f58fe-195">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="f58fe-195">Congratulations</span></span>

<span data-ttu-id="f58fe-196">Sie haben erfolgreich eine Photon PUN-Anwendung erstellt und sie mit Ihrem Unity-Projekt verbunden.</span><span class="sxs-lookup"><span data-stu-id="f58fe-196">You have successfully created a Photon PUN application and connected it to your Unity project.</span></span> <span data-ttu-id="f58fe-197">Der nächste Schritt besteht im Zulassen von Verbindungen mit anderen Benutzern, sodass sich mehrere Benutzer gegenseitig sehen können.</span><span class="sxs-lookup"><span data-stu-id="f58fe-197">Your next step is to allow connections with other users so that multiple users can see each other.</span></span>

<span data-ttu-id="f58fe-198">[Nächstes Tutorial: 2. Verbinden mehrerer Benutzer](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="f58fe-198">[Next tutorial: 2. Connecting multiple users](mrlearning-sharing(photon)-ch2.md)</span></span>
