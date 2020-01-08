---
title: Einsetzbare Kamera in Unity
description: Hololens der verwendbaren Kamera Verwendung in Unity.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: Foto, Video, hololens, Kamera, Unity, loalisierbar
ms.openlocfilehash: b4a1a7e11a7606dab76b954c8d58a335d6bae0ab
ms.sourcegitcommit: d0da0214fdd2bbac5a91a5d895bf0e87413b29b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597613"
---
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="ffc3f-104">Einsetzbare Kamera in Unity</span><span class="sxs-lookup"><span data-stu-id="ffc3f-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="ffc3f-105">Aktivieren der Funktion für Foto-Video Kamera</span><span class="sxs-lookup"><span data-stu-id="ffc3f-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="ffc3f-106">Die "Webcam"-Funktion muss für eine APP deklariert werden, um die [Kamera](locatable-camera.md)zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-106">The "WebCam" capability must be declared for an app to use the [camera](locatable-camera.md).</span></span>
1. <span data-ttu-id="ffc3f-107">Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zur Seite "> Projekteinstellungen bearbeiten > Player" navigieren.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-107">In the Unity Editor, go to the player settings by navigating to the "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="ffc3f-108">Klicken Sie auf die Registerkarte "Windows Store".</span><span class="sxs-lookup"><span data-stu-id="ffc3f-108">Click the "Windows Store" tab</span></span>
3. <span data-ttu-id="ffc3f-109">Überprüfen Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die Funktionen für **Webcam** und **Mikrofon** .</span><span class="sxs-lookup"><span data-stu-id="ffc3f-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="ffc3f-110">Nur ein einzelner Vorgang kann gleichzeitig mit der Kamera erfolgen.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="ffc3f-111">Um zu ermitteln, in welchem Modus (Foto, Video oder None) sich die Kamera derzeit befindet, können Sie unityengine. XR. WSA. Webcam. Mode überprüfen.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-111">To determine which mode (photo, video, or none) the camera is currently in, you can check UnityEngine.XR.WSA.WebCam.Mode.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="ffc3f-112">Foto Erfassung</span><span class="sxs-lookup"><span data-stu-id="ffc3f-112">Photo Capture</span></span>

<span data-ttu-id="ffc3f-113">**Namespace:** *unityengine. XR. WSA. Webcam*</span><span class="sxs-lookup"><span data-stu-id="ffc3f-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="ffc3f-114">**Typ:** *photocapture*</span><span class="sxs-lookup"><span data-stu-id="ffc3f-114">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="ffc3f-115">Mit dem Typ *photocapture* können Sie weiterhin Fotos mit der Foto Video Kamera aufnehmen.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-115">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="ffc3f-116">Das allgemeine Muster für die Verwendung von *Photo Capture* für die Aufnahme eines Fotos sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="ffc3f-116">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="ffc3f-117">Erstellen eines *photocapture* -Objekts</span><span class="sxs-lookup"><span data-stu-id="ffc3f-117">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="ffc3f-118">Erstellen Sie ein " *cameraparameters* "-Objekt mit den gewünschten Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-118">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="ffc3f-119">Foto Modus über " *startphotomodeasync* " starten</span><span class="sxs-lookup"><span data-stu-id="ffc3f-119">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="ffc3f-120">Nehmen Sie das gewünschte Foto</span><span class="sxs-lookup"><span data-stu-id="ffc3f-120">Take the desired photo</span></span>
    * <span data-ttu-id="ffc3f-121">optionale Mit diesem Bild interagieren</span><span class="sxs-lookup"><span data-stu-id="ffc3f-121">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="ffc3f-122">Foto Modus abbrechen und Ressourcen bereinigen</span><span class="sxs-lookup"><span data-stu-id="ffc3f-122">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="ffc3f-123">Allgemeine Einrichtung für photocapture</span><span class="sxs-lookup"><span data-stu-id="ffc3f-123">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="ffc3f-124">Beginnen Sie für alle drei Verwendungszwecke mit denselben ersten drei Schritten.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-124">For all three uses, start with the same first 3 steps above</span></span>

<span data-ttu-id="ffc3f-125">Beginnen Sie mit dem Erstellen eines *photocapture* -Objekts.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-125">Start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="ffc3f-126">Speichern Sie anschließend das Objekt, legen Sie die Parameter fest, und starten Sie den Photo-Modus.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-126">Next, store your object, set your parameters, and start Photo Mode</span></span>

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

<span data-ttu-id="ffc3f-127">Am Ende verwenden Sie auch denselben Bereinigungs Code, der hier präsentiert wird.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-127">In the end, you will also use the same clean up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="ffc3f-128">Nachdem Sie diese Schritte ausgeführt haben, können Sie den Typ des zu erfassenden Fotos auswählen.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-128">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="ffc3f-129">Fotos in einer Datei erfassen</span><span class="sxs-lookup"><span data-stu-id="ffc3f-129">Capture a Photo to a File</span></span>

<span data-ttu-id="ffc3f-130">Der einfachste Vorgang besteht darin, ein Foto direkt in einer Datei zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-130">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="ffc3f-131">Das Foto kann als jpg oder PNG gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-131">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="ffc3f-132">Wenn Sie den Foto Modus erfolgreich gestartet haben, erstellen Sie ein Foto, und speichern Sie es auf dem Datenträger</span><span class="sxs-lookup"><span data-stu-id="ffc3f-132">If you successfully started photo mode, take a photo and store it on disk</span></span>

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

<span data-ttu-id="ffc3f-133">Beenden Sie nach dem Erfassen des Fotos auf dem Datenträger den Photo-Modus, und bereinigen Sie die Objekte.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-133">After capturing the photo to disk, exit photo mode and then clean up your objects</span></span>

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

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="ffc3f-134">Fotos für ein Texture2D erfassen</span><span class="sxs-lookup"><span data-stu-id="ffc3f-134">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="ffc3f-135">Beim Erfassen von Daten in einem Texture2D ähnelt der Prozess stark der Erfassung auf dem Datenträger.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-135">When capturing data to a Texture2D, the process is extremely similar to capturing to disk.</span></span>

<span data-ttu-id="ffc3f-136">Befolgen Sie den oben beschriebenen Setup Vorgang.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-136">Follow the set up process above.</span></span>

<span data-ttu-id="ffc3f-137">Erfassen Sie in *onphotomodestarted*einen Frame im Speicher.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-137">In *OnPhotoModeStarted*, capture a frame to memory.</span></span>

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

<span data-ttu-id="ffc3f-138">Anschließend wenden Sie das Ergebnis auf eine Textur an und verwenden den oben aufgeführten allgemeinen Bereinigungs Code.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-138">You will then apply your result to a texture and use the common clean up code above.</span></span>

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="ffc3f-139">Fotos erfassen und mit den Rohdaten Bytes interagieren</span><span class="sxs-lookup"><span data-stu-id="ffc3f-139">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="ffc3f-140">Wenn Sie mit den unformatierten Bytes eines in-Memory-Frames interagieren möchten, befolgen Sie die gleichen Setup Schritte wie oben und *onphotomodestarted* wie bei der Erfassung eines Fotos für eine Texture2D.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-140">To interact with the raw bytes of an in memory frame, follow the same set up steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="ffc3f-141">Der Unterschied liegt in *oncapturedphototomemory* , wo Sie die Rohdaten Bytes erhalten und mit ihnen interagieren können.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-141">The difference is in *OnCapturedPhotoToMemory* where you can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="ffc3f-142">In diesem Beispiel erstellen Sie eine *Liste<Color>* die weiterverarbeitet oder auf eine Textur über *setPixels ()* angewendet werden können.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-142">In this example, you will create a *List<Color>* which could be further processed or applied to a texture via *SetPixels()*</span></span>

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

## <a name="video-capture"></a><span data-ttu-id="ffc3f-143">Video Erfassung</span><span class="sxs-lookup"><span data-stu-id="ffc3f-143">Video Capture</span></span>

<span data-ttu-id="ffc3f-144">**Namespace:** *unityengine. XR. WSA. Webcam*</span><span class="sxs-lookup"><span data-stu-id="ffc3f-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="ffc3f-145">**Typ:** *Videocapture*</span><span class="sxs-lookup"><span data-stu-id="ffc3f-145">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="ffc3f-146">*Videocapture* funktioniert sehr ähnlich wie bei *photocapture*.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-146">*VideoCapture* functions very similarly to *PhotoCapture*.</span></span> <span data-ttu-id="ffc3f-147">Die einzigen beiden Unterschiede sind, dass Sie einen Wert für Frames pro Sekunde (fps) angeben müssen, und Sie können nur direkt auf dem Datenträger als MP4-Datei speichern.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-147">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as an .mp4 file.</span></span> <span data-ttu-id="ffc3f-148">Die Schritte für die Verwendung von *Videocapture* lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="ffc3f-148">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="ffc3f-149">Erstellen eines *Videocapture* -Objekts</span><span class="sxs-lookup"><span data-stu-id="ffc3f-149">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="ffc3f-150">Erstellen Sie ein " *cameraparameters* "-Objekt mit den gewünschten Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-150">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="ffc3f-151">Starten des Video Modus über *startvideomodeasync*</span><span class="sxs-lookup"><span data-stu-id="ffc3f-151">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="ffc3f-152">Aufzeichnen des Videos starten</span><span class="sxs-lookup"><span data-stu-id="ffc3f-152">Start recording video</span></span>
5. <span data-ttu-id="ffc3f-153">Aufzeichnen von Videos anhalten</span><span class="sxs-lookup"><span data-stu-id="ffc3f-153">Stop recording video</span></span>
6. <span data-ttu-id="ffc3f-154">Video Modus abbrechen und Ressourcen bereinigen</span><span class="sxs-lookup"><span data-stu-id="ffc3f-154">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="ffc3f-155">Erstellen Sie zunächst das *Videocapture* -Objekt *Videocapture m_VideoCapture = NULL;*</span><span class="sxs-lookup"><span data-stu-id="ffc3f-155">Start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="ffc3f-156">Richten Sie als nächstes die Parameter ein, die für die Aufzeichnung verwendet werden sollen, und starten Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-156">Next, set up the parameters you will want for the recording and start.</span></span>

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

<span data-ttu-id="ffc3f-157">Starten der Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="ffc3f-157">Once started, begin the recording</span></span>

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

<span data-ttu-id="ffc3f-158">Nachdem die Aufzeichnung gestartet wurde, können Sie die Benutzeroberfläche oder das Verhalten aktualisieren, um das Beenden zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-158">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="ffc3f-159">Hier melden Sie sich einfach an.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-159">Here you just log.</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="ffc3f-160">Zu einem späteren Zeitpunkt möchten Sie die Aufzeichnung anhalten.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-160">At a later point, you will want to stop the recording.</span></span> <span data-ttu-id="ffc3f-161">Dies kann beispielsweise bei einem Timer oder einer Benutzereingabe vorkommen.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-161">This could happen from a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="ffc3f-162">Wenn die Aufzeichnung beendet wurde, beenden Sie den Videomodus, und bereinigen Sie Ihre Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-162">Once the recording has stopped, stop video mode and clean up your resources.</span></span>

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

## <a name="troubleshooting"></a><span data-ttu-id="ffc3f-163">Fehlerbehebung</span><span class="sxs-lookup"><span data-stu-id="ffc3f-163">Troubleshooting</span></span>
* <span data-ttu-id="ffc3f-164">Es sind keine Auflösungen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-164">No resolutions are available</span></span>
    * <span data-ttu-id="ffc3f-165">Stellen Sie sicher, dass die **Webcam** -Funktion in Ihrem Projekt angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="ffc3f-165">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="ffc3f-166">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ffc3f-166">See Also</span></span>
* [<span data-ttu-id="ffc3f-167">Ausrichtbare Kamera</span><span class="sxs-lookup"><span data-stu-id="ffc3f-167">Locatable camera</span></span>](locatable-camera.md)
