---
title: 'Tutorials zu den ersten Schritten: 6. Untersuchen von erweiterten Eingabeoptionen'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 18bcbc95746a2e66b88d83f279603aa7f171bbcb
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129661"
---
# <a name="6-exploring-advanced-input-options"></a>6. untersuchen erweiterter Eingabeoptionen

In diesem Tutorial werden einige erweiterte Eingabeoptionen für hololens 2 untersucht, einschließlich der Verwendung von Sprachbefehlen, der Schwenkbewegung und der Eye-Nachverfolgung.

## <a name="objectives"></a>Ziele

* Ereignisse mithilfe von Sprachbefehlen und Schlüsselwörtern Auslösers
* Verwenden von nach verfolgten Händen zum Schwenken von Texturen und 3D-Objekten mit nach verfolgten Händen
* Verwenden von hololens 2 Eye Tracking-Funktionen zum Auswählen von Objekten

## <a name="enabling-voice-commands"></a>Aktivieren der Sprachbefehle
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

In diesem Abschnitt implementieren Sie einen Sprachbefehl, mit dem Benutzer einen Sound für das Octa-Objekt abspielen können. Hierfür erstellen Sie einen neuen Sprachbefehl und konfigurieren dann das Ereignis, sodass die gewünschte Aktion ausgelöst wird, wenn das sprach Befehls Schlüsselwort gesprochen wird.

Dies sind die wichtigsten Schritte, die Sie durchführen müssen:

1. Klonen des standardmäßigen Eingabe System Profils
2. Klonen des standardmäßigen Sprach Befehls Profils
3. Neuen Sprachbefehl erstellen
4. Hinzufügen und Konfigurieren der Spracheingabe Handler-Komponente (Skript)
5. Implementieren Sie das Antwort Ereignis für den Sprachbefehl.

### <a name="1-clone-the-default-input-system-profile"></a>1. Klonen Sie das standardmäßige Eingabe System Profil.

Wählen Sie im Fenster Hierarchie das **mixedrealitytoolkit** -Objekt aus, wählen Sie im Inspektor-Fenster die Registerkarte **Eingabe** aus, und Klonen Sie das **DefaultHoloLens2InputSystemProfile** , um es durch ihr eigenes anpassbares **Eingabe System Profil**zu ersetzen:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> Eine Erinnerung zum Klonen von mrtk-Profilen finden Sie unter [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.

### <a name="2-clone-the-default-speech-commands-profile"></a>2. Klonen Sie das Standardprofil für Sprachbefehle.

Erweitern Sie den Abschnitt **sprach** Ausgabe, und Klonen Sie die **Datei defaultmixedrealitysprechcommandsprofile** , um Sie durch ihr eigenes **Profil für Sprachbefehle**zu ersetzen:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a>3. Erstellen eines neuen sprach Befehls

Klicken Sie im Abschnitt **Sprachbefehle** auf die Schaltfläche **+ neuen Sprachbefehl hinzufügen** , um am Ende der Liste vorhandener Sprachbefehle einen neuen Sprachbefehl hinzuzufügen, und geben Sie dann im **Schlüsselwort** ein passendes Wort oder einen Ausdruck ein, z. b. **Abspielen von Musik**:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> Wenn Ihr Computer nicht über ein Mikrofon verfügt und Sie den Sprachbefehl mithilfe der in-Editor-Simulation testen möchten, können Sie dem Sprachbefehl einen Keycode zuweisen, mit dem Sie ihn beim Drücken der entsprechenden Taste auslassen können.

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a>4. hinzufügen und Konfigurieren der Spracheingabe Handler-Komponente (Skript)

Wählen Sie im Fenster Hierarchie das **Octa** -Objekt aus, und fügen Sie die Komponente **Spracheingabe Handler (Skript)** dem Octa-Objekt hinzu. Deaktivieren Sie dann das Kontrollkästchen mit dem **Fokus ist erforderlich** , damit der Benutzer das Octa-Objekt nicht überprüfen muss, um den Sprachbefehl zu starten:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a>5. implementieren Sie das Antwort Ereignis für den Sprachbefehl.

Klicken Sie auf die Schaltfläche Small **+** (Skript) für Spracheingabe Handler (Skript), um ein Schlüsselwort hinzuzufügen, und wählen Sie dann aus der Dropdown Liste **Schlüsselwort** das **Wiedergabe Musik** Schlüsselwort aus, das Sie zuvor erstellt haben

![mrlearning: Basis](images/mrlearning-base/tutorial5-section1-step5-1.png)

> [!NOTE]
> Die Schlüsselwörter in der Dropdown Liste für Schlüsselwörter werden basierend auf den Schlüsselwörtern aufgefüllt, die in der Liste der Sprachbefehle im Profil für Sprachbefehle definiert sind.

Erstellen Sie ein neues **Response ()** -Ereignis, konfigurieren Sie das **Octa** -Objekt für den Empfang des Ereignisses, definieren Sie **audiosource. playoneshot** als auszulösenden Aktion, und weisen Sie dem **Audioclip** -Feld einen passenden Audioclip zu, z. b. den MRTK_Gem Audioclip:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!TIP]
> Eine Erinnerung zum Implementieren von Ereignissen und zum Zuweisen eines Audioclips finden Sie in der Anleitung zum [Implementieren der on](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) -Finger Eingaben.

## <a name="the-pan-gesture"></a>Die Geste „Schwenken“

Mit der Schwenkbewegung können Sie einen Bildlauf durchführen, indem Sie mit dem Finger oder der Hand einen Bildlauf durchführen In diesem Beispiel erfahren Sie zunächst, wie Sie einen Bildlauf für eine 2D-Benutzeroberfläche durchführen und dann darauf erweitern, um durch eine Auflistung von 3D-Objekten scrollen zu können.

Dies sind die wichtigsten Schritte, die Sie durchführen müssen:

1. Erstellen eines Quad-Objekts, das zum Schwenken verwendet werden kann
2. Hinzufügen der Near-interaktionstouchable-Komponente (Skript)
3. Fügen Sie die Komponente "Hand Interaktion schwenken Zoom (Skript)" hinzu.
4. 2D-Inhalt zum durch Scrollen hinzufügen
5. Hinzufügen von 3D-Inhalt für den scrollt
6. Hinzufügen der Komponente "mit Pan (Skript) verschieben"

> [!NOTE]
> Die Komponente "mit Pan verschieben (Skript)" ist nicht Bestandteil von mrtk. Es wurde mit den Assets dieses Tutorials bereitgestellt.

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a>1. Erstellen eines Quad-Objekts, das zum Schwenken verwendet werden kann

Klicken Sie im Hierarchie Fenster mit der rechten Maustaste auf einen leeren Bereich, und wählen Sie **3D-Objekt** > **Quad** aus, um der Szene ein vierfache hinzuzufügen. Geben Sie ihm einen passenden Namen, z. b. **pangesture**, und positionieren Sie ihn an einem geeigneten Speicherort, z. b. X = 0, Y =-0,2, Z = 2.

![mrlearning: Basis](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> Eine Erinnerung zum Hinzufügen von Unity-primitiven, z. b. ein 3D-Quad, zu Ihrer Szene, finden Sie in der Anleitung zum [Hinzufügen eines Cubes zu einer Szene](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) .

Wie bei jeder anderen Interaktion erfordert auch die schwenken-Bewegung einen Collider. Standardmäßig weist ein Quad einen Mesh-Collider auf. Der Mesh-Collider ist jedoch nicht ideal, da er äußerst dünn ist. Um dem Benutzer die Interaktion mit dem Collider zu vereinfachen, ersetzen wir den Mesh Collider durch einen Box Collider.

Wenn das pangesture-Objekt noch ausgewählt ist, klicken Sie auf das **Einstellungs** Symbol der **Mesh Collider** -Komponente, und wählen Sie **Komponente entfernen** aus, um den Mesh Collider zu entfernen:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section2-step1-2.png)

Verwenden Sie im Inspektor-Fenster die Schaltfläche **Komponente hinzufügen** , um einen **Box-Collider**hinzuzufügen, und ändern Sie dann die **Größe** des Kontrollkästchens von Z in 0,15, um die Stärke des boxcollider zu erhöhen:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a>2. Hinzufügen der touchable-Komponente (Skript) für die Near-Interaktion

Wenn das **pangesture** -Objekt noch ausgewählt ist, fügen Sie dem pangesture-Objekt die touchable-Komponente der **near-Interaktion (Script)** hinzu, und klicken Sie dann auf die Schaltflächen **fixbegrenzungen** und **Fix Center** , um die Eigenschaften des lokalen Centers und der Begrenzungen der Near-interaktionstouchable (Script) zu aktualisieren, die mit boxcollider

![mrlearning: Basis](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a>3. Fügen Sie die Komponente "Hand Interaktion schwenken Zoom (Skript)" hinzu.

Wenn das **pangesture** -Objekt noch ausgewählt ist, fügen Sie dem pangesture-Objekt die Komponente " **Hand Interaktion schwenken schwenken (Skript)** " hinzu, und aktivieren Sie dann das Kontrollkästchen " **Horizontal Sperren** ", um nur vertikales Scrollen zuzulassen:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a>4. Hinzufügen von 2D-Inhalt für den scrollt

Suchen Sie im Projekt Panel nach dem **Inhalt von pancontent** , und klicken Sie darauf, und ziehen Sie es auf die Eigenschaft Mesh Renderer **Material** Element 0 des **pangesture** -Objekts:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section2-step4-1.png)

Erweitern Sie im Inspektor-Fenster die neu hinzugefügte Komponente " **pancontent** -Material", und ändern Sie den Y-Wert in 0,5, sodass er mit dem **X-Wert** übereinstimmt und die Kacheln im Quadrat angezeigt werden:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section2-step4-2.png)

Wenn Sie jetzt den Spielmodus wechseln, können Sie den 2D-Inhalt mit der Schwenkbewegung in der in-Editor-Simulation testen:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a>5. Hinzufügen von 3D-Inhalt für den scrollt

Erstellen Sie im Hierarchie Fenster **vier Cubes** als untergeordnete Objekte von **pancontent** , und legen Sie Ihre Transformations **Skala** auf X = 0,15, Y = 0,15, Z = 0,15 fest:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section2-step5-1.png)

Um die Cubes gleichmäßig zu verteilen und einige Zeit zu sparen, fügen Sie dem übergeordneten Objekt des Cubes, d. h. dem pangesture-Objekt, die Raster Objekt Auflistungs Komponente (Skript) hinzu, und konfigurieren Sie die Raster Objekt Auflistung (Skript) wie folgt:

* Ändern von **num-Zeilen** in 1, damit alle Cubes an einer einzelnen Zeile ausgerichtet sind
* Ändern Sie die **Zellen Breite** in 0,25, um die Cubes innerhalb der Zeile leer zu legen.

Klicken Sie dann auf die Schaltfläche **Sammlung aktualisieren** , um die neue Konfiguration zu übernehmen:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a>6. Hinzufügen der Komponente "mit Pan (Skript) verschieben"

Wählen Sie im Fenster Hierarchie die Option alle untergeordneten **Cube-Objekte**aus, und verwenden Sie dann im Inspektor-Fenster die Schaltfläche **Komponente hinzufügen** , um die Komponente zum **Verschieben mit schwenken (Skript)** zu allen Cubes hinzuzufügen:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> Zur Erinnerung, wie mehrere Objekte im Hierarchie Fenster ausgewählt werden, kann tou auf die [Komponente hinzufügen der Bearbeitungs Handlers (Skript) zu allen Objekt](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) Anweisungen verweisen.

Wenn alle Cubes noch ausgewählt sind, klicken Sie auf das **pangesture** -Objekt, und ziehen Sie es in das Feld **Eingabe Quelle schwenken** :

![mrlearning: Basis](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> Die Komponente "mit Pan verschieben (Skript)" auf jedem Cube überwacht das von der Komponente "handinteraktionpanzoom (Skript)" auf dem pangesture-Objekt gesendete Pan-aktualisierte Ereignis, das Sie im obigen Schritt als Eingabe Quelle "Pan" zugewiesen haben, und aktualisiert die Position jedes Cubes. entsprechende.

Wählen Sie im Fenster Hierarchie das **pangesture** -Objekt aus, und deaktivieren Sie dann im Inspektor das Kontrollkästchen **Gitter Renderer** , um die Gitter Rendererkomponente zu deaktivieren:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section2-step6-3.png)

Wenn Sie jetzt den Spielmodus wechseln, können Sie den 3D-Inhalt mit der Schwenkbewegung in der in-Editor-Simulation testen:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a>Eyetracking

In diesem Abschnitt erfahren Sie, wie Sie die Eye-Nachverfolgung in Ihrem Projekt aktivieren. In diesem Beispiel implementieren Sie die Funktionalität, damit jedes Objekt in der 3dobjectcollection langsam wird, während es durch den Augenblick des Benutzers betrachtet wird, und löst einen Unterbrechung-Effekt aus, wenn das zu überprüfende Objekt per Luftbild-oder Sprachbefehl ausgewählt wird.

Dies sind die wichtigsten Schritte, die Sie durchführen müssen:

1. Hinzufügen der Komponente "Augen Verfolgungs Ziel (Skript)" zu allen Ziel Objekten
2. Hinzufügen der "Eye Tracking Tutorial Demo (Skript)"-Komponente zu allen Ziel Objekten
3. Implementieren Sie bei der Betrachtung des Ziel Ereignisses.
4. In ausgewähltem Ereignis implementieren
5. Aktivieren der simulierten Augen Verfolgung für in-Editor-Simulationen
6. Aktivieren von Blick Eingaben in den App-Funktionen des Visual Studio-Projekts

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a>1. Hinzufügen der Komponente "Augen Verfolgungs Ziel (Skript)" zu allen Ziel Objekten

Erweitern Sie im Fenster Hierarchie das **3dobjectcollection-** Objekt, und wählen Sie alle untergeordneten **Objekte**aus. verwenden Sie dann im Inspektor-Fenster die Schaltfläche **Komponente hinzufügen** , um die Komponente für das **Augen Verfolgungs Ziel (Skript)** allen untergeordneten Objekten hinzuzufügen:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section3-step1-1.png)

Wenn alle untergeordneten **Objekte** noch ausgewählt sind, konfigurieren Sie die Komponente für das **Augen Verfolgungs Ziel (Skript)** wie folgt:

* **Wählen Sie** die auszuführende Aktion aus, um die Air-Tap-Aktion für dieses Objekt als SELECT- **Aktion zu definieren**.
* Erweitern **Sie Sprachauswahl** , und legen Sie die sprach Befehlslisten **Größe** auf 1 fest. ändern Sie dann in der angezeigten Liste neues Element die Option **0** **, um die**sprach Befehls Aktion für dieses Objekt als SELECT-Aktion zu definieren.

![mrlearning: Basis](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a>2. Hinzufügen der "Eye Tracking Tutorial Demo (Skript)"-Komponente zu allen Ziel Objekten

Wenn alle untergeordneten **Objekte** noch ausgewählt sind, fügen Sie mithilfe der Schaltfläche **Komponente hinzufügen** die Komponente " **Eye Tracking Tutorial Demo (Script)** " allen untergeordneten Objekten hinzu:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> Die Komponente für die Augen Verfolgungs Ziel (Skript) ist nicht Bestandteil von mrtk. Es wurde mit den Assets dieses Tutorials bereitgestellt.

### <a name="3-implement-the-while-looking-at-target-event"></a>3. implementieren Sie bei der Betrachtung des Ziel Ereignisses.

Wählen Sie im Fenster Hierarchie das **Käse** Objekt aus, und erstellen Sie ein neues, während Sie das **Ziel Ereignis () ansehen** , das **Käse** Objekt so konfigurieren, dass es das Ereignis empfängt, und " **eyetrackingtutorialdemo. rotatetarget** " als Aktion definieren, die ausgelöst werden soll:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section3-step3-1.png)

**Wiederholen** Sie diesen Vorgang für jedes untergeordnete Objekt in der 3dobjectcollection.

> [!TIP]
> Eine Erinnerung, wie Ereignisse implementiert werden können, finden Sie in den Anweisungen [Hand Tracking Gesten und Interaktionen Buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) .

### <a name="4-implement-the-on-selected-event"></a>4. implementieren Sie für das ausgewählte Ereignis.

Wählen Sie im Fenster Hierarchie das Objekt **Käse** aus, und erstellen Sie dann ein neues **auf ausgewähltes Ereignis ()** , konfigurieren Sie das **Käse** Objekt, um das Ereignis zu empfangen, und definieren Sie " **eyetrackingtutorialdemo. rotatetarget** " als Aktion, die ausgelöst werden soll:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section3-step4-1.png)

**Wiederholen** Sie diesen Vorgang für jedes untergeordnete Objekt in der 3dobjectcollection.

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a>5. Aktivieren der simulierten Augen Verfolgung für in-Editor-Simulationen

Wählen Sie im Fenster Hierarchie das **mixedrealitytoolkit** -Objekt aus, und wählen Sie dann im Inspektor-Fenster die Registerkarte **Eingabe** aus, erweitern Sie den Abschnitt **Eingabedaten Anbieter** und dann den Abschnitt **Input Simulation Service** , und Klonen Sie das **defaultmixedrealityinputsimulationprofile** -Objekt, um es durch ihr eigenes anpassbares **Eingabe Simulations Profil**zu ersetzen:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> Eine Erinnerung zum Klonen von mrtk-Profilen finden Sie unter [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.

Aktivieren Sie im Abschnitt **Eye Simulation** das Kontrollkästchen **Augen Position simulieren** , um die Augen Verfolgungs Simulation zu aktivieren:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section3-step5-2.png)

Wenn Sie nun in den Spielmodus wechseln, können Sie die von Ihnen implementierten Spin-und Unterbrechung-Effekte testen, indem Sie die Ansicht so anpassen, dass der Cursor auf eines der Objekte trifft, und mithilfe von Hand Interaktion oder Sprachbefehl das Objekt auswählen:

![mrlearning: Basis](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> Wenn Sie die DefaultHoloLens2ConfigurationProfile nicht zum Klonen Ihres anpassbaren mrtk-Konfigurations Profils verwendet haben, wie in den Anweisungen zum [Konfigurieren des Mixed Reality-Toolkits](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) beschrieben, ist die Eye-Nachverfolgung in Ihrem Projekt möglicherweise nicht aktiviert und muss aktiviert werden. Hierzu finden Sie die Anweisungen unter " [Getting Started with Eye Tracking" in mrtk](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) .

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a>6. Aktivieren Sie die Blick Eingabe in den App-Funktionen des Visual Studio-Projekts.

Bevor Sie Ihre APP aus Visual Studio auf Ihrem Gerät entwickeln und bereitstellen können, müssen Sie in den App-Funktionen des Projekts die Option "Blick Eingaben" aktivieren. Hierfür können Sie die Anweisungen unter [Testen Ihrer Unity-App auf hololens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) befolgen.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben der Anwendung erfolgreich grundlegende Funktionen zur Auge Verfolgung hinzugefügt. Diese Aktionen stellen nur den Einstieg in eine ganze Welt der Möglichkeiten mit Eyetracking dar. In diesem Tutorial haben Sie auch weitere erweiterte Eingabe Features kennengelernt, wie z. b. Sprachbefehle und Schwenk Gesten.

[Nächste Lektion: 7. Erstellen einer Beispielanwendung für ein Mond Modul](mrlearning-base-ch6.md)
