---
title: 'Tutorials zu den ersten Schritten: 3. Erstellen einer Benutzeroberfläche und Konfigurieren von Mixed Reality Toolkit'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: f1d042150d1c81940e672b174c6c02ac71e05883
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554881"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a><span data-ttu-id="19b52-105">3. Erstellen einer Benutzeroberfläche und Konfigurieren von Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="19b52-105">3. Creating user interface and configure Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

<span data-ttu-id="19b52-106">Im vorherigen Tutorial haben Sie einige Funktionen kennengelernt, die das Mixed Reality Toolkit (mrtk) bietet, indem Sie Ihre erste Anwendung für die hololens 2 starten.</span><span class="sxs-lookup"><span data-stu-id="19b52-106">In the previous tutorial, you learned about some of the capabilities the Mixed Reality Toolkit (MRTK) has to offer by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="19b52-107">In diesem Tutorial erfahren Sie, wie Sie Schaltflächen zusammen mit UI-Textbereichen erstellen und organisieren und die Standard Interaktion (Toucheingabe) verwenden, um mit den einzelnen Schaltflächen zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="19b52-107">In this tutorial you will learn how to create and organize buttons along with UI text panels, and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="19b52-108">Sie werden auch das Hinzufügen einfacher Aktionen und Effekte untersuchen, z. B. das Ändern von Größe, Klang und Farbe von Objekten.</span><span class="sxs-lookup"><span data-stu-id="19b52-108">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="19b52-109">Dieses Modul führt grundlegende Konzepte zum Ändern von mrtk-Profilen ein, beginnend mit dem Ausschalten der Mesh-Visualisierung für [räumliche Karten](spatial-mapping.md) .</span><span class="sxs-lookup"><span data-stu-id="19b52-109">This module will introduce basic concepts about modifying MRTK profiles, starting with turning off the [spatial mapping](spatial-mapping.md) mesh visualization.</span></span>

## <a name="objectives"></a><span data-ttu-id="19b52-110">Ziele</span><span class="sxs-lookup"><span data-stu-id="19b52-110">Objectives</span></span>

* <span data-ttu-id="19b52-111">Anpassen und Konfigurieren von Mixed Reality-Toolkitprofilen</span><span class="sxs-lookup"><span data-stu-id="19b52-111">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="19b52-112">Interagieren mit holograms mithilfe von Benutzeroberflächen Elementen und Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="19b52-112">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="19b52-113">Grundlegende Eingaben und Interaktionen zum Handtracking</span><span class="sxs-lookup"><span data-stu-id="19b52-113">Basic hand-tracking input and interactions</span></span>

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="19b52-114">So konfigurieren Sie die Mixed Reality Toolkit-profile (Anzeige Option ' räumliches Bewusstsein ändern ')</span><span class="sxs-lookup"><span data-stu-id="19b52-114">How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

<span data-ttu-id="19b52-115">In diesem Abschnitt erfahren Sie, wie die standardmäßigen mrtk-Profile angepasst und konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="19b52-115">In this section, you will learn how to customize and configure the default MRTK profiles.</span></span>

<span data-ttu-id="19b52-116">In diesem speziellen Beispiel wird veranschaulicht, wie das räumliche Awareness-Mesh ausgeblendet wird, indem die Einstellungen des räumlichen Mesh-Beobachters geändert werden.</span><span class="sxs-lookup"><span data-stu-id="19b52-116">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="19b52-117">Sie können jedoch dieselben Prinzipien befolgen, um beliebige Einstellungen oder Werte in den mrtk-Profilen anzupassen.</span><span class="sxs-lookup"><span data-stu-id="19b52-117">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="19b52-118">Die wichtigsten Schritte, die Sie ausführen, um das räumliche Awareness-Mesh auszublenden, sind:</span><span class="sxs-lookup"><span data-stu-id="19b52-118">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="19b52-119">Standard Konfigurations Profil Klonen</span><span class="sxs-lookup"><span data-stu-id="19b52-119">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="19b52-120">Aktivieren des Systems für räumliche Informationen</span><span class="sxs-lookup"><span data-stu-id="19b52-120">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="19b52-121">Klonen des standardmäßigen Spatial Awareness System-Profils</span><span class="sxs-lookup"><span data-stu-id="19b52-121">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="19b52-122">Klonen des standardmäßigen Spatial Awareness Mesh-Profils</span><span class="sxs-lookup"><span data-stu-id="19b52-122">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="19b52-123">Ändern der Sichtbarkeit des Netzes für räumliche Informationen</span><span class="sxs-lookup"><span data-stu-id="19b52-123">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="19b52-124">Standardmäßig können die MRTK-Profile nicht bearbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="19b52-124">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="19b52-125">Dabei handelt es sich um Standardprofil Vorlagen, die Sie Klonen müssen, bevor Sie bearbeitet werden können.</span><span class="sxs-lookup"><span data-stu-id="19b52-125">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="19b52-126">Es gibt mehrere unterschiedliche Ebenen von Profilen.</span><span class="sxs-lookup"><span data-stu-id="19b52-126">There are several nested layers of profiles.</span></span> <span data-ttu-id="19b52-127">Daher ist es üblich, mehrere Profile zu klonen und zu bearbeiten, wenn eine oder mehrere Einstellungen konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="19b52-127">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="19b52-128">1. Klonen Sie das Standard Konfigurations Profil.</span><span class="sxs-lookup"><span data-stu-id="19b52-128">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="19b52-129">Das Konfigurations Profil ist das Profil der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="19b52-129">The Configuration Profile is the top level profile.</span></span> <span data-ttu-id="19b52-130">Daher müssen Sie zunächst das Konfigurations Profil Klonen, um andere Profile bearbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="19b52-130">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="19b52-131">Wenn das **mixedrealitytoolkit** -Objekt im Fenster Hierarchie ausgewählt ist, ändern Sie im Inspektor-Fenster das Mixed Reality Toolkit- **Konfigurations Profil** in **DefaultHoloLens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="19b52-131">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, change the Mixed Reality Toolkit **Configuration Profile** to **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

<span data-ttu-id="19b52-133">Wenn das **mixedrealitytoolkit** -Objekt noch ausgewählt ist, klicken Sie im Inspektor-Fenster auf die Schaltfläche zum **Kopieren & anpassen** , um das Fenster Klon Profil zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="19b52-133">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

<span data-ttu-id="19b52-135">Klicken Sie im Fenster Klon Profil auf die Schaltfläche **Klonen** , um eine bearbeitbare Kopie des **DefaultHololens2ConfigurationProfile**zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="19b52-135">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

<span data-ttu-id="19b52-137">Das neu erstellte Konfigurations Profil ist nun als Konfigurations Profil für Ihre Szene zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="19b52-137">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

<span data-ttu-id="19b52-139">Wählen Sie im Unity-Menü **Datei** > **Speichern** aus, um die Szene zu speichern.</span><span class="sxs-lookup"><span data-stu-id="19b52-139">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="19b52-140">Denken Sie daran, ihre Arbeit im gesamten Tutorial zu speichern.</span><span class="sxs-lookup"><span data-stu-id="19b52-140">Remember to save your work throughout the tutorial.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="19b52-141">2. Aktivieren des Systems für räumliche Informationen</span><span class="sxs-lookup"><span data-stu-id="19b52-141">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="19b52-142">Wenn das **mixedrealitytoolkit** -Objekt noch im Fenster Hierarchie ausgewählt ist, wählen Sie im Inspektor-Fenster die Registerkarte **räumliches Bewusstsein** aus, und aktivieren Sie dann das Kontrollkästchen **räumliches Awareness System aktivieren** :</span><span class="sxs-lookup"><span data-stu-id="19b52-142">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="19b52-144">3. Klonen des standardmäßigen Spatial Awareness System-Profils</span><span class="sxs-lookup"><span data-stu-id="19b52-144">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="19b52-145">Klicken Sie auf der Registerkarte **räumliches Bewusstsein** auf die Schaltfläche **Klonen** , um das Fenster Klon Profil zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="19b52-145">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

<span data-ttu-id="19b52-147">Klicken Sie im Fenster Klon Profil auf die Schaltfläche **Klonen** , um eine bearbeitbare Kopie von **defaultmixedrealityspatialawarenesssystemprofile**zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="19b52-147">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

<span data-ttu-id="19b52-149">Das neu erstellte Spatial Awareness System-Profil wird nun automatisch Ihrem Konfigurations Profil zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="19b52-149">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="19b52-151">4. Klonen Sie das standardmäßige räumliche Awareness Mesh Observer-Profil.</span><span class="sxs-lookup"><span data-stu-id="19b52-151">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="19b52-152">Wenn die Registerkarte **räumliches Bewusstsein** weiterhin ausgewählt ist, erweitern Sie den Abschnitt **Windows Mixed Reality Spatial Mesh Observer** , und klicken Sie dann auf die Schaltfläche **Klonen** , um das Fenster Klon Profil zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="19b52-152">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

<span data-ttu-id="19b52-154">Klicken Sie im Fenster Klon Profil auf die Schaltfläche **Klonen** , um eine bearbeitbare Kopie von **defaultmixedrealityspatialawareness meshobserverprofile**zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="19b52-154">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

<span data-ttu-id="19b52-156">Das neu erstellte Spatial Awareness Mesh-Profil wird nun automatisch Ihrem Spatial Awareness System-Profil zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="19b52-156">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="19b52-158">5. Ändern der Sichtbarkeit des Netzes für räumliche Informationen</span><span class="sxs-lookup"><span data-stu-id="19b52-158">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="19b52-159">Ändern Sie in den **Einstellungen für räumliche Gitter Beobachter**die **Anzeige Option** in " **oksion** ", damit das räumliche Zuordnungs Netz unsichtbar bleibt, während es funktionsfähig ist:</span><span class="sxs-lookup"><span data-stu-id="19b52-159">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still being functional:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="19b52-161">Obwohl das Mesh für räumliche Zuordnung nicht sichtbar ist, ist es immer noch vorhanden und funktionsfähig.</span><span class="sxs-lookup"><span data-stu-id="19b52-161">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="19b52-162">Beispielsweise werden alle holograms hinter dem räumlichen zuordnungsmesh, z. b. ein Hologramm hinter einer physischen Wand, nicht sichtbar.</span><span class="sxs-lookup"><span data-stu-id="19b52-162">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="19b52-163">Sie haben soeben erfahren, wie Sie eine Einstellung im MRTK-Profil ändern können.</span><span class="sxs-lookup"><span data-stu-id="19b52-163">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="19b52-164">Wie Sie sehen können, müssen Sie zunächst Kopien der Standardprofile erstellen, um die mrtk-Einstellungen anzupassen.</span><span class="sxs-lookup"><span data-stu-id="19b52-164">As you can see, in order to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="19b52-165">Da die Standardprofile nicht bearbeitbar sind, haben Sie Sie immer als Verweis, wenn Sie die Standardeinstellungen wiederherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="19b52-165">Because the default profiles are not editable, you will always have them as reference if you want revert back to the default settings.</span></span> <span data-ttu-id="19b52-166">Weitere Informationen zu mrtk-Profilen und deren Architektur finden Sie im Handbuch für die [Konfiguration des Mixed Reality Toolkit-Profils](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) im [mrtk-Dokumentations Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="19b52-166">To learn more about MRTK profiles and their architecture, you can visit the [Mixed Reality Toolkit profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="19b52-167">Hand Verfolgungs Gesten und austauschbare Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="19b52-167">Hand tracking gestures and interactable buttons</span></span>

<span data-ttu-id="19b52-168">In diesem Abschnitt erfahren Sie, wie Sie mithilfe der Hand Überwachung eine Schaltfläche drücken und Ereignisse auslösen, um eine Aktion auszulösen, wenn die Schaltfläche gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="19b52-168">In this section, you will learn how to use hand tracking to press a button and trigger events to cause an action when the button is pressed.</span></span>

<span data-ttu-id="19b52-169">In diesem speziellen Beispiel wird gezeigt, wie Sie die Farbe eines Cubes ändern, wenn die Schaltfläche gedrückt wird, und die Farbe zurück in die ursprüngliche Farbe ändern, wenn die Schaltfläche losgelassen wird.</span><span class="sxs-lookup"><span data-stu-id="19b52-169">This particular example will show you how to change the color of a cube when the button is pressed and change it back to it's original color when the button is released.</span></span> <span data-ttu-id="19b52-170">Sie können jedoch dieselben Prinzipien befolgen, um andere Ereignisse zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="19b52-170">However, you may follow these same principles to create other events.</span></span>

<span data-ttu-id="19b52-171">Die wichtigsten Schritte, die Sie ausführen müssen, um die Farbe des Cubes zu ändern, sind:</span><span class="sxs-lookup"><span data-stu-id="19b52-171">The main steps you will take to change the color of the cube are:</span></span>

1. <span data-ttu-id="19b52-172">Fügen Sie der Szene eine Schaltfläche für die Druck Bare Schaltfläche hinzu.</span><span class="sxs-lookup"><span data-stu-id="19b52-172">Add a pressable button prefab to the scene</span></span>
2. <span data-ttu-id="19b52-173">Hinzufügen eines Cubes zur Szene</span><span class="sxs-lookup"><span data-stu-id="19b52-173">Add a cube to the scene</span></span>
3. <span data-ttu-id="19b52-174">Konfigurieren des interactableonpressreceiver-Ereignis Typs</span><span class="sxs-lookup"><span data-stu-id="19b52-174">Configure the InteractableOnPressReceiver event type</span></span>
4. <span data-ttu-id="19b52-175">Cube so konfigurieren, dass das on Press-Ereignis empfangen wird</span><span class="sxs-lookup"><span data-stu-id="19b52-175">Configure the cube to receive the On Press event</span></span>
5. <span data-ttu-id="19b52-176">Hiermit wird die Aktion definiert, die vom on Press-Ereignis ausgelöst werden soll.</span><span class="sxs-lookup"><span data-stu-id="19b52-176">Define the action to be triggered by the On Press event</span></span>
6. <span data-ttu-id="19b52-177">Konfigurieren des Cubes, um das on-Release-Ereignis zu empfangen</span><span class="sxs-lookup"><span data-stu-id="19b52-177">Configure the cube to receive the On Release event</span></span>
7. <span data-ttu-id="19b52-178">Hiermit wird die Aktion definiert, die vom on-Release-Ereignis ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="19b52-178">Define the action to be triggered by the On Release event</span></span>
8. <span data-ttu-id="19b52-179">Testen der Schaltfläche mithilfe der in-Editor-Simulation</span><span class="sxs-lookup"><span data-stu-id="19b52-179">Test the button using the in-editor simulation</span></span>

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a><span data-ttu-id="19b52-180">1. Fügen Sie der Szene eine Schaltfläche für die Druck Bare Schaltfläche hinzu.</span><span class="sxs-lookup"><span data-stu-id="19b52-180">1. Add a pressable button prefab to the scene</span></span>

> [!TIP]
> <span data-ttu-id="19b52-181">Bei einem <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Prefab</a> handelt es sich um ein vorkonfiguriertes gameobject-Objekt, das als Unity-Medienobjekt gespeichert und im gesamten Projekt wieder verwendet werden kann</span><span class="sxs-lookup"><span data-stu-id="19b52-181">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="19b52-182">Suchen Sie im **Projektfenster**nach **PressableButtonHoloLens2** , um das in diesem Beispiel verwendete präfab zu finden:</span><span class="sxs-lookup"><span data-stu-id="19b52-182">In the **Project window**, search for **PressableButtonHoloLens2** to locate the prefab you will use for this example:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

<span data-ttu-id="19b52-184">Wählen Sie im **Such** Ergebnis **PressableButtonHoloLens2** Prefab aus, und **ziehen** Sie es in das **Hierarchie** Fenster, um es Ihrer Szene hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="19b52-184">In the **Search** result, select the **PressableButtonHoloLens2** prefab and **drag** it into the **Hierarchy** window to add it to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="19b52-186">Zum Anzeigen der Szene, wie in der folgenden Abbildung dargestellt, doppelklicken Sie auf das PressableButtonHoloLens2-Objekt im Hierarchie Fenster, um es in den Fokus zu bringen, und verwenden Sie dann die <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Szene Gizmo</a>in der oberen rechten Ecke des Fensters Szene, um den Anzeige Winkel an der vorwärts-Z-Achse anzupassen.</span><span class="sxs-lookup"><span data-stu-id="19b52-186">To display your scene as shown in the image below, double-click the PressableButtonHoloLens2 object in the Hierarchy window to bring it into focus, then use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis.</span></span>

<span data-ttu-id="19b52-187">Wenn das **PressableButtonHoloLens2** -Objekt noch ausgewählt ist, im **Inspektor** -Fenster:</span><span class="sxs-lookup"><span data-stu-id="19b52-187">With the **PressableButtonHoloLens2** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="19b52-188">Ändern Sie die **Position** der Transformation, sodass Sie vor der Kamera positioniert ist, die am Ursprung positioniert ist, z. b. x = 0, y = 0 und z = 0,5.</span><span class="sxs-lookup"><span data-stu-id="19b52-188">Change its Transform **Position** so it's positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="19b52-190">Im Allgemeinen entspricht eine Positions Einheit in Unity ungefähr 1 Meter in der physischen Welt.</span><span class="sxs-lookup"><span data-stu-id="19b52-190">In general, 1 position unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="19b52-191">Es gibt jedoch Ausnahmen, z. b. wenn Objekte untergeordnete Elemente von skalierten Objekten sind.</span><span class="sxs-lookup"><span data-stu-id="19b52-191">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span>

### <a name="2-add-a-cube-to-the-scene"></a><span data-ttu-id="19b52-192">2. Hinzufügen eines Cubes zur Szene</span><span class="sxs-lookup"><span data-stu-id="19b52-192">2. Add a cube to the scene</span></span>

<span data-ttu-id="19b52-193">Klicken Sie mit der rechten Maustaste auf eine leere Stelle innerhalb des Hierarchie Fensters, und wählen Sie **3D-Objekt** > **Cube** aus, um Ihrer Szene einen Cube hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="19b52-193">Right-click on an empty spot inside the Hierarchy window and select **3D Object** > **Cube** to add a cube to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

<span data-ttu-id="19b52-195">Wenn das **Cube** -Objekt noch ausgewählt ist, im **Inspektor** -Fenster:</span><span class="sxs-lookup"><span data-stu-id="19b52-195">With the **Cube** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="19b52-196">Ändern Sie die Transformations **Position** , sodass Sie sich in der Nähe der druckbaren Schaltfläche befindet, aber nicht mit der Schaltfläche, wie z. b. x = 0, y = 0,04 und z = 0,5.</span><span class="sxs-lookup"><span data-stu-id="19b52-196">Change its Transform **Position** so its located near the pressable button, but not overlapping with it, for example, x = 0, y = 0.04, and z = 0.5</span></span>
* <span data-ttu-id="19b52-197">Ändern Sie die Transformations **Skala** in eine passende Größe, z. b. x = 0,02, y = 0,02 und z = 0,02.</span><span class="sxs-lookup"><span data-stu-id="19b52-197">Change its Transform **Scale** to a suitable size, for example, x = 0.02, y = 0.02, and z = 0.02</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a><span data-ttu-id="19b52-199">3. Konfigurieren des interactableonpressreceiver-Ereignis Typs</span><span class="sxs-lookup"><span data-stu-id="19b52-199">3. Configure the InteractableOnPressReceiver event type</span></span>

<span data-ttu-id="19b52-200">Wählen Sie im Fenster Hierarchie das **PressableButtonHoloLens2** -Objekt aus, und wählen Sie dann im Fenster **Hamburger**des **Inspektorfensters** die Option **alle Komponenten** reduzieren aus, um einen Überblick über alle Komponenten auf diesem Objekt zu erhalten:</span><span class="sxs-lookup"><span data-stu-id="19b52-200">In the Hierarchy window, select the **PressableButtonHoloLens2** object, then in the **Inspector** window **hamburger menu**, select **Collapse All Components** to get an overview of all components on this object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

<span data-ttu-id="19b52-202">Erweitern Sie die Komponente **interactable (Skript)** , suchen Sie den Abschnitt **Ereignisse** > **Empfänger** , und erweitern Sie ihn:</span><span class="sxs-lookup"><span data-stu-id="19b52-202">Expand the **Interactable (Script)** component, then locate and expand the **Events** > **Receivers** section:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

<span data-ttu-id="19b52-204">Klicken Sie auf die Schaltfläche **Ereignis hinzufügen** , um einen neuen Ereignis Empfänger vom Ereignis Empfängertyp **interactableonpressreceiver**zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="19b52-204">Click the **Add Event** button, to create a new event receiver of Event Receiver Type **InteractableOnPressReceiver**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> <span data-ttu-id="19b52-206">Der ereignisempfängertyp mit dem Namen interactableonpressreceiver ermöglicht der Schaltfläche, auf ein gedrücktes Ereignis zu reagieren, wenn eine nach verfolgte Seite die Schaltfläche drückt</span><span class="sxs-lookup"><span data-stu-id="19b52-206">The Event Receiver Type named InteractableOnPressReceiver allows the button to respond to a pressed event when a tracked hand presses the button.</span></span>

<span data-ttu-id="19b52-207">Ändern Sie für den neu erstellten Ereignis Empfänger den **Interaktions Filter** in **Near und Far**:</span><span class="sxs-lookup"><span data-stu-id="19b52-207">For the newly created event receiver, change the **Interaction Filter** to **Near and Far**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a><span data-ttu-id="19b52-209">4. Konfigurieren Sie den Cube, um das on Press-Ereignis zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="19b52-209">4. Configure the cube to receive the On Press event</span></span>

<span data-ttu-id="19b52-210">Klicken Sie im Fenster Hierarchie auf den **Cube** , **und ziehen Sie** ihn in das Feld **Ereignis Eigenschaften** Objekt für das **on Press ()** -Ereignis, um den Cube als Empfänger des on Press ()-Ereignisses zuzuweisen:</span><span class="sxs-lookup"><span data-stu-id="19b52-210">From the Hierarchy window, **click-and-drag** the **Cube** into the **Event Properties** object field for the **On Press ()** event to assign the Cube as a receiver of the On Press () event:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a><span data-ttu-id="19b52-212">5. definieren Sie die Aktion, die vom on Press-Ereignis ausgelöst werden soll.</span><span class="sxs-lookup"><span data-stu-id="19b52-212">5. Define the action to be triggered by the On Press event</span></span>

<span data-ttu-id="19b52-213">Klicken Sie auf die Dropdown Liste Aktion, die zurzeit **keine Funktion**zugewiesen ist, und wählen Sie **meshrenderer** > **Material Material** aus, um festzulegen, dass die Eigenschaft des Cubes geändert wird, wenn das on Press ()-Ereignis ausgelöst wird:</span><span class="sxs-lookup"><span data-stu-id="19b52-213">Click the action dropdown, currently assigned **No Function**, and select **MeshRenderer** > **Material material** to set the Cube's material property to be changed when the On Press () event is triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

<span data-ttu-id="19b52-215">Klicken Sie auf das kleine **Kreis** Symbol neben dem Feld Material, das zurzeit mit **keine (Material)** aufgefüllt ist, um das Fenstermaterial auswählen zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="19b52-215">Click the small **circle** icon next to the material field, currently populated with **None (Material)**, to open the Select Material window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

<span data-ttu-id="19b52-217">**Suchen** Sie im Fenster Material auswählen nach **MRTK_Standard** , und wählen Sie ein geeignetes Material aus, z. b. **MRTK_Standard_Cyan** , damit die Farbe des Cubes in Zyan geändert wird, wenn die Schaltfläche gedrückt wird:</span><span class="sxs-lookup"><span data-stu-id="19b52-217">In the Select Material window, **search** for **MRTK_Standard** and select a suitable material, for example, **MRTK_Standard_Cyan** so the Cube's color changes to cyan when the button is pressed:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a><span data-ttu-id="19b52-219">6. Konfigurieren Sie den Cube für den Empfang des on-Release-Ereignisses.</span><span class="sxs-lookup"><span data-stu-id="19b52-219">6. Configure the cube to receive the On Release event</span></span>

<span data-ttu-id="19b52-220">**Wiederholen** Schritt 4 für das on-Release-Ereignis, um den **Cube** als Empfänger des **on-Release ()** -Ereignisses zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="19b52-220">**Repeat** Step 4 for the On Release event to assign the **Cube** as a receiver of the **On Release ()** event.</span></span>

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a><span data-ttu-id="19b52-221">7. definieren Sie die Aktion, die vom on-Release-Ereignis ausgelöst werden soll.</span><span class="sxs-lookup"><span data-stu-id="19b52-221">7. Define the action to be triggered by the On Release event</span></span>

<span data-ttu-id="19b52-222">**Wiederholen** Schritt 5 für das on-Release-Ereignis, aber wählen Sie das **MRTK_Standard_LightGray** Material aus, damit die Farbe des Cubes bei der Freigabe der Schaltfläche in die ursprüngliche helle graue Farbe zurückkehrt:</span><span class="sxs-lookup"><span data-stu-id="19b52-222">**Repeat** Step 5 for the On Release event, but choose the **MRTK_Standard_LightGray** material so the Cube's color returns to its original light gray color when the button is released:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a><span data-ttu-id="19b52-224">8. Testen der Schaltfläche mithilfe der in-Editor-Simulation</span><span class="sxs-lookup"><span data-stu-id="19b52-224">8. Test the button using the in-editor simulation</span></span>

<span data-ttu-id="19b52-225">Klicken Sie auf die **Wiedergabe** Schaltfläche, um den Spielmodus einzugeben, und testen Sie die neu konfigurierte Schaltfläche mit der Eingabe Simulation im Editor.</span><span class="sxs-lookup"><span data-stu-id="19b52-225">Press the **Play** button to enter Game mode and use the in-editor input simulation to test your newly configured button.</span></span>

<span data-ttu-id="19b52-226">Schaltfläche nicht gedrückt (Leertaste + Mausrad rückwärts):</span><span class="sxs-lookup"><span data-stu-id="19b52-226">Button not pressed (spacebar + mouse scroll wheel backward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

<span data-ttu-id="19b52-228">Gedrückte Schaltfläche (Leertaste + Mausrad nach oben):</span><span class="sxs-lookup"><span data-stu-id="19b52-228">Button pressed (spacebar + mouse scroll wheel forward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> <span data-ttu-id="19b52-230">Weitere Informationen zur Verwendung der in-Editor-Eingabe Simulation finden Sie unter [Verwenden der in-Editor-Hand Eingabe Simulation zum Testen eines Szenen](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) Handbuchs im [mrtk-Dokumentations Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="19b52-230">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="19b52-231">Erstellen eines Schaltflächenbereichs mit der MRTK-Rasterobjektsammlung</span><span class="sxs-lookup"><span data-stu-id="19b52-231">Creating a panel of buttons using MRTK’s Grid Object Collection</span></span>

<span data-ttu-id="19b52-232">In diesem Abschnitt erfahren Sie, wie Sie mehrere Schaltflächen mithilfe des Raster Objekt Auflistungs Tools von mrtk automatisch an einer Benutzeroberfläche anpassen.</span><span class="sxs-lookup"><span data-stu-id="19b52-232">In this section, you will learn how to automatically align multiple buttons into a neat user interface by using the MRTK’s Grid Object Collection tool.</span></span>

<span data-ttu-id="19b52-233">In diesem speziellen Beispiel wird gezeigt, wie ein Panel mit fünf Schaltflächen, die horizontal ausgerichtet sind, erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="19b52-233">This particular example will show you how to a create a panel with five buttons aligned horizontally.</span></span> <span data-ttu-id="19b52-234">Sie können jedoch dieselben Prinzipien befolgen, um andere Layouts zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="19b52-234">However, you may follow these same principles to create other layouts.</span></span>

<span data-ttu-id="19b52-235">Dies sind die wichtigsten Schritte, die Sie durchführen müssen:</span><span class="sxs-lookup"><span data-stu-id="19b52-235">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="19b52-236">Übergeordnete Schaltflächen Objekte zu einem übergeordneten Objekt</span><span class="sxs-lookup"><span data-stu-id="19b52-236">Parent the button objects to a parent object</span></span>
2. <span data-ttu-id="19b52-237">Hinzufügen und Konfigurieren der Komponente "Raster Objekt Auflistung (Skript)"</span><span class="sxs-lookup"><span data-stu-id="19b52-237">Add and configure the Grid Object Collection (Script) component</span></span>
3. <span data-ttu-id="19b52-238">Testen der Schaltflächen mithilfe der in-Editor-Simulation</span><span class="sxs-lookup"><span data-stu-id="19b52-238">Test the buttons using the in-editor simulation</span></span>

### <a name="1-parent-the-button-objects-to-a-parent-object"></a><span data-ttu-id="19b52-239">1. übergeordnete Schaltflächen Objekte zu einem übergeordneten Objekt</span><span class="sxs-lookup"><span data-stu-id="19b52-239">1. Parent the button objects to a parent object</span></span>

<span data-ttu-id="19b52-240">Klicken Sie im Hierarchie Fenster mit der rechten Maustaste auf eine leere Stelle, und wählen Sie **leere erstellen**aus:</span><span class="sxs-lookup"><span data-stu-id="19b52-240">Right-click on an empty spot inside the Hierarchy window and select **Create Empty**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

<span data-ttu-id="19b52-242">Klicken Sie mit der rechten Maustaste auf das neu erstellte Objekt, wählen Sie **Umbenennen**aus, und geben Sie ihm einen passenden Namen, z. b. **buttoncollection**:</span><span class="sxs-lookup"><span data-stu-id="19b52-242">Right-click on the newly created object, select **Rename**, and give it a suitable name, for example, **ButtonCollection**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

<span data-ttu-id="19b52-244">Wählen Sie das **PressableButtonHoloLens2** -Objekt aus, und **ziehen** Sie es über das **buttoncollection** -Objekt, um es zu einem untergeordneten Element des buttoncollection-Objekts zu machen:</span><span class="sxs-lookup"><span data-stu-id="19b52-244">Select the **PressableButtonHoloLens2** object and **drag** it on top of the **ButtonCollection** object to make it a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

<span data-ttu-id="19b52-246">Klicken Sie mit der rechten Maustaste auf das **PressableButtonHoloLens2** -Objekt, und wählen Sie **Duplizieren** aus, um eine Kopie der</span><span class="sxs-lookup"><span data-stu-id="19b52-246">Right-click the **PressableButtonHoloLens2** object and select **Duplicate** to create a copy of it:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

<span data-ttu-id="19b52-248">**Wiederholen** Sie diesen Schritt vier weitere Male, bis Sie über insgesamt fünf PressableButtonHoloLens2-Objekte verfügen.</span><span class="sxs-lookup"><span data-stu-id="19b52-248">**Repeat** this step four more times until you have a total of five PressableButtonHoloLens2 objects.</span></span>

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="19b52-249">2. hinzufügen und Konfigurieren der Raster Objekt-Sammlungs Komponente (Skript)</span><span class="sxs-lookup"><span data-stu-id="19b52-249">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="19b52-250">Wenn das buttoncollection-Objekt im Fenster Hierarchie ausgewählt ist, klicken Sie im Inspektor-Fenster auf die Schaltfläche **Komponente hinzufügen** , suchen Sie nach der **Raster Objekt** Auflistung, und wählen Sie Sie aus, um dem buttoncollection-Objekt eine Komponente für die Raster Objekt Auflistung (Skript) hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="19b52-250">With the ButtonCollection object selected in the Hierarchy window, in the Inspector window, click the **Add Component** button, then search for and select **Grid Object Collection** to add a Grid Object Collection (Script) component to the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

<span data-ttu-id="19b52-252">Konfigurieren Sie die Raster Objekt Auflistung (Skript) wie folgt:</span><span class="sxs-lookup"><span data-stu-id="19b52-252">Configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="19b52-253">Ändern von **num-Zeilen** in 1, damit alle Schaltflächen auf einer einzelnen Zeile ausgerichtet sind</span><span class="sxs-lookup"><span data-stu-id="19b52-253">Change **Num Rows** to 1 to have all buttons aligned on one single row</span></span>
* <span data-ttu-id="19b52-254">Ändern Sie die **Zellen Breite** in 0,05, um die Schaltflächen innerhalb der Zeile leer zu setzen.</span><span class="sxs-lookup"><span data-stu-id="19b52-254">Change **Cell Width** to 0.05 to space out the buttons within the row</span></span>

<span data-ttu-id="19b52-255">Klicken Sie dann auf die Schaltfläche **Sammlung aktualisieren** , um die neue Konfiguration zu übernehmen:</span><span class="sxs-lookup"><span data-stu-id="19b52-255">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> <span data-ttu-id="19b52-257">Die soeben angewendeten Konfigurationsänderungen stellen die minimalen Änderungen dar, die erforderlich sind, um das Ziel zu erreichen, die Schaltflächen in einer einzelnen Zeile zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="19b52-257">The configuration changes you just applied represent the minimum changes required to achieve the objective of placing the buttons in a single row.</span></span> <span data-ttu-id="19b52-258">Allerdings müssen Sie in zukünftigen Projekten, abhängig von Faktoren wie z. b. der Ausrichtung der über-und untergeordneten Objekte, möglicherweise andere Einstellungen anpassen, z. b. den Typ "Typ".</span><span class="sxs-lookup"><span data-stu-id="19b52-258">However, in future projects, depending on factors such as, for example, the orientation of the parent and child objects, you might need to adjust other settings such as, for example, the Orient Type.</span></span> <span data-ttu-id="19b52-259">Weitere Informationen zur Raster Objekt Auflistung von mrtk finden Sie im Handbuch zur [Erfassung von Objekt](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) Auflistungen im [mrtk-Dokumentations Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="19b52-259">To learn more about MRTK's Grid Object Collection, you can visit the [Object collection scripts](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

<span data-ttu-id="19b52-260">Wenn das buttoncollection-Objekt noch im Fenster Hierarchie ausgewählt ist, ändern Sie im Inspektor-Fenster die Transformations **Position** des buttoncollection-Objekts, sodass die untergeordneten Schaltflächen Objekte vor der Kamera positioniert werden, die am Ursprung positioniert ist, z. b. x = 0, y = 0 und z = 0,5:</span><span class="sxs-lookup"><span data-stu-id="19b52-260">With the ButtonCollection object still selected in the Hierarchy window, in the Inspector window, change the ButtonCollection object's Transform **Position** so its child button objects are positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> <span data-ttu-id="19b52-262">Beim ersten Hinzufügen von PressableButtonHoloLens2 Prefab zur Szene im obigen Abschnitt [Hand Tracking Gesten und Interaktionen Buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) positionierte Sie diese vor der Kamera.</span><span class="sxs-lookup"><span data-stu-id="19b52-262">When you first added the PressableButtonHoloLens2 prefab to the scene in the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) section above, you positioned it in front of the camera.</span></span> <span data-ttu-id="19b52-263">Da die Raster Objekt Auflistung jedoch die Position der unmittelbaren untergeordneten Objekte steuert, wurden die Z-Position der untergeordneten Objekte PressableButtonHoloLens2 entsprechend der Standard Entfernung der Raster Objekt Auflistung vom übergeordneten Wert 0 auf 0 zurückgesetzt.</span><span class="sxs-lookup"><span data-stu-id="19b52-263">However, because the Grid Object Collection controls its immediate child objects' position, the PressableButtonHoloLens2 child objects' Z Position were reset to 0 according to the Grid Object Collection's default Distance from parent value of 0.</span></span> <span data-ttu-id="19b52-264">Und damit die Beziehungen zwischen übergeordneten und untergeordneten Elementen organisiert bleiben, wird die Position des übergeordneten buttoncollection-Objekts verschoben, anstatt den Abstand vom übergeordneten Wert zu konfigurieren, um die untergeordneten PressableButtonHoloLens2-Objekte vorwärts zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="19b52-264">This, and to keep the parent/child positional relationship organized, is why we moved the parent ButtonCollection object's position forward instead of configuring the Distance from parent value to move the PressableButtonHoloLens2 child objects forward.</span></span>

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a><span data-ttu-id="19b52-265">3. Testen der Schaltflächen mithilfe der in-Editor-Simulation</span><span class="sxs-lookup"><span data-stu-id="19b52-265">3. Test the buttons using the in-editor simulation</span></span>

<span data-ttu-id="19b52-266">Klicken Sie auf die Wiedergabe Schaltfläche, um den Spielmodus einzugeben, und verwenden Sie die Eingabe Simulation im Editor, um die einzelnen Schaltflächen in dem neu erstellten Panel von Schaltflächen zu testen:</span><span class="sxs-lookup"><span data-stu-id="19b52-266">Press the Play button to enter Game mode and use the in-editor input simulation to test each of the buttons in in your newly created panel of buttons:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> <span data-ttu-id="19b52-268">Wenn Sie derzeit eine der fünf Schaltflächen drücken, wird die Würfel Farbe in Cyan geändert.</span><span class="sxs-lookup"><span data-stu-id="19b52-268">Currently, when your press any of the five buttons, the cube color changes to cyan.</span></span> <span data-ttu-id="19b52-269">Um die Darstellung interessanter zu gestalten, verwenden Sie das, was Sie gerade lernen, um die einzelnen Schaltflächen zu konfigurieren, um den Cube in eine andere Farbe zu ändern.</span><span class="sxs-lookup"><span data-stu-id="19b52-269">To make the experience more interesting, use what you just learn to configure each button to change the cube to a different color.</span></span>

## <a name="adding-text-into-your-scene"></a><span data-ttu-id="19b52-270">Hinzufügen von Text in Ihrer Szene</span><span class="sxs-lookup"><span data-stu-id="19b52-270">Adding text into your scene</span></span>

<span data-ttu-id="19b52-271">In diesem Abschnitt erfahren Sie, wie Sie mithilfe von "textmesh pro", die Sie im Abschnitt " [Importieren von textmesh pro Essentials Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) " im vorherigen Tutorial vorbereitet haben, Text zu ihren Mixed Reality-Umgebungen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="19b52-271">In this section, you will learn how to add text to your mixed reality experiences using Unity's TextMesh Pro, which you prepared in the [Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) section of the previous tutorial.</span></span>

<span data-ttu-id="19b52-272">In diesem speziellen Beispiel fügen Sie unterhalb der Schaltflächen Auflistung, die Sie im vorherigen Abschnitt erstellt haben, eine einfache Bezeichnung hinzu.</span><span class="sxs-lookup"><span data-stu-id="19b52-272">In this particular example, you will add a simple label underneath the button collection you created in the previous section.</span></span>

<span data-ttu-id="19b52-273">Klicken Sie mit der rechten Maustaste auf das buttoncollection-Objekt, und wählen Sie **3D-Objekt** > **Text-textmeshpro** aus, um ein textmeschpro-Objekt als untergeordnetes Element des buttoncollection-Objekts zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="19b52-273">Right-click on the ButtonCollection object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro object as a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

<span data-ttu-id="19b52-275">Wenn das neu erstellte textmeshpro-Objekt, benannter Text (tmp), noch ausgewählt ist, ändern Sie im Inspektor-Fenster seine Position und Größe so, dass die Bezeichnung sauber unterhalb der Schaltflächen Auflistung platziert wird, z. b.:</span><span class="sxs-lookup"><span data-stu-id="19b52-275">With the newly created TextMeshPro object, named Text (TMP), still selected, in the Inspector window change its position and size so the label is placed neatly underneath the button collection, for example:</span></span>

* <span data-ttu-id="19b52-276">Ändern der Rect-Transformation **Torys Y** in-0,0425</span><span class="sxs-lookup"><span data-stu-id="19b52-276">Change the Rect Transform **Pos Y** to -0.0425</span></span>
* <span data-ttu-id="19b52-277">Ändern Sie die **Breite** der Rect-Transformation in 0,24.</span><span class="sxs-lookup"><span data-stu-id="19b52-277">Change the Rect Transform **Width** to 0.24</span></span>
* <span data-ttu-id="19b52-278">Ändern Sie die **Höhe** der Rect-Transformation in 0,024.</span><span class="sxs-lookup"><span data-stu-id="19b52-278">Change the Rect Transform **Height** to 0.024</span></span>

<span data-ttu-id="19b52-279">Aktualisieren Sie dann den Text, um die Bezeichnung der Bezeichnung widerzuspiegeln, und wählen Sie Schriftart Eigenschaften aus, damit der Text in die Bezeichnung passt, z. b.:</span><span class="sxs-lookup"><span data-stu-id="19b52-279">Then update the text to reflect what the label is for and choose font properties so the text fits within the label, for example:</span></span>

* <span data-ttu-id="19b52-280">Textmesh pro- **Text** (Skript) in Schaltflächen Auflistung ändern</span><span class="sxs-lookup"><span data-stu-id="19b52-280">Change the Text Mesh Pro (Script) **Text** to Button Collection</span></span>
* <span data-ttu-id="19b52-281">Ändern Sie den Text Mesh pro- **Schrift** Schnitt (Skript) in "Fett".</span><span class="sxs-lookup"><span data-stu-id="19b52-281">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="19b52-282">Ändern Sie den **Schrift** Grad Text Mesh pro (Skript) in 0,2.</span><span class="sxs-lookup"><span data-stu-id="19b52-282">Change the Text Mesh Pro (Script) **Font Size** to 0.2</span></span>
* <span data-ttu-id="19b52-283">Ändern der **Ausrichtung** von Text Mesh pro (Skript) in Mitte und Mitte</span><span class="sxs-lookup"><span data-stu-id="19b52-283">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="19b52-285">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="19b52-285">Congratulations</span></span>

<span data-ttu-id="19b52-286">In diesem Tutorial haben Sie erfahren, wie Sie eine mrtk-Profileinstellung Klonen, anpassen und konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="19b52-286">In this tutorial, you learned how to clone, customize, and configure an MRTK profile setting.</span></span> <span data-ttu-id="19b52-287">Außerdem haben Sie erfahren, wie Sie mit Schaltflächen interagieren, um Ereignisse mithilfe von nach verfolgten Händen in den hololens 2 zu Triggern 2</span><span class="sxs-lookup"><span data-stu-id="19b52-287">You also learned how to interact with buttons to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="19b52-288">Schließlich haben Sie erfahren, wie Sie eine einfache UI-Schnittstelle mithilfe der Raster Objekt Auflistungs Komponente von mrtk und des Text Mesh pro von Unity erstellen.</span><span class="sxs-lookup"><span data-stu-id="19b52-288">Finally, you learned how to create a simple UI interface using the MRTK's Grid Object Collection component and Unity's Text Mesh Pro.</span></span>

[<span data-ttu-id="19b52-289">Nächstes Tutorial: 4. Platzieren von dynamischem Inhalt und Verwenden von Solvers</span><span class="sxs-lookup"><span data-stu-id="19b52-289">Next Tutorial: 4. Placing dynamic content and using solvers</span></span>](mrlearning-base-ch3.md)
