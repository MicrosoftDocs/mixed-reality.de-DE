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
# <a name="openxr-performance"></a><span data-ttu-id="19068-104">Openxr-Leistung</span><span class="sxs-lookup"><span data-stu-id="19068-104">OpenXR performance</span></span>

<span data-ttu-id="19068-105">Auf hololens 2 gibt es eine Reihe von Möglichkeiten, Kompositions Daten über `xrEndFrame` zu senden, was zu einer Nachbearbeitung führt, die eine spürbare Leistungs Einbuße verursachen wird.</span><span class="sxs-lookup"><span data-stu-id="19068-105">On HoloLens 2, there are a number of ways to submit composition data through `xrEndFrame` which will result in post-processing that will have a noticeable performance penalty.</span></span>
<span data-ttu-id="19068-106">Um Leistungsdaten zu vermeiden, [Senden Sie eine einzelne `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) mit den folgenden Merkmalen:</span><span class="sxs-lookup"><span data-stu-id="19068-106">To avoid performance penalities, [submit a single `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) with the following characteristics:</span></span>
* [<span data-ttu-id="19068-107">Verwenden eines Textur Arrays vorhandenes SwapChain</span><span class="sxs-lookup"><span data-stu-id="19068-107">Use a texture array swapchain</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [<span data-ttu-id="19068-108">Verwenden des Haupt Farb-vorhandenes SwapChain-Formats</span><span class="sxs-lookup"><span data-stu-id="19068-108">Use the primary color swapchain format</span></span>](openxr-best-practices.md#select-a-swapchain-format)
* [<span data-ttu-id="19068-109">Empfohlene Anzeige Dimensionen verwenden</span><span class="sxs-lookup"><span data-stu-id="19068-109">Use the recommended view dimensions</span></span>](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* <span data-ttu-id="19068-110">Legen Sie das `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT`-Flag nicht fest.</span><span class="sxs-lookup"><span data-stu-id="19068-110">Do not set the `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag</span></span>
* <span data-ttu-id="19068-111">Legen Sie den `XrCompositionLayerDepthInfoKHR` `minDepth` auf 0,0 f fest, und `maxDepth` auf 1.0 f.</span><span class="sxs-lookup"><span data-stu-id="19068-111">Set the `XrCompositionLayerDepthInfoKHR` `minDepth` to 0.0f and `maxDepth` to 1.0f</span></span>

<span data-ttu-id="19068-112">Weitere Überlegungen führen zu einer besseren Leistung:</span><span class="sxs-lookup"><span data-stu-id="19068-112">Additional considerations will result in better performance:</span></span>
* [<span data-ttu-id="19068-113">Verwenden des 16-Bit-Tiefen Formats</span><span class="sxs-lookup"><span data-stu-id="19068-113">Use the 16-bit depth format</span></span>](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [<span data-ttu-id="19068-114">Erstellen von instanziierten zeichnen-aufrufen</span><span class="sxs-lookup"><span data-stu-id="19068-114">Make instanced draw calls</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
