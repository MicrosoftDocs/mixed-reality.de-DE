---
title: Navigieren Sie in der Windows Mixed Reality home
description: HoloLens und Windows Mixed Reality-Headsets verwenden ein Paradigma zum Starten, platziert, und Bearbeiten von apps und 3D-Modellen in Ihrer Umgebung, (ob physisch oder digital). Erfahren Sie, wie Sie die Windows Mixed Reality homeverzeichnis auf beide Gerätetypen zu navigieren.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Shell, Betriebssystem, Plattform, Cliff Hauses, Haus, Start, Umgebung, starten, Menü "Start", Menü home, Pins, app, verdienen, Teleport-apps speichern, verschieben, navigieren
ms.openlocfilehash: 1ca6dd66506a64ad2e1c21870fee2725ddf20bd8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604895"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>Navigieren Sie in der Windows Mixed Reality home

Genau wie die Windows-PC-Umgebung mit dem Desktop gestartet wird, startet Windows Mixed Reality, mit der Startseite. Die Windows Mixed Reality home nutzt unsere ausgeprägten besser zu verstehen, und navigieren 3D stellen. Mit HoloLens ist Ihre Startseite Ihrer physischen Raum. Mit immersive Headsets ist Ihre Startseite einen virtuellen Ort.

Ihre Startseite ist auch, in dem Sie verwenden des Startmenüs zu öffnen, und platzieren Sie apps und Inhalt. Können Sie Ihre Startseite mit mixed Reality-Inhalt füllen und Multitasking mit mehreren apps zur gleichen Zeit. Die Dinge, die Sie in Ihrem Haus platzieren bleiben, selbst wenn Sie Ihr Gerät neu starten.

## <a name="start-menu"></a>Startmenü

![Menü "Start" auf der Microsoft HoloLens](images/start-500px.png)

Das Startmenü besteht aus:
* Systeminformationen (Netzwerkstatus, Akku Prozent, aktuelle Uhrzeit und Volumes)
* Cortana (für immersive Headsets, eine Start-Kachel, HoloLens, am Anfang starten)
* Angeheftete apps
* Die Schaltfläche "alle apps" (Pluszeichen)
* Fotos und Videos Schaltflächen für [mixed Reality-Erfassung](mixed-reality-capture.md)

Wechseln Sie zwischen der angehefteten apps und alle Ansichten durch das Pluszeichen auswählen oder minusschaltfächen klickt. Um das Menü Start auf HoloLens zu öffnen, verwenden Sie die Bewegung Bloom. Klicken Sie auf eine immersive Kopfhörer drücken Sie die Schaltfläche "Windows" auf dem Controller aus.

## <a name="launching-apps"></a>Starten von apps

Um eine app zu starten, wählen sie im Startmenü. Werden im Startmenü ausgeblendet, und die app wird im Platzierungsmodus als eine 2D-Fenster zu öffnen oder ein [3D-Modell](implementing-3d-app-launchers.md).

Um die app auszuführen, müssen Sie sie dann im Haus zu platzieren:
1. Verwenden Ihrer [bestaunen](gaze.md) oder Controller aus, um die app zu positionieren, die gewünschte Stelle. Es wird automatisch (in Größe und Position) angepasst, um den Speicherplatz zu entsprechen, in dem Sie sie platzieren.
2. Platzieren Sie die app mit der tippbewegung-(HoloLens) oder die auswählen-Schaltfläche (immersive Headsets). Verwenden Sie zum abzubrechen, und schalten Sie wieder das Startmenü, die Bewegung Bloom oder die Schaltfläche "Windows" aus.

[Direct2D-apps](building-2d-apps.md)für Desktop-, mobil-, erstellt oder Xbox kann geändert werden, um die Ausführung als mixed Reality immersive apps unter Verwendung der [HolographicSpace API](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx). Eine beeindruckende app wird der Benutzer aus der Startseite und in ein eintauchen. Benutzer können Startseite mit dieser Bewegung Bloom (HoloLens) oder durch Drücken der Windows-Taste auf ihrer Controller (immersive Headsets) zurückgeben.

Apps können auch über eine app zur app-API oder über Cortana gestartet werden.

![Apps in die Windows Mixed Reality home](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>Verschieben und Anpassen von apps

Wählen Sie **anpassen** in der app steuert Balken, um anzuzeigen, die Umstellung, Skalierung, und drehen mixed Reality-Inhalt. Wenn Sie fertig sind, wählen Sie **Fertig**.

![Der Store Slate-Objekt im Anpassung-Modus (blauer Rahmen). Beachten Sie die app-Leiste (oben) wurde geändert, um "Fertig" und "Entfernen" enthalten Schaltflächen.](images/adjust-500px.png)

Verschiedene apps möglicherweise zusätzliche Optionen auf der app-Leiste. Microsoft Edge verfügt beispielsweise über *Scrollen*, *Drag*, und *Zoom* Optionen. 

![App-Leiste für 2D apps für HoloLens](images/holobar-500px.png)

Die **wieder** Schaltfläche an der zuvor angezeigten Bildschirme in der app navigiert. Es wird beendet, wenn Sie den Anfang der Erfahrungen erreichen, die haben gezeigt wurde, in der app und gelangen nicht an andere apps.

## <a name="getting-around-your-home"></a>Abrufen von zu Hause

Mit **HoloLens**, Raum, um Ihre Startseite verschieben durchlaufen.

Mit **immersive Headsets**, Sie können auf ähnliche Weise einrichten und aufzusuchen, die in Ihrem Playspace in einem ähnlichen Bereich in der virtuellen Welt zu verschieben. Um auf langen entfernungen schwächer zu verschieben, können Sie die Ministick auf dem Controller praktisch "durchlaufen", oder Sie können *Teleportation* auf langen entfernungen schwächer sofort zu wechseln.

![Teleportation in die Windows Mixed Reality home](images/teleportation-500px.png)

**Um Teleport:**
1. Fahren Sie die Teleportation-Fadenkreuz.
   * Mithilfe von [motion Controller](motion-controllers.md): weiterleiten, Ministick zu drücken und halten Sie es an dieser Position.
   * Verwenden einen Xbox-Controller: weiterleiten, linken Ministick zu drücken und halten Sie es an dieser Position.
   * Mithilfe der Maus: Halten Sie die Maustaste gedrückt mit der rechten Maustaste (und verwenden Sie das Mausrad, um die Richtung drehen, wenn auftreten sollen, Sie Teleport).
2. Platzieren Sie das Fadenkreuz, wo Sie möchten Teleport.
   * Mithilfe von [motion Controller](motion-controllers.md): "Schräg" den Controller (auf dem Sie sind mit Ministick weiterleiten) um das Fadenkreuz zu verschieben.
   * Mit einer Xbox-Controller: Verwenden Sie Ihre [bestaunen](gaze.md) verschieben Sie das Fadenkreuz.
   * Mithilfe der Maus: bewegen Sie den Mauszeiger auf das Fadenkreuz zu verschieben.
3. Lassen Sie die Schaltfläche, um Teleport, in dem das Fadenkreuz platziert wurde.

**Um praktisch "Schritt für Schritt:"**
* Mithilfe von [motion Controller](motion-controllers.md): Klicken Sie auf unten auf dem Ministick und halten, und klicken Sie dann verschieben Ministick in die Richtung zu "durchlaufen".
* Verwenden einen Xbox-Controller: Klicken Sie auf unten auf der linken Ministick und halten, und klicken Sie dann verschieben Ministick in die Richtung zu "durchlaufen".

## <a name="immersive-headset-input-support"></a>Immersive Kopfhörer Unterstützung

[Windows Mixed Reality immersive Headsets](immersive-headset-hardware-details.md) verschiedene Eingabetypen zu unterstützen, für die Navigation in der Windows Mixed Reality home. HoloLens unterstützt keine Zubehör Eingaben für die Navigation, da Sie physisch aufzusuchen, und finden Sie in Ihrer Umgebung. HoloLens jedoch [Eingaben unterstützt](hardware-accessories.md) für die Interaktion mit apps.

### <a name="motion-controllers"></a>Motion-Controller

Die beste Windows Mixed Reality-Erfahrung werden mit Windows Mixed Reality [motion Controller](motion-controllers.md) , Unterstützung 6-von-Freiheitsgrade nachverfolgung, verwenden einfach die Sensoren in Ihrer Kopfhörer - keine externen Kameras oder Marker, die erforderlich sind.

Navigationsbefehle in Kürze verfügbar.

### <a name="gamepad"></a>Gamepad
* **Linken Ministick:**
  * Halten Sie den linken Ministick vorwärts um die [Teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) Fadenkreuz.
  * Tippen Sie auf die Links, rechts, Ministick oder zurück, die nach links verschoben, richtig, oder in kleinen Schritten zurück.
  * Klicken Sie auf unten auf der linken Ministick und halten, und klicken Sie dann Ministick in die Richtung zu verschieben [praktisch "durchlaufen".](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* Tippen Sie auf die **Ministick rechts** nach links oder rechts, um die Richtung drehen, die Sie um 45 Grad auftauchen.
* Drücken Sie die **ein** Schaltfläche führt eine SELECT-Anweisung und verhält sich wie die [tippbewegung](gestures.md#air-tap) Bewegung.
* Durch Drücken der **Handbuch** die Schaltfläche wird die [Menü "Start"](navigating-the-windows-mixed-reality-home.md#start-menu) und verhält sich wie die [Bloom](gestures.md#bloom) Geste.
* Drücken Sie die **linken und rechten Trigger** können Sie zoom in einer 2D-desktop-app, die Sie zu Hause interagieren können.

### <a name="keyboard-and-mouse"></a>Tastatur und Maus

**Hinweis**: Verwendung **Windows-Taste + Y** die Maus zwischen die Steuerung Ihres PC-Desktop und die Windows Mixed Reality home wechseln.

In der Windows Mixed Reality Startseite:
* Drücken Sie die **klicken** los führt eine SELECT-Anweisung und verhält sich wie die [tippbewegung](gestures.md#air-tap) Bewegung.
* Enthält die **mit der rechten Maustaste** Maustaste wird die [Teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) Fadenkreuz.
* Drücken Sie die **Windows** Taste auf der Tastatur wird die [Menü "Start"](navigating-the-windows-mixed-reality-home.md#start-menu) und verhält sich wie die [Bloom](gestures.md#bloom) Bewegung.
* Wenn [gazing](gaze.md) in einer 2D-desktop-app können **klicken** auswählen, **mit der rechten Maustaste** , Kontextmenüs anzuzeigen, und verwenden Sie die **Mausrad** um zu scrollen (wie es auch auf Ihrem PC Desktop).

## <a name="cortana"></a>Cortana

[Cortana](voice-input.md#hey-cortana) entspricht Ihrer persönlichen Assistenten in Windows Mixed Reality, auf dem PC und Telefon. HoloLens verfügt über ein eingebautes Mikrofon verfügen, aber immersive Headsets erfordert ggf. zusätzliche Hardware. Verwenden Sie Cortana-apps geöffnet, das Neustarten des Geräts, Dinge online suchen und vieles mehr. Entwickler können auch wählen, [Integrieren von Cortana](https://dev.windows.com/cortana) in ihrer Umgebung.

Sie können auch Sprachbefehle verwenden, zu Hause umgehen. Richten Sie z. B. auf eine Schaltfläche (mit [bestaunen](gaze.md) oder einen Controller, je nach Gerät), und sagen Sie "Select". Andere Sprachbefehle "Go Home", "Größer", "kleiner" einschließen "Schließen" und "Stehen mir."

## <a name="store-settings-and-system-apps"></a>Store, Einstellungen und System-apps

Windows Mixed Reality verfügt über eine Reihe integrierter apps, z. B.:
* **Microsoft Store** zum Abrufen von apps und Spiele
* **Feedback-Hub** zum Übermitteln von Feedback über das System und System-apps
* **Einstellungen** Systemeinstellungen konfigurieren ([einschließlich Netzwerke](connecting-to-wi-fi-on-hololens.md) und System-Updates)
* **Microsoft Edge** zum Durchsuchen von Websites
* **Fotos** anzeigen und Freigeben von Fotos und Videos
* **Kalibrierung** (nur für HoloLens) für die Anpassung von HoloLens Erfahrung, um den aktuellen Benutzer
* **Erfahren Sie, Gesten** (HoloLens) oder **erfahren Sie, Mixed Reality** (immersive Headsets), Informationen zur Verwendung Ihres Geräts
* **3D Viewer** , ergänzen Sie Ihre Welt mit mixed Reality-Inhalt
* **Mixed Reality-Portal** (Desktop-) für das Einrichten und verwalten Ihre immersive Kopfhörer und streaming eine Livevorschau Ihrer Ansicht in den Kopfhörer für andere Benutzer sehen.
* **Filme und Serien** zeigt für die Anzeige von 360 Videos und die neuesten Filme und Serien
* **Cortana** muss für alle Ihre virtuellen-Assistenten
* **Desktop** (immersive Headsets) zum Anzeigen Ihrer Desktopmonitor in eine immersive Kopfhörer
* **Datei-Explorer** Zugriff auf Dateien und Ordner auf Ihrem Gerät

## <a name="see-also"></a>Siehe auch
* [App-Ansichten](app-views.md)
* [Motion-Controller](motion-controllers.md)
* [Hardware-Zubehör](hardware-accessories.md)
* [Aspekte der Umgebung für HoloLens](environment-considerations-for-hololens.md)
* [Implementieren von 3D app-startfeldern](implementing-3d-app-launchers.md)
* [Erstellen von 3D-Modellen für die Verwendung zu Hause Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
