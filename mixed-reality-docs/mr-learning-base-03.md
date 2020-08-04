---
title: 'Tutorials zu den ersten Schritten: 3 Konfigurieren der MRTK-Profile'
description: In diesem Kurs erfahren Sie, wie Sie das Mixed Reality Toolkit (MRTK) verwenden, um eine Mixed Reality-Anwendung zu erstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: d3381241bb1418fb0e1fb7e5d29d552a533faa32
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376642"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="46bf2-105">3. Konfigurieren der MRTK-Profile</span><span class="sxs-lookup"><span data-stu-id="46bf2-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="46bf2-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="46bf2-106">Overview</span></span>

<span data-ttu-id="46bf2-107">In diesem Tutorial erfahren Sie, wie die MRTK-Profile angepasst und konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="46bf2-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="46bf2-108">Dieses Beispiel veranschaulicht insbesondere, wie das Gittermodell zur räumlichen Wahrnehmung durch Ändern der Einstellungen des Betrachters für räumliche Gittermodelle ausgeblendet wird.</span><span class="sxs-lookup"><span data-stu-id="46bf2-108">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="46bf2-109">Jedoch können Sie dieselben Prinzipien befolgen, um beliebige Einstellungen oder Werte in den MRTK-Profilen anzupassen.</span><span class="sxs-lookup"><span data-stu-id="46bf2-109">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

## <a name="objectives"></a><span data-ttu-id="46bf2-110">Ziele</span><span class="sxs-lookup"><span data-stu-id="46bf2-110">Objectives</span></span>

* <span data-ttu-id="46bf2-111">Erfahren, wie MRTK-Profile angepasst und konfiguriert werden</span><span class="sxs-lookup"><span data-stu-id="46bf2-111">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="46bf2-112">Ausblenden des Gittermodells für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="46bf2-112">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="46bf2-113">Ändern der Anzeigeoptionen für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="46bf2-113">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="46bf2-114">Dies sind die wichtigsten Schritte, die Sie ausführen, um das Gittermodell zur räumlichen Wahrnehmung auszublenden:</span><span class="sxs-lookup"><span data-stu-id="46bf2-114">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="46bf2-115">Klonen des Standardkonfigurationsprofils</span><span class="sxs-lookup"><span data-stu-id="46bf2-115">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="46bf2-116">Aktivieren des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="46bf2-116">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="46bf2-117">Klonen des Standardprofils des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="46bf2-117">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="46bf2-118">Klonen des Standardprofils des Betrachters für räumliche Gittermodelle</span><span class="sxs-lookup"><span data-stu-id="46bf2-118">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="46bf2-119">Ändern der Sichtbarkeit des Gittermodells zur räumlichen Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="46bf2-119">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="46bf2-120">Standardmäßig können die MRTK-Profile nicht bearbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="46bf2-120">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="46bf2-121">Es handelt sich um Standardprofilvorlagen, die Sie zuerst klonen müssen, um sie bearbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="46bf2-121">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="46bf2-122">Es gibt mehrere verschachtelte Profilebenen.</span><span class="sxs-lookup"><span data-stu-id="46bf2-122">There are several nested layers of profiles.</span></span> <span data-ttu-id="46bf2-123">Es ist daher gängige Praxis, mehrere Profile zu klonen und zu bearbeiten, wenn Einstellungen konfiguriert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="46bf2-123">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="46bf2-124">1. Klonen des Standardkonfigurationsprofils</span><span class="sxs-lookup"><span data-stu-id="46bf2-124">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="46bf2-125">Das Konfigurationsprofil ist das Profil der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="46bf2-125">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="46bf2-126">Folglich müssen Sie, um andere Profile bearbeiten zu können, zuerst das Konfigurationsprofil klonen.</span><span class="sxs-lookup"><span data-stu-id="46bf2-126">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="46bf2-127">Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt aus, und ändern Sie dann im Inspektorfenster das Konfigurationsprofil des **Mixed Reality-Toolkits** in **DefaultHoloLens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="46bf2-127">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="46bf2-129">Klicken Sie mit immer noch ausgewähltem **MixedRealityToolkit**-Objekt im Inspektor-Fenster auf die Schaltfläche **Copy & Customize** (Kopieren und Anpassen), um das Fenster „Clone Profile“ (Profil klonen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="46bf2-129">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="46bf2-131">Geben Sie im Fenster „Clone Profile“ (Profil klonen) einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_HoloLens2ConfigurationProfile_, und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie des **DefaultHololens2ConfigurationProfile** zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="46bf2-131">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="46bf2-133">Das neu erstellte Konfigurationsprofil wird jetzt als Konfigurationsprofil für Ihre Szene zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="46bf2-133">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="46bf2-135">Wählen Sie im Unity-Menü **File** > **Save** (Datei > Speichern) aus, um Ihre Szene zu speichern.</span><span class="sxs-lookup"><span data-stu-id="46bf2-135">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="46bf2-136">Denken Sie daran, Ihre Arbeit während der Tutorials zu speichern.</span><span class="sxs-lookup"><span data-stu-id="46bf2-136">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="46bf2-137">2. Aktivieren des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="46bf2-137">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="46bf2-138">Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt, dann im Inspektorfenster die Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) aus, und aktivieren Sie dann das Kontrollkästchen **Enable Spatial Awareness System** (System für räumliche Wahrnehmung aktivieren):</span><span class="sxs-lookup"><span data-stu-id="46bf2-138">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="46bf2-140">3. Klonen Sie das Standardprofil des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="46bf2-140">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="46bf2-141">Klicken Sie auf der Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) auf die Schaltfläche **Clone** (Klonen), um das Fenster „Clone Profile“ (Profil klonen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="46bf2-141">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="46bf2-143">Geben Sie im Fenster „Clone Profile“ (Profil klonen) einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie des **DefaultMixedRealitySpatialAwarenessSystemProfile** zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="46bf2-143">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="46bf2-145">Das neu erstellte Profil des Systems für räumliche Wahrnehmung wird Ihrem Konfigurationsprofil nun automatisch zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="46bf2-145">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="46bf2-147">4. Klonen des Standardprofils des Betrachters für räumliche Gittermodelle</span><span class="sxs-lookup"><span data-stu-id="46bf2-147">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="46bf2-148">Erweitern Sie bei immer noch ausgewählter Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) den Abschnitt **Windows Mixed Reality Spatial Mesh Observer** (Betrachter für das räumliche Gittermodell von Windows Mixed Reality), und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um das Clone Profile-Fenster (Profil klonen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="46bf2-148">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="46bf2-150">Geben Sie im Fenster „Clone Profile“ (Profil klonen) einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie von **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="46bf2-150">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="46bf2-152">Das neu erstellte Profil des Betrachters für das räumliche Gittermodell wird jetzt automatisch Ihrem Profil für das räumliche Wahrnehmungssystem zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="46bf2-152">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="46bf2-154">5. Ändern der Sichtbarkeit des Gittermodells zur räumlichen Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="46bf2-154">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="46bf2-155">Ändern Sie in den **Spatial Mesh Observer Settings** (Einstellungen des Betrachters für das räumliche Gittermodell) die **Display Option** (Anzeigeoption) in **Occlusion** (Verdeckung), um das Gittermodell zur räumlichen Abbildung unsichtbar zu machen, ohne seine Funktion aufzuheben:</span><span class="sxs-lookup"><span data-stu-id="46bf2-155">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="46bf2-157">Das räumliche Gittermodell ist zwar nicht sichtbar, es ist aber trotzdem vorhanden und funktioniert.</span><span class="sxs-lookup"><span data-stu-id="46bf2-157">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="46bf2-158">Beispielsweise sind eventuelle Hologramme hinter dem Gittermodell für die räumliche Abbildung nicht sichtbar, ganz wie ein Hologramm hinter einer physischen Wand.</span><span class="sxs-lookup"><span data-stu-id="46bf2-158">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="46bf2-159">Sie haben soeben erfahren, wie Sie eine Einstellung im MRTK-Profil ändern können.</span><span class="sxs-lookup"><span data-stu-id="46bf2-159">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="46bf2-160">Wie Sie sehen können, müssen Sie zum Anpassen der MRTK-Einstellungen zuerst Kopien der Standardprofile erstellen.</span><span class="sxs-lookup"><span data-stu-id="46bf2-160">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="46bf2-161">Da die Standardprofile nicht bearbeitbar sind, stehen sie Ihnen jederzeit als Referenz zur Verfügung, wenn Sie zu den Standardeinstellungen zurückkehren möchten.</span><span class="sxs-lookup"><span data-stu-id="46bf2-161">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="46bf2-162">Weitere Informationen zu MRTK-Profilen und ihrer Architektur finden Sie im [MRTK-Leitfaden zur Profilkonfiguration](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="46bf2-162">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="46bf2-163">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="46bf2-163">Congratulations</span></span>

<span data-ttu-id="46bf2-164">In diesem Tutorial haben Sie gelernt, wie Sie MRTK-Profile und Einstellungen klonen, anpassen und konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="46bf2-164">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

[<span data-ttu-id="46bf2-165">Nächstes Tutorial: 4. Positionieren von Objekten in der Szene</span><span class="sxs-lookup"><span data-stu-id="46bf2-165">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)
