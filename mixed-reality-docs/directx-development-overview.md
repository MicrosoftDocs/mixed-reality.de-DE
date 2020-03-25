---
title: Übersicht über die native Entwicklung
description: Erstellen Sie eine DirectX-basierte gemischte Reality-Engine, indem Sie die Windows Mixed Reality-APIs direkt verwenden.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX, Holographic Rendering, Native, Native APP, WinRT, WinRT-APP, Plattform-APIs, benutzerdefinierte Engine, Middleware
ms.openlocfilehash: 5c61739ea6c90b4547c5c9927cf2129304650926
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80159996"
---
# <a name="native-development-overview"></a>Übersicht über die native Entwicklung

Windows Mixed Reality-Anwendungen verwenden die folgenden APIs, um Umgebungen mit [gemischter Realität](mixed-reality.md) für hololens und andere immersive Headsets zu erstellen:

 - [Holographisches Rendern](rendering.md)
 - [Anvisieren](gaze-and-commit.md)
 - [Gestaltungs](gaze-and-commit.md#composite-gestures)
 - [Bewegungs Controller](motion-controllers.md)
 - [Sprache](voice-input.md)
 - [Räumliche Abbildung](spatial-mapping.md)

Sie können gemischte Reality-Anwendungen erstellen, indem Sie eine 3D-Engine verwenden, z. b. [Unity](unity-development-overview.md). Oder Sie können mithilfe von DirectX 11 oder DirectX 12 direkt zu den Windows Mixed Reality-APIs codieren. Wenn Sie die Plattform direkt nutzen, erstellen Sie im Grunde Ihre eigene Middleware oder Ihr eigenes Framework. Die Windows-APIs unterstützen Anwendungen, die sowohl C++ in C#als auch in geschrieben wurden. Wenn Sie verwenden C#, kann Ihre Anwendung die Open Source-Software Bibliothek von [sharpdx](https://sharpdx.org/) nutzen.

Windows Mixed Reality unterstützt [zwei Arten von apps](app-views.md):
* **Anwendungen mit gemischter Realität** (UWP oder Win32), die die [holographicspace-API](getting-a-holographicspace.md) oder die [openxr-API](openxr.md) verwenden, um eine [immersive Ansicht](app-views.md) für den Benutzer zu erzeugen, der die Headset-Anzeige füllt
* **2D-apps** (UWP), die DirectX, XAML oder ein anderes Framework zum Rendering von [2D-Ansichten](app-views.md#2d-views) auf Slate in der Windows Mixed Reality-Startseite verwenden

Die Unterschiede zwischen der DirectX [-Entwicklung für 2D-Ansichten und immersive Ansichten](app-views.md) betreffen in erster Linie das holografische Rendering und räumliche Eingaben. Die [iframeworkview](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) ihrer UWP-Anwendung oder das HWND ihrer Win32-Anwendung ist erforderlich und bleibt größtenteils unverändert. Das gleiche gilt für die WinRT-APIs, die für Ihre app verfügbar sind. Sie müssen jedoch eine andere Teilmenge dieser APIs verwenden, um die Vorteile der Holographic-Features zu nutzen. Beispielsweise werden die "vorhandenes SwapChain" und "Frame" vom System für holografische Anwendungen verwaltet, um eine von Pose vorhergesagte Frame Schleife zu aktivieren.

## <a name="get-started-with-openxr"></a>Einstieg in openxr

Sie können auf dem Desktop mit openxr auf einem hololens 2-oder Windows Mixed Reality-immersiven Headset entwickeln.  Wenn Sie keinen Zugriff auf ein Headset haben, können Sie stattdessen den hololens 2-Emulator oder den Windows Mixed Reality-Simulator verwenden.

Informationen zum Einstieg in die Entwicklung von openxr-Anwendungen für hololens 2 oder immersive Windows Mixed Reality-Headsets finden Sie unter Erste Schritte [mit der openxr-Entwicklung](openxr-getting-started.md).

## <a name="get-started-with-winrt"></a>Einstieg in WinRT

So beginnen Sie mit der Entwicklung von immersiven Anwendungen:
* Verwenden Sie für **UWP-apps** [die Vorlagen in Visual Studio, um ein neues UWP-Projekt zu erstellen](creating-a-holographic-directx-project.md). Suchen Sie basierend auf Ihrer Sprache C++ , Visualisierung C#oder Visualisierung die UWP-Vorlagen unter **Windows Universal** > **Holographic**.
* Beginnen Sie für **Win32-Anwendungen**mit [dem *basichologram* Win32-Beispiel](creating-a-holographic-directx-project.md#creating-a-win32-project).

Dieser Schritt ist eine gute Möglichkeit, um den Code zu erhalten, den Sie zum Hinzufügen von Holographic Rendering-Unterstützung zu einer vorhandenen Anwendung oder Engine benötigen. Der Code und die Konzepte werden in der Vorlage auf eine Weise dargestellt, die jedem Entwickler von Echtzeit-interaktiver Software vertraut ist.

In den folgenden Themen werden die grundlegenden Anforderungen beschrieben, wenn Sie DirectX-basierter Middleware Windows Mixed Reality-Unterstützung hinzufügen.

* [Erstellen Sie ein Holographic DirectX-Projekt](creating-a-holographic-directx-project.md): die Vorlage für Holographic-Anwendungen, die mit der Dokumentation verknüpft ist, zeigt die Unterschiede im Vergleich zu ihrer Verwendung. Außerdem werden die besonderen Anforderungen für ein Gerät beschrieben, das für die Funktions Zeit konzipiert ist, während Sie auf dem Kopf ruhen.
* [Verschaffen Sie sich einen holographicspace](getting-a-holographicspace.md): Sie müssen zuerst einen holographicspace erstellen, der Ihrer Anwendung die Sequenz von holographicframe-Objekten übergibt, die jede Kopfzeile darstellen, von der Sie die Darstellung machen.
* [In DirectX Rendern](rendering-in-directx.md): da eine Holographic vorhandenes SwapChain über zwei Renderziele verfügt, müssen Sie Änderungen an der Art und Weise vornehmen, in der die APP gerendert wird.
* [Koordinatensysteme in DirectX](coordinate-systems-in-directx.md): Windows Mixed Reality lernt und aktualisiert das Verständnis der Welt, wenn der Benutzer es durchläuft. Dies bietet räumliche Koordinatensysteme, die von Anwendungen verwendet werden, um die Benutzerumgebung zu verwenden, einschließlich räumlicher Anker und der definierten räumlichen Stufe des Benutzers.

## <a name="add-mixed-reality-capabilities-and-inputs"></a>Hinzufügen gemischter Reality-Funktionen und-Eingaben

Sie sollten die folgenden Hauptbausteine unterstützen, um den Benutzern Ihrer immersiven APP das bestmögliche Verhalten zu bieten:

* [Anvisieren mit dem Kopf und mit den Augen in DirectX](gaze-in-directx.md)
* [Hände und Motion-Controller in DirectX](hands-and-motion-controllers-in-directx.md)
* [Spracheingabe in DirectX](voice-input-in-directx.md)
* [Raumklang](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)
* [Räumliche Abbildung in DirectX](spatial-mapping-in-directx.md)

Dies sind andere wichtige Features, die von vielen immersiven Anwendungen verwendet werden, die auch für DirectX-Anwendungen verfügbar gemacht werden:

* [Gemeinsame Raumanker in DirectX](shared-spatial-anchors-in-directx.md)
* [Tastatur-, Maus- und Controllereingaben in DirectX](keyboard-mouse-and-controller-input-in-directx.md)

## <a name="see-also"></a>Siehe auch
* [App-Modell](app-model.md)
* [App-Ansichten](app-views.md)
