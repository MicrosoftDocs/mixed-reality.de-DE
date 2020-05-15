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
# <a name="hololens-camera-in-unreal"></a>HoloLens-Kamera in Unreal

## <a name="third-camera-mixed-reality-capture"></a>Mixed Reality-Aufnahme der dritten Kamera

Die Mixed Reality-Aufnahme (Mixed Reality Capture, MRC) der dritten Kamera kann verwendet werden, um eine Mixed Reality-Aufnahme aus der Perspektive der Kamera am HoloLens-Visor (anstelle der Perspektive der Augentexturen) zu rendern.  Dies ermöglicht eine bessere Abstimmung zwischen der realen Welt und den Hologrammen im MRC-Video. 

Wenn Sie die Mixed Reality-Aufnahme der dritten Kamera verwenden möchten, rufen Sie „SetEnabledMixedRealityCamera“ und „ResizeMixedRealityCamera“ mit den gewünschten Videodimensionen auf. 

![Dritte Kamera](images/unreal-camera-3rd.PNG)

Zeichnen Sie dann ein MRC-Video im HoloLens-Geräteportal auf. 

## <a name="pv-camera"></a>PV-Kamera

Die Webcamtextur kann auch zur Laufzeit im Spiel abgerufen werden.  Wenn Sie die Webcamtextur mit HoloLens verwenden möchten, vergewissern Sie sich zunächst im Unreal-Editor unter „Project Settings“ (Projekteinstellungen) > „Platform“ (Plattform) > „HoloLens“ > „Capabilities“ (Funktionen), dass das Kontrollkästchen für die Webcamfunktion aktiviert ist. 

Verwenden Sie die Funktion „StartCameraCapture“, um die Webcam zur Laufzeit zu aktivieren.  Beenden Sie die Aufnahme mithilfe der Funktion „StopCameraCapture“. 

![Kamera: Starten/Beenden](images/unreal-camera-startstop.PNG)

Erstellen Sie zum Rendern des Kamerabilds zunächst eine dynamische Materialinstanz, die auf einem Material im Projekt basiert.  In diesem Beispiel wird als Grundlage ein Material namens „PVCamMat“ verwendet.  Legen Sie es auf eine Variable mit dem Typ „Material Instance Dynamic Object Reference“ (Materialinstanz mit dynamischem Objektverweis) fest.  Legen Sie dann das Material des Objekts in der Szene, das zum Rendern des Kamerafeeds verwendet wird, auf diese neue dynamische Materialinstanz fest, und starten Sie einen Timer, der dazu dient, das Kamerabild an das Material zu binden. 

![Kamera: Rendern](images/unreal-camera-render.PNG)

Erstellen Sie eine neue Funktion für diesen Timer (in diesem Fall: MaterialTimer), und rufen Sie „GetARCameraImage“ auf, um die Textur von der Webcam abzurufen.  Ist diese Textur gültig, legen Sie im Shader einen Texturparameter auf dieses Bild fest.  Falls nicht, starten Sie den Materialtimer erneut. 

![Kamera: Textur](images/unreal-camera-texture.PNG)

Für das Material muss ein Parameter, der dem Namen in „SetTextureParameterValue“ entspricht, an einen Farbeintrag gebunden werden, damit das Kamerabild ordnungsgemäß angezeigt wird. 

![Kamera: Textur](images/unreal-camera-material.PNG)

## <a name="see-also"></a>Siehe auch
* [Ausrichtbare Kamera](locatable-camera.md)
* [Mixed Reality-Aufnahme für Entwickler](mixed-reality-capture-for-developers.md)
