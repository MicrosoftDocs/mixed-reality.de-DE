---
title: Verwenden die Windows Device Portal
description: Die Windows Device Portal für HoloLens können Sie konfigurieren und verwalten Ihr Gerät remote über WLAN oder ein USB. Das Geräteportal ist ein Webserver auf der HoloLens, mit dem Sie über einen Webbrowser auf dem PC eine Verbindung herstellen können. Das Device Portal enthält viele Tools, die Ihnen das Verwalten Ihrer HoloLens und Debuggen und Optimieren von apps helfen.
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Windows Device Portal, HoloLens
ms.openlocfilehash: 79a4a1f99125028fcaf71e185eb00093aa8c742f
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694582"
---
# <a name="using-the-windows-device-portal"></a>Verwenden die Windows Device Portal

<table>
<tr>
<th>Feature</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1. Generation)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> Windows Device Portal</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

Die Windows Device Portal für HoloLens können Sie konfigurieren und verwalten Ihr Gerät remote über WLAN oder ein USB. Das Geräteportal ist ein Webserver auf der HoloLens, mit dem Sie über einen Webbrowser auf dem PC eine Verbindung herstellen können. Das Device Portal enthält viele Tools, die Ihnen das Verwalten Ihrer HoloLens und Debuggen und Optimieren von apps helfen.

Diese Dokumentation bezieht sich insbesondere über die Windows Device Portal für HoloLens. Um das Windows Device Portal für Desktop (einschließlich für Windows Mixed Reality) verwenden zu können, finden Sie unter [Windows Device Portal-Übersicht](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>Einrichten von HoloLens Windows Device Portal verwenden.

1. Schalten Sie die HoloLens ein, und setzen Sie sie auf.
2. Führen Sie die [Blütengeste](gestures.md#bloom) aus, um das Hauptmenü zu starten.
3. Bestaunen an die **Einstellungen** Kachel, und führen Sie die [tippbewegung](gestures.md#air-tap) Bewegung. Führen Sie eine zweite tippbewegung um die app in Ihrer Umgebung zu platzieren. Die Einstellungs-App wird gestartet, nachdem Sie sie platziert haben.
4. Wählen Sie das Menüelement **Aktualisieren** aus.
5. Wählen Sie das Menüelement **Für Entwickler** aus.
6. Aktivieren Sie den **Entwicklermodus**.
7. [Scrollen Sie nach unten](gestures.md#composite-gestures) , und aktivieren Sie **Device Portal**.
8. Wenn Sie Windows Device Portal einrichten, damit Sie für diese HoloLens über USB oder WLAN-apps bereitstellen können, klicken Sie auf **Paar** zu [ereignispaarbildung PIN generieren](using-visual-studio.md). Lassen Sie die Einstellungs-app das PIN-Popup, bis Sie die PIN in Visual Studio bei der ersten Bereitstellung eingeben.

   ![Aktivieren den Entwicklermodus im Einstellungen-app für Windows Holographic](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a>Herstellen einer Verbindung über WLAN

1. [Wi-Fi-Verbindung mit Ihrem HoloLens](connecting-to-wi-fi-on-hololens.md).
2. Suchen Sie die IP-Adresse Ihres Geräts.
   * Suchen Sie die IP-Adresse auf dem Gerät unter **Einstellungen > Netzwerk und Internet > Wi-Fi-> Erweiterte Optionen**.
3. Über einen Webbrowser auf Ihrem PC wechseln Sie zu https://<YOUR_HOLOLENS_IP_ADDRESS>
   * Die folgende Meldung wird im Browser angezeigt werden: "Es ist ein Problem mit dem Sicherheitszertifikat der Website". Der Grund dafür ist, dass das für das Geräteportal ausgestellte Zertifikat ein Testzertifikat ist. Sie können diesen Zertifikatfehler vorerst ignorieren und fortfahren.

## <a name="connecting-over-usb"></a>Herstellen einer Verbindung per USB

1. [Installieren der Tools](install-the-tools.md) um sicherzustellen, dass Sie Visual Studio Update 1 mit den Windows 10-Entwicklertools auf Ihrem PC installiert haben. Hierdurch wird USB-Konnektivität aktiviert.
2. Schließen Sie die HoloLens mit einem Micro-USB-Kabel am PC an.
3. Rufen Sie in einem Webbrowser auf dem PC „http://127.0.0.1:10080“ auf.

## <a name="connecting-to-an-emulator"></a>Herstellen einer Verbindung mit einem emulator

Sie können das Geräteportal auch mit dem Emulator verwenden. Verwenden Sie zum Verbinden mit dem Device Portal die [Symbolleiste](using-the-hololens-emulator.md). Klicken Sie auf dieses Symbol: ![Symbol "Device Portal öffnen"](images/emulator-deviceportal.png) **öffnen Device Portal**: Öffnen Sie das Windows-Geräteportal für das HoloLens-Betriebssystem im Emulator.

## <a name="creating-a-username-and-password"></a>Erstellen einen Benutzernamen und Kennwort

![Richten Sie den Zugriff auf Windows Device Portal](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*Richten Sie den Zugriff auf Windows Device Portal*

Wenn Sie das erste Mal eine Verbindung der HoloLens mit dem Geräteportal herstellen, müssen Sie einen Benutzernamen und ein Kennwort erstellen.
1. Geben Sie in einem Webbrowser auf dem PC die IP-Adresse der HoloLens ein. Die Seite „Set up access“ wird geöffnet.
2. Klicken oder tippen Sie auf **Anforderung Pin** und sehen Sie sich die HoloLens-Anzeige, um die generierte PIN zu erhalten.
3. Geben Sie die PIN in der **PIN auf Ihrem Gerät angezeigten** Textfeld.
4. Geben Sie den Benutzernamen ein, den Sie zum Herstellen der Verbindung mit dem Geräteportal verwenden. Dabei muss es sich nicht um den Namen eines Microsoft-Kontos (MSA) oder einen Domänennamen handeln.
5. Geben Sie ein Kennwort ein, und bestätigen Sie es. Das Kennwort muss mindestens sieben Zeichen lang sein. Es muss kein MSA- oder Domänenkennwort sein.
6. Klicken Sie auf **Paar** zur Verbindung mit Windows Device Portal auf die HoloLens.

Wenn Sie diese Benutzernamen oder das Kennwort zu einem beliebigen Zeitpunkt ändern möchten, können Sie diesen Prozess wiederholen, indem Sie Zugriff auf der Sicherheitsseite des Geräts empfängerrollenbildschirm des: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm.

## <a name="security-certificate"></a>Sicherheitszertifikat

Wenn im Browser eine Meldung zu einem Zertifikatfehler angezeigt wird, können Sie diesen beheben, indem Sie eine Vertrauensstellung mit dem Gerät erstellen.

Jede HoloLens generiert ein eindeutiges selbstsigniertes Zertifikat für die SSL-Verbindung. Standardmäßig wird dieses Zertifikat vom Webbrowser des PC nicht als vertrauenswürdig angesehen, und Sie erhalten möglicherweise eine Meldung zu einem Zertifikatfehler. Sie können dieses Zertifikat von der HoloLens herunterladen (über USB oder ein vertrauenswürdiges WLAN-Netzwerk) und es auf dem PC als vertrauenswürdig einstufen, um eine sichere Verbindung mit dem Gerät herzustellen.
1. **Stellen Sie sicher, dass Sie in einem sicheren Netzwerk (USB- oder einem Wi-Fi-Netzwerk, denen Sie vertrauen) sind.**
2. Laden Sie auf der Seite "Sicherheit" im Device Portal des Geräts-Zertifikat herunter.
   * Navigieren Sie zu: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm
3. Installieren Sie das Zertifikat, das in der "Vertrauenswürdige Stammzertifizierungsstellen" auf Ihrem PC zu speichern.
   * Geben Sie im Windows-Menü: Verwalten von Zertifikaten für Computer, und starten Sie das Applet.
   * Erweitern Sie die **vertrauenswürdigen Stammzertifizierungsstelle** Ordner.
   * Klicken Sie auf die **Zertifikate** Ordner.
   * Wählen Sie im Menü Aktion: Alle Aufgaben > Import...
   * Führen Sie den Zertifikatimport-Assistenten mit der Zertifikatdatei aus, die Sie vom Geräteportal heruntergeladen haben.
4. Starten Sie den Browser neu.

## <a name="device-portal-pages"></a>Seiten des Geräteportals

### <a name="home"></a>Startseite

![Windows Device Portal-Startseite für Microsoft HoloLens](images/windows-device-portal-home-page-1000px.png)<br>
*Windows Device Portal-Startseite für Microsoft HoloLens*

Die Geräteportalsitzung beginnt auf der Startseite. Der Zugriff auf andere Seiten erfolgt über die Navigationsleiste links von der Startseite.

Die Symbolleiste am oberen Rand der Seite ermöglicht den Zugriff auf häufig verwendete Status und Features.
* **Online**: Gibt an, ob das Gerät auf-WLAN verbunden ist.
* **Herunterfahren**: Das Gerät wird deaktiviert.
* **Starten Sie neu**: Zyklen Einschalten des Geräts.
* **Sicherheit**: Öffnet die Seite Sicherheit für Geräte.
* **Cool**: Gibt die Temperatur des Geräts an.
* **A/C**: Gibt an, ob das Gerät im Netzbetrieb befindet, und geladen.
* **Hilfe**: Öffnet die Dokumentationsseite für REST-Schnittstelle.

Auf der Startseite werden die folgenden Informationen angezeigt:
* **Gerätestatus:** überwacht die Integrität des Geräts und kritische Fehler gemeldet.
* **Windows-Informationen:** zeigt den Namen der HoloLens und die derzeit installierte Version von Windows.
* **Einstellungen**: Dieser Abschnitt enthält die folgenden Einstellungen:
   * **IPD**: Abstand der interpupillary (IPD), d. h. die Entfernung, in Millimeter zwischen den Mittelpunkt der Schüler des Benutzers, bei der Suche direkt fort. Die Einstellung wird sofort wirksam. Der Standardwert wurde beim Einrichten des Geräts automatisch berechnet.
   * **Name des Geräts**: Weisen Sie einen Namen, um die HoloLens. Nach dem Ändern dieses Werts müssen Sie das Gerät neu starten, damit er wirksam wird. Nach dem Klicken auf **speichern**, ein Dialogfeld fragt, ob Sie den Neustart des Geräts entweder sofort oder später neu starten möchten.
   * **Energiesparmoduseinstellungen**: Legt fest, wie lange gewartet, bevor das Gerät wird in den Standbymodus, wenn es im Netzbetrieb befindet und wenn es im Akkubetrieb befindet.

### <a name="3d-view"></a>3D View

![In Windows Device Portal für Microsoft HoloLens-3D-Ansichtsseite](images/3dview-1000px.png)<br>
*In Windows Device Portal für Microsoft HoloLens-3D-Ansichtsseite*

Auf der Seite „3D View“ können Sie erkennen, wie die HoloLens Ihre Umgebung interpretiert. Navigieren Sie mit der Maus in der Ansicht:
* Drehen: Linksklick + mit der Maus.
* Schwenken: rechts klicken Sie auf + Mausrad;
* Zoom: Maus scrollen.
* **Überwachungsoptionen**
   * Aktivieren Sie fortlaufende visuelle Verfolgung durch Überprüfen **Force visuelle Verfolgung**. 
   * **Anhalten** visuelle Verfolgung beendet.
* **Ansichtsoptionen**: Festlegen von Optionen auf der-3D-Sicht:
  * **Nachverfolgen von**: Gibt an, ob visuelle Verfolgung aktiv ist.
  * **Anzeigen von Floor**: Zeigt eine kariertes Floor-Ebene.
  * **Anzeigen von Frustums**: Zeigt die Ansicht Frustums an.
  * **Anzeigen der Stabilisierung Ebene**: Zeigt die Ebene, die HoloLens zur Stabilisierung während der Übertragung verwendet.
  * **Anzeigen von Mesh**: Zeigt das Netz räumliche Zuordnung, das Ihrer Umgebung darstellt.
  * **Anzeigen räumlicher Anker**: Zeigt die räumliche Anker für die app aktiv. Sie müssen zum Abrufen und aktualisieren die Anker der Schaltfläche "Aktualisieren" klicken.
  * **Anzeigen von Details**: Zeigt übergeben Positionen, Head Drehung Quaternionen und der Gerät-Ursprung-Vektor, wie sie in Echtzeit zu ändern.
  * **Schaltfläche "Vollbild"** : Zeigt die 3D-Ansicht im Vollbildmodus an. Drücken Sie die ESC-Taste, um die Vollbildansicht zu beenden.
* **Entwurfsoberfläche Rekonstruktion**: Klicken oder tippen Sie auf **Update** Mesh neueste räumliche Zuordnung vom Gerät angezeigt. Ein vollständiger Durchlauf kann bis zu einige Sekunden lang dauern. Mesh wird nicht automatisch aktualisiert, in der-3D-Sicht aus, und Sie müssen manuell auf **aktualisieren** zum neuesten Mesh vom Gerät abrufen. Klicken Sie auf **speichern** um das aktuelle räumliche Zuordnung Netz als eine Obj-Datei auf Ihrem PC zu speichern.
* **Räumliche Anker**: Klicken Sie auf "Aktualisieren", um anzuzeigen, oder aktualisieren die räumliche Anker für die app aktiv.

### <a name="mixed-reality-capture"></a>Mixed Reality Capture

![Gemischte Realität erfassen Seite in Windows Device Portal für Microsoft HoloLens](images/windows-device-portal-mixed-reality-capture-page-1000px.png)<br>
*Gemischte Realität erfassen Seite in Windows Device Portal für Microsoft HoloLens*

Auf der Seite „Mixed Reality Capture“ können Sie Mediendatenströme von der HoloLens speichern.
* **Einstellungen**: Steuern Sie die Media-Datenströme, die erfasst werden, indem Sie die folgenden Einstellungen zu überprüfen:
  * **Hologramme**: Erfasst den holographic Inhalt in den video Stream an. Hologramme werden in Mono und nicht in Stereo gerendert.
  * **PV Kamera**: Erfasst den Videostream zwischen der Kamera und Fotos/Video.
  * **Mic Audio**: Erfasst die Audiodaten aus dem Mikrofon-Array.
  * **App Audio**: Erfasst die Audiodaten aus dem die derzeit ausgeführte app.
  * **Rendern von Kamera**: Richtet die Erfassung aus der Perspektive der Fotogalerie/Video-Kamera, werden Wenn [von der ausgeführten app unterstützten](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (gilt nur für HoloLens-2).
  * **Live-Vorschau-Qualität**: Wählen Sie die Bildschirmauflösung, Framerate und streaming-Rate für die Livevorschau an.
* Klicken oder tippen Sie auf die **Livevorschau** Schaltfläche, um den Stream Capture anzeigen. **Beendet die Livevorschau** hält den Capture-Stream.
* Klicken oder tippen Sie auf **Datensatz** um den Stream mixed Reality-Aufzeichnung von Aktivitäten, mithilfe der angegebenen Einstellungen zu starten. **Beenden Sie die Aufzeichnung** beendet die Aufzeichnung und speichert es.
* Klicken oder tippen Sie auf **Take Foto** auszuführende ein Standbild aus dem Stream erfassen.
* **Videos und Fotos**: Zeigt eine Liste von Videos und Fotos Erfassungen, die auf dem Gerät ausgeführt.

> [!NOTE]
> Es gibt [Einschränkungen bei der gleichzeitigen MRC](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):
> * Wenn eine app versucht, die die Foto/Video-Kamera zugreifen, während Windows Device Portal ein Video aufzeichnet, wird die Videoaufnahme beendet.
>   * HoloLens-2 wird die Aufnahme von Videos nicht beendet, wenn die app-Acesses das Foto/Videokamera SharedReadOnly-Modus.
> * Wenn die Kamera Foto/Video mit eine app aktiv verwendet wird, ist Windows Device Portal ein Foto oder einen Datensatz eines Videos nutzen.
> * Live-streaming:
>   * HoloLens (1. Generation) verhindert, dass eine app den Zugriff auf die Kamera Foto/Video-und Livestreaming von Windows Device Portal.
>   * HoloLens (1. Generation) kann nicht live-Streaming, wenn eine app die Foto/Videokamera aktiv verwendet wird.
>   * HoloLens-2 wird automatisch beendet, live-streaming, wenn eine app versucht, Zugriff auf die Kamera Foto/Video im ExclusiveControl-Modus.
>   * HoloLens 2 kann einen Livestream zu starten, während eine app die Kamera PV aktiv verwendet wird.

### <a name="performance-tracing"></a>Die Ablaufverfolgung der Leistung

![Leistung, die Ablaufverfolgung in Windows Device Portal für Microsoft HoloLens-Seite](images/windows-device-portal-performance-tracing-page-1000px.png)<br>
*Leistung, die Ablaufverfolgung in Windows Device Portal für Microsoft HoloLens-Seite*

Erfassen [Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (WPR)-ablaufverfolgungen von Ihrem HoloLens.
* **Verfügbare Profile**: Wählen Sie aus der Dropdown-Liste und klicken oder tippen Sie auf die WPR Profil **starten** zu Ablaufverfolgung starten.
* **Benutzerdefinierte Profile**: Klicken oder tippen Sie auf **Durchsuchen** auswählen ein Profils WPR von Ihrem PC. Klicken oder tippen Sie auf **Hochladen und starten**, um die Ablaufverfolgung zu starten.

Zum Beenden der Überwachung klicken Sie auf den Link „Beenden“. Bleiben Sie auf dieser Seite, bis die Datei herunterladen abgeschlossen ist.

Aufgezeichnete ETL-Dateien können in [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx) für die Analyse geöffnet werden.

### <a name="processes"></a>Prozesse

![Seite "Prozesse" in Windows Device Portal für Microsoft HoloLens](images/windows-device-portal-running-processes-page-1000px.png)<br>
*Seite "Prozesse" in Windows Device Portal für Microsoft HoloLens*

Zeigt Details zu derzeit ausgeführten Prozessen an. Diese umfassen Apps und Systemprozesse.

### <a name="system-performance"></a>Systemleistung

![System-Seite "Leistung" in Windows Device Portal für Microsoft HoloLens](images/windows-device-portal-system-performance-page-1000px.png)<br>
*System-Seite "Leistung" in Windows Device Portal für Microsoft HoloLens*

Zeigt Echtzeitgraphen mit Informationen zur Systemdiagnose an, z. B. Stromverbrauch, Bildfrequenz und CPU-Last.

Die folgenden Metriken sind verfügbar:
* **SoC Power**: Sofortige energienutzung System on a Chip, gemittelt über eine minute
* **Stromnetz**: Sofortige System energienutzung, gemittelt über eine minute
* **Framerate**: Frames pro Sekunde verpasst VBlanks pro Sekunde und aufeinander folgende verpasst VBlanks
* **GPU**: GPU-Engine-Auslastung, Prozent des Gesamtwerts verfügbar
* **CPU**: Verfügbarkeit in Prozent
* **I/O**: Lese- und Schreibvorgänge
* **Netzwerk**: Empfangen und gesendet
* **Arbeitsspeicher**: Insgesamt verwendet wird, ein Commit ausgeführt, per Pager benachrichtigt, und nicht ausgelagerten

### <a name="apps"></a>Apps

![Seite "Apps" in Windows Device Portal für Microsoft HoloLens](images/windows-device-portal-apps-page-1000px.png)<br>
*Seite "Apps" in Windows Device Portal für Microsoft HoloLens*

Verwaltet die apps, die auf die HoloLens installiert sind.
* **Installierte apps**: Entfernen Sie aus, und Starten von apps.
* **Ausführen von apps**: Listet die apps, die derzeit ausgeführt werden.
* **Installieren Sie die app**: Wählen Sie die app-Pakete für die Installation aus einem Ordner in Ihrem Computernetzwerk.
* **Abhängigkeit**: Fügen Sie Abhängigkeiten für die app, die Sie installieren möchten.
* **Bereitstellen von**: Stellen Sie die ausgewählte app und die Abhängigkeiten für die HoloLens bereit.

### <a name="app-crash-dumps"></a>App-Absturzabbilder

![Absturzabbildern Anwendungsseite in Windows Device Portal für Microsoft HoloLens](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)<br>
*Absturzabbildern Anwendungsseite in Windows Device Portal für Microsoft HoloLens*

Auf dieser Seite können Sie Absturzabbilder für die quergeladenen Apps erfassen. Überprüfen Sie die **Crash Dumps aktiviert** Kontrollkästchen für jede app, die für die Absturzabbilder erfasst werden sollen. Kehren Sie zum Erfassen von Absturzabbildern zu dieser Seite zurück. Dumpdateien können sein [für das Debuggen in Visual Studio geöffnet](https://msdn.microsoft.com/library/d5zhxt22.aspx).

### <a name="file-explorer"></a>Datei-Explorer

![Datei-Explorer-Seite in Windows Device Portal für Microsoft HoloLens](images/fileexplorer-1000px.png)<br>
*Datei-Explorer-Seite in Windows Device Portal für Microsoft HoloLens*

Verwenden Sie den Datei-Explorer zum Durchsuchen, hochladen und Herunterladen von Dateien. Sie können mit Dateien im Ordner "Dokumente", Ordner "Bilder", und in den lokalen Speicher für apps arbeiten, die Sie in Visual Studio oder im Device Portal bereitgestellt.

### <a name="kiosk-mode"></a>Kioskmodus

>[!NOTE]
>Kiosk-Modus ist nur verfügbar, mit der [Microsoft HoloLens Commercial Suite](commercial-features.md).

Überprüfen Sie die [einrichten HoloLens im Kiosk-Modus](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) Artikel in Windows IT Pro-Center für die aktuelle Anweisungen zum Aktivieren der Kiosk-Modus über die Windows Device Portal.

### <a name="logging"></a>Protokollierung

![Seite "Protokollierung" in Windows Device Portal für Microsoft HoloLens](images/windows-device-portal-logging-page-1000px.png)<br>
*Seite "Protokollierung" in Windows Device Portal für Microsoft HoloLens*

Verwaltet die Echtzeit-Ereignisablaufverfolgung für Windows (ETW) für die HoloLens.

Überprüfen Sie **ausblenden Anbieter** angezeigt der **Ereignisse** softwareversionsnummern handelt.
* **Die registrierten Anbieter**: Wählen Sie die ETW-Anbieter und der Ablaufverfolgungsebene. Für die Ablaufverfolgungsebene wird einer der folgenden Werte festgelegt:
   1. Abnormal exit or termination
   2. Severe errors
   3. Warnungen
   4. Non-error warnings

Klicken oder tippen Sie auf **Aktivieren**, um die Ablaufverfolgung zu starten. Der Anbieter wird der Liste **Aktivierte Anbieter** hinzugefügt.
* **Benutzerdefinierte Anbieter**: Wählen Sie eine benutzerdefinierte ETW-Anbieter und der Ablaufverfolgungsebene. Identifizieren Sie den Anbieter anhand seiner GUID. Fügen Sie keine Klammern in die GUID ein.
* **Aktivierte Anbieter**: Listet die aktivierten Anbietern an. Wählen Sie einen Anbieter aus der Dropdownliste aus, und klicken oder tippen Sie auf **Deaktivieren**, um die Ablaufverfolgung zu beenden. Klicken oder tippen Sie auf **Beenden**, um sämtliche Ablaufverfolgung anzuhalten.
* **Anbieter-Verlauf**: Zeigt die ETW-Anbieter, die während der aktuellen Sitzung aktiviert wurden. Klicken oder tippen Sie auf **Aktivieren**, um einen Anbieter zu aktivieren, der deaktiviert war. Klicken oder tippen Sie auf **Löschen**, um den Verlauf zu löschen.
* **Ereignisse**: Listet die ETW-Ereignisse von den ausgewählten Anbieter im Tabellenformat. Diese Tabelle wird in Echtzeit aktualisiert. Unterhalb der Tabelle, klicken Sie auf die **löschen** Schaltfläche, um alle ETW-Ereignisse aus der Tabelle zu löschen. Hierdurch werden keine Anbieter deaktiviert. Sie können auf **In Datei speichern** klicken, um die derzeit erfassten ETW-Ereignisse in eine lokale CSV-Datei zu exportieren.
* **Filter**: Können Sie die ETW-Ereignisse, die von ID, Schlüsselwort, Ebene, Name des Anbieters, Taskname oder Text erfasst zu filtern. Sie können mehrere Kriterien kombinieren:
   1. Für die Kriterien, die Anwendung auf dieselbe Eigenschaft - können Ereignisse erfüllen, eine der folgenden Kriterien werden angezeigt.
   2. Für Kriterien anwenden auf andere Eigenschaft - Ereignisse müssen alle Kriterien erfüllen.

Sie können z. B. angeben die Kriterien *(Vorgangsname enthält "Foo" oder "Befehlsleiste") und (Text "Error" oder "Warnung")*

### <a name="simulation"></a>Simulation

![Seite "Simulation" in Windows Device Portal für Microsoft HoloLens](images/windows-device-portal-simulation-page-1000px.png)<br>
*Seite "Simulation" in Windows Device Portal für Microsoft HoloLens*

Ermöglicht Ihnen das Aufzeichnen und Wiedergeben von Eingabedaten für Testzwecke.
* **Erfassen Sie Raum**: Verwendet, um eine simulierte Platz-Datei herunterzuladen, die das Netz räumliche Zuordnung für die benutzerumgebung enthält. Benennen Sie den Raum, und klicken Sie dann auf **erfassen** zum Speichern der Daten als .xef-Datei auf Ihrem PC. Diese Raumdatei kann in den HoloLens-Emulator geladen werden.
* **Aufzeichnung**: Überprüfen Sie die Datenströme aufnehmen, benennen Sie die Aufzeichnung, und klicken oder tippen Sie auf **Datensatz** neuprogrammierung gestartet. Ausführen von Aktionen mit Ihrer HoloLens, und klicken Sie dann auf **beenden** zum Speichern der Daten als .xef-Datei auf Ihrem PC. Diese Datei kann im HoloLens-Emulator oder auf dem Gerät geladen werden.
* **Playback**: Klicken oder tippen Sie auf **Upload Aufzeichnung** wählen Sie eine Xef-Datei von Ihrem PC, und senden die Daten an die HoloLens.
* **Steuerungsmodus**: Wählen Sie **Standard** oder **Simulation** aus der Dropdown-Liste und klicken oder tippen Sie auf die **festgelegt** klicken, um den Modus für die HoloLens auszuwählen. Durch Auswahl von „Simulation“ werden die realen Sensoren auf der HoloLens deaktiviert und stattdessen hochgeladene simulierte Daten verwendet. Wenn Sie zu „Simulation“ wechseln, reagiert die HoloLens nicht auf den realen Benutzer, bis Sie zurück zu „Standard“ wechseln.

### <a name="networking"></a>Netzwerk

![Registerkarte "Netzwerk" in Windows Device Portal für Microsoft HoloLens](images/windows-device-portal-networking-page-1000px.png)<br>
*Registerkarte "Netzwerk" in Windows Device Portal für Microsoft HoloLens*

Verwaltet die Wi-Fi-Verbindungen auf die HoloLens.
* **WiFi-Adapter**: Wählen Sie eine WLAN-Adapter und ein Profil mithilfe der Dropdownsteuerelemente. Klicken oder tippen Sie auf **Connect** mit den ausgewählten Adapter.
* **Verfügbare Netzwerke**: Listet die Wi-Fi-Netzwerke, denen die HoloLens herstellen können. Klicken oder tippen Sie auf **aktualisieren** zum Aktualisieren der Liste.
* **IP-Konfiguration**: Zeigt die IP-Adresse und andere Details der Verbindung.

### <a name="virtual-input"></a>Virtual Input

![Seite "virtuelle Input" in Windows Device Portal für Microsoft HoloLens](images/windows-device-portal-virtual-input-page-1000px.png)<br>
*Seite "virtuelle Input" in Windows Device Portal für Microsoft HoloLens*

Sendet die Tastatureingabe vom Remotecomputer an die HoloLens.

Klicken oder tippen Sie auf die Region **virtuellen Tastatur** zum Senden von Tastatureingaben auf die HoloLens zu aktivieren. Geben Sie in der **Eingabetext** Textfeld, und klicken oder tippen Sie auf **senden** die Tastatureingaben an die aktiven app senden.

## <a name="device-portal-rest-apis"></a>Device Portal REST-APIs

Alles, was im Device Portal basiert auf der Basis von [REST-APIs](device-portal-api-reference.md) , dass Sie optional verwenden können, auf die Daten zugreifen und Ihr Gerät programmgesteuert steuern.
