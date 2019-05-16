---
title: Verwenden den Emulator für HoloLens
description: Der Emulator für HoloLens können Sie zum Testen von mixed Reality-apps auf Ihren PC ohne ein physisches HoloLens.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
ms.localizationpriority: high
keywords: HoloLens, emulator
ms.openlocfilehash: 0dfca73e6c8e1809e1bea3df6ca344b3de0698d5
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730921"
---
# <a name="using-the-hololens-emulator"></a>Verwenden den Emulator für HoloLens

Der Emulator für HoloLens können Sie holographic apps auf Ihren PC ohne ein physisches HoloLens testen und die HoloLens-Entwicklungs-Toolset enthält. Der Emulator verwendet eine Hyper-V-VM. Die menschlichen und environmental Eingaben, die in der Regel von den Sensoren für die HoloLens gelesen werden, werden stattdessen simuliert mithilfe Ihrer Tastatur, Maus oder Xbox-Controller. Apps müssen nicht geändert werden, führen Sie auf dem Emulator und weiß nicht, dass sie auf einem echten HoloLens ausgeführt werden nicht.

Wenn Sie zum Entwickeln von Windows Mixed Reality immersive apps unter (VR) Kopfhörer oder Spiele für desktop-PCs ansehen, sehen Sie sich die [Windows Mixed Reality-Simulator](using-the-windows-mixed-reality-simulator.md), sodass Sie stattdessen Remotedesktop Headsets zu simulieren.


## <a name="installing-the-hololens-emulator"></a>Installation des Emulators HoloLens
Emulator für HoloLens und holographic Projektvorlagen herunterladen.

Versions: 
* [2-Emulator für HoloLens und holographic Projektvorlagen](https://go.microsoft.com/fwlink/?linkid=2087187).
* [HoloLens-Emulator (1. Generation) und holographic Projektvorlagen](https://go.microsoft.com/fwlink/?linkid=2065980).

Älteren Builds von der Emulator für HoloLens finden Sie auf die [HoloLens emulatorarchiv](hololens-emulator-archive.md) Seite.

### <a name="hololens-emulator-system-requirements"></a>HoloLens-Emulator – Systemanforderungen

Der Emulator für HoloLens verwendet Hyper-V mit RemoteFx (1. Generation Emulator) oder GPU-PV (2-Emulator für HoloLens) Hardware beschleunigt Grafiken. Um den Emulator verwenden zu können, sicher, dass Ihr PC diese hardwareanforderungen erfüllt:
* 64-Bit-Windows 10 Pro, Enterprise und Education 
    >[!NOTE]
    >Windows 10 Home-Edition unterstützt Hyper-V oder den Emulator für HoloLens nicht.  
    >Der 2-Emulator für HoloLens erfordert das Windows 10 Oktober 2018 update oder höher.
* CPU mit 64 Bit
* CPU mit 4 Kerne (oder mehrere CPUs mit insgesamt 4 Kerne)
* 8 GB RAM oder mehr
* Das BIOS muss die folgenden Features [unterstützt und aktiviert](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):
   * Hardwareunterstützte Virtualisierung
   * Adressübersetzung der zweiten Ebene (Second Level Address Translation, SLAT)
   * Hardwarebasierte Datenausführungsverhinderung (Data Execution Prevention, DEP)
* GPU-Anforderungen
   * DirectX 11.0 oder höher
   * Grafik-Treiber für WDDM 1.2 oder höher (1. Generation)
   * Treiber für WDDM 2.5-Grafik (2-Emulator für HoloLens)
   * Der Emulator mit einer nicht unterstützten GPU funktionieren möglicherweise, jedoch deutlich langsamer

Wenn Ihr System die oben genannten Anforderungen erfüllt **stellen Sie sicher, dass die Funktion "Hyper-V" auf dem System aktiviert wurde** über die Systemsteuerung -> Programme -> Programme und Funktionen auf -> Windows-Features aktivieren oder deaktivieren -> Stellen Sie sicher "Hyper-V" für die Emulator-Installation erfolgreich ausgewählt ist.

## <a name="deploying-apps-to-the-hololens-emulator"></a>Bereitstellen von apps mit dem Emulator für HoloLens

1. Laden Sie die app-Projektmappe in Visual Studio.
    >[!NOTE]
    >Wenn Unity verwenden zu können, erstellen Sie das Projekt aus Unity, und klicken Sie dann laden Sie die erstellte Lösung wie gewohnt in Visual Studio.
2. Für den Emulator für HoloLens (der 1. Generation), stellen Sie sicher, die Plattform nastaven NA hodnotu **X86**. Der 2-Emulator für HoloLens stellen Sie sicher die Plattform nastaven NA hodnotu **X86** oder **X64**.
3. Wählen Sie den gewünschten **Emulator für HoloLens** Version als Zielgerät für das Debuggen.
4. Wechseln Sie zu **Debuggen > Debuggen starten** , oder drücken Sie **F5** zum Starten des Emulators und Bereitstellen Ihrer app für das Debuggen.

Der Emulator dauert eine Minute oder länger, beim ersten start zu starten. Es wird empfohlen, den Emulator zu open während der Debugsitzung, damit Sie schnell apps mit dem ausgeführten Emulator bereitstellen können.

## <a name="basic-emulator-input"></a>Grundlegende Emulator-Eingabe

Steuern des Emulators ähnelt sehr viele allgemeine 3D-Videospiele. Eingabeoptionen stehen zur Verfügung, mit der Tastatur, Maus oder Xbox-Controller. Sie steuern des Emulators durch die Aktionen eines simulierten Benutzers steht, geteert eine HoloLens weiterleiten. Ihre Aktionen zu verschieben, dass die simulierten Benutzer in aller und apps im Emulator zu reagieren, wie sie auf einem echten Gerät.

Der Cursor für HoloLens (1. Generation) folgt, Bewegungen und Drehung.  Im Emulator 2 HoloLens folgt der Cursor manuell verschieben und Ausrichtung.

* **Schritt für Schritt nach vorne, zurück, links und rechts** -verwenden Sie die W, D, S und ein Schlüssel auf der Tastatur oder der linken Stick auf eine Xbox-Controller.
* **Suchen, nach unten, links und rechts** -Klick und Ziehen der Maus, verwenden Sie die Pfeiltasten auf der Tastatur oder der richtigen Stick auf eine Xbox-Controller.
* **Tippbewegung Luft** – mit der rechten Maustaste des Mauszeigers, drücken Sie die EINGABETASTE auf der Tastatur, oder verwenden Sie die A-Taste auf ein Xbox-Controller.
* **Bloom/systemstiftbewegung** – drücken Sie die Windows-Taste oder F2-Taste auf der Tastatur, oder drücken Sie die Schaltfläche "B" auf eine Xbox-Controller.
* **Übergeben Sie die datenverschiebung für das Durchführen eines Bildlaufs** – gedrückter Alt-Taste, halten Sie die rechte Maustaste gedrückt, und ziehen Sie die Maus nach oben / unten, oder in ein Xbox-Controller halten der richtige Trigger und eine Schaltfläche und den richtigen Stick nach oben oder unten verschieben.
* **Übergeben von Bewegung und die Ausrichtung** (nur HoloLens 2-Emulator) - halten Sie Alt gedrückt und ziehen Sie die Maus sich / nach unten / links / rechts, um das Handsymbol verschieben oder verwenden Sie die Pfeiltasten und Q / E zu drehen und Neigen von der Hand.  Halten Sie für ein Xbox-Controller die linke oder Rechte Stoßstange und linken Ministick um die Seite zu verschieben, nach links / rechts / vorwärts / zurück, die Ministick rechts drehen, und oben und unten auf das Steuerkreuz erhöhen oder verringern die Seite.

## <a name="anatomy-of-the-hololens-2-emulator"></a>Aufbau des Emulators HoloLens 2 

### <a name="main-window"></a>Klicken Sie im Hauptfenster

![2-Emulator für HoloLens-Hauptfenster](images/emulator2-900px.png)

### <a name="toolbar"></a>Symbolleiste

Klicken Sie auf der rechten Seite des Hauptfensters finden Sie die Symbolleiste des Emulators. Die Symbolleiste enthält die folgenden Schaltflächen:
* ![Symbol "Schließen"](images/emulator-close.png) **schließen**: Schließt den Emulator.
* ![Symbol "Minimieren"](images/emulator-minimize.png) **Minimieren**: Minimiert das Emulatorfenster.
* ![Simulation_icon](images/emulator-simulation-panel.png) **Simulation Systemsteuerung**: Anzeigen oder Ausblenden der [Simulation Systemsteuerung](#simulation-control-panel) zum Konfigurieren und Steuern von [Eingabe für den Emulator](#basic-emulator-input).
* ![Passen auf das Symbol für bildschirmaufzeichnung](images/emulator-fit.png) **an Bildschirmgröße anpassen**: Passen den Emulator zum Bildschirm.
* ![Zoom icon](images/emulator-zoom.png) **Zoom**: Stellen Sie den Emulator, größere und kleinere.
* ![Symbol "Hilfe"](images/emulator-help.png) **Hilfe**: Öffnet die Emulator-Hilfe.
* ![Symbol für Portals offenes Gerät](images/emulator-deviceportal.png) **öffnen Device Portal**: Öffnen Sie die Windows Device Portal für das Betriebssystem HoloLens im Emulator.
* ![Tool-Symbol](images/emulator-tools.png) **Tools**: Öffnen der **zusätzliche Tools** Bereich.

### <a name="simulation-control-panel"></a>Systemsteuerung für die Simulation

Die Simulation-Systemsteuerung können Sie die aktuelle Position und Ausrichtung der simulierten menschliche und simulierte Eingabegeräte anzuzeigen.  Sie können auch so konfigurieren Sie die beiden simulierten Eingabe, wie das ein- und Ausblenden von einer oder beide praktische und Geräte, die zum Steuern des simulierten Eingaben wie z. B. Tastatur, Maus und Gamepad Ihres Computers verwendet werden.

![Systemsteuerung für die Simulation](images/emulator-simulation-control-panel.png)

* Um den Bereich der Simulation anzuzeigen oder auszublenden, klicken Sie auf die Symbolleisten-Schaltfläche, oder drücken Sie F7, auf der Tastatur.
* Zeigen Sie auf den ein Steuerelement oder ein Feld, um eine QuickInfo anzuzeigen, die Tastatur, Maus und Gamepad-Steuerelemente für die es enthält.
* Wechseln Sie zum Anzeigen oder Ausblenden einer Hand, unter der linken oder rechten Seite des jeweiligen Schalters.
* Verwenden Sie entweder die linken oder Rechte Alt-Tasten auf der Tastatur, oder auf den Gamepad Stoßstange nach links oder rechts, um das Handsymbol zu steuern.
* Damit alle Eingaben für einen oder beide Hände durchführt, klicken Sie auf die Schaltfläche "Pushpin" unter der ein/aus-Schalter.  Dies ist die Entsprechung der gedrückter Alt-Taste für die Hand.
* Um die Augen Blicke Richtung steuern möchten, klicken Sie auf das Pinsymbol im Abschnitt "Augen".  Dies ist die Entsprechung des Sie "Y" auf der Tastatur gedrückt halten.
* Klicken Sie auf die Schaltfläche "Laden" im Abschnitt "Aufzeichnen", um eine Aufzeichnung Raum zu laden.  Finden Sie unter [simulierte Räume](#simulated-rooms) für Weitere Informationen.
* Um die Geschwindigkeit anpassen, die das simulierte menschlicher oder ein simuliertes Eingabegeräte verschieben oder drehen als Reaktion auf der Tastatur, Maus oder Gamepad Eingabe, klicken Sie auf das Zahnradsymbol neben "Einstellungen für Eingabe" und passen Sie die Schieberegler.
* Standardmäßig steuert Tastatureingaben simulierte menschliche und simulierte Eingabe.  Um die Ihres Computers Tastatureingaben über an die HoloLens gesendet haben, deaktivieren Sie auf "Verwendung von Tastatur für die Simulation".  F4 ist die Tastenkombination für diese Einstellung.
* Wenn der Bereich für die Simulation bereits angezeigt wird, wechselt drücken Sie F8 über den Tastaturfokus.
* Klicken Sie zum Bereich "Simulation" aus dem Emulatorfenster zu lösen, klicken Sie auf die Schaltfläche am unteren Rand der Bereich, oder drücken Sie F9 auf der Tastatur.  Schließen des Fensters, oder drücken F9 erneut wird das Fenster für den Emulator zurück.
* Die Simulation-Systemsteuerung gestartet werden kann, als separate Anwendung, sodass Sie zum Verbinden mit und zum Steuern der 2-Emulator für HoloLens, HoloLens-2-Gerät oder Windows Mixed Reality-Simulation mit PerceptionSimulationInput.exe aus % ProgramFiles(x86) \ Windows-Kits\10\Microsoft XDE\10.0.18362.0\.

### <a name="account-tab"></a>Die Registerkarte „Konto“

Die Registerkarte "Konto" können Sie den Emulator mit einem Microsoft Account anmelden zu konfigurieren. Dies ist hilfreich beim Testen der APIs, die der Benutzer mit einem Konto angemeldet sein muss.  Wechseln diese Option ist erforderlich, Sie vollständig schließen und neu starten den Emulator für HoloLens für die Einstellung wirksam wird.  Wenn diese Option aktiviert ist, fordert nachfolgenden Starts des Emulators Sie auf, dass die Anmeldung, genau wie ein Benutzer beim ersten verwenden würden die HoloLens gestartet wird.  Um schnell mit Ihrem PC Tastatur Ihre Anmeldeinformationen einzugeben, zuerst "Verwenden der Tastatur für die Simulation" in der Systemsteuerung für die Simulation deaktivieren Sie, oder drücken Sie F4, auf der Tastatur, um die Einstellung für die Tastatur aktivieren oder deaktivieren ein-/ausschalten.

### <a name="optional-settings-tab"></a>Registerkarte "optionale Einstellungen"

Die optionalen Einstellungen Registerkarte zeigt ein Steuerelement zum Aktivieren oder deaktivieren die Hardware beschleunigter Grafikfunktionen.  Hardware beschleunigte Grafikfunktionen werden standardmäßig unterstützt der Treiber für die Grafikkarte Ihres Computers verwendet werden.  Wenn Ihre Grafikkarte Treiber GPU-PV nicht unterstützt, wird diese Option nicht angezeigt.

### <a name="diagnostics-tab"></a>Registerkarte "Diagnose"

Die Registerkarte "Diagnose" zeigt die IP-Adresse des Emulators in Form eines Links zum Windows Device Portal zusammen mit dem Status der virtuellen GPU.


## <a name="anatomy-of-the-hololens-1st-gen-emulator"></a>Aufbau der HoloLens (1. Generation) Emulator

### <a name="main-window"></a>Klicken Sie im Hauptfenster

Wenn der Emulator gestartet wird, sehen Sie ein Fenster der HoloLens Betriebssystem angezeigt.

![Emulator für HoloLens-Hauptfenster](images/emulator-890px.png)

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

![Im Bereich "Zusätzliche Tools" der Emulator für HoloLens](images/emulator-simulation-500px.png)

Die Registerkarte "Simulation" zeigt den aktuellen Status der simulierten Sensoren verwendet, um die HoloLens-Betriebssystemlaufwerk innerhalb des Emulators. Mit dem Mauszeiger auf einen beliebigen Wert in der Registerkarte "Simulation" bietet eine QuickInfo, die beschreibt, wie dieses Werts zu steuern.

### <a name="room-tab"></a>Registerkarte "Raum"

Der Serveremulator simuliert die Eingabe der Welt in Form des Netzes räumliche Zuordnung von simulierten "Räume". Auf dieser Registerkarte können Sie auswählen, welche Platz um statt der standardraum zu laden.

![HoloLens-Emulator "Räume"-Registerkarte](images/emulator-room-500px.png)

Finden Sie unter [simulierte Räume](#simulated-rooms) für Weitere Informationen.

### <a name="account-tab"></a>Die Registerkarte „Konto“

Die Registerkarte "Konto" können Sie den Emulator mit einem Microsoft Account anmelden zu konfigurieren. Dies ist hilfreich beim Testen der API, die der Benutzer mit einem Konto angemeldet sein muss. Nachdem Sie das Kontrollkästchen auf dieser Seite, nachfolgenden Starts des Emulators fordert Sie zur Anmeldung aus, wie ein Benutzer erstmals die HoloLens gestartet wird.

## <a name="simulated-rooms"></a>Simulierte Räume

Simulierte Räume sind hilfreich beim Testen Ihrer app in mehreren Umgebungen. Mehrere Räume werden geliefert, mit dem Emulator und nach der Installation der Emulations finden sie in % ProgramFiles% (x86) %\Windows Kits\10\Microsoft XDE\\(Version) \Plugins\Rooms. Alle diese Räume wurden in realen Umgebungen, die mithilfe einer HoloLens erfasst:
* **DefaultRoom.xef** – eine kleine Wohnzimmer mit einem Fernsehgerät Kaffee-Tabelle und zwei Sofas. Standardmäßig geladen, wenn Sie den Emulator zu starten.
* **Bedroom1.xef** – eine kleine Schlafzimmer mit einem Schreibtisch.
* **Bedroom2.xef** -Schlafzimmer mit einer Dame Größe konzentrieren, Kommode, Nightstands und walk-in Wandschrank.
* **GreatRoom.xef** – eine hervorragende großen leeren Bereich-Raum mit Wohnzimmer, Trinken Tabellen- und Küche.
* **LivingRoom.xef** – ein Wohnzimmer mit einer Kamin, Sofa, Armchairs und einen Kaffee-Tabelle mit einer Vase.

Sie können auch eigene Räume für die Verwendung im Serveremulator mithilfe der Simulation Seite Aufzeichnen der [Windows Device Portal](using-the-windows-device-portal.md) auf Ihre HoloLens (1. Generation).

Im Emulator sehen Sie nur Hologramme, dass Sie rendern und simulierten Raum hinter der Hologramme wird nicht angezeigt. Dies ist im Gegensatz zu den tatsächlichen HoloLens, in denen Sie sowohl finden Sie unter, gemischt. Sie können die simulierten Platz im HoloLens Emulator finden Sie unter müssen Sie Ihre app zum Rendern der Gitter räumliche Zuordnung, in der Szene aktualisiert werden.

## <a name="troubleshooting"></a>Problembehandlung

Bei der Installation des Emulators aus, die Sie benötigen möglicherweise einen Fehler angezeigt *"Visual Studio 2015 Update 1 und UWP-Tools Version 1.2"*. Es gibt drei mögliche Ursachen dieses Fehlers:
* Sie haben nicht die letzte Version von Visual Studio (Visual Studio-2019, Visual Studio 2017 oder Visual Studio 2015 Update 1 oder höher). Dieses Problem beheben, installieren Sie die neueste Version von Visual Studio.
* Sie haben die letzte Version von Visual Studio, aber Sie verfügen nicht über die universelle Windows-Plattform (UWP)-Tools installiert. Dies ist ein optionales Feature für Visual Studio.

Auch ein Fehler, die Installation des Emulators auf eine nicht-Pro/Enterprise/Education-SKU von Windows angezeigt werden kann oder wenn Hyper-V-Funktion möglicherweise nicht aktiviert.
* Lesen Sie die [Systemanforderungen](#hololens-emulator-system-requirements) Abschnitt einen vollständigen Satz von Anforderungen.
* Außerdem stellen Sie sicher, dass die Hyper-V-Feature auf Ihrem System aktiviert wurde.

Wenn die Installation erfolgreich abgeschlossen, aber der Emulator für HoloLens nicht als Option für das Bereitstellen und Debuggen angezeigt, überprüfen Sie bitte Folgendes:
* Die Visual Studio-Projektkonfiguration ist auf X86 (HoloLens 1. Generation) oder X86 oder X64 (2-Emulator für HoloLens) festgelegt.
* Wenn Sie Visual Studio-2019 verwenden zu können, ist das Plattformtoolset in der Projektkonfiguration auf v142 festgelegt.

Wenn die Installation erfolgreich abgeschlossen, aber Visual Studio zeigt Fehler beim Starten des Emulators HoloLens, versuchen Sie Folgendes:
* Visual Studio als Administrator ausführen.
* Wenn Sie nur Visual Studio-2019 installiert hatten, stellen Sie sicher, dass der Registrierungswert "KitsRoot10" unter HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Kits\Installed Stämme auf 32-Bit-Ordner "Programme" verweist (z. B. "C:\Program Files (x86) \Windows Kits \10 ").  Wenn dies nicht der Fall ist, deinstallieren Sie den Emulator für HoloLens, ändern Sie den Registrierungswert in 32-Bit-Ordner "Programme" und installieren Sie den Emulator für HoloLens.  Dieses Problem wird in Visual Studio 2019 16.0.3 behoben.

Wenn ein Fehlerdialogfeld "Ungültiger Byte-Codierung" beim Start des Emulators angezeigt werden:
* Löschen Sie alle Dateien im %localappdata%\Microsoft\XDE\HCS, und versuchen Sie es noch mal.

Wenn die Debug-Zielliste in Visual Studio leer ist (z. B. "Start" ist die einzige Option), und Sie alle oben aufgeführten Problembehandlungsschritten befolgt haben:
* Löschen Sie den Ordner "ConfigurationCache" in %localappdata%\Microsoft\VisualStudio\\<*Installations-Id*> \CoreCon und versuchen Sie es noch mal.

Wenn Ihr System stürzt ab, wenn der Emulator gestartet wird, deaktivieren Sie die Hardwarebeschleunigung für Emulator-Grafiken.
* Erstellen Sie einen Registrierungs-DWORD-Wert, der mit dem Namen "DisableGPU" am HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\XDE\10.0, und legen Sie dessen Wert auf 1.

## <a name="see-also"></a>Siehe auch
* [Erweiterte Eingabe für HoloLens-Emulator und Mixed Reality-Simulator](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Emulator für HoloLens-Software-Verlauf](hololens-emulator-archive.md)
* [Räumliche Abbildung in Unity](spatial-mapping-in-unity.md)
* [Räumliche Abbildung in DirectX](spatial-mapping-in-directx.md)
