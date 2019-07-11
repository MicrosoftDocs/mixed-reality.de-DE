---
title: HoloLens – bekannte Probleme
description: Dies ist die Liste der bekannten Probleme, die HoloLens-Entwickler beeinflussen können.
author: mattzmsft
ms.author: mazeller
ms.date: 07/10/2019
ms.topic: article
keywords: Problembehandlung bei, bekanntes Problem, Hilfe
ms.openlocfilehash: 1ef9e9f411e16d2f604930f3146ede1d03d7c0f6
ms.sourcegitcommit: c36b8c8573f51afa79504c4a17084e4f55d2f664
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67789491"
---
# <a name="hololens-known-issues"></a>HoloLens – bekannte Probleme

Dies ist die aktuelle Liste der bekannten Probleme für HoloLens Auswirkungen auf Entwickler. Sie zunächst hier überprüfen Sie, wenn ein ungewöhnliches Verhalten angezeigt werden. Diese Liste wird aktualisiert gehalten, neue Probleme bekannt werdende oder gemeldete oder mit der Probleme behoben werden, in zukünftigen HoloLens-Software-Updates.

## <a name="unable-to-connect-and-deploy-to-hololens-through-visual-studio"></a>Kann keine Verbindung herstellen, HoloLens, über Visual Studio bereitstellen

>[!NOTE]
>Letzte Aktualisierung: 7/8 @ 7:25 Uhr – das Team hat die zugrunde liegende Ursache ermittelt und arbeitet zurzeit auf "beheben". Die problemumgehung unter verfügbar. 

Wir konnten die Ursache des Problems zu identifizieren. Benutzer, die Visual Studio 2015 oder früher Versionen von Visual Studio 2017 zum Bereitstellen und Debuggen von Anwendungen auf ihren HoloLens verwendet und dann anschließend verwendet die neuesten Versionen von Visual Studio 2017 oder Visual Studio-2019 mit der gleichen HoloLens sind betroffen. 

Die neueren Versionen von Visual Studio bereitstellen, eine neue Version einer Komponente, aber Dateien von der älteren Version übrig sind, auf dem Gerät, wodurch die neuere Version nicht.  Dies bewirkt, dass die folgende Fehlermeldung angezeigt: DEP0100: Stellen Sie sicher, dass das Zielgerät Entwicklermodus aktiviert ist. Eine Entwicklerlizenz konnte nicht auf erhalten <ip> aufgrund von Fehler 80004005.
 
**Problemumgehung**: 

Unser Team arbeitet zurzeit an einer Lösung. In der Zwischenzeit können Sie die folgenden Schritte verwenden, um das Problem zu umgehen, und zu unterstützen, bereitstellen und Debuggen zulassen:  
1. Öffnen Sie Visual Studio.
2. Datei -> Neu -> Projekt
3. Visual C# -> Windows Desktop -> Konsolen-App ((.NET Framework)
4. Geben Sie dem Projekt einen Namen (z. B. HoloLensDeploymentFix), und stellen Sie sicher, dass das Framework ist legen Sie mindestens .NET Framework 4.5, klicken Sie dann auf OK.
5. Mit der rechten Maustaste auf den Knoten "Verweise" im Projektmappen-Explorer, und fügen Sie die folgenden Verweise hinzu (klicken Sie im Abschnitt "Durchsuchen", und klicken Sie auf die "Durchsuchen..." Schaltfläche "):
    ```
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Deploy.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Connectivity.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\SirepInterop.dll
    ```
    >[!NOTE]
    >Wenn Sie keine 10.0.18362.0 installiert haben, verwenden Sie die neueste Version, die Sie aus.
 
6. Mit der rechten Maustaste auf das Projekt im Projektmappen-Explorer, und wählen Sie Add -> Vorhandenes Element.
 
7. Navigieren Sie zu C:\Program Files (x86) \Windows Kits\10\bin\10.0.18362.0\x86, und ändern Sie den Filter auf "alle Dateien (\*.\*)"
 
8. Wählen Sie zuerst SirepClient.dll und SshClient.dll, und klicken Sie auf "Hinzufügen".
 
9. Suchen und markieren Sie beide Dateien im Projektmappen-Explorer (sie am unteren Rand der Liste der Dateien sein sollte), und ändern Sie "In Ausgabeverzeichnis kopieren" im Fenster Eigenschaften in "Immer kopieren"
 
10. Fügen Sie Folgendes am Anfang der Datei an die vorhandene Liste der 'using'-Anweisungen: 
    ```
    using Microsoft.Tools.Deploy;
    using System.Net;
    ```
 
11. Fügen Sie in "statisch" void "Main(...)" den folgenden Code hinzu:
    ```
    RemoteDeployClient client = RemoteDeployClient.CreateRemoteDeployClient();
    client.Connect(new ConnectionOptions()
    {
        Credentials = new NetworkCredential("DevToolsUser", string.Empty),
        IPAddress = IPAddress.Parse(args[0])
    });
    client.RemoteDevice.DeleteFile(@"C:\Data\Users\DefaultAccount\AppData\Local\DevelopmentFiles\VSRemoteTools\x86\CoreCLR\mscorlib.ni.dll");
    ```
12. Erstellen -> Projektmappe erstellen
 
13. Öffnen Sie eine Eingabeaufforderung zu dem Ordner, der die kompilierte .exe (z. B. C:\MyProjects\HoloLensDeploymentFix\bin\Debug) enthält.
 
14. Führen Sie die ausführbare Datei aus, und geben Sie das Gerät die IP-Adresse als Befehlszeilenargument.  (Wenn Sie über USB verbunden, Sie können 127.0.0.1, verwenden Sie andernfalls WiFi IP-Adresse des Geräts.)  Z. B. "HoloLensDeploymentFix 127.0.0.1"
 
15. Nachdem das Tool ohne Meldungen beendet wurde (dies dauert nur wenige Sekunden), werden Sie jetzt bereitstellen und Debuggen in Visual Studio 2017 oder höher.  Durch die fortgesetzte Nutzung des Tools ist nicht erforderlich.

Wir bieten weitere Updates, sobald diese verfügbar werden.

## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a>Probleme beim Starten der Microsoft Store und apps für HoloLens

>[!NOTE]
>Letzte Aktualisierung: 4/2 @ 10: 00 Uhr - Problem beheben. 

Sie können Probleme auftreten, bei dem Versuch, starten Sie den Microsoft Store und apps für HoloLens. Wir haben festgestellt, dass das Problem tritt auf, wenn Hintergrund-app-Updates, eine neuere Version von Framework-Pakete in bestimmten Sequenzen während mindestens eine bereitstellen oder mehrere abhängige apps werden weiterhin ausgeführt. In diesem Fall verursacht ein automatische app-Update, das eine neue Version von systemeigenen .NET Framework (Version 10.0.25531 zu 10.0.27413) übermittelt, die apps, die nicht ordnungsgemäß Update für alle ausgeführten apps nutzen die vorherige Version des Frameworks ausgeführt werden.  Der Ablauf für die Framework-Update ist wie folgt:-

1.  Das neue frameworkpaket wird aus dem Store heruntergeladen und installiert
2.  Alle apps, die mit älteren Framework sind "updated" um die neuere Version zu verwenden.

Wenn Schritt 2 vor Abschluss unterbrochen wird, schlägt alle apps, die für die das neuere Framework registriert war nicht fehl, um über das Startmenü starten.  Wir sind der Meinung, dass alle Apps für HoloLens, die von diesem Problem betroffen sein könnten.

Einige Benutzer haben gemeldet, dass das Schließen von nicht reagierenden apps aus, und Starten von anderen apps wie z.B. Feedback-Hub, 3D Viewer oder Fotos löst das Problem für sie – ist jedoch nicht 100 % der Zeit möglich.

Wir haben Stamm verursacht, die dieses Problem nicht das Update selbst, aber ein Fehler im Betriebssystem verursacht wurde, die das .NET Native Framework-Update nicht ordnungsgemäß verarbeitet geführt haben. Wir freuen uns, ankündigen zu können, dass wir eine Korrektur identifiziert haben, und ein Update (OS Version 17763.380) veröffentlicht, die die Lösung enthält. 

Um festzustellen, ob es sich bei Ihrem Gerät das Update nehmen kann:

1.  Wechseln Sie zu der app "Einstellungen", und öffnen Sie "Update und Sicherheit"
2.  Klicken Sie auf "Nach Updates suchen"
3.  Wenn Update 17763.380 verfügbar ist, aktualisieren Sie auf diesen Build aus, um die Lösung für den Absturz des App-Fehler zu erhalten.
4.  Beim Aktualisieren auf diese Version des Betriebssystems, sollte die Apps wie erwartet funktionieren.

Darüber hinaus wie bei jeder HoloLens-OS-Version, wir haben das Image FFU an gesendet im Microsoft Download Center unter https://aka.ms/hololensdownload/10.0.17763.380. 

Wenn Sie nicht das Update in Anspruch nehmen möchten, haben wir eine neue Version der Microsoft Store UWP-app ab 3/29 veröffentlicht. Nachdem Sie die aktualisierte Version von den Store haben:

1) Öffnen Sie den Store, und vergewissern Sie sich, dass es geladen.
2) Verwenden Sie die Bewegung Bloom, um das Menü zu öffnen.
3) Versucht, die zuvor fehlerhaften apps öffnen
3) Wenn sie noch nicht gestartet werden kann, tippen Sie auf halten Sie das Symbol der app unterbrochen und wählen Sie deinstallieren.
4) Partitionieren diese apps aus dem Store.

Wenn Ihr Gerät weiterhin apps laden kann, können Sie durch praktische Übungen querladen einer Version von .NET Native-Framework und der Laufzeit über das Downloadcenter:

1)  Laden Sie [diese Zip-Datei](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip) aus dem Microsoft Download Center.  Entzippen erzeugt zwei Dateien.  Microsoft.NET.Native.Runtime.1.7.appx und Microsoft.NET.Native.Framework.1.7.appx
2)  Stellen Sie sicher, dass Ihr Gerät Dev entsperrt ist.  Wenn Sie, die dies nicht getan haben, bevor Sie die Anweisungen dazu sind [hier](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0).
3)  Klicken Sie dann in die Windows Device Portal abrufen möchten.  Unsere Empfehlung ist, klicken Sie hierzu über USB, und Sie würden Sie dies, indem Sie die Eingabe http://127.0.0.1:10080 in Ihrem Browser.  
4)  Nachdem Sie die im Windows Device Portal einrichten wir die benötigten "querladen" haben Dateien die beiden an, dass Sie heruntergeladen haben.  Zu diesem Zweck müssen Sie der linken Seitenleiste gesendet werden soll, bis Sie im Abschnitt "Apps" zu erhalten, und klicken Sie auf "Apps".
5)  Daraufhin wird einen Bildschirm ähnlich dem folgenden.  Finden im Abschnitt mit dem Text "Installieren der App" aus, und navigieren Sie zu, in dem Sie diese beiden APPX-Dateien entpackt werden soll.  Führen Sie nur einen zu einem Zeitpunkt, also nach der Auswahl von dem ersten Beispiel, klicken Sie dann auf "Go" im Abschnitt bereitstellen können.  Führen Sie dies dann für die zweite APPX-Datei. 
  ![Windows Device Portal Quergeladener Apps installieren](images/20190322-DevicePortal.png)<br>
6)  An diesem Punkt glauben wir Ihre Anwendungen wieder gestartet werden soll, dass Sie auch auf den Store abrufen können.
7)  In einigen Fällen muss den zusätzlichen Schritt die 3D Viewer-app zu starten, bevor betroffene apps starten, werden ausgeführt. 

Wir danken Ihnen für Ihre Geduld haben wir durchlaufen, bis des Prozess, um dieses Problem lösen, und wir freuen uns darauf zum Arbeiten mit unserer Community zum Erstellen von erfolgreichen Mixed Reality weiterhin auftritt.

## <a name="connecting-to-wifi"></a>Herstellen einer Verbindung mit WiFi

Während OOBE "und" Einstellungen "ist ein Anmeldeinformationen-Timeout von 2 Minuten. Der Benutzername und Kennwort muss innerhalb von 2 Minuten, die andernfalls eingegeben werden, die Feld "Username" automatisch gelöscht wird.

Es wird empfohlen, mithilfe der Tastatur Bluetooth für das lange Kennwörter eingeben.

## <a name="device-update"></a>Gerät aktualisieren
* 30 Sekunden nach dem ein neues Update, kann die Shell einmal nicht mehr angezeigt. Führen Sie die **Bloom** Geste zum Fortsetzen der Sitzungs.

## <a name="visual-studio"></a>Visual Studio
* Finden Sie unter [Installieren der Tools](install-the-tools.md) für die aktuelle Version von Visual Studio, die für die Entwicklung für HoloLens empfohlen.
* Wenn Sie eine app aus Visual Studio Ihre HoloLens bereitstellen zu können, wird möglicherweise der Fehler angezeigt: **Der angeforderte Vorgang kann nicht auf eine Datei mit einem Benutzer zugeordnete Abschnitt Open ausgeführt werden. (Ausnahme von HRESULT: 0x800704C8)** . In diesem Fall versuchen Sie es erneut, und die Bereitstellung in der Regel erfolgreich.

## <a name="emulator"></a>Emulator
* Nicht alle apps in der Microsoft Store werden mit dem Emulator kompatibel. Young Conker und Fragmente sind beispielsweise nicht auf dem Emulator gespielt werden.
* Sie können nicht die PC-Webcam im Emulator verwenden.
* Die Livevorschau-Funktion von der Windows Device Portal funktioniert nicht mit dem Emulator. Sie können weiterhin die Möglichkeit, Mixed Reality-Videos und Bilder erfassen.

## <a name="unity"></a>Unity
* Finden Sie unter [Installieren der Tools](install-the-tools.md) für die aktuelle Version von Unity für die Entwicklung für HoloLens empfohlen.
* Bekannte Probleme mit der Technical Preview für Unity HoloLens sind dokumentiert, der [HoloLens Unity Foren](http://forum.unity3d.com/threads/known-issues.394627/).

## <a name="windows-device-portal"></a>Windows Device Portal
* Live-Vorschau in Mixed Reality-Erfassung kann mehrere Sekunden Wartezeit aufweisen.
* Auf der Seite virtuelle Eingabe sind die Steuerelemente Geste und scrollen Sie im Abschnitt virtuelle Gesten nicht funktionsfähig. Verwenden sie haben keine Wirkung. Die virtuelle Tastatur auf derselben Seite ordnungsgemäß funktioniert.
* Nach dem Aktivieren der Entwicklermodus in den Einstellungen, dauert es einige Sekunden, bevor Sie der Switch So aktivieren Sie das Device Portal aktiviert ist.

## <a name="api"></a>API
* Wenn die Anwendung wird die [Zeitpunkt konzentrieren](focus-point-in-unity.md) hinter der Benutzer oder die normale, camera.forward, Hologramme nicht in Mixed Reality Aufzeichnen von Fotos oder Videos angezeigt. Bis dieses Problem in Windows, behoben wird, wenn Anwendungen aktiv festlegen der [konzentrieren Punkt](focus-point-in-unity.md) sollten sie sicherstellen, die Datenebene normale entgegengesetzten Kamera Weiterleitung festgelegt ist (z. B. normale = - camera.forward).

## <a name="xbox-wireless-controller"></a>Xbox-Wireless-Controller
* Xbox-Wireless-Controller-S muss aktualisiert werden, bevor sie mit HoloLens verwendet werden kann. Sicher, dass Sie [auf dem neuesten Stand](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) vor dem Versuch, Ihre Controller mit einem HoloLens zu koppeln.
* Wenn Sie Ihre HoloLens neu starten, während die Xbox-Wireless-Controller verbunden ist, wird der Controller mit HoloLens nicht automatisch wiederherzustellen. Das Handbuch Schaltfläche Licht leuchtet langsam, bis der Controller ausschaltet aus nach 3 Minuten. Verbindung von Ihrem Controller sofort, schalten Sie den Controller, indem Sie die Anleitung gedrückt, bis das Licht ausgeschaltet. Wenn Sie Ihre Controller wieder einschalten, werden sie eine Verbindung mit HoloLens wiederherstellen.
* Wenn Ihre HoloLens Standby eingibt, während die Xbox-Wireless-Controller verbunden ist, werden eine Eingabe auf dem Controller die HoloLens aktiviert. Sie können dies verhindern, indem Sie Ihre Controller ausschalten, wenn Sie fertig sind verwenden.
