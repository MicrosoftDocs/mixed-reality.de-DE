---
title: Räumlicher Ton-220-Ton
description: Befolgen Sie diese Codierungs Exemplarische Vorgehensweise mit Unity, Visual Studio und hololens, um die Details der räumlichen audiokonzepte zu erlernen.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, Tutorial, räumlicher Sound
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526911"
---
>[!NOTE]
><span data-ttu-id="8e101-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="8e101-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="8e101-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="8e101-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="8e101-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8e101-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="8e101-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="8e101-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="8e101-108">Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="8e101-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="8e101-109">Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="8e101-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="8e101-110">Räumliche Daten 220: Raumklang</span><span class="sxs-lookup"><span data-stu-id="8e101-110">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="8e101-111">[Räumlicher Sound](spatial-sound.md) atmet Leben in holograms und bietet Ihnen die Präsenz in unserer Welt.</span><span class="sxs-lookup"><span data-stu-id="8e101-111">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="8e101-112">Holograms bestehen aus Licht und Ton, und wenn Sie Ihre Hologramme nicht vergessen, kann räumlicher Sound Ihnen helfen, Sie zu finden.</span><span class="sxs-lookup"><span data-stu-id="8e101-112">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="8e101-113">Der räumliche Sound ist nicht mit dem typischen Sound vergleichbar, den Sie im Radio hören würden, es handelt sich um Sound, der in 3D-Raum positioniert ist.</span><span class="sxs-lookup"><span data-stu-id="8e101-113">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="8e101-114">Mit räumlichem Sound können Sie holograms so gestalten, wie Sie sich hinter ihnen befinden, oder auch auf Ihrem Kopf!</span><span class="sxs-lookup"><span data-stu-id="8e101-114">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="8e101-115">In diesem Kurs werden Sie wie folgt vorgehen:</span><span class="sxs-lookup"><span data-stu-id="8e101-115">In this course, you will:</span></span>

* <span data-ttu-id="8e101-116">Konfigurieren Sie Ihre Entwicklungsumgebung für die Verwendung von Microsoft Spatial Sound.</span><span class="sxs-lookup"><span data-stu-id="8e101-116">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="8e101-117">Verwenden Sie räumliche Töne, um Interaktionen zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="8e101-117">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="8e101-118">Verwenden Sie räumliche Sounds in Verbindung mit räumlicher Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="8e101-118">Use Spatial Sound in conjunction with Spatial Mapping.</span></span>
* <span data-ttu-id="8e101-119">Informieren Sie sich über die bewährten Vorgehensweisen zum Entwerfen und mischen</span><span class="sxs-lookup"><span data-stu-id="8e101-119">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="8e101-120">Verwenden Sie Sound, um besondere Effekte zu verbessern und den Benutzer in die gemischte Realität zu bringen.</span><span class="sxs-lookup"><span data-stu-id="8e101-120">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="8e101-121">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="8e101-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="8e101-122">Natürlich</span><span class="sxs-lookup"><span data-stu-id="8e101-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="8e101-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8e101-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8e101-124"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="8e101-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="8e101-125">Räumliche Daten 220: Raumklang</span><span class="sxs-lookup"><span data-stu-id="8e101-125">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="8e101-126">✔️</span><span class="sxs-lookup"><span data-stu-id="8e101-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="8e101-127">✔️</span><span class="sxs-lookup"><span data-stu-id="8e101-127">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="8e101-128">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="8e101-128">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="8e101-129">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="8e101-129">Prerequisites</span></span>

* <span data-ttu-id="8e101-130">Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md)konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="8e101-130">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="8e101-131">Einige Grund C# Legende Programmiermöglichkeiten.</span><span class="sxs-lookup"><span data-stu-id="8e101-131">Some basic C# programming ability.</span></span>
* <span data-ttu-id="8e101-132">Sie sollten die [Grundlagen von 101](holograms-101.md)abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="8e101-132">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="8e101-133">Ein hololens-Gerät, das [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode)ist.</span><span class="sxs-lookup"><span data-stu-id="8e101-133">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="8e101-134">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="8e101-134">Project files</span></span>

* <span data-ttu-id="8e101-135">Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) , die für das Projekt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="8e101-135">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="8e101-136"> Erfordert Unity 2017,2 oder höher.</span><span class="sxs-lookup"><span data-stu-id="8e101-136"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="8e101-137">Wenn Sie weiterhin Unity 5,6-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span><span class="sxs-lookup"><span data-stu-id="8e101-137">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="8e101-138">Diese Version ist möglicherweise nicht mehr auf dem neuesten Stand.</span><span class="sxs-lookup"><span data-stu-id="8e101-138">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="8e101-139">Wenn Sie weiterhin Unity 5,5-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span><span class="sxs-lookup"><span data-stu-id="8e101-139">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="8e101-140"> Diese Version ist möglicherweise nicht mehr auf dem neuesten Stand.</span><span class="sxs-lookup"><span data-stu-id="8e101-140"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="8e101-141">Wenn Sie weiterhin Unity 5,4-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span><span class="sxs-lookup"><span data-stu-id="8e101-141">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="8e101-142"> Diese Version ist möglicherweise nicht mehr auf dem neuesten Stand.</span><span class="sxs-lookup"><span data-stu-id="8e101-142"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="8e101-143">Deinstallieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht zugänglichen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="8e101-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="8e101-144">Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span><span class="sxs-lookup"><span data-stu-id="8e101-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="8e101-145">Errata und Notizen</span><span class="sxs-lookup"><span data-stu-id="8e101-145">Errata and Notes</span></span>

* <span data-ttu-id="8e101-146">"Enable nur eigenen Code" muss in Visual Studio unter "Extras-> Optionen" deaktiviert*werden (>* Debuggen, um Breakpoints im Code zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="8e101-146">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="8e101-147">Kapitel 1: Einrichtung von Unity</span><span class="sxs-lookup"><span data-stu-id="8e101-147">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="8e101-148">Ziele</span><span class="sxs-lookup"><span data-stu-id="8e101-148">Objectives</span></span>

* <span data-ttu-id="8e101-149">Ändern Sie die Sound Konfiguration von Unity, sodass Sie Microsoft Spatial Sound verwendet.</span><span class="sxs-lookup"><span data-stu-id="8e101-149">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="8e101-150">Hinzufügen eines 3D-Sounds zu einem Objekt in Unity.</span><span class="sxs-lookup"><span data-stu-id="8e101-150">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="8e101-151">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="8e101-151">Instructions</span></span>

* <span data-ttu-id="8e101-152">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="8e101-152">Start Unity.</span></span>
* <span data-ttu-id="8e101-153">Wählen Sie **Öffnen**aus.</span><span class="sxs-lookup"><span data-stu-id="8e101-153">Select **Open**.</span></span>
* <span data-ttu-id="8e101-154">Navigieren Sie zu Ihrem Desktop, und suchen Sie den Ordner, den Sie zuvor nicht archiviert haben.</span><span class="sxs-lookup"><span data-stu-id="8e101-154">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="8e101-155">Klicken Sie auf den Ordner **starting\decibel** , und klicken Sie dann auf die Schaltfläche **Ordner auswählen** .</span><span class="sxs-lookup"><span data-stu-id="8e101-155">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="8e101-156">Warten Sie, bis das Projekt in Unity geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="8e101-156">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="8e101-157">Öffnen Sie im **Projekt** Panel **scenes\decibel.unity**.</span><span class="sxs-lookup"><span data-stu-id="8e101-157">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="8e101-158">Erweitern Sie im Bereich **Hierarchie** den Knoten **hologrammcollection** , und wählen Sie **P0LY**aus.</span><span class="sxs-lookup"><span data-stu-id="8e101-158">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="8e101-159">Erweitern Sie im Inspektor den Eintrag **audiosource** , und beachten Sie, dass kein **spatialize** -Kontrollkästchen vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="8e101-159">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="8e101-160">Standardmäßig lädt Unity kein spatializer-Plug-in.</span><span class="sxs-lookup"><span data-stu-id="8e101-160">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="8e101-161">Mit den folgenden Schritten wird räumlicher Sound im Projekt aktiviert.</span><span class="sxs-lookup"><span data-stu-id="8e101-161">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="8e101-162">Wechseln Sie im oberen Menü von Unity zu **Edit > Project Settings > Audiodatei**.</span><span class="sxs-lookup"><span data-stu-id="8e101-162">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="8e101-163">Suchen Sie nach der Dropdown Liste **spatializer Plugin** , und wählen Sie **MS HRTF spatializer**aus.</span><span class="sxs-lookup"><span data-stu-id="8e101-163">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="8e101-164">Wählen Sie im Bereich **Hierarchie** die Option **hologramcollection > P0LY**aus.</span><span class="sxs-lookup"><span data-stu-id="8e101-164">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="8e101-165">Suchen Sie im **Inspektor** -Panel die Komponente **Audioquelle** .</span><span class="sxs-lookup"><span data-stu-id="8e101-165">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="8e101-166">Aktivieren Sie das Kontrollkästchen **spatialize** .</span><span class="sxs-lookup"><span data-stu-id="8e101-166">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="8e101-167">Ziehen Sie  den Schieberegler räumlichkeits Weise in **3D**, oder geben Sie 1 in das Bearbeitungsfeld **ein** .</span><span class="sxs-lookup"><span data-stu-id="8e101-167">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="8e101-168">Wir erstellen nun das Projekt in Unity und konfigurieren die Projekt Mappe in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8e101-168">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="8e101-169">Wählen Sie in Unity **Datei >** Buildeinstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="8e101-169">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="8e101-170">Klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="8e101-170">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="8e101-171">Wählen Sie in der Liste **Plattform** **universelle Windows-Plattform** aus, und klicken Sie auf **Plattform wechseln**.</span><span class="sxs-lookup"><span data-stu-id="8e101-171">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="8e101-172">Wenn Sie speziell für hololens entwickeln, legen Sie **Zielgerät** auf **hololens**fest.</span><span class="sxs-lookup"><span data-stu-id="8e101-172">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="8e101-173">Andernfalls sollten Sie es auf **jedem Gerät**belassen.</span><span class="sxs-lookup"><span data-stu-id="8e101-173">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="8e101-174">Stellen  Sie sicher, dass der Buildtyp auf **D3D** und das **SDK** auf **Latest installiert** festgelegt ist (was SDK 16299 oder höher sein sollte).</span><span class="sxs-lookup"><span data-stu-id="8e101-174">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="8e101-175">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="8e101-175">Click **Build**.</span></span>
7. <span data-ttu-id="8e101-176">Erstellen Sie einen **neuen Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="8e101-176">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="8e101-177">Klicken Sie einfach auf den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="8e101-177">Single click the **App** folder.</span></span>
9. <span data-ttu-id="8e101-178">Drücken **Sie Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="8e101-178">Press **Select Folder**.</span></span>

<span data-ttu-id="8e101-179">Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8e101-179">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="8e101-180">Öffnen Sie den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="8e101-180">Open the **App** folder.</span></span>
2. <span data-ttu-id="8e101-181">Öffnen Sie die Projekt Mappe **Decibel Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="8e101-181">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="8e101-182">Bei der Bereitstellung in hololens:</span><span class="sxs-lookup"><span data-stu-id="8e101-182">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="8e101-183">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x86**.</span><span class="sxs-lookup"><span data-stu-id="8e101-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="8e101-184">Klicken Sie auf den Dropdown Pfeil neben der Schaltfläche lokaler Computer, und wählen Sie **Remote Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="8e101-184">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="8e101-185">Geben Sie **die IP-Adresse des hololens-Geräts** ein, und legen Sie den Authentifizierungsmodus auf **Universal (unverschlüsseltes Protokoll)**</span><span class="sxs-lookup"><span data-stu-id="8e101-185">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="8e101-186">Klicken Sie auf **Auswählen**.</span><span class="sxs-lookup"><span data-stu-id="8e101-186">Click **Select**.</span></span> <span data-ttu-id="8e101-187">Wenn Sie die IP-Adresse Ihres Geräts nicht kennen, suchen Sie unter **Einstellungen > Netzwerk & Internet > Erweiterte Optionen**.</span><span class="sxs-lookup"><span data-stu-id="8e101-187">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="8e101-188">Klicken Sie in der oberen Menüleiste auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="8e101-188">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="8e101-189">Wenn Sie die Bereitstellung auf Ihrem Gerät zum ersten Mal durchführt, müssen Sie [es mit Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen)koppeln.</span><span class="sxs-lookup"><span data-stu-id="8e101-189">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span></span>

<span data-ttu-id="8e101-190">Bei der Bereitstellung auf einem immersiven Headset:</span><span class="sxs-lookup"><span data-stu-id="8e101-190">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="8e101-191">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x64**.</span><span class="sxs-lookup"><span data-stu-id="8e101-191">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="8e101-192">Stellen Sie sicher, dass das Bereitstellungs Ziel auf **lokaler Computer**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="8e101-192">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="8e101-193">Klicken Sie in der oberen Menüleiste auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="8e101-193">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="8e101-194">Kapitel 2: räumlicher Sound und Interaktion</span><span class="sxs-lookup"><span data-stu-id="8e101-194">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="8e101-195">Ziele</span><span class="sxs-lookup"><span data-stu-id="8e101-195">Objectives</span></span>

* <span data-ttu-id="8e101-196">Verbessern Sie das – Hologramm-Realismus mithilfe von Sound.</span><span class="sxs-lookup"><span data-stu-id="8e101-196">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="8e101-197">Leiten Sie den Benutzer Blick mithilfe von Sound weiter.</span><span class="sxs-lookup"><span data-stu-id="8e101-197">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="8e101-198">Stellen Sie Gesten Feedback mit Sound bereit.</span><span class="sxs-lookup"><span data-stu-id="8e101-198">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="8e101-199">Teil 1: verbessern des Realismus</span><span class="sxs-lookup"><span data-stu-id="8e101-199">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="8e101-200">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="8e101-200">Key Concepts</span></span>

* <span data-ttu-id="8e101-201">Räumalisieren Sie – Hologramm-Sounds.</span><span class="sxs-lookup"><span data-stu-id="8e101-201">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="8e101-202">Audioquellen sollten an einem geeigneten Speicherort auf dem Hologram abgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="8e101-202">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="8e101-203">Der richtige Speicherort für den Sound hängt von dem Hologram ab.</span><span class="sxs-lookup"><span data-stu-id="8e101-203">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="8e101-204">Wenn das – Hologramm z. b. von einem Menschen ist, sollte sich die Audioquelle nahe dem Mund und nicht der Fußzeile befinden.</span><span class="sxs-lookup"><span data-stu-id="8e101-204">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="8e101-205">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="8e101-205">Instructions</span></span>

<span data-ttu-id="8e101-206">Die folgenden Anweisungen fügen einen räumlichen Sound an ein Hologramm an.</span><span class="sxs-lookup"><span data-stu-id="8e101-206">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="8e101-207">Erweitern Sie im Bereich **Hierarchie** den Knoten **hologrammcollection** , und wählen Sie **P0LY**aus.</span><span class="sxs-lookup"><span data-stu-id="8e101-207">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="8e101-208">Klicken Sie im Bereich **Inspector** in der **audiosource**auf den Kreis neben **Audioclip** , und wählen Sie im Popup Fenster **polyhover** aus.</span><span class="sxs-lookup"><span data-stu-id="8e101-208">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="8e101-209">Klicken Sie auf den Kreis neben **Ausgabe** , und wählen Sie im Popup Fenster **soundeffects** aus.</span><span class="sxs-lookup"><span data-stu-id="8e101-209">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="8e101-210">Project Decibel verwendet eine Unity- **Audiomixer** -Komponente, um das Anpassen von Sound Ebenen für Gruppen von Sounds zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="8e101-210">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="8e101-211">Durch das Gruppieren von Sounds auf diese Weise kann das Gesamt Volume angepasst werden, während die relative Menge der einzelnen Sounds beibehalten wird.</span><span class="sxs-lookup"><span data-stu-id="8e101-211">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="8e101-212">Erweitern Sie in der **audiosource** **3D Sound Settings**.</span><span class="sxs-lookup"><span data-stu-id="8e101-212">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="8e101-213">Legen Sie die **Doppler-Ebene** auf **0**fest.</span><span class="sxs-lookup"><span data-stu-id="8e101-213">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="8e101-214">Durch das Festlegen von Doppler-Level auf NULL werden die Änderungen in der durch Bewegung (entweder im – Hologramm oder im Benutzer) verursachten Tonhöhe deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="8e101-214">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="8e101-215">Ein klassisches Beispiel für Doppler ist ein schnell beweglicher Wagen.</span><span class="sxs-lookup"><span data-stu-id="8e101-215">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="8e101-216">Wenn sich das Auto auf einen stationären Listener nähert, steigt die Tonhöhe der Engine.</span><span class="sxs-lookup"><span data-stu-id="8e101-216">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="8e101-217">Wenn Sie den Listener übergibt, wird die-Tonhöhe mit Distance gesenkt.</span><span class="sxs-lookup"><span data-stu-id="8e101-217">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="8e101-218">Teil 2: leiten des Benutzer Blicks</span><span class="sxs-lookup"><span data-stu-id="8e101-218">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="8e101-219">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="8e101-219">Key Concepts</span></span>

* <span data-ttu-id="8e101-220">Verwenden Sie Sound, um auf wichtige holograms aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="8e101-220">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="8e101-221">Die Ohren helfen Ihnen, den Augenblick zu lenken.</span><span class="sxs-lookup"><span data-stu-id="8e101-221">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="8e101-222">Das Gehirn hat einige Erwartungen gelernt.</span><span class="sxs-lookup"><span data-stu-id="8e101-222">The brain has some learned expectations.</span></span>

<span data-ttu-id="8e101-223">Ein Beispiel für die gewonnenen Erwartungen ist, dass die Vögel in der Regel über den Köpfen der Menschen sind.</span><span class="sxs-lookup"><span data-stu-id="8e101-223">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="8e101-224">Wenn ein Benutzer ein vogelton hört, besteht die anfängliche Reaktion darin, nach oben zu suchen.</span><span class="sxs-lookup"><span data-stu-id="8e101-224">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="8e101-225">Das Platzieren eines Vogels unterhalb des Benutzers kann dazu führen, dass er mit der richtigen Richtung des Sounds zurechtkommt, aber das – Hologramm nicht finden kann, je nachdem, dass er gesucht werden muss.</span><span class="sxs-lookup"><span data-stu-id="8e101-225">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="8e101-226">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="8e101-226">Instructions</span></span>

<span data-ttu-id="8e101-227">Mithilfe der folgenden Anweisungen können Sie P0LY hinter Ihnen verbergen, damit Sie den Sound verwenden können, um das Hologram zu suchen.</span><span class="sxs-lookup"><span data-stu-id="8e101-227">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="8e101-228">Wählen Sie im Bereich **Hierarchie** die Option **Manager**aus.</span><span class="sxs-lookup"><span data-stu-id="8e101-228">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="8e101-229">Suchen Sie im **Inspektor** -Panel den **Spracheingabe Handler**.</span><span class="sxs-lookup"><span data-stu-id="8e101-229">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="8e101-230">Erweitern Sie im **Spracheingabe Handler**den Bereich **Gehe ausblenden**.</span><span class="sxs-lookup"><span data-stu-id="8e101-230">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="8e101-231">Ändern Sie **keine Funktion** in **polyactions. gohide**.</span><span class="sxs-lookup"><span data-stu-id="8e101-231">Change **No Function** to **PolyActions.GoHide**.</span></span>

![Schlüsselwort Ausblenden ausblenden](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="8e101-233">Teil 3: Gesten Feedback</span><span class="sxs-lookup"><span data-stu-id="8e101-233">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="8e101-234">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="8e101-234">Key Concepts</span></span>

* <span data-ttu-id="8e101-235">Bereitstellen von positiver Gesten Bestätigung mit Sound</span><span class="sxs-lookup"><span data-stu-id="8e101-235">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="8e101-236">Bewegen Sie die Benutzer übermäßig lauter Sounds nicht auf die gleiche Weise</span><span class="sxs-lookup"><span data-stu-id="8e101-236">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="8e101-237">Feine Sounds funktionieren am besten</span><span class="sxs-lookup"><span data-stu-id="8e101-237">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="8e101-238">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="8e101-238">Instructions</span></span>

* <span data-ttu-id="8e101-239">Erweitern Sie im Bereich **Hierarchie** den Knoten **hologrammcollection**.</span><span class="sxs-lookup"><span data-stu-id="8e101-239">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="8e101-240">Erweitern Sie **energyhub** , und wählen Sie **Basis**aus.</span><span class="sxs-lookup"><span data-stu-id="8e101-240">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="8e101-241">Klicken Sie im **Inspektor** -Panel auf **Komponente hinzufügen** , und fügen Sie **Gesten Sound Handler**hinzu.</span><span class="sxs-lookup"><span data-stu-id="8e101-241">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="8e101-242">Klicken Sie in **Gesten Sound Handler**auf den Kreis neben **Navigation Started Clip** und **Navigation aktualisierte Clip** , und wählen Sie im Popup Fenster für beide den Bereich **rotateclick** aus.</span><span class="sxs-lookup"><span data-stu-id="8e101-242">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="8e101-243">Doppelklicken Sie auf "gesturesound Handler", um in Visual Studio zu laden.</span><span class="sxs-lookup"><span data-stu-id="8e101-243">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="8e101-244">Der Gesten Sound Handler führt die folgenden Aufgaben aus:</span><span class="sxs-lookup"><span data-stu-id="8e101-244">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="8e101-245">Erstellen und konfigurieren Sie eine **audiosource**.</span><span class="sxs-lookup"><span data-stu-id="8e101-245">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="8e101-246">Platzieren Sie die **audiosource** an der Position des entsprechenden **gameobject**.</span><span class="sxs-lookup"><span data-stu-id="8e101-246">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="8e101-247">Gibt den **Audioclip** wieder, der mit der Geste verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="8e101-247">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="8e101-248">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="8e101-248">Build and Deploy</span></span>

1. <span data-ttu-id="8e101-249">Wählen Sie in Unity **Datei >** Buildeinstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="8e101-249">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="8e101-250">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="8e101-250">Click **Build**.</span></span>
3. <span data-ttu-id="8e101-251">Klicken Sie einfach auf den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="8e101-251">Single click the **App** folder.</span></span>
4. <span data-ttu-id="8e101-252">Drücken **Sie Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="8e101-252">Press **Select Folder**.</span></span>

<span data-ttu-id="8e101-253">Überprüfen Sie, ob die Symbolleiste "Release", "x86", "x64" und "Remote Gerät" heißt.</span><span class="sxs-lookup"><span data-stu-id="8e101-253">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="8e101-254">Wenn dies nicht der Fall ist, ist dies die Codierungs Instanz von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8e101-254">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="8e101-255">Möglicherweise müssen Sie die Projekt Mappe aus dem App-Ordner erneut öffnen.</span><span class="sxs-lookup"><span data-stu-id="8e101-255">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="8e101-256">Wenn Sie dazu aufgefordert werden, laden Sie die Projektdateien erneut</span><span class="sxs-lookup"><span data-stu-id="8e101-256">If prompted, reload the project files.</span></span>
* <span data-ttu-id="8e101-257">Stellen Sie wie zuvor über Visual Studio bereit.</span><span class="sxs-lookup"><span data-stu-id="8e101-257">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="8e101-258">Nachdem die Anwendung bereitgestellt wurde:</span><span class="sxs-lookup"><span data-stu-id="8e101-258">After the application is deployed:</span></span>

* <span data-ttu-id="8e101-259">Beobachten Sie, wie sich der Sound bei der Umstellung auf P0LY ändert.</span><span class="sxs-lookup"><span data-stu-id="8e101-259">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="8e101-260">Sagen Sie *"go hide" (ausblenden* ), um P0LY zu einem Speicherort hinter Ihnen zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="8e101-260">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="8e101-261">Suchen Sie nach dem Sound.</span><span class="sxs-lookup"><span data-stu-id="8e101-261">Find it by the sound.</span></span>
* <span data-ttu-id="8e101-262">Schauen Sie sich die Basis des Energy Hubs an.</span><span class="sxs-lookup"><span data-stu-id="8e101-262">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="8e101-263">Tippen und ziehen Sie nach links oder rechts, um das – Hologramm zu drehen, und sehen Sie, wie der Klick Sound die Geste bestätigt.</span><span class="sxs-lookup"><span data-stu-id="8e101-263">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="8e101-264">Hinweis: Ein Text Panel wird zusammen mit Ihnen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8e101-264">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="8e101-265">Diese werden die verfügbaren Sprachbefehle enthalten, die Sie in diesem Kurs verwenden können.</span><span class="sxs-lookup"><span data-stu-id="8e101-265">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="8e101-266">Kapitel 3: räumliche und räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="8e101-266">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="8e101-267">Ziele</span><span class="sxs-lookup"><span data-stu-id="8e101-267">Objectives</span></span>

* <span data-ttu-id="8e101-268">Bestätigen Sie die Interaktion zwischen holograms und der realen Welt mit Sound.</span><span class="sxs-lookup"><span data-stu-id="8e101-268">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="8e101-269">Verwenden Sie den Sound mit der physischen Welt.</span><span class="sxs-lookup"><span data-stu-id="8e101-269">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="8e101-270">Teil 1-physische Welt Interaktion</span><span class="sxs-lookup"><span data-stu-id="8e101-270">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="8e101-271">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="8e101-271">Key Concepts</span></span>

* <span data-ttu-id="8e101-272">Physische Objekte machen im Allgemeinen einen Sound, wenn Sie auf eine Oberfläche oder ein anderes Objekt stoßen.</span><span class="sxs-lookup"><span data-stu-id="8e101-272">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="8e101-273">Sounds sollte Kontext freundlich sein.</span><span class="sxs-lookup"><span data-stu-id="8e101-273">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="8e101-274">Beispielsweise sollte das Festlegen eines Cup für eine Tabelle einen ruhigeren Sound als das Löschen eines Boulders auf einem Metal-Gerät machen.</span><span class="sxs-lookup"><span data-stu-id="8e101-274">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="8e101-275">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="8e101-275">Instructions</span></span>

* <span data-ttu-id="8e101-276">Erweitern Sie im Bereich **Hierarchie** den Knoten **hologrammcollection**.</span><span class="sxs-lookup"><span data-stu-id="8e101-276">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="8e101-277">Erweitern Sie **energyhub**, und wählen Sie **Basis**aus.</span><span class="sxs-lookup"><span data-stu-id="8e101-277">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="8e101-278">Klicken Sie im **Inspektor** -Panel auf **Komponente hinzufügen** , und fügen Sie **mit Sound und Action Tap**hinzu.</span><span class="sxs-lookup"><span data-stu-id="8e101-278">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="8e101-279">**Tippen Sie auf, um mit Sound und Action zu platzieren**:</span><span class="sxs-lookup"><span data-stu-id="8e101-279">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="8e101-280">Aktivieren Sie **übergeordnetes Element bei tippen**.</span><span class="sxs-lookup"><span data-stu-id="8e101-280">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="8e101-281">Legen Sie **Platzierungs Sound** auf **platzieren**fest.</span><span class="sxs-lookup"><span data-stu-id="8e101-281">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="8e101-282">Legen Sie **Pickup Sound** auf **Pickup**fest.</span><span class="sxs-lookup"><span data-stu-id="8e101-282">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="8e101-283">Drücken Sie die Taste + unten rechts unter sowohl **bei der** Aufnahme-als auch bei der **Platzierungs Aktion**.</span><span class="sxs-lookup"><span data-stu-id="8e101-283">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="8e101-284">Ziehen Sie energyhub aus der Szene in die Felder **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="8e101-284">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="8e101-285">Klicken Sie unter **on Pickup Action**auf **No Function** -> **energyhubbase** -> **resettanimation.**</span><span class="sxs-lookup"><span data-stu-id="8e101-285">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="8e101-286">Klicken Sie unter **Platzierungs Aktion**auf **keine Funktion** -> **energyhubbase** -> **onselect**.</span><span class="sxs-lookup"><span data-stu-id="8e101-286">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![Mit Sound und Action tippen](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="8e101-288">Teil 2: Sound Okklusion</span><span class="sxs-lookup"><span data-stu-id="8e101-288">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="8e101-289">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="8e101-289">Key Concepts</span></span>

* <span data-ttu-id="8e101-290">Sound, wie z. b. Light, können ausgeblendet werden.</span><span class="sxs-lookup"><span data-stu-id="8e101-290">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="8e101-291">Ein klassisches Beispiel ist eine Concert Hall.</span><span class="sxs-lookup"><span data-stu-id="8e101-291">A classic example is a concert hall.</span></span> <span data-ttu-id="8e101-292">Wenn ein Listener außerhalb der Halle steht und die Tür geschlossen ist, hört sich die Musik mit gedämpften Tönen an.</span><span class="sxs-lookup"><span data-stu-id="8e101-292">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="8e101-293">Es gibt in der Regel auch eine Reduzierung des Volumes.</span><span class="sxs-lookup"><span data-stu-id="8e101-293">There is also typically a reduction in volume.</span></span> <span data-ttu-id="8e101-294">Wenn die Tür geöffnet ist, wird das gesamte Spektrum des Sounds auf dem eigentlichen Volume gehört.</span><span class="sxs-lookup"><span data-stu-id="8e101-294">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="8e101-295">Sounds mit hoher Frequenz werden im Allgemeinen mehr als niedrige Frequenzen erfasst.</span><span class="sxs-lookup"><span data-stu-id="8e101-295">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="8e101-296">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="8e101-296">Instructions</span></span>

* <span data-ttu-id="8e101-297">Erweitern Sie im Bereich **Hierarchie** den Knoten **hologrammcollection** , und wählen Sie **P0LY**aus.</span><span class="sxs-lookup"><span data-stu-id="8e101-297">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="8e101-298">Klicken Sie im **Inspektor** -Panel auf **Komponente hinzufügen** , und fügen Sie **audioemitter**hinzu.</span><span class="sxs-lookup"><span data-stu-id="8e101-298">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="8e101-299">Die audioemitter-Klasse bietet die folgenden Features:</span><span class="sxs-lookup"><span data-stu-id="8e101-299">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="8e101-300">Stellt alle Änderungen am Volume der **audiosource**wieder her.</span><span class="sxs-lookup"><span data-stu-id="8e101-300">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="8e101-301">Führt eine " **Physik. raycastnonzuweisung** " aus der Position des Benutzers in der Richtung des **gameobject** aus, an das der **audioemitter** angefügt ist.</span><span class="sxs-lookup"><span data-stu-id="8e101-301">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="8e101-302">Die raycastnonalloc-Methode wird als Leistungsoptimierung verwendet, um Zuordnungen und die Anzahl der zurückgegebenen Ergebnisse einzuschränken.</span><span class="sxs-lookup"><span data-stu-id="8e101-302">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="8e101-303">Für jeden gefundenen **iaudioinflutercer** Ruft die **applyeffect** -Methode auf.</span><span class="sxs-lookup"><span data-stu-id="8e101-303">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="8e101-304">Für jeden vorherigen **iaudioinfludencer** , der nicht mehr gefunden wird, wird die **removeeffect** -Methode aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="8e101-304">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="8e101-305">Beachten Sie, dass audioemitter bei menschlichen Zeitskalen aktualisiert wird, im Gegensatz zu pro Frame.</span><span class="sxs-lookup"><span data-stu-id="8e101-305">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="8e101-306">Der Grund hierfür ist, dass Menschen im Allgemeinen nicht schnell genug verschieben, damit die Auswirkungen häufiger als jedes Quartal oder die Hälfte der Sekunde aktualisiert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="8e101-306">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="8e101-307">Hologramme, die schnell von einem Speicherort an einen anderen teleportieren, können die Illusion unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="8e101-307">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="8e101-308">Erweitern Sie im Bereich **Hierarchie** den Knoten **hologrammcollection**.</span><span class="sxs-lookup"><span data-stu-id="8e101-308">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="8e101-309">Erweitern Sie **energyhub** , und wählen Sie **blobaußen**aus.</span><span class="sxs-lookup"><span data-stu-id="8e101-309">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="8e101-310">Klicken Sie im **Inspektor** -Panel auf **Komponente hinzufügen** , und fügen Sie **audiookokder**hinzu.</span><span class="sxs-lookup"><span data-stu-id="8e101-310">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="8e101-311">Legen Sie in **audiookder**den Umstellungs **Frequenz** -Wert auf **1500**fest.</span><span class="sxs-lookup"><span data-stu-id="8e101-311">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="8e101-312">Diese Einstellung schränkt die audiosource-Frequenzen auf 1500 Hz und niedriger ein.</span><span class="sxs-lookup"><span data-stu-id="8e101-312">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="8e101-313">Legen Sie den **volumedurchlauf** auf **0,9**fest.</span><span class="sxs-lookup"><span data-stu-id="8e101-313">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="8e101-314">Mit dieser Einstellung wird das Volume der audiosource auf die aktuelle Ebene von 90% reduziert.</span><span class="sxs-lookup"><span data-stu-id="8e101-314">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="8e101-315">Der audiookton implementiert iaudioinflutencer für Folgendes:</span><span class="sxs-lookup"><span data-stu-id="8e101-315">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="8e101-316">Anwenden eines Okklusions Effekts mithilfe eines **audiolowpassfilter** , der an die **audiosource** angefügt wird, die den **audioemitter**kauft.</span><span class="sxs-lookup"><span data-stu-id="8e101-316">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="8e101-317">Wendet die volumedämpfung auf die audiosource an.</span><span class="sxs-lookup"><span data-stu-id="8e101-317">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="8e101-318">Deaktiviert den Effekt durch Festlegen einer neutralen Umstellungs Frequenz und Deaktivieren des Filters.</span><span class="sxs-lookup"><span data-stu-id="8e101-318">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="8e101-319">Die als neutral verwendete Häufigkeit ist 22 kHz (22000 Hz).</span><span class="sxs-lookup"><span data-stu-id="8e101-319">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="8e101-320">Diese Häufigkeit wurde gewählt, weil Sie über der maximalen maximalen Frequenz liegt, die vom menschlichen Ohr gehört werden kann, sodass keine erkennbaren Auswirkungen auf den Sound entstehen.</span><span class="sxs-lookup"><span data-stu-id="8e101-320">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="8e101-321">Wählen Sie im Bereich **Hierarchie** die Option **spatialmapping**aus.</span><span class="sxs-lookup"><span data-stu-id="8e101-321">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="8e101-322">Klicken Sie im **Inspektor** -Panel auf **Komponente hinzufügen** , und fügen Sie **audiookokder**hinzu.</span><span class="sxs-lookup"><span data-stu-id="8e101-322">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="8e101-323">Legen Sie in **audiookder**den Umstellungs **Frequenz** -Wert auf **750**fest.</span><span class="sxs-lookup"><span data-stu-id="8e101-323">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="8e101-324">Wenn sich mehrere okader im Pfad zwischen dem Benutzer und dem **audioemitter**befinden, wird die niedrigste Frequenz auf den Filter angewendet.</span><span class="sxs-lookup"><span data-stu-id="8e101-324">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="8e101-325">Legen Sie den **volumedurchlauf** auf **0,75**fest.</span><span class="sxs-lookup"><span data-stu-id="8e101-325">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="8e101-326">Wenn sich mehrere okader im Pfad zwischen dem Benutzer und dem **audioemitter**befinden, wird das Volume weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="8e101-326">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="8e101-327">Wählen Sie im Bereich **Hierarchie** die Option **Manager**aus.</span><span class="sxs-lookup"><span data-stu-id="8e101-327">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="8e101-328">Erweitern Sie im **Inspektor** -Panel den **Spracheingabe Handler**.</span><span class="sxs-lookup"><span data-stu-id="8e101-328">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="8e101-329">Erweitern Sie im **Spracheingabe Handler den Eintrag** **go-Belastung**.</span><span class="sxs-lookup"><span data-stu-id="8e101-329">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="8e101-330">Ändern Sie **keine Funktion** in **polyactions. goabgerechnet**.</span><span class="sxs-lookup"><span data-stu-id="8e101-330">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![Schlüsselwort Gehe zu](images/gocharge.png)

* <span data-ttu-id="8e101-332">Erweitern Sie **hier**.</span><span class="sxs-lookup"><span data-stu-id="8e101-332">Expand **Come Here**.</span></span>
* <span data-ttu-id="8e101-333">Ändern Sie **keine Funktion** in **polyactions. ComeBack**.</span><span class="sxs-lookup"><span data-stu-id="8e101-333">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![Schlüsselwort Komm her](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="8e101-335">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="8e101-335">Build and Deploy</span></span>

* <span data-ttu-id="8e101-336">Erstellen Sie wie zuvor das Projekt in Unity, und stellen Sie es in Visual Studio bereit.</span><span class="sxs-lookup"><span data-stu-id="8e101-336">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="8e101-337">Nachdem die Anwendung bereitgestellt wurde:</span><span class="sxs-lookup"><span data-stu-id="8e101-337">After the application is deployed:</span></span>

* <span data-ttu-id="8e101-338">Sagen Sie *"Go-Kosten"* , damit P0LY den Energie-Hub eingeben.</span><span class="sxs-lookup"><span data-stu-id="8e101-338">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="8e101-339">Beachten Sie die Änderung des Sounds.</span><span class="sxs-lookup"><span data-stu-id="8e101-339">Note the change in the sound.</span></span> <span data-ttu-id="8e101-340">Dies sollte ein wenig leiser werden.</span><span class="sxs-lookup"><span data-stu-id="8e101-340">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="8e101-341">Wenn Sie sich in der Lage sind, sich mit einer Wand oder einem anderen Objekt zwischen Ihnen und dem Energie-Hub zu positionieren, sollten Sie aufgrund der Okklusion der realen Welt eine weitere Belastung des Sounds feststellen.</span><span class="sxs-lookup"><span data-stu-id="8e101-341">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="8e101-342">Sagen *Sie* , dass P0LY den Energie-Hub verlassen und sich vor Ihnen positionieren muss.</span><span class="sxs-lookup"><span data-stu-id="8e101-342">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="8e101-343">Beachten Sie, dass die Sound Okklusion einmal entfernt wird P0LY beendet den Energie-Hub.</span><span class="sxs-lookup"><span data-stu-id="8e101-343">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="8e101-344">Wenn Sie immer noch mit der Okklusion hören, wird P0LY möglicherweise von der realen Welt ausgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="8e101-344">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="8e101-345">Versuchen Sie, die Umstellung durchführen zu lassen.</span><span class="sxs-lookup"><span data-stu-id="8e101-345">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="8e101-346">Teile von 3-Raum-Modellen</span><span class="sxs-lookup"><span data-stu-id="8e101-346">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="8e101-347">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="8e101-347">Key Concepts</span></span>

* <span data-ttu-id="8e101-348">Die Größe des Speicherplatzes bietet unter-Warteschlangen, die zur Sound Lokalisierung beitragen.</span><span class="sxs-lookup"><span data-stu-id="8e101-348">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="8e101-349">Raummodelle werden pro**audiosource**festgelegt.</span><span class="sxs-lookup"><span data-stu-id="8e101-349">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="8e101-350">Das [mixedrealitytoolkit für Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) stellt Code zum Festlegen des raummodells bereit.</span><span class="sxs-lookup"><span data-stu-id="8e101-350">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="8e101-351">Wählen Sie für gemischte Realität das Raummodell aus, das am besten zu dem realen Raum passt.</span><span class="sxs-lookup"><span data-stu-id="8e101-351">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="8e101-352">Wenn Sie ein virtuelles Reality-Szenario erstellen, wählen Sie das Raummodell aus, das für die virtuelle Umgebung am besten geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="8e101-352">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="8e101-353">Kapitel 4: Sound Design</span><span class="sxs-lookup"><span data-stu-id="8e101-353">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="8e101-354">Ziele</span><span class="sxs-lookup"><span data-stu-id="8e101-354">Objectives</span></span>

* <span data-ttu-id="8e101-355">Verstehen Sie die Überlegungen für den effektiven Sound Entwurf.</span><span class="sxs-lookup"><span data-stu-id="8e101-355">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="8e101-356">Erlernen Sie die Vorgehensweisen für das Mischen von Techniken</span><span class="sxs-lookup"><span data-stu-id="8e101-356">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="8e101-357">Teil 1: Sound und Erfahrungs Entwurf</span><span class="sxs-lookup"><span data-stu-id="8e101-357">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="8e101-358">In diesem Abschnitt werden die wichtigsten Überlegungen und Richtlinien für Sound und Design erläutert.</span><span class="sxs-lookup"><span data-stu-id="8e101-358">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="8e101-359">Alle Sounds normalisieren</span><span class="sxs-lookup"><span data-stu-id="8e101-359">Normalize all sounds</span></span>

<span data-ttu-id="8e101-360">Dadurch ist es nicht erforderlich, dass Sonderfallcode die volumeebenen pro Sound anpasst, was zeitaufwändig sein kann, und die Möglichkeit zum einfachen Aktualisieren von Sounddateien einschränkt.</span><span class="sxs-lookup"><span data-stu-id="8e101-360">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="8e101-361">Entwurf für eine unteschte Darstellung</span><span class="sxs-lookup"><span data-stu-id="8e101-361">Design for an untethered experience</span></span>

<span data-ttu-id="8e101-362">Hololens ist ein vollständig enthaltener holografischer Computer.</span><span class="sxs-lookup"><span data-stu-id="8e101-362">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="8e101-363">Ihre Benutzer können Ihre Erfahrungen während des Verschiebens nutzen und verwenden.</span><span class="sxs-lookup"><span data-stu-id="8e101-363">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="8e101-364">Testen Sie Ihre Audiomischung, indem Sie Sie durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="8e101-364">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="8e101-365">Ausgabe von logischen Speicherorten auf Ihren holograms</span><span class="sxs-lookup"><span data-stu-id="8e101-365">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="8e101-366">In der Praxis kommt ein Hund nicht von seinem Ende her, und die Stimme eines Menschen wird nicht von seinen Füßen entfernt.</span><span class="sxs-lookup"><span data-stu-id="8e101-366">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="8e101-367">Vermeiden Sie, dass Ihre Sounds aus unerwarteten teilen ihrer holograms ausgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="8e101-367">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="8e101-368">Bei kleinen holograms ist es sinnvoll, eine Soundausgabe aus der Mitte der Geometrie zu haben.</span><span class="sxs-lookup"><span data-stu-id="8e101-368">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="8e101-369">Vertraute Sounds sind die meisten lokalisierbaren Sounds</span><span class="sxs-lookup"><span data-stu-id="8e101-369">Familiar sounds are most localizable</span></span>

<span data-ttu-id="8e101-370">Die Menschen Sprache und Musik sind sehr einfach zu lokalisieren.</span><span class="sxs-lookup"><span data-stu-id="8e101-370">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="8e101-371">Wenn jemand Ihren Namen aufruft, können Sie genau feststellen, welche Richtung die Stimme erhalten hat und wie weit entfernt.</span><span class="sxs-lookup"><span data-stu-id="8e101-371">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="8e101-372">Kurze, unbekannte Sounds sind schwieriger zu lokalisieren.</span><span class="sxs-lookup"><span data-stu-id="8e101-372">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="8e101-373">Erkennen von Erwartungen von Benutzern</span><span class="sxs-lookup"><span data-stu-id="8e101-373">Be cognizant of user expectations</span></span>

<span data-ttu-id="8e101-374">Die Lebensdauer spielt einen Teil der Möglichkeit, den Speicherort eines Sounds zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="8e101-374">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="8e101-375">Dies ist ein Grund, warum die menschliche Stimme besonders leicht lokalisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="8e101-375">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="8e101-376">Es ist wichtig, dass Sie wissen, welche Erwartungen der Benutzer beim Platzieren Ihrer Sounds hat.</span><span class="sxs-lookup"><span data-stu-id="8e101-376">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="8e101-377">Wenn ein Benutzer beispielsweise einen vogelsong hört, sehen Sie sich im Allgemeinen an, da sich die Vögel in der Regel über der Sicht befinden (in der Struktur oder in einer Struktur).</span><span class="sxs-lookup"><span data-stu-id="8e101-377">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="8e101-378">Es ist nicht ungewöhnlich, dass ein Benutzer die korrekte Richtung eines Sounds einschaltet, aber in der falschen vertikalen Richtung sucht und verwirrt oder frustriert wird, wenn er das Hologram nicht finden kann.</span><span class="sxs-lookup"><span data-stu-id="8e101-378">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="8e101-379">Vermeiden Sie verborgene Emitter.</span><span class="sxs-lookup"><span data-stu-id="8e101-379">Avoid hidden emitters</span></span>

<span data-ttu-id="8e101-380">In der realen Welt können wir, wenn wir einen Sound hören, im Allgemeinen das Objekt identifizieren, das den Sound ausgibt.</span><span class="sxs-lookup"><span data-stu-id="8e101-380">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="8e101-381">Dies sollte auch für Ihre Erfahrungen sorgen.</span><span class="sxs-lookup"><span data-stu-id="8e101-381">This should also hold true in your experiences.</span></span> <span data-ttu-id="8e101-382">Es kann sehr stark sein, dass Benutzer einen Sound hören und wissen, woher der Sound stammt und ein Objekt nicht sehen kann.</span><span class="sxs-lookup"><span data-stu-id="8e101-382">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="8e101-383">Es gibt einige Ausnahmen zu dieser Richtlinie.</span><span class="sxs-lookup"><span data-stu-id="8e101-383">There are some exceptions to this guideline.</span></span> <span data-ttu-id="8e101-384">Umgebungs Klänge wie z. b. Crickets in einem Feld müssen z. b. nicht sichtbar sein.</span><span class="sxs-lookup"><span data-stu-id="8e101-384">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="8e101-385">Mit der Lebensdauer können wir uns mit der Quelle dieser Sounds vertraut machen, ohne Sie sehen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="8e101-385">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="8e101-386">Teil 2: Sound Mischung</span><span class="sxs-lookup"><span data-stu-id="8e101-386">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="8e101-387">Ziel ihrer Mischung für 70% Volume in den hololens</span><span class="sxs-lookup"><span data-stu-id="8e101-387">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="8e101-388">Gemischte Realität ermöglicht das Erkennen von holograms in der realen Welt.</span><span class="sxs-lookup"><span data-stu-id="8e101-388">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="8e101-389">Sie sollten auch das hören von echten Sounds erlauben.</span><span class="sxs-lookup"><span data-stu-id="8e101-389">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="8e101-390">Ein 70%-volumespeicherziel ermöglicht dem Benutzer, die Welt mit dem Sound Ihrer Benutzerumgebung zu hören.</span><span class="sxs-lookup"><span data-stu-id="8e101-390">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="8e101-391">Hololens bei 100% Volume sollten externe Sounds auslagern</span><span class="sxs-lookup"><span data-stu-id="8e101-391">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="8e101-392">Eine Volumeebene von 100% ist vergleichbar mit einer Virtual Reality-Darstellung.</span><span class="sxs-lookup"><span data-stu-id="8e101-392">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="8e101-393">Der Benutzer wird visuell in eine andere Welt transportiert.</span><span class="sxs-lookup"><span data-stu-id="8e101-393">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="8e101-394">Dasselbe sollte true sein.</span><span class="sxs-lookup"><span data-stu-id="8e101-394">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="8e101-395">Verwenden des Unity Audiomixer zum Anpassen von Sound Kategorien</span><span class="sxs-lookup"><span data-stu-id="8e101-395">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="8e101-396">Beim Entwerfen ihrer Mischung ist es häufig hilfreich, audiokategorien zu erstellen, und Sie können das Volume als Einheit vergrößern oder verkleinern.</span><span class="sxs-lookup"><span data-stu-id="8e101-396">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="8e101-397">Dies behält die relativen Ebenen jedes Sounds bei und ermöglicht gleichzeitig schnelle und einfache Änderungen an der gesamten Mischung.</span><span class="sxs-lookup"><span data-stu-id="8e101-397">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="8e101-398">Zu den allgemeinen Kategorien gehören: Soundeffekte, Ambiente, Sprachausgabe und Hintergrundmusik.</span><span class="sxs-lookup"><span data-stu-id="8e101-398">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="8e101-399">Sounds auf der Grundlage des Benutzer Blicks mischen</span><span class="sxs-lookup"><span data-stu-id="8e101-399">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="8e101-400">Häufig kann es hilfreich sein, die Sound Mischung in Ihrer Benutzer Darstellung zu ändern, je nachdem, wo ein Benutzer sucht (oder nicht).</span><span class="sxs-lookup"><span data-stu-id="8e101-400">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="8e101-401">Diese Technik wird häufig verwendet, um die Volumeebene für holograms zu verringern, die sich außerhalb des Holographic Frame befinden, um dem Benutzer die Möglichkeit zu geben, sich auf die darin vorgelagerten Informationen zu konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="8e101-401">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="8e101-402">Eine andere Verwendung besteht darin, das Volume eines Sounds zu vergrößern, um die Aufmerksamkeit des Benutzers auf ein wichtiges Ereignis zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="8e101-402">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="8e101-403">Entwickeln der Mischung</span><span class="sxs-lookup"><span data-stu-id="8e101-403">Building your mix</span></span>

<span data-ttu-id="8e101-404">Wenn Sie Ihre Mischung entwickeln, empfiehlt es sich, mit der Hintergrund Audiofunktion Ihrer Benutzererfahrung zu beginnen und Ebenen basierend auf der Wichtigkeit hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="8e101-404">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="8e101-405">Dies führt häufig dazu, dass jede Ebene lauter ist als die vorherige.</span><span class="sxs-lookup"><span data-stu-id="8e101-405">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="8e101-406">Wenn Sie Ihre Mischung als umgekehrten Trichter mit den geringsten wichtigen (und üblicherweise ruhigste Sounds) im unteren Bereich vorstellen, empfiehlt es sich, die Mischung ähnlich wie im folgenden Diagramm zu strukturieren.</span><span class="sxs-lookup"><span data-stu-id="8e101-406">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![Sound Mischungs Struktur](images/soundlevels.png)

<span data-ttu-id="8e101-408">Die Sprachausgabe ist ein interessantes Szenario.</span><span class="sxs-lookup"><span data-stu-id="8e101-408">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="8e101-409">Basierend auf der von Ihnen erstellten Benutzersprache möchten Sie möglicherweise einen Stereo-Sound (nicht lokalisiert) oder eine räumliche Sprache umgestalten.</span><span class="sxs-lookup"><span data-stu-id="8e101-409">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="8e101-410">Zwei veröffentlichte Microsoft-Erfahrungen veranschaulichen hervorragende Beispiele für jedes Szenario.</span><span class="sxs-lookup"><span data-stu-id="8e101-410">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="8e101-411">[Holotour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) verwendet eine Stereo Stimme über.</span><span class="sxs-lookup"><span data-stu-id="8e101-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="8e101-412">Wenn die Sprachausgabe den Speicherort beschreibt, der angezeigt wird, ist der Sound konsistent und unterscheidet sich nicht je nach Position des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="8e101-412">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="8e101-413">Dadurch kann die Sprachausgabe die Szene beschreiben, ohne die räumlichen Klänge der Umgebung zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="8e101-413">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="8e101-414">[Fragmente](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) nutzt eine spatialisierte Stimme in Form eines Detektiven.</span><span class="sxs-lookup"><span data-stu-id="8e101-414">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="8e101-415">Die Stimme des Detektivs wird verwendet, um dem Benutzer einen wichtigen Hinweis zu vermitteln, als wäre ein tatsächlicher Mensch im Raum.</span><span class="sxs-lookup"><span data-stu-id="8e101-415">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="8e101-416">Dies bietet noch mehr Einblicke in die Möglichkeiten der Behebung des Geheimnisses.</span><span class="sxs-lookup"><span data-stu-id="8e101-416">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="8e101-417">Teil 3: Leistung</span><span class="sxs-lookup"><span data-stu-id="8e101-417">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="8e101-418">CPU-Auslastung</span><span class="sxs-lookup"><span data-stu-id="8e101-418">CPU usage</span></span>

<span data-ttu-id="8e101-419">Bei Verwendung von räumlichem Sound verbrauchen 10-12-Emitter ungefähr 12% der CPU.</span><span class="sxs-lookup"><span data-stu-id="8e101-419">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="8e101-420">Lange Audiodateien streamen</span><span class="sxs-lookup"><span data-stu-id="8e101-420">Stream long audio files</span></span>

<span data-ttu-id="8e101-421">Audiodaten können groß sein, insbesondere bei häufigen Stichproben Raten (44,1 und 48 kHz).</span><span class="sxs-lookup"><span data-stu-id="8e101-421">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="8e101-422">Eine allgemeine Regel ist, dass Audiodateien, die länger als 5-10 Sekunden sind, gestreamt werden sollten, um die Anwendungs Speicherauslastung zu reduzieren</span><span class="sxs-lookup"><span data-stu-id="8e101-422">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="8e101-423">In Unity können Sie eine Audiodatei für das Streaming in den Import Einstellungen der Datei markieren.</span><span class="sxs-lookup"><span data-stu-id="8e101-423">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![Audioimportierungseinstellungen](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="8e101-425">Kapitel 5: besondere Effekte</span><span class="sxs-lookup"><span data-stu-id="8e101-425">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="8e101-426">Ziele</span><span class="sxs-lookup"><span data-stu-id="8e101-426">Objectives</span></span>

* <span data-ttu-id="8e101-427">Fügen Sie "Magic Windows" Tiefe hinzu.</span><span class="sxs-lookup"><span data-stu-id="8e101-427">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="8e101-428">Bringen Sie den Benutzer in die virtuelle Welt.</span><span class="sxs-lookup"><span data-stu-id="8e101-428">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="8e101-429">Magische Fenster</span><span class="sxs-lookup"><span data-stu-id="8e101-429">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="8e101-430">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="8e101-430">Key Concepts</span></span>

* <span data-ttu-id="8e101-431">Das Erstellen von Ansichten in eine verborgene Welt ist visuell attraktiv.</span><span class="sxs-lookup"><span data-stu-id="8e101-431">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="8e101-432">Verbessern Sie die Realismus durch Hinzufügen von Audioeffekten, wenn ein – Hologramm oder der Benutzer sich in der Nähe der verborgenen Welt befindet</span><span class="sxs-lookup"><span data-stu-id="8e101-432">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="8e101-433">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="8e101-433">Instructions</span></span>

* <span data-ttu-id="8e101-434">Erweitern Sie im Bereich **Hierarchie** den Knoten **hologrammcollection** , und wählen Sie dann **Underworld**aus.</span><span class="sxs-lookup"><span data-stu-id="8e101-434">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="8e101-435">Erweitern Sie **Underworld** , und wählen Sie **voicesource**aus.</span><span class="sxs-lookup"><span data-stu-id="8e101-435">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="8e101-436">Klicken Sie im **Inspektor** -Panel auf **Komponente hinzufügen** , und fügen Sie den **Benutzer sprach Effekt**hinzu.</span><span class="sxs-lookup"><span data-stu-id="8e101-436">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="8e101-437">Eine **audiosource** -Komponente wird " **voicesource**" hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="8e101-437">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="8e101-438">Legen Sie in **audiosource** **Output** auf **UserVoice (Mixer)** fest.</span><span class="sxs-lookup"><span data-stu-id="8e101-438">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="8e101-439">Aktivieren Sie das Kontrollkästchen **spatialize** .</span><span class="sxs-lookup"><span data-stu-id="8e101-439">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="8e101-440">Ziehen Sie  den Schieberegler räumlichkeits Weise in **3D**, oder geben Sie 1 in das Bearbeitungsfeld **ein** .</span><span class="sxs-lookup"><span data-stu-id="8e101-440">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="8e101-441">Erweitern Sie **3D-Sound Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="8e101-441">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="8e101-442">Legen Sie die **Doppler-Ebene** auf **0**fest.</span><span class="sxs-lookup"><span data-stu-id="8e101-442">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="8e101-443">Legen Sie unter **User Voice Effect**das über **geordnete Objekt** auf die **Unterwelt** aus der Szene fest.</span><span class="sxs-lookup"><span data-stu-id="8e101-443">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="8e101-444">Legen Sie **Max Distance** auf **1**fest.</span><span class="sxs-lookup"><span data-stu-id="8e101-444">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="8e101-445">Durch das Festlegen von " **Max Distance** " wird der **Benutzer** darüber informiert, wie nah der Benutzer auf das übergeordnete Objekt sein muss, bevor der Effekt aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="8e101-445">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="8e101-446">Erweitern Sie unter **User Voice Effect**den Eintrag **Chorus Parameters**.</span><span class="sxs-lookup"><span data-stu-id="8e101-446">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="8e101-447">Legen Sie die **Tiefe** auf **0,1**fest.</span><span class="sxs-lookup"><span data-stu-id="8e101-447">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="8e101-448">Legen Sie **Tap 1 Volume**, **Tap 2 Volume** und **3 Volume** auf **0,8**fest.</span><span class="sxs-lookup"><span data-stu-id="8e101-448">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="8e101-449">Legen Sie **ursprüngliches Sound Volume** auf **0,5**fest.</span><span class="sxs-lookup"><span data-stu-id="8e101-449">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="8e101-450">Mit den vorherigen Einstellungen werden die Parameter des Unity- **audiochor-Filters** konfiguriert, der verwendet wird, um die Stimme des Benutzers zu ergänzen.</span><span class="sxs-lookup"><span data-stu-id="8e101-450">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="8e101-451">Erweitern Sie unter **User Voice Effect**den Eintrag **Echo Parameters**.</span><span class="sxs-lookup"><span data-stu-id="8e101-451">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="8e101-452">**Verzögerung** auf **300** festlegen</span><span class="sxs-lookup"><span data-stu-id="8e101-452">Set **Delay** to **300**</span></span>
* <span data-ttu-id="8e101-453">Legen Sie das **Zerfalls Verhältnis** auf **0,2**fest.</span><span class="sxs-lookup"><span data-stu-id="8e101-453">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="8e101-454">Legen Sie **ursprüngliches Sound Volume** auf **0**fest.</span><span class="sxs-lookup"><span data-stu-id="8e101-454">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="8e101-455">Mit den vorherigen Einstellungen werden die Parameter des Unity- **audioechofilters** konfiguriert, der verwendet wird, um die Stimme des Benutzers zu spiegeln.</span><span class="sxs-lookup"><span data-stu-id="8e101-455">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="8e101-456">Das Skript für den Benutzer sprach Effekt ist für Folgendes zuständig:</span><span class="sxs-lookup"><span data-stu-id="8e101-456">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="8e101-457">Messen des Abstands zwischen dem Benutzer und dem **gameobject** , an das das Skript angefügt wird.</span><span class="sxs-lookup"><span data-stu-id="8e101-457">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="8e101-458">Es wird ermittelt, ob der Benutzer dem **gameobject-Objekt**zusteht.</span><span class="sxs-lookup"><span data-stu-id="8e101-458">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="8e101-459">Der Benutzer muss das gameobject-Objekt, unabhängig von der Entfernung, sehen, damit der Effekt aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="8e101-459">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="8e101-460">Anwenden und Konfigurieren eines **audiochor-Filters** und eines **audioechofilters** auf die **audiosource**.</span><span class="sxs-lookup"><span data-stu-id="8e101-460">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="8e101-461">Deaktivieren der Auswirkung durch Deaktivieren der Filter.</span><span class="sxs-lookup"><span data-stu-id="8e101-461">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="8e101-462">Der Benutzer sprach Effekt verwendet die MIC-Datenstrom Auswahl Komponente aus dem [mixedrealitytoolkit für Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), um den hochwertigen Voice-Stream auszuwählen und ihn in das Audiosystem von Unity weiterzuleiten.</span><span class="sxs-lookup"><span data-stu-id="8e101-462">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="8e101-463">Wählen Sie im Bereich **Hierarchie** die Option **Manager**aus.</span><span class="sxs-lookup"><span data-stu-id="8e101-463">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="8e101-464">Erweitern Sie im **Inspektor** -Panel den **Spracheingabe Handler**.</span><span class="sxs-lookup"><span data-stu-id="8e101-464">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="8e101-465">Erweitern Sie in **Spracheingabe Handler**die Option **Unterwelt anzeigen**.</span><span class="sxs-lookup"><span data-stu-id="8e101-465">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="8e101-466">Ändern Sie **keine Funktion** in " **underworldbase. onenable**".</span><span class="sxs-lookup"><span data-stu-id="8e101-466">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![Schlüsselwort Unterwelt anzeigen](images/showunderworld.png)

* <span data-ttu-id="8e101-468">Erweitern Sie die Option **Unterwelt ausblenden**.</span><span class="sxs-lookup"><span data-stu-id="8e101-468">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="8e101-469">Ändern Sie **keine Funktion** in **underworldbase. ondeaktiviert**.</span><span class="sxs-lookup"><span data-stu-id="8e101-469">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![Schlüsselwort Unterwelt ausblenden](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="8e101-471">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="8e101-471">Build and Deploy</span></span>

* <span data-ttu-id="8e101-472">Erstellen Sie wie zuvor das Projekt in Unity, und stellen Sie es in Visual Studio bereit.</span><span class="sxs-lookup"><span data-stu-id="8e101-472">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="8e101-473">Nachdem die Anwendung bereitgestellt wurde:</span><span class="sxs-lookup"><span data-stu-id="8e101-473">After the application is deployed:</span></span>

* <span data-ttu-id="8e101-474">Stellen Sie eine Oberfläche (Wall, Floor, Table) dar, und sagen Sie *"Show Underworld"* .</span><span class="sxs-lookup"><span data-stu-id="8e101-474">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="8e101-475">Die Unterwelt wird angezeigt, und alle anderen holograms werden ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="8e101-475">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="8e101-476">Wenn die Unterwelt nicht angezeigt wird, stellen Sie sicher, dass Sie mit der realen Oberfläche konfrontiert sind.</span><span class="sxs-lookup"><span data-stu-id="8e101-476">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="8e101-477">Ansatz innerhalb von 1 Meter des Unterwelt – Hologramm, und beginnen Sie mit der Kommunikation.</span><span class="sxs-lookup"><span data-stu-id="8e101-477">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="8e101-478">Es gibt jetzt Audioeffekte, die auf Ihre Stimme angewendet werden!</span><span class="sxs-lookup"><span data-stu-id="8e101-478">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="8e101-479">Schalten Sie die Unterwelt aus, und beachten Sie, dass der Effekt nicht mehr angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="8e101-479">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="8e101-480">Sagen Sie *"Unterwelt ausblenden"* , um die Unterwelt auszublenden.</span><span class="sxs-lookup"><span data-stu-id="8e101-480">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="8e101-481">Die Unterwelt wird ausgeblendet, und die zuvor ausgeblendeten holograms werden erneut angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8e101-481">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="8e101-482">Das Ende</span><span class="sxs-lookup"><span data-stu-id="8e101-482">The End</span></span>

<span data-ttu-id="8e101-483">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="8e101-483">Congratulations!</span></span> <span data-ttu-id="8e101-484">Sie haben jetzt die **räumliche 220 von abgeschlossen: Räumlicher**Sound.</span><span class="sxs-lookup"><span data-stu-id="8e101-484">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="8e101-485">Lauschen Sie auf die Welt, und bringen Sie Ihre Erfahrungen mit Sound!</span><span class="sxs-lookup"><span data-stu-id="8e101-485">Listen to the world and bring your experiences to life with sound!</span></span>
