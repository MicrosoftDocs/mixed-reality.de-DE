---
title: Dokumentation für die gemischte Realität Spatial Data Packager
description: Dokumentation zur Verwendung von Mixed Reality Spatial Data Packager
author: alfred-msft
ms.author: yuripek
ms.date: 05/16/2019
ms.topic: article
keywords: LBE, MixedRealitySpatialDataPackager.exe, mixedrealityspatialdatapackager
ms.openlocfilehash: 4a285cbd7423d7cacaf52370e6e19acf42672289
ms.sourcegitcommit: cfca6cb016d8683fa2c611a97d493a4947935dbb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86402739"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a>Dokumentation für die gemischte Realität Spatial Data Packager

>[!NOTE]
> Dieses Tool und der zugehörige Vorgang werden unverändert angeboten. Er kann ohne vorherige Ankündigung geändert werden und ist möglicherweise nicht mit zukünftigen Windows-oder Windows Mixed Reality-HMD-Releases kompatibel.

## <a name="download"></a>Herunterladen
 [Mixedrealityspatialdatapackager hier](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip) herunterladen

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>In Mixed Reality räumlicher Daten Packager</td>
        <td>❌</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="quickstart"></a>Schnellstart

Mit dem Mixed Reality Spatial Data Packager-Tool werden die räumlichen Daten einer Ziel-App über einen zweistufigen Export-und Importprozess von einem PC auf einen anderen kopiert. Das Tool muss mit Administratorrechten ausgeführt werden und die vorhandenen räumlichen Daten beim Importieren löschen. Beim Export bleiben die vorhandenen räumlichen Daten intakt.

Wichtige Anforderungen und Einschränkungen:

1. Das Tool muss mit Administratorrechten ausgeführt werden. 
2. Möglicherweise müssen Sie den PC neu starten, wenn das gemischte Reality-Portal nach dem Ausführen des Tools instabil ist.
3. Das Tool wird nicht ausgeführt, wenn nicht übereinstimmende oder Inkompatibilitäten auf räumliche Daten stoßen.
4. Das Tool löscht vorhandene räumliche Daten beim Importieren.
5. Wenn der Import Vorgang fehlschlägt, können vorherige Daten nicht wieder hergestellt werden, es sei denn, Sie wurden durch Exportieren zuvor
6. Qualität der Import Funktionalität abhängig vom schreibgeschützten Modus für räumliche Kartendaten
***

## <a name="mapping-best-practices"></a>Bewährte Methoden für die Zuordnung

1. Löschen vorhandener Zuordnungen in der Systemsteuerung (Einstellungen-> gemischte Realität > Umgebung > Löschen von Umgebungs Daten)
2. Gewährleisten einer ausreichenden Beleuchtung für eine gute Nachverfolgung und beim Ausführen eines gesperrten Zuordnungs Modus versuchen, die gleiche Beleuchtung aufrechtzuerhalten
3. Wenn möglich, sollten Sie den dynamischen Bereich der Beleuchtung gering halten, indem Sie Bereiche mit hoher Beleuchtung neben dunklen, Shadowing enden Bereichen vermeiden.
4. Minimieren Sie leere, textulose Oberflächen, z. b. einen Bereich verschiedener Poster auf weißen Wänden platzieren.
5. Ordnen Sie den Raum ohne dynamische Objekte in der Szene zu
6. Karte beim Import Sperren (verfügbar über Insider Preview)
7. Entsperren Sie die Zuordnung, und Scannen Sie die Umgebung neu, wenn die nach Verfolgungs Qualität abnimmt und/oder Änderungen in der Umgebung vorliegen (Beleuchtung oder Änderungen im Objekt Layout).
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a>Ausführen von Mixed Reality Spatial Data Packager mit begleitenden Skripts

Wir haben MRSpatialPackagerHelperScript.ps1 bereitgestellt, die den Map-Packager die Tools ausführt. 


Die Skript Parameter sind unten definiert:

```
-AppName <String>
    On export: The spatial anchors from the app of interest
    On import: The target app that spatial anchors should be imported for
    Returns a list of apps containing the input string if a unique app is not found

-UserName <String>
    Target username, will return a list of users if a unique match is not found

-Mode <String>
    import or export

-MapxPath <String>
    On export: Directory to export your mapx files
    On import: Directory where import mapx are stored

-LockMap <Int32>
    0 to unlock map
    1 to lock map

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a>PowerShell-Skript Beispiel Verwendung und-Ausgabe

.\MRSpatialPackagerHelperScript.ps1-appname holoshell-username Administrator Modus Export-mapxpath d:\temp\-lockmap 0
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value successfully set to 0

Running: C:\bin\MixedRealitySpatialDataPackager.exe export D:\temp\ HoloShell_cw5n1h2txyewy S-1-5-21-1279937937-3984375698-1043392598-499

Attempting to disable Windows MR driver
Driver disabled
Validating spatial data version information...
Device spatial data version OK
External spatial data version OK
Importing spatial anchors for user account phguan
Stopping SPECTRUM
Stopped SPECTRUM
Stopping SHAREDREALITYSVC
Stopped SHAREDREALITYSVC
Space ID is {00000000-4321-0000-0000-000000000000}
SUCCESS: Unpacked Space from D:\temp\map\het.mapx to
C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors\{00000000-4321-0000-0000-000000000000}\
Space ID is {78FA06B5-4416-4815-BB00-B3CB5C983B7D}
SUCCESS: Unpacked Space from D:\temp\map\sa.mapx to
C:\ProgramData\Microsoft\Spectrum\PersistedSpatialAnchors\
Attempting to enable Windows MR driver
Driver enabled
Starting SHAREDREALITYSVC
Started SHAREDREALITYSVC
Starting SPECTRUM
Started SPECTRUM
IMPORT SUCCESS
```

### <a name="how-to-export-using-mixedrealityspatialdatapackagerexe"></a>Exportieren mithilfe MixedRealitySpatialDataPackager.exe
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

Beim Exportieren von Zuordnungen vom Gerät werden zwei MapX-Dateien generiert: "Het. MapX" und "SA. MapX" Während des Export Vorgangs werden alle räumlichen Anker außer der angegebenen app und der vom Benutzer erstellten Grenze (sofern vorhanden) entfernt. Der Name der Quellpaket Familie muss mit einer vorhandenen installierten App identisch sein, oder die exe-Datei schlägt fehl.

### <a name="how-to-import-using-mixedrealityspatialdatapackagerexe"></a>Importieren mit MixedRealitySpatialDataPackager.exe
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
Beim Importieren werden die vorhandenen räumlichen Daten gelöscht und durch die Daten aus dem angegebenen Verzeichnis ersetzt. Die App-namens Eingabe gibt den Paketnamen der Ziel-APP an, die für den räumlichen Anker importiert werden soll, und die Ziel Benutzer-SID gibt den Benutzer an, der Zugriff auf die importierten räumlichen Anker haben soll. Der Name und die Benutzer-SIDs des Ziel Pakets müssen mit den vorhandenen Werten auf dem PC abgeglichen werden, andernfalls tritt ein Fehler auf.


***
## <a name="error-messages"></a>Fehlermeldungen
Außerdem werden die Fehlermeldungen unter Fehler ebenfalls mit einem HRESULT verknüpft.

### <a name="if-there-was-an-error-invalid-arguments"></a>Wenn ein Fehler ungültige Argumente vorhanden ist
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a>Wenn die ausführbare Datei nicht im Administrator Modus ausgeführt wurde
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a>Wenn beim Aktivieren oder Deaktivieren des Treibers ein Fehler aufgetreten ist
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a>Wenn beim Validieren der Version der räumlichen Datenbank ein Fehler aufgetreten ist
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a>Wenn beim Überprüfen des für die Ziel Import/Export-App bereitgestellten Paket Familiennamens ein Fehler aufgetreten ist.
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a>Wenn beim Validieren der Benutzer-SID ein Fehler aufgetreten ist
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a>Wenn ein Fehler im Zusammenhang mit den räumlichen Datendateien des Ziels oder der Quelle aufgetreten ist
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stopping-spectrumsharedrealitysvc"></a>Bei einem Fehler im Zusammenhang mit dem Starten und Beenden von "Spectrum/sharedrealitysvc"
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
