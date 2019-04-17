---
title: MR Eingabe 212 - Sprache
description: Führen Sie diese Codierung Exemplarische Vorgehensweise mit Unity, Visual Studio und HoloLens um die Details der Voice-Konzepte zu erfahren.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academy, tutorial, voice
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593796"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

<br>

# <a name="mr-input-212-voice"></a>MR Eingabe 212: Spracheingabe

[Voice-Eingabe](voice-input.md) bietet uns eine andere Möglichkeit zur Interaktion mit unserem Hologramme. Sprachbefehle funktionieren in einer sehr natürlichen und einfache Möglichkeit. Entwerfen Sie Ihre Sprachbefehle, damit sie sind:

* Natürliche
* Leicht zu merken
* Kontext entsprechenden
* Ausreichend Weitere Optionen im gleichen Kontext unterscheidet

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

In [MR Grundlagen 101](holograms-101.md), wir die KeywordRecognizer verwendet, um zwei einfache Sprachbefehle zu erstellen. In der Eingabe 212 MR, wir tiefer einsteigen und erfahren Sie, wie Sie:

* Entwerfen Sie Sprachbefehle, die für die HoloLens spracherkennungs-Engine optimiert sind.
* Stellen Sie dem Benutzer bewusst welche Stimme Befehle verfügbar sind.
* Bestätigen Sie, dass schon Sprachbefehl des Benutzers.
* Überblick über die der Benutzer sagen, verwenden eine Erkennung Diktat.
* Verwenden Sie eine Erkennung Grammatik zum Lauschen auf Befehle, die basierend auf einer SRGS oder Speech Recognition-Grammatik-Spezifikation.

In diesem Kurs wir erneut die es im erstellt Modell-Explorer behandelt [MR Eingabe 210](holograms-210.md) und [MR Eingabe 211](holograms-211.md).

>[!IMPORTANT]
>Die Videos in jeder der folgenden Kapitel eingebettet wurden mit einer älteren Version von Unity und dem Mixed Reality-Toolkit aufgezeichnet. Während die schrittweisen Anweisungen korrekt und aktuell sind, Sie möglicherweise Skripts und Visualisierungen in die entsprechenden Videos, die veraltet sind. Die Videos aus Gründen der Posterity bleiben, und es aber trotzdem anwenden, da die Konzepte behandelt.


## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td>MR Eingabe 212: Spracheingabe</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Bevor Sie beginnen

### <a name="prerequisites"></a>Vorraussetzungen

* Ein Windows 10-PCs mit dem richtigen konfiguriert [-Tools installiert](install-the-tools.md).
* Einige grundlegende C# Programmierkenntnisse.
* Sie sollten abgeschlossen haben [MR Grundlagen 101](holograms-101.md).
* Sie sollten abgeschlossen haben [MR Eingabe 210](holograms-210.md).
* Sie sollten abgeschlossen haben [MR Eingabe 211](holograms-211.md).
* Ein Gerät HoloLens [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Projektdateien

* Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) vom Projekt erforderlich sind. Ist Unity 2017.2 oder höher erforderlich.
* Un-Archive die Dateien auf dem Desktop oder andere einfach auf den Speicherort zugreifen.

>[!NOTE]
>Wenn Sie vor dem Herunterladen, den Quellcode ansehen möchten es [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).

### <a name="errata-and-notes"></a>Fehler und Anmerkungen zu dieser Version

* "Nur eigenen Code aktivieren" muss deaktiviert sein (*deaktiviert*) in Visual Studio unter Extras -> Optionen-Debuggen >, um die Haltepunkte in Ihrem Code.

## <a name="unity-setup"></a>Unity-Setup

### <a name="instructions"></a>Anweisungen

1. Starten Sie Unity.
2. Wählen Sie **öffnen**.
3. Navigieren Sie zu der **HolographicAcademy-Hologramme-212-Voice** Ordner Sie zuvor nicht archiviert.
4. Suchen und Auswählen der **ab**/**Modell-Explorer** Ordner.
5. Klicken Sie auf die **Ordner auswählen** Schaltfläche.
6. In der **Projekt** erweitern Sie die **Szenen** Ordner.
7. Doppelklicken Sie auf **ModelExplorer** Szene, um es in Unity zu laden.

### <a name="building"></a>Erstellung

1. Wählen Sie in Unity **Datei > Buildeinstellungen**.
2. Wenn **Szenen/ModelExplorer** in nicht aufgeführt ist **Szenen In Build**, klicken Sie auf **öffnen Szenen hinzufügen** die Szene hinzufügen.
3. Wenn Sie speziell für HoloLens entwickeln, legen Sie **Zielgerät** zu **HoloLens**. Andernfalls lassen Sie es auf **jedes Gerät**.
4. Stellen Sie sicher **Build Type** nastaven NA hodnotu **D3D** und **SDK** nastaven NA hodnotu **zuletzt installierte** (die sollte SDK 16299 oder höher sein).
5. Klicken Sie auf **Erstellen**.
6. Erstellen Sie eine **neuer Ordner** mit dem Namen "App".
7. Mausklick die **App** Ordner.
8. Drücken Sie **Ordner auswählen** und Unity wird beim Erstellen des Projekts für Visual Studio gestartet.

Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.

1. Öffnen der **App** Ordner.
2. Öffnen der **ModelExplorer Visual Studio-Projektmappe**.

Wenn für HoloLens bereitstellen zu können:

1. Verwenden obere auf der Symbolleiste in Visual Studio, ändern Sie das Ziel vom Debugmodus in den **Version** und ARM, **X86**.
2. Klicken Sie auf den Dropdownpfeil neben der Schaltfläche mit den lokalen Computer, und wählen **Remotecomputer**.
3. Geben Sie **die HoloLens-Geräte-IP-Adresse** und legen Sie den Authentifizierungsmodus auf **universell (unverschlüsseltes Protokoll)**. Klicken Sie auf **Auswählen**. Wenn Sie Ihre IP-Adresse des Geräts nicht kennen, suchen Sie im **Einstellungen > Netzwerk und Internet > Erweiterte Optionen**.
4. Klicken Sie in der Menüleiste im oberen Bereich auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**. Ist dies beim ersten auf Ihrem Gerät bereitstellen, Sie müssen [verbinden Sie es mit Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
5. Wenn die app bereitgestellt wurde, schließen die **Fitbox** mit eine **wählen Sie die Bewegung**.

Wenn eine immersive Kopfhörer bereitstellen:

1. Verwenden obere auf der Symbolleiste in Visual Studio, ändern Sie das Ziel vom Debugmodus in den **Version** und ARM, **X64**.
2. Stellen Sie sicher, dass das Bereitstellungsziel nastaven NA hodnotu **lokalen Computer**.
3. Klicken Sie in der Menüleiste im oberen Bereich auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.
4. Wenn die app bereitgestellt wurde, schließen die **Fitbox** den Trigger ein Controller während der Übertragung zu ziehen.

>[!NOTE]
>Sie können einige rote Fehler im Bereich von Visual Studio-Fehler feststellen. Es kann gefahrlos ignoriert werden. Wechseln Sie zur Ausgabebereich tatsächliche anzeigen Fortschritt des Builds. Fehler im Ausgabebereich ist erforderlich, Sie stellen eine Lösung (die meisten häufig durch einen Fehler in einem Skript, sie entstehen).

## <a name="chapter-1---awareness"></a>Kapitel 1 - Awareness

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>Ziele

* Erfahren Sie, den **Empfehlungen und** Voice-Befehl Entwurf.
* Verwendung **KeywordRecognizer** Blicke basierend Sprachbefehle hinzufügen.
* Einrichten von Benutzern für Sprachbefehle, die bei der Cursor **Feedback**.

### <a name="voice-command-design"></a>Voice-Befehlsentwurf

In diesem Kapitel erfahren Sie, wie Sie Sprachbefehle zu entwerfen. Wenn Sie Sprachbefehle zu erstellen:

#### <a name="do"></a>DO

* Erstellen Sie präzise Befehle. Nicht verwenden möchten *"Video abspielen, um ausgewählte"*, da dieser Befehl nicht präzise ist und diese vom Benutzer leicht vergessen werden würden. Stattdessen sollten Sie Folgendes verwenden: *"Video abspielen"*, da sie präzise und verfügt über mehrere Unterschiede zwischen.
* Verwenden Sie ein einfaches Vokabular ein. Versuchen Sie immer mit häufige Wörter und Begriffe, die einfach für den Benutzer aus, um zu ermitteln, und denken Sie daran. Beispielsweise wenn Ihre Anwendung einen Hinweis-Objekt, die angezeigt oder ausgeblendet werden kann besitzt, würden Sie nicht den Befehl verwenden *"Placard anzeigen"*, da "Placard" ein selten verwendeter Begriff ist. Stattdessen würden Sie den Befehl verwenden: *"Hinweis anzeigen"*, um den Hinweis in Ihrer Anwendung anzuzeigen.
* Achten Sie auf Einheitlichkeit. Sprachbefehle sollten in Ihrer Anwendung konsistent gehalten werden. Angenommen Sie, Sie zwei Szenen in Ihrer Anwendung haben, und sowohl im Hintergrund eine Schaltfläche zum Schließen der Anwendungs enthalten. Wenn die erste Szene der Befehl verwendet *"Exit"* verwendet, um die Schaltfläche ", aber der zweite trigger Szene Befehls *"App Schließen"*, und klicken Sie dann der Benutzer wird allerdings sehr verwirrte. Wenn die gleiche Funktionalität auf mehrere Szenen weiterhin besteht, sollten der gleichen Voice-Befehl verwendet werden, sie auslösen.

#### <a name="dont"></a>DON'T

* Verwenden Sie die einzelnen Silbe-Befehle. Beispielsweise wenn Sie einen Sprachbefehl zur Wiedergabe eines Videos erstellen, vermeiden Sie die Verwendung der einfachen Befehls *"Wiedergeben"*, wie dabei handelt es sich nur eine einzelne Silbe konnte vom System leicht übersehen werden. Stattdessen sollten Sie Folgendes verwenden: *"Video abspielen"*, da sie präzise und verfügt über mehrere Unterschiede zwischen.
* Verwenden Sie Systembefehle. Die *"Select"* Befehl ist reserviert, die vom System eine Tap-Ereignis für das Objekt derzeit fokussierten auslösen. Verwenden Sie nicht mehrfach die *"Select"* -Befehl in einem Schlüsselwort oder einen Ausdruck, da es möglicherweise nicht funktioniert wie erwartet. Zum Beispiel wenn die Stimme-zum Auswählen eines Cubes in der Anwendung Befehl wurde *"Select Cube"*, aber der Benutzer suchte auf einer Kugel, wenn sie den Befehl uttered die Kugel stattdessen ausgewählt werden sollen. Auf ähnliche Weise werden die Befehle für app-Leiste Sprache aktiviert. Verwenden Sie die folgenden Sprachbefehle nicht in der Ansicht "corewindow" aus:
    1. Zurück
    2. Bildlauftool
    3. Zoomtool in der
    4. Ziehen Sie-Tool
    5. Anpassen
    6. Entfernen
* Verwenden Sie ähnliche Sounds. Versuchen Sie es, um zu vermeiden, verwenden Sprachbefehle, die schönen. Wenn Sie eine einkaufsanwendung haben dies unterstützt *"Anzeigen Store"* und *"Mehr anzeigen"* als Sprachbefehle, Sie sollten einen der Befehle deaktivieren, während die andere verwendet wurde. Beispielsweise können Sie die *"Anzeigen Store"* Schaltfläche, um den Store zu öffnen, und deaktivieren Sie dann diesen Befehl aus, wenn im Store angezeigt wurde, damit die *"Mehr anzeigen"* Befehl kann verwendet werden, für das Durchsuchen.

### <a name="instructions"></a>Anweisungen

* In Unity **Hierarchie** verwenden das Such-Tool zum Suchen der **HoloComm_screen_mesh** Objekt.
* Doppelklicken Sie auf die **HoloComm_screen_mesh** Objekt in der **Szene**. Dies ist die Astronautenausweis des sehen Sie sich, die unsere Sprachbefehle reagiert.
* In der **Inspektor** Suchen der **Speech-Eingabequelle (Skript)** Komponente.
* Erweitern Sie die **Schlüsselwörter** Abschnitt aus, um die Sprachnachrichten unterstützten Befehl finden Sie unter: **Öffnen Sie Communicator**.
* Klicken Sie auf das Zahnrad rechts, und wählen Sie dann **Bearbeitungsskript**.
* Untersuchen **SpeechInputSource.cs** zu verstehen, wie es verwendet die **KeywordRecognizer** Sprachbefehle hinzufügen.

### <a name="build-and-deploy"></a>Erstellen und bereitstellen

* Verwenden Sie in Unity **Datei > Buildeinstellungen** um die Anwendung neu zu erstellen.
* Öffnen der **App** Ordner.
* Öffnen der **ModelExplorer Visual Studio-Projektmappe**.

(Wenn Sie bereits erstellt bzw. dieses Projekt in Visual Studio während der Einrichtung bereitgestellt, klicken Sie dann Sie können diese Instanz von Visual Studio öffnen und klicken Sie auf "Alles neu laden" Wenn Sie aufgefordert werden).

* Klicken Sie in Visual Studio auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.
* Nachdem die Anwendung, die HoloLens bereitstellt, schließen Sie das mit ähnlichen Zeichen mithilfe der [tippbewegung](gestures.md#air-tap) Bewegung.
* Bestaunen Sie an die Astronautenausweis des überwachen.
* Wenn die Überwachung über den Fokus besitzt, stellen Sie sicher, dass der Cursor in ein Mikrofon ändert. Dadurch wird ein Feedback, das der Anwendung für Sprachbefehle überwacht wird.
* Stellen Sie sicher, dass eine QuickInfo auf der Apple Watch angezeigt wird. Dadurch können Benutzer ermitteln die *"Open Communicator"* Befehl.
* Während Sie auf der Apple Watch gazing, z. B. *"Communicator öffnen"* den Communicator-Bereich zu öffnen.

## <a name="chapter-2---acknowledgement"></a>Kapitel 2 – Bestätigung

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>Ziele

* Zeichnen Sie eine Nachricht mit der Mikrofoneingabe.
* Geben Sie Feedback an den Benutzer, den der Anwendung, um ihre Stimme überwacht wird an.

>[!NOTE]
>Die **Mikrofon** Funktion muss deklariert werden, dass eine app aus dem Mikrofon aufzeichnen. Dies ist für die Sie bereits unter MR Eingabe 212, aber beachten Sie, dass für Ihre eigenen Projekte.
>
>1. Rufen Sie im Unity-Editor die playereinstellungen durch Navigieren zu "Bearbeiten > Projekt Einstellungen > Player"
>2. Klicken Sie auf der Registerkarte "Universal Windows Platform"
>3. Überprüfen Sie im Abschnitt "Einstellungen > Veröffentlichungsfunktionen" die **Mikrofon** Funktion

### <a name="instructions"></a>Anweisungen

* In Unity **Hierarchie** überprüfen Sie, ob im Bereich der **HoloComm_screen_mesh** Objekt ausgewählt ist.
* In der **Inspektor** Bereich, suchen Sie nach der **Astronautenausweis überwachen (Skript)** Komponente.
* Klicken Sie auf die blaue Cube das als Wert festgelegt ist die **Communicator-Prefab** Eigenschaft.
* In der **Projekt** Bereich der **Communicator** Prefab verfügen nun über den Fokus.
* Klicken Sie auf die **Communicator** prefab in die **Projekt** Panel an seiner Komponenten in der **Inspektor**.
* Sehen Sie sich die **Mikrofon-Manager (Skript)** Komponente diese Weise können wir des Benutzers Stimme aufgezeichnet.
* Beachten Sie, dass die **Communicator** Objekt verfügt über eine **Eingabe Handler für die Spracherkennung (Skript)** Komponente für die Reaktion auf die **Send Message** Befehl.
* Sehen Sie sich die **Communicator (Skript)** -Komponente, und doppelklicken Sie auf das Skript aus, um es in Visual Studio zu öffnen.

Communicator.cs ist verantwortlich für die ordnungsgemäße Schaltflächenstatus festlegen, auf dem Communicator-Gerät. Dadurch können Benutzer eine Nachricht aufzeichnen, es wiedergeben und sendet die Nachricht an die Astronautenausweis. Es auch starten und beenden eine animierten Wave-Form, um dem Benutzer bestätigen, dass ihre Stimme gehört, wurde.

* In **Communicator.cs**, löschen Sie die folgenden Zeilen (81 und 82), aus der **starten** Methode. Dadurch wird die Schaltfläche "Record" für den Communicator ermöglicht.

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>Erstellen und bereitstellen

* Klicken Sie in Visual Studio die Anwendung neu erstellen und auf dem Gerät bereitstellen.
* An die Astronautenausweis des Watch bestaunen und sagen *"Open Communicator"* den Communicator angezeigt.
* Drücken Sie die **Datensatz** Schaltfläche (Mikrofon) zum Starten der Aufzeichnung einer mündlichen Nachricht für die Astronautenausweis.
* Spracheingabe/-Ausgabe starten, und stellen Sie sicher, dass die Welle Animation auf der Communicator bietet Feedback an den Benutzer, dass ihre Stimme gehört wird.
* Drücken Sie die **beenden** Schaltfläche (linke Quadrat), und stellen Sie sicher, dass die Wave-Animation beendet wird.
* Drücken Sie die **spielen** Schaltfläche (Rechtwinkliges Dreieck) zum Wiedergeben der aufgezeichneten Meldung und hören sie auf dem Gerät.
* Drücken Sie die **beenden** Schaltfläche (rechts Quadrat) zum Beenden der Wiedergabe der aufgezeichneten Meldung.
* Sagen Sie *"Nachricht senden"* schließen den Communicator und von der Astronautenausweis "Nachricht empfangen" eine Antwort empfängt.

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>Kapitel 3: verstehen und die Erkennung Diktat

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>Ziele

* Verwenden Sie die Erkennung Diktat des Benutzers Sprache in Text konvertiert.
* Der Diktat Erkennung-angenommener und Endergebnisse zurück in den Communicator anzeigen.

In diesem Kapitel verwenden wir die Erkennung Diktat zum Erstellen einer Nachricht für die Astronautenausweis. Wenn Sie die Diktat-Erkennung zu verwenden, beachten Sie, dass:

* Sie müssen mit WiFi für das Erkennungsmodul Diktatmodus funktioniert verbunden werden.
* Timeouts treten auf, nach einem festgelegten Zeitraum. Es gibt zwei Timeouts zu beachten:
  * Wenn die Erkennung gestartet wird und keine Audiodaten für die ersten fünf Sekunden zu hören, tritt ein Timeout ein.
  * Wenn die Erkennung erhält ein Ergebnis, aber dann Ruheintervall 20 Sekunden lang hört, tritt ein Timeout ein.
* Nur eine Art von Erkennung (Schlüsselwort oder Spracheingaben) kann zu einem Zeitpunkt ausführen.

>[!NOTE]
>Die **Mikrofon** Funktion muss deklariert werden, dass eine app aus dem Mikrofon aufzeichnen. Dies ist für die Sie bereits unter MR Eingabe 212, aber beachten Sie, dass für Ihre eigenen Projekte.
>
>1. Rufen Sie im Unity-Editor die playereinstellungen durch Navigieren zu "Bearbeiten > Projekt Einstellungen > Player"
>2. Klicken Sie auf der Registerkarte "Universal Windows Platform"
>3. Überprüfen Sie im Abschnitt "Einstellungen > Veröffentlichungsfunktionen" die **Mikrofon** Funktion

### <a name="instructions"></a>Anweisungen

Wir werden so bearbeiten Sie **MicrophoneManager.cs** die Diktat-Erkennung zu verwenden. Dies ist, was wir hinzufügen:

1. Wenn die **Schaltfläche "Aufzeichnen"** ist wir gedrückt, **starten die DictationRecognizer**.
2. Anzeigen der **Hypothese** von der DictationRecognizer verstanden.
3. Sperren der **Ergebnisse** von der DictationRecognizer verstanden.
4. Für die DictationRecognizer-Timeouts überprüfen.
5. Wenn die **Schaltfläche "Stopp"** befindet, gedrückt wird oder mic Timeout der Sitzung, **Beenden der DictationRecognizer**.
6. Neustart der **KeywordRecognizer**, Lauschen für die **Send Message** Befehl.

Los geht's. Führen Sie alle codierungsübungen für 3.a in **MicrophoneManager.cs**, oder kopieren Sie den fertig gestellten Code finden Sie unten:

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone. 
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a>Erstellen und bereitstellen

* Erstellen Sie in Visual Studio neu, und auf Ihrem Gerät bereitstellen.
* Im Lieferumfang von eine tippbewegung Geste mit ähnlichen Zeichen zu schließen.
* An die Astronautenausweis des Watch bestaunen und sagen *"Open Communicator"*.
* Wählen Sie die **Datensatz** Schaltfläche (Mikrofon), um Ihre Nachricht aufzuzeichnen.
* Starten Sie Spracheingabe/-Ausgabe. Die **Diktat Erkennung** interpretiert die Spracherkennung und Anzeigen von die Hypothese Text in den Communicator.
* Versuchen Sie es mit dem Text *"Nachricht senden"* während Sie eine Nachricht aufzeichnen. Beachten Sie, dass die **Schlüsselwort Erkennung** reagiert nicht, da die **Diktat Erkennung** weiterhin aktiv ist.
* Beenden Sie sprechen ein paar Sekunden. Verfolgen Sie, wie die Erkennung Diktat die Hypothese schließt ab und das endgültige Ergebnis zeigt.
* Beginnen Sie sprechen, und dann eine pause 20 Sekunden. Dies bewirkt, dass die **Diktat Erkennung** Timeout.
* Beachten Sie, dass die **Schlüsselwort Erkennung** wieder aktiviert wird, nach dem oben genannten Timeout. Der Communicator wird nun auf Sprachbefehle reagieren.
* Sagen Sie *"Nachricht senden"* zum Senden der Nachricht an die Astronautenausweis.

## <a name="chapter-4---grammar-recognizer"></a>Kapitel 4: Erkennung der Grammatik

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>Ziele

* Verwenden Sie die Erkennung der Grammatik für gemäß einer SRGS oder Speech Recognition-Grammatik-Spezifikation-Datei des Benutzers Spracherkennung.

>[!NOTE]
>Die **Mikrofon** Funktion muss deklariert werden, dass eine app aus dem Mikrofon aufzeichnen. Dies ist für die Sie bereits unter MR Eingabe 212, aber beachten Sie, dass für Ihre eigenen Projekte.
>
>1. Rufen Sie im Unity-Editor die playereinstellungen durch Navigieren zu "Bearbeiten > Projekt Einstellungen > Player"
>2. Klicken Sie auf der Registerkarte "Universal Windows Platform"
>3. Überprüfen Sie im Abschnitt "Einstellungen > Veröffentlichungsfunktionen" die **Mikrofon** Funktion

### <a name="instructions"></a>Anweisungen

1. In der **Hierarchie** Bereich, suchen Sie nach **Jetpack_Center** und wählen Sie ihn.
2. Suchen Sie nach der **beigefügten Aktion** -Skript in den **Inspektor** Bereich.
3. Klicken Sie auf den kleinen Kreis rechts neben der **Objekt zum Tag zusammen** Feld.
4. Suchen Sie im Fenster, das wird angezeigt, nach **SRGSToolbox** und wählen Sie sie aus der Liste.
5. Sehen Sie sich die **SRGSColor.xml** Datei die **StreamingAssets** Ordner.
* Die Spezifikation der SRGS-Entwurf finden Sie auf der W3C-Website [hier](https://www.w3.org/TR/speech-grammar/).
* In unserem SRGS-Datei haben wir drei Arten von Regeln:
  * Eine Regel, mit der Sie eine Farbe aus einer Liste von zwölf Farben sagen kann.
  * Drei Regeln, die für eine Kombination von Farbregel und eine der drei Formen zu überwachen.
  * Die Stammregel ColorChooser, die für eine beliebige Kombination der drei Regeln für "Farbe und Form vom Typ" lauscht. Die Formen können in beliebiger Reihenfolge und in beliebigem Umfang von einem einzigen, alle drei zusammen. Dies ist die einzige Regel, die für lauscht, wie sie als Stammregel am Anfang der Datei in der ersten angegeben ist &lt;Grammatik&gt; Tag.

### <a name="build-and-deploy"></a>Erstellen und bereitstellen

* Erstellen Sie die Anwendung in Unity, anschließendes Erstellen und Bereitstellen von Visual Studio, um die app auf HoloLens auftreten.
* Im Lieferumfang von eine tippbewegung Geste mit ähnlichen Zeichen zu schließen.
* Auf der Astronautenausweis des Jetpack bestaunen Sie, und führen Sie eine tippbewegung Bewegung.
* Starten Sie Spracheingabe/-Ausgabe. Die **Grammatik Erkennung** interpretiert die Spracherkennung und die Farbe der Formen, die basierend auf der Erkennung zu ändern. Ein Beispielbefehl ist "blauen Kreis, gelben Quadrat".
* Führen Sie ein anderes Air-tippbewegung um die Toolbox zu schließen.

## <a name="the-end"></a>Das Ende

Herzlichen Glückwunsch! Sie haben jetzt **MR Eingabe 212: Voice**.

* Sie kennen die Empfehlungen und von Stimmbefehlen.
* Sie haben gesehen, wie QuickInfos eingesetzt wurden, um die Benutzer Sprachbefehle aufmerksam zu machen.
* Sie haben verschiedene Arten von Feedback zu bestätigen, dass der Benutzer beteiligen wurde verwendet.
* Sie wissen, Informationen zum Wechseln zwischen die Schlüsselwort-Erkennung und die Erkennung von Spracheingaben und wie Sie diese beiden Funktionen zum verstehen und Interpretieren der Stimme.
* Sie haben gelernt, wie eine SRGS-Datei und die Erkennung der Grammatik für die Spracherkennung in Ihrer Anwendung verwenden.
