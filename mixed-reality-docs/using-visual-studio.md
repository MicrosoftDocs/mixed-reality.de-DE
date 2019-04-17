---
title: Mithilfe von Visual Studio bereitstellen und Debuggen
description: So erstellen, Debuggen und Bereitstellen von apps für HoloLens und Windows Mixed Reality mithilfe von Visual Studio.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Visual Studio, HoloLens, Mixed Reality, Debuggen, bereitstellen
ms.openlocfilehash: 6bd47d7212d321791a11ff4db91c3e172c91f463
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594875"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Mithilfe von Visual Studio bereitstellen und Debuggen

An, ob Sie DirectX oder Unity verwenden, um Ihre mixed Reality-app entwickeln möchten, verwenden Sie Visual Studio zum Debuggen und bereitstellen. In diesem Abschnitt lernen Sie Folgendes:
* Informationen zum Bereitstellen von Anwendungen für Ihre HoloLens oder Windows Mixed Reality immersive Kopfhörer über Visual Studio.
* So verwenden Sie die HoloLens-Emulator in Visual Studio integriert.
* Informationen zum Debuggen von mixed Reality-apps.

## <a name="prerequisites"></a>Vorraussetzungen
1. Finden Sie unter [Installieren der Tools](install-the-tools.md) installationsanweisungen.
2. Erstellen Sie ein neues Projekt für die universelle Windows-app in Visual Studio 2015 Update 1 oder Visual Studio 2017. C#, C++, und JavaScript-Projekte werden unterstützt. (Oder führen Sie die Anweisungen, um [einen Build erstellen Sie eine app in Unity](holograms-100.md).)

## <a name="enabling-developer-mode"></a>Aktivieren des Entwicklermodus

Aktivieren Sie zunächst **Entwicklermodus** auf Ihrem Gerät, damit Visual Studio hergestellt werden kann.

### <a name="hololens"></a>HoloLens
1. Aktivieren Sie Ihre HoloLens und auf dem Gerät abgelegt.
2. Führen Sie die [Blütengeste](gestures.md#bloom) aus, um das Hauptmenü zu starten.
3. Bestaunen an die **Einstellungen** Kachel, und führen Sie die [tippbewegung](gestures.md#air-tap) Bewegung. Führen Sie die Zeigefingergeste ein zweites Mal aus, um die App in Ihrer Umgebung zu platzieren. Die Einstellungs-App wird gestartet, nachdem Sie sie platziert haben.
4. Wählen Sie das Menüelement **Aktualisieren** aus.
5. Wählen Sie das Menüelement **Für Entwickler** aus.
6. Aktivieren Sie den **Entwicklermodus**. Dies können Sie [Bereitstellen von apps aus Visual Studio](using-visual-studio.md) auf Ihre HoloLens.
7. Optional: Scrollen Sie nach unten, und aktivieren Sie auch **Device Portal**. Dies können Sie zudem für die Verbindung der [Windows Device Portal](using-the-windows-device-portal.md) auf Ihre HoloLens über einen Webbrowser.

### <a name="windows-pc"></a>Windows-PC

Wenn Sie mit einer Windows Mixed Reality-Kopfhörer, die mit dem PC verbundenes arbeiten, müssen Sie aktivieren **Entwicklermodus** auf dem PC.
1. Wechseln Sie zu **Einstellungen**
2. Wählen Sie **Update und Sicherheit**
3. Wählen Sie **für Entwickler**
4. Aktivieren Sie **Entwicklermodus**, lesen Sie den Haftungsausschluss für die Einstellung, die Sie ausgewählt haben, und klicken Sie auf "Ja", um die Änderung zu übernehmen.

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>Bereitstellen einer app über Wi-Fi - HoloLens (1. Generation)
1. Wählen Sie eine **X86** Buildkonfiguration für Ihre app ![X86-Konfiguration in Visual Studio erstellen](images/x86setting.png)
2. Wählen Sie **Remotecomputer** im Dropdownmenü für die Bereitstellung-Ziel ![Remotecomputer Bereitstellungsziel in Visual Studio](images/remotemachinesetting.png)
3. Für C++ und JavaScript-Projekten, wechseln Sie zu **Projekt > Eigenschaften > Konfigurationseigenschaften > Debugging**. Für C# Projekte, ein Dialogfeld-wird automatisch Popup zum Konfigurieren der Verbindung.
  a. Geben Sie die IP-Adresse Ihres Geräts bei der **Adresse** oder **Computername** Feld. Suchen Sie die IP-Adresse auf Ihre HoloLens unter **Einstellungen > Netzwerk und Internet > Erweiterte Optionen**, oder Sie können Cortana Fragen "Was ist meine IP-Adresse?"
  b. Legen Sie den Authentifizierungsmodus auf **universell (unverschlüsseltes Protokoll)**![Remoteverbindung Dialogfeld in Visual Studio](images/remotedeploy.png)
4. Wählen Sie **Debuggen > Debuggen starten** zum Bereitstellen Ihrer app, und starten Sie das Debuggen![Starten ohne Debugging in Visual Studio](images/deploynodebugging.png)
5. Beim ersten einer app auf Ihrem HoloLens von Ihrem PC bereitstellen, werden Sie für eine PIN aufgefordert. Führen Sie die **koppeln Ihr Gerät** Anweisungen unten.

Wenn Ihre HoloLens IP-Adresse ändert, können Sie die IP-Adresse des Zielcomputers ändern, indem Sie zu **Projekt > Eigenschaften > Konfigurationseigenschaften > Debuggen**

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>Bereitstellen einer app per USB - HoloLens (1. Generation)
1. Wählen Sie eine **X86** Buildkonfiguration für Ihre app ![X86-Konfiguration in Visual Studio erstellen](images/x86setting.png)
2. Wählen Sie **Gerät** im Dropdownmenü für die Bereitstellung-Ziel![gerätebereitstellung in Visual Studio](images/buildsettingsusbdeploy.png)
3. Wählen Sie **Debuggen > Debuggen starten** zum Bereitstellen Ihrer app, und starten Sie das Debuggen![Starten ohne Debugging in Visual Studio](images/deploynodebugging.png)
4. Beim ersten einer app auf Ihrem HoloLens von Ihrem PC bereitstellen, werden Sie für eine PIN aufgefordert. Führen Sie die **koppeln Ihr Gerät** Anweisungen unten.

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>Bereitstellen einer app auf Ihrem lokalen PC - immersive Kopfhörer

Befolgen Sie diese Anweisungen, wenn eine immersive Windows Mixed Reality-Kopfhörer verwenden, die Verbindung mit Ihrem PC oder [Mixed Reality-Simulator](using-the-windows-mixed-reality-simulator.md). In diesen Fällen einfach bereitstellen Sie und führen Sie der app auf dem lokalen Computer aus.
1. Wählen Sie eine **X86** oder **X64** -Konfiguration für Ihre app erstellen
2. Wählen Sie **lokalen Computer** im Dropdownmenü für die Bereitstellung-Ziel
3. Wählen Sie **Debuggen > Debuggen starten** zum Bereitstellen Ihrer app, und starten Sie das Debuggen

## <a name="pairing-your-device---hololens-1st-gen"></a>Koppeln Ihr Gerät - HoloLens (1. Generation)

Bei der ersten Bereitstellung eine app aus Visual Studio zu Ihrem HoloLens, werden Sie für eine PIN aufgefordert. Generieren Sie auf die HoloLens, eine PIN durch die Einstellungen-app starten, wechseln Sie zur **Update > für Entwickler** und tippen Sie auf **Paar**. Eine PIN wird auf Ihrer HoloLens angezeigt werden; Geben Sie diese PIN in Visual Studio an. Nach der Kopplung abgeschlossen ist, tippen Sie auf **Fertig** auf Ihre HoloLens, um das Dialogfeld zu schließen. Dieser PC ist jetzt mit der HoloLens gekoppelt und können zum Bereitstellen von apps automatisch. Wiederholen Sie diese Schritte für jede nachfolgende PC, die zum Bereitstellen von apps für Ihre HoloLens verwendet wird.

Starten Sie zum Aufheben-Paar Ihrer HoloLens von allen Computern, die es zugeordnet wurde, die **Einstellungen** wechseln Sie zur app **Update > für Entwickler** und tippen Sie auf **löschen**.

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>Bereitstellen einer app auf die HoloLens (1. Generation) Emulator
1. Stellen Sie sicher, dass  **[installiert den Emulator für HoloLens](install-the-tools.md)**.
2. Wählen Sie eine **X86** -Konfiguration für Ihre app erstellen.
![X86 erstellen-Konfiguration in Visual Studio](images/x86setting.png)
3. Wählen Sie **Emulator für HoloLens** im Dropdownmenü für die Bereitstellung-Ziel![emulatorziel in Visual Studio](images/deployemulator.png)
4. Wählen Sie **Debuggen > Debuggen starten** zum Bereitstellen Ihrer app, und starten Sie das Debuggen![Starten ohne Debugging in Visual Studio](images/deploynodebugging.png)

## <a name="graphics-debugger"></a>Grafikdebugger

Visual Studio-Grafikdiagnose-Tools sind sehr hilfreich, wenn schreiben und Optimieren einer Holographic-app. Finden Sie unter [Visual Studio-Grafikdiagnose auf MSDN](https://msdn.microsoft.com/library/hh315751.aspx) Weitere Details.

**Um dem Grafikdebugger starten**
1. Befolgen Sie obige Anweisungen, um ein Gerät oder emulator
2. Wechseln Sie zu **Debuggen > Grafiken > Diagnose starten**
3. Beim ersten, die Sie mit einem HoloLens dazu, erhalten Sie möglicherweise einen Fehler "Zugriff verweigert". Starten Sie Ihre HoloLens, um die aktualisierten Berechtigungen wirksam, und wiederholen Sie den Vorgang neu.

## <a name="profiling"></a>Die profilerstellung

Die Visual Studio-Profilerstellungstools können Sie Ihrer app zu Leistung und analysieren. Dies umfasst Tools zum Optimieren der CPU, Arbeitsspeicher, Grafiken und Netzwerk verwenden. Finden Sie unter [Ausführen von Diagnosetools ohne debugging auf MSDN](https://msdn.microsoft.com/library/dn957936.aspx) Weitere Details.

**So starten Sie die Profilerstellungstools mit HoloLens**
1. Befolgen Sie obige Anweisungen, um ein Gerät oder emulator
2. Wechseln Sie zu **Debuggen > Diagnosetools ohne Debuggen starten...**
3. Wählen Sie die Tools, die Sie verwenden möchten.
4. Klicken Sie auf **starten**
5. Beim ersten, die Sie mit einem HoloLens dazu, erhalten Sie möglicherweise einen Fehler "Zugriff verweigert". Starten Sie Ihre HoloLens, um die aktualisierten Berechtigungen wirksam, und wiederholen Sie den Vorgang neu.

## <a name="debugging-an-installed-or-running-app"></a>Debuggen einer app installierten oder ausgeführten

Sie können Visual Studio verwenden, um eine universelle Windows-app zu debuggen, die installiert wird, ohne die Bereitstellung aus Visual Studio-Projekt. Dies ist nützlich, wenn Sie eine installierte app-Paket debuggen möchten, oder sollten Sie eine app zu debuggen, die bereits ausgeführt wird.
1. Wechseln Sie zu **anderen Debug "Debuggen ->" installiertes App-Paket Debuggen-Ziele >**
2. Wählen Sie die **Remotecomputer** Ziel für HoloLens oder **lokalen Computer** für immersive Headsets.
3. Geben Sie Ihres Geräts **IP-Adresse**
4. Wählen Sie die **universelle** Authentifizierungsmodus
5. Das Fenster zeigt sowohl ausgeführte als auch inaktive apps. Wählen Sie das, was Sie debuggen möchten.
6. Wählen Sie den Code zum Debuggen (verwaltete, systemeigene, gemischt)
7. Klicken Sie auf **Anfügen** oder **starten**

## <a name="see-also"></a>Siehe auch
* [Installieren der tools](install-the-tools.md)
* [Verwendung des HoloLens Emulators](using-the-hololens-emulator.md)
* [Bereitstellen und Debuggen von apps für universelle Windows-Plattform (UWP)](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [Aktivieren Sie das Gerät für die Entwicklung](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
