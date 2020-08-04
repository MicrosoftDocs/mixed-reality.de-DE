---
title: Tutorials zu den ersten Schritten – 2 Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung
description: In diesem Kurs erfahren Sie, wie Sie das Mixed Reality Toolkit (MRTK) verwenden, um eine Mixed Reality-Anwendung zu erstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 5cac7d6f776619cbc2a0e0891b7915b656708726
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376652"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="4f94a-105">2. Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung</span><span class="sxs-lookup"><span data-stu-id="4f94a-105">2. Initializing your project and deploying your first application</span></span>

## <a name="overview"></a><span data-ttu-id="4f94a-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="4f94a-106">Overview</span></span>

<span data-ttu-id="4f94a-107">In diesem Tutorial erfahren Sie, wie Sie ein neues Unity-Projekt erstellen, es für die Entwicklung mit dem <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> konfigurieren und das MRTK importieren.</span><span class="sxs-lookup"><span data-stu-id="4f94a-107">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="4f94a-108">Außerdem werden Sie durch Konfiguration, Erstellung und Bereitstellung der einfachen Unity-Beispielszene aus Visual Studio auf Ihrer HoloLens 2 oder im Emulator geführt.</span><span class="sxs-lookup"><span data-stu-id="4f94a-108">You'll also walk through configuring, building, and deploying the basic Unity sample scene from Visual Studio to your HoloLens 2 or emulator.</span></span>

## <a name="objectives"></a><span data-ttu-id="4f94a-109">Ziele</span><span class="sxs-lookup"><span data-stu-id="4f94a-109">Objectives</span></span>

* <span data-ttu-id="4f94a-110">Erfahren, wie Unity für die HoloLens-Entwicklung konfiguriert wird</span><span class="sxs-lookup"><span data-stu-id="4f94a-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="4f94a-111">Erfahren, wie Ihre App erstellt und in HoloLens bereitgestellt wird</span><span class="sxs-lookup"><span data-stu-id="4f94a-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="4f94a-112">Kennenlernen des Gittermodells für die Raumzuordnung, der Hand-Meshes und des Frameratenzählers</span><span class="sxs-lookup"><span data-stu-id="4f94a-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="4f94a-113">Erstellen des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="4f94a-113">Creating the Unity project</span></span>

<span data-ttu-id="4f94a-114">Starten Sie **Unity Hub**, wählen Sie die Registerkarte **Projects** (Projekte) aus, und klicken Sie auf den **Abwärtspfeil** neben der Schaltfläche **New** (Neu):</span><span class="sxs-lookup"><span data-stu-id="4f94a-114">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="4f94a-116">Wählen Sie in der Dropdownliste die Unity-**Version** aus, die oben in den [Voraussetzungen](mr-learning-base-01.md#prerequisites) angegeben ist:</span><span class="sxs-lookup"><span data-stu-id="4f94a-116">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="4f94a-118">Wenn diese bestimmte Unity-Version nicht auf dem Unity Hub verfügbar ist, können Sie die Installation aus dem <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Downloadarchiv</a> von Unity einleiten.</span><span class="sxs-lookup"><span data-stu-id="4f94a-118">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="4f94a-119">Erstellen Sie im Fenster ein neues Projekt:</span><span class="sxs-lookup"><span data-stu-id="4f94a-119">In the Create a new project window:</span></span>

* <span data-ttu-id="4f94a-120">Vergewissern Sie sich, dass **Templates** (Vorlagen) auf **3D** festgelegt ist</span><span class="sxs-lookup"><span data-stu-id="4f94a-120">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="4f94a-121">Geben Sie einen passenden **Project Name** (Projektnamen) ein, z. B. _MRTK-Tutorials_</span><span class="sxs-lookup"><span data-stu-id="4f94a-121">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="4f94a-122">Wählen Sie eine geeignete **Location** (Speicherort) zum Speichern Ihres Projekts, z. B. _D:\MixedRealityLearning_</span><span class="sxs-lookup"><span data-stu-id="4f94a-122">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="4f94a-123">Klicken Sie auf die Schaltfläche **Create** (Erstellen), um das neue Unity-Projekt zu erstellen</span><span class="sxs-lookup"><span data-stu-id="4f94a-123">Click the **Create** button to create and launch your new Unity project</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="4f94a-125">Wenn Sie unter Windows arbeiten, müssen Sie den MAX_PATH-Grenzwert von 255 Zeichen beachten.</span><span class="sxs-lookup"><span data-stu-id="4f94a-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="4f94a-126">Daher sollten Sie das Unity-Projekt in der Nähe des Stammverzeichnisses des Laufwerks speichern.</span><span class="sxs-lookup"><span data-stu-id="4f94a-126">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="4f94a-127">Warten Sie, bis Unity das Projekt erstellt hat:</span><span class="sxs-lookup"><span data-stu-id="4f94a-127">Wait for Unity to create the project:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="4f94a-129">Wechseln der Buildplattform</span><span class="sxs-lookup"><span data-stu-id="4f94a-129">Switching the build platform</span></span>

<span data-ttu-id="4f94a-130">Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="4f94a-130">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="4f94a-132">Wählen Sie im Build Settings-Fenster **Universal Windows Platform** (Universelle Windows-Plattform) aus, und klicken Sie auf die Schaltfläche **Switch Platform** (Plattform wechseln):</span><span class="sxs-lookup"><span data-stu-id="4f94a-132">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="4f94a-134">Warten Sie, bis Unity den Wechsel der Plattform abgeschlossen hat:</span><span class="sxs-lookup"><span data-stu-id="4f94a-134">Wait for Unity to finish switching the platform:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="4f94a-136">Wenn Unity den Plattformwechsel abgeschlossen hat, klicken Sie auf das rote **x**-Symbol, um das Build Settings-Fenster zu schließen:</span><span class="sxs-lookup"><span data-stu-id="4f94a-136">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="4f94a-138">Importieren der TextMeshPro Essential-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4f94a-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="4f94a-139">Wählen Sie im Unity-Menü **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Fenster > TextMeshPro > TMP Essential Resources importieren) aus, um das Importfenster für Unity-Pakete zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="4f94a-139">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="4f94a-141">Klicken Sie im Import Unity Package-Fenster (Unity-Paket importieren) auf die Schaltfläche **All** (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Import** (Importieren), um die Assets zu importieren:</span><span class="sxs-lookup"><span data-stu-id="4f94a-141">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="4f94a-143">Die TextMeshPro Essential-Ressourcen sind für die Benutzeroberflächenelemente des MRTK erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4f94a-143">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="4f94a-144">Sie können diesen Schritt überspringen, wenn Sie nicht beabsichtigen, die Benutzeroberflächenelemente des MRTK in Ihrem Projekt zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="4f94a-144">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="4f94a-145">Importieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="4f94a-145">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="4f94a-146">Laden Sie das benutzerdefinierte Unity-Paket herunter:</span><span class="sxs-lookup"><span data-stu-id="4f94a-146">Download the Unity custom package:</span></span>

* [<span data-ttu-id="4f94a-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="4f94a-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

<span data-ttu-id="4f94a-148">Wählen Sie im Unity-Menü **Assets** > **Import Package** > **Custom Package...** (Assets > Paket importieren > Benutzerdefiniertes Paket...) aus, um das Fenster zum Importieren von Paketen zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="4f94a-148">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-1.png)

<span data-ttu-id="4f94a-150">Wählen Sie im Fenster „Import package...“ (Paket importieren...) das heruntergeladene **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage**-Paket aus, und klicken Sie auf die Schaltfläche **Open** (Öffnen):</span><span class="sxs-lookup"><span data-stu-id="4f94a-150">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage** you downloaded and click the **Open** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="4f94a-152">Klicken Sie im Import Unity Package-Fenster (Unity-Paket importieren) auf die Schaltfläche **All** (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Import** (Importieren), um die Assets zu importieren:</span><span class="sxs-lookup"><span data-stu-id="4f94a-152">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="4f94a-154">Konfigurieren des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="4f94a-154">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="4f94a-155">1. Übernehmen der Einstellungen des MRTK-Projektkonfigurators</span><span class="sxs-lookup"><span data-stu-id="4f94a-155">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="4f94a-156">Nachdem Unity das Importieren des Pakets aus dem vorherigen Abschnitt abgeschlossen hat, sollte das Fenster des MRTK-Projektkonfigurators angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="4f94a-156">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="4f94a-157">Ist dies nicht der Fall, öffnen Sie das Konfiguratorfenster, indem Sie zum Unity-Menu navigieren und **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Realty-Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) auswählen:</span><span class="sxs-lookup"><span data-stu-id="4f94a-157">If it doesn't, open the Configurator window by going to the Unity menu and selecting **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="4f94a-159">Klappen Sie im Projektkonfiguratorfenster des MRTK den Abschnitt **Modify Configurations** (Konfigurationen ändern) auf, vergewissern Sie sich, dass alle Optionen aktiviert sind, und klicken Sie auf die Schaltfläche **Apply** (Übernehmen), um die Einstellungen zu übernehmen:</span><span class="sxs-lookup"><span data-stu-id="4f94a-159">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-2.png)

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="4f94a-161">2. Konfigurieren zusätzlicher Projekteinstellungen</span><span class="sxs-lookup"><span data-stu-id="4f94a-161">2. Configure additional project settings</span></span>

<span data-ttu-id="4f94a-162">Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen...) aus, um das Fenster „Project Settings“ (Projekteinstellungen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="4f94a-162">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="4f94a-164">Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **Player** > **XR Settings** (Player > XR-Einstellungen) aus, klicken Sie auf das **+** -Symbol, und wählen Sie „Windows Mixed Reality“ aus, um das Windows Mixed Reality SDK hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="4f94a-164">In the Project Settings window, select **Player** > **XR Settings**, click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="4f94a-166">Nachdem Unity das Importieren des Windows Mixed Reality SDK abgeschlossen hat, sollte wieder das Fenster des MRTK-Projektkonfigurators angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="4f94a-166">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="4f94a-167">Wenn dies nicht der Fall ist, verwenden Sie das Unity-Menü, um es zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="4f94a-167">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="4f94a-168">Verwenden Sie im Fenster des MRTK-Projektkonfigurators die Dropdownliste **Audio spatializer** (Räumliche Audiowiedergabe), um den **MS HRTF Spatializer** auszuwählen, und klicken Sie dann auf die Schaltfläche **Übernehmen**, um die Einstellung zu übernehmen:</span><span class="sxs-lookup"><span data-stu-id="4f94a-168">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-3.png)

<span data-ttu-id="4f94a-170">Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **Player** > **XR Settings** (Player > XR-Einstellungen) aus, und verwenden Sie dann die Dropdownliste **Depth Format** (Tiefenformat), um **16-Bit Tiefe** auszuwählen:</span><span class="sxs-lookup"><span data-stu-id="4f94a-170">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="4f94a-172">Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **Player** > **Publishing Settings** (Player > Veröffentlichungseinstellungen) aus, geben Sie dann im Feld **Package name** (Paketname) einen passenden Namen ein, beispielsweise _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="4f94a-172">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-5.png)

> [!NOTE]
> <span data-ttu-id="4f94a-174">Der Paketname stellt den eindeutigen Bezeichner für die App dar.</span><span class="sxs-lookup"><span data-stu-id="4f94a-174">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="4f94a-175">Sie sollten diesen Bezeichner ändern, bevor Sie die App bereitstellen, um das Überschreiben zuvor installierter Apps zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="4f94a-175">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="4f94a-176">Der „Product Name“ (Produktname) ist der Name, der im HoloLens-Startmenü angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="4f94a-176">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="4f94a-177">Um das Auffinden der App während der Entwicklung zu erleichtern, fügen Sie vor dem Namen einen Unterstrich hinzu, sodass sie in Listen oben einsortiert wird.</span><span class="sxs-lookup"><span data-stu-id="4f94a-177">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="4f94a-178">Erstellen und Konfigurieren der Szene</span><span class="sxs-lookup"><span data-stu-id="4f94a-178">Creating and configuring the scene</span></span>

<span data-ttu-id="4f94a-179">Wählen Sie im Unity-Menü **File** > **New Scene** (Datei > Neue Szene) aus, um eine neue Szene zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="4f94a-179">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="4f94a-181">Wählen Sie im Unity-Menü **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Mixed Reality-Toolkit > Zu Szene hinzufügen und konfigurieren) aus, um Ihrer aktuellen Szene das MRTK hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="4f94a-181">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="4f94a-183">Überprüfen Sie bei im Hierarchiefenster ausgewähltem **MixedRealityToolkit**-Objekt im Inspektorfenster, ob das Konfigurationsprofil des **Mixed Reality-Toolkits** auf **DefaultMixedRealityToolkitConfigurationProfile** festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="4f94a-183">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="4f94a-185">Normalerweise verwenden Sie zum Entwickeln für HoloLens das DefaultHoloLens2ConfigurationProfile-Profil.</span><span class="sxs-lookup"><span data-stu-id="4f94a-185">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens.</span></span> <span data-ttu-id="4f94a-186">Im Rahmen dieses Tutorials verwenden Sie jedoch das DefaultMixedRealityToolkitConfigurationProfile-Profil und wechseln dann im nächsten Tutorial [Konfigurieren der MRTK-Profile](mr-learning-base-03.md) zum DefaultHoloLens2ConfigurationProfile-Profil.</span><span class="sxs-lookup"><span data-stu-id="4f94a-186">However, for this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile, then in the next tutorial, [Configuring the MRTK profiles](mr-learning-base-03.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

<span data-ttu-id="4f94a-187">Wählen Sie im Unity-Menü **File** > **Save As...** (Datei > Speichern unter...) aus, um das Save Scene-Fenster (Szene speichern) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="4f94a-187">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="4f94a-189">Navigieren Sie im Save Scene-Fenster zum Ordner **Scenes** (Szenen), geben Sie Ihrer Szene einen passenden Namen, beispielsweise _ErsteSchritte_, und klicken Sie auf die Schaltfläche **Save** (Speichern), um die Szene zu speichern:</span><span class="sxs-lookup"><span data-stu-id="4f94a-189">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="4f94a-191">Erstellen Ihrer Anwendung auf der HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4f94a-191">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="4f94a-192">1. Erstellen des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="4f94a-192">1. Build the Unity project</span></span>

<span data-ttu-id="4f94a-193">Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="4f94a-193">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="4f94a-194">Klicken Sie im Build Settings-Fenster (Buildeinstellungen) auf die Schaltfläche **Add Open Scenes** (Geöffnete Szenen hinzufügen), um der Liste **Scenes In Build** (Szenen im Build) Ihre aktuelle Szene hinzuzufügen, und klicken Sie dann auf die Schaltfläche **Build** (Erstellen), um das Build Universal Windows Platform-Fenster (Erstellen für Universelle Windows-Plattform) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="4f94a-194">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="4f94a-196">Wählen Sie im Build Universal Windows Platform-Fenster einen passenden Speicherort aus, um Ihren Build zu speichern, beispielsweise _D:\MixedRealityLearning\Builds_, erstellen Sie einen neuen Ordner mit einem passenden Namen, z. B. _GettingStarted_, und klicken Sie dann auf die Schaltfläche **Select Folder** (Ordner auswählen), um den Buildvorgang zu starten:</span><span class="sxs-lookup"><span data-stu-id="4f94a-196">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="4f94a-198">Warten Sie, bis Unity den Buildvorgang abgeschlossen hat:</span><span class="sxs-lookup"><span data-stu-id="4f94a-198">Wait for Unity to finish the build process:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="4f94a-200">2. Erstellen und Bereitstellen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="4f94a-200">2. Build and deploy the application</span></span>

<span data-ttu-id="4f94a-201">Wenn der Buildvorgang abgeschlossen ist, fordert Unity den Windows Datei-Explorer auf, den Speicherort zu öffnen, in dem Sie den Build gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="4f94a-201">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="4f94a-202">Navigieren Sie zum Ordner, und doppelklicken Sie auf die Projektmappendatei, um sie in Visual Studio zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="4f94a-202">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> <span data-ttu-id="4f94a-204">Wenn Sie von Visual Studio zur Installation neuer Komponenten aufgefordert werden, nehmen Sie sich einen Moment Zeit, um zu überprüfen, ob alle erforderlichen Komponenten (wie in der Dokumentation **[Installieren der Tools](install-the-tools.md)** angegeben) installiert sind.</span><span class="sxs-lookup"><span data-stu-id="4f94a-204">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="4f94a-205">Konfigurieren Sie Visual Studio für HoloLens 2, indem Sie die **Master**- oder **Release**-Konfiguration, die **ARM64**-Architektur und **Gerät** als Ziel auswählen:</span><span class="sxs-lookup"><span data-stu-id="4f94a-205">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> <span data-ttu-id="4f94a-207">Wenn Sie auf HoloLens (1. Generation) bereitstellen, wählen Sie die **x86**-Architektur aus.</span><span class="sxs-lookup"><span data-stu-id="4f94a-207">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="4f94a-208">Für HoloLens erstellen Sie normalerweise für die ARM-Architektur.</span><span class="sxs-lookup"><span data-stu-id="4f94a-208">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="4f94a-209">Jedoch besteht ein <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>bekanntes Problem</strong></a> in Unity 2019.3, das zu Fehlern führt, wenn ARM in Visual Studio als Buildarchitektur ausgewählt wird.</span><span class="sxs-lookup"><span data-stu-id="4f94a-209">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="4f94a-210">Die empfohlene Umgehung besteht darin, Builds für ARM64 zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="4f94a-210">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="4f94a-211">Wenn diese Option nicht in Frage kommt, navigieren Sie zu **Edit > Project Settings > Player > Other Settings** (Bearbeiten > Projekteinstellungen > Player > Weitere Einstellungen), und deaktivieren Sie **Graphics Jobs** (Grafikaufträge).</span><span class="sxs-lookup"><span data-stu-id="4f94a-211">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="4f94a-212">Wenn „Device“ (Gerät) nicht als Zieloption angezeigt wird, müssen Sie möglicherweise das Startprojekt für die Visual Studio-Projektmappe vom Projekt „IL2CPP“ zum Projekt „UWP“ ändern.</span><span class="sxs-lookup"><span data-stu-id="4f94a-212">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="4f94a-213">Klicken Sie dazu im Projektmappen-Explorer mit der rechten Maustaste auf den Namen Ihres Projekts (Universal Windows), und wählen Sie **Set as StartUp Project** (Als Startprojekt festlegen) aus.</span><span class="sxs-lookup"><span data-stu-id="4f94a-213">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="4f94a-214">Verbinden Sie Ihre HoloLens mit Ihrem Computer, wählen Sie dann **Debug** > **Start Without Debugging** (Debuggen > Ohne Debuggen starten) aus, um zu erstellen und auf Ihrem Gerät bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="4f94a-214">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="4f94a-216">Bevor Sie den Build für Ihr Gerät erstellen, muss das Gerät in den Entwicklermodus versetzt und mit Ihrem Entwicklungscomputer gekoppelt werden.</span><span class="sxs-lookup"><span data-stu-id="4f94a-216">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="4f94a-217">Sie können beide Schritte ausführen, indem Sie [diese Anweisungen](using-visual-studio.md) befolgen.</span><span class="sxs-lookup"><span data-stu-id="4f94a-217">Both of these steps can be completed by following [these instructions](using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="4f94a-218">Sie können auch auf dem [HoloLens Emulator](using-the-hololens-emulator.md) bereitstellen oder ein [App-Paket](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) zum Querladen erstellen.</span><span class="sxs-lookup"><span data-stu-id="4f94a-218">You can also deploy to the [HoloLens Emulator](using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="4f94a-219">Bei der Option „Start Without Debugging“ (Ohne Debuggen starten) wird die App auf Ihrem Gerät automatisch ohne angefügten Visual Studio-Debugger gestartet.</span><span class="sxs-lookup"><span data-stu-id="4f94a-219">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="4f94a-220">Wählen Sie **Build > Deploy Solution** (Erstellen > Projektmappe bereitstellen) aus, um die Anwendung auf Ihrem Gerät bereitzustellen, ohne dass sie automatisch gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="4f94a-220">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="4f94a-221">Möglicherweise fällt Ihnen in der App die Diagnoseprofilerstellung auf. Sie können sie mithilfe des Sprachbefehls **Toggle Diagnostics** (Diagnose ein-/ausschalten) ein- und ausblenden.</span><span class="sxs-lookup"><span data-stu-id="4f94a-221">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="4f94a-222">Es empfiehlt sich, während der Entwicklung den Profiler die meiste Zeit anzuzeigen, um zu verstehen, wann Änderungen an der App die Leistung beeinträchtigen können.</span><span class="sxs-lookup"><span data-stu-id="4f94a-222">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="4f94a-223">Beispielsweise sollten HoloLens-Apps [durchgängig bei 60 FPS](understanding-performance-for-mixed-reality.md) ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="4f94a-223">For example, HoloLens apps should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="4f94a-224">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="4f94a-224">Congratulations</span></span>

<span data-ttu-id="4f94a-225">Sie haben jetzt Ihre erste HoloLens-App bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="4f94a-225">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="4f94a-226">Während Sie sich in ihr bewegen, sollten Sie ein Gittermodell für die Raumzuordnung sehen, das die Oberflächen bedeckt, die von der HoloLens erkannt wurden.</span><span class="sxs-lookup"><span data-stu-id="4f94a-226">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="4f94a-227">Darüber hinaus sollten Sie Indikatoren auf Ihren Händen und Fingern für die Handverfolgung und einen Frameratenzähler zum Überwachen der App-Leistung sehen.</span><span class="sxs-lookup"><span data-stu-id="4f94a-227">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="4f94a-228">Diese Features sind nur einige der grundlegenden Bestandteile von MRTK.</span><span class="sxs-lookup"><span data-stu-id="4f94a-228">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="4f94a-229">In den bevorstehenden Tutorials fügen Sie Ihrer Szene Inhalte hinzu, um die Funktionen von HoloLens und des MRTK kennenzulernen.</span><span class="sxs-lookup"><span data-stu-id="4f94a-229">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

[<span data-ttu-id="4f94a-230">Nächstes Tutorial: 3. Konfigurieren der MRTK-Profile</span><span class="sxs-lookup"><span data-stu-id="4f94a-230">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
