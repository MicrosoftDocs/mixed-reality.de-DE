---
title: 'Tutorials zu den ersten Schritten: 3 Erstellen der Benutzeroberfläche und Konfigurieren des Mixed Reality-Toolkits'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: c389c7a3d16770dcbf57d9acdcfd81c6507f7cd6
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "79376137"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a><span data-ttu-id="0fe4b-105">3. Erstellen der Benutzeroberfläche und Konfigurieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="0fe4b-105">3. Creating user interface and configure Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

<span data-ttu-id="0fe4b-106">Im vorherigen Tutorial haben Sie einige der Funktionen kennengelernt, die das Mixed Reality Toolkit (MRTK) bietet, indem Sie Ihre erste Anwendung für die HoloLens 2 gestartet haben.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-106">In the previous tutorial, you learned about some of the capabilities the Mixed Reality Toolkit (MRTK) has to offer by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="0fe4b-107">In diesem Tutorial erfahren Sie, wie Sie Schaltflächen zusammen mit den Textbereichen der Benutzeroberfläche erstellen und organisieren und mithilfe der Standardinteraktion (Berühren) mit den einzelnen Schaltflächen interagieren.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-107">In this tutorial you will learn how to create and organize buttons along with UI text panels, and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="0fe4b-108">Sie werden auch das Hinzufügen einfacher Aktionen und Effekte untersuchen, z. B. das Ändern von Größe, Klang und Farbe von Objekten.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-108">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="0fe4b-109">In diesem Modul werden grundlegende Konzepte zum Ändern von MRTK-Profilen vorgestellt, beginnend mit dem Deaktivieren der Darstellung des Gittermodells zur [räumlichen Abbildung](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="0fe4b-109">This module will introduce basic concepts about modifying MRTK profiles, starting with turning off the [spatial mapping](spatial-mapping.md) mesh visualization.</span></span>

## <a name="objectives"></a><span data-ttu-id="0fe4b-110">Ziele</span><span class="sxs-lookup"><span data-stu-id="0fe4b-110">Objectives</span></span>

* <span data-ttu-id="0fe4b-111">Anpassen und Konfigurieren von Mixed Reality-Toolkitprofilen</span><span class="sxs-lookup"><span data-stu-id="0fe4b-111">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="0fe4b-112">Interagieren mit Hologrammen über Elemente und Schaltflächen der Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="0fe4b-112">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="0fe4b-113">Grundlegende Eingaben und Interaktionen zum Handtracking</span><span class="sxs-lookup"><span data-stu-id="0fe4b-113">Basic hand-tracking input and interactions</span></span>

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="0fe4b-114">Konfigurieren der Mixed Reality-Toolkitprofile (Option zum Ändern der Anzeige der räumlichen Wahrnehmung)</span><span class="sxs-lookup"><span data-stu-id="0fe4b-114">How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

<span data-ttu-id="0fe4b-115">In diesem Abschnitt erfahren Sie, wie die standardmäßigen MRTK-Profile angepasst und konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-115">In this section, you will learn how to customize and configure the default MRTK profiles.</span></span>

<span data-ttu-id="0fe4b-116">Dieses Beispiel veranschaulicht insbesondere, wie das Gittermodell zur räumlichen Wahrnehmung durch Ändern der Einstellungen des Betrachters für räumliche Gittermodelle ausgeblendet wird.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-116">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="0fe4b-117">Jedoch können Sie dieselben Prinzipien befolgen, um beliebige Einstellungen oder Werte in den MRTK-Profilen anzupassen.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-117">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="0fe4b-118">Dies sind die wichtigsten Schritte, die Sie ausführen, um das Gittermodell zur räumlichen Wahrnehmung auszublenden:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-118">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="0fe4b-119">Klonen des Standardkonfigurationsprofils</span><span class="sxs-lookup"><span data-stu-id="0fe4b-119">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="0fe4b-120">Aktivieren des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="0fe4b-120">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="0fe4b-121">Klonen des Standardprofils des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="0fe4b-121">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="0fe4b-122">Klonen des Standardprofils des Betrachters für räumliche Gittermodelle</span><span class="sxs-lookup"><span data-stu-id="0fe4b-122">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="0fe4b-123">Ändern der Sichtbarkeit des Gittermodells zur räumlichen Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="0fe4b-123">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="0fe4b-124">Standardmäßig können die MRTK-Profile nicht bearbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-124">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="0fe4b-125">Es handelt sich um Standardprofilvorlagen, die Sie zuerst klonen müssen, um sie bearbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-125">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="0fe4b-126">Es gibt mehrere verschachtelte Profilebenen.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-126">There are several nested layers of profiles.</span></span> <span data-ttu-id="0fe4b-127">Es ist daher gängige Praxis, mehrere Profile zu klonen und zu bearbeiten, wenn Einstellungen konfiguriert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-127">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="0fe4b-128">1. Klonen des Standardkonfigurationsprofils</span><span class="sxs-lookup"><span data-stu-id="0fe4b-128">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="0fe4b-129">Das Konfigurationsprofil ist das Profil der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-129">The Configuration Profile is the top level profile.</span></span> <span data-ttu-id="0fe4b-130">Folglich müssen Sie, um andere Profile bearbeiten zu können, zuerst das Konfigurationsprofil klonen.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-130">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="0fe4b-131">Ändern Sie bei im Hierarchiefenster ausgewähltem **MixedRealityToolkit**-Objekt im Inspektorfenster das **Konfigurationsprofil** des Mixed Reality-Toolkits in **DefaultHoloLens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-131">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, change the Mixed Reality Toolkit **Configuration Profile** to **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

<span data-ttu-id="0fe4b-133">Klicken Sie mit immer noch ausgewähltem **MixedRealityToolkit**-Objekt im Inspektor-Fenster auf die Schaltfläche **Copy & Customize** (Kopieren und Anpassen), um das Fenster „Clone Profile“ (Profil klonen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-133">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

<span data-ttu-id="0fe4b-135">Klicken Sie im Fenster „Clone Profile“ auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie des Profils **DefaultHololens2ConfigurationProfile** zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-135">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

<span data-ttu-id="0fe4b-137">Das neu erstellte Konfigurationsprofil wird jetzt als Konfigurationsprofil für Ihre Szene zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-137">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

<span data-ttu-id="0fe4b-139">Wählen Sie im Unity-Menü **File** > **Save** (Datei > Speichern) aus, um Ihre Szene zu speichern.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-139">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="0fe4b-140">Denken Sie daran, Ihre Arbeit während des Tutorials zu speichern.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-140">Remember to save your work throughout the tutorial.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="0fe4b-141">2. Aktivieren des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="0fe4b-141">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="0fe4b-142">Wählen Sie bei immer noch im Hierarchiefenster ausgewähltem **MixedRealityToolkit**-Objekt im Inspektorfenster die Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) aus, und aktivieren Sie dann das Kontrollkästchen **Enable Spatial Awareness System** (System für räumliche Wahrnehmung):</span><span class="sxs-lookup"><span data-stu-id="0fe4b-142">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="0fe4b-144">3. Klonen Sie das Standardprofil des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="0fe4b-144">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="0fe4b-145">Klicken Sie auf der Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) auf die Schaltfläche **Clone** (Klonen), um das Fenster „Clone Profile“ (Profil klonen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-145">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

<span data-ttu-id="0fe4b-147">Klicken Sie im Fenster „Clone Profile“ auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie des Profils **DefaultMixedRealitySpatialAwarenessSystemProfile** zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-147">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

<span data-ttu-id="0fe4b-149">Das neu erstellte Profil des Systems für räumliche Wahrnehmung wird Ihrem Konfigurationsprofil nun automatisch zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-149">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="0fe4b-151">4. Klonen des Standardprofils des Betrachters für räumliche Gittermodelle</span><span class="sxs-lookup"><span data-stu-id="0fe4b-151">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="0fe4b-152">Erweitern Sie bei immer noch ausgewählter Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) den Abschnitt **Windows Mixed Reality Spatial Mesh Observer** (Betrachter für das räumliche Gittermodell von Windows Mixed Reality), und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um das Clone Profile-Fenster (Profil klonen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-152">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

<span data-ttu-id="0fe4b-154">Klicken Sie im Fenster „Clone Profile“ auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie des Profils **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-154">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

<span data-ttu-id="0fe4b-156">Das neu erstellte Profil des Betrachters für das räumliche Gittermodell wird jetzt automatisch Ihrem Profil für das räumliche Wahrnehmungssystem zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-156">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="0fe4b-158">5. Ändern der Sichtbarkeit des Gittermodells zur räumlichen Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="0fe4b-158">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="0fe4b-159">Ändern Sie in den **Spatial Mesh Observer Settings** (Einstellungen des Betrachters für das räumliche Gittermodell) die **Display Option** (Anzeigeoption) in **Occlusion** (Verdeckung), um das Gittermodell zur räumlichen Abbildung unsichtbar zu machen, ohne seine Funktion aufzuheben:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-159">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still being functional:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="0fe4b-161">Das räumliche Gittermodell ist zwar nicht sichtbar, es ist aber trotzdem vorhanden und funktioniert.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-161">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="0fe4b-162">Beispielsweise sind eventuelle Hologramme hinter dem Gittermodell für die räumliche Abbildung nicht sichtbar, ganz wie ein Hologramm hinter einer physischen Wand.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-162">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="0fe4b-163">Sie haben soeben erfahren, wie Sie eine Einstellung im MRTK-Profil ändern können.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-163">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="0fe4b-164">Wie Sie sehen können, müssen Sie zum Anpassen der MRTK-Einstellungen zuerst Kopien der Standardprofile erstellen.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-164">As you can see, in order to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="0fe4b-165">Da die Standardprofile nicht bearbeitbar sind, stehen sie Ihnen jederzeit als Referenz zur Verfügung, wenn Sie zu den Standardeinstellungen zurückkehren möchten.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-165">Because the default profiles are not editable, you will always have them as reference if you want revert back to the default settings.</span></span> <span data-ttu-id="0fe4b-166">Weitere Informationen zu MRTK-Profilen und ihrer Architektur finden Sie im [Mixed Reality Toolkit-Leitfaden zur Profilkonfiguration](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="0fe4b-166">To learn more about MRTK profiles and their architecture, you can visit the [Mixed Reality Toolkit profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="0fe4b-167">Gesten für Hand-Tracking und interaktionsfähige Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="0fe4b-167">Hand tracking gestures and interactable buttons</span></span>

<span data-ttu-id="0fe4b-168">In diesem Abschnitt erfahren Sie, wie Sie Hand-Tracking verwenden, um eine Schaltfläche zu drücken und Ereignisse auszulösen, um eine Aktion zu bewirken, wenn die Schaltfläche gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-168">In this section, you will learn how to use hand tracking to press a button and trigger events to cause an action when the button is pressed.</span></span>

<span data-ttu-id="0fe4b-169">Diese Beispiel zeigt Ihnen im Einzelnen, wie Sie die Farbe eines Würfels ändern, wenn die Schaltfläche gedrückt wird, und sie wieder zur ursprünglichen Farbe zurück ändern, wenn die Schaltfläche freigegeben wird.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-169">This particular example will show you how to change the color of a cube when the button is pressed and change it back to it's original color when the button is released.</span></span> <span data-ttu-id="0fe4b-170">Nach den gleichen Prinzipien können Sie aber auch andere Ereignisse erstellen.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-170">However, you may follow these same principles to create other events.</span></span>

<span data-ttu-id="0fe4b-171">Dies sind die wichtigsten Schritte, die Sie ausführen, um die Farbe des Würfels zu ändern:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-171">The main steps you will take to change the color of the cube are:</span></span>

1. <span data-ttu-id="0fe4b-172">Hinzufügen eines Prefabs für eine drückbare Schaltfläche zur Szene</span><span class="sxs-lookup"><span data-stu-id="0fe4b-172">Add a pressable button prefab to the scene</span></span>
2. <span data-ttu-id="0fe4b-173">Hinzufügen eines Würfels zur Szene</span><span class="sxs-lookup"><span data-stu-id="0fe4b-173">Add a cube to the scene</span></span>
3. <span data-ttu-id="0fe4b-174">Konfigurieren des InteractableOnPressReceiver-Ereignistyps</span><span class="sxs-lookup"><span data-stu-id="0fe4b-174">Configure the InteractableOnPressReceiver event type</span></span>
4. <span data-ttu-id="0fe4b-175">Konfigurieren des Würfels zum Empfangen des On Press-Ereignisses</span><span class="sxs-lookup"><span data-stu-id="0fe4b-175">Configure the cube to receive the On Press event</span></span>
5. <span data-ttu-id="0fe4b-176">Definieren der Aktion, die durch das On Press-Ereignis ausgelöst werden soll</span><span class="sxs-lookup"><span data-stu-id="0fe4b-176">Define the action to be triggered by the On Press event</span></span>
6. <span data-ttu-id="0fe4b-177">Konfigurieren des Würfels zum Empfangen des On Release-Ereignisses</span><span class="sxs-lookup"><span data-stu-id="0fe4b-177">Configure the cube to receive the On Release event</span></span>
7. <span data-ttu-id="0fe4b-178">Definieren der Aktion, die durch das On Release-Ereignis ausgelöst werden soll</span><span class="sxs-lookup"><span data-stu-id="0fe4b-178">Define the action to be triggered by the On Release event</span></span>
8. <span data-ttu-id="0fe4b-179">Testen der Schaltfläche mithilfe der Simulation im Editor</span><span class="sxs-lookup"><span data-stu-id="0fe4b-179">Test the button using the in-editor simulation</span></span>

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a><span data-ttu-id="0fe4b-180">1. Hinzufügen eines Prefabs für eine drückbare Schaltfläche zur Szene</span><span class="sxs-lookup"><span data-stu-id="0fe4b-180">1. Add a pressable button prefab to the scene</span></span>

> [!TIP]
> <span data-ttu-id="0fe4b-181">Ein <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Prefab</a> ist ein vorkonfiguriertes GameObject, das als Unity-Ressource gespeichert ist und durchgängig im Projekt verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-181">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="0fe4b-182">Suchen Sie im **Projektfenster** nach **PressableButtonHoloLens2**, um das Prefab zu finden, das Sie für dieses Beispiel verwenden werden:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-182">In the **Project window**, search for **PressableButtonHoloLens2** to locate the prefab you will use for this example:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

<span data-ttu-id="0fe4b-184">Wählen Sie im Ergebnis der **Suche** das **PressableButtonHoloLens2**-Prefab aus, und **ziehen** Sie es in das **Hierarchiefenster**, um es Ihrer Szene hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-184">In the **Search** result, select the **PressableButtonHoloLens2** prefab and **drag** it into the **Hierarchy** window to add it to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="0fe4b-186">Um Ihre Szene so anzuzeigen, wie Sie in der Abbildung unten dargestellt ist, doppelklicken Sie auf das PressableButtonHoloLens2-Objekt im Hierarchiefenster, um es in den Fokus zu bringen, und verwenden Sie dann den <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, der sich in der oberen rechten Ecke des Szenefensters befindet, um den Betrachtungswinkel so anzupassen, dass er entlang der vorwärts gerichteten Z-Achse verläuft.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-186">To display your scene as shown in the image below, double-click the PressableButtonHoloLens2 object in the Hierarchy window to bring it into focus, then use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis.</span></span>

<span data-ttu-id="0fe4b-187">Führen Sie bei immer noch ausgewähltem **PressableButtonHoloLens2**-Objekt im **Inspektorfenster** folgende Aktion aus:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-187">With the **PressableButtonHoloLens2** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="0fe4b-188">Ändern Sie seine **Transformationsposition** so, dass es vor der Kamera platziert ist, die am Ursprung positioniert ist, beispielsweise x = 0, y = 0 und z = 0,5</span><span class="sxs-lookup"><span data-stu-id="0fe4b-188">Change its Transform **Position** so it's positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="0fe4b-190">Im Allgemeinen entspricht 1 Positionseinheit in Unity ungefähr einem Meter in der physischen Umgebung.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-190">In general, 1 position unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="0fe4b-191">Es gibt jedoch Ausnahmen, z. B. wenn Objekte untergeordnete Objekte von skalierten Objekten sind.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-191">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span>

### <a name="2-add-a-cube-to-the-scene"></a><span data-ttu-id="0fe4b-192">2. Hinzufügen eines Würfels zur Szene</span><span class="sxs-lookup"><span data-stu-id="0fe4b-192">2. Add a cube to the scene</span></span>

<span data-ttu-id="0fe4b-193">Klicken Sie mit der rechten Maustaste auf einen leeren Bereich innerhalb des Hierarchiefensters, und wählen Sie **3D Object** > **Cube** (3D-Objekt > Würfel) aus, um Ihrer Szene einen Würfel hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-193">Right-click on an empty spot inside the Hierarchy window and select **3D Object** > **Cube** to add a cube to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

<span data-ttu-id="0fe4b-195">Führen Sie bei immer noch ausgewähltem **Cube**-Objekt im **Inspektorfenster** folgende Aktion aus:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-195">With the **Cube** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="0fe4b-196">Ändern Sie seine **Transformationsposition** so, dass es sich in der Nähe der drückbaren Schaltfläche befindet, ohne sich mit ihr zu überschneiden, beispielsweise x = 0, y = 0,04 und z = 0,5</span><span class="sxs-lookup"><span data-stu-id="0fe4b-196">Change its Transform **Position** so its located near the pressable button, but not overlapping with it, for example, x = 0, y = 0.04, and z = 0.5</span></span>
* <span data-ttu-id="0fe4b-197">Ändern Sie seinen **Transformationsmaßstab** auf eine passende Größe, beispielsweise x = 0,02, y = 0,02 und z = 0,02</span><span class="sxs-lookup"><span data-stu-id="0fe4b-197">Change its Transform **Scale** to a suitable size, for example, x = 0.02, y = 0.02, and z = 0.02</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a><span data-ttu-id="0fe4b-199">3. Konfigurieren des InteractableOnPressReceiver-Ereignistyps</span><span class="sxs-lookup"><span data-stu-id="0fe4b-199">3. Configure the InteractableOnPressReceiver event type</span></span>

<span data-ttu-id="0fe4b-200">Wählen Sie im Hierarchiefenster das **PressableButtonHoloLens2**-Objekt und dann im **Hamburger-Menü** des **Inspektorfensters** **Alle Komponenten reduzieren** aus, um eine Übersicht aller Komponenten dieses Objekts zu erhalten:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-200">In the Hierarchy window, select the **PressableButtonHoloLens2** object, then in the **Inspector** window **hamburger menu**, select **Collapse All Components** to get an overview of all components on this object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

<span data-ttu-id="0fe4b-202">Erweitern Sie die Komponente **Interactable (Script)** , und suchen und erweitern Sie dann den Abschnitt **Events** > **Receivers** (Ereignisse > Empfänger):</span><span class="sxs-lookup"><span data-stu-id="0fe4b-202">Expand the **Interactable (Script)** component, then locate and expand the **Events** > **Receivers** section:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

<span data-ttu-id="0fe4b-204">Klicken Sie auf die Schaltfläche **Ereignis hinzufügen**, um einen neuen Ereignisempfänger vom Ereignisempfängertyp **InteractableOnPressReceiver** zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-204">Click the **Add Event** button, to create a new event receiver of Event Receiver Type **InteractableOnPressReceiver**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> <span data-ttu-id="0fe4b-206">Der Ereignisempfängertyp mit dem Namen InteractableOnPressReceiver ermöglicht es der Schaltfläche, auf ein Drücken-Ereignis zu reagieren, wenn eine nachverfolgte Hand die Schaltfläche drückt.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-206">The Event Receiver Type named InteractableOnPressReceiver allows the button to respond to a pressed event when a tracked hand presses the button.</span></span>

<span data-ttu-id="0fe4b-207">Ändern Sie für den neu erstellten Ereignisempfänger den **Interaction Filter** (Interaktionsfilter) in **Near and Far** (Nah und fern):</span><span class="sxs-lookup"><span data-stu-id="0fe4b-207">For the newly created event receiver, change the **Interaction Filter** to **Near and Far**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a><span data-ttu-id="0fe4b-209">4. Konfigurieren des Würfels zum Empfangen des On Press-Ereignisses</span><span class="sxs-lookup"><span data-stu-id="0fe4b-209">4. Configure the cube to receive the On Press event</span></span>

<span data-ttu-id="0fe4b-210">**Klicken und ziehen** Sie im Hierarchiefenster den **Würfel** auf das Objektfeld **Event Properties** (Ereigniseigenschaften), damit das **On Press ()** -Ereignis den Würfel als Empfänger des On Press ()-Ereignisses zuweist:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-210">From the Hierarchy window, **click-and-drag** the **Cube** into the **Event Properties** object field for the **On Press ()** event to assign the Cube as a receiver of the On Press () event:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a><span data-ttu-id="0fe4b-212">5. Definieren der Aktion, die durch das On Press-Ereignis ausgelöst werden soll</span><span class="sxs-lookup"><span data-stu-id="0fe4b-212">5. Define the action to be triggered by the On Press event</span></span>

<span data-ttu-id="0fe4b-213">Klicken Sie auf das Aktions-Dropdownfeld, dem aktuell **No Function** (Keine Funktion) zugewiesen ist, und wählen Sie **MeshRenderer** > **Material material** aus, um festzulegen, dass die Materialeigenschaft des Würfels geändert wird, wenn das On Press ()-Ereignis ausgelöst wird:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-213">Click the action dropdown, currently assigned **No Function**, and select **MeshRenderer** > **Material material** to set the Cube's material property to be changed when the On Press () event is triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

<span data-ttu-id="0fe4b-215">Klicken Sie auf das kleine **Kreissymbol** neben dem Materialfeld, das zurzeit mit **None (Material)** aufgefüllt ist, um das Fenster „Select Material“ (Material auswählen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-215">Click the small **circle** icon next to the material field, currently populated with **None (Material)**, to open the Select Material window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

<span data-ttu-id="0fe4b-217">**Suchen** Sie im Fenster „Select Material“ (Material auswählen) nach **MRTK_Standard**, und wählen Sie ein passendes Material aus, beispielsweise **MRTK_Standard_Cyan**, damit sich die Farbe des Würfels in Blaugrün ändert, wenn die Schaltfläche gedrückt wird:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-217">In the Select Material window, **search** for **MRTK_Standard** and select a suitable material, for example, **MRTK_Standard_Cyan** so the Cube's color changes to cyan when the button is pressed:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a><span data-ttu-id="0fe4b-219">6. Konfigurieren des Würfels zum Empfangen des On Release-Ereignisses</span><span class="sxs-lookup"><span data-stu-id="0fe4b-219">6. Configure the cube to receive the On Release event</span></span>

<span data-ttu-id="0fe4b-220">**Wiederholen** Sie Schritt 4 für das On Release-Ereignis, um den **Würfel** als einen Empfänger des **On Release ()** -Ereignisses festzulegen.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-220">**Repeat** Step 4 for the On Release event to assign the **Cube** as a receiver of the **On Release ()** event.</span></span>

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a><span data-ttu-id="0fe4b-221">7. Definieren der Aktion, die durch das On Release-Ereignis ausgelöst werden soll</span><span class="sxs-lookup"><span data-stu-id="0fe4b-221">7. Define the action to be triggered by the On Release event</span></span>

<span data-ttu-id="0fe4b-222">**Wiederholen** Sie Schritt 5 für das On Release-Ereignis, wählen Sie jedoch das **MRTK_Standard_LightGray**-Material aus, damit die Farbe des Würfels beim Freigeben der Schaltfläche zur ursprünglichen hellgrauen Farbe zurückkehrt:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-222">**Repeat** Step 5 for the On Release event, but choose the **MRTK_Standard_LightGray** material so the Cube's color returns to its original light gray color when the button is released:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a><span data-ttu-id="0fe4b-224">8. Testen der Schaltfläche mithilfe der Simulation im Editor</span><span class="sxs-lookup"><span data-stu-id="0fe4b-224">8. Test the button using the in-editor simulation</span></span>

<span data-ttu-id="0fe4b-225">Drücken Sie die **Wiedergabe**-Schaltfläche, um in den Spielmodus zu wechseln, und verwenden Sie die in den Editor integrierte Eingabesimulation, um Ihre neu konfigurierte Schaltfläche zu testen.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-225">Press the **Play** button to enter Game mode and use the in-editor input simulation to test your newly configured button.</span></span>

<span data-ttu-id="0fe4b-226">Schaltfläche nicht gedrückt (LEERTASTE + Mausrad zurück):</span><span class="sxs-lookup"><span data-stu-id="0fe4b-226">Button not pressed (spacebar + mouse scroll wheel backward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

<span data-ttu-id="0fe4b-228">Schaltfläche gedrückt (LEERTASTE + Mausrad nach vorn):</span><span class="sxs-lookup"><span data-stu-id="0fe4b-228">Button pressed (spacebar + mouse scroll wheel forward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> <span data-ttu-id="0fe4b-230">Informationen zum Verwenden der in den Editor integrierten Eingabesimulation finden Sie im Leitfaden [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) (Verwenden der in den Editor integrierten Handeingabesimulation zum Testen einer Szene) im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="0fe4b-230">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="0fe4b-231">Erstellen eines Schaltflächenbereichs mit der MRTK-Rasterobjektsammlung</span><span class="sxs-lookup"><span data-stu-id="0fe4b-231">Creating a panel of buttons using MRTK's Grid Object Collection</span></span>

<span data-ttu-id="0fe4b-232">In diesem Abschnitt erfahren Sie, wie Sie mit dem MRTK-Tool „GridObjectCollection“ automatisch mehrere Schaltflächen zu einer ordentlichen Benutzeroberfläche ausrichten.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-232">In this section, you will learn how to automatically align multiple buttons into a neat user interface by using the MRTK's Grid Object Collection tool.</span></span>

<span data-ttu-id="0fe4b-233">In diesem speziellen Beispiel wird gezeigt, wie Sie einen Bereich mit fünf Schaltflächen erstellen, die horizontal ausgerichtet sind.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-233">This particular example will show you how to a create a panel with five buttons aligned horizontally.</span></span> <span data-ttu-id="0fe4b-234">Nach den gleichen Prinzipien können Sie aber auch andere Layouts erstellen.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-234">However, you may follow these same principles to create other layouts.</span></span>

<span data-ttu-id="0fe4b-235">Dies sind die wichtigsten Schritte, die Sie durchführen müssen:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-235">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="0fe4b-236">Ordnen Sie die Schaltflächen einem übergeordneten Objekt unter</span><span class="sxs-lookup"><span data-stu-id="0fe4b-236">Parent the button objects to a parent object</span></span>
2. <span data-ttu-id="0fe4b-237">Hinzufügen und Konfigurieren der Komponente „Grid Object Collection (Script)“</span><span class="sxs-lookup"><span data-stu-id="0fe4b-237">Add and configure the Grid Object Collection (Script) component</span></span>
3. <span data-ttu-id="0fe4b-238">Testen der Schaltflächen mithilfe der Simulation im Editor</span><span class="sxs-lookup"><span data-stu-id="0fe4b-238">Test the buttons using the in-editor simulation</span></span>

### <a name="1-parent-the-button-objects-to-a-parent-object"></a><span data-ttu-id="0fe4b-239">1. Ordnen Sie die Schaltflächen einem übergeordneten Objekt unter</span><span class="sxs-lookup"><span data-stu-id="0fe4b-239">1. Parent the button objects to a parent object</span></span>

<span data-ttu-id="0fe4b-240">Klicken Sie mit der rechten Maustaste auf einen leeren Bereich innerhalb des Hierarchiefensters, und wählen Sie **Leere erstellen** aus:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-240">Right-click on an empty spot inside the Hierarchy window and select **Create Empty**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

<span data-ttu-id="0fe4b-242">Klicken Sie mit der rechten Maustaste auf das neu erstellte Objekt, wählen Sie **Umbenennen** aus, und geben Sie ihm einen passenden Namen, beispielsweise **ButtonCollection**:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-242">Right-click on the newly created object, select **Rename**, and give it a suitable name, for example, **ButtonCollection**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

<span data-ttu-id="0fe4b-244">Wählen Sie das **PressableButtonHoloLens2**-Objekt aus, und **ziehen** Sie es auf das **ButtonCollection**-Objekt, um es zu einem untergeordneten Objekt des ButtonCollection-Objekts zu machen:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-244">Select the **PressableButtonHoloLens2** object and **drag** it on top of the **ButtonCollection** object to make it a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

<span data-ttu-id="0fe4b-246">Klicken Sie mit der rechten Maustaste auf das **PressableButtonHoloLens2**-Objekt, und wählen Sie **Duplizieren** aus, um eine Kopie davon zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-246">Right-click the **PressableButtonHoloLens2** object and select **Duplicate** to create a copy of it:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

<span data-ttu-id="0fe4b-248">**Wiederholen** Sie diesen Schritt noch vier Mal, bis Sie über insgesamt fünf PressableButtonHoloLens2-Objekte verfügen.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-248">**Repeat** this step four more times until you have a total of five PressableButtonHoloLens2 objects.</span></span>

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="0fe4b-249">2. Hinzufügen und Konfigurieren der Komponente „Grid Object Collection (Script)“</span><span class="sxs-lookup"><span data-stu-id="0fe4b-249">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="0fe4b-250">Klicken Sie mit im Hierarchiefenster ausgewähltem ButtonCollection-Objekt im Inspektorfenster auf die Schaltfläche **Komponente hinzufügen**, suchen Sie dann **Grid Object Collection** (Rasterobjektsammlung), und wählen Sie sie aus, um dem ButtonCollection-Objekt eine Komponente „Grid Object Collection (Script)“ hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-250">With the ButtonCollection object selected in the Hierarchy window, in the Inspector window, click the **Add Component** button, then search for and select **Grid Object Collection** to add a Grid Object Collection (Script) component to the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

<span data-ttu-id="0fe4b-252">Konfigurieren Sie die Komponente „Grid Object Collection (Script)“ wie folgt:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-252">Configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="0fe4b-253">Ändern Sie **Num Rows** (Anzahl Zeilen) in 1, um alle Schaltflächen in einer einzelnen Zeile auszurichten</span><span class="sxs-lookup"><span data-stu-id="0fe4b-253">Change **Num Rows** to 1 to have all buttons aligned on one single row</span></span>
* <span data-ttu-id="0fe4b-254">Ändern Sie **Cell Width**  (Zellbreite) in 0,05, um die Schaltflächen innerhalb der Zeile zu verteilen.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-254">Change **Cell Width** to 0.05 to space out the buttons within the row</span></span>

<span data-ttu-id="0fe4b-255">Klicken Sie dann auf die Schaltfläche **Sammlung aktualisieren**, um die neue Konfiguration zu übernehmen:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-255">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> <span data-ttu-id="0fe4b-257">Die Konfigurationsänderungen, die Sie soeben übernommen haben, stellen die erforderlichen Mindeständerungen dar, um das Ziel zu erreichen, die Schaltflächen in einer einzelnen Zeile zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-257">The configuration changes you just applied represent the minimum changes required to achieve the objective of placing the buttons in a single row.</span></span> <span data-ttu-id="0fe4b-258">In kommenden Projekten müssen Sie, abhängig von Faktoren wie beispielsweise der Ausrichtung der über- und untergeordneten Objekte, jedoch möglicherweise weitere Einstellungen anpassen, z. B. die Ausrichtungsart.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-258">However, in future projects, depending on factors such as, for example, the orientation of the parent and child objects, you might need to adjust other settings such as, for example, the Orient Type.</span></span> <span data-ttu-id="0fe4b-259">Weitere Informationen zur Rasterobjektsammlung des MRTK finden Sie im Leitfaden [Object collection scripts](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) (Skripts für Objektsammlungen) im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="0fe4b-259">To learn more about MRTK's Grid Object Collection, you can visit the [Object collection scripts](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

<span data-ttu-id="0fe4b-260">Ändern Sie bei immer noch im Hierarchiefenster ausgewähltem ButtonCollection-Objekt die **Transformationsposition** des ButtonCollection-Objekts so, dass seine untergeordneten Schaltflächenobjekte vor der Kamera positioniert sind, die sich am Ursprung befindet, beispielsweise x = 0, y = 0 und z = 0,5:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-260">With the ButtonCollection object still selected in the Hierarchy window, in the Inspector window, change the ButtonCollection object's Transform **Position** so its child button objects are positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> <span data-ttu-id="0fe4b-262">Als Sie das PressableButtonHoloLens2-Prefab im Abschnitt [Gesten für Handtracking und interaktionsfähige Schaltflächen](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) ursprünglich hinzufügten, positionierten Sie es vor der Kamera.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-262">When you first added the PressableButtonHoloLens2 prefab to the scene in the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) section above, you positioned it in front of the camera.</span></span> <span data-ttu-id="0fe4b-263">Da die Rasterobjektsammlung jedoch die Position ihrer unmittelbar untergeordneten Objekte steuert, wurde die Z-Position der untergeordneten PressableButtonHoloLens2-Objekte entsprechend des Standardabstands 0 der Rasterobjektsammlung vom Wert des übergeordneten Objekts auf 0 zurückgesetzt.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-263">However, because the Grid Object Collection controls its immediate child objects' position, the PressableButtonHoloLens2 child objects' Z Position were reset to 0 according to the Grid Object Collection's default Distance from parent value of 0.</span></span> <span data-ttu-id="0fe4b-264">Dies ist, neben der Aufrechterhaltung einer geordneten Positionsbeziehung von über- und untergeordneten Objekten, der Grund, warum wir die Position des übergeordneten ButtonCollection-Objekts nach vorn verschoben haben, statt den Abstand vom Wert des übergeordneten Objekts zu konfigurieren, um die untergeordneten PressableButtonHoloLens2-Objekte nach vorn zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-264">This, and to keep the parent/child positional relationship organized, is why we moved the parent ButtonCollection object's position forward instead of configuring the Distance from parent value to move the PressableButtonHoloLens2 child objects forward.</span></span>

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a><span data-ttu-id="0fe4b-265">3. Testen der Schaltflächen mithilfe der Simulation im Editor</span><span class="sxs-lookup"><span data-stu-id="0fe4b-265">3. Test the buttons using the in-editor simulation</span></span>

<span data-ttu-id="0fe4b-266">Drücken Sie die Wiedergabe-Schaltfläche, um in den Spielmodus zu wechseln, und verwenden Sie die in den Editor integrierte Simulation, um jede der Schaltflächen in Ihrem neu erstellten Schaltflächenbereich zu testen:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-266">Press the Play button to enter Game mode and use the in-editor input simulation to test each of the buttons in in your newly created panel of buttons:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> <span data-ttu-id="0fe4b-268">Wenn Sie aktuell eine der fünf Schaltflächen drücken, wechselt die Farbe des Würfels zu Blaugrün.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-268">Currently, when your press any of the five buttons, the cube color changes to cyan.</span></span> <span data-ttu-id="0fe4b-269">Um die Erfahrung interessanter zu machen, wenden Sie an, was Sie soeben gelernt haben, um für jede Schaltfläche den Wechsel des Würfels zu einer anderen Farbe zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-269">To make the experience more interesting, use what you just learn to configure each button to change the cube to a different color.</span></span>

## <a name="adding-text-into-your-scene"></a><span data-ttu-id="0fe4b-270">Hinzufügen von Text zu Ihrer Szene</span><span class="sxs-lookup"><span data-stu-id="0fe4b-270">Adding text into your scene</span></span>

<span data-ttu-id="0fe4b-271">In diesem Abschnitt erfahren Sie, wie Sie Ihren Mixed Reality-Erfahrungen mithilfe von TextMesh Pro in Unity Text hinzufügen, was Sie im Abschnitt [Importieren von TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) des vorherigen Tutorials vorbereitet haben.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-271">In this section, you will learn how to add text to your mixed reality experiences using Unity's TextMesh Pro, which you prepared in the [Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) section of the previous tutorial.</span></span>

<span data-ttu-id="0fe4b-272">In diesem speziellen Beispiel fügen Sie unterhalb der Schaltflächensammlung, die Sie im vorherigen Abschnitt erstellt haben, eine einfache Bezeichnung hinzu.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-272">In this particular example, you will add a simple label underneath the button collection you created in the previous section.</span></span>

<span data-ttu-id="0fe4b-273">Klicken Sie mit der rechten Maustaste auf das ButtonCollection-Objekt, und wählen Sie **3D-Objekt** > **Text – TextMeshPro** aus, um ein TextMeshPro-Objekt als untergeordnetes Objekt des ButtonCollection-Objekts zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-273">Right-click on the ButtonCollection object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro object as a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

<span data-ttu-id="0fe4b-275">Ändern Sie bei immer noch ausgewähltem neu erstelltem TextMeshPro-Objekt namens „Text (TMP)“ im Inspektorfenster dessen Position und Größe, sodass die Bezeichnung ordentlich unterhalb der Schaltflächensammlung platziert ist, beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-275">With the newly created TextMeshPro object, named Text (TMP), still selected, in the Inspector window change its position and size so the label is placed neatly underneath the button collection, for example:</span></span>

* <span data-ttu-id="0fe4b-276">Ändern Sie die Rect-Transformations-**Pos Y** in -0,0425</span><span class="sxs-lookup"><span data-stu-id="0fe4b-276">Change the Rect Transform **Pos Y** to -0.0425</span></span>
* <span data-ttu-id="0fe4b-277">Ändern Sie die Rect-Transformations-**Breite** in-0,24</span><span class="sxs-lookup"><span data-stu-id="0fe4b-277">Change the Rect Transform **Width** to 0.24</span></span>
* <span data-ttu-id="0fe4b-278">Ändern Sie die Rect-Transformations-**Höhe** in-0,024</span><span class="sxs-lookup"><span data-stu-id="0fe4b-278">Change the Rect Transform **Height** to 0.024</span></span>

<span data-ttu-id="0fe4b-279">Aktualisieren Sie dann den Text, um den Zweck der Bezeichnung wiederzugeben, und wählen Sie die Schriftarteigenschaften, sodass der Text in die Bezeichnung passt, beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-279">Then update the text to reflect what the label is for and choose font properties so the text fits within the label, for example:</span></span>

* <span data-ttu-id="0fe4b-280">Ändern Sie den **Text** von „Text Mesh Pro (Script)“ in „Schaltflächensammlung“</span><span class="sxs-lookup"><span data-stu-id="0fe4b-280">Change the Text Mesh Pro (Script) **Text** to Button Collection</span></span>
* <span data-ttu-id="0fe4b-281">Ändern Sie den **Schriftschnitt** von „Text Mesh Pro (Script)“ in „Fett“</span><span class="sxs-lookup"><span data-stu-id="0fe4b-281">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="0fe4b-282">Ändern Sie den **Schriftgrad** von „Text Mesh Pro (Script)“ in 0,2</span><span class="sxs-lookup"><span data-stu-id="0fe4b-282">Change the Text Mesh Pro (Script) **Font Size** to 0.2</span></span>
* <span data-ttu-id="0fe4b-283">Ändern Sie die **Ausrichtung** von „Text Mesh Pro (Script)“ in „Zentriert und Mittig“</span><span class="sxs-lookup"><span data-stu-id="0fe4b-283">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="0fe4b-285">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="0fe4b-285">Congratulations</span></span>

<span data-ttu-id="0fe4b-286">In diesem Tutorial haben Sie gelernt, wie Sie eine MRTK-Profileinstellung klonen, anpassen und konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-286">In this tutorial, you learned how to clone, customize, and configure an MRTK profile setting.</span></span> <span data-ttu-id="0fe4b-287">Sie haben außerdem erfahren, wie Sie mit Schaltflächen interagieren können, um Ereignisse mit nachverfolgten Händen für die HoloLens 2 auszulösen.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-287">You also learned how to interact with buttons to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="0fe4b-288">Abschließend haben Sie erfahren, wie Sie mit der MRTK-Komponente „Grid Object Collection“ (Rasterobjektsammlung) und „TextMeshPro“ von Unity eine einfache Benutzeroberfläche erstellen.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-288">Finally, you learned how to create a simple UI interface using the MRTK's Grid Object Collection component and Unity's Text Mesh Pro.</span></span>

[<span data-ttu-id="0fe4b-289">Nächstes Tutorial: 4. Platzieren dynamischer Inhalte und Verwenden von Solvern</span><span class="sxs-lookup"><span data-stu-id="0fe4b-289">Next Tutorial: 4. Placing dynamic content and using solvers</span></span>](mrlearning-base-ch3.md)
