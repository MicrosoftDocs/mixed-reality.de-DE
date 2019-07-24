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
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a>Verwenden von webvr in Microsoft Edge mit Windows Mixed Reality

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a>Erstellen von webvr-Inhalten für Windows Mixed Reality-immersive Headsets

Webvr 1,1 ist ab Windows 10 Fall Creators Update in Microsoft Edge verfügbar. Entwickler können diese API jetzt verwenden, um immersive VR-Erfahrungen im Web zu erstellen.

Die webvr-API stellt HMD-Daten auf der Seite bereit, die verwendet werden können, um eine Stereo-WebGL-Szene zurück in den HMD zu Rendering. Details zur API-Unterstützung finden Sie auf der [Seite Status der Microsoft Edge-Plattform](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/). Die webvr-API-Oberfläche ist jederzeit in Microsoft Edge vorhanden. Beim Aufrufen von "getvrdisplays ()" wird jedoch nur ein Headset zurückgegeben, wenn entweder ein Headset angeschlossen ist oder der Simulator eingeschaltet wurde.

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a>Anzeigen von webvr-Inhalten in Windows Mixed Reality-immersiven Headsets

Anweisungen für den Zugriff auf webvr-Inhalte in Ihrem immersiven Headset finden Sie im [Leitfaden für Enthusiasten](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).

## <a name="see-also"></a>Siehe auch
* [Webvr-Informationen](http://webvr.info)
* [Webvr-Spezifikation](https://w3c.github.io/webvr/)
* [Webvr-API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)
* [WebGL-API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* [Gamepad-API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) -und [Gamepad-Erweiterungen](https://w3c.github.io/gamepad/extensions.html)
* [Umgang mit verlorenem Kontext in WebGL](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](http://www.w3.org/TR/pointerlock/)
* [gltf](https://www.khronos.org/gltf)
* [Verwenden von "Babylon. js" zum Aktivieren von webvr](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

