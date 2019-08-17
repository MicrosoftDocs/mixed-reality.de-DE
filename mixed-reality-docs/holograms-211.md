---
title: Mr-Eingabe 211-Geste
description: Befolgen Sie diese exemplarische Vorgehensweise für die Codierung mithilfe von Unity, Visual Studio und hololens, um die Details der Gesten Konzepte zu erlernen.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, Tutorial, Geste
ms.openlocfilehash: 694f51f1b56588e100d6d2676a8194d7e9936133
ms.sourcegitcommit: e9a55528965048ce34f8247ef6e544f9f432ee37
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69559885"
---
>[!NOTE]
><span data-ttu-id="871a8-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="871a8-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="871a8-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="871a8-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="871a8-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="871a8-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="871a8-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="871a8-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="871a8-108">Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="871a8-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="871a8-109">Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="871a8-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-211-gesture"></a><span data-ttu-id="871a8-110">Mr-Eingabe 211: Geste</span><span class="sxs-lookup"><span data-stu-id="871a8-110">MR Input 211: Gesture</span></span>

<span data-ttu-id="871a8-111">[Gesten](gestures.md) verwandeln die Benutzer Absicht in eine Aktion.</span><span class="sxs-lookup"><span data-stu-id="871a8-111">[Gestures](gestures.md) turn user intention into action.</span></span> <span data-ttu-id="871a8-112">Mit Gesten können Benutzer mit holograms interagieren.</span><span class="sxs-lookup"><span data-stu-id="871a8-112">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="871a8-113">In diesem Kurs erfahren Sie, wie Sie die Hände des Benutzers nachverfolgen, auf Benutzereingaben reagieren und dem Benutzer Feedback geben können, der auf dem Hand Bundesland und-Speicherort basiert.</span><span class="sxs-lookup"><span data-stu-id="871a8-113">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="871a8-114">In den [Grundlagen 101](holograms-101.md)haben wir eine einfache Air-Tap-Geste verwendet, um mit unseren holograms zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="871a8-114">In [MR Basics 101](holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="871a8-115">Nun gehen wir über die Luft tippen Bewegung hinaus und erforschen neue Konzepte für Folgendes:</span><span class="sxs-lookup"><span data-stu-id="871a8-115">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="871a8-116">Erkennen, wenn die Hand des Benutzers nachverfolgt wird, und Senden von Feedback an den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="871a8-116">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="871a8-117">Verwenden Sie eine Navigations Geste, um unsere Hologramme zu drehen.</span><span class="sxs-lookup"><span data-stu-id="871a8-117">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="871a8-118">Geben Sie uns Feedback, wenn der Benutzer die Hand verlässt.</span><span class="sxs-lookup"><span data-stu-id="871a8-118">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="871a8-119">Verwenden Sie Manipulations Ereignisse, um Benutzern das Verschieben von holograms mit ihren Händen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="871a8-119">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="871a8-120">In diesem Kurs besuchen wir den Unity-Projekt **Modell-Explorer**, den wir in der [Eingabe 210](holograms-210.md)erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="871a8-120">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="871a8-121">Unser Astronauten Freund ist zurück, um uns bei der Untersuchung dieser neuen Gesten Konzepte zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="871a8-121">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="871a8-122">Die in den folgenden Kapiteln eingebetteten Videos wurden mit einer älteren Version von Unity und dem Mixed Reality Toolkit aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="871a8-122">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="871a8-123">Die Schritt-für-Schritt-Anweisungen sind genau und aktuell, aber es werden möglicherweise Skripts und Visualisierungen in den entsprechenden Videos angezeigt, die veraltet sind.</span><span class="sxs-lookup"><span data-stu-id="871a8-123">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="871a8-124">Die Videos bleiben in der einwelt enthalten und werden weiterhin angewendet.</span><span class="sxs-lookup"><span data-stu-id="871a8-124">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="871a8-125">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="871a8-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="871a8-126">Natürlich</span><span class="sxs-lookup"><span data-stu-id="871a8-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="871a8-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="871a8-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="871a8-128"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="871a8-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="871a8-129">Mr-Eingabe 211: Geste</span><span class="sxs-lookup"><span data-stu-id="871a8-129">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="871a8-130">✔️</span><span class="sxs-lookup"><span data-stu-id="871a8-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="871a8-131">✔️</span><span class="sxs-lookup"><span data-stu-id="871a8-131">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="871a8-132">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="871a8-132">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="871a8-133">Erforderliche Komponenten</span><span class="sxs-lookup"><span data-stu-id="871a8-133">Prerequisites</span></span>

* <span data-ttu-id="871a8-134">Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md)konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="871a8-134">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="871a8-135">Einige Grund C# Legende Programmiermöglichkeiten.</span><span class="sxs-lookup"><span data-stu-id="871a8-135">Some basic C# programming ability.</span></span>
* <span data-ttu-id="871a8-136">Sie sollten die [Grundlagen von 101](holograms-101.md)abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="871a8-136">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="871a8-137">Sie sollten die [Mr-Eingabe 210](holograms-210.md)abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="871a8-137">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="871a8-138">Ein hololens-Gerät, das [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode)ist.</span><span class="sxs-lookup"><span data-stu-id="871a8-138">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="871a8-139">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="871a8-139">Project files</span></span>

* <span data-ttu-id="871a8-140">Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) , die für das Projekt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="871a8-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span><span data-ttu-id="871a8-141"> Erfordert Unity 2017,2 oder höher.</span><span class="sxs-lookup"><span data-stu-id="871a8-141"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="871a8-142">Deinstallieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht zugänglichen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="871a8-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="871a8-143">Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span><span class="sxs-lookup"><span data-stu-id="871a8-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="871a8-144">Errata und Notizen</span><span class="sxs-lookup"><span data-stu-id="871a8-144">Errata and Notes</span></span>

* <span data-ttu-id="871a8-145">"Enable nur eigenen Code" muss in Visual Studio unter"Extras-> Optionen" deaktiviert werden (> Debuggen, um Breakpoints im Code zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="871a8-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="871a8-146">Kapitel 0: Einrichtung von Unity</span><span class="sxs-lookup"><span data-stu-id="871a8-146">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="871a8-147">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="871a8-147">Instructions</span></span>

1. <span data-ttu-id="871a8-148">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="871a8-148">Start Unity.</span></span>
2. <span data-ttu-id="871a8-149">Wählen Sie **Öffnen**aus.</span><span class="sxs-lookup"><span data-stu-id="871a8-149">Select **Open**.</span></span>
3. <span data-ttu-id="871a8-150">Navigieren Sie zu dem **Gesten** Ordner, den Sie zuvor nicht archiviert haben.</span><span class="sxs-lookup"><span data-stu-id="871a8-150">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="871a8-151">Suchen und wählen Sie den **Start**/**Modell-Explorer** -Ordner aus.</span><span class="sxs-lookup"><span data-stu-id="871a8-151">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="871a8-152">Klicken Sie auf die Schaltfläche **Ordner auswählen** .</span><span class="sxs-lookup"><span data-stu-id="871a8-152">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="871a8-153">Erweitern Sie im **Projekt** Panel den Ordner **Szenen** .</span><span class="sxs-lookup"><span data-stu-id="871a8-153">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="871a8-154">Doppelklicken Sie auf **Model Explorer** Scene, um es in Unity zu laden.</span><span class="sxs-lookup"><span data-stu-id="871a8-154">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="871a8-155">Erstellung</span><span class="sxs-lookup"><span data-stu-id="871a8-155">Building</span></span>

1. <span data-ttu-id="871a8-156">Wählen Sie in Unity **Datei >** Buildeinstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="871a8-156">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="871a8-157">Wenn **Szenen/Model Explorer** nicht in **Szenen im Build**aufgeführt ist, klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="871a8-157">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="871a8-158">Wenn Sie speziell für hololens entwickeln, legen Sie **Zielgerät** auf **hololens**fest.</span><span class="sxs-lookup"><span data-stu-id="871a8-158">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="871a8-159">Andernfalls sollten Sie es auf **jedem Gerät**belassen.</span><span class="sxs-lookup"><span data-stu-id="871a8-159">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="871a8-160">Stellen Sie sicher, dass der Buildtyp auf **D3D** und das **SDK** auf **Latest installiert** festgelegt ist (was SDK 16299 oder höher sein sollte).</span><span class="sxs-lookup"><span data-stu-id="871a8-160">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="871a8-161">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="871a8-161">Click **Build**.</span></span>
6. <span data-ttu-id="871a8-162">Erstellen Sie einen **neuen Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="871a8-162">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="871a8-163">Klicken Sie einfach auf den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="871a8-163">Single click the **App** folder.</span></span>
8. <span data-ttu-id="871a8-164">Klicken **Sie auf Ordner auswählen** , und Unity startet das Projekt für Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="871a8-164">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="871a8-165">Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="871a8-165">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="871a8-166">Öffnen Sie den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="871a8-166">Open the **App** folder.</span></span>
2. <span data-ttu-id="871a8-167">Öffnen Sie die Visual Studio-Projekt Mappe **Model Explorer**.</span><span class="sxs-lookup"><span data-stu-id="871a8-167">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="871a8-168">Bei der Bereitstellung in hololens:</span><span class="sxs-lookup"><span data-stu-id="871a8-168">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="871a8-169">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x86**.</span><span class="sxs-lookup"><span data-stu-id="871a8-169">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="871a8-170">Klicken Sie auf den Dropdown Pfeil neben der Schaltfläche lokaler Computer, und wählen Sie **Remote Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="871a8-170">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="871a8-171">Geben Sie **die IP-Adresse des hololens-Geräts** ein, und legen Sie den Authentifizierungsmodus auf **Universal (unverschlüsseltes Protokoll)**</span><span class="sxs-lookup"><span data-stu-id="871a8-171">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="871a8-172">Klicken Sie auf **Auswählen**.</span><span class="sxs-lookup"><span data-stu-id="871a8-172">Click **Select**.</span></span> <span data-ttu-id="871a8-173">Wenn Sie die IP-Adresse Ihres Geräts nicht kennen, suchen Sie unter **Einstellungen > Netzwerk & Internet > Erweiterte Optionen**.</span><span class="sxs-lookup"><span data-stu-id="871a8-173">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="871a8-174">Klicken Sie in der oberen Menüleiste auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="871a8-174">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="871a8-175">Wenn Sie die Bereitstellung auf Ihrem Gerät zum ersten Mal durchführt, müssen Sie [es mit Visual Studio](using-visual-studio.md#pairing-your-device-hololens)koppeln.</span><span class="sxs-lookup"><span data-stu-id="871a8-175">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="871a8-176">Wenn die APP bereitgestellt wurde, schließen Sie das **fitbox** -Gerät mit einer **Auswahl Bewegung**ab.</span><span class="sxs-lookup"><span data-stu-id="871a8-176">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="871a8-177">Bei der Bereitstellung auf einem immersiven Headset:</span><span class="sxs-lookup"><span data-stu-id="871a8-177">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="871a8-178">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x64**.</span><span class="sxs-lookup"><span data-stu-id="871a8-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="871a8-179">Stellen Sie sicher, dass das Bereitstellungs Ziel auf **lokaler Computer**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="871a8-179">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="871a8-180">Klicken Sie in der oberen Menüleiste auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="871a8-180">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="871a8-181">Wenn die APP bereitgestellt wurde, schließen Sie die Funktion, indem Sie den-Typ auf einen Bewegungs Controller ziehen.</span><span class="sxs-lookup"><span data-stu-id="871a8-181">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="871a8-182">Im Visual Studio-Fehler Panel werden möglicherweise einige rote Fehler feststellen.</span><span class="sxs-lookup"><span data-stu-id="871a8-182">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="871a8-183">Es ist sicher, Sie zu ignorieren.</span><span class="sxs-lookup"><span data-stu-id="871a8-183">It is safe to ignore them.</span></span> <span data-ttu-id="871a8-184">Wechseln Sie zum Ausgabebereich, um den tatsächlichen buildfortschritt anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="871a8-184">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="871a8-185">Fehler im Ausgabe Panel erfordern eine Korrektur (meistens werden Sie durch einen Fehler in einem Skript verursacht).</span><span class="sxs-lookup"><span data-stu-id="871a8-185">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="871a8-186">Kapitel 1: Hand erkanntes Feedback</span><span class="sxs-lookup"><span data-stu-id="871a8-186">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="871a8-187">Ziele</span><span class="sxs-lookup"><span data-stu-id="871a8-187">Objectives</span></span>

* <span data-ttu-id="871a8-188">Hiermit werden die Hand Verfolgungs Ereignisse abonniert.</span><span class="sxs-lookup"><span data-stu-id="871a8-188">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="871a8-189">Mit Cursor Feedback können Sie Benutzer anzeigen, wenn eine Hand nachverfolgt wird.</span><span class="sxs-lookup"><span data-stu-id="871a8-189">Use cursor feedback to show users when a hand is being tracked.</span></span>

>[!NOTE]
><span data-ttu-id="871a8-190">Bei hololens 2 werden Hände erkannt, wenn die Hände sichtbar sind (nicht nur, wenn ein Finger nach oben zeigt).</span><span class="sxs-lookup"><span data-stu-id="871a8-190">On HoloLens 2 , hands detected fires whenever hands are visible (not just when a finger is pointing up).</span></span>

### <a name="instructions"></a><span data-ttu-id="871a8-191">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="871a8-191">Instructions</span></span>

* <span data-ttu-id="871a8-192">Erweitern Sie im Bereich **Hierarchie** das **InputManager** -Objekt.</span><span class="sxs-lookup"><span data-stu-id="871a8-192">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="871a8-193">Suchen Sie nach dem **gesturesinput** -Objekt, und wählen Sie es aus.</span><span class="sxs-lookup"><span data-stu-id="871a8-193">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="871a8-194">Das Skript **InteractionInputSource.cs** führt folgende Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="871a8-194">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="871a8-195">Abonniert das interaktionsourceerkannte-Ereignis und das interaktionsourcelost-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="871a8-195">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="871a8-196">Legt den handerkannten Zustand fest.</span><span class="sxs-lookup"><span data-stu-id="871a8-196">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="871a8-197">Abonniert die Ereignisse interaktionsourceerkannte und interaktionsourcelost.</span><span class="sxs-lookup"><span data-stu-id="871a8-197">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="871a8-198">Als nächstes aktualisieren wir den Cursor von der [Mr-Eingabe 210](holograms-210.md) in einen, der das Feedback abhängig von den Aktionen des Benutzers anzeigt.</span><span class="sxs-lookup"><span data-stu-id="871a8-198">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="871a8-199">Wählen Sie im Bereich **Hierarchie** das **Cursor** Objekt aus, und löschen Sie es.</span><span class="sxs-lookup"><span data-stu-id="871a8-199">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="871a8-200">Suchen Sie im **Projekt** Panel nach **currsorwithfeedback** , und ziehen Sie es in den Bereich **Hierarchie** .</span><span class="sxs-lookup"><span data-stu-id="871a8-200">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="871a8-201">Klicken Sie im **Hierarchie** Panel auf **InputManager** , und ziehen Sie dann das **cursorwithfeedback** -Objekt aus der **Hierarchie** in das **Cursor** Feld " **simplesinglepointerselector**" von InputManager am unteren Rand des **Inspektor**.</span><span class="sxs-lookup"><span data-stu-id="871a8-201">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="871a8-202">Klicken Sie in der **Hierarchie**auf das **Cursor-Feedback** .</span><span class="sxs-lookup"><span data-stu-id="871a8-202">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="871a8-203">Erweitern Sie im **Inspektor** -Panel **Cursor Zustandsdaten** für das **Objekt Cursor** Skript.</span><span class="sxs-lookup"><span data-stu-id="871a8-203">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="871a8-204">Die **Cursor Zustandsdaten** funktionieren wie folgt:</span><span class="sxs-lookup"><span data-stu-id="871a8-204">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="871a8-205">Jeder Status der Überprüfung bedeutet, dass keine Hand erkannt wird und der Benutzer einfach eine Suche durchführt.</span><span class="sxs-lookup"><span data-stu-id="871a8-205">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="871a8-206">Jeder **Interaktions** Zustand bedeutet, dass eine Hand oder ein Controller erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="871a8-206">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="871a8-207">Jeder **Hover** -Zustand bedeutet, dass der Benutzer ein Hologram ansieht.</span><span class="sxs-lookup"><span data-stu-id="871a8-207">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="871a8-208">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="871a8-208">Build and Deploy</span></span>

* <span data-ttu-id="871a8-209">Verwenden Sie in Unity **Datei >** Buildeinstellungen, um die Anwendung neu zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="871a8-209">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="871a8-210">Öffnen Sie den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="871a8-210">Open the **App** folder.</span></span>
* <span data-ttu-id="871a8-211">Öffnen Sie die Visual Studio-Projekt Mappe **Model Explorer**, wenn Sie nicht bereits geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="871a8-211">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="871a8-212">(Wenn Sie dieses Projekt bereits während der Einrichtung in Visual Studio erstellt bzw. bereitgestellt haben, können Sie diese Instanz von Visual Studio öffnen und auf "alles neu laden" klicken).</span><span class="sxs-lookup"><span data-stu-id="871a8-212">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="871a8-213">Klicken Sie in Visual Studio auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="871a8-213">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="871a8-214">Nachdem die Anwendung in den hololens bereitgestellt wurde, schließen Sie die fitbox mithilfe der Tastenkombination.</span><span class="sxs-lookup"><span data-stu-id="871a8-214">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="871a8-215">Bewegen Sie die Hand in die Anzeige, und zeigen Sie den Finger des Indexes auf den Himmel, um die Hand Verfolgung zu starten</span><span class="sxs-lookup"><span data-stu-id="871a8-215">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="871a8-216">Bewegen Sie Ihre Hand nach links, nach rechts, nach oben und unten.</span><span class="sxs-lookup"><span data-stu-id="871a8-216">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="871a8-217">Sehen Sie sich an, wie sich der Cursor ändert, wenn Ihre Hand erkannt wird, und dann in der Ansicht verloren</span><span class="sxs-lookup"><span data-stu-id="871a8-217">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="871a8-218">Wenn Sie sich auf einem immersiven Headset befinden, müssen Sie eine Verbindung herstellen und den Controller trennen.</span><span class="sxs-lookup"><span data-stu-id="871a8-218">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="871a8-219">Dieses Feedback wird auf einem immersiven Gerät weniger interessant, da ein verbundener Controller immer "verfügbar" ist.</span><span class="sxs-lookup"><span data-stu-id="871a8-219">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="871a8-220">Kapitel 2: Navigation</span><span class="sxs-lookup"><span data-stu-id="871a8-220">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="871a8-221">Ziele</span><span class="sxs-lookup"><span data-stu-id="871a8-221">Objectives</span></span>

* <span data-ttu-id="871a8-222">Verwenden Sie Navigations Gesten Ereignisse, um den Astronaut zu drehen.</span><span class="sxs-lookup"><span data-stu-id="871a8-222">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="871a8-223">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="871a8-223">Instructions</span></span>

<span data-ttu-id="871a8-224">Um Navigations Gesten in unserer APP zu verwenden, bearbeiten wir **GestureAction.cs** , um Objekte zu drehen, wenn die Navigations Bewegung auftritt.</span><span class="sxs-lookup"><span data-stu-id="871a8-224">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="871a8-225">Außerdem wird dem Cursor Feedback hinzugefügt, das angezeigt wird, wenn die Navigation verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="871a8-225">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="871a8-226">Erweitern Sie im Bereich **Hierarchie** den Eintrag **Cursor-Feedback**.</span><span class="sxs-lookup"><span data-stu-id="871a8-226">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="871a8-227">Suchen Sie im Ordner **holograms** das **scrollfeedback** -Medienobjekt.</span><span class="sxs-lookup"><span data-stu-id="871a8-227">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="871a8-228">Ziehen Sie die **scrollfeedback** -vorfab per Drag & amp; Drop auf das **Cursor** Objekt in der **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="871a8-228">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="871a8-229">Klicken Sie auf **currsorwithfeedback**.</span><span class="sxs-lookup"><span data-stu-id="871a8-229">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="871a8-230">Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="871a8-230">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="871a8-231">Geben Sie im Menü den Suchbegriff **Cursor Feedback**ein.</span><span class="sxs-lookup"><span data-stu-id="871a8-231">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="871a8-232">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="871a8-232">Select the search result.</span></span>
7. <span data-ttu-id="871a8-233">Ziehen Sie das **scrollfeedback** -Objekt mithilfe von Drag & amp; Drop aus der- **Hierarchie** in der **Cursor-Feedback** Komponente des **Inspektors**auf die Eigenschaft Bild Lauf **Erkennung erkannt**</span><span class="sxs-lookup"><span data-stu-id="871a8-233">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="871a8-234">Wählen Sie im Bereich **Hierarchie** das Objekt **Astroman** aus.</span><span class="sxs-lookup"><span data-stu-id="871a8-234">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="871a8-235">Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="871a8-235">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="871a8-236">Geben Sie im Menü die Aktion in der **Aktion**Suchfeld ein.</span><span class="sxs-lookup"><span data-stu-id="871a8-236">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="871a8-237">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="871a8-237">Select the search result.</span></span>

<span data-ttu-id="871a8-238">Öffnen Sie als nächstes **GestureAction.cs** in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="871a8-238">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="871a8-239">Bearbeiten Sie in der Codierungs Übung 2. c das Skript, um Folgendes durchzuführen:</span><span class="sxs-lookup"><span data-stu-id="871a8-239">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="871a8-240">**Drehen Sie das Astroman** -Objekt immer dann, wenn eine Navigations Geste ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="871a8-240">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="871a8-241">Berechnen Sie den " **rotationfactor** ", um die auf das Objekt angewendete Drehung zu steuern.</span><span class="sxs-lookup"><span data-stu-id="871a8-241">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="871a8-242">**Drehen Sie das Objekt** um die y-Achse, wenn der Benutzer seine Hand nach links oder rechts verschiebt.</span><span class="sxs-lookup"><span data-stu-id="871a8-242">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="871a8-243">Vervollständigen Sie die Codierungs Übungen 2. c im Skript, oder ersetzen Sie den Code durch die folgende abgeschlossene Lösung:</span><span class="sxs-lookup"><span data-stu-id="871a8-243">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

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

<span data-ttu-id="871a8-244">Sie werden feststellen, dass die anderen Navigations Ereignisse bereits mit einigen Informationen ausgefüllt sind.</span><span class="sxs-lookup"><span data-stu-id="871a8-244">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="871a8-245">Wir schieben das gameobject-Objekt auf den modalen Stapel des Toolkits, sodass der Benutzer den Fokus nicht mehr auf dem Astronaut behalten muss, sobald die Drehung begonnen hat.</span><span class="sxs-lookup"><span data-stu-id="871a8-245">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="871a8-246">Dementsprechend wird das gameobject aus dem Stapel entfernt, sobald die Geste abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="871a8-246">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="871a8-247">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="871a8-247">Build and Deploy</span></span>

1. <span data-ttu-id="871a8-248">Erstellen Sie die Anwendung in Unity neu, erstellen Sie Sie, und stellen Sie Sie aus Visual Studio bereit, um Sie in den hololens auszuführen.</span><span class="sxs-lookup"><span data-stu-id="871a8-248">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="871a8-249">Blick auf den Astronaut, zwei Pfeile sollten auf beiden Seiten des Cursors angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="871a8-249">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="871a8-250">Dieses neue visuelle Element gibt an, dass der Astronaut gedreht werden kann.</span><span class="sxs-lookup"><span data-stu-id="871a8-250">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="871a8-251">Legen Sie die Hand an der Position an der Position (Index fingerbild, die auf den Himmel zeigt), sodass die hololens Ihre Hand nachverfolgen werden.</span><span class="sxs-lookup"><span data-stu-id="871a8-251">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="871a8-252">Um den Astronaut zu drehen, verringern Sie den Finger des Indexes an eine Position, und verschieben Sie dann die Hand nach links oder rechts, um die navigationx-Geste zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="871a8-252">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="871a8-253">Kapitel 3-Hand-Anleitungen</span><span class="sxs-lookup"><span data-stu-id="871a8-253">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="871a8-254">Ziele</span><span class="sxs-lookup"><span data-stu-id="871a8-254">Objectives</span></span>

* <span data-ttu-id="871a8-255">Verwenden Sie die **Hand Leit Faden Bewertung** , um vorherzusagen, wann die Hand Verfolgung verloren geht.</span><span class="sxs-lookup"><span data-stu-id="871a8-255">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="871a8-256">Geben Sie **Feedback zu dem Cursor** an, der angezeigt wird, wenn die Hand des Benutzers den Rand der Ansicht der Kamera anzeigt.</span><span class="sxs-lookup"><span data-stu-id="871a8-256">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="871a8-257">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="871a8-257">Instructions</span></span>

1. <span data-ttu-id="871a8-258">Wählen Sie im Bereich **Hierarchie** das **Cursor** -Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="871a8-258">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="871a8-259">Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="871a8-259">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="871a8-260">Geben Sie im Menü den **Hand Leit Faden**für das Suchfeld ein.</span><span class="sxs-lookup"><span data-stu-id="871a8-260">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="871a8-261">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="871a8-261">Select the search result.</span></span>
4. <span data-ttu-id="871a8-262">Suchen Sie im **Projekt** Panel **holograms** -Ordner das **handguidancefeedback** -Asset.</span><span class="sxs-lookup"><span data-stu-id="871a8-262">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="871a8-263">Ziehen Sie das Objekt **handguidancefeedback** per Drag & Drop auf die Eigenschaft **Hand Leit Faden Anzeige** im **Inspektor** -Panel.</span><span class="sxs-lookup"><span data-stu-id="871a8-263">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="871a8-264">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="871a8-264">Build and Deploy</span></span>

* <span data-ttu-id="871a8-265">Erstellen Sie die Anwendung in Unity neu, erstellen Sie Sie in Visual Studio, und stellen Sie Sie bereit, um die APP auf hololens zu erleben</span><span class="sxs-lookup"><span data-stu-id="871a8-265">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="871a8-266">Zeigen Sie Ihre Hand an, und heben Sie den Index Finger auf, um nachverfolgt zu werden.</span><span class="sxs-lookup"><span data-stu-id="871a8-266">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="871a8-267">Beginnen Sie mit dem Drehen des Astronauten mit der Navigations Bewegung (drücken Sie den Finger und den Ziehpunkt des Indexes zusammen).</span><span class="sxs-lookup"><span data-stu-id="871a8-267">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="871a8-268">Verschieben Sie Ihre Hand ganz nach links, nach rechts, nach oben und nach unten.</span><span class="sxs-lookup"><span data-stu-id="871a8-268">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="871a8-269">Wenn die Kante des Gesten Rahmens in der Hand dargestellt wird, sollte neben dem Cursor ein Pfeil angezeigt werden, der Sie darüber informiert, dass die Hand Verfolgung verloren geht.</span><span class="sxs-lookup"><span data-stu-id="871a8-269">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="871a8-270">Der Pfeil gibt die Richtung an, in der die Hand bewegt werden soll, um zu verhindern, dass die Überwachung verloren geht.</span><span class="sxs-lookup"><span data-stu-id="871a8-270">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="871a8-271">Kapitel 4: Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="871a8-271">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="871a8-272">Ziele</span><span class="sxs-lookup"><span data-stu-id="871a8-272">Objectives</span></span>

* <span data-ttu-id="871a8-273">Verwenden Sie Manipulations Ereignisse, um den Astronaut mit ihren Händen zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="871a8-273">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="871a8-274">Geben Sie Feedback für den Cursor an, damit der Benutzer weiß, wann die Bearbeitung verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="871a8-274">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="871a8-275">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="871a8-275">Instructions</span></span>

<span data-ttu-id="871a8-276">Mit GestureManager.cs und AstronautManager.cs können wir folgende Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="871a8-276">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="871a8-277">Verwenden Sie das Speech-Schlüsselwort "**Move Astronaut**", um **Manipulations** Gesten zu aktivieren und "**Astronaut**" zu deaktivieren, um Sie zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="871a8-277">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="871a8-278">Wechseln Sie zur Reaktion auf die **Erkennungs Gestenerkennung**.</span><span class="sxs-lookup"><span data-stu-id="871a8-278">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="871a8-279">Los geht's.</span><span class="sxs-lookup"><span data-stu-id="871a8-279">Let's get started.</span></span>

1. <span data-ttu-id="871a8-280">Erstellen Sie im **Hierarchie** Panel ein neues leeres gameobject-Objekt.</span><span class="sxs-lookup"><span data-stu-id="871a8-280">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="871a8-281">Nennen Sie es "**astronautmanager**".</span><span class="sxs-lookup"><span data-stu-id="871a8-281">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="871a8-282">Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="871a8-282">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="871a8-283">Geben Sie im Menü im Suchfeld den Suchbegriff " **Astronaut Manager**" ein.</span><span class="sxs-lookup"><span data-stu-id="871a8-283">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="871a8-284">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="871a8-284">Select the search result.</span></span>
4. <span data-ttu-id="871a8-285">Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="871a8-285">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="871a8-286">Geben Sie im Menü die **Eingabe Quelle**für die Suchbegriff Sprache ein.</span><span class="sxs-lookup"><span data-stu-id="871a8-286">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="871a8-287">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="871a8-287">Select the search result.</span></span>

<span data-ttu-id="871a8-288">Nun fügen wir die Sprachbefehle hinzu, die erforderlich sind, um den Interaktions Zustand des Astronauten zu steuern.</span><span class="sxs-lookup"><span data-stu-id="871a8-288">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="871a8-289">Erweitern Sie im **Inspektor**den Abschnitt **Schlüsselwörter** .</span><span class="sxs-lookup"><span data-stu-id="871a8-289">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="871a8-290">Klicken Sie **+** auf der rechten Seite, um ein neues Schlüsselwort hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="871a8-290">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="871a8-291">Geben Sie das Schlüsselwort als **Move Astronaut**ein.</span><span class="sxs-lookup"><span data-stu-id="871a8-291">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="871a8-292">Wenn gewünscht, können Sie eine Tastenkombination hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="871a8-292">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="871a8-293">Klicken Sie **+** auf der rechten Seite, um ein neues Schlüsselwort hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="871a8-293">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="871a8-294">Geben Sie das Schlüsselwort zum **Drehen des Astronauten**ein.</span><span class="sxs-lookup"><span data-stu-id="871a8-294">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="871a8-295">Wenn gewünscht, können Sie eine Tastenkombination hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="871a8-295">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="871a8-296">Der entsprechende Handlercode finden Sie in **GestureAction.cs**im **iredner Handler. onredner keywordrecognized** -Handler.</span><span class="sxs-lookup"><span data-stu-id="871a8-296">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![Einrichten der Spracheingabe Quelle für Kapitel 4](images/holograms211-speech.png)

<span data-ttu-id="871a8-298">Als nächstes richten wir das Manipulations Feedback für den Cursor ein.</span><span class="sxs-lookup"><span data-stu-id="871a8-298">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="871a8-299">Suchen Sie im **Projekt** Panel **holograms** -Ordner das **pathingfeedback** -Asset.</span><span class="sxs-lookup"><span data-stu-id="871a8-299">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="871a8-300">Ziehen Sie die vorfab **pathingfeedback** per Drag & amp; Drop auf das **Cursor** Objekt in der **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="871a8-300">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="871a8-301">Klicken Sie im **Hierarchie** Panel auf " **Cursor**".</span><span class="sxs-lookup"><span data-stu-id="871a8-301">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="871a8-302">Ziehen Sie das **pathingfeedback** -Objekt per Drag & amp; Drop aus der- **Hierarchie** auf die Eigenschaft für die Eigenschaft "" für das **festgelegte Spiel** im **Inspektor**.</span><span class="sxs-lookup"><span data-stu-id="871a8-302">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="871a8-303">Nun müssen Sie **GestureAction.cs** Code hinzufügen, um Folgendes zu ermöglichen:</span><span class="sxs-lookup"><span data-stu-id="871a8-303">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="871a8-304">Fügen Sie der **imanipulationhandler. onmanipulationaktualisierte** -Funktion Code hinzu, mit dem der Astronaut verschoben wird, wenn eine **Manipulations** Bewegung erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="871a8-304">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="871a8-305">Berechnen Sie den **Bewegungsvektor** , um zu bestimmen, an welcher Stelle der Astronaut auf der Grundlage der Handposition verschoben werden soll.</span><span class="sxs-lookup"><span data-stu-id="871a8-305">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="871a8-306">**Verschieben** Sie den Astronauten an die neue Position.</span><span class="sxs-lookup"><span data-stu-id="871a8-306">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="871a8-307">Vervollständigen Sie die Codierungs Übung 4. a in **GestureAction.cs**, oder verwenden Sie unten unsere abgeschlossene Lösung:</span><span class="sxs-lookup"><span data-stu-id="871a8-307">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

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

### <a name="build-and-deploy"></a><span data-ttu-id="871a8-308">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="871a8-308">Build and Deploy</span></span>

* <span data-ttu-id="871a8-309">Erstellen Sie in Unity neu, und erstellen Sie Sie aus Visual Studio, um die app in hololens auszuführen.</span><span class="sxs-lookup"><span data-stu-id="871a8-309">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="871a8-310">Bewegen Sie Ihre Hand vor den hololens, und erhöhen Sie den Indexfinger, damit er nachverfolgt werden kann.</span><span class="sxs-lookup"><span data-stu-id="871a8-310">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="871a8-311">Fokussieren Sie den Cursor auf den Astronaut.</span><span class="sxs-lookup"><span data-stu-id="871a8-311">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="871a8-312">Nehmen Sie an, Sie können den Astronauten mit einer Manipulations Bewegung verschieben.</span><span class="sxs-lookup"><span data-stu-id="871a8-312">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="871a8-313">Im Cursor sollten vier Pfeile angezeigt werden, um anzugeben, dass das Programm nun auf Manipulations Ereignisse antwortet.</span><span class="sxs-lookup"><span data-stu-id="871a8-313">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="871a8-314">Verringern Sie den Finger des Indexes auf Ihren Ziehpunkt, und halten Sie ihn zusammen.</span><span class="sxs-lookup"><span data-stu-id="871a8-314">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="871a8-315">Wenn Sie die Hand herum bewegen, wird der Astronaut ebenfalls verschoben (Dies ist eine Bearbeitung).</span><span class="sxs-lookup"><span data-stu-id="871a8-315">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="871a8-316">Erhöhen Sie den Finger des Indexes, um die Bearbeitung des Astronauten zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="871a8-316">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="871a8-317">Hinweis: Wenn Sie vor dem Hand Zeiger "Move Astronaut" nicht sagen, wird stattdessen die Navigations Geste verwendet.</span><span class="sxs-lookup"><span data-stu-id="871a8-317">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="871a8-318">Nehmen wir an, dass Sie den "Astronaut" drehen, um zum rotatable-Status zurück</span><span class="sxs-lookup"><span data-stu-id="871a8-318">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="871a8-319">Kapitel 5: Modell Erweiterung</span><span class="sxs-lookup"><span data-stu-id="871a8-319">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="871a8-320">Ziele</span><span class="sxs-lookup"><span data-stu-id="871a8-320">Objectives</span></span>

* <span data-ttu-id="871a8-321">Erweitern Sie das Modell "Astronaut" in mehrere kleinere Teile, mit denen der Benutzer interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="871a8-321">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="871a8-322">Verschieben Sie jedes Stück einzeln mithilfe von Navigations-und Bearbeitungs Gesten.</span><span class="sxs-lookup"><span data-stu-id="871a8-322">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="871a8-323">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="871a8-323">Instructions</span></span>

<span data-ttu-id="871a8-324">In diesem Abschnitt werden die folgenden Aufgaben ausgeführt:</span><span class="sxs-lookup"><span data-stu-id="871a8-324">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="871a8-325">Fügen Sie ein neues Schlüsselwort "**Expand Model**" hinzu, um das Modell des Astronauten zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="871a8-325">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="871a8-326">Fügen Sie ein neues Schlüsselwort "**Modell zurücksetzen**" hinzu, um das Modell in seine ursprüngliche Form zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="871a8-326">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="871a8-327">Hierzu fügen wir der Spracheingabe Quelle aus dem vorherigen Kapitel zwei weitere Schlüsselwörter hinzu.</span><span class="sxs-lookup"><span data-stu-id="871a8-327">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="871a8-328">Wir veranschaulichen auch eine weitere Möglichkeit, Erkennungs Ereignisse zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="871a8-328">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="871a8-329">Klicken Sie im **Inspektor** auf " **astronautmanager** ", und erweitern Sie im **Inspektor**den Abschnitt " **Schlüsselwörter** ".</span><span class="sxs-lookup"><span data-stu-id="871a8-329">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="871a8-330">Klicken Sie **+** auf der rechten Seite, um ein neues Schlüsselwort hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="871a8-330">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="871a8-331">Geben Sie das Schlüsselwort als Erweiterungs **Modell**ein.</span><span class="sxs-lookup"><span data-stu-id="871a8-331">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="871a8-332">Wenn gewünscht, können Sie eine Tastenkombination hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="871a8-332">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="871a8-333">Klicken Sie **+** auf der rechten Seite, um ein neues Schlüsselwort hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="871a8-333">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="871a8-334">Geben Sie das Schlüsselwort als **Modell zurücksetzen**ein.</span><span class="sxs-lookup"><span data-stu-id="871a8-334">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="871a8-335">Wenn gewünscht, können Sie eine Tastenkombination hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="871a8-335">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="871a8-336">Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="871a8-336">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="871a8-337">Geben Sie im Menü den **Eingabe Handler**für die Suchbegriff Sprache ein.</span><span class="sxs-lookup"><span data-stu-id="871a8-337">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="871a8-338">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="871a8-338">Select the search result.</span></span>
8. <span data-ttu-id="871a8-339">Überprüfen Sie, ob es sich um einen **globalen Listener handelt**, da Sie möchten, dass diese Befehle unabhängig vom verwendeten gameobject funktionieren.</span><span class="sxs-lookup"><span data-stu-id="871a8-339">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="871a8-340">Klicken Sie **+** auf die Schaltfläche, und wählen Sie Modell aus der Dropdown Liste Schlüsselwort **erweitern**</span><span class="sxs-lookup"><span data-stu-id="871a8-340">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="871a8-341">Klicken Sie **+** unter Antwort auf den Wert, und ziehen Sie den Wert von **astronautmanager** aus der **Hierarchie** in das Feld **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="871a8-341">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="871a8-342">Klicken Sie nun auf die Dropdown Liste **keine Funktion** , und wählen Sie dann " **astronautmanager**" und " **expandmodelcommand**"</span><span class="sxs-lookup"><span data-stu-id="871a8-342">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="871a8-343">Klicken Sie auf die **+** Schaltfläche des Spracheingabe Handlers, und wählen Sie im Dropdown Menü Schlüsselwort **Zurücksetzen** aus</span><span class="sxs-lookup"><span data-stu-id="871a8-343">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="871a8-344">Klicken Sie **+** unter Antwort auf den Wert, und ziehen Sie den Wert von **astronautmanager** aus der **Hierarchie** in das Feld **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="871a8-344">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="871a8-345">Klicken Sie nun auf die Dropdown Liste **keine Funktion** , und wählen Sie dann " **astronautmanager**" und dann " **resetmodelcommand**"</span><span class="sxs-lookup"><span data-stu-id="871a8-345">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![Einrichten der Spracheingabe Quelle und des Handlers für Kapitel 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="871a8-347">Erstellen und bereitstellen</span><span class="sxs-lookup"><span data-stu-id="871a8-347">Build and Deploy</span></span>

* <span data-ttu-id="871a8-348">Probieren Sie es aus!</span><span class="sxs-lookup"><span data-stu-id="871a8-348">Try it!</span></span> <span data-ttu-id="871a8-349">Erstellen Sie die APP, und stellen Sie Sie in den hololens bereit.</span><span class="sxs-lookup"><span data-stu-id="871a8-349">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="871a8-350">Beispiel: **Erweitern Sie Modell** , um das erweiterte Modell des Astronauten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="871a8-350">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="871a8-351">Verwenden Sie die **Navigation** , um einzelne Teile der astronautenfarbe zu drehen.</span><span class="sxs-lookup"><span data-stu-id="871a8-351">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="871a8-352">Nehmen Sie an, Sie können den **Astronauten verschieben** und dann die **Bearbeitung** verwenden, um einzelne Teile des Astronauten zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="871a8-352">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="871a8-353">Nehmen Sie an, Sie können den **Astronauten rotieren** , um die Teile</span><span class="sxs-lookup"><span data-stu-id="871a8-353">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="871a8-354">Nehmen Sie beispielsweise **Reset Model** an, um den Astronaut an seine ursprüngliche Form zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="871a8-354">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="871a8-355">Das Ende</span><span class="sxs-lookup"><span data-stu-id="871a8-355">The End</span></span>

<span data-ttu-id="871a8-356">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="871a8-356">Congratulations!</span></span> <span data-ttu-id="871a8-357">Sie haben nun die **Mr-Eingabe 211 abgeschlossen: Gesten**.</span><span class="sxs-lookup"><span data-stu-id="871a8-357">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="871a8-358">Sie wissen, wie Hand Verfolgungs-, Navigations-und Bearbeitungs Ereignisse erkannt und beantwortet werden.</span><span class="sxs-lookup"><span data-stu-id="871a8-358">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="871a8-359">Sie verstehen den Unterschied zwischen Navigation und Manipulations Gesten.</span><span class="sxs-lookup"><span data-stu-id="871a8-359">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="871a8-360">Sie wissen, wie Sie den Cursor so ändern können, dass er visuelles Feedback bereitstellt, wenn eine Hand entdeckt wird, wenn eine Hand verloren geht, und für den Fall, dass ein Objekt verschiedene Interaktionen unterstützt (Navigation und Bearbeitung).</span><span class="sxs-lookup"><span data-stu-id="871a8-360">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>
