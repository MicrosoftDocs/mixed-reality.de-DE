---
title: MR Grundlagen 101 – vollständige Projekt mit Gerät
description: Führen Sie diese Codierung Exemplarische Vorgehensweise mit Unity, Visual Studio und HoloLens zum Erlernen der Grundlagen von Windows Mixed Reality.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: gemischten Windows Mixed Reality, HoloLens, tatsächlich Hologram, Academy, Tutorial
ms.openlocfilehash: 043ffac8f30a4e29586478b5dca6ecccc2b5afd3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593969"
---
>[!NOTE]
><span data-ttu-id="d5340-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="d5340-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="d5340-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="d5340-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="d5340-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d5340-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="d5340-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="d5340-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="d5340-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="d5340-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="d5340-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="d5340-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101-complete-project-with-device"></a><span data-ttu-id="d5340-110">MR Basics 101: Vollständige Projekt mit Gerät</span><span class="sxs-lookup"><span data-stu-id="d5340-110">MR Basics 101: Complete project with device</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

<span data-ttu-id="d5340-111">Dieses Tutorial führt Sie durch ein vollständiges-Projekt, erstellt in Unity, die Windows Mixed Reality-Kernfunktionen auf, einschließlich HoloLens veranschaulicht [bestaunen](gaze.md), [Gesten](gestures.md), [voice-Eingabe](voice-input.md), [räumliche Sound](spatial-sound.md) und [räumliche Zuordnung](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="d5340-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span>

<span data-ttu-id="d5340-112">Das Tutorial dauert etwa eine Stunde bis zum Abschließen.</span><span class="sxs-lookup"><span data-stu-id="d5340-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="d5340-113">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="d5340-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d5340-114">Kurs</span><span class="sxs-lookup"><span data-stu-id="d5340-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="d5340-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d5340-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d5340-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="d5340-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="d5340-117">MR Basics 101: Vollständige Projekt mit Gerät</span><span class="sxs-lookup"><span data-stu-id="d5340-117">MR Basics 101: Complete project with device</span></span></td><td style="text-align: center;"> <span data-ttu-id="d5340-118">✔️</span><span class="sxs-lookup"><span data-stu-id="d5340-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="d5340-119">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="d5340-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="d5340-120">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="d5340-120">Prerequisites</span></span>

* <span data-ttu-id="d5340-121">Ein Windows 10-PCs mit dem richtigen konfiguriert [-Tools installiert](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="d5340-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="d5340-122">Ein Gerät HoloLens [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="d5340-122">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="d5340-123">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="d5340-123">Project files</span></span>

* <span data-ttu-id="d5340-124">Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) vom Projekt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="d5340-124">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="d5340-125"> Ist Unity 2017.2 oder höher erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d5340-125"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="d5340-126">Wenn Sie weitere Unity 5.6-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="d5340-126">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="d5340-127">Wenn Sie weitere Unity 5.5-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="d5340-127">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="d5340-128">Wenn Sie weitere 5.4 von Unity-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="d5340-128">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="d5340-129">Un-Archive die Dateien auf dem Desktop oder andere einfach auf den Speicherort zugreifen.</span><span class="sxs-lookup"><span data-stu-id="d5340-129">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="d5340-130">Behalten Sie den Ordnernamen als **Origami**.</span><span class="sxs-lookup"><span data-stu-id="d5340-130">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="d5340-131">Wenn Sie vor dem Herunterladen, den Quellcode ansehen möchten es [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="d5340-131">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="d5340-132">Kapitel 1: "Holo" world</span><span class="sxs-lookup"><span data-stu-id="d5340-132">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

<span data-ttu-id="d5340-133">In diesem Kapitel wir unser erstes Unity-Projekt und durchlaufen Sie den Build einrichten und Bereitstellen von Prozess.</span><span class="sxs-lookup"><span data-stu-id="d5340-133">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="d5340-134">Ziele</span><span class="sxs-lookup"><span data-stu-id="d5340-134">Objectives</span></span>

* <span data-ttu-id="d5340-135">Richten Sie Unity aus, für die holographic Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="d5340-135">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="d5340-136">Stellen Sie ggf. ein Hologramm.</span><span class="sxs-lookup"><span data-stu-id="d5340-136">Make a hologram.</span></span>
* <span data-ttu-id="d5340-137">Finden Sie ggf. ein Hologramm, die Sie vorgenommen.</span><span class="sxs-lookup"><span data-stu-id="d5340-137">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="d5340-138">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="d5340-138">Instructions</span></span>

* <span data-ttu-id="d5340-139">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="d5340-139">Start Unity.</span></span>
* <span data-ttu-id="d5340-140">Wählen Sie **öffnen**.</span><span class="sxs-lookup"><span data-stu-id="d5340-140">Select **Open**.</span></span>
* <span data-ttu-id="d5340-141">Geben Sie den Speicherort als dem **Origami** Ordner Sie zuvor nicht archiviert.</span><span class="sxs-lookup"><span data-stu-id="d5340-141">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="d5340-142">Wählen Sie **Origami** , und klicken Sie auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="d5340-142">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="d5340-143">Da die **Origami** Projekt enthält keine Szene, speichern Sie die Szene leere standardmäßig eine neue Datei mit: **Datei** / **Szene speichern unter**.</span><span class="sxs-lookup"><span data-stu-id="d5340-143">Since the **Origami** project does not contain a scene, save the empty default scene to a new file using: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="d5340-144">Benennen Sie die neue Szene **Origami** , und drücken Sie die **speichern** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="d5340-144">Name the new scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-virtual-camera"></a><span data-ttu-id="d5340-145">Einrichten der virtuellen Hauptkamera</span><span class="sxs-lookup"><span data-stu-id="d5340-145">Setup the main virtual camera</span></span>

* <span data-ttu-id="d5340-146">In der **Hierarchie Bereich**Option **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="d5340-146">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="d5340-147">In der **Inspektor** positionieren Sie die Transformation **0,0,0**.</span><span class="sxs-lookup"><span data-stu-id="d5340-147">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="d5340-148">Suchen der **löschen Flags** -Eigenschaft, und ändern die Dropdownliste aus **Skybox** zu **Volltonfarbe**.</span><span class="sxs-lookup"><span data-stu-id="d5340-148">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="d5340-149">Klicken Sie auf die **Hintergrund** Feld, um ein Farbwähler zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="d5340-149">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="d5340-150">Legen Sie **R, G, B und A** zu **0**.</span><span class="sxs-lookup"><span data-stu-id="d5340-150">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="d5340-151">Einrichten der Szene</span><span class="sxs-lookup"><span data-stu-id="d5340-151">Setup the scene</span></span>

* <span data-ttu-id="d5340-152">In der **Hierarchie Bereich**, klicken Sie auf **erstellen** und **leere erstellen**.</span><span class="sxs-lookup"><span data-stu-id="d5340-152">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="d5340-153">Mit der rechten Maustaste den neuen **"gameobject"** und "Umbenennen" auswählen.</span><span class="sxs-lookup"><span data-stu-id="d5340-153">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="d5340-154">Benennen Sie das "gameobject" zu **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="d5340-154">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="d5340-155">Von der **Hologramme** Ordner im Projektfenster (Erweitern Sie die Ressourcen und Hologramme wählen oder doppelklicken klicken Sie auf den Ordner Hologramme im Projektfenster):</span><span class="sxs-lookup"><span data-stu-id="d5340-155">From the **Holograms** folder in the Project Panel (expand Assets and select Holograms or double click the Holograms folder in the Project Panel):</span></span>
  * <span data-ttu-id="d5340-156">Ziehen Sie **Phase** in die Hierarchie ein untergeordnetes Element des **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="d5340-156">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="d5340-157">Ziehen Sie **Sphere1** in die Hierarchie ein untergeordnetes Element des **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="d5340-157">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="d5340-158">Ziehen Sie **Sphere2** in die Hierarchie ein untergeordnetes Element des **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="d5340-158">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="d5340-159">Mit der rechten Maustaste die **gerichtetes Licht** -Objekt in der **Hierarchie Bereich** , und wählen Sie **löschen**.</span><span class="sxs-lookup"><span data-stu-id="d5340-159">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="d5340-160">Von der **Hologramme** Ordner, ziehen Sie **Lichter** in das Stammverzeichnis der **Hierarchie Bereich**.</span><span class="sxs-lookup"><span data-stu-id="d5340-160">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="d5340-161">In der **Hierarchie**, wählen die **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="d5340-161">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="d5340-162">In der **Inspektor**, positionieren Sie die Transformation **0, Verschiebung von -0,5 und 2.0**.</span><span class="sxs-lookup"><span data-stu-id="d5340-162">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="d5340-163">Drücken Sie die **spielen** -Schaltfläche in Unity, um Ihre Hologramme der Vorschau anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d5340-163">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="d5340-164">Daraufhin sollte die Origami-Objekte im Vorschaufenster.</span><span class="sxs-lookup"><span data-stu-id="d5340-164">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="d5340-165">Drücken Sie **spielen** ein zweites Mal im Vorschaumodus zu beenden.</span><span class="sxs-lookup"><span data-stu-id="d5340-165">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="d5340-166">Exportieren Sie das Projekt aus Unity in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d5340-166">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="d5340-167">Im Unity-Option **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="d5340-167">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="d5340-168">Wählen Sie **universelle Windows-Plattform** in die **Plattform** aus, und klicken Sie auf **Plattform wechseln**.</span><span class="sxs-lookup"><span data-stu-id="d5340-168">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="d5340-169">Legen Sie **SDK** zu **universelle 10** und **Buildtyp** zu **D3D**.</span><span class="sxs-lookup"><span data-stu-id="d5340-169">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="d5340-170">Überprüfen Sie **Unity C# Projekte**.</span><span class="sxs-lookup"><span data-stu-id="d5340-170">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="d5340-171">Klicken Sie auf **öffnen Szenen hinzufügen** die Szene hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="d5340-171">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="d5340-172">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="d5340-172">Click **Build**.</span></span>
* <span data-ttu-id="d5340-173">Erstellen Sie in dem Datei-Explorer-Fenster, das angezeigt wird, eine **neuer Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="d5340-173">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="d5340-174">Mausklick die **App-Ordner**.</span><span class="sxs-lookup"><span data-stu-id="d5340-174">Single click the **App Folder**.</span></span>
* <span data-ttu-id="d5340-175">Drücken Sie **wählen Sie Ordner**.</span><span class="sxs-lookup"><span data-stu-id="d5340-175">Press **Select Folder**.</span></span>
* <span data-ttu-id="d5340-176">Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d5340-176">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="d5340-177">Öffnen der **App** Ordner.</span><span class="sxs-lookup"><span data-stu-id="d5340-177">Open the **App** folder.</span></span>
* <span data-ttu-id="d5340-178">(Doppelklicken Sie hier)-Open **Origami.sln**.</span><span class="sxs-lookup"><span data-stu-id="d5340-178">Open (double click) **Origami.sln**.</span></span>
* <span data-ttu-id="d5340-179">Verwenden obere auf der Symbolleiste in Visual Studio, ändern Sie das Ziel vom Debugmodus in den **Version** und ARM, **X86**.</span><span class="sxs-lookup"><span data-stu-id="d5340-179">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="d5340-180">Klicken Sie auf den Pfeil neben der Schaltfläche ", und wählen **Remotecomputer** über Wi-Fi bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="d5340-180">Click on the arrow next to the Device button, and select **Remote Machine** to deploy over Wi-Fi.</span></span>
  * <span data-ttu-id="d5340-181">Legen Sie die **Adresse** auf den Namen oder die IP-Adresse Ihrer HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d5340-181">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="d5340-182">Wenn Sie Ihre IP-Adresse des Geräts nicht kennen, suchen Sie im **Einstellungen > Netzwerk und Internet > Erweiterte Optionen** , oder bitten Sie Cortana **"Hey Cortana, was Meine IP-Adresse ist?"**</span><span class="sxs-lookup"><span data-stu-id="d5340-182">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
  * <span data-ttu-id="d5340-183">Wenn die HoloLens über USB verbunden ist, können Sie stattdessen auswählen **Gerät** über USB bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="d5340-183">If the HoloLens is attached over USB, you may instead select **Device** to deploy over USB.</span></span>
  * <span data-ttu-id="d5340-184">Lassen Sie die **Authentifizierungsmodus** festgelegt **universelle**.</span><span class="sxs-lookup"><span data-stu-id="d5340-184">Leave the **Authentication Mode** set to **Universal**.</span></span>
  * <span data-ttu-id="d5340-185">Klicken Sie auf **auswählen**</span><span class="sxs-lookup"><span data-stu-id="d5340-185">Click **Select**</span></span>

* <span data-ttu-id="d5340-186">Klicken Sie auf **Debuggen > Starten ohne debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="d5340-186">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="d5340-187">Ist dies beim ersten auf Ihrem Gerät bereitstellen, Sie müssen [verbinden Sie es mit Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).</span><span class="sxs-lookup"><span data-stu-id="d5340-187">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).</span></span>

* <span data-ttu-id="d5340-188">Das Origami Projekt jetzt erstellen, bereitstellen, um Ihre HoloLens, und führen Sie dann.</span><span class="sxs-lookup"><span data-stu-id="d5340-188">The Origami project will now build, deploy to your HoloLens, and then run.</span></span>
* <span data-ttu-id="d5340-189">Legen Sie auf Ihre HoloLens, und suchen Sie auf Ihre neuen Hologramme finden Sie unter.</span><span class="sxs-lookup"><span data-stu-id="d5340-189">Put on your HoloLens and look around to see your new holograms.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="d5340-190">Kapitel 2: Blicke</span><span class="sxs-lookup"><span data-stu-id="d5340-190">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

<span data-ttu-id="d5340-191">In diesem Kapitel werden wir zum Einfügen des ersten der drei Methoden zur Interaktion mit Ihrem Hologramme: [bestaunen](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="d5340-191">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="d5340-192">Ziele</span><span class="sxs-lookup"><span data-stu-id="d5340-192">Objectives</span></span>

* <span data-ttu-id="d5340-193">Visualisieren Sie Ihre Blicke mithilfe eines Cursors Welt gesperrt.</span><span class="sxs-lookup"><span data-stu-id="d5340-193">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="d5340-194">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="d5340-194">Instructions</span></span>

* <span data-ttu-id="d5340-195">Wechseln Sie zurück zu Ihrem Unity-Projekt, und schließen Sie das Fenster "erstellen" aus, wenn es noch geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="d5340-195">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="d5340-196">Wählen Sie die **Hologramme** Ordner in der **Projektfenster**.</span><span class="sxs-lookup"><span data-stu-id="d5340-196">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="d5340-197">Ziehen Sie die **Cursor** -Objekt in der **Hierarchie Bereich** auf der Stammebene.</span><span class="sxs-lookup"><span data-stu-id="d5340-197">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="d5340-198">Doppelklicken Sie auf die **Cursor** Objekt, das ein genauer ansehen.</span><span class="sxs-lookup"><span data-stu-id="d5340-198">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="d5340-199">Mit der rechten Maustaste auf die **Skripts** Ordner im Projektfenster.</span><span class="sxs-lookup"><span data-stu-id="d5340-199">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="d5340-200">Klicken Sie auf die **erstellen** Untermenü.</span><span class="sxs-lookup"><span data-stu-id="d5340-200">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="d5340-201">Wählen Sie  **C# Skript**.</span><span class="sxs-lookup"><span data-stu-id="d5340-201">Select **C# Script**.</span></span>
* <span data-ttu-id="d5340-202">Nennen Sie das Skript **WorldCursor**.</span><span class="sxs-lookup"><span data-stu-id="d5340-202">Name the script **WorldCursor**.</span></span> <span data-ttu-id="d5340-203">Hinweis: Beim Namen wird Groß- und Kleinschreibung beachtet.</span><span class="sxs-lookup"><span data-stu-id="d5340-203">Note: The name is case-sensitive.</span></span> <span data-ttu-id="d5340-204">Sie müssen sich nicht um die Erweiterung .cs hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="d5340-204">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="d5340-205">Wählen Sie die **Cursor** -Objekt in der **Hierarchie Bereich**.</span><span class="sxs-lookup"><span data-stu-id="d5340-205">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="d5340-206">Drag & drop die **WorldCursor** Skript in die **Inspektor Bereich**.</span><span class="sxs-lookup"><span data-stu-id="d5340-206">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="d5340-207">Doppelklicken Sie auf die **WorldCursor** Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="d5340-207">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="d5340-208">Kopieren Sie diesen Code in **WorldCursor.cs** und **Alles speichern**.</span><span class="sxs-lookup"><span data-stu-id="d5340-208">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

            // Move the cursor to the point where the raycast hit.
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

* <span data-ttu-id="d5340-209">Erstellen Sie die app neu **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="d5340-209">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="d5340-210">Zurück zu Visual Studio-Projektmappe zuvor verwendet, um auf Ihre HoloLens bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="d5340-210">Return to the Visual Studio solution previously used to deploy to your HoloLens.</span></span>
* <span data-ttu-id="d5340-211">Wählen Sie "Alles neu laden" Wenn Sie aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="d5340-211">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="d5340-212">Klicken Sie auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="d5340-212">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="d5340-213">Jetzt sehen Sie in der Szene, und beachten Sie, wie der Cursor die Form der Objekte interagiert.</span><span class="sxs-lookup"><span data-stu-id="d5340-213">Now look around the scene and notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="d5340-214">Kapitel 3 - Gesten</span><span class="sxs-lookup"><span data-stu-id="d5340-214">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

<span data-ttu-id="d5340-215">In diesem Kapitel werden wir fügen Unterstützung für [Gesten](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="d5340-215">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="d5340-216">Wenn der Benutzer eine Dokument Kugel auswählt, erstellen wir die Kugel liegen, indem die Schwerkraft mithilfe von Unity Physik-Engine aktivieren.</span><span class="sxs-lookup"><span data-stu-id="d5340-216">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="d5340-217">Ziele</span><span class="sxs-lookup"><span data-stu-id="d5340-217">Objectives</span></span>

* <span data-ttu-id="d5340-218">Steuern Sie Ihre Hologramme mit dieser Option Bewegung.</span><span class="sxs-lookup"><span data-stu-id="d5340-218">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="d5340-219">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="d5340-219">Instructions</span></span>

<span data-ttu-id="d5340-220">Wir beginnen mit dem Erstellen eines Skripts und kann die Option Bewegung erkennen.</span><span class="sxs-lookup"><span data-stu-id="d5340-220">We'll start by creating a script then can detect the Select gesture.</span></span>

* <span data-ttu-id="d5340-221">In der **Skripts** Ordner, erstellen Sie ein Skript, mit dem Namen **GazeGestureManager**.</span><span class="sxs-lookup"><span data-stu-id="d5340-221">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="d5340-222">Ziehen Sie die **GazeGestureManager** Skript auf die **OrigamiCollection** Objekt in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="d5340-222">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="d5340-223">Öffnen der **GazeGestureManager** Skript im Visual Studio, und fügen Sie den folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="d5340-223">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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
    void Awake()
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

* <span data-ttu-id="d5340-224">Erstellen Sie ein weiteres Skript im Ordner "Scripts", dieses Mal mit dem Namen **SphereCommands**.</span><span class="sxs-lookup"><span data-stu-id="d5340-224">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="d5340-225">Erweitern Sie die **OrigamiCollection** Objekt in der Hierarchie angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d5340-225">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="d5340-226">Ziehen Sie die **SphereCommands** Skript auf die **Sphere1** Objekt in der Hierarchie-Bereich.</span><span class="sxs-lookup"><span data-stu-id="d5340-226">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="d5340-227">Ziehen Sie die **SphereCommands** Skript auf die **Sphere2** Objekt in der Hierarchie-Bereich.</span><span class="sxs-lookup"><span data-stu-id="d5340-227">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="d5340-228">Öffnen Sie das Skript zur Bearbeitung in Visual Studio, und Ersetzen Sie den Standardcode durch dies:</span><span class="sxs-lookup"><span data-stu-id="d5340-228">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="d5340-229">Exportieren, erstellen und Bereitstellen der app in Ihrem HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d5340-229">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="d5340-230">Suchen Sie auf die Kugeln.</span><span class="sxs-lookup"><span data-stu-id="d5340-230">Look at one of the spheres.</span></span>
* <span data-ttu-id="d5340-231">Führen Sie die Option Aktion, und beobachten Sie die Kugel, auf die Oberfläche des folgenden löschen.</span><span class="sxs-lookup"><span data-stu-id="d5340-231">Perform the select gesture and watch the sphere drop onto the surface below.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="d5340-232">Kapitel 4 – Sprache</span><span class="sxs-lookup"><span data-stu-id="d5340-232">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

<span data-ttu-id="d5340-233">In diesem Kapitel werden wir fügen Unterstützung für zwei [Sprachbefehle](voice-input.md): "Zurücksetzen World" um die gelöschten Kugeln an ihrem ursprünglichen Speicherort, und "Drop Kugel" die Kugel fallen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="d5340-233">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to return the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="d5340-234">Ziele</span><span class="sxs-lookup"><span data-stu-id="d5340-234">Objectives</span></span>

* <span data-ttu-id="d5340-235">Fügen Sie Sprachbefehle, die immer lauschen, im Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="d5340-235">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="d5340-236">Erstellen Sie ggf. ein Hologramm, die auf einen Sprachbefehl reagiert.</span><span class="sxs-lookup"><span data-stu-id="d5340-236">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="d5340-237">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="d5340-237">Instructions</span></span>

* <span data-ttu-id="d5340-238">In der **Skripts** Ordner, erstellen Sie ein Skript, mit dem Namen **SpeechManager**.</span><span class="sxs-lookup"><span data-stu-id="d5340-238">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="d5340-239">Ziehen Sie die **SpeechManager** Skript auf die **OrigamiCollection** Objekt in der Hierarchie</span><span class="sxs-lookup"><span data-stu-id="d5340-239">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="d5340-240">Öffnen der **SpeechManager** Skripts in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d5340-240">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="d5340-241">Kopieren Sie diesen Code in **SpeechManager.cs** und **Alles speichern**:</span><span class="sxs-lookup"><span data-stu-id="d5340-241">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="d5340-242">Öffnen der **SphereCommands** Skripts in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d5340-242">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="d5340-243">Aktualisieren Sie das Skript wie folgt:</span><span class="sxs-lookup"><span data-stu-id="d5340-243">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="d5340-244">Exportieren, erstellen und Bereitstellen der app in Ihrem HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d5340-244">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="d5340-245">Suchen Sie auf die Kugeln und sagen Sie "**löschen Kugel**".</span><span class="sxs-lookup"><span data-stu-id="d5340-245">Look at one of the spheres, and say "**Drop Sphere**".</span></span>
* <span data-ttu-id="d5340-246">Sagen Sie "**zurücksetzen Welt**", die sie wieder in ihre ursprünglichen Positionen verschieben.</span><span class="sxs-lookup"><span data-stu-id="d5340-246">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="d5340-247">Kapitel 5 – räumliche sound</span><span class="sxs-lookup"><span data-stu-id="d5340-247">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

<span data-ttu-id="d5340-248">In diesem Kapitel wir Musik hinzufügen, um die app, und dann Soundeffekten auf bestimmte Aktionen auszulösen.</span><span class="sxs-lookup"><span data-stu-id="d5340-248">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="d5340-249">Wir verwenden [räumliche Sound](spatial-sound.md) Sounds mit einen bestimmten Speicherort im 3D-Raum gewähren.</span><span class="sxs-lookup"><span data-stu-id="d5340-249">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="d5340-250">Ziele</span><span class="sxs-lookup"><span data-stu-id="d5340-250">Objectives</span></span>

* <span data-ttu-id="d5340-251">Hören Sie Hologramme in Ihrer Umgebung.</span><span class="sxs-lookup"><span data-stu-id="d5340-251">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="d5340-252">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="d5340-252">Instructions</span></span>

* <span data-ttu-id="d5340-253">Im Unity-Option in der oberen Menüleiste **Bearbeiten > Projekteinstellungen > Audio**</span><span class="sxs-lookup"><span data-stu-id="d5340-253">In Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="d5340-254">Finden Sie im Bereich-Inspektor auf der rechten Seite der **Spatializer-Plug-Ins** festlegen, und wählen **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="d5340-254">In the Inspector Panel on the right side, find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="d5340-255">Von der **Hologramme** Ordner im Projektfenster, ziehen Sie die **Umgebung** -Objekt auf den **OrigamiCollection** Objekt in der Hierarchie-Bereich.</span><span class="sxs-lookup"><span data-stu-id="d5340-255">From the **Holograms** folder in the Project panel, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="d5340-256">Wählen Sie **OrigamiCollection** und suchen Sie die **Audio Source** -Komponente in den Bereich der Eigenschaftenanalyse.</span><span class="sxs-lookup"><span data-stu-id="d5340-256">Select **OrigamiCollection** and find the **Audio Source** component in the Inspector panel.</span></span> <span data-ttu-id="d5340-257">Ändern Sie diese Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="d5340-257">Change these properties:</span></span>
  * <span data-ttu-id="d5340-258">Überprüfen Sie die **Spatialize** Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="d5340-258">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="d5340-259">Überprüfen Sie die **auf aktiv wiedergeben**.</span><span class="sxs-lookup"><span data-stu-id="d5340-259">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="d5340-260">Änderung **räumliche Blend** zu **3D** durch den Schieberegler ganz nach rechts ziehen.</span><span class="sxs-lookup"><span data-stu-id="d5340-260">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span> <span data-ttu-id="d5340-261">Wenn Sie den Schieberegler verschieben, sollten den Wert von 0 auf 1 ändern.</span><span class="sxs-lookup"><span data-stu-id="d5340-261">The value should change from 0 to 1 when you move the slider.</span></span>
  * <span data-ttu-id="d5340-262">Überprüfen Sie die **Schleife** Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="d5340-262">Check the **Loop** property.</span></span>
  * <span data-ttu-id="d5340-263">Erweitern Sie **3D Sound Einstellungen**, und geben Sie **0,1** für **Doppler Ebene**.</span><span class="sxs-lookup"><span data-stu-id="d5340-263">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="d5340-264">Legen Sie **Volume Rolloff** zu **logarithmische Rolloff**.</span><span class="sxs-lookup"><span data-stu-id="d5340-264">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="d5340-265">Legen Sie **maximaler Abstand** zu **20**.</span><span class="sxs-lookup"><span data-stu-id="d5340-265">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="d5340-266">In der **Skripts** Ordner, erstellen Sie ein Skript, mit dem Namen **SphereSounds**.</span><span class="sxs-lookup"><span data-stu-id="d5340-266">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="d5340-267">Drag & drop **SphereSounds** auf die **Sphere1** und **Sphere2** Objekte in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="d5340-267">Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="d5340-268">Open **SphereSounds** aktualisieren Sie den folgenden Code in Visual Studio und **Alles speichern**.</span><span class="sxs-lookup"><span data-stu-id="d5340-268">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="d5340-269">Speichern Sie das Skript aus, und zurück zu Unity.</span><span class="sxs-lookup"><span data-stu-id="d5340-269">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="d5340-270">Exportieren, erstellen und Bereitstellen der app in Ihrem HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d5340-270">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="d5340-271">Verschieben Sie näher und weiter von der Stufe aus, und aktivieren Sie, paralleler, hören den Sound zu ändern.</span><span class="sxs-lookup"><span data-stu-id="d5340-271">Move closer and further from the Stage and turn side-to-side to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="d5340-272">Kapitel 6 – räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="d5340-272">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

<span data-ttu-id="d5340-273">Nun verwenden wir [räumliche Zuordnung](spatial-mapping.md) ein wirkliches Objekt in der realen Welt die Spielfläche zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="d5340-273">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="d5340-274">Ziele</span><span class="sxs-lookup"><span data-stu-id="d5340-274">Objectives</span></span>

* <span data-ttu-id="d5340-275">Bringen Sie Ihre realen, in der virtuellen Welt.</span><span class="sxs-lookup"><span data-stu-id="d5340-275">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="d5340-276">Platzieren Sie Ihre Hologramme, wo sie sind die meisten für Sie.</span><span class="sxs-lookup"><span data-stu-id="d5340-276">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="d5340-277">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="d5340-277">Instructions</span></span>

* <span data-ttu-id="d5340-278">Klicken Sie in Unity, auf die **Hologramme** Ordner im Projektfenster.</span><span class="sxs-lookup"><span data-stu-id="d5340-278">In Unity, click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="d5340-279">Ziehen Sie die **räumliche Zuordnung** Asset in das Stammverzeichnis der **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="d5340-279">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="d5340-280">Klicken Sie auf die **räumliche Zuordnung** Objekt in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="d5340-280">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="d5340-281">In der **Inspektor Bereich**, ändern Sie die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="d5340-281">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="d5340-282">Überprüfen Sie die **zeichnen Visual Gitter** Feld.</span><span class="sxs-lookup"><span data-stu-id="d5340-282">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="d5340-283">Suchen Sie **zeichnen Material** , und klicken Sie auf den Kreis auf der rechten Seite.</span><span class="sxs-lookup"><span data-stu-id="d5340-283">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="d5340-284">Typ "**Drahtmodell**" in das Suchfeld oben.</span><span class="sxs-lookup"><span data-stu-id="d5340-284">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="d5340-285">Klicken Sie auf das Ergebnis, und klicken Sie dann schließen Sie das Fenster.</span><span class="sxs-lookup"><span data-stu-id="d5340-285">Click on the result and then close the window.</span></span> <span data-ttu-id="d5340-286">Wenn Sie dies tun, der Wert für Material zeichnen soll Drahtmodell abrufen oder festlegen.</span><span class="sxs-lookup"><span data-stu-id="d5340-286">When you do this, the value for Draw Material should get set to Wireframe.</span></span>
* <span data-ttu-id="d5340-287">Exportieren, erstellen und Bereitstellen der app in Ihrem HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d5340-287">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="d5340-288">Wenn die app ausgeführt wird, wird ein Drahtmodell-Netz Ihrer realen überlagern.</span><span class="sxs-lookup"><span data-stu-id="d5340-288">When the app runs, a wireframe mesh will overlay your real world.</span></span>
* <span data-ttu-id="d5340-289">Sehen Sie sich, wie eine parallele Kugel die Bühne verließ, und klicken Sie auf dem Boden liegen wird.</span><span class="sxs-lookup"><span data-stu-id="d5340-289">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="d5340-290">Jetzt zeigen wir Ihnen die OrigamiCollection an einem neuen Speicherort zu verschieben:</span><span class="sxs-lookup"><span data-stu-id="d5340-290">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="d5340-291">In der **Skripts** Ordner, erstellen Sie ein Skript, mit dem Namen **TapToPlaceParent**.</span><span class="sxs-lookup"><span data-stu-id="d5340-291">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="d5340-292">In der **Hierarchie**, erweitern Sie die **OrigamiCollection** , und wählen Sie die **Phase** Objekt.</span><span class="sxs-lookup"><span data-stu-id="d5340-292">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="d5340-293">Ziehen Sie die **TapToPlaceParent** -Skript auf die Stage-Objekt.</span><span class="sxs-lookup"><span data-stu-id="d5340-293">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="d5340-294">Öffnen der **TapToPlaceParent** Skript im Visual Studio, und aktualisieren, um folgende sein:</span><span class="sxs-lookup"><span data-stu-id="d5340-294">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="d5340-295">Exportieren, erstellen und Bereitstellen der app.</span><span class="sxs-lookup"><span data-stu-id="d5340-295">Export, build and deploy the app.</span></span>
* <span data-ttu-id="d5340-296">Jetzt sollten Sie jetzt das Spiel an einem bestimmten Speicherort zu platzieren, indem Sie darauf gazing, verwenden die Option Aktion und klicken Sie dann an einem neuen Speicherort verschieben und die Select-Geste erneut zu verwenden können.</span><span class="sxs-lookup"><span data-stu-id="d5340-296">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="chapter-7---holographic-fun"></a><span data-ttu-id="d5340-297">Kapitel 7: Holografischen Spaß</span><span class="sxs-lookup"><span data-stu-id="d5340-297">Chapter 7 - Holographic fun</span></span>

### <a name="objectives"></a><span data-ttu-id="d5340-298">Ziele</span><span class="sxs-lookup"><span data-stu-id="d5340-298">Objectives</span></span>

* <span data-ttu-id="d5340-299">Zeigen Sie auf eine holographic Underworld "entrance".</span><span class="sxs-lookup"><span data-stu-id="d5340-299">Reveal the entrance to a holographic underworld.</span></span>

### <a name="instructions"></a><span data-ttu-id="d5340-300">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="d5340-300">Instructions</span></span>

<span data-ttu-id="d5340-301">Jetzt zeigen wir Ihnen wie die holographic Underworld entdecken:</span><span class="sxs-lookup"><span data-stu-id="d5340-301">Now we'll show you how to uncover the holographic underworld:</span></span>

* <span data-ttu-id="d5340-302">Von der **Hologramme** Ordner im Projektfenster:</span><span class="sxs-lookup"><span data-stu-id="d5340-302">From the **Holograms** folder in the Project Panel:</span></span>
  * <span data-ttu-id="d5340-303">Ziehen Sie **Underworld** in die Hierarchie ein untergeordnetes Element des **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="d5340-303">Drag **Underworld** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="d5340-304">In der **Skripts** Ordner, erstellen Sie ein Skript, mit dem Namen **HitTarget**.</span><span class="sxs-lookup"><span data-stu-id="d5340-304">In the **Scripts** folder, create a script named **HitTarget**.</span></span>
* <span data-ttu-id="d5340-305">In der **Hierarchie**, erweitern Sie die **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="d5340-305">In the **Hierarchy**, expand the **OrigamiCollection**.</span></span>
* <span data-ttu-id="d5340-306">Erweitern Sie die **Phase** Objekt aus, und wählen Sie die **Ziel** Objekt (blaue Lüfter).</span><span class="sxs-lookup"><span data-stu-id="d5340-306">Expand the **Stage** object and select the **Target** object (blue fan).</span></span>
* <span data-ttu-id="d5340-307">Ziehen Sie die **HitTarget** Skript auf die **Ziel** Objekt.</span><span class="sxs-lookup"><span data-stu-id="d5340-307">Drag the **HitTarget** script onto the **Target** object.</span></span>
* <span data-ttu-id="d5340-308">Öffnen der **HitTarget** Skript im Visual Studio, und aktualisieren, um folgende sein:</span><span class="sxs-lookup"><span data-stu-id="d5340-308">Open the **HitTarget** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* <span data-ttu-id="d5340-309">Wählen Sie in Unity die **Ziel** Objekt.</span><span class="sxs-lookup"><span data-stu-id="d5340-309">In Unity, select the **Target** object.</span></span>
* <span data-ttu-id="d5340-310">Zwei öffentliche Eigenschaften werden nun angezeigt, auf die **Ziel erreicht** Komponente und Reference-Objekte in unsere Szene müssen:</span><span class="sxs-lookup"><span data-stu-id="d5340-310">Two public properties are now visible on the **Hit Target** component and need to reference objects in our scene:</span></span>
  * <span data-ttu-id="d5340-311">Ziehen Sie **Underworld** aus der **Hierarchie** zur Eigenschaftenansicht der **Underworld** Eigenschaft für die **Ziel erreicht** Komponente.</span><span class="sxs-lookup"><span data-stu-id="d5340-311">Drag **Underworld** from the **Hierarchy** panel to the **Underworld** property on the **Hit Target** component.</span></span>
  * <span data-ttu-id="d5340-312">Ziehen Sie **Phase** aus der **Hierarchie** zum Bereich der **Objekt zum Ausblenden von** Eigenschaft für die **Ziel erreicht** Komponente.</span><span class="sxs-lookup"><span data-stu-id="d5340-312">Drag **Stage** from the **Hierarchy** panel to the **Object to Hide** property on the **Hit Target** component.</span></span>
* <span data-ttu-id="d5340-313">Exportieren, erstellen und Bereitstellen der app.</span><span class="sxs-lookup"><span data-stu-id="d5340-313">Export, build and deploy the app.</span></span>
* <span data-ttu-id="d5340-314">Platzieren Sie die Origami-Auflistung, auf dem Boden, und klicken Sie dann verwenden Sie die Option Aktion, um eine Kugel löschen zu machen.</span><span class="sxs-lookup"><span data-stu-id="d5340-314">Place the Origami Collection on the floor, and then use the Select gesture to make a sphere drop.</span></span>
* <span data-ttu-id="d5340-315">Wenn die Kugel das Ziel (blaue Lüfter) erreicht, erfolgt eine Explosion.</span><span class="sxs-lookup"><span data-stu-id="d5340-315">When the sphere hits the target (blue fan), an explosion will occur.</span></span> <span data-ttu-id="d5340-316">Die Auflistung wird ausgeblendet, und eine Lücke, die Underworld angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d5340-316">The collection will be hidden and a hole to the underworld will appear.</span></span>

## <a name="the-end"></a><span data-ttu-id="d5340-317">Das Ende</span><span class="sxs-lookup"><span data-stu-id="d5340-317">The end</span></span>

<span data-ttu-id="d5340-318">Und das Ende dieses Tutorials ist!</span><span class="sxs-lookup"><span data-stu-id="d5340-318">And that's the end of this tutorial!</span></span>

<span data-ttu-id="d5340-319">Sie haben Folgendes gelernt:</span><span class="sxs-lookup"><span data-stu-id="d5340-319">You learned:</span></span>

* <span data-ttu-id="d5340-320">Vorgehensweise: erstellen eine app holographic in Unity.</span><span class="sxs-lookup"><span data-stu-id="d5340-320">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="d5340-321">Wie Sie mithilfe der Blicke, Gesten, Sprach-, Sound, und die räumliche Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="d5340-321">How to make use of gaze, gesture, voice, sound, and spatial mapping.</span></span>
* <span data-ttu-id="d5340-322">Informationen zum Erstellen und Bereitstellen einer app mithilfe von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d5340-322">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="d5340-323">Sie können nun damit beginnen, Ihre eigenen holografischen Benutzeroberfläche erstellen.</span><span class="sxs-lookup"><span data-stu-id="d5340-323">You are now ready to start creating your own holographic experience!</span></span>

## <a name="see-also"></a><span data-ttu-id="d5340-324">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d5340-324">See also</span></span>

* [<span data-ttu-id="d5340-325">MR Basics 101E: Vollständige Projekt mit dem emulator</span><span class="sxs-lookup"><span data-stu-id="d5340-325">MR Basics 101E: Complete project with emulator</span></span>](holograms-101e.md)
* [<span data-ttu-id="d5340-326">Blicke</span><span class="sxs-lookup"><span data-stu-id="d5340-326">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="d5340-327">Gesten</span><span class="sxs-lookup"><span data-stu-id="d5340-327">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="d5340-328">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="d5340-328">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="d5340-329">Räumliche sound</span><span class="sxs-lookup"><span data-stu-id="d5340-329">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="d5340-330">Räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="d5340-330">Spatial mapping</span></span>](spatial-mapping.md)
