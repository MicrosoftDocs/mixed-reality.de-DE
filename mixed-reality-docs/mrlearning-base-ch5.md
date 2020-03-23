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
# <a name="6-exploring-advanced-input-options"></a>6. Untersuchen erweiterter Eingabeoptionen

In diesem Tutorial werden einige erweiterte Eingabeoptionen für HoloLens 2 vorgestellt, z. B. Sprachbefehle, Schwenkgesten und Eyetracking.

## <a name="objectives"></a>Ziele

* Auslösen von Ereignissen mit Sprachbefehlen und Schlüsselwörtern
* Verwenden von Handtracking, um mit nachverfolgten Händen Strukturen und 3D-Objekte zu schwenken
* Nutzen der Eyetracking-Funktion von HoloLens 2 zum Auswählen von Objekten

## <a name="enabling-voice-commands"></a>Aktivieren der Sprachbefehle
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

In diesem Abschnitt implementieren Sie einen Sprachbefehl, um den Benutzer einen Soundeffekt für das Octa-Objekt wiedergeben zu lassen. Zu diesem Zweck erstellen Sie einen neuen Sprachbefehl und konfigurieren dann das Ereignis so, dass es die gewünschte Aktion auslöst, wenn das Schlüsselwort des Sprachbefehls ausgesprochen wird.

Dies sind die wichtigsten Schritte, die Sie durchführen müssen:

1. Klonen des Standardprofils des Eingabesystems
2. Klonen des Standardprofils der Spracherkennungsbefehle
3. Erstellen eines neuen Sprachbefehls
4. Hinzufügen und Konfigurieren der Komponente „Spracheingabehandler (Script)“
5. Implementieren des Antwortereignisses für den Sprachbefehl

### <a name="1-clone-the-default-input-system-profile"></a>1. Klonen des Standardprofils des Eingabesystems

Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt aus, wählen Sie dann im Inspektorfenster die Registerkarte **Eingabe** aus, und klicken Sie das **DefaultHoloLens2InputSystemProfile**, um es durch Ihr eigenes anpassbares **Eingabesystemprofil** zu ersetzen:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> Wenn Sie eine Auffrischung zum Klonen von MRTK-Profilen benötigen, lesen Sie die Anweisungen in [Konfigurieren des Mixed Reality-Toolkits](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option).

### <a name="2-clone-the-default-speech-commands-profile"></a>2. Klonen des Standardprofils der Spracherkennungsbefehle

Erweitern Sie den Abschnitt **Sprache**, und klonen Sie das **DefaultMixedRealitySpeechCommandsProfile**, um es durch Ihr eigenes **Profil der Spracherkennungsbefehle** zu ersetzen:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a>3. Erstellen eines neuen Sprachbefehls

Klicken Sie im Abschnitt **Spracherkennungsbefehle** auf die Schaltfläche **+ Add a New Speech Command** (Neuen Spracherkennungsbefehl hinzufügen), um unten in der Liste der vorhandenen Spracherkennungsbefehle einen neuen Spracherkennungsbefehl hinzuzufügen, und geben Sie dann im Feld **Schlüsselwort** ein passendes Wort oder einen passenden Ausdruck ein, beispielsweise **Musik abspielen**:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> Wenn Ihr Computer nicht über ein Mikrofon verfügt und Sie den Sprachbefehl mithilfe der in den Editor integrierten Simulation testen möchten, können Sie dem Sprachbefehl einen Tastaturcode hinzufügen, mit dessen Hilfe Sie ihn auslösen können, wenn die entsprechende Taste gedrückt wird.

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a>4. Hinzufügen und Konfigurieren der Komponente „Spracheingabehandler (Script)“

Wählen Sie im Hierarchiefenster das **Octa**-Objekt aus, und fügen Sie ihm die Komponente **Spracheingabehandler (Script)** hinzu. Deaktivieren Sie dann das Kontrollkästchen **Is Focus Required** (Fokus erforderlich), damit der Benutzer nicht auf das Octa-Objekt blicken muss, um den Sprachbefehl auszulösen:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a>5. Implementieren des Antwortereignisses für den Sprachbefehl

Klicken Sie auf der Komponente „Spracheingabehandler (Script)“ auf die kleine **+** -Schaltfläche, um der Liste der Schlüsselwörter ein Schlüsselwortelement hinzuzufügen:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

Klicken Sie auf das neu erstellte **Element 0**, um es zu erweitern, und wählen Sie dann in der **Schlüsselwort**-Dropdownliste das Schlüsselwort **Musik abspielen** aus, das Sie zuvor erstellt hatten:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> Die Schlüsselwörter in der Dropdownliste „Schlüsselwort“ werden aus den Schlüsselwörtern aufgefüllt, die in der Liste der Sprachbefehle im Profil der Spracherkennungsbefehle definiert sind.

Erstellen Sie ein neues **Response ()** -Ereignis, konfigurieren Sie das **Octa**-Objekt, um das Ereignis zu empfangen, definieren Sie **AudioSource.PlayOneShot** als die auszulösende Aktion, und weisen Sie dem Feld **Audioclip** einen passenden Audioclip zu, beispielsweise den Audioclip „MRTK_Gem“:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> Wenn Sie eine Auffrischung zum Implementieren von Ereignissen und Zuweisen von Audioclips wünschen, lesen Sie die Anweisungen in [Implementieren des „On Touch Started“-Ereignisses](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event).

## <a name="the-pan-gesture"></a>Die Geste „Schwenken“

Die Schwenkgeste ist nützlich, um mithilfe eines Fingers oder der Hand durch Inhalte zu scrollen. In diesem Beispiel erfahren Sie zunächst, wie Sie auf einer 2D-Benutzeroberfläche scrollen und anschließend darauf aufbauen, um das Scrollen durch eine Sammlung von 3D-Objekten zu erlernen.

Dies sind die wichtigsten Schritte, die Sie durchführen müssen:

1. Erstellen eines Quad-Objekts, das zum Schwenken verwendet werden kann
2. Hinzufügen der Komponente „Near Interaction touchable“ (Nah-Interaktion, berührbar)
3. Hinzufügen der Komponente „Hand Interaction Pan Zoom (Script)“ (Handinteraktion Zoomen/Schwenken (Skript))
4. Hinzufügen von 2D-Inhalten zum Scrollen
5. Hinzufügen von 3D-Inhalten zum Scrollen
6. Hinzufügen der Komponente „Move With Pan (Script)“ (Mit Schwenken bewegen (Skript))

> [!NOTE]
> Die Komponente „Move With Pan (Script)“ ist nicht Teil des MRTK. Sie wurde zusammen mit den Ressourcen für dieses Tutorial zur Verfügung gestellt.

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a>1. Erstellen eines Quad-Objekts, das zum Schwenken verwendet werden kann

Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf einen leeren Bereich, und wählen Sie **3D-Objekt** > **Quad** aus, um Ihrer Szene ein Quad-Objekt hinzuzufügen. Geben Sie ihm einen passenden Namen, beispielsweise **PanGesture**, und positionieren Sie es an einer passenden Stelle, beispielsweise an X = 0, Y = -0,2, Z = 2.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> Wenn Sie eine Auffrischung zum Hinzufügen von Unity-Primitiven benötigen, wie etwa einem 3D-Quad-Objekt, lesen Sie die Anweisungen unter [Hinzufügen eines Würfels zur Szene](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene).

Wie jede andere Interaktion erfordert auch die Schwenkgeste einen Collider. Standardmäßig weist ein Quad-Objekt einen Gittermodell-Collider auf. Der Gittermodell-Collider ist jedoch nicht ideal, da er äußerst schmal ist. Um dem Benutzer die Interaktion mit dem Collider zu vereinfachen, ersetzen wir den Gittermodell-Collider durch einen Feld-Collider.

Klicken Sie bei immer noch ausgewähltem PanGesture-Objekt auf das Symbol **Einstellungen** der **Gittermodell-Collider**-Komponente, und wählen Sie **Komponente entfernen** aus, um den Gittermodell-Collider zu entfernen:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

Verwenden Sie im Inspektorfenster die Schaltfläche **Komponente hinzufügen** aus, um einen **Feld-Collider** hinzuzufügen, und ändern Sie dann die **Größe** Z des Feld-Colliders in 0,15, um die Dicke des Feld-Colliders zu erhöhen:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a>2. Hinzufügen der Komponente „Near Interaction touchable (Script)“ (Nah-Interaktion, berührbar (Skript))

Fügen Sie bei noch ausgewähltem **PanGesture**-Objekt dem PanGesture-Objekt die Komponente **Near Interaction Touchable (Script)** (Nah-Interaktion, berührbar (Skript)) hinzu, und klicken Sie dann auf die Schaltflächen **Fix Bounds** (Begrenzungen fixieren) und **Fix Center** (Mitte fixieren), um die Eigenschaften „Local Center“ und „Bounds“ von Near Interaction Touchable (Script) so zu aktualisieren, dass sie mit dem Feld-Collider übereinstimmen:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a>3. Hinzufügen der Komponente „Hand Interaction Pan Zoom (Script)“ (Handinteraktion Zoomen/Schwenken (Skript))

Fügen Sie bei immer noch ausgewähltem **PanGesture**-Objekt die Komponente **Hand Interaction Pan Zoom (Script)** (Handinteraktion Zoomen/Schwenken (Skript)) zum PanGesture-Objekt hinzu, und aktivieren Sie dann das Kontrollkästchen **Lock Horizontal** (Horizontal sperren), um nur vertikales Scrollen zuzulassen:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a>4. Hinzufügen von 2D-Inhalten zum Scrollen

Suchen Sie im Bereich „Projekt“ nach dem **PanContent**-Material, und bewegen Sie es dann durch Klicken und Ziehen auf die Eigenschaft **Material** Element 0 des Gittermodell-Renderers des **PanGesture**-Objekts:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

Erweitern Sie im Inspektorfenster die neu hinzugefügte **PanContent**-Materialkomponente, und ändern Sie dann ihren Y-Wert für **Tiling** (Anordnung) auf 0,5, sodass er dem X-Wert entspricht und die Kachel quadratisch angezeigt wird:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

Wenn Sie jetzt in den Spielemodus wechseln, können Sie das Scrollen von 2D-Inhalten mithilfe der Schwenkgeste in der Editor-Simulation testen:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a>5. Hinzufügen von 3D-Inhalten zum Scrollen

Sie müssen im Hierarchiefenster **vier Würfel erstellen**, als untergeordnete Objekte des **PanGesture**-Objekts, deren Transformations-**Maßstab** Sie auf X = 0,15, Y = 0,15 und Z = 0,15 festlegen:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

Um die Würfel gleichmäßig anzuordnen und Zeit zu sparen, fügen Sie die Komponente **Grid Object Collection (Script)** (Rasterobjektsammlung (Skript)) dem übergeordneten Objekt der Würfel hinzu, d. h. zum **PanGesture**-Objekt, und konfigurieren SIe die Rasterobjektsammlung (Skript) wie folgt:

* Ändern Sie **Num Rows** (Anzahl Zeilen) in 1, um alle Würfel in einer einzelnen Zeile auszurichten
* Ändern Sie **Cell Width**  (Zellbreite) in 0,25, um die Würfel innerhalb der Zeile zu verteilen

Klicken Sie dann auf die Schaltfläche **Sammlung aktualisieren**, um die neue Konfiguration zu übernehmen:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a>6. Hinzufügen der Komponente „Move With Pan (Script)“ (Mit Schwenken bewegen (Skript))

Wählen Sie im Hierarchiefenster alle **Cube child objects** (Untergeordneten Würfelobjekte) aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um allen Würfeln die Komponente **Move With Pan (Script)** hinzuzufügen:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> Falls Sie eine Auffrischung zum Auswählen mehrerer Objekte im Hierarchiefenster benötigen, lesen Sie die Anweisungen unter [Add the Manipulation Handler (Script) component to all the objects](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) (Hinzufügen der Komponente „Manipulationshandler (Skript)“ zu sämtlichen Objekten).

Bewegen Sie das **PanGesture**-Objekt mittels Klicken und Ziehen auf das Feld **Pan Input Source** (Quelle der Schwenkeingabe), wobei alle Würfel immer noch ausgewählt sein müssen:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> Die Komponente „Move With Pan (Script)“ (Mit Schwenken bewegen (Skript)) auf jedem der Würfel lauscht nach dem Pan Updated-Ereignis (Schwenk aktualisiert), das von der HandInteractionPanZoom (Script)-Komponente auf dem PanGesture-Objekt gesendet wird, das Sie im Schritt oben als Eingabequelle für den Schwenk zugewiesen haben, und aktualisiert die Position jedes Würfels entsprechend.

Wählen Sie im Hierarchiefenster das **PanGesture**-Objekt aus, und **deaktivieren** Sie dann im Inspektor das Kontrollkästchen **Mesh Renderer** (Gittermodell-Renderer), um die Mesh Renderer-Komponente zu deaktivieren:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

Wenn Sie jetzt in den Spielemodus wechseln, können Sie das Scrollen von 3D-Inhalten mithilfe der Schwenkgeste in der Editor-Simulation testen:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a>Eyetracking

In diesem Abschnitt wird erläutert, wie Sie das Eyetracking in Ihrem Projekt aktivieren. Für dieses Beispiel implementieren Sie Funktionalität, um jedes Objekt in der 3DObjectCollection langsam rotieren zu lassen, während es durch das Auge des Benutzers anvisiert wird, sowie ein Aufleuchten auszulösen, wenn das anvisierte Objekt durch eine Tippbewegung in die Luft oder durch einen Sprachbefehl ausgewählt wird.

Dies sind die wichtigsten Schritte, die Sie durchführen müssen:

1. Hinzufügen der Komponente „ Eye Tracking Target (Script)“ (Blickverfolgungsziel (Skript)) zu allen Zielobjekten
2. Hinzufügen der Komponente „ Eye Tracking Tutorial Demo (Script)“ (Blickverfolgung-Tutorialdemo (Skript)) zu allen Zielobjekten
3. Implementieren des While Looking At Target-Ereignisses (Beim Ansehen des Ziels)
4. Implementieren des On Selected-Ereignisses (Bei Auswahl)
5. Aktivieren von simulierter Blickverfolgung für Simulationen im Editor
6. Aktivieren der Eingabe durch Anvisieren in den App-Funktionen des Visual Studio-Projekts

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a>1. Hinzufügen der Komponente „ Eye Tracking Target (Script)“ (Blickverfolgungsziel (Skript)) zu allen Zielobjekten

Erweitern Sie im Hierarchiefenster das **3DObjectCollection**-Objekt, und wählen Sie alle **untergeordneten Objekte** aus, verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um allen untergeordneten Objekten die **Eye Tracking Target (Script)** -Komponente hinzuzufügen:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

Konfigurieren Sie die **Eye Tracking Target (Script)** -Komponente wie folgt, während alle **untergeordneten Objekte** noch ausgewählt sind:

* Ändern Sie **Aktion auswählen** in **Auswählen**, um die Aktion des Tippens in die Luft für dieses Objekt als Auswählen zu definieren
* Erweitern Sie **Voice Select** (Sprachauswahl), und legen Sie die **Größe** der Sprachbefehlsliste auf 1 fest. Ändern Sie dann in der nun angezeigten Liste der neuen Elemente **Element 0** in **Select** (Auswählen), um die Sprachbefehlsaktion für dieses Objekt als Auswählen zu definieren

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a>2. Hinzufügen der Komponente „ Eye Tracking Tutorial Demo (Script)“ (Blickverfolgung-Tutorialdemo (Skript)) zu allen Zielobjekten

Verwenden Sie die Schaltfläche **Komponente hinzufügen**, während alle **untergeordneten Objekte** immer noch ausgewählt sind, um den untergeordneten Objekten die Komponente **Eye Tracking Tutorial Demo (Script)** hinzuzufügen:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> Die Komponente „Eye Tracking Target (Script)“ ist kein Teil des MRTK. Sie wurde zusammen mit den Ressourcen für dieses Tutorial zur Verfügung gestellt.

### <a name="3-implement-the-while-looking-at-target-event"></a>3. Implementieren des While Looking At Target-Ereignisses (Beim Ansehen des Ziels)

Wählen Sie im Hierarchiefenster das **Cheese**-Objekt (Käse), erstellen Sie dann ein neues **While Looking At Target ()** -Ereignis, konfigurieren Sie das **Cheese**-Objekt dafür, das Ereignis zu empfangen, und definieren Sie **EyeTrackingTutorialDemo.RotateTarget** als auszulösende Aktion:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

**Wiederholen** Sie diesen Vorgang für jedes der untergeordneten Objekte in der 3DObjectCollection.

> [!TIP]
> Falls Sie eine Auffrischung zum Implementieren von Ereignissen benötigen, lesen Sie die Anweisungen unter [Gesten für Handtracking und interaktionsfähige Schaltflächen](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).

### <a name="4-implement-the-on-selected-event"></a>4. Implementieren des On Selected-Ereignisses (Bei Auswahl)

Wählen Sie im Hierarchiefenster das **Cheese**-Objekt (Käse) aus, erstellen Sie dann ein neues **On Selected ()** -Ereignis, konfigurieren Sie das **Cheese**-Objekt dafür, das Ereignis zu empfangen, und definieren Sie **EyeTrackingTutorialDemo.BlipTarget** als auszulösende Aktion:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

**Wiederholen** Sie diesen Vorgang für jedes der untergeordneten Objekte in der 3DObjectCollection.

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a>5. Aktivieren von simulierter Blickverfolgung für Simulationen im Editor

Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt aus, wählen Sie dann im Inspektorfenster die Registerkarte **Eingabe** aus, erweitern Sie den Abschnitt **Input Data Providers** (Eingabedatenanbieter), dann den Abschnitt **Input Simulation Service** (Eingabesimulationsdienst), und klonen Sie das **DefaultMixedRealityInputSimulationProfile**, um es durch Ihr eigenes anpassbares **Input Simulation Profile** (Eingabesimulationsprofil) zu ersetzen:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> Wenn Sie eine Auffrischung zum Klonen von MRTK-Profilen benötigen, lesen Sie die Anweisungen in [Konfigurieren des Mixed Reality-Toolkits](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option).

Aktivieren Sie im Abschnitt **Eye Simulation** (Augensimulation) das Kontrollkästchen **Simulate Eye Position** (Augenposition simulieren), um die Blickverfolgungssimulation zu aktivieren:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

Wenn Sie jetzt in den Spielmodus wechseln, können Sie die Rotations- und die Leuchteffekte testen, die Sie implementiert haben, indem Sie die Ansicht so anpassen, dass der Cursor auf eins der Objekte trifft und Handinteraktion oder einen Sprachbefehl verwenden, um das Objekt auszuwählen:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> Wenn Sie nicht das DefaultHoloLens2ConfigurationProfile zum Klonen Ihres anpassbaren MRTK-Konfigurationsprofils verwendet haben, wie in den Anweisungen zum [Konfigurieren des Mixed Reality-Toolkits](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) gefordert, steht die Blickverfolgung in Ihrem Projekt möglicherweise nicht zur Verfügung und muss aktiviert werden. Lesen Sie zu diesem Zweck die Anweisungen unter [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) (Erste Schritte mit der Blickverfolgung in MRTK).

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a>6. Aktivieren der Eingabe durch Anvisieren in den App-Funktionen des Visual Studio-Projekts

Bevor Sie Ihre Anwendung erstellen und aus Visual Studio auf Ihrem Gerät bereitstellen, muss Eingabe durch Anvisieren in den Funktionen Ihrer Projekt-App aktiviert werden. Zu diesem Zweck können Sie die Anweisungen unter [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) (Testen Ihrer Unity-App an einer HoloLens 2) befolgen.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben Ihrer Anwendung erfolgreich grundlegende Eyetracking-Funktionen hinzugefügt. Diese Aktionen stellen nur den Einstieg in eine ganze Welt der Möglichkeiten mit Eyetracking dar. In diesem Tutorial haben Sie außerdem einiges über weitere erweiterte Eingabefunktionen erfahren, wie etwa Sprachbefehle und Schwenkgesten.

[Nächste Lektion: 7. Erstellen einer Beispielanwendung für eine Mondlandefähre (Lunar Module)](mrlearning-base-ch6.md)
