---
title: Bekannte Probleme mit hololens
description: Dies ist die Liste bekannter Probleme, die sich auf hololens-Entwickler auswirken können.
author: mattzmsft
ms.author: mazeller
ms.date: 07/10/2019
ms.topic: article
keywords: Problembehandlung, bekanntes Problem, Hilfe
ms.openlocfilehash: 80bd7499c0075399e516648dd92b7515fdba753a
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122132"
---
# <a name="hololens-known-issues"></a>Bekannte Probleme mit hololens

Dies ist die aktuelle Liste bekannter Probleme für hololens, die sich auf Entwickler auswirken. Überprüfen Sie dies zuerst, wenn Sie ein ungerade Verhalten sehen. Diese Liste wird immer dann aktualisiert, wenn neue Probleme erkannt oder gemeldet werden oder wenn Probleme in zukünftigen hololens-Software Updates behoben werden.

## <a name="unable-to-connect-and-deploy-to-hololens-through-visual-studio"></a>Über Visual Studio kann keine Verbindung hergestellt und in hololens bereitgestellt werden.

>[!NOTE]
>Letztes Update: 8/8 @ 5:11Uhr: Visual Studio hat vs 2019 Version 16,2 freigegeben, die eine Lösung für dieses Problem enthält. Es wird empfohlen, auf die neueste Version zu aktualisieren, damit dieser Fehler nicht angezeigt wird.

Visual Studio hat Visual Studio 2019 Version 16,2 freigegeben, die eine Lösung für dieses Problem enthält. Es wird empfohlen, auf die neueste Version zu aktualisieren, damit dieser Fehler nicht angezeigt wird.

Problem Ursache: Benutzer, die Visual Studio 2015 oder frühe Releases von Visual Studio 2017 zum Bereitstellen und Debuggen von Anwendungen auf Ihren hololens verwendet haben und anschließend die neuesten Versionen von Visual Studio 2017 oder Visual Studio 2019 mit denselben hololens verwenden, sind betroffen. In den neueren Versionen von Visual Studio wird eine neue Version einer Komponente bereitgestellt, aber Dateien aus der älteren Version bleiben auf dem Gerät, sodass die neuere Version fehlschlägt.  Dies bewirkt die folgende Fehlermeldung: DEP0100: Stellen Sie sicher, dass der Entwicklermodus für das Zielgerät aktiviert ist. Eine Entwicklerlizenz <ip> konnte aufgrund von Fehler 80004005 nicht abgerufen werden.
 
**Problemumgehung**: 

Obwohl dieses Problem in Visual Studio 2019 16,2 behoben wurde, können Entwickler, die in früheren Versionen von Visual Studio bleiben möchten, die folgenden Schritte ausführen, um das Problem zu umgehen und die Blockierung der Bereitstellung und des Debuggens zu unterstützen:  
1. Öffnen Sie Visual Studio.
2. Datei > New->-Projekt
3. Visual C# > Windows-Desktop > Konsolen-app (.NET Framework)
4. Geben Sie dem Projekt einen Namen (z. b. hololensdeploymentfix), und stellen Sie sicher, dass das Framework auf mindestens .NET Framework 4,5 festgelegt ist, und klicken Sie dann auf OK.
5. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf den Knoten Verweise, und fügen Sie die folgenden Verweise hinzu (Klicken Sie auf den Abschnitt "Durchsuchen", und klicken Sie auf "Durchsuchen". Schaltfläche):
    ```
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Deploy.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Connectivity.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\SirepInterop.dll
    ```
    >[!NOTE]
    >Wenn 10.0.18362.0 nicht installiert ist, verwenden Sie die neueste Version, die Sie haben.
 
6. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie > vorhandenes Element hinzufügen aus.
 
7. Navigieren Sie zu "c:\Programme (x86) \Windows Kits\10\bin\10.0.18362.0\x86", und ändern Sie den Filter in\*"\*alle Dateien (.)".
 
8. Wählen Sie sowohl sirepclient. dll als auch sshclient. dll aus, und klicken Sie auf "hinzufügen".
 
9. Suchen und wählen Sie beide Dateien in Projektmappen-Explorer aus (Sie sollten sich am Ende der Liste der Dateien befinden), und ändern Sie "in Ausgabeverzeichnis kopieren" im Eigenschaftenfenster in "immer kopieren".
 
10. Fügen Sie am Anfang der Datei der vorhandenen Liste der using-Anweisungen Folgendes hinzu: 
    ```
    using Microsoft.Tools.Deploy;
    using System.Net;
    ```
 
11. Fügen Sie in "static void Main (...)" den folgenden Code hinzu:
    ```
    RemoteDeployClient client = RemoteDeployClient.CreateRemoteDeployClient();
    client.Connect(new ConnectionOptions()
    {
        Credentials = new NetworkCredential("DevToolsUser", string.Empty),
        IPAddress = IPAddress.Parse(args[0])
    });
    client.RemoteDevice.DeleteFile(@"C:\Data\Users\DefaultAccount\AppData\Local\DevelopmentFiles\VSRemoteTools\x86\CoreCLR\mscorlib.ni.dll");
    ```
12. Build->-buildlösung
 
13. Öffnen Sie eine Eingabeaufforderung für den Ordner, der die kompilierte EXE-Datei (z. b. c:\myproject\hololensdeploymentfix\bin\debug) enthält.
 
14. Führen Sie die ausführbare Datei aus, und geben Sie die IP-Adresse des Geräts als Befehlszeilenargument an.  (Wenn eine Verbindung über USB besteht, können Sie 127.0.0.1 verwenden. verwenden Sie andernfalls die WiFi-IP-Adresse des Geräts.)  Beispiel: "hololensdeploymentfix 127.0.0.1"
 
15. Wenn das Tool ohne Nachrichten beendet wurde (Dies sollte nur einige Sekunden dauern), können Sie jetzt in Visual Studio 2017 oder höher bereitstellen und Debuggen.  Die fortgesetzte Verwendung des Tools ist nicht erforderlich.


## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a>Probleme beim Starten des Microsoft Store und der apps auf hololens

>[!NOTE]
>Letztes Update: 4/2 @ 10 am: Problem gelöst. 

Beim Starten des Microsoft Store und der apps auf hololens treten möglicherweise Probleme auf. Wir haben festgestellt, dass das Problem auftritt, wenn Hintergrund-App-Aktualisierungen eine neuere Version von frameworkpaketen in bestimmten Sequenzen bereitstellen, während mindestens eine ihrer abhängigen apps noch ausgeführt wird. In diesem Fall hat ein automatisches App-Update eine neue Version von .net Native Framework (Version 10.0.25531 an 10.0.27413) übermittelt, die bewirkt, dass die apps, die ausgeführt werden, nicht für alle laufenden apps, die die vorherige Version des Frameworks nutzen, ordnungsgemäß aktualisiert werden.  Der Flow für das Framework-Update lautet wie folgt:

1.  Das neue frameworkpaket wird aus dem Store heruntergeladen und installiert.
2.  Alle apps, die das ältere Framework verwenden, werden aktualisiert, um die neuere Version zu verwenden.

Wenn Schritt 2 vor dem Abschluss unterbrochen wird, können alle apps, für die das neuere Framework nicht registriert wurde, nicht über das Startmenü gestartet werden.  Wir glauben, dass jede APP auf hololens von diesem Problem betroffen sein könnte.

Einige Benutzer haben gemeldet, dass das Schließen von nicht reagierenden apps und das Starten anderer apps, wie z. b. Feedback-Hub, 3D-Viewer oder Fotos, das Problem damit löst. Dies funktioniert jedoch nicht 100% der Zeit.

Der Grund dafür ist, dass dieses Problem nicht auf das Update selbst zurückzuführen ist, sondern auf einen Fehler im Betriebssystem, der dazu geführt hat, dass das .net Native Framework-Update falsch behandelt wurde. Wir freuen uns, Ihnen ankündigen zu können, dass wir eine Korrektur erkannt haben und ein Update (Betriebssystemversion 17763,380) veröffentlicht haben, das die Behebung enthält. 

Wenn Sie feststellen möchten, ob Ihr Gerät das Update ausführen kann, gehen Sie

1.  Wechseln Sie zur App "Einstellungen", und öffnen Sie "Update & Security".
2.  Klicken Sie auf "nach Updates suchen".
3.  Wenn Update auf 17763,380 verfügbar ist, aktualisieren Sie diesen Build, um die Behebung für den Fehler bei der APP zu erhalten.
4.  Wenn Sie auf diese Version des Betriebssystems aktualisieren, sollten die apps erwartungsgemäß funktionieren.

Außerdem haben wir wie bei jeder hololens-Betriebssystemversion das FFU-Image im Microsoft Download Center unter https://aka.ms/hololensdownload/10.0.17763.380 veröffentlicht. 

Wenn Sie das Update nicht durchführen möchten, haben wir eine neue Version der Microsoft Store UWP-App mit der Version 3/29 veröffentlicht. Sobald Sie über die aktualisierte Version des Stores verfügen:

1) Öffnen Sie den Speicher, und vergewissern Sie sich, dass er geladen wird
2) Öffnen Sie das Menü mithilfe der aufblühenden Bewegung.
3) Es wurde versucht, zuvor unterbrochene apps zu öffnen.
3) Wenn Sie immer noch nicht gestartet werden kann, tippen Sie auf das Symbol der unterbrochenen APP, und wählen Sie deinstallieren aus.
4) Resinstall diese apps aus dem Store.

Wenn auf Ihrem Gerät apps weiterhin nicht geladen werden können, können Sie eine Version des .net Native Frameworks und der Laufzeit über das Download Center querladen. gehen Sie hierzu wie folgt vor:

1)  Laden Sie [diese ZIP-Datei](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip) aus dem Microsoft Download Center herunter.  Beim Entzippen werden zwei Dateien erstellt.  Microsoft. net. Native. Runtime. 1.7. AppX und Microsoft. net. Native. Framework. 1.7. AppX
2)  Vergewissern Sie sich, dass das Gerät entsperrt ist.  Wenn Sie dies noch nicht getan haben, müssen Sie die [hier](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0)beschriebenen Anweisungen ausführen.
3)  Sie können sich dann im Windows-Geräte Portal befinden.  Wir empfehlen Ihnen, dies über USB zu tun, indem Sie in Ihren Browser http://127.0.0.1:10080 eingeben.  
4)  Nachdem Sie das Windows-Geräte Portal eingerichtet haben, müssen Sie die beiden Dateien, die Sie heruntergeladen haben, "nebeneinander" laden.  Zu diesem Zweck müssen Sie die linke Leiste nach unten wechseln, bis Sie zum Abschnitt "Apps" gelangen und auf "Apps" klicken.
5)  Daraufhin wird ein Bildschirm angezeigt, der dem folgenden ähnelt.  Wechseln Sie zum Abschnitt "App installieren", und navigieren Sie zu dem Verzeichnis, in das Sie diese beiden AppX-Dateien entzippt haben.  Sie können nur ein-Mal ausführen, also klicken Sie nach Auswahl des ersten auf "Go" im Abschnitt "Bereitstellen".  Führen Sie diese dann für die zweite AppX-Datei aus. 
  ![Windows-Geräte Portal zum Installieren von neben geladenen Apps](images/20190322-DevicePortal.png)<br>
6)  An dieser Stelle glauben wir, dass Ihre Anwendungen wieder arbeiten sollten und dass Sie auch in den Speicher gelangen können.
7)  In einigen Fällen ist es erforderlich, den zusätzlichen Schritt zum Starten der 3D-Viewer-App auszuführen, bevor betroffene apps gestartet werden. 

Wir schätzen Ihre Geduld, da wir den Vorgang durchgeführt haben, um dieses Problem zu beheben. Wir freuen uns darauf, mit unserer Community fortfahren zu können, um erfolgreiche gemischte Umgebungen zu entwickeln.

## <a name="connecting-to-wifi"></a>Verbinden mit WiFi

Bei den Einstellungen für die & OOBE gibt es ein Timeout für Anmelde Informationen von 2 Minuten. Der Benutzername bzw. das Kennwort muss innerhalb von 2 Minuten eingegeben werden. andernfalls wird das Feld Benutzername automatisch gelöscht.

Wir empfehlen die Verwendung einer Bluetooth-Tastatur für die Eingabe von langen Kenn Wörtern.

>[!NOTE]
> Wenn während der OOBE-Option das falsche Netzwerk ausgewählt ist, muss das Gerät vollständig zurückgesetzt werden. Anweisungen finden Sie [hier.](https://docs.microsoft.com/en-us/windows/mixed-reality/reset-or-recover-your-hololens#perform-a-full-device-recovery) 

## <a name="device-update"></a>Geräte Aktualisierung
* 30 Sekunden nach einem neuen Update kann die Shell einmal verschwinden. Führen Sie die **aufblühenden** Gesten aus, um die Sitzung fortzusetzen.

## <a name="visual-studio"></a>Visual Studio
* Weitere Informationen finden Sie unter [Installieren der Tools](install-the-tools.md) für die aktuellste Version von Visual Studio, die für die hololens-Entwicklung empfohlen wird.
* Beim Bereitstellen einer APP von Visual Studio in den hololens wird möglicherweise der folgende Fehler angezeigt: **Der angeforderte Vorgang kann nicht für eine Datei ausgeführt werden, in der ein vom Benutzer zugeordneter Abschnitt geöffnet ist. (Ausnahme von HRESULT: 0x800704c8)** . Wenn dies der Fall ist, versuchen Sie es erneut, und Ihre Bereitstellung wird im allgemeinen erfolgreich

## <a name="emulator"></a>Emulator
* Nicht alle apps in der Microsoft Store sind mit dem Emulator kompatibel. Beispielsweise können die kleinen-und-Fragmente im Emulator nicht abgespielt werden.
* Die PC-Webcam kann nicht im Emulator verwendet werden.
* Das Live Vorschau Feature des Windows-Geräte Portals funktioniert nicht mit dem Emulator. Sie können trotzdem Videos und Bilder mit gemischter Realität erfassen.

## <a name="unity"></a>Unity
* Weitere Informationen finden Sie unter [Installieren der Tools](install-the-tools.md) für die aktuellste Version von Unity, die für die hololens-Entwicklung empfohlen wird.
* Bekannte Probleme bei der Technical Preview-Version von Unity hololens sind in den [hololens Unity-Foren](http://forum.unity3d.com/threads/known-issues.394627/)dokumentiert.

## <a name="windows-device-portal"></a>Windows Device Portal
* Das Live Vorschau Feature in der Mixed Reality-Erfassung kann mehrere Sekunden Latenz aufweisen.
* Auf der Seite virtuelle Eingabe sind die Gesten-und scrollsteuer Elemente im Abschnitt virtuelle Gesten nicht funktionsfähig. Die Verwendung von Ihnen hat keine Auswirkungen. Die virtuelle Tastatur auf der gleichen Seite funktioniert ordnungsgemäß.
* Nachdem Sie den Entwicklermodus in den Einstellungen aktiviert haben, kann es einige Sekunden dauern, bis der Switch aktiviert ist, um das Geräte Portal zu aktivieren.

## <a name="api"></a>API
* Wenn die Anwendung den [Fokuspunkt](focus-point-in-unity.md) hinter dem Benutzer oder dem normalen auf "Camera. Forward" festlegt, werden holograms nicht in gemischten Reality-Fotos oder Videos angezeigt. Bis dieser Fehler in Windows behoben ist, sollten Anwendungen, die den [Fokuspunkt](focus-point-in-unity.md) aktiv festlegen, sicherstellen, dass die Ebene normal gegen Kamera-vorwärts (z. b. Normal =-Camera. Forward) festgelegt ist.

## <a name="xbox-wireless-controller"></a>Xbox Wireless Controller
* Der Xbox Wireless Controller S muss aktualisiert werden, bevor er mit hololens verwendet werden kann. Stellen Sie sicher, dass Sie auf [dem neuesten Stand](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) sind, bevor Sie versuchen, Ihren Controller mit einem hololens zu Kopp
* Wenn Sie die hololens neu starten, während der Xbox Wireless-Controller verbunden ist, wird der Controller nicht automatisch wieder mit hololens verbunden. Das Ampel Schaltfläche blinkt langsam, bis der Controller nach 3 Minuten ausgeschaltet wird. Zum sofortigen erneuten Verbinden des Controllers schalten Sie den Controller ein, indem Sie die Schaltfläche "Guide" gedrückt halten, bis das Licht ausgeschaltet wird. Wenn Sie den Controller wieder einschalten, wird die Verbindung mit hololens wieder hergestellt.
* Wenn Ihre hololens in den Standbymodus versetzt werden, während der Xbox Wireless-Controller verbunden ist, werden alle Eingaben auf dem Controller die hololens reaktivieren. Sie können dies verhindern, indem Sie den Controller ausschalten, wenn Sie ihn nicht mehr benötigen.
