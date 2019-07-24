---
title: Einsetzbare Kamera in Unity
description: Hololens der verwendbaren Kamera Verwendung in Unity.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: Foto, Video, hololens, Kamera, Unity, loalisierbar
ms.openlocfilehash: f0183400f55b1c6663a9a20ab4992befe5ad0718
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515433"
---
# <a name="locatable-camera-in-unity"></a>Einsetzbare Kamera in Unity

## <a name="enabling-the-capability-for-photo-video-camera"></a>Aktivieren der Funktion für Foto-Video Kamera

Die "Webcam"-Funktion muss für eine APP deklariert werden, um die [Kamera](locatable-camera.md)zu verwenden.
1. Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zur Seite "> Projekteinstellungen bearbeiten > Player" navigieren.
2. Klicken Sie auf die Registerkarte "Windows Store".
3. Überprüfen Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die Funktionen für **Webcam** und **Mikrofon** .

Nur ein einzelner Vorgang kann gleichzeitig mit der Kamera erfolgen. Um zu ermitteln, in welchem Modus (Foto, Video oder None) sich die Kamera derzeit befindet, können Sie unityengine. XR. WSA. Webcam. Mode überprüfen.

## <a name="photo-capture"></a>Foto Erfassung

**Namespace:** *Unityengine. XR. WSA. Webcam*<br>
**Sorte** *Foto Erfassung*

Mit dem Typ *photocapture* können Sie weiterhin Fotos mit der Foto Video Kamera aufnehmen. Das allgemeine Muster für die Verwendung von *Photo Capture* für die Aufnahme eines Fotos sieht wie folgt aus:
1. Erstellen eines *photocapture* -Objekts
2. Erstellen Sie ein " *cameraparameters* "-Objekt mit den gewünschten Einstellungen.
3. Foto Modus über " *startphotomodeasync* " starten
4. Nehmen Sie das gewünschte Foto
    * optionale Mit diesem Bild interagieren
5. Foto Modus abbrechen und Ressourcen bereinigen

### <a name="common-set-up-for-photocapture"></a>Allgemeine Einrichtung für photocapture

Für alle drei Verwendungsmöglichkeiten beginnen wir mit denselben ersten drei Schritten.

Wir beginnen mit der Erstellung eines *photocapture* -Objekts.

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

Als nächstes speichern wir das Objekt, legen unsere Parameter fest und starten den Photo-Modus.

```cs
void OnPhotoCaptureCreated(PhotoCapture captureObject)
   {
       photoCaptureObject = captureObject;

       Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

       CameraParameters c = new CameraParameters();
       c.hologramOpacity = 0.0f;
       c.cameraResolutionWidth = cameraResolution.width;
       c.cameraResolutionHeight = cameraResolution.height;
       c.pixelFormat = CapturePixelFormat.BGRA32;

       captureObject.StartPhotoModeAsync(c, false, OnPhotoModeStarted);
   }
```

Am Ende verwenden wir auch denselben Bereinigungs Code, der hier vorgestellt wird.

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

Nachdem Sie diese Schritte ausgeführt haben, können Sie den Typ des zu erfassenden Fotos auswählen.

### <a name="capture-a-photo-to-a-file"></a>Fotos in einer Datei erfassen

Der einfachste Vorgang besteht darin, ein Foto direkt in einer Datei zu erfassen. Das Foto kann als jpg oder PNG gespeichert werden.

Wenn der Photo-Modus erfolgreich gestartet wurde, wird ein Foto erstellt und auf dem Datenträger gespeichert.

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format(@"CapturedImage{0}_n.jpg", Time.time);
           string filePath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

Nachdem das Foto auf der Festplatte aufgezeichnet wurde, beenden wir den Foto Modus und bereinigen dann die Objekte.

```cs
void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           Debug.Log("Saved Photo to disk!");
           photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
       }
       else
       {
           Debug.Log("Failed to save Photo to disk");
       }
   }
```

### <a name="capture-a-photo-to-a-texture2d"></a>Fotos für ein Texture2D erfassen

Beim Erfassen von Daten in einem Texture2D ähnelt der Prozess stark der Erfassung auf dem Datenträger.

Wir befolgen den oben beschriebenen Setup Vorgang.

In *onphotomodestarted*erfassen wir einen Frame im Speicher.

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           photoCaptureObject.TakePhotoAsync(OnCapturedPhotoToMemory);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

Anschließend wenden wir das Ergebnis auf eine Textur an und verwenden den oben aufgeführten allgemeinen Bereinigungs Code.

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           // Create our Texture2D for use and set the correct resolution
           Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
           // Copy the raw image data into our target texture
           photoCaptureFrame.UploadImageDataToTexture(targetTexture);
           // Do as we wish with the texture such as apply it to a material, etc.
       }
       // Clean up
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>Fotos erfassen und mit den Rohdaten Bytes interagieren

Um mit den unformatierten Bytes eines in-Memory-Frames zu interagieren, befolgen wir dieselben Setup Schritte wie oben und *onphotomodestarted* , wie bei der Erfassung eines Fotos für eine Texture2D. Der Unterschied besteht in *oncapturedphototomemory* , wo wir die Rohdaten Bytes erhalten und mit ihnen interagieren können.

In diesem Beispiel erstellen wir eine *Liste<Color>*  , die mithilfe von *setPixels ()* weiterverarbeitet oder auf eine Textur angewendet werden kann.

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           List<byte> imageBufferList = new List<byte>();
           // Copy the raw IMFMediaBuffer data into our empty byte list.
           photoCaptureFrame.CopyRawImageDataIntoBuffer(imageBufferList);

           // In this example, we captured the image using the BGRA32 format.
           // So our stride will be 4 since we have a byte for each rgba channel.
           // The raw image data will also be flipped so we access our pixel data
           // in the reverse order.
           int stride = 4;
           float denominator = 1.0f / 255.0f;
           List<Color> colorArray = new List<Color>();
           for (int i = imageBufferList.Count - 1; i >= 0; i -= stride)
           {
               float a = (int)(imageBufferList[i - 0]) * denominator;
               float r = (int)(imageBufferList[i - 1]) * denominator;
               float g = (int)(imageBufferList[i - 2]) * denominator;
               float b = (int)(imageBufferList[i - 3]) * denominator;

               colorArray.Add(new Color(r, g, b, a));
           }
           // Now we could do something with the array such as texture.SetPixels() or run image processing on the list
       }
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

## <a name="video-capture"></a>Video Erfassung

**Namespace:** *Unityengine. XR. WSA. Webcam*<br>
**Sorte** *Videocapture*

*Videocapture* funktioniert sehr ähnlich wie bei *photocapture*. Die einzigen beiden Unterschiede sind, dass Sie einen Wert für Frames pro Sekunde (fps) angeben müssen, und Sie können nur direkt auf dem Datenträger als MP4-Datei speichern. Die Schritte für die Verwendung von *Videocapture* lauten wie folgt:
1. Erstellen eines *Videocapture* -Objekts
2. Erstellen Sie ein " *cameraparameters* "-Objekt mit den gewünschten Einstellungen.
3. Starten des Video Modus über *startvideomodeasync*
4. Aufzeichnen des Videos starten
5. Aufzeichnen von Videos anhalten
6. Video Modus abbrechen und Ressourcen bereinigen

Wir beginnen mit dem Erstellen des *Videocapture* -Objekts *Videocapture m_VideoCapture = NULL;*

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

Dann richten wir die Parameter ein, die für die Aufzeichnung und den Start verwendet werden sollen.

```cs
void OnVideoCaptureCreated (VideoCapture videoCapture)
   {
       if (videoCapture != null)
       {
           m_VideoCapture = videoCapture;

           Resolution cameraResolution = VideoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           float cameraFramerate = VideoCapture.GetSupportedFrameRatesForResolution(cameraResolution).OrderByDescending((fps) => fps).First();

           CameraParameters cameraParameters = new CameraParameters();
           cameraParameters.hologramOpacity = 0.0f;
           cameraParameters.frameRate = cameraFramerate;
           cameraParameters.cameraResolutionWidth = cameraResolution.width;
           cameraParameters.cameraResolutionHeight = cameraResolution.height;
           cameraParameters.pixelFormat = CapturePixelFormat.BGRA32;

           m_VideoCapture.StartVideoModeAsync(cameraParameters,
                                               VideoCapture.AudioState.None,
                                               OnStartedVideoCaptureMode);
       }
       else
       {
           Debug.LogError("Failed to create VideoCapture Instance!");
       }
   }
```

Nachdem Sie begonnen haben, beginnen wir mit der Aufzeichnung.

```cs
void OnStartedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format("MyVideo_{0}.mp4", Time.time);
           string filepath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           m_VideoCapture.StartRecordingAsync(filepath, OnStartedRecordingVideo);
       }
   }
```

Nachdem die Aufzeichnung gestartet wurde, können Sie die Benutzeroberfläche oder das Verhalten aktualisieren, um das Beenden zu aktivieren. Hier protokollieren wir einfach

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

Zu einem späteren Zeitpunkt möchten wir die Aufzeichnung anhalten. Dies kann beispielsweise bei einem Timer oder einer Benutzereingabe vorkommen.

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

Nachdem die Aufzeichnung beendet wurde, beenden wir den Videomodus und bereinigen unsere Ressourcen.

```cs
void OnStoppedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Stopped Recording Video!");
       m_VideoCapture.StopVideoModeAsync(OnStoppedVideoCaptureMode);
   }

   void OnStoppedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       m_VideoCapture.Dispose();
       m_VideoCapture = null;
   }
```

## <a name="troubleshooting"></a>Problembehandlung
* Es sind keine Auflösungen verfügbar.
    * Stellen Sie sicher, dass die **Webcam** -Funktion in Ihrem Projekt angegeben wird.

## <a name="see-also"></a>Siehe auch
* [Ausrichtbare Kamera](locatable-camera.md)
