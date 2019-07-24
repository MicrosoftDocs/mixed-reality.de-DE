---
title: Mr-Eingabe 210-Blick
description: Befolgen Sie diese exemplarische Vorgehensweise, indem Sie Unity, Visual Studio und hololens verwenden, um die Details von Blick Konzepten zu erlernen.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, Tutorial, Blick
ms.openlocfilehash: 076314389ec5ed70347c26d50c6a993f55da0758
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993546"
---
>[!NOTE]
><span data-ttu-id="200d0-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="200d0-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="200d0-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="200d0-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="200d0-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="200d0-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="200d0-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="200d0-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="200d0-108">Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="200d0-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="200d0-109">Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="200d0-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-210-gaze"></a><span data-ttu-id="200d0-110">Mr-Eingabe 210: Blickeingabe</span><span class="sxs-lookup"><span data-stu-id="200d0-110">MR Input 210: Gaze</span></span>

<span data-ttu-id="200d0-111">Der [Blick](gaze.md) ist die erste Form der Eingabe und zeigt die Absicht und das Bewusstsein des Benutzers an.</span><span class="sxs-lookup"><span data-stu-id="200d0-111">[Gaze](gaze.md) is the first form of input and reveals the user's intent and awareness.</span></span> <span data-ttu-id="200d0-112">Die Eingabe 210 (auch Projekt-Explorer genannt) ist ein tiefer Einblick in die im Blick zusammenhängenden Konzepte für Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="200d0-112">MR Input 210 (aka Project Explorer) is a deep dive into gaze-related concepts for Windows Mixed Reality.</span></span> <span data-ttu-id="200d0-113">Wir werden dem Cursor und holograms kontextbezogene Informationen hinzufügen und dabei die Vorteile der APP im Überblick über den Benutzer in vollem Umfang nutzen.</span><span class="sxs-lookup"><span data-stu-id="200d0-113">We will be adding contextual awareness to our cursor and holograms, taking full advantage of what your app knows about the user's gaze.</span></span>

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

<span data-ttu-id="200d0-114">Wir haben hier einen freundlichen Astronauten, der Sie beim Erlernen von Blick Konzepten unterstützt.</span><span class="sxs-lookup"><span data-stu-id="200d0-114">We have a friendly astronaut here to help you learn gaze concepts.</span></span> <span data-ttu-id="200d0-115">In den [Grundlagen 101](holograms-101.md)hatten wir einen einfachen Cursor, der genau auf Ihren Blick folgt.</span><span class="sxs-lookup"><span data-stu-id="200d0-115">In [MR Basics 101](holograms-101.md), we had a simple cursor that just followed your gaze.</span></span> <span data-ttu-id="200d0-116">Heute verschieben wir einen Schritt über den einfachen Cursor hinaus:</span><span class="sxs-lookup"><span data-stu-id="200d0-116">Today we're moving a step beyond the simple cursor:</span></span>

* <span data-ttu-id="200d0-117">Wir machen den Cursor und den holograms im Blick: Beide Änderungen ändern sich je nachdem, wo der Benutzer sucht oder wo der Benutzer *nicht* sucht.</span><span class="sxs-lookup"><span data-stu-id="200d0-117">We're making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is *not* looking.</span></span> <span data-ttu-id="200d0-118">Dies macht Sie Kontext abhängig.</span><span class="sxs-lookup"><span data-stu-id="200d0-118">This makes them context-aware.</span></span>
* <span data-ttu-id="200d0-119">Wir werden dem Cursor und holograms Feedback hinzufügen, um dem Benutzer mehr Kontext für das Ziel zu geben.</span><span class="sxs-lookup"><span data-stu-id="200d0-119">We will add feedback to our cursor and holograms to give the user more context on what is being targeted.</span></span> <span data-ttu-id="200d0-120">Dieses Feedback kann ein Audiomaterial und ein visuelles Element sein.</span><span class="sxs-lookup"><span data-stu-id="200d0-120">This feedback can be audio and visual.</span></span>
* <span data-ttu-id="200d0-121">Wir zeigen Ihnen gezielte Verfahren, mit denen Benutzer kleinere Ziele erreichen können.</span><span class="sxs-lookup"><span data-stu-id="200d0-121">We'll show you targeting techniques to help users hit smaller targets.</span></span>
* <span data-ttu-id="200d0-122">Wir zeigen Ihnen, wie Sie die Aufmerksamkeit des Benutzers auf die Hologramme mit einem direktionalen Indikator zeichnen.</span><span class="sxs-lookup"><span data-stu-id="200d0-122">We'll show you how to draw the user's attention to your holograms with a directional indicator.</span></span>
* <span data-ttu-id="200d0-123">Wir informieren Sie über Techniken, mit denen Sie Ihre Hologramme mit dem Benutzer übernehmen, wenn Sie sich in ihrer Welt bewegen.</span><span class="sxs-lookup"><span data-stu-id="200d0-123">We'll teach you techniques to take your holograms with the user as she moves around in your world.</span></span>

>[!IMPORTANT]
><span data-ttu-id="200d0-124">Die in den folgenden Kapiteln eingebetteten Videos wurden mit einer älteren Version von Unity und dem Mixed Reality Toolkit aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="200d0-124">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="200d0-125">Die Schritt-für-Schritt-Anweisungen sind genau und aktuell, aber es werden möglicherweise Skripts und Visualisierungen in den entsprechenden Videos angezeigt, die veraltet sind.</span><span class="sxs-lookup"><span data-stu-id="200d0-125">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="200d0-126">Die Videos bleiben in der einwelt enthalten und werden weiterhin angewendet.</span><span class="sxs-lookup"><span data-stu-id="200d0-126">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="200d0-127">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="200d0-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="200d0-128">Natürlich</span><span class="sxs-lookup"><span data-stu-id="200d0-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="200d0-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="200d0-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="200d0-130"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="200d0-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="200d0-131">Mr-Eingabe 210: Blickeingabe</span><span class="sxs-lookup"><span data-stu-id="200d0-131">MR Input 210: Gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="200d0-132">✔️</span><span class="sxs-lookup"><span data-stu-id="200d0-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="200d0-133">✔️</span><span class="sxs-lookup"><span data-stu-id="200d0-133">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="200d0-134">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="200d0-134">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="200d0-135">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="200d0-135">Prerequisites</span></span>

* <span data-ttu-id="200d0-136">Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md)konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="200d0-136">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="200d0-137">Einige Grund C# Legende Programmiermöglichkeiten.</span><span class="sxs-lookup"><span data-stu-id="200d0-137">Some basic C# programming ability.</span></span>
* <span data-ttu-id="200d0-138">Sie sollten die [Grundlagen von 101](holograms-101.md)abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="200d0-138">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="200d0-139">Ein hololens-Gerät, das [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode)ist.</span><span class="sxs-lookup"><span data-stu-id="200d0-139">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="200d0-140">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="200d0-140">Project files</span></span>

* <span data-ttu-id="200d0-141">Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) , die für das Projekt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="200d0-141">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) required by the project.</span></span><span data-ttu-id="200d0-142"> Erfordert Unity 2017,2 oder höher.</span><span class="sxs-lookup"><span data-stu-id="200d0-142"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="200d0-143">Deinstallieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht zugänglichen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="200d0-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="200d0-144">Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span><span class="sxs-lookup"><span data-stu-id="200d0-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="200d0-145">Errata und Notizen</span><span class="sxs-lookup"><span data-stu-id="200d0-145">Errata and Notes</span></span>

* <span data-ttu-id="200d0-146">In Visual Studio muss "nur eigenen Code" unter Extras-> Optionen-> Debuggen deaktiviert (deaktiviert) werden, um Breakpoints im Code zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="200d0-146">In Visual Studio, "Just My Code" needs to be disabled (unchecked) under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="200d0-147">Kapitel 1: Einrichtung von Unity</span><span class="sxs-lookup"><span data-stu-id="200d0-147">Chapter 1 - Unity Setup</span></span>

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a><span data-ttu-id="200d0-148">Ziele</span><span class="sxs-lookup"><span data-stu-id="200d0-148">Objectives</span></span>

* <span data-ttu-id="200d0-149">Optimieren von Unity für die HoloLens-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="200d0-149">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="200d0-150">Importieren von Assets und Einrichten der Szene</span><span class="sxs-lookup"><span data-stu-id="200d0-150">Import assets and setup the scene.</span></span>
* <span data-ttu-id="200d0-151">Anzeigen des Astronauten in den hololens.</span><span class="sxs-lookup"><span data-stu-id="200d0-151">View the astronaut in the HoloLens.</span></span>

### <a name="instructions"></a><span data-ttu-id="200d0-152">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="200d0-152">Instructions</span></span>

1. <span data-ttu-id="200d0-153">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="200d0-153">Start Unity.</span></span>
2. <span data-ttu-id="200d0-154">Wählen Sie **Neues Projekt**aus.</span><span class="sxs-lookup"><span data-stu-id="200d0-154">Select **New Project**.</span></span>
3. <span data-ttu-id="200d0-155">Nennen Sie das Projekt **Model Explorer**.</span><span class="sxs-lookup"><span data-stu-id="200d0-155">Name the project **ModelExplorer**.</span></span>
4. <span data-ttu-id="200d0-156">Geben Sie Location als **den Ordner** Folder ein, den Sie zuvor nicht archiviert haben.</span><span class="sxs-lookup"><span data-stu-id="200d0-156">Enter location as the **Gaze** folder you previously un-archived.</span></span>
5. <span data-ttu-id="200d0-157">Stellen Sie sicher, dass das Projekt auf **3D** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="200d0-157">Make sure the project is set to **3D**.</span></span>
6. <span data-ttu-id="200d0-158">Klicken Sie auf **Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="200d0-158">Click **Create Project**.</span></span>

### <a name="unity-settings-for-hololens"></a><span data-ttu-id="200d0-159">Unity-Einstellungen für hololens</span><span class="sxs-lookup"><span data-stu-id="200d0-159">Unity settings for HoloLens</span></span>

<span data-ttu-id="200d0-160">Wir müssen Unity mitteilen, dass die zu exportierende App eine [immersive Ansicht](app-views.md) anstelle einer 2D-Ansicht erstellen sollte.</span><span class="sxs-lookup"><span data-stu-id="200d0-160">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="200d0-161">Dies geschieht, indem hololens als Virtual Reality-Gerät hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="200d0-161">We do that by adding HoloLens as a virtual reality device.</span></span>

1. <span data-ttu-id="200d0-162">Wechseln Sie zu **Edit > Project Settings > Player**.</span><span class="sxs-lookup"><span data-stu-id="200d0-162">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="200d0-163">Wählen Sie im **Inspektor-Panel** für die Player Einstellungen das **Windows Store** -Symbol aus.</span><span class="sxs-lookup"><span data-stu-id="200d0-163">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="200d0-164">Erweitern Sie die Gruppe " **XR-Einstellungen** ".</span><span class="sxs-lookup"><span data-stu-id="200d0-164">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="200d0-165">Aktivieren Sie im Abschnitt " **Rendering** " das Kontrollkästchen " **Virtual Reality supported** ", um eine neue **Virtual Reality** -sdsliste hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="200d0-165">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="200d0-166">Vergewissern Sie sich, dass **Windows Mixed Reality** in der Liste angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="200d0-166">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="200d0-167">Wenn nicht, klicken Sie **+** auf die Schaltfläche unten in der Liste, und wählen Sie **Windows Holographic**aus.</span><span class="sxs-lookup"><span data-stu-id="200d0-167">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>

<span data-ttu-id="200d0-168">Als nächstes müssen wir unser Skript-Back-End auf .net festlegen.</span><span class="sxs-lookup"><span data-stu-id="200d0-168">Next, we need to set our scripting backend to .NET.</span></span>

1. <span data-ttu-id="200d0-169">Wechseln Sie zu **Edit > Project Settings > Player** (möglicherweise noch im vorherigen Schritt).</span><span class="sxs-lookup"><span data-stu-id="200d0-169">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="200d0-170">Wählen Sie im **Inspektor-Panel** für die Player Einstellungen das **Windows Store** -Symbol aus.</span><span class="sxs-lookup"><span data-stu-id="200d0-170">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="200d0-171">Stellen Sie sicher, dass im Konfigurations Abschnitt **andere Einstellungen** das Skript für die **Skript** Erstellung auf **.net** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="200d0-171">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="200d0-172">Zum Schluss aktualisieren wir unsere Qualitätseinstellungen, um eine schnelle Leistung in hololens zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="200d0-172">Finally, we'll update our quality settings to achieve a fast performance on HoloLens.</span></span>

1. <span data-ttu-id="200d0-173">Wechseln Sie zu **Edit > Project Settings > Quality**.</span><span class="sxs-lookup"><span data-stu-id="200d0-173">Go to **Edit > Project Settings > Quality**.</span></span>
2. <span data-ttu-id="200d0-174">Klicken Sie in der **Standard** Zeile unter dem Windows Store-Symbol auf den Pfeil nach unten.</span><span class="sxs-lookup"><span data-stu-id="200d0-174">Click on downward pointing arrow in the **Default** row under the Windows Store icon.</span></span>
3. <span data-ttu-id="200d0-175">Wählen Sie für **Windows Store-Apps** **sehr niedrig** aus.</span><span class="sxs-lookup"><span data-stu-id="200d0-175">Select **Very Low** for **Windows Store Apps**.</span></span>

### <a name="import-project-assets"></a><span data-ttu-id="200d0-176">Projekt Objekte importieren</span><span class="sxs-lookup"><span data-stu-id="200d0-176">Import project assets</span></span>

1. <span data-ttu-id="200d0-177">Klicken Sie im **Projekt** Panel mit der rechten Maustaste auf den Ordner **Assets** .</span><span class="sxs-lookup"><span data-stu-id="200d0-177">Right click the **Assets** folder in the **Project** panel.</span></span>
2. <span data-ttu-id="200d0-178">Klicken Sie auf **Paket importieren > benutzerdefiniertes Paket**.</span><span class="sxs-lookup"><span data-stu-id="200d0-178">Click on **Import Package > Custom Package**.</span></span>
3. <span data-ttu-id="200d0-179">Navigieren Sie zu den Projektdateien, die Sie heruntergeladen haben, und klicken Sie auf **modelexplorer. unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="200d0-179">Navigate to the project files you downloaded and click on **ModelExplorer.unitypackage**.</span></span>
4. <span data-ttu-id="200d0-180">Klicken Sie auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="200d0-180">Click **Open**.</span></span>
5. <span data-ttu-id="200d0-181">Nachdem das Paket geladen wurde, klicken Sie auf die Schaltfläche **importieren** .</span><span class="sxs-lookup"><span data-stu-id="200d0-181">After the package loads, click on the **Import** button.</span></span>

### <a name="setup-the-scene"></a><span data-ttu-id="200d0-182">Einrichten der Szene</span><span class="sxs-lookup"><span data-stu-id="200d0-182">Setup the scene</span></span>

1. <span data-ttu-id="200d0-183">Löschen Sie die **Hauptkamera**in der-Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="200d0-183">In the Hierarchy, delete the **Main Camera**.</span></span>
2. <span data-ttu-id="200d0-184">Öffnen Sie im Ordner **holotoolkit** den **Eingabe** Ordner, und öffnen Sie dann den Ordner **Prefabs** .</span><span class="sxs-lookup"><span data-stu-id="200d0-184">In the **HoloToolkit** folder, open the **Input** folder, then open the **Prefabs** folder.</span></span>
3. <span data-ttu-id="200d0-185">Ziehen Sie die vorfab **mixedrealitycameraparent** aus dem Ordner **Prefabs** in die **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="200d0-185">Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy**.</span></span>
4. <span data-ttu-id="200d0-186">Klicken Sie mit der rechten Maustaste auf den **direktionalen Licht** in der Hierarchie, **und wählen**</span><span class="sxs-lookup"><span data-stu-id="200d0-186">Right-click the **Directional Light** in the Hierarchy and select **Delete**.</span></span>
5. <span data-ttu-id="200d0-187">Ziehen Sie im **holograms** -Ordner die folgenden Objekte per Drag & amp; Drop in den Stamm der **Hierarchie**:</span><span class="sxs-lookup"><span data-stu-id="200d0-187">In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy**:</span></span>
    * <span data-ttu-id="200d0-188">**Astroman**</span><span class="sxs-lookup"><span data-stu-id="200d0-188">**AstroMan**</span></span>
    * <span data-ttu-id="200d0-189">**Such**</span><span class="sxs-lookup"><span data-stu-id="200d0-189">**Lights**</span></span>
    * <span data-ttu-id="200d0-190">**Spaceaudiosource**</span><span class="sxs-lookup"><span data-stu-id="200d0-190">**SpaceAudioSource**</span></span>
    * <span data-ttu-id="200d0-191">**Spacebackground**</span><span class="sxs-lookup"><span data-stu-id="200d0-191">**SpaceBackground**</span></span>
6. <span data-ttu-id="200d0-192">Starten Sie den **Wiedergabemodus** ▶, um den Astronaut anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="200d0-192">Start **Play Mode** ▶ to view the astronaut.</span></span>
7. <span data-ttu-id="200d0-193">Klicken Sie erneut auf **Wiedergabemodus** ▶, um zu **verhindern**.</span><span class="sxs-lookup"><span data-stu-id="200d0-193">Click **Play Mode** ▶ again to **Stop**.</span></span>
8. <span data-ttu-id="200d0-194">Suchen Sie im Ordner **holograms** das **fitbox** -Asset, und ziehen Sie es in den Stamm der **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="200d0-194">In the **Holograms** folder, find the **Fitbox** asset and drag it to the root of the **Hierarchy**.</span></span>
9. <span data-ttu-id="200d0-195">Wählen Sie im Bereich **Hierarchie** die Option **fitbox** aus.</span><span class="sxs-lookup"><span data-stu-id="200d0-195">Select the **Fitbox** in the **Hierarchy** panel.</span></span>
10. <span data-ttu-id="200d0-196">Ziehen Sie die **Astroman** -Auflistung aus der **Hierarchie** in die **Hologram** -Auflistungs Eigenschaft von "fitbox" im **Inspektor** -Panel.</span><span class="sxs-lookup"><span data-stu-id="200d0-196">Drag the **AstroMan** collection from the **Hierarchy** to the **Hologram Collection** property of the Fitbox in the **Inspector** panel.</span></span>

### <a name="save-the-project"></a><span data-ttu-id="200d0-197">Speichern Sie das Projekt.</span><span class="sxs-lookup"><span data-stu-id="200d0-197">Save the project</span></span>

1. <span data-ttu-id="200d0-198">Speichern Sie die neue Szene: **File > Szene speichern**unter.</span><span class="sxs-lookup"><span data-stu-id="200d0-198">Save the new scene: **File > Save Scene As**.</span></span>
2. <span data-ttu-id="200d0-199">Klicken Sie auf **neuer Ordner** , und benennen Sie die Ordner **Szenen**.</span><span class="sxs-lookup"><span data-stu-id="200d0-199">Click **New Folder** and name the folder **Scenes**.</span></span>
3. <span data-ttu-id="200d0-200">Benennen Sie die Datei "**Model Explorer**", und speichern Sie Sie im Ordner **Szenen** .</span><span class="sxs-lookup"><span data-stu-id="200d0-200">Name the file “**ModelExplorer**” and save it in the **Scenes** folder.</span></span>

### <a name="build-the-project"></a><span data-ttu-id="200d0-201">Erstellen des Projekts</span><span class="sxs-lookup"><span data-stu-id="200d0-201">Build the project</span></span>

1. <span data-ttu-id="200d0-202">Wählen Sie in Unity **Datei >** Buildeinstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="200d0-202">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="200d0-203">Klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="200d0-203">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="200d0-204">Wählen Sie in der Liste **Plattform** **universelle Windows-Plattform** aus, und klicken Sie auf **Plattform wechseln**.</span><span class="sxs-lookup"><span data-stu-id="200d0-204">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="200d0-205">Wenn Sie speziell für hololens entwickeln, legen Sie **Zielgerät** auf **hololens**fest.</span><span class="sxs-lookup"><span data-stu-id="200d0-205">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="200d0-206">Andernfalls sollten Sie es auf **jedem Gerät**belassen.</span><span class="sxs-lookup"><span data-stu-id="200d0-206">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="200d0-207">Stellen  Sie sicher, dass der Buildtyp auf **D3D** und das **SDK** auf **Latest installiert** festgelegt ist (was SDK 16299 oder höher sein sollte).</span><span class="sxs-lookup"><span data-stu-id="200d0-207">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="200d0-208">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="200d0-208">Click **Build**.</span></span>
7. <span data-ttu-id="200d0-209">Erstellen Sie einen **neuen Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="200d0-209">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="200d0-210">Klicken Sie einfach auf den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="200d0-210">Single click the **App** folder.</span></span>
9. <span data-ttu-id="200d0-211">Drücken **Sie Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="200d0-211">Press **Select Folder**.</span></span>

<span data-ttu-id="200d0-212">Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="200d0-212">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="200d0-213">Öffnen Sie den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="200d0-213">Open the **App** folder.</span></span>
2. <span data-ttu-id="200d0-214">Öffnen Sie die Visual Studio-Projekt Mappe **Model Explorer**.</span><span class="sxs-lookup"><span data-stu-id="200d0-214">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="200d0-215">Bei der Bereitstellung in hololens:</span><span class="sxs-lookup"><span data-stu-id="200d0-215">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="200d0-216">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x86**.</span><span class="sxs-lookup"><span data-stu-id="200d0-216">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="200d0-217">Klicken Sie auf den Dropdown Pfeil neben der Schaltfläche lokaler Computer, und wählen Sie **Remote Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="200d0-217">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="200d0-218">Geben Sie **die IP-Adresse des hololens-Geräts** ein, und legen Sie den Authentifizierungsmodus auf **Universal (unverschlüsseltes Protokoll)**</span><span class="sxs-lookup"><span data-stu-id="200d0-218">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="200d0-219">Klicken Sie auf **Auswählen**.</span><span class="sxs-lookup"><span data-stu-id="200d0-219">Click **Select**.</span></span> <span data-ttu-id="200d0-220">Wenn Sie die IP-Adresse Ihres Geräts nicht kennen, suchen Sie unter **Einstellungen > Netzwerk & Internet > Erweiterte Optionen**.</span><span class="sxs-lookup"><span data-stu-id="200d0-220">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="200d0-221">Klicken Sie in der oberen Menüleiste auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="200d0-221">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="200d0-222">Wenn Sie die Bereitstellung auf Ihrem Gerät zum ersten Mal durchführt, müssen Sie [es mit Visual Studio](using-visual-studio.md#pairing-your-device-hololens)koppeln.</span><span class="sxs-lookup"><span data-stu-id="200d0-222">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="200d0-223">Wenn die APP bereitgestellt wurde, schließen Sie das **fitbox** -Gerät mit einer **Auswahl Bewegung**ab.</span><span class="sxs-lookup"><span data-stu-id="200d0-223">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="200d0-224">Bei der Bereitstellung auf einem immersiven Headset:</span><span class="sxs-lookup"><span data-stu-id="200d0-224">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="200d0-225">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x64**.</span><span class="sxs-lookup"><span data-stu-id="200d0-225">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="200d0-226">Stellen Sie sicher, dass das Bereitstellungs Ziel auf **lokaler Computer**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="200d0-226">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="200d0-227">Klicken Sie in der oberen Menüleiste auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="200d0-227">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="200d0-228">Wenn die APP bereitgestellt wurde, schließen Sie die Funktion **, indem Sie** den-Typ auf einen Bewegungs Controller ziehen.</span><span class="sxs-lookup"><span data-stu-id="200d0-228">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

## <a name="chapter-2---cursor-and-target-feedback"></a><span data-ttu-id="200d0-229">Kapitel 2: Cursor-und Ziel Feedback</span><span class="sxs-lookup"><span data-stu-id="200d0-229">Chapter 2 - Cursor and target feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a><span data-ttu-id="200d0-230">Ziele</span><span class="sxs-lookup"><span data-stu-id="200d0-230">Objectives</span></span>

* <span data-ttu-id="200d0-231">Visueller Entwurf und Verhalten des Cursors.</span><span class="sxs-lookup"><span data-stu-id="200d0-231">Cursor visual design and behavior.</span></span>
* <span data-ttu-id="200d0-232">Zeiger basiertes Cursor Feedback.</span><span class="sxs-lookup"><span data-stu-id="200d0-232">Gaze-based cursor feedback.</span></span>
* <span data-ttu-id="200d0-233">Auf Blick basierendes – Hologramm-Feedback.</span><span class="sxs-lookup"><span data-stu-id="200d0-233">Gaze-based hologram feedback.</span></span>

<span data-ttu-id="200d0-234">Wir werden unsere Arbeit auf einige Grundsätze von Cursor Entwürfen basieren, nämlich:</span><span class="sxs-lookup"><span data-stu-id="200d0-234">We're going to base our work on some cursor design principles, namely:</span></span>

* <span data-ttu-id="200d0-235">Der Cursor ist immer vorhanden.</span><span class="sxs-lookup"><span data-stu-id="200d0-235">The cursor is always present.</span></span>
* <span data-ttu-id="200d0-236">Lassen Sie den Cursor nicht zu klein oder groß werden.</span><span class="sxs-lookup"><span data-stu-id="200d0-236">Don't let the cursor get too small or big.</span></span>
* <span data-ttu-id="200d0-237">Vermeiden Sie das Blockieren von Inhalt.</span><span class="sxs-lookup"><span data-stu-id="200d0-237">Avoid obstructing content.</span></span>

### <a name="instructions"></a><span data-ttu-id="200d0-238">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="200d0-238">Instructions</span></span>

1. <span data-ttu-id="200d0-239">Suchen Sie im Ordner **holotoolkit\input\prefabs** nach dem **InputManager** -Objekt.</span><span class="sxs-lookup"><span data-stu-id="200d0-239">In the **HoloToolkit\Input\Prefabs** folder, find the **InputManager** asset.</span></span>
2. <span data-ttu-id="200d0-240">Ziehen Sie den **InputManager** in die **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="200d0-240">Drag and drop the **InputManager** onto the **Hierarchy**.</span></span>
3. <span data-ttu-id="200d0-241">Suchen Sie im Ordner **holotoolkit\input\prefabs** nach dem **Cursor** Medienobjekt.</span><span class="sxs-lookup"><span data-stu-id="200d0-241">In the **HoloToolkit\Input\Prefabs** folder, find the **Cursor** asset.</span></span>
4. <span data-ttu-id="200d0-242">Ziehen Sie den **Cursor** per Drag & Drop in die **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="200d0-242">Drag and drop the **Cursor** onto the **Hierarchy**.</span></span>
5. <span data-ttu-id="200d0-243">Wählen Sie das **InputManager** -Objekt in der **Hierarchie**aus.</span><span class="sxs-lookup"><span data-stu-id="200d0-243">Select the **InputManager** object in the **Hierarchy**.</span></span>
6. <span data-ttu-id="200d0-244">Ziehen Sie das **Cursor** Objekt aus der **Hierarchie** in das **Cursor** Feld " **simplesinglepointerselector**" von InputManager am unteren Rand des **Inspektors**.</span><span class="sxs-lookup"><span data-stu-id="200d0-244">Drag the **Cursor** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>

![Einfache Einrichtung von einzelzeigerselektor](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a><span data-ttu-id="200d0-246">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="200d0-246">Build and Deploy</span></span>

1. <span data-ttu-id="200d0-247">Erstellen Sie die APP aus dem **Datei >** den Buildeinstellungen neu.</span><span class="sxs-lookup"><span data-stu-id="200d0-247">Rebuild the app from **File > Build Settings**.</span></span>
2. <span data-ttu-id="200d0-248">Öffnen Sie den **app-Ordner**.</span><span class="sxs-lookup"><span data-stu-id="200d0-248">Open the **App folder**.</span></span>
3. <span data-ttu-id="200d0-249">Öffnen Sie die Visual Studio-Projekt Mappe **Model Explorer**.</span><span class="sxs-lookup"><span data-stu-id="200d0-249">Open the **ModelExplorer Visual Studio Solution**.</span></span>
4. <span data-ttu-id="200d0-250">Klicken Sie auf **Debuggen > Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="200d0-250">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
5. <span data-ttu-id="200d0-251">Beobachten Sie, wie der Cursor gezeichnet wird, und wie sich die Darstellung ändert, wenn Sie ein Hologram berührt.</span><span class="sxs-lookup"><span data-stu-id="200d0-251">Observe how the cursor is drawn, and how it changes appearance if it is touching a hologram.</span></span>

### <a name="instructions"></a><span data-ttu-id="200d0-252">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="200d0-252">Instructions</span></span>

1. <span data-ttu-id="200d0-253">Erweitern Sie im Bereich **Hierarchie** das Objekt " **Astroman**->**GEO_G**->**Back_Center** ".</span><span class="sxs-lookup"><span data-stu-id="200d0-253">In the **Hierarchy** panel, expand the **AstroMan**->**GEO_G**->**Back_Center** object.</span></span>
2. <span data-ttu-id="200d0-254">Doppelklicken Sie auf **Interactible.cs** , um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="200d0-254">Double click on **Interactible.cs** to open it in Visual Studio.</span></span>
3. <span data-ttu-id="200d0-255">Heben Sie die Auskommentierung der Zeilen in den Rückrufe **ifocverwendbare. onfocusenter ()** und **ifocverwendbare. onfocusexit ()** in **Interactible.cs**auf.</span><span class="sxs-lookup"><span data-stu-id="200d0-255">Uncomment the lines in the **IFocusable.OnFocusEnter()** and **IFocusable.OnFocusExit()** callbacks in **Interactible.cs**.</span></span> <span data-ttu-id="200d0-256">Diese werden vom InputManager des Mixed Reality-Toolkits aufgerufen, wenn der Fokus (entweder durch den Blick oder durch den Controller) in den Konflikt des jeweiligen gameobject-Objekts wechselt und diesen verlässt.</span><span class="sxs-lookup"><span data-stu-id="200d0-256">These are called by the Mixed Reality Toolkit's InputManager when focus (either by gaze or by controller pointing) enters and exits the specific GameObject's collider.</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
><span data-ttu-id="200d0-257">Wir verwenden `EnableKeyword` und `DisableKeyword` höher.</span><span class="sxs-lookup"><span data-stu-id="200d0-257">We use `EnableKeyword` and `DisableKeyword` above.</span></span> <span data-ttu-id="200d0-258">Um diese in ihrer eigenen App mit dem Standard-Shader des Toolkits zu nutzen, müssen Sie die [Unity-Richtlinien für den Zugriff auf Materialien per Skript](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)befolgen.</span><span class="sxs-lookup"><span data-stu-id="200d0-258">In order to make use of these in your own app with the Toolkit's Standard shader, you'll need to follow the [Unity guidelines for accessing materials via script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span></span> <span data-ttu-id="200d0-259">In diesem Fall haben wir bereits die [drei Varianten von hervorgehobenem Material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) in den Ressourcen Ordner eingefügt (suchen Sie nach den drei Materialien, deren Name hervorgehoben ist).</span><span class="sxs-lookup"><span data-stu-id="200d0-259">In this case, we've already included the [three variants of highlighted material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) needed in the Resources folder (look for the three materials with highlight in the name).</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="200d0-260">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="200d0-260">Build and Deploy</span></span>

1. <span data-ttu-id="200d0-261">Erstellen Sie wie zuvor das Projekt, und stellen Sie es auf den hololens bereit.</span><span class="sxs-lookup"><span data-stu-id="200d0-261">As before, build the project and deploy to the HoloLens.</span></span>
2. <span data-ttu-id="200d0-262">Beobachten Sie, was geschieht, wenn der Blick auf ein Objekt gerichtet ist, und wenn es nicht.</span><span class="sxs-lookup"><span data-stu-id="200d0-262">Observe what happens when the gaze is aimed at an object and when it's not.</span></span>

## <a name="chapter-3---targeting-techniques"></a><span data-ttu-id="200d0-263">Kapitel 3: Ziel Technologien</span><span class="sxs-lookup"><span data-stu-id="200d0-263">Chapter 3 - Targeting Techniques</span></span>

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a><span data-ttu-id="200d0-264">Ziele</span><span class="sxs-lookup"><span data-stu-id="200d0-264">Objectives</span></span>

* <span data-ttu-id="200d0-265">Vereinfachen Sie das Ziel von holograms.</span><span class="sxs-lookup"><span data-stu-id="200d0-265">Make it easier to target holograms.</span></span>
* <span data-ttu-id="200d0-266">Stabilisiert natürliche Head-Bewegungen.</span><span class="sxs-lookup"><span data-stu-id="200d0-266">Stabilize natural head movements.</span></span>

### <a name="instructions"></a><span data-ttu-id="200d0-267">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="200d0-267">Instructions</span></span>

1. <span data-ttu-id="200d0-268">Wählen Sie im Bereich **Hierarchie** das Objekt **InputManager** aus.</span><span class="sxs-lookup"><span data-stu-id="200d0-268">In the **Hierarchy** panel, select the **InputManager** object.</span></span>
2. <span data-ttu-id="200d0-269">Suchen Sie im **Inspektor** -Panel nach dem Skript für den **Blick-Stabilisator** .</span><span class="sxs-lookup"><span data-stu-id="200d0-269">In the **Inspector** panel, find the **Gaze Stabilizer** script.</span></span> <span data-ttu-id="200d0-270">Klicken Sie auf die Datei, um Sie in Visual Studio zu öffnen, wenn Sie ein Bild sehen möchten.</span><span class="sxs-lookup"><span data-stu-id="200d0-270">Click it to open in Visual Studio, if you want to take a look.</span></span>
    * <span data-ttu-id="200d0-271">Dieses Skript durchläuft Beispiele von raycast-Daten und trägt dazu bei, den Blick des Benutzers auf die Genauigkeit der Genauigkeit zu stabilisieren.</span><span class="sxs-lookup"><span data-stu-id="200d0-271">This script iterates over samples of Raycast data and helps stabilize the user's gaze for precision targeting.</span></span>
3. <span data-ttu-id="200d0-272">Im **Inspektor**können Sie den Wert für **gespeicherte Stabilitäts Beispiele** bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="200d0-272">In the **Inspector**, you can edit the **Stored Stability Samples** value.</span></span> <span data-ttu-id="200d0-273">Dieser Wert stellt die Anzahl der Samplings dar, die der-Stabilisator durchläuft, um den stabilisierten Wert zu berechnen.</span><span class="sxs-lookup"><span data-stu-id="200d0-273">This value represents the number of samples that the stabilizer iterates on to calculate the stabilized value.</span></span>

## <a name="chapter-4---directional-indicator"></a><span data-ttu-id="200d0-274">Kapitel 4: direktionaler Indikator</span><span class="sxs-lookup"><span data-stu-id="200d0-274">Chapter 4 - Directional indicator</span></span>

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a><span data-ttu-id="200d0-275">Ziele</span><span class="sxs-lookup"><span data-stu-id="200d0-275">Objectives</span></span>

* <span data-ttu-id="200d0-276">Fügen Sie einen direktionalen Indikator für den Cursor hinzu, um Hologramme zu finden.</span><span class="sxs-lookup"><span data-stu-id="200d0-276">Add a directional indicator on the cursor to help find holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="200d0-277">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="200d0-277">Instructions</span></span>

<span data-ttu-id="200d0-278">Wir verwenden die Datei **DirectionIndicator.cs** , um Folgendes zu tun:</span><span class="sxs-lookup"><span data-stu-id="200d0-278">We're going to use the **DirectionIndicator.cs** file which will:</span></span>

1. <span data-ttu-id="200d0-279">Zeigen Sie den direktionalen Indikator an, wenn der Benutzer nicht mit den holograms-Vorgängen.</span><span class="sxs-lookup"><span data-stu-id="200d0-279">Show the directional indicator if the user is not gazing at the holograms.</span></span>
2. <span data-ttu-id="200d0-280">Blenden Sie den direktionalen Indikator aus, wenn der Benutzer bei den holograms einen Blick anzeigt.</span><span class="sxs-lookup"><span data-stu-id="200d0-280">Hide the directional indicator if the user is gazing at the holograms.</span></span>
3. <span data-ttu-id="200d0-281">Aktualisieren Sie den direktionalen Indikator, sodass er auf die holograms zeigt.</span><span class="sxs-lookup"><span data-stu-id="200d0-281">Update the directional indicator to point to the holograms.</span></span>

<span data-ttu-id="200d0-282">Los geht's.</span><span class="sxs-lookup"><span data-stu-id="200d0-282">Let's get started.</span></span>

1. <span data-ttu-id="200d0-283">Klicken Sie im **Hierarchie** Panel auf das **Astroman** -Objekt, und klicken Sie auf **den Pfeil** , um es zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="200d0-283">Click on the **AstroMan** object in the **Hierarchy** panel and **click the arrow** to expand it.</span></span>
2. <span data-ttu-id="200d0-284">Wählen Sie im Bereich **Hierarchie** das **directionalindicator** -Objekt unter **Astroman**aus.</span><span class="sxs-lookup"><span data-stu-id="200d0-284">In the **Hierarchy** panel, select the **DirectionalIndicator** object under **AstroMan**.</span></span>
3. <span data-ttu-id="200d0-285">Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="200d0-285">In the **Inspector** panel, click the **Add Component** button.</span></span>
4. <span data-ttu-id="200d0-286">Geben Sie im Menü den Suchfeld- **Richtungsindikator**ein.</span><span class="sxs-lookup"><span data-stu-id="200d0-286">In the menu, type in the search box **Direction Indicator**.</span></span> <span data-ttu-id="200d0-287">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="200d0-287">Select the search result.</span></span>
5. <span data-ttu-id="200d0-288">Ziehen Sie im Bereich **Hierarchie** das **Cursor** Objekt per Drag & Drop auf die **Cursor** -Eigenschaft des **Inspektors**.</span><span class="sxs-lookup"><span data-stu-id="200d0-288">In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector**.</span></span>
6. <span data-ttu-id="200d0-289">Ziehen Sie im **Projekt** Panel im Ordner **holograms** das **directionalindicator** -Asset per Drag & Drop auf die **direktionale Indikator** Eigenschaft im **Inspektor**.</span><span class="sxs-lookup"><span data-stu-id="200d0-289">In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector**.</span></span>
7. <span data-ttu-id="200d0-290">Erstellen und Bereitstellen der app.</span><span class="sxs-lookup"><span data-stu-id="200d0-290">Build and deploy the app.</span></span>
8. <span data-ttu-id="200d0-291">Sehen Sie, wie das direktionale Indikator Objekt Ihnen hilft, den Astronaut zu finden.</span><span class="sxs-lookup"><span data-stu-id="200d0-291">Watch how the directional indicator object helps you find the astronaut.</span></span>

## <a name="chapter-5---billboarding"></a><span data-ttu-id="200d0-292">Kapitel 5: Abrechnung</span><span class="sxs-lookup"><span data-stu-id="200d0-292">Chapter 5 - Billboarding</span></span>

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a><span data-ttu-id="200d0-293">Ziele</span><span class="sxs-lookup"><span data-stu-id="200d0-293">Objectives</span></span>

* <span data-ttu-id="200d0-294">Verwenden Sie das-Abrechnungs Board, um holograms immer für Sie zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="200d0-294">Use billboarding to have holograms always face towards you.</span></span>

<span data-ttu-id="200d0-295">Wir verwenden die Datei **Billboard.cs** , um ein gameobject-Objekt so zu speichern, dass es dem Benutzer jederzeit zusteht.</span><span class="sxs-lookup"><span data-stu-id="200d0-295">We will be using the **Billboard.cs** file to keep a GameObject oriented such that it is facing the user at all times.</span></span>

1. <span data-ttu-id="200d0-296">Wählen Sie im Bereich **Hierarchie** das Objekt **Astroman** aus.</span><span class="sxs-lookup"><span data-stu-id="200d0-296">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
2. <span data-ttu-id="200d0-297">Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="200d0-297">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="200d0-298">Geben Sie im Menü im Suchfeld den Suchbegriff **ein.**</span><span class="sxs-lookup"><span data-stu-id="200d0-298">In the menu, type in the search box **Billboard**.</span></span> <span data-ttu-id="200d0-299">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="200d0-299">Select the search result.</span></span>
4. <span data-ttu-id="200d0-300">Legen Sie im **Inspektor** die  pivotachse auf **Y**fest.</span><span class="sxs-lookup"><span data-stu-id="200d0-300">In the **Inspector** set the **Pivot Axis** to **Y**.</span></span>
5. <span data-ttu-id="200d0-301">Probieren Sie es aus!</span><span class="sxs-lookup"><span data-stu-id="200d0-301">Try it!</span></span> <span data-ttu-id="200d0-302">Erstellen und stellen Sie die APP wie zuvor bereit.</span><span class="sxs-lookup"><span data-stu-id="200d0-302">Build and deploy the app as before.</span></span>
6. <span data-ttu-id="200d0-303">Sehen Sie sich an, wie das Billboard-Objekt Ihnen unabhängig von der Änderung des Standpunkts steht.</span><span class="sxs-lookup"><span data-stu-id="200d0-303">See how the Billboard object faces you no matter how you change the viewpoint.</span></span>
7. <span data-ttu-id="200d0-304">Löschen Sie das Skript für den Moment aus dem **Astroman** .</span><span class="sxs-lookup"><span data-stu-id="200d0-304">Delete the script from the **AstroMan** for now.</span></span>

## <a name="chapter-6---tag-along"></a><span data-ttu-id="200d0-305">Kapitel 6: tagparallel</span><span class="sxs-lookup"><span data-stu-id="200d0-305">Chapter 6 - Tag-Along</span></span>

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a><span data-ttu-id="200d0-306">Ziele</span><span class="sxs-lookup"><span data-stu-id="200d0-306">Objectives</span></span>

* <span data-ttu-id="200d0-307">Verwenden Sie Tag-Along, damit unsere Hologramme um den Raum herum stehen.</span><span class="sxs-lookup"><span data-stu-id="200d0-307">Use Tag-Along to have our holograms follow us around the room.</span></span>

<span data-ttu-id="200d0-308">Wir arbeiten an diesem Problem, indem wir die folgenden Entwurfs Einschränkungen beachten:</span><span class="sxs-lookup"><span data-stu-id="200d0-308">As we work on this issue, we'll be guided by the following design constraints:</span></span>

* <span data-ttu-id="200d0-309">Der Inhalt sollte immer auf einen Blick entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="200d0-309">Content should always be a glance away.</span></span>
* <span data-ttu-id="200d0-310">Der Inhalt sollte nicht auf dem Wege stehen.</span><span class="sxs-lookup"><span data-stu-id="200d0-310">Content should not be in the way.</span></span>
* <span data-ttu-id="200d0-311">Der Inhalt der Kopf Sperre ist unbequem.</span><span class="sxs-lookup"><span data-stu-id="200d0-311">Head-locking content is uncomfortable.</span></span>

<span data-ttu-id="200d0-312">Die hier verwendete Lösung ist die Verwendung eines "tagbasierten" Ansatzes.</span><span class="sxs-lookup"><span data-stu-id="200d0-312">The solution used here is to use a "tag-along" approach.</span></span>

<span data-ttu-id="200d0-313">Ein tagansichts Objekt verlässt die Ansicht des Benutzers niemals vollständig.</span><span class="sxs-lookup"><span data-stu-id="200d0-313">A tag-along object never fully leaves the user's view.</span></span> <span data-ttu-id="200d0-314">Sie können sich ein Tag als ein Objekt vorstellen, das an den Kopf des Benutzers durch Gummibänder angehängt ist.</span><span class="sxs-lookup"><span data-stu-id="200d0-314">You can think of the a tag-along as being an object attached to the user's head by rubber bands.</span></span> <span data-ttu-id="200d0-315">Wenn der Benutzer sich bewegt, bleibt der Inhalt in einem einfachen Blick, indem er an den Rand der Ansicht bewegt wird, ohne dass er vollständig verlässt.</span><span class="sxs-lookup"><span data-stu-id="200d0-315">As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving.</span></span> <span data-ttu-id="200d0-316">Wenn der Benutzer in Richtung des tagbasierten Objekts zeigt, wird es vollständig in die Ansicht integriert.</span><span class="sxs-lookup"><span data-stu-id="200d0-316">When the user gazes towards the tag-along object, it comes more fully into view.</span></span>

<span data-ttu-id="200d0-317">Wir verwenden die Datei **SimpleTagalong.cs** , um Folgendes zu tun:</span><span class="sxs-lookup"><span data-stu-id="200d0-317">We're going to use the **SimpleTagalong.cs** file which will:</span></span>

1. <span data-ttu-id="200d0-318">Bestimmt, ob sich das Tag-entlang-Objekt innerhalb der Kamera Begrenzungen befindet.</span><span class="sxs-lookup"><span data-stu-id="200d0-318">Determine if the Tag-Along object is within the camera bounds.</span></span>
2. <span data-ttu-id="200d0-319">Wenn nicht in der Ansicht "Frustum" angezeigt wird, positionieren Sie das Tag-entlang auf teilweise innerhalb der Ansicht "Frustum".</span><span class="sxs-lookup"><span data-stu-id="200d0-319">If not within the view frustum, position the Tag-Along to partially within the view frustum.</span></span>
3. <span data-ttu-id="200d0-320">Positionieren Sie andernfalls das Tag-parallel zu einem Standardabstand vom Benutzer.</span><span class="sxs-lookup"><span data-stu-id="200d0-320">Otherwise, position the Tag-Along to a default distance from the user.</span></span>

<span data-ttu-id="200d0-321">Zu diesem Zweck müssen wir zuerst das **Interactible.cs** -Skript ändern, um die **Tagalong-Aktion**aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="200d0-321">To do this, we first must change the **Interactible.cs** script to call the **TagalongAction**.</span></span>

1. <span data-ttu-id="200d0-322">Bearbeiten Sie **Interactible.cs** , indem Sie die Codierungs Übung 6. a abschließen (auskommentieren von Zeilen 84 bis 87).</span><span class="sxs-lookup"><span data-stu-id="200d0-322">Edit **Interactible.cs** by completing coding exercise 6.a (uncommenting lines 84 to 87).</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

<span data-ttu-id="200d0-323">Das **InteractibleAction.cs** -Skript in Kombination mit **Interactible.cs** führt benutzerdefinierte Aktionen aus, wenn Sie auf holograms tippen.</span><span class="sxs-lookup"><span data-stu-id="200d0-323">The **InteractibleAction.cs** script, paired with **Interactible.cs** performs custom actions when you tap on holograms.</span></span> <span data-ttu-id="200d0-324">In diesem Fall verwenden wir eine speziell für das Tag.</span><span class="sxs-lookup"><span data-stu-id="200d0-324">In this case, we'll use one specifically for tag-along.</span></span>

* <span data-ttu-id="200d0-325">Klicken Sie im Ordner **Scripts** auf **TagalongAction.cs** Asset, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="200d0-325">In the **Scripts** folder click on **TagalongAction.cs** asset to open in Visual Studio.</span></span>
* <span data-ttu-id="200d0-326">Führen Sie die Codierungs Übung aus, oder ändern Sie Sie in Folgendes:</span><span class="sxs-lookup"><span data-stu-id="200d0-326">Complete the coding exercise or change it to this:</span></span>
  * <span data-ttu-id="200d0-327">Geben Sie oben in der **Hierarchie**in der Suchleiste **ChestButton_Center** ein, und wählen Sie das Ergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="200d0-327">At the top of the **Hierarchy**, in the search bar type **ChestButton_Center** and select the result.</span></span>
  * <span data-ttu-id="200d0-328">Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="200d0-328">In the **Inspector** panel, click the **Add Component** button.</span></span>
  * <span data-ttu-id="200d0-329">Geben Sie im Menü in das Suchfeld **Tagalong Action**ein.</span><span class="sxs-lookup"><span data-stu-id="200d0-329">In the menu, type in the search box **Tagalong Action**.</span></span> <span data-ttu-id="200d0-330">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="200d0-330">Select the search result.</span></span>
  * <span data-ttu-id="200d0-331">Suchen Sie im Ordner **holograms** das **Tagalong** Asset.</span><span class="sxs-lookup"><span data-stu-id="200d0-331">In **Holograms** folder find the **Tagalong** asset.</span></span>
  * <span data-ttu-id="200d0-332">Wählen Sie das **ChestButton_Center** -Objekt in der **Hierarchie**aus.</span><span class="sxs-lookup"><span data-stu-id="200d0-332">Select the **ChestButton_Center** object in the **Hierarchy**.</span></span> <span data-ttu-id="200d0-333">Ziehen Sie das **Tagalong** -Objekt per Drag & amp; Drop aus dem **Projekt** Panel auf den **Inspektor** in die Eigenschaft **Objekt zu tagparallel** .</span><span class="sxs-lookup"><span data-stu-id="200d0-333">Drag and drop the **TagAlong** object from the **Project** panel onto the **Inspector** into the **Object To Tagalong** property.</span></span>
  * <span data-ttu-id="200d0-334">Ziehen Sie das **Tagalong-Aktions** Objekt aus dem **Inspektor** in das **interable-Aktions** Feld des **interfähigen** Skripts.</span><span class="sxs-lookup"><span data-stu-id="200d0-334">Drag the **Tagalong Action** object from the **Inspector** into the **Interactible Action** field on the **Interactible** script.</span></span>
* <span data-ttu-id="200d0-335">Doppelklicken Sie auf das Skript **tagalongaction** , um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="200d0-335">Double click the **TagalongAction** script to open it in Visual Studio.</span></span>

![Interacable-Einrichtung](images/holograms210-interactible.png)

<span data-ttu-id="200d0-337">Wir müssen Folgendes hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="200d0-337">We need to add the following:</span></span>

* <span data-ttu-id="200d0-338">Fügen Sie der Funktion "PerformAction" im tagalongaction-Skript (geerbt von interactibleaction) Funktionalität hinzu.</span><span class="sxs-lookup"><span data-stu-id="200d0-338">Add functionality to the PerformAction function in the TagalongAction script (inherited from InteractibleAction).</span></span>
* <span data-ttu-id="200d0-339">Fügen Sie dem Objekt "gazed-on" einen fakboardingvorgang hinzu, und legen Sie die pivotachse auf XY fest</span><span class="sxs-lookup"><span data-stu-id="200d0-339">Add billboarding to the gazed-upon object, and set the pivot axis to XY.</span></span>
* <span data-ttu-id="200d0-340">Fügen Sie dann dem-Objekt eine einfache tagverbindung hinzu.</span><span class="sxs-lookup"><span data-stu-id="200d0-340">Then add simple Tag-Along to the object.</span></span>

<span data-ttu-id="200d0-341">Hier ist unsere Lösung, von **TagalongAction.cs**:</span><span class="sxs-lookup"><span data-stu-id="200d0-341">Here's our solution, from **TagalongAction.cs**:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* <span data-ttu-id="200d0-342">Probieren Sie es aus!</span><span class="sxs-lookup"><span data-stu-id="200d0-342">Try it!</span></span> <span data-ttu-id="200d0-343">Erstellen und Bereitstellen der app.</span><span class="sxs-lookup"><span data-stu-id="200d0-343">Build and deploy the app.</span></span>
* <span data-ttu-id="200d0-344">Sehen Sie sich an, wie der Inhalt der Mitte des Blick Punkts folgt, aber nicht kontinuierlich und ohne Blockierung.</span><span class="sxs-lookup"><span data-stu-id="200d0-344">Watch how the content follows the center of the gaze point, but not continuously and without blocking it.</span></span>
