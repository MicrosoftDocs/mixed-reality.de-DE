---
title: Referenz der Geräteportal-API
description: API-Referenz für das Windows-Geräte Portal auf hololens
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Hololens, Windows-Geräte Portal, API
ms.openlocfilehash: 8c9d60f458cddd3ba258aed0ee82f7aa16c10ba6
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/12/2020
ms.locfileid: "83227958"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="21ffa-104">Referenz der Geräteportal-API</span><span class="sxs-lookup"><span data-stu-id="21ffa-104">Device portal API reference</span></span>

<span data-ttu-id="21ffa-105">Alles im [Windows-Geräte Portal](using-the-windows-device-portal.md) baut auf der Rest-API auf, mit der Sie auf die Daten zugreifen und Ihr Gerät Programm gesteuert steuern können.</span><span class="sxs-lookup"><span data-stu-id="21ffa-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="21ffa-106">App-Verlagerung</span><span class="sxs-lookup"><span data-stu-id="21ffa-106">App deloyment</span></span>

<span data-ttu-id="21ffa-107">**/API/APP/packagemanager/Package (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="21ffa-108">Deinstalliert eine APP</span><span class="sxs-lookup"><span data-stu-id="21ffa-108">Uninstalls an app</span></span>

<span data-ttu-id="21ffa-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-109">Parameters</span></span>
* <span data-ttu-id="21ffa-110">Package: der Dateiname des Pakets, das deinstalliert werden soll.</span><span class="sxs-lookup"><span data-stu-id="21ffa-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="21ffa-111">**/API/APP/packagemanager/Package (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="21ffa-112">Installiert eine APP</span><span class="sxs-lookup"><span data-stu-id="21ffa-112">Installs an App</span></span>

<span data-ttu-id="21ffa-113">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-113">Parameters</span></span>
* <span data-ttu-id="21ffa-114">Package: der Dateiname des zu installierenden Pakets.</span><span class="sxs-lookup"><span data-stu-id="21ffa-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="21ffa-115">Nutzlast</span><span class="sxs-lookup"><span data-stu-id="21ffa-115">Payload</span></span>
* <span data-ttu-id="21ffa-116">Mehrteilige konforme HTTP-Text</span><span class="sxs-lookup"><span data-stu-id="21ffa-116">multi-part conforming http body</span></span>

<span data-ttu-id="21ffa-117">**/API/APP/packagemanager/Packages (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="21ffa-118">Hiermit wird die Liste der installierten apps auf dem System mit Details abgerufen.</span><span class="sxs-lookup"><span data-stu-id="21ffa-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="21ffa-119">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="21ffa-119">Return data</span></span>
* <span data-ttu-id="21ffa-120">Liste der installierten Pakete mit Details</span><span class="sxs-lookup"><span data-stu-id="21ffa-120">List of installed packages with details</span></span>

<span data-ttu-id="21ffa-121">**/API/APP/packagemanager/State (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="21ffa-122">Hiermit wird der Status der Installation in Progress-App abgerufen.</span><span class="sxs-lookup"><span data-stu-id="21ffa-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="21ffa-123">Absturzabbildsammlung</span><span class="sxs-lookup"><span data-stu-id="21ffa-123">Dump collection</span></span>

<span data-ttu-id="21ffa-124">**/API/Debug/Dump/Usermode/CrashControl (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="21ffa-125">Deaktiviert die Absturz Abbild Erfassung für eine Sideload-app.</span><span class="sxs-lookup"><span data-stu-id="21ffa-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="21ffa-126">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-126">Parameters</span></span>
* <span data-ttu-id="21ffa-127">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="21ffa-127">packageFullname : package name</span></span>

<span data-ttu-id="21ffa-128">**/API/Debug/Dump/Usermode/CrashControl (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="21ffa-129">Ruft Einstellungen für die Absturz Abbild Erfassung von Sideload-apps ab</span><span class="sxs-lookup"><span data-stu-id="21ffa-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="21ffa-130">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-130">Parameters</span></span>
* <span data-ttu-id="21ffa-131">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="21ffa-131">packageFullname : package name</span></span>

<span data-ttu-id="21ffa-132">**/API/Debug/Dump/Usermode/CrashControl (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="21ffa-133">Aktiviert und legt Sicherungs Steuerungseinstellungen für eine per Sideload übertragene App fest.</span><span class="sxs-lookup"><span data-stu-id="21ffa-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="21ffa-134">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-134">Parameters</span></span>
* <span data-ttu-id="21ffa-135">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="21ffa-135">packageFullname : package name</span></span>

<span data-ttu-id="21ffa-136">**/API/Debug/Dump/Usermode/crashdump (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="21ffa-137">Löscht einen Absturz Abbild für eine Sideload-app.</span><span class="sxs-lookup"><span data-stu-id="21ffa-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="21ffa-138">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-138">Parameters</span></span>
* <span data-ttu-id="21ffa-139">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="21ffa-139">packageFullname : package name</span></span>
* <span data-ttu-id="21ffa-140">Dateiname: Name der Sicherungsdatei</span><span class="sxs-lookup"><span data-stu-id="21ffa-140">fileName : dump file name</span></span>

<span data-ttu-id="21ffa-141">**/API/Debug/Dump/Usermode/crashdump (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="21ffa-142">Ruft ein Absturz Abbild für eine per Sideload übertragene App ab.</span><span class="sxs-lookup"><span data-stu-id="21ffa-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="21ffa-143">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-143">Parameters</span></span>
* <span data-ttu-id="21ffa-144">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="21ffa-144">packageFullname : package name</span></span>
* <span data-ttu-id="21ffa-145">Dateiname: Name der Sicherungsdatei</span><span class="sxs-lookup"><span data-stu-id="21ffa-145">fileName : dump file name</span></span>

<span data-ttu-id="21ffa-146">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="21ffa-146">Return data</span></span>
* <span data-ttu-id="21ffa-147">Dumpdatei.</span><span class="sxs-lookup"><span data-stu-id="21ffa-147">Dump file.</span></span> <span data-ttu-id="21ffa-148">Überprüfen mit WinDbg oder Visual Studio</span><span class="sxs-lookup"><span data-stu-id="21ffa-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="21ffa-149">**/API/Debug/Dump/Usermode/Dumps (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="21ffa-150">Gibt eine Liste aller Absturz Abbilder für Sideload-apps zurück.</span><span class="sxs-lookup"><span data-stu-id="21ffa-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="21ffa-151">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="21ffa-151">Return data</span></span>
* <span data-ttu-id="21ffa-152">Liste der Absturz Abbilder pro Seite geladener apps</span><span class="sxs-lookup"><span data-stu-id="21ffa-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="21ffa-153">ETW</span><span class="sxs-lookup"><span data-stu-id="21ffa-153">ETW</span></span>

<span data-ttu-id="21ffa-154">**/API/etw/Providers (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="21ffa-155">Listet registrierte Anbieter auf.</span><span class="sxs-lookup"><span data-stu-id="21ffa-155">Enumerates registered providers</span></span>

<span data-ttu-id="21ffa-156">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="21ffa-156">Return data</span></span>
* <span data-ttu-id="21ffa-157">Liste der Anbieter, Anzeige Name und GUID</span><span class="sxs-lookup"><span data-stu-id="21ffa-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="21ffa-158">**/API/etw/Session/Realtime (Get/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="21ffa-159">Erstellt eine ETW-Sitzung in Echtzeit. verwaltet über einen WebSocket.</span><span class="sxs-lookup"><span data-stu-id="21ffa-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="21ffa-160">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="21ffa-160">Return data</span></span>
* <span data-ttu-id="21ffa-161">ETW-Ereignisse von aktivierten Anbietern</span><span class="sxs-lookup"><span data-stu-id="21ffa-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="21ffa-162">Holographic – Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="21ffa-162">Holographic OS</span></span>

<span data-ttu-id="21ffa-163">**/API/Holographic/OS/etw/customproviders (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="21ffa-164">Gibt eine Liste von hololens-spezifischen etw-Anbietern zurück, die nicht beim System registriert sind.</span><span class="sxs-lookup"><span data-stu-id="21ffa-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="21ffa-165">**/API/Holographic/OS/Services (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="21ffa-166">Gibt die Zustände aller Dienste zurück, die ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="21ffa-166">Returns the states of all services running.</span></span>

<span data-ttu-id="21ffa-167">**/API/Holographic/OS/Settings/IPD (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="21ffa-168">Ruft die gespeicherte IPD (interpupranäre Entfernung) in Millimeter ab.</span><span class="sxs-lookup"><span data-stu-id="21ffa-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="21ffa-169">**/API/Holographic/OS/Settings/IPD (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="21ffa-170">Legt die IPD fest.</span><span class="sxs-lookup"><span data-stu-id="21ffa-170">Sets the IPD</span></span>

<span data-ttu-id="21ffa-171">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-171">Parameters</span></span>
* <span data-ttu-id="21ffa-172">IPD: neuer IPD-Wert, der in Millimeter festgelegt werden soll</span><span class="sxs-lookup"><span data-stu-id="21ffa-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="21ffa-173">**/API/Holographic/OS/Webmanagement/Settings/HTTPS (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="21ffa-174">Abrufen der HTTPS-Anforderungen für das Geräteportal</span><span class="sxs-lookup"><span data-stu-id="21ffa-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="21ffa-175">**/API/Holographic/OS/Webmanagement/Settings/HTTPS (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="21ffa-176">Legt die HTTPS-Anforderungen für das Geräte Portal fest.</span><span class="sxs-lookup"><span data-stu-id="21ffa-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="21ffa-177">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-177">Parameters</span></span>
* <span data-ttu-id="21ffa-178">erforderlich: Ja, Nein oder Standard</span><span class="sxs-lookup"><span data-stu-id="21ffa-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="21ffa-179">Holografische Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="21ffa-179">Holographic Perception</span></span>

<span data-ttu-id="21ffa-180">**/API/Holographic/perception/Client (Get/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="21ffa-181">Akzeptiert WebSocket-Upgrades und führt einen perception-Client aus, der Updates bei 30 fps sendet.</span><span class="sxs-lookup"><span data-stu-id="21ffa-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="21ffa-182">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-182">Parameters</span></span>
* <span data-ttu-id="21ffa-183">clientmode: "aktiv" erzwingt den visuellen Überwachungsmodus, wenn er nicht passiv festgelegt werden kann.</span><span class="sxs-lookup"><span data-stu-id="21ffa-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="21ffa-184">Holographic-Therme</span><span class="sxs-lookup"><span data-stu-id="21ffa-184">Holographic Thermal</span></span>

<span data-ttu-id="21ffa-185">**/API/Holographic/Thermal/Stage (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="21ffa-186">Die wärmestufe des Geräts erhalten (0 normal, 1 warm, 2 kritisch)</span><span class="sxs-lookup"><span data-stu-id="21ffa-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="21ffa-187">Wahrnehmungs Simulations-Steuerelement</span><span class="sxs-lookup"><span data-stu-id="21ffa-187">Perception Simulation Control</span></span>

<span data-ttu-id="21ffa-188">**/API/Holographic/Simulation/Control/Mode (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="21ffa-189">Simulationsmodus erhalten</span><span class="sxs-lookup"><span data-stu-id="21ffa-189">Get the simulation mode</span></span>

<span data-ttu-id="21ffa-190">**/API/Holographic/Simulation/Control/Mode (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="21ffa-191">Festlegen des Simulationsmodus</span><span class="sxs-lookup"><span data-stu-id="21ffa-191">Set the simulation mode</span></span>

<span data-ttu-id="21ffa-192">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-192">Parameters</span></span>
* <span data-ttu-id="21ffa-193">Mode: Simulationsmodus: Standard, Simulation, Remote, Legacy</span><span class="sxs-lookup"><span data-stu-id="21ffa-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="21ffa-194">**/API/Holographic/Simulation/Control/Stream (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="21ffa-195">Löscht einen Steuerungsdaten Strom.</span><span class="sxs-lookup"><span data-stu-id="21ffa-195">Delete a control stream.</span></span>

<span data-ttu-id="21ffa-196">**/API/Holographic/Simulation/Control/Stream (Get/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="21ffa-197">Öffnen Sie eine websocketverbindung für einen Steuerungsdaten Strom.</span><span class="sxs-lookup"><span data-stu-id="21ffa-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="21ffa-198">**/API/Holographic/Simulation/Control/Stream (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="21ffa-199">Erstellen Sie einen Steuerungsdaten Strom (Priorität ist erforderlich), oder stellen Sie Daten in einem erstellten Stream bereit (streamid erforderlich).</span><span class="sxs-lookup"><span data-stu-id="21ffa-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="21ffa-200">Es wird erwartet, dass für die Daten der Typ "Application/Octett-Stream" festgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="21ffa-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="21ffa-201">**/API/Holographic/Simulation/Display/Stream (Get/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-201">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="21ffa-202">Fordern Sie einen Simulations Videostream mit dem Inhalt an, der im Simulationsmodus für die System Anzeige gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="21ffa-202">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="21ffa-203">Anfänglich wird ein einfacher Format Deskriptor Header gesendet, gefolgt von H. 264-codierten Texturen, denen jeweils ein Header vorangestellt ist, der den Augen Index und die Textur Größe angibt.</span><span class="sxs-lookup"><span data-stu-id="21ffa-203">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="21ffa-204">Wiedergabe von Wahrnehmungs Simulationen</span><span class="sxs-lookup"><span data-stu-id="21ffa-204">Perception Simulation Playback</span></span>

<span data-ttu-id="21ffa-205">**/API/Holographic/Simulation/Playback/File (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-205">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="21ffa-206">Löschen Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="21ffa-206">Delete a recording.</span></span>

<span data-ttu-id="21ffa-207">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-207">Parameters</span></span>
* <span data-ttu-id="21ffa-208">Aufzeichnung: Name der zu löschenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="21ffa-208">recording : Name of recording to delete.</span></span>

<span data-ttu-id="21ffa-209">**/API/Holographic/Simulation/Playback/File (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-209">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="21ffa-210">Hochladen einer Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="21ffa-210">Upload a recording.</span></span>

<span data-ttu-id="21ffa-211">**/API/Holographic/Simulation/Playback/Files (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-211">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="21ffa-212">Alle Aufzeichnungen erhalten.</span><span class="sxs-lookup"><span data-stu-id="21ffa-212">Get all recordings.</span></span>

<span data-ttu-id="21ffa-213">**/API/Holographic/Simulation/Playback/Session (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-213">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="21ffa-214">Gibt den aktuellen Wiedergabe Zustand einer Aufzeichnung an.</span><span class="sxs-lookup"><span data-stu-id="21ffa-214">Get the current playback state of a recording.</span></span>

<span data-ttu-id="21ffa-215">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-215">Parameters</span></span>
* <span data-ttu-id="21ffa-216">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="21ffa-216">recording : Name of recording.</span></span>

<span data-ttu-id="21ffa-217">**/API/Holographic/Simulation/Playback/Session/File (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-217">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="21ffa-218">Entladen Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="21ffa-218">Unload a recording.</span></span>

<span data-ttu-id="21ffa-219">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-219">Parameters</span></span>
* <span data-ttu-id="21ffa-220">Aufzeichnung: Name der zu entladenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="21ffa-220">recording : Name of recording to unload.</span></span>

<span data-ttu-id="21ffa-221">**/API/Holographic/Simulation/Playback/Session/File (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-221">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="21ffa-222">Laden Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="21ffa-222">Load a recording.</span></span>

<span data-ttu-id="21ffa-223">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-223">Parameters</span></span>
* <span data-ttu-id="21ffa-224">Aufzeichnung: Name der zu ladenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="21ffa-224">recording : Name of recording to load.</span></span>

<span data-ttu-id="21ffa-225">**/API/Holographic/Simulation/Playback/Session/Files (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-225">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="21ffa-226">Alle geladenen Aufzeichnungen erhalten.</span><span class="sxs-lookup"><span data-stu-id="21ffa-226">Get all loaded recordings.</span></span>

<span data-ttu-id="21ffa-227">**/API/Holographic/Simulation/Playback/Session/Pause (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-227">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="21ffa-228">Hält eine Aufzeichnung an.</span><span class="sxs-lookup"><span data-stu-id="21ffa-228">Pause a recording.</span></span>

<span data-ttu-id="21ffa-229">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-229">Parameters</span></span>
* <span data-ttu-id="21ffa-230">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="21ffa-230">recording : Name of recording.</span></span>

<span data-ttu-id="21ffa-231">**/API/Holographic/Simulation/Playback/Session/Play (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-231">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="21ffa-232">Wiedergabe einer Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="21ffa-232">Play a recording.</span></span>

<span data-ttu-id="21ffa-233">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-233">Parameters</span></span>
* <span data-ttu-id="21ffa-234">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="21ffa-234">recording : Name of recording.</span></span>

<span data-ttu-id="21ffa-235">**/API/Holographic/Simulation/Playback/Session/Stop (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-235">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="21ffa-236">Beendet eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="21ffa-236">Stop a recording.</span></span>

<span data-ttu-id="21ffa-237">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-237">Parameters</span></span>
* <span data-ttu-id="21ffa-238">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="21ffa-238">recording : Name of recording.</span></span>

<span data-ttu-id="21ffa-239">**/API/Holographic/Simulation/Playback/Session/Types (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-239">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="21ffa-240">Datentypen in einer geladenen Aufzeichnung erhalten.</span><span class="sxs-lookup"><span data-stu-id="21ffa-240">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="21ffa-241">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-241">Parameters</span></span>
* <span data-ttu-id="21ffa-242">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="21ffa-242">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="21ffa-243">Erfassung von Wahrnehmungs Simulationen</span><span class="sxs-lookup"><span data-stu-id="21ffa-243">Perception Simulation Recording</span></span>

<span data-ttu-id="21ffa-244">**/API/Holographic/Simulation/Recording/Start (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-244">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="21ffa-245">Startet eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="21ffa-245">Start a recording.</span></span> <span data-ttu-id="21ffa-246">Nur eine einzelne Aufzeichnung kann gleichzeitig aktiv sein.</span><span class="sxs-lookup"><span data-stu-id="21ffa-246">Only a single recording can be active at once.</span></span> <span data-ttu-id="21ffa-247">Eine der Köpfe, Hände, spatialmapping oder Umgebung muss festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="21ffa-247">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="21ffa-248">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-248">Parameters</span></span>
* <span data-ttu-id="21ffa-249">Head: Legen Sie auf 1 fest, um Head-Daten aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="21ffa-249">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="21ffa-250">Hands: wird auf 1 festgelegt, um die Daten aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="21ffa-250">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="21ffa-251">spatialmapping: auf 1 festgelegt, um die räumliche Zuordnung aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="21ffa-251">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="21ffa-252">Umgebung: Legen Sie auf 1 fest, um Umgebungs Daten aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="21ffa-252">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="21ffa-253">Name: der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="21ffa-253">name : Name of the recording.</span></span>
* <span data-ttu-id="21ffa-254">singlespatialmappingframe: wird auf 1 festgelegt, um nur einen einzelnen räumlichen zuordnungsframe aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="21ffa-254">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="21ffa-255">**/API/Holographic/Simulation/Recording/Status (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-255">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="21ffa-256">Aufzeichnungsstatus erhalten.</span><span class="sxs-lookup"><span data-stu-id="21ffa-256">Get recording state.</span></span>

<span data-ttu-id="21ffa-257">**/API/Holographic/Simulation/Recording/Stop (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-257">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="21ffa-258">Hält die aktuelle Aufzeichnung an.</span><span class="sxs-lookup"><span data-stu-id="21ffa-258">Stop the current recording.</span></span> <span data-ttu-id="21ffa-259">Die Aufzeichnung wird als Datei zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="21ffa-259">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="21ffa-260">Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="21ffa-260">Mixed Reality Capture</span></span>

<span data-ttu-id="21ffa-261">**/API/Holographic/MRC/File (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-261">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="21ffa-262">Hiermit wird eine gemischte Reality-Datei vom Gerät heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="21ffa-262">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="21ffa-263">Verwenden Sie den OP = Stream-Abfrage Parameter für das Streaming.</span><span class="sxs-lookup"><span data-stu-id="21ffa-263">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="21ffa-264">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-264">Parameters</span></span>
* <span data-ttu-id="21ffa-265">Dateiname: Name, hex64-codiert, der einzurufenden Videodatei</span><span class="sxs-lookup"><span data-stu-id="21ffa-265">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="21ffa-266">OP: Stream</span><span class="sxs-lookup"><span data-stu-id="21ffa-266">op : stream</span></span>

<span data-ttu-id="21ffa-267">**/API/Holographic/MRC/File (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-267">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="21ffa-268">Löscht eine gemischte Reality-Aufzeichnung auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="21ffa-268">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="21ffa-269">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-269">Parameters</span></span>
* <span data-ttu-id="21ffa-270">Dateiname: Name, hex64-codiert, der zu löschenden Datei</span><span class="sxs-lookup"><span data-stu-id="21ffa-270">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="21ffa-271">**/API/Holographic/MRC/Files (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-271">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="21ffa-272">Gibt die Liste der Mixed Reality-Dateien zurück, die auf dem Gerät gespeichert sind</span><span class="sxs-lookup"><span data-stu-id="21ffa-272">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="21ffa-273">**/API/Holographic/MRC/Photo (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-273">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="21ffa-274">Nimmt ein gemischtes Reality-Foto und erstellt eine Datei auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="21ffa-274">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="21ffa-275">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-275">Parameters</span></span>
* <span data-ttu-id="21ffa-276">hololens: Erfassungs holograms: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="21ffa-276">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="21ffa-277">PV: Erfassen der PV-Kamera: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="21ffa-277">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="21ffa-278">Renderfromcamera: (hololens 2) renderingaus Perspektive der Foto-/Videokamera: true oder false (Standardwert: true)</span><span class="sxs-lookup"><span data-stu-id="21ffa-278">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="21ffa-279">**/API/Holographic/MRC/Settings (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-279">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="21ffa-280">Ruft die Standardeinstellungen für die gemischte Realität-Erfassung ab.</span><span class="sxs-lookup"><span data-stu-id="21ffa-280">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="21ffa-281">**/API/Holographic/MRC/Settings (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-281">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="21ffa-282">Legt die Standardeinstellungen für die gemischte Reality-Erfassung fest.</span><span class="sxs-lookup"><span data-stu-id="21ffa-282">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="21ffa-283">Einige dieser Einstellungen werden auf das MRC-Foto und die Video Erfassung des Systems angewendet.</span><span class="sxs-lookup"><span data-stu-id="21ffa-283">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="21ffa-284">**/API/Holographic/MRC/Status (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-284">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="21ffa-285">Ruft den Status der aufgezeichnete gemischten Realität ab (wird ausgeführt, beendet).</span><span class="sxs-lookup"><span data-stu-id="21ffa-285">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="21ffa-286">**/API/Holographic/MRC/Thumbnail (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-286">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="21ffa-287">Ruft das Miniaturbild für die angegebene Datei ab.</span><span class="sxs-lookup"><span data-stu-id="21ffa-287">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="21ffa-288">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-288">Parameters</span></span>
* <span data-ttu-id="21ffa-289">Dateiname: Name, hex64-codiert, der Datei, für die die Miniaturansicht angefordert wird</span><span class="sxs-lookup"><span data-stu-id="21ffa-289">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="21ffa-290">**/API/Holographic/MRC/Video/Control/Start (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-290">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="21ffa-291">Startet eine gemischte Reality-Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="21ffa-291">Starts a mixed reality recording</span></span>

<span data-ttu-id="21ffa-292">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-292">Parameters</span></span>
* <span data-ttu-id="21ffa-293">hololens: Erfassungs holograms: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="21ffa-293">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="21ffa-294">PV: Erfassen der PV-Kamera: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="21ffa-294">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="21ffa-295">MIC: Mikrofon erfassen: true oder false (standardmäßig false)</span><span class="sxs-lookup"><span data-stu-id="21ffa-295">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="21ffa-296">Loopback: App-Audioerfassung: true oder false (standardmäßig false)</span><span class="sxs-lookup"><span data-stu-id="21ffa-296">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="21ffa-297">Renderfromcamera: (hololens 2) renderingaus Perspektive der Foto-/Videokamera: true oder false (Standardwert: true)</span><span class="sxs-lookup"><span data-stu-id="21ffa-297">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="21ffa-298">Vstab: (nur hololens 2) Videostabilisierung aktivieren: true oder false (Standardwert: true)</span><span class="sxs-lookup"><span data-stu-id="21ffa-298">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="21ffa-299">vstabbuffer: (hololens 2), Video Stabilisierungs Puffer Latenz: 0 bis 30 Frames (standardmäßig 15 Frames)</span><span class="sxs-lookup"><span data-stu-id="21ffa-299">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="21ffa-300">**/API/Holographic/MRC/Video/Control/Stop (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-300">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="21ffa-301">Beendet die aktuelle gemischte Reality-Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="21ffa-301">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="21ffa-302">Streaming mit gemischter Realität</span><span class="sxs-lookup"><span data-stu-id="21ffa-302">Mixed Reality Streaming</span></span>

<span data-ttu-id="21ffa-303">Hololens unterstützt die Live Vorschau von Mixed Reality über einen segmentierten Download einer fragmentierten MP4-Datei.</span><span class="sxs-lookup"><span data-stu-id="21ffa-303">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="21ffa-304">Gemischte Reality-Streams verwenden denselben Satz von Parametern, um zu steuern, was aufgezeichnet wird:</span><span class="sxs-lookup"><span data-stu-id="21ffa-304">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="21ffa-305">hololens: Erfassungs holograms: true oder false</span><span class="sxs-lookup"><span data-stu-id="21ffa-305">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="21ffa-306">PV: Erfassen der PV-Kamera: true oder false</span><span class="sxs-lookup"><span data-stu-id="21ffa-306">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="21ffa-307">MIC: Mikrofon erfassen: true oder false</span><span class="sxs-lookup"><span data-stu-id="21ffa-307">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="21ffa-308">Loopback: App-Audioerfassung: true oder false</span><span class="sxs-lookup"><span data-stu-id="21ffa-308">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="21ffa-309">Wenn keines dieser Angaben angegeben ist: holograms, Foto-/Videokamera und App-Audiodaten werden aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="21ffa-309">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="21ffa-310">Wenn eine Angabe festgelegt ist: die nicht angegebenen Parameter werden standardmäßig auf false festgelegt.</span><span class="sxs-lookup"><span data-stu-id="21ffa-310">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="21ffa-311">Optionale Parameter (nur hololens 2)</span><span class="sxs-lookup"><span data-stu-id="21ffa-311">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="21ffa-312">Renderfromcamera: Rendering aus Perspektive der Foto-/Videokamera: true oder false (Standardwert ist true)</span><span class="sxs-lookup"><span data-stu-id="21ffa-312">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="21ffa-313">Vstab: Videostabilisierung aktivieren: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="21ffa-313">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="21ffa-314">vstabbuffer: Puffer Wartezeit für Videostabilisierung: zwischen 0 und 30 Frames (standardmäßig 15 Frames)</span><span class="sxs-lookup"><span data-stu-id="21ffa-314">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="21ffa-315">**/API/Holographic/Stream/Live.MP4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-315">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="21ffa-316">Ein-Datenstrom von 1280x720p 30 fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="21ffa-316">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="21ffa-317">**/API/Holographic/Stream/live_high. MP4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-317">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="21ffa-318">Ein-Datenstrom von 1280x720p 30 fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="21ffa-318">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="21ffa-319">**/API/Holographic/Stream/live_med. MP4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-319">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="21ffa-320">Ein 854x480p 30 fps 2.5 MBit-Stream.</span><span class="sxs-lookup"><span data-stu-id="21ffa-320">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="21ffa-321">**/API/Holographic/Stream/live_low. MP4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-321">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="21ffa-322">Ein 428x240 p 15fps 0.6-MBit-Stream.</span><span class="sxs-lookup"><span data-stu-id="21ffa-322">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="21ffa-323">Netzwerk</span><span class="sxs-lookup"><span data-stu-id="21ffa-323">Networking</span></span>

<span data-ttu-id="21ffa-324">**/API/Networking/ipconfig (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-324">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="21ffa-325">Ruft die aktuelle IP-Konfiguration ab.</span><span class="sxs-lookup"><span data-stu-id="21ffa-325">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="21ffa-326">Betriebssysteminformationen</span><span class="sxs-lookup"><span data-stu-id="21ffa-326">OS Information</span></span>

<span data-ttu-id="21ffa-327">**/API/OS/Info (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-327">**/api/os/info (GET)**</span></span>

<span data-ttu-id="21ffa-328">Ruft Betriebssysteminformationen ab.</span><span class="sxs-lookup"><span data-stu-id="21ffa-328">Gets operating system information</span></span>

<span data-ttu-id="21ffa-329">**/API/OS/MachineName (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-329">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="21ffa-330">Ruft den Computernamen ab.</span><span class="sxs-lookup"><span data-stu-id="21ffa-330">Gets the machine name</span></span>

<span data-ttu-id="21ffa-331">**/API/OS/MachineName (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-331">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="21ffa-332">Legt den Computernamen fest.</span><span class="sxs-lookup"><span data-stu-id="21ffa-332">Sets the machine name</span></span>

<span data-ttu-id="21ffa-333">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-333">Parameters</span></span>
* <span data-ttu-id="21ffa-334">Name: neuer Computername, hex64-codiert, festgelegt auf</span><span class="sxs-lookup"><span data-stu-id="21ffa-334">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="21ffa-335">Leistungsdaten</span><span class="sxs-lookup"><span data-stu-id="21ffa-335">Performance data</span></span>

<span data-ttu-id="21ffa-336">**/API/ResourceManager/Processes (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-336">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="21ffa-337">Gibt die Liste der laufenden Prozesse mit Details zurück.</span><span class="sxs-lookup"><span data-stu-id="21ffa-337">Returns the list of running processes with details</span></span>

<span data-ttu-id="21ffa-338">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="21ffa-338">Return data</span></span>
* <span data-ttu-id="21ffa-339">JSON mit einer Liste der Prozesse und Details für jeden Prozess</span><span class="sxs-lookup"><span data-stu-id="21ffa-339">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="21ffa-340">**/API/ResourceManager/systemperf (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-340">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="21ffa-341">Gibt die System Leistungsstatistik (e/a-Lese-/Schreibvorgänge, Speicher Statistiken usw.) zurück.</span><span class="sxs-lookup"><span data-stu-id="21ffa-341">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="21ffa-342">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="21ffa-342">Return data</span></span>
* <span data-ttu-id="21ffa-343">JSON mit Systeminformationen: CPU, GPU, Arbeitsspeicher, Netzwerk, e/a</span><span class="sxs-lookup"><span data-stu-id="21ffa-343">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="21ffa-344">Power</span><span class="sxs-lookup"><span data-stu-id="21ffa-344">Power</span></span>

<span data-ttu-id="21ffa-345">**/API/Power/Battery (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-345">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="21ffa-346">Ruft den aktuellen Akku Zustand ab.</span><span class="sxs-lookup"><span data-stu-id="21ffa-346">Gets the current battery state</span></span>

<span data-ttu-id="21ffa-347">**/API/Power/State (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-347">**/api/power/state (GET)**</span></span>

<span data-ttu-id="21ffa-348">Prüft, ob sich das System in einem niedrigen Energiezustand befindet</span><span class="sxs-lookup"><span data-stu-id="21ffa-348">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="21ffa-349">Remotesteuerung</span><span class="sxs-lookup"><span data-stu-id="21ffa-349">Remote Control</span></span>

<span data-ttu-id="21ffa-350">**/API/Control/Restart (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-350">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="21ffa-351">Startet das Zielgerät neu.</span><span class="sxs-lookup"><span data-stu-id="21ffa-351">Restarts the target device</span></span>

<span data-ttu-id="21ffa-352">**/API/Control/Shutdown (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-352">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="21ffa-353">Fährt das Zielgerät herunter.</span><span class="sxs-lookup"><span data-stu-id="21ffa-353">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="21ffa-354">Task-Manager</span><span class="sxs-lookup"><span data-stu-id="21ffa-354">Task Manager</span></span>

<span data-ttu-id="21ffa-355">**/API/Taskmanager/app (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-355">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="21ffa-356">Beendet eine moderne App</span><span class="sxs-lookup"><span data-stu-id="21ffa-356">Stops a modern app</span></span>

<span data-ttu-id="21ffa-357">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-357">Parameters</span></span>
* <span data-ttu-id="21ffa-358">Package: vollständiger Name des App-Pakets, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="21ffa-358">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="21ffa-359">forcestop: erzwingen, dass alle Prozesse beendet werden (= yes)</span><span class="sxs-lookup"><span data-stu-id="21ffa-359">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="21ffa-360">**/API/Taskmanager/app (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-360">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="21ffa-361">Startet eine moderne App</span><span class="sxs-lookup"><span data-stu-id="21ffa-361">Starts a modern app</span></span>

<span data-ttu-id="21ffa-362">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-362">Parameters</span></span>
* <span data-ttu-id="21ffa-363">AppID: Praid der zu startenden APP, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="21ffa-363">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="21ffa-364">Package: vollständiger Name des App-Pakets, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="21ffa-364">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="21ffa-365">WiFi-Verwaltung</span><span class="sxs-lookup"><span data-stu-id="21ffa-365">WiFi Management</span></span>

<span data-ttu-id="21ffa-366">**/API/WiFi/Interfaces (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-366">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="21ffa-367">Listet drahtlose Netzwerkschnittstellen auf.</span><span class="sxs-lookup"><span data-stu-id="21ffa-367">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="21ffa-368">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="21ffa-368">Return data</span></span>
* <span data-ttu-id="21ffa-369">Liste der drahtlos Schnittstellen mit Details (GUID, Beschreibung usw.)</span><span class="sxs-lookup"><span data-stu-id="21ffa-369">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="21ffa-370">**/API/WiFi/Network (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-370">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="21ffa-371">Löscht ein Profil, das einem Netzwerk in einer angegebenen Schnittstelle zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="21ffa-371">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="21ffa-372">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-372">Parameters</span></span>
* <span data-ttu-id="21ffa-373">Schnittstelle: GUID der Netzwerkschnittstelle</span><span class="sxs-lookup"><span data-stu-id="21ffa-373">interface : network interface guid</span></span>
* <span data-ttu-id="21ffa-374">Profil: Profilname</span><span class="sxs-lookup"><span data-stu-id="21ffa-374">profile : profile name</span></span>

<span data-ttu-id="21ffa-375">**/API/WiFi/Networks (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-375">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="21ffa-376">Listet drahtlose Netzwerke auf der angegebenen Netzwerkschnittstelle auf.</span><span class="sxs-lookup"><span data-stu-id="21ffa-376">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="21ffa-377">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-377">Parameters</span></span>
* <span data-ttu-id="21ffa-378">Schnittstelle: GUID der Netzwerkschnittstelle</span><span class="sxs-lookup"><span data-stu-id="21ffa-378">interface : network interface guid</span></span>

<span data-ttu-id="21ffa-379">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="21ffa-379">Return data</span></span>
* <span data-ttu-id="21ffa-380">Liste der Drahtlos Netzwerke, die sich auf der Netzwerkschnittstelle befinden, mit Details</span><span class="sxs-lookup"><span data-stu-id="21ffa-380">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="21ffa-381">**/API/WiFi/Network (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-381">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="21ffa-382">Stellt eine Verbindung mit einem Netzwerk auf der angegebenen Schnittstelle her oder trennt es.</span><span class="sxs-lookup"><span data-stu-id="21ffa-382">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="21ffa-383">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-383">Parameters</span></span>
* <span data-ttu-id="21ffa-384">Schnittstelle: GUID der Netzwerkschnittstelle</span><span class="sxs-lookup"><span data-stu-id="21ffa-384">interface : network interface guid</span></span>
* <span data-ttu-id="21ffa-385">SSID: SSID, hex64-codiert, um eine Verbindung herzustellen</span><span class="sxs-lookup"><span data-stu-id="21ffa-385">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="21ffa-386">OP: verbinden oder trennen</span><span class="sxs-lookup"><span data-stu-id="21ffa-386">op : connect or disconnect</span></span>
* <span data-ttu-id="21ffa-387">kreateprofile: Ja oder Nein</span><span class="sxs-lookup"><span data-stu-id="21ffa-387">createprofile : yes or no</span></span>
* <span data-ttu-id="21ffa-388">Schlüssel: gemeinsam verwendeter Schlüssel, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="21ffa-388">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="21ffa-389">Windows Performance Recorder</span><span class="sxs-lookup"><span data-stu-id="21ffa-389">Windows Performance Recorder</span></span>

<span data-ttu-id="21ffa-390">**/API/WPR/customtrace (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-390">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="21ffa-391">Lädt ein WPR-Profil hoch und startet die Ablauf Verfolgung mithilfe des hochgeladenen Profils.</span><span class="sxs-lookup"><span data-stu-id="21ffa-391">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="21ffa-392">Nutzlast</span><span class="sxs-lookup"><span data-stu-id="21ffa-392">Payload</span></span>
* <span data-ttu-id="21ffa-393">Mehrteilige konforme HTTP-Text</span><span class="sxs-lookup"><span data-stu-id="21ffa-393">multi-part conforming http body</span></span>

<span data-ttu-id="21ffa-394">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="21ffa-394">Return data</span></span>
* <span data-ttu-id="21ffa-395">Gibt den WPR-Sitzungsstatus zurück.</span><span class="sxs-lookup"><span data-stu-id="21ffa-395">Returns the WPR session status.</span></span>

<span data-ttu-id="21ffa-396">**/API/WPR/Status (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-396">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="21ffa-397">Ruft den Status der WPR-Sitzung ab.</span><span class="sxs-lookup"><span data-stu-id="21ffa-397">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="21ffa-398">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="21ffa-398">Return data</span></span>
* <span data-ttu-id="21ffa-399">WPR-Sitzungs Status.</span><span class="sxs-lookup"><span data-stu-id="21ffa-399">WPR session status.</span></span>

<span data-ttu-id="21ffa-400">**/API/WPR/Trace (Get)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-400">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="21ffa-401">Beendet eine WPR-Ablauf Verfolgungs Sitzung (Leistung).</span><span class="sxs-lookup"><span data-stu-id="21ffa-401">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="21ffa-402">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="21ffa-402">Return data</span></span>
* <span data-ttu-id="21ffa-403">Gibt die ETL-Ablauf Verfolgungs Datei zurück.</span><span class="sxs-lookup"><span data-stu-id="21ffa-403">Returns the trace ETL file</span></span>

<span data-ttu-id="21ffa-404">**/API/WPR/Trace (Post)**</span><span class="sxs-lookup"><span data-stu-id="21ffa-404">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="21ffa-405">Startet eine Ablauf Verfolgungs Sitzung für WPR (Leistung).</span><span class="sxs-lookup"><span data-stu-id="21ffa-405">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="21ffa-406">Parameter</span><span class="sxs-lookup"><span data-stu-id="21ffa-406">Parameters</span></span>
* <span data-ttu-id="21ffa-407">Profil: Profilname.</span><span class="sxs-lookup"><span data-stu-id="21ffa-407">profile : Profile name.</span></span> <span data-ttu-id="21ffa-408">Verfügbare Profile werden in "perfprofiles/Profiles. JSON" gespeichert.</span><span class="sxs-lookup"><span data-stu-id="21ffa-408">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="21ffa-409">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="21ffa-409">Return data</span></span>
* <span data-ttu-id="21ffa-410">Beim Start wird der WPR-Sitzungs Status zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="21ffa-410">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="21ffa-411">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="21ffa-411">See also</span></span>
* [<span data-ttu-id="21ffa-412">Verwenden des Windows-Geräteportals</span><span class="sxs-lookup"><span data-stu-id="21ffa-412">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="21ffa-413">API-Referenz für den Geräte Portal (UWP)</span><span class="sxs-lookup"><span data-stu-id="21ffa-413">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
