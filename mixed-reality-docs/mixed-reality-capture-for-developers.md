---
title: Erfassung gemischter Realität für Entwickler
description: Bewährte Methoden für die Erfassung gemischter Realität für Entwickler.
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
# <a name="mixed-reality-capture-for-developers"></a>Erfassung gemischter Realität für Entwickler

> [Hinweis!] Unter [Rendering von der folgenden PV-Kamera](#render-from-the-pv-camera-opt-in) finden Sie Anleitungen zu einer neuen MRC-Funktion für hololens 2.

Da ein Benutzer jederzeit ein MRC-Foto ( [Mixed Reality Capture](mixed-reality-capture.md) ) oder ein Video erstellen kann, sollten Sie beim Entwickeln Ihrer Anwendung einige Punkte beachten. Dies umfasst bewährte Methoden für die visuelle MRC-Qualität und die Reaktion auf Systemänderungen, während mrcs aufgezeichnet werden.

Entwickler können die Erfassung und Einbindung von Mixed Reality auch nahtlos in Ihre apps integrieren.

MRC auf hololens (erste Generation) unterstützt Videos und Fotos bis 720p, während MRC auf hololens 2 Videos bis zu 1080p und Fotos mit einer Auflösung von bis zu 4 KB unterstützt.

## <a name="the-importance-of-quality-mrc"></a>Die Wichtigkeit der Quality MRC

Erfasste Fotos und Videos mit gemischter Realität stellen wahrscheinlich die erste verfügbar, die ein Benutzer über Ihre APP verfügt. Gibt an, ob Sie auf Ihrer Microsoft Store Seite oder anderen Benutzern, die mrcs in sozialen Netzwerken gemeinsam nutzen, als Mixed Reality-Screenshots Sie können MRC verwenden, um Ihre APP zu demonstrieren, Benutzer zu informieren, Benutzer zu bitten, ihre gemischten Interaktionen der Welt zu teilen und die Benutzer Forschung und Problembehebung zu lösen.

## <a name="how-mrc-impacts-your-app"></a>Auswirkungen von MRC auf Ihre APP

### <a name="enabling-mrc-in-your-app"></a>Aktivieren von MRC in Ihrer APP

Standardmäßig muss eine APP nichts tun, damit Benutzer gemischte Reality-Erfassungen durchführen können.

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>Aktivieren der verbesserten Ausrichtung für MRC in Ihrer APP

Standardmäßig kombiniert Mixed Reality Capture die Holographic-Ausgabe des rechten Auges mit der Photo/Video (PV)-Kamera. Diese beiden Quellen werden mit dem Fokuspunkt kombiniert, der von der derzeit laufenden immersiven App festgelegt wird.

Dies bedeutet, dass holograms außerhalb der Fokusebene nicht ebenfalls ausgerichtet werden (aufgrund der physischen Entfernung zwischen der PV-Kamera und der rechten Anzeige).

#### <a name="set-the-focus-point"></a>Festlegen des Fokus Punkts

Immersive Apps (auf hololens) sollten den [Schwerpunkt Punkt](focus-point-in-unity.md) festlegen, in dem Sie Ihre Stabilisierungs Ebene festlegen möchten. Dadurch wird die beste Ausrichtung sowohl im Headset als auch bei der Erfassung gemischter Realität sichergestellt.

Wenn kein Fokuspunkt festgelegt ist, wird die Stabilisierungs Ebene standardmäßig auf zwei Meter festgelegt.

#### <a name="render-from-the-pv-camera-opt-in"></a>Rendering von der PV-Kamera (Opt-in)

Hololens 2 bietet die Möglichkeit, eine immersive APP **aus der PV-Kamera** zu Renderern, während die gemischte Reality-Erfassung ausgeführt wird. Um sicherzustellen, dass die APP das zusätzliche Rendering ordnungsgemäß unterstützt, muss diese Funktion von der APP übernommen werden.

Das Rendering von der PV-Kamera bietet die folgenden Verbesserungen im Vergleich zum MRC-Standardverhalten:
* Die Ausrichtung von holograms an die physische Umgebung und die Hände (bei nahezu Interaktionen) sollte in allen Abständen genau sein, anstatt einen Offset in anderen Entfernungen als dem Punkt zu verwenden, wie Sie in der standardmäßigen MRC-Datei sehen könnten.
* Das richtige Auge im Headset wird nicht beeinträchtigt, da es nicht zum renderingder holograms für die MRC-Ausgabe verwendet wird.

Es gibt drei Schritte, um das Rendering von der PV-Kamera aus zu aktivieren:
1. Aktivieren von "photovideocamera holographicviewconfiguration"
2. Verarbeiten des zusätzlichen holographiccamera-Rendering
3. Überprüfen Sie, ob die Shader und der Code aus diesem zusätzlichen holographiccamera korrekt dargestellt werden.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration"></a>Aktivieren von "photovideocamera holographicviewconfiguration"

Zum Anmelden aktiviert eine APP einfach die [holographicviewconfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)von photovideocamera:
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfiguration.PhotoVideoCamera);
if (view != null)
{
   view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>Verarbeiten des zusätzlichen holographiccamera-Rendering in DirectX

Wenn die APP die Möglichkeit hat, von der PV-Kamera zu Rendering und die Mixed Reality-Erfassung zu starten:
1. Das cameraadded-Ereignis von holographicspace wird ausgelöst. Dieses Ereignis kann verzögert werden, wenn die APP die Kamera zu diesem Zeitpunkt nicht verarbeiten kann.
2. Nachdem das Ereignis abgeschlossen wurde (und keine ausstehenden Verweise vorhanden sind), wird der holographiccamera in der Liste der addedkameras des nächsten holographicframes angezeigt.

Wenn die gemischte Reality-Erfassung beendet wird (oder wenn die APP die Ansichts Konfiguration deaktiviert, während die gemischte Reality-Erfassung ausgeführt wird): der holographiccamera wird in der removedcameras-Liste des nächsten holographicframe angezeigt, und das cameraremove-Ereignis von holographicspace wird Lösch.

Holographiccamera wurde eine [viewconfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) -Eigenschaft hinzugefügt, um die Konfiguration zu identifizieren, zu der eine Kamera gehört.

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>Verarbeiten des zusätzlichen holographiccamera-Rendering in Unity

>[!NOTE]
> Die Unity-Unterstützung zum Rendering von der PV-Kamera befindet sich in der Entwicklung und kann noch nicht verwendet werden. Diese Dokumentation wird aktualisiert, wenn ein Build von Unity mit Unterstützung für das Rendering von der PV-Kamera verfügbar ist.

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>Überprüfen von Shadern und Code Unterstützung zusätzlicher Kameras

Führen Sie eine gemischte Reality-Erfassung aus, und überprüfen Sie, ob ungewöhnliche Ausrichtung, fehlende Inhalte oder Leistungsprobleme vorliegen. Aktualisieren Sie Shader und Code entsprechend.

Wenn bestimmte Szenen das Rendern auf eine zusätzliche Kamera nicht unterstützen, können Sie die holographicviewconfiguration von "photovideocamera" deaktivieren.

### <a name="disabling-mrc-in-your-app"></a>Deaktivieren von MRC in Ihrer APP

#### <a name="2d-app"></a>2D-App

2D-Apps können auswählen, dass Ihre visuellen Inhalte verdeckt werden, wenn die gemischte Reality-Erfassung ausgeführt wird:
* Mit dem [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present) -Flag vorhanden
* Erstellen Sie die Swapkette der APP mit dem [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) -Flag.
* Mit dem Windows 10-Update von Mai 2019, Festlegen von " [isskreendcaptureaktivierte](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled) " von applicationview

#### <a name="immersive-app"></a>Immersive App

Immersive Apps können auswählen, ob Ihre visuellen Inhalte von der gemischten Realität-Erfassung ausgeschlossen werden sollen, indem Sie:
* Festlegen des [iscontentschutzaktivierten](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) holographiccamerarenderingparameter, um die gemischte Reality-Erfassung für den zugehörigen Frame zu deaktivieren
* Festlegen von " [ishardwarecontentschutzaktivierte](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) " von holographiccamera zum Deaktivieren der Transformation für gemischte Realität für die zugehörige Holographic-Kamera

#### <a name="password-keyboard"></a>Kenn Wort Tastatur

Mit dem Windows 10-Update von Mai 2019 werden visuelle Inhalte automatisch von Mixed Reality Capture ausgeschlossen, wenn eine Kennwort-oder PIN-Tastatur sichtbar ist.

### <a name="knowing-when-mrc-is-active"></a>Wissen, wenn MRC aktiv ist

Die [appcapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture) -Klasse kann von einer App verwendet werden, um zu erfahren, wann die gemischte Reality-Erfassung (für Audiodaten oder Videos) ausgeführt wird.

>[!NOTE]
>Die [getforcurrentview](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) -API von appcapture kann NULL zurückgeben, wenn die gemischte Reality-Erfassung auf dem Gerät nicht verfügbar ist. Es ist auch wichtig, das capturingchanged-Ereignis zu deaktivieren, wenn Ihre APP angehalten wird. andernfalls kann MRC in den Status "blockiert" versetzt werden.

### <a name="best-practices-hololens-specific"></a>Bewährte Methoden (hololens-spezifisch)

MRC funktioniert ohne zusätzliche Arbeit von Entwicklern, aber es gibt einige Dinge, die Sie beachten sollten, um die beste Lösung für die Erfassung Ihrer APP bereitzustellen.

**MRC verwendet den Alpha-Channel von Hologram, um sich mit den [Kamera](locatable-camera.md) Bildern zu vermischen.**

Der wichtigste Schritt besteht darin, sicherzustellen, dass Ihre APP in transparenter schwarz gelöscht wird, anstatt auf ein undurchsichtiges schwarz zu löschen. In Unity erfolgt dies standardmäßig mit dem mixedrealitytoolkit, aber wenn Sie in nicht-Unity entwickeln, müssen Sie möglicherweise eine einzelne Zeilen Änderung vornehmen.

Im folgenden finden Sie einige Elemente, die Sie möglicherweise in MRC sehen, wenn Ihre APP nicht in transparent Black gelöscht wird:

**Beispiel Fehler**: Schwarze Ränder um den Inhalt (Fehler beim Löschen in transparente schwarze)

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

**Beispiel Fehler**: Die gesamte Hintergrundszene des holograms wird schwarz angezeigt. Das Festlegen eines Hintergrund-Alpha-Werts von 1 ergibt einen schwarzen Hintergrund.

![Das Festlegen eines Hintergrund-Alpha-Werts von 1 ergibt einen schwarzen Hintergrund.](images/clearopaqueblack-300px.png)

**Erwartetes Ergebnis**: Holograms werden ordnungsgemäß mit der realen Umgebung vermischt (erwartetes Ergebnis beim Löschen auf transparente schwarze).

![Erwartetes Ergebnis beim Löschen auf transparente schwarze](images/cleartransparentblack-300px.png)

**Lösung**:
* Ändern Sie alle Inhalte, die als undurchsichtiges schwarz angezeigt werden, um einen Alphawert von 0 zu erhalten.
* Stellen Sie sicher, dass die app in transparent Black gelöscht wird.
* Unity ist standardmäßig deaktiviert, um automatisch mit dem mixedrealitytoolkit zu löschen. wenn es sich jedoch um eine nicht-Unity-App handelt, sollten Sie die mit ID3D11DeiceContext:: clearrendertargetview () verwendete Farbe ändern. Sie möchten sicherstellen, dass Sie transparent Black (0, 0, 0, 0) anstelle von undurchsichtigem schwarz (0, 0, 0, 1) deaktivieren.

Sie können jetzt die Alpha Werte Ihrer Assets optimieren, wenn Sie möchten, aber in der Regel nicht erforderlich sind. In den meisten Fällen sehen die mrcs standardmäßig gut aus. MRC geht davon aus, dass ein prämultipliziertes Alpha Die Alpha Werte wirken sich nur auf die MRC-Erfassung aus.

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>Was Sie erwartet, wenn MRC auf hololens aktiviert ist

Folgendes gilt für hololens (First-Generation) und hololens 2, sofern nichts anderes angegeben ist:

* Das System führt zu einer Drosselung der Anwendung auf das 30Hz-Rendering. Dadurch wird ein gewisser Spielraum für die MRC-Durchführung geschaffen, sodass die APP keine Konstante Budget Reserve aufbewahren muss und auch mit der MRC-Videodaten Satz Framerate von 30 fps übereinstimmt.
* – Hologramm-Inhalte auf der rechten Seite des Geräts erscheinen möglicherweise als "Glanz", wenn Sie MRC aufzeichnen/streamen: Text kann schwieriger zu lesen sein, und – Hologramm-Kanten werden möglicherweise mehr verzweigt.
* MRC-Fotos und-Videos berücksichtigen den [Schwerpunkt Punkt](focus-point-in-unity.md) der Anwendung, wenn Sie von der Anwendung aktiviert wurde. Dadurch wird sichergestellt, dass Hologramme genau positioniert werden. Bei Videos wird der Fokuspunkt geglättet, sodass holograms möglicherweise langsam in den Platz wechseln, wenn sich die Fokuspunkt Tiefe erheblich ändert. Holograms, die sich in unterschiedlichen Tiefen vom Fokuspunkt befinden, werden möglicherweise in der realen Welt ausgeglichen (siehe Beispiel unten, wobei der Fokuspunkt auf 2 Meter festgelegt ist, aber – Hologramm auf 1 Meter festgelegt ist).

![Holograms bei 2 Messgeräten werden auf der ganzen Welt hervorragend registriert angezeigt. Holograms in der Nähe oder in weiten Abständen können leicht versetzt werden.](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>Integrieren von MRC-Funktionen in Ihre APP

Ihre Mixed Reality-App kann die MRC-Foto-oder Video Erfassung in der APP initiieren, und die erfassten Inhalte werden Ihrer APP zur Verfügung gestellt, ohne dass Sie auf der "Kamera" des Geräts gespeichert werden. Sie können eine benutzerdefinierte MRC-Aufzeichnung erstellen oder die Benutzeroberfläche der integrierten Kamera Erfassung nutzen. 

### <a name="mrc-with-built-in-camera-ui"></a>MRC mit integrierter Kamera-Benutzeroberfläche

Entwickler können die *[API Capture UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* verwenden, um ein vom Benutzer erfasstes gemischtes Reality-Foto oder Video mit nur wenigen Codezeilen zu erhalten.

Diese API gestartet die integrierte MRC-Kamera-Benutzeroberfläche, von der der Benutzer ein Foto oder Video aufnehmen kann, und gibt die resultierende Erfassung an Ihre APP zurück.  Wenn Sie eine eigene Benutzeroberfläche für die Kamera erstellen oder einen niedrigeren Zugriff auf den Erfassungsdaten Strom benötigen, können Sie eine benutzerdefinierte Mixed Reality Capture Recorder erstellen.

### <a name="creating-a-custom-mrc-recorder"></a>Erstellen einer benutzerdefinierten MRC-Aufzeichnung

Während der Benutzer immer ein Foto oder Video mit dem System-MRC-Erfassungs Dienst auslöst, möchte eine Anwendung möglicherweise eine benutzerdefinierte Kamera-APP erstellen, aber holograms wie MRC in den Kameradaten Strom einschließen. Dadurch kann die Anwendung Erfassungen im Namen des Benutzers starten, eine benutzerdefinierte Aufzeichnungs Benutzeroberfläche erstellen oder MRC-Einstellungen anpassen, um einige Beispiele zu nennen.

**Holostudio fügt eine benutzerdefinierte MRC-Kamera mithilfe von MRC-Effekten hinzu**

![Holostudio fügt eine benutzerdefinierte MRC-Kamera mithilfe von MRC-Effekten hinzu](images/cameraiconholostudio-300px.jpg)

Unity-Anwendungen sollten [Locatable_camera_in_Unity](locatable-camera-in-unity.md) für die-Eigenschaft sehen, um holograms zu aktivieren.

Andere Anwendungen können hierfür die [Windows Media Capture-APIs](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) verwenden, um die Kamera zu steuern und ein MRC-Video und einen Audioeffekt hinzuzufügen, um virtuelle Hologramme und anwendungaudiodaten in Stills und Videos einzubeziehen.

Anwendungen haben zwei Möglichkeiten, den Effekt hinzuzufügen:
* Die ältere API: [Windows. Media. Capture. mediacapture. addeffectasync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* Die neue von Microsoft empfohlene API (gibt ein-Objekt zurück, sodass dynamische Eigenschaften geändert werden können): [Windows. Media. Capture. mediacapture. addvideoeffectasync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows. Media. Capture. mediacapture. addaudioeffectasync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) , die erfordert, dass die APP eine eigene Implementierung von [ivideoeffectdefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) erstellt und [ Iaudioeffectdefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition). Ein Beispiel für die Verwendung finden Sie im Beispiel für den MRC-Effekt.

>[!NOTE]
> Der Windows. Media. mixedrealitycapture-Namespace wird von Visual Studio nicht erkannt, aber die Zeichen folgen sind immer noch gültig.

MRC-Video Effekt (**Windows. Media. mixedrealitycapture. mixedrealitycapturevideoeffect**)

|  Eigenschaftenname  |  Typ  |  Standardwert  |  Beschreibung | 
|----------|----------|----------|----------|
|  Streamtype  |  UInt32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))  |  1 (videorecord)  |  Beschreiben Sie den Erfassungsdaten Strom, für den dieser Effekt verwendet wird. Audiodaten sind nicht verfügbar. | 
|  Hologramcompositionaktivierte  |  boolean  |  TRUE  |  Flag zum Aktivieren oder Deaktivieren von holograms bei der Video Erfassung. | 
|  Recordingindialisioraktiviert  |  boolean  |  TRUE  |  Flag zum Aktivieren oder Deaktivieren des Aufzeichnungs Indikators auf dem Bildschirm während der – Hologramm-Erfassung. | 
|  Videostabilizationaktivierte  |  boolean  |  FALSE  |  Flag zum Aktivieren oder Deaktivieren der Videostabilisierung, die von hololens-Tracker unterbunden wird. | 
|  Videostabilizationbufferlength  |  UINT32  |  0  |  Legen Sie fest, wie viele historische Frames für die Videostabilisierung verwendet werden. 0 (null): Latenz und nahezu "kostenlos" aus Leistungs-und Leistungs Perspektive. 15 wird für die höchste Qualität empfohlen (auf Kosten von 15 Frames an Latenz und Arbeitsspeicher). | 
|  Globalopacitykoeffizienten  |  float  |  0,9 (hololens) 1,0 (immersives Headset)  |  Legen Sie den globalen Deckkraft Koeffizienten von – Hologramm im Bereich von 0,0 (vollständig transparent) auf 1,0 (vollständig deckend) fest. | 
|  Blankonprotectedcontent  |  boolean  |  FALSE  |  Flag zum Aktivieren oder Deaktivieren der Rückgabe eines leeren Frames, wenn eine 2D-UWP-App geschützte Inhalte anzeigt. Wenn dieses Flag false ist und eine 2D-UWP-App geschützte Inhalte anzeigt, wird die 2D-UWP-app durch eine geschützte Inhalts Textur sowohl im Headset als auch in der Mixed Reality-Erfassung ersetzt. |
|  Showhiddenmesh  |  boolean  |  FALSE  |  Flag zum Aktivieren oder Deaktivieren der Anzeige des ausgeblendeten Bereichs Netzes der Holographic-Kamera und des benachbarten Inhalts. |
| Outputsize | Größe | 0, 0 | Legen Sie die gewünschte Ausgabegröße nach dem Zuschneiden für die Videostabilisierung fest. Eine standardmäßige zuergröße wird ausgewählt, wenn 0 oder eine ungültige Ausgabegröße angegeben wird. |
| Preferredhologrammperspective | UINT32 | 1 (photovideocamera) | Eine Aufzählung, mit der angegeben wird, welche Konfiguration der holografischen Kameraansicht aufgezeichnet werden soll. Das Festlegen von 0 (anzeigen) bedeutet, dass die APP nicht zum Rendering von der Foto-/Videokamera aufgefordert wird. |

MRC-Audioeffekt (**Windows. Media. mixedrealitycapture. mixedrealitycaptureaudioeffect**)

<table>
<tr>
<th>Eigenschaftenname</th>
<th>Typ</th>
<th>Standardwert</th>
<th>Beschreibung</th>
</tr>
<tr>
<td>Mixermode</td>
<td>UINT32</td>
<td>2</td>
<td>
<ul>
<li>1,0 Nur MIC-Audiodaten</li>
<li>1 Nur systemaudiodatei</li>
<li>2,2 MIC-und systemaudiodaten</li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a>Gleichzeitige MRC-Einschränkungen

Es gibt bestimmte Einschränkungen für mehrere apps, die gleichzeitig auf MRC zugreifen.

#### <a name="photovideo-camera-access"></a>Foto-/Videokamera-Zugriff

Die Foto-/Videokamera ist auf die Anzahl der Prozesse beschränkt, die gleichzeitig auf die Kamera zugreifen können. Während ein Prozess das Aufzeichnen von Videos oder das Aufzeichnen eines Fotos durchführt, kann ein anderer Prozess die Foto-/Videokamera nicht abrufen. (Dies gilt für die gemischte Reality-Erfassung und die standardmäßige Foto-/Videoerfassung)

Mit hololens 2 kann eine APP die Eigenschaft " [sharingmode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode) " von mediacaptureinitializationsettings verwenden, um anzugeben, dass Sie sharedreadnur ausführen möchten, wenn Sie keine exklusive Kontrolle über die Foto-/Videokamera benötigen. Dies bedeutet, dass die Auflösung und Framerate der Erfassung darauf beschränkt sind, welche anderen apps die Kamera für die Bereitstellung konfiguriert hat.

##### <a name="built-in-mrc-photovideo-camera-access"></a>Integrierter MRC-Foto-/Videokamer-Zugriff

In Windows 10 integrierte MRC-Funktionalität (über Cortana, Startmenü, Hardware Kombinationen, miracast, Windows-Geräte Portal):
* Wird standardmäßig mit exclusivecontrol ausgeführt

Allerdings wurde die Unterstützung für jedes Subsystem hinzugefügt, um in einem freigegebenen Modus zu arbeiten:
* Wenn eine APP exclusivecontrol-Zugriff auf die Foto-/Videokamera anfordert, wird die integrierte MRC-Datei automatisch mit der Foto-/Videokamera beendet, sodass die App-Anforderung erfolgreich ausgeführt wird.
* Wenn die integrierte MRC gestartet wird, während eine APP exclusivecontrol hat, wird die integrierte MRC-Datei im sharedreadonly-Modus ausgeführt.

Diese Funktion für den freigegebenen Modus weist bestimmte Einschränkungen auf:
* Foto über Cortana, Hardware Verknüpfungen oder Startmenü: Erfordert das Windows 10-Update vom April 2018 (oder höher)
* Video über Cortana, Hardware Verknüpfungen oder das Startmenü: Erfordert das Windows 10-Update vom April 2018 (oder höher)
* Streaming von MRC über miracast: Erfordert das Windows 10-Update vom Oktober 2018 (oder höher)
* Streaming von MRC über das Windows-Geräte Portal oder über die "hololens"-Begleit-App: Erfordert hololens 2

>[!NOTE]
> Die Auflösung und die Framerate der integrierten MRC-Kamera-Benutzeroberfläche werden möglicherweise von den normalen Werten reduziert, wenn eine andere APP die Foto-/Videokamera verwendet.

#### <a name="mrc-access"></a>MRC-Zugriff

Beim Windows 10-Update vom April 2018 gibt es keine Einschränkung mehr für mehrere apps, die auf den MRC-Stream zugreifen (der Zugriff auf die Foto-und Videokamera hat jedoch weiterhin Einschränkungen).

Vor dem Windows 10-Update vom April 2018 konnte sich die benutzerdefinierte MRC-Aufzeichnung einer APP mit System MRC (Aufzeichnen von Fotos, Aufzeichnen von Videos oder Streaming aus dem Windows-Geräte Portal) gegenseitig ausschließen.

## <a name="see-also"></a>Siehe auch
* [Mixed Reality-Aufnahme](mixed-reality-capture.md)
* [Spectator View](spectator-view.md)
