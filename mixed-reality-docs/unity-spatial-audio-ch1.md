---
title: Lernprogramme für räumliche Audiodaten-1. Hinzufügen räumlicher Audiodaten zu Ihrem Projekt
description: Fügen Sie das Microsoft spatializer-Plug-in zu Ihrem Unity-Projekt hinzu, um auf hololens 2 HRTF Hardware Offload zuzugreifen.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: Gemischte Realität, Unity, Tutorial, hololens2, räumliche Audiodaten
ms.openlocfilehash: 8978017b3ce6c49a81b3eee2fe21e9234f4e71f0
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182797"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="9b094-105">Hinzufügen räumlicher Audiodaten zu Ihrem Unity-Projekt</span><span class="sxs-lookup"><span data-stu-id="9b094-105">Adding spatial audio to your Unity project</span></span>

<span data-ttu-id="9b094-106">Willkommen beim Spatial audiotutioral für Unity auf HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="9b094-106">Welcome to the spatial audio tutioral for Unity on HoloLens2.</span></span> <span data-ttu-id="9b094-107">Diese tutorialsequenz zeigt Folgendes:</span><span class="sxs-lookup"><span data-stu-id="9b094-107">This tutorial sequence shows:</span></span>
* <span data-ttu-id="9b094-108">Verwenden von HRTF Auslagerung auf hololens 2 in Unity</span><span class="sxs-lookup"><span data-stu-id="9b094-108">How to use HRTF offload on HoloLens 2 in Unity</span></span>
* <span data-ttu-id="9b094-109">Aktivieren von "Reverb" bei Verwendung von "HRTF Auslagerung"</span><span class="sxs-lookup"><span data-stu-id="9b094-109">How to enable reverb when using HRTF offload</span></span>

<span data-ttu-id="9b094-110">Das [GitHub-Repository für Microsoft spatializer](https://github.com/microsoft/spatialaudio-unity) verfügt über ein abgeschlossenes Unity-Projekt für diese tutorialsequenz.</span><span class="sxs-lookup"><span data-stu-id="9b094-110">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span> 

<span data-ttu-id="9b094-111">Unsere Empfehlungen für den Fall, dass es hilfreich sein kann, Klänge zu spatialisieren, finden Sie unter [Spatial Sound Design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span><span class="sxs-lookup"><span data-stu-id="9b094-111">For our recommendations on when it can be helpful to spatialize sounds, see [spatial sound design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="objectives"></a><span data-ttu-id="9b094-112">Ziele</span><span class="sxs-lookup"><span data-stu-id="9b094-112">Objectives</span></span>
<span data-ttu-id="9b094-113">In diesem ersten Kapitel gehen Sie wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="9b094-113">In this first chapter, you'll:</span></span>
* <span data-ttu-id="9b094-114">Erstellen eines Unity-Projekts und Importieren von mrtk</span><span class="sxs-lookup"><span data-stu-id="9b094-114">Create a Unity project and import MRTK</span></span>
* <span data-ttu-id="9b094-115">Importieren des Microsoft spatializer-Plug-ins</span><span class="sxs-lookup"><span data-stu-id="9b094-115">Import the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="9b094-116">Aktivieren des Microsoft spatializer-Plug-ins</span><span class="sxs-lookup"><span data-stu-id="9b094-116">Enable the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="9b094-117">Aktivieren räumlicher Audiodaten auf Ihrer Entwickler Arbeitsstation</span><span class="sxs-lookup"><span data-stu-id="9b094-117">Enable spatial audio on your developer workstation</span></span>

## <a name="create-a-project-and-add-nuget-for-unity"></a><span data-ttu-id="9b094-118">Erstellen eines Projekts und Hinzufügen von nuget für Unity</span><span class="sxs-lookup"><span data-stu-id="9b094-118">Create a project and add NuGet for Unity</span></span>
<span data-ttu-id="9b094-119">Beginnen Sie mit einem leeren Unity-Projekt, und fügen Sie nuget für Unity hinzu, und konfigurieren Sie es:</span><span class="sxs-lookup"><span data-stu-id="9b094-119">Start with an empty Unity project, then add and configure NuGet for Unity:</span></span>
1. <span data-ttu-id="9b094-120">Herunterladen des neuesten [nugetforunity. unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span><span class="sxs-lookup"><span data-stu-id="9b094-120">Download the latest [NuGetForUnity .unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span></span>
2. <span data-ttu-id="9b094-121">Klicken Sie in der Unity-Menüleiste auf **Assets-> Paket importieren > benutzerdefiniertes Paket...** , und installieren Sie das nugetforunity-Paket:</span><span class="sxs-lookup"><span data-stu-id="9b094-121">In the Unity menu bar, click **Assets -> Import Package -> Custom Package...** and install the NuGetForUnity package:</span></span>

![Benutzerdefiniertes Paket importieren](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a><span data-ttu-id="9b094-123">Hinzufügen des Windows Mixed Reality-Pakets</span><span class="sxs-lookup"><span data-stu-id="9b094-123">Add the Windows Mixed Reality package</span></span>
<span data-ttu-id="9b094-124">Die Unterstützung von Windows Mixed Reality in Unity 2019 und höher ist in einem optionalen Paket enthalten.</span><span class="sxs-lookup"><span data-stu-id="9b094-124">Windows Mixed Reality support in Unity 2019 and later is contained in an optional package.</span></span> <span data-ttu-id="9b094-125">Um Sie dem Projekt hinzuzufügen, öffnen Sie die **Fenster > Paket-Manager** über die Unity-Menüleiste:</span><span class="sxs-lookup"><span data-stu-id="9b094-125">To add it to your project, open **Window -> Package Manager** from the Unity menu bar:</span></span>

![Paket-Manager-Menü](images/spatial-audio/package-manager-menu.png)

<span data-ttu-id="9b094-127">Suchen und installieren Sie dann das **Windows Mixed Reality** -Paket:</span><span class="sxs-lookup"><span data-stu-id="9b094-127">Then find and install the **Windows Mixed Reality** package:</span></span>

![Paket-Manager-Fenster](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a><span data-ttu-id="9b094-129">Installieren von mrtk und Microsoft spatializer</span><span class="sxs-lookup"><span data-stu-id="9b094-129">Install MRTK and Microsoft Spatializer</span></span>
<span data-ttu-id="9b094-130">Installieren Sie mithilfe von nuget für Unity die mrtk-und Microsoft spatializer-Plug-ins:</span><span class="sxs-lookup"><span data-stu-id="9b094-130">Using NuGet for Unity, install the MRTK and Microsoft Spatializer plugins:</span></span>
1. <span data-ttu-id="9b094-131">Klicken Sie in der Unity-Menüleiste auf **nuget-> nuget-Pakete verwalten**.</span><span class="sxs-lookup"><span data-stu-id="9b094-131">In the Unity menu bar, click on **NuGet -> Manage NuGet Packages**.</span></span>

![NuGet-Pakete verwalten](images/spatial-audio/manage-nuget-packages.png)

2. <span data-ttu-id="9b094-133">Geben Sie im **Suchfeld** "Microsoft. mixedreality. Toolkit" ein, und installieren Sie das mrtk Core-Paket: **Microsoft. mixedreality. Toolkit. Foundation**</span><span class="sxs-lookup"><span data-stu-id="9b094-133">In the **Search** box, enter "Microsoft.MixedReality.Toolkit" and install the MRTK core package: **Microsoft.MixedReality.Toolkit.Foundation**</span></span>

![Mrtk-nuget-Paket](images/spatial-audio/mrtk-nuget-package.png)

<span data-ttu-id="9b094-135">Das [mrtk-nuget-Paket](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) hat zusätzlichen Kontext und Details.</span><span class="sxs-lookup"><span data-stu-id="9b094-135">[MRTK NuGet Package](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) has additional context and details.</span></span>

4. <span data-ttu-id="9b094-136">Geben Sie im **Suchfeld** "Microsoft. spatialaudiodatei" ein, und installieren Sie das Microsoft spatializer-Paket: **Microsoft. spatialaudio. spatializer. unity**</span><span class="sxs-lookup"><span data-stu-id="9b094-136">In the **Search** box, enter "Microsoft.SpatialAudio" and install the Microsoft Spatializer package: **Microsoft.SpatialAudio.Spatializer.Unity**</span></span>

![Spatializer-Plug-in nuget](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a><span data-ttu-id="9b094-138">Einrichten von mrtk in Ihrem Projekt</span><span class="sxs-lookup"><span data-stu-id="9b094-138">Set up MRTK in your project</span></span>

1. <span data-ttu-id="9b094-139">Öffnen Sie das Fenster mit den Buildeinstellungen, indem Sie zu **Datei > Buildeinstellungen**navigieren.</span><span class="sxs-lookup"><span data-stu-id="9b094-139">Open the Build Settings window by going to **File -> Build Settings**.</span></span>

2. <span data-ttu-id="9b094-140">Wählen Sie die _universelle Windows-Plattform_ aus, und klicken Sie auf **Plattform wechseln**</span><span class="sxs-lookup"><span data-stu-id="9b094-140">Select the _Universal Windows Platform_ and click **Switch Platform**.</span></span>

3. <span data-ttu-id="9b094-141">Klicken Sie im **Fenster erstellen** auf **Player Einstellungen** , um die Eigenschaften für **Player Einstellungen** im **Inspektor** -Bereich zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="9b094-141">Click **Player Settings** in the **Build Window** to open the **Player Settings** properties in the **Inspector** pane.</span></span>
    * <span data-ttu-id="9b094-142">Aktivieren Sie unter **XR-Einstellungen**das Kontrollkästchen **Virtual Reality supported** .</span><span class="sxs-lookup"><span data-stu-id="9b094-142">Under **XR Settings**, check the **Virtual Reality Supported** checkbox</span></span>
    * <span data-ttu-id="9b094-143">Ändern Sie unter " **XR Settings**" den **Stereo-Renderingmodus** in **Single Pass-instanziierten**.</span><span class="sxs-lookup"><span data-stu-id="9b094-143">Under **XR Settings**, change the **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>
    * <span data-ttu-id="9b094-144">Aktivieren Sie unter **Veröffentlichungs Einstellungen**das Kontrollkästchen **räumliche Wahrnehmung** im Abschnitt " **Funktionen** ".</span><span class="sxs-lookup"><span data-stu-id="9b094-144">Under **Publishing Settings**, check the **Spatial Perception** checkbox in the **Capabilities** section</span></span>

4. <span data-ttu-id="9b094-145">Klicken Sie in der Menüleiste auf **Mixed Reality Toolkit-> zu Szene hinzufügen und konfigurieren.**</span><span class="sxs-lookup"><span data-stu-id="9b094-145">On the menu bar, click **Mixed Reality Toolkit -> Add to Scene and Configure..**</span></span> <span data-ttu-id="9b094-146">, um mrtk Ihrer Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="9b094-146">to add MRTK to your scene.</span></span>

<span data-ttu-id="9b094-147">Weitere Anleitungen, einschließlich der Erstellung der APP und Bereitstellung auf einem hololens 2, finden Sie in [Kapitel 1 des Lern Basismoduls von Mr](mrlearning-base-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="9b094-147">For additional guidance, including how to build your app and deploy to a HoloLens 2, see [Chapter 1 of the MR Learning Base Module](mrlearning-base-ch1.md).</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="9b094-148">Aktivieren des Microsoft spatializer-Plug-ins</span><span class="sxs-lookup"><span data-stu-id="9b094-148">Enable the Microsoft Spatializer plugin</span></span>
<span data-ttu-id="9b094-149">Aktivieren Sie das **Microsoft spatializer** -Plug-in.</span><span class="sxs-lookup"><span data-stu-id="9b094-149">Enable the **Microsoft Spatializer** plugin.</span></span> <span data-ttu-id="9b094-150">Öffnen Sie die **Projekteinstellungen bearbeiten-> > Audiodatei**, und ändern Sie das **spatializer-Plug** -in in "Microsoft spatializer".</span><span class="sxs-lookup"><span data-stu-id="9b094-150">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span> <span data-ttu-id="9b094-151">Der **Audioabschnitt** der **Projekteinstellungen** sieht nun wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="9b094-151">The **Audio** section of the **Project Settings** will now look like this:</span></span>

![Projekteinstellungen mit dem spatializer-Plug-in](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="9b094-153">Aktivieren räumlicher Audiodaten auf Ihrer Arbeitsstation</span><span class="sxs-lookup"><span data-stu-id="9b094-153">Enable spatial audio on your workstation</span></span>
<span data-ttu-id="9b094-154">Unter Desktop Versionen von Windows ist das räumliche Audioformat standardmäßig deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="9b094-154">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="9b094-155">Aktivieren Sie diese Option, indem Sie in der Taskleiste mit der rechten Maustaste auf das Volume-Symbol klicken.</span><span class="sxs-lookup"><span data-stu-id="9b094-155">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="9b094-156">Um die beste Darstellung von hololens 2 zu erhalten, wählen Sie **räumliches sound-> Windows-Sonic für Kopfhörer aus**.</span><span class="sxs-lookup"><span data-stu-id="9b094-156">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![Desktop Einstellungen für räumliche Desktops](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> <span data-ttu-id="9b094-158">Diese Einstellung ist nur erforderlich, wenn Sie Vorhaben, das Projekt im Unity-Editor zu testen.</span><span class="sxs-lookup"><span data-stu-id="9b094-158">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9b094-159">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="9b094-159">Next steps</span></span>
<span data-ttu-id="9b094-160">Fahren Sie mit [Unity Spatial Audio Kapitel 2](unity-spatial-audio-ch2.md) fort, um Schaltflächen-Interaktions Sounds zu spatialisieren.</span><span class="sxs-lookup"><span data-stu-id="9b094-160">Continue on to [Unity spatial audio chapter 2](unity-spatial-audio-ch2.md) to spatialize button interaction sounds.</span></span>

