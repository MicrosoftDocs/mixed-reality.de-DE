---
title: Windows Mixed Reality und die neue Microsoft Edge
description: Machen Sie sich bereit für den neuen Microsoft Edge in Windows Mixed Reality. Enthält Änderungen, die erwartet werden sollen, sowie bekannte Probleme.
author: mattzmsft
ms.author: mazeller
ms.date: 01/15/2020
ms.topic: article
keywords: Edge, neu, immersives Web, Microsoft Edge, Browser, VR
ms.openlocfilehash: d61780045e795850012536a36fde67b9934c76aa
ms.sourcegitcommit: 4282d92e93869e4829338bdf7d981c3ee0260bfd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85216231"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality und die neue Microsoft Edge

Der [neue Microsoft Edge ist jetzt zum Herunterladen verfügbar](https://blogs.windows.com/windowsexperience/?p=173496), aber Kunden können auch warten, bis [Sie in einem zukünftigen Update von Windows 10 installiert werden. Befolgen Sie dabei](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/)in den nächsten Monaten einen gemessenen Rollout. 

Mit dieser Nachricht möchten **wir den Windows Mixed Reality-VR-Headset-Kunden wissen, was von der neuen Microsoft Edge zu erwarten ist, und Sie über einige ausstehende Updates informieren, die ihre webbrowserdarstellung in Windows Mixed Reality verbessern**.

## <a name="introducing-the-new-microsoft-edge"></a>Einführung in den neuen Microsoft Edge

Die neue Microsoft Edge-Website [übernimmt das Projekt "Chrom Open Source](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) " auf dem Desktop, um eine bessere webkompatibilität für Kunden und weniger Fragmentierung des Internets für alle Webentwickler zu erzielen. Es unterstützt auch webxr beim Start, den neuen Standard zum Erstellen von immersiven Webumgebungen für VR-Headsets anstelle von webvr.

>[!IMPORTANT]
>Wenn Sie Microsoft Edge auf einem aktuellen Windows 10-Gerät installieren, ersetzt es die vorherige (Legacy-) Version auf Ihrem PC.

## <a name="getting-ready-for-the-new-microsoft-edge"></a>Vorbereitung auf den neuen Microsoft Edge

Windows Mixed Reality VR-Headset-Kunden, die den neuen Microsoft Edge in der Mixed Reality-Startseite verwenden möchten, sollten **auf Windows 10, Version 1903 oder höher, für die native Unterstützung von Win32-Anwendungen (wie dem neuen Microsoft Edge)** in der Mixed Reality-Startseite aktualisieren. Überprüfen Sie Windows Update oder [Installieren Sie die neueste Version von Windows 10 manuell](https://www.microsoft.com/en-us/software-download/windows10).

Um die bestmögliche Microsoft Edge-Benutzersprache in der Mixed Reality-Startseite zu nutzen, wird empfohlen, auf **einige wichtige Windows Mixed Reality-Optimierungen für den neuen Microsoft Edge zu warten, der mit dem kumulativen Update von 2020-01 für Windows 10, Version 1903 (oder höher)**, erreichbar ist, das in Windows Update bis Ende Januar verfügbar sein sollte.

>[!IMPORTANT]
>Wenn Sie den neuen Microsoft Edge herunterladen möchten, bevor Sie diese Updates ausführen, gibt es einige bekannte Probleme mit dem Verhalten in Windows Mixed Reality (Weitere Informationen finden Sie weiter unten).

## <a name="known-issues"></a>Bekannte Probleme

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Bekannte Probleme, die durch das kumulative Update 2020-01 für Windows 10, Version 1903 (oder höher) behoben wurden

- Das Starten einer beliebigen Win32-APP, einschließlich des neuen Microsoft Edge, bewirkt, dass die Headset-Anzeige kurz fixiert wird.
- Die Microsoft Edge-Kachel verschwindet im Windows Mixed Reality-Startmenü (Sie finden es im Ordner "Classic Apps").
- Windows aus dem vorherigen Microsoft Edge wird immer noch um die gemischte Realität herum platziert, kann aber nicht verwendet werden. Der Versuch, diese Windows-Fenster in der Desktop-App zu aktivieren, wird gestartet.
- Wenn Sie einen Link in der Mixed Reality-Startseite auswählen, wird ein Webbrowser auf dem Desktop anstelle der Mixed Reality-Startseite gestartet.
- Die webvr-Showcase-APP ist in der Mixed Reality-Homepage enthalten, obwohl webvr nicht mehr unterstützt wird.
- Allgemeine Verbesserungen beim Starten von Tastatur und visuellen Elementen.

### <a name="additional-known-issues"></a>Weitere bekannte Probleme

-   Websites, die in Windows Mixed Reality geöffnet werden, gehen verloren, wenn das gemischte Reality-Portal geschlossen wird. die Microsoft Edge-Fenster bleiben jedoch erhalten, wo Sie in der Mixed Reality-Startseite platziert werden.
- Webxr-Funktionen, einschließlich der 360 Viewer-Erweiterung, werden möglicherweise auf PCs mit einem Hybrid-GPU-Setup nicht ordnungsgemäß gestartet. Sie können dieses Problem möglicherweise umgehen, indem Sie Ihre dedizierte GPU als standardgpu in Ihrer Grafikkarten Software auswählen.
-   Das Audioformat von Microsoft Edge-Fenstern ist nicht räumlich.
-   **Korrigiert in 360 Viewer Extension Version 2.3.8**: das Öffnen eines 360-Videos von YouTube in Windows Mixed Reality kann dazu führen, dass das Video im Headset verzerrt wird. Das Neustarten von Edge sollte die 360 Viewer-Erweiterung unsichtbar aktualisieren, um dieses Problem zu beheben. Sie können überprüfen, welche Version der Erweiterung Sie haben, indem Sie `edge://system/` in die Adressleiste eingeben und auf die Schaltfläche **erweitern** neben "Erweiterungen" klicken.
-   Während Windows Mixed Reality-Sitzungen werden virtuelle Monitore in den Einstellungen > System > Anzeige als generische physische Monitore angezeigt.



