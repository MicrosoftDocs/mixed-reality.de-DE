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
# <a name="device-portal-api-reference"></a><span data-ttu-id="5fa2a-104">Device Portal-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="5fa2a-104">Device portal API reference</span></span>

<span data-ttu-id="5fa2a-105">Alles, was in der [Windows Device Portal](using-the-windows-device-portal.md) basiert auf REST-API, Sie verwenden können, auf die Daten zugreifen und Ihr Gerät programmgesteuert steuern.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="5fa2a-106">App-Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="5fa2a-106">App deloyment</span></span>

<span data-ttu-id="5fa2a-107">**/API/App/packagemanager/Package (löschen)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="5fa2a-108">Eine app deinstalliert</span><span class="sxs-lookup"><span data-stu-id="5fa2a-108">Uninstalls an app</span></span>

<span data-ttu-id="5fa2a-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-109">Parameters</span></span>
* <span data-ttu-id="5fa2a-110">Paket: Der Dateiname des Pakets deinstalliert werden.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="5fa2a-111">**/api/app/packagemanager/package (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="5fa2a-112">Installieren einer App</span><span class="sxs-lookup"><span data-stu-id="5fa2a-112">Installs an App</span></span>

<span data-ttu-id="5fa2a-113">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-113">Parameters</span></span>
* <span data-ttu-id="5fa2a-114">Paket: Der Dateiname des Pakets installiert werden.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="5fa2a-115">Nutzlast</span><span class="sxs-lookup"><span data-stu-id="5fa2a-115">Payload</span></span>
* <span data-ttu-id="5fa2a-116">Mehrteilige konformen http-Text</span><span class="sxs-lookup"><span data-stu-id="5fa2a-116">multi-part conforming http body</span></span>

<span data-ttu-id="5fa2a-117">**/API/App/packagemanager/Packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="5fa2a-118">Ruft die Liste der installierten apps auf dem System mit details</span><span class="sxs-lookup"><span data-stu-id="5fa2a-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="5fa2a-119">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="5fa2a-119">Return data</span></span>
* <span data-ttu-id="5fa2a-120">Liste der installierten Pakete mit den details</span><span class="sxs-lookup"><span data-stu-id="5fa2a-120">List of installed packages with details</span></span>

<span data-ttu-id="5fa2a-121">**/api/app/packagemanager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="5fa2a-122">Ruft den Status des in-app-Installation wird ausgeführt</span><span class="sxs-lookup"><span data-stu-id="5fa2a-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="5fa2a-123">Absturzabbildsammlung</span><span class="sxs-lookup"><span data-stu-id="5fa2a-123">Dump collection</span></span>

<span data-ttu-id="5fa2a-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="5fa2a-125">Deaktiviert die absturzabbilderfassung für sideload-Apps</span><span class="sxs-lookup"><span data-stu-id="5fa2a-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="5fa2a-126">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-126">Parameters</span></span>
* <span data-ttu-id="5fa2a-127">PackageFullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="5fa2a-127">packageFullname : package name</span></span>

<span data-ttu-id="5fa2a-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="5fa2a-129">Ruft die Einstellungen für quergeladene apps absturzabbilderfassung</span><span class="sxs-lookup"><span data-stu-id="5fa2a-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="5fa2a-130">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-130">Parameters</span></span>
* <span data-ttu-id="5fa2a-131">PackageFullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="5fa2a-131">packageFullname : package name</span></span>

<span data-ttu-id="5fa2a-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="5fa2a-133">Aktiviert und legt Dump-verwaltungseinstellungen für sideload-Apps</span><span class="sxs-lookup"><span data-stu-id="5fa2a-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="5fa2a-134">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-134">Parameters</span></span>
* <span data-ttu-id="5fa2a-135">PackageFullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="5fa2a-135">packageFullname : package name</span></span>

<span data-ttu-id="5fa2a-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="5fa2a-137">Löscht ein Absturzabbild für eine app mittels sideload übertragene</span><span class="sxs-lookup"><span data-stu-id="5fa2a-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="5fa2a-138">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-138">Parameters</span></span>
* <span data-ttu-id="5fa2a-139">PackageFullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="5fa2a-139">packageFullname : package name</span></span>
* <span data-ttu-id="5fa2a-140">Dateiname: Dump-Dateiname</span><span class="sxs-lookup"><span data-stu-id="5fa2a-140">fileName : dump file name</span></span>

<span data-ttu-id="5fa2a-141">**/api/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="5fa2a-142">Ruft ein Absturzabbild für eine app mittels sideload übertragene</span><span class="sxs-lookup"><span data-stu-id="5fa2a-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="5fa2a-143">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-143">Parameters</span></span>
* <span data-ttu-id="5fa2a-144">PackageFullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="5fa2a-144">packageFullname : package name</span></span>
* <span data-ttu-id="5fa2a-145">Dateiname: Dump-Dateiname</span><span class="sxs-lookup"><span data-stu-id="5fa2a-145">fileName : dump file name</span></span>

<span data-ttu-id="5fa2a-146">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="5fa2a-146">Return data</span></span>
* <span data-ttu-id="5fa2a-147">Sichern Sie die Datei.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-147">Dump file.</span></span> <span data-ttu-id="5fa2a-148">Überprüfen Sie mit WinDbg oder Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5fa2a-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="5fa2a-149">**/api/debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="5fa2a-150">Gibt eine Liste mit allen Absturzabbilder für quergeladene apps</span><span class="sxs-lookup"><span data-stu-id="5fa2a-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="5fa2a-151">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="5fa2a-151">Return data</span></span>
* <span data-ttu-id="5fa2a-152">Liste der Abstürze pro Seite geladen app sichert</span><span class="sxs-lookup"><span data-stu-id="5fa2a-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="5fa2a-153">ETW</span><span class="sxs-lookup"><span data-stu-id="5fa2a-153">ETW</span></span>

<span data-ttu-id="5fa2a-154">**/API/ETW/Providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="5fa2a-155">Listet die registrierten Anbieter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-155">Enumerates registered providers</span></span>

<span data-ttu-id="5fa2a-156">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="5fa2a-156">Return data</span></span>
* <span data-ttu-id="5fa2a-157">Liste der Anbieter "," Anzeigename "und" GUID</span><span class="sxs-lookup"><span data-stu-id="5fa2a-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="5fa2a-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="5fa2a-159">Erstellt eine Echtzeit-ETW-Sitzung. über ein Websocket verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="5fa2a-160">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="5fa2a-160">Return data</span></span>
* <span data-ttu-id="5fa2a-161">ETW-Ereignisse von den aktivierten Anbietern</span><span class="sxs-lookup"><span data-stu-id="5fa2a-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="5fa2a-162">Holographic – Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="5fa2a-162">Holographic OS</span></span>

<span data-ttu-id="5fa2a-163">**/api/holographic/os/etw/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="5fa2a-164">Gibt eine Liste von HoloLens bestimmte ETW-Anbieter, die nicht mit dem System registriert sind</span><span class="sxs-lookup"><span data-stu-id="5fa2a-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="5fa2a-165">**/api/holographic/os/services (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="5fa2a-166">Gibt den Status aller Dienste, die ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-166">Returns the states of all services running.</span></span>

<span data-ttu-id="5fa2a-167">**/api/holographic/os/settings/ipd (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="5fa2a-168">Ruft den gespeicherten Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor (Interpupillary Abstand) in Millimeter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="5fa2a-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="5fa2a-170">Legt die IPD</span><span class="sxs-lookup"><span data-stu-id="5fa2a-170">Sets the IPD</span></span>

<span data-ttu-id="5fa2a-171">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-171">Parameters</span></span>
* <span data-ttu-id="5fa2a-172">IPD: Neues IPD-Wert in Millimetern festgelegt werden</span><span class="sxs-lookup"><span data-stu-id="5fa2a-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="5fa2a-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="5fa2a-174">Abrufen der HTTPS-Anforderungen für das Geräteportal</span><span class="sxs-lookup"><span data-stu-id="5fa2a-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="5fa2a-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="5fa2a-176">Legt die HTTPS-Anforderungen für das Device Portal</span><span class="sxs-lookup"><span data-stu-id="5fa2a-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="5fa2a-177">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-177">Parameters</span></span>
* <span data-ttu-id="5fa2a-178">erforderlich: Ja, Nein oder Standardwert</span><span class="sxs-lookup"><span data-stu-id="5fa2a-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="5fa2a-179">Holographic Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="5fa2a-179">Holographic Perception</span></span>

<span data-ttu-id="5fa2a-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="5fa2a-181">Upgrades der Websocket akzeptiert, und führt einen Wahrnehmung-Client, der Updates auf 30 BpS sendet.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="5fa2a-182">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-182">Parameters</span></span>
* <span data-ttu-id="5fa2a-183">Clientmode: "aktiv" erzwingt eine visual Nachverfolgungsmodus, wenn es nicht Passiv hergestellt werden kann</span><span class="sxs-lookup"><span data-stu-id="5fa2a-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="5fa2a-184">Holographic Thermischer</span><span class="sxs-lookup"><span data-stu-id="5fa2a-184">Holographic Thermal</span></span>

<span data-ttu-id="5fa2a-185">**/api/holographic/thermal/stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="5fa2a-186">Abrufen der temperaturüberwachung Phase des Geräts (0 – Normal, 1 betriebsbereiten, 2, kritische)</span><span class="sxs-lookup"><span data-stu-id="5fa2a-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="5fa2a-187">Perception Simulation-Steuerelement</span><span class="sxs-lookup"><span data-stu-id="5fa2a-187">Perception Simulation Control</span></span>

<span data-ttu-id="5fa2a-188">**/api/holographic/simulation/control/mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="5fa2a-189">Wurde der Simulationsmodus abrufen</span><span class="sxs-lookup"><span data-stu-id="5fa2a-189">Get the simulation mode</span></span>

<span data-ttu-id="5fa2a-190">**/api/holographic/simulation/control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="5fa2a-191">Legen Sie den Simulationsmodus</span><span class="sxs-lookup"><span data-stu-id="5fa2a-191">Set the simulation mode</span></span>

<span data-ttu-id="5fa2a-192">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-192">Parameters</span></span>
* <span data-ttu-id="5fa2a-193">Modus: Simulationsmodus: Standard, Simulation, Remote, ältere</span><span class="sxs-lookup"><span data-stu-id="5fa2a-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="5fa2a-194">**/api/holographic/simulation/control/stream (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="5fa2a-195">Löschen Sie einen Steuerelement-Datenstrom.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-195">Delete a control stream.</span></span>

<span data-ttu-id="5fa2a-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="5fa2a-197">Öffnen Sie eine Web-Socket-Verbindung für einen Steuerelement-Datenstrom.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="5fa2a-198">**/api/holographic/simulation/control/stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="5fa2a-199">Erstellen Sie einen Steuerelement-Datenstrom (Priorität erforderlich ist) oder Veröffentlichen von Daten für einen erstellten Stream (StreamId erforderlich).</span><span class="sxs-lookup"><span data-stu-id="5fa2a-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="5fa2a-200">Bereitgestellte Daten werden vom Typ "Application/Octet-Stream" erwartet.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="5fa2a-201">Perception Simulation Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="5fa2a-201">Perception Simulation Playback</span></span>

<span data-ttu-id="5fa2a-202">**/API/holographic/Simulation/Playback/File (löschen)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="5fa2a-203">Löschen Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-203">Delete a recording.</span></span>

<span data-ttu-id="5fa2a-204">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-204">Parameters</span></span>
* <span data-ttu-id="5fa2a-205">Aufzeichnung: Der Name der Aufnahme zur löschen.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="5fa2a-206">**/api/holographic/simulation/playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="5fa2a-207">Laden Sie eine Aufzeichnung hoch.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-207">Upload a recording.</span></span>

<span data-ttu-id="5fa2a-208">**/API/holographic/Simulation/Playback/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="5fa2a-209">Alle Aufzeichnungen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-209">Get all recordings.</span></span>

<span data-ttu-id="5fa2a-210">**/API/holographic/Simulation/Playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="5fa2a-211">Rufen Sie den aktuellen Status der Wiedergabe einer Aufzeichnung an.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="5fa2a-212">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-212">Parameters</span></span>
* <span data-ttu-id="5fa2a-213">Aufzeichnung: Der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-213">recording : Name of recording.</span></span>

<span data-ttu-id="5fa2a-214">**/API/holographic/Simulation/Playback/Session/File (löschen)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="5fa2a-215">Entladen Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-215">Unload a recording.</span></span>

<span data-ttu-id="5fa2a-216">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-216">Parameters</span></span>
* <span data-ttu-id="5fa2a-217">Aufzeichnung: Der Name der Aufnahme zur nicht entladen.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="5fa2a-218">**/API/holographic/Simulation/Playback/Session/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="5fa2a-219">Laden Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-219">Load a recording.</span></span>

<span data-ttu-id="5fa2a-220">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-220">Parameters</span></span>
* <span data-ttu-id="5fa2a-221">Aufzeichnung: Der Name der Aufnahme zur geladen werden.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="5fa2a-222">**/API/holographic/Simulation/Playback/Session/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="5fa2a-223">Alle geladene Aufzeichnungen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-223">Get all loaded recordings.</span></span>

<span data-ttu-id="5fa2a-224">**/api/holographic/simulation/playback/session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="5fa2a-225">Halten Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-225">Pause a recording.</span></span>

<span data-ttu-id="5fa2a-226">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-226">Parameters</span></span>
* <span data-ttu-id="5fa2a-227">Aufzeichnung: Der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-227">recording : Name of recording.</span></span>

<span data-ttu-id="5fa2a-228">**/API/holographic/Simulation/Playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="5fa2a-229">Wiedergeben Sie eine Aufnahme.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-229">Play a recording.</span></span>

<span data-ttu-id="5fa2a-230">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-230">Parameters</span></span>
* <span data-ttu-id="5fa2a-231">Aufzeichnung: Der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-231">recording : Name of recording.</span></span>

<span data-ttu-id="5fa2a-232">**/api/holographic/simulation/playback/session/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="5fa2a-233">Eine Aufzeichnung zu beenden.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-233">Stop a recording.</span></span>

<span data-ttu-id="5fa2a-234">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-234">Parameters</span></span>
* <span data-ttu-id="5fa2a-235">Aufzeichnung: Der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-235">recording : Name of recording.</span></span>

<span data-ttu-id="5fa2a-236">**/API/holographic/Simulation/Playback/Session/Types (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="5fa2a-237">Rufen Sie die Arten von Daten in einer geladenen Aufzeichnung an.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="5fa2a-238">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-238">Parameters</span></span>
* <span data-ttu-id="5fa2a-239">Aufzeichnung: Der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="5fa2a-240">Aufzeichnung der Wahrnehmung-Simulation</span><span class="sxs-lookup"><span data-stu-id="5fa2a-240">Perception Simulation Recording</span></span>

<span data-ttu-id="5fa2a-241">**/api/holographic/simulation/recording/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="5fa2a-242">Starten Sie Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-242">Start a recording.</span></span> <span data-ttu-id="5fa2a-243">Nur eine einzigen Aufzeichnung gleichzeitig aktiv sein kann.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="5fa2a-244">Head, praktische, SpatialMapping oder Umgebung muss festgelegt, werden.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="5fa2a-245">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-245">Parameters</span></span>
* <span data-ttu-id="5fa2a-246">Head: Legen Sie auf 1 fest, um die Daten des Datensatzes Head.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="5fa2a-247">praktische: Auf 1 festgelegt, um manuell Daten aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="5fa2a-248">SpatialMapping: Auf 1 festgelegt, um die räumliche Zuordnung zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="5fa2a-249">Umgebung: Zum Aufzeichnen von Umgebungsdaten auf 1 festgelegt.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="5fa2a-250">Name: Der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-250">name : Name of the recording.</span></span>
* <span data-ttu-id="5fa2a-251">SingleSpatialMappingFrame: Auf 1 festgelegt, um nur einen einzigen räumliche Zuordnung Frame zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="5fa2a-252">**/api/holographic/simulation/recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="5fa2a-253">Aufzeichnen von Status zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-253">Get recording state.</span></span>

<span data-ttu-id="5fa2a-254">**/api/holographic/simulation/recording/stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="5fa2a-255">Die aktuelle Aufzeichnung zu beenden.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-255">Stop the current recording.</span></span> <span data-ttu-id="5fa2a-256">Aufzeichnung wird als Datei zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="5fa2a-257">Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="5fa2a-257">Mixed Reality Capture</span></span>

<span data-ttu-id="5fa2a-258">**/api/holographic/mrc/file (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="5fa2a-259">Lädt eine mixed Reality-Datei auf dem Gerät herunter.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="5fa2a-260">Verwenden von Op = Stream-Abfrageparameter für das streaming.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="5fa2a-261">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-261">Parameters</span></span>
* <span data-ttu-id="5fa2a-262">Dateiname: Name, hex64 codiert, der die Datei zum Abrufen</span><span class="sxs-lookup"><span data-stu-id="5fa2a-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="5fa2a-263">Op: Stream</span><span class="sxs-lookup"><span data-stu-id="5fa2a-263">op : stream</span></span>

<span data-ttu-id="5fa2a-264">**/API/holographic/MRC/File (löschen)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="5fa2a-265">Löscht die gemischte Realität vom Gerät aufzeichnen.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="5fa2a-266">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-266">Parameters</span></span>
* <span data-ttu-id="5fa2a-267">Dateiname: Name, hex64 codiert, der zu löschenden Datei</span><span class="sxs-lookup"><span data-stu-id="5fa2a-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="5fa2a-268">**/api/holographic/mrc/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="5fa2a-269">Gibt die Liste der auf dem Gerät gespeicherten mixed Reality-Dateien</span><span class="sxs-lookup"><span data-stu-id="5fa2a-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="5fa2a-270">**/api/holographic/mrc/photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="5fa2a-271">Nimmt ein Foto mixed Reality und erstellt eine Datei auf dem Gerät</span><span class="sxs-lookup"><span data-stu-id="5fa2a-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="5fa2a-272">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-272">Parameters</span></span>
* <span data-ttu-id="5fa2a-273">Holo: Erfassen von Hologramme: "true" oder "false" (standardmäßig "false")</span><span class="sxs-lookup"><span data-stu-id="5fa2a-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="5fa2a-274">PV: Erfassung PV Kamera: "true" oder "false" (standardmäßig "false")</span><span class="sxs-lookup"><span data-stu-id="5fa2a-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="5fa2a-275">RenderFromCamera: (Gilt nur für HoloLens-2) Rendern aus Perspektive der Fotogalerie/Videokamera: "true" oder "false" (standardmäßig auf "true")</span><span class="sxs-lookup"><span data-stu-id="5fa2a-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="5fa2a-276">**/api/holographic/mrc/settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="5fa2a-277">Ruft gemischt den Standard tatsächlich Capture-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="5fa2a-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="5fa2a-278">**/api/holographic/mrc/settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="5fa2a-279">Legt kombiniert den Standard tatsächlich Capture-Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="5fa2a-280">Einige dieser Einstellungen werden auf MRC Foto und Erfassen des Systems angewendet.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="5fa2a-281">**/api/holographic/mrc/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="5fa2a-282">Ruft den Status der mixed Reality aufgezeichnet ("ausführen", "beendet")</span><span class="sxs-lookup"><span data-stu-id="5fa2a-282">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="5fa2a-283">**/API/holographic/MRC/Thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-283">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="5fa2a-284">Ruft die Miniaturansicht für die angegebene Datei.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-284">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="5fa2a-285">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-285">Parameters</span></span>
* <span data-ttu-id="5fa2a-286">Dateiname: Name, hex64 codiert, der die Datei, die für die die Miniaturansicht angefordert wird</span><span class="sxs-lookup"><span data-stu-id="5fa2a-286">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="5fa2a-287">**/api/holographic/mrc/video/control/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-287">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="5fa2a-288">Startet eine Aufzeichnung mixed reality</span><span class="sxs-lookup"><span data-stu-id="5fa2a-288">Starts a mixed reality recording</span></span>

<span data-ttu-id="5fa2a-289">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-289">Parameters</span></span>
* <span data-ttu-id="5fa2a-290">Holo: Erfassen von Hologramme: "true" oder "false" (standardmäßig "false")</span><span class="sxs-lookup"><span data-stu-id="5fa2a-290">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="5fa2a-291">PV: Erfassung PV Kamera: "true" oder "false" (standardmäßig "false")</span><span class="sxs-lookup"><span data-stu-id="5fa2a-291">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="5fa2a-292">MIC: Erfassung Mikrofon: "true" oder "false" (standardmäßig "false")</span><span class="sxs-lookup"><span data-stu-id="5fa2a-292">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="5fa2a-293">Loopback: Erfassen von app-Audio: "true" oder "false" (standardmäßig "false")</span><span class="sxs-lookup"><span data-stu-id="5fa2a-293">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="5fa2a-294">RenderFromCamera: (Gilt nur für HoloLens-2) Rendern aus Perspektive der Fotogalerie/Videokamera: "true" oder "false" (standardmäßig auf "true")</span><span class="sxs-lookup"><span data-stu-id="5fa2a-294">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="5fa2a-295">Vstab: Enable-videostabilisierung (gilt nur für HoloLens-2): "true" oder "false" (standardmäßig auf "true")</span><span class="sxs-lookup"><span data-stu-id="5fa2a-295">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="5fa2a-296">vstabbuffer: (Gilt nur für HoloLens-2) videostabilisierung Puffer Latenz: 0 bis 30 Frames (standardmäßig 15 Frames)</span><span class="sxs-lookup"><span data-stu-id="5fa2a-296">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="5fa2a-297">**/api/holographic/mrc/video/control/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-297">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="5fa2a-298">Beendet kombiniert die aktuelle Realität Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="5fa2a-298">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="5fa2a-299">Mixed Reality-Streaming</span><span class="sxs-lookup"><span data-stu-id="5fa2a-299">Mixed Reality Streaming</span></span>

<span data-ttu-id="5fa2a-300">HoloLens unterstützt die Livevorschau von mixed Reality über aufgeteilte Download von einem fragmentierte MP4-Dateien.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-300">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="5fa2a-301">Mixed Reality-Streams teilen den gleichen Satz von Parametern, die steuern, was erfasst werden:</span><span class="sxs-lookup"><span data-stu-id="5fa2a-301">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="5fa2a-302">Holo: Erfassen von Hologramme: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="5fa2a-302">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="5fa2a-303">PV: Erfassung PV Kamera: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="5fa2a-303">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="5fa2a-304">MIC: Erfassung Mikrofon: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="5fa2a-304">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="5fa2a-305">Loopback: Erfassen von app-Audio: "true" oder "false"</span><span class="sxs-lookup"><span data-stu-id="5fa2a-305">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="5fa2a-306">Wenn keine dieser Optionen angegeben werden:-Hologramme, Foto/Videokamera und app-Audio werden erfasst werden</span><span class="sxs-lookup"><span data-stu-id="5fa2a-306">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="5fa2a-307">Wenn angegeben werden: die Parameter nicht angegeben werden standardmäßig auf "false"</span><span class="sxs-lookup"><span data-stu-id="5fa2a-307">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="5fa2a-308">Optionale Parameter (gilt nur für HoloLens-2)</span><span class="sxs-lookup"><span data-stu-id="5fa2a-308">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="5fa2a-309">RenderFromCamera: Rendern aus Perspektive der Fotogalerie/Videokamera: "true" oder "false" (standardmäßig auf "true")</span><span class="sxs-lookup"><span data-stu-id="5fa2a-309">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="5fa2a-310">Vstab: Aktivieren von videostabilisierung: "true" oder "false" (standardmäßig "false")</span><span class="sxs-lookup"><span data-stu-id="5fa2a-310">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="5fa2a-311">Vstabbuffer: videostabilisierung Puffer Latenz: 0 bis 30 Frames (standardmäßig 15 Frames)</span><span class="sxs-lookup"><span data-stu-id="5fa2a-311">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="5fa2a-312">**/api/holographic/stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-312">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="5fa2a-313">Ein 1280x720p 30 BpS 5Mbit-Datenstrom.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-313">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="5fa2a-314">**/api/holographic/stream/live_high.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-314">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="5fa2a-315">Ein 1280x720p 30 BpS 5Mbit-Datenstrom.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="5fa2a-316">**/api/holographic/stream/live_med.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="5fa2a-317">Ein 854x480p 30 BpS 2.5Mbit-Datenstrom.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-317">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="5fa2a-318">**/api/holographic/stream/live_low.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-318">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="5fa2a-319">Ein 428x240p 15fps 0.6Mbit-Datenstrom.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-319">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="5fa2a-320">Netzwerk</span><span class="sxs-lookup"><span data-stu-id="5fa2a-320">Networking</span></span>

<span data-ttu-id="5fa2a-321">**/api/networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-321">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="5fa2a-322">Ruft die aktuelle IP-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="5fa2a-322">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="5fa2a-323">Informationen zum Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="5fa2a-323">OS Information</span></span>

<span data-ttu-id="5fa2a-324">**/api/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-324">**/api/os/info (GET)**</span></span>

<span data-ttu-id="5fa2a-325">Ruft Informationen zum Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="5fa2a-325">Gets operating system information</span></span>

<span data-ttu-id="5fa2a-326">**/api/os/machinename (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-326">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="5fa2a-327">Ruft den Computernamen ab</span><span class="sxs-lookup"><span data-stu-id="5fa2a-327">Gets the machine name</span></span>

<span data-ttu-id="5fa2a-328">**/api/os/machinename (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-328">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="5fa2a-329">Legt den Computernamen fest</span><span class="sxs-lookup"><span data-stu-id="5fa2a-329">Sets the machine name</span></span>

<span data-ttu-id="5fa2a-330">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-330">Parameters</span></span>
* <span data-ttu-id="5fa2a-331">Name: Neuen Namen des Computers hex64 codiert, um für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="5fa2a-331">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="5fa2a-332">Leistungsdaten</span><span class="sxs-lookup"><span data-stu-id="5fa2a-332">Performance data</span></span>

<span data-ttu-id="5fa2a-333">**/api/resourcemanager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-333">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="5fa2a-334">Gibt die Liste der ausgeführten Prozesse mit details</span><span class="sxs-lookup"><span data-stu-id="5fa2a-334">Returns the list of running processes with details</span></span>

<span data-ttu-id="5fa2a-335">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="5fa2a-335">Return data</span></span>
* <span data-ttu-id="5fa2a-336">JSON mit Liste der Prozesse und Details für jeden Prozess</span><span class="sxs-lookup"><span data-stu-id="5fa2a-336">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="5fa2a-337">**/api/resourcemanager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-337">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="5fa2a-338">Statistische Daten aus System Perf (e/a-Lese-/Schreibzugriff, speicherstatistiken usw.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-338">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="5fa2a-339">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="5fa2a-339">Return data</span></span>
* <span data-ttu-id="5fa2a-340">JSON mit Systeminformationen: CPU, GPU, Arbeitsspeicher, Netzwerk, e/a</span><span class="sxs-lookup"><span data-stu-id="5fa2a-340">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="5fa2a-341">Stromversorgung</span><span class="sxs-lookup"><span data-stu-id="5fa2a-341">Power</span></span>

<span data-ttu-id="5fa2a-342">**/api/power/battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-342">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="5fa2a-343">Ruft den aktuellen Zustand der Akkus</span><span class="sxs-lookup"><span data-stu-id="5fa2a-343">Gets the current battery state</span></span>

<span data-ttu-id="5fa2a-344">**/API/Power/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-344">**/api/power/state (GET)**</span></span>

<span data-ttu-id="5fa2a-345">Überprüft, ob das System in einen Energiesparmodus ist.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-345">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="5fa2a-346">Remotesteuerung</span><span class="sxs-lookup"><span data-stu-id="5fa2a-346">Remote Control</span></span>

<span data-ttu-id="5fa2a-347">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-347">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="5fa2a-348">Wird die Zielgerät neu gestartet</span><span class="sxs-lookup"><span data-stu-id="5fa2a-348">Restarts the target device</span></span>

<span data-ttu-id="5fa2a-349">**/api/control/shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-349">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="5fa2a-350">Das Gerät heruntergefahren</span><span class="sxs-lookup"><span data-stu-id="5fa2a-350">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="5fa2a-351">Task-Manager</span><span class="sxs-lookup"><span data-stu-id="5fa2a-351">Task Manager</span></span>

<span data-ttu-id="5fa2a-352">**/api/taskmanager/app (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-352">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="5fa2a-353">Beendet einen modernen Apps</span><span class="sxs-lookup"><span data-stu-id="5fa2a-353">Stops a modern app</span></span>

<span data-ttu-id="5fa2a-354">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-354">Parameters</span></span>
* <span data-ttu-id="5fa2a-355">Paket: Vollständigen Namen des app-Pakets, hex64 codiert</span><span class="sxs-lookup"><span data-stu-id="5fa2a-355">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="5fa2a-356">"forcestop": Erzwingen, dass alle Prozesse beendet (= Yes)</span><span class="sxs-lookup"><span data-stu-id="5fa2a-356">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="5fa2a-357">**/api/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-357">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="5fa2a-358">Startet einen modernen Apps</span><span class="sxs-lookup"><span data-stu-id="5fa2a-358">Starts a modern app</span></span>

<span data-ttu-id="5fa2a-359">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-359">Parameters</span></span>
* <span data-ttu-id="5fa2a-360">App-ID: PRAID der app zu starten, codiert hex64</span><span class="sxs-lookup"><span data-stu-id="5fa2a-360">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="5fa2a-361">Paket: Vollständigen Namen des app-Pakets, hex64 codiert</span><span class="sxs-lookup"><span data-stu-id="5fa2a-361">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="5fa2a-362">WiFi-Verwaltung</span><span class="sxs-lookup"><span data-stu-id="5fa2a-362">WiFi Management</span></span>

<span data-ttu-id="5fa2a-363">**/API/WiFi/Interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-363">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="5fa2a-364">Listet Drahtlosnetzwerk-Schnittstellen</span><span class="sxs-lookup"><span data-stu-id="5fa2a-364">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="5fa2a-365">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="5fa2a-365">Return data</span></span>
* <span data-ttu-id="5fa2a-366">Liste der drahtlosen Schnittstellen mit den Details (GUID, Beschreibung usw.).</span><span class="sxs-lookup"><span data-stu-id="5fa2a-366">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="5fa2a-367">**/api/wifi/network (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-367">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="5fa2a-368">Löscht ein Profil ein Netzwerk auf eine angegebene Schnittstelle zugeordnet</span><span class="sxs-lookup"><span data-stu-id="5fa2a-368">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="5fa2a-369">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-369">Parameters</span></span>
* <span data-ttu-id="5fa2a-370">Schnittstelle: Netzwerk-Guid der Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5fa2a-370">interface : network interface guid</span></span>
* <span data-ttu-id="5fa2a-371">Profil: Profilname</span><span class="sxs-lookup"><span data-stu-id="5fa2a-371">profile : profile name</span></span>

<span data-ttu-id="5fa2a-372">**/api/wifi/networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-372">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="5fa2a-373">Listet Drahtlosnetzwerke auf die angegebene Netzwerkschnittstelle</span><span class="sxs-lookup"><span data-stu-id="5fa2a-373">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="5fa2a-374">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-374">Parameters</span></span>
* <span data-ttu-id="5fa2a-375">Schnittstelle: Netzwerk-Guid der Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5fa2a-375">interface : network interface guid</span></span>

<span data-ttu-id="5fa2a-376">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="5fa2a-376">Return data</span></span>
* <span data-ttu-id="5fa2a-377">Liste der Drahtlosnetzwerke finden Sie auf die Netzwerkschnittstelle mit details</span><span class="sxs-lookup"><span data-stu-id="5fa2a-377">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="5fa2a-378">**/api/wifi/network (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-378">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="5fa2a-379">Eine Verbindung herstellt oder trennt die Verbindung mit einem Netzwerk für die angegebene Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5fa2a-379">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="5fa2a-380">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-380">Parameters</span></span>
* <span data-ttu-id="5fa2a-381">Schnittstelle: Netzwerk-Guid der Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5fa2a-381">interface : network interface guid</span></span>
* <span data-ttu-id="5fa2a-382">SSID: Ssid, hex64 codiert sind, klicken Sie zum Herstellen einer Verbindung mit</span><span class="sxs-lookup"><span data-stu-id="5fa2a-382">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="5fa2a-383">Op: herstellen oder trennen</span><span class="sxs-lookup"><span data-stu-id="5fa2a-383">op : connect or disconnect</span></span>
* <span data-ttu-id="5fa2a-384">CreateProfile: Ja oder Nein</span><span class="sxs-lookup"><span data-stu-id="5fa2a-384">createprofile : yes or no</span></span>
* <span data-ttu-id="5fa2a-385">Schlüssel: shared Key, hex64 codiert</span><span class="sxs-lookup"><span data-stu-id="5fa2a-385">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="5fa2a-386">Windows-Leistungsaufzeichnung</span><span class="sxs-lookup"><span data-stu-id="5fa2a-386">Windows Performance Recorder</span></span>

<span data-ttu-id="5fa2a-387">**/api/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-387">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="5fa2a-388">Lädt ein WPR-Profil, und startet die Protokollierung mithilfe des hochgeladenen Profils.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-388">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="5fa2a-389">Nutzlast</span><span class="sxs-lookup"><span data-stu-id="5fa2a-389">Payload</span></span>
* <span data-ttu-id="5fa2a-390">Mehrteilige konformen http-Text</span><span class="sxs-lookup"><span data-stu-id="5fa2a-390">multi-part conforming http body</span></span>

<span data-ttu-id="5fa2a-391">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="5fa2a-391">Return data</span></span>
* <span data-ttu-id="5fa2a-392">Gibt den WPR-Sitzungsstatus zurück.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-392">Returns the WPR session status.</span></span>

<span data-ttu-id="5fa2a-393">**/api/wpr/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-393">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="5fa2a-394">Ruft den Status der Sitzung WPR ab</span><span class="sxs-lookup"><span data-stu-id="5fa2a-394">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="5fa2a-395">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="5fa2a-395">Return data</span></span>
* <span data-ttu-id="5fa2a-396">WPR Sitzungsstatus.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-396">WPR session status.</span></span>

<span data-ttu-id="5fa2a-397">**/api/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-397">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="5fa2a-398">Beendet eine Ablaufverfolgungssitzung WPR (Leistung)</span><span class="sxs-lookup"><span data-stu-id="5fa2a-398">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="5fa2a-399">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="5fa2a-399">Return data</span></span>
* <span data-ttu-id="5fa2a-400">Gibt zurück, die ETL-Datei</span><span class="sxs-lookup"><span data-stu-id="5fa2a-400">Returns the trace ETL file</span></span>

<span data-ttu-id="5fa2a-401">**/api/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="5fa2a-401">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="5fa2a-402">Startet eine WPR (Leistung), die Ablaufverfolgung von Sitzungen</span><span class="sxs-lookup"><span data-stu-id="5fa2a-402">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="5fa2a-403">Parameter</span><span class="sxs-lookup"><span data-stu-id="5fa2a-403">Parameters</span></span>
* <span data-ttu-id="5fa2a-404">Profil: Profilname.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-404">profile : Profile name.</span></span> <span data-ttu-id="5fa2a-405">Verfügbare Profile werden in perfprofiles/profiles.json gespeichert.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-405">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="5fa2a-406">Zurückgeben von Daten</span><span class="sxs-lookup"><span data-stu-id="5fa2a-406">Return data</span></span>
* <span data-ttu-id="5fa2a-407">Beim Start wird der WPR-Sitzung-Status zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="5fa2a-407">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="5fa2a-408">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="5fa2a-408">See also</span></span>
* [<span data-ttu-id="5fa2a-409">Verwenden des Windows-Geräteportals</span><span class="sxs-lookup"><span data-stu-id="5fa2a-409">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="5fa2a-410">Device Portal-Core-API-Referenz (UWP)</span><span class="sxs-lookup"><span data-stu-id="5fa2a-410">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
