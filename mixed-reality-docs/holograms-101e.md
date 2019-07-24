---
title: Grundlagen 101 e-Complete Project with Emulator
description: Befolgen Sie diese exemplarische Vorgehensweise, indem Sie Unity, Visual Studio und den hololens-Emulator verwenden, um die Grundlagen einer Holographic-Anwendung kennenzulernen.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Gemischte Realität, Windows Mixed Reality, hololens, Hologram, Academy, Tutorial, Emulator
ms.openlocfilehash: 77f7d497396937bf471a69fa514cef84ab0b699d
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522322"
---
>[!NOTE]
><span data-ttu-id="b164a-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="b164a-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="b164a-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="b164a-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="b164a-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b164a-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="b164a-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="b164a-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="b164a-108">Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="b164a-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="b164a-109">Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="b164a-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a><span data-ttu-id="b164a-110">Grundlagen 101 e: Projekt mit Emulator vervollständigen</span><span class="sxs-lookup"><span data-stu-id="b164a-110">MR Basics 101E: Complete project with emulator</span></span>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

<span data-ttu-id="b164a-111">In diesem Tutorial werden Sie durch ein vollständiges Projekt geführt, das in Unity integriert ist, das grundlegende Windows Mixed Reality-Features in hololens veranschaulicht, einschließlich [Blick](gaze.md), [Gesten](gestures.md), [Spracheingabe](voice-input.md), [räumlichem Sound](spatial-sound.md) und [räumlicher Zuordnung](spatial-mapping.md) . .</span><span class="sxs-lookup"><span data-stu-id="b164a-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span> <span data-ttu-id="b164a-112">Das Tutorial dauert ungefähr 1 Stunde.</span><span class="sxs-lookup"><span data-stu-id="b164a-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="b164a-113">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="b164a-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="b164a-114">Natürlich</span><span class="sxs-lookup"><span data-stu-id="b164a-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="b164a-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="b164a-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="b164a-116"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="b164a-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="b164a-117">Grundlagen 101 e: Projekt mit Emulator vervollständigen</span><span class="sxs-lookup"><span data-stu-id="b164a-117">MR Basics 101E: Complete project with emulator</span></span></td><td style="text-align: center;"> <span data-ttu-id="b164a-118">✔️</span><span class="sxs-lookup"><span data-stu-id="b164a-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="b164a-119">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="b164a-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="b164a-120">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="b164a-120">Prerequisites</span></span>

* <span data-ttu-id="b164a-121">Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md)konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="b164a-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

### <a name="project-files"></a><span data-ttu-id="b164a-122">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="b164a-122">Project files</span></span>

* <span data-ttu-id="b164a-123">Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) , die für das Projekt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="b164a-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="b164a-124"> Erfordert Unity 2017,2 oder höher.</span><span class="sxs-lookup"><span data-stu-id="b164a-124"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="b164a-125">Wenn Sie weiterhin Unity 5,6-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="b164a-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="b164a-126">Wenn Sie weiterhin Unity 5,5-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="b164a-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="b164a-127">Wenn Sie weiterhin Unity 5,4-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="b164a-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="b164a-128">Deinstallieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht zugänglichen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="b164a-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="b164a-129">Behalten Sie den Ordnernamen **Origami**bei.</span><span class="sxs-lookup"><span data-stu-id="b164a-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="b164a-130">Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="b164a-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="b164a-131">Kapitel 1: "Holo" World</span><span class="sxs-lookup"><span data-stu-id="b164a-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

<span data-ttu-id="b164a-132">In diesem Kapitel richten wir das erste Unity-Projekt ein und durchlaufen den Build-und Bereitstellungs Prozess.</span><span class="sxs-lookup"><span data-stu-id="b164a-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="b164a-133">Ziele</span><span class="sxs-lookup"><span data-stu-id="b164a-133">Objectives</span></span>

* <span data-ttu-id="b164a-134">Einrichten von Unity für die Holographic-Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="b164a-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="b164a-135">Erstellen Sie ein Hologram.</span><span class="sxs-lookup"><span data-stu-id="b164a-135">Make a hologram.</span></span>
* <span data-ttu-id="b164a-136">Sehen Sie sich ein von Ihnen vorgenommene – Hologramm an.</span><span class="sxs-lookup"><span data-stu-id="b164a-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="b164a-137">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="b164a-137">Instructions</span></span>

* <span data-ttu-id="b164a-138">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="b164a-138">Start Unity.</span></span>
* <span data-ttu-id="b164a-139">Wählen Sie **Öffnen**aus.</span><span class="sxs-lookup"><span data-stu-id="b164a-139">Select **Open**.</span></span>
* <span data-ttu-id="b164a-140">Geben Sie Location als den Ordner **Origami** ein, den Sie zuvor nicht archiviert haben.</span><span class="sxs-lookup"><span data-stu-id="b164a-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="b164a-141">Wählen Sie **Origami** , und klicken Sie auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="b164a-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="b164a-142">Speichern Sie die neue Szene: Datei / **Speichern**unter.</span><span class="sxs-lookup"><span data-stu-id="b164a-142">Save the new scene: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="b164a-143">Nennen Sie die Szene **Origami** , und klicken Sie auf die Schaltfläche **Speichern** .</span><span class="sxs-lookup"><span data-stu-id="b164a-143">Name the scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-camera"></a><span data-ttu-id="b164a-144">Einrichten der Hauptkamera</span><span class="sxs-lookup"><span data-stu-id="b164a-144">Setup the main camera</span></span>

* <span data-ttu-id="b164a-145">Wählen Sie im Bereich **Hierarchie**die Option **Hauptkamera**aus.</span><span class="sxs-lookup"><span data-stu-id="b164a-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="b164a-146">Legen Sie im **Inspektor** die Transformations Position auf **0, 0, 0**fest.</span><span class="sxs-lookup"><span data-stu-id="b164a-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="b164a-147">Suchen Sie die Eigenschaft **Clear Flags** , und ändern Sie die Dropdown Liste von  **Skybox** in voll Tonfarbe.</span><span class="sxs-lookup"><span data-stu-id="b164a-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="b164a-148">Klicken Sie auf das Feld **Hintergrund** , um eine Farbauswahl zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="b164a-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="b164a-149">Legen Sie **R, G, B und A** auf **0**fest.</span><span class="sxs-lookup"><span data-stu-id="b164a-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="b164a-150">Einrichten der Szene</span><span class="sxs-lookup"><span data-stu-id="b164a-150">Setup the scene</span></span>

* <span data-ttu-id="b164a-151">Klicken Sie im **Hierarchie Panel**auf **Erstellen** , und erstellen Sie eine **leere**.</span><span class="sxs-lookup"><span data-stu-id="b164a-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="b164a-152">Klicken Sie mit der rechten Maustaste auf das neue **gameobject** und wählen Sie umbenennen</span><span class="sxs-lookup"><span data-stu-id="b164a-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="b164a-153">Benennen Sie das gameobject in **origamicollection**um.</span><span class="sxs-lookup"><span data-stu-id="b164a-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="b164a-154">Aus dem Ordner " **holograms** " im **Projekt Panel**:</span><span class="sxs-lookup"><span data-stu-id="b164a-154">From the **Holograms** folder in the **Project Panel**:</span></span>
  * <span data-ttu-id="b164a-155">Ziehen Sie die **Phase** in die Hierarchie, um ein untergeordnetes Element von **origamicollection**zu sein.</span><span class="sxs-lookup"><span data-stu-id="b164a-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="b164a-156">Ziehen Sie **Sphere1** in die Hierarchie, um ein untergeordnetes Element von **origamicollection**zu sein.</span><span class="sxs-lookup"><span data-stu-id="b164a-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="b164a-157">Ziehen Sie **Sphere2** in die Hierarchie, um ein untergeordnetes Element von **origamicollection**zu sein.</span><span class="sxs-lookup"><span data-stu-id="b164a-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="b164a-158">Klicken Sie im Bereich **Hierarchie** mit der rechten Maustaste auf das Objekt **direktional hell** , und wählen Sie **Löschen**aus</span><span class="sxs-lookup"><span data-stu-id="b164a-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="b164a-159">Ziehen Sie aus dem Ordner **holograms** die **Beleuchtung** in das Stammverzeichnis des Bereichs **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="b164a-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="b164a-160">Wählen Sie in der **Hierarchie**die Option **origamicollection**aus.</span><span class="sxs-lookup"><span data-stu-id="b164a-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="b164a-161">Legen Sie im **Inspektor**die Transformations Position auf **0,-0,5, 2,0**fest.</span><span class="sxs-lookup"><span data-stu-id="b164a-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="b164a-162">Klicken Sie in Unity auf die **Wiedergabe** Schaltfläche, um eine Vorschau der holograms anzuzeigen</span><span class="sxs-lookup"><span data-stu-id="b164a-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="b164a-163">Die Origami-Objekte sollten im Vorschaufenster angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b164a-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="b164a-164">Drücken **Sie** ein zweites Mal, um den Vorschaumodus zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="b164a-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="b164a-165">Exportieren des Projekts aus Unity in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b164a-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="b164a-166">Wählen Sie in Unity **Datei >** Buildeinstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="b164a-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="b164a-167">Wählen Sie in der Liste **Plattform** den **Windows Store** aus, und klicken Sie auf **Plattform wechseln**.</span><span class="sxs-lookup"><span data-stu-id="b164a-167">Select **Windows Store** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="b164a-168">Legen Sie das **SDK** auf **Universal 10** und den Buildtyp auf **D3D**fest.</span><span class="sxs-lookup"><span data-stu-id="b164a-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="b164a-169">Überprüfen Sie **Unity C# -Projekte**.</span><span class="sxs-lookup"><span data-stu-id="b164a-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="b164a-170">Klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="b164a-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="b164a-171">Klicken Sie auf **Player Einstellungen...** .</span><span class="sxs-lookup"><span data-stu-id="b164a-171">Click **Player Settings...**.</span></span>
* <span data-ttu-id="b164a-172">Wählen Sie im Inspektor-Panel das **Windows Store-Logo**aus.</span><span class="sxs-lookup"><span data-stu-id="b164a-172">In the Inspector Panel select the **Windows Store logo**.</span></span> <span data-ttu-id="b164a-173">Wählen Sie dann **Veröffentlichungs Einstellungen**aus.</span><span class="sxs-lookup"><span data-stu-id="b164a-173">Then select **Publishing Settings**.</span></span>
* <span data-ttu-id="b164a-174">Wählen Sie im Abschnitt " **Funktionen** " die Funktionen " **Mikrofon** " und " **spatialperception** " aus.</span><span class="sxs-lookup"><span data-stu-id="b164a-174">In the **Capabilities** section, select the **Microphone** and **SpatialPerception** capabilities.</span></span>
* <span data-ttu-id="b164a-175">Klicken Sie im Fenster "Buildeinstellungen" auf " **Erstellen**".</span><span class="sxs-lookup"><span data-stu-id="b164a-175">Back in the Build Settings window, click **Build**.</span></span>
* <span data-ttu-id="b164a-176">Erstellen Sie einen **neuen Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="b164a-176">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="b164a-177">Klicken Sie einfach auf den **app-Ordner**.</span><span class="sxs-lookup"><span data-stu-id="b164a-177">Single click the **App Folder**.</span></span>
* <span data-ttu-id="b164a-178">Drücken **Sie Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="b164a-178">Press **Select Folder**.</span></span>
* <span data-ttu-id="b164a-179">Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b164a-179">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="b164a-180">Öffnen Sie den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="b164a-180">Open the **App** folder.</span></span>
* <span data-ttu-id="b164a-181">Öffnen Sie die Visual Studio-Projekt Mappe **Origami**.</span><span class="sxs-lookup"><span data-stu-id="b164a-181">Open the **Origami Visual Studio Solution**.</span></span>
* <span data-ttu-id="b164a-182">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x86**.</span><span class="sxs-lookup"><span data-stu-id="b164a-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
  * <span data-ttu-id="b164a-183">Klicken Sie auf den Pfeil neben der Schaltfläche Gerät, und wählen Sie **hololens Emulator**aus.</span><span class="sxs-lookup"><span data-stu-id="b164a-183">Click on the arrow next to the Device button, and select **HoloLens Emulator**.</span></span>
  * <span data-ttu-id="b164a-184">Klicken Sie auf **Debuggen > Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="b164a-184">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
  * <span data-ttu-id="b164a-185">Nach einiger Zeit wird der Emulator mit dem Origami-Projekt gestartet.</span><span class="sxs-lookup"><span data-stu-id="b164a-185">After some time the emulator will start with the Origami project.</span></span> <span data-ttu-id="b164a-186">Beim ersten Starten des [Emulators](using-the-hololens-emulator.md)kann es bis zu 15 Minuten dauern, bis der Emulator gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="b164a-186">When first launching the [emulator](using-the-hololens-emulator.md), it can take as long as 15 minutes for the emulator to start up.</span></span> <span data-ttu-id="b164a-187">Schließen Sie die Datei nach dem Start nicht.</span><span class="sxs-lookup"><span data-stu-id="b164a-187">Once it starts, do not close it.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="b164a-188">Kapitel 2: Blick</span><span class="sxs-lookup"><span data-stu-id="b164a-188">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

<span data-ttu-id="b164a-189">In diesem Kapitel werden die ersten von drei Möglichkeiten vorgestellt, mit denen Sie mit ihren holograms interagieren [können.](gaze.md)</span><span class="sxs-lookup"><span data-stu-id="b164a-189">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="b164a-190">Ziele</span><span class="sxs-lookup"><span data-stu-id="b164a-190">Objectives</span></span>

* <span data-ttu-id="b164a-191">Visualisieren Sie Ihren Blick mithilfe eines weltweit gesperrten Cursors.</span><span class="sxs-lookup"><span data-stu-id="b164a-191">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="b164a-192">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="b164a-192">Instructions</span></span>

* <span data-ttu-id="b164a-193">Wechseln Sie zurück zu Ihrem Unity-Projekt, und schließen Sie das Fenster mit den Buildeinstellungen, wenn es noch geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="b164a-193">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="b164a-194">Wählen Sie im **Projekt Panel**den Ordner **holograms** aus.</span><span class="sxs-lookup"><span data-stu-id="b164a-194">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="b164a-195">Ziehen Sie das **Cursor** Objekt in das **Hierarchie Panel** auf der Stamm Ebene.</span><span class="sxs-lookup"><span data-stu-id="b164a-195">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="b164a-196">Doppelklicken Sie auf das **Cursor** Objekt, um es genauer zu betrachten.</span><span class="sxs-lookup"><span data-stu-id="b164a-196">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="b164a-197">Klicken Sie im Projekt Panel mit der rechten Maustaste auf den Ordner **Scripts** .</span><span class="sxs-lookup"><span data-stu-id="b164a-197">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="b164a-198">Klicken Sie auf das Untermenü **Erstellen** .</span><span class="sxs-lookup"><span data-stu-id="b164a-198">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="b164a-199">Wählen Sie  **C# Skript**aus.</span><span class="sxs-lookup"><span data-stu-id="b164a-199">Select **C# Script**.</span></span>
* <span data-ttu-id="b164a-200">Nennen Sie das Skript **worldcursor**.</span><span class="sxs-lookup"><span data-stu-id="b164a-200">Name the script **WorldCursor**.</span></span> <span data-ttu-id="b164a-201">Hinweis: Beim Namen wird Groß- und Kleinschreibung beachtet.</span><span class="sxs-lookup"><span data-stu-id="b164a-201">Note: The name is case-sensitive.</span></span> <span data-ttu-id="b164a-202">Sie müssen die Erweiterung ". cs" nicht hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b164a-202">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="b164a-203">Wählen Sie im **Hierarchie Panel**das **Cursor** Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="b164a-203">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="b164a-204">Verschieben Sie das **worldcursor** -Skript per Drag & amp; Drop in den Bereich **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="b164a-204">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="b164a-205">Doppelklicken Sie auf das Skript **worldcursor** , um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="b164a-205">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="b164a-206">Fügen Sie diesen Code in **WorldCursor.cs** ein, und **Speichern Sie alle**.</span><span class="sxs-lookup"><span data-stu-id="b164a-206">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

* <span data-ttu-id="b164a-207">Erstellen Sie die APP aus dem **Datei >** den Buildeinstellungen neu.</span><span class="sxs-lookup"><span data-stu-id="b164a-207">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="b164a-208">Kehren Sie zur Visual Studio-Projekt Mappe zurück, die zuvor zur Bereitstellung im Emulator verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="b164a-208">Return to the Visual Studio solution previously used to deploy to the emulator.</span></span>
* <span data-ttu-id="b164a-209">Wählen Sie bei entsprechender Aufforderung "alle neu laden" aus.</span><span class="sxs-lookup"><span data-stu-id="b164a-209">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="b164a-210">Klicken Sie auf **Debuggen > Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="b164a-210">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="b164a-211">Verwenden Sie den Xbox-Controller, um die Szene zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="b164a-211">Use the Xbox controller to look around the scene.</span></span> <span data-ttu-id="b164a-212">Beachten Sie, wie der Cursor mit der Form von-Objekten interagiert.</span><span class="sxs-lookup"><span data-stu-id="b164a-212">Notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="b164a-213">Kapitel 3: Gesten</span><span class="sxs-lookup"><span data-stu-id="b164a-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

<span data-ttu-id="b164a-214">In diesem Kapitel wird die Unterstützung für [Gesten](gestures.md)hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="b164a-214">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="b164a-215">Wenn der Benutzer eine Papierkugel auswählt, wird die Kugel durch das Aktivieren der Schwerkraft mit der Physik-Engine von Unity erreicht.</span><span class="sxs-lookup"><span data-stu-id="b164a-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="b164a-216">Ziele</span><span class="sxs-lookup"><span data-stu-id="b164a-216">Objectives</span></span>

* <span data-ttu-id="b164a-217">Steuern Sie Ihre Hologramme mit der SELECT-Geste.</span><span class="sxs-lookup"><span data-stu-id="b164a-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="b164a-218">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="b164a-218">Instructions</span></span>

<span data-ttu-id="b164a-219">Wir beginnen mit dem Erstellen eines Skripts, als die SELECT-Geste erkennen zu können.</span><span class="sxs-lookup"><span data-stu-id="b164a-219">We'll start by creating a script than can detect the Select gesture.</span></span>

* <span data-ttu-id="b164a-220">Erstellen Sie im Ordner **Scripts** ein Skript mit dem Namen " **gazegesturemanager**".</span><span class="sxs-lookup"><span data-stu-id="b164a-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="b164a-221">Ziehen Sie das Skript " **gazegesturemanager** " auf das Objekt " **origamicollection** " in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="b164a-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="b164a-222">Öffnen Sie das Skript " **gazegesturemanager** " in Visual Studio, und fügen Sie den folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="b164a-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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

* <span data-ttu-id="b164a-223">Erstellen Sie ein weiteres Skript im Ordner "Scripts", diesmal mit dem Namen **spherecommands**.</span><span class="sxs-lookup"><span data-stu-id="b164a-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="b164a-224">Erweitern Sie das Objekt **origamicollection** in der Hierarchie Ansicht.</span><span class="sxs-lookup"><span data-stu-id="b164a-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="b164a-225">Ziehen Sie das **spherecommands** -Skript auf das **Sphere1** -Objekt im Hierarchie Panel.</span><span class="sxs-lookup"><span data-stu-id="b164a-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="b164a-226">Ziehen Sie das **spherecommands** -Skript auf das **Sphere2** -Objekt im Hierarchie Panel.</span><span class="sxs-lookup"><span data-stu-id="b164a-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="b164a-227">Öffnen Sie das Skript in Visual Studio zur Bearbeitung, und ersetzen Sie den Standard Code durch den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="b164a-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="b164a-228">Exportieren, erstellen und Bereitstellen der APP auf dem hololens-Emulator.</span><span class="sxs-lookup"><span data-stu-id="b164a-228">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="b164a-229">Sehen Sie sich die Szene an, und zentrieren Sie eine der Bereiche.</span><span class="sxs-lookup"><span data-stu-id="b164a-229">Look around the scene, and center on one of the spheres.</span></span>
* <span data-ttu-id="b164a-230">Drücken Sie **die Schaltfläche** auf dem Xbox-Controller, oder drücken Sie die Leertaste, um die Auswahl Bewegung zu simulieren.</span><span class="sxs-lookup"><span data-stu-id="b164a-230">Press the **A** button on the Xbox controller or press the Spacebar to simulate the Select gesture.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="b164a-231">Kapitel 4: Stimme</span><span class="sxs-lookup"><span data-stu-id="b164a-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

<span data-ttu-id="b164a-232">In diesem Kapitel wird die Unterstützung für zwei [Sprachbefehle](voice-input.md)hinzugefügt: "World zurücksetzen" gibt die gelöschten Bereiche an ihren ursprünglichen Speicherort zurück, und "Drop Sphere", um die Kugel zu verlieren.</span><span class="sxs-lookup"><span data-stu-id="b164a-232">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to returns the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="b164a-233">Ziele</span><span class="sxs-lookup"><span data-stu-id="b164a-233">Objectives</span></span>

* <span data-ttu-id="b164a-234">Fügen Sie Sprachbefehle hinzu, die immer im Hintergrund lauschen.</span><span class="sxs-lookup"><span data-stu-id="b164a-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="b164a-235">Erstellen Sie ein – Hologramm, das auf einen Voice-Befehl reagiert.</span><span class="sxs-lookup"><span data-stu-id="b164a-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="b164a-236">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="b164a-236">Instructions</span></span>

* <span data-ttu-id="b164a-237">Erstellen Sie **im Ordner** Skripts ein Skript mit dem Namen " **Redner-Manager**".</span><span class="sxs-lookup"><span data-stu-id="b164a-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="b164a-238">Ziehen Sie das **sprach-Manager** -Skript auf das **origamicollection** -Objekt in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="b164a-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="b164a-239">Öffnen Sie das **sprach-Manager** -Skript in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b164a-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="b164a-240">Kopieren Sie diesen Code, und fügen Sie ihn in **SpeechManager.cs** ein. **Speichern Sie alle**</span><span class="sxs-lookup"><span data-stu-id="b164a-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="b164a-241">Öffnen Sie das **spherecommands** -Skript in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b164a-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="b164a-242">Aktualisieren Sie das Skript wie folgt:</span><span class="sxs-lookup"><span data-stu-id="b164a-242">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="b164a-243">Exportieren, erstellen und Bereitstellen der APP auf dem hololens-Emulator.</span><span class="sxs-lookup"><span data-stu-id="b164a-243">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="b164a-244">Der Emulator unterstützt das Mikrofon Ihres PCs und antwortet auf Ihre Stimme: passen Sie die Ansicht so an, dass sich der Cursor in einer der Bereiche befindet, und sagen Sie "Drop Sphere".</span><span class="sxs-lookup"><span data-stu-id="b164a-244">The emulator will support your PC's microphone and respond to your voice: adjust the view so the cursor is on one of the spheres, and say "Drop Sphere".</span></span>
* <span data-ttu-id="b164a-245">Sagen Sie "**Welt zurücksetzen**", um Sie wieder an Ihre ursprünglichen Positionen zu bringen.</span><span class="sxs-lookup"><span data-stu-id="b164a-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="b164a-246">Kapitel 5: räumlicher Sound</span><span class="sxs-lookup"><span data-stu-id="b164a-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

<span data-ttu-id="b164a-247">In diesem Kapitel werden wir der App Musik hinzufügen und dann bei bestimmten Aktionen Soundeffekte auslöst.</span><span class="sxs-lookup"><span data-stu-id="b164a-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="b164a-248">Wir verwenden den [räumlichen Ton](spatial-sound.md) , um Klänge an einem bestimmten Speicherort im 3D-Raum zu geben.</span><span class="sxs-lookup"><span data-stu-id="b164a-248">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="b164a-249">Ziele</span><span class="sxs-lookup"><span data-stu-id="b164a-249">Objectives</span></span>

* <span data-ttu-id="b164a-250">Hören Sie holograms in ihrer Welt.</span><span class="sxs-lookup"><span data-stu-id="b164a-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="b164a-251">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="b164a-251">Instructions</span></span>

* <span data-ttu-id="b164a-252">Wählen Sie in Unity im oberen Menü **> Projekteinstellungen > Audiodatei** aus.</span><span class="sxs-lookup"><span data-stu-id="b164a-252">In the Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="b164a-253">Suchen Sie die Einstellung **spatializer Plugin** , und wählen Sie **MS HRTF spatializer**aus.</span><span class="sxs-lookup"><span data-stu-id="b164a-253">Find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="b164a-254">Ziehen Sie das **Ambiente** -Objekt aus dem Ordner **holograms** auf das Objekt **origamicollection** im Bereich Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="b164a-254">From the **Holograms** folder, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="b164a-255">Wählen Sie **origamicollection** aus, und suchen Sie die Komponente **Audioquelle** .</span><span class="sxs-lookup"><span data-stu-id="b164a-255">Select **OrigamiCollection** and find the **Audio Source** component.</span></span> <span data-ttu-id="b164a-256">Ändern Sie die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="b164a-256">Change these properties:</span></span>
  * <span data-ttu-id="b164a-257">Überprüfen Sie die **spatialize** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="b164a-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="b164a-258">Überprüfen Sie die wieder **Gabe bei wach**.</span><span class="sxs-lookup"><span data-stu-id="b164a-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="b164a-259">Ändern Sie **räumliche Blend** in **3D** , indem Sie den Schieberegler nach rechts ziehen.</span><span class="sxs-lookup"><span data-stu-id="b164a-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span>
  * <span data-ttu-id="b164a-260">Überprüfen Sie die **Loop** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="b164a-260">Check the **Loop** property.</span></span>
  * <span data-ttu-id="b164a-261">Erweitern Sie **3D-Sound Einstellungen**, und geben Sie **0,1** für die **Doppler-Ebene**ein.</span><span class="sxs-lookup"><span data-stu-id="b164a-261">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="b164a-262">Legen Sie **volumenrolloff** auf **logarithmische Rolloff**fest.</span><span class="sxs-lookup"><span data-stu-id="b164a-262">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="b164a-263">Legen Sie **Max Distance** auf **20**fest.</span><span class="sxs-lookup"><span data-stu-id="b164a-263">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="b164a-264">Erstellen Sie im Ordner **Scripts** ein Skript mit dem Namen " **spheresounds**".</span><span class="sxs-lookup"><span data-stu-id="b164a-264">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="b164a-265">Ziehen Sie " **spheresounds** " in die **Sphere1** -und **Sphere2** -Objekte in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="b164a-265">Drag **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="b164a-266">Öffnen Sie " **spheresounds** " in Visual Studio, aktualisieren Sie den folgenden Code, und **Speichern Sie alle**.</span><span class="sxs-lookup"><span data-stu-id="b164a-266">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="b164a-267">Speichern Sie das Skript, und kehren Sie zu Unity zurück.</span><span class="sxs-lookup"><span data-stu-id="b164a-267">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="b164a-268">Exportieren, erstellen und Bereitstellen der APP auf dem hololens-Emulator.</span><span class="sxs-lookup"><span data-stu-id="b164a-268">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="b164a-269">Tragen Sie Kopfhörer, um den vollständigen Effekt zu erhalten, und bewegen Sie sich näher und weiter von der Stufe aus, um die Geräusche zu ändern.</span><span class="sxs-lookup"><span data-stu-id="b164a-269">Wear headphones to get the full effect, and move closer and further from the Stage to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="b164a-270">Kapitel 6: räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="b164a-270">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

<span data-ttu-id="b164a-271">Nun verwenden wir die [räumliche Zuordnung](spatial-mapping.md) , um das Spiel Board in einem realen Objekt in der realen Welt zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="b164a-271">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="b164a-272">Ziele</span><span class="sxs-lookup"><span data-stu-id="b164a-272">Objectives</span></span>

* <span data-ttu-id="b164a-273">Bringen Sie Ihre reale Welt in die virtuelle Welt.</span><span class="sxs-lookup"><span data-stu-id="b164a-273">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="b164a-274">Platzieren Sie Ihre Hologramme, wo Sie für Sie am wichtigsten sind.</span><span class="sxs-lookup"><span data-stu-id="b164a-274">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="b164a-275">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="b164a-275">Instructions</span></span>

* <span data-ttu-id="b164a-276">Klicken Sie im Projekt Panel auf den Ordner **holograms** .</span><span class="sxs-lookup"><span data-stu-id="b164a-276">Click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="b164a-277">Ziehen Sie das Objekt für die **räumliche Zuordnung** in den Stamm der **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="b164a-277">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="b164a-278">Klicken Sie in der Hierarchie auf das **räumliche Mapping** -Objekt.</span><span class="sxs-lookup"><span data-stu-id="b164a-278">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="b164a-279">Ändern Sie im **Inspektor-Panel**die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="b164a-279">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="b164a-280">Aktivieren Sie das Kontrollkästchen **visuelle Meshes zeichnen** .</span><span class="sxs-lookup"><span data-stu-id="b164a-280">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="b164a-281">Suchen Sie das **Zeichnungs Material** , und klicken Sie auf den Kreis rechts.</span><span class="sxs-lookup"><span data-stu-id="b164a-281">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="b164a-282">Geben Sie im Feld oben den Text "**Draht Modell**" in das Suchfeld ein.</span><span class="sxs-lookup"><span data-stu-id="b164a-282">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="b164a-283">Klicken Sie auf das Ergebnis, und schließen Sie das Fenster.</span><span class="sxs-lookup"><span data-stu-id="b164a-283">Click on the result and then close the window.</span></span>
* <span data-ttu-id="b164a-284">Exportieren, erstellen und Bereitstellen der APP auf dem hololens-Emulator.</span><span class="sxs-lookup"><span data-stu-id="b164a-284">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="b164a-285">Wenn die app ausgeführt wird, wird ein Mesh eines zuvor gescannten realen Wohnraums in Wireframe gerendert.</span><span class="sxs-lookup"><span data-stu-id="b164a-285">When the app runs, a mesh of a previously scanned real-world living room will be rendered in wireframe.</span></span>
* <span data-ttu-id="b164a-286">Sehen Sie sich an, wie sich eine parallele Kugel auf der Ebene befindet und auf den Boden zeigt.</span><span class="sxs-lookup"><span data-stu-id="b164a-286">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="b164a-287">Nun zeigen wir Ihnen, wie Sie die origamicollection an einen neuen Speicherort verschieben:</span><span class="sxs-lookup"><span data-stu-id="b164a-287">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="b164a-288">Erstellen Sie im Ordner **Scripts** ein Skript mit dem Namen " **taptoplaceparent**".</span><span class="sxs-lookup"><span data-stu-id="b164a-288">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="b164a-289">Erweitern Sie in der- **Hierarchie**die **origamicollection** , und wählen Sie das **Stage** -Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="b164a-289">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="b164a-290">Ziehen Sie das Skript **taptoplaceparent** auf das Stage-Objekt.</span><span class="sxs-lookup"><span data-stu-id="b164a-290">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="b164a-291">Öffnen Sie das Skript " **taptoplaceparent** " in Visual Studio, und aktualisieren Sie es wie folgt:</span><span class="sxs-lookup"><span data-stu-id="b164a-291">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="b164a-292">Exportieren, erstellen und Bereitstellen der app.</span><span class="sxs-lookup"><span data-stu-id="b164a-292">Export, build and deploy the app.</span></span>
* <span data-ttu-id="b164a-293">Nun sollten Sie nun in der Lage sein, das Spiel an einem bestimmten Speicherort zu platzieren, indem Sie die Auswahl Bewegung (**eine** oder Leertaste) verwenden und dann an eine neue Position verschieben und die Auswahl erneut verwenden.</span><span class="sxs-lookup"><span data-stu-id="b164a-293">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture (**A** or Spacebar) and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="the-end"></a><span data-ttu-id="b164a-294">Das Ende</span><span class="sxs-lookup"><span data-stu-id="b164a-294">The end</span></span>

<span data-ttu-id="b164a-295">Und das ist das Ende dieses Tutorials!</span><span class="sxs-lookup"><span data-stu-id="b164a-295">And that's the end of this tutorial!</span></span>

<span data-ttu-id="b164a-296">Sie haben Folgendes gelernt:</span><span class="sxs-lookup"><span data-stu-id="b164a-296">You learned:</span></span>

* <span data-ttu-id="b164a-297">Erstellen einer Holographic-app in Unity.</span><span class="sxs-lookup"><span data-stu-id="b164a-297">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="b164a-298">Verwendung von Blick, Bewegung, Stimme, Sounds und räumlicher Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="b164a-298">How to make use of gaze, gesture, voice, sounds, and spatial mapping.</span></span>
* <span data-ttu-id="b164a-299">Erfahren Sie, wie Sie eine APP mit Visual Studio erstellen und bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="b164a-299">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="b164a-300">Sie sind nun bereit, eigene Holographic apps zu erstellen!</span><span class="sxs-lookup"><span data-stu-id="b164a-300">You are now ready to start creating your own holographic apps!</span></span>

## <a name="see-also"></a><span data-ttu-id="b164a-301">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b164a-301">See also</span></span>

* [<span data-ttu-id="b164a-302">MR-Grundlagen 101: Vollständiges Projekt mit Gerät</span><span class="sxs-lookup"><span data-stu-id="b164a-302">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="b164a-303">Anvisieren</span><span class="sxs-lookup"><span data-stu-id="b164a-303">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="b164a-304">Gesten</span><span class="sxs-lookup"><span data-stu-id="b164a-304">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="b164a-305">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="b164a-305">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="b164a-306">Raumklang</span><span class="sxs-lookup"><span data-stu-id="b164a-306">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="b164a-307">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="b164a-307">Spatial mapping</span></span>](spatial-mapping.md)
