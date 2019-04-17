---
title: App-Modell
description: Windows Mixed Reality verwendet das app-Modell, das von der universellen Windows-Plattform, ein Modell und die Umgebung für die moderne Windows-apps bereitgestellt.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: UWP-app-Modell, Lebenszyklus, anhalten, fortsetzen, Kachel, Ansichten und Verträge
ms.openlocfilehash: 5dc84122e591e7d91657b6f8eadf6eb947f2d706
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595856"
---
# <a name="app-model"></a>App-Modell

Windows Mixed Reality verwendet das app-Modell bereitgestellt wird, durch die [universelle Windows-Plattform](https://docs.microsoft.com/windows/uwp/get-started/) (UWP) können ein Modell und die Umgebung für die moderne Windows-apps. Das UWP-app-Modell definiert, wie apps installiert sind, aktualisiert, versioniert und sichere und vollständig entfernt. Es bestimmt, wie apps ausführen, den Energiesparmodus und beenden - Anwendungslebenszyklus und wie Zustand beibehalten werden kann. Hierin sind auch Integration sowie Interaktion mit dem Betriebssystem, Dateien und andere apps.

![Direct2D-apps in die Windows Mixed Reality Startseite in einem Bereich Frühstück angeordnet sind](images/20160112-055908-hololens-500px.jpg)<br>
*Apps mit einer 2D-Ansicht in die Windows Mixed Reality home angeordnet sind*

## <a name="app-lifecycle"></a>App-Lebenszyklus

Der Lebenszyklus einer mixed Reality-app umfasst die standard-app-Konzepten wie Platzierung, starten, beenden und entfernen.

### <a name="placement-is-launch"></a>Die Platzierung ist, starten

Jede app beginnt in mixed Reality, platzieren Sie eine app-Kachel (nur ein [Windows sekundäre Kachel](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile)) in der [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md). Diese app-Kacheln, startet auf Platzierung, die app ausgeführt wird. Diese app-Kacheln speichern und bleiben Sie in den Speicherort, wo sie platziert werden, fungiert wie Startprogramme jederzeit Sie zurück zur app abgerufen werden soll.

![Platzierung setzt eine sekundäre Kachel in der ganzen Welt](images/slide1-600px.png)<br>
*Platzierung setzt eine sekundäre Kachel in der ganzen Welt*

Sobald Platzierung abgeschlossen ist (es sei denn, die Platzierung von gestartet wurde. ein [app zu app](app-model.md#protocols) starten), die app gestartet wird, starten. Windows Mixed Reality können eine begrenzte Anzahl von apps auf einmal ausführen. Sobald Sie platzieren und eine app starten, möglicherweise andere aktive apps anhalten, einen Screenshot der letzte Zustand der app auf die Kachel der app zu verlassen, wo Sie sie platziert. Finden Sie unter [Windows 10-UWP-app-Lebenszyklus](https://docs.microsoft.com/windows/uwp/launch-resume/app-lifecycle) für Weitere Informationen zur Behandlung von "Resume" und andere Ereignisse zur app-Lebenszyklus.

![Nach dem Platzieren von einer Kachel, die app läuft](images/slide2-500px.png) ![Statusdiagramm für die app ausgeführt, angehalten oder nicht ausgeführt](images/ic576232-500px.png)<br>
*Links: nach dem Platzieren von einer Kachel, wird die app ausgeführt. Rechts: Statusdiagramm für die app ausgeführt, angehalten oder wird nicht ausgeführt werden.*

### <a name="remove-is-closeterminate-process"></a>Remove ist Prozess beenden schließen

Wenn Sie eine platzierten app-Kachel aus der Welt entfernen, wird die zugrunde liegenden Prozesse geschlossen. Dies kann hilfreich, um sicherzustellen, dass Ihre app beendet wird oder eine problematische Anwendung neu zu starten sein.

### <a name="app-suspensiontermination"></a>App Suspension bzw. der Beendigung

In der [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md), der Benutzer kann mehrere Einstiegspunkte für eine app zu erstellen. Hierfür wird das Starten der app über das Startmenü, und platzieren die app-Kachel in der ganzen Welt. Jede Kachel der app verhält sich wie einem anderen Einstiegspunkt und verfügt über eine separate Kachel-Instanz im System. Eine Abfrage für [SecondaryTile.FindAllAsync](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync) führt zu einem **"secondarytile"** für jede app-Instanz.

Wenn es sich bei eine UWP-app anhält, wird ein Screenshot des aktuellen Zustands erstellt.

![Screenshots werden für angehaltene apps angezeigt.](images/slide9-800px.png)<br>
*Screenshots werden für angehaltene apps angezeigt.*

Ein wichtiger Unterschied zu anderen Windows 10-Shells ist wie die app über eine Aktivierung des app-Instanz über informiert ist die [CoreApplication.Resuming](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming) und [CoreWindow.Activated](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated) Ereignisse.

|  Szenario |  Fortsetzen  |  Aktiviert | 
|----------|----------|----------|
|  Starten Sie die neue Instanz der app über das Startmenü  |   |  **Aktiviert** mit einem neuen [TileId](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) | 
|  Starten Sie die zweite Instanz der app über das Startmenü  |   |  **Aktiviert** mit einem neuen **TileId** | 
|  Wählen Sie die Instanz der app, die nicht derzeit aktiv ist  |   |  **Aktiviert** mit der **TileId** der Instanz zugeordnet | 
|  Wählen Sie eine andere app und dann die zuvor aktive Instanz  |  **Fortsetzen von** ausgelöst  |  | 
|  Wählen Sie eine andere app und dann die Instanz, die zuvor nicht aktiv war  |  **Fortsetzen von** ausgelöst  |  Klicken Sie dann **Activated** mit der **TileId** der Instanz zugeordnet | 

### <a name="extended-execution"></a>Erweiterte Ausführung

Manchmal muss Ihre app weiter im Hintergrund ausführen oder die Wiedergabe von Audiodaten. [Hintergrundaufgaben](https://docs.microsoft.com/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest) HoloLens verfügbar sind.

![Apps können im Hintergrund ausgeführt.](images/slide10-800px.png)<br>
*Apps können im Hintergrund ausgeführt.*

## <a name="app-views"></a>App-Ansichten

Wenn Ihre app aktiviert, können Sie auswählen, welche Art von Ansicht Sie anzeigen möchten. Für einer app **"coreapplication"**, es ist immer ein primären [app-Ansicht](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationView) und eine beliebige Anzahl von weiteren app-Ansichten, die Sie erstellen möchten. Auf Desktop können Sie eine app-Ansicht als Fenster vorstellen. Unsere mixed Reality-app-Vorlagen erstellen Sie ein Unity-Projekt, in die primären app-Ansicht ist [immersive](app-views.md). 

Ihre app kann eine zusätzliche Direct2D-app-Ansicht, die mithilfe der Technologie wie XAML, zur Verwendung von Windows 10-Features wie z. B. in app-Käufe erstellen. Wenn Ihre app als UWP-app für andere Windows 10-Geräte gestartet, eine Primäransicht ist, 2D, aber Sie können "aufleuchten" in mixed Reality durch Hinzufügen einer zusätzlichen app-Ansicht, die faszinierende Anwendungsperformance volumetrically angezeigt wird. Stellen Sie sich, eine Foto-Viewer-app in XAML, in dem die Schaltfläche "Slideshow" zu einer umfassenden app-Ansicht gewechselt, die Fotos aus der app in der ganzen Welt und Oberflächen flog, erstellen.

![Die ausgeführte app kann eine 2D-Ansicht oder eine immersive Ansicht verfügen.](images/slide3-800px.png)<br>
*Die ausgeführte app kann eine 2D-Ansicht oder eine immersive Ansicht verfügen.*

### <a name="creating-an-immersive-view"></a>Erstellen einer immersiven-Ansicht

Mixed Reality-apps sind diejenigen, die eine immersive Ansicht, die erstellen mit erfolgt die [HolographicSpace](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace) Typ.

Eine app, die ausschließlich immersive sollten immer beim Start eine immersive Ansicht erstellen, auch wenn auf dem Desktop gestartet. Immersive Ansichten werden immer in den Kopfhörer, unabhängig von dem sie erstellt wurden. Aktiviert eine immersive Ansicht zeigt das Mixed Reality-Portal und führen den Benutzer auf ihre Kopfhörer.

Eine app, die mit einer 2D-Ansicht auf dem desktop beginnt möglicherweise eine sekundäre immersive Ansicht zum Anzeigen der Inhalte in den Kopfhörer erstellen. Ein Beispiel hierfür ist ein 2D-Edge-Fenster auf dem Überwachungsserver ein 360-Grad-Video in die Kopfhörer anzeigt.

![Apps, die im immersive Ansicht sind die einzige sichtbar](images/slide4-800px.png)<br>
*Eine app, die Ausführung in eine immersive Ansicht ist die einzige, der sichtbar*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>2D-Ansicht in die Windows Mixed Reality home

Etwas anderes als eine faszinierende Ansicht gerendert wird als eine 2D-Ansicht in Ihrer Umgebung.

Eine app möglicherweise 2D Ansichten, die auf dem desktop überwachen und in den Kopfhörer. Beachten Sie, dass eine neue 2D-Ansicht in der gleichen Shell wie die Sicht platziert werden, die sie entweder auf dem Bildschirm oder in den Kopfhörer erstellt. Es ist nicht aktuell möglich, für eine app oder einen Benutzer eine 2D-Ansicht zwischen dem Mixed Reality-Startseite und der Monitor zu verschieben.

![Apps, die im 2D-Ansicht freigeben den Speicherplatz in der gemischten Welt mit anderen apps](images/slide5-800px.png)<br>
*Apps, die in einer Freigabe 2D-Ansicht den Speicherplatz mit anderen apps*

### <a name="placement-of-additional-app-tiles"></a>Platzierung von zusätzlichen app-Kacheln

Sie können platzieren, wie viele apps mit einer 2D-Texturmap. in Ihrer Umgebung anzeigen, dabei die [sekundären Kachel APIs](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles). Diese Kacheln "angehefteten" werden als Splash-Screens angezeigt, die Benutzer platzieren müssen und dann später Sie Ihre app zu starten können. Windows Mixed Reality unterstützt derzeit nicht das Rendern von 2D-Kachel Inhalte als live-Kacheln.

![Apps können mehrere Platzierungen Verwendung sekundärer Kacheln haben.](images/slide6-800px.png)<br>
*Apps können mehrere Platzierungen Verwendung sekundärer Kacheln haben.*

### <a name="switching-views"></a>Ansicht wechseln

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>Der Wechsel von der 2D-XAML-Ansicht für die immersiven Ansicht

Wenn die app, XAML, und klicken Sie dann auf die XAML verwendet [IFrameworkViewSource](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkviewsource) wird die erste Ansicht der app steuern. Die app muss so wechseln Sie zur immersive Ansicht vor dem Aktivieren der **"corewindow"**, um sicherzustellen, dass die app gestartet wird, direkt in die Materie einzusteigen.

Verwendung [CoreApplication.CreateNewView](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_) und [ApplicationViewSwitcher.SwitchAsync](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_) auf die aktive Ansicht zu vereinfachen.

> [!NOTE]
>* Geben Sie nicht die [ApplicationViewSwitchingOptions.ConsolidateViews](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions) flag **SwitchAsync** beim Wechsel von der XAML-Ansicht zu der immersive Ansicht oder das Slate-Objekt, das die app gestartet wird entfernt aus der ganzen Welt.
>* **SwitchAsync** aufgerufen werden soll, mithilfe der [Dispatcher](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher) der Ansicht, die Sie in einfügen zugeordnet.
>* Sie müssen **SwitchAsync** zurück an die XAML-Ansicht bei Bedarf zum Starten einer virtuellen Tastatur oder einer anderen Anwendung aktivieren möchten.

![Apps können zwischen 2D und immersive Ansichten wechseln](images/slide7-600px.png) ![Wenn eine app in eine immersive Ansicht wechselt, der gemischten Welt und andere apps nicht mehr angezeigt](images/slide8-600px.png)<br>
*Links: apps können zwischen 2D und immersive Ansicht wechseln. Rechts: Wenn eine app in eine immersive Ansicht wechselt, werden die Windows Mixed Reality-Startseite und andere apps ausgeblendet.*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>Wechseln von der immersive Ansicht wieder zu einer Tastatur XAML-Ansicht

Ein häufiger Grund für die hin und her wechseln, zwischen Ansichten ist eine Tastatur in mixed Reality-app angezeigt. Die Shell ist nur die Systemtastatur anzeigen, wenn die app eine Direct2D-Ansicht angezeigt werden. Wenn die app zum Abrufen der Texteingabe muss, möglicherweise Geben Sie eine benutzerdefinierte XAML-Ansicht mit einem Text-Eingabefeld, wechseln Sie zu diesem und wechseln Sie dann nach die Eingabe abgeschlossen ist.

Wie im vorherigen Abschnitt, das Sie verwenden können **ApplicationViewSwitcher.SwitchAsync** für den Übergang zurück zu einer XAML-Ansicht von Ihrer immersive Ansicht.

## <a name="app-size"></a>App-Größe

Direct2D-app-Ansichten werden immer in einer festen virtuellen Slate-Objekt angezeigt. Dadurch werden alle 2D Ansichten, die genaue gleiche Menge an Inhalt anzuzeigen. Hier sind einige weitere Details zur Größe der 2D-Ansicht Ihrer app:
* Das Seitenverhältnis der app wird beim Ändern der Größe beibehalten.
* App [Auflösung und Skalierung Faktor](building-2d-apps.md#2d-app-view-resolution-and-scale-factor) werden durch Ändern der Größe nicht geändert.
* Apps sind nicht die tatsächliche Größe in der ganzen Welt Abfragen können.

![Direct2D-apps werden mit festen Fenstergrößen angezeigt.](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*Apps mit einer 2D-Ansicht werden mit festen Fenstergrößen angezeigt.*

## <a name="app-tiles"></a>App-Kacheln

Im Startmenü verwendet die standardkachel für kleine und mittelgroße Kachel für Pins und **alle Apps** Liste in mixed Reality. 

![Klicken Sie im Menü Start für Windows Mixed Reality](images/start-500px.png)<br>
*Klicken Sie im Menü Start für Windows Mixed Reality*

## <a name="app-to-app-interactions"></a>App für app-Interaktionen

Wie Sie apps erstellen, haben Sie Zugriff auf die umfangreichen app zu app Kommunikationsmechanismen verfügbar unter Windows 10. Perfekt funktionieren viele der neuen Protokoll-APIs und Datei-Registrierungen für HoloLens, um die app wird gestartet und die Kommunikation zu ermöglichen. 

Beachten Sie, dass für desktop Headsets, die app verknüpft ist, mit der angegebenen Dateierweiterung Protokoll möglicherweise eine Win32-app, die nur auf dem desktop oder in der desktop Slate-Objekt angezeigt werden kann.

### <a name="protocols"></a>Protokolle

HoloLens unterstützt die app zu app-Start über die [Windows.System.Launcher APIs](https://docs.microsoft.com/uwp/api/Windows.System.Launcher).

Es gibt einige Punkte beachtet werden, wenn eine andere Anwendung zu starten:

* Bei Start ein nicht modalen, z. B. Aktionen [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_), die Benutzer muss die app vor der Interaktion mit platzieren.

* Wenn eine modale starten, z. B. über durchführen [LaunchUriForResultsAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_), die modale app befindet sich über dem Fenster.

* Windows Mixed Reality können keine Anwendungen basierend auf exklusive Sichten überlagern. Um die gestartete app anzuzeigen, akzeptiert Windows den Benutzer zurück auf der ganzen Welt, um die Anwendung anzuzeigen.

### <a name="file-pickers"></a>Datei dateiöffnungs-

HoloLens unterstützt beide [FileOpenPicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileOpenPicker) und [FileSavePicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) Verträge. Allerdings ist keine app vorinstalliert, die den Verträgen für die Dateiauswahl erfüllt. Diese apps – z. B. OneDrive – können aus dem Microsoft Store installiert werden.

Wenn Sie mehr als eine Datei Picker-app installiert haben, werden Sie Benutzeroberfläche zur begriffserklärung treffen nicht angezeigt, für die Auswahl der app zu starten; Stattdessen wird die erste Dateiauswahl installiert ausgewählt. Wenn Sie eine Datei zu speichern, wird der Dateiname generiert enthält den Zeitstempel. Dies kann nicht vom Benutzer geändert werden.

Standardmäßig werden die folgenden Erweiterungen lokal unterstützt:

|  App  |  Extensions | 
|----------|----------|
|  Fotos  |  bmp, gif, jpg, png, avi, mov, mp4, wmv | 
|  Microsoft Edge  |  htm, html, pdf, svg, xml | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>App-Verträge und-Erweiterungen für Windows Mixed Reality

App-Verträge und Erweiterungspunkte können Sie zum Registrieren Ihrer app um tiefere Betriebssystemfunktionen, wie eine Dateierweiterung Ausnahmebehandlung oder bei Verwenden von Hintergrundtasks nutzen. Dies ist eine Liste der unterstützten und nicht unterstützten Verträge und Erweiterungspunkte für HoloLens.

|  Vertrag oder eine Erweiterung  |  Unterstützt? | 
|----------|----------|
| [Kontobildanbieter (Durchwahl)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#account_picture_provider) | Nicht unterstützt | 
| [Alarm](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#alarm) | Nicht unterstützt | 
| [App service](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#app_service) | Unterstützt, aber nicht voll funktionsfähig | 
| [Terminanbieter](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#appointmnets_provider) | Nicht unterstützt | 
| [Automatische Wiedergabe (Durchwahl)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#autoplay) | Nicht unterstützt | 
| [Aufgaben im Hintergrund (Durchwahl)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#background_tasts) | Teilweise unterstützt (nicht alle Vorgänge für Trigger) | 
| [Update-Vorgang (Durchwahl)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#update_task) | Unterstützt | 
| [Zwischengespeicherte Datei Updater-Vertrag](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#cached_file_updater) | Unterstützt | 
| [Kameraeinstellungen (Durchwahl)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#camera_settings) | Nicht unterstützt | 
| [Wählprotokoll](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#dial_protocol) | Nicht unterstützt | 
| [Datei-Aktivierung (Durchwahl)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_activation) | Unterstützt | 
| [Dateiauswahlvertrag zum Öffnen](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_open_picker_contract) | Unterstützt | 
| [Dateispeicherungsauswahl-Vertrag](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_save_picker_contract) | Unterstützt | 
| [Aufruf der Sperre-Bildschirm](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#lock_screen_call) | Nicht unterstützt | 
| [Medienwiedergabe](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#media_playback) | Nicht unterstützt | 
| [Wiedergeben auf Vertrag](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#playto_contract) | Nicht unterstützt | 
| [Vorinstallierte Konfiguration-Aufgabe](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#preinstalled_config_task) | Nicht unterstützt | 
| [3D-Workflow drucken](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_3d_workflow) | Unterstützt | 
| [(Durchwahl) Einstellungen für Druckaufgaben](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_task_settings) | Nicht unterstützt | 
| [URI-Aktivierung (Durchwahl)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#protocol_activation) | Unterstützt | 
| [Eingeschränkter Start](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#restricted_launch) | Nicht unterstützt | 
| [Search-Vertrag](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#search_contract) | Nicht unterstützt | 
| [Einstellungen für contract](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#settings_contract) | Nicht unterstützt | 
| [Freigabevertrag](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#share_contract) | Nicht unterstützt | 
| [SSL-Zertifikate (Durchwahl)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#ssl_certificates) | Unterstützt | 
| [Webkontoanbieter](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#web_account_provider) | Unterstützt | 

## <a name="app-file-storage"></a>App-Dateispeicher

Alle Storage erfolgt über die [Windows.Storage-Namespace](https://docs.microsoft.com/uwp/api/Windows.Storage). Finden Sie die folgende Dokumentation für weitere Details. HoloLens unterstützt app Storage Sync/roaming nicht.

* [Dateien, Ordner und Bibliotheken](https://docs.microsoft.com/windows/uwp/files/index)
* [Speichern und Abrufen von Einstellungen und anderen App-Daten](https://docs.microsoft.com/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>Bekannte Ordner

Finden Sie unter [KnownFolders](https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders) die vollständigen Details für UWP-apps.

<table>
<tr>
<th> Eigenschaft</th><th> Für HoloLens unterstützt</th><th> Für immersive Headsets unterstützt</th><th> Beschreibung</th>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">AppCaptures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft den Ordner App erfasst.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">CameraRoll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft die im Ordner Eigene Aufnahmen ab.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">DocumentsLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft die Bibliothek Dokumente ab. Die Bibliothek Dokumente ist nicht zur allgemeinen Verwendung vorgesehen.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">"Musikbibliothek"</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft die Musikbibliothek ab.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft die 3D Ordner "Objects" ab.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">PicturesLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft die Bibliothek "Bilder" ab.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">Wiedergabelisten</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft die Play-Listen-Ordner ab.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">SavedPictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft den Ordner Bilder gespeichert.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">VideosLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft die Bibliothek "Videos" ab.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">HomeGroup</a></td><td></td><td style="text-align: center;">✔️</td><td>Ruft den Ordner "Heimnetzgruppe" ab.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">MediaServerDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Ruft den Ordner der Medien (Digital Living Network Alliance (DLNA))-Servergeräten ab.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">RecordedCalls</a></td><td></td><td style="text-align: center;">✔️</td><td>Ruft den Ordner mit aufgezeichneten anrufen.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Ruft den Wechselmedien-Ordner ab.</td>
</tr>
</table>

## <a name="app-package"></a>App-Paket

Mit Windows 10 Sie nicht mehr als Ziel ein Betriebssystems sondern [Ziel Ihrer app an eine oder mehrere gerätefamilien](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide#device-families). Eine Gerätefamilie identifiziert die APIs, Systemmerkmale und Verhaltensweisen, die Sie auf allen Geräten innerhalb der Gerätefamilie erwarten können. Es bestimmt auch, die Gruppe von Geräten, auf denen Ihre app installiert werden kann, aus, der [Microsoft Store](submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families).

* Um sowohl desktop Headsets und HoloLens Ziel festzulegen, als Ziel Ihrer app für die **Windows.Universal** -Gerätefamilie konzipiert.
* Um desktopoptimierung Headsets Ziel festzulegen, als Ziel Ihrer app für die **Windows.Desktop** -Gerätefamilie konzipiert.
* Um nur die HoloLens Ziel festzulegen, als Ziel Ihrer app für die **Windows.Holographic** -Gerätefamilie konzipiert.

## <a name="see-also"></a>Siehe auch

* [App-Ansichten](app-views.md)
* [Aktualisieren von 2D UWP-apps für mixed reality](building-2d-apps.md)
* [Leitfaden zum Entwerfen von 3D app-Startfeld](3d-app-launcher-design-guidance.md)
* [Implementieren von 3D app-startfeldern](implementing-3d-app-launchers.md)
