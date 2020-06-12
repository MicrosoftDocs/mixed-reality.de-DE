---
title: Hololens Research-Modus
description: Mithilfe des Research-Modus auf hololens kann eine Anwendung auf wichtige Geräte Sensordaten Ströme (Tiefe, Umgebungs Überwachung und IR-Reflektivität) zugreifen.
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
keywords: Research Mode, CV, RS4, Maschinelles sehen, Forschung, hololens, hololens 2
ms.openlocfilehash: 62b82e3a36452d4b104bf04999e556ec19d2a5e3
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720396"
---
# <a name="hololens-research-mode"></a>HoloLens-Forschungsmodus

## <a name="overview"></a>Übersicht

Der Forschungs Modus wurde in den ersten hololens der Generation eingeführt, um den Zugriff auf die Schlüssel Sensoren auf dem Gerät zu erhalten, insbesondere für Forschungsanwendungen, die nicht für die Bereitstellung vorgesehen sind. Sie können jetzt Daten aus den folgenden Eingaben sammeln:

* **Sichtbare Umgebungs Überwachungskameras** , die vom System für die Kopf-und Zuordnungs Bildung verwendet werden.
* **Tiefe Kamera** – wird in zwei Modi betrieben:  
    + Short-Throw, High Frequency (30 fps) fast-Tiefe-Erkennung für die [Hand Verfolgung](interaction-fundamentals.md)
    + Lange throw-, Low-Frequency (1-5 fps)-Erkennung, die von der [räumlichen Zuordnung](spatial-mapping.md) verwendet wird
* **Zwei Versionen des IR-Reflektivität-Streams** : werden von den hololens zum Berechnen der Tiefe verwendet. Diese Bilder werden von Infrarot beleuchtet und sind von der Sichtbarkeit sichtbar.

Wenn Sie ein hololens 2 verwenden, können Sie auch auf die folgenden Eingaben zugreifen:

* **Beschleunigungsmesser** – wird vom System verwendet, um die lineare Beschleunigung entlang der X-, Y-und Z-Achse und der Schweregrad zu ermitteln.
* **Gyro** – wird vom System verwendet, um Drehungen zu bestimmen.
* **Magnetometer** – wird vom System zum Schätzen der absoluten Ausrichtung verwendet.

![Screenshot der Recherche Modus-App](images/sensor-stream-viewer.jpg)<br>
*Eine gemischte Realität-Erfassung einer Testanwendung, die die acht im Research-Modus verfügbaren Sensordaten Ströme anzeigt*

> [!NOTE]
> Die Research Mode-Funktion wurde als Teil des [Windows 10-Updates vom April 2018](release-notes-april-2018.md) für hololens hinzugefügt und ist in früheren Versionen nicht verfügbar.

## <a name="usage"></a>Verwendung

Der Forschungs Modus wurde für akademische und Industrieexperten entwickelt, die neue Ideen in den Feldern Maschinelles Sehen und Robotik kennenlernen.  Sie ist nicht für Anwendungen gedacht, die in Unternehmensumgebungen bereitgestellt werden oder über die Microsoft Store oder andere Vertriebskanäle verfügbar sind.

Außerdem bietet Microsoft keine Garantie dafür, dass der Forschungs Modus oder die entsprechende Funktionalität bei zukünftigen Hardware-oder Betriebssystemupdates unterstützt wird. Dies sollte jedoch nicht daran hindern, ihn zum entwickeln und Testen neuer Ideen zu verwenden.

## <a name="security-and-performance"></a>Sicherheit und Leistung

Beachten Sie, dass die Aktivierung des Research-Modus mehr Akkuleistung als die Verwendung der hololens 2 unter normalen Bedingungen beansprucht. Dies gilt auch dann, wenn die Anwendung, die die Research Mode-Features verwendet, nicht ausgeführt wird.  Wenn Sie diesen Modus aktivieren, kann die Gesamtsicherheit Ihres Geräts auch gesenkt werden, da Anwendungen möglicherweise Sensordaten missbrauchen.  Weitere Informationen zur Gerätesicherheit finden Sie in den häufig gestellten Fragen zur [hololens-Sicherheit](https://docs.microsoft.com/hololens/hololens-faq-security).  


## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    <!-- <col width="33%" /> -->
    </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>Hololens 1. Gen</strong></a></td>
        <!-- <td><a href="hololens2-hardware.md"><strong>HoloLens 2</strong></a></td> -->
    </tr>
     <tr>
        <td>Kopf Verfolgungs Kameras</td>
        <td>✔️</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>Tiefe & IR-Kamera</td>
        <td>✔️</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>Beschleunigungsmesser</td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>Gyroskop</td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>Magnetometer</td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
</table>

> [!IMPORTANT]
> Die Unterstützung für den Research-Modus für hololens 2 wird voraussichtlich in der öffentlichen Vorschauversion im Juli 2020 verfügbar sein und umfasst alle oben aufgeführten Features. Weitere Informationen finden Sie hier. 

## <a name="enabling-research-mode"></a>Aktivieren des Research-Modus

Der Forschungs Modus ist eine Erweiterung des Entwicklermodus. Bevor Sie beginnen, müssen die Entwickler Funktionen des Geräts für den Zugriff auf die Einstellungen für den Research-Modus aktiviert werden: 

* Öffnen Sie das **Startmenü > Einstellungen** , und wählen Sie **Updates**aus.
* Wählen Sie **für Entwickler aus** , und aktivieren Sie **Entwicklermodus**.
* Scrollen Sie nach unten, und aktivieren Sie das **Geräte Portal**.

Nachdem die Entwickler Features aktiviert wurden, stellen Sie eine [Verbindung mit dem Geräte Portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) her, um die Funktionen des Research-Modus zu aktivieren.

Auf *hololens 1. Gen*:

* Wechseln Sie im **Geräte Portal**zum **System > Research-Modus** .
* Wählen Sie **Zugriff auf Sensordaten Strom zulassen**aus.
* Starten Sie das Gerät über das **Power** -Menü Element oben auf der Seite neu.

Nachdem Sie das Gerät neu gestartet haben, können die Anwendungen, die über das **Geräte Portal** geladen werden, auf Datenströme im Forschungs Modus zugreifen.

![Registerkarte "Forschungs Modus" des hololens-Geräte Portals](images/ResearchModeDevPortal.png)<br>
*Fenster "Forschungs Modus" im hololens-Geräte Portal*

## <a name="using-sensor-data-in-your-apps"></a>Verwenden von Sensordaten in ihren apps

*Hololens 1. Gen*

Anwendungen können auf die Sensordaten Strom Daten auf die gleiche Weise zugreifen wie auf Foto-und Videokamera-Streams über [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197). 

Alle APIs, die für die hololens-Entwicklung funktionieren, sind auch im Research-Modus verfügbar. Insbesondere weiß die Anwendung genau, wo sich hololens bei jeder Sensor Frame-Erfassungs Zeit in einem 6DOF-Raum befindet.

Beispielanwendungen zum Zugreifen auf die verschiedenen Datenströme im Forschungs Modus, zum Verwenden der systeminternen Funktionen [und der extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)und zum Aufzeichnen von Streams im GitHub-Repository-Repository [hololensforcv](https://github.com/Microsoft/HoloLensForCV) .

 > [!NOTE]
 > Zu diesem Zeitpunkt funktioniert das hololensforcv-Beispiel nicht auf hololens 2.

## <a name="known-issues"></a>Bekannte Probleme

Sie können den [Issue Tracker](https://github.com/Microsoft/HololensForCV/issues) im hololensforcv-Repository verwenden, um bekannte Probleme zu verfolgen.

## <a name="see-also"></a>Siehe auch

* [Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [Hololensforcv GitHub-Repository](https://github.com/Microsoft/HoloLensForCV)
* [Verwenden des Windows-Geräteportals](using-the-windows-device-portal.md)
