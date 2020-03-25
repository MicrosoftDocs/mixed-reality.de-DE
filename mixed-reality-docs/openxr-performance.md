---
title: Openxr-Leistung
description: Debuggen Sie die GPU-Leistung Ihrer openxr-Anwendungen.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: Openxr, Khronos, basicxrapp, DirectX, Native, Native APP, benutzerdefiniertes Modul, Middleware, Leistung, Optimierung, GPU-Debugging, renderdoc, pix
ms.openlocfilehash: 717dc2d534773bd28f5ad2d5c3720bf4177a1480
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163344"
---
# <a name="openxr-performance"></a>Openxr-Leistung

Auf hololens 2 gibt es eine Reihe von Möglichkeiten, Kompositions Daten über `xrEndFrame` zu senden, was zu einer Nachbearbeitung führt, die eine spürbare Leistungs Einbuße verursachen wird.
Um Leistungsdaten zu vermeiden, [Senden Sie eine einzelne `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) mit den folgenden Merkmalen:
* [Verwenden eines Textur Arrays vorhandenes SwapChain](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [Verwenden des Haupt Farb-vorhandenes SwapChain-Formats](openxr-best-practices.md#select-a-swapchain-format)
* [Empfohlene Anzeige Dimensionen verwenden](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* Legen Sie das `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT`-Flag nicht fest.
* Legen Sie den `XrCompositionLayerDepthInfoKHR` `minDepth` auf 0,0 f fest, und `maxDepth` auf 1.0 f.

Weitere Überlegungen führen zu einer besseren Leistung:
* [Verwenden des 16-Bit-Tiefen Formats](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [Erstellen von instanziierten zeichnen-aufrufen](openxr-best-practices.md#render-with-texture-array-and-vprt)
