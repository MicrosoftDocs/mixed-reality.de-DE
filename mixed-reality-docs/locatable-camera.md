---
title: Gebietsschemabezogene Kamera
description: Allgemeine Informationen zu den mit Internetzugriff HoloLens frontkamera.
author: wguyman
ms.author: wguyman
ms.date: 02/24/2019
ms.topic: article
keywords: Kamera, Hololens, Farbe Kamera, Front-facing
ms.openlocfilehash: ffcd6faf15dd8556db393237d468a3cdf60e4bdb
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596324"
---
# <a name="locatable-camera"></a>Gebietsschemabezogene Kamera

HoloLens enthält, eine Welt gerichteten Kamera, die auf der Vorderseite des Geräts, das kann apps finden Sie unter der Benutzer bereitgestellt wird. Entwickler haben Zugriff auf und Kontrolle der Kamera, genauso wie für die Color-Kameras auf Smartphones, tragbare Geräte und Desktops. Die gleichen universelle Windows [medienaufzeichnung](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) und Windows Media Foundation-APIs, die an mobile Geräte und Desktops arbeiten HoloLens. Unity [hat auch diese Windows-APIs umschlossen](locatable-camera-in-unity.md) abstrahieren einfache Verwendung der Kamera auf HoloLens für Aufgaben wie dauert regulären Fotos und Videos (mit oder ohne Hologramme), und suchen die Position der Kamera in und Perspektive auf die die Szene.

## <a name="device-camera-information"></a>Kamera-Geräteinformationen

### <a name="hololens-first-generation"></a>HoloLens (löschbaren)

* Feste Fokus Foto / (PV) Videokamera, weiß automatischen Lastenausgleich, automatische Offenlegung und vollständigen Verarbeitung pipe
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

* Autofokus Foto/Video (PV) Kamera mit weißen automatischen Lastenausgleich, automatische Offenlegung und vollständigen Verarbeitung pipe
* Whitepaper leuchtet Datenschutz mit Internetzugriff der ganzen Welt, wenn die Kamera aktiv ist.
* Die Kamera unterstützt die folgenden Modi (alle video Modi sind Seitenverhältnis 16:9):

  >[!NOTE]
  >Diese Modi unterliegen noch Änderungen, die vor der allgemeinen Verfügbarkeit von HoloLens 2.

  |  Video  |  Vorschau  |  Weiterhin  |  Frameraten  |  Horizontale Sichtfeld (H-Blickfeld) |  Empfohlene Verwendung | 
  |----------|----------|----------|----------|----------|----------|
  |  1920x1080 |  1920x1080 |  Nicht zutreffend |  30, 15 f/s  |  54deg  |  Mithilfe von videostabilisierung (Standardmodus) | 
  |  Nicht zutreffend |  Nicht zutreffend |  3904X2196 |  Nicht zutreffend  |  64deg |  Standbild der höchsten Auflösung | 
  |  2272x1278 |  2272x1278 |  Nicht zutreffend |  30, 15 f/s  |  64deg |  Overscan (Auffüllung)-Lösung vor der videostabilisierung | 
  |  1952x1100 |  1952x1100 |  1952x1100  |  30, 15 f/s  |  64deg |  Hoher Qualität | 
  |  1280x720 |  1280x720 |  Nicht zutreffend |  30, 15, 5 f/s  |  64deg |  Niedrige Power bzw. Beschlusses Modus für das streaming und Aufgaben der bildverarbeitung | 

## <a name="locating-the-device-camera-in-the-world"></a>Suchen die Kamera des Geräts in der ganzen Welt

Wenn HoloLens Fotos und Videos verweist, enthalten die aufgezeichneten Frames die Position der Kamera in der ganzen Welt als auch die perspektivische Projektion der Kamera. Dadurch können Anwendungen, Grund, über die Position der Kamera in der realen Welt ergänzte imaging-Szenarien. Entwickler können ihre eigenen Szenarien, die mit ihren bevorzugten bildverarbeitung oder einen benutzerdefinierten Computer Vision Bibliotheken kreativ zurücksetzen.

"Kamera" an anderer Stelle im HoloLens Dokumentation bezieht sich möglicherweise auf die "virtuelle Spiel Kamera" (die Frustums der app rendert). Es sei denn, die andernfalls gekennzeichnet ist, bezieht sich "Kamera" auf dieser Seite auf der realen Welt RGB-Farbe Kamera ein.

Die Details auf dieser Seite Abdeckung [Media Foundation Attribute](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx), es gibt jedoch auch APIs, um die Kamera systeminternen Funktionen mit pull [WinRT-APIs](https://msdn.microsoft.com/library/windows/apps/windows.media.devices.core.cameraintrinsics).  

### <a name="images-with-coordinate-systems"></a>Images mit Koordinatensysteme

Jedes Bild-Frame (ob Fotos oder Videos) enthält, sowie zwei wichtige Transformationen in einem Koordinatensystem. Die "View" wandeln Sie Zuordnungen aus der angegebenen Koordinatensystem bis zur Kamera und der "Projection" wird von der Kamera Pixel im Bild. Zusammen definieren diese Transformationen für jedes Pixel ein Strahl im 3D-Raum, die den Pfad repräsentiert, die von der Photonen, die das Pixel erzeugt. Diese Strahlung können auf andere Inhalte in der app verknüpft werden, durch die Transformation von Koordinatensystem des Frames abrufen, auf einige andere Koordinatensystem (z. B. aus einem [feststehende Verweisrahmen](coordinate-systems.md#stationary-frame-of-reference)). Zusammenfassend lässt sich sagen, bietet der einzelnen Bild-Frame Folgendes:
* Die Pixeldaten (im Format der RGB-/ NV12/JPEG/usw.)
* 3 Teile der Metadaten (gespeichert als [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)), die jeden Frame "auffindbaren" machen:

|  Attributname  |  Typ  |  GUID  |  Beschreibung | 
|----------|----------|----------|----------|
|  MFSampleExtension_Spatial_CameraCoordinateSystem  |  IUnknown ([SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx))  |  {9D13C82F-2199-4E67-91CD-D1A4181F2534}  |  Speichert die [Koordinatensystem](coordinate-systems-in-directx.md) des aufgezeichneten Frames | 
|  MFSampleExtension_Spatial_CameraViewTransform  |  Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))  |  {4E251FA4-830F-4770-859A-4B8D99AA809B}  |  Speichert der Kamera systemexterne Transformation im Koordinatensystem | 
|  MFSampleExtension_Spatial_CameraProjectionTransform  |  Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))  |  {47F9FCB5-2A02-4F26-A477-792FDF95886A}  |  Speichert die Projektion Transformation der Kamera | 

Die Transformation für die Projektion stellt die inhärenten Eigenschaften (als zentraler Länge Mittelpunkt der Projektion, neigen) den Fokus auf ein Image-Ebene, die von-1 bis + 1, in der X- und Y-Achse erweitert zugeordnet.

```
Matrix4x4 format          Terms
   m11 m12 m13 m14      fx    0   0   0
   m21 m22 m23 m24     skew  fy   0   0
   m31 m32 m33 m34      cx   cy   A  -1
   m41 m42 m43 m44       0    0   B   0
```

Verschiedene Anwendungen müssen unterschiedliche Koordinatensysteme. Hier ist eine Übersicht über die Vorgehensweise zum Suchen eines Pixels Kamera für eine einzelne Anwendung:

![Transformationen angewendet werden, um die Kamera Koordinatensysteme](images/pvcameratransform5-500px.png)

### <a name="camera-to-application-specified-coordinate-system"></a>Kamera Koordinatensystem anwendungsspezifische

Um auf Ihre Anwendung/globales Koordinatensystem aus dem 'CameraView' und "CameraCoordinateSystem" zu wechseln, benötigen Sie Folgendes:

[Gebietsschemabezogene Kamera in Unity](locatable-camera-in-unity.md): CameraToWorldMatrix wird automatisch von PhotoCaptureFrame-Klasse bereitgestellt, (sodass Sie nicht über die Transformationen CameraCoordinateSystem machen müssen).

[Gebietsschemabezogene Kamera in DirectX](locatable-camera-in-directx.md): Zeigt die recht einfache Möglichkeit zum Abfragen von der Transformation zwischen Koordinatensystem der Kamera und Ihrer eigenen Anwendung Coordinate system(s).

### <a name="application-specified-coordinate-system-to-pixel-coordinates"></a>Koordinatensystem in Pixelkoordinaten anwendungsspezifische

Angenommen, Sie verwenden möchten, suchen oder an einer bestimmten 3d Position auf ein kamerabild Zeichnen:

Die Ansichts- und Projektionstransformation Transformationen, während die beiden Matrizen 4 x 4 müssen etwas anders verwendet werden. Nämlich nach dem Ausführen der Projektion an, eine würde "normalisieren, indem Sie w', dieser zusätzliche Schritt in der Projektion simuliert, wie mehrere 3d Speicherorte als 2d denselben Speicherort auf einem Bildschirm ergeben können (d. h. wird alles an einem bestimmten Strahl auf demselben Pixel angezeigt). Daher wichtige Punkte (im shadercode):

```
// Usual 3d math:
 float4x4 WorldToCamera = inverse( CameraToWorld );
 float4 CameraSpacePos = mul( WorldToCamera, float4( WorldSpacePos.xyz, 1 ) ); // use 1 as the W component
 // Projection math:
 float4 ImagePosUnnormalized = mul( CameraProjection, float4( CameraSpacePos.xyz, 1 ) ); // use 1 as the W component
 float2 ImagePosProjected = ImagePosUnnormalized.xy / ImagePosUnnormalized.w; // normalize by W, gives -1 to 1 space
 float2 ImagePosZeroToOne = ( ImagePosProjected * 0.5 ) + float2( 0.5, 0.5 ); // good for GPU textures
 int2 PixelPos = int2( ImagePosZeroToOne.x * ImageWidth, ( 1 - ImagePosZeroToOne.y ) * ImageHeight ); // good for CPU textures
```

### <a name="pixel-to-application-specified-coordinate-system"></a>Pixel, um das Koordinatensystem anwendungsspezifische

Vom Pixel ist globale Koordinaten etwas komplizierter:

```
float2 ImagePosZeroToOne = float2( PixelPos.x / ImageWidth, 1.0 - (PixelPos.y / ImageHeight ) );
 float2 ImagePosProjected = ( ( ImagePosZeroToOne * 2.0 ) - float2(1,1) ); // -1 to 1 space
 float3 CameraSpacePos = UnProjectVector( Projection, float3( ImagePosProjected, 1) );
 float3 WorldSpaceRayPoint1 = mul( CameraToWorld, float4(0,0,0,1) ); // camera location in world space
 float3 WorldSpaceRayPoint2 = mul( CameraToWorld, CameraSpacePos ); // ray point in world space
```

Wird definiert, in denen UnProject als:

```
public static Vector3 UnProjectVector(Matrix4x4 proj, Vector3 to)
 {
   Vector3 from = new Vector3(0, 0, 0);
   var axsX = proj.GetRow(0);
   var axsY = proj.GetRow(1);
   var axsZ = proj.GetRow(2);
   from.z = to.z / axsZ.z;
   from.y = (to.y - (from.z * axsY.z)) / axsY.y;
   from.x = (to.x - (from.z * axsX.z)) / axsX.x;
   return from;
 }
```

Um die tatsächlichen World-Position eines Punkts zu suchen, Sie benötigen entweder: zwei Welt Strahlen und suchen Sie nach ihrer Schnittmenge oder eine bekannte Größe der Punkte.

### <a name="distortion-error"></a>Verzerrung-Fehler

Auf HoloLens sind die Videos und weiterhin Image Streams unverfälschten in das System die Image-Verarbeitungspipeline, bevor die Frames der Anwendung zur Verfügung gestellt werden (die Vorschau des Datenstroms enthält die ursprünglichen verzerrt Frames). Da nur die Projektionsmatrix verfügbar gemacht werden, Anwendungen müssen davon ausgehen Bild-Frames stellen eine perfekte Pinhole Kamera, die Undistortion funktionieren jedoch in der Image-Prozessor möglicherweise einen Fehler von bis zu 10 Pixel weiterhin lassen, wenn die Projektionsmatrix in Verwendung die Frame-Metadaten. In vielen Fällen – dieser Fehler wird spielt keine Rolle, aber wenn Sie Hologramme, die reale Welt Poster/Marker, z. B. ausrichten sind und Sie feststellen, dass eine < 10px offset (etwa 11mm für Hologramme positioniert-Zähler sofort 2) dieser Verzerrung Fehler könnte die Ursache sein.

## <a name="locatable-camera-usage-scenarios"></a>Szenarien für die Verwendung gebietsschemabezogene Kamera

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>Anzeigen eines Fotos oder Videos in der ganzen Welt, in dem er erfasst wurde

Die Kamera des Geräts Frames verfügen über eine "Kamera, World"-Transformation, die verwendet werden kann, um anzuzeigen, genau, in dem das Gerät wurde bei der das Image erstellt wurde. Zum Beispiel könnten Sie positionieren ein kleines holographic Symbol an dieser Stelle (CameraToWorld.MultiplyPoint(Vector3.zero)) und sogar zeichnen einen kleinen Pfeil in die Richtung von die Kamera (CameraToWorld.MultiplyVector(Vector3.forward)). konfrontiert wurde

### <a name="painting-the-world-using-a-camera-shader"></a>Zeichnen der Welt über eine Kamera-shader

In diesem Abschnitt erstellen wir ein Material "Shader", Farben, die abhängig von die ganzen Welt, in denen sie in der Ansicht für eine Kamera des Geräts angezeigt wurde. Wir lassen jetzt effektiv ist, dass jeder Vertex, deren Speicherort relativ zur Kamera herausfinden wird, und klicken Sie dann jedes Pixel, die die Projektionsmatrix Abbildung verwendet werden Out welches Texel image zugeordnet ist. Schließlich und optional werden wir die Ecken des Bilds, das es mehr als ein Traum-ähnliche Arbeitsspeicher angezeigt wird eingeblendet:

```
// In the vertex shader:
 float4 worldSpace = mul( ObjectToWorld, float4( vertexPos.xyz, 1));
 float4 cameraSpace = mul( CameraWorldToLocal, float4(worldSpace.xyz, 1));

 // In the pixel shader:
 float4 unprojectedTex = mul( CameraProjection, float4( cameraSpace .xyz, 1));
 float2 projectedTex = (unprojectedTex.xy / unprojectedTex.w);
 float2 unitTexcoord = ((projectedTex * 0.5) + float4(0.5, 0.5, 0, 0));
 float4 cameraTextureColor = tex2D(_CameraTex, unitTexcoord);
 // Fade out edges for better look:
 float pctInView = saturate((1.0 - length(projectedTex.xy)) * 3.0);
 float4 finalColor = float4( cameraTextureColor.rgb, pctInView );
```

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
2. Suchen der [verknüpften zeigt für Feature](#pixel-to-application-specified-coordinate-system), und deren Strahlung World
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

### <a name="render-holograms-from-the-cameras-position"></a>Rendern von Hologramme aus die Position der Kamera

Hinweis: Wenn Sie versuchen, Ihre eigenen erstellen [Mixed Reality-Erfassung (MRC)](mixed-reality-capture.md), die Hologramme mit der Kamera-Datenstrom kombiniert, können Sie die [MRC Effekte](mixed-reality-capture-for-developers.md) oder aktivieren Sie die Eigenschaft ShowHolograms in [ Gebietsschemabezogene Kamera in Unity](locatable-camera-in-unity.md).

Wenn Sie eine besondere Render direkt auf den RGB-Kamera-Datenstrom möchten, ist es möglich, Hologramme im Raum aus die Position der Kamera mit einer videofeed synchron zu rendern, um eine benutzerdefinierte – Hologramm Aufzeichnung/live-Vorschau bereitzustellen.

In Skype dazu wir der remote-Client anzeigen, was die HoloLens-Benutzers angezeigt wird, und für die Interaktion mit der gleichen Hologramme ermöglichen. Vor dem Senden über die einzelnen Videoframes, über den Dienst Skype, nehmen wir die entsprechenden Kamera-Daten des Frames. Wir dann Verpacken der Kamera systemexterne und systeminterne-Metadaten mit des Videoframes und senden Sie sie über die Skype-Dienst.

Auf der Empfängerseite haben mithilfe von Unity wir bereits alle die Hologramme im des Benutzers, der die HoloLens-Raum mit dem gleichen Koordinatensystem synchronisiert. Dadurch können wir der Kamera-systemexterne-Metadaten verwenden, um die Unity-Kamera in den genauen Ort der Welt (in Bezug auf die restlichen den Hologramme) zu platzieren, das der Benutzer HoloLens ständigen wurde, wenn sich dieses video Frame erfasst wurde, und verwenden die Kamera systeminterne Informationen Stellen Sie sicher, dass die Sicht identisch ist.

Nachdem wir die Kamera ordnungsgemäß eingerichtet haben, kombiniert welche die Kamera auf den Frame angezeigt, die wir von Skype wird erhalten, erstellen eine mixed Reality-Ansicht der HoloLens der Benutzer sieht mit Graphics.Blit Hologramme.

```cs
private void OnFrameReceived(Texture frameTexture, Vector3 cameraPosition, Quaternion cameraRotation, Matrix4x4 cameraProjectionMatrix)
{
    //set material that will be blitted onto the RenderTexture
    this.compositeMaterial.SetTexture(CompositeRenderer.CameraTextureMaterialProperty, frameTexture);
    //set the camera to be that of the HoloLens's device camera
    this.Camera.transform.position = cameraPosition;
    this.Camera.transform.rotation = cameraRotation;
    this.Camera.projectionMatrix = cameraProjectionMatrix;
    //trigger the Graphics's Blit now that the frame and camera are set up
    this.TextureReady = false;
}
private void OnRenderImage(RenderTexture source, RenderTexture destination)
{
    if (!this.TextureReady)
    {
        Graphics.Blit(source, destination, this.compositeMaterial);
        this.TextureReady = true;
    }
}
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>Nachverfolgen oder stationär markiert zu identifizieren oder beweglichen reale Objekte/Gesichtern, LEDs oder andere Bibliotheken Erkennung

Beispiele:
* Industrielle Roboter mit LEDs (oder QR-Codes für das Verschieben von langsamer Objekte)
* Identifizierung und die Erkennung von Objekten im Raum
* Identifizierung und die Erkennung von Personen im Raum (z. B. direkte holographic Kontaktkarten in Gesichtern)

## <a name="see-also"></a>Siehe auch
* [Gebietsschemabezogene Kamera in DirectX](locatable-camera-in-directx.md)
* [Gebietsschemabezogene Kamera in Unity](locatable-camera-in-unity.md)
* [Mixed Reality-Erfassung](mixed-reality-capture.md)
* [Mixed Reality-Erfassung für Entwickler](mixed-reality-capture-for-developers.md)
* [Medienaufzeichnung Einführung](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
