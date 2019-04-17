---
title: Gebietsschemabezogene Kamera in Unity
description: HoloLens auffindbaren kameragebrauch in Unity.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: Foto, Video, Hololens, Kamera, Unity, gefunden werden
ms.openlocfilehash: f0183400f55b1c6663a9a20ab4992befe5ad0718
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595115"
---
# <a name="locatable-camera-in-unity"></a>Gebietsschemabezogene Kamera in Unity

## <a name="enabling-the-capability-for-photo-video-camera"></a>Aktivieren die Funktion für die Foto-Videokamera

Die Funktion "WebCam" muss deklariert werden, für eine app für die Verwendung der [Kamera](locatable-camera.md).
1. Rufen Sie im Unity-Editor die playereinstellungen durch Navigieren zu "Bearbeiten > Projekt Einstellungen > Player"-Seite
2. Klicken Sie auf der Registerkarte "Windows Store"
3. Überprüfen Sie im Abschnitt "Einstellungen > Veröffentlichungsfunktionen" die **WebCam** und **Mikrofon** Funktionen

Nur ein einzelner Vorgang kann mit der Kamera zu einem Zeitpunkt ausgeführt. Um zu bestimmen, welchen Modus (Foto, Video oder keine) die Kamera in aktuell ist, können Sie UnityEngine.XR.WSA.WebCam.Mode überprüfen.

## <a name="photo-capture"></a>Fotoaufnahmen

**Namespace:** *UnityEngine.XR.WSA.WebCam*<br>
**Typ:** *PhotoCapture*

Die *PhotoCapture* Typ können Sie die Fotos mit der Foto-Videokamera weiterhin zu nutzen. Das allgemeine Muster für die Verwendung von *PhotoCapture* auf ein Bild aufnehmen kann lautet wie folgt:
1. Erstellen Sie eine *PhotoCapture* Objekt
2. Erstellen Sie eine *CameraParameters* Objekt mit den Einstellungen, die wir möchten
3. Starten Sie den Fotomodus über *StartPhotoModeAsync*
4. Die gewünschte Foto
    * (optional) Dieses Bild interagieren
5. Fotomodus beenden und Bereinigen von Ressourcen

### <a name="common-set-up-for-photocapture"></a>Allgemeine einrichten für PhotoCapture

Für alle drei Verwendungszwecke beginnen wir mit dem gleichen ersten 3 oben genannten Schritte

Erstellen Sie zunächst eine *PhotoCapture* Objekt

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

Als Nächstes wir das-Objekt speichern, legen Sie unsere Parameter und Foto Startmodus

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

Am Ende auch verwenden dem Bereinigen der hier dargestellte Code wir

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

Nach diesen Schritten können Sie, welche Art von Fotos erfassen auswählen.

### <a name="capture-a-photo-to-a-file"></a>Erfassen Sie ein Foto in einer Datei

Die einfachste Operation ist ein Foto direkt in eine Datei zu erfassen. Das Foto kann als eine JPG- oder eine PNG-Datei gespeichert werden.

Wenn wir erfolgreich Fotomodus gestartet haben, wir nun ein Foto und speichern Sie sie auf dem Datenträger

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

Nach dem Erfassen des Fotos auf dem Datenträger an, wir Fotomodus beenden und bereinigen Sie anschließend auf unsere Objekte

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

### <a name="capture-a-photo-to-a-texture2d"></a>Erfassen Sie ein Foto auf ein Texture2D

Beim Erfassen von Daten in ein Texture2D ähnelt der Prozess sehr auf Datenträger erfassen.

Wir befolgen den Einrichten der oben beschriebenen Prozess.

In *OnPhotoModeStarted*, werden wir einen Frame in den Speicher erfasst.

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

Wir dann wenden Sie unser Ergebnis auf eine Textur und verwendet die allgemeinen bereinigen Sie die oben angegebenen Code.

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>Erfassen Sie ein Foto und interagieren mit den unformatierten bytes

Für die Interaktion mit den unformatierten Bytes einer in-Memory Frame befolgen wir die gleichen Schritte wie oben beschrieben einrichten und *OnPhotoModeStarted* wie ein Foto auf ein Texture2D erfassen. Der Unterschied besteht darin, *OnCapturedPhotoToMemory* , in dem die unformatierten Bytes zu erhalten und mit ihnen interagieren.

In diesem Beispiel erstellen wir eine *Liste<Color>*  verarbeitet oder angewendet wird, auf eine Textur über die möglicherweise weitere *SetPixels()*

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

## <a name="video-capture"></a>Videoaufzeichnung

**Namespace:** *UnityEngine.XR.WSA.WebCam*<br>
**Typ:** *VideoCapture*

*VideoCapture* funktioniert sehr ähnlich wie *PhotoCapture*. Die nur zwei Unterschiede liegen, dass Sie einen Wert für die Frames pro Sekunde (FPS) angeben müssen und Sie können nur direkt auf den Datenträger als eine MP4-Datei speichern. Die Schritte zur Verwendung *VideoCapture* lauten wie folgt:
1. Erstellen Sie eine *VideoCapture* Objekt
2. Erstellen Sie eine *CameraParameters* Objekt mit den Einstellungen, die wir möchten
3. Starten Sie den Video-Modus über *StartVideoModeAsync*
4. Starten Sie die Aufnahme von Videos
5. Beenden Sie die Aufnahme von Videos
6. Video-Modus beenden und Bereinigen von Ressourcen

Erstellen Sie zunächst unser *VideoCapture* Objekt *VideoCapture M_VideoCapture = Null;*

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

Wir werden klicken Sie dann die Parameter einrichten, die für die Aufzeichnung und Start werden sollten.

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

Nach dem Start werden wir die Aufzeichnung beginnen.

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

Nach der Aufzeichnung gestartet wurde, konnte Sie Ihre UI oder Verhaltensweisen, zum Aktivieren von beenden aktualisieren. Wir Anmelden hier nur

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

Zu einem späteren Zeitpunkt möchten wir die Aufzeichnung zu beenden. Dies kann über einen Timer oder eine Benutzereingabe, z. B. passieren.

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

Nachdem Sie die Aufzeichnung beendet wurde, wir Videomodus beenden und Bereinigen von Ressourcen.

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
* Keine Lösungen sind verfügbar.
    * Stellen Sie sicher die **WebCam** Funktion in Ihrem Projekt angegeben ist.

## <a name="see-also"></a>Siehe auch
* [Gebietsschemabezogene Kamera](locatable-camera.md)
