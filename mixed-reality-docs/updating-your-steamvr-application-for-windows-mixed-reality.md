---
title: Aktualisieren Ihre Anwendung SteamVR für Windows Mixed Reality
description: Bewährte Methoden für Ihre Anwendung SteamVR zum Maximieren der Kompatibilität mit Windows Mixed Reality-Headsets zu aktualisieren.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR, Compatibility
ms.openlocfilehash: db21651df8e586edf500f0d05def4b1ea5474284
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593368"
---
# <a name="updating-your-steamvr-application-for-windows-mixed-reality"></a>Aktualisieren Ihre Anwendung SteamVR für Windows Mixed Reality

Wir empfehlen Entwicklern, testen und optimieren ihre SteamVR Funktionen unter Windows Mixed Reality-Headsets ausgeführt. Diese Dokumentation umfasst allgemeine Verbesserungen, die Entwickler treffen können, um sicherzustellen, dass ihre Erfahrungen, die in Windows Mixed Reality großartig läuft.

## <a name="initial-setup-instructions"></a>Anweisungen zum ersten Einrichten

Zu testen Ihres Spiels oder Ihrer-app unter Windows Mixed Reality-stellen Sie sicher, dass auf erste folgen Sie unseren [Handbuch mit ersten Schritten.](http://aka.ms/WindowsMixedRealitySteamVR)

## <a name="controller-models"></a>Controller-Modelle
1. Wenn Ihre app Controller-Modellen wird gerendert:
    * Verwenden der [Windows Mixed Reality Motion-Controller-Modelle](motion-controllers.md#rendering-the-motion-controller-model)
    * IVRRenderModel::GetComponentState verwenden, um lokale erhalten transformiert in Komponenten (z. b. Zeiger Haltung)
2. Benutzeroberflächen, die Händigkeit Standardtyps erhalten Hinweise aus der Eingabe-APIs zum unterscheiden von Controllern [(Unity-Beispiel)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)

## <a name="controls"></a>Steuerelemente

Beim Entwerfen und Anpassen Ihrer Steuerelementlayout Beachten Sie den folgenden Satz von reservierten Befehle:
1. Klicken Sie auf die **linken und rechten analoge Ministick** ist reserviert für die **Datenstrom Dashboard**.
2. Die **Windows-Schaltfläche** Benutzer immer auf die Windows Mixed Reality home zurück.

Wenn möglich, standardmäßig die thumb-Stick basierend Teleportation entsprechend der [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) Teleportation-Verhalten

## <a name="tooltips-and-ui"></a>QuickInfos und Benutzeroberfläche

Viele VR-Spiele nutzen Motion-Controller-QuickInfos und überlagert, um Benutzer über die wichtigsten Befehle für ihre Spiele und Apps erfahren. Beim Optimieren Ihrer Anwendung für die Windows Mixed Reality wird empfohlen, überprüfen diesen Teil Ihrer Erfahrung, um sicherzustellen, dass die QuickInfos, die die Windows-Controller-Modelle zugeordnet.

Außerdem treten unbedingt alle Punkte in Ihre Umgebung, in denen Sie Bilder der Controller anzeigen, geben Sie die aktualisierten Abbilder mithilfe der Windows Mixed Reality-Motion-Controller.

## <a name="haptics"></a>Haptics

Beginnend mit der [Windows 10 April 2018 Update](release-notes-april-2018.md), Haptics werden jetzt unterstützt, SteamVR in Windows Mixed Reality-Funktionen zu nutzen. Wenn Sie bereits Ihren SteamVR App- oder Spiele-Unterstützung für Haptics enthält, es sollte jetzt funktionieren (mit ohne zusätzliche Arbeit) mit [Windows Mixed Reality-Motion-Controller](motion-controllers.md).

Windows Mixed Reality-Motion-Controller verwenden einen standardmäßigen Haptics Motor, im Gegensatz zu der linearen Aktuatoren finden Sie in einigen anderen SteamVR Motion Controllern, was zu einer etwas anderen als erwartet Benutzeroberfläche führen kann. Daher empfehlen wir testen und optimieren Ihren Haptics Entwurf mithilfe von Windows Mixed Reality-Motion-Controller. Beispielsweise sind gelegentlich kurze Übermitteln von haptischem Impulse (5 bis 10 ms) auf Windows Mixed Reality-Motion-Controllern weniger erkennbar. Um ein deutlicher Puls zu erzeugen, experimentieren Sie vor angewiesen wird, Power off erneut Bezug auf das Senden einer längeren "click" (40-70ms) um den motor mehr Zeit, um zu starten.

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>Starten von Windows Mixed Reality-Startmenü SteamVR-apps

Für VR-Umgebungen, die über den Datenstrom verteilt, haben wir [aktualisiert, die Windows Mixed Reality für SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) zusammen mit den neuesten [Windows Insider](https://insider.windows.com) RS5 Flügen, sodass SteamVR Titel jetzt in werden angezeigt die Windows Mixed Reality starten im Menü "alle apps" aufgeführt automatisch. Mit dieser Softwareversionen installiert können Ihre Kunden jetzt SteamVR Titel direkt aus in die Windows Mixed Reality Startseite starten, ohne ihre Headsets.

## <a name="windows-mixed-reality-logo"></a>Windows Mixed Reality-logo

Wechseln Sie zum Windows Mixed Reality-Unterstützung für den Titel anzuzeigen, klicken auf den Link "Store-Seite bearbeiten" auf Ihre App-Angebotsseite auf die Registerkarte "Grundlegende Info", und scrollen Sie zum "Virtual Reality". Deaktivieren Sie das "ausblenden Windows Mixed Reality" aus, und klicken Sie dann im Store veröffentlichen.

## <a name="bugs-and-feedback"></a>Fehler und feedback

Ihr Feedback ist sehr nützlich, wenn es darum geht, Verbessern der benutzerfreundlichkeit Windows Mixed Reality SteamVR. Bitte senden Sie alle Feedback und Fehler über die [Windows-Feedback-Hub](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback). Hier sind einige [Tipps zur Erstellung Ihres Feedbacks SteamVR als hilfreich wie möglich machen](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).

Wenn Sie Fragen oder Kommentare zum Freigeben verfügen, Sie können auch erreichen Sie uns auf unsere [Datenstrom Forum](http://steamcommunity.com/app/719950/discussions/).

## <a name="faqs-and-troubleshooting"></a>Häufig gestellte Fragen und Problembehandlung

Wenn Sie allgemeine Probleme, die zum Einrichten oder Wiedergabe Ihrer Erfahrungen ausführen [sehen Sie sich die neuesten Problembehandlungsschritte](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).

## <a name="see-also"></a>Siehe auch
* [Installieren der tools](install-the-tools.md)
* [Kopfhörer und Motion-Controller-Treiber-Verlauf](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Windows Mixed Reality minimale PC Kompatibilität an die hardwareempfehlungen](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
