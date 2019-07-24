---
title: Mr-Eingabe 212-Stimme
description: Befolgen Sie diese exemplarische Vorgehensweise, indem Sie Unity, Visual Studio und hololens verwenden, um die Details der sprach Konzepte zu erlernen.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, Tutorial, Stimme
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522352"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.

<br>

# <a name="mr-input-212-voice"></a>Mr-Eingabe 212: Spracheingabe

Die [Spracheingabe](voice-input.md) bietet uns eine weitere Möglichkeit, mit unseren holograms zu interagieren. Sprachbefehle funktionieren auf sehr natürliche und einfache Weise. Entwerfen Sie Ihre Sprachbefehle so, dass Sie wie folgt lauten:

* Natürliche
* Leicht zu merken
* Geeigneter Kontext
* Ausreichend Unterschied zu anderen Optionen innerhalb desselben Kontexts

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

In den [Grundlagen 101](holograms-101.md)haben wir keywordrecognizer verwendet, um zwei einfache Sprachbefehle zu erstellen. In der Eingabe 212 gehen wir genauer vor und lernen, wie Sie:

* Entwerfen Sie Sprachbefehle, die für die hololens-Sprach-Engine optimiert sind.
* Sorgen Sie dafür, dass der Benutzer weiß, welche Sprachbefehle verfügbar sind.
* Bestätigen Sie, dass der Sprachbefehl des Benutzers gehört.
* Verstehen Sie, was der Benutzer sagt, mithilfe einer Diktat Erkennung.
* Verwenden Sie eine Grammatik Erkennung, um Befehle auf der Grundlage einer SRGS-oder Spracherkennungs-Grammatik Spezifikation (File) abzuhören.

In diesem Kurs überprüfen wir den Modell-Explorer, den wir in der [Eingabe 210](holograms-210.md) und in der [Eingabe 211](holograms-211.md)von Mr erstellt haben.

>[!IMPORTANT]
>Die in den folgenden Kapiteln eingebetteten Videos wurden mit einer älteren Version von Unity und dem Mixed Reality Toolkit aufgezeichnet. Die Schritt-für-Schritt-Anweisungen sind genau und aktuell, aber es werden möglicherweise Skripts und Visualisierungen in den entsprechenden Videos angezeigt, die veraltet sind. Die Videos bleiben in der einwelt enthalten und werden weiterhin angewendet.


## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>Mr-Eingabe 212: Spracheingabe</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Bevor Sie beginnen

### <a name="prerequisites"></a>Vorraussetzungen

* Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md)konfiguriert ist.
* Einige Grund C# Legende Programmiermöglichkeiten.
* Sie sollten die [Grundlagen von 101](holograms-101.md)abgeschlossen haben.
* Sie sollten die [Mr-Eingabe 210](holograms-210.md)abgeschlossen haben.
* Sie sollten die [Mr-Eingabe 211](holograms-211.md)abgeschlossen haben.
* Ein hololens-Gerät, das [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode)ist.

### <a name="project-files"></a>Projektdateien

* Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) , die für das Projekt erforderlich sind. Erfordert Unity 2017,2 oder höher.
* Deinstallieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht zugänglichen Speicherort.

>[!NOTE]
>Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).

### <a name="errata-and-notes"></a>Errata und Notizen

* "Enable nur eigenen Code" muss in Visual Studio unter "Extras-> Optionen" deaktiviert*werden (>* Debuggen, um Breakpoints im Code zu erreichen.

## <a name="unity-setup"></a>Unity-Setup

### <a name="instructions"></a>Anweisungen

1. Starten Sie Unity.
2. Wählen Sie **Öffnen**aus.
3. Navigieren Sie zum Ordner **holographicacademy-holograms-212-Voice** , den Sie zuvor nicht archiviert haben.
4. Suchen und wählen Sie den **Start**/**Modell-Explorer** -Ordner aus.
5. Klicken Sie auf die Schaltfläche **Ordner auswählen** .
6. Erweitern Sie im **Projekt** Panel den Ordner **Szenen** .
7. Doppelklicken Sie auf **Model Explorer** Scene, um es in Unity zu laden.

### <a name="building"></a>Erstellung

1. Wählen Sie in Unity **Datei >** Buildeinstellungen aus.
2. Wenn **Szenen/Model Explorer** nicht in **Szenen im Build**aufgeführt ist, klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.
3. Wenn Sie speziell für hololens entwickeln, legen Sie **Zielgerät** auf **hololens**fest. Andernfalls sollten Sie es auf **jedem Gerät**belassen.
4. Stellen  Sie sicher, dass der Buildtyp auf **D3D** und das **SDK** auf **Latest installiert** festgelegt ist (was SDK 16299 oder höher sein sollte).
5. Klicken Sie auf **Erstellen**.
6. Erstellen Sie einen **neuen Ordner** mit dem Namen "App".
7. Klicken Sie einfach auf den **App** -Ordner.
8. Klicken **Sie auf Ordner auswählen** , und Unity startet das Projekt für Visual Studio.

Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.

1. Öffnen Sie den **App** -Ordner.
2. Öffnen Sie die Visual Studio-Projekt Mappe **Model Explorer**.

Bei der Bereitstellung in hololens:

1. Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x86**.
2. Klicken Sie auf den Dropdown Pfeil neben der Schaltfläche lokaler Computer, und wählen Sie **Remote Computer**aus.
3. Geben Sie **die IP-Adresse des hololens-Geräts** ein, und legen Sie den Authentifizierungsmodus auf **Universal (unverschlüsseltes Protokoll)** Klicken Sie auf **Auswählen**. Wenn Sie die IP-Adresse Ihres Geräts nicht kennen, suchen Sie unter **Einstellungen > Netzwerk & Internet > Erweiterte Optionen**.
4. Klicken Sie in der oberen Menüleiste auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**. Wenn Sie die Bereitstellung auf Ihrem Gerät zum ersten Mal durchführt, müssen Sie [es mit Visual Studio](using-visual-studio.md#pairing-your-device-hololens)koppeln.
5. Wenn die APP bereitgestellt wurde, schließen Sie das **fitbox** -Gerät mit einer **Auswahl Bewegung**ab.

Bei der Bereitstellung auf einem immersiven Headset:

1. Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x64**.
2. Stellen Sie sicher, dass das Bereitstellungs Ziel auf **lokaler Computer**festgelegt ist.
3. Klicken Sie in der oberen Menüleiste auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.
4. Wenn die APP bereitgestellt wurde, schließen Sie die Funktion **, indem Sie** den-Typ auf einen Bewegungs Controller ziehen.

>[!NOTE]
>Im Visual Studio-Fehler Panel werden möglicherweise einige rote Fehler feststellen. Es ist sicher, Sie zu ignorieren. Wechseln Sie zum Ausgabebereich, um den tatsächlichen buildfortschritt anzuzeigen. Fehler im Ausgabe Panel erfordern eine Korrektur (meistens werden Sie durch einen Fehler in einem Skript verursacht).

## <a name="chapter-1---awareness"></a>Kapitel 1: Informationen zum Bewusstsein

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>Ziele

* Erfahren Sie mehr über die **DOS-und "TS** of Voice Command Design".
* Verwenden Sie **keywordrecognizer** , um auf Blick basierende Sprachbefehle hinzuzufügen.
* Sorgen Sie dafür, dass Benutzer Sprachbefehle mithilfe von Cursor **Feedback**erkennen.

### <a name="voice-command-design"></a>Sprach Befehls Entwurf

In diesem Kapitel erfahren Sie mehr über das Entwerfen von Sprachbefehlen. Beim Erstellen von Sprachbefehlen:

#### <a name="do"></a>DO

* Erstellen Sie präzise Befehle. Sie möchten nicht *"das aktuell ausgewählte Video abspielen*" verwenden, da dieser Befehl nicht präzise ist und vom Benutzer leicht vergessen wird. Verwenden Sie stattdessen Folgendes: *"Video abspielen"* , da es kurz ist und über mehrere Silben verfügt.
* Verwenden Sie ein einfaches Vokabular. Versuchen Sie immer, gängige Wörter und Ausdrücke zu verwenden, die für den Benutzer leicht zu erkennen und zu merken sind. Wenn Ihre Anwendung z. b. ein Notiz Objekt hätte, das in der Ansicht angezeigt oder ausgeblendet werden kann, würden Sie den Befehl *"Placard anzeigen"* nicht verwenden, da "Placard" ein selten verwendeter Begriff ist. Verwenden Sie stattdessen den Befehl: *"Hinweis anzeigen"* , um den Hinweis in der Anwendung anzuzeigen.
* Achten Sie auf Einheitlichkeit. Sprachbefehle sollten in der gesamten Anwendung konsistent gehalten werden. Stellen Sie sich vor, dass Sie in Ihrer Anwendung zwei Szenen haben und beide Szenen eine Schaltfläche zum Schließen der Anwendung enthalten. Wenn in der ersten Szene der Befehl *"Exit"* zum auslöst der Schaltfläche verwendet wird, aber die zweite Szene den Befehl *"APP schließen"* verwendet hat, wird der Benutzer sehr verwirrt. Wenn die gleiche Funktionalität in mehreren Szenen beibehalten wird, sollte der gleiche Sprachbefehl verwendet werden, um Sie zu initiieren.

#### <a name="dont"></a>TUE NICHT

* Verwenden Sie einzelne Silb Bare Befehle. Wenn Sie z. b. einen Sprachbefehl zum Abspielen eines Videos erstellt haben, sollten Sie die Verwendung des einfachen Befehls *"Play"* vermeiden, da es sich nur um eine einzelne Silb Bare Sprache handelt, die vom System leicht übersehen werden könnte. Verwenden Sie stattdessen Folgendes: *"Video abspielen"* , da es kurz ist und über mehrere Silben verfügt.
* Verwenden Sie Systembefehle. Der Befehl *"Select"* ist vom System für das auslöst eines Tap-Ereignisses für das aktuell fokussierte Objekt reserviert. Verwenden Sie den Befehl *"Select"* nicht in einem Schlüsselwort oder Ausdruck, da dies möglicherweise nicht erwartungsgemäß funktioniert. Wenn z. b. der Sprachbefehl zum Auswählen eines Cubes in der Anwendung *"Select Cube"* war, der Benutzer aber eine Kugel schaute, als er den Befehl aussprach, wird stattdessen die Kugel ausgewählt. Ähnliche app-leisten Befehle sind sprach fähig. Verwenden Sie die folgenden Sprachbefehle nicht in der corewindow-Ansicht:
    1. Zurück
    2. Scrolltool
    3. Zoom Tool
    4. Tool ziehen
    5. Anpassen
    6. Entfernen
* Verwenden Sie ähnliche Sounds. Versuchen Sie, die Verwendung von Sprachbefehlen zu vermeiden, die sich in der Wenn Sie über eine Einkaufs Anwendung verfügen, in der *"Store anzeigen"* und *"mehr anzeigen"* als Sprachbefehle unterstützt werden, sollten Sie einen der Befehle deaktivieren, während der andere verwendet wurde. Beispielsweise können Sie die Schaltfläche *"Store anzeigen"* verwenden, um den Store zu öffnen, und dann diesen Befehl deaktivieren, wenn der Speicher angezeigt wird, sodass der Befehl *"Weitere anzeigen"* zum Durchsuchen verwendet werden kann.

### <a name="instructions"></a>Anweisungen

* Verwenden Sie im Bereich **Hierarchie** von Unity das Suchtool, um das **holoComm_screen_mesh** -Objekt zu suchen.
* Doppelklicken Sie auf das **holoComm_screen_mesh** -Objekt, um es in der **Szene**anzuzeigen. Dies ist die Überwachung des Astronauten, die auf unsere Sprachbefehle antwortet.
* Suchen Sie im **Inspektor** -Panel die Komponente **Spracheingabe Quelle (Skript)** .
* Erweitern Sie den Abschnitt **Schlüsselwörter** , um den unterstützten Sprachbefehl anzuzeigen: **Öffnen Sie Communicator**.
* Klicken Sie rechts auf das Zahnrad Symbol, und wählen Sie **Skript bearbeiten**aus.
* Erkunden Sie **SpeechInputSource.cs** , um zu verstehen, wie das **keywordrecognizer** zum Hinzufügen von Sprachbefehlen verwendet wird.

### <a name="build-and-deploy"></a>Erstellen und bereitstellen

* Verwenden Sie in Unity **Datei >** Buildeinstellungen, um die Anwendung neu zu erstellen.
* Öffnen Sie den **App** -Ordner.
* Öffnen Sie die Visual Studio-Projekt Mappe **Model Explorer**.

(Wenn Sie dieses Projekt bereits während der Einrichtung in Visual Studio erstellt bzw. bereitgestellt haben, können Sie diese Instanz von Visual Studio öffnen und auf "alles neu laden" klicken).

* Klicken Sie in Visual Studio auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.
* Nachdem die Anwendung in den hololens bereitgestellt wurde, schließen Sie das Feld anpassen mithilfe der [Tasten](gestures.md#air-tap) Kombination.
* Schauen Sie sich die Überwachung des Astronauten an.
* Wenn die Überwachung den Fokus besitzt, überprüfen Sie, ob sich der Cursor in ein Mikrofon ändert. Dadurch erhalten Sie Feedback, dass die Anwendung Sprachbefehle abhört.
* Vergewissern Sie sich, dass auf der Überwachung eine QuickInfo angezeigt wird. Dadurch können Benutzer den Befehl *"Open Communicator"* ermitteln.
* Nehmen Sie beim Ansehen bei der Überwachung *"Open Communicator"* an, um den Communicator-Bereich zu öffnen.

## <a name="chapter-2---acknowledgement"></a>Kapitel 2: Bestätigung

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>Ziele

* Aufzeichnen einer Nachricht mithilfe der Mikrofon Eingabe.
* Geben Sie dem Benutzer Feedback, dass die Anwendung seine Stimme abhört.

>[!NOTE]
>Die **Mikrofon** Funktion muss deklariert werden, damit eine APP vom Mikrofon aufgezeichnet werden muss. Dies erfolgt bereits in der Mr-Eingabe 212, aber beachten Sie dies für Ihre eigenen Projekte.
>
>1. Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zu "> Projekteinstellungen bearbeiten > Player" navigieren.
>2. Klicken Sie auf die Registerkarte "universelle Windows-Plattform".
>3. Aktivieren Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die **Mikrofon** Funktion.

### <a name="instructions"></a>Anweisungen

* Überprüfen Sie im Bereich **Hierarchie** der Unity, ob das **holoComm_screen_mesh** -Objekt ausgewählt ist.
* Suchen Sie im **Inspektor** -Panel nach der Komponente " **Astronauten Überwachung (Skript)** ".
* Klicken Sie auf den kleinen, blauen Cube, der als Wert der **Communicator Prefab** -Eigenschaft festgelegt wird.
* Im **Projekt** Panel sollte die **Communicator** -vorfab jetzt den Fokus haben.
* Klicken Sie im **Projekt** Panel auf die **Communicator** -vorfab, um die zugehörigen Komponenten im **Inspektor**anzuzeigen.
* Sehen Sie sich die Komponente " **Mikrofon-Manager (Skript)** " an, damit wir die Stimme des Benutzers aufzeichnen können.
* Beachten Sie, dass das **Communicator** -Objekt über eine **Spracheingabe Handler-Komponente (Skript)** für die Antwort auf den Befehl " **Nachricht senden** " verfügt.
* Sehen Sie sich die **Communicator (Script)** -Komponente an, und doppelklicken Sie auf das Skript, um es in Visual Studio zu öffnen.

Communicator.cs ist dafür verantwortlich, die richtigen Schaltflächen Zustände auf dem Communicator-Gerät festzulegen. Dies ermöglicht es unseren Benutzern, eine Nachricht aufzuzeichnen, wieder abzuspielen und die Nachricht an den Astronauten zu senden. Außerdem wird ein animiertes Wellen Formular gestartet und angehalten, um dem Benutzer zu bestätigen, dass seine Stimme gehört.

* Löschen Sie in **Communicator.cs**die folgenden Zeilen (81 und 82) aus der **Start** -Methode. Dadurch wird die Schaltfläche "Record" auf dem Communicator aktiviert.

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>Erstellen und bereitstellen

* Erstellen Sie in Visual Studio die Anwendung neu, und stellen Sie Sie auf dem Gerät bereit.
* Schauen Sie sich die Überwachung des Astronauten an, und sagen Sie *"Open Communicator"* , um den Communicator anzuzeigen.
* Klicken Sie auf die Schaltfläche " **Record** " (Mikrofon), um die Aufzeichnung einer verbalen Nachricht für den Astronauten zu starten
* Beginnen Sie mit dem Gespräch, und überprüfen Sie, ob die Wave-Animation auf dem Communicator abgespielt wird, der dem Benutzer Feedback zur Verfügung stellt, dass Ihre Stimme gehört.
* Klicken Sie auf die Schaltfläche **Beenden** (linkes Quadrat), und überprüfen Sie, ob die Wave-Animation beendet wird.
* Drücken Sie die **Wiedergabe** Schaltfläche (Rechts Dreieck), um die aufgezeichnete Nachricht wiederzugeben und auf dem Gerät zu hören.
* Klicken Sie auf die Schaltfläche zum **Abbrechen** (rechts Quadrat), um die Wiedergabe der aufgezeichneten Nachricht zu verhindern.
* Sagen *Sie "Nachricht senden"* , um den Communicator zu schließen und die Antwort "Nachricht empfangen" vom Astronauten zu empfangen.

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>Kapitel 3: verstehen und der Diktat Erkennung

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>Ziele

* Verwenden Sie die Diktat Erkennung, um die Sprache des Benutzers in Text zu konvertieren.
* Zeigen Sie die hypothetisierungserkenfizierung hypothetische und abschließende Ergebnisse in Communicator an.

In diesem Kapitel verwenden wir die Diktat Erkennung, um eine Nachricht für den Astronaut zu erstellen. Beachten Sie beim Verwenden der Diktat Erkennung Folgendes:

* Sie müssen mit WiFi verbunden sein, damit die Diktat Erkennung funktioniert.
* Timeouts treten nach einer festgelegten Zeitspanne auf. Es gibt zwei Timeouts, die Sie beachten sollten:
  * Wenn die Erkennung startet und keine Audiodaten für die ersten fünf Sekunden hört, wird ein Timeout angezeigt.
  * Wenn die Erkennung ein Ergebnis erhalten hat, dann aber für einen Zeitraum von 20 Sekunden den Ruhe Wert erfährt, wird ein Timeout verursacht.
* Es kann jeweils nur ein Erkennungs Funktionstyp (Schlüsselwort oder Diktat) ausgeführt werden.

>[!NOTE]
>Die **Mikrofon** Funktion muss deklariert werden, damit eine APP vom Mikrofon aufgezeichnet werden muss. Dies erfolgt bereits in der Mr-Eingabe 212, aber beachten Sie dies für Ihre eigenen Projekte.
>
>1. Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zu "> Projekteinstellungen bearbeiten > Player" navigieren.
>2. Klicken Sie auf die Registerkarte "universelle Windows-Plattform".
>3. Aktivieren Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die **Mikrofon** Funktion.

### <a name="instructions"></a>Anweisungen

Wir werden **MicrophoneManager.cs** bearbeiten, um die Diktat Erkennung zu verwenden. Dies fügen wir hinzu:

1. Wenn die **Schaltfläche "Datensatz** " gedrückt ist, **starten wir das "diktationerkenzer**".
2. Zeigen Sie die **Hypothese** an, was der diktationerkenzer verstanden hat.
3. Lock in den **Ergebnissen** der von der diktationerkenzer erkannten Ergebnisse.
4. Überprüfen Sie, ob Timeouts von der "diktationerkenzer".
5. Wenn die **Schaltfläche "beenden** " gedrückt wird oder bei der MIC-Sitzung ein Timeout auftritt, **Beenden Sie das "diktationerkenzer**".
6. Starten Sie den **keywordrecognizer**neu, der auf den Befehl " **Nachricht senden** " lauscht.

Los geht's. Vervollständigen Sie alle Codierungs Übungen für 3. a in **MicrophoneManager.cs**, oder kopieren Sie den unten stehenden Code, und fügen Sie ihn ein:

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

* Erstellen Sie in Visual Studio neu, und stellen Sie auf Ihrem Gerät bereit.
* Schließen Sie das Feld "anpassen" mit einer Tastenkombination.
* Schauen Sie sich die Überwachung des Astronauten an, und sagen Sie *"Open Communicator"* .
* Wählen Sie die Schaltfläche **Datensatz** (Mikrofon) aus, um Ihre Nachricht aufzuzeichnen.
* Beginnen Sie den Einstieg. Die **Diktat Erkennung** interpretiert Ihre Sprache und zeigt den Text mit hypothetischer Größe in Communicator an.
* Versuchen Sie, *"Nachricht senden"* zu sagen, während Sie eine Nachricht aufzeichnen. Beachten Sie, dass die **Schlüsselwort Erkennung** nicht antwortet, weil die **Diktat Erkennung** noch aktiv ist.
* Sprechen Sie einige Sekunden lang nicht mehr. Sehen Sie sich an, wie die Diktat Erkennung die Hypothese abschließt und das Endergebnis anzeigt.
* Beginnen Sie mit der Sprachverarbeitung, und halten Sie dann 20 Sekunden an Dies führt dazu, dass die **diktierungerkenfizierung** ein Timeout verursacht.
* Beachten Sie, dass die **Schlüsselwort Erkennung** nach dem obigen Timeout erneut aktiviert wird. Der Communicator antwortet nun auf Sprachbefehle.
* Sagen Sie *"Nachricht senden"* , um die Nachricht an den Astronaut zu senden.

## <a name="chapter-4---grammar-recognizer"></a>Kapitel 4: Grammatik Erkennung

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>Ziele

* Verwenden Sie die Grammatik Erkennung, um die Sprache des Benutzers gemäß einer SRGS-oder Spracherkennungs-Grammatik Spezifikation zu erkennen.

>[!NOTE]
>Die **Mikrofon** Funktion muss deklariert werden, damit eine APP vom Mikrofon aufgezeichnet werden muss. Dies erfolgt bereits in der Mr-Eingabe 212, aber beachten Sie dies für Ihre eigenen Projekte.
>
>1. Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zu "> Projekteinstellungen bearbeiten > Player" navigieren.
>2. Klicken Sie auf die Registerkarte "universelle Windows-Plattform".
>3. Aktivieren Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die **Mikrofon** Funktion.

### <a name="instructions"></a>Anweisungen

1. Suchen Sie im **Hierarchie** Panel nach **Jetpack_Center** , und wählen Sie es aus.
2. Suchen Sie im **Inspektor** -Panel nach dem Skript " **Tagalong Action** ".
3. Klicken Sie rechts neben dem Feld **zu tagendes Objekt auf** den kleinen Kreis.
4. Suchen Sie im Fenster, das angezeigt wird, nach **srgstoolbox** , und wählen Sie es aus der Liste aus.
5. Sehen Sie sich die Datei " **srgscolor. XML** " im Ordner " **streamingassets** " an.
* Die SRGS-Entwurfs Spezifikation finden Sie [hier](https://www.w3.org/TR/speech-grammar/)auf der W3C-Website.
* In der SRGS-Datei gibt es drei Arten von Regeln:
  * Eine Regel, mit der Sie eine Farbe aus einer Liste von zwölf Farben sagen können.
  * Drei Regeln, die auf eine Kombination der Farbregel und einer der drei Formen lauschen.
  * Die Stamm Regel colorchooser, die auf eine beliebige Kombination der drei "Color + Shape"-Regeln lauscht. Die Formen können in beliebiger Reihenfolge und in beliebiger Reihenfolge von nur einem bis zu allen drei Formen bezeichnet werden. Dies ist die einzige Regel, die überwacht wird, da Sie als Stamm Regel am Anfang der Datei im ursprünglichen &lt;Grammatik&gt; -Tag angegeben wird.

### <a name="build-and-deploy"></a>Erstellen und bereitstellen

* Erstellen Sie die Anwendung in Unity neu, erstellen Sie Sie in Visual Studio, und stellen Sie Sie bereit, um die APP auf hololens zu erleben
* Schließen Sie das Feld "anpassen" mit einer Tastenkombination.
* Schauen Sie sich das Jetpack des Astronauten an, und führen Sie eine Luft tippen Bewegung aus.
* Beginnen Sie den Einstieg. Die **Grammatik Erkennung** interpretiert Ihre Sprache und ändert die Farben der Formen basierend auf der Erkennung. Ein Beispiel Befehl ist "blauer Kreis, gelbes Quadrat".
* Führen Sie eine weitere Luft tippen Bewegung aus, um die Toolbox zu schließen.

## <a name="the-end"></a>Das Ende

Herzlichen Glückwunsch! Sie haben nun die **Mr-Eingabe 212 abgeschlossen: Stimme**an.

* Sie kennen die DOS-und die TS von Voice-Befehlen.
* Sie haben gesehen, wie Quick Infos verwendet wurden, um die Benutzer auf Sprachbefehle aufmerksam zu machen.
* Sie haben verschiedene Feedback Typen verwendet, um zu bestätigen, dass die Stimme des Benutzers gehört.
* Sie wissen, wie Sie zwischen der Schlüsselwort Erkennung und der Diktat Erkennung wechseln und wie diese beiden Features Ihre Stimme verstehen und interpretieren.
* Sie haben gelernt, wie Sie eine SRGS-Datei und die Grammatik Erkennung für die Spracherkennung in Ihrer Anwendung verwenden.
