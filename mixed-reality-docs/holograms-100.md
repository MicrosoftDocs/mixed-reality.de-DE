---
title: 'Grundlagen 100: Einstieg in Unity'
description: Erfahren Sie, wie Sie Ihre erste einfache "Hello World"-Anwendung mit gemischter Realität erstellen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Gemischte Realität, Windows Mixed Reality, hololens, immersive, VR, Mr, Einstieg, Hologram, Academy, Tutorial
ms.openlocfilehash: 0600383b3cca3f580f014597217afc6ae78836dd
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926639"
---
>[!NOTE]
><span data-ttu-id="b8a2c-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="b8a2c-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="b8a2c-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="b8a2c-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="b8a2c-108">Es wurde [eine neue Reihe von Tutorials](mrlearning-base.md) für hololens 2 gepostet.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a><span data-ttu-id="b8a2c-109">Grundlagen 100: Einstieg in Unity</span><span class="sxs-lookup"><span data-stu-id="b8a2c-109">MR Basics 100: Getting started with Unity</span></span>

<span data-ttu-id="b8a2c-110">Dieses Tutorial führt Sie durch die Erstellung einer einfachen Mixed Reality-APP, die mit Unity erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-110">This tutorial will walk you through creating a basic mixed reality app built with Unity.</span></span>

## <a name="device-support"></a><span data-ttu-id="b8a2c-111">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="b8a2c-111">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="b8a2c-112">Natürlich</span><span class="sxs-lookup"><span data-stu-id="b8a2c-112">Course</span></span></th><th style="width:150px"> <span data-ttu-id="b8a2c-113"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="b8a2c-113"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="b8a2c-114"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="b8a2c-114"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="b8a2c-115">Grundlagen 100: Einstieg in Unity</span><span class="sxs-lookup"><span data-stu-id="b8a2c-115">MR Basics 100: Getting started with Unity</span></span></td><td style="text-align: center;"> <span data-ttu-id="b8a2c-116">✔️</span><span class="sxs-lookup"><span data-stu-id="b8a2c-116">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="b8a2c-117">✔️</span><span class="sxs-lookup"><span data-stu-id="b8a2c-117">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="b8a2c-118">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="b8a2c-118">Prerequisites</span></span>

* <span data-ttu-id="b8a2c-119">Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md)konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-119">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

## <a name="chapter-1---create-a-new-project"></a><span data-ttu-id="b8a2c-120">Kapitel 1: Erstellen eines neuen Projekts</span><span class="sxs-lookup"><span data-stu-id="b8a2c-120">Chapter 1 - Create a New Project</span></span>

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

<span data-ttu-id="b8a2c-121">Zum Erstellen einer APP mit Unity müssen Sie zunächst ein Projekt erstellen.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-121">To build an app with Unity, you first need to create a project.</span></span> <span data-ttu-id="b8a2c-122">Dieses Projekt ist in einigen Ordnern organisiert, wobei es sich bei den wichtigsten Elementen um den Ordner "Assets" handelt.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-122">This project is organized into a few folders, the most important of which is your Assets folder.</span></span> <span data-ttu-id="b8a2c-123">Dies ist der Ordner, der alle Ressourcen enthält, die Sie aus Tools für die Erstellung digitaler Inhalte importieren, z. b. Maya, max. Kino 4D oder Photoshop, sämtlichen Code, den Sie mit Visual Studio oder Ihrem bevorzugten Code-Editor erstellen, und beliebig viele Inhalts Dateien, die Unity beim Verfassen von Szenen erstellt. , Animationen und andere Unity-Ressourcentypen im Editor.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-123">This is the folder that holds all assets you import from digital content creation tools such as Maya, Max Cinema 4D or Photoshop, all code you create with Visual Studio or your favorite code editor, and any number of content files that Unity creates as you compose scenes, animations and other Unity asset types in the editor.</span></span>

<span data-ttu-id="b8a2c-124">Um UWP-apps zu erstellen und bereitzustellen, kann Unity das Projekt als Visual Studio-Projekt Mappe exportieren, die alle erforderlichen Medienobjekt-und Code Dateien enthält.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-124">To build and deploy UWP apps, Unity can export the project as a Visual Studio solution that will contain all necessary asset and code files.</span></span>

1. <span data-ttu-id="b8a2c-125">Unity starten</span><span class="sxs-lookup"><span data-stu-id="b8a2c-125">Start Unity</span></span>
2. <span data-ttu-id="b8a2c-126">**Neu** auswählen</span><span class="sxs-lookup"><span data-stu-id="b8a2c-126">Select **New**</span></span>
3. <span data-ttu-id="b8a2c-127">Geben Sie einen Projektnamen ein (z. b. "mixedrealityintroduction").</span><span class="sxs-lookup"><span data-stu-id="b8a2c-127">Enter a project name (e.g. "MixedRealityIntroduction")</span></span>
4. <span data-ttu-id="b8a2c-128">Geben Sie einen Speicherort zum Speichern Ihres Projekts ein.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-128">Enter a location to save your project</span></span>
5. <span data-ttu-id="b8a2c-129">Stellen Sie sicher, dass der **3D-** Schalter ausgewählt ist</span><span class="sxs-lookup"><span data-stu-id="b8a2c-129">Ensure the **3D** toggle is selected</span></span>
6. <span data-ttu-id="b8a2c-130">**Projekt erstellen** auswählen</span><span class="sxs-lookup"><span data-stu-id="b8a2c-130">Select **Create project**</span></span>

<span data-ttu-id="b8a2c-131">Herzlichen Glückwunsch, Sie sind alle Setup für die ersten Schritte mit ihren Mixed Reality-Anpassungen.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-131">Congrats, you are all setup to get started with your mixed reality customizations now.</span></span>

## <a name="chapter-2---setup-the-camera"></a><span data-ttu-id="b8a2c-132">Kapitel 2: Einrichten der Kamera</span><span class="sxs-lookup"><span data-stu-id="b8a2c-132">Chapter 2 - Setup the Camera</span></span>

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

<span data-ttu-id="b8a2c-133">Die Unity-Hauptkamera behandelt die Kopf-und stereorenderingvorgänge.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-133">The Unity Main Camera handles head tracking and stereoscopic rendering.</span></span> <span data-ttu-id="b8a2c-134">An der Hauptkamera müssen einige Änderungen vorgenommen werden, damit Sie mit gemischter Realität verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-134">There are a few changes to make to the Main Camera to use it with mixed reality.</span></span>

1. <span data-ttu-id="b8a2c-135">Datei > neuen Szene auswählen</span><span class="sxs-lookup"><span data-stu-id="b8a2c-135">Select File > New Scene</span></span>

<span data-ttu-id="b8a2c-136">Erstens ist es einfacher, Ihre APP zu entwerfen, wenn Sie sich die Anfangsposition des Benutzers als (**X**: 0, **Y**: 0, **Z**: 0) vorstellen.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-136">First, it will be easier to lay out your app if you imagine the starting position of the user as (**X**: 0, **Y**: 0, **Z**: 0).</span></span> <span data-ttu-id="b8a2c-137">Da die Hauptkamera die Bewegung des Benutzers nachverfolgt, kann die Startposition des Benutzers festgelegt werden, indem die Startposition der Hauptkamera festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-137">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

1. <span data-ttu-id="b8a2c-138">Auswählen der **Hauptkamera** im **Hierarchie** Panel</span><span class="sxs-lookup"><span data-stu-id="b8a2c-138">Select **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="b8a2c-139">Suchen Sie im **Inspektor** -Panel die **Transformations** Komponente, und ändern Sie die **Position** von (**x**: 0, **y**: 1, **z**:-10) in (**x**: 0, **y**: 0, **z**: 0).</span><span class="sxs-lookup"><span data-stu-id="b8a2c-139">In the **Inspector** panel, find the **Transform** component and change the **Position** from (**X**: 0, **Y**: 1, **Z**: -10) to (**X**: 0, **Y**: 0, **Z**: 0)</span></span>

<span data-ttu-id="b8a2c-140">Zweitens benötigt der Standard Hintergrund der Kamera einige Gedanken.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-140">Second, the default Camera background needs some thought.</span></span>

<span data-ttu-id="b8a2c-141">**Bei hololens-Anwendungen**sollte die reale Welt hinter alles stehen, was von der Kamera gerendert wird, und keine Skybox-Textur.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-141">**For HoloLens applications**, the real world should appear behind everything the camera renders, not a Skybox texture.</span></span>

1. <span data-ttu-id="b8a2c-142">Wenn im Bereich **Hierarchie** weiterhin die **Hauptkamera** ausgewählt ist, suchen Sie im **Inspektor** -Panel nach der **Kamera** Komponente, und ändern Sie die Dropdown Liste **Flag löschen** von **Skybox** in voll **Tonfarbe**.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-142">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Clear Flags** dropdown from **Skybox** to **Solid Color**.</span></span>
2. <span data-ttu-id="b8a2c-143">Wählen Sie die **Hintergrund** Farbauswahl aus, und ändern Sie die **RGBA** -Werte in (0,0).</span><span class="sxs-lookup"><span data-stu-id="b8a2c-143">Select the **Background** color picker and change the **RGBA** values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="b8a2c-144">**Für gemischte Reality-Anwendungen, die auf immersive Headsets ausgerichtet**sind, können wir die von Unity bereitgestellte Standard Textur von Skybox verwenden.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-144">**For mixed reality applications targeted to immersive headsets**, we can use the default Skybox texture that Unity provides.</span></span>

1. <span data-ttu-id="b8a2c-145">Wenn im **Hierarchie** Panel noch die **Hauptkamera** ausgewählt ist, suchen Sie im **Inspektor** -Panel nach der **Kamera** Komponente, und lassen Sie die Dropdown Liste **Flag löschen** auf **Skybox**.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-145">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Clear Flags** dropdown to **Skybox**.</span></span>

<span data-ttu-id="b8a2c-146">Als drittes betrachten wir die Near-Clip-Ebene in Unity und verhindern, dass Objekte zu nah an den Benutzern gerendert werden, wenn ein Benutzer ein Objekt nähert oder ein Objekt einen Benutzer nähert.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-146">Third, let us consider the near clip plane in Unity and prevent objects from being rendered too close to the users eyes as a user approaches an object or an object approaches a user.</span></span>

<span data-ttu-id="b8a2c-147">**Bei hololens-Anwendungen**kann die Near-Clip-Ebene auf die [hololens-empfohlenen](camera-in-unity.md#clip-planes) 0,85 Meter festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-147">**For HoloLens applications**, the near clip plane can be set to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 meters.</span></span>

1. <span data-ttu-id="b8a2c-148">Wenn im Bereich **Hierarchie** weiterhin die **Hauptkamera** ausgewählt ist, suchen Sie im **Inspektor** -Panel nach der **Kamera** Komponente, und ändern Sie das Feld **near-Clip Plane** von der Standardeinstellung **0,3** auf die empfohlenen Werte für hololens **0,85.** .</span><span class="sxs-lookup"><span data-stu-id="b8a2c-148">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Near Clip Plane** field from the default **0.3** to the HoloLens recommended **0.85**.</span></span>

<span data-ttu-id="b8a2c-149">**Für gemischte Reality-Anwendungen, die auf immersive Headsets ausgerichtet**sind, können wir die von Unity bereitgestellte Standardeinstellung verwenden.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-149">**For mixed reality applications targeted to immersive headsets**, we can use the default setting that Unity provides.</span></span>

1. <span data-ttu-id="b8a2c-150">Wenn im Bereich **Hierarchie** weiterhin die **Hauptkamera** ausgewählt ist, suchen Sie im **Inspektor** -Panel nach der **Kamera** Komponente, und lassen Sie das Feld **near Clip Plane** auf den Standardwert **0,3**.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-150">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Near Clip Plane** field to the default **0.3**.</span></span>

<span data-ttu-id="b8a2c-151">Abschließend können wir unseren Fortschritt speichern.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-151">Finally, let us save our progress so far.</span></span> <span data-ttu-id="b8a2c-152">Um die Szenen Änderungen zu speichern, klicken Sie auf **Datei > Szene speichern**unter, benennen Sie **die Szene,** und wählen Sie **Speichern**aus.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-152">To save the scene changes, select **File > Save Scene As**, name the scene **Main**, and select **Save**.</span></span>

## <a name="chapter-3---setup-the-project-settings"></a><span data-ttu-id="b8a2c-153">Kapitel 3: Einrichten der Projekteinstellungen</span><span class="sxs-lookup"><span data-stu-id="b8a2c-153">Chapter 3 - Setup the Project Settings</span></span>

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

<span data-ttu-id="b8a2c-154">In diesem Kapitel werden einige Unity-Projekteinstellungen festgelegt, die uns dabei helfen, das Windows Holographic SDK für die Entwicklung zu entwickeln.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-154">In this chapter, we will set some Unity project settings that help us target the Windows Holographic SDK for development.</span></span> <span data-ttu-id="b8a2c-155">Wir legen auch einige Qualitätseinstellungen für die Anwendung fest.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-155">We will also set some quality settings for our application.</span></span> <span data-ttu-id="b8a2c-156">Abschließend wird sichergestellt, dass unsere Buildziele auf Windows Store festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-156">Finally, we will ensure our build targets are set to Windows Store.</span></span>

### <a name="unity-performance-and-quality-settings"></a><span data-ttu-id="b8a2c-157">Unity-Leistungs-und Qualitätseinstellungen</span><span class="sxs-lookup"><span data-stu-id="b8a2c-157">Unity performance and quality settings</span></span>

<span data-ttu-id="b8a2c-158">**Unity-Qualitätseinstellungen für hololens**</span><span class="sxs-lookup"><span data-stu-id="b8a2c-158">**Unity quality settings for HoloLens**</span></span>

![Unity-Qualitätseinstellungen für hololens](images/qualitysettings.png)

<span data-ttu-id="b8a2c-160">Da das Verwalten von hoher Framerate in hololens so wichtig ist, möchten wir, dass die Qualitätseinstellungen für die schnellste Leistung optimiert werden.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-160">Since maintaining high framerate on HoloLens is so important, we want the quality settings tuned for fastest performance.</span></span> <span data-ttu-id="b8a2c-161">Ausführlichere Informationen zur Leistung finden Sie unter [Empfehlungen zur Leistung für Unity](performance-recommendations-for-unity.md).</span><span class="sxs-lookup"><span data-stu-id="b8a2c-161">For more detailed performance information, [Performance recommendations for Unity](performance-recommendations-for-unity.md).</span></span>

1. <span data-ttu-id="b8a2c-162">Wählen Sie **> Projekteinstellungen bearbeiten > Qualität** aus.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-162">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="b8a2c-163">Wählen Sie im **Windows Store** -Logo die **Dropdown** Liste aus, und wählen Sie **sehr niedrig**aus.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-163">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="b8a2c-164">Sie werden feststellen, dass die Einstellung ordnungsgemäß angewendet wird, wenn das Feld in der Windows Store-Spalte und die **sehr niedrige** Zeile grün ist.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-164">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

<span data-ttu-id="b8a2c-165">**Für gemischte Reality-Anwendungen, die für die Anzeige von Anzeigen vorgesehen**sind, können Sie die Qualitätseinstellungen auf die Standardwerte überlassen.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-165">**For mixed reality applications targeted to occluded displays**, you can leave the quality settings to its default values.</span></span>

### <a name="target-windows-10-sdk"></a><span data-ttu-id="b8a2c-166">Windows 10-Ziel-SDK</span><span class="sxs-lookup"><span data-stu-id="b8a2c-166">Target Windows 10 SDK</span></span>

<span data-ttu-id="b8a2c-167">**Windows Holographic-Ziel SDK**</span><span class="sxs-lookup"><span data-stu-id="b8a2c-167">**Target Windows Holographic SDK**</span></span>

![Windows Holographic-Ziel SDK](images/xrsettings.png)

<span data-ttu-id="b8a2c-169">Wir müssen Unity mitteilen, dass die zu exportierende App eine [immersive Ansicht](app-views.md) anstelle einer 2D-Ansicht erstellen sollte.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-169">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="b8a2c-170">Dies geschieht durch Aktivieren der Virtual Reality-Unterstützung für Unity, die auf das Windows 10 SDK abzielen.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-170">We do this by enabling Virtual Reality support on Unity targeting the Windows 10 SDK.</span></span>

1. <span data-ttu-id="b8a2c-171">Wechseln Sie zu **Edit > Project Settings > Player**.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-171">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="b8a2c-172">Wählen Sie im **Inspektor-Panel** für die Player Einstellungen das **Windows Store** -Symbol aus.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-172">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="b8a2c-173">Erweitern Sie die Gruppe " **XR-Einstellungen** ".</span><span class="sxs-lookup"><span data-stu-id="b8a2c-173">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="b8a2c-174">Aktivieren Sie im Abschnitt " **Rendering** " das Kontrollkästchen " **Virtual Reality supported** ", um eine neue **Virtual Reality-sdsliste** hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-174">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="b8a2c-175">Vergewissern Sie sich, dass **Windows Mixed Reality** in der Liste angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-175">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="b8a2c-176">Wenn dies nicht der Grund ist, wählen Sie die Schaltfläche **+** unten in der Liste aus, und wählen Sie **Windows Mixed Reality**aus.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-176">If not, select the **+** button at the bottom of the list and choose **Windows Mixed Reality**.</span></span>

>[!NOTE]
><span data-ttu-id="b8a2c-177">Wenn das **Windows Store** -Symbol nicht angezeigt wird, vergewissern Sie sich, dass Sie vor der Installation das Windows Store .NET-Skript-Back-End ausgewählt haben.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-177">If you do not see the **Windows Store** icon, double check to make sure you selected the Windows Store .NET Scripting Backend prior to installation.</span></span> <span data-ttu-id="b8a2c-178">Andernfalls müssen Sie Unity möglicherweise mit der richtigen Windows-Installation neu installieren.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-178">If not, you may need to reinstall Unity with the correct Windows installation.</span></span>

<span data-ttu-id="b8a2c-179">**.NET-Konfiguration überprüfen**</span><span class="sxs-lookup"><span data-stu-id="b8a2c-179">**Verify .NET Configuration**</span></span>

![.NET-Konfiguration überprüfen](images/configoptions-375px.png)

1. <span data-ttu-id="b8a2c-181">Wechseln Sie zu **Edit > Project Settings > Player** (möglicherweise noch im vorherigen Schritt).</span><span class="sxs-lookup"><span data-stu-id="b8a2c-181">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="b8a2c-182">Wählen Sie im **Inspektor-Panel** für die Player Einstellungen das **Windows Store** -Symbol aus.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-182">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="b8a2c-183">Stellen Sie sicher, dass im Konfigurations Abschnitt **andere Einstellungen** das Skript für die **Skript** Erstellung auf **.net** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-183">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="b8a2c-184">Tolle Aufgabe zum Anwenden aller Projekteinstellungen.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-184">Awesome job on getting all the project settings applied.</span></span> <span data-ttu-id="b8a2c-185">Als Nächstes fügen wir ein Hologram hinzu.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-185">Next, let us add a hologram!</span></span>

## <a name="chapter-4---create-a-cube"></a><span data-ttu-id="b8a2c-186">Kapitel 4: Erstellen eines Cubes</span><span class="sxs-lookup"><span data-stu-id="b8a2c-186">Chapter 4 - Create a cube</span></span>

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

<span data-ttu-id="b8a2c-187">Das Erstellen eines Cubes in Ihrem Unity-Projekt erfolgt genauso wie das Erstellen eines beliebigen anderen Objekts in Unity.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-187">Creating a cube in your Unity project is just like creating any other object in Unity.</span></span> <span data-ttu-id="b8a2c-188">Das Platzieren eines Cubes vor dem Benutzer ist einfach, da das Koordinatensystem von Unity der realen Welt zugeordnet ist, wobei eine Einheit in Unity ungefähr eine Meter in der realen Welt ist.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-188">Placing a cube in front of the user is easy because Unity's coordinate system is mapped to the real world - where one meter in Unity is approximately one meter in the real world.</span></span>

1. <span data-ttu-id="b8a2c-189">Wählen Sie in der oberen linken Ecke des Bereichs **Hierarchie** die Dropdown Liste **Erstellen** aus, und wählen Sie **3D-Objekt > Cube**aus.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-189">In the top left corner of the **Hierarchy** panel, select the **Create** dropdown and choose **3D Object > Cube**.</span></span>
2. <span data-ttu-id="b8a2c-190">Wählen Sie im **Hierarchie** Panel den neu erstellten **Cube** aus.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-190">Select the newly created **Cube** in the **Hierarchy** panel</span></span>
3. <span data-ttu-id="b8a2c-191">Suchen Sie im **Inspektor** die **Transformations** Komponente, und ändern Sie die **Position** in (**X**: 0, **Y**: 0, **Z**: 2).</span><span class="sxs-lookup"><span data-stu-id="b8a2c-191">In the **Inspector** find the **Transform** component and change **Position** to (**X**: 0, **Y**: 0, **Z**: 2).</span></span> <span data-ttu-id="b8a2c-192">*Dadurch wird der Cube 2 Meter vor der Anfangsposition des Benutzers positioniert.*</span><span class="sxs-lookup"><span data-stu-id="b8a2c-192">*This positions the cube 2 meters in front of the user's starting position.*</span></span>
4. <span data-ttu-id="b8a2c-193">Ändern Sie in der **Transformations** Komponente **die Drehung** in (**x**: 45, **y**: 45, **z**: 45), und ändern Sie die **Skalierung** in (**x**: 0,25, **y**: 0,25, **z**: 0,25).</span><span class="sxs-lookup"><span data-stu-id="b8a2c-193">In the **Transform** component, change **Rotation** to (**X**: 45, **Y**: 45, **Z**: 45) and change **Scale** to (**X**: 0.25, **Y**: 0.25, **Z**: 0.25).</span></span> <span data-ttu-id="b8a2c-194">*Dadurch wird der Cube auf 0,25 Meter skaliert.*</span><span class="sxs-lookup"><span data-stu-id="b8a2c-194">*This scales the cube to 0.25 meters.*</span></span>
5. <span data-ttu-id="b8a2c-195">Um die Szenen Änderungen zu speichern, wählen Sie **Datei > Szene speichern**aus.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-195">To save the scene changes, select **File > Save Scene**.</span></span>

## <a name="chapter-5---verify-on-device-from-unity-editor"></a><span data-ttu-id="b8a2c-196">Kapitel 5: Überprüfen des Geräts über den Unity-Editor</span><span class="sxs-lookup"><span data-stu-id="b8a2c-196">Chapter 5 - Verify on device from Unity editor</span></span>

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

<span data-ttu-id="b8a2c-197">Nachdem wir nun den Cube erstellt haben, ist es an der Zeit, eine schnell Überprüfung im Gerät durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-197">Now that we have created our cube, it is time to do a quick check in device.</span></span> <span data-ttu-id="b8a2c-198">Sie können dies direkt im Unity-Editor tun.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-198">You can do this directly from within the Unity editor.</span></span>

### <a name="initial-setup"></a><span data-ttu-id="b8a2c-199">Anfängliche Einrichtung</span><span class="sxs-lookup"><span data-stu-id="b8a2c-199">Initial setup</span></span>

1. <span data-ttu-id="b8a2c-200">Öffnen Sie auf dem Entwicklungs-PC in Unity das Fenster **Datei > Fenster Build-Einstellungen** .</span><span class="sxs-lookup"><span data-stu-id="b8a2c-200">On your development PC, in Unity, open **File > Build Settings** window.</span></span>
2. <span data-ttu-id="b8a2c-201">Ändern Sie **Platform** in **universelle Windows-Plattform** und klicken Sie auf **Plattform wechseln** .</span><span class="sxs-lookup"><span data-stu-id="b8a2c-201">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**</span></span>

### <a name="for-hololens-use-unity-remoting"></a><span data-ttu-id="b8a2c-202">Verwenden Sie für hololens Unity-Remoting</span><span class="sxs-lookup"><span data-stu-id="b8a2c-202">For HoloLens use Unity Remoting</span></span>

1. <span data-ttu-id="b8a2c-203">Installieren und führen Sie auf Ihren hololens den [Holographic Remoting Player](holographic-remoting-player.md)aus, der im Windows Store verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-203">On your HoloLens, install and run the [Holographic Remoting Player](holographic-remoting-player.md), available from the Windows Store.</span></span> <span data-ttu-id="b8a2c-204">Starten Sie die Anwendung auf dem Gerät, und Sie wechselt in den Wartezustand und zeigt die IP-Adresse des Geräts an.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-204">Launch the application on the device, and it will enter a waiting state and show the IP address of the device.</span></span> <span data-ttu-id="b8a2c-205">Notieren Sie sich die IP-Adresse.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-205">Note down the IP.</span></span>
2. <span data-ttu-id="b8a2c-206">Öffnen Sie **Fenster > XR > Holographic Emulation**.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-206">Open **Window > XR > Holographic Emulation**.</span></span>
3. <span data-ttu-id="b8a2c-207">Ändern Sie den **Emulations Modus** von **None** in **Remote zu Gerät**.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-207">Change **Emulation Mode** from **None** to **Remote to Device**.</span></span>
4. <span data-ttu-id="b8a2c-208">Geben Sie auf dem **Remote Computer**die IP-Adresse der zuvor notierten hololens ein.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-208">In **Remote Machine**, enter the IP address of your HoloLens noted earlier.</span></span>
5. <span data-ttu-id="b8a2c-209">Klicken Sie auf **Verbinden**.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-209">Click **Connect**.</span></span>
6. <span data-ttu-id="b8a2c-210">Stellen Sie sicher, dass der **Verbindungs Status** in grünes **verbunden**wechselt.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-210">Ensure the **Connection Status** changes to green **Connected**.</span></span>
7. <span data-ttu-id="b8a2c-211">Jetzt können **Sie im Unity-Editor auf "** wiedergeben" klicken.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-211">Now you can now click **Play** in the Unity editor.</span></span>

<span data-ttu-id="b8a2c-212">Nun können Sie den Cube im Gerät und im Editor sehen.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-212">You will now be able to see the cube in device and in the editor.</span></span> <span data-ttu-id="b8a2c-213">Sie können Objekte anhalten, überprüfen und Debuggen, wie Sie eine APP im Editor ausführen, da dies im Wesentlichen geschieht, aber mit Video-, Audio-und Geräte Eingaben, die zwischen dem Host Computer und dem Gerät über das Netzwerk übertragen werden.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-213">You can pause, inspect objects, and debug just like you are running an app in the editor, because that’s essentially what’s happening, but with video, audio, and device input transmitted back and forth across the network between the host machine and the device.</span></span>

### <a name="for-other-mixed-reality-supported-headsets"></a><span data-ttu-id="b8a2c-214">Für andere von Mixed Reality unterstützte Headsets</span><span class="sxs-lookup"><span data-stu-id="b8a2c-214">For other mixed reality supported headsets</span></span>

1. <span data-ttu-id="b8a2c-215">Verbinden Sie das Headset mit dem Entwicklungs-PC, indem Sie das USB-Kabel und das HDMI-oder Anzeige Anschlusskabel verwenden.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-215">Connect the headset to your development PC using the USB cable and the HDMI or display port cable.</span></span>
2. <span data-ttu-id="b8a2c-216">Starten Sie das **Mixed Reality-Portal** , und stellen Sie sicher, dass Sie die erste Ausführung abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-216">Launch the **Mixed Reality Portal** and ensure you have completed the first run experience.</span></span>
3. <span data-ttu-id="b8a2c-217">Aus Unity können Sie nun auf die Wiedergabe Schaltfläche klicken.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-217">From Unity, you can now press the Play button.</span></span>

<span data-ttu-id="b8a2c-218">Nun können Sie das Cube-Rendering in Ihrem Mixed Reality-Headset und im Editor sehen.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-218">You will now be able to see the cube rendering in your mixed reality headset and in the editor.</span></span>

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a><span data-ttu-id="b8a2c-219">Kapitel 6: Erstellen und Bereitstellen für ein Gerät aus Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b8a2c-219">Chapter 6 - Build and deploy to device from Visual Studio</span></span>

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

<span data-ttu-id="b8a2c-220">Nun können wir das Projekt in Visual Studio kompilieren und auf dem Zielgerät bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-220">We are now ready to compile our project to Visual Studio and deploy to our target device.</span></span>

### <a name="export-to-the-visual-studio-solution"></a><span data-ttu-id="b8a2c-221">Exportieren in die Visual Studio-Projekt Mappe</span><span class="sxs-lookup"><span data-stu-id="b8a2c-221">Export to the Visual Studio solution</span></span>

1.  <span data-ttu-id="b8a2c-222">Öffnen Sie die **Datei >** Fenster mit den Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-222">Open **File > Build Settings** window.</span></span>
2.  <span data-ttu-id="b8a2c-223">Klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-223">Click **Add Open Scenes** to add the scene.</span></span>
3.  <span data-ttu-id="b8a2c-224">Wechseln Sie zu **universelle Windows-Plattform** **Plattform** , und klicken Sie auf **Plattform wechseln**.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-224">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**.</span></span>
4.  <span data-ttu-id="b8a2c-225">Stellen Sie in den **Windows Store** -Einstellungen sicher, dass **SDK** **Universal 10**ist.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-225">In **Windows Store** settings ensure, **SDK** is **Universal 10**.</span></span>
5.  <span data-ttu-id="b8a2c-226">Überlassen Sie für Zielgerät **ein beliebiges Gerät für okkludierte** anzeigen, oder wechseln Sie zu **hololens**.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-226">For Target device, leave to **Any Device** for occluded displays or switch to **HoloLens**.</span></span>
6.  <span data-ttu-id="b8a2c-227">Der **UWP-Buildtyp** muss **D3D**lauten.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-227">**UWP Build Type** should be **D3D**.</span></span>
7.  <span data-ttu-id="b8a2c-228">Das **UWP SDK** ist möglicherweise auf dem **neuesten installiert**.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-228">**UWP SDK** could be left at **Latest installed**.</span></span>
8.  <span data-ttu-id="b8a2c-229">Überprüfen Sie die **Unity C# -Projekte** unter Debugging.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-229">Check **Unity C# Projects** under Debugging.</span></span>
9.  <span data-ttu-id="b8a2c-230">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-230">Click **Build**.</span></span>
10. <span data-ttu-id="b8a2c-231">Klicken Sie im Datei-Explorer auf **neuer Ordner** , und benennen Sie den Ordner **"App"** .</span><span class="sxs-lookup"><span data-stu-id="b8a2c-231">In the file explorer, click **New Folder** and name the folder **"App"**.</span></span>
11. <span data-ttu-id="b8a2c-232">Wenn der **App** -Ordner ausgewählt ist, klicken Sie auf die Schaltfläche **Ordner auswählen** .</span><span class="sxs-lookup"><span data-stu-id="b8a2c-232">With the **App** folder selected, click the **Select Folder** button.</span></span>
12. <span data-ttu-id="b8a2c-233">Wenn Unity erstellt wurde, wird ein Fenster des Windows-Datei-Explorers angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-233">When Unity is done building, a Windows File Explorer window will appear.</span></span>
13. <span data-ttu-id="b8a2c-234">Öffnen Sie den **App** -Ordner im Datei-Explorer.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-234">Open the **App** folder in file explorer.</span></span>
14. <span data-ttu-id="b8a2c-235">Öffnen Sie die generierte Visual Studio-Projekt Mappe (in diesem Beispiel mixedrealityintroduction. sln).</span><span class="sxs-lookup"><span data-stu-id="b8a2c-235">Open the generated Visual Studio solution (MixedRealityIntroduction.sln in this example)</span></span>

### <a name="compile-the-visual-studio-solution"></a><span data-ttu-id="b8a2c-236">Kompilieren der Visual Studio-Projekt Mappe</span><span class="sxs-lookup"><span data-stu-id="b8a2c-236">Compile the Visual Studio solution</span></span>

<span data-ttu-id="b8a2c-237">Schließlich kompilieren wir die exportierte Visual Studio-Projekt Mappe, stellen Sie bereit und testen Sie auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-237">Finally, we will compile the exported Visual Studio solution, deploy it, and try it out on the device.</span></span>

1. <span data-ttu-id="b8a2c-238">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von **Debug** in **Release** und von **Arm** in **x86**.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-238">Using the top toolbar in Visual Studio, change the target from **Debug** to **Release** and from **ARM** to **X86**.</span></span>

<span data-ttu-id="b8a2c-239">Die Anweisungen unterscheiden sich für die Bereitstellung auf einem Gerät im Vergleich zum Emulator.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-239">The instructions differ for deploying to a device versus the emulator.</span></span> <span data-ttu-id="b8a2c-240">Befolgen Sie die Anweisungen, die dem Setup entsprechen.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-240">Follow the instructions that match your setup.</span></span>

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a><span data-ttu-id="b8a2c-241">Bereitstellen für ein gemischtes Reality-Gerät über Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="b8a2c-241">Deploy to mixed reality device over Wi-Fi</span></span>

1. <span data-ttu-id="b8a2c-242">Klicken Sie auf den Pfeil neben der Schaltfläche **lokaler Computer** , und ändern Sie das Bereitstellungs Ziel in **Remote Computer**.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-242">Click on the arrow next to the **Local Machine** button, and change the deployment target to **Remote Machine**.</span></span>
2. <span data-ttu-id="b8a2c-243">Geben Sie die IP-Adresse Ihres gemischten Reality-Geräts ein, und ändern Sie den **Authentifizierungsmodus** für hololens und **Windows** für andere Geräte in Universal (unverschlüsseltes Protokoll).</span><span class="sxs-lookup"><span data-stu-id="b8a2c-243">Enter the IP address of your mixed reality device and change **Authentication Mode** to Universal (Unencrypted Protocol) for HoloLens and **Windows** for other devices.</span></span>
3. <span data-ttu-id="b8a2c-244">Klicken Sie auf **Debuggen > ohne Debugging starten**.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-244">Click **Debug > Start without debugging**.</span></span>

<span data-ttu-id="b8a2c-245">Bei **hololens**müssen Sie, wenn dies die erste Bereitstellung auf Ihrem Gerät ist, [mit Visual Studio](using-visual-studio.md)koppeln.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-245">**For HoloLens**, If this is the first time deploying to your device, you will need to pair [using Visual Studio](using-visual-studio.md).</span></span>

### <a name="deploy-to-mixed-reality-device-over-usb"></a><span data-ttu-id="b8a2c-246">Auf gemischtes Reality-Gerät über USB bereitstellen</span><span class="sxs-lookup"><span data-stu-id="b8a2c-246">Deploy to mixed reality device over USB</span></span>

<span data-ttu-id="b8a2c-247">Stellen Sie sicher, dass das Gerät über das USB-Kabel angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-247">Ensure you device is plugged in via the USB cable.</span></span>

1. <span data-ttu-id="b8a2c-248">Klicken Sie **für hololens**auf den Pfeil neben der Schaltfläche **lokaler Computer** , und ändern Sie das Bereitstellungs Ziel auf **Gerät**.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-248">**For HoloLens**, click on the arrow next to the **Local Machine** button, and change the deployment target to **Device**.</span></span>
2. <span data-ttu-id="b8a2c-249">Behalten Sie **für die Zielgeräte, die an Ihren PC angeschlossen**sind, die Einstellung lokaler Computer bei.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-249">**For targeting occluded devices attached to your PC**, keep the setting to Local Machine.</span></span> <span data-ttu-id="b8a2c-250">Stellen Sie sicher, dass das **gemischte Reality-Portal** ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-250">Ensure you have the **Mixed Reality Portal** running.</span></span>
3. <span data-ttu-id="b8a2c-251">Klicken Sie auf **Debuggen > ohne Debugging starten**.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-251">Click **Debug > Start without debugging**.</span></span>

### <a name="deploy-to-emulator"></a><span data-ttu-id="b8a2c-252">In Emulator bereitstellen</span><span class="sxs-lookup"><span data-stu-id="b8a2c-252">Deploy to Emulator</span></span>

1. <span data-ttu-id="b8a2c-253">Klicken Sie auf den Pfeil neben der Schaltfläche **Gerät** , und wählen Sie in der Dropdown-Taste **hololens Emulator**aus.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-253">Click on the arrow next to the **Device** button, and from drop down select **HoloLens Emulator**.</span></span>
2. <span data-ttu-id="b8a2c-254">Klicken Sie auf **Debuggen > ohne Debugging starten**.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-254">Click **Debug > Start without debugging**.</span></span>

### <a name="try-out-your-app"></a><span data-ttu-id="b8a2c-255">Testen Sie Ihre APP</span><span class="sxs-lookup"><span data-stu-id="b8a2c-255">Try out your app</span></span>

<span data-ttu-id="b8a2c-256">Nachdem Sie Ihre APP bereitgestellt haben, versuchen Sie, alle den Cube zu verschieben, und beobachten Sie, dass Sie in der Welt vor Ihnen bleibt.</span><span class="sxs-lookup"><span data-stu-id="b8a2c-256">Now that your app is deployed, try moving all around the cube and observe that it stays in the world in front of you.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8a2c-257">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="b8a2c-257">See also</span></span>

* [<span data-ttu-id="b8a2c-258">Unity-Entwicklung – Übersicht</span><span class="sxs-lookup"><span data-stu-id="b8a2c-258">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="b8a2c-259">Bewährte Methoden für das Arbeiten mit Unity und Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b8a2c-259">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="b8a2c-260">Grundlagen 101</span><span class="sxs-lookup"><span data-stu-id="b8a2c-260">MR Basics 101</span></span>](holograms-101.md)
* [<span data-ttu-id="b8a2c-261">Grundlagen 101 e</span><span class="sxs-lookup"><span data-stu-id="b8a2c-261">MR Basics 101E</span></span>](holograms-101e.md)
