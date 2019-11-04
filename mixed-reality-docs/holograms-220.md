---
title: Räumlicher Ton-220-Ton
description: Befolgen Sie diese Codierungs Exemplarische Vorgehensweise mit Unity, Visual Studio und hololens, um die Details der räumlichen audiokonzepte zu erlernen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, Tutorial, räumlicher Sound
ms.openlocfilehash: a3fc054927d73cf9ac21f831caa4ec23875977bd
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434725"
---
>[!NOTE]
><span data-ttu-id="329e7-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="329e7-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="329e7-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="329e7-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="329e7-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="329e7-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="329e7-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="329e7-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="329e7-108">Es wurde [eine neue Reihe von Tutorials](mrlearning-base.md) für hololens 2 gepostet.</span><span class="sxs-lookup"><span data-stu-id="329e7-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="329e7-109">Mr Spatial 220: räumlicher Sound</span><span class="sxs-lookup"><span data-stu-id="329e7-109">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="329e7-110">[Räumlicher Sound](spatial-sound.md) atmet Leben in holograms und bietet Ihnen die Präsenz in unserer Welt.</span><span class="sxs-lookup"><span data-stu-id="329e7-110">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="329e7-111">Holograms bestehen aus Licht und Ton, und wenn Sie Ihre Hologramme nicht vergessen, kann räumlicher Sound Ihnen helfen, Sie zu finden.</span><span class="sxs-lookup"><span data-stu-id="329e7-111">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="329e7-112">Der räumliche Sound ist nicht mit dem typischen Sound vergleichbar, den Sie im Radio hören würden, es handelt sich um Sound, der in 3D-Raum positioniert ist.</span><span class="sxs-lookup"><span data-stu-id="329e7-112">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="329e7-113">Mit räumlichem Sound können Sie holograms so gestalten, wie Sie sich hinter ihnen befinden, oder auch auf Ihrem Kopf!</span><span class="sxs-lookup"><span data-stu-id="329e7-113">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="329e7-114">In diesem Kurs werden Sie wie folgt vorgehen:</span><span class="sxs-lookup"><span data-stu-id="329e7-114">In this course, you will:</span></span>

* <span data-ttu-id="329e7-115">Konfigurieren Sie Ihre Entwicklungsumgebung für die Verwendung von Microsoft Spatial Sound.</span><span class="sxs-lookup"><span data-stu-id="329e7-115">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="329e7-116">Verwenden Sie räumliche Töne, um Interaktionen zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="329e7-116">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="329e7-117">Verwenden Sie räumliche Sounds in Verbindung mit [räumlicher Zuordnung](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="329e7-117">Use Spatial Sound in conjunction with [Spatial Mapping](spatial-mapping.md).</span></span>
* <span data-ttu-id="329e7-118">Informieren Sie sich über die bewährten Vorgehensweisen zum Entwerfen und mischen</span><span class="sxs-lookup"><span data-stu-id="329e7-118">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="329e7-119">Verwenden Sie Sound, um besondere Effekte zu verbessern und den Benutzer in die gemischte Realität zu bringen.</span><span class="sxs-lookup"><span data-stu-id="329e7-119">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="329e7-120">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="329e7-120">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="329e7-121">Natürlich</span><span class="sxs-lookup"><span data-stu-id="329e7-121">Course</span></span></th><th style="width:150px"> <span data-ttu-id="329e7-122"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="329e7-122"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="329e7-123"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="329e7-123"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="329e7-124">Mr Spatial 220: räumlicher Sound</span><span class="sxs-lookup"><span data-stu-id="329e7-124">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="329e7-125">✔️</span><span class="sxs-lookup"><span data-stu-id="329e7-125">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="329e7-126">✔️</span><span class="sxs-lookup"><span data-stu-id="329e7-126">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="329e7-127">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="329e7-127">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="329e7-128">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="329e7-128">Prerequisites</span></span>

* <span data-ttu-id="329e7-129">Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md)konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="329e7-129">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="329e7-130">Einige Grund C# Legende Programmiermöglichkeiten.</span><span class="sxs-lookup"><span data-stu-id="329e7-130">Some basic C# programming ability.</span></span>
* <span data-ttu-id="329e7-131">Sie sollten die [Grundlagen von 101](holograms-101.md)abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="329e7-131">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="329e7-132">Ein hololens-Gerät, das [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode)ist.</span><span class="sxs-lookup"><span data-stu-id="329e7-132">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="329e7-133">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="329e7-133">Project files</span></span>

* <span data-ttu-id="329e7-134">Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) , die für das Projekt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="329e7-134">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="329e7-135"> Erfordert Unity 2017,2 oder höher.</span><span class="sxs-lookup"><span data-stu-id="329e7-135"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="329e7-136">Wenn Sie weiterhin Unity 5,6-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span><span class="sxs-lookup"><span data-stu-id="329e7-136">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="329e7-137">Diese Version ist möglicherweise nicht mehr auf dem neuesten Stand.</span><span class="sxs-lookup"><span data-stu-id="329e7-137">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="329e7-138">Wenn Sie weiterhin Unity 5,5-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span><span class="sxs-lookup"><span data-stu-id="329e7-138">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="329e7-139"> Diese Version ist möglicherweise nicht mehr auf dem neuesten Stand.</span><span class="sxs-lookup"><span data-stu-id="329e7-139"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="329e7-140">Wenn Sie weiterhin Unity 5,4-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span><span class="sxs-lookup"><span data-stu-id="329e7-140">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="329e7-141"> Diese Version ist möglicherweise nicht mehr auf dem neuesten Stand.</span><span class="sxs-lookup"><span data-stu-id="329e7-141"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="329e7-142">Deinstallieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht zugänglichen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="329e7-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="329e7-143">Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span><span class="sxs-lookup"><span data-stu-id="329e7-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="329e7-144">Errata und Notizen</span><span class="sxs-lookup"><span data-stu-id="329e7-144">Errata and Notes</span></span>

* <span data-ttu-id="329e7-145">"Enable nur eigenen Code" muss in Visual Studio unter "Extras-> Optionen" deaktiviert*werden (>* Debuggen, um Breakpoints im Code zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="329e7-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="329e7-146">Kapitel 1: Einrichtung von Unity</span><span class="sxs-lookup"><span data-stu-id="329e7-146">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="329e7-147">Ziele</span><span class="sxs-lookup"><span data-stu-id="329e7-147">Objectives</span></span>

* <span data-ttu-id="329e7-148">Ändern Sie die Sound Konfiguration von Unity, sodass Sie Microsoft Spatial Sound verwendet.</span><span class="sxs-lookup"><span data-stu-id="329e7-148">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="329e7-149">Hinzufügen eines 3D-Sounds zu einem Objekt in Unity.</span><span class="sxs-lookup"><span data-stu-id="329e7-149">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="329e7-150">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="329e7-150">Instructions</span></span>

* <span data-ttu-id="329e7-151">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="329e7-151">Start Unity.</span></span>
* <span data-ttu-id="329e7-152">Wählen Sie **Öffnen**aus.</span><span class="sxs-lookup"><span data-stu-id="329e7-152">Select **Open**.</span></span>
* <span data-ttu-id="329e7-153">Navigieren Sie zu Ihrem Desktop, und suchen Sie den Ordner, den Sie zuvor nicht archiviert haben.</span><span class="sxs-lookup"><span data-stu-id="329e7-153">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="329e7-154">Klicken Sie auf den Ordner **starting\decibel** , und klicken Sie dann auf die Schaltfläche **Ordner auswählen** .</span><span class="sxs-lookup"><span data-stu-id="329e7-154">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="329e7-155">Warten Sie, bis das Projekt in Unity geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="329e7-155">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="329e7-156">Öffnen Sie im **Projekt** Panel **scenes\decibel.unity**.</span><span class="sxs-lookup"><span data-stu-id="329e7-156">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="329e7-157">Erweitern Sie im Bereich **Hierarchie** den Knoten **hologrammcollection** , und wählen Sie **P0LY**aus.</span><span class="sxs-lookup"><span data-stu-id="329e7-157">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="329e7-158">Erweitern Sie im Inspektor den Eintrag **audiosource** , und beachten Sie, dass kein **spatialize** -Kontrollkästchen vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="329e7-158">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="329e7-159">Standardmäßig lädt Unity kein spatializer-Plug-in.</span><span class="sxs-lookup"><span data-stu-id="329e7-159">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="329e7-160">Mit den folgenden Schritten wird räumlicher Sound im Projekt aktiviert.</span><span class="sxs-lookup"><span data-stu-id="329e7-160">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="329e7-161">Wechseln Sie im oberen Menü von Unity zu **Edit > Project Settings > Audiodatei**.</span><span class="sxs-lookup"><span data-stu-id="329e7-161">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="329e7-162">Suchen Sie nach der Dropdown Liste **spatializer Plugin** , und wählen Sie **MS HRTF spatializer**aus.</span><span class="sxs-lookup"><span data-stu-id="329e7-162">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="329e7-163">Wählen Sie im Bereich **Hierarchie** die Option **hologramcollection > P0LY**aus.</span><span class="sxs-lookup"><span data-stu-id="329e7-163">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="329e7-164">Suchen Sie im **Inspektor** -Panel die Komponente **Audioquelle** .</span><span class="sxs-lookup"><span data-stu-id="329e7-164">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="329e7-165">Aktivieren Sie das Kontrollkästchen **spatialize** .</span><span class="sxs-lookup"><span data-stu-id="329e7-165">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="329e7-166">Ziehen Sie den Schieberegler **räumlichkeits** Weise in **3D**, oder geben Sie 1 in das Bearbeitungsfeld **ein** .</span><span class="sxs-lookup"><span data-stu-id="329e7-166">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="329e7-167">Wir erstellen nun das Projekt in Unity und konfigurieren die Projekt Mappe in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="329e7-167">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="329e7-168">Wählen Sie in Unity **Datei > Buildeinstellungen**aus.</span><span class="sxs-lookup"><span data-stu-id="329e7-168">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="329e7-169">Klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="329e7-169">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="329e7-170">Wählen Sie in der Liste **Plattform** **universelle Windows-Plattform** aus, und klicken Sie auf **Plattform wechseln**.</span><span class="sxs-lookup"><span data-stu-id="329e7-170">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="329e7-171">Wenn Sie speziell für hololens entwickeln, legen Sie **Zielgerät** auf **hololens**fest.</span><span class="sxs-lookup"><span data-stu-id="329e7-171">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="329e7-172">Andernfalls sollten Sie es auf **jedem Gerät**belassen.</span><span class="sxs-lookup"><span data-stu-id="329e7-172">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="329e7-173">Stellen Sie sicher, dass der **Buildtyp** auf **D3D** und das **SDK** auf **Latest installiert** festgelegt ist (was SDK 16299 oder höher sein sollte).</span><span class="sxs-lookup"><span data-stu-id="329e7-173">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="329e7-174">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="329e7-174">Click **Build**.</span></span>
7. <span data-ttu-id="329e7-175">Erstellen Sie einen **neuen Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="329e7-175">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="329e7-176">Klicken Sie einfach auf den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="329e7-176">Single click the **App** folder.</span></span>
9. <span data-ttu-id="329e7-177">Drücken **Sie Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="329e7-177">Press **Select Folder**.</span></span>

<span data-ttu-id="329e7-178">Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="329e7-178">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="329e7-179">Öffnen Sie den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="329e7-179">Open the **App** folder.</span></span>
2. <span data-ttu-id="329e7-180">Öffnen Sie die Projekt Mappe **Decibel Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="329e7-180">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="329e7-181">Bei der Bereitstellung in hololens:</span><span class="sxs-lookup"><span data-stu-id="329e7-181">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="329e7-182">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x86**.</span><span class="sxs-lookup"><span data-stu-id="329e7-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="329e7-183">Klicken Sie auf den Dropdown Pfeil neben der Schaltfläche lokaler Computer, und wählen Sie **Remote Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="329e7-183">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="329e7-184">Geben Sie **die IP-Adresse des hololens-Geräts** ein, und legen Sie den Authentifizierungsmodus auf **Universal (unverschlüsseltes Protokoll)**</span><span class="sxs-lookup"><span data-stu-id="329e7-184">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="329e7-185">Klicken Sie auf **Auswählen**.</span><span class="sxs-lookup"><span data-stu-id="329e7-185">Click **Select**.</span></span> <span data-ttu-id="329e7-186">Wenn Sie die IP-Adresse Ihres Geräts nicht kennen, suchen Sie unter **Einstellungen > Netzwerk & Internet > Erweiterte Optionen**.</span><span class="sxs-lookup"><span data-stu-id="329e7-186">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="329e7-187">Klicken Sie in der oberen Menüleiste auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="329e7-187">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="329e7-188">Wenn Sie die Bereitstellung auf Ihrem Gerät zum ersten Mal durchführt, müssen Sie [es mit Visual Studio](using-visual-studio.md#pairing-your-device)koppeln.</span><span class="sxs-lookup"><span data-stu-id="329e7-188">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>

<span data-ttu-id="329e7-189">Bei der Bereitstellung auf einem immersiven Headset:</span><span class="sxs-lookup"><span data-stu-id="329e7-189">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="329e7-190">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x64**.</span><span class="sxs-lookup"><span data-stu-id="329e7-190">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="329e7-191">Stellen Sie sicher, dass das Bereitstellungs Ziel auf **lokaler Computer**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="329e7-191">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="329e7-192">Klicken Sie in der oberen Menüleiste auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="329e7-192">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="329e7-193">Kapitel 2: räumlicher Sound und Interaktion</span><span class="sxs-lookup"><span data-stu-id="329e7-193">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="329e7-194">Ziele</span><span class="sxs-lookup"><span data-stu-id="329e7-194">Objectives</span></span>

* <span data-ttu-id="329e7-195">Verbessern Sie das – Hologramm-Realismus mithilfe von Sound.</span><span class="sxs-lookup"><span data-stu-id="329e7-195">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="329e7-196">Leiten Sie den Benutzer Blick mithilfe von Sound weiter.</span><span class="sxs-lookup"><span data-stu-id="329e7-196">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="329e7-197">Stellen Sie Gesten Feedback mit Sound bereit.</span><span class="sxs-lookup"><span data-stu-id="329e7-197">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="329e7-198">Teil 1: verbessern des Realismus</span><span class="sxs-lookup"><span data-stu-id="329e7-198">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="329e7-199">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="329e7-199">Key Concepts</span></span>

* <span data-ttu-id="329e7-200">Räumalisieren Sie – Hologramm-Sounds.</span><span class="sxs-lookup"><span data-stu-id="329e7-200">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="329e7-201">Audioquellen sollten an einem geeigneten Speicherort auf dem Hologram abgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="329e7-201">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="329e7-202">Der richtige Speicherort für den Sound hängt von dem Hologram ab.</span><span class="sxs-lookup"><span data-stu-id="329e7-202">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="329e7-203">Wenn das – Hologramm z. b. von einem Menschen ist, sollte sich die Audioquelle nahe dem Mund und nicht der Fußzeile befinden.</span><span class="sxs-lookup"><span data-stu-id="329e7-203">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="329e7-204">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="329e7-204">Instructions</span></span>

<span data-ttu-id="329e7-205">Die folgenden Anweisungen fügen einen räumlichen Sound an ein Hologramm an.</span><span class="sxs-lookup"><span data-stu-id="329e7-205">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="329e7-206">Erweitern Sie im Bereich **Hierarchie** den Knoten **hologrammcollection** , und wählen Sie **P0LY**aus.</span><span class="sxs-lookup"><span data-stu-id="329e7-206">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="329e7-207">Klicken Sie im Bereich **Inspector** in der **audiosource**auf den Kreis neben **Audioclip** , und wählen Sie im Popup Fenster **polyhover** aus.</span><span class="sxs-lookup"><span data-stu-id="329e7-207">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="329e7-208">Klicken Sie auf den Kreis neben **Ausgabe** , und wählen Sie im Popup Fenster **soundeffects** aus.</span><span class="sxs-lookup"><span data-stu-id="329e7-208">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="329e7-209">Project Decibel verwendet eine Unity- **Audiomixer** -Komponente, um das Anpassen von Sound Ebenen für Gruppen von Sounds zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="329e7-209">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="329e7-210">Durch das Gruppieren von Sounds auf diese Weise kann das Gesamt Volume angepasst werden, während die relative Menge der einzelnen Sounds beibehalten wird.</span><span class="sxs-lookup"><span data-stu-id="329e7-210">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="329e7-211">Erweitern Sie in der **audiosource** **3D Sound Settings**.</span><span class="sxs-lookup"><span data-stu-id="329e7-211">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="329e7-212">Legen Sie die **Doppler-Ebene** auf **0**fest.</span><span class="sxs-lookup"><span data-stu-id="329e7-212">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="329e7-213">Durch das Festlegen von Doppler-Level auf NULL werden die Änderungen in der durch Bewegung (entweder im – Hologramm oder im Benutzer) verursachten Tonhöhe deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="329e7-213">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="329e7-214">Ein klassisches Beispiel für Doppler ist ein schnell beweglicher Wagen.</span><span class="sxs-lookup"><span data-stu-id="329e7-214">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="329e7-215">Wenn sich das Auto auf einen stationären Listener nähert, steigt die Tonhöhe der Engine.</span><span class="sxs-lookup"><span data-stu-id="329e7-215">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="329e7-216">Wenn Sie den Listener übergibt, wird die-Tonhöhe mit Distance gesenkt.</span><span class="sxs-lookup"><span data-stu-id="329e7-216">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="329e7-217">Teil 2: leiten des Benutzer Blicks</span><span class="sxs-lookup"><span data-stu-id="329e7-217">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="329e7-218">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="329e7-218">Key Concepts</span></span>

* <span data-ttu-id="329e7-219">Verwenden Sie Sound, um auf wichtige holograms aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="329e7-219">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="329e7-220">Die Ohren helfen Ihnen, den Augenblick zu lenken.</span><span class="sxs-lookup"><span data-stu-id="329e7-220">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="329e7-221">Das Gehirn hat einige Erwartungen gelernt.</span><span class="sxs-lookup"><span data-stu-id="329e7-221">The brain has some learned expectations.</span></span>

<span data-ttu-id="329e7-222">Ein Beispiel für die gewonnenen Erwartungen ist, dass die Vögel in der Regel über den Köpfen der Menschen sind.</span><span class="sxs-lookup"><span data-stu-id="329e7-222">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="329e7-223">Wenn ein Benutzer ein vogelton hört, besteht die anfängliche Reaktion darin, nach oben zu suchen.</span><span class="sxs-lookup"><span data-stu-id="329e7-223">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="329e7-224">Das Platzieren eines Vogels unterhalb des Benutzers kann dazu führen, dass er mit der richtigen Richtung des Sounds zurechtkommt, aber das – Hologramm nicht finden kann, je nachdem, dass er gesucht werden muss.</span><span class="sxs-lookup"><span data-stu-id="329e7-224">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="329e7-225">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="329e7-225">Instructions</span></span>

<span data-ttu-id="329e7-226">Mithilfe der folgenden Anweisungen können Sie P0LY hinter Ihnen verbergen, damit Sie den Sound verwenden können, um das Hologram zu suchen.</span><span class="sxs-lookup"><span data-stu-id="329e7-226">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="329e7-227">Wählen Sie im Bereich **Hierarchie** die Option **Manager**aus.</span><span class="sxs-lookup"><span data-stu-id="329e7-227">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="329e7-228">Suchen Sie im **Inspektor** -Panel den **Spracheingabe Handler**.</span><span class="sxs-lookup"><span data-stu-id="329e7-228">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="329e7-229">Erweitern Sie im **Spracheingabe Handler**den Bereich **Gehe ausblenden**.</span><span class="sxs-lookup"><span data-stu-id="329e7-229">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="329e7-230">Ändern Sie **keine Funktion** in **polyactions. gohide**.</span><span class="sxs-lookup"><span data-stu-id="329e7-230">Change **No Function** to **PolyActions.GoHide**.</span></span>

![Schlüsselwort: gehe ausblenden](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="329e7-232">Teil 3: Gesten Feedback</span><span class="sxs-lookup"><span data-stu-id="329e7-232">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="329e7-233">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="329e7-233">Key Concepts</span></span>

* <span data-ttu-id="329e7-234">Bereitstellen von positiver Gesten Bestätigung mit Sound</span><span class="sxs-lookup"><span data-stu-id="329e7-234">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="329e7-235">Bewegen Sie die Benutzer übermäßig lauter Sounds nicht auf die gleiche Weise</span><span class="sxs-lookup"><span data-stu-id="329e7-235">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="329e7-236">Feine Sounds funktionieren am besten</span><span class="sxs-lookup"><span data-stu-id="329e7-236">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="329e7-237">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="329e7-237">Instructions</span></span>

* <span data-ttu-id="329e7-238">Erweitern Sie im Bereich **Hierarchie** den Knoten **hologrammcollection**.</span><span class="sxs-lookup"><span data-stu-id="329e7-238">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="329e7-239">Erweitern Sie **energyhub** , und wählen Sie **Basis**aus.</span><span class="sxs-lookup"><span data-stu-id="329e7-239">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="329e7-240">Klicken Sie im **Inspektor** -Panel auf **Komponente hinzufügen** , und fügen Sie **Gesten Sound Handler**hinzu.</span><span class="sxs-lookup"><span data-stu-id="329e7-240">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="329e7-241">Klicken Sie in **Gesten Sound Handler**auf den Kreis neben **Navigation Started Clip** und **Navigation aktualisierte Clip** , und wählen Sie im Popup Fenster für beide den Bereich **rotateclick** aus.</span><span class="sxs-lookup"><span data-stu-id="329e7-241">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="329e7-242">Doppelklicken Sie auf "gesturesound Handler", um in Visual Studio zu laden.</span><span class="sxs-lookup"><span data-stu-id="329e7-242">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="329e7-243">Der Gesten Sound Handler führt die folgenden Aufgaben aus:</span><span class="sxs-lookup"><span data-stu-id="329e7-243">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="329e7-244">Erstellen und konfigurieren Sie eine **audiosource**.</span><span class="sxs-lookup"><span data-stu-id="329e7-244">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="329e7-245">Platzieren Sie die **audiosource** an der Position des entsprechenden **gameobject**.</span><span class="sxs-lookup"><span data-stu-id="329e7-245">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="329e7-246">Gibt den **Audioclip** wieder, der mit der Geste verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="329e7-246">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="329e7-247">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="329e7-247">Build and Deploy</span></span>

1. <span data-ttu-id="329e7-248">Wählen Sie in Unity **Datei > Buildeinstellungen**aus.</span><span class="sxs-lookup"><span data-stu-id="329e7-248">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="329e7-249">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="329e7-249">Click **Build**.</span></span>
3. <span data-ttu-id="329e7-250">Klicken Sie einfach auf den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="329e7-250">Single click the **App** folder.</span></span>
4. <span data-ttu-id="329e7-251">Drücken **Sie Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="329e7-251">Press **Select Folder**.</span></span>

<span data-ttu-id="329e7-252">Überprüfen Sie, ob die Symbolleiste "Release", "x86", "x64" und "Remote Gerät" heißt.</span><span class="sxs-lookup"><span data-stu-id="329e7-252">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="329e7-253">Wenn dies nicht der Fall ist, ist dies die Codierungs Instanz von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="329e7-253">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="329e7-254">Möglicherweise müssen Sie die Projekt Mappe aus dem App-Ordner erneut öffnen.</span><span class="sxs-lookup"><span data-stu-id="329e7-254">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="329e7-255">Wenn Sie dazu aufgefordert werden, laden Sie die Projektdateien erneut</span><span class="sxs-lookup"><span data-stu-id="329e7-255">If prompted, reload the project files.</span></span>
* <span data-ttu-id="329e7-256">Stellen Sie wie zuvor über Visual Studio bereit.</span><span class="sxs-lookup"><span data-stu-id="329e7-256">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="329e7-257">Nachdem die Anwendung bereitgestellt wurde:</span><span class="sxs-lookup"><span data-stu-id="329e7-257">After the application is deployed:</span></span>

* <span data-ttu-id="329e7-258">Beobachten Sie, wie sich der Sound bei der Umstellung auf P0LY ändert.</span><span class="sxs-lookup"><span data-stu-id="329e7-258">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="329e7-259">Sagen Sie *"go hide" (ausblenden* ), um P0LY zu einem Speicherort hinter Ihnen zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="329e7-259">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="329e7-260">Suchen Sie nach dem Sound.</span><span class="sxs-lookup"><span data-stu-id="329e7-260">Find it by the sound.</span></span>
* <span data-ttu-id="329e7-261">Schauen Sie sich die Basis des Energy Hubs an.</span><span class="sxs-lookup"><span data-stu-id="329e7-261">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="329e7-262">Tippen und ziehen Sie nach links oder rechts, um das – Hologramm zu drehen, und sehen Sie, wie der Klick Sound die Geste bestätigt.</span><span class="sxs-lookup"><span data-stu-id="329e7-262">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="329e7-263">Hinweis: Es gibt einen Textbereich, der mit Ihnen versehen wird.</span><span class="sxs-lookup"><span data-stu-id="329e7-263">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="329e7-264">Diese werden die verfügbaren Sprachbefehle enthalten, die Sie in diesem Kurs verwenden können.</span><span class="sxs-lookup"><span data-stu-id="329e7-264">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="329e7-265">Kapitel 3: räumliche und räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="329e7-265">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="329e7-266">Ziele</span><span class="sxs-lookup"><span data-stu-id="329e7-266">Objectives</span></span>

* <span data-ttu-id="329e7-267">Bestätigen Sie die Interaktion zwischen holograms und der realen Welt mit Sound.</span><span class="sxs-lookup"><span data-stu-id="329e7-267">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="329e7-268">Verwenden Sie den Sound mit der physischen Welt.</span><span class="sxs-lookup"><span data-stu-id="329e7-268">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="329e7-269">Teil 1-physische Welt Interaktion</span><span class="sxs-lookup"><span data-stu-id="329e7-269">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="329e7-270">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="329e7-270">Key Concepts</span></span>

* <span data-ttu-id="329e7-271">Physische Objekte machen im Allgemeinen einen Sound, wenn Sie auf eine Oberfläche oder ein anderes Objekt stoßen.</span><span class="sxs-lookup"><span data-stu-id="329e7-271">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="329e7-272">Sounds sollte Kontext freundlich sein.</span><span class="sxs-lookup"><span data-stu-id="329e7-272">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="329e7-273">Beispielsweise sollte das Festlegen eines Cup für eine Tabelle einen ruhigeren Sound als das Löschen eines Boulders auf einem Metal-Gerät machen.</span><span class="sxs-lookup"><span data-stu-id="329e7-273">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="329e7-274">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="329e7-274">Instructions</span></span>

* <span data-ttu-id="329e7-275">Erweitern Sie im Bereich **Hierarchie** den Knoten **hologrammcollection**.</span><span class="sxs-lookup"><span data-stu-id="329e7-275">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="329e7-276">Erweitern Sie **energyhub**, und wählen Sie **Basis**aus.</span><span class="sxs-lookup"><span data-stu-id="329e7-276">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="329e7-277">Klicken Sie im **Inspektor** -Panel auf **Komponente hinzufügen** , und fügen Sie **mit Sound und Action Tap**hinzu.</span><span class="sxs-lookup"><span data-stu-id="329e7-277">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="329e7-278">**Tippen Sie auf, um mit Sound und Action zu platzieren**:</span><span class="sxs-lookup"><span data-stu-id="329e7-278">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="329e7-279">Aktivieren Sie **übergeordnetes Element bei tippen**.</span><span class="sxs-lookup"><span data-stu-id="329e7-279">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="329e7-280">Legen Sie **Platzierungs Sound** auf **platzieren**fest.</span><span class="sxs-lookup"><span data-stu-id="329e7-280">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="329e7-281">Legen Sie **Pickup Sound** auf **Pickup**fest.</span><span class="sxs-lookup"><span data-stu-id="329e7-281">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="329e7-282">Drücken Sie die Taste + unten rechts unter sowohl **bei der** Aufnahme-als auch bei der **Platzierungs Aktion**.</span><span class="sxs-lookup"><span data-stu-id="329e7-282">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="329e7-283">Ziehen Sie energyhub aus der Szene in die Felder **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="329e7-283">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="329e7-284">Klicken Sie unter **on Pickup Action**auf **No Function** -> **energyhubbase** -> **resettanimation.**</span><span class="sxs-lookup"><span data-stu-id="329e7-284">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="329e7-285">Klicken Sie unter **Platzierungs Aktion**auf **keine Funktion** -> **energyhubbase** -> **onselect**.</span><span class="sxs-lookup"><span data-stu-id="329e7-285">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![Mit Sound und Action tippen](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="329e7-287">Teil 2: Sound Okklusion</span><span class="sxs-lookup"><span data-stu-id="329e7-287">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="329e7-288">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="329e7-288">Key Concepts</span></span>

* <span data-ttu-id="329e7-289">Sound, wie z. b. Light, können ausgeblendet werden.</span><span class="sxs-lookup"><span data-stu-id="329e7-289">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="329e7-290">Ein klassisches Beispiel ist eine Concert Hall.</span><span class="sxs-lookup"><span data-stu-id="329e7-290">A classic example is a concert hall.</span></span> <span data-ttu-id="329e7-291">Wenn ein Listener außerhalb der Halle steht und die Tür geschlossen ist, hört sich die Musik mit gedämpften Tönen an.</span><span class="sxs-lookup"><span data-stu-id="329e7-291">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="329e7-292">Es gibt in der Regel auch eine Reduzierung des Volumes.</span><span class="sxs-lookup"><span data-stu-id="329e7-292">There is also typically a reduction in volume.</span></span> <span data-ttu-id="329e7-293">Wenn die Tür geöffnet ist, wird das gesamte Spektrum des Sounds auf dem eigentlichen Volume gehört.</span><span class="sxs-lookup"><span data-stu-id="329e7-293">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="329e7-294">Sounds mit hoher Frequenz werden im Allgemeinen mehr als niedrige Frequenzen erfasst.</span><span class="sxs-lookup"><span data-stu-id="329e7-294">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="329e7-295">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="329e7-295">Instructions</span></span>

* <span data-ttu-id="329e7-296">Erweitern Sie im Bereich **Hierarchie** den Knoten **hologrammcollection** , und wählen Sie **P0LY**aus.</span><span class="sxs-lookup"><span data-stu-id="329e7-296">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="329e7-297">Klicken Sie im **Inspektor** -Panel auf **Komponente hinzufügen** , und fügen Sie **audioemitter**hinzu.</span><span class="sxs-lookup"><span data-stu-id="329e7-297">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="329e7-298">Die audioemitter-Klasse bietet die folgenden Features:</span><span class="sxs-lookup"><span data-stu-id="329e7-298">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="329e7-299">Stellt alle Änderungen am Volume der **audiosource**wieder her.</span><span class="sxs-lookup"><span data-stu-id="329e7-299">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="329e7-300">Führt eine " **Physik. raycastnonzuweisung** " aus der Position des Benutzers in der Richtung des **gameobject** aus, an das der **audioemitter** angefügt ist.</span><span class="sxs-lookup"><span data-stu-id="329e7-300">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="329e7-301">Die raycastnonalloc-Methode wird als Leistungsoptimierung verwendet, um Zuordnungen und die Anzahl der zurückgegebenen Ergebnisse einzuschränken.</span><span class="sxs-lookup"><span data-stu-id="329e7-301">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="329e7-302">Für jeden gefundenen **iaudioinflutercer** Ruft die **applyeffect** -Methode auf.</span><span class="sxs-lookup"><span data-stu-id="329e7-302">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="329e7-303">Für jeden vorherigen **iaudioinfludencer** , der nicht mehr gefunden wird, wird die **removeeffect** -Methode aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="329e7-303">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="329e7-304">Beachten Sie, dass audioemitter bei menschlichen Zeitskalen aktualisiert wird, im Gegensatz zu pro Frame.</span><span class="sxs-lookup"><span data-stu-id="329e7-304">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="329e7-305">Der Grund hierfür ist, dass Menschen im Allgemeinen nicht schnell genug verschieben, damit die Auswirkungen häufiger als jedes Quartal oder die Hälfte der Sekunde aktualisiert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="329e7-305">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="329e7-306">Hologramme, die schnell von einem Speicherort an einen anderen teleportieren, können die Illusion unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="329e7-306">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="329e7-307">Erweitern Sie im Bereich **Hierarchie** den Knoten **hologrammcollection**.</span><span class="sxs-lookup"><span data-stu-id="329e7-307">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="329e7-308">Erweitern Sie **energyhub** , und wählen Sie **blobaußen**aus.</span><span class="sxs-lookup"><span data-stu-id="329e7-308">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="329e7-309">Klicken Sie im **Inspektor** -Panel auf **Komponente hinzufügen** , und fügen Sie **audiookokder**hinzu.</span><span class="sxs-lookup"><span data-stu-id="329e7-309">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="329e7-310">Legen Sie in **audiookder**den Umstellungs **Frequenz** -Wert auf **1500**fest.</span><span class="sxs-lookup"><span data-stu-id="329e7-310">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="329e7-311">Diese Einstellung schränkt die audiosource-Frequenzen auf 1500 Hz und niedriger ein.</span><span class="sxs-lookup"><span data-stu-id="329e7-311">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="329e7-312">Legen Sie den **volumedurchlauf** auf **0,9**fest.</span><span class="sxs-lookup"><span data-stu-id="329e7-312">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="329e7-313">Mit dieser Einstellung wird das Volume der audiosource auf die aktuelle Ebene von 90% reduziert.</span><span class="sxs-lookup"><span data-stu-id="329e7-313">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="329e7-314">Der audiookton implementiert iaudioinflutencer für Folgendes:</span><span class="sxs-lookup"><span data-stu-id="329e7-314">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="329e7-315">Anwenden eines Okklusions Effekts mithilfe eines **audiolowpassfilter** , der an die **audiosource** angefügt wird, die den **audioemitter**kauft.</span><span class="sxs-lookup"><span data-stu-id="329e7-315">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="329e7-316">Wendet die volumedämpfung auf die audiosource an.</span><span class="sxs-lookup"><span data-stu-id="329e7-316">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="329e7-317">Deaktiviert den Effekt durch Festlegen einer neutralen Umstellungs Frequenz und Deaktivieren des Filters.</span><span class="sxs-lookup"><span data-stu-id="329e7-317">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="329e7-318">Die als neutral verwendete Häufigkeit ist 22 kHz (22000 Hz).</span><span class="sxs-lookup"><span data-stu-id="329e7-318">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="329e7-319">Diese Häufigkeit wurde gewählt, weil Sie über der maximalen maximalen Frequenz liegt, die vom menschlichen Ohr gehört werden kann, sodass keine erkennbaren Auswirkungen auf den Sound entstehen.</span><span class="sxs-lookup"><span data-stu-id="329e7-319">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="329e7-320">Wählen Sie im Bereich **Hierarchie** die Option **spatialmapping**aus.</span><span class="sxs-lookup"><span data-stu-id="329e7-320">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="329e7-321">Klicken Sie im **Inspektor** -Panel auf **Komponente hinzufügen** , und fügen Sie **audiookokder**hinzu.</span><span class="sxs-lookup"><span data-stu-id="329e7-321">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="329e7-322">Legen Sie in **audiookder**den Umstellungs **Frequenz** -Wert auf **750**fest.</span><span class="sxs-lookup"><span data-stu-id="329e7-322">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="329e7-323">Wenn sich mehrere okader im Pfad zwischen dem Benutzer und dem **audioemitter**befinden, wird die niedrigste Frequenz auf den Filter angewendet.</span><span class="sxs-lookup"><span data-stu-id="329e7-323">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="329e7-324">Legen Sie den **volumedurchlauf** auf **0,75**fest.</span><span class="sxs-lookup"><span data-stu-id="329e7-324">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="329e7-325">Wenn sich mehrere okader im Pfad zwischen dem Benutzer und dem **audioemitter**befinden, wird das Volume weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="329e7-325">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="329e7-326">Wählen Sie im Bereich **Hierarchie** die Option **Manager**aus.</span><span class="sxs-lookup"><span data-stu-id="329e7-326">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="329e7-327">Erweitern Sie im **Inspektor** -Panel den **Spracheingabe Handler**.</span><span class="sxs-lookup"><span data-stu-id="329e7-327">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="329e7-328">Erweitern Sie im **Spracheingabe Handler den Eintrag** **go-Belastung**.</span><span class="sxs-lookup"><span data-stu-id="329e7-328">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="329e7-329">Ändern Sie **keine Funktion** in **polyactions. goabgerechnet**.</span><span class="sxs-lookup"><span data-stu-id="329e7-329">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![Schlüsselwort: go](images/gocharge.png)

* <span data-ttu-id="329e7-331">Erweitern Sie **hier**.</span><span class="sxs-lookup"><span data-stu-id="329e7-331">Expand **Come Here**.</span></span>
* <span data-ttu-id="329e7-332">Ändern Sie **keine Funktion** in **polyactions. ComeBack**.</span><span class="sxs-lookup"><span data-stu-id="329e7-332">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![Schlüsselwort: hier](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="329e7-334">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="329e7-334">Build and Deploy</span></span>

* <span data-ttu-id="329e7-335">Erstellen Sie wie zuvor das Projekt in Unity, und stellen Sie es in Visual Studio bereit.</span><span class="sxs-lookup"><span data-stu-id="329e7-335">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="329e7-336">Nachdem die Anwendung bereitgestellt wurde:</span><span class="sxs-lookup"><span data-stu-id="329e7-336">After the application is deployed:</span></span>

* <span data-ttu-id="329e7-337">Sagen Sie *"Go-Kosten"* , damit P0LY den Energie-Hub eingeben.</span><span class="sxs-lookup"><span data-stu-id="329e7-337">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="329e7-338">Beachten Sie die Änderung des Sounds.</span><span class="sxs-lookup"><span data-stu-id="329e7-338">Note the change in the sound.</span></span> <span data-ttu-id="329e7-339">Dies sollte ein wenig leiser werden.</span><span class="sxs-lookup"><span data-stu-id="329e7-339">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="329e7-340">Wenn Sie sich in der Lage sind, sich mit einer Wand oder einem anderen Objekt zwischen Ihnen und dem Energie-Hub zu positionieren, sollten Sie aufgrund der Okklusion der realen Welt eine weitere Belastung des Sounds feststellen.</span><span class="sxs-lookup"><span data-stu-id="329e7-340">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="329e7-341">Sagen Sie, dass P0LY den Energie-Hub verlassen und sich vor Ihnen *Positionieren muss.*</span><span class="sxs-lookup"><span data-stu-id="329e7-341">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="329e7-342">Beachten Sie, dass die Sound Okklusion einmal entfernt wird P0LY beendet den Energie-Hub.</span><span class="sxs-lookup"><span data-stu-id="329e7-342">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="329e7-343">Wenn Sie immer noch mit der Okklusion hören, wird P0LY möglicherweise von der realen Welt ausgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="329e7-343">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="329e7-344">Versuchen Sie, die Umstellung durchführen zu lassen.</span><span class="sxs-lookup"><span data-stu-id="329e7-344">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="329e7-345">Teile von 3-Raum-Modellen</span><span class="sxs-lookup"><span data-stu-id="329e7-345">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="329e7-346">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="329e7-346">Key Concepts</span></span>

* <span data-ttu-id="329e7-347">Die Größe des Speicherplatzes bietet unter-Warteschlangen, die zur Sound Lokalisierung beitragen.</span><span class="sxs-lookup"><span data-stu-id="329e7-347">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="329e7-348">Raummodelle werden pro**audiosource**festgelegt.</span><span class="sxs-lookup"><span data-stu-id="329e7-348">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="329e7-349">Das [mixedrealitytoolkit für Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) stellt Code zum Festlegen des raummodells bereit.</span><span class="sxs-lookup"><span data-stu-id="329e7-349">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="329e7-350">Wählen Sie für gemischte Realität das Raummodell aus, das am besten zu dem realen Raum passt.</span><span class="sxs-lookup"><span data-stu-id="329e7-350">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="329e7-351">Wenn Sie ein virtuelles Reality-Szenario erstellen, wählen Sie das Raummodell aus, das für die virtuelle Umgebung am besten geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="329e7-351">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="329e7-352">Kapitel 4: Sound Design</span><span class="sxs-lookup"><span data-stu-id="329e7-352">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="329e7-353">Ziele</span><span class="sxs-lookup"><span data-stu-id="329e7-353">Objectives</span></span>

* <span data-ttu-id="329e7-354">Verstehen Sie die Überlegungen für den effektiven Sound Entwurf.</span><span class="sxs-lookup"><span data-stu-id="329e7-354">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="329e7-355">Erlernen Sie die Vorgehensweisen für das Mischen von Techniken</span><span class="sxs-lookup"><span data-stu-id="329e7-355">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="329e7-356">Teil 1: Sound und Erfahrungs Entwurf</span><span class="sxs-lookup"><span data-stu-id="329e7-356">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="329e7-357">In diesem Abschnitt werden die wichtigsten Überlegungen und Richtlinien für Sound und Design erläutert.</span><span class="sxs-lookup"><span data-stu-id="329e7-357">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="329e7-358">Alle Sounds normalisieren</span><span class="sxs-lookup"><span data-stu-id="329e7-358">Normalize all sounds</span></span>

<span data-ttu-id="329e7-359">Dadurch ist es nicht erforderlich, dass Sonderfallcode die volumeebenen pro Sound anpasst, was zeitaufwändig sein kann, und die Möglichkeit zum einfachen Aktualisieren von Sounddateien einschränkt.</span><span class="sxs-lookup"><span data-stu-id="329e7-359">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="329e7-360">Entwurf für eine unteschte Darstellung</span><span class="sxs-lookup"><span data-stu-id="329e7-360">Design for an untethered experience</span></span>

<span data-ttu-id="329e7-361">Hololens ist ein vollständig enthaltener holografischer Computer.</span><span class="sxs-lookup"><span data-stu-id="329e7-361">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="329e7-362">Ihre Benutzer können Ihre Erfahrungen während des Verschiebens nutzen und verwenden.</span><span class="sxs-lookup"><span data-stu-id="329e7-362">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="329e7-363">Testen Sie Ihre Audiomischung, indem Sie Sie durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="329e7-363">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="329e7-364">Ausgabe von logischen Speicherorten auf Ihren holograms</span><span class="sxs-lookup"><span data-stu-id="329e7-364">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="329e7-365">In der Praxis kommt ein Hund nicht von seinem Ende her, und die Stimme eines Menschen wird nicht von seinen Füßen entfernt.</span><span class="sxs-lookup"><span data-stu-id="329e7-365">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="329e7-366">Vermeiden Sie, dass Ihre Sounds aus unerwarteten teilen ihrer holograms ausgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="329e7-366">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="329e7-367">Bei kleinen holograms ist es sinnvoll, eine Soundausgabe aus der Mitte der Geometrie zu haben.</span><span class="sxs-lookup"><span data-stu-id="329e7-367">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="329e7-368">Vertraute Sounds sind die meisten lokalisierbaren Sounds</span><span class="sxs-lookup"><span data-stu-id="329e7-368">Familiar sounds are most localizable</span></span>

<span data-ttu-id="329e7-369">Die Menschen Sprache und Musik sind sehr einfach zu lokalisieren.</span><span class="sxs-lookup"><span data-stu-id="329e7-369">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="329e7-370">Wenn jemand Ihren Namen aufruft, können Sie genau feststellen, welche Richtung die Stimme erhalten hat und wie weit entfernt.</span><span class="sxs-lookup"><span data-stu-id="329e7-370">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="329e7-371">Kurze, unbekannte Sounds sind schwieriger zu lokalisieren.</span><span class="sxs-lookup"><span data-stu-id="329e7-371">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="329e7-372">Erkennen von Erwartungen von Benutzern</span><span class="sxs-lookup"><span data-stu-id="329e7-372">Be cognizant of user expectations</span></span>

<span data-ttu-id="329e7-373">Die Lebensdauer spielt einen Teil der Möglichkeit, den Speicherort eines Sounds zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="329e7-373">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="329e7-374">Dies ist ein Grund, warum die menschliche Stimme besonders leicht lokalisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="329e7-374">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="329e7-375">Es ist wichtig, dass Sie wissen, welche Erwartungen der Benutzer beim Platzieren Ihrer Sounds hat.</span><span class="sxs-lookup"><span data-stu-id="329e7-375">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="329e7-376">Wenn ein Benutzer beispielsweise einen vogelsong hört, sehen Sie sich im Allgemeinen an, da sich die Vögel in der Regel über der Sicht befinden (in der Struktur oder in einer Struktur).</span><span class="sxs-lookup"><span data-stu-id="329e7-376">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="329e7-377">Es ist nicht ungewöhnlich, dass ein Benutzer die korrekte Richtung eines Sounds einschaltet, aber in der falschen vertikalen Richtung sucht und verwirrt oder frustriert wird, wenn er das Hologram nicht finden kann.</span><span class="sxs-lookup"><span data-stu-id="329e7-377">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="329e7-378">Vermeiden Sie verborgene Emitter.</span><span class="sxs-lookup"><span data-stu-id="329e7-378">Avoid hidden emitters</span></span>

<span data-ttu-id="329e7-379">In der realen Welt können wir, wenn wir einen Sound hören, im Allgemeinen das Objekt identifizieren, das den Sound ausgibt.</span><span class="sxs-lookup"><span data-stu-id="329e7-379">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="329e7-380">Dies sollte auch für Ihre Erfahrungen sorgen.</span><span class="sxs-lookup"><span data-stu-id="329e7-380">This should also hold true in your experiences.</span></span> <span data-ttu-id="329e7-381">Es kann sehr stark sein, dass Benutzer einen Sound hören und wissen, woher der Sound stammt und ein Objekt nicht sehen kann.</span><span class="sxs-lookup"><span data-stu-id="329e7-381">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="329e7-382">Es gibt einige Ausnahmen zu dieser Richtlinie.</span><span class="sxs-lookup"><span data-stu-id="329e7-382">There are some exceptions to this guideline.</span></span> <span data-ttu-id="329e7-383">Umgebungs Klänge wie z. b. Crickets in einem Feld müssen z. b. nicht sichtbar sein.</span><span class="sxs-lookup"><span data-stu-id="329e7-383">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="329e7-384">Mit der Lebensdauer können wir uns mit der Quelle dieser Sounds vertraut machen, ohne Sie sehen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="329e7-384">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="329e7-385">Teil 2: Sound Mischung</span><span class="sxs-lookup"><span data-stu-id="329e7-385">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="329e7-386">Ziel ihrer Mischung für 70% Volume in den hololens</span><span class="sxs-lookup"><span data-stu-id="329e7-386">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="329e7-387">Gemischte Realität ermöglicht das Erkennen von holograms in der realen Welt.</span><span class="sxs-lookup"><span data-stu-id="329e7-387">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="329e7-388">Sie sollten auch das hören von echten Sounds erlauben.</span><span class="sxs-lookup"><span data-stu-id="329e7-388">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="329e7-389">Ein 70%-volumespeicherziel ermöglicht dem Benutzer, die Welt mit dem Sound Ihrer Benutzerumgebung zu hören.</span><span class="sxs-lookup"><span data-stu-id="329e7-389">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="329e7-390">Hololens bei 100% Volume sollten externe Sounds auslagern</span><span class="sxs-lookup"><span data-stu-id="329e7-390">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="329e7-391">Eine Volumeebene von 100% ist vergleichbar mit einer Virtual Reality-Darstellung.</span><span class="sxs-lookup"><span data-stu-id="329e7-391">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="329e7-392">Der Benutzer wird visuell in eine andere Welt transportiert.</span><span class="sxs-lookup"><span data-stu-id="329e7-392">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="329e7-393">Dasselbe sollte true sein.</span><span class="sxs-lookup"><span data-stu-id="329e7-393">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="329e7-394">Verwenden des Unity Audiomixer zum Anpassen von Sound Kategorien</span><span class="sxs-lookup"><span data-stu-id="329e7-394">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="329e7-395">Beim Entwerfen ihrer Mischung ist es häufig hilfreich, audiokategorien zu erstellen, und Sie können das Volume als Einheit vergrößern oder verkleinern.</span><span class="sxs-lookup"><span data-stu-id="329e7-395">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="329e7-396">Dies behält die relativen Ebenen jedes Sounds bei und ermöglicht gleichzeitig schnelle und einfache Änderungen an der gesamten Mischung.</span><span class="sxs-lookup"><span data-stu-id="329e7-396">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="329e7-397">Zu den allgemeinen Kategorien gehören: Soundeffekte, Ambiente, Sprachausgabe und Hintergrundmusik.</span><span class="sxs-lookup"><span data-stu-id="329e7-397">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="329e7-398">Sounds auf der Grundlage des Benutzer Blicks mischen</span><span class="sxs-lookup"><span data-stu-id="329e7-398">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="329e7-399">Häufig kann es hilfreich sein, die Sound Mischung in Ihrer Benutzer Darstellung zu ändern, je nachdem, wo ein Benutzer sucht (oder nicht).</span><span class="sxs-lookup"><span data-stu-id="329e7-399">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="329e7-400">Diese Technik wird häufig verwendet, um die Volumeebene für holograms zu verringern, die sich außerhalb des Holographic Frame befinden, um dem Benutzer die Möglichkeit zu geben, sich auf die darin vorgelagerten Informationen zu konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="329e7-400">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="329e7-401">Eine andere Verwendung besteht darin, das Volume eines Sounds zu vergrößern, um die Aufmerksamkeit des Benutzers auf ein wichtiges Ereignis zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="329e7-401">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="329e7-402">Entwickeln der Mischung</span><span class="sxs-lookup"><span data-stu-id="329e7-402">Building your mix</span></span>

<span data-ttu-id="329e7-403">Wenn Sie Ihre Mischung entwickeln, empfiehlt es sich, mit der Hintergrund Audiofunktion Ihrer Benutzererfahrung zu beginnen und Ebenen basierend auf der Wichtigkeit hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="329e7-403">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="329e7-404">Dies führt häufig dazu, dass jede Ebene lauter ist als die vorherige.</span><span class="sxs-lookup"><span data-stu-id="329e7-404">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="329e7-405">Wenn Sie Ihre Mischung als umgekehrten Trichter mit den geringsten wichtigen (und üblicherweise ruhigste Sounds) im unteren Bereich vorstellen, empfiehlt es sich, die Mischung ähnlich wie im folgenden Diagramm zu strukturieren.</span><span class="sxs-lookup"><span data-stu-id="329e7-405">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![Sound Mischungs Struktur](images/soundlevels.png)

<span data-ttu-id="329e7-407">Die Sprachausgabe ist ein interessantes Szenario.</span><span class="sxs-lookup"><span data-stu-id="329e7-407">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="329e7-408">Basierend auf der von Ihnen erstellten Benutzersprache möchten Sie möglicherweise einen Stereo-Sound (nicht lokalisiert) oder eine räumliche Sprache umgestalten.</span><span class="sxs-lookup"><span data-stu-id="329e7-408">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="329e7-409">Zwei veröffentlichte Microsoft-Erfahrungen veranschaulichen hervorragende Beispiele für jedes Szenario.</span><span class="sxs-lookup"><span data-stu-id="329e7-409">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="329e7-410">[Holotour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) verwendet eine Stereo Stimme über.</span><span class="sxs-lookup"><span data-stu-id="329e7-410">[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="329e7-411">Wenn die Sprachausgabe den Speicherort beschreibt, der angezeigt wird, ist der Sound konsistent und unterscheidet sich nicht je nach Position des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="329e7-411">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="329e7-412">Dadurch kann die Sprachausgabe die Szene beschreiben, ohne die räumlichen Klänge der Umgebung zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="329e7-412">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="329e7-413">[Fragmente](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) nutzt eine spatialisierte Stimme in Form eines Detektiven.</span><span class="sxs-lookup"><span data-stu-id="329e7-413">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="329e7-414">Die Stimme des Detektivs wird verwendet, um dem Benutzer einen wichtigen Hinweis zu vermitteln, als wäre ein tatsächlicher Mensch im Raum.</span><span class="sxs-lookup"><span data-stu-id="329e7-414">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="329e7-415">Dies bietet noch mehr Einblicke in die Möglichkeiten der Behebung des Geheimnisses.</span><span class="sxs-lookup"><span data-stu-id="329e7-415">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="329e7-416">Teil 3: Leistung</span><span class="sxs-lookup"><span data-stu-id="329e7-416">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="329e7-417">CPU-Auslastung</span><span class="sxs-lookup"><span data-stu-id="329e7-417">CPU usage</span></span>

<span data-ttu-id="329e7-418">Bei Verwendung von räumlichem Sound verbrauchen 10-12-Emitter ungefähr 12% der CPU.</span><span class="sxs-lookup"><span data-stu-id="329e7-418">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="329e7-419">Lange Audiodateien streamen</span><span class="sxs-lookup"><span data-stu-id="329e7-419">Stream long audio files</span></span>

<span data-ttu-id="329e7-420">Audiodaten können groß sein, insbesondere bei häufigen Stichproben Raten (44,1 und 48 kHz).</span><span class="sxs-lookup"><span data-stu-id="329e7-420">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="329e7-421">Eine allgemeine Regel ist, dass Audiodateien, die länger als 5-10 Sekunden sind, gestreamt werden sollten, um die Anwendungs Speicherauslastung zu reduzieren</span><span class="sxs-lookup"><span data-stu-id="329e7-421">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="329e7-422">In Unity können Sie eine Audiodatei für das Streaming in den Import Einstellungen der Datei markieren.</span><span class="sxs-lookup"><span data-stu-id="329e7-422">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![Audioimportierungseinstellungen](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="329e7-424">Kapitel 5: besondere Effekte</span><span class="sxs-lookup"><span data-stu-id="329e7-424">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="329e7-425">Ziele</span><span class="sxs-lookup"><span data-stu-id="329e7-425">Objectives</span></span>

* <span data-ttu-id="329e7-426">Fügen Sie "Magic Windows" Tiefe hinzu.</span><span class="sxs-lookup"><span data-stu-id="329e7-426">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="329e7-427">Bringen Sie den Benutzer in die virtuelle Welt.</span><span class="sxs-lookup"><span data-stu-id="329e7-427">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="329e7-428">Magische Fenster</span><span class="sxs-lookup"><span data-stu-id="329e7-428">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="329e7-429">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="329e7-429">Key Concepts</span></span>

* <span data-ttu-id="329e7-430">Das Erstellen von Ansichten in eine verborgene Welt ist visuell attraktiv.</span><span class="sxs-lookup"><span data-stu-id="329e7-430">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="329e7-431">Verbessern Sie die Realismus durch Hinzufügen von Audioeffekten, wenn ein – Hologramm oder der Benutzer sich in der Nähe der verborgenen Welt befindet</span><span class="sxs-lookup"><span data-stu-id="329e7-431">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="329e7-432">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="329e7-432">Instructions</span></span>

* <span data-ttu-id="329e7-433">Erweitern Sie im Bereich **Hierarchie** den Knoten **hologrammcollection** , und wählen Sie dann **Underworld**aus.</span><span class="sxs-lookup"><span data-stu-id="329e7-433">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="329e7-434">Erweitern Sie **Underworld** , und wählen Sie **voicesource**aus.</span><span class="sxs-lookup"><span data-stu-id="329e7-434">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="329e7-435">Klicken Sie im **Inspektor** -Panel auf **Komponente hinzufügen** , und fügen Sie den **Benutzer sprach Effekt**hinzu.</span><span class="sxs-lookup"><span data-stu-id="329e7-435">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="329e7-436">Eine **audiosource** -Komponente wird " **voicesource**" hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="329e7-436">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="329e7-437">Legen Sie in **audiosource** **Output** auf **UserVoice (Mixer)** fest.</span><span class="sxs-lookup"><span data-stu-id="329e7-437">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="329e7-438">Aktivieren Sie das Kontrollkästchen **spatialize** .</span><span class="sxs-lookup"><span data-stu-id="329e7-438">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="329e7-439">Ziehen Sie den Schieberegler **räumlichkeits** Weise in **3D**, oder geben Sie 1 in das Bearbeitungsfeld **ein** .</span><span class="sxs-lookup"><span data-stu-id="329e7-439">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="329e7-440">Erweitern Sie **3D-Sound Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="329e7-440">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="329e7-441">Legen Sie die **Doppler-Ebene** auf **0**fest.</span><span class="sxs-lookup"><span data-stu-id="329e7-441">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="329e7-442">Legen Sie unter **User Voice Effect**das über **geordnete Objekt** auf die **Unterwelt** aus der Szene fest.</span><span class="sxs-lookup"><span data-stu-id="329e7-442">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="329e7-443">Legen Sie **Max Distance** auf **1**fest.</span><span class="sxs-lookup"><span data-stu-id="329e7-443">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="329e7-444">Durch das Festlegen von " **Max Distance** " wird der **Benutzer** darüber informiert, wie nah der Benutzer auf das übergeordnete Objekt sein muss, bevor der Effekt aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="329e7-444">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="329e7-445">Erweitern Sie unter **User Voice Effect**den Eintrag **Chorus Parameters**.</span><span class="sxs-lookup"><span data-stu-id="329e7-445">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="329e7-446">Legen Sie die **Tiefe** auf **0,1**fest.</span><span class="sxs-lookup"><span data-stu-id="329e7-446">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="329e7-447">Legen Sie **Tap 1 Volume**, **Tap 2 Volume** und **3 Volume** auf **0,8**fest.</span><span class="sxs-lookup"><span data-stu-id="329e7-447">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="329e7-448">Legen Sie **ursprüngliches Sound Volume** auf **0,5**fest.</span><span class="sxs-lookup"><span data-stu-id="329e7-448">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="329e7-449">Mit den vorherigen Einstellungen werden die Parameter des Unity- **audiochor-Filters** konfiguriert, der verwendet wird, um die Stimme des Benutzers zu ergänzen.</span><span class="sxs-lookup"><span data-stu-id="329e7-449">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="329e7-450">Erweitern Sie unter **User Voice Effect**den Eintrag **Echo Parameters**.</span><span class="sxs-lookup"><span data-stu-id="329e7-450">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="329e7-451">**Verzögerung** auf **300** festlegen</span><span class="sxs-lookup"><span data-stu-id="329e7-451">Set **Delay** to **300**</span></span>
* <span data-ttu-id="329e7-452">Legen Sie das **Zerfalls Verhältnis** auf **0,2**fest.</span><span class="sxs-lookup"><span data-stu-id="329e7-452">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="329e7-453">Legen Sie **ursprüngliches Sound Volume** auf **0**fest.</span><span class="sxs-lookup"><span data-stu-id="329e7-453">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="329e7-454">Mit den vorherigen Einstellungen werden die Parameter des Unity- **audioechofilters** konfiguriert, der verwendet wird, um die Stimme des Benutzers zu spiegeln.</span><span class="sxs-lookup"><span data-stu-id="329e7-454">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="329e7-455">Das Skript für den Benutzer sprach Effekt ist für Folgendes zuständig:</span><span class="sxs-lookup"><span data-stu-id="329e7-455">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="329e7-456">Messen des Abstands zwischen dem Benutzer und dem **gameobject** , an das das Skript angefügt wird.</span><span class="sxs-lookup"><span data-stu-id="329e7-456">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="329e7-457">Es wird ermittelt, ob der Benutzer dem **gameobject-Objekt**zusteht.</span><span class="sxs-lookup"><span data-stu-id="329e7-457">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="329e7-458">Der Benutzer muss das gameobject-Objekt, unabhängig von der Entfernung, sehen, damit der Effekt aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="329e7-458">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="329e7-459">Anwenden und Konfigurieren eines **audiochor-Filters** und eines **audioechofilters** auf die **audiosource**.</span><span class="sxs-lookup"><span data-stu-id="329e7-459">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="329e7-460">Deaktivieren der Auswirkung durch Deaktivieren der Filter.</span><span class="sxs-lookup"><span data-stu-id="329e7-460">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="329e7-461">Der Benutzer sprach Effekt verwendet die MIC-Datenstrom Auswahl Komponente aus dem [mixedrealitytoolkit für Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), um den hochwertigen Voice-Stream auszuwählen und ihn in das Audiosystem von Unity weiterzuleiten.</span><span class="sxs-lookup"><span data-stu-id="329e7-461">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="329e7-462">Wählen Sie im Bereich **Hierarchie** die Option **Manager**aus.</span><span class="sxs-lookup"><span data-stu-id="329e7-462">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="329e7-463">Erweitern Sie im **Inspektor** -Panel den **Spracheingabe Handler**.</span><span class="sxs-lookup"><span data-stu-id="329e7-463">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="329e7-464">Erweitern Sie in **Spracheingabe Handler**die Option **Unterwelt anzeigen**.</span><span class="sxs-lookup"><span data-stu-id="329e7-464">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="329e7-465">Ändern Sie **keine Funktion** in " **underworldbase. onenable**".</span><span class="sxs-lookup"><span data-stu-id="329e7-465">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![Schlüsselwort: Unterwelt anzeigen](images/showunderworld.png)

* <span data-ttu-id="329e7-467">Erweitern Sie die Option **Unterwelt ausblenden**.</span><span class="sxs-lookup"><span data-stu-id="329e7-467">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="329e7-468">Ändern Sie **keine Funktion** in **underworldbase. ondeaktiviert**.</span><span class="sxs-lookup"><span data-stu-id="329e7-468">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![Schlüsselwort: Ausblenden der Unterwelt](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="329e7-470">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="329e7-470">Build and Deploy</span></span>

* <span data-ttu-id="329e7-471">Erstellen Sie wie zuvor das Projekt in Unity, und stellen Sie es in Visual Studio bereit.</span><span class="sxs-lookup"><span data-stu-id="329e7-471">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="329e7-472">Nachdem die Anwendung bereitgestellt wurde:</span><span class="sxs-lookup"><span data-stu-id="329e7-472">After the application is deployed:</span></span>

* <span data-ttu-id="329e7-473">Stellen Sie eine Oberfläche (Wall, Floor, Table) dar, und sagen Sie *"Show Underworld"* .</span><span class="sxs-lookup"><span data-stu-id="329e7-473">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="329e7-474">Die Unterwelt wird angezeigt, und alle anderen holograms werden ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="329e7-474">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="329e7-475">Wenn die Unterwelt nicht angezeigt wird, stellen Sie sicher, dass Sie mit der realen Oberfläche konfrontiert sind.</span><span class="sxs-lookup"><span data-stu-id="329e7-475">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="329e7-476">Ansatz innerhalb von 1 Meter des Unterwelt – Hologramm, und beginnen Sie mit der Kommunikation.</span><span class="sxs-lookup"><span data-stu-id="329e7-476">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="329e7-477">Es gibt jetzt Audioeffekte, die auf Ihre Stimme angewendet werden!</span><span class="sxs-lookup"><span data-stu-id="329e7-477">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="329e7-478">Schalten Sie die Unterwelt aus, und beachten Sie, dass der Effekt nicht mehr angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="329e7-478">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="329e7-479">Sagen Sie *"Unterwelt ausblenden"* , um die Unterwelt auszublenden.</span><span class="sxs-lookup"><span data-stu-id="329e7-479">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="329e7-480">Die Unterwelt wird ausgeblendet, und die zuvor ausgeblendeten holograms werden erneut angezeigt.</span><span class="sxs-lookup"><span data-stu-id="329e7-480">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="329e7-481">Das Ende</span><span class="sxs-lookup"><span data-stu-id="329e7-481">The End</span></span>

<span data-ttu-id="329e7-482">Gratulation!</span><span class="sxs-lookup"><span data-stu-id="329e7-482">Congratulations!</span></span> <span data-ttu-id="329e7-483">Sie haben jetzt den räumlichen **Ton 220: Spatial Sound**abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="329e7-483">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="329e7-484">Lauschen Sie auf die Welt, und bringen Sie Ihre Erfahrungen mit Sound!</span><span class="sxs-lookup"><span data-stu-id="329e7-484">Listen to the world and bring your experiences to life with sound!</span></span>
