---
title: Verwenden von webxr mit Windows Mixed Reality
description: Übersicht über die Verwendung und Entwicklung für webxr in Windows Mixed Reality
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: Webxr, winmr, webar, webvr, windowsmixedreality, hololens, Windows Mixed Reality, Web VR, Web XR, Web Mr, Web AR, 360, 360 Video, 360 Videos, 360 Photo, 360 Fotos, 360 Content, immersives Web, immersiveweb, IW
ms.openlocfilehash: 01e6cd44e9879cd7fd9b11e178134eaf364cc53c
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278441"
---
# <a name="webxr-overview"></a><span data-ttu-id="828b2-104">Übersicht über webxr</span><span class="sxs-lookup"><span data-stu-id="828b2-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="828b2-105">Was ist webxr?</span><span class="sxs-lookup"><span data-stu-id="828b2-105">What is WebXR</span></span>

<span data-ttu-id="828b2-106">Die **webxr-Geräte-API** ist für den Zugriff auf die Geräte der **virtuellen Realität (VR)** und der **erweiterten Realität (AR)** , einschließlich **Sensoren** und auf dem **Web** **eingebundenes anzeigen** .</span><span class="sxs-lookup"><span data-stu-id="828b2-106">The **WebXR device API** is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="828b2-107">Die webxr-Geräte-API ist zurzeit auf Microsoft Edge verfügbar, und die Chrome-Version 79 und höhere Versionen unterstützen webxr als Standard.</span><span class="sxs-lookup"><span data-stu-id="828b2-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="828b2-108">Den neuesten Browser-Support Status für webxr finden Sie unter [caniuse.com](https://caniuse.com/#search=webxr).</span><span class="sxs-lookup"><span data-stu-id="828b2-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

<span data-ttu-id="828b2-109">Erfahren Sie mehr über die [gemischte Windows-Realität und den neuen Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)in den [Neuerungen](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide) .</span><span class="sxs-lookup"><span data-stu-id="828b2-109">Learn more about the [Windows Mixed Reality and the new Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)in [What's new](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide) section.</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="828b2-110">Anzeigen von webxr</span><span class="sxs-lookup"><span data-stu-id="828b2-110">Viewing WebXR</span></span>

<span data-ttu-id="828b2-111">Um zu testen, ob Ihr Browser webxr unterstützt, können Sie in Ihrem Browser zu [webxr-Beispielen](https://immersive-web.github.io/webxr-samples/) navigieren.</span><span class="sxs-lookup"><span data-stu-id="828b2-111">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="828b2-112">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="828b2-112">See Also</span></span>

* [<span data-ttu-id="828b2-113">Webxr-Geräte-API-Spezifikation</span><span class="sxs-lookup"><span data-stu-id="828b2-113">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="828b2-114">Dokumentation zur webxr-Geräte-API</span><span class="sxs-lookup"><span data-stu-id="828b2-114">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="828b2-115">Immersiveweb. dev</span><span class="sxs-lookup"><span data-stu-id="828b2-115">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="828b2-116">Webxr-Beispiele</span><span class="sxs-lookup"><span data-stu-id="828b2-116">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="828b2-117">Windows Mixed Reality und die neue Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="828b2-117">Windows Mixed Reality and the new Microsoft Edge</span></span>](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="828b2-118">Immersives Web-W3C GitHub</span><span class="sxs-lookup"><span data-stu-id="828b2-118">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="828b2-119">[WebGL-API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="828b2-119">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="828b2-120">[Gamepad-API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) -und [Gamepad-Erweiterungen](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="828b2-120">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="828b2-121">Umgang mit verlorenem Kontext in WebGL</span><span class="sxs-lookup"><span data-stu-id="828b2-121">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="828b2-122">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="828b2-122">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="828b2-123">gltf</span><span class="sxs-lookup"><span data-stu-id="828b2-123">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="828b2-124">Verwenden von "Babylon. js" zum Erstellen von webxr-Erfahrungen</span><span class="sxs-lookup"><span data-stu-id="828b2-124">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="828b2-125">Immersive Web-Community-Gruppe</span><span class="sxs-lookup"><span data-stu-id="828b2-125">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)
