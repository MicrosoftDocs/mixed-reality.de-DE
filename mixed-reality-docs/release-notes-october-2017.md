---
title: Anmerkungen zu dieser Version – Oktober 2017
description: Windows Mixed Reality-Versionshinweise für Windows 10 Fall Creators Update (Oktober 2017).
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Freigeben der Anmerkungen zu dieser Version, Version, Windows 10, Build, rs3, Betriebssystem
ms.openlocfilehash: 7274dcf1db449fa35981eb72192fea9873fcc90a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593357"
---
# <a name="release-notes---october-2017"></a>Anmerkungen zu dieser Version – Oktober 2017

Willkommen bei Windows Mixed Reality. Die Version von der **[Windows 10 Fall Creators Update](https://blogs.windows.com/windowsexperience/2017/10/17/whats-new-windows-10-fall-creators-update/)** führt die Unterstützung für neue [Windows Mixed Reality immersive Headsets](immersive-headset-hardware-details.md) und [motion-Controller ](motion-controllers.md), aktivieren Sie neue Welten zu untersuchen, VR-Spiele spielen, und erleben Sie fesselnde Unterhaltung beim Verbinden mit einem [capable PC Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

Die Version von Windows Mixed Reality-Headsets und während der Übertragung Controller ist der Höhepunkt eine massive teamleistung und einen wichtigen Schritt vorwärts für die [Windows Mixed Reality-Plattform](mixed-reality.md), wozu [Microsoft HoloLens](hololens-hardware-details.md). Während die HoloLens ein Update mit der Veröffentlichung von der Windows 10 Fall Creators Update wird nicht empfangen werden, wissen Sie, dass arbeiten HoloLens beendet, noch nicht aus; Wir müssen viele Erkenntnisse und Einblicke, um unsere bisherige Arbeit in Windows Mixed Reality als Ganzes anzuwenden. In der Tat immersive Headsets Windows Mixed Reality und während der Übertragung, dass Controller einen hervorragenden Einstieg darstellen für die Entwicklung für HoloLens auch, wie die gleichen APIs, Tools und Konzepte gelten für beide.

Um auf die neueste Version für jedes Gerät zu aktualisieren, öffnen die **Einstellungen** wechseln Sie zur app **Update und Sicherheit**, und wählen Sie dann die **nach Updates suchen** Schaltfläche. Auf einem Windows 10-PC, Sie können auch manuell installieren der Windows 10 Fall Creators Update mithilfe der [Tool zur Erstellung von Windows Media](https://www.microsoft.com/software-download/windows10).

 **Neueste Release für den Desktop:** 10 Windows_desktop, Oktober 2017 (**10.0.16299.15**, Windows 10 Fall Creators Update)<br>
 **Neueste Release für HoloLens:** [Windows 10 Holographic August 2016](release-notes-august-2016.md) (**10.0.14393.0**, Windows 10 Anniversary Update)

>[!VIDEO https://www.youtube.com/embed/YBcLy1lkegg]

## <a name="introducing-windows-mixed-reality"></a>Einführung in Windows Mixed Reality

Die Windows 10 Fall Creators Update führt offiziell die Unterstützung für Windows Mixed Reality-Headsets Motion-Controller, sowie die Windows 10 weltweit ersten räumlichen-Betriebssystem machen. Hier sind die wichtigsten:
* **[Verschiedene Headsets](https://blogs.windows.com/windowsexperience/2017/10/03/how-to-pre-order-your-windows-mixed-reality-headset/)**  -Windows Mixed Reality ermöglicht Partnern zusammen, um eine Vielzahl von Headsets bieten beginnen am 399 US-Dollar mit Motion-Controllern gebündelt.
* **[Motion Controller](motion-controllers.md)**  -Windows Mixed Reality-Motion-Controller drahtlos mit dem PC über Bluetooth zu koppeln und sechs Grad einer Bewegungsfreiheit von nachverfolgen, zahlreiche Eingabemethoden und IMUs feature.
* **[Einfache Einrichtung und Portabilität](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)**  : Legen einrichten und erste Schritte mit weniger als 10 Minuten. Immersive Headsets verwenden Inside-Out-Überwachung, um Ihre Bewegung und Controller während der Übertragung mit sechs Grad einer Bewegungsfreiheit von nachzuverfolgen. Keine externen Kameras oder Leuchtturm Marker erforderlich!
* **[Unterstützung für einen größeren Bereich von PCs](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)**  -Windows Mixed Reality mehr Benutzern auf den desktop VR als je zuvor auftreten können, mit Unterstützung für SELECT-Anweisung integriert werden soll, Grafikkarten und PCs, die beginnend am 499 US-Dollar.
* **[Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md)**  -erste räumliche Betriebssystem der Welt bietet eine vertraute home Umgebung Multitasking mit Direct2D-apps, beim Starten VR-Spiele und apps und platziert dekorativen Hologramme.
* **[Beeindruckende VR-Spiele und apps in der Microsoft Store](https://www.microsoft.com/store/collections/MR-All-ImmersiveContent/)**  – von immersive Unterhaltung wie Hulu VR und 360 video über die "EPIC" Spiele wie SUPERHOT VR und Arizona Paar Sonnenstrahlen entgegen, die Microsoft Store verfügt über einen Bereich von Inhalten in gemischten Windows auftreten Realität.
* **[SteamVR Vorabzugriff](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)**  : die Windows 10 Fall Creators Update aktiviert die Unterstützung für SteamVR Titel mit Windows Mixed Reality-Headsets wiedergegeben werden soll, und Controllern, sodass der größten Katalogs von VR titles für gemischte Windows verfügbar Benutzer, die Realität.

## <a name="known-issues"></a>Bekannte Probleme

Wir haben hart daran gearbeitet, um eine hervorragende Windows Mixed Reality-Erfahrung zu bieten, aber verfolgen wir noch einige bekannte Probleme. Wenn Sie andere Benutzer finden, wenden Sie [senden Sie uns Feedback](give-us-feedback.md).

### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Desktop-app in die Windows Mixed Reality home
* Snipping Tool funktioniert nicht in Desktop-app.
* Desktop-app beibehalten-Einstellung auf neu starten nicht.
* Wenn Sie Mixed Reality-Verwaltungsportal (Vorschau) auf Ihrem Desktop verwenden, wenn die Desktop-app in die Windows Mixed Reality Startseite zu öffnen, werden Sie mit dem unendlichen Spiegeleffekt feststellen. 
* Ausführen der Desktop-app möglicherweise Leistungsprobleme auf nicht - Ultra Windows Mixed Reality-PCs; Es wird nicht empfohlen.  
* Desktop-app kann automatisch gestartet, da ein nicht sichtbar auf Desktop-Fenster den Fokus besitzt. 
* Desktop User Account Control Aufforderung veranlasst Kopfhörer Schwarz angezeigt, bis die Eingabeaufforderung abgeschlossen ist.

### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality-setup
* Beim Einrichten von Windows mit einem Kopfhörer angeschlossen kann Ihren PC-Monitor gelöscht. Trennen Sie Ihre Kopfhörer zum Aktivieren der Ausgabe auf den PC-Monitor, um Windows Setup abzuschließen.
* Wenn Sie eine Grenze zu erstellen, kann die Ablaufverfolgung fehlschlagen. Wenn dies der Fall ist, versuchen Sie es erneut, wie das System Weitere Informationen zu Ihrem Speicherplatz im Laufe der Zeit wird.
* Wenn Sie Cortana aktiviert oder deaktiviert während des Setups von Windows Mixed Reality aktivieren, wird diese Änderung auf Ihre Cortana-desktopeinstellungen angewendet werden.
* Wenn Sie nicht Kopfhörer angeschlossen haben, kann zusätzliche Tipps übersehen werden, wenn Sie zuerst die Windows Mixed Reality home besuchen.
* Bluetooth-Kopfhörer können Störungen mit Motion-Controllern führen. Es wird empfohlen, entkoppelt oder Bluetooth-Controller herunterzufahren, während Windows Mixed Reality-Sitzungen.

### <a name="games-and-apps-from-windows-store"></a>Spiele und apps von Windows Store
* Einige Spiele grafisch intensive wie Forza Motorsport 6, möglicherweise Leistungsprobleme auf weniger leistungsstarken PCs, wenn in Windows Mixed Reality wiedergegeben.

### <a name="audio"></a>Audio
* Wie bereits erwähnt, funktionieren Audio von Bluetooth-Peripheriegeräte nicht gut mit Windows Mixed Reality-Telefonie- und räumliche sound Erfahrungen. Sie können auch negativ auf Ihre Bewegung-Controller-Umgebung auswirken. Wir empfehlen nicht die Verwendung von Bluetooth-Audio-Headsets mit Windows Mixed Reality.
* Sie können keine audio-Gerät angeschlossen (oder Teil) der Kopfhörer für die Audiowiedergabe, wenn das Gerät nicht getragen wird. Wenn Sie nur eine audio Kopfhörer verfügen, empfiehlt es sich, die zur Verbindung mit des Hosts-PC anstelle der Kopfhörer das audio Kopfhörer. Wenn also dann Sie die "Wechseln zur Kopfhörer Audio" in deaktivieren müssen **Einstellungen** > **Mixed Reality** > **Audio- und Spracherkennung**.
* Einige Anwendungen, einschließlich vieler derjenigen, die gestartet wird, über SteamVR, können Sie verlieren Audio oder aufhängen führt, wenn das Audiogerät nimmt an, wenn beim Starten oder beenden das Mixed Reality-Portal. Starten Sie die app neu, wenn Sie zum Beheben dieses Fehlers die Mixed Reality-Portal-app geöffnet haben.
* Wenn Sie Cortana auf Ihrem Host-PC vor der Verwendung Ihrer Windows Mixed Reality-Kopfhörer aktiviert haben, verlieren Sie möglicherweise die räumliche sound-Simulation, die auf die apps, die Sie für die Windows Mixed Reality home platzieren angewendet. Die problemumgehung besteht darin, aktivieren Sie "Windows Sonic für Kopfhörer" auf alle Audiogeräten, die auf Ihren PC, sogar Ihre Kopfhörer verbundener audio-Gerät angefügt:
   1. Klicken Sie auf das Speaker-Symbol auf der desktop-Taskleiste, und wählen Sie aus der Liste der Audiogeräte.
   2. Mit der rechten Maustaste in des Speaker-Symbols auf der desktop-Taskleiste, und wählen Sie "Windows Sonic für Kopfhörer" im Menü "Speaker-Setup".
   3. Wiederholen Sie diese Schritte für alle Ihre Audiogeräte (Endpunkte).
>[!NOTE]
> - Da die an Ihre Kopfhörer angeschlossen Kopfhörer/Speakers nicht angezeigt werden, es sei denn, Sie sind es trägt, müssen Sie dies im Desktop-app-Fenster in der Windows Mixed Reality home, diese Einstellung gilt für das Audiogerät durchführen Ihrer Kopfhörer verbunden (oder integriert in Ihrer Kopfhörer).
> - Eine weitere Option ist "Let Cortana-Reaktion auf Hey Cortana" deaktivieren **Einstellungen** > **Cortana** auf Ihrem Desktop vor dem Starten von Windows Mixed Reality.

* Wenn Sie ein anderes multimedia USB-Gerät (z. B. eine Webcam) den gleichen USB-Hub (entweder extern oder in Ihrem PC) für die Windows Mixed Reality-Kopfhörer freigegeben hat, kann in seltenen Fällen den Kopfhörer des audio Jack/Kopfhörer entweder Sound Fiepen oder ohne Audio überhaupt haben. Sie können dies durch Ihre Kopfhörer in einen USB-Anschluss beheben, die nicht den gleichen Hub als das andere Gerät freigeben, oder trennen/Deaktivieren von Ihrem anderen multimedia USB-Gerät.
* In sehr seltenen Fällen geben Sie den Host-PC USB-Hub kann nicht ausreichend Leistung, die Windows Mixed Reality-Kopfhörer, und der eines plötzlichen Ansturms von Störungen durch die Kopfhörer an den Kopfhörer angeschlossen.

### <a name="speech"></a>Spracherkennung
* Cortana kann nicht für Überwachung/denken und audio Antworten auf Befehle ihre Audiohinweise wiedergeben.
* Cortana in China, Japan Märkten nicht ordnungsgemäß anzeigen Text unterhalb des Cortana-Kreises bei der Verwendung.
* Cortana kann langsam beim ersten sein, wenn er in einer Mixed Reality-Portal-Sitzung aufgerufen wird. Sie können diese umgehen, indem Sie Sie sicher, dass "Let Cortana auf Hey Cortana Antworten" machen unter **Einstellungen** > **Cortana** > **sprechen Sie mit Cortana** ist aktiviert.
* Cortana kann langsamer auf PCs ausgeführt werden, die nicht Windows Mixed Reality Ultra-PCs sind.
* Wenn die Systemtastatur auf einer anderen Sprache als die Sprache der Benutzeroberfläche in Windows Mixed Reality festgelegt ist, führt zu ein Fehlerdialogfeld zu diktieren funktioniert nicht aufgrund von nicht durch Wi-Fi-Verbindung mithilfe von Diktatmodus über die Tastatur in Windows Mixed Reality. Zum Beheben des Problems einfach sicher, dass die Systemsprache der Tastatur die Windows Mixed Reality-Benutzeroberfläche übereinstimmt.
* Spanien wird nicht ordnungsgemäß als einen Markt erkannt wird, in denen Sprache für Windows Mixed Reality aktiviert ist.

### <a name="holograms"></a>Hologramme
* Wenn Sie eine große Anzahl von Hologramme in Ihr Windows Mixed Reality home platziert haben, können einige nicht mehr angezeigt und wieder eingeblendet, wie Sie sich mit der Registerkarte. Um dies zu vermeiden, entfernen Sie einige der Hologramme in diesem Bereich der Startseite Windows Mixed Reality-Paket aus.

### <a name="motion-controllers"></a>Motion-Controller
* Wenn Sie auf einer Webseite in Microsoft Edge klicken, wird in einigen Fällen der Inhalt anstatt auf vergrößert.
* Manchmal, wenn Sie auf einen Link im Rand klicken, funktioniert die Auswahl nicht.

## <a name="prior-release-notes"></a>Anmerkungen zu dieser früheren Version
* [Anmerkungen zu dieser Version – August 2016](release-notes-august-2016.md)
* [Anmerkungen zu dieser Version – Mai 2016](release-notes-may-2016.md)
* [Anmerkungen zu dieser Version – März 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Siehe auch
* [Unterstützung für immersive Kopfhörer (externer Link)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [HoloLens – bekannte Probleme](hololens-known-issues.md)
* [Installieren der tools](install-the-tools.md)
* [Geben Sie uns feedback](give-us-feedback.md)
