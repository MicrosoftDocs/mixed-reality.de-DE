---
title: Anmerkungen zu dieser Version-Mai 2020
description: Windows Mixed Reality-Versions Hinweise für das Windows 10-Update vom Mai 2020 (auch bekannt als 2004).
author: tmlyon
ms.author: tmlyon
ms.date: 05/27/2020
ms.topic: article
keywords: Anmerkungen zu dieser Version, Version, Windows 10, Build, 20h1, OS, 2020, 2004
ms.openlocfilehash: ec92259662109001c02cf631eb6b9948d61ba9de
ms.sourcegitcommit: b0d15083ec1095e08c9d776e5bae66b4449383bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2020
ms.locfileid: "84124137"
---
# <a name="release-notes---may-2020"></a>Anmerkungen zu dieser Version-Mai 2020

Das **Windows 10-Update von Mai 2020 (V2004)** enthält neue Features für Windows Mixed Reality (VR)-Headsets, wie z. b. die Möglichkeit zum Starten von Win32-Anwendungen in der Mixed Reality-Startseite. Hololens (1st Gen) ist eine langfristige Wartung (LTS), wobei Wartungsupdates monatlich veröffentlicht werden müssen.

Zum Aktualisieren auf die neueste Version auf dem PC für Windows Mixed Reality immersive (VR)-Headsets öffnen Sie die app " **Einstellungen** ", navigieren Sie zu **Update & Security**, und wählen Sie dann die Schaltfläche **nach Updates suchen aus** . Auf einem Windows 10-PC können Sie das **Windows 10-Update von Mai 2020** auch manuell mithilfe des [Windows Media-Erstellungs Tools](https://www.microsoft.com/software-download/windows10)installieren.

**Neueste Version für Desktop**: Windows 10 V2004 (10.0.19041.264)

## <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Updates für Windows Mixed Reality-immersive Headsets

### <a name="introducing-the-new-microsoft-edge"></a>Einführung in den neuen Microsoft Edge
Wie [bereits angekündigt](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge), haben wir Aktualisierungen vorgenommen, um die Unterstützung für die Verwendung des neuen Microsoft Edge-Browsers in Windows Mixed Reality zu verbessern. Der neue Microsoft Edge übernimmt das Chromium-Open-Source-Projekt, um eine bessere webkompatibilität für Kunden und weniger Fragmentierung des Internets für alle Webentwickler zu erzielen. Es unterstützt auch webxr, den neuen Standard zum Erstellen von immersiven Webumgebungen für VR-Headsets anstelle von webvr.

### <a name="improved-settings-for-wmr"></a>Verbesserte Einstellungen für WMR
Dank Ihres Feedbacks haben wir die Einstellungen auf der Seite für die Headset-Anzeige hinzugefügt und verdeutlicht:

* Die **visuelle Qualität meiner zu Hause** ändernden Einstellungen wirkt sich nur auf die gemischte Umgebung in der Praxis aus ("Klippe House" und "SkyLoft"):

* **Anpassung der Detail-und Qualitäts Qualität in der Mixed Reality-Startseite** : Hierdurch werden einige der in der Startseite verwendeten renderingauswirkungen geändert. Insbesondere wird die visuelle Qualität unterschiedlicher Materialien (Holz, konkrete usw.) skaliert, wenn Sie diese Einstellung von "niedrig" in "hoch" ändern.

* **Ändern der Auflösung von App** -Fenstern: Standardmäßig werden die meisten 2D-Fenster, die auf der Startseite gestartet werden, mit der Auflösung 720p gestartet. Obwohl Sie die Größe der Dateien & vertikal manuell ändern können, können Sie Sie auch dazu verwenden, dass Sie stattdessen bei 1080p gestartet werden. Zuvor war diese Option in der visuellen Qualität als sehr hohe (Beta-) Option verfügbar. Wir haben ihn entsprechend als separate Einstellung aufgeteilt.

* **Optionen** für die Verwendung: Diese Optionen passen die gemischte Realität an, um die Last auf 90 Systemen zu reduzieren Sie können diese zusätzlichen Einstellungen explizit aktivieren bzw. deaktivieren, oder Sie können die Option Windows entscheiden lassen und unsere Heuristik weiterhin entscheiden, wann diese ein-und ausgeschaltet werden soll.

* **Lösung** : Wenn Sie über ein hochauflösende Headset wie den HP-Reverb verfügen, unterstützen wir die Ausführung bei der systemeigenen Auflösung oder bei einer reduzierten Auflösung aus Leistungsgründen. Frühere Headsets, wie z. b. Samsung Odyssee und Odyssee, unterstützen nur eine einzige Lösung, sodass Sie diese Einstellung auf diesen Headsets nicht ändern können.

* **Framerate** : Sie können nun die Framerate der Headset-Anzeige manuell festlegen oder die Heuristik von Windows verwenden, um zu bestimmen, ob 60 Hz oder 90 Hz besser geeignet ist.

* **Kalibrierung** : wie zuvor können Sie Ihre IPD (interpupilläre Entfernung) anpassen, wenn Sie von Ihrem Headset unterstützt wird.

* **Eingabe wechseln** : Schalten Sie das Verhalten des Eingabefokus Schaltens (Win + Y) so um, dass es automatisch (basierend auf dem Anwesenheits Sensor-Feedback) oder manuell erfolgt.

### <a name="new-cortana-app"></a>Neue Cortana-App
Dieses Update für Windows enthält die neueste Version der Cortana-APP, die zurzeit nur auf Englisch ist und einige gemischte, gemischte Befehle wie "Bild nehmen" und "Video nehmen" nicht mehr unterstützt. Sie können die neue Cortana weiterhin verwenden, um apps zu starten, und Sie unterstützt auch neue produktivitätsorientierte Befehle wie "Wann ist meine nächste Besprechung?". oder "Senden Sie eine e-Mail an <name> , dass ich später ausführe."

#### <a name="please-help-us-improve"></a>Helfen Sie uns bei der Verbesserung!
Wir werden kontinuierlich darauf achten, die Kompatibilität zu verbessern.  Wenn Sie feststellen, dass sich Ihre bevorzugte klassische Win32-Anwendung in Windows Mixed Reality nicht korrekt verhält, senden Sie uns Feedback über unseren [Feedback-Hub](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub).

## <a name="prior-release-notes"></a>Vorherige Anmerkungen zu dieser Version

* [Anmerkungen zu dieser Version-Mai 2019](release-notes-may-2019.md)
* [Versionshinweise – Oktober 2018](release-notes-october-2018.md)
* [Anmerkungen zu dieser Version-April 2018](release-notes-april-2018.md)
* [Versionshinweise – Oktober 2017](release-notes-october-2017.md)
* [Versionshinweise – August 2016](release-notes-august-2016.md)
* [Versionshinweise – Mai 2016](release-notes-may-2016.md)
* [Versionshinweise – März 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Siehe auch
* [Immersive Headset-Unterstützung (externer Link)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Hololens-Unterstützung (externer Link)](https://support.microsoft.com/products/hololens)
* [Installieren der Tools](install-the-tools.md)
* [Geben Sie uns Feedback](give-us-feedback.md)
