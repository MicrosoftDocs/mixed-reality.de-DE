---
title: Mr-Freigabe 240-mehrere hololens-Geräte
description: Befolgen Sie diese exemplarische Vorgehensweise, indem Sie Unity, Visual Studio und hololens verwenden, um die Details der Freigabe von holograms zu erlernen.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Sharing, Networking, Academy, Tutorial
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522333"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a>Mr-Freigabe 240: Mehrere hololens-Geräte

Holograms sind in unserer Welt vorhanden, da Sie sich im Raum bewegen. Hololens hält Hologramme an, indem verschiedene [Koordinatensysteme](coordinate-systems.md) verwendet werden, um den Speicherort und die Ausrichtung von Objekten nachzuverfolgen. Wenn wir diese Koordinatensysteme zwischen Geräten teilen, können wir eine gemeinsame Umgebung erstellen, die es uns ermöglicht, an einer freigegebenen Holographic World teilzunehmen.

In diesem Tutorial werden folgende Aktionen durchführt:

* Einrichten eines Netzwerks für eine gemeinsame Nutzung.
* Freigeben von holograms für hololens-Geräte.
* Entdecken Sie andere Personen in unserer freigegebenen Holographic World.
* Erstellen Sie eine gemeinsame interaktive Darstellung, bei der Sie auf andere Spieler abzielen, und starten Sie Projektile auf Ihnen!

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>Mr-Freigabe 240: Mehrere hololens-Geräte</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Bevor Sie beginnen

### <a name="prerequisites"></a>Vorraussetzungen

* Ein Windows 10-PC, der mit den richtigen Tools konfiguriert ist, die mit Internet Zugriff [installiert](install-the-tools.md) sind
* Mindestens zwei hololens-Geräte, die [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode)sind.

### <a name="project-files"></a>Projektdateien

* Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) , die für das Projekt erforderlich sind. Erfordert Unity 2017,2 oder höher.
  * Wenn Sie weiterhin Unity 5,6-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).
  * Wenn Sie weiterhin Unity 5,5-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).
  * Wenn Sie weiterhin Unity 5,4-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).
* Deinstallieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht zugänglichen Speicherort. Behalten Sie den Ordnernamen **sharedholograms**bei.

>[!NOTE]
>Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).

## <a name="chapter-1---holo-world"></a>Kapitel 1-Holo World

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

In diesem Kapitel richten wir das erste Unity-Projekt ein und durchlaufen den Build-und Bereitstellungs Prozess.

### <a name="objectives"></a>Ziele

* Einrichten von Unity zum Entwickeln von Holographic apps.
* Sehen Sie sich Ihr Hologram!

### <a name="instructions"></a>Anweisungen

* Starten Sie Unity.
* Wählen Sie **Öffnen**aus.
* Geben Sie den Speicherort als Ordner **sharedholograms** ein, den Sie zuvor nicht archiviert haben.
* Wählen Sie **Projekt Name** , und klicken Sie auf **Ordner auswählen**.
* Klicken Sie in der **Hierarchie**mit der rechten Maustaste auf die **Hauptkamera** , und wählen Sie **Löschen**.
* Suchen Sie im Ordner **holotoolkit-Sharing-240/Prefabs/Camera** nach der **Hauptkamera** -vorfab.
* Verschieben Sie die **Hauptkamera** per Drag & Drop in die **Hierarchie**.
* Klicken Sie in der **Hierarchie**auf **Erstellen** , und erstellen Sie eine **leere**.
* Klicken Sie mit der rechten Maustaste auf das neue **gameobject** und wählen Sie **Umbenennen**
* Benennen Sie das gameobject in **hologramcollection**um.
* Wählen Sie das **hologramcollection** -Objekt in der **Hierarchie**aus.
* Legen Sie im **Inspektor** die **Transformations Position** auf Folgendes fest: **STUBEN 0, Y:-0,25, Z: 2**.
* Suchen Sie im Ordner **holograms** des **Projekt Panels**nach dem **energyhub** -Medienobjekt.
* Ziehen Sie das **energyhub** -Objekt per Drag & Drop aus dem **Projekt Panel** in die **Hierarchie** als untergeordnetes Element **von hologramcollection**.
* Wählen Sie **Datei > Szene speichern unter...**
* Benennen Sie die Szene **sharedholograms** , und klicken Sie auf **Speichern**.
* Klicken Sie in Unity auf die **Wiedergabe** Schaltfläche, um eine Vorschau der holograms anzuzeigen
* Drücken **Sie** ein zweites Mal, um den Vorschaumodus zu verhindern.

**Exportieren des Projekts aus Unity in Visual Studio**
* Wählen Sie in Unity **Datei >** Buildeinstellungen aus.
* Klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.
* Wählen Sie in der Liste **Plattform** **universelle Windows-Plattform** aus, und klicken Sie auf **Plattform wechseln**.
* Legen Sie **SDK** auf **Universal 10**fest.
* Legen Sie **Zielgerät** auf **hololens** und **UWP** -Buildtyp auf **D3D**fest.
* Überprüfen Sie **Unity C# -Projekte**.
* Klicken Sie auf **Erstellen**.
* Erstellen Sie im Datei-Explorer-Fenster, das angezeigt wird, einen **neuen Ordner** mit dem Namen "App".
* Klicken Sie einfach auf den **App** -Ordner.
* Drücken **Sie Ordner auswählen**.
* Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.
* Öffnen Sie den **App** -Ordner.
* Öffnen Sie **sharedholograms. sln** , um Visual Studio zu starten.
* Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x86**.
* Klicken Sie auf den Dropdown Pfeil neben lokaler Computer, und wählen Sie **Remote Gerät**aus.
    * Legen Sie die **Adresse** auf den Namen oder die IP-Adresse der hololens fest. Wenn Sie die IP-Adresse Ihres Geräts nicht kennen, suchen Sie in den **Einstellungen > Netzwerk & Internet > Erweiterte Optionen** , oder Fragen Sie Cortana **"Hey Cortana, was ist meine IP-Adresse?"** .
    * Lassen Sie den **Authentifizierungsmodus** auf **Universal**festgelegt.
    * Klicken Sie auf **auswählen**
* Klicken Sie auf **Debuggen > Starten ohne Debugging** , oder drücken Sie **STRG + F5**. Wenn Sie die Bereitstellung auf Ihrem Gerät zum ersten Mal durchführt, müssen Sie [es mit Visual Studio](using-visual-studio.md#pairing-your-device-hololens)koppeln.
* Platzieren Sie die hololens, und suchen Sie das energyhub Hologram.

## <a name="chapter-2---interaction"></a>Kapitel 2: Interaktion

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

In diesem Kapitel interagieren wir mit unseren holograms. Zuerst fügen wir einen Cursor zum Visualisieren unseres [Blicks](gaze.md)hinzu. Dann fügen wir [Gesten](gestures.md) hinzu und verwenden unsere Hand, um die Hologramme in den Raum zu versetzen.

### <a name="objectives"></a>Ziele

* Verwenden Sie die Blick Eingabe, um einen Cursor zu steuern.
* Verwenden Sie Gesten Eingaben für die Interaktion mit holograms.

### <a name="instructions"></a>Anweisungen

**Anvisieren**
* Wählen Sie im Bereich **Hierarchie** das **hologramcollection** -Objekt aus.
* Klicken Sie im **Inspektor-Panel** auf die Schaltfläche **Komponente hinzufügen** .
* Geben Sie im Menü im Suchfeld den Suchbegriff **ein.** Wählen Sie das Suchergebnis aus.
* Suchen Sie im Ordner **HoloToolkit-Sharing-240\Prefabs\Input** nach dem **Cursor** Medienobjekt.
* Ziehen Sie das **Cursor** Medienobjekt per Drag & Drop auf die **Hierarchie**.

**Gestaltungs**
* Wählen Sie im Bereich **Hierarchie** das **hologramcollection** -Objekt aus.
* Klicken Sie auf **Komponente hinzufügen** , und geben Sie **Gesten-Manager** in das Suchfeld ein. Wählen Sie das Suchergebnis aus.
* Erweitern Sie im Bereich **Hierarchie**den Knoten **hologrammcollection**.
* Wählen Sie das untergeordnete **energyhub** -Objekt aus.
* Klicken Sie im **Inspektor-Panel** auf die Schaltfläche **Komponente hinzufügen** .
* Geben Sie im Menü das Suchfeld **Hologram Placement**ein. Wählen Sie das Suchergebnis aus.
* Speichern Sie die Szene, indem Sie **Datei > Szene speichern**auswählen.

**Bereitstellen und nutzen**
* Verwenden Sie die Anweisungen aus dem vorherigen Kapitel, um Ihre hololens zu erstellen und bereitzustellen.
* Nachdem die APP auf Ihren hololens gestartet wurde, bewegen Sie Ihren Kopf und sehen, wie der energyhub ihren Blick folgt.
* Beachten Sie, dass der Cursor angezeigt wird, wenn Sie das Hologramm betrachten, und sich an einem Punktlicht ändert, wenn Sie nicht in ein Hologramm eingeblendet werden.
* Führen Sie einen lufttipp aus, um das Hologram zu platzieren. Zu diesem Zeitpunkt können Sie das – Hologramm nur einmal platzieren (erneut bereitstellen, um es erneut zu versuchen).

## <a name="chapter-3---shared-coordinates"></a>Kapitel 3: freigegebene Koordinaten

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

Es ist Spaß, Hologramme zu sehen und mit Ihnen zu interagieren, aber wir gehen weiter. Wir legen unsere erste gemeinsame Benutzeransicht fest.

### <a name="objectives"></a>Ziele

* Einrichten eines Netzwerks für eine gemeinsame Nutzung.
* Richten Sie einen allgemeinen Verweis Punkt ein.
* Teilen Sie Koordinatensysteme auf allen Geräten.
* Jeder sieht dasselbe Hologram!

>[!NOTE]
>Die Funktionen **internetclientserver** und **privatenetworkclientserver** müssen für eine APP deklariert werden, um eine Verbindung mit dem Freigabe Server herzustellen. Dies erfolgt für Sie bereits in holograms 240, aber beachten Sie dies für Ihre eigenen Projekte.
>1. Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zu "> Projekteinstellungen bearbeiten > Player" navigieren.
>2. Klicken Sie auf die Registerkarte "Windows Store".
>3. Überprüfen Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die Funktion " **internetclientserver** " und die Funktion " **privatenetworkclientserver** ".

### <a name="instructions"></a>Anweisungen

* Navigieren Sie im **Projekt Panel** zum Ordner **HoloToolkit-Sharing-240\Prefabs\Sharing** .
* Ziehen Sie die **Freigabe** vorfab per Drag & amp; Drop in den Bereich **Hierarchie**.

Als nächstes müssen wir den Freigabe Dienst starten. Dieser Schritt muss nur von **einem PC** in der gemeinsamen Nutzung durchlaufen werden.
* Wählen Sie in Unity im oberen Menü das **Menü holotoolkit-Sharing-240**aus.
* Wählen Sie in der Dropdown-Dropdown-Option das Element **Launch Sharing Service** aus.
* Aktivieren Sie die Option **privates Netzwerk** , und klicken Sie auf **Zugriff zulassen** , wenn die Firewall angezeigt wird.
* Notieren Sie sich die im Fenster Freigabe Dienst-Konsolenfenster angezeigte IPv4-Adresse. Dies ist dieselbe IP-Adresse wie der Computer, auf dem der Dienst ausgeführt wird.

Befolgen Sie die restlichen Anweisungen auf **allen PCs** , die der freigegebenen Funktion beitreten werden.
* Wählen Sie in der **Hierarchie**das **Freigabe** Objekt aus.
* Ändern Sie im **Inspektor**auf der Komponente der **Freigabe Stufe** die **Server Adresse** von "localhost" in die IPv4-Adresse des Computers, auf dem "sharingservice. exe" ausgeführt wird.
* Wählen Sie in der **Hierarchie** das **hologramcollection** -Objekt aus.
* Klicken Sie im **Inspektor** auf die Schaltfläche **Komponente hinzufügen** .
* Geben Sie im Suchfeld den **Text Import**-/Export-Manager ein. Wählen Sie das Suchergebnis aus.
* Navigieren Sie im **Projekt Panel** zum Ordner **Scripts** .
* Doppelklicken Sie auf das **hologramplacement** -Skript, um es in Visual Studio zu öffnen.
* Ersetzen Sie den Inhalt durch den folgenden Code.

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

* Wählen Sie in Unity im Bereich **Hierarchie**die Option **hologramcollection** aus.
* Klicken Sie im **Inspektor-Panel** auf die Schaltfläche **Komponente hinzufügen** .
* Geben Sie im Menü den Suchbegriff **App State Manager**ein. Wählen Sie das Suchergebnis aus.

**Bereitstellen und nutzen**
* Erstellen Sie das Projekt für Ihre hololens-Geräte.
* Legen Sie einen hololens für die erste Bereitstellung fest. Sie müssen warten, bis der Anker in den Dienst hochgeladen wird, bevor Sie den energyhub platzieren können (Dies kann ungefähr 30-60 Sekunden dauern). Bis der Upload abgeschlossen ist, werden Ihre Tap-Gesten ignoriert.
* Nachdem der energyhub platziert wurde, wird der Speicherort in den Dienst hochgeladen, und Sie können dann auf allen anderen hololens-Geräten bereitstellen.
* Wenn ein neuer hololens zum ersten Mal an der Sitzung teilnimmt, ist der Speicherort des energyhubs auf diesem Gerät möglicherweise nicht korrekt. Sobald jedoch die Anker-und energyhub-Standorte vom Dienst heruntergeladen wurden, sollte der energyhub zum neuen freigegebenen Speicherort springen. Wenn dies nicht innerhalb von ~ 30-60 Sekunden erfolgt, gehen Sie zu dem Zeitpunkt, an dem sich die ursprünglichen hololens beim Festlegen des Ankers befunden haben, um weitere Umgebungs Hinweise zu sammeln. Wenn der Speicherort noch nicht gesperrt ist, stellen Sie die erneute Bereitstellung auf dem Gerät bereit.
* Wenn die Geräte bereit sind und die app ausführen, suchen Sie nach dem energyhub. Können Sie alle den Speicherort des holograms und die Richtung des Texts akzeptieren?

## <a name="chapter-4---discovery"></a>Kapitel 4: Ermittlung

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

Alle Benutzer können jetzt dasselbe Hologram sehen! Sehen wir uns nun an, dass alle anderen Personen mit unserer freigegebenen Holographic World verbunden sind. In diesem Kapitel werden die Head-und Rotation aller anderen hololens-Geräte in derselben Freigabe Sitzung erläutert.

### <a name="objectives"></a>Ziele

* Entdecken Sie einander in unserer gemeinsamen Darstellung.
* Wählen Sie einen Player Avatar aus, und geben Sie ihn frei
* Fügen Sie den Player Avatar neben den Köpfen der Menschen an.

### <a name="instructions"></a>Anweisungen

* Navigieren Sie im **Projekt Panel** zum Ordner **holograms** .
* Verschieben Sie den **playeravatarstore** per Drag & amp; Drop in die **Hierarchie**.
* Navigieren Sie im **Projekt Panel** zum Ordner **Scripts** .
* Doppelklicken Sie auf das Skript " **avatarselector** ", um es in Visual Studio zu öffnen.
* Ersetzen Sie den Inhalt durch den folgenden Code.

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

* Wählen Sie in der **Hierarchie** das **hologramcollection** -Objekt aus.
* Klicken Sie im **Inspektor** auf **Komponente hinzufügen**.
* Geben Sie im Suchfeld als Suchbegriff **local Player Manager**ein. Wählen Sie das Suchergebnis aus.
* Wählen Sie in der **Hierarchie** das **hologramcollection** -Objekt aus.
* Klicken Sie im **Inspektor** auf **Komponente hinzufügen**.
* Geben Sie im Suchfeld als Suchbegriff **Remote Player-Manager**ein. Wählen Sie das Suchergebnis aus.
* Öffnen Sie das **hologramplacement** -Skript in Visual Studio.
* Ersetzen Sie den Inhalt durch den folgenden Code.

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

* Öffnen Sie das **appstatus Manager** -Skript in Visual Studio.
* Ersetzen Sie den Inhalt durch den folgenden Code.

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
* Erstellen Sie das Projekt, und stellen Sie es auf Ihren hololens-Geräten bereit.
* Wenn Sie einen pinganton hören, suchen Sie das Avatar-Auswahlmenü, und wählen Sie einen Avatar mit der Luft tippen Bewegung aus.
* Wenn Sie keine holograms betrachten, wird durch die Punktbeleuchtung um den Cursor eine andere Farbe aktiviert, wenn Ihre hololens mit dem Dienst kommuniziert: initialisieren (dunkellila), Herunterladen des Ankers (grün), Importieren/Exportieren von Standortdaten (gelb), der Anker wird hochgeladen (blau). Wenn Ihr Cursor die Standardfarbe (hell lila) ist, können Sie mit anderen Spielern in Ihrer Sitzung interagieren!
* Sehen Sie sich andere Personen an, die mit Ihrem Platz verbunden sind. es gibt einen Holographic-Roboter, der über der Schulter schwebt und seine Kopfbewegungen imitiert.

## <a name="chapter-5---placement"></a>Kapitel 5: Platzierung

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

In diesem Kapitel wird der Anker auf realen Oberflächen platziert. Wir verwenden freigegebene Koordinaten zum Platzieren dieses Ankers zwischen allen Personen, die mit der gemeinsamen Benutzer Verbindung verbunden sind.

### <a name="objectives"></a>Ziele

* Platzieren Sie holograms auf der räumlichen Karte basierend auf der Hauptposition des Players.

### <a name="instructions"></a>Anweisungen

* Navigieren Sie im **Projekt Panel** zum Ordner **holograms** .
* Ziehen Sie die **customspatialmapping** -vorfab per Drag & Drop auf die **Hierarchie**.
* Navigieren Sie im **Projekt Panel** zum Ordner **Scripts** .
* Doppelklicken Sie auf das Skript **appstatus Manager** , um es in Visual Studio zu öffnen.
* Ersetzen Sie den Inhalt durch den folgenden Code.

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

* Navigieren Sie im **Projekt Panel** zum Ordner **Scripts** .
* Doppelklicken Sie auf das **hologramplacement** -Skript, um es in Visual Studio zu öffnen.
* Ersetzen Sie den Inhalt durch den folgenden Code.

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
* Erstellen Sie das Projekt, und stellen Sie es auf Ihren hololens-Geräten bereit.
* Wenn die APP bereit ist, stehen Sie in einem Kreis und sehen, wie der energyhub in der Mitte von allen Benutzern angezeigt wird.
* Tippen Sie, um den energyhub zu platzieren.
* Verwenden Sie den Sprachbefehl "Ziel zurücksetzen", um die energyhub-Sicherungskopie auszuwählen und als Gruppe zusammenzuarbeiten, um das Hologramm an einen neuen Speicherort zu verschieben.

## <a name="chapter-6---real-world-physics"></a>Kapitel 6: Reale Physik

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

In diesem Kapitel fügen wir holograms hinzu, die aus realen Oberflächen springen. Sehen Sie sich ihren Platz mit Projekten an, die von Ihnen und Ihren Freunden gestartet wurden!

### <a name="objectives"></a>Ziele

* Starten Sie Projekt Kacheln, die aus realen Oberflächen springen.
* Geben Sie die Projekt Kacheln frei, damit Sie von anderen Playern angezeigt werden.

### <a name="instructions"></a>Anweisungen

* Wählen Sie in der **Hierarchie** das **hologramcollection** -Objekt aus.
* Klicken Sie im **Inspektor** auf **Komponente hinzufügen**.
* Geben Sie im Suchfeld als Suchbegriff **projectile Launcher**ein. Wählen Sie das Suchergebnis aus.

**Bereitstellen und nutzen**
* Erstellen und bereitstellen auf Ihren hololens-Geräten.
* Wenn die APP auf allen Geräten ausgeführt wird, können Sie auf der realen Oberfläche auf der realen Oberfläche eine Luft tippen, um projectile zu starten.
* Sehen Sie sich an, was geschieht, wenn Ihre Projekt Kachel mit dem Avatar eines anderen Players kollidiert!

## <a name="chapter-7---grand-finale"></a>Kapitel 7: groß-Finale

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

In diesem Kapitel wird ein Portal erläutert, das nur mit der Zusammenarbeit ermittelt werden kann.

### <a name="objectives"></a>Ziele

* Arbeiten Sie zusammen, um auf dem Anker ausreichend Projekt Kacheln zu starten, um ein geheimes Portal zu entdecken.

### <a name="instructions"></a>Anweisungen

* Navigieren Sie im **Projekt Panel** zum Ordner **holograms** .
* Verschieben Sie das Objekt " **Underworld** " per Drag & Drop als untergeordnetes Element **von hologramcollection**.
* Klicken Sie bei ausgewähltem **hologrammcollection** im **Inspektor**auf die Schaltfläche **Komponente hinzufügen** .
* Geben Sie im Menü im Suchfeld den Suchbegriff **explodetarget**ein. Wählen Sie das Suchergebnis aus.
* Wenn **hologrammcollection** ausgewählt ist, ziehen Sie das **energyhub** -Objekt aus der **Hierarchie** in das **Zielfeld** des **Inspektors**.
* Wenn **hologrammcollection** ausgewählt ist, ziehen Sie das Objekt " **Underworld** " aus der **Hierarchie** in das Feld " **Unterwelt** " des **Inspektors**.

**Bereitstellen und nutzen**
* Erstellen und bereitstellen auf Ihren hololens-Geräten.
* Wenn die APP gestartet wurde, können Sie zusammenarbeiten, um Projektile auf dem energyhub zu starten.
* Wenn die Unterwelt angezeigt wird, starten Sie Projektile bei Unterwelt-Robotern (führen Sie dreimal einen Roboter aus).
