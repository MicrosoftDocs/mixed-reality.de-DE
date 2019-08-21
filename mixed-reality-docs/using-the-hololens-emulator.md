---
title: Verwendung des HoloLens-Emulators
description: Mit dem HoloLens-Emulator können Sie Mixed Reality-Apps auf Ihrem PC ohne eine physische HoloLens testen.
author: pbarnettms
ms.author: pbarnett
ms.date: 08/14/2019
ms.topic: article
ms.localizationpriority: high
keywords: HoloLens, Emulator
ms.openlocfilehash: 6c112b7706f1dfff7c4affbdb4ee7326f0e15c8a
ms.sourcegitcommit: 06c27acdac24c845952f9c1d3611770756f25820
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2019
ms.locfileid: "69030173"
---
# <a name="using-the-hololens-emulator"></a>Verwendung des HoloLens-Emulators

Mit dem HoloLens-Emulator können Sie holografische Anwendungen auf Ihrem PC ohne eine physische HoloLens testen. Er enthält außerdem das HoloLens-Entwicklungstoolset. Der Emulator verwendet einen virtuellen Hyper-V-Computer. Die Eingaben der Benutzer und der Umgebung, die normalerweise von den Sensoren der HoloLens erfasst werden, werden von Ihrer Tastatur, Maus oder dem Xbox-Controller simuliert. Anwendungen müssen nicht modifiziert werden, um auf dem Emulator zu funktionieren. Zudem erkennen sie nicht, dass sie nicht auf einer echten HoloLens ausgeführt werden.

Wenn Sie Anwendungen für immersive Windows Mixed Reality-Headsets (VR) oder Spiele für Desktop-PCs entwickeln möchten, testen Sie den [Windows Mixed Reality-Simulator](using-the-windows-mixed-reality-simulator.md), mit dem Sie Desktop-Headsets simulieren können.


## <a name="installing-the-hololens-emulator"></a>Installieren des HoloLens-Emulators
Lade den HoloLens-Emulator herunter.

Versionen: 
* [HoloLens 2-Emulator](https://go.microsoft.com/fwlink/?linkid=2101019).
* [HoloLens-Emulator (1. Generation) und holografische Projektvorlagen](https://go.microsoft.com/fwlink/?linkid=2065980)

Ältere Builds des HoloLens-Emulators finden Sie auf der Seite [HoloLens-Emulator – Archiv](hololens-emulator-archive.md).

### <a name="hololens-emulator-system-requirements"></a>HoloLens-Emulator – Systemanforderungen

Der HoloLens-Emulator verwendet Hyper-V mit RemoteFx (Emulator der 1. Generation) oder GPU-PV (HoloLens 2-Emulator) für Grafiken mit Hardwarebeschleunigung. Um den Emulator zu verwenden, stellen Sie sicher, dass Ihr PC die folgenden Hardwareanforderungen erfüllt:
* Windows 10 Pro, Enterprise oder Education – 64-Bit 
    >[!NOTE]
    >Windows 10 Home-Edition unterstützt Hyper-V oder den HoloLens-Emulator nicht.  
    >Der HoloLens 2-Emulator benötigt das Windows 10 October 2018 Update oder höher.
* 64-Bit-CPU
* CPU mit 4 Kernen (oder mehrere CPUs mit insgesamt 4 Kernen)
* Mindestens 8 GB RAM
* Im BIOS müssen die folgenden Features [unterstützt und aktiviert sein](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):
   * Hardwareunterstützte Virtualisierung
   * Adressübersetzung der zweiten Ebene (Second Level Address Translation, SLAT)
   * Hardwarebasierte Datenausführungsverhinderung (Data Execution Prevention, DEP)
* GPU-Anforderungen
   * DirectX 11.0 oder höher
   * Grafiktreiber für WDDM 1.2 oder höher (1. Generation)
   * Grafiktreiber für WDDM 2.5 (HoloLens 2-Emulator)
   * Der Emulator funktioniert möglicherweise mit einem nicht unterstützten Grafikprozessor, ist aber deutlich langsamer

Wenn Ihr System die oben aufgeführten Anforderungen erfüllt, **stellen Sie sicher, dass das Feature „Hyper-V“ auf Ihrem System** über „Systemsteuerung -> Programme -> Programme -> Programme und Features -> Windows-Features aktivieren oder deaktivieren“ aktiviert wurde. Stellen Sie sicher, dass „Hyper-V“ aktiviert ist, damit die Emulatorinstallation erfolgreich ist.

## <a name="deploying-apps-to-the-hololens-emulator"></a>Bereitstellen von Apps für den HoloLens-Emulator

1. Laden Sie Ihre Anwendungslösung in Visual Studio.
    >[!NOTE]
    >Wenn Sie Unity verwenden, erstellen Sie Ihr Projekt in Unity, und laden Sie dann die erstellte Lösung wie gewohnt in Visual Studio.
2. Stellen Sie für HoloLens-Emulator (1. Generation) sicher, dass die Plattform auf **x86** eingestellt ist. Stellen Sie für den HoloLens 2-Emulator sicher, dass die Plattform auf **x86** oder **x64** eingestellt ist.
3. Wählen Sie die gewünschte Version für den **HoloLens-Emulator** als Zielgerät für das Debugging aus.
4. Wechseln Sie zu **Debuggen > Debuggen starten** oder drücken Sie **F5**, um den Emulator zu starten und Ihre Anwendung für das Debuggen bereitzustellen.

Der Emulator kann beim ersten Start eine Minute oder länger benötigen. Es wird empfohlen, den Emulator während der Debugsitzung geöffnet zu lassen, damit Sie Anwendungen schnell im Emulator bereitstellen können.

## <a name="basic-emulator-input"></a>Grundlegende Emulatoreingabe

Die Steuerung des Emulators ist mit vielen gängigen 3D-Videospielen vergleichbar. Es sind Eingabeoptionen über die Tastatur, Maus oder den Xbox-Controller verfügbar. Sie steuern den Emulator, indem Sie die Aktionen eines simulierten Benutzers durch Tragen einer HoloLens steuern. Ihre Aktionen bewegen den simulierten Benutzer in der Umgebung. Anwendungen, die im Emulator ausgeführt werden, reagieren wie auf einem echten Gerät.

Der Cursor der HoloLens (1. Generation) folgt der Kopfbewegung und -drehung. Im HoloLens 2-Emulator folgt der Cursor der Handbewegung und der Ausrichtung.

* **Nach vorne, hinten, links und rechts gehen**: Verwenden Sie die Tasten W, A, S und D auf Ihrer Tastatur oder den linken Stick eines Xbox-Controllers.
* **Nach oben, unten, links und rechts schauen**: Klicken und ziehen Sie mit der Maus, verwenden Sie die Pfeiltasten auf Ihrer Tastatur oder den rechten Stick eines Xbox-Controllers.
* **Tippbewegung in die Luft**: Klicken Sie mit der rechten Maustaste, drücken Sie die Eingabetaste auf Ihrer Tastatur, oder verwenden Sie die Taste A eines Xbox-Controllers.
* **Öffnen/Systemgeste**: Drücken Sie die Windows-Taste oder die F2-Taste auf Ihrer Tastatur, oder drücken Sie die B-Taste eines Xbox-Controllers.
* **Handbewegung zum Scrollen**: Halten Sie gleichzeitig die ALT-Taste und die rechte Maustaste gedrückt, und ziehen Sie die Maus nach oben oder unten, oder halten Sie den rechten Auslöser und die Taste A eines Xbox-Controllers gedrückt, und bewegen Sie den rechten Stick auf und ab.
* **Handbewegung und Ausrichtung**: (nur HoloLens 2-Emulator) Halten Sie die ALT-Taste gedrückt, und ziehen Sie die Maus nach oben oder unten, links oder rechts, um die Hand zu bewegen, oder verwenden Sie die Pfeiltasten und Q oder E, um die Hand zu drehen und zu neigen. Bei einem Xbox-Controller halten Sie den linken oder rechten Bumper gedrückt, und verwenden Sie den linken Stick, um die Hand nach links, rechts, vorne und hinten zu bewegen, den rechten Stick, um die Hand zu drehen, und bewegen Sie das Dpad nach oben oder unten, um die Hand anzuheben oder zu senken.

## <a name="anatomy-of-the-hololens-2-emulator"></a>Aufbau des HoloLens 2-Emulators 

### <a name="main-window"></a>Hauptfenster

![Hauptfenster des HoloLens 2-Emulators](images/emulator2-900px.png)

### <a name="toolbar"></a>Symbolleiste

Rechts neben dem Hauptfenster befindet sich die Symbolleiste des Emulators. Die Symbolleiste enthält die folgenden Schaltflächen:
* ![Schließen-Symbol](images/emulator-close.png) **Schließen**: Schließt den Emulator.
* ![Minimieren-Symbol](images/emulator-minimize.png) **Minimieren**: Minimiert das Emulatorfenster.
* ![Simulation-Symbol](images/emulator-simulation-panel.png) **Systemsteuerung der Simulation**: Blenden Sie die [Systemsteuerung der Simulation](#simulation-control-panel) zum Konfigurieren und Steuern der [Eingabe für den Emulator](#basic-emulator-input) ein oder aus.
* ![Bildschirmgröße anpassen-Symbol](images/emulator-fit.png) **Bildschirmgröße anpassen**: Passt den Emulator an den Bildschirm an.
* ![Zoom-Symbol](images/emulator-zoom.png) **Zoomen**: Vergrößern und verkleinern Sie den Emulator.
* ![Hilfe-Symbol](images/emulator-help.png) **Hilfe**: Öffnen Sie die Hilfe zum Emulator.
* ![Symbol „Geräteportal öffnen“](images/emulator-deviceportal.png) **Geräteportal öffnen**: Öffnen Sie das Windows-Geräteportal für das HoloLens-Betriebssystem im Emulator.
* ![Tools-Symbol](images/emulator-tools.png) **Tools**: Öffnen Sie den Bereich für **zusätzliche Tools**.

### <a name="simulation-control-panel"></a>Systemsteuerung der Simulation

Mithilfe der Systemsteuerung der Simulation können Sie die aktuelle Position und Ausrichtung des simulierten Benutzers und der simulierten Eingabegeräte anzeigen. Sie ermöglicht es Ihnen auch, sowohl simulierte Eingaben, wie das Ein- und Ausblenden einer oder beider Hände, als auch Geräte zur Steuerung simulierter Eingaben, wie Tastatur, Maus und Gamepad Ihres PCs, zu konfigurieren.

![Systemsteuerung der Simulation](images/emulator-simulation-control-panel.png)

* Um die Systemsteuerung der Simulation ein- oder auszublenden, klicken Sie auf die Symbolleistenschaltfläche, oder drücken Sie F7 auf der Tastatur.
* Bewegen Sie den Mauszeiger über ein Steuerelement oder Feld, um eine QuickInfo anzuzeigen, die zugehörige Tastatur-, Maus- und Gamepad-Steuerelemente enthält.
* Um eine Hand ein- oder auszublenden, schalten Sie den entsprechenden Schalter unter der linken oder rechten Hand um.
* Verwenden Sie zum Steuern der Hand entweder die linke oder rechte ALT-Taste auf Ihrer Tastatur oder den linken oder rechten Bumper des Gamepads.
* Um alle Eingaben an eine oder beide Hände weiterzuleiten, klicken Sie auf die Markierungstaste unter dem Umschalter.  Dies entspricht dem Halten der ALT-Taste für die Hand.
* Klicken Sie zur Steuerung der Richtung für das Anvisieren mit den Augen auf die Markierung im Abschnitt „Eyes“ (Augen). Dies entspricht dem Halten der Y-Taste auf der Tastatur.
* Klicken Sie zum Laden einer Raumaufzeichnung auf die Schaltfläche „Load“ (Laden) im Abschnitt „Recording“ (Aufzeichnung). Weitere Informationen finden Sie unter [simulierte Räume](#simulated-rooms).
* Um die Geschwindigkeit anzupassen, mit der sich der simulierte Benutzer oder die simulierten Eingabegeräte als Reaktion auf die Eingabe von Tastatur, Maus oder Gamepad bewegen oder drehen, klicken Sie auf das Zahnradsymbol neben „Input settings“ (Eingabeeinstellungen), und passen Sie die Schieberegler an.
* Standardmäßig steuert die Tastatureingabe den simulierten Benutzer und die simulierte Eingabe. Damit die Tastatureingabe Ihres PCs an die HoloLens weitergeleitet wird, deaktivieren Sie das Kontrollkästchen „Use Keyboard for Simulation“ (Tastatur für Simulation verwenden).  F4 ist die Tastenkombination für diese Einstellung.
* Wenn der Simulationsbereich bereits angezeigt wird, drücken Sie F8, um den Tastaturfokus dorthin zu verschieben.
* Klicken Sie auf die Schaltfläche am unteren Rand des Bereichs, oder drücken Sie F9 auf Ihrer Tastatur, um den Simulationsbereich beim Emulatorfenster auszudocken.  Wenn Sie das Fenster schließen oder erneut F9 drücken, kehrt das Fenster zum Emulator zurück.
* Die Systemsteuerung der Simulation kann als separate Anwendung gestartet werden, sodass Sie sich mit dem HoloLens 2-Emulator, einem HoloLens 2-Gerät oder der Windows Mixed Reality-Simulation verbinden und dieses steuern können, indem Sie „PerceptionSimulationInput.exe“ unter „%ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\10.0.18362.0\“ ausführen.

### <a name="account-tab"></a>Die Registerkarte „Konto“

Auf der Registerkarte „Account“ (Konto) können Sie den Emulator für die Anmeldung mit einem Microsoft-Konto konfigurieren. Dies ist beim Testen von APIs hilfreich, bei denen der Benutzer mit einem Konto angemeldet sein muss. Das Umschalten dieser Option erfordert, dass Sie den HoloLens-Emulator vollständig schließen und neu starten, damit die Einstellung wirksam wird. Wenn diese Option aktiviert ist, werden Sie bei nachfolgenden Starts des Emulators zur Anmeldung aufgefordert, genau wie ein Benutzer beim ersten Start der HoloLens. Um Ihre Anmeldeinformationen über die Tastatur Ihres PCs einzugeben, deaktivieren Sie zunächst „Use Keyboard for Simulation“ (Tastatur für Simulation verwenden) in der Systemsteuerung für die Simulation, oder drücken Sie F4 auf Ihrer Tastatur, um die Tastatureinstellung zu aktivieren oder zu deaktivieren.

### <a name="optional-settings-tab"></a>Registerkarte „Optional Settings“ (Optionale Einstellungen)

Auf der Registerkarte „Optional Settings“ (Optionale Einstellungen) wird ein Steuerelement angezeigt, mit dem hardwarebeschleunigte Grafiken aktiviert oder deaktiviert werden können. Hardwarebeschleunigte Grafiken werden standardmäßig verwendet, wenn sie vom Treiber für die Grafikkarte Ihres PCs unterstützt werden. Wenn der Treiber Ihrer Grafikkarte „GPU-PV“ nicht unterstützt, wird diese Option nicht angezeigt.

### <a name="diagnostics-tab"></a>Registerkarte „Diagnostics“ (Diagnose)

Auf der Registerkarte „Diagnostics“ (Diagnose) wird die IP-Adresse des Emulators in Form eines Links zum Windows-Geräteportal sowie der Status der virtuellen GPU angezeigt.


## <a name="anatomy-of-the-hololens-1st-gen-emulator"></a>Aufbau des HoloLens-Emulators (1. Generation)

### <a name="main-window"></a>Hauptfenster

Beim Starten des Emulators wird ein Fenster mit dem HoloLens-Betriebssystem angezeigt.

![Hauptfenster des HoloLens-Emulators](images/emulator-890px.png)

### <a name="toolbar"></a>Symbolleiste

Rechts neben dem Hauptfenster befindet sich die Symbolleiste des Emulators. Die Symbolleiste enthält die folgenden Schaltflächen:
* ![Schließen-Symbol](images/emulator-close.png) **Schließen**: Schließt den Emulator.
* ![Minimieren-Symbol](images/emulator-minimize.png) **Minimieren**: Minimiert das Emulatorfenster.
* ![Symbol „Benutzereingabe“](images/emulator-control.png) **Benutzereingabe**: Maus und Tastatur werden verwendet, um die [Benutzereingaben für den Emulator](#basic-emulator-input) zu simulieren.
* ![Symbol „Tastatur- und Mauseingabe“](images/emulator-input.png) **Tastatur- und Mauseingabe**: Tastatur- und Mauseingaben werden als Tastatur- und Mausereignisse direkt an das HoloLens-Betriebssystem übergeben, als ob Sie eine Bluetooth-Tastatur und -Maus angeschlossen hätten.
* ![Bildschirmgröße anpassen-Symbol](images/emulator-fit.png) **Bildschirmgröße anpassen**: Passt den Emulator an den Bildschirm an.
* ![Zoom-Symbol](images/emulator-zoom.png) **Zoomen**: Vergrößert und verkleinert den Emulator.
* ![Hilfe-Symbol](images/emulator-help.png) **Hilfe**: Öffnet die Hilfe zum Emulator.
* ![Symbol „Geräteportal öffnen“](images/emulator-deviceportal.png) **Geräteportal öffnen**: Öffnen Sie das Windows-Geräteportal für das HoloLens-Betriebssystem im Emulator.
* ![Tools-Symbol](images/emulator-tools.png) **Tools**: Öffnen Sie den Bereich für **zusätzliche Tools**.

### <a name="simulation-tab"></a>Registerkarte „Simulation“

Die Standardregisterkarte im Bereich **Additional Tools** (Zusätzliche Tools) ist die Registerkarte **Simulation**.

![Bereich „Additional Tools“ (Zusätzliche Tools) des HoloLens-Emulators](images/emulator-simulation-500px.png)

Die Registerkarte „Simulation“ zeigt den aktuellen Zustand der simulierten Sensoren an, mit denen das HoloLens-Betriebssystem im Emulator gesteuert wird. Wenn Sie den Mauszeiger über einen beliebigen Wert auf der Registerkarte „Simulation“ bewegen, wird eine QuickInfo angezeigt, die beschreibt, wie Sie diesen Wert steuern können.

### <a name="room-tab"></a>Registerkarte „Room“ (Raum)

Der Emulator simuliert die Eingaben für die Umgebung in Form des Gittermodells für die räumliche Abbildung aus simulierten Räumen. Auf dieser Registerkarte können Sie anstelle des Standardraums den zu ladenden Raum auswählen.

![Registerkarte „Rooms“ (Räume) des HoloLens-Emulators](images/emulator-room-500px.png)

Weitere Informationen finden Sie unter [simulierte Räume](#simulated-rooms).

### <a name="account-tab"></a>Die Registerkarte „Konto“

Auf der Registerkarte „Account“ (Konto) können Sie den Emulator für die Anmeldung mit einem Microsoft-Konto konfigurieren. Dies ist beim Testen von APIs hilfreich, bei denen der Benutzer mit einem Konto angemeldet sein muss. Nachdem Sie das Kontrollkästchen auf dieser Seite aktiviert haben, werden Sie bei nachfolgenden Starts des Emulators zur Anmeldung aufgefordert, genau wie ein Benutzer beim ersten Start der HoloLens.

## <a name="simulated-rooms"></a>Simulierte Räume

Simulierte Räume sind hilfreich, um Ihre Anwendung in mehreren Umgebungen zu testen. Zusammen mit dem Emulator werden mehrere Räume ausgeliefert. Sobald Sie die Emulation installiert haben, finden Sie diese unter „%ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\\(version)\Plugins\Rooms“. Alle diese Räume wurden in realen Umgebungen mit einer HoloLens erfasst:
* **DefaultRoom.xef**: Ein kleines Wohnzimmer mit Fernseher, Couchtisch und zwei Sofas. Beim Starten des Emulators wird dieser Raum standardmäßig geladen.
* **Bedroom1.xef**: Ein kleines Schlafzimmer mit einem Schreibtisch.
* **Bedroom2.xef**: Ein Schlafzimmer mit einem Doppelbett, einer Kommode, Nachttischen und einem begehbaren Kleiderschrank.
* **GreatRoom.xef**: Ein großer offener Raum mit großem Wohnzimmer, Esstisch und Küche.
* **LivingRoom.xef**: Ein Wohnzimmer mit Kamin, Sofa, Sesseln und einem Couchtisch mit Vase.

Sie können auch eigene Räume aufzeichnen, die Sie im Emulator verwenden können, indem Sie die Seite „Simulation“ des [Windows-Geräteportals](using-the-windows-device-portal.md) für Ihre HoloLens (1. Generation) verwenden.

Im Emulator sehen Sie nur die von Ihnen gerenderten Hologramme. Den simulierten Raum hinter den Hologrammen können Sie jedoch nicht sehen. Dies steht im Gegensatz zur tatsächlichen HoloLens, bei der beides kombiniert zu sehen ist. Wenn Sie den simulierten Raum im HoloLens-Emulator anzeigen möchten, müssen Sie Ihre Anwendung aktualisieren, um das Gittermodell für die räumliche Abbildung in der Szene darzustellen.

## <a name="troubleshooting"></a>Problembehandlung

Möglicherweise wird bei der Installation des Emulators ein Fehler angezeigt, dass Sie *Visual Studio 2015 Update 1 und die UWP-Tools Version 1.2* benötigen. Es gibt drei mögliche Ursachen für diesen Fehler:
* Sie verfügen nicht über eine ausreichend aktuelle Version von Visual Studio (Visual Studio 2019, Visual Studio 2017 oder Visual Studio 2015 Update 1 oder höher). Installieren Sie zur Behebung dieses Problems die neueste Version von Visual Studio.
* Sie verfügen über eine neuere Version von Visual Studio, aber Sie haben nicht die UWP-Tools (universelle Windows-Plattform) installiert. Dies ist ein optionales Feature für Visual Studio.

Möglicherweise wird auch ein Fehler bei der Installation des Emulators auf einer Nicht-Pro/-Enterprise/-Education-SKU von Windows angezeigt, oder wenn Sie das Hyper-V-Feature nicht aktiviert haben.
* Eine vollständige Liste der Anforderungen finden Sie oben im Abschnitt [Systemanforderungen](#hololens-emulator-system-requirements).
* Stellen Sie außerdem sicher, dass das Hyper-V-Feature auf Ihrem System aktiviert ist.

Wenn Ihre Installation erfolgreich abgeschlossen wurde, der HoloLens-Emulator jedoch nicht als Option für die Bereitstellung und das Debuggen zur Verfügung steht, überprüfen Sie die folgenden Punkte:
* Ihre Visual Studio-Projektkonfiguration ist auf x86 (HoloLens 1. Generation) bzw. x86 oder x64 (HoloLens 2-Emulator) eingestellt.
* Wenn Sie Visual Studio 2019 verwenden, ist das Plattformtoolset in Ihrer Projektkonfiguration auf „v142“ festgelegt.

Wenn Ihre Installation erfolgreich abgeschlossen wurde, Visual Studio jedoch beim Starten des HoloLens-Emulators einen Fehler anzeigt, versuchen Sie Folgendes:
* Ausführen von Visual Studio als Administrator
* Wenn Sie nur Visual Studio 2019 installiert haben, vergewissern Sie sich, dass der Registrierungswert „KitsRoot10“ unter „HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Kits\Installed Roots“ auf Ihren 32-Bit-Ordner für „Program Files“ zeigt (z. B. „C:\Program Files (x86)\Windows Kits\10“).  Wenn dies nicht der Fall ist, deinstallieren Sie den HoloLens-Emulator, ändern Sie den Registrierungswert in Ihren 32-Bit-Ordner für „Program Files“, und installieren Sie dann den HoloLens-Emulator erneut.  Dieses Problem wird in Visual Studio 2019 16.0.3 behandelt.

Wenn der Emulator beim Start ein Fehlerdialogfeld „Ungültige Bytecodierung“ anzeigt:
* Löschen Sie alle Dateien in „%localappdata%\Microsoft\XDE\HCS“ und versuchen Sie es erneut.

Wenn Ihre Liste der Debugziele in Visual Studio leer ist (z. B. ist „Start“ die einzige Option) und Sie alle oben genannten Schritte zur Problembehandlung ausgeführt haben:
* Löschen Sie den Ordner „ConfigurationCache“ in „%localappdata%\Microsoft\VisualStudio\\<*Installations-ID*>\CoreCon“ und versuchen Sie es erneut.

Wenn Ihr System beim Starten des Emulators hängen bleibt, deaktivieren Sie die Hardwarebeschleunigung für Emulatorgrafiken.
* Erstellen Sie in der Registrierung einen DWORD-Wert namens „DisableGPU“ unter „HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\XDE\10.0“, und legen Sie seinen Wert auf 1 fest.

## <a name="see-also"></a>Weitere Informationen
* [Erweiterte Eingabe für HoloLens-Emulator und Mixed Reality-Simulator](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [HoloLens-Emulator – Softwareverlauf](hololens-emulator-archive.md)
* [Räumliche Abbildung in Unity](spatial-mapping-in-unity.md)
* [Räumliche Abbildung in DirectX](spatial-mapping-in-directx.md)
