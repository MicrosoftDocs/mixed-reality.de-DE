---
title: OpenXR
description: Testen Sie die vorläufigen OpenXR 0,90-API mit der Mixed Reality OpenXR Developer Preview.
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: Mixed Reality OpenXR Entwicklervorschau
ms.openlocfilehash: c5ac87145ca23e4a6fbe578a285e27d50f1f22a1
ms.sourcegitcommit: 36192101052666da01dd6c59cad4cfabd4ecb6f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65048499"
---
# <a name="openxr"></a>OpenXR

OpenXR ist eine open Standard-lizenzgebührenfreie aus [Khronos](https://www.khronos.org/) , einheitlichen Zugriff auf eine große Bandbreite von Geräten bereitstellt, von vielen Anbietern, die umfassen die [mixed Reality Spektrum](mixed-reality.md).

Mit OpenXR, können Sie erstellen, Anwendungen, die sowohl holographic-Geräten (z. B. 2 für HoloLens), die digitalen Inhalte in der Praxis zu platzieren, als gäbe es wirklich, als auch immersive Geräte (z. B. Windows Mixed Reality-Headsets für desktop-PCs), das Ausblenden der physische Welt und durch eine digitale Inhalte zu ersetzen.  OpenXR können Sie Code schreiben, nachdem die, die für eine Vielzahl unterschiedlicher Hardwareplattformen dann portabel ist.

Der OpenXR Standard ist zurzeit in einer vorläufigen Phase mit einer anfänglichen OpenXR 0,90-Spezifikation für Feedback veröffentlicht.  Weitere Informationen zu OpenXR, einschließlich des Zugriffs auf die [vorläufigen 0,90 Spezifikation](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html) und [Header](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr), finden Sie unter den [Khronos OpenXR Seite](https://www.khronos.org/openxr/). 

Sie können die vorläufigen OpenXR 0,90-API auf eine HoloLens-2 oder eine desktop-PC mit der Mixed Reality OpenXR Developer Preview testen.  Diese frühe Laufzeit kann Anwendungen, die für die OpenXR 0,90-API, die HoloLens-2 oder Windows Mixed Reality immersive Headsets auf dem Desktop als Ziel.

Wenn Sie keinen Zugriff auf einen Kopfhörer haben, können Sie die HoloLens-2-Emulator oder auf Windows Mixed Reality Simulator verwenden.

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-hololens-2"></a>Einrichten der Mixed Reality OpenXR Developer Preview für HoloLens 2

Erste Schritte mit der Mixed Reality OpenXR Developer Preview für HoloLens 2:

1. Richten Sie eine HoloLens-2, oder führen Sie die Anweisungen, um [installieren Sie den Emulator für HoloLens 2](using-the-hololens-emulator.md).
1. Starten Sie den Store-app in dem Gerät oder Emulator aus, und stellen Sie sicher, dass alle apps aktualisiert werden.  Dadurch werden die Mixed Reality OpenXR Entwicklervorschau für die Verwendung mit apps auf dem Gerät installiert.  Wenn Sie den Emulator zu verwenden, sollten Sie zurate ziehen, um die [Emulator Eingabe Anweisungen](using-the-hololens-emulator.md#basic-emulator-input) können Sie die Store-app im Emulator zu verwenden.

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-immersive-desktop-headsets"></a>Die gemischte Realität OpenXR Entwicklervorschau für immersive desktop Headsets einrichten

Erste Schritte mit der Mixed Reality OpenXR Developer Preview auf einem desktop-PC:

1. Werden Sie sicher, dass Sie sind mindestens die Windows 10 Oktober 2018 aktualisieren (1809).  Wenn Sie eine frühere Version von Windows 10 sind, können Sie auf der Oktober 2018 aktualisieren Aktualisieren mit der [Update-Assistenten von Windows 10](https://www.microsoft.com/en-us/software-download/windows10).  Wenn Sie noch abenteuerlustig fühlen, können Sie installieren ein [Windows 10 Insider Preview-Build, der die Mai 2019 Update (1903)](https://insider.windows.com).
1. Richten Sie eine Windows Mixed Reality-Kopfhörer oder führen Sie die Anweisungen, um [aktivieren Sie die Windows Mixed Reality-Simulator](using-the-windows-mixed-reality-simulator.md).
1. Installieren Sie die [Mixed Reality OpenXR Developer Preview app](https://www.microsoft.com/store/productId/9n5cvvl23qbt).  Diese app ruft richten Sie mit der Vorschau OpenXR-Laufzeit unter Windows 10 Oktober 2018 Update (1809) oder höher.  Nach der Installation dieser app, bleibt die Windows Store die Laufzeit auf dem neuesten Stand.
1. Führen Sie die Mixed Reality OpenXR Developer Preview-app über das Startmenü, und befolgen Sie die Anweisungen, um die Laufzeit zu aktivieren.  In Kürze, diese app erlauben Ihnen, auch andere OpenXR Debuginformationen zu untersuchen.

![Mixed Reality OpenXR Developer Preview-app](images/mixed-reality-openxr-developer-preview.png)

### <a name="support-for-windows-10-october-2018-update"></a>Unterstützung für Windows 10 Oktober 2018 Update

Mit der Mixed Reality OpenXR Developer Preview auf einem desktop-PC mit Windows 10 Oktober 2018 für den Start zu aktualisieren (1809, die aktuelle Version von Windows), müssen Sie einige weitere Schritte ausführen:

1. Die Schritte aus, um die Mixed Reality OpenXR Developer Preview installieren.
1. Installieren Sie zum Festlegen der Mixed Reality OpenXR Developer Preview als aktive OpenXR-Laufzeit Ihres Systems die [Mixed Reality OpenXR Developer Preview Compatibility Pack](https://aka.ms/openxr-compat).

## <a name="building-a-sample-openxr-app"></a>Erstellen eine Beispiel-app OpenXR

Die [BasicXrApp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp) -Projekt zeigt ein Beispiel für einfache OpenXR mit zwei Visual Studio-Projekt-Dateien, eine für sowohl eine Win32-desktop-app und eine für eine UWP-HoloLens-2-app.  Da die Projektmappe ein HoloLens-UWP-Projekt enthält, müssen Sie die [entwicklungsworkload von universelle Windows-Plattform](install-the-tools.md#installation-checklist) installiert, die in Visual Studio, um ihn vollständig zu öffnen.

Beachten Sie, dass zwar die Win32- und UWP-Projektdateien aufgrund von Unterschieden bei der paketerstellung und Bereitstellung, den app-Code innerhalb jedes Projekt separate 100 % identisch ist.

## <a name="feedback"></a>Feedback senden

Geben von Feedback zur der [OpenXR bereitstellbare 0,90 Spezifikation](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html), finden Sie auf die [Khronos OpenXR Foren](https://community.khronos.org/c/openxr), [#openxr-Slack-Kanal](https://khr.io/slack) und die [Spezifikation problemverfolgung](https://github.com/KhronosGroup/OpenXR-Docs/issues).

## <a name="troubleshooting"></a>Problembehandlung

Hier sind einige Tipps zur Problembehandlung für das Mixed Reality OpenXR Developer Preview.  Wenn Sie sonstige erkannte Probleme auftreten, besuchen Sie bitte die [Khronos OpenXR Foren](https://community.khronos.org/c/openxr) oder [#openxr-Slack-Kanal](https://khr.io/slack).

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>OpenXR-app, die nicht gestartet werden, Windows Mixed Reality

Wenn Ihre app OpenXR bei der Ausführung nicht Windows Mixed Reality startet, kann die Mixed Reality OpenXR Developer Preview nicht als die aktive Laufzeit festgelegt werden.  Achten Sie darauf, führen Sie die Mixed Reality OpenXR Developer Preview-app, und befolgen die Anweisungen, um die Laufzeit zu aktivieren.

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a>Mixed Reality OpenXR Developer Preview-app kann nicht installiert werden 

Werden Sie sicher, dass Sie sind mindestens die Windows 10 Oktober 2018 aktualisieren (1809).  Wenn Sie eine frühere Version von Windows 10 sind, können Sie auf der Oktober 2018 aktualisieren Aktualisieren mit der [Update-Assistenten von Windows 10](https://www.microsoft.com/en-us/software-download/windows10).

Wenn die Installation der App Mixed Reality OpenXR Developer Preview Schaltfläche ist "nothing" unter Windows 10 Oktober 2018 aktualisieren, Ihr System möglicherweise veraltete Systemanforderungen für die app zwischengespeichert haben.  Sie können den Befehl ausführen `wsreset.exe` an einer Eingabeaufforderung zum Löschen des Caches.

## <a name="see-also"></a>Siehe auch

* [Weitere Informationen zu OpenXR](https://www.khronos.org/openxr/)
* [OpenXR bereitstellbare 0,90-Spezifikation](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [OpenXR bereitstellbare 0,90-API-Referenz](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [OpenXR bereitstellbare 0,90-Header](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
* [OpenXR bereitstellbare 0,90-Kurzübersicht](https://www.khronos.org/registry/OpenXR/specs/0.90/refguide/OpenXR-0.90-web.pdf)
