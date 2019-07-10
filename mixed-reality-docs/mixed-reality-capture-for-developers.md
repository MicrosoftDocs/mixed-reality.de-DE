---
title: Mixed Reality-Erfassung für Entwickler
description: Bewährte Methoden für mixed Reality für Entwickler erfassen.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: MRC, Foto, Video, Erfassung, Kamera
ms.openlocfilehash: d1675d2d6c74c6d15ca245a66719e00f2a7c2111
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694363"
---
# <a name="mixed-reality-capture-for-developers"></a>Mixed Reality-Erfassung für Entwickler

> [HINWEIS!] Finden Sie unter [rendern, die von der Kamera PV](#render-from-the-pv-camera-opt-in) unten Anleitungen dazu, eine neue MRC-Funktion für HoloLens 2.

Da ein Benutzer in Anspruch nehmen könnte eine [mixed Reality-Erfassung](mixed-reality-capture.md) (MRC) Foto oder video zu einem beliebigen Zeitpunkt einige Dinge, die Sie beim Entwickeln Ihrer Anwendung bedenken sollten vorhanden sind. Dies umfasst bewährte Methoden für die MRC visuelle Qualität und reagieren auf Änderungen am Informationssystem wird, während MRCs erfasst werden.

Entwickler können außerdem nahtlos mixed Reality-Erfassung und dem Einfügen in ihre apps integrieren.

MRC für HoloLens (löschbaren) unterstützt Videos und Fotos von bis zu 720p, während MRC für HoloLens-2 Videos bis zu 1080p und Fotos bis 4-KB-Lösung unterstützt.

## <a name="the-importance-of-quality-mrc"></a>Die Bedeutung der Qualität MRC

Mixed Reality erfasst, Fotos und Videos sind wahrscheinlich die zum ersten Mal ein Benutzer Ihrer App haben. Ob als mixed Reality-Screenshots auf der Seite der Microsoft Store oder von anderen Benutzern, die gemeinsame Nutzung MRCs in sozialen Netzwerken. Können Sie MRC-demo-Ihrer-app, Schulen von Benutzern, fordern Sie Benutzer auf ihre Interaktionen gemischten Welt zu teilen und für Benutzer Forschung und Lösen von Problemen.

## <a name="how-mrc-impacts-your-app"></a>Auswirkungen auf die MRC Ihrer app

### <a name="enabling-mrc-in-your-app"></a>Aktivierung MRC in Ihrer app

Standardmäßig muss eine app nicht nichts tun, um Benutzern mixed Reality Erfassungen zu ermöglichen.

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>Verbesserte Ausrichtung für MRC in Ihrer app aktivieren

Standardmäßig kombiniert mixed Reality-Erfassung des richtigen Auge holographic Ausgabe mit der Kamera Foto/Video (PV). Aus diesen beiden Quellen werden kombiniert mit den Fokuspunkt, die von der aktuell ausgeführten immersive app festgelegt.

Dies bedeutet, dass Hologramme außerhalb der Fokus-Ebene sowie (aufgrund der physischen Abstand zwischen der Kamera BW und der richtigen Anzeige) ausgerichtet sind, wird nicht.

#### <a name="set-the-focus-point"></a>Legen Sie den Fokuspunkt

Sollte immersive apps unter (auf HoloLens) festgelegt. die [Zeitpunkt konzentrieren](focus-point-in-unity.md) , in dem sie ihre Datenebene Stabilisierung sein soll. Dadurch wird sichergestellt, die beste Ausrichtung in sowohl den Kopfhörer und mixed Reality-Capture-Vorgangs.

Wenn ein Fokuspunkt nicht festgelegt ist, wird die Stabilisierung Ebene zwei Verbrauchseinheiten standardmäßig verwendet.

#### <a name="render-from-the-pv-camera-opt-in"></a>Rendern von der Kamera PV (opt-in)

HoloLens 2 fügt die Möglichkeit, eine immersive app **rendern, die von der Kamera PV** während mixed Reality-Erfassung ausgeführt wird. Um sicherzustellen, dass die app die zusätzliche Rendering ordnungsgemäß unterstützt, muss die app auf diese Funktion teilnehmen.

Rendern Sie aus den PV Kamera bietet die folgenden Verbesserungen über die MRC standarderfahrung:
* – Hologramm Ausrichtung sowohl die Hände (für nahezu Interaktionen) Ihrer physischen Umgebung sollten richtig überhaupt, Abstände, anstatt einen Offset an entfernungen als die Fokuspunkt, wie Sie in der standardmäßigen MRC sehen können.
* Das richtige Auge in den Kopfhörer werden nicht beeinträchtigt, wie es zum Rendern der Hologramme für die MRC-Ausgabe verwendet wird.

Es gibt drei Schritte zum Rendern von der Kamera PV zu aktivieren:
1. Aktivieren Sie die PhotoVideoCamera HolographicViewConfiguration
2. Behandeln Sie die zusätzlichen HolographicCamera Rendern
3. Überprüfen Sie Ihre Shader und der Code ordnungsgemäß aus dieser zusätzlichen HolographicCamera Rendern

##### <a name="enable-the-photovideocamera-holographicviewconfiguration"></a>Aktivieren Sie die PhotoVideoCamera HolographicViewConfiguration

Zum teilnehmen, kann eine app einfach die PhotoVideoCamera des [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfiguration.PhotoVideoCamera);
if (view != null)
{
   view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>Die zusätzliche HolographicCamera das Rendering in DirectX verarbeiten

Wenn die app hat sich für die von der Kamera PV Rendern und mixed Reality-Sammlung gestartet wird:
1. Die HolographicSpace CameraAdded Ereignis wird ausgelöst. Dieses Ereignis kann verzögert werden, wenn die app die Kamera zu diesem Zeitpunkt nicht verarbeiten kann.
2. Sobald das Ereignis wurde abgeschlossen (und es keine ausstehenden Verzögerungen gibt) wird die HolographicCamera in den nächsten HolographicFrame AddedCameras Liste angezeigt.

Bei der Erfassung stoppt, mixed Reality (oder wenn die app die Ansichtskonfiguration deaktiviert, während mixed Reality-Erfassung ausgeführt wird): die HolographicCamera in den nächsten HolographicFrame RemovedCameras Liste angezeigt und wird von der HolographicSpaces CameraRemoved Ereignis ausgelöst werden.

Ein [ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) HolographicCamera, um die Konfiguration anzugeben, eine Kamera gehört zu, Eigenschaft hinzugefügt wurde.

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>Behandeln Sie die zusätzlichen HolographicCamera das Rendering in Unity

>[!NOTE]
> Unity-Unterstützung zum Rendern von der Kamera PV befindet sich in Entwicklung und kann nicht verwendet werden, noch. In dieser Dokumentation wird aktualisiert werden, wenn ein Build von Unity mit Unterstützung für das Rendering von der Kamera PV verfügbar ist.

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>Shader überprüfen und Unterstützung für zusätzliche Kameras code

Führen Sie eine mixed Reality-Erfassung und Überprüfung auf ungewöhnliche Ausrichtung, fehlenden Inhalte oder Leistungsprobleme auftreten. Aktualisieren Sie Shader und Code entsprechend.

Treten bestimmte Szenen, die keine zusätzliche Kamera rendern nicht unterstützen, können Sie die PhotoVideoCameras HolographicViewConfiguration währenddessen deaktivieren.

### <a name="disabling-mrc-in-your-app"></a>Deaktivieren MRC in Ihrer app

#### <a name="2d-app"></a>Direct2D-app

Direct2D-apps können festlegen, dass ihre visuellen Inhalt verdeckt, wenn mixed Reality-Erfassung ausgeführt wird:
* Vorhanden, mit der [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present) Flag
* Erstellen der app-SwapChain mit der [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) Flag
* Mit dem Windows 10 möglicherweise 2019 aktualisieren, Festlegen des ApplicationView [IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)

#### <a name="immersive-app"></a>Umfassenden app

Vollbildschirmanwendungen können ihre visuellen Inhalt von mixed Reality-Erfassung durch ausgeschlossen haben:
* Festlegen des HolographicCameraRenderingParameter [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) mixed Reality-Erfassung für deren zugeordneten Rahmen deaktivieren
* Festlegen des HolographicCamera [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) um mixed Reality-Capture für die zugeordnete holographic Kamera zu deaktivieren

#### <a name="password-keyboard"></a>Password-Tastatur

Mit dem Windows 10 2019 Update vom Mai, visuellen Inhalt wird automatisch von mixed Reality-Erfassung ausgeschlossen, wenn eine Kennwort oder eine Pin-Tastatur angezeigt wird.

### <a name="knowing-when-mrc-is-active"></a>Wissen, wenn MRC aktiv ist.

Die [AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture) Klasse kann von einer app verwendet werden, wissen Sie, wenn mixed Reality-Erfassung System (für Audio oder Video) ausgeführt wird.

>[!NOTE]
>Die AppCapture [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API kann Null, wenn mixed Reality-Erfassung nicht zur Verfügung, auf dem Gerät zurück. Es ist auch wichtig, heben Sie die Registrierung der CapturingChanged-Ereignis, wenn Ihre app angehalten wird, andernfalls MRC in einen blockierten Zustand erhalten kann.

### <a name="best-practices-hololens-specific"></a>Bewährte Methoden (HoloLens-spezifisch)

MRC wird erwartet, ohne zusätzliche Arbeit von Entwicklern arbeiten, aber es gibt einige Dinge zu beachten, die am besten mixed Reality Erfassung Ihrer App bereit.

**MRC verwendet die Hologramm alpha-Kanal, um mit blend die [Kamera](locatable-camera.md) Bilder**

Der wichtigste Schritt ist, um sicherzustellen, dass Ihre app auf transparentes Schwarz anstelle von löschen deckend Schwarz gelöscht wird. In Unity Dies erfolgt standardmäßig mit der MixedRealityToolkit, aber wenn Sie im Unity-nicht entwickeln, müssen Sie möglicherweise stellen eine zeilenweise ändern.

Hier sind einige der Elemente, die in MRC angezeigt werden, wenn Ihre app nicht auf transparentes Schwarz gelöscht wird:

**Beispiel-Fehler**: Schwarz Flanken, um den Inhalt (nicht auf transparentes Schwarz deaktivieren)

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

**Beispiel-Fehler**: Die gesamten Hintergrund-Szene von Hologramm wird schwarz angezeigt. Festlegen von einem Hintergrund Alphawert von 1 resultiert in einem schwarzen Hintergrund

![Festlegen von einem Hintergrund Alphawert von 1 resultiert in einem schwarzen Hintergrund](images/clearopaqueblack-300px.png)

**Erwartetes Ergebnis**: Hologramme werden ordnungsgemäß mit der realen Welt (erwartetes Ergebnis, wenn auf transparentes Schwarz löschen) kombinierten angezeigt.

![Erwartetes Ergebnis, wenn auf transparentes Schwarz löschen](images/cleartransparentblack-300px.png)

**Lösung**:
* Ändern Sie alle Inhalte, die als deckend Schwarz angezeigt wird der Alphawert 0 haben.
* Stellen Sie sicher, dass die app auf transparentes Schwarz gelöscht wird.
* Unity-Standardeinstellungen zu löschen, um automatisch mit der MixedRealityToolkit, jedoch ist, wenn sie eine nicht-Unity-app, die Sie, die Farbe mit ID3D11DeiceContext::ClearRenderTargetView() ändern sollten löschen. Sie möchten sicherstellen, dass Sie das Kontrollkästchen auf transparentes Schwarz (0,0,0,0) anstelle von deckend Schwarz (0,0,0,1 ab).

Sie können jetzt die Alphawerte Ihrer Assets optimieren, wenn Sie möchten, in der Regel müssen jedoch nicht. In den meisten Fällen, sieht MRCs gute vorkonfiguriert. MRC wird davon ausgegangen, vorab multipliziertes Alpha. Die Alphawerte wirkt sich nur auf die MRC-Erfassung aus.

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>Was Sie erwartet, wenn MRC für HoloLens aktiviert ist

Folgendes gilt sowohl für HoloLens (löschbaren) als auch für HoloLens-2, sofern nicht anders angegeben:

* Das System wird die Anwendung für das Rendern von 30 Hz drosseln. Dadurch wird einigen Spielraum für MRC ausgeführt werden, damit die Anwendung nicht zu einer Konstanten Budget Reserve muss erstellt und entspricht auch die MRC Videoaufnahme Framerate 30 fps
* – Hologramm Inhalt im rechten Auge des Geräts kann auf "" Sprenkeln "" angezeigt, wenn die Aufzeichnung/streaming MRC: Text werden schwieriger zu lesen und – Hologramm Kanten möglicherweise mehr Splitter (Aktivierung bei 3. Kamera Rendern in **HoloLens 2** vermeidet Dieser Kompromiss)
* MRC Fotos und Videos werden von der Anwendung berücksichtigt [konzentrieren Punkt](focus-point-in-unity.md) , wenn die Anwendung diese Option aktiviert ist, die gewährleisten Hologramme präzise positioniert sind. Videos ist der Fokuspunkt geglättet, damit Hologramme langsam an Stelle abweichen scheint, wenn der Fokus Punkttiefe erheblich geändert. Hologramme, die in anderen Ebenen aus den Fokuspunkt sind scheinbar Offset aus der realen Welt (siehe Beispiel unten, in denen Fokuspunkt ist auf 2 Werte festgelegt, aber – Hologramm 1 Meter Umkreis um positioniert ist).

![Hologramme auf 2 Zähler werden in der ganzen Welt perfekt registriert angezeigt. Hologramme bei einer Entfernung von schließen oder weit unter Umständen etwas ausgeglichen werden.](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>Die Integration von MRC-Funktionen in Ihrer app

Ihre mixed Reality-app kann initiieren, MRC Foto oder eine videoaufzeichnung von der app aus, und die erfassten Inhalte ohne gespeichert wird Ihre app zur Verfügung gestellt wird, die des Geräts "Eigene Aufnahmen". Sie können Erstellen eines benutzerdefiniertes MRC aufzeichnungs oder nutzen Sie integrierte Kamera-Aufnahme-Benutzeroberfläche. 

### <a name="mrc-with-built-in-camera-ui"></a>MRC mit integrierten Kamera-Benutzeroberfläche

Entwickler können mithilfe der *[Camera Capture UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* zum Abrufen eines Benutzer erfassten mixed Reality-Fotos oder Videos mit nur wenigen Codezeilen.

Diese API startet die integrierte MRC-Kamera-Benutzeroberfläche, von dem der Benutzer dauert eines Fotos oder Videos, und gibt die resultierende Erfassung zu Ihrer app.  Wenn Sie Ihre eigenen Kamera-Benutzeroberfläche erstellt werden soll, oder Low-Level benötigen Zugriff auf den Stream erfassen, können Sie einen benutzerdefinierten Mixed Reality erfassen Recorder erstellen.

### <a name="creating-a-custom-mrc-recorder"></a>Erstellen eines benutzerdefinierten MRC aufzeichnungs

Während der Benutzer ein Foto immer auslösen kann oder video mit dem System MRC Dienst erfassen, sollten eine Anwendung fügen Sie des Kamera-Streams wie MRC Hologramme jedoch eine benutzerdefinierte Kamera-app erstellen. Dadurch kann es sich um die Anwendung starten Erfassungen im Auftrag des Benutzers, benutzerdefinierte Aufzeichnung Benutzeroberfläche zu erstellen oder Anpassen von MRC-Einstellungen so, dass einige zu nennen.

**HoloStudio Fügt eine benutzerdefinierte MRC-Kamera, die mithilfe von MRC-Effekten**

![HoloStudio Fügt eine benutzerdefinierte MRC-Kamera, die mithilfe von MRC-Effekten](images/cameraiconholostudio-300px.jpg)

Unity-Anwendungen sollte [Locatable_camera_in_Unity](locatable-camera-in-unity.md) für die Eigenschaft Hologramme zu aktivieren.

Andere Anwendungen können dazu die [Windows Media-Capture-APIs](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) steuern die Kamera und einen Effekt hinzufügen, MRC-Video und Audio Einbeziehung von virtuellen Hologramme und Anwendung Audio in noch und Videos.

Anwendungen haben zwei Optionen, um den Effekt hinzufügen:
* Die ältere API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* Das neue Microsoft empfohlene API (gibt ein Objekt, wodurch sie dynamische Eigenschaften bearbeiten): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) das erforderlich ist, erstellen Sie die app eine eigene Implementierung von [IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) und [IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition). Informieren Sie sich die MRC-Wirkung-Beispiel für Beispiel für die Verwendung.

>[!NOTE]
> Der Windows.Media.MixedRealityCapture-Namespace wird von Visual Studio nicht erkannt werden, aber die Zeichenfolgen immer noch gültig sind.

MRC Video Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)

|  Eigenschaftenname  |  Typ  |  Standardwert  |  Beschreibung | 
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))  |  1 (VideoRecord)  |  Beschreiben Sie die Capture-Stream für diesen Effekt verwendet wird. Audio ist nicht verfügbar. | 
|  HologramCompositionEnabled  |  boolean  |  TRUE  |  Flag zum Aktivieren oder Deaktivieren von Hologramme in videoaufzeichnung. | 
|  RecordingIndicatorEnabled  |  boolean  |  TRUE  |  Flag zum Aktivieren oder deaktivieren während der Erfassung – Hologramm Aufzeichnung Indikator auf dem Bildschirm. | 
|  VideoStabilizationEnabled  |  boolean  |  FALSE  |  Flag zum Aktivieren oder Deaktivieren von videostabilisierung mit Strom versorgt, durch die HoloLens-nachverfolgung. | 
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  Legen Sie, wie viele historische Frames für videostabilisierung verwendet werden. 0 ist, 0-Latenz und vom Standpunkt der Leistungsfähigkeit fast "frei". 15 empfiehlt sich für die höchste Qualität (auf Kosten der 15 Frames der Latenz und des Speichers). | 
|  GlobalOpacityCoefficient  |  float  |  0.9 (HoloLens) 1.0 (Immersive Kopfhörer)  |  Globale Deckkraft Koeffizienten des – Hologramm im Bereich von 0,0 (vollständig transparent) auf 1,0 festgelegt (vollständig deckend). | 
|  BlankOnProtectedContent  |  boolean  |  FALSE  |  Flag zum Aktivieren oder deaktivieren Sie einen leeren Frame zurückgeben, wenn ein 2d UWP-app mit geschützten Inhalt vorhanden ist. Wenn dieses Flag auf "false" und einer 2D-Texturmap. UWP-app ist ist mit geschützten Inhalt, 2D-UWP-app von einer geschützten Inhalt Textur in sowohl den Kopfhörer und die Erfassung von mixed Reality ersetzt wird. |
|  ShowHiddenMesh  |  boolean  |  FALSE  |  Flag zum Anzeigen der holographic Kamera ausgeblendeten Bereich Mesh und benachbarten Inhalt aktivieren oder deaktivieren. |
| OutputSize | Größe | 0, 0 | Legen Sie die gewünschte Ausgabe-Größe, nach dem Zuschneiden für videostabilisierung. Wenn 0 oder eine ungültige Ausgabegröße angegeben wird, wird eine Standardgröße von Zuschneiden ausgewählt. |
| PreferredHologramPerspective | UINT32 | 1 (PhotoVideoCamera) | Die Enumeration wird verwendet, um anzugeben, welche holographic Kamera Ansichtskonfiguration erfasst werden sollen. Festlegen von 0 bedeutet, dass (anzeigen), die die app wird nicht aufgefordert, die zwischen der Kamera und Fotos/Video-Rendern |

MRC Audio Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)

<table>
<tr>
<th>Eigenschaftenname</th>
<th>Typ</th>
<th>Standardwert</th>
<th>Beschreibung</th>
</tr>
<tr>
<td>MixerMode</td>
<td>UINT32</td>
<td>2</td>
<td>
<ul>
<li>0 : Nur die MIC-audio</li>
<li>1 : Nur systemaudio</li>
<li>2 : MIC und die systemaudio</li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a>Gleichzeitige MRC-Einschränkungen

Es gibt bestimmte Einschränkungen für mehrere apps, die Zugriff auf MRC zur gleichen Zeit.

#### <a name="photovideo-camera-access"></a>Foto/Video-Kamerazugriff

Die Foto/Videokamera ist beschränkt auf die Anzahl der Prozesse, die sie gleichzeitig zugreifen können. Während ein Prozesses aufzeichnet fehl Video- oder die Fotoaufnahme durch die andere Prozesse, die Fotos/Videokamera abzurufen. (Dies gilt für sowohl Mixed Reality erfassen und in der standard Foto/Video-Erfassung)

Eine app kann mit HoloLens-2, die "mediacaptureinitializationsettings" verwenden [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode) Eigenschaft, um anzugeben, dass sie SharedReadOnly ausgeführt werden, wenn sie nicht, exklusive Kontrolle über das Foto/Videokamera benötigen möchten. Dies bedeutet, die Auflösung und die Framerate der Erfassung ist beschränkt, was andere apps die Kamera zu konfiguriert haben.

##### <a name="built-in-mrc-photovideo-camera-access"></a>Integrierte MRC Foto/Video-Kamerazugriff

MRC-Funktionalität in Windows 10 (über Cortana, Menü "Start", Hardware-Verknüpfungen, Miracast, Windows Device Portal) erstellt:
* Wird standardmäßig mit ExclusiveControl ausgeführt

Allerdings verfügt über Unterstützung für jedes Subsystem für die Ausführung im freigegebenen Modus wurden hinzugefügt:
* Wenn eine app ExclusiveControl-Zugriff auf die Kamera Foto/Video anfordert, beendet integrierte MRC automatisch die Foto/Video-Kamera verwenden, damit die app Anforderung erfolgreich ist
* Wenn integrierte MRC gestartet wird, während eine app ExclusiveControl hat, wird integrierten MRC im SharedReadOnly-Modus ausgeführt.

Diese Funktion im freigegebenen Modus verfügt über bestimmte Einschränkungen:
* Foto über Cortana, Verknüpfungen von Hardware oder Menü "Start": Erfordert die Windows 10 April 2018 aktualisieren (oder höher)
* Video über Cortana, Verknüpfungen von Hardware oder Menü "Start": Erfordert die Windows 10 April 2018 aktualisieren (oder höher)
* Streaming MRC über Miracast: Erfordert die Windows 10 Oktober 2018 aktualisieren (oder höher)
* Streaming MRC, über die Windows Device Portal oder über die HoloLens Companion-app: Erfordert die HoloLens 2

>[!NOTE]
> Die Auflösung und Framerate von den integrierten MRC-Kamera-Benutzeroberfläche können über die normalen Werte beeinträchtigt werden, wenn die Kamera Foto/Video von einer anderen app verwendet wird.

#### <a name="mrc-access"></a>MRC-Zugriff

Mit dem Windows 10 April 2018 Update steht nicht mehr eine Einschränkung für mehrere apps, die Zugriff auf die MRC-Stream (allerdings der Zugriff auf die Kamera Foto/Video weiterhin gelten Einschränkungen).

Auf dem Windows 10 April 2018 zuvor Update einer app benutzerdefinierte MRC Recorder gegenseitig System MRC (Aufnahme von Fotos, Videos zu erfassen oder über die Windows Device Portal-streaming).

## <a name="see-also"></a>Siehe auch
* [Mixed Reality-Aufnahme](mixed-reality-capture.md)
* [Spectator View](spectator-view.md)
