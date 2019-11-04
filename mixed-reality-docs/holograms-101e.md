---
title: Grundlagen 101 e-Complete Project with Emulator
description: Befolgen Sie diese exemplarische Vorgehensweise, indem Sie Unity, Visual Studio und den hololens-Emulator verwenden, um die Grundlagen einer Holographic-Anwendung kennenzulernen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Gemischte Realität, Windows Mixed Reality, hololens, Hologram, Academy, Tutorial, Emulator
ms.openlocfilehash: b1d8e1f3f272051bdd6f69ab88c3aef4f86f13ef
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434704"
---
>[!NOTE]
><span data-ttu-id="8d5a7-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="8d5a7-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="8d5a7-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="8d5a7-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="8d5a7-108">Es wurde [eine neue Reihe von Tutorials](mrlearning-base.md) für hololens 2 gepostet.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a><span data-ttu-id="8d5a7-109">Grundlagen 101 e: vervollständigen eines Projekts mit Emulator</span><span class="sxs-lookup"><span data-stu-id="8d5a7-109">MR Basics 101E: Complete project with emulator</span></span>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

<span data-ttu-id="8d5a7-110">In diesem Tutorial werden Sie durch ein vollständiges Projekt geführt, das in Unity integriert ist, das grundlegende Windows Mixed Reality-Features in hololens veranschaulicht, einschließlich [Blick](gaze-and-commit.md), [Gesten](gaze-and-commit.md#composite-gestures), [Spracheingabe](voice-input.md), [räumlichem Sound](spatial-sound.md) und [räumlicher Zuordnung](spatial-mapping.md) . .</span><span class="sxs-lookup"><span data-stu-id="8d5a7-110">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze-and-commit.md), [gestures](gaze-and-commit.md#composite-gestures), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span> <span data-ttu-id="8d5a7-111">Das Tutorial dauert ungefähr 1 Stunde.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-111">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="8d5a7-112">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="8d5a7-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="8d5a7-113">Natürlich</span><span class="sxs-lookup"><span data-stu-id="8d5a7-113">Course</span></span></th><th style="width:150px"> <span data-ttu-id="8d5a7-114"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8d5a7-114"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8d5a7-115"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="8d5a7-115"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="8d5a7-116">Grundlagen 101 e: vervollständigen eines Projekts mit Emulator</span><span class="sxs-lookup"><span data-stu-id="8d5a7-116">MR Basics 101E: Complete project with emulator</span></span></td><td style="text-align: center;"> <span data-ttu-id="8d5a7-117">✔️</span><span class="sxs-lookup"><span data-stu-id="8d5a7-117">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="8d5a7-118">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="8d5a7-118">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="8d5a7-119">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="8d5a7-119">Prerequisites</span></span>

* <span data-ttu-id="8d5a7-120">Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md)konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-120">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

### <a name="project-files"></a><span data-ttu-id="8d5a7-121">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="8d5a7-121">Project files</span></span>

* <span data-ttu-id="8d5a7-122">Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) , die für das Projekt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-122">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="8d5a7-123"> Erfordert Unity 2017,2 oder höher.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-123"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="8d5a7-124">Wenn Sie weiterhin Unity 5,6-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="8d5a7-124">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="8d5a7-125">Wenn Sie weiterhin Unity 5,5-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="8d5a7-125">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="8d5a7-126">Wenn Sie weiterhin Unity 5,4-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="8d5a7-126">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="8d5a7-127">Deinstallieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht zugänglichen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-127">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="8d5a7-128">Behalten Sie den Ordnernamen **Origami**bei.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-128">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="8d5a7-129">Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="8d5a7-129">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="8d5a7-130">Kapitel 1: "Holo" World</span><span class="sxs-lookup"><span data-stu-id="8d5a7-130">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

<span data-ttu-id="8d5a7-131">In diesem Kapitel richten wir das erste Unity-Projekt ein und durchlaufen den Build-und Bereitstellungs Prozess.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-131">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="8d5a7-132">Ziele</span><span class="sxs-lookup"><span data-stu-id="8d5a7-132">Objectives</span></span>

* <span data-ttu-id="8d5a7-133">Einrichten von Unity für die Holographic-Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-133">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="8d5a7-134">Erstellen Sie ein Hologram.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-134">Make a hologram.</span></span>
* <span data-ttu-id="8d5a7-135">Sehen Sie sich ein von Ihnen vorgenommene – Hologramm an.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-135">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="8d5a7-136">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="8d5a7-136">Instructions</span></span>

* <span data-ttu-id="8d5a7-137">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-137">Start Unity.</span></span>
* <span data-ttu-id="8d5a7-138">Wählen Sie **Öffnen**aus.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-138">Select **Open**.</span></span>
* <span data-ttu-id="8d5a7-139">Geben Sie Location als den Ordner **Origami** ein, den Sie zuvor nicht archiviert haben.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-139">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="8d5a7-140">Wählen Sie **Origami** , und klicken Sie auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-140">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="8d5a7-141">Speichern Sie die neue Szene: **File** / **Szene speichern**unter.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-141">Save the new scene: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="8d5a7-142">Nennen Sie die Szene **Origami** , und klicken Sie auf die Schaltfläche **Speichern** .</span><span class="sxs-lookup"><span data-stu-id="8d5a7-142">Name the scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-camera"></a><span data-ttu-id="8d5a7-143">Einrichten der Hauptkamera</span><span class="sxs-lookup"><span data-stu-id="8d5a7-143">Setup the main camera</span></span>

* <span data-ttu-id="8d5a7-144">Wählen Sie im Bereich **Hierarchie**die Option **Hauptkamera**aus.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-144">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="8d5a7-145">Legen Sie im **Inspektor** die Transformations Position auf **0, 0, 0**fest.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-145">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="8d5a7-146">Suchen Sie die Eigenschaft **Clear Flags** , und ändern Sie die Dropdown Liste von **Skybox** in voll **Tonfarbe**.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-146">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="8d5a7-147">Klicken Sie auf das Feld **Hintergrund** , um eine Farbauswahl zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-147">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="8d5a7-148">Legen Sie **R, G, B und A** auf **0**fest.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-148">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="8d5a7-149">Einrichten der Szene</span><span class="sxs-lookup"><span data-stu-id="8d5a7-149">Setup the scene</span></span>

* <span data-ttu-id="8d5a7-150">Klicken Sie im **Hierarchie Panel**auf **Erstellen** , und erstellen Sie eine **leere**.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-150">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="8d5a7-151">Klicken Sie mit der rechten Maustaste auf das neue **gameobject** und wählen Sie umbenennen</span><span class="sxs-lookup"><span data-stu-id="8d5a7-151">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="8d5a7-152">Benennen Sie das gameobject in **origamicollection**um.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-152">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="8d5a7-153">Aus dem Ordner " **holograms** " im **Projekt Panel**:</span><span class="sxs-lookup"><span data-stu-id="8d5a7-153">From the **Holograms** folder in the **Project Panel**:</span></span>
  * <span data-ttu-id="8d5a7-154">Ziehen Sie die **Phase** in die Hierarchie, um ein untergeordnetes Element von **origamicollection**zu sein.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-154">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="8d5a7-155">Ziehen Sie **Sphere1** in die Hierarchie, um ein untergeordnetes Element von **origamicollection**zu sein.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-155">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="8d5a7-156">Ziehen Sie **Sphere2** in die Hierarchie, um ein untergeordnetes Element von **origamicollection**zu sein.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-156">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="8d5a7-157">Klicken Sie im Bereich **Hierarchie** mit der rechten Maustaste auf das Objekt **direktional hell** , und wählen Sie **Löschen**aus</span><span class="sxs-lookup"><span data-stu-id="8d5a7-157">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="8d5a7-158">Ziehen Sie aus dem Ordner **holograms** die **Beleuchtung** in das Stammverzeichnis des Bereichs **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-158">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="8d5a7-159">Wählen Sie in der **Hierarchie**die Option **origamicollection**aus.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-159">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="8d5a7-160">Legen Sie im **Inspektor**die Transformations Position auf **0,-0,5, 2,0**fest.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-160">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="8d5a7-161">Klicken Sie in Unity auf die **Wiedergabe** Schaltfläche, um eine Vorschau der holograms anzuzeigen</span><span class="sxs-lookup"><span data-stu-id="8d5a7-161">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="8d5a7-162">Die Origami-Objekte sollten im Vorschaufenster angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-162">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="8d5a7-163">Drücken **Sie** ein zweites Mal, um den Vorschaumodus zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-163">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="8d5a7-164">Exportieren des Projekts aus Unity in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8d5a7-164">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="8d5a7-165">Wählen Sie in Unity **Datei > Buildeinstellungen**aus.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-165">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="8d5a7-166">Wählen Sie in der Liste **Plattform** den **Windows Store** aus, und klicken Sie auf **Plattform wechseln**.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-166">Select **Windows Store** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="8d5a7-167">Legen Sie das **SDK** auf **Universal 10** und den Buildtyp auf **D3D**fest.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-167">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="8d5a7-168">Überprüfen Sie **Unity C# -Projekte**.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-168">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="8d5a7-169">Klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-169">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="8d5a7-170">Klicken Sie auf **Player Einstellungen...** .</span><span class="sxs-lookup"><span data-stu-id="8d5a7-170">Click **Player Settings...**.</span></span>
* <span data-ttu-id="8d5a7-171">Wählen Sie im Inspektor-Panel das **Windows Store-Logo**aus.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-171">In the Inspector Panel select the **Windows Store logo**.</span></span> <span data-ttu-id="8d5a7-172">Wählen Sie dann **Veröffentlichungs Einstellungen**aus.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-172">Then select **Publishing Settings**.</span></span>
* <span data-ttu-id="8d5a7-173">Wählen Sie im Abschnitt " **Funktionen** " die Funktionen " **Mikrofon** " und " **spatialperception** " aus.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-173">In the **Capabilities** section, select the **Microphone** and **SpatialPerception** capabilities.</span></span>
* <span data-ttu-id="8d5a7-174">Klicken Sie im Fenster "Buildeinstellungen" auf " **Erstellen**".</span><span class="sxs-lookup"><span data-stu-id="8d5a7-174">Back in the Build Settings window, click **Build**.</span></span>
* <span data-ttu-id="8d5a7-175">Erstellen Sie einen **neuen Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="8d5a7-175">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="8d5a7-176">Klicken Sie einfach auf den **app-Ordner**.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-176">Single click the **App Folder**.</span></span>
* <span data-ttu-id="8d5a7-177">Drücken **Sie Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-177">Press **Select Folder**.</span></span>
* <span data-ttu-id="8d5a7-178">Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-178">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="8d5a7-179">Öffnen Sie den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-179">Open the **App** folder.</span></span>
* <span data-ttu-id="8d5a7-180">Öffnen Sie die Visual Studio-Projekt Mappe **Origami**.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-180">Open the **Origami Visual Studio Solution**.</span></span>
* <span data-ttu-id="8d5a7-181">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x86**.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-181">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
  * <span data-ttu-id="8d5a7-182">Klicken Sie auf den Pfeil neben der Schaltfläche Gerät, und wählen Sie **hololens Emulator**aus.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-182">Click on the arrow next to the Device button, and select **HoloLens Emulator**.</span></span>
  * <span data-ttu-id="8d5a7-183">Klicken Sie auf **Debuggen > Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-183">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
  * <span data-ttu-id="8d5a7-184">Nach einiger Zeit wird der Emulator mit dem Origami-Projekt gestartet.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-184">After some time the emulator will start with the Origami project.</span></span> <span data-ttu-id="8d5a7-185">Beim ersten Starten des [Emulators](using-the-hololens-emulator.md)kann es bis zu 15 Minuten dauern, bis der Emulator gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-185">When first launching the [emulator](using-the-hololens-emulator.md), it can take as long as 15 minutes for the emulator to start up.</span></span> <span data-ttu-id="8d5a7-186">Schließen Sie die Datei nach dem Start nicht.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-186">Once it starts, do not close it.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="8d5a7-187">Kapitel 2: Blick</span><span class="sxs-lookup"><span data-stu-id="8d5a7-187">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

<span data-ttu-id="8d5a7-188">In diesem Kapitel werden die ersten von drei Möglichkeiten vorgestellt, mit denen Sie mit ihren holograms interagieren [können.](gaze-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="8d5a7-188">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze-and-commit.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="8d5a7-189">Ziele</span><span class="sxs-lookup"><span data-stu-id="8d5a7-189">Objectives</span></span>

* <span data-ttu-id="8d5a7-190">Visualisieren Sie Ihren Blick mithilfe eines weltweit gesperrten Cursors.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-190">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="8d5a7-191">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="8d5a7-191">Instructions</span></span>

* <span data-ttu-id="8d5a7-192">Wechseln Sie zurück zu Ihrem Unity-Projekt, und schließen Sie das Fenster mit den Buildeinstellungen, wenn es noch geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-192">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="8d5a7-193">Wählen Sie im **Projekt Panel**den Ordner **holograms** aus.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-193">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="8d5a7-194">Ziehen Sie das **Cursor** Objekt in das **Hierarchie Panel** auf der Stamm Ebene.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-194">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="8d5a7-195">Doppelklicken Sie auf das **Cursor** Objekt, um es genauer zu betrachten.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-195">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="8d5a7-196">Klicken Sie im Projekt Panel mit der rechten Maustaste auf den Ordner **Scripts** .</span><span class="sxs-lookup"><span data-stu-id="8d5a7-196">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="8d5a7-197">Klicken Sie auf das Untermenü **Erstellen** .</span><span class="sxs-lookup"><span data-stu-id="8d5a7-197">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="8d5a7-198">Wählen Sie  **C# Skript**aus.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-198">Select **C# Script**.</span></span>
* <span data-ttu-id="8d5a7-199">Nennen Sie das Skript **worldcursor**.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-199">Name the script **WorldCursor**.</span></span> <span data-ttu-id="8d5a7-200">Hinweis: bei dem Namen wird die Groß-/Kleinschreibung beachtet.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-200">Note: The name is case-sensitive.</span></span> <span data-ttu-id="8d5a7-201">Sie müssen die Erweiterung ". cs" nicht hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-201">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="8d5a7-202">Wählen Sie im **Hierarchie Panel**das **Cursor** Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-202">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="8d5a7-203">Verschieben Sie das **worldcursor** -Skript per Drag & amp; Drop in den Bereich **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-203">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="8d5a7-204">Doppelklicken Sie auf das Skript **worldcursor** , um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-204">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="8d5a7-205">Fügen Sie diesen Code in **WorldCursor.cs** ein, und **Speichern Sie alle**.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-205">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

* <span data-ttu-id="8d5a7-206">Erstellen Sie die APP aus dem **Datei > den Buildeinstellungen**neu.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-206">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="8d5a7-207">Kehren Sie zur Visual Studio-Projekt Mappe zurück, die zuvor zur Bereitstellung im Emulator verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-207">Return to the Visual Studio solution previously used to deploy to the emulator.</span></span>
* <span data-ttu-id="8d5a7-208">Wählen Sie bei entsprechender Aufforderung "alle neu laden" aus.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-208">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="8d5a7-209">Klicken Sie auf **Debuggen > Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-209">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="8d5a7-210">Verwenden Sie den Xbox-Controller, um die Szene zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-210">Use the Xbox controller to look around the scene.</span></span> <span data-ttu-id="8d5a7-211">Beachten Sie, wie der Cursor mit der Form von-Objekten interagiert.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-211">Notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="8d5a7-212">Kapitel 3: Gesten</span><span class="sxs-lookup"><span data-stu-id="8d5a7-212">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

<span data-ttu-id="8d5a7-213">In diesem Kapitel wird die Unterstützung für [Gesten](gaze-and-commit.md#composite-gestures)hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-213">In this chapter, we'll add support for [gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="8d5a7-214">Wenn der Benutzer eine Papierkugel auswählt, wird die Kugel durch das Aktivieren der Schwerkraft mit der Physik-Engine von Unity erreicht.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-214">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="8d5a7-215">Ziele</span><span class="sxs-lookup"><span data-stu-id="8d5a7-215">Objectives</span></span>

* <span data-ttu-id="8d5a7-216">Steuern Sie Ihre Hologramme mit der SELECT-Geste.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-216">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="8d5a7-217">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="8d5a7-217">Instructions</span></span>

<span data-ttu-id="8d5a7-218">Wir beginnen mit dem Erstellen eines Skripts, als die SELECT-Geste erkennen zu können.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-218">We'll start by creating a script than can detect the Select gesture.</span></span>

* <span data-ttu-id="8d5a7-219">Erstellen Sie im Ordner **Scripts** ein Skript mit dem Namen " **gazegesturemanager**".</span><span class="sxs-lookup"><span data-stu-id="8d5a7-219">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="8d5a7-220">Ziehen Sie das Skript " **gazegesturemanager** " auf das Objekt " **origamicollection** " in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-220">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="8d5a7-221">Öffnen Sie das Skript " **gazegesturemanager** " in Visual Studio, und fügen Sie den folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="8d5a7-221">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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

* <span data-ttu-id="8d5a7-222">Erstellen Sie ein weiteres Skript im Ordner "Scripts", diesmal mit dem Namen **spherecommands**.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-222">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="8d5a7-223">Erweitern Sie das Objekt **origamicollection** in der Hierarchie Ansicht.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-223">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="8d5a7-224">Ziehen Sie das **spherecommands** -Skript auf das **Sphere1** -Objekt im Hierarchie Panel.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-224">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="8d5a7-225">Ziehen Sie das **spherecommands** -Skript auf das **Sphere2** -Objekt im Hierarchie Panel.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-225">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="8d5a7-226">Öffnen Sie das Skript in Visual Studio zur Bearbeitung, und ersetzen Sie den Standard Code durch den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="8d5a7-226">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="8d5a7-227">Exportieren, erstellen und Bereitstellen der APP auf dem hololens-Emulator.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-227">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="8d5a7-228">Sehen Sie sich die Szene an, und zentrieren Sie eine der Bereiche.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-228">Look around the scene, and center on one of the spheres.</span></span>
* <span data-ttu-id="8d5a7-229">Drücken Sie **die Schaltfläche** auf dem Xbox-Controller, oder drücken Sie die Leertaste, um die Auswahl Bewegung zu simulieren.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-229">Press the **A** button on the Xbox controller or press the Spacebar to simulate the Select gesture.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="8d5a7-230">Kapitel 4: Stimme</span><span class="sxs-lookup"><span data-stu-id="8d5a7-230">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

<span data-ttu-id="8d5a7-231">In diesem Kapitel fügen wir die Unterstützung für zwei [Sprachbefehle](voice-input.md)hinzu: "Reset World", um die gelöschten Bereiche an ihren ursprünglichen Speicherort zurückzugeben, und "Drop Sphere", um die Kugel zu verlieren.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-231">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to returns the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="8d5a7-232">Ziele</span><span class="sxs-lookup"><span data-stu-id="8d5a7-232">Objectives</span></span>

* <span data-ttu-id="8d5a7-233">Fügen Sie Sprachbefehle hinzu, die immer im Hintergrund lauschen.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-233">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="8d5a7-234">Erstellen Sie ein – Hologramm, das auf einen Voice-Befehl reagiert.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-234">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="8d5a7-235">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="8d5a7-235">Instructions</span></span>

* <span data-ttu-id="8d5a7-236">Erstellen Sie **im Ordner Skripts ein** Skript mit dem Namen " **Redner-Manager**".</span><span class="sxs-lookup"><span data-stu-id="8d5a7-236">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="8d5a7-237">Ziehen Sie das **sprach-Manager** -Skript auf das **origamicollection** -Objekt in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-237">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="8d5a7-238">Öffnen Sie das **sprach-Manager** -Skript in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-238">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="8d5a7-239">Kopieren Sie diesen Code, und fügen Sie ihn in **SpeechManager.cs** ein. **Speichern Sie alle**</span><span class="sxs-lookup"><span data-stu-id="8d5a7-239">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="8d5a7-240">Öffnen Sie das **spherecommands** -Skript in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-240">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="8d5a7-241">Aktualisieren Sie das Skript wie folgt:</span><span class="sxs-lookup"><span data-stu-id="8d5a7-241">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="8d5a7-242">Exportieren, erstellen und Bereitstellen der APP auf dem hololens-Emulator.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-242">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="8d5a7-243">Der Emulator unterstützt das Mikrofon Ihres PCs und antwortet auf Ihre Stimme: passen Sie die Ansicht so an, dass sich der Cursor in einer der Bereiche befindet, und sagen Sie "Drop Sphere".</span><span class="sxs-lookup"><span data-stu-id="8d5a7-243">The emulator will support your PC's microphone and respond to your voice: adjust the view so the cursor is on one of the spheres, and say "Drop Sphere".</span></span>
* <span data-ttu-id="8d5a7-244">Sagen Sie "**Welt zurücksetzen**", um Sie wieder an Ihre ursprünglichen Positionen zu bringen.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-244">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="8d5a7-245">Kapitel 5: räumlicher Sound</span><span class="sxs-lookup"><span data-stu-id="8d5a7-245">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

<span data-ttu-id="8d5a7-246">In diesem Kapitel werden wir der App Musik hinzufügen und dann bei bestimmten Aktionen Soundeffekte auslöst.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-246">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="8d5a7-247">Wir verwenden den [räumlichen Ton](spatial-sound.md) , um Klänge an einem bestimmten Speicherort im 3D-Raum zu geben.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-247">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="8d5a7-248">Ziele</span><span class="sxs-lookup"><span data-stu-id="8d5a7-248">Objectives</span></span>

* <span data-ttu-id="8d5a7-249">Hören Sie holograms in ihrer Welt.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-249">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="8d5a7-250">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="8d5a7-250">Instructions</span></span>

* <span data-ttu-id="8d5a7-251">Wählen Sie in Unity im oberen Menü **> Projekteinstellungen > Audiodatei** aus.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-251">In the Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="8d5a7-252">Suchen Sie die Einstellung **spatializer Plugin** , und wählen Sie **MS HRTF spatializer**aus.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-252">Find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="8d5a7-253">Ziehen Sie das **Ambiente** -Objekt aus dem Ordner **holograms** auf das Objekt **origamicollection** im Bereich Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-253">From the **Holograms** folder, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="8d5a7-254">Wählen Sie **origamicollection** aus, und suchen Sie die Komponente **Audioquelle** .</span><span class="sxs-lookup"><span data-stu-id="8d5a7-254">Select **OrigamiCollection** and find the **Audio Source** component.</span></span> <span data-ttu-id="8d5a7-255">Ändern Sie die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="8d5a7-255">Change these properties:</span></span>
  * <span data-ttu-id="8d5a7-256">Überprüfen Sie die **spatialize** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-256">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="8d5a7-257">Überprüfen Sie die wieder **Gabe bei wach**.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-257">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="8d5a7-258">Ändern Sie **räumliche Blend** in **3D** , indem Sie den Schieberegler nach rechts ziehen.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-258">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span>
  * <span data-ttu-id="8d5a7-259">Überprüfen Sie die **Loop** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-259">Check the **Loop** property.</span></span>
  * <span data-ttu-id="8d5a7-260">Erweitern Sie **3D-Sound Einstellungen**, und geben Sie **0,1** für die **Doppler-Ebene**ein.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-260">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="8d5a7-261">Legen Sie **volumenrolloff** auf **logarithmische Rolloff**fest.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-261">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="8d5a7-262">Legen Sie **Max Distance** auf **20**fest.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-262">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="8d5a7-263">Erstellen Sie im Ordner **Scripts** ein Skript mit dem Namen " **spheresounds**".</span><span class="sxs-lookup"><span data-stu-id="8d5a7-263">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="8d5a7-264">Ziehen Sie " **spheresounds** " in die **Sphere1** -und **Sphere2** -Objekte in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-264">Drag **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="8d5a7-265">Öffnen Sie " **spheresounds** " in Visual Studio, aktualisieren Sie den folgenden Code, und **Speichern Sie alle**.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-265">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="8d5a7-266">Speichern Sie das Skript, und kehren Sie zu Unity zurück.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-266">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="8d5a7-267">Exportieren, erstellen und Bereitstellen der APP auf dem hololens-Emulator.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-267">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="8d5a7-268">Tragen Sie Kopfhörer, um den vollständigen Effekt zu erhalten, und bewegen Sie sich näher und weiter von der Stufe aus, um die Geräusche zu ändern.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-268">Wear headphones to get the full effect, and move closer and further from the Stage to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="8d5a7-269">Kapitel 6: räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="8d5a7-269">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

<span data-ttu-id="8d5a7-270">Nun verwenden wir die [räumliche Zuordnung](spatial-mapping.md) , um das Spiel Board in einem realen Objekt in der realen Welt zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-270">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="8d5a7-271">Ziele</span><span class="sxs-lookup"><span data-stu-id="8d5a7-271">Objectives</span></span>

* <span data-ttu-id="8d5a7-272">Bringen Sie Ihre reale Welt in die virtuelle Welt.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-272">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="8d5a7-273">Platzieren Sie Ihre Hologramme, wo Sie für Sie am wichtigsten sind.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-273">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="8d5a7-274">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="8d5a7-274">Instructions</span></span>

* <span data-ttu-id="8d5a7-275">Klicken Sie im Projekt Panel auf den Ordner **holograms** .</span><span class="sxs-lookup"><span data-stu-id="8d5a7-275">Click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="8d5a7-276">Ziehen Sie das Objekt für die **räumliche Zuordnung** in den Stamm der **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-276">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="8d5a7-277">Klicken Sie in der Hierarchie auf das **räumliche Mapping** -Objekt.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-277">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="8d5a7-278">Ändern Sie im **Inspektor-Panel**die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="8d5a7-278">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="8d5a7-279">Aktivieren Sie das Kontrollkästchen **visuelle Meshes zeichnen** .</span><span class="sxs-lookup"><span data-stu-id="8d5a7-279">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="8d5a7-280">Suchen Sie das **Zeichnungs Material** , und klicken Sie auf den Kreis rechts.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-280">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="8d5a7-281">Geben Sie im Feld oben den Text "**Draht Modell**" in das Suchfeld ein.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-281">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="8d5a7-282">Klicken Sie auf das Ergebnis, und schließen Sie das Fenster.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-282">Click on the result and then close the window.</span></span>
* <span data-ttu-id="8d5a7-283">Exportieren, erstellen und Bereitstellen der APP auf dem hololens-Emulator.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-283">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="8d5a7-284">Wenn die app ausgeführt wird, wird ein Mesh eines zuvor gescannten realen Wohnraums in Wireframe gerendert.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-284">When the app runs, a mesh of a previously scanned real-world living room will be rendered in wireframe.</span></span>
* <span data-ttu-id="8d5a7-285">Sehen Sie sich an, wie sich eine parallele Kugel auf der Ebene befindet und auf den Boden zeigt.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-285">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="8d5a7-286">Nun zeigen wir Ihnen, wie Sie die origamicollection an einen neuen Speicherort verschieben:</span><span class="sxs-lookup"><span data-stu-id="8d5a7-286">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="8d5a7-287">Erstellen Sie im Ordner **Scripts** ein Skript mit dem Namen " **taptoplaceparent**".</span><span class="sxs-lookup"><span data-stu-id="8d5a7-287">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="8d5a7-288">Erweitern Sie in der- **Hierarchie**die **origamicollection** , und wählen Sie das **Stage** -Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-288">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="8d5a7-289">Ziehen Sie das Skript **taptoplaceparent** auf das Stage-Objekt.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-289">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="8d5a7-290">Öffnen Sie das Skript " **taptoplaceparent** " in Visual Studio, und aktualisieren Sie es wie folgt:</span><span class="sxs-lookup"><span data-stu-id="8d5a7-290">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="8d5a7-291">Exportieren, erstellen und Bereitstellen der app.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-291">Export, build and deploy the app.</span></span>
* <span data-ttu-id="8d5a7-292">Nun sollten Sie nun in der Lage sein, das Spiel an einem bestimmten Speicherort zu platzieren, indem Sie die Auswahl Bewegung (**eine** oder Leertaste) verwenden und dann an eine neue Position verschieben und die Auswahl erneut verwenden.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-292">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture (**A** or Spacebar) and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="the-end"></a><span data-ttu-id="8d5a7-293">Das Ende</span><span class="sxs-lookup"><span data-stu-id="8d5a7-293">The end</span></span>

<span data-ttu-id="8d5a7-294">Und das ist das Ende dieses Tutorials!</span><span class="sxs-lookup"><span data-stu-id="8d5a7-294">And that's the end of this tutorial!</span></span>

<span data-ttu-id="8d5a7-295">Sie haben Folgendes gelernt:</span><span class="sxs-lookup"><span data-stu-id="8d5a7-295">You learned:</span></span>

* <span data-ttu-id="8d5a7-296">Erstellen einer Holographic-app in Unity.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-296">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="8d5a7-297">Verwendung von Blick, Bewegung, Stimme, Sounds und räumlicher Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-297">How to make use of gaze, gesture, voice, sounds, and spatial mapping.</span></span>
* <span data-ttu-id="8d5a7-298">Erfahren Sie, wie Sie eine APP mit Visual Studio erstellen und bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="8d5a7-298">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="8d5a7-299">Sie sind nun bereit, eigene Holographic apps zu erstellen!</span><span class="sxs-lookup"><span data-stu-id="8d5a7-299">You are now ready to start creating your own holographic apps!</span></span>

## <a name="see-also"></a><span data-ttu-id="8d5a7-300">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="8d5a7-300">See also</span></span>

* [<span data-ttu-id="8d5a7-301">Grundlagen 101: Projekt mit Gerät abschließen</span><span class="sxs-lookup"><span data-stu-id="8d5a7-301">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="8d5a7-302">Anvisieren</span><span class="sxs-lookup"><span data-stu-id="8d5a7-302">Gaze</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="8d5a7-303">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="8d5a7-303">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="8d5a7-304">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="8d5a7-304">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="8d5a7-305">Raumklang</span><span class="sxs-lookup"><span data-stu-id="8d5a7-305">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="8d5a7-306">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="8d5a7-306">Spatial mapping</span></span>](spatial-mapping.md)
