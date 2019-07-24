---
title: Verwenden von webvr in Microsoft Edge mit Windows Mixed Reality
description: Übersicht über die Verwendung und Entwicklung für webvr in Windows Mixed Reality
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: Webvr, webxr, winmr, webar, Web VR, Web XR, Web Mr, Web AR, 360, 360 Video, 360 Videos, 360 Photo, 360 Fotos, 360 Content, immersives Web, immersiveweb, IW
ms.openlocfilehash: fab17f4dcecc34d8f1ca4836dce6de90522899cd
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548756"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a><span data-ttu-id="b993d-104">Verwenden von webvr in Microsoft Edge mit Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b993d-104">Using WebVR in Microsoft Edge with Windows Mixed Reality</span></span>

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="b993d-105">Erstellen von webvr-Inhalten für Windows Mixed Reality-immersive Headsets</span><span class="sxs-lookup"><span data-stu-id="b993d-105">Creating WebVR content for Windows Mixed reality immersive headsets</span></span>

<span data-ttu-id="b993d-106">Webvr 1,1 ist ab Windows 10 Fall Creators Update in Microsoft Edge verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b993d-106">WebVR 1.1 is available in Microsoft Edge beginning with the Windows 10 Fall Creators Update.</span></span> <span data-ttu-id="b993d-107">Entwickler können diese API jetzt verwenden, um immersive VR-Erfahrungen im Web zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b993d-107">Developers can now use this API to create immersive VR experiences on the web.</span></span>

<span data-ttu-id="b993d-108">Die webvr-API stellt HMD-Daten auf der Seite bereit, die verwendet werden können, um eine Stereo-WebGL-Szene zurück in den HMD zu Rendering.</span><span class="sxs-lookup"><span data-stu-id="b993d-108">The WebVR API provides HMD pose data to the page which can be used to render a stereo WebGL scene back to the HMD.</span></span> <span data-ttu-id="b993d-109">Details zur API-Unterstützung finden Sie auf der [Seite Status der Microsoft Edge-Plattform](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span><span class="sxs-lookup"><span data-stu-id="b993d-109">Details on API support is available on the [Microsoft Edge Platform Status page](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span></span> <span data-ttu-id="b993d-110">Die webvr-API-Oberfläche ist jederzeit in Microsoft Edge vorhanden.</span><span class="sxs-lookup"><span data-stu-id="b993d-110">The WebVR API surface area is present at all times within Microsoft Edge.</span></span> <span data-ttu-id="b993d-111">Beim Aufrufen von "getvrdisplays ()" wird jedoch nur ein Headset zurückgegeben, wenn entweder ein Headset angeschlossen ist oder der Simulator eingeschaltet wurde.</span><span class="sxs-lookup"><span data-stu-id="b993d-111">However, a call to getVRDisplays() will only return a headset if either a headset is plugged in or the simulator has been turned on.</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="b993d-112">Anzeigen von webvr-Inhalten in Windows Mixed Reality-immersiven Headsets</span><span class="sxs-lookup"><span data-stu-id="b993d-112">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="b993d-113">Anweisungen für den Zugriff auf webvr-Inhalte in Ihrem immersiven Headset finden Sie im [Leitfaden für Enthusiasten](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span><span class="sxs-lookup"><span data-stu-id="b993d-113">Instructions for accessing WebVR content in your immersive headset can be found in the [Enthusiast's Guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="b993d-114">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b993d-114">See Also</span></span>
* [<span data-ttu-id="b993d-115">Webvr-Informationen</span><span class="sxs-lookup"><span data-stu-id="b993d-115">WebVR information</span></span>](http://webvr.info)
* [<span data-ttu-id="b993d-116">Webvr-Spezifikation</span><span class="sxs-lookup"><span data-stu-id="b993d-116">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="b993d-117">[Webvr-API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="b993d-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span></span>
* <span data-ttu-id="b993d-118">[WebGL-API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="b993d-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="b993d-119">[Gamepad-API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) -und [Gamepad-Erweiterungen](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="b993d-119">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="b993d-120">Umgang mit verlorenem Kontext in WebGL</span><span class="sxs-lookup"><span data-stu-id="b993d-120">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="b993d-121">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="b993d-121">Pointerlock</span></span>](http://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="b993d-122">gltf</span><span class="sxs-lookup"><span data-stu-id="b993d-122">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="b993d-123">Verwenden von "Babylon. js" zum Aktivieren von webvr</span><span class="sxs-lookup"><span data-stu-id="b993d-123">Using Babylon.js to enable WebVR</span></span>](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

