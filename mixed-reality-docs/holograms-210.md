---
title: MR Eingabe 210 - Blicke
description: Führen Sie diese exemplarischen Vorgehensweise erfahren, die Details der Blicke Konzepte auf Unity, Visual Studio und HoloLens mit Codierung.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Holotoolkit, Mixedrealitytoolkit, Mixedrealitytoolkit-Unity Academy, Tutorial, Blicke
ms.openlocfilehash: 63c55e8a7a348f2a3e0cc29a9795d7fabcef5df0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593976"
---
>[!NOTE]
><span data-ttu-id="85cef-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="85cef-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="85cef-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="85cef-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="85cef-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="85cef-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="85cef-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="85cef-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="85cef-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="85cef-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="85cef-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="85cef-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-210-gaze"></a><span data-ttu-id="85cef-110">MR Eingabe 210: Blickeingabe</span><span class="sxs-lookup"><span data-stu-id="85cef-110">MR Input 210: Gaze</span></span>

<span data-ttu-id="85cef-111">[Bestaunen](gaze.md) ist die erste Form der Eingabe und zeigt die Absicht und Informationen des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="85cef-111">[Gaze](gaze.md) is the first form of input and reveals the user's intent and awareness.</span></span> <span data-ttu-id="85cef-112">MR Eingabe 210 (auch bekannt als Projekt-Explorer) ist eine ausführliche Betrachtung Blicke bezogene Konzepte für die Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="85cef-112">MR Input 210 (aka Project Explorer) is a deep dive into gaze-related concepts for Windows Mixed Reality.</span></span> <span data-ttu-id="85cef-113">Wir werden hinzufügen kontextbezogene Informationen zu den Cursor und Hologramme, voll ausschöpfen was Ihre app des Benutzers Blicke bekannt sind.</span><span class="sxs-lookup"><span data-stu-id="85cef-113">We will be adding contextual awareness to our cursor and holograms, taking full advantage of what your app knows about the user's gaze.</span></span>

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

<span data-ttu-id="85cef-114">Wir haben eine benutzerfreundliche Astronautenausweis Hier können Sie die Blicke Konzepten vertraut zu machen.</span><span class="sxs-lookup"><span data-stu-id="85cef-114">We have a friendly astronaut here to help you learn gaze concepts.</span></span> <span data-ttu-id="85cef-115">In [MR Grundlagen 101](holograms-101.md), einen einfachen Cursor, der gerade Ihre Blicke gefolgt werden musste.</span><span class="sxs-lookup"><span data-stu-id="85cef-115">In [MR Basics 101](holograms-101.md), we had a simple cursor that just followed your gaze.</span></span> <span data-ttu-id="85cef-116">Heute haben wir einen Schritt weiter als die einfachen Cursor verschieben:</span><span class="sxs-lookup"><span data-stu-id="85cef-116">Today we're moving a step beyond the simple cursor:</span></span>

* <span data-ttu-id="85cef-117">Machen wir den Cursor und unsere Hologramme Blicke unterstützenden: beide ändern sich basierend auf, in denen der Benutzer sieht – oder, in denen der Benutzer ist *nicht* suchen.</span><span class="sxs-lookup"><span data-stu-id="85cef-117">We're making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is *not* looking.</span></span> <span data-ttu-id="85cef-118">Dadurch werden sie Kontext berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="85cef-118">This makes them context-aware.</span></span>
* <span data-ttu-id="85cef-119">Fügen wir Feedback zu unseren Cursor und Hologramme, Benutzern mehr Kontext auf was vorgesehen ist.</span><span class="sxs-lookup"><span data-stu-id="85cef-119">We will add feedback to our cursor and holograms to give the user more context on what is being targeted.</span></span> <span data-ttu-id="85cef-120">Dieses Feedback kann es sich um Audio- und visuellen sein.</span><span class="sxs-lookup"><span data-stu-id="85cef-120">This feedback can be audio and visual.</span></span>
* <span data-ttu-id="85cef-121">Wir zeigen Ihnen die Zielgruppenadressierung anhand bestimmter Techniken, um die Benutzer, die kleinere Ziele erreichen können.</span><span class="sxs-lookup"><span data-stu-id="85cef-121">We'll show you targeting techniques to help users hit smaller targets.</span></span>
* <span data-ttu-id="85cef-122">Wir zeigen Ihnen die Aufmerksamkeit des Benutzers zu Ihrer Hologramme mit einem richtungsindikator zeichnen.</span><span class="sxs-lookup"><span data-stu-id="85cef-122">We'll show you how to draw the user's attention to your holograms with a directional indicator.</span></span>
* <span data-ttu-id="85cef-123">Wir werden Sie die Portalwebsite Verfahren, um Ihre Hologramme mit dem Benutzer zu nutzen, wie sie in Ihrer Welt verschiebt.</span><span class="sxs-lookup"><span data-stu-id="85cef-123">We'll teach you techniques to take your holograms with the user as she moves around in your world.</span></span>

>[!IMPORTANT]
><span data-ttu-id="85cef-124">Die Videos in jeder der folgenden Kapitel eingebettet wurden mit einer älteren Version von Unity und dem Mixed Reality-Toolkit aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="85cef-124">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="85cef-125">Während die schrittweisen Anweisungen korrekt und aktuell sind, Sie möglicherweise Skripts und Visualisierungen in die entsprechenden Videos, die veraltet sind.</span><span class="sxs-lookup"><span data-stu-id="85cef-125">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="85cef-126">Die Videos aus Gründen der Posterity bleiben, und es aber trotzdem anwenden, da die Konzepte behandelt.</span><span class="sxs-lookup"><span data-stu-id="85cef-126">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="85cef-127">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="85cef-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="85cef-128">Kurs</span><span class="sxs-lookup"><span data-stu-id="85cef-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="85cef-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="85cef-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="85cef-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="85cef-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="85cef-131">MR Eingabe 210: Blickeingabe</span><span class="sxs-lookup"><span data-stu-id="85cef-131">MR Input 210: Gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="85cef-132">✔️</span><span class="sxs-lookup"><span data-stu-id="85cef-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="85cef-133">✔️</span><span class="sxs-lookup"><span data-stu-id="85cef-133">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="85cef-134">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="85cef-134">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="85cef-135">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="85cef-135">Prerequisites</span></span>

* <span data-ttu-id="85cef-136">Ein Windows 10-PCs mit dem richtigen konfiguriert [-Tools installiert](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="85cef-136">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="85cef-137">Einige grundlegende C# Programmierkenntnisse.</span><span class="sxs-lookup"><span data-stu-id="85cef-137">Some basic C# programming ability.</span></span>
* <span data-ttu-id="85cef-138">Sie sollten abgeschlossen haben [MR Grundlagen 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="85cef-138">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="85cef-139">Ein Gerät HoloLens [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="85cef-139">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="85cef-140">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="85cef-140">Project files</span></span>

* <span data-ttu-id="85cef-141">Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) vom Projekt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="85cef-141">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) required by the project.</span></span><span data-ttu-id="85cef-142"> Ist Unity 2017.2 oder höher erforderlich.</span><span class="sxs-lookup"><span data-stu-id="85cef-142"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="85cef-143">Un-Archive die Dateien auf dem Desktop oder andere einfach auf den Speicherort zugreifen.</span><span class="sxs-lookup"><span data-stu-id="85cef-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="85cef-144">Wenn Sie vor dem Herunterladen, den Quellcode ansehen möchten es [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span><span class="sxs-lookup"><span data-stu-id="85cef-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="85cef-145">Fehler und Anmerkungen zu dieser Version</span><span class="sxs-lookup"><span data-stu-id="85cef-145">Errata and Notes</span></span>

* <span data-ttu-id="85cef-146">"Nur eigenen Code" in Visual Studio muss sein Disabled (deaktiviert) unter Extras -> Optionen -> Debugging um Haltepunkte in Ihrem Code.</span><span class="sxs-lookup"><span data-stu-id="85cef-146">In Visual Studio, "Just My Code" needs to be disabled (unchecked) under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="85cef-147">Kapitel 1: Unity-Setup</span><span class="sxs-lookup"><span data-stu-id="85cef-147">Chapter 1 - Unity Setup</span></span>

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a><span data-ttu-id="85cef-148">Ziele</span><span class="sxs-lookup"><span data-stu-id="85cef-148">Objectives</span></span>

* <span data-ttu-id="85cef-149">Optimieren von Unity für die Entwicklung für HoloLens.</span><span class="sxs-lookup"><span data-stu-id="85cef-149">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="85cef-150">Importieren von Objekten aus, und richten Sie die Szene.</span><span class="sxs-lookup"><span data-stu-id="85cef-150">Import assets and setup the scene.</span></span>
* <span data-ttu-id="85cef-151">Zeigen Sie die Astronautenausweis, in die HoloLens.</span><span class="sxs-lookup"><span data-stu-id="85cef-151">View the astronaut in the HoloLens.</span></span>

### <a name="instructions"></a><span data-ttu-id="85cef-152">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="85cef-152">Instructions</span></span>

1. <span data-ttu-id="85cef-153">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="85cef-153">Start Unity.</span></span>
2. <span data-ttu-id="85cef-154">Wählen Sie **neues Projekt**.</span><span class="sxs-lookup"><span data-stu-id="85cef-154">Select **New Project**.</span></span>
3. <span data-ttu-id="85cef-155">Nennen Sie das Projekt **ModelExplorer**.</span><span class="sxs-lookup"><span data-stu-id="85cef-155">Name the project **ModelExplorer**.</span></span>
4. <span data-ttu-id="85cef-156">Geben Sie den Speicherort als dem **bestaunen** Ordner Sie zuvor nicht archiviert.</span><span class="sxs-lookup"><span data-stu-id="85cef-156">Enter location as the **Gaze** folder you previously un-archived.</span></span>
5. <span data-ttu-id="85cef-157">Stellen Sie sicher, dass das Projekt nastaven NA hodnotu **3D**.</span><span class="sxs-lookup"><span data-stu-id="85cef-157">Make sure the project is set to **3D**.</span></span>
6. <span data-ttu-id="85cef-158">Klicken Sie auf **erstellen Projekt**.</span><span class="sxs-lookup"><span data-stu-id="85cef-158">Click **Create Project**.</span></span>

### <a name="unity-settings-for-hololens"></a><span data-ttu-id="85cef-159">Unity-Einstellungen für HoloLens</span><span class="sxs-lookup"><span data-stu-id="85cef-159">Unity settings for HoloLens</span></span>

<span data-ttu-id="85cef-160">Wir müssen wissen, dass die app aus, es versucht wird, exportieren, zu erstellen, sollten Unity eine [immersive Ansicht](app-views.md) anstelle einer 2D-Ansicht.</span><span class="sxs-lookup"><span data-stu-id="85cef-160">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="85cef-161">Zu diesem Zweck HoloLens als virtuelle Realität Gerät hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="85cef-161">We do that by adding HoloLens as a virtual reality device.</span></span>

1. <span data-ttu-id="85cef-162">Wechseln Sie zu **Bearbeiten > Projekteinstellungen > Player**.</span><span class="sxs-lookup"><span data-stu-id="85cef-162">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="85cef-163">In der **Inspektor Bereich** Playereinstellungen, wählen Sie die **Windows Store** Symbol.</span><span class="sxs-lookup"><span data-stu-id="85cef-163">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="85cef-164">Erweitern Sie die **XR-Einstellungen** Gruppe.</span><span class="sxs-lookup"><span data-stu-id="85cef-164">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="85cef-165">In der **Rendern** aktivieren Sie im Abschnitt der **virtuelle Realität unterstützt** Kontrollkästchen zum Hinzufügen einer neuen **virtuelle Realität SDKs** Liste.</span><span class="sxs-lookup"><span data-stu-id="85cef-165">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="85cef-166">Überprüfen Sie, ob **Windows Mixed Reality** in der Liste angezeigt.</span><span class="sxs-lookup"><span data-stu-id="85cef-166">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="85cef-167">Wenn nicht der Fall, wählen Sie die **+** Schaltfläche am unteren Rand der Liste aus, und wählen Sie **Windows Holographic**.</span><span class="sxs-lookup"><span data-stu-id="85cef-167">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>

<span data-ttu-id="85cef-168">Als Nächstes müssen wir das Skript Back-End zu .NET festlegen.</span><span class="sxs-lookup"><span data-stu-id="85cef-168">Next, we need to set our scripting backend to .NET.</span></span>

1. <span data-ttu-id="85cef-169">Wechseln Sie zu **Bearbeiten > Projekteinstellungen > Player** (Sie können weiterhin haben dies aus dem vorherigen Schritt).</span><span class="sxs-lookup"><span data-stu-id="85cef-169">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="85cef-170">In der **Inspektor Bereich** Playereinstellungen, wählen Sie die **Windows Store** Symbol.</span><span class="sxs-lookup"><span data-stu-id="85cef-170">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="85cef-171">In der **Weitere Einstellungen** Konfiguration im Abschnitt, stellen Sie sicher, dass **Scripting Back-End-** nastaven NA hodnotu **.NET**</span><span class="sxs-lookup"><span data-stu-id="85cef-171">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="85cef-172">Zum Schluss aktualisieren wir unsere Qualität-Einstellungen, um eine hohe verarbeitungsleistung zu HoloLens zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="85cef-172">Finally, we'll update our quality settings to achieve a fast performance on HoloLens.</span></span>

1. <span data-ttu-id="85cef-173">Wechseln Sie zu **Bearbeiten > Projekteinstellungen > Qualität**.</span><span class="sxs-lookup"><span data-stu-id="85cef-173">Go to **Edit > Project Settings > Quality**.</span></span>
2. <span data-ttu-id="85cef-174">Klicken Sie auf den nach unten zeigenden Pfeil in der **Standard** Zeile unter dem Windows Store-Symbol.</span><span class="sxs-lookup"><span data-stu-id="85cef-174">Click on downward pointing arrow in the **Default** row under the Windows Store icon.</span></span>
3. <span data-ttu-id="85cef-175">Wählen Sie **schnellste** für **Windows Store-Apps**.</span><span class="sxs-lookup"><span data-stu-id="85cef-175">Select **Fastest** for **Windows Store Apps**.</span></span>

### <a name="import-project-assets"></a><span data-ttu-id="85cef-176">Importieren von Projektressourcen</span><span class="sxs-lookup"><span data-stu-id="85cef-176">Import project assets</span></span>

1. <span data-ttu-id="85cef-177">Klicken Sie mit der rechten Maustaste auf die **Assets** Ordner in der **Projekt** Bereich.</span><span class="sxs-lookup"><span data-stu-id="85cef-177">Right click the **Assets** folder in the **Project** panel.</span></span>
2. <span data-ttu-id="85cef-178">Klicken Sie auf **Paket importieren > benutzerdefiniertes Paket**.</span><span class="sxs-lookup"><span data-stu-id="85cef-178">Click on **Import Package > Custom Package**.</span></span>
3. <span data-ttu-id="85cef-179">Navigieren Sie zu den Projektdateien, die Sie heruntergeladen haben, und klicken Sie auf **ModelExplorer.unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="85cef-179">Navigate to the project files you downloaded and click on **ModelExplorer.unitypackage**.</span></span>
4. <span data-ttu-id="85cef-180">Klicken Sie auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="85cef-180">Click **Open**.</span></span>
5. <span data-ttu-id="85cef-181">Nachdem das Paket geladen wird, klicken Sie auf die **Import** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="85cef-181">After the package loads, click on the **Import** button.</span></span>

### <a name="setup-the-scene"></a><span data-ttu-id="85cef-182">Einrichten der Szene</span><span class="sxs-lookup"><span data-stu-id="85cef-182">Setup the scene</span></span>

1. <span data-ttu-id="85cef-183">Löschen Sie in der Hierarchie der **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="85cef-183">In the Hierarchy, delete the **Main Camera**.</span></span>
2. <span data-ttu-id="85cef-184">In der **HoloToolkit** Ordner die **Eingabe** Ordner öffnen Sie dann die **Prefabs** Ordner.</span><span class="sxs-lookup"><span data-stu-id="85cef-184">In the **HoloToolkit** folder, open the **Input** folder, then open the **Prefabs** folder.</span></span>
3. <span data-ttu-id="85cef-185">Drag & drop die **MixedRealityCameraParent** prefab aus der **Prefabs** Ordner in der **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="85cef-185">Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy**.</span></span>
4. <span data-ttu-id="85cef-186">Mit der rechten Maustaste die **gerichtetes Licht** in der Hierarchie, und wählen Sie **löschen**.</span><span class="sxs-lookup"><span data-stu-id="85cef-186">Right-click the **Directional Light** in the Hierarchy and select **Delete**.</span></span>
5. <span data-ttu-id="85cef-187">In der **Hologramme** Ordner Drag & drop die folgenden Ressourcen in das Stammverzeichnis der **Hierarchie**:</span><span class="sxs-lookup"><span data-stu-id="85cef-187">In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy**:</span></span>
    * <span data-ttu-id="85cef-188">**AstroMan**</span><span class="sxs-lookup"><span data-stu-id="85cef-188">**AstroMan**</span></span>
    * <span data-ttu-id="85cef-189">**Lights**</span><span class="sxs-lookup"><span data-stu-id="85cef-189">**Lights**</span></span>
    * <span data-ttu-id="85cef-190">**SpaceAudioSource**</span><span class="sxs-lookup"><span data-stu-id="85cef-190">**SpaceAudioSource**</span></span>
    * <span data-ttu-id="85cef-191">**SpaceBackground**</span><span class="sxs-lookup"><span data-stu-id="85cef-191">**SpaceBackground**</span></span>
6. <span data-ttu-id="85cef-192">Starten Sie **spielen Modus** ▶ der Astronautenausweis anzeigen.</span><span class="sxs-lookup"><span data-stu-id="85cef-192">Start **Play Mode** ▶ to view the astronaut.</span></span>
7. <span data-ttu-id="85cef-193">Klicken Sie auf **spielen Modus** ▶ erneut aus, um **beenden**.</span><span class="sxs-lookup"><span data-stu-id="85cef-193">Click **Play Mode** ▶ again to **Stop**.</span></span>
8. <span data-ttu-id="85cef-194">In der **Hologramme** Ordner finden Sie die **Fitbox** Asset und ziehen Sie es in das Stammverzeichnis des der **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="85cef-194">In the **Holograms** folder, find the **Fitbox** asset and drag it to the root of the **Hierarchy**.</span></span>
9. <span data-ttu-id="85cef-195">Wählen Sie die **Fitbox** in die **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="85cef-195">Select the **Fitbox** in the **Hierarchy** panel.</span></span>
10. <span data-ttu-id="85cef-196">Ziehen Sie die **AstroMan** Auflistung von der **Hierarchie** zu der **– Hologramm Auflistung** Eigenschaft der Fitbox in der **Inspector** Bereich.</span><span class="sxs-lookup"><span data-stu-id="85cef-196">Drag the **AstroMan** collection from the **Hierarchy** to the **Hologram Collection** property of the Fitbox in the **Inspector** panel.</span></span>

### <a name="save-the-project"></a><span data-ttu-id="85cef-197">Speichern Sie das Projekt</span><span class="sxs-lookup"><span data-stu-id="85cef-197">Save the project</span></span>

1. <span data-ttu-id="85cef-198">Speichern Sie die neue Szene: **Datei > Szene speichern unter**.</span><span class="sxs-lookup"><span data-stu-id="85cef-198">Save the new scene: **File > Save Scene As**.</span></span>
2. <span data-ttu-id="85cef-199">Klicken Sie auf **neuer Ordner** und nennen Sie den Ordner **Szenen**.</span><span class="sxs-lookup"><span data-stu-id="85cef-199">Click **New Folder** and name the folder **Scenes**.</span></span>
3. <span data-ttu-id="85cef-200">Nennen Sie die Datei "**ModelExplorer**", und speichern Sie ihn in das **Szenen** Ordner.</span><span class="sxs-lookup"><span data-stu-id="85cef-200">Name the file “**ModelExplorer**” and save it in the **Scenes** folder.</span></span>

### <a name="build-the-project"></a><span data-ttu-id="85cef-201">Erstellen Sie das Projekt</span><span class="sxs-lookup"><span data-stu-id="85cef-201">Build the project</span></span>

1. <span data-ttu-id="85cef-202">Wählen Sie in Unity **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="85cef-202">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="85cef-203">Klicken Sie auf **öffnen Szenen hinzufügen** die Szene hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="85cef-203">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="85cef-204">Wählen Sie **universelle Windows-Plattform** in die **Plattform** aus, und klicken Sie auf **Plattform wechseln**.</span><span class="sxs-lookup"><span data-stu-id="85cef-204">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="85cef-205">Wenn Sie speziell für HoloLens entwickeln, legen Sie **Zielgerät** zu **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="85cef-205">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="85cef-206">Andernfalls lassen Sie es auf **jedes Gerät**.</span><span class="sxs-lookup"><span data-stu-id="85cef-206">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="85cef-207">Stellen Sie sicher **Build Type** nastaven NA hodnotu **D3D** und **SDK** nastaven NA hodnotu **zuletzt installierte** (die sollte SDK 16299 oder höher sein).</span><span class="sxs-lookup"><span data-stu-id="85cef-207">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="85cef-208">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="85cef-208">Click **Build**.</span></span>
7. <span data-ttu-id="85cef-209">Erstellen Sie eine **neuer Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="85cef-209">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="85cef-210">Mausklick die **App** Ordner.</span><span class="sxs-lookup"><span data-stu-id="85cef-210">Single click the **App** folder.</span></span>
9. <span data-ttu-id="85cef-211">Drücken Sie **wählen Sie Ordner**.</span><span class="sxs-lookup"><span data-stu-id="85cef-211">Press **Select Folder**.</span></span>

<span data-ttu-id="85cef-212">Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="85cef-212">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="85cef-213">Öffnen der **App** Ordner.</span><span class="sxs-lookup"><span data-stu-id="85cef-213">Open the **App** folder.</span></span>
2. <span data-ttu-id="85cef-214">Öffnen der **ModelExplorer Visual Studio-Projektmappe**.</span><span class="sxs-lookup"><span data-stu-id="85cef-214">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="85cef-215">Wenn für HoloLens bereitstellen zu können:</span><span class="sxs-lookup"><span data-stu-id="85cef-215">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="85cef-216">Verwenden obere auf der Symbolleiste in Visual Studio, ändern Sie das Ziel vom Debugmodus in den **Version** und ARM, **X86**.</span><span class="sxs-lookup"><span data-stu-id="85cef-216">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="85cef-217">Klicken Sie auf den Dropdownpfeil neben der Schaltfläche mit den lokalen Computer, und wählen **Remotecomputer**.</span><span class="sxs-lookup"><span data-stu-id="85cef-217">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="85cef-218">Geben Sie **die HoloLens-Geräte-IP-Adresse** und legen Sie den Authentifizierungsmodus auf **universell (unverschlüsseltes Protokoll)**.</span><span class="sxs-lookup"><span data-stu-id="85cef-218">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="85cef-219">Klicken Sie auf **Auswählen**.</span><span class="sxs-lookup"><span data-stu-id="85cef-219">Click **Select**.</span></span> <span data-ttu-id="85cef-220">Wenn Sie Ihre IP-Adresse des Geräts nicht kennen, suchen Sie im **Einstellungen > Netzwerk und Internet > Erweiterte Optionen**.</span><span class="sxs-lookup"><span data-stu-id="85cef-220">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="85cef-221">Klicken Sie in der Menüleiste im oberen Bereich auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="85cef-221">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="85cef-222">Ist dies beim ersten auf Ihrem Gerät bereitstellen, Sie müssen [verbinden Sie es mit Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="85cef-222">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="85cef-223">Wenn die app bereitgestellt wurde, schließen die **Fitbox** mit eine **wählen Sie die Bewegung**.</span><span class="sxs-lookup"><span data-stu-id="85cef-223">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="85cef-224">Wenn eine immersive Kopfhörer bereitstellen:</span><span class="sxs-lookup"><span data-stu-id="85cef-224">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="85cef-225">Verwenden obere auf der Symbolleiste in Visual Studio, ändern Sie das Ziel vom Debugmodus in den **Version** und ARM, **X64**.</span><span class="sxs-lookup"><span data-stu-id="85cef-225">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="85cef-226">Stellen Sie sicher, dass das Bereitstellungsziel nastaven NA hodnotu **lokalen Computer**.</span><span class="sxs-lookup"><span data-stu-id="85cef-226">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="85cef-227">Klicken Sie in der Menüleiste im oberen Bereich auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="85cef-227">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="85cef-228">Wenn die app bereitgestellt wurde, schließen die **Fitbox** den Trigger ein Controller während der Übertragung zu ziehen.</span><span class="sxs-lookup"><span data-stu-id="85cef-228">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

## <a name="chapter-2---cursor-and-target-feedback"></a><span data-ttu-id="85cef-229">Kapitel 2 – Cursor und Ziel-Feedback</span><span class="sxs-lookup"><span data-stu-id="85cef-229">Chapter 2 - Cursor and target feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a><span data-ttu-id="85cef-230">Ziele</span><span class="sxs-lookup"><span data-stu-id="85cef-230">Objectives</span></span>

* <span data-ttu-id="85cef-231">Cursor visueller Entwurf und das Verhalten.</span><span class="sxs-lookup"><span data-stu-id="85cef-231">Cursor visual design and behavior.</span></span>
* <span data-ttu-id="85cef-232">Cursor Blicke basierende Feedback.</span><span class="sxs-lookup"><span data-stu-id="85cef-232">Gaze-based cursor feedback.</span></span>
* <span data-ttu-id="85cef-233">Blicke basierende – Hologramm Feedback.</span><span class="sxs-lookup"><span data-stu-id="85cef-233">Gaze-based hologram feedback.</span></span>

<span data-ttu-id="85cef-234">Wir werden unsere Arbeit einige Entwurfsprinzipien, Cursor, d. h. als Grundlage für:</span><span class="sxs-lookup"><span data-stu-id="85cef-234">We're going to base our work on some cursor design principles, namely:</span></span>

* <span data-ttu-id="85cef-235">Der Cursor ist immer vorhanden.</span><span class="sxs-lookup"><span data-stu-id="85cef-235">The cursor is always present.</span></span>
* <span data-ttu-id="85cef-236">Lassen Sie nicht den Cursor zu klein oder groß zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="85cef-236">Don't let the cursor get too small or big.</span></span>
* <span data-ttu-id="85cef-237">Vermeiden Sie die Inhalte sitzt.</span><span class="sxs-lookup"><span data-stu-id="85cef-237">Avoid obstructing content.</span></span>

### <a name="instructions"></a><span data-ttu-id="85cef-238">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="85cef-238">Instructions</span></span>

1. <span data-ttu-id="85cef-239">In der **HoloToolkit\Input\Prefabs** Ordner finden Sie die **InputManager** Asset.</span><span class="sxs-lookup"><span data-stu-id="85cef-239">In the **HoloToolkit\Input\Prefabs** folder, find the **InputManager** asset.</span></span>
2. <span data-ttu-id="85cef-240">Drag & drop die **InputManager** auf die **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="85cef-240">Drag and drop the **InputManager** onto the **Hierarchy**.</span></span>
3. <span data-ttu-id="85cef-241">In der **HoloToolkit\Input\Prefabs** Ordner finden Sie die **Cursor** Asset.</span><span class="sxs-lookup"><span data-stu-id="85cef-241">In the **HoloToolkit\Input\Prefabs** folder, find the **Cursor** asset.</span></span>
4. <span data-ttu-id="85cef-242">Drag & drop die **Cursor** auf die **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="85cef-242">Drag and drop the **Cursor** onto the **Hierarchy**.</span></span>
5. <span data-ttu-id="85cef-243">Wählen Sie die **InputManager** -Objekt in der **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="85cef-243">Select the **InputManager** object in the **Hierarchy**.</span></span>
6. <span data-ttu-id="85cef-244">Ziehen Sie die **Cursor** -Objekt aus der **Hierarchie** in die InputManager des **SimpleSinglePointerSelector**des **Cursor** Feld auf der Ende der **Inspektor**.</span><span class="sxs-lookup"><span data-stu-id="85cef-244">Drag the **Cursor** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>

![Einfache Einrichtung für einfache Zeiger-Auswahl](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a><span data-ttu-id="85cef-246">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="85cef-246">Build and Deploy</span></span>

1. <span data-ttu-id="85cef-247">Erstellen Sie die app neu **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="85cef-247">Rebuild the app from **File > Build Settings**.</span></span>
2. <span data-ttu-id="85cef-248">Öffnen der **App-Ordner**.</span><span class="sxs-lookup"><span data-stu-id="85cef-248">Open the **App folder**.</span></span>
3. <span data-ttu-id="85cef-249">Öffnen der **ModelExplorer Visual Studio-Projektmappe**.</span><span class="sxs-lookup"><span data-stu-id="85cef-249">Open the **ModelExplorer Visual Studio Solution**.</span></span>
4. <span data-ttu-id="85cef-250">Klicken Sie auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="85cef-250">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
5. <span data-ttu-id="85cef-251">Beachten Sie, wie der Cursor gezeichnet wird und wie es die Darstellung sich ändert, wenn er ggf. ein Hologramm berührt wird.</span><span class="sxs-lookup"><span data-stu-id="85cef-251">Observe how the cursor is drawn, and how it changes appearance if it is touching a hologram.</span></span>

### <a name="instructions"></a><span data-ttu-id="85cef-252">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="85cef-252">Instructions</span></span>

1. <span data-ttu-id="85cef-253">In der **Hierarchie** erweitern Sie die **AstroMan**->**GEO_G**->**Back_Center** Objekt.</span><span class="sxs-lookup"><span data-stu-id="85cef-253">In the **Hierarchy** panel, expand the **AstroMan**->**GEO_G**->**Back_Center** object.</span></span>
2. <span data-ttu-id="85cef-254">Klicken Sie mit der Doppelklicken auf **Interactible.cs** um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="85cef-254">Double click on **Interactible.cs** to open it in Visual Studio.</span></span>
3. <span data-ttu-id="85cef-255">Auskommentierung der Zeilen in der **IFocusable.OnFocusEnter()** und **IFocusable.OnFocusExit()** Rückrufe in **Interactible.cs**.</span><span class="sxs-lookup"><span data-stu-id="85cef-255">Uncomment the lines in the **IFocusable.OnFocusEnter()** and **IFocusable.OnFocusExit()** callbacks in **Interactible.cs**.</span></span> <span data-ttu-id="85cef-256">Diese werden durch das Mixed Reality-Toolkit InputManager bezeichnet, liegt der Fokus (entweder durch Blicke oder Controller zeigen) eingibt und das spezifische "gameobject" "collider" beendet.</span><span class="sxs-lookup"><span data-stu-id="85cef-256">These are called by the Mixed Reality Toolkit's InputManager when focus (either by gaze or by controller pointing) enters and exits the specific GameObject's collider.</span></span>

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
><span data-ttu-id="85cef-257">Wir verwenden `EnableKeyword` und `DisableKeyword` oben.</span><span class="sxs-lookup"><span data-stu-id="85cef-257">We use `EnableKeyword` and `DisableKeyword` above.</span></span> <span data-ttu-id="85cef-258">Um machen diese in Ihre eigene app mit Standard-Shader des Toolkits verwenden, müssen Sie folgen den [Unity-Richtlinien für den Zugriff auf Materialien über ein Skript](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span><span class="sxs-lookup"><span data-stu-id="85cef-258">In order to make use of these in your own app with the Toolkit's Standard shader, you'll need to follow the [Unity guidelines for accessing materials via script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span></span> <span data-ttu-id="85cef-259">In diesem Fall haben wir bereits enthalten die [drei Varianten von hervorgehobenen Material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) in den Ordner "Resources" (Suchen Sie nach den drei Materialien mit Hervorhebung im Namen) erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="85cef-259">In this case, we've already included the [three variants of highlighted material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) needed in the Resources folder (look for the three materials with highlight in the name).</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="85cef-260">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="85cef-260">Build and Deploy</span></span>

1. <span data-ttu-id="85cef-261">Wie zuvor, erstellen Sie das Projekt aus, und stellen in die HoloLens.</span><span class="sxs-lookup"><span data-stu-id="85cef-261">As before, build the project and deploy to the HoloLens.</span></span>
2. <span data-ttu-id="85cef-262">Beachten Sie, was geschieht, wenn ein Objekt die Blicke gedacht ist und wenn es nicht ist.</span><span class="sxs-lookup"><span data-stu-id="85cef-262">Observe what happens when the gaze is aimed at an object and when it's not.</span></span>

## <a name="chapter-3---targeting-techniques"></a><span data-ttu-id="85cef-263">Kapitel 3 – Methoden für</span><span class="sxs-lookup"><span data-stu-id="85cef-263">Chapter 3 - Targeting Techniques</span></span>

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a><span data-ttu-id="85cef-264">Ziele</span><span class="sxs-lookup"><span data-stu-id="85cef-264">Objectives</span></span>

* <span data-ttu-id="85cef-265">Erleichtern Sie es, Ziel-Hologramme.</span><span class="sxs-lookup"><span data-stu-id="85cef-265">Make it easier to target holograms.</span></span>
* <span data-ttu-id="85cef-266">Stabilisieren Sie natürliche Head Verschiebungen.</span><span class="sxs-lookup"><span data-stu-id="85cef-266">Stabilize natural head movements.</span></span>

### <a name="instructions"></a><span data-ttu-id="85cef-267">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="85cef-267">Instructions</span></span>

1. <span data-ttu-id="85cef-268">In der **Hierarchie** wählen die **InputManager** Objekt.</span><span class="sxs-lookup"><span data-stu-id="85cef-268">In the **Hierarchy** panel, select the **InputManager** object.</span></span>
2. <span data-ttu-id="85cef-269">In der **Inspektor** Bereich, suchen Sie nach der **bestaunen Stabilisierung** Skript.</span><span class="sxs-lookup"><span data-stu-id="85cef-269">In the **Inspector** panel, find the **Gaze Stabilizer** script.</span></span> <span data-ttu-id="85cef-270">Klicken Sie in Visual Studio, öffnen sie das, wenn Sie sich ansehen möchten.</span><span class="sxs-lookup"><span data-stu-id="85cef-270">Click it to open in Visual Studio, if you want to take a look.</span></span>
    * <span data-ttu-id="85cef-271">Dieses Skript führt eine Iteration durch Beispiele von Raycast Daten und hilft dabei, Blicke des Benutzers, für die Ziel-Genauigkeit zu stabilisieren.</span><span class="sxs-lookup"><span data-stu-id="85cef-271">This script iterates over samples of Raycast data and helps stabilize the user's gaze for precision targeting.</span></span>
3. <span data-ttu-id="85cef-272">In der **Inspektor**, können Sie bearbeiten die **gespeicherten Stabilität Beispiele** Wert.</span><span class="sxs-lookup"><span data-stu-id="85cef-272">In the **Inspector**, you can edit the **Stored Stability Samples** value.</span></span> <span data-ttu-id="85cef-273">Dieser Wert stellt die Anzahl der Samplings, denen an der Stabilisierung durchläuft den stabilisierten Wert zu berechnen.</span><span class="sxs-lookup"><span data-stu-id="85cef-273">This value represents the number of samples that the stabilizer iterates on to calculate the stabilized value.</span></span>

## <a name="chapter-4---directional-indicator"></a><span data-ttu-id="85cef-274">Kapitel 4 – richtungsindikator</span><span class="sxs-lookup"><span data-stu-id="85cef-274">Chapter 4 - Directional indicator</span></span>

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a><span data-ttu-id="85cef-275">Ziele</span><span class="sxs-lookup"><span data-stu-id="85cef-275">Objectives</span></span>

* <span data-ttu-id="85cef-276">Hinzufügen einer richtungsindikator für den Cursor, um Hologramme zu finden.</span><span class="sxs-lookup"><span data-stu-id="85cef-276">Add a directional indicator on the cursor to help find holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="85cef-277">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="85cef-277">Instructions</span></span>

<span data-ttu-id="85cef-278">Wir verwenden wollen die **DirectionIndicator.cs** Datei die:</span><span class="sxs-lookup"><span data-stu-id="85cef-278">We're going to use the **DirectionIndicator.cs** file which will:</span></span>

1. <span data-ttu-id="85cef-279">Zeigen Sie die richtungsindikator aus, wenn der Benutzer nicht auf die Hologramme gazing ist.</span><span class="sxs-lookup"><span data-stu-id="85cef-279">Show the directional indicator if the user is not gazing at the holograms.</span></span>
2. <span data-ttu-id="85cef-280">Blenden Sie die richtungsindikator aus, wenn der Benutzer auf die Hologramme gazing ist.</span><span class="sxs-lookup"><span data-stu-id="85cef-280">Hide the directional indicator if the user is gazing at the holograms.</span></span>
3. <span data-ttu-id="85cef-281">Aktualisieren Sie die richtungsindikator, um auf die Hologramme zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="85cef-281">Update the directional indicator to point to the holograms.</span></span>

<span data-ttu-id="85cef-282">Los geht's.</span><span class="sxs-lookup"><span data-stu-id="85cef-282">Let's get started.</span></span>

1. <span data-ttu-id="85cef-283">Klicken Sie auf die **AstroMan** -Objekt in der **Hierarchie** Bereich und **klicken Sie auf den Pfeil** um ihn zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="85cef-283">Click on the **AstroMan** object in the **Hierarchy** panel and **click the arrow** to expand it.</span></span>
2. <span data-ttu-id="85cef-284">In der **Hierarchie** wählen die **DirectionalIndicator** Objekt unter **AstroMan**.</span><span class="sxs-lookup"><span data-stu-id="85cef-284">In the **Hierarchy** panel, select the **DirectionalIndicator** object under **AstroMan**.</span></span>
3. <span data-ttu-id="85cef-285">In der **Inspektor** Bereich, klicken Sie auf die **Add Component** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="85cef-285">In the **Inspector** panel, click the **Add Component** button.</span></span>
4. <span data-ttu-id="85cef-286">Geben Sie im Menü, in das Suchfeld **Indikator für die Verweisrichtung**.</span><span class="sxs-lookup"><span data-stu-id="85cef-286">In the menu, type in the search box **Direction Indicator**.</span></span> <span data-ttu-id="85cef-287">Wählen Sie das Suchergebnis.</span><span class="sxs-lookup"><span data-stu-id="85cef-287">Select the search result.</span></span>
5. <span data-ttu-id="85cef-288">In der **Hierarchie** Bereich drag und drop der **Cursor** -Objekt auf die **Cursor** -Eigenschaft in der **Inspektor**.</span><span class="sxs-lookup"><span data-stu-id="85cef-288">In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector**.</span></span>
6. <span data-ttu-id="85cef-289">In der **Projekt** im Bereich der **Hologramme** Ordner Drag & Drop die **DirectionalIndicator** Medienobjekt, auf die **Richtungsindikator**-Eigenschaft in der **Inspektor**.</span><span class="sxs-lookup"><span data-stu-id="85cef-289">In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector**.</span></span>
7. <span data-ttu-id="85cef-290">Erstellen und Bereitstellen der app.</span><span class="sxs-lookup"><span data-stu-id="85cef-290">Build and deploy the app.</span></span>
8. <span data-ttu-id="85cef-291">Sehen Sie sich, wie das richtungsindikator-Objekt die Astronautenausweis finden kann.</span><span class="sxs-lookup"><span data-stu-id="85cef-291">Watch how the directional indicator object helps you find the astronaut.</span></span>

## <a name="chapter-5---billboarding"></a><span data-ttu-id="85cef-292">Kapitel 5 – Billboarding</span><span class="sxs-lookup"><span data-stu-id="85cef-292">Chapter 5 - Billboarding</span></span>

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a><span data-ttu-id="85cef-293">Ziele</span><span class="sxs-lookup"><span data-stu-id="85cef-293">Objectives</span></span>

* <span data-ttu-id="85cef-294">Mit der billboarding Hologramme immer zu Ihnen hin auftreten müssen.</span><span class="sxs-lookup"><span data-stu-id="85cef-294">Use billboarding to have holograms always face towards you.</span></span>

<span data-ttu-id="85cef-295">Wir verwenden die **Billboard.cs** Datei zu einem "gameobject" ausgerichtet, dass es immer den Benutzer zeigt.</span><span class="sxs-lookup"><span data-stu-id="85cef-295">We will be using the **Billboard.cs** file to keep a GameObject oriented such that it is facing the user at all times.</span></span>

1. <span data-ttu-id="85cef-296">In der **Hierarchie** wählen die **AstroMan** Objekt.</span><span class="sxs-lookup"><span data-stu-id="85cef-296">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
2. <span data-ttu-id="85cef-297">In der **Inspektor** Bereich, klicken Sie auf die **Add Component** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="85cef-297">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="85cef-298">Geben Sie im Menü, in das Suchfeld **Billboard**.</span><span class="sxs-lookup"><span data-stu-id="85cef-298">In the menu, type in the search box **Billboard**.</span></span> <span data-ttu-id="85cef-299">Wählen Sie das Suchergebnis.</span><span class="sxs-lookup"><span data-stu-id="85cef-299">Select the search result.</span></span>
4. <span data-ttu-id="85cef-300">In der **Inspektor** legen Sie die **Pivot Achse** zu **Y**.</span><span class="sxs-lookup"><span data-stu-id="85cef-300">In the **Inspector** set the **Pivot Axis** to **Y**.</span></span>
5. <span data-ttu-id="85cef-301">Probieren Sie es aus!</span><span class="sxs-lookup"><span data-stu-id="85cef-301">Try it!</span></span> <span data-ttu-id="85cef-302">Erstellen und Bereitstellen der app als vor.</span><span class="sxs-lookup"><span data-stu-id="85cef-302">Build and deploy the app as before.</span></span>
6. <span data-ttu-id="85cef-303">Sehen Sie, wie Gesichter Sie stattdessen das Billboard unabhängig davon, wie Sie den Standpunkt ändern.</span><span class="sxs-lookup"><span data-stu-id="85cef-303">See how the Billboard object faces you no matter how you change the viewpoint.</span></span>
7. <span data-ttu-id="85cef-304">Löschen Sie das Skript aus dem **AstroMan** jetzt.</span><span class="sxs-lookup"><span data-stu-id="85cef-304">Delete the script from the **AstroMan** for now.</span></span>

## <a name="chapter-6---tag-along"></a><span data-ttu-id="85cef-305">Kapitel 6 – Tag-Along</span><span class="sxs-lookup"><span data-stu-id="85cef-305">Chapter 6 - Tag-Along</span></span>

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a><span data-ttu-id="85cef-306">Ziele</span><span class="sxs-lookup"><span data-stu-id="85cef-306">Objectives</span></span>

* <span data-ttu-id="85cef-307">Verwenden Sie Tag-Along, um unsere Hologramme uns im Raum Folgen haben.</span><span class="sxs-lookup"><span data-stu-id="85cef-307">Use Tag-Along to have our holograms follow us around the room.</span></span>

<span data-ttu-id="85cef-308">Wie wir zu diesem Problem arbeiten, müssen wir durch die folgenden Einschränkungen beim Entwurf geführt:</span><span class="sxs-lookup"><span data-stu-id="85cef-308">As we work on this issue, we'll be guided by the following design constraints:</span></span>

* <span data-ttu-id="85cef-309">Der Inhalt muss immer sofort ein Blick entsprechen.</span><span class="sxs-lookup"><span data-stu-id="85cef-309">Content should always be a glance away.</span></span>
* <span data-ttu-id="85cef-310">Inhalt darf nicht auf die Weise sein.</span><span class="sxs-lookup"><span data-stu-id="85cef-310">Content should not be in the way.</span></span>
* <span data-ttu-id="85cef-311">Head-Sperren Inhalt ist unangenehm.</span><span class="sxs-lookup"><span data-stu-id="85cef-311">Head-locking content is uncomfortable.</span></span>

<span data-ttu-id="85cef-312">Die hier verwendete Lösung ist die Verwendung ein Ansatzes "Tag-along".</span><span class="sxs-lookup"><span data-stu-id="85cef-312">The solution used here is to use a "tag-along" approach.</span></span>

<span data-ttu-id="85cef-313">Ein Objekt Tag-along verlässt nie vollständig die Ansicht des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="85cef-313">A tag-along object never fully leaves the user's view.</span></span> <span data-ttu-id="85cef-314">Stellen Sie sich die einer Tag-along als ein Objekt des Benutzers Head von weiche Ränder hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="85cef-314">You can think of the a tag-along as being an object attached to the user's head by rubber bands.</span></span> <span data-ttu-id="85cef-315">Wenn der Benutzer bewegt, bleibt der Inhalt in einen Blick einfach, indem er auf den Rand der Ansicht ohne vollständig mit.</span><span class="sxs-lookup"><span data-stu-id="85cef-315">As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving.</span></span> <span data-ttu-id="85cef-316">Wenn der Benutzer auf das Objekt Tag-along gazes, erfolgt genauer an.</span><span class="sxs-lookup"><span data-stu-id="85cef-316">When the user gazes towards the tag-along object, it comes more fully into view.</span></span>

<span data-ttu-id="85cef-317">Wir verwenden wollen die **SimpleTagalong.cs** Datei die:</span><span class="sxs-lookup"><span data-stu-id="85cef-317">We're going to use the **SimpleTagalong.cs** file which will:</span></span>

1. <span data-ttu-id="85cef-318">Bestimmt, ob das Tag-Along Objekt in dem kameragrenzen befindet.</span><span class="sxs-lookup"><span data-stu-id="85cef-318">Determine if the Tag-Along object is within the camera bounds.</span></span>
2. <span data-ttu-id="85cef-319">Wenn dies nicht in der Frustums anzeigen, positionieren Sie die Tag-Along, teilweise in der Ansicht Frustums.</span><span class="sxs-lookup"><span data-stu-id="85cef-319">If not within the view frustum, position the Tag-Along to partially within the view frustum.</span></span>
3. <span data-ttu-id="85cef-320">Positionieren Sie die Tag-Along, andernfalls zu einer Standard-Entfernung des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="85cef-320">Otherwise, position the Tag-Along to a default distance from the user.</span></span>

<span data-ttu-id="85cef-321">Zu diesem Zweck zunächst muss ändern wir die **Interactible.cs** Skript zum Aufrufen der **TagalongAction**.</span><span class="sxs-lookup"><span data-stu-id="85cef-321">To do this, we first must change the **Interactible.cs** script to call the **TagalongAction**.</span></span>

1. <span data-ttu-id="85cef-322">Bearbeiten Sie **Interactible.cs** üben Sie nach Abschluss der Codierung 6.a (Aufheben der auskommentierung Zeilen 84 zu 87).</span><span class="sxs-lookup"><span data-stu-id="85cef-322">Edit **Interactible.cs** by completing coding exercise 6.a (uncommenting lines 84 to 87).</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

<span data-ttu-id="85cef-323">Die **InteractibleAction.cs** Skript zusammen mit **Interactible.cs** werden benutzerdefinierte Aktionen ausgeführt, wenn Sie auf Hologramme tippen.</span><span class="sxs-lookup"><span data-stu-id="85cef-323">The **InteractibleAction.cs** script, paired with **Interactible.cs** performs custom actions when you tap on holograms.</span></span> <span data-ttu-id="85cef-324">In diesem Fall verwenden wir eine speziell für Tag-along.</span><span class="sxs-lookup"><span data-stu-id="85cef-324">In this case, we'll use one specifically for tag-along.</span></span>

* <span data-ttu-id="85cef-325">In der **Skripts** Ordner, klicken Sie auf **TagalongAction.cs** Medienobjekt in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="85cef-325">In the **Scripts** folder click on **TagalongAction.cs** asset to open in Visual Studio.</span></span>
* <span data-ttu-id="85cef-326">Führen Sie in dieser Übung Schreiben von Code aus oder ändern Sie ihn folgendermaßen:</span><span class="sxs-lookup"><span data-stu-id="85cef-326">Complete the coding exercise or change it to this:</span></span>
  * <span data-ttu-id="85cef-327">Am oberen Rand der **Hierarchie**, in der Leiste Suchtyp **ChestButton_Center** , und wählen Sie das Ergebnis.</span><span class="sxs-lookup"><span data-stu-id="85cef-327">At the top of the **Hierarchy**, in the search bar type **ChestButton_Center** and select the result.</span></span>
  * <span data-ttu-id="85cef-328">In der **Inspektor** Bereich, klicken Sie auf die **Add Component** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="85cef-328">In the **Inspector** panel, click the **Add Component** button.</span></span>
  * <span data-ttu-id="85cef-329">Geben Sie im Menü, in das Suchfeld **beigefügten Aktion**.</span><span class="sxs-lookup"><span data-stu-id="85cef-329">In the menu, type in the search box **Tagalong Action**.</span></span> <span data-ttu-id="85cef-330">Wählen Sie das Suchergebnis.</span><span class="sxs-lookup"><span data-stu-id="85cef-330">Select the search result.</span></span>
  * <span data-ttu-id="85cef-331">In **Hologramme** Ordner suchen der **beigefügten** Asset.</span><span class="sxs-lookup"><span data-stu-id="85cef-331">In **Holograms** folder find the **Tagalong** asset.</span></span>
  * <span data-ttu-id="85cef-332">Wählen Sie die **ChestButton_Center** -Objekt in der **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="85cef-332">Select the **ChestButton_Center** object in the **Hierarchy**.</span></span> <span data-ttu-id="85cef-333">Drag & drop die **beigefügten** -Objekt aus der **Projekt** panel auf die **Inspektor** in die **Objekt um beigefügten** Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="85cef-333">Drag and drop the **TagAlong** object from the **Project** panel onto the **Inspector** into the **Object To Tagalong** property.</span></span>
  * <span data-ttu-id="85cef-334">Ziehen Sie die **beigefügten Aktion** -Objekt aus der **Inspektor** in die **Interactible Aktion** Feld der **Interactible** Skript.</span><span class="sxs-lookup"><span data-stu-id="85cef-334">Drag the **Tagalong Action** object from the **Inspector** into the **Interactible Action** field on the **Interactible** script.</span></span>
* <span data-ttu-id="85cef-335">Klicken Sie mit der Doppelklicken auf die **TagalongAction** Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="85cef-335">Double click the **TagalongAction** script to open it in Visual Studio.</span></span>

![Interactible einrichten](images/holograms210-interactible.png)

<span data-ttu-id="85cef-337">Wir müssen die folgenden hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="85cef-337">We need to add the following:</span></span>

* <span data-ttu-id="85cef-338">Fügen Sie Funktionen für die PerformAction-Funktion im Skript TagalongAction (geerbt von InteractibleAction) hinzu.</span><span class="sxs-lookup"><span data-stu-id="85cef-338">Add functionality to the PerformAction function in the TagalongAction script (inherited from InteractibleAction).</span></span>
* <span data-ttu-id="85cef-339">Fügen Sie die auf das Objekt gazed bei billboarding, und legen Sie die PowerPivot-Achse auf der XY.</span><span class="sxs-lookup"><span data-stu-id="85cef-339">Add billboarding to the gazed-upon object, and set the pivot axis to XY.</span></span>
* <span data-ttu-id="85cef-340">Fügen Sie einfach Tag-Along klicken Sie dann auf das Objekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="85cef-340">Then add simple Tag-Along to the object.</span></span>

<span data-ttu-id="85cef-341">Hier ist unsere Lösung aus **TagalongAction.cs**:</span><span class="sxs-lookup"><span data-stu-id="85cef-341">Here's our solution, from **TagalongAction.cs**:</span></span>

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

* <span data-ttu-id="85cef-342">Probieren Sie es aus!</span><span class="sxs-lookup"><span data-stu-id="85cef-342">Try it!</span></span> <span data-ttu-id="85cef-343">Erstellen und Bereitstellen der app.</span><span class="sxs-lookup"><span data-stu-id="85cef-343">Build and deploy the app.</span></span>
* <span data-ttu-id="85cef-344">Sehen Sie sich, wie der Inhalt die Mitte des Punkts Blicke, folgt jedoch nicht fortlaufend und ohne dass sie blockiert.</span><span class="sxs-lookup"><span data-stu-id="85cef-344">Watch how the content follows the center of the gaze point, but not continuously and without blocking it.</span></span>
