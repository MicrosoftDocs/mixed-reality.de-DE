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
# <a name="device-portal-api-reference"></a><span data-ttu-id="11e88-104">Referenz zur Geräte Portal-API</span><span class="sxs-lookup"><span data-stu-id="11e88-104">Device portal API reference</span></span>

<span data-ttu-id="11e88-105">Alles im [Windows-Geräte Portal](using-the-windows-device-portal.md) baut auf der Rest-API auf, mit der Sie auf die Daten zugreifen und Ihr Gerät Programm gesteuert steuern können.</span><span class="sxs-lookup"><span data-stu-id="11e88-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="11e88-106">App-Verlagerung</span><span class="sxs-lookup"><span data-stu-id="11e88-106">App deloyment</span></span>

<span data-ttu-id="11e88-107">**/API/APP/packagemanager/Package (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="11e88-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="11e88-108">Deinstalliert eine APP</span><span class="sxs-lookup"><span data-stu-id="11e88-108">Uninstalls an app</span></span>

<span data-ttu-id="11e88-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-109">Parameters</span></span>
* <span data-ttu-id="11e88-110">Paketen Der Dateiname des Pakets, das deinstalliert werden soll.</span><span class="sxs-lookup"><span data-stu-id="11e88-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="11e88-111">**/API/APP/packagemanager/Package (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="11e88-112">Installiert eine APP</span><span class="sxs-lookup"><span data-stu-id="11e88-112">Installs an App</span></span>

<span data-ttu-id="11e88-113">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-113">Parameters</span></span>
* <span data-ttu-id="11e88-114">Paketen Der Dateiname des zu installierenden Pakets.</span><span class="sxs-lookup"><span data-stu-id="11e88-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="11e88-115">Nutz</span><span class="sxs-lookup"><span data-stu-id="11e88-115">Payload</span></span>
* <span data-ttu-id="11e88-116">Mehrteilige konforme HTTP-Text</span><span class="sxs-lookup"><span data-stu-id="11e88-116">multi-part conforming http body</span></span>

<span data-ttu-id="11e88-117">**/API/APP/packagemanager/Packages (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="11e88-118">Hiermit wird die Liste der installierten apps auf dem System mit Details abgerufen.</span><span class="sxs-lookup"><span data-stu-id="11e88-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="11e88-119">Rückgabe Daten</span><span class="sxs-lookup"><span data-stu-id="11e88-119">Return data</span></span>
* <span data-ttu-id="11e88-120">Liste der installierten Pakete mit Details</span><span class="sxs-lookup"><span data-stu-id="11e88-120">List of installed packages with details</span></span>

<span data-ttu-id="11e88-121">**/API/APP/packagemanager/State (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="11e88-122">Hiermit wird der Status der Installation in Progress-App abgerufen.</span><span class="sxs-lookup"><span data-stu-id="11e88-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="11e88-123">Absturzabbildsammlung</span><span class="sxs-lookup"><span data-stu-id="11e88-123">Dump collection</span></span>

<span data-ttu-id="11e88-124">**/API/Debug/Dump/Usermode/CrashControl (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="11e88-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="11e88-125">Deaktiviert die Absturz Abbild Erfassung für eine Sideload-app.</span><span class="sxs-lookup"><span data-stu-id="11e88-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="11e88-126">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-126">Parameters</span></span>
* <span data-ttu-id="11e88-127">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="11e88-127">packageFullname : package name</span></span>

<span data-ttu-id="11e88-128">**/API/Debug/Dump/Usermode/CrashControl (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="11e88-129">Ruft Einstellungen für die Absturz Abbild Erfassung von Sideload-apps ab</span><span class="sxs-lookup"><span data-stu-id="11e88-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="11e88-130">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-130">Parameters</span></span>
* <span data-ttu-id="11e88-131">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="11e88-131">packageFullname : package name</span></span>

<span data-ttu-id="11e88-132">**/API/Debug/Dump/Usermode/CrashControl (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="11e88-133">Aktiviert und legt Sicherungs Steuerungseinstellungen für eine per Sideload übertragene App fest.</span><span class="sxs-lookup"><span data-stu-id="11e88-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="11e88-134">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-134">Parameters</span></span>
* <span data-ttu-id="11e88-135">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="11e88-135">packageFullname : package name</span></span>

<span data-ttu-id="11e88-136">**/API/Debug/Dump/Usermode/crashdump (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="11e88-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="11e88-137">Löscht einen Absturz Abbild für eine Sideload-app.</span><span class="sxs-lookup"><span data-stu-id="11e88-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="11e88-138">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-138">Parameters</span></span>
* <span data-ttu-id="11e88-139">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="11e88-139">packageFullname : package name</span></span>
* <span data-ttu-id="11e88-140">Dateiname: Name der Sicherungsdatei</span><span class="sxs-lookup"><span data-stu-id="11e88-140">fileName : dump file name</span></span>

<span data-ttu-id="11e88-141">**/API/Debug/Dump/Usermode/crashdump (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="11e88-142">Ruft ein Absturz Abbild für eine per Sideload übertragene App ab.</span><span class="sxs-lookup"><span data-stu-id="11e88-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="11e88-143">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-143">Parameters</span></span>
* <span data-ttu-id="11e88-144">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="11e88-144">packageFullname : package name</span></span>
* <span data-ttu-id="11e88-145">Dateiname: Name der Sicherungsdatei</span><span class="sxs-lookup"><span data-stu-id="11e88-145">fileName : dump file name</span></span>

<span data-ttu-id="11e88-146">Rückgabe Daten</span><span class="sxs-lookup"><span data-stu-id="11e88-146">Return data</span></span>
* <span data-ttu-id="11e88-147">Dumpdatei.</span><span class="sxs-lookup"><span data-stu-id="11e88-147">Dump file.</span></span> <span data-ttu-id="11e88-148">Überprüfen mit WinDbg oder Visual Studio</span><span class="sxs-lookup"><span data-stu-id="11e88-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="11e88-149">**/API/Debug/Dump/Usermode/Dumps (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="11e88-150">Gibt eine Liste aller Absturz Abbilder für Sideload-apps zurück.</span><span class="sxs-lookup"><span data-stu-id="11e88-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="11e88-151">Rückgabe Daten</span><span class="sxs-lookup"><span data-stu-id="11e88-151">Return data</span></span>
* <span data-ttu-id="11e88-152">Liste der Absturz Abbilder pro Seite geladener apps</span><span class="sxs-lookup"><span data-stu-id="11e88-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="11e88-153">ETW</span><span class="sxs-lookup"><span data-stu-id="11e88-153">ETW</span></span>

<span data-ttu-id="11e88-154">**/API/etw/Providers (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="11e88-155">Listet registrierte Anbieter auf.</span><span class="sxs-lookup"><span data-stu-id="11e88-155">Enumerates registered providers</span></span>

<span data-ttu-id="11e88-156">Rückgabe Daten</span><span class="sxs-lookup"><span data-stu-id="11e88-156">Return data</span></span>
* <span data-ttu-id="11e88-157">Liste der Anbieter, Anzeige Name und GUID</span><span class="sxs-lookup"><span data-stu-id="11e88-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="11e88-158">**/API/etw/Session/Realtime (Get/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="11e88-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="11e88-159">Erstellt eine ETW-Sitzung in Echtzeit. verwaltet über einen WebSocket.</span><span class="sxs-lookup"><span data-stu-id="11e88-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="11e88-160">Rückgabe Daten</span><span class="sxs-lookup"><span data-stu-id="11e88-160">Return data</span></span>
* <span data-ttu-id="11e88-161">ETW-Ereignisse von aktivierten Anbietern</span><span class="sxs-lookup"><span data-stu-id="11e88-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="11e88-162">Holographic – Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="11e88-162">Holographic OS</span></span>

<span data-ttu-id="11e88-163">**/API/Holographic/OS/etw/customproviders (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="11e88-164">Gibt eine Liste von hololens-spezifischen etw-Anbietern zurück, die nicht beim System registriert sind.</span><span class="sxs-lookup"><span data-stu-id="11e88-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="11e88-165">**/API/Holographic/OS/Services (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="11e88-166">Gibt die Zustände aller Dienste zurück, die ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="11e88-166">Returns the states of all services running.</span></span>

<span data-ttu-id="11e88-167">**/API/Holographic/OS/Settings/IPD (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="11e88-168">Ruft die gespeicherte IPD (interpupranäre Entfernung) in Millimeter ab.</span><span class="sxs-lookup"><span data-stu-id="11e88-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="11e88-169">**/API/Holographic/OS/Settings/IPD (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="11e88-170">Legt die IPD fest.</span><span class="sxs-lookup"><span data-stu-id="11e88-170">Sets the IPD</span></span>

<span data-ttu-id="11e88-171">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-171">Parameters</span></span>
* <span data-ttu-id="11e88-172">IPD Neuer IPD-Wert, der in Millimeter festgelegt werden soll</span><span class="sxs-lookup"><span data-stu-id="11e88-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="11e88-173">**/API/Holographic/OS/Webmanagement/Settings/HTTPS (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="11e88-174">Abrufen der HTTPS-Anforderungen für das Geräteportal</span><span class="sxs-lookup"><span data-stu-id="11e88-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="11e88-175">**/API/Holographic/OS/Webmanagement/Settings/HTTPS (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="11e88-176">Legt die HTTPS-Anforderungen für das Geräte Portal fest.</span><span class="sxs-lookup"><span data-stu-id="11e88-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="11e88-177">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-177">Parameters</span></span>
* <span data-ttu-id="11e88-178">erforderlich: Ja, Nein oder Standard</span><span class="sxs-lookup"><span data-stu-id="11e88-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="11e88-179">Holografische Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="11e88-179">Holographic Perception</span></span>

<span data-ttu-id="11e88-180">**/API/Holographic/perception/Client (Get/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="11e88-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="11e88-181">Akzeptiert WebSocket-Upgrades und führt einen perception-Client aus, der Updates bei 30 fps sendet.</span><span class="sxs-lookup"><span data-stu-id="11e88-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="11e88-182">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-182">Parameters</span></span>
* <span data-ttu-id="11e88-183">clientmode: "aktiv" erzwingt den visuellen Überwachungsmodus, wenn er nicht passiv festgelegt werden kann.</span><span class="sxs-lookup"><span data-stu-id="11e88-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="11e88-184">Holographic-Therme</span><span class="sxs-lookup"><span data-stu-id="11e88-184">Holographic Thermal</span></span>

<span data-ttu-id="11e88-185">**/API/Holographic/Thermal/Stage (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="11e88-186">Die wärmestufe des Geräts erhalten (0 normal, 1 warm, 2 kritisch)</span><span class="sxs-lookup"><span data-stu-id="11e88-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="11e88-187">Wahrnehmungs Simulations-Steuerelement</span><span class="sxs-lookup"><span data-stu-id="11e88-187">Perception Simulation Control</span></span>

<span data-ttu-id="11e88-188">**/API/Holographic/Simulation/Control/Mode (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="11e88-189">Simulationsmodus erhalten</span><span class="sxs-lookup"><span data-stu-id="11e88-189">Get the simulation mode</span></span>

<span data-ttu-id="11e88-190">**/API/Holographic/Simulation/Control/Mode (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="11e88-191">Festlegen des Simulationsmodus</span><span class="sxs-lookup"><span data-stu-id="11e88-191">Set the simulation mode</span></span>

<span data-ttu-id="11e88-192">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-192">Parameters</span></span>
* <span data-ttu-id="11e88-193">Mode: Simulationsmodus: Standard, Simulation, Remote, Legacy</span><span class="sxs-lookup"><span data-stu-id="11e88-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="11e88-194">**/API/Holographic/Simulation/Control/Stream (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="11e88-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="11e88-195">Löscht einen Steuerungsdaten Strom.</span><span class="sxs-lookup"><span data-stu-id="11e88-195">Delete a control stream.</span></span>

<span data-ttu-id="11e88-196">**/API/Holographic/Simulation/Control/Stream (Get/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="11e88-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="11e88-197">Öffnen Sie eine websocketverbindung für einen Steuerungsdaten Strom.</span><span class="sxs-lookup"><span data-stu-id="11e88-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="11e88-198">**/API/Holographic/Simulation/Control/Stream (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="11e88-199">Erstellen Sie einen Steuerungsdaten Strom (Priorität ist erforderlich), oder stellen Sie Daten in einem erstellten Stream bereit (streamid erforderlich).</span><span class="sxs-lookup"><span data-stu-id="11e88-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="11e88-200">Es wird erwartet, dass für die Daten der Typ "Application/Octett-Stream" festgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="11e88-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="11e88-201">Wiedergabe von Wahrnehmungs Simulationen</span><span class="sxs-lookup"><span data-stu-id="11e88-201">Perception Simulation Playback</span></span>

<span data-ttu-id="11e88-202">**/API/Holographic/Simulation/Playback/File (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="11e88-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="11e88-203">Löschen Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="11e88-203">Delete a recording.</span></span>

<span data-ttu-id="11e88-204">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-204">Parameters</span></span>
* <span data-ttu-id="11e88-205">verzeichnet Der Name der zu löschenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="11e88-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="11e88-206">**/API/Holographic/Simulation/Playback/File (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="11e88-207">Hochladen einer Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="11e88-207">Upload a recording.</span></span>

<span data-ttu-id="11e88-208">**/API/Holographic/Simulation/Playback/Files (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="11e88-209">Alle Aufzeichnungen erhalten.</span><span class="sxs-lookup"><span data-stu-id="11e88-209">Get all recordings.</span></span>

<span data-ttu-id="11e88-210">**/API/Holographic/Simulation/Playback/Session (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="11e88-211">Gibt den aktuellen Wiedergabe Zustand einer Aufzeichnung an.</span><span class="sxs-lookup"><span data-stu-id="11e88-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="11e88-212">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-212">Parameters</span></span>
* <span data-ttu-id="11e88-213">verzeichnet Der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="11e88-213">recording : Name of recording.</span></span>

<span data-ttu-id="11e88-214">**/API/Holographic/Simulation/Playback/Session/File (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="11e88-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="11e88-215">Entladen Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="11e88-215">Unload a recording.</span></span>

<span data-ttu-id="11e88-216">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-216">Parameters</span></span>
* <span data-ttu-id="11e88-217">verzeichnet Der Name der zu entladenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="11e88-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="11e88-218">**/API/Holographic/Simulation/Playback/Session/File (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="11e88-219">Laden Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="11e88-219">Load a recording.</span></span>

<span data-ttu-id="11e88-220">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-220">Parameters</span></span>
* <span data-ttu-id="11e88-221">verzeichnet Der Name der zu ladenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="11e88-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="11e88-222">**/API/Holographic/Simulation/Playback/Session/Files (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="11e88-223">Alle geladenen Aufzeichnungen erhalten.</span><span class="sxs-lookup"><span data-stu-id="11e88-223">Get all loaded recordings.</span></span>

<span data-ttu-id="11e88-224">**/API/Holographic/Simulation/Playback/Session/Pause (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="11e88-225">Hält eine Aufzeichnung an.</span><span class="sxs-lookup"><span data-stu-id="11e88-225">Pause a recording.</span></span>

<span data-ttu-id="11e88-226">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-226">Parameters</span></span>
* <span data-ttu-id="11e88-227">verzeichnet Der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="11e88-227">recording : Name of recording.</span></span>

<span data-ttu-id="11e88-228">**/API/Holographic/Simulation/Playback/Session/Play (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="11e88-229">Wiedergabe einer Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="11e88-229">Play a recording.</span></span>

<span data-ttu-id="11e88-230">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-230">Parameters</span></span>
* <span data-ttu-id="11e88-231">verzeichnet Der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="11e88-231">recording : Name of recording.</span></span>

<span data-ttu-id="11e88-232">**/API/Holographic/Simulation/Playback/Session/Stop (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="11e88-233">Beendet eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="11e88-233">Stop a recording.</span></span>

<span data-ttu-id="11e88-234">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-234">Parameters</span></span>
* <span data-ttu-id="11e88-235">verzeichnet Der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="11e88-235">recording : Name of recording.</span></span>

<span data-ttu-id="11e88-236">**/API/Holographic/Simulation/Playback/Session/Types (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="11e88-237">Datentypen in einer geladenen Aufzeichnung erhalten.</span><span class="sxs-lookup"><span data-stu-id="11e88-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="11e88-238">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-238">Parameters</span></span>
* <span data-ttu-id="11e88-239">verzeichnet Der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="11e88-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="11e88-240">Erfassung von Wahrnehmungs Simulationen</span><span class="sxs-lookup"><span data-stu-id="11e88-240">Perception Simulation Recording</span></span>

<span data-ttu-id="11e88-241">**/API/Holographic/Simulation/Recording/Start (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="11e88-242">Startet eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="11e88-242">Start a recording.</span></span> <span data-ttu-id="11e88-243">Nur eine einzelne Aufzeichnung kann gleichzeitig aktiv sein.</span><span class="sxs-lookup"><span data-stu-id="11e88-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="11e88-244">Eine der Köpfe, Hände, spatialmapping oder Umgebung muss festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="11e88-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="11e88-245">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-245">Parameters</span></span>
* <span data-ttu-id="11e88-246">Stadt Legen Sie auf 1 fest, um Head-Daten aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="11e88-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="11e88-247">Hände Legen Sie auf 1 fest, um die Daten aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="11e88-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="11e88-248">spatialmapping: Legen Sie auf 1 fest, um die räumliche Zuordnung aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="11e88-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="11e88-249">Umgebung Legen Sie auf 1 fest, um Umgebungs Daten aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="11e88-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="11e88-250">Benennen Der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="11e88-250">name : Name of the recording.</span></span>
* <span data-ttu-id="11e88-251">singlespatialmappingframe: Legen Sie auf 1 fest, um nur einen einzelnen räumlichen zuordnungsframe aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="11e88-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="11e88-252">**/API/Holographic/Simulation/Recording/Status (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="11e88-253">Aufzeichnungsstatus erhalten.</span><span class="sxs-lookup"><span data-stu-id="11e88-253">Get recording state.</span></span>

<span data-ttu-id="11e88-254">**/API/Holographic/Simulation/Recording/Stop (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="11e88-255">Hält die aktuelle Aufzeichnung an.</span><span class="sxs-lookup"><span data-stu-id="11e88-255">Stop the current recording.</span></span> <span data-ttu-id="11e88-256">Die Aufzeichnung wird als Datei zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="11e88-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="11e88-257">Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="11e88-257">Mixed Reality Capture</span></span>

<span data-ttu-id="11e88-258">**/API/Holographic/MRC/File (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="11e88-259">Hiermit wird eine gemischte Reality-Datei vom Gerät heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="11e88-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="11e88-260">Verwenden Sie den OP = Stream-Abfrage Parameter für das Streaming.</span><span class="sxs-lookup"><span data-stu-id="11e88-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="11e88-261">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-261">Parameters</span></span>
* <span data-ttu-id="11e88-262">Einfügen Name, hex64 codiert, der Videodatei, die Sie erhalten</span><span class="sxs-lookup"><span data-stu-id="11e88-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="11e88-263">OP: Stream</span><span class="sxs-lookup"><span data-stu-id="11e88-263">op : stream</span></span>

<span data-ttu-id="11e88-264">**/API/Holographic/MRC/File (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="11e88-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="11e88-265">Löscht eine gemischte Reality-Aufzeichnung auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="11e88-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="11e88-266">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-266">Parameters</span></span>
* <span data-ttu-id="11e88-267">Einfügen Name, hex64-codiert, der zu löschenden Datei</span><span class="sxs-lookup"><span data-stu-id="11e88-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="11e88-268">**/API/Holographic/MRC/Files (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="11e88-269">Gibt die Liste der Mixed Reality-Dateien zurück, die auf dem Gerät gespeichert sind</span><span class="sxs-lookup"><span data-stu-id="11e88-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="11e88-270">**/API/Holographic/MRC/Photo (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="11e88-271">Nimmt ein gemischtes Reality-Foto und erstellt eine Datei auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="11e88-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="11e88-272">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-272">Parameters</span></span>
* <span data-ttu-id="11e88-273">hololens: Erfassungs holograms: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="11e88-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="11e88-274">PV: Erfassen der PV-Kamera: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="11e88-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="11e88-275">Renderfromcamera: (Nur hololens 2) Rendering aus der Perspektive der Foto-/Videokamera: true oder false (Standardwert: true)</span><span class="sxs-lookup"><span data-stu-id="11e88-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="11e88-276">**/API/Holographic/MRC/Settings (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="11e88-277">Ruft die Standardeinstellungen für die gemischte Realität-Erfassung ab.</span><span class="sxs-lookup"><span data-stu-id="11e88-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="11e88-278">**/API/Holographic/MRC/Settings (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="11e88-279">Legt die Standardeinstellungen für die gemischte Reality-Erfassung fest.</span><span class="sxs-lookup"><span data-stu-id="11e88-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="11e88-280">Einige dieser Einstellungen werden auf das MRC-Foto und die Video Erfassung des Systems angewendet.</span><span class="sxs-lookup"><span data-stu-id="11e88-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="11e88-281">**/API/Holographic/MRC/Status (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="11e88-282">Ruft den Status der aufgezeichnete gemischten Realität ab (wird ausgeführt, beendet).</span><span class="sxs-lookup"><span data-stu-id="11e88-282">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="11e88-283">**/API/Holographic/MRC/Thumbnail (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-283">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="11e88-284">Ruft das Miniaturbild für die angegebene Datei ab.</span><span class="sxs-lookup"><span data-stu-id="11e88-284">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="11e88-285">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-285">Parameters</span></span>
* <span data-ttu-id="11e88-286">Einfügen Name, hex64 codiert, der Datei, für die die Miniaturansicht angefordert wird</span><span class="sxs-lookup"><span data-stu-id="11e88-286">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="11e88-287">**/API/Holographic/MRC/Video/Control/Start (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-287">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="11e88-288">Startet eine gemischte Reality-Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="11e88-288">Starts a mixed reality recording</span></span>

<span data-ttu-id="11e88-289">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-289">Parameters</span></span>
* <span data-ttu-id="11e88-290">hololens: Erfassungs holograms: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="11e88-290">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="11e88-291">PV: Erfassen der PV-Kamera: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="11e88-291">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="11e88-292">MIC: Mikrofon erfassen: true oder false (standardmäßig false)</span><span class="sxs-lookup"><span data-stu-id="11e88-292">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="11e88-293">Loopback: App-Audioerfassung: true oder false (standardmäßig false)</span><span class="sxs-lookup"><span data-stu-id="11e88-293">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="11e88-294">Renderfromcamera: (Nur hololens 2) Rendering aus der Perspektive der Foto-/Videokamera: true oder false (Standardwert: true)</span><span class="sxs-lookup"><span data-stu-id="11e88-294">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="11e88-295">Vstab: (Nur hololens 2) Videostabilisierung aktivieren: true oder false (Standardwert: true)</span><span class="sxs-lookup"><span data-stu-id="11e88-295">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="11e88-296">vstabbuffer: (Nur hololens 2), Video Stabilisierungs Puffer Wartezeit: zwischen 0 und 30 Frames (standardmäßig 15 Frames)</span><span class="sxs-lookup"><span data-stu-id="11e88-296">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="11e88-297">**/API/Holographic/MRC/Video/Control/Stop (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-297">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="11e88-298">Beendet die aktuelle gemischte Reality-Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="11e88-298">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="11e88-299">Streaming mit gemischter Realität</span><span class="sxs-lookup"><span data-stu-id="11e88-299">Mixed Reality Streaming</span></span>

<span data-ttu-id="11e88-300">Hololens unterstützt die Live Vorschau von Mixed Reality über einen segmentierten Download einer fragmentierten MP4-Datei.</span><span class="sxs-lookup"><span data-stu-id="11e88-300">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="11e88-301">Gemischte Reality-Streams verwenden denselben Satz von Parametern, um zu steuern, was aufgezeichnet wird:</span><span class="sxs-lookup"><span data-stu-id="11e88-301">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="11e88-302">hololens: Erfassungs holograms: true oder false</span><span class="sxs-lookup"><span data-stu-id="11e88-302">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="11e88-303">PV: Erfassen der PV-Kamera: true oder false</span><span class="sxs-lookup"><span data-stu-id="11e88-303">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="11e88-304">MIC: Mikrofon erfassen: true oder false</span><span class="sxs-lookup"><span data-stu-id="11e88-304">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="11e88-305">Loopback: App-Audioerfassung: true oder false</span><span class="sxs-lookup"><span data-stu-id="11e88-305">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="11e88-306">Wenn keines dieser Angaben angegeben ist: holograms, Foto-/Videokamera und App-Audiodaten werden aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="11e88-306">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="11e88-307">Wenn eine Angabe festgelegt ist: die nicht angegebenen Parameter werden standardmäßig auf false festgelegt.</span><span class="sxs-lookup"><span data-stu-id="11e88-307">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="11e88-308">Optionale Parameter (nur hololens 2)</span><span class="sxs-lookup"><span data-stu-id="11e88-308">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="11e88-309">Renderfromcamera: Rendering aus Perspektive der Foto-/Videokamera: true oder false (Standardwert ist true)</span><span class="sxs-lookup"><span data-stu-id="11e88-309">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="11e88-310">Vstab: Videostabilisierung aktivieren: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="11e88-310">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="11e88-311">vstabbuffer: Puffer Wartezeit für Videostabilisierung: zwischen 0 und 30 Frames (standardmäßig 15 Frames)</span><span class="sxs-lookup"><span data-stu-id="11e88-311">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="11e88-312">**/API/Holographic/Stream/Live.MP4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-312">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="11e88-313">Ein-Datenstrom von 1280x720p 30 fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="11e88-313">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="11e88-314">**/API/Holographic/Stream/live_high.MP4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-314">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="11e88-315">Ein-Datenstrom von 1280x720p 30 fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="11e88-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="11e88-316">**/API/Holographic/Stream/live_med.MP4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="11e88-317">Ein 854x480p 30 fps 2.5 MBit-Stream.</span><span class="sxs-lookup"><span data-stu-id="11e88-317">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="11e88-318">**/API/Holographic/Stream/live_low.MP4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-318">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="11e88-319">Ein 428x240 p 15fps 0.6-MBit-Stream.</span><span class="sxs-lookup"><span data-stu-id="11e88-319">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="11e88-320">Netzwerk</span><span class="sxs-lookup"><span data-stu-id="11e88-320">Networking</span></span>

<span data-ttu-id="11e88-321">**/API/Networking/ipconfig (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-321">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="11e88-322">Ruft die aktuelle IP-Konfiguration ab.</span><span class="sxs-lookup"><span data-stu-id="11e88-322">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="11e88-323">Betriebssysteminformationen</span><span class="sxs-lookup"><span data-stu-id="11e88-323">OS Information</span></span>

<span data-ttu-id="11e88-324">**/API/OS/Info (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-324">**/api/os/info (GET)**</span></span>

<span data-ttu-id="11e88-325">Ruft Betriebssysteminformationen ab.</span><span class="sxs-lookup"><span data-stu-id="11e88-325">Gets operating system information</span></span>

<span data-ttu-id="11e88-326">**/API/OS/MachineName (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-326">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="11e88-327">Ruft den Computernamen ab.</span><span class="sxs-lookup"><span data-stu-id="11e88-327">Gets the machine name</span></span>

<span data-ttu-id="11e88-328">**/API/OS/MachineName (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-328">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="11e88-329">Legt den Computernamen fest.</span><span class="sxs-lookup"><span data-stu-id="11e88-329">Sets the machine name</span></span>

<span data-ttu-id="11e88-330">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-330">Parameters</span></span>
* <span data-ttu-id="11e88-331">Benennen Neuer Computername, hex64-codiert, festgelegt auf</span><span class="sxs-lookup"><span data-stu-id="11e88-331">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="11e88-332">Leistungsdaten</span><span class="sxs-lookup"><span data-stu-id="11e88-332">Performance data</span></span>

<span data-ttu-id="11e88-333">**/API/ResourceManager/Processes (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-333">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="11e88-334">Gibt die Liste der laufenden Prozesse mit Details zurück.</span><span class="sxs-lookup"><span data-stu-id="11e88-334">Returns the list of running processes with details</span></span>

<span data-ttu-id="11e88-335">Rückgabe Daten</span><span class="sxs-lookup"><span data-stu-id="11e88-335">Return data</span></span>
* <span data-ttu-id="11e88-336">JSON mit einer Liste der Prozesse und Details für jeden Prozess</span><span class="sxs-lookup"><span data-stu-id="11e88-336">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="11e88-337">**/API/ResourceManager/systemperf (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-337">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="11e88-338">Gibt die System Leistungsstatistik (e/a-Lese-/Schreibvorgänge, Speicher Statistiken usw.) zurück.</span><span class="sxs-lookup"><span data-stu-id="11e88-338">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="11e88-339">Rückgabe Daten</span><span class="sxs-lookup"><span data-stu-id="11e88-339">Return data</span></span>
* <span data-ttu-id="11e88-340">JSON mit Systeminformationen: CPU, GPU, Arbeitsspeicher, Netzwerk, e/a</span><span class="sxs-lookup"><span data-stu-id="11e88-340">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="11e88-341">Stromversorgung</span><span class="sxs-lookup"><span data-stu-id="11e88-341">Power</span></span>

<span data-ttu-id="11e88-342">**/API/Power/Battery (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-342">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="11e88-343">Ruft den aktuellen Akku Zustand ab.</span><span class="sxs-lookup"><span data-stu-id="11e88-343">Gets the current battery state</span></span>

<span data-ttu-id="11e88-344">**/API/Power/State (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-344">**/api/power/state (GET)**</span></span>

<span data-ttu-id="11e88-345">Prüft, ob sich das System in einem niedrigen Energiezustand befindet</span><span class="sxs-lookup"><span data-stu-id="11e88-345">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="11e88-346">Remotesteuerung</span><span class="sxs-lookup"><span data-stu-id="11e88-346">Remote Control</span></span>

<span data-ttu-id="11e88-347">**/API/Control/Restart (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-347">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="11e88-348">Startet das Zielgerät neu.</span><span class="sxs-lookup"><span data-stu-id="11e88-348">Restarts the target device</span></span>

<span data-ttu-id="11e88-349">**/API/Control/Shutdown (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-349">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="11e88-350">Fährt das Zielgerät herunter.</span><span class="sxs-lookup"><span data-stu-id="11e88-350">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="11e88-351">Task-Manager</span><span class="sxs-lookup"><span data-stu-id="11e88-351">Task Manager</span></span>

<span data-ttu-id="11e88-352">**/API/Taskmanager/app (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="11e88-352">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="11e88-353">Beendet eine moderne App</span><span class="sxs-lookup"><span data-stu-id="11e88-353">Stops a modern app</span></span>

<span data-ttu-id="11e88-354">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-354">Parameters</span></span>
* <span data-ttu-id="11e88-355">Paketen Vollständiger Name des App-Pakets, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="11e88-355">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="11e88-356">forcestop: Beendigung aller Prozesse erzwingen (= ja)</span><span class="sxs-lookup"><span data-stu-id="11e88-356">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="11e88-357">**/API/Taskmanager/app (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-357">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="11e88-358">Startet eine moderne App</span><span class="sxs-lookup"><span data-stu-id="11e88-358">Starts a modern app</span></span>

<span data-ttu-id="11e88-359">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-359">Parameters</span></span>
* <span data-ttu-id="11e88-360">AppID Praid der APP, die gestartet werden soll, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="11e88-360">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="11e88-361">Paketen Vollständiger Name des App-Pakets, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="11e88-361">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="11e88-362">WiFi-Verwaltung</span><span class="sxs-lookup"><span data-stu-id="11e88-362">WiFi Management</span></span>

<span data-ttu-id="11e88-363">**/API/WiFi/Interfaces (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-363">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="11e88-364">Listet drahtlose Netzwerkschnittstellen auf.</span><span class="sxs-lookup"><span data-stu-id="11e88-364">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="11e88-365">Rückgabe Daten</span><span class="sxs-lookup"><span data-stu-id="11e88-365">Return data</span></span>
* <span data-ttu-id="11e88-366">Liste der drahtlos Schnittstellen mit Details (GUID, Beschreibung usw.)</span><span class="sxs-lookup"><span data-stu-id="11e88-366">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="11e88-367">**/API/WiFi/Network (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="11e88-367">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="11e88-368">Löscht ein Profil, das einem Netzwerk in einer angegebenen Schnittstelle zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="11e88-368">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="11e88-369">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-369">Parameters</span></span>
* <span data-ttu-id="11e88-370">Schnittstelle: GUID der Netzwerkschnittstelle</span><span class="sxs-lookup"><span data-stu-id="11e88-370">interface : network interface guid</span></span>
* <span data-ttu-id="11e88-371">Profil: Profilname</span><span class="sxs-lookup"><span data-stu-id="11e88-371">profile : profile name</span></span>

<span data-ttu-id="11e88-372">**/API/WiFi/Networks (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-372">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="11e88-373">Listet drahtlose Netzwerke auf der angegebenen Netzwerkschnittstelle auf.</span><span class="sxs-lookup"><span data-stu-id="11e88-373">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="11e88-374">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-374">Parameters</span></span>
* <span data-ttu-id="11e88-375">Schnittstelle: GUID der Netzwerkschnittstelle</span><span class="sxs-lookup"><span data-stu-id="11e88-375">interface : network interface guid</span></span>

<span data-ttu-id="11e88-376">Rückgabe Daten</span><span class="sxs-lookup"><span data-stu-id="11e88-376">Return data</span></span>
* <span data-ttu-id="11e88-377">Liste der Drahtlos Netzwerke, die sich auf der Netzwerkschnittstelle befinden, mit Details</span><span class="sxs-lookup"><span data-stu-id="11e88-377">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="11e88-378">**/API/WiFi/Network (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-378">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="11e88-379">Stellt eine Verbindung mit einem Netzwerk auf der angegebenen Schnittstelle her oder trennt es.</span><span class="sxs-lookup"><span data-stu-id="11e88-379">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="11e88-380">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-380">Parameters</span></span>
* <span data-ttu-id="11e88-381">Schnittstelle: GUID der Netzwerkschnittstelle</span><span class="sxs-lookup"><span data-stu-id="11e88-381">interface : network interface guid</span></span>
* <span data-ttu-id="11e88-382">SSID: SSID, hex64-codiert, um eine Verbindung herzustellen</span><span class="sxs-lookup"><span data-stu-id="11e88-382">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="11e88-383">OP: verbinden oder trennen</span><span class="sxs-lookup"><span data-stu-id="11e88-383">op : connect or disconnect</span></span>
* <span data-ttu-id="11e88-384">kreateprofile: Ja oder Nein</span><span class="sxs-lookup"><span data-stu-id="11e88-384">createprofile : yes or no</span></span>
* <span data-ttu-id="11e88-385">Schlüssel: gemeinsam verwendeter Schlüssel, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="11e88-385">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="11e88-386">Windows-Leistungs Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="11e88-386">Windows Performance Recorder</span></span>

<span data-ttu-id="11e88-387">**/API/WPR/customtrace (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-387">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="11e88-388">Lädt ein WPR-Profil hoch und startet die Ablauf Verfolgung mithilfe des hochgeladenen Profils.</span><span class="sxs-lookup"><span data-stu-id="11e88-388">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="11e88-389">Nutz</span><span class="sxs-lookup"><span data-stu-id="11e88-389">Payload</span></span>
* <span data-ttu-id="11e88-390">Mehrteilige konforme HTTP-Text</span><span class="sxs-lookup"><span data-stu-id="11e88-390">multi-part conforming http body</span></span>

<span data-ttu-id="11e88-391">Rückgabe Daten</span><span class="sxs-lookup"><span data-stu-id="11e88-391">Return data</span></span>
* <span data-ttu-id="11e88-392">Gibt den WPR-Sitzungsstatus zurück.</span><span class="sxs-lookup"><span data-stu-id="11e88-392">Returns the WPR session status.</span></span>

<span data-ttu-id="11e88-393">**/API/WPR/Status (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-393">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="11e88-394">Ruft den Status der WPR-Sitzung ab.</span><span class="sxs-lookup"><span data-stu-id="11e88-394">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="11e88-395">Rückgabe Daten</span><span class="sxs-lookup"><span data-stu-id="11e88-395">Return data</span></span>
* <span data-ttu-id="11e88-396">WPR-Sitzungs Status.</span><span class="sxs-lookup"><span data-stu-id="11e88-396">WPR session status.</span></span>

<span data-ttu-id="11e88-397">**/API/WPR/Trace (Get)**</span><span class="sxs-lookup"><span data-stu-id="11e88-397">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="11e88-398">Beendet eine WPR-Ablauf Verfolgungs Sitzung (Leistung).</span><span class="sxs-lookup"><span data-stu-id="11e88-398">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="11e88-399">Rückgabe Daten</span><span class="sxs-lookup"><span data-stu-id="11e88-399">Return data</span></span>
* <span data-ttu-id="11e88-400">Gibt die ETL-Ablauf Verfolgungs Datei zurück.</span><span class="sxs-lookup"><span data-stu-id="11e88-400">Returns the trace ETL file</span></span>

<span data-ttu-id="11e88-401">**/API/WPR/Trace (Post)**</span><span class="sxs-lookup"><span data-stu-id="11e88-401">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="11e88-402">Startet eine Ablauf Verfolgungs Sitzung für WPR (Leistung).</span><span class="sxs-lookup"><span data-stu-id="11e88-402">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="11e88-403">Parameter</span><span class="sxs-lookup"><span data-stu-id="11e88-403">Parameters</span></span>
* <span data-ttu-id="11e88-404">Profil Profilname.</span><span class="sxs-lookup"><span data-stu-id="11e88-404">profile : Profile name.</span></span> <span data-ttu-id="11e88-405">Verfügbare Profile werden in "perfprofiles/Profiles. JSON" gespeichert.</span><span class="sxs-lookup"><span data-stu-id="11e88-405">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="11e88-406">Rückgabe Daten</span><span class="sxs-lookup"><span data-stu-id="11e88-406">Return data</span></span>
* <span data-ttu-id="11e88-407">Beim Start wird der WPR-Sitzungs Status zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="11e88-407">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="11e88-408">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="11e88-408">See also</span></span>
* [<span data-ttu-id="11e88-409">Verwenden des Windows-Geräteportals</span><span class="sxs-lookup"><span data-stu-id="11e88-409">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="11e88-410">API-Referenz für den Geräte Portal (UWP)</span><span class="sxs-lookup"><span data-stu-id="11e88-410">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
