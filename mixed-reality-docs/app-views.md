---
title: App-Ansichten
description: Die beiden Arten von Ansichten in Windows Mixed Reality-apps sind faszinierende und Direct2D-Ansichten.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: immersive Ansicht 2D-Ansicht, Tablet PCs,-app
ms.openlocfilehash: 2cf65941616ac6906d40e4b4616311317ac705d3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604734"
---
# <a name="app-views"></a>App-Ansichten

Windows-apps können zwei Arten von Ansichten enthalten **immersive Ansichten** und **2D Ansichten**. Apps können zwischen ihren verschiedenen immersive und 2D Ansichten, zeigt ihre 2D-Ansichten entweder auf einem Monitor als ein Fenster oder in einen Kopfhörer als ein Slate wechseln. Apps, verfügen über mindestens eine immersive Ansicht, gehören zur Kategorie **mixed Reality-apps**. Apps, die nie eine immersive Sicht sind **2D apps**.

## <a name="immersive-views"></a>Immersive Ansichten

Eine immersive Ansicht bietet Ihrer app die Möglichkeit, Hologramme in die Welt um Sie zu erstellen, oder den Benutzer in einer virtuellen Umgebung tauchen. Beim Zeichnen von einer app in der Ansicht immersive ist ist keine anderen Apps zur gleichen Zeit zeichnen&mdash;Hologramme von mehreren apps sind nicht zusammengesetzte zusammen. Durch Anpassen der ständig die Perspektive aus, die Ihre [app rendert](rendering.md) der Szene entsprechend Head Bewegungen des Benutzers, kann Ihre app gerendert werden [World-locked](coordinate-systems.md) Hologramme, die an einem festen Punkt in die tatsächlichen bleiben Welt, oder es kann eine virtuelle Welt rendern, die die Position enthält, wenn ein Benutzer darin bewegt.

![In eine immersive-Ansicht können Hologramme in der ganzen Welt, um Sie herum platziert werden.](images/designoverview.jpg)<br>
*Hologramme können in eine immersive-Ansicht in der ganzen Welt, um Sie herum platziert werden*

Auf [HoloLens](hololens-hardware-details.md), Ihre app rendert der Hologramme auf die reale Umgebung des Benutzers. Auf einem [immersive Windows Mixed Reality-Kopfhörer](immersive-headset-hardware-details.md), dem Benutzer kann nicht angezeigt, die reale Welt und dem Benutzer wird angezeigt, damit alles, was von Ihrer app gerendert werden muss.

Die [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) (einschließlich des Startmenüs und Hologramme Sie, um die Umgebung platziert haben) rendert nicht in eine immersive entweder anzeigen. HoloLens werden Benachrichtigungen des Systems, die auftreten, während eine immersive Ansicht angezeigt werden von Cortana akustisch übertragen werden und der Benutzer mit der Spracheingabe reagieren kann.

Klicken Sie in eine immersive anzeigen, ist Ihre Anwendung auch verantwortlich für die Verarbeitung aller Eingaben. Eingabe in Windows Mixed Reality setzt sich aus [bestaunen](gaze.md), [Geste](gestures.md) (nur für HoloLens), [Voice](voice-input.md) und [motion Controller](motion-controllers.md) (immersive Headsets nur).

## <a name="2d-views"></a>2D Ansichten

![Mehrere 2D Ansichten angeordnet, um die Windows Mixed Reality home](images/teleportation-640px.png)<br>
*Mehrere apps mit einer 2D-Ansicht platziert werden, um die Windows Mixed Reality home*

Eine app mit einer 2D-Ansicht angezeigt wird, der [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) (der "Shell" bezeichnet) als eine virtuelle Slate-Objekt, gerendert werden soll, zusammen mit der app-startfeldern und andere Hologramme, die der Benutzer wurde in die Welt platziert. Der Benutzer kann diese Slate-Objekt zu verschieben und zu skalieren, anpassen, obwohl es mit einer festen Auflösung unabhängig von seiner Größe bleibt. Wenn eine Direct2D erste Ansicht Ihrer app ist, wird Ihre 2D-Inhalt die gleichen Slate-Objekt verwendet, um die app zu starten ausgefüllt.

In einer desktop-Kopfhörer können Sie apps, universelle Windows-Plattform (UWP) ausführen, die heute auf Ihrem desktop ausgeführt. Diese apps sind heute bereits 2D Rendern von Ansichten, und ihre Inhalte auf einem Slate-Objekt im Welt des Benutzers, beim Starten automatisch angezeigt. 2D UWP-apps können als Ziel der **Windows.Universal** Gerätefamilie auf beide desktop Headsets und HoloLens als Slate-PCs ausgeführt.

Eine wichtige Verwendung von 2D Ansichten ist ein Textformat-Eintrag angezeigt, die vornehmen können verwenden der Systemtastatur. Da die Shell nicht über eine immersive Ansicht rendern kann, muss die app in einer 2D-zum Anzeigen die Systemtastatur wechseln. Apps, die Texteingabe zustimmen können zu einer 2D-Ansicht ein Textfeld wechseln. Während dieses Textfeld den Fokus hat, zeigt das System die Systemtastatur, damit der Benutzer Text eingeben.

Beachten Sie, dass auf einem desktop-PC, eine app 2D Ansichten, die auf dem desktop überwachen und in eine angefügte Kopfhörer verfügen kann. Beispielsweise können Sie Edge auf Ihrem desktop Monitor mithilfe der 2D Hauptansicht eine 360-Grad-Video durchsuchen. Wenn Sie das Video abspielen, startet Edge eine sekundäre immersive Ansicht innerhalb der Kopfhörer, um den Inhalt für immersive video anzuzeigen.

## <a name="see-also"></a>Siehe auch

* [App-Modell](app-model.md)
* [Aktualisieren von 2D UWP-apps für mixed reality](building-2d-apps.md)
* [Abrufen einer HolographicSpace](getting-a-holographicspace.md)
* [Navigieren Sie in der Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md)
* [Mixed Reality-App-Typen](types-of-mixed-reality-apps.md)
