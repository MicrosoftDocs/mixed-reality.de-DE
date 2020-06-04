---
title: 'Tutorials zu Azure Spatial Anchors: 4 Azure Spatial Anchors für Android und iOS'
description: In diesem Tutorial erfahren Sie, wie Sie Azure Spatial Anchors in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/18/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, Kurs, HoloLens, Azure, Spatial Anchors
ms.localizationpriority: high
ms.openlocfilehash: a35f73ae5aee493182f0f4990aa345d990c3f513
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/26/2020
ms.locfileid: "83867622"
---
# <a name="4-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="c6774-105">4. Azure Spatial Anchors für Android und iOS</span><span class="sxs-lookup"><span data-stu-id="c6774-105">4. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="c6774-106">In diesem Tutorial erfahren Sie, wie Sie Ihr Projekt für Android- und iOS-Geräte mithilfe von AR Foundation, dem ARCore XR-Plug-In und dem ARKit-XR-Plug-In erstellen.</span><span class="sxs-lookup"><span data-stu-id="c6774-106">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="c6774-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="c6774-107">Objectives</span></span>

* <span data-ttu-id="c6774-108">Lernen, wie Sie ein Projekt für Android-Geräte mithilfe von Unity AR Foundation und dem ARCore XR-Plug-In erstellen.</span><span class="sxs-lookup"><span data-stu-id="c6774-108">Learn how to build your project to Android device using Unity AR Foundation and ARCore XR Plugin.</span></span>
* <span data-ttu-id="c6774-109">Lernen, wie Sie ein Projekt für iOS-Geräte mithilfe von Unity AR Foundation und dem ARKit XR-Plug-In erstellen.</span><span class="sxs-lookup"><span data-stu-id="c6774-109">Learn how to build your project to an iOS device using Unity AR Foundation and ARKit XR Plugin.</span></span>

[!NOTE] <span data-ttu-id="c6774-110">Um dieses Tutorial abzuschließen, sollten Sie unbedingt Azure Spatial Anchors-Tutorials > [Erste Schritte mit Azure Spatial Anchors](mrlearning-asa-ch1.md) durchgearbeitet haben.</span><span class="sxs-lookup"><span data-stu-id="c6774-110">To complete this tutorial, make sure you have completed Azure Spatial Anchors Tutorials -> [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md).</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="c6774-111">Hinzufügen von integrierten Unity-Paketen</span><span class="sxs-lookup"><span data-stu-id="c6774-111">Adding inbuilt Unity packages</span></span>

<span data-ttu-id="c6774-112">In diesem Abschnitt installieren Sie die in Unity integrierten Pakete AR Foundation, ARCore XR-Plug-In und ARKit XR-Plug-In, die für die Unterstützung von Android- und iOS-Geräten erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="c6774-112">In this section, you will install Unity's inbuilt AR Foundation, ARCore XR Plugin, and ARKit XR Plugin packages required to support Android and iOS devices.</span></span>

<span data-ttu-id="c6774-113">Achten Sie darauf, die richtige Version dieser Unity-Pakete zu installieren, wie unten aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="c6774-113">Make sure you install the correct version of these Unity packages as listed below:</span></span>

* <span data-ttu-id="c6774-114">**AR Foundation 2.1.4**</span><span class="sxs-lookup"><span data-stu-id="c6774-114">**AR Foundation 2.1.4**</span></span>
* <span data-ttu-id="c6774-115">**Arcore-XR-Plug-In 2.2.0 Preview 2**</span><span class="sxs-lookup"><span data-stu-id="c6774-115">**ARCore XR plugin 2.2.0 preview 2**</span></span>
* <span data-ttu-id="c6774-116">**ARKit XR-Plug-In 2.1.1**</span><span class="sxs-lookup"><span data-stu-id="c6774-116">**ARKit XR plugin 2.1.1**</span></span>

[!NOTE] <span data-ttu-id="c6774-117">Wenn Sie dieses Projekt für Android entwickeln, ist es nicht erforderlich, das ARKit XR-Plug-In-Paket zu installieren.</span><span class="sxs-lookup"><span data-stu-id="c6774-117">If you are developing this project for Android, there is no need to install the ARKit XR Plugin package.</span></span> <span data-ttu-id="c6774-118">Analog dazu brauchen Sie, wenn Sie dieses Projekt für iOS entwickeln, das ARCore XR-Plug-In nicht zu installieren.</span><span class="sxs-lookup"><span data-stu-id="c6774-118">Similarly, if you are developing this project for iOS, you do not need to install the ARCore XR Plugin.</span></span>

<span data-ttu-id="c6774-119">Wählen Sie im Unity-Menü **Window** > **Package Manager** (Fenster > Paket-Manager) aus:</span><span class="sxs-lookup"><span data-stu-id="c6774-119">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-1.png)

<span data-ttu-id="c6774-121">Es kann einige Sekunden dauern, bis alle Pakete in der Liste angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c6774-121">It might take a few seconds before all packages appear in the list.</span></span> <span data-ttu-id="c6774-122">Sie zeigen Vorschaupakete an, indem Sie auf die Option „Erweitert“ klicken und „**Vorschaupakete anzeigen**“ auswählen.</span><span class="sxs-lookup"><span data-stu-id="c6774-122">Display preview packages by clicking on Advanced option and select "**Show preview packages.**"</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-2.png)

<span data-ttu-id="c6774-124">Wählen Sie im Fenster des Paket-Managers **AR Foundation** aus. Hier werden viele Versionen angezeigt, Sie müssen Version 2.1.4 auswählen und das Paket aktualisieren, indem Sie auf die Schaltfläche **Update to 2.1.4** (Auf 2.1.4 aktualisieren) klicken:</span><span class="sxs-lookup"><span data-stu-id="c6774-124">In the Package Manager window, select **AR Foundation**, here you see many version and need to select version 2.1.4 and update the package by clicking the **Update to 2.1.4** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-3.png)

<span data-ttu-id="c6774-126">Um Android-Geräte zu unterstützen, folgen Sie dem gleichen Vorgang wie beim Importieren von ARCore XR Plugin 2.2.0 Preview 2.</span><span class="sxs-lookup"><span data-stu-id="c6774-126">To support Android devices, follow the same process to import ARCore XR Plugin 2.2.0 preview 2.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-4.png)

<span data-ttu-id="c6774-128">Um iOS-Geräte zu unterstützen, sollten Sie das Unity-Paket **ARKit XR-Plug-In 2.1.1** aus dem Paket-Manager installieren.</span><span class="sxs-lookup"><span data-stu-id="c6774-128">To support iOS devices, you should import the **ARKit XR plugin 2.1.1** Unity package from the Package Manager.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-5.png)

## <a name="customize-mrtk-to-support-ar-foundation-camera"></a><span data-ttu-id="c6774-130">Anpassen von MRTK zur Unterstützung der AR Foundation-Kamera</span><span class="sxs-lookup"><span data-stu-id="c6774-130">Customize MRTK to support AR Foundation camera</span></span>

<span data-ttu-id="c6774-131">Passen Sie die MRTK-Einstellungen für die Unterstützung von AR Foundation an, indem Sie im Hierarchiefenster „MixedRealityToolKit“ auswählen und im Inspektorfenster auf die Schaltfläche **Clone** (Klonen) im Mixed Reality ToolKit klicken.</span><span class="sxs-lookup"><span data-stu-id="c6774-131">Customize MRTK settings to support AR Foundation by selecting MixedRealityToolKit in the Hierarchy window and click the **Clone** button in Mixed Reality ToolKit in the Inspector window.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-1.png)

<span data-ttu-id="c6774-133">Wenn Sie auf die Schaltfläche **Clone** klicken, wird ein neues Fenster „Clone Profile“ (Profil klonen) angezeigt. Klicken Sie erneut auf die Schaltfläche „Clone“, um das DefaultMixedRealityToolkitProfile zu klonen.</span><span class="sxs-lookup"><span data-stu-id="c6774-133">When you click the **Clone** button, a new Clone Profile window will appear, click on the Clone button again to clone the DefaultMixedRealityToolkitProfile.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-2.png)

<span data-ttu-id="c6774-135">Klonen Sie analog hierzu das Kameraprofil im Inspektorfenster, benennen Sie das Profil in “UnityARConfigurationProfile” um, und klicken Sie auf die **Clone**-Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="c6774-135">Similarly, clone the camera profile in the Inspector window and rename the profile to “UnityARConfigurationProfile” and click on the **Clone** button.</span></span> <span data-ttu-id="c6774-136">Suchen Sie im Inspektorfenster den Eintrag „MixedReality“, wählen Sie die Registerkarte „Kamera“ aus, erweitern Sie die Kameraeinstellungs-Anbieter im Inspektorfenster, und klicken Sie auf **+Add Camera Setting Provider** (Anbieter von Kameraeinstellungen hinzufügen) > erweitern Sie **New data provider 1** (Neuer Datenanbieter 1) > wählen Sie den Typ **None** (Keiner) aus > wählen Sie **Microsoft .MixedReality.Toolkit.Experimental.UnityAR** > wählen Sie **UnityARCameraSettings** aus.</span><span class="sxs-lookup"><span data-stu-id="c6774-136">In the Inspector window, locate the MixedReality, select the Camera tab Expand the camera setting providers in the inspector window and click on **+Add Camera Setting Provider** > expand **New data provider 1**> select Type **None** >select **Microsoft .MixedReality.Toolkit.Experimental.UnityAR** > Select **UnityARCameraSettings**.</span></span>


![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-3.png)

<span data-ttu-id="c6774-138">Fügen Sie bei im Inspektorfenster ausgewähltem MixedRealityToolKit-Objekt Unterstützungsskripts an, indem Sie auf die Schaltfläche **Add component** (Komponente hinzufügen) klicken, „AR Reference Point Manager“ (AR-Bezugspunkt-Manager) eingeben und das Skript auswählen.</span><span class="sxs-lookup"><span data-stu-id="c6774-138">With the MixedRealityToolKit object selected in the Hierarchy window, in the Inspector window, attach supporting scripts by clicking on the **Add component** button and type in AR reference Point manager and select the script.</span></span>

<span data-ttu-id="c6774-139">Durch das Hinzufügen des Skripts „AR Reference Point Manager“ wird automatisch der „AR session origin“ (AR-Sitzungsursprung) zusammen mit dem Skript im Inspektorfenster hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="c6774-139">Adding the  "AR Reference Point Manager" script will automatically add "AR session origin" along with it in the Inspector window.</span></span> <span data-ttu-id="c6774-140">Nach dem Hinzufügen der Unterstützungsskripts sollte das Inspektorfenster wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="c6774-140">After adding the supporting scripts, the Inspector window should look like this.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-4.png)

## <a name="build-application-to-android-device"></a><span data-ttu-id="c6774-142">Erstellen der Anwendung für ein Android-Gerät</span><span class="sxs-lookup"><span data-stu-id="c6774-142">Build application to Android device</span></span>

<span data-ttu-id="c6774-143">Um diese Anwendung für Ihr Android-Gerät zu erstellen, klicken Sie oben im Fenster auf **Datei**, und wählen Sie **Buildeinstellungen** aus.</span><span class="sxs-lookup"><span data-stu-id="c6774-143">To build this application to your Android device, click on **File** at the top of the window and select **Build Settings.**</span></span> <span data-ttu-id="c6774-144">Auf dem Bildschirm wird ein neues Fenster angezeigt, wählen Sie **Android** aus, und klicken Sie auf **Plattform wechseln**.</span><span class="sxs-lookup"><span data-stu-id="c6774-144">A new window will appear on the screen, select **Android,** and click on the **Switch Platform**.</span></span> <span data-ttu-id="c6774-145">Das Wechseln der Plattform nimmt einige Minuten in Anspruch.</span><span class="sxs-lookup"><span data-stu-id="c6774-145">It will take a few minutes to switch platform.</span></span> <span data-ttu-id="c6774-146">Klicken Sie nach dem Wechsel zur Android-Plattform auf **Add Open Scenes** (Offene Szenen hinzufügen), und vergewissern Sie sich, dass Ihre aktuelle Szene die einzige ausgewählte Szene in der Liste **Szenen in Build** ist.</span><span class="sxs-lookup"><span data-stu-id="c6774-146">After switching to the Android platform, click on **Add Open Scenes** and make sure your current scene is the only selected scene in the **Scenes In Build** list.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-1.png)

<span data-ttu-id="c6774-148">Schließen Sie das Fenster **Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="c6774-148">Close the **Build Settings** window.</span></span> <span data-ttu-id="c6774-149">Wählen Sie im Unity-Menü **Mixed Reality Toolkit** > **Hilfsprogramme** > **Unity-Projekt konfigurieren** aus, und klicken Sie auf **Übernehmen**, um das Unity-Projekt für die Android-Plattform zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="c6774-149">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click on **Apply** to configure the Unity project for the Android platform.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-2.png)

<span data-ttu-id="c6774-151">Wählen Sie im Unity-Menü **Edit** > **Project Settings** (Bearbeiten > Projekteinstellungen) aus, um das Fenster „Project Settings“ (Projekteinstellungen) zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c6774-151">In the Unity menu, select **Edit** > **Project Settings** to open the Project Settings window.</span></span> <span data-ttu-id="c6774-152">Wählen Sie im Fenster „Projekteinstellungen“ die Registerkarte **Player** aus, klappen Sie den Abschnitt „Weitere Einstellungen“ auf, wählen Sie **Vulkan** aus, und entfernen Sie die Einstellung, indem Sie auf das Minuszeichen (-) klicken.</span><span class="sxs-lookup"><span data-stu-id="c6774-152">In the Project Settings, window selects the **Player** tab, expand the Other Settings section, select **Vulkan,** and remove it by clicking the "-" symbol.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-3.png)

<span data-ttu-id="c6774-154">Schließen Sie das Fenster „Playereinstellungen“, und öffnen Sie das Fenster „Buildeinstellungen“ erneut.</span><span class="sxs-lookup"><span data-stu-id="c6774-154">Close the Player Settings window and open the Build Settings window again.</span></span> <span data-ttu-id="c6774-155">Verbinden Sie dann mithilfe eines USB-Kabels Ihr Android-Gerät mit Ihrem Computer, wählen Sie Ihr Gerät in der Dropdownliste **Build and Run on** (Erstellen und Ausführen auf) aus, und klicken Sie dann auf **Build And Run** (Erstellen und Ausführen).</span><span class="sxs-lookup"><span data-stu-id="c6774-155">Then, using a USB cable, connect your Android device to your computer and select your device in the **Build and Run on** the dropdown, then click **Build And Run**.</span></span> <span data-ttu-id="c6774-156">Sie werden aufgefordert, eine APK-Datei zu speichern, der Sie einen beliebigen Namen geben können.</span><span class="sxs-lookup"><span data-stu-id="c6774-156">You will be asked to save a .apk file, which you can pick any name.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-4.png)

> [!NOTE]
> <span data-ttu-id="c6774-158">Wenn im Fenster der Unity-Konsole irgendwelche Fehler im Zusammenhang mit Android SDK-, NDK- und/oder JDK-Modulen angezeigt werden, müssen Sie den Unity Hub öffnen und die zugehörigen SDK-, NDK- und JDK-Module für das Modul zur Android-Buildunterstützung installieren.</span><span class="sxs-lookup"><span data-stu-id="c6774-158">If you get any error in the Unity Console window related to Android SDK, NDK, and or JDK modules, you need to open Unity Hub and install the associated SDK, NDK, and JDK modules for the Android Build Support module.</span></span>

<span data-ttu-id="c6774-159">Wenn der Buildvorgang abgeschlossen ist, sollten Ihre Anwendungen automatisch auf dem Android-Gerät geladen werden.</span><span class="sxs-lookup"><span data-stu-id="c6774-159">When the build process is complete, your applications should automatically load on your Android device.</span></span>

## <a name="build-application-to-ios-device"></a><span data-ttu-id="c6774-160">Erstellen der Anwendung für ein iOS-Gerät</span><span class="sxs-lookup"><span data-stu-id="c6774-160">Build application to iOS Device</span></span>

<span data-ttu-id="c6774-161">Um diese Anwendung für Ihr iOS-Gerät zu erstellen, klicken Sie oben im Fenster auf **Datei**, und wählen Sie **Buildeinstellungen** aus.</span><span class="sxs-lookup"><span data-stu-id="c6774-161">To build this application to your iOS device, click on **File** at the top of the window and select **Build Settings.**</span></span> <span data-ttu-id="c6774-162">Auf dem Bildschirm wird ein neues Fenster angezeigt, wählen Sie **iOS** aus, und klicken Sie auf **Plattform wechseln**.</span><span class="sxs-lookup"><span data-stu-id="c6774-162">A new window will appear on the screen, then select **iOS** and click on the **Switch Platform**.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-1.png)

<span data-ttu-id="c6774-164">Schließen Sie das Fenster **Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="c6774-164">Close the **Build Settings** window.</span></span> <span data-ttu-id="c6774-165">Wählen Sie im Unity-Menü **Mixed Reality Toolkit** > **Hilfsprogramme** > **Unity-Projekt konfigurieren** aus, und klicken Sie auf **Übernehmen**, um das Unity-Projekt für die iOS-Plattform zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="c6774-165">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click on **Apply** to configure the Unity project for the iOS platform.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-2.png)

<span data-ttu-id="c6774-167">Um das iOS-XCode-Projekt zu erstellen, wechseln Sie zu den Buildeinstellungen, und klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="c6774-167">To build the iOS XCode project, go to Build Settings and, click on **Build**.</span></span>

<span data-ttu-id="c6774-168">Folgen Sie [diesem Leitfaden](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project), um zu erfahren, wie Sie dieses Projekt auf Ihrem iOS-Gerät bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c6774-168">Follow [this guide](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) to learn how to deploy this project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="c6774-169">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="c6774-169">Congratulations</span></span>

<span data-ttu-id="c6774-170">In diesem Tutorial haben Sie gelernt, wie Sie Ihr Projekt für Android- und iOS-Geräte erstellen.</span><span class="sxs-lookup"><span data-stu-id="c6774-170">In this tutorial, you learned how to build your project for Android and iOS devices.</span></span> <span data-ttu-id="c6774-171">Außerdem haben Sie gelernt, wie Sie AR Foundation, das ARCore XR-Plug-In und das ARKit XR-Plug-In verwenden, damit Ihr Projekt auf Android- und iOS-Geräten funktioniert.</span><span class="sxs-lookup"><span data-stu-id="c6774-171">You also learned how to use AR Foundation, ARCore XR Plugin, and ARKit XR Plugin to make your project work for Android and iOS devices.</span></span>