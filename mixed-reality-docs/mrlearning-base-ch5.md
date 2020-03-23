---
title: 'Tutorials zu den ersten Schritten: 6 Untersuchen erweiterter Eingabeoptionen'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: ec078015304e1cddc9b042fb5e94cf1904a302cb
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376087"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="5c5d7-105">6. Untersuchen erweiterter Eingabeoptionen</span><span class="sxs-lookup"><span data-stu-id="5c5d7-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="5c5d7-106">In diesem Tutorial werden einige erweiterte Eingabeoptionen für HoloLens 2 vorgestellt, z. B. Sprachbefehle, Schwenkgesten und Eyetracking.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-106">In this tutorial, you will explore a few advanced input options for HoloLens 2, including the use of voice commands, panning gesture, and eye tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="5c5d7-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="5c5d7-107">Objectives</span></span>

* <span data-ttu-id="5c5d7-108">Auslösen von Ereignissen mit Sprachbefehlen und Schlüsselwörtern</span><span class="sxs-lookup"><span data-stu-id="5c5d7-108">Trigger events using voice commands and keywords</span></span>
* <span data-ttu-id="5c5d7-109">Verwenden von Handtracking, um mit nachverfolgten Händen Strukturen und 3D-Objekte zu schwenken</span><span class="sxs-lookup"><span data-stu-id="5c5d7-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
* <span data-ttu-id="5c5d7-110">Nutzen der Eyetracking-Funktion von HoloLens 2 zum Auswählen von Objekten</span><span class="sxs-lookup"><span data-stu-id="5c5d7-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="enabling-voice-commands"></a><span data-ttu-id="5c5d7-111">Aktivieren der Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="5c5d7-111">Enabling Voice Commands</span></span>
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

<span data-ttu-id="5c5d7-112">In diesem Abschnitt implementieren Sie einen Sprachbefehl, um den Benutzer einen Soundeffekt für das Octa-Objekt wiedergeben zu lassen.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-112">In this section, you will implement a speech command to let the user play a sound on the Octa object.</span></span> <span data-ttu-id="5c5d7-113">Zu diesem Zweck erstellen Sie einen neuen Sprachbefehl und konfigurieren dann das Ereignis so, dass es die gewünschte Aktion auslöst, wenn das Schlüsselwort des Sprachbefehls ausgesprochen wird.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-113">For this, you will create a new speech command and then configure the event so it triggers the desired action when the speech command keyword is spoken.</span></span>

<span data-ttu-id="5c5d7-114">Dies sind die wichtigsten Schritte, die Sie durchführen müssen:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-114">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="5c5d7-115">Klonen des Standardprofils des Eingabesystems</span><span class="sxs-lookup"><span data-stu-id="5c5d7-115">Clone the default Input System Profile</span></span>
2. <span data-ttu-id="5c5d7-116">Klonen des Standardprofils der Spracherkennungsbefehle</span><span class="sxs-lookup"><span data-stu-id="5c5d7-116">Clone the default Speech Commands Profile</span></span>
3. <span data-ttu-id="5c5d7-117">Erstellen eines neuen Sprachbefehls</span><span class="sxs-lookup"><span data-stu-id="5c5d7-117">Create a new speech command</span></span>
4. <span data-ttu-id="5c5d7-118">Hinzufügen und Konfigurieren der Komponente „Spracheingabehandler (Script)“</span><span class="sxs-lookup"><span data-stu-id="5c5d7-118">Add and configure the Speech Input Handler (Script) component</span></span>
5. <span data-ttu-id="5c5d7-119">Implementieren des Antwortereignisses für den Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="5c5d7-119">Implement the Response event for the speech command</span></span>

### <a name="1-clone-the-default-input-system-profile"></a><span data-ttu-id="5c5d7-120">1. Klonen des Standardprofils des Eingabesystems</span><span class="sxs-lookup"><span data-stu-id="5c5d7-120">1. Clone the default Input System Profile</span></span>

<span data-ttu-id="5c5d7-121">Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt aus, wählen Sie dann im Inspektorfenster die Registerkarte **Eingabe** aus, und klicken Sie das **DefaultHoloLens2InputSystemProfile**, um es durch Ihr eigenes anpassbares **Eingabesystemprofil** zu ersetzen:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-121">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab and clone the **DefaultHoloLens2InputSystemProfile** to replace it with your own customizable **Input System Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="5c5d7-123">Wenn Sie eine Auffrischung zum Klonen von MRTK-Profilen benötigen, lesen Sie die Anweisungen in [Konfigurieren des Mixed Reality-Toolkits](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option).</span><span class="sxs-lookup"><span data-stu-id="5c5d7-123">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

### <a name="2-clone-the-default-speech-commands-profile"></a><span data-ttu-id="5c5d7-124">2. Klonen des Standardprofils der Spracherkennungsbefehle</span><span class="sxs-lookup"><span data-stu-id="5c5d7-124">2. Clone the default Speech Commands Profile</span></span>

<span data-ttu-id="5c5d7-125">Erweitern Sie den Abschnitt **Sprache**, und klonen Sie das **DefaultMixedRealitySpeechCommandsProfile**, um es durch Ihr eigenes **Profil der Spracherkennungsbefehle** zu ersetzen:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-125">Expand the **Speech** section and clone the **DefaultMixedRealitySpeechCommandsProfile** to replace it with your own customizable **Speech Commands Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a><span data-ttu-id="5c5d7-127">3. Erstellen eines neuen Sprachbefehls</span><span class="sxs-lookup"><span data-stu-id="5c5d7-127">3. Create a new speech command</span></span>

<span data-ttu-id="5c5d7-128">Klicken Sie im Abschnitt **Spracherkennungsbefehle** auf die Schaltfläche **+ Add a New Speech Command** (Neuen Spracherkennungsbefehl hinzufügen), um unten in der Liste der vorhandenen Spracherkennungsbefehle einen neuen Spracherkennungsbefehl hinzuzufügen, und geben Sie dann im Feld **Schlüsselwort** ein passendes Wort oder einen passenden Ausdruck ein, beispielsweise **Musik abspielen**:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-128">In the **Speech Commands** section, click the **+ Add a New Speech Command** button to add a new speech command to the bottom of the list of existing speech commands, then in the **Keyword** field enter a suitable word or phrase, for example **Play Music**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> <span data-ttu-id="5c5d7-130">Wenn Ihr Computer nicht über ein Mikrofon verfügt und Sie den Sprachbefehl mithilfe der in den Editor integrierten Simulation testen möchten, können Sie dem Sprachbefehl einen Tastaturcode hinzufügen, mit dessen Hilfe Sie ihn auslösen können, wenn die entsprechende Taste gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-130">If your computer doesn't have a microphone and you would like to test the speech command using the in-editor simulation, you can assign a KeyCode to the speech command which will let you trigger it when the corresponding key is pressed.</span></span>

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a><span data-ttu-id="5c5d7-131">4. Hinzufügen und Konfigurieren der Komponente „Spracheingabehandler (Script)“</span><span class="sxs-lookup"><span data-stu-id="5c5d7-131">4. Add and configure the Speech Input Handler (Script) component</span></span>

<span data-ttu-id="5c5d7-132">Wählen Sie im Hierarchiefenster das **Octa**-Objekt aus, und fügen Sie ihm die Komponente **Spracheingabehandler (Script)** hinzu.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-132">In the Hierarchy window, select the **Octa** object and add the **Speech Input Handler (Script)** component to the Octa object.</span></span> <span data-ttu-id="5c5d7-133">Deaktivieren Sie dann das Kontrollkästchen **Is Focus Required** (Fokus erforderlich), damit der Benutzer nicht auf das Octa-Objekt blicken muss, um den Sprachbefehl auszulösen:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-133">Then uncheck the **Is Focus Required** checkbox so the user is not required to look at the Octa object to trigger the speech command:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a><span data-ttu-id="5c5d7-135">5. Implementieren des Antwortereignisses für den Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="5c5d7-135">5. Implement the Response event for the speech command</span></span>

<span data-ttu-id="5c5d7-136">Klicken Sie auf der Komponente „Spracheingabehandler (Script)“ auf die kleine **+** -Schaltfläche, um der Liste der Schlüsselwörter ein Schlüsselwortelement hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-136">On the Speech Input Handler (Script) component, click the small **+** button to add a keyword element to the list of keywords:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

<span data-ttu-id="5c5d7-138">Klicken Sie auf das neu erstellte **Element 0**, um es zu erweitern, und wählen Sie dann in der **Schlüsselwort**-Dropdownliste das Schlüsselwort **Musik abspielen** aus, das Sie zuvor erstellt hatten:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-138">Click the newly created **Element 0** to expand it, and then, from the **Keyword** dropdown, choose the **Play Music** keyword you created earlier:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> <span data-ttu-id="5c5d7-140">Die Schlüsselwörter in der Dropdownliste „Schlüsselwort“ werden aus den Schlüsselwörtern aufgefüllt, die in der Liste der Sprachbefehle im Profil der Spracherkennungsbefehle definiert sind.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-140">The keywords in the Keyword dropdown are populated based on the keywords defined in the Speech Commands list in the Speech Commands Profile.</span></span>

<span data-ttu-id="5c5d7-141">Erstellen Sie ein neues **Response ()** -Ereignis, konfigurieren Sie das **Octa**-Objekt, um das Ereignis zu empfangen, definieren Sie **AudioSource.PlayOneShot** als die auszulösende Aktion, und weisen Sie dem Feld **Audioclip** einen passenden Audioclip zu, beispielsweise den Audioclip „MRTK_Gem“:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-141">Create a new **Response ()** event, configure the **Octa** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> <span data-ttu-id="5c5d7-143">Wenn Sie eine Auffrischung zum Implementieren von Ereignissen und Zuweisen von Audioclips wünschen, lesen Sie die Anweisungen in [Implementieren des „On Touch Started“-Ereignisses](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event).</span><span class="sxs-lookup"><span data-stu-id="5c5d7-143">For a reminder on how to implement events and assign an audio clip, you can refer to the [Implement the On Touch Started event](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) instructions.</span></span>

## <a name="the-pan-gesture"></a><span data-ttu-id="5c5d7-144">Die Geste „Schwenken“</span><span class="sxs-lookup"><span data-stu-id="5c5d7-144">The Pan Gesture</span></span>

<span data-ttu-id="5c5d7-145">Die Schwenkgeste ist nützlich, um mithilfe eines Fingers oder der Hand durch Inhalte zu scrollen.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-145">The pan gesture is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="5c5d7-146">In diesem Beispiel erfahren Sie zunächst, wie Sie auf einer 2D-Benutzeroberfläche scrollen und anschließend darauf aufbauen, um das Scrollen durch eine Sammlung von 3D-Objekten zu erlernen.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-146">In this example, you will first learn how to scroll a 2D UI and then expand on that to be able to scroll through a collection of 3D objects.</span></span>

<span data-ttu-id="5c5d7-147">Dies sind die wichtigsten Schritte, die Sie durchführen müssen:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-147">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="5c5d7-148">Erstellen eines Quad-Objekts, das zum Schwenken verwendet werden kann</span><span class="sxs-lookup"><span data-stu-id="5c5d7-148">Create a Quad object that can be used for panning</span></span>
2. <span data-ttu-id="5c5d7-149">Hinzufügen der Komponente „Near Interaction touchable“ (Nah-Interaktion, berührbar)</span><span class="sxs-lookup"><span data-stu-id="5c5d7-149">Add the Near Interaction Touchable (Script) component</span></span>
3. <span data-ttu-id="5c5d7-150">Hinzufügen der Komponente „Hand Interaction Pan Zoom (Script)“ (Handinteraktion Zoomen/Schwenken (Skript))</span><span class="sxs-lookup"><span data-stu-id="5c5d7-150">Add the Hand Interaction Pan Zoom (Script) component</span></span>
4. <span data-ttu-id="5c5d7-151">Hinzufügen von 2D-Inhalten zum Scrollen</span><span class="sxs-lookup"><span data-stu-id="5c5d7-151">Add 2D content to be scrolled</span></span>
5. <span data-ttu-id="5c5d7-152">Hinzufügen von 3D-Inhalten zum Scrollen</span><span class="sxs-lookup"><span data-stu-id="5c5d7-152">Add 3D content to be scrolled</span></span>
6. <span data-ttu-id="5c5d7-153">Hinzufügen der Komponente „Move With Pan (Script)“ (Mit Schwenken bewegen (Skript))</span><span class="sxs-lookup"><span data-stu-id="5c5d7-153">Add the Move With Pan (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="5c5d7-154">Die Komponente „Move With Pan (Script)“ ist nicht Teil des MRTK.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-154">The Move With Pan (Script) component is not part of MRTK.</span></span> <span data-ttu-id="5c5d7-155">Sie wurde zusammen mit den Ressourcen für dieses Tutorial zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-155">It was provided with this tutorial's assets.</span></span>

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a><span data-ttu-id="5c5d7-156">1. Erstellen eines Quad-Objekts, das zum Schwenken verwendet werden kann</span><span class="sxs-lookup"><span data-stu-id="5c5d7-156">1. Create a Quad object that can be used for panning</span></span>

<span data-ttu-id="5c5d7-157">Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf einen leeren Bereich, und wählen Sie **3D-Objekt** > **Quad** aus, um Ihrer Szene ein Quad-Objekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-157">In the Hierarchy window, right-click at an empty area and select **3D Object** > **Quad** to add a quad to your scene.</span></span> <span data-ttu-id="5c5d7-158">Geben Sie ihm einen passenden Namen, beispielsweise **PanGesture**, und positionieren Sie es an einer passenden Stelle, beispielsweise an X = 0, Y = -0,2, Z = 2.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-158">Give it a suitable name, for example, **PanGesture**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="5c5d7-160">Wenn Sie eine Auffrischung zum Hinzufügen von Unity-Primitiven benötigen, wie etwa einem 3D-Quad-Objekt, lesen Sie die Anweisungen unter [Hinzufügen eines Würfels zur Szene](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene).</span><span class="sxs-lookup"><span data-stu-id="5c5d7-160">For a reminder on how to add Unity primitives, such as a 3D quad, to your scene, you can refer to the [Add a cube to the scene](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) instructions.</span></span>

<span data-ttu-id="5c5d7-161">Wie jede andere Interaktion erfordert auch die Schwenkgeste einen Collider.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-161">As with any other interaction, the the pan gesture also requires a collider.</span></span> <span data-ttu-id="5c5d7-162">Standardmäßig weist ein Quad-Objekt einen Gittermodell-Collider auf.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-162">By default, a Quad has a mesh collider.</span></span> <span data-ttu-id="5c5d7-163">Der Gittermodell-Collider ist jedoch nicht ideal, da er äußerst schmal ist.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-163">However, the mesh collider is not ideal because it is extremely thin.</span></span> <span data-ttu-id="5c5d7-164">Um dem Benutzer die Interaktion mit dem Collider zu vereinfachen, ersetzen wir den Gittermodell-Collider durch einen Feld-Collider.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-164">To make it easier for the user to interact with the collider, we will replace the mesh collider with a box collider.</span></span>

<span data-ttu-id="5c5d7-165">Klicken Sie bei immer noch ausgewähltem PanGesture-Objekt auf das Symbol **Einstellungen** der **Gittermodell-Collider**-Komponente, und wählen Sie **Komponente entfernen** aus, um den Gittermodell-Collider zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-165">With the PanGesture object still selected, click the **Mesh Collider** component's **Settings** icon and select **Remove Component** to remove the Mesh Collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

<span data-ttu-id="5c5d7-167">Verwenden Sie im Inspektorfenster die Schaltfläche **Komponente hinzufügen** aus, um einen **Feld-Collider** hinzuzufügen, und ändern Sie dann die **Größe** Z des Feld-Colliders in 0,15, um die Dicke des Feld-Colliders zu erhöhen:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-167">In the Inspector window, use the **Add Component** button to add a **Box Collider**, then change the Box Collider **Size** Z to 0.15 to increase the thickness of the box collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a><span data-ttu-id="5c5d7-169">2. Hinzufügen der Komponente „Near Interaction touchable (Script)“ (Nah-Interaktion, berührbar (Skript))</span><span class="sxs-lookup"><span data-stu-id="5c5d7-169">2. Add the Near Interaction Touchable (Script) component</span></span>

<span data-ttu-id="5c5d7-170">Fügen Sie bei noch ausgewähltem **PanGesture**-Objekt dem PanGesture-Objekt die Komponente **Near Interaction Touchable (Script)** (Nah-Interaktion, berührbar (Skript)) hinzu, und klicken Sie dann auf die Schaltflächen **Fix Bounds** (Begrenzungen fixieren) und **Fix Center** (Mitte fixieren), um die Eigenschaften „Local Center“ und „Bounds“ von Near Interaction Touchable (Script) so zu aktualisieren, dass sie mit dem Feld-Collider übereinstimmen:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-170">With the **PanGesture** object still selected, add the **Near Interaction Touchable (Script)** component to the PanGesture object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a><span data-ttu-id="5c5d7-172">3. Hinzufügen der Komponente „Hand Interaction Pan Zoom (Script)“ (Handinteraktion Zoomen/Schwenken (Skript))</span><span class="sxs-lookup"><span data-stu-id="5c5d7-172">3. Add the Hand Interaction Pan Zoom (Script) component</span></span>

<span data-ttu-id="5c5d7-173">Fügen Sie bei immer noch ausgewähltem **PanGesture**-Objekt die Komponente **Hand Interaction Pan Zoom (Script)** (Handinteraktion Zoomen/Schwenken (Skript)) zum PanGesture-Objekt hinzu, und aktivieren Sie dann das Kontrollkästchen **Lock Horizontal** (Horizontal sperren), um nur vertikales Scrollen zuzulassen:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-173">With the **PanGesture** object still selected, add the **Hand Interaction Pan Zoom (Script)** component to the PanGesture object, and then check the **Lock Horizontal** checkbox to allow vertical scrolling only:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a><span data-ttu-id="5c5d7-175">4. Hinzufügen von 2D-Inhalten zum Scrollen</span><span class="sxs-lookup"><span data-stu-id="5c5d7-175">4. Add 2D content to be scrolled</span></span>

<span data-ttu-id="5c5d7-176">Suchen Sie im Bereich „Projekt“ nach dem **PanContent**-Material, und bewegen Sie es dann durch Klicken und Ziehen auf die Eigenschaft **Material** Element 0 des Gittermodell-Renderers des **PanGesture**-Objekts:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-176">In the Project panel, search for the **PanContent** material and then click-and-drag it on to the **PanGesture** object's Mesh Renderer **Material** Element 0 property:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

<span data-ttu-id="5c5d7-178">Erweitern Sie im Inspektorfenster die neu hinzugefügte **PanContent**-Materialkomponente, und ändern Sie dann ihren Y-Wert für **Tiling** (Anordnung) auf 0,5, sodass er dem X-Wert entspricht und die Kachel quadratisch angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-178">In the Inspector window, expand the newly added **PanContent** material component, and then change it's **Tiling** Y value to 0.5 so it matches the X value and the tiles appear square:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

<span data-ttu-id="5c5d7-180">Wenn Sie jetzt in den Spielemodus wechseln, können Sie das Scrollen von 2D-Inhalten mithilfe der Schwenkgeste in der Editor-Simulation testen:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-180">If you now enter Game mode, you can test scrolling the 2D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a><span data-ttu-id="5c5d7-182">5. Hinzufügen von 3D-Inhalten zum Scrollen</span><span class="sxs-lookup"><span data-stu-id="5c5d7-182">5. Add 3D content to be scrolled</span></span>

<span data-ttu-id="5c5d7-183">Sie müssen im Hierarchiefenster **vier Würfel erstellen**, als untergeordnete Objekte des **PanGesture**-Objekts, deren Transformations-**Maßstab** Sie auf X = 0,15, Y = 0,15 und Z = 0,15 festlegen:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-183">In the Hierarchy window, **create four cubes** as a child objects of the **PanGesture** object and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

<span data-ttu-id="5c5d7-185">Um die Würfel gleichmäßig anzuordnen und Zeit zu sparen, fügen Sie die Komponente **Grid Object Collection (Script)** (Rasterobjektsammlung (Skript)) dem übergeordneten Objekt der Würfel hinzu, d. h. zum **PanGesture**-Objekt, und konfigurieren SIe die Rasterobjektsammlung (Skript) wie folgt:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-185">To space the cubes out evenly, and save some time, add the **Grid Object Collection (Script)** component, to the cubes' parent object, i.e. the **PanGesture** object, and configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="5c5d7-186">Ändern Sie **Num Rows** (Anzahl Zeilen) in 1, um alle Würfel in einer einzelnen Zeile auszurichten</span><span class="sxs-lookup"><span data-stu-id="5c5d7-186">Change **Num Rows** to 1 to have all the cubes aligned on one single row</span></span>
* <span data-ttu-id="5c5d7-187">Ändern Sie **Cell Width**  (Zellbreite) in 0,25, um die Würfel innerhalb der Zeile zu verteilen</span><span class="sxs-lookup"><span data-stu-id="5c5d7-187">Change **Cell Width** to 0.25 to space out the cubes within the row</span></span>

<span data-ttu-id="5c5d7-188">Klicken Sie dann auf die Schaltfläche **Sammlung aktualisieren**, um die neue Konfiguration zu übernehmen:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-188">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a><span data-ttu-id="5c5d7-190">6. Hinzufügen der Komponente „Move With Pan (Script)“ (Mit Schwenken bewegen (Skript))</span><span class="sxs-lookup"><span data-stu-id="5c5d7-190">6. Add the Move With Pan (Script) component</span></span>

<span data-ttu-id="5c5d7-191">Wählen Sie im Hierarchiefenster alle **Cube child objects** (Untergeordneten Würfelobjekte) aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um allen Würfeln die Komponente **Move With Pan (Script)** hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-191">In the Hierarchy window, select all the **Cube child objects**, then in the Inspector window, use the **Add Component** button to add the **Move With Pan (Script)** component to all the cubes:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> <span data-ttu-id="5c5d7-193">Falls Sie eine Auffrischung zum Auswählen mehrerer Objekte im Hierarchiefenster benötigen, lesen Sie die Anweisungen unter [Add the Manipulation Handler (Script) component to all the objects](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) (Hinzufügen der Komponente „Manipulationshandler (Skript)“ zu sämtlichen Objekten).</span><span class="sxs-lookup"><span data-stu-id="5c5d7-193">For a reminder on how to select multiple objects in the Hierarchy window, tou can refer to the [Add the Manipulation Handler (Script) component to all the objects](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) instructions.</span></span>

<span data-ttu-id="5c5d7-194">Bewegen Sie das **PanGesture**-Objekt mittels Klicken und Ziehen auf das Feld **Pan Input Source** (Quelle der Schwenkeingabe), wobei alle Würfel immer noch ausgewählt sein müssen:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-194">With all the cubes still selected, click-and-drag the **PanGesture** object to the **Pan Input Source** field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> <span data-ttu-id="5c5d7-196">Die Komponente „Move With Pan (Script)“ (Mit Schwenken bewegen (Skript)) auf jedem der Würfel lauscht nach dem Pan Updated-Ereignis (Schwenk aktualisiert), das von der HandInteractionPanZoom (Script)-Komponente auf dem PanGesture-Objekt gesendet wird, das Sie im Schritt oben als Eingabequelle für den Schwenk zugewiesen haben, und aktualisiert die Position jedes Würfels entsprechend.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-196">The Move With Pan (Script) component on each cube listens for the Pan Updated event sent by the HandInteractionPanZoom (Script) component on the PanGesture object, which you assigned as the Pan Input Source in the step above, and updates each cube's position accordingly.</span></span>

<span data-ttu-id="5c5d7-197">Wählen Sie im Hierarchiefenster das **PanGesture**-Objekt aus, und **deaktivieren** Sie dann im Inspektor das Kontrollkästchen **Mesh Renderer** (Gittermodell-Renderer), um die Mesh Renderer-Komponente zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-197">In the Hierarchy window, select the **PanGesture** object, then in the inspector **un-check** the **Mesh Renderer** checkbox to disable the Mesh Renderer component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

<span data-ttu-id="5c5d7-199">Wenn Sie jetzt in den Spielemodus wechseln, können Sie das Scrollen von 3D-Inhalten mithilfe der Schwenkgeste in der Editor-Simulation testen:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-199">If you now enter Game mode, you can test scrolling the 3D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a><span data-ttu-id="5c5d7-201">Eyetracking</span><span class="sxs-lookup"><span data-stu-id="5c5d7-201">Eye Tracking</span></span>

<span data-ttu-id="5c5d7-202">In diesem Abschnitt wird erläutert, wie Sie das Eyetracking in Ihrem Projekt aktivieren.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-202">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="5c5d7-203">Für dieses Beispiel implementieren Sie Funktionalität, um jedes Objekt in der 3DObjectCollection langsam rotieren zu lassen, während es durch das Auge des Benutzers anvisiert wird, sowie ein Aufleuchten auszulösen, wenn das anvisierte Objekt durch eine Tippbewegung in die Luft oder durch einen Sprachbefehl ausgewählt wird.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-203">For this example, you will implement functionality to make each object in the 3DObjectCollection spin slowly while being looked at by the user's eye gaze, as well as, trigger a blip effect when the object being looked at is selected by air-tap or speech command.</span></span>

<span data-ttu-id="5c5d7-204">Dies sind die wichtigsten Schritte, die Sie durchführen müssen:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-204">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="5c5d7-205">Hinzufügen der Komponente „ Eye Tracking Target (Script)“ (Blickverfolgungsziel (Skript)) zu allen Zielobjekten</span><span class="sxs-lookup"><span data-stu-id="5c5d7-205">Add the Eye Tracking Target (Script) component to all target objects</span></span>
2. <span data-ttu-id="5c5d7-206">Hinzufügen der Komponente „ Eye Tracking Tutorial Demo (Script)“ (Blickverfolgung-Tutorialdemo (Skript)) zu allen Zielobjekten</span><span class="sxs-lookup"><span data-stu-id="5c5d7-206">Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>
3. <span data-ttu-id="5c5d7-207">Implementieren des While Looking At Target-Ereignisses (Beim Ansehen des Ziels)</span><span class="sxs-lookup"><span data-stu-id="5c5d7-207">Implement the While Looking At Target event</span></span>
4. <span data-ttu-id="5c5d7-208">Implementieren des On Selected-Ereignisses (Bei Auswahl)</span><span class="sxs-lookup"><span data-stu-id="5c5d7-208">Implement the On Selected event</span></span>
5. <span data-ttu-id="5c5d7-209">Aktivieren von simulierter Blickverfolgung für Simulationen im Editor</span><span class="sxs-lookup"><span data-stu-id="5c5d7-209">Enable simulated eye tracking for in-editor simulations</span></span>
6. <span data-ttu-id="5c5d7-210">Aktivieren der Eingabe durch Anvisieren in den App-Funktionen des Visual Studio-Projekts</span><span class="sxs-lookup"><span data-stu-id="5c5d7-210">Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a><span data-ttu-id="5c5d7-211">1. Hinzufügen der Komponente „ Eye Tracking Target (Script)“ (Blickverfolgungsziel (Skript)) zu allen Zielobjekten</span><span class="sxs-lookup"><span data-stu-id="5c5d7-211">1. Add the Eye Tracking Target (Script) component to all target objects</span></span>

<span data-ttu-id="5c5d7-212">Erweitern Sie im Hierarchiefenster das **3DObjectCollection**-Objekt, und wählen Sie alle **untergeordneten Objekte** aus, verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um allen untergeordneten Objekten die **Eye Tracking Target (Script)** -Komponente hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-212">In the Hierarchy window, expand the **3DObjectCollection** object and select all the **child objects**, then in the Inspector window, use the **Add Component** button to add the **Eye Tracking Target (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

<span data-ttu-id="5c5d7-214">Konfigurieren Sie die **Eye Tracking Target (Script)** -Komponente wie folgt, während alle **untergeordneten Objekte** noch ausgewählt sind:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-214">With all the **child objects** still selected, configure the **Eye Tracking Target (Script)** component as follows:</span></span>

* <span data-ttu-id="5c5d7-215">Ändern Sie **Aktion auswählen** in **Auswählen**, um die Aktion des Tippens in die Luft für dieses Objekt als Auswählen zu definieren</span><span class="sxs-lookup"><span data-stu-id="5c5d7-215">Change **Select Action** to **Select**, to define the air-tap action for this object as Select</span></span>
* <span data-ttu-id="5c5d7-216">Erweitern Sie **Voice Select** (Sprachauswahl), und legen Sie die **Größe** der Sprachbefehlsliste auf 1 fest. Ändern Sie dann in der nun angezeigten Liste der neuen Elemente **Element 0** in **Select** (Auswählen), um die Sprachbefehlsaktion für dieses Objekt als Auswählen zu definieren</span><span class="sxs-lookup"><span data-stu-id="5c5d7-216">Expand **Voice Select** and set the voice command list **Size** to 1, and then, in the new element list that appear, change **Element 0** to **Select**, to define the speech command action for this object as Select</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a><span data-ttu-id="5c5d7-218">2. Hinzufügen der Komponente „ Eye Tracking Tutorial Demo (Script)“ (Blickverfolgung-Tutorialdemo (Skript)) zu allen Zielobjekten</span><span class="sxs-lookup"><span data-stu-id="5c5d7-218">2. Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>

<span data-ttu-id="5c5d7-219">Verwenden Sie die Schaltfläche **Komponente hinzufügen**, während alle **untergeordneten Objekte** immer noch ausgewählt sind, um den untergeordneten Objekten die Komponente **Eye Tracking Tutorial Demo (Script)** hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-219">With all the **child objects** still selected, use the **Add Component** button to add the **Eye Tracking Tutorial Demo (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> <span data-ttu-id="5c5d7-221">Die Komponente „Eye Tracking Target (Script)“ ist kein Teil des MRTK.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-221">The Eye Tracking Target (Script) component is not part of MRTK.</span></span> <span data-ttu-id="5c5d7-222">Sie wurde zusammen mit den Ressourcen für dieses Tutorial zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-222">It was provided with this tutorial's assets.</span></span>

### <a name="3-implement-the-while-looking-at-target-event"></a><span data-ttu-id="5c5d7-223">3. Implementieren des While Looking At Target-Ereignisses (Beim Ansehen des Ziels)</span><span class="sxs-lookup"><span data-stu-id="5c5d7-223">3. Implement the While Looking At Target event</span></span>

<span data-ttu-id="5c5d7-224">Wählen Sie im Hierarchiefenster das **Cheese**-Objekt (Käse), erstellen Sie dann ein neues **While Looking At Target ()** -Ereignis, konfigurieren Sie das **Cheese**-Objekt dafür, das Ereignis zu empfangen, und definieren Sie **EyeTrackingTutorialDemo.RotateTarget** als auszulösende Aktion:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-224">In the Hierarchy window, select the **Cheese** object, then create a new **While Looking At Target ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

<span data-ttu-id="5c5d7-226">**Wiederholen** Sie diesen Vorgang für jedes der untergeordneten Objekte in der 3DObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-226">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

> [!TIP]
> <span data-ttu-id="5c5d7-227">Falls Sie eine Auffrischung zum Implementieren von Ereignissen benötigen, lesen Sie die Anweisungen unter [Gesten für Handtracking und interaktionsfähige Schaltflächen](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).</span><span class="sxs-lookup"><span data-stu-id="5c5d7-227">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="4-implement-the-on-selected-event"></a><span data-ttu-id="5c5d7-228">4. Implementieren des On Selected-Ereignisses (Bei Auswahl)</span><span class="sxs-lookup"><span data-stu-id="5c5d7-228">4. Implement the On Selected event</span></span>

<span data-ttu-id="5c5d7-229">Wählen Sie im Hierarchiefenster das **Cheese**-Objekt (Käse) aus, erstellen Sie dann ein neues **On Selected ()** -Ereignis, konfigurieren Sie das **Cheese**-Objekt dafür, das Ereignis zu empfangen, und definieren Sie **EyeTrackingTutorialDemo.BlipTarget** als auszulösende Aktion:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-229">In the Hierarchy window, select the **Cheese** object, then create a new **On Selected ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.BlipTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

<span data-ttu-id="5c5d7-231">**Wiederholen** Sie diesen Vorgang für jedes der untergeordneten Objekte in der 3DObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-231">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a><span data-ttu-id="5c5d7-232">5. Aktivieren von simulierter Blickverfolgung für Simulationen im Editor</span><span class="sxs-lookup"><span data-stu-id="5c5d7-232">5. Enable simulated eye tracking for in-editor simulations</span></span>

<span data-ttu-id="5c5d7-233">Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt aus, wählen Sie dann im Inspektorfenster die Registerkarte **Eingabe** aus, erweitern Sie den Abschnitt **Input Data Providers** (Eingabedatenanbieter), dann den Abschnitt **Input Simulation Service** (Eingabesimulationsdienst), und klonen Sie das **DefaultMixedRealityInputSimulationProfile**, um es durch Ihr eigenes anpassbares **Input Simulation Profile** (Eingabesimulationsprofil) zu ersetzen:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-233">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab, expand the **Input Data Providers** section and then the **Input Simulation Service** section, and clone the **DefaultMixedRealityInputSimulationProfile** to replace it with your own customizable **Input Simulation Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> <span data-ttu-id="5c5d7-235">Wenn Sie eine Auffrischung zum Klonen von MRTK-Profilen benötigen, lesen Sie die Anweisungen in [Konfigurieren des Mixed Reality-Toolkits](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option).</span><span class="sxs-lookup"><span data-stu-id="5c5d7-235">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="5c5d7-236">Aktivieren Sie im Abschnitt **Eye Simulation** (Augensimulation) das Kontrollkästchen **Simulate Eye Position** (Augenposition simulieren), um die Blickverfolgungssimulation zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-236">In the **Eye Simulation** section, check the **Simulate Eye Position** checkbox to enable eye tracking simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

<span data-ttu-id="5c5d7-238">Wenn Sie jetzt in den Spielmodus wechseln, können Sie die Rotations- und die Leuchteffekte testen, die Sie implementiert haben, indem Sie die Ansicht so anpassen, dass der Cursor auf eins der Objekte trifft und Handinteraktion oder einen Sprachbefehl verwenden, um das Objekt auszuwählen:</span><span class="sxs-lookup"><span data-stu-id="5c5d7-238">If you now enter Game mode, you can test the spin and blip effects you implemented by adjusting the view so the cursor hits one of the objects and using hand interaction or speech command to select the object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> <span data-ttu-id="5c5d7-240">Wenn Sie nicht das DefaultHoloLens2ConfigurationProfile zum Klonen Ihres anpassbaren MRTK-Konfigurationsprofils verwendet haben, wie in den Anweisungen zum [Konfigurieren des Mixed Reality-Toolkits](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) gefordert, steht die Blickverfolgung in Ihrem Projekt möglicherweise nicht zur Verfügung und muss aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-240">If you did not use the DefaultHoloLens2ConfigurationProfile to clone your customizable MRTK configuration profile, as instructed in the [Configure the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) instructions, eye tracking may not be enable in your project and will need to be enabled.</span></span> <span data-ttu-id="5c5d7-241">Lesen Sie zu diesem Zweck die Anweisungen unter [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) (Erste Schritte mit der Blickverfolgung in MRTK).</span><span class="sxs-lookup"><span data-stu-id="5c5d7-241">For that, you can refer to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions.</span></span>

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a><span data-ttu-id="5c5d7-242">6. Aktivieren der Eingabe durch Anvisieren in den App-Funktionen des Visual Studio-Projekts</span><span class="sxs-lookup"><span data-stu-id="5c5d7-242">6. Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

<span data-ttu-id="5c5d7-243">Bevor Sie Ihre Anwendung erstellen und aus Visual Studio auf Ihrem Gerät bereitstellen, muss Eingabe durch Anvisieren in den Funktionen Ihrer Projekt-App aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-243">Before building and deploying your app from Visual Studio to your device, Gaze Input has to been enabled in the project's app capabilities.</span></span> <span data-ttu-id="5c5d7-244">Zu diesem Zweck können Sie die Anweisungen unter [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) (Testen Ihrer Unity-App an einer HoloLens 2) befolgen.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-244">For this, you can follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="5c5d7-245">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="5c5d7-245">Congratulations</span></span>

<span data-ttu-id="5c5d7-246">Sie haben Ihrer Anwendung erfolgreich grundlegende Eyetracking-Funktionen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-246">You have successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="5c5d7-247">Diese Aktionen stellen nur den Einstieg in eine ganze Welt der Möglichkeiten mit Eyetracking dar.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-247">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="5c5d7-248">In diesem Tutorial haben Sie außerdem einiges über weitere erweiterte Eingabefunktionen erfahren, wie etwa Sprachbefehle und Schwenkgesten.</span><span class="sxs-lookup"><span data-stu-id="5c5d7-248">In this tutorial, you also learned about other advanced input features, such as voice commands and panning gestures.</span></span>

[<span data-ttu-id="5c5d7-249">Nächste Lektion: 7. Erstellen einer Beispielanwendung für eine Mondlandefähre (Lunar Module)</span><span class="sxs-lookup"><span data-stu-id="5c5d7-249">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)
