---
title: Energie
description: Das Kalibrieren Ihrer IPD (interpupillary Distance) kann die Qualität ihrer visuellen Elemente verbessern. Sowohl hololens als auch Windows Mixed Reality mit immersiven Headsets bieten Möglichkeiten zum Anpassen von IPD.
author: xerxesb85
ms.author: xerxesb
ms.date: 02/24/2019
ms.topic: article
keywords: Kalibrierung, Komfort, visuelle Elemente, Qualität, IPD
ms.openlocfilehash: e86319dadeda02f71427b87980268eaf18942c49
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122090"
---
# <a name="improve-visual-quality-and-comfort"></a>Verbessern der visuellen Qualität und des Komforts
Hololens, hololens 2 und Windows Mixed Reality mit immersiven Headsets bieten verschiedene Möglichkeiten, die Qualität der visuellen Darstellung zu verbessern. 

## <a name="hololens-2"></a>Hololens 2

### <a name="calibration"></a>Energie

Hololens 2 ist darauf ausgelegt, für unsere Kunden die qualitativ hochwertige visuelle Darstellung und den Komfort zu bieten. Die Technologie für die Augen Nachverfolgung wird verwendet, um die Benutzerumgebung zum Anzeigen und interagieren mit der virtuellen Umgebung zu verbessern.  

Auf hololens 2 werden Sie aufgefordert, Ihre visuellen Elemente während der Einrichtung des Geräts zu kalibrieren. Benutzer werden aufgefordert, eine Reihe von Fixierungs Zielen zu überprüfen. Dadurch kann das Gerät das Rendering von holograms an den Benutzer anpassen, um eine präzise positionierte holograms sicherzustellen, eine bequeme 3D-Anzeige und eine verbesserte Anzeigequalität. Alle Anpassungen erfolgen dynamisch, ohne dass eine manuelle Optimierung erforderlich ist. Wenn Sie die Augen als Meilensteine verwenden, wird das Gerät einzeln an jeden Benutzer angepasst, und die visuellen Elemente werden angepasst, wenn sich das Headset leicht in der gesamten Verwendung befindet. Die Nachverfolgung von Augen Positionen wird intern vom System verwendet, und Entwickler müssen nichts tun, um diese Funktion nutzen zu können. Tatsächlich sind diese Informationen für Entwickler nicht verfügbar.
Weitere Informationen zu den Datentypen, die das Augen Verfolgungssystem für Entwickler bereitstellt, finden Sie in den [Überwachungs-APIs](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) .

Bei hololens 2 wird durch das Durchführen der Kalibrierung auch eine genaue Überwachung des Augenblicks für jeden Benutzer sichergestellt. Mit der Blickverfolgung können Anwendungen in Echtzeit verfolgen, wohin der Benutzer schaut. Dies ist die Hauptfunktion, die Entwickler nutzen können, um ein ganz neues Kontext-, Grundlegendes und Interaktionen in der holografischen Benutzer Funktionalität zu ermöglichen.  

Die Kalibrierungsdaten werden lokal auf dem Gerät gespeichert und sind keinen Kontoinformationen zugeordnet. Es gibt keinen Datensatz darüber, wer das Gerät ohne Kalibrierung verwendet hat. Dies bedeutet, dass Benutzer bei der erstmaligen Verwendung des Geräts zur Kalibrierung aufgefordert werden, sowie für Benutzer, die zuvor die Kalibrierung deaktiviert haben, oder wenn die Kalibrierung nicht erfolgreich war. Die Kalibrierungsdaten können immer aus dem Gerät in den **Einstellungen** > **Datenschutz** > **Eye Tracker**gelöscht werden. 

### <a name="calibration-failures"></a>Kalibrierungs Fehler
Die Kalibrierung sollte für die meisten Benutzer funktionieren, aber es gibt Fälle, in denen der Benutzer möglicherweise nicht in der Lage ist, die Kalibrierung erfolgreich durchzusetzen.  
Einige Beispiele für die Kalibrierung von Fehlern sind folgende:
- Der Benutzer hat die kalibrierungsziele während der Kalibrierung nicht betrachtet.
- Nicht ordnungsgemäß positionierter oder nicht ordnungsgemäß positionierter Geräte Hypervisor oder Geräte-Hypervisor 
- Bestimmte Arten von Kontaktlinsen und-Gläsern (farbige Kontaktlinsen, einige Toric-Kontaktlinsen, IR-Blockierungs Gläser, einige hoch verschreibungspflichtige Gläser, Sonnenbrillen usw.)
- Geänderte oder gekratzte Gläser
- Deutlichere Zusammensetzung, einige Wimpern Erweiterungen
- Oksions-und/oder Geräte-Hypervisor (Haare, einige Dicke Brillenrahmen)
- Eye Physiologie, bestimmte Augen Zustände und/oder Augenchirurgie (einige schmale Augen, lange Wimpern, amblyopia, Nystagmus, einige Fälle von LASIK oder andere Eye-Operationen usw.)

Wenn die Kalibrierung nicht erfolgreich ist, versuchen Sie es mit einer der folgenden Korrekturen: 
- Bereinigen des Geräte-Visors
- Reinigen der Brille
- Bewegen Sie Ihren Geräte-Hypervisor auf alle Weise in
- Stellen Sie sicher, dass die Sensoren bzw. Ihre Augen nicht behindern (z. b. Haare). 
- Stellen Sie sicher, dass in Ihrem Raum genügend Licht vorhanden ist, und dass Sie sich nicht unter direkter Sonneneinstrahlung befinden.
- Stellen Sie sicher, dass Sie die Ziele bei der Kalibrierung sorgfältig befolgen.

Wenn Sie alle Richtlinien befolgt haben und die Kalibrierung weiterhin fehlschlägt, können Sie die Kalibrierungs Aufforderung > in**Systemkalibrierung** > für Einstellungen deaktivieren: *"Wenn eine neue Person diese hololens verwendet, muss die automatische* aufzurufende" Eye-Kalibrierung "deaktiviert werden. Beachten Sie, dass dies zu einer schlechteren Qualität und zu Problemen beim Rendern von – Hologramm führen kann.

### <a name="launching-the-calibration-app-from-settings"></a>Starten der Kalibrierungs-App aus den Einstellungen
1. Wechseln Sie zur Seite "Einstellungen" auf den hololens 2.
    * Verwenden Sie die *"Start Geste"* , um das [Startmenü anzuzeigen](navigating-the-windows-mixed-reality-home.md#start-menu). Alternativ dazu können Sie auch einfach *"Gehe zu Start"* sagen.
    * Wenn die **Einstellungen** nicht zum Starten angeheftet sind, wählen Sie **alle apps** aus, um alle apps anzuzeigen.
    * Start **Einstellungen**
2. Navigieren Sie zu > **Systemkalibrierung** > **Eye-Kalibrierung** , und wählen Sie die Option **Eye**


### <a name="calibration-when-sharing-a-devicesession"></a>Kalibrierung bei der Freigabe eines Geräts/einer Sitzung
Hololens 2 können von Personen gemeinsam genutzt werden, ohne dass jede Person die Geräte Einrichtung durchlaufen muss.
Hololens 2 fordert den Benutzer auf, visuelle Elemente zu kalibrieren, wenn das Gerät auf den Kopf gestellt wird, wenn der Benutzer nicht mit dem Gerät vertraut ist. Wenn der Benutzer zuvor die visuellen Elemente auf dem Gerät auf dem Gerät abgestimmt hat, wird die Anzeige nahtlos auf die Qualität abgestimmt, und es wird eine bequeme Anzeige angezeigt, wenn der Benutzer das Gerät auf den Kopf setzt. 


## <a name="hololens-v1"></a>Hololens (v1)
Das Kalibrieren Ihrer IPD (interpupillary Distance) kann die Qualität ihrer visuellen Elemente verbessern.

### <a name="during-setup"></a>Während des Setups

![Bildschirm für IPD-fingerausrichtung im zweiten Schritt](images/ipd-finger-alignment-300px.jpg)<br>

*Bildschirm für IPD-fingerausrichtung im zweiten Schritt*

Bei hololens werden Sie aufgefordert, Ihre visuellen Elemente während des Setups zu kalibrieren. Dadurch kann das Gerät die – Hologramm-Anzeige entsprechend der [interpupillary Distance](https://en.wikipedia.org/wiki/Interpupillary_distance) (IPD) des Benutzers anpassen. Bei einer falschen IPD werden holograms möglicherweise instabil oder in falscher Entfernung angezeigt.

Nachdem Cortana sich selbst eingeführt hat, ist der erste Setup Schritt die Kalibrierung. Es wird empfohlen, dass Sie den Kalibrierungs Schritt in dieser Setup Phase ausführen. Sie können Sie jedoch überspringen, indem Sie darauf warten, dass Sie von Cortana aufgefordert werden, "überspringen", um fortzufahren.

Benutzer werden aufgefordert, Ihren Finger mit einer Reihe von sechs Zielen pro Auge auszurichten. Durch diesen Vorgang legt hololens die richtige IPD für den Benutzer fest. Wenn die Kalibrierung für einen neuen Benutzer aktualisiert oder angepasst werden muss, kann Sie mithilfe der Kalibrierungs-App außerhalb des Setups ausgeführt werden.

### <a name="calibration-app"></a>Kalibrierungs-App

Die Kalibrierung kann jederzeit über die Kalibrierungs-app ausgeführt werden. Die Kalibrierungs-APP wird standardmäßig installiert, und Sie können über das Startmenü oder über die app "Einstellungen" auf Sie zugreifen. Die Kalibrierung wird empfohlen, wenn Sie die Qualität ihrer visuellen Elemente verbessern oder visuelle Elemente für einen neuen Benutzer kalibrieren möchten.

**Starten der APP vom Start**
1. Verwenden [Sie](gestures.md#bloom) die Option zum [Starten des Startmenü](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Wählen **+** Sie diese Option, um alle apps anzuzeigen.
3. Starten Sie die **Kalibrierung**.

![Zugreifen auf die Kalibrierungs-App über die Shell](images/calibration-shell.png)

![Die als livecube nach dem Starten angezeigte Kalibrierungs-App](images/calibration-livecube-200px.png)

**Starten der APP über Einstellungen**
1. Verwenden [Sie](gestures.md#bloom) die Option zum [Starten des Startmenü](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Wählen **+** Sie diese Option aus, um alle apps anzuzeigen, wenn **Einstellungen** nicht zum Starten angeheftet
3. Start **Einstellungen**.
4. Navigieren Sie zu **System** > **Hilfsprogramme** , und wählen Sie dann **Kalibrierung öffnen**aus.

![Starten der Kalibrierungs-App über die app "Einstellungen"](images/calibration-settings-500px.jpg)


## <a name="immersive-headsets"></a>Immersive Headsets

Wenn Sie IPD in Ihrem Headset ändern möchten, öffnen Sie die app "Einstellungen", und navigieren Sie zur **Mixed Reality** > -**Headset-Anzeige** und verschieben Sie das Schieberegler Die Änderungen werden in Echtzeit in Ihrem Headset angezeigt. Wenn Sie Ihr IPD kennen, können Sie es möglicherweise auch direkt über einen Besuch von optomekurzer St eingeben.

Sie können diese Einstellung auch anpassen, indem Sie zu **Einstellungen** > **Mixed Reality** > -**Headset-Anzeige** auf Ihrem PC wechseln.

Wenn Ihr Headset die IPD-Anpassung nicht unterstützt, wird diese Einstellung deaktiviert.

## <a name="see-also"></a>Siehe auch
* [Umgebungsüberlegungen für HoloLens](environment-considerations-for-hololens.md)
