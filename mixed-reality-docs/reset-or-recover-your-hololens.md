---
title: Zurücksetzen oder Wiederherstellen von hololens
description: Sowohl grundlegende als auch erweiterte Anweisungen zum Neustarten oder Zurücksetzen der hololens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Vorgehensweise, Neustart, zurücksetzen, wiederherstellen, harte zurück setzung, vorläufiges zurücksetzen, Energie Zyklen, hololens, Herunterfahren
ms.openlocfilehash: abf71a5f122b1c6f800bf970f51da11a34be956b
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524028"
---
# <a name="reset-or-recover-your-hololens"></a>Zurücksetzen oder Wiederherstellen von hololens

Wenn Sie Probleme mit ihren hololens haben, können Sie versuchen, mit der Geräte Wiederherstellung einen Neustart, eine zurück setzung oder sogar einen erneuten Flash Vorgang auszuführen. Dieses Dokument führt Sie durch die empfohlenen Schritte nacheinander.

## <a name="perform-a-device-reboot"></a>Ausführen eines Geräte Neustarts

Wenn in den hololens Probleme auftreten oder nicht reagiert wird, versuchen Sie es zunächst mit einer der folgenden Methoden neu zu starten.

### <a name="perform-a-safe-reboot-via-cortana"></a>Ausführen eines sicheren Neustarts über Cortana

Die sicherste Möglichkeit zum Neustarten der hololens ist über Cortana. Dies ist im Allgemeinen ein hervorragend erster Schritt, wenn ein Problem mit hololens auftritt:
1. Auf Ihrem Gerät platzieren
2. Stellen Sie sicher, dass Sie eingeschaltet ist, dass ein Benutzer angemeldet ist und das Gerät nicht darauf wartet, dass ein Kennwort zum Entsperren dieses Kennworts angezeigt wird.
3. Sagen Sie "Hey Cortana, Reboot" oder "Hey Cortana, Restart".
4. Wenn Sie bestätigt, dass Sie eine Bestätigung erhalten. Warten Sie einen Moment, bis ein Sound wiedergegeben wird, nachdem er die Frage gestellt hat, und geben Sie an, dass Sie Sie hört und dann "yes" (ja).
5. Das Gerät wird jetzt neu gestartet/neu gestartet.

### <a name="perform-a-safe-reboot-via-windows-device-portal"></a>Ausführen eines sicheren Neustarts über das Windows-Geräte Portal

Wenn die obige Funktion nicht funktioniert, können Sie versuchen, das Gerät über das [Windows-Geräte Portal](using-the-windows-device-portal.md)neu zu starten. In der oberen rechten Ecke gibt es eine Option, mit der das Gerät neu gestartet/heruntergefahren werden kann.

### <a name="perform-a-safe-reboot-via-the-power-button"></a>Ausführen eines sicheren Neustarts über den Netzschalter

Wenn Sie das Gerät immer noch nicht neu starten können, können Sie versuchen, einen Neustart über den Netzschalter auszugeben:
1. Drücken und halten Sie den Netzschalter 5 Sekunden lang gedrückt.
   1. Nach 1 Sekunde werden alle fünf LEDs beleuchtet, und langsam von rechts nach links ausschalten.
   2. Nach 5 Sekunden sind alle LEDs deaktiviert, was darauf hinweist, dass der Befehl zum Herunterfahren erfolgreich ausgegeben wurde.
   3. Beachten Sie, dass es wichtig ist, die Schaltfläche sofort zu beenden, nachdem alle LEDs ausgeschaltet wurden.
2. Warten Sie eine Minute, bis das Herunterfahren ordnungsgemäß ausgeführt wurde. Beachten Sie, dass das Herunterfahren möglicherweise noch in Bearbeitung ist, auch wenn die Anzeige deaktiviert ist.
3. Schalten Sie das Gerät erneut ein, indem Sie den Netzschalter 1 Sekunde gedrückt halten.

### <a name="perform-an-unsafe-forced-reboot"></a>Ausführen eines unsicheren erzwungenen Neustarts

Wenn keine der oben genannten Methoden in der Lage ist, das Gerät neu zu starten, können Sie einen Neustart erzwingen. Beachten Sie, dass diese Methode dem Abrufen der Batterie aus den hololens entspricht und daher ein gefährlicher Vorgang ist, der das Gerät in einem beschädigten Zustand belassen kann. 

>[!WARNING]
>Dies ist eine potenziell schädliche Methode und sollte nur verwendet werden, wenn keine der oben genannten Methoden funktioniert.

1. Halten Sie den Netzschalter für mindestens 10 Sekunden gedrückt.
   * Es ist in Ordnung, die Schaltfläche länger als 10 Sekunden aufzunehmen.
   * Es ist sicher, jede LED-Aktivität zu ignorieren.
2. Schaltfläche Freigeben und 2-3 Sekunden warten
3. Schalten Sie das Gerät erneut ein, indem Sie den Netzschalter 1 Sekunde gedrückt halten.

## <a name="reset-the-device-to-a-factory-clean-state"></a>Zurücksetzen des Geräts auf einen Werks sauberen Zustand

Wenn nach dem Neustart weiterhin Probleme auftreten, können Sie versuchen, den Zustand auf einen Werk sauberen Zustand zurückzusetzen. Wenn Sie Ihr Gerät zurücksetzen, werden alle Ihre persönlichen Daten, Apps und Einstellungen gelöscht. Wenn Sie zurücksetzen, wird nur die neueste installierte Version von Windows Holographic installiert, und Sie müssen alle Initialisierungs Schritte wiederholen (z. b. kalibrieren, mit WiFi verbinden, ein Benutzerkonto erstellen, apps herunterladen usw.).
1. Starten Sie die **Einstellungen** app-> **Update** -> **Reset**
2. Wählen Sie die Option **Gerät zurücksetzen** und das Bestätigungs Dialogfeld aus.
3. Wenn Sie Ihr Gerät zurücksetzen, wird das Gerät neu gestartet und zeigt eine Reihe von drehenden Gängen mit einer Statusanzeige an.
4. Warten Sie ungefähr 30 Minuten, bis dieser Vorgang abgeschlossen ist.
5. Die zurück setzung wird beendet, und das Gerät wird im Standardfenster neu gestartet.

## <a name="perform-a-full-device-recovery"></a>Ausführen einer vollständigen Geräte Wiederherstellung

Wenn Ihr Gerät nach dem Ausführen der oben genannten Optionen **weiterhin** eingefroren ist, nicht reagiert oder Updates oder Software Probleme auftritt, können Sie es mit dem Windows-Geräte Wiederherstellungs Tool wiederherstellen. Die Wiederherstellung Ihres Geräts ähnelt dem Zurücksetzen des Geräts in dem Sinne, dass es den gesamten Benutzer Inhalt auf dem Gerät löscht, einschließlich apps, Spiele, Fotos, Benutzerkonten usw. Sichern Sie nach Möglichkeit alle Informationen, die Sie beibehalten möchten.

So stellen Sie Ihre hololens vollständig wieder her:
1. Trennen Sie alle Telefone und Windows-Geräte vom PC
2. Installieren und starten Sie das [Windows-Geräte Wiederherstellungs Tool](https://support.microsoft.com/help/12379/windows-10-mobile-device-recovery-tool-faq) (wdrt) auf Ihrem PC.
3. Verbinden Sie Ihre hololens mit Ihrem PC, indem Sie das Micro-USB-Kabel verwenden, mit dem Sie
   * Beachten Sie, dass nicht alle USB-Kabel gleich erstellt werden. Auch wenn Sie ein anderes Kabel erfolgreich verwendet haben, macht dieser Flow neue Zustände verfügbar, in denen das Kabel möglicherweise nicht ausgeführt wird. Das, mit dem Ihre hololens geliefert wurden, ist die am besten geeignete Option.
4. Wenn das Tool das Gerät automatisch erkennt, wird eine hololens-Kachel angezeigt. Klicken Sie darauf, und befolgen Sie die Anweisungen, um den Vorgang abzuschließen.

>[!NOTE]
>Wdrt kann Ihr Gerät auf einer älteren Version von Windows Holographic wiederherstellen. Sie müssen möglicherweise Updates nach dem blinken installieren.

Wenn das Tool das Gerät nicht automatisch erkennen kann, versuchen Sie Folgendes:
1. Starten Sie den PC neu, und versuchen Sie es noch mal.
2. Klicken Sie auf die **Schaltfläche mein Gerät wurde nicht erkannt**, wählen Sie **Microsoft hololens**aus, und befolgen Sie die restlichen Anweisungen auf dem Bildschirm.
