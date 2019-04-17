---
title: MR räumlich 220 - räumliche sound
description: Führen Sie diese Codierung Exemplarische Vorgehensweise mit Unity, Visual Studio und HoloLens um die Details der räumlichen sound Konzepte zu erfahren.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Holotoolkit, Mixedrealitytoolkit, Mixedrealitytoolkit-Unity, Academy, Tutorial, räumliche sound
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593832"
---
>[!NOTE]
><span data-ttu-id="5ff94-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="5ff94-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="5ff94-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="5ff94-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="5ff94-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5ff94-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="5ff94-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="5ff94-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="5ff94-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="5ff94-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="5ff94-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="5ff94-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="5ff94-110">MR Spatial 220: Raumklang</span><span class="sxs-lookup"><span data-stu-id="5ff94-110">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="5ff94-111">[Räumliche Sound](spatial-sound.md) breathes Leben in Hologramme und sorgt dafür, dass in unserer Welt.</span><span class="sxs-lookup"><span data-stu-id="5ff94-111">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="5ff94-112">Hologramme von Licht und Sound bestehen, und wenn Sie doch Ihre Hologramme aus den Augen zu verlieren, räumliche Sound können Sie zu finden.</span><span class="sxs-lookup"><span data-stu-id="5ff94-112">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="5ff94-113">Es ist kein räumlicher Sound wie typische Sounds, die Sie auf die Radio hören würde, Klänge, mit denen im 3D-Raum positioniert ist.</span><span class="sxs-lookup"><span data-stu-id="5ff94-113">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="5ff94-114">Räumliche Sound können Sie machen Hologramme sound scheinen hinter, neben oder sogar auf den Kopf zu sein!</span><span class="sxs-lookup"><span data-stu-id="5ff94-114">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="5ff94-115">In diesem Kurs führen Sie folgende Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="5ff94-115">In this course, you will:</span></span>

* <span data-ttu-id="5ff94-116">Konfigurieren Sie Ihre Entwicklungsumgebung für Microsoft Spatial Sound verwenden.</span><span class="sxs-lookup"><span data-stu-id="5ff94-116">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="5ff94-117">Verwenden Sie räumliche Sound, um Interaktionen zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="5ff94-117">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="5ff94-118">Verwenden Sie räumliche Sound in Verbindung mit räumlichen zuordnen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-118">Use Spatial Sound in conjunction with Spatial Mapping.</span></span>
* <span data-ttu-id="5ff94-119">Erfahren Sie, Entwurf und die Verwendung von bewährten Methoden.</span><span class="sxs-lookup"><span data-stu-id="5ff94-119">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="5ff94-120">Verwendung von Tönen verbessern Spezialeffekte zu erzeugen, und schalten den Benutzer in die Welt der Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="5ff94-120">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="5ff94-121">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="5ff94-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="5ff94-122">Kurs</span><span class="sxs-lookup"><span data-stu-id="5ff94-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="5ff94-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="5ff94-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="5ff94-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="5ff94-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="5ff94-125">MR Spatial 220: Raumklang</span><span class="sxs-lookup"><span data-stu-id="5ff94-125">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="5ff94-126">✔️</span><span class="sxs-lookup"><span data-stu-id="5ff94-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="5ff94-127">✔️</span><span class="sxs-lookup"><span data-stu-id="5ff94-127">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="5ff94-128">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="5ff94-128">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="5ff94-129">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="5ff94-129">Prerequisites</span></span>

* <span data-ttu-id="5ff94-130">Ein Windows 10-PCs mit dem richtigen konfiguriert [-Tools installiert](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="5ff94-130">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="5ff94-131">Einige grundlegende C# Programmierkenntnisse.</span><span class="sxs-lookup"><span data-stu-id="5ff94-131">Some basic C# programming ability.</span></span>
* <span data-ttu-id="5ff94-132">Sie sollten abgeschlossen haben [MR Grundlagen 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="5ff94-132">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="5ff94-133">Ein Gerät HoloLens [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="5ff94-133">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="5ff94-134">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="5ff94-134">Project files</span></span>

* <span data-ttu-id="5ff94-135">Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) vom Projekt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="5ff94-135">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="5ff94-136"> Ist Unity 2017.2 oder höher erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5ff94-136"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="5ff94-137">Wenn Sie weitere Unity 5.6-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span><span class="sxs-lookup"><span data-stu-id="5ff94-137">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="5ff94-138">Diese Version kann nicht mehr auf dem neuesten Stand sein.</span><span class="sxs-lookup"><span data-stu-id="5ff94-138">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="5ff94-139">Wenn Sie weitere Unity 5.5-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span><span class="sxs-lookup"><span data-stu-id="5ff94-139">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="5ff94-140"> Diese Version kann nicht mehr auf dem neuesten Stand sein.</span><span class="sxs-lookup"><span data-stu-id="5ff94-140"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="5ff94-141">Wenn Sie weitere 5.4 von Unity-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span><span class="sxs-lookup"><span data-stu-id="5ff94-141">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="5ff94-142"> Diese Version kann nicht mehr auf dem neuesten Stand sein.</span><span class="sxs-lookup"><span data-stu-id="5ff94-142"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="5ff94-143">Un-Archive die Dateien auf dem Desktop oder andere einfach auf den Speicherort zugreifen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="5ff94-144">Wenn Sie vor dem Herunterladen, den Quellcode ansehen möchten es [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span><span class="sxs-lookup"><span data-stu-id="5ff94-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="5ff94-145">Fehler und Anmerkungen zu dieser Version</span><span class="sxs-lookup"><span data-stu-id="5ff94-145">Errata and Notes</span></span>

* <span data-ttu-id="5ff94-146">"Nur eigenen Code aktivieren" muss deaktiviert sein (*deaktiviert*) in Visual Studio unter Extras -> Optionen-Debuggen >, um die Haltepunkte in Ihrem Code.</span><span class="sxs-lookup"><span data-stu-id="5ff94-146">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="5ff94-147">Kapitel 1: Unity-Setup</span><span class="sxs-lookup"><span data-stu-id="5ff94-147">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="5ff94-148">Ziele</span><span class="sxs-lookup"><span data-stu-id="5ff94-148">Objectives</span></span>

* <span data-ttu-id="5ff94-149">Ändern von Unity sound-Konfiguration zum Microsoft Spatial Sound verwenden.</span><span class="sxs-lookup"><span data-stu-id="5ff94-149">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="5ff94-150">Fügen Sie auf ein Objekt in Unity 3D Sound hinzu.</span><span class="sxs-lookup"><span data-stu-id="5ff94-150">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="5ff94-151">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="5ff94-151">Instructions</span></span>

* <span data-ttu-id="5ff94-152">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="5ff94-152">Start Unity.</span></span>
* <span data-ttu-id="5ff94-153">Wählen Sie **öffnen**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-153">Select **Open**.</span></span>
* <span data-ttu-id="5ff94-154">Navigieren Sie zu Ihrem Desktop und suchen Sie den Ordner Sie zuvor nicht archiviert.</span><span class="sxs-lookup"><span data-stu-id="5ff94-154">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="5ff94-155">Klicken Sie auf die **Starting\Decibel** Ordner, und drücken Sie dann die **Ordner auswählen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="5ff94-155">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="5ff94-156">Warten Sie auf das Projekt im Unity geladen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-156">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="5ff94-157">In der **Projekt** Bereich öffnen **Scenes\Decibel.unity**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-157">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="5ff94-158">In der **Hierarchie** erweitern **HologramCollection** , und wählen Sie **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-158">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="5ff94-159">Erweitern Sie in der Eigenschaftenanalyse **AudioSource** und beachten Sie, dass es keine **Spatialize** Kontrollkästchen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-159">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="5ff94-160">Standardmäßig wird in Unity eine Spatializer-Plug-Ins nicht geladen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-160">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="5ff94-161">Die folgenden Schritte können räumlich Sound im Projekt.</span><span class="sxs-lookup"><span data-stu-id="5ff94-161">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="5ff94-162">Navigieren Sie im oberen Menü Unity zu **Bearbeiten > Projekteinstellungen > Audio**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-162">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="5ff94-163">Suchen der **Spatializer-Plug-Ins** Dropdown-Liste, und wählen Sie **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-163">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="5ff94-164">In der **Hierarchie** wählen **HologramCollection > P0LY**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-164">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="5ff94-165">In der **Inspektor** Bereich, suchen Sie nach der **Audio Source** Komponente.</span><span class="sxs-lookup"><span data-stu-id="5ff94-165">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="5ff94-166">Überprüfen Sie die **Spatialize** Kontrollkästchen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-166">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="5ff94-167">Ziehen Sie die **räumliche Blend** Schieberegler ganz nach **3D**, oder geben Sie **1** in das Bearbeitungsfeld.</span><span class="sxs-lookup"><span data-stu-id="5ff94-167">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="5ff94-168">Jetzt erstellen Sie das Projekt in Unity und konfigurieren die Projektmappe in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5ff94-168">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="5ff94-169">Wählen Sie in Unity **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-169">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="5ff94-170">Klicken Sie auf **öffnen Szenen hinzufügen** die Szene hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-170">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="5ff94-171">Wählen Sie **universelle Windows-Plattform** in die **Plattform** aus, und klicken Sie auf **Plattform wechseln**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-171">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="5ff94-172">Wenn Sie speziell für HoloLens entwickeln, legen Sie **Zielgerät** zu **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-172">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="5ff94-173">Andernfalls lassen Sie es auf **jedes Gerät**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-173">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="5ff94-174">Stellen Sie sicher **Build Type** nastaven NA hodnotu **D3D** und **SDK** nastaven NA hodnotu **zuletzt installierte** (die sollte SDK 16299 oder höher sein).</span><span class="sxs-lookup"><span data-stu-id="5ff94-174">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="5ff94-175">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-175">Click **Build**.</span></span>
7. <span data-ttu-id="5ff94-176">Erstellen Sie eine **neuer Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="5ff94-176">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="5ff94-177">Mausklick die **App** Ordner.</span><span class="sxs-lookup"><span data-stu-id="5ff94-177">Single click the **App** folder.</span></span>
9. <span data-ttu-id="5ff94-178">Drücken Sie **wählen Sie Ordner**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-178">Press **Select Folder**.</span></span>

<span data-ttu-id="5ff94-179">Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5ff94-179">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="5ff94-180">Öffnen der **App** Ordner.</span><span class="sxs-lookup"><span data-stu-id="5ff94-180">Open the **App** folder.</span></span>
2. <span data-ttu-id="5ff94-181">Öffnen der **Dezibel Visual Studio-Projektmappe**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-181">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="5ff94-182">Wenn für HoloLens bereitstellen zu können:</span><span class="sxs-lookup"><span data-stu-id="5ff94-182">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="5ff94-183">Verwenden obere auf der Symbolleiste in Visual Studio, ändern Sie das Ziel vom Debugmodus in den **Version** und ARM, **X86**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="5ff94-184">Klicken Sie auf den Dropdownpfeil neben der Schaltfläche mit den lokalen Computer, und wählen **Remotecomputer**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-184">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="5ff94-185">Geben Sie **die HoloLens-Geräte-IP-Adresse** und legen Sie den Authentifizierungsmodus auf **universell (unverschlüsseltes Protokoll)**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-185">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="5ff94-186">Klicken Sie auf **Auswählen**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-186">Click **Select**.</span></span> <span data-ttu-id="5ff94-187">Wenn Sie Ihre IP-Adresse des Geräts nicht kennen, suchen Sie im **Einstellungen > Netzwerk und Internet > Erweiterte Optionen**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-187">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="5ff94-188">Klicken Sie in der Menüleiste im oberen Bereich auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-188">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="5ff94-189">Ist dies beim ersten auf Ihrem Gerät bereitstellen, Sie müssen [verbinden Sie es mit Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span><span class="sxs-lookup"><span data-stu-id="5ff94-189">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span></span>

<span data-ttu-id="5ff94-190">Wenn eine immersive Kopfhörer bereitstellen:</span><span class="sxs-lookup"><span data-stu-id="5ff94-190">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="5ff94-191">Verwenden obere auf der Symbolleiste in Visual Studio, ändern Sie das Ziel vom Debugmodus in den **Version** und ARM, **X64**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-191">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="5ff94-192">Stellen Sie sicher, dass das Bereitstellungsziel nastaven NA hodnotu **lokalen Computer**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-192">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="5ff94-193">Klicken Sie in der Menüleiste im oberen Bereich auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-193">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="5ff94-194">Kapitel 2: räumliche Sound- und Interaktion</span><span class="sxs-lookup"><span data-stu-id="5ff94-194">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="5ff94-195">Ziele</span><span class="sxs-lookup"><span data-stu-id="5ff94-195">Objectives</span></span>

* <span data-ttu-id="5ff94-196">Verbessern Sie – Hologramm wirklichkeitsgetreuen Bilder mithilfe von Sounds.</span><span class="sxs-lookup"><span data-stu-id="5ff94-196">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="5ff94-197">Weiterleiten des Benutzers Blicke Sound verwenden.</span><span class="sxs-lookup"><span data-stu-id="5ff94-197">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="5ff94-198">Geben Sie mithilfe von Sound Geste-Feedback.</span><span class="sxs-lookup"><span data-stu-id="5ff94-198">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="5ff94-199">Teil 1 – Verbesserung realer zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="5ff94-199">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="5ff94-200">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="5ff94-200">Key Concepts</span></span>

* <span data-ttu-id="5ff94-201">Spatialize – Hologramm Sounds.</span><span class="sxs-lookup"><span data-stu-id="5ff94-201">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="5ff94-202">Sound Quellen, die am einen geeigneten Speicherort auf dem Hologramm eingefügt werden soll.</span><span class="sxs-lookup"><span data-stu-id="5ff94-202">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="5ff94-203">Die gewünschte Position für den Sound wird die Hologramm abhängig.</span><span class="sxs-lookup"><span data-stu-id="5ff94-203">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="5ff94-204">Wenn einem Benutzer, der die – Hologramm ist, sollten z. B. Schallquelle Mund und nicht die Füße gespeichert sein.</span><span class="sxs-lookup"><span data-stu-id="5ff94-204">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="5ff94-205">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="5ff94-205">Instructions</span></span>

<span data-ttu-id="5ff94-206">Die folgenden Anweisungen werden ggf. ein Hologramm Sound spatialized zuordnen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-206">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="5ff94-207">In der **Hierarchie** erweitern **HologramCollection** , und wählen Sie **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-207">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="5ff94-208">In der **Inspektor** im Bereich der **AudioSource**, klicken Sie auf den Kreis neben **AudioClip** , und wählen Sie **PolyHover** aus der Popupliste.</span><span class="sxs-lookup"><span data-stu-id="5ff94-208">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="5ff94-209">Klicken Sie auf den Kreis neben **Ausgabe** , und wählen Sie **SoundEffects** aus der Popupliste.</span><span class="sxs-lookup"><span data-stu-id="5ff94-209">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="5ff94-210">Projekt Dezibel verwendet eine Unity **AudioMixer** -Komponente verwendet, damit Geräuschpegel für Gruppen von Sounds anpassen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-210">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="5ff94-211">Durch Gruppierung von Sounds auf diese Weise kann das gesamte Volume und gleichzeitig die relative Menge der einzelnen Sound angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="5ff94-211">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="5ff94-212">In der **AudioSource**, erweitern Sie **3D Sound Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-212">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="5ff94-213">Legen Sie **Doppler-Ebene** zu **0**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-213">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="5ff94-214">Festlegen von Doppler Ebene auf 0 (null) deaktiviert die Änderungen in der Stimmhöhe verursacht werden, die in Motion (entweder die Hologramm oder der Benutzer).</span><span class="sxs-lookup"><span data-stu-id="5ff94-214">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="5ff94-215">Ein klassisches Beispiel Doppler ist eine schnelle, flexible Auto.</span><span class="sxs-lookup"><span data-stu-id="5ff94-215">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="5ff94-216">Wenn sich das Fahrzeug stationären Listener nähert, steigt die Schriftbreite des Datenbankmoduls.</span><span class="sxs-lookup"><span data-stu-id="5ff94-216">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="5ff94-217">Wenn den Listener übergibt, verringert sich die Schriftbreite mit Abstand.</span><span class="sxs-lookup"><span data-stu-id="5ff94-217">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="5ff94-218">Teil 2: Weiterleiten des Benutzers Blicke</span><span class="sxs-lookup"><span data-stu-id="5ff94-218">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="5ff94-219">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="5ff94-219">Key Concepts</span></span>

* <span data-ttu-id="5ff94-220">Verwenden Sie die Aufmerksamkeit auf wichtige Hologramme Sound.</span><span class="sxs-lookup"><span data-stu-id="5ff94-220">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="5ff94-221">Die Ohren besser, in denen die Augen suchen soll.</span><span class="sxs-lookup"><span data-stu-id="5ff94-221">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="5ff94-222">Das Gehirn hat bestimmte Erwartungen Gelernten.</span><span class="sxs-lookup"><span data-stu-id="5ff94-222">The brain has some learned expectations.</span></span>

<span data-ttu-id="5ff94-223">Ein Beispiel für gelernten Erwartungen ist, dass Vögel in der Regel über den Köpfen der Menschen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-223">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="5ff94-224">Wenn ein Benutzer einen Sound Bird hört, ist ihre erste Reaktion nachschlagen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-224">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="5ff94-225">Platzieren einer Bird unterhalb der Benutzer kann Ihnen den Klang, aber nicht auf die – Hologramm basierend auf der Annahme zu suchen müssen, finden Sie die richtige Richtung zeigenden führen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-225">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="5ff94-226">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="5ff94-226">Instructions</span></span>

<span data-ttu-id="5ff94-227">Die folgenden Anweisungen aktivieren P0LY hinter, ausblenden, sodass Sie Sound verwenden können, die – Hologramm gesucht werden soll.</span><span class="sxs-lookup"><span data-stu-id="5ff94-227">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="5ff94-228">In der **Hierarchie** wählen **Managern**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-228">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="5ff94-229">In der **Inspektor** Bereich, suchen Sie nach **Spracherkennung Eingabe Handler**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-229">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="5ff94-230">In **Spracherkennung Eingabe Handler**, erweitern Sie **wechseln ausblenden**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-230">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="5ff94-231">Änderung **keine Funktion** zu **PolyActions.GoHide**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-231">Change **No Function** to **PolyActions.GoHide**.</span></span>

![Keyword: Wechseln Sie ausblenden](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="5ff94-233">Teil 3 – Geste Feedback</span><span class="sxs-lookup"><span data-stu-id="5ff94-233">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="5ff94-234">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="5ff94-234">Key Concepts</span></span>

* <span data-ttu-id="5ff94-235">Bietet dem Benutzer mit positiven Geste Bestätigung mithilfe von sound</span><span class="sxs-lookup"><span data-stu-id="5ff94-235">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="5ff94-236">Des Benutzers, übermäßig laut Sounds Get auf die Weise nicht zu überlasten</span><span class="sxs-lookup"><span data-stu-id="5ff94-236">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="5ff94-237">Feine Sounds Arbeit best - nicht überlagern, die Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="5ff94-237">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="5ff94-238">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="5ff94-238">Instructions</span></span>

* <span data-ttu-id="5ff94-239">In der **Hierarchie** erweitern **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-239">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="5ff94-240">Erweitern Sie **EnergyHub** , und wählen Sie **Base**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-240">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="5ff94-241">In der **Inspektor** auf **Add Component** und fügen **Sound Gestenhandler**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-241">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="5ff94-242">In **Sound Gestenhandler**, klicken Sie auf den Kreis neben **Navigation Schritte Clip** und **Navigation aktualisiert Clip** , und wählen Sie **RotateClick**aus der Popupliste für beide.</span><span class="sxs-lookup"><span data-stu-id="5ff94-242">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="5ff94-243">Doppelklicken Sie auf "GestureSoundHandler" in Visual Studio geladen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-243">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="5ff94-244">Geste Sound-Ereignishandler führt die folgenden Aufgaben durch:</span><span class="sxs-lookup"><span data-stu-id="5ff94-244">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="5ff94-245">Erstellen und Konfigurieren einer **AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-245">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="5ff94-246">Ort der **AudioSource** am Speicherort des entsprechenden **"gameobject"**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-246">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="5ff94-247">Spielt den **AudioClip** der Bewegung zugeordneten.</span><span class="sxs-lookup"><span data-stu-id="5ff94-247">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="5ff94-248">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="5ff94-248">Build and Deploy</span></span>

1. <span data-ttu-id="5ff94-249">Wählen Sie in Unity **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-249">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="5ff94-250">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-250">Click **Build**.</span></span>
3. <span data-ttu-id="5ff94-251">Mausklick die **App** Ordner.</span><span class="sxs-lookup"><span data-stu-id="5ff94-251">Single click the **App** folder.</span></span>
4. <span data-ttu-id="5ff94-252">Drücken Sie **wählen Sie Ordner**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-252">Press **Select Folder**.</span></span>

<span data-ttu-id="5ff94-253">Überprüfen Sie, dass die Symbolleiste "Release", "x 86" oder "X64" und "Remotegerät" lautet.</span><span class="sxs-lookup"><span data-stu-id="5ff94-253">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="5ff94-254">Wenn dies nicht der Fall ist, dies ist die Codierung Instanz von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5ff94-254">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="5ff94-255">Sie müssen möglicherweise die Lösung über den App-Ordner erneut zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-255">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="5ff94-256">Wenn Sie dazu aufgefordert werden, laden Sie die Projektdateien.</span><span class="sxs-lookup"><span data-stu-id="5ff94-256">If prompted, reload the project files.</span></span>
* <span data-ttu-id="5ff94-257">Wie zuvor in Visual Studio bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-257">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="5ff94-258">Nachdem die Anwendung bereitgestellt wird:</span><span class="sxs-lookup"><span data-stu-id="5ff94-258">After the application is deployed:</span></span>

* <span data-ttu-id="5ff94-259">Beachten Sie, wie der Sound ändert, während Sie sich auf P0LY bewegen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-259">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="5ff94-260">Sagen Sie *"Wechseln Sie verbergen"* P0LY an eine Position hinter Ihnen verschieben vornehmen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-260">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="5ff94-261">Finden Sie es, indem Sie den Sound.</span><span class="sxs-lookup"><span data-stu-id="5ff94-261">Find it by the sound.</span></span>
* <span data-ttu-id="5ff94-262">Bestaunen Sie an der Basis des Energie-Hubs.</span><span class="sxs-lookup"><span data-stu-id="5ff94-262">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="5ff94-263">Tippen Sie auf, und ziehen Sie nach links oder rechts drehen den – Hologramm, und beachten, wie der Sound durch Klicken auf die Aktion bestätigt.</span><span class="sxs-lookup"><span data-stu-id="5ff94-263">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="5ff94-264">Hinweis: Es ist ein Text-Bereich, der Tag-along mit Ihnen wird ein.</span><span class="sxs-lookup"><span data-stu-id="5ff94-264">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="5ff94-265">Diese werden die verfügbaren Stimmbefehle enthalten, die Sie in diesem Kurs verwenden können.</span><span class="sxs-lookup"><span data-stu-id="5ff94-265">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="5ff94-266">Kapitel 3: räumliche Sound und räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="5ff94-266">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="5ff94-267">Ziele</span><span class="sxs-lookup"><span data-stu-id="5ff94-267">Objectives</span></span>

* <span data-ttu-id="5ff94-268">Interaktion zwischen Hologramme und die reale Welt, die mit der Sound zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-268">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="5ff94-269">Verdeckt Sound mithilfe der realen Welt.</span><span class="sxs-lookup"><span data-stu-id="5ff94-269">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="5ff94-270">Teil 1 – die Interaktion der realen Welt</span><span class="sxs-lookup"><span data-stu-id="5ff94-270">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="5ff94-271">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="5ff94-271">Key Concepts</span></span>

* <span data-ttu-id="5ff94-272">Physische Objekte in der Regel einen Sound vornehmen, wenn festgestellt wird eine Fläche oder einem anderen Objekt.</span><span class="sxs-lookup"><span data-stu-id="5ff94-272">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="5ff94-273">Sounds sollte innerhalb der Umgebung geeigneten Kontext.</span><span class="sxs-lookup"><span data-stu-id="5ff94-273">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="5ff94-274">Festlegen einer Tasse in einer Tabelle sollten z. B. ruhigerer Sound als eine Boulder auf einen Teil-Metal-Computern löschen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-274">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="5ff94-275">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="5ff94-275">Instructions</span></span>

* <span data-ttu-id="5ff94-276">In der **Hierarchie** erweitern **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-276">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="5ff94-277">Erweitern Sie **EnergyHub**Option **Base**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-277">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="5ff94-278">In der **Inspektor** auf **Add Component** und fügen **tippen, direkt mit Sound- und Aktion**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-278">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="5ff94-279">In **Tippen Sie auf, um anstelle von Sounds und Aktion**:</span><span class="sxs-lookup"><span data-stu-id="5ff94-279">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="5ff94-280">Überprüfen Sie **Platzieren von übergeordneten auf Tap**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-280">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="5ff94-281">Legen Sie **Platzierung Sound** zu **Ort**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-281">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="5ff94-282">Legen Sie **Pickup Sound** zu **Pickup**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-282">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="5ff94-283">Drücken Sie die + in der unteren rechten in beiden Verzeichnissen **bei Pickup Aktion** und **bei Platzierung Aktion**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-283">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="5ff94-284">Ziehen Sie EnergyHub aus der Szene in der **None (Objekt)** Felder.</span><span class="sxs-lookup"><span data-stu-id="5ff94-284">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="5ff94-285">Klicken Sie unter **bei Pickup Aktion**, klicken Sie auf **keine Funktion** -> **EnergyHubBase** -> **ResetAnimation**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-285">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="5ff94-286">Klicken Sie unter **bei Platzierung Aktion**, klicken Sie auf **keine Funktion** -> **EnergyHubBase** -> **OnSelect**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-286">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![Tippen Sie auf, um anstelle von Sounds und Aktion](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="5ff94-288">Teil 2 – Sound verdecken.</span><span class="sxs-lookup"><span data-stu-id="5ff94-288">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="5ff94-289">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="5ff94-289">Key Concepts</span></span>

* <span data-ttu-id="5ff94-290">Sound, wie Licht, kann okkludierte sein.</span><span class="sxs-lookup"><span data-stu-id="5ff94-290">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="5ff94-291">Ein klassisches Beispiel ist eine Concert Hall.</span><span class="sxs-lookup"><span data-stu-id="5ff94-291">A classic example is a concert hall.</span></span> <span data-ttu-id="5ff94-292">Wenn ein Listener verfügbar ist, außerhalb des Unternehmens und die Tür geschlossen ist, die dumpf Musik und Sound.</span><span class="sxs-lookup"><span data-stu-id="5ff94-292">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="5ff94-293">Es ist auch in der Regel eine Reduzierung des Volumens.</span><span class="sxs-lookup"><span data-stu-id="5ff94-293">There is also typically a reduction in volume.</span></span> <span data-ttu-id="5ff94-294">Wenn die Tür geöffnet wird, ist das gesamte Spektrum von den Sound am des tatsächlichen Umfangs hören.</span><span class="sxs-lookup"><span data-stu-id="5ff94-294">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="5ff94-295">Hohe Auslastung Sounds sind in der Regel mehr als Frequenzen absorbiert.</span><span class="sxs-lookup"><span data-stu-id="5ff94-295">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="5ff94-296">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="5ff94-296">Instructions</span></span>

* <span data-ttu-id="5ff94-297">In der **Hierarchie** erweitern **HologramCollection** , und wählen Sie **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-297">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="5ff94-298">In der **Inspektor** auf **Add Component** und fügen **Audio Korrekturemitter**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-298">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="5ff94-299">Die Korrekturemitter für Audio-Klasse bietet die folgenden Features:</span><span class="sxs-lookup"><span data-stu-id="5ff94-299">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="5ff94-300">Stellt alle Änderungen auf das Volume von der **AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-300">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="5ff94-301">Führt eine **Physics.RaycastNonAlloc** aus Position in Richtung des Benutzers die **"gameobject"** , die **AudioEmitter** angefügt ist.</span><span class="sxs-lookup"><span data-stu-id="5ff94-301">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="5ff94-302">Die RaycastNonAlloc-Methode wird zur leistungsoptimierung verwendet, um Zuordnungen sowie die Anzahl der zurückgegebenen Ergebnisse zu beschränken.</span><span class="sxs-lookup"><span data-stu-id="5ff94-302">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="5ff94-303">Für jede **IAudioInfluencer** auftritt, ruft der **ApplyEffect** Methode.</span><span class="sxs-lookup"><span data-stu-id="5ff94-303">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="5ff94-304">Für jeden vorherigen **IAudioInfluencer** , nicht mehr festgestellt werden, Aufruf der **RemoveEffect** Methode.</span><span class="sxs-lookup"><span data-stu-id="5ff94-304">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="5ff94-305">Beachten Sie, dass AudioEmitter auf pro-Frame-Basis auf menschliche Zeitskalen, im Gegensatz zu updates.</span><span class="sxs-lookup"><span data-stu-id="5ff94-305">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="5ff94-306">Dies geschieht, da die Menschen in der Regel nicht schnell genug für den Effekt, die häufiger als einmal pro Quartal oder eine halbe Sekunde aktualisiert werden müssen verschieben.</span><span class="sxs-lookup"><span data-stu-id="5ff94-306">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="5ff94-307">Hologramme, Teleport schnell von einem Speicherort in einen anderen kann die Illusion unterbrochen werden.</span><span class="sxs-lookup"><span data-stu-id="5ff94-307">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="5ff94-308">In der **Hierarchie** erweitern **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-308">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="5ff94-309">Erweitern Sie **EnergyHub** , und wählen Sie **BlobOutside**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-309">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="5ff94-310">In der **Inspektor** auf **Add Component** und fügen **Audio Occluder**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-310">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="5ff94-311">In **Audio Occluder**legen **Grenzwert Häufigkeit** zu **1500**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-311">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="5ff94-312">Diese Einstellung beschränkt die AudioSource Frequenzen für 1500 Hz und niedriger.</span><span class="sxs-lookup"><span data-stu-id="5ff94-312">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="5ff94-313">Legen Sie **Pass-Through-Datenträger** zu **0.9**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-313">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="5ff94-314">Diese Einstellung verringert die Menge an die AudioSource 90 % der aktuellen Ebene.</span><span class="sxs-lookup"><span data-stu-id="5ff94-314">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="5ff94-315">Audio Occluder implementiert IAudioInfluencer auf:</span><span class="sxs-lookup"><span data-stu-id="5ff94-315">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="5ff94-316">Anwenden einer verdecken Effekt mithilfe einer **AudioLowPassFilter** dem zugeordnet, der **AudioSource** verwalteten kaufen der **AudioEmitter**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-316">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="5ff94-317">Gilt die AudioSource Volume Attenuation hinzu.</span><span class="sxs-lookup"><span data-stu-id="5ff94-317">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="5ff94-318">Deaktiviert die Auswirkungen von einer neutralen Grenzfrequenz festlegen, und Deaktivieren des Filters.</span><span class="sxs-lookup"><span data-stu-id="5ff94-318">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="5ff94-319">Die Häufigkeit, die als neutrale ist 22 kHz (22000 Hz).</span><span class="sxs-lookup"><span data-stu-id="5ff94-319">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="5ff94-320">Die Häufigkeit wurde gewählt, da über die nominale maximale Häufigkeit, die das menschliche Ohr, diese vornehmen keine wahrnehmbaren Auswirkungen auf den Sound hören kann.</span><span class="sxs-lookup"><span data-stu-id="5ff94-320">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="5ff94-321">In der **Hierarchie** wählen **SpatialMapping**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-321">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="5ff94-322">In der **Inspektor** auf **Add Component** und fügen **Audio Occluder**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-322">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="5ff94-323">In **Audio Occluder**legen **Grenzwert Häufigkeit** zu **750**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-323">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="5ff94-324">Wenn mehrere Occluders sind, auf dem Pfad zwischen Benutzer und dem **AudioEmitter**, die niedrigste Häufigkeit wird angewendet, um den Filter.</span><span class="sxs-lookup"><span data-stu-id="5ff94-324">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="5ff94-325">Legen Sie **Pass-Through-Datenträger** zu **0,75**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-325">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="5ff94-326">Wenn mehrere Occluders sind, auf dem Pfad zwischen Benutzer und dem **AudioEmitter**, die Pass-through-Datenträger lichtdurchlässigen angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="5ff94-326">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="5ff94-327">In der **Hierarchie** wählen **Managern**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-327">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="5ff94-328">In der **Inspektor** erweitern **Spracherkennung Eingabe Handler**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-328">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="5ff94-329">In **Spracherkennung Eingabe Handler**, erweitern Sie **wechseln Gebühren**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-329">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="5ff94-330">Änderung **keine Funktion** zu **PolyActions.GoCharge**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-330">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![Keyword: Wechseln Sie kostenlos](images/gocharge.png)

* <span data-ttu-id="5ff94-332">Erweitern Sie **hierher**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-332">Expand **Come Here**.</span></span>
* <span data-ttu-id="5ff94-333">Änderung **keine Funktion** zu **PolyActions.ComeBack**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-333">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![Keyword: Komm her](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="5ff94-335">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="5ff94-335">Build and Deploy</span></span>

* <span data-ttu-id="5ff94-336">Wie zuvor erstellen Sie das Projekt im Unity, und stellen Sie in Visual Studio bereit.</span><span class="sxs-lookup"><span data-stu-id="5ff94-336">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="5ff94-337">Nachdem die Anwendung bereitgestellt wird:</span><span class="sxs-lookup"><span data-stu-id="5ff94-337">After the application is deployed:</span></span>

* <span data-ttu-id="5ff94-338">Sagen Sie *"Wechseln Sie kostenlos"* P0LY Geben Sie den Hub Energie haben.</span><span class="sxs-lookup"><span data-stu-id="5ff94-338">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="5ff94-339">Beachten Sie die Änderung der Sound.</span><span class="sxs-lookup"><span data-stu-id="5ff94-339">Note the change in the sound.</span></span> <span data-ttu-id="5ff94-340">Es sollte dumpfe und ein wenig leiser klingen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-340">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="5ff94-341">Wenn Sie sich mit einer Wand oder ein anderes Objekt zwischen Ihnen und dem Hub Energie positionieren können, sollten Sie feststellen, einen weiteren muffling des Sounds am Einschluss von der realen Welt.</span><span class="sxs-lookup"><span data-stu-id="5ff94-341">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="5ff94-342">Sagen Sie *"Kommen hier"* P0LY, lassen Sie den Hub Energie, und positionieren Sie sich selbst vor Ihnen haben.</span><span class="sxs-lookup"><span data-stu-id="5ff94-342">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="5ff94-343">Beachten Sie, dass der sound verdecken entfernt wird, sobald P0LY Energie Hub beendet wird.</span><span class="sxs-lookup"><span data-stu-id="5ff94-343">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="5ff94-344">Falls Sie immer noch hören verdecken, können von der realen Welt P0LY okkludierte sein.</span><span class="sxs-lookup"><span data-stu-id="5ff94-344">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="5ff94-345">Versuchen Sie, um sicherzustellen, dass Sie eine klare uneingeschränkten Zugriff auf P0LY zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="5ff94-345">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="5ff94-346">Teil 3 – Platz Modelle</span><span class="sxs-lookup"><span data-stu-id="5ff94-346">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="5ff94-347">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="5ff94-347">Key Concepts</span></span>

* <span data-ttu-id="5ff94-348">Die Größe des Speicherplatzes bietet subliminalen Warteschlangen, die zur Lokalisierung der sound beitragen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-348">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="5ff94-349">Raum Modelle werden pro festgelegt-**AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-349">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="5ff94-350">Die [MixedRealityToolkit für Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) enthält Code zum Festlegen des Modells Platz.</span><span class="sxs-lookup"><span data-stu-id="5ff94-350">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="5ff94-351">Wählen Sie für Mixed Reality-Umgebungen das Platz-Modell, das den realen Welt Speicherplatz am besten geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="5ff94-351">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="5ff94-352">Wenn Sie ein Virtual Reality-Szenario erstellen, wählen Sie das Platz-Modell, das die virtuelle Umgebung am besten geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="5ff94-352">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="5ff94-353">Kapitel 4 – Entwurf</span><span class="sxs-lookup"><span data-stu-id="5ff94-353">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="5ff94-354">Ziele</span><span class="sxs-lookup"><span data-stu-id="5ff94-354">Objectives</span></span>

* <span data-ttu-id="5ff94-355">Erfahren Sie, Überlegungen zum effektiven Entwurf.</span><span class="sxs-lookup"><span data-stu-id="5ff94-355">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="5ff94-356">Erfahren Sie, Mischen von Methoden und Richtlinien.</span><span class="sxs-lookup"><span data-stu-id="5ff94-356">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="5ff94-357">Teil 1 – Sound- und Entwurf der Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="5ff94-357">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="5ff94-358">Dieser Abschnitt beschreibt die wichtigsten Sound und Überlegungen zum Entwurf der Benutzeroberfläche und Richtlinien.</span><span class="sxs-lookup"><span data-stu-id="5ff94-358">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="5ff94-359">Normalisieren Sie alle sounds</span><span class="sxs-lookup"><span data-stu-id="5ff94-359">Normalize all sounds</span></span>

<span data-ttu-id="5ff94-360">Dadurch muss die Groß-/Kleinschreibung spezialcode Lautstärkestufen pro Sound, Anpassen der zeitaufwändig sein kann, und beschränkt die Fähigkeit, um Audiodateien problemlos zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="5ff94-360">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="5ff94-361">Entwurf für eine unabhängig</span><span class="sxs-lookup"><span data-stu-id="5ff94-361">Design for an untethered experience</span></span>

<span data-ttu-id="5ff94-362">HoloLens handelt es sich um eine vollständig enthaltene, unabhängig holographic-Computer.</span><span class="sxs-lookup"><span data-stu-id="5ff94-362">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="5ff94-363">Ihre Benutzer können und Ihre Erfahrungen beim Verschieben von verwenden.</span><span class="sxs-lookup"><span data-stu-id="5ff94-363">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="5ff94-364">Achten Sie darauf, dass die audio Mischung zu testen, indem Sie zu durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-364">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="5ff94-365">Ausgeben von Sounds über logischen Laufwerke auf Ihrem Hologramme</span><span class="sxs-lookup"><span data-stu-id="5ff94-365">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="5ff94-366">In der realen Welt Hundes nicht über die Tail Hundegebellsound, und einem Benutzer, der die Sprache nicht aus seiner Fuß stammt.</span><span class="sxs-lookup"><span data-stu-id="5ff94-366">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="5ff94-367">Vermeiden Sie, die Ihre Sounds aus unerwarteten Teile Ihrer Hologramme ausgeben.</span><span class="sxs-lookup"><span data-stu-id="5ff94-367">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="5ff94-368">Kleine Hologramme ist es sinnvoll, die aus der Mitte der Geometrie ausgeben klingen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-368">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="5ff94-369">Vertraut klingt sind die meisten lokalisierbar</span><span class="sxs-lookup"><span data-stu-id="5ff94-369">Familiar sounds are most localizable</span></span>

<span data-ttu-id="5ff94-370">Die menschliche Stimme und Musik sind sehr einfach zu lokalisieren.</span><span class="sxs-lookup"><span data-stu-id="5ff94-370">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="5ff94-371">Wenn ein Benutzer den Namen Ihres aufgerufen wird, können Sie sehr genau bestimmen, in welche Richtung die Stimme stammen und wie weit entfernt.</span><span class="sxs-lookup"><span data-stu-id="5ff94-371">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="5ff94-372">Sounds für kurzen, nicht vertraut sind schwerer zu lokalisieren.</span><span class="sxs-lookup"><span data-stu-id="5ff94-372">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="5ff94-373">Werden Sie die Erwartungen der Benutzer kennen sollten</span><span class="sxs-lookup"><span data-stu-id="5ff94-373">Be cognizant of user expectations</span></span>

<span data-ttu-id="5ff94-374">Leben Erfahrung spielt eine Rolle in unserer Fähigkeit zur Identifizierung des Speicherorts eines Sounds.</span><span class="sxs-lookup"><span data-stu-id="5ff94-374">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="5ff94-375">Dies ist ein Grund, warum die menschliche Stimme besonders einfach zu lokalisieren ist.</span><span class="sxs-lookup"><span data-stu-id="5ff94-375">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="5ff94-376">Es ist wichtig zu beachten gelernten Erwartungen des Benutzers bei der Platzierung Ihrer Sounds.</span><span class="sxs-lookup"><span data-stu-id="5ff94-376">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="5ff94-377">Z. B. wenn ein Benutzer eine Bird "Song" hört suchen sie in der Regel, wie Vögel tendenziell über den uneingeschränkten Zugriff (fliegenden oder in einer Struktur).</span><span class="sxs-lookup"><span data-stu-id="5ff94-377">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="5ff94-378">Es ist nicht ungewöhnlich, dass ein Benutzer in der richtigen Richtung eines Sounds, aber in vertikaler Richtung falsche suchen und verwechseln oder frustriert sind, wenn sie nicht die Hologramm gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="5ff94-378">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="5ff94-379">Vermeiden Sie ausgeblendete korrekturemitter ab</span><span class="sxs-lookup"><span data-stu-id="5ff94-379">Avoid hidden emitters</span></span>

<span data-ttu-id="5ff94-380">In der Praxis Wenn wir hören, dass eine solide, können wir in der Regel das Objekt identifizieren, das den Klang ausgibt.</span><span class="sxs-lookup"><span data-stu-id="5ff94-380">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="5ff94-381">Dies sollte auch in Ihre Erfahrungen mit "true" enthalten.</span><span class="sxs-lookup"><span data-stu-id="5ff94-381">This should also hold true in your experiences.</span></span> <span data-ttu-id="5ff94-382">Sie können für Benutzer, einen Sound hören, wissen Sie in den Ursprung des Klang sehr verwirrend sein und nicht auf ein Objekt finden Sie unter.</span><span class="sxs-lookup"><span data-stu-id="5ff94-382">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="5ff94-383">Es gibt einige Ausnahmen von dieser Richtlinie.</span><span class="sxs-lookup"><span data-stu-id="5ff94-383">There are some exceptions to this guideline.</span></span> <span data-ttu-id="5ff94-384">Beispielsweise müssen Ambiente Audiokomponenten wie Crickets in einem Feld nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5ff94-384">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="5ff94-385">Life-Erfahrung bietet uns die Vertrautheit mit der Quelle dieser Sounds, ohne dass es finden Sie unter.</span><span class="sxs-lookup"><span data-stu-id="5ff94-385">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="5ff94-386">Teil 2 – Sound mischen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-386">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="5ff94-387">Die Mischung für die HoloLens 70 % Volume als Ziel</span><span class="sxs-lookup"><span data-stu-id="5ff94-387">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="5ff94-388">Mixed Reality-Erfahrungen ermöglichen Hologramme, die in der realen Welt angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5ff94-388">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="5ff94-389">Sie sollten auch reale Welt Sounds zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-389">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="5ff94-390">Ein Ziel 70 % Volume kann der Benutzer die Welt um diese zusammen mit Ihren Erfahrungen zu hören.</span><span class="sxs-lookup"><span data-stu-id="5ff94-390">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="5ff94-391">HoloLens unter 100 % Volume sollte herausfiltert externe ertrinken.</span><span class="sxs-lookup"><span data-stu-id="5ff94-391">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="5ff94-392">Eine Volume-Ebene von 100 % entspricht in etwa eine Virtual Reality-Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="5ff94-392">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="5ff94-393">Visuell wird der Benutzer zu einem anderen System übertragen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-393">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="5ff94-394">Die gleiche muss "true" akustisch enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="5ff94-394">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="5ff94-395">Verwenden Sie die Unity-AudioMixer Kategorien von Sounds anpassen</span><span class="sxs-lookup"><span data-stu-id="5ff94-395">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="5ff94-396">Beim Entwerfen Ihrer testmischung ist es oft hilfreich, sound Kategorien erstellen und haben die Möglichkeit, erhöhen oder Verringern ihres Umfangs als eine Einheit.</span><span class="sxs-lookup"><span data-stu-id="5ff94-396">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="5ff94-397">Dies behält die relativen Leistungsstufen für jeden Sound gleichzeitig schnelle und einfache Änderungen an der Kombination aus.</span><span class="sxs-lookup"><span data-stu-id="5ff94-397">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="5ff94-398">Allgemeine Kategorien sind: Soundeffekte, Umgebung, Voice-Failover und Hintergrundmusik.</span><span class="sxs-lookup"><span data-stu-id="5ff94-398">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="5ff94-399">Kombinieren Sie anhand des Benutzers Blicke sounds</span><span class="sxs-lookup"><span data-stu-id="5ff94-399">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="5ff94-400">Es kann häufig hilfreich sein, ändern Sie den sound Mischung in Ihre Umgebung basierend auf den Speicherort ein Benutzers ist (oder nicht) suchen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-400">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="5ff94-401">Ein gängiges Szenario für dieses Verfahren werden die Volumeebene für Hologramme zu reduzieren, die außerhalb von den Holographic Frame für den Benutzer zu konzentrieren, die Informationen direkt vor ihnen erleichtern.</span><span class="sxs-lookup"><span data-stu-id="5ff94-401">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="5ff94-402">Eine weitere Verwendungsmöglichkeit ist zum Erhöhen der Lautstärke eines Sounds aus, um die Aufmerksamkeit des Benutzers auf ein wichtiges Ereignis zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-402">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="5ff94-403">Erstellen die Mischung</span><span class="sxs-lookup"><span data-stu-id="5ff94-403">Building your mix</span></span>

<span data-ttu-id="5ff94-404">Wenn Sie die Mischung erstellen zu können, empfiehlt es sich mit hintergrundaudiofunktion für Ihre Umgebung die beginnen, und basierte auf Wichtigkeit Ebenen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-404">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="5ff94-405">Oft führt dies in jeder Schicht wird als die vorherige lauter.</span><span class="sxs-lookup"><span data-stu-id="5ff94-405">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="5ff94-406">Die Mischung vorstellen, als eine invertierte Trichter, mit dem am wenigsten wichtige (und in der Regel leisesten Sounds) im unteren Bereich wird empfohlen, die ähnlich wie im folgenden Diagramm Mischung Struktur.</span><span class="sxs-lookup"><span data-stu-id="5ff94-406">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![Sound Mix-Struktur](images/soundlevels.png)

<span data-ttu-id="5ff94-408">Voice-Failover sind ein interessantes Szenario.</span><span class="sxs-lookup"><span data-stu-id="5ff94-408">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="5ff94-409">Basierend auf der Erfahrung, die Sie erstellen Sie nach Wunsch eine (nicht lokalisierte) Stereosound oder Ihre Stimme Failover spatialize.</span><span class="sxs-lookup"><span data-stu-id="5ff94-409">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="5ff94-410">Zwei Microsoft veröffentlichte Erfahrungen hervorragende Beispiele für jedes Szenario zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-410">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="5ff94-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) Sprachnotizen Stereo verwendet.</span><span class="sxs-lookup"><span data-stu-id="5ff94-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="5ff94-412">Wenn die Sprachausgabe den Speicherort, der angezeigt wird, beschreibt, wird der Sound sind konsistent und ist nicht variieren je nach Position des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="5ff94-412">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="5ff94-413">Dies ermöglicht die Sprachausgabe um der Szene ohne Durchführung von die spatialized Sounds aus der Umgebung zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="5ff94-413">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="5ff94-414">[Fragmente](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) nutzt eine spatialized Stimme über in Form einer Detective.</span><span class="sxs-lookup"><span data-stu-id="5ff94-414">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="5ff94-415">Des Detektivs Stimme wird verwendet, zu bringen die Aufmerksamkeit des Benutzers, ein wichtiger Hinweis darauf, wie bei einer tatsächlichen Menschen im Raum.</span><span class="sxs-lookup"><span data-stu-id="5ff94-415">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="5ff94-416">Dies ermöglicht eine noch größere Eindruck davon zu Entwicklungsthemen in die Oberfläche der Rätsel lösen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-416">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="5ff94-417">Teil 3: Leistung</span><span class="sxs-lookup"><span data-stu-id="5ff94-417">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="5ff94-418">CPU-Auslastung</span><span class="sxs-lookup"><span data-stu-id="5ff94-418">CPU usage</span></span>

<span data-ttu-id="5ff94-419">Wenn räumliche Sound verwenden, werden 10.-12. korrekturemitter ungefähr 12 % der CPU verbraucht.</span><span class="sxs-lookup"><span data-stu-id="5ff94-419">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="5ff94-420">Lange Audiodateien Stream</span><span class="sxs-lookup"><span data-stu-id="5ff94-420">Stream long audio files</span></span>

<span data-ttu-id="5ff94-421">Audiodaten können vor allem bei allgemeinen Samplingraten (48, und 44,1 kHz) groß sein.</span><span class="sxs-lookup"><span data-stu-id="5ff94-421">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="5ff94-422">Eine allgemeine Regel gilt, Audiodateien, die länger als 5 bis 10 Sekunden gestreamt werden sollen, um die speicherauslastung der Anwendung zu reduzieren.</span><span class="sxs-lookup"><span data-stu-id="5ff94-422">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="5ff94-423">In Unity können Sie eine Audiodatei für das streaming in der Datei importeinstellungen markieren.</span><span class="sxs-lookup"><span data-stu-id="5ff94-423">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![Audio Importieren von Einstellungen](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="5ff94-425">Kapitel 5 – Spezialeffekte zu erzeugen</span><span class="sxs-lookup"><span data-stu-id="5ff94-425">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="5ff94-426">Ziele</span><span class="sxs-lookup"><span data-stu-id="5ff94-426">Objectives</span></span>

* <span data-ttu-id="5ff94-427">Tiefe "Magic-Windows" hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-427">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="5ff94-428">Bringen Sie den Benutzer in der virtuellen Welt ein.</span><span class="sxs-lookup"><span data-stu-id="5ff94-428">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="5ff94-429">Magic Windows</span><span class="sxs-lookup"><span data-stu-id="5ff94-429">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="5ff94-430">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="5ff94-430">Key Concepts</span></span>

* <span data-ttu-id="5ff94-431">Erstellen von Ansichten in einer ausgeblendeten Welt, ist eine visuell ansprechende.</span><span class="sxs-lookup"><span data-stu-id="5ff94-431">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="5ff94-432">Verbessern Sie realer zu gestalten, indem Sie das Hinzufügen von Audioeffekten Wenn ggf. ein Hologramm oder der Benutzer in der Nähe der ausgeblendeten Welt ist.</span><span class="sxs-lookup"><span data-stu-id="5ff94-432">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="5ff94-433">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="5ff94-433">Instructions</span></span>

* <span data-ttu-id="5ff94-434">In der **Hierarchie** erweitern **HologramCollection** , und wählen Sie **Underworld**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-434">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="5ff94-435">Erweitern Sie **Underworld** , und wählen Sie **VoiceSource**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-435">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="5ff94-436">In der **Inspektor** auf **Add Component** und fügen **User Voice-Effekt**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-436">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="5ff94-437">Ein **AudioSource** Komponente hinzugefügt **VoiceSource**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-437">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="5ff94-438">In **AudioSource**legen **Ausgabe** zu **UserVoice (Mixer)**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-438">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="5ff94-439">Überprüfen Sie die **Spatialize** Kontrollkästchen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-439">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="5ff94-440">Ziehen Sie die **räumliche Blend** Schieberegler ganz nach **3D**, oder geben Sie **1** in das Bearbeitungsfeld.</span><span class="sxs-lookup"><span data-stu-id="5ff94-440">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="5ff94-441">Erweitern Sie **3D Sound Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-441">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="5ff94-442">Legen Sie **Doppler-Ebene** zu **0**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-442">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="5ff94-443">In **User Voice-Effekt**legen **übergeordnetes Objekt** auf die **Underworld** aus der Szene.</span><span class="sxs-lookup"><span data-stu-id="5ff94-443">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="5ff94-444">Legen Sie **maximaler Abstand** zu **1**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-444">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="5ff94-445">Festlegen von **maximaler Abstand** weist **User Voice-Effekt** wie nahe der Benutzer auf das übergeordnete Objekt sein muss, bevor der Effekt aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="5ff94-445">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="5ff94-446">In **User Voice-Effekt**, erweitern Sie **heißen Talbot Parameter**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-446">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="5ff94-447">Legen Sie **Tiefe** zu **0,1**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-447">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="5ff94-448">Legen Sie **Tippen Sie auf 1 Volume**, **Tippen Sie auf 2 Volume** und **Tippen Sie auf 3 Volume** zu **0,8**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-448">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="5ff94-449">Legen Sie **ursprünglichen Sound Volume** zu **0,5**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-449">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="5ff94-450">Die vorherigen Einstellungen konfigurieren Sie die Parameter von Unity **AudioChorusFilter** verwendet, um Sie Umfang des Benutzers Stimme hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-450">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="5ff94-451">In **User Voice-Effekt**, erweitern Sie **Echo Parameter**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-451">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="5ff94-452">Legen Sie **Verzögerung** zu **300**</span><span class="sxs-lookup"><span data-stu-id="5ff94-452">Set **Delay** to **300**</span></span>
* <span data-ttu-id="5ff94-453">Legen Sie **Decay-Verhältnis** zu **0,2**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-453">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="5ff94-454">Legen Sie **ursprünglichen Sound Volume** zu **0**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-454">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="5ff94-455">Die vorherigen Einstellungen konfigurieren Sie die Parameter von Unity **AudioEchoFilter** verwendet, damit das Benutzerfeedback, das zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="5ff94-455">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="5ff94-456">Das Skript User Voice-Effekt ist verantwortlich für:</span><span class="sxs-lookup"><span data-stu-id="5ff94-456">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="5ff94-457">Den Abstand zwischen dem Benutzer zu messen und die **"gameobject"** , dem das Skript zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="5ff94-457">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="5ff94-458">Bestimmen, und zwar unabhängig davon, ob der Benutzer zeigt die **"gameobject"**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-458">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="5ff94-459">Der Benutzer muss das "gameobject", unabhängig vom Abstand für den Effekt zu aktivierenden verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="5ff94-459">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="5ff94-460">Anwenden und konfigurieren eine **AudioChorusFilter** und ein **AudioEchoFilter** auf die **AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-460">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="5ff94-461">Deaktivieren den Effekt, indem Sie die Filter deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="5ff94-461">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="5ff94-462">User Voice-Effekt verwendet die Mic-Stream-Selektor-Komponente, aus der [MixedRealityToolkit für Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), um die qualitativ hochwertige Sprachstream wählen aus, und sie in Unity-audio-System weiterzuleiten.</span><span class="sxs-lookup"><span data-stu-id="5ff94-462">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="5ff94-463">In der **Hierarchie** wählen **Managern**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-463">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="5ff94-464">In der **Inspektor** erweitern **Spracherkennung Eingabe Handler**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-464">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="5ff94-465">In **Spracherkennung Eingabe Handler**, erweitern Sie **anzeigen Underworld**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-465">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="5ff94-466">Änderung **keine Funktion** zu **UnderworldBase.OnEnable**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-466">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![Keyword: Underworld anzeigen](images/showunderworld.png)

* <span data-ttu-id="5ff94-468">Erweitern Sie **ausblenden Underworld**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-468">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="5ff94-469">Änderung **keine Funktion** zu **UnderworldBase.OnDisable**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-469">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![Keyword: Hide Underworld](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="5ff94-471">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="5ff94-471">Build and Deploy</span></span>

* <span data-ttu-id="5ff94-472">Wie zuvor erstellen Sie das Projekt im Unity, und stellen Sie in Visual Studio bereit.</span><span class="sxs-lookup"><span data-stu-id="5ff94-472">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="5ff94-473">Nachdem die Anwendung bereitgestellt wird:</span><span class="sxs-lookup"><span data-stu-id="5ff94-473">After the application is deployed:</span></span>

* <span data-ttu-id="5ff94-474">Sehen Sie eine Fläche (Wand, Floor, Tabelle) und sagen *"Underworld anzeigen"*.</span><span class="sxs-lookup"><span data-stu-id="5ff94-474">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="5ff94-475">Die Underworld wird angezeigt, und alle anderen Hologramme ausgeblendet werden.</span><span class="sxs-lookup"><span data-stu-id="5ff94-475">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="5ff94-476">Die Underworld nicht angezeigt wird, sicher, dass eine reale Oberfläche aufgetretenen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-476">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="5ff94-477">Innerhalb von 1 Meter Umkreis um die Underworld – Hologramm Ansatz, und sprechen.</span><span class="sxs-lookup"><span data-stu-id="5ff94-477">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="5ff94-478">Es gibt jetzt Audioeffekte angewendet werden, um Ihre Stimme!</span><span class="sxs-lookup"><span data-stu-id="5ff94-478">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="5ff94-479">Aktivieren Sie die Underworld, und beachten Sie, wie der Effekt nicht mehr angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="5ff94-479">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="5ff94-480">Sagen Sie *"Underworld ausblenden"* der Underworld ausblenden.</span><span class="sxs-lookup"><span data-stu-id="5ff94-480">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="5ff94-481">Die Underworld werden ausgeblendet, und die zuvor nicht Hologramme werden erneut angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5ff94-481">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="5ff94-482">Das Ende</span><span class="sxs-lookup"><span data-stu-id="5ff94-482">The End</span></span>

<span data-ttu-id="5ff94-483">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="5ff94-483">Congratulations!</span></span> <span data-ttu-id="5ff94-484">Sie haben jetzt **MR räumliche 220: Räumliche Sound**.</span><span class="sxs-lookup"><span data-stu-id="5ff94-484">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="5ff94-485">Lauschen auf der ganzen Welt, und setzen Sie Ihre Erfahrungen mit Sound!</span><span class="sxs-lookup"><span data-stu-id="5ff94-485">Listen to the world and bring your experiences to life with sound!</span></span>
