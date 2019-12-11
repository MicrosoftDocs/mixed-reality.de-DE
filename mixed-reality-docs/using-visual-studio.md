---
title: Verwenden von Visual Studio zum Bereitstellen und Debuggen
description: Erfahren Sie, wie Sie Apps für HoloLens und Windows Mixed Reality mithilfe von Visual Studio erstellen, debuggen und bereitstellen.
author: pbarnettms
ms.author: pbarnett
ms.date: 10/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, Mixed Reality, debuggen, bereitstellen
ms.openlocfilehash: b7e6a8d538670a53de20a2f3a2850639e756da1a
ms.sourcegitcommit: 05fa75193059a2dac4b580a9eef7b6c4bb64d8d7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74830832"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Verwenden von Visual Studio zum Bereitstellen und Debuggen

Unabhängig davon, ob Sie DirectX oder Unity zur Entwicklung ihrer Mixed Reality-App verwenden möchten, zum Debuggen und Bereitstellen verwenden Sie Visual Studio. In diesem Abschnitt wird Folgendes erläutert:
* Bereitstellen von Anwendungen auf Ihrer HoloLens oder Ihrem immersiven Windows Mixed Reality-Headset mithilfe von Visual Studio.
* Verwenden des in Visual Studio integrierten HoloLens-Emulators.
* Debuggen von Mixed Reality-Apps.

## <a name="prerequisites"></a>Voraussetzungen
1. Installationsanweisungen finden Sie unter [Installieren der Tools](install-the-tools.md).
2. Erstellen Sie ein neues Projekt für Universelle Windows-Apps in Visual Studio.  Verwenden Sie für HoloLens (1. Gen.) Visual Studio 2017 oder höher.  Verwenden Sie für HoloLens 2 Visual Studio 2019 16.2 oder höher. C# und C++ werden unterstützt. (Oder befolgen Sie die Anweisungen zum [Erstellen einer App in Unity](holograms-100.md).)

## <a name="enabling-developer-mode"></a>Aktivieren des Entwicklermodus

Aktivieren Sie zunächst den **Entwicklermodus** auf Ihrem Gerät, damit Visual Studio eine Verbindung damit herstellen kann.

### <a name="hololens"></a>HoloLens
1. Schalten Sie die HoloLens ein, und setzen Sie sie auf.
2. Führen Sie die [Blütengeste](system-gesture.md#bloom) aus, um das Hauptmenü zu starten.
3. Betrachten Sie die Kachel **Einstellungen**, und führen Sie die [Zeigefingergeste](gaze-and-commit.md#composite-gestures) aus. Führen Sie die Zeigefingergeste ein zweites Mal aus, um die App in Ihrer Umgebung zu platzieren. Die Einstellungs-App wird gestartet, nachdem Sie sie platziert haben.
4. Wählen Sie das Menüelement **Aktualisieren** aus.
5. Wählen Sie das Menüelement **Für Entwickler** aus.
6. Aktivieren Sie den **Entwicklermodus**. Auf diese Weise können Sie in Ihrer HoloLens [Apps aus Visual Studio bereitstellen](using-visual-studio.md).
7. Optional: Scrollen Sie nach unten, und aktivieren Sie das **Geräteportal**. Auf diese Weise können Sie außerdem in Ihrer HoloLens eine Verbindung mit dem [Windows-Geräteportal](using-the-windows-device-portal.md) über einen Webbrowser herstellen.

### <a name="windows-pc"></a>Windows PC

Wenn Sie mit einem Windows Mixed Reality-Headset arbeiten, das mit dem PC verbunden ist, müssen Sie den **Entwicklermodus** auf dem PC aktivieren.
1. Navigieren Sie zu **Einstellungen**
2. Wählen Sie **Update und Sicherheit** aus
3. Wählen Sie **Für Entwickler** aus
4. Aktivieren Sie den **Entwicklermodus**, lesen Sie den Haftungsausschluss für die ausgewählte Einstellung, und klicken Sie dann auf „Ja“ um die Änderung zu übernehmen.

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>Bereitstellen einer App über WLAN: HoloLens (1. Gen.)
1. Wählen Sie eine **x86**-Buildkonfiguration für Ihre App aus ![x86-Buildkonfiguration in Visual Studio](images/x86setting.png)
2. Wählen Sie im Dropdownmenü für das Bereitstellungsziel **Remotecomputer** aus ![Bereitstellungsziel „Remotecomputer“ in Visual Studio](images/remotemachinesetting.png)
3. Navigieren Sie für C++- und JavaScript-Projekte zu **Projekt > Eigenschaften > Konfigurationseigenschaften > Debuggen**. Bei C#-Projekten wird automatisch ein Dialogfeld angezeigt, in dem Sie Ihre Verbindung konfigurieren können.
  a. Geben Sie die IP-Adresse Ihres Geräts im Feld **Adresse** oder **Computername** ein. Suchen Sie die IP-Adresse auf Ihrer HoloLens unter **Einstellungen > Netzwerk und Internet > Erweiterte Optionen**, oder fragen Sie Cortana "Wie heißt meine IP-Adresse?"
  b. Legen Sie den Authentifizierungsmodus auf **Universell (unverschlüsseltes Protokoll)** fest ![Remoteverbindungs-Dialogfeld in Visual Studio](images/remotedeploy.png)
4. Wählen Sie **Debuggen > Debuggen starten** aus, um Ihre App bereitzustellen und das Debuggen zu starten ![Starten ohne Debuggen in Visual Studio](images/deploywithdebugging.png)
5. Beim erstmaligen Bereitstellen einer App in Ihrer HoloLens von Ihrem Computer aus werden Sie zur Eingabe einer PIN aufgefordert. Befolgen Sie die Anweisungen unten zum **Koppeln Ihres Geräts**.

## <a name="deploying-an-app-over-wi-fi---hololens-2"></a>Bereitstellen einer App über WLAN: HoloLens 2
1. Wählen Sie eine **ARM**- oder **ARM64**-Buildkonfiguration für Ihre App aus ![ARM64-Buildkonfiguration in Visual Studio](images/arm64setting.png)
2. Wählen Sie im Dropdownmenü für das Bereitstellungsziel **Remotecomputer** aus ![Bereitstellungsziel „Remotecomputer“ in Visual Studio](images/remotemachinesetting_arm64.png)
3. Navigieren Sie für C++- und JavaScript-Projekte zu **Projekt > Eigenschaften > Konfigurationseigenschaften > Debuggen**. Bei C#-Projekten wird automatisch ein Dialogfeld angezeigt, in dem Sie Ihre Verbindung konfigurieren können.
  a. Geben Sie die IP-Adresse Ihres Geräts im Feld **Adresse** oder **Computername** ein. Suchen Sie die IP-Adresse auf Ihrer HoloLens unter **Einstellungen > Netzwerk und Internet > Erweiterte Optionen**, oder fragen Sie Cortana "Wie heißt meine IP-Adresse?"
  b. Legen Sie den Authentifizierungsmodus auf **Universell (unverschlüsseltes Protokoll)** fest ![Remoteverbindungs-Dialogfeld in Visual Studio](images/remotedeploy.png)
4. Wählen Sie **Debuggen > Debuggen starten** aus, um Ihre App bereitzustellen und das Debuggen zu starten ![Starten ohne Debuggen in Visual Studio](images/deploywithdebugging.png)
5. Beim erstmaligen Bereitstellen einer App in Ihrer HoloLens von Ihrem Computer aus werden Sie zur Eingabe einer PIN aufgefordert. Befolgen Sie die Anweisungen unten zum **Koppeln Ihres Geräts**.

Wenn sich die IP-Adresse Ihrer HoloLens ändert, können Sie die IP-Adresse des Zielcomputers ändern, indem Sie zu **Projekt > Eigenschaften > Konfigurationseigenschaften > Debuggen** navigieren.

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>Bereitstellen einer App über USB: HoloLens (1. Gen.)
1. Wählen Sie eine **x86**-Buildkonfiguration für Ihre App aus ![x86-Buildkonfiguration in Visual Studio](images/x86setting.png)
2. Wählen Sie im Dropdownmenü für das Bereitstellungsziel **Gerät** aus ![Gerätebereitstellung in Visual Studio](images/buildsettingsusbdeploy.png)
3. Wählen Sie **Debuggen > Debuggen starten** aus, um Ihre App bereitzustellen und das Debuggen zu starten ![Starten ohne Debuggen in Visual Studio](images/deploywithdebugging.png)
4. Beim erstmaligen Bereitstellen einer App in Ihrer HoloLens von Ihrem Computer aus werden Sie zur Eingabe einer PIN aufgefordert. Befolgen Sie die Anweisungen unten zum **Koppeln Ihres Geräts**.

## <a name="deploying-an-app-over-usb---hololens-2"></a>Bereitstellen einer App über USB: HoloLens 2
1. Wählen Sie eine **ARM**- oder **ARM64**-Buildkonfiguration für Ihre App aus ![ARM64-Buildkonfiguration in Visual Studio](images/arm64setting.png)
2. Wählen Sie im Dropdownmenü für das Bereitstellungsziel **Gerät** aus ![Gerätebereitstellung in Visual Studio](images/buildsettingsusbdeploy_arm64.png)
3. Wählen Sie **Debuggen > Debuggen starten** aus, um Ihre App bereitzustellen und das Debuggen zu starten ![Starten ohne Debuggen in Visual Studio](images/deploywithdebugging.png)
4. Beim erstmaligen Bereitstellen einer App in Ihrer HoloLens von Ihrem Computer aus werden Sie zur Eingabe einer PIN aufgefordert. Befolgen Sie die Anweisungen unten zum **Koppeln Ihres Geräts**.

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>Bereitstellen einer App auf Ihrem lokalen Computer: Immersives Headset

Befolgen Sie diese Anweisungen, wenn Sie ein immersives Windows Mixed Reality-Headset verwenden, das eine Verbindung mit Ihrem PC oder dem [Mixed Reality-Simulator](using-the-windows-mixed-reality-simulator.md) herstellt. Stellen Sie in diesen Fällen Ihre App einfach auf dem lokalen Computer bereit, und führen Sie sie aus.
1. Wählen Sie eine **x86**- oder **x64**-Buildkonfiguration aus
2. Wählen Sie im Dropdownmenü für das Bereitstellungsziel **Lokaler Computer** aus
3. Wählen Sie **Debuggen > Debuggen starten** aus, um Ihre App bereitzustellen und den Debugvorgang zu starten.

## <a name="pairing-your-device"></a>Koppeln Ihres Geräts

Beim erstmaligen Bereitstellen einer App aus Visual Studio in Ihrer HoloLens werden Sie zur Eingabe einer PIN aufgefordert. Generieren Sie auf der HoloLens eine PIN, indem Sie die Einstellungs-App starten, zu **Update > Für Entwickler** navigieren und auf **Koppeln** tippen. In der HoloLens wird eine PIN angezeigt; geben Sie diese PIN in Visual Studio ein. Tippen Sie nach dem vollzogenen Koppeln in Ihrer HoloLens auf **Fertig**, um das Dialogfeld zu schließen. Dieser PC ist nun mit der HoloLens gekoppelt, und Sie können Apps automatisch bereitstellen. Wiederholen Sie diese Schritte für jeden nachfolgenden PC, der zum Bereitstellen von Apps auf Ihrer HoloLens verwendet wird.

Um die Kopplung Ihrer HoloLens mit allen Computern, mit denen sie gekoppelt wurde, aufzuheben, starten Sie die App **Einstellungen**, navigieren Sie zu **Update > Für Entwickler**, und tippen Sie auf **Löschen**.

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>Bereitstellen einer App auf dem HoloLens-Emulator (1. Gen.)
1. Vergewissern Sie sich, dass Sie **[den HoloLens-Emulator installiert](install-the-tools.md)** haben.
2. Wählen Sie eine **x86**-Buildkonfiguration für Ihre App aus.
![x86-Buildkonfiguration in Visual Studio](images/x86setting.png)
3. Wählen Sie im Dropdownmenü für das Bereitstellungsziel **HoloLens-Emulator** aus ![Emulatorziel in Visual Studio](images/deployemulator.png)
4. Wählen Sie **Debuggen > Debuggen starten** aus, um Ihre App bereitzustellen und das Debuggen zu starten ![Starten ohne Debuggen in Visual Studio](images/deploywithdebugging.png)

## <a name="deploying-an-app-to-the-hololens-2-emulator"></a>Bereitstellen einer App auf dem HoloLens 2-Emulator
1. Vergewissern Sie sich, dass Sie **[den HoloLens-Emulator installiert](install-the-tools.md)** haben.
2. Wählen Sie eine **x86**- oder **x64**-Buildkonfiguration für Ihre App aus.
![x86-Buildkonfiguration in Visual Studio](images/x86setting.png)
3. Wählen Sie im Dropdownmenü für das Bereitstellungsziel **HoloLens 2-Emulator** aus ![Emulatorziel in Visual Studio](images/deployemulator2.png)
4. Wählen Sie **Debuggen > Debuggen starten** aus, um Ihre App bereitzustellen und das Debuggen zu starten ![Starten ohne Debuggen in Visual Studio](images/deploywithdebugging.png)

## <a name="graphics-debugger-for-hololens-1st-gen"></a>Grafikdebugger für HoloLens (1. Gen.)

Die Visual Studio-Grafikdiagnose-Tools sind beim Schreiben und Optimieren einer holografischen App sehr nützlich. Ausführliche Informationen finden Sie unter [Visual Studio-Grafikdiagnose auf MSDN](https://msdn.microsoft.com/library/hh315751.aspx).

**So starten Sie den Grafikdebugger**
1. Befolgen Sie die Anweisungen oben, um ein Gerät oder einen Emulator als Ziel festzulegen.
2. Navigieren Sie zu **Debuggen > Grafik > Diagnose starten**
3. Wenn Sie dies zum ersten Mal auf einer HoloLens ausführen, wird möglicherweise ein Fehler „Zugriff verweigert“ angezeigt. Starten Sie die HoloLens neu, damit aktualisierte Berechtigungen wirksam werden können, und wiederholen Sie den Vorgang.

## <a name="profiling"></a>Profilerstellung

Die Visual Studio-Tools zur Profilerstellung ermöglichen Ihnen das Analysieren von Leistung und Ressourcennutzung Ihrer App. Dies beinhaltet Tools zur Optimierung von CPU-, Arbeitsspeicher-, Grafik- und Netzwerkauslastung. Ausführliche Informationen finden Sie unter [Ausführen von Diagnosetools ohne Debuggen auf MSDN](https://msdn.microsoft.com/library/dn957936.aspx).

**So starten Sie die Profilerstellungstools in HoloLens**
1. Befolgen Sie die Anweisungen oben, um ein Gerät oder einen Emulator als Ziel festzulegen.
2. Navigieren Sie zu **Debuggen > Diagnosetools ohne Debuggen starten...**
3. Wählen Sie die Tools aus, die Sie verwenden möchten.
4. Klicken Sie auf **Start**.
5. Wenn Sie dies zum ersten Mal auf einer HoloLens ausführen, wird möglicherweise ein Fehler „Zugriff verweigert“ angezeigt. Starten Sie die HoloLens neu, damit aktualisierte Berechtigungen wirksam werden können, und wiederholen Sie den Vorgang.

## <a name="debugging-an-installed-or-running-app"></a>Debuggen einer installierten oder aktuell laufenden App

Sie können Visual Studio verwenden, um eine Universelle Windows-App zu debuggen, die ohne Bereitstellung aus einem Visual Studio-Projekt installiert wurde. Dies ist nützlich, wenn Sie ein installiertes App-Paket oder eine App debuggen möchten, die bereits ausgeführt wird.
1. Navigieren Sie zu **Debuggen > Andere Debugziele > Installiertes App-Paket debuggen**
2. Wählen Sie das Ziel **Remotecomputer** für HoloLens oder **Lokaler Computer** für immersive Headsets aus.
3. Geben Sie die **IP-Adresse** Ihres Geräts ein.
4. Wählen Sie den Authentifizierungsmodus **Universell** aus.
5. Im Fenster werden sowohl ausgeführte als auch inaktive Apps angezeigt. Suchen Sie die App aus, die Sie debuggen möchten.
6. Wählen Sie den zu debuggenden Codetyp aus (Verwaltet, Nativ, Gemischt)
7. Klicken Sie auf **Anfügen** oder **Start**

## <a name="see-also"></a>Weitere Informationen
* [Installieren der Tools](install-the-tools.md)
* [Verwendung des HoloLens Emulators](using-the-hololens-emulator.md)
* [Bereitstellen und Debuggen von UWP (Universelle Windows-Plattform)-Apps](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [Aktivieren Ihres Geräts für die Entwicklung](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
