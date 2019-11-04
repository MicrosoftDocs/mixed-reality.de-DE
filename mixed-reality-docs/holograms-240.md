---
title: Mr-Freigabe 240-mehrere hololens-Geräte
description: Befolgen Sie diese exemplarische Vorgehensweise, indem Sie Unity, Visual Studio und hololens verwenden, um die Details der Freigabe von holograms zu erlernen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Sharing, Networking, Academy, Tutorial
ms.openlocfilehash: 0d8e8f4484546d82caadf162623a6f4059eb2f00
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434566"
---
>[!NOTE]
><span data-ttu-id="3922c-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="3922c-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="3922c-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="3922c-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="3922c-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="3922c-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="3922c-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="3922c-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="3922c-108">Es wurde [eine neue Reihe von Tutorials](mrlearning-base.md) für hololens 2 gepostet.</span><span class="sxs-lookup"><span data-stu-id="3922c-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a><span data-ttu-id="3922c-109">Mr-Freigabe 240: mehrere hololens-Geräte</span><span class="sxs-lookup"><span data-stu-id="3922c-109">MR Sharing 240: Multiple HoloLens devices</span></span>

<span data-ttu-id="3922c-110">Holograms sind in unserer Welt vorhanden, da Sie sich im Raum bewegen.</span><span class="sxs-lookup"><span data-stu-id="3922c-110">Holograms are given presence in our world by remaining in place as we move about in space.</span></span> <span data-ttu-id="3922c-111">Hololens hält Hologramme an, indem verschiedene [Koordinatensysteme](coordinate-systems.md) verwendet werden, um den Speicherort und die Ausrichtung von Objekten nachzuverfolgen.</span><span class="sxs-lookup"><span data-stu-id="3922c-111">HoloLens keeps holograms in place by using various [coordinate systems](coordinate-systems.md) to keep track of the location and orientation of objects.</span></span> <span data-ttu-id="3922c-112">Wenn wir diese Koordinatensysteme zwischen Geräten teilen, können wir eine gemeinsame Umgebung erstellen, die es uns ermöglicht, an einer freigegebenen Holographic World teilzunehmen.</span><span class="sxs-lookup"><span data-stu-id="3922c-112">When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.</span></span>

<span data-ttu-id="3922c-113">In diesem Tutorial werden folgende Aktionen durchführt:</span><span class="sxs-lookup"><span data-stu-id="3922c-113">In this tutorial, we will:</span></span>

* <span data-ttu-id="3922c-114">Einrichten eines Netzwerks für eine gemeinsame Nutzung.</span><span class="sxs-lookup"><span data-stu-id="3922c-114">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="3922c-115">Freigeben von holograms für hololens-Geräte.</span><span class="sxs-lookup"><span data-stu-id="3922c-115">Share holograms across HoloLens devices.</span></span>
* <span data-ttu-id="3922c-116">Entdecken Sie andere Personen in unserer freigegebenen Holographic World.</span><span class="sxs-lookup"><span data-stu-id="3922c-116">Discover other people in our shared holographic world.</span></span>
* <span data-ttu-id="3922c-117">Erstellen Sie eine gemeinsame interaktive Darstellung, bei der Sie auf andere Spieler abzielen, und starten Sie Projektile auf Ihnen!</span><span class="sxs-lookup"><span data-stu-id="3922c-117">Create a shared interactive experience where you can target other players - and launch projectiles at them!</span></span>

## <a name="device-support"></a><span data-ttu-id="3922c-118">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="3922c-118">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="3922c-119">Natürlich</span><span class="sxs-lookup"><span data-stu-id="3922c-119">Course</span></span></th><th style="width:150px"> <span data-ttu-id="3922c-120"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="3922c-120"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="3922c-121"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="3922c-121"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="3922c-122">Mr-Freigabe 240: mehrere hololens-Geräte</span><span class="sxs-lookup"><span data-stu-id="3922c-122">MR Sharing 240: Multiple HoloLens devices</span></span></td><td style="text-align: center;"> <span data-ttu-id="3922c-123">✔️</span><span class="sxs-lookup"><span data-stu-id="3922c-123">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="3922c-124">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="3922c-124">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="3922c-125">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="3922c-125">Prerequisites</span></span>

* <span data-ttu-id="3922c-126">Ein Windows 10-PC, der mit den richtigen Tools konfiguriert ist, die mit Internet Zugriff [installiert](install-the-tools.md) sind</span><span class="sxs-lookup"><span data-stu-id="3922c-126">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md) with Internet access.</span></span>
* <span data-ttu-id="3922c-127">Mindestens zwei hololens-Geräte, die [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode)sind.</span><span class="sxs-lookup"><span data-stu-id="3922c-127">At least two HoloLens devices [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="3922c-128">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="3922c-128">Project files</span></span>

* <span data-ttu-id="3922c-129">Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) , die für das Projekt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="3922c-129">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) required by the project.</span></span> <span data-ttu-id="3922c-130">Erfordert Unity 2017,2 oder höher.</span><span class="sxs-lookup"><span data-stu-id="3922c-130">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="3922c-131">Wenn Sie weiterhin Unity 5,6-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span><span class="sxs-lookup"><span data-stu-id="3922c-131">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span></span>
  * <span data-ttu-id="3922c-132">Wenn Sie weiterhin Unity 5,5-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span><span class="sxs-lookup"><span data-stu-id="3922c-132">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span></span>
  * <span data-ttu-id="3922c-133">Wenn Sie weiterhin Unity 5,4-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span><span class="sxs-lookup"><span data-stu-id="3922c-133">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span></span>
* <span data-ttu-id="3922c-134">Deinstallieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht zugänglichen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="3922c-134">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="3922c-135">Behalten Sie den Ordnernamen **sharedholograms**bei.</span><span class="sxs-lookup"><span data-stu-id="3922c-135">Keep the folder name as **SharedHolograms**.</span></span>

>[!NOTE]
><span data-ttu-id="3922c-136">Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span><span class="sxs-lookup"><span data-stu-id="3922c-136">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="3922c-137">Kapitel 1-Holo World</span><span class="sxs-lookup"><span data-stu-id="3922c-137">Chapter 1 - Holo World</span></span>

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

<span data-ttu-id="3922c-138">In diesem Kapitel richten wir das erste Unity-Projekt ein und durchlaufen den Build-und Bereitstellungs Prozess.</span><span class="sxs-lookup"><span data-stu-id="3922c-138">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="3922c-139">Ziele</span><span class="sxs-lookup"><span data-stu-id="3922c-139">Objectives</span></span>

* <span data-ttu-id="3922c-140">Einrichten von Unity zum Entwickeln von Holographic apps.</span><span class="sxs-lookup"><span data-stu-id="3922c-140">Setup Unity to develop holographic apps.</span></span>
* <span data-ttu-id="3922c-141">Sehen Sie sich Ihr Hologram!</span><span class="sxs-lookup"><span data-stu-id="3922c-141">See your hologram!</span></span>

### <a name="instructions"></a><span data-ttu-id="3922c-142">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="3922c-142">Instructions</span></span>

* <span data-ttu-id="3922c-143">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="3922c-143">Start Unity.</span></span>
* <span data-ttu-id="3922c-144">Wählen Sie **Öffnen**aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-144">Select **Open**.</span></span>
* <span data-ttu-id="3922c-145">Geben Sie den Speicherort als Ordner **sharedholograms** ein, den Sie zuvor nicht archiviert haben.</span><span class="sxs-lookup"><span data-stu-id="3922c-145">Enter location as the **SharedHolograms** folder you previously unarchived.</span></span>
* <span data-ttu-id="3922c-146">Wählen Sie **Projekt Name** , und klicken Sie auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="3922c-146">Select **Project Name** and click **Select Folder**.</span></span>
* <span data-ttu-id="3922c-147">Klicken Sie in der **Hierarchie**mit der rechten Maustaste auf die **Hauptkamera** , und wählen Sie **Löschen**.</span><span class="sxs-lookup"><span data-stu-id="3922c-147">In the **Hierarchy**, right-click the **Main Camera** and select **Delete**.</span></span>
* <span data-ttu-id="3922c-148">Suchen Sie im Ordner **holotoolkit-Sharing-240/Prefabs/Camera** nach der **Hauptkamera** -vorfab.</span><span class="sxs-lookup"><span data-stu-id="3922c-148">In the **HoloToolkit-Sharing-240/Prefabs/Camera** folder, find the **Main Camera** prefab.</span></span>
* <span data-ttu-id="3922c-149">Verschieben Sie die **Hauptkamera** per Drag & Drop in die **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="3922c-149">Drag and drop the **Main Camera** into the **Hierarchy**.</span></span>
* <span data-ttu-id="3922c-150">Klicken Sie in der **Hierarchie**auf **Erstellen** , und erstellen Sie eine **leere**.</span><span class="sxs-lookup"><span data-stu-id="3922c-150">In the **Hierarchy**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="3922c-151">Klicken Sie mit der rechten Maustaste auf das neue **gameobject** und wählen Sie **Umbenennen**</span><span class="sxs-lookup"><span data-stu-id="3922c-151">Right-click the new **GameObject** and select **Rename**.</span></span>
* <span data-ttu-id="3922c-152">Benennen Sie das gameobject in **hologramcollection**um.</span><span class="sxs-lookup"><span data-stu-id="3922c-152">Rename the GameObject to **HologramCollection**.</span></span>
* <span data-ttu-id="3922c-153">Wählen Sie das **hologramcollection** -Objekt in der **Hierarchie**aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-153">Select the **HologramCollection** object in the **Hierarchy**.</span></span>
* <span data-ttu-id="3922c-154">Legen Sie im **Inspektor** die **Transformations Position** auf: **X: 0, Y:-0,25, Z: 2**fest.</span><span class="sxs-lookup"><span data-stu-id="3922c-154">In the **Inspector** set the **transform position** to: **X: 0, Y: -0.25, Z: 2**.</span></span>
* <span data-ttu-id="3922c-155">Suchen Sie im Ordner **holograms** des **Projekt Panels**nach dem **energyhub** -Medienobjekt.</span><span class="sxs-lookup"><span data-stu-id="3922c-155">In the **Holograms** folder in the **Project panel**, find the **EnergyHub** asset.</span></span>
* <span data-ttu-id="3922c-156">Ziehen Sie das **energyhub** -Objekt per Drag & Drop aus dem **Projekt Panel** in die **Hierarchie** als untergeordnetes Element **von hologramcollection**.</span><span class="sxs-lookup"><span data-stu-id="3922c-156">Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="3922c-157">Wählen Sie **Datei > Szene speichern unter...**</span><span class="sxs-lookup"><span data-stu-id="3922c-157">Select **File > Save Scene As...**</span></span>
* <span data-ttu-id="3922c-158">Benennen Sie die Szene **sharedholograms** , und klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="3922c-158">Name the scene **SharedHolograms** and click **Save**.</span></span>
* <span data-ttu-id="3922c-159">Klicken Sie in Unity auf die **Wiedergabe** Schaltfläche, um eine Vorschau der holograms anzuzeigen</span><span class="sxs-lookup"><span data-stu-id="3922c-159">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="3922c-160">Drücken **Sie** ein zweites Mal, um den Vorschaumodus zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="3922c-160">Press **Play** a second time to stop preview mode.</span></span>

<span data-ttu-id="3922c-161">**Exportieren des Projekts aus Unity in Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="3922c-161">**Export the project from Unity to Visual Studio**</span></span>

* <span data-ttu-id="3922c-162">Wählen Sie in Unity **Datei > Buildeinstellungen**aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-162">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="3922c-163">Klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="3922c-163">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="3922c-164">Wählen Sie in der Liste **Plattform** **universelle Windows-Plattform** aus, und klicken Sie auf **Plattform wechseln**.</span><span class="sxs-lookup"><span data-stu-id="3922c-164">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="3922c-165">Legen Sie **SDK** auf **Universal 10**fest.</span><span class="sxs-lookup"><span data-stu-id="3922c-165">Set **SDK** to **Universal 10**.</span></span>
* <span data-ttu-id="3922c-166">Legen Sie **Zielgerät** auf **hololens** und **UWP-Buildtyp** auf **D3D**fest.</span><span class="sxs-lookup"><span data-stu-id="3922c-166">Set **Target device** to **HoloLens** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="3922c-167">Überprüfen Sie **Unity C# -Projekte**.</span><span class="sxs-lookup"><span data-stu-id="3922c-167">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="3922c-168">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="3922c-168">Click **Build**.</span></span>
* <span data-ttu-id="3922c-169">Erstellen Sie im Datei-Explorer-Fenster, das angezeigt wird, einen **neuen Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="3922c-169">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="3922c-170">Klicken Sie einfach auf den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="3922c-170">Single click the **App** folder.</span></span>
* <span data-ttu-id="3922c-171">Drücken **Sie Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="3922c-171">Press **Select Folder**.</span></span>
* <span data-ttu-id="3922c-172">Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3922c-172">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="3922c-173">Öffnen Sie den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="3922c-173">Open the **App** folder.</span></span>
* <span data-ttu-id="3922c-174">Öffnen Sie **sharedholograms. sln** , um Visual Studio zu starten.</span><span class="sxs-lookup"><span data-stu-id="3922c-174">Open **SharedHolograms.sln** to launch Visual Studio.</span></span>
* <span data-ttu-id="3922c-175">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x86**.</span><span class="sxs-lookup"><span data-stu-id="3922c-175">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="3922c-176">Klicken Sie auf den Dropdown Pfeil neben lokaler Computer, und wählen Sie **Remote Gerät**aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-176">Click on the drop-down arrow next to Local Machine, and select **Remote Device**.</span></span>
    * <span data-ttu-id="3922c-177">Legen Sie die **Adresse** auf den Namen oder die IP-Adresse der hololens fest.</span><span class="sxs-lookup"><span data-stu-id="3922c-177">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="3922c-178">Wenn Sie die IP-Adresse Ihres Geräts nicht kennen, suchen Sie in den **Einstellungen > Netzwerk & Internet > Erweiterte Optionen** , oder Fragen Sie Cortana **"Hey Cortana, was ist meine IP-Adresse?"** .</span><span class="sxs-lookup"><span data-stu-id="3922c-178">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
    * <span data-ttu-id="3922c-179">Lassen Sie den **Authentifizierungsmodus** auf **Universal**festgelegt.</span><span class="sxs-lookup"><span data-stu-id="3922c-179">Leave the **Authentication Mode** set to **Universal**.</span></span>
    * <span data-ttu-id="3922c-180">Klicken Sie auf **auswählen**</span><span class="sxs-lookup"><span data-stu-id="3922c-180">Click **Select**</span></span>
* <span data-ttu-id="3922c-181">Klicken Sie auf **Debuggen > Starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="3922c-181">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="3922c-182">Wenn Sie die Bereitstellung auf Ihrem Gerät zum ersten Mal durchführt, müssen Sie [es mit Visual Studio](using-visual-studio.md#pairing-your-device)koppeln.</span><span class="sxs-lookup"><span data-stu-id="3922c-182">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>
* <span data-ttu-id="3922c-183">Platzieren Sie die hololens, und suchen Sie das energyhub Hologram.</span><span class="sxs-lookup"><span data-stu-id="3922c-183">Put on your HoloLens and find the EnergyHub hologram.</span></span>

## <a name="chapter-2---interaction"></a><span data-ttu-id="3922c-184">Kapitel 2: Interaktion</span><span class="sxs-lookup"><span data-stu-id="3922c-184">Chapter 2 - Interaction</span></span>

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

<span data-ttu-id="3922c-185">In diesem Kapitel interagieren wir mit unseren holograms.</span><span class="sxs-lookup"><span data-stu-id="3922c-185">In this chapter, we'll interact with our holograms.</span></span> <span data-ttu-id="3922c-186">Zuerst fügen wir einen Cursor zum Visualisieren unseres [Blicks](gaze-and-commit.md)hinzu.</span><span class="sxs-lookup"><span data-stu-id="3922c-186">First, we'll add a cursor to visualize our [Gaze](gaze-and-commit.md).</span></span> <span data-ttu-id="3922c-187">Dann fügen wir [Gesten](gaze-and-commit.md#composite-gestures) hinzu und verwenden unsere Hand, um die Hologramme in den Raum zu versetzen.</span><span class="sxs-lookup"><span data-stu-id="3922c-187">Then, we'll add [Gestures](gaze-and-commit.md#composite-gestures) and use our hand to place our holograms in space.</span></span>

### <a name="objectives"></a><span data-ttu-id="3922c-188">Ziele</span><span class="sxs-lookup"><span data-stu-id="3922c-188">Objectives</span></span>

* <span data-ttu-id="3922c-189">Verwenden Sie die Blick Eingabe, um einen Cursor zu steuern.</span><span class="sxs-lookup"><span data-stu-id="3922c-189">Use gaze input to control a cursor.</span></span>
* <span data-ttu-id="3922c-190">Verwenden Sie Gesten Eingaben für die Interaktion mit holograms.</span><span class="sxs-lookup"><span data-stu-id="3922c-190">Use gesture input to interact with holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="3922c-191">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="3922c-191">Instructions</span></span>

<span data-ttu-id="3922c-192">**Anvisieren**</span><span class="sxs-lookup"><span data-stu-id="3922c-192">**Gaze**</span></span>

* <span data-ttu-id="3922c-193">Wählen Sie im Bereich **Hierarchie** das **hologramcollection** -Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-193">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="3922c-194">Klicken Sie im **Inspektor-Panel** auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="3922c-194">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="3922c-195">Geben Sie im Menü im Suchfeld den Suchbegriff **ein.**</span><span class="sxs-lookup"><span data-stu-id="3922c-195">In the menu, type in the search box **Gaze Manager**.</span></span> <span data-ttu-id="3922c-196">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-196">Select the search result.</span></span>
* <span data-ttu-id="3922c-197">Suchen Sie im Ordner **HoloToolkit-Sharing-240\Prefabs\Input** nach dem **Cursor** Medienobjekt.</span><span class="sxs-lookup"><span data-stu-id="3922c-197">In the **HoloToolkit-Sharing-240\Prefabs\Input** folder, find the **Cursor** asset.</span></span>
* <span data-ttu-id="3922c-198">Ziehen Sie das **Cursor** Medienobjekt per Drag & Drop auf die **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="3922c-198">Drag and drop the **Cursor** asset onto the **Hierarchy**.</span></span>

<span data-ttu-id="3922c-199">**Gestaltungs**</span><span class="sxs-lookup"><span data-stu-id="3922c-199">**Gesture**</span></span>

* <span data-ttu-id="3922c-200">Wählen Sie im Bereich **Hierarchie** das **hologramcollection** -Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-200">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="3922c-201">Klicken Sie auf **Komponente hinzufügen** , und geben Sie **Gesten-Manager** in das Suchfeld ein.</span><span class="sxs-lookup"><span data-stu-id="3922c-201">Click **Add Component** and type **Gesture Manager** in the search field.</span></span> <span data-ttu-id="3922c-202">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-202">Select the search result.</span></span>
* <span data-ttu-id="3922c-203">Erweitern Sie im Bereich **Hierarchie**den Knoten **hologrammcollection**.</span><span class="sxs-lookup"><span data-stu-id="3922c-203">In the **Hierarchy panel**, expand **HologramCollection**.</span></span>
* <span data-ttu-id="3922c-204">Wählen Sie das untergeordnete **energyhub** -Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-204">Select the child **EnergyHub** object.</span></span>
* <span data-ttu-id="3922c-205">Klicken Sie im **Inspektor-Panel** auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="3922c-205">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="3922c-206">Geben Sie im Menü das Suchfeld **Hologram Placement**ein.</span><span class="sxs-lookup"><span data-stu-id="3922c-206">In the menu, type in the search box **Hologram Placement**.</span></span> <span data-ttu-id="3922c-207">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-207">Select the search result.</span></span>
* <span data-ttu-id="3922c-208">Speichern Sie die Szene, indem Sie **Datei > Szene speichern**auswählen.</span><span class="sxs-lookup"><span data-stu-id="3922c-208">Save the scene by selecting **File > Save Scene**.</span></span>

<span data-ttu-id="3922c-209">**Bereitstellen und nutzen**</span><span class="sxs-lookup"><span data-stu-id="3922c-209">**Deploy and enjoy**</span></span>

* <span data-ttu-id="3922c-210">Verwenden Sie die Anweisungen aus dem vorherigen Kapitel, um Ihre hololens zu erstellen und bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="3922c-210">Build and deploy to your HoloLens, using the instructions from the previous chapter.</span></span>
* <span data-ttu-id="3922c-211">Nachdem die APP auf Ihren hololens gestartet wurde, bewegen Sie Ihren Kopf und sehen, wie der energyhub ihren Blick folgt.</span><span class="sxs-lookup"><span data-stu-id="3922c-211">Once the app launches on your HoloLens, move your head around and notice how the EnergyHub follows your gaze.</span></span>
* <span data-ttu-id="3922c-212">Beachten Sie, dass der Cursor angezeigt wird, wenn Sie das Hologramm betrachten, und sich an einem Punktlicht ändert, wenn Sie nicht in ein Hologramm eingeblendet werden.</span><span class="sxs-lookup"><span data-stu-id="3922c-212">Notice how the cursor appears when you gaze upon the hologram, and changes to a point light when not gazing at a hologram.</span></span>
* <span data-ttu-id="3922c-213">Führen Sie einen lufttipp aus, um das Hologram zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="3922c-213">Perform an air-tap to place the hologram.</span></span> <span data-ttu-id="3922c-214">Zu diesem Zeitpunkt können Sie das – Hologramm nur einmal platzieren (erneut bereitstellen, um es erneut zu versuchen).</span><span class="sxs-lookup"><span data-stu-id="3922c-214">At this time in our project, you can only place the hologram once (redeploy to try again).</span></span>

## <a name="chapter-3---shared-coordinates"></a><span data-ttu-id="3922c-215">Kapitel 3: freigegebene Koordinaten</span><span class="sxs-lookup"><span data-stu-id="3922c-215">Chapter 3 - Shared Coordinates</span></span>

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

<span data-ttu-id="3922c-216">Es ist Spaß, Hologramme zu sehen und mit Ihnen zu interagieren, aber wir gehen weiter.</span><span class="sxs-lookup"><span data-stu-id="3922c-216">It's fun to see and interact with holograms, but let's go further.</span></span> <span data-ttu-id="3922c-217">Wir legen unsere erste gemeinsame Benutzeransicht fest.</span><span class="sxs-lookup"><span data-stu-id="3922c-217">We'll set up our first shared experience - a hologram everyone can see together.</span></span>

### <a name="objectives"></a><span data-ttu-id="3922c-218">Ziele</span><span class="sxs-lookup"><span data-stu-id="3922c-218">Objectives</span></span>

* <span data-ttu-id="3922c-219">Einrichten eines Netzwerks für eine gemeinsame Nutzung.</span><span class="sxs-lookup"><span data-stu-id="3922c-219">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="3922c-220">Richten Sie einen allgemeinen Verweis Punkt ein.</span><span class="sxs-lookup"><span data-stu-id="3922c-220">Establish a common reference point.</span></span>
* <span data-ttu-id="3922c-221">Teilen Sie Koordinatensysteme auf allen Geräten.</span><span class="sxs-lookup"><span data-stu-id="3922c-221">Share coordinate systems across devices.</span></span>
* <span data-ttu-id="3922c-222">Jeder sieht dasselbe Hologram!</span><span class="sxs-lookup"><span data-stu-id="3922c-222">Everyone sees the same hologram!</span></span>

>[!NOTE]
><span data-ttu-id="3922c-223">Die Funktionen **internetclientserver** und **privatenetworkclientserver** müssen für eine APP deklariert werden, um eine Verbindung mit dem Freigabe Server herzustellen.</span><span class="sxs-lookup"><span data-stu-id="3922c-223">The **InternetClientServer** and **PrivateNetworkClientServer** capabilities must be declared for an app to connect to the sharing server.</span></span> <span data-ttu-id="3922c-224">Dies erfolgt für Sie bereits in holograms 240, aber beachten Sie dies für Ihre eigenen Projekte.</span><span class="sxs-lookup"><span data-stu-id="3922c-224">This is done for you already in Holograms 240, but keep this in mind for your own projects.</span></span>

>1. <span data-ttu-id="3922c-225">Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zu "> Projekteinstellungen bearbeiten > Player" navigieren.</span><span class="sxs-lookup"><span data-stu-id="3922c-225">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="3922c-226">Klicken Sie auf die Registerkarte "Windows Store".</span><span class="sxs-lookup"><span data-stu-id="3922c-226">Click on the "Windows Store" tab</span></span>
>3. <span data-ttu-id="3922c-227">Überprüfen Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die Funktion " **internetclientserver** " und die Funktion " **privatenetworkclientserver** ".</span><span class="sxs-lookup"><span data-stu-id="3922c-227">In the "Publishing Settings > Capabilities" section, check the **InternetClientServer** capability and the **PrivateNetworkClientServer** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="3922c-228">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="3922c-228">Instructions</span></span>

* <span data-ttu-id="3922c-229">Navigieren Sie im **Projekt Panel** zum Ordner **HoloToolkit-Sharing-240\Prefabs\Sharing** .</span><span class="sxs-lookup"><span data-stu-id="3922c-229">In the **Project panel** navigate to the **HoloToolkit-Sharing-240\Prefabs\Sharing** folder.</span></span>
* <span data-ttu-id="3922c-230">Ziehen Sie die **Freigabe** vorfab per Drag & amp; Drop in den Bereich **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="3922c-230">Drag and drop the **Sharing** prefab into the **Hierarchy panel**.</span></span>

<span data-ttu-id="3922c-231">Als nächstes müssen wir den Freigabe Dienst starten.</span><span class="sxs-lookup"><span data-stu-id="3922c-231">Next we need to launch the sharing service.</span></span> <span data-ttu-id="3922c-232">Dieser Schritt muss nur von **einem PC** in der gemeinsamen Nutzung durchlaufen werden.</span><span class="sxs-lookup"><span data-stu-id="3922c-232">Only **one PC** in the shared experience needs to do this step.</span></span>

* <span data-ttu-id="3922c-233">Wählen Sie in Unity im oberen Menü das **Menü holotoolkit-Sharing-240**aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-233">In Unity - in the top-hand menu - select the **HoloToolkit-Sharing-240 menu**.</span></span>
* <span data-ttu-id="3922c-234">Wählen Sie in der Dropdown-Dropdown-Option das Element **Launch Sharing Service** aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-234">Select the **Launch Sharing Service** item in the drop-down.</span></span>
* <span data-ttu-id="3922c-235">Aktivieren Sie die Option **privates Netzwerk** , und klicken Sie auf **Zugriff zulassen** , wenn die Firewall angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3922c-235">Check the **Private Network** option and click **Allow Access** when the firewall prompt appears.</span></span>
* <span data-ttu-id="3922c-236">Notieren Sie sich die im Fenster Freigabe Dienst-Konsolenfenster angezeigte IPv4-Adresse.</span><span class="sxs-lookup"><span data-stu-id="3922c-236">Note down the IPv4 address displayed in the Sharing Service console window.</span></span> <span data-ttu-id="3922c-237">Dies ist dieselbe IP-Adresse wie der Computer, auf dem der Dienst ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3922c-237">This is the same IP as the machine the service is being run on.</span></span>

<span data-ttu-id="3922c-238">Befolgen Sie die restlichen Anweisungen auf **allen PCs** , die der freigegebenen Funktion beitreten werden.</span><span class="sxs-lookup"><span data-stu-id="3922c-238">Follow the rest of the instructions on **all PCs** that will join the shared experience.</span></span>

* <span data-ttu-id="3922c-239">Wählen Sie in der **Hierarchie**das **Freigabe** Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-239">In the **Hierarchy**, select the **Sharing** object.</span></span>
* <span data-ttu-id="3922c-240">Ändern Sie im **Inspektor**auf der Komponente der **Freigabe Stufe** die **Server Adresse** von "localhost" in die IPv4-Adresse des Computers, auf dem "sharingservice. exe" ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3922c-240">In the **Inspector**, on the **Sharing Stage** component, change the **Server Address** from 'localhost' to the IPv4 address of the machine running SharingService.exe.</span></span>
* <span data-ttu-id="3922c-241">Wählen Sie in der **Hierarchie** das **hologramcollection** -Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-241">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="3922c-242">Klicken Sie im **Inspektor** auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="3922c-242">In the **Inspector** click the **Add Component** button.</span></span>
* <span data-ttu-id="3922c-243">Geben Sie im Suchfeld den **Text Import-/Export-Manager**ein.</span><span class="sxs-lookup"><span data-stu-id="3922c-243">In the search box, type **Import Export Anchor Manager**.</span></span> <span data-ttu-id="3922c-244">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-244">Select the search result.</span></span>
* <span data-ttu-id="3922c-245">Navigieren Sie im **Projekt Panel** zum Ordner **Scripts** .</span><span class="sxs-lookup"><span data-stu-id="3922c-245">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="3922c-246">Doppelklicken Sie auf das **hologramplacement** -Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="3922c-246">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="3922c-247">Ersetzen Sie den Inhalt durch den folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="3922c-247">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="3922c-248">Wählen Sie in Unity im Bereich **Hierarchie**die Option **hologramcollection** aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-248">Back in Unity, select the **HologramCollection** in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="3922c-249">Klicken Sie im **Inspektor-Panel** auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="3922c-249">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="3922c-250">Geben Sie im Menü den Suchbegriff **App State Manager**ein.</span><span class="sxs-lookup"><span data-stu-id="3922c-250">In the menu, type in the search box **App State Manager**.</span></span> <span data-ttu-id="3922c-251">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-251">Select the search result.</span></span>

<span data-ttu-id="3922c-252">**Bereitstellen und nutzen**</span><span class="sxs-lookup"><span data-stu-id="3922c-252">**Deploy and enjoy**</span></span>

* <span data-ttu-id="3922c-253">Erstellen Sie das Projekt für Ihre hololens-Geräte.</span><span class="sxs-lookup"><span data-stu-id="3922c-253">Build the project for your HoloLens devices.</span></span>
* <span data-ttu-id="3922c-254">Legen Sie einen hololens für die erste Bereitstellung fest.</span><span class="sxs-lookup"><span data-stu-id="3922c-254">Designate one HoloLens to deploy to first.</span></span> <span data-ttu-id="3922c-255">Sie müssen warten, bis der Anker in den Dienst hochgeladen wird, bevor Sie den energyhub platzieren können (Dies kann ungefähr 30-60 Sekunden dauern).</span><span class="sxs-lookup"><span data-stu-id="3922c-255">You will need to wait for the Anchor to be uploaded to the service before you can place the EnergyHub (this can take ~30-60 seconds).</span></span> <span data-ttu-id="3922c-256">Bis der Upload abgeschlossen ist, werden Ihre Tap-Gesten ignoriert.</span><span class="sxs-lookup"><span data-stu-id="3922c-256">Until the upload is done, your tap gestures will be ignored.</span></span>
* <span data-ttu-id="3922c-257">Nachdem der energyhub platziert wurde, wird der Speicherort in den Dienst hochgeladen, und Sie können dann auf allen anderen hololens-Geräten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="3922c-257">After the EnergyHub has been placed, its location will be uploaded to the service and you can then deploy to all other HoloLens devices.</span></span>
* <span data-ttu-id="3922c-258">Wenn ein neuer hololens zum ersten Mal an der Sitzung teilnimmt, ist der Speicherort des energyhubs auf diesem Gerät möglicherweise nicht korrekt.</span><span class="sxs-lookup"><span data-stu-id="3922c-258">When a new HoloLens first joins the session, the location of the EnergyHub may not be correct on that device.</span></span> <span data-ttu-id="3922c-259">Sobald jedoch die Anker-und energyhub-Standorte vom Dienst heruntergeladen wurden, sollte der energyhub zum neuen freigegebenen Speicherort springen.</span><span class="sxs-lookup"><span data-stu-id="3922c-259">However, as soon as the anchor and EnergyHub locations have been downloaded from the service, the EnergyHub should jump to the new, shared location.</span></span> <span data-ttu-id="3922c-260">Wenn dies nicht innerhalb von ~ 30-60 Sekunden erfolgt, gehen Sie zu dem Zeitpunkt, an dem sich die ursprünglichen hololens beim Festlegen des Ankers befunden haben, um weitere Umgebungs Hinweise zu sammeln.</span><span class="sxs-lookup"><span data-stu-id="3922c-260">If this does not happen within ~30-60 seconds, walk to where the original HoloLens was when setting the anchor to gather more environment clues.</span></span> <span data-ttu-id="3922c-261">Wenn der Speicherort noch nicht gesperrt ist, stellen Sie die erneute Bereitstellung auf dem Gerät bereit.</span><span class="sxs-lookup"><span data-stu-id="3922c-261">If the location still does not lock on, redeploy to the device.</span></span>
* <span data-ttu-id="3922c-262">Wenn die Geräte bereit sind und die app ausführen, suchen Sie nach dem energyhub.</span><span class="sxs-lookup"><span data-stu-id="3922c-262">When the devices are all ready and running the app, look for the EnergyHub.</span></span> <span data-ttu-id="3922c-263">Können Sie alle den Speicherort des holograms und die Richtung des Texts akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="3922c-263">Can you all agree on the hologram's location and which direction the text is facing?</span></span>

## <a name="chapter-4---discovery"></a><span data-ttu-id="3922c-264">Kapitel 4: Ermittlung</span><span class="sxs-lookup"><span data-stu-id="3922c-264">Chapter 4 - Discovery</span></span>

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

<span data-ttu-id="3922c-265">Alle Benutzer können jetzt dasselbe Hologram sehen!</span><span class="sxs-lookup"><span data-stu-id="3922c-265">Everyone can now see the same hologram!</span></span> <span data-ttu-id="3922c-266">Sehen wir uns nun an, dass alle anderen Personen mit unserer freigegebenen Holographic World verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="3922c-266">Now let's see everyone else connected to our shared holographic world.</span></span> <span data-ttu-id="3922c-267">In diesem Kapitel werden die Head-und Rotation aller anderen hololens-Geräte in derselben Freigabe Sitzung erläutert.</span><span class="sxs-lookup"><span data-stu-id="3922c-267">In this chapter, we'll grab the head location and rotation of all other HoloLens devices in the same sharing session.</span></span>

### <a name="objectives"></a><span data-ttu-id="3922c-268">Ziele</span><span class="sxs-lookup"><span data-stu-id="3922c-268">Objectives</span></span>

* <span data-ttu-id="3922c-269">Entdecken Sie einander in unserer gemeinsamen Darstellung.</span><span class="sxs-lookup"><span data-stu-id="3922c-269">Discover each other in our shared experience.</span></span>
* <span data-ttu-id="3922c-270">Wählen Sie einen Player Avatar aus, und geben Sie ihn frei</span><span class="sxs-lookup"><span data-stu-id="3922c-270">Choose and share a player avatar.</span></span>
* <span data-ttu-id="3922c-271">Fügen Sie den Player Avatar neben den Köpfen der Menschen an.</span><span class="sxs-lookup"><span data-stu-id="3922c-271">Attach the player avatar next to everyone's heads.</span></span>

### <a name="instructions"></a><span data-ttu-id="3922c-272">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="3922c-272">Instructions</span></span>

* <span data-ttu-id="3922c-273">Navigieren Sie im **Projekt Panel** zum Ordner **holograms** .</span><span class="sxs-lookup"><span data-stu-id="3922c-273">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="3922c-274">Verschieben Sie den **playeravatarstore** per Drag & amp; Drop in die **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="3922c-274">Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.</span></span>
* <span data-ttu-id="3922c-275">Navigieren Sie im **Projekt Panel** zum Ordner **Scripts** .</span><span class="sxs-lookup"><span data-stu-id="3922c-275">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="3922c-276">Doppelklicken Sie auf das Skript " **avatarselector** ", um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="3922c-276">Double-click the **AvatarSelector** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="3922c-277">Ersetzen Sie den Inhalt durch den folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="3922c-277">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* <span data-ttu-id="3922c-278">Wählen Sie in der **Hierarchie** das **hologramcollection** -Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-278">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="3922c-279">Klicken Sie im **Inspektor** auf **Komponente hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="3922c-279">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="3922c-280">Geben Sie im Suchfeld als Suchbegriff **local Player Manager**ein.</span><span class="sxs-lookup"><span data-stu-id="3922c-280">In the search box, type **Local Player Manager**.</span></span> <span data-ttu-id="3922c-281">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-281">Select the search result.</span></span>
* <span data-ttu-id="3922c-282">Wählen Sie in der **Hierarchie** das **hologramcollection** -Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-282">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="3922c-283">Klicken Sie im **Inspektor** auf **Komponente hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="3922c-283">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="3922c-284">Geben Sie im Suchfeld als Suchbegriff **Remote Player-Manager**ein.</span><span class="sxs-lookup"><span data-stu-id="3922c-284">In the search box, type **Remote Player Manager**.</span></span> <span data-ttu-id="3922c-285">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-285">Select the search result.</span></span>
* <span data-ttu-id="3922c-286">Öffnen Sie das **hologramplacement** -Skript in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3922c-286">Open the **HologramPlacement** script in Visual Studio.</span></span>
* <span data-ttu-id="3922c-287">Ersetzen Sie den Inhalt durch den folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="3922c-287">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="3922c-288">Öffnen Sie das **appstatus Manager** -Skript in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3922c-288">Open the **AppStateManager** script in Visual Studio.</span></span>
* <span data-ttu-id="3922c-289">Ersetzen Sie den Inhalt durch den folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="3922c-289">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

<span data-ttu-id="3922c-290">**Bereitstellen und nutzen**</span><span class="sxs-lookup"><span data-stu-id="3922c-290">**Deploy and Enjoy**</span></span>

* <span data-ttu-id="3922c-291">Erstellen Sie das Projekt, und stellen Sie es auf Ihren hololens-Geräten bereit.</span><span class="sxs-lookup"><span data-stu-id="3922c-291">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="3922c-292">Wenn Sie einen pinganton hören, suchen Sie das Avatar-Auswahlmenü, und wählen Sie einen Avatar mit der Luft tippen Bewegung aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-292">When you hear a pinging sound, find the avatar selection menu and select an avatar with the air-tap gesture.</span></span>
* <span data-ttu-id="3922c-293">Wenn Sie keine holograms betrachten, wird durch die Punktbeleuchtung um den Cursor eine andere Farbe aktiviert, wenn Ihre hololens mit dem Dienst kommuniziert: initialisieren (dunkellila), Herunterladen des Ankers (grün), Importieren/Exportieren von Standortdaten (gelb), der Anker wird hochgeladen (blau).</span><span class="sxs-lookup"><span data-stu-id="3922c-293">If you're not looking at any holograms, the point light around your cursor will turn a different color when your HoloLens is communicating with the service: initializing (dark purple), downloading the anchor (green), importing/exporting location data (yellow), uploading the anchor (blue).</span></span> <span data-ttu-id="3922c-294">Wenn Ihr Cursor die Standardfarbe (hell lila) ist, können Sie mit anderen Spielern in Ihrer Sitzung interagieren!</span><span class="sxs-lookup"><span data-stu-id="3922c-294">If your point light around your cursor is the default color (light purple), then you are ready to interact with other players in your session!</span></span>
* <span data-ttu-id="3922c-295">Sehen Sie sich andere Personen an, die mit Ihrem Platz verbunden sind. es gibt einen Holographic-Roboter, der über der Schulter schwebt und seine Kopfbewegungen imitiert.</span><span class="sxs-lookup"><span data-stu-id="3922c-295">Look at other people connected to your space - there will be a holographic robot floating above their shoulder and mimicking their head motions!</span></span>

## <a name="chapter-5---placement"></a><span data-ttu-id="3922c-296">Kapitel 5: Platzierung</span><span class="sxs-lookup"><span data-stu-id="3922c-296">Chapter 5 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

<span data-ttu-id="3922c-297">In diesem Kapitel wird der Anker auf realen Oberflächen platziert.</span><span class="sxs-lookup"><span data-stu-id="3922c-297">In this chapter, we'll make the anchor able to be placed on real-world surfaces.</span></span> <span data-ttu-id="3922c-298">Wir verwenden freigegebene Koordinaten zum Platzieren dieses Ankers zwischen allen Personen, die mit der gemeinsamen Benutzer Verbindung verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="3922c-298">We'll use shared coordinates to place that anchor in the middle point between everyone connected to the shared experience.</span></span>

### <a name="objectives"></a><span data-ttu-id="3922c-299">Ziele</span><span class="sxs-lookup"><span data-stu-id="3922c-299">Objectives</span></span>

* <span data-ttu-id="3922c-300">Platzieren Sie holograms basierend auf der Hauptposition des Players im räumlichen Mapping-Mesh.</span><span class="sxs-lookup"><span data-stu-id="3922c-300">Place holograms on the spatial mapping mesh based on players’ head position.</span></span>

### <a name="instructions"></a><span data-ttu-id="3922c-301">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="3922c-301">Instructions</span></span>

* <span data-ttu-id="3922c-302">Navigieren Sie im **Projekt Panel** zum Ordner **holograms** .</span><span class="sxs-lookup"><span data-stu-id="3922c-302">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="3922c-303">Ziehen Sie die **customspatialmapping** -vorfab per Drag & Drop auf die **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="3922c-303">Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.</span></span>
* <span data-ttu-id="3922c-304">Navigieren Sie im **Projekt Panel** zum Ordner **Scripts** .</span><span class="sxs-lookup"><span data-stu-id="3922c-304">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="3922c-305">Doppelklicken Sie auf das Skript **appstatus Manager** , um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="3922c-305">Double-click the **AppStateManager** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="3922c-306">Ersetzen Sie den Inhalt durch den folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="3922c-306">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* <span data-ttu-id="3922c-307">Navigieren Sie im **Projekt Panel** zum Ordner **Scripts** .</span><span class="sxs-lookup"><span data-stu-id="3922c-307">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="3922c-308">Doppelklicken Sie auf das **hologramplacement** -Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="3922c-308">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="3922c-309">Ersetzen Sie den Inhalt durch den folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="3922c-309">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

<span data-ttu-id="3922c-310">**Bereitstellen und nutzen**</span><span class="sxs-lookup"><span data-stu-id="3922c-310">**Deploy and enjoy**</span></span>

* <span data-ttu-id="3922c-311">Erstellen Sie das Projekt, und stellen Sie es auf Ihren hololens-Geräten bereit.</span><span class="sxs-lookup"><span data-stu-id="3922c-311">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="3922c-312">Wenn die APP bereit ist, stehen Sie in einem Kreis und sehen, wie der energyhub in der Mitte von allen Benutzern angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3922c-312">When the app is ready, stand in a circle and notice how the EnergyHub appears in the center of everyone.</span></span>
* <span data-ttu-id="3922c-313">Tippen Sie, um den energyhub zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="3922c-313">Tap to place the EnergyHub.</span></span>
* <span data-ttu-id="3922c-314">Verwenden Sie den Sprachbefehl "Ziel zurücksetzen", um die energyhub-Sicherungskopie auszuwählen und als Gruppe zusammenzuarbeiten, um das Hologramm an einen neuen Speicherort zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="3922c-314">Try the voice command 'Reset Target' to pick the EnergyHub back up and work together as a group to move the hologram to a new location.</span></span>

## <a name="chapter-6---real-world-physics"></a><span data-ttu-id="3922c-315">Kapitel 6: Reale Physik</span><span class="sxs-lookup"><span data-stu-id="3922c-315">Chapter 6 - Real-World Physics</span></span>

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

<span data-ttu-id="3922c-316">In diesem Kapitel fügen wir holograms hinzu, die aus realen Oberflächen springen.</span><span class="sxs-lookup"><span data-stu-id="3922c-316">In this chapter we'll add holograms that bounce off real-world surfaces.</span></span> <span data-ttu-id="3922c-317">Sehen Sie sich ihren Platz mit Projekten an, die von Ihnen und Ihren Freunden gestartet wurden!</span><span class="sxs-lookup"><span data-stu-id="3922c-317">Watch your space fill up with projects launched by both you and your friends!</span></span>

### <a name="objectives"></a><span data-ttu-id="3922c-318">Ziele</span><span class="sxs-lookup"><span data-stu-id="3922c-318">Objectives</span></span>

* <span data-ttu-id="3922c-319">Starten Sie Projekt Kacheln, die aus realen Oberflächen springen.</span><span class="sxs-lookup"><span data-stu-id="3922c-319">Launch projectiles that bounce off real-world surfaces.</span></span>
* <span data-ttu-id="3922c-320">Geben Sie die Projekt Kacheln frei, damit Sie von anderen Playern angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="3922c-320">Share the projectiles so other players can see them.</span></span>

### <a name="instructions"></a><span data-ttu-id="3922c-321">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="3922c-321">Instructions</span></span>

* <span data-ttu-id="3922c-322">Wählen Sie in der **Hierarchie** das **hologramcollection** -Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-322">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="3922c-323">Klicken Sie im **Inspektor** auf **Komponente hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="3922c-323">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="3922c-324">Geben Sie im Suchfeld als Suchbegriff **projectile Launcher**ein.</span><span class="sxs-lookup"><span data-stu-id="3922c-324">In the search box, type **Projectile Launcher**.</span></span> <span data-ttu-id="3922c-325">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-325">Select the search result.</span></span>

<span data-ttu-id="3922c-326">**Bereitstellen und nutzen**</span><span class="sxs-lookup"><span data-stu-id="3922c-326">**Deploy and enjoy**</span></span>

* <span data-ttu-id="3922c-327">Erstellen und bereitstellen auf Ihren hololens-Geräten.</span><span class="sxs-lookup"><span data-stu-id="3922c-327">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="3922c-328">Wenn die APP auf allen Geräten ausgeführt wird, können Sie auf der realen Oberfläche auf der realen Oberfläche eine Luft tippen, um projectile zu starten.</span><span class="sxs-lookup"><span data-stu-id="3922c-328">When the app is running on all devices, perform an air-tap to launch projectile at real world surfaces.</span></span>
* <span data-ttu-id="3922c-329">Sehen Sie sich an, was geschieht, wenn Ihre Projekt Kachel mit dem Avatar eines anderen Players kollidiert!</span><span class="sxs-lookup"><span data-stu-id="3922c-329">See what happens when your projectile collides with another player's avatar!</span></span>

## <a name="chapter-7---grand-finale"></a><span data-ttu-id="3922c-330">Kapitel 7: groß-Finale</span><span class="sxs-lookup"><span data-stu-id="3922c-330">Chapter 7 - Grand Finale</span></span>

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

<span data-ttu-id="3922c-331">In diesem Kapitel wird ein Portal erläutert, das nur mit der Zusammenarbeit ermittelt werden kann.</span><span class="sxs-lookup"><span data-stu-id="3922c-331">In this chapter, we'll uncover a portal that can only be discovered with collaboration.</span></span>

### <a name="objectives"></a><span data-ttu-id="3922c-332">Ziele</span><span class="sxs-lookup"><span data-stu-id="3922c-332">Objectives</span></span>

* <span data-ttu-id="3922c-333">Arbeiten Sie zusammen, um auf dem Anker ausreichend Projekt Kacheln zu starten, um ein geheimes Portal zu entdecken.</span><span class="sxs-lookup"><span data-stu-id="3922c-333">Work together to launch enough projectiles at the anchor to uncover a secret portal!</span></span>

### <a name="instructions"></a><span data-ttu-id="3922c-334">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="3922c-334">Instructions</span></span>

* <span data-ttu-id="3922c-335">Navigieren Sie im **Projekt Panel** zum Ordner **holograms** .</span><span class="sxs-lookup"><span data-stu-id="3922c-335">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="3922c-336">Verschieben Sie das Objekt " **Underworld** " per Drag & Drop als untergeordnetes Element **von hologramcollection**.</span><span class="sxs-lookup"><span data-stu-id="3922c-336">Drag and drop the **Underworld** asset as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="3922c-337">Klicken Sie bei ausgewähltem **hologrammcollection** im **Inspektor**auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="3922c-337">With **HologramCollection** selected, click the **Add Component** button in the **Inspector**.</span></span>
* <span data-ttu-id="3922c-338">Geben Sie im Menü im Suchfeld den Suchbegriff **explodetarget**ein.</span><span class="sxs-lookup"><span data-stu-id="3922c-338">In the menu, type in the search box **ExplodeTarget**.</span></span> <span data-ttu-id="3922c-339">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="3922c-339">Select the search result.</span></span>
* <span data-ttu-id="3922c-340">Wenn **hologrammcollection** ausgewählt ist, ziehen Sie das **energyhub** -Objekt aus der **Hierarchie** in das **Zielfeld** des **Inspektors**.</span><span class="sxs-lookup"><span data-stu-id="3922c-340">With **HologramCollection** selected, from the **Hierarchy** drag the **EnergyHub** object to the **Target** field in the **Inspector**.</span></span>
* <span data-ttu-id="3922c-341">Wenn **hologrammcollection** ausgewählt ist, ziehen Sie das Objekt " **Underworld** " aus der **Hierarchie** in das Feld " **Unterwelt** " des **Inspektors**.</span><span class="sxs-lookup"><span data-stu-id="3922c-341">With **HologramCollection** selected, from the **Hierarchy** drag the **Underworld** object to the **Underworld** field in the **Inspector**.</span></span>

<span data-ttu-id="3922c-342">**Bereitstellen und nutzen**</span><span class="sxs-lookup"><span data-stu-id="3922c-342">**Deploy and enjoy**</span></span>

* <span data-ttu-id="3922c-343">Erstellen und bereitstellen auf Ihren hololens-Geräten.</span><span class="sxs-lookup"><span data-stu-id="3922c-343">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="3922c-344">Wenn die APP gestartet wurde, können Sie zusammenarbeiten, um Projektile auf dem energyhub zu starten.</span><span class="sxs-lookup"><span data-stu-id="3922c-344">When the app has launched, collaborate together to launch projectiles at the EnergyHub.</span></span>
* <span data-ttu-id="3922c-345">Wenn die Unterwelt angezeigt wird, starten Sie Projektile bei Unterwelt-Robotern (führen Sie dreimal einen Roboter aus).</span><span class="sxs-lookup"><span data-stu-id="3922c-345">When the underworld appears, launch projectiles at underworld robots (hit a robot three times for extra fun).</span></span>
