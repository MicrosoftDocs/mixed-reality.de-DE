---
title: Hololens-Problembehandlung
description: Schritte zur Problembehandlung für Microsoft hololens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Probleme, Fehler, Problembehandlung, Behebung, Hilfe, Support, hololens
ms.openlocfilehash: 855bb0cafb0d3fba0d8d97c93d9415b51bcc2fb3
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438280"
---
# <a name="hololens-troubleshooting"></a>Hololens-Problembehandlung

## <a name="my-hololens-is-unresponsive-or-wont-boot"></a>Meine hololens reagiert nicht oder wird nicht gestartet.

Wenn Ihre hololens nicht gestartet werden:
* Wenn die LEDs nach dem Netzschalter nicht leuchten oder nur eine LED kurz mit Blinks verknüpft ist, müssen Sie möglicherweise Ihre hololens berechnen.
* Wenn die LEDs angezeigt werden, wenn Sie den Netzschalter drücken, aber auf den angezeigten anzeigen nichts angezeigt wird, halten Sie den Netzschalter gedrückt, bis alle 5 der LEDs durch Drücken der Schaltfläche ausschalten.

Wenn Ihre hololens eingefroren oder nicht mehr reagiert:
* Deaktivieren Sie die hololens, indem Sie den Netzschalter drücken, bis alle 5 der LEDs von der Netz Taste ausgeschaltet sind, oder 10 Sekunden, wenn die LEDs nicht reagiert. Drücken Sie erneut die Taste, um zu starten.

Wenn diese Schritte nicht funktionieren:
* Sie können versuchen, [Ihr Gerät](reset-or-recover-your-hololens.md)wiederherzustellen.

## <a name="holograms-dont-look-good-or-are-moving-around"></a>Holograms sind nicht gut geeignet oder werden verschoben.

Wenn Ihre Hologramme instabil, schnell oder nicht richtig aussehen, versuchen Sie es mit einer der folgenden Korrekturen:
* Bereinigen Sie Ihren Geräte-Hypervisor, und stellen Sie sicher, dass die Sensoren nicht behindert werden.
* Stellen Sie sicher, dass genügend Licht in Ihrem Raum vorhanden ist.
* Versuchen Sie, die Umgebung zu durchlaufen und zu betrachten, damit hololens Sie vollständig scannen können.
* Versuchen Sie, die Kalibrierungs-App auszuführen. Die hololens werden so kalibriert, dass Sie am besten für Sie geeignet sind. Wechseln Sie zu **Einstellungen** > **System** > **Hilfsprogramme**. Wählen Sie unter Kalibrierung die Option **Kalibrierung öffnen**aus.
* Wenn nach dem Ausführen der Kalibrierungs-App weiterhin Probleme auftreten, verwenden Sie die Sensor Optimierungs-APP, um Ihre Geräte Sensoren zu optimieren. Wechseln Sie zu **Einstellungen** > **System** > **Hilfsprogramme**. Wählen Sie unter Sensor Optimierung die Option **Sensor Optimierung öffnen**aus.

## <a name="hololens-doesnt-respond-to-my-gestures"></a>Hololens reagiert nicht auf meine Gesten.

Um sicherzustellen, dass hololens ihre Gesten sehen können, behalten Sie die Hand in dem Gesten Rahmen, der einige Füße auf beiden Seiten von Ihnen erweitert. Wenn hololens Ihre Hand sehen können, ändert sich der Cursor von einem Punkt in einen Ring. Erfahren Sie mehr über die Verwendung von [Gesten](gaze-and-commit.md#composite-gestures).

Wenn Ihre Umgebung zu dunkel ist, werden hololens möglicherweise nicht angezeigt. Stellen Sie also sicher, dass genügend Licht vorhanden ist.

Wenn Ihr Hypervisor Fingerabdrücke oder Smudge hat, verwenden Sie das Mikro Fiber-Reinigungstuch, das in den hololens enthalten war, um Ihren Hypervisor sanft zu bereinigen.

## <a name="hololens-doesnt-respond-to-my-voice-commands"></a>Hololens antwortet nicht auf meine Sprachbefehle.

Wenn Cortana nicht auf Ihre Sprachbefehle antwortet, stellen Sie sicher, dass Cortana aktiviert ist. Wählen Sie in der Liste alle apps die Option Cortana > Menü > Notebook > Einstellungen aus, um Änderungen vorzunehmen. Weitere Informationen dazu, was Sie sagen können, finden Sie unter Verwenden Ihrer Stimme zum Steuern von hololens.

## <a name="i-cant-place-holograms-or-see-holograms-i-previously-placed"></a>Ich kann keine holograms platzieren, oder ich möchte holograms nicht anzeigen.

Wenn hololens Ihren Speicherplatz nicht zuordnen oder laden kann, wird der Modus in den eingeschränkten Modus versetzt, und Sie können keine Hologramme platzieren, oder Sie können die von Ihnen platzierten holograms nicht anzeigen. Probieren Sie Folgendes aus:
* Stellen Sie sicher, dass in Ihrer Umgebung ausreichend Licht vorhanden ist, sodass hololens den Raum sehen und zuordnen können.
* Stellen Sie sicher, dass Sie mit einem WLAN-Netzwerk verbunden sind. Wenn Sie nicht mit Wi-Fi verbunden sind, können hololens einen bekannten Bereich nicht identifizieren und laden.
* Wenn Sie einen neuen Speicherplatz erstellen müssen, stellen Sie eine Verbindung mit Wi-Fi her, und starten Sie die hololens neu.
* Um festzustellen, ob der richtige Speicherplatz aktiv ist, oder um ein Leerzeichen manuell zu laden, wechseln Sie zu **Einstellungen** > **System** > **Spaces**.
* Wenn der richtige Speicherplatz geladen ist und Sie weiterhin Probleme haben, ist der Speicherplatz möglicherweise beschädigt. Um dieses Problem zu beheben, wählen Sie den Bereich aus, und klicken Sie auf entfernen. Nachdem das Leerzeichen entfernt wurde, beginnen hololens damit, Ihre Umgebung zu ordnen und einen neuen Speicherplatz zu erstellen.

## <a name="my-hololens-frequently-enters-limited-mode-or-shows-a-tracking-lost-message"></a>Meine hololens wechselt häufig in den eingeschränkten Modus oder zeigt eine Meldung "Nachverfolgung verloren" an.

Wenn auf Ihrem Gerät häufig die Meldung "eingeschränkter Modus" oder "Nachverfolgung verloren" angezeigt wird, probieren Sie die Vorschläge von " [meine holograms" nicht gut aus, oder gehen Sie um](#holograms-dont-look-good-or-are-moving-around).

## <a name="my-hololens-cant-tell-what-space-im-in"></a>Meine hololens können nicht erkennen, in welchem Bereich ich bin.

Wenn Ihre hololens den verwendeten Speicherplatz nicht automatisch identifizieren und laden können, stellen Sie sicher, dass Sie mit Wi-Fi verbunden sind, dass es viel Licht in den Raum gibt, und es gab keine größeren Änderungen an der Umgebung. Sie können ein Leerzeichen auch manuell laden oder die Leerzeichen verwalten, indem Sie zu **Einstellungen** > **System** > **Spaces**wechseln.

## <a name="im-getting-a-low-disk-space-error"></a>Ich erhalte den Fehler "wenig Speicherplatz".

Sie müssen Speicherplatz freigeben, indem Sie eine oder mehrere der folgenden Aktionen ausführen:
* Löschen Sie einige nicht verwendete Leerzeichen. Wechseln Sie zu **Einstellungen** > **System** > **Spaces**, wählen Sie einen Speicherplatz aus, den Sie nicht mehr benötigen, und wählen Sie dann **Entfernen**aus.
* Entfernen Sie einige der von Ihnen platzierten holograms.
* Löschen Sie einige Bilder und Videos in der Fotos-app.
* Deinstallieren Sie einige apps aus ihren hololens. Tippen Sie in der Liste alle apps auf die zu deinstallierende APP, und wählen Sie dann **deinstallieren**aus.

## <a name="my-hololens-cant-create-a-new-space"></a>Meine hololens können keinen neuen Speicherplatz erstellen.

Das wahrscheinlichste Problem ist, dass der Speicherplatz knapp wird. Probieren Sie einen der [obigen Tipps](#im-getting-a-low-disk-space-error) aus, um Speicherplatz freizugeben.
