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
# <a name="mixed-reality-spatial-data-packager-documentation"></a><span data-ttu-id="666a6-104">Mixed Reality räumliche Daten-Manager-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="666a6-104">Mixed Reality Spatial Data Packager Documentation</span></span>

>[!NOTE]
> <span data-ttu-id="666a6-105">Dieses Tool und der Vorgang werden als angeboten – ist.</span><span class="sxs-lookup"><span data-stu-id="666a6-105">This tool and its operation are offered as-is.</span></span> <span data-ttu-id="666a6-106">Dabei handelt es sich vorbehalten ohne Benachrichtigung möglicherweise nicht kompatibel mit zukünftigen Windows oder Windows Mixed Reality HMD frei.</span><span class="sxs-lookup"><span data-stu-id="666a6-106">It is subject to change without any notice and may not be compatible with future Windows or Windows Mixed Reality HMD releases.</span></span>

## <a name="download"></a><span data-ttu-id="666a6-107">Herunterladen</span><span class="sxs-lookup"><span data-stu-id="666a6-107">Download</span></span>
 <span data-ttu-id="666a6-108">Herunterladen [MixedRealitySpatialDataPackager hier](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span><span class="sxs-lookup"><span data-stu-id="666a6-108">Download [MixedRealitySpatialDataPackager here](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span></span>

## <a name="quickstart"></a><span data-ttu-id="666a6-109">Schnellstart</span><span class="sxs-lookup"><span data-stu-id="666a6-109">Quickstart</span></span>

<span data-ttu-id="666a6-110">Das Mixed Reality räumliche Daten Packager-Tool kopiert die räumlichen Daten von einem Ziel-app von einem PC zu einem anderen über eine zwei Schritten exportieren und Importieren von Prozess.</span><span class="sxs-lookup"><span data-stu-id="666a6-110">The Mixed Reality Spatial Data Packager tool copies the spatial data of a target app from one PC to another through a two step export and import process.</span></span> <span data-ttu-id="666a6-111">Das Tool muss mit Administratorrechten ausgeführt werden, und löscht die vorhandenen räumlichen Daten beim Import.</span><span class="sxs-lookup"><span data-stu-id="666a6-111">The tool must be run with administrator privileges and deletes the existing spatial data on import.</span></span> <span data-ttu-id="666a6-112">Export lässt sich die vorhandenen räumlichen Daten intakt.</span><span class="sxs-lookup"><span data-stu-id="666a6-112">Export leaves the existing spatial data intact.</span></span>

<span data-ttu-id="666a6-113">Wichtige Anforderungen und Einschränkungen:</span><span class="sxs-lookup"><span data-stu-id="666a6-113">Key requirements and limitations:</span></span>

1. <span data-ttu-id="666a6-114">Tool muss mit Administratorrechten ausgeführt werden</span><span class="sxs-lookup"><span data-stu-id="666a6-114">Tool must be run with administrator privileges</span></span> 
2. <span data-ttu-id="666a6-115">Möglicherweise müssen Sie den PC neu starten, wenn Mixed Reality-Portal instabil ist, nach dem Ausführen des Tools</span><span class="sxs-lookup"><span data-stu-id="666a6-115">You may have to restart PC if Mixed Reality Portal is unstable after running the tool</span></span>
3. <span data-ttu-id="666a6-116">Tool wird nicht ausgeführt werden, wenn Versionskonflikte, die räumliche Daten oder Inkompatibilitäten festgestellt.</span><span class="sxs-lookup"><span data-stu-id="666a6-116">Tool will not run when encountering spatial data version mismatches or incompatibilities</span></span>
4. <span data-ttu-id="666a6-117">Tools werden vorhandene räumliche Daten beim Import gelöscht.</span><span class="sxs-lookup"><span data-stu-id="666a6-117">Tool will erase existing spatial data on import</span></span>
5. <span data-ttu-id="666a6-118">Ausfall Importvorgang vorherigen können nicht Daten wiederhergestellt werden, wenn sie gesichert wurde, indem zuvor exportieren</span><span class="sxs-lookup"><span data-stu-id="666a6-118">If import process fails previous data cannot be restored unless it has been backed up by exporting previously</span></span>
6. <span data-ttu-id="666a6-119">Qualität der Importfunktion "Read-Only" Modus für räumliche Kartendaten abhängig</span><span class="sxs-lookup"><span data-stu-id="666a6-119">Quality of import functionality contingent on “Read-Only” mode for spatial map data</span></span>
***

## <a name="mapping-best-practices"></a><span data-ttu-id="666a6-120">Zuordnen von bewährten Methoden</span><span class="sxs-lookup"><span data-stu-id="666a6-120">Mapping Best Practices</span></span>

1. <span data-ttu-id="666a6-121">Löschen von Zuordnungen in der Systemsteuerung (Mixed Reality-Einstellungen > >-Umgebung löschen Umgebungsdaten ->)</span><span class="sxs-lookup"><span data-stu-id="666a6-121">Clear existing maps from the Control Panel (Settings -> Mixed Reality -> Environment -> Clear environment data)</span></span>
2. <span data-ttu-id="666a6-122">Stellen Sie sicher über ausreichende Beleuchtung für gute Überwachung, und wenn mit gesperrten Zuordnungsmodus versuchen, die die gleiche Beleuchtung verwalten</span><span class="sxs-lookup"><span data-stu-id="666a6-122">Ensure sufficient lighting for good tracking and if running locked map mode try to maintain the same lighting</span></span>
3. <span data-ttu-id="666a6-123">Wenn möglich gehalten Sie den dynamischen Bereich von Beleuchtung niedrig durch das Vermeiden der Bereiche der hohen Beleuchtung neben dunkle Bereiche Shadowing durchgeführt wurde</span><span class="sxs-lookup"><span data-stu-id="666a6-123">When possible keep the lighting dynamic range low by avoiding areas of high illumination next to dark, shadowed areas</span></span>
4. <span data-ttu-id="666a6-124">Minimieren Sie leere, textureless Flächen platzieren z. B. einen Bereich von verschiedenen Poster auf weißen Wände</span><span class="sxs-lookup"><span data-stu-id="666a6-124">Minimize blank, textureless surfaces e.g. place a range of different posters on white walls</span></span>
5. <span data-ttu-id="666a6-125">Ordnen Sie den Adressraum ohne dynamische Objekte in der Szene, wie das Verschieben von Personen</span><span class="sxs-lookup"><span data-stu-id="666a6-125">Map the space without dynamic objects in the scene such as moving people</span></span>
6. <span data-ttu-id="666a6-126">Sperren Sie die Zuordnung beim Import (verfügbar über Insider Preview)</span><span class="sxs-lookup"><span data-stu-id="666a6-126">Lock the map on import (available via Insider Preview)</span></span>
7. <span data-ttu-id="666a6-127">Entsperren Sie die Karte zu und Einlesen Sie die Umgebung neu, beim Nachverfolgen der Qualität beeinträchtigt wird, bzw. Änderungen in der Umgebung (Beleuchtung oder Änderungen in das Objektlayout) vorliegen.</span><span class="sxs-lookup"><span data-stu-id="666a6-127">Unlock the map and rescan the enviornment when tracking quality degrades and/or there are changes in the environment (lighting or changes in object layout)</span></span>
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a><span data-ttu-id="666a6-128">Ausgeführte Mixed Reality räumliche Daten Packager mit Begleiterskript</span><span class="sxs-lookup"><span data-stu-id="666a6-128">Running Mixed Reality Spatial Data Packager with Companion Script</span></span>

<span data-ttu-id="666a6-129">Wir haben MRSpatialPackagerHelperScript.ps1 bereitgestellt, die die Map-Objekt-Manager Tools ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="666a6-129">We have provided MRSpatialPackagerHelperScript.ps1 that runs the map packager the tools.</span></span> 


<span data-ttu-id="666a6-130">Die Skriptparameter sind unten definiert:</span><span class="sxs-lookup"><span data-stu-id="666a6-130">The script parameters are defined below:</span></span>

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

### <a name="powershell-script-example-usage-and-output"></a><span data-ttu-id="666a6-131">Beispielsyntax für die PowerShell-Skript und die Ausgabe</span><span class="sxs-lookup"><span data-stu-id="666a6-131">Powershell Script Example Usage and Output</span></span>

<span data-ttu-id="666a6-132">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span><span class="sxs-lookup"><span data-stu-id="666a6-132">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span></span>
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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a><span data-ttu-id="666a6-133">Wie Sie mithilfe von MixedRealityPackager.exe Export</span><span class="sxs-lookup"><span data-stu-id="666a6-133">How to Export using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

<span data-ttu-id="666a6-134">Exportieren von Zuordnungen, die einem Gerät generiert zwei Mapx-Dateien, het.mapx und sa.mapx.</span><span class="sxs-lookup"><span data-stu-id="666a6-134">Exporting maps off device generates two mapx files, het.mapx and sa.mapx.</span></span> <span data-ttu-id="666a6-135">Während des Exportvorgangs werden alle räumlichen Anker mit Ausnahme der angegebenen app und die Grenze benutzererstellte entfernt (falls vorhanden).</span><span class="sxs-lookup"><span data-stu-id="666a6-135">During the export process all spatial anchors are removed except for the specified app and the user-created boundary (if it exists).</span></span> <span data-ttu-id="666a6-136">Den paketfamiliennamen für die Quelle muss eine vorhandene installierte app übereinstimmen, oder die EXE-Datei schlägt fehl.</span><span class="sxs-lookup"><span data-stu-id="666a6-136">The source package family name must match an existing installed app or the exe will fail.</span></span>

### <a name="how-to-import-using-mixedrealitypackagerexe"></a><span data-ttu-id="666a6-137">Wie Sie mithilfe von MixedRealityPackager.exe importieren</span><span class="sxs-lookup"><span data-stu-id="666a6-137">How to Import using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
<span data-ttu-id="666a6-138">Importieren, löscht die vorhandenen räumlichen Daten und ersetzt es durch die Daten im angegebenen Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="666a6-138">Import deletes the existing spatial data and replaces it with the data from the specified directory.</span></span> <span data-ttu-id="666a6-139">Die Eingabe der app-Name Gibt an, für der Paketnamen der die Ziel-app, die die räumlichen Anker wie importiert werden soll, und gibt an, die Zielbenutzer-SID für das der Benutzer, der Zugriff auf die importierten räumliche Anker haben sollen.</span><span class="sxs-lookup"><span data-stu-id="666a6-139">The app name input specifies the package name of the target app that like the spatial anchors should be imported for and the target user SID specifies the user that should have access to the imported spatial anchors.</span></span> <span data-ttu-id="666a6-140">Paketfamilienname Ziel und Benutzer-SIDs müssen vorhandene Werte in den PC übereinstimmen oder die EXE-Datei schlägt fehl.</span><span class="sxs-lookup"><span data-stu-id="666a6-140">The target package family name and user SIDs must match existing values on the PC or the exe will fail.</span></span>


***
## <a name="error-messages"></a><span data-ttu-id="666a6-141">Fehlermeldungen</span><span class="sxs-lookup"><span data-stu-id="666a6-141">Error Messages</span></span>
<span data-ttu-id="666a6-142">Darüber hinaus werden die Fehlermeldungen unten Fehler auch mit dem HRESULT begleitet</span><span class="sxs-lookup"><span data-stu-id="666a6-142">In addition the error messages below failures will also be accompanied with an HRESULT</span></span>

### <a name="if-there-was-an-error-invalid-arguments"></a><span data-ttu-id="666a6-143">Wenn ein Fehler wurden ungültige Argumente aufgetreten</span><span class="sxs-lookup"><span data-stu-id="666a6-143">If there was an error invalid arguments</span></span>
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a><span data-ttu-id="666a6-144">Wenn die ausführbare Datei nicht im Administratormodus ausgeführt wurde</span><span class="sxs-lookup"><span data-stu-id="666a6-144">If the executable was not run in administrator mode</span></span>
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a><span data-ttu-id="666a6-145">Wenn ein Fehler aktivieren oder deaktivieren den Treiber</span><span class="sxs-lookup"><span data-stu-id="666a6-145">If there was an error enabling or disabling the driver</span></span>
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a><span data-ttu-id="666a6-146">Wenn Fehler bei die spatial-Datenbank-Version überprüfen</span><span class="sxs-lookup"><span data-stu-id="666a6-146">If there was an error validating the spatial database version</span></span>
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a><span data-ttu-id="666a6-147">Wenn Fehler bei der Überprüfung den paketfamiliennamen für Ziel-Import/Export-app bereitgestellt</span><span class="sxs-lookup"><span data-stu-id="666a6-147">If there was an error validating the package family name provided for target import/export app</span></span>
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a><span data-ttu-id="666a6-148">Wenn Fehler bei der Überprüfung der Benutzers-SID</span><span class="sxs-lookup"><span data-stu-id="666a6-148">If there was an error validating the user SID</span></span>
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a><span data-ttu-id="666a6-149">Wenn gab es verknüpften Fehler an das Ziel oder die Quelle räumlicher Daten Dateien</span><span class="sxs-lookup"><span data-stu-id="666a6-149">If there was an error related to the destination or source spatial data files</span></span>
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stoping-spectrumsharedrealitysvc"></a><span data-ttu-id="666a6-150">Wenn ein Fehler im Zusammenhang mit der Start- und das Beenden des Spektrums/SharedRealitySvc</span><span class="sxs-lookup"><span data-stu-id="666a6-150">If there was an error related to starting and stoping Spectrum/SharedRealitySvc</span></span>
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
