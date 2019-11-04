---
title: Räumliche 230-räumliche Zuordnung
description: Befolgen Sie diese exemplarische Vorgehensweise für die Code Erstellung mithilfe von Unity, Visual Studio und hololens, um die Details der Konzepte räumlicher Zuordnung kennenzulernen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, Tutorial, räumliche Zuordnung, Oberflächenrekonstruktion, Mesh
ms.openlocfilehash: cf4a2dd3e5eb74c0aaf849442e5f5e404d7cb661
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434580"
---
>[!NOTE]
><span data-ttu-id="23d6c-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="23d6c-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="23d6c-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="23d6c-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="23d6c-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="23d6c-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="23d6c-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="23d6c-108">Es wurde [eine neue Reihe von Tutorials](mrlearning-base.md) für hololens 2 gepostet.</span><span class="sxs-lookup"><span data-stu-id="23d6c-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-spatial-230-spatial-mapping"></a><span data-ttu-id="23d6c-109">Räumliche Daten 230: räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="23d6c-109">MR Spatial 230: Spatial mapping</span></span>

<span data-ttu-id="23d6c-110">[Räumliche Zuordnung](spatial-mapping.md) kombiniert die reale und die virtuelle Welt zusammen, indem Hologramme über die Umgebung vermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="23d6c-110">[Spatial mapping](spatial-mapping.md) combines the real world and virtual world together by teaching holograms about the environment.</span></span> <span data-ttu-id="23d6c-111">Im räumlichen 230 (Project Planetarium) erfahren Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="23d6c-111">In MR Spatial 230 (Project Planetarium) we'll learn how to:</span></span>

* <span data-ttu-id="23d6c-112">Scannen Sie die Umgebung, und übertragen Sie Daten aus den hololens auf den Entwicklungs Computer.</span><span class="sxs-lookup"><span data-stu-id="23d6c-112">Scan the environment and transfer data from the HoloLens to your development machine.</span></span>
* <span data-ttu-id="23d6c-113">Entdecken Sie Shader, und erfahren Sie, wie Sie Sie zum Visualisieren Ihres Speicherplatzes verwenden können.</span><span class="sxs-lookup"><span data-stu-id="23d6c-113">Explore shaders and learn how to use them for visualizing your space.</span></span>
* <span data-ttu-id="23d6c-114">Unterbrechen Sie das Raum Netz mithilfe der Mesh-Verarbeitung in einfache Ebenen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-114">Break down the room mesh into simple planes using mesh processing.</span></span>
* <span data-ttu-id="23d6c-115">Gehen Sie über die in den [Grundlagen 101](holograms-101.md)erlernten Platzierungs Techniken hinaus, und geben Sie Feedback darüber an, wo ein – Hologramm in der Umgebung platziert werden kann.</span><span class="sxs-lookup"><span data-stu-id="23d6c-115">Go beyond the placement techniques we learned in [MR Basics 101](holograms-101.md), and provide feedback about where a hologram can be placed in the environment.</span></span>
* <span data-ttu-id="23d6c-116">Entdecken Sie die Auswirkungen auf die Okklusion. wenn sich Ihr – Hologramm hinter einem realen Objekt befindet, können Sie es dennoch mit der x-ray-Vision sehen!</span><span class="sxs-lookup"><span data-stu-id="23d6c-116">Explore occlusion effects, so when your hologram is behind a real-world object, you can still see it with x-ray vision!</span></span>

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a><span data-ttu-id="23d6c-117">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="23d6c-117">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="23d6c-118">Natürlich</span><span class="sxs-lookup"><span data-stu-id="23d6c-118">Course</span></span></th><th style="width:150px"> <span data-ttu-id="23d6c-119"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="23d6c-119"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="23d6c-120"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="23d6c-120"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="23d6c-121">Räumliche Daten 230: räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="23d6c-121">MR Spatial 230: Spatial mapping</span></span></td><td style="text-align: center;"> <span data-ttu-id="23d6c-122">✔️</span><span class="sxs-lookup"><span data-stu-id="23d6c-122">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="23d6c-123">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="23d6c-123">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="23d6c-124">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="23d6c-124">Prerequisites</span></span>

* <span data-ttu-id="23d6c-125">Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md)konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="23d6c-125">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="23d6c-126">Einige Grund C# Legende Programmiermöglichkeiten.</span><span class="sxs-lookup"><span data-stu-id="23d6c-126">Some basic C# programming ability.</span></span>
* <span data-ttu-id="23d6c-127">Sie sollten die [Grundlagen von 101](holograms-101.md)abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="23d6c-127">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="23d6c-128">Ein hololens-Gerät, das [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode)ist.</span><span class="sxs-lookup"><span data-stu-id="23d6c-128">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="23d6c-129">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="23d6c-129">Project files</span></span>

* <span data-ttu-id="23d6c-130">Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) , die für das Projekt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="23d6c-130">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) required by the project.</span></span><span data-ttu-id="23d6c-131"> Erfordert Unity 2017,2 oder höher.</span><span class="sxs-lookup"><span data-stu-id="23d6c-131"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="23d6c-132">Wenn Sie weiterhin Unity 5,6-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span><span class="sxs-lookup"><span data-stu-id="23d6c-132">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span></span>
  * <span data-ttu-id="23d6c-133">Wenn Sie weiterhin Unity 5,5-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span><span class="sxs-lookup"><span data-stu-id="23d6c-133">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span></span>
  * <span data-ttu-id="23d6c-134">Wenn Sie weiterhin Unity 5,4-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span><span class="sxs-lookup"><span data-stu-id="23d6c-134">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span></span>
* <span data-ttu-id="23d6c-135">Deinstallieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht zugänglichen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="23d6c-135">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="23d6c-136">Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span><span class="sxs-lookup"><span data-stu-id="23d6c-136">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span></span>

### <a name="notes"></a><span data-ttu-id="23d6c-137">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="23d6c-137">Notes</span></span>

* <span data-ttu-id="23d6c-138">"Enable nur eigenen Code" muss in Visual Studio unter Extras > Optionen > Debuggen*deaktiviert (deaktiviert*) werden, um Breakpoints im Code zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-138">"Enable Just My Code" in Visual Studio needs to be disabled (*unchecked*) under Tools > Options > Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="23d6c-139">Unity-Setup</span><span class="sxs-lookup"><span data-stu-id="23d6c-139">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* <span data-ttu-id="23d6c-140">Starten Sie **Unity**.</span><span class="sxs-lookup"><span data-stu-id="23d6c-140">Start **Unity**.</span></span>
* <span data-ttu-id="23d6c-141">Wählen Sie **neu** aus, um ein neues Projekt zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-141">Select **New** to create a new project.</span></span>
* <span data-ttu-id="23d6c-142">Nennen Sie das Projekt **Planetarium**.</span><span class="sxs-lookup"><span data-stu-id="23d6c-142">Name the project **Planetarium**.</span></span>
* <span data-ttu-id="23d6c-143">Überprüfen Sie, ob die Einstellung **3D** ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="23d6c-143">Verify that the **3D** setting is selected.</span></span>
* <span data-ttu-id="23d6c-144">Klicken Sie auf **Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="23d6c-144">Click **Create Project**.</span></span>
* <span data-ttu-id="23d6c-145">Nachdem Unity gestartet wurde, wechseln Sie zu **Edit > Project Settings > Player**.</span><span class="sxs-lookup"><span data-stu-id="23d6c-145">Once Unity launches, go to **Edit > Project Settings > Player**.</span></span>
* <span data-ttu-id="23d6c-146">Suchen Sie im **Inspektor** -Panel nach dem grünen **Windows Store** -Symbol, und wählen Sie es aus.</span><span class="sxs-lookup"><span data-stu-id="23d6c-146">In the **Inspector** panel, find and select the green **Windows Store** icon.</span></span>
* <span data-ttu-id="23d6c-147">Erweitern Sie **andere Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="23d6c-147">Expand **Other Settings**.</span></span>
* <span data-ttu-id="23d6c-148">Aktivieren Sie im Abschnitt " **Rendering** " die Option " **Virtual Reality supported** ".</span><span class="sxs-lookup"><span data-stu-id="23d6c-148">In the **Rendering** section, check the **Virtual Reality Supported** option.</span></span>
* <span data-ttu-id="23d6c-149">Vergewissern Sie sich, dass **Windows Holographic** in der Liste der **Virtual Reality sdert**angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="23d6c-149">Verify that **Windows Holographic** appears in the list of **Virtual Reality SDKs**.</span></span> <span data-ttu-id="23d6c-150">Wenn dies nicht der Grund ist, wählen Sie die Schaltfläche **+** unten in der Liste aus, und wählen Sie **Windows Holographic**aus.</span><span class="sxs-lookup"><span data-stu-id="23d6c-150">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>
* <span data-ttu-id="23d6c-151">Erweitern Sie **Veröffentlichungs Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="23d6c-151">Expand **Publishing Settings**.</span></span>
* <span data-ttu-id="23d6c-152">Überprüfen Sie im Abschnitt **Funktionen** die folgenden Einstellungen:</span><span class="sxs-lookup"><span data-stu-id="23d6c-152">In the **Capabilities** section, check the following settings:</span></span>
    * <span data-ttu-id="23d6c-153">Internetclientserver</span><span class="sxs-lookup"><span data-stu-id="23d6c-153">InternetClientServer</span></span>
    * <span data-ttu-id="23d6c-154">Privatenetworkclientserver</span><span class="sxs-lookup"><span data-stu-id="23d6c-154">PrivateNetworkClientServer</span></span>
    * <span data-ttu-id="23d6c-155">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="23d6c-155">Microphone</span></span>
    * <span data-ttu-id="23d6c-156">Spatialperception</span><span class="sxs-lookup"><span data-stu-id="23d6c-156">SpatialPerception</span></span>
* <span data-ttu-id="23d6c-157">Wechseln Sie zu **Edit > Project Settings > Quality**</span><span class="sxs-lookup"><span data-stu-id="23d6c-157">Go to **Edit > Project Settings > Quality**</span></span>
* <span data-ttu-id="23d6c-158">Wählen Sie im **Inspektor** -Panel unter dem Windows Store-Symbol den schwarzen Dropdown Pfeil unter der Zeile "Default" aus, und ändern Sie die Standardeinstellung in **sehr niedrig**.</span><span class="sxs-lookup"><span data-stu-id="23d6c-158">In the **Inspector** panel, under the Windows Store icon, select the black drop-down arrow under the 'Default' row and change the default setting to **Very Low**.</span></span>
* <span data-ttu-id="23d6c-159">Wechseln Sie zu **Assets > Importieren Sie das Paket > benutzerdefiniertes Paket**.</span><span class="sxs-lookup"><span data-stu-id="23d6c-159">Go to **Assets > Import Package > Custom Package**.</span></span>
* <span data-ttu-id="23d6c-160">Navigieren Sie zum Ordner " **. ..\holographicacademy-holograms-230-spatialmapping\starting** ".</span><span class="sxs-lookup"><span data-stu-id="23d6c-160">Navigate to the **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** folder.</span></span>
* <span data-ttu-id="23d6c-161">Klicken Sie auf " **Planetarium. unitypackage**".</span><span class="sxs-lookup"><span data-stu-id="23d6c-161">Click on **Planetarium.unitypackage**.</span></span>
* <span data-ttu-id="23d6c-162">Klicken Sie auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="23d6c-162">Click **Open**.</span></span>
* <span data-ttu-id="23d6c-163">Ein Fenster zum **Importieren von Unity-Paketen** sollte angezeigt werden. Klicken Sie auf die Schaltfläche **importieren** .</span><span class="sxs-lookup"><span data-stu-id="23d6c-163">An **Import Unity Package** window should appear, click on the **Import** button.</span></span>
* <span data-ttu-id="23d6c-164">Warten Sie, bis Unity alle Assets importiert, die wir benötigen, um dieses Projekt abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-164">Wait for Unity to import all of the assets that we will need to complete this project.</span></span>
* <span data-ttu-id="23d6c-165">Löschen Sie im **Hierarchie** Panel die **Hauptkamera**.</span><span class="sxs-lookup"><span data-stu-id="23d6c-165">In the **Hierarchy** panel, delete the **Main Camera**.</span></span>
* <span data-ttu-id="23d6c-166">Suchen Sie im **Projekt** Panel im Ordner **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** das **Hauptkamera** Objekt.</span><span class="sxs-lookup"><span data-stu-id="23d6c-166">In the **Project** panel, **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** folder, find the **Main Camera** object.</span></span>
* <span data-ttu-id="23d6c-167">Ziehen Sie die **Hauptkamera** -vorfab per Drag & Drop in den Bereich **Hierarchie** .</span><span class="sxs-lookup"><span data-stu-id="23d6c-167">Drag and drop the **Main Camera** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="23d6c-168">Löschen Sie im **Hierarchie** Panel das **direktionale Light** -Objekt.</span><span class="sxs-lookup"><span data-stu-id="23d6c-168">In the **Hierarchy** panel, delete the **Directional Light** object.</span></span>
* <span data-ttu-id="23d6c-169">Suchen Sie im **Projekt** Panel im Ordner **holograms** das **Cursor** Objekt.</span><span class="sxs-lookup"><span data-stu-id="23d6c-169">In the **Project** panel, **Holograms** folder, locate the **Cursor** object.</span></span>
* <span data-ttu-id="23d6c-170">Ziehen Sie & den **Cursor** vorfab in der **Hierarchie**ablegen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-170">Drag & drop the **Cursor** prefab into the **Hierarchy**.</span></span>
* <span data-ttu-id="23d6c-171">Wählen Sie im Bereich **Hierarchie** das **Cursor** Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="23d6c-171">In the **Hierarchy** panel, select the **Cursor** object.</span></span>
* <span data-ttu-id="23d6c-172">Klicken Sie im **Inspektor** -Panel auf die Dropdown Liste **Ebene** , und wählen Sie **Ebenen bearbeiten...** aus.</span><span class="sxs-lookup"><span data-stu-id="23d6c-172">In the **Inspector** panel, click the **Layer** drop-down and select **Edit Layers...**.</span></span>
* <span data-ttu-id="23d6c-173">Benennen Sie die **Benutzerebene 31** als "**spatialmapping**".</span><span class="sxs-lookup"><span data-stu-id="23d6c-173">Name **User Layer 31** as "**SpatialMapping**".</span></span>
* <span data-ttu-id="23d6c-174">Speichern Sie die neue Szene: **File > Szene speichern unter...**</span><span class="sxs-lookup"><span data-stu-id="23d6c-174">Save the new scene: **File > Save Scene As...**</span></span>
* <span data-ttu-id="23d6c-175">Klicken Sie auf **neuer Ordner** , und benennen Sie die Ordner **Szenen**.</span><span class="sxs-lookup"><span data-stu-id="23d6c-175">Click **New Folder** and name the folder **Scenes**.</span></span>
* <span data-ttu-id="23d6c-176">Benennen Sie die Datei "**Planetarium**", und speichern Sie Sie im Ordner **Szenen** .</span><span class="sxs-lookup"><span data-stu-id="23d6c-176">Name the file "**Planetarium**" and save it in the **Scenes** folder.</span></span>

## <a name="chapter-1---scanning"></a><span data-ttu-id="23d6c-177">Kapitel 1: Scannen</span><span class="sxs-lookup"><span data-stu-id="23d6c-177">Chapter 1 - Scanning</span></span>

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

<span data-ttu-id="23d6c-178">**Ziele**</span><span class="sxs-lookup"><span data-stu-id="23d6c-178">**Objectives**</span></span>

* <span data-ttu-id="23d6c-179">Erfahren Sie mehr über den surfaceobserver und wie sich seine Einstellungen auf die Leistung und Leistung auswirken.</span><span class="sxs-lookup"><span data-stu-id="23d6c-179">Learn about the SurfaceObserver and how its settings impact experience and performance.</span></span>
* <span data-ttu-id="23d6c-180">Erstellen Sie eine Raum Überprüfung, um die Netze Ihres Raums zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-180">Create a room scanning experience to collect the meshes of your room.</span></span>

<span data-ttu-id="23d6c-181">**Anweisungen**</span><span class="sxs-lookup"><span data-stu-id="23d6c-181">**Instructions**</span></span>

* <span data-ttu-id="23d6c-182">Suchen Sie im Ordner " **Projekt** Panel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** " nach der **spatialmapping** -vorfab.</span><span class="sxs-lookup"><span data-stu-id="23d6c-182">In the **Project** panel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** folder, find the **SpatialMapping** prefab.</span></span>
* <span data-ttu-id="23d6c-183">Ziehen Sie & ziehen Sie die vorfab **spatialmapping** in den Bereich **Hierarchie** .</span><span class="sxs-lookup"><span data-stu-id="23d6c-183">Drag & drop the **SpatialMapping** prefab into the **Hierarchy** panel.</span></span>

<span data-ttu-id="23d6c-184">**Build und Bereitstellung (Teil 1)**</span><span class="sxs-lookup"><span data-stu-id="23d6c-184">**Build and Deploy (part 1)**</span></span>

* <span data-ttu-id="23d6c-185">Wählen Sie in Unity **Datei > Buildeinstellungen**aus.</span><span class="sxs-lookup"><span data-stu-id="23d6c-185">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="23d6c-186">Klicken Sie auf **offene Szenen hinzufügen** , um dem Build die **Planetarium** -Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-186">Click **Add Open Scenes** to add the **Planetarium** scene to the build.</span></span>
* <span data-ttu-id="23d6c-187">Wählen Sie in der Liste **Plattform** **universelle Windows-Plattform** aus, und klicken Sie auf **Plattform wechseln**.</span><span class="sxs-lookup"><span data-stu-id="23d6c-187">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="23d6c-188">Legen Sie **SDK** auf **Universal 10** und **UWP Build Type** auf **D3D**fest.</span><span class="sxs-lookup"><span data-stu-id="23d6c-188">Set **SDK** to **Universal 10** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="23d6c-189">Überprüfen Sie **Unity C# -Projekte**.</span><span class="sxs-lookup"><span data-stu-id="23d6c-189">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="23d6c-190">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="23d6c-190">Click **Build**.</span></span>
* <span data-ttu-id="23d6c-191">Erstellen Sie einen **neuen Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="23d6c-191">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="23d6c-192">Klicken Sie einfach auf den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="23d6c-192">Single click the **App** folder.</span></span>
* <span data-ttu-id="23d6c-193">Klicken Sie auf die Schaltfläche **Ordner auswählen** .</span><span class="sxs-lookup"><span data-stu-id="23d6c-193">Press the **Select Folder** button.</span></span>
* <span data-ttu-id="23d6c-194">Wenn Unity erstellt wurde, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="23d6c-194">When Unity is done building, a File Explorer window will appear.</span></span>
* <span data-ttu-id="23d6c-195">Doppelklicken Sie auf den **App** -Ordner, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-195">Double-click on the **App** folder to open it.</span></span>
* <span data-ttu-id="23d6c-196">Doppelklicken Sie auf " **Planetarium. sln** ", um das Projekt in Visual Studio zu laden.</span><span class="sxs-lookup"><span data-stu-id="23d6c-196">Double-click on **Planetarium.sln** to load the project in Visual Studio.</span></span>
* <span data-ttu-id="23d6c-197">Verwenden Sie in Visual Studio die obere Symbolleiste, um die Konfiguration in **Release**zu ändern.</span><span class="sxs-lookup"><span data-stu-id="23d6c-197">In Visual Studio, use the top toolbar to change the Configuration to **Release**.</span></span>
* <span data-ttu-id="23d6c-198">Ändern Sie die Plattform in **x86**.</span><span class="sxs-lookup"><span data-stu-id="23d6c-198">Change the Platform to **x86**.</span></span>
* <span data-ttu-id="23d6c-199">Klicken Sie auf den Dropdown Pfeil rechts neben "lokaler Computer", und wählen Sie **Remote Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="23d6c-199">Click on the drop-down arrow to the right of 'Local Machine', and select **Remote Machine**.</span></span>
* <span data-ttu-id="23d6c-200">Geben Sie die [IP-Adresse Ihres Geräts](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) in das Adressfeld ein, und ändern Sie den Authentifizierungsmodus in **Universal (unverschlüsseltes Protokoll)** .</span><span class="sxs-lookup"><span data-stu-id="23d6c-200">Enter [your device's IP address](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) in the Address field and change Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span>
* <span data-ttu-id="23d6c-201">Klicken Sie auf **Debuggen > Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="23d6c-201">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="23d6c-202">Sehen Sie sich den **Ausgabe** Bereich in Visual Studio zum Erstellen und Bereitstellen des Status an.</span><span class="sxs-lookup"><span data-stu-id="23d6c-202">Watch the **Output** panel in Visual Studio for build and deploy status.</span></span>
* <span data-ttu-id="23d6c-203">Nachdem Ihre APP bereitgestellt wurde, durchlaufen Sie den Raum.</span><span class="sxs-lookup"><span data-stu-id="23d6c-203">Once your app has deployed, walk around the room.</span></span> <span data-ttu-id="23d6c-204">Sie sehen die umgebenden Oberflächen, die durch schwarze und weiße Draht Modell-Meshes abgedeckt werden.</span><span class="sxs-lookup"><span data-stu-id="23d6c-204">You will see the surrounding surfaces covered by black and white wireframe meshes.</span></span>
* <span data-ttu-id="23d6c-205">Überprüfen Sie Ihre Umgebung.</span><span class="sxs-lookup"><span data-stu-id="23d6c-205">Scan your surroundings.</span></span> <span data-ttu-id="23d6c-206">Achten Sie darauf, Wände, Oberflächen und Fußböden zu betrachten.</span><span class="sxs-lookup"><span data-stu-id="23d6c-206">Be sure to look at walls, ceilings, and floors.</span></span>

<span data-ttu-id="23d6c-207">**Erstellen und bereitstellen (Teil 2)**</span><span class="sxs-lookup"><span data-stu-id="23d6c-207">**Build and Deploy (part 2)**</span></span>

<span data-ttu-id="23d6c-208">Betrachten wir nun, wie sich die räumliche Zuordnung auf die Leistung auswirken kann.</span><span class="sxs-lookup"><span data-stu-id="23d6c-208">Now let's explore how Spatial Mapping can affect performance.</span></span>

* <span data-ttu-id="23d6c-209">Wählen Sie in Unity **Fenster > Profiler**aus.</span><span class="sxs-lookup"><span data-stu-id="23d6c-209">In Unity, select **Window > Profiler**.</span></span>
* <span data-ttu-id="23d6c-210">Klicken Sie auf **Profiler > GPU hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="23d6c-210">Click **Add Profiler > GPU**.</span></span>
* <span data-ttu-id="23d6c-211">Klicken Sie auf **Active Profiler > <Enter IP>** .</span><span class="sxs-lookup"><span data-stu-id="23d6c-211">Click **Active Profiler > <Enter IP>**.</span></span>
* <span data-ttu-id="23d6c-212">Geben Sie die **IP-Adresse** der hololens ein.</span><span class="sxs-lookup"><span data-stu-id="23d6c-212">Enter the **IP address** of your HoloLens.</span></span>
* <span data-ttu-id="23d6c-213">Klicken Sie auf **Verbinden**.</span><span class="sxs-lookup"><span data-stu-id="23d6c-213">Click **Connect**.</span></span>
* <span data-ttu-id="23d6c-214">Beachten Sie die Anzahl der Millisekunden, die die GPU zum Rendering eines Frames benötigt.</span><span class="sxs-lookup"><span data-stu-id="23d6c-214">Observe the number of milliseconds it takes for the GPU to render a frame.</span></span>
* <span data-ttu-id="23d6c-215">Verhindern, dass die Anwendung auf dem Gerät ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="23d6c-215">Stop the application from running on the device.</span></span>
* <span data-ttu-id="23d6c-216">Kehren Sie zu Visual Studio zurück, und öffnen Sie **SpatialMappingObserver.cs**.</span><span class="sxs-lookup"><span data-stu-id="23d6c-216">Return to Visual Studio and open **SpatialMappingObserver.cs**.</span></span> <span data-ttu-id="23d6c-217">Sie finden ihn im Ordner "holotoolkit\spatialmapping" des Projekts "Assembly-CSharp" (Universal Windows).</span><span class="sxs-lookup"><span data-stu-id="23d6c-217">You will find it in the HoloToolkit\SpatialMapping folder of the Assembly-CSharp (Universal Windows) project.</span></span>
* <span data-ttu-id="23d6c-218">Suchen Sie die Funktion " **Awa()** ", und fügen Sie die folgende Codezeile hinzu: " **testanglespercubicmeter = 1200;** "</span><span class="sxs-lookup"><span data-stu-id="23d6c-218">Find the **Awake()** function, and add the following line of code: **TrianglesPerCubicMeter = 1200;**</span></span>
* <span data-ttu-id="23d6c-219">Stellen Sie das Projekt erneut auf Ihrem Gerät bereit, und stellen Sie dann **erneut eine Verbindung mit dem Profiler**her.</span><span class="sxs-lookup"><span data-stu-id="23d6c-219">Re-deploy the project to your device, and then **reconnect the profiler**.</span></span> <span data-ttu-id="23d6c-220">Beachten Sie die Änderung in der Anzahl von Millisekunden zum Rendering eines Frames.</span><span class="sxs-lookup"><span data-stu-id="23d6c-220">Observe the change in the number of milliseconds to render a frame.</span></span>
* <span data-ttu-id="23d6c-221">Verhindern, dass die Anwendung auf dem Gerät ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="23d6c-221">Stop the application from running on the device.</span></span>

<span data-ttu-id="23d6c-222">**Speichern und laden in Unity**</span><span class="sxs-lookup"><span data-stu-id="23d6c-222">**Save and load in Unity**</span></span>

<span data-ttu-id="23d6c-223">Schließlich speichere ich unser Raum Netz und lade es in Unity.</span><span class="sxs-lookup"><span data-stu-id="23d6c-223">Finally, let's save our room mesh and load it into Unity.</span></span>

* <span data-ttu-id="23d6c-224">Kehren Sie zu Visual Studio zurück, und entfernen Sie die Zeile " **tranglespercubicmeter** ", die Sie in der Funktion " **Awa()** " im vorherigen Abschnitt hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="23d6c-224">Return to Visual Studio and remove the **TrianglesPerCubicMeter** line that you added in the **Awake()** function during the previous section.</span></span>
* <span data-ttu-id="23d6c-225">Stellen Sie das Projekt erneut auf Ihrem Gerät bereit.</span><span class="sxs-lookup"><span data-stu-id="23d6c-225">Redeploy the project to your device.</span></span> <span data-ttu-id="23d6c-226">Wir sollten nun mit **500** Dreiecke pro Kubikmeter ausführen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-226">We should now be running with **500** triangles per cubic meter.</span></span>
* <span data-ttu-id="23d6c-227">Öffnen Sie einen Browser, und geben Sie die IP-Adresse des hololens ein, um zum **Windows-Geräte Portal**zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="23d6c-227">Open a browser and enter in your HoloLens IPAddress to navigate to the **Windows Device Portal**.</span></span>
* <span data-ttu-id="23d6c-228">Wählen Sie die Option **3D-Ansicht** im linken Bereich aus.</span><span class="sxs-lookup"><span data-stu-id="23d6c-228">Select the **3D View** option in the left panel.</span></span>
* <span data-ttu-id="23d6c-229">Klicken Sie unter **Oberflächen wieder** Herstellung auf die Schaltfläche **Aktualisieren** .</span><span class="sxs-lookup"><span data-stu-id="23d6c-229">Under **Surface reconstruction** select the **Update** button.</span></span>
* <span data-ttu-id="23d6c-230">Sehen Sie sich an, wie die Bereiche, die Sie auf den hololens überprüft haben, im Anzeige Fenster angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="23d6c-230">Watch as the areas that you have scanned on your HoloLens appear in the display window.</span></span>
* <span data-ttu-id="23d6c-231">Zum Speichern des Raum Scans klicken Sie auf die Schaltfläche **Speichern** .</span><span class="sxs-lookup"><span data-stu-id="23d6c-231">To save your room scan, press the **Save** button.</span></span>
* <span data-ttu-id="23d6c-232">Öffnen Sie den Ordner " **Downloads** ", um das gespeicherte Raummodell " **srmesh. obj**" zu finden.</span><span class="sxs-lookup"><span data-stu-id="23d6c-232">Open your **Downloads** folder to find the saved room model **SRMesh.obj**.</span></span>
* <span data-ttu-id="23d6c-233">Kopieren Sie " **srmesh. obj** " in den Ordner " **Assets** " Ihres Unity-Projekts.</span><span class="sxs-lookup"><span data-stu-id="23d6c-233">Copy **SRMesh.obj** to the **Assets** folder of your Unity project.</span></span>
* <span data-ttu-id="23d6c-234">Wählen Sie in Unity das **spatialmapping** -Objekt im **Hierarchie** Panel aus.</span><span class="sxs-lookup"><span data-stu-id="23d6c-234">In Unity, select the **SpatialMapping** object in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="23d6c-235">Suchen Sie die Komponente **Objekt Oberflächen Beobachter (Skript)** .</span><span class="sxs-lookup"><span data-stu-id="23d6c-235">Locate the **Object Surface Observer (Script)** component.</span></span>
* <span data-ttu-id="23d6c-236">Klicken Sie auf den Kreis rechts neben der Eigenschaft **Raummodell** .</span><span class="sxs-lookup"><span data-stu-id="23d6c-236">Click the circle to the right of the **Room Model** property.</span></span>
* <span data-ttu-id="23d6c-237">Suchen und wählen Sie das **srmesh** -Objekt aus, und schließen Sie das Fenster.</span><span class="sxs-lookup"><span data-stu-id="23d6c-237">Find and select the **SRMesh** object and then close the window.</span></span>
* <span data-ttu-id="23d6c-238">Vergewissern Sie sich, dass die Eigenschaft **Raummodell** im **Inspektor** -Panel nun auf **srmesh**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="23d6c-238">Verify that the **Room Model** property in the **Inspector** panel is now set to **SRMesh**.</span></span>
* <span data-ttu-id="23d6c-239">Drücken Sie die **Wiedergabe** Schaltfläche, um den Vorschaumodus von Unity einzugeben.</span><span class="sxs-lookup"><span data-stu-id="23d6c-239">Press the **Play** button to enter Unity's preview mode.</span></span>
* <span data-ttu-id="23d6c-240">Die spatialmapping-Komponente lädt die Netzen aus dem gespeicherten Raummodell, sodass Sie Sie in Unity verwenden können.</span><span class="sxs-lookup"><span data-stu-id="23d6c-240">The SpatialMapping component will load the meshes from the saved room model so you can use them in Unity.</span></span>
* <span data-ttu-id="23d6c-241">Wechseln Sie zur Ansicht **Szene** , um das gesamte mit dem Draht Modell-Shader angezeigte Raummodell anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-241">Switch to **Scene** view to see all of your room model displayed with the wireframe shader.</span></span>
* <span data-ttu-id="23d6c-242">Drücken Sie erneut die **Wiedergabe** Schaltfläche, um den Vorschaumodus zu beenden</span><span class="sxs-lookup"><span data-stu-id="23d6c-242">Press the **Play** button again to exit preview mode.</span></span>

<span data-ttu-id="23d6c-243">**Hinweis:** Wenn Sie das nächste Mal in Unity in den Vorschaumodus wechseln, wird das gespeicherte Raum Netz standardmäßig geladen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-243">**NOTE:** The next time that you enter preview mode in Unity, it will load the saved room mesh by default.</span></span>

## <a name="chapter-2---visualization"></a><span data-ttu-id="23d6c-244">Kapitel 2: Visualisierung</span><span class="sxs-lookup"><span data-stu-id="23d6c-244">Chapter 2 - Visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

<span data-ttu-id="23d6c-245">**Ziele**</span><span class="sxs-lookup"><span data-stu-id="23d6c-245">**Objectives**</span></span>

* <span data-ttu-id="23d6c-246">Erfahren Sie mehr über die Grundlagen von Shaders.</span><span class="sxs-lookup"><span data-stu-id="23d6c-246">Learn the basics of shaders.</span></span>
* <span data-ttu-id="23d6c-247">Visualisieren Sie Ihre Umgebung.</span><span class="sxs-lookup"><span data-stu-id="23d6c-247">Visualize your surroundings.</span></span>

<span data-ttu-id="23d6c-248">**Anweisungen**</span><span class="sxs-lookup"><span data-stu-id="23d6c-248">**Instructions**</span></span>

* <span data-ttu-id="23d6c-249">Wählen Sie im Bereich **Hierarchie** der Unity das **spatialmapping** -Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="23d6c-249">In Unity's **Hierarchy** panel, select the **SpatialMapping** object.</span></span>
* <span data-ttu-id="23d6c-250">Suchen Sie im **Inspektor** -Panel die Komponente **räumlicher zuordnungsmanager (Skript)** .</span><span class="sxs-lookup"><span data-stu-id="23d6c-250">In the **Inspector** panel, find the **Spatial Mapping Manager (Script)** component.</span></span>
* <span data-ttu-id="23d6c-251">Klicken Sie auf den Kreis rechts neben der Eigenschaft **Oberflächen Material** .</span><span class="sxs-lookup"><span data-stu-id="23d6c-251">Click the circle to the right of the **Surface Material** property.</span></span>
* <span data-ttu-id="23d6c-252">Suchen und wählen Sie das Material **bluelinesonwalls** aus, und schließen Sie das Fenster.</span><span class="sxs-lookup"><span data-stu-id="23d6c-252">Find and select the **BlueLinesOnWalls** material and close the window.</span></span>
* <span data-ttu-id="23d6c-253">Doppelklicken Sie im **Projekt** Panel Ordner **Shaders** auf **bluelinesonwalls** , um den Shader in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-253">In the **Project** panel **Shaders** folder, double-click on **BlueLinesOnWalls** to open the shader in Visual Studio.</span></span>
* <span data-ttu-id="23d6c-254">Dies ist ein einfacher Pixel-Shader (Vertex zu Fragment), der die folgenden Aufgaben durchführt:</span><span class="sxs-lookup"><span data-stu-id="23d6c-254">This is a simple pixel (vertex to fragment) shader, which accomplishes the following tasks:</span></span>
    1. <span data-ttu-id="23d6c-255">Konvertiert den Speicherort eines Scheitel Punkts in den Raum.</span><span class="sxs-lookup"><span data-stu-id="23d6c-255">Converts a vertex's location to world space.</span></span>
    2. <span data-ttu-id="23d6c-256">Überprüft den normalen Scheitelpunkt, um zu bestimmen, ob ein Pixel vertikal ist.</span><span class="sxs-lookup"><span data-stu-id="23d6c-256">Checks the vertex's normal to determine if a pixel is vertical.</span></span>
    3. <span data-ttu-id="23d6c-257">Legt die Farbe des Pixels zum Rendern fest.</span><span class="sxs-lookup"><span data-stu-id="23d6c-257">Sets the color of the pixel for rendering.</span></span>

<span data-ttu-id="23d6c-258">**Erstellen und bereitstellen**</span><span class="sxs-lookup"><span data-stu-id="23d6c-258">**Build and Deploy**</span></span>

* <span data-ttu-id="23d6c-259">Kehren Sie zu Unity zurück, und drücken Sie die **Wiedergabe** Taste, um den Vorschau</span><span class="sxs-lookup"><span data-stu-id="23d6c-259">Return to Unity and press **Play** to enter preview mode.</span></span>
* <span data-ttu-id="23d6c-260">Blaue Linien werden auf allen vertikalen Oberflächen des Raum Netzes gerendert (das automatisch aus den gespeicherten Scandaten geladen wird).</span><span class="sxs-lookup"><span data-stu-id="23d6c-260">Blue lines will be rendered on all vertical surfaces of the room mesh (which automatically loaded from our saved scanning data).</span></span>
* <span data-ttu-id="23d6c-261">Wechseln Sie zur Registerkarte **Szene** , um die Ansicht des Raums anzupassen und zu sehen, wie das gesamte Raum Netz in Unity angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="23d6c-261">Switch to the **Scene** tab to adjust your view of the room and see how the entire room mesh appears in Unity.</span></span>
* <span data-ttu-id="23d6c-262">Suchen Sie im **Projekt** Panel den Ordner **Material** , und wählen Sie das Material **bluelinesonwalls** aus.</span><span class="sxs-lookup"><span data-stu-id="23d6c-262">In the **Project** panel, find the **Materials** folder and select the **BlueLinesOnWalls** material.</span></span>
* <span data-ttu-id="23d6c-263">Ändern Sie einige Eigenschaften, und sehen Sie, wie die Änderungen im Unity-Editor angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="23d6c-263">Modify some properties and see how the changes appear in the Unity editor.</span></span>
    * <span data-ttu-id="23d6c-264">Passen Sie im **Inspektor** -Panel den **linescale** -Wert an, damit die Linien dicker oder dünner angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="23d6c-264">In the **Inspector** panel, adjust the **LineScale** value to make the lines appear thicker or thinner.</span></span>
    * <span data-ttu-id="23d6c-265">Passen Sie im **Inspektor** -Panel den Wert von **linespermeter** an, um zu ändern, wie viele Zeilen auf jeder Wand angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="23d6c-265">In the **Inspector** panel, adjust the **LinesPerMeter** value to change how many lines appear on each wall.</span></span>
* <span data-ttu-id="23d6c-266">Klicken Sie erneut auf **abspielen** , um den Vorschaumodus zu beenden</span><span class="sxs-lookup"><span data-stu-id="23d6c-266">Click **Play** again to exit preview mode.</span></span>
* <span data-ttu-id="23d6c-267">Erstellen Sie die hololens und stellen Sie Sie bereit, und beobachten Sie, wie das Shader-Rendering auf realen Oberflächen erscheint.</span><span class="sxs-lookup"><span data-stu-id="23d6c-267">Build and deploy to the HoloLens and observe how the shader rendering appears on real surfaces.</span></span>

<span data-ttu-id="23d6c-268">Unity bietet eine hervorragende Vorschau der Materialien, aber es ist immer eine gute Idee, das Rendering im Gerät auszuchecken.</span><span class="sxs-lookup"><span data-stu-id="23d6c-268">Unity does a great job of previewing materials, but it's always a good idea to check-out rendering in the device.</span></span>

## <a name="chapter-3---processing"></a><span data-ttu-id="23d6c-269">Kapitel 3: verarbeiten</span><span class="sxs-lookup"><span data-stu-id="23d6c-269">Chapter 3 - Processing</span></span>

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

<span data-ttu-id="23d6c-270">**Ziele**</span><span class="sxs-lookup"><span data-stu-id="23d6c-270">**Objectives**</span></span>

* <span data-ttu-id="23d6c-271">Erlernen Sie Techniken zum Verarbeiten räumlicher Mapping-Daten für die Verwendung in Ihrer Anwendung.</span><span class="sxs-lookup"><span data-stu-id="23d6c-271">Learn techniques to process spatial mapping data for use in your application.</span></span>
* <span data-ttu-id="23d6c-272">Analysieren räumlicher Zuordnungsdaten zum Suchen von Ebenen und Entfernen von Dreiecken</span><span class="sxs-lookup"><span data-stu-id="23d6c-272">Analyze spatial mapping data to find planes and remove triangles.</span></span>
* <span data-ttu-id="23d6c-273">Verwenden Sie für die – Hologramm-Platzierung Flächen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-273">Use planes for hologram placement.</span></span>

<span data-ttu-id="23d6c-274">**Anweisungen**</span><span class="sxs-lookup"><span data-stu-id="23d6c-274">**Instructions**</span></span>

* <span data-ttu-id="23d6c-275">Suchen Sie im **Projekt** Panel von Unity im Ordner **holograms** das **spatialprocessing** -Objekt.</span><span class="sxs-lookup"><span data-stu-id="23d6c-275">In Unity's **Project** panel, **Holograms** folder, find the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="23d6c-276">Ziehen Sie & das **spatialprocessing** -Objekt in den Bereich **Hierarchie** ablegen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-276">Drag & drop the **SpatialProcessing** object into the **Hierarchy** panel.</span></span>

<span data-ttu-id="23d6c-277">Das spatialprocessing-präfab umfasst Komponenten für die Verarbeitung der räumlichen Zuordnungsdaten.</span><span class="sxs-lookup"><span data-stu-id="23d6c-277">The SpatialProcessing prefab includes components for processing the spatial mapping data.</span></span> <span data-ttu-id="23d6c-278">**SurfaceMeshesToPlanes.cs** findet und generiert auf der Grundlage der räumlichen Zuordnungsdaten Ebenen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-278">**SurfaceMeshesToPlanes.cs** will find and generate planes based on the spatial mapping data.</span></span> <span data-ttu-id="23d6c-279">Wir verwenden in unserer Anwendung Flächen zum Darstellen von Wänden, Flächen und Oberflächen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-279">We will use planes in our application to represent walls, floors and ceilings.</span></span> <span data-ttu-id="23d6c-280">Diese vorfab umfasst auch **RemoveSurfaceVertices.cs** , mit dem Vertices aus dem räumlichen zuordnungsmesh entfernt werden können.</span><span class="sxs-lookup"><span data-stu-id="23d6c-280">This prefab also includes **RemoveSurfaceVertices.cs** which can remove vertices from the spatial mapping mesh.</span></span> <span data-ttu-id="23d6c-281">Dies kann verwendet werden, um Löcher im Mesh zu erstellen oder um überzählige Dreiecke zu entfernen, die nicht mehr benötigt werden (da stattdessen Flächen verwendet werden können).</span><span class="sxs-lookup"><span data-stu-id="23d6c-281">This can be used to create holes in the mesh, or to remove excess triangles that are no longer needed (because planes can be used instead).</span></span>

* <span data-ttu-id="23d6c-282">Suchen Sie im **Projekt** Panel von Unity im Ordner **holograms** das **spacecollection** -Objekt.</span><span class="sxs-lookup"><span data-stu-id="23d6c-282">In Unity's **Project** panel, **Holograms** folder, find the **SpaceCollection** object.</span></span>
* <span data-ttu-id="23d6c-283">Ziehen Sie das **spacecollection** -Objekt per Drag & Drop in den Bereich **Hierarchie** .</span><span class="sxs-lookup"><span data-stu-id="23d6c-283">Drag and drop the **SpaceCollection** object into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="23d6c-284">Wählen Sie im Bereich **Hierarchie** das **spatialprocessing** -Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="23d6c-284">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="23d6c-285">Suchen Sie im **Inspektor** -Panel die Komponente " **Play Space Manager (Skript)** ".</span><span class="sxs-lookup"><span data-stu-id="23d6c-285">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="23d6c-286">Doppelklicken Sie auf **PlaySpaceManager.cs** , um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-286">Double-click on **PlaySpaceManager.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="23d6c-287">PlaySpaceManager.cs enthält anwendungsspezifischen Code.</span><span class="sxs-lookup"><span data-stu-id="23d6c-287">PlaySpaceManager.cs contains application-specific code.</span></span> <span data-ttu-id="23d6c-288">Wir werden diesem Skriptfunktionen hinzufügen, um folgendes Verhalten zu ermöglichen:</span><span class="sxs-lookup"><span data-stu-id="23d6c-288">We will add functionality to this script to enable the following behavior:</span></span>

1. <span data-ttu-id="23d6c-289">Die Erfassung räumlicher Zuordnungsdaten wird beendet, wenn das Überprüfungs Zeit Limit (10 Sekunden) überschritten wird.</span><span class="sxs-lookup"><span data-stu-id="23d6c-289">Stop collecting spatial mapping data after we exceed the scanning time limit (10 seconds).</span></span>
2. <span data-ttu-id="23d6c-290">Verarbeiten Sie die räumlichen Mapping-Daten:</span><span class="sxs-lookup"><span data-stu-id="23d6c-290">Process the spatial mapping data:</span></span>
    1. <span data-ttu-id="23d6c-291">Verwenden Sie surfacetten, um eine einfachere Darstellung der Welt als Flächen (Wände, Flächen, Oberflächen usw.) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-291">Use SurfaceMeshesToPlanes to create a simpler representation of the world as planes (walls, floors, ceilings, etc).</span></span>
    2. <span data-ttu-id="23d6c-292">Verwenden Sie removesurfacevertices, um Oberflächen überdreitel zu entfernen, die innerhalb der Ebenen liegen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-292">Use RemoveSurfaceVertices to remove surface triangles that fall within plane boundaries.</span></span>
3. <span data-ttu-id="23d6c-293">Generieren Sie eine Sammlung von holograms auf der ganzen Welt, und platzieren Sie Sie in der Nähe des Benutzers auf der Wand-und Bodenebene.</span><span class="sxs-lookup"><span data-stu-id="23d6c-293">Generate a collection of holograms in the world and place them on wall and floor planes near the user.</span></span>

<span data-ttu-id="23d6c-294">Führen Sie die in PlaySpaceManager.cs markierten Codierungs Übungen aus, oder ersetzen Sie das Skript durch die fertige Projekt Mappe aus folgendem:</span><span class="sxs-lookup"><span data-stu-id="23d6c-294">Complete the coding exercises marked in PlaySpaceManager.cs, or replace the script with the finished solution from below:</span></span>

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

<span data-ttu-id="23d6c-295">**Erstellen und bereitstellen**</span><span class="sxs-lookup"><span data-stu-id="23d6c-295">**Build and Deploy**</span></span>

* <span data-ttu-id="23d6c-296">Drücken Sie vor der Bereitstellung in den hololens in Unity die **Wiedergabe** Schaltfläche, um den Wiedergabemodus einzugeben.</span><span class="sxs-lookup"><span data-stu-id="23d6c-296">Before deploying to the HoloLens, press the **Play** button in Unity to enter play mode.</span></span>
* <span data-ttu-id="23d6c-297">Nachdem das Raum Netz aus der Datei geladen wurde, warten Sie 10 Sekunden, bevor die Verarbeitung im Netz für räumliche Zuordnung gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="23d6c-297">After the room mesh is loaded from file, wait for 10 seconds before processing starts on the spatial mapping mesh.</span></span>
* <span data-ttu-id="23d6c-298">Wenn die Verarbeitung fertiggestellt ist, werden die flächenflächen, Wände, Ceiling usw. angezeigt.</span><span class="sxs-lookup"><span data-stu-id="23d6c-298">When processing is complete, planes will appear to represent the floor, walls, ceiling, etc.</span></span>
* <span data-ttu-id="23d6c-299">Nachdem alle Ebenen gefunden wurden, sollte ein Sonnensystem in einer Tabelle mit der Nähe der Kamera angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="23d6c-299">After all of the planes have been found, you should see a solar system appear on a table of floor near the camera.</span></span>
* <span data-ttu-id="23d6c-300">In der Nähe der Kamera sollten auch zwei Poster angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="23d6c-300">Two posters should appear on walls near the camera too.</span></span> <span data-ttu-id="23d6c-301">Wechseln Sie zur Registerkarte **Szene** , wenn Sie im **Spiel** Modus nicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="23d6c-301">Switch to the **Scene** tab if you cannot see them in **Game** mode.</span></span>
* <span data-ttu-id="23d6c-302">Drücken Sie erneut die **Wiedergabe** Schaltfläche, um den Wiedergabemodus zu beenden</span><span class="sxs-lookup"><span data-stu-id="23d6c-302">Press the **Play** button again to exit play mode.</span></span>
* <span data-ttu-id="23d6c-303">Erstellen und stellen Sie die hololens wie gewohnt bereit.</span><span class="sxs-lookup"><span data-stu-id="23d6c-303">Build and deploy to the HoloLens, as usual.</span></span>
* <span data-ttu-id="23d6c-304">Warten Sie, bis die Überprüfung und Verarbeitung der räumlichen Mapping-Daten durchgeführt wurden.</span><span class="sxs-lookup"><span data-stu-id="23d6c-304">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="23d6c-305">Wenn Sie die Ebenen sehen, finden Sie heraus, das Sonnensystem und die Poster in ihrer Welt zu finden.</span><span class="sxs-lookup"><span data-stu-id="23d6c-305">Once you see planes, try to find the solar system and posters in your world.</span></span>

## <a name="chapter-4---placement"></a><span data-ttu-id="23d6c-306">Kapitel 4: Platzierung</span><span class="sxs-lookup"><span data-stu-id="23d6c-306">Chapter 4 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

<span data-ttu-id="23d6c-307">**Ziele**</span><span class="sxs-lookup"><span data-stu-id="23d6c-307">**Objectives**</span></span>

* <span data-ttu-id="23d6c-308">Stellen Sie fest, ob ein – Hologramm auf eine Oberfläche passt.</span><span class="sxs-lookup"><span data-stu-id="23d6c-308">Determine if a hologram will fit on a surface.</span></span>
* <span data-ttu-id="23d6c-309">Geben Sie dem Benutzer Feedback, wenn ein – Hologramm in eine Oberfläche passt oder nicht.</span><span class="sxs-lookup"><span data-stu-id="23d6c-309">Provide feedback to the user when a hologram can/cannot fit on a surface.</span></span>

<span data-ttu-id="23d6c-310">**Anweisungen**</span><span class="sxs-lookup"><span data-stu-id="23d6c-310">**Instructions**</span></span>

* <span data-ttu-id="23d6c-311">Wählen Sie im Bereich **Hierarchie** der Unity das **spatialprocessing** -Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="23d6c-311">In Unity's **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="23d6c-312">Suchen Sie im **Inspektor** -Panel nach der Komponente, die an die Flächen **(Skript)** ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="23d6c-312">In the **Inspector** panel, find the **Surface Meshes To Planes (Script)** component.</span></span>
* <span data-ttu-id="23d6c-313">Ändern Sie die Eigenschaft **zeichnen-Ebenen** in **nichts** , um die Auswahl zu löschen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-313">Change the **Draw Planes** property to **Nothing** to clear the selection.</span></span>
* <span data-ttu-id="23d6c-314">Ändern Sie die Eigenschaft **zeichnen-Ebenen** in **Wall**, sodass nur die Zeichen Wandflächen gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="23d6c-314">Change the **Draw Planes** property to **Wall**, so that only wall planes will be rendered.</span></span>
* <span data-ttu-id="23d6c-315">Doppelklicken Sie im **Projekt** Panel im Ordner **Skripts** auf **Placeable.cs** , um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-315">In the **Project** panel, **Scripts** folder, double-click on **Placeable.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="23d6c-316">Das **ersetzbare** Skript ist bereits an das Poster-und Projektions Feld angefügt, die nach Abschluss der Flächensuche erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="23d6c-316">The **Placeable** script is already attached to the posters and projection box that are created after plane finding completes.</span></span> <span data-ttu-id="23d6c-317">Wir müssen lediglich Code auskommentieren, und mit diesem Skript wird Folgendes erreicht:</span><span class="sxs-lookup"><span data-stu-id="23d6c-317">All we need to do is uncomment some code, and this script will achieve the following:</span></span>

1. <span data-ttu-id="23d6c-318">Stellen Sie fest, ob ein – Hologramm auf eine Oberfläche passt, indem Sie das Raycasting aus dem Mittelpunkt und vier Ecken des umgebenden Cubes anfügen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-318">Determine if a hologram will fit on a surface by raycasting from the center and four corners of the bounding cube.</span></span>
2. <span data-ttu-id="23d6c-319">Überprüfen Sie die Oberflächen normale, um zu ermitteln, ob Sie für das – Hologramm reibungslos genug ist.</span><span class="sxs-lookup"><span data-stu-id="23d6c-319">Check the surface normal to determine if it is smooth enough for the hologram to sit flush on.</span></span>
3. <span data-ttu-id="23d6c-320">Rendering eines umgebenden Cubes um das Hologramm, um die tatsächliche Größe beim Platzieren anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-320">Render a bounding cube around the hologram to show its actual size while being placed.</span></span>
4. <span data-ttu-id="23d6c-321">Wandeln Sie einen Schatten unter/hinter dem – Hologramm um, um anzuzeigen, wo er auf der Etage/Wand platziert wird.</span><span class="sxs-lookup"><span data-stu-id="23d6c-321">Cast a shadow under/behind the hologram to show where it will be placed on the floor/wall.</span></span>
5. <span data-ttu-id="23d6c-322">Renderden Schatten als rot, wenn das – Hologramm nicht auf der Oberfläche platziert werden kann, oder grün, wenn dies möglich ist.</span><span class="sxs-lookup"><span data-stu-id="23d6c-322">Render the shadow as red, if the hologram cannot be placed on the surface, or green, if it can.</span></span>
6. <span data-ttu-id="23d6c-323">Richten Sie das Hologramm erneut an den Surface-Typ (vertikal oder horizontal) aus, zu dem er eine Affinität hat.</span><span class="sxs-lookup"><span data-stu-id="23d6c-323">Re-orient the hologram to align with the surface type (vertical or horizontal) that it has affinity to.</span></span>
7. <span data-ttu-id="23d6c-324">Platzieren Sie das – Hologramm reibungslos auf der ausgewählten Oberfläche, um das Springen oder Ausrichtungs Verhalten zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="23d6c-324">Smoothly place the hologram on the selected surface to avoid jumping or snapping behavior.</span></span>

<span data-ttu-id="23d6c-325">Kommentieren Sie den gesamten Code in der Codierungs Übung unten aus, oder verwenden Sie diese abgeschlossene Lösung in **Placeable.cs**:</span><span class="sxs-lookup"><span data-stu-id="23d6c-325">Uncomment all code in the coding exercise below, or use this completed solution in **Placeable.cs**:</span></span>

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
    /// The alignToVerticalSurface parameter is ignored if the object
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

<span data-ttu-id="23d6c-326">**Erstellen und bereitstellen**</span><span class="sxs-lookup"><span data-stu-id="23d6c-326">**Build and Deploy**</span></span>

* <span data-ttu-id="23d6c-327">Erstellen Sie wie zuvor das Projekt, und stellen Sie es auf den hololens bereit.</span><span class="sxs-lookup"><span data-stu-id="23d6c-327">As before, build the project and deploy to the HoloLens.</span></span>
* <span data-ttu-id="23d6c-328">Warten Sie, bis die Überprüfung und Verarbeitung der räumlichen Mapping-Daten durchgeführt wurden.</span><span class="sxs-lookup"><span data-stu-id="23d6c-328">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="23d6c-329">Wenn das Sonnensystem angezeigt wird, schauen Sie sich das folgende Projektions Feld an, und führen Sie eine Auswahl Geste aus, um es zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="23d6c-329">When you see the solar system, gaze at the projection box below and perform a select gesture to move it around.</span></span> <span data-ttu-id="23d6c-330">Während das Projektions Feld ausgewählt ist, wird ein umschließender Cube um das Projektions Feld sichtbar.</span><span class="sxs-lookup"><span data-stu-id="23d6c-330">While the projection box is selected, a bounding cube will be visible around the projection box.</span></span>
* <span data-ttu-id="23d6c-331">Bewegen Sie den Blick an eine andere Position im Raum.</span><span class="sxs-lookup"><span data-stu-id="23d6c-331">Move you head to gaze at a different location in the room.</span></span> <span data-ttu-id="23d6c-332">Das Projektions Feld sollte dem Blick folgen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-332">The projection box should follow your gaze.</span></span> <span data-ttu-id="23d6c-333">Wenn der Schatten unterhalb des Projektions Felds rot angezeigt wird, können Sie das Hologramm nicht auf dieser Oberfläche platzieren.</span><span class="sxs-lookup"><span data-stu-id="23d6c-333">When the shadow below the projection box turns red, you cannot place the hologram on that surface.</span></span> <span data-ttu-id="23d6c-334">Wenn der Schatten unterhalb der Projektionsfläche grün wird, können Sie das – Hologramm durch Ausführen einer weiteren Auswahl Bewegung platzieren.</span><span class="sxs-lookup"><span data-stu-id="23d6c-334">When the shadow below the projection box turns green, you can place the hologram by performing another select gesture.</span></span>
* <span data-ttu-id="23d6c-335">Suchen und wählen Sie eines der Holographic-Poster an einer Wand aus, um es an einen neuen Speicherort zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="23d6c-335">Find and select one of the holographic posters on a wall to move it to a new location.</span></span> <span data-ttu-id="23d6c-336">Beachten Sie, dass Sie das Poster nicht auf der Boden-oder Ceiling-Oberfläche platzieren können und dass es bei der Navigation ordnungsgemäß auf die einzelnen Wände ausgerichtet bleibt.</span><span class="sxs-lookup"><span data-stu-id="23d6c-336">Notice that you cannot place the poster on the floor or ceiling, and that it stays correctly oriented to each wall as you move around.</span></span>

## <a name="chapter-5---occlusion"></a><span data-ttu-id="23d6c-337">Kapitel 5-Okklusion</span><span class="sxs-lookup"><span data-stu-id="23d6c-337">Chapter 5 - Occlusion</span></span>

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

<span data-ttu-id="23d6c-338">**Ziele**</span><span class="sxs-lookup"><span data-stu-id="23d6c-338">**Objectives**</span></span>

* <span data-ttu-id="23d6c-339">Stellen Sie fest, ob ein – Hologramm durch das räumliche Mapping-Mesh verdeckt wird.</span><span class="sxs-lookup"><span data-stu-id="23d6c-339">Determine if a hologram is occluded by the spatial mapping mesh.</span></span>
* <span data-ttu-id="23d6c-340">Anwenden verschiedener Okklusions Techniken, um einen Spaß Effekt zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-340">Apply different occlusion techniques to achieve a fun effect.</span></span>

<span data-ttu-id="23d6c-341">**Anweisungen**</span><span class="sxs-lookup"><span data-stu-id="23d6c-341">**Instructions**</span></span>

<span data-ttu-id="23d6c-342">Zuerst gestatten wir dem räumlichen zuordnungsmesh, andere Hologramme zu okzieren, ohne die wirkliche Welt zu verzieren:</span><span class="sxs-lookup"><span data-stu-id="23d6c-342">First, we are going to allow the spatial mapping mesh to occlude other holograms without occluding the real world:</span></span>

* <span data-ttu-id="23d6c-343">Wählen Sie im Bereich **Hierarchie** das **spatialprocessing** -Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="23d6c-343">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="23d6c-344">Suchen Sie im **Inspektor** -Panel die Komponente " **Play Space Manager (Skript)** ".</span><span class="sxs-lookup"><span data-stu-id="23d6c-344">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="23d6c-345">Klicken Sie auf den Kreis rechts neben der Eigenschaft **sekundäres Material** .</span><span class="sxs-lookup"><span data-stu-id="23d6c-345">Click the circle to the right of the **Secondary Material** property.</span></span>
* <span data-ttu-id="23d6c-346">Suchen und wählen Sie das **oksions** Material aus, und schließen Sie das Fenster.</span><span class="sxs-lookup"><span data-stu-id="23d6c-346">Find and select the **Occlusion** material and close the window.</span></span>

<span data-ttu-id="23d6c-347">Als Nächstes fügen wir ein spezielles Verhalten zur Erde hinzu, sodass es eine blaue Hervorhebung hat, wenn es von einem anderen – Hologramm (wie der Sun) oder durch das räumliche zuordnungsmesh wird:</span><span class="sxs-lookup"><span data-stu-id="23d6c-347">Next, we are going to add a special behavior to Earth, so that it has a blue highlight whenever it becomes occluded by another hologram (like the sun), or by the spatial mapping mesh:</span></span>

* <span data-ttu-id="23d6c-348">Erweitern Sie im **Projekt** Panel im Ordner **holograms** das Objekt " **Solar System** ".</span><span class="sxs-lookup"><span data-stu-id="23d6c-348">In the **Project** panel, in the **Holograms** folder, expand the **SolarSystem** object.</span></span>
* <span data-ttu-id="23d6c-349">Klicken Sie auf **Erde**.</span><span class="sxs-lookup"><span data-stu-id="23d6c-349">Click on **Earth**.</span></span>
* <span data-ttu-id="23d6c-350">Suchen Sie im **Inspektor** -Panel nach dem Material der Erde (untere Komponente).</span><span class="sxs-lookup"><span data-stu-id="23d6c-350">In the **Inspector** panel, find the Earth's material (bottom component).</span></span>
* <span data-ttu-id="23d6c-351">Ändern Sie in der **Shader-Dropdown-** Datei den Shader in **benutzerdefiniertes > oksionrim**.</span><span class="sxs-lookup"><span data-stu-id="23d6c-351">In the **Shader drop-down**, change the shader to **Custom > OcclusionRim**.</span></span> <span data-ttu-id="23d6c-352">Dadurch wird eine blaue Hervorhebung um die Erde herum gerendert, wenn Sie von einem anderen Objekt verdeckt wird.</span><span class="sxs-lookup"><span data-stu-id="23d6c-352">This will render a blue highlight around Earth whenever it is occluded by another object.</span></span>

<span data-ttu-id="23d6c-353">Zum Schluss aktivieren wir einen x-ray-Vision-Effekt für Planeten in unserem Sonnensystem.</span><span class="sxs-lookup"><span data-stu-id="23d6c-353">Finally, we are going to enable an x-ray vision effect for planets in our solar system.</span></span> <span data-ttu-id="23d6c-354">Wir müssen **PlanetOcclusion.cs** (im Ordner scripz\solarsystem) bearbeiten, um Folgendes zu erreichen:</span><span class="sxs-lookup"><span data-stu-id="23d6c-354">We will need to edit **PlanetOcclusion.cs** (found in the Scripts\SolarSystem folder) in order to achieve the following:</span></span>

1. <span data-ttu-id="23d6c-355">Stellen Sie fest, ob ein Planet von der spatialmapping-Schicht (Raum-und Flächen) verdeckt wird.</span><span class="sxs-lookup"><span data-stu-id="23d6c-355">Determine if a planet is occluded by the SpatialMapping layer (room meshes and planes).</span></span>
2. <span data-ttu-id="23d6c-356">Zeigt die Draht Modell-Darstellung eines Planeten an, wenn er von der spatialmapping-Ebene verdeckt wird.</span><span class="sxs-lookup"><span data-stu-id="23d6c-356">Show the wireframe representation of a planet whenever it is occluded by the SpatialMapping layer.</span></span>
3. <span data-ttu-id="23d6c-357">Blenden Sie die Draht Modell-Darstellung eines Planeten aus, wenn er nicht durch die spatialmapping-Ebene blockiert wird.</span><span class="sxs-lookup"><span data-stu-id="23d6c-357">Hide the wireframe representation of a planet when it is not blocked by the SpatialMapping layer.</span></span>

<span data-ttu-id="23d6c-358">Befolgen Sie die Codierungs Übung in PlanetOcclusion.cs, oder verwenden Sie die folgende Lösung:</span><span class="sxs-lookup"><span data-stu-id="23d6c-358">Follow the coding exercise in PlanetOcclusion.cs, or use the following solution:</span></span>

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

<span data-ttu-id="23d6c-359">**Erstellen und bereitstellen**</span><span class="sxs-lookup"><span data-stu-id="23d6c-359">**Build and Deploy**</span></span>

* <span data-ttu-id="23d6c-360">Erstellen Sie die Anwendung wie üblich, und stellen Sie Sie in hololens bereit.</span><span class="sxs-lookup"><span data-stu-id="23d6c-360">Build and deploy the application to HoloLens, as usual.</span></span>
* <span data-ttu-id="23d6c-361">Warten Sie, bis die Überprüfung und Verarbeitung der räumlichen Mapping-Daten fertig sind. (es sollten blaue Linien auf den Wänden angezeigt werden.)</span><span class="sxs-lookup"><span data-stu-id="23d6c-361">Wait for scanning and processing of the spatial mapping data to be complete (you should see blue lines appear on walls).</span></span>
* <span data-ttu-id="23d6c-362">Suchen Sie das Projektions Feld des Sonnensystems, und wählen Sie es aus, und legen Sie dann das Kontrollkästchen neben einer Wand oder hinter einem Zählers fest.</span><span class="sxs-lookup"><span data-stu-id="23d6c-362">Find and select the solar system's projection box and then set the box next to a wall or behind a counter.</span></span>
* <span data-ttu-id="23d6c-363">Sie können die grundlegende oksion anzeigen, indem Sie hinter den Oberflächen auf dem Poster oder der Projektionsfläche ausblenden.</span><span class="sxs-lookup"><span data-stu-id="23d6c-363">You can view basic occlusion by hiding behind surfaces to peer at the poster or projection box.</span></span>
* <span data-ttu-id="23d6c-364">Suchen Sie nach der Erde. es sollte ein blauer Hervorhebungs Effekt auftreten, wenn Sie auf ein anderes Hologramm oder eine Oberfläche zurückgeht.</span><span class="sxs-lookup"><span data-stu-id="23d6c-364">Look for the Earth, there should be a blue highlight effect whenever it goes behind another hologram or surface.</span></span>
* <span data-ttu-id="23d6c-365">Beobachten Sie, wie sich die Planeten hinter der Wand oder anderen Oberflächen im Raum bewegen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-365">Watch as the planets move behind the wall or other surfaces in the room.</span></span> <span data-ttu-id="23d6c-366">Sie verfügen nun über eine x-ray-Vision und können Ihre Draht Modell-Skelette sehen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-366">You now have x-ray vision and can see their wireframe skeletons!</span></span>

## <a name="the-end"></a><span data-ttu-id="23d6c-367">Das Ende</span><span class="sxs-lookup"><span data-stu-id="23d6c-367">The End</span></span>

<span data-ttu-id="23d6c-368">Gratulation!</span><span class="sxs-lookup"><span data-stu-id="23d6c-368">Congratulations!</span></span> <span data-ttu-id="23d6c-369">Sie haben jetzt die räumliche **230: räumliche Zuordnung**abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="23d6c-369">You have now completed **MR Spatial 230: Spatial mapping**.</span></span>

* <span data-ttu-id="23d6c-370">Sie wissen, wie Sie Ihre Umgebung scannen und räumliche Mapping-Daten in Unity laden.</span><span class="sxs-lookup"><span data-stu-id="23d6c-370">You know how to scan your environment and load spatial mapping data to Unity.</span></span>
* <span data-ttu-id="23d6c-371">Sie verstehen die Grundlagen von Shadern und die Art und Weise, wie Materialien zum erneuten visualisieren der Welt eingesetzt werden können.</span><span class="sxs-lookup"><span data-stu-id="23d6c-371">You understand the basics of shaders and how materials can be used to re-visualize the world.</span></span>
* <span data-ttu-id="23d6c-372">Sie haben neue Verarbeitungstechniken zum Suchen von Ebenen und zum Entfernen von Dreiecken aus einem Mesh gelernt.</span><span class="sxs-lookup"><span data-stu-id="23d6c-372">You learned of new processing techniques for finding planes and removing triangles from a mesh.</span></span>
* <span data-ttu-id="23d6c-373">Sie konnten Hologramme an Oberflächen verschieben und platzieren, die sinnvoll waren.</span><span class="sxs-lookup"><span data-stu-id="23d6c-373">You were able to move and place holograms on surfaces that made sense.</span></span>
* <span data-ttu-id="23d6c-374">Sie haben verschiedene Okklusions Techniken erlebt und die Leistungsfähigkeit der x-ray-Vision genutzt!</span><span class="sxs-lookup"><span data-stu-id="23d6c-374">You experienced different occlusion techniques and harnessed the power of x-ray vision!</span></span>
