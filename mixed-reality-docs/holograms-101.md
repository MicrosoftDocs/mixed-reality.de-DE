---
title: MR Grundlagen 101 – vollständige Projekt mit Gerät
description: Führen Sie diese Codierung Exemplarische Vorgehensweise mit Unity, Visual Studio und HoloLens zum Erlernen der Grundlagen von Windows Mixed Reality.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: gemischten Windows Mixed Reality, HoloLens, tatsächlich Hologram, Academy, Tutorial
ms.openlocfilehash: 043ffac8f30a4e29586478b5dca6ecccc2b5afd3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593969"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

<br>

# <a name="mr-basics-101-complete-project-with-device"></a>MR Basics 101: Vollständige Projekt mit Gerät

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

Dieses Tutorial führt Sie durch ein vollständiges-Projekt, erstellt in Unity, die Windows Mixed Reality-Kernfunktionen auf, einschließlich HoloLens veranschaulicht [bestaunen](gaze.md), [Gesten](gestures.md), [voice-Eingabe](voice-input.md), [räumliche Sound](spatial-sound.md) und [räumliche Zuordnung](spatial-mapping.md).

Das Tutorial dauert etwa eine Stunde bis zum Abschließen.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td>MR Basics 101: Vollständige Projekt mit Gerät</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Bevor Sie beginnen

### <a name="prerequisites"></a>Vorraussetzungen

* Ein Windows 10-PCs mit dem richtigen konfiguriert [-Tools installiert](install-the-tools.md).
* Ein Gerät HoloLens [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Projektdateien

* Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) vom Projekt erforderlich sind. Ist Unity 2017.2 oder höher erforderlich.
  * Wenn Sie weitere Unity 5.6-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).
  * Wenn Sie weitere Unity 5.5-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).
  * Wenn Sie weitere 5.4 von Unity-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).
* Un-Archive die Dateien auf dem Desktop oder andere einfach auf den Speicherort zugreifen. Behalten Sie den Ordnernamen als **Origami**.

>[!NOTE]
>Wenn Sie vor dem Herunterladen, den Quellcode ansehen möchten es [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).

## <a name="chapter-1---holo-world"></a>Kapitel 1: "Holo" world

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

In diesem Kapitel wir unser erstes Unity-Projekt und durchlaufen Sie den Build einrichten und Bereitstellen von Prozess.

### <a name="objectives"></a>Ziele

* Richten Sie Unity aus, für die holographic Entwicklung.
* Stellen Sie ggf. ein Hologramm.
* Finden Sie ggf. ein Hologramm, die Sie vorgenommen.

### <a name="instructions"></a>Anweisungen

* Starten Sie Unity.
* Wählen Sie **öffnen**.
* Geben Sie den Speicherort als dem **Origami** Ordner Sie zuvor nicht archiviert.
* Wählen Sie **Origami** , und klicken Sie auf **Ordner auswählen**.
* Da die **Origami** Projekt enthält keine Szene, speichern Sie die Szene leere standardmäßig eine neue Datei mit: **Datei** / **Szene speichern unter**.
* Benennen Sie die neue Szene **Origami** , und drücken Sie die **speichern** Schaltfläche.

#### <a name="setup-the-main-virtual-camera"></a>Einrichten der virtuellen Hauptkamera

* In der **Hierarchie Bereich**Option **Main Camera**.
* In der **Inspektor** positionieren Sie die Transformation **0,0,0**.
* Suchen der **löschen Flags** -Eigenschaft, und ändern die Dropdownliste aus **Skybox** zu **Volltonfarbe**.
* Klicken Sie auf die **Hintergrund** Feld, um ein Farbwähler zu öffnen.
* Legen Sie **R, G, B und A** zu **0**.

#### <a name="setup-the-scene"></a>Einrichten der Szene

* In der **Hierarchie Bereich**, klicken Sie auf **erstellen** und **leere erstellen**.
* Mit der rechten Maustaste den neuen **"gameobject"** und "Umbenennen" auswählen. Benennen Sie das "gameobject" zu **OrigamiCollection**.
* Von der **Hologramme** Ordner im Projektfenster (Erweitern Sie die Ressourcen und Hologramme wählen oder doppelklicken klicken Sie auf den Ordner Hologramme im Projektfenster):
  * Ziehen Sie **Phase** in die Hierarchie ein untergeordnetes Element des **OrigamiCollection**.
  * Ziehen Sie **Sphere1** in die Hierarchie ein untergeordnetes Element des **OrigamiCollection**.
  * Ziehen Sie **Sphere2** in die Hierarchie ein untergeordnetes Element des **OrigamiCollection**.
* Mit der rechten Maustaste die **gerichtetes Licht** -Objekt in der **Hierarchie Bereich** , und wählen Sie **löschen**.
* Von der **Hologramme** Ordner, ziehen Sie **Lichter** in das Stammverzeichnis der **Hierarchie Bereich**.
* In der **Hierarchie**, wählen die **OrigamiCollection**.
* In der **Inspektor**, positionieren Sie die Transformation **0, Verschiebung von -0,5 und 2.0**.
* Drücken Sie die **spielen** -Schaltfläche in Unity, um Ihre Hologramme der Vorschau anzuzeigen.
* Daraufhin sollte die Origami-Objekte im Vorschaufenster.
* Drücken Sie **spielen** ein zweites Mal im Vorschaumodus zu beenden.

#### <a name="export-the-project-from-unity-to-visual-studio"></a>Exportieren Sie das Projekt aus Unity in Visual Studio

* Im Unity-Option **Datei > Buildeinstellungen**.
* Wählen Sie **universelle Windows-Plattform** in die **Plattform** aus, und klicken Sie auf **Plattform wechseln**.
* Legen Sie **SDK** zu **universelle 10** und **Buildtyp** zu **D3D**.
* Überprüfen Sie **Unity C# Projekte**.
* Klicken Sie auf **öffnen Szenen hinzufügen** die Szene hinzufügen.
* Klicken Sie auf **Erstellen**.
* Erstellen Sie in dem Datei-Explorer-Fenster, das angezeigt wird, eine **neuer Ordner** mit dem Namen "App".
* Mausklick die **App-Ordner**.
* Drücken Sie **wählen Sie Ordner**.
* Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.
* Öffnen der **App** Ordner.
* (Doppelklicken Sie hier)-Open **Origami.sln**.
* Verwenden obere auf der Symbolleiste in Visual Studio, ändern Sie das Ziel vom Debugmodus in den **Version** und ARM, **X86**.
* Klicken Sie auf den Pfeil neben der Schaltfläche ", und wählen **Remotecomputer** über Wi-Fi bereitstellen.
  * Legen Sie die **Adresse** auf den Namen oder die IP-Adresse Ihrer HoloLens. Wenn Sie Ihre IP-Adresse des Geräts nicht kennen, suchen Sie im **Einstellungen > Netzwerk und Internet > Erweiterte Optionen** , oder bitten Sie Cortana **"Hey Cortana, was Meine IP-Adresse ist?"**
  * Wenn die HoloLens über USB verbunden ist, können Sie stattdessen auswählen **Gerät** über USB bereitstellen.
  * Lassen Sie die **Authentifizierungsmodus** festgelegt **universelle**.
  * Klicken Sie auf **auswählen**

* Klicken Sie auf **Debuggen > Starten ohne debugging** , oder drücken Sie **STRG + F5**. Ist dies beim ersten auf Ihrem Gerät bereitstellen, Sie müssen [verbinden Sie es mit Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).

* Das Origami Projekt jetzt erstellen, bereitstellen, um Ihre HoloLens, und führen Sie dann.
* Legen Sie auf Ihre HoloLens, und suchen Sie auf Ihre neuen Hologramme finden Sie unter.

## <a name="chapter-2---gaze"></a>Kapitel 2: Blicke

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

In diesem Kapitel werden wir zum Einfügen des ersten der drei Methoden zur Interaktion mit Ihrem Hologramme: [bestaunen](gaze.md).

### <a name="objectives"></a>Ziele

* Visualisieren Sie Ihre Blicke mithilfe eines Cursors Welt gesperrt.

### <a name="instructions"></a>Anweisungen

* Wechseln Sie zurück zu Ihrem Unity-Projekt, und schließen Sie das Fenster "erstellen" aus, wenn es noch geöffnet ist.
* Wählen Sie die **Hologramme** Ordner in der **Projektfenster**.
* Ziehen Sie die **Cursor** -Objekt in der **Hierarchie Bereich** auf der Stammebene.
* Doppelklicken Sie auf die **Cursor** Objekt, das ein genauer ansehen.
* Mit der rechten Maustaste auf die **Skripts** Ordner im Projektfenster.
* Klicken Sie auf die **erstellen** Untermenü.
* Wählen Sie  **C# Skript**.
* Nennen Sie das Skript **WorldCursor**. Hinweis: Beim Namen wird Groß- und Kleinschreibung beachtet. Sie müssen sich nicht um die Erweiterung .cs hinzuzufügen.
* Wählen Sie die **Cursor** -Objekt in der **Hierarchie Bereich**.
* Drag & drop die **WorldCursor** Skript in die **Inspektor Bereich**.
* Doppelklicken Sie auf die **WorldCursor** Skript, um es in Visual Studio zu öffnen.
* Kopieren Sie diesen Code in **WorldCursor.cs** und **Alles speichern**.

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

* Erstellen Sie die app neu **Datei > Buildeinstellungen**.
* Zurück zu Visual Studio-Projektmappe zuvor verwendet, um auf Ihre HoloLens bereitstellen.
* Wählen Sie "Alles neu laden" Wenn Sie aufgefordert werden.
* Klicken Sie auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.
* Jetzt sehen Sie in der Szene, und beachten Sie, wie der Cursor die Form der Objekte interagiert.

## <a name="chapter-3---gestures"></a>Kapitel 3 - Gesten

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

In diesem Kapitel werden wir fügen Unterstützung für [Gesten](gestures.md). Wenn der Benutzer eine Dokument Kugel auswählt, erstellen wir die Kugel liegen, indem die Schwerkraft mithilfe von Unity Physik-Engine aktivieren.

### <a name="objectives"></a>Ziele

* Steuern Sie Ihre Hologramme mit dieser Option Bewegung.

### <a name="instructions"></a>Anweisungen

Wir beginnen mit dem Erstellen eines Skripts und kann die Option Bewegung erkennen.

* In der **Skripts** Ordner, erstellen Sie ein Skript, mit dem Namen **GazeGestureManager**.
* Ziehen Sie die **GazeGestureManager** Skript auf die **OrigamiCollection** Objekt in der Hierarchie.
* Öffnen der **GazeGestureManager** Skript im Visual Studio, und fügen Sie den folgenden Code hinzu:

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

* Erstellen Sie ein weiteres Skript im Ordner "Scripts", dieses Mal mit dem Namen **SphereCommands**.
* Erweitern Sie die **OrigamiCollection** Objekt in der Hierarchie angezeigt.
* Ziehen Sie die **SphereCommands** Skript auf die **Sphere1** Objekt in der Hierarchie-Bereich.
* Ziehen Sie die **SphereCommands** Skript auf die **Sphere2** Objekt in der Hierarchie-Bereich.
* Öffnen Sie das Skript zur Bearbeitung in Visual Studio, und Ersetzen Sie den Standardcode durch dies:

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

* Exportieren, erstellen und Bereitstellen der app in Ihrem HoloLens.
* Suchen Sie auf die Kugeln.
* Führen Sie die Option Aktion, und beobachten Sie die Kugel, auf die Oberfläche des folgenden löschen.

## <a name="chapter-4---voice"></a>Kapitel 4 – Sprache

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

In diesem Kapitel werden wir fügen Unterstützung für zwei [Sprachbefehle](voice-input.md): "Zurücksetzen World" um die gelöschten Kugeln an ihrem ursprünglichen Speicherort, und "Drop Kugel" die Kugel fallen vornehmen.

### <a name="objectives"></a>Ziele

* Fügen Sie Sprachbefehle, die immer lauschen, im Hintergrund.
* Erstellen Sie ggf. ein Hologramm, die auf einen Sprachbefehl reagiert.

### <a name="instructions"></a>Anweisungen

* In der **Skripts** Ordner, erstellen Sie ein Skript, mit dem Namen **SpeechManager**.
* Ziehen Sie die **SpeechManager** Skript auf die **OrigamiCollection** Objekt in der Hierarchie
* Öffnen der **SpeechManager** Skripts in Visual Studio.
* Kopieren Sie diesen Code in **SpeechManager.cs** und **Alles speichern**:

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

* Öffnen der **SphereCommands** Skripts in Visual Studio.
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

* Exportieren, erstellen und Bereitstellen der app in Ihrem HoloLens.
* Suchen Sie auf die Kugeln und sagen Sie "**löschen Kugel**".
* Sagen Sie "**zurücksetzen Welt**", die sie wieder in ihre ursprünglichen Positionen verschieben.

## <a name="chapter-5---spatial-sound"></a>Kapitel 5 – räumliche sound

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

In diesem Kapitel wir Musik hinzufügen, um die app, und dann Soundeffekten auf bestimmte Aktionen auszulösen. Wir verwenden [räumliche Sound](spatial-sound.md) Sounds mit einen bestimmten Speicherort im 3D-Raum gewähren.

### <a name="objectives"></a>Ziele

* Hören Sie Hologramme in Ihrer Umgebung.

### <a name="instructions"></a>Anweisungen

* Im Unity-Option in der oberen Menüleiste **Bearbeiten > Projekteinstellungen > Audio**
* Finden Sie im Bereich-Inspektor auf der rechten Seite der **Spatializer-Plug-Ins** festlegen, und wählen **MS HRTF Spatializer**.
* Von der **Hologramme** Ordner im Projektfenster, ziehen Sie die **Umgebung** -Objekt auf den **OrigamiCollection** Objekt in der Hierarchie-Bereich.
* Wählen Sie **OrigamiCollection** und suchen Sie die **Audio Source** -Komponente in den Bereich der Eigenschaftenanalyse. Ändern Sie diese Eigenschaften:
  * Überprüfen Sie die **Spatialize** Eigenschaft.
  * Überprüfen Sie die **auf aktiv wiedergeben**.
  * Änderung **räumliche Blend** zu **3D** durch den Schieberegler ganz nach rechts ziehen. Wenn Sie den Schieberegler verschieben, sollten den Wert von 0 auf 1 ändern.
  * Überprüfen Sie die **Schleife** Eigenschaft.
  * Erweitern Sie **3D Sound Einstellungen**, und geben Sie **0,1** für **Doppler Ebene**.
  * Legen Sie **Volume Rolloff** zu **logarithmische Rolloff**.
  * Legen Sie **maximaler Abstand** zu **20**.
* In der **Skripts** Ordner, erstellen Sie ein Skript, mit dem Namen **SphereSounds**.
* Drag & drop **SphereSounds** auf die **Sphere1** und **Sphere2** Objekte in der Hierarchie.
* Open **SphereSounds** aktualisieren Sie den folgenden Code in Visual Studio und **Alles speichern**.

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

* Speichern Sie das Skript aus, und zurück zu Unity.
* Exportieren, erstellen und Bereitstellen der app in Ihrem HoloLens.
* Verschieben Sie näher und weiter von der Stufe aus, und aktivieren Sie, paralleler, hören den Sound zu ändern.

## <a name="chapter-6---spatial-mapping"></a>Kapitel 6 – räumliche Zuordnung

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

Nun verwenden wir [räumliche Zuordnung](spatial-mapping.md) ein wirkliches Objekt in der realen Welt die Spielfläche zu platzieren.

### <a name="objectives"></a>Ziele

* Bringen Sie Ihre realen, in der virtuellen Welt.
* Platzieren Sie Ihre Hologramme, wo sie sind die meisten für Sie.

### <a name="instructions"></a>Anweisungen

* Klicken Sie in Unity, auf die **Hologramme** Ordner im Projektfenster.
* Ziehen Sie die **räumliche Zuordnung** Asset in das Stammverzeichnis der **Hierarchie**.
* Klicken Sie auf die **räumliche Zuordnung** Objekt in der Hierarchie.
* In der **Inspektor Bereich**, ändern Sie die folgenden Eigenschaften:
  * Überprüfen Sie die **zeichnen Visual Gitter** Feld.
  * Suchen Sie **zeichnen Material** , und klicken Sie auf den Kreis auf der rechten Seite. Typ "**Drahtmodell**" in das Suchfeld oben. Klicken Sie auf das Ergebnis, und klicken Sie dann schließen Sie das Fenster. Wenn Sie dies tun, der Wert für Material zeichnen soll Drahtmodell abrufen oder festlegen.
* Exportieren, erstellen und Bereitstellen der app in Ihrem HoloLens.
* Wenn die app ausgeführt wird, wird ein Drahtmodell-Netz Ihrer realen überlagern.
* Sehen Sie sich, wie eine parallele Kugel die Bühne verließ, und klicken Sie auf dem Boden liegen wird.

Jetzt zeigen wir Ihnen die OrigamiCollection an einem neuen Speicherort zu verschieben:

* In der **Skripts** Ordner, erstellen Sie ein Skript, mit dem Namen **TapToPlaceParent**.
* In der **Hierarchie**, erweitern Sie die **OrigamiCollection** , und wählen Sie die **Phase** Objekt.
* Ziehen Sie die **TapToPlaceParent** -Skript auf die Stage-Objekt.
* Öffnen der **TapToPlaceParent** Skript im Visual Studio, und aktualisieren, um folgende sein:

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
* Jetzt sollten Sie jetzt das Spiel an einem bestimmten Speicherort zu platzieren, indem Sie darauf gazing, verwenden die Option Aktion und klicken Sie dann an einem neuen Speicherort verschieben und die Select-Geste erneut zu verwenden können.

## <a name="chapter-7---holographic-fun"></a>Kapitel 7: Holografischen Spaß

### <a name="objectives"></a>Ziele

* Zeigen Sie auf eine holographic Underworld "entrance".

### <a name="instructions"></a>Anweisungen

Jetzt zeigen wir Ihnen wie die holographic Underworld entdecken:

* Von der **Hologramme** Ordner im Projektfenster:
  * Ziehen Sie **Underworld** in die Hierarchie ein untergeordnetes Element des **OrigamiCollection**.
* In der **Skripts** Ordner, erstellen Sie ein Skript, mit dem Namen **HitTarget**.
* In der **Hierarchie**, erweitern Sie die **OrigamiCollection**.
* Erweitern Sie die **Phase** Objekt aus, und wählen Sie die **Ziel** Objekt (blaue Lüfter).
* Ziehen Sie die **HitTarget** Skript auf die **Ziel** Objekt.
* Öffnen der **HitTarget** Skript im Visual Studio, und aktualisieren, um folgende sein:

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

* Wählen Sie in Unity die **Ziel** Objekt.
* Zwei öffentliche Eigenschaften werden nun angezeigt, auf die **Ziel erreicht** Komponente und Reference-Objekte in unsere Szene müssen:
  * Ziehen Sie **Underworld** aus der **Hierarchie** zur Eigenschaftenansicht der **Underworld** Eigenschaft für die **Ziel erreicht** Komponente.
  * Ziehen Sie **Phase** aus der **Hierarchie** zum Bereich der **Objekt zum Ausblenden von** Eigenschaft für die **Ziel erreicht** Komponente.
* Exportieren, erstellen und Bereitstellen der app.
* Platzieren Sie die Origami-Auflistung, auf dem Boden, und klicken Sie dann verwenden Sie die Option Aktion, um eine Kugel löschen zu machen.
* Wenn die Kugel das Ziel (blaue Lüfter) erreicht, erfolgt eine Explosion. Die Auflistung wird ausgeblendet, und eine Lücke, die Underworld angezeigt.

## <a name="the-end"></a>Das Ende

Und das Ende dieses Tutorials ist!

Sie haben Folgendes gelernt:

* Vorgehensweise: erstellen eine app holographic in Unity.
* Wie Sie mithilfe der Blicke, Gesten, Sprach-, Sound, und die räumliche Zuordnung.
* Informationen zum Erstellen und Bereitstellen einer app mithilfe von Visual Studio.

Sie können nun damit beginnen, Ihre eigenen holografischen Benutzeroberfläche erstellen.

## <a name="see-also"></a>Siehe auch

* [MR Basics 101E: Vollständige Projekt mit dem emulator](holograms-101e.md)
* [Blicke](gaze.md)
* [Gesten](gestures.md)
* [Spracheingabe](voice-input.md)
* [Räumliche sound](spatial-sound.md)
* [Räumliche Zuordnung](spatial-mapping.md)
