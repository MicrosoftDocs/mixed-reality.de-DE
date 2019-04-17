---
title: MR Grundlagen 101E - vollständige Projekt mit dem emulator
description: Führen Sie diese exemplarische Vorgehensweise mit Unity, Visual Studio Emulator für HoloLens zum Erlernen der Grundlagen einer holographic-Anwendung programmieren.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Gemischte Realität Windows Mixed Reality, HoloLens, Hologramm, Academy, Tutorial, emulator
ms.openlocfilehash: 77f7d497396937bf471a69fa514cef84ab0b699d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593988"
---
>[!NOTE]
><span data-ttu-id="0b728-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="0b728-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="0b728-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="0b728-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="0b728-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="0b728-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="0b728-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="0b728-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="0b728-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="0b728-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="0b728-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="0b728-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a><span data-ttu-id="0b728-110">MR Basics 101E: Vollständige Projekt mit dem emulator</span><span class="sxs-lookup"><span data-stu-id="0b728-110">MR Basics 101E: Complete project with emulator</span></span>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

<span data-ttu-id="0b728-111">Dieses Tutorial führt Sie durch ein vollständiges-Projekt, erstellt in Unity, die Windows Mixed Reality-Kernfunktionen auf, einschließlich HoloLens veranschaulicht [bestaunen](gaze.md), [Gesten](gestures.md), [voice-Eingabe](voice-input.md), [räumliche Sound](spatial-sound.md) und [räumliche Zuordnung](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="0b728-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span> <span data-ttu-id="0b728-112">Das Tutorial dauert etwa eine Stunde bis zum Abschließen.</span><span class="sxs-lookup"><span data-stu-id="0b728-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="0b728-113">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="0b728-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0b728-114">Kurs</span><span class="sxs-lookup"><span data-stu-id="0b728-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="0b728-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0b728-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0b728-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="0b728-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="0b728-117">MR Basics 101E: Vollständige Projekt mit dem emulator</span><span class="sxs-lookup"><span data-stu-id="0b728-117">MR Basics 101E: Complete project with emulator</span></span></td><td style="text-align: center;"> <span data-ttu-id="0b728-118">✔️</span><span class="sxs-lookup"><span data-stu-id="0b728-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="0b728-119">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="0b728-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="0b728-120">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="0b728-120">Prerequisites</span></span>

* <span data-ttu-id="0b728-121">Ein Windows 10-PCs mit dem richtigen konfiguriert [-Tools installiert](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="0b728-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

### <a name="project-files"></a><span data-ttu-id="0b728-122">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="0b728-122">Project files</span></span>

* <span data-ttu-id="0b728-123">Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) vom Projekt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="0b728-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="0b728-124"> Ist Unity 2017.2 oder höher erforderlich.</span><span class="sxs-lookup"><span data-stu-id="0b728-124"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="0b728-125">Wenn Sie weitere Unity 5.6-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="0b728-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="0b728-126">Wenn Sie weitere Unity 5.5-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="0b728-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="0b728-127">Wenn Sie weitere 5.4 von Unity-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="0b728-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="0b728-128">Un-Archive die Dateien auf dem Desktop oder andere einfach auf den Speicherort zugreifen.</span><span class="sxs-lookup"><span data-stu-id="0b728-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="0b728-129">Behalten Sie den Ordnernamen als **Origami**.</span><span class="sxs-lookup"><span data-stu-id="0b728-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="0b728-130">Wenn Sie vor dem Herunterladen, den Quellcode ansehen möchten es [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="0b728-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="0b728-131">Kapitel 1: "Holo" world</span><span class="sxs-lookup"><span data-stu-id="0b728-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

<span data-ttu-id="0b728-132">In diesem Kapitel wir unser erstes Unity-Projekt und durchlaufen Sie den Build einrichten und Bereitstellen von Prozess.</span><span class="sxs-lookup"><span data-stu-id="0b728-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="0b728-133">Ziele</span><span class="sxs-lookup"><span data-stu-id="0b728-133">Objectives</span></span>

* <span data-ttu-id="0b728-134">Richten Sie Unity aus, für die holographic Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="0b728-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="0b728-135">Stellen Sie ggf. ein Hologramm.</span><span class="sxs-lookup"><span data-stu-id="0b728-135">Make a hologram.</span></span>
* <span data-ttu-id="0b728-136">Finden Sie ggf. ein Hologramm, die Sie vorgenommen.</span><span class="sxs-lookup"><span data-stu-id="0b728-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="0b728-137">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="0b728-137">Instructions</span></span>

* <span data-ttu-id="0b728-138">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="0b728-138">Start Unity.</span></span>
* <span data-ttu-id="0b728-139">Wählen Sie **öffnen**.</span><span class="sxs-lookup"><span data-stu-id="0b728-139">Select **Open**.</span></span>
* <span data-ttu-id="0b728-140">Geben Sie den Speicherort als dem **Origami** Ordner Sie zuvor nicht archiviert.</span><span class="sxs-lookup"><span data-stu-id="0b728-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="0b728-141">Wählen Sie **Origami** , und klicken Sie auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="0b728-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="0b728-142">Speichern Sie die neue Szene: **Datei** / **Szene speichern unter**.</span><span class="sxs-lookup"><span data-stu-id="0b728-142">Save the new scene: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="0b728-143">Benennen Sie die Szene **Origami** , und drücken Sie die **speichern** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="0b728-143">Name the scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-camera"></a><span data-ttu-id="0b728-144">Einrichten der Hauptkamera</span><span class="sxs-lookup"><span data-stu-id="0b728-144">Setup the main camera</span></span>

* <span data-ttu-id="0b728-145">In der **Hierarchie Bereich**Option **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="0b728-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="0b728-146">In der **Inspektor** positionieren Sie die Transformation **0,0,0**.</span><span class="sxs-lookup"><span data-stu-id="0b728-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="0b728-147">Suchen der **löschen Flags** -Eigenschaft, und ändern die Dropdownliste aus **Skybox** zu **Volltonfarbe**.</span><span class="sxs-lookup"><span data-stu-id="0b728-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="0b728-148">Klicken Sie auf die **Hintergrund** Feld, um ein Farbwähler zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="0b728-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="0b728-149">Legen Sie **R, G, B und A** zu **0**.</span><span class="sxs-lookup"><span data-stu-id="0b728-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="0b728-150">Einrichten der Szene</span><span class="sxs-lookup"><span data-stu-id="0b728-150">Setup the scene</span></span>

* <span data-ttu-id="0b728-151">In der **Hierarchie Bereich**, klicken Sie auf **erstellen** und **leere erstellen**.</span><span class="sxs-lookup"><span data-stu-id="0b728-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="0b728-152">Mit der rechten Maustaste den neuen **"gameobject"** und "Umbenennen" auswählen.</span><span class="sxs-lookup"><span data-stu-id="0b728-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="0b728-153">Benennen Sie das "gameobject" zu **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="0b728-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="0b728-154">Von der **Hologramme** Ordner in der **Projektfenster**:</span><span class="sxs-lookup"><span data-stu-id="0b728-154">From the **Holograms** folder in the **Project Panel**:</span></span>
  * <span data-ttu-id="0b728-155">Ziehen Sie **Phase** in die Hierarchie ein untergeordnetes Element des **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="0b728-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="0b728-156">Ziehen Sie **Sphere1** in die Hierarchie ein untergeordnetes Element des **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="0b728-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="0b728-157">Ziehen Sie **Sphere2** in die Hierarchie ein untergeordnetes Element des **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="0b728-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="0b728-158">Mit der rechten Maustaste die **gerichtetes Licht** -Objekt in der **Hierarchie Bereich** , und wählen Sie **löschen**.</span><span class="sxs-lookup"><span data-stu-id="0b728-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="0b728-159">Von der **Hologramme** Ordner, ziehen Sie **Lichter** in das Stammverzeichnis der **Hierarchie Bereich**.</span><span class="sxs-lookup"><span data-stu-id="0b728-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="0b728-160">In der **Hierarchie**, wählen die **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="0b728-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="0b728-161">In der **Inspektor**, positionieren Sie die Transformation **0, Verschiebung von -0,5 und 2.0**.</span><span class="sxs-lookup"><span data-stu-id="0b728-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="0b728-162">Drücken Sie die **spielen** -Schaltfläche in Unity, um Ihre Hologramme der Vorschau anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="0b728-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="0b728-163">Daraufhin sollte die Origami-Objekte im Vorschaufenster.</span><span class="sxs-lookup"><span data-stu-id="0b728-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="0b728-164">Drücken Sie **spielen** ein zweites Mal im Vorschaumodus zu beenden.</span><span class="sxs-lookup"><span data-stu-id="0b728-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="0b728-165">Exportieren Sie das Projekt aus Unity in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0b728-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="0b728-166">Im Unity-Option **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="0b728-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="0b728-167">Wählen Sie **Windows Store** in die **Plattform** aus, und klicken Sie auf **Plattform wechseln**.</span><span class="sxs-lookup"><span data-stu-id="0b728-167">Select **Windows Store** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="0b728-168">Legen Sie **SDK** zu **universelle 10** und **Buildtyp** zu **D3D**.</span><span class="sxs-lookup"><span data-stu-id="0b728-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="0b728-169">Überprüfen Sie **Unity C# Projekte**.</span><span class="sxs-lookup"><span data-stu-id="0b728-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="0b728-170">Klicken Sie auf **öffnen Szenen hinzufügen** die Szene hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="0b728-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="0b728-171">Klicken Sie auf **Playereinstellungen...** .</span><span class="sxs-lookup"><span data-stu-id="0b728-171">Click **Player Settings...**.</span></span>
* <span data-ttu-id="0b728-172">Im Inspektor-Bereich die Option der **Windows Store-Logo**.</span><span class="sxs-lookup"><span data-stu-id="0b728-172">In the Inspector Panel select the **Windows Store logo**.</span></span> <span data-ttu-id="0b728-173">Wählen Sie dann **Veröffentlichungseinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="0b728-173">Then select **Publishing Settings**.</span></span>
* <span data-ttu-id="0b728-174">In der **Funktionen** wählen Sie im Abschnitt der **Mikrofon** und **SpatialPerception** Funktionen.</span><span class="sxs-lookup"><span data-stu-id="0b728-174">In the **Capabilities** section, select the **Microphone** and **SpatialPerception** capabilities.</span></span>
* <span data-ttu-id="0b728-175">Klicken Sie im Fenster Buildeinstellungen auf **erstellen**.</span><span class="sxs-lookup"><span data-stu-id="0b728-175">Back in the Build Settings window, click **Build**.</span></span>
* <span data-ttu-id="0b728-176">Erstellen Sie eine **neuer Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="0b728-176">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="0b728-177">Mausklick die **App-Ordner**.</span><span class="sxs-lookup"><span data-stu-id="0b728-177">Single click the **App Folder**.</span></span>
* <span data-ttu-id="0b728-178">Drücken Sie **wählen Sie Ordner**.</span><span class="sxs-lookup"><span data-stu-id="0b728-178">Press **Select Folder**.</span></span>
* <span data-ttu-id="0b728-179">Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0b728-179">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="0b728-180">Öffnen der **App** Ordner.</span><span class="sxs-lookup"><span data-stu-id="0b728-180">Open the **App** folder.</span></span>
* <span data-ttu-id="0b728-181">Öffnen der **Origami Visual Studio-Projektmappe**.</span><span class="sxs-lookup"><span data-stu-id="0b728-181">Open the **Origami Visual Studio Solution**.</span></span>
* <span data-ttu-id="0b728-182">Verwenden obere auf der Symbolleiste in Visual Studio, ändern Sie das Ziel vom Debugmodus in den **Version** und ARM, **X86**.</span><span class="sxs-lookup"><span data-stu-id="0b728-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
  * <span data-ttu-id="0b728-183">Klicken Sie auf den Pfeil neben der Schaltfläche ", und wählen **Emulator für HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="0b728-183">Click on the arrow next to the Device button, and select **HoloLens Emulator**.</span></span>
  * <span data-ttu-id="0b728-184">Klicken Sie auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="0b728-184">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
  * <span data-ttu-id="0b728-185">Nach einiger Zeit wird der Emulator mit dem Origami-Projekt gestartet.</span><span class="sxs-lookup"><span data-stu-id="0b728-185">After some time the emulator will start with the Origami project.</span></span> <span data-ttu-id="0b728-186">Beim ersten Starten der [Emulator](using-the-hololens-emulator.md), es kann bis zu 15 Minuten, bis der Emulator gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="0b728-186">When first launching the [emulator](using-the-hololens-emulator.md), it can take as long as 15 minutes for the emulator to start up.</span></span> <span data-ttu-id="0b728-187">Nachdem es gestartet wurde, schließen Sie es nicht.</span><span class="sxs-lookup"><span data-stu-id="0b728-187">Once it starts, do not close it.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="0b728-188">Kapitel 2: Blicke</span><span class="sxs-lookup"><span data-stu-id="0b728-188">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

<span data-ttu-id="0b728-189">In diesem Kapitel werden wir zum Einfügen des ersten der drei Methoden zur Interaktion mit Ihrem Hologramme: [bestaunen](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="0b728-189">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="0b728-190">Ziele</span><span class="sxs-lookup"><span data-stu-id="0b728-190">Objectives</span></span>

* <span data-ttu-id="0b728-191">Visualisieren Sie Ihre Blicke mithilfe eines Cursors Welt gesperrt.</span><span class="sxs-lookup"><span data-stu-id="0b728-191">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="0b728-192">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="0b728-192">Instructions</span></span>

* <span data-ttu-id="0b728-193">Wechseln Sie zurück zu Ihrem Unity-Projekt, und schließen Sie das Fenster "erstellen" aus, wenn es noch geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="0b728-193">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="0b728-194">Wählen Sie die **Hologramme** Ordner in der **Projektfenster**.</span><span class="sxs-lookup"><span data-stu-id="0b728-194">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="0b728-195">Ziehen Sie die **Cursor** -Objekt in der **Hierarchie Bereich** auf der Stammebene.</span><span class="sxs-lookup"><span data-stu-id="0b728-195">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="0b728-196">Doppelklicken Sie auf die **Cursor** Objekt, das ein genauer ansehen.</span><span class="sxs-lookup"><span data-stu-id="0b728-196">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="0b728-197">Mit der rechten Maustaste auf die **Skripts** Ordner im Projektfenster.</span><span class="sxs-lookup"><span data-stu-id="0b728-197">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="0b728-198">Klicken Sie auf die **erstellen** Untermenü.</span><span class="sxs-lookup"><span data-stu-id="0b728-198">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="0b728-199">Wählen Sie  **C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="0b728-199">Select **C# Script**.</span></span>
* <span data-ttu-id="0b728-200">Nennen Sie das Skript **WorldCursor**.</span><span class="sxs-lookup"><span data-stu-id="0b728-200">Name the script **WorldCursor**.</span></span> <span data-ttu-id="0b728-201">Hinweis: Beim Namen wird Groß- und Kleinschreibung beachtet.</span><span class="sxs-lookup"><span data-stu-id="0b728-201">Note: The name is case-sensitive.</span></span> <span data-ttu-id="0b728-202">Sie müssen sich nicht um die Erweiterung .cs hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="0b728-202">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="0b728-203">Wählen Sie die **Cursor** -Objekt in der **Hierarchie Bereich**.</span><span class="sxs-lookup"><span data-stu-id="0b728-203">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="0b728-204">Drag & drop die **WorldCursor** Skript in die **Inspektor Bereich**.</span><span class="sxs-lookup"><span data-stu-id="0b728-204">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="0b728-205">Doppelklicken Sie auf die **WorldCursor** Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="0b728-205">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="0b728-206">Kopieren Sie diesen Code in **WorldCursor.cs** und **Alles speichern**.</span><span class="sxs-lookup"><span data-stu-id="0b728-206">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move thecursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* <span data-ttu-id="0b728-207">Erstellen Sie die app neu **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="0b728-207">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="0b728-208">Zurück zu Visual Studio-Projektmappe zuvor verwendet, um auf dem Emulator bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="0b728-208">Return to the Visual Studio solution previously used to deploy to the emulator.</span></span>
* <span data-ttu-id="0b728-209">Wählen Sie "Alles neu laden" Wenn Sie aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="0b728-209">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="0b728-210">Klicken Sie auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="0b728-210">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="0b728-211">Verwenden Sie die Xbox-Controller, um in der Szene zu suchen.</span><span class="sxs-lookup"><span data-stu-id="0b728-211">Use the Xbox controller to look around the scene.</span></span> <span data-ttu-id="0b728-212">Beachten Sie, wie der Cursor die Form der Objekte interagiert.</span><span class="sxs-lookup"><span data-stu-id="0b728-212">Notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="0b728-213">Kapitel 3 - Gesten</span><span class="sxs-lookup"><span data-stu-id="0b728-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

<span data-ttu-id="0b728-214">In diesem Kapitel werden wir fügen Unterstützung für [Gesten](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="0b728-214">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="0b728-215">Wenn der Benutzer eine Dokument Kugel auswählt, erstellen wir die Kugel liegen, indem die Schwerkraft mithilfe von Unity Physik-Engine aktivieren.</span><span class="sxs-lookup"><span data-stu-id="0b728-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="0b728-216">Ziele</span><span class="sxs-lookup"><span data-stu-id="0b728-216">Objectives</span></span>

* <span data-ttu-id="0b728-217">Steuern Sie Ihre Hologramme mit dieser Option Bewegung.</span><span class="sxs-lookup"><span data-stu-id="0b728-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="0b728-218">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="0b728-218">Instructions</span></span>

<span data-ttu-id="0b728-219">Wir beginnen, Erstellen eines Skripts, als die Option Geste erkannt werden können.</span><span class="sxs-lookup"><span data-stu-id="0b728-219">We'll start by creating a script than can detect the Select gesture.</span></span>

* <span data-ttu-id="0b728-220">In der **Skripts** Ordner, erstellen Sie ein Skript, mit dem Namen **GazeGestureManager**.</span><span class="sxs-lookup"><span data-stu-id="0b728-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="0b728-221">Ziehen Sie die **GazeGestureManager** Skript auf die **OrigamiCollection** Objekt in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="0b728-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="0b728-222">Öffnen der **GazeGestureManager** Skript im Visual Studio, und fügen Sie den folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="0b728-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Start()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* <span data-ttu-id="0b728-223">Erstellen Sie ein weiteres Skript im Ordner "Scripts", dieses Mal mit dem Namen **SphereCommands**.</span><span class="sxs-lookup"><span data-stu-id="0b728-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="0b728-224">Erweitern Sie die **OrigamiCollection** Objekt in der Hierarchie angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0b728-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="0b728-225">Ziehen Sie die **SphereCommands** Skript auf die **Sphere1** Objekt in der Hierarchie-Bereich.</span><span class="sxs-lookup"><span data-stu-id="0b728-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="0b728-226">Ziehen Sie die **SphereCommands** Skript auf die **Sphere2** Objekt in der Hierarchie-Bereich.</span><span class="sxs-lookup"><span data-stu-id="0b728-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="0b728-227">Öffnen Sie das Skript zur Bearbeitung in Visual Studio, und Ersetzen Sie den Standardcode durch dies:</span><span class="sxs-lookup"><span data-stu-id="0b728-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* <span data-ttu-id="0b728-228">Exportieren, erstellen und Bereitstellen der app im Emulator für HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0b728-228">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="0b728-229">Suchen Sie in der Szene, und auf einem der die Kugeln center.</span><span class="sxs-lookup"><span data-stu-id="0b728-229">Look around the scene, and center on one of the spheres.</span></span>
* <span data-ttu-id="0b728-230">Drücken Sie die **ein** auf der Xbox-Controller auf die Schaltfläche, oder drücken Sie die LEERTASTE, um die Select-Aktion zu simulieren.</span><span class="sxs-lookup"><span data-stu-id="0b728-230">Press the **A** button on the Xbox controller or press the Spacebar to simulate the Select gesture.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="0b728-231">Kapitel 4 – Sprache</span><span class="sxs-lookup"><span data-stu-id="0b728-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

<span data-ttu-id="0b728-232">In diesem Kapitel werden wir fügen Unterstützung für zwei [Sprachbefehle](voice-input.md): "Zurücksetzen World", gibt der gelöschten Kugeln an ihrem ursprünglichen Speicherort, und klicken Sie auf "Drop Kugel" die Kugel fallen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="0b728-232">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to returns the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="0b728-233">Ziele</span><span class="sxs-lookup"><span data-stu-id="0b728-233">Objectives</span></span>

* <span data-ttu-id="0b728-234">Fügen Sie Sprachbefehle, die immer lauschen, im Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="0b728-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="0b728-235">Erstellen Sie ggf. ein Hologramm, die auf einen Sprachbefehl reagiert.</span><span class="sxs-lookup"><span data-stu-id="0b728-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="0b728-236">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="0b728-236">Instructions</span></span>

* <span data-ttu-id="0b728-237">In der **Skripts** Ordner, erstellen Sie ein Skript, mit dem Namen **SpeechManager**.</span><span class="sxs-lookup"><span data-stu-id="0b728-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="0b728-238">Ziehen Sie die **SpeechManager** Skript auf die **OrigamiCollection** Objekt in der Hierarchie</span><span class="sxs-lookup"><span data-stu-id="0b728-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="0b728-239">Öffnen der **SpeechManager** Skripts in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b728-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="0b728-240">Kopieren Sie diesen Code in **SpeechManager.cs** und **Alles speichern**:</span><span class="sxs-lookup"><span data-stu-id="0b728-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* <span data-ttu-id="0b728-241">Öffnen der **SphereCommands** Skripts in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b728-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="0b728-242">Aktualisieren Sie das Skript wie folgt:</span><span class="sxs-lookup"><span data-stu-id="0b728-242">Update the script to read as follows:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* <span data-ttu-id="0b728-243">Exportieren, erstellen und Bereitstellen der app im Emulator für HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0b728-243">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="0b728-244">Der Emulator unterstützen Ihres Computers Mikrofon und reagieren auf Ihre Stimme: Passen Sie die Ansicht aus, damit der Cursor auf einem der die Kugeln befindet, und sagen Sie "Drop Kugel".</span><span class="sxs-lookup"><span data-stu-id="0b728-244">The emulator will support your PC's microphone and respond to your voice: adjust the view so the cursor is on one of the spheres, and say "Drop Sphere".</span></span>
* <span data-ttu-id="0b728-245">Sagen Sie "**zurücksetzen Welt**", die sie wieder in ihre ursprünglichen Positionen verschieben.</span><span class="sxs-lookup"><span data-stu-id="0b728-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="0b728-246">Kapitel 5 – räumliche sound</span><span class="sxs-lookup"><span data-stu-id="0b728-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

<span data-ttu-id="0b728-247">In diesem Kapitel wir Musik hinzufügen, um die app, und dann Soundeffekten auf bestimmte Aktionen auszulösen.</span><span class="sxs-lookup"><span data-stu-id="0b728-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="0b728-248">Wir verwenden [räumliche Sound](spatial-sound.md) Sounds mit einen bestimmten Speicherort im 3D-Raum gewähren.</span><span class="sxs-lookup"><span data-stu-id="0b728-248">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="0b728-249">Ziele</span><span class="sxs-lookup"><span data-stu-id="0b728-249">Objectives</span></span>

* <span data-ttu-id="0b728-250">Hören Sie Hologramme in Ihrer Umgebung.</span><span class="sxs-lookup"><span data-stu-id="0b728-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="0b728-251">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="0b728-251">Instructions</span></span>

* <span data-ttu-id="0b728-252">Wählen Sie im oberen Menü Unity **Bearbeiten > Projekteinstellungen > Audio**</span><span class="sxs-lookup"><span data-stu-id="0b728-252">In the Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="0b728-253">Suchen der **Spatializer-Plug-Ins** festlegen, und wählen **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="0b728-253">Find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="0b728-254">Von der **Hologramme** Ordner, ziehen Sie die **Umgebung** -Objekt auf den **OrigamiCollection** Objekt in der Hierarchie-Bereich.</span><span class="sxs-lookup"><span data-stu-id="0b728-254">From the **Holograms** folder, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="0b728-255">Wählen Sie **OrigamiCollection** und suchen Sie die **Audio Source** Komponente.</span><span class="sxs-lookup"><span data-stu-id="0b728-255">Select **OrigamiCollection** and find the **Audio Source** component.</span></span> <span data-ttu-id="0b728-256">Ändern Sie diese Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="0b728-256">Change these properties:</span></span>
  * <span data-ttu-id="0b728-257">Überprüfen Sie die **Spatialize** Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="0b728-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="0b728-258">Überprüfen Sie die **auf aktiv wiedergeben**.</span><span class="sxs-lookup"><span data-stu-id="0b728-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="0b728-259">Änderung **räumliche Blend** zu **3D** durch den Schieberegler ganz nach rechts ziehen.</span><span class="sxs-lookup"><span data-stu-id="0b728-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span>
  * <span data-ttu-id="0b728-260">Überprüfen Sie die **Schleife** Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="0b728-260">Check the **Loop** property.</span></span>
  * <span data-ttu-id="0b728-261">Erweitern Sie **3D Sound Einstellungen**, und geben Sie **0,1** für **Doppler Ebene**.</span><span class="sxs-lookup"><span data-stu-id="0b728-261">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="0b728-262">Legen Sie **Volume Rolloff** zu **logarithmische Rolloff**.</span><span class="sxs-lookup"><span data-stu-id="0b728-262">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="0b728-263">Legen Sie **maximaler Abstand** zu **20**.</span><span class="sxs-lookup"><span data-stu-id="0b728-263">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="0b728-264">In der **Skripts** Ordner, erstellen Sie ein Skript, mit dem Namen **SphereSounds**.</span><span class="sxs-lookup"><span data-stu-id="0b728-264">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="0b728-265">Ziehen Sie **SphereSounds** auf die **Sphere1** und **Sphere2** Objekte in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="0b728-265">Drag **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="0b728-266">Open **SphereSounds** aktualisieren Sie den folgenden Code in Visual Studio und **Alles speichern**.</span><span class="sxs-lookup"><span data-stu-id="0b728-266">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* <span data-ttu-id="0b728-267">Speichern Sie das Skript aus, und zurück zu Unity.</span><span class="sxs-lookup"><span data-stu-id="0b728-267">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="0b728-268">Exportieren, erstellen und Bereitstellen der app im Emulator für HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0b728-268">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="0b728-269">Wear Kopfhörer, um den vollen Effekt zu erhalten, und verschieben Sie genauere und weiter von der Phase zum Ändern der Audiowiedergabe an.</span><span class="sxs-lookup"><span data-stu-id="0b728-269">Wear headphones to get the full effect, and move closer and further from the Stage to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="0b728-270">Kapitel 6 – räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="0b728-270">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

<span data-ttu-id="0b728-271">Nun verwenden wir [räumliche Zuordnung](spatial-mapping.md) ein wirkliches Objekt in der realen Welt die Spielfläche zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="0b728-271">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="0b728-272">Ziele</span><span class="sxs-lookup"><span data-stu-id="0b728-272">Objectives</span></span>

* <span data-ttu-id="0b728-273">Bringen Sie Ihre realen, in der virtuellen Welt.</span><span class="sxs-lookup"><span data-stu-id="0b728-273">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="0b728-274">Platzieren Sie Ihre Hologramme, wo sie sind die meisten für Sie.</span><span class="sxs-lookup"><span data-stu-id="0b728-274">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="0b728-275">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="0b728-275">Instructions</span></span>

* <span data-ttu-id="0b728-276">Klicken Sie auf die **Hologramme** Ordner im Projektfenster.</span><span class="sxs-lookup"><span data-stu-id="0b728-276">Click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="0b728-277">Ziehen Sie die **räumliche Zuordnung** Asset in das Stammverzeichnis der **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="0b728-277">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="0b728-278">Klicken Sie auf die **räumliche Zuordnung** Objekt in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="0b728-278">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="0b728-279">In der **Inspektor Bereich**, ändern Sie die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="0b728-279">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="0b728-280">Überprüfen Sie die **zeichnen Visual Gitter** Feld.</span><span class="sxs-lookup"><span data-stu-id="0b728-280">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="0b728-281">Suchen Sie **zeichnen Material** , und klicken Sie auf den Kreis auf der rechten Seite.</span><span class="sxs-lookup"><span data-stu-id="0b728-281">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="0b728-282">Typ "**Drahtmodell**" in das Suchfeld oben.</span><span class="sxs-lookup"><span data-stu-id="0b728-282">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="0b728-283">Klicken Sie auf das Ergebnis, und klicken Sie dann schließen Sie das Fenster.</span><span class="sxs-lookup"><span data-stu-id="0b728-283">Click on the result and then close the window.</span></span>
* <span data-ttu-id="0b728-284">Exportieren, erstellen und Bereitstellen der app im Emulator für HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0b728-284">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="0b728-285">Wenn die app ausgeführt wird, wird ein Netz von einer zuvor gescannte realen Wohnzimmer in Drahtmodell gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="0b728-285">When the app runs, a mesh of a previously scanned real-world living room will be rendered in wireframe.</span></span>
* <span data-ttu-id="0b728-286">Sehen Sie sich, wie eine parallele Kugel die Bühne verließ, und klicken Sie auf dem Boden liegen wird.</span><span class="sxs-lookup"><span data-stu-id="0b728-286">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="0b728-287">Jetzt zeigen wir Ihnen die OrigamiCollection an einem neuen Speicherort zu verschieben:</span><span class="sxs-lookup"><span data-stu-id="0b728-287">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="0b728-288">In der **Skripts** Ordner, erstellen Sie ein Skript, mit dem Namen **TapToPlaceParent**.</span><span class="sxs-lookup"><span data-stu-id="0b728-288">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="0b728-289">In der **Hierarchie**, erweitern Sie die **OrigamiCollection** , und wählen Sie die **Phase** Objekt.</span><span class="sxs-lookup"><span data-stu-id="0b728-289">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="0b728-290">Ziehen Sie die **TapToPlaceParent** -Skript auf die Stage-Objekt.</span><span class="sxs-lookup"><span data-stu-id="0b728-290">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="0b728-291">Öffnen der **TapToPlaceParent** Skript im Visual Studio, und aktualisieren, um folgende sein:</span><span class="sxs-lookup"><span data-stu-id="0b728-291">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* <span data-ttu-id="0b728-292">Exportieren, erstellen und Bereitstellen der app.</span><span class="sxs-lookup"><span data-stu-id="0b728-292">Export, build and deploy the app.</span></span>
* <span data-ttu-id="0b728-293">Nachdem Sie nun das Spiel an einem bestimmten Speicherort zu platzieren, indem es gazing können soll, verwenden Sie die Option Aktion (**ein** oder die LEERTASTE) und klicken Sie dann an einen neuen Speicherort verschieben und die Select-Geste erneut zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="0b728-293">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture (**A** or Spacebar) and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="the-end"></a><span data-ttu-id="0b728-294">Das Ende</span><span class="sxs-lookup"><span data-stu-id="0b728-294">The end</span></span>

<span data-ttu-id="0b728-295">Und das Ende dieses Tutorials ist!</span><span class="sxs-lookup"><span data-stu-id="0b728-295">And that's the end of this tutorial!</span></span>

<span data-ttu-id="0b728-296">Sie haben Folgendes gelernt:</span><span class="sxs-lookup"><span data-stu-id="0b728-296">You learned:</span></span>

* <span data-ttu-id="0b728-297">Vorgehensweise: erstellen eine app holographic in Unity.</span><span class="sxs-lookup"><span data-stu-id="0b728-297">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="0b728-298">Wie Sie Blicke, Gesten, Sprach-, Sounds und räumliche Zuordnung verwenden.</span><span class="sxs-lookup"><span data-stu-id="0b728-298">How to make use of gaze, gesture, voice, sounds, and spatial mapping.</span></span>
* <span data-ttu-id="0b728-299">Informationen zum Erstellen und Bereitstellen einer app mithilfe von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b728-299">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="0b728-300">Sie können nun damit beginnen, Ihre eigenen holographic apps erstellen.</span><span class="sxs-lookup"><span data-stu-id="0b728-300">You are now ready to start creating your own holographic apps!</span></span>

## <a name="see-also"></a><span data-ttu-id="0b728-301">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0b728-301">See also</span></span>

* [<span data-ttu-id="0b728-302">MR Basics 101: Vollständige Projekt mit Gerät</span><span class="sxs-lookup"><span data-stu-id="0b728-302">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="0b728-303">Blicke</span><span class="sxs-lookup"><span data-stu-id="0b728-303">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="0b728-304">Gesten</span><span class="sxs-lookup"><span data-stu-id="0b728-304">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="0b728-305">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="0b728-305">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="0b728-306">Räumliche sound</span><span class="sxs-lookup"><span data-stu-id="0b728-306">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="0b728-307">Räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="0b728-307">Spatial mapping</span></span>](spatial-mapping.md)
