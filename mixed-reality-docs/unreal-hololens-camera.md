---
title: HoloLens-Kamera in Unreal
description: Leitfaden für die Verwendung der HoloLens-Kamera in Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, Kamera, dritte Kamera, MRC
ms.openlocfilehash: 9ef9ce27d161130c6b9f3aa6bb1dbc47d7608ad9
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840119"
---
# <a name="hololens-camera-in-unreal"></a><span data-ttu-id="e944a-104">HoloLens-Kamera in Unreal</span><span class="sxs-lookup"><span data-stu-id="e944a-104">HoloLens Camera in Unreal</span></span>

## <a name="third-camera-mixed-reality-capture"></a><span data-ttu-id="e944a-105">Mixed Reality-Aufnahme der dritten Kamera</span><span class="sxs-lookup"><span data-stu-id="e944a-105">Third Camera Mixed Reality Capture</span></span>

<span data-ttu-id="e944a-106">Die Mixed Reality-Aufnahme (Mixed Reality Capture, MRC) der dritten Kamera kann verwendet werden, um eine Mixed Reality-Aufnahme aus der Perspektive der Kamera am HoloLens-Visor (anstelle der Perspektive der Augentexturen) zu rendern.</span><span class="sxs-lookup"><span data-stu-id="e944a-106">Third camera Mixed Reality Capture (MRC) can be used to render a mixed reality capture from the perspective of the camera on the HoloLens visor, rather than the perspective of the eye textures.</span></span>  <span data-ttu-id="e944a-107">Dies ermöglicht eine bessere Abstimmung zwischen der realen Welt und den Hologrammen im MRC-Video.</span><span class="sxs-lookup"><span data-stu-id="e944a-107">This improves the mapping between the real world and the holograms in the MRC video.</span></span> 

<span data-ttu-id="e944a-108">Wenn Sie die Mixed Reality-Aufnahme der dritten Kamera verwenden möchten, rufen Sie „SetEnabledMixedRealityCamera“ und „ResizeMixedRealityCamera“ mit den gewünschten Videodimensionen auf.</span><span class="sxs-lookup"><span data-stu-id="e944a-108">To opt into using third camera MRC, call SetEnabledMixedRealityCamera and ResizeMixedRealityCamera with the desired video dimensions.</span></span> 

![Dritte Kamera](images/unreal-camera-3rd.PNG)

<span data-ttu-id="e944a-110">Zeichnen Sie dann ein MRC-Video im HoloLens-Geräteportal auf.</span><span class="sxs-lookup"><span data-stu-id="e944a-110">Then record an MRC video in the HoloLens device portal.</span></span> 

## <a name="pv-camera"></a><span data-ttu-id="e944a-111">PV-Kamera</span><span class="sxs-lookup"><span data-stu-id="e944a-111">PV Camera</span></span>

<span data-ttu-id="e944a-112">Die Webcamtextur kann auch zur Laufzeit im Spiel abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="e944a-112">The webcam texture can also be retrieved in the game at runtime.</span></span>  <span data-ttu-id="e944a-113">Wenn Sie die Webcamtextur mit HoloLens verwenden möchten, vergewissern Sie sich zunächst im Unreal-Editor unter „Project Settings“ (Projekteinstellungen) > „Platform“ (Plattform) > „HoloLens“ > „Capabilities“ (Funktionen), dass das Kontrollkästchen für die Webcamfunktion aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="e944a-113">To get the webcam texture on HoloLens, first ensure the “Webcam” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span> 

<span data-ttu-id="e944a-114">Verwenden Sie die Funktion „StartCameraCapture“, um die Webcam zur Laufzeit zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="e944a-114">Opt into using the webcam at runtime with the StartCameraCapture function.</span></span>  <span data-ttu-id="e944a-115">Beenden Sie die Aufnahme mithilfe der Funktion „StopCameraCapture“.</span><span class="sxs-lookup"><span data-stu-id="e944a-115">Stop capturing with the StopCameraCapture function.</span></span> 

![Kamera: Starten/Beenden](images/unreal-camera-startstop.PNG)

<span data-ttu-id="e944a-117">Erstellen Sie zum Rendern des Kamerabilds zunächst eine dynamische Materialinstanz, die auf einem Material im Projekt basiert.</span><span class="sxs-lookup"><span data-stu-id="e944a-117">To render the camera image, first create a dynamic material instance based on a material in the project.</span></span>  <span data-ttu-id="e944a-118">In diesem Beispiel wird als Grundlage ein Material namens „PVCamMat“ verwendet.</span><span class="sxs-lookup"><span data-stu-id="e944a-118">In this case based on a material named PVCamMat.</span></span>  <span data-ttu-id="e944a-119">Legen Sie es auf eine Variable mit dem Typ „Material Instance Dynamic Object Reference“ (Materialinstanz mit dynamischem Objektverweis) fest.</span><span class="sxs-lookup"><span data-stu-id="e944a-119">Set this to a variable with type Material Instance Dynamic Object Reference.</span></span>  <span data-ttu-id="e944a-120">Legen Sie dann das Material des Objekts in der Szene, das zum Rendern des Kamerafeeds verwendet wird, auf diese neue dynamische Materialinstanz fest, und starten Sie einen Timer, der dazu dient, das Kamerabild an das Material zu binden.</span><span class="sxs-lookup"><span data-stu-id="e944a-120">Then set the material of the object in the scene that will render the camera feed to this new dynamic material instance and start a timer that will be used to bind the camera image to the material.</span></span> 

![Kamera: Rendern](images/unreal-camera-render.PNG)

<span data-ttu-id="e944a-122">Erstellen Sie eine neue Funktion für diesen Timer (in diesem Fall: MaterialTimer), und rufen Sie „GetARCameraImage“ auf, um die Textur von der Webcam abzurufen.</span><span class="sxs-lookup"><span data-stu-id="e944a-122">Create a new function for this timer, in this case MaterialTimer, and call GetARCameraImage to get the texture from the webcam.</span></span>  <span data-ttu-id="e944a-123">Ist diese Textur gültig, legen Sie im Shader einen Texturparameter auf dieses Bild fest.</span><span class="sxs-lookup"><span data-stu-id="e944a-123">If this texture is valid, set a texture parameter in the shader to this image.</span></span>  <span data-ttu-id="e944a-124">Falls nicht, starten Sie den Materialtimer erneut.</span><span class="sxs-lookup"><span data-stu-id="e944a-124">Otherwise, start the material timer again.</span></span> 

![Kamera: Textur](images/unreal-camera-texture.PNG)

<span data-ttu-id="e944a-126">Für das Material muss ein Parameter, der dem Namen in „SetTextureParameterValue“ entspricht, an einen Farbeintrag gebunden werden, damit das Kamerabild ordnungsgemäß angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e944a-126">The material should have a parameter matching the name in SetTextureParameterValue bound to a color entry to properly display the camera image.</span></span> 

![Kamera: Textur](images/unreal-camera-material.PNG)

## <a name="see-also"></a><span data-ttu-id="e944a-128">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e944a-128">See also</span></span>
* [<span data-ttu-id="e944a-129">Ausrichtbare Kamera</span><span class="sxs-lookup"><span data-stu-id="e944a-129">Locatable camera</span></span>](locatable-camera.md)
* [<span data-ttu-id="e944a-130">Mixed Reality-Aufnahme für Entwickler</span><span class="sxs-lookup"><span data-stu-id="e944a-130">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
