---
title: Aktualisieren von 2D-UWP-Apps für gemischte Realität
description: In diesem Artikel wird beschrieben, wie Sie Ihre vorhandene 2D-universelle Windows-Plattform-App auf hololens und Windows Mixed Reality-immersiven Headsets aktualisieren.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 2D-APP, UWP, flatapp, hololens, immersives Headset, App-Modell, Schaltfläche "zurück", App-Leiste, dpi, Auflösung, Skalierung
ms.openlocfilehash: 46d2a9ca044dee977faecc84d610dc0811a4bfb7
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436979"
---
# <a name="updating-2d-uwp-apps-for-mixed-reality"></a>Aktualisieren von 2D-UWP-Apps für gemischte Realität

Windows Mixed Reality ermöglicht Benutzern das Anzeigen von holograms, als ob Sie sich in ihrer physischen oder digitalen Welt befinden. Im Kern sind sowohl hololens als auch Desktop-PCs, an die Sie die immersiven Headset-Zubehör anfügen, Windows 10-Geräte. Dies bedeutet, dass Sie in der Lage sind, fast alle universelle Windows-Plattform-Apps (UWP) im Store als 2D-apps auszuführen.

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>Erstellen einer 2D-UWP-App für gemischte Realität

Der erste Schritt bei der Einführung einer 2D-app in gemischte Reality-Headsets besteht darin, Ihre APP als standardmäßige 2D-App auf Ihrem Desktop Monitor zu starten.

### <a name="building-a-new-2d-uwp-app"></a>Neue 2D-UWP-APP wird aufgebaut

Um eine neue 2D-App für gemischte Realität zu erstellen, erstellen Sie einfach eine standardmäßige 2D-universelle Windows-Plattform-app (UWP). Es sind keine weiteren App-Änderungen erforderlich, damit diese APP als Slate in gemischter Realität ausgeführt wird.

Informationen zu den ersten Schritten bei der Erstellung einer 2D-UWP-App finden Sie im Artikel [Erstellen Ihrer ersten App](https://docs.microsoft.com/windows/uwp/get-started/your-first-app) .

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>Einbinden einer vorhandenen 2D Store-App in die UWP

Wenn Sie bereits über eine 2D-Windows-App im Store verfügen, müssen Sie zunächst sicherstellen, dass die Windows 10-universelle Windows-Plattform (UWP) als Ziel verwendet wird. Im folgenden finden Sie alle potenziellen Ausgangspunkte, die Sie möglicherweise mit ihrer Store-App haben:
<br>

|  Startpunkt  |  Ziel der AppX-Manifest-Plattform  |  Wie wird dies universell gemacht? | 
|----------|----------|----------|
|  Windows Phone (Silverlight)  |  Silverlight-App-Manifest |  [Migrieren zu WinRT](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx) | 
|  Windows Phone 8,1 universell  |  8,1 AppX-Manifest, das kein Platt Form Ziel enthält  |  [Migrieren Sie Ihre APP zum universelle Windows-Plattform](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows Store 8  |  8 AppX-Manifest, das kein Platt Form Ziel enthält  |  [Migrieren Sie Ihre APP zum universelle Windows-Plattform](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows Store 8,1 universell  |  8,1 AppX-Manifest, das kein Platt Form Ziel enthält  |  [Migrieren Sie Ihre APP zum universelle Windows-Plattform](https://msdn.microsoft.com/library/mt148501.aspx) | 

Wenn Sie bereits über eine 2D-Unity-App verfügen, die heute als Win32-App erstellt wurde (der "PC, Mac & eigenständige Linux-Buildziel)", können Sie auf gemischte Realität abzielen, indem Sie stattdessen Unity in das Build-Ziel "universelle Windows-Plattform" wechseln

Wir erläutern, wie Sie Ihre App mithilfe der [unten stehenden](#publish-and-maintain-your-universal-app)Gerätefamilie Windows. Holographic speziell auf hololens beschränken können.

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>Ausführen der 2D-app in einem Windows Mixed Reality-immersiven Headset

Wenn Sie Ihre 2D-App auf dem Desktop Computer bereitgestellt haben, auf dem Sie den Monitor entwickeln und ausprobieren, sind Sie bereits bereit, ihn in einem immersiven Desktop-Headset auszuprobieren!

Wechseln Sie einfach zum Startmenü im Mixed Reality-Headset, und starten Sie die APP von dort aus. Die Desktopshell und die Holographic Shell verwenden beide denselben UWP-apps, sodass die APP bereits vorhanden sein sollte, nachdem Sie Sie von Visual Studio aus bereitgestellt haben.

## <a name="targeting-both-immersive-headsets-and-hololens"></a>Ziel für immersive Headsets und hololens

Gratulation! Ihre APP verwendet jetzt die Windows 10-universelle Windows-Plattform (UWP).

Ihre APP ist jetzt in der Lage, auf den heutigen Windows-Geräten wie Desktop, Mobile, Xbox, Windows Mixed Reality-und hololens und zukünftigen Windows-Geräten ausgeführt zu werden. Allerdings müssen Sie sicherstellen, dass Ihre APP für die Windows. Universal-Gerätefamilie steht, damit Sie tatsächlich auf alle diese Geräte abzielen.

### <a name="change-your-device-family-to-windowsuniversal"></a>Ändern der Gerätefamilie in Windows. Universal

Wechseln wir nun zu Ihrem AppX-Manifest, um sicherzustellen, dass Ihre Windows 10-UWP-App auf hololens ausgeführt werden kann:
* Öffnen Sie die Projektmappendatei Ihrer APP mit **Visual Studio** , und navigieren Sie zum App-Paket Manifest.
* Klicken Sie mit der rechten Maustaste in der Projekt Mappe auf die Datei " **Package. appxmanifest** **", und** wechseln Sie<br>
  !["Package. appxmanifest" in Projektmappen-Explorer](images/openappxmanifest-500px.png)<br>
* Stellen Sie sicher, dass Ihre Zielplattform im Abschnitt "Abhängigkeiten" Windows. Universal ist.
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* Sicher!

Wenn Sie Visual Studio nicht für Ihre Entwicklungsumgebung verwenden, können Sie " **appxmanifest. XML** " im Text-Editor Ihrer Wahl öffnen, um sicherzustellen, dass Sie die **Windows. Universal** *targetdevicefamily*als Ziel verwenden.

### <a name="run-in-the-hololens-emulator"></a>Ausführen im hololens-Emulator

Nun, da ihre UWP-app "Windows. Universal" als Ziel hat, können Sie Ihre APP erstellen und im [hololens-Emulator](using-the-hololens-emulator.md)ausführen.
* Stellen Sie sicher, dass Sie [den hololens-Emulator installiert](install-the-tools.md)haben.
* Wählen Sie in Visual Studio die **x86** -Buildkonfiguration für Ihre APP aus.

  ![x86-Buildkonfiguration in Visual Studio](images/x86setting.png)<br>
* Wählen Sie im Dropdown Menü Bereitstellungs Ziel die Option **hololens-Emulator** aus.

  ![Hololens-Emulator in der Liste der Bereitstellungs Ziele](images/deployemulator-500px.png)<br>
* Wählen Sie **Debuggen > Debugging starten** , um die APP bereitzustellen und das Debugging zu starten
* Der Emulator startet Ihre APP und führt Sie aus.
* Mit Tastatur, Maus und/oder einem Xbox-Controller platzieren Sie die APP auf der Welt, um Sie zu starten.

  ![Hololens-Emulator mit einem UWP-Beispiel geladen](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>Nächste Schritte

An diesem Punkt kann eines von zwei Dingen eintreten:
1. Ihre APP zeigt ihren Begrüßungs Vorgang an und wird gestartet, nachdem Sie im Emulator abgelegt wurde. Prima!
2. Oder wenn Sie eine ladende Animation für ein 2D Hologram sehen, wird das Laden angehalten, und Ihre APP wird nur auf dem Begrüßungsbildschirm angezeigt. Dies bedeutet, dass etwas schief gelaufen ist, und es wird eine weitere Untersuchung durchgeführt, um zu verstehen, wie Sie Ihre APP in gemischter Realität umsetzen.

Um das Ende des Fehlers zu erreichen, was dazu führen kann, dass Ihre UWP-APP nicht in hololens gestartet wird, müssen Sie Debuggen.

### <a name="running-your-uwp-app-in-the-debugger"></a>Ausführen der UWP-App im Debugger

Diese Schritte führen Sie durch das Debuggen der UWP-App mit dem Visual Studio-Debugger.
* Wenn Sie dies nicht bereits getan haben, öffnen Sie die Projekt Mappe in Visual Studio. Ändern Sie das Ziel in den **hololens-Emulator** und die Buildkonfiguration in **x86**.
* Wählen Sie **Debuggen > Debugging starten** , um die APP bereitzustellen und das Debugging zu starten
* Platzieren Sie die APP mit der Maus, Tastatur oder dem Xbox-Controller auf der ganzen Welt.
* Visual Studio sollte nun irgendwo in Ihrem app-Code unterbrechen.
  - Wenn Ihre APP aufgrund eines nicht behandelten Fehlers nicht sofort abstürzen oder in den Debugger wechselt, durchlaufen Sie einen Testdurchlauf der Kern Features Ihrer APP, um sicherzustellen, dass alles ausgeführt wird und funktionsfähig ist. Möglicherweise werden Fehler wie unten dargestellt angezeigt (interne Ausnahmen, die behandelt werden). Um sicherzustellen, dass Sie keine internen Fehler vermissen, die sich auf die APP-Leistung auswirken, führen Sie die automatisierten Tests und Komponententests durch, um sicherzustellen, dass alles wie erwartet funktioniert.

![Hololens-Emulator mit einem UWP-Beispiel geladen, das eine System Ausnahme anzeigt](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>Aktualisieren der Benutzeroberfläche

Nun, da ihre UWP-App auf immersiven Headsets und/oder hololens als 2D Hologram ausgeführt wird, werden wir als nächstes sicherstellen, dass Sie sehr schön aussieht. Hier sind einige Punkte zu beachten:
* Windows Mixed Reality führt alle 2D-apps mit fester Auflösung und dpi-Wert aus, der 853x480 effektiven Pixeln entspricht. Berücksichtigen Sie, ob Ihr Design in dieser Skala verfeinert werden muss, und überprüfen Sie den unten stehenden Entwurfs Leit Faden, um Ihre Benutzeroberflächen und immersive Headsets zu verbessern.
* Windows Mixed Reality [unterstützt keine](app-model.md) 2D-Live Kacheln. Wenn die Kernfunktionalität Informationen zu einer Live-Kachel anzeigt, sollten Sie diese Informationen in Ihre APP zurück verschieben oder [3D-App-Launcher](3d-app-launcher-design-guidance.md)erkunden.

### <a name="2d-app-view-resolution-and-scale-factor"></a>2D-App-Ansichts Auflösung und Skalierungsfaktor

![Vom reaktionsfähigen Design](images/scale-500px.png)

Windows 10 verschiebt den gesamten visuellen Entwurf von "Real Screen Pixels" in " **effektive Pixel**". Das heißt, Entwickler entwerfen Ihre Benutzeroberfläche gemäß den Windows 10-Richtlinien für die Benutzeroberfläche für effektive Pixel, und die Windows-Skalierung stellt sicher, dass diese effektiven Pixel die richtige Größe für die Verwendbarkeit über Geräte, Auflösungen, dpi usw. sind Weitere Informationen zu dieser [buildpräsentation](https://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx)finden Sie [in diesem großartigen Lesevorgang auf MSDN](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx) .

Auch wenn die einzigartige Möglichkeit besteht, apps in einer Reihe von Entfernungen in ihrer Welt zu platzieren, wird empfohlen, TV-ähnliche Anzeige Abstände zu erzielen, um die beste Lesbarkeit und Interaktion mit Blick und Gesten zu erzielen. Aus diesem Grund zeigt ein virtuelles Slate in der Mixed Reality-Startseite ihre flache UWP-Ansicht an:

**1280X720, 150% dpi** (853x480 effektive Pixel)

Diese Lösung bietet mehrere Vorteile:
* Dieses effektive Pixel Layout hat ungefähr dieselbe Informationsdichte wie ein Tablet oder ein kleiner Desktop.
* Sie entspricht dem fixierten dpi-Wert und den effektiven Pixeln für UWP-apps, die auf Xbox One ausgeführt werden, und ermöglicht so Geräte übergreifende nahtlose Geräte
* Diese Größe sieht gut aus, wenn die Skalierung über die verschiedenen betriebsabstände für apps weltweit hinweg skaliert wird.

### <a name="2d-app-view-interface-design-best-practices"></a>bewährte Methoden zum Entwerfen von 2D-App-Ansichten

**Können**
* Befolgen Sie die [Windows 10 Human Interface Guidelines (hig)](https://dev.windows.com/design) für Stile, Schriftgrößen und Schaltflächen Größen. Hololens führt die Arbeit aus, um sicherzustellen, dass Ihre APP über kompatible App-Muster, lesbare Textgrößen und geeignete Treffer Zielgrößen verfügt.
* Stellen Sie sicher, dass Ihre Benutzeroberfläche die bewährten Methoden für das [reaktionsfähige Design](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx) befolgt, um die einzigartige Auflösung und den dpi-dpi-
* Verwenden Sie die "Light"-Farbdesign Empfehlungen von Windows.

**Tue nicht:**
* Ändern Sie die Benutzeroberfläche in gemischter Realität zu stark, um sicherzustellen, dass Benutzer über eine vertraute Benutzeroberfläche verfügen.

### <a name="understand-the-app-model"></a>Grundlegendes zum App-Modell

Das [App-Modell](app-model.md) für Mixed Reality ist für die Verwendung der Mixed Reality-Startseite konzipiert, in der viele apps miteinander verbunden sind. Stellen Sie sich dies als das Mixed Reality-Äquivalent des Desktops vor, in dem Sie viele 2D-apps gleichzeitig ausführen. Dies hat Auswirkungen auf den Lebenszyklus von apps, Kacheln und andere wichtige Features Ihrer APP.

### <a name="app-bar-and-back-button"></a>App-Leiste und zurück-Schaltfläche

2D-Ansichten werden mit einer APP-Leiste oberhalb ihres Inhalts ergänzt. Die APP-Leiste verfügt über zwei Punkte der APP-spezifischen Personalisierung:

**Title:** zeigt den *Display Name* der der app-Instanz zugeordneten Kachel an.

**Zurück-Schaltfläche:** löst beim Drücken das *[Rück](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* gerufene Ereignis aus. Die Sichtbarkeit der Schaltfläche "zurück" wird durch *[systemnavigationmanager. appviewbackbuttonvisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)* gesteuert.

![App-leisten-UI in der 2D-App-Ansicht](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*Benutzeroberfläche der APP-Leiste in der 2D-App*

### <a name="test-your-2d-apps-design"></a>Testen des Entwurfs Ihrer 2D-App

Es ist wichtig, Ihre APP zu testen, um sicherzustellen, dass der Text lesbar ist, die Schaltflächen targetable sind und die gesamte App korrekt aussieht. Sie können auf einem Desktop-Headset, hololens, einem Emulator oder einem Fingerabdruck Gerät [Testen](testing-your-app-on-hololens.md) , bei dem die Auflösung auf 1.280 x 720 @150% festgelegt ist.

## <a name="new-input-possibilities"></a>Neue Eingabemöglichkeiten

Hololens verwendet erweiterte tiefen Sensoren, um die Welt anzuzeigen und Benutzer anzuzeigen. Dies ermöglicht erweiterte Handgesten wie z. b. [Bloom](system-gesture.md#bloom) und [Luft tippen](gaze-and-commit.md#composite-gestures). Leistungsstarke Mikrofone ermöglichen auch [Spracherfahrung](voice-input.md).

Mit Desktop-Headsets können Benutzer Bewegungs Controller verwenden, um auf apps zu verweisen und Maßnahmen zu ergreifen. Sie können auch einen Gamepad verwenden, der auf Objekte mit dem Blick abzielt.

Windows kümmert sich um all diese Komplexität für UWP-apps und übersetzt Ihren [Blick](gaze-and-commit.md), Gesten, sprach-und Bewegungs Controller Eingaben in [Zeiger Ereignisse](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events) , die den Eingabe Mechanismus abstrahieren. Ein Benutzer hat z. b. möglicherweise eine Luft tippen oder den SELECT-Auslösevorgang auf einem Motion Controller abgerufen, aber 2D-Anwendungen müssen nicht wissen, woher die Eingabe stammt. es wird nur ein 2D-touchpress angezeigt, wie bei einem Touchscreen.

Im folgenden finden Sie die grundlegenden Konzepte und Szenarios, die Sie für die Eingabe verstehen sollten, wenn Sie Ihre UWP-app in hololens bringen:
* Der [Blick](gaze-and-commit.md) wandelt sich in Hover-Ereignisse um, die unerwartet Menüs, Flyouts oder andere Elemente der Benutzeroberfläche aufklappen können, um nur durch das Überprüfen der APP herum zu navigieren.
* Der Blick ist nicht so präzise wie die Maus Eingaben. Verwenden Sie für hololens entsprechend große Treffer Ziele, ähnlich wie bei mobilen Anwendungen mit Touchscreen. Kleine Elemente in der Nähe der Kanten der APP sind besonders schwer zu interagieren.
* Benutzer müssen die Eingabemodi wechseln, damit Sie vom Bildlauf zu Drag & Drop auf zwei Finger schwenken wechseln können. Wenn Ihre APP für Touch-Eingaben konzipiert wurde, sollten Sie sicherstellen, dass keine größeren Funktionen hinter zwei Finger schwenken gesperrt sind. Wenn dies der Fall ist, sollten Sie über alternative Eingabe Mechanismen wie Schaltflächen verfügen, die zwei Finger schwenken initiieren können. Beispielsweise kann die Maps-APP mit zwei Finger schwenken vergrößert werden, verfügt aber über eine Plus-, minus-und Drehungs Schaltfläche, um die gleichen Zoom Interaktionen mit nur einem Mausklick zu simulieren.

[Spracheingaben](voice-input.md) sind ein wichtiger Bestandteil der gemischten Realität. Wir haben alle sprach-APIs in Windows 10 aktiviert, die Cortana verwenden, wenn Sie ein Headset verwenden.

## <a name="publish-and-maintain-your-universal-app"></a>Veröffentlichen und verwalten Sie Ihre universelle App

Sobald Ihre APP ausgeführt wird, Verpacken Sie Ihre APP, um [Sie an den Microsoft Store zu senden](submitting-an-app-to-the-microsoft-store.md).

## <a name="see-also"></a>Weitere Informationen:
* [App-Modell](app-model.md)
* [Anvisieren mit dem Kopf und Ausführen](gaze-and-commit.md)
* [Motion-Controller](motion-controllers.md)
* [Spracheingabe](voice-input.md)
* [Senden einer App an den Microsoft Store](submitting-an-app-to-the-microsoft-store.md)
* [Verwendung des HoloLens Emulators](using-the-hololens-emulator.md)
