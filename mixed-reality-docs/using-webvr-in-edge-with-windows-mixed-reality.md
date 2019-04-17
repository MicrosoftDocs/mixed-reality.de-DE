---
title: Mithilfe von WebVR in Microsoft Edge mit Windows Mixed Reality
description: Übersicht über die Verwendung und Entwicklung für WebVR in Windows Mixed Reality
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: WebVR, WebXR, WinMR, WebAR, Vr web, Xr-web-, web-Mr, web-Ar, 360 360 Video, 360 Videos, 360 Foto, 360 Fotos, 360-Inhalte, faszinierende Web, Immersiveweb, IT-Mitarbeiter
ms.openlocfilehash: fab17f4dcecc34d8f1ca4836dce6de90522899cd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604635"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a><span data-ttu-id="3952e-104">Mithilfe von WebVR in Microsoft Edge mit Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3952e-104">Using WebVR in Microsoft Edge with Windows Mixed Reality</span></span>

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="3952e-105">Erstellen von WebVR-Inhalt für Windows Mixed Reality-immersive headsets</span><span class="sxs-lookup"><span data-stu-id="3952e-105">Creating WebVR content for Windows Mixed reality immersive headsets</span></span>

<span data-ttu-id="3952e-106">WebVR 1.1 ist in Microsoft Edge, beginnend mit der Windows 10 Fall Creators Update verfügbar.</span><span class="sxs-lookup"><span data-stu-id="3952e-106">WebVR 1.1 is available in Microsoft Edge beginning with the Windows 10 Fall Creators Update.</span></span> <span data-ttu-id="3952e-107">Entwickler können jetzt diese API verwenden, im Web immersive VR-weberfahrungen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3952e-107">Developers can now use this API to create immersive VR experiences on the web.</span></span>

<span data-ttu-id="3952e-108">Die WebVR-API bietet HMD Haltung Daten auf der Seite, die zum Rendern einer Stereoanlage WebGL-Szene an die HMD verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="3952e-108">The WebVR API provides HMD pose data to the page which can be used to render a stereo WebGL scene back to the HMD.</span></span> <span data-ttu-id="3952e-109">Informationen zur API-Unterstützung steht auf der [Microsoft Edge-Plattform-Statusseite](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span><span class="sxs-lookup"><span data-stu-id="3952e-109">Details on API support is available on the [Microsoft Edge Platform Status page](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span></span> <span data-ttu-id="3952e-110">WebVR API-Oberfläche, die immer in Microsoft Edge vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3952e-110">The WebVR API surface area is present at all times within Microsoft Edge.</span></span> <span data-ttu-id="3952e-111">Allerdings wird ein Aufruf von getVRDisplays() nur einen Kopfhörer zurück, wenn es sich bei einen Kopfhörer angeschlossen ist, oder der Simulator war eingeschaltet.</span><span class="sxs-lookup"><span data-stu-id="3952e-111">However, a call to getVRDisplays() will only return a headset if either a headset is plugged in or the simulator has been turned on.</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="3952e-112">Anzeige von WebVR-Inhalten in Windows Mixed Reality immersive headsets</span><span class="sxs-lookup"><span data-stu-id="3952e-112">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="3952e-113">Anweisungen für den Zugriff auf WebVR-Inhalten in Ihre immersive Kopfhörer finden Sie der [Enthusiast Handbuch](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span><span class="sxs-lookup"><span data-stu-id="3952e-113">Instructions for accessing WebVR content in your immersive headset can be found in the [Enthusiast's Guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="3952e-114">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3952e-114">See Also</span></span>
* [<span data-ttu-id="3952e-115">WebVR-Informationen</span><span class="sxs-lookup"><span data-stu-id="3952e-115">WebVR information</span></span>](http://webvr.info)
* [<span data-ttu-id="3952e-116">WebVR-Spezifikation</span><span class="sxs-lookup"><span data-stu-id="3952e-116">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="3952e-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="3952e-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span></span>
* <span data-ttu-id="3952e-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="3952e-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="3952e-119">[Gamepad-API-](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) und [Gamepad-Erweiterungen](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="3952e-119">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="3952e-120">Behandlung von Kontext in WebGL verloren</span><span class="sxs-lookup"><span data-stu-id="3952e-120">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="3952e-121">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="3952e-121">Pointerlock</span></span>](http://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="3952e-122">glTF</span><span class="sxs-lookup"><span data-stu-id="3952e-122">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="3952e-123">Verwenden von Babylon.js für WebVR</span><span class="sxs-lookup"><span data-stu-id="3952e-123">Using Babylon.js to enable WebVR</span></span>](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

