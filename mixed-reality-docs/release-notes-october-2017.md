---
title: Anmerkungen zu dieser Version-Oktober 2017
description: Windows Mixed Reality-Versions Hinweise für das Windows 10 Fall Creators Update (Oktober 2017).
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Anmerkungen zu dieser Version, Version, Windows 10, Build, RS3, Betriebssystem
ms.openlocfilehash: 7274dcf1db449fa35981eb72192fea9873fcc90a
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524098"
---
# <a name="release-notes---october-2017"></a>Anmerkungen zu dieser Version-Oktober 2017

Willkommen bei Windows Mixed Reality! Die Veröffentlichung von **[Windows 10 Fall Creators Update](https://blogs.windows.com/windowsexperience/2017/10/17/whats-new-windows-10-fall-creators-update/)** bietet Unterstützung für neue [Windows Mixed Reality-immersive Headsets](immersive-headset-hardware-details.md) und [Bewegungs Controller](motion-controllers.md)und ermöglicht Ihnen das untersuchen neuer Welten, das Abspielen von VR-spielen und das Eintauchen in die Praxis. Unterhaltung, wenn eine Verbindung mit einem [Windows Mixed Reality-fähigen PC](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)besteht.

Die Veröffentlichung von Windows Mixed Reality-Headsets und Motion Controller ist der Höhepunkt eines enormen Team Aufwands und ein wichtiger Schritt nach vorn für die [Windows Mixed Reality-Plattform](mixed-reality.md), die [Microsoft hololens](hololens-hardware-details.md)umfasst. Obwohl hololens kein Update mit der Veröffentlichung von Windows 10 Fall Creators Update empfängt, wissen Sie, dass die Arbeit an hololens nicht angehalten wurde. Wir werden viele Erkenntnisse und Einblicke erhalten, um von der aktuellen Arbeit in Windows Mixed Reality als Ganzes zu kommen. Tatsächlich stellen immersive Headsets und Bewegungs Controller in Windows Mixed Reality einen hervorragend Einstiegspunkt für die Entwicklung von hololens dar, da dieselben APIs, Tools und Konzepte für beides gelten.

Um für jedes Gerät ein Update auf die neueste Version zu starten, öffnen Sie die app " **Einstellungen** ", navigieren Sie zu **Update & Sicherheit**, und wählen Sie dann die Schaltfläche **nach Updates suchen** . Auf einem Windows 10-PC können Sie das Windows 10 Fall Creators Update auch manuell mithilfe des [Windows Media-Erstellungs Tools](https://www.microsoft.com/software-download/windows10)installieren.

 **Neueste Version für Desktop:** Windows 10 Desktop Oktober 2017 (**10.0.16299.15**, Windows 10 Fall Creators Update)<br>
 **Neueste Version für hololens:** [Windows 10 Holographic August 2016](release-notes-august-2016.md) (**10.0.14393.0**, Windows 10 Anniversary Update)

>[!VIDEO https://www.youtube.com/embed/YBcLy1lkegg]

## <a name="introducing-windows-mixed-reality"></a>Einführung in Windows Mixed Reality

Das Windows 10 Fall Creators Update führt offiziell die Unterstützung für Windows Mixed Reality-Headsets und Bewegungs Controller ein und macht Windows 10 das erste räumliche Betriebssystem der Welt. Dies umfasst u.a. die folgenden Funktionen:
* Eine **[Vielzahl von Headsets](https://blogs.windows.com/windowsexperience/2017/10/03/how-to-pre-order-your-windows-mixed-reality-headset/)** : in Windows Mixed Reality können Partner eine Vielzahl von Headsets anbieten, die bei der Bereitstellung von $399 USD mit Motion-Controllern gestartet werden.
* **[Motion-Controller](motion-controllers.md)** -Windows Mixed Reality Motion Controllers koppeln Sie drahtlos mit Ihrem PC über Bluetooth, und die Nachverfolgung von sechs Grad an Freiheit, zahlreiche Eingabemethoden und Imus.
* **[Einfache Einrichtung und Portabilität](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)** : Einrichtung und Einstieg in weniger als 10 Minuten. Immersive Headsets verwenden die in-out-Nachverfolgung, um Ihre Bewegung zu verfolgen, und ihre Bewegungs Controller mit sechs Freiheitsgraden. Es sind keine externen Kameras oder Leuchtturm Marker erforderlich!
* **[Unterstützung für eine größere Anzahl von PCs](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)** : in Windows Mixed Reality können mehr Benutzer mit dem Desktop-VR arbeiten als je zuvor, mit Unterstützung für ausgewählte, integrierte Grafikkarten und PCs ab $499 USD.
* **[Windows Mixed Reality Home](navigating-the-windows-mixed-reality-home.md)** : das erste räumliche Betriebssystem der Welt stellt eine vertraute Heimumgebung für das Multitasking mit 2D-apps, das Starten von VR-spielen und-apps und das Platzieren von dekorativen holograms bereit.
* **[Beeindruckende VR-Spiele und-apps in der Microsoft Store](https://www.microsoft.com/store/collections/MR-All-ImmersiveContent/)** , von immersiven Unterhaltung wie Hulu VR und 360 Video bis hin zu Epic-spielen wie superhot VR und Arizona Sunshine, bietet das Microsoft Store eine Reihe von Inhalten, die in Windows Mixed Reality angezeigt werden können.
* **[Steamvr-frühzeitiger Zugriff](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)** : das Windows 10 Fall Creators Update ermöglicht die Unterstützung von steamvr-Titeln mit Windows Mixed Reality-Headsets und-Controllern und stellt den größten Katalog von VR-Titeln für Windows Mixed Reality-Benutzer zur Verfügung.

## <a name="known-issues"></a>Bekannte Probleme

Wir haben hart daran gearbeitet, eine großartige Windows Mixed Reality-Erfahrung bereitzustellen, aber wir verfolgen weiterhin einige bekannte Probleme. Wenn Sie andere finden, [Geben Sie uns Feedback](give-us-feedback.md).

### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Desktop-app in der Windows Mixed Reality-Startseite
* Das Snipping-Tool funktioniert nicht in der Desktop-App.
* Die Einstellung für die Desktop-App wird beim erneuten Starten nicht beibehalten.
* Wenn Sie auf Ihrem Desktop die Mixed Reality Portal Preview-Version verwenden, können Sie beim Öffnen der Desktop-app in der Windows Mixed Reality-Startseite den unendlichen Spiegeleffekt bemerken. 
* Das Ausführen der Desktop-App kann bei nicht-Ultra-Windows Mixed Reality-PCs zu Leistungsproblemen führen. Dies wird nicht empfohlen.  
* Die Desktop-App kann automatisch gestartet werden, da ein unsichtbares Fenster auf dem Desktop den Fokus besitzt. 
* Bei der Eingabeaufforderung für die Desktop Benutzerkontensteuerung wird das Headset schwarz angezeigt, bis die Eingabeaufforderung abgeschlossen ist.

### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality-Setup
* Wenn Sie Windows mit einem mit einem Headset verbundenen Verbindungsaufbau einrichten, wird der PC-Monitor möglicherweise leer. Entfernen Sie Ihr Headset, um die Ausgabe an Ihren PC-Monitor zu aktivieren und Windows Setup abzuschließen.
* Beim Erstellen einer Grenze schlägt die Ablauf Verfolgung möglicherweise fehl. Wenn dies der Fall ist, versuchen Sie es erneut, da das System im Laufe der Zeit mehr über Ihren Raum erfährt.
* Wenn Sie Cortana während des Windows Mixed Reality-Setups aktivieren oder deaktivieren, wird diese Änderung auf Ihre Desktop-Cortana-Einstellungen angewendet.
* Wenn Sie keine Kopfhörer verbunden haben, können Sie beim ersten Besuch der Windows Mixed Reality-Startseite weitere Tipps übersehen.
* Bluetooth-Kopfhörer können zu Störungen bei Bewegungs Controllern führen. Es wird empfohlen, Bluetooth-Controller bei Windows Mixed Reality-Sitzungen abzukoppeln oder herunter zu schalten.

### <a name="games-and-apps-from-windows-store"></a>Spiele und Apps aus dem Windows Store
* Einige grafisch intensive Spiele, wie z. b. Forza Motorsport 6, können zu Leistungsproblemen auf weniger leistungsfähigen PCs führen, wenn Sie in Windows Mixed Reality gespielt werden.

### <a name="audio"></a>Audio
* Wie bereits erwähnt, funktionieren Bluetooth-Audioperipherie-Peripheriegeräte nicht gut mit Windows Mixed Reality Voice und räumlichen Sound Umgebungen. Sie können sich auch negativ auf die Benutzeroberflächen Funktion des Bewegungs Controllers auswirken. Es wird nicht empfohlen, Bluetooth-Audioheadsets mit Windows Mixed Reality zu verwenden.
* Sie können das Audiogerät, das mit (oder teilweise) verbunden ist, nicht für die Audiowiedergabe verwenden, wenn das Gerät nicht genutzt wird. Wenn Sie nur über ein audioheadset verfügen, empfiehlt es sich möglicherweise, das audioheadset mit dem Host-PC anstatt mit dem Headset zu verbinden. Wenn dies der Fall ist, müssen Sie in den **Einstellungen** > **Mixed Reality** > **Audiound Speech**die Option "an Headset-audiowechsel wechseln" deaktivieren.
* Einige Anwendungen, einschließlich vieler Anwendungen, die über steamvr gestartet werden, können das Audiogerät verlieren, wenn sich das Audiogerät ändert, wenn Sie das Mixed Reality-Portal starten oder beenden. Starten Sie die APP neu, nachdem Sie die Mixed Reality-Portal-app geöffnet haben, um dies zu korrigieren.
* Wenn Cortana auf Ihrem Host-PC aktiviert ist, bevor Sie Ihr Windows Mixed Reality-Headset verwenden, verlieren Sie möglicherweise die räumliche Audiosimulation, die auf die apps angewendet wird, die Sie in der Windows Mixed Reality-Startseite platzieren. Die Problem Umgehung besteht darin, "Windows Sonic for Kopfhörer" auf allen Audiogeräten zu aktivieren, die an Ihren PC angeschlossen sind, auch mit Ihrem mit dem Headset verbundenen Audiogerät:
   1. Klicken Sie in der Desktop-Taskleiste mit der linken Maustaste auf das Redner Symbol, und wählen Sie aus der Liste der Audiogeräte.
   2. Klicken Sie in der Desktop-Taskleiste mit der rechten Maustaste auf das Redner Symbol, und wählen Sie im Menü "sprechersetup" die Option "Windows-Sound für Kopfhörer"
   3. Wiederholen Sie diese Schritte für alle Ihre Audiogeräte (Endpunkte).
>[!NOTE]
> - Da die mit Ihrem Headset verbundenen Kopfhörer/Sprecher nur angezeigt werden, wenn Sie Sie nicht verwenden, müssen Sie dies innerhalb des Fensters Desktop-App des Windows Mixed Reality Home tun, um diese Einstellung auf das Audiogerät anwenden zu können, das mit Ihrem Headset verbunden ist (oder integriert). in Ihrem Headset).
> - Eine andere Möglichkeit besteht darin, die Option "Cortana auf Hallo Cortana Antworten" in den **Einstellungen** > **Cortana** auf Ihrem Desktop zu deaktivieren, bevor Windows Mixed Reality gestartet wird.

* Wenn ein anderes Multimedia-USB-Gerät (z. b. eine Web-Cam) denselben USB-Hub (entweder extern oder innerhalb Ihres PCs) mit dem Windows Mixed Reality-Headset gemeinsam nutzt, kann der AudioJack/-Kopfhörer des Headsets in seltenen Fällen entweder einen rauschenden Sound oder überhaupt keine Audiodaten enthalten. Sie können dies durch Ihr Headset an einem USB-Anschluss beheben, der nicht denselben Hub wie das andere Gerät verwendet, oder Sie können ihr anderes USB-Multimedia-Gerät trennen bzw. deaktivieren.
* In seltenen Fällen kann der USB-Hub des Host-PCs nicht genügend Stromversorgung für das Windows Mixed Reality-Headset bereitstellen, und Sie bemerken möglicherweise einen Burst Rausch von dem mit dem Headset verbundenen Kopfhörer.

### <a name="speech"></a>Spracherkennung
* Cortana kann Ihre Audiohinweise zum lauschen/überdenken und audioantworten auf Befehle nicht wiedergeben.
* Cortana in China-und Japan-Märkten zeigt während der Verwendung den Text unterhalb des Cortana-Kreises nicht ordnungsgemäß an.
* Cortana kann langsam sein, wenn Sie zum ersten Mal in einer gemischten Reality-Portal Sitzung aufgerufen wird. Sie können dieses Problem umgehen, indem Sie sicherstellen, dass Cortana auf Hey Cortana antwortet, unter **Einstellungen** > **Cortana** > **Talk to Cortana** aktiviert ist.
* Cortana kann auf PCs langsamer ausgeführt werden, bei denen es sich nicht um Windows Mixed Reality Ultra-PCs handelt.
* Wenn die System Tastatur auf eine Sprache festgelegt ist, die sich von der Benutzeroberflächen Sprache in Windows Mixed Reality unterscheidet, führt die Verwendung von Diktat auf der Tastatur in Windows Mixed Reality zu einem Fehler Dialogfeld, dass das Diktat nicht funktioniert, weil keine Wi-Fi-Verbindung besteht. Um das Problem zu beheben, stellen Sie einfach sicher, dass die Tastatur Sprache des Systems mit der Programmiersprache Windows Mixed Reality übereinstimmt.
* Spanien wird nicht ordnungsgemäß als Markt erkannt, auf dem Sprache für Windows Mixed Reality aktiviert ist.

### <a name="holograms"></a>Hologramme
* Wenn Sie in Ihrer Windows Mixed Reality-Homepage eine große Anzahl von holograms platziert haben, werden einige möglicherweise nicht mehr angezeigt, und Sie werden bei der Suche wieder angezeigt. Um dies zu vermeiden, entfernen Sie einige der Hologramme in diesem Bereich des Windows Mixed Reality-Home.

### <a name="motion-controllers"></a>Motion-Controller
* Wenn Sie auf eine Webseite in Microsoft Edge klicken, wird der Inhalt manchmal vergrößert, anstatt auf "Click".
* Wenn Sie auf eine Webseite in Microsoft Edge klicken, wird der Inhalt manchmal vergrößert, anstatt auf "Click".

## <a name="prior-release-notes"></a>Vorherige Anmerkungen zu dieser Version
* [Versionshinweise – August 2016](release-notes-august-2016.md)
* [Versionshinweise – Mai 2016](release-notes-may-2016.md)
* [Versionshinweise – März 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Siehe auch
* [Immersive Headset-Unterstützung (externer Link)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [HoloLens – bekannte Probleme](hololens-known-issues.md)
* [Installieren der Tools](install-the-tools.md)
* [Feedback senden](give-us-feedback.md)
