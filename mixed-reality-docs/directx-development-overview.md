---
title: Übersicht über die Entwicklung von DirectX
description: Erstellen eine DirectX-basierten mixed Reality-Engine, die die Windows Mixed Reality-APIs direkt verwenden.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Rendern von DirectX, holographic, systemeigene, systemeigene app WinRT, WinRT-app-Plattform-APIs, benutzerdefinierte Engine middleware
ms.openlocfilehash: 60c4de7025099f38f0902e2ff24579e7088835a6
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65628991"
---
# <a name="directx-development-overview"></a>Übersicht über die Entwicklung von DirectX

Windows Mixed Reality-apps verwenden die [holographic Rendering](rendering.md), [bestaunen](gaze.md), [Geste](gestures.md), [Motion-Controller](motion-controllers.md), [Stimme ](voice-input.md) und [räumliche Zuordnung](spatial-mapping.md) APIs zum Erstellen [mixed Reality](mixed-reality.md) für HoloLens und immersive Headsets auftritt. Sie können mit 3D-Engine, wie mixed Reality-apps erstellen [Unity](unity-development-overview.md), oder Sie können direkt auf den gemischten Windows-APIs Realität mit DirectX 11 oder DirectX 12. Wenn Sie die Plattform direkt nutzen, werden Sie im Grunde Ihre eigene Middleware oder ein Framework erstellen. Die Windows-APIs unterstützen sowohl geschriebene apps C++ und C#. Wenn Sie gerne verwenden würden C#, kann Ihre Anwendung nutzen, die ["sharpdx"](http://sharpdx.org/) open-Source-Softwarebibliothek.

Unterstützt die Windows Mixed Reality [zwei Arten von apps](app-views.md):
* **Mixed Reality-apps** (UWP und Win32) die Verwendung der [HolographicSpace-API](getting-a-holographicspace.md) zum Rendern einer [immersive Ansicht](app-views.md) für den Benutzer, die die Kopfhörer Anzeige ausfüllt.
* **2D apps** (UWP) können die verwenden DirectX, XAML oder andere Frameworks zum Rendern [2D Ansichten](app-views.md#2d-views) auf Slate-PCs in der Windows Mixed Reality home.

Die Unterschiede zwischen der Entwicklung von DirectX für [2D- und immersive Ansichten](app-views.md) sind in erster Linie im Zusammenhang mit holographic Rendering und räumliche Eingabe. Der UWP-app ["iframeworkview"](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) oder Ihre Win32-app-HWND sind weiterhin erforderlich, und bleiben Sie größtenteils gleich, wie die WinRT-APIs für Ihre app verfügbar. Allerdings können Sie eine andere Teilmenge dieser APIs holographic Funktionen nutzen. Z. B. die SwapChain wird vom System für holographic apps verwaltet und arbeiten Sie mit der HolographicSpace-API verwenden, anstatt die DXGI an [präsentieren Frames](rendering-in-directx.md).

Zum Einstieg in die Entwicklung von immersive apps unter:
* Für **UWP-apps**, [Erstellen eines neuen UWP-Projekts mit den Vorlagen in Visual Studio](creating-a-holographic-directx-project.md). Abhängig von Ihrer Sprache, **Visual C++**  oder **Visual C#** , sehen Sie die UWP-Vorlagen unter **Windows Universal**  >   **Holographic**.
* Für **Win32-apps**, [Starten über die *BasicHologram* Win32-Beispiel](creating-a-holographic-directx-project.md#creating-a-win32-project).

Dies ist eine hervorragende Möglichkeit, den Code zu erhalten, den Sie Unterstützung für Rendering von holographic zu einer vorhandenen app oder -Engine hinzufügen müssen. Code und Konzepte werden in der Vorlage in einer Weise angezeigt, die für alle Entwickler, der in Echtzeit interaktive Software vertraut ist.

## <a name="getting-started"></a>Erste Schritte

Die folgenden Themen behandeln die grundlegenden Anforderungen von Middleware DirectX-basierten Windows Mixed Reality-Unterstützung hinzugefügt:
* [Erstellen eines holographic DirectX-Projekts](creating-a-holographic-directx-project.md): Die holographic app-Vorlage, die zusammen mit der Dokumentation zeigt Ihnen die Unterschiede zwischen was Sie sich gewöhnt und den speziellen Anforderungen von einem Gerät, das entworfen wurde, um funktionsfähig sind, während auf den Kopf geführt eingeführt.
* [Abrufen einer HolographicSpace](getting-a-holographicspace.md): Sie müssen zuerst eine HolographicSpace, erstellen Sie in dem Ihre app die Sequenz der HolographicFrame Objekte enthalten sind, die jede Head Position darstellen, aus der Sie gerendert werden.
* [Rendern in DirectX](rendering-in-directx.md): Da eine holographic SwapChain zwei Renderziele aufweist, müssen Sie wahrscheinlich auf die Möglichkeit, einige Änderungen vornehmen, die Anwendung rendert.
* [Koordinatensysteme im DirectX](coordinate-systems-in-directx.md): Windows Mixed Reality erlernt und aktualisiert die Kenntnisse aus der ganzen Welt als der Benutzer führt, räumliche Koordinatensysteme, die apps, um verständlich des Benutzers-Umgebung verwenden, einschließlich räumliche Anker und des Benutzers definierten räumliche Phase bereitstellen.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Hinzufügen von mixed Reality-Funktionen und Eingaben

Um die bestmögliche Leistung für Benutzer Ihrer immersive Apps zu aktivieren, sollten Sie die folgenden wichtigsten Bausteine zu unterstützen:
* [Haupt- und Eye Blicke in DirectX](gaze-in-directx.md)
* [Praktische und Motion-Controllern in DirectX](hands-and-motion-controllers-in-directx.md)
* [Spracheingabe in DirectX](voice-input-in-directx.md)
* [Raumklang in DirectX](spatial-sound-in-directx.md)
* [Räumliche Abbildung in DirectX](spatial-mapping-in-directx.md)

Es gibt andere wichtige Features, die viele faszinierende apps zu verwenden möchten, die auch in DirectX-apps verfügbar gemacht werden:
* [Gemeinsame Raumanker in DirectX](shared-spatial-anchors-in-directx.md)
* [Ausrichtbare Kamera in DirectX](locatable-camera-in-directx.md)
* [Tastatur-, Maus- und Controllereingaben in DirectX](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>Siehe auch
* [App-Modell](app-model.md)
* [App-Ansichten](app-views.md)
