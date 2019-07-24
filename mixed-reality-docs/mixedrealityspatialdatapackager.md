---
title: Dokumentation für die gemischte Realität Spatial Data Packager
description: Dokumentation zur Verwendung von Mixed Reality Spatial Data Packager
author: alfred-msft
ms.author: alreynol
ms.date: 05/16/2019
ms.topic: article
keywords: LBE, mixedrealityspatialdatapackager. exe, mixedrealityspatialdatapackager
ms.openlocfilehash: 7ad1159af9eecd3ca3622dd25cc1f49fb0b1700a
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942106"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a><span data-ttu-id="f4294-104">Dokumentation für die gemischte Realität Spatial Data Packager</span><span class="sxs-lookup"><span data-stu-id="f4294-104">Mixed Reality Spatial Data Packager Documentation</span></span>

>[!NOTE]
> <span data-ttu-id="f4294-105">Dieses Tool und der zugehörige Vorgang werden unverändert angeboten.</span><span class="sxs-lookup"><span data-stu-id="f4294-105">This tool and its operation are offered as-is.</span></span> <span data-ttu-id="f4294-106">Er kann ohne vorherige Ankündigung geändert werden und ist möglicherweise nicht mit zukünftigen Windows-oder Windows Mixed Reality-HMD-Releases kompatibel.</span><span class="sxs-lookup"><span data-stu-id="f4294-106">It is subject to change without any notice and may not be compatible with future Windows or Windows Mixed Reality HMD releases.</span></span>

## <a name="download"></a><span data-ttu-id="f4294-107">Herunterladen</span><span class="sxs-lookup"><span data-stu-id="f4294-107">Download</span></span>
 <span data-ttu-id="f4294-108">[Mixedrealityspatialdatapackager hier](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip) herunterladen</span><span class="sxs-lookup"><span data-stu-id="f4294-108">Download [MixedRealitySpatialDataPackager here](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span></span>

## <a name="quickstart"></a><span data-ttu-id="f4294-109">Schnellstart</span><span class="sxs-lookup"><span data-stu-id="f4294-109">Quickstart</span></span>

<span data-ttu-id="f4294-110">Mit dem Mixed Reality Spatial Data Packager-Tool werden die räumlichen Daten einer Ziel-App über einen zweistufigen Export-und Importprozess von einem PC auf einen anderen kopiert.</span><span class="sxs-lookup"><span data-stu-id="f4294-110">The Mixed Reality Spatial Data Packager tool copies the spatial data of a target app from one PC to another through a two step export and import process.</span></span> <span data-ttu-id="f4294-111">Das Tool muss mit Administratorrechten ausgeführt werden und die vorhandenen räumlichen Daten beim Importieren löschen.</span><span class="sxs-lookup"><span data-stu-id="f4294-111">The tool must be run with administrator privileges and deletes the existing spatial data on import.</span></span> <span data-ttu-id="f4294-112">Beim Export bleiben die vorhandenen räumlichen Daten intakt.</span><span class="sxs-lookup"><span data-stu-id="f4294-112">Export leaves the existing spatial data intact.</span></span>

<span data-ttu-id="f4294-113">Wichtige Anforderungen und Einschränkungen:</span><span class="sxs-lookup"><span data-stu-id="f4294-113">Key requirements and limitations:</span></span>

1. <span data-ttu-id="f4294-114">Das Tool muss mit Administratorrechten ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="f4294-114">Tool must be run with administrator privileges</span></span> 
2. <span data-ttu-id="f4294-115">Möglicherweise müssen Sie den PC neu starten, wenn das gemischte Reality-Portal nach dem Ausführen des Tools instabil ist.</span><span class="sxs-lookup"><span data-stu-id="f4294-115">You may have to restart PC if Mixed Reality Portal is unstable after running the tool</span></span>
3. <span data-ttu-id="f4294-116">Das Tool wird nicht ausgeführt, wenn nicht übereinstimmende oder Inkompatibilitäten auf räumliche Daten stoßen.</span><span class="sxs-lookup"><span data-stu-id="f4294-116">Tool will not run when encountering spatial data version mismatches or incompatibilities</span></span>
4. <span data-ttu-id="f4294-117">Das Tool löscht vorhandene räumliche Daten beim Importieren.</span><span class="sxs-lookup"><span data-stu-id="f4294-117">Tool will erase existing spatial data on import</span></span>
5. <span data-ttu-id="f4294-118">Wenn der Import Vorgang fehlschlägt, können vorherige Daten nicht wieder hergestellt werden, es sei denn, Sie wurden durch Exportieren zuvor</span><span class="sxs-lookup"><span data-stu-id="f4294-118">If import process fails previous data cannot be restored unless it has been backed up by exporting previously</span></span>
6. <span data-ttu-id="f4294-119">Qualität der Import Funktionalität abhängig vom schreibgeschützten Modus für räumliche Kartendaten</span><span class="sxs-lookup"><span data-stu-id="f4294-119">Quality of import functionality contingent on “Read-Only” mode for spatial map data</span></span>
***

## <a name="mapping-best-practices"></a><span data-ttu-id="f4294-120">Bewährte Methoden für die Zuordnung</span><span class="sxs-lookup"><span data-stu-id="f4294-120">Mapping Best Practices</span></span>

1. <span data-ttu-id="f4294-121">Löschen vorhandener Zuordnungen in der Systemsteuerung (Einstellungen-> Gemischte Realität > Umgebung > Löschen von Umgebungs Daten)</span><span class="sxs-lookup"><span data-stu-id="f4294-121">Clear existing maps from the Control Panel (Settings -> Mixed Reality -> Environment -> Clear environment data)</span></span>
2. <span data-ttu-id="f4294-122">Gewährleisten einer ausreichenden Beleuchtung für eine gute Nachverfolgung und beim Ausführen eines gesperrten Zuordnungs Modus versuchen, die gleiche Beleuchtung aufrechtzuerhalten</span><span class="sxs-lookup"><span data-stu-id="f4294-122">Ensure sufficient lighting for good tracking and if running locked map mode try to maintain the same lighting</span></span>
3. <span data-ttu-id="f4294-123">Wenn möglich, sollten Sie den dynamischen Bereich der Beleuchtung gering halten, indem Sie Bereiche mit hoher Beleuchtung neben dunklen, Shadowing enden Bereichen vermeiden.</span><span class="sxs-lookup"><span data-stu-id="f4294-123">When possible keep the lighting dynamic range low by avoiding areas of high illumination next to dark, shadowed areas</span></span>
4. <span data-ttu-id="f4294-124">Minimieren Sie leere, textulose Oberflächen, z. b. einen Bereich verschiedener Poster auf weißen Wänden platzieren.</span><span class="sxs-lookup"><span data-stu-id="f4294-124">Minimize blank, textureless surfaces e.g. place a range of different posters on white walls</span></span>
5. <span data-ttu-id="f4294-125">Ordnen Sie den Raum ohne dynamische Objekte in der Szene zu</span><span class="sxs-lookup"><span data-stu-id="f4294-125">Map the space without dynamic objects in the scene such as moving people</span></span>
6. <span data-ttu-id="f4294-126">Karte beim Import Sperren (verfügbar über Insider Preview)</span><span class="sxs-lookup"><span data-stu-id="f4294-126">Lock the map on import (available via Insider Preview)</span></span>
7. <span data-ttu-id="f4294-127">Entsperren Sie die Zuordnung, und Scannen Sie die Umgebung neu, wenn die nach Verfolgungs Qualität abnimmt und/oder Änderungen in der Umgebung vorliegen (Beleuchtung oder Änderungen im Objekt Layout).</span><span class="sxs-lookup"><span data-stu-id="f4294-127">Unlock the map and rescan the enviornment when tracking quality degrades and/or there are changes in the environment (lighting or changes in object layout)</span></span>
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a><span data-ttu-id="f4294-128">Ausführen von Mixed Reality Spatial Data Packager mit begleitenden Skripts</span><span class="sxs-lookup"><span data-stu-id="f4294-128">Running Mixed Reality Spatial Data Packager with Companion Script</span></span>

<span data-ttu-id="f4294-129">Wir haben mrspatialpackagerhelperscript. ps1 bereitgestellt, das den Map Packager die Tools ausführt.</span><span class="sxs-lookup"><span data-stu-id="f4294-129">We have provided MRSpatialPackagerHelperScript.ps1 that runs the map packager the tools.</span></span> 


<span data-ttu-id="f4294-130">Die Skript Parameter sind unten definiert:</span><span class="sxs-lookup"><span data-stu-id="f4294-130">The script parameters are defined below:</span></span>

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

### <a name="powershell-script-example-usage-and-output"></a><span data-ttu-id="f4294-131">PowerShell-Skript Beispiel Verwendung und-Ausgabe</span><span class="sxs-lookup"><span data-stu-id="f4294-131">Powershell Script Example Usage and Output</span></span>

<span data-ttu-id="f4294-132">.\Mrspatialpackagerhelperscript.ps1-appname holoshell-username Administrator Modus Export-mapxpath d:\temp\-lockmap 0</span><span class="sxs-lookup"><span data-stu-id="f4294-132">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span></span>
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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a><span data-ttu-id="f4294-133">Exportieren mithilfe von "mixedrealitypackager. exe"</span><span class="sxs-lookup"><span data-stu-id="f4294-133">How to Export using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

<span data-ttu-id="f4294-134">Beim Exportieren von Zuordnungen vom Gerät werden zwei MapX-Dateien generiert: "Het. MapX" und "SA. MapX"</span><span class="sxs-lookup"><span data-stu-id="f4294-134">Exporting maps off device generates two mapx files, het.mapx and sa.mapx.</span></span> <span data-ttu-id="f4294-135">Während des Export Vorgangs werden alle räumlichen Anker außer der angegebenen app und der vom Benutzer erstellten Grenze (sofern vorhanden) entfernt.</span><span class="sxs-lookup"><span data-stu-id="f4294-135">During the export process all spatial anchors are removed except for the specified app and the user-created boundary (if it exists).</span></span> <span data-ttu-id="f4294-136">Der Name der Quellpaket Familie muss mit einer vorhandenen installierten App identisch sein, oder die exe-Datei schlägt fehl.</span><span class="sxs-lookup"><span data-stu-id="f4294-136">The source package family name must match an existing installed app or the exe will fail.</span></span>

### <a name="how-to-import-using-mixedrealitypackagerexe"></a><span data-ttu-id="f4294-137">Importieren mithilfe von "mixedrealitypackager. exe"</span><span class="sxs-lookup"><span data-stu-id="f4294-137">How to Import using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
<span data-ttu-id="f4294-138">Beim Importieren werden die vorhandenen räumlichen Daten gelöscht und durch die Daten aus dem angegebenen Verzeichnis ersetzt.</span><span class="sxs-lookup"><span data-stu-id="f4294-138">Import deletes the existing spatial data and replaces it with the data from the specified directory.</span></span> <span data-ttu-id="f4294-139">Die App-namens Eingabe gibt den Paketnamen der Ziel-APP an, die für den räumlichen Anker importiert werden soll, und die Ziel Benutzer-SID gibt den Benutzer an, der Zugriff auf die importierten räumlichen Anker haben soll.</span><span class="sxs-lookup"><span data-stu-id="f4294-139">The app name input specifies the package name of the target app that like the spatial anchors should be imported for and the target user SID specifies the user that should have access to the imported spatial anchors.</span></span> <span data-ttu-id="f4294-140">Der Name und die Benutzer-SIDs des Ziel Pakets müssen mit den vorhandenen Werten auf dem PC abgeglichen werden, andernfalls tritt ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="f4294-140">The target package family name and user SIDs must match existing values on the PC or the exe will fail.</span></span>


***
## <a name="error-messages"></a><span data-ttu-id="f4294-141">Fehlermeldungen</span><span class="sxs-lookup"><span data-stu-id="f4294-141">Error Messages</span></span>
<span data-ttu-id="f4294-142">Außerdem werden die Fehlermeldungen unter Fehler ebenfalls mit einem HRESULT verknüpft.</span><span class="sxs-lookup"><span data-stu-id="f4294-142">In addition the error messages below failures will also be accompanied with an HRESULT</span></span>

### <a name="if-there-was-an-error-invalid-arguments"></a><span data-ttu-id="f4294-143">Wenn ein Fehler ungültige Argumente vorhanden ist</span><span class="sxs-lookup"><span data-stu-id="f4294-143">If there was an error invalid arguments</span></span>
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a><span data-ttu-id="f4294-144">Wenn die ausführbare Datei nicht im Administrator Modus ausgeführt wurde</span><span class="sxs-lookup"><span data-stu-id="f4294-144">If the executable was not run in administrator mode</span></span>
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a><span data-ttu-id="f4294-145">Wenn beim Aktivieren oder Deaktivieren des Treibers ein Fehler aufgetreten ist</span><span class="sxs-lookup"><span data-stu-id="f4294-145">If there was an error enabling or disabling the driver</span></span>
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a><span data-ttu-id="f4294-146">Wenn beim Validieren der Version der räumlichen Datenbank ein Fehler aufgetreten ist</span><span class="sxs-lookup"><span data-stu-id="f4294-146">If there was an error validating the spatial database version</span></span>
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a><span data-ttu-id="f4294-147">Wenn beim Überprüfen des für die Ziel Import/Export-App bereitgestellten Paket Familiennamens ein Fehler aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="f4294-147">If there was an error validating the package family name provided for target import/export app</span></span>
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a><span data-ttu-id="f4294-148">Wenn beim Validieren der Benutzer-SID ein Fehler aufgetreten ist</span><span class="sxs-lookup"><span data-stu-id="f4294-148">If there was an error validating the user SID</span></span>
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a><span data-ttu-id="f4294-149">Wenn ein Fehler im Zusammenhang mit den räumlichen Datendateien des Ziels oder der Quelle aufgetreten ist</span><span class="sxs-lookup"><span data-stu-id="f4294-149">If there was an error related to the destination or source spatial data files</span></span>
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stoping-spectrumsharedrealitysvc"></a><span data-ttu-id="f4294-150">Bei einem Fehler im Zusammenhang mit dem Starten und Beenden von "Spectrum/sharedrealitysvc"</span><span class="sxs-lookup"><span data-stu-id="f4294-150">If there was an error related to starting and stoping Spectrum/SharedRealitySvc</span></span>
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
