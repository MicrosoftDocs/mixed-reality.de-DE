---
title: Gebietsschemabezogene Kamera
description: Allgemeine Informationen über die frontkamera HoloLens, wie es funktioniert und die Profile und Lösungen, die Entwicklern zur Verfügung.
author: cdedmonds
ms.author: wguyman, cdedmonds
ms.date: 06/12/2019
ms.topic: article
keywords: Kamera, Hololens, Farbe Kamera, mit Internetzugriff, Hololens, 2, cv, Computer Vision, fiducial Front, Marker, QR-Code, qr, Foto, video
ms.openlocfilehash: b80e201723f8f499a6d35008b9d308f93b925b1c
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694537"
---
# <a name="locatable-camera"></a>Gebietsschemabezogene Kamera

HoloLens enthält, eine Welt gerichteten Kamera, die auf der Vorderseite des Geräts, das kann apps finden Sie unter der Benutzer bereitgestellt wird. Entwickler haben Zugriff auf und Kontrolle der Kamera, genauso wie für die Color-Kameras auf Smartphones, tragbare Geräte und Desktops. Die gleichen universelle Windows [medienaufzeichnung](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) und Windows Media Foundation-APIs, die an mobile Geräte und Desktops arbeiten HoloLens. Unity [hat auch diese Windows-APIs umschlossen](locatable-camera-in-unity.md) abstrahieren einfache Verwendung der Kamera auf HoloLens für Aufgaben wie dauert regulären Fotos und Videos (mit oder ohne Hologramme), und suchen die Position der Kamera in und Perspektive auf die die Szene.

## <a name="device-camera-information"></a>Kamera-Geräteinformationen

### <a name="hololens-first-generation"></a>HoloLens (löschbaren)

* Feste Fokus Foto/Video (PV) Kamera mit weißen automatischen Lastenausgleich, automatische Offenlegung und vollständigen Image-Verarbeitungspipeline.
* Whitepaper leuchtet Datenschutz mit Internetzugriff der ganzen Welt, wenn die Kamera aktiv ist.
* Die Kamera unterstützt die folgenden Modi (alle Modi sind Seitenverhältnis 16:9) auf 30, 24, 20, 15 und 5 f/s:

  |  Video  |  Vorschau  |  Weiterhin  |  Horizontale Sichtfeld (H-Blickfeld) |  Empfohlene Verwendung | 
  |----------|----------|----------|----------|----------|
  |  1280x720 |  1280x720 |  1280x720 |  45deg  |  Mithilfe von videostabilisierung (Standardmodus) | 
  |  Nicht zutreffend |  Nicht zutreffend |  2048x1152 |  67deg |  Standbild der höchsten Auflösung | 
  |  1408x792 |  1408x792 |  1408x792 |  48deg |  Overscan (Auffüllung)-Lösung vor der videostabilisierung | 
  |  1344x756 |  1344x756 |  1344x756 |  67deg |  Große Blickfeld Videomodus mit overscan | 
  |  896x504 |  896x504 |  896x504 |  48deg |  Energieeffiziente / -Modus mit niedriger Auflösung für Image Verarbeitungsaufgaben. | 

### <a name="hololens-2"></a>HoloLens 2

* Autofokus Foto/Video (PV) Kamera mit weißen automatischen Lastenausgleich, automatische Offenlegung und vollständigen Image-Verarbeitungspipeline.
* Whitepaper leuchtet Datenschutz mit Internetzugriff der ganzen Welt, wenn die Kamera aktiv ist.
* HoloLens-2 unterstützt Profile für andere Kamera. Erfahren Sie, wie Sie [ermitteln, und wählen Sie die Kamera Funktionen](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/camera-profiles).
* Die Kamera unterstützt die folgenden Profile und Lösungen, die (alle video Modi sind Seitenverhältnis 16:9):
  
  | Profil                                         | Video     | Vorschau   | Weiterhin     | Frameraten | Horizontale Sichtfeld (H-Blickfeld) | Empfohlene Verwendung                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | Ältere, BalancedVideoAndPhoto 0, 100             | 2272x1278 | 2272x1278 |           | 15,30       | 64.69                            | Videoaufzeichnung von hoher Qualität                |
  | Ältere, BalancedVideoAndPhoto 0, 100             | 896x504   | 896x504   |           | 15,30       | 64.69                            | Vorschau des Datenstroms für hochwertige Fotoaufnahmen |
  | Ältere, BalancedVideoAndPhoto 0, 100             |           |           | 3904x2196 |             | 64.69                            | Hohe Qualität Fotoaufnahmen                  |
  | BalancedVideoAndPhoto,120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15,30       | 64.69                            | Langer Dauer Szenarien                     |
  | BalancedVideoAndPhoto,120                       | 1504x846  | 1504x846  |           | 15,30       | 64.69                            | Langer Dauer Szenarien                     |
  | VideoConferencing,100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15,30,60    | 64.69                            | Videokonferenzen, langen-Szenarien |
  | Videokonferenzen, 100                           | 1504x846  | 1504x846  |           | 5,15,30,60  | 64.69                            | Videokonferenzen, langen-Szenarien |
  | Videokonferenzen, 100 BalancedVideoAndPhoto, 120 | 1920x1080 | 1920x1080 | 1920x1080 | 15,30       | 64.69                            | Videokonferenzen, langen-Szenarien |
  | Videokonferenzen, 100 BalancedVideoAndPhoto, 120 | 1280x720  | 1280x720  | 1280x720  | 15,30       | 64.69                            | Videokonferenzen, langen-Szenarien |
  | Videokonferenzen, 100 BalancedVideoAndPhoto, 120 | 1128x636  |           |           | 15,30       | 64.69                            | Videokonferenzen, langen-Szenarien |
  | Videokonferenzen, 100 BalancedVideoAndPhoto, 120 | 960 x 540   |           |           | 15,30       | 64.69                            | Videokonferenzen, langen-Szenarien |
  | Videokonferenzen, 100 BalancedVideoAndPhoto, 120 | 760x428   |           |           | 15,30       | 64.69                            | Videokonferenzen, langen-Szenarien |
  | Videokonferenzen, 100 BalancedVideoAndPhoto, 120 | 640x360   |           |           | 15,30       | 64.69                            | Videokonferenzen, langen-Szenarien |
  | Videokonferenzen, 100 BalancedVideoAndPhoto, 120 | 500x282   |           |           | 15,30       | 64.69                            | Videokonferenzen, langen-Szenarien |
  | Videokonferenzen, 100 BalancedVideoAndPhoto, 120 | 424x240   |           |           | 15,30       | 64.69                            | Videokonferenzen, langen-Szenarien |

>[!NOTE]
>Kunden profitieren [mixed Reality-Erfassung](mixed-reality-capture.md) zu Videos und Fotos Ihrer-App, z. Hologramme und videostabilisierung b.
>
>Als Entwickler werden beachtet, die Sie berücksichtigen sollten, wenn Ihre app zu erstellen, wenn gewünscht, so gut wie möglich zu suchen, wenn ein Kunde Inhalte erfasst. Sie können auch aktivieren (mixed Reality-Erfassung aus direkt in Ihrer app und anpassen). Weitere Informationen zu [mixed Reality-Erfassung für Entwickler](mixed-reality-capture-for-developers.md).

## <a name="locating-the-device-camera-in-the-world"></a>Suchen die Kamera des Geräts in der ganzen Welt

Wenn HoloLens Fotos und Videos verweist, enthalten die aufgezeichneten Frames die Position der Kamera in der ganzen Welt als auch die codelens-Modell der Kamera. Dadurch können Anwendungen, Grund, über die Position der Kamera in der realen Welt ergänzte imaging-Szenarien. Entwickler können ihre eigenen Szenarien, die mit ihren bevorzugten bildverarbeitung oder einen benutzerdefinierten Computer Vision Bibliotheken kreativ zurücksetzen.

"Kamera" an anderer Stelle im HoloLens Dokumentation bezieht sich möglicherweise auf die "virtuelle Spiel Kamera" (die Frustums der app rendert). Es sei denn, die andernfalls gekennzeichnet ist, bezieht sich "Kamera" auf dieser Seite auf der realen Welt RGB-Farbe Kamera ein.

Die Details auf dieser Seite Cover mithilfe der [MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference) Klasse, aber es gibt auch APIs zum Pull-Kamera systeminterne Funktionen und Standorten mithilfe von [Media Foundation Attribute](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx). Finden Sie in der [Holographic Gesicht Beispiel für den Überwachungsprofil](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) für Weitere Informationen.

### <a name="images-with-coordinate-systems"></a>Images mit Koordinatensysteme

Jedes Bild-Frame (, ob Fotos oder Videos) umfasst eine [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) Stamm der Kamera zum Zeitpunkt der Erfassung, die mithilfe von zugegriffen werden kann die [Koordinatensystem](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) Eigenschaft Ihre [MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference). Darüber hinaus jeder Frame enthält eine Beschreibung des Modells Linse Kamera, die im befinden die [CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) Eigenschaft. Zusammen definieren diese Transformationen für jedes Pixel ein Strahl im 3D-Raum, die den Pfad repräsentiert, die von der Photonen, die das Pixel erzeugt. Diese Strahlung können auf andere Inhalte in der app verknüpft werden, durch die Transformation von Koordinatensystem des Frames abrufen, auf einige andere Koordinatensystem (z. B. aus einem [feststehende Verweisrahmen](coordinate-systems.md#stationary-frame-of-reference)). Zusammenfassend lässt sich sagen, bietet der einzelnen Bild-Frame Folgendes:
* Die Pixeldaten (im Format der RGB-/ NV12/JPEG/usw.)
* Ein [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) aus dem Speicherort der Erfassung
* Ein [CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) Klasse, die den Fokus Modus der Kamera enthält.

### <a name="camera-to-application-specified-coordinate-system"></a>Kamera Koordinatensystem anwendungsspezifische

Um auf Ihre Anwendung/globales Koordinatensystem aus dem 'CameraIntrinsics' und "CameraCoordinateSystem" zu wechseln, benötigen Sie Folgendes:

[Gebietsschemabezogene Kamera in Unity](locatable-camera-in-unity.md): CameraToWorldMatrix wird automatisch von PhotoCaptureFrame-Klasse bereitgestellt, (sodass Sie nicht über die Transformationen CameraCoordinateSystem machen müssen).

[Gebietsschemabezogene Kamera in DirectX](locatable-camera-in-directx.md): Zeigt die recht einfache Möglichkeit zum Abfragen von der Transformation zwischen Koordinatensystem der Kamera und Ihrer eigenen Anwendung Coordinate system(s).

### <a name="distortion-error"></a>Verzerrung-Fehler

Auf HoloLens sind die Videos und weiterhin Image Streams unverfälschten in das System die Image-Verarbeitungspipeline, bevor die Frames der Anwendung zur Verfügung gestellt werden (die Vorschau des Datenstroms enthält die ursprünglichen verzerrt Frames). Da nur die CameraIntrinsics zur Verfügung gestellt werden, Anwendungen müssen davon ausgehen Bild-Frames stellen eine perfekte Pinhole Kamera, die Undistortion funktionieren jedoch in der Image-Prozessor können weiterhin lassen Fehler von bis zu 10 Pixel für HoloLens (löschbaren) Wenn die CameraIntrinsics in den Frame-Metadaten verwenden zu können. In vielen Fällen – dieser Fehler wird spielt keine Rolle, aber wenn Sie Hologramme, die reale Welt Poster/Marker, z. B. ausrichten sind und Sie feststellen, dass eine < 10px offset (etwa 11mm für Hologramme positioniert-Zähler sofort 2) dieser Verzerrung Fehler könnte die Ursache sein. 

## <a name="locatable-camera-usage-scenarios"></a>Szenarien für die Verwendung gebietsschemabezogene Kamera

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>Anzeigen eines Fotos oder Videos in der ganzen Welt, in dem er erfasst wurde

Die Kamera des Geräts Frames verfügen über eine "Kamera, World"-Transformation, die verwendet werden kann, um anzuzeigen, genau, in dem das Gerät wurde bei der das Image erstellt wurde. Zum Beispiel könnten Sie positionieren ein kleines holographic Symbol an dieser Stelle (CameraToWorld.MultiplyPoint(Vector3.zero)) und sogar zeichnen einen kleinen Pfeil in die Richtung von die Kamera (CameraToWorld.MultiplyVector(Vector3.forward)). konfrontiert wurde

### <a name="tag--pattern--poster--object-tracking"></a>Tag / Pattern / Poster / Objektverfolgung

Viele mixed Reality-Anwendungen verwenden eine erkennbare Bild oder ein visual Muster zum Erstellen eines nachverfolgbare Punkts im Bereich. Dies wird dann zum Rendern verwendet Objekte relativ zum, die zeigen, oder erstellen Sie einen bekannten Speicherort. Einige Verwendungsmöglichkeiten für HoloLens gehören, suchen, die ein Objekt der realen Welt mit Fiducials (z. B. eine TV-Monitor mit einem QR-Code) gekennzeichnet, platzieren Hologramme über Fiducials und visuell Kopplung mit nicht-HoloLens-Geräten wie Tablets, die für die Kommunikation mit HoloLens über eingerichtet haben Wi-Fi.

Um ein visual-Muster erkennen, und legen Sie das Objekt im Raum, Anwendungen, benötigen Sie Folgendes:
1. Ein Bild Muster Anerkennung Toolkit, z. B. QR-Code "," AR-Tags "," Gesicht Finder "," Kreis-nachverfolgungsmodule, OCR usw.
2. Bild-Frames zur Laufzeit sammeln und diese an die Anerkennung Ebene übergeben
3. Unproject auftraten Bild wieder in die Welt Positionen und wahrscheinlich Welt Strahlung an. Unter
4. Positionieren Sie Ihre virtuellen Modelle über diese Standorte weltweit

Einige wichtige Image Verarbeitung Links:
* [OpenCV](http://opencv.org/)
* [Qr-Tags](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](http://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

Halten eine interaktive Anwendung Framerate ist wichtig, insbesondere beim Umgang mit Algorithmen für die Erkennung langer Image. Aus diesem Grund verwenden wir im Allgemeinen im folgenden Format ein:
1. Hauptthread: verwaltet das Kameraobjekt
2. Hauptthread: neue Anforderungen-Frames (Async)
3. Hauptthread: Übergeben von neuen Frames zum Nachverfolgen von Threads
4. Überwachung-Thread: verarbeitet, Bild, um die wichtigsten Punkte zu sammeln
5. Hauptthread: verschiebt virtuelle Modell entsprechend finden Sie wichtige Punkte
6. Hauptthread: Wiederholen Sie Schritt 2

Einige Images-Marker-Systeme bieten nur einen einzelnen Pixels-Speicherort (andere bieten die vollständigen Transformation in diesem Fall in diesem Abschnitt nicht benötigt wird), das ist gleichbedeutend mit einem Strahl von möglichen Speicherorten. Rufen Sie an zentraler Stelle 3d können dann mehrere Strahlung nutzen und finden das endgültige Ergebnis, indem deren ungefähre Schnittmenge. Zu diesem Zweck müssen Sie Folgendes ausführen:
1. Abrufen einer Schleife, die jetzt mehrere Kamera Abbilder erfassen
2. Hier finden Sie das entsprechende Feature Punkte und deren Strahlung world
3. Wenn Sie ein Wörterbuch von Features, mit mehreren Welt Strahlung, haben können Sie den folgenden Code, um für die Schnittmenge dieser Strahlung zu lösen:

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

Wenn mindestens zwei überwachte Tag-Standorten, können Sie eine modelled Szene entsprechend das aktuellen Benutzer-Szenario positionieren. Wenn Sie Schwerkraft wird davon ausgegangen, müssen Sie drei Tags stellen dafür. In vielen Fällen, die wir verwenden ein einfaches Farbschema, in dem weiße Kugeln in Echtzeit darstellen, nachverfolgt Tag-Standorte, und blaue Kugeln modelliert Tag-Orte darstellen, dadurch kann der Benutzer an der die Ausrichtung Qualität visuell zu messen. Es wird davon ausgegangen folgende Setup alle unsere Anwendungen:
* Mindestens zwei modelliert Tag-Standorten
* Eine "Kalibrierung Raum" auf, das in der Szene das übergeordnete Element der tags
* Bezeichner der Kamera-Funktion
* Verhalten, das verschiebt Bereich Kalibrierung der Anpassung an die modelled Tags mit den Tags in Echtzeit (wir sind darauf achten, die den übergeordneten Bereich, nicht die modelled Marker selbst zu verschieben, da andere Connect Positionen bezogen auf sie ist).

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

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>Nachverfolgen oder stationär markiert zu identifizieren oder beweglichen reale Objekte/Gesichtern, LEDs oder andere Bibliotheken Erkennung

Beispiele:
* Industrielle Roboter mit LEDs (oder QR-Codes für das Verschieben von langsamer Objekte)
* Identifizierung und die Erkennung von Objekten im Raum
* Identifizierung und die Erkennung von Personen im Raum (z. B. direkte holographic Kontaktkarten in Gesichtern)

## <a name="see-also"></a>Siehe auch
* [Ausrichtbare Kamera in DirectX](locatable-camera-in-directx.md)
* [Ausrichtbare Kamera in Unity](locatable-camera-in-unity.md)
* [Mixed Reality-Aufnahme](mixed-reality-capture.md)
* [Mixed Reality-Aufnahme für Entwickler](mixed-reality-capture-for-developers.md)
* [Medienaufzeichnung Einführung](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
* [Beispiel zur nachverfolgung holographic gesichtserkennung](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
