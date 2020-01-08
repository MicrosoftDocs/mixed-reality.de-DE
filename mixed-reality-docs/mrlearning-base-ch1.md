---
title: Tutorials zu den ersten Schritten – 2 Initialisieren des Projekts und der ersten Anwendung
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: d0c166f760884efab9719ecba1ff83285872e2ef
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334417"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="104b1-105">2. Initialisieren des Projekts und der ersten Anwendung</span><span class="sxs-lookup"><span data-stu-id="104b1-105">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="104b1-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="104b1-106">Overview</span></span>

<span data-ttu-id="104b1-107">In dieser ersten Lektion lernen Sie einige der Funktionen kennen, die das <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality-Toolkit (MRTK)</a> bietet, starten Ihre erste Anwendung für das HoloLens 2-Gerät und stellen sie auf dem Gerät bereit.</span><span class="sxs-lookup"><span data-stu-id="104b1-107">In this first lesson, you'll learn about some of the capabilities the <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> has to offer, start your first application for the HoloLens 2, and deploy it to the device.</span></span>

## <a name="objectives"></a><span data-ttu-id="104b1-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="104b1-108">Objectives</span></span>

* <span data-ttu-id="104b1-109">Konfigurieren von Unity für die HoloLens-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="104b1-109">Configure Unity for HoloLens development.</span></span>
* <span data-ttu-id="104b1-110">Importieren von Assets und Einrichten der Szene</span><span class="sxs-lookup"><span data-stu-id="104b1-110">Import assets and set up the scene.</span></span>
* <span data-ttu-id="104b1-111">Visualisierung des Gittermodells für die Raumzuordnung, der Hand-Meshes und des Frameratenzählers</span><span class="sxs-lookup"><span data-stu-id="104b1-111">Visualization of the spatial mapping mesh, hand meshes, and the framerate counter.</span></span>

## <a name="create-new-unity-project"></a><span data-ttu-id="104b1-112">Erstellen eines neuen Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="104b1-112">Create new Unity project</span></span>

1. <span data-ttu-id="104b1-113">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="104b1-113">Start Unity.</span></span>

2. <span data-ttu-id="104b1-114">Wählen Sie **Neu** aus.</span><span class="sxs-lookup"><span data-stu-id="104b1-114">Select **New**.</span></span>

    ![Lektion 1 Abschnitt 1 Schritt 2](images/mrlearning-base-ch1-1-step2.JPG)

3. <span data-ttu-id="104b1-116">Geben Sie einen Projektnamen ein (z. B. "MixedRealityBase").</span><span class="sxs-lookup"><span data-stu-id="104b1-116">Enter a project name (e.g. "MixedRealityBase").</span></span>

    ![Lektion 1 Abschnitt 1 Schritt 3](images/mrlearning-base-ch1-1-step3.JPG)

4. <span data-ttu-id="104b1-118">Geben Sie einen Speicherort zum Speichern Ihres Projekts ein.</span><span class="sxs-lookup"><span data-stu-id="104b1-118">Enter a location to save your project.</span></span>

    ![Lektion 1 Abschnitt 1 Schritt 4](images/mrlearning-base-ch1-1-step4.JPG)

5. <span data-ttu-id="104b1-120">Stellen Sie sicher, dass das Projekt auf **3D** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="104b1-120">Make sure the project is set to **3D**.</span></span>

    ![Lektion 1 Abschnitt 1 Schritt 5](images/mrlearning-base-ch1-1-step5.JPG)

6. <span data-ttu-id="104b1-122">Klicken Sie auf **Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="104b1-122">Click **Create Project**.</span></span>

    ![Lektion 1 Abschnitt 1 Schritt 6](images/mrlearning-base-ch1-1-step6.JPG)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="104b1-124">Konfigurieren des Unity-Projekts für Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="104b1-124">Configure the Unity project for Windows Mixed Reality</span></span>

1. <span data-ttu-id="104b1-125">Öffnen Sie das Fenster *Buildeinstellungen*, indem Sie zu **Datei** > **Buildeinstellungen** wechseln.</span><span class="sxs-lookup"><span data-stu-id="104b1-125">Open the *Build Settings* window by going to **File** > **Build Settings**.</span></span>

    ![Lektion 1 Abschnitt 2 Schritt 1](images/mrlearning-base-ch1-2-step1.JPG)

2. <span data-ttu-id="104b1-127">Wählen Sie die *universelle Windows-Plattform* aus, und klicken Sie auf die Schaltfläche **Plattform wechseln**, um die Plattform zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="104b1-127">Select the *Universal Windows Platform* and click the **Switch Platform** button to switch platforms.</span></span> <span data-ttu-id="104b1-128">Anwendungen, die auf HoloLens 2 ausgeführt werden, müssen mit der Universellen Windows-Plattform (UWP) kompatibel sein.</span><span class="sxs-lookup"><span data-stu-id="104b1-128">Applications running on HoloLens 2 are required to be Universal Windows Platform (UWP) compatible.</span></span>

    ![Lektion 1 Abschnitt 2 Schritt 2](images/mrlearning-base-ch1-2-step2.JPG)

3. <span data-ttu-id="104b1-130">Aktivieren Sie virtuelle Realität, indem Sie im Buildfenster auf die Schaltfläche **Player-Einstellungen** klicken, und aktivieren Sie dann im Inspektorbereich unter „XR-Einstellungen“ das Kontrollkästchen für die *VR-Unterstützung*, wie in der folgenden Abbildung gezeigt.</span><span class="sxs-lookup"><span data-stu-id="104b1-130">Enable virtual reality by clicking the **Player Settings** button in the Build Window, and enable the *Virtual Reality Supported* checkbox under XR Settings from the inspector panel, as shown in the image below.</span></span> <span data-ttu-id="104b1-131">Beachten Sie, dass Sie das Fenster *Buildeinstellungen* möglicherweise verschieben oder minimieren müssen, um den Inspektorbereich sehen zu können.</span><span class="sxs-lookup"><span data-stu-id="104b1-131">Note that you might need to drag the *Build Settings* window out of the way in order to see the inspector panel.</span></span> <span data-ttu-id="104b1-132">Das Kontrollkästchen für die *VR-Unterstützung* betrifft auch Mixed Reality- und Augmented Reality-Headsets, da es sich auf die Aktivierung der stereoskopischen Funktion (Rendering unterschiedlicher Bilder für jedes Auge) bezieht.</span><span class="sxs-lookup"><span data-stu-id="104b1-132">The *Virtual Reality Supported* checkbox also applies to Mixed Reality and Augmented Reality headsets because it refers to the enabling of stereoscopic vision (rendering different images for each eye.)</span></span>

    ![Lektion 1 Abschnitt 2 Schritt 3](images/mrlearning-base-ch1-2-step3.JPG)

4. <span data-ttu-id="104b1-134">Ändern Sie außerdem unter "XR-Einstellungen" den *Stereo Rendering Mode* (Stereo-Renderingmodus) in *Single Pass Instanced* (Einzeldurchgangs-Instanz).</span><span class="sxs-lookup"><span data-stu-id="104b1-134">Also under XR Settings, change the *Stereo Rendering Mode* to *Single Pass Instanced*.</span></span> <span data-ttu-id="104b1-135">Diese [Renderingpipeline-Stil](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) bietet im Allgemeinen die höchste Leistung für HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="104b1-135">This [rendering pipeline style](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) is generally most performant for HoloLens 2.</span></span> <span data-ttu-id="104b1-136">Wenn Sie sich für weitere leistungsfähige Konfigurationen für Ihre Unity-Umgebung interessieren, befolgen Sie [diese Anweisungen](recommended-settings-for-unity.md).</span><span class="sxs-lookup"><span data-stu-id="104b1-136">If interested in other performant configurations for your Unity environment, follow [these instructions](recommended-settings-for-unity.md).</span></span>

    ![Lektion 1 Abschnitt 2 Schritt 4](images/mrlearning-base-ch1-2-step4.jpg)

5. <span data-ttu-id="104b1-138">Vergewissern Sie sich im gleichen Inspektorbereich, dass unter *Veröffentlichungseinstellungen* im Abschnitt „Funktionen“ das Kontrollkästchen *Räumliche Wahrnehmung* aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="104b1-138">From the same inspector panel, ensure that the *Spatial Perception* checkbox in the capabilities section is enabled under *Publishing Settings*.</span></span> <span data-ttu-id="104b1-139">Die Funktion „Räumliche Wahrnehmung“ ermöglicht das Visualisieren des Gittermodells für die Raumzuordnung auf einem Mixed Reality-Gerät wie HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="104b1-139">Spatial Perception allows us to visualize the spatial mapping mesh on a mixed reality device, such as HoloLens 2.</span></span> <span data-ttu-id="104b1-140">Sie finden die Veröffentlichungseinstellungen im Inspektorbereich oberhalb von „XR-Einstellungen“ und unterhalb von „Andere Einstellungen“.</span><span class="sxs-lookup"><span data-stu-id="104b1-140">Publishing Settings are found in the inspector panel, above XR Settings and under Other Settings.</span></span>

    ![Lektion 1 Abschnitt 2 Schritt 5](images/mrlearning-base-ch1-2-step5.JPG)

    >[!NOTE]
    ><span data-ttu-id="104b1-142">Obwohl in diesem Abschnitt nicht verwendet, können Sie einige weitere allgemeine Funktionen aktivieren, wie z. B. das *Mikrofon* für Sprachbefehle und *InternetClient* für das Herstellen einer Verbindung mit Diensten, die eine Netzwerkverbindung erfordern.</span><span class="sxs-lookup"><span data-stu-id="104b1-142">While not used in this section, some other common capabilities you might want to enable include the *Microphone* for voice commands, and *InternetClient* for connecting to services requiring a network connection.</span></span>

## <a name="import-the-mixed-reality-toolkit"></a><span data-ttu-id="104b1-143">Importieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="104b1-143">Import the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="104b1-144">Laden Sie das Unity-Paket [Mixed Reality-Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)[Version 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) herunter, und speichern Sie es in einem Ordner auf Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="104b1-144">Download the [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [foundation package version 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) and save it to a folder on your PC.</span></span>

2. <span data-ttu-id="104b1-145">Importieren Sie das *Mixed Reality Toolkit*-Paket, das Sie im vorherigen Schritt heruntergeladen haben.</span><span class="sxs-lookup"><span data-stu-id="104b1-145">Import the *Mixed Reality Toolkit* package that you downloaded in the previous step.</span></span> <span data-ttu-id="104b1-146">Klicken Sie zunächst auf **Assets** > **Import** > **Custom Package** (Ressourcen > Importieren > Benutzerdefiniertes Paket), wählen Sie *Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage* aus, und öffnen Sie es, um den Importvorgang zu starten.</span><span class="sxs-lookup"><span data-stu-id="104b1-146">Start by clicking on **Assets** > **Import** > **Custom Package**, select *Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage* and open it to begin the importing process.</span></span> <span data-ttu-id="104b1-147">Warten Sie einige Minuten bis zum Abschluss des Importvorgangs.</span><span class="sxs-lookup"><span data-stu-id="104b1-147">Allow a few minutes for the importing process to complete.</span></span>

    ![Lektion 1 Abschnitt 3 Schritt 2a](images/mrlearning-base-ch1-3-step2a.JPG)

    ![Lektion 1 Abschnitt 3 Schritt 2b](images/mrlearning-base-ch1-3-step2b.JPG)

3. <span data-ttu-id="104b1-150">Klicken Sie im nächsten Popupfenster auf **Import** (Importieren), um mit dem Importieren des Mixed Reality-Toolkits zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="104b1-150">In the next pop-up window, click **Import** to begin importing the selected package into the Unity project.</span></span> <span data-ttu-id="104b1-151">Stellen Sie sicher, dass alle Elemente aktiviert sind, wie in der Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="104b1-151">Ensure all items are checked as shown in the image.</span></span>

    ![Lektion 1 Abschnitt 3 Schritt 3](images/mrlearning-base-ch1-3-step3.JPG)

    > [!NOTE]
    > <span data-ttu-id="104b1-153">Wenn ein Popupdialogfeld angezeigt wird, in dem Sie gefragt werden, ob die Standardeinstellungen des Mixed Reality-Toolkits übernommen werden sollen, klicken Sie auf **Übernehmen**.</span><span class="sxs-lookup"><span data-stu-id="104b1-153">If you see a pop-up dialog box asking to apply the Mixed Reality Toolkit default settings, click **Apply**.</span></span> <span data-ttu-id="104b1-154">Das MRTK analysiert beim Import für das automatische Setup Ihr Projekt und prüft es auf fehlende empfohlene Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="104b1-154">MRTK analyzes your project for any missing recommended settings when imported for automated setup.</span></span> <span data-ttu-id="104b1-155">Abhängig von Ihren Einstellungen sieht das Popup möglicherweise anders aus als in der Abbildung unten.</span><span class="sxs-lookup"><span data-stu-id="104b1-155">Depending on your settings, the pop-up might look different than the image below.</span></span>

    ![Lektion 1 Abschnitt 3 Schritt 4 HINWEIS 1](images/mrlearning-base-ch1-3-step4-note1.JPG)

## <a name="configure-the-mixed-reality-toolkit"></a><span data-ttu-id="104b1-157">Konfigurieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="104b1-157">Configure the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="104b1-158">Fügen Sie Ihrer aktuellen Szene das *Mixed Reality Toolkit* hinzu, indem Sie in der Menüleiste **Mixed Reality Toolkit** > **Add to Scene and Configure..** (Zu Szene hinzufügen und konfigurieren...)</span><span class="sxs-lookup"><span data-stu-id="104b1-158">Add the *Mixed Reality Toolkit* to your current scene by selecting **Mixed Reality Toolkit** > **Add to Scene and Configure..**</span></span> <span data-ttu-id="104b1-159">auswählen.</span><span class="sxs-lookup"><span data-stu-id="104b1-159">from the menu bar.</span></span> <span data-ttu-id="104b1-160">Wenn dieses Menüelement nach dem Importieren des Mixed Reality-Toolkits nicht angezeigt wird, starten Sie Unity neu.</span><span class="sxs-lookup"><span data-stu-id="104b1-160">If you don't see this menu item after importing the mixed reality toolkit, restart Unity.</span></span>

    ![Lektion 1 Abschnitt 4 Schritt 1](images/mrlearning-base-ch1-4-step1.JPG)

    > [!NOTE]
    > <span data-ttu-id="104b1-162">Möglicherweise wird ein Popupdialogfeld zum Auswählen eines [Profils für das Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html) angezeigt.</span><span class="sxs-lookup"><span data-stu-id="104b1-162">You may see a pop-up dialog box for selecting a [profile for the Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html).</span></span> <span data-ttu-id="104b1-163">Wählen Sie das Profil *DefaultHoloLens2ConfigurationProfile* aus, indem Sie darauf doppelklicken.</span><span class="sxs-lookup"><span data-stu-id="104b1-163">Choose the profile named *DefaultHoloLens2ConfigurationProfile* by double-clicking it.</span></span>

2. <span data-ttu-id="104b1-164">Ihre Szene verfügt nun über mehrere neue Elemente und Änderungen.</span><span class="sxs-lookup"><span data-stu-id="104b1-164">Your scene will have several new items and modifications.</span></span> <span data-ttu-id="104b1-165">Speichern Sie Ihre Szene unter einem anderen Namen, indem Sie auf **Datei** > **Speichern unter...** klicken, und geben Sie der Szene einen Namen, beispielsweise *Basisszene*.</span><span class="sxs-lookup"><span data-stu-id="104b1-165">Save your scene under a different name by clicking **File** > **Save As...**, and give your scene a name, such as *BaseScene*.</span></span> <span data-ttu-id="104b1-166">Ordnen Sie Ihre Szene ein, indem Sie sie im Ordner *Scenes* (Szenen) im Ordner *Assets* (Ressourcen) Ihres Projekts speichern.</span><span class="sxs-lookup"><span data-stu-id="104b1-166">Keep your scene organized by saving it to the *Scenes* folder in your project’s *Assets* folder.</span></span>

    ![Lektion 1 Abschnitt 4 Schritt 2a](images/mrlearning-base-ch1-4-step2a.JPG)

    ![Lektion 1 Abschnitt 4 Schritt 2b](images/mrlearning-base-ch1-4-step2b.JPG)

## <a name="build-your-application-to-your-device"></a><span data-ttu-id="104b1-169">Erstellen Ihrer Anwendung auf Ihrem Gerät</span><span class="sxs-lookup"><span data-stu-id="104b1-169">Build your application to your device</span></span>

1. <span data-ttu-id="104b1-170">Wenn Sie das Fenster *Buildeinstellungen* aus den vorherigen Abschnitten geschlossen haben, öffnen Sie das Fenster *Buildeinstellungen* erneut, indem Sie zu **Datei** > **Buildeinstellungen** wechseln.</span><span class="sxs-lookup"><span data-stu-id="104b1-170">If you closed the *Build Settings* window from the previous sections, open the *Build Settings* window again by going to **File** > **Build Settings**.</span></span>

    ![Lektion 1 Abschnitt 5 Schritt 1](images/mrlearning-base-ch1-5-step1.JPG)

2. <span data-ttu-id="104b1-172">Achten Sie darauf, dass Ihre soeben erstellte Szene in der Liste *Scenes in Build* (Szenen im Build) enthalten ist, indem Sie auf die Schaltfläche **Add Open Scenes** (Geöffnete Szenen hinzufügen) klicken, während die Szene in Unity geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="104b1-172">Ensure the scene you just created is in the *Scenes in Build* list by clicking on the **Add Open Scenes** button while your scene is open in Unity.</span></span>

3. <span data-ttu-id="104b1-173">Klicken Sie auf die Schaltfläche **Build** (Erstellen), um den Buildprozess zu starten.</span><span class="sxs-lookup"><span data-stu-id="104b1-173">Press the **Build** button to begin the build process.</span></span>

    ![Lektion 1 Abschnitt 5 Schritt 3](images/mrlearning-base-ch1-5-step3.JPG)

4. <span data-ttu-id="104b1-175">Erstellen und benennen Sie einen neuen Ordner für Ihre Anwendung.</span><span class="sxs-lookup"><span data-stu-id="104b1-175">Create and name a new folder for your application.</span></span> <span data-ttu-id="104b1-176">In der folgenden Abbildung können Sie sehen, dass ein Ordner mit dem Namen „App“ erstellt wurde, der die Anwendung enthalten soll.</span><span class="sxs-lookup"><span data-stu-id="104b1-176">In the image below, a folder with the name App was created to contain the application.</span></span> <span data-ttu-id="104b1-177">Klicken Sie auf **Select Folder** (Ordner auswählen), um mit der Erstellung im neu erstellten Ordner zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="104b1-177">Click **Select Folder** to begin building to the newly created folder.</span></span> <span data-ttu-id="104b1-178">Nach Abschluss der Erstellung (des Buildvorgangs) können Sie das Fenster *Build Settings* (Buildeinstellungen) in Unity schließen.</span><span class="sxs-lookup"><span data-stu-id="104b1-178">After the build has completed, you can close the *Build Settings* window in Unity.</span></span>

    ![Lektion 1 Abschnitt 5 Schritt 4](images/mrlearning-base-ch1-5-step4.JPG)

    >[!IMPORTANT]
    ><span data-ttu-id="104b1-180">Wenn der Vorgang fehlschlägt, wiederholen Sie den Buildvorgang, oder starten Sie Unity neu, und wiederholen Sie dann den Buildvorgang.</span><span class="sxs-lookup"><span data-stu-id="104b1-180">If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="104b1-181">Eventuell wird ein Fehler angezeigt, z. B. "Fehler: CS0246 = Der Typ- oder Namespacename 'XX' konnte nicht gefunden werden. (Fehlt eine Using-Anweisung oder ein Assemblyverweis?)"</span><span class="sxs-lookup"><span data-stu-id="104b1-181">If you see an error, such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?).</span></span> <span data-ttu-id="104b1-182">In diesem Fall müssen Sie möglicherweise das [Windows 10 SDK (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk) installieren.</span><span class="sxs-lookup"><span data-stu-id="104b1-182">If so, you might need to install [Windows 10 SDK (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk)</span></span>

5. <span data-ttu-id="104b1-183">Öffnen Sie nach Abschluss des Buildvorgangs den neu erstellten Ordner, der Ihre neu erstellten Anwendungsdateien enthält.</span><span class="sxs-lookup"><span data-stu-id="104b1-183">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="104b1-184">Doppelklicken Sie auf die Projektmappe *MixedRealityBase.sln* (oder auf den entsprechenden Namen, wenn Sie einen alternativen Namen für Ihr Projekt verwendet haben), um die Projektmappendatei in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="104b1-184">Double-click on the *MixedRealityBase.sln* solution, or the corresponding name, if you used an alternative name for your project, to open the solution file in Visual Studio.</span></span>

    >[!NOTE]
    ><span data-ttu-id="104b1-185">Achten Sie darauf, dass Sie den neu erstellten Ordner öffnen (also den Ordner *App*, wenn Sie die Namenskonventionen in den vorherigen Schritten befolgt haben), weil außerhalb dieses Ordners noch eine SLN-Datei mit einem ähnlichen Namen vorhanden ist, die nicht mit der SLN-Datei im Buildordner verwechselt werden darf.</span><span class="sxs-lookup"><span data-stu-id="104b1-185">Be sure to open the newly created folder (i.e. the *App* folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder, that is not to be confused with the .sln file inside the build folder.</span></span> <span data-ttu-id="104b1-186">Die Ordnerstruktur sollte ähnlich wie in dieser Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="104b1-186">The folder structure should look similar to the image below.</span></span>
    >
    ><span data-ttu-id="104b1-187">Wenn Sie von Visual Studio zur Installation neuer Komponenten aufgefordert werden, nehmen Sie sich einen Moment Zeit, um zu überprüfen, ob alle erforderlichen Komponenten (wie auf der Seite [Installieren der Tools](install-the-tools.md) angegeben) installiert sind.</span><span class="sxs-lookup"><span data-stu-id="104b1-187">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in [the "Install the Tools" page](install-the-tools.md)</span></span>

    ![Lektion 1 Abschnitt 5 Schritt 5](images/mrlearning-base-ch1-5-step5.JPG)

6. <span data-ttu-id="104b1-189">Verbinden Sie Ihre HoloLens 2 mit Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="104b1-189">Connect your HoloLens 2 into your PC.</span></span> <span data-ttu-id="104b1-190">Bei diesen Anweisungen wird davon ausgegangen, dass Sie auf einem HoloLens 2-Gerät bereitstellen. Sie können die Bereitstellung aber auch auf dem [HoloLens 2-Emulator](using-the-hololens-emulator.md) vornehmen oder ein [App-Paket für das Querladen](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>) erstellen.</span><span class="sxs-lookup"><span data-stu-id="104b1-190">While these instructions assume you will be deploying to a HoloLens 2 device, you might also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span></span>

    >[!IMPORTANT]
    ><span data-ttu-id="104b1-191">Bevor Sie den Build für Ihr Gerät erstellen, muss das Gerät in den *Entwicklermodus* versetzt und mit Ihrem Entwicklungscomputer gekoppelt werden.</span><span class="sxs-lookup"><span data-stu-id="104b1-191">Before building to your device, the device must be in *Developer Mode* and paired with your development machine.</span></span> <span data-ttu-id="104b1-192">Sie können beide Schritte ausführen, indem Sie [diese Anweisungen](using-visual-studio.md) befolgen.</span><span class="sxs-lookup"><span data-stu-id="104b1-192">Both of these steps can be completed by following [these instructions](using-visual-studio.md)</span></span>

7. <span data-ttu-id="104b1-193">Konfigurieren Sie Visual Studio für die Erstellung auf Ihrem HoloLens 2-Gerät, indem Sie die Konfiguration *Release* oder *Master*, die Architektur *ARM* und das Ziel *Device* (Gerät) auswählen.</span><span class="sxs-lookup"><span data-stu-id="104b1-193">Configure Visual Studio for building to your HoloLens 2 by selecting the *Release* or *Master* configuration, the *ARM* architecture, and *Device* as target.</span></span>

    ![Lektion 1 Abschnitt 5 Schritt 8](images/mrlearning-base-ch1-5-step7.JPG)

8. <span data-ttu-id="104b1-195">Der letzte Schritt ist die Erstellung und Bereitstellung auf Ihrem Gerät durch Auswählen von **Debuggen** > **Starten ohne Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="104b1-195">The final step is to build and deploy to your device by selecting **Debug** > **Start without debugging**.</span></span> <span data-ttu-id="104b1-196">Wenn Sie *Starten ohne Debuggen* auswählen, wird die Anwendung sofort nach einem erfolgreichen Buildvorgang auf Ihrem Gerät gestartet, ohne dass jedoch der Debugger gestartet und Debuginformationen in Visual Studio angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="104b1-196">Selecting *Start without Debugging* causes the application to immediately start on your device upon a successful build, but without the debugger attached and information appearing in Visual Studio.</span></span> <span data-ttu-id="104b1-197">Dies bedeutet auch, dass Sie das USB-Kabel entfernen können, während Ihre Anwendung auf Ihrem HoloLens 2-Gerät ausgeführt wird, ohne dass die Anwendung beendet wird.</span><span class="sxs-lookup"><span data-stu-id="104b1-197">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="104b1-198">Sie können auch **Build** > **Projektmappe bereitstellen** auswählen, um die Anwendung auf Ihrem Gerät bereitzustellen, ohne dass sie automatisch gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="104b1-198">You might also select **Build** > **Deploy Solution** to deploy to your device without having the application automatically start.</span></span>

    ![Lektion 1 Abschnitt 5 Schritt 9](images/mrlearning-base-ch1-5-step8.JPG)

## <a name="congratulations"></a><span data-ttu-id="104b1-200">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="104b1-200">Congratulations</span></span>

<span data-ttu-id="104b1-201">Sie haben jetzt Ihre erste HoloLens 2-Anwendung bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="104b1-201">You have now deployed your first HoloLens 2 application.</span></span> <span data-ttu-id="104b1-202">Während Sie sich in ihr bewegen, sollten Sie ein Gittermodell für die Raumzuordnung sehen, das alle Oberflächen bedeckt, die von der HoloLens 2 erkannt wurden.</span><span class="sxs-lookup"><span data-stu-id="104b1-202">As you walk around, you should see a spatial mapping mesh covering all the surfaces that have been perceived by the HoloLens 2.</span></span> <span data-ttu-id="104b1-203">Darüber hinaus sollten Sie Indikatoren auf Ihren Händen und Fingern für die Handverfolgung und einen Frameratenzähler zum Überwachen der Anwendungsleistung sehen.</span><span class="sxs-lookup"><span data-stu-id="104b1-203">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on application performance.</span></span> <span data-ttu-id="104b1-204">Dies sind nur einige der grundlegenden Elemente, die standardmäßig im Mixed Reality-Toolkit enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="104b1-204">These are just a few of the foundational pieces, included out of the box, with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="104b1-205">In den folgenden Lektionen fügen Sie Ihrer Szene mehr Inhalte und Interaktivität hinzu, sodass Sie alle Funktionen der HoloLens 2 und des Mixed Reality-Toolkits umfassend erkunden können.</span><span class="sxs-lookup"><span data-stu-id="104b1-205">In the lessons to come, you will start adding more content and interactivity to your scene so that you can fully explore the capabilities of HoloLens 2 and the Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="104b1-206">Möglicherweise bemerken Sie in der App den Visual Profiler.</span><span class="sxs-lookup"><span data-stu-id="104b1-206">In the app, you may notice the visual profiler.</span></span> <span data-ttu-id="104b1-207">In [Lektion 5](mrlearning-base-ch5.md) erfahren Sie, wie Sie den Frameratenzähler mithilfe eines Sprachbefehls umschalten.</span><span class="sxs-lookup"><span data-stu-id="104b1-207">You will cover how to toggle the frame rate counter using a voice command in [Lesson 5](mrlearning-base-ch5.md).</span></span> <span data-ttu-id="104b1-208">Im Allgemeinen empfiehlt es sich, den Visual Profiler während der Entwicklung stets eingeblendet zu lassen, damit Sie nachvollziehen können, wenn sich Codeänderungen auf die Leistung auswirken.</span><span class="sxs-lookup"><span data-stu-id="104b1-208">It is generally recommended to keep the visual profiler visible at all times during development to understand when code changes may have impacted perf.</span></span> <span data-ttu-id="104b1-209">HoloLens 2-Anwendungen sollten [durchgängig bei 60 FPS ausgeführt werden](understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="104b1-209">HoloLens 2 application should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

[<span data-ttu-id="104b1-210">Nächste Lektion: 3. Erstellen der Benutzeroberfläche und Konfigurieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="104b1-210">Next Lesson: 3. Creating user interface and configure Mixed Reality Toolkit</span></span>](mrlearning-base-ch2.md)
