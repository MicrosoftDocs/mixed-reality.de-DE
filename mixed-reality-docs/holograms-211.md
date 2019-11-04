---
title: Mr-Eingabe 211-Geste
description: Befolgen Sie diese exemplarische Vorgehensweise für die Codierung mithilfe von Unity, Visual Studio und hololens, um die Details der Gesten Konzepte zu erlernen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, Tutorial, Geste
ms.openlocfilehash: d7a92e4b2f196d6d8b0ba0fe3ccb2aed87479ac1
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434695"
---
>[!NOTE]
><span data-ttu-id="82a0b-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="82a0b-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="82a0b-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="82a0b-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="82a0b-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="82a0b-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="82a0b-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="82a0b-108">Es wurde [eine neue Reihe von Tutorials](mrlearning-base.md) für hololens 2 gepostet.</span><span class="sxs-lookup"><span data-stu-id="82a0b-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

# <a name="mr-input-211-gesture"></a><span data-ttu-id="82a0b-109">Mr-Eingabe 211: Geste</span><span class="sxs-lookup"><span data-stu-id="82a0b-109">MR Input 211: Gesture</span></span>

<span data-ttu-id="82a0b-110">[Gesten](gaze-and-commit.md#composite-gestures) verwandeln die Benutzer Absicht in eine Aktion.</span><span class="sxs-lookup"><span data-stu-id="82a0b-110">[Gestures](gaze-and-commit.md#composite-gestures) turn user intention into action.</span></span> <span data-ttu-id="82a0b-111">Mit Gesten können Benutzer mit holograms interagieren.</span><span class="sxs-lookup"><span data-stu-id="82a0b-111">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="82a0b-112">In diesem Kurs erfahren Sie, wie Sie die Hände des Benutzers nachverfolgen, auf Benutzereingaben reagieren und dem Benutzer Feedback geben können, der auf dem Hand Bundesland und-Speicherort basiert.</span><span class="sxs-lookup"><span data-stu-id="82a0b-112">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="82a0b-113">In den [Grundlagen 101](holograms-101.md)haben wir eine einfache Air-Tap-Geste verwendet, um mit unseren holograms zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="82a0b-113">In [MR Basics 101](holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="82a0b-114">Nun gehen wir über die Luft tippen Bewegung hinaus und erforschen neue Konzepte für Folgendes:</span><span class="sxs-lookup"><span data-stu-id="82a0b-114">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="82a0b-115">Erkennen, wenn die Hand des Benutzers nachverfolgt wird, und Senden von Feedback an den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="82a0b-115">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="82a0b-116">Verwenden Sie eine Navigations Geste, um unsere Hologramme zu drehen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-116">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="82a0b-117">Geben Sie uns Feedback, wenn der Benutzer die Hand verlässt.</span><span class="sxs-lookup"><span data-stu-id="82a0b-117">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="82a0b-118">Verwenden Sie Manipulations Ereignisse, um Benutzern das Verschieben von holograms mit ihren Händen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-118">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="82a0b-119">In diesem Kurs besuchen wir den Unity-Projekt **Modell-Explorer**, den wir in der [Eingabe 210](holograms-210.md)erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="82a0b-119">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="82a0b-120">Unser Astronauten Freund ist zurück, um uns bei der Untersuchung dieser neuen Gesten Konzepte zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-120">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="82a0b-121">Die in den folgenden Kapiteln eingebetteten Videos wurden mit einer älteren Version von Unity und dem Mixed Reality Toolkit aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="82a0b-121">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="82a0b-122">Die Schritt-für-Schritt-Anweisungen sind genau und aktuell, aber es werden möglicherweise Skripts und Visualisierungen in den entsprechenden Videos angezeigt, die veraltet sind.</span><span class="sxs-lookup"><span data-stu-id="82a0b-122">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="82a0b-123">Die Videos bleiben in der einwelt enthalten und werden weiterhin angewendet.</span><span class="sxs-lookup"><span data-stu-id="82a0b-123">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="82a0b-124">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="82a0b-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="82a0b-125">Natürlich</span><span class="sxs-lookup"><span data-stu-id="82a0b-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="82a0b-126"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="82a0b-126"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="82a0b-127"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="82a0b-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="82a0b-128">Mr-Eingabe 211: Geste</span><span class="sxs-lookup"><span data-stu-id="82a0b-128">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="82a0b-129">✔️</span><span class="sxs-lookup"><span data-stu-id="82a0b-129">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="82a0b-130">✔️</span><span class="sxs-lookup"><span data-stu-id="82a0b-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="82a0b-131">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="82a0b-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="82a0b-132">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="82a0b-132">Prerequisites</span></span>

* <span data-ttu-id="82a0b-133">Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md)konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="82a0b-133">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="82a0b-134">Einige Grund C# Legende Programmiermöglichkeiten.</span><span class="sxs-lookup"><span data-stu-id="82a0b-134">Some basic C# programming ability.</span></span>
* <span data-ttu-id="82a0b-135">Sie sollten die [Grundlagen von 101](holograms-101.md)abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="82a0b-135">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="82a0b-136">Sie sollten die [Mr-Eingabe 210](holograms-210.md)abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="82a0b-136">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="82a0b-137">Ein hololens-Gerät, das [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode)ist.</span><span class="sxs-lookup"><span data-stu-id="82a0b-137">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="82a0b-138">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="82a0b-138">Project files</span></span>

* <span data-ttu-id="82a0b-139">Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) , die für das Projekt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="82a0b-139">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span><span data-ttu-id="82a0b-140"> Erfordert Unity 2017,2 oder höher.</span><span class="sxs-lookup"><span data-stu-id="82a0b-140"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="82a0b-141">Deinstallieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht zugänglichen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="82a0b-141">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="82a0b-142">Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span><span class="sxs-lookup"><span data-stu-id="82a0b-142">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="82a0b-143">Errata und Notizen</span><span class="sxs-lookup"><span data-stu-id="82a0b-143">Errata and Notes</span></span>

* <span data-ttu-id="82a0b-144">"Enable nur eigenen Code" muss in Visual Studio unter "Extras-> Optionen" deaktiviert*werden (>* Debuggen, um Breakpoints im Code zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-144">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="82a0b-145">Kapitel 0: Einrichtung von Unity</span><span class="sxs-lookup"><span data-stu-id="82a0b-145">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="82a0b-146">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="82a0b-146">Instructions</span></span>

1. <span data-ttu-id="82a0b-147">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="82a0b-147">Start Unity.</span></span>
2. <span data-ttu-id="82a0b-148">Wählen Sie **Öffnen**aus.</span><span class="sxs-lookup"><span data-stu-id="82a0b-148">Select **Open**.</span></span>
3. <span data-ttu-id="82a0b-149">Navigieren Sie zu dem **Gesten** Ordner, den Sie zuvor nicht archiviert haben.</span><span class="sxs-lookup"><span data-stu-id="82a0b-149">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="82a0b-150">Suchen Sie den Ordner **Start**/**Model Explorer** , und wählen Sie ihn aus.</span><span class="sxs-lookup"><span data-stu-id="82a0b-150">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="82a0b-151">Klicken Sie auf die Schaltfläche **Ordner auswählen** .</span><span class="sxs-lookup"><span data-stu-id="82a0b-151">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="82a0b-152">Erweitern Sie im **Projekt** Panel den Ordner **Szenen** .</span><span class="sxs-lookup"><span data-stu-id="82a0b-152">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="82a0b-153">Doppelklicken Sie auf **Model Explorer** Scene, um es in Unity zu laden.</span><span class="sxs-lookup"><span data-stu-id="82a0b-153">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="82a0b-154">Erstellen</span><span class="sxs-lookup"><span data-stu-id="82a0b-154">Building</span></span>

1. <span data-ttu-id="82a0b-155">Wählen Sie in Unity **Datei > Buildeinstellungen**aus.</span><span class="sxs-lookup"><span data-stu-id="82a0b-155">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="82a0b-156">Wenn **Szenen/Model Explorer** nicht in **Szenen im Build**aufgeführt ist, klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-156">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="82a0b-157">Wenn Sie speziell für hololens entwickeln, legen Sie **Zielgerät** auf **hololens**fest.</span><span class="sxs-lookup"><span data-stu-id="82a0b-157">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="82a0b-158">Andernfalls sollten Sie es auf **jedem Gerät**belassen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-158">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="82a0b-159">Stellen Sie sicher, dass der **Buildtyp** auf **D3D** und das **SDK** auf **Latest installiert** festgelegt ist (was SDK 16299 oder höher sein sollte).</span><span class="sxs-lookup"><span data-stu-id="82a0b-159">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="82a0b-160">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="82a0b-160">Click **Build**.</span></span>
6. <span data-ttu-id="82a0b-161">Erstellen Sie einen **neuen Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="82a0b-161">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="82a0b-162">Klicken Sie einfach auf den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="82a0b-162">Single click the **App** folder.</span></span>
8. <span data-ttu-id="82a0b-163">Klicken **Sie auf Ordner auswählen** , und Unity startet das Projekt für Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="82a0b-163">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="82a0b-164">Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="82a0b-164">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="82a0b-165">Öffnen Sie den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="82a0b-165">Open the **App** folder.</span></span>
2. <span data-ttu-id="82a0b-166">Öffnen Sie die Visual Studio-Projekt Mappe **Model Explorer**.</span><span class="sxs-lookup"><span data-stu-id="82a0b-166">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="82a0b-167">Bei der Bereitstellung in hololens:</span><span class="sxs-lookup"><span data-stu-id="82a0b-167">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="82a0b-168">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x86**.</span><span class="sxs-lookup"><span data-stu-id="82a0b-168">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="82a0b-169">Klicken Sie auf den Dropdown Pfeil neben der Schaltfläche lokaler Computer, und wählen Sie **Remote Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="82a0b-169">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="82a0b-170">Geben Sie **die IP-Adresse des hololens-Geräts** ein, und legen Sie den Authentifizierungsmodus auf **Universal (unverschlüsseltes Protokoll)**</span><span class="sxs-lookup"><span data-stu-id="82a0b-170">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="82a0b-171">Klicken Sie auf **Auswählen**.</span><span class="sxs-lookup"><span data-stu-id="82a0b-171">Click **Select**.</span></span> <span data-ttu-id="82a0b-172">Wenn Sie die IP-Adresse Ihres Geräts nicht kennen, suchen Sie unter **Einstellungen > Netzwerk & Internet > Erweiterte Optionen**.</span><span class="sxs-lookup"><span data-stu-id="82a0b-172">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="82a0b-173">Klicken Sie in der oberen Menüleiste auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="82a0b-173">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="82a0b-174">Wenn Sie die Bereitstellung auf Ihrem Gerät zum ersten Mal durchführt, müssen Sie [es mit Visual Studio](using-visual-studio.md#pairing-your-device)koppeln.</span><span class="sxs-lookup"><span data-stu-id="82a0b-174">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="82a0b-175">Wenn die APP bereitgestellt wurde, schließen Sie das **fitbox** -Gerät mit einer **Auswahl Bewegung**ab.</span><span class="sxs-lookup"><span data-stu-id="82a0b-175">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="82a0b-176">Bei der Bereitstellung auf einem immersiven Headset:</span><span class="sxs-lookup"><span data-stu-id="82a0b-176">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="82a0b-177">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x64**.</span><span class="sxs-lookup"><span data-stu-id="82a0b-177">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="82a0b-178">Stellen Sie sicher, dass das Bereitstellungs Ziel auf **lokaler Computer**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="82a0b-178">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="82a0b-179">Klicken Sie in der oberen Menüleiste auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="82a0b-179">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="82a0b-180">Wenn die APP bereitgestellt wurde, schließen Sie die Funktion **, indem Sie den-** Typ auf einen Bewegungs Controller ziehen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-180">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="82a0b-181">Im Visual Studio-Fehler Panel werden möglicherweise einige rote Fehler feststellen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-181">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="82a0b-182">Es ist sicher, Sie zu ignorieren.</span><span class="sxs-lookup"><span data-stu-id="82a0b-182">It is safe to ignore them.</span></span> <span data-ttu-id="82a0b-183">Wechseln Sie zum Ausgabebereich, um den tatsächlichen buildfortschritt anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-183">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="82a0b-184">Fehler im Ausgabe Panel erfordern eine Korrektur (meistens werden Sie durch einen Fehler in einem Skript verursacht).</span><span class="sxs-lookup"><span data-stu-id="82a0b-184">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="82a0b-185">Kapitel 1: Hand erkanntes Feedback</span><span class="sxs-lookup"><span data-stu-id="82a0b-185">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="82a0b-186">Ziele</span><span class="sxs-lookup"><span data-stu-id="82a0b-186">Objectives</span></span>

* <span data-ttu-id="82a0b-187">Hiermit werden die Hand Verfolgungs Ereignisse abonniert.</span><span class="sxs-lookup"><span data-stu-id="82a0b-187">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="82a0b-188">Mit Cursor Feedback können Sie Benutzer anzeigen, wenn eine Hand nachverfolgt wird.</span><span class="sxs-lookup"><span data-stu-id="82a0b-188">Use cursor feedback to show users when a hand is being tracked.</span></span>

>[!NOTE]
><span data-ttu-id="82a0b-189">Bei hololens 2 werden Hände erkannt, wenn die Hände sichtbar sind (nicht nur, wenn ein Finger nach oben zeigt).</span><span class="sxs-lookup"><span data-stu-id="82a0b-189">On HoloLens 2 , hands detected fires whenever hands are visible (not just when a finger is pointing up).</span></span>

### <a name="instructions"></a><span data-ttu-id="82a0b-190">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="82a0b-190">Instructions</span></span>

* <span data-ttu-id="82a0b-191">Erweitern Sie im Bereich **Hierarchie** das **InputManager** -Objekt.</span><span class="sxs-lookup"><span data-stu-id="82a0b-191">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="82a0b-192">Suchen Sie nach dem **gesturesinput** -Objekt, und wählen Sie es aus.</span><span class="sxs-lookup"><span data-stu-id="82a0b-192">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="82a0b-193">Das Skript **InteractionInputSource.cs** führt folgende Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="82a0b-193">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="82a0b-194">Abonniert das interaktionsourceerkannte-Ereignis und das interaktionsourcelost-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="82a0b-194">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="82a0b-195">Legt den handerkannten Zustand fest.</span><span class="sxs-lookup"><span data-stu-id="82a0b-195">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="82a0b-196">Abonniert die Ereignisse interaktionsourceerkannte und interaktionsourcelost.</span><span class="sxs-lookup"><span data-stu-id="82a0b-196">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="82a0b-197">Als nächstes aktualisieren wir den Cursor von der [Mr-Eingabe 210](holograms-210.md) in einen, der das Feedback abhängig von den Aktionen des Benutzers anzeigt.</span><span class="sxs-lookup"><span data-stu-id="82a0b-197">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="82a0b-198">Wählen Sie im Bereich **Hierarchie** das **Cursor** Objekt aus, und löschen Sie es.</span><span class="sxs-lookup"><span data-stu-id="82a0b-198">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="82a0b-199">Suchen Sie im **Projekt** Panel nach **currsorwithfeedback** , und ziehen Sie es in den Bereich **Hierarchie** .</span><span class="sxs-lookup"><span data-stu-id="82a0b-199">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="82a0b-200">Klicken Sie im **Hierarchie** Panel auf **InputManager** , und ziehen Sie dann das **cursorwithfeedback** -Objekt aus der **Hierarchie** in das **Cursor** Feld " **simplesinglepointerselector**" von InputManager am unteren Rand des **Inspektor**.</span><span class="sxs-lookup"><span data-stu-id="82a0b-200">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="82a0b-201">Klicken Sie in der **Hierarchie**auf das **Cursor-Feedback** .</span><span class="sxs-lookup"><span data-stu-id="82a0b-201">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="82a0b-202">Erweitern Sie im **Inspektor** -Panel **Cursor Zustandsdaten** für das **Objekt Cursor** Skript.</span><span class="sxs-lookup"><span data-stu-id="82a0b-202">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="82a0b-203">Die **Cursor Zustandsdaten** funktionieren wie folgt:</span><span class="sxs-lookup"><span data-stu-id="82a0b-203">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="82a0b-204">Jeder Status der Überprüfung bedeutet, **dass keine Hand** erkannt wird und der Benutzer einfach eine Suche durchführt.</span><span class="sxs-lookup"><span data-stu-id="82a0b-204">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="82a0b-205">Jeder **Interaktions** Zustand bedeutet, dass eine Hand oder ein Controller erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="82a0b-205">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="82a0b-206">Jeder **Hover** -Zustand bedeutet, dass der Benutzer ein Hologram ansieht.</span><span class="sxs-lookup"><span data-stu-id="82a0b-206">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="82a0b-207">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="82a0b-207">Build and Deploy</span></span>

* <span data-ttu-id="82a0b-208">Verwenden Sie in Unity **Datei > Buildeinstellungen** , um die Anwendung neu zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-208">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="82a0b-209">Öffnen Sie den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="82a0b-209">Open the **App** folder.</span></span>
* <span data-ttu-id="82a0b-210">Öffnen Sie die Visual Studio-Projekt Mappe **Model Explorer**, wenn Sie nicht bereits geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="82a0b-210">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="82a0b-211">(Wenn Sie dieses Projekt bereits während der Einrichtung in Visual Studio erstellt bzw. bereitgestellt haben, können Sie diese Instanz von Visual Studio öffnen und auf "alles neu laden" klicken).</span><span class="sxs-lookup"><span data-stu-id="82a0b-211">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="82a0b-212">Klicken Sie in Visual Studio auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="82a0b-212">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="82a0b-213">Nachdem die Anwendung in den hololens bereitgestellt wurde, schließen Sie die fitbox mithilfe der Tastenkombination.</span><span class="sxs-lookup"><span data-stu-id="82a0b-213">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="82a0b-214">Bewegen Sie die Hand in die Anzeige, und zeigen Sie den Finger des Indexes auf den Himmel, um die Hand Verfolgung zu starten</span><span class="sxs-lookup"><span data-stu-id="82a0b-214">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="82a0b-215">Bewegen Sie Ihre Hand nach links, nach rechts, nach oben und unten.</span><span class="sxs-lookup"><span data-stu-id="82a0b-215">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="82a0b-216">Sehen Sie sich an, wie sich der Cursor ändert, wenn Ihre Hand erkannt wird, und dann in der Ansicht verloren</span><span class="sxs-lookup"><span data-stu-id="82a0b-216">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="82a0b-217">Wenn Sie sich auf einem immersiven Headset befinden, müssen Sie eine Verbindung herstellen und den Controller trennen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-217">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="82a0b-218">Dieses Feedback wird auf einem immersiven Gerät weniger interessant, da ein verbundener Controller immer "verfügbar" ist.</span><span class="sxs-lookup"><span data-stu-id="82a0b-218">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="82a0b-219">Kapitel 2: Navigation</span><span class="sxs-lookup"><span data-stu-id="82a0b-219">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="82a0b-220">Ziele</span><span class="sxs-lookup"><span data-stu-id="82a0b-220">Objectives</span></span>

* <span data-ttu-id="82a0b-221">Verwenden Sie Navigations Gesten Ereignisse, um den Astronaut zu drehen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-221">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="82a0b-222">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="82a0b-222">Instructions</span></span>

<span data-ttu-id="82a0b-223">Um Navigations Gesten in unserer APP zu verwenden, bearbeiten wir **GestureAction.cs** , um Objekte zu drehen, wenn die Navigations Bewegung auftritt.</span><span class="sxs-lookup"><span data-stu-id="82a0b-223">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="82a0b-224">Außerdem wird dem Cursor Feedback hinzugefügt, das angezeigt wird, wenn die Navigation verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="82a0b-224">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="82a0b-225">Erweitern Sie im Bereich **Hierarchie** den Eintrag **Cursor-Feedback**.</span><span class="sxs-lookup"><span data-stu-id="82a0b-225">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="82a0b-226">Suchen Sie im Ordner **holograms** das **scrollfeedback** -Medienobjekt.</span><span class="sxs-lookup"><span data-stu-id="82a0b-226">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="82a0b-227">Ziehen Sie die **scrollfeedback** -vorfab per Drag & amp; Drop auf das **Cursor** Objekt in der **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="82a0b-227">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="82a0b-228">Klicken Sie auf **currsorwithfeedback**.</span><span class="sxs-lookup"><span data-stu-id="82a0b-228">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="82a0b-229">Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="82a0b-229">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="82a0b-230">Geben Sie im Menü den Suchbegriff **Cursor Feedback**ein.</span><span class="sxs-lookup"><span data-stu-id="82a0b-230">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="82a0b-231">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="82a0b-231">Select the search result.</span></span>
7. <span data-ttu-id="82a0b-232">Ziehen Sie das **scrollfeedback** -Objekt mithilfe von Drag & amp; Drop aus der- **Hierarchie** in der **Cursor-Feedback** Komponente des **Inspektors**auf die Eigenschaft Bild Lauf **Erkennung erkannt**</span><span class="sxs-lookup"><span data-stu-id="82a0b-232">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="82a0b-233">Wählen Sie im Bereich **Hierarchie** das Objekt **Astroman** aus.</span><span class="sxs-lookup"><span data-stu-id="82a0b-233">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="82a0b-234">Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="82a0b-234">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="82a0b-235">Geben Sie im Menü die Aktion in der **Aktion**Suchfeld ein.</span><span class="sxs-lookup"><span data-stu-id="82a0b-235">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="82a0b-236">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="82a0b-236">Select the search result.</span></span>

<span data-ttu-id="82a0b-237">Öffnen Sie als nächstes **GestureAction.cs** in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="82a0b-237">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="82a0b-238">Bearbeiten Sie in der Codierungs Übung 2. c das Skript, um Folgendes durchzuführen:</span><span class="sxs-lookup"><span data-stu-id="82a0b-238">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="82a0b-239">**Drehen Sie das Astroman** -Objekt immer dann, wenn eine Navigations Geste ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="82a0b-239">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="82a0b-240">Berechnen Sie den " **rotationfactor** ", um die auf das Objekt angewendete Drehung zu steuern.</span><span class="sxs-lookup"><span data-stu-id="82a0b-240">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="82a0b-241">**Drehen Sie das Objekt** um die y-Achse, wenn der Benutzer seine Hand nach links oder rechts verschiebt.</span><span class="sxs-lookup"><span data-stu-id="82a0b-241">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="82a0b-242">Vervollständigen Sie die Codierungs Übungen 2. c im Skript, oder ersetzen Sie den Code durch die folgende abgeschlossene Lösung:</span><span class="sxs-lookup"><span data-stu-id="82a0b-242">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

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

<span data-ttu-id="82a0b-243">Sie werden feststellen, dass die anderen Navigations Ereignisse bereits mit einigen Informationen ausgefüllt sind.</span><span class="sxs-lookup"><span data-stu-id="82a0b-243">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="82a0b-244">Wir schieben das gameobject-Objekt auf den modalen Stapel des Toolkits, sodass der Benutzer den Fokus nicht mehr auf dem Astronaut behalten muss, sobald die Drehung begonnen hat.</span><span class="sxs-lookup"><span data-stu-id="82a0b-244">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="82a0b-245">Dementsprechend wird das gameobject aus dem Stapel entfernt, sobald die Geste abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="82a0b-245">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="82a0b-246">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="82a0b-246">Build and Deploy</span></span>

1. <span data-ttu-id="82a0b-247">Erstellen Sie die Anwendung in Unity neu, erstellen Sie Sie, und stellen Sie Sie aus Visual Studio bereit, um Sie in den hololens auszuführen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-247">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="82a0b-248">Blick auf den Astronaut, zwei Pfeile sollten auf beiden Seiten des Cursors angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="82a0b-248">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="82a0b-249">Dieses neue visuelle Element gibt an, dass der Astronaut gedreht werden kann.</span><span class="sxs-lookup"><span data-stu-id="82a0b-249">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="82a0b-250">Legen Sie die Hand an der Position an der Position (Index fingerbild, die auf den Himmel zeigt), sodass die hololens Ihre Hand nachverfolgen werden.</span><span class="sxs-lookup"><span data-stu-id="82a0b-250">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="82a0b-251">Um den Astronaut zu drehen, verringern Sie den Finger des Indexes an eine Position, und verschieben Sie dann die Hand nach links oder rechts, um die navigationx-Geste zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="82a0b-251">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="82a0b-252">Kapitel 3-Hand-Anleitungen</span><span class="sxs-lookup"><span data-stu-id="82a0b-252">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="82a0b-253">Ziele</span><span class="sxs-lookup"><span data-stu-id="82a0b-253">Objectives</span></span>

* <span data-ttu-id="82a0b-254">Verwenden Sie die **Hand Leit Faden Bewertung** , um vorherzusagen, wann die Hand Verfolgung verloren geht.</span><span class="sxs-lookup"><span data-stu-id="82a0b-254">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="82a0b-255">Geben Sie **Feedback zu dem Cursor** an, der angezeigt wird, wenn die Hand des Benutzers den Rand der Ansicht der Kamera anzeigt.</span><span class="sxs-lookup"><span data-stu-id="82a0b-255">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="82a0b-256">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="82a0b-256">Instructions</span></span>

1. <span data-ttu-id="82a0b-257">Wählen Sie im Bereich **Hierarchie** das **Cursor** -Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="82a0b-257">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="82a0b-258">Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="82a0b-258">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="82a0b-259">Geben Sie im Menü den **Hand Leit Faden**für das Suchfeld ein.</span><span class="sxs-lookup"><span data-stu-id="82a0b-259">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="82a0b-260">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="82a0b-260">Select the search result.</span></span>
4. <span data-ttu-id="82a0b-261">Suchen Sie im **Projekt** Panel **holograms** -Ordner das **handguidancefeedback** -Asset.</span><span class="sxs-lookup"><span data-stu-id="82a0b-261">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="82a0b-262">Ziehen Sie das Objekt **handguidancefeedback** per Drag & Drop auf die Eigenschaft **Hand Leit Faden Anzeige** im **Inspektor** -Panel.</span><span class="sxs-lookup"><span data-stu-id="82a0b-262">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="82a0b-263">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="82a0b-263">Build and Deploy</span></span>

* <span data-ttu-id="82a0b-264">Erstellen Sie die Anwendung in Unity neu, erstellen Sie Sie in Visual Studio, und stellen Sie Sie bereit, um die APP auf hololens zu erleben</span><span class="sxs-lookup"><span data-stu-id="82a0b-264">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="82a0b-265">Zeigen Sie Ihre Hand an, und heben Sie den Index Finger auf, um nachverfolgt zu werden.</span><span class="sxs-lookup"><span data-stu-id="82a0b-265">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="82a0b-266">Beginnen Sie mit dem Drehen des Astronauten mit der Navigations Bewegung (drücken Sie den Finger und den Ziehpunkt des Indexes zusammen).</span><span class="sxs-lookup"><span data-stu-id="82a0b-266">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="82a0b-267">Verschieben Sie Ihre Hand ganz nach links, nach rechts, nach oben und nach unten.</span><span class="sxs-lookup"><span data-stu-id="82a0b-267">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="82a0b-268">Wenn die Kante des Gesten Rahmens in der Hand dargestellt wird, sollte neben dem Cursor ein Pfeil angezeigt werden, der Sie darüber informiert, dass die Hand Verfolgung verloren geht.</span><span class="sxs-lookup"><span data-stu-id="82a0b-268">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="82a0b-269">Der Pfeil gibt die Richtung an, in der die Hand bewegt werden soll, um zu verhindern, dass die Überwachung verloren geht.</span><span class="sxs-lookup"><span data-stu-id="82a0b-269">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="82a0b-270">Kapitel 4: Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="82a0b-270">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="82a0b-271">Ziele</span><span class="sxs-lookup"><span data-stu-id="82a0b-271">Objectives</span></span>

* <span data-ttu-id="82a0b-272">Verwenden Sie Manipulations Ereignisse, um den Astronaut mit ihren Händen zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="82a0b-272">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="82a0b-273">Geben Sie Feedback für den Cursor an, damit der Benutzer weiß, wann die Bearbeitung verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="82a0b-273">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="82a0b-274">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="82a0b-274">Instructions</span></span>

<span data-ttu-id="82a0b-275">Mit GestureManager.cs und AstronautManager.cs können wir folgende Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="82a0b-275">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="82a0b-276">Verwenden Sie das Speech-Schlüsselwort "**Move Astronaut**", um **Manipulations** Gesten zu aktivieren und "**Astronaut**" zu deaktivieren, um Sie zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="82a0b-276">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="82a0b-277">Wechseln Sie zur Reaktion auf die **Erkennungs Gestenerkennung**.</span><span class="sxs-lookup"><span data-stu-id="82a0b-277">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="82a0b-278">Los geht's.</span><span class="sxs-lookup"><span data-stu-id="82a0b-278">Let's get started.</span></span>

1. <span data-ttu-id="82a0b-279">Erstellen Sie im **Hierarchie** Panel ein neues leeres gameobject-Objekt.</span><span class="sxs-lookup"><span data-stu-id="82a0b-279">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="82a0b-280">Nennen Sie es "**astronautmanager**".</span><span class="sxs-lookup"><span data-stu-id="82a0b-280">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="82a0b-281">Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="82a0b-281">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="82a0b-282">Geben Sie im Menü im Suchfeld den Suchbegriff " **Astronaut Manager**" ein.</span><span class="sxs-lookup"><span data-stu-id="82a0b-282">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="82a0b-283">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="82a0b-283">Select the search result.</span></span>
4. <span data-ttu-id="82a0b-284">Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="82a0b-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="82a0b-285">Geben Sie im Menü die **Eingabe Quelle**für die Suchbegriff Sprache ein.</span><span class="sxs-lookup"><span data-stu-id="82a0b-285">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="82a0b-286">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="82a0b-286">Select the search result.</span></span>

<span data-ttu-id="82a0b-287">Nun fügen wir die Sprachbefehle hinzu, die erforderlich sind, um den Interaktions Zustand des Astronauten zu steuern.</span><span class="sxs-lookup"><span data-stu-id="82a0b-287">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="82a0b-288">Erweitern Sie im **Inspektor**den Abschnitt **Schlüsselwörter** .</span><span class="sxs-lookup"><span data-stu-id="82a0b-288">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="82a0b-289">Klicken Sie auf die **+** auf der rechten Seite, um ein neues Schlüsselwort hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-289">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="82a0b-290">Geben Sie das Schlüsselwort als **Move Astronaut**ein.</span><span class="sxs-lookup"><span data-stu-id="82a0b-290">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="82a0b-291">Wenn gewünscht, können Sie eine Tastenkombination hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-291">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="82a0b-292">Klicken Sie auf die **+** auf der rechten Seite, um ein neues Schlüsselwort hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-292">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="82a0b-293">Geben Sie das Schlüsselwort zum **Drehen des Astronauten**ein.</span><span class="sxs-lookup"><span data-stu-id="82a0b-293">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="82a0b-294">Wenn gewünscht, können Sie eine Tastenkombination hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-294">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="82a0b-295">Der entsprechende Handlercode finden Sie in **GestureAction.cs**im **iredner Handler. onredner keywordrecognized** -Handler.</span><span class="sxs-lookup"><span data-stu-id="82a0b-295">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![Einrichten der Spracheingabe Quelle für Kapitel 4](images/holograms211-speech.png)

<span data-ttu-id="82a0b-297">Als nächstes richten wir das Manipulations Feedback für den Cursor ein.</span><span class="sxs-lookup"><span data-stu-id="82a0b-297">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="82a0b-298">Suchen Sie im **Projekt** Panel **holograms** -Ordner das **pathingfeedback** -Asset.</span><span class="sxs-lookup"><span data-stu-id="82a0b-298">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="82a0b-299">Ziehen Sie die vorfab **pathingfeedback** per Drag & amp; Drop auf das **Cursor** Objekt in der **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="82a0b-299">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="82a0b-300">Klicken Sie im **Hierarchie** Panel auf " **Cursor**".</span><span class="sxs-lookup"><span data-stu-id="82a0b-300">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="82a0b-301">Ziehen Sie das **pathingfeedback** -Objekt per Drag & amp; Drop aus der- **Hierarchie** auf die Eigenschaft für die Eigenschaft "" **für das** **festgelegte Spiel** im **Inspektor**.</span><span class="sxs-lookup"><span data-stu-id="82a0b-301">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="82a0b-302">Nun müssen Sie **GestureAction.cs** Code hinzufügen, um Folgendes zu ermöglichen:</span><span class="sxs-lookup"><span data-stu-id="82a0b-302">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="82a0b-303">Fügen Sie der **imanipulationhandler. onmanipulationaktualisierte** -Funktion Code hinzu, mit dem der Astronaut verschoben wird, wenn eine **Manipulations** Bewegung erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="82a0b-303">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="82a0b-304">Berechnen Sie den **Bewegungsvektor** , um zu bestimmen, an welcher Stelle der Astronaut auf der Grundlage der Handposition verschoben werden soll.</span><span class="sxs-lookup"><span data-stu-id="82a0b-304">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="82a0b-305">**Verschieben** Sie den Astronauten an die neue Position.</span><span class="sxs-lookup"><span data-stu-id="82a0b-305">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="82a0b-306">Vervollständigen Sie die Codierungs Übung 4. a in **GestureAction.cs**, oder verwenden Sie unten unsere abgeschlossene Lösung:</span><span class="sxs-lookup"><span data-stu-id="82a0b-306">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

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

### <a name="build-and-deploy"></a><span data-ttu-id="82a0b-307">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="82a0b-307">Build and Deploy</span></span>

* <span data-ttu-id="82a0b-308">Erstellen Sie in Unity neu, und erstellen Sie Sie aus Visual Studio, um die app in hololens auszuführen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-308">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="82a0b-309">Bewegen Sie Ihre Hand vor den hololens, und erhöhen Sie den Indexfinger, damit er nachverfolgt werden kann.</span><span class="sxs-lookup"><span data-stu-id="82a0b-309">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="82a0b-310">Fokussieren Sie den Cursor auf den Astronaut.</span><span class="sxs-lookup"><span data-stu-id="82a0b-310">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="82a0b-311">Nehmen Sie an, Sie können den Astronauten mit einer Manipulations Bewegung verschieben.</span><span class="sxs-lookup"><span data-stu-id="82a0b-311">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="82a0b-312">Im Cursor sollten vier Pfeile angezeigt werden, um anzugeben, dass das Programm nun auf Manipulations Ereignisse antwortet.</span><span class="sxs-lookup"><span data-stu-id="82a0b-312">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="82a0b-313">Verringern Sie den Finger des Indexes auf Ihren Ziehpunkt, und halten Sie ihn zusammen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-313">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="82a0b-314">Wenn Sie die Hand herum bewegen, wird der Astronaut ebenfalls verschoben (Dies ist eine Bearbeitung).</span><span class="sxs-lookup"><span data-stu-id="82a0b-314">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="82a0b-315">Erhöhen Sie den Finger des Indexes, um die Bearbeitung des Astronauten zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="82a0b-315">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="82a0b-316">Hinweis: Wenn Sie "Move Astronaut" nicht vor Hand bewegen, wird stattdessen die Navigations Geste verwendet.</span><span class="sxs-lookup"><span data-stu-id="82a0b-316">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="82a0b-317">Nehmen wir an, dass Sie den "Astronaut" drehen, um zum rotatable-Status zurück</span><span class="sxs-lookup"><span data-stu-id="82a0b-317">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="82a0b-318">Kapitel 5: Modell Erweiterung</span><span class="sxs-lookup"><span data-stu-id="82a0b-318">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="82a0b-319">Ziele</span><span class="sxs-lookup"><span data-stu-id="82a0b-319">Objectives</span></span>

* <span data-ttu-id="82a0b-320">Erweitern Sie das Modell "Astronaut" in mehrere kleinere Teile, mit denen der Benutzer interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="82a0b-320">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="82a0b-321">Verschieben Sie jedes Stück einzeln mithilfe von Navigations-und Bearbeitungs Gesten.</span><span class="sxs-lookup"><span data-stu-id="82a0b-321">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="82a0b-322">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="82a0b-322">Instructions</span></span>

<span data-ttu-id="82a0b-323">In diesem Abschnitt werden die folgenden Aufgaben ausgeführt:</span><span class="sxs-lookup"><span data-stu-id="82a0b-323">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="82a0b-324">Fügen Sie ein neues Schlüsselwort "**Expand Model**" hinzu, um das Modell des Astronauten zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="82a0b-324">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="82a0b-325">Fügen Sie ein neues Schlüsselwort "**Modell zurücksetzen**" hinzu, um das Modell in seine ursprüngliche Form zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="82a0b-325">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="82a0b-326">Hierzu fügen wir der Spracheingabe Quelle aus dem vorherigen Kapitel zwei weitere Schlüsselwörter hinzu.</span><span class="sxs-lookup"><span data-stu-id="82a0b-326">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="82a0b-327">Wir veranschaulichen auch eine weitere Möglichkeit, Erkennungs Ereignisse zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="82a0b-327">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="82a0b-328">Klicken Sie im **Inspektor** auf " **astronautmanager** ", und erweitern Sie im **Inspektor**den Abschnitt " **Schlüsselwörter** ".</span><span class="sxs-lookup"><span data-stu-id="82a0b-328">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="82a0b-329">Klicken Sie auf die **+** auf der rechten Seite, um ein neues Schlüsselwort hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-329">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="82a0b-330">Geben Sie das Schlüsselwort als Erweiterungs **Modell**ein.</span><span class="sxs-lookup"><span data-stu-id="82a0b-330">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="82a0b-331">Wenn gewünscht, können Sie eine Tastenkombination hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-331">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="82a0b-332">Klicken Sie auf die **+** auf der rechten Seite, um ein neues Schlüsselwort hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-332">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="82a0b-333">Geben Sie das Schlüsselwort als **Modell zurücksetzen**ein.</span><span class="sxs-lookup"><span data-stu-id="82a0b-333">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="82a0b-334">Wenn gewünscht, können Sie eine Tastenkombination hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-334">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="82a0b-335">Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="82a0b-335">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="82a0b-336">Geben Sie im Menü den **Eingabe Handler**für die Suchbegriff Sprache ein.</span><span class="sxs-lookup"><span data-stu-id="82a0b-336">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="82a0b-337">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="82a0b-337">Select the search result.</span></span>
8. <span data-ttu-id="82a0b-338">Überprüfen Sie, ob es sich um einen **globalen Listener handelt**, da Sie möchten, dass diese Befehle unabhängig vom verwendeten gameobject funktionieren.</span><span class="sxs-lookup"><span data-stu-id="82a0b-338">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="82a0b-339">Klicken Sie auf die Schaltfläche **+** , und wählen Sie Modell aus der Dropdown Liste Schlüsselwort **erweitern**</span><span class="sxs-lookup"><span data-stu-id="82a0b-339">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="82a0b-340">Klicken Sie unter Antwort auf die **+** , und ziehen Sie den Wert von **astronautmanager** aus der **Hierarchie** in das Feld **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="82a0b-340">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="82a0b-341">Klicken Sie nun auf die Dropdown Liste **keine Funktion** , und wählen Sie dann " **astronautmanager**" und " **expandmodelcommand**"</span><span class="sxs-lookup"><span data-stu-id="82a0b-341">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="82a0b-342">Klicken Sie auf die **+** Schaltfläche des Spracheingabe Handlers, und wählen Sie aus der Dropdown Liste Schlüsselwort **zurück**</span><span class="sxs-lookup"><span data-stu-id="82a0b-342">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="82a0b-343">Klicken Sie unter Antwort auf die **+** , und ziehen Sie den Wert von **astronautmanager** aus der **Hierarchie** in das Feld **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="82a0b-343">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="82a0b-344">Klicken Sie nun auf die Dropdown Liste **keine Funktion** , und wählen Sie dann " **astronautmanager**" und dann " **resetmodelcommand**"</span><span class="sxs-lookup"><span data-stu-id="82a0b-344">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![Einrichten der Spracheingabe Quelle und des Handlers für Kapitel 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="82a0b-346">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="82a0b-346">Build and Deploy</span></span>

* <span data-ttu-id="82a0b-347">Probieren Sie es aus!</span><span class="sxs-lookup"><span data-stu-id="82a0b-347">Try it!</span></span> <span data-ttu-id="82a0b-348">Erstellen Sie die APP, und stellen Sie Sie in den hololens bereit.</span><span class="sxs-lookup"><span data-stu-id="82a0b-348">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="82a0b-349">Beispiel: **Erweitern Sie Modell** , um das erweiterte Modell des Astronauten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-349">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="82a0b-350">Verwenden Sie die **Navigation** , um einzelne Teile der astronautenfarbe zu drehen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-350">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="82a0b-351">Nehmen Sie an, Sie können den **Astronauten verschieben** und dann die **Bearbeitung** verwenden, um einzelne Teile des Astronauten zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="82a0b-351">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="82a0b-352">Nehmen Sie an, Sie können den **Astronauten rotieren** , um die Teile</span><span class="sxs-lookup"><span data-stu-id="82a0b-352">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="82a0b-353">Nehmen Sie beispielsweise **Reset Model** an, um den Astronaut an seine ursprüngliche Form zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="82a0b-353">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="82a0b-354">Das Ende</span><span class="sxs-lookup"><span data-stu-id="82a0b-354">The End</span></span>

<span data-ttu-id="82a0b-355">Gratulation!</span><span class="sxs-lookup"><span data-stu-id="82a0b-355">Congratulations!</span></span> <span data-ttu-id="82a0b-356">Sie haben nun die **Eingabe 211: Geste**abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="82a0b-356">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="82a0b-357">Sie wissen, wie Hand Verfolgungs-, Navigations-und Bearbeitungs Ereignisse erkannt und beantwortet werden.</span><span class="sxs-lookup"><span data-stu-id="82a0b-357">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="82a0b-358">Sie verstehen den Unterschied zwischen Navigation und Manipulations Gesten.</span><span class="sxs-lookup"><span data-stu-id="82a0b-358">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="82a0b-359">Sie wissen, wie Sie den Cursor so ändern können, dass er visuelles Feedback bereitstellt, wenn eine Hand entdeckt wird, wenn eine Hand verloren geht, und für den Fall, dass ein Objekt verschiedene Interaktionen unterstützt (Navigation und Bearbeitung).</span><span class="sxs-lookup"><span data-stu-id="82a0b-359">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>
