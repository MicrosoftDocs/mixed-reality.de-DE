---
title: Mr-Eingabe 212-Stimme
description: Befolgen Sie diese exemplarische Vorgehensweise, indem Sie Unity, Visual Studio und hololens verwenden, um die Details der sprach Konzepte zu erlernen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, Tutorial, Stimme
ms.openlocfilehash: 9db503ea4c7db9a3eb272ad9663024ca3a407dda
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434599"
---
>[!NOTE]
><span data-ttu-id="1ef32-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1ef32-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="1ef32-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1ef32-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1ef32-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1ef32-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="1ef32-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1ef32-108">Es wurde [eine neue Reihe von Tutorials](mrlearning-base.md) für hololens 2 gepostet.</span><span class="sxs-lookup"><span data-stu-id="1ef32-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-input-212-voice"></a><span data-ttu-id="1ef32-109">Mr-Eingabe 212: Stimme</span><span class="sxs-lookup"><span data-stu-id="1ef32-109">MR Input 212: Voice</span></span>

<span data-ttu-id="1ef32-110">Die [Spracheingabe](voice-input.md) bietet uns eine weitere Möglichkeit, mit unseren holograms zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="1ef32-110">[Voice input](voice-input.md) gives us another way to interact with our holograms.</span></span> <span data-ttu-id="1ef32-111">Sprachbefehle funktionieren auf sehr natürliche und einfache Weise.</span><span class="sxs-lookup"><span data-stu-id="1ef32-111">Voice commands work in a very natural and easy way.</span></span> <span data-ttu-id="1ef32-112">Entwerfen Sie Ihre Sprachbefehle so, dass Sie wie folgt lauten:</span><span class="sxs-lookup"><span data-stu-id="1ef32-112">Design your voice commands so that they are:</span></span>

* <span data-ttu-id="1ef32-113">Natürliche</span><span class="sxs-lookup"><span data-stu-id="1ef32-113">Natural</span></span>
* <span data-ttu-id="1ef32-114">Leicht zu merken</span><span class="sxs-lookup"><span data-stu-id="1ef32-114">Easy to remember</span></span>
* <span data-ttu-id="1ef32-115">Geeigneter Kontext</span><span class="sxs-lookup"><span data-stu-id="1ef32-115">Context appropriate</span></span>
* <span data-ttu-id="1ef32-116">Ausreichend Unterschied zu anderen Optionen innerhalb desselben Kontexts</span><span class="sxs-lookup"><span data-stu-id="1ef32-116">Sufficiently distinct from other options within the same context</span></span>

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

<span data-ttu-id="1ef32-117">In den [Grundlagen 101](holograms-101.md)haben wir keywordrecognizer verwendet, um zwei einfache Sprachbefehle zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-117">In [MR Basics 101](holograms-101.md), we used the KeywordRecognizer to build two simple voice commands.</span></span> <span data-ttu-id="1ef32-118">In der Eingabe 212 gehen wir genauer vor und lernen, wie Sie:</span><span class="sxs-lookup"><span data-stu-id="1ef32-118">In MR Input 212, we'll dive deeper and learn how to:</span></span>

* <span data-ttu-id="1ef32-119">Entwerfen Sie Sprachbefehle, die für die hololens-Sprach-Engine optimiert sind.</span><span class="sxs-lookup"><span data-stu-id="1ef32-119">Design voice commands that are optimized for the HoloLens speech engine.</span></span>
* <span data-ttu-id="1ef32-120">Sorgen Sie dafür, dass der Benutzer weiß, welche Sprachbefehle verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="1ef32-120">Make the user aware of what voice commands are available.</span></span>
* <span data-ttu-id="1ef32-121">Bestätigen Sie, dass der Sprachbefehl des Benutzers gehört.</span><span class="sxs-lookup"><span data-stu-id="1ef32-121">Acknowledge that we've heard the user's voice command.</span></span>
* <span data-ttu-id="1ef32-122">Verstehen Sie, was der Benutzer sagt, mithilfe einer Diktat Erkennung.</span><span class="sxs-lookup"><span data-stu-id="1ef32-122">Understand what the user is saying, using a Dictation Recognizer.</span></span>
* <span data-ttu-id="1ef32-123">Verwenden Sie eine Grammatik Erkennung, um Befehle auf der Grundlage einer SRGS-oder Spracherkennungs-Grammatik Spezifikation (File) abzuhören.</span><span class="sxs-lookup"><span data-stu-id="1ef32-123">Use a Grammar Recognizer to listen for commands based on an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

<span data-ttu-id="1ef32-124">In diesem Kurs überprüfen wir den Modell-Explorer, den wir in der [Eingabe 210](holograms-210.md) und in der [Eingabe 211](holograms-211.md)von Mr erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="1ef32-124">In this course, we'll revisit Model Explorer, which we built in [MR Input 210](holograms-210.md) and [MR Input 211](holograms-211.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="1ef32-125">Die in den folgenden Kapiteln eingebetteten Videos wurden mit einer älteren Version von Unity und dem Mixed Reality Toolkit aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="1ef32-125">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="1ef32-126">Die Schritt-für-Schritt-Anweisungen sind genau und aktuell, aber es werden möglicherweise Skripts und Visualisierungen in den entsprechenden Videos angezeigt, die veraltet sind.</span><span class="sxs-lookup"><span data-stu-id="1ef32-126">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="1ef32-127">Die Videos bleiben in der einwelt enthalten und werden weiterhin angewendet.</span><span class="sxs-lookup"><span data-stu-id="1ef32-127">The videos remain included for posterity and because the concepts covered still apply.</span></span>


## <a name="device-support"></a><span data-ttu-id="1ef32-128">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="1ef32-128">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1ef32-129">Natürlich</span><span class="sxs-lookup"><span data-stu-id="1ef32-129">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1ef32-130"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1ef32-130"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1ef32-131"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="1ef32-131"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="1ef32-132">Mr-Eingabe 212: Stimme</span><span class="sxs-lookup"><span data-stu-id="1ef32-132">MR Input 212: Voice</span></span></td><td style="text-align: center;"> <span data-ttu-id="1ef32-133">✔️</span><span class="sxs-lookup"><span data-stu-id="1ef32-133">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1ef32-134">✔️</span><span class="sxs-lookup"><span data-stu-id="1ef32-134">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="1ef32-135">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="1ef32-135">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="1ef32-136">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="1ef32-136">Prerequisites</span></span>

* <span data-ttu-id="1ef32-137">Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md)konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="1ef32-137">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="1ef32-138">Einige Grund C# Legende Programmiermöglichkeiten.</span><span class="sxs-lookup"><span data-stu-id="1ef32-138">Some basic C# programming ability.</span></span>
* <span data-ttu-id="1ef32-139">Sie sollten die [Grundlagen von 101](holograms-101.md)abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="1ef32-139">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="1ef32-140">Sie sollten die [Mr-Eingabe 210](holograms-210.md)abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="1ef32-140">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="1ef32-141">Sie sollten die [Mr-Eingabe 211](holograms-211.md)abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="1ef32-141">You should have completed [MR Input 211](holograms-211.md).</span></span>
* <span data-ttu-id="1ef32-142">Ein hololens-Gerät, das [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode)ist.</span><span class="sxs-lookup"><span data-stu-id="1ef32-142">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="1ef32-143">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="1ef32-143">Project files</span></span>

* <span data-ttu-id="1ef32-144">Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) , die für das Projekt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="1ef32-144">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) required by the project.</span></span> <span data-ttu-id="1ef32-145">Erfordert Unity 2017,2 oder höher.</span><span class="sxs-lookup"><span data-stu-id="1ef32-145">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="1ef32-146">Deinstallieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht zugänglichen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="1ef32-146">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="1ef32-147">Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span><span class="sxs-lookup"><span data-stu-id="1ef32-147">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="1ef32-148">Errata und Notizen</span><span class="sxs-lookup"><span data-stu-id="1ef32-148">Errata and Notes</span></span>

* <span data-ttu-id="1ef32-149">"Enable nur eigenen Code" muss in Visual Studio unter "Extras-> Optionen" deaktiviert*werden (>* Debuggen, um Breakpoints im Code zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-149">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="1ef32-150">Unity-Setup</span><span class="sxs-lookup"><span data-stu-id="1ef32-150">Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="1ef32-151">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="1ef32-151">Instructions</span></span>

1. <span data-ttu-id="1ef32-152">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="1ef32-152">Start Unity.</span></span>
2. <span data-ttu-id="1ef32-153">Wählen Sie **Öffnen**aus.</span><span class="sxs-lookup"><span data-stu-id="1ef32-153">Select **Open**.</span></span>
3. <span data-ttu-id="1ef32-154">Navigieren Sie zum Ordner **holographicacademy-holograms-212-Voice** , den Sie zuvor nicht archiviert haben.</span><span class="sxs-lookup"><span data-stu-id="1ef32-154">Navigate to the **HolographicAcademy-Holograms-212-Voice** folder you previously un-archived.</span></span>
4. <span data-ttu-id="1ef32-155">Suchen Sie den Ordner **Start**/**Model Explorer** , und wählen Sie ihn aus.</span><span class="sxs-lookup"><span data-stu-id="1ef32-155">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="1ef32-156">Klicken Sie auf die Schaltfläche **Ordner auswählen** .</span><span class="sxs-lookup"><span data-stu-id="1ef32-156">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="1ef32-157">Erweitern Sie im **Projekt** Panel den Ordner **Szenen** .</span><span class="sxs-lookup"><span data-stu-id="1ef32-157">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="1ef32-158">Doppelklicken Sie auf **Model Explorer** Scene, um es in Unity zu laden.</span><span class="sxs-lookup"><span data-stu-id="1ef32-158">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="1ef32-159">Erstellen</span><span class="sxs-lookup"><span data-stu-id="1ef32-159">Building</span></span>

1. <span data-ttu-id="1ef32-160">Wählen Sie in Unity **Datei > Buildeinstellungen**aus.</span><span class="sxs-lookup"><span data-stu-id="1ef32-160">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="1ef32-161">Wenn **Szenen/Model Explorer** nicht in **Szenen im Build**aufgeführt ist, klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-161">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="1ef32-162">Wenn Sie speziell für hololens entwickeln, legen Sie **Zielgerät** auf **hololens**fest.</span><span class="sxs-lookup"><span data-stu-id="1ef32-162">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="1ef32-163">Andernfalls sollten Sie es auf **jedem Gerät**belassen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-163">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="1ef32-164">Stellen Sie sicher, dass der **Buildtyp** auf **D3D** und das **SDK** auf **Latest installiert** festgelegt ist (was SDK 16299 oder höher sein sollte).</span><span class="sxs-lookup"><span data-stu-id="1ef32-164">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="1ef32-165">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="1ef32-165">Click **Build**.</span></span>
6. <span data-ttu-id="1ef32-166">Erstellen Sie einen **neuen Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="1ef32-166">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="1ef32-167">Klicken Sie einfach auf den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="1ef32-167">Single click the **App** folder.</span></span>
8. <span data-ttu-id="1ef32-168">Klicken **Sie auf Ordner auswählen** , und Unity startet das Projekt für Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1ef32-168">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="1ef32-169">Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1ef32-169">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="1ef32-170">Öffnen Sie den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="1ef32-170">Open the **App** folder.</span></span>
2. <span data-ttu-id="1ef32-171">Öffnen Sie die Visual Studio-Projekt Mappe **Model Explorer**.</span><span class="sxs-lookup"><span data-stu-id="1ef32-171">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="1ef32-172">Bei der Bereitstellung in hololens:</span><span class="sxs-lookup"><span data-stu-id="1ef32-172">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="1ef32-173">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x86**.</span><span class="sxs-lookup"><span data-stu-id="1ef32-173">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="1ef32-174">Klicken Sie auf den Dropdown Pfeil neben der Schaltfläche lokaler Computer, und wählen Sie **Remote Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="1ef32-174">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="1ef32-175">Geben Sie **die IP-Adresse des hololens-Geräts** ein, und legen Sie den Authentifizierungsmodus auf **Universal (unverschlüsseltes Protokoll)**</span><span class="sxs-lookup"><span data-stu-id="1ef32-175">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="1ef32-176">Klicken Sie auf **Auswählen**.</span><span class="sxs-lookup"><span data-stu-id="1ef32-176">Click **Select**.</span></span> <span data-ttu-id="1ef32-177">Wenn Sie die IP-Adresse Ihres Geräts nicht kennen, suchen Sie unter **Einstellungen > Netzwerk & Internet > Erweiterte Optionen**.</span><span class="sxs-lookup"><span data-stu-id="1ef32-177">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="1ef32-178">Klicken Sie in der oberen Menüleiste auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="1ef32-178">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="1ef32-179">Wenn Sie die Bereitstellung auf Ihrem Gerät zum ersten Mal durchführt, müssen Sie [es mit Visual Studio](using-visual-studio.md#pairing-your-device)koppeln.</span><span class="sxs-lookup"><span data-stu-id="1ef32-179">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="1ef32-180">Wenn die APP bereitgestellt wurde, schließen Sie das **fitbox** -Gerät mit einer **Auswahl Bewegung**ab.</span><span class="sxs-lookup"><span data-stu-id="1ef32-180">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="1ef32-181">Bei der Bereitstellung auf einem immersiven Headset:</span><span class="sxs-lookup"><span data-stu-id="1ef32-181">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="1ef32-182">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x64**.</span><span class="sxs-lookup"><span data-stu-id="1ef32-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="1ef32-183">Stellen Sie sicher, dass das Bereitstellungs Ziel auf **lokaler Computer**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="1ef32-183">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="1ef32-184">Klicken Sie in der oberen Menüleiste auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="1ef32-184">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="1ef32-185">Wenn die APP bereitgestellt wurde, schließen Sie die Funktion **, indem Sie den-** Typ auf einen Bewegungs Controller ziehen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-185">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="1ef32-186">Im Visual Studio-Fehler Panel werden möglicherweise einige rote Fehler feststellen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-186">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="1ef32-187">Es ist sicher, Sie zu ignorieren.</span><span class="sxs-lookup"><span data-stu-id="1ef32-187">It is safe to ignore them.</span></span> <span data-ttu-id="1ef32-188">Wechseln Sie zum Ausgabebereich, um den tatsächlichen buildfortschritt anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-188">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="1ef32-189">Fehler im Ausgabe Panel erfordern eine Korrektur (meistens werden Sie durch einen Fehler in einem Skript verursacht).</span><span class="sxs-lookup"><span data-stu-id="1ef32-189">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---awareness"></a><span data-ttu-id="1ef32-190">Kapitel 1: Informationen zum Bewusstsein</span><span class="sxs-lookup"><span data-stu-id="1ef32-190">Chapter 1 - Awareness</span></span>

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a><span data-ttu-id="1ef32-191">Ziele</span><span class="sxs-lookup"><span data-stu-id="1ef32-191">Objectives</span></span>

* <span data-ttu-id="1ef32-192">Erfahren Sie mehr über die **DOS-und "TS** of Voice Command Design".</span><span class="sxs-lookup"><span data-stu-id="1ef32-192">Learn the **Dos and Don'ts** of voice command design.</span></span>
* <span data-ttu-id="1ef32-193">Verwenden Sie **keywordrecognizer** , um auf Blick basierende Sprachbefehle hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-193">Use **KeywordRecognizer** to add gaze based voice commands.</span></span>
* <span data-ttu-id="1ef32-194">Sorgen Sie dafür, dass Benutzer Sprachbefehle mithilfe von Cursor **Feedback**erkennen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-194">Make users aware of voice commands using cursor **feedback**.</span></span>

### <a name="voice-command-design"></a><span data-ttu-id="1ef32-195">Sprach Befehls Entwurf</span><span class="sxs-lookup"><span data-stu-id="1ef32-195">Voice Command Design</span></span>

<span data-ttu-id="1ef32-196">In diesem Kapitel erfahren Sie mehr über das Entwerfen von Sprachbefehlen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-196">In this chapter, you'll learn about designing voice commands.</span></span> <span data-ttu-id="1ef32-197">Beim Erstellen von Sprachbefehlen:</span><span class="sxs-lookup"><span data-stu-id="1ef32-197">When creating voice commands:</span></span>

#### <a name="do"></a><span data-ttu-id="1ef32-198">DO</span><span class="sxs-lookup"><span data-stu-id="1ef32-198">DO</span></span>

* <span data-ttu-id="1ef32-199">Erstellen Sie präzise Befehle.</span><span class="sxs-lookup"><span data-stu-id="1ef32-199">Create concise commands.</span></span> <span data-ttu-id="1ef32-200">Sie möchten nicht *"das aktuell ausgewählte Video abspielen*" verwenden, da dieser Befehl nicht präzise ist und vom Benutzer leicht vergessen wird.</span><span class="sxs-lookup"><span data-stu-id="1ef32-200">You don't want to use *"Play the currently selected video"*, because that command is not concise and would easily be forgotten by the user.</span></span> <span data-ttu-id="1ef32-201">Verwenden Sie stattdessen *"Video abspielen"* , da es sich um einen präzisen Wert handelt, der über mehrere Silben verfügt.</span><span class="sxs-lookup"><span data-stu-id="1ef32-201">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="1ef32-202">Verwenden Sie ein einfaches Vokabular.</span><span class="sxs-lookup"><span data-stu-id="1ef32-202">Use a simple vocabulary.</span></span> <span data-ttu-id="1ef32-203">Versuchen Sie immer, gängige Wörter und Ausdrücke zu verwenden, die für den Benutzer leicht zu erkennen und zu merken sind.</span><span class="sxs-lookup"><span data-stu-id="1ef32-203">Always try to use common words and phrases that are easy for the user to discover and remember.</span></span> <span data-ttu-id="1ef32-204">Wenn Ihre Anwendung z. b. ein Notiz Objekt hätte, das in der Ansicht angezeigt oder ausgeblendet werden kann, würden Sie den Befehl *"Placard anzeigen"* nicht verwenden, da "Placard" ein selten verwendeter Begriff ist.</span><span class="sxs-lookup"><span data-stu-id="1ef32-204">For example, if your application had a note object that could be displayed or hidden from view, you would not use the command *"Show Placard"*, because "placard" is a rarely used term.</span></span> <span data-ttu-id="1ef32-205">Verwenden Sie stattdessen den Befehl *"Show Note"* , um den Hinweis in der Anwendung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-205">Instead, you would use the command: *"Show Note"*, to reveal the note in your application.</span></span>
* <span data-ttu-id="1ef32-206">Achten Sie auf Einheitlichkeit.</span><span class="sxs-lookup"><span data-stu-id="1ef32-206">Be consistent.</span></span> <span data-ttu-id="1ef32-207">Sprachbefehle sollten in der gesamten Anwendung konsistent gehalten werden.</span><span class="sxs-lookup"><span data-stu-id="1ef32-207">Voice commands should be kept consistent across your application.</span></span> <span data-ttu-id="1ef32-208">Stellen Sie sich vor, dass Sie in Ihrer Anwendung zwei Szenen haben und beide Szenen eine Schaltfläche zum Schließen der Anwendung enthalten.</span><span class="sxs-lookup"><span data-stu-id="1ef32-208">Imagine that you have two scenes in your application and both scenes contain a button for closing the application.</span></span> <span data-ttu-id="1ef32-209">Wenn in der ersten Szene der Befehl *"Exit"* zum auslöst der Schaltfläche verwendet wird, aber die zweite Szene den Befehl *"APP schließen"* verwendet hat, wird der Benutzer sehr verwirrt.</span><span class="sxs-lookup"><span data-stu-id="1ef32-209">If the first scene used the command *"Exit"* to trigger the button, but the second scene used the command *"Close App"*, then the user is going to get very confused.</span></span> <span data-ttu-id="1ef32-210">Wenn die gleiche Funktionalität in mehreren Szenen beibehalten wird, sollte der gleiche Sprachbefehl verwendet werden, um Sie zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="1ef32-210">If the same functionality persists across multiple scenes, then the same voice command should be used to trigger it.</span></span>

#### <a name="dont"></a><span data-ttu-id="1ef32-211">Tue nicht</span><span class="sxs-lookup"><span data-stu-id="1ef32-211">DON'T</span></span>

* <span data-ttu-id="1ef32-212">Verwenden Sie einzelne Silb Bare Befehle.</span><span class="sxs-lookup"><span data-stu-id="1ef32-212">Use single syllable commands.</span></span> <span data-ttu-id="1ef32-213">Wenn Sie z. b. einen Sprachbefehl zum Abspielen eines Videos erstellt haben, sollten Sie die Verwendung des einfachen Befehls *"Play"* vermeiden, da es sich nur um eine einzelne Silb Bare Sprache handelt, die vom System leicht übersehen werden könnte.</span><span class="sxs-lookup"><span data-stu-id="1ef32-213">As an example, if you were creating a voice command to play a video, you should avoid using the simple command *"Play"*, as it is only a single syllable and could easily be missed by the system.</span></span> <span data-ttu-id="1ef32-214">Verwenden Sie stattdessen *"Video abspielen"* , da es sich um einen präzisen Wert handelt, der über mehrere Silben verfügt.</span><span class="sxs-lookup"><span data-stu-id="1ef32-214">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="1ef32-215">Verwenden Sie Systembefehle.</span><span class="sxs-lookup"><span data-stu-id="1ef32-215">Use system commands.</span></span> <span data-ttu-id="1ef32-216">Der Befehl *"Select"* ist vom System für das auslöst eines Tap-Ereignisses für das aktuell fokussierte Objekt reserviert.</span><span class="sxs-lookup"><span data-stu-id="1ef32-216">The *"Select"* command is reserved by the system to trigger a Tap event for the currently focused object.</span></span> <span data-ttu-id="1ef32-217">Verwenden Sie den Befehl *"Select"* nicht in einem Schlüsselwort oder Ausdruck, da dies möglicherweise nicht erwartungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="1ef32-217">Do not re-use the *"Select"* command in a keyword or phrase, as it might not work as you expect.</span></span> <span data-ttu-id="1ef32-218">Wenn z. b. der Sprachbefehl zum Auswählen eines Cubes in der Anwendung *"Select Cube"* war, der Benutzer aber eine Kugel schaute, als er den Befehl aussprach, wird stattdessen die Kugel ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="1ef32-218">For example, if the voice command for selecting a cube in your application was *"Select cube"*, but the user was looking at a sphere when they uttered the command, then the sphere would be selected instead.</span></span> <span data-ttu-id="1ef32-219">Ähnliche app-leisten Befehle sind sprach fähig.</span><span class="sxs-lookup"><span data-stu-id="1ef32-219">Similarly app bar commands are voice enabled.</span></span> <span data-ttu-id="1ef32-220">Verwenden Sie die folgenden Sprachbefehle nicht in der corewindow-Ansicht:</span><span class="sxs-lookup"><span data-stu-id="1ef32-220">Don't use the following speech commands in your CoreWindow View:</span></span>
    1. <span data-ttu-id="1ef32-221">Zurück</span><span class="sxs-lookup"><span data-stu-id="1ef32-221">Go Back</span></span>
    2. <span data-ttu-id="1ef32-222">Scrolltool</span><span class="sxs-lookup"><span data-stu-id="1ef32-222">Scroll Tool</span></span>
    3. <span data-ttu-id="1ef32-223">Zoom Tool</span><span class="sxs-lookup"><span data-stu-id="1ef32-223">Zoom Tool</span></span>
    4. <span data-ttu-id="1ef32-224">Tool ziehen</span><span class="sxs-lookup"><span data-stu-id="1ef32-224">Drag Tool</span></span>
    5. <span data-ttu-id="1ef32-225">Anpassen</span><span class="sxs-lookup"><span data-stu-id="1ef32-225">Adjust</span></span>
    6. <span data-ttu-id="1ef32-226">Entfernen</span><span class="sxs-lookup"><span data-stu-id="1ef32-226">Remove</span></span>
* <span data-ttu-id="1ef32-227">Verwenden Sie ähnliche Sounds.</span><span class="sxs-lookup"><span data-stu-id="1ef32-227">Use similar sounds.</span></span> <span data-ttu-id="1ef32-228">Versuchen Sie, die Verwendung von Sprachbefehlen zu vermeiden, die sich in der</span><span class="sxs-lookup"><span data-stu-id="1ef32-228">Try to avoid using voice commands that rhyme.</span></span> <span data-ttu-id="1ef32-229">Wenn Sie über eine Einkaufs Anwendung verfügen, in der *"Store anzeigen"* und *"mehr anzeigen"* als Sprachbefehle unterstützt werden, sollten Sie einen der Befehle deaktivieren, während der andere verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="1ef32-229">If you had a shopping application which supported *"Show Store"* and *"Show More"* as voice commands, then you would want to disable one of the commands while the other was in use.</span></span> <span data-ttu-id="1ef32-230">Beispielsweise können Sie die Schaltfläche *"Store anzeigen"* verwenden, um den Store zu öffnen, und dann diesen Befehl deaktivieren, wenn der Speicher angezeigt wird, sodass der Befehl *"Weitere anzeigen"* zum Durchsuchen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="1ef32-230">For example, you could use the *"Show Store"* button to open the store, and then disable that command when the store was displayed so that the *"Show More"* command could be used for browsing.</span></span>

### <a name="instructions"></a><span data-ttu-id="1ef32-231">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="1ef32-231">Instructions</span></span>

* <span data-ttu-id="1ef32-232">Verwenden Sie im Bereich **Hierarchie** von Unity das Suchtool, um das **holoComm_screen_mesh** -Objekt zu suchen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-232">In Unity's **Hierarchy** panel, use the search tool to find the **holoComm_screen_mesh** object.</span></span>
* <span data-ttu-id="1ef32-233">Doppelklicken Sie auf das **holoComm_screen_mesh** -Objekt, um es in der **Szene**anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-233">Double-click on the **holoComm_screen_mesh** object to view it in the **Scene**.</span></span> <span data-ttu-id="1ef32-234">Dies ist die Überwachung des Astronauten, die auf unsere Sprachbefehle antwortet.</span><span class="sxs-lookup"><span data-stu-id="1ef32-234">This is the astronaut's watch, which will respond to our voice commands.</span></span>
* <span data-ttu-id="1ef32-235">Suchen Sie im **Inspektor** -Panel die Komponente **Spracheingabe Quelle (Skript)** .</span><span class="sxs-lookup"><span data-stu-id="1ef32-235">In the **Inspector** panel, locate the **Speech Input Source (Script)** component.</span></span>
* <span data-ttu-id="1ef32-236">Erweitern Sie den Abschnitt **Schlüsselwörter** , um den unterstützten Sprachbefehl anzuzeigen: **Open Communicator**.</span><span class="sxs-lookup"><span data-stu-id="1ef32-236">Expand the **Keywords** section to see the supported voice command: **Open Communicator**.</span></span>
* <span data-ttu-id="1ef32-237">Klicken Sie rechts auf das Zahnrad Symbol, und wählen Sie **Skript bearbeiten**aus.</span><span class="sxs-lookup"><span data-stu-id="1ef32-237">Click the cog to the right side, then select **Edit Script**.</span></span>
* <span data-ttu-id="1ef32-238">Erkunden Sie **SpeechInputSource.cs** , um zu verstehen, wie das **keywordrecognizer** zum Hinzufügen von Sprachbefehlen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="1ef32-238">Explore **SpeechInputSource.cs** to understand how it uses the **KeywordRecognizer** to add voice commands.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="1ef32-239">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="1ef32-239">Build and Deploy</span></span>

* <span data-ttu-id="1ef32-240">Verwenden Sie in Unity **Datei > Buildeinstellungen** , um die Anwendung neu zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-240">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="1ef32-241">Öffnen Sie den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="1ef32-241">Open the **App** folder.</span></span>
* <span data-ttu-id="1ef32-242">Öffnen Sie die Visual Studio-Projekt Mappe **Model Explorer**.</span><span class="sxs-lookup"><span data-stu-id="1ef32-242">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="1ef32-243">(Wenn Sie dieses Projekt bereits während der Einrichtung in Visual Studio erstellt bzw. bereitgestellt haben, können Sie diese Instanz von Visual Studio öffnen und auf "alles neu laden" klicken).</span><span class="sxs-lookup"><span data-stu-id="1ef32-243">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>

* <span data-ttu-id="1ef32-244">Klicken Sie in Visual Studio auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="1ef32-244">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="1ef32-245">Nachdem die Anwendung in den hololens bereitgestellt wurde, schließen Sie das Feld anpassen mithilfe der [Tasten](gaze-and-commit.md#composite-gestures) Kombination.</span><span class="sxs-lookup"><span data-stu-id="1ef32-245">After the application deploys to the HoloLens, dismiss the fit box using the [air-tap](gaze-and-commit.md#composite-gestures) gesture.</span></span>
* <span data-ttu-id="1ef32-246">Schauen Sie sich die Überwachung des Astronauten an.</span><span class="sxs-lookup"><span data-stu-id="1ef32-246">Gaze at the astronaut's watch.</span></span>
* <span data-ttu-id="1ef32-247">Wenn die Überwachung den Fokus besitzt, überprüfen Sie, ob sich der Cursor in ein Mikrofon ändert.</span><span class="sxs-lookup"><span data-stu-id="1ef32-247">When the watch has focus, verify that the cursor changes to a microphone.</span></span> <span data-ttu-id="1ef32-248">Dadurch erhalten Sie Feedback, dass die Anwendung Sprachbefehle abhört.</span><span class="sxs-lookup"><span data-stu-id="1ef32-248">This provides feedback that the application is listening for voice commands.</span></span>
* <span data-ttu-id="1ef32-249">Vergewissern Sie sich, dass auf der Überwachung eine QuickInfo angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="1ef32-249">Verify that a tooltip appears on the watch.</span></span> <span data-ttu-id="1ef32-250">Dadurch können Benutzer den Befehl *"Open Communicator"* ermitteln.</span><span class="sxs-lookup"><span data-stu-id="1ef32-250">This helps users discover the *"Open Communicator"* command.</span></span>
* <span data-ttu-id="1ef32-251">Nehmen Sie beim Ansehen bei der Überwachung *"Open Communicator"* an, um den Communicator-Bereich zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-251">While gazing at the watch, say *"Open Communicator"* to open the communicator panel.</span></span>

## <a name="chapter-2---acknowledgement"></a><span data-ttu-id="1ef32-252">Kapitel 2: Bestätigung</span><span class="sxs-lookup"><span data-stu-id="1ef32-252">Chapter 2 - Acknowledgement</span></span>

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a><span data-ttu-id="1ef32-253">Ziele</span><span class="sxs-lookup"><span data-stu-id="1ef32-253">Objectives</span></span>

* <span data-ttu-id="1ef32-254">Aufzeichnen einer Nachricht mithilfe der Mikrofon Eingabe.</span><span class="sxs-lookup"><span data-stu-id="1ef32-254">Record a message using the Microphone input.</span></span>
* <span data-ttu-id="1ef32-255">Geben Sie dem Benutzer Feedback, dass die Anwendung seine Stimme abhört.</span><span class="sxs-lookup"><span data-stu-id="1ef32-255">Give feedback to the user that the application is listening to their voice.</span></span>

>[!NOTE]
><span data-ttu-id="1ef32-256">Die **Mikrofon** Funktion muss deklariert werden, damit eine APP vom Mikrofon aufgezeichnet werden muss.</span><span class="sxs-lookup"><span data-stu-id="1ef32-256">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="1ef32-257">Dies erfolgt bereits in der Mr-Eingabe 212, aber beachten Sie dies für Ihre eigenen Projekte.</span><span class="sxs-lookup"><span data-stu-id="1ef32-257">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="1ef32-258">Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zu "> Projekteinstellungen bearbeiten > Player" navigieren.</span><span class="sxs-lookup"><span data-stu-id="1ef32-258">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="1ef32-259">Klicken Sie auf die Registerkarte "universelle Windows-Plattform".</span><span class="sxs-lookup"><span data-stu-id="1ef32-259">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="1ef32-260">Aktivieren Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die **Mikrofon** Funktion.</span><span class="sxs-lookup"><span data-stu-id="1ef32-260">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="1ef32-261">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="1ef32-261">Instructions</span></span>

* <span data-ttu-id="1ef32-262">Überprüfen Sie im Bereich **Hierarchie** der Unity, ob das **holoComm_screen_mesh** -Objekt ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="1ef32-262">In Unity's **Hierarchy** panel, verify that the **holoComm_screen_mesh** object is selected.</span></span>
* <span data-ttu-id="1ef32-263">Suchen Sie im **Inspektor** -Panel nach der Komponente " **Astronauten Überwachung (Skript)** ".</span><span class="sxs-lookup"><span data-stu-id="1ef32-263">In the **Inspector** panel, find the **Astronaut Watch (Script)** component.</span></span>
* <span data-ttu-id="1ef32-264">Klicken Sie auf den kleinen, blauen Cube, der als Wert der **Communicator Prefab** -Eigenschaft festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="1ef32-264">Click on the small, blue cube which is set as the value of the **Communicator Prefab** property.</span></span>
* <span data-ttu-id="1ef32-265">Im **Projekt** Panel sollte die **Communicator** -vorfab jetzt den Fokus haben.</span><span class="sxs-lookup"><span data-stu-id="1ef32-265">In the **Project** panel, the **Communicator** prefab should now have focus.</span></span>
* <span data-ttu-id="1ef32-266">Klicken Sie im **Projekt** Panel auf die **Communicator** -vorfab, um die zugehörigen Komponenten im **Inspektor**anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-266">Click on the **Communicator** prefab in the **Project** panel to view its components in the **Inspector**.</span></span>
* <span data-ttu-id="1ef32-267">Sehen Sie sich die Komponente " **Mikrofon-Manager (Skript)** " an, damit wir die Stimme des Benutzers aufzeichnen können.</span><span class="sxs-lookup"><span data-stu-id="1ef32-267">Look at the **Microphone Manager (Script)** component, this will allow us to record the user's voice.</span></span>
* <span data-ttu-id="1ef32-268">Beachten Sie, dass das **Communicator** -Objekt über eine **Spracheingabe Handler-Komponente (Skript)** für die Antwort auf den Befehl " **Nachricht senden** " verfügt.</span><span class="sxs-lookup"><span data-stu-id="1ef32-268">Notice that the **Communicator** object has a **Speech Input Handler (Script)** component for responding to the **Send Message** command.</span></span>
* <span data-ttu-id="1ef32-269">Sehen Sie sich die **Communicator (Script)** -Komponente an, und doppelklicken Sie auf das Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-269">Look at the **Communicator (Script)** component and double-click on the script to open it in Visual Studio.</span></span>

<span data-ttu-id="1ef32-270">Communicator.cs ist dafür verantwortlich, die richtigen Schaltflächen Zustände auf dem Communicator-Gerät festzulegen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-270">Communicator.cs is responsible for setting the proper button states on the communicator device.</span></span> <span data-ttu-id="1ef32-271">Dies ermöglicht es unseren Benutzern, eine Nachricht aufzuzeichnen, wieder abzuspielen und die Nachricht an den Astronauten zu senden.</span><span class="sxs-lookup"><span data-stu-id="1ef32-271">This will allow our users to record a message, play it back, and send the message to the astronaut.</span></span> <span data-ttu-id="1ef32-272">Außerdem wird ein animiertes Wellen Formular gestartet und angehalten, um dem Benutzer zu bestätigen, dass seine Stimme gehört.</span><span class="sxs-lookup"><span data-stu-id="1ef32-272">It will also start and stop an animated wave form, to acknowledge to the user that their voice was heard.</span></span>

* <span data-ttu-id="1ef32-273">Löschen Sie in **Communicator.cs**die folgenden Zeilen (81 und 82) aus der **Start** -Methode.</span><span class="sxs-lookup"><span data-stu-id="1ef32-273">In **Communicator.cs**, delete the following lines (81 and 82) from the **Start** method.</span></span> <span data-ttu-id="1ef32-274">Dadurch wird die Schaltfläche "Record" auf dem Communicator aktiviert.</span><span class="sxs-lookup"><span data-stu-id="1ef32-274">This will enable the 'Record' button on the communicator.</span></span>

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a><span data-ttu-id="1ef32-275">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="1ef32-275">Build and Deploy</span></span>

* <span data-ttu-id="1ef32-276">Erstellen Sie in Visual Studio die Anwendung neu, und stellen Sie Sie auf dem Gerät bereit.</span><span class="sxs-lookup"><span data-stu-id="1ef32-276">In Visual Studio, rebuild your application and deploy to the device.</span></span>
* <span data-ttu-id="1ef32-277">Schauen Sie sich die Überwachung des Astronauten an, und sagen Sie *"Open Communicator"* , um den Communicator anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-277">Gaze at the astronaut's watch and say *"Open Communicator"* to show the communicator.</span></span>
* <span data-ttu-id="1ef32-278">Klicken Sie auf die Schaltfläche " **Record** " (Mikrofon), um die Aufzeichnung einer verbalen Nachricht für den Astronauten zu starten</span><span class="sxs-lookup"><span data-stu-id="1ef32-278">Press the **Record** button (microphone) to start recording a verbal message for the astronaut.</span></span>
* <span data-ttu-id="1ef32-279">Beginnen Sie mit dem Gespräch, und überprüfen Sie, ob die Wave-Animation auf dem Communicator abgespielt wird, der dem Benutzer Feedback zur Verfügung stellt, dass Ihre Stimme gehört.</span><span class="sxs-lookup"><span data-stu-id="1ef32-279">Start speaking, and verify that the wave animation plays on the communicator, which provides feedback to the user that their voice is heard.</span></span>
* <span data-ttu-id="1ef32-280">Klicken Sie auf die Schaltfläche **Beenden** (linkes Quadrat), und überprüfen Sie, ob die Wave-Animation beendet wird.</span><span class="sxs-lookup"><span data-stu-id="1ef32-280">Press the **Stop** button (left square), and verify that the wave animation stops running.</span></span>
* <span data-ttu-id="1ef32-281">Drücken Sie die **Wiedergabe** Schaltfläche (Rechts Dreieck), um die aufgezeichnete Nachricht wiederzugeben und auf dem Gerät zu hören.</span><span class="sxs-lookup"><span data-stu-id="1ef32-281">Press the **Play** button (right triangle) to play back the recorded message and hear it on the device.</span></span>
* <span data-ttu-id="1ef32-282">Klicken Sie auf die Schaltfläche zum **Abbrechen** (rechts Quadrat), um die Wiedergabe der aufgezeichneten Nachricht zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="1ef32-282">Press the **Stop** button (right square) to stop playback of the recorded message.</span></span>
* <span data-ttu-id="1ef32-283">Sagen *Sie "Nachricht senden"* , um den Communicator zu schließen und die Antwort "Nachricht empfangen" vom Astronauten zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-283">Say *"Send Message"* to close the communicator and receive a 'Message Received' response from the astronaut.</span></span>

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a><span data-ttu-id="1ef32-284">Kapitel 3: verstehen und der Diktat Erkennung</span><span class="sxs-lookup"><span data-stu-id="1ef32-284">Chapter 3 - Understanding and the Dictation Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a><span data-ttu-id="1ef32-285">Ziele</span><span class="sxs-lookup"><span data-stu-id="1ef32-285">Objectives</span></span>

* <span data-ttu-id="1ef32-286">Verwenden Sie die Diktat Erkennung, um die Sprache des Benutzers in Text zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="1ef32-286">Use the Dictation Recognizer to convert the user's speech to text.</span></span>
* <span data-ttu-id="1ef32-287">Zeigen Sie die hypothetisierungserkenfizierung hypothetische und abschließende Ergebnisse in Communicator an.</span><span class="sxs-lookup"><span data-stu-id="1ef32-287">Show the Dictation Recognizer's hypothesized and final results in the communicator.</span></span>

<span data-ttu-id="1ef32-288">In diesem Kapitel verwenden wir die Diktat Erkennung, um eine Nachricht für den Astronaut zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-288">In this chapter, we'll use the Dictation Recognizer to create a message for the astronaut.</span></span> <span data-ttu-id="1ef32-289">Beachten Sie beim Verwenden der Diktat Erkennung Folgendes:</span><span class="sxs-lookup"><span data-stu-id="1ef32-289">When using the Dictation Recognizer, keep in mind that:</span></span>

* <span data-ttu-id="1ef32-290">Sie müssen mit WiFi verbunden sein, damit die Diktat Erkennung funktioniert.</span><span class="sxs-lookup"><span data-stu-id="1ef32-290">You must be connected to WiFi for the Dictation Recognizer to work.</span></span>
* <span data-ttu-id="1ef32-291">Timeouts treten nach einer festgelegten Zeitspanne auf.</span><span class="sxs-lookup"><span data-stu-id="1ef32-291">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="1ef32-292">Es gibt zwei Timeouts, die Sie beachten sollten:</span><span class="sxs-lookup"><span data-stu-id="1ef32-292">There are two timeouts to be aware of:</span></span>
  * <span data-ttu-id="1ef32-293">Wenn die Erkennung startet und keine Audiodaten für die ersten fünf Sekunden hört, wird ein Timeout angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1ef32-293">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
  * <span data-ttu-id="1ef32-294">Wenn die Erkennung ein Ergebnis erhalten hat, dann aber für einen Zeitraum von 20 Sekunden den Ruhe Wert erfährt, wird ein Timeout verursacht.</span><span class="sxs-lookup"><span data-stu-id="1ef32-294">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>
* <span data-ttu-id="1ef32-295">Es kann jeweils nur ein Erkennungs Funktionstyp (Schlüsselwort oder Diktat) ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="1ef32-295">Only one type of recognizer (Keyword or Dictation) can run at a time.</span></span>

>[!NOTE]
><span data-ttu-id="1ef32-296">Die **Mikrofon** Funktion muss deklariert werden, damit eine APP vom Mikrofon aufgezeichnet werden muss.</span><span class="sxs-lookup"><span data-stu-id="1ef32-296">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="1ef32-297">Dies erfolgt bereits in der Mr-Eingabe 212, aber beachten Sie dies für Ihre eigenen Projekte.</span><span class="sxs-lookup"><span data-stu-id="1ef32-297">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="1ef32-298">Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zu "> Projekteinstellungen bearbeiten > Player" navigieren.</span><span class="sxs-lookup"><span data-stu-id="1ef32-298">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="1ef32-299">Klicken Sie auf die Registerkarte "universelle Windows-Plattform".</span><span class="sxs-lookup"><span data-stu-id="1ef32-299">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="1ef32-300">Aktivieren Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die **Mikrofon** Funktion.</span><span class="sxs-lookup"><span data-stu-id="1ef32-300">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="1ef32-301">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="1ef32-301">Instructions</span></span>

<span data-ttu-id="1ef32-302">Wir werden **MicrophoneManager.cs** bearbeiten, um die Diktat Erkennung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="1ef32-302">We're going to edit **MicrophoneManager.cs** to use the Dictation Recognizer.</span></span> <span data-ttu-id="1ef32-303">Dies fügen wir hinzu:</span><span class="sxs-lookup"><span data-stu-id="1ef32-303">This is what we'll add:</span></span>

1. <span data-ttu-id="1ef32-304">Wenn die **Schaltfläche "Datensatz** " gedrückt ist, **starten wir das "diktationerkenzer**".</span><span class="sxs-lookup"><span data-stu-id="1ef32-304">When the **Record button** is pressed, we'll **start the DictationRecognizer**.</span></span>
2. <span data-ttu-id="1ef32-305">Zeigen Sie die **Hypothese** an, was der diktationerkenzer verstanden hat.</span><span class="sxs-lookup"><span data-stu-id="1ef32-305">Show the **hypothesis** of what the DictationRecognizer understood.</span></span>
3. <span data-ttu-id="1ef32-306">Lock in den **Ergebnissen** der von der diktationerkenzer erkannten Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="1ef32-306">Lock in the **results** of what the DictationRecognizer understood.</span></span>
4. <span data-ttu-id="1ef32-307">Überprüfen Sie, ob Timeouts von der "diktationerkenzer".</span><span class="sxs-lookup"><span data-stu-id="1ef32-307">Check for timeouts from the DictationRecognizer.</span></span>
5. <span data-ttu-id="1ef32-308">Wenn die **Schaltfläche "beenden** " gedrückt wird oder bei der MIC-Sitzung ein Timeout auftritt, **Beenden Sie das "diktationerkenzer**".</span><span class="sxs-lookup"><span data-stu-id="1ef32-308">When the **Stop button** is pressed, or the mic session times out, **stop the DictationRecognizer**.</span></span>
6. <span data-ttu-id="1ef32-309">Starten Sie den **keywordrecognizer**neu, der auf den Befehl " **Nachricht senden** " lauscht.</span><span class="sxs-lookup"><span data-stu-id="1ef32-309">Restart the **KeywordRecognizer**, which will listen for the **Send Message** command.</span></span>

<span data-ttu-id="1ef32-310">Los geht's.</span><span class="sxs-lookup"><span data-stu-id="1ef32-310">Let's get started.</span></span> <span data-ttu-id="1ef32-311">Vervollständigen Sie alle Codierungs Übungen für 3. a in **MicrophoneManager.cs**, oder kopieren Sie den unten stehenden Code, und fügen Sie ihn ein:</span><span class="sxs-lookup"><span data-stu-id="1ef32-311">Complete all coding exercises for 3.a in **MicrophoneManager.cs**, or copy and paste the finished code found below:</span></span>

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

### <a name="build-and-deploy"></a><span data-ttu-id="1ef32-312">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="1ef32-312">Build and Deploy</span></span>

* <span data-ttu-id="1ef32-313">Erstellen Sie in Visual Studio neu, und stellen Sie auf Ihrem Gerät bereit.</span><span class="sxs-lookup"><span data-stu-id="1ef32-313">Rebuild in Visual Studio and deploy to your device.</span></span>
* <span data-ttu-id="1ef32-314">Schließen Sie das Feld "anpassen" mit einer Tastenkombination.</span><span class="sxs-lookup"><span data-stu-id="1ef32-314">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="1ef32-315">Schauen Sie sich die Überwachung des Astronauten an, und sagen Sie *"Open Communicator"* .</span><span class="sxs-lookup"><span data-stu-id="1ef32-315">Gaze at the astronaut's watch and say *"Open Communicator"*.</span></span>
* <span data-ttu-id="1ef32-316">Wählen Sie die Schaltfläche **Datensatz** (Mikrofon) aus, um Ihre Nachricht aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-316">Select the **Record** button (microphone) to record your message.</span></span>
* <span data-ttu-id="1ef32-317">Beginnen Sie den Einstieg.</span><span class="sxs-lookup"><span data-stu-id="1ef32-317">Start speaking.</span></span> <span data-ttu-id="1ef32-318">Die **Diktat Erkennung** interpretiert Ihre Sprache und zeigt den Text mit hypothetischer Größe in Communicator an.</span><span class="sxs-lookup"><span data-stu-id="1ef32-318">The **Dictation Recognizer** will interpret your speech and show the hypothesized text in the communicator.</span></span>
* <span data-ttu-id="1ef32-319">Versuchen Sie, *"Nachricht senden"* zu sagen, während Sie eine Nachricht aufzeichnen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-319">Try saying *"Send Message"* while you are recording a message.</span></span> <span data-ttu-id="1ef32-320">Beachten Sie, dass die **Schlüsselwort Erkennung** nicht antwortet, weil die **Diktat Erkennung** noch aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="1ef32-320">Notice that the **Keyword Recognizer** does not respond because the **Dictation Recognizer** is still active.</span></span>
* <span data-ttu-id="1ef32-321">Sprechen Sie einige Sekunden lang nicht mehr.</span><span class="sxs-lookup"><span data-stu-id="1ef32-321">Stop speaking for a few seconds.</span></span> <span data-ttu-id="1ef32-322">Sehen Sie sich an, wie die Diktat Erkennung die Hypothese abschließt und das Endergebnis anzeigt.</span><span class="sxs-lookup"><span data-stu-id="1ef32-322">Watch as the Dictation Recognizer completes its hypothesis and shows the final result.</span></span>
* <span data-ttu-id="1ef32-323">Beginnen Sie mit der Sprachverarbeitung, und halten Sie dann 20 Sekunden an</span><span class="sxs-lookup"><span data-stu-id="1ef32-323">Begin speaking and then pause for 20 seconds.</span></span> <span data-ttu-id="1ef32-324">Dies führt dazu, dass die **diktierungerkenfizierung** ein Timeout verursacht.</span><span class="sxs-lookup"><span data-stu-id="1ef32-324">This will cause the **Dictation Recognizer** to timeout.</span></span>
* <span data-ttu-id="1ef32-325">Beachten Sie, dass die **Schlüsselwort Erkennung** nach dem obigen Timeout erneut aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="1ef32-325">Notice that the **Keyword Recognizer** is re-enabled after the above timeout.</span></span> <span data-ttu-id="1ef32-326">Der Communicator antwortet nun auf Sprachbefehle.</span><span class="sxs-lookup"><span data-stu-id="1ef32-326">The communicator will now respond to voice commands.</span></span>
* <span data-ttu-id="1ef32-327">Sagen Sie *"Nachricht senden"* , um die Nachricht an den Astronaut zu senden.</span><span class="sxs-lookup"><span data-stu-id="1ef32-327">Say *"Send Message"* to send the message to the astronaut.</span></span>

## <a name="chapter-4---grammar-recognizer"></a><span data-ttu-id="1ef32-328">Kapitel 4: Grammatik Erkennung</span><span class="sxs-lookup"><span data-stu-id="1ef32-328">Chapter 4 - Grammar Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a><span data-ttu-id="1ef32-329">Ziele</span><span class="sxs-lookup"><span data-stu-id="1ef32-329">Objectives</span></span>

* <span data-ttu-id="1ef32-330">Verwenden Sie die Grammatik Erkennung, um die Sprache des Benutzers gemäß einer SRGS-oder Spracherkennungs-Grammatik Spezifikation zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-330">Use the Grammar Recognizer to recognize the user's speech according to an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

>[!NOTE]
><span data-ttu-id="1ef32-331">Die **Mikrofon** Funktion muss deklariert werden, damit eine APP vom Mikrofon aufgezeichnet werden muss.</span><span class="sxs-lookup"><span data-stu-id="1ef32-331">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="1ef32-332">Dies erfolgt bereits in der Mr-Eingabe 212, aber beachten Sie dies für Ihre eigenen Projekte.</span><span class="sxs-lookup"><span data-stu-id="1ef32-332">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="1ef32-333">Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zu "> Projekteinstellungen bearbeiten > Player" navigieren.</span><span class="sxs-lookup"><span data-stu-id="1ef32-333">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="1ef32-334">Klicken Sie auf die Registerkarte "universelle Windows-Plattform".</span><span class="sxs-lookup"><span data-stu-id="1ef32-334">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="1ef32-335">Aktivieren Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die **Mikrofon** Funktion.</span><span class="sxs-lookup"><span data-stu-id="1ef32-335">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="1ef32-336">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="1ef32-336">Instructions</span></span>

1. <span data-ttu-id="1ef32-337">Suchen Sie im **Hierarchie** Panel nach **Jetpack_Center** , und wählen Sie es aus.</span><span class="sxs-lookup"><span data-stu-id="1ef32-337">In the **Hierarchy** panel, search for **Jetpack_Center** and select it.</span></span>
2. <span data-ttu-id="1ef32-338">Suchen Sie im **Inspektor** -Panel nach dem Skript " **Tagalong Action** ".</span><span class="sxs-lookup"><span data-stu-id="1ef32-338">Look for the **Tagalong Action** script in the **Inspector** panel.</span></span>
3. <span data-ttu-id="1ef32-339">Klicken Sie rechts neben dem Feld **zu tagendes Objekt auf** den kleinen Kreis.</span><span class="sxs-lookup"><span data-stu-id="1ef32-339">Click the little circle to the right of the **Object To Tag Along** field.</span></span>
4. <span data-ttu-id="1ef32-340">Suchen Sie im Fenster, das angezeigt wird, nach **srgstoolbox** , und wählen Sie es aus der Liste aus.</span><span class="sxs-lookup"><span data-stu-id="1ef32-340">In the window that pops up, search for **SRGSToolbox** and select it from the list.</span></span>
5. <span data-ttu-id="1ef32-341">Sehen Sie sich die Datei " **srgscolor. XML** " im Ordner " **streamingassets** " an.</span><span class="sxs-lookup"><span data-stu-id="1ef32-341">Take a look at the **SRGSColor.xml** file in the **StreamingAssets** folder.</span></span>
    1. <span data-ttu-id="1ef32-342">Die SRGS-Entwurfs Spezifikation finden Sie [hier](https://www.w3.org/TR/speech-grammar/)auf der W3C-Website.</span><span class="sxs-lookup"><span data-stu-id="1ef32-342">The SRGS design spec can be found on the W3C website [here](https://www.w3.org/TR/speech-grammar/).</span></span>

<span data-ttu-id="1ef32-343">In der SRGS-Datei gibt es drei Arten von Regeln:</span><span class="sxs-lookup"><span data-stu-id="1ef32-343">In our SRGS file, we have three types of rules:</span></span>

* <span data-ttu-id="1ef32-344">Eine Regel, mit der Sie eine Farbe aus einer Liste von zwölf Farben sagen können.</span><span class="sxs-lookup"><span data-stu-id="1ef32-344">A rule which lets you say one color from a list of twelve colors.</span></span>
* <span data-ttu-id="1ef32-345">Drei Regeln, die auf eine Kombination der Farbregel und einer der drei Formen lauschen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-345">Three rules which listen for a combination of the color rule and one of the three shapes.</span></span>
* <span data-ttu-id="1ef32-346">Die Stamm Regel colorchooser, die auf eine beliebige Kombination der drei "Color + Shape"-Regeln lauscht.</span><span class="sxs-lookup"><span data-stu-id="1ef32-346">The root rule, colorChooser, which listens for any combination of the three "color + shape" rules.</span></span> <span data-ttu-id="1ef32-347">Die Formen können in beliebiger Reihenfolge und in beliebiger Reihenfolge von nur einem bis zu allen drei Formen bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="1ef32-347">The shapes can be said in any order and in any amount from just one to all three.</span></span> <span data-ttu-id="1ef32-348">Dies ist die einzige Regel, die überwacht wird, da Sie als Stamm Regel am Anfang der Datei in der ersten &lt;Grammatik&gt;-Tags angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="1ef32-348">This is the only rule that is listened for, as it's specified as the root rule at the top of the file in the initial &lt;grammar&gt; tag.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="1ef32-349">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="1ef32-349">Build and Deploy</span></span>

* <span data-ttu-id="1ef32-350">Erstellen Sie die Anwendung in Unity neu, erstellen Sie Sie in Visual Studio, und stellen Sie Sie bereit, um die APP auf hololens zu erleben</span><span class="sxs-lookup"><span data-stu-id="1ef32-350">Rebuild the application in Unity, then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="1ef32-351">Schließen Sie das Feld "anpassen" mit einer Tastenkombination.</span><span class="sxs-lookup"><span data-stu-id="1ef32-351">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="1ef32-352">Schauen Sie sich das Jetpack des Astronauten an, und führen Sie eine Luft tippen Bewegung aus.</span><span class="sxs-lookup"><span data-stu-id="1ef32-352">Gaze at the astronaut's jetpack and perform an air-tap gesture.</span></span>
* <span data-ttu-id="1ef32-353">Beginnen Sie den Einstieg.</span><span class="sxs-lookup"><span data-stu-id="1ef32-353">Start speaking.</span></span> <span data-ttu-id="1ef32-354">Die **Grammatik Erkennung** interpretiert Ihre Sprache und ändert die Farben der Formen basierend auf der Erkennung.</span><span class="sxs-lookup"><span data-stu-id="1ef32-354">The **Grammar Recognizer** will interpret your speech and change the colors of the shapes based on the recognition.</span></span> <span data-ttu-id="1ef32-355">Ein Beispiel Befehl ist "blauer Kreis, gelbes Quadrat".</span><span class="sxs-lookup"><span data-stu-id="1ef32-355">An example command is "blue circle, yellow square".</span></span>
* <span data-ttu-id="1ef32-356">Führen Sie eine weitere Luft tippen Bewegung aus, um die Toolbox zu schließen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-356">Perform another air-tap gesture to dismiss the toolbox.</span></span>

## <a name="the-end"></a><span data-ttu-id="1ef32-357">Das Ende</span><span class="sxs-lookup"><span data-stu-id="1ef32-357">The End</span></span>

<span data-ttu-id="1ef32-358">Gratulation!</span><span class="sxs-lookup"><span data-stu-id="1ef32-358">Congratulations!</span></span> <span data-ttu-id="1ef32-359">Nun haben Sie die **Mr-Eingabe 212: Voice**abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-359">You have now completed **MR Input 212: Voice**.</span></span>

* <span data-ttu-id="1ef32-360">Sie kennen die DOS-und die TS von Voice-Befehlen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-360">You know the Dos and Don'ts of voice commands.</span></span>
* <span data-ttu-id="1ef32-361">Sie haben gesehen, wie Quick Infos verwendet wurden, um die Benutzer auf Sprachbefehle aufmerksam zu machen.</span><span class="sxs-lookup"><span data-stu-id="1ef32-361">You saw how tooltips were employed to make users aware of voice commands.</span></span>
* <span data-ttu-id="1ef32-362">Sie haben verschiedene Feedback Typen verwendet, um zu bestätigen, dass die Stimme des Benutzers gehört.</span><span class="sxs-lookup"><span data-stu-id="1ef32-362">You saw several types of feedback used to acknowledge that the user's voice was heard.</span></span>
* <span data-ttu-id="1ef32-363">Sie wissen, wie Sie zwischen der Schlüsselwort Erkennung und der Diktat Erkennung wechseln und wie diese beiden Features Ihre Stimme verstehen und interpretieren.</span><span class="sxs-lookup"><span data-stu-id="1ef32-363">You know how to switch between the Keyword Recognizer and the Dictation Recognizer, and how these two features understand and interpret your voice.</span></span>
* <span data-ttu-id="1ef32-364">Sie haben gelernt, wie Sie eine SRGS-Datei und die Grammatik Erkennung für die Spracherkennung in Ihrer Anwendung verwenden.</span><span class="sxs-lookup"><span data-stu-id="1ef32-364">You learned how to use an SRGS file and the Grammar Recognizer for speech recognition in your application.</span></span>
