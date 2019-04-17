---
title: Device Portal-API-Referenz
description: API-Referenz für die Windows Device Portal für HoloLens
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Windows Device Portal-,-API
ms.openlocfilehash: 507ab98734adea80d0aad41d99124e3d91846f28
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596066"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="c2197-104">Device Portal-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="c2197-104">Device portal API reference</span></span>

<span data-ttu-id="c2197-105">Alles, was in der [Windows Device Portal](using-the-windows-device-portal.md) basiert auf REST-API, Sie verwenden können, auf die Daten zugreifen und Ihr Gerät programmgesteuert steuern.</span><span class="sxs-lookup"><span data-stu-id="c2197-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="c2197-106">App-Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="c2197-106">App deloyment</span></span>

<span data-ttu-id="c2197-107">**/API/App/packagemanager/Package (löschen)**</span><span class="sxs-lookup"><span data-stu-id="c2197-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="c2197-108">Eine app deinstalliert</span><span class="sxs-lookup"><span data-stu-id="c2197-108">Uninstalls an app</span></span>

<span data-ttu-id="c2197-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-109">Parameters</span></span>
* <span data-ttu-id="c2197-110">Paket: Der Dateiname des Pakets deinstalliert werden.</span><span class="sxs-lookup"><span data-stu-id="c2197-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="c2197-111">**/api/app/packagemanager/package (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="c2197-112">Installieren einer App</span><span class="sxs-lookup"><span data-stu-id="c2197-112">Installs an App</span></span>

<span data-ttu-id="c2197-113">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-113">Parameters</span></span>
* <span data-ttu-id="c2197-114">Paket: Der Dateiname des Pakets installiert werden.</span><span class="sxs-lookup"><span data-stu-id="c2197-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="c2197-115">Nutzlast</span><span class="sxs-lookup"><span data-stu-id="c2197-115">Payload</span></span>
* <span data-ttu-id="c2197-116">Mehrteilige konformen http-Text</span><span class="sxs-lookup"><span data-stu-id="c2197-116">multi-part conforming http body</span></span>

<span data-ttu-id="c2197-117">**/API/App/packagemanager/Packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="c2197-118">Ruft die Liste der installierten apps auf dem System mit details</span><span class="sxs-lookup"><span data-stu-id="c2197-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="c2197-119">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="c2197-119">Return data</span></span>
* <span data-ttu-id="c2197-120">Liste der installierten Pakete mit den details</span><span class="sxs-lookup"><span data-stu-id="c2197-120">List of installed packages with details</span></span>

<span data-ttu-id="c2197-121">**/api/app/packagemanager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="c2197-122">Ruft den Status des in-app-Installation wird ausgeführt</span><span class="sxs-lookup"><span data-stu-id="c2197-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="c2197-123">Absturzabbildsammlung</span><span class="sxs-lookup"><span data-stu-id="c2197-123">Dump collection</span></span>

<span data-ttu-id="c2197-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="c2197-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="c2197-125">Deaktiviert die absturzabbilderfassung für sideload-Apps</span><span class="sxs-lookup"><span data-stu-id="c2197-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="c2197-126">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-126">Parameters</span></span>
* <span data-ttu-id="c2197-127">PackageFullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="c2197-127">packageFullname : package name</span></span>

<span data-ttu-id="c2197-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="c2197-129">Ruft die Einstellungen für quergeladene apps absturzabbilderfassung</span><span class="sxs-lookup"><span data-stu-id="c2197-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="c2197-130">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-130">Parameters</span></span>
* <span data-ttu-id="c2197-131">PackageFullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="c2197-131">packageFullname : package name</span></span>

<span data-ttu-id="c2197-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="c2197-133">Aktiviert und legt Dump-verwaltungseinstellungen für sideload-Apps</span><span class="sxs-lookup"><span data-stu-id="c2197-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="c2197-134">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-134">Parameters</span></span>
* <span data-ttu-id="c2197-135">PackageFullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="c2197-135">packageFullname : package name</span></span>

<span data-ttu-id="c2197-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="c2197-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="c2197-137">Löscht ein Absturzabbild für eine app mittels sideload übertragene</span><span class="sxs-lookup"><span data-stu-id="c2197-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="c2197-138">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-138">Parameters</span></span>
* <span data-ttu-id="c2197-139">PackageFullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="c2197-139">packageFullname : package name</span></span>
* <span data-ttu-id="c2197-140">Dateiname: Dump-Dateiname</span><span class="sxs-lookup"><span data-stu-id="c2197-140">fileName : dump file name</span></span>

<span data-ttu-id="c2197-141">**/api/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="c2197-142">Ruft ein Absturzabbild für eine app mittels sideload übertragene</span><span class="sxs-lookup"><span data-stu-id="c2197-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="c2197-143">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-143">Parameters</span></span>
* <span data-ttu-id="c2197-144">PackageFullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="c2197-144">packageFullname : package name</span></span>
* <span data-ttu-id="c2197-145">Dateiname: Dump-Dateiname</span><span class="sxs-lookup"><span data-stu-id="c2197-145">fileName : dump file name</span></span>

<span data-ttu-id="c2197-146">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="c2197-146">Return data</span></span>
* <span data-ttu-id="c2197-147">Sichern Sie die Datei.</span><span class="sxs-lookup"><span data-stu-id="c2197-147">Dump file.</span></span> <span data-ttu-id="c2197-148">Überprüfen Sie mit WinDbg oder Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c2197-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="c2197-149">**/api/debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="c2197-150">Gibt eine Liste mit allen Absturzabbilder für quergeladene apps</span><span class="sxs-lookup"><span data-stu-id="c2197-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="c2197-151">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="c2197-151">Return data</span></span>
* <span data-ttu-id="c2197-152">Liste der Abstürze pro Seite geladen app sichert</span><span class="sxs-lookup"><span data-stu-id="c2197-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="c2197-153">ETW</span><span class="sxs-lookup"><span data-stu-id="c2197-153">ETW</span></span>

<span data-ttu-id="c2197-154">**/API/ETW/Providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="c2197-155">Listet die registrierten Anbieter</span><span class="sxs-lookup"><span data-stu-id="c2197-155">Enumerates registered providers</span></span>

<span data-ttu-id="c2197-156">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="c2197-156">Return data</span></span>
* <span data-ttu-id="c2197-157">Liste der Anbieter "," Anzeigename "und" GUID</span><span class="sxs-lookup"><span data-stu-id="c2197-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="c2197-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="c2197-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="c2197-159">Erstellt eine Echtzeit-ETW-Sitzung. über ein Websocket verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="c2197-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="c2197-160">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="c2197-160">Return data</span></span>
* <span data-ttu-id="c2197-161">ETW-Ereignisse von den aktivierten Anbietern</span><span class="sxs-lookup"><span data-stu-id="c2197-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="c2197-162">Holographic – Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="c2197-162">Holographic OS</span></span>

<span data-ttu-id="c2197-163">**/api/holographic/os/etw/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="c2197-164">Gibt eine Liste von HoloLens bestimmte ETW-Anbieter, die nicht mit dem System registriert sind</span><span class="sxs-lookup"><span data-stu-id="c2197-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="c2197-165">**/api/holographic/os/services (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="c2197-166">Gibt den Status aller Dienste, die ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c2197-166">Returns the states of all services running.</span></span>

<span data-ttu-id="c2197-167">**/api/holographic/os/settings/ipd (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="c2197-168">Ruft den gespeicherten Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor (Interpupillary Abstand) in Millimeter</span><span class="sxs-lookup"><span data-stu-id="c2197-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="c2197-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="c2197-170">Legt die IPD</span><span class="sxs-lookup"><span data-stu-id="c2197-170">Sets the IPD</span></span>

<span data-ttu-id="c2197-171">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-171">Parameters</span></span>
* <span data-ttu-id="c2197-172">IPD: Neues IPD-Wert in Millimetern festgelegt werden</span><span class="sxs-lookup"><span data-stu-id="c2197-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="c2197-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="c2197-174">Abrufen der HTTPS-Anforderungen für das Geräteportal</span><span class="sxs-lookup"><span data-stu-id="c2197-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="c2197-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="c2197-176">Legt die HTTPS-Anforderungen für das Device Portal</span><span class="sxs-lookup"><span data-stu-id="c2197-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="c2197-177">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-177">Parameters</span></span>
* <span data-ttu-id="c2197-178">erforderlich: Ja, Nein oder Standardwert</span><span class="sxs-lookup"><span data-stu-id="c2197-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="c2197-179">Holographic Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="c2197-179">Holographic Perception</span></span>

<span data-ttu-id="c2197-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="c2197-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="c2197-181">Upgrades der Websocket akzeptiert, und führt einen Wahrnehmung-Client, der Updates auf 30 BpS sendet.</span><span class="sxs-lookup"><span data-stu-id="c2197-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="c2197-182">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-182">Parameters</span></span>
* <span data-ttu-id="c2197-183">Clientmode: "aktiv" erzwingt eine visual Nachverfolgungsmodus, wenn es nicht Passiv hergestellt werden kann</span><span class="sxs-lookup"><span data-stu-id="c2197-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="c2197-184">Holographic Thermischer</span><span class="sxs-lookup"><span data-stu-id="c2197-184">Holographic Thermal</span></span>

<span data-ttu-id="c2197-185">**/api/holographic/thermal/stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="c2197-186">Abrufen der temperaturüberwachung Phase des Geräts (0 – Normal, 1 betriebsbereiten, 2, kritische)</span><span class="sxs-lookup"><span data-stu-id="c2197-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="c2197-187">Perception Simulation-Steuerelement</span><span class="sxs-lookup"><span data-stu-id="c2197-187">Perception Simulation Control</span></span>

<span data-ttu-id="c2197-188">**/api/holographic/simulation/control/mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="c2197-189">Wurde der Simulationsmodus abrufen</span><span class="sxs-lookup"><span data-stu-id="c2197-189">Get the simulation mode</span></span>

<span data-ttu-id="c2197-190">**/api/holographic/simulation/control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="c2197-191">Legen Sie den Simulationsmodus</span><span class="sxs-lookup"><span data-stu-id="c2197-191">Set the simulation mode</span></span>

<span data-ttu-id="c2197-192">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-192">Parameters</span></span>
* <span data-ttu-id="c2197-193">Modus: Simulationsmodus: Standard, Simulation, Remote, ältere</span><span class="sxs-lookup"><span data-stu-id="c2197-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="c2197-194">**/api/holographic/simulation/control/stream (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="c2197-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="c2197-195">Löschen Sie einen Steuerelement-Datenstrom.</span><span class="sxs-lookup"><span data-stu-id="c2197-195">Delete a control stream.</span></span>

<span data-ttu-id="c2197-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="c2197-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="c2197-197">Öffnen Sie eine Web-Socket-Verbindung für einen Steuerelement-Datenstrom.</span><span class="sxs-lookup"><span data-stu-id="c2197-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="c2197-198">**/api/holographic/simulation/control/stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="c2197-199">Erstellen Sie einen Steuerelement-Datenstrom (Priorität erforderlich ist) oder Veröffentlichen von Daten für einen erstellten Stream (StreamId erforderlich).</span><span class="sxs-lookup"><span data-stu-id="c2197-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="c2197-200">Bereitgestellte Daten werden vom Typ "Application/Octet-Stream" erwartet.</span><span class="sxs-lookup"><span data-stu-id="c2197-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="c2197-201">Perception Simulation Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="c2197-201">Perception Simulation Playback</span></span>

<span data-ttu-id="c2197-202">**/API/holographic/Simulation/Playback/File (löschen)**</span><span class="sxs-lookup"><span data-stu-id="c2197-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="c2197-203">Löschen Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="c2197-203">Delete a recording.</span></span>

<span data-ttu-id="c2197-204">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-204">Parameters</span></span>
* <span data-ttu-id="c2197-205">Aufzeichnung: Der Name der Aufnahme zur löschen.</span><span class="sxs-lookup"><span data-stu-id="c2197-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="c2197-206">**/api/holographic/simulation/playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="c2197-207">Laden Sie eine Aufzeichnung hoch.</span><span class="sxs-lookup"><span data-stu-id="c2197-207">Upload a recording.</span></span>

<span data-ttu-id="c2197-208">**/API/holographic/Simulation/Playback/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="c2197-209">Alle Aufzeichnungen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c2197-209">Get all recordings.</span></span>

<span data-ttu-id="c2197-210">**/API/holographic/Simulation/Playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="c2197-211">Rufen Sie den aktuellen Status der Wiedergabe einer Aufzeichnung an.</span><span class="sxs-lookup"><span data-stu-id="c2197-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="c2197-212">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-212">Parameters</span></span>
* <span data-ttu-id="c2197-213">Aufzeichnung: Der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="c2197-213">recording : Name of recording.</span></span>

<span data-ttu-id="c2197-214">**/API/holographic/Simulation/Playback/Session/File (löschen)**</span><span class="sxs-lookup"><span data-stu-id="c2197-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="c2197-215">Entladen Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="c2197-215">Unload a recording.</span></span>

<span data-ttu-id="c2197-216">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-216">Parameters</span></span>
* <span data-ttu-id="c2197-217">Aufzeichnung: Der Name der Aufnahme zur nicht entladen.</span><span class="sxs-lookup"><span data-stu-id="c2197-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="c2197-218">**/API/holographic/Simulation/Playback/Session/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="c2197-219">Laden Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="c2197-219">Load a recording.</span></span>

<span data-ttu-id="c2197-220">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-220">Parameters</span></span>
* <span data-ttu-id="c2197-221">Aufzeichnung: Der Name der Aufnahme zur geladen werden.</span><span class="sxs-lookup"><span data-stu-id="c2197-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="c2197-222">**/API/holographic/Simulation/Playback/Session/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="c2197-223">Alle geladene Aufzeichnungen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c2197-223">Get all loaded recordings.</span></span>

<span data-ttu-id="c2197-224">**/api/holographic/simulation/playback/session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="c2197-225">Halten Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="c2197-225">Pause a recording.</span></span>

<span data-ttu-id="c2197-226">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-226">Parameters</span></span>
* <span data-ttu-id="c2197-227">Aufzeichnung: Der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="c2197-227">recording : Name of recording.</span></span>

<span data-ttu-id="c2197-228">**/API/holographic/Simulation/Playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="c2197-229">Wiedergeben Sie eine Aufnahme.</span><span class="sxs-lookup"><span data-stu-id="c2197-229">Play a recording.</span></span>

<span data-ttu-id="c2197-230">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-230">Parameters</span></span>
* <span data-ttu-id="c2197-231">Aufzeichnung: Der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="c2197-231">recording : Name of recording.</span></span>

<span data-ttu-id="c2197-232">**/api/holographic/simulation/playback/session/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="c2197-233">Eine Aufzeichnung zu beenden.</span><span class="sxs-lookup"><span data-stu-id="c2197-233">Stop a recording.</span></span>

<span data-ttu-id="c2197-234">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-234">Parameters</span></span>
* <span data-ttu-id="c2197-235">Aufzeichnung: Der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="c2197-235">recording : Name of recording.</span></span>

<span data-ttu-id="c2197-236">**/API/holographic/Simulation/Playback/Session/Types (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="c2197-237">Rufen Sie die Arten von Daten in einer geladenen Aufzeichnung an.</span><span class="sxs-lookup"><span data-stu-id="c2197-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="c2197-238">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-238">Parameters</span></span>
* <span data-ttu-id="c2197-239">Aufzeichnung: Der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="c2197-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="c2197-240">Aufzeichnung der Wahrnehmung-Simulation</span><span class="sxs-lookup"><span data-stu-id="c2197-240">Perception Simulation Recording</span></span>

<span data-ttu-id="c2197-241">**/api/holographic/simulation/recording/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="c2197-242">Starten Sie Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="c2197-242">Start a recording.</span></span> <span data-ttu-id="c2197-243">Nur eine einzigen Aufzeichnung gleichzeitig aktiv sein kann.</span><span class="sxs-lookup"><span data-stu-id="c2197-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="c2197-244">Head, praktische, SpatialMapping oder Umgebung muss festgelegt, werden.</span><span class="sxs-lookup"><span data-stu-id="c2197-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="c2197-245">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-245">Parameters</span></span>
* <span data-ttu-id="c2197-246">Head: Legen Sie auf 1 fest, um die Daten des Datensatzes Head.</span><span class="sxs-lookup"><span data-stu-id="c2197-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="c2197-247">praktische: Auf 1 festgelegt, um manuell Daten aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="c2197-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="c2197-248">SpatialMapping: Auf 1 festgelegt, um die räumliche Zuordnung zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="c2197-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="c2197-249">Umgebung: Zum Aufzeichnen von Umgebungsdaten auf 1 festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c2197-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="c2197-250">Name: Der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="c2197-250">name : Name of the recording.</span></span>
* <span data-ttu-id="c2197-251">SingleSpatialMappingFrame: Auf 1 festgelegt, um nur einen einzigen räumliche Zuordnung Frame zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="c2197-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="c2197-252">**/api/holographic/simulation/recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="c2197-253">Aufzeichnen von Status zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c2197-253">Get recording state.</span></span>

<span data-ttu-id="c2197-254">**/api/holographic/simulation/recording/stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="c2197-255">Die aktuelle Aufzeichnung zu beenden.</span><span class="sxs-lookup"><span data-stu-id="c2197-255">Stop the current recording.</span></span> <span data-ttu-id="c2197-256">Aufzeichnung wird als Datei zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="c2197-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="c2197-257">Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="c2197-257">Mixed Reality Capture</span></span>

<span data-ttu-id="c2197-258">**/API/holographic/MRC/File (löschen)**</span><span class="sxs-lookup"><span data-stu-id="c2197-258">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="c2197-259">Löscht die gemischte Realität vom Gerät aufzeichnen.</span><span class="sxs-lookup"><span data-stu-id="c2197-259">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="c2197-260">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-260">Parameters</span></span>
* <span data-ttu-id="c2197-261">Dateiname: Name, hex64 codiert, der zu löschenden Datei</span><span class="sxs-lookup"><span data-stu-id="c2197-261">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="c2197-262">**/api/holographic/mrc/settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-262">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="c2197-263">Ruft gemischt den Standard tatsächlich Capture-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="c2197-263">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="c2197-264">**/api/holographic/mrc/file (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-264">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="c2197-265">Lädt eine mixed Reality-Datei auf dem Gerät herunter.</span><span class="sxs-lookup"><span data-stu-id="c2197-265">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="c2197-266">Verwenden von Op = Stream-Abfrageparameter für das streaming.</span><span class="sxs-lookup"><span data-stu-id="c2197-266">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="c2197-267">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-267">Parameters</span></span>
* <span data-ttu-id="c2197-268">Dateiname: Name, hex64 codiert, der die Datei zum Abrufen</span><span class="sxs-lookup"><span data-stu-id="c2197-268">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="c2197-269">Op: Stream</span><span class="sxs-lookup"><span data-stu-id="c2197-269">op : stream</span></span>

<span data-ttu-id="c2197-270">**/API/holographic/MRC/Thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-270">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="c2197-271">Ruft die Miniaturansicht für die angegebene Datei.</span><span class="sxs-lookup"><span data-stu-id="c2197-271">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="c2197-272">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-272">Parameters</span></span>
* <span data-ttu-id="c2197-273">Dateiname: Name, hex64 codiert, der die Datei, die für die die Miniaturansicht angefordert wird</span><span class="sxs-lookup"><span data-stu-id="c2197-273">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="c2197-274">**/api/holographic/mrc/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-274">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="c2197-275">Ruft den Status der mixed Reality aufgezeichnet ("ausführen", "beendet")</span><span class="sxs-lookup"><span data-stu-id="c2197-275">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="c2197-276">**/api/holographic/mrc/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-276">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="c2197-277">Gibt die Liste der auf dem Gerät gespeicherten mixed Reality-Dateien</span><span class="sxs-lookup"><span data-stu-id="c2197-277">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="c2197-278">**/api/holographic/mrc/settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="c2197-279">Legt gemischt den Standard tatsächlich Capture-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="c2197-279">Sets the default mixed reality capture settings</span></span>

<span data-ttu-id="c2197-280">**/api/holographic/mrc/video/control/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-280">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="c2197-281">Startet eine Aufzeichnung mixed reality</span><span class="sxs-lookup"><span data-stu-id="c2197-281">Starts a mixed reality recording</span></span>

<span data-ttu-id="c2197-282">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-282">Parameters</span></span>
* <span data-ttu-id="c2197-283">Holo: Erfassen von Hologramme: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="c2197-283">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="c2197-284">PV: Erfassung PV Kamera: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="c2197-284">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="c2197-285">MIC: Erfassung Mikrofon: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="c2197-285">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="c2197-286">Loopback: Erfassen von app-Audio: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="c2197-286">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="c2197-287">**/api/holographic/mrc/video/control/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-287">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="c2197-288">Beendet kombiniert die aktuelle Realität Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="c2197-288">Stops the current mixed reality recording</span></span>

<span data-ttu-id="c2197-289">**/api/holographic/mrc/photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-289">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="c2197-290">Nimmt ein Foto mixed Reality und erstellt eine Datei auf dem Gerät</span><span class="sxs-lookup"><span data-stu-id="c2197-290">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="c2197-291">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-291">Parameters</span></span>
* <span data-ttu-id="c2197-292">Holo: Erfassen von Hologramme: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="c2197-292">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="c2197-293">PV: Erfassung PV Kamera: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="c2197-293">pv : capture PV camera: true or false</span></span>

<span data-ttu-id="c2197-294">Mixed Reality-Streaming</span><span class="sxs-lookup"><span data-stu-id="c2197-294">Mixed Reality Streaming</span></span>

<span data-ttu-id="c2197-295">**/api/holographic/stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-295">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="c2197-296">Starten des portionsweisen Downloads einer fragmentierten MP4-Datei</span><span class="sxs-lookup"><span data-stu-id="c2197-296">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="c2197-297">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-297">Parameters</span></span>
* <span data-ttu-id="c2197-298">Holo: Erfassen von Hologramme: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="c2197-298">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="c2197-299">PV: Erfassung PV Kamera: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="c2197-299">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="c2197-300">MIC: Erfassung Mikrofon: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="c2197-300">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="c2197-301">Loopback: Erfassen von app-Audio: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="c2197-301">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="c2197-302">**/api/holographic/stream/live_high.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-302">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="c2197-303">Starten des portionsweisen Downloads einer fragmentierten MP4-Datei</span><span class="sxs-lookup"><span data-stu-id="c2197-303">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="c2197-304">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-304">Parameters</span></span>
* <span data-ttu-id="c2197-305">Holo: Erfassen von Hologramme: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="c2197-305">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="c2197-306">PV: Erfassung PV Kamera: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="c2197-306">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="c2197-307">MIC: Erfassung Mikrofon: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="c2197-307">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="c2197-308">Loopback: Erfassen von app-Audio: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="c2197-308">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="c2197-309">**/api/holographic/stream/live_low.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-309">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="c2197-310">Starten des portionsweisen Downloads einer fragmentierten MP4-Datei</span><span class="sxs-lookup"><span data-stu-id="c2197-310">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="c2197-311">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-311">Parameters</span></span>
* <span data-ttu-id="c2197-312">Holo: Erfassen von Hologramme: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="c2197-312">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="c2197-313">PV: Erfassung PV Kamera: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="c2197-313">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="c2197-314">MIC: Erfassung Mikrofon: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="c2197-314">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="c2197-315">Loopback: Erfassen von app-Audio: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="c2197-315">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="c2197-316">**/api/holographic/stream/live_med.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="c2197-317">Starten des portionsweisen Downloads einer fragmentierten MP4-Datei</span><span class="sxs-lookup"><span data-stu-id="c2197-317">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="c2197-318">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-318">Parameters</span></span>
* <span data-ttu-id="c2197-319">Holo: Erfassen von Hologramme: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="c2197-319">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="c2197-320">PV: Erfassung PV Kamera: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="c2197-320">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="c2197-321">MIC: Erfassung Mikrofon: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="c2197-321">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="c2197-322">Loopback: Erfassen von app-Audio: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="c2197-322">loopback : capture app audio: true or false</span></span>

## <a name="networking"></a><span data-ttu-id="c2197-323">Netzwerk</span><span class="sxs-lookup"><span data-stu-id="c2197-323">Networking</span></span>

<span data-ttu-id="c2197-324">**/api/networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-324">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="c2197-325">Ruft die aktuelle IP-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="c2197-325">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="c2197-326">Informationen zum Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="c2197-326">OS Information</span></span>

<span data-ttu-id="c2197-327">**/api/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-327">**/api/os/info (GET)**</span></span>

<span data-ttu-id="c2197-328">Ruft Informationen zum Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="c2197-328">Gets operating system information</span></span>

<span data-ttu-id="c2197-329">**/api/os/machinename (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-329">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="c2197-330">Ruft den Computernamen ab</span><span class="sxs-lookup"><span data-stu-id="c2197-330">Gets the machine name</span></span>

<span data-ttu-id="c2197-331">**/api/os/machinename (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-331">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="c2197-332">Legt den Computernamen fest</span><span class="sxs-lookup"><span data-stu-id="c2197-332">Sets the machine name</span></span>

<span data-ttu-id="c2197-333">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-333">Parameters</span></span>
* <span data-ttu-id="c2197-334">Name: Neuen Namen des Computers hex64 codiert, um für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="c2197-334">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="c2197-335">Leistungsdaten</span><span class="sxs-lookup"><span data-stu-id="c2197-335">Performance data</span></span>

<span data-ttu-id="c2197-336">**/api/resourcemanager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-336">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="c2197-337">Gibt die Liste der ausgeführten Prozesse mit details</span><span class="sxs-lookup"><span data-stu-id="c2197-337">Returns the list of running processes with details</span></span>

<span data-ttu-id="c2197-338">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="c2197-338">Return data</span></span>
* <span data-ttu-id="c2197-339">JSON mit Liste der Prozesse und Details für jeden Prozess</span><span class="sxs-lookup"><span data-stu-id="c2197-339">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="c2197-340">**/api/resourcemanager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-340">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="c2197-341">Statistische Daten aus System Perf (e/a-Lese-/Schreibzugriff, speicherstatistiken usw.</span><span class="sxs-lookup"><span data-stu-id="c2197-341">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="c2197-342">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="c2197-342">Return data</span></span>
* <span data-ttu-id="c2197-343">JSON mit Systeminformationen: CPU, GPU, Arbeitsspeicher, Netzwerk, e/a</span><span class="sxs-lookup"><span data-stu-id="c2197-343">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="c2197-344">Stromversorgung</span><span class="sxs-lookup"><span data-stu-id="c2197-344">Power</span></span>

<span data-ttu-id="c2197-345">**/api/power/battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-345">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="c2197-346">Ruft den aktuellen Zustand der Akkus</span><span class="sxs-lookup"><span data-stu-id="c2197-346">Gets the current battery state</span></span>

<span data-ttu-id="c2197-347">**/API/Power/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-347">**/api/power/state (GET)**</span></span>

<span data-ttu-id="c2197-348">Überprüft, ob das System in einen Energiesparmodus ist.</span><span class="sxs-lookup"><span data-stu-id="c2197-348">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="c2197-349">Remotesteuerung</span><span class="sxs-lookup"><span data-stu-id="c2197-349">Remote Control</span></span>

<span data-ttu-id="c2197-350">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-350">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="c2197-351">Wird die Zielgerät neu gestartet</span><span class="sxs-lookup"><span data-stu-id="c2197-351">Restarts the target device</span></span>

<span data-ttu-id="c2197-352">**/api/control/shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-352">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="c2197-353">Das Gerät heruntergefahren</span><span class="sxs-lookup"><span data-stu-id="c2197-353">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="c2197-354">Task-Manager</span><span class="sxs-lookup"><span data-stu-id="c2197-354">Task Manager</span></span>

<span data-ttu-id="c2197-355">**/api/taskmanager/app (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="c2197-355">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="c2197-356">Beendet einen modernen Apps</span><span class="sxs-lookup"><span data-stu-id="c2197-356">Stops a modern app</span></span>

<span data-ttu-id="c2197-357">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-357">Parameters</span></span>
* <span data-ttu-id="c2197-358">Paket: Vollständigen Namen des app-Pakets, hex64 codiert</span><span class="sxs-lookup"><span data-stu-id="c2197-358">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="c2197-359">"forcestop": Erzwingen, dass alle Prozesse beendet (= Yes)</span><span class="sxs-lookup"><span data-stu-id="c2197-359">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="c2197-360">**/api/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-360">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="c2197-361">Startet einen modernen Apps</span><span class="sxs-lookup"><span data-stu-id="c2197-361">Starts a modern app</span></span>

<span data-ttu-id="c2197-362">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-362">Parameters</span></span>
* <span data-ttu-id="c2197-363">App-ID: PRAID der app zu starten, codiert hex64</span><span class="sxs-lookup"><span data-stu-id="c2197-363">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="c2197-364">Paket: Vollständigen Namen des app-Pakets, hex64 codiert</span><span class="sxs-lookup"><span data-stu-id="c2197-364">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="c2197-365">WiFi-Verwaltung</span><span class="sxs-lookup"><span data-stu-id="c2197-365">WiFi Management</span></span>

<span data-ttu-id="c2197-366">**/API/WiFi/Interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-366">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="c2197-367">Listet Drahtlosnetzwerk-Schnittstellen</span><span class="sxs-lookup"><span data-stu-id="c2197-367">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="c2197-368">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="c2197-368">Return data</span></span>
* <span data-ttu-id="c2197-369">Liste der drahtlosen Schnittstellen mit den Details (GUID, Beschreibung usw.).</span><span class="sxs-lookup"><span data-stu-id="c2197-369">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="c2197-370">**/api/wifi/network (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="c2197-370">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="c2197-371">Löscht ein Profil ein Netzwerk auf eine angegebene Schnittstelle zugeordnet</span><span class="sxs-lookup"><span data-stu-id="c2197-371">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="c2197-372">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-372">Parameters</span></span>
* <span data-ttu-id="c2197-373">Schnittstelle: Netzwerk-Guid der Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="c2197-373">interface : network interface guid</span></span>
* <span data-ttu-id="c2197-374">Profil: Profilname</span><span class="sxs-lookup"><span data-stu-id="c2197-374">profile : profile name</span></span>

<span data-ttu-id="c2197-375">**/api/wifi/networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-375">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="c2197-376">Listet Drahtlosnetzwerke auf die angegebene Netzwerkschnittstelle</span><span class="sxs-lookup"><span data-stu-id="c2197-376">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="c2197-377">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-377">Parameters</span></span>
* <span data-ttu-id="c2197-378">Schnittstelle: Netzwerk-Guid der Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="c2197-378">interface : network interface guid</span></span>

<span data-ttu-id="c2197-379">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="c2197-379">Return data</span></span>
* <span data-ttu-id="c2197-380">Liste der Drahtlosnetzwerke finden Sie auf die Netzwerkschnittstelle mit details</span><span class="sxs-lookup"><span data-stu-id="c2197-380">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="c2197-381">**/api/wifi/network (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-381">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="c2197-382">Eine Verbindung herstellt oder trennt die Verbindung mit einem Netzwerk für die angegebene Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="c2197-382">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="c2197-383">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-383">Parameters</span></span>
* <span data-ttu-id="c2197-384">Schnittstelle: Netzwerk-Guid der Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="c2197-384">interface : network interface guid</span></span>
* <span data-ttu-id="c2197-385">SSID: Ssid, hex64 codiert sind, klicken Sie zum Herstellen einer Verbindung mit</span><span class="sxs-lookup"><span data-stu-id="c2197-385">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="c2197-386">Op: herstellen oder trennen</span><span class="sxs-lookup"><span data-stu-id="c2197-386">op : connect or disconnect</span></span>
* <span data-ttu-id="c2197-387">CreateProfile: Ja oder Nein</span><span class="sxs-lookup"><span data-stu-id="c2197-387">createprofile : yes or no</span></span>
* <span data-ttu-id="c2197-388">Schlüssel: shared Key, hex64 codiert</span><span class="sxs-lookup"><span data-stu-id="c2197-388">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="c2197-389">Windows-Leistungsaufzeichnung</span><span class="sxs-lookup"><span data-stu-id="c2197-389">Windows Performance Recorder</span></span>

<span data-ttu-id="c2197-390">**/api/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-390">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="c2197-391">Lädt ein WPR-Profil, und startet die Protokollierung mithilfe des hochgeladenen Profils.</span><span class="sxs-lookup"><span data-stu-id="c2197-391">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="c2197-392">Nutzlast</span><span class="sxs-lookup"><span data-stu-id="c2197-392">Payload</span></span>
* <span data-ttu-id="c2197-393">Mehrteilige konformen http-Text</span><span class="sxs-lookup"><span data-stu-id="c2197-393">multi-part conforming http body</span></span>

<span data-ttu-id="c2197-394">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="c2197-394">Return data</span></span>
* <span data-ttu-id="c2197-395">Gibt den WPR-Sitzungsstatus zurück.</span><span class="sxs-lookup"><span data-stu-id="c2197-395">Returns the WPR session status.</span></span>

<span data-ttu-id="c2197-396">**/api/wpr/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-396">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="c2197-397">Ruft den Status der Sitzung WPR ab</span><span class="sxs-lookup"><span data-stu-id="c2197-397">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="c2197-398">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="c2197-398">Return data</span></span>
* <span data-ttu-id="c2197-399">WPR Sitzungsstatus.</span><span class="sxs-lookup"><span data-stu-id="c2197-399">WPR session status.</span></span>

<span data-ttu-id="c2197-400">**/api/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="c2197-400">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="c2197-401">Beendet eine Ablaufverfolgungssitzung WPR (Leistung)</span><span class="sxs-lookup"><span data-stu-id="c2197-401">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="c2197-402">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="c2197-402">Return data</span></span>
* <span data-ttu-id="c2197-403">Gibt zurück, die ETL-Datei</span><span class="sxs-lookup"><span data-stu-id="c2197-403">Returns the trace ETL file</span></span>

<span data-ttu-id="c2197-404">**/api/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="c2197-404">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="c2197-405">Startet eine WPR (Leistung), die Ablaufverfolgung von Sitzungen</span><span class="sxs-lookup"><span data-stu-id="c2197-405">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="c2197-406">Parameter</span><span class="sxs-lookup"><span data-stu-id="c2197-406">Parameters</span></span>
* <span data-ttu-id="c2197-407">Profil: Profilname.</span><span class="sxs-lookup"><span data-stu-id="c2197-407">profile : Profile name.</span></span> <span data-ttu-id="c2197-408">Verfügbare Profile werden in perfprofiles/profiles.json gespeichert.</span><span class="sxs-lookup"><span data-stu-id="c2197-408">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="c2197-409">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="c2197-409">Return data</span></span>
* <span data-ttu-id="c2197-410">Beim Start wird der WPR-Sitzung-Status zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="c2197-410">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="c2197-411">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c2197-411">See also</span></span>
* [<span data-ttu-id="c2197-412">Verwenden die Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="c2197-412">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="c2197-413">Device Portal-Core-API-Referenz (UWP)</span><span class="sxs-lookup"><span data-stu-id="c2197-413">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
