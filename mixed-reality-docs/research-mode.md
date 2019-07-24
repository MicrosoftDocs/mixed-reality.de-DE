---
title: Hololens Research-Modus
description: Mithilfe des Research-Modus auf hololens kann eine Anwendung auf wichtige Geräte Sensordaten Ströme (Tiefe, Umgebungs Überwachung und IR-Reflektivität) zugreifen.
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: Research Mode, CV, RS4, Maschinelles sehen, Forschung, hololens
ms.openlocfilehash: e9a7683f8d582b459185066e74655e8f2b236db4
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829931"
---
# <a name="hololens-research-mode"></a>Hololens Research-Modus

> [!NOTE]
> Diese Funktion wurde als Teil des [Windows 10-Updates vom April 2018](release-notes-april-2018.md) für hololens hinzugefügt und ist in früheren Versionen nicht verfügbar.

Der Forschungs Modus ist eine neue Funktion von hololens, die Anwendungs Zugriff auf die Schlüssel Sensoren auf dem Gerät bietet. Dazu gehören:
- Die vier Umgebungs Überwachungskameras, die vom System für das Zuordnen von Zuordnungen und das Head-Tracking verwendet werden.
- Zwei Versionen der tiefenkamera Daten – eine für die nahe greifende Erfassung mit hoher Frequenz (30 fps), häufig in der Hand Nachverfolgung verwendet, und die andere für die untere Frequenz (1 fps), bei der es sich um eine weitgehende Erfassung handelt, die zurzeit von der räumlichen Zuordnung verwendet wird,
- Zwei Versionen eines IR-Reflektivität-Streams, die von den hololens zur computetiefe verwendet werden, aber von der eigenen richtigen Bedeutung sind, da diese Bilder aus den hololens beleuchtet werden und von Umgebungslicht nicht beeinträchtigt werden.

![Screenshot der Recherche Modus-App](images/sensor-stream-viewer.jpg)<br>
*Eine gemischte Realität-Erfassung einer Testanwendung, die die acht im Research-Modus verfügbaren Sensordaten Ströme anzeigt*

## <a name="device-support"></a>Unterstützung von Geräten

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Funktion</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Forschungs Modus</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-using-research-mode"></a>Vor der Verwendung des Research-Modus

Der Forschungs Modus ist gut benannt: er ist für akademische und Industrieexperten gedacht, die neue Ideen in den Feldern von Maschinelles Sehen und Robotik ausprobieren.  Der Forschungs Modus ist nicht für Anwendungen gedacht, die über ein Unternehmen bereitgestellt oder in der Microsoft Store bereitgestellt werden. Der Grund hierfür ist, dass der Research-Modus die Sicherheit Ihres Geräts verringert und eine deutlich höhere Akkuleistung als der normale Betrieb beansprucht. Microsoft ist nicht verpflichtet, diesen Modus auf zukünftigen Geräten zu unterstützen. Daher empfiehlt es sich, diese zum entwickeln und Testen neuer Ideen zu verwenden. Allerdings sind Sie nicht in der Lage, Anwendungen, die den Research-Modus verwenden, umfassend bereitzustellen oder sicherzustellen, dass Sie weiterhin auf zukünftiger Hardware funktionieren.

## <a name="enabling-research-mode"></a>Aktivieren des Research-Modus

Der Forschungs Modus ist ein unter Modus des Entwicklermodus. Sie müssen zunächst den Entwicklermodus in der App "Einstellungen" aktivieren (**Einstellungen > Update & Sicherheits > für Entwickler**):

1. Legen Sie "Entwickler Features verwenden" auf **on** fest.
2. Legen **Sie "** Geräte Portal aktivieren" auf ein fest.

Navigieren Sie dann mithilfe eines Webbrowsers, der mit dem gleichen WLAN verbunden ist wie Ihre hololens, zur IP-Adresse Ihres hololens (über **Einstellungen > Netzwerk & Internet > Wi-Fi-> Hardware Eigenschaften**). Dies ist das [Geräte Portal](using-the-windows-device-portal.md), und im Abschnitt "System" des Portals finden Sie eine Seite "Research Mode":

![Registerkarte "Forschungs Modus" des hololens-Geräte Portals](images/ResearchModeDevPortal.png)<br>
*Forschungs Modus im hololens-Geräte Portal*

Nachdem Sie **Zugriff auf Sensordaten Ströme zulassen**ausgewählt haben, müssen Sie hololens neu starten. Dies können Sie über das Geräte Portal unter dem Menü Element "Power" am oberen Rand der Seite tun.

Nachdem das Gerät neu gestartet wurde, sollten Anwendungen, die über das Geräte Portal geladen wurden, auf Datenströme im Forschungs Modus zugreifen können.

## <a name="using-sensor-data-in-your-apps"></a>Verwenden von Sensordaten in ihren apps

Anwendungen können auf Sensordaten Ströme zugreifen, indem Sie [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) Datenströme genau auf die gleiche Weise öffnen, wie Sie auf den Photo/Video-Kamera-Stream zugreifen. 

Alle APIs, die für die hololens-Entwicklung funktionieren, sind auch im Research-Modus verfügbar. Insbesondere kann die Anwendung genau wissen, wo sich hololens bei jeder Sensor Frame-Erfassungs Zeit in einem 6DOF-Raum befindet.

Beispielanwendungen, die zeigen, wie Sie auf die verschiedenen Datenstreams im Forschungs Modus zugreifen, wie Sie die systeminternen und extrinsics verwenden und Datenströme aufzeichnen, sind im [GitHub-Repository hololensforcv](https://github.com/Microsoft/HoloLensForCV)verfügbar.

## <a name="known-issues"></a>Bekannte Probleme

Weitere Informationen finden Sie im Repository "hololensforcv" unter [Problem](https://github.com/Microsoft/HololensForCV/issues) Verfolgung.

## <a name="see-also"></a>Siehe auch

* [Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [Hololensforcv GitHub-Repository](https://github.com/Microsoft/HoloLensForCV)
* [Verwenden des Windows-Geräteportals](using-the-windows-device-portal.md)
