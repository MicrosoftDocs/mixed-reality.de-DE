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
# <a name="hololens-photovideo-camera-in-unreal"></a>HoloLens-Foto-/Videokamera in Unreal

HoloLens verfügt über eine Foto-/Videokamera (FV), die einerseits für die Mixed Reality-Aufnahme (Mixed Reality Capture, MRC) und andererseits von einer App zum Zugriff auf visuelle Elemente der realen Welt verwendet werden kann.

## <a name="render-from-the-pv-camera-for-mrc"></a>Rendering von der FV-Kamera für MRC

> [!NOTE]
> Dafür ist **Unreal Engine 4.25** oder höher erforderlich.

Das System und benutzerdefinierte MRC-Rekorder erstellen Mixed Reality-Aufnahmen, indem sie die FV-Kamera mit Hologrammen kombinieren, die von der immersiven App gerendert werden.

Standardmäßig wird für die Mixed-Reality-Aufnahme die holografische Ausgabe des rechten Auges verwendet. Wenn eine immersive App hingegen [von der FV-Kamera rendert](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), wird stattdessen diese verwendet. Dies ermöglicht eine bessere Abstimmung zwischen der realen Welt und den Hologrammen im MRC-Video.

So abonnieren Sie das Rendering von der FV-Kamera:

1. Rufen Sie **SetEnabledMixedRealityCamera** und **ResizeMixedRealityCamera** auf.
    * Verwenden Sie die Werte **Size X** (Größe X) und **Size Y** (Größe Y), um die Videoabmessungen festzulegen.

![Dritte Kamera](images/unreal-camera-3rd.PNG)

Unreal verarbeitet dann Anforderungen von MRC, aus der Perspektive der FV-Kamera zu rendern.

> [!NOTE]
> Nur wenn [Mixed Reality Capture](mixed-reality-capture.md) (Mixed Reality-Aufnahme) ausgelöst wird, wird die App aufgefordert, aus der Perspektive der Foto-/Videokamera zu rendern.

## <a name="using-the-pv-camera"></a>Verwenden der FV-Kamera

Die Webcam-Textur kann im Spiel zur Laufzeit abgerufen werden, dies muss jedoch im Editor unter **Edit > Project Settings** (Bearbeiten > Projekteinstellungen) aktiviert werden:
1. Wechseln Sie zu **Platforms > HoloLens > Capabilities** (Plattformen > HoloLens > Funktionen), und aktivieren Sie **Webcam**.
    * Verwenden Sie die Funktion **StartCameraCapture**, um die Webcam zur Laufzeit zu nutzen, und die Funktion **StopCameraCapture**, um die Aufzeichnung zu beenden.

![Kamera: Starten/Beenden](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a>Rendern eines Bilds
So wird das Kamerabild gerendert:
1. Erstellen Sie auf der Grundlage eines Materials im Projekt eine dynamische Materialinstanz, die im Screenshot unten den Namen **PVCamMat** trägt.  
2. Legen Sie die dynamische Materialinstanz auf eine **Material Instance Dynamic Object Reference**-Variable (Materialinstanz mit dynamischem Objektverweis) fest.  
3. Legen Sie das Material des Objekts in der Szene, das den Kamerafeed rendern soll, auf diese neue dynamische Materialinstanz fest.
    * Starten Sie einen Timer, der dazu verwendet wird, das Kamerabild an das Material zu binden. 

![Kamera: Rendern](images/unreal-camera-render.PNG)

4. Erstellen Sie eine neue Funktion für diesen Timer (in diesem Fall: **MaterialTimer**), und rufen Sie **GetARCameraImage** auf, um die Textur von der Webcam abzurufen.  
5. Ist diese Textur gültig, legen Sie im Shader einen Texturparameter auf dieses Bild fest.  Falls nicht, starten Sie den Materialtimer erneut. 

![Kamera: Textur](images/unreal-camera-texture.PNG)

5. Achten Sie darauf, dass das Material über einen Parameter verfügt, der mit dem Namen in **SetTextureParameterValue** übereinstimmt, der an einen Farbeintrag gebunden ist. Ohne dies kann das Kamerabild nicht ordnungsgemäß angezeigt werden.

![Kamera: Textur](images/unreal-camera-material.PNG)

## <a name="see-also"></a>Siehe auch
* [Ausrichtbare Kamera](locatable-camera.md)
* [Mixed Reality-Aufnahme für Entwickler](mixed-reality-capture-for-developers.md)
