---
title: MR 240 - mehrere HoloLens-Geräte freigeben
description: Führen Sie diese exemplarischen Vorgehensweise erfahren, die Details der Freigabe Hologramme auf Unity, Visual Studio und HoloLens mit Codierung.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, sharing, networking, academy, tutorial
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594887"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a>MR 240 freigeben: Mehrere HoloLens-Geräte

Hologramme Anwesenheit in unserer Welt mit gewährt verbleibende vorhanden, wie wir im Raum umher zu schieben. HoloLens behält Hologramme in Position mithilfe verschiedener [Koordinatensysteme](coordinate-systems.md) zum Nachverfolgen der Ort und die Ausrichtung von Objekten. Wenn wir diese Koordinatensysteme zwischen Geräten freigeben, können wir eine gemeinsame Erfahrung erstellen, die zur Teilnahme an einer freigegebenen holographic Welt ermöglicht.

In diesem Tutorial wird Folgendes beschrieben:

* Einrichten eines Netzwerks für einen gemeinsamen Erfahrung.
* Teilen Sie Hologramme für HoloLens-Geräte.
* Entdecken Sie andere Personen in unserem gemeinsamen holographic.
* Erstellen Sie eine freigegebene interaktive Benutzeroberfläche können Sie weitere Entwicklungen - Ziel und Starten der Projektile auf sie!

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td>MR 240 freigeben: Mehrere HoloLens-Geräte</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Bevor Sie beginnen

### <a name="prerequisites"></a>Vorraussetzungen

* Ein Windows 10-PCs mit dem richtigen konfiguriert [-Tools installiert](install-the-tools.md) mit Internetzugriff.
* HoloLens-Geräte über mindestens zwei [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Projektdateien

* Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) vom Projekt erforderlich sind. Ist Unity 2017.2 oder höher erforderlich.
  * Wenn Sie weitere Unity 5.6-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).
  * Wenn Sie weitere Unity 5.5-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).
  * Wenn Sie weitere 5.4 von Unity-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).
* Un-Archive die Dateien auf dem Desktop oder andere einfach auf den Speicherort zugreifen. Behalten Sie den Ordnernamen als **SharedHolograms**.

>[!NOTE]
>Wenn Sie vor dem Herunterladen, den Quellcode ansehen möchten es [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).

## <a name="chapter-1---holo-world"></a>Kapitel 1: Holo World

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

In diesem Kapitel wir unser erstes Unity-Projekt und durchlaufen Sie den Build einrichten und Bereitstellen von Prozess.

### <a name="objectives"></a>Ziele

* Richten Sie Unity um holographic apps zu entwickeln.
* Finden Sie unter Ihrem – Hologramm!

### <a name="instructions"></a>Anweisungen

* Starten Sie Unity.
* Wählen Sie **öffnen**.
* Geben Sie den Speicherort als dem **SharedHolograms** Ordner, die Sie zuvor nicht archiviert.
* Wählen Sie **Projektname** , und klicken Sie auf **Ordner auswählen**.
* In der **Hierarchie**, mit der rechten Maustaste die **Main Camera** , und wählen Sie **löschen**.
* In der **HoloToolkit-Freigabe-240/Prefabs/Kamera** Ordner finden Sie die **Main Camera** prefab.
* Drag & drop die **Main Camera** in die **Hierarchie**.
* In der **Hierarchie**, klicken Sie auf **erstellen** und **leere erstellen**.
* Mit der rechten Maustaste den neuen **"gameobject"** , und wählen Sie **umbenennen**.
* Benennen Sie das "gameobject" zu **HologramCollection**.
* Wählen Sie die **HologramCollection** -Objekt in der **Hierarchie**.
* In der **Inspektor** legen Sie die **transformieren Position** zu: **X: 0, Y: -0.25, Z: 2**.
* In der **Hologramme** Ordner in der **Projektfenster**, finden Sie die **EnergyHub** Asset.
* Drag & drop die **EnergyHub** -Objekt aus der **Projektfenster** auf die **Hierarchie** als eine **untergeordnetes Element des HologramCollection**.
* Wählen Sie **Datei > Szene speichern unter...**
* Benennen Sie die Szene **SharedHolograms** , und klicken Sie auf **speichern**.
* Drücken Sie die **spielen** -Schaltfläche in Unity, um Ihre Hologramme der Vorschau anzuzeigen.
* Drücken Sie **spielen** ein zweites Mal im Vorschaumodus zu beenden.

**Exportieren Sie das Projekt aus Unity in Visual Studio**
* Im Unity-Option **Datei > Buildeinstellungen**.
* Klicken Sie auf **öffnen Szenen hinzufügen** die Szene hinzufügen.
* Wählen Sie **universelle Windows-Plattform** in die **Plattform** aus, und klicken Sie auf **Plattform wechseln**.
* Legen Sie **SDK** zu **universelle 10**.
* Legen Sie **Zielgerät** zu **HoloLens** und **UWP Build Type** zu **D3D**.
* Überprüfen Sie **Unity C# Projekte**.
* Klicken Sie auf **Erstellen**.
* Erstellen Sie in dem Datei-Explorer-Fenster, das angezeigt wird, eine **neuer Ordner** mit dem Namen "App".
* Mausklick die **App** Ordner.
* Drücken Sie **wählen Sie Ordner**.
* Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.
* Öffnen der **App** Ordner.
* Open **SharedHolograms.sln** zum Starten von Visual Studio.
* Verwenden obere auf der Symbolleiste in Visual Studio, ändern Sie das Ziel vom Debugmodus in den **Version** und ARM, **X86**.
* Klicken Sie auf den Dropdownpfeil neben dem lokalen Computer, und wählen **Remotegerät**.
    * Legen Sie die **Adresse** auf den Namen oder die IP-Adresse Ihrer HoloLens. Wenn Sie Ihre IP-Adresse des Geräts nicht kennen, suchen Sie im **Einstellungen > Netzwerk und Internet > Erweiterte Optionen** , oder bitten Sie Cortana **"Hey Cortana, was Meine IP-Adresse ist?"**
    * Lassen Sie die **Authentifizierungsmodus** festgelegt **universelle**.
    * Klicken Sie auf **auswählen**
* Klicken Sie auf **Debuggen > Starten ohne debugging** , oder drücken Sie **STRG + F5**. Ist dies beim ersten auf Ihrem Gerät bereitstellen, Sie müssen [verbinden Sie es mit Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
* Legen Sie auf Ihre HoloLens, und suchen Sie die EnergyHub – Hologramm.

## <a name="chapter-2---interaction"></a>Kapitel 2 – Interaktionen

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

In diesem Kapitel werden wir mit unserem Hologramme interagieren. Zunächst fügen wir einen Cursor zum Visualisieren unsere [bestaunen](gaze.md). Klicken Sie dann wir fügen [Gesten](gestures.md) und verwenden Sie unsere Seite, um unsere Hologramme im Raum platzieren.

### <a name="objectives"></a>Ziele

* Verwenden Sie die Blicke, die Eingabe für einen Cursor zu steuern.
* Verwenden Sie die Eingabe für die Interaktion mit Hologramme Geste.

### <a name="instructions"></a>Anweisungen

**Blicke**
* In der **Hierarchie Bereich** wählen Sie die **HologramCollection** Objekt.
* In der **Inspektor Bereich** klicken Sie auf die **Add Component** Schaltfläche.
* Geben Sie im Menü, in das Suchfeld **bestaunen Manager**. Wählen Sie das Suchergebnis.
* In der **HoloToolkit-Freigabe-240\Prefabs\Input** Ordner finden Sie die **Cursor** Asset.
* Drag & drop die **Cursor** Medienobjekt, auf die **Hierarchie**.

**Aktion**
* In der **Hierarchie Bereich** wählen Sie die **HologramCollection** Objekt.
* Klicken Sie auf **Add Component** und **Gesten-Manager** in das Suchfeld ein. Wählen Sie das Suchergebnis.
* In der **Hierarchie Bereich**, erweitern Sie **HologramCollection**.
* Wählen Sie das untergeordnete Element **EnergyHub** Objekt.
* In der **Inspektor Bereich** klicken Sie auf die **Add Component** Schaltfläche.
* Geben Sie im Menü, in das Suchfeld **– Hologramm Platzierung**. Wählen Sie das Suchergebnis.
* Speichern Sie die Szene durch Auswählen von **Datei > Szene speichern**.

**Bereitstellen und nutzen**
* Erstellen Sie und Bereitstellen Sie, um Ihre HoloLens, mithilfe der Anweisungen aus dem vorhergehenden Kapitel.
* Sobald die app auf Ihrem HoloLens wird gestartet, verschieben Sie Kopf zu, und beachten Sie, wie die EnergyHub Ihre Blicke verfolgt.
* Beachten Sie, wie der Cursor wird angezeigt, wenn Sie bei der Hologramm bestaunen und Änderungen an Punktuelles Licht, wenn nicht am ggf. ein Hologramm gazing.
* Führen Sie eine tippbewegung Hologramm platzieren. Zu diesem Zeitpunkt in unserem Projekt können Sie nur einmal die Hologramm (Wiederholen Sie die Bereitstellung erneut versuchen) platzieren.

## <a name="chapter-3---shared-coordinates"></a>Koordiniert die Kapitel 3 – freigegeben

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

Es Spaß macht, finden Sie unter und Hologramme interagieren, aber noch weiter gehen. Wir richten unsere erste gemeinsamen Erfahrung - ggf. ein Hologramm, die alle zusammen sehen kann.

### <a name="objectives"></a>Ziele

* Einrichten eines Netzwerks für einen gemeinsamen Erfahrung.
* Richten Sie keinen gemeinsamen Zeitpunkt für den Verweis.
* Teilen Sie Koordinatensysteme auf Geräten.
* Alle sehen die gleichen – Hologramm!

>[!NOTE]
>Die **InternetClientServer** und **PrivateNetworkClientServer** Funktionen müssen deklariert werden, für eine app für die Verbindung mit dem Server freigeben. Dies ist für die Sie bereits unter Hologramme 240, aber beachten Sie, dass für Ihre eigenen Projekte.
>1. Rufen Sie im Unity-Editor die playereinstellungen durch Navigieren zu "Bearbeiten > Projekt Einstellungen > Player"
>2. Klicken Sie auf der Registerkarte "Windows Store"
>3. Überprüfen Sie im Abschnitt "Einstellungen > Veröffentlichungsfunktionen" die **InternetClientServer** Funktion und die **PrivateNetworkClientServer** Funktion

### <a name="instructions"></a>Anweisungen

* In der **Projektfenster** navigieren Sie zu der **HoloToolkit-Freigabe-240\Prefabs\Sharing** Ordner.
* Drag & drop die **Freigabe** prefab in die **Hierarchie Bereich**.

Als Nächstes müssen wir den Freigabedienst zu starten. Nur **einen PC** erleben Sie in der gemeinsam verwendeten muss diesen Schritt nicht ausführen.
* Wählen Sie im Menü oben Hand – in Unity – die **HoloToolkit-Freigabe-240-Menü**.
* Wählen Sie die **Freigabedienst starten** Element in der Dropdownliste aus.
* Überprüfen Sie die **privates Netzwerk** aus, und klicken Sie auf **Zugriff zulassen** Wenn die Firewall-Eingabeaufforderung angezeigt wird.
* Notieren Sie sich die IPv4-Adresse, die in die gemeinsame Nutzung der Konsolenfenster angezeigt. Dies ist die gleiche IP-Adresse des Computers, die der Dienst ausgeführt wird.

Befolgen Sie die restlichen Anweisungen auf **alle PCs** , wird die freigegebene Benutzeroberfläche beitreten.
* In der **Hierarchie**, wählen die **Freigabe** Objekt.
* In der **Inspektor**auf die **Freigabe Phase** Komponente ändern der **Serveradresse** von 'Localhost', um die IPv4-Adresse des Computers SharingService.exe ausgeführt.
* In der **Hierarchie** wählen Sie die **HologramCollection** Objekt.
* In der **Inspektor** klicken Sie auf die **Add Component** Schaltfläche.
* Geben Sie in das Suchfeld **Import Export Anker Manager**. Wählen Sie das Suchergebnis.
* In der **Projektfenster** navigieren Sie zu der **Skripts** Ordner.
* Doppelklicken Sie auf die **HologramPlacement** Skript, um es in Visual Studio zu öffnen.
* Ersetzen Sie den Inhalt durch den folgenden Code ein.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;
        
        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* Wählen Sie in Unity, die **HologramCollection** in die **Hierarchie Bereich**.
* In der **Inspektor Bereich** klicken Sie auf die **Add Component** Schaltfläche.
* Geben Sie im Menü, in das Suchfeld **App-Status-Manager**. Wählen Sie das Suchergebnis.

**Bereitstellen und nutzen**
* Erstellen Sie das Projekt für Ihre HoloLens-Geräte.
* Legen Sie eine HoloLens zunächst bereitstellen. Sie müssen warten, bis der Anker an den Dienst hochgeladen werden, bevor Sie die EnergyHub platzieren können (dies dauert ca. 30 bis 60 Sekunden). Bis der Upload abgeschlossen ist, werden Ihre Bewegungen Tap ignoriert.
* Nachdem die EnergyHub platziert wurde, am Speicherort auf den Dienst hochgeladen werden, und anschließend können Sie für alle anderen HoloLens-Geräte bereitstellen.
* Wenn eine neue HoloLens zunächst die Sitzung beitritt, möglicherweise der Speicherort der EnergyHub nicht korrekt auf dem Gerät. Als den Anker und die EnergyHub Speicherorte vom Dienst heruntergeladen wurden, sollte die EnergyHub jedoch auf den neuen, freigegebenen Speicherort wechseln. Wenn dieser Fehler nicht innerhalb von ca. 30 bis 60 tritt Sekunden behandelt wird, auf die ursprünglichen HoloLens, bei denen war, beim Festlegen des Ankers aus, um weitere Hinweise der Umgebung zu sammeln. Wenn Sie der Speicherort noch nicht gesperrt ist, auf dem Gerät erneut bereitstellen.
* Wenn die Geräte sind, und die app ausgeführt wird, Suchen nach den EnergyHub. Können alle stimmen Sie auf der Hologramm Speicherort und die Richtung des Texts sind aufgetreten?

## <a name="chapter-4---discovery"></a>Kapitel 4 – Ermittlung

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

Alle Benutzer sehen nun die gleichen – Hologramm! Jetzt sehen wir uns an alle anderen freigegebenen holographic in unserem verbunden. In diesem Kapitel werden wir die Head-Speicherort und die Rotation der alle anderen HoloLens-Geräte in der gleichen Sitzung für die Freigabe abrufen.

### <a name="objectives"></a>Ziele

* Erkennen Sie einander, in unserem gemeinsamen Erfahrung.
* Wählen Sie aus, und geben Sie einen Player Avatar frei.
* Fügen Sie die Player-Avatar neben den Köpfen.

### <a name="instructions"></a>Anweisungen

* In der **Projektfenster** navigieren Sie zu der **Hologramme** Ordner.
* Drag & drop die **PlayerAvatarStore** in die **Hierarchie**.
* In der **Projektfenster** navigieren Sie zu der **Skripts** Ordner.
* Doppelklicken Sie auf die **AvatarSelector** Skript, um es in Visual Studio zu öffnen.
* Ersetzen Sie den Inhalt durch den folgenden Code ein.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);        
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* In der **Hierarchie** wählen Sie die **HologramCollection** Objekt.
* In der **Inspektor** klicken Sie auf **Add Component**.
* Geben Sie in das Suchfeld **Player-Manager für lokalen**. Wählen Sie das Suchergebnis.
* In der **Hierarchie** wählen Sie die **HologramCollection** Objekt.
* In der **Inspektor** klicken Sie auf **Add Component**.
* Geben Sie in das Suchfeld **Remote-Player-Manager**. Wählen Sie das Suchergebnis.
* Öffnen der **HologramPlacement** Skripts in Visual Studio.
* Ersetzen Sie den Inhalt durch den folgenden Code ein.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* Öffnen der **AppStateManager** Skripts in Visual Studio.
* Ersetzen Sie den Inhalt durch den folgenden Code ein.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

**Bereitstellen und nutzen**
* Erstellen Sie und Bereitstellen Sie des Projekts für Ihre HoloLens-Geräte.
* Wenn Sie einen Pingen Sound hören, gefunden Sie Auswahlmenü Avatar, und wählen Sie einen Avatar mit der tippbewegung Bewegung aus.
* Wenn alle Hologramme nicht angezeigt wird, der Punkt hell rund um den Cursor wird, sobald eine andere Farbe Ihrer HoloLens mit dem Dienst kommuniziert wird: (dunkelpurpur) initialisieren, den Anker (Grün), Importieren/Exportieren von Daten (gelb) herunterladen Hochladen des Ankers (Blau). Ist Point hell rund um den Cursor auf die Standardfarbe (hell Lila), sind Sie bereit für die Interaktion mit anderen Spielern in der Sitzung.
* Sehen Sie sich andere Personen wertsynchronisierung in Ihrem - Verbindung wird ein holographic Roboter über die Schulter unverankerte und ihre Head Bewegungen imitiert.

## <a name="chapter-5---placement"></a>Kapitel 5 - Platzierung

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

In diesem Kapitel werden wir nicht auf Flächen der realen Welt platziert werden Anker zu erhalten. Wir verwenden freigegebene Koordinaten, Anker in der mittlere Punkt zwischen den alle in Verbindung, auf die freigegebene Benutzeroberfläche zu platzieren.

### <a name="objectives"></a>Ziele

* Platzieren Sie Hologramme, auf die räumliche Zuordnung, die anhand der HomeRuns Head-Position.

### <a name="instructions"></a>Anweisungen

* In der **Projektfenster** navigieren Sie zu der **Hologramme** Ordner.
* Drag & drop die **CustomSpatialMapping** prefab auf die **Hierarchie**.
* In der **Projektfenster** navigieren Sie zu der **Skripts** Ordner.
* Doppelklicken Sie auf die **AppStateManager** Skript, um es in Visual Studio zu öffnen.
* Ersetzen Sie den Inhalt durch den folgenden Code ein.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to 
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a 
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* In der **Projektfenster** navigieren Sie zu der **Skripts** Ordner.
* Doppelklicken Sie auf die **HologramPlacement** Skript, um es in Visual Studio zu öffnen.
* Ersetzen Sie den Inhalt durch den folgenden Code ein.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the 
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

**Bereitstellen und nutzen**
* Erstellen Sie und Bereitstellen Sie des Projekts für Ihre HoloLens-Geräte.
* Wenn die app bereit ist, stehen in einem Kreis aus, und beachten Sie, wie die EnergyHub in der Mitte der "Jeder" angezeigt wird.
* Tippen Sie auf diese Option, um die EnergyHub zu platzieren.
* Führen Sie den Befehl mit dem Voice "Target zurücksetzen", wählen Sie die EnergyHub Sichern von und arbeiten zusammen als eine Gruppe, die – Hologramm an einem neuen Speicherort zu verschieben.

## <a name="chapter-6---real-world-physics"></a>Kapitel 6 – Physik der realen Welt

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

In diesem Kapitel wird Hologramme hinzugefügt, die reale Flächen abprallen. Sehen Sie sich der Speicherplatz gänzlich mit Projekten, die von Ihnen und Ihren Freunden gestartet!

### <a name="objectives"></a>Ziele

* Starten Sie die Projektile, die reale Flächen abprallen.
* Geben Sie die Projektile aus, damit sie von anderen Spielern angezeigt werden können.

### <a name="instructions"></a>Anweisungen

* In der **Hierarchie** wählen Sie die **HologramCollection** Objekt.
* In der **Inspektor** klicken Sie auf **Add Component**.
* Geben Sie in das Suchfeld **Projektil Startprogramm**. Wählen Sie das Suchergebnis.

**Bereitstellen und nutzen**
* Erstellen und an Ihre HoloLens-Geräte bereitstellen.
* Wenn die app auf allen Geräten ausgeführt wird, führen Sie eine tippbewegung um Projektil auf Flächen der realen Welt zu starten.
* Erfahren Sie, was geschieht, wenn Ihre Projektil mit einen anderen Player Avatar kollidiert!

## <a name="chapter-7---grand-finale"></a>Kapitel 7 – Grand Erfahrung

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

In diesem Kapitel werden wir ein Portal aufdecken, die nur bei der Zusammenarbeit ermittelt werden können.

### <a name="objectives"></a>Ziele

* Zusammenarbeiten Sie, um genügend Projektile auf der Anker aus, um ein Geheimnis Portal gewinnen starten!

### <a name="instructions"></a>Anweisungen

* In der **Projektfenster** navigieren Sie zu der **Hologramme** Ordner.
* Drag & drop die **Underworld** -Objekt als eine **untergeordnetes Element des HologramCollection**.
* Mit **HologramCollection** ausgewählt ist, klicken Sie auf die **Add Component** Schaltfläche der **Inspektor**.
* Geben Sie im Menü, in das Suchfeld **ExplodeTarget**. Wählen Sie das Suchergebnis.
* Mit **HologramCollection** ausgewählten, von der **Hierarchie** ziehen Sie die **EnergyHub** -Objekt an die **Ziel** -Feld in der **Inspektor**.
* Mit **HologramCollection** ausgewählten, von der **Hierarchie** ziehen Sie die **Underworld** -Objekt an die **Underworld** -Feld in der  **Inspector**.

**Bereitstellen und nutzen**
* Erstellen und an Ihre HoloLens-Geräte bereitstellen.
* Wenn die app gestartet wurde, werden zusammen zum Starten der Projektile auf die EnergyHub zusammenarbeiten.
* Wenn die Underworld angezeigt wird, starten Sie die Projektile auf Underworld Roboter (Treffer einem Roboter ausgegangen dreifache für zusätzliche Spaß).
