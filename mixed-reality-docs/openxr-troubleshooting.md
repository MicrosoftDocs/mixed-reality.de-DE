---
title: Problembehandlung bei openxr
description: Beheben Sie Probleme in ihren openxr-Anwendungen.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: Openxr, Khronos, basicxrapp, DirectX, Native, Native APP, benutzerdefinierte Engine, Middleware, Problembehandlung
ms.openlocfilehash: 08ca671ded7230a4ba3cfcdc640233082af51040
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163364"
---
# <a name="openxr-troubleshooting"></a>Problembehandlung bei openxr

Im folgenden finden Sie einige Tipps zur Problembehandlung bei der Entwicklung einer openxr-App mithilfe der Windows Mixed Reality openxr-Laufzeit.  Wenn Sie weitere Fragen zur <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">openxr 1,0-Spezifikation</a>haben, besuchen Sie die <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos openxr-Foren</a> oder <a href="https://khr.io/slack" target="_blank">Slack #openxr Channel</a>.

>[!NOTE]
>In der aktuellen Windows Mixed Reality openxr-Laufzeit mit x86-apps sind bekannte Probleme aufgetreten.  Sie sollten momentan openxr-Desktop-Apps für x64 erstellen.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>Openxr-App startet nicht Windows Mixed Reality

Wenn Ihre openxr-APP nicht Windows Mixed Reality startet, wenn Sie Sie ausführen, kann die openxr-Laufzeit von Windows Mixed Reality nicht als aktive Laufzeit festgelegt werden.  Befolgen Sie die obigen Anweisungen für den [Einstieg in openxr für Windows Mixed Reality-Headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) , um die Laufzeit zu aktivieren.

Sie können auch das [Windows Mixed Reality openxr-Entwickler Portal](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-portal) ausführen, um weitere Hilfe zur Problembehandlung im Zusammenhang mit dem Status der Windows Mixed Reality openxr-Laufzeit auf Ihrem System zu erhalten.

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a>Das gemischte Reality-Portal zeigt das Menü Element "Set up openxr" nicht an.

Stellen Sie sicher, dass mindestens das Windows 10-Update vom Oktober 2018 (1809) ausgeführt wird.  Wenn Sie eine frühere Version von Windows 10 verwenden, können Sie mit dem [Windows 10 Update Assistant](https://www.microsoft.com//software-download/windows10)auf das Update von Mai 2019 (1903) aktualisieren.

Das Menü Element "Einrichten von openxr" ist möglicherweise nicht verfügbar, wenn Sie eine ältere Version der Mixed Reality-Portal-APP haben.  [Überprüfen Sie, ob](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m) Sie über die neueste Version verfügen.

Beachten Sie, dass das Menü Element "Set up openxr" nicht angezeigt wird, wenn die Windows Mixed Reality openxr-Laufzeit bereits installiert und aktiv ist.  Sie können das [Windows Mixed Reality openxr-Entwickler Portal](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-portal) installieren, um den aktuellen Status der openxr-Laufzeit auf Ihrem System zu ermitteln.