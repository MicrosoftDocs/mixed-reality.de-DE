---
title: MR 240 - mehrere HoloLens-Geräte freigeben
description: Führen Sie diese exemplarischen Vorgehensweise erfahren, die Details der Freigabe Hologramme auf Unity, Visual Studio und HoloLens mit Codierung.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, sharing, networking, academy, tutorial
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594887"
---
>[!NOTE]
><span data-ttu-id="22010-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="22010-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="22010-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="22010-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="22010-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="22010-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="22010-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="22010-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="22010-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="22010-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="22010-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="22010-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a><span data-ttu-id="22010-110">MR 240 freigeben: Mehrere HoloLens-Geräte</span><span class="sxs-lookup"><span data-stu-id="22010-110">MR Sharing 240: Multiple HoloLens devices</span></span>

<span data-ttu-id="22010-111">Hologramme Anwesenheit in unserer Welt mit gewährt verbleibende vorhanden, wie wir im Raum umher zu schieben.</span><span class="sxs-lookup"><span data-stu-id="22010-111">Holograms are given presence in our world by remaining in place as we move about in space.</span></span> <span data-ttu-id="22010-112">HoloLens behält Hologramme in Position mithilfe verschiedener [Koordinatensysteme](coordinate-systems.md) zum Nachverfolgen der Ort und die Ausrichtung von Objekten.</span><span class="sxs-lookup"><span data-stu-id="22010-112">HoloLens keeps holograms in place by using various [coordinate systems](coordinate-systems.md) to keep track of the location and orientation of objects.</span></span> <span data-ttu-id="22010-113">Wenn wir diese Koordinatensysteme zwischen Geräten freigeben, können wir eine gemeinsame Erfahrung erstellen, die zur Teilnahme an einer freigegebenen holographic Welt ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="22010-113">When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.</span></span>

<span data-ttu-id="22010-114">In diesem Tutorial wird Folgendes beschrieben:</span><span class="sxs-lookup"><span data-stu-id="22010-114">In this tutorial, we will:</span></span>

* <span data-ttu-id="22010-115">Einrichten eines Netzwerks für einen gemeinsamen Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="22010-115">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="22010-116">Teilen Sie Hologramme für HoloLens-Geräte.</span><span class="sxs-lookup"><span data-stu-id="22010-116">Share holograms across HoloLens devices.</span></span>
* <span data-ttu-id="22010-117">Entdecken Sie andere Personen in unserem gemeinsamen holographic.</span><span class="sxs-lookup"><span data-stu-id="22010-117">Discover other people in our shared holographic world.</span></span>
* <span data-ttu-id="22010-118">Erstellen Sie eine freigegebene interaktive Benutzeroberfläche können Sie weitere Entwicklungen - Ziel und Starten der Projektile auf sie!</span><span class="sxs-lookup"><span data-stu-id="22010-118">Create a shared interactive experience where you can target other players - and launch projectiles at them!</span></span>

## <a name="device-support"></a><span data-ttu-id="22010-119">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="22010-119">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="22010-120">Kurs</span><span class="sxs-lookup"><span data-stu-id="22010-120">Course</span></span></th><th style="width:150px"> <span data-ttu-id="22010-121"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="22010-121"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="22010-122"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="22010-122"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="22010-123">MR 240 freigeben: Mehrere HoloLens-Geräte</span><span class="sxs-lookup"><span data-stu-id="22010-123">MR Sharing 240: Multiple HoloLens devices</span></span></td><td style="text-align: center;"> <span data-ttu-id="22010-124">✔️</span><span class="sxs-lookup"><span data-stu-id="22010-124">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="22010-125">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="22010-125">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="22010-126">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="22010-126">Prerequisites</span></span>

* <span data-ttu-id="22010-127">Ein Windows 10-PCs mit dem richtigen konfiguriert [-Tools installiert](install-the-tools.md) mit Internetzugriff.</span><span class="sxs-lookup"><span data-stu-id="22010-127">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md) with Internet access.</span></span>
* <span data-ttu-id="22010-128">HoloLens-Geräte über mindestens zwei [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="22010-128">At least two HoloLens devices [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="22010-129">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="22010-129">Project files</span></span>

* <span data-ttu-id="22010-130">Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) vom Projekt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="22010-130">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) required by the project.</span></span> <span data-ttu-id="22010-131">Ist Unity 2017.2 oder höher erforderlich.</span><span class="sxs-lookup"><span data-stu-id="22010-131">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="22010-132">Wenn Sie weitere Unity 5.6-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span><span class="sxs-lookup"><span data-stu-id="22010-132">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span></span>
  * <span data-ttu-id="22010-133">Wenn Sie weitere Unity 5.5-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span><span class="sxs-lookup"><span data-stu-id="22010-133">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span></span>
  * <span data-ttu-id="22010-134">Wenn Sie weitere 5.4 von Unity-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span><span class="sxs-lookup"><span data-stu-id="22010-134">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span></span>
* <span data-ttu-id="22010-135">Un-Archive die Dateien auf dem Desktop oder andere einfach auf den Speicherort zugreifen.</span><span class="sxs-lookup"><span data-stu-id="22010-135">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="22010-136">Behalten Sie den Ordnernamen als **SharedHolograms**.</span><span class="sxs-lookup"><span data-stu-id="22010-136">Keep the folder name as **SharedHolograms**.</span></span>

>[!NOTE]
><span data-ttu-id="22010-137">Wenn Sie vor dem Herunterladen, den Quellcode ansehen möchten es [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span><span class="sxs-lookup"><span data-stu-id="22010-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="22010-138">Kapitel 1: Holo World</span><span class="sxs-lookup"><span data-stu-id="22010-138">Chapter 1 - Holo World</span></span>

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

<span data-ttu-id="22010-139">In diesem Kapitel wir unser erstes Unity-Projekt und durchlaufen Sie den Build einrichten und Bereitstellen von Prozess.</span><span class="sxs-lookup"><span data-stu-id="22010-139">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="22010-140">Ziele</span><span class="sxs-lookup"><span data-stu-id="22010-140">Objectives</span></span>

* <span data-ttu-id="22010-141">Richten Sie Unity um holographic apps zu entwickeln.</span><span class="sxs-lookup"><span data-stu-id="22010-141">Setup Unity to develop holographic apps.</span></span>
* <span data-ttu-id="22010-142">Finden Sie unter Ihrem – Hologramm!</span><span class="sxs-lookup"><span data-stu-id="22010-142">See your hologram!</span></span>

### <a name="instructions"></a><span data-ttu-id="22010-143">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="22010-143">Instructions</span></span>

* <span data-ttu-id="22010-144">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="22010-144">Start Unity.</span></span>
* <span data-ttu-id="22010-145">Wählen Sie **öffnen**.</span><span class="sxs-lookup"><span data-stu-id="22010-145">Select **Open**.</span></span>
* <span data-ttu-id="22010-146">Geben Sie den Speicherort als dem **SharedHolograms** Ordner, die Sie zuvor nicht archiviert.</span><span class="sxs-lookup"><span data-stu-id="22010-146">Enter location as the **SharedHolograms** folder you previously unarchived.</span></span>
* <span data-ttu-id="22010-147">Wählen Sie **Projektname** , und klicken Sie auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="22010-147">Select **Project Name** and click **Select Folder**.</span></span>
* <span data-ttu-id="22010-148">In der **Hierarchie**, mit der rechten Maustaste die **Main Camera** , und wählen Sie **löschen**.</span><span class="sxs-lookup"><span data-stu-id="22010-148">In the **Hierarchy**, right-click the **Main Camera** and select **Delete**.</span></span>
* <span data-ttu-id="22010-149">In der **HoloToolkit-Freigabe-240/Prefabs/Kamera** Ordner finden Sie die **Main Camera** prefab.</span><span class="sxs-lookup"><span data-stu-id="22010-149">In the **HoloToolkit-Sharing-240/Prefabs/Camera** folder, find the **Main Camera** prefab.</span></span>
* <span data-ttu-id="22010-150">Drag & drop die **Main Camera** in die **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="22010-150">Drag and drop the **Main Camera** into the **Hierarchy**.</span></span>
* <span data-ttu-id="22010-151">In der **Hierarchie**, klicken Sie auf **erstellen** und **leere erstellen**.</span><span class="sxs-lookup"><span data-stu-id="22010-151">In the **Hierarchy**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="22010-152">Mit der rechten Maustaste den neuen **"gameobject"** , und wählen Sie **umbenennen**.</span><span class="sxs-lookup"><span data-stu-id="22010-152">Right-click the new **GameObject** and select **Rename**.</span></span>
* <span data-ttu-id="22010-153">Benennen Sie das "gameobject" zu **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="22010-153">Rename the GameObject to **HologramCollection**.</span></span>
* <span data-ttu-id="22010-154">Wählen Sie die **HologramCollection** -Objekt in der **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="22010-154">Select the **HologramCollection** object in the **Hierarchy**.</span></span>
* <span data-ttu-id="22010-155">In der **Inspektor** legen Sie die **transformieren Position** zu: **X: 0, Y: -0.25, Z: 2**.</span><span class="sxs-lookup"><span data-stu-id="22010-155">In the **Inspector** set the **transform position** to: **X: 0, Y: -0.25, Z: 2**.</span></span>
* <span data-ttu-id="22010-156">In der **Hologramme** Ordner in der **Projektfenster**, finden Sie die **EnergyHub** Asset.</span><span class="sxs-lookup"><span data-stu-id="22010-156">In the **Holograms** folder in the **Project panel**, find the **EnergyHub** asset.</span></span>
* <span data-ttu-id="22010-157">Drag & drop die **EnergyHub** -Objekt aus der **Projektfenster** auf die **Hierarchie** als eine **untergeordnetes Element des HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="22010-157">Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="22010-158">Wählen Sie **Datei > Szene speichern unter...**</span><span class="sxs-lookup"><span data-stu-id="22010-158">Select **File > Save Scene As...**</span></span>
* <span data-ttu-id="22010-159">Benennen Sie die Szene **SharedHolograms** , und klicken Sie auf **speichern**.</span><span class="sxs-lookup"><span data-stu-id="22010-159">Name the scene **SharedHolograms** and click **Save**.</span></span>
* <span data-ttu-id="22010-160">Drücken Sie die **spielen** -Schaltfläche in Unity, um Ihre Hologramme der Vorschau anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="22010-160">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="22010-161">Drücken Sie **spielen** ein zweites Mal im Vorschaumodus zu beenden.</span><span class="sxs-lookup"><span data-stu-id="22010-161">Press **Play** a second time to stop preview mode.</span></span>

<span data-ttu-id="22010-162">**Exportieren Sie das Projekt aus Unity in Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="22010-162">**Export the project from Unity to Visual Studio**</span></span>
* <span data-ttu-id="22010-163">Im Unity-Option **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="22010-163">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="22010-164">Klicken Sie auf **öffnen Szenen hinzufügen** die Szene hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="22010-164">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="22010-165">Wählen Sie **universelle Windows-Plattform** in die **Plattform** aus, und klicken Sie auf **Plattform wechseln**.</span><span class="sxs-lookup"><span data-stu-id="22010-165">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="22010-166">Legen Sie **SDK** zu **universelle 10**.</span><span class="sxs-lookup"><span data-stu-id="22010-166">Set **SDK** to **Universal 10**.</span></span>
* <span data-ttu-id="22010-167">Legen Sie **Zielgerät** zu **HoloLens** und **UWP Build Type** zu **D3D**.</span><span class="sxs-lookup"><span data-stu-id="22010-167">Set **Target device** to **HoloLens** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="22010-168">Überprüfen Sie **Unity C# Projekte**.</span><span class="sxs-lookup"><span data-stu-id="22010-168">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="22010-169">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="22010-169">Click **Build**.</span></span>
* <span data-ttu-id="22010-170">Erstellen Sie in dem Datei-Explorer-Fenster, das angezeigt wird, eine **neuer Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="22010-170">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="22010-171">Mausklick die **App** Ordner.</span><span class="sxs-lookup"><span data-stu-id="22010-171">Single click the **App** folder.</span></span>
* <span data-ttu-id="22010-172">Drücken Sie **wählen Sie Ordner**.</span><span class="sxs-lookup"><span data-stu-id="22010-172">Press **Select Folder**.</span></span>
* <span data-ttu-id="22010-173">Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="22010-173">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="22010-174">Öffnen der **App** Ordner.</span><span class="sxs-lookup"><span data-stu-id="22010-174">Open the **App** folder.</span></span>
* <span data-ttu-id="22010-175">Open **SharedHolograms.sln** zum Starten von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="22010-175">Open **SharedHolograms.sln** to launch Visual Studio.</span></span>
* <span data-ttu-id="22010-176">Verwenden obere auf der Symbolleiste in Visual Studio, ändern Sie das Ziel vom Debugmodus in den **Version** und ARM, **X86**.</span><span class="sxs-lookup"><span data-stu-id="22010-176">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="22010-177">Klicken Sie auf den Dropdownpfeil neben dem lokalen Computer, und wählen **Remotegerät**.</span><span class="sxs-lookup"><span data-stu-id="22010-177">Click on the drop-down arrow next to Local Machine, and select **Remote Device**.</span></span>
    * <span data-ttu-id="22010-178">Legen Sie die **Adresse** auf den Namen oder die IP-Adresse Ihrer HoloLens.</span><span class="sxs-lookup"><span data-stu-id="22010-178">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="22010-179">Wenn Sie Ihre IP-Adresse des Geräts nicht kennen, suchen Sie im **Einstellungen > Netzwerk und Internet > Erweiterte Optionen** , oder bitten Sie Cortana **"Hey Cortana, was Meine IP-Adresse ist?"**</span><span class="sxs-lookup"><span data-stu-id="22010-179">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
    * <span data-ttu-id="22010-180">Lassen Sie die **Authentifizierungsmodus** festgelegt **universelle**.</span><span class="sxs-lookup"><span data-stu-id="22010-180">Leave the **Authentication Mode** set to **Universal**.</span></span>
    * <span data-ttu-id="22010-181">Klicken Sie auf **auswählen**</span><span class="sxs-lookup"><span data-stu-id="22010-181">Click **Select**</span></span>
* <span data-ttu-id="22010-182">Klicken Sie auf **Debuggen > Starten ohne debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="22010-182">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="22010-183">Ist dies beim ersten auf Ihrem Gerät bereitstellen, Sie müssen [verbinden Sie es mit Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="22010-183">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
* <span data-ttu-id="22010-184">Legen Sie auf Ihre HoloLens, und suchen Sie die EnergyHub – Hologramm.</span><span class="sxs-lookup"><span data-stu-id="22010-184">Put on your HoloLens and find the EnergyHub hologram.</span></span>

## <a name="chapter-2---interaction"></a><span data-ttu-id="22010-185">Kapitel 2 – Interaktionen</span><span class="sxs-lookup"><span data-stu-id="22010-185">Chapter 2 - Interaction</span></span>

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

<span data-ttu-id="22010-186">In diesem Kapitel werden wir mit unserem Hologramme interagieren.</span><span class="sxs-lookup"><span data-stu-id="22010-186">In this chapter, we'll interact with our holograms.</span></span> <span data-ttu-id="22010-187">Zunächst fügen wir einen Cursor zum Visualisieren unsere [bestaunen](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="22010-187">First, we'll add a cursor to visualize our [Gaze](gaze.md).</span></span> <span data-ttu-id="22010-188">Klicken Sie dann wir fügen [Gesten](gestures.md) und verwenden Sie unsere Seite, um unsere Hologramme im Raum platzieren.</span><span class="sxs-lookup"><span data-stu-id="22010-188">Then, we'll add [Gestures](gestures.md) and use our hand to place our holograms in space.</span></span>

### <a name="objectives"></a><span data-ttu-id="22010-189">Ziele</span><span class="sxs-lookup"><span data-stu-id="22010-189">Objectives</span></span>

* <span data-ttu-id="22010-190">Verwenden Sie die Blicke, die Eingabe für einen Cursor zu steuern.</span><span class="sxs-lookup"><span data-stu-id="22010-190">Use gaze input to control a cursor.</span></span>
* <span data-ttu-id="22010-191">Verwenden Sie die Eingabe für die Interaktion mit Hologramme Geste.</span><span class="sxs-lookup"><span data-stu-id="22010-191">Use gesture input to interact with holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="22010-192">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="22010-192">Instructions</span></span>

<span data-ttu-id="22010-193">**Blicke**</span><span class="sxs-lookup"><span data-stu-id="22010-193">**Gaze**</span></span>
* <span data-ttu-id="22010-194">In der **Hierarchie Bereich** wählen Sie die **HologramCollection** Objekt.</span><span class="sxs-lookup"><span data-stu-id="22010-194">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="22010-195">In der **Inspektor Bereich** klicken Sie auf die **Add Component** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="22010-195">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="22010-196">Geben Sie im Menü, in das Suchfeld **bestaunen Manager**.</span><span class="sxs-lookup"><span data-stu-id="22010-196">In the menu, type in the search box **Gaze Manager**.</span></span> <span data-ttu-id="22010-197">Wählen Sie das Suchergebnis.</span><span class="sxs-lookup"><span data-stu-id="22010-197">Select the search result.</span></span>
* <span data-ttu-id="22010-198">In der **HoloToolkit-Freigabe-240\Prefabs\Input** Ordner finden Sie die **Cursor** Asset.</span><span class="sxs-lookup"><span data-stu-id="22010-198">In the **HoloToolkit-Sharing-240\Prefabs\Input** folder, find the **Cursor** asset.</span></span>
* <span data-ttu-id="22010-199">Drag & drop die **Cursor** Medienobjekt, auf die **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="22010-199">Drag and drop the **Cursor** asset onto the **Hierarchy**.</span></span>

<span data-ttu-id="22010-200">**Aktion**</span><span class="sxs-lookup"><span data-stu-id="22010-200">**Gesture**</span></span>
* <span data-ttu-id="22010-201">In der **Hierarchie Bereich** wählen Sie die **HologramCollection** Objekt.</span><span class="sxs-lookup"><span data-stu-id="22010-201">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="22010-202">Klicken Sie auf **Add Component** und **Gesten-Manager** in das Suchfeld ein.</span><span class="sxs-lookup"><span data-stu-id="22010-202">Click **Add Component** and type **Gesture Manager** in the search field.</span></span> <span data-ttu-id="22010-203">Wählen Sie das Suchergebnis.</span><span class="sxs-lookup"><span data-stu-id="22010-203">Select the search result.</span></span>
* <span data-ttu-id="22010-204">In der **Hierarchie Bereich**, erweitern Sie **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="22010-204">In the **Hierarchy panel**, expand **HologramCollection**.</span></span>
* <span data-ttu-id="22010-205">Wählen Sie das untergeordnete Element **EnergyHub** Objekt.</span><span class="sxs-lookup"><span data-stu-id="22010-205">Select the child **EnergyHub** object.</span></span>
* <span data-ttu-id="22010-206">In der **Inspektor Bereich** klicken Sie auf die **Add Component** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="22010-206">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="22010-207">Geben Sie im Menü, in das Suchfeld **– Hologramm Platzierung**.</span><span class="sxs-lookup"><span data-stu-id="22010-207">In the menu, type in the search box **Hologram Placement**.</span></span> <span data-ttu-id="22010-208">Wählen Sie das Suchergebnis.</span><span class="sxs-lookup"><span data-stu-id="22010-208">Select the search result.</span></span>
* <span data-ttu-id="22010-209">Speichern Sie die Szene durch Auswählen von **Datei > Szene speichern**.</span><span class="sxs-lookup"><span data-stu-id="22010-209">Save the scene by selecting **File > Save Scene**.</span></span>

<span data-ttu-id="22010-210">**Bereitstellen und nutzen**</span><span class="sxs-lookup"><span data-stu-id="22010-210">**Deploy and enjoy**</span></span>
* <span data-ttu-id="22010-211">Erstellen Sie und Bereitstellen Sie, um Ihre HoloLens, mithilfe der Anweisungen aus dem vorhergehenden Kapitel.</span><span class="sxs-lookup"><span data-stu-id="22010-211">Build and deploy to your HoloLens, using the instructions from the previous chapter.</span></span>
* <span data-ttu-id="22010-212">Sobald die app auf Ihrem HoloLens wird gestartet, verschieben Sie Kopf zu, und beachten Sie, wie die EnergyHub Ihre Blicke verfolgt.</span><span class="sxs-lookup"><span data-stu-id="22010-212">Once the app launches on your HoloLens, move your head around and notice how the EnergyHub follows your gaze.</span></span>
* <span data-ttu-id="22010-213">Beachten Sie, wie der Cursor wird angezeigt, wenn Sie bei der Hologramm bestaunen und Änderungen an Punktuelles Licht, wenn nicht am ggf. ein Hologramm gazing.</span><span class="sxs-lookup"><span data-stu-id="22010-213">Notice how the cursor appears when you gaze upon the hologram, and changes to a point light when not gazing at a hologram.</span></span>
* <span data-ttu-id="22010-214">Führen Sie eine tippbewegung Hologramm platzieren.</span><span class="sxs-lookup"><span data-stu-id="22010-214">Perform an air-tap to place the hologram.</span></span> <span data-ttu-id="22010-215">Zu diesem Zeitpunkt in unserem Projekt können Sie nur einmal die Hologramm (Wiederholen Sie die Bereitstellung erneut versuchen) platzieren.</span><span class="sxs-lookup"><span data-stu-id="22010-215">At this time in our project, you can only place the hologram once (redeploy to try again).</span></span>

## <a name="chapter-3---shared-coordinates"></a><span data-ttu-id="22010-216">Koordiniert die Kapitel 3 – freigegeben</span><span class="sxs-lookup"><span data-stu-id="22010-216">Chapter 3 - Shared Coordinates</span></span>

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

<span data-ttu-id="22010-217">Es Spaß macht, finden Sie unter und Hologramme interagieren, aber noch weiter gehen.</span><span class="sxs-lookup"><span data-stu-id="22010-217">It's fun to see and interact with holograms, but let's go further.</span></span> <span data-ttu-id="22010-218">Wir richten unsere erste gemeinsamen Erfahrung - ggf. ein Hologramm, die alle zusammen sehen kann.</span><span class="sxs-lookup"><span data-stu-id="22010-218">We'll set up our first shared experience - a hologram everyone can see together.</span></span>

### <a name="objectives"></a><span data-ttu-id="22010-219">Ziele</span><span class="sxs-lookup"><span data-stu-id="22010-219">Objectives</span></span>

* <span data-ttu-id="22010-220">Einrichten eines Netzwerks für einen gemeinsamen Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="22010-220">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="22010-221">Richten Sie keinen gemeinsamen Zeitpunkt für den Verweis.</span><span class="sxs-lookup"><span data-stu-id="22010-221">Establish a common reference point.</span></span>
* <span data-ttu-id="22010-222">Teilen Sie Koordinatensysteme auf Geräten.</span><span class="sxs-lookup"><span data-stu-id="22010-222">Share coordinate systems across devices.</span></span>
* <span data-ttu-id="22010-223">Alle sehen die gleichen – Hologramm!</span><span class="sxs-lookup"><span data-stu-id="22010-223">Everyone sees the same hologram!</span></span>

>[!NOTE]
><span data-ttu-id="22010-224">Die **InternetClientServer** und **PrivateNetworkClientServer** Funktionen müssen deklariert werden, für eine app für die Verbindung mit dem Server freigeben.</span><span class="sxs-lookup"><span data-stu-id="22010-224">The **InternetClientServer** and **PrivateNetworkClientServer** capabilities must be declared for an app to connect to the sharing server.</span></span> <span data-ttu-id="22010-225">Dies ist für die Sie bereits unter Hologramme 240, aber beachten Sie, dass für Ihre eigenen Projekte.</span><span class="sxs-lookup"><span data-stu-id="22010-225">This is done for you already in Holograms 240, but keep this in mind for your own projects.</span></span>
>1. <span data-ttu-id="22010-226">Rufen Sie im Unity-Editor die playereinstellungen durch Navigieren zu "Bearbeiten > Projekt Einstellungen > Player"</span><span class="sxs-lookup"><span data-stu-id="22010-226">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="22010-227">Klicken Sie auf der Registerkarte "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="22010-227">Click on the "Windows Store" tab</span></span>
>3. <span data-ttu-id="22010-228">Überprüfen Sie im Abschnitt "Einstellungen > Veröffentlichungsfunktionen" die **InternetClientServer** Funktion und die **PrivateNetworkClientServer** Funktion</span><span class="sxs-lookup"><span data-stu-id="22010-228">In the "Publishing Settings > Capabilities" section, check the **InternetClientServer** capability and the **PrivateNetworkClientServer** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="22010-229">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="22010-229">Instructions</span></span>

* <span data-ttu-id="22010-230">In der **Projektfenster** navigieren Sie zu der **HoloToolkit-Freigabe-240\Prefabs\Sharing** Ordner.</span><span class="sxs-lookup"><span data-stu-id="22010-230">In the **Project panel** navigate to the **HoloToolkit-Sharing-240\Prefabs\Sharing** folder.</span></span>
* <span data-ttu-id="22010-231">Drag & drop die **Freigabe** prefab in die **Hierarchie Bereich**.</span><span class="sxs-lookup"><span data-stu-id="22010-231">Drag and drop the **Sharing** prefab into the **Hierarchy panel**.</span></span>

<span data-ttu-id="22010-232">Als Nächstes müssen wir den Freigabedienst zu starten.</span><span class="sxs-lookup"><span data-stu-id="22010-232">Next we need to launch the sharing service.</span></span> <span data-ttu-id="22010-233">Nur **einen PC** erleben Sie in der gemeinsam verwendeten muss diesen Schritt nicht ausführen.</span><span class="sxs-lookup"><span data-stu-id="22010-233">Only **one PC** in the shared experience needs to do this step.</span></span>
* <span data-ttu-id="22010-234">Wählen Sie im Menü oben Hand – in Unity – die **HoloToolkit-Freigabe-240-Menü**.</span><span class="sxs-lookup"><span data-stu-id="22010-234">In Unity - in the top-hand menu - select the **HoloToolkit-Sharing-240 menu**.</span></span>
* <span data-ttu-id="22010-235">Wählen Sie die **Freigabedienst starten** Element in der Dropdownliste aus.</span><span class="sxs-lookup"><span data-stu-id="22010-235">Select the **Launch Sharing Service** item in the drop-down.</span></span>
* <span data-ttu-id="22010-236">Überprüfen Sie die **privates Netzwerk** aus, und klicken Sie auf **Zugriff zulassen** Wenn die Firewall-Eingabeaufforderung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="22010-236">Check the **Private Network** option and click **Allow Access** when the firewall prompt appears.</span></span>
* <span data-ttu-id="22010-237">Notieren Sie sich die IPv4-Adresse, die in die gemeinsame Nutzung der Konsolenfenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="22010-237">Note down the IPv4 address displayed in the Sharing Service console window.</span></span> <span data-ttu-id="22010-238">Dies ist die gleiche IP-Adresse des Computers, die der Dienst ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="22010-238">This is the same IP as the machine the service is being run on.</span></span>

<span data-ttu-id="22010-239">Befolgen Sie die restlichen Anweisungen auf **alle PCs** , wird die freigegebene Benutzeroberfläche beitreten.</span><span class="sxs-lookup"><span data-stu-id="22010-239">Follow the rest of the instructions on **all PCs** that will join the shared experience.</span></span>
* <span data-ttu-id="22010-240">In der **Hierarchie**, wählen die **Freigabe** Objekt.</span><span class="sxs-lookup"><span data-stu-id="22010-240">In the **Hierarchy**, select the **Sharing** object.</span></span>
* <span data-ttu-id="22010-241">In der **Inspektor**auf die **Freigabe Phase** Komponente ändern der **Serveradresse** von 'Localhost', um die IPv4-Adresse des Computers SharingService.exe ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="22010-241">In the **Inspector**, on the **Sharing Stage** component, change the **Server Address** from 'localhost' to the IPv4 address of the machine running SharingService.exe.</span></span>
* <span data-ttu-id="22010-242">In der **Hierarchie** wählen Sie die **HologramCollection** Objekt.</span><span class="sxs-lookup"><span data-stu-id="22010-242">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="22010-243">In der **Inspektor** klicken Sie auf die **Add Component** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="22010-243">In the **Inspector** click the **Add Component** button.</span></span>
* <span data-ttu-id="22010-244">Geben Sie in das Suchfeld **Import Export Anker Manager**.</span><span class="sxs-lookup"><span data-stu-id="22010-244">In the search box, type **Import Export Anchor Manager**.</span></span> <span data-ttu-id="22010-245">Wählen Sie das Suchergebnis.</span><span class="sxs-lookup"><span data-stu-id="22010-245">Select the search result.</span></span>
* <span data-ttu-id="22010-246">In der **Projektfenster** navigieren Sie zu der **Skripts** Ordner.</span><span class="sxs-lookup"><span data-stu-id="22010-246">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="22010-247">Doppelklicken Sie auf die **HologramPlacement** Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="22010-247">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="22010-248">Ersetzen Sie den Inhalt durch den folgenden Code ein.</span><span class="sxs-lookup"><span data-stu-id="22010-248">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;
        
        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="22010-249">Wählen Sie in Unity, die **HologramCollection** in die **Hierarchie Bereich**.</span><span class="sxs-lookup"><span data-stu-id="22010-249">Back in Unity, select the **HologramCollection** in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="22010-250">In der **Inspektor Bereich** klicken Sie auf die **Add Component** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="22010-250">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="22010-251">Geben Sie im Menü, in das Suchfeld **App-Status-Manager**.</span><span class="sxs-lookup"><span data-stu-id="22010-251">In the menu, type in the search box **App State Manager**.</span></span> <span data-ttu-id="22010-252">Wählen Sie das Suchergebnis.</span><span class="sxs-lookup"><span data-stu-id="22010-252">Select the search result.</span></span>

<span data-ttu-id="22010-253">**Bereitstellen und nutzen**</span><span class="sxs-lookup"><span data-stu-id="22010-253">**Deploy and enjoy**</span></span>
* <span data-ttu-id="22010-254">Erstellen Sie das Projekt für Ihre HoloLens-Geräte.</span><span class="sxs-lookup"><span data-stu-id="22010-254">Build the project for your HoloLens devices.</span></span>
* <span data-ttu-id="22010-255">Legen Sie eine HoloLens zunächst bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="22010-255">Designate one HoloLens to deploy to first.</span></span> <span data-ttu-id="22010-256">Sie müssen warten, bis der Anker an den Dienst hochgeladen werden, bevor Sie die EnergyHub platzieren können (dies dauert ca. 30 bis 60 Sekunden).</span><span class="sxs-lookup"><span data-stu-id="22010-256">You will need to wait for the Anchor to be uploaded to the service before you can place the EnergyHub (this can take ~30-60 seconds).</span></span> <span data-ttu-id="22010-257">Bis der Upload abgeschlossen ist, werden Ihre Bewegungen Tap ignoriert.</span><span class="sxs-lookup"><span data-stu-id="22010-257">Until the upload is done, your tap gestures will be ignored.</span></span>
* <span data-ttu-id="22010-258">Nachdem die EnergyHub platziert wurde, am Speicherort auf den Dienst hochgeladen werden, und anschließend können Sie für alle anderen HoloLens-Geräte bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="22010-258">After the EnergyHub has been placed, its location will be uploaded to the service and you can then deploy to all other HoloLens devices.</span></span>
* <span data-ttu-id="22010-259">Wenn eine neue HoloLens zunächst die Sitzung beitritt, möglicherweise der Speicherort der EnergyHub nicht korrekt auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="22010-259">When a new HoloLens first joins the session, the location of the EnergyHub may not be correct on that device.</span></span> <span data-ttu-id="22010-260">Als den Anker und die EnergyHub Speicherorte vom Dienst heruntergeladen wurden, sollte die EnergyHub jedoch auf den neuen, freigegebenen Speicherort wechseln.</span><span class="sxs-lookup"><span data-stu-id="22010-260">However, as soon as the anchor and EnergyHub locations have been downloaded from the service, the EnergyHub should jump to the new, shared location.</span></span> <span data-ttu-id="22010-261">Wenn dieser Fehler nicht innerhalb von ca. 30 bis 60 tritt Sekunden behandelt wird, auf die ursprünglichen HoloLens, bei denen war, beim Festlegen des Ankers aus, um weitere Hinweise der Umgebung zu sammeln.</span><span class="sxs-lookup"><span data-stu-id="22010-261">If this does not happen within ~30-60 seconds, walk to where the original HoloLens was when setting the anchor to gather more environment clues.</span></span> <span data-ttu-id="22010-262">Wenn Sie der Speicherort noch nicht gesperrt ist, auf dem Gerät erneut bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="22010-262">If the location still does not lock on, redeploy to the device.</span></span>
* <span data-ttu-id="22010-263">Wenn die Geräte sind, und die app ausgeführt wird, Suchen nach den EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="22010-263">When the devices are all ready and running the app, look for the EnergyHub.</span></span> <span data-ttu-id="22010-264">Können alle stimmen Sie auf der Hologramm Speicherort und die Richtung des Texts sind aufgetreten?</span><span class="sxs-lookup"><span data-stu-id="22010-264">Can you all agree on the hologram's location and which direction the text is facing?</span></span>

## <a name="chapter-4---discovery"></a><span data-ttu-id="22010-265">Kapitel 4 – Ermittlung</span><span class="sxs-lookup"><span data-stu-id="22010-265">Chapter 4 - Discovery</span></span>

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

<span data-ttu-id="22010-266">Alle Benutzer sehen nun die gleichen – Hologramm!</span><span class="sxs-lookup"><span data-stu-id="22010-266">Everyone can now see the same hologram!</span></span> <span data-ttu-id="22010-267">Jetzt sehen wir uns an alle anderen freigegebenen holographic in unserem verbunden.</span><span class="sxs-lookup"><span data-stu-id="22010-267">Now let's see everyone else connected to our shared holographic world.</span></span> <span data-ttu-id="22010-268">In diesem Kapitel werden wir die Head-Speicherort und die Rotation der alle anderen HoloLens-Geräte in der gleichen Sitzung für die Freigabe abrufen.</span><span class="sxs-lookup"><span data-stu-id="22010-268">In this chapter, we'll grab the head location and rotation of all other HoloLens devices in the same sharing session.</span></span>

### <a name="objectives"></a><span data-ttu-id="22010-269">Ziele</span><span class="sxs-lookup"><span data-stu-id="22010-269">Objectives</span></span>

* <span data-ttu-id="22010-270">Erkennen Sie einander, in unserem gemeinsamen Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="22010-270">Discover each other in our shared experience.</span></span>
* <span data-ttu-id="22010-271">Wählen Sie aus, und geben Sie einen Player Avatar frei.</span><span class="sxs-lookup"><span data-stu-id="22010-271">Choose and share a player avatar.</span></span>
* <span data-ttu-id="22010-272">Fügen Sie die Player-Avatar neben den Köpfen.</span><span class="sxs-lookup"><span data-stu-id="22010-272">Attach the player avatar next to everyone's heads.</span></span>

### <a name="instructions"></a><span data-ttu-id="22010-273">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="22010-273">Instructions</span></span>

* <span data-ttu-id="22010-274">In der **Projektfenster** navigieren Sie zu der **Hologramme** Ordner.</span><span class="sxs-lookup"><span data-stu-id="22010-274">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="22010-275">Drag & drop die **PlayerAvatarStore** in die **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="22010-275">Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.</span></span>
* <span data-ttu-id="22010-276">In der **Projektfenster** navigieren Sie zu der **Skripts** Ordner.</span><span class="sxs-lookup"><span data-stu-id="22010-276">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="22010-277">Doppelklicken Sie auf die **AvatarSelector** Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="22010-277">Double-click the **AvatarSelector** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="22010-278">Ersetzen Sie den Inhalt durch den folgenden Code ein.</span><span class="sxs-lookup"><span data-stu-id="22010-278">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);        
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* <span data-ttu-id="22010-279">In der **Hierarchie** wählen Sie die **HologramCollection** Objekt.</span><span class="sxs-lookup"><span data-stu-id="22010-279">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="22010-280">In der **Inspektor** klicken Sie auf **Add Component**.</span><span class="sxs-lookup"><span data-stu-id="22010-280">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="22010-281">Geben Sie in das Suchfeld **Player-Manager für lokalen**.</span><span class="sxs-lookup"><span data-stu-id="22010-281">In the search box, type **Local Player Manager**.</span></span> <span data-ttu-id="22010-282">Wählen Sie das Suchergebnis.</span><span class="sxs-lookup"><span data-stu-id="22010-282">Select the search result.</span></span>
* <span data-ttu-id="22010-283">In der **Hierarchie** wählen Sie die **HologramCollection** Objekt.</span><span class="sxs-lookup"><span data-stu-id="22010-283">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="22010-284">In der **Inspektor** klicken Sie auf **Add Component**.</span><span class="sxs-lookup"><span data-stu-id="22010-284">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="22010-285">Geben Sie in das Suchfeld **Remote-Player-Manager**.</span><span class="sxs-lookup"><span data-stu-id="22010-285">In the search box, type **Remote Player Manager**.</span></span> <span data-ttu-id="22010-286">Wählen Sie das Suchergebnis.</span><span class="sxs-lookup"><span data-stu-id="22010-286">Select the search result.</span></span>
* <span data-ttu-id="22010-287">Öffnen der **HologramPlacement** Skripts in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="22010-287">Open the **HologramPlacement** script in Visual Studio.</span></span>
* <span data-ttu-id="22010-288">Ersetzen Sie den Inhalt durch den folgenden Code ein.</span><span class="sxs-lookup"><span data-stu-id="22010-288">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="22010-289">Öffnen der **AppStateManager** Skripts in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="22010-289">Open the **AppStateManager** script in Visual Studio.</span></span>
* <span data-ttu-id="22010-290">Ersetzen Sie den Inhalt durch den folgenden Code ein.</span><span class="sxs-lookup"><span data-stu-id="22010-290">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

<span data-ttu-id="22010-291">**Bereitstellen und nutzen**</span><span class="sxs-lookup"><span data-stu-id="22010-291">**Deploy and Enjoy**</span></span>
* <span data-ttu-id="22010-292">Erstellen Sie und Bereitstellen Sie des Projekts für Ihre HoloLens-Geräte.</span><span class="sxs-lookup"><span data-stu-id="22010-292">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="22010-293">Wenn Sie einen Pingen Sound hören, gefunden Sie Auswahlmenü Avatar, und wählen Sie einen Avatar mit der tippbewegung Bewegung aus.</span><span class="sxs-lookup"><span data-stu-id="22010-293">When you hear a pinging sound, find the avatar selection menu and select an avatar with the air-tap gesture.</span></span>
* <span data-ttu-id="22010-294">Wenn alle Hologramme nicht angezeigt wird, der Punkt hell rund um den Cursor wird, sobald eine andere Farbe Ihrer HoloLens mit dem Dienst kommuniziert wird: (dunkelpurpur) initialisieren, den Anker (Grün), Importieren/Exportieren von Daten (gelb) herunterladen Hochladen des Ankers (Blau).</span><span class="sxs-lookup"><span data-stu-id="22010-294">If you're not looking at any holograms, the point light around your cursor will turn a different color when your HoloLens is communicating with the service: initializing (dark purple), downloading the anchor (green), importing/exporting location data (yellow), uploading the anchor (blue).</span></span> <span data-ttu-id="22010-295">Ist Point hell rund um den Cursor auf die Standardfarbe (hell Lila), sind Sie bereit für die Interaktion mit anderen Spielern in der Sitzung.</span><span class="sxs-lookup"><span data-stu-id="22010-295">If your point light around your cursor is the default color (light purple), then you are ready to interact with other players in your session!</span></span>
* <span data-ttu-id="22010-296">Sehen Sie sich andere Personen wertsynchronisierung in Ihrem - Verbindung wird ein holographic Roboter über die Schulter unverankerte und ihre Head Bewegungen imitiert.</span><span class="sxs-lookup"><span data-stu-id="22010-296">Look at other people connected to your space - there will be a holographic robot floating above their shoulder and mimicking their head motions!</span></span>

## <a name="chapter-5---placement"></a><span data-ttu-id="22010-297">Kapitel 5 - Platzierung</span><span class="sxs-lookup"><span data-stu-id="22010-297">Chapter 5 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

<span data-ttu-id="22010-298">In diesem Kapitel werden wir nicht auf Flächen der realen Welt platziert werden Anker zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="22010-298">In this chapter, we'll make the anchor able to be placed on real-world surfaces.</span></span> <span data-ttu-id="22010-299">Wir verwenden freigegebene Koordinaten, Anker in der mittlere Punkt zwischen den alle in Verbindung, auf die freigegebene Benutzeroberfläche zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="22010-299">We'll use shared coordinates to place that anchor in the middle point between everyone connected to the shared experience.</span></span>

### <a name="objectives"></a><span data-ttu-id="22010-300">Ziele</span><span class="sxs-lookup"><span data-stu-id="22010-300">Objectives</span></span>

* <span data-ttu-id="22010-301">Platzieren Sie Hologramme, auf die räumliche Zuordnung, die anhand der HomeRuns Head-Position.</span><span class="sxs-lookup"><span data-stu-id="22010-301">Place holograms on the spatial map based on players’ head position.</span></span>

### <a name="instructions"></a><span data-ttu-id="22010-302">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="22010-302">Instructions</span></span>

* <span data-ttu-id="22010-303">In der **Projektfenster** navigieren Sie zu der **Hologramme** Ordner.</span><span class="sxs-lookup"><span data-stu-id="22010-303">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="22010-304">Drag & drop die **CustomSpatialMapping** prefab auf die **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="22010-304">Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.</span></span>
* <span data-ttu-id="22010-305">In der **Projektfenster** navigieren Sie zu der **Skripts** Ordner.</span><span class="sxs-lookup"><span data-stu-id="22010-305">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="22010-306">Doppelklicken Sie auf die **AppStateManager** Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="22010-306">Double-click the **AppStateManager** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="22010-307">Ersetzen Sie den Inhalt durch den folgenden Code ein.</span><span class="sxs-lookup"><span data-stu-id="22010-307">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to 
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a 
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* <span data-ttu-id="22010-308">In der **Projektfenster** navigieren Sie zu der **Skripts** Ordner.</span><span class="sxs-lookup"><span data-stu-id="22010-308">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="22010-309">Doppelklicken Sie auf die **HologramPlacement** Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="22010-309">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="22010-310">Ersetzen Sie den Inhalt durch den folgenden Code ein.</span><span class="sxs-lookup"><span data-stu-id="22010-310">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the 
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

<span data-ttu-id="22010-311">**Bereitstellen und nutzen**</span><span class="sxs-lookup"><span data-stu-id="22010-311">**Deploy and enjoy**</span></span>
* <span data-ttu-id="22010-312">Erstellen Sie und Bereitstellen Sie des Projekts für Ihre HoloLens-Geräte.</span><span class="sxs-lookup"><span data-stu-id="22010-312">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="22010-313">Wenn die app bereit ist, stehen in einem Kreis aus, und beachten Sie, wie die EnergyHub in der Mitte der "Jeder" angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="22010-313">When the app is ready, stand in a circle and notice how the EnergyHub appears in the center of everyone.</span></span>
* <span data-ttu-id="22010-314">Tippen Sie auf diese Option, um die EnergyHub zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="22010-314">Tap to place the EnergyHub.</span></span>
* <span data-ttu-id="22010-315">Führen Sie den Befehl mit dem Voice "Target zurücksetzen", wählen Sie die EnergyHub Sichern von und arbeiten zusammen als eine Gruppe, die – Hologramm an einem neuen Speicherort zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="22010-315">Try the voice command 'Reset Target' to pick the EnergyHub back up and work together as a group to move the hologram to a new location.</span></span>

## <a name="chapter-6---real-world-physics"></a><span data-ttu-id="22010-316">Kapitel 6 – Physik der realen Welt</span><span class="sxs-lookup"><span data-stu-id="22010-316">Chapter 6 - Real-World Physics</span></span>

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

<span data-ttu-id="22010-317">In diesem Kapitel wird Hologramme hinzugefügt, die reale Flächen abprallen.</span><span class="sxs-lookup"><span data-stu-id="22010-317">In this chapter we'll add holograms that bounce off real-world surfaces.</span></span> <span data-ttu-id="22010-318">Sehen Sie sich der Speicherplatz gänzlich mit Projekten, die von Ihnen und Ihren Freunden gestartet!</span><span class="sxs-lookup"><span data-stu-id="22010-318">Watch your space fill up with projects launched by both you and your friends!</span></span>

### <a name="objectives"></a><span data-ttu-id="22010-319">Ziele</span><span class="sxs-lookup"><span data-stu-id="22010-319">Objectives</span></span>

* <span data-ttu-id="22010-320">Starten Sie die Projektile, die reale Flächen abprallen.</span><span class="sxs-lookup"><span data-stu-id="22010-320">Launch projectiles that bounce off real-world surfaces.</span></span>
* <span data-ttu-id="22010-321">Geben Sie die Projektile aus, damit sie von anderen Spielern angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="22010-321">Share the projectiles so other players can see them.</span></span>

### <a name="instructions"></a><span data-ttu-id="22010-322">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="22010-322">Instructions</span></span>

* <span data-ttu-id="22010-323">In der **Hierarchie** wählen Sie die **HologramCollection** Objekt.</span><span class="sxs-lookup"><span data-stu-id="22010-323">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="22010-324">In der **Inspektor** klicken Sie auf **Add Component**.</span><span class="sxs-lookup"><span data-stu-id="22010-324">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="22010-325">Geben Sie in das Suchfeld **Projektil Startprogramm**.</span><span class="sxs-lookup"><span data-stu-id="22010-325">In the search box, type **Projectile Launcher**.</span></span> <span data-ttu-id="22010-326">Wählen Sie das Suchergebnis.</span><span class="sxs-lookup"><span data-stu-id="22010-326">Select the search result.</span></span>

<span data-ttu-id="22010-327">**Bereitstellen und nutzen**</span><span class="sxs-lookup"><span data-stu-id="22010-327">**Deploy and enjoy**</span></span>
* <span data-ttu-id="22010-328">Erstellen und an Ihre HoloLens-Geräte bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="22010-328">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="22010-329">Wenn die app auf allen Geräten ausgeführt wird, führen Sie eine tippbewegung um Projektil auf Flächen der realen Welt zu starten.</span><span class="sxs-lookup"><span data-stu-id="22010-329">When the app is running on all devices, perform an air-tap to launch projectile at real world surfaces.</span></span>
* <span data-ttu-id="22010-330">Erfahren Sie, was geschieht, wenn Ihre Projektil mit einen anderen Player Avatar kollidiert!</span><span class="sxs-lookup"><span data-stu-id="22010-330">See what happens when your projectile collides with another player's avatar!</span></span>

## <a name="chapter-7---grand-finale"></a><span data-ttu-id="22010-331">Kapitel 7 – Grand Erfahrung</span><span class="sxs-lookup"><span data-stu-id="22010-331">Chapter 7 - Grand Finale</span></span>

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

<span data-ttu-id="22010-332">In diesem Kapitel werden wir ein Portal aufdecken, die nur bei der Zusammenarbeit ermittelt werden können.</span><span class="sxs-lookup"><span data-stu-id="22010-332">In this chapter, we'll uncover a portal that can only be discovered with collaboration.</span></span>

### <a name="objectives"></a><span data-ttu-id="22010-333">Ziele</span><span class="sxs-lookup"><span data-stu-id="22010-333">Objectives</span></span>

* <span data-ttu-id="22010-334">Zusammenarbeiten Sie, um genügend Projektile auf der Anker aus, um ein Geheimnis Portal gewinnen starten!</span><span class="sxs-lookup"><span data-stu-id="22010-334">Work together to launch enough projectiles at the anchor to uncover a secret portal!</span></span>

### <a name="instructions"></a><span data-ttu-id="22010-335">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="22010-335">Instructions</span></span>

* <span data-ttu-id="22010-336">In der **Projektfenster** navigieren Sie zu der **Hologramme** Ordner.</span><span class="sxs-lookup"><span data-stu-id="22010-336">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="22010-337">Drag & drop die **Underworld** -Objekt als eine **untergeordnetes Element des HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="22010-337">Drag and drop the **Underworld** asset as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="22010-338">Mit **HologramCollection** ausgewählt ist, klicken Sie auf die **Add Component** Schaltfläche der **Inspektor**.</span><span class="sxs-lookup"><span data-stu-id="22010-338">With **HologramCollection** selected, click the **Add Component** button in the **Inspector**.</span></span>
* <span data-ttu-id="22010-339">Geben Sie im Menü, in das Suchfeld **ExplodeTarget**.</span><span class="sxs-lookup"><span data-stu-id="22010-339">In the menu, type in the search box **ExplodeTarget**.</span></span> <span data-ttu-id="22010-340">Wählen Sie das Suchergebnis.</span><span class="sxs-lookup"><span data-stu-id="22010-340">Select the search result.</span></span>
* <span data-ttu-id="22010-341">Mit **HologramCollection** ausgewählten, von der **Hierarchie** ziehen Sie die **EnergyHub** -Objekt an die **Ziel** -Feld in der **Inspektor**.</span><span class="sxs-lookup"><span data-stu-id="22010-341">With **HologramCollection** selected, from the **Hierarchy** drag the **EnergyHub** object to the **Target** field in the **Inspector**.</span></span>
* <span data-ttu-id="22010-342">Mit **HologramCollection** ausgewählten, von der **Hierarchie** ziehen Sie die **Underworld** -Objekt an die **Underworld** -Feld in der  **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="22010-342">With **HologramCollection** selected, from the **Hierarchy** drag the **Underworld** object to the **Underworld** field in the **Inspector**.</span></span>

<span data-ttu-id="22010-343">**Bereitstellen und nutzen**</span><span class="sxs-lookup"><span data-stu-id="22010-343">**Deploy and enjoy**</span></span>
* <span data-ttu-id="22010-344">Erstellen und an Ihre HoloLens-Geräte bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="22010-344">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="22010-345">Wenn die app gestartet wurde, werden zusammen zum Starten der Projektile auf die EnergyHub zusammenarbeiten.</span><span class="sxs-lookup"><span data-stu-id="22010-345">When the app has launched, collaborate together to launch projectiles at the EnergyHub.</span></span>
* <span data-ttu-id="22010-346">Wenn die Underworld angezeigt wird, starten Sie die Projektile auf Underworld Roboter (Treffer einem Roboter ausgegangen dreifache für zusätzliche Spaß).</span><span class="sxs-lookup"><span data-stu-id="22010-346">When the underworld appears, launch projectiles at underworld robots (hit a robot three times for extra fun).</span></span>
