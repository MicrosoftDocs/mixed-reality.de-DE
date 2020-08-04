---
title: Tutorials zu Holographic Remoting am PC – 2. Erstellen einer PC-Anwendung für Holographic Remoting
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie Mixed Reality-Remoting von Ihrem PC zu HoloLens 2 ausführen.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 6d11d91a0e08c48c09f676171dcb9bb8a0ff74de
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376372"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a><span data-ttu-id="339ad-105">2. Erstellen einer PC-Anwendung für Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="339ad-105">2. Creating a Holographic Remoting PC application</span></span>

<span data-ttu-id="339ad-106">In diesem Tutorial erfahren Sie, wie Sie eine PC-App für Holographic Remoting erstellen und zu einem beliebigen Zeitpunkt eine Verbindung mit HoloLens 2 herstellen. Auf diese Weise können Sie 3D-Inhalte in Mixed Reality visualisieren.</span><span class="sxs-lookup"><span data-stu-id="339ad-106">In this tutorial, you will learn how to create a PC app for Holographic Remoting and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="339ad-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="339ad-107">Objectives</span></span>

* <span data-ttu-id="339ad-108">Konfigurieren von Unity für Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="339ad-108">Configure Unity for Holographic Remoting</span></span>
* <span data-ttu-id="339ad-109">Erfahren Sie, wie Sie die Anwendung mit Visual Studio erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="339ad-109">Learn how to build and deploy the application with Visual Studio</span></span>
* <span data-ttu-id="339ad-110">Entwickeln von Holographic Remoting-Anwendungen und Herstellen einer Verbindung mit HoloLens</span><span class="sxs-lookup"><span data-stu-id="339ad-110">Developing Holographic Remoting application and connecting to HoloLens</span></span>

## <a name="configuring-your-scene-for-holographic-remoting"></a><span data-ttu-id="339ad-111">Konfigurieren Ihrer Szene für Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="339ad-111">Configuring your scene for Holographic Remoting</span></span>

<span data-ttu-id="339ad-112">In diesem Abschnitt konfigurieren Sie das Projekt so, dass Sie Ihre Mixed Reality-Lösung in Echtzeit über eine WLAN-Verbindung von Ihrem PC aus auf das HoloLens 2-Gerät streamen können.</span><span class="sxs-lookup"><span data-stu-id="339ad-112">In this section, you will configure your project to stream your Mixed Reality experience to your HoloLens 2 device from your PC in real-time over a Wi-Fi connection.</span></span>

<span data-ttu-id="339ad-113">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs**, klicken Sie auf das Prefab **HolographicRemoting**, und ziehen Sie es in ihre Szene.</span><span class="sxs-lookup"><span data-stu-id="339ad-113">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** folder, and click and drag **HolographicRemoting** prefab into your scene.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section1-Step1-1.png)

## <a name="build-your-application-to-pc"></a><span data-ttu-id="339ad-115">Erstellen Ihrer Anwendung auf dem PC</span><span class="sxs-lookup"><span data-stu-id="339ad-115">Build your application to PC</span></span>

<span data-ttu-id="339ad-116">Ihre Holographic Remoting-App kann jetzt auf Ihrem PC erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="339ad-116">Your Holographic Remoting app is now ready to build on your PC.</span></span> <span data-ttu-id="339ad-117">Führen Sie die folgenden Schritte aus, und nehmen Sie diese Änderungen vor, um die Anwendung auf Ihrem PC zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="339ad-117">Follow the below steps and make these changes to build this application on to your PC.</span></span>

### <a name="1-set-the-player-settings"></a><span data-ttu-id="339ad-118">1. Festlegen der Playereinstellungen</span><span class="sxs-lookup"><span data-stu-id="339ad-118">1. Set the player settings</span></span>

<span data-ttu-id="339ad-119">Wählen Sie im Unity-Menü „Edit > Project Settings“ (Bearbeiten > Projekteinstellungen) aus, um das Fenster „Player Settings“ (Playereinstellungen) zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="339ad-119">In the Unity menu, select Edit > Project Settings to open the Player Settings window.</span></span>

<span data-ttu-id="339ad-120">Aktivieren Sie im Abschnitt **XR Settings** (XR-Einstellungen) das Kontrollkästchen **WSA Holographic Remoting Supported** (WSA Holographic Remoting unterstützt), und aktivieren Sie Holographic Remoting.</span><span class="sxs-lookup"><span data-stu-id="339ad-120">In the **XR Settings** section, select the **WSA Holographic Remoting Supported** checkbox and enable the Holographic Remoting.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a><span data-ttu-id="339ad-122">2. Erstellen des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="339ad-122">2. Build the Unity Project</span></span>

<span data-ttu-id="339ad-123">Wählen Sie im Unity-Menü „File > Build Settings“ (Datei > Buildeinstellungen) aus, um das Fenster „Build Settings“ (Buildeinstellungen) zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="339ad-123">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="339ad-124">Klicken Sie im Fenster „Build Settings“ (Buildeinstellungen) auf die Schaltfläche ***Add Open Scenes*** (Geöffnete Szenen hinzufügen), um den Szenen die aktuelle Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="339ad-124">In the Build Settings window, click the ***Add Open Scenes*** button to add your current scene to the Scenes.</span></span> <span data-ttu-id="339ad-125">Klicken Sie in der Liste „Build“ auf die ***Schaltfläche „Build“***, um das Fenster „Build Universal Windows Platform“ (Universelle Windows-Plattform erstellen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="339ad-125">In the Build list, then click the ***Build button*** to open the Build Universal Windows Platform window:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

<span data-ttu-id="339ad-127">Wählen Sie im Fenster „Build Universal Windows Platform“ einen passenden Speicherort zum Speichern Ihres Builds aus, z. B. „Documents\MixedRealityLearning“.</span><span class="sxs-lookup"><span data-stu-id="339ad-127">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="339ad-128">Erstellen Sie einen neuen Ordner, und geben Sie ihm einen geeigneten Namen, z. B. „PCHolographicRemoting“.</span><span class="sxs-lookup"><span data-stu-id="339ad-128">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="339ad-129">Klicken Sie dann auf die Schaltfläche ***Select Folder*** (Ordner auswählen), um den Buildprozess zu starten:</span><span class="sxs-lookup"><span data-stu-id="339ad-129">Then click the ***Select Folder*** button to start the build process:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

<span data-ttu-id="339ad-131">Warten Sie, bis Unity den Buildvorgang abgeschlossen hat.</span><span class="sxs-lookup"><span data-stu-id="339ad-131">Wait for Unity to finish the build process.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a><span data-ttu-id="339ad-133">3. Erstellen und Bereitstellen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="339ad-133">3. Build and deploy the application</span></span>

<span data-ttu-id="339ad-134">Wenn der Buildvorgang abgeschlossen ist, fordert Unity den Windows Datei-Explorer auf, den Speicherort zu öffnen, in dem Sie den Build gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="339ad-134">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="339ad-135">Navigieren Sie im Ordner, und doppelklicken Sie auf die SLN-Datei, um sie in Visual Studio zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="339ad-135">Navigate inside the folder, and double-click the .sln file to open it in Visual Studio:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> <span data-ttu-id="339ad-137">Wenn Sie von Visual Studio zur Installation neuer Komponenten aufgefordert werden, nehmen Sie sich einen Moment Zeit, um zu überprüfen, ob alle erforderlichen Komponenten (wie in der Dokumentation „Installieren der Tools“ angegeben) installiert sind.</span><span class="sxs-lookup"><span data-stu-id="339ad-137">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the Install the Tools documentation.</span></span>

<span data-ttu-id="339ad-138">Konfigurieren Sie Visual Studio für den PC, indem Sie die Releasekonfiguration, die x64-Architektur und einen lokalen Computer als Ziel auswählen:</span><span class="sxs-lookup"><span data-stu-id="339ad-138">Configure Visual Studio for PC by selecting the Release configuration, the x64 architecture, and Local Machine as target:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

<span data-ttu-id="339ad-140">Klicken Sie auf die Schaltfläche ***Lokaler Computer***.</span><span class="sxs-lookup"><span data-stu-id="339ad-140">Click the button that says ***Local Machine***.</span></span> <span data-ttu-id="339ad-141">Die Anwendung wird auf Ihrem PC erstellt und bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="339ad-141">It starts to build and deploy the application on to your PC.</span></span> <span data-ttu-id="339ad-142">Die Anwendung wird standardmäßig auf Ihrem PC installiert.</span><span class="sxs-lookup"><span data-stu-id="339ad-142">The application will be installed in your PC by default.</span></span>

## <a name="testing-holographic-remoting-remote-application"></a><span data-ttu-id="339ad-143">Testen einer Holographic Remoting-Remoteanwendung</span><span class="sxs-lookup"><span data-stu-id="339ad-143">Testing Holographic Remoting remote application</span></span>

<span data-ttu-id="339ad-144">Zum Herstellen einer Verbindung Ihrer PC-Anwendung mit HoloLens 2 führen Sie den folgenden Prozess aus:</span><span class="sxs-lookup"><span data-stu-id="339ad-144">To connect your PC application to your HoloLens 2, follow the below process:</span></span>

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a><span data-ttu-id="339ad-145">1. Installieren der Remoting Player-Anwendung auf HoloLens 2-Geräten</span><span class="sxs-lookup"><span data-stu-id="339ad-145">1. Install the Remoting Player application on HoloLens 2 device</span></span>

* <span data-ttu-id="339ad-146">Besuchen Sie auf dem HoloLens 2-Gerät die Store-App, und suchen Sie nach „**Remoting Player**“.</span><span class="sxs-lookup"><span data-stu-id="339ad-146">On your HoloLens 2, visit the Store app and search for "**Remoting Player**."</span></span>
* <span data-ttu-id="339ad-147">Wählen Sie die **Remoting Player**-App aus.</span><span class="sxs-lookup"><span data-stu-id="339ad-147">Select the **Remoting Player** app.</span></span>
* <span data-ttu-id="339ad-148">Tippen Sie auf **Installieren**, um die App herunterzuladen und zu installieren.</span><span class="sxs-lookup"><span data-stu-id="339ad-148">Tap **Install** to download and install the app.</span></span>

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a><span data-ttu-id="339ad-149">2. Verbinden der PC-App für Holographic Remoting mit dem Remoting Player</span><span class="sxs-lookup"><span data-stu-id="339ad-149">2. Connect the Holographic remoting PC app to the Remoting Player</span></span>

* <span data-ttu-id="339ad-150">Starten Sie den **Remoting Player** auf Ihrem HoloLens-Gerät.</span><span class="sxs-lookup"><span data-stu-id="339ad-150">Start the **Remoting Player** on your HoloLens.</span></span>
* <span data-ttu-id="339ad-151">Notieren Sie sich die HoloLens-**IP-Adresse**.</span><span class="sxs-lookup"><span data-stu-id="339ad-151">Take note of the HoloLens **IP address**.</span></span> <span data-ttu-id="339ad-152">Sie wird vom **Remoting Player** als Hologramm angezeigt, sobald er gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="339ad-152">It will be displayed as a hologram by the **Remoting Player** as soon as it launches.</span></span>
* <span data-ttu-id="339ad-153">Öffnen Sie die PC-Anwendung für Holographic Remoting auf Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="339ad-153">Open the Holographic Remoting PC application on your PC.</span></span>
* <span data-ttu-id="339ad-154">Nachdem die Anwendung gestartet wurde, geben Sie die **IP-Adresse** ein, und klicken Sie auf die Schaltfläche **Connect** (Verbinden), um eine Verbindung herzustellen.</span><span class="sxs-lookup"><span data-stu-id="339ad-154">Once the application is launched, enter the **IP address** and click on the **Connect**  button to connect.</span></span>

## <a name="congratulations"></a><span data-ttu-id="339ad-155">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="339ad-155">Congratulations</span></span>

<span data-ttu-id="339ad-156">In diesem Tutorial haben Sie erfahren, wie Sie eine Remote-App für Holographic Remoting erstellen und zu einem beliebigen Zeitpunkt eine Verbindung mit HoloLens 2 herstellen. Auf diese Weise können Sie 3D-Inhalte in Mixed Reality visualisieren.</span><span class="sxs-lookup"><span data-stu-id="339ad-156">In this tutorial, you learned how to create a Holographic Remoting remote app and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span> <span data-ttu-id="339ad-157">Sobald das HoloLens-Gerät eine Verbindung mit der PC-Anwendung für Holographic Remoting hergestellt hat, sollte die Mixed Reality-Lösung auf das HoloLens 2-Gerät gestreamt werden.</span><span class="sxs-lookup"><span data-stu-id="339ad-157">Once the HoloLens connected to the Holographic Remoting PC application, you should see the mixed reality experience streaming into your HoloLens 2 device.</span></span>
