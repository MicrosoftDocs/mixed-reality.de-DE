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
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="5274e-104">Gebietsschemabezogene Kamera in Unity</span><span class="sxs-lookup"><span data-stu-id="5274e-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="5274e-105">Aktivieren die Funktion für die Foto-Videokamera</span><span class="sxs-lookup"><span data-stu-id="5274e-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="5274e-106">Die Funktion "WebCam" muss deklariert werden, für eine app für die Verwendung der [Kamera](locatable-camera.md).</span><span class="sxs-lookup"><span data-stu-id="5274e-106">The "WebCam" capability must be declared for an app to use the [camera](locatable-camera.md).</span></span>
1. <span data-ttu-id="5274e-107">Rufen Sie im Unity-Editor die playereinstellungen durch Navigieren zu "Bearbeiten > Projekt Einstellungen > Player"-Seite</span><span class="sxs-lookup"><span data-stu-id="5274e-107">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="5274e-108">Klicken Sie auf der Registerkarte "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="5274e-108">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="5274e-109">Überprüfen Sie im Abschnitt "Einstellungen > Veröffentlichungsfunktionen" die **WebCam** und **Mikrofon** Funktionen</span><span class="sxs-lookup"><span data-stu-id="5274e-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="5274e-110">Nur ein einzelner Vorgang kann mit der Kamera zu einem Zeitpunkt ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="5274e-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="5274e-111">Um zu bestimmen, welchen Modus (Foto, Video oder keine) die Kamera in aktuell ist, können Sie UnityEngine.XR.WSA.WebCam.Mode überprüfen.</span><span class="sxs-lookup"><span data-stu-id="5274e-111">To determine which mode (photo, video, or none) the camera is currently in, you can check UnityEngine.XR.WSA.WebCam.Mode.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="5274e-112">Fotoaufnahmen</span><span class="sxs-lookup"><span data-stu-id="5274e-112">Photo Capture</span></span>

<span data-ttu-id="5274e-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span><span class="sxs-lookup"><span data-stu-id="5274e-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="5274e-114">**Typ:** *PhotoCapture*</span><span class="sxs-lookup"><span data-stu-id="5274e-114">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="5274e-115">Die *PhotoCapture* Typ können Sie die Fotos mit der Foto-Videokamera weiterhin zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="5274e-115">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="5274e-116">Das allgemeine Muster für die Verwendung von *PhotoCapture* auf ein Bild aufnehmen kann lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="5274e-116">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="5274e-117">Erstellen Sie eine *PhotoCapture* Objekt</span><span class="sxs-lookup"><span data-stu-id="5274e-117">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="5274e-118">Erstellen Sie eine *CameraParameters* Objekt mit den Einstellungen, die wir möchten</span><span class="sxs-lookup"><span data-stu-id="5274e-118">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="5274e-119">Starten Sie den Fotomodus über *StartPhotoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="5274e-119">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="5274e-120">Die gewünschte Foto</span><span class="sxs-lookup"><span data-stu-id="5274e-120">Take the desired photo</span></span>
    * <span data-ttu-id="5274e-121">(optional) Dieses Bild interagieren</span><span class="sxs-lookup"><span data-stu-id="5274e-121">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="5274e-122">Fotomodus beenden und Bereinigen von Ressourcen</span><span class="sxs-lookup"><span data-stu-id="5274e-122">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="5274e-123">Allgemeine einrichten für PhotoCapture</span><span class="sxs-lookup"><span data-stu-id="5274e-123">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="5274e-124">Für alle drei Verwendungszwecke beginnen wir mit dem gleichen ersten 3 oben genannten Schritte</span><span class="sxs-lookup"><span data-stu-id="5274e-124">For all three uses, we start with the same first 3 steps above</span></span>

<span data-ttu-id="5274e-125">Erstellen Sie zunächst eine *PhotoCapture* Objekt</span><span class="sxs-lookup"><span data-stu-id="5274e-125">We start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="5274e-126">Als Nächstes wir das-Objekt speichern, legen Sie unsere Parameter und Foto Startmodus</span><span class="sxs-lookup"><span data-stu-id="5274e-126">Next we store our object, set our parameters, and start Photo Mode</span></span>

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

<span data-ttu-id="5274e-127">Am Ende auch verwenden dem Bereinigen der hier dargestellte Code wir</span><span class="sxs-lookup"><span data-stu-id="5274e-127">In the end, we will also use the same clean up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="5274e-128">Nach diesen Schritten können Sie, welche Art von Fotos erfassen auswählen.</span><span class="sxs-lookup"><span data-stu-id="5274e-128">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="5274e-129">Erfassen Sie ein Foto in einer Datei</span><span class="sxs-lookup"><span data-stu-id="5274e-129">Capture a Photo to a File</span></span>

<span data-ttu-id="5274e-130">Die einfachste Operation ist ein Foto direkt in eine Datei zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="5274e-130">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="5274e-131">Das Foto kann als eine JPG- oder eine PNG-Datei gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="5274e-131">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="5274e-132">Wenn wir erfolgreich Fotomodus gestartet haben, wir nun ein Foto und speichern Sie sie auf dem Datenträger</span><span class="sxs-lookup"><span data-stu-id="5274e-132">If we successfully started photo mode, we now will take a photo and store it on disk</span></span>

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

<span data-ttu-id="5274e-133">Nach dem Erfassen des Fotos auf dem Datenträger an, wir Fotomodus beenden und bereinigen Sie anschließend auf unsere Objekte</span><span class="sxs-lookup"><span data-stu-id="5274e-133">After capturing the photo to disk, we will exit photo mode and then clean up our objects</span></span>

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

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="5274e-134">Erfassen Sie ein Foto auf ein Texture2D</span><span class="sxs-lookup"><span data-stu-id="5274e-134">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="5274e-135">Beim Erfassen von Daten in ein Texture2D ähnelt der Prozess sehr auf Datenträger erfassen.</span><span class="sxs-lookup"><span data-stu-id="5274e-135">When capturing data to a Texture2D, the process is extremely similar to capturing to disk.</span></span>

<span data-ttu-id="5274e-136">Wir befolgen den Einrichten der oben beschriebenen Prozess.</span><span class="sxs-lookup"><span data-stu-id="5274e-136">We will follow the set up process above.</span></span>

<span data-ttu-id="5274e-137">In *OnPhotoModeStarted*, werden wir einen Frame in den Speicher erfasst.</span><span class="sxs-lookup"><span data-stu-id="5274e-137">In *OnPhotoModeStarted*, we will capture a frame to memory.</span></span>

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

<span data-ttu-id="5274e-138">Wir dann wenden Sie unser Ergebnis auf eine Textur und verwendet die allgemeinen bereinigen Sie die oben angegebenen Code.</span><span class="sxs-lookup"><span data-stu-id="5274e-138">We will then apply our result to a texture and use the common clean up code above.</span></span>

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="5274e-139">Erfassen Sie ein Foto und interagieren mit den unformatierten bytes</span><span class="sxs-lookup"><span data-stu-id="5274e-139">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="5274e-140">Für die Interaktion mit den unformatierten Bytes einer in-Memory Frame befolgen wir die gleichen Schritte wie oben beschrieben einrichten und *OnPhotoModeStarted* wie ein Foto auf ein Texture2D erfassen.</span><span class="sxs-lookup"><span data-stu-id="5274e-140">To interact with the raw bytes of an in memory frame, we will follow the same set up steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="5274e-141">Der Unterschied besteht darin, *OnCapturedPhotoToMemory* , in dem die unformatierten Bytes zu erhalten und mit ihnen interagieren.</span><span class="sxs-lookup"><span data-stu-id="5274e-141">The difference is in *OnCapturedPhotoToMemory* where we can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="5274e-142">In diesem Beispiel erstellen wir eine *Liste<Color>*  verarbeitet oder angewendet wird, auf eine Textur über die möglicherweise weitere *SetPixels()*</span><span class="sxs-lookup"><span data-stu-id="5274e-142">In this example, we will create a *List<Color>* which could be further processed or applied to a texture via *SetPixels()*</span></span>

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

## <a name="video-capture"></a><span data-ttu-id="5274e-143">Videoaufzeichnung</span><span class="sxs-lookup"><span data-stu-id="5274e-143">Video Capture</span></span>

<span data-ttu-id="5274e-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span><span class="sxs-lookup"><span data-stu-id="5274e-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="5274e-145">**Typ:** *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="5274e-145">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="5274e-146">*VideoCapture* funktioniert sehr ähnlich wie *PhotoCapture*.</span><span class="sxs-lookup"><span data-stu-id="5274e-146">*VideoCapture* functions very similarly to *PhotoCapture*.</span></span> <span data-ttu-id="5274e-147">Die nur zwei Unterschiede liegen, dass Sie einen Wert für die Frames pro Sekunde (FPS) angeben müssen und Sie können nur direkt auf den Datenträger als eine MP4-Datei speichern.</span><span class="sxs-lookup"><span data-stu-id="5274e-147">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as an .mp4 file.</span></span> <span data-ttu-id="5274e-148">Die Schritte zur Verwendung *VideoCapture* lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="5274e-148">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="5274e-149">Erstellen Sie eine *VideoCapture* Objekt</span><span class="sxs-lookup"><span data-stu-id="5274e-149">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="5274e-150">Erstellen Sie eine *CameraParameters* Objekt mit den Einstellungen, die wir möchten</span><span class="sxs-lookup"><span data-stu-id="5274e-150">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="5274e-151">Starten Sie den Video-Modus über *StartVideoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="5274e-151">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="5274e-152">Starten Sie die Aufnahme von Videos</span><span class="sxs-lookup"><span data-stu-id="5274e-152">Start recording video</span></span>
5. <span data-ttu-id="5274e-153">Beenden Sie die Aufnahme von Videos</span><span class="sxs-lookup"><span data-stu-id="5274e-153">Stop recording video</span></span>
6. <span data-ttu-id="5274e-154">Video-Modus beenden und Bereinigen von Ressourcen</span><span class="sxs-lookup"><span data-stu-id="5274e-154">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="5274e-155">Erstellen Sie zunächst unser *VideoCapture* Objekt *VideoCapture M_VideoCapture = Null;*</span><span class="sxs-lookup"><span data-stu-id="5274e-155">We start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="5274e-156">Wir werden klicken Sie dann die Parameter einrichten, die für die Aufzeichnung und Start werden sollten.</span><span class="sxs-lookup"><span data-stu-id="5274e-156">We then will set up the parameters we will want for the recording and start.</span></span>

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

<span data-ttu-id="5274e-157">Nach dem Start werden wir die Aufzeichnung beginnen.</span><span class="sxs-lookup"><span data-stu-id="5274e-157">Once started, we will begin the recording</span></span>

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

<span data-ttu-id="5274e-158">Nach der Aufzeichnung gestartet wurde, konnte Sie Ihre UI oder Verhaltensweisen, zum Aktivieren von beenden aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="5274e-158">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="5274e-159">Wir Anmelden hier nur</span><span class="sxs-lookup"><span data-stu-id="5274e-159">Here we just log</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="5274e-160">Zu einem späteren Zeitpunkt möchten wir die Aufzeichnung zu beenden.</span><span class="sxs-lookup"><span data-stu-id="5274e-160">At a later point, we will want to stop the recording.</span></span> <span data-ttu-id="5274e-161">Dies kann über einen Timer oder eine Benutzereingabe, z. B. passieren.</span><span class="sxs-lookup"><span data-stu-id="5274e-161">This could happen from a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="5274e-162">Nachdem Sie die Aufzeichnung beendet wurde, wir Videomodus beenden und Bereinigen von Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="5274e-162">Once the recording has stopped, we will stop video mode and clean up our resources.</span></span>

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

## <a name="troubleshooting"></a><span data-ttu-id="5274e-163">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="5274e-163">Troubleshooting</span></span>
* <span data-ttu-id="5274e-164">Keine Lösungen sind verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5274e-164">No resolutions are available</span></span>
    * <span data-ttu-id="5274e-165">Stellen Sie sicher die **WebCam** Funktion in Ihrem Projekt angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="5274e-165">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="5274e-166">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="5274e-166">See Also</span></span>
* [<span data-ttu-id="5274e-167">Gebietsschemabezogene Kamera</span><span class="sxs-lookup"><span data-stu-id="5274e-167">Locatable camera</span></span>](locatable-camera.md)
