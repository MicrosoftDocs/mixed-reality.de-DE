---
title: Grundlagen 101-Projekt mit Gerät abschließen
description: Befolgen Sie diese exemplarische Vorgehensweise zum Programmieren mit Unity, Visual Studio und hololens, um die Grundlagen von Windows Mixed Reality kennenzulernen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Gemischte Realität, Windows Mixed Reality, hololens, Hologram, Academy, Tutorial
ms.openlocfilehash: 456aeea88b0d7f51acb52156d8139ec2df06883a
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434716"
---
>[!NOTE]
><span data-ttu-id="19e15-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="19e15-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="19e15-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="19e15-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="19e15-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="19e15-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="19e15-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="19e15-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="19e15-108">Es wurde [eine neue Reihe von Tutorials](mrlearning-base.md) für hololens 2 gepostet.</span><span class="sxs-lookup"><span data-stu-id="19e15-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-basics-101-complete-project-with-device"></a><span data-ttu-id="19e15-109">Grundlagen 101: Projekt mit Gerät abschließen</span><span class="sxs-lookup"><span data-stu-id="19e15-109">MR Basics 101: Complete project with device</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

<span data-ttu-id="19e15-110">In diesem Tutorial werden Sie durch ein vollständiges Projekt geführt, das in Unity integriert ist, das grundlegende Windows Mixed Reality-Features in hololens veranschaulicht, einschließlich [Blick](gaze-and-commit.md), [Gesten](gaze-and-commit.md#composite-gestures), [Spracheingabe](voice-input.md), [räumlichem Sound](spatial-sound.md) und [räumlicher Zuordnung](spatial-mapping.md) . .</span><span class="sxs-lookup"><span data-stu-id="19e15-110">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze-and-commit.md), [gestures](gaze-and-commit.md#composite-gestures), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span>

<span data-ttu-id="19e15-111">Das Tutorial dauert ungefähr 1 Stunde.</span><span class="sxs-lookup"><span data-stu-id="19e15-111">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="19e15-112">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="19e15-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="19e15-113">Natürlich</span><span class="sxs-lookup"><span data-stu-id="19e15-113">Course</span></span></th><th style="width:150px"> <span data-ttu-id="19e15-114"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="19e15-114"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="19e15-115"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="19e15-115"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="19e15-116">Grundlagen 101: Projekt mit Gerät abschließen</span><span class="sxs-lookup"><span data-stu-id="19e15-116">MR Basics 101: Complete project with device</span></span></td><td style="text-align: center;"> <span data-ttu-id="19e15-117">✔️</span><span class="sxs-lookup"><span data-stu-id="19e15-117">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="19e15-118">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="19e15-118">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="19e15-119">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="19e15-119">Prerequisites</span></span>

* <span data-ttu-id="19e15-120">Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md)konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="19e15-120">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="19e15-121">Ein hololens-Gerät, das [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode)ist.</span><span class="sxs-lookup"><span data-stu-id="19e15-121">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="19e15-122">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="19e15-122">Project files</span></span>

* <span data-ttu-id="19e15-123">Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) , die für das Projekt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="19e15-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="19e15-124"> Erfordert Unity 2017,2 oder höher.</span><span class="sxs-lookup"><span data-stu-id="19e15-124"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="19e15-125">Wenn Sie weiterhin Unity 5,6-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="19e15-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="19e15-126">Wenn Sie weiterhin Unity 5,5-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="19e15-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="19e15-127">Wenn Sie weiterhin Unity 5,4-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="19e15-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="19e15-128">Deinstallieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht zugänglichen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="19e15-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="19e15-129">Behalten Sie den Ordnernamen **Origami**bei.</span><span class="sxs-lookup"><span data-stu-id="19e15-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="19e15-130">Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="19e15-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="19e15-131">Kapitel 1: "Holo" World</span><span class="sxs-lookup"><span data-stu-id="19e15-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

<span data-ttu-id="19e15-132">In diesem Kapitel richten wir das erste Unity-Projekt ein und durchlaufen den Build-und Bereitstellungs Prozess.</span><span class="sxs-lookup"><span data-stu-id="19e15-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="19e15-133">Ziele</span><span class="sxs-lookup"><span data-stu-id="19e15-133">Objectives</span></span>

* <span data-ttu-id="19e15-134">Einrichten von Unity für die Holographic-Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="19e15-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="19e15-135">Erstellen Sie ein Hologram.</span><span class="sxs-lookup"><span data-stu-id="19e15-135">Make a hologram.</span></span>
* <span data-ttu-id="19e15-136">Sehen Sie sich ein von Ihnen vorgenommene – Hologramm an.</span><span class="sxs-lookup"><span data-stu-id="19e15-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="19e15-137">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="19e15-137">Instructions</span></span>

* <span data-ttu-id="19e15-138">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="19e15-138">Start Unity.</span></span>
* <span data-ttu-id="19e15-139">Wählen Sie **Öffnen**aus.</span><span class="sxs-lookup"><span data-stu-id="19e15-139">Select **Open**.</span></span>
* <span data-ttu-id="19e15-140">Geben Sie Location als den Ordner **Origami** ein, den Sie zuvor nicht archiviert haben.</span><span class="sxs-lookup"><span data-stu-id="19e15-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="19e15-141">Wählen Sie **Origami** , und klicken Sie auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="19e15-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="19e15-142">Da das **Origami** -Projekt keine Szene enthält, speichern Sie die leere Standard Szene in einer neuen Datei, indem Sie Folgendes verwenden: **File** / **Szene speichern als**.</span><span class="sxs-lookup"><span data-stu-id="19e15-142">Since the **Origami** project does not contain a scene, save the empty default scene to a new file using: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="19e15-143">Nennen Sie die neue Szene **Origami** , und klicken Sie auf die Schaltfläche **Speichern** .</span><span class="sxs-lookup"><span data-stu-id="19e15-143">Name the new scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-virtual-camera"></a><span data-ttu-id="19e15-144">Einrichten der virtuellen Hauptkamera</span><span class="sxs-lookup"><span data-stu-id="19e15-144">Setup the main virtual camera</span></span>

* <span data-ttu-id="19e15-145">Wählen Sie im Bereich **Hierarchie**die Option **Hauptkamera**aus.</span><span class="sxs-lookup"><span data-stu-id="19e15-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="19e15-146">Legen Sie im **Inspektor** die Transformations Position auf **0, 0, 0**fest.</span><span class="sxs-lookup"><span data-stu-id="19e15-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="19e15-147">Suchen Sie die Eigenschaft **Clear Flags** , und ändern Sie die Dropdown Liste von **Skybox** in voll **Tonfarbe**.</span><span class="sxs-lookup"><span data-stu-id="19e15-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="19e15-148">Klicken Sie auf das Feld **Hintergrund** , um eine Farbauswahl zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="19e15-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="19e15-149">Legen Sie **R, G, B und A** auf **0**fest.</span><span class="sxs-lookup"><span data-stu-id="19e15-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="19e15-150">Einrichten der Szene</span><span class="sxs-lookup"><span data-stu-id="19e15-150">Setup the scene</span></span>

* <span data-ttu-id="19e15-151">Klicken Sie im **Hierarchie Panel**auf **Erstellen** , und erstellen Sie eine **leere**.</span><span class="sxs-lookup"><span data-stu-id="19e15-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="19e15-152">Klicken Sie mit der rechten Maustaste auf das neue **gameobject** und wählen Sie umbenennen</span><span class="sxs-lookup"><span data-stu-id="19e15-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="19e15-153">Benennen Sie das gameobject in **origamicollection**um.</span><span class="sxs-lookup"><span data-stu-id="19e15-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="19e15-154">Wählen Sie im Projekt Panel im Ordner **holograms** (Objekte erweitern und holograms aus, oder Doppelklicken Sie im Projekt Panel auf den Ordner holograms):</span><span class="sxs-lookup"><span data-stu-id="19e15-154">From the **Holograms** folder in the Project Panel (expand Assets and select Holograms or double click the Holograms folder in the Project Panel):</span></span>
  * <span data-ttu-id="19e15-155">Ziehen Sie die **Phase** in die Hierarchie, um ein untergeordnetes Element von **origamicollection**zu sein.</span><span class="sxs-lookup"><span data-stu-id="19e15-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="19e15-156">Ziehen Sie **Sphere1** in die Hierarchie, um ein untergeordnetes Element von **origamicollection**zu sein.</span><span class="sxs-lookup"><span data-stu-id="19e15-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="19e15-157">Ziehen Sie **Sphere2** in die Hierarchie, um ein untergeordnetes Element von **origamicollection**zu sein.</span><span class="sxs-lookup"><span data-stu-id="19e15-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="19e15-158">Klicken Sie im Bereich **Hierarchie** mit der rechten Maustaste auf das Objekt **direktional hell** , und wählen Sie **Löschen**aus</span><span class="sxs-lookup"><span data-stu-id="19e15-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="19e15-159">Ziehen Sie aus dem Ordner **holograms** die **Beleuchtung** in das Stammverzeichnis des Bereichs **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="19e15-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="19e15-160">Wählen Sie in der **Hierarchie**die Option **origamicollection**aus.</span><span class="sxs-lookup"><span data-stu-id="19e15-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="19e15-161">Legen Sie im **Inspektor**die Transformations Position auf **0,-0,5, 2,0**fest.</span><span class="sxs-lookup"><span data-stu-id="19e15-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="19e15-162">Klicken Sie in Unity auf die **Wiedergabe** Schaltfläche, um eine Vorschau der holograms anzuzeigen</span><span class="sxs-lookup"><span data-stu-id="19e15-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="19e15-163">Die Origami-Objekte sollten im Vorschaufenster angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="19e15-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="19e15-164">Drücken **Sie** ein zweites Mal, um den Vorschaumodus zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="19e15-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="19e15-165">Exportieren des Projekts aus Unity in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="19e15-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="19e15-166">Wählen Sie in Unity **Datei > Buildeinstellungen**aus.</span><span class="sxs-lookup"><span data-stu-id="19e15-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="19e15-167">Wählen Sie in der Liste **Plattform** **universelle Windows-Plattform** aus, und klicken Sie auf **Plattform wechseln**.</span><span class="sxs-lookup"><span data-stu-id="19e15-167">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="19e15-168">Legen Sie das **SDK** auf **Universal 10** und den Buildtyp auf **D3D**fest.</span><span class="sxs-lookup"><span data-stu-id="19e15-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="19e15-169">Überprüfen Sie **Unity C# -Projekte**.</span><span class="sxs-lookup"><span data-stu-id="19e15-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="19e15-170">Klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="19e15-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="19e15-171">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="19e15-171">Click **Build**.</span></span>
* <span data-ttu-id="19e15-172">Erstellen Sie im Datei-Explorer-Fenster, das angezeigt wird, einen **neuen Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="19e15-172">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="19e15-173">Klicken Sie einfach auf den **app-Ordner**.</span><span class="sxs-lookup"><span data-stu-id="19e15-173">Single click the **App Folder**.</span></span>
* <span data-ttu-id="19e15-174">Drücken **Sie Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="19e15-174">Press **Select Folder**.</span></span>
* <span data-ttu-id="19e15-175">Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="19e15-175">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="19e15-176">Öffnen Sie den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="19e15-176">Open the **App** folder.</span></span>
* <span data-ttu-id="19e15-177">Öffnen Sie (Doppelklicken Sie auf) **Origami. sln**.</span><span class="sxs-lookup"><span data-stu-id="19e15-177">Open (double click) **Origami.sln**.</span></span>
* <span data-ttu-id="19e15-178">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x86**.</span><span class="sxs-lookup"><span data-stu-id="19e15-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="19e15-179">Klicken Sie auf den Pfeil neben der Schaltfläche Gerät, und wählen Sie **Remote Computer** aus, um die Bereitstellung über Wi-Fi durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="19e15-179">Click on the arrow next to the Device button, and select **Remote Machine** to deploy over Wi-Fi.</span></span>
  * <span data-ttu-id="19e15-180">Legen Sie die **Adresse** auf den Namen oder die IP-Adresse der hololens fest.</span><span class="sxs-lookup"><span data-stu-id="19e15-180">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="19e15-181">Wenn Sie die IP-Adresse Ihres Geräts nicht kennen, suchen Sie in den **Einstellungen > Netzwerk & Internet > Erweiterte Optionen** , oder Fragen Sie Cortana **"Hey Cortana, was ist meine IP-Adresse?"** .</span><span class="sxs-lookup"><span data-stu-id="19e15-181">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
  * <span data-ttu-id="19e15-182">Wenn die hololens über USB angefügt sind, können Sie stattdessen ein **Gerät** für die Bereitstellung über USB auswählen.</span><span class="sxs-lookup"><span data-stu-id="19e15-182">If the HoloLens is attached over USB, you may instead select **Device** to deploy over USB.</span></span>
  * <span data-ttu-id="19e15-183">Lassen Sie den **Authentifizierungsmodus** auf **Universal**festgelegt.</span><span class="sxs-lookup"><span data-stu-id="19e15-183">Leave the **Authentication Mode** set to **Universal**.</span></span>
  * <span data-ttu-id="19e15-184">Klicken Sie auf **auswählen**</span><span class="sxs-lookup"><span data-stu-id="19e15-184">Click **Select**</span></span>

* <span data-ttu-id="19e15-185">Klicken Sie auf **Debuggen > Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="19e15-185">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="19e15-186">Wenn Sie die Bereitstellung auf Ihrem Gerät zum ersten Mal durchführt, müssen Sie [es mit Visual Studio](using-visual-studio.md#pairing-your-device)koppeln.</span><span class="sxs-lookup"><span data-stu-id="19e15-186">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>

* <span data-ttu-id="19e15-187">Das Projekt Origami wird nun erstellt, in den hololens bereitgestellt und dann ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="19e15-187">The Origami project will now build, deploy to your HoloLens, and then run.</span></span>
* <span data-ttu-id="19e15-188">Platzieren Sie Ihre hololens, und sehen Sie sich an, um Ihre neuen holograms anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="19e15-188">Put on your HoloLens and look around to see your new holograms.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="19e15-189">Kapitel 2: Blick</span><span class="sxs-lookup"><span data-stu-id="19e15-189">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

<span data-ttu-id="19e15-190">In diesem Kapitel werden die ersten von drei Möglichkeiten vorgestellt, mit denen Sie mit ihren holograms interagieren [können.](gaze-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="19e15-190">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze-and-commit.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="19e15-191">Ziele</span><span class="sxs-lookup"><span data-stu-id="19e15-191">Objectives</span></span>

* <span data-ttu-id="19e15-192">Visualisieren Sie Ihren Blick mithilfe eines weltweit gesperrten Cursors.</span><span class="sxs-lookup"><span data-stu-id="19e15-192">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="19e15-193">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="19e15-193">Instructions</span></span>

* <span data-ttu-id="19e15-194">Wechseln Sie zurück zu Ihrem Unity-Projekt, und schließen Sie das Fenster mit den Buildeinstellungen, wenn es noch geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="19e15-194">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="19e15-195">Wählen Sie im **Projekt Panel**den Ordner **holograms** aus.</span><span class="sxs-lookup"><span data-stu-id="19e15-195">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="19e15-196">Ziehen Sie das **Cursor** Objekt in das **Hierarchie Panel** auf der Stamm Ebene.</span><span class="sxs-lookup"><span data-stu-id="19e15-196">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="19e15-197">Doppelklicken Sie auf das **Cursor** Objekt, um es genauer zu betrachten.</span><span class="sxs-lookup"><span data-stu-id="19e15-197">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="19e15-198">Klicken Sie im Projekt Panel mit der rechten Maustaste auf den Ordner **Scripts** .</span><span class="sxs-lookup"><span data-stu-id="19e15-198">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="19e15-199">Klicken Sie auf das Untermenü **Erstellen** .</span><span class="sxs-lookup"><span data-stu-id="19e15-199">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="19e15-200">Wählen Sie  **C# Skript**aus.</span><span class="sxs-lookup"><span data-stu-id="19e15-200">Select **C# Script**.</span></span>
* <span data-ttu-id="19e15-201">Nennen Sie das Skript **worldcursor**.</span><span class="sxs-lookup"><span data-stu-id="19e15-201">Name the script **WorldCursor**.</span></span> <span data-ttu-id="19e15-202">Hinweis: bei dem Namen wird die Groß-/Kleinschreibung beachtet.</span><span class="sxs-lookup"><span data-stu-id="19e15-202">Note: The name is case-sensitive.</span></span> <span data-ttu-id="19e15-203">Sie müssen die Erweiterung ". cs" nicht hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="19e15-203">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="19e15-204">Wählen Sie im **Hierarchie Panel**das **Cursor** Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="19e15-204">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="19e15-205">Verschieben Sie das **worldcursor** -Skript per Drag & amp; Drop in den Bereich **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="19e15-205">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="19e15-206">Doppelklicken Sie auf das Skript **worldcursor** , um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="19e15-206">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="19e15-207">Fügen Sie diesen Code in **WorldCursor.cs** ein, und **Speichern Sie alle**.</span><span class="sxs-lookup"><span data-stu-id="19e15-207">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

* <span data-ttu-id="19e15-208">Erstellen Sie die APP aus dem **Datei > den Buildeinstellungen**neu.</span><span class="sxs-lookup"><span data-stu-id="19e15-208">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="19e15-209">Kehren Sie zur Visual Studio-Projekt Mappe zurück, die Sie zuvor für die Bereitstellung in hololens verwendet haben</span><span class="sxs-lookup"><span data-stu-id="19e15-209">Return to the Visual Studio solution previously used to deploy to your HoloLens.</span></span>
* <span data-ttu-id="19e15-210">Wählen Sie bei entsprechender Aufforderung "alle neu laden" aus.</span><span class="sxs-lookup"><span data-stu-id="19e15-210">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="19e15-211">Klicken Sie auf **Debuggen > Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="19e15-211">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="19e15-212">Sehen Sie sich nun die Szene an, und sehen Sie, wie der Cursor mit der Form von Objekten interagiert.</span><span class="sxs-lookup"><span data-stu-id="19e15-212">Now look around the scene and notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="19e15-213">Kapitel 3: Gesten</span><span class="sxs-lookup"><span data-stu-id="19e15-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

<span data-ttu-id="19e15-214">In diesem Kapitel wird die Unterstützung für [Gesten](gaze-and-commit.md#composite-gestures)hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="19e15-214">In this chapter, we'll add support for [gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="19e15-215">Wenn der Benutzer eine Papierkugel auswählt, wird die Kugel durch das Aktivieren der Schwerkraft mit der Physik-Engine von Unity erreicht.</span><span class="sxs-lookup"><span data-stu-id="19e15-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="19e15-216">Ziele</span><span class="sxs-lookup"><span data-stu-id="19e15-216">Objectives</span></span>

* <span data-ttu-id="19e15-217">Steuern Sie Ihre Hologramme mit der SELECT-Geste.</span><span class="sxs-lookup"><span data-stu-id="19e15-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="19e15-218">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="19e15-218">Instructions</span></span>

<span data-ttu-id="19e15-219">Wir beginnen mit der Erstellung eines Skripts und können dann die SELECT-Geste erkennen.</span><span class="sxs-lookup"><span data-stu-id="19e15-219">We'll start by creating a script then can detect the Select gesture.</span></span>

* <span data-ttu-id="19e15-220">Erstellen Sie im Ordner **Scripts** ein Skript mit dem Namen " **gazegesturemanager**".</span><span class="sxs-lookup"><span data-stu-id="19e15-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="19e15-221">Ziehen Sie das Skript " **gazegesturemanager** " auf das Objekt " **origamicollection** " in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="19e15-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="19e15-222">Öffnen Sie das Skript " **gazegesturemanager** " in Visual Studio, und fügen Sie den folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="19e15-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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

* <span data-ttu-id="19e15-223">Erstellen Sie ein weiteres Skript im Ordner "Scripts", diesmal mit dem Namen **spherecommands**.</span><span class="sxs-lookup"><span data-stu-id="19e15-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="19e15-224">Erweitern Sie das Objekt **origamicollection** in der Hierarchie Ansicht.</span><span class="sxs-lookup"><span data-stu-id="19e15-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="19e15-225">Ziehen Sie das **spherecommands** -Skript auf das **Sphere1** -Objekt im Hierarchie Panel.</span><span class="sxs-lookup"><span data-stu-id="19e15-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="19e15-226">Ziehen Sie das **spherecommands** -Skript auf das **Sphere2** -Objekt im Hierarchie Panel.</span><span class="sxs-lookup"><span data-stu-id="19e15-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="19e15-227">Öffnen Sie das Skript in Visual Studio zur Bearbeitung, und ersetzen Sie den Standard Code durch den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="19e15-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="19e15-228">Exportieren, erstellen und Bereitstellen der app in ihren hololens.</span><span class="sxs-lookup"><span data-stu-id="19e15-228">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="19e15-229">Sehen Sie sich einen der Bereiche an.</span><span class="sxs-lookup"><span data-stu-id="19e15-229">Look at one of the spheres.</span></span>
* <span data-ttu-id="19e15-230">Führen Sie die SELECT-Geste aus, und beobachten Sie den unteren Bereich der Kugel.</span><span class="sxs-lookup"><span data-stu-id="19e15-230">Perform the select gesture and watch the sphere drop onto the surface below.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="19e15-231">Kapitel 4: Stimme</span><span class="sxs-lookup"><span data-stu-id="19e15-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

<span data-ttu-id="19e15-232">In diesem Kapitel fügen wir die Unterstützung für zwei [Sprachbefehle](voice-input.md)hinzu: "Reset World", um die gelöschten Bereiche an ihren ursprünglichen Speicherort zurückzugeben, und "Drop Sphere", um die Kugel zu verlieren.</span><span class="sxs-lookup"><span data-stu-id="19e15-232">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to return the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="19e15-233">Ziele</span><span class="sxs-lookup"><span data-stu-id="19e15-233">Objectives</span></span>

* <span data-ttu-id="19e15-234">Fügen Sie Sprachbefehle hinzu, die immer im Hintergrund lauschen.</span><span class="sxs-lookup"><span data-stu-id="19e15-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="19e15-235">Erstellen Sie ein – Hologramm, das auf einen Voice-Befehl reagiert.</span><span class="sxs-lookup"><span data-stu-id="19e15-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="19e15-236">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="19e15-236">Instructions</span></span>

* <span data-ttu-id="19e15-237">Erstellen Sie **im Ordner Skripts ein** Skript mit dem Namen " **Redner-Manager**".</span><span class="sxs-lookup"><span data-stu-id="19e15-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="19e15-238">Ziehen Sie das **sprach-Manager** -Skript auf das **origamicollection** -Objekt in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="19e15-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="19e15-239">Öffnen Sie das **sprach-Manager** -Skript in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="19e15-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="19e15-240">Kopieren Sie diesen Code, und fügen Sie ihn in **SpeechManager.cs** ein. **Speichern Sie alle**</span><span class="sxs-lookup"><span data-stu-id="19e15-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="19e15-241">Öffnen Sie das **spherecommands** -Skript in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="19e15-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="19e15-242">Aktualisieren Sie das Skript wie folgt:</span><span class="sxs-lookup"><span data-stu-id="19e15-242">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="19e15-243">Exportieren, erstellen und Bereitstellen der app in ihren hololens.</span><span class="sxs-lookup"><span data-stu-id="19e15-243">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="19e15-244">Sehen Sie sich einen der Bereiche an, und sagen Sie "**Drop Sphere**".</span><span class="sxs-lookup"><span data-stu-id="19e15-244">Look at one of the spheres, and say "**Drop Sphere**".</span></span>
* <span data-ttu-id="19e15-245">Sagen Sie "**Welt zurücksetzen**", um Sie wieder an Ihre ursprünglichen Positionen zu bringen.</span><span class="sxs-lookup"><span data-stu-id="19e15-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="19e15-246">Kapitel 5: räumlicher Sound</span><span class="sxs-lookup"><span data-stu-id="19e15-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

<span data-ttu-id="19e15-247">In diesem Kapitel werden wir der App Musik hinzufügen und dann bei bestimmten Aktionen Soundeffekte auslöst.</span><span class="sxs-lookup"><span data-stu-id="19e15-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="19e15-248">Wir verwenden den [räumlichen Ton](spatial-sound.md) , um Klänge an einem bestimmten Speicherort im 3D-Raum zu geben.</span><span class="sxs-lookup"><span data-stu-id="19e15-248">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="19e15-249">Ziele</span><span class="sxs-lookup"><span data-stu-id="19e15-249">Objectives</span></span>

* <span data-ttu-id="19e15-250">Hören Sie holograms in ihrer Welt.</span><span class="sxs-lookup"><span data-stu-id="19e15-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="19e15-251">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="19e15-251">Instructions</span></span>

* <span data-ttu-id="19e15-252">Wählen Sie in Unity im oberen Menü **> Projekteinstellungen > Audiodatei bearbeiten** aus.</span><span class="sxs-lookup"><span data-stu-id="19e15-252">In Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="19e15-253">Suchen Sie im Inspektor-Panel auf der rechten Seite die Einstellung für das **spatializer-Plug** -in, und wählen Sie **MS HRTF spatializer**aus.</span><span class="sxs-lookup"><span data-stu-id="19e15-253">In the Inspector Panel on the right side, find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="19e15-254">Ziehen Sie das **Ambiente** -Objekt aus dem Ordner **holograms** im Projekt Panel auf das Objekt **origamicollection** im Bereich Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="19e15-254">From the **Holograms** folder in the Project panel, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="19e15-255">Wählen Sie **origamicollection** aus, und suchen Sie im Inspektor-Panel die Komponente **Audioquelle** .</span><span class="sxs-lookup"><span data-stu-id="19e15-255">Select **OrigamiCollection** and find the **Audio Source** component in the Inspector panel.</span></span> <span data-ttu-id="19e15-256">Ändern Sie die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="19e15-256">Change these properties:</span></span>
  * <span data-ttu-id="19e15-257">Überprüfen Sie die **spatialize** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="19e15-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="19e15-258">Überprüfen Sie die wieder **Gabe bei wach**.</span><span class="sxs-lookup"><span data-stu-id="19e15-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="19e15-259">Ändern Sie **räumliche Blend** in **3D** , indem Sie den Schieberegler nach rechts ziehen.</span><span class="sxs-lookup"><span data-stu-id="19e15-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span> <span data-ttu-id="19e15-260">Wenn Sie den Schieberegler verschieben, sollte der Wert von 0 in 1 geändert werden.</span><span class="sxs-lookup"><span data-stu-id="19e15-260">The value should change from 0 to 1 when you move the slider.</span></span>
  * <span data-ttu-id="19e15-261">Überprüfen Sie die **Loop** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="19e15-261">Check the **Loop** property.</span></span>
  * <span data-ttu-id="19e15-262">Erweitern Sie **3D-Sound Einstellungen**, und geben Sie **0,1** für die **Doppler-Ebene**ein.</span><span class="sxs-lookup"><span data-stu-id="19e15-262">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="19e15-263">Legen Sie **volumenrolloff** auf **logarithmische Rolloff**fest.</span><span class="sxs-lookup"><span data-stu-id="19e15-263">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="19e15-264">Legen Sie **Max Distance** auf **20**fest.</span><span class="sxs-lookup"><span data-stu-id="19e15-264">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="19e15-265">Erstellen Sie im Ordner **Scripts** ein Skript mit dem Namen " **spheresounds**".</span><span class="sxs-lookup"><span data-stu-id="19e15-265">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="19e15-266">Ziehen Sie **spheresounds** per Drag & Drop auf die Objekte **Sphere1** und **Sphere2** in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="19e15-266">Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="19e15-267">Öffnen Sie " **spheresounds** " in Visual Studio, aktualisieren Sie den folgenden Code, und **Speichern Sie alle**.</span><span class="sxs-lookup"><span data-stu-id="19e15-267">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="19e15-268">Speichern Sie das Skript, und kehren Sie zu Unity zurück.</span><span class="sxs-lookup"><span data-stu-id="19e15-268">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="19e15-269">Exportieren, erstellen und Bereitstellen der app in ihren hololens.</span><span class="sxs-lookup"><span data-stu-id="19e15-269">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="19e15-270">Bewegen Sie sich näher und weiter von der Stufe aus, und schalten Sie die Seite auf die Seite, um die Geräusche zu ändern.</span><span class="sxs-lookup"><span data-stu-id="19e15-270">Move closer and further from the Stage and turn side-to-side to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="19e15-271">Kapitel 6: räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="19e15-271">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

<span data-ttu-id="19e15-272">Nun verwenden wir die [räumliche Zuordnung](spatial-mapping.md) , um das Spiel Board in einem realen Objekt in der realen Welt zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="19e15-272">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="19e15-273">Ziele</span><span class="sxs-lookup"><span data-stu-id="19e15-273">Objectives</span></span>

* <span data-ttu-id="19e15-274">Bringen Sie Ihre reale Welt in die virtuelle Welt.</span><span class="sxs-lookup"><span data-stu-id="19e15-274">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="19e15-275">Platzieren Sie Ihre Hologramme, wo Sie für Sie am wichtigsten sind.</span><span class="sxs-lookup"><span data-stu-id="19e15-275">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="19e15-276">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="19e15-276">Instructions</span></span>

* <span data-ttu-id="19e15-277">Klicken Sie in Unity im Projekt Panel auf den Ordner **holograms** .</span><span class="sxs-lookup"><span data-stu-id="19e15-277">In Unity, click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="19e15-278">Ziehen Sie das Objekt für die **räumliche Zuordnung** in den Stamm der **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="19e15-278">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="19e15-279">Klicken Sie in der Hierarchie auf das **räumliche Mapping** -Objekt.</span><span class="sxs-lookup"><span data-stu-id="19e15-279">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="19e15-280">Ändern Sie im **Inspektor-Panel**die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="19e15-280">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="19e15-281">Aktivieren Sie das Kontrollkästchen **visuelle Meshes zeichnen** .</span><span class="sxs-lookup"><span data-stu-id="19e15-281">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="19e15-282">Suchen Sie das **Zeichnungs Material** , und klicken Sie auf den Kreis rechts.</span><span class="sxs-lookup"><span data-stu-id="19e15-282">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="19e15-283">Geben Sie im Feld oben den Text "**Draht Modell**" in das Suchfeld ein.</span><span class="sxs-lookup"><span data-stu-id="19e15-283">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="19e15-284">Klicken Sie auf das Ergebnis, und schließen Sie das Fenster.</span><span class="sxs-lookup"><span data-stu-id="19e15-284">Click on the result and then close the window.</span></span> <span data-ttu-id="19e15-285">Wenn Sie dies tun, sollte der Wert für Zeichnungs Material auf Wireframe festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="19e15-285">When you do this, the value for Draw Material should get set to Wireframe.</span></span>
* <span data-ttu-id="19e15-286">Exportieren, erstellen und Bereitstellen der app in ihren hololens.</span><span class="sxs-lookup"><span data-stu-id="19e15-286">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="19e15-287">Wenn die app ausgeführt wird, überlagert ein Draht Modell-Mesh ihre reale Welt.</span><span class="sxs-lookup"><span data-stu-id="19e15-287">When the app runs, a wireframe mesh will overlay your real world.</span></span>
* <span data-ttu-id="19e15-288">Sehen Sie sich an, wie sich eine parallele Kugel auf der Ebene befindet und auf den Boden zeigt.</span><span class="sxs-lookup"><span data-stu-id="19e15-288">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="19e15-289">Nun zeigen wir Ihnen, wie Sie die origamicollection an einen neuen Speicherort verschieben:</span><span class="sxs-lookup"><span data-stu-id="19e15-289">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="19e15-290">Erstellen Sie im Ordner **Scripts** ein Skript mit dem Namen " **taptoplaceparent**".</span><span class="sxs-lookup"><span data-stu-id="19e15-290">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="19e15-291">Erweitern Sie in der- **Hierarchie**die **origamicollection** , und wählen Sie das **Stage** -Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="19e15-291">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="19e15-292">Ziehen Sie das Skript **taptoplaceparent** auf das Stage-Objekt.</span><span class="sxs-lookup"><span data-stu-id="19e15-292">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="19e15-293">Öffnen Sie das Skript " **taptoplaceparent** " in Visual Studio, und aktualisieren Sie es wie folgt:</span><span class="sxs-lookup"><span data-stu-id="19e15-293">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="19e15-294">Exportieren, erstellen und Bereitstellen der app.</span><span class="sxs-lookup"><span data-stu-id="19e15-294">Export, build and deploy the app.</span></span>
* <span data-ttu-id="19e15-295">Jetzt sollten Sie nun in der Lage sein, das Spiel an einem bestimmten Speicherort zu platzieren, indem Sie es mit der SELECT-Geste anordnen und dann an eine neue Stelle verschieben und die Auswahl Geste erneut verwenden.</span><span class="sxs-lookup"><span data-stu-id="19e15-295">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="chapter-7---holographic-fun"></a><span data-ttu-id="19e15-296">Kapitel 7: Holographic Fun</span><span class="sxs-lookup"><span data-stu-id="19e15-296">Chapter 7 - Holographic fun</span></span>

### <a name="objectives"></a><span data-ttu-id="19e15-297">Ziele</span><span class="sxs-lookup"><span data-stu-id="19e15-297">Objectives</span></span>

* <span data-ttu-id="19e15-298">Zeigen Sie den Einstieg in eine Holographic-Unterwelt an.</span><span class="sxs-lookup"><span data-stu-id="19e15-298">Reveal the entrance to a holographic underworld.</span></span>

### <a name="instructions"></a><span data-ttu-id="19e15-299">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="19e15-299">Instructions</span></span>

<span data-ttu-id="19e15-300">Nun zeigen wir Ihnen, wie Sie die Holographic-Unterwelt entdecken:</span><span class="sxs-lookup"><span data-stu-id="19e15-300">Now we'll show you how to uncover the holographic underworld:</span></span>

* <span data-ttu-id="19e15-301">Aus dem Ordner " **holograms** " im Projekt Panel:</span><span class="sxs-lookup"><span data-stu-id="19e15-301">From the **Holograms** folder in the Project Panel:</span></span>
  * <span data-ttu-id="19e15-302">Ziehen Sie **Underworld** in die Hierarchie, um ein untergeordnetes Element von **origamicollection**zu sein.</span><span class="sxs-lookup"><span data-stu-id="19e15-302">Drag **Underworld** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="19e15-303">Erstellen Sie im Ordner **Scripts** ein Skript mit dem Namen **hittarget**.</span><span class="sxs-lookup"><span data-stu-id="19e15-303">In the **Scripts** folder, create a script named **HitTarget**.</span></span>
* <span data-ttu-id="19e15-304">Erweitern Sie in der- **Hierarchie**die " **origamicollection**".</span><span class="sxs-lookup"><span data-stu-id="19e15-304">In the **Hierarchy**, expand the **OrigamiCollection**.</span></span>
* <span data-ttu-id="19e15-305">Erweitern Sie das **Stage** -Objekt, und wählen Sie das **Ziel** Objekt (blauer Lüfter) aus.</span><span class="sxs-lookup"><span data-stu-id="19e15-305">Expand the **Stage** object and select the **Target** object (blue fan).</span></span>
* <span data-ttu-id="19e15-306">Ziehen **Sie das hittarget** -Skript auf das **Ziel** Objekt.</span><span class="sxs-lookup"><span data-stu-id="19e15-306">Drag the **HitTarget** script onto the **Target** object.</span></span>
* <span data-ttu-id="19e15-307">Öffnen Sie das **hittarget** -Skript in Visual Studio, und aktualisieren Sie es wie folgt:</span><span class="sxs-lookup"><span data-stu-id="19e15-307">Open the **HitTarget** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="19e15-308">Wählen Sie in Unity das **Ziel** Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="19e15-308">In Unity, select the **Target** object.</span></span>
* <span data-ttu-id="19e15-309">Zwei öffentliche Eigenschaften sind jetzt für die **Treffer Ziel** Komponente sichtbar, und Sie müssen auf Objekte in unserer Szene verweisen:</span><span class="sxs-lookup"><span data-stu-id="19e15-309">Two public properties are now visible on the **Hit Target** component and need to reference objects in our scene:</span></span>
  * <span data-ttu-id="19e15-310">Ziehen Sie die Option " **Underworld** " aus dem Bereich **Hierarchie** in **die Eigenschaft für** die **Ziel** Komponente.</span><span class="sxs-lookup"><span data-stu-id="19e15-310">Drag **Underworld** from the **Hierarchy** panel to the **Underworld** property on the **Hit Target** component.</span></span>
  * <span data-ttu-id="19e15-311">Ziehen Sie **Phase** aus dem Bereich **Hierarchie** auf das **Objekt, um** die Eigenschaft für die **Treffer Ziel** Komponente auszublenden.</span><span class="sxs-lookup"><span data-stu-id="19e15-311">Drag **Stage** from the **Hierarchy** panel to the **Object to Hide** property on the **Hit Target** component.</span></span>
* <span data-ttu-id="19e15-312">Exportieren, erstellen und Bereitstellen der app.</span><span class="sxs-lookup"><span data-stu-id="19e15-312">Export, build and deploy the app.</span></span>
* <span data-ttu-id="19e15-313">Platzieren Sie die Origami-Auflistung auf der Etage, und verwenden Sie dann die Aktion auswählen, um einen Kugel Ablage Vorgang zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="19e15-313">Place the Origami Collection on the floor, and then use the Select gesture to make a sphere drop.</span></span>
* <span data-ttu-id="19e15-314">Wenn die Kugel auf das Ziel (blauer Lüfter) trifft, tritt eine Explosion auf.</span><span class="sxs-lookup"><span data-stu-id="19e15-314">When the sphere hits the target (blue fan), an explosion will occur.</span></span> <span data-ttu-id="19e15-315">Die Sammlung wird ausgeblendet, und ein Loch in der Unterwelt wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="19e15-315">The collection will be hidden and a hole to the underworld will appear.</span></span>

## <a name="the-end"></a><span data-ttu-id="19e15-316">Das Ende</span><span class="sxs-lookup"><span data-stu-id="19e15-316">The end</span></span>

<span data-ttu-id="19e15-317">Und das ist das Ende dieses Tutorials!</span><span class="sxs-lookup"><span data-stu-id="19e15-317">And that's the end of this tutorial!</span></span>

<span data-ttu-id="19e15-318">Sie haben Folgendes gelernt:</span><span class="sxs-lookup"><span data-stu-id="19e15-318">You learned:</span></span>

* <span data-ttu-id="19e15-319">Erstellen einer Holographic-app in Unity.</span><span class="sxs-lookup"><span data-stu-id="19e15-319">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="19e15-320">Verwendung von Blick, Bewegung, Stimme, Sound und räumlicher Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="19e15-320">How to make use of gaze, gesture, voice, sound, and spatial mapping.</span></span>
* <span data-ttu-id="19e15-321">Erfahren Sie, wie Sie eine APP mit Visual Studio erstellen und bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="19e15-321">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="19e15-322">Nun können Sie mit der Erstellung Ihrer eigenen Holographic-Benutzeroberflächen beginnen!</span><span class="sxs-lookup"><span data-stu-id="19e15-322">You are now ready to start creating your own holographic experience!</span></span>

## <a name="see-also"></a><span data-ttu-id="19e15-323">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="19e15-323">See also</span></span>

* [<span data-ttu-id="19e15-324">Grundlagen 101 e: vervollständigen eines Projekts mit Emulator</span><span class="sxs-lookup"><span data-stu-id="19e15-324">MR Basics 101E: Complete project with emulator</span></span>](holograms-101e.md)
* [<span data-ttu-id="19e15-325">Anvisieren</span><span class="sxs-lookup"><span data-stu-id="19e15-325">Gaze</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="19e15-326">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="19e15-326">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="19e15-327">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="19e15-327">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="19e15-328">Raumklang</span><span class="sxs-lookup"><span data-stu-id="19e15-328">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="19e15-329">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="19e15-329">Spatial mapping</span></span>](spatial-mapping.md)
