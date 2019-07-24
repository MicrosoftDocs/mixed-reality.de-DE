---
title: Openxr
description: Testen Sie die vorläufige openxr 0,90-API mit der Mixed Reality openxr Developer Preview.
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: Gemischte Realität openxr Developer Preview
ms.openlocfilehash: 723b0b85785d4b6dd735430aa76a24b9ce05b5c7
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039181"
---
# <a name="openxr"></a>Openxr

Openxr ist ein offener, kostenloser Standard von [Khronos](https://www.khronos.org/) , der systemeigenen Zugriff auf eine Vielzahl von Geräten von vielen Anbietern ermöglicht, die sich über das [gemischte Reality-Spektrum](mixed-reality.md)erstrecken.

Mit openxr können Sie Anwendungen erstellen, die sowohl auf Holographic-Geräte (z. b. hololens 2) abzielen, die digitale Inhalte in der realen Welt platzieren, als wären Sie tatsächlich vorhanden, als auch auf immersive Geräte (wie Windows Mixed Reality-Headsets für Desktop-PCs), die das physische Welt und durch eine digitale Umgebung ersetzen.  Mit openxr können Sie Code einmal schreiben, der dann über eine große Bandbreite von Hardwareplattformen portabel ist.

Openxr Standard ist zurzeit in einer provisorischen Phase, in der eine anfängliche openxr 0,90-Spezifikation für Feedback veröffentlicht wird.  Weitere Informationen zu openxr, einschließlich des Zugriffs auf die [provisorischen 0,90-Spezifikationen](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html) und- [Header](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr), finden Sie auf der [Seite zu Khronos openxr](https://www.khronos.org/openxr/). 

Sie können die vorläufige openxr 0,90-API auf einem hololens 2 oder einem Desktop-PC testen, indem Sie die Mixed Reality openxr Developer Preview verwenden.  Diese frühe Laufzeit ermöglicht Anwendungen, die auf die openxr 0,90-API abzielen, das Ziel von hololens 2-oder Windows Mixed Reality-auf dem Desktop.

Wenn Sie keinen Zugriff auf ein Headset haben, können Sie stattdessen den hololens 2-Emulator oder den Windows Mixed Reality-Simulator verwenden.

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-hololens-2"></a>Einrichten der gemischten Realität openxr Developer Preview für hololens 2

Für den Einstieg in die gemischte Realität openxr Developer Preview auf hololens 2:

1. Richten Sie einen hololens 2 ein, oder befolgen Sie die Anweisungen zum [Installieren des hololens 2-Emulators](using-the-hololens-emulator.md).
1. Starten Sie die Store-App innerhalb des Geräts oder Emulators, und stellen Sie sicher, dass alle apps aktualisiert werden.  Dadurch wird die gemischte Realität openxr Developer Preview für die Verwendung mit apps auf diesem Gerät installiert.  Wenn Sie den Emulator verwenden, sollten Sie sich die [Emulator-Eingabe Anweisungen](using-the-hololens-emulator.md#basic-emulator-input) ansehen, damit Sie die Store-App im Emulator verwenden können.

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-immersive-desktop-headsets"></a>Einrichten der gemischten Realität openxr Developer Preview für immersive Desktop-Headsets

Für den Einstieg in die gemischte Realität openxr Developer Preview auf einem Desktop-PC:

1. Stellen Sie sicher, dass Sie das Windows 10-Update vom Oktober 2018 (1809) oder das Windows 10-Update vom Mai 2019 (1903) ausführen.  Wenn Sie eine frühere Version von Windows 10 verwenden, können Sie mit dem [Windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10)ein Upgrade auf das Update von Mai 2019 durchführen.
1. Richten Sie ein Windows Mixed Reality-Headset ein, oder befolgen Sie die Anweisungen zum [Aktivieren des Windows Mixed Reality-Simulators](using-the-windows-mixed-reality-simulator.md).
1. Installieren Sie die [Mixed Reality openxr Developer Preview-App](https://www.microsoft.com/store/productId/9n5cvvl23qbt).  Diese APP wird Ihnen für die Vorschauversion von openxr Runtime unter Windows 10 Oktober 2018 Update (1809) oder höher eingerichtet.  Nachdem Sie diese APP installiert haben, wird die Laufzeit vom Windows Store auf dem neuesten Stand gehalten.
1. Führen Sie die Mixed Reality openxr Developer Preview-App über das Startmenü aus, und befolgen Sie die Anweisungen, um die Laufzeit zu aktivieren.  In Kürze können Sie mit dieser APP auch andere openxr-Debuginformationen untersuchen.

![Gemischte Realität openxr Developer Preview-App](images/mixed-reality-openxr-developer-preview.png)

### <a name="support-for-windows-10-october-2018-update"></a>Unterstützung für Windows 10-Update vom Oktober 2018

Wenn Sie das Windows 10-Update von Mai 2019 (1903) ausführen und die obigen Schritte ausgeführt haben, sollten Sie die gemischte Realität openxr Developer Preview verwenden!

Wenn Sie nicht bereit sind, den [Desktop-PC auf das Update von Mai 2019 zu aktualisieren](https://www.microsoft.com/en-us/software-download/windows10), können Sie mit dem Windows 10-Update vom Oktober 2018 (1809) fortfahren, indem Sie einen weiteren Schritt ausführen:

1. Führen Sie die obigen Schritte aus, um die Entwicklervorschau für die gemischte Realität openxr zu installieren.
1. Um die gemischte Realität openxr Developer Preview als aktive openxr-Laufzeit Ihres Systems festzulegen, installieren Sie das [Mixed Reality openxr Developer Preview Compatibility Pack](https://aka.ms/openxr-compat).

## <a name="building-a-sample-openxr-app"></a>Aufbauen einer openxr-Beispiel-App

Das [basicxrapp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp) -Projekt veranschaulicht ein einfaches openxr-Beispiel mit zwei Visual Studio-Projektdateien, eines für eine Win32-Desktop-App und eines für eine UWP hololens 2-App.  Da die Projekt Mappe ein hololens-UWP-Projekt enthält, benötigen Sie die [Arbeitsauslastung der universelle Windows-Plattform Entwicklung](install-the-tools.md#installation-checklist) , die in Visual Studio installiert ist, um Sie vollständig zu öffnen.

Beachten Sie Folgendes: während die Win32-und UWP-Projektdateien aufgrund von Unterschieden bei der Paket Erstellung und Bereitstellung getrennt sind, ist der app-Code in jedem Projekt 100% identisch.

## <a name="feedback"></a>Feedback

Wenn Sie Feedback zur [openxr](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)-Version 0,90 erhalten möchten, besuchen Sie [die Khronos openxr-Foren](https://community.khronos.org/c/openxr), [Slack #openxr Channel](https://khr.io/slack) und die [spec Issue Tracker](https://github.com/KhronosGroup/OpenXR-Docs/issues).

## <a name="troubleshooting"></a>Problembehandlung

Hier finden Sie einige Tipps zur Problembehandlung für die gemischte Realität openxr Developer Preview.  Wenn Sie auf andere Probleme stoßen, besuchen Sie die [Khronos openxr-Foren](https://community.khronos.org/c/openxr) oder [Slack #openxr Channel](https://khr.io/slack).

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>Openxr-App startet nicht Windows Mixed Reality

Wenn Ihre openxr-APP nicht Windows Mixed Reality startet, wenn Sie Sie ausführen, kann die gemischte Realität openxr Developer Preview nicht als aktive Laufzeit festgelegt werden.  Stellen Sie sicher, dass Sie die Mixed Reality openxr Developer Preview-app ausführen, und befolgen Sie die Anweisungen, um die Laufzeit zu aktivieren.

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a>Die gemischte Realität openxr Developer Preview-App kann nicht installiert werden. 

Stellen Sie sicher, dass mindestens das Windows 10-Update vom Oktober 2018 (1809) ausgeführt wird.  Wenn Sie eine frühere Version von Windows 10 verwenden, können Sie mit dem [Windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10)auf das Update von Mai 2019 (1903) aktualisieren.

Wenn die Schaltfläche Installieren in der gemischten Realität openxr Developer Preview-App keine Windows 10-Updates vom Oktober 2018 ausführt, hat Ihr System möglicherweise veraltete Systemanforderungen für die APP zwischengespeichert.  Sie können den Befehl `wsreset.exe` über eine Eingabeaufforderung ausführen, um den Cache zu löschen.

## <a name="see-also"></a>Siehe auch

* [Weitere Informationen zu openxr](https://www.khronos.org/openxr/)
* [Openxr-vorläufige 0,90-Spezifikation](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [Referenz zur openxr-provisorischen 0,90-API](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [Openxr-vorläufige 0,90-Header](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
* [Leitfaden für openxr provisorisch 0,90 Kurzübersicht](https://www.khronos.org/registry/OpenXR/specs/0.90/refguide/OpenXR-0.90-web.pdf)
