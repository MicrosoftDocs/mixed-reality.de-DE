---
title: App-Ansichten
description: Die zwei Arten von Ansichten in Windows Mixed Reality-apps sind immersive Ansichten und 2D-Ansichten.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: immersive Ansicht, 2D-Ansicht, Slate, App
ms.openlocfilehash: a5b50df5be31d66a866e691d9e059bcf38672064
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437039"
---
# <a name="app-views"></a>App-Ansichten

Windows-Apps können zwei Arten von Ansichten, **immersive Ansichten** und **2D-Ansichten**enthalten. Apps können zwischen den verschiedenen immersiven Ansichten und 2D-Ansichten wechseln, wobei ihre 2D-Ansichten entweder in einem Monitor als Fenster oder in einem Headset als Slate angezeigt werden. Apps, die mindestens eine immersive Ansicht aufweisen, werden als **Mixed Reality-apps**kategorisiert. Apps, die nie eine immersive Ansicht haben, sind **2D-apps**.

## <a name="immersive-views"></a>Immersive Ansichten

Eine immersive Ansicht bietet Ihrer APP die Möglichkeit, auf der ganzen Welt Hologramme zu erstellen oder den Benutzer in eine virtuelle Umgebung einzuschließen. Wenn eine app in der immersiven Ansicht gezeichnet wird, wird keine andere APP gleichzeitig gezeichnet,&mdash;holograms aus mehreren apps nicht zusammengeführt werden. Durch die kontinuierliche Anpassung der Perspektive, von der Ihre APP die Szene [rendert](rendering.md) , sodass Sie den Kopfbewegungen des Benutzers entspricht, kann Ihre APP [weltweit gesperrte](coordinate-systems.md) holograms rendern, die an einem festgelegten Punkt in der realen Welt verbleiben, oder eine virtuelle Welt rendern, die die Position, in der sich ein Benutzer bewegt.

Wenn Sie sich in einer immersiven Ansicht befinden, können Sie auf der ganzen Welt holograms platzieren. ![](images/designoverview-940px.jpg)<br>
*Wenn Sie sich in einer immersiven Ansicht befinden, können holograms auf der ganzen Welt platziert werden.*

Bei [hololens](hololens-hardware-details.md)rendert Ihre APP Ihre Hologramme auf der realen Umgebung des Benutzers. In einem [Windows Mixed Reality-immersiven Headset](immersive-headset-hardware-details.md)kann der Benutzer die reale Welt nicht sehen, sodass Ihre APP alles Rendering muss, was dem Benutzer angezeigt wird.

Die [Windows Mixed Reality-Startseite](navigating-the-windows-mixed-reality-home.md) (einschließlich des Start Menüs und holograms, die Sie um die Umgebung platziert haben) wird in einer immersiven Ansicht nicht angezeigt. Bei hololens werden alle System Benachrichtigungen, die während der Anzeige einer immersiven Ansicht auftreten, von Cortana übermittelt, und der Benutzer kann mit der Spracheingabe Antworten.

In einer immersiven Ansicht ist Ihre APP auch für die Verarbeitung aller Eingaben verantwortlich. Die Eingabe in der gemischten Realität von Windows besteht aus [Blick](gaze-and-commit.md), Bewegung [(nur](gaze-and-commit.md#composite-gestures) hololens), [sprach](voice-input.md) -und [Bewegungs Controllern](motion-controllers.md) (nur immersive Headsets).

## <a name="2d-views"></a>2D-Ansichten

![mehrere 2D-Ansichten, die auf der Windows Mixed Reality-Startseite angeordnet sind](images/teleportation-940px.png)<br>
*Mehrere apps mit einer 2D-Ansicht, die in der Windows Mixed Reality-Startseite platziert wird*

Eine APP mit einer 2D-Ansicht wird in der [Windows Mixed Reality-Start](navigating-the-windows-mixed-reality-home.md) Seite (manchmal als "Shell" bezeichnet) als virtuelles Slate angezeigt, das zusammen mit den App-launchern und anderen holograms gerendert wird, die der Benutzer in der Welt abgelegt hat. Der Benutzer kann diesen Slate so anpassen, dass er verschoben und skaliert wird, obwohl er unabhängig von seiner Größe bei fester Auflösung verbleibt. Wenn es sich bei der ersten Ansicht der App um eine 2D-Ansicht handelt, wird für den 2D-Inhalt das gleiche Slate-Element aufgefüllt, das zum Starten der APP

In einem Desktop-Headset können Sie alle universelle Windows-Plattform-Apps (UWP) ausführen, die noch heute auf dem Desktop Monitor ausgeführt werden. Diese apps Rendern bereits heute 2D-Ansichten, und ihre Inhalte werden automatisch auf einem Schiefer in der Benutzer Welt angezeigt, wenn Sie gestartet werden. 2D UWP-Apps können die **Windows. Universal** -Gerätefamilie für die Ausführung sowohl auf Desktop-Headsets als auch auf hololens als Slates ausrichten.

Eine zentrale Verwendung von 2D-Ansichten besteht darin, ein Texteingabe Formular anzuzeigen, mit dem die System Tastatur verwendet werden kann. Da die Shell nicht über eine immersive Ansicht hinaus Rendering durchzuführen ist, muss die APP zu einer 2D-Ansicht wechseln, um die System Tastatur anzuzeigen. Apps, die Texteingaben akzeptieren möchten, können mit einem Textfeld zu einer 2D-Ansicht wechseln. Während dieses Textfeld den Fokus besitzt, zeigt das System die Tastatur des Systems an, sodass der Benutzer Text eingeben kann.

Beachten Sie, dass eine APP auf einem Desktop-PC über 2D-Ansichten sowohl für den Desktop Monitor als auch für ein angefügtes Headset verfügen kann. Beispielsweise können Sie mit der zweiten 2D-Ansicht Edge auf dem Desktop Monitor durchsuchen, um ein Video mit dem 360-Grad zu finden. Wenn Sie das Video abspielen, startet Microsoft Edge eine sekundäre immersive Ansicht im Headset, um die immersiven Videoinhalte anzuzeigen.

## <a name="see-also"></a>Weitere Informationen:

* [App-Modell](app-model.md)
* [Aktualisieren von 2D-UWP-Apps für Mixed Reality](building-2d-apps.md)
* [Abrufen eines HolographicSpace-Objekts](getting-a-holographicspace.md)
* [Navigieren auf der Startseite von Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
* [Typen von Mixed Reality-Apps](types-of-mixed-reality-apps.md)
