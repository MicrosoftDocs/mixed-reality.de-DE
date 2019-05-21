---
title: Mixed Reality räumliche Daten-Manager-Dokumentation
description: Dokumentation für die Verwendung von Mixed Reality räumliche Daten Packager
author: alfred-msft
ms.author: alreynol
ms.date: 05/16/2019
ms.topic: article
keywords: lbe, MixedRealitySpatialDataPackager.exe, MixedRealitySpatialDataPackager
ms.openlocfilehash: 7ad1159af9eecd3ca3622dd25cc1f49fb0b1700a
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942106"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a>Mixed Reality räumliche Daten-Manager-Dokumentation

>[!NOTE]
> Dieses Tool und der Vorgang werden als angeboten – ist. Dabei handelt es sich vorbehalten ohne Benachrichtigung möglicherweise nicht kompatibel mit zukünftigen Windows oder Windows Mixed Reality HMD frei.

## <a name="download"></a>Herunterladen
 Herunterladen [MixedRealitySpatialDataPackager hier](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)

## <a name="quickstart"></a>Schnellstart

Das Mixed Reality räumliche Daten Packager-Tool kopiert die räumlichen Daten von einem Ziel-app von einem PC zu einem anderen über eine zwei Schritten exportieren und Importieren von Prozess. Das Tool muss mit Administratorrechten ausgeführt werden, und löscht die vorhandenen räumlichen Daten beim Import. Export lässt sich die vorhandenen räumlichen Daten intakt.

Wichtige Anforderungen und Einschränkungen:

1. Tool muss mit Administratorrechten ausgeführt werden 
2. Möglicherweise müssen Sie den PC neu starten, wenn Mixed Reality-Portal instabil ist, nach dem Ausführen des Tools
3. Tool wird nicht ausgeführt werden, wenn Versionskonflikte, die räumliche Daten oder Inkompatibilitäten festgestellt.
4. Tools werden vorhandene räumliche Daten beim Import gelöscht.
5. Ausfall Importvorgang vorherigen können nicht Daten wiederhergestellt werden, wenn sie gesichert wurde, indem zuvor exportieren
6. Qualität der Importfunktion "Read-Only" Modus für räumliche Kartendaten abhängig
***

## <a name="mapping-best-practices"></a>Zuordnen von bewährten Methoden

1. Löschen von Zuordnungen in der Systemsteuerung (Mixed Reality-Einstellungen > >-Umgebung löschen Umgebungsdaten ->)
2. Stellen Sie sicher über ausreichende Beleuchtung für gute Überwachung, und wenn mit gesperrten Zuordnungsmodus versuchen, die die gleiche Beleuchtung verwalten
3. Wenn möglich gehalten Sie den dynamischen Bereich von Beleuchtung niedrig durch das Vermeiden der Bereiche der hohen Beleuchtung neben dunkle Bereiche Shadowing durchgeführt wurde
4. Minimieren Sie leere, textureless Flächen platzieren z. B. einen Bereich von verschiedenen Poster auf weißen Wände
5. Ordnen Sie den Adressraum ohne dynamische Objekte in der Szene, wie das Verschieben von Personen
6. Sperren Sie die Zuordnung beim Import (verfügbar über Insider Preview)
7. Entsperren Sie die Karte zu und Einlesen Sie die Umgebung neu, beim Nachverfolgen der Qualität beeinträchtigt wird, bzw. Änderungen in der Umgebung (Beleuchtung oder Änderungen in das Objektlayout) vorliegen.
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a>Ausgeführte Mixed Reality räumliche Daten Packager mit Begleiterskript

Wir haben MRSpatialPackagerHelperScript.ps1 bereitgestellt, die die Map-Objekt-Manager Tools ausgeführt wird. 


Die Skriptparameter sind unten definiert:

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
    This functionality requires an updated driver from Insider Preview Builds with the Map Locking feature

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a>Beispielsyntax für die PowerShell-Skript und die Ausgabe

.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value succesfully set to 0

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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a>Wie Sie mithilfe von MixedRealityPackager.exe Export
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

Exportieren von Zuordnungen, die einem Gerät generiert zwei Mapx-Dateien, het.mapx und sa.mapx. Während des Exportvorgangs werden alle räumlichen Anker mit Ausnahme der angegebenen app und die Grenze benutzererstellte entfernt (falls vorhanden). Den paketfamiliennamen für die Quelle muss eine vorhandene installierte app übereinstimmen, oder die EXE-Datei schlägt fehl.

### <a name="how-to-import-using-mixedrealitypackagerexe"></a>Wie Sie mithilfe von MixedRealityPackager.exe importieren
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
Importieren, löscht die vorhandenen räumlichen Daten und ersetzt es durch die Daten im angegebenen Verzeichnis. Die Eingabe der app-Name Gibt an, für der Paketnamen der die Ziel-app, die die räumlichen Anker wie importiert werden soll, und gibt an, die Zielbenutzer-SID für das der Benutzer, der Zugriff auf die importierten räumliche Anker haben sollen. Paketfamilienname Ziel und Benutzer-SIDs müssen vorhandene Werte in den PC übereinstimmen oder die EXE-Datei schlägt fehl.


***
## <a name="error-messages"></a>Fehlermeldungen
Darüber hinaus werden die Fehlermeldungen unten Fehler auch mit dem HRESULT begleitet

### <a name="if-there-was-an-error-invalid-arguments"></a>Wenn ein Fehler wurden ungültige Argumente aufgetreten
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a>Wenn die ausführbare Datei nicht im Administratormodus ausgeführt wurde
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a>Wenn ein Fehler aktivieren oder deaktivieren den Treiber
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a>Wenn Fehler bei die spatial-Datenbank-Version überprüfen
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a>Wenn Fehler bei der Überprüfung den paketfamiliennamen für Ziel-Import/Export-app bereitgestellt
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a>Wenn Fehler bei der Überprüfung der Benutzers-SID
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a>Wenn gab es verknüpften Fehler an das Ziel oder die Quelle räumlicher Daten Dateien
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stoping-spectrumsharedrealitysvc"></a>Wenn ein Fehler im Zusammenhang mit der Start- und das Beenden des Spektrums/SharedRealitySvc
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
