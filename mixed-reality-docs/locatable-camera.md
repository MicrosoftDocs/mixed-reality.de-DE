---
title: Erhebbare Kamera
description: Allgemeine Informationen zu der hololens-Front-Kamera, ihrer Funktionsweise und den Profilen und Auflösungen, die Entwicklern zur Verfügung stehen.
author: cdedmonds
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: Kamera, hololens, Farbkamera, Vorderseite, hololens 2, CV, Maschinelles sehen, Zeichen, Marker, QR-Code, QR, Foto, Video
ms.openlocfilehash: e906da63b07643ccbf386c6fc72cc3c58006ae72
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438505"
---
# <a name="locatable-camera"></a>Erhebbare Kamera

Hololens enthält eine weltweit eingebundene Kamera, die auf der Vorderseite des Geräts bereitgestellt wird. Dadurch können apps sehen, was der Benutzer sieht. Entwickler haben Zugriff auf und die Steuerung der Kamera, ebenso wie bei Farbkameras auf Smartphones, portables oder Desktops. Die gleichen universellen Windows [Media Capture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) -und Windows Media Foundation-APIs, die auf mobilen und Desktop-apps funktionieren, funktionieren in hololens. Unity [hat diese Windows-APIs ebenfalls umschließt](locatable-camera-in-unity.md) , um die einfache Verwendung der Kamera in hololens für Aufgaben wie das nehmen von regulären Fotos und Videos (mit oder ohne holograms) zu abstrahieren und die Position der Kamera in der Szene zu ermitteln.

## <a name="device-camera-information"></a>Gerätekamera Informationen

### <a name="hololens-first-generation"></a>Hololens (erste Generation)

* Mit dem automatischen Leerraum, dem automatischen verfügbar machen und der Pipeline für die vollständige Bildverarbeitung fixierte Foto-/Video-Kamera (PV).
* Die Welt der weißen Datenschutz wird immer dann beleuchtet, wenn die Kamera aktiv ist.
* Die Kamera unterstützt die folgenden Modi (alle Modi sind 16:9-Seitenverhältnis) bei 30, 24, 20, 15 und 5 fps:

  |  Video  |  Preview  |  Auch  |  Horizontales Feld der Ansicht (H-FOV) |  Empfohlene Verwendung | 
  |----------|----------|----------|----------|----------|
  |  1\.280 x 720 |  1\.280 x 720 |  1\.280 x 720 |  45deg  |  (Standardmodus mit Videostabilisierung) | 
  |  n. v. |  n. v. |  2048x1152 |  67deg |  Bild mit der höchsten Auflösung | 
  |  1408x792 |  1408x792 |  1408x792 |  48deg |  Überprüfung (Padding) vor der Videostabilisierung | 
  |  1344x756 |  1344x756 |  1344x756 |  67deg |  Großer FOV-Videomodus mit Overscan | 
  |  896x504 |  896x504 |  896x504 |  48deg |  Niedriger Energie-/tieflösungmodus für Abbild Verarbeitungsaufgaben | 

### <a name="hololens-2"></a>HoloLens 2

* Auto-Fokus Foto/Video-Kamera (PV) mit automatischem Leerraum, automatischer Verfügbarkeit und vollständiger Bild Verarbeitungs Pipeline.
* Die Welt der weißen Datenschutz wird immer dann beleuchtet, wenn die Kamera aktiv ist.
* Hololens 2 unterstützt verschiedene Kameraprofile. Erfahren Sie, wie [Sie Kamerafunktionen ermitteln und auswählen](https://docs.microsoft.com//windows/uwp/audio-video-camera/camera-profiles)können.
* Die Kamera unterstützt die folgenden Profile und Auflösungen (alle Video Modi sind 16:9-Seitenverhältnis):
  
  | Profil                                         | Video     | Preview   | Auch     | Frame Raten | Horizontales Feld der Ansicht (H-FOV) | Empfohlene Verwendung                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | Legacy, 0 balancedvideoandphoto, 100             | 2272x1278 | 2272x1278 |           | 15, 30       | 64,69                            | Videoaufzeichnung mit hoher Qualität                |
  | Legacy, 0 balancedvideoandphoto, 100             | 896x504   | 896x504   |           | 15, 30       | 64,69                            | Vorschau Datenstrom für hochwertige Foto Erfassung |
  | Legacy, 0 balancedvideoandphoto, 100             |           |           | 3904x2196 |             | 64,69                            | Foto Erfassung mit hoher Qualität                  |
  | Balancedvideoandphoto, 120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15, 30       | 64,69                            | Szenarios mit langer Laufzeit                     |
  | Balancedvideoandphoto, 120                       | 1504x846  | 1504x846  |           | 15, 30       | 64,69                            | Szenarios mit langer Laufzeit                     |
  | Videokonferenzen, 100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15, 30, 60    | 64,69                            | Video Konferenzen, Szenarios mit langer Laufzeit |
  | Videokonferenzen, 100                           | 1504x846  | 1504x846  |           | 5, 15, 30, 60  | 64,69                            | Video Konferenzen, Szenarios mit langer Laufzeit |
  | Videoconferencing, 100 balancedvideoandphoto, 120 | 1920x1080 | 1920x1080 | 1920x1080 | 15, 30       | 64,69                            | Video Konferenzen, Szenarios mit langer Laufzeit |
  | Videoconferencing, 100 balancedvideoandphoto, 120 | 1\.280 x 720  | 1\.280 x 720  | 1\.280 x 720  | 15, 30       | 64,69                            | Video Konferenzen, Szenarios mit langer Laufzeit |
  | Videoconferencing, 100 balancedvideoandphoto, 120 | 1128x636  |           |           | 15, 30       | 64,69                            | Video Konferenzen, Szenarios mit langer Laufzeit |
  | Videoconferencing, 100 balancedvideoandphoto, 120 | 960 x 540   |           |           | 15, 30       | 64,69                            | Video Konferenzen, Szenarios mit langer Laufzeit |
  | Videoconferencing, 100 balancedvideoandphoto, 120 | 760x428   |           |           | 15, 30       | 64,69                            | Video Konferenzen, Szenarios mit langer Laufzeit |
  | Videoconferencing, 100 balancedvideoandphoto, 120 | 640x360   |           |           | 15, 30       | 64,69                            | Video Konferenzen, Szenarios mit langer Laufzeit |
  | Videoconferencing, 100 balancedvideoandphoto, 120 | 500 x 282   |           |           | 15, 30       | 64,69                            | Video Konferenzen, Szenarios mit langer Laufzeit |
  | Videoconferencing, 100 balancedvideoandphoto, 120 | 424x240   |           |           | 15, 30       | 64,69                            | Video Konferenzen, Szenarios mit langer Laufzeit |

>[!NOTE]
>Kunden können die [gemischte Reality-Erfassung](mixed-reality-capture.md) nutzen, um Videos oder Fotos Ihrer APP zu erstellen, die Hologramme und Videostabilisierung enthalten.
>
>Als Entwickler sollten Sie beim Erstellen Ihrer APP berücksichtigen, dass Sie beim Erfassen von Inhalten so gut wie möglich aussehen sollten. Sie können die gemischte Reality-Erfassung auch direkt in Ihrer APP aktivieren (und anpassen). Weitere Informationen finden Sie unter [Mixed Reality Capture für Entwickler](mixed-reality-capture-for-developers.md).

## <a name="locating-the-device-camera-in-the-world"></a>Auffinden der Gerätekamera weltweit

Wenn hololens Fotos und Videos aufnimmt, beinhalten die erfassten Frames den Ort der Kamera auf der Welt und das Modell der Kamera. Dies ermöglicht es Anwendungen, die Position der Kamera in der realen Welt für erweiterte Abbild Erstellungs Szenarios zu untersuchen. Entwickler können Ihre eigenen Szenarien mithilfe Ihrer bevorzugten Bildverarbeitung oder Ihrer benutzerdefinierten Maschinelles Sehen-Bibliotheken kreativ gestalten.

"Kamera" an anderer Stelle in der hololens-Dokumentation bezieht sich auf die "virtuelle Spiel Kamera" (die Frustration, in der die APP rendert). Sofern nicht anders angegeben, bezieht sich "Kamera" auf dieser Seite auf die tatsächliche RGB-Farbkamera.

Die Details auf dieser Seite decken mithilfe der [mediaframereferenzierungsklasse](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.mediaframereference) ab, aber es gibt auch APIs zum Abrufen von systeminternen systeminternen Funktionen und Speicherorten mithilfe von [Media Foundation Attributen](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx). Weitere Informationen finden Sie im Beispiel für die [holografische Gesichts Verfolgung](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) .

### <a name="images-with-coordinate-systems"></a>Images mit Koordinatensystemen

Jeder Bild Rahmen (egal ob Foto oder Video) enthält ein [spatialcoordinatesystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) , das zum Zeitpunkt der Erfassung auf der Kamera verankert ist, auf die mithilfe der [CoordinateSystem](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) -Eigenschaft von [mediaframereferenziert](https://docs.microsoft.com//uwp/api/Windows.Media.Capture.Frames.MediaFrameReference)werden kann. Außerdem enthält jeder Frame eine Beschreibung des Kamera Zeichen Modells, das in der Eigenschaft [cameraintrinsics](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) zu finden ist. In der Regel definieren diese Transformationen für jedes Pixel einen Strahl in 3D-Raum, der den Pfad darstellt, der von den Photonen, die das Pixel erzeugt haben, übernommen wird. Diese Strahlen können mit anderem Inhalt in der APP verknüpft werden, indem die Transformation aus dem Koordinatensystem des Frames in ein anderes Koordinatensystem (z. b. aus einem [stationären Verweis Rahmen](coordinate-systems.md#stationary-frame-of-reference)) bezogen wird. Zusammenfassend bietet jeder Bild Rahmen Folgendes:
* Pixel Daten (im Format RGB/NV12/JPEG/usw.)
* Ein [spatialcoordinatesystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) vom Speicherort der Erfassung
* Eine [cameraintrinsics](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) -Klasse, die den Linsen Modus der Kamera enthält.

### <a name="camera-to-application-specified-coordinate-system"></a>Von der Kamera zu Anwendung angegebenes Koordinaten System

Um von den "cameraintrinsics" und "cameracoordinatesystem" in ihr Anwendungs-/World-Koordinatensystem zu wechseln, benötigen Sie Folgendes:

[Einsetzbare Kamera in Unity](locatable-camera-in-unity.md): cameratoworldmatrix wird automatisch von der photocaptureframe-Klasse bereitgestellt (sodass Sie sich keine Gedanken über die "cameracoordinatesystem"-Transformationen machen müssen).

[Einsetzbare Kamera in DirectX](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking): das Beispiel für die holografische Gesichts Verfolgung zeigt die relativ unkomplizierte Methode zum Abfragen der Transformation zwischen dem Koordinatensystem der Kamera und ihren eigenen Anwendungs Koordinatensystemen.

### <a name="distortion-error"></a>Verzerrungs Fehler

Bei hololens sind das Video und die bildstreams in der Bild Verarbeitungs Pipeline des Systems unverzerrt, bevor die Frames der Anwendung zur Verfügung gestellt werden (der vorschaustream enthält die ursprünglichen verzerrten Rahmen). Da nur die cameraintrinsics verfügbar gemacht werden, müssen Anwendungen davon ausgehen, dass Bild Rahmen eine perfekte Kamera darstellen.

Bei hololens (erste Generation) kann die unzerungs Funktion im Bildprozessor bei der Verwendung von cameraintrinsics in den Frame-Metadaten weiterhin einen Fehler von bis zu 10 Pixel hinterlassen. In vielen Anwendungsfällen ist dieser Fehler nicht von Bedeutung. Wenn Sie z. b. Hologramme an realen Poster/Markierungen ausrichten, sehen Sie sich beispielsweise einen < 10px-Offset an (ungefähr 11mm für holograms, der 2 Meter entfernt ist), könnte dieser Fehler bei der Verzerrung auftreten. 

## <a name="locatable-camera-usage-scenarios"></a>Szenarios für die verwendbare Verwendung von Kameras

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>Foto oder Video in der Welt anzeigen, in der es aufgezeichnet wurde

Die Gerätekamera Rahmen verfügen über eine "Kamera-an-Welt"-Transformation, die verwendet werden kann, um genau anzuzeigen, wo das Gerät war, als das Abbild erstellt wurde. Sie können z. b. ein kleines Holographic-Symbol an dieser Stelle positionieren (cameratoworld. multiplypoint (Vector3. Zero)) und sogar einen kleinen Pfeil in der Richtung zeichnen, in der die Kamera steht (cameratoworld. multiplyvector (Vector3. Forward)).

### <a name="tag--pattern--poster--object-tracking"></a>Tag/Muster/Poster/Objektverfolgung

Viele Mixed Reality-Anwendungen verwenden ein erkennbares Bild oder visuelles Muster, um einen standbybaren Punkt im Raum zu schaffen. Diese wird dann zum Rendering von Objekten in Relation zu diesem Punkt oder zum Erstellen eines bekannten Speicher Orts verwendet. Einige Verwendungen von hololens beinhalten das Auffinden eines realen Objekts, das mit einem-Objekt (z. b. einem TV-Monitor mit einem QR-Code) gekennzeichnet ist, das Platzieren von holograms über das-Objekt und das visuelle koppeln mit nicht hololens-Geräten wie Tablets, die für die Kommunikation mit hololens über Wi-Fi.

Um ein visuelles Muster zu erkennen und dieses Objekt dann in den Anwendungs Raum zu versetzen, benötigen Sie einige Dinge:
1. Ein Bildmuster Erkennungs-Toolkit, z. b. QR-Code, AR-Tags, Gesichts Finder, Zirkel Tracker, OCR usw.
2. Bild Rahmen zur Laufzeit erfassen und an die Erkennungs Schicht übergeben
3. Entprojizieren Sie Ihre Image Positionen wieder in die Welt Positionen oder wahrscheinlich weltweit. Details zu diesen Features finden Sie unter
4. Positionieren Sie Ihre virtuellen Modelle an den Standorten der Welt.

Einige wichtige Bild Verarbeitungs Links:
* [OpenCV](https://opencv.org/)
* [QR-Tags](https://en.wikipedia.org/wiki/QR_code)
* [Fakesdk](https://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

Die Beibehaltung einer interaktiven Anwendungsframe-Rate ist wichtig, insbesondere beim Umgang mit Bild Erkennungsalgorithmen mit langer Laufzeit. Aus diesem Grund verwenden wir häufig das folgende Muster:
1. Haupt Thread: verwaltet das Kamera Objekt.
2. Haupt Thread: neue Frames anfordern (Async)
3. Haupt Thread: neue Frames an nach Verfolgungs Thread übergeben
4. Überwachungs Thread: verarbeitet das Image zum Erfassen von Schlüsselpunkten.
5. Haupt Thread: verschiebt das virtuelle Modell entsprechend der gefundenen wichtigen Punkte.
6. Haupt Thread: Wiederholen aus Schritt 2

Einige Abbild Markersysteme stellen nur einen einzelnen Pixel Speicherort bereit (andere stellen die vollständige Transformation bereit. in diesem Fall wird dieser Abschnitt nicht benötigt), was einem Ray möglicher Standorte entspricht. Um zu einem einzelnen 3D--Speicherort zu gelangen, können wir mehrere Strahlen nutzen und das Endergebnis nach dem ungefähren Schnittpunkt suchen. Zu diesem Zweck müssen Sie folgende Schritte ausführen:
1. Schleife zum Erfassen mehrerer Kamerabilder
2. Suchen der zugehörigen featurepunkte und ihrer weltweiten Strahlen
3. Wenn Sie ein Wörterbuch mit Features haben, die jeweils über mehrere Welt Strahlen verfügen, können Sie den folgenden Code verwenden, um die Schnittmenge dieser Strahlen zu lösen:

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

Bei zwei oder mehr nach verfolgten tagstandorten können Sie eine modellierte Szene so positionieren, dass Sie dem aktuellen Szenario des Benutzers entspricht. Wenn Sie die Schwerkraft nicht annehmen können, benötigen Sie drei Tag-Orte. In vielen Fällen wird ein einfaches Farbschema verwendet, bei dem weiße Bereiche in Echtzeit überwachte tagspeicher Orte darstellen und blaue Bereiche modellierte tagspeicher Orte darstellen, sodass der Benutzer die ausrichtungsqualität visuell einschätzen kann. Wir gehen davon aus, dass Sie das folgende Setup in allen Anwendungen ausführen:
* Mindestens zwei modellierte tagspeicher Orte
* Ein "Kalibrierungs Raum", der in der Szene das übergeordnete Element der Tags ist
* Kamera Funktions Bezeichner
* Das Verhalten, bei dem der Kalibrierungsbereich verschoben wird, um die modellierten Tags mit den Echt Zeit Tags auszurichten (es ist vorsichtig, den übergeordneten Bereich und nicht die modellierten Marker selbst zu verschieben, weil eine andere Verbindung relativ zu diesen Tags ist).

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>Mithilfe von LEDs oder anderen Erkennungs Bibliotheken nachverfolgen oder identifizieren Sie in der Praxis markierte Objekte/Gesichter in der Praxis

Beispiele:
* Industrieroboter mit LEDs (oder QR-Codes zum langsameren Verschieben von Objekten)
* Identifizieren und erkennen von Objekten im Raum
* Personen im Raum identifizieren und erkennen (z. b. Holographic-Kontaktkarten über Flächen platzieren)

## <a name="see-also"></a>Weitere Informationen:
* [Beispiel für eine abrechenbare Kamera](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
* [Ausrichtbare Kamera in Unity](locatable-camera-in-unity.md)
* [Mixed Reality-Aufnahme](mixed-reality-capture.md)
* [Mixed Reality-Aufnahme für Entwickler](mixed-reality-capture-for-developers.md)
* [Einführung in Media Capture](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
* [Beispiel für die holografische Gesichts Verfolgung](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
