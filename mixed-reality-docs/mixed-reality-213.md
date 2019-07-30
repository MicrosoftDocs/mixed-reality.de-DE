---
title: Mr-Eingabe 213
description: Befolgen Sie dieses Lernprogramm zum Programmieren mit Unity, Visual Studio und immersiven Headsets, um die Details von Bewegungs Controllern kennenzulernen.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, immersive, Motion Controller, Academy, Tutorial
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516388"
---
>[!NOTE]
><span data-ttu-id="fc6e8-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="fc6e8-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="fc6e8-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="fc6e8-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="fc6e8-108">Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="fc6e8-109">Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-213-motion-controllers"></a><span data-ttu-id="fc6e8-110">Mr-Eingabe 213: Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="fc6e8-110">MR Input 213: Motion controllers</span></span>

<span data-ttu-id="fc6e8-111">Bewegungs Controller in der Mixed Reality-Welt fügen eine weitere Interaktivität hinzu.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-111">Motion controllers in the mixed reality world add another level of interactivity.</span></span> <span data-ttu-id="fc6e8-112">Mit [Motion-Controllern](motion-controllers.md)können wir direkt mit Objekten auf natürlichere Weise interagieren, ähnlich wie bei den physischen Interaktionen in der Praxis, wodurch das Eintauchen und die Freude an Ihrer APP verbessert werden.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-112">With [motion controllers](motion-controllers.md), we can directly interact with objects in a more natural way, similar to our physical interactions in real life, increasing immersion and delight in your app experience.</span></span>

<span data-ttu-id="fc6e8-113">In der Eingabe 213 werden die Eingabeereignisse des Bewegungs Controllers durch die Erstellung einer einfachen räumlichen Darstellung untersucht.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-113">In MR Input 213, we will explore the motion controller's input events by creating a simple spatial painting experience.</span></span> <span data-ttu-id="fc6e8-114">Mit dieser APP können Benutzer im dreidimensionalen Raum mit verschiedenen Arten von Pinsel und Farben zeichnen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-114">With this app, users can paint in three-dimensional space with various types of brushes and colors.</span></span>

## <a name="topics-covered-in-this-tutorial"></a><span data-ttu-id="fc6e8-115">In diesem Tutorial behandelte Themen</span><span class="sxs-lookup"><span data-stu-id="fc6e8-115">Topics covered in this tutorial</span></span>

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|<span data-ttu-id="fc6e8-119">**Controller Visualisierung**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-119">**Controller visualization**</span></span>|<span data-ttu-id="fc6e8-120">**Controller Eingabeereignisse**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-120">**Controller input events**</span></span>|<span data-ttu-id="fc6e8-121">**Benutzerdefinierter Controller und Benutzeroberfläche**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-121">**Custom controller and UI**</span></span>|
|<span data-ttu-id="fc6e8-122">Erfahren Sie, wie Sie Motion Controller-Modelle im Spielmodus und der Laufzeit von Unity Renderern.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-122">Learn how to render motion controller models in Unity's game mode and runtime.</span></span>|<span data-ttu-id="fc6e8-123">Lernen Sie die verschiedenen Arten von Schaltflächen Ereignissen und deren Anwendungen kennen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-123">Understand different types of button events and their applications.</span></span>|<span data-ttu-id="fc6e8-124">Erfahren Sie, wie Sie Benutzeroberflächen Elemente oberhalb des Controllers überlagern oder vollständig anpassen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-124">Learn how to overlay UI elements on top of the controller or fully customize it.</span></span>|

## <a name="device-support"></a><span data-ttu-id="fc6e8-125">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="fc6e8-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="fc6e8-126">Natürlich</span><span class="sxs-lookup"><span data-stu-id="fc6e8-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="fc6e8-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="fc6e8-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="fc6e8-128"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="fc6e8-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="fc6e8-129">Mr-Eingabe 213: Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="fc6e8-129">MR Input 213: Motion controllers</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="fc6e8-130">✔️</span><span class="sxs-lookup"><span data-stu-id="fc6e8-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="fc6e8-131">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="fc6e8-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="fc6e8-132">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="fc6e8-132">Prerequisites</span></span>

<span data-ttu-id="fc6e8-133">Sehen Sie sich die Installations Checkliste für immersive Headsets auf [dieser Seite](install-the-tools.md)an.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-133">See the installation checklist for immersive headsets on [this page](install-the-tools.md).</span></span>

* <span data-ttu-id="fc6e8-134">Für dieses Tutorial ist [Unity 2017.2.1 P2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-134">This tutorial requires [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span></span>

### <a name="project-files"></a><span data-ttu-id="fc6e8-135">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="fc6e8-135">Project files</span></span>

* <span data-ttu-id="fc6e8-136">[Laden Sie die Dateien herunter](https://github.com/Microsoft/MixedReality213/archive/master.zip) , die für das Projekt erforderlich sind, und extrahieren Sie die Dateien auf den Desktop.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-136">[Download the files](https://github.com/Microsoft/MixedReality213/archive/master.zip) required by the project and extract the files to the Desktop.</span></span>

>[!NOTE]
><span data-ttu-id="fc6e8-137">Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/MixedReality213).</span><span class="sxs-lookup"><span data-stu-id="fc6e8-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/MixedReality213).</span></span>

## <a name="unity-setup"></a><span data-ttu-id="fc6e8-138">Unity-Setup</span><span class="sxs-lookup"><span data-stu-id="fc6e8-138">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a><span data-ttu-id="fc6e8-139">Ziele</span><span class="sxs-lookup"><span data-stu-id="fc6e8-139">Objectives</span></span>

* <span data-ttu-id="fc6e8-140">Optimieren von Unity für die Windows Mixed Reality-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="fc6e8-140">Optimize Unity for Windows Mixed Reality development</span></span>
* <span data-ttu-id="fc6e8-141">Mixed Reality-Kamera einrichten</span><span class="sxs-lookup"><span data-stu-id="fc6e8-141">Setup Mixed Reality Camera</span></span>
* <span data-ttu-id="fc6e8-142">Umgebung einrichten</span><span class="sxs-lookup"><span data-stu-id="fc6e8-142">Setup environment</span></span>

### <a name="instructions"></a><span data-ttu-id="fc6e8-143">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="fc6e8-143">Instructions</span></span>

* <span data-ttu-id="fc6e8-144">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-144">Start Unity.</span></span>
* <span data-ttu-id="fc6e8-145">Wählen Sie **Öffnen**aus.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-145">Select **Open**.</span></span>
* <span data-ttu-id="fc6e8-146">Navigieren Sie zu Ihrem Desktop, und suchen Sie den Ordner **MixedReality213-Master** , den Sie zuvor nicht archiviert haben.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-146">Navigate to your Desktop and find the **MixedReality213-master** folder you previously unarchived.</span></span>
* <span data-ttu-id="fc6e8-147">Klicken Sie auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-147">Click **Select Folder**.</span></span>
* <span data-ttu-id="fc6e8-148">Nachdem Unity das Laden von Projektdateien abgeschlossen hat, kann der Unity-Editor angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-148">Once Unity finishes loading project files, you will be able to see Unity editor.</span></span>
* <span data-ttu-id="fc6e8-149">Wählen Sie in Unity **Datei >** Buildeinstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-149">In Unity, select **File > Build Settings**.</span></span>

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* <span data-ttu-id="fc6e8-151">Wählen Sie in der Liste **Plattform** **universelle Windows-Plattform** aus, und klicken Sie auf die Schaltfläche **Plattform wechseln** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-151">Select **Universal Windows Platform** in the **Platform** list and click the **Switch Platform** button.</span></span>
* <span data-ttu-id="fc6e8-152">Zielgerät auf **beliebiges Gerät** festlegen</span><span class="sxs-lookup"><span data-stu-id="fc6e8-152">Set Target Device to **Any device**</span></span>
* <span data-ttu-id="fc6e8-153">Buildtyp auf **D3D** festlegen</span><span class="sxs-lookup"><span data-stu-id="fc6e8-153">Set Build Type to **D3D**</span></span>
* <span data-ttu-id="fc6e8-154">SDK auf **Letztes installiert** festlegen</span><span class="sxs-lookup"><span data-stu-id="fc6e8-154">Set SDK to **Latest Installed**</span></span>
* <span data-ttu-id="fc6e8-155">**Unity C# -Projekte** überprüfen</span><span class="sxs-lookup"><span data-stu-id="fc6e8-155">Check **Unity C# Projects**</span></span>
    * <span data-ttu-id="fc6e8-156">Auf diese Weise können Sie Skriptdateien im Visual Studio-Projekt ändern, ohne das Unity-Projekt neu zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-156">This allows you modify script files in the Visual Studio project without rebuilding Unity project.</span></span>
* <span data-ttu-id="fc6e8-157">Klicken Sie auf **Player-Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-157">Click **Player Settings**.</span></span>
* <span data-ttu-id="fc6e8-158">Scrollen Sie im **Inspektor** -Panel nach unten.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-158">In the **Inspector** panel, scroll down to the bottom</span></span>
* <span data-ttu-id="fc6e8-159">Aktivieren Sie in den XR-Einstellungen die Option **unterstützte virtuelle**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-159">In XR Settings, check **Virtual Reality Supported**</span></span>
* <span data-ttu-id="fc6e8-160">Wählen Sie unter Virtual Reality sdert **Windows Mixed Reality** aus.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-160">Under Virtual Reality SDKs, select **Windows Mixed Reality**</span></span>

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* <span data-ttu-id="fc6e8-162">Fenster "Buildeinstellungen" schließen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-162">Close **Build Settings** window.</span></span>

### <a name="project-structure"></a><span data-ttu-id="fc6e8-163">Projektstruktur</span><span class="sxs-lookup"><span data-stu-id="fc6e8-163">Project structure</span></span>

<span data-ttu-id="fc6e8-164">In diesem Tutorial wird **[Mixed Reality Toolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** verwendet.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-164">This tutorial uses **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span></span> <span data-ttu-id="fc6e8-165">Die Releases können auf [dieser Seite](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-165">You can find the releases on [this page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span>

![Projectstructure](images/mr213-projectstructure-650px.png)

<span data-ttu-id="fc6e8-167">**Abgeschlossene Szenen für Ihre Referenz**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-167">**Completed scenes for your reference**</span></span>
* <span data-ttu-id="fc6e8-168">Im Ordner " **Szenen** " finden Sie zwei abgeschlossene Unity-Szenen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-168">You will find two completed Unity scenes under **Scenes** folder.</span></span>
    * <span data-ttu-id="fc6e8-169">**MixedReality213**: Abgeschlossene Szene mit einem Pinsel</span><span class="sxs-lookup"><span data-stu-id="fc6e8-169">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="fc6e8-170">**MixedReality213Advanced**: Abgeschlossene Szene für erweiterten Entwurf mit mehreren Pinseln</span><span class="sxs-lookup"><span data-stu-id="fc6e8-170">**MixedReality213Advanced**: Completed scene for advanced design with multiple brushes</span></span>

<span data-ttu-id="fc6e8-171">**Neue Szenen Einrichtung für das Tutorial**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-171">**New Scene setup for the tutorial**</span></span>
* <span data-ttu-id="fc6e8-172">Klicken Sie in Unity auf **Datei > neue Szene** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-172">In Unity, click **File > New Scene**</span></span>
* <span data-ttu-id="fc6e8-173">**Hauptkamera** und **Direktionales Licht** löschen</span><span class="sxs-lookup"><span data-stu-id="fc6e8-173">Delete **Main Camera** and **Directional Light**</span></span>
* <span data-ttu-id="fc6e8-174">Suchen Sie im **Projekt Panel**die folgenden Prefabs, und ziehen Sie Sie in das **Hierarchie** Panel:</span><span class="sxs-lookup"><span data-stu-id="fc6e8-174">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="fc6e8-175">Assets/holotoolkit/Input/Prefabs/**mixedrealitycamera**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span></span>
    * <span data-ttu-id="fc6e8-176">Assets/appprefabs/**Umgebung**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-176">Assets/AppPrefabs/**Environment**</span></span>

![Kamera und Umgebung](images/mr213-cameraenvironment-300px.jpg)
* <span data-ttu-id="fc6e8-178">Es gibt zwei Kamera-präfaben im Mixed Reality Toolkit:</span><span class="sxs-lookup"><span data-stu-id="fc6e8-178">There are two camera prefabs in Mixed Reality Toolkit:</span></span>
    * <span data-ttu-id="fc6e8-179">**Mixedrealitycamera. Prefab**: Nur Kamera</span><span class="sxs-lookup"><span data-stu-id="fc6e8-179">**MixedRealityCamera.prefab**: Camera only</span></span>
    * <span data-ttu-id="fc6e8-180">**Mixedrealitycameraparent. Prefab**: Kamera + teleportierung + Grenze</span><span class="sxs-lookup"><span data-stu-id="fc6e8-180">**MixedRealityCameraParent.prefab**: Camera + Teleportation + Boundary</span></span>
    * <span data-ttu-id="fc6e8-181">In diesem Tutorial verwenden wir **mixedrealitycamera** ohne teleportationsfeature.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-181">In this tutorial, we will use **MixedRealityCamera** without teleportation feature.</span></span> <span data-ttu-id="fc6e8-182">Aus diesem Grund haben wir eine einfache **Umgebungs** Vorschau hinzugefügt, die eine grundlegende Oberfläche enthält, um das Gefühl des Benutzers zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-182">Because of this, we added simple **Environment** prefab which contains a basic floor to make the user feel grounded.</span></span>
    * <span data-ttu-id="fc6e8-183">Weitere Informationen zur teleportung mit **mixedrealitycameraparent**finden Sie unter [Advanced Design-Teleportations-und fortbewegungs](#advanced-design---teleportation-and-locomotion) Modus.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-183">To learn more about the teleportation with **MixedRealityCameraParent**, see [Advanced design - Teleportation and locomotion](#advanced-design---teleportation-and-locomotion)</span></span>

<span data-ttu-id="fc6e8-184">**Skybox-Setup**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-184">**Skybox setup**</span></span>
* <span data-ttu-id="fc6e8-185">Klicken Sie auf **Fenster > Beleuchtungs > Einstellungen**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-185">Click **Window > Lighting > Settings**</span></span>
* <span data-ttu-id="fc6e8-186">Klicken Sie auf den Kreis auf der rechten Seite des **Felds Skybox-Material** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-186">Click the circle on the right side of the **Skybox Material field**</span></span>
* <span data-ttu-id="fc6e8-187">Geben Sie "Gray" ein, und wählen Sie **skyboxgray** aus.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-187">Type in ‘gray’ and select **SkyboxGray**</span></span>

<span data-ttu-id="fc6e8-188">(Assets/appprefabs/Support/Materials/skyboxgray. Mat)</span><span class="sxs-lookup"><span data-stu-id="fc6e8-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span></span>

![Festlegen von Skybox](images/mr123-skyboxsetting-400px.jpg)
* <span data-ttu-id="fc6e8-190">Aktivieren Sie die **Skybox** -Option, um die zugewiesene graue Gradient Skybox anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-190">Check **Skybox** option to be able to see assigned gray gradient skybox</span></span>

![Option ' Skybox ' umschalten](images/mr213-skyboxcheck-400px.jpg)
* <span data-ttu-id="fc6e8-192">Die Szene mit mixedrealitycamera, Environment und Gray Skybox sieht wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-192">The scene with MixedRealityCamera, Environment and gray skybox will look like this.</span></span>

![MixedReality213-Umgebung](images/mr213-environment-600px.jpg)
* <span data-ttu-id="fc6e8-194">Klicken Sie auf **Datei > Szene speichern** unter</span><span class="sxs-lookup"><span data-stu-id="fc6e8-194">Click **File > Save Scene as**</span></span>
* <span data-ttu-id="fc6e8-195">**Speichern** Sie Ihre Szene unter Szenen Ordner mit einem beliebigen Namen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-195">**Save** your scene under Scenes folder with any name</span></span>

## <a name="chapter-1---controller-visualization"></a><span data-ttu-id="fc6e8-196">Kapitel 1: Controller Visualisierung</span><span class="sxs-lookup"><span data-stu-id="fc6e8-196">Chapter 1 - Controller visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a><span data-ttu-id="fc6e8-197">Ziele</span><span class="sxs-lookup"><span data-stu-id="fc6e8-197">Objectives</span></span>

* <span data-ttu-id="fc6e8-198">Erfahren Sie, wie Sie Motion Controller-Modelle im Unity-Spielmodus und zur Laufzeit Renderern.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-198">Learn how to render motion controller models in Unity's game mode and at runtime.</span></span>

<span data-ttu-id="fc6e8-199">Windows Mixed Reality bietet ein animiertes Controller Modell für die Controller Visualisierung.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-199">Windows Mixed Reality provides an animated controller model for controller visualization.</span></span> <span data-ttu-id="fc6e8-200">Es gibt mehrere Ansätze, die Sie für die Controller Visualisierung in Ihrer APP verwenden können:</span><span class="sxs-lookup"><span data-stu-id="fc6e8-200">There are several approaches you can take for controller visualization in your app:</span></span>
* <span data-ttu-id="fc6e8-201">Standard-Standard Controller ohne Änderung verwenden</span><span class="sxs-lookup"><span data-stu-id="fc6e8-201">Default - Using default controller without modification</span></span>
* <span data-ttu-id="fc6e8-202">Hybride Verwendung des Standard Controllers, aber anpassen einiger Elemente oder Überlagern von UI-Komponenten</span><span class="sxs-lookup"><span data-stu-id="fc6e8-202">Hybrid - Using default controller, but customizing some of its elements or overlaying UI components</span></span>
* <span data-ttu-id="fc6e8-203">Ersetzung: Verwenden eines eigenen benutzerdefinierten 3D-Modells für den Controller</span><span class="sxs-lookup"><span data-stu-id="fc6e8-203">Replacement - Using your own customized 3D model for the controller</span></span>

<span data-ttu-id="fc6e8-204">In diesem Kapitel werden die Beispiele dieser Controller Anpassungen erläutert.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-204">In this chapter, we will learn about the examples of these controller customizations.</span></span>

### <a name="instructions"></a><span data-ttu-id="fc6e8-205">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="fc6e8-205">Instructions</span></span>

* <span data-ttu-id="fc6e8-206">Geben Sie im **Projekt** Panel im Suchfeld den Text " **mutioncontrollers** " ein.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-206">In the **Project** panel, type **MotionControllers** in the search box .</span></span> <span data-ttu-id="fc6e8-207">Sie finden es auch unter Assets/holotoolkit/Input/Prefabs/.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-207">You can also find it under Assets/HoloToolkit/Input/Prefabs/.</span></span>
* <span data-ttu-id="fc6e8-208">Ziehen Sie den vorfab " **mueconcontrollers** " in das **Hierarchie** Panel.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-208">Drag the **MotionControllers** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="fc6e8-209">Klicken Sie im **Hierarchie** Panel **auf die** vorfab-vorfab.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-209">Click on the **MotionControllers** prefab in the **Hierarchy** panel.</span></span>

<span data-ttu-id="fc6e8-210">**Vorfab von "mutioncontrollers"**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-210">**MotionControllers prefab**</span></span>

<span data-ttu-id="fc6e8-211">Die Prefab-Funktion von " **mueconcontrollers** " verfügt über ein Skript " **mutioncontrollervisualizer** ", das die Slots für alternative Controller Modelle enthält</span><span class="sxs-lookup"><span data-stu-id="fc6e8-211">**MotionControllers** prefab has a **MotionControllerVisualizer** script which provides the slots for alternate controller models.</span></span> <span data-ttu-id="fc6e8-212">Wenn Sie Ihre eigenen, benutzerdefinierten 3D-Modelle zuweisen, z. b. eine Hand oder ein Schwert, und die Option "immer alternatives nach links/rechts verwenden" aktivieren, werden Sie anstelle des Standardmodells angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-212">If you assign your own custom 3D models such as a hand or a sword and check 'Always Use Alternate Left/Right Model', you will see them instead of the default model.</span></span> <span data-ttu-id="fc6e8-213">Wir verwenden diesen Slot in Kapitel 4, um das Controller Modell durch einen Pinsel zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-213">We will use this slot in Chapter 4 to replace the controller model with a brush.</span></span>

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

<span data-ttu-id="fc6e8-215">**Anweisungen**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-215">**Instructions**</span></span>
* <span data-ttu-id="fc6e8-216">Doppelklicken Sie im **Inspektor** -Panel auf das Skript " **mutioncontrollervisualizer** ", um den Code in Visual Studio anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-216">In the **Inspector** panel, double click **MotionControllerVisualizer** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="fc6e8-217">**Skript für die "mutioncontrollervisualizer"**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-217">**MotionControllerVisualizer script**</span></span>

<span data-ttu-id="fc6e8-218">Die Klassen " **mutioncontrollervisualizer** " und " **mutioncontrollerinfo** " bieten die Möglichkeit, auf & Ändern der Standard Controller Modelle zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-218">The **MotionControllerVisualizer** and **MotionControllerInfo** classes provide the means to access & modify the default controller models.</span></span> <span data-ttu-id="fc6e8-219">" **Mutioncontrollervisualizer** " abonniert das **Interaction sourcefound** -Ereignis von Unity und instanziiert Controller Modelle automatisch, wenn Sie gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-219">**MotionControllerVisualizer** subscribes to Unity's **InteractionSourceDetected** event and automatically instantiates controller models when they are found.</span></span>

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

<span data-ttu-id="fc6e8-220">Die Controller Modelle werden gemäß [der gltf-Spezifikation](https://github.com/KhronosGroup/glTF)zugestellt.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-220">The controller models are delivered according to [the glTF specification](https://github.com/KhronosGroup/glTF).</span></span> <span data-ttu-id="fc6e8-221">Dieses Format wurde erstellt, um ein gemeinsames Format bereitzustellen, während gleichzeitig der Prozess für das übertragen und entpacken von 3D-Assets verbessert wurde.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-221">This format has been created to provide a common format, while improving the process behind transmitting and unpacking 3D assets.</span></span> <span data-ttu-id="fc6e8-222">In diesem Fall müssen wir die Controller Modelle zur Laufzeit abrufen und laden, da wir die Benutzerumgebung so nahtlos wie möglich gestalten möchten, und es ist nicht garantiert, welche Version der Bewegungs Controller der Benutzer verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-222">In this case, we need to retrieve and load the controller models at runtime, as we want to make the user's experience as seamless as possible, and it's not guaranteed which version of the motion controllers the user might be using.</span></span> <span data-ttu-id="fc6e8-223">In diesem Kurs wird über das Mixed Reality Toolkit eine Version des [unitygltf-Projekts](https://github.com/KhronosGroup/UnityGLTF)der Khronos-Gruppe verwendet.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-223">This course, via the Mixed Reality Toolkit, uses a version of the Khronos Group's [UnityGLTF project](https://github.com/KhronosGroup/UnityGLTF).</span></span>

<span data-ttu-id="fc6e8-224">Nachdem der Controller übermittelt wurde, können die Skripts mithilfe von " **futioncontrollerinfo** " die Transformationen für bestimmte Controller Elemente suchen, damit Sie sich ordnungsgemäß positionieren können.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-224">Once the controller has been delivered, scripts can use **MotionControllerInfo** to find the transforms for specific controller elements so they can correctly position themselves.</span></span>

<span data-ttu-id="fc6e8-225">In einem späteren Kapitel erfahren Sie, wie diese Skripts zum Anfügen von UI-Elementen an die Controller verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-225">In a later chapter, we will learn how to use these scripts to attach UI elements to the controllers.</span></span>

<span data-ttu-id="fc6e8-226">*In einigen Skripts finden Sie Code Blöcke mit **#if! UNITY_EDITOR** oder **UNITY_WSA**. Diese Code Blöcke werden nur für die UWP-Laufzeit ausgeführt, wenn Sie Windows bereitstellen. Dies liegt daran, dass der Satz von APIs, der vom Unity-Editor und der UWP-App-Laufzeit verwendet wird, anders ist.*</span><span class="sxs-lookup"><span data-stu-id="fc6e8-226">*In some scripts, you will find code blocks with **#if !UNITY_EDITOR** or **UNITY_WSA**. These code blocks run only on the UWP runtime when you deploy to Windows. This is because the set of APIs used by the Unity editor and the UWP app runtime are different.*</span></span>
* <span data-ttu-id="fc6e8-227">**Speichern** Sie die Szene, und klicken Sie auf die Schaltfläche **abspielen** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-227">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="fc6e8-228">Sie können die Szene mit Motion Controller in Ihrem Headset sehen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-228">You will be able to see the scene with motion controllers in your headset.</span></span> <span data-ttu-id="fc6e8-229">Sie können ausführliche Animationen für Schaltflächen Klicks, die Fingereingabe Bewegung und Touchpad Touch-Hervorhebung sehen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-229">You can see detailed animations for button clicks, thumbstick movement, and touchpad touch highlighting.</span></span>

![MR213_Controller-Visualisierungs Standard](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a><span data-ttu-id="fc6e8-231">Kapitel 2: Anfügen von Benutzeroberflächen Elementen an den Controller</span><span class="sxs-lookup"><span data-stu-id="fc6e8-231">Chapter 2 - Attaching UI elements to the controller</span></span>

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a><span data-ttu-id="fc6e8-232">Ziele</span><span class="sxs-lookup"><span data-stu-id="fc6e8-232">Objectives</span></span>

* <span data-ttu-id="fc6e8-233">Weitere Informationen zu den Elementen der Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="fc6e8-233">Learn about the elements of the motion controllers</span></span>
* <span data-ttu-id="fc6e8-234">Erfahren Sie, wie Sie Objekte an bestimmte Teile der Controller anfügen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-234">Learn how to attach objects to specific parts of the controllers</span></span>

<span data-ttu-id="fc6e8-235">In diesem Kapitel erfahren Sie, wie Sie dem Controller Benutzeroberflächen Elemente hinzufügen, auf die der Benutzer jederzeit problemlos zugreifen und diese bearbeiten kann.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-235">In this chapter, you will learn how to add user interface elements to the controller which the user can easily access and manipulate at anytime.</span></span> <span data-ttu-id="fc6e8-236">Außerdem erfahren Sie, wie Sie mithilfe der Touchpad-Eingabe eine einfache Benutzeroberfläche für die Farbauswahl hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-236">You will also learn how to add a simple color picker UI using the touchpad input.</span></span>

### <a name="instructions"></a><span data-ttu-id="fc6e8-237">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="fc6e8-237">Instructions</span></span>

* <span data-ttu-id="fc6e8-238">Suchen Sie im **Projekt** Panel das Skript " **mutioncontrollerinfo** ".</span><span class="sxs-lookup"><span data-stu-id="fc6e8-238">In the **Project** panel, search **MotionControllerInfo** script.</span></span>
* <span data-ttu-id="fc6e8-239">Doppelklicken Sie im Suchergebnis auf das Skript " **mutioncontrollerinfo** ", um den Code in Visual Studio anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-239">From the search result, double click **MotionControllerInfo** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="fc6e8-240">**"Mutioncontrollerinfo"-Skript**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-240">**MotionControllerInfo script**</span></span>

<span data-ttu-id="fc6e8-241">Der erste Schritt besteht darin, das Element des Controllers auszuwählen, an das die Benutzeroberfläche angefügt werden soll.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-241">The first step is to choose which element of the controller you want the UI to attach to.</span></span> <span data-ttu-id="fc6e8-242">Diese Elemente werden in **controllerelementenum** in **MotionControllerInfo.cs**definiert.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-242">These elements are defined in **ControllerElementEnum** in **MotionControllerInfo.cs**.</span></span>

![MR213-Element](images/mr213-motioncontrollerelements-1000px.jpg)
* <span data-ttu-id="fc6e8-244">**Home**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-244">**Home**</span></span>
* <span data-ttu-id="fc6e8-245">**Stehen**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-245">**Menu**</span></span>
* <span data-ttu-id="fc6e8-246">**Gespür**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-246">**Grasp**</span></span>
* <span data-ttu-id="fc6e8-247">**Ministick**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-247">**Thumbstick**</span></span>
* <span data-ttu-id="fc6e8-248">**Auswahl**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-248">**Select**</span></span>
* <span data-ttu-id="fc6e8-249">**Touchpad**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-249">**Touchpad**</span></span>
* <span data-ttu-id="fc6e8-250">**Zeige** Darstellung – dieses Element stellt die Spitze des Controllers dar, der auf die Vorwärtsrichtung zeigt.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-250">**Pointing pose** – this element represents the tip of the controller pointing forward direction.</span></span>

<span data-ttu-id="fc6e8-251">**Anweisungen**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-251">**Instructions**</span></span>
* <span data-ttu-id="fc6e8-252">Suchen Sie im **Projekt** Panel das Skript " **attachdecontroller** ".</span><span class="sxs-lookup"><span data-stu-id="fc6e8-252">In the **Project** panel, search **AttachToController** script.</span></span>
* <span data-ttu-id="fc6e8-253">Doppelklicken Sie im Suchergebnis auf **attachdecontroller** -Skript, um den Code in Visual Studio anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-253">From the search result, double click **AttachToController** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="fc6e8-254">**Attachtoicontroller-Skript**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-254">**AttachToController script**</span></span>

<span data-ttu-id="fc6e8-255">Das anfügecontroller-Skript bietet eine einfache Möglichkeit, beliebige Objekte an eine angegebene Controller häntigkeit und ein Element anzufügen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-255">The **AttachToController** script provides a simple way to attach any objects to a specified controller handedness and element.</span></span>

<span data-ttu-id="fc6e8-256">In **attachelementto Controller ()** ,</span><span class="sxs-lookup"><span data-stu-id="fc6e8-256">In **AttachElementToController()**,</span></span>
* <span data-ttu-id="fc6e8-257">Überprüfen Sie die häntigkeit mithilfe von "" "" "" "" " **.**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-257">Check handedness using **MotionControllerInfo.Handedness**</span></span>
* <span data-ttu-id="fc6e8-258">Bestimmtes Element des Controllers mithilfe von " **mutioncontrollerinfo. trygetelement ()** " erhalten</span><span class="sxs-lookup"><span data-stu-id="fc6e8-258">Get specific element of the controller using **MotionControllerInfo.TryGetElement()**</span></span>
* <span data-ttu-id="fc6e8-259">Nachdem Sie die Transformation des Elements aus dem Controller Modell abgerufen haben, übergeordnet Sie das Objekt darunter, und legen Sie die lokale Position des Objekts & Drehung auf NULL fest.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-259">After retrieving the element's transform from the controller model, parent the object under it and set object's local position & rotation to zero.</span></span>

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

<span data-ttu-id="fc6e8-260">Die einfachste Möglichkeit zur Verwendung des **attachtoicontroller** -Skripts ist die Vererbung von der Anwendung, wie dies im Fall von **colorpickerwheel** der Fall ist.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-260">The simplest way to use **AttachToController** script is to inherit from it, as we've done in the case of **ColorPickerWheel.**</span></span> <span data-ttu-id="fc6e8-261">Überschreiben Sie einfach die Funktionen **onattachdecontroller** und **ondetatchfromcontroller** , um Setup/Aufschlüsselung auszuführen, wenn der Controller erkannt/getrennt wird.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-261">Simply override the **OnAttachToController** and **OnDetatchFromController** functions to perform your setup / breakdown when the controller is detected / disconnected.</span></span>

<span data-ttu-id="fc6e8-262">**Anweisungen**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-262">**Instructions**</span></span>
* <span data-ttu-id="fc6e8-263">Geben Sie im **Projekt** Panel im Suchfeld den Suchbegriff **colorpickerwheel**ein.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-263">In the **Project** panel, type in the search box **ColorPickerWheel**.</span></span> <span data-ttu-id="fc6e8-264">Sie finden es auch unter Assets/appprefabs/.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-264">You can also find it under Assets/AppPrefabs/.</span></span>
* <span data-ttu-id="fc6e8-265">Ziehen Sie **colorpickerwheel** Prefab in den Bereich **Hierarchie** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-265">Drag **ColorPickerWheel** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="fc6e8-266">Klicken Sie im **Hierarchie** Panel auf **colorpickerwheel** Prefab.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-266">Click the **ColorPickerWheel** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="fc6e8-267">Doppelklicken Sie im **Inspektor** -Panel auf **colorpickerwheel** -Skript, um den Code in Visual Studio anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-267">In the **Inspector** panel, double click **ColorPickerWheel** Script to see the code in Visual Studio.</span></span>

![Colorpickerwheel-präfab](images/mr213-colorpickerwheel-1000px.jpg)

<span data-ttu-id="fc6e8-269">**Colorpickerwheel-Skript**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-269">**ColorPickerWheel script**</span></span>

<span data-ttu-id="fc6e8-270">Da **colorpickerwheel** " **AttachTo Controller**" erbt, zeigt es die **häntigkeit** und das **Element** im **Inspektor** -Panel.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-270">Since **ColorPickerWheel** inherits **AttachToController**, it shows **Handedness** and **Element** in the **Inspector** panel.</span></span> <span data-ttu-id="fc6e8-271">Wir fügen die Benutzeroberfläche an das Touchpad-Element auf dem linken Controller an.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-271">We'll be attaching the UI to the Touchpad element on the left controller.</span></span>

![Colorpickerwheel-Skript](images/mr213-attachtocontroller-300px.jpg)

<span data-ttu-id="fc6e8-273">**Colorpickerwheel** überschreibt den **onattachto Controller** und **onde tatchfromcontroller** , um das Eingabe Ereignis zu abonnieren, das im nächsten Kapitel für die Farbauswahl mit der Touchpad-Eingabe verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-273">**ColorPickerWheel** overrides the **OnAttachToController** and **OnDetatchFromController** to subscribe to the input event which will be used in next chapter for color selection with touchpad input.</span></span>

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
* <span data-ttu-id="fc6e8-274">**Speichern** Sie die Szene, und klicken Sie auf die Schaltfläche **abspielen** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-274">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="fc6e8-275">**Alternative Methode zum Anfügen von Objekten an die Controller**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-275">**Alternative method for attaching objects to the controllers**</span></span>

<span data-ttu-id="fc6e8-276">Es wird empfohlen, dass Ihre Skripts von **attachoncontroller** erben und **onattachoncontroller**überschreiben.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-276">We recommend that your scripts inherit from **AttachToController** and override **OnAttachToController**.</span></span> <span data-ttu-id="fc6e8-277">Dies ist jedoch möglicherweise nicht immer möglich.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-277">However, this may not always be possible.</span></span> <span data-ttu-id="fc6e8-278">Eine Alternative ist die Verwendung als eigenständige Komponente.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-278">An alternative is using it as a standalone component.</span></span> <span data-ttu-id="fc6e8-279">Dies kann hilfreich sein, wenn Sie eine vorhandene vorfab an einen Controller anfügen möchten, ohne Ihre Skripts umgestalten zu müssen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-279">This can be useful when you want to attach an existing prefab to a controller without refactoring your scripts.</span></span> <span data-ttu-id="fc6e8-280">Legen Sie einfach fest, dass die Klasse auf "true" festgelegt ist, bevor Sie Setup ausführen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-280">Simply have your class wait for IsAttached to be set to true before performing any setup.</span></span> <span data-ttu-id="fc6e8-281">Die einfachste Möglichkeit hierfür ist die Verwendung einer Coroutine für "Start".</span><span class="sxs-lookup"><span data-stu-id="fc6e8-281">The simplest way to do this is by using a coroutine for 'Start.'</span></span>

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a><span data-ttu-id="fc6e8-282">Kapitel 3: Arbeiten mit Touchpad-Eingaben</span><span class="sxs-lookup"><span data-stu-id="fc6e8-282">Chapter 3 - Working with touchpad input</span></span>

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a><span data-ttu-id="fc6e8-283">Ziele</span><span class="sxs-lookup"><span data-stu-id="fc6e8-283">Objectives</span></span>

* <span data-ttu-id="fc6e8-284">Erfahren Sie, wie Sie Eingabedaten Ereignisse von Touchpad erhalten.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-284">Learn how to get touchpad input data events</span></span>
* <span data-ttu-id="fc6e8-285">Erfahren Sie, wie Sie die Positionsinformationen der Touchpad-Achse für Ihre APP verwenden.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-285">Learn how to use touchpad axis position information for your app experience</span></span>

### <a name="instructions"></a><span data-ttu-id="fc6e8-286">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="fc6e8-286">Instructions</span></span>

* <span data-ttu-id="fc6e8-287">Klicken Sie im **Hierarchie** Panel auf **colorpickerwheel** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-287">In the **Hierarchy** panel, click **ColorPickerWheel**</span></span>
* <span data-ttu-id="fc6e8-288">Doppelklicken Sie im **Inspektor** -Panel unter **animatior**auf **colorpickerwheelcontroller** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-288">In the **Inspector** panel, under **Animatior**, double click **ColorPickerWheelController**</span></span>
* <span data-ttu-id="fc6e8-289">Sie können die **animatorregister** Karte geöffnet sehen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-289">You will be able to see **Animator** tab opened</span></span>

<span data-ttu-id="fc6e8-290">**Anzeige/Ausblenden der Benutzeroberfläche mit dem Animations Controller von Unity**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-290">**Showing/hiding UI with Unity's Animation controller**</span></span>

<span data-ttu-id="fc6e8-291">Um die **colorpickerwheel** -Benutzeroberfläche mit Animation anzuzeigen und auszublenden, verwenden wir das [Animationssystem von Unity](https://docs.unity3d.com/Manual/AnimationOverview.html).</span><span class="sxs-lookup"><span data-stu-id="fc6e8-291">To show and hide the **ColorPickerWheel** UI with animation, we are using [Unity's animation system](https://docs.unity3d.com/Manual/AnimationOverview.html).</span></span> <span data-ttu-id="fc6e8-292">Wenn Sie die **Visible** -Eigenschaft von **colorpickerwheel**auf true oder false festlegen, werden Animations Trigger **angezeigt** und **ausgeblendet** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-292">Setting the **ColorPickerWheel**'s **Visible** property to true or false triggers **Show** and **Hide** animation triggers.</span></span> <span data-ttu-id="fc6e8-293">Ein **-und** **Ausblenden** von Parametern ist im **colorpickerwheelcontroller** -Animations Controller definiert.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-293">**Show** and **Hide** parameters are defined in the **ColorPickerWheelController** animation controller.</span></span>

![Unity-Animations Controller](images/mr123-animationcontroller-550px.jpg)

<span data-ttu-id="fc6e8-295">**Anweisungen**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-295">**Instructions**</span></span>
* <span data-ttu-id="fc6e8-296">Wählen Sie im Bereich **Hierarchie** die Option **colorpickerwheel** Prefab aus.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-296">In the **Hierarchy** panel, select **ColorPickerWheel** prefab</span></span>
* <span data-ttu-id="fc6e8-297">Doppelklicken Sie im **Inspektor** -Panel auf **colorpickerwheel** -Skript, um den Code in Visual Studio anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-297">In the **Inspector** panel, double click **ColorPickerWheel** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="fc6e8-298">**Colorpickerwheel-Skript**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-298">**ColorPickerWheel script**</span></span>

<span data-ttu-id="fc6e8-299">**Colorpickerwheel** abonniert das **interaktionsourceupdati-** Ereignis von Unity, um auf Touchpad-Ereignisse zu lauschen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-299">**ColorPickerWheel** subscribes to Unity's **InteractionSourceUpdated** event to listen for touchpad events.</span></span>

<span data-ttu-id="fc6e8-300">In **interaktionsourceupdatiert ()** prüft das Skript zunächst, ob Folgendes möglich ist:</span><span class="sxs-lookup"><span data-stu-id="fc6e8-300">In **InteractionSourceUpdated()**, the script first checks to ensure that it:</span></span>
* <span data-ttu-id="fc6e8-301">ist tatsächlich ein Touchpad-Ereignis (obj. State). **touchpadtouched**)</span><span class="sxs-lookup"><span data-stu-id="fc6e8-301">is actually a touchpad event (obj.state.**touchpadTouched**)</span></span>
* <span data-ttu-id="fc6e8-302">stammt vom linken Controller (obj. State. Source). **häntigkeit**)</span><span class="sxs-lookup"><span data-stu-id="fc6e8-302">originates from the left controller (obj.state.source.**handedness**)</span></span>

<span data-ttu-id="fc6e8-303">Wenn beide true sind, ist die Touchpad-Position (obj. State). **touchpadposition**) ist **Selector Position**zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-303">If both are true, the touchpad position (obj.state.**touchpadPosition**) is assigned to **selectorPosition**.</span></span>

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

<span data-ttu-id="fc6e8-304">In **Update ()** , basierend auf der **Visible** -Eigenschaft, werden Animations Trigger in der animatorkomponente der Farbauswahl angezeigt und ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-304">In **Update()**, based on **visible** property, it triggers Show and Hide animation triggers in the color picker's animator component</span></span>

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

<span data-ttu-id="fc6e8-305">In **Update ()** wird **Selector Position** verwendet, um einen Strahl in den Mesh-Collider des Farbrades umzuwandeln, der eine UV-Position zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-305">In **Update()**, **selectorPosition** is used to cast a ray at the color wheel's mesh collider, which returns a UV position.</span></span> <span data-ttu-id="fc6e8-306">Diese Position kann dann verwendet werden, um die Pixel Koordinate und den Farbwert der Textur des Farbrades zu suchen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-306">This position can then be used to find the pixel coordinate and color value of the color wheel's texture.</span></span> <span data-ttu-id="fc6e8-307">Auf diesen Wert kann von anderen Skripts über die **selectedColor** -Eigenschaft zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-307">This value is accessible to other scripts via the **SelectedColor** property.</span></span>

![Rad-Raycasting für Farbauswahl](images/mr213-colorpickerwheel-raycast-700px.png)

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

## <a name="chapter-4---overriding-controller-model"></a><span data-ttu-id="fc6e8-309">Kapitel 4: Überschreiben des Controller Modells</span><span class="sxs-lookup"><span data-stu-id="fc6e8-309">Chapter 4 - Overriding controller model</span></span>

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a><span data-ttu-id="fc6e8-310">Ziele</span><span class="sxs-lookup"><span data-stu-id="fc6e8-310">Objectives</span></span>

* <span data-ttu-id="fc6e8-311">Erfahren Sie, wie Sie das Controller Modell mit einem benutzerdefinierten 3D-Modell überschreiben.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-311">Learn how to override the controller model with a custom 3D model.</span></span>

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a><span data-ttu-id="fc6e8-313">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="fc6e8-313">Instructions</span></span>

* <span data-ttu-id="fc6e8-314">Klicken **Sie** im **Hierarchie** Panel auf "".</span><span class="sxs-lookup"><span data-stu-id="fc6e8-314">Click **MotionControllers** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="fc6e8-315">Klicken Sie rechts neben dem Feld **alternativer rechter Controller** auf den Kreis.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-315">Click the circle on the right side of the **Alternate Right Controller** field.</span></span>
* <span data-ttu-id="fc6e8-316">Geben Sie **"brushcontroller**" ein, und wählen Sie das präfab aus dem Ergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-316">Type in **'BrushController**' and select the prefab from the result.</span></span> <span data-ttu-id="fc6e8-317">Sie finden ihn unter Assets/appprefabs/**brushcontroller**.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-317">You can find it under Assets/AppPrefabs/**BrushController**.</span></span>
* <span data-ttu-id="fc6e8-318">Aktivieren Sie **immer alternatives Rechtes Modell verwenden** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-318">Check **Always Use Alternate Right Model**</span></span>

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

<span data-ttu-id="fc6e8-320">Die **brushcontroller** -vorfab muss nicht im **Hierarchie** Panel enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-320">The **BrushController** prefab does not have to be included in the **Hierarchy** panel.</span></span> <span data-ttu-id="fc6e8-321">Zum Auschecken der untergeordneten Komponenten:</span><span class="sxs-lookup"><span data-stu-id="fc6e8-321">However, to check out its child components:</span></span>
* <span data-ttu-id="fc6e8-322">Geben Sie im **Projekt** Panel " **brushcontroller** " ein, und ziehen Sie " **brushcontroller** Prefab" in das **Hierarchie** Panel.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-322">In the **Project** panel, type in **BrushController** and drag **BrushController** prefab into the **Hierarchy** panel.</span></span>

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

<span data-ttu-id="fc6e8-324">Sie finden die **Tip** -Komponente in **brushcontroller**.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-324">You will find the **Tip** component in **BrushController**.</span></span> <span data-ttu-id="fc6e8-325">Wir verwenden die Transformation zum Starten/Abbrechen von Zeichnungslinien.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-325">We will use its transform to start/stop drawing lines.</span></span>
* <span data-ttu-id="fc6e8-326">Löschen Sie den **brushcontroller** aus dem Bereich **Hierarchie** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-326">Delete the **BrushController** from the **Hierarchy** panel.</span></span>
* <span data-ttu-id="fc6e8-327">**Speichern** Sie die Szene, und klicken Sie auf die Schaltfläche **abspielen** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-327">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="fc6e8-328">Sie können sehen, dass das Pinsel Modell den rechten Bewegungs Controller ersetzt hat.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-328">You will be able to see the brush model replaced the right-hand motion controller.</span></span>

## <a name="chapter-5---painting-with-select-input"></a><span data-ttu-id="fc6e8-329">Kapitel 5: Zeichnen mit SELECT-Eingabe</span><span class="sxs-lookup"><span data-stu-id="fc6e8-329">Chapter 5 - Painting with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a><span data-ttu-id="fc6e8-330">Ziele</span><span class="sxs-lookup"><span data-stu-id="fc6e8-330">Objectives</span></span>

* <span data-ttu-id="fc6e8-331">Erfahren Sie, wie Sie das Ereignis "Select Button" verwenden, um eine Zeilen Zeichnung zu starten und anzuhalten.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-331">Learn how to use the Select button event to start and stop a line drawing</span></span>

### <a name="instructions"></a><span data-ttu-id="fc6e8-332">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="fc6e8-332">Instructions</span></span>

* <span data-ttu-id="fc6e8-333">Suchen Sie im **Projekt** Panel den Abschnitt " **brushcontroller** Prefab".</span><span class="sxs-lookup"><span data-stu-id="fc6e8-333">Search **BrushController** prefab in the **Project** panel.</span></span>
* <span data-ttu-id="fc6e8-334">Doppelklicken Sie im **Inspektor** -Panel auf das **Pinsel Controller** Skript, um den Code in Visual Studio anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-334">In the **Inspector** panel, double click **BrushController** Script to see the code in Visual Studio</span></span>

<span data-ttu-id="fc6e8-335">**Brushcontroller-Skript**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-335">**BrushController script**</span></span>

<span data-ttu-id="fc6e8-336">Der **brushcontroller** abonniert die interaktionsourcepressed -und **interaktionsourcereleasing** -Ereignisse des interaktionmanagers.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-336">**BrushController** subscribes to the InteractionManager's **InteractionSourcePressed** and **InteractionSourceReleased** events.</span></span> <span data-ttu-id="fc6e8-337">Wenn das **interaktionsourcepressed** -Ereignis ausgelöst wird, wird die **Draw** -Eigenschaft des Pinsels auf true festgelegt. Wenn das **interaktionsourcereleasing** -Ereignis ausgelöst wird, wird die **Draw** -Eigenschaft des Pinsels auf false festgelegt.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-337">When **InteractionSourcePressed** event is triggered, the brush's **Draw** property is set to true; when **InteractionSourceReleased** event is triggered, the brush's **Draw** property is set to false.</span></span>

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

<span data-ttu-id="fc6e8-338">Obwohl **Draw** auf true festgelegt ist, generiert der Pinsel Punkte in einem instanziierten Unity- **linerenderer**.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-338">While **Draw** is set to true, the brush will generate points in an instantiated Unity **LineRenderer**.</span></span> <span data-ttu-id="fc6e8-339">Ein Verweis auf diese vorfab wird im Feld **Strich-vorfab** des Pinsels beibehalten.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-339">A reference to this prefab is kept in the brush's **Stroke Prefab** field.</span></span>

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

<span data-ttu-id="fc6e8-340">Um die aktuell ausgewählte Farbe von der Oberfläche für die Farbauswahl des Rades zu verwenden, muss für den **brushcontroller** ein Verweis auf das **colorpickerwheel** -Objekt vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-340">To use the currently selected color from the color picker wheel UI, **BrushController** needs to have a reference to the **ColorPickerWheel** object.</span></span> <span data-ttu-id="fc6e8-341">Da das **brushcontroller** -präfab zur Laufzeit als Ersatz Controller instanziiert wird, müssen alle Verweise auf Objekte in der Szene zur Laufzeit festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-341">Because the **BrushController** prefab is instantiated at runtime as a replacement controller, any references to objects in the scene will have to be set at runtime.</span></span> <span data-ttu-id="fc6e8-342">In diesem Fall verwenden wir " **gameobject. findobjectoftype** ", um das **colorpickerwheel**zu finden:</span><span class="sxs-lookup"><span data-stu-id="fc6e8-342">In this case we use **GameObject.FindObjectOfType** to locate the **ColorPickerWheel**:</span></span>

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
* <span data-ttu-id="fc6e8-343">**Speichern** Sie die Szene, und klicken Sie auf die Schaltfläche **abspielen** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-343">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="fc6e8-344">Mithilfe der Schaltfläche auswählen des rechten Controllers können Sie Zeilen und zeichnen zeichnen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-344">You will be able to draw the lines and paint using the select button on the right-hand controller.</span></span>

## <a name="chapter-6---object-spawning-with-select-input"></a><span data-ttu-id="fc6e8-345">Kapitel 6: das Erzeugen von Objekten mit SELECT-Eingabe</span><span class="sxs-lookup"><span data-stu-id="fc6e8-345">Chapter 6 - Object spawning with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a><span data-ttu-id="fc6e8-346">Ziele</span><span class="sxs-lookup"><span data-stu-id="fc6e8-346">Objectives</span></span>

* <span data-ttu-id="fc6e8-347">Informationen zum Verwenden von Eingabe Ereignissen für die Schaltfläche "auswählen" und "</span><span class="sxs-lookup"><span data-stu-id="fc6e8-347">Learn how to use Select and Grasp button input events</span></span>
* <span data-ttu-id="fc6e8-348">Weitere Informationen zum Instanziieren von Objekten</span><span class="sxs-lookup"><span data-stu-id="fc6e8-348">Learn how to instantiate objects</span></span>

### <a name="instructions"></a><span data-ttu-id="fc6e8-349">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="fc6e8-349">Instructions</span></span>

* <span data-ttu-id="fc6e8-350">Geben Sie im **Projekt** Panel im Suchfeld **objectspawner** ein.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-350">In the **Project** panel, type **ObjectSpawner** in the search box.</span></span> <span data-ttu-id="fc6e8-351">Sie finden es auch unter Assets/appprefabs/</span><span class="sxs-lookup"><span data-stu-id="fc6e8-351">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="fc6e8-352">Ziehen Sie die vorfab **objectspawner** in den Bereich **Hierarchie** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-352">Drag the **ObjectSpawner** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="fc6e8-353">Klicken Sie im **Hierarchie** Panel auf **objectspawner** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-353">Click **ObjectSpawner** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="fc6e8-354">**Objectspawner** verfügt über ein Feld mit dem Namen **Color Source**.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-354">**ObjectSpawner** has a field named **Color Source**.</span></span>
* <span data-ttu-id="fc6e8-355">Ziehen Sie im **Hierarchie** Panel den **colorpickerwheel** -Verweis in dieses Feld.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-355">From the **Hierarchy** panel, drag the **ColorPickerWheel** reference into this field.</span></span>

![Object Spawner Inspector](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* <span data-ttu-id="fc6e8-357">Klicken Sie im **Hierarchie** Panel auf die vorfab **objectspawner** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-357">Click the **ObjectSpawner** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="fc6e8-358">Doppelklicken Sie im **Inspektor** -Panel auf **objectspawner** Script, um den Code in Visual Studio anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-358">In the **Inspector** panel, double click **ObjectSpawner** Script to see the code in Visual Studio.</span></span>

<span data-ttu-id="fc6e8-359">**Objectspawner-Skript**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-359">**ObjectSpawner script**</span></span>

<span data-ttu-id="fc6e8-360">Der **objectspawner** instanziiert Kopien eines primitiven Netzes (Cube, Kugel, Zylinder) in den Raum.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-360">The **ObjectSpawner** instantiates copies of a primitive mesh (cube, sphere, cylinder) into the space.</span></span> <span data-ttu-id="fc6e8-361">Wenn eine **interaktionsourcepressed** erkannt wird, überprüft Sie die häntigkeit und, wenn es sich um ein **interaktionsourcepresstype. Grasp** -oder **interaktionsourcepresstype. Select** -Ereignis handelt.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-361">When a **InteractionSourcePressed** is detected it checks the handedness and if it's an **InteractionSourcePressType.Grasp** or **InteractionSourcePressType.Select** event.</span></span>

<span data-ttu-id="fc6e8-362">Bei einem **grasp** -Ereignis erhöht es den Index des aktuellen Mesh-Typs (Kugel, Cube, Zylinder).</span><span class="sxs-lookup"><span data-stu-id="fc6e8-362">For a **Grasp** event, it increments the index of current mesh type (sphere, cube, cylinder)</span></span>

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

<span data-ttu-id="fc6e8-363">Bei einem **Select** -Ereignis in **spawnobject ()** wird ein neues-Objekt instanziiert, nicht übergeordnet und in der Welt veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-363">For a **Select** event, in **SpawnObject()**, a new object is instantiated, un-parented and released into the world.</span></span>

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

<span data-ttu-id="fc6e8-364">Der **objectspawner** verwendet das **colorpickerwheel** , um die Farbe des Materials des Anzeige Objekts festzulegen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-364">The **ObjectSpawner** uses the **ColorPickerWheel** to set the color of the display object's material.</span></span> <span data-ttu-id="fc6e8-365">Erzeugten Objekten wird eine Instanz dieses Materials zugewiesen, damit Sie Ihre Farbe beibehalten.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-365">Spawned objects are given an instance of this material so they will retain their color.</span></span>
* <span data-ttu-id="fc6e8-366">**Speichern** Sie die Szene, und klicken Sie auf die Schaltfläche **abspielen** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-366">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="fc6e8-367">Mit der Schaltfläche "auswählen" können Sie die Objekte mit der Schaltfläche "übersetzen" und "Objekte" mithilfe der Schaltfläche "</span><span class="sxs-lookup"><span data-stu-id="fc6e8-367">You will be able to change the objects with the Grasp button and spawn objects with the Select button.</span></span>

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a><span data-ttu-id="fc6e8-368">Erstellen und Bereitstellen der APP im Mixed Reality-Portal</span><span class="sxs-lookup"><span data-stu-id="fc6e8-368">Build and deploy app to Mixed Reality Portal</span></span>
* <span data-ttu-id="fc6e8-369">Wählen Sie in Unity **Datei >** Buildeinstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-369">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="fc6e8-370">Klicken Sie auf **offene Szenen hinzufügen** , um die aktuelle Szene zu den **Kulissen in Build**hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-370">Click **Add Open Scenes** to add current scene to the **Scenes In Build**.</span></span>
* <span data-ttu-id="fc6e8-371">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-371">Click **Build**.</span></span>
* <span data-ttu-id="fc6e8-372">Erstellen Sie einen **neuen Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="fc6e8-372">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="fc6e8-373">Klicken Sie einfach auf den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-373">Single click the **App** folder.</span></span>
* <span data-ttu-id="fc6e8-374">Klicken Sie auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-374">Click **Select Folder**.</span></span>
* <span data-ttu-id="fc6e8-375">Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-375">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="fc6e8-376">Öffnen Sie den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-376">Open the **App** folder.</span></span>
* <span data-ttu-id="fc6e8-377">Doppelklicken Sie auf **yourscenename. sln** Visual Studio-Projektmappendatei.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-377">Double click **YourSceneName.sln** Visual Studio Solution file.</span></span>
* <span data-ttu-id="fc6e8-378">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x64**.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-378">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X64**.</span></span>
* <span data-ttu-id="fc6e8-379">Klicken Sie auf den Dropdown Pfeil neben der Schaltfläche Gerät, und wählen Sie **lokaler Computer**aus.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-379">Click on the drop-down arrow next to the Device button, and select **Local Machine**.</span></span>
* <span data-ttu-id="fc6e8-380">Klicken Sie im Menü auf **Debuggen > Starten ohne Debuggen** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-380">Click **Debug -> Start Without debugging** in the menu or press **Ctrl + F5**.</span></span>

<span data-ttu-id="fc6e8-381">Nun wird die APP im Mixed Reality-Portal erstellt und installiert.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-381">Now the app is built and installed in Mixed Reality Portal.</span></span> <span data-ttu-id="fc6e8-382">Sie können Sie erneut über das Startmenü im Mixed Reality-Portal starten.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-382">You can launch it again through Start menu in Mixed Reality Portal.</span></span>

## <a name="advanced-design---brush-tools-with-radial-layout"></a><span data-ttu-id="fc6e8-383">Erweiterte Entwurfs Pinsel Tools mit radialem Layout</span><span class="sxs-lookup"><span data-stu-id="fc6e8-383">Advanced design - Brush tools with radial layout</span></span>

![MixedReality213 Main](images/mr213-main-600px.jpg)

<span data-ttu-id="fc6e8-385">In diesem Kapitel erfahren Sie, wie Sie das standardmäßige Motion Controller-Modell durch eine benutzerdefinierte Pinsel Tool Auflistung ersetzen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-385">In this chapter, you will learn how to replace the default motion controller model with a custom brush tool collection.</span></span> <span data-ttu-id="fc6e8-386">Eine Referenz finden Sie im Ordner "abgeschlossene Szene **MixedReality213Advanced** " unter **Szenen** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-386">For your reference, you can find the completed scene **MixedReality213Advanced** under **Scenes** folder.</span></span>

### <a name="instructions"></a><span data-ttu-id="fc6e8-387">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="fc6e8-387">Instructions</span></span>

* <span data-ttu-id="fc6e8-388">Geben Sie im **Projekt** Panel im Suchfeld den Text **brushselector** ein.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-388">In the **Project** panel, type **BrushSelector** in the search box .</span></span> <span data-ttu-id="fc6e8-389">Sie finden es auch unter Assets/appprefabs/</span><span class="sxs-lookup"><span data-stu-id="fc6e8-389">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="fc6e8-390">Ziehen Sie die vorfab von **brushselector** in den Bereich **Hierarchie** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-390">Drag the **BrushSelector** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="fc6e8-391">Erstellen Sie für die Organisation ein leeres gameobject namens **Pinsel** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-391">For organization, create an empty GameObject called **Brushes**</span></span>
* <span data-ttu-id="fc6e8-392">Ziehen Sie die folgenden Prefabs aus dem **Projekt** Panel in **Pinsel** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-392">Drag following prefabs from the **Project** panel into **Brushes**</span></span>
    * <span data-ttu-id="fc6e8-393">Assets/appprefabs/**brushfat**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-393">Assets/AppPrefabs/**BrushFat**</span></span>
    * <span data-ttu-id="fc6e8-394">Assets/appprefabs/**brushthin**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-394">Assets/AppPrefabs/**BrushThin**</span></span>
    * <span data-ttu-id="fc6e8-395">Assets/appprefabs/**Radierer**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-395">Assets/AppPrefabs/**Eraser**</span></span>
    * <span data-ttu-id="fc6e8-396">Assets/appprefabs/**markerfat**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-396">Assets/AppPrefabs/**MarkerFat**</span></span>
    * <span data-ttu-id="fc6e8-397">Assets/appprefabs/**markerthin**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-397">Assets/AppPrefabs/**MarkerThin**</span></span>
    * <span data-ttu-id="fc6e8-398">Assets/appprefabs/**Stift**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-398">Assets/AppPrefabs/**Pencil**</span></span>

![Pinsel](images/mixedreality213-brushes-250px.png)
* <span data-ttu-id="fc6e8-400">Klicken **Sie** im **Hierarchie** Panel auf die vorfab-vorfab.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-400">Click **MotionControllers** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="fc6e8-401">Deaktivieren Sie im **Inspektor** -Panel die Option **alternatives Rechtes Modell immer verwenden** auf der **Motion Controller** -Schnellansicht.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-401">In the **Inspector** panel, uncheck **Always Use Alternate Right Model** on the **Motion Controller Visualizer**</span></span>
* <span data-ttu-id="fc6e8-402">Klicken Sie im Bereich **Hierarchie** auf **brushselector** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-402">In the **Hierarchy** panel, click **BrushSelector**</span></span>
* <span data-ttu-id="fc6e8-403">Der **brushselector** hat ein Feld mit dem Namen **ColorPicker** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-403">**BrushSelector** has a field named **ColorPicker**</span></span>
* <span data-ttu-id="fc6e8-404">Ziehen Sie im Bereich **Hierarchie** das **colorpickerwheel** in das Feld **ColorPicker** im **Inspektor** -Panel.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-404">From the **Hierarchy** panel, drag the **ColorPickerWheel** into **ColorPicker** field in the **Inspector** panel.</span></span>

![Colorpickerwheel zum pinselselektor zuweisen](images/mr213-brushselector-500px.jpg)
* <span data-ttu-id="fc6e8-406">Wählen Sie im Bereich **Hierarchie** unter **brushselector** Prefab das **Menü** Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-406">In the **Hierarchy** panel, under **BrushSelector** prefab, select the **Menu** object.</span></span>
* <span data-ttu-id="fc6e8-407">Öffnen Sie im **Inspektor** -Panel unter der **lineobjectcollection** -Komponente die Dropdown Liste **Objekt** Array.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-407">In the **Inspector** panel, under the **LineObjectCollection** component, open the **Objects** array dropdown.</span></span> <span data-ttu-id="fc6e8-408">Sechs leere Slots werden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-408">You will see 6 empty slots.</span></span>
* <span data-ttu-id="fc6e8-409">Ziehen Sie im Bereich **Hierarchie** die einzelnen Prefabs unter dem gameobject- **Pinsel** in beliebiger Reihenfolge in diese Slots.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-409">From the **Hierarchy** panel, drag each of the prefabs parented under the **Brushes** GameObject into these slots in any order.</span></span> <span data-ttu-id="fc6e8-410">(Stellen Sie sicher, dass Sie die Prefabs aus der Szene ziehen, nicht die präfabs im Projektordner.)</span><span class="sxs-lookup"><span data-stu-id="fc6e8-410">(Make sure you're dragging the prefabs from the scene, not the prefabs in the project folder.)</span></span>

![Pinsel Auswahl](images/mr213-brushselectorbrushes-700px.jpg)

<span data-ttu-id="fc6e8-412">**Brushselector-vorfab**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-412">**BrushSelector prefab**</span></span>

<span data-ttu-id="fc6e8-413">Da der **brushselector** **attachdecontroller**erbt, werden die Optionen für die **häntigkeit** und das **Element** im **Inspektor** -Panel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-413">Since the **BrushSelector** inherits **AttachToController**, it shows **Handedness** and **Element** options in the **Inspector** panel.</span></span> <span data-ttu-id="fc6e8-414">Wir haben **right** ausgewählt und **zeigen eine Pose** an, um Pinsel Tools an den rechten Controller mit Vorwärtsrichtung anzufügen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-414">We selected **Right** and **Pointing Pose** to attach brush tools to the right hand controller with forward direction.</span></span>

<span data-ttu-id="fc6e8-415">Der **brushselector** nutzt zwei Hilfsprogramme:</span><span class="sxs-lookup"><span data-stu-id="fc6e8-415">The **BrushSelector** makes use of two utilities:</span></span>
* <span data-ttu-id="fc6e8-416">**Ellipse**: wird verwendet, um Punkte im Raum entlang einer Ellipse-Form zu generieren.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-416">**Ellipse**: used to generate points in space along an ellipse shape.</span></span>
* <span data-ttu-id="fc6e8-417">**Lineobjectcollection**: verteilt Objekte mithilfe der von einer beliebigen Zeilen Klasse generierten Punkte (z. b. Ellipse).</span><span class="sxs-lookup"><span data-stu-id="fc6e8-417">**LineObjectCollection**: distributes objects using the points generated by any Line class (eg, Ellipse).</span></span> <span data-ttu-id="fc6e8-418">Das ist das, was wir verwenden werden, um die Pinsel entlang der Ellipse-Form zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-418">This is what we'll be using to place our brushes along the Ellipse shape.</span></span>

<span data-ttu-id="fc6e8-419">In Kombination können diese Hilfsprogramme verwendet werden, um ein radiales Menü zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-419">When combined, these utilities can be used to create a radial menu.</span></span>

<span data-ttu-id="fc6e8-420">**Lineobjectcollection-Skript**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-420">**LineObjectCollection script**</span></span>

<span data-ttu-id="fc6e8-421">**Lineobjectcollection** verfügt über Steuerelemente für Größe, Position und Drehung von Objekten, die entlang der Zeile verteilt werden.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-421">**LineObjectCollection** has controls for the size, position and rotation of objects distributed along its line.</span></span> <span data-ttu-id="fc6e8-422">Dies ist nützlich, um radiale Menüs wie die Pinsel Auswahl zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-422">This is useful for creating radial menus like the brush selector.</span></span> <span data-ttu-id="fc6e8-423">Um die Darstellung von Pinseln zu erstellen, die von nichts zentral hochskaliert werden, wenn Sie sich auf die ausgewählte Position im Zentrum angleichen, wird die **objectscale** -Kurve in der Mitte zentriert und an den Rändern ausgeschaltet.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-423">To create the appearance of brushes that scale up from nothing as they approach the center selected position, the **ObjectScale** curve peaks in the center and tapers off at the edges.</span></span>

<span data-ttu-id="fc6e8-424">**Pinsel Auswahl Skript**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-424">**BrushSelector script**</span></span>

<span data-ttu-id="fc6e8-425">Im Fall von " **brushselector**" haben wir die Verwendung der Verfahrens bezogenen Animation gewählt.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-425">In the case of the **BrushSelector**, we've chosen to use procedural animation.</span></span> <span data-ttu-id="fc6e8-426">Zuerst werden Pinsel Modelle durch das **lineobjectcollection** -Skript in einer Ellipse verteilt.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-426">First, brush models are distributed in an ellipse by the **LineObjectCollection** script.</span></span> <span data-ttu-id="fc6e8-427">Dann ist jeder Pinsel dafür verantwortlich, seine Position in der Hand des Benutzers basierend auf seinem **DisplayMode** -Wert beizubehalten, der sich auf der Grundlage der Auswahl ändert.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-427">Then, each brush is responsible for maintaining its position in the user's hand based on its **DisplayMode** value, which changes based on the selection.</span></span> <span data-ttu-id="fc6e8-428">Wir haben uns für einen Verfahrensansatz entschieden, da die hohe Wahrscheinlichkeit, dass der Pinsel positioniert wird, unterbrochen wird, wenn der Benutzer Pinsel auswählt.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-428">We chose a procedural approach because of the high probability of brush position transitions being interrupted as the user selects brushes.</span></span> <span data-ttu-id="fc6e8-429">Mecanim-Animationen können Unterbrechungen ordnungsgemäß behandeln, Sie sind jedoch tendenziell komplizierter als ein einfacher Lerp-Vorgang.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-429">Mecanim animations can handle interruptions gracefully, but it tends to be more complicated than a simple Lerp operation.</span></span>

<span data-ttu-id="fc6e8-430">" **Brushselector** " verwendet eine Kombination aus beidem.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-430">**BrushSelector** uses a combination of both.</span></span> <span data-ttu-id="fc6e8-431">Wenn Touchpad-Eingaben erkannt werden, werden Pinseloptionen sichtbar und im radialen Menü zentral hochskaliert.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-431">When touchpad input is detected, brush options become visible and scale up along the radial menu.</span></span> <span data-ttu-id="fc6e8-432">Nach einem Timeout Zeitraum (der angibt, dass der Benutzer eine Auswahl getroffen hat) können die Pinseloptionen wieder herunterskaliert werden, sodass nur der ausgewählte Pinsel erhalten bleibt.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-432">After a timeout period (which indicates that the user has made a selection) the brush options scale down again, leaving only the selected brush.</span></span>

<span data-ttu-id="fc6e8-433">**Visualisieren der Touchpad-Eingabe**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-433">**Visualizing touchpad input**</span></span>

<span data-ttu-id="fc6e8-434">Auch in Fällen, in denen das Controller Modell vollständig ersetzt wurde, kann es hilfreich sein, Eingaben für die ursprünglichen Modell Eingaben anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-434">Even in cases where the controller model has been completely replaced, it can be helpful to show input on the original model inputs.</span></span> <span data-ttu-id="fc6e8-435">Dies trägt dazu bei, die Aktionen des Benutzers in der Praxis zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-435">This helps to ground the user's actions in reality.</span></span> <span data-ttu-id="fc6e8-436">Für den **brushselector** haben wir ausgewählt, dass der Touchpad beim Empfang der Eingabe kurz sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-436">For the **BrushSelector** we've chosen to make the touchpad briefly visible when the input is received.</span></span> <span data-ttu-id="fc6e8-437">Dies wurde erreicht, indem das Touchpad-Element vom Controller abgerufen wurde, dessen Material durch ein benutzerdefiniertes Material ersetzt wurde. Anschließend wird ein Farbverlauf auf die Farbe dieses Materials angewendet, basierend auf dem Zeitpunkt, an dem die Touchpad-Eingabe zuletzt empfangen wurde.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-437">This was done by retrieving the Touchpad element from the controller, replacing its material with a custom material, then applying a gradient to that material's color based on the last time touchpad input was received.</span></span>

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

<span data-ttu-id="fc6e8-438">**Auswahl des Pinsel Tools mit Touchpad-Eingabe**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-438">**Brush tool selection with touchpad input**</span></span>

<span data-ttu-id="fc6e8-439">Wenn die Pinsel Auswahl die gedrückte Eingabe von Touchpad erkennt, wird die Position der Eingabe überprüft, um festzustellen, ob Sie sich links oder rechts befand.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-439">When the brush selector detects touchpad's pressed input, it checks the position of the input to determine if it was to the left or right.</span></span>

<span data-ttu-id="fc6e8-440">**Strichstärke mit selectpressedamount**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-440">**Stroke thickness with selectPressedAmount**</span></span>

<span data-ttu-id="fc6e8-441">Anstelle des **interaktionsourcepresstype. Select** -Ereignisses in **interaktionsourcepressed ()** können Sie den analogen Wert der gedrückten Menge über **selectpressedamount**erhalten.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-441">Instead of the **InteractionSourcePressType.Select** event in the **InteractionSourcePressed()**, you can get the analog value of the pressed amount through **selectPressedAmount**.</span></span> <span data-ttu-id="fc6e8-442">Dieser Wert kann in **interaktionsourceupveraltet ()** abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-442">This value can be retrieved in **InteractionSourceUpdated()**.</span></span>

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

<span data-ttu-id="fc6e8-443">**Erradierskript**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-443">**Eraser script**</span></span>

<span data-ttu-id="fc6e8-444">Der Radierer ist ein spezieller Pinseltyp, der die **drawovertime ()** -Funktion des Basis **Pinsels**überschreibt.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-444">**Eraser** is a special type of brush that overrides the base **Brush**'s **DrawOverTime()** function.</span></span> <span data-ttu-id="fc6e8-445">Obwohl Draw den Wert true hat, prüft der Radierer, ob seine Spitze sich mit vorhandenen Pinselstrichen überschneidet.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-445">While Draw is true, the eraser checks to see if its tip intersects with any existing brush strokes.</span></span> <span data-ttu-id="fc6e8-446">Wenn dies der Fall ist, werden Sie zu einer Warteschlange hinzugefügt, die verkleinert und gelöscht werden soll.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-446">If it does, they are added to a queue to be shrunk down and deleted.</span></span>

## <a name="advanced-design---teleportation-and-locomotion"></a><span data-ttu-id="fc6e8-447">Erweiterte Design-teleportierung und-Bewegung</span><span class="sxs-lookup"><span data-stu-id="fc6e8-447">Advanced design - Teleportation and locomotion</span></span>

<span data-ttu-id="fc6e8-448">Wenn Sie zulassen möchten, dass der Benutzer die Szene mit der teleportierung über den Finger Stick bewegt, verwenden Sie **mixedrealitycameraparent** anstelle von **mixedrealitycamera**.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-448">If you want to allow the user to move around the scene with teleportation using thumbstick, use **MixedRealityCameraParent** instead of **MixedRealityCamera**.</span></span> <span data-ttu-id="fc6e8-449">Außerdem müssen Sie **InputManager** und **defaultcusor**hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-449">You also need to add **InputManager** and **DefaultCusor**.</span></span> <span data-ttu-id="fc6e8-450">Da **mixedrealitycameraparent** bereits " **mutioncontrollers** " und " **Border** " als untergeordnete Komponenten enthält, sollten Sie vorhandene " **mueconcontrollers** " und " **Umgebungs** vorfab" entfernen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-450">Since **MixedRealityCameraParent** already includes **MotionControllers** and **Boundary** as child components, you should remove existing **MotionControllers** and **Environment** prefab.</span></span>

### <a name="instructions"></a><span data-ttu-id="fc6e8-451">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="fc6e8-451">Instructions</span></span>

* <span data-ttu-id="fc6e8-452">Löschen Sie im **Hierarchie** Panel **mixedrealitycamera**, **Environment** und **mutioncontrollers** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-452">In the **Hierarchy** panel, delete **MixedRealityCamera**, **Environment** and **MotionControllers**</span></span>
* <span data-ttu-id="fc6e8-453">Suchen Sie im **Projekt Panel**die folgenden Prefabs, und ziehen Sie Sie in das **Hierarchie** Panel:</span><span class="sxs-lookup"><span data-stu-id="fc6e8-453">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="fc6e8-454">Assets/appprefabs/Input/Prefabs/**mixedrealitycameraparent**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span></span>
    * <span data-ttu-id="fc6e8-455">Assets/appprefabs/Input/Prefabs/**InputManager**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-455">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span></span>
    * <span data-ttu-id="fc6e8-456">Assets/appprefabs/Input/Prefabs/Cursor/**DefaultCursor**</span><span class="sxs-lookup"><span data-stu-id="fc6e8-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span></span>

![Übergeordnetes Mixed Reality-Kamera](images/mr213-cameraparent-300px.png)
* <span data-ttu-id="fc6e8-458">Klicken Sie im **Hierarchie** Panel auf **Eingabe-Manager** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-458">In the **Hierarchy** panel, click **Input Manager**</span></span>
* <span data-ttu-id="fc6e8-459">Scrollen Sie im **Inspektor** -Panel nach unten zum Abschnitt **einfache Auswahl des einzelnen Zeigers** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-459">In the **Inspector** panel, scroll down to the **Simple Single Pointer Selector** section</span></span>
* <span data-ttu-id="fc6e8-460">Ziehen Sie im Bereich **Hierarchie** **DefaultCursor** in das Feld **Cursor** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-460">From the **Hierarchy** panel, drag **DefaultCursor** into **Cursor** field</span></span>

![Zuweisen von DefaultCursor](images/mr213-defaultcursor-500px.png)
* <span data-ttu-id="fc6e8-462">**Speichern** Sie die Szene, und klicken Sie auf die Schaltfläche **abspielen** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-462">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="fc6e8-463">Sie können den Finger Stick verwenden, um nach links/rechts oder Teleport zu drehen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-463">You will be able to use the thumbstick to rotate left/right or teleport.</span></span>

## <a name="the-end"></a><span data-ttu-id="fc6e8-464">Das Ende</span><span class="sxs-lookup"><span data-stu-id="fc6e8-464">The end</span></span>

<span data-ttu-id="fc6e8-465">Und das ist das Ende dieses Tutorials!</span><span class="sxs-lookup"><span data-stu-id="fc6e8-465">And that's the end of this tutorial!</span></span> <span data-ttu-id="fc6e8-466">Sie haben Folgendes gelernt:</span><span class="sxs-lookup"><span data-stu-id="fc6e8-466">You learned:</span></span>
* <span data-ttu-id="fc6e8-467">Arbeiten mit Motion Controller-Modellen im Spielmodus und der Laufzeit von Unity.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-467">How to work with motion controller models in Unity's game mode and runtime.</span></span>
* <span data-ttu-id="fc6e8-468">Verwenden verschiedener Arten von Schaltflächen Ereignissen und ihrer Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-468">How to use different types of button events and their applications.</span></span>
* <span data-ttu-id="fc6e8-469">Überlagern von UI-Elementen oberhalb des Controllers oder vollständiges anpassen.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-469">How to overlay UI elements on top of the controller or fully customize it.</span></span>

<span data-ttu-id="fc6e8-470">Nun können Sie mit der Erstellung Ihrer eigenen immersiven Benutzer Arbeit mit Motion Controller beginnen!</span><span class="sxs-lookup"><span data-stu-id="fc6e8-470">You are now ready to start creating your own immersive experience with motion controllers!</span></span>

## <a name="completed-scenes"></a><span data-ttu-id="fc6e8-471">Abgeschlossene Szenen</span><span class="sxs-lookup"><span data-stu-id="fc6e8-471">Completed scenes</span></span>

* <span data-ttu-id="fc6e8-472">Klicken Sie im Unity- **Projekt** Panel auf den Ordner **Szenen** .</span><span class="sxs-lookup"><span data-stu-id="fc6e8-472">In Unity's **Project** panel click on the **Scenes** folder.</span></span>
* <span data-ttu-id="fc6e8-473">Sie finden zwei Unity-Sceens- **MixedReality213** und **MixedReality213Advanced**.</span><span class="sxs-lookup"><span data-stu-id="fc6e8-473">You will find two Unity sceens **MixedReality213** and **MixedReality213Advanced**.</span></span>
    * <span data-ttu-id="fc6e8-474">**MixedReality213**: Abgeschlossene Szene mit einem Pinsel</span><span class="sxs-lookup"><span data-stu-id="fc6e8-474">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="fc6e8-475">**MixedReality213Advanced**: Abgeschlossene Szene mit mehreren Pinseln mit dem Press Amount-Beispiel der Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="fc6e8-475">**MixedReality213Advanced**: Completed scene with multiple brush with select button's press amount example</span></span>

## <a name="see-also"></a><span data-ttu-id="fc6e8-476">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="fc6e8-476">See also</span></span>

* [<span data-ttu-id="fc6e8-477">Eingabe 213-Projektdateien</span><span class="sxs-lookup"><span data-stu-id="fc6e8-477">MR Input 213 project files</span></span>](https://github.com/Microsoft/MixedReality213)
* [<span data-ttu-id="fc6e8-478">Mixed Reality Toolkit: Test Szene für Motion Controller</span><span class="sxs-lookup"><span data-stu-id="fc6e8-478">Mixed Reality Toolkit - Motion Controller Test scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [<span data-ttu-id="fc6e8-479">Mixed Reality Toolkit-Griff Mechanik</span><span class="sxs-lookup"><span data-stu-id="fc6e8-479">Mixed Reality Toolkit - Grab Mechanics</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [<span data-ttu-id="fc6e8-480">Entwicklungs Richtlinien für Motion Controller</span><span class="sxs-lookup"><span data-stu-id="fc6e8-480">Motion controller development guidelines</span></span>](motion-controllers.md)
