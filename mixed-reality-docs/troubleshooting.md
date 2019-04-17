---
title: HoloLens-Problembehandlung
description: Schritte zur Problembehandlung, für Microsoft HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Probleme, Fehler, Problembehandlung, beheben und Unterstützung, HoloLens
ms.openlocfilehash: 7b7a32a9a358ff75b2675d265445d9ef1acc1b9e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593256"
---
# <a name="hololens-troubleshooting"></a>HoloLens-Problembehandlung

## <a name="my-hololens-is-unresponsive-or-wont-boot"></a>Meine HoloLens reagiert nicht oder nicht starten

Wenn Ihre HoloLens nicht mehr gestartet werden:
* Wenn die LEDs, indem Sie den Netzschalter light nicht immer oder nur 1 LED blinkt, kurz, müssen Sie möglicherweise Ihre HoloLens zu berechnen.
* Wenn die LEDs leuchtet auf, wenn Sie den Netzschalter drücken, aber Sie nicht, was auf die die Anzeige sehen können, halten Sie den Netzschalter betätigen, bis alle 5 die LEDs, indem Sie den Netzschalter deaktivieren.

Wenn Ihre HoloLens fixierten oder nicht reagiert wird:
* Deaktivieren Sie Ihre HoloLens aus, indem Sie den Netzschalter drücken, bis die LEDs, indem Sie den Netzschalter alle 5 selbst deaktivieren, oder für 10 Sekunden aktivieren, wenn die LEDs nicht reagiert werden. Drücken Sie die Netzschalter erneut aus, um zu starten.

Wenn Sie diese Schritte funktionieren nicht:
* Sie können versuchen, [Wiederherstellen Ihres Geräts](reset-or-recover-your-hololens.md).

## <a name="holograms-dont-look-good-or-are-moving-around"></a>Hologramme nicht gut aussehen oder verschoben werden.

Wenn Ihre Hologramme instabil, ruckartige sind oder nicht angezeigt ordnungsgemäß, probieren Sie eine dieser Fixes:
* Bereinigen Sie Ihr Gerät Hypervisor, und stellen Sie sicher, dass nichts die Sensoren sitzt ist.
* Stellen Sie sicher, dass genügend Licht in Ihre Platz vorhanden ist.
* Versuchen Sie es zu durchlaufen, um aus, und sehen sich Ihre Umgebung so HoloLens können sie mehr vollständig gescannt werden.
* Führen Sie die Kalibrierung-app. Es wird kalibriert Ihre HoloLens zur Ihren Augen am besten geeignet. Wechseln Sie zu **Einstellungen** > **System** > **Dienstprogramme**. Wählen Sie die Kalibrierung der **öffnen Kalibrierung**.
* Wenn weiterhin Probleme auftreten werden nach dem Ausführen der app Kalibrierung, mithilfe der app-Sensor Optimierung um Ihrer gerätesensoren zu optimieren. Wechseln Sie zu **Einstellungen** > **System** > **Dienstprogramme**. Wählen Sie unter Sensor zu optimieren, **öffnen Sensor Optimierung**.

## <a name="hololens-doesnt-respond-to-my-gestures"></a>HoloLens, die auf Meine Gesten reagiert nicht.

Um sicherzustellen, dass die HoloLens Ihrer Aktionen sehen können, halten Sie Ihre Hand im Frame Geste, der eine Reihe von Fuß auf beiden Seiten von Ihnen erweitert. Wenn HoloLens Ihre Hand angezeigt wird können, ändert sich der Cursor aus einem Punkt in einen Ring. Weitere Informationen zur Verwendung [Gesten](gestures.md).

Wenn Ihre Umgebung zu dunkel befindet, möglicherweise nicht HoloLens finden Sie unter der Hand, stellen Sie daher sicher, dass genügend Licht.

Wenn Ihre gemeinsame Fingerabdrücke oder verwischen verfügt, verwenden Sie die Microfiber bereinigen Holz, das in die HoloLens Ihre Visor vorsichtig bereinigt wurde.

## <a name="hololens-doesnt-respond-to-my-voice-commands"></a>HoloLens reagiert nicht auf Meine Sprachbefehle.

Stellen Sie Cortana auf Ihre Sprachbefehle nicht antwortet, sicher, dass Cortana aktiviert ist. Wählen Sie auf der alle apps Cortana > Menü > Notebook > Einstellungen, um Änderungen vorzunehmen. Um weitere Informationen dazu, was Sie sagen können, finden Sie unter Verwenden Ihre Stimme zum Steuern von HoloLens.

## <a name="i-cant-place-holograms-or-see-holograms-i-previously-placed"></a>Nicht Hologramme platzieren oder finden Sie unter Hologramme, die ich zuvor platziert werden.

Wenn HoloLens kann nicht zugeordnet oder der Speicherplatz zu laden, wird es Limited-Modus versetzt, und nicht möglich Hologramme platzieren oder finden Sie unter Hologramme, die Sie gespeichert haben. Probieren Sie Folgendes aus:
* Stellen Sie sicher, dass genügend Licht in Ihrer Umgebung vorhanden ist, damit die HoloLens finden Sie unter und den Speicherplatz zugeordnet werden kann.
* Stellen Sie sicher, dass Sie mit einem Wi-Fi-Netzwerk verbunden sind. Wenn Sie nicht mit Wi-Fi verbunden sind, kann nicht HoloLens identifizieren und zu einem bekannten Leerzeichen laden.
* Wenn Sie zum Erstellen eines neuen Bereichs müssen, Wi-Fi-Verbindung, und starten Sie Ihre HoloLens.
* Um festzustellen, ob der richtige Platz aktiv ist, oder ein Leerzeichen manuell laden, wechseln Sie zu **Einstellungen** > **System** > **Leerzeichen**.
* Wenn der richtige Platz geladen wird und sind weiterhin Probleme auftreten, wird der Speicherplatz ist möglicherweise beschädigt. Um dieses Problem zu beheben, wählen Sie den Speicherplatz, und wählen Sie dann entfernen. Sobald die Leerzeichen entfernt wurde, HoloLens startet, Zuordnen von Ihrer Umgebung und Erstellen eines neuen Bereichs.

## <a name="my-hololens-frequently-enters-limited-mode-or-shows-a-tracking-lost-message"></a>Meine HoloLens häufig Limited-Modus wechselt, oder zeigt eine Meldung "Tracking verloren".

Wenn Ihr Gerät häufig ein "Modus limited" oder eine Nachricht "nachverfolgung" verloren"angezeigt wird, versuchen Sie es mit den Vorschlägen von [Meine Hologramme nicht gut aussehen oder verschoben werden](#holograms-dont-look-good-or-are-moving-around).

## <a name="my-hololens-cant-tell-what-space-im-in"></a>Meine HoloLens erkennbar nicht, verfügbaren Speicherplatz in der.

Wenn Ihre HoloLens kann nicht automatisch ermitteln und laden den Speicherplatz befinden Sie sich im, stellen Sie sicher, dass Sie Wi-Fi verbunden sind, es bleibt noch viel des Lichts im Raum und alle wichtigen Änderungen an der Umgebung noch nicht. Sie können auch manuell laden, ein Leerzeichen oder hier verwalten: Ihre Leerzeichen **Einstellungen** > **System** > **Leerzeichen**.

## <a name="im-getting-a-low-disk-space-error"></a>Ich erhalte einen Fehler "wenig Speicherplatz".

Sie müssen einige Speicherplatz freizugeben, indem Sie eine oder mehrere der folgenden:
* Löschen Sie einige nicht verwendeten Leerzeichen ein. Wechseln Sie zu **Einstellungen** > **System** > **Leerzeichen**, wählen Sie ein Leerzeichen, die Sie nicht mehr benötigen, und wählen Sie dann **entfernen**.
* Entfernen Sie einige der Hologramme, die Sie gespeichert haben.
* Löschen Sie einige Bilder und Videos in der Fotos-app.
* Deinstallieren Sie einige apps von Ihrer HoloLens. Klicken Sie in der Liste mit allen apps tippen und halten Sie die app, die Sie verwenden möchten, deinstallieren, und wählen Sie dann **Deinstallieren**.

## <a name="my-hololens-cant-create-a-new-space"></a>Meine HoloLens kann kein neues Bereichs erstellt werden.

Das Problem wahrscheinlichste darin ist, dass Sie auf verfügt über unzureichenden Speicherplatz haben. Führen Sie eine der der [Tipps, die oben genannten](#im-getting-a-low-disk-space-error) , um Speicherplatz freizugeben.
