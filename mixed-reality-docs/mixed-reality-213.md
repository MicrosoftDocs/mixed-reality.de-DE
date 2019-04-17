---
title: MR Eingabe 213
description: Dieses Tutorial Schreiben von Code mithilfe von Unity, Visual Studio und immersive Headsets für die Details der Motion-Controller.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Holotoolkit, Mixedrealitytoolkit, Mixedrealitytoolkit-Unity, immersive motion, Controller, Academy, Tutorial
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604704"
---
>[!NOTE]
><span data-ttu-id="11a02-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="11a02-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="11a02-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="11a02-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="11a02-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="11a02-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="11a02-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="11a02-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="11a02-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="11a02-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="11a02-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="11a02-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-213-motion-controllers"></a><span data-ttu-id="11a02-110">MR Eingabe 213: Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="11a02-110">MR Input 213: Motion controllers</span></span>

<span data-ttu-id="11a02-111">Motion-Controller in der Welt mixed Reality fügen Sie ein anderes Maß an Interaktivität hinzu.</span><span class="sxs-lookup"><span data-stu-id="11a02-111">Motion controllers in the mixed reality world add another level of interactivity.</span></span> <span data-ttu-id="11a02-112">Mit [motion Controller](motion-controllers.md), können direkte Interaktion mit Objekten auf natürlichere Weise, wie unsere physischen Interaktionen in der Praxis zu Entwicklungsthemen zu erhöhen und erfreuen Sie Ihre app-Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="11a02-112">With [motion controllers](motion-controllers.md), we can directly interact with objects in a more natural way, similar to our physical interactions in real life, increasing immersion and delight in your app experience.</span></span>

<span data-ttu-id="11a02-113">Eingabe 213 MR erforschen wir Eingabeereignisse von der Motion-Controller durch eine einfache räumliche zeichnen-Umgebung erstellen.</span><span class="sxs-lookup"><span data-stu-id="11a02-113">In MR Input 213, we will explore the motion controller's input events by creating a simple spatial painting experience.</span></span> <span data-ttu-id="11a02-114">Mit dieser app können Benutzer im dreidimensionalen Raum mit verschiedenen Typen von Pinsel und Farben zeichnen.</span><span class="sxs-lookup"><span data-stu-id="11a02-114">With this app, users can paint in three-dimensional space with various types of brushes and colors.</span></span>

## <a name="topics-covered-in-this-tutorial"></a><span data-ttu-id="11a02-115">In diesem Tutorial behandelten Themen</span><span class="sxs-lookup"><span data-stu-id="11a02-115">Topics covered in this tutorial</span></span>

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|<span data-ttu-id="11a02-119">**Controller-Visualisierung**</span><span class="sxs-lookup"><span data-stu-id="11a02-119">**Controller visualization**</span></span>|<span data-ttu-id="11a02-120">**Controller-Eingabeereignisse**</span><span class="sxs-lookup"><span data-stu-id="11a02-120">**Controller input events**</span></span>|<span data-ttu-id="11a02-121">**Benutzerdefinierten Controller und Benutzeroberfläche**</span><span class="sxs-lookup"><span data-stu-id="11a02-121">**Custom controller and UI**</span></span>|
|<span data-ttu-id="11a02-122">Erfahren Sie, wie während der Übertragung Controller-Modellen in Unity-Spiele-Modus und Laufzeit gerendert.</span><span class="sxs-lookup"><span data-stu-id="11a02-122">Learn how to render motion controller models in Unity's game mode and runtime.</span></span>|<span data-ttu-id="11a02-123">Erfahren Sie, verschiedene Typen von Schaltflächenereignisse und ihre Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="11a02-123">Understand different types of button events and their applications.</span></span>|<span data-ttu-id="11a02-124">Erfahren Sie, wie overlay-Elemente der Benutzeroberfläche auf dem Controller oder vollständig anpassen.</span><span class="sxs-lookup"><span data-stu-id="11a02-124">Learn how to overlay UI elements on top of the controller or fully customize it.</span></span>|

## <a name="device-support"></a><span data-ttu-id="11a02-125">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="11a02-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="11a02-126">Kurs</span><span class="sxs-lookup"><span data-stu-id="11a02-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="11a02-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="11a02-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="11a02-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="11a02-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="11a02-129">MR Eingabe 213: Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="11a02-129">MR Input 213: Motion controllers</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="11a02-130">✔️</span><span class="sxs-lookup"><span data-stu-id="11a02-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="11a02-131">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="11a02-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="11a02-132">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="11a02-132">Prerequisites</span></span>

<span data-ttu-id="11a02-133">Finden Sie auf die Installations-Checkliste für immersive Headsets [auf dieser Seite](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="11a02-133">See the installation checklist for immersive headsets on [this page](install-the-tools.md).</span></span>

* <span data-ttu-id="11a02-134">In diesem Lernprogramm [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span><span class="sxs-lookup"><span data-stu-id="11a02-134">This tutorial requires [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span></span>

### <a name="project-files"></a><span data-ttu-id="11a02-135">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="11a02-135">Project files</span></span>

* <span data-ttu-id="11a02-136">[Laden Sie die Dateien](https://github.com/Microsoft/MixedReality213/archive/master.zip) vom das Projekt benötigt, und extrahieren Sie die Dateien auf dem Desktop.</span><span class="sxs-lookup"><span data-stu-id="11a02-136">[Download the files](https://github.com/Microsoft/MixedReality213/archive/master.zip) required by the project and extract the files to the Desktop.</span></span>

>[!NOTE]
><span data-ttu-id="11a02-137">Wenn Sie vor dem Herunterladen, den Quellcode ansehen möchten es [auf GitHub verfügbar](https://github.com/Microsoft/MixedReality213).</span><span class="sxs-lookup"><span data-stu-id="11a02-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/MixedReality213).</span></span>

## <a name="unity-setup"></a><span data-ttu-id="11a02-138">Unity-setup</span><span class="sxs-lookup"><span data-stu-id="11a02-138">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a><span data-ttu-id="11a02-139">Ziele</span><span class="sxs-lookup"><span data-stu-id="11a02-139">Objectives</span></span>

* <span data-ttu-id="11a02-140">Optimieren von Unity für Windows Mixed Reality-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="11a02-140">Optimize Unity for Windows Mixed Reality development</span></span>
* <span data-ttu-id="11a02-141">Einrichten von Mixed Reality-Kamera</span><span class="sxs-lookup"><span data-stu-id="11a02-141">Setup Mixed Reality Camera</span></span>
* <span data-ttu-id="11a02-142">Einrichten der Umgebung</span><span class="sxs-lookup"><span data-stu-id="11a02-142">Setup environment</span></span>

### <a name="instructions"></a><span data-ttu-id="11a02-143">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="11a02-143">Instructions</span></span>

* <span data-ttu-id="11a02-144">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="11a02-144">Start Unity.</span></span>
* <span data-ttu-id="11a02-145">Wählen Sie **öffnen**.</span><span class="sxs-lookup"><span data-stu-id="11a02-145">Select **Open**.</span></span>
* <span data-ttu-id="11a02-146">Navigieren Sie zu Ihrem Desktop und finden die **MixedReality213-Master** Ordner, die Sie zuvor nicht archiviert.</span><span class="sxs-lookup"><span data-stu-id="11a02-146">Navigate to your Desktop and find the **MixedReality213-master** folder you previously unarchived.</span></span>
* <span data-ttu-id="11a02-147">Klicken Sie auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="11a02-147">Click **Select Folder**.</span></span>
* <span data-ttu-id="11a02-148">Wenn Unity abgeschlossen ist, Projektdateien werden geladen, werden Sie Unity-Editor angezeigt.</span><span class="sxs-lookup"><span data-stu-id="11a02-148">Once Unity finishes loading project files, you will be able to see Unity editor.</span></span>
* <span data-ttu-id="11a02-149">Wählen Sie in Unity **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="11a02-149">In Unity, select **File > Build Settings**.</span></span>

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* <span data-ttu-id="11a02-151">Wählen Sie **universelle Windows-Plattform** in die **Plattform** aus, und klicken Sie auf die **Plattform wechseln** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="11a02-151">Select **Universal Windows Platform** in the **Platform** list and click the **Switch Platform** button.</span></span>
* <span data-ttu-id="11a02-152">Legen Sie Zielgerät auf **jedes Gerät**</span><span class="sxs-lookup"><span data-stu-id="11a02-152">Set Target Device to **Any device**</span></span>
* <span data-ttu-id="11a02-153">Legen Sie Buildtyp auf **D3D**</span><span class="sxs-lookup"><span data-stu-id="11a02-153">Set Build Type to **D3D**</span></span>
* <span data-ttu-id="11a02-154">Legen Sie die SDK auf **zuletzt installierte**</span><span class="sxs-lookup"><span data-stu-id="11a02-154">Set SDK to **Latest Installed**</span></span>
* <span data-ttu-id="11a02-155">Überprüfen Sie **Unity C# Projekte**</span><span class="sxs-lookup"><span data-stu-id="11a02-155">Check **Unity C# Projects**</span></span>
    * <span data-ttu-id="11a02-156">Dadurch, dass Sie die Skriptdateien in Visual Studio-Projekt ändern, ohne Neuerstellung von Unity-Projekt.</span><span class="sxs-lookup"><span data-stu-id="11a02-156">This allows you modify script files in the Visual Studio project without rebuilding Unity project.</span></span>
* <span data-ttu-id="11a02-157">Klicken Sie auf **Playereinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="11a02-157">Click **Player Settings**.</span></span>
* <span data-ttu-id="11a02-158">In der **Inspektor** Panel, führen Sie einen Bildlauf nach unten</span><span class="sxs-lookup"><span data-stu-id="11a02-158">In the **Inspector** panel, scroll down to the bottom</span></span>
* <span data-ttu-id="11a02-159">Überprüfen Sie unter "XR-Einstellungen" **virtuelle Realität unterstützt**</span><span class="sxs-lookup"><span data-stu-id="11a02-159">In XR Settings, check **Virtual Reality Supported**</span></span>
* <span data-ttu-id="11a02-160">Wählen Sie unter virtuelle Realität SDKs **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="11a02-160">Under Virtual Reality SDKs, select **Windows Mixed Reality**</span></span>

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* <span data-ttu-id="11a02-162">Schließen **Buildeinstellungen** Fenster.</span><span class="sxs-lookup"><span data-stu-id="11a02-162">Close **Build Settings** window.</span></span>

### <a name="project-structure"></a><span data-ttu-id="11a02-163">Struktur des Projekts</span><span class="sxs-lookup"><span data-stu-id="11a02-163">Project structure</span></span>

<span data-ttu-id="11a02-164">Dieses Tutorial verwendet  **[Mixed Reality-Toolkit – Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span><span class="sxs-lookup"><span data-stu-id="11a02-164">This tutorial uses **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span></span> <span data-ttu-id="11a02-165">Die Versionen finden Sie auf [auf dieser Seite](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span><span class="sxs-lookup"><span data-stu-id="11a02-165">You can find the releases on [this page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span>

![ProjectStructure](images/mr213-projectstructure-650px.png)

<span data-ttu-id="11a02-167">**Abgeschlossene Szenen zur Referenz**</span><span class="sxs-lookup"><span data-stu-id="11a02-167">**Completed scenes for your reference**</span></span>
* <span data-ttu-id="11a02-168">Sehen Sie zwei abgeschlossene Unity im Hintergrund unter **Szenen** Ordner.</span><span class="sxs-lookup"><span data-stu-id="11a02-168">You will find two completed Unity scenes under **Scenes** folder.</span></span>
    * <span data-ttu-id="11a02-169">**MixedReality213**: Vollständige Szene mit einzelnen Pinsel</span><span class="sxs-lookup"><span data-stu-id="11a02-169">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="11a02-170">**MixedReality213Advanced**: Für erweiterte Entwurf mit mehreren Pinsel Szene abgeschlossen</span><span class="sxs-lookup"><span data-stu-id="11a02-170">**MixedReality213Advanced**: Completed scene for advanced design with multiple brushes</span></span>

<span data-ttu-id="11a02-171">**Einrichten einer neuen Szene für das tutorial**</span><span class="sxs-lookup"><span data-stu-id="11a02-171">**New Scene setup for the tutorial**</span></span>
* <span data-ttu-id="11a02-172">Klicken Sie in Unity auf **Datei > neue Szene**</span><span class="sxs-lookup"><span data-stu-id="11a02-172">In Unity, click **File > New Scene**</span></span>
* <span data-ttu-id="11a02-173">Löschen Sie **Hauptkamera** und **gerichtetes Licht**</span><span class="sxs-lookup"><span data-stu-id="11a02-173">Delete **Main Camera** and **Directional Light**</span></span>
* <span data-ttu-id="11a02-174">Von der **Projektfenster**, suchen, und ziehen Sie die folgenden prefabs (Vorlagen) in der **Hierarchie** Bereich:</span><span class="sxs-lookup"><span data-stu-id="11a02-174">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="11a02-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="11a02-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span></span>
    * <span data-ttu-id="11a02-176">Assets/AppPrefabs/**Environment**</span><span class="sxs-lookup"><span data-stu-id="11a02-176">Assets/AppPrefabs/**Environment**</span></span>

![Kamera und Umgebung](images/mr213-cameraenvironment-300px.jpg)
* <span data-ttu-id="11a02-178">Es gibt zwei Kamera Prefabs in Mixed Reality-Toolkit:</span><span class="sxs-lookup"><span data-stu-id="11a02-178">There are two camera prefabs in Mixed Reality Toolkit:</span></span>
    * <span data-ttu-id="11a02-179">**MixedRealityCamera.prefab**: Nur der Kamera</span><span class="sxs-lookup"><span data-stu-id="11a02-179">**MixedRealityCamera.prefab**: Camera only</span></span>
    * <span data-ttu-id="11a02-180">**MixedRealityCameraParent.prefab**: Kamera + Teleportation + Grenze</span><span class="sxs-lookup"><span data-stu-id="11a02-180">**MixedRealityCameraParent.prefab**: Camera + Teleportation + Boundary</span></span>
    * <span data-ttu-id="11a02-181">In diesem Tutorial verwenden wir **MixedRealityCamera** ohne Teleportation-Funktion.</span><span class="sxs-lookup"><span data-stu-id="11a02-181">In this tutorial, we will use **MixedRealityCamera** without teleportation feature.</span></span> <span data-ttu-id="11a02-182">Aus diesem Grund wir einfache hinzugefügt **Umgebung** Prefab enthält eine grundlegende Etage um geerdete können Benutzer zu machen.</span><span class="sxs-lookup"><span data-stu-id="11a02-182">Because of this, we added simple **Environment** prefab which contains a basic floor to make the user feel grounded.</span></span>
    * <span data-ttu-id="11a02-183">Weitere Informationen zu den Teleportation mit **MixedRealityCameraParent**, finden Sie unter [erweitert Design - Teleportation und Locomotion](#advanced-design---teleportation-and-locomotion)</span><span class="sxs-lookup"><span data-stu-id="11a02-183">To learn more about the teleportation with **MixedRealityCameraParent**, see [Advanced design - Teleportation and locomotion](#advanced-design---teleportation-and-locomotion)</span></span>

<span data-ttu-id="11a02-184">**Skybox-setup**</span><span class="sxs-lookup"><span data-stu-id="11a02-184">**Skybox setup**</span></span>
* <span data-ttu-id="11a02-185">Klicken Sie auf **Fenster > Beleuchtung > Einstellungen**</span><span class="sxs-lookup"><span data-stu-id="11a02-185">Click **Window > Lighting > Settings**</span></span>
* <span data-ttu-id="11a02-186">Klicken Sie auf den Kreis auf dem rechten Rand der **Skybox Material-Feld**</span><span class="sxs-lookup"><span data-stu-id="11a02-186">Click the circle on the right side of the **Skybox Material field**</span></span>
* <span data-ttu-id="11a02-187">Geben Sie in "grau", und wählen Sie **SkyboxGray**</span><span class="sxs-lookup"><span data-stu-id="11a02-187">Type in ‘gray’ and select **SkyboxGray**</span></span>

<span data-ttu-id="11a02-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span><span class="sxs-lookup"><span data-stu-id="11a02-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span></span>

![Festlegen von skybox](images/mr123-skyboxsetting-400px.jpg)
* <span data-ttu-id="11a02-190">Überprüfen Sie **Skybox** können angezeigt werden zugewiesen, grauen Farbverlauf Skybox</span><span class="sxs-lookup"><span data-stu-id="11a02-190">Check **Skybox** option to be able to see assigned gray gradient skybox</span></span>

![Skybox Umschaltoption](images/mr213-skyboxcheck-400px.jpg)
* <span data-ttu-id="11a02-192">Die Szene mit MixedRealityCamera "," Umgebung "und" graue Skybox sieht wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="11a02-192">The scene with MixedRealityCamera, Environment and gray skybox will look like this.</span></span>

![MixedReality213 Environment](images/mr213-environment-600px.jpg)
* <span data-ttu-id="11a02-194">Klicken Sie auf **Datei > Szene speichern unter**</span><span class="sxs-lookup"><span data-stu-id="11a02-194">Click **File > Save Scene as**</span></span>
* <span data-ttu-id="11a02-195">**Speichern Sie** Ihrer Szene Ordner im Hintergrund mit einem beliebigen Namen</span><span class="sxs-lookup"><span data-stu-id="11a02-195">**Save** your scene under Scenes folder with any name</span></span>

## <a name="chapter-1---controller-visualization"></a><span data-ttu-id="11a02-196">Kapitel 1 - Controller-Visualisierung</span><span class="sxs-lookup"><span data-stu-id="11a02-196">Chapter 1 - Controller visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a><span data-ttu-id="11a02-197">Ziele</span><span class="sxs-lookup"><span data-stu-id="11a02-197">Objectives</span></span>

* <span data-ttu-id="11a02-198">Erfahren Sie, wie während der Übertragung Controller-Modelle im Unity Spiele-Modus und zur Laufzeit gerendert.</span><span class="sxs-lookup"><span data-stu-id="11a02-198">Learn how to render motion controller models in Unity's game mode and at runtime.</span></span>

<span data-ttu-id="11a02-199">Windows Mixed Reality bietet eine animierte Controllermodell für die Controller-Visualisierung.</span><span class="sxs-lookup"><span data-stu-id="11a02-199">Windows Mixed Reality provides an animated controller model for controller visualization.</span></span> <span data-ttu-id="11a02-200">Es gibt verschiedene Ansätze, die Sie für die Visualisierung der Controller in Ihrer app ausführen können:</span><span class="sxs-lookup"><span data-stu-id="11a02-200">There are several approaches you can take for controller visualization in your app:</span></span>
* <span data-ttu-id="11a02-201">Standard - Standardcontroller, ohne Änderungen verwenden</span><span class="sxs-lookup"><span data-stu-id="11a02-201">Default - Using default controller without modification</span></span>
* <span data-ttu-id="11a02-202">Hybrid - Standardcontroller, verwenden jedoch einige Elemente anpassen oder Überlagern von UI-Komponenten</span><span class="sxs-lookup"><span data-stu-id="11a02-202">Hybrid - Using default controller, but customizing some of its elements or overlaying UI components</span></span>
* <span data-ttu-id="11a02-203">Ersatz - Ihre eigene angepasste 3D-Modell für den controller</span><span class="sxs-lookup"><span data-stu-id="11a02-203">Replacement - Using your own customized 3D model for the controller</span></span>

<span data-ttu-id="11a02-204">In diesem Kapitel lernen wir zu den Beispielen dieser Controller Anpassungen.</span><span class="sxs-lookup"><span data-stu-id="11a02-204">In this chapter, we will learn about the examples of these controller customizations.</span></span>

### <a name="instructions"></a><span data-ttu-id="11a02-205">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="11a02-205">Instructions</span></span>

* <span data-ttu-id="11a02-206">In der **Projekt** geben **MotionControllers** in das Suchfeld.</span><span class="sxs-lookup"><span data-stu-id="11a02-206">In the **Project** panel, type **MotionControllers** in the search box .</span></span> <span data-ttu-id="11a02-207">Sie finden ihn außerdem unter Assets/HoloToolkit/Input/Prefabs /.</span><span class="sxs-lookup"><span data-stu-id="11a02-207">You can also find it under Assets/HoloToolkit/Input/Prefabs/.</span></span>
* <span data-ttu-id="11a02-208">Ziehen Sie die **MotionControllers** prefab in die **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="11a02-208">Drag the **MotionControllers** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="11a02-209">Klicken Sie auf die **MotionControllers** prefab in die **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="11a02-209">Click on the **MotionControllers** prefab in the **Hierarchy** panel.</span></span>

<span data-ttu-id="11a02-210">**MotionControllers prefabs**</span><span class="sxs-lookup"><span data-stu-id="11a02-210">**MotionControllers prefab**</span></span>

<span data-ttu-id="11a02-211">**MotionControllers** Prefab ist ein **MotionControllerVisualizer** Skript an der die Steckplätze für alternativen Controller Modelle enthält.</span><span class="sxs-lookup"><span data-stu-id="11a02-211">**MotionControllers** prefab has a **MotionControllerVisualizer** script which provides the slots for alternate controller models.</span></span> <span data-ttu-id="11a02-212">Wenn Sie Ihre eigenen benutzerdefinierten 3D-Modelle, z. B. einer Hand oder ein "sword" zuweisen und überprüfen 'Immer mit alternativen links/rechts Model', sehen Sie diese anstelle des Standard-Modells.</span><span class="sxs-lookup"><span data-stu-id="11a02-212">If you assign your own custom 3D models such as a hand or a sword and check 'Always Use Alternate Left/Right Model', you will see them instead of the default model.</span></span> <span data-ttu-id="11a02-213">Wir werden dieser Steckplatz in Kapitel 4 verwenden, um die Controller-Modell mit einem Pinsel zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="11a02-213">We will use this slot in Chapter 4 to replace the controller model with a brush.</span></span>

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

<span data-ttu-id="11a02-215">**Anweisungen**</span><span class="sxs-lookup"><span data-stu-id="11a02-215">**Instructions**</span></span>
* <span data-ttu-id="11a02-216">In der **Inspektor** panel, doppelklicken Sie auf **MotionControllerVisualizer** Skript den Code in Visual Studio finden Sie unter</span><span class="sxs-lookup"><span data-stu-id="11a02-216">In the **Inspector** panel, double click **MotionControllerVisualizer** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="11a02-217">**MotionControllerVisualizer-Skript**</span><span class="sxs-lookup"><span data-stu-id="11a02-217">**MotionControllerVisualizer script**</span></span>

<span data-ttu-id="11a02-218">Die **MotionControllerVisualizer** und **MotionControllerInfo** Klassen bieten die Möglichkeit zum Zugriff auf und ändern die Standard-Controller-Modelle.</span><span class="sxs-lookup"><span data-stu-id="11a02-218">The **MotionControllerVisualizer** and **MotionControllerInfo** classes provide the means to access & modify the default controller models.</span></span> <span data-ttu-id="11a02-219">**MotionControllerVisualizer** Unity abonniert **InteractionSourceDetected** Ereignis und Controller-Modelle automatisch instanziiert, wenn sie gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="11a02-219">**MotionControllerVisualizer** subscribes to Unity's **InteractionSourceDetected** event and automatically instantiates controller models when they are found.</span></span>

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

<span data-ttu-id="11a02-220">Die Controller-Modelle werden bereitgestellt, gemäß [der Spezifikation GlTF](https://github.com/KhronosGroup/glTF).</span><span class="sxs-lookup"><span data-stu-id="11a02-220">The controller models are delivered according to [the glTF specification](https://github.com/KhronosGroup/glTF).</span></span> <span data-ttu-id="11a02-221">Dieses Format wurde erstellt, um ein einheitliches Format, bei der Verbesserung des Prozesses übertragen, und Entpacken von 3D-Objekten bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="11a02-221">This format has been created to provide a common format, while improving the process behind transmitting and unpacking 3D assets.</span></span> <span data-ttu-id="11a02-222">In diesem Fall müssen wir zum Abrufen und laden die Controller-Modelle zur Laufzeit, wie wir der benutzerfreundlichkeit des so reibungslos wie möglich gestalten möchten, und es ist nicht garantiert, welche Version der Controller während der Übertragung der Benutzer verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="11a02-222">In this case, we need to retrieve and load the controller models at runtime, as we want to make the user's experience as seamless as possible, and it's not guaranteed which version of the motion controllers the user might be using.</span></span> <span data-ttu-id="11a02-223">Dieser Kurs, über das Mixed Reality-Toolkit, verwendet eine Version von der Gruppe Khronos [UnityGLTF Projekt](https://github.com/KhronosGroup/UnityGLTF).</span><span class="sxs-lookup"><span data-stu-id="11a02-223">This course, via the Mixed Reality Toolkit, uses a version of the Khronos Group's [UnityGLTF project](https://github.com/KhronosGroup/UnityGLTF).</span></span>

<span data-ttu-id="11a02-224">Skripts können verwendet werden, sobald der Controller übermittelt wurden, **MotionControllerInfo** , finden die Transformationen für bestimmte Controller-Elemente, sodass sie selbst richtig positionieren können.</span><span class="sxs-lookup"><span data-stu-id="11a02-224">Once the controller has been delivered, scripts can use **MotionControllerInfo** to find the transforms for specific controller elements so they can correctly position themselves.</span></span>

<span data-ttu-id="11a02-225">In einem der folgenden Kapitel lernen wir, wie Sie diese Skripts zu verwenden, um Benutzeroberflächenelemente auf Controller anzufügen.</span><span class="sxs-lookup"><span data-stu-id="11a02-225">In a later chapter, we will learn how to use these scripts to attach UI elements to the controllers.</span></span>

<span data-ttu-id="11a02-226">*In einigen Skripts finden Sie Codeblöcke mit **#if! UNITY_EDITOR** oder **UNITY_WSA**. Diese Codeblöcke, die nur auf die UWP-Laufzeit ausgeführt werden, beim Bereitstellen von für Windows. Das liegt der Satz von APIs, die von Unity-Editor und die UWP-app-Laufzeit verwendet werden, sind unterschiedlich.*</span><span class="sxs-lookup"><span data-stu-id="11a02-226">*In some scripts, you will find code blocks with **#if !UNITY_EDITOR** or **UNITY_WSA**. These code blocks run only on the UWP runtime when you deploy to Windows. This is because the set of APIs used by the Unity editor and the UWP app runtime are different.*</span></span>
* <span data-ttu-id="11a02-227">**Speichern Sie** der Szene, und klicken Sie auf die **spielen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="11a02-227">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="11a02-228">Sie werden können Sie die Szene mit Motion-Controllern in Ihre Kopfhörer.</span><span class="sxs-lookup"><span data-stu-id="11a02-228">You will be able to see the scene with motion controllers in your headset.</span></span> <span data-ttu-id="11a02-229">Sie können ausführliche Animationen auf eine Schaltfläche, Ministick verschieben und Hervorheben von Touchpad Touch anzeigen.</span><span class="sxs-lookup"><span data-stu-id="11a02-229">You can see detailed animations for button clicks, thumbstick movement, and touchpad touch highlighting.</span></span>

![MR213_Controller Visualisierung Standard](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a><span data-ttu-id="11a02-231">Kapitel 2: Anfügen von UI-Elemente mit dem controller</span><span class="sxs-lookup"><span data-stu-id="11a02-231">Chapter 2 - Attaching UI elements to the controller</span></span>

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a><span data-ttu-id="11a02-232">Ziele</span><span class="sxs-lookup"><span data-stu-id="11a02-232">Objectives</span></span>

* <span data-ttu-id="11a02-233">Erfahren Sie mehr über die Elemente der Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="11a02-233">Learn about the elements of the motion controllers</span></span>
* <span data-ttu-id="11a02-234">Erfahren Sie, wie zum Anfügen von Objekten auf bestimmte Teile der Controller</span><span class="sxs-lookup"><span data-stu-id="11a02-234">Learn how to attach objects to specific parts of the controllers</span></span>

<span data-ttu-id="11a02-235">In diesem Kapitel lernen Sie, wie Sie die Elemente der Benutzeroberfläche der Controller hinzufügen, die der Benutzer kann einfach zugreifen und diese jederzeit auf Bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="11a02-235">In this chapter, you will learn how to add user interface elements to the controller which the user can easily access and manipulate at anytime.</span></span> <span data-ttu-id="11a02-236">Außerdem lernen Sie, wie eine einfache Farbauswahl-Benutzeroberfläche mit dem Touchpad Eingabe hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="11a02-236">You will also learn how to add a simple color picker UI using the touchpad input.</span></span>

### <a name="instructions"></a><span data-ttu-id="11a02-237">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="11a02-237">Instructions</span></span>

* <span data-ttu-id="11a02-238">In der **Projekt** Bereich, suchen Sie **MotionControllerInfo** Skript.</span><span class="sxs-lookup"><span data-stu-id="11a02-238">In the **Project** panel, search **MotionControllerInfo** script.</span></span>
* <span data-ttu-id="11a02-239">Im Suchergebnis doppelklicken **MotionControllerInfo** Skript, um den Code in Visual Studio anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="11a02-239">From the search result, double click **MotionControllerInfo** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="11a02-240">**MotionControllerInfo-Skript**</span><span class="sxs-lookup"><span data-stu-id="11a02-240">**MotionControllerInfo script**</span></span>

<span data-ttu-id="11a02-241">Der erste Schritt ist, welches Element des Controllers die Benutzeroberfläche an angefügt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="11a02-241">The first step is to choose which element of the controller you want the UI to attach to.</span></span> <span data-ttu-id="11a02-242">Diese Elemente sind in definiert **ControllerElementEnum** in **MotionControllerInfo.cs**.</span><span class="sxs-lookup"><span data-stu-id="11a02-242">These elements are defined in **ControllerElementEnum** in **MotionControllerInfo.cs**.</span></span>

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)
* <span data-ttu-id="11a02-244">**Home**</span><span class="sxs-lookup"><span data-stu-id="11a02-244">**Home**</span></span>
* <span data-ttu-id="11a02-245">**Menü "**</span><span class="sxs-lookup"><span data-stu-id="11a02-245">**Menu**</span></span>
* <span data-ttu-id="11a02-246">**Verstehen**</span><span class="sxs-lookup"><span data-stu-id="11a02-246">**Grasp**</span></span>
* <span data-ttu-id="11a02-247">**Thumbstick**</span><span class="sxs-lookup"><span data-stu-id="11a02-247">**Thumbstick**</span></span>
* <span data-ttu-id="11a02-248">**Wählen Sie**</span><span class="sxs-lookup"><span data-stu-id="11a02-248">**Select**</span></span>
* <span data-ttu-id="11a02-249">**Touchpad**</span><span class="sxs-lookup"><span data-stu-id="11a02-249">**Touchpad**</span></span>
* <span data-ttu-id="11a02-250">**Zeigen Sie Haltung** : dieses Element stellt dar, die Spitze des Controllers vorwärts verweist.</span><span class="sxs-lookup"><span data-stu-id="11a02-250">**Pointing pose** – this element represents the tip of the controller pointing forward direction.</span></span>

<span data-ttu-id="11a02-251">**Anweisungen**</span><span class="sxs-lookup"><span data-stu-id="11a02-251">**Instructions**</span></span>
* <span data-ttu-id="11a02-252">In der **Projekt** Bereich, suchen Sie **AttachToController** Skript.</span><span class="sxs-lookup"><span data-stu-id="11a02-252">In the **Project** panel, search **AttachToController** script.</span></span>
* <span data-ttu-id="11a02-253">Im Suchergebnis doppelklicken **AttachToController** Skript, um den Code in Visual Studio anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="11a02-253">From the search result, double click **AttachToController** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="11a02-254">**AttachToController-Skript**</span><span class="sxs-lookup"><span data-stu-id="11a02-254">**AttachToController script**</span></span>

<span data-ttu-id="11a02-255">Die **AttachToController** -Skript zeigt eine einfache Möglichkeit, alle Objekte in einer angegebenen Controller Händigkeit und das-Element anzufügen.</span><span class="sxs-lookup"><span data-stu-id="11a02-255">The **AttachToController** script provides a simple way to attach any objects to a specified controller handedness and element.</span></span>

<span data-ttu-id="11a02-256">In **AttachElementToController()**,</span><span class="sxs-lookup"><span data-stu-id="11a02-256">In **AttachElementToController()**,</span></span>
* <span data-ttu-id="11a02-257">Überprüfen Sie mit der Händigkeit **MotionControllerInfo.Handedness**</span><span class="sxs-lookup"><span data-stu-id="11a02-257">Check handedness using **MotionControllerInfo.Handedness**</span></span>
* <span data-ttu-id="11a02-258">Abrufen von bestimmten Element dem Controller mithilfe **MotionControllerInfo.TryGetElement()**</span><span class="sxs-lookup"><span data-stu-id="11a02-258">Get specific element of the controller using **MotionControllerInfo.TryGetElement()**</span></span>
* <span data-ttu-id="11a02-259">Klicken Sie nach dem Abrufen des Elements aus dem Controllermodell, übergeordneten Objekts im es transformieren, und lokale Position und Drehung des Objekts auf 0 (null) festgelegt.</span><span class="sxs-lookup"><span data-stu-id="11a02-259">After retrieving the element's transform from the controller model, parent the object under it and set object's local position & rotation to zero.</span></span>

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

<span data-ttu-id="11a02-260">Die einfachste Möglichkeit zum Verwenden **AttachToController** Skript ist das erben, wie im Fall von **ColorPickerWheel.**</span><span class="sxs-lookup"><span data-stu-id="11a02-260">The simplest way to use **AttachToController** script is to inherit from it, as we've done in the case of **ColorPickerWheel.**</span></span> <span data-ttu-id="11a02-261">Überschreiben Sie einfach die **OnAttachToController** und **OnDetatchFromController** Funktionen, um das Setup ausführen / Aufschlüsselung, wenn der Controller getrennt / gefunden wird.</span><span class="sxs-lookup"><span data-stu-id="11a02-261">Simply override the **OnAttachToController** and **OnDetatchFromController** functions to perform your setup / breakdown when the controller is detected / disconnected.</span></span>

<span data-ttu-id="11a02-262">**Anweisungen**</span><span class="sxs-lookup"><span data-stu-id="11a02-262">**Instructions**</span></span>
* <span data-ttu-id="11a02-263">In der **Projekt** Geben Sie im Suchfeld **ColorPickerWheel**.</span><span class="sxs-lookup"><span data-stu-id="11a02-263">In the **Project** panel, type in the search box **ColorPickerWheel**.</span></span> <span data-ttu-id="11a02-264">Sie finden ihn außerdem unter Assets/AppPrefabs /.</span><span class="sxs-lookup"><span data-stu-id="11a02-264">You can also find it under Assets/AppPrefabs/.</span></span>
* <span data-ttu-id="11a02-265">Ziehen Sie **ColorPickerWheel** prefab in die **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="11a02-265">Drag **ColorPickerWheel** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="11a02-266">Klicken Sie auf die **ColorPickerWheel** prefab in die **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="11a02-266">Click the **ColorPickerWheel** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="11a02-267">In der **Inspektor** panel, doppelklicken Sie auf **ColorPickerWheel** Skript, um den Code in Visual Studio anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="11a02-267">In the **Inspector** panel, double click **ColorPickerWheel** Script to see the code in Visual Studio.</span></span>

![ColorPickerWheel prefabs](images/mr213-colorpickerwheel-1000px.jpg)

<span data-ttu-id="11a02-269">**ColorPickerWheel-Skript**</span><span class="sxs-lookup"><span data-stu-id="11a02-269">**ColorPickerWheel script**</span></span>

<span data-ttu-id="11a02-270">Da **ColorPickerWheel** erbt **AttachToController**, es zeigt **Händigkeit** und **Element** in die  **Inspector** Bereich.</span><span class="sxs-lookup"><span data-stu-id="11a02-270">Since **ColorPickerWheel** inherits **AttachToController**, it shows **Handedness** and **Element** in the **Inspector** panel.</span></span> <span data-ttu-id="11a02-271">Wir werden die Benutzeroberfläche auf das Touchpad-Element, auf dem linken Controller angefügt werden.</span><span class="sxs-lookup"><span data-stu-id="11a02-271">We'll be attaching the UI to the Touchpad element on the left controller.</span></span>

![ColorPickerWheel-Skript](images/mr213-attachtocontroller-300px.jpg)

<span data-ttu-id="11a02-273">**ColorPickerWheel** überschreibt die **OnAttachToController** und **OnDetatchFromController** das Eingabeereignis abonnieren, die im nächsten Kapitel zur Farbauswahl mit verwendet wird Touchpad eingeben.</span><span class="sxs-lookup"><span data-stu-id="11a02-273">**ColorPickerWheel** overrides the **OnAttachToController** and **OnDetatchFromController** to subscribe to the input event which will be used in next chapter for color selection with touchpad input.</span></span>

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```
* <span data-ttu-id="11a02-274">**Speichern Sie** der Szene, und klicken Sie auf die **spielen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="11a02-274">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="11a02-275">**Alternative Methode zum Anfügen von Objekten auf Controller**</span><span class="sxs-lookup"><span data-stu-id="11a02-275">**Alternative method for attaching objects to the controllers**</span></span>

<span data-ttu-id="11a02-276">Es wird empfohlen, Ihre Skripts erben **AttachToController** und überschreiben **OnAttachToController**.</span><span class="sxs-lookup"><span data-stu-id="11a02-276">We recommend that your scripts inherit from **AttachToController** and override **OnAttachToController**.</span></span> <span data-ttu-id="11a02-277">Allerdings kann dies nicht immer möglich.</span><span class="sxs-lookup"><span data-stu-id="11a02-277">However, this may not always be possible.</span></span> <span data-ttu-id="11a02-278">Eine Alternative ist es als eigenständige Komponente verwenden.</span><span class="sxs-lookup"><span data-stu-id="11a02-278">An alternative is using it as a standalone component.</span></span> <span data-ttu-id="11a02-279">Dies kann nützlich sein, wenn Sie einen Controller ohne Umgestaltung Ihrer Skripts einer vorhandenen Prefab anfügen möchten.</span><span class="sxs-lookup"><span data-stu-id="11a02-279">This can be useful when you want to attach an existing prefab to a controller without refactoring your scripts.</span></span> <span data-ttu-id="11a02-280">Haben Sie einfach Ihre Klasse IsAttached festgelegt werden, warten vor dem Ausführen von Setup "true".</span><span class="sxs-lookup"><span data-stu-id="11a02-280">Simply have your class wait for IsAttached to be set to true before performing any setup.</span></span> <span data-ttu-id="11a02-281">Die einfachste Möglichkeit hierzu ist, mithilfe einer Coroutine für "Start".</span><span class="sxs-lookup"><span data-stu-id="11a02-281">The simplest way to do this is by using a coroutine for 'Start.'</span></span>

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a><span data-ttu-id="11a02-282">Kapitel 3 – arbeiten mit Touchpad-Eingabe</span><span class="sxs-lookup"><span data-stu-id="11a02-282">Chapter 3 - Working with touchpad input</span></span>

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a><span data-ttu-id="11a02-283">Ziele</span><span class="sxs-lookup"><span data-stu-id="11a02-283">Objectives</span></span>

* <span data-ttu-id="11a02-284">Erfahren Sie, wie Touchpad Eingabedaten Ereignisse abrufen</span><span class="sxs-lookup"><span data-stu-id="11a02-284">Learn how to get touchpad input data events</span></span>
* <span data-ttu-id="11a02-285">Informationen Sie zur Verwendung von Informationen zur Position der Achse Touchpad für Ihre app-Erfahrung</span><span class="sxs-lookup"><span data-stu-id="11a02-285">Learn how to use touchpad axis position information for your app experience</span></span>

### <a name="instructions"></a><span data-ttu-id="11a02-286">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="11a02-286">Instructions</span></span>

* <span data-ttu-id="11a02-287">In der **Hierarchie** auf **ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="11a02-287">In the **Hierarchy** panel, click **ColorPickerWheel**</span></span>
* <span data-ttu-id="11a02-288">In der **Inspektor** Bereich unter **Animatior**, Doppelklick **ColorPickerWheelController**</span><span class="sxs-lookup"><span data-stu-id="11a02-288">In the **Inspector** panel, under **Animatior**, double click **ColorPickerWheelController**</span></span>
* <span data-ttu-id="11a02-289">Sie werden sehen **Animator** Registerkarte geöffnet</span><span class="sxs-lookup"><span data-stu-id="11a02-289">You will be able to see **Animator** tab opened</span></span>

<span data-ttu-id="11a02-290">**Anzeigen/ausblenden-Benutzeroberfläche mit Unity Animationscontroller**</span><span class="sxs-lookup"><span data-stu-id="11a02-290">**Showing/hiding UI with Unity's Animation controller**</span></span>

<span data-ttu-id="11a02-291">Ein-und Ausblenden der **ColorPickerWheel** -Benutzeroberfläche mit Animation verwenden wir [Unity Animationssystem](https://docs.unity3d.com/Manual/AnimationOverview.html).</span><span class="sxs-lookup"><span data-stu-id="11a02-291">To show and hide the **ColorPickerWheel** UI with animation, we are using [Unity's animation system](https://docs.unity3d.com/Manual/AnimationOverview.html).</span></span> <span data-ttu-id="11a02-292">Festlegen der **ColorPickerWheel**des **Visible** Eigenschaft auf "true" oder "false" Trigger **anzeigen** und **ausblenden** Animationstrigger.</span><span class="sxs-lookup"><span data-stu-id="11a02-292">Setting the **ColorPickerWheel**'s **Visible** property to true or false triggers **Show** and **Hide** animation triggers.</span></span> <span data-ttu-id="11a02-293">**Anzeigen** und **ausblenden** Parameter werden definiert, der **ColorPickerWheelController** Animationscontroller.</span><span class="sxs-lookup"><span data-stu-id="11a02-293">**Show** and **Hide** parameters are defined in the **ColorPickerWheelController** animation controller.</span></span>

![Unity-Animationscontroller](images/mr123-animationcontroller-550px.jpg)

<span data-ttu-id="11a02-295">**Anweisungen**</span><span class="sxs-lookup"><span data-stu-id="11a02-295">**Instructions**</span></span>
* <span data-ttu-id="11a02-296">In der **Hierarchie** wählen **ColorPickerWheel** prefab</span><span class="sxs-lookup"><span data-stu-id="11a02-296">In the **Hierarchy** panel, select **ColorPickerWheel** prefab</span></span>
* <span data-ttu-id="11a02-297">In der **Inspektor** panel, doppelklicken Sie auf **ColorPickerWheel** Skript den Code in Visual Studio finden Sie unter</span><span class="sxs-lookup"><span data-stu-id="11a02-297">In the **Inspector** panel, double click **ColorPickerWheel** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="11a02-298">**ColorPickerWheel-Skript**</span><span class="sxs-lookup"><span data-stu-id="11a02-298">**ColorPickerWheel script**</span></span>

<span data-ttu-id="11a02-299">**ColorPickerWheel** Unity abonniert **InteractionSourceUpdated** Ereignis Touchpad Ereignisse zu überwachen.</span><span class="sxs-lookup"><span data-stu-id="11a02-299">**ColorPickerWheel** subscribes to Unity's **InteractionSourceUpdated** event to listen for touchpad events.</span></span>

<span data-ttu-id="11a02-300">In **InteractionSourceUpdated()**, zuerst das Skript überprüft, um sicherzustellen, dass es:</span><span class="sxs-lookup"><span data-stu-id="11a02-300">In **InteractionSourceUpdated()**, the script first checks to ensure that it:</span></span>
* <span data-ttu-id="11a02-301">ist tatsächlich ein Touchpad-Ereignis (obj.state. **TouchpadTouched**)</span><span class="sxs-lookup"><span data-stu-id="11a02-301">is actually a touchpad event (obj.state.**touchpadTouched**)</span></span>
* <span data-ttu-id="11a02-302">stammt aus dem linken Controller (obj.state.source. **Händigkeit**)</span><span class="sxs-lookup"><span data-stu-id="11a02-302">originates from the left controller (obj.state.source.**handedness**)</span></span>

<span data-ttu-id="11a02-303">Wenn beides zutrifft, positionieren Sie das Touchpad (obj.state. **TouchpadPosition**) zugewiesen wird **SelectorPosition**.</span><span class="sxs-lookup"><span data-stu-id="11a02-303">If both are true, the touchpad position (obj.state.**touchpadPosition**) is assigned to **selectorPosition**.</span></span>

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

<span data-ttu-id="11a02-304">In **Update()** basierend auf **sichtbar** Eigenschaft auslöst werden ein- / ausblenden-Animation-Trigger in der Farbauswahl Animator-Komponente</span><span class="sxs-lookup"><span data-stu-id="11a02-304">In **Update()**, based on **visible** property, it triggers Show and Hide animation triggers in the color picker's animator component</span></span>

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

<span data-ttu-id="11a02-305">In **Update()**, **SelectorPosition** wird verwendet, um ein Strahl unter dem Farbkreis Mesh "collider", umgewandelt. Dadurch kann eine UV-Position gibt.</span><span class="sxs-lookup"><span data-stu-id="11a02-305">In **Update()**, **selectorPosition** is used to cast a ray at the color wheel's mesh collider, which returns a UV position.</span></span> <span data-ttu-id="11a02-306">Diese Position kann dann verwendet werden, finden die Pixelkoordinate und Farbwert dem Farbkreis Textur.</span><span class="sxs-lookup"><span data-stu-id="11a02-306">This position can then be used to find the pixel coordinate and color value of the color wheel's texture.</span></span> <span data-ttu-id="11a02-307">Dieser Wert kann zugegriffen werden, um andere Skripts über die **SelectedColor** Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="11a02-307">This value is accessible to other scripts via the **SelectedColor** property.</span></span>

![Farbe Auswahl Wheel feinheiten beim Raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a><span data-ttu-id="11a02-309">Kapitel 4 – überschreiben die Controller-Modell</span><span class="sxs-lookup"><span data-stu-id="11a02-309">Chapter 4 - Overriding controller model</span></span>

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a><span data-ttu-id="11a02-310">Ziele</span><span class="sxs-lookup"><span data-stu-id="11a02-310">Objectives</span></span>

* <span data-ttu-id="11a02-311">Erfahren Sie, wie das Controllermodell mit einem benutzerdefinierten 3D-Modell außer Kraft zu setzen.</span><span class="sxs-lookup"><span data-stu-id="11a02-311">Learn how to override the controller model with a custom 3D model.</span></span>

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a><span data-ttu-id="11a02-313">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="11a02-313">Instructions</span></span>

* <span data-ttu-id="11a02-314">Klicken Sie auf **MotionControllers** in die **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="11a02-314">Click **MotionControllers** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="11a02-315">Klicken Sie auf den Kreis auf dem rechten Rand der **alternativen rechts Controller** Feld.</span><span class="sxs-lookup"><span data-stu-id="11a02-315">Click the circle on the right side of the **Alternate Right Controller** field.</span></span>
* <span data-ttu-id="11a02-316">Geben Sie in **"BrushController**", und wählen Sie das Prefab aus dem Ergebnis.</span><span class="sxs-lookup"><span data-stu-id="11a02-316">Type in **'BrushController**' and select the prefab from the result.</span></span> <span data-ttu-id="11a02-317">Sie finden diese Ressourcen/AppPrefabs/**BrushController**.</span><span class="sxs-lookup"><span data-stu-id="11a02-317">You can find it under Assets/AppPrefabs/**BrushController**.</span></span>
* <span data-ttu-id="11a02-318">Überprüfen Sie **alternativen richtige Modell immer verwenden**</span><span class="sxs-lookup"><span data-stu-id="11a02-318">Check **Always Use Alternate Right Model**</span></span>

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

<span data-ttu-id="11a02-320">Die **BrushController** Prefab muss nicht in aufgenommen werden die **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="11a02-320">The **BrushController** prefab does not have to be included in the **Hierarchy** panel.</span></span> <span data-ttu-id="11a02-321">Allerdings Auschecken von seinen untergeordneten Komponenten:</span><span class="sxs-lookup"><span data-stu-id="11a02-321">However, to check out its child components:</span></span>
* <span data-ttu-id="11a02-322">In der **Projekt** Bereich, geben Sie im **BrushController** , und ziehen Sie **BrushController** prefab in die **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="11a02-322">In the **Project** panel, type in **BrushController** and drag **BrushController** prefab into the **Hierarchy** panel.</span></span>

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

<span data-ttu-id="11a02-324">Sie finden die **Tipp** -Komponente in **BrushController**.</span><span class="sxs-lookup"><span data-stu-id="11a02-324">You will find the **Tip** component in **BrushController**.</span></span> <span data-ttu-id="11a02-325">Wir verwenden seine Transformation Starten/Beenden von Zeichnen von Linien.</span><span class="sxs-lookup"><span data-stu-id="11a02-325">We will use its transform to start/stop drawing lines.</span></span>
* <span data-ttu-id="11a02-326">Löschen der **BrushController** aus der **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="11a02-326">Delete the **BrushController** from the **Hierarchy** panel.</span></span>
* <span data-ttu-id="11a02-327">**Speichern Sie** der Szene, und klicken Sie auf die **spielen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="11a02-327">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="11a02-328">Sie werden sehen, dass das Pinsel-Modell mit der rechten Motion-Controller ersetzt.</span><span class="sxs-lookup"><span data-stu-id="11a02-328">You will be able to see the brush model replaced the right-hand motion controller.</span></span>

## <a name="chapter-5---painting-with-select-input"></a><span data-ttu-id="11a02-329">Kapitel 5 – Eingabe Zeichnen mit Select-Anweisung</span><span class="sxs-lookup"><span data-stu-id="11a02-329">Chapter 5 - Painting with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a><span data-ttu-id="11a02-330">Ziele</span><span class="sxs-lookup"><span data-stu-id="11a02-330">Objectives</span></span>

* <span data-ttu-id="11a02-331">Erfahren Sie, wie das Ereignis auswählen-Schaltfläche zum Starten und beenden eine Strichzeichnung verwenden</span><span class="sxs-lookup"><span data-stu-id="11a02-331">Learn how to use the Select button event to start and stop a line drawing</span></span>

### <a name="instructions"></a><span data-ttu-id="11a02-332">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="11a02-332">Instructions</span></span>

* <span data-ttu-id="11a02-333">Suche **BrushController** prefab in die **Projekt** Bereich.</span><span class="sxs-lookup"><span data-stu-id="11a02-333">Search **BrushController** prefab in the **Project** panel.</span></span>
* <span data-ttu-id="11a02-334">In der **Inspektor** panel, doppelklicken Sie auf **BrushController** Skript den Code in Visual Studio finden Sie unter</span><span class="sxs-lookup"><span data-stu-id="11a02-334">In the **Inspector** panel, double click **BrushController** Script to see the code in Visual Studio</span></span>

<span data-ttu-id="11a02-335">**BrushController-Skript**</span><span class="sxs-lookup"><span data-stu-id="11a02-335">**BrushController script**</span></span>

<span data-ttu-id="11a02-336">**BrushController** abonniert die InteractionManager des **InteractionSourcePressed** und **InteractionSourceReleased** Ereignisse.</span><span class="sxs-lookup"><span data-stu-id="11a02-336">**BrushController** subscribes to the InteractionManager's **InteractionSourcePressed** and **InteractionSourceReleased** events.</span></span> <span data-ttu-id="11a02-337">Wenn **InteractionSourcePressed** Ereignis wird ausgelöst, des Pinsels **zeichnen** -Eigenschaftensatz auf "true", wenn **InteractionSourceReleased** Ereignis wird ausgelöst, des Pinsels **Zeichnen** Eigenschaft auf "false" festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="11a02-337">When **InteractionSourcePressed** event is triggered, the brush's **Draw** property is set to true; when **InteractionSourceReleased** event is triggered, the brush's **Draw** property is set to false.</span></span>

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

<span data-ttu-id="11a02-338">Während **zeichnen** nastaven NA hodnotu True gibt an, der Pinsel generiert Punkte in einem instanziierten Unity **LineRenderer**.</span><span class="sxs-lookup"><span data-stu-id="11a02-338">While **Draw** is set to true, the brush will generate points in an instantiated Unity **LineRenderer**.</span></span> <span data-ttu-id="11a02-339">Ein Verweis auf dieses Prefab bleibt im des Pinsels **Stroke Prefab** Feld.</span><span class="sxs-lookup"><span data-stu-id="11a02-339">A reference to this prefab is kept in the brush's **Stroke Prefab** field.</span></span>

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

<span data-ttu-id="11a02-340">Verwenden Sie die zurzeit ausgewählte Farbe aus der Auswahl-Farbkreis-Benutzeroberfläche **BrushController** benötigt einen Verweis auf die **ColorPickerWheel** Objekt.</span><span class="sxs-lookup"><span data-stu-id="11a02-340">To use the currently selected color from the color picker wheel UI, **BrushController** needs to have a reference to the **ColorPickerWheel** object.</span></span> <span data-ttu-id="11a02-341">Da die **BrushController** Prefab zur Laufzeit als eine Ersatzcontroller instanziiert wird, müssen alle Verweise auf Objekte in der Szene zur Laufzeit festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="11a02-341">Because the **BrushController** prefab is instantiated at runtime as a replacement controller, any references to objects in the scene will have to be set at runtime.</span></span> <span data-ttu-id="11a02-342">In diesem Fall verwenden wir **GameObject.FindObjectOfType** zum Suchen der **ColorPickerWheel**:</span><span class="sxs-lookup"><span data-stu-id="11a02-342">In this case we use **GameObject.FindObjectOfType** to locate the **ColorPickerWheel**:</span></span>

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```
* <span data-ttu-id="11a02-343">**Speichern Sie** der Szene, und klicken Sie auf die **spielen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="11a02-343">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="11a02-344">Sie werden zum Zeichnen der Linien und zeichnen, verwenden die auswählen-Schaltfläche am rechten Controller.</span><span class="sxs-lookup"><span data-stu-id="11a02-344">You will be able to draw the lines and paint using the select button on the right-hand controller.</span></span>

## <a name="chapter-6---object-spawning-with-select-input"></a><span data-ttu-id="11a02-345">Kapitel 6: Eingabe Objekt erzeugen mit Select-Anweisung</span><span class="sxs-lookup"><span data-stu-id="11a02-345">Chapter 6 - Object spawning with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a><span data-ttu-id="11a02-346">Ziele</span><span class="sxs-lookup"><span data-stu-id="11a02-346">Objectives</span></span>

* <span data-ttu-id="11a02-347">Erfahren Sie, wie Sie mit der Option, und fassen Sie die Schaltfläche Eingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="11a02-347">Learn how to use Select and Grasp button input events</span></span>
* <span data-ttu-id="11a02-348">Erfahren Sie, wie zum Instanziieren von Objekten</span><span class="sxs-lookup"><span data-stu-id="11a02-348">Learn how to instantiate objects</span></span>

### <a name="instructions"></a><span data-ttu-id="11a02-349">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="11a02-349">Instructions</span></span>

* <span data-ttu-id="11a02-350">In der **Projekt** geben **ObjectSpawner** in das Suchfeld.</span><span class="sxs-lookup"><span data-stu-id="11a02-350">In the **Project** panel, type **ObjectSpawner** in the search box.</span></span> <span data-ttu-id="11a02-351">Sie finden ihn außerdem unter Assets/AppPrefabs /</span><span class="sxs-lookup"><span data-stu-id="11a02-351">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="11a02-352">Ziehen Sie die **ObjectSpawner** prefab in die **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="11a02-352">Drag the **ObjectSpawner** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="11a02-353">Klicken Sie auf **ObjectSpawner** in die **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="11a02-353">Click **ObjectSpawner** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="11a02-354">**ObjectSpawner** verfügt über ein Feld mit dem Namen **Farbe Quelle**.</span><span class="sxs-lookup"><span data-stu-id="11a02-354">**ObjectSpawner** has a field named **Color Source**.</span></span>
* <span data-ttu-id="11a02-355">Von der **Hierarchie** ziehen Sie die **ColorPickerWheel** Verweis in dieses Feld.</span><span class="sxs-lookup"><span data-stu-id="11a02-355">From the **Hierarchy** panel, drag the **ColorPickerWheel** reference into this field.</span></span>

![Objekt Spawner Inspector](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* <span data-ttu-id="11a02-357">Klicken Sie auf die **ObjectSpawner** prefab in die **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="11a02-357">Click the **ObjectSpawner** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="11a02-358">In der **Inspektor** panel, doppelklicken Sie auf **ObjectSpawner** Skript, um den Code in Visual Studio anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="11a02-358">In the **Inspector** panel, double click **ObjectSpawner** Script to see the code in Visual Studio.</span></span>

<span data-ttu-id="11a02-359">**ObjectSpawner-Skript**</span><span class="sxs-lookup"><span data-stu-id="11a02-359">**ObjectSpawner script**</span></span>

<span data-ttu-id="11a02-360">Die **ObjectSpawner** Kopien eines primitiven Netzes (Cube, Kugel, Zylinder) in den Bereich instanziiert.</span><span class="sxs-lookup"><span data-stu-id="11a02-360">The **ObjectSpawner** instantiates copies of a primitive mesh (cube, sphere, cylinder) into the space.</span></span> <span data-ttu-id="11a02-361">Wenn eine **InteractionSourcePressed** erkannt wird, überprüft er die rechts-oder Linkshändigkeit und es ist ein **InteractionSourcePressType.Grasp** oder **InteractionSourcePressType.Select** das Ereignis.</span><span class="sxs-lookup"><span data-stu-id="11a02-361">When a **InteractionSourcePressed** is detected it checks the handedness and if it's an **InteractionSourcePressType.Grasp** or **InteractionSourcePressType.Select** event.</span></span>

<span data-ttu-id="11a02-362">Für eine **verstehen** -Ereignis, es erhöht den Index des aktuellen Netztyp (Kugel, Cube, Zylinder)</span><span class="sxs-lookup"><span data-stu-id="11a02-362">For a **Grasp** event, it increments the index of current mesh type (sphere, cube, cylinder)</span></span>

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

<span data-ttu-id="11a02-363">Für eine **wählen** Ereignis im **SpawnObject()**, ein neues Objekt ist instanziiert, ohne übergeordnetes Element und veröffentlicht Sie in der ganzen Welt.</span><span class="sxs-lookup"><span data-stu-id="11a02-363">For a **Select** event, in **SpawnObject()**, a new object is instantiated, un-parented and released into the world.</span></span>

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detatch the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

<span data-ttu-id="11a02-364">Die **ObjectSpawner** verwendet die **ColorPickerWheel** zum Festlegen der Farbe des Materials für die des Anzeigeobjekts.</span><span class="sxs-lookup"><span data-stu-id="11a02-364">The **ObjectSpawner** uses the **ColorPickerWheel** to set the color of the display object's material.</span></span> <span data-ttu-id="11a02-365">Erzeugten Objekte werden bei einer Instanz der in diesem Material, so sie ihre Farbe behalten.</span><span class="sxs-lookup"><span data-stu-id="11a02-365">Spawned objects are given an instance of this material so they will retain their color.</span></span>
* <span data-ttu-id="11a02-366">**Speichern Sie** der Szene, und klicken Sie auf die **spielen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="11a02-366">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="11a02-367">Sie werden die Objekte mit der Schaltfläche "verstehen" ändern und erzeugen Objekte mit der Schaltfläche auswählen können.</span><span class="sxs-lookup"><span data-stu-id="11a02-367">You will be able to change the objects with the Grasp button and spawn objects with the Select button.</span></span>

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a><span data-ttu-id="11a02-368">Erstellen Sie und Bereitstellen Sie der app, Mixed Reality-Portal</span><span class="sxs-lookup"><span data-stu-id="11a02-368">Build and deploy app to Mixed Reality Portal</span></span>
* <span data-ttu-id="11a02-369">Wählen Sie in Unity **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="11a02-369">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="11a02-370">Klicken Sie auf **öffnen Szenen hinzufügen** aktuelle Szene zum Hinzufügen der **Szenen In Build**.</span><span class="sxs-lookup"><span data-stu-id="11a02-370">Click **Add Open Scenes** to add current scene to the **Scenes In Build**.</span></span>
* <span data-ttu-id="11a02-371">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="11a02-371">Click **Build**.</span></span>
* <span data-ttu-id="11a02-372">Erstellen Sie eine **neuer Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="11a02-372">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="11a02-373">Mausklick die **App** Ordner.</span><span class="sxs-lookup"><span data-stu-id="11a02-373">Single click the **App** folder.</span></span>
* <span data-ttu-id="11a02-374">Klicken Sie auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="11a02-374">Click **Select Folder**.</span></span>
* <span data-ttu-id="11a02-375">Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="11a02-375">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="11a02-376">Öffnen der **App** Ordner.</span><span class="sxs-lookup"><span data-stu-id="11a02-376">Open the **App** folder.</span></span>
* <span data-ttu-id="11a02-377">Doppelklick **YourSceneName.sln** Visual Studio-Projektmappendatei.</span><span class="sxs-lookup"><span data-stu-id="11a02-377">Double click **YourSceneName.sln** Visual Studio Solution file.</span></span>
* <span data-ttu-id="11a02-378">Verwenden obere auf der Symbolleiste in Visual Studio, ändern Sie das Ziel vom Debugmodus in den **Version** und ARM, **X64**.</span><span class="sxs-lookup"><span data-stu-id="11a02-378">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X64**.</span></span>
* <span data-ttu-id="11a02-379">Klicken Sie auf den Dropdownpfeil neben der Schaltfläche "Geräte", und wählen **lokalen Computer**.</span><span class="sxs-lookup"><span data-stu-id="11a02-379">Click on the drop-down arrow next to the Device button, and select **Local Machine**.</span></span>
* <span data-ttu-id="11a02-380">Klicken Sie auf **Debuggen -> Starten ohne debugging** in das Menü, oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="11a02-380">Click **Debug -> Start Without debugging** in the menu or press **Ctrl + F5**.</span></span>

<span data-ttu-id="11a02-381">Die app wird jetzt erstellt und in Mixed Reality-Portal installiert.</span><span class="sxs-lookup"><span data-stu-id="11a02-381">Now the app is built and installed in Mixed Reality Portal.</span></span> <span data-ttu-id="11a02-382">Sie können es erneut über das Menü "Start" in Mixed Reality-Portal starten.</span><span class="sxs-lookup"><span data-stu-id="11a02-382">You can launch it again through Start menu in Mixed Reality Portal.</span></span>

## <a name="advanced-design---brush-tools-with-radial-layout"></a><span data-ttu-id="11a02-383">Erweiterte Design - Pinsel Tools mit radialen layout</span><span class="sxs-lookup"><span data-stu-id="11a02-383">Advanced design - Brush tools with radial layout</span></span>

![MixedReality213 Main](images/mr213-main-600px.jpg)

<span data-ttu-id="11a02-385">In diesem Kapitel lernen Sie, wie das Standardmodell für Controller während der Übertragung durch eine Auflistung der benutzerdefinierten Pinsel-Tool ersetzt.</span><span class="sxs-lookup"><span data-stu-id="11a02-385">In this chapter, you will learn how to replace the default motion controller model with a custom brush tool collection.</span></span> <span data-ttu-id="11a02-386">Zu Referenzzwecken finden Sie die vollständige Szene **MixedReality213Advanced** unter **Szenen** Ordner.</span><span class="sxs-lookup"><span data-stu-id="11a02-386">For your reference, you can find the completed scene **MixedReality213Advanced** under **Scenes** folder.</span></span>

### <a name="instructions"></a><span data-ttu-id="11a02-387">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="11a02-387">Instructions</span></span>

* <span data-ttu-id="11a02-388">In der **Projekt** geben **BrushSelector** in das Suchfeld.</span><span class="sxs-lookup"><span data-stu-id="11a02-388">In the **Project** panel, type **BrushSelector** in the search box .</span></span> <span data-ttu-id="11a02-389">Sie finden ihn außerdem unter Assets/AppPrefabs /</span><span class="sxs-lookup"><span data-stu-id="11a02-389">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="11a02-390">Ziehen Sie die **BrushSelector** prefab in die **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="11a02-390">Drag the **BrushSelector** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="11a02-391">Für die Organisation, erstellen Sie ein leeres GameObject, dem Namen **Pinsel**</span><span class="sxs-lookup"><span data-stu-id="11a02-391">For organization, create an empty GameObject called **Brushes**</span></span>
* <span data-ttu-id="11a02-392">Ziehen Sie folgende Prefabs aus der **Projekt** -Bereich in **Pinsel**</span><span class="sxs-lookup"><span data-stu-id="11a02-392">Drag following prefabs from the **Project** panel into **Brushes**</span></span>
    * <span data-ttu-id="11a02-393">Assets/AppPrefabs/**BrushFat**</span><span class="sxs-lookup"><span data-stu-id="11a02-393">Assets/AppPrefabs/**BrushFat**</span></span>
    * <span data-ttu-id="11a02-394">Assets/AppPrefabs/**BrushThin**</span><span class="sxs-lookup"><span data-stu-id="11a02-394">Assets/AppPrefabs/**BrushThin**</span></span>
    * <span data-ttu-id="11a02-395">Assets/AppPrefabs/**Eraser**</span><span class="sxs-lookup"><span data-stu-id="11a02-395">Assets/AppPrefabs/**Eraser**</span></span>
    * <span data-ttu-id="11a02-396">Assets/AppPrefabs/**MarkerFat**</span><span class="sxs-lookup"><span data-stu-id="11a02-396">Assets/AppPrefabs/**MarkerFat**</span></span>
    * <span data-ttu-id="11a02-397">Assets/AppPrefabs/**MarkerThin**</span><span class="sxs-lookup"><span data-stu-id="11a02-397">Assets/AppPrefabs/**MarkerThin**</span></span>
    * <span data-ttu-id="11a02-398">Assets/AppPrefabs/**Pencil**</span><span class="sxs-lookup"><span data-stu-id="11a02-398">Assets/AppPrefabs/**Pencil**</span></span>

![Pinsel](images/mixedreality213-brushes-250px.png)
* <span data-ttu-id="11a02-400">Klicken Sie auf **MotionControllers** prefab in die **Hierarchie** Bereich.</span><span class="sxs-lookup"><span data-stu-id="11a02-400">Click **MotionControllers** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="11a02-401">In der **Inspektor** Bereich, deaktivieren Sie **immer alternative rechts Modell** auf die **Motion-Controller-Schnellansicht**</span><span class="sxs-lookup"><span data-stu-id="11a02-401">In the **Inspector** panel, uncheck **Always Use Alternate Right Model** on the **Motion Controller Visualizer**</span></span>
* <span data-ttu-id="11a02-402">In der **Hierarchie** auf **BrushSelector**</span><span class="sxs-lookup"><span data-stu-id="11a02-402">In the **Hierarchy** panel, click **BrushSelector**</span></span>
* <span data-ttu-id="11a02-403">**BrushSelector** verfügt über ein Feld mit dem Namen **ColorPicker**</span><span class="sxs-lookup"><span data-stu-id="11a02-403">**BrushSelector** has a field named **ColorPicker**</span></span>
* <span data-ttu-id="11a02-404">Von der **Hierarchie** ziehen Sie die **ColorPickerWheel** in **ColorPicker** -Feld in der **Inspektor** Bereich.</span><span class="sxs-lookup"><span data-stu-id="11a02-404">From the **Hierarchy** panel, drag the **ColorPickerWheel** into **ColorPicker** field in the **Inspector** panel.</span></span>

![Weisen Sie ColorPickerWheel zu Selektor Pinsel](images/mr213-brushselector-500px.jpg)
* <span data-ttu-id="11a02-406">In der **Hierarchie** Bereich unter **BrushSelector** prefab, wählen die **Menü** Objekt.</span><span class="sxs-lookup"><span data-stu-id="11a02-406">In the **Hierarchy** panel, under **BrushSelector** prefab, select the **Menu** object.</span></span>
* <span data-ttu-id="11a02-407">In der **Inspektor** Bereich unter der **LineObjectCollection** Komponente, öffnen die **Objekte** Array-Dropdownliste.</span><span class="sxs-lookup"><span data-stu-id="11a02-407">In the **Inspector** panel, under the **LineObjectCollection** component, open the **Objects** array dropdown.</span></span> <span data-ttu-id="11a02-408">Sie sehen, dass 6 leere Steckplätze.</span><span class="sxs-lookup"><span data-stu-id="11a02-408">You will see 6 empty slots.</span></span>
* <span data-ttu-id="11a02-409">Von der **Hierarchie** ziehen Sie jede der Prefabs übergeordnetes Element besitzt, klicken Sie unter den **Pinsel** "gameobject" in diesen Slots in beliebiger Reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="11a02-409">From the **Hierarchy** panel, drag each of the prefabs parented under the **Brushes** GameObject into these slots in any order.</span></span> <span data-ttu-id="11a02-410">(Stellen Sie sicher, dass Sie den prefabs (Vorlagen) von der Szene nicht den Prefabs im Projektordner ziehen können.)</span><span class="sxs-lookup"><span data-stu-id="11a02-410">(Make sure you're dragging the prefabs from the scene, not the prefabs in the project folder.)</span></span>

![Pinsel-Auswahl](images/mr213-brushselectorbrushes-700px.jpg)

<span data-ttu-id="11a02-412">**BrushSelector prefabs**</span><span class="sxs-lookup"><span data-stu-id="11a02-412">**BrushSelector prefab**</span></span>

<span data-ttu-id="11a02-413">Da die **BrushSelector** erbt **AttachToController**, es zeigt **Händigkeit** und **Element** "Optionen" der  **Inspector** Bereich.</span><span class="sxs-lookup"><span data-stu-id="11a02-413">Since the **BrushSelector** inherits **AttachToController**, it shows **Handedness** and **Element** options in the **Inspector** panel.</span></span> <span data-ttu-id="11a02-414">Ausgewählten **rechts** und **zeigt darstellen** Pinsel Tools an den rechten-Controller mit vorwärts angefügt.</span><span class="sxs-lookup"><span data-stu-id="11a02-414">We selected **Right** and **Pointing Pose** to attach brush tools to the right hand controller with forward direction.</span></span>

<span data-ttu-id="11a02-415">Die **BrushSelector** verwendet zwei Hilfsprogramme:</span><span class="sxs-lookup"><span data-stu-id="11a02-415">The **BrushSelector** makes use of two utilities:</span></span>
* <span data-ttu-id="11a02-416">**Ellipse**: verwendet, um Punkte im Raum auf eine Form "Ellipse" zu generieren.</span><span class="sxs-lookup"><span data-stu-id="11a02-416">**Ellipse**: used to generate points in space along an ellipse shape.</span></span>
* <span data-ttu-id="11a02-417">**LineObjectCollection**: verteilt die Objekte, die mit den Punkten, die von jeder Zeile-Klasse (z.B. "Ellipse") generiert.</span><span class="sxs-lookup"><span data-stu-id="11a02-417">**LineObjectCollection**: distributes objects using the points generated by any Line class (eg, Ellipse).</span></span> <span data-ttu-id="11a02-418">Dies ist, was wir verwenden unsere Pinsel auf die Form "Ellipse" zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="11a02-418">This is what we'll be using to place our brushes along the Ellipse shape.</span></span>

<span data-ttu-id="11a02-419">In Kombination können diese Hilfsprogramme verwendet werden, zum Erstellen eines radialen Menüs.</span><span class="sxs-lookup"><span data-stu-id="11a02-419">When combined, these utilities can be used to create a radial menu.</span></span>

<span data-ttu-id="11a02-420">**LineObjectCollection-Skript**</span><span class="sxs-lookup"><span data-stu-id="11a02-420">**LineObjectCollection script**</span></span>

<span data-ttu-id="11a02-421">**LineObjectCollection** verfügt über Steuerelemente für die Größe, Position und Drehung der Objekte, die entlang der Zeile verteilt.</span><span class="sxs-lookup"><span data-stu-id="11a02-421">**LineObjectCollection** has controls for the size, position and rotation of objects distributed along its line.</span></span> <span data-ttu-id="11a02-422">Dies ist nützlich zum Erstellen von radialen Menüs wie das Pinsel-Selektor.</span><span class="sxs-lookup"><span data-stu-id="11a02-422">This is useful for creating radial menus like the brush selector.</span></span> <span data-ttu-id="11a02-423">Erstellen Sie die Darstellung der Pinsel, Skalierung Einrichten von nothing, wie sie die Position Center ausgewählt Ansatz der **ObjectScale** Spitzen in den Mittelpunkt und den Rändern an den Kanten-Kurve.</span><span class="sxs-lookup"><span data-stu-id="11a02-423">To create the appearance of brushes that scale up from nothing as they approach the center selected position, the **ObjectScale** curve peaks in the center and tapers off at the edges.</span></span>

<span data-ttu-id="11a02-424">**BrushSelector-Skript**</span><span class="sxs-lookup"><span data-stu-id="11a02-424">**BrushSelector script**</span></span>

<span data-ttu-id="11a02-425">Im Fall von der **BrushSelector**, haben wir uns entschieden, prozedurale Animation verwenden.</span><span class="sxs-lookup"><span data-stu-id="11a02-425">In the case of the **BrushSelector**, we've chosen to use procedural animation.</span></span> <span data-ttu-id="11a02-426">Zunächst Pinsel Modelle in einer Ellipse durch verteilt werden die **LineObjectCollection** Skript.</span><span class="sxs-lookup"><span data-stu-id="11a02-426">First, brush models are distributed in an ellipse by the **LineObjectCollection** script.</span></span> <span data-ttu-id="11a02-427">Klicken Sie dann jeden Pinsel ist verantwortlich für die Verwaltung der Position des Benutzers verfügen, die basierend auf dessen **"DisplayMode"** -Wert, der Änderungen, auf der Auswahl basiert.</span><span class="sxs-lookup"><span data-stu-id="11a02-427">Then, each brush is responsible for maintaining its position in the user's hand based on its **DisplayMode** value, which changes based on the selection.</span></span> <span data-ttu-id="11a02-428">Wir haben uns ein prozedurales Verfahren für die hohe Wahrscheinlichkeit von Übergängen an Position Pinsel wird unterbrochen, da der Benutzer Brushes auswählt.</span><span class="sxs-lookup"><span data-stu-id="11a02-428">We chose a procedural approach because of the high probability of brush position transitions being interrupted as the user selects brushes.</span></span> <span data-ttu-id="11a02-429">Mecanim Animationen können Unterbrechungen ordnungsgemäß behandeln, aber dies eher zu viel komplizierter ist als ein einfacher Lerp Vorgang sein.</span><span class="sxs-lookup"><span data-stu-id="11a02-429">Mecanim animations can handle interruptions gracefully, but it tends to be more complicated than a simple Lerp operation.</span></span>

<span data-ttu-id="11a02-430">**BrushSelector** verwendet eine Kombination aus beidem.</span><span class="sxs-lookup"><span data-stu-id="11a02-430">**BrushSelector** uses a combination of both.</span></span> <span data-ttu-id="11a02-431">Wenn Touchpad Eingabe erkannt wird, wird Pinseloptionen sichtbar und zentrales hochskalieren auf das Menü "radial".</span><span class="sxs-lookup"><span data-stu-id="11a02-431">When touchpad input is detected, brush options become visible and scale up along the radial menu.</span></span> <span data-ttu-id="11a02-432">Nach Ablauf eines Timeouts (dies besagt, dass der Benutzer eine Auswahl getroffen hat)-Optionen der Pinsel skalieren nach unten in diesem Fall nur den ausgewählten Pinsel verlassen.</span><span class="sxs-lookup"><span data-stu-id="11a02-432">After a timeout period (which indicates that the user has made a selection) the brush options scale down again, leaving only the selected brush.</span></span>

<span data-ttu-id="11a02-433">**Visualisieren von Touchpad-Eingabe**</span><span class="sxs-lookup"><span data-stu-id="11a02-433">**Visualizing touchpad input**</span></span>

<span data-ttu-id="11a02-434">Selbst in Fällen, in dem das Controllermodell vollständig ersetzt wurde, kann es hilfreich sein, auf die ursprünglichen modelleingaben Eingabe angezeigt sein.</span><span class="sxs-lookup"><span data-stu-id="11a02-434">Even in cases where the controller model has been completely replaced, it can be helpful to show input on the original model inputs.</span></span> <span data-ttu-id="11a02-435">Dadurch wird die Aktionen des Benutzers in der Praxis erden.</span><span class="sxs-lookup"><span data-stu-id="11a02-435">This helps to ground the user's actions in reality.</span></span> <span data-ttu-id="11a02-436">Für die **BrushSelector** haben wir uns entschieden, machen Sie das Touchpad kurz sichtbar, wenn die Eingabe empfangen wird.</span><span class="sxs-lookup"><span data-stu-id="11a02-436">For the **BrushSelector** we've chosen to make the touchpad briefly visible when the input is received.</span></span> <span data-ttu-id="11a02-437">Dies erfolgte durch Abrufen des Touchpad-Elements aus dem Controller, und Ersetzen Sie dabei mit einem benutzerdefinierten Material, dessen Material, und klicken Sie dann das Anwenden eines Farbverlaufs des Materials Farbe basierend auf der letzten Zeit Touchpad Eingabe empfangen wurde.</span><span class="sxs-lookup"><span data-stu-id="11a02-437">This was done by retrieving the Touchpad element from the controller, replacing its material with a custom material, then applying a gradient to that material's color based on the last time touchpad input was received.</span></span>

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }
            
    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

<span data-ttu-id="11a02-438">**Pinsel-Tool-Auswahl mit Touchpad-Eingabe**</span><span class="sxs-lookup"><span data-stu-id="11a02-438">**Brush tool selection with touchpad input**</span></span>

<span data-ttu-id="11a02-439">Wenn der Selektor Pinsel Touchpad des gedrückten Eingabe erkennt, wird die Position der Eingabe um festzustellen, ob sie nach links oder rechts wurde überprüft.</span><span class="sxs-lookup"><span data-stu-id="11a02-439">When the brush selector detects touchpad's pressed input, it checks the position of the input to determine if it was to the left or right.</span></span>

<span data-ttu-id="11a02-440">**Strichstärke mit selectPressedAmount**</span><span class="sxs-lookup"><span data-stu-id="11a02-440">**Stroke thickness with selectPressedAmount**</span></span>

<span data-ttu-id="11a02-441">Statt die **InteractionSourcePressType.Select** Ereignis in der **InteractionSourcePressed()**, erhalten Sie den analogen Wert, der den gedrückten Betrag über **SelectPressedAmount**.</span><span class="sxs-lookup"><span data-stu-id="11a02-441">Instead of the **InteractionSourcePressType.Select** event in the **InteractionSourcePressed()**, you can get the analog value of the pressed amount through **selectPressedAmount**.</span></span> <span data-ttu-id="11a02-442">Dieser Wert kann abgerufen werden, **InteractionSourceUpdated()**.</span><span class="sxs-lookup"><span data-stu-id="11a02-442">This value can be retrieved in **InteractionSourceUpdated()**.</span></span>

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

<span data-ttu-id="11a02-443">**Radierer-Skript**</span><span class="sxs-lookup"><span data-stu-id="11a02-443">**Eraser script**</span></span>

<span data-ttu-id="11a02-444">**Radierer** ist ein spezieller Typ des Pinsels, die die Basis überschreibt **Pinsel**des **DrawOverTime()** Funktion.</span><span class="sxs-lookup"><span data-stu-id="11a02-444">**Eraser** is a special type of brush that overrides the base **Brush**'s **DrawOverTime()** function.</span></span> <span data-ttu-id="11a02-445">Beim Zeichnen auf "true" festgelegt ist, überprüft der Radierer, um festzustellen, ob die QuickInfo mit vorhandenen Pinselstriche überschneidet.</span><span class="sxs-lookup"><span data-stu-id="11a02-445">While Draw is true, the eraser checks to see if its tip intersects with any existing brush strokes.</span></span> <span data-ttu-id="11a02-446">Wenn Ja, sind sie an eine Warteschlange, die nach-unten verkleinert werden hinzugefügt und gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="11a02-446">If it does, they are added to a queue to be shrunk down and deleted.</span></span>

## <a name="advanced-design---teleportation-and-locomotion"></a><span data-ttu-id="11a02-447">Erweiterte Design - Teleportation und locomotion</span><span class="sxs-lookup"><span data-stu-id="11a02-447">Advanced design - Teleportation and locomotion</span></span>

<span data-ttu-id="11a02-448">Wenn Sie zulassen möchten, den Benutzer mit Teleportation Ministick mithilfe der Szene verschieben, verwenden Sie **MixedRealityCameraParent** anstelle von **MixedRealityCamera**.</span><span class="sxs-lookup"><span data-stu-id="11a02-448">If you want to allow the user to move around the scene with teleportation using thumbstick, use **MixedRealityCameraParent** instead of **MixedRealityCamera**.</span></span> <span data-ttu-id="11a02-449">Sie müssen auch hinzufügen **InputManager** und **DefaultCusor**.</span><span class="sxs-lookup"><span data-stu-id="11a02-449">You also need to add **InputManager** and **DefaultCusor**.</span></span> <span data-ttu-id="11a02-450">Da **MixedRealityCameraParent** enthält bereits **MotionControllers** und **Grenze** als untergeordneten Komponenten, entfernen Sie vorhandene  **MotionControllers** und **Umgebung** prefab.</span><span class="sxs-lookup"><span data-stu-id="11a02-450">Since **MixedRealityCameraParent** already includes **MotionControllers** and **Boundary** as child components, you should remove existing **MotionControllers** and **Environment** prefab.</span></span>

### <a name="instructions"></a><span data-ttu-id="11a02-451">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="11a02-451">Instructions</span></span>

* <span data-ttu-id="11a02-452">In der **Hierarchie** panel, löschen Sie **MixedRealityCamera**, **Umgebung** und **MotionControllers**</span><span class="sxs-lookup"><span data-stu-id="11a02-452">In the **Hierarchy** panel, delete **MixedRealityCamera**, **Environment** and **MotionControllers**</span></span>
* <span data-ttu-id="11a02-453">Von der **Projektfenster**, suchen, und ziehen Sie die folgenden prefabs (Vorlagen) in der **Hierarchie** Bereich:</span><span class="sxs-lookup"><span data-stu-id="11a02-453">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="11a02-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span><span class="sxs-lookup"><span data-stu-id="11a02-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span></span>
    * <span data-ttu-id="11a02-455">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span><span class="sxs-lookup"><span data-stu-id="11a02-455">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span></span>
    * <span data-ttu-id="11a02-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span><span class="sxs-lookup"><span data-stu-id="11a02-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span></span>

![Die Kamera übergeordneten Mixed Reality](images/mr213-cameraparent-300px.png)
* <span data-ttu-id="11a02-458">In der **Hierarchie** auf **Eingabe-Manager**</span><span class="sxs-lookup"><span data-stu-id="11a02-458">In the **Hierarchy** panel, click **Input Manager**</span></span>
* <span data-ttu-id="11a02-459">In der **Inspektor** panel, führen Sie einen Bildlauf nach unten, um die **einfache einfache Auswahl der Zeiger** Abschnitt</span><span class="sxs-lookup"><span data-stu-id="11a02-459">In the **Inspector** panel, scroll down to the **Simple Single Pointer Selector** section</span></span>
* <span data-ttu-id="11a02-460">Von der **Hierarchie** ziehen Sie **DefaultCursor** in **Cursor** Feld</span><span class="sxs-lookup"><span data-stu-id="11a02-460">From the **Hierarchy** panel, drag **DefaultCursor** into **Cursor** field</span></span>

![Zuweisen von DefaultCursor](images/mr213-defaultcursor-500px.png)
* <span data-ttu-id="11a02-462">**Speichern Sie** der Szene, und klicken Sie auf die **spielen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="11a02-462">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="11a02-463">Sie werden Ministick verwenden, um Links/rechts bzw. Teleport zu drehen.</span><span class="sxs-lookup"><span data-stu-id="11a02-463">You will be able to use the thumbstick to rotate left/right or teleport.</span></span>

## <a name="the-end"></a><span data-ttu-id="11a02-464">Das Ende</span><span class="sxs-lookup"><span data-stu-id="11a02-464">The end</span></span>

<span data-ttu-id="11a02-465">Und das Ende dieses Tutorials ist!</span><span class="sxs-lookup"><span data-stu-id="11a02-465">And that's the end of this tutorial!</span></span> <span data-ttu-id="11a02-466">Sie haben Folgendes gelernt:</span><span class="sxs-lookup"><span data-stu-id="11a02-466">You learned:</span></span>
* <span data-ttu-id="11a02-467">Verwendung von Motion-Controller-Modellen in Unity Spielmodus und Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="11a02-467">How to work with motion controller models in Unity's game mode and runtime.</span></span>
* <span data-ttu-id="11a02-468">Wie Sie verschiedene Typen von Schaltflächenereignisse und ihren Anwendungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="11a02-468">How to use different types of button events and their applications.</span></span>
* <span data-ttu-id="11a02-469">Gewusst wie overlay-Elemente der Benutzeroberfläche auf dem Controller oder vollständig anpassen.</span><span class="sxs-lookup"><span data-stu-id="11a02-469">How to overlay UI elements on top of the controller or fully customize it.</span></span>

<span data-ttu-id="11a02-470">Sie können nun damit beginnen, erstellen eigene beeindruckende Erfahrung mit Motion-Controller.</span><span class="sxs-lookup"><span data-stu-id="11a02-470">You are now ready to start creating your own immersive experience with motion controllers!</span></span>

## <a name="completed-scenes"></a><span data-ttu-id="11a02-471">Abgeschlossene Szenen</span><span class="sxs-lookup"><span data-stu-id="11a02-471">Completed scenes</span></span>

* <span data-ttu-id="11a02-472">In Unity **Projekt** Bereich, klicken Sie auf die **Szenen** Ordner.</span><span class="sxs-lookup"><span data-stu-id="11a02-472">In Unity's **Project** panel click on the **Scenes** folder.</span></span>
* <span data-ttu-id="11a02-473">Sehen Sie zwei Unity Sceens **MixedReality213** und **MixedReality213Advanced**.</span><span class="sxs-lookup"><span data-stu-id="11a02-473">You will find two Unity sceens **MixedReality213** and **MixedReality213Advanced**.</span></span>
    * <span data-ttu-id="11a02-474">**MixedReality213**: Vollständige Szene mit einzelnen Pinsel</span><span class="sxs-lookup"><span data-stu-id="11a02-474">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="11a02-475">**MixedReality213Advanced**: Vollständige Szene mit mehreren Pinsel, mit der Schaltfläche auswählen, drücken Sie Betrag-Beispiel</span><span class="sxs-lookup"><span data-stu-id="11a02-475">**MixedReality213Advanced**: Completed scene with multiple brush with select button's press amount example</span></span>

## <a name="see-also"></a><span data-ttu-id="11a02-476">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="11a02-476">See also</span></span>

* [<span data-ttu-id="11a02-477">MR Eingabe 213-Projektdateien</span><span class="sxs-lookup"><span data-stu-id="11a02-477">MR Input 213 project files</span></span>](https://github.com/Microsoft/MixedReality213)
* [<span data-ttu-id="11a02-478">Mixed Reality-Toolkit - Motion-Controller-Test-Szene</span><span class="sxs-lookup"><span data-stu-id="11a02-478">Mixed Reality Toolkit - Motion Controller Test scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [<span data-ttu-id="11a02-479">Ziehen Sie Mixed Reality-Toolkit – Funktionsweise</span><span class="sxs-lookup"><span data-stu-id="11a02-479">Mixed Reality Toolkit - Grab Mechanics</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [<span data-ttu-id="11a02-480">Richtlinien für die Entwicklung von Motion-controller</span><span class="sxs-lookup"><span data-stu-id="11a02-480">Motion controller development guidelines</span></span>](motion-controllers.md)
