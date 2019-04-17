---
title: Mixed Reality-Erfassung für Entwickler
description: Bewährte Methoden für mixed Reality für Entwickler erfassen.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: MRC, Foto, Video, Erfassung, Kamera
ms.openlocfilehash: c2d98baf16b2ea724247224aabadc1e2ca533ec1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594008"
---
# <a name="mixed-reality-capture-for-developers"></a>Mixed Reality-Erfassung für Entwickler

> [!NOTE]
> Weitere Anleitungen, die speziell für HoloLens 2 [bald](index.md#news-and-notes). 

Finden Sie unter [aktivieren MRC in Ihrer app](#enabling-mrc-in-your-app) unten Anleitungen dazu, eine neue MRC-Funktion für HoloLens 2.

Da ein Benutzer in Anspruch nehmen könnte eine [mixed Reality-Erfassung](mixed-reality-capture.md) (MRC) Foto oder video zu einem beliebigen Zeitpunkt einige Dinge, die Sie beim Entwickeln Ihrer Anwendung bedenken sollten vorhanden sind. Dies umfasst bewährte Methoden für die MRC visuelle Qualität und reagieren auf Änderungen am Informationssystem wird, während MRCs erfasst werden.

Entwickler können außerdem nahtlos mixed Reality-Erfassung und dem Einfügen in ihre apps integrieren.

MRC für HoloLens (löschbaren) unterstützt Videos und Fotos von bis zu 720p, während MRC für HoloLens-2 Videos bis zu 1080p und Fotos bis 4-KB-Lösung unterstützt.

## <a name="the-importance-of-quality-mrc"></a>Die Bedeutung der Qualität MRC

Mixed Reality erfasst, Fotos und Videos sind wahrscheinlich die zum ersten Mal ein Benutzer Ihrer App haben. Ob als mixed Reality-Screenshots auf der Seite der Microsoft Store oder von anderen Benutzern, die gemeinsame Nutzung MRCs in sozialen Netzwerken. Können Sie MRC-demo-Ihrer-app, Schulen von Benutzern, fordern Sie Benutzer auf ihre Interaktionen gemischten Welt zu teilen und für Benutzer Forschung und Lösen von Problemen.

## <a name="how-mrc-impacts-your-app"></a>Auswirkungen auf die MRC Ihrer app

### <a name="enabling-mrc-in-your-app"></a>Aktivierung MRC in Ihrer app

Standardmäßig muss eine app nicht nichts tun, um Benutzern mixed Reality Erfassungen zu ermöglichen. Jedoch, da der Entwurf von HoloLens 2 den Abstand zwischen der Kamera Foto/Video (PV) und die Anzeige erhöht, wir werden eingeführt eine neue Option zum Erzeugen einer 3. Kamera Rendern der Kamera und PV ausgerichtet **HoloLens 2**. 

Die Entscheidung bei 3. Kamera Rendern in HoloLens 2 bietet die folgenden Verbesserungen über die MRC standarderfahrung:
* – Hologramm Ausrichtung sowohl die Hände (für nahezu Interaktionen) Ihrer physischen Umgebung sollten fehlerfrei sein überhaupt entfernungen, anstatt einen Offset an entfernungen als die [konzentrieren Punkt](focus-point-in-unity.md) wie Sie in der standardmäßigen MRC sehen können.
* Das richtige Auge in den Kopfhörer werden nicht beeinträchtigt, wie es zum Rendern der Hologramme für die MRC-Ausgabe verwendet wird.

### <a name="disabling-mrc-in-your-app"></a>Deaktivieren MRC in Ihrer app

Wenn eine Direct2D-app verwendet [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://msdn.microsoft.com/library/windows/desktop/bb509554(v=vs.85).aspx) oder [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://msdn.microsoft.com/library/windows/desktop/bb173076(v=vs.85).aspx) um geschützte Inhalte mit einer ordnungsgemäß konfigurierten SwapChain anzuzeigen, werden die visuellen Inhalt der app automatisch verschlüsselt, während mixed Reality-Erfassung ausgeführt wird.

### <a name="knowing-when-mrc-is-active"></a>Wissen, wenn MRC aktiv ist.

Die [AppCapture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.aspx) Klasse kann von einer app verwendet werden, wissen Sie, wenn mixed Reality-Erfassung System (für Audio oder Video) ausgeführt wird.

>[!NOTE]
>Die AppCapture [GetForCurrentView](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.getforcurrentview.aspx) API kann Null, wenn mixed Reality-Erfassung nicht zur Verfügung, auf dem Gerät zurück. Es ist auch wichtig, heben Sie die Registrierung der CapturingChanged-Ereignis, wenn Ihre app angehalten wird, andernfalls MRC in einen blockierten Zustand erhalten kann.

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

Andere Anwendungen können dazu die [Windows Media-Capture-APIs](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) steuern die Kamera und einen Effekt hinzufügen, MRC-Video und Audio Einbeziehung von virtuellen Hologramme und Anwendung Audio in noch und Videos.

Anwendungen haben zwei Optionen, um den Effekt hinzufügen:
* Die ältere API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://msdn.microsoft.com/library/windows/apps/br211961.aspx)
* Das neue Microsoft empfohlene API (gibt ein Objekt, wodurch sie dynamische Eigenschaften bearbeiten): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addvideoeffectasync.aspx) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addaudioeffectasync.aspx) das erforderlich ist, erstellen Sie die app eine eigene Implementierung von [IVideoEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.ivideoeffectdefinition.aspx) und [IAudioEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.iaudioeffectdefinition.aspx). Informieren Sie sich die MRC-Wirkung-Beispiel für Beispiel für die Verwendung.

(Beachten Sie, dass diese Namespaces von Visual Studio nicht erkannt werden werden, aber die Zeichenfolgen immer noch gültig sind)

MRC Video Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)

|  Eigenschaftenname  |  Typ  |  Standardwert  |  Beschreibung | 
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediastreamtype.aspx))  |  1 (VideoRecord)  |  Beschreiben Sie die Capture-Stream für diesen Effekt verwendet wird. Audio ist nicht verfügbar. | 
|  HologramCompositionEnabled  |  boolean  |  TRUE  |  Flag zum Aktivieren oder Deaktivieren von Hologramme in videoaufzeichnung. | 
|  RecordingIndicatorEnabled  |  boolean  |  TRUE  |  Flag zum Aktivieren oder deaktivieren während der Erfassung – Hologramm Aufzeichnung Indikator auf dem Bildschirm. | 
|  VideoStabilizationEnabled  |  boolean  |  FALSE  |  Flag zum Aktivieren oder Deaktivieren von videostabilisierung mit Strom versorgt, durch die HoloLens-nachverfolgung. | 
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  Legen Sie, wie viele historische Frames für videostabilisierung verwendet werden. 0 ist, 0-Latenz und vom Standpunkt der Leistungsfähigkeit fast "frei". 15 empfiehlt sich für die höchste Qualität (auf Kosten der 15 Frames der Latenz und des Speichers). | 
|  GlobalOpacityCoefficient  |  float  |  0.9 (HoloLens) 1.0 (Immersive Kopfhörer)  |  Globale Deckkraft Koeffizienten des – Hologramm im Bereich von 0,0 (vollständig transparent) auf 1,0 festgelegt (vollständig deckend). | 
|  BlankOnProtectedContent  |  boolean  |  FALSE  |  Flag zum Aktivieren oder deaktivieren Sie einen leeren Frame zurückgeben, wenn ein 2d UWP-app mit geschützten Inhalt vorhanden ist. Wenn dieses Flag auf "false" und einer 2D-Texturmap. UWP-app ist ist mit geschützten Inhalt, 2D-UWP-app von einer geschützten Inhalt Textur in sowohl den Kopfhörer und die Erfassung von mixed Reality ersetzt wird. |
|  ShowHiddenMesh  |  boolean  |  FALSE  |  Flag zum Anzeigen der holographic Kamera ausgeblendeten Bereich Mesh und benachbarten Inhalt aktivieren oder deaktivieren. |

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

Mit dem Windows 10 April 2018 Update, diese Einschränkung gilt nicht, wenn die integrierten MRC-Kamera-Benutzeroberfläche verwendet wird, werden Sie nach dem Start einer app mit dem Foto/Videokamera eines Fotos oder Videos. In diesem Fall können die Auflösung und Framerate von den integrierten MRC-Kamera-Benutzeroberfläche über die normalen Werte beeinträchtigt werden.

Mit dem Windows 10 Oktober 2018 Update, diese Einschränkung gilt nicht für das streaming von MRC über Miracast.

#### <a name="mrc-access"></a>MRC-Zugriff

Mit dem Windows 10 April 2018 Update steht nicht mehr eine Einschränkung für mehrere apps, die Zugriff auf die MRC-Stream (allerdings der Zugriff auf die Kamera Foto/Video weiterhin gelten Einschränkungen).

Auf dem Windows 10 April 2018 zuvor Update einer app benutzerdefinierte MRC Recorder gegenseitig System MRC (Aufnahme von Fotos, Videos zu erfassen oder über die Windows Device Portal-streaming).

## <a name="see-also"></a>Siehe auch
* [Mixed Reality-Erfassung](mixed-reality-capture.md)
* [Spectator anzeigen](spectator-view.md)
