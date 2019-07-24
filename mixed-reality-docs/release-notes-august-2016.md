---
title: Anmerkungen zu dieser Version-August 2016
description: Hololens-Versions Hinweise für die Windows 10 Anniversary-Version (Fall 2016)
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Hololens, Anmerkungen zu dieser Version, Betriebssystem, Plattform, Features, kommerzielle Suite
ms.openlocfilehash: 2fde8665f3572589abd3dcdfb3747ca487b66afb
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524277"
---
# <a name="release-notes---august-2016"></a>Anmerkungen zu dieser Version-August 2016

Das hololens-Team überwacht das Feedback von Entwicklern im Windows-Insider Programm, um unsere Arbeit zu priorisieren. Bitte geben Sie [uns Feedback](give-us-feedback.md) über den Feedback-Hub, die [Entwickler Foren](https://forums.hololens.com) und [Twitter via @HoloLens ](https://twitter.com/hololens). Da Windows 10 das Anniversary Update umfasst, bietet das hololens-Team eine weitere Verbesserung der Holographic-Darstellung. In diesem Update haben wir uns auf wichtige Korrekturen, Verbesserungen und die Einführung von Features konzentriert, die von Unternehmen angefordert werden und in der kommerziellen Suite von Microsoft hololens verfügbar sind.

**Neueste Version:** Windows Holographic August 2016-Update (**10.0.14393.0**, Windows 10 Anniversary Release)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

Um [auf die aktuelle Version zu aktualisieren](updating-hololens.md), öffnen Sie die app " *Einstellungen* ", navigieren Sie zu *Update & Sicherheit*, und wählen Sie dann die Schaltfläche *nach Updates suchen aus* .

## <a name="new-features"></a>Neue Funktionen

**An Prozess Debuggen anfügen** Hololens unterstützt jetzt das Debuggen von "Attach zu Process". Sie können Visual Studio 2015 Update 3 verwenden, um eine Verbindung mit einer laufenden app auf einem hololens herzustellen und mit dem [Debuggen zu beginnen](using-visual-studio.md#debugging-an-installed-or-running-app). Dies funktioniert, ohne dass eine Bereitstellung aus einem Visual Studio-Projekt erforderlich ist.

**Aktualisierter hololens-Emulator** Wir haben auch eine aktualisierte Version des hololens-Emulators veröffentlicht.

**Gamepad-Unterstützung** Sie können jetzt Bluetooth-Gamepads mit hololens verwenden. Der neu veröffentlichte Xbox Wireless Controller bietet Bluetooth-Funktionen und kann verwendet werden, um Ihre bevorzugten Spiele und Apps mit Gamepad-aktiviertem Spiel zu spielen. Ein [Controller Update](http://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) muss angewendet werden, bevor Sie die Xbox Wireless Controller S mit hololens verbinden können. Der Xbox Wireless Controller S wird von [xinput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx) -und [Windows. Gaming. Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) -APIs unterstützt. Auf zusätzliche Modelle von Bluetooth-Controllern kann über die [Windows. Gaming. Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) -API zugegriffen werden.

## <a name="improvements-and-fixes"></a>Verbesserungen und Korrekturen

Wir sind mit dem Rest des Windows 10 Anniversary Update synchron, sodass Sie zusätzlich zu den hololens-spezifischen Korrekturen auch die ganze Güte von Windows Update erhalten, um die Zuverlässigkeit und Leistung der Plattform zu erhöhen. Ihr Feedback ist äußerst wertvoll und wird für Korrekturen in der-Version priorisiert.

Wir haben die folgenden Funktionen verbessert:
* Melden Sie sich an.
* Arbeitsplatz Beitritt.
* Energieeffizienz für Geräte Energiestatus Übergänge.
* Stabilität durch Mixed Reality-Erfassungen.
* Zuverlässigkeit für Bluetooth-Konnektivität
* – Hologramm-Persistenz in Multi-App-Szenario.

Die folgenden Probleme wurden behoben:
* der Visual Studio-Profiler und der Grafik Debugger können keine Verbindung herstellen.
* Fotos & Dokumente werden im Datei-Explorer im Geräte Portal nicht angezeigt.
* die APP-Leiste kann während des angewendeter Cursors im Anpassungsmodus blinken
* Im Anpassungsmodus wechselt der Eye-Gaze-Punkt-Cursor zu einem späteren Zeitpunkt in den 4-Pfeil-Cursor.
* "Hey Cortana Play Music" startet Groove nicht.
* nach dem vorherigen Update wird bei "Go Home" der Pins-Bereich nicht ordnungsgemäß angezeigt.

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Einführung in die kommerzielle Suite von Microsoft hololens

Die kommerzielle Suite von Microsoft hololens ist für die Unternehmens Bereitstellung bereit. Wir haben unsere frühen Geschäftspartner mit mehreren hoch angeforderten [kommerziellen Features](commercial-features.md) erweitert.

Wenden Sie sich an Ihren lokalen Microsoft-Konto Manager, um die Microsoft hololens-Handels Suite zu erwerben.

### <a name="key-commercial-features"></a>Wichtige kommerzielle Features 

* **Kiosk Modus.** Mit dem Modus "hololens Kiosk" können Sie einschränken, welche apps ausgeführt werden, um Demo-oder Showcase-Erfahrungen zu ermöglichen.<br>
  ![Im Kiosk Modus wird hololens direkt in der APP Ihrer Wahl gestartet.](images/201608-kioskmode-400px.png)
* **Verwaltung mobiler Geräte (Mobile Device Management, MDM) für hololens.** Ihre IT-Abteilung kann mehrere hololens-Geräte gleichzeitig mit Lösungen wie Microsoft InTune verwalten. Sie können Einstellungen verwalten, zu installierende Apps auswählen und Sicherheitskonfigurationen festlegen, die auf die Anforderungen Ihrer Organisation zugeschnitten sind.<br>
  ![Die Verwaltung mobiler Geräte auf hololens ermöglicht Geräteverwaltung auf Unternehmens Niveau über mehrere Geräte hinweg.](images/201608-enterprisemanagement-400px.png)
* **Windows Update für Unternehmen.** Kontrollierte Betriebssystemupdates für Geräte und Unterstützung für den Branch für langfristige Wartung.
* **Datensicherheit.** Die BitLocker-Datenverschlüsselung ist auf hololens aktiviert, um die gleiche Sicherheitsstufe wie alle anderen Windows-Geräte bereitzustellen.
* **Arbeitsplatz Zugriff.** Jeder in Ihrer Organisation kann eine Remote Verbindung mit dem Unternehmensnetzwerk über ein virtuelles privates Netzwerk auf einem hololens herstellen. Hololens können auch auf WLAN-Netzwerke zugreifen, für die Anmelde Informationen erforderlich sind.
* **Microsoft Store für Unternehmen.** Ihre IT-Abteilung kann auch einen privaten Unternehmens Speicher einrichten, der nur die apps Ihres Unternehmens für ihre jeweilige hololens-Nutzung enthält. Verteilen Sie Ihre Unternehmenssoftware auf sichere Weise an die ausgewählte Gruppe von Unternehmens Benutzern.

### <a name="development-edition-vs-commercial-suite"></a>Entwicklungs Edition im Vergleich zu Kommerzielle Suite

<table>
<tr>
<th>Features</th><th>Development Edition</th><th>Kommerzielle Suite</th>
</tr><tr>
<td>Geräteverschlüsselung (BitLocker)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Virtuelles privates Netzwerk (VPN)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="using-the-windows-device-portal.md#kiosk-mode">Kiosk Modus</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Verwaltung und Bereitstellung</th>
</tr><tr>
<td>Mobile Geräteverwaltung (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Möglichkeit zum Blockieren der Aufhebung der Registrierung</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Zertifikat basierter Wi-Fi-Zugriff für Unternehmen</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (Consumer)</td><td style="text-align: center;">Schutz</td><td style="text-align: center;">Filtern über MDM</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">Business Store-Portal</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Sicherheit und Identität</th>
</tr><tr>
<td>Anmelden mit Azure Active Directory (AAD)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Mit Microsoft-Konto (MSA) anmelden</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Anmelde Informationen der nächsten Generation mit PIN entsperren</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">Sicherer Start</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Wartung und Support</th>
</tr><tr>
<td>Automatische Systemupdates beim Eintreffen</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Windows Update für Unternehmen</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Branch für langfristige Wartung</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>Vorherige Anmerkungen zu dieser Version
* [Versionshinweise – Mai 2016](release-notes-may-2016.md)
* [Versionshinweise – März 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Siehe auch
* [HoloLens – bekannte Probleme](hololens-known-issues.md)
* [Kommerzielle Features](commercial-features.md)
* [Installieren der Tools](install-the-tools.md)
* [Verwendung des HoloLens Emulators](using-the-hololens-emulator.md)
