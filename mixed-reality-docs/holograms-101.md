---
title: Grundlagen 101-Projekt mit Gerät abschließen
description: Befolgen Sie diese exemplarische Vorgehensweise zum Programmieren mit Unity, Visual Studio und hololens, um die Grundlagen von Windows Mixed Reality kennenzulernen.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Gemischte Realität, Windows Mixed Reality, hololens, Hologram, Academy, Tutorial
ms.openlocfilehash: 043ffac8f30a4e29586478b5dca6ecccc2b5afd3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524027"
---
>[!NOTE]
><span data-ttu-id="d02a6-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="d02a6-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="d02a6-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="d02a6-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="d02a6-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d02a6-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="d02a6-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="d02a6-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="d02a6-108">Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="d02a6-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="d02a6-109">Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="d02a6-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101-complete-project-with-device"></a><span data-ttu-id="d02a6-110">Grundlagen 101: Projekt mit Gerät vervollständigen</span><span class="sxs-lookup"><span data-stu-id="d02a6-110">MR Basics 101: Complete project with device</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

<span data-ttu-id="d02a6-111">In diesem Tutorial werden Sie durch ein vollständiges Projekt geführt, das in Unity integriert ist, das grundlegende Windows Mixed Reality-Features in hololens veranschaulicht, einschließlich [Blick](gaze.md), [Gesten](gestures.md), [Spracheingabe](voice-input.md), [räumlichem Sound](spatial-sound.md) und [räumlicher Zuordnung](spatial-mapping.md) . .</span><span class="sxs-lookup"><span data-stu-id="d02a6-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span>

<span data-ttu-id="d02a6-112">Das Tutorial dauert ungefähr 1 Stunde.</span><span class="sxs-lookup"><span data-stu-id="d02a6-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="d02a6-113">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="d02a6-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d02a6-114">Natürlich</span><span class="sxs-lookup"><span data-stu-id="d02a6-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="d02a6-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d02a6-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d02a6-116"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="d02a6-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="d02a6-117">Grundlagen 101: Projekt mit Gerät vervollständigen</span><span class="sxs-lookup"><span data-stu-id="d02a6-117">MR Basics 101: Complete project with device</span></span></td><td style="text-align: center;"> <span data-ttu-id="d02a6-118">✔️</span><span class="sxs-lookup"><span data-stu-id="d02a6-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="d02a6-119">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="d02a6-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="d02a6-120">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="d02a6-120">Prerequisites</span></span>

* <span data-ttu-id="d02a6-121">Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md)konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="d02a6-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="d02a6-122">Ein hololens-Gerät, das [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode)ist.</span><span class="sxs-lookup"><span data-stu-id="d02a6-122">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="d02a6-123">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="d02a6-123">Project files</span></span>

* <span data-ttu-id="d02a6-124">Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) , die für das Projekt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="d02a6-124">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="d02a6-125"> Erfordert Unity 2017,2 oder höher.</span><span class="sxs-lookup"><span data-stu-id="d02a6-125"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="d02a6-126">Wenn Sie weiterhin Unity 5,6-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="d02a6-126">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="d02a6-127">Wenn Sie weiterhin Unity 5,5-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="d02a6-127">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="d02a6-128">Wenn Sie weiterhin Unity 5,4-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="d02a6-128">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="d02a6-129">Deinstallieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht zugänglichen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="d02a6-129">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="d02a6-130">Behalten Sie den Ordnernamen **Origami**bei.</span><span class="sxs-lookup"><span data-stu-id="d02a6-130">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="d02a6-131">Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="d02a6-131">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="d02a6-132">Kapitel 1: "Holo" World</span><span class="sxs-lookup"><span data-stu-id="d02a6-132">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

<span data-ttu-id="d02a6-133">In diesem Kapitel richten wir das erste Unity-Projekt ein und durchlaufen den Build-und Bereitstellungs Prozess.</span><span class="sxs-lookup"><span data-stu-id="d02a6-133">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="d02a6-134">Ziele</span><span class="sxs-lookup"><span data-stu-id="d02a6-134">Objectives</span></span>

* <span data-ttu-id="d02a6-135">Einrichten von Unity für die Holographic-Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="d02a6-135">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="d02a6-136">Erstellen Sie ein Hologram.</span><span class="sxs-lookup"><span data-stu-id="d02a6-136">Make a hologram.</span></span>
* <span data-ttu-id="d02a6-137">Sehen Sie sich ein von Ihnen vorgenommene – Hologramm an.</span><span class="sxs-lookup"><span data-stu-id="d02a6-137">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="d02a6-138">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="d02a6-138">Instructions</span></span>

* <span data-ttu-id="d02a6-139">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="d02a6-139">Start Unity.</span></span>
* <span data-ttu-id="d02a6-140">Wählen Sie **Öffnen**aus.</span><span class="sxs-lookup"><span data-stu-id="d02a6-140">Select **Open**.</span></span>
* <span data-ttu-id="d02a6-141">Geben Sie Location als den Ordner **Origami** ein, den Sie zuvor nicht archiviert haben.</span><span class="sxs-lookup"><span data-stu-id="d02a6-141">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="d02a6-142">Wählen Sie **Origami** , und klicken Sie auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="d02a6-142">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="d02a6-143">Da das **Origami** -Projekt keine Szene enthält, speichern Sie die leere Standard Szene mit folgenden Aktionen in einer neuen Datei: Datei / **Speichern**unter.</span><span class="sxs-lookup"><span data-stu-id="d02a6-143">Since the **Origami** project does not contain a scene, save the empty default scene to a new file using: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="d02a6-144">Nennen Sie die neue Szene **Origami** , und klicken Sie auf die Schaltfläche **Speichern** .</span><span class="sxs-lookup"><span data-stu-id="d02a6-144">Name the new scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-virtual-camera"></a><span data-ttu-id="d02a6-145">Einrichten der virtuellen Hauptkamera</span><span class="sxs-lookup"><span data-stu-id="d02a6-145">Setup the main virtual camera</span></span>

* <span data-ttu-id="d02a6-146">Wählen Sie im Bereich **Hierarchie**die Option **Hauptkamera**aus.</span><span class="sxs-lookup"><span data-stu-id="d02a6-146">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="d02a6-147">Legen Sie im **Inspektor** die Transformations Position auf **0, 0, 0**fest.</span><span class="sxs-lookup"><span data-stu-id="d02a6-147">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="d02a6-148">Suchen Sie die Eigenschaft **Clear Flags** , und ändern Sie die Dropdown Liste von  **Skybox** in voll Tonfarbe.</span><span class="sxs-lookup"><span data-stu-id="d02a6-148">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="d02a6-149">Klicken Sie auf das Feld **Hintergrund** , um eine Farbauswahl zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="d02a6-149">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="d02a6-150">Legen Sie **R, G, B und A** auf **0**fest.</span><span class="sxs-lookup"><span data-stu-id="d02a6-150">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="d02a6-151">Einrichten der Szene</span><span class="sxs-lookup"><span data-stu-id="d02a6-151">Setup the scene</span></span>

* <span data-ttu-id="d02a6-152">Klicken Sie im **Hierarchie Panel**auf **Erstellen** , und erstellen Sie eine **leere**.</span><span class="sxs-lookup"><span data-stu-id="d02a6-152">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="d02a6-153">Klicken Sie mit der rechten Maustaste auf das neue **gameobject** und wählen Sie umbenennen</span><span class="sxs-lookup"><span data-stu-id="d02a6-153">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="d02a6-154">Benennen Sie das gameobject in **origamicollection**um.</span><span class="sxs-lookup"><span data-stu-id="d02a6-154">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="d02a6-155">Wählen Sie im Projekt Panel im Ordner **holograms** (Objekte erweitern und holograms aus, oder Doppelklicken Sie im Projekt Panel auf den Ordner holograms):</span><span class="sxs-lookup"><span data-stu-id="d02a6-155">From the **Holograms** folder in the Project Panel (expand Assets and select Holograms or double click the Holograms folder in the Project Panel):</span></span>
  * <span data-ttu-id="d02a6-156">Ziehen Sie die **Phase** in die Hierarchie, um ein untergeordnetes Element von **origamicollection**zu sein.</span><span class="sxs-lookup"><span data-stu-id="d02a6-156">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="d02a6-157">Ziehen Sie **Sphere1** in die Hierarchie, um ein untergeordnetes Element von **origamicollection**zu sein.</span><span class="sxs-lookup"><span data-stu-id="d02a6-157">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="d02a6-158">Ziehen Sie **Sphere2** in die Hierarchie, um ein untergeordnetes Element von **origamicollection**zu sein.</span><span class="sxs-lookup"><span data-stu-id="d02a6-158">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="d02a6-159">Klicken Sie im Bereich **Hierarchie** mit der rechten Maustaste auf das Objekt **direktional hell** , und wählen Sie **Löschen**aus</span><span class="sxs-lookup"><span data-stu-id="d02a6-159">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="d02a6-160">Ziehen Sie aus dem Ordner **holograms** die **Beleuchtung** in das Stammverzeichnis des Bereichs **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="d02a6-160">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="d02a6-161">Wählen Sie in der **Hierarchie**die Option **origamicollection**aus.</span><span class="sxs-lookup"><span data-stu-id="d02a6-161">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="d02a6-162">Legen Sie im **Inspektor**die Transformations Position auf **0,-0,5, 2,0**fest.</span><span class="sxs-lookup"><span data-stu-id="d02a6-162">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="d02a6-163">Klicken Sie in Unity auf die **Wiedergabe** Schaltfläche, um eine Vorschau der holograms anzuzeigen</span><span class="sxs-lookup"><span data-stu-id="d02a6-163">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="d02a6-164">Die Origami-Objekte sollten im Vorschaufenster angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d02a6-164">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="d02a6-165">Drücken **Sie** ein zweites Mal, um den Vorschaumodus zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="d02a6-165">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="d02a6-166">Exportieren des Projekts aus Unity in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d02a6-166">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="d02a6-167">Wählen Sie in Unity **Datei >** Buildeinstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="d02a6-167">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="d02a6-168">Wählen Sie in der Liste **Plattform** **universelle Windows-Plattform** aus, und klicken Sie auf **Plattform wechseln**.</span><span class="sxs-lookup"><span data-stu-id="d02a6-168">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="d02a6-169">Legen Sie das **SDK** auf **Universal 10** und den Buildtyp auf **D3D**fest.</span><span class="sxs-lookup"><span data-stu-id="d02a6-169">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="d02a6-170">Überprüfen Sie **Unity C# -Projekte**.</span><span class="sxs-lookup"><span data-stu-id="d02a6-170">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="d02a6-171">Klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="d02a6-171">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="d02a6-172">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="d02a6-172">Click **Build**.</span></span>
* <span data-ttu-id="d02a6-173">Erstellen Sie im Datei-Explorer-Fenster, das angezeigt wird, einen **neuen Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="d02a6-173">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="d02a6-174">Klicken Sie einfach auf den **app-Ordner**.</span><span class="sxs-lookup"><span data-stu-id="d02a6-174">Single click the **App Folder**.</span></span>
* <span data-ttu-id="d02a6-175">Drücken **Sie Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="d02a6-175">Press **Select Folder**.</span></span>
* <span data-ttu-id="d02a6-176">Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d02a6-176">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="d02a6-177">Öffnen Sie den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="d02a6-177">Open the **App** folder.</span></span>
* <span data-ttu-id="d02a6-178">Öffnen Sie (Doppelklicken Sie auf) **Origami. sln**.</span><span class="sxs-lookup"><span data-stu-id="d02a6-178">Open (double click) **Origami.sln**.</span></span>
* <span data-ttu-id="d02a6-179">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x86**.</span><span class="sxs-lookup"><span data-stu-id="d02a6-179">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="d02a6-180">Klicken Sie auf den Pfeil neben der Schaltfläche Gerät, und wählen Sie **Remote Computer** aus, um die Bereitstellung über Wi-Fi durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="d02a6-180">Click on the arrow next to the Device button, and select **Remote Machine** to deploy over Wi-Fi.</span></span>
  * <span data-ttu-id="d02a6-181">Legen Sie die **Adresse** auf den Namen oder die IP-Adresse der hololens fest.</span><span class="sxs-lookup"><span data-stu-id="d02a6-181">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="d02a6-182">Wenn Sie die IP-Adresse Ihres Geräts nicht kennen, suchen Sie in den **Einstellungen > Netzwerk & Internet > Erweiterte Optionen** , oder Fragen Sie Cortana **"Hey Cortana, was ist meine IP-Adresse?"** .</span><span class="sxs-lookup"><span data-stu-id="d02a6-182">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
  * <span data-ttu-id="d02a6-183">Wenn die hololens über USB angefügt sind, können Sie stattdessen ein **Gerät** für die Bereitstellung über USB auswählen.</span><span class="sxs-lookup"><span data-stu-id="d02a6-183">If the HoloLens is attached over USB, you may instead select **Device** to deploy over USB.</span></span>
  * <span data-ttu-id="d02a6-184">Lassen Sie den **Authentifizierungsmodus** auf **Universal**festgelegt.</span><span class="sxs-lookup"><span data-stu-id="d02a6-184">Leave the **Authentication Mode** set to **Universal**.</span></span>
  * <span data-ttu-id="d02a6-185">Klicken Sie auf **auswählen**</span><span class="sxs-lookup"><span data-stu-id="d02a6-185">Click **Select**</span></span>

* <span data-ttu-id="d02a6-186">Klicken Sie auf **Debuggen > Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="d02a6-186">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="d02a6-187">Wenn Sie die Bereitstellung auf Ihrem Gerät zum ersten Mal durchführt, müssen Sie [es mit Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen))koppeln.</span><span class="sxs-lookup"><span data-stu-id="d02a6-187">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).</span></span>

* <span data-ttu-id="d02a6-188">Das Projekt Origami wird nun erstellt, in den hololens bereitgestellt und dann ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="d02a6-188">The Origami project will now build, deploy to your HoloLens, and then run.</span></span>
* <span data-ttu-id="d02a6-189">Platzieren Sie Ihre hololens, und sehen Sie sich an, um Ihre neuen holograms anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d02a6-189">Put on your HoloLens and look around to see your new holograms.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="d02a6-190">Kapitel 2: Blick</span><span class="sxs-lookup"><span data-stu-id="d02a6-190">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

<span data-ttu-id="d02a6-191">In diesem Kapitel werden die ersten von drei Möglichkeiten vorgestellt, mit denen Sie mit ihren holograms interagieren [können.](gaze.md)</span><span class="sxs-lookup"><span data-stu-id="d02a6-191">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="d02a6-192">Ziele</span><span class="sxs-lookup"><span data-stu-id="d02a6-192">Objectives</span></span>

* <span data-ttu-id="d02a6-193">Visualisieren Sie Ihren Blick mithilfe eines weltweit gesperrten Cursors.</span><span class="sxs-lookup"><span data-stu-id="d02a6-193">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="d02a6-194">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="d02a6-194">Instructions</span></span>

* <span data-ttu-id="d02a6-195">Wechseln Sie zurück zu Ihrem Unity-Projekt, und schließen Sie das Fenster mit den Buildeinstellungen, wenn es noch geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="d02a6-195">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="d02a6-196">Wählen Sie im **Projekt Panel**den Ordner **holograms** aus.</span><span class="sxs-lookup"><span data-stu-id="d02a6-196">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="d02a6-197">Ziehen Sie das **Cursor** Objekt in das **Hierarchie Panel** auf der Stamm Ebene.</span><span class="sxs-lookup"><span data-stu-id="d02a6-197">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="d02a6-198">Doppelklicken Sie auf das **Cursor** Objekt, um es genauer zu betrachten.</span><span class="sxs-lookup"><span data-stu-id="d02a6-198">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="d02a6-199">Klicken Sie im Projekt Panel mit der rechten Maustaste auf den Ordner **Scripts** .</span><span class="sxs-lookup"><span data-stu-id="d02a6-199">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="d02a6-200">Klicken Sie auf das Untermenü **Erstellen** .</span><span class="sxs-lookup"><span data-stu-id="d02a6-200">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="d02a6-201">Wählen Sie  **C# Skript**aus.</span><span class="sxs-lookup"><span data-stu-id="d02a6-201">Select **C# Script**.</span></span>
* <span data-ttu-id="d02a6-202">Nennen Sie das Skript **worldcursor**.</span><span class="sxs-lookup"><span data-stu-id="d02a6-202">Name the script **WorldCursor**.</span></span> <span data-ttu-id="d02a6-203">Hinweis: Beim Namen wird Groß- und Kleinschreibung beachtet.</span><span class="sxs-lookup"><span data-stu-id="d02a6-203">Note: The name is case-sensitive.</span></span> <span data-ttu-id="d02a6-204">Sie müssen die Erweiterung ". cs" nicht hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="d02a6-204">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="d02a6-205">Wählen Sie im **Hierarchie Panel**das **Cursor** Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="d02a6-205">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="d02a6-206">Verschieben Sie das **worldcursor** -Skript per Drag & amp; Drop in den Bereich **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="d02a6-206">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="d02a6-207">Doppelklicken Sie auf das Skript **worldcursor** , um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="d02a6-207">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="d02a6-208">Fügen Sie diesen Code in **WorldCursor.cs** ein, und **Speichern Sie alle**.</span><span class="sxs-lookup"><span data-stu-id="d02a6-208">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

* <span data-ttu-id="d02a6-209">Erstellen Sie die APP aus dem **Datei >** den Buildeinstellungen neu.</span><span class="sxs-lookup"><span data-stu-id="d02a6-209">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="d02a6-210">Kehren Sie zur Visual Studio-Projekt Mappe zurück, die Sie zuvor für die Bereitstellung in hololens verwendet haben</span><span class="sxs-lookup"><span data-stu-id="d02a6-210">Return to the Visual Studio solution previously used to deploy to your HoloLens.</span></span>
* <span data-ttu-id="d02a6-211">Wählen Sie bei entsprechender Aufforderung "alle neu laden" aus.</span><span class="sxs-lookup"><span data-stu-id="d02a6-211">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="d02a6-212">Klicken Sie auf **Debuggen > Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="d02a6-212">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="d02a6-213">Sehen Sie sich nun die Szene an, und sehen Sie, wie der Cursor mit der Form von Objekten interagiert.</span><span class="sxs-lookup"><span data-stu-id="d02a6-213">Now look around the scene and notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="d02a6-214">Kapitel 3: Gesten</span><span class="sxs-lookup"><span data-stu-id="d02a6-214">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

<span data-ttu-id="d02a6-215">In diesem Kapitel wird die Unterstützung für [Gesten](gestures.md)hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="d02a6-215">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="d02a6-216">Wenn der Benutzer eine Papierkugel auswählt, wird die Kugel durch das Aktivieren der Schwerkraft mit der Physik-Engine von Unity erreicht.</span><span class="sxs-lookup"><span data-stu-id="d02a6-216">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="d02a6-217">Ziele</span><span class="sxs-lookup"><span data-stu-id="d02a6-217">Objectives</span></span>

* <span data-ttu-id="d02a6-218">Steuern Sie Ihre Hologramme mit der SELECT-Geste.</span><span class="sxs-lookup"><span data-stu-id="d02a6-218">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="d02a6-219">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="d02a6-219">Instructions</span></span>

<span data-ttu-id="d02a6-220">Wir beginnen mit der Erstellung eines Skripts und können dann die SELECT-Geste erkennen.</span><span class="sxs-lookup"><span data-stu-id="d02a6-220">We'll start by creating a script then can detect the Select gesture.</span></span>

* <span data-ttu-id="d02a6-221">Erstellen Sie im Ordner **Scripts** ein Skript mit dem Namen " **gazegesturemanager**".</span><span class="sxs-lookup"><span data-stu-id="d02a6-221">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="d02a6-222">Ziehen Sie das Skript " **gazegesturemanager** " auf das Objekt " **origamicollection** " in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="d02a6-222">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="d02a6-223">Öffnen Sie das Skript " **gazegesturemanager** " in Visual Studio, und fügen Sie den folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="d02a6-223">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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

* <span data-ttu-id="d02a6-224">Erstellen Sie ein weiteres Skript im Ordner "Scripts", diesmal mit dem Namen **spherecommands**.</span><span class="sxs-lookup"><span data-stu-id="d02a6-224">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="d02a6-225">Erweitern Sie das Objekt **origamicollection** in der Hierarchie Ansicht.</span><span class="sxs-lookup"><span data-stu-id="d02a6-225">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="d02a6-226">Ziehen Sie das **spherecommands** -Skript auf das **Sphere1** -Objekt im Hierarchie Panel.</span><span class="sxs-lookup"><span data-stu-id="d02a6-226">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="d02a6-227">Ziehen Sie das **spherecommands** -Skript auf das **Sphere2** -Objekt im Hierarchie Panel.</span><span class="sxs-lookup"><span data-stu-id="d02a6-227">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="d02a6-228">Öffnen Sie das Skript in Visual Studio zur Bearbeitung, und ersetzen Sie den Standard Code durch den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="d02a6-228">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="d02a6-229">Exportieren, erstellen und Bereitstellen der app in ihren hololens.</span><span class="sxs-lookup"><span data-stu-id="d02a6-229">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="d02a6-230">Sehen Sie sich einen der Bereiche an.</span><span class="sxs-lookup"><span data-stu-id="d02a6-230">Look at one of the spheres.</span></span>
* <span data-ttu-id="d02a6-231">Führen Sie die SELECT-Geste aus, und beobachten Sie den unteren Bereich der Kugel.</span><span class="sxs-lookup"><span data-stu-id="d02a6-231">Perform the select gesture and watch the sphere drop onto the surface below.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="d02a6-232">Kapitel 4: Stimme</span><span class="sxs-lookup"><span data-stu-id="d02a6-232">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

<span data-ttu-id="d02a6-233">In diesem Kapitel wird die Unterstützung für zwei [Sprachbefehle](voice-input.md)hinzugefügt: "Welt zurücksetzen", um die gelöschten Bereiche an ihren ursprünglichen Speicherort zurückzugeben, und "Drop Sphere", um die Kugel zu verlieren.</span><span class="sxs-lookup"><span data-stu-id="d02a6-233">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to return the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="d02a6-234">Ziele</span><span class="sxs-lookup"><span data-stu-id="d02a6-234">Objectives</span></span>

* <span data-ttu-id="d02a6-235">Fügen Sie Sprachbefehle hinzu, die immer im Hintergrund lauschen.</span><span class="sxs-lookup"><span data-stu-id="d02a6-235">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="d02a6-236">Erstellen Sie ein – Hologramm, das auf einen Voice-Befehl reagiert.</span><span class="sxs-lookup"><span data-stu-id="d02a6-236">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="d02a6-237">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="d02a6-237">Instructions</span></span>

* <span data-ttu-id="d02a6-238">Erstellen Sie **im Ordner** Skripts ein Skript mit dem Namen " **Redner-Manager**".</span><span class="sxs-lookup"><span data-stu-id="d02a6-238">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="d02a6-239">Ziehen Sie das **sprach-Manager** -Skript auf das **origamicollection** -Objekt in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="d02a6-239">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="d02a6-240">Öffnen Sie das **sprach-Manager** -Skript in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d02a6-240">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="d02a6-241">Kopieren Sie diesen Code, und fügen Sie ihn in **SpeechManager.cs** ein. **Speichern Sie alle**</span><span class="sxs-lookup"><span data-stu-id="d02a6-241">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="d02a6-242">Öffnen Sie das **spherecommands** -Skript in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d02a6-242">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="d02a6-243">Aktualisieren Sie das Skript wie folgt:</span><span class="sxs-lookup"><span data-stu-id="d02a6-243">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="d02a6-244">Exportieren, erstellen und Bereitstellen der app in ihren hololens.</span><span class="sxs-lookup"><span data-stu-id="d02a6-244">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="d02a6-245">Sehen Sie sich einen der Bereiche an, und sagen Sie "**Drop Sphere**".</span><span class="sxs-lookup"><span data-stu-id="d02a6-245">Look at one of the spheres, and say "**Drop Sphere**".</span></span>
* <span data-ttu-id="d02a6-246">Sagen Sie "**Welt zurücksetzen**", um Sie wieder an Ihre ursprünglichen Positionen zu bringen.</span><span class="sxs-lookup"><span data-stu-id="d02a6-246">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="d02a6-247">Kapitel 5: räumlicher Sound</span><span class="sxs-lookup"><span data-stu-id="d02a6-247">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

<span data-ttu-id="d02a6-248">In diesem Kapitel werden wir der App Musik hinzufügen und dann bei bestimmten Aktionen Soundeffekte auslöst.</span><span class="sxs-lookup"><span data-stu-id="d02a6-248">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="d02a6-249">Wir verwenden den [räumlichen Ton](spatial-sound.md) , um Klänge an einem bestimmten Speicherort im 3D-Raum zu geben.</span><span class="sxs-lookup"><span data-stu-id="d02a6-249">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="d02a6-250">Ziele</span><span class="sxs-lookup"><span data-stu-id="d02a6-250">Objectives</span></span>

* <span data-ttu-id="d02a6-251">Hören Sie holograms in ihrer Welt.</span><span class="sxs-lookup"><span data-stu-id="d02a6-251">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="d02a6-252">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="d02a6-252">Instructions</span></span>

* <span data-ttu-id="d02a6-253">Wählen Sie in Unity im oberen Menü **> Projekteinstellungen > Audiodatei bearbeiten** aus.</span><span class="sxs-lookup"><span data-stu-id="d02a6-253">In Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="d02a6-254">Suchen Sie im Inspektor-Panel auf der rechten Seite die Einstellung für das **spatializer-Plug** -in, und wählen Sie **MS HRTF spatializer**aus.</span><span class="sxs-lookup"><span data-stu-id="d02a6-254">In the Inspector Panel on the right side, find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="d02a6-255">Ziehen Sie das **Ambiente** -Objekt aus dem Ordner **holograms** im Projekt Panel auf das Objekt **origamicollection** im Bereich Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="d02a6-255">From the **Holograms** folder in the Project panel, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="d02a6-256">Wählen Sie **origamicollection** aus, und suchen Sie im Inspektor-Panel die Komponente **Audioquelle** .</span><span class="sxs-lookup"><span data-stu-id="d02a6-256">Select **OrigamiCollection** and find the **Audio Source** component in the Inspector panel.</span></span> <span data-ttu-id="d02a6-257">Ändern Sie die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="d02a6-257">Change these properties:</span></span>
  * <span data-ttu-id="d02a6-258">Überprüfen Sie die **spatialize** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="d02a6-258">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="d02a6-259">Überprüfen Sie die wieder **Gabe bei wach**.</span><span class="sxs-lookup"><span data-stu-id="d02a6-259">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="d02a6-260">Ändern Sie **räumliche Blend** in **3D** , indem Sie den Schieberegler nach rechts ziehen.</span><span class="sxs-lookup"><span data-stu-id="d02a6-260">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span> <span data-ttu-id="d02a6-261">Wenn Sie den Schieberegler verschieben, sollte der Wert von 0 in 1 geändert werden.</span><span class="sxs-lookup"><span data-stu-id="d02a6-261">The value should change from 0 to 1 when you move the slider.</span></span>
  * <span data-ttu-id="d02a6-262">Überprüfen Sie die **Loop** -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="d02a6-262">Check the **Loop** property.</span></span>
  * <span data-ttu-id="d02a6-263">Erweitern Sie **3D-Sound Einstellungen**, und geben Sie **0,1** für die **Doppler-Ebene**ein.</span><span class="sxs-lookup"><span data-stu-id="d02a6-263">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="d02a6-264">Legen Sie **volumenrolloff** auf **logarithmische Rolloff**fest.</span><span class="sxs-lookup"><span data-stu-id="d02a6-264">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="d02a6-265">Legen Sie **Max Distance** auf **20**fest.</span><span class="sxs-lookup"><span data-stu-id="d02a6-265">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="d02a6-266">Erstellen Sie im Ordner **Scripts** ein Skript mit dem Namen " **spheresounds**".</span><span class="sxs-lookup"><span data-stu-id="d02a6-266">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="d02a6-267">Ziehen Sie **spheresounds** per Drag & Drop auf die Objekte **Sphere1** und **Sphere2** in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="d02a6-267">Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="d02a6-268">Öffnen Sie " **spheresounds** " in Visual Studio, aktualisieren Sie den folgenden Code, und **Speichern Sie alle**.</span><span class="sxs-lookup"><span data-stu-id="d02a6-268">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="d02a6-269">Speichern Sie das Skript, und kehren Sie zu Unity zurück.</span><span class="sxs-lookup"><span data-stu-id="d02a6-269">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="d02a6-270">Exportieren, erstellen und Bereitstellen der app in ihren hololens.</span><span class="sxs-lookup"><span data-stu-id="d02a6-270">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="d02a6-271">Bewegen Sie sich näher und weiter von der Stufe aus, und schalten Sie die Seite auf die Seite, um die Geräusche zu ändern.</span><span class="sxs-lookup"><span data-stu-id="d02a6-271">Move closer and further from the Stage and turn side-to-side to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="d02a6-272">Kapitel 6: räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="d02a6-272">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

<span data-ttu-id="d02a6-273">Nun verwenden wir die [räumliche Zuordnung](spatial-mapping.md) , um das Spiel Board in einem realen Objekt in der realen Welt zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="d02a6-273">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="d02a6-274">Ziele</span><span class="sxs-lookup"><span data-stu-id="d02a6-274">Objectives</span></span>

* <span data-ttu-id="d02a6-275">Bringen Sie Ihre reale Welt in die virtuelle Welt.</span><span class="sxs-lookup"><span data-stu-id="d02a6-275">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="d02a6-276">Platzieren Sie Ihre Hologramme, wo Sie für Sie am wichtigsten sind.</span><span class="sxs-lookup"><span data-stu-id="d02a6-276">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="d02a6-277">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="d02a6-277">Instructions</span></span>

* <span data-ttu-id="d02a6-278">Klicken Sie in Unity im Projekt Panel auf den Ordner **holograms** .</span><span class="sxs-lookup"><span data-stu-id="d02a6-278">In Unity, click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="d02a6-279">Ziehen Sie das Objekt für die **räumliche Zuordnung** in den Stamm der **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="d02a6-279">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="d02a6-280">Klicken Sie in der Hierarchie auf das **räumliche Mapping** -Objekt.</span><span class="sxs-lookup"><span data-stu-id="d02a6-280">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="d02a6-281">Ändern Sie im **Inspektor-Panel**die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="d02a6-281">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="d02a6-282">Aktivieren Sie das Kontrollkästchen **visuelle Meshes zeichnen** .</span><span class="sxs-lookup"><span data-stu-id="d02a6-282">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="d02a6-283">Suchen Sie das **Zeichnungs Material** , und klicken Sie auf den Kreis rechts.</span><span class="sxs-lookup"><span data-stu-id="d02a6-283">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="d02a6-284">Geben Sie im Feld oben den Text "**Draht Modell**" in das Suchfeld ein.</span><span class="sxs-lookup"><span data-stu-id="d02a6-284">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="d02a6-285">Klicken Sie auf das Ergebnis, und schließen Sie das Fenster.</span><span class="sxs-lookup"><span data-stu-id="d02a6-285">Click on the result and then close the window.</span></span> <span data-ttu-id="d02a6-286">Wenn Sie dies tun, sollte der Wert für Zeichnungs Material auf Wireframe festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="d02a6-286">When you do this, the value for Draw Material should get set to Wireframe.</span></span>
* <span data-ttu-id="d02a6-287">Exportieren, erstellen und Bereitstellen der app in ihren hololens.</span><span class="sxs-lookup"><span data-stu-id="d02a6-287">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="d02a6-288">Wenn die app ausgeführt wird, überlagert ein Draht Modell-Mesh ihre reale Welt.</span><span class="sxs-lookup"><span data-stu-id="d02a6-288">When the app runs, a wireframe mesh will overlay your real world.</span></span>
* <span data-ttu-id="d02a6-289">Sehen Sie sich an, wie sich eine parallele Kugel auf der Ebene befindet und auf den Boden zeigt.</span><span class="sxs-lookup"><span data-stu-id="d02a6-289">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="d02a6-290">Nun zeigen wir Ihnen, wie Sie die origamicollection an einen neuen Speicherort verschieben:</span><span class="sxs-lookup"><span data-stu-id="d02a6-290">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="d02a6-291">Erstellen Sie im Ordner **Scripts** ein Skript mit dem Namen " **taptoplaceparent**".</span><span class="sxs-lookup"><span data-stu-id="d02a6-291">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="d02a6-292">Erweitern Sie in der- **Hierarchie**die **origamicollection** , und wählen Sie das **Stage** -Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="d02a6-292">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="d02a6-293">Ziehen Sie das Skript **taptoplaceparent** auf das Stage-Objekt.</span><span class="sxs-lookup"><span data-stu-id="d02a6-293">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="d02a6-294">Öffnen Sie das Skript " **taptoplaceparent** " in Visual Studio, und aktualisieren Sie es wie folgt:</span><span class="sxs-lookup"><span data-stu-id="d02a6-294">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="d02a6-295">Exportieren, erstellen und Bereitstellen der app.</span><span class="sxs-lookup"><span data-stu-id="d02a6-295">Export, build and deploy the app.</span></span>
* <span data-ttu-id="d02a6-296">Jetzt sollten Sie nun in der Lage sein, das Spiel an einem bestimmten Speicherort zu platzieren, indem Sie es mit der SELECT-Geste anordnen und dann an eine neue Stelle verschieben und die Auswahl Geste erneut verwenden.</span><span class="sxs-lookup"><span data-stu-id="d02a6-296">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="chapter-7---holographic-fun"></a><span data-ttu-id="d02a6-297">Kapitel 7: Holographic Fun</span><span class="sxs-lookup"><span data-stu-id="d02a6-297">Chapter 7 - Holographic fun</span></span>

### <a name="objectives"></a><span data-ttu-id="d02a6-298">Ziele</span><span class="sxs-lookup"><span data-stu-id="d02a6-298">Objectives</span></span>

* <span data-ttu-id="d02a6-299">Zeigen Sie den Einstieg in eine Holographic-Unterwelt an.</span><span class="sxs-lookup"><span data-stu-id="d02a6-299">Reveal the entrance to a holographic underworld.</span></span>

### <a name="instructions"></a><span data-ttu-id="d02a6-300">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="d02a6-300">Instructions</span></span>

<span data-ttu-id="d02a6-301">Nun zeigen wir Ihnen, wie Sie die Holographic-Unterwelt entdecken:</span><span class="sxs-lookup"><span data-stu-id="d02a6-301">Now we'll show you how to uncover the holographic underworld:</span></span>

* <span data-ttu-id="d02a6-302">Aus dem Ordner " **holograms** " im Projekt Panel:</span><span class="sxs-lookup"><span data-stu-id="d02a6-302">From the **Holograms** folder in the Project Panel:</span></span>
  * <span data-ttu-id="d02a6-303">Ziehen Sie **Underworld** in die Hierarchie, um ein untergeordnetes Element von **origamicollection**zu sein.</span><span class="sxs-lookup"><span data-stu-id="d02a6-303">Drag **Underworld** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="d02a6-304">Erstellen Sie im Ordner **Scripts** ein Skript mit dem Namen **hittarget**.</span><span class="sxs-lookup"><span data-stu-id="d02a6-304">In the **Scripts** folder, create a script named **HitTarget**.</span></span>
* <span data-ttu-id="d02a6-305">Erweitern Sie in der- **Hierarchie**die " **origamicollection**".</span><span class="sxs-lookup"><span data-stu-id="d02a6-305">In the **Hierarchy**, expand the **OrigamiCollection**.</span></span>
* <span data-ttu-id="d02a6-306">Erweitern Sie das **Stage** -Objekt, und wählen Sie das **Ziel** Objekt (blauer Lüfter) aus.</span><span class="sxs-lookup"><span data-stu-id="d02a6-306">Expand the **Stage** object and select the **Target** object (blue fan).</span></span>
* <span data-ttu-id="d02a6-307">Ziehen **Sie das hittarget** -Skript auf das **Ziel** Objekt.</span><span class="sxs-lookup"><span data-stu-id="d02a6-307">Drag the **HitTarget** script onto the **Target** object.</span></span>
* <span data-ttu-id="d02a6-308">Öffnen Sie das **hittarget** -Skript in Visual Studio, und aktualisieren Sie es wie folgt:</span><span class="sxs-lookup"><span data-stu-id="d02a6-308">Open the **HitTarget** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="d02a6-309">Wählen Sie in Unity das **Ziel** Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="d02a6-309">In Unity, select the **Target** object.</span></span>
* <span data-ttu-id="d02a6-310">Zwei öffentliche Eigenschaften sind jetzt für die **Treffer Ziel** Komponente sichtbar, und Sie müssen auf Objekte in unserer Szene verweisen:</span><span class="sxs-lookup"><span data-stu-id="d02a6-310">Two public properties are now visible on the **Hit Target** component and need to reference objects in our scene:</span></span>
  * <span data-ttu-id="d02a6-311">Ziehen Sie die Option " **Underworld** " aus dem Bereich **Hierarchie** in **die Eigenschaft für** die **Ziel** Komponente.</span><span class="sxs-lookup"><span data-stu-id="d02a6-311">Drag **Underworld** from the **Hierarchy** panel to the **Underworld** property on the **Hit Target** component.</span></span>
  * <span data-ttu-id="d02a6-312">Ziehen Sie **Phase** aus dem Bereich **Hierarchie** auf das **Objekt, um** die Eigenschaft für die **Treffer Ziel** Komponente auszublenden.</span><span class="sxs-lookup"><span data-stu-id="d02a6-312">Drag **Stage** from the **Hierarchy** panel to the **Object to Hide** property on the **Hit Target** component.</span></span>
* <span data-ttu-id="d02a6-313">Exportieren, erstellen und Bereitstellen der app.</span><span class="sxs-lookup"><span data-stu-id="d02a6-313">Export, build and deploy the app.</span></span>
* <span data-ttu-id="d02a6-314">Platzieren Sie die Origami-Auflistung auf der Etage, und verwenden Sie dann die Aktion auswählen, um einen Kugel Ablage Vorgang zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d02a6-314">Place the Origami Collection on the floor, and then use the Select gesture to make a sphere drop.</span></span>
* <span data-ttu-id="d02a6-315">Wenn die Kugel auf das Ziel (blauer Lüfter) trifft, tritt eine Explosion auf.</span><span class="sxs-lookup"><span data-stu-id="d02a6-315">When the sphere hits the target (blue fan), an explosion will occur.</span></span> <span data-ttu-id="d02a6-316">Die Sammlung wird ausgeblendet, und ein Loch in der Unterwelt wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d02a6-316">The collection will be hidden and a hole to the underworld will appear.</span></span>

## <a name="the-end"></a><span data-ttu-id="d02a6-317">Das Ende</span><span class="sxs-lookup"><span data-stu-id="d02a6-317">The end</span></span>

<span data-ttu-id="d02a6-318">Und das ist das Ende dieses Tutorials!</span><span class="sxs-lookup"><span data-stu-id="d02a6-318">And that's the end of this tutorial!</span></span>

<span data-ttu-id="d02a6-319">Sie haben Folgendes gelernt:</span><span class="sxs-lookup"><span data-stu-id="d02a6-319">You learned:</span></span>

* <span data-ttu-id="d02a6-320">Erstellen einer Holographic-app in Unity.</span><span class="sxs-lookup"><span data-stu-id="d02a6-320">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="d02a6-321">Verwendung von Blick, Bewegung, Stimme, Sound und räumlicher Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="d02a6-321">How to make use of gaze, gesture, voice, sound, and spatial mapping.</span></span>
* <span data-ttu-id="d02a6-322">Erfahren Sie, wie Sie eine APP mit Visual Studio erstellen und bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="d02a6-322">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="d02a6-323">Nun können Sie mit der Erstellung Ihrer eigenen Holographic-Benutzeroberflächen beginnen!</span><span class="sxs-lookup"><span data-stu-id="d02a6-323">You are now ready to start creating your own holographic experience!</span></span>

## <a name="see-also"></a><span data-ttu-id="d02a6-324">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d02a6-324">See also</span></span>

* [<span data-ttu-id="d02a6-325">MR-Grundlagen 101E: Vollständiges Projekt mit Emulator</span><span class="sxs-lookup"><span data-stu-id="d02a6-325">MR Basics 101E: Complete project with emulator</span></span>](holograms-101e.md)
* [<span data-ttu-id="d02a6-326">Anvisieren</span><span class="sxs-lookup"><span data-stu-id="d02a6-326">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="d02a6-327">Gesten</span><span class="sxs-lookup"><span data-stu-id="d02a6-327">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="d02a6-328">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="d02a6-328">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="d02a6-329">Raumklang</span><span class="sxs-lookup"><span data-stu-id="d02a6-329">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="d02a6-330">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="d02a6-330">Spatial mapping</span></span>](spatial-mapping.md)
