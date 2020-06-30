---
title: HoloLens-Foto-/Videokamera in Unreal
description: Leitfaden für die Verwendung der HoloLens-Foto-/Videokamera in Unreal
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, Kamera, FV-Kamera, MRC
ms.openlocfilehash: e15ea593283a22dc31cd496de596159035d83799
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720326"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="54636-104">HoloLens-Foto-/Videokamera in Unreal</span><span class="sxs-lookup"><span data-stu-id="54636-104">HoloLens Photo/Video Camera in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="54636-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="54636-105">Overview</span></span>

<span data-ttu-id="54636-106">HoloLens verfügt über eine Foto-/Videokamera (FV), die einerseits für die Mixed Reality-Aufnahme (Mixed Reality Capture, MRC) und andererseits von einer App zum Zugriff auf visuelle Elemente der realen Welt verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="54636-106">The HoloLens has a Photo/Video (PV) Camera that is used for both Mixed Reality Capture (MRC) and can be used by an app to access real-world visuals.</span></span>

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="54636-107">Rendering von der FV-Kamera für MRC</span><span class="sxs-lookup"><span data-stu-id="54636-107">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="54636-108">Dafür ist **Unreal Engine 4.25** oder höher erforderlich.</span><span class="sxs-lookup"><span data-stu-id="54636-108">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="54636-109">Das System und benutzerdefinierte MRC-Rekorder erstellen Mixed Reality-Aufnahmen, indem sie die FV-Kamera mit Hologrammen kombinieren, die von der immersiven App gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="54636-109">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="54636-110">Standardmäßig wird für die Mixed-Reality-Aufnahme die holografische Ausgabe des rechten Auges verwendet.</span><span class="sxs-lookup"><span data-stu-id="54636-110">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="54636-111">Wenn eine immersive App hingegen [von der FV-Kamera rendert](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), wird stattdessen diese verwendet.</span><span class="sxs-lookup"><span data-stu-id="54636-111">If an immersive app chooses to [render from the PV Camera](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="54636-112">Dies ermöglicht eine bessere Abstimmung zwischen der realen Welt und den Hologrammen im MRC-Video.</span><span class="sxs-lookup"><span data-stu-id="54636-112">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="54636-113">So abonnieren Sie das Rendering von der FV-Kamera:</span><span class="sxs-lookup"><span data-stu-id="54636-113">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="54636-114">Rufen Sie **SetEnabledMixedRealityCamera** und **ResizeMixedRealityCamera** auf.</span><span class="sxs-lookup"><span data-stu-id="54636-114">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="54636-115">Verwenden Sie die Werte **Size X** (Größe X) und **Size Y** (Größe Y), um die Videoabmessungen festzulegen.</span><span class="sxs-lookup"><span data-stu-id="54636-115">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![Dritte Kamera](images/unreal-camera-3rd.PNG)

<span data-ttu-id="54636-117">Unreal verarbeitet dann Anforderungen von MRC, aus der Perspektive der FV-Kamera zu rendern.</span><span class="sxs-lookup"><span data-stu-id="54636-117">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="54636-118">Nur wenn [Mixed Reality Capture](mixed-reality-capture.md) (Mixed Reality-Aufnahme) ausgelöst wird, wird die App aufgefordert, aus der Perspektive der Foto-/Videokamera zu rendern.</span><span class="sxs-lookup"><span data-stu-id="54636-118">Only when [Mixed Reality Capture](mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="54636-119">Verwenden der FV-Kamera</span><span class="sxs-lookup"><span data-stu-id="54636-119">Using the PV Camera</span></span>

<span data-ttu-id="54636-120">Die Webcam-Textur kann im Spiel zur Laufzeit abgerufen werden, dies muss jedoch im Editor unter **Edit > Project Settings** (Bearbeiten > Projekteinstellungen) aktiviert werden:</span><span class="sxs-lookup"><span data-stu-id="54636-120">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="54636-121">Wechseln Sie zu **Platforms > HoloLens > Capabilities** (Plattformen > HoloLens > Funktionen), und aktivieren Sie **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="54636-121">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="54636-122">Verwenden Sie die Funktion **StartCameraCapture**, um die Webcam zur Laufzeit zu nutzen, und die Funktion **StopCameraCapture**, um die Aufzeichnung zu beenden.</span><span class="sxs-lookup"><span data-stu-id="54636-122">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Kamera: Starten/Beenden](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="54636-124">Rendern eines Bilds</span><span class="sxs-lookup"><span data-stu-id="54636-124">Rendering an image</span></span>
<span data-ttu-id="54636-125">So wird das Kamerabild gerendert:</span><span class="sxs-lookup"><span data-stu-id="54636-125">To render the camera image:</span></span>
1. <span data-ttu-id="54636-126">Erstellen Sie auf der Grundlage eines Materials im Projekt eine dynamische Materialinstanz, die im Screenshot unten den Namen **PVCamMat** trägt.</span><span class="sxs-lookup"><span data-stu-id="54636-126">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="54636-127">Legen Sie die dynamische Materialinstanz auf eine **Material Instance Dynamic Object Reference**-Variable (Materialinstanz mit dynamischem Objektverweis) fest.</span><span class="sxs-lookup"><span data-stu-id="54636-127">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="54636-128">Legen Sie das Material des Objekts in der Szene, das den Kamerafeed rendern soll, auf diese neue dynamische Materialinstanz fest.</span><span class="sxs-lookup"><span data-stu-id="54636-128">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="54636-129">Starten Sie einen Timer, der dazu verwendet wird, das Kamerabild an das Material zu binden.</span><span class="sxs-lookup"><span data-stu-id="54636-129">Start a timer that will be used to bind the camera image to the material.</span></span> 

![Kamera: Rendern](images/unreal-camera-render.PNG)

4. <span data-ttu-id="54636-131">Erstellen Sie eine neue Funktion für diesen Timer (in diesem Fall: **MaterialTimer**), und rufen Sie **GetARCameraImage** auf, um die Textur von der Webcam abzurufen.</span><span class="sxs-lookup"><span data-stu-id="54636-131">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="54636-132">Ist diese Textur gültig, legen Sie im Shader einen Texturparameter auf dieses Bild fest.</span><span class="sxs-lookup"><span data-stu-id="54636-132">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="54636-133">Falls nicht, starten Sie den Materialtimer erneut.</span><span class="sxs-lookup"><span data-stu-id="54636-133">Otherwise, start the material timer again.</span></span> 

![Kamera: Textur](images/unreal-camera-texture.PNG)

5. <span data-ttu-id="54636-135">Achten Sie darauf, dass das Material über einen Parameter verfügt, der mit dem Namen in **SetTextureParameterValue** übereinstimmt, der an einen Farbeintrag gebunden ist.</span><span class="sxs-lookup"><span data-stu-id="54636-135">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="54636-136">Ohne dies kann das Kamerabild nicht ordnungsgemäß angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="54636-136">Without this, the camera image can't be properly displayed.</span></span>

![Kamera: Textur](images/unreal-camera-material.PNG)

## <a name="see-also"></a><span data-ttu-id="54636-138">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="54636-138">See also</span></span>
* [<span data-ttu-id="54636-139">Ausrichtbare Kamera</span><span class="sxs-lookup"><span data-stu-id="54636-139">Locatable camera</span></span>](locatable-camera.md)
* [<span data-ttu-id="54636-140">Mixed Reality-Aufnahme für Entwickler</span><span class="sxs-lookup"><span data-stu-id="54636-140">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
