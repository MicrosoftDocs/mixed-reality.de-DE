---
title: 'Grundlagen 100: Einstieg in Unity'
description: Erfahren Sie, wie Sie Ihre erste einfache "Hello World"-Anwendung mit gemischter Realität erstellen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Gemischte Realität, Windows Mixed Reality, hololens, immersive, VR, Mr, Einstieg, Hologram, Academy, Tutorial
ms.openlocfilehash: 58a1785ef74872c633cf65d6a32e24d517367359
ms.sourcegitcommit: f523b74a549721b6bec69cb5d2eca5b7673a793c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85570306"
---
# <a name="mr-basics-100-getting-started-with-unity"></a>MR-Grundlagen 100: Erste Schritte mit Unity

>[!IMPORTANT]
>Die Tutorials der Mixed Reality Academy wurden im Hinblick auf HoloLens (1. Gen.) und immersive Mixed Reality-Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. [Es wurde eine neue Reihe von Tutorials](mrlearning-base.md) für HoloLens 2 veröffentlicht.

Dieses Tutorial führt Sie durch die Erstellung einer einfachen Mixed Reality-APP, die mit Unity erstellt wurde.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>MR-Grundlagen 100: Erste Schritte mit Unity</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md)konfiguriert ist.

## <a name="chapter-1---create-a-new-project"></a>Kapitel 1: Erstellen eines neuen Projekts

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

Zum Erstellen einer APP mit Unity müssen Sie zunächst ein Projekt erstellen. Dieses Projekt ist in einigen Ordnern organisiert, wobei es sich bei den wichtigsten Elementen um den Ordner "Assets" handelt. Dabei handelt es sich um den Ordner, der alle Ressourcen enthält, die Sie aus Tools für die Erstellung digitaler Inhalte importieren, wie z. b. Maya, max. Kino 4D oder Photoshop, sämtlichen Code, den Sie mit Visual Studio oder Ihrem bevorzugten Code-Editor erstellen, und beliebig viele Inhalts Dateien, die Unity erstellt, wenn Sie Szenen, Animationen und andere Unity-Ressourcentypen

Um UWP-apps zu erstellen und bereitzustellen, kann Unity das Projekt als Visual Studio-Projekt Mappe exportieren, die alle erforderlichen Medienobjekt-und Code Dateien enthält.

1. Unity starten
2. **Neu** auswählen
3. Geben Sie einen Projektnamen ein (z. b. "mixedrealityintroduction").
4. Geben Sie einen Speicherort zum Speichern Ihres Projekts ein.
5. Stellen Sie sicher, dass der **3D-** Schalter ausgewählt ist
6. **Projekt erstellen** auswählen

Herzlichen Glückwunsch, Sie sind alle Setup für die ersten Schritte mit ihren Mixed Reality-Anpassungen.

## <a name="chapter-2---setup-the-camera"></a>Kapitel 2: Einrichten der Kamera

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

Die Unity-Hauptkamera behandelt die Kopf-und stereorenderingvorgänge. An der Hauptkamera müssen einige Änderungen vorgenommen werden, damit Sie mit gemischter Realität verwendet werden kann.

1. Datei > neuen Szene auswählen

Erstens ist es einfacher, Ihre APP zu entwerfen, wenn Sie sich die Anfangsposition des Benutzers als (**X**: 0, **Y**: 0, **Z**: 0) vorstellen. Da die Hauptkamera die Bewegung des Benutzers nachverfolgt, kann die Startposition des Benutzers festgelegt werden, indem die Startposition der Hauptkamera festgelegt wird.

1. Auswählen der **Hauptkamera** im **Hierarchie** Panel
2. Suchen Sie im **Inspektor** -Panel die **Transformations** Komponente, und ändern Sie die **Position** von (**x**: 0, **y**: 1, **z**:-10) in (**x**: 0, **y**: 0, **z**: 0).

Zweitens benötigt der Standard Hintergrund der Kamera einige Gedanken.

**Bei hololens-Anwendungen**sollte die reale Welt hinter alles stehen, was von der Kamera gerendert wird, und keine Skybox-Textur.

1. Wenn im Bereich **Hierarchie** weiterhin die **Hauptkamera** ausgewählt ist, suchen Sie im **Inspektor** -Panel nach der **Kamera** Komponente, und ändern Sie die Dropdown Liste **Flag löschen** von **Skybox** in voll **Tonfarbe**.
2. Wählen Sie die **Hintergrund** Farbauswahl aus, und ändern Sie die **RGBA** -Werte in (0,0).

**Für gemischte Reality-Anwendungen, die auf immersive Headsets ausgerichtet**sind, können wir die von Unity bereitgestellte Standard Textur von Skybox verwenden.

1. Wenn im **Hierarchie** Panel noch die **Hauptkamera** ausgewählt ist, suchen Sie im **Inspektor** -Panel nach der **Kamera** Komponente, und lassen Sie die Dropdown Liste **Flag löschen** auf **Skybox**.

Als drittes betrachten wir die Near-Clip-Ebene in Unity und verhindern, dass Objekte zu nah an den Benutzern gerendert werden, wenn ein Benutzer ein Objekt nähert oder ein Objekt einen Benutzer nähert.

**Bei hololens-Anwendungen**kann die Near-Clip-Ebene auf die [hololens-empfohlenen](camera-in-unity.md#clip-planes) 0,85 Meter festgelegt werden.

1. Wenn im **Hierarchie** Panel noch die **Hauptkamera** ausgewählt ist, suchen Sie im **Inspektor** -Panel nach der **Kamera** Komponente, und ändern Sie das Feld **near-Clip Plane** von der Standardeinstellung **0,3** in das Feld hololens Recommended **0,85**.

**Für gemischte Reality-Anwendungen, die auf immersive Headsets ausgerichtet**sind, können wir die von Unity bereitgestellte Standardeinstellung verwenden.

1. Wenn im Bereich **Hierarchie** weiterhin die **Hauptkamera** ausgewählt ist, suchen Sie im **Inspektor** -Panel nach der **Kamera** Komponente, und lassen Sie das Feld **near Clip Plane** auf den Standardwert **0,3**.

Abschließend können wir unseren Fortschritt speichern. Um die Szenen Änderungen zu speichern, klicken Sie auf **Datei > Szene speichern**unter, benennen Sie **die Szene,** und wählen Sie **Speichern**aus.

## <a name="chapter-3---setup-the-project-settings"></a>Kapitel 3: Einrichten der Projekteinstellungen

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

In diesem Kapitel werden einige Unity-Projekteinstellungen festgelegt, die uns dabei helfen, das Windows Holographic SDK für die Entwicklung zu entwickeln. Wir legen auch einige Qualitätseinstellungen für die Anwendung fest. Abschließend wird sichergestellt, dass unsere Buildziele auf universelle Windows-Plattform festgelegt sind.

### <a name="unity-performance-and-quality-settings"></a>Unity-Leistungs-und Qualitätseinstellungen

**Unity-Qualitätseinstellungen für hololens**

![Unity-Qualitätseinstellungen für hololens](images/qualitysettings.png)

Da das Verwalten von hoher Framerate in hololens so wichtig ist, möchten wir, dass die Qualitätseinstellungen für die schnellste Leistung optimiert werden. Ausführlichere Informationen zur Leistung finden Sie unter [Empfehlungen zur Leistung für Unity](performance-recommendations-for-unity.md).

1. Wählen Sie **> Projekteinstellungen bearbeiten > Qualität** aus.
2. Wählen Sie im **universelle Windows-Plattform** Logo die **Dropdown** Liste aus, und wählen Sie **sehr niedrig**aus. Sie werden feststellen, dass die Einstellung ordnungsgemäß angewendet wird, wenn das Feld in der universelle Windows-Plattform-Spalte und die **sehr niedrige** Zeile grün ist.

**Für gemischte Reality-Anwendungen, die für die Anzeige von Anzeigen vorgesehen**sind, können Sie die Qualitätseinstellungen auf die Standardwerte überlassen.

### <a name="target-windows-10-sdk"></a>Windows 10-Ziel-SDK

**Windows Holographic-Ziel SDK**

![Windows Holographic-Ziel SDK](images/xrsettings.png)

Wir müssen Unity mitteilen, dass die zu exportierende App eine [immersive Ansicht](app-views.md) anstelle einer 2D-Ansicht erstellen sollte. Dies geschieht durch Aktivieren der Virtual Reality-Unterstützung für Unity, die auf das Windows 10 SDK abzielen.

1. Wechseln Sie zu **Edit > Project Settings > Player**.
2. Wählen Sie im **Inspektor-Panel** für die Player-Einstellungen das **universelle Windows-Plattform** Symbol aus.
3. Erweitern Sie die Gruppe **XR-Einstellungen**.
4. Aktivieren Sie im Abschnitt " **Rendering** " das Kontrollkästchen " **Virtual Reality supported** ", um eine neue **Virtual Reality-sdsliste** hinzuzufügen.
5. Überprüfen Sie, ob in der Liste **Windows Mixed Reality** angezeigt wird. Wenn nicht, wählen Sie die Schaltfläche **+** am Ende der Liste aus, und wählen Sie **Windows Mixed Reality** aus.

>[!NOTE]
>Wenn das **universelle Windows-Plattform** -Symbol nicht angezeigt wird, vergewissern Sie sich, dass Sie während der Installation universelle Windows-Plattform Buildunterstützung ausgewählt haben. Wenn nicht, müssen Sie Unity eventuell mit der richtigen Windows-Installation neu installieren.

Tolle Aufgabe zum Anwenden aller Projekteinstellungen. Als Nächstes fügen wir ein Hologram hinzu.

## <a name="chapter-4---create-a-cube"></a>Kapitel 4: Erstellen eines Cubes

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

Das Erstellen eines Cubes in Ihrem Unity-Projekt erfolgt genauso wie das Erstellen eines beliebigen anderen Objekts in Unity. Das Platzieren eines Cubes vor dem Benutzer ist einfach, da das Koordinatensystem von Unity der realen Welt zugeordnet ist, wobei eine Einheit in Unity ungefähr eine Meter in der realen Welt ist.

1. Wählen Sie in der oberen linken Ecke des Bereichs **Hierarchie** die Dropdown Liste **Erstellen** aus, und wählen Sie **3D-Objekt > Cube**aus.
2. Wählen Sie im **Hierarchie** Panel den neu erstellten **Cube** aus.
3. Suchen Sie im **Inspektor** die **Transformations** Komponente, und ändern Sie die **Position** in (**X**: 0, **Y**: 0, **Z**: 2). *Dadurch wird der Cube 2 Meter vor der Anfangsposition des Benutzers positioniert.*
4. Ändern Sie in der **Transformations** Komponente **die Drehung** in (**x**: 45, **y**: 45, **z**: 45), und ändern Sie die **Skalierung** in (**x**: 0,25, **y**: 0,25, **z**: 0,25). *Dadurch wird der Cube auf 0,25 Meter skaliert.*
5. Um die Szenen Änderungen zu speichern, wählen Sie **Datei > Szene speichern**aus.

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>Kapitel 5: Überprüfen des Geräts über den Unity-Editor

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

Nachdem wir nun den Cube erstellt haben, ist es an der Zeit, eine schnell Überprüfung im Gerät durchzuführen. Sie können dies direkt im Unity-Editor tun.

### <a name="initial-setup"></a>Erste Einrichtung

1. Öffnen Sie auf dem Entwicklungs-PC in Unity das Fenster **Datei > Fenster Build-Einstellungen** .
2. Ändern Sie **Platform** in **universelle Windows-Plattform** und klicken Sie auf **Plattform wechseln** .

### <a name="for-hololens-use-unity-remoting"></a>Verwenden Sie für hololens Unity-Remoting

1. Installieren und führen Sie auf Ihren hololens den [Holographic Remoting Player](holographic-remoting-player.md)aus, der im Windows Store verfügbar ist. Starten Sie die Anwendung auf dem Gerät, und Sie wechselt in den Wartezustand und zeigt die IP-Adresse des Geräts an. Notieren Sie sich die IP-Adresse.
2. Öffnen Sie **Fenster > XR > Holographic Emulation**.
3. Ändern Sie den **Emulations Modus** von **None** in **Remote zu Gerät**.
4. Geben Sie auf dem **Remote Computer**die IP-Adresse der zuvor notierten hololens ein.
5. Klicken Sie auf **Verbinden**.
6. Stellen Sie sicher, dass der **Verbindungs Status** in grünes **verbunden**wechselt.
7. Jetzt können **Sie im Unity-Editor auf "** wiedergeben" klicken.

Nun können Sie den Cube im Gerät und im Editor sehen. Sie können Objekte anhalten, überprüfen und Debuggen, wie Sie eine APP im Editor ausführen, da dies im Wesentlichen geschieht, aber mit Video-, Audio-und Geräte Eingaben, die zwischen dem Host Computer und dem Gerät über das Netzwerk übertragen werden.

### <a name="for-other-mixed-reality-supported-headsets"></a>Für andere von Mixed Reality unterstützte Headsets

1. Verbinden Sie das Headset mit dem Entwicklungs-PC, indem Sie das USB-Kabel und das HDMI-oder Anzeige Anschlusskabel verwenden.
2. Starten Sie das **Mixed Reality-Portal** , und stellen Sie sicher, dass Sie die erste Ausführung abgeschlossen haben.
3. Aus Unity können Sie nun auf die Wiedergabe Schaltfläche klicken.

Nun können Sie das Cube-Rendering in Ihrem Mixed Reality-Headset und im Editor sehen.

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>Kapitel 6: Erstellen und Bereitstellen für ein Gerät aus Visual Studio

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

Nun können wir das Projekt in Visual Studio kompilieren und auf dem Zielgerät bereitstellen.

### <a name="export-to-the-visual-studio-solution"></a>Exportieren in die Visual Studio-Projekt Mappe

1. Öffnen Sie die **Datei >** Fenster mit den Buildeinstellungen.
1. Klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.
1. Wechseln Sie zu **universelle Windows-Plattform** **Plattform** , und klicken Sie auf **Plattform wechseln**.
1. Stellen Sie sicher, dass in **universelle Windows-Plattform** Einstellungen das **SDK** **Universal 10**ist.
1. Überlassen Sie für Zielgerät **ein beliebiges Gerät für okkludierte** anzeigen, oder wechseln Sie zu **hololens**.
1. Der **UWP-Buildtyp** muss **D3D**lauten.
1. Das **UWP SDK** ist möglicherweise auf dem **neuesten installiert**.
1. Klicken Sie auf **Erstellen**.
1. Klicken Sie im Datei-Explorer auf **neuer Ordner** , und benennen Sie den Ordner **"App"**.
1. Wenn der **App** -Ordner ausgewählt ist, klicken Sie auf die Schaltfläche **Ordner auswählen** .
1. Wenn Unity erstellt wurde, wird ein Fenster des Windows-Datei-Explorers angezeigt.
1. Öffnen Sie den **App** -Ordner im Datei-Explorer.
1. Öffnen Sie die generierte Visual Studio-Projekt Mappe (in diesem Beispiel mixedrealityintroduction. sln).

### <a name="compile-the-visual-studio-solution"></a>Kompilieren der Visual Studio-Projekt Mappe

Schließlich kompilieren wir die exportierte Visual Studio-Projekt Mappe, stellen Sie bereit und testen Sie auf dem Gerät.

1. Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von **Debug** in **Release** und von **Arm** in **x86**.

Die Anweisungen unterscheiden sich für die Bereitstellung auf einem Gerät im Vergleich zum Emulator. Befolgen Sie die Anweisungen, die dem Setup entsprechen.

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>Bereitstellen für ein gemischtes Reality-Gerät über Wi-Fi

1. Klicken Sie auf den Pfeil neben der Schaltfläche **lokaler Computer** , und ändern Sie das Bereitstellungs Ziel in **Remote Computer**.
2. Geben Sie die IP-Adresse Ihres gemischten Reality-Geräts ein, und ändern Sie den **Authentifizierungsmodus** für hololens und **Windows** für andere Geräte in Universal (unverschlüsseltes Protokoll).
3. Klicken Sie auf **Debuggen > ohne Debugging starten**.

Bei **hololens**müssen Sie, wenn dies die erste Bereitstellung auf Ihrem Gerät ist, [mit Visual Studio](using-visual-studio.md)koppeln.

### <a name="deploy-to-mixed-reality-device-over-usb"></a>Auf gemischtes Reality-Gerät über USB bereitstellen

Stellen Sie sicher, dass das Gerät über das USB-Kabel angeschlossen ist.

1. Klicken Sie **für hololens**auf den Pfeil neben der Schaltfläche **lokaler Computer** , und ändern Sie das Bereitstellungs Ziel auf **Gerät**.
2. Behalten Sie **für die Zielgeräte, die an Ihren PC angeschlossen**sind, die Einstellung lokaler Computer bei. Stellen Sie sicher, dass das **gemischte Reality-Portal** ausgeführt wird.
3. Klicken Sie auf **Debuggen > ohne Debugging starten**.

### <a name="deploy-to-emulator"></a>In Emulator bereitstellen

1. Klicken Sie auf den Pfeil neben der Schaltfläche **Gerät** , und wählen Sie in der Dropdown-Taste **hololens Emulator**aus.
2. Klicken Sie auf **Debuggen > ohne Debugging starten**.

### <a name="try-out-your-app"></a>Testen Sie Ihre APP

Nachdem Sie Ihre APP bereitgestellt haben, versuchen Sie, alle den Cube zu verschieben, und beobachten Sie, dass Sie in der Welt vor Ihnen bleibt.

## <a name="see-also"></a>Weitere Informationen

* [Unity-Entwicklung – Übersicht](unity-development-overview.md)
* [Bewährte Methoden für das Arbeiten mit Unity und Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [MR-Grundlagen 101](holograms-101.md)
* [MR-Grundlagen 101E](holograms-101e.md)
