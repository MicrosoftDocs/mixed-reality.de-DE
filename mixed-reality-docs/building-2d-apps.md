---
title: Aktualisieren von 2D UWP-apps für mixed reality
description: Dieser Artikel beschreibt das Aktualisieren Ihrer vorhandenen 2D universelle Windows-Plattform-app auf HoloLens und Windows Mixed Reality immersive Headsets ausgeführt.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Direct2D-app, UWP, Flatfile-app, HoloLens, immersive Kopfhörer, app-Modell back-Schaltfläche "," app-Leiste "," DPI-Wert "," Resolution "," Skalieren
ms.openlocfilehash: 35a2e7774a79e35893821467f7e9ef8c004efa20
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595364"
---
# <a name="updating-2d-uwp-apps-for-mixed-reality"></a>Aktualisieren von 2D UWP-apps für mixed reality

Windows Mixed Reality ermöglicht Benutzern Hologramme angezeigt wird, als wären sie richtige für Sie in Ihrer Welt physisch oder digital. Im Prinzip sind HoloLens und die Desktop-PCs, die Sie, immersive Kopfhörer Zubehör anfügen Windows 10-Geräte; Dies bedeutet, dass Sie fast alle apps (Universelle Windows Plattform) in den Store als Direct2D-apps ausgeführt werden können.

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>Erstellen einer Direct2D-UWP-app für mixed reality

Der erste Schritt zum Onlineschalten einer Direct2D-app, mixed Reality-Headsets ist, Ihre app als eine standard-Direct2D-app auf Ihrem desktop ausgeführt.

### <a name="building-a-new-2d-uwp-app"></a>Erstellen einer neuen 2D UWP-app

Um eine neue Direct2D-app für mixed Reality zu erstellen, erstellen Sie einfach ein standard-2D-app (Universelle Windows Plattform). Es sind keine weiteren app-Änderungen erforderlich, damit diese app dann als ein Slate in mixed Reality ausführen.

Informationen zum Einstieg eine Direct2D-UWP-app erstellen, sehen Sie sich die [Erstellen Ihrer ersten app](https://docs.microsoft.com/windows/uwp/get-started/your-first-app) Artikel.

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>Schalten eine vorhandene 2D Store-app auf UWP

Wenn Sie bereits über eine Direct2D-Windows-app in den Store haben, müssen Sie zunächst sicherstellen, dass er die Windows 10 universelle Windows-Plattform (UWP) abzielt. Hier sind alle möglichen Ausgangspunkte, die Sie mit Ihrer Store-app noch heute möglicherweise:
<br>

|  Startpunkt  |  Zielplattform für die AppX-Manifests  |  Wie diese Universal stellen? | 
|----------|----------|----------|
|  Windows Phone (Silverlight)  |  Silverlight-App-Manifest |  [Migrieren zu WinRT](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx) | 
|  Windows Phone 8.1 Universal  |  8.1 AppX-Manifests, die keine Zielplattform  |  [Migrieren Sie Ihre app für die universelle Windows-Plattform](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows Store 8  |  8 AppX-Manifests, die keine Zielplattform  |  [Migrieren Sie Ihre app für die universelle Windows-Plattform](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows Store 8.1 Universal  |  8.1 AppX-Manifests, die keine Zielplattform  |  [Migrieren Sie Ihre app für die universelle Windows-Plattform](https://msdn.microsoft.com/library/mt148501.aspx) | 

Wenn eine 2D Unity-app, die heutzutage als Win32-app ("PC, Mac und Linux Standalone" Buildziel) erstellt haben, können Sie die mixed Reality abzielen, stattdessen Designer Unity in das Build-Ziel "Universal Windows Platform" wechseln.

Sprechen wir über Methoden, mit denen Sie Ihre app beschränken können, speziell für die Gerätefamilie Windows.Holographic mit HoloLens [unten](#publish-and-maintain-your-universal-app).

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>Führen Sie Ihre Direct2D-app in eine immersive Windows Mixed Reality-Kopfhörer

Wenn Sie Ihre Direct2D-app auf den desktop bereitgestellt haben, Sie entwickeln und auf dem Monitor ausprobiert, können Sie sich bereits in eine immersive desktop Kopfhörer herzlich!

Nur im Menü "Start" in den Kopfhörer mixed Reality und starten Sie die app von dort aus. Die desktop-Shell und die holographic Shell verwenden den gleichen Satz von UWP-apps, und so die app sollte schon vorhanden sein, nachdem Sie in Visual Studio bereitgestellt haben.

## <a name="targeting-both-immersive-headsets-and-hololens"></a>Die jeweils auf immersive Headsets und HoloLens

Herzlichen Glückwunsch! Ihre app verwendet nun die Windows 10 universelle Windows-Plattform (UWP).

Ihre app ist jetzt auf moderne Windows-Geräte, z. B. Desktop-, Mobile, Windows Mixed Reality immersive Headsets, Xbox und HoloLens, auch als künftigen Geräten unter Windows ausgeführt werden kann. Allerdings um tatsächlich alle diese Geräte als Ziel verwenden, müssen Sie sicherstellen, dass Ihre app die Gerätefamilie Windows.Universal ausgelegt ist.

### <a name="change-your-device-family-to-windowsuniversal"></a>Ändern Sie Ihre Gerätefamilie in Windows.Universal

Jetzt lassen Sie uns Ihre AppX-Manifests, um sicherzustellen, dass Ihre Windows 10-UWP-app kann auf HoloLens ausgeführt:
* Öffnen Sie die Datei Ihrer app-Lösung mit **Visual Studio** und navigieren Sie zu der app-Paketmanifest
* Klicken Sie mit der rechten Maustaste auf die **"Package.appxmanifest"** -Datei in der Projektmappe, und wechseln Sie zu **Anzeigecode**<br>
  ![Datei "Package.appxmanifest" im Projektmappen-Explorer](images/openappxmanifest-500px.png)<br>
* Sicherstellen Sie, dass Ihre Zielplattform Windows.Universal in den Abschnitt "Dependencies" ist.
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* Sparen Sie!

Wenn Sie für die Entwicklungsumgebung Visual Studio nicht verwenden, können Sie öffnen **"appxmanifest.xml"** im Text-Editor Ihrer Wahl, um sicherzustellen, dass Ihre Zielgruppen die **Windows.Universal**  *TargetDeviceFamily*.

### <a name="run-in-the-hololens-emulator"></a>Führen Sie im HoloLens Emulator

Nun, da Ihre UWP-app "Windows.Universal" abzielt, lassen Sie uns Ihre app erstellen, und führen Sie es der [Emulator für HoloLens](using-the-hololens-emulator.md).
* Stellen Sie sicher, dass [installiert den Emulator für HoloLens](install-the-tools.md).
* Wählen Sie in Visual Studio die **X86** -Konfiguration für Ihre app erstellen

  ![X86 erstellen-Konfiguration in Visual Studio](images/x86setting.png)<br>
* Wählen Sie **Emulator für HoloLens** im Dropdownmenü für die Bereitstellung-Ziel

  ![HoloLens-Emulator in der Liste der Bereitstellungsziele](images/deployemulator-500px.png)<br>
* Wählen Sie **Debuggen > Debuggen starten** zum Bereitstellen Ihrer app und dem Debuggen beginnen.
* Der Emulator startet und Ausführen der app.
* Versetzen Sie die app mit einer Tastatur, Maus und/oder ein Xbox-Controller in der ganzen Welt, um sie zu starten.

  ![Emulator für HoloLens geladen wird, mit einem UWP-Beispiel](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>Nächste Schritte

An diesem Punkt kann eine der zwei Dinge geschehen:
1. Ihre app wird der Begrüßungsbildschirm angezeigt und gestartet wird, nachdem sie im Emulator platziert wird! Prima!
2. Oder nachdem Sie eine laden-Animation für eine 2D – Hologramm angezeigt wird, laden wird beendet, und sehen Sie nur Ihre app die Splash-Bildschirm angezeigt. Dies bedeutet, dass es ist leider dauert es genauer untersucht, wie Sie Ihre app zum Leben in Mixed Reality zu verstehen.

Rufen Sie am unteren Rand die Ursache Ihrer UWP-app nicht, um auf HoloLens zu starten, müssen Sie debuggen.

### <a name="running-your-uwp-app-in-the-debugger"></a>Die UWP-app ausführen im debugger

Diese Schritte führt Sie durch die UWP-app mit Visual Studio-Debugger Debuggen.
* Wenn Sie nicht bereits geschehen, öffnen Sie die Projektmappe in Visual Studio. Ändern Sie das Ziel der **Emulator für HoloLens** und die Buildkonfiguration in **X86**.
* Wählen Sie **Debuggen > Debuggen starten** zum Bereitstellen Ihrer app und dem Debuggen beginnen.
* Platzieren Sie die app, in der ganzen Welt mit Ihrer Maus, Tastatur oder Xbox-Controller.
* Visual Studio sollte jetzt an einer beliebigen Stelle im app-Code unterbrochen.
  - Wenn Ihre app nicht sofort abstürzt bzw. den Debugger aufgrund eines nicht behandelten Fehlers unterbrechen, durchlaufen Sie dann einen Testdurchlauf der wichtigsten Funktionen Ihrer App an, stellen Sie sicher, dass alles, was ausgeführt wird und funktionsfähig. Sie können Fehler wie finden Sie in der Abbildung unten (Interne Ausnahmen, die behandelt werden). Um sicherzustellen, dass Sie nicht interne Fehler verpassen, die die benutzerfreundlichkeit Ihrer app auswirken, führen Sie Ihre automatisierten Tests und Komponententests aus, um sicherzustellen, dass alles wie erwartet verhält.

![Emulator für HoloLens geladen wird, mit einem UWP-Beispiel zeigt eine Systemausnahme](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>Aktualisieren der Benutzeroberflächenautomatisierungs

Nun, dass die UWP-app für immersive Headsets und/oder HoloLens als eine 2D-– Hologramm ausgeführt wird, wird als Nächstes wir sicherstellen, dass es ansprechender aussieht. Hier sind einige Punkte zu berücksichtigen:
* Windows Mixed Reality führen alle Direct2D-apps auf einer festen Auflösung und DPI-Wert, der entspricht, mit effektiven Pixeln 853 x 480. Überlegen Sie, ob es sich bei Ihrem Entwurf Optimierung in diesem Maßstab benötigt, und überprüfen Sie die Entwurfsrichtlinien unten, um Ihre Erfahrung auf HoloLens und immersive Headsets zu verbessern.
* Windows Mixed Reality [unterstützt keine](app-model.md) 2D live-Kacheln. Wenn Ihre Kernfunktionalität Informationen auf einer live-Kachel angezeigt wird, sollten Sie diese Informationen zurück in Ihre app zu verschieben, oder sehen Sie sich [3D app-startfeldern von](3d-app-launcher-design-guidance.md).

### <a name="2d-app-view-resolution-and-scale-factor"></a>Auflösung und Skalierung aufruffaktor des Direct2D-app

![Von reaktionsfähiges design](images/scale-500px.png)

Windows 10 verschiebt alle visuellen Entwurf von echten Bildschirmpixel, um die **effektiven Pixeln**. Bedeutet, dass Entwickler entwerfen ihre Benutzeroberfläche mit dem folgenden Windows 10 Human Interface Guidelines für die effektive Pixel, und Skalieren von Windows wird sichergestellt, dass die effektive Pixel der richtigen Größe zum Zweck der benutzerfreundlichkeit auf Geräten, Auflösungen, DPI, usw. Finden Sie in diesem [hervorragende Lesen auf MSDN](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx) sowie diese Informationen [BUILD-Präsentation](http://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx).

Auch bei die einzigartige Möglichkeit, apps in Ihrer Umgebung in einem Bereich von Abständen platzieren werden TV-ähnliche Anzeige entfernungen empfohlen, um die Übersichtlichkeit und die Interaktion mit Blicke/Bewegung zu erzeugen. Aus diesem Grund wird ein virtuelles Slate zu Hause Mixed Reality Ihrer Flatfile UWP Ansicht angezeigt:

**1280 x 720, 150 % DPI** (853 x 480 effektive Pixel)

Diese Lösung bietet mehrere Vorteile:
* Dieses Layout effektive Pixel müssen über die gleichen informationsdichte als ein Tablet oder einen kleinen Desktop.
* Sie entspricht den festen DPI-Wert und effektiven Pixeln für UWP-apps, die auf der Xbox One, von einem nahtlosen Benutzererlebnis auf Geräten ausgeführt wird.
* Diese Größe Ihren vorstellungen entspricht, wenn unsere Bereich des Betriebs entfernungen für apps in der ganzen Welt skaliert.

### <a name="2d-app-view-interface-design-best-practices"></a>Direct2D-app-Schnittstelle Entwurf bewährte anzeigen

**Führen Sie aus:**
* Führen Sie die [Windows 10 Human Interface Richtlinien (Benutzeroberflächen)](https://dev.windows.com/design) für Formatvorlagen, Schriftgrößen und Schaltflächengröße. HoloLens erfolgt die Arbeit, um sicherzustellen, dass Ihre app kompatiblen app-Muster, lesbaren Textgrößen und entsprechendes Treffer Ziel Größe hat.
* Stellen Sie sicher Ihre Benutzeroberfläche folgt bewährte Methoden für die [reaktionsfähiges Design](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx) , optimiert HoloLens eindeutige Auflösung und DPI-Wert zu suchen.
* Verwenden Sie die "light" Farbe-Design-Empfehlungen von Windows.

**Tue nicht:**
* Ändern Sie die Benutzeroberfläche zu erheblich in gemischte Realität, um sicherzustellen, dass Benutzern eine vertraute Erfahrung in und aus den Kopfhörer.

### <a name="understand-the-app-model"></a>Verstehen Sie das app-Modell

Die [app-Modell](app-model.md) für mixed Reality dient dem Mixed Reality nach Hause verwenden, in denen viele apps, die live zusammen. Stellen Sie sich die mixed Reality-Entsprechung des Desktops, führen Sie viele Direct2D-apps auf einmal. Dies hat Auswirkungen auf die app-Lebenszyklus, Kacheln und andere wichtige Features Ihrer App.

### <a name="app-bar-and-back-button"></a>App-Leiste und Schaltfläche "zurück"

2D Ansichten werden mit einer appleiste oben ihre Inhalte ergänzt. Die app-Leiste verfügt über zwei Punkte der app-spezifische Personalisierung:

**Titel:** zeigt die *"DisplayName"* der Kachel der app-Instanz zugeordnet

**Schaltfläche "zurück":** löst die *[BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* Ereignis aus, wenn Sie gedrückt. Back-Schaltfläche-Sichtbarkeit wird gesteuert, indem  *[SystemNavigationManager.AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)*.

![App Befehlsleisten-Benutzeroberfläche in Direct2D-app-Ansicht](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*App Befehlsleisten-Benutzeroberfläche in Direct2D-app-Ansicht*

### <a name="test-your-2d-apps-design"></a>Testen Sie Ihre Direct2D-app-Entwurf

Es ist wichtig zum Testen Ihrer app, um sicherzustellen, dass der Text lesbar ist, die Schaltflächen sind als Ziel gesetzt und die gesamte app fehlerfrei ist. Sie können [testen](testing-your-app-on-hololens.md) auf einem desktop Kopfhörer, eine HoloLens, einem Emulator oder einem touchgerät mit einer Auflösung von 1280 x 720 festgelegt @150%.

## <a name="new-input-possibilities"></a>Neue Eingabe Möglichkeiten

HoloLens verwendet erweiterte Tiefe Sensoren, finden in der ganzen Welt, und Benutzer sehen. Dies ermöglicht erweiterte gestensteuerung wie [Bloom](gestures.md#bloom) und [tippbewegung](gestures.md#air-tap). Auch aktivieren, leistungsstarke Mikrofone [voice-Erfahrungen](voice-input.md).

Mit Desktop Headsets können Benutzer während der Übertragung Controller verwenden, zeigen Sie auf die apps, und ergreifen. Sie können auch eine Gamepad, für Objekte mit ihren Blicke.

Windows übernimmt dieser Komplexität für UWP-apps, übersetzen Ihre [bestaunen](gaze.md), Gesten, Sprach- und Controller-Eingabe in motion [zeigerereignisse](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events) , die die Eingabeelemente Weg abstrahiert. Beispielsweise wird ein Benutzer möglicherweise eine tippbewegung mit ihre Westentasche durchgeführt oder den Select-Trigger auf einem Motion-Controller abgerufen, aber 2D Anwendungen müssen nicht wissen, wohin die Eingabe stammen – nur eine 2D Fingereingabe-Taste drücken, als ob Sie sich auf einem Touchscreen angezeigt.

Hier sind die allgemeinen Konzepte/Szenarien, die Sie für die Eingabe verstehen sollten, wenn Sie die UWP-app, HoloLens:
* [Bestaunen](gaze.md) ändert sich in der Hover-Ereignisse, die Menüs, Flyouts oder andere Elemente der Benutzeroberfläche für das anzeigen, indem Sie einfach um Ihre app gazing unerwartet ausgelöst werden können.
* Blicke ist nicht so präzise wie Mauseingaben. Verwendung dimensioniert Treffer Ziele für HoloLens, mobilen Anwendungen ähnelt. Kleine Elemente in der Nähe von den Rändern der app sind besonders schwierig diese zu interagieren.
* Benutzer müssen Eingabemodi zu scrollen zu ziehen, um zwei Finger Schwenken wechseln. Wenn Ihre app für Touch-Punkts entwickelt wurde, sollten Sie sicherstellen, dass keine wichtigen Funktionen, die hinter der zwei Finger Schwenken gesperrt ist. Wenn dies der Fall ist, sollten Sie in Betracht ziehen, alternative Eingabemechanismen wie Schaltflächen, die zwei-Finger-Schwenken initiieren können. Z. B. der Karten-app mit zwei-Finger-Schwenken vergrößern kann, aber verfügt über ein Plus, minus, und drehen Sie um die gleichen Zoom-Interaktionen mit einzelnen Klicks zu haben.

[Voice-Eingabe](voice-input.md) ist ein wichtiger Bestandteil der mixed Reality-Erfahrung. Wir haben alle APIs aktiviert, die in Windows 10, Cortana einschalten, wenn Sie einen Kopfhörer zu verwenden sind.

## <a name="publish-and-maintain-your-universal-app"></a>Veröffentlichen Sie und verwalten Sie Ihrer Universal-app

Sobald Ihre app einsatzbereit ist, Packen Sie Ihre app [an den Microsoft Store übermitteln](submitting-an-app-to-the-microsoft-store.md).

## <a name="see-also"></a>Siehe auch
* [App-Modell](app-model.md)
* [Blicke](gaze.md)
* [Aktion](gestures.md)
* [Motion-Controller](motion-controllers.md)
* [Voice](voice-input.md)
* [Übermitteln einer app an den Microsoft Store](submitting-an-app-to-the-microsoft-store.md)
* [Verwendung des HoloLens Emulators](using-the-hololens-emulator.md)
