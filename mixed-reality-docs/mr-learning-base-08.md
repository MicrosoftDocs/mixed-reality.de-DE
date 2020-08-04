---
title: 'Tutorials zu den ersten Schritten: 8. Verwenden von Eye Tracking'
description: In diesem Kurs erfahren Sie, wie Sie das Mixed Reality Toolkit (MRTK) verwenden, um eine Mixed Reality-Anwendung zu erstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 31552cba9a68d1f1214395dbf4e4ed84ecd3f388
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376602"
---
# <a name="8-using-eye-tracking"></a><span data-ttu-id="b0515-105">8. Verwenden von Eye Tracking</span><span class="sxs-lookup"><span data-stu-id="b0515-105">8. Using eye-tracking</span></span>

## <a name="overview"></a><span data-ttu-id="b0515-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="b0515-106">Overview</span></span>

<span data-ttu-id="b0515-107">In diesem Tutorial erfahren Sie, wie Sie Eye Tracking für HoloLens 2 aktivieren und Objekten Eye Tracking hinzufügen, um Aktionen auszulösen, wenn der Benutzer die Objekte ansieht.</span><span class="sxs-lookup"><span data-stu-id="b0515-107">In this tutorial, you will learn how to enable eye-tracking for HoloLens 2 and add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!NOTE]
> <span data-ttu-id="b0515-108">Wenn Sie dieses Projekt auch in HoloLens (1. Generation) bereitstellen, beachten Sie, dass Eye Tracking nur in HoloLens 2 unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="b0515-108">If you are also deploying this project to HoloLens (1st generation), note that eye-tracking is only supported on HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="b0515-109">Ziele</span><span class="sxs-lookup"><span data-stu-id="b0515-109">Objectives</span></span>

* <span data-ttu-id="b0515-110">Erfahren, wie Eye Tracking für HoloLens 2 aktiviert wird</span><span class="sxs-lookup"><span data-stu-id="b0515-110">Learn how to enable eye-tracking for HoleLens 2</span></span>
* <span data-ttu-id="b0515-111">Erfahren, wie Eye Tracking zum Auslösen von Aktionen verwendet wird</span><span class="sxs-lookup"><span data-stu-id="b0515-111">Learn how to use eye-tracking to trigger action</span></span>

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="b0515-112">Sicherstellen, dass die Eingabe durch Anvisieren mit den Augen aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="b0515-112">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="b0515-113">Wählen Sie im Unity-Menü „Mixed Reality Toolkit > Utilities > **Configure Unity Project**“ (Mixed Reality Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) aus, um das Fenster **MRTK Project Configurator** (MRTK-Projektkonfigurator) zu öffnen, und überprüfen Sie dann im Abschnitt **UWP Capabilities** (UWP-Funktionen), ob die Funktion **Enable Eye Gaze Input** (Eingabe durch Anvisieren mit den Augen) grau dargestellt wird:</span><span class="sxs-lookup"><span data-stu-id="b0515-113">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="b0515-115">Die Funktion zur Eingabe durch Anvisieren hätte im Rahmen der Anweisungen zum [Übernehmen der Einstellungen des MRTK-Projektkonfigurators](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) aktiviert werden sollen, während der ursprünglichen Konfiguration des Unity-Projekts zu Beginn dieser Tutorialreihe.</span><span class="sxs-lookup"><span data-stu-id="b0515-115">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="b0515-116">Sollte sie nicht aktiviert sein, achten Sie darauf, sie jetzt zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="b0515-116">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="b0515-117">Aktivieren des Anvisierens mit den Augen im Blickanbieter</span><span class="sxs-lookup"><span data-stu-id="b0515-117">Enabling eye based gaze in the gaze provider</span></span>

<span data-ttu-id="b0515-118">Wählen Sie im Hierarchiefenster das Objekt **MixedRealityToolkit** aus, wählen Sie dann im Inspektorfenster die Registerkarte „MixedRealityToolkit > **Input**“ aus, und führen Sie die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="b0515-118">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="b0515-119">Klonen Sie das Profil **DefaultHoloLens2InputSystemProfile**, und geben Sie ihm einen passenden Namen, beispielsweise _GettingStarted_HoloLens2InputSystemProfile_</span><span class="sxs-lookup"><span data-stu-id="b0515-119">Clone the **DefaultHoloLens2InputSystemProfile** and give it a suitable name, for example, _GettingStarted_HoloLens2InputSystemProfile_</span></span>
* <span data-ttu-id="b0515-120">Erweitern Sie den Abschnitt **Pointers** (Zeiger)</span><span class="sxs-lookup"><span data-stu-id="b0515-120">Expand the **Pointers** section</span></span>
* <span data-ttu-id="b0515-121">Klonen Sie das Profil **DefaultMixedRealityPointerProfile**, und geben Sie ihm einen passenden Namen, beispielsweise _GettingStarted_MixedRealityPointerProfile_</span><span class="sxs-lookup"><span data-stu-id="b0515-121">Clone the **DefaultMixedRealityPointerProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityPointerProfile_</span></span>
* <span data-ttu-id="b0515-122">Suchen Sie den Abschnitt **Gaze Settings** (Blickeinstellungen), und aktivieren Sie das Kontrollkästchen **Is Eye Tracking Enabled** (Ist Eye Tracking aktiviert)</span><span class="sxs-lookup"><span data-stu-id="b0515-122">Locate the **Gaze Settings** section and check the **Is Eye Tracking Enabled** checkbox</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="b0515-124">Wenn Sie eine Auffrischung zum Klonen von MRTK-Profilen benötigen, lesen Sie die Anweisungen in [Konfigurieren der MRTK-Profile](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="b0515-124">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a><span data-ttu-id="b0515-125">Aktivieren von simuliertem Eye Tracking für den Unity-Editor</span><span class="sxs-lookup"><span data-stu-id="b0515-125">Enabling simulated eye-tracking for the Unity editor</span></span>

<span data-ttu-id="b0515-126">Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt aus, und navigieren Sie dann im Inspektorfenster zur Registerkarte **Input** (Eingabe). Führen Sie dann Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="b0515-126">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, navigate to the **Input** tab, then:</span></span>

* <span data-ttu-id="b0515-127">Klappen Sie den Abschnitt **Input Data Providers** > **Input Simulation Service** (Eingabedatenanbieter > Eingabesimulationsdienst) auf</span><span class="sxs-lookup"><span data-stu-id="b0515-127">Expand the **Input Data Providers** > **Input Simulation Service** section</span></span>
* <span data-ttu-id="b0515-128">Klonen Sie das Profil **DefaultMixedRealityInputSimulationProfile**, und geben Sie ihm einen passenden Namen, beispielsweise _GettingStarted_MixedRealityInputSimulationProfile_</span><span class="sxs-lookup"><span data-stu-id="b0515-128">Clone the **DefaultMixedRealityInputSimulationProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityInputSimulationProfile_</span></span>
* <span data-ttu-id="b0515-129">Suchen Sie den Abschnitt **Eye Simulation** (Augensimulation), und aktivieren Sie das Kontrollkästchen **Simulate Eye Position** (Augenposition simulieren)</span><span class="sxs-lookup"><span data-stu-id="b0515-129">Locate the **Eye Simulation** section and check the **Simulate Eye Position** checkbox</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a><span data-ttu-id="b0515-131">Hinzufügen von Eye Tracking zu Objekten</span><span class="sxs-lookup"><span data-stu-id="b0515-131">Adding eye-tracking to objects</span></span>

<span data-ttu-id="b0515-132">Klappen Sie im Hierarchiefenster das Objekt „RoverExplorer > **Buttons**“ (RoverExplorer > Schaltflächen) auf, klappen Sie dann für jedes der drei untergeordneten Schaltflächenobjekte das Objekt „SeeItSayItLabel > **TextMeshPro**“ auf, und wählen Sie es aus:</span><span class="sxs-lookup"><span data-stu-id="b0515-132">In the Hierarchy window, expand the RoverExplorer > **Buttons** object, then for each of the three child button objects, expand and select the SeeItSayItLabel > **TextMeshPro** object:</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-1.png)

<span data-ttu-id="b0515-134">Verwenden Sie, während die drei TextMeshPro-Objekte noch ausgewählt sind, im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um allen ausgewählten Objekten die folgenden Komponenten hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="b0515-134">With the three TextMeshPro objects still selected, in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="b0515-135">**Box Collider**-Komponente</span><span class="sxs-lookup"><span data-stu-id="b0515-135">**Box Collider** component</span></span>
* <span data-ttu-id="b0515-136">**EyeTrackingTarget**-Komponente</span><span class="sxs-lookup"><span data-stu-id="b0515-136">**EyeTrackingTarget** component</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-2.png)

<span data-ttu-id="b0515-138">Wählen Sie im Hierarchiefenster das Objekt **Hints** > SeeItSayItLabel > **TextMeshPro** (Hinweise > SeeItSayItLabel > TextMeshPro) aus, und konfigurieren Sie dann die **EyeTrackingTarget**-Komponente wie folgt:</span><span class="sxs-lookup"><span data-stu-id="b0515-138">In the Hierarchy window, select the **Hints** > SeeItSayItLabel > **TextMeshPro** object, then configure the **EyeTrackingTarget** component as follows:</span></span>

* <span data-ttu-id="b0515-139">Im Ereignisabschnitt **On Look At Start ()**</span><span class="sxs-lookup"><span data-stu-id="b0515-139">In the **On Look At Start ()** event section</span></span>
  * <span data-ttu-id="b0515-140">Klicken Sie auf das kleine **+** -Symbol, um ein weiteres Ereignis hinzuzufügen</span><span class="sxs-lookup"><span data-stu-id="b0515-140">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="b0515-141">Weisen Sie das Objekt selbst, d. h. das gleiche **TextMeshPro**-Objekt, dem Feld **None (Object)** (Ohne (Objekt)) zu</span><span class="sxs-lookup"><span data-stu-id="b0515-141">Assign the object itself, i.e. the same **TextMeshPro** object, to the **None (Object)** field</span></span>
  * <span data-ttu-id="b0515-142">Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **TextMeshPro** > **float fontSize** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="b0515-142">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="b0515-143">Legen Sie das Argument auf **0,06** fest, um den aktuellen Schriftgrad von 0,04 um 50 % zu erhöhen</span><span class="sxs-lookup"><span data-stu-id="b0515-143">Set the argument to **0.06** to increase the current font size of 0.04 by 50%</span></span>
* <span data-ttu-id="b0515-144">Im Ereignisabschnitt **On Look Away ()**</span><span class="sxs-lookup"><span data-stu-id="b0515-144">In the **On Look Away ()** event section</span></span>
  * <span data-ttu-id="b0515-145">Klicken Sie auf das kleine **+** -Symbol, um ein weiteres Ereignis hinzuzufügen</span><span class="sxs-lookup"><span data-stu-id="b0515-145">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="b0515-146">Weisen Sie das Objekt selbst, d. h. das gleiche **TextMeshPro**-Objekt, dem Feld **None (Object)** (Ohne (Objekt)) zu</span><span class="sxs-lookup"><span data-stu-id="b0515-146">Assign the object itself, i.e. the same **TextMeshPro** object, to the **None (Object)** field</span></span>
  * <span data-ttu-id="b0515-147">Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **TextMeshPro** > **float fontSize** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="b0515-147">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="b0515-148">Legen Sie das Argument auf **0,04** fest, um den Schriftgrad wieder auf 0,04 zurückzusetzen</span><span class="sxs-lookup"><span data-stu-id="b0515-148">Set the argument to **0.04** to reset the font size back to 0.04</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-3.png)

<span data-ttu-id="b0515-150">**Wiederholen** Sie diesen Schritt für das Objekt **Explode** > SeeItSayItLabel > **TextMeshPro** (Explodieren > SeeItSayItLabel > TextMeshPro) und das Objekt **Reset** > SeeItSayItLabel > **TextMeshPro** (Zurücksetzen > SeeItSayItLabel > TextMeshPro).</span><span class="sxs-lookup"><span data-stu-id="b0515-150">**Repeat** this step for the **Explode** > SeeItSayItLabel > **TextMeshPro** object and the **Reset** > SeeItSayItLabel > **TextMeshPro** object.</span></span>

<span data-ttu-id="b0515-151">Wenn Sie jetzt in den Spielmodus wechseln, dann die rechte Maustaste drücken und sie gedrückt halten, während Sie die Maus bewegen, bis der Blick auf eine der Bezeichnungen trifft, sehen Sie dass sich der Schriftgrad um 50 % vergrößert und wieder zur normalen Größe zurückkehrt, wenn Sie den Blick abwenden:</span><span class="sxs-lookup"><span data-stu-id="b0515-151">If you now enter Game mode and then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the labels, you will see the font size increase by 50% and reset back to its original size when looking away:</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="b0515-153">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="b0515-153">Congratulations</span></span>

<span data-ttu-id="b0515-154">In diesem Tutorial haben Sie erfahren, wie Sie Eye Tracking für HoloLens 2 aktivieren und Objekten Eye Tracking hinzufügen, um Aktionen auszulösen, wenn der Benutzer die Objekte ansieht.</span><span class="sxs-lookup"><span data-stu-id="b0515-154">In this tutorial, you learned how to enable eye-tracking for HoloLens 2 and how to add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

[<span data-ttu-id="b0515-155">Nächstes Tutorial: 9. Verwenden von Sprachbefehlen</span><span class="sxs-lookup"><span data-stu-id="b0515-155">Next Tutorial: 9. Using speech commands</span></span>](mr-learning-base-09.md)