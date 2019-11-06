---
title: Navigieren in der Windows Mixed Reality-Startseite
description: Hololens und Windows Mixed Reality-Headsets haben ein Paradigma für das starten, platzieren und manipulieren von apps und 3D-Modellen in Ihrer Umgebung (unabhängig davon, ob physisch oder Digital). Erfahren Sie, wie Sie auf beiden Gerätetypen in der Windows Mixed Reality-Startseite navigieren.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Shell, Betriebssystem, Plattform, Klippe, Haus, Home, Umgebung, Start, Startmenü, Startmenü, Pins, APP, Apps starten, Apps platzieren, teleportieren, verschieben, navigieren
ms.openlocfilehash: 9de4cb44505d6cf4d0d3e4bd0fd9c5ee681063a5
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438159"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>Navigieren in der Windows Mixed Reality-Startseite

Ebenso wie die Windows-PC-Darstellung mit dem Desktop startet, beginnt Windows Mixed Reality mit der Startseite. Die Windows Mixed Reality-Homepage nutzt unsere angeborenen Möglichkeiten, um 3D-Orte zu verstehen und zu navigieren. Bei hololens ist Ihre Startseite Ihr physischer Raum. Mit immersiven Headsets ist Ihr Zuhause ein virtueller Ort.

In Ihrer Startseite verwenden Sie auch das Startmenü, um apps und Inhalte zu öffnen und zu platzieren. Sie können Ihre Startseite mit gemischtem Reality-Inhalt und Multitaskings auffüllen, indem Sie mehrere apps gleichzeitig verwenden. Die Dinge, die Sie in Ihrem Zuhause platzieren, bleiben auch dann, wenn Sie Ihr Gerät neu starten.

## <a name="start-menu"></a>Startmenü

![Startmenü für Microsoft hololens](images/start-500px.png)

Das Startmenü besteht aus folgendem:
* System Informationen (Netzwerkstatus, Akku Prozentsatz, aktuelle Uhrzeit und Volume)
* Cortana (auf immersiven Headsets, eine Start Kachel, auf hololens oben im Startmenü)
* Fixierte apps
* Schaltfläche "alle apps" (Pluszeichen)
* Foto-und Video Schaltflächen für die [gemischte Erfassung](mixed-reality-capture.md)

Wechseln Sie zwischen den Ansichten angeheftete apps und alle apps, indem Sie die Schaltflächen Plus oder minus auswählen. Um das Startmenü auf hololens zu öffnen, verwenden Sie die aufblütebewegung. Drücken Sie auf einem immersiven Headset die Windows-Taste auf dem Controller.

## <a name="launching-apps"></a>Starten von apps

Um eine APP zu starten, wählen Sie Sie im Startmenü aus. Das Startmenü wird ausgeblendet, und die APP wird im Platzierungs Modus geöffnet, entweder als 2D-Fenster oder als [3D-Modell](implementing-3d-app-launchers.md).

Um die APP auszuführen, müssen Sie Sie in ihrer eigenen Homepage platzieren:
1. Verwenden Sie Ihren [Blick](gaze-and-commit.md) oder Controller, um die APP zu positionieren, wo Sie Sie möchten. Sie wird automatisch (in Größe und Position) angepasst, damit Sie dem Platz entspricht, in dem Sie Sie platzieren.
2. Platzieren Sie die App mithilfe von Air-Tap (hololens) oder der Schaltfläche auswählen (immersives Headsets). Wenn Sie das Startmenü abbrechen und wieder zurückkehren möchten, verwenden Sie die Schaltfläche mit den aufblühen oder Windows.

[2D-apps](building-2d-apps.md), die für Desktop, Mobile oder Xbox erstellt wurden, können so geändert werden, dass Sie mit der [holographicspace-API](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx)als immersive gemischte Realität-apps ausgeführt werden. Eine immersive App bringt den Benutzer aus der Startseite und in eine immersive Darstellung. Benutzer können die Startseite mit der Blüten Bewegung (hololens) oder durch Drücken der Windows-Taste auf Ihrem Controller (immersive Headsets) zurückgeben.

Apps können auch über eine APP-zu-app-API oder über Cortana gestartet werden.

![Apps in der Windows Mixed Reality-Startseite](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>Verschieben und Anpassen von apps

Wählen Sie in der APP-Leiste **Anpassen** aus, um Steuerelemente anzuzeigen, die Inhalte mit gemischter Realität verschieben, skalieren und drehen. Wenn Sie fertig sind **, wählen Sie fertig aus**.

![Das Speicher Slate im Anpassungsmodus (blauer Frame). Beachten Sie, dass die APP-Leiste (oben) geändert wurde, sodass Sie die Schaltflächen "Done" und "Remove" enthält.](images/adjust-500px.png)

Unterschiedliche apps haben möglicherweise zusätzliche Optionen auf der APP-Leiste. Microsoft Edge verfügt beispielsweise über *Scroll*-, *Drag*-und *Zoom* -Optionen. 

![App-Leiste für 2D-apps, die auf hololens ausgeführt werden](images/holobar-500px.png)

Die Schaltfläche " **zurück** " navigiert zurück zu den zuvor angezeigten Bildschirmen in der app. Sie wird beendet, wenn Sie den Anfang der in der APP angezeigten Erfahrungen erreichen und nicht zu anderen apps navigieren.

## <a name="getting-around-your-home"></a>Zu Hause

Mit **hololens**bewegen Sie den physischen Raum, um zu Ihrem Zuhause zu navigieren.

Mit **immersiven Headsets**können Sie in Ihrem Playspace auf ähnliche Weise fortfahren, um in einem ähnlichen Bereich in der virtuellen Welt zu navigieren. Wenn Sie über längere Entfernungen hinweg wechseln möchten, können Sie den Finger Stick auf dem Controller auf die gleiche Weise "durchlaufen", oder Sie können die *teleportung* verwenden, um sofort längere Entfernungen zu überspringen.

![Teleportierung in der Windows Mixed Reality-Startseite](images/teleportation-500px.png)

**An Teleport:**
1. Rufen Sie den Teleportations-Reticle auf.
   * Verwenden von [Bewegungs Controllern](motion-controllers.md): Drücken Sie den Finger Stick vorwärts, und halten Sie ihn an dieser Position gedrückt.
   * Verwenden eines Xbox-Controllers: Drücken Sie den linken Finger Stick vorwärts, und halten Sie ihn an dieser Position gedrückt.
   * Mit der Maus: halten Sie die Maustaste gedrückt, und verwenden Sie das Mausrad, um die Richtung zu drehen, die Sie beim teleportieren möchten.
2. Platzieren Sie den Reticle, an den Sie teleportieren möchten.
   * Verwenden von [Bewegungs Controllern](motion-controllers.md): neigen Sie den Controller (auf dem Sie den Finger Stick halten), um den Reticle zu verschieben.
   * Verwenden eines Xbox-Controllers: Verwenden Sie den [Blick](gaze-and-commit.md) , um den Reticle zu verschieben.
   * Mit der Maus: bewegen Sie die Maus, um den Reticle zu verschieben.
3. Geben Sie die Schaltfläche an den Teleport an, an dem der Reticle abgelegt wurde.

**Bis zu "Walk:"**
* Verwenden von [Bewegungs Controllern](motion-controllers.md): Klicken Sie auf dem Finger Stick auf nach unten, und bewegen Sie den Finger Stick in der Richtung, die Sie "durchlaufen".
* Verwenden eines Xbox-Controllers: Klicken Sie auf der linken Seite auf nach unten, und halten Sie den Finger Stick in der Richtung, die Sie durchlaufen möchten.

## <a name="immersive-headset-input-support"></a>Unterstützung von immersiven Headset-Eingaben

[Immersive Headsets in Windows Mixed Reality](immersive-headset-hardware-details.md) unterstützen mehrere Eingabetypen für die Navigation in der Windows Mixed Reality-Startseite. Hololens unterstützt keine Zubehör Eingaben für die Navigation, da Sie physisch herumlaufen und Ihre Umgebung sehen. Hololens [unterstützt jedoch Eingaben](hardware-accessories.md) für die Interaktion mit apps.

### <a name="motion-controllers"></a>Motion-Controller

Die beste Windows Mixed Reality-Lösung ist die Verwendung von Windows Mixed Reality [Motion-Controllern](motion-controllers.md) , die eine Nachverfolgung von 6 Grad an Freiheit unterstützen, indem nur die Sensoren in Ihrem Headset verwendet werden, ohne dass externe Kameras oder Marker erforderlich sind!

Navigations Befehle in Kürze verfügbar.

### <a name="gamepad"></a>Gamepad
* **Linker Finger Stick:**
  * Halten Sie den linken Finger Stick nach vorne, um den [Teleportations](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) -Reticle aufzurufenden.
  * Tippen Sie auf den Finger Stick Links, rechts oder zurück, um in kleinen Schritten nach links, rechts oder zurück zu wechseln.
  * Klicken Sie auf der linken Seite auf nach unten, und halten Sie den Finger Stick in der Richtung, die Sie [virtuell durchlaufen möchten.](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* Tippen Sie auf den **rechten Finger Stick** Links oder rechts, um die Richtung um 45 Grad zu drehen.
* Wenn Sie auf die Schaltfläche **A** klicken, wird eine Auswahl durchgeführt und das Verhalten der [Tippbewegung in die Luft](gaze-and-commit.md#composite-gestures) gespiegelt.
* Durch Drücken der Schaltfläche **Guide** (Leitfaden) wird das [Startmenü](navigating-the-windows-mixed-reality-home.md#start-menu) geöffnet und das Verhalten der [Öffnengeste](system-gesture.md#bloom) gespiegelt.
* Wenn Sie den **linken und den rechten Trigger** drücken, können Sie eine 2D-Desktop-App, mit der Sie interagieren, in der Startseite vergrößern und verkleinern.

### <a name="keyboard-and-mouse"></a>Tastatur und Maus

**Hinweis:** Verwenden Sie die **Windows-Taste + Y** , um die Maus zwischen dem Steuern des Desktops Ihres PCs und der Windows Mixed Reality-Startseite zu wechseln.

Innerhalb der Windows Mixed Reality-Startseite:
* Wenn Sie mit der **linken Maustaste auf** die Maustaste klicken, wird eine SELECT-Aktion durchführt, die wie die [Luft tippen](gaze-and-commit.md#composite-gestures) Bewegung
* Wenn Sie mit der **rechten Maustaste klicken** , wird der [teleportationsreticle](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) angezeigt.
* Wenn Sie die **Windows** -Taste auf der Tastatur drücken, wird das [Startmenü](navigating-the-windows-mixed-reality-home.md#start-menu) geöffnet, und Sie verhält sich wie die [Blüte](system-gesture.md#bloom) Bewegung.
* Wenn Sie in einer 2D-Desktop-App mit der **linken Maustaste klicken** , klicken [Sie mit der](gaze-and-commit.md) **rechten** Maustaste, um Kontextmenüs anzuzeigen, und verwenden Sie das **Mausrad** , um einen Bildlauf durchzuführen (genau wie auf dem Desktop Ihres PCs).

## <a name="cortana"></a>Cortana

[Cortana](voice-input.md#hey-cortana) ist Ihr persönlicher Assistent in Windows Mixed Reality, ebenso wie auf dem PC und Telefon. Hololens verfügt über ein integriertes Mikrofon, aber immersive Headsets erfordern möglicherweise zusätzliche Hardware. Verwenden Sie Cortana, um apps zu öffnen, Ihr Gerät neu zu starten, Dinge online zu sehen und vieles mehr. Entwickler können sich auch für die [Integration von Cortana](https://dev.windows.com/cortana) in Ihre Erfahrungen entscheiden.

Sie können auch Sprachbefehle verwenden, um zu Hause zu gelangen. Zeigen Sie z. b. auf eine Schaltfläche (über einen [Blick](gaze-and-commit.md) oder einen Controller, je nach Gerät), und sagen Sie "Select". Weitere Sprachbefehle sind "Go Home", "Bigger", "kleiner", "Close" und "Face Me".

## <a name="store-settings-and-system-apps"></a>Store-, Einstellungs-und System-apps

Windows Mixed Reality verfügt über eine Reihe integrierter apps, wie z. b.:
* **Microsoft Store** zum erhalten von apps und spielen
* **Feedback-Hub** zum Übermitteln von Feedback über die System-und System-apps
* **Einstellungen** zum Konfigurieren von Systemeinstellungen ([einschließlich Netzwerk](connecting-to-wi-fi-on-hololens.md) -und Systemupdates)
* **Microsoft Edge** zum Durchsuchen von Websites
* **Fotos** zum Anzeigen und Freigeben von Fotos und Videos
* **Kalibrierung** (nur hololens) zum Anpassen der hololens-Darstellung an den aktuellen Benutzer
* **Erlernen Sie Gesten** (hololens), oder **erlernen Sie Gemischte Realität** (immersives Headsets), um mehr über die Verwendung Ihres Geräts zu erfahren.
* **3D-Viewer** zur Ergänzung ihrer Welt mit gemischtem Reality-Inhalt
* **Gemischtes Reality-Portal** (Desktop) zum Einrichten und Verwalten Ihres immersiven Headsets und Streamen einer Live Vorschau Ihrer Ansicht im Headset, damit Sie von anderen Benutzern angezeigt werden.
* **Filme und TV** zum Anzeigen von 360-Videos und die neuesten Filme und Fernsehsendungen
* **Cortana** für alle Anforderungen Ihres virtuellen Assistenten
* **Desktop** (immersive Headsets) zum Anzeigen Ihres Desktop Monitors in einem immersiven Headset
* **Datei-Explorer** Zugreifen auf Dateien und Ordner, die sich auf Ihrem Gerät befinden

## <a name="see-also"></a>Weitere Informationen:
* [App-Ansichten](app-views.md)
* [Motion-Controller](motion-controllers.md)
* [Hardware-Zubehör](hardware-accessories.md)
* [Umgebungsüberlegungen für HoloLens](environment-considerations-for-hololens.md)
* [Implementieren von 3D-App-launchern](implementing-3d-app-launchers.md)
* [Erstellen von 3D-Modellen für die Verwendung in der Windows Mixed Reality-Startseite](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
