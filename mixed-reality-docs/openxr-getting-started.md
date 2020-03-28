---
title: Einstieg in openxr
description: Beginnen Sie mit der Verwendung des portablen openxr-API-Standards für Windows Mixed Reality und hololens 2-Headsets.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: Openxr, Khronos, basicxrapp, Windows Mixed Reality openxr-Entwickler Portal, DirectX, Native, Native APP, benutzerdefiniertes Modul, Middleware, Getting Started, 101, Vorschau Erweiterungen
ms.openlocfilehash: db45308834f920413420f080a35b378f6a55fa49
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362031"
---
# <a name="getting-started-with-openxr"></a>Einstieg in openxr

Sie können auf dem Desktop mit openxr auf einem hololens 2-oder Windows Mixed Reality-immersiven Headset entwickeln.  Wenn Sie keinen Zugriff auf ein Headset haben, können Sie stattdessen den hololens 2-Emulator oder den Windows Mixed Reality-Simulator verwenden.

## <a name="getting-started-with-openxr-for-hololens-2"></a>Getting Started with openxr for hololens 2

So beginnen Sie mit der Entwicklung von openxr-Anwendungen für hololens 2:

1. Richten Sie einen hololens 2 ein, oder befolgen Sie die Anweisungen, um [eine aktuelle Version des hololens 2-Emulators zu installieren](using-the-hololens-emulator.md).  Wenn Ihr Gerät vor kurzem aktualisiert wurde oder wenn Sie ein Aktuelles emulatorimage verwenden, sollte openxr 1,0 bereits einsatzbereit sein.
1. Um sicherzustellen, dass Sie über die neueste openxr-Laufzeit mit allen vorhandenen [Erweiterungen](openxr.md#roadmap) verfügen, starten Sie die Store-App innerhalb des Geräts oder Emulators, öffnen Sie das Menü in der oberen rechten Ecke, klicken Sie auf **Downloads und Updates** , und klicken Sie auf **Updates erhalten**.  Dadurch wird sichergestellt, dass die openxr-Laufzeit auf den hololens auf dem neuesten Stand ist.  Beachten Sie Folgendes: Wenn Sie den Emulator verwenden, wird das Emulatorbild jedes Mal zurückgesetzt, wenn Sie es starten. Daher sollten Sie sicherstellen, dass Sie über [die neueste Version des hololens 2-Emulatorbilds](using-the-hololens-emulator.md)verfügen.

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Einstieg in openxr für Windows Mixed Reality-Headsets

So beginnen Sie mit der Entwicklung von openxr-Anwendungen für immersive Windows Mixed Reality-Headsets:

1. Stellen Sie sicher, dass mindestens das Windows 10-Update von Mai 2019 (1903) ausgeführt wird. Dies ist die Mindestanforderung für Endbenutzer von Windows Mixed Reality, openxr-Anwendungen auszuführen.  Wenn Sie eine frühere Version von Windows 10 verwenden, können Sie ein Upgrade mit dem <a href="https://www.microsoft.com/software-download/windows10" target="_blank">Windows 10 Update Assistant</a>durchführen.
2. Richten Sie ein Windows Mixed Reality-Headset ein, oder befolgen Sie die Anweisungen zum [Aktivieren des Windows Mixed Reality-Simulators](using-the-windows-mixed-reality-simulator.md).  Wenn Sie Windows Mixed Reality einrichten, wird die Windows Mixed Reality openxr-Laufzeit automatisch von Mixed Reality Portal installiert.  Der Microsoft Store behält die Laufzeit dann bei.
3. Aktivieren Sie die Windows Mixed Reality openxr-Laufzeit, indem Sie das gemischte Reality-Portal im Startmenü starten und dann auf die Schaltfläche... unten links, und wählen Sie "openxr einrichten".<br>
![Einrichten von openxr im Mixed Reality-Portal](images/mixed-reality-portal-set-up-openxr.png)

Wenn Sie die Windows Mixed Reality-openxr-Laufzeit erneut aktivieren müssen, wiederholen Sie Schritt 3.

> [!NOTE]
> Die Windows Mixed Reality openxr-Laufzeit wird in Kürze automatisch für alle Windows Mixed Reality-Endbenutzer aktiviert.

## <a name="getting-the-windows-mixed-reality-openxr-developer-portal"></a>Kennenlernen des Windows Mixed Reality openxr-Entwickler Portals

Um die Windows Mixed Reality openxr-Laufzeit auszuprobieren, können Sie die <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">gemischte Realität openxr Developer Portal-App</a>installieren.  Diese APP bietet eine Demo Szene, die verschiedene Features von openxr sowie eine Seite mit dem System Status ausführt, die wichtige Informationen zur aktiven Laufzeit und zum aktuellen Headset bereitstellt.

Wenn Sie den Emulator verwenden, ist die einfachste Möglichkeit zum Installieren des Entwickler Portals für die gemischte Realität die Verwendung des [Windows-Geräte Portals](using-the-windows-device-portal.md), indem Sie zur Seite "openxr" navigieren und dann unter "Entwickler Features" auf die Schaltfläche "installieren" klicken. (dies funktioniert auch auf einem physischen hololens 2-Gerät.)

![Gemischte Realität openxr-Entwickler Portal-App](images/mixed-reality-openxr-developer-portal.png)

## <a name="building-a-sample-openxr-app"></a>Aufbauen einer openxr-Beispiel-App

Stellen Sie sicher, dass Sie [die Tools installieren, die](install-the-tools.md) Sie für die openxr-Entwicklung benötigen, sofern noch nicht geschehen.

Das <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">basicxrapp</a> -Projekt veranschaulicht ein einfaches openxr-Beispiel mit zwei Visual Studio-Projektdateien, eines für eine Win32-Desktop-App und eines für eine UWP hololens 2-App.  Da die Projekt Mappe ein hololens-UWP-Projekt enthält, benötigen Sie die [Arbeitsauslastung der universelle Windows-Plattform Entwicklung](install-the-tools.md#installation-checklist) , die in Visual Studio installiert ist, um Sie vollständig zu öffnen.

Beachten Sie Folgendes: während die Win32-und UWP-Projektdateien aufgrund von Unterschieden bei der Paket Erstellung und Bereitstellung getrennt sind, ist der app-Code in jedem Projekt 100% identisch.

Nach dem Aufbau eines openxr Win32-Desktops. EXE, Sie können es mit einem VR-Headset auf jeder Desktop-VR-Plattform verwenden, die openxr unterstützt, unabhängig davon, ob es sich um ein Windows Mixed Reality-Headset oder ein anderes Headset handelt.

Nachdem Sie ein openxr UWP-App-Paket aufgebaut haben, können Sie [Dieses Paket](using-visual-studio.md) entweder auf einem hololens 2-Gerät oder auf dem hololens 2-Emulator bereitstellen.

## <a name="integrate-the-openxr-loader-into-a-project"></a>Integrieren des openxr-Lade Moduls in ein Projekt

Für den Einstieg in openxr in einem vorhandenen Projekt fügen Sie das openxr-Lade Modul ein.  Das Lade Modul ermittelt die aktive openxr-Laufzeit auf dem Gerät und ermöglicht den Zugriff auf die Kernfunktionen und Erweiterungsfunktionen, die es implementiert.

Sie können entweder auf [das offizielle openxr nuget-Paket](#reference-official-openxr-nuget-package) aus Ihrem Visual Studio-Projekt verweisen oder [die offizielle openxr-Lade Programmquelle](#include-official-openxr-loader-source) aus dem GitHub-Repository Khronos einschließen.  Beide Ansätze erhalten Zugriff auf openxr 1,0 Core-Features sowie auf veröffentlichte `KHR`, `EXT` und `MSFT` Erweiterungen.

Wenn Sie auch mit `MSFT_preview`-Erweiterungen experimentieren möchten, können Sie die [Vorschau von openxr-Headern](#using-preview-extensions) aus dem GitHub-Repository mit gemischter Realität kopieren.

### <a name="reference-official-openxr-nuget-package"></a>Verweis auf das offizielle openxr-nuget-Paket

Das <a href="https://www.nuget.org/packages/OpenXR.Loader/" target="_blank"> **openxr. Loader** -nuget-Paket</a> ist die einfachste Möglichkeit, auf ein vorab erstelltes openxr-Lade Modul zu verweisen. DLL in Ihrer Visual Studio C++ -Projekt Mappe.  Dadurch erhalten Sie Zugriff auf openxr 1,0 Core-Features sowie auf veröffentlichte `KHR`, `EXT` und `MSFT` Erweiterungen.

So fügen Sie der Visual Studio C++ -Projekt Mappe einen "openxr. Loader"-nuget-Paket Verweis hinzu:
1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, das openxr verwendet, und wählen Sie **nuget-Pakete verwalten...** aus.
1. Wechseln Sie zur Registerkarte **Durchsuchen** , und suchen Sie nach **openxr. Loader**.
1. Wählen Sie das Paket **openxr. Loader** aus, und klicken Sie im Detailbereich auf der rechten Seite auf installieren.
1. Klicken Sie auf OK, um die Änderungen am Projekt zu übernehmen.
1. Fügen Sie `#include <openxr/openxr.h>` einer Quelldatei hinzu, um mit der Verwendung der openxr-API zu beginnen.

Ein Beispiel für die openxr-API in Aktion finden Sie in der <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">basicxrapp</a> -Beispiel-app.

### <a name="include-official-openxr-loader-source"></a>Offizielle openxr-Ladedienst Quelle einbeziehen

Wenn Sie das Lade Modul selbst erstellen möchten, z. b. um das zusätzliche Lade Modul zu vermeiden. DLL, Sie können die offiziellen Khronos openxr-Lade Quell Quellen in Ihr Projekt abrufen.  Dadurch erhalten Sie Zugriff auf openxr 1,0 Core-Features sowie auf veröffentlichte `KHR`, `EXT` und `MSFT` Erweiterungen.

Befolgen Sie zum Einstieg die Anweisungen im Repository " <a href="https://github.com/KhronosGroup/OpenXR-SDK" target="_blank">Khronos openxr-SDK" auf GitHub</a>.  Das Projekt ist so eingerichtet, dass es mit CMake erstellt wird. Wenn Sie MSBuild verwenden, müssen Sie den Code in Ihr eigenes Projekt kopieren.

## <a name="using-preview-extensions"></a>Verwenden von Vorschau Erweiterungen

Die in der [Erweiterungs Roadmap](openxr.md#roadmap) aufgeführten `MSFT_preview` Erweiterungen sind experimentelle Lieferanten Erweiterungen, die in der Vorschau angezeigt werden, um Feedback zu sammeln.  Diese Erweiterungen gelten nur für Entwickler Geräte und werden entfernt, wenn die echte Erweiterung ausgeliefert wird.

Wenn Sie die verfügbaren `MSFT_preview`-Erweiterungen testen möchten, führen Sie die folgenden Schritte aus, um Ihr Projekt zu aktualisieren:
1. Befolgen Sie einen der oben genannten Vorgehensweisen, um ein openxr-Lade Modul in Ihr Projekt zu integrieren.
1. Ersetzen Sie die openxr-Standard Header in Ihrem Projekt durch die <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/openxr_preview/include/openxr" target="_blank">Vorschau Header aus dem Mixed Reality openxr-Repository auf GitHub</a>.

So aktivieren Sie die Vorschau Erweiterungen auf ihren Ziel-hololens 2 oder auf dem Desktop-PC:
  1. Aktivieren Sie das Windows-Geräte Portal auf dem Zielgerät:
     * Wenn das Zielgerät ein hololens 2-Gerät ist, [befolgen Sie diese Anweisungen](using-the-windows-device-portal.md) auf dem Zielgerät.  Beachten Sie, dass dies ein physisches Headset erfordert, da ein bekanntes Problem im hololens 2-Emulator verhindert, dass die Benutzeroberfläche im nächsten Schritt im Emulator angezeigt wird.
     * Wenn Ihr Zielgerät ein Desktop-PC ist, dem eine immersive Headset-Peripherie angefügt ist, <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-desktop#set-up-device-portal-on-windows-desktop" target="_blank">befolgen Sie diese Anweisungen</a> auf dem Desktop-Zielcomputer.
  1. Navigieren Sie im linken Bereich zur Registerkarte **openxr** , und aktivieren Sie die Option **neueste Vorschauversion openxr-Laufzeit verwenden**.  Dadurch wird die Vorschau Laufzeit auf Ihrem Gerät aktiviert, für die Vorschau Erweiterungen aktiviert sind.

Eine Dokumentation zu diesen Vorschau Erweiterungen und Beispielen zur Verwendung finden Sie im Repository " <a href="https://github.com/microsoft/OpenXR-MixedReality#openxr-preview-extensions" target="_blank">Mixed Reality openxr</a> ".

## <a name="troubleshooting"></a>Problembehandlung

Wenn Sie Probleme mit der openxr-Entwicklung haben, sehen Sie sich unsere [Tipps zur Problem](openxr-troubleshooting.md)Behandlung an.