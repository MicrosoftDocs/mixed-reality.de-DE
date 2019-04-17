---
title: Anmerkungen zu dieser Version – August 2016
description: HoloLens-Versionshinweise für das Windows 10 Anniversary-Version (Herbst 2016)
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, release Notes, Betriebssystem, Plattform, Funktionen, commercial suite
ms.openlocfilehash: 2fde8665f3572589abd3dcdfb3747ca487b66afb
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596357"
---
# <a name="release-notes---august-2016"></a>Anmerkungen zu dieser Version – August 2016

Das Team HoloLens Lauscht auf Feedback von Entwicklern in der Windows-Insider-Programm, unsere Arbeit zu priorisieren. Fahren Sie mit [senden Sie uns Feedback](give-us-feedback.md) über den Feedback-Hub, den [Entwicklerforen](https://forums.hololens.com) und [über Twitter @HoloLens ](https://twitter.com/hololens). Als Windows 10 verbessern umarmungen, die dem Anniversary-Update, das Team HoloLens übermitteln Ordnung ist, weiter zur holografischen Benutzeroberfläche. In diesem Update wird standen auf wichtige Fehlerbehebungen, Verbesserungen und Einführung in Features, die angefordert von Unternehmen und in der kommerziellen Microsoft HoloLens-Suite zur Verfügung.

**Neueste Version:** Update für Windows Holographic August 2016 (**10.0.14393.0**, Windows 10 Anniversary-Version)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

Um [Update auf die aktuelle Version](updating-hololens.md)öffnen die *Einstellungen* -app, wechseln Sie zu *Update und Sicherheit*, und wählen Sie dann die *nach Updates suchen* Schaltfläche ".

## <a name="new-features"></a>Neue Funktionen

**Fügen Sie Debuggen, Prozess** HoloLens unterstützt jetzt die anfügen-Prozess zu debuggen. Sie können Visual Studio 2015 Update 3 verwenden, für die Verbindung mit einer ausgeführten app auf einem HoloLens und [Debuggen sie](using-visual-studio.md#debugging-an-installed-or-running-app). Dies funktioniert ohne aus einem Visual Studio-Projekt bereitstellen zu müssen.

**HoloLens-Emulator aktualisiert** haben wir auch eine aktualisierte Version des Emulators HoloLens eingeführt.

**Gamepad-Unterstützung** können Sie jetzt gekoppelt und Bluetooth-Gamepads mit HoloLens verwenden! Die neu veröffentlichten Xbox Wireless-Controller-S Bluetooth-Funktionen features und können verwendet werden, um Ihre bevorzugten Gamepad-fähigen Spiele und apps zu spielen. Ein [controllerupdate](http://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) angewendet werden muss, bevor Sie die Xbox-Wireless-Controller-S mit HoloLens verbinden können. Die Xbox-Wireless-Controller-S wird von unterstützt [XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx) und [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) APIs. Zusätzliche Modelle der Bluetooth-Controller zugegriffen werden können, über die [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API.

## <a name="improvements-and-fixes"></a>Verbesserungen und Fehlerbehebungen

Wir sind synchron mit dem Rest der Windows 10 Anniversary Update, damit zusätzlich zu den spezifischen Fixes Hololens, Sie auch all die Vorteile aus dem Windows Update Plattform Zuverlässigkeit und Leistung zu erhöhen erhalten. Ihr Feedback ist hochgradig Werten und für Korrekturen in der Version priorisiert.

Wir haben die folgenden Funktionen verbessert:
* Melden Sie sich Erfahrungen.
* Workplace Join.
* Energieeffizienz für Gerät Übergänge der energieverwaltung.
* Stabilität Mixed Reality erfasst.
* Zuverlässigkeit für Bluetooth-Verbindungen
* – Hologramm Dauerhaftigkeit in mehreren app-Szenario.

Die folgenden Probleme wurden behoben:
* die Visual Studio-Profiler und den grafikdebugger keine Verbindung herstellen.
* Fotos und Dokumente werden nicht im Datei-Explorer in das Device Portal angezeigt.
* der App-Leiste können flash, wenn der Cursor sich darüber im Modus "anpassen" befindet.
* Im Modus "anpassen" der Eye Blicke Punkt Cursor verändert sich auf den Pfeil in der 4-Cursor noch Mal langsamer.
* "Hey Cortana Musik wiedergeben" Groove wird nicht gestartet.
* nach dem vorherigen Update wird sagen "Go Home" nicht im Bereich Pins richtig angezeigt.

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Einführung in die kommerzielle Microsoft HoloLens-Suite

Die Microsoft HoloLens Commercial Suite ist für die unternehmensbereitstellung bereit. Wir haben einige stark nachgefragte hinzugefügt [kommerziellen Features](commercial-features.md) aus unserer frühen Geschäftspartner.

Wenden Sie sich an Ihren lokalen Microsoft Account Manager, um die Microsoft HoloLens Commercial Suite erwerben.

### <a name="key-commercial-features"></a>Wichtige kommerziellen Features 

* **Kiosk-Modus.** Mit HoloLens Kiosk-Modus können Sie welche apps ausführen, um die Demo- oder Showcase Ihre einschränken.<br>
  ![Startet Kiosk-Modus HoloLens, direkt in die app Ihrer Wahl.](images/201608-kioskmode-400px.png)
* **Verwaltung mobiler Geräte (MDM) für HoloLens.** Ihre IT-Abteilung kann mehrere HoloLens-Geräte, die gleichzeitig mit Lösungen wie Microsoft Intune verwalten. Sie können Einstellungen verwalten, zu installierende Apps auswählen und Sicherheitskonfigurationen festlegen, die auf die Anforderungen Ihrer Organisation zugeschnitten sind.<br>
  ![Mobilgeräteverwaltung für HoloLens stellt geräteverwaltung für Unternehmen auf Unternehmensniveau bereit, auf mehreren Geräten.](images/201608-enterprisemanagement-400px.png)
* **Windows Update for Business.** Aktualisieren des Betriebssystems für Geräte und Unterstützung für long Term servicing Branch wird gesteuert.
* **Sicherheit der Daten.** BitLocker die datenverschlüsselung ist für HoloLens aktiviert, das dieselbe Schutzebene wie jedes andere Windows-Gerät bereitstellen.
* **Arbeiten Sie den Zugriff.** Jeder in Ihrer Organisation kann sich Remote mit dem Unternehmensnetzwerk über VPN auf einem HoloLens verbinden. HoloLens können auch Wi-Fi-Netzwerke zugreifen, die Anmeldeinformationen erfordern.
* **Microsoft Store für Unternehmen.** Ihre IT-Abteilung kann ein Unternehmen mit dem privaten Speicher, einrichten, die nur für Ihre spezifische Nutzung von HoloLens apps Ihres Unternehmens enthält. Sichere Verteilung Ihrer Enterprise-Software für ausgewählte Gruppe von Enterprise-Benutzer.

### <a name="development-edition-vs-commercial-suite"></a>Development Edition im Vergleich Commercial Suite

<table>
<tr>
<th>Features</th><th>Development Edition</th><th>Commercial Suite</th>
</tr><tr>
<td>Geräteverschlüsselung (Bitlocker)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Virtuelles privates Netzwerk (VPN)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="using-the-windows-device-portal.md#kiosk-mode">Kiosk-Modus</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Verwaltung und Bereitstellung</th>
</tr><tr>
<td>Mobile Geräteverwaltung (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Möglichkeit, die Aufhebung der Registrierung blockieren</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Zertifikat-basierter Unternehmens-WLAN-Zugriff</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (Consumer)</td><td style="text-align: center;">Consumer</td><td style="text-align: center;">Filtern mit der Verwaltung mobiler Geräte</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">Business Store-Portal</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Sicherheit und Identität</th>
</tr><tr>
<td>Melden Sie sich mit Azure Active Directory (AAD)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Melden Sie sich mit Microsoft-Konto (MSA)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Next Generation-Anmeldeinformationen mit PIN entsperren</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">Sicherer Start</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Wartung und Support</th>
</tr><tr>
<td>Automatische System aktualisiert, sobald sie eintreffen</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Windows Update for Business</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Long-Term servicing branch</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>Anmerkungen zu dieser früheren Version
* [Anmerkungen zu dieser Version – Mai 2016](release-notes-may-2016.md)
* [Anmerkungen zu dieser Version – März 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Siehe auch
* [HoloLens – bekannte Probleme](hololens-known-issues.md)
* [Kommerziellen features](commercial-features.md)
* [Installieren der tools](install-the-tools.md)
* [Verwendung des HoloLens Emulators](using-the-hololens-emulator.md)
