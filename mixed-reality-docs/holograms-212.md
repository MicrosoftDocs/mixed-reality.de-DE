---
title: MR Eingabe 212 - Sprache
description: Führen Sie diese Codierung Exemplarische Vorgehensweise mit Unity, Visual Studio und HoloLens um die Details der Voice-Konzepte zu erfahren.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academy, tutorial, voice
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593796"
---
>[!NOTE]
><span data-ttu-id="86608-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="86608-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="86608-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="86608-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="86608-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="86608-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="86608-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="86608-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="86608-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="86608-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="86608-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="86608-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-212-voice"></a><span data-ttu-id="86608-110">MR Eingabe 212: Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="86608-110">MR Input 212: Voice</span></span>

<span data-ttu-id="86608-111">[Voice-Eingabe](voice-input.md) bietet uns eine andere Möglichkeit zur Interaktion mit unserem Hologramme.</span><span class="sxs-lookup"><span data-stu-id="86608-111">[Voice input](voice-input.md) gives us another way to interact with our holograms.</span></span> <span data-ttu-id="86608-112">Sprachbefehle funktionieren in einer sehr natürlichen und einfache Möglichkeit.</span><span class="sxs-lookup"><span data-stu-id="86608-112">Voice commands work in a very natural and easy way.</span></span> <span data-ttu-id="86608-113">Entwerfen Sie Ihre Sprachbefehle, damit sie sind:</span><span class="sxs-lookup"><span data-stu-id="86608-113">Design your voice commands so that they are:</span></span>

* <span data-ttu-id="86608-114">Natürliche</span><span class="sxs-lookup"><span data-stu-id="86608-114">Natural</span></span>
* <span data-ttu-id="86608-115">Leicht zu merken</span><span class="sxs-lookup"><span data-stu-id="86608-115">Easy to remember</span></span>
* <span data-ttu-id="86608-116">Kontext entsprechenden</span><span class="sxs-lookup"><span data-stu-id="86608-116">Context appropriate</span></span>
* <span data-ttu-id="86608-117">Ausreichend Weitere Optionen im gleichen Kontext unterscheidet</span><span class="sxs-lookup"><span data-stu-id="86608-117">Sufficiently distinct from other options within the same context</span></span>

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

<span data-ttu-id="86608-118">In [MR Grundlagen 101](holograms-101.md), wir die KeywordRecognizer verwendet, um zwei einfache Sprachbefehle zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="86608-118">In [MR Basics 101](holograms-101.md), we used the KeywordRecognizer to build two simple voice commands.</span></span> <span data-ttu-id="86608-119">In der Eingabe 212 MR, wir tiefer einsteigen und erfahren Sie, wie Sie:</span><span class="sxs-lookup"><span data-stu-id="86608-119">In MR Input 212, we'll dive deeper and learn how to:</span></span>

* <span data-ttu-id="86608-120">Entwerfen Sie Sprachbefehle, die für die HoloLens spracherkennungs-Engine optimiert sind.</span><span class="sxs-lookup"><span data-stu-id="86608-120">Design voice commands that are optimized for the HoloLens speech engine.</span></span>
* <span data-ttu-id="86608-121">Stellen Sie dem Benutzer bewusst welche Stimme Befehle verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="86608-121">Make the user aware of what voice commands are available.</span></span>
* <span data-ttu-id="86608-122">Bestätigen Sie, dass schon Sprachbefehl des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="86608-122">Acknowledge that we've heard the user's voice command.</span></span>
* <span data-ttu-id="86608-123">Überblick über die der Benutzer sagen, verwenden eine Erkennung Diktat.</span><span class="sxs-lookup"><span data-stu-id="86608-123">Understand what the user is saying, using a Dictation Recognizer.</span></span>
* <span data-ttu-id="86608-124">Verwenden Sie eine Erkennung Grammatik zum Lauschen auf Befehle, die basierend auf einer SRGS oder Speech Recognition-Grammatik-Spezifikation.</span><span class="sxs-lookup"><span data-stu-id="86608-124">Use a Grammar Recognizer to listen for commands based on an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

<span data-ttu-id="86608-125">In diesem Kurs wir erneut die es im erstellt Modell-Explorer behandelt [MR Eingabe 210](holograms-210.md) und [MR Eingabe 211](holograms-211.md).</span><span class="sxs-lookup"><span data-stu-id="86608-125">In this course, we'll revisit Model Explorer, which we built in [MR Input 210](holograms-210.md) and [MR Input 211](holograms-211.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="86608-126">Die Videos in jeder der folgenden Kapitel eingebettet wurden mit einer älteren Version von Unity und dem Mixed Reality-Toolkit aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="86608-126">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="86608-127">Während die schrittweisen Anweisungen korrekt und aktuell sind, Sie möglicherweise Skripts und Visualisierungen in die entsprechenden Videos, die veraltet sind.</span><span class="sxs-lookup"><span data-stu-id="86608-127">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="86608-128">Die Videos aus Gründen der Posterity bleiben, und es aber trotzdem anwenden, da die Konzepte behandelt.</span><span class="sxs-lookup"><span data-stu-id="86608-128">The videos remain included for posterity and because the concepts covered still apply.</span></span>


## <a name="device-support"></a><span data-ttu-id="86608-129">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="86608-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="86608-130">Kurs</span><span class="sxs-lookup"><span data-stu-id="86608-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="86608-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="86608-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="86608-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="86608-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="86608-133">MR Eingabe 212: Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="86608-133">MR Input 212: Voice</span></span></td><td style="text-align: center;"> <span data-ttu-id="86608-134">✔️</span><span class="sxs-lookup"><span data-stu-id="86608-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="86608-135">✔️</span><span class="sxs-lookup"><span data-stu-id="86608-135">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="86608-136">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="86608-136">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="86608-137">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="86608-137">Prerequisites</span></span>

* <span data-ttu-id="86608-138">Ein Windows 10-PCs mit dem richtigen konfiguriert [-Tools installiert](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="86608-138">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="86608-139">Einige grundlegende C# Programmierkenntnisse.</span><span class="sxs-lookup"><span data-stu-id="86608-139">Some basic C# programming ability.</span></span>
* <span data-ttu-id="86608-140">Sie sollten abgeschlossen haben [MR Grundlagen 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="86608-140">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="86608-141">Sie sollten abgeschlossen haben [MR Eingabe 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="86608-141">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="86608-142">Sie sollten abgeschlossen haben [MR Eingabe 211](holograms-211.md).</span><span class="sxs-lookup"><span data-stu-id="86608-142">You should have completed [MR Input 211](holograms-211.md).</span></span>
* <span data-ttu-id="86608-143">Ein Gerät HoloLens [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="86608-143">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="86608-144">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="86608-144">Project files</span></span>

* <span data-ttu-id="86608-145">Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) vom Projekt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="86608-145">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) required by the project.</span></span> <span data-ttu-id="86608-146">Ist Unity 2017.2 oder höher erforderlich.</span><span class="sxs-lookup"><span data-stu-id="86608-146">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="86608-147">Un-Archive die Dateien auf dem Desktop oder andere einfach auf den Speicherort zugreifen.</span><span class="sxs-lookup"><span data-stu-id="86608-147">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="86608-148">Wenn Sie vor dem Herunterladen, den Quellcode ansehen möchten es [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span><span class="sxs-lookup"><span data-stu-id="86608-148">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="86608-149">Fehler und Anmerkungen zu dieser Version</span><span class="sxs-lookup"><span data-stu-id="86608-149">Errata and Notes</span></span>

* <span data-ttu-id="86608-150">"Nur eigenen Code aktivieren" muss deaktiviert sein (*deaktiviert*) in Visual Studio unter Extras -> Optionen-Debuggen >, um die Haltepunkte in Ihrem Code.</span><span class="sxs-lookup"><span data-stu-id="86608-150">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="86608-151">Unity-Setup</span><span class="sxs-lookup"><span data-stu-id="86608-151">Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="86608-152">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="86608-152">Instructions</span></span>

1. <span data-ttu-id="86608-153">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="86608-153">Start Unity.</span></span>
2. <span data-ttu-id="86608-154">Wählen Sie **öffnen**.</span><span class="sxs-lookup"><span data-stu-id="86608-154">Select **Open**.</span></span>
3. <span data-ttu-id="86608-155">Navigieren Sie zu der **HolographicAcademy-Hologramme-212-Voice** Ordner Sie zuvor nicht archiviert.</span><span class="sxs-lookup"><span data-stu-id="86608-155">Navigate to the **HolographicAcademy-Holograms-212-Voice** folder you previously un-archived.</span></span>
4. <span data-ttu-id="86608-156">Suchen und Auswählen der **ab**/**Modell-Explorer** Ordner.</span><span class="sxs-lookup"><span data-stu-id="86608-156">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="86608-157">Klicken Sie auf die **Ordner auswählen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="86608-157">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="86608-158">In der **Projekt** erweitern Sie die **Szenen** Ordner.</span><span class="sxs-lookup"><span data-stu-id="86608-158">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="86608-159">Doppelklicken Sie auf **ModelExplorer** Szene, um es in Unity zu laden.</span><span class="sxs-lookup"><span data-stu-id="86608-159">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="86608-160">Erstellung</span><span class="sxs-lookup"><span data-stu-id="86608-160">Building</span></span>

1. <span data-ttu-id="86608-161">Wählen Sie in Unity **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="86608-161">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="86608-162">Wenn **Szenen/ModelExplorer** in nicht aufgeführt ist **Szenen In Build**, klicken Sie auf **öffnen Szenen hinzufügen** die Szene hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="86608-162">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="86608-163">Wenn Sie speziell für HoloLens entwickeln, legen Sie **Zielgerät** zu **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="86608-163">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="86608-164">Andernfalls lassen Sie es auf **jedes Gerät**.</span><span class="sxs-lookup"><span data-stu-id="86608-164">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="86608-165">Stellen Sie sicher **Build Type** nastaven NA hodnotu **D3D** und **SDK** nastaven NA hodnotu **zuletzt installierte** (die sollte SDK 16299 oder höher sein).</span><span class="sxs-lookup"><span data-stu-id="86608-165">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="86608-166">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="86608-166">Click **Build**.</span></span>
6. <span data-ttu-id="86608-167">Erstellen Sie eine **neuer Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="86608-167">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="86608-168">Mausklick die **App** Ordner.</span><span class="sxs-lookup"><span data-stu-id="86608-168">Single click the **App** folder.</span></span>
8. <span data-ttu-id="86608-169">Drücken Sie **Ordner auswählen** und Unity wird beim Erstellen des Projekts für Visual Studio gestartet.</span><span class="sxs-lookup"><span data-stu-id="86608-169">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="86608-170">Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="86608-170">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="86608-171">Öffnen der **App** Ordner.</span><span class="sxs-lookup"><span data-stu-id="86608-171">Open the **App** folder.</span></span>
2. <span data-ttu-id="86608-172">Öffnen der **ModelExplorer Visual Studio-Projektmappe**.</span><span class="sxs-lookup"><span data-stu-id="86608-172">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="86608-173">Wenn für HoloLens bereitstellen zu können:</span><span class="sxs-lookup"><span data-stu-id="86608-173">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="86608-174">Verwenden obere auf der Symbolleiste in Visual Studio, ändern Sie das Ziel vom Debugmodus in den **Version** und ARM, **X86**.</span><span class="sxs-lookup"><span data-stu-id="86608-174">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="86608-175">Klicken Sie auf den Dropdownpfeil neben der Schaltfläche mit den lokalen Computer, und wählen **Remotecomputer**.</span><span class="sxs-lookup"><span data-stu-id="86608-175">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="86608-176">Geben Sie **die HoloLens-Geräte-IP-Adresse** und legen Sie den Authentifizierungsmodus auf **universell (unverschlüsseltes Protokoll)**.</span><span class="sxs-lookup"><span data-stu-id="86608-176">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="86608-177">Klicken Sie auf **Auswählen**.</span><span class="sxs-lookup"><span data-stu-id="86608-177">Click **Select**.</span></span> <span data-ttu-id="86608-178">Wenn Sie Ihre IP-Adresse des Geräts nicht kennen, suchen Sie im **Einstellungen > Netzwerk und Internet > Erweiterte Optionen**.</span><span class="sxs-lookup"><span data-stu-id="86608-178">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="86608-179">Klicken Sie in der Menüleiste im oberen Bereich auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="86608-179">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="86608-180">Ist dies beim ersten auf Ihrem Gerät bereitstellen, Sie müssen [verbinden Sie es mit Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="86608-180">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="86608-181">Wenn die app bereitgestellt wurde, schließen die **Fitbox** mit eine **wählen Sie die Bewegung**.</span><span class="sxs-lookup"><span data-stu-id="86608-181">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="86608-182">Wenn eine immersive Kopfhörer bereitstellen:</span><span class="sxs-lookup"><span data-stu-id="86608-182">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="86608-183">Verwenden obere auf der Symbolleiste in Visual Studio, ändern Sie das Ziel vom Debugmodus in den **Version** und ARM, **X64**.</span><span class="sxs-lookup"><span data-stu-id="86608-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="86608-184">Stellen Sie sicher, dass das Bereitstellungsziel nastaven NA hodnotu **lokalen Computer**.</span><span class="sxs-lookup"><span data-stu-id="86608-184">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="86608-185">Klicken Sie in der Menüleiste im oberen Bereich auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="86608-185">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="86608-186">Wenn die app bereitgestellt wurde, schließen die **Fitbox** den Trigger ein Controller während der Übertragung zu ziehen.</span><span class="sxs-lookup"><span data-stu-id="86608-186">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="86608-187">Sie können einige rote Fehler im Bereich von Visual Studio-Fehler feststellen.</span><span class="sxs-lookup"><span data-stu-id="86608-187">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="86608-188">Es kann gefahrlos ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="86608-188">It is safe to ignore them.</span></span> <span data-ttu-id="86608-189">Wechseln Sie zur Ausgabebereich tatsächliche anzeigen Fortschritt des Builds.</span><span class="sxs-lookup"><span data-stu-id="86608-189">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="86608-190">Fehler im Ausgabebereich ist erforderlich, Sie stellen eine Lösung (die meisten häufig durch einen Fehler in einem Skript, sie entstehen).</span><span class="sxs-lookup"><span data-stu-id="86608-190">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---awareness"></a><span data-ttu-id="86608-191">Kapitel 1 - Awareness</span><span class="sxs-lookup"><span data-stu-id="86608-191">Chapter 1 - Awareness</span></span>

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a><span data-ttu-id="86608-192">Ziele</span><span class="sxs-lookup"><span data-stu-id="86608-192">Objectives</span></span>

* <span data-ttu-id="86608-193">Erfahren Sie, den **Empfehlungen und** Voice-Befehl Entwurf.</span><span class="sxs-lookup"><span data-stu-id="86608-193">Learn the **Dos and Don'ts** of voice command design.</span></span>
* <span data-ttu-id="86608-194">Verwendung **KeywordRecognizer** Blicke basierend Sprachbefehle hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="86608-194">Use **KeywordRecognizer** to add gaze based voice commands.</span></span>
* <span data-ttu-id="86608-195">Einrichten von Benutzern für Sprachbefehle, die bei der Cursor **Feedback**.</span><span class="sxs-lookup"><span data-stu-id="86608-195">Make users aware of voice commands using cursor **feedback**.</span></span>

### <a name="voice-command-design"></a><span data-ttu-id="86608-196">Voice-Befehlsentwurf</span><span class="sxs-lookup"><span data-stu-id="86608-196">Voice Command Design</span></span>

<span data-ttu-id="86608-197">In diesem Kapitel erfahren Sie, wie Sie Sprachbefehle zu entwerfen.</span><span class="sxs-lookup"><span data-stu-id="86608-197">In this chapter, you'll learn about designing voice commands.</span></span> <span data-ttu-id="86608-198">Wenn Sie Sprachbefehle zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="86608-198">When creating voice commands:</span></span>

#### <a name="do"></a><span data-ttu-id="86608-199">DO</span><span class="sxs-lookup"><span data-stu-id="86608-199">DO</span></span>

* <span data-ttu-id="86608-200">Erstellen Sie präzise Befehle.</span><span class="sxs-lookup"><span data-stu-id="86608-200">Create concise commands.</span></span> <span data-ttu-id="86608-201">Nicht verwenden möchten *"Video abspielen, um ausgewählte"*, da dieser Befehl nicht präzise ist und diese vom Benutzer leicht vergessen werden würden.</span><span class="sxs-lookup"><span data-stu-id="86608-201">You don't want to use *"Play the currently selected video"*, because that command is not concise and would easily be forgotten by the user.</span></span> <span data-ttu-id="86608-202">Stattdessen sollten Sie Folgendes verwenden: *"Video abspielen"*, da sie präzise und verfügt über mehrere Unterschiede zwischen.</span><span class="sxs-lookup"><span data-stu-id="86608-202">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="86608-203">Verwenden Sie ein einfaches Vokabular ein.</span><span class="sxs-lookup"><span data-stu-id="86608-203">Use a simple vocabulary.</span></span> <span data-ttu-id="86608-204">Versuchen Sie immer mit häufige Wörter und Begriffe, die einfach für den Benutzer aus, um zu ermitteln, und denken Sie daran.</span><span class="sxs-lookup"><span data-stu-id="86608-204">Always try to use common words and phrases that are easy for the user to discover and remember.</span></span> <span data-ttu-id="86608-205">Beispielsweise wenn Ihre Anwendung einen Hinweis-Objekt, die angezeigt oder ausgeblendet werden kann besitzt, würden Sie nicht den Befehl verwenden *"Placard anzeigen"*, da "Placard" ein selten verwendeter Begriff ist.</span><span class="sxs-lookup"><span data-stu-id="86608-205">For example, if your application had a note object that could be displayed or hidden from view, you would not use the command *"Show Placard"*, because "placard" is a rarely used term.</span></span> <span data-ttu-id="86608-206">Stattdessen würden Sie den Befehl verwenden: *"Hinweis anzeigen"*, um den Hinweis in Ihrer Anwendung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="86608-206">Instead, you would use the command: *"Show Note"*, to reveal the note in your application.</span></span>
* <span data-ttu-id="86608-207">Achten Sie auf Einheitlichkeit.</span><span class="sxs-lookup"><span data-stu-id="86608-207">Be consistent.</span></span> <span data-ttu-id="86608-208">Sprachbefehle sollten in Ihrer Anwendung konsistent gehalten werden.</span><span class="sxs-lookup"><span data-stu-id="86608-208">Voice commands should be kept consistent across your application.</span></span> <span data-ttu-id="86608-209">Angenommen Sie, Sie zwei Szenen in Ihrer Anwendung haben, und sowohl im Hintergrund eine Schaltfläche zum Schließen der Anwendungs enthalten.</span><span class="sxs-lookup"><span data-stu-id="86608-209">Imagine that you have two scenes in your application and both scenes contain a button for closing the application.</span></span> <span data-ttu-id="86608-210">Wenn die erste Szene der Befehl verwendet *"Exit"* verwendet, um die Schaltfläche ", aber der zweite trigger Szene Befehls *"App Schließen"*, und klicken Sie dann der Benutzer wird allerdings sehr verwirrte.</span><span class="sxs-lookup"><span data-stu-id="86608-210">If the first scene used the command *"Exit"* to trigger the button, but the second scene used the command *"Close App"*, then the user is going to get very confused.</span></span> <span data-ttu-id="86608-211">Wenn die gleiche Funktionalität auf mehrere Szenen weiterhin besteht, sollten der gleichen Voice-Befehl verwendet werden, sie auslösen.</span><span class="sxs-lookup"><span data-stu-id="86608-211">If the same functionality persists across multiple scenes, then the same voice command should be used to trigger it.</span></span>

#### <a name="dont"></a><span data-ttu-id="86608-212">DON'T</span><span class="sxs-lookup"><span data-stu-id="86608-212">DON'T</span></span>

* <span data-ttu-id="86608-213">Verwenden Sie die einzelnen Silbe-Befehle.</span><span class="sxs-lookup"><span data-stu-id="86608-213">Use single syllable commands.</span></span> <span data-ttu-id="86608-214">Beispielsweise wenn Sie einen Sprachbefehl zur Wiedergabe eines Videos erstellen, vermeiden Sie die Verwendung der einfachen Befehls *"Wiedergeben"*, wie dabei handelt es sich nur eine einzelne Silbe konnte vom System leicht übersehen werden.</span><span class="sxs-lookup"><span data-stu-id="86608-214">As an example, if you were creating a voice command to play a video, you should avoid using the simple command *"Play"*, as it is only a single syllable and could easily be missed by the system.</span></span> <span data-ttu-id="86608-215">Stattdessen sollten Sie Folgendes verwenden: *"Video abspielen"*, da sie präzise und verfügt über mehrere Unterschiede zwischen.</span><span class="sxs-lookup"><span data-stu-id="86608-215">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="86608-216">Verwenden Sie Systembefehle.</span><span class="sxs-lookup"><span data-stu-id="86608-216">Use system commands.</span></span> <span data-ttu-id="86608-217">Die *"Select"* Befehl ist reserviert, die vom System eine Tap-Ereignis für das Objekt derzeit fokussierten auslösen.</span><span class="sxs-lookup"><span data-stu-id="86608-217">The *"Select"* command is reserved by the system to trigger a Tap event for the currently focused object.</span></span> <span data-ttu-id="86608-218">Verwenden Sie nicht mehrfach die *"Select"* -Befehl in einem Schlüsselwort oder einen Ausdruck, da es möglicherweise nicht funktioniert wie erwartet.</span><span class="sxs-lookup"><span data-stu-id="86608-218">Do not re-use the *"Select"* command in a keyword or phrase, as it might not work as you expect.</span></span> <span data-ttu-id="86608-219">Zum Beispiel wenn die Stimme-zum Auswählen eines Cubes in der Anwendung Befehl wurde *"Select Cube"*, aber der Benutzer suchte auf einer Kugel, wenn sie den Befehl uttered die Kugel stattdessen ausgewählt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="86608-219">For example, if the voice command for selecting a cube in your application was *"Select cube"*, but the user was looking at a sphere when they uttered the command, then the sphere would be selected instead.</span></span> <span data-ttu-id="86608-220">Auf ähnliche Weise werden die Befehle für app-Leiste Sprache aktiviert.</span><span class="sxs-lookup"><span data-stu-id="86608-220">Similarly app bar commands are voice enabled.</span></span> <span data-ttu-id="86608-221">Verwenden Sie die folgenden Sprachbefehle nicht in der Ansicht "corewindow" aus:</span><span class="sxs-lookup"><span data-stu-id="86608-221">Don't use the following speech commands in your CoreWindow View:</span></span>
    1. <span data-ttu-id="86608-222">Zurück</span><span class="sxs-lookup"><span data-stu-id="86608-222">Go Back</span></span>
    2. <span data-ttu-id="86608-223">Bildlauftool</span><span class="sxs-lookup"><span data-stu-id="86608-223">Scroll Tool</span></span>
    3. <span data-ttu-id="86608-224">Zoomtool in der</span><span class="sxs-lookup"><span data-stu-id="86608-224">Zoom Tool</span></span>
    4. <span data-ttu-id="86608-225">Ziehen Sie-Tool</span><span class="sxs-lookup"><span data-stu-id="86608-225">Drag Tool</span></span>
    5. <span data-ttu-id="86608-226">Anpassen</span><span class="sxs-lookup"><span data-stu-id="86608-226">Adjust</span></span>
    6. <span data-ttu-id="86608-227">Entfernen</span><span class="sxs-lookup"><span data-stu-id="86608-227">Remove</span></span>
* <span data-ttu-id="86608-228">Verwenden Sie ähnliche Sounds.</span><span class="sxs-lookup"><span data-stu-id="86608-228">Use similar sounds.</span></span> <span data-ttu-id="86608-229">Versuchen Sie es, um zu vermeiden, verwenden Sprachbefehle, die schönen.</span><span class="sxs-lookup"><span data-stu-id="86608-229">Try to avoid using voice commands that rhyme.</span></span> <span data-ttu-id="86608-230">Wenn Sie eine einkaufsanwendung haben dies unterstützt *"Anzeigen Store"* und *"Mehr anzeigen"* als Sprachbefehle, Sie sollten einen der Befehle deaktivieren, während die andere verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="86608-230">If you had a shopping application which supported *"Show Store"* and *"Show More"* as voice commands, then you would want to disable one of the commands while the other was in use.</span></span> <span data-ttu-id="86608-231">Beispielsweise können Sie die *"Anzeigen Store"* Schaltfläche, um den Store zu öffnen, und deaktivieren Sie dann diesen Befehl aus, wenn im Store angezeigt wurde, damit die *"Mehr anzeigen"* Befehl kann verwendet werden, für das Durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="86608-231">For example, you could use the *"Show Store"* button to open the store, and then disable that command when the store was displayed so that the *"Show More"* command could be used for browsing.</span></span>

### <a name="instructions"></a><span data-ttu-id="86608-232">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="86608-232">Instructions</span></span>

* <span data-ttu-id="86608-233">In Unity **Hierarchie** verwenden das Such-Tool zum Suchen der **HoloComm_screen_mesh** Objekt.</span><span class="sxs-lookup"><span data-stu-id="86608-233">In Unity's **Hierarchy** panel, use the search tool to find the **holoComm_screen_mesh** object.</span></span>
* <span data-ttu-id="86608-234">Doppelklicken Sie auf die **HoloComm_screen_mesh** Objekt in der **Szene**.</span><span class="sxs-lookup"><span data-stu-id="86608-234">Double-click on the **holoComm_screen_mesh** object to view it in the **Scene**.</span></span> <span data-ttu-id="86608-235">Dies ist die Astronautenausweis des sehen Sie sich, die unsere Sprachbefehle reagiert.</span><span class="sxs-lookup"><span data-stu-id="86608-235">This is the astronaut's watch, which will respond to our voice commands.</span></span>
* <span data-ttu-id="86608-236">In der **Inspektor** Suchen der **Speech-Eingabequelle (Skript)** Komponente.</span><span class="sxs-lookup"><span data-stu-id="86608-236">In the **Inspector** panel, locate the **Speech Input Source (Script)** component.</span></span>
* <span data-ttu-id="86608-237">Erweitern Sie die **Schlüsselwörter** Abschnitt aus, um die Sprachnachrichten unterstützten Befehl finden Sie unter: **Öffnen Sie Communicator**.</span><span class="sxs-lookup"><span data-stu-id="86608-237">Expand the **Keywords** section to see the supported voice command: **Open Communicator**.</span></span>
* <span data-ttu-id="86608-238">Klicken Sie auf das Zahnrad rechts, und wählen Sie dann **Bearbeitungsskript**.</span><span class="sxs-lookup"><span data-stu-id="86608-238">Click the cog to the right side, then select **Edit Script**.</span></span>
* <span data-ttu-id="86608-239">Untersuchen **SpeechInputSource.cs** zu verstehen, wie es verwendet die **KeywordRecognizer** Sprachbefehle hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="86608-239">Explore **SpeechInputSource.cs** to understand how it uses the **KeywordRecognizer** to add voice commands.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="86608-240">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="86608-240">Build and Deploy</span></span>

* <span data-ttu-id="86608-241">Verwenden Sie in Unity **Datei > Buildeinstellungen** um die Anwendung neu zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="86608-241">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="86608-242">Öffnen der **App** Ordner.</span><span class="sxs-lookup"><span data-stu-id="86608-242">Open the **App** folder.</span></span>
* <span data-ttu-id="86608-243">Öffnen der **ModelExplorer Visual Studio-Projektmappe**.</span><span class="sxs-lookup"><span data-stu-id="86608-243">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="86608-244">(Wenn Sie bereits erstellt bzw. dieses Projekt in Visual Studio während der Einrichtung bereitgestellt, klicken Sie dann Sie können diese Instanz von Visual Studio öffnen und klicken Sie auf "Alles neu laden" Wenn Sie aufgefordert werden).</span><span class="sxs-lookup"><span data-stu-id="86608-244">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>

* <span data-ttu-id="86608-245">Klicken Sie in Visual Studio auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="86608-245">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="86608-246">Nachdem die Anwendung, die HoloLens bereitstellt, schließen Sie das mit ähnlichen Zeichen mithilfe der [tippbewegung](gestures.md#air-tap) Bewegung.</span><span class="sxs-lookup"><span data-stu-id="86608-246">After the application deploys to the HoloLens, dismiss the fit box using the [air-tap](gestures.md#air-tap) gesture.</span></span>
* <span data-ttu-id="86608-247">Bestaunen Sie an die Astronautenausweis des überwachen.</span><span class="sxs-lookup"><span data-stu-id="86608-247">Gaze at the astronaut's watch.</span></span>
* <span data-ttu-id="86608-248">Wenn die Überwachung über den Fokus besitzt, stellen Sie sicher, dass der Cursor in ein Mikrofon ändert.</span><span class="sxs-lookup"><span data-stu-id="86608-248">When the watch has focus, verify that the cursor changes to a microphone.</span></span> <span data-ttu-id="86608-249">Dadurch wird ein Feedback, das der Anwendung für Sprachbefehle überwacht wird.</span><span class="sxs-lookup"><span data-stu-id="86608-249">This provides feedback that the application is listening for voice commands.</span></span>
* <span data-ttu-id="86608-250">Stellen Sie sicher, dass eine QuickInfo auf der Apple Watch angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="86608-250">Verify that a tooltip appears on the watch.</span></span> <span data-ttu-id="86608-251">Dadurch können Benutzer ermitteln die *"Open Communicator"* Befehl.</span><span class="sxs-lookup"><span data-stu-id="86608-251">This helps users discover the *"Open Communicator"* command.</span></span>
* <span data-ttu-id="86608-252">Während Sie auf der Apple Watch gazing, z. B. *"Communicator öffnen"* den Communicator-Bereich zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="86608-252">While gazing at the watch, say *"Open Communicator"* to open the communicator panel.</span></span>

## <a name="chapter-2---acknowledgement"></a><span data-ttu-id="86608-253">Kapitel 2 – Bestätigung</span><span class="sxs-lookup"><span data-stu-id="86608-253">Chapter 2 - Acknowledgement</span></span>

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a><span data-ttu-id="86608-254">Ziele</span><span class="sxs-lookup"><span data-stu-id="86608-254">Objectives</span></span>

* <span data-ttu-id="86608-255">Zeichnen Sie eine Nachricht mit der Mikrofoneingabe.</span><span class="sxs-lookup"><span data-stu-id="86608-255">Record a message using the Microphone input.</span></span>
* <span data-ttu-id="86608-256">Geben Sie Feedback an den Benutzer, den der Anwendung, um ihre Stimme überwacht wird an.</span><span class="sxs-lookup"><span data-stu-id="86608-256">Give feedback to the user that the application is listening to their voice.</span></span>

>[!NOTE]
><span data-ttu-id="86608-257">Die **Mikrofon** Funktion muss deklariert werden, dass eine app aus dem Mikrofon aufzeichnen.</span><span class="sxs-lookup"><span data-stu-id="86608-257">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="86608-258">Dies ist für die Sie bereits unter MR Eingabe 212, aber beachten Sie, dass für Ihre eigenen Projekte.</span><span class="sxs-lookup"><span data-stu-id="86608-258">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="86608-259">Rufen Sie im Unity-Editor die playereinstellungen durch Navigieren zu "Bearbeiten > Projekt Einstellungen > Player"</span><span class="sxs-lookup"><span data-stu-id="86608-259">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="86608-260">Klicken Sie auf der Registerkarte "Universal Windows Platform"</span><span class="sxs-lookup"><span data-stu-id="86608-260">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="86608-261">Überprüfen Sie im Abschnitt "Einstellungen > Veröffentlichungsfunktionen" die **Mikrofon** Funktion</span><span class="sxs-lookup"><span data-stu-id="86608-261">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="86608-262">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="86608-262">Instructions</span></span>

* <span data-ttu-id="86608-263">In Unity **Hierarchie** überprüfen Sie, ob im Bereich der **HoloComm_screen_mesh** Objekt ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="86608-263">In Unity's **Hierarchy** panel, verify that the **holoComm_screen_mesh** object is selected.</span></span>
* <span data-ttu-id="86608-264">In der **Inspektor** Bereich, suchen Sie nach der **Astronautenausweis überwachen (Skript)** Komponente.</span><span class="sxs-lookup"><span data-stu-id="86608-264">In the **Inspector** panel, find the **Astronaut Watch (Script)** component.</span></span>
* <span data-ttu-id="86608-265">Klicken Sie auf die blaue Cube das als Wert festgelegt ist die **Communicator-Prefab** Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="86608-265">Click on the small, blue cube which is set as the value of the **Communicator Prefab** property.</span></span>
* <span data-ttu-id="86608-266">In der **Projekt** Bereich der **Communicator** Prefab verfügen nun über den Fokus.</span><span class="sxs-lookup"><span data-stu-id="86608-266">In the **Project** panel, the **Communicator** prefab should now have focus.</span></span>
* <span data-ttu-id="86608-267">Klicken Sie auf die **Communicator** prefab in die **Projekt** Panel an seiner Komponenten in der **Inspektor**.</span><span class="sxs-lookup"><span data-stu-id="86608-267">Click on the **Communicator** prefab in the **Project** panel to view its components in the **Inspector**.</span></span>
* <span data-ttu-id="86608-268">Sehen Sie sich die **Mikrofon-Manager (Skript)** Komponente diese Weise können wir des Benutzers Stimme aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="86608-268">Look at the **Microphone Manager (Script)** component, this will allow us to record the user's voice.</span></span>
* <span data-ttu-id="86608-269">Beachten Sie, dass die **Communicator** Objekt verfügt über eine **Eingabe Handler für die Spracherkennung (Skript)** Komponente für die Reaktion auf die **Send Message** Befehl.</span><span class="sxs-lookup"><span data-stu-id="86608-269">Notice that the **Communicator** object has a **Speech Input Handler (Script)** component for responding to the **Send Message** command.</span></span>
* <span data-ttu-id="86608-270">Sehen Sie sich die **Communicator (Skript)** -Komponente, und doppelklicken Sie auf das Skript aus, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="86608-270">Look at the **Communicator (Script)** component and double-click on the script to open it in Visual Studio.</span></span>

<span data-ttu-id="86608-271">Communicator.cs ist verantwortlich für die ordnungsgemäße Schaltflächenstatus festlegen, auf dem Communicator-Gerät.</span><span class="sxs-lookup"><span data-stu-id="86608-271">Communicator.cs is responsible for setting the proper button states on the communicator device.</span></span> <span data-ttu-id="86608-272">Dadurch können Benutzer eine Nachricht aufzeichnen, es wiedergeben und sendet die Nachricht an die Astronautenausweis.</span><span class="sxs-lookup"><span data-stu-id="86608-272">This will allow our users to record a message, play it back, and send the message to the astronaut.</span></span> <span data-ttu-id="86608-273">Es auch starten und beenden eine animierten Wave-Form, um dem Benutzer bestätigen, dass ihre Stimme gehört, wurde.</span><span class="sxs-lookup"><span data-stu-id="86608-273">It will also start and stop an animated wave form, to acknowledge to the user that their voice was heard.</span></span>

* <span data-ttu-id="86608-274">In **Communicator.cs**, löschen Sie die folgenden Zeilen (81 und 82), aus der **starten** Methode.</span><span class="sxs-lookup"><span data-stu-id="86608-274">In **Communicator.cs**, delete the following lines (81 and 82) from the **Start** method.</span></span> <span data-ttu-id="86608-275">Dadurch wird die Schaltfläche "Record" für den Communicator ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="86608-275">This will enable the 'Record' button on the communicator.</span></span>

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a><span data-ttu-id="86608-276">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="86608-276">Build and Deploy</span></span>

* <span data-ttu-id="86608-277">Klicken Sie in Visual Studio die Anwendung neu erstellen und auf dem Gerät bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="86608-277">In Visual Studio, rebuild your application and deploy to the device.</span></span>
* <span data-ttu-id="86608-278">An die Astronautenausweis des Watch bestaunen und sagen *"Open Communicator"* den Communicator angezeigt.</span><span class="sxs-lookup"><span data-stu-id="86608-278">Gaze at the astronaut's watch and say *"Open Communicator"* to show the communicator.</span></span>
* <span data-ttu-id="86608-279">Drücken Sie die **Datensatz** Schaltfläche (Mikrofon) zum Starten der Aufzeichnung einer mündlichen Nachricht für die Astronautenausweis.</span><span class="sxs-lookup"><span data-stu-id="86608-279">Press the **Record** button (microphone) to start recording a verbal message for the astronaut.</span></span>
* <span data-ttu-id="86608-280">Spracheingabe/-Ausgabe starten, und stellen Sie sicher, dass die Welle Animation auf der Communicator bietet Feedback an den Benutzer, dass ihre Stimme gehört wird.</span><span class="sxs-lookup"><span data-stu-id="86608-280">Start speaking, and verify that the wave animation plays on the communicator, which provides feedback to the user that their voice is heard.</span></span>
* <span data-ttu-id="86608-281">Drücken Sie die **beenden** Schaltfläche (linke Quadrat), und stellen Sie sicher, dass die Wave-Animation beendet wird.</span><span class="sxs-lookup"><span data-stu-id="86608-281">Press the **Stop** button (left square), and verify that the wave animation stops running.</span></span>
* <span data-ttu-id="86608-282">Drücken Sie die **spielen** Schaltfläche (Rechtwinkliges Dreieck) zum Wiedergeben der aufgezeichneten Meldung und hören sie auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="86608-282">Press the **Play** button (right triangle) to play back the recorded message and hear it on the device.</span></span>
* <span data-ttu-id="86608-283">Drücken Sie die **beenden** Schaltfläche (rechts Quadrat) zum Beenden der Wiedergabe der aufgezeichneten Meldung.</span><span class="sxs-lookup"><span data-stu-id="86608-283">Press the **Stop** button (right square) to stop playback of the recorded message.</span></span>
* <span data-ttu-id="86608-284">Sagen Sie *"Nachricht senden"* schließen den Communicator und von der Astronautenausweis "Nachricht empfangen" eine Antwort empfängt.</span><span class="sxs-lookup"><span data-stu-id="86608-284">Say *"Send Message"* to close the communicator and receive a 'Message Received' response from the astronaut.</span></span>

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a><span data-ttu-id="86608-285">Kapitel 3: verstehen und die Erkennung Diktat</span><span class="sxs-lookup"><span data-stu-id="86608-285">Chapter 3 - Understanding and the Dictation Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a><span data-ttu-id="86608-286">Ziele</span><span class="sxs-lookup"><span data-stu-id="86608-286">Objectives</span></span>

* <span data-ttu-id="86608-287">Verwenden Sie die Erkennung Diktat des Benutzers Sprache in Text konvertiert.</span><span class="sxs-lookup"><span data-stu-id="86608-287">Use the Dictation Recognizer to convert the user's speech to text.</span></span>
* <span data-ttu-id="86608-288">Der Diktat Erkennung-angenommener und Endergebnisse zurück in den Communicator anzeigen.</span><span class="sxs-lookup"><span data-stu-id="86608-288">Show the Dictation Recognizer's hypothesized and final results in the communicator.</span></span>

<span data-ttu-id="86608-289">In diesem Kapitel verwenden wir die Erkennung Diktat zum Erstellen einer Nachricht für die Astronautenausweis.</span><span class="sxs-lookup"><span data-stu-id="86608-289">In this chapter, we'll use the Dictation Recognizer to create a message for the astronaut.</span></span> <span data-ttu-id="86608-290">Wenn Sie die Diktat-Erkennung zu verwenden, beachten Sie, dass:</span><span class="sxs-lookup"><span data-stu-id="86608-290">When using the Dictation Recognizer, keep in mind that:</span></span>

* <span data-ttu-id="86608-291">Sie müssen mit WiFi für das Erkennungsmodul Diktatmodus funktioniert verbunden werden.</span><span class="sxs-lookup"><span data-stu-id="86608-291">You must be connected to WiFi for the Dictation Recognizer to work.</span></span>
* <span data-ttu-id="86608-292">Timeouts treten auf, nach einem festgelegten Zeitraum.</span><span class="sxs-lookup"><span data-stu-id="86608-292">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="86608-293">Es gibt zwei Timeouts zu beachten:</span><span class="sxs-lookup"><span data-stu-id="86608-293">There are two timeouts to be aware of:</span></span>
  * <span data-ttu-id="86608-294">Wenn die Erkennung gestartet wird und keine Audiodaten für die ersten fünf Sekunden zu hören, tritt ein Timeout ein.</span><span class="sxs-lookup"><span data-stu-id="86608-294">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
  * <span data-ttu-id="86608-295">Wenn die Erkennung erhält ein Ergebnis, aber dann Ruheintervall 20 Sekunden lang hört, tritt ein Timeout ein.</span><span class="sxs-lookup"><span data-stu-id="86608-295">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>
* <span data-ttu-id="86608-296">Nur eine Art von Erkennung (Schlüsselwort oder Spracheingaben) kann zu einem Zeitpunkt ausführen.</span><span class="sxs-lookup"><span data-stu-id="86608-296">Only one type of recognizer (Keyword or Dictation) can run at a time.</span></span>

>[!NOTE]
><span data-ttu-id="86608-297">Die **Mikrofon** Funktion muss deklariert werden, dass eine app aus dem Mikrofon aufzeichnen.</span><span class="sxs-lookup"><span data-stu-id="86608-297">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="86608-298">Dies ist für die Sie bereits unter MR Eingabe 212, aber beachten Sie, dass für Ihre eigenen Projekte.</span><span class="sxs-lookup"><span data-stu-id="86608-298">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="86608-299">Rufen Sie im Unity-Editor die playereinstellungen durch Navigieren zu "Bearbeiten > Projekt Einstellungen > Player"</span><span class="sxs-lookup"><span data-stu-id="86608-299">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="86608-300">Klicken Sie auf der Registerkarte "Universal Windows Platform"</span><span class="sxs-lookup"><span data-stu-id="86608-300">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="86608-301">Überprüfen Sie im Abschnitt "Einstellungen > Veröffentlichungsfunktionen" die **Mikrofon** Funktion</span><span class="sxs-lookup"><span data-stu-id="86608-301">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="86608-302">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="86608-302">Instructions</span></span>

<span data-ttu-id="86608-303">Wir werden so bearbeiten Sie **MicrophoneManager.cs** die Diktat-Erkennung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="86608-303">We're going to edit **MicrophoneManager.cs** to use the Dictation Recognizer.</span></span> <span data-ttu-id="86608-304">Dies ist, was wir hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="86608-304">This is what we'll add:</span></span>

1. <span data-ttu-id="86608-305">Wenn die **Schaltfläche "Aufzeichnen"** ist wir gedrückt, **starten die DictationRecognizer**.</span><span class="sxs-lookup"><span data-stu-id="86608-305">When the **Record button** is pressed, we'll **start the DictationRecognizer**.</span></span>
2. <span data-ttu-id="86608-306">Anzeigen der **Hypothese** von der DictationRecognizer verstanden.</span><span class="sxs-lookup"><span data-stu-id="86608-306">Show the **hypothesis** of what the DictationRecognizer understood.</span></span>
3. <span data-ttu-id="86608-307">Sperren der **Ergebnisse** von der DictationRecognizer verstanden.</span><span class="sxs-lookup"><span data-stu-id="86608-307">Lock in the **results** of what the DictationRecognizer understood.</span></span>
4. <span data-ttu-id="86608-308">Für die DictationRecognizer-Timeouts überprüfen.</span><span class="sxs-lookup"><span data-stu-id="86608-308">Check for timeouts from the DictationRecognizer.</span></span>
5. <span data-ttu-id="86608-309">Wenn die **Schaltfläche "Stopp"** befindet, gedrückt wird oder mic Timeout der Sitzung, **Beenden der DictationRecognizer**.</span><span class="sxs-lookup"><span data-stu-id="86608-309">When the **Stop button** is pressed, or the mic session times out, **stop the DictationRecognizer**.</span></span>
6. <span data-ttu-id="86608-310">Neustart der **KeywordRecognizer**, Lauschen für die **Send Message** Befehl.</span><span class="sxs-lookup"><span data-stu-id="86608-310">Restart the **KeywordRecognizer**, which will listen for the **Send Message** command.</span></span>

<span data-ttu-id="86608-311">Los geht's.</span><span class="sxs-lookup"><span data-stu-id="86608-311">Let's get started.</span></span> <span data-ttu-id="86608-312">Führen Sie alle codierungsübungen für 3.a in **MicrophoneManager.cs**, oder kopieren Sie den fertig gestellten Code finden Sie unten:</span><span class="sxs-lookup"><span data-stu-id="86608-312">Complete all coding exercises for 3.a in **MicrophoneManager.cs**, or copy and paste the finished code found below:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone. 
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="86608-313">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="86608-313">Build and Deploy</span></span>

* <span data-ttu-id="86608-314">Erstellen Sie in Visual Studio neu, und auf Ihrem Gerät bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="86608-314">Rebuild in Visual Studio and deploy to your device.</span></span>
* <span data-ttu-id="86608-315">Im Lieferumfang von eine tippbewegung Geste mit ähnlichen Zeichen zu schließen.</span><span class="sxs-lookup"><span data-stu-id="86608-315">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="86608-316">An die Astronautenausweis des Watch bestaunen und sagen *"Open Communicator"*.</span><span class="sxs-lookup"><span data-stu-id="86608-316">Gaze at the astronaut's watch and say *"Open Communicator"*.</span></span>
* <span data-ttu-id="86608-317">Wählen Sie die **Datensatz** Schaltfläche (Mikrofon), um Ihre Nachricht aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="86608-317">Select the **Record** button (microphone) to record your message.</span></span>
* <span data-ttu-id="86608-318">Starten Sie Spracheingabe/-Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="86608-318">Start speaking.</span></span> <span data-ttu-id="86608-319">Die **Diktat Erkennung** interpretiert die Spracherkennung und Anzeigen von die Hypothese Text in den Communicator.</span><span class="sxs-lookup"><span data-stu-id="86608-319">The **Dictation Recognizer** will interpret your speech and show the hypothesized text in the communicator.</span></span>
* <span data-ttu-id="86608-320">Versuchen Sie es mit dem Text *"Nachricht senden"* während Sie eine Nachricht aufzeichnen.</span><span class="sxs-lookup"><span data-stu-id="86608-320">Try saying *"Send Message"* while you are recording a message.</span></span> <span data-ttu-id="86608-321">Beachten Sie, dass die **Schlüsselwort Erkennung** reagiert nicht, da die **Diktat Erkennung** weiterhin aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="86608-321">Notice that the **Keyword Recognizer** does not respond because the **Dictation Recognizer** is still active.</span></span>
* <span data-ttu-id="86608-322">Beenden Sie sprechen ein paar Sekunden.</span><span class="sxs-lookup"><span data-stu-id="86608-322">Stop speaking for a few seconds.</span></span> <span data-ttu-id="86608-323">Verfolgen Sie, wie die Erkennung Diktat die Hypothese schließt ab und das endgültige Ergebnis zeigt.</span><span class="sxs-lookup"><span data-stu-id="86608-323">Watch as the Dictation Recognizer completes its hypothesis and shows the final result.</span></span>
* <span data-ttu-id="86608-324">Beginnen Sie sprechen, und dann eine pause 20 Sekunden.</span><span class="sxs-lookup"><span data-stu-id="86608-324">Begin speaking and then pause for 20 seconds.</span></span> <span data-ttu-id="86608-325">Dies bewirkt, dass die **Diktat Erkennung** Timeout.</span><span class="sxs-lookup"><span data-stu-id="86608-325">This will cause the **Dictation Recognizer** to timeout.</span></span>
* <span data-ttu-id="86608-326">Beachten Sie, dass die **Schlüsselwort Erkennung** wieder aktiviert wird, nach dem oben genannten Timeout.</span><span class="sxs-lookup"><span data-stu-id="86608-326">Notice that the **Keyword Recognizer** is re-enabled after the above timeout.</span></span> <span data-ttu-id="86608-327">Der Communicator wird nun auf Sprachbefehle reagieren.</span><span class="sxs-lookup"><span data-stu-id="86608-327">The communicator will now respond to voice commands.</span></span>
* <span data-ttu-id="86608-328">Sagen Sie *"Nachricht senden"* zum Senden der Nachricht an die Astronautenausweis.</span><span class="sxs-lookup"><span data-stu-id="86608-328">Say *"Send Message"* to send the message to the astronaut.</span></span>

## <a name="chapter-4---grammar-recognizer"></a><span data-ttu-id="86608-329">Kapitel 4: Erkennung der Grammatik</span><span class="sxs-lookup"><span data-stu-id="86608-329">Chapter 4 - Grammar Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a><span data-ttu-id="86608-330">Ziele</span><span class="sxs-lookup"><span data-stu-id="86608-330">Objectives</span></span>

* <span data-ttu-id="86608-331">Verwenden Sie die Erkennung der Grammatik für gemäß einer SRGS oder Speech Recognition-Grammatik-Spezifikation-Datei des Benutzers Spracherkennung.</span><span class="sxs-lookup"><span data-stu-id="86608-331">Use the Grammar Recognizer to recognize the user's speech according to an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

>[!NOTE]
><span data-ttu-id="86608-332">Die **Mikrofon** Funktion muss deklariert werden, dass eine app aus dem Mikrofon aufzeichnen.</span><span class="sxs-lookup"><span data-stu-id="86608-332">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="86608-333">Dies ist für die Sie bereits unter MR Eingabe 212, aber beachten Sie, dass für Ihre eigenen Projekte.</span><span class="sxs-lookup"><span data-stu-id="86608-333">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="86608-334">Rufen Sie im Unity-Editor die playereinstellungen durch Navigieren zu "Bearbeiten > Projekt Einstellungen > Player"</span><span class="sxs-lookup"><span data-stu-id="86608-334">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="86608-335">Klicken Sie auf der Registerkarte "Universal Windows Platform"</span><span class="sxs-lookup"><span data-stu-id="86608-335">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="86608-336">Überprüfen Sie im Abschnitt "Einstellungen > Veröffentlichungsfunktionen" die **Mikrofon** Funktion</span><span class="sxs-lookup"><span data-stu-id="86608-336">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="86608-337">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="86608-337">Instructions</span></span>

1. <span data-ttu-id="86608-338">In der **Hierarchie** Bereich, suchen Sie nach **Jetpack_Center** und wählen Sie ihn.</span><span class="sxs-lookup"><span data-stu-id="86608-338">In the **Hierarchy** panel, search for **Jetpack_Center** and select it.</span></span>
2. <span data-ttu-id="86608-339">Suchen Sie nach der **beigefügten Aktion** -Skript in den **Inspektor** Bereich.</span><span class="sxs-lookup"><span data-stu-id="86608-339">Look for the **Tagalong Action** script in the **Inspector** panel.</span></span>
3. <span data-ttu-id="86608-340">Klicken Sie auf den kleinen Kreis rechts neben der **Objekt zum Tag zusammen** Feld.</span><span class="sxs-lookup"><span data-stu-id="86608-340">Click the little circle to the right of the **Object To Tag Along** field.</span></span>
4. <span data-ttu-id="86608-341">Suchen Sie im Fenster, das wird angezeigt, nach **SRGSToolbox** und wählen Sie sie aus der Liste.</span><span class="sxs-lookup"><span data-stu-id="86608-341">In the window that pops up, search for **SRGSToolbox** and select it from the list.</span></span>
5. <span data-ttu-id="86608-342">Sehen Sie sich die **SRGSColor.xml** Datei die **StreamingAssets** Ordner.</span><span class="sxs-lookup"><span data-stu-id="86608-342">Take a look at the **SRGSColor.xml** file in the **StreamingAssets** folder.</span></span>
* <span data-ttu-id="86608-343">Die Spezifikation der SRGS-Entwurf finden Sie auf der W3C-Website [hier](https://www.w3.org/TR/speech-grammar/).</span><span class="sxs-lookup"><span data-stu-id="86608-343">The SRGS design spec can be found on the W3C website [here](https://www.w3.org/TR/speech-grammar/).</span></span>
* <span data-ttu-id="86608-344">In unserem SRGS-Datei haben wir drei Arten von Regeln:</span><span class="sxs-lookup"><span data-stu-id="86608-344">In our SRGS file, we have three types of rules:</span></span>
  * <span data-ttu-id="86608-345">Eine Regel, mit der Sie eine Farbe aus einer Liste von zwölf Farben sagen kann.</span><span class="sxs-lookup"><span data-stu-id="86608-345">A rule which lets you say one color from a list of twelve colors.</span></span>
  * <span data-ttu-id="86608-346">Drei Regeln, die für eine Kombination von Farbregel und eine der drei Formen zu überwachen.</span><span class="sxs-lookup"><span data-stu-id="86608-346">Three rules which listen for a combination of the color rule and one of the three shapes.</span></span>
  * <span data-ttu-id="86608-347">Die Stammregel ColorChooser, die für eine beliebige Kombination der drei Regeln für "Farbe und Form vom Typ" lauscht.</span><span class="sxs-lookup"><span data-stu-id="86608-347">The root rule, colorChooser, which listens for any combination of the three "color + shape" rules.</span></span> <span data-ttu-id="86608-348">Die Formen können in beliebiger Reihenfolge und in beliebigem Umfang von einem einzigen, alle drei zusammen.</span><span class="sxs-lookup"><span data-stu-id="86608-348">The shapes can be said in any order and in any amount from just one to all three.</span></span> <span data-ttu-id="86608-349">Dies ist die einzige Regel, die für lauscht, wie sie als Stammregel am Anfang der Datei in der ersten angegeben ist &lt;Grammatik&gt; Tag.</span><span class="sxs-lookup"><span data-stu-id="86608-349">This is the only rule that is listened for, as it's specified as the root rule at the top of the file in the initial &lt;grammar&gt; tag.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="86608-350">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="86608-350">Build and Deploy</span></span>

* <span data-ttu-id="86608-351">Erstellen Sie die Anwendung in Unity, anschließendes Erstellen und Bereitstellen von Visual Studio, um die app auf HoloLens auftreten.</span><span class="sxs-lookup"><span data-stu-id="86608-351">Rebuild the application in Unity, then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="86608-352">Im Lieferumfang von eine tippbewegung Geste mit ähnlichen Zeichen zu schließen.</span><span class="sxs-lookup"><span data-stu-id="86608-352">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="86608-353">Auf der Astronautenausweis des Jetpack bestaunen Sie, und führen Sie eine tippbewegung Bewegung.</span><span class="sxs-lookup"><span data-stu-id="86608-353">Gaze at the astronaut's jetpack and perform an air-tap gesture.</span></span>
* <span data-ttu-id="86608-354">Starten Sie Spracheingabe/-Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="86608-354">Start speaking.</span></span> <span data-ttu-id="86608-355">Die **Grammatik Erkennung** interpretiert die Spracherkennung und die Farbe der Formen, die basierend auf der Erkennung zu ändern.</span><span class="sxs-lookup"><span data-stu-id="86608-355">The **Grammar Recognizer** will interpret your speech and change the colors of the shapes based on the recognition.</span></span> <span data-ttu-id="86608-356">Ein Beispielbefehl ist "blauen Kreis, gelben Quadrat".</span><span class="sxs-lookup"><span data-stu-id="86608-356">An example command is "blue circle, yellow square".</span></span>
* <span data-ttu-id="86608-357">Führen Sie ein anderes Air-tippbewegung um die Toolbox zu schließen.</span><span class="sxs-lookup"><span data-stu-id="86608-357">Perform another air-tap gesture to dismiss the toolbox.</span></span>

## <a name="the-end"></a><span data-ttu-id="86608-358">Das Ende</span><span class="sxs-lookup"><span data-stu-id="86608-358">The End</span></span>

<span data-ttu-id="86608-359">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="86608-359">Congratulations!</span></span> <span data-ttu-id="86608-360">Sie haben jetzt **MR Eingabe 212: Voice**.</span><span class="sxs-lookup"><span data-stu-id="86608-360">You have now completed **MR Input 212: Voice**.</span></span>

* <span data-ttu-id="86608-361">Sie kennen die Empfehlungen und von Stimmbefehlen.</span><span class="sxs-lookup"><span data-stu-id="86608-361">You know the Dos and Don'ts of voice commands.</span></span>
* <span data-ttu-id="86608-362">Sie haben gesehen, wie QuickInfos eingesetzt wurden, um die Benutzer Sprachbefehle aufmerksam zu machen.</span><span class="sxs-lookup"><span data-stu-id="86608-362">You saw how tooltips were employed to make users aware of voice commands.</span></span>
* <span data-ttu-id="86608-363">Sie haben verschiedene Arten von Feedback zu bestätigen, dass der Benutzer beteiligen wurde verwendet.</span><span class="sxs-lookup"><span data-stu-id="86608-363">You saw several types of feedback used to acknowledge that the user's voice was heard.</span></span>
* <span data-ttu-id="86608-364">Sie wissen, Informationen zum Wechseln zwischen die Schlüsselwort-Erkennung und die Erkennung von Spracheingaben und wie Sie diese beiden Funktionen zum verstehen und Interpretieren der Stimme.</span><span class="sxs-lookup"><span data-stu-id="86608-364">You know how to switch between the Keyword Recognizer and the Dictation Recognizer, and how these two features understand and interpret your voice.</span></span>
* <span data-ttu-id="86608-365">Sie haben gelernt, wie eine SRGS-Datei und die Erkennung der Grammatik für die Spracherkennung in Ihrer Anwendung verwenden.</span><span class="sxs-lookup"><span data-stu-id="86608-365">You learned how to use an SRGS file and the Grammar Recognizer for speech recognition in your application.</span></span>
