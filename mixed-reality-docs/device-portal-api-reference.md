---
title: Referenz zur Geräte Portal-API
description: API-Referenz für das Windows-Geräte Portal auf hololens
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Hololens, Windows-Geräte Portal, API
ms.openlocfilehash: 236de35c2c736fc5a0289b7be1f1548f0a08fa26
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278238"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="006ac-104">Referenz zur Geräte Portal-API</span><span class="sxs-lookup"><span data-stu-id="006ac-104">Device portal API reference</span></span>

<span data-ttu-id="006ac-105">Alles im [Windows-Geräte Portal](using-the-windows-device-portal.md) baut auf der Rest-API auf, mit der Sie auf die Daten zugreifen und Ihr Gerät Programm gesteuert steuern können.</span><span class="sxs-lookup"><span data-stu-id="006ac-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="006ac-106">App-Verlagerung</span><span class="sxs-lookup"><span data-stu-id="006ac-106">App deloyment</span></span>

<span data-ttu-id="006ac-107">**/API/APP/packagemanager/Package (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="006ac-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="006ac-108">Deinstalliert eine APP</span><span class="sxs-lookup"><span data-stu-id="006ac-108">Uninstalls an app</span></span>

<span data-ttu-id="006ac-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-109">Parameters</span></span>
* <span data-ttu-id="006ac-110">Package: der Dateiname des Pakets, das deinstalliert werden soll.</span><span class="sxs-lookup"><span data-stu-id="006ac-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="006ac-111">**/API/APP/packagemanager/Package (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="006ac-112">Installiert eine APP</span><span class="sxs-lookup"><span data-stu-id="006ac-112">Installs an App</span></span>

<span data-ttu-id="006ac-113">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-113">Parameters</span></span>
* <span data-ttu-id="006ac-114">Package: der Dateiname des zu installierenden Pakets.</span><span class="sxs-lookup"><span data-stu-id="006ac-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="006ac-115">Payload</span><span class="sxs-lookup"><span data-stu-id="006ac-115">Payload</span></span>
* <span data-ttu-id="006ac-116">Mehrteilige konforme HTTP-Text</span><span class="sxs-lookup"><span data-stu-id="006ac-116">multi-part conforming http body</span></span>

<span data-ttu-id="006ac-117">**/API/APP/packagemanager/Packages (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="006ac-118">Hiermit wird die Liste der installierten apps auf dem System mit Details abgerufen.</span><span class="sxs-lookup"><span data-stu-id="006ac-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="006ac-119">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="006ac-119">Return data</span></span>
* <span data-ttu-id="006ac-120">Liste der installierten Pakete mit Details</span><span class="sxs-lookup"><span data-stu-id="006ac-120">List of installed packages with details</span></span>

<span data-ttu-id="006ac-121">**/API/APP/packagemanager/State (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="006ac-122">Hiermit wird der Status der Installation in Progress-App abgerufen.</span><span class="sxs-lookup"><span data-stu-id="006ac-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="006ac-123">Absturzabbildsammlung</span><span class="sxs-lookup"><span data-stu-id="006ac-123">Dump collection</span></span>

<span data-ttu-id="006ac-124">**/API/Debug/Dump/Usermode/CrashControl (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="006ac-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="006ac-125">Deaktiviert die Absturz Abbild Erfassung für eine Sideload-app.</span><span class="sxs-lookup"><span data-stu-id="006ac-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="006ac-126">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-126">Parameters</span></span>
* <span data-ttu-id="006ac-127">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="006ac-127">packageFullname : package name</span></span>

<span data-ttu-id="006ac-128">**/API/Debug/Dump/Usermode/CrashControl (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="006ac-129">Ruft Einstellungen für die Absturz Abbild Erfassung von Sideload-apps ab</span><span class="sxs-lookup"><span data-stu-id="006ac-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="006ac-130">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-130">Parameters</span></span>
* <span data-ttu-id="006ac-131">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="006ac-131">packageFullname : package name</span></span>

<span data-ttu-id="006ac-132">**/API/Debug/Dump/Usermode/CrashControl (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="006ac-133">Aktiviert und legt Sicherungs Steuerungseinstellungen für eine per Sideload übertragene App fest.</span><span class="sxs-lookup"><span data-stu-id="006ac-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="006ac-134">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-134">Parameters</span></span>
* <span data-ttu-id="006ac-135">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="006ac-135">packageFullname : package name</span></span>

<span data-ttu-id="006ac-136">**/API/Debug/Dump/Usermode/crashdump (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="006ac-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="006ac-137">Löscht einen Absturz Abbild für eine Sideload-app.</span><span class="sxs-lookup"><span data-stu-id="006ac-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="006ac-138">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-138">Parameters</span></span>
* <span data-ttu-id="006ac-139">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="006ac-139">packageFullname : package name</span></span>
* <span data-ttu-id="006ac-140">Dateiname: Name der Sicherungsdatei</span><span class="sxs-lookup"><span data-stu-id="006ac-140">fileName : dump file name</span></span>

<span data-ttu-id="006ac-141">**/API/Debug/Dump/Usermode/crashdump (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="006ac-142">Ruft ein Absturz Abbild für eine per Sideload übertragene App ab.</span><span class="sxs-lookup"><span data-stu-id="006ac-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="006ac-143">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-143">Parameters</span></span>
* <span data-ttu-id="006ac-144">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="006ac-144">packageFullname : package name</span></span>
* <span data-ttu-id="006ac-145">Dateiname: Name der Sicherungsdatei</span><span class="sxs-lookup"><span data-stu-id="006ac-145">fileName : dump file name</span></span>

<span data-ttu-id="006ac-146">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="006ac-146">Return data</span></span>
* <span data-ttu-id="006ac-147">Dumpdatei.</span><span class="sxs-lookup"><span data-stu-id="006ac-147">Dump file.</span></span> <span data-ttu-id="006ac-148">Überprüfen mit WinDbg oder Visual Studio</span><span class="sxs-lookup"><span data-stu-id="006ac-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="006ac-149">**/API/Debug/Dump/Usermode/Dumps (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="006ac-150">Gibt eine Liste aller Absturz Abbilder für Sideload-apps zurück.</span><span class="sxs-lookup"><span data-stu-id="006ac-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="006ac-151">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="006ac-151">Return data</span></span>
* <span data-ttu-id="006ac-152">Liste der Absturz Abbilder pro Seite geladener apps</span><span class="sxs-lookup"><span data-stu-id="006ac-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="006ac-153">ETW</span><span class="sxs-lookup"><span data-stu-id="006ac-153">ETW</span></span>

<span data-ttu-id="006ac-154">**/API/etw/Providers (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="006ac-155">Listet registrierte Anbieter auf.</span><span class="sxs-lookup"><span data-stu-id="006ac-155">Enumerates registered providers</span></span>

<span data-ttu-id="006ac-156">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="006ac-156">Return data</span></span>
* <span data-ttu-id="006ac-157">Liste der Anbieter, Anzeige Name und GUID</span><span class="sxs-lookup"><span data-stu-id="006ac-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="006ac-158">**/API/etw/Session/Realtime (Get/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="006ac-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="006ac-159">Erstellt eine ETW-Sitzung in Echtzeit. verwaltet über einen WebSocket.</span><span class="sxs-lookup"><span data-stu-id="006ac-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="006ac-160">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="006ac-160">Return data</span></span>
* <span data-ttu-id="006ac-161">ETW-Ereignisse von aktivierten Anbietern</span><span class="sxs-lookup"><span data-stu-id="006ac-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="006ac-162">Holographic – Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="006ac-162">Holographic OS</span></span>

<span data-ttu-id="006ac-163">**/API/Holographic/OS/etw/customproviders (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="006ac-164">Gibt eine Liste von hololens-spezifischen etw-Anbietern zurück, die nicht beim System registriert sind.</span><span class="sxs-lookup"><span data-stu-id="006ac-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="006ac-165">**/API/Holographic/OS/Services (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="006ac-166">Gibt die Zustände aller Dienste zurück, die ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="006ac-166">Returns the states of all services running.</span></span>

<span data-ttu-id="006ac-167">**/API/Holographic/OS/Settings/IPD (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="006ac-168">Ruft die gespeicherte IPD (interpupranäre Entfernung) in Millimeter ab.</span><span class="sxs-lookup"><span data-stu-id="006ac-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="006ac-169">**/API/Holographic/OS/Settings/IPD (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="006ac-170">Legt die IPD fest.</span><span class="sxs-lookup"><span data-stu-id="006ac-170">Sets the IPD</span></span>

<span data-ttu-id="006ac-171">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-171">Parameters</span></span>
* <span data-ttu-id="006ac-172">IPD: neuer IPD-Wert, der in Millimeter festgelegt werden soll</span><span class="sxs-lookup"><span data-stu-id="006ac-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="006ac-173">**/API/Holographic/OS/Webmanagement/Settings/HTTPS (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="006ac-174">Abrufen der HTTPS-Anforderungen für das Geräteportal</span><span class="sxs-lookup"><span data-stu-id="006ac-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="006ac-175">**/API/Holographic/OS/Webmanagement/Settings/HTTPS (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="006ac-176">Legt die HTTPS-Anforderungen für das Geräte Portal fest.</span><span class="sxs-lookup"><span data-stu-id="006ac-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="006ac-177">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-177">Parameters</span></span>
* <span data-ttu-id="006ac-178">erforderlich: Ja, Nein oder Standard</span><span class="sxs-lookup"><span data-stu-id="006ac-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="006ac-179">Holografische Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="006ac-179">Holographic Perception</span></span>

<span data-ttu-id="006ac-180">**/API/Holographic/perception/Client (Get/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="006ac-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="006ac-181">Akzeptiert WebSocket-Upgrades und führt einen perception-Client aus, der Updates bei 30 fps sendet.</span><span class="sxs-lookup"><span data-stu-id="006ac-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="006ac-182">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-182">Parameters</span></span>
* <span data-ttu-id="006ac-183">clientmode: "aktiv" erzwingt den visuellen Überwachungsmodus, wenn er nicht passiv festgelegt werden kann.</span><span class="sxs-lookup"><span data-stu-id="006ac-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="006ac-184">Holographic-Therme</span><span class="sxs-lookup"><span data-stu-id="006ac-184">Holographic Thermal</span></span>

<span data-ttu-id="006ac-185">**/API/Holographic/Thermal/Stage (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="006ac-186">Die wärmestufe des Geräts erhalten (0 normal, 1 warm, 2 kritisch)</span><span class="sxs-lookup"><span data-stu-id="006ac-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="006ac-187">Wahrnehmungs Simulations-Steuerelement</span><span class="sxs-lookup"><span data-stu-id="006ac-187">Perception Simulation Control</span></span>

<span data-ttu-id="006ac-188">**/API/Holographic/Simulation/Control/Mode (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="006ac-189">Abrufen des Simulationsmodus</span><span class="sxs-lookup"><span data-stu-id="006ac-189">Get the simulation mode</span></span>

<span data-ttu-id="006ac-190">**/API/Holographic/Simulation/Control/Mode (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="006ac-191">Festlegen des Simulationsmodus</span><span class="sxs-lookup"><span data-stu-id="006ac-191">Set the simulation mode</span></span>

<span data-ttu-id="006ac-192">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-192">Parameters</span></span>
* <span data-ttu-id="006ac-193">Mode: Simulationsmodus: Standard, Simulation, Remote, Legacy</span><span class="sxs-lookup"><span data-stu-id="006ac-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="006ac-194">**/API/Holographic/Simulation/Control/Stream (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="006ac-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="006ac-195">Löscht einen Steuerungsdaten Strom.</span><span class="sxs-lookup"><span data-stu-id="006ac-195">Delete a control stream.</span></span>

<span data-ttu-id="006ac-196">**/API/Holographic/Simulation/Control/Stream (Get/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="006ac-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="006ac-197">Öffnen Sie eine websocketverbindung für einen Steuerungsdaten Strom.</span><span class="sxs-lookup"><span data-stu-id="006ac-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="006ac-198">**/API/Holographic/Simulation/Control/Stream (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="006ac-199">Erstellen Sie einen Steuerungsdaten Strom (Priorität ist erforderlich), oder stellen Sie Daten in einem erstellten Stream bereit (streamid erforderlich).</span><span class="sxs-lookup"><span data-stu-id="006ac-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="006ac-200">Es wird erwartet, dass für die Daten der Typ "Application/Octett-Stream" festgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="006ac-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="006ac-201">Wiedergabe von Wahrnehmungs Simulationen</span><span class="sxs-lookup"><span data-stu-id="006ac-201">Perception Simulation Playback</span></span>

<span data-ttu-id="006ac-202">**/API/Holographic/Simulation/Playback/File (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="006ac-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="006ac-203">Löschen Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="006ac-203">Delete a recording.</span></span>

<span data-ttu-id="006ac-204">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-204">Parameters</span></span>
* <span data-ttu-id="006ac-205">Aufzeichnung: Name der zu löschenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="006ac-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="006ac-206">**/API/Holographic/Simulation/Playback/File (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="006ac-207">Hochladen einer Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="006ac-207">Upload a recording.</span></span>

<span data-ttu-id="006ac-208">**/API/Holographic/Simulation/Playback/Files (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="006ac-209">Alle Aufzeichnungen erhalten.</span><span class="sxs-lookup"><span data-stu-id="006ac-209">Get all recordings.</span></span>

<span data-ttu-id="006ac-210">**/API/Holographic/Simulation/Playback/Session (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="006ac-211">Gibt den aktuellen Wiedergabe Zustand einer Aufzeichnung an.</span><span class="sxs-lookup"><span data-stu-id="006ac-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="006ac-212">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-212">Parameters</span></span>
* <span data-ttu-id="006ac-213">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="006ac-213">recording : Name of recording.</span></span>

<span data-ttu-id="006ac-214">**/API/Holographic/Simulation/Playback/Session/File (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="006ac-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="006ac-215">Entladen Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="006ac-215">Unload a recording.</span></span>

<span data-ttu-id="006ac-216">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-216">Parameters</span></span>
* <span data-ttu-id="006ac-217">Aufzeichnung: Name der zu entladenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="006ac-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="006ac-218">**/API/Holographic/Simulation/Playback/Session/File (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="006ac-219">Laden Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="006ac-219">Load a recording.</span></span>

<span data-ttu-id="006ac-220">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-220">Parameters</span></span>
* <span data-ttu-id="006ac-221">Aufzeichnung: Name der zu ladenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="006ac-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="006ac-222">**/API/Holographic/Simulation/Playback/Session/Files (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="006ac-223">Alle geladenen Aufzeichnungen erhalten.</span><span class="sxs-lookup"><span data-stu-id="006ac-223">Get all loaded recordings.</span></span>

<span data-ttu-id="006ac-224">**/API/Holographic/Simulation/Playback/Session/Pause (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="006ac-225">Hält eine Aufzeichnung an.</span><span class="sxs-lookup"><span data-stu-id="006ac-225">Pause a recording.</span></span>

<span data-ttu-id="006ac-226">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-226">Parameters</span></span>
* <span data-ttu-id="006ac-227">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="006ac-227">recording : Name of recording.</span></span>

<span data-ttu-id="006ac-228">**/API/Holographic/Simulation/Playback/Session/Play (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="006ac-229">Wiedergabe einer Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="006ac-229">Play a recording.</span></span>

<span data-ttu-id="006ac-230">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-230">Parameters</span></span>
* <span data-ttu-id="006ac-231">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="006ac-231">recording : Name of recording.</span></span>

<span data-ttu-id="006ac-232">**/API/Holographic/Simulation/Playback/Session/Stop (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="006ac-233">Beendet eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="006ac-233">Stop a recording.</span></span>

<span data-ttu-id="006ac-234">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-234">Parameters</span></span>
* <span data-ttu-id="006ac-235">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="006ac-235">recording : Name of recording.</span></span>

<span data-ttu-id="006ac-236">**/API/Holographic/Simulation/Playback/Session/Types (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="006ac-237">Datentypen in einer geladenen Aufzeichnung erhalten.</span><span class="sxs-lookup"><span data-stu-id="006ac-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="006ac-238">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-238">Parameters</span></span>
* <span data-ttu-id="006ac-239">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="006ac-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="006ac-240">Erfassung von Wahrnehmungs Simulationen</span><span class="sxs-lookup"><span data-stu-id="006ac-240">Perception Simulation Recording</span></span>

<span data-ttu-id="006ac-241">**/API/Holographic/Simulation/Recording/Start (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="006ac-242">Startet eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="006ac-242">Start a recording.</span></span> <span data-ttu-id="006ac-243">Nur eine einzelne Aufzeichnung kann gleichzeitig aktiv sein.</span><span class="sxs-lookup"><span data-stu-id="006ac-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="006ac-244">Eine der Köpfe, Hände, spatialmapping oder Umgebung muss festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="006ac-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="006ac-245">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-245">Parameters</span></span>
* <span data-ttu-id="006ac-246">Head: Legen Sie auf 1 fest, um Head-Daten aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="006ac-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="006ac-247">Hands: wird auf 1 festgelegt, um die Daten aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="006ac-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="006ac-248">spatialmapping: auf 1 festgelegt, um die räumliche Zuordnung aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="006ac-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="006ac-249">Umgebung: Legen Sie auf 1 fest, um Umgebungs Daten aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="006ac-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="006ac-250">Name: der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="006ac-250">name : Name of the recording.</span></span>
* <span data-ttu-id="006ac-251">singlespatialmappingframe: wird auf 1 festgelegt, um nur einen einzelnen räumlichen zuordnungsframe aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="006ac-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="006ac-252">**/API/Holographic/Simulation/Recording/Status (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="006ac-253">Aufzeichnungsstatus erhalten.</span><span class="sxs-lookup"><span data-stu-id="006ac-253">Get recording state.</span></span>

<span data-ttu-id="006ac-254">**/API/Holographic/Simulation/Recording/Stop (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="006ac-255">Hält die aktuelle Aufzeichnung an.</span><span class="sxs-lookup"><span data-stu-id="006ac-255">Stop the current recording.</span></span> <span data-ttu-id="006ac-256">Die Aufzeichnung wird als Datei zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="006ac-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="006ac-257">Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="006ac-257">Mixed Reality Capture</span></span>

<span data-ttu-id="006ac-258">**/API/Holographic/MRC/File (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="006ac-259">Hiermit wird eine gemischte Reality-Datei vom Gerät heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="006ac-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="006ac-260">Verwenden Sie den OP = Stream-Abfrage Parameter für das Streaming.</span><span class="sxs-lookup"><span data-stu-id="006ac-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="006ac-261">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-261">Parameters</span></span>
* <span data-ttu-id="006ac-262">Dateiname: Name, hex64-codiert, der einzurufenden Videodatei</span><span class="sxs-lookup"><span data-stu-id="006ac-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="006ac-263">OP: Stream</span><span class="sxs-lookup"><span data-stu-id="006ac-263">op : stream</span></span>

<span data-ttu-id="006ac-264">**/API/Holographic/MRC/File (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="006ac-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="006ac-265">Löscht eine gemischte Reality-Aufzeichnung auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="006ac-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="006ac-266">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-266">Parameters</span></span>
* <span data-ttu-id="006ac-267">Dateiname: Name, hex64-codiert, der zu löschenden Datei</span><span class="sxs-lookup"><span data-stu-id="006ac-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="006ac-268">**/API/Holographic/MRC/Files (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="006ac-269">Gibt die Liste der Mixed Reality-Dateien zurück, die auf dem Gerät gespeichert sind</span><span class="sxs-lookup"><span data-stu-id="006ac-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="006ac-270">**/API/Holographic/MRC/Photo (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="006ac-271">Nimmt ein gemischtes Reality-Foto und erstellt eine Datei auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="006ac-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="006ac-272">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-272">Parameters</span></span>
* <span data-ttu-id="006ac-273">hololens: Erfassungs holograms: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="006ac-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="006ac-274">PV: Erfassen der PV-Kamera: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="006ac-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="006ac-275">Renderfromcamera: (hololens 2) renderingaus Perspektive der Foto-/Videokamera: true oder false (Standardwert: true)</span><span class="sxs-lookup"><span data-stu-id="006ac-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="006ac-276">**/API/Holographic/MRC/Settings (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="006ac-277">Ruft die Standardeinstellungen für die gemischte Realität-Erfassung ab.</span><span class="sxs-lookup"><span data-stu-id="006ac-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="006ac-278">**/API/Holographic/MRC/Settings (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="006ac-279">Legt die Standardeinstellungen für die gemischte Reality-Erfassung fest.</span><span class="sxs-lookup"><span data-stu-id="006ac-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="006ac-280">Einige dieser Einstellungen werden auf das MRC-Foto und die Video Erfassung des Systems angewendet.</span><span class="sxs-lookup"><span data-stu-id="006ac-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="006ac-281">**/API/Holographic/MRC/Status (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="006ac-282">Ruft den Status der aufgezeichnete gemischten Realität ab (wird ausgeführt, beendet).</span><span class="sxs-lookup"><span data-stu-id="006ac-282">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="006ac-283">**/API/Holographic/MRC/Thumbnail (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-283">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="006ac-284">Ruft das Miniaturbild für die angegebene Datei ab.</span><span class="sxs-lookup"><span data-stu-id="006ac-284">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="006ac-285">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-285">Parameters</span></span>
* <span data-ttu-id="006ac-286">Dateiname: Name, hex64-codiert, der Datei, für die die Miniaturansicht angefordert wird</span><span class="sxs-lookup"><span data-stu-id="006ac-286">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="006ac-287">**/API/Holographic/MRC/Video/Control/Start (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-287">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="006ac-288">Startet eine gemischte Reality-Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="006ac-288">Starts a mixed reality recording</span></span>

<span data-ttu-id="006ac-289">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-289">Parameters</span></span>
* <span data-ttu-id="006ac-290">hololens: Erfassungs holograms: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="006ac-290">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="006ac-291">PV: Erfassen der PV-Kamera: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="006ac-291">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="006ac-292">MIC: Mikrofon erfassen: true oder false (standardmäßig false)</span><span class="sxs-lookup"><span data-stu-id="006ac-292">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="006ac-293">Loopback: App-Audioerfassung: true oder false (standardmäßig false)</span><span class="sxs-lookup"><span data-stu-id="006ac-293">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="006ac-294">Renderfromcamera: (hololens 2) renderingaus Perspektive der Foto-/Videokamera: true oder false (Standardwert: true)</span><span class="sxs-lookup"><span data-stu-id="006ac-294">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="006ac-295">Vstab: (nur hololens 2) Videostabilisierung aktivieren: true oder false (Standardwert: true)</span><span class="sxs-lookup"><span data-stu-id="006ac-295">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="006ac-296">vstabbuffer: (hololens 2), Video Stabilisierungs Puffer Latenz: 0 bis 30 Frames (standardmäßig 15 Frames)</span><span class="sxs-lookup"><span data-stu-id="006ac-296">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="006ac-297">**/API/Holographic/MRC/Video/Control/Stop (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-297">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="006ac-298">Beendet die aktuelle gemischte Reality-Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="006ac-298">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="006ac-299">Streaming mit gemischter Realität</span><span class="sxs-lookup"><span data-stu-id="006ac-299">Mixed Reality Streaming</span></span>

<span data-ttu-id="006ac-300">Hololens unterstützt die Live Vorschau von Mixed Reality über einen segmentierten Download einer fragmentierten MP4-Datei.</span><span class="sxs-lookup"><span data-stu-id="006ac-300">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="006ac-301">Gemischte Reality-Streams verwenden denselben Satz von Parametern, um zu steuern, was aufgezeichnet wird:</span><span class="sxs-lookup"><span data-stu-id="006ac-301">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="006ac-302">hololens: Erfassungs holograms: true oder false</span><span class="sxs-lookup"><span data-stu-id="006ac-302">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="006ac-303">PV: Erfassen der PV-Kamera: true oder false</span><span class="sxs-lookup"><span data-stu-id="006ac-303">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="006ac-304">MIC: Mikrofon erfassen: true oder false</span><span class="sxs-lookup"><span data-stu-id="006ac-304">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="006ac-305">Loopback: App-Audioerfassung: true oder false</span><span class="sxs-lookup"><span data-stu-id="006ac-305">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="006ac-306">Wenn keines dieser Angaben angegeben ist: holograms, Foto-/Videokamera und App-Audiodaten werden aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="006ac-306">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="006ac-307">Wenn eine Angabe festgelegt ist: die nicht angegebenen Parameter werden standardmäßig auf false festgelegt.</span><span class="sxs-lookup"><span data-stu-id="006ac-307">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="006ac-308">Optionale Parameter (nur hololens 2)</span><span class="sxs-lookup"><span data-stu-id="006ac-308">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="006ac-309">Renderfromcamera: Rendering aus Perspektive der Foto-/Videokamera: true oder false (Standardwert ist true)</span><span class="sxs-lookup"><span data-stu-id="006ac-309">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="006ac-310">Vstab: Videostabilisierung aktivieren: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="006ac-310">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="006ac-311">vstabbuffer: Puffer Wartezeit für Videostabilisierung: zwischen 0 und 30 Frames (standardmäßig 15 Frames)</span><span class="sxs-lookup"><span data-stu-id="006ac-311">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="006ac-312">**/API/Holographic/Stream/Live.MP4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-312">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="006ac-313">Ein-Datenstrom von 1280x720p 30 fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="006ac-313">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="006ac-314">**/API/Holographic/Stream/live_high. MP4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-314">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="006ac-315">Ein-Datenstrom von 1280x720p 30 fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="006ac-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="006ac-316">**/API/Holographic/Stream/live_med. MP4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="006ac-317">Ein 854x480p 30 fps 2.5 MBit-Stream.</span><span class="sxs-lookup"><span data-stu-id="006ac-317">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="006ac-318">**/API/Holographic/Stream/live_low. MP4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-318">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="006ac-319">Ein 428x240 p 15fps 0.6-MBit-Stream.</span><span class="sxs-lookup"><span data-stu-id="006ac-319">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="006ac-320">Netzwerk</span><span class="sxs-lookup"><span data-stu-id="006ac-320">Networking</span></span>

<span data-ttu-id="006ac-321">**/API/Networking/ipconfig (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-321">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="006ac-322">Ruft die aktuelle IP-Konfiguration ab.</span><span class="sxs-lookup"><span data-stu-id="006ac-322">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="006ac-323">Betriebssysteminformationen</span><span class="sxs-lookup"><span data-stu-id="006ac-323">OS Information</span></span>

<span data-ttu-id="006ac-324">**/API/OS/Info (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-324">**/api/os/info (GET)**</span></span>

<span data-ttu-id="006ac-325">Ruft Betriebssysteminformationen ab.</span><span class="sxs-lookup"><span data-stu-id="006ac-325">Gets operating system information</span></span>

<span data-ttu-id="006ac-326">**/API/OS/MachineName (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-326">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="006ac-327">Ruft den Computernamen ab.</span><span class="sxs-lookup"><span data-stu-id="006ac-327">Gets the machine name</span></span>

<span data-ttu-id="006ac-328">**/API/OS/MachineName (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-328">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="006ac-329">Legt den Computernamen fest.</span><span class="sxs-lookup"><span data-stu-id="006ac-329">Sets the machine name</span></span>

<span data-ttu-id="006ac-330">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-330">Parameters</span></span>
* <span data-ttu-id="006ac-331">Name: neuer Computername, hex64-codiert, festgelegt auf</span><span class="sxs-lookup"><span data-stu-id="006ac-331">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="006ac-332">Leistungsdaten</span><span class="sxs-lookup"><span data-stu-id="006ac-332">Performance data</span></span>

<span data-ttu-id="006ac-333">**/API/ResourceManager/Processes (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-333">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="006ac-334">Gibt die Liste der laufenden Prozesse mit Details zurück.</span><span class="sxs-lookup"><span data-stu-id="006ac-334">Returns the list of running processes with details</span></span>

<span data-ttu-id="006ac-335">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="006ac-335">Return data</span></span>
* <span data-ttu-id="006ac-336">JSON mit einer Liste der Prozesse und Details für jeden Prozess</span><span class="sxs-lookup"><span data-stu-id="006ac-336">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="006ac-337">**/API/ResourceManager/systemperf (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-337">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="006ac-338">Gibt die System Leistungsstatistik (e/a-Lese-/Schreibvorgänge, Speicher Statistiken usw.) zurück.</span><span class="sxs-lookup"><span data-stu-id="006ac-338">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="006ac-339">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="006ac-339">Return data</span></span>
* <span data-ttu-id="006ac-340">JSON mit Systeminformationen: CPU, GPU, Arbeitsspeicher, Netzwerk, e/a</span><span class="sxs-lookup"><span data-stu-id="006ac-340">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="006ac-341">Leistung</span><span class="sxs-lookup"><span data-stu-id="006ac-341">Power</span></span>

<span data-ttu-id="006ac-342">**/API/Power/Battery (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-342">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="006ac-343">Ruft den aktuellen Akku Zustand ab.</span><span class="sxs-lookup"><span data-stu-id="006ac-343">Gets the current battery state</span></span>

<span data-ttu-id="006ac-344">**/API/Power/State (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-344">**/api/power/state (GET)**</span></span>

<span data-ttu-id="006ac-345">Prüft, ob sich das System in einem niedrigen Energiezustand befindet</span><span class="sxs-lookup"><span data-stu-id="006ac-345">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="006ac-346">Remotesteuerung</span><span class="sxs-lookup"><span data-stu-id="006ac-346">Remote Control</span></span>

<span data-ttu-id="006ac-347">**/API/Control/Restart (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-347">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="006ac-348">Startet das Zielgerät neu.</span><span class="sxs-lookup"><span data-stu-id="006ac-348">Restarts the target device</span></span>

<span data-ttu-id="006ac-349">**/API/Control/Shutdown (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-349">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="006ac-350">Fährt das Zielgerät herunter.</span><span class="sxs-lookup"><span data-stu-id="006ac-350">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="006ac-351">Task-Manager</span><span class="sxs-lookup"><span data-stu-id="006ac-351">Task Manager</span></span>

<span data-ttu-id="006ac-352">**/API/Taskmanager/app (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="006ac-352">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="006ac-353">Beendet eine moderne App</span><span class="sxs-lookup"><span data-stu-id="006ac-353">Stops a modern app</span></span>

<span data-ttu-id="006ac-354">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-354">Parameters</span></span>
* <span data-ttu-id="006ac-355">Package: vollständiger Name des App-Pakets, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="006ac-355">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="006ac-356">forcestop: erzwingen, dass alle Prozesse beendet werden (= yes)</span><span class="sxs-lookup"><span data-stu-id="006ac-356">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="006ac-357">**/API/Taskmanager/app (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-357">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="006ac-358">Startet eine moderne App</span><span class="sxs-lookup"><span data-stu-id="006ac-358">Starts a modern app</span></span>

<span data-ttu-id="006ac-359">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-359">Parameters</span></span>
* <span data-ttu-id="006ac-360">AppID: Praid der zu startenden APP, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="006ac-360">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="006ac-361">Package: vollständiger Name des App-Pakets, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="006ac-361">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="006ac-362">WiFi-Verwaltung</span><span class="sxs-lookup"><span data-stu-id="006ac-362">WiFi Management</span></span>

<span data-ttu-id="006ac-363">**/API/WiFi/Interfaces (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-363">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="006ac-364">Listet drahtlose Netzwerkschnittstellen auf.</span><span class="sxs-lookup"><span data-stu-id="006ac-364">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="006ac-365">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="006ac-365">Return data</span></span>
* <span data-ttu-id="006ac-366">Liste der drahtlos Schnittstellen mit Details (GUID, Beschreibung usw.)</span><span class="sxs-lookup"><span data-stu-id="006ac-366">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="006ac-367">**/API/WiFi/Network (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="006ac-367">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="006ac-368">Löscht ein Profil, das einem Netzwerk in einer angegebenen Schnittstelle zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="006ac-368">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="006ac-369">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-369">Parameters</span></span>
* <span data-ttu-id="006ac-370">Schnittstelle: GUID der Netzwerkschnittstelle</span><span class="sxs-lookup"><span data-stu-id="006ac-370">interface : network interface guid</span></span>
* <span data-ttu-id="006ac-371">Profil: Profilname</span><span class="sxs-lookup"><span data-stu-id="006ac-371">profile : profile name</span></span>

<span data-ttu-id="006ac-372">**/API/WiFi/Networks (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-372">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="006ac-373">Listet drahtlose Netzwerke auf der angegebenen Netzwerkschnittstelle auf.</span><span class="sxs-lookup"><span data-stu-id="006ac-373">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="006ac-374">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-374">Parameters</span></span>
* <span data-ttu-id="006ac-375">Schnittstelle: GUID der Netzwerkschnittstelle</span><span class="sxs-lookup"><span data-stu-id="006ac-375">interface : network interface guid</span></span>

<span data-ttu-id="006ac-376">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="006ac-376">Return data</span></span>
* <span data-ttu-id="006ac-377">Liste der Drahtlos Netzwerke, die sich auf der Netzwerkschnittstelle befinden, mit Details</span><span class="sxs-lookup"><span data-stu-id="006ac-377">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="006ac-378">**/API/WiFi/Network (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-378">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="006ac-379">Stellt eine Verbindung mit einem Netzwerk auf der angegebenen Schnittstelle her oder trennt es.</span><span class="sxs-lookup"><span data-stu-id="006ac-379">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="006ac-380">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-380">Parameters</span></span>
* <span data-ttu-id="006ac-381">Schnittstelle: GUID der Netzwerkschnittstelle</span><span class="sxs-lookup"><span data-stu-id="006ac-381">interface : network interface guid</span></span>
* <span data-ttu-id="006ac-382">SSID: SSID, hex64-codiert, um eine Verbindung herzustellen</span><span class="sxs-lookup"><span data-stu-id="006ac-382">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="006ac-383">OP: verbinden oder trennen</span><span class="sxs-lookup"><span data-stu-id="006ac-383">op : connect or disconnect</span></span>
* <span data-ttu-id="006ac-384">kreateprofile: Ja oder Nein</span><span class="sxs-lookup"><span data-stu-id="006ac-384">createprofile : yes or no</span></span>
* <span data-ttu-id="006ac-385">Schlüssel: gemeinsam verwendeter Schlüssel, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="006ac-385">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="006ac-386">Windows Performance Recorder</span><span class="sxs-lookup"><span data-stu-id="006ac-386">Windows Performance Recorder</span></span>

<span data-ttu-id="006ac-387">**/API/WPR/customtrace (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-387">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="006ac-388">Lädt ein WPR-Profil hoch und startet die Ablauf Verfolgung mithilfe des hochgeladenen Profils.</span><span class="sxs-lookup"><span data-stu-id="006ac-388">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="006ac-389">Payload</span><span class="sxs-lookup"><span data-stu-id="006ac-389">Payload</span></span>
* <span data-ttu-id="006ac-390">Mehrteilige konforme HTTP-Text</span><span class="sxs-lookup"><span data-stu-id="006ac-390">multi-part conforming http body</span></span>

<span data-ttu-id="006ac-391">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="006ac-391">Return data</span></span>
* <span data-ttu-id="006ac-392">Gibt den WPR-Sitzungsstatus zurück.</span><span class="sxs-lookup"><span data-stu-id="006ac-392">Returns the WPR session status.</span></span>

<span data-ttu-id="006ac-393">**/API/WPR/Status (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-393">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="006ac-394">Ruft den Status der WPR-Sitzung ab.</span><span class="sxs-lookup"><span data-stu-id="006ac-394">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="006ac-395">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="006ac-395">Return data</span></span>
* <span data-ttu-id="006ac-396">WPR-Sitzungs Status.</span><span class="sxs-lookup"><span data-stu-id="006ac-396">WPR session status.</span></span>

<span data-ttu-id="006ac-397">**/API/WPR/Trace (Get)**</span><span class="sxs-lookup"><span data-stu-id="006ac-397">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="006ac-398">Beendet eine WPR-Ablauf Verfolgungs Sitzung (Leistung).</span><span class="sxs-lookup"><span data-stu-id="006ac-398">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="006ac-399">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="006ac-399">Return data</span></span>
* <span data-ttu-id="006ac-400">Gibt die ETL-Ablauf Verfolgungs Datei zurück.</span><span class="sxs-lookup"><span data-stu-id="006ac-400">Returns the trace ETL file</span></span>

<span data-ttu-id="006ac-401">**/API/WPR/Trace (Post)**</span><span class="sxs-lookup"><span data-stu-id="006ac-401">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="006ac-402">Startet eine Ablauf Verfolgungs Sitzung für WPR (Leistung).</span><span class="sxs-lookup"><span data-stu-id="006ac-402">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="006ac-403">Parameter</span><span class="sxs-lookup"><span data-stu-id="006ac-403">Parameters</span></span>
* <span data-ttu-id="006ac-404">Profil: Profilname.</span><span class="sxs-lookup"><span data-stu-id="006ac-404">profile : Profile name.</span></span> <span data-ttu-id="006ac-405">Verfügbare Profile werden in "perfprofiles/Profiles. JSON" gespeichert.</span><span class="sxs-lookup"><span data-stu-id="006ac-405">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="006ac-406">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="006ac-406">Return data</span></span>
* <span data-ttu-id="006ac-407">Beim Start wird der WPR-Sitzungs Status zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="006ac-407">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="006ac-408">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="006ac-408">See also</span></span>
* [<span data-ttu-id="006ac-409">Verwenden des Windows-Geräteportals</span><span class="sxs-lookup"><span data-stu-id="006ac-409">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="006ac-410">API-Referenz für den Geräte Portal (UWP)</span><span class="sxs-lookup"><span data-stu-id="006ac-410">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
