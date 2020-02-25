---
title: 'Tutorials zu den ersten Schritten: 6. Untersuchen von erweiterten Eingabeoptionen'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: aaa02ce118fd051d94311e837b143affc96ff72b
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554258"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="ad6e8-105">6. untersuchen erweiterter Eingabeoptionen</span><span class="sxs-lookup"><span data-stu-id="ad6e8-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="ad6e8-106">In diesem Tutorial werden einige erweiterte Eingabeoptionen für hololens 2 untersucht, einschließlich der Verwendung von Sprachbefehlen, der Schwenkbewegung und der Eye-Nachverfolgung.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-106">In this tutorial, you will explore a few advanced input options for HoloLens 2, including the use of voice commands, panning gesture, and eye tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="ad6e8-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="ad6e8-107">Objectives</span></span>

* <span data-ttu-id="ad6e8-108">Ereignisse mithilfe von Sprachbefehlen und Schlüsselwörtern Auslösers</span><span class="sxs-lookup"><span data-stu-id="ad6e8-108">Trigger events using voice commands and keywords</span></span>
* <span data-ttu-id="ad6e8-109">Verwenden von nach verfolgten Händen zum Schwenken von Texturen und 3D-Objekten mit nach verfolgten Händen</span><span class="sxs-lookup"><span data-stu-id="ad6e8-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
* <span data-ttu-id="ad6e8-110">Verwenden von hololens 2 Eye Tracking-Funktionen zum Auswählen von Objekten</span><span class="sxs-lookup"><span data-stu-id="ad6e8-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="enabling-voice-commands"></a><span data-ttu-id="ad6e8-111">Aktivieren der Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="ad6e8-111">Enabling Voice Commands</span></span>
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

<span data-ttu-id="ad6e8-112">In diesem Abschnitt implementieren Sie einen Sprachbefehl, mit dem Benutzer einen Sound für das Octa-Objekt abspielen können.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-112">In this section, you will implement a speech command to let the user play a sound on the Octa object.</span></span> <span data-ttu-id="ad6e8-113">Hierfür erstellen Sie einen neuen Sprachbefehl und konfigurieren dann das Ereignis, sodass die gewünschte Aktion ausgelöst wird, wenn das sprach Befehls Schlüsselwort gesprochen wird.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-113">For this, you will create a new speech command and then configure the event so it triggers the desired action when the speech command keyword is spoken.</span></span>

<span data-ttu-id="ad6e8-114">Dies sind die wichtigsten Schritte, die Sie durchführen müssen:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-114">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="ad6e8-115">Klonen des standardmäßigen Eingabe System Profils</span><span class="sxs-lookup"><span data-stu-id="ad6e8-115">Clone the default Input System Profile</span></span>
2. <span data-ttu-id="ad6e8-116">Klonen des standardmäßigen Sprach Befehls Profils</span><span class="sxs-lookup"><span data-stu-id="ad6e8-116">Clone the default Speech Commands Profile</span></span>
3. <span data-ttu-id="ad6e8-117">Neuen Sprachbefehl erstellen</span><span class="sxs-lookup"><span data-stu-id="ad6e8-117">Create a new speech command</span></span>
4. <span data-ttu-id="ad6e8-118">Hinzufügen und Konfigurieren der Spracheingabe Handler-Komponente (Skript)</span><span class="sxs-lookup"><span data-stu-id="ad6e8-118">Add and configure the Speech Input Handler (Script) component</span></span>
5. <span data-ttu-id="ad6e8-119">Implementieren Sie das Antwort Ereignis für den Sprachbefehl.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-119">Implement the Response event for the speech command</span></span>

### <a name="1-clone-the-default-input-system-profile"></a><span data-ttu-id="ad6e8-120">1. Klonen Sie das standardmäßige Eingabe System Profil.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-120">1. Clone the default Input System Profile</span></span>

<span data-ttu-id="ad6e8-121">Wählen Sie im Fenster Hierarchie das **mixedrealitytoolkit** -Objekt aus, wählen Sie im Inspektor-Fenster die Registerkarte **Eingabe** aus, und Klonen Sie das **DefaultHoloLens2InputSystemProfile** , um es durch ihr eigenes anpassbares **Eingabe System Profil**zu ersetzen:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-121">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab and clone the **DefaultHoloLens2InputSystemProfile** to replace it with your own customizable **Input System Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="ad6e8-123">Eine Erinnerung zum Klonen von mrtk-Profilen finden Sie unter [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-123">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

### <a name="2-clone-the-default-speech-commands-profile"></a><span data-ttu-id="ad6e8-124">2. Klonen Sie das Standardprofil für Sprachbefehle.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-124">2. Clone the default Speech Commands Profile</span></span>

<span data-ttu-id="ad6e8-125">Erweitern Sie den Abschnitt **sprach** Ausgabe, und Klonen Sie die **Datei defaultmixedrealitysprechcommandsprofile** , um Sie durch ihr eigenes **Profil für Sprachbefehle**zu ersetzen:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-125">Expand the **Speech** section and clone the **DefaultMixedRealitySpeechCommandsProfile** to replace it with your own customizable **Speech Commands Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a><span data-ttu-id="ad6e8-127">3. Erstellen eines neuen sprach Befehls</span><span class="sxs-lookup"><span data-stu-id="ad6e8-127">3. Create a new speech command</span></span>

<span data-ttu-id="ad6e8-128">Klicken Sie im Abschnitt **Sprachbefehle** auf die Schaltfläche **+ neuen Sprachbefehl hinzufügen** , um am Ende der Liste vorhandener Sprachbefehle einen neuen Sprachbefehl hinzuzufügen, und geben Sie dann im **Schlüsselwort** ein passendes Wort oder einen Ausdruck ein, z. b. **Abspielen von Musik**:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-128">In the **Speech Commands** section, click the **+ Add a New Speech Command** button to add a new speech command to the bottom of the list of existing speech commands, then in the **Keyword** field enter a suitable word or phrase, for example **Play Music**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> <span data-ttu-id="ad6e8-130">Wenn Ihr Computer nicht über ein Mikrofon verfügt und Sie den Sprachbefehl mithilfe der in-Editor-Simulation testen möchten, können Sie dem Sprachbefehl einen Keycode zuweisen, mit dem Sie ihn beim Drücken der entsprechenden Taste auslassen können.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-130">If your computer doesn't have a microphone and you would like to test the speech command using the in-editor simulation, you can assign a KeyCode to the speech command which will let you trigger it when the corresponding key is pressed.</span></span>

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a><span data-ttu-id="ad6e8-131">4. hinzufügen und Konfigurieren der Spracheingabe Handler-Komponente (Skript)</span><span class="sxs-lookup"><span data-stu-id="ad6e8-131">4. Add and configure the Speech Input Handler (Script) component</span></span>

<span data-ttu-id="ad6e8-132">Wählen Sie im Fenster Hierarchie das **Octa** -Objekt aus, und fügen Sie die Komponente **Spracheingabe Handler (Skript)** dem Octa-Objekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-132">In the Hierarchy window, select the **Octa** object and add the **Speech Input Handler (Script)** component to the Octa object.</span></span> <span data-ttu-id="ad6e8-133">Deaktivieren Sie dann das Kontrollkästchen mit dem **Fokus ist erforderlich** , damit der Benutzer das Octa-Objekt nicht überprüfen muss, um den Sprachbefehl zu starten:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-133">Then uncheck the **Is Focus Required** checkbox so the user is not required to look at the Octa object to trigger the speech command:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a><span data-ttu-id="ad6e8-135">5. implementieren Sie das Antwort Ereignis für den Sprachbefehl.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-135">5. Implement the Response event for the speech command</span></span>

<span data-ttu-id="ad6e8-136">Klicken Sie in der Spracheingabe Handler-Komponente (Skript) auf die Schaltfläche Small **+** , um der Liste der Schlüsselwörter ein Schlüsselwort Element hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-136">On the Speech Input Handler (Script) component, click the small **+** button to add a keyword element to the list of keywords:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

<span data-ttu-id="ad6e8-138">Klicken Sie auf das neu erstellte **Element 0** , um es zu erweitern, und wählen Sie dann aus der Dropdown Liste **Schlüsselwort** das **Play Music** -Schlüsselwort, das Sie zuvor erstellt haben:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-138">Click the newly created **Element 0** to expand it, and then, from the **Keyword** dropdown, choose the **Play Music** keyword you created earlier:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> <span data-ttu-id="ad6e8-140">Die Schlüsselwörter in der Dropdown Liste für Schlüsselwörter werden basierend auf den Schlüsselwörtern aufgefüllt, die in der Liste der Sprachbefehle im Profil für Sprachbefehle definiert sind.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-140">The keywords in the Keyword dropdown are populated based on the keywords defined in the Speech Commands list in the Speech Commands Profile.</span></span>

<span data-ttu-id="ad6e8-141">Erstellen Sie ein neues **Response ()** -Ereignis, konfigurieren Sie das **Octa** -Objekt für den Empfang des Ereignisses, definieren Sie **audiosource. playoneshot** als auszulösenden Aktion, und weisen Sie dem **Audioclip** -Feld einen passenden Audioclip zu, z. b. den MRTK_Gem Audioclip:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-141">Create a new **Response ()** event, configure the **Octa** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> <span data-ttu-id="ad6e8-143">Eine Erinnerung zum Implementieren von Ereignissen und zum Zuweisen eines Audioclips finden Sie in der Anleitung zum [Implementieren der on](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) -Finger Eingaben.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-143">For a reminder on how to implement events and assign an audio clip, you can refer to the [Implement the On Touch Started event](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) instructions.</span></span>

## <a name="the-pan-gesture"></a><span data-ttu-id="ad6e8-144">Die Geste „Schwenken“</span><span class="sxs-lookup"><span data-stu-id="ad6e8-144">The Pan Gesture</span></span>

<span data-ttu-id="ad6e8-145">Mit der Schwenkbewegung können Sie einen Bildlauf durchführen, indem Sie mit dem Finger oder der Hand einen Bildlauf durchführen</span><span class="sxs-lookup"><span data-stu-id="ad6e8-145">The pan gesture is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="ad6e8-146">In diesem Beispiel erfahren Sie zunächst, wie Sie einen Bildlauf für eine 2D-Benutzeroberfläche durchführen und dann darauf erweitern, um durch eine Auflistung von 3D-Objekten scrollen zu können.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-146">In this example, you will first learn how to scroll a 2D UI and then expand on that to be able to scroll through a collection of 3D objects.</span></span>

<span data-ttu-id="ad6e8-147">Dies sind die wichtigsten Schritte, die Sie durchführen müssen:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-147">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="ad6e8-148">Erstellen eines Quad-Objekts, das zum Schwenken verwendet werden kann</span><span class="sxs-lookup"><span data-stu-id="ad6e8-148">Create a Quad object that can be used for panning</span></span>
2. <span data-ttu-id="ad6e8-149">Hinzufügen der Near-interaktionstouchable-Komponente (Skript)</span><span class="sxs-lookup"><span data-stu-id="ad6e8-149">Add the Near Interaction Touchable (Script) component</span></span>
3. <span data-ttu-id="ad6e8-150">Fügen Sie die Komponente "Hand Interaktion schwenken Zoom (Skript)" hinzu.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-150">Add the Hand Interaction Pan Zoom (Script) component</span></span>
4. <span data-ttu-id="ad6e8-151">2D-Inhalt zum durch Scrollen hinzufügen</span><span class="sxs-lookup"><span data-stu-id="ad6e8-151">Add 2D content to be scrolled</span></span>
5. <span data-ttu-id="ad6e8-152">Hinzufügen von 3D-Inhalt für den scrollt</span><span class="sxs-lookup"><span data-stu-id="ad6e8-152">Add 3D content to be scrolled</span></span>
6. <span data-ttu-id="ad6e8-153">Hinzufügen der Komponente "mit Pan (Skript) verschieben"</span><span class="sxs-lookup"><span data-stu-id="ad6e8-153">Add the Move With Pan (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="ad6e8-154">Die Komponente "mit Pan verschieben (Skript)" ist nicht Bestandteil von mrtk.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-154">The Move With Pan (Script) component is not part of MRTK.</span></span> <span data-ttu-id="ad6e8-155">Es wurde mit den Assets dieses Tutorials bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-155">It was provided with this tutorial's assets.</span></span>

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a><span data-ttu-id="ad6e8-156">1. Erstellen eines Quad-Objekts, das zum Schwenken verwendet werden kann</span><span class="sxs-lookup"><span data-stu-id="ad6e8-156">1. Create a Quad object that can be used for panning</span></span>

<span data-ttu-id="ad6e8-157">Klicken Sie im Hierarchie Fenster mit der rechten Maustaste auf einen leeren Bereich, und wählen Sie **3D-Objekt** > **Quad** aus, um der Szene ein vierfache hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-157">In the Hierarchy window, right-click at an empty area and select **3D Object** > **Quad** to add a quad to your scene.</span></span> <span data-ttu-id="ad6e8-158">Geben Sie ihm einen passenden Namen, z. b. **pangesture**, und positionieren Sie ihn an einem geeigneten Speicherort, z. b. X = 0, Y =-0,2, Z = 2.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-158">Give it a suitable name, for example, **PanGesture**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="ad6e8-160">Eine Erinnerung zum Hinzufügen von Unity-primitiven, z. b. ein 3D-Quad, zu Ihrer Szene, finden Sie in der Anleitung zum [Hinzufügen eines Cubes zu einer Szene](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) .</span><span class="sxs-lookup"><span data-stu-id="ad6e8-160">For a reminder on how to add Unity primitives, such as a 3D quad, to your scene, you can refer to the [Add a cube to the scene](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) instructions.</span></span>

<span data-ttu-id="ad6e8-161">Wie bei jeder anderen Interaktion erfordert auch die schwenken-Bewegung einen Collider.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-161">As with any other interaction, the the pan gesture also requires a collider.</span></span> <span data-ttu-id="ad6e8-162">Standardmäßig weist ein Quad einen Mesh-Collider auf.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-162">By default, a Quad has a mesh collider.</span></span> <span data-ttu-id="ad6e8-163">Der Mesh-Collider ist jedoch nicht ideal, da er äußerst dünn ist.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-163">However, the mesh collider is not ideal because it is extremely thin.</span></span> <span data-ttu-id="ad6e8-164">Um dem Benutzer die Interaktion mit dem Collider zu vereinfachen, ersetzen wir den Mesh Collider durch einen Box Collider.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-164">To make it easier for the user to interact with the collider, we will replace the mesh collider with a box collider.</span></span>

<span data-ttu-id="ad6e8-165">Wenn das pangesture-Objekt noch ausgewählt ist, klicken Sie auf das **Einstellungs** Symbol der **Mesh Collider** -Komponente, und wählen Sie **Komponente entfernen** aus, um den Mesh Collider zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-165">With the PanGesture object still selected, click the **Mesh Collider** component's **Settings** icon and select **Remove Component** to remove the Mesh Collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

<span data-ttu-id="ad6e8-167">Verwenden Sie im Inspektor-Fenster die Schaltfläche **Komponente hinzufügen** , um einen **Box-Collider**hinzuzufügen, und ändern Sie dann die **Größe** des Kontrollkästchens von Z in 0,15, um die Stärke des boxcollider zu erhöhen:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-167">In the Inspector window, use the **Add Component** button to add a **Box Collider**, then change the Box Collider **Size** Z to 0.15 to increase the thickness of the box collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a><span data-ttu-id="ad6e8-169">2. Hinzufügen der touchable-Komponente (Skript) für die Near-Interaktion</span><span class="sxs-lookup"><span data-stu-id="ad6e8-169">2. Add the Near Interaction Touchable (Script) component</span></span>

<span data-ttu-id="ad6e8-170">Wenn das **pangesture** -Objekt noch ausgewählt ist, fügen Sie dem pangesture-Objekt die touchable-Komponente der **near-Interaktion (Script)** hinzu, und klicken Sie dann auf die Schaltflächen **fixbegrenzungen** und **Fix Center** , um die Eigenschaften des lokalen Centers und der Begrenzungen der Near-interaktionstouchable (Script) zu aktualisieren, die mit boxcollider</span><span class="sxs-lookup"><span data-stu-id="ad6e8-170">With the **PanGesture** object still selected, add the **Near Interaction Touchable (Script)** component to the PanGesture object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a><span data-ttu-id="ad6e8-172">3. Fügen Sie die Komponente "Hand Interaktion schwenken Zoom (Skript)" hinzu.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-172">3. Add the Hand Interaction Pan Zoom (Script) component</span></span>

<span data-ttu-id="ad6e8-173">Wenn das **pangesture** -Objekt noch ausgewählt ist, fügen Sie dem pangesture-Objekt die Komponente " **Hand Interaktion schwenken schwenken (Skript)** " hinzu, und aktivieren Sie dann das Kontrollkästchen " **Horizontal Sperren** ", um nur vertikales Scrollen zuzulassen:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-173">With the **PanGesture** object still selected, add the **Hand Interaction Pan Zoom (Script)** component to the PanGesture object, and then check the **Lock Horizontal** checkbox to allow vertical scrolling only:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a><span data-ttu-id="ad6e8-175">4. Hinzufügen von 2D-Inhalt für den scrollt</span><span class="sxs-lookup"><span data-stu-id="ad6e8-175">4. Add 2D content to be scrolled</span></span>

<span data-ttu-id="ad6e8-176">Suchen Sie im Projekt Panel nach dem **Inhalt von pancontent** , und klicken Sie darauf, und ziehen Sie es auf die Eigenschaft Mesh Renderer **Material** Element 0 des **pangesture** -Objekts:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-176">In the Project panel, search for the **PanContent** material and then click-and-drag it on to the **PanGesture** object's Mesh Renderer **Material** Element 0 property:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

<span data-ttu-id="ad6e8-178">Erweitern Sie im Inspektor-Fenster die neu hinzugefügte Komponente " **pancontent** -Material", und ändern Sie den Y-Wert in 0,5, sodass er mit dem **X-Wert** übereinstimmt und die Kacheln im Quadrat angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-178">In the Inspector window, expand the newly added **PanContent** material component, and then change it's **Tiling** Y value to 0.5 so it matches the X value and the tiles appear square:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

<span data-ttu-id="ad6e8-180">Wenn Sie jetzt den Spielmodus wechseln, können Sie den 2D-Inhalt mit der Schwenkbewegung in der in-Editor-Simulation testen:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-180">If you now enter Game mode, you can test scrolling the 2D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a><span data-ttu-id="ad6e8-182">5. Hinzufügen von 3D-Inhalt für den scrollt</span><span class="sxs-lookup"><span data-stu-id="ad6e8-182">5. Add 3D content to be scrolled</span></span>

<span data-ttu-id="ad6e8-183">Erstellen Sie im Hierarchie Fenster **vier Cubes** als untergeordnete Objekte des **pangesture** -Objekts, und legen Sie Ihre Transformations **Skala** auf X = 0,15, Y = 0,15, Z = 0,15 fest:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-183">In the Hierarchy window, **create four cubes** as a child objects of the **PanGesture** object and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

<span data-ttu-id="ad6e8-185">Um die Cubes gleichmäßig zu verteilen und einige Zeit zu sparen, fügen Sie dem übergeordneten Objekt des Cubes, d. h. dem **pangesture** -Objekt, die Raster Objekt Auflistungs Komponente **(Skript)** hinzu, und konfigurieren Sie die Raster Objekt Auflistung (Skript) wie folgt:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-185">To space the cubes out evenly, and save some time, add the **Grid Object Collection (Script)** component, to the cubes' parent object, i.e. the **PanGesture** object, and configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="ad6e8-186">Ändern von **num-Zeilen** in 1, damit alle Cubes an einer einzelnen Zeile ausgerichtet sind</span><span class="sxs-lookup"><span data-stu-id="ad6e8-186">Change **Num Rows** to 1 to have all the cubes aligned on one single row</span></span>
* <span data-ttu-id="ad6e8-187">Ändern Sie die **Zellen Breite** in 0,25, um die Cubes innerhalb der Zeile leer zu legen.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-187">Change **Cell Width** to 0.25 to space out the cubes within the row</span></span>

<span data-ttu-id="ad6e8-188">Klicken Sie dann auf die Schaltfläche **Sammlung aktualisieren** , um die neue Konfiguration zu übernehmen:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-188">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a><span data-ttu-id="ad6e8-190">6. Hinzufügen der Komponente "mit Pan (Skript) verschieben"</span><span class="sxs-lookup"><span data-stu-id="ad6e8-190">6. Add the Move With Pan (Script) component</span></span>

<span data-ttu-id="ad6e8-191">Wählen Sie im Fenster Hierarchie die Option alle untergeordneten **Cube-Objekte**aus, und verwenden Sie dann im Inspektor-Fenster die Schaltfläche **Komponente hinzufügen** , um die Komponente zum **Verschieben mit schwenken (Skript)** zu allen Cubes hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-191">In the Hierarchy window, select all the **Cube child objects**, then in the Inspector window, use the **Add Component** button to add the **Move With Pan (Script)** component to all the cubes:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> <span data-ttu-id="ad6e8-193">Zur Erinnerung, wie mehrere Objekte im Hierarchie Fenster ausgewählt werden, kann tou auf die [Komponente hinzufügen der Bearbeitungs Handlers (Skript) zu allen Objekt](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) Anweisungen verweisen.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-193">For a reminder on how to select multiple objects in the Hierarchy window, tou can refer to the [Add the Manipulation Handler (Script) component to all the objects](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) instructions.</span></span>

<span data-ttu-id="ad6e8-194">Wenn alle Cubes noch ausgewählt sind, klicken Sie auf das **pangesture** -Objekt, und ziehen Sie es in das Feld **Eingabe Quelle schwenken** :</span><span class="sxs-lookup"><span data-stu-id="ad6e8-194">With all the cubes still selected, click-and-drag the **PanGesture** object to the **Pan Input Source** field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> <span data-ttu-id="ad6e8-196">Die Komponente "mit Pan verschieben (Skript)" auf jedem Cube überwacht das von der Komponente "handinteraktionpanzoom (Skript)" auf dem pangesture-Objekt gesendete Pan-aktualisierte Ereignis, das Sie im obigen Schritt als Eingabe Quelle "Pan" zugewiesen haben, und aktualisiert die Position jedes Cubes. entsprechende.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-196">The Move With Pan (Script) component on each cube listens for the Pan Updated event sent by the HandInteractionPanZoom (Script) component on the PanGesture object, which you assigned as the Pan Input Source in the step above, and updates each cube's position accordingly.</span></span>

<span data-ttu-id="ad6e8-197">Wählen Sie im Fenster Hierarchie das **pangesture** -Objekt aus, und deaktivieren Sie dann im Inspektor das Kontrollkästchen **Gitter Renderer** , um die Gitter Rendererkomponente zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-197">In the Hierarchy window, select the **PanGesture** object, then in the inspector **un-check** the **Mesh Renderer** checkbox to disable the Mesh Renderer component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

<span data-ttu-id="ad6e8-199">Wenn Sie jetzt den Spielmodus wechseln, können Sie den 3D-Inhalt mit der Schwenkbewegung in der in-Editor-Simulation testen:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-199">If you now enter Game mode, you can test scrolling the 3D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a><span data-ttu-id="ad6e8-201">Eyetracking</span><span class="sxs-lookup"><span data-stu-id="ad6e8-201">Eye Tracking</span></span>

<span data-ttu-id="ad6e8-202">In diesem Abschnitt erfahren Sie, wie Sie die Eye-Nachverfolgung in Ihrem Projekt aktivieren.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-202">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="ad6e8-203">In diesem Beispiel implementieren Sie die Funktionalität, damit jedes Objekt in der 3dobjectcollection langsam wird, während es durch den Augenblick des Benutzers betrachtet wird, und löst einen Unterbrechung-Effekt aus, wenn das zu überprüfende Objekt per Luftbild-oder Sprachbefehl ausgewählt wird.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-203">For this example, you will implement functionality to make each object in the 3DObjectCollection spin slowly while being looked at by the user's eye gaze, as well as, trigger a blip effect when the object being looked at is selected by air-tap or speech command.</span></span>

<span data-ttu-id="ad6e8-204">Dies sind die wichtigsten Schritte, die Sie durchführen müssen:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-204">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="ad6e8-205">Hinzufügen der Komponente "Augen Verfolgungs Ziel (Skript)" zu allen Ziel Objekten</span><span class="sxs-lookup"><span data-stu-id="ad6e8-205">Add the Eye Tracking Target (Script) component to all target objects</span></span>
2. <span data-ttu-id="ad6e8-206">Hinzufügen der "Eye Tracking Tutorial Demo (Skript)"-Komponente zu allen Ziel Objekten</span><span class="sxs-lookup"><span data-stu-id="ad6e8-206">Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>
3. <span data-ttu-id="ad6e8-207">Implementieren Sie bei der Betrachtung des Ziel Ereignisses.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-207">Implement the While Looking At Target event</span></span>
4. <span data-ttu-id="ad6e8-208">In ausgewähltem Ereignis implementieren</span><span class="sxs-lookup"><span data-stu-id="ad6e8-208">Implement the On Selected event</span></span>
5. <span data-ttu-id="ad6e8-209">Aktivieren der simulierten Augen Verfolgung für in-Editor-Simulationen</span><span class="sxs-lookup"><span data-stu-id="ad6e8-209">Enable simulated eye tracking for in-editor simulations</span></span>
6. <span data-ttu-id="ad6e8-210">Aktivieren von Blick Eingaben in den App-Funktionen des Visual Studio-Projekts</span><span class="sxs-lookup"><span data-stu-id="ad6e8-210">Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a><span data-ttu-id="ad6e8-211">1. Hinzufügen der Komponente "Augen Verfolgungs Ziel (Skript)" zu allen Ziel Objekten</span><span class="sxs-lookup"><span data-stu-id="ad6e8-211">1. Add the Eye Tracking Target (Script) component to all target objects</span></span>

<span data-ttu-id="ad6e8-212">Erweitern Sie im Fenster Hierarchie das **3dobjectcollection-** Objekt, und wählen Sie alle untergeordneten **Objekte**aus. verwenden Sie dann im Inspektor-Fenster die Schaltfläche **Komponente hinzufügen** , um die Komponente für das **Augen Verfolgungs Ziel (Skript)** allen untergeordneten Objekten hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-212">In the Hierarchy window, expand the **3DObjectCollection** object and select all the **child objects**, then in the Inspector window, use the **Add Component** button to add the **Eye Tracking Target (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

<span data-ttu-id="ad6e8-214">Wenn alle untergeordneten **Objekte** noch ausgewählt sind, konfigurieren Sie die Komponente für das **Augen Verfolgungs Ziel (Skript)** wie folgt:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-214">With all the **child objects** still selected, configure the **Eye Tracking Target (Script)** component as follows:</span></span>

* <span data-ttu-id="ad6e8-215">**Wählen Sie** die auszuführende Aktion aus, um die Air-Tap-Aktion für dieses Objekt als SELECT- **Aktion zu definieren**.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-215">Change **Select Action** to **Select**, to define the air-tap action for this object as Select</span></span>
* <span data-ttu-id="ad6e8-216">Erweitern **Sie Sprachauswahl** , und legen Sie die sprach Befehlslisten **Größe** auf 1 fest. ändern Sie dann in der angezeigten Liste neues Element die Option **0** **, um die**sprach Befehls Aktion für dieses Objekt als SELECT-Aktion zu definieren.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-216">Expand **Voice Select** and set the voice command list **Size** to 1, and then, in the new element list that appear, change **Element 0** to **Select**, to define the speech command action for this object as Select</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a><span data-ttu-id="ad6e8-218">2. Hinzufügen der "Eye Tracking Tutorial Demo (Skript)"-Komponente zu allen Ziel Objekten</span><span class="sxs-lookup"><span data-stu-id="ad6e8-218">2. Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>

<span data-ttu-id="ad6e8-219">Wenn alle untergeordneten **Objekte** noch ausgewählt sind, fügen Sie mithilfe der Schaltfläche **Komponente hinzufügen** die Komponente " **Eye Tracking Tutorial Demo (Script)** " allen untergeordneten Objekten hinzu:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-219">With all the **child objects** still selected, use the **Add Component** button to add the **Eye Tracking Tutorial Demo (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> <span data-ttu-id="ad6e8-221">Die Komponente für die Augen Verfolgungs Ziel (Skript) ist nicht Bestandteil von mrtk.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-221">The Eye Tracking Target (Script) component is not part of MRTK.</span></span> <span data-ttu-id="ad6e8-222">Es wurde mit den Assets dieses Tutorials bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-222">It was provided with this tutorial's assets.</span></span>

### <a name="3-implement-the-while-looking-at-target-event"></a><span data-ttu-id="ad6e8-223">3. implementieren Sie bei der Betrachtung des Ziel Ereignisses.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-223">3. Implement the While Looking At Target event</span></span>

<span data-ttu-id="ad6e8-224">Wählen Sie im Fenster Hierarchie das **Käse** Objekt aus, und erstellen Sie ein neues, während Sie das **Ziel Ereignis () ansehen** , das **Käse** Objekt so konfigurieren, dass es das Ereignis empfängt, und " **eyetrackingtutorialdemo. rotatetarget** " als Aktion definieren, die ausgelöst werden soll:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-224">In the Hierarchy window, select the **Cheese** object, then create a new **While Looking At Target ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

<span data-ttu-id="ad6e8-226">**Wiederholen** Sie diesen Vorgang für jedes untergeordnete Objekt in der 3dobjectcollection.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-226">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

> [!TIP]
> <span data-ttu-id="ad6e8-227">Eine Erinnerung, wie Ereignisse implementiert werden können, finden Sie in den Anweisungen [Hand Tracking Gesten und Interaktionen Buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) .</span><span class="sxs-lookup"><span data-stu-id="ad6e8-227">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="4-implement-the-on-selected-event"></a><span data-ttu-id="ad6e8-228">4. implementieren Sie für das ausgewählte Ereignis.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-228">4. Implement the On Selected event</span></span>

<span data-ttu-id="ad6e8-229">Wählen Sie im Fenster Hierarchie das Objekt **Käse** aus, und erstellen Sie dann ein neues **auf ausgewähltes Ereignis ()** , konfigurieren Sie das **Käse** Objekt, um das Ereignis zu empfangen, und definieren Sie " **eyetrackingtutorialdemo. bliptarget** " als Aktion, die ausgelöst werden soll:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-229">In the Hierarchy window, select the **Cheese** object, then create a new **On Selected ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.BlipTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

<span data-ttu-id="ad6e8-231">**Wiederholen** Sie diesen Vorgang für jedes untergeordnete Objekt in der 3dobjectcollection.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-231">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a><span data-ttu-id="ad6e8-232">5. Aktivieren der simulierten Augen Verfolgung für in-Editor-Simulationen</span><span class="sxs-lookup"><span data-stu-id="ad6e8-232">5. Enable simulated eye tracking for in-editor simulations</span></span>

<span data-ttu-id="ad6e8-233">Wählen Sie im Fenster Hierarchie das **mixedrealitytoolkit** -Objekt aus, und wählen Sie dann im Inspektor-Fenster die Registerkarte **Eingabe** aus, erweitern Sie den Abschnitt **Eingabedaten Anbieter** und dann den Abschnitt **Input Simulation Service** , und Klonen Sie das **defaultmixedrealityinputsimulationprofile** -Objekt, um es durch ihr eigenes anpassbares **Eingabe Simulations Profil**zu ersetzen:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-233">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab, expand the **Input Data Providers** section and then the **Input Simulation Service** section, and clone the **DefaultMixedRealityInputSimulationProfile** to replace it with your own customizable **Input Simulation Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> <span data-ttu-id="ad6e8-235">Eine Erinnerung zum Klonen von mrtk-Profilen finden Sie unter [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-235">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="ad6e8-236">Aktivieren Sie im Abschnitt **Eye Simulation** das Kontrollkästchen **Augen Position simulieren** , um die Augen Verfolgungs Simulation zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-236">In the **Eye Simulation** section, check the **Simulate Eye Position** checkbox to enable eye tracking simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

<span data-ttu-id="ad6e8-238">Wenn Sie nun in den Spielmodus wechseln, können Sie die von Ihnen implementierten Spin-und Unterbrechung-Effekte testen, indem Sie die Ansicht so anpassen, dass der Cursor auf eines der Objekte trifft, und mithilfe von Hand Interaktion oder Sprachbefehl das Objekt auswählen:</span><span class="sxs-lookup"><span data-stu-id="ad6e8-238">If you now enter Game mode, you can test the spin and blip effects you implemented by adjusting the view so the cursor hits one of the objects and using hand interaction or speech command to select the object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> <span data-ttu-id="ad6e8-240">Wenn Sie die DefaultHoloLens2ConfigurationProfile nicht zum Klonen Ihres anpassbaren mrtk-Konfigurations Profils verwendet haben, wie in den Anweisungen zum [Konfigurieren des Mixed Reality-Toolkits](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) beschrieben, ist die Eye-Nachverfolgung in Ihrem Projekt möglicherweise nicht aktiviert und muss aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-240">If you did not use the DefaultHoloLens2ConfigurationProfile to clone your customizable MRTK configuration profile, as instructed in the [Configure the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) instructions, eye tracking may not be enable in your project and will need to be enabled.</span></span> <span data-ttu-id="ad6e8-241">Hierzu finden Sie die Anweisungen unter " [Getting Started with Eye Tracking" in mrtk](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) .</span><span class="sxs-lookup"><span data-stu-id="ad6e8-241">For that, you can refer to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions.</span></span>

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a><span data-ttu-id="ad6e8-242">6. Aktivieren Sie die Blick Eingabe in den App-Funktionen des Visual Studio-Projekts.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-242">6. Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

<span data-ttu-id="ad6e8-243">Bevor Sie Ihre APP aus Visual Studio auf Ihrem Gerät entwickeln und bereitstellen können, müssen Sie in den App-Funktionen des Projekts die Option "Blick Eingaben" aktivieren.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-243">Before building and deploying your app from Visual Studio to your device, Gaze Input has to been enabled in the project's app capabilities.</span></span> <span data-ttu-id="ad6e8-244">Hierfür können Sie die Anweisungen unter [Testen Ihrer Unity-App auf hololens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) befolgen.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-244">For this, you can follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="ad6e8-245">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="ad6e8-245">Congratulations</span></span>

<span data-ttu-id="ad6e8-246">Sie haben der Anwendung erfolgreich grundlegende Funktionen zur Auge Verfolgung hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-246">You have successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="ad6e8-247">Diese Aktionen stellen nur den Einstieg in eine ganze Welt der Möglichkeiten mit Eyetracking dar.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-247">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="ad6e8-248">In diesem Tutorial haben Sie auch weitere erweiterte Eingabe Features kennengelernt, wie z. b. Sprachbefehle und Schwenk Gesten.</span><span class="sxs-lookup"><span data-stu-id="ad6e8-248">In this tutorial, you also learned about other advanced input features, such as voice commands and panning gestures.</span></span>

[<span data-ttu-id="ad6e8-249">Nächste Lektion: 7. Erstellen einer Beispielanwendung für ein Mond Modul</span><span class="sxs-lookup"><span data-stu-id="ad6e8-249">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)
