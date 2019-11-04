---
title: Mr-Eingabe 211-Geste
description: Befolgen Sie diese exemplarische Vorgehensweise für die Codierung mithilfe von Unity, Visual Studio und hololens, um die Details der Gesten Konzepte zu erlernen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, Tutorial, Geste
ms.openlocfilehash: d7a92e4b2f196d6d8b0ba0fe3ccb2aed87479ac1
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434695"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es wurde [eine neue Reihe von Tutorials](mrlearning-base.md) für hololens 2 gepostet.

# <a name="mr-input-211-gesture"></a>Mr-Eingabe 211: Geste

[Gesten](gaze-and-commit.md#composite-gestures) verwandeln die Benutzer Absicht in eine Aktion. Mit Gesten können Benutzer mit holograms interagieren. In diesem Kurs erfahren Sie, wie Sie die Hände des Benutzers nachverfolgen, auf Benutzereingaben reagieren und dem Benutzer Feedback geben können, der auf dem Hand Bundesland und-Speicherort basiert.

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

In den [Grundlagen 101](holograms-101.md)haben wir eine einfache Air-Tap-Geste verwendet, um mit unseren holograms zu interagieren. Nun gehen wir über die Luft tippen Bewegung hinaus und erforschen neue Konzepte für Folgendes:

* Erkennen, wenn die Hand des Benutzers nachverfolgt wird, und Senden von Feedback an den Benutzer.
* Verwenden Sie eine Navigations Geste, um unsere Hologramme zu drehen.
* Geben Sie uns Feedback, wenn der Benutzer die Hand verlässt.
* Verwenden Sie Manipulations Ereignisse, um Benutzern das Verschieben von holograms mit ihren Händen zu ermöglichen.

In diesem Kurs besuchen wir den Unity-Projekt **Modell-Explorer**, den wir in der [Eingabe 210](holograms-210.md)erstellt haben. Unser Astronauten Freund ist zurück, um uns bei der Untersuchung dieser neuen Gesten Konzepte zu unterstützen.

>[!IMPORTANT]
>Die in den folgenden Kapiteln eingebetteten Videos wurden mit einer älteren Version von Unity und dem Mixed Reality Toolkit aufgezeichnet. Die Schritt-für-Schritt-Anweisungen sind genau und aktuell, aber es werden möglicherweise Skripts und Visualisierungen in den entsprechenden Videos angezeigt, die veraltet sind. Die Videos bleiben in der einwelt enthalten und werden weiterhin angewendet.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>Mr-Eingabe 211: Geste</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Bevor Sie beginnen

### <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md)konfiguriert ist.
* Einige Grund C# Legende Programmiermöglichkeiten.
* Sie sollten die [Grundlagen von 101](holograms-101.md)abgeschlossen haben.
* Sie sollten die [Mr-Eingabe 210](holograms-210.md)abgeschlossen haben.
* Ein hololens-Gerät, das [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode)ist.

### <a name="project-files"></a>Projektdateien

* Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) , die für das Projekt erforderlich sind. Erfordert Unity 2017,2 oder höher.
* Deinstallieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht zugänglichen Speicherort.

>[!NOTE]
>Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).

### <a name="errata-and-notes"></a>Errata und Notizen

* "Enable nur eigenen Code" muss in Visual Studio unter "Extras-> Optionen" deaktiviert*werden (>* Debuggen, um Breakpoints im Code zu erreichen.

## <a name="chapter-0---unity-setup"></a>Kapitel 0: Einrichtung von Unity

### <a name="instructions"></a>Anweisungen

1. Starten Sie Unity.
2. Wählen Sie **Öffnen**aus.
3. Navigieren Sie zu dem **Gesten** Ordner, den Sie zuvor nicht archiviert haben.
4. Suchen Sie den Ordner **Start**/**Model Explorer** , und wählen Sie ihn aus.
5. Klicken Sie auf die Schaltfläche **Ordner auswählen** .
6. Erweitern Sie im **Projekt** Panel den Ordner **Szenen** .
7. Doppelklicken Sie auf **Model Explorer** Scene, um es in Unity zu laden.

### <a name="building"></a>Erstellen

1. Wählen Sie in Unity **Datei > Buildeinstellungen**aus.
2. Wenn **Szenen/Model Explorer** nicht in **Szenen im Build**aufgeführt ist, klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.
3. Wenn Sie speziell für hololens entwickeln, legen Sie **Zielgerät** auf **hololens**fest. Andernfalls sollten Sie es auf **jedem Gerät**belassen.
4. Stellen Sie sicher, dass der **Buildtyp** auf **D3D** und das **SDK** auf **Latest installiert** festgelegt ist (was SDK 16299 oder höher sein sollte).
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
4. Klicken Sie in der oberen Menüleiste auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**. Wenn Sie die Bereitstellung auf Ihrem Gerät zum ersten Mal durchführt, müssen Sie [es mit Visual Studio](using-visual-studio.md#pairing-your-device)koppeln.
5. Wenn die APP bereitgestellt wurde, schließen Sie das **fitbox** -Gerät mit einer **Auswahl Bewegung**ab.

Bei der Bereitstellung auf einem immersiven Headset:

1. Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x64**.
2. Stellen Sie sicher, dass das Bereitstellungs Ziel auf **lokaler Computer**festgelegt ist.
3. Klicken Sie in der oberen Menüleiste auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.
4. Wenn die APP bereitgestellt wurde, schließen Sie die Funktion **, indem Sie den-** Typ auf einen Bewegungs Controller ziehen.

>[!NOTE]
>Im Visual Studio-Fehler Panel werden möglicherweise einige rote Fehler feststellen. Es ist sicher, Sie zu ignorieren. Wechseln Sie zum Ausgabebereich, um den tatsächlichen buildfortschritt anzuzeigen. Fehler im Ausgabe Panel erfordern eine Korrektur (meistens werden Sie durch einen Fehler in einem Skript verursacht).

## <a name="chapter-1---hand-detected-feedback"></a>Kapitel 1: Hand erkanntes Feedback

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>Ziele

* Hiermit werden die Hand Verfolgungs Ereignisse abonniert.
* Mit Cursor Feedback können Sie Benutzer anzeigen, wenn eine Hand nachverfolgt wird.

>[!NOTE]
>Bei hololens 2 werden Hände erkannt, wenn die Hände sichtbar sind (nicht nur, wenn ein Finger nach oben zeigt).

### <a name="instructions"></a>Anweisungen

* Erweitern Sie im Bereich **Hierarchie** das **InputManager** -Objekt.
* Suchen Sie nach dem **gesturesinput** -Objekt, und wählen Sie es aus.

Das Skript **InteractionInputSource.cs** führt folgende Schritte aus:

1. Abonniert das interaktionsourceerkannte-Ereignis und das interaktionsourcelost-Ereignis.
2. Legt den handerkannten Zustand fest.
3. Abonniert die Ereignisse interaktionsourceerkannte und interaktionsourcelost.

Als nächstes aktualisieren wir den Cursor von der [Mr-Eingabe 210](holograms-210.md) in einen, der das Feedback abhängig von den Aktionen des Benutzers anzeigt.

1. Wählen Sie im Bereich **Hierarchie** das **Cursor** Objekt aus, und löschen Sie es.
2. Suchen Sie im **Projekt** Panel nach **currsorwithfeedback** , und ziehen Sie es in den Bereich **Hierarchie** .
3. Klicken Sie im **Hierarchie** Panel auf **InputManager** , und ziehen Sie dann das **cursorwithfeedback** -Objekt aus der **Hierarchie** in das **Cursor** Feld " **simplesinglepointerselector**" von InputManager am unteren Rand des **Inspektor**.
4. Klicken Sie in der **Hierarchie**auf das **Cursor-Feedback** .
5. Erweitern Sie im **Inspektor** -Panel **Cursor Zustandsdaten** für das **Objekt Cursor** Skript.

Die **Cursor Zustandsdaten** funktionieren wie folgt:

* Jeder Status der Überprüfung bedeutet, **dass keine Hand** erkannt wird und der Benutzer einfach eine Suche durchführt.
* Jeder **Interaktions** Zustand bedeutet, dass eine Hand oder ein Controller erkannt wird.
* Jeder **Hover** -Zustand bedeutet, dass der Benutzer ein Hologram ansieht.

### <a name="build-and-deploy"></a>Erstellen und bereitstellen

* Verwenden Sie in Unity **Datei > Buildeinstellungen** , um die Anwendung neu zu erstellen.
* Öffnen Sie den **App** -Ordner.
* Öffnen Sie die Visual Studio-Projekt Mappe **Model Explorer**, wenn Sie nicht bereits geöffnet ist.
  * (Wenn Sie dieses Projekt bereits während der Einrichtung in Visual Studio erstellt bzw. bereitgestellt haben, können Sie diese Instanz von Visual Studio öffnen und auf "alles neu laden" klicken).
* Klicken Sie in Visual Studio auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.
* Nachdem die Anwendung in den hololens bereitgestellt wurde, schließen Sie die fitbox mithilfe der Tastenkombination.
* Bewegen Sie die Hand in die Anzeige, und zeigen Sie den Finger des Indexes auf den Himmel, um die Hand Verfolgung zu starten
* Bewegen Sie Ihre Hand nach links, nach rechts, nach oben und unten.
* Sehen Sie sich an, wie sich der Cursor ändert, wenn Ihre Hand erkannt wird, und dann in der Ansicht verloren
* Wenn Sie sich auf einem immersiven Headset befinden, müssen Sie eine Verbindung herstellen und den Controller trennen. Dieses Feedback wird auf einem immersiven Gerät weniger interessant, da ein verbundener Controller immer "verfügbar" ist.

## <a name="chapter-2---navigation"></a>Kapitel 2: Navigation

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>Ziele

* Verwenden Sie Navigations Gesten Ereignisse, um den Astronaut zu drehen.

### <a name="instructions"></a>Anweisungen

Um Navigations Gesten in unserer APP zu verwenden, bearbeiten wir **GestureAction.cs** , um Objekte zu drehen, wenn die Navigations Bewegung auftritt. Außerdem wird dem Cursor Feedback hinzugefügt, das angezeigt wird, wenn die Navigation verfügbar ist.

1. Erweitern Sie im Bereich **Hierarchie** den Eintrag **Cursor-Feedback**.
2. Suchen Sie im Ordner **holograms** das **scrollfeedback** -Medienobjekt.
3. Ziehen Sie die **scrollfeedback** -vorfab per Drag & amp; Drop auf das **Cursor** Objekt in der **Hierarchie**.
4. Klicken Sie auf **currsorwithfeedback**.
5. Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .
6. Geben Sie im Menü den Suchbegriff **Cursor Feedback**ein. Wählen Sie das Suchergebnis aus.
7. Ziehen Sie das **scrollfeedback** -Objekt mithilfe von Drag & amp; Drop aus der- **Hierarchie** in der **Cursor-Feedback** Komponente des **Inspektors**auf die Eigenschaft Bild Lauf **Erkennung erkannt**
8. Wählen Sie im Bereich **Hierarchie** das Objekt **Astroman** aus.
9. Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .
10. Geben Sie im Menü die Aktion in der **Aktion**Suchfeld ein. Wählen Sie das Suchergebnis aus.

Öffnen Sie als nächstes **GestureAction.cs** in Visual Studio. Bearbeiten Sie in der Codierungs Übung 2. c das Skript, um Folgendes durchzuführen:

1. **Drehen Sie das Astroman** -Objekt immer dann, wenn eine Navigations Geste ausgeführt wird.
2. Berechnen Sie den " **rotationfactor** ", um die auf das Objekt angewendete Drehung zu steuern.
3. **Drehen Sie das Objekt** um die y-Achse, wenn der Benutzer seine Hand nach links oder rechts verschiebt.

Vervollständigen Sie die Codierungs Übungen 2. c im Skript, oder ersetzen Sie den Code durch die folgende abgeschlossene Lösung:

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

Sie werden feststellen, dass die anderen Navigations Ereignisse bereits mit einigen Informationen ausgefüllt sind. Wir schieben das gameobject-Objekt auf den modalen Stapel des Toolkits, sodass der Benutzer den Fokus nicht mehr auf dem Astronaut behalten muss, sobald die Drehung begonnen hat. Dementsprechend wird das gameobject aus dem Stapel entfernt, sobald die Geste abgeschlossen ist.

### <a name="build-and-deploy"></a>Erstellen und bereitstellen

1. Erstellen Sie die Anwendung in Unity neu, erstellen Sie Sie, und stellen Sie Sie aus Visual Studio bereit, um Sie in den hololens auszuführen.
2. Blick auf den Astronaut, zwei Pfeile sollten auf beiden Seiten des Cursors angezeigt werden. Dieses neue visuelle Element gibt an, dass der Astronaut gedreht werden kann.
3. Legen Sie die Hand an der Position an der Position (Index fingerbild, die auf den Himmel zeigt), sodass die hololens Ihre Hand nachverfolgen werden.
4. Um den Astronaut zu drehen, verringern Sie den Finger des Indexes an eine Position, und verschieben Sie dann die Hand nach links oder rechts, um die navigationx-Geste zu initiieren.

## <a name="chapter-3---hand-guidance"></a>Kapitel 3-Hand-Anleitungen

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>Ziele

* Verwenden Sie die **Hand Leit Faden Bewertung** , um vorherzusagen, wann die Hand Verfolgung verloren geht.
* Geben Sie **Feedback zu dem Cursor** an, der angezeigt wird, wenn die Hand des Benutzers den Rand der Ansicht der Kamera anzeigt.

### <a name="instructions"></a>Anweisungen

1. Wählen Sie im Bereich **Hierarchie** das **Cursor** -Objekt aus.
2. Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .
3. Geben Sie im Menü den **Hand Leit Faden**für das Suchfeld ein. Wählen Sie das Suchergebnis aus.
4. Suchen Sie im **Projekt** Panel **holograms** -Ordner das **handguidancefeedback** -Asset.
5. Ziehen Sie das Objekt **handguidancefeedback** per Drag & Drop auf die Eigenschaft **Hand Leit Faden Anzeige** im **Inspektor** -Panel.

### <a name="build-and-deploy"></a>Erstellen und bereitstellen

* Erstellen Sie die Anwendung in Unity neu, erstellen Sie Sie in Visual Studio, und stellen Sie Sie bereit, um die APP auf hololens zu erleben
* Zeigen Sie Ihre Hand an, und heben Sie den Index Finger auf, um nachverfolgt zu werden.
* Beginnen Sie mit dem Drehen des Astronauten mit der Navigations Bewegung (drücken Sie den Finger und den Ziehpunkt des Indexes zusammen).
* Verschieben Sie Ihre Hand ganz nach links, nach rechts, nach oben und nach unten.
* Wenn die Kante des Gesten Rahmens in der Hand dargestellt wird, sollte neben dem Cursor ein Pfeil angezeigt werden, der Sie darüber informiert, dass die Hand Verfolgung verloren geht. Der Pfeil gibt die Richtung an, in der die Hand bewegt werden soll, um zu verhindern, dass die Überwachung verloren geht.

## <a name="chapter-4---manipulation"></a>Kapitel 4: Bearbeitung

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>Ziele

* Verwenden Sie Manipulations Ereignisse, um den Astronaut mit ihren Händen zu verschieben.
* Geben Sie Feedback für den Cursor an, damit der Benutzer weiß, wann die Bearbeitung verwendet werden kann.

### <a name="instructions"></a>Anweisungen

Mit GestureManager.cs und AstronautManager.cs können wir folgende Aktionen ausführen:

1. Verwenden Sie das Speech-Schlüsselwort "**Move Astronaut**", um **Manipulations** Gesten zu aktivieren und "**Astronaut**" zu deaktivieren, um Sie zu deaktivieren.
2. Wechseln Sie zur Reaktion auf die **Erkennungs Gestenerkennung**.

Los geht's.

1. Erstellen Sie im **Hierarchie** Panel ein neues leeres gameobject-Objekt. Nennen Sie es "**astronautmanager**".
2. Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .
3. Geben Sie im Menü im Suchfeld den Suchbegriff " **Astronaut Manager**" ein. Wählen Sie das Suchergebnis aus.
4. Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .
5. Geben Sie im Menü die **Eingabe Quelle**für die Suchbegriff Sprache ein. Wählen Sie das Suchergebnis aus.

Nun fügen wir die Sprachbefehle hinzu, die erforderlich sind, um den Interaktions Zustand des Astronauten zu steuern.

1. Erweitern Sie im **Inspektor**den Abschnitt **Schlüsselwörter** .
2. Klicken Sie auf die **+** auf der rechten Seite, um ein neues Schlüsselwort hinzuzufügen.
3. Geben Sie das Schlüsselwort als **Move Astronaut**ein. Wenn gewünscht, können Sie eine Tastenkombination hinzufügen.
4. Klicken Sie auf die **+** auf der rechten Seite, um ein neues Schlüsselwort hinzuzufügen.
5. Geben Sie das Schlüsselwort zum **Drehen des Astronauten**ein. Wenn gewünscht, können Sie eine Tastenkombination hinzufügen.
6. Der entsprechende Handlercode finden Sie in **GestureAction.cs**im **iredner Handler. onredner keywordrecognized** -Handler.

![Einrichten der Spracheingabe Quelle für Kapitel 4](images/holograms211-speech.png)

Als nächstes richten wir das Manipulations Feedback für den Cursor ein.

1. Suchen Sie im **Projekt** Panel **holograms** -Ordner das **pathingfeedback** -Asset.
2. Ziehen Sie die vorfab **pathingfeedback** per Drag & amp; Drop auf das **Cursor** Objekt in der **Hierarchie**.
3. Klicken Sie im **Hierarchie** Panel auf " **Cursor**".
4. Ziehen Sie das **pathingfeedback** -Objekt per Drag & amp; Drop aus der- **Hierarchie** auf die Eigenschaft für die Eigenschaft "" **für das** **festgelegte Spiel** im **Inspektor**.

Nun müssen Sie **GestureAction.cs** Code hinzufügen, um Folgendes zu ermöglichen:

1. Fügen Sie der **imanipulationhandler. onmanipulationaktualisierte** -Funktion Code hinzu, mit dem der Astronaut verschoben wird, wenn eine **Manipulations** Bewegung erkannt wird.
2. Berechnen Sie den **Bewegungsvektor** , um zu bestimmen, an welcher Stelle der Astronaut auf der Grundlage der Handposition verschoben werden soll.
3. **Verschieben** Sie den Astronauten an die neue Position.

Vervollständigen Sie die Codierungs Übung 4. a in **GestureAction.cs**, oder verwenden Sie unten unsere abgeschlossene Lösung:

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a>Erstellen und bereitstellen

* Erstellen Sie in Unity neu, und erstellen Sie Sie aus Visual Studio, um die app in hololens auszuführen.
* Bewegen Sie Ihre Hand vor den hololens, und erhöhen Sie den Indexfinger, damit er nachverfolgt werden kann.
* Fokussieren Sie den Cursor auf den Astronaut.
* Nehmen Sie an, Sie können den Astronauten mit einer Manipulations Bewegung verschieben.
* Im Cursor sollten vier Pfeile angezeigt werden, um anzugeben, dass das Programm nun auf Manipulations Ereignisse antwortet.
* Verringern Sie den Finger des Indexes auf Ihren Ziehpunkt, und halten Sie ihn zusammen.
* Wenn Sie die Hand herum bewegen, wird der Astronaut ebenfalls verschoben (Dies ist eine Bearbeitung).
* Erhöhen Sie den Finger des Indexes, um die Bearbeitung des Astronauten zu verhindern.
* Hinweis: Wenn Sie "Move Astronaut" nicht vor Hand bewegen, wird stattdessen die Navigations Geste verwendet.
* Nehmen wir an, dass Sie den "Astronaut" drehen, um zum rotatable-Status zurück

## <a name="chapter-5---model-expansion"></a>Kapitel 5: Modell Erweiterung

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>Ziele

* Erweitern Sie das Modell "Astronaut" in mehrere kleinere Teile, mit denen der Benutzer interagieren kann.
* Verschieben Sie jedes Stück einzeln mithilfe von Navigations-und Bearbeitungs Gesten.

### <a name="instructions"></a>Anweisungen

In diesem Abschnitt werden die folgenden Aufgaben ausgeführt:

1. Fügen Sie ein neues Schlüsselwort "**Expand Model**" hinzu, um das Modell des Astronauten zu erweitern.
2. Fügen Sie ein neues Schlüsselwort "**Modell zurücksetzen**" hinzu, um das Modell in seine ursprüngliche Form zurückzugeben.

Hierzu fügen wir der Spracheingabe Quelle aus dem vorherigen Kapitel zwei weitere Schlüsselwörter hinzu. Wir veranschaulichen auch eine weitere Möglichkeit, Erkennungs Ereignisse zu behandeln.

1. Klicken Sie im **Inspektor** auf " **astronautmanager** ", und erweitern Sie im **Inspektor**den Abschnitt " **Schlüsselwörter** ".
2. Klicken Sie auf die **+** auf der rechten Seite, um ein neues Schlüsselwort hinzuzufügen.
3. Geben Sie das Schlüsselwort als Erweiterungs **Modell**ein. Wenn gewünscht, können Sie eine Tastenkombination hinzufügen.
4. Klicken Sie auf die **+** auf der rechten Seite, um ein neues Schlüsselwort hinzuzufügen.
5. Geben Sie das Schlüsselwort als **Modell zurücksetzen**ein. Wenn gewünscht, können Sie eine Tastenkombination hinzufügen.
6. Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .
7. Geben Sie im Menü den **Eingabe Handler**für die Suchbegriff Sprache ein. Wählen Sie das Suchergebnis aus.
8. Überprüfen Sie, ob es sich um einen **globalen Listener handelt**, da Sie möchten, dass diese Befehle unabhängig vom verwendeten gameobject funktionieren.
9. Klicken Sie auf die Schaltfläche **+** , und wählen Sie Modell aus der Dropdown Liste Schlüsselwort **erweitern**
10. Klicken Sie unter Antwort auf die **+** , und ziehen Sie den Wert von **astronautmanager** aus der **Hierarchie** in das Feld **None (Object)** .
11. Klicken Sie nun auf die Dropdown Liste **keine Funktion** , und wählen Sie dann " **astronautmanager**" und " **expandmodelcommand**"
12. Klicken Sie auf die **+** Schaltfläche des Spracheingabe Handlers, und wählen Sie aus der Dropdown Liste Schlüsselwort **zurück**
13. Klicken Sie unter Antwort auf die **+** , und ziehen Sie den Wert von **astronautmanager** aus der **Hierarchie** in das Feld **None (Object)** .
14. Klicken Sie nun auf die Dropdown Liste **keine Funktion** , und wählen Sie dann " **astronautmanager**" und dann " **resetmodelcommand**"

![Einrichten der Spracheingabe Quelle und des Handlers für Kapitel 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>Erstellen und bereitstellen

* Probieren Sie es aus! Erstellen Sie die APP, und stellen Sie Sie in den hololens bereit.
* Beispiel: **Erweitern Sie Modell** , um das erweiterte Modell des Astronauten anzuzeigen.
* Verwenden Sie die **Navigation** , um einzelne Teile der astronautenfarbe zu drehen.
* Nehmen Sie an, Sie können den **Astronauten verschieben** und dann die **Bearbeitung** verwenden, um einzelne Teile des Astronauten zu verschieben.
* Nehmen Sie an, Sie können den **Astronauten rotieren** , um die Teile
* Nehmen Sie beispielsweise **Reset Model** an, um den Astronaut an seine ursprüngliche Form zurückzugeben.

## <a name="the-end"></a>Das Ende

Gratulation! Sie haben nun die **Eingabe 211: Geste**abgeschlossen.

* Sie wissen, wie Hand Verfolgungs-, Navigations-und Bearbeitungs Ereignisse erkannt und beantwortet werden.
* Sie verstehen den Unterschied zwischen Navigation und Manipulations Gesten.
* Sie wissen, wie Sie den Cursor so ändern können, dass er visuelles Feedback bereitstellt, wenn eine Hand entdeckt wird, wenn eine Hand verloren geht, und für den Fall, dass ein Objekt verschiedene Interaktionen unterstützt (Navigation und Bearbeitung).
