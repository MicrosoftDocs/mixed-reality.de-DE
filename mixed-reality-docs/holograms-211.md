---
title: MR Eingabe 211 - Bewegung
description: Führen Sie diese Codierung Exemplarische Vorgehensweise, HoloLens, Unity und Visual Studio verwenden, um die Details der Bewegung Konzepte zu erfahren.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academy, tutorial, gesture
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596147"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

# <a name="mr-input-211-gesture"></a>MR Eingabe 211: Geste

[Bewegungen](gestures.md) Absicht Benutzers in Aktion zu aktivieren. Bei den Bewegungen können Benutzer mit Hologramme interagieren. In diesem Kurs erfahren wir, wie zum Nachverfolgen des Benutzers Hände auf Benutzereingaben reagieren, und Erteilen von Feedback an den Benutzer basierend auf Seite Zustand und den Speicherort.

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

In [MR Grundlagen 101](holograms-101.md), wir eine Geste für ein einfaches tippbewegung-Interaktion mit unserem Hologramme verwendet. Nun, wir über die tippbewegung Geste verschieben und neue Konzepte zu untersuchen:

* Erkennen Sie, wenn der Benutzer manuell nachverfolgt wird, und geben Sie Feedback an den Benutzer.
* Verwenden Sie eine Geste für ein Navigationsbereich, um unsere Hologramme drehen.
* Geben Sie Feedback, wenn des Benutzers manuell wird nicht aus der Sicht.
* Verwenden Sie Manipulation-Ereignisse, damit Benutzer Hologramme mit der Hand verschieben können.

In diesem Kurs werden wir die Unity-Projekts überdenken **Modell-Explorer**, die wir erstellt [MR Eingabe 210](holograms-210.md). Unser Freund Astronautenausweis werden zurück an unserem Seminar diese neuen Konzepte für die Bewegung, uns beim unterstützen.

>[!IMPORTANT]
>Die Videos in jeder der folgenden Kapitel eingebettet wurden mit einer älteren Version von Unity und dem Mixed Reality-Toolkit aufgezeichnet. Während die schrittweisen Anweisungen korrekt und aktuell sind, Sie möglicherweise Skripts und Visualisierungen in die entsprechenden Videos, die veraltet sind. Die Videos aus Gründen der Posterity bleiben, und es aber trotzdem anwenden, da die Konzepte behandelt.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td>MR Eingabe 211: Geste</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Bevor Sie beginnen

### <a name="prerequisites"></a>Vorraussetzungen

* Ein Windows 10-PCs mit dem richtigen konfiguriert [-Tools installiert](install-the-tools.md).
* Einige grundlegende C# Programmierkenntnisse.
* Sie sollten abgeschlossen haben [MR Grundlagen 101](holograms-101.md).
* Sie sollten abgeschlossen haben [MR Eingabe 210](holograms-210.md).
* Ein Gerät HoloLens [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Projektdateien

* Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) vom Projekt erforderlich sind. Ist Unity 2017.2 oder höher erforderlich.
* Un-Archive die Dateien auf dem Desktop oder andere einfach auf den Speicherort zugreifen.

>[!NOTE]
>Wenn Sie vor dem Herunterladen, den Quellcode ansehen möchten es [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).

### <a name="errata-and-notes"></a>Fehler und Anmerkungen zu dieser Version

* "Nur eigenen Code aktivieren" muss deaktiviert sein (*deaktiviert*) in Visual Studio unter Extras -> Optionen-Debuggen >, um die Haltepunkte in Ihrem Code.

## <a name="chapter-0---unity-setup"></a>Kapitel 0 - Setup für Unity

### <a name="instructions"></a>Anweisungen

1. Starten Sie Unity.
2. Wählen Sie **öffnen**.
3. Navigieren Sie zu der **Geste** Ordner Sie zuvor nicht archiviert.
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

## <a name="chapter-1---hand-detected-feedback"></a>Kapitel 1 - Seite erkannt, feedback

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>Ziele

* Nachverfolgungsereignisse zur hand zu abonnieren.
* Verwenden Sie Cursor Feedback, um Benutzern angezeigt, wenn eine Hand nachverfolgt wird.

### <a name="instructions"></a>Anweisungen

* In der **Hierarchie** erweitern Sie die **InputManager** Objekt.
* Suchen Sie nach, und wählen Sie die **GesturesInput** Objekt.

Die **InteractionInputSource.cs** Skript führt folgende Schritte aus:

1. Abonniert die Ereignisse InteractionSourceDetected und InteractionSourceLost.
2. Legt den HandDetected-Zustand.
3. Kündigt das Abonnement die InteractionSourceDetected und InteractionSourceLost-Ereignisse.

Als Nächstes führen wir die der Cursor aus Aktualisierung [MR Eingabe 210](holograms-210.md) in eine, die Feedback je nach den Aktionen des Benutzers anzeigt.

1. In der **Hierarchie** wählen die **Cursor** Objekt aus, und löschen Sie sie.
2. In der **Projekt** Bereich, suchen Sie nach **CursorWithFeedback** , und ziehen Sie ihn in das **Hierarchie** Bereich.
3. Klicken Sie auf **InputManager** in die **Hierarchie** Bereich, und ziehen Sie die **CursorWithFeedback** -Objekt aus der **Hierarchie** in der Die InputManager **SimpleSinglePointerSelector**des **Cursor** Feld am unteren Rand der **Inspektor**.
4. Klicken Sie auf die **CursorWithFeedback** in die **Hierarchie**.
5. In der **Inspektor** erweitern **Cursor Zustandsdaten** auf die **Objekt Cursor** Skript.

Die **Cursor Zustandsdaten** funktioniert wie folgt aus:

* Alle **beobachten** Status bedeutet, dass keine Hand erkannt und der Benutzer wird einfach untersucht.
* Alle **interagieren** Status bedeutet, dass eine Seite oder ein Controller erkannt wird.
* Alle **zeigen** Status bedeutet, dass der Benutzer wird ggf. ein Hologramm ansehen.

### <a name="build-and-deploy"></a>Erstellen und bereitstellen

* Verwenden Sie in Unity **Datei > Buildeinstellungen** um die Anwendung neu zu erstellen.
* Öffnen der **App** Ordner.
* Wenn sie nicht bereits geöffnet ist, öffnen Sie die **ModelExplorer Visual Studio-Projektmappe**.
  * (Wenn Sie bereits erstellt bzw. dieses Projekt in Visual Studio während der Einrichtung bereitgestellt, klicken Sie dann Sie können diese Instanz von Visual Studio öffnen und klicken Sie auf "Alles neu laden" Wenn Sie aufgefordert werden).
* Klicken Sie in Visual Studio auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.
* Nachdem die Anwendung, die HoloLens bereitstellt, schließen Sie die Fitbox mit der tippbewegung Bewegung.
* Verschieben Sie Ihre Hand an, und zeigen Sie Ihren Index Finger auf den Himmel Hand, die nachverfolgung zu starten.
* Verschieben Sie Ihre Hand links, rechts, oben und nach unten.
* Sehen Sie sich, wie sich der Cursor ändert, wenn Sie Ihre Hand erkannt wird, und klicken Sie dann aus der Ansicht verloren.
* Wenn Sie eine immersive Kopfhörer nutzen, müssen Sie eine Verbindung herstellen und trennen Ihre Controller. Dieses Feedback wird auf einem Gerät faszinierende weniger interessant, da ein verbundene Controller immer werden "verfügbar".

## <a name="chapter-2---navigation"></a>Kapitel 2 – Navigation

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>Ziele

* Verwenden Sie Gestenereignisse der Navigationsbereich, um die Astronautenausweis drehen.

### <a name="instructions"></a>Anweisungen

Um die Navigation Gesten in unserer app verwenden zu können, werden wir bearbeiten **GestureAction.cs** zu Objekten zu rotieren, wenn die Navigation-Aktion tritt auf. Darüber hinaus fügen wir Feedback an den Cursor angezeigt wird, wenn die Navigation verfügbar ist.

1. In der **Hierarchie** erweitern **CursorWithFeedback**.
2. In der **Hologramme** Ordner finden Sie die **ScrollFeedback** Asset.
3. Drag & drop die **ScrollFeedback** prefab auf die **CursorWithFeedback** "gameobject" in der **Hierarchie**.
4. Klicken Sie auf **CursorWithFeedback**.
5. In der **Inspektor** Bereich, klicken Sie auf die **Add Component** Schaltfläche.
6. Geben Sie im Menü, in das Suchfeld **CursorFeedback**. Wählen Sie das Suchergebnis.
7. Drag & drop die **ScrollFeedback** -Objekt aus der **Hierarchie** auf die **Scroll-Spielobjekt erkannt** -Eigenschaft in der **Cursor Feedback**-Komponente in die **Inspektor**.
8. In der **Hierarchie** wählen die **AstroMan** Objekt.
9. In der **Inspektor** Bereich, klicken Sie auf die **Add Component** Schaltfläche.
10. Geben Sie im Menü, in das Suchfeld **Geste Aktion**. Wählen Sie das Suchergebnis.

Öffnen Sie als Nächstes **GestureAction.cs** in Visual Studio. Codierung 2.c Übung, bearbeiten Sie das Skript aus, um die folgenden Schritte ausführen:

1. **Drehen Sie das AstroMan** Objekt immer eine Navigation-Aktion ausgeführt wird.
2. Berechnen der **RotationFactor** steuern den Grad der Drehung, die auf das Objekt angewendet.
3. **Das Objekt drehen** um die y-Achse, wenn der Benutzer ihre Westentasche nach links oder rechts bewegt.

Vollständige Codierung führt 2.c in Skripts oder Ersetzen Sie den Code mit der vollständigen Lösung unten:

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

Sie werden feststellen, dass die anderen Navigationsereignisse bereits mit einige Informationen gefüllt sind. Das "gameobject" auf des Toolkits push InputSystems modalen Stapel, sodass der Benutzer nicht den Fokus auf die Astronautenausweis beibehalten, nach der Rotation begonnen hat. Dementsprechend lesen wir das "gameobject" aus dem Stapel, sobald die Aktion abgeschlossen ist.

### <a name="build-and-deploy"></a>Erstellen und bereitstellen

1. Erstellen Sie die Anwendung in Unity und erstellen und Bereitstellen von Visual Studio für die Ausführung in die HoloLens.
2. Bestaunen Sie an die Astronautenausweis zwei Pfeile sollte auf beiden Seiten des Cursors angezeigt werden. Dieses neue visuelle Element gibt an, dass die Astronautenausweis gedreht werden kann.
3. Platzieren Sie Ihre Hand bereit Position (Index Finger vom Himmel zu holen ausgerichtet), damit die HoloLens Nachverfolgen Ihrer manuell gestartet werden kann.
4. Um die Astronautenausweis zu drehen, senken Sie Ihre Zeigefinger an eine Position verkleinern und dann verschieben Sie Ihre Hand, nach links oder rechts, um die Bewegung NavigationX auszulösen.

## <a name="chapter-3---hand-guidance"></a>Kapitel 3 – manuell Anleitungen

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>Ziele

* Verwenden **übergeben Anleitungen Bewertung** um vorherzusagen, beim Nachverfolgen von Hand verloren.
* Geben Sie **Feedback für den Cursor** angezeigt, wenn der Benutzer manuell der Kamera Rand der Ansicht nähert.

### <a name="instructions"></a>Anweisungen

1. In der **Hierarchie** wählen die **CursorWithFeedback** Objekt.
2. In der **Inspektor** Bereich, klicken Sie auf die **Add Component** Schaltfläche.
3. Geben Sie im Menü, in das Suchfeld **Hand Anleitungen**. Wählen Sie das Suchergebnis.
4. In der **Projekt** Bereich **Hologramme** Ordner finden Sie die **HandGuidanceFeedback** Asset.
5. Drag & drop die **HandGuidanceFeedback** Medienobjekt, auf die **Hand Anleitungen Indikator** -Eigenschaft in der **Inspektor** Bereich.

### <a name="build-and-deploy"></a>Erstellen und bereitstellen

* Erstellen Sie die Anwendung in Unity und erstellen und Bereitstellen von Visual Studio, um die app auf HoloLens auftreten.
* Bringen Sie Ihre Hand an, und lösen Sie Ihren Finger Index, der nachverfolgt werden.
* Starten Sie die Rotation der Astronautenausweis mit dieser Bewegung Navigation (Verkleinern der Zeigefinger und thumb-zusammen).
* Verschieben Sie Ihre Hand, ganz links, rechts, oben und unten.
* Wie Sie Ihre Hand den Rand des Rahmens Geste nähert ein Pfeil sollte angezeigt werden wird der Cursor, damit Sie gewarnt, dass diese manuell nachverfolgen verloren gehen. Der Pfeil gibt die Richtung, damit Ihre Seite zu verschieben, um zu verhindern, dass bei der nachverfolgung, verloren gehen.

## <a name="chapter-4---manipulation"></a>Kapitel 4: Bearbeitung

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>Ziele

* Verwenden Sie Manipulation-Ereignisse, um die Astronautenausweis mit der Hand zu verschieben.
* Geben Sie Feedback für den Cursor, damit der Benutzer wissen, wann die Bearbeitung verwendet werden kann.

### <a name="instructions"></a>Anweisungen

GestureManager.cs und AstronautManager.cs können wir die folgenden Schritte ausführen:

1. Verwenden Sie das Schlüsselwort der Sprache "**Astronautenausweis verschieben**" So aktivieren Sie **Manipulation** Gesten und "**drehen Astronautenausweis**" um sie zu deaktivieren.
2. Wechseln Sie zum Reagieren auf die **Stiftbewegungs-Erkennung von Manipulation**.

Los geht's.

1. In der **Hierarchie** erstellen ein neues leeres "gameobject". Nennen Sie es "**AstronautManager**".
2. In der **Inspektor** Bereich, klicken Sie auf die **Add Component** Schaltfläche.
3. Geben Sie im Menü, in das Suchfeld **Astronautenausweis Manager**. Wählen Sie das Suchergebnis.
4. In der **Inspektor** Bereich, klicken Sie auf die **Add Component** Schaltfläche.
5. Geben Sie im Menü, in das Suchfeld **Speech-Eingabequelle**. Wählen Sie das Suchergebnis.

Wir fügen jetzt die Spracherkennung-Befehle, die erforderlich sind, um den Interaktionszustand des der Astronautenausweis zu steuern.

1. Erweitern Sie die **Schlüsselwörter** im Abschnitt der **Inspektor**.
2. Klicken Sie auf die **+** auf der rechten Seite ein neues Schlüsselwort hinzufügen.
3. Geben Sie das Schlüsselwort als **verschieben Astronautenausweis**. Eine Verknüpfung für die Schlüssel bei Bedarf hinzufügen können.
4. Klicken Sie auf die **+** auf der rechten Seite ein neues Schlüsselwort hinzufügen.
5. Geben Sie das Schlüsselwort als **drehen Astronautenausweis**. Eine Verknüpfung für die Schlüssel bei Bedarf hinzufügen können.
6. Der entsprechende Handlercode befinden sich **GestureAction.cs**in die **ISpeechHandler.OnSpeechKeywordRecognized** Handler.

![Wie Sie die Einrichtung der Spracherkennung Eingabequelle für Kapitel 4](images/holograms211-speech.png)

Richten Sie als Nächstes die Manipulation Feedback für den Cursor.

1. In der **Projekt** Bereich **Hologramme** Ordner finden Sie die **PathingFeedback** Asset.
2. Drag & drop die **PathingFeedback** prefab auf die **CursorWithFeedback** -Objekt in der **Hierarchie**.
3. In der **Hierarchie** Bereich, klicken Sie auf **CursorWithFeedback**.
4. Drag & drop die **PathingFeedback** -Objekt aus der **Hierarchie** auf die **Pfade erkannt Spielobjekt** -Eigenschaft in der **Cursor Feedback**-Komponente in die **Inspektor**.

Nun wir zum Hinzufügen von Code müssen **GestureAction.cs** um Folgendes zu aktivieren:

1. Fügen Sie Code in die **IManipulationHandler.OnManipulationUpdated** -Funktion, die die Astronautenausweis verschoben wird bei einer **Manipulation** Geste erkannt wird.
2. Berechnen der **Bewegung Vektor** um zu bestimmen, in denen die Astronautenausweis zu verschoben werden soll basierend auf Seite Position.
3. **Verschieben Sie** der Astronautenausweis an die neue Position.

Vollständige Codierung 4.a in Übung **GestureAction.cs**, oder verwenden Sie unsere abgeschlossenen Lösung unten:

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

* In Unity neu erstellen, und klicken Sie dann erstellen und Bereitstellen von Visual Studio zum Ausführen der app in HoloLens.
* Verschieben Sie Ihre Hand vor die HoloLens, und erhöhen Sie Ihre Zeigefinger, sodass sie nachverfolgt werden kann.
* Konzentrieren Sie sich des Cursors über der Astronautenausweis.
* Sagen Sie 'Astronautenausweis verschieben", um die Astronautenausweis mit einer Bewegung der Manipulation zu verschieben.
* Vier Pfeile sollte angezeigt werden, cursorbesitzer im Cursor, um anzugeben, dass die Anwendung nun auf Manipulation-Ereignisse reagieren.
* Senken Sie Ihre Zeigefinger auf Ihre Thumb-Steuerelement, und bleiben Sie gequetscht zusammen.
* Wenn Sie Ihre Hand zu bewegen, wird zu den Astronautenausweis verschoben (Dies ist ein Manipulation).
* Lösen Sie Ihren Finger Index, um die Astronautenausweis Bearbeitung zu beenden.
* Hinweis: Wenn Sie "Astronautenausweis verschieben" vor dem Verschieben Ihre Hand nicht sagen, wird stattdessen die Aktion für die Navigation verwendet.
* Sagen Sie "Rotieren Astronautenausweis", um die rotatable Zustand wiederherzustellen.

## <a name="chapter-5---model-expansion"></a>Kapitel 5 – Model-Erweiterung

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>Ziele

* Erweitern Sie das Modell Astronautenausweis in mehrere, kleinere Teile, dass der Benutzer interagieren kann.
* Verschieben Sie jedes Datenelement, die einzeln über die Datennavigation und-Bearbeitung Gesten.

### <a name="instructions"></a>Anweisungen

In diesem Abschnitt werden wir die folgenden Aufgaben auszuführen:

1. Fügen Sie ein neues Schlüsselwort "**Modell erweitern**" um das Modell Astronautenausweis zu erweitern.
2. Fügen Sie ein neues Schlüsselwort "**Modell zurücksetzen**" auf das Modell in seiner ursprünglichen Form zurück.

Dazu müssen wir die Eingabequelle Sprache aus dem vorhergehenden Kapitel zwei weitere Schlüsselwörter hinzugefügt. Außerdem zeigen wir Ihnen eine weitere Möglichkeit zum Behandeln von Ereignissen der Erkennung.

1. Klicken Sie wieder auf **AstronautManager** in die **Inspektor** und erweitern Sie die **Schlüsselwörter** im Abschnitt der **Inspektor**.
2. Klicken Sie auf die **+** auf der rechten Seite ein neues Schlüsselwort hinzufügen.
3. Geben Sie das Schlüsselwort als **Modell erweitern**. Eine Verknüpfung für die Schlüssel bei Bedarf hinzufügen können.
4. Klicken Sie auf die **+** auf der rechten Seite ein neues Schlüsselwort hinzufügen.
5. Geben Sie das Schlüsselwort als **Modell zurücksetzen**. Eine Verknüpfung für die Schlüssel bei Bedarf hinzufügen können.
6. In der **Inspektor** Bereich, klicken Sie auf die **Add Component** Schaltfläche.
7. Geben Sie im Menü, in das Suchfeld **Spracherkennung Eingabe Handler**. Wählen Sie das Suchergebnis.
8. Überprüfen Sie **globale Listener ist**, da diese Befehle funktionieren Sie unabhängig von der "gameobject" konzentrieren wir sollten.
9. Klicken Sie auf die **+** Schaltfläche, und wählen **Modell erweitern** aus der Dropdownliste "Schlüsselwort".
10. Klicken Sie auf die **+** unter Antwort, und ziehen Sie die **AstronautManager** aus der **Hierarchie** in die **None (Objekt)** Feld.
11. Klicken Sie nun die **keine Funktion** Dropdownliste wählen **AstronautManager**, klicken Sie dann **ExpandModelCommand**.
12. Klicken Sie auf die Spracherkennung Eingabe des Handlers **+** Schaltfläche, und wählen **Modell zurücksetzen** aus der Dropdownliste "Schlüsselwort".
13. Klicken Sie auf die **+** unter Antwort, und ziehen Sie die **AstronautManager** aus der **Hierarchie** in die **None (Objekt)** Feld.
14. Klicken Sie nun die **keine Funktion** Dropdownliste wählen **AstronautManager**, klicken Sie dann **ResetModelCommand**.

![Wie Sie die Einrichtung der Eingabequelle Spracherkennung und -Handler für Kapitel 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>Erstellen und bereitstellen

* Probieren Sie es aus! Erstellen und Bereitstellen der app, die HoloLens.
* Sagen Sie **Modell erweitern** auf dem erweiterten Astronautenausweis-Modell finden Sie unter.
* Verwendung **Navigation** einzelne Teile die Farbe Astronautenausweis gedreht.
* Angenommen, **verschieben Astronautenausweis** und verwenden Sie dann **Manipulation** einzelne Teile die Farbe Astronautenausweis zu verschieben.
* Sagen Sie **drehen Astronautenausweis** auf die einzelnen Teile erneut drehen.
* Sagen Sie **Modell zurücksetzen** der Astronautenausweis in seiner ursprünglichen Form zurückgegeben.

## <a name="the-end"></a>Das Ende

Herzlichen Glückwunsch! Sie haben jetzt **MR Eingabe 211: Geste**.

* Sie wissen, wie Sie erkennen und darauf reagieren zu manuell nachverfolgen, Navigation und Bearbeitungsereignisse.
* Sie kennen den Unterschied zwischen Datennavigation und-Bearbeitung Gesten.
* Sie wissen, wie so ändern Sie den Cursor zum Bereitstellen von visuellem Feedback, wenn eine Hand erkannt wird, wenn gerade eine Hand gehen verloren, und wenn ein Objekt mit verschiedene Aktivitäten, die (Navigation Vs Manipulation) unterstützt.
