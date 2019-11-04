---
title: Grundlagen 101-Projekt mit Gerät abschließen
description: Befolgen Sie diese exemplarische Vorgehensweise zum Programmieren mit Unity, Visual Studio und hololens, um die Grundlagen von Windows Mixed Reality kennenzulernen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Gemischte Realität, Windows Mixed Reality, hololens, Hologram, Academy, Tutorial
ms.openlocfilehash: 456aeea88b0d7f51acb52156d8139ec2df06883a
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434716"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es wurde [eine neue Reihe von Tutorials](mrlearning-base.md) für hololens 2 gepostet.

<br>

# <a name="mr-basics-101-complete-project-with-device"></a>Grundlagen 101: Projekt mit Gerät abschließen

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

In diesem Tutorial werden Sie durch ein vollständiges Projekt geführt, das in Unity integriert ist, das grundlegende Windows Mixed Reality-Features in hololens veranschaulicht, einschließlich [Blick](gaze-and-commit.md), [Gesten](gaze-and-commit.md#composite-gestures), [Spracheingabe](voice-input.md), [räumlichem Sound](spatial-sound.md) und [räumlicher Zuordnung](spatial-mapping.md) . .

Das Tutorial dauert ungefähr 1 Stunde.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>Grundlagen 101: Projekt mit Gerät abschließen</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Bevor Sie beginnen

### <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md)konfiguriert ist.
* Ein hololens-Gerät, das [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode)ist.

### <a name="project-files"></a>Projektdateien

* Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) , die für das Projekt erforderlich sind. Erfordert Unity 2017,2 oder höher.
  * Wenn Sie weiterhin Unity 5,6-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).
  * Wenn Sie weiterhin Unity 5,5-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).
  * Wenn Sie weiterhin Unity 5,4-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).
* Deinstallieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht zugänglichen Speicherort. Behalten Sie den Ordnernamen **Origami**bei.

>[!NOTE]
>Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).

## <a name="chapter-1---holo-world"></a>Kapitel 1: "Holo" World

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

In diesem Kapitel richten wir das erste Unity-Projekt ein und durchlaufen den Build-und Bereitstellungs Prozess.

### <a name="objectives"></a>Ziele

* Einrichten von Unity für die Holographic-Entwicklung.
* Erstellen Sie ein Hologram.
* Sehen Sie sich ein von Ihnen vorgenommene – Hologramm an.

### <a name="instructions"></a>Anweisungen

* Starten Sie Unity.
* Wählen Sie **Öffnen**aus.
* Geben Sie Location als den Ordner **Origami** ein, den Sie zuvor nicht archiviert haben.
* Wählen Sie **Origami** , und klicken Sie auf **Ordner auswählen**.
* Da das **Origami** -Projekt keine Szene enthält, speichern Sie die leere Standard Szene in einer neuen Datei, indem Sie Folgendes verwenden: **File** / **Szene speichern als**.
* Nennen Sie die neue Szene **Origami** , und klicken Sie auf die Schaltfläche **Speichern** .

#### <a name="setup-the-main-virtual-camera"></a>Einrichten der virtuellen Hauptkamera

* Wählen Sie im Bereich **Hierarchie**die Option **Hauptkamera**aus.
* Legen Sie im **Inspektor** die Transformations Position auf **0, 0, 0**fest.
* Suchen Sie die Eigenschaft **Clear Flags** , und ändern Sie die Dropdown Liste von **Skybox** in voll **Tonfarbe**.
* Klicken Sie auf das Feld **Hintergrund** , um eine Farbauswahl zu öffnen.
* Legen Sie **R, G, B und A** auf **0**fest.

#### <a name="setup-the-scene"></a>Einrichten der Szene

* Klicken Sie im **Hierarchie Panel**auf **Erstellen** , und erstellen Sie eine **leere**.
* Klicken Sie mit der rechten Maustaste auf das neue **gameobject** und wählen Sie umbenennen Benennen Sie das gameobject in **origamicollection**um.
* Wählen Sie im Projekt Panel im Ordner **holograms** (Objekte erweitern und holograms aus, oder Doppelklicken Sie im Projekt Panel auf den Ordner holograms):
  * Ziehen Sie die **Phase** in die Hierarchie, um ein untergeordnetes Element von **origamicollection**zu sein.
  * Ziehen Sie **Sphere1** in die Hierarchie, um ein untergeordnetes Element von **origamicollection**zu sein.
  * Ziehen Sie **Sphere2** in die Hierarchie, um ein untergeordnetes Element von **origamicollection**zu sein.
* Klicken Sie im Bereich **Hierarchie** mit der rechten Maustaste auf das Objekt **direktional hell** , und wählen Sie **Löschen**aus
* Ziehen Sie aus dem Ordner **holograms** die **Beleuchtung** in das Stammverzeichnis des Bereichs **Hierarchie**.
* Wählen Sie in der **Hierarchie**die Option **origamicollection**aus.
* Legen Sie im **Inspektor**die Transformations Position auf **0,-0,5, 2,0**fest.
* Klicken Sie in Unity auf die **Wiedergabe** Schaltfläche, um eine Vorschau der holograms anzuzeigen
* Die Origami-Objekte sollten im Vorschaufenster angezeigt werden.
* Drücken **Sie** ein zweites Mal, um den Vorschaumodus zu verhindern.

#### <a name="export-the-project-from-unity-to-visual-studio"></a>Exportieren des Projekts aus Unity in Visual Studio

* Wählen Sie in Unity **Datei > Buildeinstellungen**aus.
* Wählen Sie in der Liste **Plattform** **universelle Windows-Plattform** aus, und klicken Sie auf **Plattform wechseln**.
* Legen Sie das **SDK** auf **Universal 10** und den Buildtyp auf **D3D**fest.
* Überprüfen Sie **Unity C# -Projekte**.
* Klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.
* Klicken Sie auf **Erstellen**.
* Erstellen Sie im Datei-Explorer-Fenster, das angezeigt wird, einen **neuen Ordner** mit dem Namen "App".
* Klicken Sie einfach auf den **app-Ordner**.
* Drücken **Sie Ordner auswählen**.
* Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.
* Öffnen Sie den **App** -Ordner.
* Öffnen Sie (Doppelklicken Sie auf) **Origami. sln**.
* Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x86**.
* Klicken Sie auf den Pfeil neben der Schaltfläche Gerät, und wählen Sie **Remote Computer** aus, um die Bereitstellung über Wi-Fi durchzuführen.
  * Legen Sie die **Adresse** auf den Namen oder die IP-Adresse der hololens fest. Wenn Sie die IP-Adresse Ihres Geräts nicht kennen, suchen Sie in den **Einstellungen > Netzwerk & Internet > Erweiterte Optionen** , oder Fragen Sie Cortana **"Hey Cortana, was ist meine IP-Adresse?"** .
  * Wenn die hololens über USB angefügt sind, können Sie stattdessen ein **Gerät** für die Bereitstellung über USB auswählen.
  * Lassen Sie den **Authentifizierungsmodus** auf **Universal**festgelegt.
  * Klicken Sie auf **auswählen**

* Klicken Sie auf **Debuggen > Starten ohne Debugging** , oder drücken Sie **STRG + F5**. Wenn Sie die Bereitstellung auf Ihrem Gerät zum ersten Mal durchführt, müssen Sie [es mit Visual Studio](using-visual-studio.md#pairing-your-device)koppeln.

* Das Projekt Origami wird nun erstellt, in den hololens bereitgestellt und dann ausgeführt.
* Platzieren Sie Ihre hololens, und sehen Sie sich an, um Ihre neuen holograms anzuzeigen.

## <a name="chapter-2---gaze"></a>Kapitel 2: Blick

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

In diesem Kapitel werden die ersten von drei Möglichkeiten vorgestellt, mit denen Sie mit ihren holograms interagieren [können.](gaze-and-commit.md)

### <a name="objectives"></a>Ziele

* Visualisieren Sie Ihren Blick mithilfe eines weltweit gesperrten Cursors.

### <a name="instructions"></a>Anweisungen

* Wechseln Sie zurück zu Ihrem Unity-Projekt, und schließen Sie das Fenster mit den Buildeinstellungen, wenn es noch geöffnet ist.
* Wählen Sie im **Projekt Panel**den Ordner **holograms** aus.
* Ziehen Sie das **Cursor** Objekt in das **Hierarchie Panel** auf der Stamm Ebene.
* Doppelklicken Sie auf das **Cursor** Objekt, um es genauer zu betrachten.
* Klicken Sie im Projekt Panel mit der rechten Maustaste auf den Ordner **Scripts** .
* Klicken Sie auf das Untermenü **Erstellen** .
* Wählen Sie  **C# Skript**aus.
* Nennen Sie das Skript **worldcursor**. Hinweis: bei dem Namen wird die Groß-/Kleinschreibung beachtet. Sie müssen die Erweiterung ". cs" nicht hinzufügen.
* Wählen Sie im **Hierarchie Panel**das **Cursor** Objekt aus.
* Verschieben Sie das **worldcursor** -Skript per Drag & amp; Drop in den Bereich **Inspector**.
* Doppelklicken Sie auf das Skript **worldcursor** , um es in Visual Studio zu öffnen.
* Fügen Sie diesen Code in **WorldCursor.cs** ein, und **Speichern Sie alle**.

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move the cursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* Erstellen Sie die APP aus dem **Datei > den Buildeinstellungen**neu.
* Kehren Sie zur Visual Studio-Projekt Mappe zurück, die Sie zuvor für die Bereitstellung in hololens verwendet haben
* Wählen Sie bei entsprechender Aufforderung "alle neu laden" aus.
* Klicken Sie auf **Debuggen > Starten ohne Debugging** , oder drücken Sie **STRG + F5**.
* Sehen Sie sich nun die Szene an, und sehen Sie, wie der Cursor mit der Form von Objekten interagiert.

## <a name="chapter-3---gestures"></a>Kapitel 3: Gesten

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

In diesem Kapitel wird die Unterstützung für [Gesten](gaze-and-commit.md#composite-gestures)hinzugefügt. Wenn der Benutzer eine Papierkugel auswählt, wird die Kugel durch das Aktivieren der Schwerkraft mit der Physik-Engine von Unity erreicht.

### <a name="objectives"></a>Ziele

* Steuern Sie Ihre Hologramme mit der SELECT-Geste.

### <a name="instructions"></a>Anweisungen

Wir beginnen mit der Erstellung eines Skripts und können dann die SELECT-Geste erkennen.

* Erstellen Sie im Ordner **Scripts** ein Skript mit dem Namen " **gazegesturemanager**".
* Ziehen Sie das Skript " **gazegesturemanager** " auf das Objekt " **origamicollection** " in der Hierarchie.
* Öffnen Sie das Skript " **gazegesturemanager** " in Visual Studio, und fügen Sie den folgenden Code hinzu:

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Awake()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* Erstellen Sie ein weiteres Skript im Ordner "Scripts", diesmal mit dem Namen **spherecommands**.
* Erweitern Sie das Objekt **origamicollection** in der Hierarchie Ansicht.
* Ziehen Sie das **spherecommands** -Skript auf das **Sphere1** -Objekt im Hierarchie Panel.
* Ziehen Sie das **spherecommands** -Skript auf das **Sphere2** -Objekt im Hierarchie Panel.
* Öffnen Sie das Skript in Visual Studio zur Bearbeitung, und ersetzen Sie den Standard Code durch den folgenden Code:

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* Exportieren, erstellen und Bereitstellen der app in ihren hololens.
* Sehen Sie sich einen der Bereiche an.
* Führen Sie die SELECT-Geste aus, und beobachten Sie den unteren Bereich der Kugel.

## <a name="chapter-4---voice"></a>Kapitel 4: Stimme

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

In diesem Kapitel fügen wir die Unterstützung für zwei [Sprachbefehle](voice-input.md)hinzu: "Reset World", um die gelöschten Bereiche an ihren ursprünglichen Speicherort zurückzugeben, und "Drop Sphere", um die Kugel zu verlieren.

### <a name="objectives"></a>Ziele

* Fügen Sie Sprachbefehle hinzu, die immer im Hintergrund lauschen.
* Erstellen Sie ein – Hologramm, das auf einen Voice-Befehl reagiert.

### <a name="instructions"></a>Anweisungen

* Erstellen Sie **im Ordner Skripts ein** Skript mit dem Namen " **Redner-Manager**".
* Ziehen Sie das **sprach-Manager** -Skript auf das **origamicollection** -Objekt in der Hierarchie.
* Öffnen Sie das **sprach-Manager** -Skript in Visual Studio.
* Kopieren Sie diesen Code, und fügen Sie ihn in **SpeechManager.cs** ein. **Speichern Sie alle**

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* Öffnen Sie das **spherecommands** -Skript in Visual Studio.
* Aktualisieren Sie das Skript wie folgt:

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* Exportieren, erstellen und Bereitstellen der app in ihren hololens.
* Sehen Sie sich einen der Bereiche an, und sagen Sie "**Drop Sphere**".
* Sagen Sie "**Welt zurücksetzen**", um Sie wieder an Ihre ursprünglichen Positionen zu bringen.

## <a name="chapter-5---spatial-sound"></a>Kapitel 5: räumlicher Sound

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

In diesem Kapitel werden wir der App Musik hinzufügen und dann bei bestimmten Aktionen Soundeffekte auslöst. Wir verwenden den [räumlichen Ton](spatial-sound.md) , um Klänge an einem bestimmten Speicherort im 3D-Raum zu geben.

### <a name="objectives"></a>Ziele

* Hören Sie holograms in ihrer Welt.

### <a name="instructions"></a>Anweisungen

* Wählen Sie in Unity im oberen Menü **> Projekteinstellungen > Audiodatei bearbeiten** aus.
* Suchen Sie im Inspektor-Panel auf der rechten Seite die Einstellung für das **spatializer-Plug** -in, und wählen Sie **MS HRTF spatializer**aus.
* Ziehen Sie das **Ambiente** -Objekt aus dem Ordner **holograms** im Projekt Panel auf das Objekt **origamicollection** im Bereich Hierarchie.
* Wählen Sie **origamicollection** aus, und suchen Sie im Inspektor-Panel die Komponente **Audioquelle** . Ändern Sie die folgenden Eigenschaften:
  * Überprüfen Sie die **spatialize** -Eigenschaft.
  * Überprüfen Sie die wieder **Gabe bei wach**.
  * Ändern Sie **räumliche Blend** in **3D** , indem Sie den Schieberegler nach rechts ziehen. Wenn Sie den Schieberegler verschieben, sollte der Wert von 0 in 1 geändert werden.
  * Überprüfen Sie die **Loop** -Eigenschaft.
  * Erweitern Sie **3D-Sound Einstellungen**, und geben Sie **0,1** für die **Doppler-Ebene**ein.
  * Legen Sie **volumenrolloff** auf **logarithmische Rolloff**fest.
  * Legen Sie **Max Distance** auf **20**fest.
* Erstellen Sie im Ordner **Scripts** ein Skript mit dem Namen " **spheresounds**".
* Ziehen Sie **spheresounds** per Drag & Drop auf die Objekte **Sphere1** und **Sphere2** in der Hierarchie.
* Öffnen Sie " **spheresounds** " in Visual Studio, aktualisieren Sie den folgenden Code, und **Speichern Sie alle**.

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* Speichern Sie das Skript, und kehren Sie zu Unity zurück.
* Exportieren, erstellen und Bereitstellen der app in ihren hololens.
* Bewegen Sie sich näher und weiter von der Stufe aus, und schalten Sie die Seite auf die Seite, um die Geräusche zu ändern.

## <a name="chapter-6---spatial-mapping"></a>Kapitel 6: räumliche Zuordnung

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

Nun verwenden wir die [räumliche Zuordnung](spatial-mapping.md) , um das Spiel Board in einem realen Objekt in der realen Welt zu platzieren.

### <a name="objectives"></a>Ziele

* Bringen Sie Ihre reale Welt in die virtuelle Welt.
* Platzieren Sie Ihre Hologramme, wo Sie für Sie am wichtigsten sind.

### <a name="instructions"></a>Anweisungen

* Klicken Sie in Unity im Projekt Panel auf den Ordner **holograms** .
* Ziehen Sie das Objekt für die **räumliche Zuordnung** in den Stamm der **Hierarchie**.
* Klicken Sie in der Hierarchie auf das **räumliche Mapping** -Objekt.
* Ändern Sie im **Inspektor-Panel**die folgenden Eigenschaften:
  * Aktivieren Sie das Kontrollkästchen **visuelle Meshes zeichnen** .
  * Suchen Sie das **Zeichnungs Material** , und klicken Sie auf den Kreis rechts. Geben Sie im Feld oben den Text "**Draht Modell**" in das Suchfeld ein. Klicken Sie auf das Ergebnis, und schließen Sie das Fenster. Wenn Sie dies tun, sollte der Wert für Zeichnungs Material auf Wireframe festgelegt werden.
* Exportieren, erstellen und Bereitstellen der app in ihren hololens.
* Wenn die app ausgeführt wird, überlagert ein Draht Modell-Mesh ihre reale Welt.
* Sehen Sie sich an, wie sich eine parallele Kugel auf der Ebene befindet und auf den Boden zeigt.

Nun zeigen wir Ihnen, wie Sie die origamicollection an einen neuen Speicherort verschieben:

* Erstellen Sie im Ordner **Scripts** ein Skript mit dem Namen " **taptoplaceparent**".
* Erweitern Sie in der- **Hierarchie**die **origamicollection** , und wählen Sie das **Stage** -Objekt aus.
* Ziehen Sie das Skript **taptoplaceparent** auf das Stage-Objekt.
* Öffnen Sie das Skript " **taptoplaceparent** " in Visual Studio, und aktualisieren Sie es wie folgt:

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* Exportieren, erstellen und Bereitstellen der app.
* Jetzt sollten Sie nun in der Lage sein, das Spiel an einem bestimmten Speicherort zu platzieren, indem Sie es mit der SELECT-Geste anordnen und dann an eine neue Stelle verschieben und die Auswahl Geste erneut verwenden.

## <a name="chapter-7---holographic-fun"></a>Kapitel 7: Holographic Fun

### <a name="objectives"></a>Ziele

* Zeigen Sie den Einstieg in eine Holographic-Unterwelt an.

### <a name="instructions"></a>Anweisungen

Nun zeigen wir Ihnen, wie Sie die Holographic-Unterwelt entdecken:

* Aus dem Ordner " **holograms** " im Projekt Panel:
  * Ziehen Sie **Underworld** in die Hierarchie, um ein untergeordnetes Element von **origamicollection**zu sein.
* Erstellen Sie im Ordner **Scripts** ein Skript mit dem Namen **hittarget**.
* Erweitern Sie in der- **Hierarchie**die " **origamicollection**".
* Erweitern Sie das **Stage** -Objekt, und wählen Sie das **Ziel** Objekt (blauer Lüfter) aus.
* Ziehen **Sie das hittarget** -Skript auf das **Ziel** Objekt.
* Öffnen Sie das **hittarget** -Skript in Visual Studio, und aktualisieren Sie es wie folgt:

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* Wählen Sie in Unity das **Ziel** Objekt aus.
* Zwei öffentliche Eigenschaften sind jetzt für die **Treffer Ziel** Komponente sichtbar, und Sie müssen auf Objekte in unserer Szene verweisen:
  * Ziehen Sie die Option " **Underworld** " aus dem Bereich **Hierarchie** in **die Eigenschaft für** die **Ziel** Komponente.
  * Ziehen Sie **Phase** aus dem Bereich **Hierarchie** auf das **Objekt, um** die Eigenschaft für die **Treffer Ziel** Komponente auszublenden.
* Exportieren, erstellen und Bereitstellen der app.
* Platzieren Sie die Origami-Auflistung auf der Etage, und verwenden Sie dann die Aktion auswählen, um einen Kugel Ablage Vorgang zu erstellen.
* Wenn die Kugel auf das Ziel (blauer Lüfter) trifft, tritt eine Explosion auf. Die Sammlung wird ausgeblendet, und ein Loch in der Unterwelt wird angezeigt.

## <a name="the-end"></a>Das Ende

Und das ist das Ende dieses Tutorials!

Sie haben Folgendes gelernt:

* Erstellen einer Holographic-app in Unity.
* Verwendung von Blick, Bewegung, Stimme, Sound und räumlicher Zuordnung.
* Erfahren Sie, wie Sie eine APP mit Visual Studio erstellen und bereitstellen.

Nun können Sie mit der Erstellung Ihrer eigenen Holographic-Benutzeroberflächen beginnen!

## <a name="see-also"></a>Weitere Informationen:

* [Grundlagen 101 e: vervollständigen eines Projekts mit Emulator](holograms-101e.md)
* [Anvisieren](gaze-and-commit.md)
* [Anvisieren mit dem Kopf und Ausführen](gaze-and-commit.md)
* [Spracheingabe](voice-input.md)
* [Raumklang](spatial-sound.md)
* [Räumliche Abbildung](spatial-mapping.md)
