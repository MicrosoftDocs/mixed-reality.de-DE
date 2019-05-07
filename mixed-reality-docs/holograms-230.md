---
title: MR räumlich 230 - räumliche Zuordnung
description: Führen Sie diese exemplarische Vorgehensweise verwenden die Details der räumlichen Mapping-Konzepten finden Sie Unity, Visual Studio und HoloLens codieren.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Holotoolkit, Mixedrealitytoolkit, Mixedrealitytoolkit-Unity, Academy, Tutorial, räumliche Zuordnung, Surface Wiederaufbau, Netz
ms.openlocfilehash: ed58676a0fda660cc6b4c197239aeb53166baa4d
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993563"
---
>[!NOTE]
><span data-ttu-id="49914-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="49914-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="49914-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="49914-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="49914-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="49914-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="49914-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="49914-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="49914-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="49914-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="49914-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="49914-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-230-spatial-mapping"></a><span data-ttu-id="49914-110">MR Spatial 230: Räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="49914-110">MR Spatial 230: Spatial mapping</span></span>

<span data-ttu-id="49914-111">[Räumliche Zuordnung](spatial-mapping.md) kombiniert die reale Welt und die virtuelle Welt von unterrichten Hologramme über die Umgebung.</span><span class="sxs-lookup"><span data-stu-id="49914-111">[Spatial mapping](spatial-mapping.md) combines the real world and virtual world together by teaching holograms about the environment.</span></span> <span data-ttu-id="49914-112">In räumlichen MR-230 (Projekt Planetarium) erfahren wir Gewusst wie:</span><span class="sxs-lookup"><span data-stu-id="49914-112">In MR Spatial 230 (Project Planetarium) we'll learn how to:</span></span>

* <span data-ttu-id="49914-113">Überprüfen Sie die Umgebung und Daten aus der HoloLens auf Ihren Entwicklungscomputer.</span><span class="sxs-lookup"><span data-stu-id="49914-113">Scan the environment and transfer data from the HoloLens to your development machine.</span></span>
* <span data-ttu-id="49914-114">Erkunden Sie Shader, und erfahren Sie, wie zum Visualisieren der Speicherplatz zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="49914-114">Explore shaders and learn how to use them for visualizing your space.</span></span>
* <span data-ttu-id="49914-115">Unterteilen Sie das Netz Platz in einfachen Ebenen mithilfe von Mesh-Verarbeitung aus.</span><span class="sxs-lookup"><span data-stu-id="49914-115">Break down the room mesh into simple planes using mesh processing.</span></span>
* <span data-ttu-id="49914-116">Wechseln Sie über die Platzierung-Techniken, die wir gelernt [MR Grundlagen 101](holograms-101.md), und geben Sie Feedback zur, in denen ggf. ein Hologramm, in der Umgebung platziert werden kann.</span><span class="sxs-lookup"><span data-stu-id="49914-116">Go beyond the placement techniques we learned in [MR Basics 101](holograms-101.md), and provide feedback about where a hologram can be placed in the environment.</span></span>
* <span data-ttu-id="49914-117">Untersuchen Sie verdecken Effekte, also wenn Ihre – Hologramm hinter einem echten Objekt ist, Sie immer noch mit x-Ray-Vision sehen!</span><span class="sxs-lookup"><span data-stu-id="49914-117">Explore occlusion effects, so when your hologram is behind a real-world object, you can still see it with x-ray vision!</span></span>

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a><span data-ttu-id="49914-118">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="49914-118">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="49914-119">Kurs</span><span class="sxs-lookup"><span data-stu-id="49914-119">Course</span></span></th><th style="width:150px"> <span data-ttu-id="49914-120"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="49914-120"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="49914-121"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="49914-121"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="49914-122">MR Spatial 230: Räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="49914-122">MR Spatial 230: Spatial mapping</span></span></td><td style="text-align: center;"> <span data-ttu-id="49914-123">✔️</span><span class="sxs-lookup"><span data-stu-id="49914-123">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="49914-124">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="49914-124">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="49914-125">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="49914-125">Prerequisites</span></span>

* <span data-ttu-id="49914-126">Ein Windows 10-PCs mit dem richtigen konfiguriert [-Tools installiert](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="49914-126">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="49914-127">Einige grundlegende C# Programmierkenntnisse.</span><span class="sxs-lookup"><span data-stu-id="49914-127">Some basic C# programming ability.</span></span>
* <span data-ttu-id="49914-128">Sie sollten abgeschlossen haben [MR Grundlagen 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="49914-128">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="49914-129">Ein Gerät HoloLens [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="49914-129">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="49914-130">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="49914-130">Project files</span></span>

* <span data-ttu-id="49914-131">Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) vom Projekt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="49914-131">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) required by the project.</span></span><span data-ttu-id="49914-132"> Ist Unity 2017.2 oder höher erforderlich.</span><span class="sxs-lookup"><span data-stu-id="49914-132"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="49914-133">Wenn Sie weitere Unity 5.6-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span><span class="sxs-lookup"><span data-stu-id="49914-133">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span></span>
  * <span data-ttu-id="49914-134">Wenn Sie weitere Unity 5.5-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span><span class="sxs-lookup"><span data-stu-id="49914-134">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span></span>
  * <span data-ttu-id="49914-135">Wenn Sie weitere 5.4 von Unity-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span><span class="sxs-lookup"><span data-stu-id="49914-135">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span></span>
* <span data-ttu-id="49914-136">Un-Archive die Dateien auf dem Desktop oder andere einfach auf den Speicherort zugreifen.</span><span class="sxs-lookup"><span data-stu-id="49914-136">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="49914-137">Wenn Sie vor dem Herunterladen, den Quellcode ansehen möchten es [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span><span class="sxs-lookup"><span data-stu-id="49914-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span></span>

### <a name="notes"></a><span data-ttu-id="49914-138">Hinweise</span><span class="sxs-lookup"><span data-stu-id="49914-138">Notes</span></span>

* <span data-ttu-id="49914-139">"Nur eigenen Code aktivieren" in Visual Studio muss deaktiviert werden soll (*deaktiviert*) unter Extras > Optionen > Debugging, um die Haltepunkte in Ihrem Code.</span><span class="sxs-lookup"><span data-stu-id="49914-139">"Enable Just My Code" in Visual Studio needs to be disabled (*unchecked*) under Tools > Options > Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="49914-140">Unity-setup</span><span class="sxs-lookup"><span data-stu-id="49914-140">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* <span data-ttu-id="49914-141">Starten Sie **Unity**.</span><span class="sxs-lookup"><span data-stu-id="49914-141">Start **Unity**.</span></span>
* <span data-ttu-id="49914-142">Wählen Sie **neu** zum Erstellen eines neuen Projekts.</span><span class="sxs-lookup"><span data-stu-id="49914-142">Select **New** to create a new project.</span></span>
* <span data-ttu-id="49914-143">Nennen Sie das Projekt **Planetarium**.</span><span class="sxs-lookup"><span data-stu-id="49914-143">Name the project **Planetarium**.</span></span>
* <span data-ttu-id="49914-144">Überprüfen Sie, ob die **3D** Einstellung ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="49914-144">Verify that the **3D** setting is selected.</span></span>
* <span data-ttu-id="49914-145">Klicken Sie auf **erstellen Projekt**.</span><span class="sxs-lookup"><span data-stu-id="49914-145">Click **Create Project**.</span></span>
* <span data-ttu-id="49914-146">Nachdem Unity gestartet wird, wechseln Sie zur **Bearbeiten > Projekteinstellungen > Player**.</span><span class="sxs-lookup"><span data-stu-id="49914-146">Once Unity launches, go to **Edit > Project Settings > Player**.</span></span>
* <span data-ttu-id="49914-147">In der **Inspektor** Bereich, suchen und wählen Sie das grüne **Windows Store** Symbol.</span><span class="sxs-lookup"><span data-stu-id="49914-147">In the **Inspector** panel, find and select the green **Windows Store** icon.</span></span>
* <span data-ttu-id="49914-148">Erweitern Sie **andere Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="49914-148">Expand **Other Settings**.</span></span>
* <span data-ttu-id="49914-149">In der **Rendern** aktivieren Sie im Abschnitt der **virtuelle Realität unterstützt** Option.</span><span class="sxs-lookup"><span data-stu-id="49914-149">In the **Rendering** section, check the **Virtual Reality Supported** option.</span></span>
* <span data-ttu-id="49914-150">Überprüfen Sie, ob **Windows Holographic** angezeigt wird, in der Liste der **virtuelle Realität SDKs**.</span><span class="sxs-lookup"><span data-stu-id="49914-150">Verify that **Windows Holographic** appears in the list of **Virtual Reality SDKs**.</span></span> <span data-ttu-id="49914-151">Wenn nicht der Fall, wählen Sie die **+** Schaltfläche am unteren Rand der Liste aus, und wählen Sie **Windows Holographic**.</span><span class="sxs-lookup"><span data-stu-id="49914-151">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>
* <span data-ttu-id="49914-152">Erweitern Sie **Einstellungen veröffentlichen**.</span><span class="sxs-lookup"><span data-stu-id="49914-152">Expand **Publishing Settings**.</span></span>
* <span data-ttu-id="49914-153">In der **Funktionen** Abschnitt, überprüfen Sie die folgenden Einstellungen:</span><span class="sxs-lookup"><span data-stu-id="49914-153">In the **Capabilities** section, check the following settings:</span></span>
    * <span data-ttu-id="49914-154">InternetClientServer</span><span class="sxs-lookup"><span data-stu-id="49914-154">InternetClientServer</span></span>
    * <span data-ttu-id="49914-155">PrivateNetworkClientServer</span><span class="sxs-lookup"><span data-stu-id="49914-155">PrivateNetworkClientServer</span></span>
    * <span data-ttu-id="49914-156">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="49914-156">Microphone</span></span>
    * <span data-ttu-id="49914-157">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="49914-157">SpatialPerception</span></span>
* <span data-ttu-id="49914-158">Wechseln Sie zu **Bearbeiten > Projekteinstellungen > Qualität**</span><span class="sxs-lookup"><span data-stu-id="49914-158">Go to **Edit > Project Settings > Quality**</span></span>
* <span data-ttu-id="49914-159">In der **Inspektor** Bereich unter dem Windows Store-Symbol, wählen den schwarzen Pfeil der Dropdownliste unter der Zeile mit "Default", und ändern Sie die Standardeinstellung **sehr niedrig**.</span><span class="sxs-lookup"><span data-stu-id="49914-159">In the **Inspector** panel, under the Windows Store icon, select the black drop-down arrow under the 'Default' row and change the default setting to **Very Low**.</span></span>
* <span data-ttu-id="49914-160">Wechseln Sie zu **Assets > Paket importieren > benutzerdefiniertes Paket**.</span><span class="sxs-lookup"><span data-stu-id="49914-160">Go to **Assets > Import Package > Custom Package**.</span></span>
* <span data-ttu-id="49914-161">Navigieren Sie zu der **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** Ordner.</span><span class="sxs-lookup"><span data-stu-id="49914-161">Navigate to the **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** folder.</span></span>
* <span data-ttu-id="49914-162">Klicken Sie auf **Planetarium.unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="49914-162">Click on **Planetarium.unitypackage**.</span></span>
* <span data-ttu-id="49914-163">Klicken Sie auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="49914-163">Click **Open**.</span></span>
* <span data-ttu-id="49914-164">Ein **Unity-Paket importieren** Fenster sollte angezeigt werden, klicken Sie auf die **Import** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="49914-164">An **Import Unity Package** window should appear, click on the **Import** button.</span></span>
* <span data-ttu-id="49914-165">Warten Sie Unity aus, um alle Ressourcen zu importieren, die wir benötigen, um dieses Projekt abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="49914-165">Wait for Unity to import all of the assets that we will need to complete this project.</span></span>
* <span data-ttu-id="49914-166">In der **Hierarchie** panel, löschen Sie die **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="49914-166">In the **Hierarchy** panel, delete the **Main Camera**.</span></span>
* <span data-ttu-id="49914-167">In der **Projekt** Bereich **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** Ordner finden Sie die **Main Camera** Objekt.</span><span class="sxs-lookup"><span data-stu-id="49914-167">In the **Project** panel, **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** folder, find the **Main Camera** object.</span></span>
* <span data-ttu-id="49914-168">Drag & drop die **Main Camera** prefab in die **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="49914-168">Drag and drop the **Main Camera** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="49914-169">In der **Hierarchie** panel, löschen Sie die **gerichtetes Licht** Objekt.</span><span class="sxs-lookup"><span data-stu-id="49914-169">In the **Hierarchy** panel, delete the **Directional Light** object.</span></span>
* <span data-ttu-id="49914-170">In der **Projekt** Bereich **Hologramme** Ordner, suchen Sie die **Cursor** Objekt.</span><span class="sxs-lookup"><span data-stu-id="49914-170">In the **Project** panel, **Holograms** folder, locate the **Cursor** object.</span></span>
* <span data-ttu-id="49914-171">Drag & drop die **Cursor** prefab in die **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="49914-171">Drag & drop the **Cursor** prefab into the **Hierarchy**.</span></span>
* <span data-ttu-id="49914-172">In der **Hierarchie** wählen die **Cursor** Objekt.</span><span class="sxs-lookup"><span data-stu-id="49914-172">In the **Hierarchy** panel, select the **Cursor** object.</span></span>
* <span data-ttu-id="49914-173">In der **Inspektor** Bereich, klicken Sie auf die **Ebene** Dropdownliste aus, und wählen **Ebenen bearbeiten...** .</span><span class="sxs-lookup"><span data-stu-id="49914-173">In the **Inspector** panel, click the **Layer** drop-down and select **Edit Layers...**.</span></span>
* <span data-ttu-id="49914-174">Namen **Benutzerebene 31** als "**SpatialMapping**".</span><span class="sxs-lookup"><span data-stu-id="49914-174">Name **User Layer 31** as "**SpatialMapping**".</span></span>
* <span data-ttu-id="49914-175">Speichern Sie die neue Szene: **Datei > Szene speichern unter...**</span><span class="sxs-lookup"><span data-stu-id="49914-175">Save the new scene: **File > Save Scene As...**</span></span>
* <span data-ttu-id="49914-176">Klicken Sie auf **neuer Ordner** und nennen Sie den Ordner **Szenen**.</span><span class="sxs-lookup"><span data-stu-id="49914-176">Click **New Folder** and name the folder **Scenes**.</span></span>
* <span data-ttu-id="49914-177">Nennen Sie die Datei "**Planetarium**", und speichern Sie ihn in das **Szenen** Ordner.</span><span class="sxs-lookup"><span data-stu-id="49914-177">Name the file "**Planetarium**" and save it in the **Scenes** folder.</span></span>

## <a name="chapter-1---scanning"></a><span data-ttu-id="49914-178">Kapitel 1: Überprüfen</span><span class="sxs-lookup"><span data-stu-id="49914-178">Chapter 1 - Scanning</span></span>

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

<span data-ttu-id="49914-179">**Ziele**</span><span class="sxs-lookup"><span data-stu-id="49914-179">**Objectives**</span></span>
* <span data-ttu-id="49914-180">Informationen Sie zu den SurfaceObserver und wie die Auswirkungen der Einstellungen in der Benutzeroberfläche und Leistung.</span><span class="sxs-lookup"><span data-stu-id="49914-180">Learn about the SurfaceObserver and how its settings impact experience and performance.</span></span>
* <span data-ttu-id="49914-181">Erstellen Sie ein Zimmer Scannen Erfahrung, um die Gitter des Raums erfassen.</span><span class="sxs-lookup"><span data-stu-id="49914-181">Create a room scanning experience to collect the meshes of your room.</span></span>

<span data-ttu-id="49914-182">**Anweisungen**</span><span class="sxs-lookup"><span data-stu-id="49914-182">**Instructions**</span></span>
* <span data-ttu-id="49914-183">In der **Projekt** Bereich **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** Ordner finden Sie die **SpatialMapping** prefab.</span><span class="sxs-lookup"><span data-stu-id="49914-183">In the **Project** panel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** folder, find the **SpatialMapping** prefab.</span></span>
* <span data-ttu-id="49914-184">Drag & drop die **SpatialMapping** prefab in die **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="49914-184">Drag & drop the **SpatialMapping** prefab into the **Hierarchy** panel.</span></span>

<span data-ttu-id="49914-185">**Erstellen und bereitstellen (Teil 1)**</span><span class="sxs-lookup"><span data-stu-id="49914-185">**Build and Deploy (part 1)**</span></span>
* <span data-ttu-id="49914-186">Wählen Sie in Unity **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="49914-186">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="49914-187">Klicken Sie auf **öffnen Szenen hinzufügen** Hinzufügen der **Planetarium** Szene auf den Build.</span><span class="sxs-lookup"><span data-stu-id="49914-187">Click **Add Open Scenes** to add the **Planetarium** scene to the build.</span></span>
* <span data-ttu-id="49914-188">Wählen Sie **universelle Windows-Plattform** in die **Plattform** aus, und klicken Sie auf **Plattform wechseln**.</span><span class="sxs-lookup"><span data-stu-id="49914-188">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="49914-189">Legen Sie **SDK** zu **universelle 10** und **UWP Buildtyp** zu **D3D**.</span><span class="sxs-lookup"><span data-stu-id="49914-189">Set **SDK** to **Universal 10** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="49914-190">Überprüfen Sie **Unity C# Projekte**.</span><span class="sxs-lookup"><span data-stu-id="49914-190">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="49914-191">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="49914-191">Click **Build**.</span></span>
* <span data-ttu-id="49914-192">Erstellen Sie eine **neuer Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="49914-192">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="49914-193">Mausklick die **App** Ordner.</span><span class="sxs-lookup"><span data-stu-id="49914-193">Single click the **App** folder.</span></span>
* <span data-ttu-id="49914-194">Drücken Sie die **Ordner auswählen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="49914-194">Press the **Select Folder** button.</span></span>
* <span data-ttu-id="49914-195">Unity wird nach Abschluss erstellen, ein Datei-Explorer-Fenster wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="49914-195">When Unity is done building, a File Explorer window will appear.</span></span>
* <span data-ttu-id="49914-196">Doppelklicken Sie auf die **App** Ordner aus, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="49914-196">Double-click on the **App** folder to open it.</span></span>
* <span data-ttu-id="49914-197">Doppelklicken Sie auf **Planetarium.sln** auf das Projekt in Visual Studio geladen werden.</span><span class="sxs-lookup"><span data-stu-id="49914-197">Double-click on **Planetarium.sln** to load the project in Visual Studio.</span></span>
* <span data-ttu-id="49914-198">Verwenden Sie in Visual Studio obere auf der Symbolleiste, um die Konfiguration zu ändern **Version**.</span><span class="sxs-lookup"><span data-stu-id="49914-198">In Visual Studio, use the top toolbar to change the Configuration to **Release**.</span></span>
* <span data-ttu-id="49914-199">Ändern Sie die Plattform **X86**.</span><span class="sxs-lookup"><span data-stu-id="49914-199">Change the Platform to **x86**.</span></span>
* <span data-ttu-id="49914-200">Klicken Sie auf den Dropdown-Pfeil rechts neben "Lokaler Computer", und wählen Sie **Remotecomputer**.</span><span class="sxs-lookup"><span data-stu-id="49914-200">Click on the drop-down arrow to the right of 'Local Machine', and select **Remote Machine**.</span></span>
* <span data-ttu-id="49914-201">Geben Sie [die IP-Adresse Ihres Geräts](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) in die Adresse ein, und Ändern des Authentifizierungsmodus in **universell (unverschlüsseltes Protokoll)**.</span><span class="sxs-lookup"><span data-stu-id="49914-201">Enter [your device's IP address](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) in the Address field and change Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span>
* <span data-ttu-id="49914-202">Klicken Sie auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="49914-202">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="49914-203">Sehen Sie sich die **Ausgabe** panel in Visual Studio für Build und Bereitstellungsstatus.</span><span class="sxs-lookup"><span data-stu-id="49914-203">Watch the **Output** panel in Visual Studio for build and deploy status.</span></span>
* <span data-ttu-id="49914-204">Sobald Ihre app bereitgestellt wurde, führen Sie im Raum.</span><span class="sxs-lookup"><span data-stu-id="49914-204">Once your app has deployed, walk around the room.</span></span> <span data-ttu-id="49914-205">Sie sehen, dass die umgebenden Flächen, die von Schwarz oder weiß Drahtmodell Gitter abgedeckt.</span><span class="sxs-lookup"><span data-stu-id="49914-205">You will see the surrounding surfaces covered by black and white wireframe meshes.</span></span>
* <span data-ttu-id="49914-206">Überprüfen Sie Ihre Umgebung.</span><span class="sxs-lookup"><span data-stu-id="49914-206">Scan your surroundings.</span></span> <span data-ttu-id="49914-207">Achten Sie darauf, Wände, Höchstgrenzen und Stockwerken ansehen.</span><span class="sxs-lookup"><span data-stu-id="49914-207">Be sure to look at walls, ceilings, and floors.</span></span>

<span data-ttu-id="49914-208">**Erstellen und bereitstellen (Teil 2)**</span><span class="sxs-lookup"><span data-stu-id="49914-208">**Build and Deploy (part 2)**</span></span>

<span data-ttu-id="49914-209">Jetzt sehen wir uns wie räumliche Zuordnung Leistungseinbußen führen kann.</span><span class="sxs-lookup"><span data-stu-id="49914-209">Now let's explore how Spatial Mapping can affect performance.</span></span>
* <span data-ttu-id="49914-210">Wählen Sie in Unity **Fenster > Profiler**.</span><span class="sxs-lookup"><span data-stu-id="49914-210">In Unity, select **Window > Profiler**.</span></span>
* <span data-ttu-id="49914-211">Klicken Sie auf **Profiler hinzufügen > GPU**.</span><span class="sxs-lookup"><span data-stu-id="49914-211">Click **Add Profiler > GPU**.</span></span>
* <span data-ttu-id="49914-212">Klicken Sie auf **Active Profiler > <Enter IP>** .</span><span class="sxs-lookup"><span data-stu-id="49914-212">Click **Active Profiler > <Enter IP>**.</span></span>
* <span data-ttu-id="49914-213">Geben Sie die **IP-Adresse** von Ihrem HoloLens.</span><span class="sxs-lookup"><span data-stu-id="49914-213">Enter the **IP address** of your HoloLens.</span></span>
* <span data-ttu-id="49914-214">Klicken Sie auf **Verbinden**.</span><span class="sxs-lookup"><span data-stu-id="49914-214">Click **Connect**.</span></span>
* <span data-ttu-id="49914-215">Beachten Sie die Anzahl der Millisekunden, die es, bis die GPU dauert, einen Frame zu rendern.</span><span class="sxs-lookup"><span data-stu-id="49914-215">Observe the number of milliseconds it takes for the GPU to render a frame.</span></span>
* <span data-ttu-id="49914-216">Beenden Sie die Anwendung aus, die auf dem Gerät ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="49914-216">Stop the application from running on the device.</span></span>
* <span data-ttu-id="49914-217">Zurück zu Visual Studio, und öffnen Sie **SpatialMappingObserver.cs**.</span><span class="sxs-lookup"><span data-stu-id="49914-217">Return to Visual Studio and open **SpatialMappingObserver.cs**.</span></span> <span data-ttu-id="49914-218">Sie finden es im Ordner "HoloToolkit\SpatialMapping" des Projekts Assembly-CSharp (Universal Windows).</span><span class="sxs-lookup"><span data-stu-id="49914-218">You will find it in the HoloToolkit\SpatialMapping folder of the Assembly-CSharp (Universal Windows) project.</span></span>
* <span data-ttu-id="49914-219">Suchen der **Awake()** funktionieren, und fügen Sie die folgende Codezeile hinzu: **TrianglesPerCubicMeter = 1200;**</span><span class="sxs-lookup"><span data-stu-id="49914-219">Find the **Awake()** function, and add the following line of code: **TrianglesPerCubicMeter = 1200;**</span></span>
* <span data-ttu-id="49914-220">Erneutes Bereitstellen des Projekts auf Ihrem Gerät, und klicken Sie dann **verbinden Sie den Profiler**.</span><span class="sxs-lookup"><span data-stu-id="49914-220">Re-deploy the project to your device, and then **reconnect the profiler**.</span></span> <span data-ttu-id="49914-221">Beachten Sie die Änderung in die Anzahl der Millisekunden, die einen Frame zu rendern.</span><span class="sxs-lookup"><span data-stu-id="49914-221">Observe the change in the number of milliseconds to render a frame.</span></span>
* <span data-ttu-id="49914-222">Beenden Sie die Anwendung aus, die auf dem Gerät ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="49914-222">Stop the application from running on the device.</span></span>

<span data-ttu-id="49914-223">**Speichern Sie und Laden Sie in Unity**</span><span class="sxs-lookup"><span data-stu-id="49914-223">**Save and load in Unity**</span></span>

<span data-ttu-id="49914-224">Abschließend sehen wir unser Platz Netz zu speichern und Laden sie in Unity.</span><span class="sxs-lookup"><span data-stu-id="49914-224">Finally, let's save our room mesh and load it into Unity.</span></span>
* <span data-ttu-id="49914-225">Zurück zu Visual Studio, und entfernen Sie die **TrianglesPerCubicMeter** Zeile, die Sie in hinzugefügt haben die **Awake()** -Funktion während der im vorherigen Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="49914-225">Return to Visual Studio and remove the **TrianglesPerCubicMeter** line that you added in the **Awake()** function during the previous section.</span></span>
* <span data-ttu-id="49914-226">Bereitstellen Sie das Projekt auf Ihrem Gerät erneut.</span><span class="sxs-lookup"><span data-stu-id="49914-226">Redeploy the project to your device.</span></span> <span data-ttu-id="49914-227">Wir sollten jetzt ausgeführt werden, wobei **500** Dreiecke pro kubische Meter.</span><span class="sxs-lookup"><span data-stu-id="49914-227">We should now be running with **500** triangles per cubic meter.</span></span>
* <span data-ttu-id="49914-228">Öffnen Sie einen Browser, und geben Sie in Ihrem HoloLens IPAddress, zu dem navigiert die **Windows Device Portal**.</span><span class="sxs-lookup"><span data-stu-id="49914-228">Open a browser and enter in your HoloLens IPAddress to navigate to the **Windows Device Portal**.</span></span>
* <span data-ttu-id="49914-229">Wählen Sie die **-3D-Sicht** Option im linken Bereich.</span><span class="sxs-lookup"><span data-stu-id="49914-229">Select the **3D View** option in the left panel.</span></span>
* <span data-ttu-id="49914-230">Klicken Sie unter **Oberfläche Rekonstruktion** wählen Sie die **Update** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="49914-230">Under **Surface reconstruction** select the **Update** button.</span></span>
* <span data-ttu-id="49914-231">Sehen Sie sich, wie der Bereiche, die Sie für Ihre HoloLens überprüft haben, die in das Anzeigefenster angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="49914-231">Watch as the areas that you have scanned on your HoloLens appear in the display window.</span></span>
* <span data-ttu-id="49914-232">Um die Überprüfung der Raum zu speichern, drücken Sie die **speichern** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="49914-232">To save your room scan, press the **Save** button.</span></span>
* <span data-ttu-id="49914-233">Öffnen Ihrer **Downloads** Ordner aus, um das Modell gespeicherte Platz ermitteln **SRMesh.obj**.</span><span class="sxs-lookup"><span data-stu-id="49914-233">Open your **Downloads** folder to find the saved room model **SRMesh.obj**.</span></span>
* <span data-ttu-id="49914-234">Kopie **SRMesh.obj** auf die **Assets** Ordner Ihres Unity-Projekts.</span><span class="sxs-lookup"><span data-stu-id="49914-234">Copy **SRMesh.obj** to the **Assets** folder of your Unity project.</span></span>
* <span data-ttu-id="49914-235">Wählen Sie in Unity die **SpatialMapping** -Objekt in der **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="49914-235">In Unity, select the **SpatialMapping** object in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="49914-236">Suchen Sie die **Objekt Oberfläche Beobachter (Skript)** Komponente.</span><span class="sxs-lookup"><span data-stu-id="49914-236">Locate the **Object Surface Observer (Script)** component.</span></span>
* <span data-ttu-id="49914-237">Klicken Sie auf den Kreis neben der **Platz Modell** Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="49914-237">Click the circle to the right of the **Room Model** property.</span></span>
* <span data-ttu-id="49914-238">Suchen und Auswählen der **SRMesh** Objekt aus, und klicken Sie dann das Fenster schließen.</span><span class="sxs-lookup"><span data-stu-id="49914-238">Find and select the **SRMesh** object and then close the window.</span></span>
* <span data-ttu-id="49914-239">Überprüfen Sie, ob die **Platz Modell** -Eigenschaft in der **Inspektor** Bereich ist nun so festgelegt **SRMesh**.</span><span class="sxs-lookup"><span data-stu-id="49914-239">Verify that the **Room Model** property in the **Inspector** panel is now set to **SRMesh**.</span></span>
* <span data-ttu-id="49914-240">Drücken Sie die **spielen** Schaltfläche Unity Vorschaumodus eingeben.</span><span class="sxs-lookup"><span data-stu-id="49914-240">Press the **Play** button to enter Unity's preview mode.</span></span>
* <span data-ttu-id="49914-241">Die SpatialMapping-Komponente wird die Gitter aus dem Modell gespeicherten Platz geladen, damit Sie sie in Unity verwenden können.</span><span class="sxs-lookup"><span data-stu-id="49914-241">The SpatialMapping component will load the meshes from the saved room model so you can use them in Unity.</span></span>
* <span data-ttu-id="49914-242">Wechseln Sie zur **Szene** Ansicht, um die Anzeige aller Ihr Platz-Modell, das mit dem Shader Drahtmodell angezeigt.</span><span class="sxs-lookup"><span data-stu-id="49914-242">Switch to **Scene** view to see all of your room model displayed with the wireframe shader.</span></span>
* <span data-ttu-id="49914-243">Drücken Sie die **spielen** Schaltfläche erneut aus, um im Vorschaumodus zu beenden.</span><span class="sxs-lookup"><span data-stu-id="49914-243">Press the **Play** button again to exit preview mode.</span></span>

<span data-ttu-id="49914-244">**HINWEIS:** Das nächste Mal die Eingabe im Vorschaumodus in Unity wird das Netz gespeicherten Platz standardmäßig geladen.</span><span class="sxs-lookup"><span data-stu-id="49914-244">**NOTE:** The next time that you enter preview mode in Unity, it will load the saved room mesh by default.</span></span>

## <a name="chapter-2---visualization"></a><span data-ttu-id="49914-245">Kapitel 2: Visualisierung</span><span class="sxs-lookup"><span data-stu-id="49914-245">Chapter 2 - Visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

<span data-ttu-id="49914-246">**Ziele**</span><span class="sxs-lookup"><span data-stu-id="49914-246">**Objectives**</span></span>
* <span data-ttu-id="49914-247">Enthält die Grundlagen von Shadern.</span><span class="sxs-lookup"><span data-stu-id="49914-247">Learn the basics of shaders.</span></span>
* <span data-ttu-id="49914-248">Visualisieren Sie Ihre Umgebung.</span><span class="sxs-lookup"><span data-stu-id="49914-248">Visualize your surroundings.</span></span>

<span data-ttu-id="49914-249">**Anweisungen**</span><span class="sxs-lookup"><span data-stu-id="49914-249">**Instructions**</span></span>
* <span data-ttu-id="49914-250">In Unity **Hierarchie** wählen die **SpatialMapping** Objekt.</span><span class="sxs-lookup"><span data-stu-id="49914-250">In Unity's **Hierarchy** panel, select the **SpatialMapping** object.</span></span>
* <span data-ttu-id="49914-251">In der **Inspektor** Bereich, suchen Sie nach der **räumliche Zuordnungs-Manager (Skript)** Komponente.</span><span class="sxs-lookup"><span data-stu-id="49914-251">In the **Inspector** panel, find the **Spatial Mapping Manager (Script)** component.</span></span>
* <span data-ttu-id="49914-252">Klicken Sie auf den Kreis neben der **Oberfläche Material** Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="49914-252">Click the circle to the right of the **Surface Material** property.</span></span>
* <span data-ttu-id="49914-253">Suchen und Auswählen der **BlueLinesOnWalls** "Material" und schließen Sie das Fenster.</span><span class="sxs-lookup"><span data-stu-id="49914-253">Find and select the **BlueLinesOnWalls** material and close the window.</span></span>
* <span data-ttu-id="49914-254">In der **Projekt** Bereich **Shader** Ordner, doppelklicken Sie auf **BlueLinesOnWalls** auf den Shader in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="49914-254">In the **Project** panel **Shaders** folder, double-click on **BlueLinesOnWalls** to open the shader in Visual Studio.</span></span>
* <span data-ttu-id="49914-255">Dies ist eine einfache Pixelverarbeitungsvorgänge (Vertex, fragment) Shader, der die folgenden Aufgaben erledigt wird:</span><span class="sxs-lookup"><span data-stu-id="49914-255">This is a simple pixel (vertex to fragment) shader, which accomplishes the following tasks:</span></span>
    1. <span data-ttu-id="49914-256">Konvertiert des Vertex-Speicherort in einen Raum der Welt.</span><span class="sxs-lookup"><span data-stu-id="49914-256">Converts a vertex's location to world space.</span></span>
    2. <span data-ttu-id="49914-257">Überprüft, dass der Scheitelpunkt ist normal, um festzustellen, ob eine Pixel vertikal ist.</span><span class="sxs-lookup"><span data-stu-id="49914-257">Checks the vertex's normal to determine if a pixel is vertical.</span></span>
    3. <span data-ttu-id="49914-258">Legt die Farbe des Pixels für das Rendering.</span><span class="sxs-lookup"><span data-stu-id="49914-258">Sets the color of the pixel for rendering.</span></span>

<span data-ttu-id="49914-259">**Erstellen und bereitstellen**</span><span class="sxs-lookup"><span data-stu-id="49914-259">**Build and Deploy**</span></span>
* <span data-ttu-id="49914-260">Zurück zu Unity, und drücken Sie **spielen** Vorschaumodus eingeben.</span><span class="sxs-lookup"><span data-stu-id="49914-260">Return to Unity and press **Play** to enter preview mode.</span></span>
* <span data-ttu-id="49914-261">Blaue Linien werden auf alle vertikale Oberflächen des Netzes Platz gerendert werden (die aus den gespeicherten Scannen Daten automatisch geladen wird).</span><span class="sxs-lookup"><span data-stu-id="49914-261">Blue lines will be rendered on all vertical surfaces of the room mesh (which automatically loaded from our saved scanning data).</span></span>
* <span data-ttu-id="49914-262">Wechseln Sie zu der **Szene** Registerkarte Anpassen Ihrer Ansicht des Raums und wie das Netz ganzen Raum in Unity angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="49914-262">Switch to the **Scene** tab to adjust your view of the room and see how the entire room mesh appears in Unity.</span></span>
* <span data-ttu-id="49914-263">In der **Projekt** Bereich, suchen Sie nach der **Materialien** Ordner, und wählen die **BlueLinesOnWalls** Material.</span><span class="sxs-lookup"><span data-stu-id="49914-263">In the **Project** panel, find the **Materials** folder and select the **BlueLinesOnWalls** material.</span></span>
* <span data-ttu-id="49914-264">Ändern Sie einige Eigenschaften, und sehen Sie, wie die Änderungen im Unity-Editor angezeigt.</span><span class="sxs-lookup"><span data-stu-id="49914-264">Modify some properties and see how the changes appear in the Unity editor.</span></span>
    * <span data-ttu-id="49914-265">In der **Inspektor** panel, passen Sie die **LineScale** Wert, um die Zeilen dicker oder schlankere angezeigt herzustellen.</span><span class="sxs-lookup"><span data-stu-id="49914-265">In the **Inspector** panel, adjust the **LineScale** value to make the lines appear thicker or thinner.</span></span>
    * <span data-ttu-id="49914-266">In der **Inspektor** panel, passen Sie die **LinesPerMeter** Wert ändern, wie viele Zeilen für jede Wand angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="49914-266">In the **Inspector** panel, adjust the **LinesPerMeter** value to change how many lines appear on each wall.</span></span>
* <span data-ttu-id="49914-267">Klicken Sie auf **spielen** erneut aus, um im Vorschaumodus zu beenden.</span><span class="sxs-lookup"><span data-stu-id="49914-267">Click **Play** again to exit preview mode.</span></span>
* <span data-ttu-id="49914-268">Erstellen Sie und Bereitstellen Sie, die HoloLens, und beobachten Sie, wie der Shader, der rendering auf echten Oberflächen angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="49914-268">Build and deploy to the HoloLens and observe how the shader rendering appears on real surfaces.</span></span>

<span data-ttu-id="49914-269">Unity eignet sich gut in der Vorschau anzuzeigen Materialien, aber es ist immer eine gute Idee, informieren Sie sich Rendering auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="49914-269">Unity does a great job of previewing materials, but it's always a good idea to check-out rendering in the device.</span></span>

## <a name="chapter-3---processing"></a><span data-ttu-id="49914-270">Kapitel 3 – verarbeiten</span><span class="sxs-lookup"><span data-stu-id="49914-270">Chapter 3 - Processing</span></span>

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

<span data-ttu-id="49914-271">**Ziele**</span><span class="sxs-lookup"><span data-stu-id="49914-271">**Objectives**</span></span>
* <span data-ttu-id="49914-272">Erfahren Sie, Verfahren, um räumliche Zuordnung von Daten für die Verwendung in Ihrer Anwendung zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="49914-272">Learn techniques to process spatial mapping data for use in your application.</span></span>
* <span data-ttu-id="49914-273">Analysieren Sie Daten räumliche Zuordnung, um Ebenen zu finden und Dreiecke zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="49914-273">Analyze spatial mapping data to find planes and remove triangles.</span></span>
* <span data-ttu-id="49914-274">Verwenden Sie für die Platzierung von – Hologramm Ebenen.</span><span class="sxs-lookup"><span data-stu-id="49914-274">Use planes for hologram placement.</span></span>

<span data-ttu-id="49914-275">**Anweisungen**</span><span class="sxs-lookup"><span data-stu-id="49914-275">**Instructions**</span></span>
* <span data-ttu-id="49914-276">In Unity **Projekt** Bereich **Hologramme** Ordner finden Sie die **SpatialProcessing** Objekt.</span><span class="sxs-lookup"><span data-stu-id="49914-276">In Unity's **Project** panel, **Holograms** folder, find the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="49914-277">Drag & drop die **SpatialProcessing** -Objekt in der **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="49914-277">Drag & drop the **SpatialProcessing** object into the **Hierarchy** panel.</span></span>

<span data-ttu-id="49914-278">Das Prefab SpatialProcessing enthält Komponenten für die Verarbeitung der Daten für die räumliche Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="49914-278">The SpatialProcessing prefab includes components for processing the spatial mapping data.</span></span> <span data-ttu-id="49914-279">**SurfaceMeshesToPlanes.cs** findet und Ebenen, die basierend auf den spatial Zuordnungsdaten zu generieren.</span><span class="sxs-lookup"><span data-stu-id="49914-279">**SurfaceMeshesToPlanes.cs** will find and generate planes based on the spatial mapping data.</span></span> <span data-ttu-id="49914-280">Wir verwenden Ebenen in unserer Anwendung, Wände, Etagen und Obergrenzen darstellen.</span><span class="sxs-lookup"><span data-stu-id="49914-280">We will use planes in our application to represent walls, floors and ceilings.</span></span> <span data-ttu-id="49914-281">Diese Prefab enthält auch **RemoveSurfaceVertices.cs** können die Scheitelpunkte aus dem Netz räumliche Zuordnung entfernen.</span><span class="sxs-lookup"><span data-stu-id="49914-281">This prefab also includes **RemoveSurfaceVertices.cs** which can remove vertices from the spatial mapping mesh.</span></span> <span data-ttu-id="49914-282">Dies kann verwendet werden, um Lücken im Netz zu erstellen oder überschüssige Dreiecke zu entfernen, die nicht mehr benötigt werden (da Ebenen stattdessen verwendet werden können).</span><span class="sxs-lookup"><span data-stu-id="49914-282">This can be used to create holes in the mesh, or to remove excess triangles that are no longer needed (because planes can be used instead).</span></span>
* <span data-ttu-id="49914-283">In Unity **Projekt** Bereich **Hologramme** Ordner finden Sie die **SpaceCollection** Objekt.</span><span class="sxs-lookup"><span data-stu-id="49914-283">In Unity's **Project** panel, **Holograms** folder, find the **SpaceCollection** object.</span></span>
* <span data-ttu-id="49914-284">Drag & drop die **SpaceCollection** -Objekt in der **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="49914-284">Drag and drop the **SpaceCollection** object into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="49914-285">In der **Hierarchie** wählen die **SpatialProcessing** Objekt.</span><span class="sxs-lookup"><span data-stu-id="49914-285">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="49914-286">In der **Inspektor** Bereich, suchen Sie nach der **spielen Space-Manager (Skript)** Komponente.</span><span class="sxs-lookup"><span data-stu-id="49914-286">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="49914-287">Doppelklicken Sie auf **PlaySpaceManager.cs** um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="49914-287">Double-click on **PlaySpaceManager.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="49914-288">PlaySpaceManager.cs enthält anwendungsspezifische Code.</span><span class="sxs-lookup"><span data-stu-id="49914-288">PlaySpaceManager.cs contains application-specific code.</span></span> <span data-ttu-id="49914-289">Wir werden dieses Skript so aktivieren Sie das folgende Verhalten Funktionalität hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="49914-289">We will add functionality to this script to enable the following behavior:</span></span>
1. <span data-ttu-id="49914-290">Beenden der Datensammlung räumliche Zuordnung, nachdem die Überprüfung Zeitlimit (10 Sekunden) überschritten.</span><span class="sxs-lookup"><span data-stu-id="49914-290">Stop collecting spatial mapping data after we exceed the scanning time limit (10 seconds).</span></span>
2. <span data-ttu-id="49914-291">Die räumliche Zuordnung-Daten verarbeiten:</span><span class="sxs-lookup"><span data-stu-id="49914-291">Process the spatial mapping data:</span></span>
    1. <span data-ttu-id="49914-292">Verwenden Sie SurfaceMeshesToPlanes, um einer einfacheren Darstellung der Welt als Ebenen (Wände, Etagen, Obergrenzen, usw.) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="49914-292">Use SurfaceMeshesToPlanes to create a simpler representation of the world as planes (walls, floors, ceilings, etc).</span></span>
    2. <span data-ttu-id="49914-293">Verwenden Sie RemoveSurfaceVertices Oberfläche Dreiecke zu entfernen, die in der Datenebene Grenzen liegen.</span><span class="sxs-lookup"><span data-stu-id="49914-293">Use RemoveSurfaceVertices to remove surface triangles that fall within plane boundaries.</span></span>
3. <span data-ttu-id="49914-294">Generieren Sie eine Auflistung von Hologramme in der ganzen Welt, und platzieren Sie sie auf die Wand und Floor Ebenen in der Nähe der Benutzer.</span><span class="sxs-lookup"><span data-stu-id="49914-294">Generate a collection of holograms in the world and place them on wall and floor planes near the user.</span></span>

<span data-ttu-id="49914-295">Führen Sie die markierten PlaySpaceManager.cs codierungsübungen, oder Ersetzen Sie das Skript mit dem fertigen Lösung von unten:</span><span class="sxs-lookup"><span data-stu-id="49914-295">Complete the coding exercises marked in PlaySpaceManager.cs, or replace the script with the finished solution from below:</span></span>

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by 
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

<span data-ttu-id="49914-296">**Erstellen und bereitstellen**</span><span class="sxs-lookup"><span data-stu-id="49914-296">**Build and Deploy**</span></span>
* <span data-ttu-id="49914-297">Vor der Bereitstellung, die HoloLens, drücken Sie die **spielen** -Schaltfläche in Unity Spielmodus eingeben.</span><span class="sxs-lookup"><span data-stu-id="49914-297">Before deploying to the HoloLens, press the **Play** button in Unity to enter play mode.</span></span>
* <span data-ttu-id="49914-298">Nach dem Raum Netz aus der Datei geladen wird, warten Sie 10 Sekunden vor Beginn der Verarbeitung des Netzes räumliche Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="49914-298">After the room mesh is loaded from file, wait for 10 seconds before processing starts on the spatial mapping mesh.</span></span>
* <span data-ttu-id="49914-299">Wenn die Verarbeitung abgeschlossen ist, werden Ebenen darstellen, Floor, Wände, Ceiling usw. angezeigt.</span><span class="sxs-lookup"><span data-stu-id="49914-299">When processing is complete, planes will appear to represent the floor, walls, ceiling, etc.</span></span>
* <span data-ttu-id="49914-300">Nachdem alle wurden der Ebenen gefunden. Daraufhin sollte ein Sonnensystem auf eine Tabelle mit Floor in der Nähe der Kamera angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="49914-300">After all of the planes have been found, you should see a solar system appear on a table of floor near the camera.</span></span>
* <span data-ttu-id="49914-301">Zwei Poster sollte zu Wände in der Nähe der Kamera angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="49914-301">Two posters should appear on walls near the camera too.</span></span> <span data-ttu-id="49914-302">Wechseln Sie zu der **Szene** Registerkarte, wenn sie in nicht **Spiel** Modus.</span><span class="sxs-lookup"><span data-stu-id="49914-302">Switch to the **Scene** tab if you cannot see them in **Game** mode.</span></span>
* <span data-ttu-id="49914-303">Drücken Sie die **spielen** Schaltfläche wieder zu Spielmodus zu schließen.</span><span class="sxs-lookup"><span data-stu-id="49914-303">Press the **Play** button again to exit play mode.</span></span>
* <span data-ttu-id="49914-304">Erstellen Sie und Bereitstellen Sie, die HoloLens, wie gewohnt.</span><span class="sxs-lookup"><span data-stu-id="49914-304">Build and deploy to the HoloLens, as usual.</span></span>
* <span data-ttu-id="49914-305">Warten Sie scannen und die Verarbeitung der Daten räumliche Zuordnung abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="49914-305">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="49914-306">Sobald Ebenen angezeigt werden, versuchen Sie es, um den Sonnensystem und Poster in Ihre Welt zu finden.</span><span class="sxs-lookup"><span data-stu-id="49914-306">Once you see planes, try to find the solar system and posters in your world.</span></span>

## <a name="chapter-4---placement"></a><span data-ttu-id="49914-307">Kapitel 4 - Platzierung</span><span class="sxs-lookup"><span data-stu-id="49914-307">Chapter 4 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

<span data-ttu-id="49914-308">**Ziele**</span><span class="sxs-lookup"><span data-stu-id="49914-308">**Objectives**</span></span>
* <span data-ttu-id="49914-309">Bestimmt, ob Sie ggf. ein Hologramm auf einer Oberfläche passt.</span><span class="sxs-lookup"><span data-stu-id="49914-309">Determine if a hologram will fit on a surface.</span></span>
* <span data-ttu-id="49914-310">Geben Sie Feedback an den Benutzer, wenn auf einer Oberfläche ggf. ein Hologramm passen kann/kann nicht.</span><span class="sxs-lookup"><span data-stu-id="49914-310">Provide feedback to the user when a hologram can/cannot fit on a surface.</span></span>

<span data-ttu-id="49914-311">**Anweisungen**</span><span class="sxs-lookup"><span data-stu-id="49914-311">**Instructions**</span></span>
* <span data-ttu-id="49914-312">In Unity **Hierarchie** wählen die **SpatialProcessing** Objekt.</span><span class="sxs-lookup"><span data-stu-id="49914-312">In Unity's **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="49914-313">In der **Inspektor** Bereich, suchen Sie nach der **Oberfläche, Gitter zu Ebenen (Skript)** Komponente.</span><span class="sxs-lookup"><span data-stu-id="49914-313">In the **Inspector** panel, find the **Surface Meshes To Planes (Script)** component.</span></span>
* <span data-ttu-id="49914-314">Ändern der **Ebenen zeichnen** Eigenschaft **nichts** um die Auswahl aufzuheben.</span><span class="sxs-lookup"><span data-stu-id="49914-314">Change the **Draw Planes** property to **Nothing** to clear the selection.</span></span>
* <span data-ttu-id="49914-315">Ändern der **Ebenen zeichnen** Eigenschaft **Wand**, sodass nur die Wand Ebenen gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="49914-315">Change the **Draw Planes** property to **Wall**, so that only wall planes will be rendered.</span></span>
* <span data-ttu-id="49914-316">In der **Projekt** Bereich **Skripts** Doppelklicken Sie auf Ordner **Placeable.cs** um sie in Visual Studio öffnen.</span><span class="sxs-lookup"><span data-stu-id="49914-316">In the **Project** panel, **Scripts** folder, double-click on **Placeable.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="49914-317">Die **Placeable** Skript bereits an das Poster und die Projektion-Feld, die erstellt werden, nach Abschluss der Datenebene suchen angefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="49914-317">The **Placeable** script is already attached to the posters and projection box that are created after plane finding completes.</span></span> <span data-ttu-id="49914-318">Alles, was erforderlich ist, ist einige Code auskommentiert haben und dieses Skript wird Folgendes erreichen:</span><span class="sxs-lookup"><span data-stu-id="49914-318">All we need to do is uncomment some code, and this script will achieve the following:</span></span>
1. <span data-ttu-id="49914-319">Bestimmt, ob Sie ggf. ein Hologramm auf einer Oberfläche von feinheiten beim Raycasting, aus dem Mittelpunkt und die vier Ecken des umschließenden Cubes passt.</span><span class="sxs-lookup"><span data-stu-id="49914-319">Determine if a hologram will fit on a surface by raycasting from the center and four corners of the bounding cube.</span></span>
2. <span data-ttu-id="49914-320">Überprüfen Sie die Oberfläche zu bestimmen, ob sie genug für die Hologramm gerne leeren auf verläuft normal.</span><span class="sxs-lookup"><span data-stu-id="49914-320">Check the surface normal to determine if it is smooth enough for the hologram to sit flush on.</span></span>
3. <span data-ttu-id="49914-321">Rendern Sie einen umgebenden Cube mit den Hologramm die tatsächliche Größe angezeigt werden, während des Einfügens.</span><span class="sxs-lookup"><span data-stu-id="49914-321">Render a bounding cube around the hologram to show its actual size while being placed.</span></span>
4. <span data-ttu-id="49914-322">Wandeln Sie einen Schatten unter bzw. hinter der – Hologramm, um anzuzeigen, wo er an den Boden/Wand platziert werden.</span><span class="sxs-lookup"><span data-stu-id="49914-322">Cast a shadow under/behind the hologram to show where it will be placed on the floor/wall.</span></span>
5. <span data-ttu-id="49914-323">Rendern des Schattens Rot dargestellt, ein, wenn es sich bei der – Hologramm kann nicht auf die Entwurfsoberfläche, oder Grün, platziert werden, sofern dies möglich.</span><span class="sxs-lookup"><span data-stu-id="49914-323">Render the shadow as red, if the hologram cannot be placed on the surface, or green, if it can.</span></span>
6. <span data-ttu-id="49914-324">Neu ausrichten der – Hologramm, um mit dem Surface-Typ (vertikal oder horizontal) auszurichten, dass sie die Affinität für hat.</span><span class="sxs-lookup"><span data-stu-id="49914-324">Re-orient the hologram to align with the surface type (vertical or horizontal) that it has affinity to.</span></span>
7. <span data-ttu-id="49914-325">Platzieren Sie den – Hologramm reibungslos auf der ausgewählten Fläche springen oder Andocken Verhalten vermeiden.</span><span class="sxs-lookup"><span data-stu-id="49914-325">Smoothly place the hologram on the selected surface to avoid jumping or snapping behavior.</span></span>

<span data-ttu-id="49914-326">Entfernen Sie alle Code in der Programmierung Übung unten aus, oder verwenden Sie diese abgeschlossenen Lösung in **Placeable.cs**:</span><span class="sxs-lookup"><span data-stu-id="49914-326">Uncomment all code in the coding exercise below, or use this completed solution in **Placeable.cs**:</span></span>

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.    
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The aligntoVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.        
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

<span data-ttu-id="49914-327">**Erstellen und bereitstellen**</span><span class="sxs-lookup"><span data-stu-id="49914-327">**Build and Deploy**</span></span>
* <span data-ttu-id="49914-328">Wie zuvor, erstellen Sie das Projekt aus, und stellen in die HoloLens.</span><span class="sxs-lookup"><span data-stu-id="49914-328">As before, build the project and deploy to the HoloLens.</span></span>
* <span data-ttu-id="49914-329">Warten Sie scannen und die Verarbeitung der Daten räumliche Zuordnung abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="49914-329">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="49914-330">Wenn Sonnensystem angezeigt wird, auf das nachfolgende Feld Projektion bestaunen Sie, und führen Sie eine Option Geste, verschieben Sie ihn.</span><span class="sxs-lookup"><span data-stu-id="49914-330">When you see the solar system, gaze at the projection box below and perform a select gesture to move it around.</span></span> <span data-ttu-id="49914-331">Während der Projektion Feld ausgewählt ist, werden ein umgebenden Cube angezeigt, um das Feld für die Projektion.</span><span class="sxs-lookup"><span data-stu-id="49914-331">While the projection box is selected, a bounding cube will be visible around the projection box.</span></span>
* <span data-ttu-id="49914-332">Verschieben Sie Sie an einer anderen Stelle im Raum bestaunen lesen.</span><span class="sxs-lookup"><span data-stu-id="49914-332">Move you head to gaze at a different location in the room.</span></span> <span data-ttu-id="49914-333">Das Feld für die Projektion, sollte Ihre Blicke folgen.</span><span class="sxs-lookup"><span data-stu-id="49914-333">The projection box should follow your gaze.</span></span> <span data-ttu-id="49914-334">Wenn der Schatten unterhalb des Felds Projektion rot angezeigt wird, können nicht Sie Hologramm auf, die dann platzieren.</span><span class="sxs-lookup"><span data-stu-id="49914-334">When the shadow below the projection box turns red, you cannot place the hologram on that surface.</span></span> <span data-ttu-id="49914-335">Wenn der Schatten unterhalb des Felds Projektion Grün, können Sie die – Hologramm platzieren, anhand einer anderen Option Geste.</span><span class="sxs-lookup"><span data-stu-id="49914-335">When the shadow below the projection box turns green, you can place the hologram by performing another select gesture.</span></span>
* <span data-ttu-id="49914-336">Suchen Sie und wählen Sie eine holographic Poster an einer Wand in einem neuen Speicherort zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="49914-336">Find and select one of the holographic posters on a wall to move it to a new location.</span></span> <span data-ttu-id="49914-337">Beachten Sie, dass das Poster kann nicht auf dem Boden oder Ceiling man und, es auf jede Wand richtig ausgerichtet bleibt, wenn Sie bewegen.</span><span class="sxs-lookup"><span data-stu-id="49914-337">Notice that you cannot place the poster on the floor or ceiling, and that it stays correctly oriented to each wall as you move around.</span></span>

## <a name="chapter-5---occlusion"></a><span data-ttu-id="49914-338">Kapitel 5 – verdecken</span><span class="sxs-lookup"><span data-stu-id="49914-338">Chapter 5 - Occlusion</span></span>

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

<span data-ttu-id="49914-339">**Ziele**</span><span class="sxs-lookup"><span data-stu-id="49914-339">**Objectives**</span></span>
* <span data-ttu-id="49914-340">Bestimmt, ob durch das Netz räumliche Zuordnung ggf. ein Hologramm okkludierte ist.</span><span class="sxs-lookup"><span data-stu-id="49914-340">Determine if a hologram is occluded by the spatial mapping mesh.</span></span>
* <span data-ttu-id="49914-341">Anwenden von verschiedenen verdecken-Techniken, um ein unterhaltsames zu erreichen wirksam.</span><span class="sxs-lookup"><span data-stu-id="49914-341">Apply different occlusion techniques to achieve a fun effect.</span></span>

<span data-ttu-id="49914-342">**Anweisungen**</span><span class="sxs-lookup"><span data-stu-id="49914-342">**Instructions**</span></span>

<span data-ttu-id="49914-343">Zunächst werden wir räumliche Zuordnung Mesh zu anderen Hologramme verdeckt wird, ohne die reale Welt occluding zulassen:</span><span class="sxs-lookup"><span data-stu-id="49914-343">First, we are going to allow the spatial mapping mesh to occlude other holograms without occluding the real world:</span></span>
* <span data-ttu-id="49914-344">In der **Hierarchie** wählen die **SpatialProcessing** Objekt.</span><span class="sxs-lookup"><span data-stu-id="49914-344">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="49914-345">In der **Inspektor** Bereich, suchen Sie nach der **spielen Space-Manager (Skript)** Komponente.</span><span class="sxs-lookup"><span data-stu-id="49914-345">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="49914-346">Klicken Sie auf den Kreis neben der **sekundären Material** Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="49914-346">Click the circle to the right of the **Secondary Material** property.</span></span>
* <span data-ttu-id="49914-347">Suchen und Auswählen der **verdecken** "Material" und schließen Sie das Fenster.</span><span class="sxs-lookup"><span data-stu-id="49914-347">Find and select the **Occlusion** material and close the window.</span></span>

<span data-ttu-id="49914-348">Als Nächstes werden wir ein besonderes Verhalten auf der Erde, hinzufügen, damit sie eine blaue Hervorhebung aufweist, wenn er durch einen anderen Hologramm (z. B. die Sonne) oder durch das Netz räumliche Zuordnung okkludierte wird:</span><span class="sxs-lookup"><span data-stu-id="49914-348">Next, we are going to add a special behavior to Earth, so that it has a blue highlight whenever it becomes occluded by another hologram (like the sun), or by the spatial mapping mesh:</span></span>
* <span data-ttu-id="49914-349">In der **Projekt** im Bereich der **Hologramme** Ordner, erweitern Sie die **SolarSystem** Objekt.</span><span class="sxs-lookup"><span data-stu-id="49914-349">In the **Project** panel, in the **Holograms** folder, expand the **SolarSystem** object.</span></span>
* <span data-ttu-id="49914-350">Klicken Sie auf **Earth**.</span><span class="sxs-lookup"><span data-stu-id="49914-350">Click on **Earth**.</span></span>
* <span data-ttu-id="49914-351">In der **Inspektor** Bereich, der Erde Material (unten Komponente) zu finden.</span><span class="sxs-lookup"><span data-stu-id="49914-351">In the **Inspector** panel, find the Earth's material (bottom component).</span></span>
* <span data-ttu-id="49914-352">In der **Shader Dropdownliste**, ändern Sie den Shader **benutzerdefinierte > OcclusionRim**.</span><span class="sxs-lookup"><span data-stu-id="49914-352">In the **Shader drop-down**, change the shader to **Custom > OcclusionRim**.</span></span> <span data-ttu-id="49914-353">Dadurch wird eine blaue Hervorhebung um Earth gerendert, wenn er von einem anderen Objekt okkludierte ist.</span><span class="sxs-lookup"><span data-stu-id="49914-353">This will render a blue highlight around Earth whenever it is occluded by another object.</span></span>

<span data-ttu-id="49914-354">Abschließend werden wir einen x-Ray Vision Effekt für Planeten unseres Sonnensystems zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="49914-354">Finally, we are going to enable an x-ray vision effect for planets in our solar system.</span></span> <span data-ttu-id="49914-355">Wir müssen bearbeiten **PlanetOcclusion.cs** (finden Sie im Ordner "Scripts\SolarSystem") um Folgendes zu erreichen:</span><span class="sxs-lookup"><span data-stu-id="49914-355">We will need to edit **PlanetOcclusion.cs** (found in the Scripts\SolarSystem folder) in order to achieve the following:</span></span>
1. <span data-ttu-id="49914-356">Bestimmt, ob eine Planeten von der SpatialMapping-Ebene (Platz Gitter und Ebenen) okkludierte ist.</span><span class="sxs-lookup"><span data-stu-id="49914-356">Determine if a planet is occluded by the SpatialMapping layer (room meshes and planes).</span></span>
2. <span data-ttu-id="49914-357">Zeigen Sie die Drahtmodell Darstellung einer weltweit, wenn es von der Ebene SpatialMapping okkludierte ist.</span><span class="sxs-lookup"><span data-stu-id="49914-357">Show the wireframe representation of a planet whenever it is occluded by the SpatialMapping layer.</span></span>
3. <span data-ttu-id="49914-358">Blenden Sie die Drahtmodell Darstellung einer weltweit, wenn er nicht von der Ebene SpatialMapping blockiert wird.</span><span class="sxs-lookup"><span data-stu-id="49914-358">Hide the wireframe representation of a planet when it is not blocked by the SpatialMapping layer.</span></span>

<span data-ttu-id="49914-359">Führen Sie die Codierung Übung in PlanetOcclusion.cs, oder verwenden Sie die folgende Lösung:</span><span class="sxs-lookup"><span data-stu-id="49914-359">Follow the coding exercise in PlanetOcclusion.cs, or use the following solution:</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

<span data-ttu-id="49914-360">**Erstellen und bereitstellen**</span><span class="sxs-lookup"><span data-stu-id="49914-360">**Build and Deploy**</span></span>
* <span data-ttu-id="49914-361">Erstellen und die Anwendung für HoloLens, wie gewohnt bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="49914-361">Build and deploy the application to HoloLens, as usual.</span></span>
* <span data-ttu-id="49914-362">Warten Sie, zu scannen und die Verarbeitung der Daten räumliche Zuordnung abgeschlossen sein, (daraufhin blaue Linien in Wände angezeigt werden).</span><span class="sxs-lookup"><span data-stu-id="49914-362">Wait for scanning and processing of the spatial mapping data to be complete (you should see blue lines appear on walls).</span></span>
* <span data-ttu-id="49914-363">Suchen Sie und Kontrollkästchen Sie das Sonnensystem Projektion, und legen Sie dann das Kontrollkästchen neben einer Wand oder hinter einen Leistungsindikator.</span><span class="sxs-lookup"><span data-stu-id="49914-363">Find and select the solar system's projection box and then set the box next to a wall or behind a counter.</span></span>
* <span data-ttu-id="49914-364">Sie können grundlegende verdecken von ausblenden hinter Flächen auf das Poster oder Projektion Peering anzeigen.</span><span class="sxs-lookup"><span data-stu-id="49914-364">You can view basic occlusion by hiding behind surfaces to peer at the poster or projection box.</span></span>
* <span data-ttu-id="49914-365">Suchen Sie nach der Erde, sollte eine blaue Hervorhebung Auswirkung, wenn darin hinter einer anderen – Hologramm oder Fläche.</span><span class="sxs-lookup"><span data-stu-id="49914-365">Look for the Earth, there should be a blue highlight effect whenever it goes behind another hologram or surface.</span></span>
* <span data-ttu-id="49914-366">Sehen Sie sich, wie die Planeten hinter die Wand oder andere Oberflächen im Raum verschieben.</span><span class="sxs-lookup"><span data-stu-id="49914-366">Watch as the planets move behind the wall or other surfaces in the room.</span></span> <span data-ttu-id="49914-367">X-Ray-Vision und alle ihre Drahtmodell Skelette sehen!</span><span class="sxs-lookup"><span data-stu-id="49914-367">You now have x-ray vision and can see their wireframe skeletons!</span></span>

## <a name="the-end"></a><span data-ttu-id="49914-368">Das Ende</span><span class="sxs-lookup"><span data-stu-id="49914-368">The End</span></span>

<span data-ttu-id="49914-369">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="49914-369">Congratulations!</span></span> <span data-ttu-id="49914-370">Sie haben jetzt **MR räumliche 230: Räumliche Zuordnung**.</span><span class="sxs-lookup"><span data-stu-id="49914-370">You have now completed **MR Spatial 230: Spatial mapping**.</span></span>
* <span data-ttu-id="49914-371">Sie wissen, wie Sie Ihre Umgebung und Load räumliche Zuordnungsdaten mit Unity zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="49914-371">You know how to scan your environment and load spatial mapping data to Unity.</span></span>
* <span data-ttu-id="49914-372">Sie kennen die Grundlagen der Shader und wie Materialien verwendet werden können, um die Welt neu zu visualisieren.</span><span class="sxs-lookup"><span data-stu-id="49914-372">You understand the basics of shaders and how materials can be used to re-visualize the world.</span></span>
* <span data-ttu-id="49914-373">Sie erfahren, von der Verarbeitungstechniken für die Suche nach Ebenen aus, und Entfernen von Dreiecke aus einem Mesh.</span><span class="sxs-lookup"><span data-stu-id="49914-373">You learned of new processing techniques for finding planes and removing triangles from a mesh.</span></span>
* <span data-ttu-id="49914-374">Sie konnten zu verschieben, und platzieren Sie Hologramme auf Oberflächen, die sinnvoll vorgenommen.</span><span class="sxs-lookup"><span data-stu-id="49914-374">You were able to move and place holograms on surfaces that made sense.</span></span>
* <span data-ttu-id="49914-375">Sie verdecken von verschiedenen Techniken aufgetreten und ein Showcase mit die Leistungsfähigkeit von x-Ray-maschinelles sehen.</span><span class="sxs-lookup"><span data-stu-id="49914-375">You experienced different occlusion techniques and harnessed the power of x-ray vision!</span></span>
