---
title: Übersicht über die Entwicklung von JavaScript Mixed Reality
description: Übersicht über die Entwicklung gemischter Realität mithilfe von JavaScript für Web-, Mobile und Windows-immersive Headsets.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: Webxr, winmr, webar, webvr, windowsmixedreality, hololens, Windows Mixed Reality, Web VR, Web XR, Web Mr, Web AR, 360, 360 Video, 360 Videos, 360 Photo, 360 Fotos, 360 Content, immersives Web, immersive-Web, IW, immersiveweb
ms.openlocfilehash: a1288e8f477f42b0937e797623fb83fe8f63685c
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835609"
---
# <a name="mixed-reality-development-with-javascript-overview"></a>Mixed Reality-Entwicklung mit JavaScript (Übersicht)

## <a name="mixed-reality-applications-on-the-web"></a>Gemischte Reality-Anwendungen im Web

Mixed Reality-Features sind im Web verfügbar, indem [webxr-Geräte-APIs](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API) und als [veraltet markierte webvr-APIs](webxr-overview.md)verwendet werden. Browser, die keine vollständigen webxr-Features unterstützen, können [webxr-polyfills](https://github.com/immersive-web/webxr-polyfill) zu Ihrer Website hinzufügen.

## <a name="what-is-webxr-polyfill"></a>Was ist webxr Polyfill?

Eine JavaScript-Implementierung der webxr-Geräte-API sowie das webxr-Gamepad-Modul. Dieses Polyfill ermöglicht Entwicklern das Schreiben anhand der neuesten Spezifikation, das Bereitstellen von Unterstützung, wenn Sie auf Browsern ausgeführt werden, die die webvr 1,1-Spezifikation implementieren, oder auf mobilen Geräten ohne webvr/webxr-Unterstützung.

## <a name="javascript-libraries-to-build-mixed-reality-applications-on-the-web"></a>JavaScript-Bibliotheken zum Erstellen gemischter Reality-Anwendungen im Web

## <a name="babylonjs"></a>Babylon. js

Babylon ist ein JavaScript-3D-Modul, das die Entwicklung von 3D-Inhalten und immersiven Anwendungen erleichtert. Vor den ersten Schritten mit immersiven Anwendungen empfiehlt es sich, die Grundlagen der Entwicklung von Babylon. js zu erlernen.

Erfahren Sie, wie Sie im [Abschnitt "Getting Started](https://doc.babylonjs.com/)" eine Mixed Reality-Anwendung mit Babylon erstellen. Spielen Sie mit den 3D-Beispielen und dem zugehörigen Quellcode unter Verwendung von [Babylon Playground](https://doc.babylonjs.com/examples/). Machen Sie sich mit der Entwicklung gemischter Realität im [Abschnitt webxr](https://doc.babylonjs.com/how_to/introduction_to_webxr) der Dokumentation vertraut. 

## <a name="a-frame"></a>A-Frame

Ein-Frame ist ein deklaratives JavaScript-Framework für den Einstieg in die virtuelle Realität im Web. Weitere Informationen finden Sie in der [Dokumentation zum A-Frame](https://aframe.io/) .

## <a name="threejs"></a>Drei. js

Drei. js ist eine beliebte 3D-Bibliothek zum Erstellen von immersiven Erfahrungen. Weitere Informationen zu [drei. js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) finden Sie auf der Dokumentationsseite und in den [Beispielen](https://threejs.org/examples/#webgl_animation_cloth).

## <a name="webgl"></a>WebGL

Mithilfe von WebGL-APIs können Sie direkt auf die webxr-Geräte-APIs zugreifen. WebGL (Webgrafik Bibliothek) ist eine JavaScript-API zum Rendern von hochleistungsfähigen interaktiven 3D-und 2D-Grafiken innerhalb eines kompatiblen Webbrowsers ohne Verwendung von Plug-ins. Weitere Informationen zu den [WebGL-APIs](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)finden Sie unter.

## <a name="mixed-reality-native-mobile-applications-using-javascript"></a>Native Mobile Anwendungen mit JavaScript in gemischter Realität

Mit der Hilfe von wenigen JavaScript-Bibliotheken können Sie Ihre Umgebungen mit gemischter Realität einmalig schreiben und für Web-und Native Plattformen wie Windows Mixed Reality-Headsets, Android-und IOS-Geräte bereitstellen.

## <a name="babylon-native"></a>Nativer Babylon

Die Native Plattform von [Babylon](https://www.babylonjs.com/native/) ermöglicht jedem Benutzer, seinen Babylon. js-Code zu erstellen und eine native Anwendung zu erstellen, wodurch die Leistungsfähigkeit nativer Technologien entsperrt wird. Sie können [Babylon Native auf GitHub](https://github.com/BabylonJS/BabylonNative) herunterladen und im [Blog von Babylon. js](https://medium.com/@babylonjs/babylon-native-821f1694fffc)mehr darüber erfahren.

## <a name="react-native"></a>React Native

"System eigen [" ist eine](https://reactnative.dev/) andere Open Source-Bibliothek, die Entwicklern das Erstellen mit JavaScript und die Bereitstellung auf mehreren Plattformen ermöglicht. Sie können [auf GitHub auf GitHub reagieren](https://github.com/facebook/react-native) und mehr darüber erfahren, wie im systemeigenen [Blog von reagieren](https://reactnative.dev/blog/).

## <a name="see-also"></a>Weitere Informationen

* [Übersicht über webxr](webxr-overview.md)
* [Webxr-Geräte-API-Spezifikation](https://immersive-web.github.io/webxr/)
* [Dokumentation zur webxr-Geräte-API](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb. dev](https://immersiveweb.dev/)
* [Webxr-Beispiele](https://immersive-web.github.io/webxr-samples/)
* [Verwenden von "Babylon. js" zum Erstellen von webxr-Erfahrungen](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Windows Mixed Reality und die neue Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [Immersives Web-W3C GitHub](https://github.com/immersive-web)
* [WebGL-API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* [Gamepad-API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) -und [Gamepad-Erweiterungen](https://w3c.github.io/gamepad/extensions.html)
* [Übersicht über webvr](webvr-overview.md)
