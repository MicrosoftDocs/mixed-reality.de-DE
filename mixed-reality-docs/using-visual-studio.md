---
title: Verwenden von Visual Studio zum Bereitstellen und Debuggen
description: Erfahren Sie, wie Sie Apps für hololens und Windows Mixed Reality mithilfe von Visual Studio erstellen, Debuggen und bereitstellen.
author: pbarnettms
ms.author: pbarnett
ms.date: 10/24/2019
ms.topic: article
keywords: Visual Studio, hololens, gemischte Realität, Debuggen, bereitstellen
ms.openlocfilehash: 2b84183417a1bd4eaa90eef58bebe2b65966b933
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437299"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Verwenden von Visual Studio zum Bereitstellen und Debuggen

Unabhängig davon, ob Sie DirectX oder Unity zur Entwicklung ihrer Mixed Reality-App verwenden möchten, verwenden Sie Visual Studio zum Debuggen und bereitstellen. In diesem Abschnitt lernen Sie Folgendes:
* Erfahren Sie, wie Sie Anwendungen in den hololens oder im immersiven Windows Mixed Reality-Headset über Visual Studio bereitstellen.
* So verwenden Sie den in Visual Studio integrierten hololens-Emulator.
* Debuggen von Mixed Reality-apps

## <a name="prerequisites"></a>Voraussetzungen
1. Anweisungen zur Installation finden Sie [unter Installieren der Tools](install-the-tools.md) .
2. Erstellen Sie in Visual Studio ein neues universelles Windows-App-Projekt.  Verwenden Sie für hololens (1. Gen) Visual Studio 2017 oder höher.  Verwenden Sie für hololens 2 Visual Studio 2019 16,2 oder höher. C#und C++ werden unterstützt. (Oder befolgen Sie die Anweisungen zum [Erstellen einer APP in Unity](holograms-100.md).)

## <a name="enabling-developer-mode"></a>Aktivieren des Entwicklermodus

Beginnen Sie, indem Sie den **Entwicklermodus** auf Ihrem Gerät aktivieren, damit Visual Studio eine Verbindung damit herstellen kann.

### <a name="hololens"></a>HoloLens
1. Schalten Sie die hololens ein, und legen Sie Sie auf dem Gerät ab.
2. Führen Sie die [Blütengeste](system-gesture.md#bloom) aus, um das Hauptmenü zu starten.
3. Schauen Sie sich die Kachel " **Einstellungen** " an, und führen Sie die [Tasten](gaze-and-commit.md#composite-gestures) Kombination aus. Führen Sie die Zeigefingergeste ein zweites Mal aus, um die App in Ihrer Umgebung zu platzieren. Die Einstellungs-App wird gestartet, nachdem Sie sie platziert haben.
4. Wählen Sie das Menüelement **Aktualisieren** aus.
5. Wählen Sie das Menüelement **Für Entwickler** aus.
6. Aktivieren Sie den **Entwicklermodus**. Auf diese Weise können Sie [Apps aus Visual Studio](using-visual-studio.md) in ihren hololens bereitstellen.
7. Optional: Scrollen Sie nach unten, und aktivieren Sie auch das **Geräte Portal**. Auf diese Weise können Sie auch über einen Webbrowser eine Verbindung mit dem [Windows-Geräte Portal](using-the-windows-device-portal.md) auf Ihren hololens herstellen.

### <a name="windows-pc"></a>Windows-PC

Wenn Sie mit einem Windows Mixed Reality-Headset arbeiten, das mit dem PC verbunden ist, müssen Sie auf dem PC den **Entwicklermodus** aktivieren.
1. Zu **Einstellungen** wechseln
2. Auswählen von **Update und Sicherheit**
3. **Für Entwickler** auswählen
4. Aktivieren Sie den **Entwicklermodus**, lesen Sie den Haftungsausschluss für die ausgewählte Einstellung, und klicken Sie auf Ja, um die Änderung zu übernehmen.

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>Bereitstellen einer APP über Wi-Fi-hololens (1. Gen)
1. Wählen Sie eine **x86** -Buildkonfiguration für Ihre APP aus, ![x86-Buildkonfiguration in Visual Studio](images/x86setting.png)
2. Wählen Sie im Dropdown Menü Bereitstellungs Ziel den **Remote Computer** aus ![Bereitstellungs Ziel für Remote Computer in Visual Studio](images/remotemachinesetting.png)
3. Wechseln C++ Sie für-und JavaScript-Projekte zu **Project > Eigenschaften > Konfigurations Eigenschaften > Debuggen**. Für C# -Projekte wird automatisch ein Dialogfeld angezeigt, in dem die Verbindung konfiguriert wird.
  a. Geben Sie die IP-Adresse Ihres Geräts in das Feld **Adresse** oder **Computer Name** ein. Suchen Sie die IP-Adresse in den hololens unter **Einstellungen > Netzwerk & Internet > Erweiterte Optionen**, oder Fragen Sie Cortana "Was ist meine IP-Adresse?".
  b. Legen Sie den Authentifizierungsmodus auf **Universelles (unverschlüsseltes Protokoll)** ![Dialogfeld "Remote Verbindung" in Visual Studio](images/remotedeploy.png)
4. Wählen Sie **Debuggen > Debuggen starten**](images/deploywithdebugging.png) aus, um die APP bereitzustellen und das Debuggen zu starten![starten ohne Debugging
5. Wenn Sie eine APP zum ersten Mal auf Ihrem PC auf Ihren hololens bereitstellen, werden Sie aufgefordert, eine PIN einzugeben. Befolgen Sie die Anweisungen unter Kopplung **Ihrer Geräte** .

## <a name="deploying-an-app-over-wi-fi---hololens-2"></a>Bereitstellen einer APP über Wi-Fi-hololens 2
1. Wählen Sie eine **Arm** -oder **ARM64** -Buildkonfiguration für Ihre APP ![ARM64 Buildkonfiguration in Visual Studio aus](images/arm64setting.png)
2. Wählen Sie im Dropdown Menü Bereitstellungs Ziel den **Remote Computer** aus ![Bereitstellungs Ziel für Remote Computer in Visual Studio](images/remotemachinesetting_arm64.png)
3. Wechseln C++ Sie für-und JavaScript-Projekte zu **Project > Eigenschaften > Konfigurations Eigenschaften > Debuggen**. Für C# -Projekte wird automatisch ein Dialogfeld angezeigt, in dem die Verbindung konfiguriert wird.
  a. Geben Sie die IP-Adresse Ihres Geräts in das Feld **Adresse** oder **Computer Name** ein. Suchen Sie die IP-Adresse in den hololens unter **Einstellungen > Netzwerk & Internet > Erweiterte Optionen**, oder Fragen Sie Cortana "Was ist meine IP-Adresse?".
  b. Legen Sie den Authentifizierungsmodus auf **Universelles (unverschlüsseltes Protokoll)** ![Dialogfeld "Remote Verbindung" in Visual Studio](images/remotedeploy.png)
4. Wählen Sie **Debuggen > Debuggen starten**](images/deploywithdebugging.png) aus, um die APP bereitzustellen und das Debuggen zu starten![starten ohne Debugging
5. Wenn Sie eine APP zum ersten Mal auf Ihrem PC auf Ihren hololens bereitstellen, werden Sie aufgefordert, eine PIN einzugeben. Befolgen Sie die Anweisungen unter Kopplung **Ihrer Geräte** .

Wenn sich die IP-Adresse der hololens-IP-Adresse ändert, können Sie die IP-Adresse des Ziel Computers ändern, indem Sie zu **Projekt > Eigenschaften > Konfigurations Eigenschaften > Debugging** wechseln.

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>Bereitstellen einer APP über USB-hololens (1. Gen)
1. Wählen Sie eine **x86** -Buildkonfiguration für Ihre APP aus, ![x86-Buildkonfiguration in Visual Studio](images/x86setting.png)
2. Wählen Sie im Dropdown Menü Bereitstellungs Ziel die Option **Gerät** aus,![Geräte Bereitstellung in Visual Studio](images/buildsettingsusbdeploy.png)
3. Wählen Sie **Debuggen > Debuggen starten**](images/deploywithdebugging.png) aus, um die APP bereitzustellen und das Debuggen zu starten![starten ohne Debugging
4. Wenn Sie eine APP zum ersten Mal auf Ihrem PC auf Ihren hololens bereitstellen, werden Sie aufgefordert, eine PIN einzugeben. Befolgen Sie die Anweisungen unter Kopplung **Ihrer Geräte** .

## <a name="deploying-an-app-over-usb---hololens-2"></a>Bereitstellen einer APP über USB-hololens 2
1. Wählen Sie eine **Arm** -oder **ARM64** -Buildkonfiguration für Ihre APP ![ARM64 Buildkonfiguration in Visual Studio aus](images/arm64setting.png)
2. Wählen Sie im Dropdown Menü Bereitstellungs Ziel die Option **Gerät** aus,![Geräte Bereitstellung in Visual Studio](images/buildsettingsusbdeploy_arm64.png)
3. Wählen Sie **Debuggen > Debuggen starten**](images/deploywithdebugging.png) aus, um die APP bereitzustellen und das Debuggen zu starten![starten ohne Debugging
4. Wenn Sie eine APP zum ersten Mal auf Ihrem PC auf Ihren hololens bereitstellen, werden Sie aufgefordert, eine PIN einzugeben. Befolgen Sie die Anweisungen unter Kopplung **Ihrer Geräte** .

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>Bereitstellen einer APP auf Ihrem lokalen PC-immersiven Headset

Befolgen Sie diese Anweisungen, wenn Sie ein Windows Mixed Reality-immersives Headset verwenden, das eine Verbindung mit Ihrem PC oder dem [Mixed Reality-Simulator](using-the-windows-mixed-reality-simulator.md)herstellt. In diesen Fällen können Sie Ihre APP einfach auf dem lokalen PC bereitstellen und ausführen.
1. Wählen Sie eine **x86** -oder **x64** -Buildkonfiguration für Ihre APP aus
2. Wählen Sie im Dropdown Menü Bereitstellungs Ziel die Option **lokaler Computer** aus.
3. Wählen Sie **Debuggen > Debuggen starten** aus, um die APP bereitzustellen

## <a name="pairing-your-device"></a>Koppeln Ihres Geräts

Wenn Sie eine APP von Visual Studio zum ersten Mal in ihren hololens bereitstellen, werden Sie aufgefordert, eine PIN einzugeben. Generieren Sie auf den hololens eine PIN, indem Sie die Einstellungs-APP starten. wechseln Sie zu **Update > für Entwickler** , und tippen Sie auf **paar**. Auf den hololens wird eine PIN angezeigt. Geben Sie diese PIN in Visual Studio ein. Nachdem die Kopplung abgeschlossen ist, tippen Sie auf den hololens auf **done** , um das Dialogfeld zu schließen. Dieser PC ist nun mit den hololens gekoppelt, und Sie können Apps automatisch bereitstellen. Wiederholen Sie diese Schritte für jeden nachfolgenden PC, der zum Bereitstellen von apps in ihren hololens verwendet wird.

Wenn Sie die hololens von allen Computern aufheben möchten, mit denen Sie gekoppelt war, starten Sie die app " **Einstellungen** ", navigieren Sie zu **Update > für Entwickler** , und tippen Sie auf " **Löschen**".

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>Bereitstellen einer APP für den hololens-Emulator (1st Gen)
1. Stellen Sie sicher, dass Sie **[den hololens-Emulator installiert](install-the-tools.md)** haben.
2. Wählen Sie eine **x86** -Buildkonfiguration für Ihre APP aus.
![x86-Buildkonfiguration in Visual Studio](images/x86setting.png)
3. Wählen Sie im Dropdown Menü Bereitstellungs Ziel![emulatorziel in Visual Studio aus, um den **Emulator hololens** zu aktivieren](images/deployemulator.png)
4. Wählen Sie **Debuggen > Debuggen starten**](images/deploywithdebugging.png) aus, um die APP bereitzustellen und das Debuggen zu starten![starten ohne Debugging

## <a name="deploying-an-app-to-the-hololens-2-emulator"></a>Bereitstellen einer APP auf dem hololens 2-Emulator
1. Stellen Sie sicher, dass Sie **[den hololens-Emulator installiert](install-the-tools.md)** haben.
2. Wählen Sie eine **x86** -oder **x64** -Buildkonfiguration für Ihre APP aus.
![x86-Buildkonfiguration in Visual Studio](images/x86setting.png)
3. Wählen Sie im Dropdown Menü "Bereitstellungs Ziel" den **Emulator "hololens 2** " aus![emulatorziel in Visual Studio](images/deployemulator2.png)
4. Wählen Sie **Debuggen > Debuggen starten**](images/deploywithdebugging.png) aus, um die APP bereitzustellen und das Debuggen zu starten![starten ohne Debugging

## <a name="graphics-debugger-for-hololens-1st-gen"></a>Grafik Debugger für hololens (1. Gen)

Die Visual Studio-Grafikdiagnose Tools sind beim Schreiben und Optimieren einer Holographic-APP sehr hilfreich. Ausführliche Informationen finden Sie [in der Visual Studio-Grafikdiagnose auf MSDN](https://msdn.microsoft.com/library/hh315751.aspx) .

**So starten Sie den Grafik Debugger**
1. Befolgen Sie die obigen Anweisungen für ein Gerät oder einen Emulator.
2. Wechseln Sie zu **debug> Grafik > Diagnose starten** .
3. Wenn Sie dies zum ersten Mal mit einem hololens tun, erhalten Sie möglicherweise den Fehler "Zugriff verweigert". Starten Sie die hololens neu, damit aktualisierte Berechtigungen wirksam werden, und wiederholen Sie den Vorgang.

## <a name="profiling"></a>Liert

Die Visual Studio-Profil Erstellungs Tools ermöglichen es Ihnen, die Leistung und Ressourcennutzung Ihrer APP zu analysieren. Dies umfasst Tools zur Optimierung der CPU, des Arbeitsspeichers, der Grafiken und der Netzwerk Verwendung. Ausführliche Informationen finden Sie [unter Ausführen von Diagnosetools ohne Debuggen auf MSDN](https://msdn.microsoft.com/library/dn957936.aspx) .

**So starten Sie die Profilerstellungstools mit hololens**
1. Befolgen Sie die obigen Anweisungen für ein Gerät oder einen Emulator.
2. Gehe zu **Debuggen > Diagnosetools ohne Debugging starten...**
3. Wählen Sie die Tools aus, die Sie verwenden möchten.
4. Klicken Sie auf **Start**
5. Wenn Sie dies zum ersten Mal mit einem hololens tun, erhalten Sie möglicherweise den Fehler "Zugriff verweigert". Starten Sie die hololens neu, damit aktualisierte Berechtigungen wirksam werden, und wiederholen Sie den Vorgang.

## <a name="debugging-an-installed-or-running-app"></a>Debuggen einer installierten oder laufenden app

Sie können Visual Studio zum Debuggen einer universellen Windows-App verwenden, die ohne Bereitstellung aus einem Visual Studio-Projekt installiert wird. Dies ist hilfreich, wenn Sie ein installiertes App-Paket debuggen möchten oder wenn Sie eine APP debuggen möchten, die bereits ausgeführt wird.
1. Wechseln Sie zu **debug-> andere debugziele > installiertes App-Paket Debuggen**
2. Wählen Sie das **Remote Computer** Ziel für hololens oder **den lokalen Computer** für immersive Headsets aus.
3. Geben Sie die **IP-Adresse** Ihres Geräts ein.
4. Wählen Sie den **universellen** Authentifizierungsmodus aus.
5. Im Fenster werden sowohl aktive als auch inaktive apps angezeigt. Wählen Sie den Inhalt aus, den Sie debuggen möchten.
6. Wählen Sie den zu debuggenden Codetyp aus (verwaltet, System eigen, gemischt).
7. Klicken Sie auf **Anfügen oder starten**

## <a name="see-also"></a>Weitere Informationen:
* [Installieren der Tools](install-the-tools.md)
* [Verwendung des HoloLens Emulators](using-the-hololens-emulator.md)
* [Bereitstellen und Debuggen von universelle Windows-Plattform-Apps (UWP)](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [Aktivieren des Geräts für die Entwicklung](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
