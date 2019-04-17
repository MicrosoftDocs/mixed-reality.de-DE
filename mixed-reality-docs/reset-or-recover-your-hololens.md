---
title: Zurücksetzen Sie oder Wiederherstellen Sie Ihrer HoloLens
description: Die grundlegenden und erweiterten Anweisungen für das neu zu starten, oder das Zurücksetzen Ihrer HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Exemplarische Vorgehensweise, neu starten, zurücksetzen, wiederherstellen "," Kaltstart "," Warmstart "," Energiezyklus, HoloLens, Herunterfahren
ms.openlocfilehash: abf71a5f122b1c6f800bf970f51da11a34be956b
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594177"
---
# <a name="reset-or-recover-your-hololens"></a>Zurücksetzen Sie oder Wiederherstellen Sie Ihrer HoloLens

Wenn Sie Probleme mit Ihrem HoloLens auftreten, möglicherweise einen Neustart möchten, zurückgesetzt oder flash auch erneut mit der Wiederherstellung des Geräts. Dieses Dokument führt Sie durch die empfohlenen Schritte nacheinander.

## <a name="perform-a-device-reboot"></a>Führen Sie einen Neustart des Geräts

Wenn Ihre HoloLens Probleme oder nicht reagiert, versuchen Sie zunächst es über eine der Neustart der folgenden Methoden.

### <a name="perform-a-safe-reboot-via-cortana"></a>Führen Sie einen sicheren Neustart über Cortana

Die sicherste Möglichkeit, die HoloLens Neustart erfolgt über Cortana. Dies ist eine hervorragende ersten Schritt im Allgemeinen auf, wenn ein Problem mit HoloLens:
1. Legen Sie auf Ihrem Gerät
2. Stellen Sie sicher, dass er eingeschaltet ist, ein Benutzer angemeldet ist und ein Kennwort zum Entsperren des Geräts nicht wartet.
3. Z. B. "Hey Cortana, neu starten" oder "Hey Cortana, neu starten."
4. Wenn sie bestätigt fragt sie Sie zur Bestätigung. Warten Sie einen zweiten für einen Sound wiedergegeben wird, nachdem er abgeschlossen ist ihre Frage angezeigt, dass sie Ihnen überwacht wird, und nennen Sie dann auf "Ja".
5. Das Gerät wird jetzt ein Neustart/Neustarten.

### <a name="perform-a-safe-reboot-via-windows-device-portal"></a>Führen Sie einen sicheren Neustart über Windows Device Portal

Wenn es sich bei den oben genannten nicht funktioniert, können Sie versuchen, zum Neustarten des Geräts über [Windows Device Portal](using-the-windows-device-portal.md). In der oberen rechten Ecke besteht eine Option zum Neustarten/Herunterfahren des Geräts.

### <a name="perform-a-safe-reboot-via-the-power-button"></a>Führen Sie einen sicheren Neustart über die Schaltfläche "Power"

Wenn Sie weiterhin Ihr Gerät neu gestartet werden können, können Sie versuchen, einen Neustart über den Netzschalter ausgeben:
1. Drücken Sie und halten Sie den Netzschalter betätigen, 5 Sekunden
   1. Nach 1 Sekunde sehen Sie, alle 5 LEDs beleuchten, klicken Sie dann langsam von rechts nach links deaktivieren
   2. Nach 5 Sekunden werden aller LEDs deaktivieren, angezeigt, dass der Befehl zum Herunterfahren erfolgreich ausgegeben wurde
   3. Beachten Sie, dass es ist wichtig, beenden, drücken die Schaltfläche mit den unmittelbar auf Alles, was die LEDs deaktiviert haben
2. Warten Sie eine Minute für das Herunterfahren ordnungsgemäß erfolgreich ausgeführt werden kann. Beachten Sie, dass das Herunterfahren noch im Gang sein kann, selbst wenn zeigt die deaktiviert sind.
3. Schalten Sie das Gerät erneut durch Gedrückthalten des Netzschalters 1 Sekunde

### <a name="perform-an-unsafe-forced-reboot"></a>Führen Sie einen unsichere erzwungen Neustart

Wenn keine der oben genannten Methoden erfolgreich Ihre Geräte neu starten können, können Sie einen Neustart erzwingen. Beachten Sie, dass diese Methode entspricht dem Abrufen des Akkus aus dem HoloLens und daher einen gefährlichen Vorgang, der Ihr Gerät in einen fehlerhaften Status versetzen kann. 

>[!WARNING]
>Dies ist eine Methode, schädigende und sollte nur verwendet werden, falls keiner der oben genannten Methoden funktioniert.

1. Drücken Sie und halten Sie den Netzschalter auf mindestens 10 Sekunden
   * Es ist in Ordnung, die länger als 10 Sekunden die Schaltfläche "-" enthalten soll.
   * Es ist sicherer, ignorieren alle Aktivitäten der LED
2. Lassen Sie die los, und warten Sie, 2 und 3 Sekunden
3. Schalten Sie das Gerät erneut durch Gedrückthalten des Netzschalters 1 Sekunde

## <a name="reset-the-device-to-a-factory-clean-state"></a>Zurücksetzen des Geräts in einem Zustand bereinigen

Wenn Ihre HoloLens weiterhin Probleme auftreten wird nach dem Neustart, können Sie versuchen, in einem sauberen Zustand zurücksetzen. Wenn Sie Ihr Gerät zurücksetzen, werden alle Ihre persönlichen Daten, apps und Einstellungen gelöscht. Zurücksetzen, wird nur die neueste installierte Version von Windows Holographic installieren und müssen alle Initialisierungsschritte wiederholen (kalibrieren, eine Verbindung mit WiFi herstellen, ein Benutzerkonto erstellen, Herunterladen von apps usw....).
1. Starten Sie den **Einstellungen** app -> **Update** -> **zurücksetzen**
2. Wählen Sie die **zurückgesetzte Gerät** aus, und Lesen Sie das Dialogfeld "Bestätigung"
3. Wenn Sie, zum Zurücksetzen Ihres Geräts zustimmen, wird das Gerät neu gestartet und ein Satz von rotierende Zahnrädern, für eine Statusanzeige angezeigt
4. Warten Sie ungefähr 30 Minuten, bis dieser Prozess abgeschlossen
5. Das Zurücksetzen abgeschlossen und das Gerät wird neu gestartet, in der Out-of der Box-experience

## <a name="perform-a-full-device-recovery"></a>Führen Sie eine Wiederherstellung des gesamten Geräts

Wenn Sie nach dem Ausführen der oben genannten Optionen an, Ihr Gerät ist **weiterhin** fixiert, nicht mehr reagiert, oder treten Probleme mit Update oder einen Softwareupdatepunkt können Sie mithilfe der Windows Device Recovery Tool wiederherstellen. Wiederherstellen Ihres Geräts ähnelt der zurücksetzen in dem Sinne, dass alle Benutzerinhalte auf dem Gerät, einschließlich apps, Spiele, Fotos, Benutzerkonten und gelöscht werden. Sichern Sie wenn möglich, alle Informationen, die Sie beibehalten möchten.

Ihre HoloLens vollständig wiederherstellen zu können:
1. Trennen Sie alle Smartphones und Windows-Geräte von Ihrem PC
2. Installieren und starten Sie den [Windows Device Recovery Tool](https://support.microsoft.com/help/12379/windows-10-mobile-device-recovery-tool-faq) (WDRT) auf Ihrem PC
3. Verbinden Sie Ihre HoloLens auf Ihren PC mit dem Micro-USB-Kabel, die im Lieferumfang enthaltene
   * Beachten Sie, dass nicht alle USB-Kabel gleich sind. Auch wenn Sie ein weiteres Kabel erfolgreich verwendet haben, wird dieser Flow neue Status verfügbar machen, in dem das Kabel nicht ebenfalls ausgeführt werden kann. Der Lieferumfang Ihrer HoloLens ist die beste und die meisten gut getestete-option
4. Wenn das Tool automatisch Ihr Gerät erkennt wird eine HoloLens-Kachel angezeigt. Klicken Sie darauf, und befolgen Sie die Anweisungen, um den Vorgang abzuschließen

>[!NOTE]
>WDRT kann Ihr Gerät auf eine ältere Version von Windows Holographic wiederherzustellen. Sie müssen möglicherweise Updates nach blinken installieren

Wenn das Tool, Ihr Gerät automatisch zu erkennen ist, versuchen Sie Folgendes ein:
1. Starten Sie Ihren PC, und versuchen Sie es erneut (Dadurch werden die meisten Probleme behoben) neu.
2. Klicken Sie auf die **mein Gerät wurde nicht erkannt. Schaltfläche**, wählen Sie **Microsoft HoloLens**, und befolgen Sie die restlichen Anweisungen auf dem Bildschirm
