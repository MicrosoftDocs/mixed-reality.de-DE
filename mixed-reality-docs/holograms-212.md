---
title: Mr-Eingabe 212-Stimme
description: Befolgen Sie diese exemplarische Vorgehensweise, indem Sie Unity, Visual Studio und hololens verwenden, um die Details der sprach Konzepte zu erlernen.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, Tutorial, Stimme
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522352"
---
>[!NOTE]
><span data-ttu-id="82ca4-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="82ca4-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="82ca4-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="82ca4-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="82ca4-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="82ca4-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="82ca4-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="82ca4-108">Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="82ca4-109">Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="82ca4-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-212-voice"></a><span data-ttu-id="82ca4-110">Mr-Eingabe 212: Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="82ca4-110">MR Input 212: Voice</span></span>

<span data-ttu-id="82ca4-111">Die [Spracheingabe](voice-input.md) bietet uns eine weitere Möglichkeit, mit unseren holograms zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="82ca4-111">[Voice input](voice-input.md) gives us another way to interact with our holograms.</span></span> <span data-ttu-id="82ca4-112">Sprachbefehle funktionieren auf sehr natürliche und einfache Weise.</span><span class="sxs-lookup"><span data-stu-id="82ca4-112">Voice commands work in a very natural and easy way.</span></span> <span data-ttu-id="82ca4-113">Entwerfen Sie Ihre Sprachbefehle so, dass Sie wie folgt lauten:</span><span class="sxs-lookup"><span data-stu-id="82ca4-113">Design your voice commands so that they are:</span></span>

* <span data-ttu-id="82ca4-114">Natürliche</span><span class="sxs-lookup"><span data-stu-id="82ca4-114">Natural</span></span>
* <span data-ttu-id="82ca4-115">Leicht zu merken</span><span class="sxs-lookup"><span data-stu-id="82ca4-115">Easy to remember</span></span>
* <span data-ttu-id="82ca4-116">Geeigneter Kontext</span><span class="sxs-lookup"><span data-stu-id="82ca4-116">Context appropriate</span></span>
* <span data-ttu-id="82ca4-117">Ausreichend Unterschied zu anderen Optionen innerhalb desselben Kontexts</span><span class="sxs-lookup"><span data-stu-id="82ca4-117">Sufficiently distinct from other options within the same context</span></span>

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

<span data-ttu-id="82ca4-118">In den [Grundlagen 101](holograms-101.md)haben wir keywordrecognizer verwendet, um zwei einfache Sprachbefehle zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-118">In [MR Basics 101](holograms-101.md), we used the KeywordRecognizer to build two simple voice commands.</span></span> <span data-ttu-id="82ca4-119">In der Eingabe 212 gehen wir genauer vor und lernen, wie Sie:</span><span class="sxs-lookup"><span data-stu-id="82ca4-119">In MR Input 212, we'll dive deeper and learn how to:</span></span>

* <span data-ttu-id="82ca4-120">Entwerfen Sie Sprachbefehle, die für die hololens-Sprach-Engine optimiert sind.</span><span class="sxs-lookup"><span data-stu-id="82ca4-120">Design voice commands that are optimized for the HoloLens speech engine.</span></span>
* <span data-ttu-id="82ca4-121">Sorgen Sie dafür, dass der Benutzer weiß, welche Sprachbefehle verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="82ca4-121">Make the user aware of what voice commands are available.</span></span>
* <span data-ttu-id="82ca4-122">Bestätigen Sie, dass der Sprachbefehl des Benutzers gehört.</span><span class="sxs-lookup"><span data-stu-id="82ca4-122">Acknowledge that we've heard the user's voice command.</span></span>
* <span data-ttu-id="82ca4-123">Verstehen Sie, was der Benutzer sagt, mithilfe einer Diktat Erkennung.</span><span class="sxs-lookup"><span data-stu-id="82ca4-123">Understand what the user is saying, using a Dictation Recognizer.</span></span>
* <span data-ttu-id="82ca4-124">Verwenden Sie eine Grammatik Erkennung, um Befehle auf der Grundlage einer SRGS-oder Spracherkennungs-Grammatik Spezifikation (File) abzuhören.</span><span class="sxs-lookup"><span data-stu-id="82ca4-124">Use a Grammar Recognizer to listen for commands based on an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

<span data-ttu-id="82ca4-125">In diesem Kurs überprüfen wir den Modell-Explorer, den wir in der [Eingabe 210](holograms-210.md) und in der [Eingabe 211](holograms-211.md)von Mr erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="82ca4-125">In this course, we'll revisit Model Explorer, which we built in [MR Input 210](holograms-210.md) and [MR Input 211](holograms-211.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="82ca4-126">Die in den folgenden Kapiteln eingebetteten Videos wurden mit einer älteren Version von Unity und dem Mixed Reality Toolkit aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="82ca4-126">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="82ca4-127">Die Schritt-für-Schritt-Anweisungen sind genau und aktuell, aber es werden möglicherweise Skripts und Visualisierungen in den entsprechenden Videos angezeigt, die veraltet sind.</span><span class="sxs-lookup"><span data-stu-id="82ca4-127">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="82ca4-128">Die Videos bleiben in der einwelt enthalten und werden weiterhin angewendet.</span><span class="sxs-lookup"><span data-stu-id="82ca4-128">The videos remain included for posterity and because the concepts covered still apply.</span></span>


## <a name="device-support"></a><span data-ttu-id="82ca4-129">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="82ca4-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="82ca4-130">Natürlich</span><span class="sxs-lookup"><span data-stu-id="82ca4-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="82ca4-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="82ca4-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="82ca4-132"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="82ca4-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="82ca4-133">Mr-Eingabe 212: Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="82ca4-133">MR Input 212: Voice</span></span></td><td style="text-align: center;"> <span data-ttu-id="82ca4-134">✔️</span><span class="sxs-lookup"><span data-stu-id="82ca4-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="82ca4-135">✔️</span><span class="sxs-lookup"><span data-stu-id="82ca4-135">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="82ca4-136">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="82ca4-136">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="82ca4-137">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="82ca4-137">Prerequisites</span></span>

* <span data-ttu-id="82ca4-138">Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md)konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="82ca4-138">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="82ca4-139">Einige Grund C# Legende Programmiermöglichkeiten.</span><span class="sxs-lookup"><span data-stu-id="82ca4-139">Some basic C# programming ability.</span></span>
* <span data-ttu-id="82ca4-140">Sie sollten die [Grundlagen von 101](holograms-101.md)abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="82ca4-140">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="82ca4-141">Sie sollten die [Mr-Eingabe 210](holograms-210.md)abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="82ca4-141">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="82ca4-142">Sie sollten die [Mr-Eingabe 211](holograms-211.md)abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="82ca4-142">You should have completed [MR Input 211](holograms-211.md).</span></span>
* <span data-ttu-id="82ca4-143">Ein hololens-Gerät, das [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode)ist.</span><span class="sxs-lookup"><span data-stu-id="82ca4-143">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="82ca4-144">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="82ca4-144">Project files</span></span>

* <span data-ttu-id="82ca4-145">Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) , die für das Projekt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="82ca4-145">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) required by the project.</span></span> <span data-ttu-id="82ca4-146">Erfordert Unity 2017,2 oder höher.</span><span class="sxs-lookup"><span data-stu-id="82ca4-146">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="82ca4-147">Deinstallieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht zugänglichen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="82ca4-147">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="82ca4-148">Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span><span class="sxs-lookup"><span data-stu-id="82ca4-148">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="82ca4-149">Errata und Notizen</span><span class="sxs-lookup"><span data-stu-id="82ca4-149">Errata and Notes</span></span>

* <span data-ttu-id="82ca4-150">"Enable nur eigenen Code" muss in Visual Studio unter "Extras-> Optionen" deaktiviert*werden (>* Debuggen, um Breakpoints im Code zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-150">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="82ca4-151">Unity-Setup</span><span class="sxs-lookup"><span data-stu-id="82ca4-151">Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="82ca4-152">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="82ca4-152">Instructions</span></span>

1. <span data-ttu-id="82ca4-153">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="82ca4-153">Start Unity.</span></span>
2. <span data-ttu-id="82ca4-154">Wählen Sie **Öffnen**aus.</span><span class="sxs-lookup"><span data-stu-id="82ca4-154">Select **Open**.</span></span>
3. <span data-ttu-id="82ca4-155">Navigieren Sie zum Ordner **holographicacademy-holograms-212-Voice** , den Sie zuvor nicht archiviert haben.</span><span class="sxs-lookup"><span data-stu-id="82ca4-155">Navigate to the **HolographicAcademy-Holograms-212-Voice** folder you previously un-archived.</span></span>
4. <span data-ttu-id="82ca4-156">Suchen und wählen Sie den **Start**/**Modell-Explorer** -Ordner aus.</span><span class="sxs-lookup"><span data-stu-id="82ca4-156">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="82ca4-157">Klicken Sie auf die Schaltfläche **Ordner auswählen** .</span><span class="sxs-lookup"><span data-stu-id="82ca4-157">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="82ca4-158">Erweitern Sie im **Projekt** Panel den Ordner **Szenen** .</span><span class="sxs-lookup"><span data-stu-id="82ca4-158">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="82ca4-159">Doppelklicken Sie auf **Model Explorer** Scene, um es in Unity zu laden.</span><span class="sxs-lookup"><span data-stu-id="82ca4-159">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="82ca4-160">Erstellung</span><span class="sxs-lookup"><span data-stu-id="82ca4-160">Building</span></span>

1. <span data-ttu-id="82ca4-161">Wählen Sie in Unity **Datei >** Buildeinstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="82ca4-161">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="82ca4-162">Wenn **Szenen/Model Explorer** nicht in **Szenen im Build**aufgeführt ist, klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-162">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="82ca4-163">Wenn Sie speziell für hololens entwickeln, legen Sie **Zielgerät** auf **hololens**fest.</span><span class="sxs-lookup"><span data-stu-id="82ca4-163">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="82ca4-164">Andernfalls sollten Sie es auf **jedem Gerät**belassen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-164">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="82ca4-165">Stellen  Sie sicher, dass der Buildtyp auf **D3D** und das **SDK** auf **Latest installiert** festgelegt ist (was SDK 16299 oder höher sein sollte).</span><span class="sxs-lookup"><span data-stu-id="82ca4-165">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="82ca4-166">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="82ca4-166">Click **Build**.</span></span>
6. <span data-ttu-id="82ca4-167">Erstellen Sie einen **neuen Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="82ca4-167">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="82ca4-168">Klicken Sie einfach auf den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="82ca4-168">Single click the **App** folder.</span></span>
8. <span data-ttu-id="82ca4-169">Klicken **Sie auf Ordner auswählen** , und Unity startet das Projekt für Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="82ca4-169">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="82ca4-170">Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="82ca4-170">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="82ca4-171">Öffnen Sie den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="82ca4-171">Open the **App** folder.</span></span>
2. <span data-ttu-id="82ca4-172">Öffnen Sie die Visual Studio-Projekt Mappe **Model Explorer**.</span><span class="sxs-lookup"><span data-stu-id="82ca4-172">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="82ca4-173">Bei der Bereitstellung in hololens:</span><span class="sxs-lookup"><span data-stu-id="82ca4-173">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="82ca4-174">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x86**.</span><span class="sxs-lookup"><span data-stu-id="82ca4-174">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="82ca4-175">Klicken Sie auf den Dropdown Pfeil neben der Schaltfläche lokaler Computer, und wählen Sie **Remote Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="82ca4-175">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="82ca4-176">Geben Sie **die IP-Adresse des hololens-Geräts** ein, und legen Sie den Authentifizierungsmodus auf **Universal (unverschlüsseltes Protokoll)**</span><span class="sxs-lookup"><span data-stu-id="82ca4-176">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="82ca4-177">Klicken Sie auf **Auswählen**.</span><span class="sxs-lookup"><span data-stu-id="82ca4-177">Click **Select**.</span></span> <span data-ttu-id="82ca4-178">Wenn Sie die IP-Adresse Ihres Geräts nicht kennen, suchen Sie unter **Einstellungen > Netzwerk & Internet > Erweiterte Optionen**.</span><span class="sxs-lookup"><span data-stu-id="82ca4-178">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="82ca4-179">Klicken Sie in der oberen Menüleiste auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="82ca4-179">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="82ca4-180">Wenn Sie die Bereitstellung auf Ihrem Gerät zum ersten Mal durchführt, müssen Sie [es mit Visual Studio](using-visual-studio.md#pairing-your-device-hololens)koppeln.</span><span class="sxs-lookup"><span data-stu-id="82ca4-180">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="82ca4-181">Wenn die APP bereitgestellt wurde, schließen Sie das **fitbox** -Gerät mit einer **Auswahl Bewegung**ab.</span><span class="sxs-lookup"><span data-stu-id="82ca4-181">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="82ca4-182">Bei der Bereitstellung auf einem immersiven Headset:</span><span class="sxs-lookup"><span data-stu-id="82ca4-182">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="82ca4-183">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x64**.</span><span class="sxs-lookup"><span data-stu-id="82ca4-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="82ca4-184">Stellen Sie sicher, dass das Bereitstellungs Ziel auf **lokaler Computer**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="82ca4-184">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="82ca4-185">Klicken Sie in der oberen Menüleiste auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="82ca4-185">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="82ca4-186">Wenn die APP bereitgestellt wurde, schließen Sie die Funktion **, indem Sie** den-Typ auf einen Bewegungs Controller ziehen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-186">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="82ca4-187">Im Visual Studio-Fehler Panel werden möglicherweise einige rote Fehler feststellen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-187">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="82ca4-188">Es ist sicher, Sie zu ignorieren.</span><span class="sxs-lookup"><span data-stu-id="82ca4-188">It is safe to ignore them.</span></span> <span data-ttu-id="82ca4-189">Wechseln Sie zum Ausgabebereich, um den tatsächlichen buildfortschritt anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-189">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="82ca4-190">Fehler im Ausgabe Panel erfordern eine Korrektur (meistens werden Sie durch einen Fehler in einem Skript verursacht).</span><span class="sxs-lookup"><span data-stu-id="82ca4-190">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---awareness"></a><span data-ttu-id="82ca4-191">Kapitel 1: Informationen zum Bewusstsein</span><span class="sxs-lookup"><span data-stu-id="82ca4-191">Chapter 1 - Awareness</span></span>

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a><span data-ttu-id="82ca4-192">Ziele</span><span class="sxs-lookup"><span data-stu-id="82ca4-192">Objectives</span></span>

* <span data-ttu-id="82ca4-193">Erfahren Sie mehr über die **DOS-und "TS** of Voice Command Design".</span><span class="sxs-lookup"><span data-stu-id="82ca4-193">Learn the **Dos and Don'ts** of voice command design.</span></span>
* <span data-ttu-id="82ca4-194">Verwenden Sie **keywordrecognizer** , um auf Blick basierende Sprachbefehle hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-194">Use **KeywordRecognizer** to add gaze based voice commands.</span></span>
* <span data-ttu-id="82ca4-195">Sorgen Sie dafür, dass Benutzer Sprachbefehle mithilfe von Cursor **Feedback**erkennen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-195">Make users aware of voice commands using cursor **feedback**.</span></span>

### <a name="voice-command-design"></a><span data-ttu-id="82ca4-196">Sprach Befehls Entwurf</span><span class="sxs-lookup"><span data-stu-id="82ca4-196">Voice Command Design</span></span>

<span data-ttu-id="82ca4-197">In diesem Kapitel erfahren Sie mehr über das Entwerfen von Sprachbefehlen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-197">In this chapter, you'll learn about designing voice commands.</span></span> <span data-ttu-id="82ca4-198">Beim Erstellen von Sprachbefehlen:</span><span class="sxs-lookup"><span data-stu-id="82ca4-198">When creating voice commands:</span></span>

#### <a name="do"></a><span data-ttu-id="82ca4-199">DO</span><span class="sxs-lookup"><span data-stu-id="82ca4-199">DO</span></span>

* <span data-ttu-id="82ca4-200">Erstellen Sie präzise Befehle.</span><span class="sxs-lookup"><span data-stu-id="82ca4-200">Create concise commands.</span></span> <span data-ttu-id="82ca4-201">Sie möchten nicht *"das aktuell ausgewählte Video abspielen*" verwenden, da dieser Befehl nicht präzise ist und vom Benutzer leicht vergessen wird.</span><span class="sxs-lookup"><span data-stu-id="82ca4-201">You don't want to use *"Play the currently selected video"*, because that command is not concise and would easily be forgotten by the user.</span></span> <span data-ttu-id="82ca4-202">Verwenden Sie stattdessen Folgendes: *"Video abspielen"* , da es kurz ist und über mehrere Silben verfügt.</span><span class="sxs-lookup"><span data-stu-id="82ca4-202">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="82ca4-203">Verwenden Sie ein einfaches Vokabular.</span><span class="sxs-lookup"><span data-stu-id="82ca4-203">Use a simple vocabulary.</span></span> <span data-ttu-id="82ca4-204">Versuchen Sie immer, gängige Wörter und Ausdrücke zu verwenden, die für den Benutzer leicht zu erkennen und zu merken sind.</span><span class="sxs-lookup"><span data-stu-id="82ca4-204">Always try to use common words and phrases that are easy for the user to discover and remember.</span></span> <span data-ttu-id="82ca4-205">Wenn Ihre Anwendung z. b. ein Notiz Objekt hätte, das in der Ansicht angezeigt oder ausgeblendet werden kann, würden Sie den Befehl *"Placard anzeigen"* nicht verwenden, da "Placard" ein selten verwendeter Begriff ist.</span><span class="sxs-lookup"><span data-stu-id="82ca4-205">For example, if your application had a note object that could be displayed or hidden from view, you would not use the command *"Show Placard"*, because "placard" is a rarely used term.</span></span> <span data-ttu-id="82ca4-206">Verwenden Sie stattdessen den Befehl: *"Hinweis anzeigen"* , um den Hinweis in der Anwendung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-206">Instead, you would use the command: *"Show Note"*, to reveal the note in your application.</span></span>
* <span data-ttu-id="82ca4-207">Achten Sie auf Einheitlichkeit.</span><span class="sxs-lookup"><span data-stu-id="82ca4-207">Be consistent.</span></span> <span data-ttu-id="82ca4-208">Sprachbefehle sollten in der gesamten Anwendung konsistent gehalten werden.</span><span class="sxs-lookup"><span data-stu-id="82ca4-208">Voice commands should be kept consistent across your application.</span></span> <span data-ttu-id="82ca4-209">Stellen Sie sich vor, dass Sie in Ihrer Anwendung zwei Szenen haben und beide Szenen eine Schaltfläche zum Schließen der Anwendung enthalten.</span><span class="sxs-lookup"><span data-stu-id="82ca4-209">Imagine that you have two scenes in your application and both scenes contain a button for closing the application.</span></span> <span data-ttu-id="82ca4-210">Wenn in der ersten Szene der Befehl *"Exit"* zum auslöst der Schaltfläche verwendet wird, aber die zweite Szene den Befehl *"APP schließen"* verwendet hat, wird der Benutzer sehr verwirrt.</span><span class="sxs-lookup"><span data-stu-id="82ca4-210">If the first scene used the command *"Exit"* to trigger the button, but the second scene used the command *"Close App"*, then the user is going to get very confused.</span></span> <span data-ttu-id="82ca4-211">Wenn die gleiche Funktionalität in mehreren Szenen beibehalten wird, sollte der gleiche Sprachbefehl verwendet werden, um Sie zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="82ca4-211">If the same functionality persists across multiple scenes, then the same voice command should be used to trigger it.</span></span>

#### <a name="dont"></a><span data-ttu-id="82ca4-212">TUE NICHT</span><span class="sxs-lookup"><span data-stu-id="82ca4-212">DON'T</span></span>

* <span data-ttu-id="82ca4-213">Verwenden Sie einzelne Silb Bare Befehle.</span><span class="sxs-lookup"><span data-stu-id="82ca4-213">Use single syllable commands.</span></span> <span data-ttu-id="82ca4-214">Wenn Sie z. b. einen Sprachbefehl zum Abspielen eines Videos erstellt haben, sollten Sie die Verwendung des einfachen Befehls *"Play"* vermeiden, da es sich nur um eine einzelne Silb Bare Sprache handelt, die vom System leicht übersehen werden könnte.</span><span class="sxs-lookup"><span data-stu-id="82ca4-214">As an example, if you were creating a voice command to play a video, you should avoid using the simple command *"Play"*, as it is only a single syllable and could easily be missed by the system.</span></span> <span data-ttu-id="82ca4-215">Verwenden Sie stattdessen Folgendes: *"Video abspielen"* , da es kurz ist und über mehrere Silben verfügt.</span><span class="sxs-lookup"><span data-stu-id="82ca4-215">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="82ca4-216">Verwenden Sie Systembefehle.</span><span class="sxs-lookup"><span data-stu-id="82ca4-216">Use system commands.</span></span> <span data-ttu-id="82ca4-217">Der Befehl *"Select"* ist vom System für das auslöst eines Tap-Ereignisses für das aktuell fokussierte Objekt reserviert.</span><span class="sxs-lookup"><span data-stu-id="82ca4-217">The *"Select"* command is reserved by the system to trigger a Tap event for the currently focused object.</span></span> <span data-ttu-id="82ca4-218">Verwenden Sie den Befehl *"Select"* nicht in einem Schlüsselwort oder Ausdruck, da dies möglicherweise nicht erwartungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="82ca4-218">Do not re-use the *"Select"* command in a keyword or phrase, as it might not work as you expect.</span></span> <span data-ttu-id="82ca4-219">Wenn z. b. der Sprachbefehl zum Auswählen eines Cubes in der Anwendung *"Select Cube"* war, der Benutzer aber eine Kugel schaute, als er den Befehl aussprach, wird stattdessen die Kugel ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="82ca4-219">For example, if the voice command for selecting a cube in your application was *"Select cube"*, but the user was looking at a sphere when they uttered the command, then the sphere would be selected instead.</span></span> <span data-ttu-id="82ca4-220">Ähnliche app-leisten Befehle sind sprach fähig.</span><span class="sxs-lookup"><span data-stu-id="82ca4-220">Similarly app bar commands are voice enabled.</span></span> <span data-ttu-id="82ca4-221">Verwenden Sie die folgenden Sprachbefehle nicht in der corewindow-Ansicht:</span><span class="sxs-lookup"><span data-stu-id="82ca4-221">Don't use the following speech commands in your CoreWindow View:</span></span>
    1. <span data-ttu-id="82ca4-222">Zurück</span><span class="sxs-lookup"><span data-stu-id="82ca4-222">Go Back</span></span>
    2. <span data-ttu-id="82ca4-223">Scrolltool</span><span class="sxs-lookup"><span data-stu-id="82ca4-223">Scroll Tool</span></span>
    3. <span data-ttu-id="82ca4-224">Zoom Tool</span><span class="sxs-lookup"><span data-stu-id="82ca4-224">Zoom Tool</span></span>
    4. <span data-ttu-id="82ca4-225">Tool ziehen</span><span class="sxs-lookup"><span data-stu-id="82ca4-225">Drag Tool</span></span>
    5. <span data-ttu-id="82ca4-226">Anpassen</span><span class="sxs-lookup"><span data-stu-id="82ca4-226">Adjust</span></span>
    6. <span data-ttu-id="82ca4-227">Entfernen</span><span class="sxs-lookup"><span data-stu-id="82ca4-227">Remove</span></span>
* <span data-ttu-id="82ca4-228">Verwenden Sie ähnliche Sounds.</span><span class="sxs-lookup"><span data-stu-id="82ca4-228">Use similar sounds.</span></span> <span data-ttu-id="82ca4-229">Versuchen Sie, die Verwendung von Sprachbefehlen zu vermeiden, die sich in der</span><span class="sxs-lookup"><span data-stu-id="82ca4-229">Try to avoid using voice commands that rhyme.</span></span> <span data-ttu-id="82ca4-230">Wenn Sie über eine Einkaufs Anwendung verfügen, in der *"Store anzeigen"* und *"mehr anzeigen"* als Sprachbefehle unterstützt werden, sollten Sie einen der Befehle deaktivieren, während der andere verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="82ca4-230">If you had a shopping application which supported *"Show Store"* and *"Show More"* as voice commands, then you would want to disable one of the commands while the other was in use.</span></span> <span data-ttu-id="82ca4-231">Beispielsweise können Sie die Schaltfläche *"Store anzeigen"* verwenden, um den Store zu öffnen, und dann diesen Befehl deaktivieren, wenn der Speicher angezeigt wird, sodass der Befehl *"Weitere anzeigen"* zum Durchsuchen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="82ca4-231">For example, you could use the *"Show Store"* button to open the store, and then disable that command when the store was displayed so that the *"Show More"* command could be used for browsing.</span></span>

### <a name="instructions"></a><span data-ttu-id="82ca4-232">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="82ca4-232">Instructions</span></span>

* <span data-ttu-id="82ca4-233">Verwenden Sie im Bereich **Hierarchie** von Unity das Suchtool, um das **holoComm_screen_mesh** -Objekt zu suchen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-233">In Unity's **Hierarchy** panel, use the search tool to find the **holoComm_screen_mesh** object.</span></span>
* <span data-ttu-id="82ca4-234">Doppelklicken Sie auf das **holoComm_screen_mesh** -Objekt, um es in der **Szene**anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-234">Double-click on the **holoComm_screen_mesh** object to view it in the **Scene**.</span></span> <span data-ttu-id="82ca4-235">Dies ist die Überwachung des Astronauten, die auf unsere Sprachbefehle antwortet.</span><span class="sxs-lookup"><span data-stu-id="82ca4-235">This is the astronaut's watch, which will respond to our voice commands.</span></span>
* <span data-ttu-id="82ca4-236">Suchen Sie im **Inspektor** -Panel die Komponente **Spracheingabe Quelle (Skript)** .</span><span class="sxs-lookup"><span data-stu-id="82ca4-236">In the **Inspector** panel, locate the **Speech Input Source (Script)** component.</span></span>
* <span data-ttu-id="82ca4-237">Erweitern Sie den Abschnitt **Schlüsselwörter** , um den unterstützten Sprachbefehl anzuzeigen: **Öffnen Sie Communicator**.</span><span class="sxs-lookup"><span data-stu-id="82ca4-237">Expand the **Keywords** section to see the supported voice command: **Open Communicator**.</span></span>
* <span data-ttu-id="82ca4-238">Klicken Sie rechts auf das Zahnrad Symbol, und wählen Sie **Skript bearbeiten**aus.</span><span class="sxs-lookup"><span data-stu-id="82ca4-238">Click the cog to the right side, then select **Edit Script**.</span></span>
* <span data-ttu-id="82ca4-239">Erkunden Sie **SpeechInputSource.cs** , um zu verstehen, wie das **keywordrecognizer** zum Hinzufügen von Sprachbefehlen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="82ca4-239">Explore **SpeechInputSource.cs** to understand how it uses the **KeywordRecognizer** to add voice commands.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="82ca4-240">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="82ca4-240">Build and Deploy</span></span>

* <span data-ttu-id="82ca4-241">Verwenden Sie in Unity **Datei >** Buildeinstellungen, um die Anwendung neu zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-241">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="82ca4-242">Öffnen Sie den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="82ca4-242">Open the **App** folder.</span></span>
* <span data-ttu-id="82ca4-243">Öffnen Sie die Visual Studio-Projekt Mappe **Model Explorer**.</span><span class="sxs-lookup"><span data-stu-id="82ca4-243">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="82ca4-244">(Wenn Sie dieses Projekt bereits während der Einrichtung in Visual Studio erstellt bzw. bereitgestellt haben, können Sie diese Instanz von Visual Studio öffnen und auf "alles neu laden" klicken).</span><span class="sxs-lookup"><span data-stu-id="82ca4-244">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>

* <span data-ttu-id="82ca4-245">Klicken Sie in Visual Studio auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="82ca4-245">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="82ca4-246">Nachdem die Anwendung in den hololens bereitgestellt wurde, schließen Sie das Feld anpassen mithilfe der [Tasten](gestures.md#air-tap) Kombination.</span><span class="sxs-lookup"><span data-stu-id="82ca4-246">After the application deploys to the HoloLens, dismiss the fit box using the [air-tap](gestures.md#air-tap) gesture.</span></span>
* <span data-ttu-id="82ca4-247">Schauen Sie sich die Überwachung des Astronauten an.</span><span class="sxs-lookup"><span data-stu-id="82ca4-247">Gaze at the astronaut's watch.</span></span>
* <span data-ttu-id="82ca4-248">Wenn die Überwachung den Fokus besitzt, überprüfen Sie, ob sich der Cursor in ein Mikrofon ändert.</span><span class="sxs-lookup"><span data-stu-id="82ca4-248">When the watch has focus, verify that the cursor changes to a microphone.</span></span> <span data-ttu-id="82ca4-249">Dadurch erhalten Sie Feedback, dass die Anwendung Sprachbefehle abhört.</span><span class="sxs-lookup"><span data-stu-id="82ca4-249">This provides feedback that the application is listening for voice commands.</span></span>
* <span data-ttu-id="82ca4-250">Vergewissern Sie sich, dass auf der Überwachung eine QuickInfo angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="82ca4-250">Verify that a tooltip appears on the watch.</span></span> <span data-ttu-id="82ca4-251">Dadurch können Benutzer den Befehl *"Open Communicator"* ermitteln.</span><span class="sxs-lookup"><span data-stu-id="82ca4-251">This helps users discover the *"Open Communicator"* command.</span></span>
* <span data-ttu-id="82ca4-252">Nehmen Sie beim Ansehen bei der Überwachung *"Open Communicator"* an, um den Communicator-Bereich zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-252">While gazing at the watch, say *"Open Communicator"* to open the communicator panel.</span></span>

## <a name="chapter-2---acknowledgement"></a><span data-ttu-id="82ca4-253">Kapitel 2: Bestätigung</span><span class="sxs-lookup"><span data-stu-id="82ca4-253">Chapter 2 - Acknowledgement</span></span>

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a><span data-ttu-id="82ca4-254">Ziele</span><span class="sxs-lookup"><span data-stu-id="82ca4-254">Objectives</span></span>

* <span data-ttu-id="82ca4-255">Aufzeichnen einer Nachricht mithilfe der Mikrofon Eingabe.</span><span class="sxs-lookup"><span data-stu-id="82ca4-255">Record a message using the Microphone input.</span></span>
* <span data-ttu-id="82ca4-256">Geben Sie dem Benutzer Feedback, dass die Anwendung seine Stimme abhört.</span><span class="sxs-lookup"><span data-stu-id="82ca4-256">Give feedback to the user that the application is listening to their voice.</span></span>

>[!NOTE]
><span data-ttu-id="82ca4-257">Die **Mikrofon** Funktion muss deklariert werden, damit eine APP vom Mikrofon aufgezeichnet werden muss.</span><span class="sxs-lookup"><span data-stu-id="82ca4-257">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="82ca4-258">Dies erfolgt bereits in der Mr-Eingabe 212, aber beachten Sie dies für Ihre eigenen Projekte.</span><span class="sxs-lookup"><span data-stu-id="82ca4-258">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="82ca4-259">Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zu "> Projekteinstellungen bearbeiten > Player" navigieren.</span><span class="sxs-lookup"><span data-stu-id="82ca4-259">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="82ca4-260">Klicken Sie auf die Registerkarte "universelle Windows-Plattform".</span><span class="sxs-lookup"><span data-stu-id="82ca4-260">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="82ca4-261">Aktivieren Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die **Mikrofon** Funktion.</span><span class="sxs-lookup"><span data-stu-id="82ca4-261">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="82ca4-262">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="82ca4-262">Instructions</span></span>

* <span data-ttu-id="82ca4-263">Überprüfen Sie im Bereich **Hierarchie** der Unity, ob das **holoComm_screen_mesh** -Objekt ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="82ca4-263">In Unity's **Hierarchy** panel, verify that the **holoComm_screen_mesh** object is selected.</span></span>
* <span data-ttu-id="82ca4-264">Suchen Sie im **Inspektor** -Panel nach der Komponente " **Astronauten Überwachung (Skript)** ".</span><span class="sxs-lookup"><span data-stu-id="82ca4-264">In the **Inspector** panel, find the **Astronaut Watch (Script)** component.</span></span>
* <span data-ttu-id="82ca4-265">Klicken Sie auf den kleinen, blauen Cube, der als Wert der **Communicator Prefab** -Eigenschaft festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="82ca4-265">Click on the small, blue cube which is set as the value of the **Communicator Prefab** property.</span></span>
* <span data-ttu-id="82ca4-266">Im **Projekt** Panel sollte die **Communicator** -vorfab jetzt den Fokus haben.</span><span class="sxs-lookup"><span data-stu-id="82ca4-266">In the **Project** panel, the **Communicator** prefab should now have focus.</span></span>
* <span data-ttu-id="82ca4-267">Klicken Sie im **Projekt** Panel auf die **Communicator** -vorfab, um die zugehörigen Komponenten im **Inspektor**anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-267">Click on the **Communicator** prefab in the **Project** panel to view its components in the **Inspector**.</span></span>
* <span data-ttu-id="82ca4-268">Sehen Sie sich die Komponente " **Mikrofon-Manager (Skript)** " an, damit wir die Stimme des Benutzers aufzeichnen können.</span><span class="sxs-lookup"><span data-stu-id="82ca4-268">Look at the **Microphone Manager (Script)** component, this will allow us to record the user's voice.</span></span>
* <span data-ttu-id="82ca4-269">Beachten Sie, dass das **Communicator** -Objekt über eine **Spracheingabe Handler-Komponente (Skript)** für die Antwort auf den Befehl " **Nachricht senden** " verfügt.</span><span class="sxs-lookup"><span data-stu-id="82ca4-269">Notice that the **Communicator** object has a **Speech Input Handler (Script)** component for responding to the **Send Message** command.</span></span>
* <span data-ttu-id="82ca4-270">Sehen Sie sich die **Communicator (Script)** -Komponente an, und doppelklicken Sie auf das Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-270">Look at the **Communicator (Script)** component and double-click on the script to open it in Visual Studio.</span></span>

<span data-ttu-id="82ca4-271">Communicator.cs ist dafür verantwortlich, die richtigen Schaltflächen Zustände auf dem Communicator-Gerät festzulegen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-271">Communicator.cs is responsible for setting the proper button states on the communicator device.</span></span> <span data-ttu-id="82ca4-272">Dies ermöglicht es unseren Benutzern, eine Nachricht aufzuzeichnen, wieder abzuspielen und die Nachricht an den Astronauten zu senden.</span><span class="sxs-lookup"><span data-stu-id="82ca4-272">This will allow our users to record a message, play it back, and send the message to the astronaut.</span></span> <span data-ttu-id="82ca4-273">Außerdem wird ein animiertes Wellen Formular gestartet und angehalten, um dem Benutzer zu bestätigen, dass seine Stimme gehört.</span><span class="sxs-lookup"><span data-stu-id="82ca4-273">It will also start and stop an animated wave form, to acknowledge to the user that their voice was heard.</span></span>

* <span data-ttu-id="82ca4-274">Löschen Sie in **Communicator.cs**die folgenden Zeilen (81 und 82) aus der **Start** -Methode.</span><span class="sxs-lookup"><span data-stu-id="82ca4-274">In **Communicator.cs**, delete the following lines (81 and 82) from the **Start** method.</span></span> <span data-ttu-id="82ca4-275">Dadurch wird die Schaltfläche "Record" auf dem Communicator aktiviert.</span><span class="sxs-lookup"><span data-stu-id="82ca4-275">This will enable the 'Record' button on the communicator.</span></span>

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a><span data-ttu-id="82ca4-276">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="82ca4-276">Build and Deploy</span></span>

* <span data-ttu-id="82ca4-277">Erstellen Sie in Visual Studio die Anwendung neu, und stellen Sie Sie auf dem Gerät bereit.</span><span class="sxs-lookup"><span data-stu-id="82ca4-277">In Visual Studio, rebuild your application and deploy to the device.</span></span>
* <span data-ttu-id="82ca4-278">Schauen Sie sich die Überwachung des Astronauten an, und sagen Sie *"Open Communicator"* , um den Communicator anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-278">Gaze at the astronaut's watch and say *"Open Communicator"* to show the communicator.</span></span>
* <span data-ttu-id="82ca4-279">Klicken Sie auf die Schaltfläche " **Record** " (Mikrofon), um die Aufzeichnung einer verbalen Nachricht für den Astronauten zu starten</span><span class="sxs-lookup"><span data-stu-id="82ca4-279">Press the **Record** button (microphone) to start recording a verbal message for the astronaut.</span></span>
* <span data-ttu-id="82ca4-280">Beginnen Sie mit dem Gespräch, und überprüfen Sie, ob die Wave-Animation auf dem Communicator abgespielt wird, der dem Benutzer Feedback zur Verfügung stellt, dass Ihre Stimme gehört.</span><span class="sxs-lookup"><span data-stu-id="82ca4-280">Start speaking, and verify that the wave animation plays on the communicator, which provides feedback to the user that their voice is heard.</span></span>
* <span data-ttu-id="82ca4-281">Klicken Sie auf die Schaltfläche **Beenden** (linkes Quadrat), und überprüfen Sie, ob die Wave-Animation beendet wird.</span><span class="sxs-lookup"><span data-stu-id="82ca4-281">Press the **Stop** button (left square), and verify that the wave animation stops running.</span></span>
* <span data-ttu-id="82ca4-282">Drücken Sie die **Wiedergabe** Schaltfläche (Rechts Dreieck), um die aufgezeichnete Nachricht wiederzugeben und auf dem Gerät zu hören.</span><span class="sxs-lookup"><span data-stu-id="82ca4-282">Press the **Play** button (right triangle) to play back the recorded message and hear it on the device.</span></span>
* <span data-ttu-id="82ca4-283">Klicken Sie auf die Schaltfläche zum **Abbrechen** (rechts Quadrat), um die Wiedergabe der aufgezeichneten Nachricht zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="82ca4-283">Press the **Stop** button (right square) to stop playback of the recorded message.</span></span>
* <span data-ttu-id="82ca4-284">Sagen *Sie "Nachricht senden"* , um den Communicator zu schließen und die Antwort "Nachricht empfangen" vom Astronauten zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-284">Say *"Send Message"* to close the communicator and receive a 'Message Received' response from the astronaut.</span></span>

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a><span data-ttu-id="82ca4-285">Kapitel 3: verstehen und der Diktat Erkennung</span><span class="sxs-lookup"><span data-stu-id="82ca4-285">Chapter 3 - Understanding and the Dictation Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a><span data-ttu-id="82ca4-286">Ziele</span><span class="sxs-lookup"><span data-stu-id="82ca4-286">Objectives</span></span>

* <span data-ttu-id="82ca4-287">Verwenden Sie die Diktat Erkennung, um die Sprache des Benutzers in Text zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="82ca4-287">Use the Dictation Recognizer to convert the user's speech to text.</span></span>
* <span data-ttu-id="82ca4-288">Zeigen Sie die hypothetisierungserkenfizierung hypothetische und abschließende Ergebnisse in Communicator an.</span><span class="sxs-lookup"><span data-stu-id="82ca4-288">Show the Dictation Recognizer's hypothesized and final results in the communicator.</span></span>

<span data-ttu-id="82ca4-289">In diesem Kapitel verwenden wir die Diktat Erkennung, um eine Nachricht für den Astronaut zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-289">In this chapter, we'll use the Dictation Recognizer to create a message for the astronaut.</span></span> <span data-ttu-id="82ca4-290">Beachten Sie beim Verwenden der Diktat Erkennung Folgendes:</span><span class="sxs-lookup"><span data-stu-id="82ca4-290">When using the Dictation Recognizer, keep in mind that:</span></span>

* <span data-ttu-id="82ca4-291">Sie müssen mit WiFi verbunden sein, damit die Diktat Erkennung funktioniert.</span><span class="sxs-lookup"><span data-stu-id="82ca4-291">You must be connected to WiFi for the Dictation Recognizer to work.</span></span>
* <span data-ttu-id="82ca4-292">Timeouts treten nach einer festgelegten Zeitspanne auf.</span><span class="sxs-lookup"><span data-stu-id="82ca4-292">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="82ca4-293">Es gibt zwei Timeouts, die Sie beachten sollten:</span><span class="sxs-lookup"><span data-stu-id="82ca4-293">There are two timeouts to be aware of:</span></span>
  * <span data-ttu-id="82ca4-294">Wenn die Erkennung startet und keine Audiodaten für die ersten fünf Sekunden hört, wird ein Timeout angezeigt.</span><span class="sxs-lookup"><span data-stu-id="82ca4-294">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
  * <span data-ttu-id="82ca4-295">Wenn die Erkennung ein Ergebnis erhalten hat, dann aber für einen Zeitraum von 20 Sekunden den Ruhe Wert erfährt, wird ein Timeout verursacht.</span><span class="sxs-lookup"><span data-stu-id="82ca4-295">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>
* <span data-ttu-id="82ca4-296">Es kann jeweils nur ein Erkennungs Funktionstyp (Schlüsselwort oder Diktat) ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="82ca4-296">Only one type of recognizer (Keyword or Dictation) can run at a time.</span></span>

>[!NOTE]
><span data-ttu-id="82ca4-297">Die **Mikrofon** Funktion muss deklariert werden, damit eine APP vom Mikrofon aufgezeichnet werden muss.</span><span class="sxs-lookup"><span data-stu-id="82ca4-297">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="82ca4-298">Dies erfolgt bereits in der Mr-Eingabe 212, aber beachten Sie dies für Ihre eigenen Projekte.</span><span class="sxs-lookup"><span data-stu-id="82ca4-298">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="82ca4-299">Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zu "> Projekteinstellungen bearbeiten > Player" navigieren.</span><span class="sxs-lookup"><span data-stu-id="82ca4-299">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="82ca4-300">Klicken Sie auf die Registerkarte "universelle Windows-Plattform".</span><span class="sxs-lookup"><span data-stu-id="82ca4-300">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="82ca4-301">Aktivieren Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die **Mikrofon** Funktion.</span><span class="sxs-lookup"><span data-stu-id="82ca4-301">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="82ca4-302">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="82ca4-302">Instructions</span></span>

<span data-ttu-id="82ca4-303">Wir werden **MicrophoneManager.cs** bearbeiten, um die Diktat Erkennung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="82ca4-303">We're going to edit **MicrophoneManager.cs** to use the Dictation Recognizer.</span></span> <span data-ttu-id="82ca4-304">Dies fügen wir hinzu:</span><span class="sxs-lookup"><span data-stu-id="82ca4-304">This is what we'll add:</span></span>

1. <span data-ttu-id="82ca4-305">Wenn die **Schaltfläche "Datensatz** " gedrückt ist, **starten wir das "diktationerkenzer**".</span><span class="sxs-lookup"><span data-stu-id="82ca4-305">When the **Record button** is pressed, we'll **start the DictationRecognizer**.</span></span>
2. <span data-ttu-id="82ca4-306">Zeigen Sie die **Hypothese** an, was der diktationerkenzer verstanden hat.</span><span class="sxs-lookup"><span data-stu-id="82ca4-306">Show the **hypothesis** of what the DictationRecognizer understood.</span></span>
3. <span data-ttu-id="82ca4-307">Lock in den **Ergebnissen** der von der diktationerkenzer erkannten Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="82ca4-307">Lock in the **results** of what the DictationRecognizer understood.</span></span>
4. <span data-ttu-id="82ca4-308">Überprüfen Sie, ob Timeouts von der "diktationerkenzer".</span><span class="sxs-lookup"><span data-stu-id="82ca4-308">Check for timeouts from the DictationRecognizer.</span></span>
5. <span data-ttu-id="82ca4-309">Wenn die **Schaltfläche "beenden** " gedrückt wird oder bei der MIC-Sitzung ein Timeout auftritt, **Beenden Sie das "diktationerkenzer**".</span><span class="sxs-lookup"><span data-stu-id="82ca4-309">When the **Stop button** is pressed, or the mic session times out, **stop the DictationRecognizer**.</span></span>
6. <span data-ttu-id="82ca4-310">Starten Sie den **keywordrecognizer**neu, der auf den Befehl " **Nachricht senden** " lauscht.</span><span class="sxs-lookup"><span data-stu-id="82ca4-310">Restart the **KeywordRecognizer**, which will listen for the **Send Message** command.</span></span>

<span data-ttu-id="82ca4-311">Los geht's.</span><span class="sxs-lookup"><span data-stu-id="82ca4-311">Let's get started.</span></span> <span data-ttu-id="82ca4-312">Vervollständigen Sie alle Codierungs Übungen für 3. a in **MicrophoneManager.cs**, oder kopieren Sie den unten stehenden Code, und fügen Sie ihn ein:</span><span class="sxs-lookup"><span data-stu-id="82ca4-312">Complete all coding exercises for 3.a in **MicrophoneManager.cs**, or copy and paste the finished code found below:</span></span>

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

### <a name="build-and-deploy"></a><span data-ttu-id="82ca4-313">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="82ca4-313">Build and Deploy</span></span>

* <span data-ttu-id="82ca4-314">Erstellen Sie in Visual Studio neu, und stellen Sie auf Ihrem Gerät bereit.</span><span class="sxs-lookup"><span data-stu-id="82ca4-314">Rebuild in Visual Studio and deploy to your device.</span></span>
* <span data-ttu-id="82ca4-315">Schließen Sie das Feld "anpassen" mit einer Tastenkombination.</span><span class="sxs-lookup"><span data-stu-id="82ca4-315">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="82ca4-316">Schauen Sie sich die Überwachung des Astronauten an, und sagen Sie *"Open Communicator"* .</span><span class="sxs-lookup"><span data-stu-id="82ca4-316">Gaze at the astronaut's watch and say *"Open Communicator"*.</span></span>
* <span data-ttu-id="82ca4-317">Wählen Sie die Schaltfläche **Datensatz** (Mikrofon) aus, um Ihre Nachricht aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-317">Select the **Record** button (microphone) to record your message.</span></span>
* <span data-ttu-id="82ca4-318">Beginnen Sie den Einstieg.</span><span class="sxs-lookup"><span data-stu-id="82ca4-318">Start speaking.</span></span> <span data-ttu-id="82ca4-319">Die **Diktat Erkennung** interpretiert Ihre Sprache und zeigt den Text mit hypothetischer Größe in Communicator an.</span><span class="sxs-lookup"><span data-stu-id="82ca4-319">The **Dictation Recognizer** will interpret your speech and show the hypothesized text in the communicator.</span></span>
* <span data-ttu-id="82ca4-320">Versuchen Sie, *"Nachricht senden"* zu sagen, während Sie eine Nachricht aufzeichnen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-320">Try saying *"Send Message"* while you are recording a message.</span></span> <span data-ttu-id="82ca4-321">Beachten Sie, dass die **Schlüsselwort Erkennung** nicht antwortet, weil die **Diktat Erkennung** noch aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="82ca4-321">Notice that the **Keyword Recognizer** does not respond because the **Dictation Recognizer** is still active.</span></span>
* <span data-ttu-id="82ca4-322">Sprechen Sie einige Sekunden lang nicht mehr.</span><span class="sxs-lookup"><span data-stu-id="82ca4-322">Stop speaking for a few seconds.</span></span> <span data-ttu-id="82ca4-323">Sehen Sie sich an, wie die Diktat Erkennung die Hypothese abschließt und das Endergebnis anzeigt.</span><span class="sxs-lookup"><span data-stu-id="82ca4-323">Watch as the Dictation Recognizer completes its hypothesis and shows the final result.</span></span>
* <span data-ttu-id="82ca4-324">Beginnen Sie mit der Sprachverarbeitung, und halten Sie dann 20 Sekunden an</span><span class="sxs-lookup"><span data-stu-id="82ca4-324">Begin speaking and then pause for 20 seconds.</span></span> <span data-ttu-id="82ca4-325">Dies führt dazu, dass die **diktierungerkenfizierung** ein Timeout verursacht.</span><span class="sxs-lookup"><span data-stu-id="82ca4-325">This will cause the **Dictation Recognizer** to timeout.</span></span>
* <span data-ttu-id="82ca4-326">Beachten Sie, dass die **Schlüsselwort Erkennung** nach dem obigen Timeout erneut aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="82ca4-326">Notice that the **Keyword Recognizer** is re-enabled after the above timeout.</span></span> <span data-ttu-id="82ca4-327">Der Communicator antwortet nun auf Sprachbefehle.</span><span class="sxs-lookup"><span data-stu-id="82ca4-327">The communicator will now respond to voice commands.</span></span>
* <span data-ttu-id="82ca4-328">Sagen Sie *"Nachricht senden"* , um die Nachricht an den Astronaut zu senden.</span><span class="sxs-lookup"><span data-stu-id="82ca4-328">Say *"Send Message"* to send the message to the astronaut.</span></span>

## <a name="chapter-4---grammar-recognizer"></a><span data-ttu-id="82ca4-329">Kapitel 4: Grammatik Erkennung</span><span class="sxs-lookup"><span data-stu-id="82ca4-329">Chapter 4 - Grammar Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a><span data-ttu-id="82ca4-330">Ziele</span><span class="sxs-lookup"><span data-stu-id="82ca4-330">Objectives</span></span>

* <span data-ttu-id="82ca4-331">Verwenden Sie die Grammatik Erkennung, um die Sprache des Benutzers gemäß einer SRGS-oder Spracherkennungs-Grammatik Spezifikation zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-331">Use the Grammar Recognizer to recognize the user's speech according to an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

>[!NOTE]
><span data-ttu-id="82ca4-332">Die **Mikrofon** Funktion muss deklariert werden, damit eine APP vom Mikrofon aufgezeichnet werden muss.</span><span class="sxs-lookup"><span data-stu-id="82ca4-332">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="82ca4-333">Dies erfolgt bereits in der Mr-Eingabe 212, aber beachten Sie dies für Ihre eigenen Projekte.</span><span class="sxs-lookup"><span data-stu-id="82ca4-333">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="82ca4-334">Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zu "> Projekteinstellungen bearbeiten > Player" navigieren.</span><span class="sxs-lookup"><span data-stu-id="82ca4-334">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="82ca4-335">Klicken Sie auf die Registerkarte "universelle Windows-Plattform".</span><span class="sxs-lookup"><span data-stu-id="82ca4-335">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="82ca4-336">Aktivieren Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die **Mikrofon** Funktion.</span><span class="sxs-lookup"><span data-stu-id="82ca4-336">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="82ca4-337">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="82ca4-337">Instructions</span></span>

1. <span data-ttu-id="82ca4-338">Suchen Sie im **Hierarchie** Panel nach **Jetpack_Center** , und wählen Sie es aus.</span><span class="sxs-lookup"><span data-stu-id="82ca4-338">In the **Hierarchy** panel, search for **Jetpack_Center** and select it.</span></span>
2. <span data-ttu-id="82ca4-339">Suchen Sie im **Inspektor** -Panel nach dem Skript " **Tagalong Action** ".</span><span class="sxs-lookup"><span data-stu-id="82ca4-339">Look for the **Tagalong Action** script in the **Inspector** panel.</span></span>
3. <span data-ttu-id="82ca4-340">Klicken Sie rechts neben dem Feld **zu tagendes Objekt auf** den kleinen Kreis.</span><span class="sxs-lookup"><span data-stu-id="82ca4-340">Click the little circle to the right of the **Object To Tag Along** field.</span></span>
4. <span data-ttu-id="82ca4-341">Suchen Sie im Fenster, das angezeigt wird, nach **srgstoolbox** , und wählen Sie es aus der Liste aus.</span><span class="sxs-lookup"><span data-stu-id="82ca4-341">In the window that pops up, search for **SRGSToolbox** and select it from the list.</span></span>
5. <span data-ttu-id="82ca4-342">Sehen Sie sich die Datei " **srgscolor. XML** " im Ordner " **streamingassets** " an.</span><span class="sxs-lookup"><span data-stu-id="82ca4-342">Take a look at the **SRGSColor.xml** file in the **StreamingAssets** folder.</span></span>
* <span data-ttu-id="82ca4-343">Die SRGS-Entwurfs Spezifikation finden Sie [hier](https://www.w3.org/TR/speech-grammar/)auf der W3C-Website.</span><span class="sxs-lookup"><span data-stu-id="82ca4-343">The SRGS design spec can be found on the W3C website [here](https://www.w3.org/TR/speech-grammar/).</span></span>
* <span data-ttu-id="82ca4-344">In der SRGS-Datei gibt es drei Arten von Regeln:</span><span class="sxs-lookup"><span data-stu-id="82ca4-344">In our SRGS file, we have three types of rules:</span></span>
  * <span data-ttu-id="82ca4-345">Eine Regel, mit der Sie eine Farbe aus einer Liste von zwölf Farben sagen können.</span><span class="sxs-lookup"><span data-stu-id="82ca4-345">A rule which lets you say one color from a list of twelve colors.</span></span>
  * <span data-ttu-id="82ca4-346">Drei Regeln, die auf eine Kombination der Farbregel und einer der drei Formen lauschen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-346">Three rules which listen for a combination of the color rule and one of the three shapes.</span></span>
  * <span data-ttu-id="82ca4-347">Die Stamm Regel colorchooser, die auf eine beliebige Kombination der drei "Color + Shape"-Regeln lauscht.</span><span class="sxs-lookup"><span data-stu-id="82ca4-347">The root rule, colorChooser, which listens for any combination of the three "color + shape" rules.</span></span> <span data-ttu-id="82ca4-348">Die Formen können in beliebiger Reihenfolge und in beliebiger Reihenfolge von nur einem bis zu allen drei Formen bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="82ca4-348">The shapes can be said in any order and in any amount from just one to all three.</span></span> <span data-ttu-id="82ca4-349">Dies ist die einzige Regel, die überwacht wird, da Sie als Stamm Regel am Anfang der Datei im ursprünglichen &lt;Grammatik&gt; -Tag angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="82ca4-349">This is the only rule that is listened for, as it's specified as the root rule at the top of the file in the initial &lt;grammar&gt; tag.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="82ca4-350">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="82ca4-350">Build and Deploy</span></span>

* <span data-ttu-id="82ca4-351">Erstellen Sie die Anwendung in Unity neu, erstellen Sie Sie in Visual Studio, und stellen Sie Sie bereit, um die APP auf hololens zu erleben</span><span class="sxs-lookup"><span data-stu-id="82ca4-351">Rebuild the application in Unity, then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="82ca4-352">Schließen Sie das Feld "anpassen" mit einer Tastenkombination.</span><span class="sxs-lookup"><span data-stu-id="82ca4-352">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="82ca4-353">Schauen Sie sich das Jetpack des Astronauten an, und führen Sie eine Luft tippen Bewegung aus.</span><span class="sxs-lookup"><span data-stu-id="82ca4-353">Gaze at the astronaut's jetpack and perform an air-tap gesture.</span></span>
* <span data-ttu-id="82ca4-354">Beginnen Sie den Einstieg.</span><span class="sxs-lookup"><span data-stu-id="82ca4-354">Start speaking.</span></span> <span data-ttu-id="82ca4-355">Die **Grammatik Erkennung** interpretiert Ihre Sprache und ändert die Farben der Formen basierend auf der Erkennung.</span><span class="sxs-lookup"><span data-stu-id="82ca4-355">The **Grammar Recognizer** will interpret your speech and change the colors of the shapes based on the recognition.</span></span> <span data-ttu-id="82ca4-356">Ein Beispiel Befehl ist "blauer Kreis, gelbes Quadrat".</span><span class="sxs-lookup"><span data-stu-id="82ca4-356">An example command is "blue circle, yellow square".</span></span>
* <span data-ttu-id="82ca4-357">Führen Sie eine weitere Luft tippen Bewegung aus, um die Toolbox zu schließen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-357">Perform another air-tap gesture to dismiss the toolbox.</span></span>

## <a name="the-end"></a><span data-ttu-id="82ca4-358">Das Ende</span><span class="sxs-lookup"><span data-stu-id="82ca4-358">The End</span></span>

<span data-ttu-id="82ca4-359">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="82ca4-359">Congratulations!</span></span> <span data-ttu-id="82ca4-360">Sie haben nun die **Mr-Eingabe 212 abgeschlossen: Stimme**an.</span><span class="sxs-lookup"><span data-stu-id="82ca4-360">You have now completed **MR Input 212: Voice**.</span></span>

* <span data-ttu-id="82ca4-361">Sie kennen die DOS-und die TS von Voice-Befehlen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-361">You know the Dos and Don'ts of voice commands.</span></span>
* <span data-ttu-id="82ca4-362">Sie haben gesehen, wie Quick Infos verwendet wurden, um die Benutzer auf Sprachbefehle aufmerksam zu machen.</span><span class="sxs-lookup"><span data-stu-id="82ca4-362">You saw how tooltips were employed to make users aware of voice commands.</span></span>
* <span data-ttu-id="82ca4-363">Sie haben verschiedene Feedback Typen verwendet, um zu bestätigen, dass die Stimme des Benutzers gehört.</span><span class="sxs-lookup"><span data-stu-id="82ca4-363">You saw several types of feedback used to acknowledge that the user's voice was heard.</span></span>
* <span data-ttu-id="82ca4-364">Sie wissen, wie Sie zwischen der Schlüsselwort Erkennung und der Diktat Erkennung wechseln und wie diese beiden Features Ihre Stimme verstehen und interpretieren.</span><span class="sxs-lookup"><span data-stu-id="82ca4-364">You know how to switch between the Keyword Recognizer and the Dictation Recognizer, and how these two features understand and interpret your voice.</span></span>
* <span data-ttu-id="82ca4-365">Sie haben gelernt, wie Sie eine SRGS-Datei und die Grammatik Erkennung für die Spracherkennung in Ihrer Anwendung verwenden.</span><span class="sxs-lookup"><span data-stu-id="82ca4-365">You learned how to use an SRGS file and the Grammar Recognizer for speech recognition in your application.</span></span>
