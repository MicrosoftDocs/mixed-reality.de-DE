---
title: Verwenden des Windows-Geräte Portals
description: Im Windows-Geräte Portal für hololens können Sie Ihr Gerät remote über Wi-Fi oder USB konfigurieren und verwalten. Das Geräteportal ist ein Webserver auf der HoloLens, mit dem Sie über einen Webbrowser auf dem PC eine Verbindung herstellen können. Das Geräte Portal enthält viele Tools, die Ihnen helfen, ihre hololens zu verwalten und ihre apps zu Debuggen und zu optimieren.
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Windows-Geräte Portal, hololens
ms.openlocfilehash: 43ecfead7d2882d3624809bc05184f74131b8594
ms.sourcegitcommit: 1ec628a9107194c0a9d4073b5ca09ee816030e85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/01/2020
ms.locfileid: "78202720"
---
# <a name="using-the-windows-device-portal"></a>Verwenden des Windows-Geräte Portals

<table>
<tr>
<th>Feature</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1. Generation)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> Windows Device Portal</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

Im Windows-Geräte Portal für hololens können Sie Ihr Gerät remote über Wi-Fi oder USB konfigurieren und verwalten. Das Geräteportal ist ein Webserver auf der HoloLens, mit dem Sie über einen Webbrowser auf dem PC eine Verbindung herstellen können. Das Geräte Portal enthält viele Tools, die Ihnen helfen, ihre hololens zu verwalten und ihre apps zu Debuggen und zu optimieren.

Diese Dokumentation dient speziell zum Windows-Geräte Portal für hololens. Informationen zum Verwenden des Windows-Geräte Portals für Desktop (einschließlich für Windows Mixed Reality) finden Sie unter [Übersicht über das Windows-Geräte Portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal) .

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>Einrichten von hololens für die Verwendung des Windows-Geräte Portals

1. Schalten Sie die HoloLens ein, und setzen Sie sie auf.
2. Führen Sie die [Start Geste](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture) für HoloLens2 [oder die](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom) Option auf hololens (1. Gen) aus, um das Hauptmenü zu starten. 
3. Schauen Sie sich die Kachel " **Einstellungen** " an, und führen Sie die [Tasten](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) Kombination auf hololens (1. Gen) aus, oder wählen Sie Sie in hololens 2 aus, indem [Sie sie berühren oder einen Hand Strahl verwenden](https://docs.microsoft.com/hololens/hololens2-basic-usage). 
4. Wählen Sie das Menüelement **Aktualisieren** aus.
5. Wählen Sie das Menüelement **Für Entwickler** aus.
6. Aktivieren Sie den **Entwicklermodus**.
7. [Scrollen Sie nach unten](gaze-and-commit.md#composite-gestures) , und aktivieren Sie das **Geräte Portal**.
8. Wenn Sie das Windows-Geräte Portal einrichten, sodass Sie Apps auf diesen hololens über USB oder WLAN bereitstellen können, klicken Sie auf **paar** , um [eine paarweise PIN zu generieren](using-visual-studio.md). Belassen Sie die Einstellungs-APP im Popup Fenster, bis Sie die PIN während der ersten Bereitstellung in Visual Studio eingeben.

   ![Aktivieren des Entwicklermodus in der App "Einstellungen" für Windows Holographic](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a>Herstellen einer Verbindung über Wi-Fi

1. [Verbinden Sie Ihre hololens mit Wi-Fi](connecting-to-wi-fi-on-hololens.md).
2. Suchen Sie die IP-Adresse Ihres Geräts.
   * Suchen Sie die IP-Adresse auf dem Gerät unter **Einstellungen > Netzwerk & Internet > Wi-Fi-> Erweiterte Optionen**.
3. Wechseln Sie in einem Webbrowser auf Ihrem PC zu https://< YOUR_HOLOLENS_IP_ADDRESS >
   * Im Browser wird die folgende Meldung angezeigt: "Es besteht ein Problem mit dem Sicherheitszertifikat dieser Website". Der Grund dafür ist, dass das für das Geräteportal ausgestellte Zertifikat ein Testzertifikat ist. Sie können diesen Zertifikatfehler vorerst ignorieren und fortfahren.

## <a name="connecting-over-usb"></a>Herstellen einer Verbindung über USB

1. [Installieren Sie die Tools](install-the-tools.md) , um sicherzustellen, dass Visual Studio Update 1 mit den Windows 10-Entwicklertools auf Ihrem PC installiert ist. Hierdurch wird USB-Konnektivität aktiviert.
2. Verbinden Sie Ihre hololens mit dem PC mit einem Micro-USB-Kabel für hololens (1. Gen) oder USB-C für hololens 2.
3. Wechseln Sie in einem Webbrowser auf Ihrem PC zu [https://127.0.0.1:10080](https://127.0.0.1:10080).

## <a name="connecting-to-an-emulator"></a>Herstellen einer Verbindung mit einem Emulator

Sie können das Geräteportal auch mit dem Emulator verwenden. Verwenden Sie die [Symbolleiste](using-the-hololens-emulator.md), um eine Verbindung mit dem Geräte Portal herzustellen. Klicken Sie auf dieses Symbol: ![Symbol zum Öffnen des Geräte Portals](images/emulator-deviceportal.png) öffnen Sie das Geräte **Portal**: Öffnen Sie das Windows-Geräte Portal für das hololens-Betriebssystem im Emulator.

## <a name="creating-a-username-and-password"></a>Erstellen eines Benutzernamens und Kennworts

![Einrichten des Zugriffs auf das Windows-Geräte Portal](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*Einrichten des Zugriffs auf das Windows-Geräte Portal*

Wenn Sie das erste Mal eine Verbindung der HoloLens mit dem Geräteportal herstellen, müssen Sie einen Benutzernamen und ein Kennwort erstellen.
1. Geben Sie in einem Webbrowser auf dem PC die IP-Adresse der HoloLens ein. Die Seite „Set up access“ wird geöffnet.
2. Klicken oder tippen Sie auf **Anforderungs-Pin** , und überprüfen Sie die hololens-Anzeige, um die generierte PIN zu erhalten.
3. Geben Sie die PIN in der PIN ein, die im Textfeld **Ihres Geräts angezeigt wird** .
4. Geben Sie den Benutzernamen ein, den Sie zum Herstellen der Verbindung mit dem Geräteportal verwenden. Dabei muss es sich nicht um den Namen eines Microsoft-Kontos (MSA) oder einen Domänennamen handeln.
5. Geben Sie ein Kennwort ein, und bestätigen Sie es. Das Kennwort muss mindestens sieben Zeichen lang sein. Es muss kein MSA- oder Domänenkennwort sein.
6. Klicken Sie auf **paar** , um eine Verbindung mit dem Windows-Geräte Portal auf den hololens herzustellen

Wenn Sie diesen Benutzernamen oder das Kennwort jederzeit ändern möchten, können Sie diesen Vorgang wiederholen, indem Sie die Seite "Gerätesicherheit" aufrufen, indem Sie zu: https://< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm.

## <a name="security-certificate"></a>Sicherheitszertifikat

Wenn in Ihrem Browser ein "Zertifikat Fehler" angezeigt wird, können Sie ihn beheben, indem Sie eine Vertrauensstellung mit dem Gerät erstellen.

Jede HoloLens generiert ein eindeutiges selbstsigniertes Zertifikat für die SSL-Verbindung. Standardmäßig wird dieses Zertifikat vom Webbrowser des PC nicht als vertrauenswürdig angesehen, und Sie erhalten möglicherweise eine Meldung zu einem Zertifikatfehler. Sie können dieses Zertifikat von der HoloLens herunterladen (über USB oder ein vertrauenswürdiges WLAN-Netzwerk) und es auf dem PC als vertrauenswürdig einstufen, um eine sichere Verbindung mit dem Gerät herzustellen.
1. **Stellen Sie sicher, dass Sie sich in einem sicheren Netzwerk (USB-oder WLAN-Netzwerk, dem Sie Vertrauen) befinden.**
2. Laden Sie das Zertifikat dieses Geräts von der Seite "Sicherheit" im Geräte Portal herunter.
   * Navigieren Sie zu: https://< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm
   * Öffnen Sie den Knoten für System > Einstellungen. 
   * Scrollen Sie nach unten zu Gerätesicherheit, und klicken Sie auf die Schaltfläche "Zertifikat dieses Geräts herunterladen".
3. Installieren Sie das Zertifikat im Speicher "Vertrauenswürdige Stamm Zertifizierungsstellen" auf Ihrem PC.
   * Geben Sie im Windows-Menü Folgendes ein: Computer Zertifikate verwalten, und starten Sie das Applet.
   * Erweitern Sie den Ordner **Vertrauenswürdige Stamm Zertifizierungs** Stelle.
   * Klicken Sie auf den Ordner **Zertifikate**.
   * Wählen Sie im Menü „Aktion“ die Aktion „Alle Aufgaben“ > „Importieren“ aus.
   * Führen Sie den Zertifikatimport-Assistenten mit der Zertifikatdatei aus, die Sie vom Geräteportal heruntergeladen haben.
4. Starten Sie den Browser neu.

>[!NOTE]
> Dieses Zertifikat wird nur für das Gerät als vertrauenswürdig eingestuft, und der Benutzer muss den Prozess erneut durchlaufen, wenn das Gerät mit einem flashed versehen ist.


## <a name="device-portal-pages"></a>Seiten des Geräteportals

### <a name="home"></a>Startseite

![Windows-Geräte Portal-Startseite auf Microsoft hololens-](images/windows-device-portal-home-page-1000px.png)<br>
*Windows-Geräte Portal-Startseite für Microsoft hololens*

Die Geräteportalsitzung beginnt auf der Startseite. Der Zugriff auf andere Seiten erfolgt über die Navigationsleiste links von der Startseite.

Die Symbolleiste am oberen Rand der Seite ermöglicht den Zugriff auf häufig verwendete Status und Features.
* **Online**: Gibt an, ob das Gerät mit dem WLAN verbunden ist.
* **Herunterfahren**: Schaltet das Gerät aus.
* **Neu starten**: Schaltet das Gerät aus und wieder ein.
* **Sicherheit**: Öffnet die Seite „Device Security“.
* **Cool**: Gibt die Temperatur des Geräts an.
* **A/C**: Gibt an, ob das Gerät angeschlossen ist und geladen wird.
* **Hilfe**: Öffnet die Seite mit der Dokumentation der REST-Schnittstelle.

Auf der Startseite werden die folgenden Informationen angezeigt:
* **Geräte Status:** überwacht die Integrität des Geräts und meldet kritische Fehler.
* **Windows-Informationen:** zeigt den Namen der hololens und die aktuell installierte Version von Windows an.
* **Einstellungen**: Dieser Abschnitt enthält die folgenden Einstellungen:
   * **IPD**: Legt den Pupillenabstand (Interpupillary Distance, IPD) fest. Dies ist der Abstand in Millimeter zwischen dem Mittelpunkt der Pupillen des Benutzers, wenn dieser geradeaus schaut. Die Einstellung wird sofort wirksam. Der Standardwert wurde beim Einrichten des Geräts automatisch berechnet.
   * **Gerätename**: Weisen Sie der HoloLens einen Namen zu. Nach dem Ändern dieses Werts müssen Sie das Gerät neu starten, damit er wirksam wird. Nachdem Sie auf **Speichern**geklickt haben, wird ein Dialogfeld gefragt, ob Sie das Gerät sofort neu starten oder später neu starten möchten.
   * **Standbymoduseinstellungen**: Hier legen Sie die Wartezeit fest, bevor das Gerät in den Ruhezustand wechselt, wenn es angeschlossen ist und wenn es mit Akkustrom betrieben wird.

### <a name="3d-view"></a>3D View

![3D-Ansichts Seite im Windows-Geräte Portal auf Microsoft hololens-](images/3dview-1000px.png)<br>
*3D-Ansichts Seite im Windows-Geräte Portal unter Microsoft hololens*

Auf der Seite „3D View“ können Sie erkennen, wie die HoloLens Ihre Umgebung interpretiert. Navigieren Sie mit der Maus in der Ansicht:
* Drehen: Linksklick + Maus;
* Schwenken: Klicken Sie mit der rechten Maustaste auf + Maus.
* Zoom: Maus scrollen.
* **Überwachungs Optionen**
   * Aktivieren der kontinuierlichen visuellen Nachverfolgung durch Aktivieren der **visuellen Nachverfolgung erzwingen**. 
   * **Anhalten beendet** visuelle Überwachung.
* **Ansichtsoptionen**: Legen Sie Optionen für die 3D-Ansicht fest:
  * **Tracking**: gibt an, ob die visuelle Überwachung aktiv ist.
  * **Boden anzeigen**: Zeigt eine schachbrettartige Bodenfläche an.
  * **Frustum anzeigen**: Zeigt das Ansichts-Frustum an.
  * **Stabilisierungsebene anzeigen**: Zeigt die Ebene an, die von der HoloLens für die Bewegungsstabilisierung verwendet wird.
  * **Mesh anzeigen**: zeigt das räumliche Mapping-Mesh an, das Ihre Umgebung darstellt.
  * **Räumliche Anker anzeigen**: zeigt räumliche Anker für die aktive APP an. Sie müssen auf die Schaltfläche Aktualisieren klicken, um die Anker zu erhalten und zu aktualisieren.
  * **Details anzeigen**: Zeigt die Änderung von Handpositionen, der Kopfdrehungsquaternionen und des Geräteursprungsvektors in Echtzeit an.
  * **Vollbildschaltfläche**: Mit dieser Schaltfläche wird die Seite „3D View“ im Vollbildmodus angezeigt. Drücken Sie die ESC-Taste, um die Vollbildansicht zu beenden.
* **Oberfläche-wieder**Herstellung: Klicken oder tippen Sie auf **Aktualisieren** , um das neueste räumliche zugriffsmesh vom Gerät anzuzeigen. Ein vollständiger Durchlauf kann einige Zeit in Anspruch nehmen (bis zu wenigen Sekunden). Das Mesh wird in der 3D-Ansicht nicht automatisch aktualisiert, und Sie müssen manuell auf " **Aktualisieren** " klicken, um das neueste Mesh vom Gerät zu erhalten. Klicken Sie auf **Speichern** , um das aktuelle räumliche Mapping-Mesh als obj-Datei auf Ihrem PC zu speichern.
* **Räumliche Anker**: Klicken Sie auf "Aktualisieren", um die räumlichen Anker für die aktive App anzuzeigen oder zu aktualisieren.

### <a name="mixed-reality-capture"></a>Mixed Reality Capture

![Mixed Reality Capture Page im Windows-Geräte Portal auf Microsoft hololens-](images/windows-device-portal-mixed-reality-capture-page-1000px.png)<br>
*Gemischte Reality-Erfassungs Seite im Windows-Geräte Portal unter Microsoft hololens*

Auf der Seite „Mixed Reality Capture“ können Sie Mediendatenströme von der HoloLens speichern.
* **Einstellungen**: Steuern der Mediendaten Ströme, die erfasst werden, indem die folgenden Einstellungen überprüft werden:
  * **Holograms**: erfasst den Holographic-Inhalt im Videostream. Hologramme werden in Mono und nicht in Stereo gerendert.
  * **PV camera**: Erfasst den Videodatenstrom der Foto-/Videokamera.
  * **Mic Audio**: Erfasst Audioaufnahmen vom Mikrofonarray.
  * **App Audio**: Erfasst Audioaufnahmen von der derzeit ausgeführten App.
  * **Rendering von Kamera**: richtet die Erfassung so aus, dass Sie aus der Perspektive der Foto-/Videokamera besteht, wenn Sie [von der laufenden App unterstützt](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) wird (nur hololens 2).
  * **Live preview quality**: Wählen Sie die Bildschirmauflösung, Bildfrequenz und Streamingrate für die Live-Vorschau aus.
* Klicken oder tippen Sie auf die **Live Vorschau** Schaltfläche, um den Aufzeichnungsdaten Strom anzuzeigen. " **Live Preview beenden** " beendet den Aufzeichnungsdaten Strom.
* Klicken oder tippen Sie auf **Datensatz** , um mit den angegebenen Einstellungen zu beginnen, den Mixed-Reality-Stream aufzuzeichnen. **Aufzeichnung beenden** beendet die Aufzeichnung und speichert Sie.
* Klicken oder tippen Sie auf **Foto aufnehmen** , um ein Bild aus dem Erfassungsdaten Strom zu übernehmen.
* **Videos und Fotos**: Zeigt eine Liste der auf dem Gerät aufgenommenen Videos und Fotos an.

> [!NOTE]
> Es gibt [Einschränkungen für die gleichzeitige MRC](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations)-Authentifizierung:
> * Wenn eine APP versucht, auf die Foto-/Videokamera zuzugreifen, während das Windows-Geräte Portal ein Video zeichnet, wird die Videoaufzeichnung angehalten.
>   * Hololens 2 hält das Aufzeichnen von Videos nicht an, wenn die APP mit dem sharedreadonly-Modus auf die Foto-/Videokamera zugreift.
> * Wenn eine APP aktiv die Foto-/Videokamera verwendet, kann das Windows-Geräte Portal ein Foto aufnehmen oder ein Video aufzeichnen.
> * Live Streaming:
>   * Hololens (1st Gen) verhindert, dass eine APP auf die Foto-/Videokamera zugreift, während Live Streaming vom Windows-Geräte Portal aus durchführen.
>   * Hololens (1st Gen) kann nicht in den Livestream geschaltet werden, wenn eine APP aktiv die Foto-/Videokamera verwendet.
>   * Hololens 2 hält Live Streaming automatisch an, wenn eine APP versucht, auf die Foto-/Videokamera im exclusivecontrol-Modus zuzugreifen.
>   * Hololens 2 kann einen Livestream starten, während eine APP aktiv die PV-Kamera verwendet.

### <a name="performance-tracing"></a>Leistungs Ablauf Verfolgung

![Seite "Leistungs Ablauf Verfolgung" im Windows-Geräte Portal unter Microsoft hololens](images/windows-device-portal-performance-tracing-page-1000px.png)<br>
*Seite "Leistungs Ablauf Verfolgung" im Windows-Geräte Portal unter Microsoft hololens*

Erfassen Sie [Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (WPR)-Ablauf Verfolgungen aus ihren hololens.
* **Verfügbare Profile**: Wählen Sie in der Dropdownliste das WPR-Profil aus, und klicken oder tippen Sie auf **Starten**, um die Ablaufverfolgung zu starten.
* **Benutzerdefinierte Profile**: Klicken oder tippen Sie auf **Durchsuchen**, um ein WPR-Profil vom PC auszuwählen. Klicken oder tippen Sie auf **Hochladen und starten**, um die Ablaufverfolgung zu starten.

Um die Ablauf Verfolgung anzuhalten, klicken Sie auf den Link "Abbrechen". Bleiben Sie auf dieser Seite, bis das Herunterladen der Ablauf Verfolgungs Datei abgeschlossen ist.

Aufgezeichnete ETL-Dateien können in [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx) für die Analyse geöffnet werden.

### <a name="processes"></a>Prozesse

Seite "![Prozesse" im Windows-Geräte Portal unter Microsoft hololens](images/windows-device-portal-running-processes-page-1000px.png)<br>
*Seite "Prozesse" im Windows-Geräte Portal unter Microsoft hololens*

Zeigt Details zu derzeit ausgeführten Prozessen an. Diese umfassen Apps und Systemprozesse.

### <a name="system-performance"></a>Systemleistung

![Seite "System Leistung" im Windows-Geräte Portal auf Microsoft hololens](images/windows-device-portal-system-performance-page-1000px.png)<br>
*Seite "System Leistung" im Windows-Geräte Portal unter Microsoft hololens*

Zeigt Echtzeitgraphen mit Informationen zur Systemdiagnose an, z. B. Stromverbrauch, Bildfrequenz und CPU-Last.

Die folgenden Metriken sind verfügbar:
* **SoC Power**: Sofortige Nutzung des System-on-a-Chip-Stroms, gemittelt über eine Minute.
* **Systemstromversorgung**: Sofortige Nutzung des Systemstroms, gemittelt über eine Minute.
* **Framerate**: Bilder pro Sekunde, übersprungene VBlanks pro Sekunde und aufeinanderfolgende übersprungene VBlanks
* **GPU**: Auslastung des GPU-Moduls, gesamte Verfügbarkeit in Prozent
* **CPU**: Verfügbarkeit in Prozent
* **E/A**: Lese- und Schreibvorgänge
* **Netzwerk**: Empfangen und gesendet
* Arbeits **Speicher**: Gesamtmenge, Verwendung, Commit, Auslagerung und nicht Auslagerungsseiten

### <a name="apps"></a>Apps

![Seite "Apps" im Windows-Geräte Portal auf Microsoft hololens](images/windows-device-portal-apps-page-1000px.png)<br>
*Seite "Apps" im Windows-Geräte Portal unter Microsoft hololens*

Verwaltet die apps, die auf den hololens installiert sind.
* **Installierte Apps**: Hier können Sie Apps entfernen und starten.
* **Running apps**: Listet Apps auf, die derzeit ausgeführt werden.
* **App installieren**: Wählen Sie App-Pakete für die Installation aus einem Ordner auf Ihrem Computer/Netzwerk aus.
* **Abhängigkeit**: Hier fügen Sie Abhängigkeiten für die zu installierende App hinzu.
* Bereit **stellen: Stellen**Sie die ausgewählten apps und Abhängigkeiten in den hololens bereit.

### <a name="app-crash-dumps"></a>Absturz Abbilder für apps

Seite "![App-Absturz Abbilder" im Windows-Geräte Portal unter Microsoft hololens](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)<br>
*Seite "Absturz Abbilder für App" im Windows-Geräte Portal unter Microsoft hololens*

Auf dieser Seite können Sie Absturzabbilder für die quergeladenen Apps erfassen. Aktivieren Sie das Kontrollkästchen "Absturz Abbilder **aktiviert** " für jede APP, für die Sie Absturz Abbilder sammeln möchten. Kehren Sie zum Erfassen von Absturzabbildern zu dieser Seite zurück. Dumpdateien können [zum Debuggen in Visual Studio geöffnet](https://msdn.microsoft.com/library/d5zhxt22.aspx)werden.

### <a name="file-explorer"></a>Datei-Explorer

![Seite "Datei-Explorer" im Windows-Geräte Portal für Microsoft hololens](images/fileexplorer-1000px.png)<br>
*Seite "Datei-Explorer" im Windows-Geräte Portal unter Microsoft hololens*

Verwenden Sie den Datei-Explorer, um Dateien zu durchsuchen, hochzuladen und herunterzuladen. Sie können mit Dateien im Ordner "Dokumente", im Ordner "Bilder" und in den lokalen Speicher Ordnern für apps arbeiten, die Sie über Visual Studio oder das Geräte Portal bereitgestellt haben.

### <a name="kiosk-mode"></a>Kioskmodus

>[!NOTE]
>Der Kiosk Modus ist nur bei der [kommerziellen Suite von Microsoft hololens](commercial-features.md)verfügbar.

Aktuelle Anweisungen zum Aktivieren des Kiosk Modus über das Windows-Geräte Portal finden Sie im Artikel [Einrichten von hololens im Kiosk Modus](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) im Windows IT-Portal.

### <a name="logging"></a>Protokollierung

![Seite "Protokollierung" im Windows-Geräte Portal auf Microsoft hololens](images/windows-device-portal-logging-page-1000px.png)<br>
*Seite "Protokollierung" im Windows-Geräte Portal unter Microsoft hololens*

Verwaltet die Echtzeit-Ereignis Ablauf Verfolgung für Windows (ETW) auf den hololens.

Aktivieren Sie **Anbieter ausblenden** , um nur die **Ereignis** Liste anzuzeigen.
* **Registrierte Anbieter**: Wählen Sie den ETW-Anbieter und die Ablaufverfolgungsebene aus. Für die Ablaufverfolgungsebene wird einer der folgenden Werte festgelegt:
   1. Abnormal exit or termination
   2. Severe errors
   3. Warnungen
   4. Non-error warnings

Klicken oder tippen Sie auf **Aktivieren**, um die Ablaufverfolgung zu starten. Der Anbieter wird der Liste **Aktivierte Anbieter** hinzugefügt.
* **Benutzerdefinierte Anbieter**: Wählen Sie einen benutzerdefinierten ETW-Anbieter und die Ablaufverfolgungsebene aus. Identifizieren Sie den Anbieter anhand seiner GUID. Fügen Sie keine Klammern in die GUID ein.
* **Enabled Providers**: Listet die aktivierten Anbieter auf. Wählen Sie einen Anbieter aus der Dropdownliste aus, und klicken oder tippen Sie auf **Deaktivieren**, um die Ablaufverfolgung zu beenden. Klicken oder tippen Sie auf **Beenden**, um sämtliche Ablaufverfolgung anzuhalten.
* **Anbieterverlauf**: Zeigt die ETW-Anbieter an, die während der aktuellen Sitzung aktiviert wurden. Klicken oder tippen Sie auf **Aktivieren**, um einen Anbieter zu aktivieren, der deaktiviert war. Klicken oder tippen Sie auf **Löschen**, um den Verlauf zu löschen.
* **Ereignisse**: Listet-ETW-Ereignisse der ausgewählten Anbieter im Tabellenformat auf. Diese Tabelle wird in Echtzeit aktualisiert. Klicken Sie unter der Tabelle auf die Schaltfläche **Löschen**, um alle ETW-Ereignisse aus der Tabelle zu löschen. Hierdurch werden keine Anbieter deaktiviert. Sie können auf **In Datei speichern** klicken, um die derzeit erfassten ETW-Ereignisse in eine lokale CSV-Datei zu exportieren.
* **Filter**: Hiermit können Sie die ETW-Ereignisse filtern, die nach ID, Schlüsselwort, Ebene, Anbieter Name, Aufgaben Name oder Text gesammelt werden. Sie können mehrere Kriterien zusammen kombinieren:
   1. Für Kriterien, die auf dieselbe Eigenschaft angewendet werden, werden Ereignisse angezeigt, die eines dieser Kriterien erfüllen können.
   2. Bei Kriterien, die auf eine andere Eigenschaft angewendet werden, müssen Ereignisse alle Kriterien erfüllen.

Sie können z. b. die Kriterien angeben *(der Taskname enthält ' foo ' oder ' Bar ') und (Text enthält ' error ' oder ' Warning ')* .

### <a name="simulation"></a>Simulation

![Simulations Seite im Windows-Geräte Portal für Microsoft hololens](images/windows-device-portal-simulation-page-1000px.png)<br>
*Simulations Seite im Windows-Geräte Portal unter Microsoft hololens*

Ermöglicht Ihnen das Aufzeichnen und Wiedergeben von Eingabedaten für Testzwecke.
* **Capture room**: Wird verwendet, um eine Datei für einen simulierten Raum herunterzuladen, die das Spatial-Mapping-Gitter für die Umgebung des Benutzers enthält. Benennen Sie den Raum, und klicken Sie dann auf **erfassen** , um die Daten als xef-Datei auf Ihrem PC zu speichern. Diese Raumdatei kann in den HoloLens-Emulator geladen werden.
* **Aufzeichnung**: Überprüfen Sie die Datenströme, die aufgezeichnet werden sollen, benennen Sie die Aufzeichnung, und klicken oder tippen Sie auf **Datensatz** , um das neu Führen Sie Aktionen mit ihren hololens aus, und klicken Sie dann auf " **Abbrechen** ", um die Daten als xef-Datei auf Ihrem PC zu speichern. Diese Datei kann im HoloLens-Emulator oder auf dem Gerät geladen werden.
* **Wiedergabe**: Klicken oder tippen Sie auf **Aufzeichnung hochladen** , um eine xef-Datei von Ihrem PC auszuwählen und die Daten an die hololens zu senden.
* **Steuerelement Modus**: Wählen Sie in der Dropdown Liste die Option **Standard** oder **Simulation** aus, und klicken oder tippen Sie auf die Schaltfläche **festlegen** , um den Modus auf den hololens auszuwählen. Durch Auswahl von „Simulation“ werden die realen Sensoren auf der HoloLens deaktiviert und stattdessen hochgeladene simulierte Daten verwendet. Wenn Sie zu „Simulation“ wechseln, reagiert die HoloLens nicht auf den realen Benutzer, bis Sie zurück zu „Standard“ wechseln.

### <a name="networking"></a>Netzwerk

![Netzwerkseite im Windows-Geräte Portal für Microsoft hololens](images/windows-device-portal-networking-page-1000px.png)<br>
*Netzwerkseite im Windows-Geräte Portal unter Microsoft hololens*

Verwaltet WLAN-Verbindungen auf den hololens.
* **WiFi-Adapter**: Wählen Sie einen WLAN-Adapter und ein Profil mithilfe der Dropdown-Steuerelemente aus. Klicken oder tippen Sie auf **verbinden** , um den ausgewählten Adapter zu verwenden.
* **Verfügbare Netzwerke**: Listet die WLAN-Netzwerke auf, mit denen die hololens eine Verbindung herstellen können. Klicken oder tippen Sie auf **Aktualisieren** , um die Liste zu aktualisieren.
* **IP-Konfiguration**: zeigt die IP-Adresse und andere Details der Netzwerkverbindung an.

### <a name="virtual-input"></a>Virtual Input

![Seite virtuelle Eingabe im Windows-Geräte Portal auf Microsoft hololens-](images/windows-device-portal-virtual-input-page-1000px.png)<br>
*Virtuelle Eingabe Seite im Windows-Geräte Portal unter Microsoft hololens*

Sendet die Tastatureingabe vom Remotecomputer an die HoloLens.

Klicken oder tippen Sie auf den Bereich unter **virtuelle Tastatur** , um das Senden von Tastatureingaben an die hololens zu aktivieren. Geben Sie in das Textfeld **Eingabetext** ein, und klicken oder tippen Sie auf **senden** , um die Tastatureingaben an die aktive APP zu senden.

## <a name="device-portal-rest-apis"></a>Geräte Portal-Rest-API

Alles im Geräte Portal basiert auf der [Rest-API](device-portal-api-reference.md) , die Sie optional zum Zugreifen auf die Daten und zum programmgesteuerten Steuern des Geräts verwenden können.
