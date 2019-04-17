---
title: OpenXR
description: Testen Sie die vorläufigen OpenXR 0,90-API mit der Mixed Reality OpenXR Developer Preview.
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: Mixed Reality OpenXR Entwicklervorschau
ms.openlocfilehash: 0d8debf5c12cb88aaba402145c6a597f761491ee
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596354"
---
# <a name="openxr"></a>OpenXR

OpenXR ist eine open Standard-lizenzgebührenfreie aus [Khronos](https://www.khronos.org/) , einheitlichen Zugriff auf eine große Bandbreite von Geräten bereitstellt, von vielen Anbietern, die umfassen die [mixed Reality Spektrum](mixed-reality.md).

Mit OpenXR, können Sie erstellen, Anwendungen, die sowohl holographic-Geräten (z. B. 2 für HoloLens), die digitalen Inhalte in der Praxis zu platzieren, als gäbe es wirklich, als auch immersive Geräte (z. B. Windows Mixed Reality-Headsets für desktop-PCs), das Ausblenden der physische Welt und durch eine digitale Inhalte zu ersetzen.  OpenXR können Sie Code schreiben, nachdem die, die für eine Vielzahl unterschiedlicher Hardwareplattformen dann portabel ist.

Der OpenXR Standard ist zurzeit in einer vorläufigen Phase mit einer anfänglichen OpenXR 0,90-Spezifikation für Feedback veröffentlicht.  Weitere Informationen zu OpenXR, einschließlich des Zugriffs auf die [vorläufigen 0,90 Spezifikation](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html) und [Header](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr), finden Sie unter den [Khronos OpenXR Seite](https://www.khronos.org/openxr/).

## <a name="setting-up-the-mixed-reality-openxr-developer-preview"></a>Einrichten der Mixed Reality OpenXR Developer Preview

Sie können die vorläufigen OpenXR 0,90-API verwenden die Mixed Reality OpenXR Developer Preview noch heute testen.  Diese frühe Laufzeit kann Anwendungen für die API OpenXR 0,90 Ziel immersive Headsets auf dem Desktop, Windows Mixed Reality.  Wenn Sie keinen Zugriff auf einen Kopfhörer haben, können Sie stattdessen Windows Mixed Reality Simulator verwenden.

Erste Schritte mit der Mixed Reality OpenXR Developer Preview:

1. Werden Sie sicher, dass Sie sind mindestens die Windows 10 Oktober 2018 aktualisieren.  Wenn Sie eine frühere Version von Windows 10 sind, können Sie auf der Oktober 2018 aktualisieren Aktualisieren mit der [Update-Assistenten von Windows 10](https://www.microsoft.com/en-us/software-download/windows10).  Wenn Sie noch abenteuerlustig fühlen, können Sie installieren ein [Windows 10 Insider Preview Build](https://insider.windows.com).
1. Richten Sie eine Windows Mixed Reality-Kopfhörer oder führen Sie die Anweisungen, um [aktivieren Sie die Windows Mixed Reality-Simulator](using-the-windows-mixed-reality-simulator.md).
1. Installieren Sie die [Mixed Reality OpenXR Developer Preview app](https://www.microsoft.com/store/productId/9n5cvvl23qbt).  Diese app ruft Sie in der Vorschauversion OpenXR-Laufzeit unter Windows 10 Oktober 2018 aktualisieren oder höher.  Nach der Installation dieser app, bleibt die Windows Store die Laufzeit auf dem neuesten Stand.
1. Führen Sie die Mixed Reality OpenXR Developer Preview-app über das Startmenü, und befolgen Sie die Anweisungen, um die Laufzeit zu aktivieren.  In Kürze, diese app erlauben Ihnen, auch andere OpenXR Debuginformationen zu untersuchen.

![Mixed Reality OpenXR Developer Preview-app](images/mixed-reality-openxr-developer-preview.png)

## <a name="support-for-windows-10-october-2018-update"></a>Unterstützung für Windows 10 Oktober 2018 Update

Für den Anfang mit der Mixed Reality OpenXR Developer Preview auf dem Windows 10 Oktober 2018 aktualisieren (die aktuelle Version von Windows), müssen Sie einige weitere Schritte ausführen:

1. Die Schritte aus, um die Mixed Reality OpenXR Developer Preview installieren.
1. Installieren Sie zum Festlegen der Mixed Reality OpenXR Developer Preview als aktive OpenXR-Laufzeit Ihres Systems die [Mixed Reality OpenXR Developer Preview Compatibility Pack](https://aka.ms/openxr-compat).

## <a name="building-a-test-openxr-app"></a>Erstellen einen Test OpenXR-app

Die [Hello_xr](https://github.com/KhronosGroup/OpenXR-SDK/tree/master/src/tests/hello_xr) OpenXR-Test-app veranschaulicht die Verwendung der verschiedenen Teile der API.  Führen Sie diese [einrichtungsanweisungen](https://github.com/KhronosGroup/OpenXR-SDK/blob/master/BUILDING.md), dem der Test-app und die OpenXR-Header selbst erstellen.

## <a name="feedback"></a>Feedback senden

Geben von Feedback zur der [OpenXR bereitstellbare 0,90 Spezifikation](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html), finden Sie auf die [Khronos OpenXR Foren](https://community.khronos.org/c/openxr), [#openxr-Slack-Kanal](https://khr.io/slack) und die [Spezifikation problemverfolgung](https://github.com/KhronosGroup/OpenXR-Docs/issues).

## <a name="troubleshooting"></a>Problembehandlung

Hier sind einige Tipps zur Problembehandlung für das Mixed Reality OpenXR Developer Preview.  Wenn Sie sonstige erkannte Probleme auftreten, besuchen Sie bitte die [Khronos OpenXR Foren](https://community.khronos.org/c/openxr) oder [#openxr-Slack-Kanal](https://khr.io/slack).

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>OpenXR-app, die nicht gestartet werden, Windows Mixed Reality

Wenn Ihre app OpenXR bei der Ausführung nicht Windows Mixed Reality startet, kann die Mixed Reality OpenXR Developer Preview nicht als die aktive Laufzeit festgelegt werden.  Achten Sie darauf, führen Sie die Mixed Reality OpenXR Developer Preview-app, und befolgen die Anweisungen, um die Laufzeit zu aktivieren.

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a>Mixed Reality OpenXR Developer Preview-app kann nicht installiert werden 

Werden Sie sicher, dass Sie sind mindestens die Windows 10 Oktober 2018 aktualisieren.  Wenn Sie eine frühere Version von Windows 10 sind, können Sie auf der Oktober 2018 aktualisieren Aktualisieren mit der [Update-Assistenten von Windows 10](https://www.microsoft.com/en-us/software-download/windows10).

Wenn die Installation der App Mixed Reality OpenXR Developer Preview Schaltfläche ist "nothing" unter Windows 10 Oktober 2018 aktualisieren, Ihr System möglicherweise veraltete Systemanforderungen für die app zwischengespeichert haben.  Sie können den Befehl ausführen `wsreset.exe` an einer Eingabeaufforderung zum Löschen des Caches.

## <a name="see-also"></a>Siehe auch

* [Weitere Informationen zu OpenXR](https://www.khronos.org/openxr/)
* [OpenXR bereitstellbare 0,90-Spezifikation](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [OpenXR bereitstellbare 0,90-API-Referenz](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [OpenXR bereitstellbare 0,90-Header](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
