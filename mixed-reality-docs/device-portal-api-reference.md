---
title: Device Portal-API-Referenz
description: API-Referenz für die Windows Device Portal für HoloLens
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Windows Device Portal-,-API
ms.openlocfilehash: 4b5b48c13b1b7ec8bfdf447f42097a8448b6a0e6
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694435"
---
# <a name="device-portal-api-reference"></a>Device Portal-API-Referenz

Alles, was in der [Windows Device Portal](using-the-windows-device-portal.md) basiert auf REST-API, Sie verwenden können, auf die Daten zugreifen und Ihr Gerät programmgesteuert steuern.

## <a name="app-deloyment"></a>App-Bereitstellung

**/API/App/packagemanager/Package (löschen)**

Eine app deinstalliert

Parameter
* Paket: Der Dateiname des Pakets deinstalliert werden.

**/api/app/packagemanager/package (POST)**

Installieren einer App

Parameter
* Paket: Der Dateiname des Pakets installiert werden.

Nutzlast
* Mehrteilige konformen http-Text

**/API/App/packagemanager/Packages (GET)**

Ruft die Liste der installierten apps auf dem System mit details

Zurückgeben von Daten
* Liste der installierten Pakete mit den details

**/api/app/packagemanager/state (GET)**

Ruft den Status des in-app-Installation wird ausgeführt

## <a name="dump-collection"></a>Absturzabbildsammlung

**/api/debug/dump/usermode/crashcontrol (DELETE)**

Deaktiviert die absturzabbilderfassung für sideload-Apps

Parameter
* PackageFullname: Paketname

**/api/debug/dump/usermode/crashcontrol (GET)**

Ruft die Einstellungen für quergeladene apps absturzabbilderfassung

Parameter
* PackageFullname: Paketname

**/api/debug/dump/usermode/crashcontrol (POST)**

Aktiviert und legt Dump-verwaltungseinstellungen für sideload-Apps

Parameter
* PackageFullname: Paketname

**/api/debug/dump/usermode/crashdump (DELETE)**

Löscht ein Absturzabbild für eine app mittels sideload übertragene

Parameter
* PackageFullname: Paketname
* Dateiname: Dump-Dateiname

**/api/debug/dump/usermode/crashdump (GET)**

Ruft ein Absturzabbild für eine app mittels sideload übertragene

Parameter
* PackageFullname: Paketname
* Dateiname: Dump-Dateiname

Zurückgeben von Daten
* Sichern Sie die Datei. Überprüfen Sie mit WinDbg oder Visual Studio

**/api/debug/dump/usermode/dumps (GET)**

Gibt eine Liste mit allen Absturzabbilder für quergeladene apps

Zurückgeben von Daten
* Liste der Abstürze pro Seite geladen app sichert

## <a name="etw"></a>ETW

**/API/ETW/Providers (GET)**

Listet die registrierten Anbieter

Zurückgeben von Daten
* Liste der Anbieter "," Anzeigename "und" GUID

**/api/etw/session/realtime (GET/WebSocket)**

Erstellt eine Echtzeit-ETW-Sitzung. über ein Websocket verwaltet werden.

Zurückgeben von Daten
* ETW-Ereignisse von den aktivierten Anbietern

## <a name="holographic-os"></a>Holographic – Betriebssystem

**/api/holographic/os/etw/customproviders (GET)**

Gibt eine Liste von HoloLens bestimmte ETW-Anbieter, die nicht mit dem System registriert sind

**/api/holographic/os/services (GET)**

Gibt den Status aller Dienste, die ausgeführt wird.

**/api/holographic/os/settings/ipd (GET)**

Ruft den gespeicherten Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor (Interpupillary Abstand) in Millimeter

**/api/holographic/os/settings/ipd (POST)**

Legt die IPD

Parameter
* IPD: Neues IPD-Wert in Millimetern festgelegt werden

**/api/holographic/os/webmanagement/settings/https (GET)**

Abrufen der HTTPS-Anforderungen für das Geräteportal

**/api/holographic/os/webmanagement/settings/https (POST)**

Legt die HTTPS-Anforderungen für das Device Portal

Parameter
* erforderlich: Ja, Nein oder Standardwert

## <a name="holographic-perception"></a>Holographic Wahrnehmung

**/api/holographic/perception/client (GET/WebSocket)**

Upgrades der Websocket akzeptiert, und führt einen Wahrnehmung-Client, der Updates auf 30 BpS sendet.

Parameter
* Clientmode: "aktiv" erzwingt eine visual Nachverfolgungsmodus, wenn es nicht Passiv hergestellt werden kann

## <a name="holographic-thermal"></a>Holographic Thermischer

**/api/holographic/thermal/stage (GET)**

Abrufen der temperaturüberwachung Phase des Geräts (0 – Normal, 1 betriebsbereiten, 2, kritische)

## <a name="perception-simulation-control"></a>Perception Simulation-Steuerelement

**/api/holographic/simulation/control/mode (GET)**

Wurde der Simulationsmodus abrufen

**/api/holographic/simulation/control/mode (POST)**

Legen Sie den Simulationsmodus

Parameter
* Modus: Simulationsmodus: Standard, Simulation, Remote, ältere

**/api/holographic/simulation/control/stream (DELETE)**

Löschen Sie einen Steuerelement-Datenstrom.

**/api/holographic/simulation/control/stream (GET/WebSocket)**

Öffnen Sie eine Web-Socket-Verbindung für einen Steuerelement-Datenstrom.

**/api/holographic/simulation/control/stream (POST)**

Erstellen Sie einen Steuerelement-Datenstrom (Priorität erforderlich ist) oder Veröffentlichen von Daten für einen erstellten Stream (StreamId erforderlich). Bereitgestellte Daten werden vom Typ "Application/Octet-Stream" erwartet.

## <a name="perception-simulation-playback"></a>Perception Simulation Wiedergabe

**/API/holographic/Simulation/Playback/File (löschen)**

Löschen Sie eine Aufzeichnung.

Parameter
* Aufzeichnung: Der Name der Aufnahme zur löschen.

**/api/holographic/simulation/playback/file (POST)**

Laden Sie eine Aufzeichnung hoch.

**/API/holographic/Simulation/Playback/Files (GET)**

Alle Aufzeichnungen zu erhalten.

**/API/holographic/Simulation/Playback/Session (GET)**

Rufen Sie den aktuellen Status der Wiedergabe einer Aufzeichnung an.

Parameter
* Aufzeichnung: Der Name der Aufzeichnung.

**/API/holographic/Simulation/Playback/Session/File (löschen)**

Entladen Sie eine Aufzeichnung.

Parameter
* Aufzeichnung: Der Name der Aufnahme zur nicht entladen.

**/API/holographic/Simulation/Playback/Session/File (POST)**

Laden Sie eine Aufzeichnung.

Parameter
* Aufzeichnung: Der Name der Aufnahme zur geladen werden.

**/API/holographic/Simulation/Playback/Session/Files (GET)**

Alle geladene Aufzeichnungen zu erhalten.

**/api/holographic/simulation/playback/session/pause (POST)**

Halten Sie eine Aufzeichnung.

Parameter
* Aufzeichnung: Der Name der Aufzeichnung.

**/API/holographic/Simulation/Playback/Session/Play (POST)**

Wiedergeben Sie eine Aufnahme.

Parameter
* Aufzeichnung: Der Name der Aufzeichnung.

**/api/holographic/simulation/playback/session/stop (POST)**

Eine Aufzeichnung zu beenden.

Parameter
* Aufzeichnung: Der Name der Aufzeichnung.

**/API/holographic/Simulation/Playback/Session/Types (GET)**

Rufen Sie die Arten von Daten in einer geladenen Aufzeichnung an.

Parameter
* Aufzeichnung: Der Name der Aufzeichnung.

## <a name="perception-simulation-recording"></a>Aufzeichnung der Wahrnehmung-Simulation

**/api/holographic/simulation/recording/start (POST)**

Starten Sie Aufzeichnung. Nur eine einzigen Aufzeichnung gleichzeitig aktiv sein kann. Head, praktische, SpatialMapping oder Umgebung muss festgelegt, werden.

Parameter
* Head: Legen Sie auf 1 fest, um die Daten des Datensatzes Head.
* praktische: Auf 1 festgelegt, um manuell Daten aufzuzeichnen.
* SpatialMapping: Auf 1 festgelegt, um die räumliche Zuordnung zu zeichnen.
* Umgebung: Zum Aufzeichnen von Umgebungsdaten auf 1 festgelegt.
* Name: Der Name der Aufzeichnung.
* SingleSpatialMappingFrame: Auf 1 festgelegt, um nur einen einzigen räumliche Zuordnung Frame zu erfassen.

**/api/holographic/simulation/recording/status (GET)**

Aufzeichnen von Status zu erhalten.

**/api/holographic/simulation/recording/stop (GET)**

Die aktuelle Aufzeichnung zu beenden. Aufzeichnung wird als Datei zurückgegeben.

## <a name="mixed-reality-capture"></a>Mixed Reality Capture

**/api/holographic/mrc/file (GET)**

Lädt eine mixed Reality-Datei auf dem Gerät herunter. Verwenden von Op = Stream-Abfrageparameter für das streaming.

Parameter
* Dateiname: Name, hex64 codiert, der die Datei zum Abrufen
* Op: Stream

**/API/holographic/MRC/File (löschen)**

Löscht die gemischte Realität vom Gerät aufzeichnen.

Parameter
* Dateiname: Name, hex64 codiert, der zu löschenden Datei

**/api/holographic/mrc/files (GET)**

Gibt die Liste der auf dem Gerät gespeicherten mixed Reality-Dateien

**/api/holographic/mrc/photo (POST)**

Nimmt ein Foto mixed Reality und erstellt eine Datei auf dem Gerät

Parameter
* Holo: Erfassen von Hologramme: "true" oder "false" (standardmäßig "false")
* PV: Erfassung PV Kamera: "true" oder "false" (standardmäßig "false")
* RenderFromCamera: (Gilt nur für HoloLens-2) Rendern aus Perspektive der Fotogalerie/Videokamera: "true" oder "false" (standardmäßig auf "true")

**/api/holographic/mrc/settings (GET)**

Ruft gemischt den Standard tatsächlich Capture-Einstellungen

**/api/holographic/mrc/settings (POST)**

Legt kombiniert den Standard tatsächlich Capture-Einstellungen.  Einige dieser Einstellungen werden auf MRC Foto und Erfassen des Systems angewendet.

**/api/holographic/mrc/status (GET)**

Ruft den Status der mixed Reality aufgezeichnet ("ausführen", "beendet")

**/API/holographic/MRC/Thumbnail (GET)**

Ruft die Miniaturansicht für die angegebene Datei.

Parameter
* Dateiname: Name, hex64 codiert, der die Datei, die für die die Miniaturansicht angefordert wird

**/api/holographic/mrc/video/control/start (POST)**

Startet eine Aufzeichnung mixed reality

Parameter
* Holo: Erfassen von Hologramme: "true" oder "false" (standardmäßig "false")
* PV: Erfassung PV Kamera: "true" oder "false" (standardmäßig "false")
* MIC: Erfassung Mikrofon: "true" oder "false" (standardmäßig "false")
* Loopback: Erfassen von app-Audio: "true" oder "false" (standardmäßig "false")
* RenderFromCamera: (Gilt nur für HoloLens-2) Rendern aus Perspektive der Fotogalerie/Videokamera: "true" oder "false" (standardmäßig auf "true")
* Vstab: Enable-videostabilisierung (gilt nur für HoloLens-2): "true" oder "false" (standardmäßig auf "true")
* vstabbuffer: (Gilt nur für HoloLens-2) videostabilisierung Puffer Latenz: 0 bis 30 Frames (standardmäßig 15 Frames)

**/api/holographic/mrc/video/control/stop (POST)**

Beendet kombiniert die aktuelle Realität Aufzeichnung

## <a name="mixed-reality-streaming"></a>Mixed Reality-Streaming

HoloLens unterstützt die Livevorschau von mixed Reality über aufgeteilte Download von einem fragmentierte MP4-Dateien.

Mixed Reality-Streams teilen den gleichen Satz von Parametern, die steuern, was erfasst werden:
* Holo: Erfassen von Hologramme: "true" oder "false"
* PV: Erfassung PV Kamera: "true" oder "false"
* MIC: Erfassung Mikrofon: "true" oder "false"
* Loopback: Erfassen von app-Audio: "true" oder "false"

Wenn keine dieser Optionen angegeben werden:-Hologramme, Foto/Videokamera und app-Audio werden erfasst werden<br>
Wenn angegeben werden: die Parameter nicht angegeben werden standardmäßig auf "false"

Optionale Parameter (gilt nur für HoloLens-2)
* RenderFromCamera: Rendern aus Perspektive der Fotogalerie/Videokamera: "true" oder "false" (standardmäßig auf "true")
* Vstab: Aktivieren von videostabilisierung: "true" oder "false" (standardmäßig "false")
* Vstabbuffer: videostabilisierung Puffer Latenz: 0 bis 30 Frames (standardmäßig 15 Frames)

**/api/holographic/stream/live.mp4 (GET)**

Ein 1280x720p 30 BpS 5Mbit-Datenstrom.

**/api/holographic/stream/live_high.mp4 (GET)**

Ein 1280x720p 30 BpS 5Mbit-Datenstrom.

**/api/holographic/stream/live_med.mp4 (GET)**

Ein 854x480p 30 BpS 2.5Mbit-Datenstrom.

**/api/holographic/stream/live_low.mp4 (GET)**

Ein 428x240p 15fps 0.6Mbit-Datenstrom.

## <a name="networking"></a>Netzwerk

**/api/networking/ipconfig (GET)**

Ruft die aktuelle IP-Konfiguration

## <a name="os-information"></a>Informationen zum Betriebssystem

**/api/os/info (GET)**

Ruft Informationen zum Betriebssystem

**/api/os/machinename (GET)**

Ruft den Computernamen ab

**/api/os/machinename (POST)**

Legt den Computernamen fest

Parameter
* Name: Neuen Namen des Computers hex64 codiert, um für die Verwendung

## <a name="performance-data"></a>Leistungsdaten

**/api/resourcemanager/processes (GET)**

Gibt die Liste der ausgeführten Prozesse mit details

Zurückgeben von Daten
* JSON mit Liste der Prozesse und Details für jeden Prozess

**/api/resourcemanager/systemperf (GET)**

Statistische Daten aus System Perf (e/a-Lese-/Schreibzugriff, speicherstatistiken usw.

Zurückgeben von Daten
* JSON mit Systeminformationen: CPU, GPU, Arbeitsspeicher, Netzwerk, e/a

## <a name="power"></a>Stromversorgung

**/api/power/battery (GET)**

Ruft den aktuellen Zustand der Akkus

**/API/Power/State (GET)**

Überprüft, ob das System in einen Energiesparmodus ist.

## <a name="remote-control"></a>Remotesteuerung

**/api/control/restart (POST)**

Wird die Zielgerät neu gestartet

**/api/control/shutdown (POST)**

Das Gerät heruntergefahren

## <a name="task-manager"></a>Task-Manager

**/api/taskmanager/app (DELETE)**

Beendet einen modernen Apps

Parameter
* Paket: Vollständigen Namen des app-Pakets, hex64 codiert
* "forcestop": Erzwingen, dass alle Prozesse beendet (= Yes)

**/api/taskmanager/app (POST)**

Startet einen modernen Apps

Parameter
* App-ID: PRAID der app zu starten, codiert hex64
* Paket: Vollständigen Namen des app-Pakets, hex64 codiert

## <a name="wifi-management"></a>WiFi-Verwaltung

**/API/WiFi/Interfaces (GET)**

Listet Drahtlosnetzwerk-Schnittstellen

Zurückgeben von Daten
* Liste der drahtlosen Schnittstellen mit den Details (GUID, Beschreibung usw.).

**/api/wifi/network (DELETE)**

Löscht ein Profil ein Netzwerk auf eine angegebene Schnittstelle zugeordnet

Parameter
* Schnittstelle: Netzwerk-Guid der Schnittstelle
* Profil: Profilname

**/api/wifi/networks (GET)**

Listet Drahtlosnetzwerke auf die angegebene Netzwerkschnittstelle

Parameter
* Schnittstelle: Netzwerk-Guid der Schnittstelle

Zurückgeben von Daten
* Liste der Drahtlosnetzwerke finden Sie auf die Netzwerkschnittstelle mit details

**/api/wifi/network (POST)**

Eine Verbindung herstellt oder trennt die Verbindung mit einem Netzwerk für die angegebene Schnittstelle

Parameter
* Schnittstelle: Netzwerk-Guid der Schnittstelle
* SSID: Ssid, hex64 codiert sind, klicken Sie zum Herstellen einer Verbindung mit
* Op: herstellen oder trennen
* CreateProfile: Ja oder Nein
* Schlüssel: shared Key, hex64 codiert

## <a name="windows-performance-recorder"></a>Windows-Leistungsaufzeichnung

**/api/wpr/customtrace (POST)**

Lädt ein WPR-Profil, und startet die Protokollierung mithilfe des hochgeladenen Profils.

Nutzlast
* Mehrteilige konformen http-Text

Zurückgeben von Daten
* Gibt den WPR-Sitzungsstatus zurück.

**/api/wpr/status (GET)**

Ruft den Status der Sitzung WPR ab

Zurückgeben von Daten
* WPR Sitzungsstatus.

**/api/wpr/trace (GET)**

Beendet eine Ablaufverfolgungssitzung WPR (Leistung)

Zurückgeben von Daten
* Gibt zurück, die ETL-Datei

**/api/wpr/trace (POST)**

Startet eine WPR (Leistung), die Ablaufverfolgung von Sitzungen

Parameter
* Profil: Profilname. Verfügbare Profile werden in perfprofiles/profiles.json gespeichert.

Zurückgeben von Daten
* Beim Start wird der WPR-Sitzung-Status zurückgegeben.

## <a name="see-also"></a>Siehe auch
* [Verwenden des Windows-Geräteportals](using-the-windows-device-portal.md)
* [Device Portal-Core-API-Referenz (UWP)](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
