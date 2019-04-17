---
title: Anmerkungen zu dieser Version – April 2018
description: HoloLens und Windows Mixed Reality-Versionshinweise für Windows 10 April 2018 zu aktualisieren (auch bekannt als RS4).
author: mattzmsft
ms.author: mazeller
ms.date: 05/21/2018
ms.topic: article
keywords: Freigeben der Anmerkungen zu dieser Version, Version, Windows 10, Build, rs4, Betriebssystem
ms.openlocfilehash: 1fc1b43b0581234e835379fd553b78121108086e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594596"
---
# <a name="release-notes---april-2018"></a>Anmerkungen zu dieser Version – April 2018

Die **[Windows 10 April 2018 Update](https://blogs.windows.com/windowsexperience/2018/04/30/whats-new-in-the-windows-10-april-2018-update)** (auch bekannt als RS4) bietet neue Features für HoloLens und Windows Mixed Reality immersive Headsets mit PCs. 

Um auf das neueste Release für alle Geräte zu aktualisieren, öffnen die **Einstellungen** wechseln Sie zur app **Update und Sicherheit**, und wählen Sie dann die **nach Updates suchen** Schaltfläche. Auf einem Windows 10-PC, können Sie auch manuell installieren der Windows 10 April 2018 Aktualisieren mit der [Tool zur Erstellung von Windows Media](https://www.microsoft.com/software-download/windows10).

**Neueste Release für den Desktop:** Windows 10 April 2018 Update (**10.0.17134.1**)<br>
**Neueste Release für HoloLens:** Windows 10 April 2018 Update (**10.0.17134.80**)<br>
<br>

>[!VIDEO https://www.youtube.com/embed/O-84oWjSbr0]

*Aktualisieren von einer Nachricht von Alex Kipman und Übersicht über die neuen mixed Reality-Features in Windows 10 April 2018*

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Neue Features für immersive Headsets Windows Mixed Reality

Windows 10 April 2018 Update enthält zahlreiche Verbesserungen für die Verwendung von Windows Mixed Reality immersive (VR) Headsets mit Ihrem desktop-PC, z.B.: 

* **Neue Umgebungen für die gemischte Realität home** – jetzt können Sie zwischen den Cliff House und die neue Umgebung für Skyloft dazu **stellen** im Startmenü. Wir haben außerdem hinzugefügt [ein experimentelles Feature](add-custom-home-environments.md) wird, mit denen Sie die benutzerdefinierte Umgebungen verwenden Sie erstellt haben.
* **Schnellzugriff auf mixed Reality-Erfassung** – Sie können jetzt Fotografieren mixed Reality mit Controller während der Übertragung. Halten Sie die Windows-Schaltfläche, und tippen Sie dann auf den Trigger. Dies funktioniert über Umgebungen hinweg und apps, aber mit DRM geschützte Inhalte werden nicht erfasst.
* **Neue Optionen für den Start und das Ändern der Größe von Inhalt** -Apps werden jetzt automatisch platziert vor Ihnen, wenn Sie über das Startmenü starten. Sie können jetzt auch die Direct2D-apps ändern, durch Ziehen der Ränder und Ecken des Fensters.
* **Leicht zu Inhalten mit "Teleport" Voice-Befehl wechseln** – Sie können jetzt schnell Teleport vor Inhalt in die Windows Mixed Reality home werden durch gazing Inhalt und dem Spruch "Teleport."
* **[Animierte 3D app-startfeldern von](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#animation-guidelines) und [dekorativen 3D-Objekte](enable-placement-of-3d-models-in-the-home.md) für die gemischte Realität home** -können Sie jetzt das Hinzufügen von Animationen, 3D app-startfeldern von und ermöglichen Benutzern, platzieren Sie dekorative 3D-Modelle von einer Webseite oder 2D-app in der Windows Mixed Reality home.
* **[Verbesserungen an Windows Mixed Reality für SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md)**  -Windows Mixed Reality für SteamVR je MIMO "early Access" mit neuen Aktualisierungen, einschließlich: Übermitteln von haptischem Feedback bei Verwendung von Motion-Controller, verbesserte Leistung und Zuverlässigkeit, und Verbesserungen an der Darstellung der Motion-Controller im SteamVR.
* **Weitere Verbesserungen** -automatische Leistungseinstellungen wurden aktualisiert, um eine optimierte Erfahrung zu bieten (Sie können [manuell überschreiben](#visual-quality) mit dieser Einstellung). -Setup bietet nun Ausführlichere Informationen über häufige Kompatibilitätsprobleme mit USB 3.0-Karten für Controller und Grafiken.

## <a name="new-features-for-hololens"></a>Neue Features für HoloLens

Windows 10 April 2018 Update ist für alle Kunden, die HoloLens eingetroffen! Dieses Update enthält eine Vielzahl von Verbesserungen, die seit der letzten Hauptversion von HoloLens-Software in eingeführt wurden [August 2016](release-notes-august-2016.md).

### <a name="for-everyone"></a>Für alle Benutzer

<table>
  <tr>
    <th>Feature</th><th>Details</th><th>Anweisungen</th>
  </tr>
  <tr>
    <td>Automatische platzierungsalgorithmus von 2D- und 3D-Spiele Inhalten beim Start</td><td>Eine Direct2D-app-Startfeld oder 2D UWP-app automatisch – stellen in der ganzen Welt auf eine optimale Größe und der Entfernung, die beim Starten anstatt den Benutzer platzieren. Wenn ein <a href="app-views.md">umfassenden app</a> verwendet ein Direct2D-app-Startprogramm anstelle von einer <a href="3d-app-launcher-design-guidance.md">-3D-app-Startfeld</a>, die umfassenden app wird automatisch starten aus dem Direct2D-app-Startfeld identisch wie RS1.<br><br>Ein-3D-app-Startfeld über das Startmenü Auto-stellen auch in der ganzen Welt. Benutzer können für das Startprogramm zum Starten der immersiven app anstelle der automatischen Starts der app, klicken Sie auf. Geöffnet, aus der app Hologramme und Edge-3D-Inhalte automatisch – stellen auch in der ganzen Welt.</td><td>Wenn Sie eine app über das Startmenü zu öffnen, werden Sie nicht mehr an der ganzen Welt platzieren aufgefordert.<br><br>Wenn die Direct2D-app /<a href="3d-app-launcher-design-guidance.md">-3D-app-Startfeld</a> Platzierung nicht optimal ist, können Sie problemlos wechseln sie mit der neuen flüssige app Bearbeitungen, die unten beschriebenen. Sie können auch neu positionieren den Direct2D-app-Startfeld/3D-Inhalt indem sagen "dieses verschieben" und dann Blicke, um den Inhalt neu zu positionieren.</td>
  </tr>
  <tr>
    <td>Dynamisches app bearbeiten</td><td>Verschieben Sie, skalieren Sie und rotieren Sie 2D-und 3D-Inhalt ohne Eingabe von "Anpassen" Modus.</td><td>Um eine Direct2D-UWP-app oder eine Direct2D-app-Startprogramm zu verschieben, bestaunen Sie einfach an die appleiste und verwenden Sie dann das Tap halten Sie und ziehen Sie die Bewegung. Sie-3D-Inhalte durch gazing an einer beliebigen Stelle auf das Objekt verschieben können, und tippen Sie auf + enthalten + ziehen Sie dann.<br><br>Zum Ändern der Größe 2D-Inhalt bestaunen Sie in die Ecke. Der Blicke-Cursor wird in einen Größenänderungscursor aktivieren, und klicken Sie dann können Sie tippen Sie auf + halten und ziehen Sie zum Ändern der Größe. Sie können auch 2D-Inhalt Höhe oder Breite vornehmen, indem an den Rändern suchen, und ziehen.<br><br>-3D-Inhalte zu ändern, heben Sie sich beide in Ihren Händen in Bewegung dataframe, Finger an der Position bereit. Sie sehen, dass den Cursor in einen Zustand mit 2 wenig Händen zu aktivieren. Führen Sie das Tap, und halten Sie die Geste mit sowohl der Hand. Verschieben Sie sich näher oder weiter auseinander werden Sie die Größe des Objekts ändern. Verschieben Ihre Hände vorwärts und rückwärts im Verhältnis zueinander wird das Objekt zu drehen. Sie können auch ändern der Größe/2D-Inhalt auf diese Weise drehen.</td>
  </tr>
  <tr>
    <td>Direct2D-app horizontal skalieren mit geänderte flussrichtung</td><td>Stellen Sie eine 2D UWP-app, die größere Seitenverhältnis nutzen, um weitere app-Inhalte anzuzeigen. Beispiel dafür wäre die Mail-app, die breit genug ist, im Vorschaufenster angezeigt.</td><td>Bestaunen Sie einfach am linken oder rechten Rand der 2D UWP-app, finden Sie unter der Größenänderungscursor und klicken Sie dann verwenden Sie das Tap halten und ziehen die Aktion zum Ändern der Größe.</td>
  </tr>
  <tr>
    <td>Erweiterte Voice-befehlsunterstützung</td><td>Sie können dazu weitere einfach Ihre Stimme.</td><td>Probieren Sie diese Sprachbefehle:<ul><li>"Gehe zu" Start": wird im Startmenü oder beendet eine <a href="app-views.md">umfassenden app</a>.</li><li>"Dies verschieben" - können Sie ein Objekt zu verschieben.</li></ul></td>
  </tr>
  <tr>
    <td>Aktualisierte Hologramme und Fotos-apps</td><td>Aktualisierte Hologramme-app mit neuen Hologramme. Aktualisierte Fotos-app.</td><td>Sie sehen, dass ein neues Aussehen für die apps-Hologramme und Fotos. Die Hologramme-app enthält mehrere neue Hologramme und eine Bezeichnung-Hersteller für einfachere Erstellung von Text.</td>
  </tr>
  <tr>
    <td>Verbesserte mixed Reality-Erfassung</td><td>Hardware-Kontextmenü-Start und Ende MRC video.</td><td>Halten Sie lauter + nach unten bei 3 Sekunden zum Starten der Aufzeichnung MRC-Video. Beide Tippen Sie erneut auf, oder verwenden Sie die Bewegung Bloom, um zu beenden.</td>
  </tr>
  <tr>
    <td>Konsolidierte Leerzeichen</td><td>Vereinfachen Sie die Verwaltung des Adressraums für Hologramme in ein einzelnes Leerzeichen.</td><td>HoloLens sucht nach der Speicherplatz wird automatisch und erfordert nicht mehr verwaltet, oder wählen Sie die Leerzeichen. Wenn Sie Probleme mit Hologramme auf Sie haben, wechseln Sie zu <b>Einstellungen > System > Hologramme > Entfernen Sie in der Nähe Hologramme</b>. Bei Bedarf können Sie auch wählen <b>entfernen Sie alle Hologramme</b>.</td>
  </tr>
  <tr>
    <td>Verbessertes audio immersion</td><td>Sie können jetzt besser hören von HoloLens in entsprechende abweichungen auf, Umgebungen und mehr immer immersivere Sound von Anwendungen auftreten, wie ihre Sound durch echte Wände erkannt, die vom Gerät verdeckt werden wird.</td><td>Sie müssen nichts tun, um verbesserte räumliche Sounds zu nutzen.</td>
  </tr>
  <tr>
    <td>Datei-Explorer</td><td>Verschieben und Löschen von Dateien in HoloLens.</td><td>Sie können die <b>Datei-Explorer</b> verschieben und Löschen von Dateien aus HoloLens-app.<br><br><b>Tipp:</b> Wenn Sie nicht, dass alle Dateien sehen, die "Zuletzt verwendet"-Filter aktiv sein (Uhrsymbol wird im linken Bereich hervorgehoben). Wählen Sie zum Beheben der <b>dieses Gerät</b> dokumentieren Symbol im linken Bereich (unterhalb der Uhrsymbol), oder öffnen Sie das Menü, und wählen <b>dieses Gerät</b>.
</td>
  </tr>
  <tr>
    <td>Unterstützung von MTP (Media Transfer Protocol)</td><td>Können Ihre Bibliotheken (Fotos, Videos, Dokumente) den Zugriff auf Ihrem desktop-PC für HoloLens für die einfache Übertragung an.</td><td>Ähnlich wie andere mobile Geräte, die HoloLens Herstellen einer Verbindung mit Ihrem PC, um <b>Datei-Explorer</b> auf EasyTransfer von HoloLens-Bibliotheken (Fotos, Videos, Dokumente) zugreifen.<br><br><b>Tipps:</b><ul><li>Wenn Sie alle Dateien nicht sehen, stellen Sie sicher, dass Sie zu Ihrem HoloLens melden Sie sich beim Zugriff auf Ihre Daten zu aktivieren.</li><li>Von <b>Datei-Explorer</b> auf Ihrem PC, Sie können auswählen, <b>Geräteeigenschaften</b> auf Windows Holographic-Betriebssystem-Versionsnummer (Firmwareversion) und die Seriennummer des Geräts finden Sie unter.</li></ul><b>Bekanntes Problem:</b> Umbenennen von HoloLens über <b>Datei-Explorer</b> auf Ihrem PC ist nicht aktiviert.</td>
  </tr>
  <tr>
    <td>Captive Portal Netzwerkunterstützung während des Setups</td><td>Sie können jetzt festlegen, um Ihre HoloLens in einem Gast-Netzwerk auf Hotels, Konferenz Rechenzentren, Einzelhändlern oder Unternehmen, die captive Portal verwenden.</td><td>Wählen Sie das Netzwerk, überprüfen Sie bei Bedarf automatisch zu verbinden, und geben Sie die Netzwerkinformationen, wie Sie dazu aufgefordert werden, während des Setups.</td>
  </tr>
  <tr>
    <td>Fotos und Videos Synchronisierung über OneDrive-app</td><td>Ihre Fotos und Videos von HoloLens werden jetzt über die OneDrive-app aus dem Microsoft Store nicht direkt über die Fotos-app synchronisiert.</td><td>Um dies einzurichten, laden Sie, und starten Sie die OneDrive-app aus dem Store. Bei der ersten Ausführung sollten Sie aufgefordert, die automatisch Ihre Fotos in OneDrive hochgeladen werden, oder die Option finden Sie in den app-Einstellungen.</td>
  </tr>
</table>

### <a name="for-developers"></a>Für Entwickler

<table>
  <tr>
    <th>Feature</th><th>Details</th><th>Anweisungen</th>
  </tr>
  <tr>
    <td>Verbesserungen der räumliche Zuordnung</td><td>Verbesserungen der Qualität, Leistung und Vereinfachung.</td><td>Räumliche Zuordnung Mesh übersichtlichere angezeigt – weniger Dreiecke sind erforderlich, um die gleichen Detailebene darstellen. Sie können Änderungen bemerken, Dreieck Dichte in der Szene.</td>
  </tr>
  <tr>
    <td>Automatische Auswahl des Fokuspunkt basierend auf Tiefenpuffer</td><td>Ermöglicht das Senden eines Tiefenpuffer Windows HoloLens, wählen Sie den Fokuspunkt-zu-automatisch – Hologramm Stabilität zu optimieren.</td><td>Wechseln Sie in Unity zu <b>Bearbeiten > Projekteinstellungen > Player > Registerkarte für die universelle Windows-Plattform > XR-Einstellungen</b>, erweitern Sie die <b>Windows Mixed Reality-SDK</b> Element aus, und stellen Sie sicher <b>Tiefenpuffer aktivieren Freigeben von</b> aktiviert ist. Dies wird automatisch für neue Projekte überprüft werden.<br><br>Stellen Sie sicher für DirectX-apps, rufen Sie die <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer">CommitDirect3D11DepthBuffer </a> Methode für <b>HolographicRenderingParameters</b> jeden Frame zum Angeben des Tiefe-Puffers, in Windows.
</td>
  </tr>
  <tr>
    <td>Holographic Reprojection-Modi</td><td>Sie können jetzt mit Feldern fester Breite Reprojection für HoloLens zur Verbesserung der Stabilität – Hologramm fest gesperrt Text-Inhalt, wie der 360-Grad-Video deaktivieren.</td><td>Legen Sie in Unity <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html">HolographicSettings.ReprojectionMode</a> zu <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html">HolographicReprojectionMode.OrientationOnly</a> Wenn alle Inhalte in der Ansicht sind fest mit Text gesperrt.<br><br>Legen Sie für die DirectX-apps, <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.reprojectionmode"> HolographicCameraRenderingParameters.ReprojectionMode</a> zu <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicreprojectionmode">HolographicReprojectionMode.OrientationOnly</a> Wenn alle Inhalte in der Ansicht sind fest mit Text gesperrt.</td>
  </tr>
  <tr>
    <td>App-Kollatierungsanpassungen-APIs</td><td>Windows-APIs wissen mehr dazu, in denen Ihre app ausgeführt wird, z. B., ob der Anzeige des Geräts transparent (HoloLens) oder deckend (immersive Kopfhörer) ist, und gibt an, ob eine UWP-app-2D-Ansicht in der holografischen Shell angezeigt wird.</td><td>Unity haben, zuvor manuell verfügbar gemachten <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html">HolographicSettings.IsDisplayOpaque</a> in einer Weise, die diesem Build noch gearbeitet.<br><br>Für DirectX-apps können Sie jetzt auf vorhandenen APIs wie z. B. zugreifen <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.isopaque">HolographicDisplay.GetDefault(). IsOpaque</a> und <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview.iscurrentviewpresentedonholographicdisplay">HolographicApplicationPreview.IsCurrentViewPresentedOnHolographicDisplay</a> auf und HoloLens.
</td>
  </tr>
  <tr>
      <td>Research-Modus</td><td>Ermöglicht es Entwicklern, die wichtige HoloLens Sensoren zugreifen, beim Erstellen von academic und gewerbliche Anwendungen So testen Sie neue Ideen in die Felder der maschinelles sehen und Robotik angewendet, einschließlich:<ul><li>Die vier Kameras nachverfolgung Umgebung</li><li>Zwei Versionen der Tiefe Kamera Zuordnungsdaten</li><li>Zwei Versionen des eine IR-Reflexionsvermögen Streams</li></ul></td><td><a href="research-mode.md">Research-Modus-Dokumentation</a><br><a href="https://github.com/Microsoft/HoloLensForCV">Research-Modus-Beispiel-apps</a></td>
  </tr>
</table>

### <a name="for-commercial-customers"></a>Für Geschäftskunden

<table>
  <tr>
    <th>Feature</th><th>Details</th><th>Anweisungen</th>
  </tr>
  <tr>
    <td>Verwenden Sie mehrere Azure Active Directory-Benutzerkonten auf einem einzelnen Gerät</td><td>Freigeben Sie eine HoloLens für mehrere Azure AD-Benutzer mit ihren eigenen Einstellungen und Benutzerdaten auf Gerät.</td><td><a href="https://docs.microsoft.com/hololens/hololens-multiple-users">IT Pro-Center: Freigabe HoloLens für mehrere Personen</a></td>
  </tr>
  <tr>
    <td>Ändern Sie Wi-Fi-Netzwerk bei Anmeldung</td><td>Ändern Sie Wi-Fi-Netzwerk vor der Anmeldung eine andere Benutzer ermöglichen, melden Sie sich mit seinem Azure AD-Kontos, zum ersten Mal, sodass Benutzer Geräte an verschiedenen Standorten gemeinsam nutzen und Projekt-Sites.</td><td>Klicken Sie auf der Anmeldeseite angezeigt können das Symbol "Netzwerk" unter dem Feld "Kennwort" Sie mit einem Netzwerk verbinden. Dies ist hilfreich, wenn dies zum ersten Mal anmelden bei einem Gerät ist.</td>
  </tr>
  <tr>
    <td>Einheitliche Registrierung</td><td>Es ist nun einfach ein HoloLens-Benutzer, der das Gerät mit einem persönlichen Microsoft-Konto zum Hinzufügen eines Geschäftskontos (Azure AD) und verknüpfen das Gerät mit ihrer MDM-Server einrichten.</td><td>Melden Sie sich mit einem Azure AD-Konto, und die Registrierung erfolgt automatisch.</td>
  </tr>
  <tr>
    <td>E-Mail-Synchronisierung ohne MDM-Registrierung</td><td>Unterstützung für Exchange Active Sync (EAS) e-Mail-Synchronisierung ohne MDM-Registrierung.</td><td>Sie können e-Mail-Adresse jetzt synchronisieren, ohne Registrierung in der Verwaltung mobiler Geräte. Sie können Einrichten des Geräts mit einem Microsoft Account, herunterladen und installieren die Mail-app, und fügen Sie direkt ein geschäftliches e-Mail-Konto hinzu.</td>
  </tr>
</table>

### <a name="for-it-pros"></a>Für IT-Spezialisten

<table>
  <tr>
    <th>Feature</th><th>Details</th><th>Anweisungen</th>
  </tr>
  <tr>
    <td>Neue "Windows Holographic for Business" Betriebssystem-name</td><td>Deaktivieren Sie die Edition zu benennen, um Verwirrung Edition-Lizenz für das Upgrade-Anwendung zu verringern, wenn HoloLens Commercial Suite-Features aktiviert werden.</td><td>Sie sehen, welche Edition von Windows Holographic auf Ihrem Gerät in <b>Einstellungen > System > zu</b>. "Windows Holographic for Business" wird angezeigt, wenn ein Edition Update angewendet wurde, um die Commercial Suite-Funktionen zu aktivieren. Erfahren Sie, wie Sie <a href="https://docs.microsoft.com/hololens/hololens-upgrade-enterprise">Entsperren von Windows Holographic for Business-Features</a>.</td>
  </tr>
  <tr>
  <td>Windows Configuration Designer (WCD)</td><td>Erstellen und Bearbeiten von Bereitstellungspaketen um HoloLens über aktualisierte WCD-app zu konfigurieren. Einfache HoloLens-Assistent für die Edition aktualisieren, konfigurierbare OOBE, Region/Zeitzone, Bulk-Azure AD-Token, Netzwerk und CSP-Entwickler. Erweiterter Editor gefiltert nach HoloLens unterstützt Optionen, einschließlich der zugewiesenen Zugriff und Konto Management CSPs.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro-Center: Konfigurieren Sie HoloLens, die mithilfe eines Bereitstellungspakets</a></td>
  </tr>
  <tr>
    <td>Konfiguriert Setup (OOBE)</td><td>Ausblenden von Kalibrierung, Geste/Blicke Trainings- und Wi-Fi-Konfigurationsbildschirme während des Setups.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning#create-a-provisioning-package-for-hololens-using-the-hololens-wizard">IT Pro-Center: Konfigurieren Sie HoloLens, die mithilfe eines Bereitstellungspakets</a></td>
  </tr>
  <tr>
    <td>Massenimport von Azure AD-token-Unterstützung</td><td>Registrieren Sie Geräte auf Azure AD-Mandanten für schnellere benutzerflow Setup aus.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro-Center: Konfigurieren Sie HoloLens, die mithilfe eines Bereitstellungspakets</a></td>
  </tr>
  <tr>
  <td>DeveloperSetup-Konfigurationsdienstanbieter</td><td>Bereitstellen von Profil HoloLens im Entwicklermodus einrichten. Ist nützlich für Entwicklung und Demo-Geräte.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro-Center: Konfigurieren Sie HoloLens, die mithilfe eines Bereitstellungspakets</a></td>
  </tr>
  <tr>
  <td>AccountManagement-Konfigurationsdienstanbieter</td><td>Freigeben einer HoloLens-Gerät, und Entfernen von Benutzerdaten nach dem Abmelden oder Inaktivität/Storage Schwellenwerte zur vorübergehenden Verwendung. Unterstützt die Azure AD-Konten.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro-Center: Konfigurieren Sie HoloLens, die mithilfe eines Bereitstellungspakets</a></td>
  </tr>
  <tr>
  <td>Zugewiesener Zugriff</td><td>Windows, die Zugriff für Mitarbeiter der ersten Zeile oder Demos zugewiesen werden. Einzelne oder mehrere app-sperren. Keine Notwendigkeit für Entwickler entsperren.</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk">IT Pro-Center: Einrichten von HoloLens im Kiosk-Modus</a></td>
  </tr>
  <tr>
  <td>Gastzugriff für Kiosk-Geräte</td><td>Zugriff mit Gastkontos ohne Kennwort für Demos wird von Windows zugewiesen. Einzelne oder mehrere app-sperren. Keine Notwendigkeit für Entwickler entsperren.</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk#guest">IT Pro-Center: Einrichten von HoloLens im Kiosk-Modus</a></td>
  </tr>
  <tr>
    <td>Einrichten der Diagnose von (OOBE)</td><td>Erhalten Sie Diagnoseprotokolle von HoloLens, damit Sie Azure AD-Anmeldung Beheben von Fehlern bei können (bevor die Feedback-Hub für den Benutzer, deren Anmeldung konnte nicht, verfügbar ist).</td><td>Beim Setup oder der Anmeldung ein Fehler auftritt, wählen Sie den neuen <b>sammelt Informationen</b> Option aus, um die Diagnoseprotokolle für die Problembehandlung zu erhalten.</td>
  </tr>
  <tr>
    <td>Lokales Konto auf unbestimmte Kennwortablauf</td><td>Entfernen Sie die Unterbrechung des Geräts zurückgesetzt, wenn ein lokales Kennwort abläuft.</td><td>Bei der Bereitstellung eines lokalen Kontos nicht mehr benötigten zum Ändern des Kennworts 42 Tage in <b>Einstellungen</b>, wie Sie das Kennwort für das laufen nicht mehr ab.</td>
  </tr>
  <tr>
    <td>Synchronisierungsstatus für die Verwaltung mobiler Geräte und details</td><td>Standardmäßige Windows-Funktionalität zum Synchronisierungsstatus für die Verwaltung mobiler Geräte und Details in HoloLens zu verstehen.</td><td>Sehen Sie die MDM-Synchronisierungsstatus für ein Gerät in <b>Einstellungen > Konten > Zugriff auf Geschäfts-, Schul- oder Unikonto > Info</b>. In der <b>des gerätesynchronisierungsstatus<b> Abschnitt, Sie können eine Synchronisierung zu starten, finden Sie unter Bereiche, die von MDM verwaltet werden und erstellen und exportieren Sie einen Bericht für die erweiterte Diagnose.</td>
  </tr>
</table>

## <a name="known-issues"></a>Bekannte Probleme

Wir haben hart daran gearbeitet, um eine hervorragende Windows Mixed Reality-Erfahrung zu bieten, aber verfolgen wir noch einige bekannte Probleme. Wenn Sie andere Benutzer finden, wenden Sie [senden Sie uns Feedback](give-us-feedback.md).

### <a name="hololens"></a>HoloLens

#### <a name="after-update"></a>Nach dem update

Sie können die folgenden Probleme feststellen, nach dem Upgrade von RS1 auf Version RS4 auf Ihre HoloLens:
* **Zurücksetzen von Pins** -3 x 3-apps, die an Ihr Startmenü angeheftet wird nach dem Update auf die Standardwerte zurückgesetzt. 
* **Apps und Zurücksetzen der platzierten Hologramme** -Apps, die in Ihre Welt platziert wird nach der Aktualisierung entfernt und erneut in Ihrem Bereich platziert werden müssen. 
* **Feedback-Hub kann nicht sofort starten** -unmittelbar nach dem Update, es wird einige Minuten dauern, bevor Sie sich einige Posteingang-apps wie Feedback-Hub, starten, während sie aktualisiert werden können. 
* **Unternehmen Wi-Fi-Zertifikate müssen erneut synchronisiert werden** – wir untersuchen ein Problem, das erfordert die HoloLens verbunden sein, mit einem anderen Netzwerk in der Reihenfolge für Unternehmen Zertifikate, die an das Gerät erneut synchronisiert werden, bevor er eine Verbindung mit herstellen kann Unternehmensnetzwerke mithilfe von Zertifikaten. 
* **265 HEVC-Video-Wiedergabe funktioniert nicht** -Anwendungen, die versuchen, die zum Wiedergeben von 265 Videos erhalten eine Fehlermeldung angezeigt. Die problemumgehung besteht darin, [Zugriff auf die Windows Device Portal](using-the-windows-device-portal.md)Option **Apps** auf der linken Navigationsleiste auf und **entfernen** die HEVC-Anwendung. Installieren Sie dann auf die neueste Version [HEVC-Video-Erweiterung](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) aus dem Microsoft Store. Wir untersuchen das Problem. 

#### <a name="for-developers-updating-hololens-apps-for-devices-running-windows-10-april-2018-update"></a>Für Entwickler: Aktualisieren von HoloLens-apps für Geräte unter Windows 10 April 2018 aktualisieren

Sowie eine umfassende Liste von [neue Features](#new-features-for-hololens), das Windows 10 April 2018 Update (RS4) für HoloLens erzwingt einige Code-Verhaltensweisen, die nicht von frühere Versionen:
* **Berechtigungsanforderungen zu sensiblen Ressourcen (Kamera, Mikrofon, usw.).**  -Version RS4 für HoloLens erzwingt die berechtigungsanforderungen für apps, die auf vertrauliche Ressourcen, z. B. Kamera oder Mikrofon beabsichtigt. Rs1 für HoloLens nicht erzwingen, dass diese aufforderungen, also wenn der sofortigen Zugriff auf diese Ressourcen in Ihrer app geht davon aus, es stürzt möglicherweise ab, in Version RS4 (selbst wenn der Benutzer die Berechtigung für die angeforderte Ressource gewährt). Lesen Sie die relevanten [UWP-app-Funktion Deklarationen Artikel](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations) für Weitere Informationen.
* **Aufrufe an apps außerhalb Ihrer eigenen** -Version RS4 für HoloLens erzwingt die ordnungsgemäßen Verwendung von der [ *Windows.System.Launcher* Klasse](https://docs.microsoft.com/uwp/api/Windows.System.Launcher) zum Starten einer anderen app aus Ihren eigenen. Wir haben z. B. Probleme mit apps, die aufrufen gesehen *Windows.System.Launcher.LaunchUriForResultsAsync* von einem nicht - ASTA-UI-Thread. Dies wäre in RS1 für HoloLens erfolgreich, aber Version RS4 erfordert der Aufruf im UI-Thread ausgeführt werden.

### <a name="windows-mixed-reality-on-desktop"></a>Windows Mixed Reality auf Desktop

#### <a name="visual-quality"></a>Visuelle Qualität

* Sollten Sie feststellen, nach dem die Windows 10 April 2018 aktualisieren, Grafiken unscharf als vor dem sein, oder, dass das Sichtfeld kleineren Ihre Kopfhörer aussieht, der automatische leistungseinstellung wurden möglicherweise geändert um eine ausreichende Framerate auf weniger leistungsfähigen zu gewährleisten. Grafikkarte (z. B. Nvidia-1050). Sie können manuell überschreiben diese (falls gewünscht) durch Navigieren zu **Einstellungen > Mixed Reality > Kopfhörer anzeigen > erleben Sie die Optionen > ändern** und ändern "Automatisch" auf "90 Hz." Sie können auch versuchen, Ändern von **visuelle Qualität** (auf der gleichen Seite der Einstellungen) auf "High".

#### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality-setup

* Beim Einrichten von Windows mit einem Kopfhörer angeschlossen kann Ihren PC-Monitor gelöscht. Trennen Sie Ihre Kopfhörer zum Aktivieren der Ausgabe auf den PC-Monitor, um Windows Setup abzuschließen.
* Wenn Sie nicht Kopfhörer angeschlossen haben, kann zusätzliche Tipps übersehen werden, wenn Sie zuerst die Windows Mixed Reality home besuchen.
* Andere Bluetooth-Geräte können Störungen mit Motion-Controllern führen. Wenn während der Übertragung Controller Verbindung/Kopplung/Verfolgen von Problemen, die Bluetooth-Funktion (sofern es sich um eine externe Dongle) sicherstellen haben ist an einem Speicherort hindernisfreien und nicht direkt neben einem anderen Bluetooth-Dongle angeschlossen. Versuchen Sie auch andere Bluetooth-Peripheriegeräte herunterzufahren, während Windows Mixed Reality-Sitzungen, um festzustellen, ob es hilft.

#### <a name="games-and-apps-from-the-microsoft-store"></a>Spiele und apps aus dem Microsoft Store

* Einige Spiele grafisch intensive wie Forza Motorsport 7 möglicherweise Leistungsprobleme auf weniger leistungsstarken PCs, wenn in Windows Mixed Reality wiedergegeben.

#### <a name="audio"></a>Audio

* Wenn Sie Cortana auf Ihrem Host-PC vor der Verwendung Ihrer Windows Mixed Reality-Kopfhörer aktiviert haben, verlieren Sie räumliche sound Simulation, die auf die apps, die Sie für die Windows Mixed Reality home platzieren angewendet. 
   * Die problemumgehung besteht darin, aktivieren Sie "Windows Sonic für Kopfhörer" auf alle Audiogeräten, die auf Ihren PC, sogar Ihre Kopfhörer verbundener audio-Gerät angefügt:
      1. Klicken Sie auf das Speaker-Symbol auf der desktop-Taskleiste, und wählen Sie aus der Liste der Audiogeräte.
      2. Mit der rechten Maustaste in des Speaker-Symbols auf der desktop-Taskleiste, und wählen Sie "Windows Sonic für Kopfhörer" im Menü "Speaker-Setup".
      3. Wiederholen Sie diese Schritte für alle Ihre Audiogeräte (Endpunkte).
   * Eine weitere Option ist "Let Cortana-Reaktion auf Hey Cortana" in deaktivieren **Einstellungen** > **Cortana** auf Ihrem Desktop vor dem Starten von Windows Mixed Reality.
* Wenn Sie ein anderes multimedia USB-Gerät (z. B. eine Webcam) den gleichen USB-Hub (entweder extern oder in Ihrem PC) für die Windows Mixed Reality-Kopfhörer freigegeben hat, kann in seltenen Fällen den Kopfhörer des audio Jack/Kopfhörer entweder Sound Fiepen oder ohne Audio überhaupt haben. Sie können dies durch Ihre Kopfhörer in einen USB-Anschluss beheben, die nicht den gleichen Hub als das andere Gerät freigeben, oder trennen/Deaktivieren von Ihrem anderen multimedia USB-Gerät.
* In sehr seltenen Fällen geben Sie den Host-PC USB-Hub kann nicht ausreichend Leistung, die Windows Mixed Reality-Kopfhörer, und der eines plötzlichen Ansturms von Störungen durch die Kopfhörer an den Kopfhörer angeschlossen.

#### <a name="holograms"></a>Hologramme

* Wenn Sie eine große Anzahl von Hologramme in Ihr Windows Mixed Reality home platziert haben, können einige nicht mehr angezeigt und wieder eingeblendet, wie Sie sich mit der Registerkarte. Um dies zu vermeiden, entfernen Sie einige der Hologramme in diesem Bereich der Startseite Windows Mixed Reality-Paket aus.

#### <a name="motion-controllers"></a>Motion-Controller

* Wenn die Eingabe nicht an den Kopfhörer weitergeleitet wird, wird der Motion-Controller kurz entfernt, wenn neben den Raum Grenze gehalten wird. Drücken die Windows-Taste + Y, um sicherzustellen, dass ein blaues Banner zwischen der Desktopmonitor vorhanden ist, wird dies beheben. 
* In einigen Fällen wird beim Klicken auf eine Webseite in Microsoft Edge, der Inhalt anstatt auf vergrößert.

#### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Desktop-app in die Windows Mixed Reality home

* Snipping Tool funktioniert nicht in Desktop-app.
* Desktop-app beibehalten-Einstellung auf neu starten nicht.
* Wenn Sie Mixed Reality-Verwaltungsportal (Vorschau) auf Ihrem Desktop verwenden, wenn die Desktop-app in die Windows Mixed Reality Startseite zu öffnen, werden Sie mit dem unendlichen Spiegeleffekt feststellen. 
* Ausführen der Desktop-app möglicherweise Leistungsprobleme auf nicht - Ultra Windows Mixed Reality-PCs; Es wird nicht empfohlen.  
* Desktop-app kann automatisch gestartet, da ein nicht sichtbar auf Desktop-Fenster den Fokus besitzt. 
* Desktop User Account Control Aufforderung veranlasst Kopfhörer Schwarz angezeigt, bis die Eingabeaufforderung abgeschlossen ist.

#### <a name="windows-mixed-reality-for-steamvr"></a>Windows Mixed Reality für SteamVR

* Möglicherweise müssen Sie die Mixed Reality-Portal starten nach der Aktualisierung die erforderlichen Softwareupdates für die Windows 10 April 2018 sicherstellen Update haben vor dem Starten der SteamVR. 
* Sie muss auf eine aktuelle Version von Windows Mixed Reality für SteamVR Kompatibilität mit Windows 10 April 2018 aktualisieren. Stellen Sie sicher, dass automatische Updates für Windows Mixed Reality für SteamVR, aktiviert sind die im Abschnitt "Software" Ihrer Bibliothek im Stream befindet.  

#### <a name="other-issues"></a>Andere Probleme

>[!IMPORTANT]
>Eine frühe Version von Windows 10 April 2018 in Update per Push an Insider (Version 17134.5) fehlt einen Teil der Software, die zum Ausführen von Windows Mixed Reality. Es wird empfohlen, vermeiden diese Version aus, wenn Windows Mixed Reality verwenden. 

Wir haben einen Leistungsverlust identifiziert, wenn Surface Book 2 auf dem ersten Release dieses Updates (10.0.17134.1) zu verwenden, die wir gearbeitet. in einem zukünftigen Update-Patch. Es wird empfohlen, warten, bis dies vor dem manuell aktualisieren oder warten, bis das Update, das normalerweise Rollout behoben wurde.

## <a name="provide-feedback-and-report-issues"></a>Bereitstellen von Feedback und melden Sie Probleme

Verwenden Sie die [Feedback Hub-app auf Ihrem HoloLens oder Windows 10-PCs](give-us-feedback.md) Feedback und melden Sie Probleme bereitstellen. Mithilfe von Feedback-Hub wird sichergestellt, dass alle erforderlichen Diagnoseinformationen enthalten, damit unsere Techniker schnelles Debuggen und das Problem beheben können.

>[!NOTE]
>Achten Sie darauf, dass Sie die Eingabeaufforderung akzeptieren, mit der Frage, ob Sie die Feedback-Hub, um den Ordner "Dokumente" zugreifen möchten (Wählen Sie **Ja** Aufforderung).

## <a name="prior-release-notes"></a>Anmerkungen zu dieser früheren Version

* [Anmerkungen zu dieser Version – Oktober 2017](release-notes-october-2017.md)
* [Anmerkungen zu dieser Version – August 2016](release-notes-august-2016.md)
* [Anmerkungen zu dieser Version – Mai 2016](release-notes-may-2016.md)
* [Anmerkungen zu dieser Version – März 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Siehe auch
* [Unterstützung für immersive Kopfhörer (externer Link)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [HoloLens-Unterstützung (externer Link)](https://support.microsoft.com/products/hololens)
* [Installieren der tools](install-the-tools.md)
* [Geben Sie uns feedback](give-us-feedback.md)

