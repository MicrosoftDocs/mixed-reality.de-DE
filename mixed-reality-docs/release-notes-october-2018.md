---
title: Anmerkungen zu dieser Version-Oktober 2018
description: Hololens und Windows Mixed Reality-Versions Hinweise für das Windows 10-Update vom Oktober 2018 (auch bekannt als RS5).
author: mattzmsft
ms.author: mazeller
ms.date: 10/02/2018
ms.topic: article
keywords: Anmerkungen zu dieser Version, Version, Windows 10, Build, RS5, Betriebssystem
ms.openlocfilehash: 794050910be40e7f98d0a1f67c2e1cf6963305dd
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524259"
---
# <a name="release-notes---october-2018"></a>Anmerkungen zu dieser Version-Oktober 2018

Das **[Windows 10-Update vom Oktober 2018](https://blogs.windows.com/windowsexperience/2018/10/02/find-out-whats-new-in-windows-and-office-in-october/)** (auch bekannt als RS5) umfasst neue Features für hololens und Windows Mixed Reality-immersive Headsets, die mit PCs verbunden sind. 

Zum Aktualisieren auf die neueste Version auf hololens oder PC (für Windows Mixed Reality immersive (VR)-Headsets) öffnen Sie die app " **Einstellungen** ", navigieren Sie zu **Update & Sicherheit**, und wählen Sie dann die Schaltfläche **nach Updates suchen aus** . Auf einem Windows 10-PC können Sie das Windows 10-Update vom Oktober 2018 auch manuell mithilfe des [Windows Media-Erstellungs Tools](https://www.microsoft.com/software-download/windows10)installieren.

**Neueste Version für Desktop:** Windows 10-Update vom Oktober 2018 (**10.0.17763.107**)<br>
**Neueste Version für hololens:** Windows 10-Update vom Oktober 2018 (**10.0.17763.134**)<br>

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Neue Features für Windows Mixed Reality-immersive Headsets

Das Windows 10-Update vom Oktober 2018 umfasst viele Verbesserungen für die Verwendung von Windows Mixed Reality-(VR)-Headsets mit Ihrem Desktop-PC.

### <a name="for-everyone"></a>Für alle

* **Mixed Reality-Taschenlampe** : Öffnen Sie ein Portal in der realen Welt, um Ihre Tastatur zu finden, sehen Sie sich an, oder sehen Sie sich Ihre Umgebung an, ohne Ihr Headset zu entfernen! Sie können Mixed Reality-Taschen Taschen über das Startmenü aktivieren, indem Sie auf dem Motion-Controller auf Windows + STRG drücken, oder indem Sie "Taschenlampe ein/aus" aufrufen. Zeigen Sie Ihren Controller in der Richtung an, die Sie sehen möchten, wie z. b. die Verwendung einer Taschenlampe in der dunklen.

    ![Mixed Reality-Taschenlampe](images/mr-flashlight.png)

* **Neue apps und Möglichkeiten zum Starten von Inhalten in der Mixed Reality-Startseite**
    * Wenn Sie [Windows Mixed Reality für steamvr](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)verwenden, werden Ihre steamvr-Titel nun im Startmenü angezeigt, und die App-Launcher können jeweils in der Mixed Reality-Startseite platziert werden.
    
        ![Steamvr-App-Launcher](images/steamvr-launchers.png)
        
    * Neue *360-Videos* -App zum Ermitteln einer regelmäßig zusammengestellten Auswahl von 360-Grad-Videos.
    * Neue *webvr Showcase* -App zum Ermitteln einer regelmäßig zusammengestellten Auswahl von webvr-Erfahrungen.
    * Erstmalige Windows Mixed Reality-Kunden wechseln zum ersten Mal in das Klippe-Haus und finden es für einige unserer bevorzugten, immersiven apps und Spiele aus der Microsoft Store.
    * Microsoft Edge Windows enthält jetzt eine *Freigabe* Schaltfläche.
* **Menü "schnelle Aktionen** ": innerhalb einer immersiven Mixed Reality-App können Sie auf die Windows-Schaltfläche klicken, um auf ein neues Menü für schnelle Aktionen zuzugreifen, mit einfachem Zugriff auf das Menü " *steamvr*", *Foto-/Videoerfassung*, *Taschenlampe*und *Startseite*.
* **Unterstützung für Rucksack-PCs** : Windows Mixed Reality immersive (VR)-Headsets werden auf Rucksack-PCs ausgeführt, ohne dass ein Anzeige Emulator erforderlich ist, nachdem Setup abgeschlossen wurde.
* **Neue Audiofeatures** : Sie können jetzt die Audiodaten von Windows Mixed Reality mit dem audiowagen (oder dem Kopfhörer) in Ihrem Headset *und* einem Audiogerät, das mit Ihrem PC verbunden ist (wie externe Referenten), spiegeln. Wir haben auch einen visuellen Indikator für die Volumeebene in der Anzeige Ihres Headsets hinzugefügt.
* **Weitere Verbesserungen**
    * Updates des gemischten Reality-Portals werden nun über die Microsoft Store bereitgestellt, sodass schnellere Updates zwischen größeren Windows-Releases ermöglicht werden. Beachten Sie, dass dies nur für die Desktop-App gilt und das Windows Mixed Reality-Headset-Verhalten weiterhin mit dem Betriebssystem aktualisiert wird. 
    * Wenn die Headsets in den Standbymodus wechseln, werden Windows Mixed Reality-apps angehalten und nicht beendet (bis das gemischte Reality-Portal geschlossen ist).
    
### <a name="for-developers"></a>Für Entwickler

* **[QR-Code](qr-code-tracking.md)** -Nachverfolgung: Aktivieren Sie die Überwachung von QR-Code in ihrer Mixed Reality-APP, sodass Windows Mixed Reality-(VR)-Headsets nach QR-Codes suchen und diese an interessierte apps zurückgeben können.
* **Hardware-DRM-Unterstützung für immersive apps** : Entwickler können jetzt durch Hardware geschützte backpuffertexturen anfordern, wenn Sie von der Anzeige Hardware unterstützt werden, sodass Anwendungen Hardware geschützte Inhalte aus Quellen wie PlayReady verwenden können.
* **[Integrieren Sie die Benutzeroberfläche für die Erfassung gemischter Erkenntnisse in immersive apps](mixed-reality-capture-for-developers.md#integrating-mrc-functionality-from-within-your-app)** : Entwickler können die Transformation für gemischtes umsetzen mithilfe der integrierten Windows- [Kamera Erfassung](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) mit nur wenigen Codezeilen in Ihre apps integrieren.

## <a name="new-features-for-hololens"></a>Neue Features für hololens

Das Windows 10-Update vom Oktober 2018 ist öffentlich für alle hololens-Kunden verfügbar und umfasst eine Reihe von Verbesserungen, wie z. b.:

### <a name="for-everyone"></a>Für alle

* **Menü "schnelle Aktionen** ": innerhalb einer immersiven Mixed Reality-App können Sie auf die Windows-Schaltfläche klicken, um auf ein neues Menü für schnelle Aktionen zuzugreifen    *, und*stellen Sie eine *Verbindung*her.
* **Starten/Anhalten der Video Erfassung über das Menü "Start" oder "schnelle Aktionen** ": Wenn Sie die Videoaufzeichnung im Startmenü oder im Menü "schnelle Aktionen" starten, können Sie die Aufzeichnung von der gleichen Stelle aus anhalten. (Vergessen Sie nicht, Sie können dies immer auch mit Sprachbefehlen tun.)
* **Projekt auf ein miracast-fähiges Gerät** : projizieren Sie Ihren hololens-Inhalt auf ein nahe gelegenes Surface-Gerät oder TV/Monitor, wenn Sie eine miracast-aktivierte Anzeige oder einen Adapter verwenden.
* **Neue Benachrichtigungen** : Sie können Benachrichtigungen auf hololens anzeigen und darauf reagieren, wie Sie es auch auf einem PC tun.  
* **Nützliche Überlagerungen in immersiven Mixed Reality-apps** : Sie sehen jetzt Überlagerungen wie Tastatur, Dialoge, Dateiauswahl usw., wenn Sie immersive Mixed Reality-Apps verwenden.
* **Visueller Indikator für volumeänderung** : Wenn Sie die Schaltflächen "nach oben" und "nach unten" in den hololens verwenden, sehen Sie einen visuellen Indikator der Volumeebene im Headset.
* **Neue visuelle Elemente für den Geräte Start** : ein Lade Indikator wurde während des Startvorgangs hinzugefügt, um ein visuelles Feedback zu erhalten, das vom System geladen wird.
* **Nahe gelegene Freigabe** : die gemeinsame Nutzung von Windows ermöglicht es Ihnen, eine Erfassung mit einem Windows-Gerät in der Nähe zu teilen.  
* **Freigabe von Microsoft Edge** : Microsoft Edge enthält jetzt eine *Freigabe* Schaltfläche. 

### <a name="for-developers"></a>Für Entwickler

* **[Integrieren Sie die Benutzeroberfläche für die Erfassung gemischter Erkenntnisse in immersive apps](mixed-reality-capture-for-developers.md#integrating-mrc-functionality-from-within-your-app)** : Entwickler können die Transformation für gemischtes umsetzen mithilfe der integrierten Windows- [Kamera Erfassung](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) mit nur wenigen Codezeilen in Ihre apps integrieren.

### <a name="for-commercial-customers"></a>Für kommerzielle Kunden

* **Aktivieren** der Bereitstellung nach der Installation: Sie können jetzt jederzeit mithilfe von Einstellungen ein Lauf Zeit Bereitstellungs Paket anwenden.
* **Zugewiesener Zugriff mit Azure Ad Gruppen** : Sie können nun Azure Ad Gruppen für die Konfiguration von Windows-zugewiesenem Zugriff verwenden, um eine Einzel-oder Multi-App-Kiosk Konfiguration einzurichten.
* **Pin-Anmeldung beim Profil Schalter von Anmeldebildschirm** anheften-Anmeldung ist jetzt für "anderer Benutzer" auf dem Anmeldebildschirm verfügbar. 
* **Lesen von Gerätehardware Informationen über MDM** : IT-Administratoren können hololens nach Geräteserien Nummer in der MDM-Konsole anzeigen und nachverfolgen.
* **Festlegen des hololens-Geräte namens über MDM (umbenennen)** : IT-Administratoren können hololens-Geräte in der MDM-Konsole sehen und umbenennen.

### <a name="for-international-customers"></a>Für internationale Kunden

Sie können nun hololens mit lokalisierter Benutzeroberfläche für vereinfachtes Chinesisch oder Japanisch verwenden, darunter lokalisierte Pinyin-Tastatur, Diktat, Text-zu-Sprache (TTS) und Sprachbefehle.

## <a name="known-issues"></a>Bekannte Probleme

Wir haben hart daran gearbeitet, eine großartige Windows Mixed Reality-Erfahrung bereitzustellen, aber wir verfolgen weiterhin einige bekannte Probleme. Wenn Sie andere finden, [Geben Sie uns Feedback](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback).

### <a name="hololens"></a>HoloLens
 
#### <a name="after-update"></a>Nach dem Update
Möglicherweise bemerken Sie folgende Probleme, wenn Sie das Windows 10-Update vom Oktober 2018 auf Ihren hololens verwenden:
* **Apps können sich beim Starten über eine Benachrichtigung in der Anmelde Schleife befinden** – einige apps, für die eine Anmeldung erforderlich ist, können beim Starten über eine Benachrichtigung in eine endlos Anmelde Schleife aufgenommen werden. Dies kann z. b. der Fall sein, nachdem die Microsoft Unternehmensportal-App aus dem Microsoft Store installiert und von der Benachrichtigung zum Abschluss der Installation gestartet wurde.
* Die **Seite "App-Anmeldung" kann mit einer leeren Seite abgeschlossen** werden – in einigen Fällen, in denen eine Anmeldeaufforderung Ihre Anwendung anzeigt, wird die Anmeldeseite nach Abschluss nicht geschlossen, sondern eine leere (schwarze) Seite angezeigt. Sie können entweder die leere Seite schließen oder Sie verschieben, um die darunter liegende Anwendung zu erkennen. Dies kann beispielsweise bei der Anmeldung während der MDM-Registrierung über die app "Einstellungen" vorkommen. 

## <a name="provide-feedback-and-report-issues"></a>Bereitstellen von Feedback und melden von Problemen

Verwenden Sie die [Feedback-Hub-App auf Ihren hololens oder Windows 10-PCs](give-us-feedback.md) , um Feedback zu geben und Probleme zu melden. Die Verwendung von Feedback Hub stellt sicher, dass alle erforderlichen Diagnoseinformationen enthalten sind, damit unsere Techniker das Problem schnell Debuggen und beheben können.

>[!NOTE]
>Stellen Sie sicher, dass Sie die Eingabeaufforderung akzeptieren, in der Sie gefragt werden, ob der Feedback-  Hub auf den Ordner "Dokumente" zugreifen soll.

## <a name="prior-release-notes"></a>Vorherige Anmerkungen zu dieser Version

* [Versionshinweise – April 2018](release-notes-april-2018.md)
* [Versionshinweise – Oktober 2017](release-notes-october-2017.md)
* [Versionshinweise – August 2016](release-notes-august-2016.md)
* [Versionshinweise – Mai 2016](release-notes-may-2016.md)
* [Versionshinweise – März 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Siehe auch
* [Immersive Headset-Unterstützung (externer Link)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Hololens-Unterstützung (externer Link)](https://support.microsoft.com/products/hololens)
* [Installieren der Tools](install-the-tools.md)
* [Feedback senden](give-us-feedback.md)

