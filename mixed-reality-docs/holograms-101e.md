---
title: Grundlagen 101 e-Complete Project with Emulator
description: Befolgen Sie diese exemplarische Vorgehensweise, indem Sie Unity, Visual Studio und den hololens-Emulator verwenden, um die Grundlagen einer Holographic-Anwendung kennenzulernen.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Gemischte Realität, Windows Mixed Reality, hololens, Hologram, Academy, Tutorial, Emulator
ms.openlocfilehash: 77f7d497396937bf471a69fa514cef84ab0b699d
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522322"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a>Grundlagen 101 e: Projekt mit Emulator vervollständigen

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

In diesem Tutorial werden Sie durch ein vollständiges Projekt geführt, das in Unity integriert ist, das grundlegende Windows Mixed Reality-Features in hololens veranschaulicht, einschließlich [Blick](gaze.md), [Gesten](gestures.md), [Spracheingabe](voice-input.md), [räumlichem Sound](spatial-sound.md) und [räumlicher Zuordnung](spatial-mapping.md) . . Das Tutorial dauert ungefähr 1 Stunde.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>Grundlagen 101 e: Projekt mit Emulator vervollständigen</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Bevor Sie beginnen

### <a name="prerequisites"></a>Vorraussetzungen

* Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md)konfiguriert ist.

### <a name="project-files"></a>Projektdateien

* Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) , die für das Projekt erforderlich sind. Erfordert Unity 2017,2 oder höher.
  * Wenn Sie weiterhin Unity 5,6-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).
  * Wenn Sie weiterhin Unity 5,5-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).
  * Wenn Sie weiterhin Unity 5,4-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).
* Deinstallieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht zugänglichen Speicherort. Behalten Sie den Ordnernamen **Origami**bei.

>[!NOTE]
>Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).

## <a name="chapter-1---holo-world"></a>Kapitel 1: "Holo" World

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

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
* Speichern Sie die neue Szene: Datei / **Speichern**unter.
* Nennen Sie die Szene **Origami** , und klicken Sie auf die Schaltfläche **Speichern** .

#### <a name="setup-the-main-camera"></a>Einrichten der Hauptkamera

* Wählen Sie im Bereich **Hierarchie**die Option **Hauptkamera**aus.
* Legen Sie im **Inspektor** die Transformations Position auf **0, 0, 0**fest.
* Suchen Sie die Eigenschaft **Clear Flags** , und ändern Sie die Dropdown Liste von  **Skybox** in voll Tonfarbe.
* Klicken Sie auf das Feld **Hintergrund** , um eine Farbauswahl zu öffnen.
* Legen Sie **R, G, B und A** auf **0**fest.

#### <a name="setup-the-scene"></a>Einrichten der Szene

* Klicken Sie im **Hierarchie Panel**auf **Erstellen** , und erstellen Sie eine **leere**.
* Klicken Sie mit der rechten Maustaste auf das neue **gameobject** und wählen Sie umbenennen Benennen Sie das gameobject in **origamicollection**um.
* Aus dem Ordner " **holograms** " im **Projekt Panel**:
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

* Wählen Sie in Unity **Datei >** Buildeinstellungen aus.
* Wählen Sie in der Liste **Plattform** den **Windows Store** aus, und klicken Sie auf **Plattform wechseln**.
* Legen Sie das **SDK** auf **Universal 10** und den Buildtyp auf **D3D**fest.
* Überprüfen Sie **Unity C# -Projekte**.
* Klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.
* Klicken Sie auf **Player Einstellungen...** .
* Wählen Sie im Inspektor-Panel das **Windows Store-Logo**aus. Wählen Sie dann **Veröffentlichungs Einstellungen**aus.
* Wählen Sie im Abschnitt " **Funktionen** " die Funktionen " **Mikrofon** " und " **spatialperception** " aus.
* Klicken Sie im Fenster "Buildeinstellungen" auf " **Erstellen**".
* Erstellen Sie einen **neuen Ordner** mit dem Namen "App".
* Klicken Sie einfach auf den **app-Ordner**.
* Drücken **Sie Ordner auswählen**.
* Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.
* Öffnen Sie den **App** -Ordner.
* Öffnen Sie die Visual Studio-Projekt Mappe **Origami**.
* Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x86**.
  * Klicken Sie auf den Pfeil neben der Schaltfläche Gerät, und wählen Sie **hololens Emulator**aus.
  * Klicken Sie auf **Debuggen > Starten ohne Debugging** , oder drücken Sie **STRG + F5**.
  * Nach einiger Zeit wird der Emulator mit dem Origami-Projekt gestartet. Beim ersten Starten des [Emulators](using-the-hololens-emulator.md)kann es bis zu 15 Minuten dauern, bis der Emulator gestartet wird. Schließen Sie die Datei nach dem Start nicht.

## <a name="chapter-2---gaze"></a>Kapitel 2: Blick

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

In diesem Kapitel werden die ersten von drei Möglichkeiten vorgestellt, mit denen Sie mit ihren holograms interagieren [können.](gaze.md)

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
* Nennen Sie das Skript **worldcursor**. Hinweis: Beim Namen wird Groß- und Kleinschreibung beachtet. Sie müssen die Erweiterung ". cs" nicht hinzufügen.
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

            // Move thecursor to the point where the raycast hit.
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

* Erstellen Sie die APP aus dem **Datei >** den Buildeinstellungen neu.
* Kehren Sie zur Visual Studio-Projekt Mappe zurück, die zuvor zur Bereitstellung im Emulator verwendet wurde.
* Wählen Sie bei entsprechender Aufforderung "alle neu laden" aus.
* Klicken Sie auf **Debuggen > Starten ohne Debugging** , oder drücken Sie **STRG + F5**.
* Verwenden Sie den Xbox-Controller, um die Szene zu überprüfen. Beachten Sie, wie der Cursor mit der Form von-Objekten interagiert.

## <a name="chapter-3---gestures"></a>Kapitel 3: Gesten

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

In diesem Kapitel wird die Unterstützung für [Gesten](gestures.md)hinzugefügt. Wenn der Benutzer eine Papierkugel auswählt, wird die Kugel durch das Aktivieren der Schwerkraft mit der Physik-Engine von Unity erreicht.

### <a name="objectives"></a>Ziele

* Steuern Sie Ihre Hologramme mit der SELECT-Geste.

### <a name="instructions"></a>Anweisungen

Wir beginnen mit dem Erstellen eines Skripts, als die SELECT-Geste erkennen zu können.

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
    void Start()
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

* Exportieren, erstellen und Bereitstellen der APP auf dem hololens-Emulator.
* Sehen Sie sich die Szene an, und zentrieren Sie eine der Bereiche.
* Drücken Sie **die Schaltfläche** auf dem Xbox-Controller, oder drücken Sie die Leertaste, um die Auswahl Bewegung zu simulieren.

## <a name="chapter-4---voice"></a>Kapitel 4: Stimme

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

In diesem Kapitel wird die Unterstützung für zwei [Sprachbefehle](voice-input.md)hinzugefügt: "World zurücksetzen" gibt die gelöschten Bereiche an ihren ursprünglichen Speicherort zurück, und "Drop Sphere", um die Kugel zu verlieren.

### <a name="objectives"></a>Ziele

* Fügen Sie Sprachbefehle hinzu, die immer im Hintergrund lauschen.
* Erstellen Sie ein – Hologramm, das auf einen Voice-Befehl reagiert.

### <a name="instructions"></a>Anweisungen

* Erstellen Sie **im Ordner** Skripts ein Skript mit dem Namen " **Redner-Manager**".
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

* Exportieren, erstellen und Bereitstellen der APP auf dem hololens-Emulator.
* Der Emulator unterstützt das Mikrofon Ihres PCs und antwortet auf Ihre Stimme: passen Sie die Ansicht so an, dass sich der Cursor in einer der Bereiche befindet, und sagen Sie "Drop Sphere".
* Sagen Sie "**Welt zurücksetzen**", um Sie wieder an Ihre ursprünglichen Positionen zu bringen.

## <a name="chapter-5---spatial-sound"></a>Kapitel 5: räumlicher Sound

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

In diesem Kapitel werden wir der App Musik hinzufügen und dann bei bestimmten Aktionen Soundeffekte auslöst. Wir verwenden den [räumlichen Ton](spatial-sound.md) , um Klänge an einem bestimmten Speicherort im 3D-Raum zu geben.

### <a name="objectives"></a>Ziele

* Hören Sie holograms in ihrer Welt.

### <a name="instructions"></a>Anweisungen

* Wählen Sie in Unity im oberen Menü **> Projekteinstellungen > Audiodatei** aus.
* Suchen Sie die Einstellung **spatializer Plugin** , und wählen Sie **MS HRTF spatializer**aus.
* Ziehen Sie das **Ambiente** -Objekt aus dem Ordner **holograms** auf das Objekt **origamicollection** im Bereich Hierarchie.
* Wählen Sie **origamicollection** aus, und suchen Sie die Komponente **Audioquelle** . Ändern Sie die folgenden Eigenschaften:
  * Überprüfen Sie die **spatialize** -Eigenschaft.
  * Überprüfen Sie die wieder **Gabe bei wach**.
  * Ändern Sie **räumliche Blend** in **3D** , indem Sie den Schieberegler nach rechts ziehen.
  * Überprüfen Sie die **Loop** -Eigenschaft.
  * Erweitern Sie **3D-Sound Einstellungen**, und geben Sie **0,1** für die **Doppler-Ebene**ein.
  * Legen Sie **volumenrolloff** auf **logarithmische Rolloff**fest.
  * Legen Sie **Max Distance** auf **20**fest.
* Erstellen Sie im Ordner **Scripts** ein Skript mit dem Namen " **spheresounds**".
* Ziehen Sie " **spheresounds** " in die **Sphere1** -und **Sphere2** -Objekte in der Hierarchie.
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
* Exportieren, erstellen und Bereitstellen der APP auf dem hololens-Emulator.
* Tragen Sie Kopfhörer, um den vollständigen Effekt zu erhalten, und bewegen Sie sich näher und weiter von der Stufe aus, um die Geräusche zu ändern.

## <a name="chapter-6---spatial-mapping"></a>Kapitel 6: räumliche Zuordnung

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

Nun verwenden wir die [räumliche Zuordnung](spatial-mapping.md) , um das Spiel Board in einem realen Objekt in der realen Welt zu platzieren.

### <a name="objectives"></a>Ziele

* Bringen Sie Ihre reale Welt in die virtuelle Welt.
* Platzieren Sie Ihre Hologramme, wo Sie für Sie am wichtigsten sind.

### <a name="instructions"></a>Anweisungen

* Klicken Sie im Projekt Panel auf den Ordner **holograms** .
* Ziehen Sie das Objekt für die **räumliche Zuordnung** in den Stamm der **Hierarchie**.
* Klicken Sie in der Hierarchie auf das **räumliche Mapping** -Objekt.
* Ändern Sie im **Inspektor-Panel**die folgenden Eigenschaften:
  * Aktivieren Sie das Kontrollkästchen **visuelle Meshes zeichnen** .
  * Suchen Sie das **Zeichnungs Material** , und klicken Sie auf den Kreis rechts. Geben Sie im Feld oben den Text "**Draht Modell**" in das Suchfeld ein. Klicken Sie auf das Ergebnis, und schließen Sie das Fenster.
* Exportieren, erstellen und Bereitstellen der APP auf dem hololens-Emulator.
* Wenn die app ausgeführt wird, wird ein Mesh eines zuvor gescannten realen Wohnraums in Wireframe gerendert.
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
* Nun sollten Sie nun in der Lage sein, das Spiel an einem bestimmten Speicherort zu platzieren, indem Sie die Auswahl Bewegung (**eine** oder Leertaste) verwenden und dann an eine neue Position verschieben und die Auswahl erneut verwenden.

## <a name="the-end"></a>Das Ende

Und das ist das Ende dieses Tutorials!

Sie haben Folgendes gelernt:

* Erstellen einer Holographic-app in Unity.
* Verwendung von Blick, Bewegung, Stimme, Sounds und räumlicher Zuordnung.
* Erfahren Sie, wie Sie eine APP mit Visual Studio erstellen und bereitstellen.

Sie sind nun bereit, eigene Holographic apps zu erstellen!

## <a name="see-also"></a>Siehe auch

* [MR-Grundlagen 101: Vollständiges Projekt mit Gerät](holograms-101.md)
* [Anvisieren](gaze.md)
* [Gesten](gestures.md)
* [Spracheingabe](voice-input.md)
* [Raumklang](spatial-sound.md)
* [Räumliche Abbildung](spatial-mapping.md)
