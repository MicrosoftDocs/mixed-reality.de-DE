---
title: DirectX-Entwicklungs Übersicht
description: Erstellen Sie eine DirectX-basierte gemischte Reality-Engine direkt mithilfe der Windows Mixed Reality-APIs.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX, Holographic Rendering, Native, Native APP, WinRT, WinRT-APP, Plattform-APIs, benutzerdefinierte Engine, Middleware
ms.openlocfilehash: 0af73314c3c93d230ef87ed468f718f5b3e1813c
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926629"
---
# <a name="directx-development-overview"></a>DirectX-Entwicklungs Übersicht


Windows Mixed Reality-Anwendungen verwenden die [Holographic](rendering.md)-APIs Rendering, [Gaze](gaze-and-commit.md), [Geste](gaze-and-commit.md#composite-gestures), [Motion Controller](motion-controllers.md), [Voice](voice-input.md)und [räumliche Zuordnung](spatial-mapping.md) , um [gemischte Realität](mixed-reality.md) für hololens und immersive Headsets. Sie können gemischte Reality-Anwendungen mit einer 3D-Engine, z. b. [Unity](unity-development-overview.md), erstellen, oder Sie können direkt mithilfe von DirectX 11 oder DirectX 12 mit den Windows Mixed Reality-APIs codieren. Wenn Sie die Plattform direkt nutzen, werden Sie im Wesentlichen eine eigene Middleware oder ein eigenes Framework aufbauen. Die Windows C++ -APIs unterstützen Anwendungen, die C#in und geschrieben wurden. Wenn Sie sich für die C#Verwendung von entscheiden, kann die Anwendung die Open Source-Software Bibliothek von [sharpdx](https://sharpdx.org/) nutzen.


Windows Mixed Reality unterstützt [zwei Arten von apps](app-views.md):
* **Gemischte Reality-Anwendungen** (UWP oder Win32), die die [holographicspace-API](getting-a-holographicspace.md) verwenden, um eine [immersive Ansicht](app-views.md) für den Benutzer zu erzeugen, der die Headset-Anzeige füllt.
* **2D-apps** (UWP), die DirectX, XAML oder andere Frameworks zum Rendering von [2D-Ansichten](app-views.md#2d-views) auf Slate in der Windows Mixed Reality-Startseite verwenden.


Die Unterschiede zwischen der DirectX [-Entwicklung für 2D-Sichten und immersive Sichten](app-views.md) beziehen sich hauptsächlich auf das Holographic-Rendering und räumliche Eingaben. Die [iframeworkview](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) ihrer UWP-Anwendung oder das HWND ihrer Win32-Anwendung ist erforderlich und bleibt größtenteils unverändert, ebenso wie die WinRT-APIs, die für Ihre Anwendung verfügbar sind. Sie müssen jedoch eine andere Teilmenge dieser APIs verwenden, um die Vorteile der Holographic-Features zu nutzen. Beispielsweise wird die Swapkette vom System für Holographic-Anwendungen verwaltet. Sie arbeiten mit der holographicspace-API anstelle von DXGI, um [Frames darzustellen](rendering-in-directx.md).

So beginnen Sie mit der Entwicklung von immersiven Anwendungen:
* Erstellen Sie für **UWP-apps** [mit den Vorlagen in Visual Studio ein neues UWP-Projekt](creating-a-holographic-directx-project.md). Basierend auf Ihrer Sprache, **Visualisierung C++**  oder **Visualisierung C#** finden Sie die UWP-Vorlagen unter **Windows Universal** > **Holographic**.
* Beginnen Sie für **Win32-Anwendungen**mit [dem *basichologram* Win32-Beispiel](creating-a-holographic-directx-project.md#creating-a-win32-project).

Dies ist eine großartige Möglichkeit, um den Code zu erhalten, den Sie zum Hinzufügen von Holographic-Rendering-Unterstützung zu einer vorhandenen Anwendung oder Engine benötigen. Code und Konzepte werden in der Vorlage auf eine Weise vorgestellt, die jedem Entwickler von Echtzeit-interaktiver Software vertraut ist.


## <a name="getting-started"></a>Erste Schritte

In den folgenden Themen werden die grundlegenden Anforderungen für das Hinzufügen von Windows Mixed Reality-Unterstützung zu DirectX-basierter Middleware erläutert:

* [Erstellen eines Holographic DirectX-Projekts](creating-a-holographic-directx-project.md): die Vorlage für Holographic-Anwendungen, die mit der Dokumentation verknüpft ist, zeigt Ihnen die Unterschiede zwischen dem, was Sie verwenden, und den besonderen Anforderungen, die von einem Gerät eingeführt wurden, das für die Funktionsweise von Wenn Sie sich auf dem Kopf befinden.
* [Holen Sie sich einen holographicspace](getting-a-holographicspace.md): Sie müssen zunächst einen holographicspace erstellen, der Ihrer Anwendung die Sequenz von holographicframe-Objekten bereitstellt, die jede Hauptposition darstellen, von der Sie das Rendering durchführen.
* [Rendering in DirectX](rendering-in-directx.md): da eine Holographic Swap-Kette über zwei Renderziele verfügt, müssen Sie einige Änderungen an der Art und Weise vornehmen, in der die Anwendung gerendert wird.
* [Koordinatensysteme in DirectX](coordinate-systems-in-directx.md): Windows Mixed Reality lernt und aktualisiert das Verständnis der Welt, wenn der Benutzer es durchläuft. Dies bietet räumliche Koordinatensysteme, die von Anwendungen verwendet werden, um die Benutzerumgebung zu verwenden, einschließlich räumlicher Anker und der definierten räumlichen Stufe des Benutzers.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Hinzufügen gemischter Reality-Funktionen und-Eingaben

Sie sollten die folgenden wichtigen Bausteine unterstützen, um die bestmögliche Benutzer Leistung für Benutzer Ihrer immersiven Anwendung zu ermöglichen:

* [Anvisieren mit dem Kopf und mit den Augen in DirectX](gaze-in-directx.md)
* [Hände und Motion-Controller in DirectX](hands-and-motion-controllers-in-directx.md)
* [Spracheingabe in DirectX](voice-input-in-directx.md)
* [Raumklang](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)
* [Räumliche Abbildung in DirectX](spatial-mapping-in-directx.md)


Es gibt noch weitere wichtige Features, die von vielen immersiven Anwendungen verwendet werden, die auch für DirectX-Anwendungen verfügbar gemacht werden:

* [Gemeinsame Raumanker in DirectX](shared-spatial-anchors-in-directx.md)
* [Tastatur-, Maus- und Controllereingaben in DirectX](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>Weitere Informationen:
* [App-Modell](app-model.md)
* [App-Ansichten](app-views.md)
