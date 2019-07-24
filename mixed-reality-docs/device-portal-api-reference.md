---
title: Referenz zur Geräte Portal-API
description: API-Referenz für das Windows-Geräte Portal auf hololens
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: Hololens, Windows-Geräte Portal, API
ms.openlocfilehash: 4b5b48c13b1b7ec8bfdf447f42097a8448b6a0e6
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694435"
---
# <a name="device-portal-api-reference"></a>Referenz zur Geräte Portal-API

Alles im [Windows-Geräte Portal](using-the-windows-device-portal.md) baut auf der Rest-API auf, mit der Sie auf die Daten zugreifen und Ihr Gerät Programm gesteuert steuern können.

## <a name="app-deloyment"></a>App-Verlagerung

**/API/APP/packagemanager/Package (Löschen)**

Deinstalliert eine APP

Parameter
* Paketen Der Dateiname des Pakets, das deinstalliert werden soll.

**/API/APP/packagemanager/Package (Post)**

Installiert eine APP

Parameter
* Paketen Der Dateiname des zu installierenden Pakets.

Nutz
* Mehrteilige konforme HTTP-Text

**/API/APP/packagemanager/Packages (Get)**

Hiermit wird die Liste der installierten apps auf dem System mit Details abgerufen.

Rückgabe Daten
* Liste der installierten Pakete mit Details

**/API/APP/packagemanager/State (Get)**

Hiermit wird der Status der Installation in Progress-App abgerufen.

## <a name="dump-collection"></a>Absturzabbildsammlung

**/API/Debug/Dump/Usermode/CrashControl (Löschen)**

Deaktiviert die Absturz Abbild Erfassung für eine Sideload-app.

Parameter
* packagefullname: Paketname

**/API/Debug/Dump/Usermode/CrashControl (Get)**

Ruft Einstellungen für die Absturz Abbild Erfassung von Sideload-apps ab

Parameter
* packagefullname: Paketname

**/API/Debug/Dump/Usermode/CrashControl (Post)**

Aktiviert und legt Sicherungs Steuerungseinstellungen für eine per Sideload übertragene App fest.

Parameter
* packagefullname: Paketname

**/API/Debug/Dump/Usermode/crashdump (Löschen)**

Löscht einen Absturz Abbild für eine Sideload-app.

Parameter
* packagefullname: Paketname
* Dateiname: Name der Sicherungsdatei

**/API/Debug/Dump/Usermode/crashdump (Get)**

Ruft ein Absturz Abbild für eine per Sideload übertragene App ab.

Parameter
* packagefullname: Paketname
* Dateiname: Name der Sicherungsdatei

Rückgabe Daten
* Dumpdatei. Überprüfen mit WinDbg oder Visual Studio

**/API/Debug/Dump/Usermode/Dumps (Get)**

Gibt eine Liste aller Absturz Abbilder für Sideload-apps zurück.

Rückgabe Daten
* Liste der Absturz Abbilder pro Seite geladener apps

## <a name="etw"></a>ETW

**/API/etw/Providers (Get)**

Listet registrierte Anbieter auf.

Rückgabe Daten
* Liste der Anbieter, Anzeige Name und GUID

**/API/etw/Session/Realtime (Get/WebSocket)**

Erstellt eine ETW-Sitzung in Echtzeit. verwaltet über einen WebSocket.

Rückgabe Daten
* ETW-Ereignisse von aktivierten Anbietern

## <a name="holographic-os"></a>Holographic – Betriebssystem

**/API/Holographic/OS/etw/customproviders (Get)**

Gibt eine Liste von hololens-spezifischen etw-Anbietern zurück, die nicht beim System registriert sind.

**/API/Holographic/OS/Services (Get)**

Gibt die Zustände aller Dienste zurück, die ausgeführt werden.

**/API/Holographic/OS/Settings/IPD (Get)**

Ruft die gespeicherte IPD (interpupranäre Entfernung) in Millimeter ab.

**/API/Holographic/OS/Settings/IPD (Post)**

Legt die IPD fest.

Parameter
* IPD Neuer IPD-Wert, der in Millimeter festgelegt werden soll

**/API/Holographic/OS/Webmanagement/Settings/HTTPS (Get)**

Abrufen der HTTPS-Anforderungen für das Geräteportal

**/API/Holographic/OS/Webmanagement/Settings/HTTPS (Post)**

Legt die HTTPS-Anforderungen für das Geräte Portal fest.

Parameter
* erforderlich: Ja, Nein oder Standard

## <a name="holographic-perception"></a>Holografische Wahrnehmung

**/API/Holographic/perception/Client (Get/WebSocket)**

Akzeptiert WebSocket-Upgrades und führt einen perception-Client aus, der Updates bei 30 fps sendet.

Parameter
* clientmode: "aktiv" erzwingt den visuellen Überwachungsmodus, wenn er nicht passiv festgelegt werden kann.

## <a name="holographic-thermal"></a>Holographic-Therme

**/API/Holographic/Thermal/Stage (Get)**

Die wärmestufe des Geräts erhalten (0 normal, 1 warm, 2 kritisch)

## <a name="perception-simulation-control"></a>Wahrnehmungs Simulations-Steuerelement

**/API/Holographic/Simulation/Control/Mode (Get)**

Simulationsmodus erhalten

**/API/Holographic/Simulation/Control/Mode (Post)**

Festlegen des Simulationsmodus

Parameter
* Mode: Simulationsmodus: Standard, Simulation, Remote, Legacy

**/API/Holographic/Simulation/Control/Stream (Löschen)**

Löscht einen Steuerungsdaten Strom.

**/API/Holographic/Simulation/Control/Stream (Get/WebSocket)**

Öffnen Sie eine websocketverbindung für einen Steuerungsdaten Strom.

**/API/Holographic/Simulation/Control/Stream (Post)**

Erstellen Sie einen Steuerungsdaten Strom (Priorität ist erforderlich), oder stellen Sie Daten in einem erstellten Stream bereit (streamid erforderlich). Es wird erwartet, dass für die Daten der Typ "Application/Octett-Stream" festgestellt wird.

## <a name="perception-simulation-playback"></a>Wiedergabe von Wahrnehmungs Simulationen

**/API/Holographic/Simulation/Playback/File (Löschen)**

Löschen Sie eine Aufzeichnung.

Parameter
* verzeichnet Der Name der zu löschenden Aufzeichnung.

**/API/Holographic/Simulation/Playback/File (Post)**

Hochladen einer Aufzeichnung.

**/API/Holographic/Simulation/Playback/Files (Get)**

Alle Aufzeichnungen erhalten.

**/API/Holographic/Simulation/Playback/Session (Get)**

Gibt den aktuellen Wiedergabe Zustand einer Aufzeichnung an.

Parameter
* verzeichnet Der Name der Aufzeichnung.

**/API/Holographic/Simulation/Playback/Session/File (Löschen)**

Entladen Sie eine Aufzeichnung.

Parameter
* verzeichnet Der Name der zu entladenden Aufzeichnung.

**/API/Holographic/Simulation/Playback/Session/File (Post)**

Laden Sie eine Aufzeichnung.

Parameter
* verzeichnet Der Name der zu ladenden Aufzeichnung.

**/API/Holographic/Simulation/Playback/Session/Files (Get)**

Alle geladenen Aufzeichnungen erhalten.

**/API/Holographic/Simulation/Playback/Session/Pause (Post)**

Hält eine Aufzeichnung an.

Parameter
* verzeichnet Der Name der Aufzeichnung.

**/API/Holographic/Simulation/Playback/Session/Play (Post)**

Wiedergabe einer Aufzeichnung.

Parameter
* verzeichnet Der Name der Aufzeichnung.

**/API/Holographic/Simulation/Playback/Session/Stop (Post)**

Beendet eine Aufzeichnung.

Parameter
* verzeichnet Der Name der Aufzeichnung.

**/API/Holographic/Simulation/Playback/Session/Types (Get)**

Datentypen in einer geladenen Aufzeichnung erhalten.

Parameter
* verzeichnet Der Name der Aufzeichnung.

## <a name="perception-simulation-recording"></a>Erfassung von Wahrnehmungs Simulationen

**/API/Holographic/Simulation/Recording/Start (Post)**

Startet eine Aufzeichnung. Nur eine einzelne Aufzeichnung kann gleichzeitig aktiv sein. Eine der Köpfe, Hände, spatialmapping oder Umgebung muss festgelegt werden.

Parameter
* Stadt Legen Sie auf 1 fest, um Head-Daten aufzuzeichnen.
* Hände Legen Sie auf 1 fest, um die Daten aufzuzeichnen.
* spatialmapping: Legen Sie auf 1 fest, um die räumliche Zuordnung aufzuzeichnen.
* Umgebung Legen Sie auf 1 fest, um Umgebungs Daten aufzuzeichnen.
* Benennen Der Name der Aufzeichnung.
* singlespatialmappingframe: Legen Sie auf 1 fest, um nur einen einzelnen räumlichen zuordnungsframe aufzuzeichnen.

**/API/Holographic/Simulation/Recording/Status (Get)**

Aufzeichnungsstatus erhalten.

**/API/Holographic/Simulation/Recording/Stop (Get)**

Hält die aktuelle Aufzeichnung an. Die Aufzeichnung wird als Datei zurückgegeben.

## <a name="mixed-reality-capture"></a>Mixed Reality Capture

**/API/Holographic/MRC/File (Get)**

Hiermit wird eine gemischte Reality-Datei vom Gerät heruntergeladen. Verwenden Sie den OP = Stream-Abfrage Parameter für das Streaming.

Parameter
* Einfügen Name, hex64 codiert, der Videodatei, die Sie erhalten
* OP: Stream

**/API/Holographic/MRC/File (Löschen)**

Löscht eine gemischte Reality-Aufzeichnung auf dem Gerät.

Parameter
* Einfügen Name, hex64-codiert, der zu löschenden Datei

**/API/Holographic/MRC/Files (Get)**

Gibt die Liste der Mixed Reality-Dateien zurück, die auf dem Gerät gespeichert sind

**/API/Holographic/MRC/Photo (Post)**

Nimmt ein gemischtes Reality-Foto und erstellt eine Datei auf dem Gerät.

Parameter
* hololens: Erfassungs holograms: true oder false (Standardwert: false)
* PV: Erfassen der PV-Kamera: true oder false (Standardwert: false)
* Renderfromcamera: (Nur hololens 2) Rendering aus der Perspektive der Foto-/Videokamera: true oder false (Standardwert: true)

**/API/Holographic/MRC/Settings (Get)**

Ruft die Standardeinstellungen für die gemischte Realität-Erfassung ab.

**/API/Holographic/MRC/Settings (Post)**

Legt die Standardeinstellungen für die gemischte Reality-Erfassung fest.  Einige dieser Einstellungen werden auf das MRC-Foto und die Video Erfassung des Systems angewendet.

**/API/Holographic/MRC/Status (Get)**

Ruft den Status der aufgezeichnete gemischten Realität ab (wird ausgeführt, beendet).

**/API/Holographic/MRC/Thumbnail (Get)**

Ruft das Miniaturbild für die angegebene Datei ab.

Parameter
* Einfügen Name, hex64 codiert, der Datei, für die die Miniaturansicht angefordert wird

**/API/Holographic/MRC/Video/Control/Start (Post)**

Startet eine gemischte Reality-Aufzeichnung

Parameter
* hololens: Erfassungs holograms: true oder false (Standardwert: false)
* PV: Erfassen der PV-Kamera: true oder false (Standardwert: false)
* MIC: Mikrofon erfassen: true oder false (standardmäßig false)
* Loopback: App-Audioerfassung: true oder false (standardmäßig false)
* Renderfromcamera: (Nur hololens 2) Rendering aus der Perspektive der Foto-/Videokamera: true oder false (Standardwert: true)
* Vstab: (Nur hololens 2) Videostabilisierung aktivieren: true oder false (Standardwert: true)
* vstabbuffer: (Nur hololens 2), Video Stabilisierungs Puffer Wartezeit: zwischen 0 und 30 Frames (standardmäßig 15 Frames)

**/API/Holographic/MRC/Video/Control/Stop (Post)**

Beendet die aktuelle gemischte Reality-Aufzeichnung

## <a name="mixed-reality-streaming"></a>Streaming mit gemischter Realität

Hololens unterstützt die Live Vorschau von Mixed Reality über einen segmentierten Download einer fragmentierten MP4-Datei.

Gemischte Reality-Streams verwenden denselben Satz von Parametern, um zu steuern, was aufgezeichnet wird:
* hololens: Erfassungs holograms: true oder false
* PV: Erfassen der PV-Kamera: true oder false
* MIC: Mikrofon erfassen: true oder false
* Loopback: App-Audioerfassung: true oder false

Wenn keines dieser Angaben angegeben ist: holograms, Foto-/Videokamera und App-Audiodaten werden aufgezeichnet.<br>
Wenn eine Angabe festgelegt ist: die nicht angegebenen Parameter werden standardmäßig auf false festgelegt.

Optionale Parameter (nur hololens 2)
* Renderfromcamera: Rendering aus Perspektive der Foto-/Videokamera: true oder false (Standardwert ist true)
* Vstab: Videostabilisierung aktivieren: true oder false (Standardwert: false)
* vstabbuffer: Puffer Wartezeit für Videostabilisierung: zwischen 0 und 30 Frames (standardmäßig 15 Frames)

**/API/Holographic/Stream/Live.MP4 (Get)**

Ein-Datenstrom von 1280x720p 30 fps 5Mbit.

**/API/Holographic/Stream/live_high.MP4 (Get)**

Ein-Datenstrom von 1280x720p 30 fps 5Mbit.

**/API/Holographic/Stream/live_med.MP4 (Get)**

Ein 854x480p 30 fps 2.5 MBit-Stream.

**/API/Holographic/Stream/live_low.MP4 (Get)**

Ein 428x240 p 15fps 0.6-MBit-Stream.

## <a name="networking"></a>Netzwerk

**/API/Networking/ipconfig (Get)**

Ruft die aktuelle IP-Konfiguration ab.

## <a name="os-information"></a>Betriebssysteminformationen

**/API/OS/Info (Get)**

Ruft Betriebssysteminformationen ab.

**/API/OS/MachineName (Get)**

Ruft den Computernamen ab.

**/API/OS/MachineName (Post)**

Legt den Computernamen fest.

Parameter
* Benennen Neuer Computername, hex64-codiert, festgelegt auf

## <a name="performance-data"></a>Leistungsdaten

**/API/ResourceManager/Processes (Get)**

Gibt die Liste der laufenden Prozesse mit Details zurück.

Rückgabe Daten
* JSON mit einer Liste der Prozesse und Details für jeden Prozess

**/API/ResourceManager/systemperf (Get)**

Gibt die System Leistungsstatistik (e/a-Lese-/Schreibvorgänge, Speicher Statistiken usw.) zurück.

Rückgabe Daten
* JSON mit Systeminformationen: CPU, GPU, Arbeitsspeicher, Netzwerk, e/a

## <a name="power"></a>Stromversorgung

**/API/Power/Battery (Get)**

Ruft den aktuellen Akku Zustand ab.

**/API/Power/State (Get)**

Prüft, ob sich das System in einem niedrigen Energiezustand befindet

## <a name="remote-control"></a>Remotesteuerung

**/API/Control/Restart (Post)**

Startet das Zielgerät neu.

**/API/Control/Shutdown (Post)**

Fährt das Zielgerät herunter.

## <a name="task-manager"></a>Task-Manager

**/API/Taskmanager/app (Löschen)**

Beendet eine moderne App

Parameter
* Paketen Vollständiger Name des App-Pakets, hex64-codiert
* forcestop: Beendigung aller Prozesse erzwingen (= ja)

**/API/Taskmanager/app (Post)**

Startet eine moderne App

Parameter
* AppID Praid der APP, die gestartet werden soll, hex64-codiert
* Paketen Vollständiger Name des App-Pakets, hex64-codiert

## <a name="wifi-management"></a>WiFi-Verwaltung

**/API/WiFi/Interfaces (Get)**

Listet drahtlose Netzwerkschnittstellen auf.

Rückgabe Daten
* Liste der drahtlos Schnittstellen mit Details (GUID, Beschreibung usw.)

**/API/WiFi/Network (Löschen)**

Löscht ein Profil, das einem Netzwerk in einer angegebenen Schnittstelle zugeordnet ist.

Parameter
* Schnittstelle: GUID der Netzwerkschnittstelle
* Profil: Profilname

**/API/WiFi/Networks (Get)**

Listet drahtlose Netzwerke auf der angegebenen Netzwerkschnittstelle auf.

Parameter
* Schnittstelle: GUID der Netzwerkschnittstelle

Rückgabe Daten
* Liste der Drahtlos Netzwerke, die sich auf der Netzwerkschnittstelle befinden, mit Details

**/API/WiFi/Network (Post)**

Stellt eine Verbindung mit einem Netzwerk auf der angegebenen Schnittstelle her oder trennt es.

Parameter
* Schnittstelle: GUID der Netzwerkschnittstelle
* SSID: SSID, hex64-codiert, um eine Verbindung herzustellen
* OP: verbinden oder trennen
* kreateprofile: Ja oder Nein
* Schlüssel: gemeinsam verwendeter Schlüssel, hex64-codiert

## <a name="windows-performance-recorder"></a>Windows-Leistungs Aufzeichnung

**/API/WPR/customtrace (Post)**

Lädt ein WPR-Profil hoch und startet die Ablauf Verfolgung mithilfe des hochgeladenen Profils.

Nutz
* Mehrteilige konforme HTTP-Text

Rückgabe Daten
* Gibt den WPR-Sitzungsstatus zurück.

**/API/WPR/Status (Get)**

Ruft den Status der WPR-Sitzung ab.

Rückgabe Daten
* WPR-Sitzungs Status.

**/API/WPR/Trace (Get)**

Beendet eine WPR-Ablauf Verfolgungs Sitzung (Leistung).

Rückgabe Daten
* Gibt die ETL-Ablauf Verfolgungs Datei zurück.

**/API/WPR/Trace (Post)**

Startet eine Ablauf Verfolgungs Sitzung für WPR (Leistung).

Parameter
* Profil Profilname. Verfügbare Profile werden in "perfprofiles/Profiles. JSON" gespeichert.

Rückgabe Daten
* Beim Start wird der WPR-Sitzungs Status zurückgegeben.

## <a name="see-also"></a>Siehe auch
* [Verwenden des Windows-Geräteportals](using-the-windows-device-portal.md)
* [API-Referenz für den Geräte Portal (UWP)](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
