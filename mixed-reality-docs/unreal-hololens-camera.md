---
title: HoloLens-Foto-/Videokamera in Unreal
description: Leitfaden für die Verwendung der HoloLens-Foto-/Videokamera in Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, Kamera, FV-Kamera, MRC
ms.openlocfilehash: 06ceb26d58fe60848e5e90360aa2e05984a901c5
ms.sourcegitcommit: f24ac845e184c2f90e8b15adab9addb913f5cb83
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84451335"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="d95dd-104">HoloLens-Foto-/Videokamera in Unreal</span><span class="sxs-lookup"><span data-stu-id="d95dd-104">HoloLens Photo/Video Camera in Unreal</span></span>

<span data-ttu-id="d95dd-105">HoloLens verfügt über eine Foto-/Videokamera (FV), die einerseits für die Mixed Reality-Aufnahme (Mixed Reality Capture, MRC) und andererseits von einer App zum Zugriff auf visuelle Elemente der realen Welt verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="d95dd-105">The HoloLens has a Photo/Video (PV) Camera that is used for both Mixed Reality Capture (MRC) and can be used by an app to access real-world visuals.</span></span>

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="d95dd-106">Rendering von der FV-Kamera für MRC</span><span class="sxs-lookup"><span data-stu-id="d95dd-106">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="d95dd-107">Dafür ist **Unreal Engine 4.25** oder höher erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d95dd-107">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="d95dd-108">Das System und benutzerdefinierte MRC-Rekorder erstellen Mixed Reality-Aufnahmen, indem sie die FV-Kamera mit Hologrammen kombinieren, die von der immersiven App gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="d95dd-108">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="d95dd-109">Standardmäßig wird für die Mixed-Reality-Aufnahme die holografische Ausgabe des rechten Auges verwendet.</span><span class="sxs-lookup"><span data-stu-id="d95dd-109">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="d95dd-110">Wenn eine immersive App hingegen [von der FV-Kamera rendert](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), wird stattdessen diese verwendet.</span><span class="sxs-lookup"><span data-stu-id="d95dd-110">If an immersive app chooses to [render from the PV Camera](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="d95dd-111">Dies ermöglicht eine bessere Abstimmung zwischen der realen Welt und den Hologrammen im MRC-Video.</span><span class="sxs-lookup"><span data-stu-id="d95dd-111">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="d95dd-112">So abonnieren Sie das Rendering von der FV-Kamera:</span><span class="sxs-lookup"><span data-stu-id="d95dd-112">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="d95dd-113">Rufen Sie **SetEnabledMixedRealityCamera** und **ResizeMixedRealityCamera** auf.</span><span class="sxs-lookup"><span data-stu-id="d95dd-113">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="d95dd-114">Verwenden Sie die Werte **Size X** (Größe X) und **Size Y** (Größe Y), um die Videoabmessungen festzulegen.</span><span class="sxs-lookup"><span data-stu-id="d95dd-114">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![Dritte Kamera](images/unreal-camera-3rd.PNG)

<span data-ttu-id="d95dd-116">Unreal verarbeitet dann Anforderungen von MRC, aus der Perspektive der FV-Kamera zu rendern.</span><span class="sxs-lookup"><span data-stu-id="d95dd-116">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="d95dd-117">Nur wenn [Mixed Reality Capture](mixed-reality-capture.md) (Mixed Reality-Aufnahme) ausgelöst wird, wird die App aufgefordert, aus der Perspektive der Foto-/Videokamera zu rendern.</span><span class="sxs-lookup"><span data-stu-id="d95dd-117">Only when [Mixed Reality Capture](mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="d95dd-118">Verwenden der FV-Kamera</span><span class="sxs-lookup"><span data-stu-id="d95dd-118">Using the PV Camera</span></span>

<span data-ttu-id="d95dd-119">Die Webcam-Textur kann im Spiel zur Laufzeit abgerufen werden, dies muss jedoch im Editor unter **Edit > Project Settings** (Bearbeiten > Projekteinstellungen) aktiviert werden:</span><span class="sxs-lookup"><span data-stu-id="d95dd-119">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="d95dd-120">Wechseln Sie zu **Platforms > HoloLens > Capabilities** (Plattformen > HoloLens > Funktionen), und aktivieren Sie **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="d95dd-120">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="d95dd-121">Verwenden Sie die Funktion **StartCameraCapture**, um die Webcam zur Laufzeit zu nutzen, und die Funktion **StopCameraCapture**, um die Aufzeichnung zu beenden.</span><span class="sxs-lookup"><span data-stu-id="d95dd-121">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Kamera: Starten/Beenden](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="d95dd-123">Rendern eines Bilds</span><span class="sxs-lookup"><span data-stu-id="d95dd-123">Rendering an image</span></span>
<span data-ttu-id="d95dd-124">So wird das Kamerabild gerendert:</span><span class="sxs-lookup"><span data-stu-id="d95dd-124">To render the camera image:</span></span>
1. <span data-ttu-id="d95dd-125">Erstellen Sie auf der Grundlage eines Materials im Projekt eine dynamische Materialinstanz, die im Screenshot unten den Namen **PVCamMat** trägt.</span><span class="sxs-lookup"><span data-stu-id="d95dd-125">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="d95dd-126">Legen Sie die dynamische Materialinstanz auf eine **Material Instance Dynamic Object Reference**-Variable (Materialinstanz mit dynamischem Objektverweis) fest.</span><span class="sxs-lookup"><span data-stu-id="d95dd-126">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="d95dd-127">Legen Sie das Material des Objekts in der Szene, das den Kamerafeed rendern soll, auf diese neue dynamische Materialinstanz fest.</span><span class="sxs-lookup"><span data-stu-id="d95dd-127">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="d95dd-128">Starten Sie einen Timer, der dazu verwendet wird, das Kamerabild an das Material zu binden.</span><span class="sxs-lookup"><span data-stu-id="d95dd-128">Start a timer that will be used to bind the camera image to the material.</span></span> 

![Kamera: Rendern](images/unreal-camera-render.PNG)

4. <span data-ttu-id="d95dd-130">Erstellen Sie eine neue Funktion für diesen Timer (in diesem Fall: **MaterialTimer**), und rufen Sie **GetARCameraImage** auf, um die Textur von der Webcam abzurufen.</span><span class="sxs-lookup"><span data-stu-id="d95dd-130">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="d95dd-131">Ist diese Textur gültig, legen Sie im Shader einen Texturparameter auf dieses Bild fest.</span><span class="sxs-lookup"><span data-stu-id="d95dd-131">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="d95dd-132">Falls nicht, starten Sie den Materialtimer erneut.</span><span class="sxs-lookup"><span data-stu-id="d95dd-132">Otherwise, start the material timer again.</span></span> 

![Kamera: Textur](images/unreal-camera-texture.PNG)

5. <span data-ttu-id="d95dd-134">Achten Sie darauf, dass das Material über einen Parameter verfügt, der mit dem Namen in **SetTextureParameterValue** übereinstimmt, der an einen Farbeintrag gebunden ist.</span><span class="sxs-lookup"><span data-stu-id="d95dd-134">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="d95dd-135">Ohne dies kann das Kamerabild nicht ordnungsgemäß angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d95dd-135">Without this, the camera image can't be properly displayed.</span></span>

![Kamera: Textur](images/unreal-camera-material.PNG)

## <a name="see-also"></a><span data-ttu-id="d95dd-137">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d95dd-137">See also</span></span>
* [<span data-ttu-id="d95dd-138">Ausrichtbare Kamera</span><span class="sxs-lookup"><span data-stu-id="d95dd-138">Locatable camera</span></span>](locatable-camera.md)
* [<span data-ttu-id="d95dd-139">Mixed Reality-Aufnahme für Entwickler</span><span class="sxs-lookup"><span data-stu-id="d95dd-139">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
