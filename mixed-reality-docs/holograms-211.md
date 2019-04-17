---
title: MR Eingabe 211 - Bewegung
description: Führen Sie diese Codierung Exemplarische Vorgehensweise, HoloLens, Unity und Visual Studio verwenden, um die Details der Bewegung Konzepte zu erfahren.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academy, tutorial, gesture
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596147"
---
>[!NOTE]
><span data-ttu-id="74ec4-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="74ec4-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="74ec4-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="74ec4-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="74ec4-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="74ec4-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="74ec4-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="74ec4-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="74ec4-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="74ec4-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="74ec4-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="74ec4-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-211-gesture"></a><span data-ttu-id="74ec4-110">MR Eingabe 211: Geste</span><span class="sxs-lookup"><span data-stu-id="74ec4-110">MR Input 211: Gesture</span></span>

<span data-ttu-id="74ec4-111">[Bewegungen](gestures.md) Absicht Benutzers in Aktion zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="74ec4-111">[Gestures](gestures.md) turn user intention into action.</span></span> <span data-ttu-id="74ec4-112">Bei den Bewegungen können Benutzer mit Hologramme interagieren.</span><span class="sxs-lookup"><span data-stu-id="74ec4-112">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="74ec4-113">In diesem Kurs erfahren wir, wie zum Nachverfolgen des Benutzers Hände auf Benutzereingaben reagieren, und Erteilen von Feedback an den Benutzer basierend auf Seite Zustand und den Speicherort.</span><span class="sxs-lookup"><span data-stu-id="74ec4-113">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="74ec4-114">In [MR Grundlagen 101](holograms-101.md), wir eine Geste für ein einfaches tippbewegung-Interaktion mit unserem Hologramme verwendet.</span><span class="sxs-lookup"><span data-stu-id="74ec4-114">In [MR Basics 101](holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="74ec4-115">Nun, wir über die tippbewegung Geste verschieben und neue Konzepte zu untersuchen:</span><span class="sxs-lookup"><span data-stu-id="74ec4-115">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="74ec4-116">Erkennen Sie, wenn der Benutzer manuell nachverfolgt wird, und geben Sie Feedback an den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="74ec4-116">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="74ec4-117">Verwenden Sie eine Geste für ein Navigationsbereich, um unsere Hologramme drehen.</span><span class="sxs-lookup"><span data-stu-id="74ec4-117">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="74ec4-118">Geben Sie Feedback, wenn des Benutzers manuell wird nicht aus der Sicht.</span><span class="sxs-lookup"><span data-stu-id="74ec4-118">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="74ec4-119">Verwenden Sie Manipulation-Ereignisse, damit Benutzer Hologramme mit der Hand verschieben können.</span><span class="sxs-lookup"><span data-stu-id="74ec4-119">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="74ec4-120">In diesem Kurs werden wir die Unity-Projekts überdenken **Modell-Explorer**, die wir erstellt [MR Eingabe 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="74ec4-120">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="74ec4-121">Unser Freund Astronautenausweis werden zurück an unserem Seminar diese neuen Konzepte für die Bewegung, uns beim unterstützen.</span><span class="sxs-lookup"><span data-stu-id="74ec4-121">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="74ec4-122">Die Videos in jeder der folgenden Kapitel eingebettet wurden mit einer älteren Version von Unity und dem Mixed Reality-Toolkit aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="74ec4-122">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="74ec4-123">Während die schrittweisen Anweisungen korrekt und aktuell sind, Sie möglicherweise Skripts und Visualisierungen in die entsprechenden Videos, die veraltet sind.</span><span class="sxs-lookup"><span data-stu-id="74ec4-123">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="74ec4-124">Die Videos aus Gründen der Posterity bleiben, und es aber trotzdem anwenden, da die Konzepte behandelt.</span><span class="sxs-lookup"><span data-stu-id="74ec4-124">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="74ec4-125">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="74ec4-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="74ec4-126">Kurs</span><span class="sxs-lookup"><span data-stu-id="74ec4-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="74ec4-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="74ec4-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="74ec4-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="74ec4-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="74ec4-129">MR Eingabe 211: Geste</span><span class="sxs-lookup"><span data-stu-id="74ec4-129">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="74ec4-130">✔️</span><span class="sxs-lookup"><span data-stu-id="74ec4-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="74ec4-131">✔️</span><span class="sxs-lookup"><span data-stu-id="74ec4-131">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="74ec4-132">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="74ec4-132">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="74ec4-133">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="74ec4-133">Prerequisites</span></span>

* <span data-ttu-id="74ec4-134">Ein Windows 10-PCs mit dem richtigen konfiguriert [-Tools installiert](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="74ec4-134">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="74ec4-135">Einige grundlegende C# Programmierkenntnisse.</span><span class="sxs-lookup"><span data-stu-id="74ec4-135">Some basic C# programming ability.</span></span>
* <span data-ttu-id="74ec4-136">Sie sollten abgeschlossen haben [MR Grundlagen 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="74ec4-136">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="74ec4-137">Sie sollten abgeschlossen haben [MR Eingabe 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="74ec4-137">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="74ec4-138">Ein Gerät HoloLens [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="74ec4-138">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="74ec4-139">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="74ec4-139">Project files</span></span>

* <span data-ttu-id="74ec4-140">Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) vom Projekt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="74ec4-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span><span data-ttu-id="74ec4-141"> Ist Unity 2017.2 oder höher erforderlich.</span><span class="sxs-lookup"><span data-stu-id="74ec4-141"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="74ec4-142">Un-Archive die Dateien auf dem Desktop oder andere einfach auf den Speicherort zugreifen.</span><span class="sxs-lookup"><span data-stu-id="74ec4-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="74ec4-143">Wenn Sie vor dem Herunterladen, den Quellcode ansehen möchten es [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span><span class="sxs-lookup"><span data-stu-id="74ec4-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="74ec4-144">Fehler und Anmerkungen zu dieser Version</span><span class="sxs-lookup"><span data-stu-id="74ec4-144">Errata and Notes</span></span>

* <span data-ttu-id="74ec4-145">"Nur eigenen Code aktivieren" muss deaktiviert sein (*deaktiviert*) in Visual Studio unter Extras -> Optionen-Debuggen >, um die Haltepunkte in Ihrem Code.</span><span class="sxs-lookup"><span data-stu-id="74ec4-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="74ec4-146">Kapitel 0 - Setup für Unity</span><span class="sxs-lookup"><span data-stu-id="74ec4-146">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="74ec4-147">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="74ec4-147">Instructions</span></span>

1. <span data-ttu-id="74ec4-148">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="74ec4-148">Start Unity.</span></span>
2. <span data-ttu-id="74ec4-149">Wählen Sie **öffnen**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-149">Select **Open**.</span></span>
3. <span data-ttu-id="74ec4-150">Navigieren Sie zu der **Geste** Ordner Sie zuvor nicht archiviert.</span><span class="sxs-lookup"><span data-stu-id="74ec4-150">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="74ec4-151">Suchen und Auswählen der **ab**/**Modell-Explorer** Ordner.</span><span class="sxs-lookup"><span data-stu-id="74ec4-151">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="74ec4-152">Klicken Sie auf die **Ordner auswählen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="74ec4-152">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="74ec4-153">In der **Projekt** erweitern Sie die **Szenen** Ordner.</span><span class="sxs-lookup"><span data-stu-id="74ec4-153">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="74ec4-154">Doppelklicken Sie auf **ModelExplorer** Szene, um es in Unity zu laden.</span><span class="sxs-lookup"><span data-stu-id="74ec4-154">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="74ec4-155">Erstellung</span><span class="sxs-lookup"><span data-stu-id="74ec4-155">Building</span></span>

1. <span data-ttu-id="74ec4-156">Wählen Sie in Unity **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-156">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="74ec4-157">Wenn **Szenen/ModelExplorer** in nicht aufgeführt ist **Szenen In Build**, klicken Sie auf **öffnen Szenen hinzufügen** die Szene hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="74ec4-157">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="74ec4-158">Wenn Sie speziell für HoloLens entwickeln, legen Sie **Zielgerät** zu **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-158">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="74ec4-159">Andernfalls lassen Sie es auf **jedes Gerät**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-159">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="74ec4-160">Stellen Sie sicher **Build Type** nastaven NA hodnotu **D3D** und **SDK** nastaven NA hodnotu **zuletzt installierte** (die sollte SDK 16299 oder höher sein).</span><span class="sxs-lookup"><span data-stu-id="74ec4-160">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="74ec4-161">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-161">Click **Build**.</span></span>
6. <span data-ttu-id="74ec4-162">Erstellen Sie eine **neuer Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="74ec4-162">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="74ec4-163">Mausklick die **App** Ordner.</span><span class="sxs-lookup"><span data-stu-id="74ec4-163">Single click the **App** folder.</span></span>
8. <span data-ttu-id="74ec4-164">Drücken Sie **Ordner auswählen** und Unity wird beim Erstellen des Projekts für Visual Studio gestartet.</span><span class="sxs-lookup"><span data-stu-id="74ec4-164">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="74ec4-165">Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="74ec4-165">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="74ec4-166">Öffnen der **App** Ordner.</span><span class="sxs-lookup"><span data-stu-id="74ec4-166">Open the **App** folder.</span></span>
2. <span data-ttu-id="74ec4-167">Öffnen der **ModelExplorer Visual Studio-Projektmappe**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-167">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="74ec4-168">Wenn für HoloLens bereitstellen zu können:</span><span class="sxs-lookup"><span data-stu-id="74ec4-168">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="74ec4-169">Verwenden obere auf der Symbolleiste in Visual Studio, ändern Sie das Ziel vom Debugmodus in den **Version** und ARM, **X86**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-169">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="74ec4-170">Klicken Sie auf den Dropdownpfeil neben der Schaltfläche mit den lokalen Computer, und wählen **Remotecomputer**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-170">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="74ec4-171">Geben Sie **die HoloLens-Geräte-IP-Adresse** und legen Sie den Authentifizierungsmodus auf **universell (unverschlüsseltes Protokoll)**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-171">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="74ec4-172">Klicken Sie auf **Auswählen**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-172">Click **Select**.</span></span> <span data-ttu-id="74ec4-173">Wenn Sie Ihre IP-Adresse des Geräts nicht kennen, suchen Sie im **Einstellungen > Netzwerk und Internet > Erweiterte Optionen**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-173">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="74ec4-174">Klicken Sie in der Menüleiste im oberen Bereich auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-174">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="74ec4-175">Ist dies beim ersten auf Ihrem Gerät bereitstellen, Sie müssen [verbinden Sie es mit Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="74ec4-175">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="74ec4-176">Wenn die app bereitgestellt wurde, schließen die **Fitbox** mit eine **wählen Sie die Bewegung**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-176">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="74ec4-177">Wenn eine immersive Kopfhörer bereitstellen:</span><span class="sxs-lookup"><span data-stu-id="74ec4-177">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="74ec4-178">Verwenden obere auf der Symbolleiste in Visual Studio, ändern Sie das Ziel vom Debugmodus in den **Version** und ARM, **X64**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="74ec4-179">Stellen Sie sicher, dass das Bereitstellungsziel nastaven NA hodnotu **lokalen Computer**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-179">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="74ec4-180">Klicken Sie in der Menüleiste im oberen Bereich auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-180">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="74ec4-181">Wenn die app bereitgestellt wurde, schließen die **Fitbox** den Trigger ein Controller während der Übertragung zu ziehen.</span><span class="sxs-lookup"><span data-stu-id="74ec4-181">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="74ec4-182">Sie können einige rote Fehler im Bereich von Visual Studio-Fehler feststellen.</span><span class="sxs-lookup"><span data-stu-id="74ec4-182">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="74ec4-183">Es kann gefahrlos ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="74ec4-183">It is safe to ignore them.</span></span> <span data-ttu-id="74ec4-184">Wechseln Sie zur Ausgabebereich tatsächliche anzeigen Fortschritt des Builds.</span><span class="sxs-lookup"><span data-stu-id="74ec4-184">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="74ec4-185">Fehler im Ausgabebereich ist erforderlich, Sie stellen eine Lösung (die meisten häufig durch einen Fehler in einem Skript, sie entstehen).</span><span class="sxs-lookup"><span data-stu-id="74ec4-185">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="74ec4-186">Kapitel 1 - Seite erkannt, feedback</span><span class="sxs-lookup"><span data-stu-id="74ec4-186">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="74ec4-187">Ziele</span><span class="sxs-lookup"><span data-stu-id="74ec4-187">Objectives</span></span>

* <span data-ttu-id="74ec4-188">Nachverfolgungsereignisse zur hand zu abonnieren.</span><span class="sxs-lookup"><span data-stu-id="74ec4-188">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="74ec4-189">Verwenden Sie Cursor Feedback, um Benutzern angezeigt, wenn eine Hand nachverfolgt wird.</span><span class="sxs-lookup"><span data-stu-id="74ec4-189">Use cursor feedback to show users when a hand is being tracked.</span></span>

### <a name="instructions"></a><span data-ttu-id="74ec4-190">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="74ec4-190">Instructions</span></span>

* <span data-ttu-id="74ec4-191">In der **Hierarchie** erweitern Sie die **InputManager** Objekt.</span><span class="sxs-lookup"><span data-stu-id="74ec4-191">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="74ec4-192">Suchen Sie nach, und wählen Sie die **GesturesInput** Objekt.</span><span class="sxs-lookup"><span data-stu-id="74ec4-192">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="74ec4-193">Die **InteractionInputSource.cs** Skript führt folgende Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="74ec4-193">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="74ec4-194">Abonniert die Ereignisse InteractionSourceDetected und InteractionSourceLost.</span><span class="sxs-lookup"><span data-stu-id="74ec4-194">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="74ec4-195">Legt den HandDetected-Zustand.</span><span class="sxs-lookup"><span data-stu-id="74ec4-195">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="74ec4-196">Kündigt das Abonnement die InteractionSourceDetected und InteractionSourceLost-Ereignisse.</span><span class="sxs-lookup"><span data-stu-id="74ec4-196">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="74ec4-197">Als Nächstes führen wir die der Cursor aus Aktualisierung [MR Eingabe 210](holograms-210.md) in eine, die Feedback je nach den Aktionen des Benutzers anzeigt.</span><span class="sxs-lookup"><span data-stu-id="74ec4-197">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="74ec4-198">In der **Hierarchie** wählen die **Cursor** Objekt aus, und löschen Sie sie.</span><span class="sxs-lookup"><span data-stu-id="74ec4-198">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="74ec4-199">In der **Projekt** Bereich, suchen Sie nach **CursorWithFeedback** , und ziehen Sie ihn in das **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="74ec4-199">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="74ec4-200">Klicken Sie auf **InputManager** in die **Hierarchie** Bereich, und ziehen Sie die **CursorWithFeedback** -Objekt aus der **Hierarchie** in der Die InputManager **SimpleSinglePointerSelector**des **Cursor** Feld am unteren Rand der **Inspektor**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-200">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="74ec4-201">Klicken Sie auf die **CursorWithFeedback** in die **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-201">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="74ec4-202">In der **Inspektor** erweitern **Cursor Zustandsdaten** auf die **Objekt Cursor** Skript.</span><span class="sxs-lookup"><span data-stu-id="74ec4-202">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="74ec4-203">Die **Cursor Zustandsdaten** funktioniert wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="74ec4-203">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="74ec4-204">Alle **beobachten** Status bedeutet, dass keine Hand erkannt und der Benutzer wird einfach untersucht.</span><span class="sxs-lookup"><span data-stu-id="74ec4-204">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="74ec4-205">Alle **interagieren** Status bedeutet, dass eine Seite oder ein Controller erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="74ec4-205">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="74ec4-206">Alle **zeigen** Status bedeutet, dass der Benutzer wird ggf. ein Hologramm ansehen.</span><span class="sxs-lookup"><span data-stu-id="74ec4-206">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="74ec4-207">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="74ec4-207">Build and Deploy</span></span>

* <span data-ttu-id="74ec4-208">Verwenden Sie in Unity **Datei > Buildeinstellungen** um die Anwendung neu zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="74ec4-208">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="74ec4-209">Öffnen der **App** Ordner.</span><span class="sxs-lookup"><span data-stu-id="74ec4-209">Open the **App** folder.</span></span>
* <span data-ttu-id="74ec4-210">Wenn sie nicht bereits geöffnet ist, öffnen Sie die **ModelExplorer Visual Studio-Projektmappe**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-210">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="74ec4-211">(Wenn Sie bereits erstellt bzw. dieses Projekt in Visual Studio während der Einrichtung bereitgestellt, klicken Sie dann Sie können diese Instanz von Visual Studio öffnen und klicken Sie auf "Alles neu laden" Wenn Sie aufgefordert werden).</span><span class="sxs-lookup"><span data-stu-id="74ec4-211">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="74ec4-212">Klicken Sie in Visual Studio auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-212">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="74ec4-213">Nachdem die Anwendung, die HoloLens bereitstellt, schließen Sie die Fitbox mit der tippbewegung Bewegung.</span><span class="sxs-lookup"><span data-stu-id="74ec4-213">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="74ec4-214">Verschieben Sie Ihre Hand an, und zeigen Sie Ihren Index Finger auf den Himmel Hand, die nachverfolgung zu starten.</span><span class="sxs-lookup"><span data-stu-id="74ec4-214">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="74ec4-215">Verschieben Sie Ihre Hand links, rechts, oben und nach unten.</span><span class="sxs-lookup"><span data-stu-id="74ec4-215">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="74ec4-216">Sehen Sie sich, wie sich der Cursor ändert, wenn Sie Ihre Hand erkannt wird, und klicken Sie dann aus der Ansicht verloren.</span><span class="sxs-lookup"><span data-stu-id="74ec4-216">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="74ec4-217">Wenn Sie eine immersive Kopfhörer nutzen, müssen Sie eine Verbindung herstellen und trennen Ihre Controller.</span><span class="sxs-lookup"><span data-stu-id="74ec4-217">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="74ec4-218">Dieses Feedback wird auf einem Gerät faszinierende weniger interessant, da ein verbundene Controller immer werden "verfügbar".</span><span class="sxs-lookup"><span data-stu-id="74ec4-218">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="74ec4-219">Kapitel 2 – Navigation</span><span class="sxs-lookup"><span data-stu-id="74ec4-219">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="74ec4-220">Ziele</span><span class="sxs-lookup"><span data-stu-id="74ec4-220">Objectives</span></span>

* <span data-ttu-id="74ec4-221">Verwenden Sie Gestenereignisse der Navigationsbereich, um die Astronautenausweis drehen.</span><span class="sxs-lookup"><span data-stu-id="74ec4-221">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="74ec4-222">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="74ec4-222">Instructions</span></span>

<span data-ttu-id="74ec4-223">Um die Navigation Gesten in unserer app verwenden zu können, werden wir bearbeiten **GestureAction.cs** zu Objekten zu rotieren, wenn die Navigation-Aktion tritt auf.</span><span class="sxs-lookup"><span data-stu-id="74ec4-223">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="74ec4-224">Darüber hinaus fügen wir Feedback an den Cursor angezeigt wird, wenn die Navigation verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="74ec4-224">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="74ec4-225">In der **Hierarchie** erweitern **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-225">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="74ec4-226">In der **Hologramme** Ordner finden Sie die **ScrollFeedback** Asset.</span><span class="sxs-lookup"><span data-stu-id="74ec4-226">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="74ec4-227">Drag & drop die **ScrollFeedback** prefab auf die **CursorWithFeedback** "gameobject" in der **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-227">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="74ec4-228">Klicken Sie auf **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-228">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="74ec4-229">In der **Inspektor** Bereich, klicken Sie auf die **Add Component** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="74ec4-229">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="74ec4-230">Geben Sie im Menü, in das Suchfeld **CursorFeedback**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-230">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="74ec4-231">Wählen Sie das Suchergebnis.</span><span class="sxs-lookup"><span data-stu-id="74ec4-231">Select the search result.</span></span>
7. <span data-ttu-id="74ec4-232">Drag & drop die **ScrollFeedback** -Objekt aus der **Hierarchie** auf die **Scroll-Spielobjekt erkannt** -Eigenschaft in der **Cursor Feedback**-Komponente in die **Inspektor**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-232">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="74ec4-233">In der **Hierarchie** wählen die **AstroMan** Objekt.</span><span class="sxs-lookup"><span data-stu-id="74ec4-233">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="74ec4-234">In der **Inspektor** Bereich, klicken Sie auf die **Add Component** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="74ec4-234">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="74ec4-235">Geben Sie im Menü, in das Suchfeld **Geste Aktion**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-235">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="74ec4-236">Wählen Sie das Suchergebnis.</span><span class="sxs-lookup"><span data-stu-id="74ec4-236">Select the search result.</span></span>

<span data-ttu-id="74ec4-237">Öffnen Sie als Nächstes **GestureAction.cs** in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="74ec4-237">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="74ec4-238">Codierung 2.c Übung, bearbeiten Sie das Skript aus, um die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="74ec4-238">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="74ec4-239">**Drehen Sie das AstroMan** Objekt immer eine Navigation-Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="74ec4-239">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="74ec4-240">Berechnen der **RotationFactor** steuern den Grad der Drehung, die auf das Objekt angewendet.</span><span class="sxs-lookup"><span data-stu-id="74ec4-240">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="74ec4-241">**Das Objekt drehen** um die y-Achse, wenn der Benutzer ihre Westentasche nach links oder rechts bewegt.</span><span class="sxs-lookup"><span data-stu-id="74ec4-241">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="74ec4-242">Vollständige Codierung führt 2.c in Skripts oder Ersetzen Sie den Code mit der vollständigen Lösung unten:</span><span class="sxs-lookup"><span data-stu-id="74ec4-242">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

<span data-ttu-id="74ec4-243">Sie werden feststellen, dass die anderen Navigationsereignisse bereits mit einige Informationen gefüllt sind.</span><span class="sxs-lookup"><span data-stu-id="74ec4-243">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="74ec4-244">Das "gameobject" auf des Toolkits push InputSystems modalen Stapel, sodass der Benutzer nicht den Fokus auf die Astronautenausweis beibehalten, nach der Rotation begonnen hat.</span><span class="sxs-lookup"><span data-stu-id="74ec4-244">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="74ec4-245">Dementsprechend lesen wir das "gameobject" aus dem Stapel, sobald die Aktion abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="74ec4-245">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="74ec4-246">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="74ec4-246">Build and Deploy</span></span>

1. <span data-ttu-id="74ec4-247">Erstellen Sie die Anwendung in Unity und erstellen und Bereitstellen von Visual Studio für die Ausführung in die HoloLens.</span><span class="sxs-lookup"><span data-stu-id="74ec4-247">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="74ec4-248">Bestaunen Sie an die Astronautenausweis zwei Pfeile sollte auf beiden Seiten des Cursors angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="74ec4-248">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="74ec4-249">Dieses neue visuelle Element gibt an, dass die Astronautenausweis gedreht werden kann.</span><span class="sxs-lookup"><span data-stu-id="74ec4-249">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="74ec4-250">Platzieren Sie Ihre Hand bereit Position (Index Finger vom Himmel zu holen ausgerichtet), damit die HoloLens Nachverfolgen Ihrer manuell gestartet werden kann.</span><span class="sxs-lookup"><span data-stu-id="74ec4-250">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="74ec4-251">Um die Astronautenausweis zu drehen, senken Sie Ihre Zeigefinger an eine Position verkleinern und dann verschieben Sie Ihre Hand, nach links oder rechts, um die Bewegung NavigationX auszulösen.</span><span class="sxs-lookup"><span data-stu-id="74ec4-251">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="74ec4-252">Kapitel 3 – manuell Anleitungen</span><span class="sxs-lookup"><span data-stu-id="74ec4-252">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="74ec4-253">Ziele</span><span class="sxs-lookup"><span data-stu-id="74ec4-253">Objectives</span></span>

* <span data-ttu-id="74ec4-254">Verwenden **übergeben Anleitungen Bewertung** um vorherzusagen, beim Nachverfolgen von Hand verloren.</span><span class="sxs-lookup"><span data-stu-id="74ec4-254">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="74ec4-255">Geben Sie **Feedback für den Cursor** angezeigt, wenn der Benutzer manuell der Kamera Rand der Ansicht nähert.</span><span class="sxs-lookup"><span data-stu-id="74ec4-255">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="74ec4-256">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="74ec4-256">Instructions</span></span>

1. <span data-ttu-id="74ec4-257">In der **Hierarchie** wählen die **CursorWithFeedback** Objekt.</span><span class="sxs-lookup"><span data-stu-id="74ec4-257">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="74ec4-258">In der **Inspektor** Bereich, klicken Sie auf die **Add Component** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="74ec4-258">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="74ec4-259">Geben Sie im Menü, in das Suchfeld **Hand Anleitungen**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-259">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="74ec4-260">Wählen Sie das Suchergebnis.</span><span class="sxs-lookup"><span data-stu-id="74ec4-260">Select the search result.</span></span>
4. <span data-ttu-id="74ec4-261">In der **Projekt** Bereich **Hologramme** Ordner finden Sie die **HandGuidanceFeedback** Asset.</span><span class="sxs-lookup"><span data-stu-id="74ec4-261">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="74ec4-262">Drag & drop die **HandGuidanceFeedback** Medienobjekt, auf die **Hand Anleitungen Indikator** -Eigenschaft in der **Inspektor** Bereich.</span><span class="sxs-lookup"><span data-stu-id="74ec4-262">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="74ec4-263">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="74ec4-263">Build and Deploy</span></span>

* <span data-ttu-id="74ec4-264">Erstellen Sie die Anwendung in Unity und erstellen und Bereitstellen von Visual Studio, um die app auf HoloLens auftreten.</span><span class="sxs-lookup"><span data-stu-id="74ec4-264">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="74ec4-265">Bringen Sie Ihre Hand an, und lösen Sie Ihren Finger Index, der nachverfolgt werden.</span><span class="sxs-lookup"><span data-stu-id="74ec4-265">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="74ec4-266">Starten Sie die Rotation der Astronautenausweis mit dieser Bewegung Navigation (Verkleinern der Zeigefinger und thumb-zusammen).</span><span class="sxs-lookup"><span data-stu-id="74ec4-266">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="74ec4-267">Verschieben Sie Ihre Hand, ganz links, rechts, oben und unten.</span><span class="sxs-lookup"><span data-stu-id="74ec4-267">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="74ec4-268">Wie Sie Ihre Hand den Rand des Rahmens Geste nähert ein Pfeil sollte angezeigt werden wird der Cursor, damit Sie gewarnt, dass diese manuell nachverfolgen verloren gehen.</span><span class="sxs-lookup"><span data-stu-id="74ec4-268">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="74ec4-269">Der Pfeil gibt die Richtung, damit Ihre Seite zu verschieben, um zu verhindern, dass bei der nachverfolgung, verloren gehen.</span><span class="sxs-lookup"><span data-stu-id="74ec4-269">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="74ec4-270">Kapitel 4: Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="74ec4-270">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="74ec4-271">Ziele</span><span class="sxs-lookup"><span data-stu-id="74ec4-271">Objectives</span></span>

* <span data-ttu-id="74ec4-272">Verwenden Sie Manipulation-Ereignisse, um die Astronautenausweis mit der Hand zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="74ec4-272">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="74ec4-273">Geben Sie Feedback für den Cursor, damit der Benutzer wissen, wann die Bearbeitung verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="74ec4-273">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="74ec4-274">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="74ec4-274">Instructions</span></span>

<span data-ttu-id="74ec4-275">GestureManager.cs und AstronautManager.cs können wir die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="74ec4-275">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="74ec4-276">Verwenden Sie das Schlüsselwort der Sprache "**Astronautenausweis verschieben**" So aktivieren Sie **Manipulation** Gesten und "**drehen Astronautenausweis**" um sie zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="74ec4-276">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="74ec4-277">Wechseln Sie zum Reagieren auf die **Stiftbewegungs-Erkennung von Manipulation**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-277">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="74ec4-278">Los geht's.</span><span class="sxs-lookup"><span data-stu-id="74ec4-278">Let's get started.</span></span>

1. <span data-ttu-id="74ec4-279">In der **Hierarchie** erstellen ein neues leeres "gameobject".</span><span class="sxs-lookup"><span data-stu-id="74ec4-279">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="74ec4-280">Nennen Sie es "**AstronautManager**".</span><span class="sxs-lookup"><span data-stu-id="74ec4-280">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="74ec4-281">In der **Inspektor** Bereich, klicken Sie auf die **Add Component** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="74ec4-281">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="74ec4-282">Geben Sie im Menü, in das Suchfeld **Astronautenausweis Manager**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-282">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="74ec4-283">Wählen Sie das Suchergebnis.</span><span class="sxs-lookup"><span data-stu-id="74ec4-283">Select the search result.</span></span>
4. <span data-ttu-id="74ec4-284">In der **Inspektor** Bereich, klicken Sie auf die **Add Component** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="74ec4-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="74ec4-285">Geben Sie im Menü, in das Suchfeld **Speech-Eingabequelle**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-285">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="74ec4-286">Wählen Sie das Suchergebnis.</span><span class="sxs-lookup"><span data-stu-id="74ec4-286">Select the search result.</span></span>

<span data-ttu-id="74ec4-287">Wir fügen jetzt die Spracherkennung-Befehle, die erforderlich sind, um den Interaktionszustand des der Astronautenausweis zu steuern.</span><span class="sxs-lookup"><span data-stu-id="74ec4-287">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="74ec4-288">Erweitern Sie die **Schlüsselwörter** im Abschnitt der **Inspektor**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-288">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="74ec4-289">Klicken Sie auf die **+** auf der rechten Seite ein neues Schlüsselwort hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="74ec4-289">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="74ec4-290">Geben Sie das Schlüsselwort als **verschieben Astronautenausweis**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-290">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="74ec4-291">Eine Verknüpfung für die Schlüssel bei Bedarf hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="74ec4-291">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="74ec4-292">Klicken Sie auf die **+** auf der rechten Seite ein neues Schlüsselwort hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="74ec4-292">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="74ec4-293">Geben Sie das Schlüsselwort als **drehen Astronautenausweis**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-293">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="74ec4-294">Eine Verknüpfung für die Schlüssel bei Bedarf hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="74ec4-294">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="74ec4-295">Der entsprechende Handlercode befinden sich **GestureAction.cs**in die **ISpeechHandler.OnSpeechKeywordRecognized** Handler.</span><span class="sxs-lookup"><span data-stu-id="74ec4-295">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![Wie Sie die Einrichtung der Spracherkennung Eingabequelle für Kapitel 4](images/holograms211-speech.png)

<span data-ttu-id="74ec4-297">Richten Sie als Nächstes die Manipulation Feedback für den Cursor.</span><span class="sxs-lookup"><span data-stu-id="74ec4-297">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="74ec4-298">In der **Projekt** Bereich **Hologramme** Ordner finden Sie die **PathingFeedback** Asset.</span><span class="sxs-lookup"><span data-stu-id="74ec4-298">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="74ec4-299">Drag & drop die **PathingFeedback** prefab auf die **CursorWithFeedback** -Objekt in der **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-299">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="74ec4-300">In der **Hierarchie** Bereich, klicken Sie auf **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-300">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="74ec4-301">Drag & drop die **PathingFeedback** -Objekt aus der **Hierarchie** auf die **Pfade erkannt Spielobjekt** -Eigenschaft in der **Cursor Feedback**-Komponente in die **Inspektor**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-301">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="74ec4-302">Nun wir zum Hinzufügen von Code müssen **GestureAction.cs** um Folgendes zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="74ec4-302">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="74ec4-303">Fügen Sie Code in die **IManipulationHandler.OnManipulationUpdated** -Funktion, die die Astronautenausweis verschoben wird bei einer **Manipulation** Geste erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="74ec4-303">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="74ec4-304">Berechnen der **Bewegung Vektor** um zu bestimmen, in denen die Astronautenausweis zu verschoben werden soll basierend auf Seite Position.</span><span class="sxs-lookup"><span data-stu-id="74ec4-304">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="74ec4-305">**Verschieben Sie** der Astronautenausweis an die neue Position.</span><span class="sxs-lookup"><span data-stu-id="74ec4-305">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="74ec4-306">Vollständige Codierung 4.a in Übung **GestureAction.cs**, oder verwenden Sie unsere abgeschlossenen Lösung unten:</span><span class="sxs-lookup"><span data-stu-id="74ec4-306">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="74ec4-307">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="74ec4-307">Build and Deploy</span></span>

* <span data-ttu-id="74ec4-308">In Unity neu erstellen, und klicken Sie dann erstellen und Bereitstellen von Visual Studio zum Ausführen der app in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="74ec4-308">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="74ec4-309">Verschieben Sie Ihre Hand vor die HoloLens, und erhöhen Sie Ihre Zeigefinger, sodass sie nachverfolgt werden kann.</span><span class="sxs-lookup"><span data-stu-id="74ec4-309">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="74ec4-310">Konzentrieren Sie sich des Cursors über der Astronautenausweis.</span><span class="sxs-lookup"><span data-stu-id="74ec4-310">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="74ec4-311">Sagen Sie 'Astronautenausweis verschieben", um die Astronautenausweis mit einer Bewegung der Manipulation zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="74ec4-311">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="74ec4-312">Vier Pfeile sollte angezeigt werden, cursorbesitzer im Cursor, um anzugeben, dass die Anwendung nun auf Manipulation-Ereignisse reagieren.</span><span class="sxs-lookup"><span data-stu-id="74ec4-312">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="74ec4-313">Senken Sie Ihre Zeigefinger auf Ihre Thumb-Steuerelement, und bleiben Sie gequetscht zusammen.</span><span class="sxs-lookup"><span data-stu-id="74ec4-313">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="74ec4-314">Wenn Sie Ihre Hand zu bewegen, wird zu den Astronautenausweis verschoben (Dies ist ein Manipulation).</span><span class="sxs-lookup"><span data-stu-id="74ec4-314">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="74ec4-315">Lösen Sie Ihren Finger Index, um die Astronautenausweis Bearbeitung zu beenden.</span><span class="sxs-lookup"><span data-stu-id="74ec4-315">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="74ec4-316">Hinweis: Wenn Sie "Astronautenausweis verschieben" vor dem Verschieben Ihre Hand nicht sagen, wird stattdessen die Aktion für die Navigation verwendet.</span><span class="sxs-lookup"><span data-stu-id="74ec4-316">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="74ec4-317">Sagen Sie "Rotieren Astronautenausweis", um die rotatable Zustand wiederherzustellen.</span><span class="sxs-lookup"><span data-stu-id="74ec4-317">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="74ec4-318">Kapitel 5 – Model-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="74ec4-318">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="74ec4-319">Ziele</span><span class="sxs-lookup"><span data-stu-id="74ec4-319">Objectives</span></span>

* <span data-ttu-id="74ec4-320">Erweitern Sie das Modell Astronautenausweis in mehrere, kleinere Teile, dass der Benutzer interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="74ec4-320">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="74ec4-321">Verschieben Sie jedes Datenelement, die einzeln über die Datennavigation und-Bearbeitung Gesten.</span><span class="sxs-lookup"><span data-stu-id="74ec4-321">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="74ec4-322">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="74ec4-322">Instructions</span></span>

<span data-ttu-id="74ec4-323">In diesem Abschnitt werden wir die folgenden Aufgaben auszuführen:</span><span class="sxs-lookup"><span data-stu-id="74ec4-323">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="74ec4-324">Fügen Sie ein neues Schlüsselwort "**Modell erweitern**" um das Modell Astronautenausweis zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="74ec4-324">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="74ec4-325">Fügen Sie ein neues Schlüsselwort "**Modell zurücksetzen**" auf das Modell in seiner ursprünglichen Form zurück.</span><span class="sxs-lookup"><span data-stu-id="74ec4-325">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="74ec4-326">Dazu müssen wir die Eingabequelle Sprache aus dem vorhergehenden Kapitel zwei weitere Schlüsselwörter hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="74ec4-326">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="74ec4-327">Außerdem zeigen wir Ihnen eine weitere Möglichkeit zum Behandeln von Ereignissen der Erkennung.</span><span class="sxs-lookup"><span data-stu-id="74ec4-327">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="74ec4-328">Klicken Sie wieder auf **AstronautManager** in die **Inspektor** und erweitern Sie die **Schlüsselwörter** im Abschnitt der **Inspektor**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-328">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="74ec4-329">Klicken Sie auf die **+** auf der rechten Seite ein neues Schlüsselwort hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="74ec4-329">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="74ec4-330">Geben Sie das Schlüsselwort als **Modell erweitern**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-330">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="74ec4-331">Eine Verknüpfung für die Schlüssel bei Bedarf hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="74ec4-331">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="74ec4-332">Klicken Sie auf die **+** auf der rechten Seite ein neues Schlüsselwort hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="74ec4-332">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="74ec4-333">Geben Sie das Schlüsselwort als **Modell zurücksetzen**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-333">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="74ec4-334">Eine Verknüpfung für die Schlüssel bei Bedarf hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="74ec4-334">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="74ec4-335">In der **Inspektor** Bereich, klicken Sie auf die **Add Component** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="74ec4-335">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="74ec4-336">Geben Sie im Menü, in das Suchfeld **Spracherkennung Eingabe Handler**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-336">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="74ec4-337">Wählen Sie das Suchergebnis.</span><span class="sxs-lookup"><span data-stu-id="74ec4-337">Select the search result.</span></span>
8. <span data-ttu-id="74ec4-338">Überprüfen Sie **globale Listener ist**, da diese Befehle funktionieren Sie unabhängig von der "gameobject" konzentrieren wir sollten.</span><span class="sxs-lookup"><span data-stu-id="74ec4-338">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="74ec4-339">Klicken Sie auf die **+** Schaltfläche, und wählen **Modell erweitern** aus der Dropdownliste "Schlüsselwort".</span><span class="sxs-lookup"><span data-stu-id="74ec4-339">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="74ec4-340">Klicken Sie auf die **+** unter Antwort, und ziehen Sie die **AstronautManager** aus der **Hierarchie** in die **None (Objekt)** Feld.</span><span class="sxs-lookup"><span data-stu-id="74ec4-340">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="74ec4-341">Klicken Sie nun die **keine Funktion** Dropdownliste wählen **AstronautManager**, klicken Sie dann **ExpandModelCommand**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-341">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="74ec4-342">Klicken Sie auf die Spracherkennung Eingabe des Handlers **+** Schaltfläche, und wählen **Modell zurücksetzen** aus der Dropdownliste "Schlüsselwort".</span><span class="sxs-lookup"><span data-stu-id="74ec4-342">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="74ec4-343">Klicken Sie auf die **+** unter Antwort, und ziehen Sie die **AstronautManager** aus der **Hierarchie** in die **None (Objekt)** Feld.</span><span class="sxs-lookup"><span data-stu-id="74ec4-343">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="74ec4-344">Klicken Sie nun die **keine Funktion** Dropdownliste wählen **AstronautManager**, klicken Sie dann **ResetModelCommand**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-344">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![Wie Sie die Einrichtung der Eingabequelle Spracherkennung und -Handler für Kapitel 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="74ec4-346">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="74ec4-346">Build and Deploy</span></span>

* <span data-ttu-id="74ec4-347">Probieren Sie es aus!</span><span class="sxs-lookup"><span data-stu-id="74ec4-347">Try it!</span></span> <span data-ttu-id="74ec4-348">Erstellen und Bereitstellen der app, die HoloLens.</span><span class="sxs-lookup"><span data-stu-id="74ec4-348">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="74ec4-349">Sagen Sie **Modell erweitern** auf dem erweiterten Astronautenausweis-Modell finden Sie unter.</span><span class="sxs-lookup"><span data-stu-id="74ec4-349">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="74ec4-350">Verwendung **Navigation** einzelne Teile die Farbe Astronautenausweis gedreht.</span><span class="sxs-lookup"><span data-stu-id="74ec4-350">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="74ec4-351">Angenommen, **verschieben Astronautenausweis** und verwenden Sie dann **Manipulation** einzelne Teile die Farbe Astronautenausweis zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="74ec4-351">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="74ec4-352">Sagen Sie **drehen Astronautenausweis** auf die einzelnen Teile erneut drehen.</span><span class="sxs-lookup"><span data-stu-id="74ec4-352">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="74ec4-353">Sagen Sie **Modell zurücksetzen** der Astronautenausweis in seiner ursprünglichen Form zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="74ec4-353">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="74ec4-354">Das Ende</span><span class="sxs-lookup"><span data-stu-id="74ec4-354">The End</span></span>

<span data-ttu-id="74ec4-355">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="74ec4-355">Congratulations!</span></span> <span data-ttu-id="74ec4-356">Sie haben jetzt **MR Eingabe 211: Geste**.</span><span class="sxs-lookup"><span data-stu-id="74ec4-356">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="74ec4-357">Sie wissen, wie Sie erkennen und darauf reagieren zu manuell nachverfolgen, Navigation und Bearbeitungsereignisse.</span><span class="sxs-lookup"><span data-stu-id="74ec4-357">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="74ec4-358">Sie kennen den Unterschied zwischen Datennavigation und-Bearbeitung Gesten.</span><span class="sxs-lookup"><span data-stu-id="74ec4-358">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="74ec4-359">Sie wissen, wie so ändern Sie den Cursor zum Bereitstellen von visuellem Feedback, wenn eine Hand erkannt wird, wenn gerade eine Hand gehen verloren, und wenn ein Objekt mit verschiedene Aktivitäten, die (Navigation Vs Manipulation) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="74ec4-359">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>
