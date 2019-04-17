---
title: Verwenden den Emulator für HoloLens
description: Der Emulator für HoloLens können Sie zum Testen von mixed Reality-apps auf Ihren PC ohne ein physisches HoloLens.
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, emulator
ms.openlocfilehash: 3551bf48037f0cb7e8d243f2d89d43664e7c3475
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596684"
---
# <a name="using-the-hololens-emulator"></a>Verwenden den Emulator für HoloLens

Der Emulator für HoloLens können Sie holographic apps auf Ihren PC ohne ein physisches HoloLens testen und die HoloLens-Entwicklungs-Toolset enthält. Der Emulator verwendet eine Hyper-V-VM. Die menschlichen und environmental Eingaben, die in der Regel von den Sensoren für die HoloLens gelesen werden, werden stattdessen simuliert mithilfe Ihrer Tastatur, Maus oder Xbox-Controller. Apps müssen nicht geändert werden, führen Sie auf dem Emulator und weiß nicht, dass sie auf einem echten HoloLens ausgeführt werden nicht.

Wenn Sie zum Entwickeln von Windows Mixed Reality immersive apps unter (VR) Kopfhörer oder Spiele für desktop-PCs ansehen, sehen Sie sich die [Windows Mixed Reality-Simulator](using-the-windows-mixed-reality-simulator.md), sodass Sie stattdessen Remotedesktop Headsets zu simulieren.

> [!NOTE]
> Weitere Anleitungen, die speziell für HoloLens 2 [bald](index.md#news-and-notes).

## <a name="installing-the-hololens-emulator"></a>Installation des Emulators HoloLens

Herunterladen der [HoloLens (1. Generation)-Emulator und holographic Projektvorlagen](https://go.microsoft.com/fwlink/?linkid=2065980).

Älteren Builds von der Emulator für HoloLens finden Sie auf die [HoloLens emulatorarchiv](hololens-emulator-archive.md) Seite.

### <a name="hololens-emulator-system-requirements"></a>HoloLens-Emulator – Systemanforderungen

Der Emulator für HoloLens basiert auf Hyper-V und RemoteFx für Hardware beschleunigter Grafikfunktionen verwendet. Um den Emulator verwenden zu können, sicher, dass Ihr PC diese hardwareanforderungen erfüllt:
* 64-Bit-Windows 10 Pro, Enterprise und Education 
    >[!NOTE]
    >Windows 10 Home-Edition unterstützt keine Hyper-V oder den Emulator für HoloLens
* CPU mit 64 Bit
* CPU mit 4 Kerne (oder mehrere CPUs mit insgesamt 4 Kerne)
* 8 GB RAM oder mehr
* Das BIOS muss die folgenden Features [unterstützt und aktiviert](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):
   * Hardwareunterstützte Virtualisierung
   * Adressübersetzung der zweiten Ebene (Second Level Address Translation, SLAT)
   * Hardwarebasierte Datenausführungsverhinderung (Data Execution Prevention, DEP)
* GPU-Anforderungen (der Emulator funktioniert mit einer nicht unterstützten GPU, jedoch deutlich langsamer)
   * DirectX 11.0 oder höher
   * Treiber für WDDM 1.2 oder höher

Wenn Ihr System die oben genannten Anforderungen erfüllt **stellen Sie sicher, dass die Funktion "Hyper-V" auf dem System aktiviert wurde** über die Systemsteuerung -> Programme -> Programme und Funktionen auf -> Windows-Features aktivieren oder deaktivieren -> Stellen Sie sicher "Hyper-V" für die Emulator-Installation erfolgreich ausgewählt ist.

### <a name="installation-troubleshooting"></a>Problembehandlung der Installation

Bei der Installation des Emulators aus, die Sie benötigen möglicherweise einen Fehler angezeigt *"Visual Studio 2015 Update 1 und UWP-Tools Version 1.2"*. Es gibt drei mögliche Ursachen dieses Fehlers:
* Sie haben nicht die letzte Version von Visual Studio (Visual Studio 2017 oder Visual Studio 2015 Update 1 oder höher). Dieses Problem beheben, installieren Sie die neueste Version von Visual Studio.
* Sie haben die letzte Version von Visual Studio, aber Sie verfügen nicht über die universelle Windows-Plattform (UWP)-Tools installiert. Dies ist ein optionales Feature für Visual Studio.

Auch ein Fehler, die Installation des Emulators auf eine nicht-PRO/Enterprise/Education-SKU von Windows angezeigt werden kann oder wenn Hyper-V-Funktion möglicherweise nicht aktiviert.
* Lesen Sie die [Systemanforderungen](#hololens-emulator-system-requirements) Abschnitt einen vollständigen Satz von Anforderungen.
* Außerdem stellen Sie sicher, dass die Hyper-V-Feature auf Ihrem System aktiviert wurde.

## <a name="deploying-apps-to-the-hololens-emulator"></a>Bereitstellen von apps mit dem Emulator für HoloLens

1. Laden Sie die app-Projektmappe in Visual Studio 2015.
    >[!NOTE]
    >Wenn Unity verwenden zu können, erstellen Sie das Projekt aus Unity, und klicken Sie dann laden Sie die erstellte Lösung wie gewohnt in Visual Studio.
2. Stellen Sie sicher, die Plattform nastaven NA hodnotu **X86**.
3. Wählen Sie die **Emulator für HoloLens** als Zielgerät für das Debuggen.
4. Wechseln Sie zu **Debuggen > Debuggen starten** , oder drücken Sie **F5** zum Starten des Emulators und Bereitstellen Ihrer app für das Debuggen.

Der Emulator dauert eine Minute oder länger, beim ersten start zu starten. Es wird empfohlen, den Emulator zu open während der Debugsitzung, damit Sie schnell apps mit dem ausgeführten Emulator bereitstellen können.

## <a name="basic-emulator-input"></a>Grundlegende Emulator-Eingabe

Steuern des Emulators ähnelt sehr viele allgemeine 3D-Videospiele. Eingabeoptionen stehen zur Verfügung, mit der Tastatur, Maus oder Xbox-Controller. Sie steuern des Emulators durch die Aktionen eines simulierten Benutzers steht, geteert eine HoloLens weiterleiten. Ihre Aktionen zu verschieben, dass die simulierten Benutzer in aller und apps im Emulator zu reagieren, wie sie auf einem echten Gerät.
* **Schritt für Schritt nach vorne, zurück, links und rechts** -verwenden Sie die W, D, S und ein Schlüssel auf der Tastatur oder der linken Stick auf eine Xbox-Controller.
* **Suchen, nach unten, links und rechts** -Klick und Ziehen der Maus, verwenden Sie die Pfeiltasten auf der Tastatur oder der richtigen Stick auf eine Xbox-Controller.
* **Tippbewegung Luft** – mit der rechten Maustaste des Mauszeigers, drücken Sie die EINGABETASTE auf der Tastatur, oder verwenden Sie die A-Taste auf ein Xbox-Controller.
* **Blühen Geste** – drücken Sie die Windows-Taste oder F2-Taste auf der Tastatur, oder drücken Sie die Schaltfläche "B" auf eine Xbox-Controller.
* **Übergeben Sie die datenverschiebung für das Durchführen eines Bildlaufs** – gedrückter Alt-Taste, halten Sie die rechte Maustaste gedrückt, und ziehen Sie die Maus nach oben / unten, oder in ein Xbox-Controller halten der richtige Trigger und eine Schaltfläche und den richtigen Stick nach oben oder unten verschieben.

## <a name="anatomy-of-the-hololens-emulator"></a>Aufbau des Emulators HoloLens

### <a name="main-window"></a>Klicken Sie im Hauptfenster

Wenn der Emulator gestartet wird, sehen Sie ein Fenster der HoloLens Betriebssystem angezeigt.

![HoloLens-Emulator-Hauptfenster](images/emulator-890px.png)

### <a name="toolbar"></a>Symbolleiste

Klicken Sie auf der rechten Seite des Hauptfensters finden Sie die Symbolleiste des Emulators. Die Symbolleiste enthält die folgenden Schaltflächen:
* ![Symbol "Schließen"](images/emulator-close.png) **schließen**: Schließt den Emulator.
* ![Symbol "Minimieren"](images/emulator-minimize.png) **Minimieren**: Minimiert das Emulatorfenster.
* ![Symbol für menschliche input](images/emulator-control.png) **menschliche Input**: Maus und Tastatur werden verwendet, um menschliche simulieren [Eingabe für den Emulator](#basic-emulator-input).
* ![Tastatur und Maus Eingabe Symbol](images/emulator-input.png) **Tastatur- und Mauseingabe**: Tastatur- und Mauseingaben werden direkt an das Betriebssystem HoloLens als Tastatur-und Mausereignisse übergeben, als ob Sie eine Bluetooth-Tastatur und Maus verbunden.
* ![Passen auf das Symbol für bildschirmaufzeichnung](images/emulator-fit.png) **an Bildschirmgröße anpassen**: Passen den Emulator zum Bildschirm.
* ![Zoom icon](images/emulator-zoom.png) **Zoom**: Stellen Sie den Emulator, größere und kleinere.
* ![Symbol "Hilfe"](images/emulator-help.png) **Hilfe**: Öffnet die Emulator-Hilfe.
* ![Symbol für Portals offenes Gerät](images/emulator-deviceportal.png) **öffnen Device Portal**: Öffnen Sie die Windows Device Portal für das Betriebssystem HoloLens im Emulator.
* ![Tool-Symbol](images/emulator-tools.png) **Tools**: Öffnen der **zusätzliche Tools** Bereich.

### <a name="simulation-tab"></a>Registerkarte "Simulation"

Die Standardregisterkarte innerhalb der **zusätzliche Tools** Bereich ist die **Simulation** Registerkarte.

![HoloLens-Emulator "Zusätzliche Tools" im Bereich](images/emulator-simulation-500px.png)

Die Registerkarte "Simulation" zeigt den aktuellen Status der simulierten Sensoren verwendet, um die HoloLens-Betriebssystemlaufwerk innerhalb des Emulators. Mit dem Mauszeiger auf einen beliebigen Wert in der Registerkarte "Simulation" bietet eine QuickInfo, die beschreibt, wie dieses Werts zu steuern.

### <a name="room-tab"></a>Registerkarte "Raum"

Der Serveremulator simuliert die Eingabe der Welt in Form des Netzes räumliche Zuordnung von simulierten "Räume". Auf dieser Registerkarte können Sie auswählen, welche Platz um statt der standardraum zu laden.

![HoloLens-Emulator "Räume"-Registerkarte](images/emulator-room-500px.png)

Simulierte Räume sind hilfreich beim Testen Ihrer app in mehreren Umgebungen. Mehrere Räume sind im Lieferumfang des Emulators aus, und nach der Installation der Emulations finden sie im Verzeichnis % ProgramFiles(x86) %\Programme%\Microsoft Dateien (x86) \Microsoft XDE\10.0.11082.0\Plugins\Rooms. Alle diese Räume wurden in realen Umgebungen, die mithilfe einer HoloLens erfasst:
* **DefaultRoom.xef** – eine kleine Wohnzimmer mit einem Fernsehgerät Kaffee-Tabelle und zwei Sofas. Standardmäßig geladen, wenn Sie den Emulator zu starten.
* **Bedroom1.xef** – eine kleine Schlafzimmer mit einem Schreibtisch.
* **Bedroom2.xef** -Schlafzimmer mit einer Dame Größe konzentrieren, Kommode, Nightstands und walk-in Wandschrank.
* **GreatRoom.xef** – eine hervorragende großen leeren Bereich-Raum mit Wohnzimmer, Trinken Tabellen- und Küche.
* **LivingRoom.xef** – ein Wohnzimmer mit einer Kamin, Sofa, Armchairs und einen Kaffee-Tabelle mit einer Vase.

Sie können auch eigene Räume für die Verwendung im Serveremulator mithilfe der Simulation Seite Aufzeichnen der [Windows Device Portal](using-the-windows-device-portal.md) auf Ihre HoloLens.

Auf dem Emulator verwenden sehen Sie nur Hologramme, dass Sie rendern und simulierten Raum hinter der Hologramme wird nicht angezeigt. Dies ist im Gegensatz zu den tatsächlichen HoloLens, in denen Sie sowohl finden Sie unter, gemischt. Sie können die simulierten Platz im Emulator HoloLens finden Sie unter müssen Sie Ihre app zum Rendern der Gitter räumliche Zuordnung, in der Szene aktualisiert werden.

### <a name="account-tab"></a>Die Registerkarte „Konto“

Die Registerkarte "Konto" können Sie den Emulator mit einem Microsoft Account anmelden zu konfigurieren. Dies ist hilfreich beim Testen der API, die der Benutzer mit einem Konto angemeldet sein muss. Nachdem Sie das Kontrollkästchen auf dieser Seite, nachfolgenden Starts des Emulators fordert Sie zur Anmeldung aus, wie ein Benutzer erstmals die HoloLens gestartet wird.

## <a name="see-also"></a>Siehe auch
* [Erweiterte HoloLens-Emulator und Mixed Reality-Simulator-Eingabe](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [HoloLens-Emulator-Software-Verlauf](hololens-emulator-archive.md)
* [Räumliche Zuordnung in Unity](spatial-mapping-in-unity.md)
* [Räumliche Zuordnung in DirectX](spatial-mapping-in-directx.md)
