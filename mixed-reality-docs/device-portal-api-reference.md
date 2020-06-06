---
title: Referenz der Geräteportal-API
description: API-Referenz für das Windows-Geräte Portal auf hololens
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Hololens, Windows-Geräte Portal, API
ms.openlocfilehash: 17268c9a20d3da0ee90e5d6cead4342d3badf800
ms.sourcegitcommit: f24ac845e184c2f90e8b15adab9addb913f5cb83
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84451325"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="8a359-104">Referenz der Geräteportal-API</span><span class="sxs-lookup"><span data-stu-id="8a359-104">Device portal API reference</span></span>

<span data-ttu-id="8a359-105">Alles im [Windows-Geräte Portal](using-the-windows-device-portal.md) baut auf der Rest-API auf, mit der Sie auf die Daten zugreifen und Ihr Gerät Programm gesteuert steuern können.</span><span class="sxs-lookup"><span data-stu-id="8a359-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="8a359-106">App-Verlagerung</span><span class="sxs-lookup"><span data-stu-id="8a359-106">App deloyment</span></span>

<span data-ttu-id="8a359-107">**/API/APP/packagemanager/Package (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="8a359-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="8a359-108">Deinstalliert eine APP</span><span class="sxs-lookup"><span data-stu-id="8a359-108">Uninstalls an app</span></span>

<span data-ttu-id="8a359-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-109">Parameters</span></span>
* <span data-ttu-id="8a359-110">Package: der Dateiname des Pakets, das deinstalliert werden soll.</span><span class="sxs-lookup"><span data-stu-id="8a359-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="8a359-111">**/API/APP/packagemanager/Package (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="8a359-112">Installiert eine APP</span><span class="sxs-lookup"><span data-stu-id="8a359-112">Installs an App</span></span>

<span data-ttu-id="8a359-113">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-113">Parameters</span></span>
* <span data-ttu-id="8a359-114">Package: der Dateiname des zu installierenden Pakets.</span><span class="sxs-lookup"><span data-stu-id="8a359-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="8a359-115">Nutzlast</span><span class="sxs-lookup"><span data-stu-id="8a359-115">Payload</span></span>
* <span data-ttu-id="8a359-116">Mehrteilige konforme HTTP-Text</span><span class="sxs-lookup"><span data-stu-id="8a359-116">multi-part conforming http body</span></span>

<span data-ttu-id="8a359-117">**/API/APP/packagemanager/Packages (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="8a359-118">Hiermit wird die Liste der installierten apps auf dem System mit Details abgerufen.</span><span class="sxs-lookup"><span data-stu-id="8a359-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="8a359-119">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="8a359-119">Return data</span></span>
* <span data-ttu-id="8a359-120">Liste der installierten Pakete mit Details</span><span class="sxs-lookup"><span data-stu-id="8a359-120">List of installed packages with details</span></span>

<span data-ttu-id="8a359-121">**/API/APP/packagemanager/State (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="8a359-122">Hiermit wird der Status der Installation in Progress-App abgerufen.</span><span class="sxs-lookup"><span data-stu-id="8a359-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="8a359-123">Absturzabbildsammlung</span><span class="sxs-lookup"><span data-stu-id="8a359-123">Dump collection</span></span>

<span data-ttu-id="8a359-124">**/API/Debug/Dump/Usermode/CrashControl (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="8a359-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="8a359-125">Deaktiviert die Absturz Abbild Erfassung für eine Sideload-app.</span><span class="sxs-lookup"><span data-stu-id="8a359-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="8a359-126">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-126">Parameters</span></span>
* <span data-ttu-id="8a359-127">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="8a359-127">packageFullname : package name</span></span>

<span data-ttu-id="8a359-128">**/API/Debug/Dump/Usermode/CrashControl (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="8a359-129">Ruft Einstellungen für die Absturz Abbild Erfassung von Sideload-apps ab</span><span class="sxs-lookup"><span data-stu-id="8a359-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="8a359-130">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-130">Parameters</span></span>
* <span data-ttu-id="8a359-131">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="8a359-131">packageFullname : package name</span></span>

<span data-ttu-id="8a359-132">**/API/Debug/Dump/Usermode/CrashControl (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="8a359-133">Aktiviert und legt Sicherungs Steuerungseinstellungen für eine per Sideload übertragene App fest.</span><span class="sxs-lookup"><span data-stu-id="8a359-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="8a359-134">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-134">Parameters</span></span>
* <span data-ttu-id="8a359-135">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="8a359-135">packageFullname : package name</span></span>

<span data-ttu-id="8a359-136">**/API/Debug/Dump/Usermode/crashdump (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="8a359-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="8a359-137">Löscht einen Absturz Abbild für eine Sideload-app.</span><span class="sxs-lookup"><span data-stu-id="8a359-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="8a359-138">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-138">Parameters</span></span>
* <span data-ttu-id="8a359-139">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="8a359-139">packageFullname : package name</span></span>
* <span data-ttu-id="8a359-140">Dateiname: Name der Sicherungsdatei</span><span class="sxs-lookup"><span data-stu-id="8a359-140">fileName : dump file name</span></span>

<span data-ttu-id="8a359-141">**/API/Debug/Dump/Usermode/crashdump (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="8a359-142">Ruft ein Absturz Abbild für eine per Sideload übertragene App ab.</span><span class="sxs-lookup"><span data-stu-id="8a359-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="8a359-143">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-143">Parameters</span></span>
* <span data-ttu-id="8a359-144">packagefullname: Paketname</span><span class="sxs-lookup"><span data-stu-id="8a359-144">packageFullname : package name</span></span>
* <span data-ttu-id="8a359-145">Dateiname: Name der Sicherungsdatei</span><span class="sxs-lookup"><span data-stu-id="8a359-145">fileName : dump file name</span></span>

<span data-ttu-id="8a359-146">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="8a359-146">Return data</span></span>
* <span data-ttu-id="8a359-147">Dumpdatei.</span><span class="sxs-lookup"><span data-stu-id="8a359-147">Dump file.</span></span> <span data-ttu-id="8a359-148">Überprüfen mit WinDbg oder Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8a359-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="8a359-149">**/API/Debug/Dump/Usermode/Dumps (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="8a359-150">Gibt eine Liste aller Absturz Abbilder für Sideload-apps zurück.</span><span class="sxs-lookup"><span data-stu-id="8a359-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="8a359-151">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="8a359-151">Return data</span></span>
* <span data-ttu-id="8a359-152">Liste der Absturz Abbilder pro Seite geladener apps</span><span class="sxs-lookup"><span data-stu-id="8a359-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="8a359-153">ETW</span><span class="sxs-lookup"><span data-stu-id="8a359-153">ETW</span></span>

<span data-ttu-id="8a359-154">**/API/etw/Providers (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="8a359-155">Listet registrierte Anbieter auf.</span><span class="sxs-lookup"><span data-stu-id="8a359-155">Enumerates registered providers</span></span>

<span data-ttu-id="8a359-156">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="8a359-156">Return data</span></span>
* <span data-ttu-id="8a359-157">Liste der Anbieter, Anzeige Name und GUID</span><span class="sxs-lookup"><span data-stu-id="8a359-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="8a359-158">**/API/etw/Session/Realtime (Get/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="8a359-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="8a359-159">Erstellt eine ETW-Sitzung in Echtzeit. verwaltet über einen WebSocket.</span><span class="sxs-lookup"><span data-stu-id="8a359-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="8a359-160">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="8a359-160">Return data</span></span>
* <span data-ttu-id="8a359-161">ETW-Ereignisse von aktivierten Anbietern</span><span class="sxs-lookup"><span data-stu-id="8a359-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="8a359-162">Holographic – Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="8a359-162">Holographic OS</span></span>

<span data-ttu-id="8a359-163">**/API/Holographic/OS/etw/customproviders (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="8a359-164">Gibt eine Liste von hololens-spezifischen etw-Anbietern zurück, die nicht beim System registriert sind.</span><span class="sxs-lookup"><span data-stu-id="8a359-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="8a359-165">**/API/Holographic/OS/Services (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="8a359-166">Gibt die Zustände aller Dienste zurück, die ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="8a359-166">Returns the states of all services running.</span></span>

<span data-ttu-id="8a359-167">**/API/Holographic/OS/Settings/IPD (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="8a359-168">Ruft die gespeicherte IPD (interpupranäre Entfernung) in Millimeter ab.</span><span class="sxs-lookup"><span data-stu-id="8a359-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="8a359-169">**/API/Holographic/OS/Settings/IPD (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="8a359-170">Legt die IPD fest.</span><span class="sxs-lookup"><span data-stu-id="8a359-170">Sets the IPD</span></span>

<span data-ttu-id="8a359-171">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-171">Parameters</span></span>
* <span data-ttu-id="8a359-172">IPD: neuer IPD-Wert, der in Millimeter festgelegt werden soll</span><span class="sxs-lookup"><span data-stu-id="8a359-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="8a359-173">**/API/Holographic/OS/Webmanagement/Settings/HTTPS (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="8a359-174">Abrufen der HTTPS-Anforderungen für das Geräteportal</span><span class="sxs-lookup"><span data-stu-id="8a359-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="8a359-175">**/API/Holographic/OS/Webmanagement/Settings/HTTPS (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="8a359-176">Legt die HTTPS-Anforderungen für das Geräte Portal fest.</span><span class="sxs-lookup"><span data-stu-id="8a359-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="8a359-177">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-177">Parameters</span></span>
* <span data-ttu-id="8a359-178">erforderlich: Ja, Nein oder Standard</span><span class="sxs-lookup"><span data-stu-id="8a359-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="8a359-179">Holografische Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="8a359-179">Holographic Perception</span></span>

<span data-ttu-id="8a359-180">**/API/Holographic/perception/Client (Get/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="8a359-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="8a359-181">Akzeptiert WebSocket-Upgrades und führt einen perception-Client aus, der Updates bei 30 fps sendet.</span><span class="sxs-lookup"><span data-stu-id="8a359-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="8a359-182">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-182">Parameters</span></span>
* <span data-ttu-id="8a359-183">clientmode: "aktiv" erzwingt den visuellen Überwachungsmodus, wenn er nicht passiv festgelegt werden kann.</span><span class="sxs-lookup"><span data-stu-id="8a359-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="8a359-184">Holographic-Therme</span><span class="sxs-lookup"><span data-stu-id="8a359-184">Holographic Thermal</span></span>

<span data-ttu-id="8a359-185">**/API/Holographic/Thermal/Stage (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="8a359-186">Die wärmestufe des Geräts erhalten (0 normal, 1 warm, 2 kritisch)</span><span class="sxs-lookup"><span data-stu-id="8a359-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="8a359-187">Wahrnehmungs Simulations-Steuerelement</span><span class="sxs-lookup"><span data-stu-id="8a359-187">Perception Simulation Control</span></span>

<span data-ttu-id="8a359-188">**/API/Holographic/Simulation/Control/Mode (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="8a359-189">Simulationsmodus erhalten</span><span class="sxs-lookup"><span data-stu-id="8a359-189">Get the simulation mode</span></span>

<span data-ttu-id="8a359-190">**/API/Holographic/Simulation/Control/Mode (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="8a359-191">Festlegen des Simulationsmodus</span><span class="sxs-lookup"><span data-stu-id="8a359-191">Set the simulation mode</span></span>

<span data-ttu-id="8a359-192">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-192">Parameters</span></span>
* <span data-ttu-id="8a359-193">Mode: Simulationsmodus: Standard, Simulation, Remote, Legacy</span><span class="sxs-lookup"><span data-stu-id="8a359-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="8a359-194">**/API/Holographic/Simulation/Control/Stream (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="8a359-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="8a359-195">Löscht einen Steuerungsdaten Strom.</span><span class="sxs-lookup"><span data-stu-id="8a359-195">Delete a control stream.</span></span>

<span data-ttu-id="8a359-196">**/API/Holographic/Simulation/Control/Stream (Get/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="8a359-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="8a359-197">Öffnen Sie eine websocketverbindung für einen Steuerungsdaten Strom.</span><span class="sxs-lookup"><span data-stu-id="8a359-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="8a359-198">**/API/Holographic/Simulation/Control/Stream (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="8a359-199">Erstellen Sie einen Steuerungsdaten Strom (Priorität ist erforderlich), oder stellen Sie Daten in einem erstellten Stream bereit (streamid erforderlich).</span><span class="sxs-lookup"><span data-stu-id="8a359-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="8a359-200">Es wird erwartet, dass für die Daten der Typ "Application/Octett-Stream" festgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="8a359-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="8a359-201">**/API/Holographic/Simulation/Display/Stream (Get/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="8a359-201">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="8a359-202">Fordern Sie einen Simulations Videostream mit dem Inhalt an, der im Simulationsmodus für die System Anzeige gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="8a359-202">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="8a359-203">Anfänglich wird ein einfacher Format Deskriptor Header gesendet, gefolgt von H. 264-codierten Texturen, denen jeweils ein Header vorangestellt ist, der den Augen Index und die Textur Größe angibt.</span><span class="sxs-lookup"><span data-stu-id="8a359-203">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="8a359-204">Wiedergabe von Wahrnehmungs Simulationen</span><span class="sxs-lookup"><span data-stu-id="8a359-204">Perception Simulation Playback</span></span>

<span data-ttu-id="8a359-205">**/API/Holographic/Simulation/Playback/File (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="8a359-205">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="8a359-206">Löschen Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="8a359-206">Delete a recording.</span></span>

<span data-ttu-id="8a359-207">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-207">Parameters</span></span>
* <span data-ttu-id="8a359-208">Aufzeichnung: Name der zu löschenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="8a359-208">recording : Name of recording to delete.</span></span>

<span data-ttu-id="8a359-209">**/API/Holographic/Simulation/Playback/File (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-209">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="8a359-210">Hochladen einer Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="8a359-210">Upload a recording.</span></span>

<span data-ttu-id="8a359-211">**/API/Holographic/Simulation/Playback/Files (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-211">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="8a359-212">Alle Aufzeichnungen erhalten.</span><span class="sxs-lookup"><span data-stu-id="8a359-212">Get all recordings.</span></span>

<span data-ttu-id="8a359-213">**/API/Holographic/Simulation/Playback/Session (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-213">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="8a359-214">Gibt den aktuellen Wiedergabe Zustand einer Aufzeichnung an.</span><span class="sxs-lookup"><span data-stu-id="8a359-214">Get the current playback state of a recording.</span></span>

<span data-ttu-id="8a359-215">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-215">Parameters</span></span>
* <span data-ttu-id="8a359-216">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="8a359-216">recording : Name of recording.</span></span>

<span data-ttu-id="8a359-217">**/API/Holographic/Simulation/Playback/Session/File (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="8a359-217">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="8a359-218">Entladen Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="8a359-218">Unload a recording.</span></span>

<span data-ttu-id="8a359-219">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-219">Parameters</span></span>
* <span data-ttu-id="8a359-220">Aufzeichnung: Name der zu entladenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="8a359-220">recording : Name of recording to unload.</span></span>

<span data-ttu-id="8a359-221">**/API/Holographic/Simulation/Playback/Session/File (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-221">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="8a359-222">Laden Sie eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="8a359-222">Load a recording.</span></span>

<span data-ttu-id="8a359-223">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-223">Parameters</span></span>
* <span data-ttu-id="8a359-224">Aufzeichnung: Name der zu ladenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="8a359-224">recording : Name of recording to load.</span></span>

<span data-ttu-id="8a359-225">**/API/Holographic/Simulation/Playback/Session/Files (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-225">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="8a359-226">Alle geladenen Aufzeichnungen erhalten.</span><span class="sxs-lookup"><span data-stu-id="8a359-226">Get all loaded recordings.</span></span>

<span data-ttu-id="8a359-227">**/API/Holographic/Simulation/Playback/Session/Pause (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-227">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="8a359-228">Hält eine Aufzeichnung an.</span><span class="sxs-lookup"><span data-stu-id="8a359-228">Pause a recording.</span></span>

<span data-ttu-id="8a359-229">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-229">Parameters</span></span>
* <span data-ttu-id="8a359-230">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="8a359-230">recording : Name of recording.</span></span>

<span data-ttu-id="8a359-231">**/API/Holographic/Simulation/Playback/Session/Play (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-231">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="8a359-232">Wiedergabe einer Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="8a359-232">Play a recording.</span></span>

<span data-ttu-id="8a359-233">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-233">Parameters</span></span>
* <span data-ttu-id="8a359-234">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="8a359-234">recording : Name of recording.</span></span>

<span data-ttu-id="8a359-235">**/API/Holographic/Simulation/Playback/Session/Stop (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-235">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="8a359-236">Beendet eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="8a359-236">Stop a recording.</span></span>

<span data-ttu-id="8a359-237">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-237">Parameters</span></span>
* <span data-ttu-id="8a359-238">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="8a359-238">recording : Name of recording.</span></span>

<span data-ttu-id="8a359-239">**/API/Holographic/Simulation/Playback/Session/Types (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-239">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="8a359-240">Datentypen in einer geladenen Aufzeichnung erhalten.</span><span class="sxs-lookup"><span data-stu-id="8a359-240">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="8a359-241">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-241">Parameters</span></span>
* <span data-ttu-id="8a359-242">Aufzeichnung: Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="8a359-242">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="8a359-243">Erfassung von Wahrnehmungs Simulationen</span><span class="sxs-lookup"><span data-stu-id="8a359-243">Perception Simulation Recording</span></span>

<span data-ttu-id="8a359-244">**/API/Holographic/Simulation/Recording/Start (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-244">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="8a359-245">Startet eine Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="8a359-245">Start a recording.</span></span> <span data-ttu-id="8a359-246">Nur eine einzelne Aufzeichnung kann gleichzeitig aktiv sein.</span><span class="sxs-lookup"><span data-stu-id="8a359-246">Only a single recording can be active at once.</span></span> <span data-ttu-id="8a359-247">Eine der Köpfe, Hände, spatialmapping oder Umgebung muss festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="8a359-247">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="8a359-248">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-248">Parameters</span></span>
* <span data-ttu-id="8a359-249">Head: Legen Sie auf 1 fest, um Head-Daten aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="8a359-249">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="8a359-250">Hands: wird auf 1 festgelegt, um die Daten aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="8a359-250">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="8a359-251">spatialmapping: auf 1 festgelegt, um die räumliche Zuordnung aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="8a359-251">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="8a359-252">Umgebung: Legen Sie auf 1 fest, um Umgebungs Daten aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="8a359-252">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="8a359-253">Name: der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="8a359-253">name : Name of the recording.</span></span>
* <span data-ttu-id="8a359-254">singlespatialmappingframe: wird auf 1 festgelegt, um nur einen einzelnen räumlichen zuordnungsframe aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="8a359-254">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="8a359-255">**/API/Holographic/Simulation/Recording/Status (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-255">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="8a359-256">Aufzeichnungsstatus erhalten.</span><span class="sxs-lookup"><span data-stu-id="8a359-256">Get recording state.</span></span>

<span data-ttu-id="8a359-257">**/API/Holographic/Simulation/Recording/Stop (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-257">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="8a359-258">Hält die aktuelle Aufzeichnung an.</span><span class="sxs-lookup"><span data-stu-id="8a359-258">Stop the current recording.</span></span> <span data-ttu-id="8a359-259">Die Aufzeichnung wird als Datei zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8a359-259">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="8a359-260">Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="8a359-260">Mixed Reality Capture</span></span>

<span data-ttu-id="8a359-261">**/API/Holographic/MRC/File (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-261">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="8a359-262">Hiermit wird eine gemischte Reality-Datei vom Gerät heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="8a359-262">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="8a359-263">Verwenden Sie den OP = Stream-Abfrage Parameter für das Streaming.</span><span class="sxs-lookup"><span data-stu-id="8a359-263">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="8a359-264">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-264">Parameters</span></span>
* <span data-ttu-id="8a359-265">Dateiname: Name, hex64-codiert, der einzurufenden Videodatei</span><span class="sxs-lookup"><span data-stu-id="8a359-265">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="8a359-266">OP: Stream</span><span class="sxs-lookup"><span data-stu-id="8a359-266">op : stream</span></span>

<span data-ttu-id="8a359-267">**/API/Holographic/MRC/File (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="8a359-267">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="8a359-268">Löscht eine gemischte Reality-Aufzeichnung auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="8a359-268">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="8a359-269">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-269">Parameters</span></span>
* <span data-ttu-id="8a359-270">Dateiname: Name, hex64-codiert, der zu löschenden Datei</span><span class="sxs-lookup"><span data-stu-id="8a359-270">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="8a359-271">**/API/Holographic/MRC/Files (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-271">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="8a359-272">Gibt die Liste der Mixed Reality-Dateien zurück, die auf dem Gerät gespeichert sind</span><span class="sxs-lookup"><span data-stu-id="8a359-272">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="8a359-273">**/API/Holographic/MRC/Photo (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-273">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="8a359-274">Nimmt ein gemischtes Reality-Foto und erstellt eine Datei auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="8a359-274">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="8a359-275">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-275">Parameters</span></span>
* <span data-ttu-id="8a359-276">hololens: Erfassungs holograms: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="8a359-276">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="8a359-277">PV: Erfassen der PV-Kamera: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="8a359-277">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="8a359-278">Renderfromcamera: (hololens 2) renderingaus Perspektive der Foto-/Videokamera: true oder false (Standardwert: true)</span><span class="sxs-lookup"><span data-stu-id="8a359-278">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="8a359-279">**/API/Holographic/MRC/Settings (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-279">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="8a359-280">Ruft die Standardeinstellungen für die gemischte Realität-Erfassung ab.</span><span class="sxs-lookup"><span data-stu-id="8a359-280">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="8a359-281">**/API/Holographic/MRC/Settings (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-281">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="8a359-282">Legt die Standardeinstellungen für die gemischte Reality-Erfassung fest.</span><span class="sxs-lookup"><span data-stu-id="8a359-282">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="8a359-283">Einige dieser Einstellungen werden auf das MRC-Foto und die Video Erfassung des Systems angewendet.</span><span class="sxs-lookup"><span data-stu-id="8a359-283">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="8a359-284">**/API/Holographic/MRC/Status (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-284">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="8a359-285">Ruft den Zustand der Mixed Reality-Erfassung im Windows-Geräte Portal ab.</span><span class="sxs-lookup"><span data-stu-id="8a359-285">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="8a359-286">***Antwort***</span><span class="sxs-lookup"><span data-stu-id="8a359-286">***Response***</span></span>

<span data-ttu-id="8a359-287">Die Antwort enthält eine JSON-Eigenschaft, die angibt, ob das Windows-Geräte Portal Videos aufzeichnet.</span><span class="sxs-lookup"><span data-stu-id="8a359-287">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="8a359-288">**/API/Holographic/MRC/Thumbnail (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-288">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="8a359-289">Ruft das Miniaturbild für die angegebene Datei ab.</span><span class="sxs-lookup"><span data-stu-id="8a359-289">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="8a359-290">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-290">Parameters</span></span>
* <span data-ttu-id="8a359-291">Dateiname: Name, hex64-codiert, der Datei, für die die Miniaturansicht angefordert wird</span><span class="sxs-lookup"><span data-stu-id="8a359-291">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="8a359-292">**/API/Holographic/MRC/Video/Control/Start (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-292">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="8a359-293">Startet eine gemischte Reality-Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="8a359-293">Starts a mixed reality recording</span></span>

<span data-ttu-id="8a359-294">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-294">Parameters</span></span>
* <span data-ttu-id="8a359-295">hololens: Erfassungs holograms: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="8a359-295">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="8a359-296">PV: Erfassen der PV-Kamera: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="8a359-296">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="8a359-297">MIC: Mikrofon erfassen: true oder false (standardmäßig false)</span><span class="sxs-lookup"><span data-stu-id="8a359-297">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="8a359-298">Loopback: App-Audioerfassung: true oder false (standardmäßig false)</span><span class="sxs-lookup"><span data-stu-id="8a359-298">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="8a359-299">Renderfromcamera: (hololens 2) renderingaus Perspektive der Foto-/Videokamera: true oder false (Standardwert: true)</span><span class="sxs-lookup"><span data-stu-id="8a359-299">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="8a359-300">Vstab: (nur hololens 2) Videostabilisierung aktivieren: true oder false (Standardwert: true)</span><span class="sxs-lookup"><span data-stu-id="8a359-300">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="8a359-301">vstabbuffer: (hololens 2), Video Stabilisierungs Puffer Latenz: 0 bis 30 Frames (standardmäßig 15 Frames)</span><span class="sxs-lookup"><span data-stu-id="8a359-301">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="8a359-302">**/API/Holographic/MRC/Video/Control/Stop (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-302">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="8a359-303">Beendet die aktuelle gemischte Reality-Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="8a359-303">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="8a359-304">Streaming mit gemischter Realität</span><span class="sxs-lookup"><span data-stu-id="8a359-304">Mixed Reality Streaming</span></span>

<span data-ttu-id="8a359-305">Hololens unterstützt die Live Vorschau von Mixed Reality über einen segmentierten Download einer fragmentierten MP4-Datei.</span><span class="sxs-lookup"><span data-stu-id="8a359-305">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="8a359-306">Gemischte Reality-Streams verwenden denselben Satz von Parametern, um zu steuern, was aufgezeichnet wird:</span><span class="sxs-lookup"><span data-stu-id="8a359-306">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="8a359-307">hololens: Erfassungs holograms: true oder false</span><span class="sxs-lookup"><span data-stu-id="8a359-307">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="8a359-308">PV: Erfassen der PV-Kamera: true oder false</span><span class="sxs-lookup"><span data-stu-id="8a359-308">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="8a359-309">MIC: Mikrofon erfassen: true oder false</span><span class="sxs-lookup"><span data-stu-id="8a359-309">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="8a359-310">Loopback: App-Audioerfassung: true oder false</span><span class="sxs-lookup"><span data-stu-id="8a359-310">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="8a359-311">Wenn keines dieser Angaben angegeben ist: holograms, Foto-/Videokamera und App-Audiodaten werden aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="8a359-311">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="8a359-312">Wenn eine Angabe festgelegt ist: die nicht angegebenen Parameter werden standardmäßig auf false festgelegt.</span><span class="sxs-lookup"><span data-stu-id="8a359-312">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="8a359-313">Optionale Parameter (nur hololens 2)</span><span class="sxs-lookup"><span data-stu-id="8a359-313">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="8a359-314">Renderfromcamera: Rendering aus Perspektive der Foto-/Videokamera: true oder false (Standardwert ist true)</span><span class="sxs-lookup"><span data-stu-id="8a359-314">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="8a359-315">Vstab: Videostabilisierung aktivieren: true oder false (Standardwert: false)</span><span class="sxs-lookup"><span data-stu-id="8a359-315">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="8a359-316">vstabbuffer: Puffer Wartezeit für Videostabilisierung: zwischen 0 und 30 Frames (standardmäßig 15 Frames)</span><span class="sxs-lookup"><span data-stu-id="8a359-316">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="8a359-317">**/API/Holographic/Stream/Live.MP4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-317">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="8a359-318">Ein-Datenstrom von 1280x720p 30 fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="8a359-318">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="8a359-319">**/API/Holographic/Stream/live_high. MP4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-319">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="8a359-320">Ein-Datenstrom von 1280x720p 30 fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="8a359-320">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="8a359-321">**/API/Holographic/Stream/live_med. MP4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-321">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="8a359-322">Ein 854x480p 30 fps 2.5 MBit-Stream.</span><span class="sxs-lookup"><span data-stu-id="8a359-322">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="8a359-323">**/API/Holographic/Stream/live_low. MP4 (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-323">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="8a359-324">Ein 428x240 p 15fps 0.6-MBit-Stream.</span><span class="sxs-lookup"><span data-stu-id="8a359-324">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="8a359-325">Netzwerk</span><span class="sxs-lookup"><span data-stu-id="8a359-325">Networking</span></span>

<span data-ttu-id="8a359-326">**/API/Networking/ipconfig (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-326">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="8a359-327">Ruft die aktuelle IP-Konfiguration ab.</span><span class="sxs-lookup"><span data-stu-id="8a359-327">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="8a359-328">Betriebssysteminformationen</span><span class="sxs-lookup"><span data-stu-id="8a359-328">OS Information</span></span>

<span data-ttu-id="8a359-329">**/API/OS/Info (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-329">**/api/os/info (GET)**</span></span>

<span data-ttu-id="8a359-330">Ruft Betriebssysteminformationen ab.</span><span class="sxs-lookup"><span data-stu-id="8a359-330">Gets operating system information</span></span>

<span data-ttu-id="8a359-331">**/API/OS/MachineName (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-331">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="8a359-332">Ruft den Computernamen ab.</span><span class="sxs-lookup"><span data-stu-id="8a359-332">Gets the machine name</span></span>

<span data-ttu-id="8a359-333">**/API/OS/MachineName (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-333">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="8a359-334">Legt den Computernamen fest.</span><span class="sxs-lookup"><span data-stu-id="8a359-334">Sets the machine name</span></span>

<span data-ttu-id="8a359-335">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-335">Parameters</span></span>
* <span data-ttu-id="8a359-336">Name: neuer Computername, hex64-codiert, festgelegt auf</span><span class="sxs-lookup"><span data-stu-id="8a359-336">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="8a359-337">Leistungsdaten</span><span class="sxs-lookup"><span data-stu-id="8a359-337">Performance data</span></span>

<span data-ttu-id="8a359-338">**/API/ResourceManager/Processes (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-338">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="8a359-339">Gibt die Liste der laufenden Prozesse mit Details zurück.</span><span class="sxs-lookup"><span data-stu-id="8a359-339">Returns the list of running processes with details</span></span>

<span data-ttu-id="8a359-340">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="8a359-340">Return data</span></span>
* <span data-ttu-id="8a359-341">JSON mit einer Liste der Prozesse und Details für jeden Prozess</span><span class="sxs-lookup"><span data-stu-id="8a359-341">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="8a359-342">**/API/ResourceManager/systemperf (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-342">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="8a359-343">Gibt die System Leistungsstatistik (e/a-Lese-/Schreibvorgänge, Speicher Statistiken usw.) zurück.</span><span class="sxs-lookup"><span data-stu-id="8a359-343">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="8a359-344">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="8a359-344">Return data</span></span>
* <span data-ttu-id="8a359-345">JSON mit Systeminformationen: CPU, GPU, Arbeitsspeicher, Netzwerk, e/a</span><span class="sxs-lookup"><span data-stu-id="8a359-345">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="8a359-346">Leistung</span><span class="sxs-lookup"><span data-stu-id="8a359-346">Power</span></span>

<span data-ttu-id="8a359-347">**/API/Power/Battery (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-347">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="8a359-348">Ruft den aktuellen Akku Zustand ab.</span><span class="sxs-lookup"><span data-stu-id="8a359-348">Gets the current battery state</span></span>

<span data-ttu-id="8a359-349">**/API/Power/State (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-349">**/api/power/state (GET)**</span></span>

<span data-ttu-id="8a359-350">Prüft, ob sich das System in einem niedrigen Energiezustand befindet</span><span class="sxs-lookup"><span data-stu-id="8a359-350">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="8a359-351">Remotesteuerung</span><span class="sxs-lookup"><span data-stu-id="8a359-351">Remote Control</span></span>

<span data-ttu-id="8a359-352">**/API/Control/Restart (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-352">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="8a359-353">Startet das Zielgerät neu.</span><span class="sxs-lookup"><span data-stu-id="8a359-353">Restarts the target device</span></span>

<span data-ttu-id="8a359-354">**/API/Control/Shutdown (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-354">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="8a359-355">Fährt das Zielgerät herunter.</span><span class="sxs-lookup"><span data-stu-id="8a359-355">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="8a359-356">Task-Manager</span><span class="sxs-lookup"><span data-stu-id="8a359-356">Task Manager</span></span>

<span data-ttu-id="8a359-357">**/API/Taskmanager/app (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="8a359-357">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="8a359-358">Beendet eine moderne App</span><span class="sxs-lookup"><span data-stu-id="8a359-358">Stops a modern app</span></span>

<span data-ttu-id="8a359-359">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-359">Parameters</span></span>
* <span data-ttu-id="8a359-360">Package: vollständiger Name des App-Pakets, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="8a359-360">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="8a359-361">forcestop: erzwingen, dass alle Prozesse beendet werden (= yes)</span><span class="sxs-lookup"><span data-stu-id="8a359-361">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="8a359-362">**/API/Taskmanager/app (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-362">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="8a359-363">Startet eine moderne App</span><span class="sxs-lookup"><span data-stu-id="8a359-363">Starts a modern app</span></span>

<span data-ttu-id="8a359-364">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-364">Parameters</span></span>
* <span data-ttu-id="8a359-365">AppID: Praid der zu startenden APP, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="8a359-365">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="8a359-366">Package: vollständiger Name des App-Pakets, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="8a359-366">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="8a359-367">WiFi-Verwaltung</span><span class="sxs-lookup"><span data-stu-id="8a359-367">WiFi Management</span></span>

<span data-ttu-id="8a359-368">**/API/WiFi/Interfaces (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-368">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="8a359-369">Listet drahtlose Netzwerkschnittstellen auf.</span><span class="sxs-lookup"><span data-stu-id="8a359-369">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="8a359-370">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="8a359-370">Return data</span></span>
* <span data-ttu-id="8a359-371">Liste der drahtlos Schnittstellen mit Details (GUID, Beschreibung usw.)</span><span class="sxs-lookup"><span data-stu-id="8a359-371">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="8a359-372">**/API/WiFi/Network (Löschen)**</span><span class="sxs-lookup"><span data-stu-id="8a359-372">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="8a359-373">Löscht ein Profil, das einem Netzwerk in einer angegebenen Schnittstelle zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="8a359-373">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="8a359-374">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-374">Parameters</span></span>
* <span data-ttu-id="8a359-375">Schnittstelle: GUID der Netzwerkschnittstelle</span><span class="sxs-lookup"><span data-stu-id="8a359-375">interface : network interface guid</span></span>
* <span data-ttu-id="8a359-376">Profil: Profilname</span><span class="sxs-lookup"><span data-stu-id="8a359-376">profile : profile name</span></span>

<span data-ttu-id="8a359-377">**/API/WiFi/Networks (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-377">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="8a359-378">Listet drahtlose Netzwerke auf der angegebenen Netzwerkschnittstelle auf.</span><span class="sxs-lookup"><span data-stu-id="8a359-378">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="8a359-379">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-379">Parameters</span></span>
* <span data-ttu-id="8a359-380">Schnittstelle: GUID der Netzwerkschnittstelle</span><span class="sxs-lookup"><span data-stu-id="8a359-380">interface : network interface guid</span></span>

<span data-ttu-id="8a359-381">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="8a359-381">Return data</span></span>
* <span data-ttu-id="8a359-382">Liste der Drahtlos Netzwerke, die sich auf der Netzwerkschnittstelle befinden, mit Details</span><span class="sxs-lookup"><span data-stu-id="8a359-382">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="8a359-383">**/API/WiFi/Network (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-383">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="8a359-384">Stellt eine Verbindung mit einem Netzwerk auf der angegebenen Schnittstelle her oder trennt es.</span><span class="sxs-lookup"><span data-stu-id="8a359-384">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="8a359-385">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-385">Parameters</span></span>
* <span data-ttu-id="8a359-386">Schnittstelle: GUID der Netzwerkschnittstelle</span><span class="sxs-lookup"><span data-stu-id="8a359-386">interface : network interface guid</span></span>
* <span data-ttu-id="8a359-387">SSID: SSID, hex64-codiert, um eine Verbindung herzustellen</span><span class="sxs-lookup"><span data-stu-id="8a359-387">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="8a359-388">OP: verbinden oder trennen</span><span class="sxs-lookup"><span data-stu-id="8a359-388">op : connect or disconnect</span></span>
* <span data-ttu-id="8a359-389">kreateprofile: Ja oder Nein</span><span class="sxs-lookup"><span data-stu-id="8a359-389">createprofile : yes or no</span></span>
* <span data-ttu-id="8a359-390">Schlüssel: gemeinsam verwendeter Schlüssel, hex64-codiert</span><span class="sxs-lookup"><span data-stu-id="8a359-390">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="8a359-391">Windows Performance Recorder</span><span class="sxs-lookup"><span data-stu-id="8a359-391">Windows Performance Recorder</span></span>

<span data-ttu-id="8a359-392">**/API/WPR/customtrace (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-392">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="8a359-393">Lädt ein WPR-Profil hoch und startet die Ablauf Verfolgung mithilfe des hochgeladenen Profils.</span><span class="sxs-lookup"><span data-stu-id="8a359-393">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="8a359-394">Nutzlast</span><span class="sxs-lookup"><span data-stu-id="8a359-394">Payload</span></span>
* <span data-ttu-id="8a359-395">Mehrteilige konforme HTTP-Text</span><span class="sxs-lookup"><span data-stu-id="8a359-395">multi-part conforming http body</span></span>

<span data-ttu-id="8a359-396">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="8a359-396">Return data</span></span>
* <span data-ttu-id="8a359-397">Gibt den WPR-Sitzungsstatus zurück.</span><span class="sxs-lookup"><span data-stu-id="8a359-397">Returns the WPR session status.</span></span>

<span data-ttu-id="8a359-398">**/API/WPR/Status (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-398">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="8a359-399">Ruft den Status der WPR-Sitzung ab.</span><span class="sxs-lookup"><span data-stu-id="8a359-399">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="8a359-400">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="8a359-400">Return data</span></span>
* <span data-ttu-id="8a359-401">WPR-Sitzungs Status.</span><span class="sxs-lookup"><span data-stu-id="8a359-401">WPR session status.</span></span>

<span data-ttu-id="8a359-402">**/API/WPR/Trace (Get)**</span><span class="sxs-lookup"><span data-stu-id="8a359-402">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="8a359-403">Beendet eine WPR-Ablauf Verfolgungs Sitzung (Leistung).</span><span class="sxs-lookup"><span data-stu-id="8a359-403">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="8a359-404">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="8a359-404">Return data</span></span>
* <span data-ttu-id="8a359-405">Gibt die ETL-Ablauf Verfolgungs Datei zurück.</span><span class="sxs-lookup"><span data-stu-id="8a359-405">Returns the trace ETL file</span></span>

<span data-ttu-id="8a359-406">**/API/WPR/Trace (Post)**</span><span class="sxs-lookup"><span data-stu-id="8a359-406">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="8a359-407">Startet eine Ablauf Verfolgungs Sitzung für WPR (Leistung).</span><span class="sxs-lookup"><span data-stu-id="8a359-407">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="8a359-408">Parameter</span><span class="sxs-lookup"><span data-stu-id="8a359-408">Parameters</span></span>
* <span data-ttu-id="8a359-409">Profil: Profilname.</span><span class="sxs-lookup"><span data-stu-id="8a359-409">profile : Profile name.</span></span> <span data-ttu-id="8a359-410">Verfügbare Profile werden in "perfprofiles/Profiles. JSON" gespeichert.</span><span class="sxs-lookup"><span data-stu-id="8a359-410">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="8a359-411">Daten zurückgeben</span><span class="sxs-lookup"><span data-stu-id="8a359-411">Return data</span></span>
* <span data-ttu-id="8a359-412">Beim Start wird der WPR-Sitzungs Status zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8a359-412">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a359-413">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8a359-413">See also</span></span>
* [<span data-ttu-id="8a359-414">Verwenden des Windows-Geräteportals</span><span class="sxs-lookup"><span data-stu-id="8a359-414">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="8a359-415">API-Referenz für den Geräte Portal (UWP)</span><span class="sxs-lookup"><span data-stu-id="8a359-415">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
