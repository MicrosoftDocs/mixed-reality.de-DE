---
title: Grundlagen der MR 100 – erste Schritte mit Unity
description: Erfahren Sie, wie Sie Ihre erste einfache mixed Reality-"Hello World"-Anwendung zu erstellen.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Gemischte Realität, Windows Mixed Reality, HoloLens, immersive Vr, Mr, ersten Schritten erhalten – Hologramm, Academy, Tutorial
ms.openlocfilehash: fd3bed955e80ec18b7be500adbdb0fcb7062d129
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993622"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a>MR Basics 100: Erste Schritte mit Unity

Dieses Tutorial führt Sie durch die Erstellung einer grundlegenden mixed Reality-Apps, die mit Unity erstellt.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td>MR Basics 100: Erste Schritte mit Unity</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Vorraussetzungen

* Ein Windows 10-PCs mit dem richtigen konfiguriert [-Tools installiert](install-the-tools.md).

## <a name="chapter-1---create-a-new-project"></a>Kapitel 1: Erstellen eines neuen Projekts

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

Um eine app mit Unity zu erstellen, müssen Sie zunächst ein Projekt zu erstellen. Dieses Projekt ist in einigen Ordnern organisiert, die wichtigste von denen Ihr Ordner "Assets" ist. Dies ist der Ordner, der alle Ressourcen enthält, die Sie importieren, von Erstellung digitaler Inhalte-Tools, z. B. Maya, Max. Kino 4D oder Photoshop, alle Code, den Sie mit Visual Studio oder Ihrem bevorzugten Code-Editor erstellen und eine beliebige Anzahl von Inhaltsdateien, dass Unity, als Sie erstellt kombinieren Sie Szenen , Animationen und andere Ressourcentypen "Unity" im Editor.

Zum Erstellen und Bereitstellen von UWP-apps, kann Unity das Projekt als Visual Studio-Projektmappe exportieren, die alle notwendigen Asset und Codedateien enthalten soll.

1. Starten Sie Unity
2. Wählen Sie **neu**
3. Geben Sie einen Projektnamen ein (z.B.) "MixedRealityIntroduction")
4. Geben Sie einen Speicherort zum Speichern des Projekts
5. Stellen Sie sicher die **3D** Umschaltfläche aktiviert ist
6. Wählen Sie **Projekt erstellen**

Herzlichen Glückwunsch, sind Sie alle Setup, um mit den Anpassungen mixed Reality noch heute loszulegen.

## <a name="chapter-2---setup-the-camera"></a>Kapitel 2: Einrichten der Kamera

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

Die Unity-Main Camera behandelt Head nachverfolgen und stereoskopische Rendering. Es gibt einige Änderungen an der Main-Kamera zu vornehmen, mit dem mixed Reality.
1. Wählen Sie die Datei > neue Szene

Zuerst, es wird einfacher sein, um das Layout von Ihrer app, wenn Sie sich, die Anfangsposition des Benutzers als vorstellen (**X**: 0, **Y**: 0, **Z**: 0). Da die Main Camera Bewegung des Benutzers Head nachverfolgt, kann die Anfangsposition des Benutzers festgelegt werden, durch die Position der Kamera Main festlegen.
1. Wählen Sie **Main Camera** in die **Hierarchie** Bereich
2. In der **Inspektor** Bereich, suchen Sie nach der **transformieren** -Komponente, und Ändern der **Position** aus (**X**: 0, **Y**: 1, **Z**:-10), (**X**: 0, **Y**: 0, **Z**: 0)

Zweitens, benötigt die Kamera-Standardhintergrund einige Überlegungen.

**Für HoloLens Anwendungen**, die reale Welt sollte angezeigt werden hinter alles, was die Kamera gerendert wird, nicht auf eine Textur Skybox.
1. Mit der **Main Camera** noch ausgewählt, die der **Hierarchie** Bereich, suchen Sie nach der **Kamera** -Komponente in die **Inspektor** Bereich, und ändern Sie die **Löschen Flags** Dropdownliste **Skybox** zu **Volltonfarbe**.
2. Wählen Sie die **Hintergrund** Farbauswahl angezeigt, und ändern Sie die **RGBA** Werte (0, 0, 0, 0)

**Für mixed Reality-Anwendungen, die speziell für Programmentwickler konzipiert immersive Headsets**, verwenden wir die standardmäßigen Skybox Textur, in der Unity bietet.
1. Mit der **Main Camera** noch ausgewählt, die der **Hierarchie** Bereich, suchen Sie nach der **Kamera** -Komponente in die **Inspector** Bereich, und behalten Sie die **Löschen Flags** Dropdownliste aus, um **Skybox**.

Drittens: lassen Sie uns betrachten Sie die nahezu vorderen Clippingebene in Unity und verhindern Sie Objekte gerendert zu nahe an die Benutzer Augen wie ein Benutzer, ein Objekt erreicht oder ein Objekt einen Benutzer erreicht.

**Für HoloLens Anwendungen**, die nahezu vorderen Clippingebene kann festgelegt werden, um die [HoloLens empfohlen](camera-in-unity.md#clip-planes) 0.85 Zähler.
1. Mit der **Main Camera** noch ausgewählt, die der **Hierarchie** Bereich, suchen Sie nach der **Kamera** -Komponente in die **Inspektor** Bereich, und ändern Sie die **Am vorderen Clippingebene** Feld von der Standardeinstellung **0.3** , die HoloLens empfohlen **0,85**.

**Für mixed Reality-Anwendungen, die speziell für Programmentwickler konzipiert immersive Headsets**, wir können die Standardeinstellung, die Unity bietet.
1. Mit der **Main Camera** noch ausgewählt, die der **Hierarchie** Bereich, suchen Sie nach der **Kamera** -Komponente in die **Inspector** Bereich, und behalten Sie die **Am vorderen Clippingebene** Feld auf den Standardwert **0.3**.

Lassen Sie uns speichern Sie abschließend unseren Fortschritt bisher. Wählen Sie zum Speichern der Änderungen für die Szene **Datei > Szene speichern unter**, benennen Sie die Szene **Main**, und wählen Sie **speichern**.

## <a name="chapter-3---setup-the-project-settings"></a>Kapitel 3 – Setup den Projekteinstellungen

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

In diesem Kapitel wird festgelegt einige Einstellungen der Unity-Projekt, die uns helfen Ziel die Windows Holographic-SDK für die Entwicklung. Wir werden auch einige Qualität-Einstellungen für die Anwendung festlegen. Zum Schluss stellen wir sicher, dass unsere Buildziele auf Windows Store festgelegt werden.

### <a name="unity-performance-and-quality-settings"></a>Einstellungen für die Leistung und Qualität von Unity

**Unity-Quality-Einstellungen für HoloLens**

![Unity-Quality-Einstellungen für HoloLens](images/qualitysettings.png) 

Da hohe Framerate für HoloLens Verwaltung so wichtig ist, möchten wir die Qualität-Einstellungen für schnellste Leistung optimiert. Ausführlichere Informationen zu Leistungsaspekten [Empfehlungen zur Leistung für Unity](performance-recommendations-for-unity.md).
1. Wählen Sie **Bearbeiten > Projekteinstellungen > Qualität**
2. Wählen Sie die **Dropdownliste** unter der **Windows Store** Logo, und wählen **sehr niedrig**. Wissen Sie, dass die Einstellung ist ordnungsgemäß angewendet, wenn das Feld in der Windows Store-Spalte und **sehr niedrig** Zeile wird grün angezeigt.

**Für mixed Reality-Anwendungen, die speziell für Programmentwickler konzipiert okkludierte zeigt**, lassen Sie die Einstellungen für die Qualität auf seine Standardwerte.

### <a name="target-windows-10-sdk"></a>Entwickeln für Windows 10 SDK

**SDK-Zielversion Windows Holographic**

![SDK-Zielversion Windows Holographic](images/xrsettings.png) 

Wir müssen wissen, dass die app aus, es versucht wird, exportieren, zu erstellen, sollten Unity eine [immersive Ansicht](app-views.md) anstelle einer 2D-Ansicht. Wir dazu Aktivieren der Unterstützung für virtuelle Realität in Unity für Windows 10-SDKS.
1. Wechseln Sie zu **Bearbeiten > Projekteinstellungen > Player**.
2. In der **Inspektor Bereich** Playereinstellungen, wählen Sie die **Windows Store** Symbol.
3. Erweitern Sie die **XR-Einstellungen** Gruppe.
4. In der **Rendern** aktivieren Sie im Abschnitt der **virtuelle Realität unterstützt** Kontrollkästchen zum Hinzufügen einer neuen **virtuelle Realität SDKs** Liste.
5. Überprüfen Sie, ob **Windows Mixed Reality** in der Liste angezeigt. Wenn nicht der Fall, wählen Sie die **+** Schaltfläche am unteren Rand der Liste aus, und wählen Sie **Windows Mixed Reality**.

>[!NOTE]
>Wenn Sie nicht sehen die **Windows Store** Symbol, überprüfen, um sicherzustellen, dass Sie das Windows Store .NET Scripting Back-End vor der Installation ausgewählt. Wenn dies nicht der Fall ist, müssen Sie möglicherweise Unity mit der richtigen Windows-Installation neu zu installieren.

**Überprüfen der Konfiguration für .NET**

![Überprüfen der Konfiguration für .NET](images/configoptions-375px.png)

1. Wechseln Sie zu **Bearbeiten > Projekteinstellungen > Player** (Sie können weiterhin haben dies aus dem vorherigen Schritt).
2. In der **Inspektor Bereich** Playereinstellungen, wählen Sie die **Windows Store** Symbol.
3. In der **Weitere Einstellungen** Konfiguration im Abschnitt, stellen Sie sicher, dass **Scripting Back-End-** nastaven NA hodnotu **.NET**

Fantastisch zum Abrufen aller projekteinstellungen übernommen. Als Nächstes fügen Sie ggf. ein Hologramm lassen Sie uns!

## <a name="chapter-4---create-a-cube"></a>Kapitel 4: Erstellen eines Cubes

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

Erstellen einen Cube in Ihrem Unity-Projekt ist, wie erstellen ein anderes Objekt in Unity. Platzieren einen Cube vor dem Benutzer ist einfach, da der realen Welt – von Unity-Koordinatensystem zugeordnet ist, in denen ein Messgerät in Unity ungefähr ein Messgerät in der Praxis ist.
1. In der oberen linken Ecke des der **Hierarchie** wählen die **erstellen** Dropdownliste, und wählen Sie **3D Object > Cube**.
2. Wählen Sie den neu erstellten **Cube** in die **Hierarchie** Bereich
3. In der **Inspektor** finden Sie die **transformieren** -Komponente, und ändern Sie **Position** auf (**X**: 0, **Y**: 0, **Z**: 2). *Dies positioniert den Cube 2 Zähler vor Anfangsposition des Benutzers.*
4. In der **transformieren** Komponente Änderung **Drehung** auf (**X**: 45, **Y**: 45, **Z**: 45), und ändern Sie **Skalierung** auf (**X**: 0.25, **Y**: 0.25, **Z**: 0.25). *Hiermit skalieren Sie den Cube zu 0,25 m.*
5. Wählen Sie zum Speichern der Änderungen für die Szene **Datei > Szene speichern**.

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>Kapitel 5 – überprüfen Sie, ob auf dem Gerät von Unity-editor

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

Nachdem wir den Cube erstellt haben, ist es Zeit für eine schnelle Überprüfung auf Gerät. Sie können direkt aus in der Unity-Editor dazu.

### <a name="initial-setup"></a>Anfangssetup
1. Öffnen Sie auf Ihrem Entwicklungs-PC, in Unity **Datei > Buildeinstellungen** Fenster.
2. Änderung **Plattform** zu **universelle Windows-Plattform** , und klicken Sie auf **Switch-Plattform**

### <a name="for-hololens-use-unity-remoting"></a>Für HoloLens Unity-Remoting verwenden.
1. Klicken Sie auf Ihre HoloLens, installieren, und führen Sie die [Holographic Remoting-Player](holographic-remoting-player.md), verfügbar über den Windows Store. Starten Sie die Anwendung auf dem Gerät, und geben Sie einen Wartestatus wird und die IP-Adresse des Geräts angezeigt. Notieren Sie sich die IP-Adresse.
2. Open **Fenster > XR > Holographic Emulation**.
3. Änderung **Emulationsmodus** aus **keine** zu **Gerät Remote**.
4. In **Remotecomputer**, geben Sie die IP-Adresse Ihre zuvor notierten HoloLens.
5. Klicken Sie auf **Verbinden**.
6. Stellen Sie sicher die **Verbindungsstatus** ändert sich in Grün **verbunden**.
7. Jetzt können Sie jetzt auf **spielen** im Unity-Editor.

Sie nun werden den Cube, in dem Gerät und im Editor angezeigt. Sie können anhalten, Objekte zu überprüfen und Debuggen, wie Sie eine app im Editor ausgeführt werden, da dies im Wesentlichen ist, was passiert, jedoch mit Video, Audio und Geräteeingabe hin und her übertragen, über das Netzwerk zwischen dem Host-Computer und dem Gerät.

### <a name="for-other-mixed-reality-supported-headsets"></a>Für andere mixed Reality unterstützt headsets

1. Herstellen einer Verbindung den Entwicklungs-PC das USB-Kabel mit der HDMI-mit den Kopfhörer oder für Port Kabel angezeigt.
2. Starten Sie den **Mixed Reality-Portal** und stellen Sie sicher, Sie haben die Willkommensseite.
3. In Unity können Sie jetzt die Schaltfläche "Wiedergabe" drücken.

Sie jetzt werden das Cube-Rendering in Ihrer mixed Reality-Kopfhörer und im Editor angezeigt.

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>Kapitel 6: Erstellen und bereitstellen, die auf Gerät aus Visual Studio

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

Wir können nun unser Projekt in Visual Studio zu kompilieren und auf unserer Zielgerät bereitstellen.

### <a name="export-to-the-visual-studio-solution"></a>Exportieren Sie in Visual Studio-Projektmappe
1.  Open **Datei > Buildeinstellungen** Fenster.
2.  Klicken Sie auf **öffnen Szenen hinzufügen** die Szene hinzufügen.
3.  Änderung **Plattform** zu **universelle Windows-Plattform** , und klicken Sie auf **Plattform wechseln**.
4.  In **Windows Store** Einstellungen stellen Sie sicher, **SDK** ist **universelle 10**.
5.  Für das Zielgerät, überlassen Sie **einem beliebigen Gerät** für okkludierte zeigt oder wechseln Sie zu **HoloLens**.
6.  **UWP-Buildtyp** muss **D3D**.
7.  **UWP SDK** beibehalten werden kann. bei **zuletzt installierte**.
8.  Überprüfen Sie **Unity C# Projekte** beim Debuggen.
9.  Klicken Sie auf **Erstellen**.
10. Klicken Sie im Datei-Explorer auf **neuer Ordner** und nennen Sie den Ordner **"App"**.
11. Mit der **App** Ordner ausgewählt haben, klicken Sie auf die **Ordner auswählen** Schaltfläche.
12. Unity wird nach Abschluss erstellen, ein Windows-Datei-Explorer-Fenster wird angezeigt.
13. Öffnen der **App** Ordner im Datei-Explorer.
14. Öffnen Sie die generierte Visual Studio-Projektmappe (MixedRealityIntroduction.sln in diesem Beispiel)

### <a name="compile-the-visual-studio-solution"></a>Kompilieren Sie die Visual Studio-Projektmappe

Abschließend werden wir exportierte Visual Studio-Projektmappe zu kompilieren, bereitstellen und probieren Sie es auf dem Gerät.
1. Verwenden obere auf der Symbolleiste in Visual Studio, ändern Sie das Ziel in **Debuggen** zu **Version** und **ARM** zu **X86**.

Die Anweisungen unterscheiden sich für die Bereitstellung auf einem Gerät im Vergleich zu den Emulator. Führen Sie die Anweisungen, die Ihre Einrichtung zu entsprechen.

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>Bereitstellen Sie für mixed Reality-Gerät über WLAN
1. Klicken Sie auf den Pfeil neben der **lokalen Computer** Schaltfläche, und ändern Sie das Bereitstellungsziel um **Remotecomputer**.
2. Geben Sie die IP-Adresse Ihres Geräts mixed Reality und ändern Sie **Authentifizierungsmodus** , universell (unverschlüsseltes Protokoll) für HoloLens und **Windows** für andere Geräte.
3. Klicken Sie auf **Debuggen > Starten ohne debugging**.

**Für HoloLens**, wenn das erste Mal auf Ihrem Gerät bereitstellen, müssen Sie Paar [mithilfe von Visual Studio](using-visual-studio.md).

### <a name="deploy-to-mixed-reality-device-over-usb"></a>Bereitstellen Sie für mixed Reality-Gerät über USB

Stellen Sie sicher, dass Ihr Gerät über das USB-Kabel angeschlossen ist.
1. **Für HoloLens**, klicken Sie auf den Pfeil neben der **lokalen Computer** Schaltfläche, und ändern Sie das Bereitstellungsziel um **Gerät**.
2. **Für die Ziel-okkludierte-Geräte, die auf Ihren PC verbunden**, halten Sie die Einstellung auf dem lokalen Computer. Stellen Sie sicher, Sie haben die **Mixed Reality-Portal** ausgeführt wird.
3. Klicken Sie auf **Debuggen > Starten ohne debugging**.

### <a name="deploy-to-emulator"></a>Emulator bereitstellen
1. Klicken Sie auf den Pfeil neben der **Gerät** Schaltfläche, und aus der Dropdownliste wählen **Emulator für HoloLens**.
2. Klicken Sie auf **Debuggen > Starten ohne debugging**.

### <a name="try-out-your-app"></a>Testen Sie Ihre app

Nun, dass Ihre app bereitgestellt wird, versuchen Sie für den Cube zu verschieben, und beachten Sie, dass es in der Welt vor Ihnen bleibt.

## <a name="see-also"></a>Siehe auch
* [Unity-Entwicklung – Übersicht](unity-development-overview.md)
* [Bewährte Methoden für das Arbeiten mit Unity und Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [MR Basics 101](holograms-101.md)
* [MR Basics 101E](holograms-101e.md)
