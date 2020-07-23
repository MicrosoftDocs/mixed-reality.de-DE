---
title: 'Tutorials zu Azure Speech-Diensten: 1 Integrieren und Verwenden von Spracherkennung und Transkription'
description: In diesem Kurs erfahren Sie, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: f376ab268e9c2869e48b325fa728672a16ee6d32
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303681"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="e7617-105">1. Integrieren und Verwenden von Spracherkennung und Transkription</span><span class="sxs-lookup"><span data-stu-id="e7617-105">1. Integrating and using speech recognition and transcription</span></span>

## <a name="overview"></a><span data-ttu-id="e7617-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="e7617-106">Overview</span></span>


<span data-ttu-id="e7617-107">In dieser Tutorialreihe erstellen Sie eine Mixed Reality-Anwendung, die die Verwendung von Azure Speech Services mit der HoloLens 2 untersucht.</span><span class="sxs-lookup"><span data-stu-id="e7617-107">In this tutorial series, you will create a Mixed Reality application that explores the use of Azure Speech Services with the HoloLens 2.</span></span> <span data-ttu-id="e7617-108">Wenn Sie diese Tutorialreihe durcharbeiten, können Sie das Mikrofon Ihres Geräts verwenden, um Spracheingaben in Echtzeit in Text zu übertragen, Ihre Sprache in andere Sprachen zu übersetzen und die Funktion zur Absichtserkennung nutzen, um Sprachbefehle mithilfe von künstlicher Intelligenz zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="e7617-108">When you complete this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Intent recognition feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="e7617-109">Ziele</span><span class="sxs-lookup"><span data-stu-id="e7617-109">Objectives</span></span>

* <span data-ttu-id="e7617-110">Lernen, wie sich die Azure Speech Services in eine HoloLens 2-Anwendung integrieren lassen</span><span class="sxs-lookup"><span data-stu-id="e7617-110">Learn how to integrate Azure Speech Services with a HoloLens 2 application</span></span>
* <span data-ttu-id="e7617-111">Lernen, wie die Spracherkennung zum Umwandeln in Text verwendet werden kann</span><span class="sxs-lookup"><span data-stu-id="e7617-111">Learn how to use speech recognition to transcribe text</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e7617-112">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="e7617-112">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="e7617-113">Wenn Sie die Reihe [Tutorials zu den ersten Schritten](mr-learning-base-01.md) noch nicht abgeschlossen haben, empfiehlt es sich, zunächst diese Tutorials abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="e7617-113">If you have not completed the [Getting started tutorials](mr-learning-base-01.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="e7617-114">Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](install-the-tools.md) ist</span><span class="sxs-lookup"><span data-stu-id="e7617-114">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="e7617-115">Windows 10 SDK (10.0.18362.0 oder höher)</span><span class="sxs-lookup"><span data-stu-id="e7617-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="e7617-116">Grundlagenkenntnisse in der C#-Programmierung</span><span class="sxs-lookup"><span data-stu-id="e7617-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="e7617-117">Ein für die [Entwicklung konfiguriertes](using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät</span><span class="sxs-lookup"><span data-stu-id="e7617-117">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="e7617-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.2.X und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform</span><span class="sxs-lookup"><span data-stu-id="e7617-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e7617-119">Die empfohlene Unity-Version für diese Tutorialreihe ist Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="e7617-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="e7617-120">Diese übertrifft alle Versionsanforderungen oder -empfehlungen, die in den oben verlinkten Voraussetzungen angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="e7617-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="e7617-121">Erstellen und Vorbereiten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="e7617-121">Creating and preparing the Unity project</span></span>

<span data-ttu-id="e7617-122">In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die MRTK-Entwicklung vor.</span><span class="sxs-lookup"><span data-stu-id="e7617-122">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="e7617-123">Befolgen Sie zu diesem Zweck zunächst die Anweisungen unter [Initialisieren des Projekts und der ersten Anwendung](mr-learning-base-02.md), jedoch ohne die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihrem Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2), die die folgenden Schritte beinhalten:</span><span class="sxs-lookup"><span data-stu-id="e7617-123">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="e7617-124">[Erstellen eines neuen Unity-Projekts](mr-learning-base-02.md#creating-the-unity-project), das mit einem passenden Namen bezeichnet wird, beispielsweise *MRTK-Tutorials*</span><span class="sxs-lookup"><span data-stu-id="e7617-124">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="e7617-125">Wechseln der Buildplattform</span><span class="sxs-lookup"><span data-stu-id="e7617-125">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
3. [<span data-ttu-id="e7617-126">Importieren der TextMeshPro Essential-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="e7617-126">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="e7617-127">Importieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="e7617-127">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="e7617-128">Konfigurieren des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="e7617-128">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
6. <span data-ttu-id="e7617-129">[Erstellen und Konfigurieren der Szene](mr-learning-base-02.md#creating-and-configuring-the-scene) und Bezeichnen der Szene mit einem passenden Namen, z. B. *AzureSpeechServices*</span><span class="sxs-lookup"><span data-stu-id="e7617-129">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureSpeechServices*</span></span>

<span data-ttu-id="e7617-130">Befolgen Sie dann die Anweisungen unter [Ändern der Anzeigeoption der räumlichen Wahrnehmung](mr-learning-base-03.md#changing-the-spatial-awareness-display-option), um das **DefaultHoloLens2ConfigurationProfile** als MRTK-Konfigurationsprofil für Ihre Szene festzulegen, und ändern Sie die Anzeigeoptionen für das Gittermodell zur räumlichen Wahrnehmung in **Occlusion** (Verdeckung).</span><span class="sxs-lookup"><span data-stu-id="e7617-130">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="configuring-the-speech-commands-start-behavior"></a><span data-ttu-id="e7617-131">Konfigurieren des Startverhaltens der Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="e7617-131">Configuring the speech commands start behavior</span></span>

<span data-ttu-id="e7617-132">Da Sie das Speech SDK für die Spracherkennung und -Transkription verwenden, müssen Sie die MRTK-Sprachbefehle so konfigurieren, dass sie die Funktionalität des Speech SDKs nicht beeinträchtigen.</span><span class="sxs-lookup"><span data-stu-id="e7617-132">Because you will use the Speech SDK for speech recognition and transcription you need to configure the MRTK Speech Commands so they do not interfere with the Speech SDK functionality.</span></span> <span data-ttu-id="e7617-133">Um dies zu erreichen, können Sie das Startverhalten der Sprachbefehle vom automatischen Start auf manuellen Start umstellen.</span><span class="sxs-lookup"><span data-stu-id="e7617-133">To achieve this you can change the speech commands start behavior from Auto Start to Manual Start.</span></span>

<span data-ttu-id="e7617-134">Wählen Sie bei im Hierarchiefenster ausgewähltem **MixedRealityToolkit**-Objekt im Inspektorfenster die Registerkarte**Input** (Eingabe) aus, klonen Sie das **DefaultHoloLens2InputSystemProfile** und das **DefaultMixedRealitySpeechCommandsProfile**, und ändern Sie dann die Sprachbefehle **Start Behavior** (Startverhalten) in **Manual Start** (Manueller Start):</span><span class="sxs-lookup"><span data-stu-id="e7617-134">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, select the **Input** tab, clone the **DefaultHoloLens2InputSystemProfile** and the **DefaultMixedRealitySpeechCommandsProfile**, and then change the speech commands **Start Behavior** to **Manual Start**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="e7617-136">Wenn Sie eine Auffrischung zum Klonen und Konfigurieren von MRTK-Profilen benötigen, lesen Sie die Anweisungen in [Konfigurieren der Mixed Reality Toolkit-Profile](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="e7617-136">For a reminder on how to clone and configure MRTK profiles, you can refer to the [Configuring the Mixed Reality Toolkit profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="e7617-137">Konfigurieren der Funktionen</span><span class="sxs-lookup"><span data-stu-id="e7617-137">Configuring the capabilities</span></span>

<span data-ttu-id="e7617-138">Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen) aus, um das Fenster mit den Player-Einstellungen zu öffnen, und suchen Sie dann den Abschnitt **Player** >  **Publishing Settings** (Player > Veröffentlichungseinstellungen):</span><span class="sxs-lookup"><span data-stu-id="e7617-138">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-1.png)

<span data-ttu-id="e7617-140">Scrollen Sie in den **Publishing Settings** nach unten zum Abschnitt **Capabilities** (Funktionen), und vergewissern Sie sich, dass die Funktionen **InternetClient**, **Microphone** und **SpatialPerception**, die Sie im Rahmen der Erstellung des Projekts zu Beginn des Tutorials erstellt haben, aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="e7617-140">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="e7617-141">Aktivieren Sie dann die Funktionen **InternetClientServer** und **PrivateNetworkClientServer**:</span><span class="sxs-lookup"><span data-stu-id="e7617-141">Then, enable the **InternetClientServer** and **PrivateNetworkClientServer** capabilities:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="e7617-143">Importieren der Tutorialressourcen</span><span class="sxs-lookup"><span data-stu-id="e7617-143">Importing the tutorial assets</span></span>

<span data-ttu-id="e7617-144">Laden Sie die folgenden benutzerdefinierten Unity-Pakete herunter, und **importieren** Sie sie **in der Reihenfolge, in der sie aufgelistet sind**:</span><span class="sxs-lookup"><span data-stu-id="e7617-144">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="e7617-145">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (latest version)</span><span class="sxs-lookup"><span data-stu-id="e7617-145">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (latest version)</span></span>
* [<span data-ttu-id="e7617-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="e7617-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="e7617-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="e7617-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-speech-services-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="e7617-148">Wenn Sie eine Auffrischung zum Importieren eines benutzerdefinierten Unity-Pakets benötigen, lesen Sie die Anweisungen unter [Importieren des Mixed Reality-Toolkits](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="e7617-148">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="e7617-149">Nach dem Importieren der Tutorialressourcen sollte Ihr Projektfenster ähnlich wie die folgende Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="e7617-149">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section4-step1-1.png)

## <a name="preparing-the-scene"></a><span data-ttu-id="e7617-151">Vorbereiten der Szene</span><span class="sxs-lookup"><span data-stu-id="e7617-151">Preparing the scene</span></span>

<span data-ttu-id="e7617-152">In diesem Abschnitt bereiten Sie die Szene vor, indem Sie das Prefab für das Tutorial hinzufügen und die Komponente „Lunarcom Controller (Skript)“ konfigurieren, um Ihre Szene zu steuern.</span><span class="sxs-lookup"><span data-stu-id="e7617-152">In this section, you will prepare the scene by adding the tutorial prefab and configure the Lunarcom Controller (Script) component to control your scene.</span></span>

<span data-ttu-id="e7617-153">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs**, und ziehen Sie das **Lunarcom**-Prefab auf das Hierarchiefenster, um es Ihrer Szene hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="e7617-153">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** folder and drag the **Lunarcom** prefab into the Hierarchy window to add it to your scene:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-1.png)

<span data-ttu-id="e7617-155">Verwenden Sie bei im Hierarchiefenster ausgewähltem **Lunarcom**-Objekt im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um die Komponente **Lunarcom Controller (Script)** zum Lunarcom-Objekt hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="e7617-155">With the **Lunarcom** object still selected in the Hierarchy window, in the Inspector window, use the **Add Component** button to add the **Lunarcom Controller (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> <span data-ttu-id="e7617-157">Die Komponente „Lunarcom Controller (Script)“ ist kein Bestandteil des MRTK.</span><span class="sxs-lookup"><span data-stu-id="e7617-157">The Lunarcom Controller (Script) component is not part of MRTK.</span></span> <span data-ttu-id="e7617-158">Sie wurde zusammen mit den Ressourcen für dieses Tutorial zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="e7617-158">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="e7617-159">Klappen Sie das noch ausgewählte **Lunarcom**-Objekt auf, um seine untergeordneten Objekte anzuzeigen, und ziehen Sie dann das **Terminal**-Objekt auf das **Terminal**-Feld der Lunarcom Controller (Script)-Komponente:</span><span class="sxs-lookup"><span data-stu-id="e7617-159">With the **Lunarcom** object still selected, expand it to reveal its child objects, then drag the **Terminal** object into the Lunarcom Controller (Script) component's **Terminal** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-3.png)

<span data-ttu-id="e7617-161">Klappen Sie bei noch ausgewähltem **Lunarcom**-Objekt das Terminal-Objekt auf, um seine untergeordneten Objekte anzuzeigen, ziehen Sie dann das **ConnectionLight**-Objekt auf das **ConnectionLight**-Feld der Lunarcom Controller (Script)-Komponente und das **OutputText**-Objekt auf das **Output Text**-Feld:</span><span class="sxs-lookup"><span data-stu-id="e7617-161">With the **Lunarcom** object still selected, expand the Terminal object to reveal its child objects, then drag the **ConnectionLight** object into the Lunarcom Controller (Script) component's **Connection Light** field and the **OutputText** object into the **Output Text** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-4.png)

<span data-ttu-id="e7617-163">Klappen Sie bei noch ausgewähltem **Lunarcom**-Objekt das Buttons-Objekt auf, um seine untergeordneten Objekte anzuzeigen, und klappen Sie dann im Inspektorfenster die **Buttons**-Liste auf, legen Sie seine **Size** (Größe) auf 3 fest, und ziehen Sie die Objekte **MicButton**, **SatelliteButton** und **RocketButton** auf die **Element**-Felder 0, 1 bzw. 2:</span><span class="sxs-lookup"><span data-stu-id="e7617-163">With the **Lunarcom** object still selected, expand the Buttons object to reveal its child objects, and then in the Inspector window, expand the **Buttons** list, set its **Size** to 3, and drag the **MicButton**, **SatelliteButton**, and **RocketButton** objects into the **Element** 0, 1, and 2 fields respectively:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a><span data-ttu-id="e7617-165">Verbinden des Unity-Projekts mit der Azure-Ressource</span><span class="sxs-lookup"><span data-stu-id="e7617-165">Connecting the Unity project to the Azure resource</span></span>

<span data-ttu-id="e7617-166">Um Azure Speech Services zu verwenden, müssen Sie eine Azure-Ressource erstellen und einen API-Schlüssel für den Speech Service abrufen.</span><span class="sxs-lookup"><span data-stu-id="e7617-166">To use Azure Speech Services, you need to create an Azure resource and obtain an API key for the Speech Service.</span></span> <span data-ttu-id="e7617-167">Befolgen Sie die Anweisungen unter [Speech Service kostenlos testen](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started), und notieren Sie sich Ihre Dienstregion (auch als Standort bezeichnet) und den API-Schlüssel (auch als Schlüssel1 oder Schlüssel2 bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="e7617-167">Follow the [Try the Speech service for free](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) instructions and make a note of your service region (also known as Location) and API key (also known as Key1 or Key2).</span></span>

<span data-ttu-id="e7617-168">Wählen Sie in Ihrem Hierarchiefenster das **Lunarcom**-Objekt aus, suchen Sie dann im Inspektorfenster den Abschnitt **Speech SDK Credentials** der **Lunarcom Controller (Script)** -Komponente, und konfigurieren Sie ihn wie folgt:</span><span class="sxs-lookup"><span data-stu-id="e7617-168">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Controller (Script)** component's **Speech SDK Credentials** section and configure it as follows:</span></span>

* <span data-ttu-id="e7617-169">Geben Sie im Feld **Speech Service API Key** Ihren API-Schlüssel (Schlüssel1 oder Schlüssel2) ein</span><span class="sxs-lookup"><span data-stu-id="e7617-169">In the **Speech Service API Key** field, enter your API key (Key1 or Key2)</span></span>
* <span data-ttu-id="e7617-170">Geben Sie im Feld **Speech Service Region** Ihre Dienstregion (Standort) ein. Verwenden Sie dazu Kleinbuchstaben, und entfernen Sie alle Leerzeichen.</span><span class="sxs-lookup"><span data-stu-id="e7617-170">In the **Speech Service Region** field, enter your service region (Location) using lowercase letters and spaces removed</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a><span data-ttu-id="e7617-172">Verwenden der Spracherkennung zum Transkribieren von Sprache</span><span class="sxs-lookup"><span data-stu-id="e7617-172">Using speech recognition to transcribe speech</span></span>

<span data-ttu-id="e7617-173">Wählen Sie im Hierarchiefenster das **Lunarcom**-Objekt aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um dem Lunarcom-Objekt die Komponente **Lunarcom Speech Recognizer (Script)** hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="e7617-173">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Speech Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> <span data-ttu-id="e7617-175">Die Komponente „Lunarcom Speech Recognizer (Script)“ ist kein Bestandteil des MRTK.</span><span class="sxs-lookup"><span data-stu-id="e7617-175">The Lunarcom Speech Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="e7617-176">Sie wurde zusammen mit den Ressourcen für dieses Tutorial zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="e7617-176">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="e7617-177">Wenn Sie jetzt in den Spielmodus wechseln, können Sie die Spracherkennung testen, indem Sie zuerst auf die Mikrofonschaltfläche klicken.</span><span class="sxs-lookup"><span data-stu-id="e7617-177">If you now enter Game mode, you can test the speech recognition by first pressing the microphone button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-2.png)

<span data-ttu-id="e7617-179">Falls Ihr Computer über ein Mikrofon verfügt, wird Ihre Sprache dann, wenn Sie etwas sagen, im Terminalbereich transkribiert:</span><span class="sxs-lookup"><span data-stu-id="e7617-179">Then, assuming your computer has a microphone, when you say something, your speech will be transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-3.png)


> [!CAUTION]
> <span data-ttu-id="e7617-181">Die Anwendung muss eine Verbindung mit Azure herstellen, achten Sie also darauf, dass Ihr Computer/Gerät mit dem Internet verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="e7617-181">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="e7617-182">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="e7617-182">Congratulations</span></span>

<span data-ttu-id="e7617-183">Sie haben die von Azure unterstützte Spracherkennung implementiert.</span><span class="sxs-lookup"><span data-stu-id="e7617-183">You have implemented speech recognition powered by Azure.</span></span> <span data-ttu-id="e7617-184">Führen Sie die Anwendung auf Ihrem Gerät aus, um sicherzustellen, dass das Feature ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="e7617-184">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="e7617-185">Im nächsten Tutorial erfahren Sie, wie Sie Befehle mit der Azure-Spracherkennung ausführen.</span><span class="sxs-lookup"><span data-stu-id="e7617-185">In the next tutorial, you will learn how to execute commands using Azure speech recognition.</span></span>

[<span data-ttu-id="e7617-186">Nächstes Tutorial: 2. Verwenden der Spracherkennung zum Ausführen von Befehlen</span><span class="sxs-lookup"><span data-stu-id="e7617-186">Next tutorial: 2. Using speech recognition to execute commands</span></span>](mrlearning-speechSDK-ch2.md)
