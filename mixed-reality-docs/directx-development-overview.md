---
title: Übersicht über die Entwicklung von DirectX
description: Erstellen eine DirectX-basierten mixed Reality-Engine, die die Windows Mixed Reality-APIs direkt verwenden.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Rendern von DirectX, holographic, systemeigene, systemeigene app WinRT, WinRT-app-Plattform-APIs, benutzerdefinierte Engine middleware
ms.openlocfilehash: da6beae6e256fef49481b581395e507b3f2acd04
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414383"
---
# <a name="directx-development-overview"></a>Übersicht über die Entwicklung von DirectX


Windows Mixed Reality-Anwendungen verwenden die [holographic Rendering](rendering.md), [bestaunen](gaze.md), [Geste](gestures.md), [Motion-Controller](motion-controllers.md), [Voice](voice-input.md), und [räumliche Zuordnung](spatial-mapping.md) APIs zum Erstellen [mixed Reality](mixed-reality.md) für HoloLens und immersive Headsets auftritt. Sie mixed Reality-Anwendungen, die diese 3D-Engine, z. B. mit erstellen [Unity](unity-development-overview.md), oder Sie können direkt auf den gemischten Windows-APIs Realität mit DirectX 11 oder DirectX 12. Wenn Sie die Plattform direkt nutzen, werden Sie im Grunde Ihre eigene Middleware oder ein Framework erstellen. Die Windows-APIs unterstützen Anwendungen, die in beiden geschrieben C++ und C#. Wenn Sie auch verwenden C#, kann Ihre Anwendung nutzen, die ["sharpdx"](http://sharpdx.org/) open-Source-Softwarebibliothek.


Unterstützt die Windows Mixed Reality [zwei Arten von apps](app-views.md):
* **Mixed Reality-Anwendungen** ("UWP" oder "Win32") verwenden, die die [HolographicSpace-API](getting-a-holographicspace.md) zum Rendern einer [immersive Ansicht](app-views.md) für den Benutzer, die die Kopfhörer Anzeige ausfüllt.
* **2D apps** (UWP), DirectX, XAML, oder verwenden andere Frameworks zum Rendern [2D Ansichten](app-views.md#2d-views) auf Slate-PCs in der Windows Mixed Reality home.


Die Unterschiede zwischen der Entwicklung von DirectX für [2D- und immersive Ansichten](app-views.md) sind in erster Linie im Zusammenhang mit holographic Rendering und räumliche Eingabe. Ihrer UWP-Anwendung ["iframeworkview"](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) oder HWND für Ihre Win32-Anwendung erforderlich sind, und bleiben Sie größtenteils gleich, wie die WinRT-APIs für Ihre Anwendung verfügbar. Allerdings müssen Sie eine andere Teilmenge dieser APIs verwenden, um holographic Funktionen nutzen. Beispielsweise wird die SwapChain vom System für holographic Appslications verwaltet. Arbeiten Sie mit der HolographicSpace-API verwenden, anstatt die DXGI an [präsentieren Frames](rendering-in-directx.md).

Zum Einstieg in die Entwicklung von interaktiven Anwendungen:
* Für **UWP-apps**, [Erstellen eines neuen UWP-Projekts mit den Vorlagen in Visual Studio](creating-a-holographic-directx-project.md). Abhängig von Ihrer Sprache, **Visual C++**  oder **Visual C#** , finden Sie die UWP-Vorlagen unter **Windows Universal**  >   **Holographic**.
* Für **Win32-Anwendungen**, [Starten über die *BasicHologram* Win32-Beispiel](creating-a-holographic-directx-project.md#creating-a-win32-project).

Dies ist eine hervorragende Möglichkeit, den Code zu erhalten, den Sie eine vorhandene Anwendung oder ein Modul holographic Renderingunterstützung hinzufügen müssen. Code und Konzepte werden in der Vorlage in einer Weise angezeigt, die für alle Entwickler, der in Echtzeit interaktive Software vertraut ist.


## <a name="getting-started"></a>Erste Schritte

Die folgenden Themen behandeln die grundlegenden Anforderungen von Middleware DirectX-basierten Windows Mixed Reality-Unterstützung hinzugefügt:

* [Erstellen eines holographic DirectX-Projekts](creating-a-holographic-directx-project.md): Die Vorlage holographic-Anwendung, die zusammen mit der Dokumentation erfahren Sie, die Unterschiede zwischen was Sie sich gewöhnt sowie den speziellen Anforderungen von einem Gerät, das entworfen wurde, um funktionsfähig sind, während auf den Kopf geführt eingeführt.
* [Abrufen einer HolographicSpace](getting-a-holographicspace.md): Sie müssen zuerst eine HolographicSpace zu erstellen, die Ihre Anwendung die Sequenz der HolographicFrame Objekte bereitstellt, die jede Head Position darstellen, aus der Sie gerendert werden.
* [Rendern in DirectX](rendering-in-directx.md): Da eine holographic SwapChain zwei Renderziele aufweist, müssen Sie auf die Möglichkeit, einige Änderungen vornehmen, die Anwendung rendert.
* [Koordinatensysteme im DirectX](coordinate-systems-in-directx.md): Windows Mixed Reality erlernt und aktualisiert seine Verständnis der Welt führt der Benutzer auf. Dadurch werden räumliche Koordinatensysteme Anwendungen verwenden, um verständlich des Benutzers-Umgebung, einschließlich der räumlichen Anker und des Benutzers definiert, räumliche Phase.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Hinzufügen von mixed Reality-Funktionen und Eingaben

Um die bestmögliche Leistung für Benutzer von Ihrem immersive Appslication zu aktivieren, sollten Sie die folgenden wichtigsten Bausteine zu unterstützen:

* [Anvisieren mit dem Kopf und mit den Augen in DirectX](gaze-in-directx.md)
* [Hände und Motion-Controller in DirectX](hands-and-motion-controllers-in-directx.md)
* [Spracheingabe in DirectX](voice-input-in-directx.md)
* [Raumklang in DirectX](spatial-sound-in-directx.md)
* [Räumliche Abbildung in DirectX](spatial-mapping-in-directx.md)


Es gibt andere wichtige Features, die viele immersive Anwendungen verwenden möchten, die auch für DirectX-Anwendungen verfügbar gemacht werden:

* [Gemeinsame Raumanker in DirectX](shared-spatial-anchors-in-directx.md)
* [Ausrichtbare Kamera in DirectX](locatable-camera-in-directx.md)
* [Tastatur-, Maus- und Controllereingaben in DirectX](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>Siehe auch
* [App-Modell](app-model.md)
* [App-Ansichten](app-views.md)
