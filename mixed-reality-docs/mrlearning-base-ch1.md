---
title: Tutorials zu den ersten Schritten – 2 Initialisieren des Projekts und der ersten Anwendung
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 9c219313ad6e73cde78efd8e5e718a466ebd6137
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554400"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="bd566-105">2. Initialisieren des Projekts und der ersten Anwendung</span><span class="sxs-lookup"><span data-stu-id="bd566-105">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="bd566-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="bd566-106">Overview</span></span>

<!-- TODO: Consider expanding to include summary of each tutorial in this tutorial series -->
<span data-ttu-id="bd566-107">In diesem ersten Tutorial lernen Sie einige der Funktionen kennen, die das <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality-Toolkit (MRTK)</a> bietet, starten Ihre erste Anwendung für das HoloLens 2-Gerät und stellen sie auf dem Gerät bereit.</span><span class="sxs-lookup"><span data-stu-id="bd566-107">In this first tutorial, you will learn about some of the capabilities the <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> has to offer, start your first application for the HoloLens 2, and deploy it to the device.</span></span>

## <a name="objectives"></a><span data-ttu-id="bd566-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="bd566-108">Objectives</span></span>

* <span data-ttu-id="bd566-109">Konfigurieren von Unity für die HoloLens-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="bd566-109">Configure Unity for HoloLens development</span></span>
* <span data-ttu-id="bd566-110">Importieren von Assets und Einrichten der Szene</span><span class="sxs-lookup"><span data-stu-id="bd566-110">Import assets and set up the scene</span></span>
* <span data-ttu-id="bd566-111">Visualisierung des Gittermodells für die Raumzuordnung, der Hand-Meshes und des Frameratenzählers</span><span class="sxs-lookup"><span data-stu-id="bd566-111">Visualization of the spatial mapping mesh, hand meshes, and the framerate counter</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bd566-112">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="bd566-112">Prerequisites</span></span>

* <span data-ttu-id="bd566-113">Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](install-the-tools.md) ist</span><span class="sxs-lookup"><span data-stu-id="bd566-113">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="bd566-114">Windows 10 SDK (10.0.18362.0 oder höher)</span><span class="sxs-lookup"><span data-stu-id="bd566-114">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="bd566-115">Grundlagenkenntnisse in der C#-Programmierung</span><span class="sxs-lookup"><span data-stu-id="bd566-115">Some basic C# programming ability</span></span>
* <span data-ttu-id="bd566-116">Ein für die [Entwicklung konfiguriertes](using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät</span><span class="sxs-lookup"><span data-stu-id="bd566-116">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="bd566-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.2.X und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform</span><span class="sxs-lookup"><span data-stu-id="bd566-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bd566-118">Die empfohlene Unity-Version für diese Tutorialreihe ist Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="bd566-118">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="bd566-119">Diese übertrifft alle Versionsanforderungen oder -empfehlungen, die in den oben verlinkten Voraussetzungen angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="bd566-119">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="create-new-unity-project"></a><span data-ttu-id="bd566-120">Erstellen eines neuen Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="bd566-120">Create new Unity project</span></span>

<span data-ttu-id="bd566-121">Starten Sie **Unity Hub**, wählen Sie die Registerkarte **Projects** (Projekte) aus, und klicken Sie auf den **Abwärtspfeil** neben der Schaltfläche **New** (Neu):</span><span class="sxs-lookup"><span data-stu-id="bd566-121">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-1.png)

<span data-ttu-id="bd566-123">Wählen Sie die Unity-Version aus, die im Abschnitt [Voraussetzungen](#prerequisites) oben angegeben ist:</span><span class="sxs-lookup"><span data-stu-id="bd566-123">Select the Unity version specified in the [Prerequisites](#prerequisites) section above:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-2.png)

<span data-ttu-id="bd566-125">Erstellen Sie im Fenster ein neues Projekt:</span><span class="sxs-lookup"><span data-stu-id="bd566-125">In the Create a new project window:</span></span>

* <span data-ttu-id="bd566-126">Vergewissern Sie sich, dass **Templates** (Vorlagen) auf **3D** festgelegt ist</span><span class="sxs-lookup"><span data-stu-id="bd566-126">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="bd566-127">Geben Sie einen passenden **Project Name** (Projektnamen) ein, z. B. _MRTK-Tutorials_</span><span class="sxs-lookup"><span data-stu-id="bd566-127">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="bd566-128">Wählen Sie eine geeignete **Location** (Speicherort) zum Speichern Ihres Projekts, z. B. _D:\MixedRealityLearning_</span><span class="sxs-lookup"><span data-stu-id="bd566-128">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="bd566-129">Klicken Sie auf die Schaltfläche **Create** (Erstellen), um das neue Unity-Projekt zu erstellen</span><span class="sxs-lookup"><span data-stu-id="bd566-129">Click the **Create** button to create and launch your new Unity project</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="bd566-131">Wenn Sie unter Windows arbeiten, müssen Sie den MAX_PATH-Grenzwert von 255 Zeichen beachten.</span><span class="sxs-lookup"><span data-stu-id="bd566-131">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="bd566-132">Dieser Grenzwert gilt auch für Unity und kann zu Fehlern beim Kompilieren führen, wenn ein Dateipfad länger als 255 Zeichen ist.</span><span class="sxs-lookup"><span data-stu-id="bd566-132">Unity is affected by these limits and may fail to compile if any file path is longer than 255 characters.</span></span> <span data-ttu-id="bd566-133">Daher empfiehlt es sich unbedingt, Ihr Unity-Projekt so nah wie möglich am Stamm des Laufwerks zu speichern.</span><span class="sxs-lookup"><span data-stu-id="bd566-133">Consequently, it is strongly recommended to store your Unity project as close to the root of the drive as possible.</span></span>

<span data-ttu-id="bd566-134">Warten Sie, bis Unity das Projekt erstellt hat:</span><span class="sxs-lookup"><span data-stu-id="bd566-134">Wait for Unity to create the project:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-4.png)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="bd566-136">Konfigurieren des Unity-Projekts für Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="bd566-136">Configure the Unity project for Windows Mixed Reality</span></span>

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

<span data-ttu-id="bd566-137">In diesem Abschnitt wechseln Sie die Erstellungsplattform und aktivieren Virtual Reality sowie räumliche Wahrnehmung.</span><span class="sxs-lookup"><span data-stu-id="bd566-137">In this section, you will switch build platform, enable virtual reality, and enable spatial perception.</span></span>

### <a name="1-switch-build-platform"></a><span data-ttu-id="bd566-138">1. Wechseln der Buildplattform</span><span class="sxs-lookup"><span data-stu-id="bd566-138">1. Switch build platform</span></span>

<span data-ttu-id="bd566-139">Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="bd566-139">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-1.png)

<span data-ttu-id="bd566-141">Wählen Sie im Build Settings-Fenster **Universal Windows Platform** (Universelle Windows-Plattform) aus, und klicken Sie auf die Schaltfläche **Switch Platform** (Plattform wechseln):</span><span class="sxs-lookup"><span data-stu-id="bd566-141">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-2.png)

<span data-ttu-id="bd566-143">Warten Sie, bis Unity den Wechsel der Plattform abgeschlossen hat:</span><span class="sxs-lookup"><span data-stu-id="bd566-143">Wait for Unity to finish switching the platform:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-3.png)

<span data-ttu-id="bd566-145">Wenn Unity den Plattformwechsel abgeschlossen hat, klicken Sie auf das rote **x**-Symbol, um das Build Settings-Fenster zu schließen:</span><span class="sxs-lookup"><span data-stu-id="bd566-145">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-4.png)

### <a name="2-enable-virtual-reality"></a><span data-ttu-id="bd566-147">2. Aktivieren von Virtual Reality</span><span class="sxs-lookup"><span data-stu-id="bd566-147">2. Enable virtual reality</span></span>

> [!NOTE]
> <span data-ttu-id="bd566-148">Das Aktivieren von Virtual Reality betrifft auch Mixed Reality- und Augmented Reality-Headsets, da es sich auf das Aktivieren der stereoskopischen Funktionen bezieht, d. h. auf das Rendering unterschiedlicher Bilder für jedes Auge.</span><span class="sxs-lookup"><span data-stu-id="bd566-148">Enabling virtual reality also applies to mixed reality and augmented reality headsets because it refers to enabling stereoscopic vision, i.e. rendering different images for each eye.</span></span>

<span data-ttu-id="bd566-149">Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen...) aus, um das Fenster „Project Settings“ (Projekteinstellungen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="bd566-149">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-1.png)

<span data-ttu-id="bd566-151">Wählen Sie im Project Settings-Fenster **Player** > **XR Settings** (Player > XR-Einstellungen) aus, um die XR-Einstellungen zu erweitern:</span><span class="sxs-lookup"><span data-stu-id="bd566-151">In the Project Settings window, select **Player** > **XR Settings** to expand the XR Settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-2.png)

<span data-ttu-id="bd566-153">Aktivieren Sie in den XR-Einstellungen das Kontrollkästchen **Virtual Reality Supported** (Virtual Reality-Unterstützung), um Virtual Reality zu aktivieren, klicken Sie dann auf das **+** -Symbol, und wählen Sie **Windows Mixed Reality** aus, um das Windows Mixed Reality SDK hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="bd566-153">In the XR Settings, check the **Virtual Reality Supported** checkbox to enable virtual reality, then click the **+** icon and select **Windows Mixed Reality** to add the Windows Mixed Reality SDK:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-3.png)

<span data-ttu-id="bd566-155">Warten Sie, bis Unity das SDK hinzugefügt hat:</span><span class="sxs-lookup"><span data-stu-id="bd566-155">Wait for Unity to finish adding the SDK:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-4.png)

<span data-ttu-id="bd566-157">Wenn Unity das Hinzufügen des SDK abgeschlossen hat, optimieren Sie die XR-Einstellungen wie folgt:</span><span class="sxs-lookup"><span data-stu-id="bd566-157">When Unity has finished adding the SDK, optimize the XR Settings as follows:</span></span>

* <span data-ttu-id="bd566-158">Legen Sie das **Depth Format** (Tiefenformat) für Windows Mixed Reality auf **16-bit depth** (16-Bit Tiefe) fest</span><span class="sxs-lookup"><span data-stu-id="bd566-158">Set Windows Mixed Reality **Depth Format** to **16-bit depth**</span></span>
* <span data-ttu-id="bd566-159">Aktivieren Sie das Windows Mixed Reality-Kontrollkästchen **Enable Depth Sharing** (Freigeben der Tiefe aktivieren)</span><span class="sxs-lookup"><span data-stu-id="bd566-159">Check the Windows Mixed Reality **Enable Depth Sharing** checkbox</span></span>
* <span data-ttu-id="bd566-160">Legen Sie den Stereo-**Rendering Mode\*** (Rendermodus) auf **Single Pass Instanced** (Single-Pass-Instanz) fest</span><span class="sxs-lookup"><span data-stu-id="bd566-160">Set Stereo **Rendering Mode\*** to **Single Pass Instanced**</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-5.png)

> [!TIP]
> <span data-ttu-id="bd566-162">Weitere Informationen zum Optimieren von Unity für Windows Mixed Reality finden Sie in der Dokumentation [Recommended settings for Unity](recommended-settings-for-unity.md) (Empfohlene Einstellungen für Unity).</span><span class="sxs-lookup"><span data-stu-id="bd566-162">To learn more about optimizing Unity for Windows Mixed Reality, you can refer to the [Recommended settings for Unity](recommended-settings-for-unity.md) documentation.</span></span>

### <a name="3-enable-spatial-perception"></a><span data-ttu-id="bd566-163">3. Aktivieren der räumlichen Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="bd566-163">3. Enable spatial perception</span></span>

> [!NOTE]
> <span data-ttu-id="bd566-164">Die Funktion „Räumliche Wahrnehmung“ ermöglicht das Visualisieren des Gittermodells für die Raumzuordnung auf Windows Mixed Reality-Geräten.</span><span class="sxs-lookup"><span data-stu-id="bd566-164">Spatial perception allows visualization of the spatial mapping mesh on Windows Mixed Reality devices.</span></span>

<span data-ttu-id="bd566-165">Wählen Sie im Project Settings-Fenster (Projekteinstellungen) **Player** > **Publishing Settings** (Player > Veröffentlichungseinstellungen) aus, um die Veröffentlichungseinstellungen auszuklappen:</span><span class="sxs-lookup"><span data-stu-id="bd566-165">In the Project Settings window, select **Player** > **Publishing Settings** to expand the Publishing Settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-1.png)

<span data-ttu-id="bd566-167">Scrollen Sie in den Veröffentlichungseinstellungen abwärts bis zum Abschnitt **Capabilities** (Funktionen), und aktivieren Sie das Kontrollkästchen **SpatialPerception** (Räumliche Wahrnehmung):</span><span class="sxs-lookup"><span data-stu-id="bd566-167">In the Publishing Settings, scroll down to the **Capabilities** section and check the **SpatialPerception** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-2.png)

<!-- TODO: Consider adding info about audio spatializer plugin setting -->

<span data-ttu-id="bd566-169">Schließen Sie das Project Settings-Fenster.</span><span class="sxs-lookup"><span data-stu-id="bd566-169">Close the Project Settings window.</span></span>

## <a name="import-textmesh-pro-essential-resources"></a><span data-ttu-id="bd566-170">Importieren von TextMesh Pro Essential Resources</span><span class="sxs-lookup"><span data-stu-id="bd566-170">Import TextMesh Pro Essential Resources</span></span>

> [!NOTE]
> <span data-ttu-id="bd566-171">Wir importieren dieses Paket, da es von den Elementen der Benutzeroberfläche des Mixed Reality Toolkit benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="bd566-171">We are importing this package because it is required by Mixed Reality Toolkit's UI elements.</span></span>

<span data-ttu-id="bd566-172">Wählen Sie im Unity-Menü **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Fenster > TextMeshPro > TMP Essential Resources importieren) aus:</span><span class="sxs-lookup"><span data-stu-id="bd566-172">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-1.png)

<span data-ttu-id="bd566-174">Klicken Sie im Import Unity Package-Fenster (Unity-Paket importieren) auf die Schaltfläche **All** (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Import** (Importieren), um die Assets zu importieren:</span><span class="sxs-lookup"><span data-stu-id="bd566-174">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-2.png)

## <a name="import-the-mixed-reality-toolkit"></a><span data-ttu-id="bd566-176">Importieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="bd566-176">Import the Mixed Reality Toolkit</span></span>

<span data-ttu-id="bd566-177">Laden Sie das benutzerdefinierte Unity-Paket herunter:</span><span class="sxs-lookup"><span data-stu-id="bd566-177">Download the Unity custom package:</span></span>

* [<span data-ttu-id="bd566-178">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="bd566-178">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)

<span data-ttu-id="bd566-179">Wählen Sie im Unity-Menü **Assets** > **Import Package** > **Custom Package...** (Assets > Paket importieren > Benutzerdefiniertes Paket...) aus, um das Fenster zum Importieren von Paketen zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="bd566-179">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-1.png)

<span data-ttu-id="bd566-181">Wählen Sie im Fenster „Import package...“ (Paket importieren...) das heruntergeladene **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage**-Paket aus, und klicken Sie auf die Schaltfläche **Open** (Öffnen):</span><span class="sxs-lookup"><span data-stu-id="bd566-181">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage** you downloaded and click the **Open** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-2.png)

<span data-ttu-id="bd566-183">Klicken Sie im Import Unity Package-Fenster (Unity-Paket importieren) auf die Schaltfläche **All** (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Import** (Importieren), um die Assets zu importieren:</span><span class="sxs-lookup"><span data-stu-id="bd566-183">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-3.png)

## <a name="configure-the-unity-project-for-the-mixed-reality-toolkit"></a><span data-ttu-id="bd566-185">Konfigurieren des Unity-Projekts für das Mixed Reality-Toolkit</span><span class="sxs-lookup"><span data-stu-id="bd566-185">Configure the Unity project for the Mixed Reality Toolkit</span></span>

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

<span data-ttu-id="bd566-186">Nachdem das Paket importiert wurde, sollte das MRTK Project Configurator-Fenster (MRTK-Projektkonfiguration) angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bd566-186">After the package has been imported, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="bd566-187">Wenn das nicht der Fall ist, öffnen Sie es, indem Sie im Unity-Menü **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality-Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) auswählen.</span><span class="sxs-lookup"><span data-stu-id="bd566-187">If it does not, open it by selecting **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** in the Unity menu.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-1.png)

<span data-ttu-id="bd566-189">Erweitern Sie im MRTK Project Configurator-Fenster den Abschnitt **Modify Configurations** (Konfigurationen ändern), <u>deaktivieren</u> Sie das Kontrollkästchen **Enable MSBuild for Unity** (MSBuild für Unity aktivieren), achten Sie darauf, dass alle anderen Optionen aktiviert sind, und klicken Sie auf die Schaltfläche **Apply** (Übernehmen), um die Einstellungen zu übernehmen:</span><span class="sxs-lookup"><span data-stu-id="bd566-189">In the MRTK Project Configurator window, expand the **Modify Configurations** section, <u>uncheck</u> the **Enable MSBuild for Unity** checkbox, ensure all other options are checked, and click the **Apply** button to apply the settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="bd566-191">MSBuild für Unity unterstützt möglicherweise nicht alle verwenden SDKs, und die Deaktivierung nach der erstmaligen Aktivierung kann schwierig sein.</span><span class="sxs-lookup"><span data-stu-id="bd566-191">MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="bd566-192">Es wird daher dringend empfohlen, MSBuild für Unity nicht zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="bd566-192">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configure-the-mixed-reality-toolkit"></a><span data-ttu-id="bd566-193">Konfigurieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="bd566-193">Configure the Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Add the Mixed Reality Toolkit to the Unity scene' -->

<span data-ttu-id="bd566-194">Wählen Sie im Unity-Menü **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Mixed Reality-Toolkit > Zu Szene hinzufügen und konfigurieren) aus, um Ihrer aktuellen Szene das Mixed Reality-Toolkit hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="bd566-194">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the Mixed Reality Toolkit to your current scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-1.png)

<span data-ttu-id="bd566-196">Überprüfen Sie bei im Hierarchiefenster ausgewähltem MixedRealityToolkit-Objekt im Inspektorfenster, ob das Konfigurationsprofil des Mixed Reality-Toolkits auf **DefaultMixedRealityToolkitConfigurationProfile** festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="bd566-196">With the MixedRealityToolkit object selected in the Hierarchy window, in the Inspector window, verify the Mixed Reality Toolkit configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-2.png)

> [!IMPORTANT]
> <span data-ttu-id="bd566-198">Normalerweise verwenden Sie zum Entwickeln für HoloLens 2 das DefaultHoloLens2ConfigurationProfile-Profil.</span><span class="sxs-lookup"><span data-stu-id="bd566-198">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens 2.</span></span> <span data-ttu-id="bd566-199">Für die Zwecke dieses Tutorials verwenden Sie jedoch das DefaultMixedRealityToolkitConfigurationProfile-Profil und wechseln dann im nächsten Tutorial [Erstellen der Benutzeroberfläche und Konfigurieren des Mixed Reality-Toolkits](mrlearning-base-ch2.md) zum DefaultHoloLens2ConfigurationProfile-Profil.</span><span class="sxs-lookup"><span data-stu-id="bd566-199">However, for the purpose of this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile, then in the next tutorial, [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

<span data-ttu-id="bd566-200">Wählen Sie im Unity-Menü **File** > **Save As...** (Datei > Speichern unter...) aus, um das Save Scene-Fenster (Szene speichern) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="bd566-200">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-3.png)

<span data-ttu-id="bd566-202">Navigieren Sie im Save Scene-Fenster zum Ordner **Scenes** (Szenen), geben Sie Ihrer Szene einen passenden Namen, beispielsweise _ErsteSchritte_, und klicken Sie auf die Schaltfläche **Save** (Speichern), um die Szene zu speichern:</span><span class="sxs-lookup"><span data-stu-id="bd566-202">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-4.png)

## <a name="build-your-application-to-your-device"></a><span data-ttu-id="bd566-204">Erstellen Ihrer Anwendung auf Ihrem Gerät</span><span class="sxs-lookup"><span data-stu-id="bd566-204">Build your application to your device</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="bd566-205">1. Erstellen des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="bd566-205">1. Build the Unity project</span></span>

<span data-ttu-id="bd566-206">Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="bd566-206">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="bd566-207">Klicken Sie im Build Settings-Fenster (Buildeinstellungen) auf die Schaltfläche **Add Open Scenes** (Geöffnete Szenen hinzufügen), um der Liste **Scenes In Build** (Szenen im Build) Ihre aktuelle Szene hinzuzufügen, und klicken Sie dann auf die Schaltfläche **Build** (Erstellen), um das Build Universal Windows Platform-Fenster (Erstellen für Universelle Windows-Plattform) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="bd566-207">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-1.png)

<span data-ttu-id="bd566-209">Wählen Sie im Build Universal Windows Platform-Fenster einen passenden Speicherort aus, um Ihren Build zu speichern, beispielsweise _D:\MixedRealityLearning\Builds_, erstellen Sie einen neuen Ordner mit einem passenden Namen, z. B. _GettingStarted_, und klicken Sie dann auf die Schaltfläche **Select Folder** (Ordner auswählen), um den Buildvorgang zu starten:</span><span class="sxs-lookup"><span data-stu-id="bd566-209">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-2.png)

<span data-ttu-id="bd566-211">Warten Sie, bis Unity den Buildvorgang abgeschlossen hat:</span><span class="sxs-lookup"><span data-stu-id="bd566-211">Wait for Unity to finish the build process:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="bd566-213">2. Erstellen und Bereitstellen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="bd566-213">2. Build and deploy the application</span></span>

<span data-ttu-id="bd566-214">Wenn der Buildvorgang abgeschlossen ist, fordert Unity den Windows Datei-Explorer auf, den Speicherort zu öffnen, in dem Sie den Build gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="bd566-214">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="bd566-215">Navigieren Sie zum Ordner, und doppelklicken Sie auf die Projektmappendatei, um sie in Visual Studio zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="bd566-215">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-1.png)

> [!NOTE]
> <span data-ttu-id="bd566-217">Wenn Sie von Visual Studio zur Installation neuer Komponenten aufgefordert werden, nehmen Sie sich einen Moment Zeit, um zu überprüfen, ob alle erforderlichen Komponenten (wie in der Dokumentation [Installieren der Tools](install-the-tools.md) angegeben) installiert sind.</span><span class="sxs-lookup"><span data-stu-id="bd566-217">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the [Install the Tools](install-the-tools.md) documentation.</span></span>

<span data-ttu-id="bd566-218">Konfigurieren Sie Visual Studio für HoloLens 2, indem Sie die **Master**- oder **Release**-Konfiguration, die **ARM**-Architektur und **Gerät** als Ziel auswählen:</span><span class="sxs-lookup"><span data-stu-id="bd566-218">Configure Visual Studio for HoloLens 2 by selecting the **Master** or **Release** configuration, the **ARM** architecture, and **Device** as target:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-2.png)

<span data-ttu-id="bd566-220">Verbinden Sie Ihre HoloLens 2 mit Ihrem Computer.</span><span class="sxs-lookup"><span data-stu-id="bd566-220">Connect your HoloLens 2 to your computer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bd566-221">Bevor Sie den Build für Ihr Gerät erstellen, muss das Gerät in den Entwicklermodus versetzt und mit Ihrem Entwicklungscomputer gekoppelt werden.</span><span class="sxs-lookup"><span data-stu-id="bd566-221">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="bd566-222">Sie können beide Schritte ausführen, indem Sie [diese Anweisungen](using-visual-studio.md) befolgen.</span><span class="sxs-lookup"><span data-stu-id="bd566-222">Both of these steps can be completed by following [these instructions](using-visual-studio.md).</span></span>

<span data-ttu-id="bd566-223">Der letzte Schritt ist die Erstellung und Bereitstellung auf Ihrem Gerät durch Auswählen von **Debuggen** > **Starten ohne Debuggen**:</span><span class="sxs-lookup"><span data-stu-id="bd566-223">The final step is to build and deploy to your device by selecting **Debug** > **Start Without Debugging**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-3.png)

<span data-ttu-id="bd566-225">Bei diesen Anweisungen wird davon ausgegangen, dass Sie auf einem HoloLens 2-Gerät bereitstellen. Sie können die Bereitstellung aber auch auf dem [HoloLens 2-Emulator](using-the-hololens-emulator.md) vornehmen oder ein [App-Paket für das Querladen](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>) erstellen.</span><span class="sxs-lookup"><span data-stu-id="bd566-225">While these instructions assume you will be deploying to a HoloLens 2 device, you can also deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).</span></span>

<span data-ttu-id="bd566-226">Wenn Sie „Starten ohne Debuggen“ auswählen, wird die Anwendung sofort nach einem erfolgreichen Buildvorgang auf Ihrem Gerät gestartet, ohne dass jedoch der Debugger gestartet und Debuginformationen in Visual Studio angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bd566-226">Selecting Start without Debugging causes the application to immediately start on your device upon a successful build, but without the debugger attached and information appearing in Visual Studio.</span></span> <span data-ttu-id="bd566-227">Dies bedeutet auch, dass Sie das USB-Kabel entfernen können, während Ihre Anwendung auf Ihrem HoloLens 2-Gerät ausgeführt wird, ohne dass die Anwendung beendet wird.</span><span class="sxs-lookup"><span data-stu-id="bd566-227">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span>

<span data-ttu-id="bd566-228">Um die Anwendung auf Ihrem Gerät bereitzustellen, ohne dass sie automatisch gestartet wird, können Sie „Build“ > „Projektmappe bereitstellen“ auswählen.</span><span class="sxs-lookup"><span data-stu-id="bd566-228">To deploy to your device without having the application start automatically, you can select Build > Deploy Solution.</span></span>

## <a name="congratulations"></a><span data-ttu-id="bd566-229">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="bd566-229">Congratulations</span></span>

<!-- TODO: Consider cleanup and adding in app screenshots -->
<span data-ttu-id="bd566-230">Sie haben jetzt Ihre erste HoloLens 2-Anwendung bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="bd566-230">You have now deployed your first HoloLens 2 application.</span></span> <span data-ttu-id="bd566-231">Während Sie sich in ihr bewegen, sollten Sie ein Gittermodell für die Raumzuordnung sehen, das alle Oberflächen bedeckt, die von der HoloLens 2 erkannt wurden.</span><span class="sxs-lookup"><span data-stu-id="bd566-231">As you walk around, you should see a spatial mapping mesh covering all the surfaces that have been perceived by the HoloLens 2.</span></span> <span data-ttu-id="bd566-232">Darüber hinaus sollten Sie Indikatoren auf Ihren Händen und Fingern für die Handverfolgung und einen Frameratenzähler zum Überwachen der Anwendungsleistung sehen.</span><span class="sxs-lookup"><span data-stu-id="bd566-232">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on application performance.</span></span> <span data-ttu-id="bd566-233">Dies sind nur einige der grundlegenden Elemente, die standardmäßig im Mixed Reality-Toolkit enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="bd566-233">These are just a few of the foundational pieces, included out of the box, with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="bd566-234">In den folgenden Tutorials fügen Sie Ihrer Szene mehr Inhalte und Interaktivität hinzu, sodass Sie alle Funktionen der HoloLens 2 und des Mixed Reality-Toolkits umfassend erkunden können.</span><span class="sxs-lookup"><span data-stu-id="bd566-234">In the tutorials to come, you will start adding more content and interactivity to your scene so that you can fully explore the capabilities of HoloLens 2 and the Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="bd566-235">Möglicherweise fällt Ihnen in der App die Diagnoseprofilerstellung auf. Sie können sie mithilfe des Sprachbefehls **Toogle Diagnostics** (Diagnose ein-/ausschalten) ein- und ausblenden.</span><span class="sxs-lookup"><span data-stu-id="bd566-235">In the app, you may notice the Diagnostics profiler, you can toggle it's visibility using the speech command **Toogle Diagnostics**.</span></span> <span data-ttu-id="bd566-236">Es wird jedoch im Allgemeinen empfohlen, die Profilerstellung während der Entwicklung jederzeit sichtbar zu lassen, um sehen zu können, wann sich Änderungen an der App möglicherweise negativ auf die Leistung auswirken. Beispielsweise sollte eine HoloLens 2-Anwendung [durchgängig mit 60 BpS](understanding-performance-for-mixed-reality.md) ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="bd566-236">However, it is generally recommended to keep the profiler visible at all times during development to understand when changes to the app may have impacted performance, for example, HoloLens 2 application should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

[<span data-ttu-id="bd566-237">Nächstes Tutorial: 3. Erstellen der Benutzeroberfläche und Konfigurieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="bd566-237">Next Tutorial: 3. Creating user interface and configure Mixed Reality Toolkit</span></span>](mrlearning-base-ch2.md)
