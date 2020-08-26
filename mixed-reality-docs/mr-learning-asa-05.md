---
title: 'Tutorials zu Azure Spatial Anchors: 5 Azure Spatial Anchors für Android und iOS'
description: In diesem Kurs lernen Sie, wie Sie ein Unity-Projekt mit dem Mixed Reality Toolkit und Azure Spatial Anchors unter Android und iOS bereitstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, Android, iOS
ms.localizationpriority: high
ms.openlocfilehash: 8c63204948b3e4aa3d25e5b2ca948798726f0838
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376542"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="6db7a-105">5. Azure Spatial Anchors für Android und iOS</span><span class="sxs-lookup"><span data-stu-id="6db7a-105">5. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="6db7a-106">In diesem Tutorial erfahren Sie, wie Sie Ihr Projekt für Android- und iOS-Geräte mithilfe von AR Foundation, dem ARCore XR-Plug-In und dem ARKit-XR-Plug-In erstellen.</span><span class="sxs-lookup"><span data-stu-id="6db7a-106">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="6db7a-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="6db7a-107">Objectives</span></span>

* <span data-ttu-id="6db7a-108">Lernen, wie Sie ein Projekt für Android-Geräte mithilfe von Unity AR Foundation und dem ARCore XR-Plug-In erstellen</span><span class="sxs-lookup"><span data-stu-id="6db7a-108">Learn how to build your project to your Android device using Unity's AR Foundation and ARCore XR Plugin</span></span>
* <span data-ttu-id="6db7a-109">Lernen, wie Sie ein Projekt für iOS-Geräte mithilfe von Unity AR Foundation und dem ARKit XR-Plug-In erstellen</span><span class="sxs-lookup"><span data-stu-id="6db7a-109">Learn how to build your project to your iOS device using Unity's AR Foundation and ARKit XR Plugin</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="6db7a-110">Installieren von integrierten Unity-Paketen</span><span class="sxs-lookup"><span data-stu-id="6db7a-110">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="6db7a-111">In diesem Abschnitt führen Sie ein Upgrade aus und installieren die folgenden integrierten Pakete:</span><span class="sxs-lookup"><span data-stu-id="6db7a-111">In this section, you will upgrade and install the following inbuilt packages:</span></span>

* <span data-ttu-id="6db7a-112">AR Foundation 3.1.3</span><span class="sxs-lookup"><span data-stu-id="6db7a-112">AR Foundation 3.1.3</span></span>
* <span data-ttu-id="6db7a-113">Legacy Input Helpers 2.1.4</span><span class="sxs-lookup"><span data-stu-id="6db7a-113">Legacy Input Helpers 2.1.4</span></span>
* <span data-ttu-id="6db7a-114">ARCore XR-Plug-In 3.1.3 für Android-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="6db7a-114">ARCore XR Plugin 3.1.3 for Android support</span></span>
* <span data-ttu-id="6db7a-115">ARKit XR-Plug-In 3.1.3 für iOS-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="6db7a-115">ARKit XR plugin 3.1.3 for iOS support</span></span>

> [!CAUTION]
> <span data-ttu-id="6db7a-116">Nicht alle Versionen sind mit MRTK kompatibel, und nur bestimmte Versionen funktionieren zusammen, achten Sie also darauf, genau die oben aufgeführten Versionen zu installieren.</span><span class="sxs-lookup"><span data-stu-id="6db7a-116">Not all version are compatible with MRTK and only certain version works together, so make sure you install the exact versions listed above.</span></span>

<span data-ttu-id="6db7a-117">Wählen Sie im Unity-Menü **Fenster** > **Package Manager** (Paket-Manager) aus, um das Fenster „Package Manager“ zu öffnen, wählen Sie dann **AR Foundation** > **3.1.3** aus, und klicken Sie auf die Schaltfläche **Update to 3.1.3** (Auf 3.1.3 aktualisieren), um das Paket zu aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="6db7a-117">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** > **3.1.3** and click the **Update to 3.1.3** button to update the package:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section1-step1-1.png)

<span data-ttu-id="6db7a-119">Befolgen Sie die gleiche Vorgehensweise, um bei Bedarf die verbleibenden Pakete zu installieren.</span><span class="sxs-lookup"><span data-stu-id="6db7a-119">Follow the same process to import the remaining packages as needed.</span></span>

> [!NOTE]
> <span data-ttu-id="6db7a-120">Wenn Sie dieses Projekt für Android entwickeln, ist es nicht erforderlich, das ARKit XR-Plug-In-Paket zu installieren.</span><span class="sxs-lookup"><span data-stu-id="6db7a-120">If you are developing this project for Android, there is no need to install the ARKit XR Plugin package.</span></span> <span data-ttu-id="6db7a-121">Analog dazu brauchen Sie, wenn Sie dieses Projekt für iOS entwickeln, das ARCore XR-Plug-In nicht zu installieren.</span><span class="sxs-lookup"><span data-stu-id="6db7a-121">Similarly, if you are developing this project for iOS, you do not need to install the ARCore XR Plugin.</span></span>

## <a name="configure-mrtk-for-ar-foundation-camera"></a><span data-ttu-id="6db7a-122">Konfigurieren des MRTK für die AR Foundation Camera</span><span class="sxs-lookup"><span data-stu-id="6db7a-122">Configure MRTK for AR Foundation Camera</span></span>

<span data-ttu-id="6db7a-123">In diesem Abschnitt erfahren Sie, wie Sie das MRTK für die Bereitstellung auf einem mobilen Gerät konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="6db7a-123">In this section, you will learn how to configure MRTK for deploying to a mobile device.</span></span>

<span data-ttu-id="6db7a-124">Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="6db7a-124">In the Hierarchy window, select the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="6db7a-125">Wählen Sie dann im Inspektorfenster die Registerkarte **Camera** (Kamera) aus, klonen Sie das Kameraprofil, und geben Sie ihm einen passenden Namen, beispielsweise **AzureSpatialAnchors_ARCameraProfile**:</span><span class="sxs-lookup"><span data-stu-id="6db7a-125">Then in the Inspector window, select the **Camera** tab, clone the camera profile, and give it a suitable name, for example, **AzureSpatialAnchors_ARCameraProfile**:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="6db7a-127">Wenn Sie eine Auffrischung zum Klonen von MRTK-Profilen benötigen, lesen Sie die Anweisungen in [Konfigurieren der Mixed Reality Toolkit-Profile](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="6db7a-127">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the Mixed Reality Toolkit profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="6db7a-128">Klappen Sie bei im Inspektorfenster noch ausgewählter Registerkarte **Camera** (Kamera) die **Camera Setting Providers** (Anbieter von Kameraeinstellungen) auf, und klicken Sie auf die Schaltfläche **+ Add Camera Setting Provider** (Anbieter von Kameraeinstellungen hinzufügen). Klappen Sie dann den neu hinzugefügten **New data provider 1** (Neuer Datenanbieter 1) auf:</span><span class="sxs-lookup"><span data-stu-id="6db7a-128">With the **Camera** tab still selected in the Inspector window, expand the **Camera Setting Providers** and click the **+ Add Camera Setting Provider** button, then expand the newly added **New data provider 1**:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-2.png)

<span data-ttu-id="6db7a-130">Ändern Sie mithilfe der **Type**-Dropdownliste den Typ in **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span><span class="sxs-lookup"><span data-stu-id="6db7a-130">Using the **Type** dropdown, change the type to **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-3.png)

<span data-ttu-id="6db7a-132">Verwenden Sie bei im Hierarchiefenster noch ausgewähltem **MixedRealityToolkit**-Objekt die Schaltfläche **Add Component** (Komponente hinzufügen) im Inspektorfenster, um die folgenden Komponenten hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="6db7a-132">With the **MixedRealityToolkit** object still selected in the Hierarchy window, use the **Add Component** button in the Inspector window to add the following components:</span></span>

* <span data-ttu-id="6db7a-133">AR Anchor Manager (Script)</span><span class="sxs-lookup"><span data-stu-id="6db7a-133">AR Anchor Manager (Script)</span></span>
* <span data-ttu-id="6db7a-134">DisableDiagnosticsSystem (Script)</span><span class="sxs-lookup"><span data-stu-id="6db7a-134">DisableDiagnosticsSystem (Script)</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="6db7a-136">Wenn Sie die Komponente „AR Reference Point Manager (Script)“ hinzufügen, wird die Komponente „AR Session Origin (Script)“ automatisch hinzugefügt, da sie von der Komponente „AR Reference Point Manager (Script)“ benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="6db7a-136">When you add the AR Reference Point Manager (Script) component, the AR Session Origin (Script) component is automatically added because it is required by the AR Reference Point Manager (Script) component.</span></span>

## <a name="building-your-application-to-your-android-device"></a><span data-ttu-id="6db7a-137">Erstellen Ihrer Anwendung für Ihr Android-Gerät</span><span class="sxs-lookup"><span data-stu-id="6db7a-137">Building your application to your Android device</span></span>

<span data-ttu-id="6db7a-138">In diesem Abschnitt erfahren Sie, wie Sie Ihr Projekt so konfigurieren, dass es für ein Android-Gerät erstellt und auf diesem bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="6db7a-138">In this section, you will learn how to configure your project to build and deploy it to an Android device.</span></span>

<span data-ttu-id="6db7a-139">Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen, und ändern Sie die Plattform dann in Android:</span><span class="sxs-lookup"><span data-stu-id="6db7a-139">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and then switch the platform to Android:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="6db7a-141">Falls Sie eine Auffrischung zum Wechseln der Buildplattform benötigen, lesen Sie die Anweisungen zum [Wechseln der Buildplattform](mr-learning-base-02.md#switching-the-build-platform).</span><span class="sxs-lookup"><span data-stu-id="6db7a-141">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="6db7a-142">Schließen Sie das Fenster „Build Settings“ (Buildeinstellungen).</span><span class="sxs-lookup"><span data-stu-id="6db7a-142">Close the Build Settings window.</span></span>

<span data-ttu-id="6db7a-143">Wählen Sie im Unity-Menü **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) aus, um das **MRTK Project Configurator**-Fenster (MRTK-Projektkonfigurator) zu öffnen, vergewissern Sie sich, dass alle Optionen ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Übernehmen**, um die Einstellungen zu übernehmen:</span><span class="sxs-lookup"><span data-stu-id="6db7a-143">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-2.png)

<span data-ttu-id="6db7a-145">Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen) aus, um das Fenster mit den Playereinstellungen zu öffnen, suchen Sie dann den Abschnitt **Player** >  **Other Settings** (Player > Weitere Einstellungen), wählen Sie **Vulkan** aus, und entfernen Sie die Einstellung, indem Sie auf das **„-“** -Symbol klicken:</span><span class="sxs-lookup"><span data-stu-id="6db7a-145">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, select **Vulkan** and remove it by clicking the **"-"** symbol:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-3.png)

<span data-ttu-id="6db7a-147">Schließen Sie das Fenster „Playereinstellungen“, und öffnen Sie das Fenster „Buildeinstellungen“ erneut.</span><span class="sxs-lookup"><span data-stu-id="6db7a-147">Close the Player Settings window and open the Build Settings window again.</span></span>

<span data-ttu-id="6db7a-148">Klicken Sie im Fenster „Buildeinstellungen“ auf die Schaltfläche **Add Open Scenes** (Geöffnete Szenen hinzufügen), um Ihre aktuelle Szene zur Liste **Scenes In Build** (Szenen im Build) hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="6db7a-148">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span> <span data-ttu-id="6db7a-149">Verwenden Sie dann ein USB-Kabel, um Ihr Android-Gerät mit Ihrem Computer zu verbinden, und wählen Sie es in der Dropdownliste **Run Device** (Ausführendes Gerät) aus:</span><span class="sxs-lookup"><span data-stu-id="6db7a-149">Then, use a USB cable, connect your Android device to your computer and select it from the **Run Device** dropdown:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> <span data-ttu-id="6db7a-151">Wenn Ihr Gerät nicht in der Dropdownliste „Run Device“ angezeigt wird, müssen Sie möglicherweise auf die Aktualisieren-Schaltfläche neben der Dropdownliste klicken.</span><span class="sxs-lookup"><span data-stu-id="6db7a-151">If your device does not appear in the Run Device dropdown, you might need to press the Refresh button next to the dropdown.</span></span>

<span data-ttu-id="6db7a-152">Klicken Sie im Fenster „Buildeinstellungen“ auf die Schaltfläche **Build And Run** (Erstellen und ausführen), um das Fenster „Build Android“ (Für Android erstellen) zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="6db7a-152">In the Build Settings window, click the **Build And Run** button to open the Build Android window.</span></span>

<span data-ttu-id="6db7a-153">Wählen Sie einen geeigneten Speicherplatz zum Speichern Ihres Builds, beispielsweise _D:\MixedRealityLearning\Builds_, geben Sie dann dem APK einen passenden Namen, beispielsweise _MRTKTutorials-AzureSpatialAnchors_, und klicken Sie auf die **Speichern**-Schaltfläche, um den Buildprozess zu starten:</span><span class="sxs-lookup"><span data-stu-id="6db7a-153">Choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, then give the apk a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and click the **Save** button to start the build process:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
<span data-ttu-id="6db7a-155">Wenn im Fenster der Unity-Konsole irgendwelche Fehler im Zusammenhang mit Android SDK-, NDK- oder JDK-Modulen angezeigt werden, müssen Sie den Unity Hub öffnen und die zugehörigen Module für die Android-Buildunterstützung installieren.</span><span class="sxs-lookup"><span data-stu-id="6db7a-155">If you get any error in the Unity Console window related to Android SDK, NDK, or JDK modules, you need to open Unity Hub and install the associated Android Build Support modules.</span></span>

<span data-ttu-id="6db7a-156">Wenn der Buildvorgang abgeschlossen ist, sollten Ihre Apps automatisch auf dem Android-Gerät geladen werden.</span><span class="sxs-lookup"><span data-stu-id="6db7a-156">When the build process is complete, your apps should automatically load on your Android device.</span></span>

## <a name="building-your-application-to-your-ios-device"></a><span data-ttu-id="6db7a-157">Erstellen Ihrer Anwendung für Ihr iOS-Gerät</span><span class="sxs-lookup"><span data-stu-id="6db7a-157">Building your application to your iOS device</span></span>

<span data-ttu-id="6db7a-158">In diesem Abschnitt erfahren Sie, wie Sie Ihr Projekt so konfigurieren, dass es für ein iOS-Gerät erstellt und auf diesem bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="6db7a-158">In this section, you will learn how to configure your project, to build and deploy it to your iOS device.</span></span>

<span data-ttu-id="6db7a-159">Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen, und ändern Sie die Plattform in iOS:</span><span class="sxs-lookup"><span data-stu-id="6db7a-159">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and switch platform to iOS:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="6db7a-161">Falls Sie eine Auffrischung zum Wechseln der Buildplattform benötigen, lesen Sie die Anweisungen zum [Wechseln der Buildplattform](mr-learning-base-02.md#switching-the-build-platform).</span><span class="sxs-lookup"><span data-stu-id="6db7a-161">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="6db7a-162">Schließen Sie das Fenster „Build Settings“ (Buildeinstellungen).</span><span class="sxs-lookup"><span data-stu-id="6db7a-162">Close the Build Settings window.</span></span>

<span data-ttu-id="6db7a-163">Wählen Sie im Unity-Menü **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) aus, um das **MRTK Project Configurator**-Fenster (MRTK-Projektkonfigurator) zu öffnen, vergewissern Sie sich, dass alle Optionen ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Übernehmen**, um die Einstellungen zu übernehmen:</span><span class="sxs-lookup"><span data-stu-id="6db7a-163">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-2.png)

<span data-ttu-id="6db7a-165">Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen) aus, um das Fenster mit den Playereinstellungen zu öffnen, suchen Sie dann den Abschnitt **Player** >  **Other Settings** (Player > Weitere Einstellungen), und deaktivieren Sie das Kontrollkästchen **Strip Engine Code** (Engine-Code entfernen), um es zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="6db7a-165">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, uncheck the **Strip Engine Code** checkbox to disable it:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-3.png)

<span data-ttu-id="6db7a-167">Schließen Sie das Fenster „Player Settings“ (Playereinstellungen), und öffnen Sie das Fenster **Build Settings** (Buildeinstellungen) erneut.</span><span class="sxs-lookup"><span data-stu-id="6db7a-167">Close the Player Settings window and open the **Build Settings** window again.</span></span>

<span data-ttu-id="6db7a-168">Klicken Sie im Fenster „Buildeinstellungen“ auf die Schaltfläche **Add Open Scenes** (Geöffnete Szenen hinzufügen), um Ihre aktuelle Szene der Liste **Scenes In Build** (Szenen im Build) hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="6db7a-168">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-4.png)

<span data-ttu-id="6db7a-170">Klicken Sie im Fenster „Buildeinstellungen“ auf die Schaltfläche **Erstellen**, um das Fenster „Build iOS“ (Für iOS erstellen) zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="6db7a-170">In the Build Settings window, click the **Build** button to open the Build iOS window.</span></span>

<span data-ttu-id="6db7a-171">Wählen Sie einen geeigneten Speicherplatz zum Speichern Ihres Xcode-Projekts, beispielsweise _D:\MixedRealityLearning\Builds_, erstellen Sie einen neuen Ordner, geben Sie ihm einen passenden Namen, beispielsweise _MRTKTutorials-AzureSpatialAnchors_, und klicken Sie dann auf die Schaltfläche **Select Folder** (Ordner auswählen), um den Buildvorgang zu starten:</span><span class="sxs-lookup"><span data-stu-id="6db7a-171">Choose a suitable location to store your Xcode project, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and then click the **Select Folder** button to start the build process:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-5.png)

<span data-ttu-id="6db7a-173">Wenn der Buildvorgang abgeschlossen ist, befolgen Sie die Anweisungen in [Export the Xcode project](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) (Xcode-Projekt exportieren), um Ihr Xcode-Projekt auf Ihrem iOS-Gerät bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="6db7a-173">When the build process is complete, follow the [Export the Xcode project](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) instructions to learn to deploy your Xcode project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="6db7a-174">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="6db7a-174">Congratulations</span></span>

<span data-ttu-id="6db7a-175">In diesem Tutorial haben Sie erfahren, wie Sie Ihr Projekt für Android- und iOS-Geräte mithilfe von AR Foundation, dem ARCore XR-Plug-In und dem ARKit-XR-Plug-In erstellen.</span><span class="sxs-lookup"><span data-stu-id="6db7a-175">In this tutorial, you learned how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>
