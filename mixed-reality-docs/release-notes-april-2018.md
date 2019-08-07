---
title: Anmerkungen zu dieser Version-April 2018
description: Hololens und Windows Mixed Reality-Versions Hinweise für das Windows 10-Update vom April 2018 (auch bekannt als "RS4").
author: mattzmsft
ms.author: mazeller
ms.date: 05/21/2018
ms.topic: article
keywords: Anmerkungen zu dieser Version, Version, Windows 10, Build, RS4, OS
ms.openlocfilehash: 1fc1b43b0581234e835379fd553b78121108086e
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524173"
---
# <a name="release-notes---april-2018"></a>Anmerkungen zu dieser Version-April 2018

Das **[Windows 10-Update vom April 2018](https://blogs.windows.com/windowsexperience/2018/04/30/whats-new-in-the-windows-10-april-2018-update)** (auch als "RS4" bezeichnet) umfasst neue Features für hololens und Windows Mixed Reality-immersive Headsets, die mit PCs verbunden sind. 

Wenn Sie ein Update auf die neueste Version des Gerätetyps durchlaufen möchten, öffnen Sie die app " **Einstellungen** ", navigieren Sie zu **Update & Sicherheit**, und wählen Sie dann die Schaltfläche **nach Updates suchen** Auf einem Windows 10-PC können Sie das Windows 10-Update vom April 2018 auch manuell mithilfe des [Windows Media-Erstellungs Tools](https://www.microsoft.com/software-download/windows10)installieren.

**Neueste Version für Desktop:** Windows 10 April 2018-Update (**10.0.17134.1**)<br>
**Neueste Version für hololens:** Windows 10 April 2018-Update (**10.0.17134.80**)<br>
<br>

>[!VIDEO https://www.youtube.com/embed/O-84oWjSbr0]

*Eine Meldung von Alex Kipman und eine Übersicht über die neuen Mixed Reality-Features im Windows 10-Update vom April 2018*

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Neue Features für Windows Mixed Reality-immersive Headsets

Das Windows 10-Update vom April 2018 umfasst viele Verbesserungen für die Verwendung von Windows Mixed Reality-(VR)-Headsets mit Ihrem Desktop-PC, wie z. b.: 

* **Neue Umgebungen für die gemischte Realität-Startseite** : Sie können jetzt zwischen dem Klippe und der neuen SkyLoft-Umgebung wählen, indem Sie im Startmenü auf " **Orte** " klicken. Wir haben auch [ein experimentelles Feature](add-custom-home-environments.md) hinzugefügt, mit dem Sie benutzerdefinierte Umgebungen verwenden können, die Sie erstellt haben.
* **Schneller Zugriff auf die gemischte Reality-Erfassung** : Sie können jetzt gemischte Reality-Fotos mithilfe eines Bewegungs Controllers durchführen. Halten Sie die Windows-Taste gedrückt, und tippen Sie dann auf den- Dies funktioniert in Umgebungen und apps, aber es werden keine Inhalte aufgezeichnet, die mit DRM geschützt sind.
* **Neue Optionen für das Starten und Ändern der Größe von Inhalten** : apps werden nun automatisch eingefügt, wenn Sie Sie über das Startmenü starten. Sie können jetzt auch die Größe von 2D-apps ändern, indem Sie die Ränder und Ecken des Fensters ziehen.
* Wechseln Sie **einfach zu Inhalten mit dem Sprachbefehl "Teleport"** . Sie können nun schnell an den Inhalt in der Windows Mixed Reality-Startseite, indem Sie den Inhalt ansehen und "Teleport" aufrufen.
* **[Animierte 3D-App-Launcher](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#animation-guidelines) und [dekorative 3D-Objekte](enable-placement-of-3d-models-in-the-home.md) für die gemischte Reality-Startseite** : Sie können jetzt Animationen zu 3D-App-Start Feldern hinzufügen und Benutzern das Platzieren von dekorativen 3D-Modellen aus einer Webseite oder einer 2D-app in die Windows Mixed Reality-Homepage ermöglichen.
* **[Verbesserungen an Windows Mixed Reality für steamvr](updating-your-steamvr-application-for-windows-mixed-reality.md)** -Windows Mixed Reality für steamvr ist bei neuen Upgrades nicht "frühzeitiger Zugriff", wie z. bbweise: haptisches Feedback bei der Verwendung von Bewegungs Controllern, verbesserte Leistung und Zuverlässigkeit und Verbesserungen der Darstellung von Bewegungs Controllern in steamvr.
* **Weitere Verbesserungen** : automatische Leistungseinstellungen wurden aktualisiert, um eine optimierte Umgebung zu bieten (Sie können diese Einstellung [manuell überschreiben](#visual-quality) ). Setup bietet nun ausführlichere Informationen zu häufigen Kompatibilitätsproblemen bei USB 3,0-Controllern und Grafikkarten.

## <a name="new-features-for-hololens"></a>Neue Features für hololens

Das Windows 10 April 2018-Update ist für alle hololens-Kunden eingetroffen! Dieses Update ist mit Verbesserungen verpackt, die seit der letzten Hauptversion der hololens-Software im [August 2016](release-notes-august-2016.md)eingeführt wurden.

### <a name="for-everyone"></a>Für alle

<table>
  <tr>
    <th>Feature</th><th>Details</th><th>Anweisungen</th>
  </tr>
  <tr>
    <td>Automatische Platzierung von 2D-und 3D-Inhalten beim Start</td><td>Ein 2D-App-Start Programm oder eine 2D-UWP-APP wird in der Welt automatisch in einer optimalen Größe und Entfernung angezeigt, wenn der Benutzer Sie nicht mehr platzieren muss. Wenn eine <a href="app-views.md">immersive App</a> ein 2D-App-Start Programm anstelle eines <a href="3d-app-launcher-design-guidance.md">3D-App</a>-Start Programms verwendet, wird die immersive App automatisch von dem 2D-App-Start Programm wie in RS1 gestartet.<br><br>Ein 3D-App-Start Programm aus dem Startmenü wird auch automatisch in der Welt platziert. Anstatt die APP automatisch zu starten, können Benutzer auf das Start Programm klicken, um die immersive APP zu starten. 3D-Inhalte, die von der holograms-APP und von Edge geöffnet werden, werden auch automatisch in der Welt platziert.</td><td>Wenn Sie eine APP über das Startmenü öffnen, werden Sie nicht mehr aufgefordert, Sie in der Welt zu platzieren.<br><br>Wenn die Platzierung der 2D-APP/<a href="3d-app-launcher-design-guidance.md">3D-App-Start</a> Programm nicht optimal ist, können Sie Sie problemlos mithilfe der unten beschriebenen neuen, flüssigen App-Manipulationen verschieben. Sie können auch das 2D-Startfeld/3D-Inhalt neu positionieren, indem Sie "Move This" (verschieben) und anschließendes Verwenden von "Blick" verwenden, um den Inhalt neu zu positionieren.</td>
  </tr>
  <tr>
    <td>Dynamische App-Bearbeitung</td><td>Verschieben, Ändern der Größe und Drehen von 2D-und 3D-Inhalt, ohne in den Modus "anpassen" wechseln zu müssen.</td><td>Um eine 2D-UWP-APP oder ein 2D-App-Startfeld zu verschieben, schauen Sie sich einfach die zugehörige App-Leiste an Sie können 3D-Inhalte verschieben, indem Sie eine beliebige Stelle im Objekt verwenden und dann Tap + Hold + Drag verwenden.<br><br>Um die Größe von 2D-Inhalten zu ändern, schauen Sie sich die Ecke an. Der Cursor Cursor wird in einen Größenänderung-Cursor umgewandelt, und Sie können dann auf + halten und ziehen klicken, um die Größe zu ändern. Sie können den 2D-Inhalt auch vergrößern oder vergrößern, indem Sie seine Ränder und Zieh Richtung betrachten.<br><br>Um die Größe des 3D-Inhalts zu ändern, können Sie beide Hände in Gesten Rahmen und in der Bereitschafts Position nach oben heben. Sie sehen, dass der Cursor in einen Zustand mit zwei kleinen Händen verwandelt wird. Halten Sie das Tippen und halten Sie mit beiden Händen. Wenn Sie Ihre Hände näher oder weiter auseinander verschieben, ändern Sie die Größe des Objekts. Wenn Sie Ihre Hände relativ zueinander vorwärts und rückwärts bewegen, wird das Objekt rotiert. Auf diese Weise können Sie auch den 2D-Inhalt ändern/drehen.</td>
  </tr>
  <tr>
    <td>Horizontale Größenänderung von 2D-apps mit Umbruch</td><td>Machen Sie eine 2D-UWP-App breiter im Seitenverhältnis, um mehr App-Inhalte anzuzeigen. So ist beispielsweise die e-Mail-App breit genug, um den Vorschaubereich anzuzeigen.</td><td>Schauen Sie sich einfach den linken oder rechten Rand der 2D-UWP-APP an, um den Größenänderung-Cursor anzuzeigen, und verwenden Sie dann die Tastenkombination tippen und halten und ziehen, um die Größe zu ändern.</td>
  </tr>
  <tr>
    <td>Erweiterte sprach Befehls Unterstützung</td><td>Sie können einfach Ihre Stimme verwenden.</td><td>Probieren Sie diese Sprachbefehle aus:<ul><li>"Gehe zu Start": öffnet das Startmenü oder beendet eine <a href="app-views.md">immersive App</a>.</li><li>"Move This" (verschieben): ermöglicht das Verschieben eines Objekts.</li></ul></td>
  </tr>
  <tr>
    <td>Aktualisierte holograms-und Fotos-apps</td><td>Die holograms-App wurde mit neuen holograms aktualisiert. Aktualisierte Fotos-app.</td><td>Sie werden feststellen, dass ein aktualisiertes Aussehen der holograms-und Photos-apps angezeigt wird Die holograms-app enthält mehrere neue holograms und einen Bezeichnungs Ersteller zur einfacheren Erstellung von Text.</td>
  </tr>
  <tr>
    <td>Verbesserte gemischte Reality-Erfassung</td><td>Hardware Verknüpfung starten und Beenden des MRC-Videos.</td><td>Halten Sie das Volume nach oben und nach unten für 3 Sekunden, um das MRC-Video aufzuzeichnen. Tippen Sie erneut auf beides, oder verwenden Sie die aufblüdigungs Bewegung zum Ende</td>
  </tr>
  <tr>
    <td>Konsolidierte Leerzeichen</td><td>Vereinfachen Sie die Speicherplatz Verwaltung für holograms in ein einzelnes Leerzeichen.</td><td>Hololens sucht automatisch nach Ihrem Speicherplatz und erfordert nicht mehr das Verwalten oder auswählen von Leerzeichen. Wenn Sie Probleme mit holograms haben, können Sie zu <b>Einstellungen > System > holograms wechseln > die in der Nähe befindlichen holograms entfernen</b>. Bei Bedarf können Sie auch <b>alle holograms entfernen</b>auswählen.</td>
  </tr>
  <tr>
    <td>Verbessertes audioeintauchen</td><td>Sie können jetzt hololens in unähnlichen Umgebungen besser hören und mehr aus Anwendungen mit einem größeren Sound vergleichen, da Ihr Sound durch echte Wände verdeckt wird, die vom Gerät erkannt werden.</td><td>Sie müssen nichts tun, um den verbesserten räumlichen Sound zu genießen.</td>
  </tr>
  <tr>
    <td>Datei-Explorer</td><td>Verschieben und Löschen von Dateien in hololens.</td><td>Sie können die <b>Datei-Explorer</b> -App verwenden, um Dateien aus hololens zu verschieben und zu löschen.<br><br><b>Tipp:</b> Wenn keine Dateien angezeigt werden, ist der Filter "zuletzt" möglicherweise aktiv (das Clock-Symbol wird im linken Bereich hervorgehoben). Um das Problem zu beheben, wählen Sie das Symbol <b>dieses Geräte</b> Dokument im linken Bereich aus (unterhalb des Takt Symbols), oder öffnen Sie das Menü, und wählen Sie <b>dieses Gerät</b>aus.
</td>
  </tr>
  <tr>
    <td>MTP-Unterstützung (Media Transfer Protocol)</td><td>Ermöglicht dem Desktop-PC den Zugriff auf Ihre Bibliotheken (Fotos, Videos, Dokumente) auf hololens für eine einfache Übertragung.</td><td>Verbinden Sie Ihre hololens mit Ihrem PC ähnlich wie andere mobile Geräte, um den <b>Datei-Explorer</b> für den Zugriff auf hololens-Bibliotheken (Fotos, Videos, Dokumente) zur einfachen Übertragung zu öffnen.<br><br><b>Chti</b><ul><li>Wenn keine Dateien angezeigt werden, stellen Sie sicher, dass Sie sich bei ihren hololens anmelden, um den Zugriff auf Ihre Daten zu ermöglichen.</li><li>Im <b>Datei-Explorer</b> auf Ihrem PC können Sie <b>Geräteeigenschaften</b> auswählen, um die Versionsnummer des Windows Holographic-Betriebssystems (Firmwareversion) und die Seriennummer des Geräts anzuzeigen.</li></ul><b>Bekanntes Problem:</b> Das Umbenennen von hololens über den <b>Datei-Explorer</b> auf Ihrem PC ist nicht aktiviert.</td>
  </tr>
  <tr>
    <td>Netzwerkunterstützung des Captive Portals während des Setups</td><td>Sie können nun ihre hololens in einem Gastnetzwerk in Hotels, Konferenz Centern, Einzelhandelsgeschäften oder Unternehmen einrichten, die das Captive Portal verwenden.</td><td>Wählen Sie während des Setups das Netzwerk aus, aktivieren Sie bei Bedarf automatisch verbinden, und geben Sie die Netzwerkinformationen wie angefordert ein.</td>
  </tr>
  <tr>
    <td>Foto-und Videosynchronisierung über die onedrive-App</td><td>Ihre Fotos und Videos aus hololens werden nun über die onedrive-App aus dem Microsoft Store und nicht direkt über die Fotos-App synchronisiert.</td><td>Um dies einzurichten, laden Sie die onedrive-App aus dem Store herunter, und starten Sie Sie. Bei der ersten Ausführung sollten Sie aufgefordert werden, Ihre Fotos automatisch auf onedrive hochzuladen, oder Sie können die Option in den App-Einstellungen finden.</td>
  </tr>
</table>

### <a name="for-developers"></a>Für Entwickler

<table>
  <tr>
    <th>Feature</th><th>Details</th><th>Anweisungen</th>
  </tr>
  <tr>
    <td>Verbesserte räumliche Zuordnung</td><td>Verbesserungen bei Qualität, Vereinfachung und Leistung.</td><td>Das Mesh der räumlichen Zuordnung erscheint sauberer – es sind weniger Dreiecke erforderlich, um dieselbe Detailebene darzustellen. Möglicherweise bemerken Sie Änderungen in der Dreiecks Dichte in der Szene.</td>
  </tr>
  <tr>
    <td>Automatische Auswahl des Fokus Punkts basierend auf dem tiefen Puffer</td><td>Durch das Übermitteln eines tiefen Puffers an Windows kann hololens automatisch einen Fokuspunkt auswählen, um die – Hologramm-Stabilität zu optimieren.</td><td>Wechseln Sie in Unity zu <b>Edit > Project Settings > Player > universelle Windows-Plattform Tab > XR Settings</b>, erweitern Sie das <b>Windows Mixed Reality SDK</b> -Element, und vergewissern Sie sich, dass <b>Tiefe Puffer Freigabe aktivieren</b> aktiviert ist. Diese wird automatisch auf neue Projekte geprüft.<br><br>Stellen Sie bei DirectX-apps sicher, dass Sie die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer">CommitDirect3D11DepthBuffer</a> -Methode für <b>holographicrenderingparameters</b> jeden Frame aufzurufen, um Windows den tiefen Puffer bereitzustellen.
</td>
  </tr>
  <tr>
    <td>Holographic-neuprojektions Modi</td><td>Sie können nun die neuprojektion von Positionen auf hololens deaktivieren, um die hologrammstabilität von streng gesperrtem Inhalt, z. b. 360-Grad-Video, zu verbessern.</td><td>Legen Sie in Unity <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html">holographicsettings. reprojectionmode</a> auf <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html">holographikreprojectionmode. orientationonly</a> fest, wenn der gesamte Inhalt in der Ansicht streng gesperrt ist.<br><br>Legen Sie für DirectX-apps <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.reprojectionmode">holographiccamer-deringparameters. reprojectionmode</a> auf <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicreprojectionmode">holographikreprojectionmode. orientationonly</a> fest, wenn der gesamte Inhalt in der Ansicht ordnungsgemäß mit dem Text gesperrt ist.</td>
  </tr>
  <tr>
    <td>App-maßgeschneiderte APIs</td><td>Windows-APIs informieren darüber, wo Ihre APP ausgeführt wird, beispielsweise, ob die Geräte Anzeige transparent (hololens) oder nicht transparent (immersives Headset) ist und ob die 2D-Ansicht einer UWP-app in der Holographic Shell angezeigt wird.</td><td>In Unity war zuvor das manuelle Bereitstellen von <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html">holographicsettings. isdisplaytransparent</a> auf eine Weise möglich, die sogar vor diesem Build funktionierte.<br><br>Für DirectX-Apps können Sie nun auf vorhandene APIs wie <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.isopaque">holographicdisplay. GetDefault () zugreifen. IsOpaque</a> und <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview.iscurrentviewpresentedonholographicdisplay">holographicapplicationpreview. iscurrentviewpresentedonholographicdisplay</a> auch auf hololens.
</td>
  </tr>
  <tr>
      <td>Forschungs Modus</td><td>Ermöglicht Entwicklern den Zugriff auf Schlüssel hololens-Sensoren bei der Erstellung von akademischen und Industrieanwendungen zum Testen neuer Ideen in den Feldern von maschinellem sehen und Robotik, einschließlich:<ul><li>Die vier Umgebungs Überwachungskameras</li><li>Zwei Versionen der tiefen Zuordnung von Kameradaten</li><li>Zwei Versionen eines IR-Reflektivität-Streams</li></ul></td><td><a href="research-mode.md">Dokumentation zum Forschungs Modus</a><br><a href="https://github.com/Microsoft/HoloLensForCV">Beispiel-Apps für Forschungs Modus</a></td>
  </tr>
</table>

### <a name="for-commercial-customers"></a>Für kommerzielle Kunden

<table>
  <tr>
    <th>Feature</th><th>Details</th><th>Anweisungen</th>
  </tr>
  <tr>
    <td>Verwenden mehrerer Azure Active Directory Benutzerkonten auf einem einzelnen Gerät</td><td>Freigeben von hololens für mehrere Azure AD Benutzer, jeweils mit eigenen Benutzereinstellungen und Benutzerdaten auf dem Gerät.</td><td><a href="https://docs.microsoft.com/hololens/hololens-multiple-users">IT-Profi Center: Hololens für mehrere Personen freigeben</a></td>
  </tr>
  <tr>
    <td>Ändern des WLAN-Netzwerks bei der Anmeldung</td><td>Ändern Sie das WLAN-Netzwerk, bevor Sie sich anmelden, um es einem anderen Benutzer zu ermöglichen, sich zum ersten Mal mit seinem Azure AD Benutzerkonto anzumelden, sodass Benutzer Geräte an verschiedenen Standorten und Auftrags Standorten freigeben können.</td><td>Auf dem Anmeldebildschirm können Sie das Netzwerk Symbol unter dem Feld "Kennwort" verwenden, um eine Verbindung mit einem Netzwerk herzustellen. Dies ist hilfreich, wenn Sie sich zum ersten Mal bei einem Gerät anmelden.</td>
  </tr>
  <tr>
    <td>Einheitliche Registrierung</td><td>Es ist nun einfach für einen hololens-Benutzer, der das Gerät mit einer persönlichen Microsoft-Konto einrichtet, ein Geschäftskonto (Azure AD) hinzuzufügen und es dem MDM-Server hinzuzufügen.</td><td>Melden Sie sich einfach mit einem Azure AD Konto an, und die Registrierung erfolgt automatisch.</td>
  </tr>
  <tr>
    <td>E-Mail-Synchronisierung ohne MDM-Registrierung</td><td>Unterstützung für die Exchange Active Sync (EAS)-e-Mail-Synchronisierung ohne MDM-Registrierung.</td><td>Sie können jetzt e-Mails synchronisieren, ohne sich bei MDM anzumelden. Sie können das Gerät mit einem Microsoft-Konto einrichten, die e-Mail-app herunterladen und installieren und ein Geschäfts-e-Mail-Konto direkt hinzufügen.</td>
  </tr>
</table>

### <a name="for-it-pros"></a>Für IT-Spezialisten

<table>
  <tr>
    <th>Feature</th><th>Details</th><th>Anweisungen</th>
  </tr>
  <tr>
    <td>Neuer Betriebssystem Name "Windows Holographic for Business"</td><td>Löschen Sie die Editions Benennung, um Verwechslungen für Editions Upgrade zu reduzieren, wenn die Features der kommerziellen Suite auf hololens aktiviert sind.</td><td>In den <b>Einstellungen > System ></b>Info können Sie sehen, welche Edition von Windows Holographic auf Ihrem Gerät angezeigt wird. "Windows Holographic for Business" wird angezeigt, wenn ein Editions Update angewendet wurde, um die Features der kommerziellen Suite zu aktivieren. Erfahren Sie, wie Sie <a href="https://docs.microsoft.com/hololens/hololens-upgrade-enterprise">Windows Holographic for Business-Features entsperren</a>.</td>
  </tr>
  <tr>
  <td>Windows-Konfigurations-Designer (WCD)</td><td>Erstellen und bearbeiten Sie Bereitstellungs Pakete, um hololens über die aktualisierte WCD-APP zu konfigurieren. Einfacher hololens-Assistent für Editions Update, konfigurierbare OOBE, Region/Zeitzone, Massen Azure AD Token, Netzwerk und Entwickler-CSP. Erweiterter Editor ist nach hololens unterstützter Optionen, einschließlich zugewiesener Zugriffs-und Kontoverwaltungs-CSPs, gefiltert.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT-Profi Center: Konfigurieren von hololens mithilfe eines Bereitstellungs Pakets</a></td>
  </tr>
  <tr>
    <td>Konfigurierbares Setup (OOBE)</td><td>Ausblenden von Kalibrierung, Gesten/Blick-Schulungen und WLAN-Konfigurations Bildschirmen während des Setups.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning#create-a-provisioning-package-for-hololens-using-the-hololens-wizard">IT-Profi Center: Konfigurieren von hololens mithilfe eines Bereitstellungs Pakets</a></td>
  </tr>
  <tr>
    <td>Unterstützung für Massen Azure AD Token</td><td>Registrieren Sie das Gerät vorab bei Azure AD Directory-Mandanten, um den Flow für die Benutzer Installation zu beschleunigen</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT-Profi Center: Konfigurieren von hololens mithilfe eines Bereitstellungs Pakets</a></td>
  </tr>
  <tr>
  <td>DeveloperSetup-Konfigurationsdienstanbieter</td><td>Profil bereitstellen, um hololens im Entwicklermodus einzurichten. Nützlich für Entwicklungs-und Demogeräte.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT-Profi Center: Konfigurieren von hololens mithilfe eines Bereitstellungs Pakets</a></td>
  </tr>
  <tr>
  <td>AccountManagement-Konfigurationsdienstanbieter</td><td>Freigeben eines hololens-Geräts und Entfernen von Benutzerdaten nach Abmelde-oder Inaktivität/Speicher Schwellenwerten für die temporäre Verwendung. Unterstützt Azure Ad Konten.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT-Profi Center: Konfigurieren von hololens mithilfe eines Bereitstellungs Pakets</a></td>
  </tr>
  <tr>
  <td>Zugewiesener Zugriff</td><td>Von Windows zugewiesener Zugriff für erst zeilige Worker oder Demos. Sperre für eine einzelne oder mehrere apps. Der Entwickler muss nicht entsperrt werden.</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk">IT-Profi Center: Einrichten von hololens im Kiosk Modus</a></td>
  </tr>
  <tr>
  <td>Gast Zugriff für Kiosk Geräte</td><td>Windows hat Zugriff mit Kenn Wort losem Gastkonto für Demos zugewiesen. Sperre für eine einzelne oder mehrere apps. Der Entwickler muss nicht entsperrt werden.</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk#guest">IT-Profi Center: Einrichten von hololens im Kiosk Modus</a></td>
  </tr>
  <tr>
    <td>Einrichten der (OOBE)-Diagnose</td><td>Erhalten Sie Diagnoseprotokolle aus hololens, damit Sie Azure AD Anmelde Fehlern beheben können (bevor der Feedback-Hub für den Benutzer verfügbar ist, bei dem die Anmeldung fehlgeschlagen ist).</td><td>Wenn beim Setup oder bei der Anmeldung ein Fehler auftritt, wählen Sie die Option neue <b>Collect-Informationen</b> , um Diagnoseprotokolle für die Problembehandlung zu erhalten</td>
  </tr>
  <tr>
    <td>Nicht bestimmtes Kennwort für das lokale Konto</td><td>Entfernen der Unterbrechung der Geräte Zurücksetzung, wenn das Kennwort des lokalen Kontos</td><td>Wenn Sie ein lokales Konto bereitstellen, müssen Sie das Kennwort nicht mehr alle 42 Tage in den <b>Einstellungen</b>ändern, da das Konto Kennwort nicht mehr abläuft.</td>
  </tr>
  <tr>
    <td>MDM-Synchronisierungs Status und Details</td><td>Standard mäßige Windows-Funktionen, um den MDM-Synchronisierungs Status und Details in hololens zu verstehen.</td><td>Sie können den MDM-Synchronisierungs Status für ein Gerät unter Einstellungen > Konten überprüfen > auf Geschäfts- <b>oder Schul > Informationen zugreifen</b>. <b> Im Abschnitt <b>Geräte Synchronisierungs Status können Sie eine Synchronisierung starten, die von MDM verwalteten Bereiche anzeigen und einen erweiterten Diagnosebericht erstellen und exportieren.</td>
  </tr>
</table>

## <a name="known-issues"></a>Bekannte Probleme

Wir haben hart daran gearbeitet, eine großartige Windows Mixed Reality-Erfahrung bereitzustellen, aber wir verfolgen weiterhin einige bekannte Probleme. Wenn Sie andere finden, [Geben Sie uns Feedback](give-us-feedback.md).

### <a name="hololens"></a>HoloLens

#### <a name="after-update"></a>Nach dem Update

Nach dem Aktualisieren von RS1 auf RS4 auf Ihren hololens werden möglicherweise die folgenden Probleme feststellen:
* PIN- **zurück** Setzung: die 3X3-apps, die an Ihr Startmenü angeheftet werden, werden nach dem Update auf die Standardwerte zurückgesetzt 
* **Apps und platzierte holograms werden zurückgesetzt** : apps, die in ihrer Welt platziert werden, werden nach dem Update entfernt und müssen im gesamten Speicherplatz neu platziert werden. 
* Der **FeedHub kann nicht sofort** direkt nach dem Update gestartet werden. es dauert einige Minuten, bis Sie einige Posteingang-apps wie den Feedback-Hub starten können, während Sie sich selbst aktualisieren. 
* **WLAN-Unternehmens Zertifikate müssen neu synchronisiert werden** . Wir untersuchen ein Problem, das erfordert, dass die hololens mit einem anderen Netzwerk verbunden werden müssen, damit Unternehmens Zertifikate erneut mit dem Gerät synchronisiert werden können, bevor die Verbindung mit dem Unternehmen wieder hergestellt werden kann. Netzwerke, die Zertifikate verwenden. 
* **H. 265 hevc-Video Wiedergabe funktioniert nicht** : Anwendungen, die versuchen, h. 265-Videos wiederzugeben, erhalten eine Fehlermeldung. Sie können das Problem umgehen, indem Sie auf [das Windows-Geräte Portal zugreifen](using-the-windows-device-portal.md), auf der linken Navigationsleiste auf **apps** klicken und die hevc-Anwendung **Entfernen** . Installieren Sie dann die neueste [hevc-Video Erweiterung](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) aus der Microsoft Store. Wir untersuchen das Problem. 

#### <a name="for-developers-updating-hololens-apps-for-devices-running-windows-10-april-2018-update"></a>Für Entwickler: Aktualisieren von hololens-Apps für Geräte mit dem Windows 10-Update vom April 2018

Zusammen mit einer hervor artigen Liste [neuer Features](#new-features-for-hololens)erzwingt das Windows 10 April 2018 Update (RS4) für hololens einige Code Verhaltensweisen, die in früheren Versionen nicht aufgetreten sind:
* **Berechtigungsanforderungen zur Verwendung sensibler Ressourcen (Kamera, Mikrofon usw.)** -RS4 auf hololens erzwingt Berechtigungsanforderungen für apps, die auf sensible Ressourcen zugreifen möchten, z. b. auf die Kamera oder das Mikrofon. Von RS1 auf hololens wurden diese Aufforderungen nicht erzwungen. wenn die APP also den sofortigen Zugriff auf diese Ressourcen annimmt, stürzt Sie in "RS4" (selbst wenn der Benutzer die Berechtigung für die angeforderte Ressource erteilt) ab. Weitere Informationen finden Sie im [Artikel relevante UWP-App-Funktions Deklarationen](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations) .
* **Aufrufe von apps außerhalb ihrer eigenen** -RS4 in hololens erzwingen die ordnungsgemäße Verwendung der [ *Windows. System. Launcher* -Klasse](https://docs.microsoft.com/uwp/api/Windows.System.Launcher) , um eine andere APP von ihrer eigenen Anwendung zu starten. Wir haben beispielsweise Probleme mit Apps erkannt, die *Windows. System. Launcher. launchuriforresultionasync* von einem nicht-Asta-Thread (UI) aufrufen. Dies wäre in "RS1" bei hololens erfolgreich, aber für "RS4" ist es erforderlich, dass der-Befehl im UI-Thread ausgeführt wird.

### <a name="windows-mixed-reality-on-desktop"></a>Windows Mixed Reality auf dem Desktop

#### <a name="visual-quality"></a>Visuelle Qualität

* Wenn Sie nach dem Update von Windows 10 April 2018 bemerken, dass Grafiken weniger unscharf sind als zuvor, oder wenn das Sichtfeld auf Ihrem Headset kleiner aussieht, wurde möglicherweise die Automatische Leistungseinstellung geändert, um eine ausreichende Framerate für einen weniger leistungsfähigen Wert zu erhalten. Grafikkarte (z. b. NVIDIA 1050). Sie können dies manuell überschreiben (wenn Sie sich entscheiden), indem Sie zu **Einstellungen > Gemischte Realität Navigieren > Headset > Optionen anzeigen > ändern** und "automatisch" in "90 Hz" ändern. Sie können auch versuchen, die **visuelle Qualität** (auf der gleichen Seite Einstellungen) in "hoch" zu ändern.

#### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality-Setup

* Wenn Sie Windows mit einem mit einem Headset verbundenen Verbindungsaufbau einrichten, wird der PC-Monitor möglicherweise leer. Entfernen Sie Ihr Headset, um die Ausgabe an Ihren PC-Monitor zu aktivieren und Windows Setup abzuschließen.
* Wenn Sie keine Kopfhörer verbunden haben, können Sie beim ersten Besuch der Windows Mixed Reality-Startseite weitere Tipps übersehen.
* Andere Bluetooth-Geräte können zu Störungen bei Bewegungs Controllern führen. Wenn die Bewegungs Controller Probleme mit der Verbindung/Kopplung/Nachverfolgung haben, stellen Sie sicher, dass das Bluetooth-Radio (bei einem externen Dongle) an einem nicht gesperrte Speicherort angeschlossen ist und nicht direkt neben einem anderen Bluetooth-Ring. Versuchen Sie auch, andere Bluetooth-Peripheriegeräte während der Windows Mixed Reality-Sitzungen zu unterstützen, um zu ermitteln, ob dies hilft

#### <a name="games-and-apps-from-the-microsoft-store"></a>Spiele und Apps aus dem Microsoft Store

* Einige grafisch intensive Spiele, wie z. b. "Forza Motor 7", können bei der Wiedergabe in Windows Mixed Reality Leistungsprobleme auf weniger leistungsfähigen PCs verursachen.

#### <a name="audio"></a>Audio

* Wenn Cortana auf Ihrem Host-PC aktiviert ist, bevor Sie Ihr Windows Mixed Reality-Headset verwenden, verlieren Sie möglicherweise eine räumliche Audiosimulation, die auf die apps angewendet wird, die Sie in der Windows Mixed Reality-Startseite platzieren. 
   * Die Problem Umgehung besteht darin, "Windows Sonic for Kopfhörer" auf allen Audiogeräten zu aktivieren, die an Ihren PC angeschlossen sind, auch mit Ihrem mit dem Headset verbundenen Audiogerät:
      1. Klicken Sie in der Desktop-Taskleiste mit der linken Maustaste auf das Redner Symbol, und wählen Sie aus der Liste der Audiogeräte.
      2. Klicken Sie in der Desktop-Taskleiste mit der rechten Maustaste auf das Redner Symbol, und wählen Sie im Menü "sprechersetup" die Option "Windows-Sound für Kopfhörer"
      3. Wiederholen Sie diese Schritte für alle Ihre Audiogeräte (Endpunkte).
   * Eine weitere Option ist die Deaktivierung von Cortana auf "Hey Cortana" in den **Einstellungen** > **Cortana** auf Ihrem Desktop vor dem Starten von Windows Mixed Reality.
* Wenn ein anderes Multimedia-USB-Gerät (z. b. eine Web-Cam) denselben USB-Hub (entweder extern oder innerhalb Ihres PCs) mit dem Windows Mixed Reality-Headset gemeinsam nutzt, kann der AudioJack/-Kopfhörer des Headsets in seltenen Fällen entweder einen rauschenden Sound oder überhaupt keine Audiodaten enthalten. Sie können dies durch Ihr Headset an einem USB-Anschluss beheben, der nicht denselben Hub wie das andere Gerät verwendet, oder Sie können ihr anderes USB-Multimedia-Gerät trennen bzw. deaktivieren.
* In seltenen Fällen kann der USB-Hub des Host-PCs nicht genügend Stromversorgung für das Windows Mixed Reality-Headset bereitstellen, und Sie bemerken möglicherweise einen Burst Rausch von dem mit dem Headset verbundenen Kopfhörer.

#### <a name="holograms"></a>Hologramme

* Wenn Sie in Ihrer Windows Mixed Reality-Homepage eine große Anzahl von holograms platziert haben, werden einige möglicherweise nicht mehr angezeigt, und Sie werden bei der Suche wieder angezeigt. Um dies zu vermeiden, entfernen Sie einige der Hologramme in diesem Bereich des Windows Mixed Reality-Home.

#### <a name="motion-controllers"></a>Motion-Controller

* Wenn die Eingabe nicht an das Headset weitergeleitet wird, wird der Motion-Controller kurz ausgeblendet, wenn er neben der Raumgrenze gehalten wird. Wenn Sie "Win + Y" drücken, um sicherzustellen, dass ein blaues Banner über den Desktop Monitor verfügt, wird dies behoben. 
* Wenn Sie in Microsoft Edge auf eine Webseite klicken, wird der Inhalt manchmal vergrößert, anstatt auf "Click".

#### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Desktop-app in der Windows Mixed Reality-Startseite

* Das Snipping-Tool funktioniert nicht in der Desktop-App.
* Die Einstellung für die Desktop-App wird beim erneuten Starten nicht beibehalten.
* Wenn Sie auf Ihrem Desktop die Mixed Reality Portal Preview-Version verwenden, können Sie beim Öffnen der Desktop-app in der Windows Mixed Reality-Startseite den unendlichen Spiegeleffekt bemerken. 
* Das Ausführen der Desktop-App kann bei nicht-Ultra-Windows Mixed Reality-PCs zu Leistungsproblemen führen. Dies wird nicht empfohlen.  
* Die Desktop-App kann automatisch gestartet werden, da ein unsichtbares Fenster auf dem Desktop den Fokus besitzt. 
* Bei der Eingabeaufforderung für die Desktop Benutzerkontensteuerung wird das Headset schwarz angezeigt, bis die Eingabeaufforderung abgeschlossen ist.

#### <a name="windows-mixed-reality-for-steamvr"></a>Windows Mixed Reality für steamvr

* Möglicherweise müssen Sie nach der Aktualisierung das Mixed Reality-Portal starten, um sicherzustellen, dass die erforderlichen Software Updates für das Windows 10-Update vom April 2018 abgeschlossen sind, bevor Sie steamvr starten 
* Sie müssen über eine aktuelle Version von Windows Mixed Reality für steamvr verfügen, damit Sie mit dem Windows 10-Update vom April 2018 kompatibel bleiben. Stellen Sie sicher, dass automatische Updates für Windows Mixed Reality für steamvr aktiviert sind, das sich im Abschnitt "Software" Ihrer Bibliothek in "Steam" befindet.  

#### <a name="other-issues"></a>Andere Probleme

>[!IMPORTANT]
>In einer frühen Version des Windows 10 April 2018-Updates, das an Insider (Version 17134,5) übermittelt wurde, fehlte eine Software, die für die Ausführung von Windows Mixed Reality erforderlich war. Wenn Sie Windows Mixed Reality verwenden, empfiehlt es sich, diese Version zu vermeiden. 

Wir haben bei der ersten Veröffentlichung dieses Updates (10.0.17134.1) eine Leistungs Regression bei der Verwendung von Surface Book 2 festgestellt, die wir in einem bevorstehenden Update Patch korrigieren werden. Wir empfehlen, dass Sie warten, bis dies behoben wurde, bevor Sie manuell aktualisiert werden, oder wenn Sie darauf warten, dass der Aktualisierungs Rollout

## <a name="provide-feedback-and-report-issues"></a>Bereitstellen von Feedback und melden von Problemen

Verwenden Sie die [Feedback-Hub-App auf Ihren hololens oder Windows 10-PCs](give-us-feedback.md) , um Feedback zu geben und Probleme zu melden. Die Verwendung von Feedback Hub stellt sicher, dass alle erforderlichen Diagnoseinformationen enthalten sind, damit unsere Techniker das Problem schnell Debuggen und beheben können.

>[!NOTE]
>Stellen Sie sicher, dass Sie die Eingabeaufforderung akzeptieren, in der Sie gefragt werden, ob der Feedback- Hub auf den Ordner "Dokumente" zugreifen soll.

## <a name="prior-release-notes"></a>Vorherige Anmerkungen zu dieser Version

* [Versionshinweise – Oktober 2017](release-notes-october-2017.md)
* [Versionshinweise – August 2016](release-notes-august-2016.md)
* [Versionshinweise – Mai 2016](release-notes-may-2016.md)
* [Versionshinweise – März 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Siehe auch
* [Immersive Headset-Unterstützung (externer Link)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Hololens-Unterstützung (externer Link)](https://support.microsoft.com/products/hololens)
* [Installieren der Tools](install-the-tools.md)
* [Feedback senden](give-us-feedback.md)

