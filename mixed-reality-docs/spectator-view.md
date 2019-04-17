---
title: Spectator anzeigen
description: Visualisieren Sie Hologramme von einem externen Gerät als Mittel zum veranschaulichen einer mixed Reality-Erfahrung unter einen externen Monitor oder die Aufzeichnung des Videos mit einer mixed Reality-Erfahrung.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Spectator anzeigen, iPhone, iOS, iPad, OpenCV, Kamera, ARKit, HoloLens, Mixed Reality, MixedRealityToolkit, Demo aufzeichnen
ms.openlocfilehash: 77102cf5fb1c23f27f7f2d651c6ca1ae9df5a1d1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595415"
---
# <a name="spectator-view-for-hololens"></a>Spectator-Ansicht für HoloLens

![Marker](images/SpecViewPhoneHero.jpg)


## <a name="current-refactor"></a>Aktuelle Refactor!

> [!NOTE]
>Spectator-Ansicht für HoloLens ist aktiv umgestaltet werden. Dazu richtet sich an, die Vorschau zu konsolidieren und Pro Codebasen und erweitern die Unterstützung auf HoloLens 2. 

Zum Anzeigen des aktuellen Status der Umgestaltung Spectator-Ansicht finden Sie unter "Features/SpectatorView" Branches in MixedRealityToolkit sowohl MixedRealityToolkit Unity Repositorys:

https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/feature/spectatorView/Assets/MixedRealityToolkit.Extensions/SpectatorView

und

https://github.com/Microsoft/MixedRealityToolkit/tree/feature/spectatorView/SpectatorViewPlugin

## <a name="overview"></a>Übersicht

Wenn eine HoloLens steht, geteert, wir häufig vergessen, dass eine Person, die es keinen auf können nicht die Wunder der derzeitigen auftreten, die wir können. In der Ansicht Spectator können andere Benutzer auf einem 2D-Bildschirm sehen, was ein HoloLens-Benutzer in ihrer Umgebung angezeigt wird.
Spectator anzeigen (Vorschau) ist die schnelle und kostengünstige Ansatz für die Aufzeichnung von Hologramme in HD ', während für die professionelle und hochwertige Aufzeichnung Hologramme Spectator Ansicht Pro vorgesehen ist.

Die folgende Tabelle zeigt sowohl Optionen und ihre Funktionen. Wählen Sie die Option, die am besten Ihren Anforderungen für die Videoaufnahme:

|                                      | Spectator anzeigen (Vorschau) |              Spectator anzeigen Pro              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| HD-Qualität                         |         Full HD         |        Professionelle und hochwertige Filmen (laut DSLR)      |
| Einfache Kamera-Bewegung                      |            ✔            |                                             |
| Dritte Person Ansicht                    |            ✔            |                      ✔                      |
| Können zu Bildschirmen gestreamt werden           |            ✔            |                      ✔                      |
| Tragbar                             |            ✔            |                                             |
| Drahtlos                             |            ✔            |                                             |
| Zusätzliche erforderliche hardware         |     iPhone (oder iPad)    | HoloLens + Rig + Tripod + DSLR + PC + Unity |
| Hardware-Investitionen                  |           Niedrig           |                     Hoch                    |
| Plattformübergreifend                       |           iOS           |                                             |
| Viewer interagieren können                  |            ✔            |                                             |
| Netzwerkeinrichtung (UNET scripting) |            ✔            |                      ✔                      |
| Dauer der Common Language Runtime-setup               |         Zeitpunkt         |                     Verzögerte Anzeige                    |

## <a name="spectator-view-preview"></a>Spectator anzeigen (Vorschau)

![Marker](images/SpecViewPhoneDemo.jpg)

### <a name="use-cases"></a>Anwendungsfälle

- Filmen Hologramme in HD: Spectator Ansicht (Vorschau) können Sie eine mixed Reality-Erfahrung, die mit einem iPhone aufzeichnen. Zeichnen in full HD und Anti-Aliasing für Hologramme und sogar Schatten. Es ist eine kostengünstige und schnelle Möglichkeit zum Erfassen von Videos mit Hologramme.
- Livedemos: Stream live mixed Reality verbessern, Apple TV direkt über Ihr iPhone oder iPad Spielerlebnis ohne Verzögerungen.
- Freigeben Sie die Erfahrung für Gäste: Lassen Sie nicht HoloLens Benutzer Hologramme direkt von ihren Telefonen oder Tablets.

### <a name="current-features"></a>Aktuelle features

- Netzwerk-AutoErmittlung für Smartphones zur Sitzung hinzufügen.
- Automatische sitzungsverarbeitung, damit Benutzer die richtigen Sitzung hinzugefügt werden.
- Räumliche Synchronisierung von Hologramme, damit jeder Hologramme genau dieselbe Stelle ein sieht.
- iOS-Unterstützung (ARKit-fähige Geräte).
- Mehrere Gäste für iOS.
- Aufzeichnen von Videos + Hologramme + Umgebungsgeräuschen + – Hologramm Sound.
- Geben Sie Blatt aus, damit Sie Video speichern, e-Mail oder andere unterstützende apps freigeben können.


>[!NOTE] 
>Der Code Spectator anzeigen (Vorschau) kann nicht mit den Spectator Ansicht Pro Versionscode verwendet werden. Es wird empfohlen, um es in neuen Projekten zu implementieren, wenn eine videoaufzeichnung der Hologramme erforderlich ist.

<br>

>[!VIDEO https://www.youtube.com/embed/3fXlPw_FGLg]


### <a name="licenses"></a>Lizenzen

- [OpenCV - (3-Klausel BSD-Lizenz)](https://opencv.org/license.html)
- [Unity ARKit - (MIT-Lizenz)](https://bitbucket.org/Unity-Technologies/unity-arkit-plugin/src/3691df77caca2095d632c5e72ff4ffa68ced111f/LICENSES/MIT_LICENSE?at=default&fileviewer=file-view-default)

## <a name="how-to-set-up-spectator-view-preview"></a>So richten Sie Spectator anzeigen (Vorschau)

### <a name="requirements"></a>Anforderungen

- [Spectator anzeigen-Plug-Ins und erforderlichen OpenCV-Binärdateien](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin) -Informationen zum Erstellen der Spectator View Native-Plug-Ins finden Sie unten. Von den generierten Binärdateien benötigen Sie Folgendes:

    - opencv_aruco343.dll
    - opencv_calib3d343.dll
    - opencv_core343.dll
    - opencv_features2d343.dll
    - opencv_flann343.dll
    - opencv_imgproc343.dll

    - zlib1.dll
    - SpectatorViewPlugin.dll
- Spectator-Ansicht verwendet Unity Networking (UNET) für die Netzwerkermittlung und räumliche synchronisiert. Dies bedeutet, dass alle Interaktivität während der Anwendung zwischen den Geräten synchronisiert werden muss.
- Unity 2017.2.1p2 oder höher
- Hardware
    - A HoloLens
    - Windows-PC mit Windows 10
    - ARKit kompatibles Gerät (iPhone 6 s oder höher / iPad Pro 2016 oder höher / iPad 2017 oder höher) – unter iOS 11 oder höher
    - Mac mit Xcode 9.2 oder höher
- Apple-Entwicklerkonto, kostenlose oder [bezahlt](https://developer.apple.com/)
- Microsoft Visual Studio 2017

### <a name="building-the-spectator-view-native-plugin"></a>Erstellen die Ansicht der Spectator native-Plug-in

Gehen Sie folgendermaßen vor, um die erforderlichen Dateien zu generieren: https://github.com/Microsoft/MixedRealityToolkit/blob/master/SpectatorViewPlugin/README.md

### <a name="project-setup"></a>Einrichtung des Projekts

1. Bereiten Sie vor der Szene, um sicherzustellen, dass alle sichtbar "gameobjects" innerhalb der Szene unter einem www-Stammverzeichnis "gameobject" enthalten sind.

    ![Www-Stammverzeichnis](images/SpecViewPhoneWorldRoot2.PNG)

2. Fügen Sie das Prefab SpectatorView ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab)) in die Szene.
3. Fügen Sie das Prefab SpectatorViewNetworking ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab)) in die Szene.
4. Wählen Sie das SpectatorViewNetworking "gameobject", und auf die Komponente SpectatorViewNetworkingManager befindet sich ein paar Dinge, die Sie verknüpfen können. Wenn Countdownzeitgebers wird diese Komponente erforderlichen Skripts zur Laufzeit suchen.
    - Marker Erkennung HoloLens-SpectatorView/Hololens/MarkerDetection >.
    - Marker-Generation-3D-SpectatorView/IPhone/SyncMarker/3DMarker >.

    ![SpectatorView-Netzwerkermittlung](images/SpecViewPhoneNetworkDiscovery.PNG)

### <a name="networking-your-app"></a>Netzwerk-Ihrer-app

- Spectator Ansicht UNET für die Netzwerke verwendet und verwaltet alle Host-Client-Verbindungen für Sie.
- Jeder spezifischen app-Daten synchronisiert und von Ihnen stammt, verwenden z. B. SyncVars, NetworkTransform, NetworkBehavior implementiert werden müssen.
- Weitere Informationen zum Netzwerkbetrieb Unity finden Sie auf [Multiplayer-Spiele und Netzwerkressourcen](https://docs.unity3d.com/Manual/UNet.html). (Anmerkung: UNet wurde als veraltet markiert; die aktuelle Refactoring der Codebasis Spectator Ansicht wird dieses Problem zu beheben)

### <a name="building-for-each-platform-hololens-or-ios"></a>Erstellen für jede Plattform (HoloLens oder iOS)

- Wenn Sie für iOS zu erstellen, stellen Sie sicher, dass Sie die Komponente GLTF MRTK entfernen, da dies noch nicht mit dieser Plattform kompatibel ist.
- Auf der obersten Ebene der SpectatorView prefabs ist eine Komponente namens "Plattform Switcher" vorhanden. Wählen Sie die Plattform, die, der Sie für erstellen möchten.
    - Wenn Sie 'Hololens' auswählen sollte alle "gameobjects" unter dem iPhone "gameobject" in der SpectatorView Prefab inaktiv "und" alle "gameobjects" unter "Hololens' aktiv angezeigt werden.
    - Dies kann eine Weile dauern, wie abhängig von der Plattform Sie wählen die HoloToolkit wird hinzugefügt oder aus dem Projekt entfernt.

    ![Plattform-Switcher](images/SpecViewPhoneSwitcher.PNG)

- Stellen Sie sicher, dass Sie alle Versionen der Anwendung mit der gleichen Unity-Editor-Instanz (Do nicht schließen Unity zwischen builds) aufgrund eines nicht aufgelösten mit Unity erstellen.

### <a name="running-your-app"></a>Die app ausgeführt wird

Sobald Sie erstellt und eine Version der Anwendung auf einem iPhone und HoloLens bereitgestellt haben, sollten Sie diese verbinden können.

1. Stellen Sie sicher, dass sowohl für Geräte im gleichen WLAN-Netzwerk sind.
2. Starten der Anwendung auf die sowohl für Geräte, ohne bestimmte Reihenfolge. Die beim Starten der Anwendungs auf dem iPhone löst die HoloLens-Kamera zum Aktivieren und starten die Aufnahme von Fotos.
3. Sobald die iPhone-app gestartet wird, sucht es nach Oberflächen wie Stockwerken oder Tabellen. Wenn Flächen gefunden werden, sollte einen Marker, die etwa wie folgt angezeigt werden. Diese Markierung, die HoloLens anzeigen.

    ![Marker](images/SpecViewPhoneMarker.PNG)

4. Sobald die Markierung durch die HoloLens erkannt wird es nicht mehr angezeigt, und beide Geräte verbunden und räumlich synchronisiert werden soll.

### <a name="recording-video"></a>Aufnahme von Videos

1. Klicken Sie zum Erfassen und speichern ein Video aus dem iPhone, tippen Sie und halten Sie den Bildschirm, 1 Sekunde. Klicken Sie im Menü für die Aufzeichnung wird geöffnet.
2. Tippen Sie auf die Schaltfläche zum Aufzeichnen von Rot, einen Countdown, bevor Sie beginnen, auf den Bildschirm zeichnen wird gestartet.
3. Aufzeichnung tippen und halten den Bildschirm für eine andere 1 Sekunde, tippen Sie dann auf die Schaltfläche "Beenden".
4. Nachdem eine Schaltfläche "Vorschau" (blaue Schaltfläche) wird angezeigt, das aufgezeichnete Video geladen wurde, tippen Sie, um die aufgezeichneten Videos ansehen.
5. Öffnen Sie die Freigabe aus, und wählen Sie speichern, um eigene Aufnahmen.

### <a name="example-scene"></a>Beispiel-Szene

Die Szene ein Beispiel finden Sie im [HoloToolkit-Examples\SpectatorView\Scenes\SpectatorViewExample.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpectatorView/Scenes/SpectatorViewExample.unity)

### <a name="troubleshooting"></a>Problembehandlung

**Im Unity-Editor stellt keine Verbindung zu einer Sitzung gehostet, die von einem HoloLens-Gerät her.**

- Dies ist möglicherweise die Windows-Firewall.
- Wechseln Sie zur Windows-Firewall-Optionen.
- Ermöglichen Sie eine app oder ein Feature durch die Windows-Firewall.
- Für alle Instanzen des Unity-Editor in die Liste Teilstriche, Domäne, privat und öffentlich.
- Klicken Sie dann zurück zur Windows-Firewall-Optionen.
- Klicken Sie auf Erweiterte Einstellungen.
- Klicken Sie auf eingehende Regeln.
- Alle Instanzen des Unity-Editors sollte ein grünes Häkchen verfügen.
- Für alle Instanzen des Unity-Editor, die ein grünes Häkchen verfügen:
    - Doppelklicken.
    - Wählen Sie im Dialogfeld "Aktion" Verbindung zulassen.
    - Klicken Sie auf „OK“.
    - Starten Sie Unity-Editor neu.

**Zur Laufzeit, sagt die iPhone-Bildschirm "Suchen von Floor..." aber keine AR-Markierung angezeigt wird.**

- Das iPhone ist auf der Suche für eine horizontale Fläche, so dass Sie möglicherweise die iPhone-Kamera für die Bodenfläche oder eine Tabelle verweist. Dadurch wird ARKit Flächen erforderlich, dass räumlich Synchronisierung mit HoloLens finden.

**HoloLens-Kamera schaltet sich nicht automatisch beim iPhone wird versucht, verbinden.**

- Stellen Sie sicher, dass sowohl HoloLens und iPhone im gleichen WLAN-Netzwerk ausgeführt werden.

**Beim Starten von einer Anwendung Spectator anzeigen auf einem mobilen Gerät, aktivieren andere Hololens unter anderen Spectator Anzeigen von apps auf ihre Kamera**

- "GoTo" die NewDeviceDiscovery-Komponente und ändern Sie den Port für die Broadcast-Schlüssel und die Übertragung auf zwei eindeutige Werte.
- Rufen Sie SpectatorViewDiscovery aus, und ändern Sie den Schlüssel übertragen und die Broadcast-Port in einen anderen Satz von eindeutigen Nummern.

**Die HoloLens wird nicht mit dem Mac Unity-Editor eine Verbindung herstellen.**

- Dies ist ein bekanntes Problem, die auf die Unity-Version verknüpft werden kann. Erstellen von auf dem iPhone sollten weiterhin funktionieren und verbinden Sie wie gewohnt.

**Die Kamera HoloLens aktiviert, aber es kann nicht auf den Marker zu überprüfen.**

- Stellen Sie sicher, dass Sie alle Versionen der Anwendung mithilfe der gleichen Unity-Editor-Instanz (Do nicht schließen Unity zwischen builds) erstellen. Dies ist aufgrund eines unbekannten Problems mit Unity.

## <a name="spectator-view-pro"></a>Spectator anzeigen Pro

![Einrichtung von Spectator anzeigen](images/spectatorview-300px.png)

Die Verwendung von Spectator Ansicht Pro umfasst diese vier Komponenten:
1. Eine app, die speziell entwickelt, um Spectator anzeigen, aktivieren Sie basierend auf [Erfahrungen in mixed Reality freigegeben](shared-experiences-in-mixed-reality.md).
2. Ein Benutzer steht, geteert HoloLens, die mithilfe der app.
3. Spectator Ansicht Kamera Rig ein Video für die dritte Person Perspektive bereitstellen.
4. Eine desktop-PC ausgeführt wird die freigegebene Benutzeroberfläche-app und die Zusammensetzung der Hologramme in einem Spectator Katalogansicht von Videos.

![Ansicht Pro Spectator-setup](images/hololensspectatorview-500px.jpg) 

### <a name="use-cases"></a>Anwendungsfälle

>[!VIDEO https://www.youtube.com/embed/DgIHjxoPy_c]


*Spectator Sicht kann für die gemeinsame Nutzung Ihrer Spiele holographic verwendet werden, unabhängig davon, ob sie ein Standbild, einen Videoclip oder eine live-Demonstration.*


Es gibt drei wichtige Szenarien, die mit dieser Technologie gut funktionieren:

**1. Fotoaufnahmen**<br>
Diese Technologie nutzen, können Sie hochauflösende Bilder von Ihrem Hologramme erfassen. Diese Images können verwendet werden, Inhalte auf die marketing-Ereignisse zu veranschaulichen, senden an sich potenzielle Clients oder die Anwendung für die Windows Store übermitteln. Sie erhalten, welche Kamera Foto entscheiden, Sie verwenden, um die Aufzeichnung dieser Abbilder möchten, daher möglicherweise eine Qualität DSLR Kamera bevorzugen.


![Spectator Ansicht Pro Foto-Capture-Beispiel](images/fall-350px.jpg)<br>
*Foto-Capture-Beispiel – machen es so aussieht, das die Bodenfläche Lava besteht.*


**2. Videoaufzeichnung**<br>
Sind die besten Story Mechanismus zur Freigabe von einer holographic app-Benutzeroberfläche mit vielen Benutzern mitgeteilt werden. Spectator anzeigen kann, wählen Sie die Kamera, Fokus und Framing, der Farben am besten, wie Sie Ihre app zu präsentieren möchten. Es versetzt Sie Kontrolle über die Videoqualität basierend auf der Grafikhardware Ihnen zur Verfügung stehen.

![Spectator Ansicht Pro video-Capture-Beispiel](images/spectatorviewvideo.gif)<br>
*Videoaufzeichnung-Beispiel: eine mixed Reality-Erfahrung Zusammenarbeit aufzeichnen.*


**3. Live-Demos**<br>
Spectator-Ansicht ist eine bevorzugte Methode für die live-Demos, wie die Kameraposition gleichmäßig oder kontrollierter bleibt. Da Sie eine Videokamera qualitativ hochwertige verwenden können, können Sie auch qualitativ hochwertigen Bildern vorgesehen, die für einen großen Bildschirm produzieren. Dies eignet sich auch für das Streamen von live-Demos auf einem Bildschirm, möglicherweise in den eager Teilnehmer in Zeile warten auf die Reihe.

### <a name="comparing-video-capture-techniques"></a>Vergleichen von video-Capture-Techniken

[Mixed Reality-Erfassung](mixed-reality-capture.md) (MRC) bietet eine video Kombination, was die HoloLens-Benutzers aus Ego-von-Sicht angezeigt wird. Spectator Ansicht erzeugt ein Video von einer dritten Person Perspektive können den video Beobachter für die Umgebung mit Hologramme und der Benutzer ein HoloLens-Gerät steht, geteert finden Sie unter. Da Sie die Wahl der Kamera haben, können höhere Auflösung sowie Bilder für eine bessere Qualität als die integrierte HoloLens-Kamera für MRC-Images verwendet außerdem Spectator Ansichten erstellen. Aus diesem Grund ist Spectator Ansicht für app-Bilder in der Windows Store, Videos, marketing oder projizieren eine Liveansicht für ein Publikum besser geeignet.

![Spectator Ansicht Pro professional-Kamera, die in Microsoft-Keynote-Präsentationen verwendet](images/spectator-view-professional-red-camera-300px.jpg)<br>
*Spectator Ansicht Pro professional-Kamera, die in Microsoft-Keynote-Präsentationen verwendet*


Spectator Ansicht wurde ein wesentlicher Bestandteil des wie Microsoft HoloLens dargestellt verfügt über Funktionen für ein Publikum seit Anfang, wenn das Produkt vom Januar 2015 angekündigt wurde. Die professional-Setup verwendet hatte, hohe Anforderungen an die und eine teure Preis-Tag, damit hinwollen. Beispielsweise verwendet die Kamera ein Signal Genlock genauen Zeitpunkt sichergestellt werden, die mit dem Überwachungssystem HoloLens koordiniert. In diesem Setup war Bewegen der Kamera des Spectator Ansicht möglich gleichzeitig Hologramme stabile entsprechend die Erfahrung einer Person, die die Benutzeroberfläche direkt in HoloLens angezeigt wird.

Die Open-Source-Version der Spectator Ansicht Einbußen im Hinblick auf die Möglichkeit, das Rig Kamera zu verschieben, um die Kosten für das gesamte Setup erheblich senken. Dieses Projekt verwendet eine externe Kamera auf einem HoloLens fest eingebunden, um hochauflösende Bilder und Videos von Ihrem holographic Unity-Projekt nutzen. **Während der live-Demos sollte die Kamera in einer festen Position bleiben.** Verschiebung der Kamera kann – Hologramm Jitter oder Abweichung führen. Dies ist da die zeitplanung des Videoframes und das Rendern von Hologramme auf dem PC nicht exakt synchronisiert werden können. Daher bleiben die Kamera gleichmäßig oder beschränken die Bewegung erzeugt ein Ergebnis in der Nähe die Person, die eine HoloLens trägt sehen.

Damit wird Ihre app kann Spectator angezeigt, Sie müssen zum Erstellen einer [freigegebene Benutzeroberfläche](holograms-240.md) app und stellen Sie sicher, die app kann sowohl HoloLens als auch Desktop im Unity-Editor ausgeführt. Die desktop-Version der app werden zusätzliche Komponenten, die in diesem Video mit der gerenderten Hologramme feed zusammengesetzte erstellt haben.

## <a name="how-to-set-up-spectator-view-pro"></a>Wie Sie Spectator Ansicht Pro einrichten 

### <a name="requirements"></a>Anforderungen

![Spectator Ansicht Pro Rig](images/spectatorviewrig-350px.jpg)

#### <a name="hardware-shopping-list"></a>Einkaufsliste Hardware

Unten ist eine empfohlene Liste von Hardware, aber Sie können experimentieren mit anderen kompatiblen Einheiten zu. 

|Hardwarekomponente                                                                     |Empfehlung               | 
|:--------------------------------------------------------------------------------------|:----------------------------|
|Ein PC-Konfiguration, die für die holographic-Entwicklung mit dem Emulator für HoloLens funktioniert.  |                              | 
|Kamera mit HDMI-out "oder" Fotoaufnahmen SDK                                             | Wir haben für Fotos und videoaufzeichnung, getestet der [kanon entsprechend EOS 5D Mark III](https://www.amazon.com/Canon-Frame-Full-HD-Digital-Camera/dp/B007FGYZFI/ref=sr_1_3?s=photo&ie=UTF8&qid=1480537693&sr=1-3&keywords=Canon+5D+Mark+III) Kamera. Wir haben für live-Demos, getestet der [Blackmagic Entwurf Produktion Kamera 4K](https://www.amazon.com/Blackmagic-Design-Production-Camera-Mount/dp/B00CWLSHYG/ref=sr_1_1?s=photo&ie=UTF8&qid=1480537790&sr=1-1&keywords=blackmagic+design+production+camera+4k).<br><br>Beachten Sie, dass jede Kamera eingebaut mit HDMI-Ausgabe (z. B. GoPro) funktionieren sollte. Viele der unsere Videos an, verwenden die [kanon entsprechend EF 14mm f/2.8 L II USM Ultra-Wide Winkel fest Fokus](https://www.amazon.com/Canon-Ultra-Wide-Angle-Digital-Cameras/dp/B000V5P94Q), Sie sollten jedoch eine Kameraobjektiv, die Ihren Anforderungen entspricht. | 
|Erfassen Sie Karte für Ihren PC, erhalten von Ihrer Kamera Rig kalibrieren, und eine Vorschau Ihrer zusammengesetzte Szene Farbe frames |  Wir haben getestet der [Blackmagic Entwurf Intensität Pro 4-KB-Capture-Karte](https://www.amazon.com/dp/B00U3QNP7Q). | 
|Kabel                                                                                 |  [HDMI zu Mini-HDMI](https://www.amazon.com/AmazonBasics-High-Speed-Mini-HDMI-HDMI-Cable/dp/B014I8UHXE?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o03_s00) für das Anfügen von Ihrer Kamera an Ihre Capture-Karte. Stellen Sie sicher, dass Sie eine HDMI-Formfaktor erwerben, die Ihre Kamera geeignet ist. (GoPro, gibt z. B. über [Micro HDMI](https://www.amazon.com/dp/B014I8U33I/ref=twister_B0198TA40O?_encoding=UTF8&psc=1).)<br><br>[HDMI-Kabel](https://www.amazon.com/dp/B014I8TC4E/ref=twister_B016I3XG0S?_encoding=UTF8&th=1) für die kombinierte oder auf eine Vorschau TV-feed anzeigen | 
|Bearbeitet die Aluminum Klammer ein, um Ihre HoloLens bis zur Kamera zu verbinden. | [Aluminum Klammer](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/HoloLens_Mount.stp)   | 
|3D gedruckt Adapter zur Verbindung mit der Kamera Hotshoe der HoloLens-Bereitstellung.| [Gedruckte 3D-Adapter](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/Mount_Adapter.stl)  | 
|Hotshoe Verbindungselement zum Einbinden des Hotshoe-Adapters                                       |  [Hotshoe Verbindungselement](https://www.amazon.com/Fotasy-SCX2-Adapter-Premier-Cleaning/dp/B00HPAPFNU/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) | 
|Gemischte Nuts, Bolts und tools                                                |  [1/4-20" nuts](https://www.amazon.com/Hillman-Group-150003-20-Inch-100-Pack/dp/B000BPEPNW/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img)<br>[1/4-20 "x 3/4" Bolts](https://www.amazon.com/Hard-Find-Fastener-014973100032-4-20-Inch/dp/B004S6RZPK/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) <br>[7/16 Mutter-Treiber](https://www.amazon.com/Klein-Tools-630-7-Cushion-Grip-Hollow-Shank/dp/B000BPG4CW/ref=sr_1_1?ie=UTF8&qid=1479853212&sr=8-1)<br>[T15 Torx](https://www.amazon.com/Stanley-60-011-Standard-Torx-Screwdriver/dp/B000KFXDWW/ref=sr_1_1?ie=UTF8&qid=1479853303&sr=8-1)<br>[T7 Torx](https://www.amazon.com/SE-7542ST-6-Piece-Professional-Screwdriver/dp/B000ST3K3W/ref=sr_1_1?ie=UTF8&qid=1479853479&sr=8-1) | 

#### <a name="software-components"></a>Softwarekomponenten

1. Software heruntergeladen haben, aus der [GitHub-Projekt für Spectator Ansicht](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView).
2. [Blackmagic Capture-Karte SDK](https://www.blackmagicdesign.com/support). \
 Suchen Sie nach der Desktop-Video-Entwickler-SDK in "Neueste Downloads".
3. [Video Runtime Blackmagic Desktop](https://www.blackmagicdesign.com/support). \
 Suchen Sie nach Videos Desktopsoftware Update in der "Letzten Downloads". \
 Stellen Sie sicher die Anzahl entspricht Version der SDK-Version.
4. [OpenCV 3.1](https://opencv.org/releases.html) für Kalibrierung oder ohne die Blackmagic Capture-Karte erfassen.
5. [Kanon entsprechend SDK](https://www.usa.canon.com/internet/portal/us/home/explore/solutions-services/digital-camera-sdk-information) (Optional). \
 Wenn Sie eine Kamera kanon entsprechend verwenden und Zugriff auf das SDK kanon entsprechend haben, können Sie Ihre Kamera auf Ihren PC zu Bilder mit höherer Auflösung anpassen.
6. Unity für holographic app-Entwicklung. \
 Unterstützte Version finden Sie in der OSS-Projekt.
7. Visual Studio 2015 mit den neuesten Updates.

### <a name="building-your-own-spectator-view-pro-camera"></a>Erstellen Ihre eigenen Spectator Ansicht Pro Kamera

**BEACHTEN SIE, DASS &AMP; HAFTUNGSAUSSCHLUSS:** Wenn Sie Änderungen der HoloLens-Hardware (einschließlich, aber nicht beschränkt auf, das Einrichten Ihrer HoloLens für "Spectator View") grundlegende vornehmen sollten immer Sicherheitsvorkehrungen beobachtet werden. Lesen Sie alle Anleitungen und Handbüchern, bevor die Änderungen. Es ist Ihre Aufgabe, befolgen alle Anweisungen, und verwenden Sie Tools wie angegeben. Sie können erworben oder Ihre HoloLens mit einer beschränkten Garantie oder ohne Garantie lizenziert. Lesen Sie die anwendbaren [HoloLens-Software-Lizenzbedingungen oder der Nutzungsbedingungen und Verkauf](https://www.microsoft.com/hololens/support/warranty) , Ihre Garantie Möglichkeiten zu kennen.

<br>

>[!VIDEO https://www.youtube.com/embed/aKX8UMejtWc]

#### <a name="rig-assembly"></a>Rig-Assembly

![Assemblierten Spectator Ansicht Pro Rig mit HoloLens und DSLR Kamera.](images/assembly.gif)<br>
*Assemblierten Spectator Ansicht Pro Rig mit HoloLens und DSLR Kamera*


* Verwenden Sie ein T7 Schraubendreher, um die HoloLens die Kopfband aufheben. Sobald die Schrauben lose befinden, herumzustöbern Sie, durch eine Büroklammer von der anderen Seite angezeigt.
* Entfernen Sie die Schraube Obergrenze innerhalb von der Hypervisor HoloLens mit einer kleinen flach Head Schraubendreher front.
* Verwenden Sie ein T15 Schraubendreher, um die kleinen Torx-Bolts aus, die Sie entfernen die HoloLens-Klammer entfernen und Hook gestalteten Anlagen.
* Platzieren Sie die HoloLens, auf die Klammer, und richten Sie die verfügbar gemachten Lücke an die Innenseite der Hypervisor mit die Projektion auf der Vorderseite der Klammer. Die HoloLens' Arms sollten durch die Pins am unteren Rand der Klammer bleibt.
* Fügen Sie Sie erneut, und der Hook gestalteten Anlagen zum Sichern der HoloLens, um die Klammer.
* Fügen Sie das Verbindungselement Hotshoe, an die Hotshoe der Kamera.
* Fügen Sie den Adapter für die Bereitstellung auf Verbindungselements Hotshoe.
* Drehen Sie den Adapter, damit die engen Seite weiterleiten-Sie und Parallel zur Fokus von der Kamera.
* Sichern Sie den Adapter vorhanden, mit einer 1/4" Mutter, die mit dem Treiber 7/16 Mutter.
* Positionieren Sie die Klammer für den Adapter aus, also am Anfang der HoloLens Visor so nah wie möglich an den Anfang des Fokus von der Kamera.
* Fügen Sie die Klammer mit 4-Zoll-1/4"-Display und Muttern mit dem Treiber Mutter von 7/16.

#### <a name="pc-setup"></a>PC-Setup
* Installieren Sie die Software aus dem Abschnitt der Software-Komponenten.
* Fügen Sie die Capture-Karte auf einen geöffneten PCIe-Slot auf dem Motherboard hinzu.
* Schließen Sie eine HDMI-Kabel von Ihrer Kamera im äußeren HDMI-Slot (HDMI-In) auf der Karte erfassen.
* Schließen Sie eine HDMI-Kabel mit einem optionalen Vorschau-Monitor aus dem Center HDMI-Slot (HDMI-Out) auf der Karte erfassen.

#### <a name="camera-setup"></a>Kamera-Setup
* Ändern Sie die Kamera in Anzeigemodus, damit auf die voller Auflösung von 1920 × 1080 statt auf ein zugeschnittenes 3:4 Foto Auflösung ausgegeben.
* Suchen Sie nach der Kamera HDMI-Einstellungen, und aktivieren Sie **Spiegelung** oder **zwei Monitore**.
* Legen Sie die ausgabeauflösung 1080 p.
* Deaktivieren Sie **Ansicht auf Bildschirmanzeige Live** damit alle Überlagerungen Bildschirm nicht in die zusammengesetzte feed angezeigt werden.
* Aktivieren der Kamera **Live-Ansicht**.
* Wenn die **kanon entsprechend SDK** und möchten eine Flash-Einheit verwenden, deaktivieren Sie **automatische LV dafür**.
* Schließen Sie eine HDMI-Kabel zwischen der Kamera im äußeren HDMI-Slot (HDMI-In) auf der Karte erfassen.

#### <a name="calibration"></a>Kalibrierung

Nach dem Festlegen Ihrer Spectator Ansicht Rig, müssen Sie kalibrieren, um die Position und Drehung Offset von der Kamera auf Ihrem HoloLens zu erhalten.
* Öffnen Sie die Kalibrierung Visual Studio-Projektmappe unter Calibration\Calibration.sln.
* In dieser Lösung finden Sie die Datei dependencies.props Makros für die Speicherorte inc, 3rd Party Quellen erstellt.
* Aktualisieren Sie diese Datei mit dem Speicherort Installation OpenCV 3.1, das Blackmagic SDK und dem kanon entsprechend-SDK (falls zutreffend)

![Abhängigkeit Speicherorte Momentaufnahme in Visual Studio](images/dependencies-600px.png)<br>
*Abhängigkeit Speicherorte Momentaufnahme in Visual Studio*


* Die Kalibrierung Muster Calibration\CalibrationPatterns\2_66_grid_FULL.png auf einer Oberfläche Flatfile, feste ausgeben.
* Schließen Sie Ihre HoloLens an Ihren PC über USB an.
* Aktualisieren Sie die Präprozessordefinitionen **HOLOLENS_USER** und **HOLOLENS_PW** in **"stdafx.h"** mit Portal Anmeldeinformationen für Ihre HoloLens Gerät.
* Fügen Sie die Kamera an Ihre Capture-Karte über HDMI aus, und aktivieren Sie ihn.
* Führen Sie die Kalibrierung-Lösung.
* Verschieben Sie das Schachbrettmuster rund um die Ansicht wie folgt:

![Kalibrierung Spectator Ansicht Pro Rigs](images/calibration.gif)<br>
*Kalibrierung Spectator Ansicht Pro Rigs*


* Ein Bild werden automatisch ausgeführt werden, wenn ein Schachbretts an angezeigt wird. Suchen Sie nach der weißen Licht beleuchtet, auf die HoloLens Hypervisor, bevor gelangt sind, um die nächste Haltung.
* Drücken Sie anschließend **EINGABETASTE** die Kalibrierung App den Fokus auf das Erstellen einer **CalibrationData.txt** Datei.
* Diese Datei wird gespeichert werden, um **Documents\CalibrationFiles\CalibrationData.txt**
* Überprüfen Sie diese Datei, um festzustellen, ob Ihre Kalibrierungsdaten korrekt ist:
   * **DSLR RMS** nahe 0 werden sollte.
   * **HoloLens RMS** nahe 0 werden sollte.
   * **Stereo RMS** möglicherweise werden 20 bis 50, dies ist akzeptabel, da das Sichtfeld zwischen den zwei Kameras abweichen kann.
   * **Übersetzung** wird der Abstand zwischen der HoloLens Kamera und den angefügten Kameraobjektiv. Dies ist in Meter.
   * **Drehung** sollte in der Nähe Identität sein.
   * **DSLR_fov** y-Wert sollte in der Nähe vertikale Blickfeld von Ihrem objektiv als zentraler Länge und alle Kamera Text Zuschneiden Faktoren erwartet werden.
* Wenn eine der oben genannten Werte entspricht nicht sinnvoll angezeigt werden, neu zu überdenken.
* Kopieren Sie diese Datei, um die **Assets** Verzeichnis in Ihrem Unity-Projekt.

### <a name="compositor"></a>Compositor

Der Compositor ist eine Unity-Erweiterung, die als ein Fenster im Unity-Editor ausgeführt wird. Um dies zu ermöglichen, muss die Compositor Visual Studio-Projektmappe zuerst erstellt werden.
* Öffnen Sie die Compositor Visual Studio-Projektmappe unter Compositor\Compositor.sln
* Aktualisieren Sie dependencies.props anhand derselben Kriterien aus der oben genannten Kalibrierung-Projektmappe. Wenn Sie die Kalibrierung Schritte befolgt haben, wird diese Datei bereits aktualisiert wurden.
* Erstellen Sie die gesamte Lösung als die Version und die Architektur, die Ihrer Version von Unity-Architektur entspricht. Erstellen Sie im Zweifelsfall x X86 und X64 aus.
* Wenn Sie die Lösung für X64 erstellt haben, erstellen Sie das Projekt SpatialPerceptionHelper auch als X86 fest, da sie auf die HoloLens ausgeführt werden soll.
* Schließen Sie Unity aus, wenn sie Ihre Anwendung ausgeführt wird. Unity muss erneut gestartet werden, wenn die DLLs zur Laufzeit geändert werden.
* Führen Sie Compositor\CopyDLL.cmd zum Kopieren von die DLLs, die von dieser Lösung zu Ihrem Unity-Projekt erstellt. Dieses Skript kopiert die DLLs zum Beispielprojekt enthalten ist. Nachdem Sie Ihr eigenes Projekt eingerichtet haben, können Sie CopyDLL mit einem Befehlszeilenargument auf Ihres Projekts Assets Verzeichnis gibt es auch kopieren ausführen.
* Starten Sie die Beispiel-app für Unity.

### <a name="unity-app"></a>Unity-app

Der Compositor wird als ein im Unity-Editor-Fenster ausgeführt. Das Projekt enthaltenen Beispiels bietet alles, was einrichten Spectator Ansicht nach der Compositor Entitätsformular DLLs kopiert werden.

Spectator Ansicht muss die Anwendung für die Ausführung als ein [freigegebene Benutzeroberfläche](holograms-240.md). Dies bedeutet, dass alle Zustandsänderungen, Anwendung, die für die HoloLens stattfinden werden, um die app in Unity ausgeführt wird, zu aktualisieren vernetzt müssen.

Wenn ein neues Unity-Projekt beginnen, müssen Sie eine Einrichtung zuerst durchführen:
* Kopie **Assets/Add-Ons/HolographicCameraRig** aus dem Beispielprojekt zu Ihrem Projekt.
* Fügen Sie die neuesten MixedRealityToolkit zu Ihrem Projekt, einschließlich **Freigabe**, **"csc.rsp"**, **gmcs.rsp**, und **smcs.rsp**.
* Hinzufügen Ihrer **CalibrationData.txt** -Datei in Ihrem Verzeichnis Bestand.

![Unity-Ressourcen-Directory-Momentaufnahme](images/files-400px.png)

* Hinzufügen der **HolographicCameraRig\Prefabs\SpectatorViewManager** prefab zu Ihrer Szene und die Felder ausfüllen:
   * **HolographicCameraManager** gefüllt werden soll, mit der HolographicCameraManager prefabs aus dem HolographicCameraRig prefab-Verzeichnis.
   * **Anker** gefüllt werden soll, mit dem Anchor-Prefab aus dem HolographicCameraRig prefab-Verzeichnis.
   * **Freigeben von** mit der Freigabe prefabs aus der MixedRealityToolkit gefüllt werden soll.
   * Hinweis: Wenn diese Prefabs bereits in der Projekthierarchie vorhanden sind, werden die vorhandenen prefabs (Vorlagen) statt diese Befehle verwendet werden.
   * **Spectator Ansicht IP** sollte die IP-Adresse Ihrer HoloLens Rig Spectator Ansicht angefügt werden.
   * **Freigeben von Dienst-IP** sollte die IP-Adresse des Computers die MixedRealityToolkit SharingService ausgeführt werden.
   * Optional: Wenn Sie mehrere Spectator anzeigen Rigs auf mehrere Computer angefügt haben die, **lokaler Computer-IP-Adresse** sollte festgelegt werden, mit dem PC das Spectator Ansicht Rig kommuniziert.

![Spectator Ansichten-Manager-Eigenschaften in Unity](images/spectatorviewmanager-500px.png)

* Starten Sie den MixedRealityToolkit **Freigabedienst**
* Erstellen und Bereitstellen der app, wie eine D3D-UWP, die HoloLens Rigs Spectator Ansicht angefügt.
* Bereitstellen Sie die app für alle anderen HoloLens-Geräte in der Umgebung.
* Überprüfen Sie die **im Hintergrund ausführen** Kontrollkästchen unter **bearbeiten/Project Settings/Player**.

![Führen Sie in den Hintergrund-Einstellung in Unity](images/run-in-bg-400px.png)
* Starten Sie im Fenster der Compositor unter **Spectator anzeigen/Compositor**

![Ansicht der Compositor für Spectator-Ansicht in Unity](images/compositor-500px.png)

* In diesem Fenster können Sie:
   * Starten Sie die Aufnahme von Videos
   * Aufnehmen von Bildern
   * – Hologramm Deckkraft ändern
   * Ändern des Frame-Offsets (die die Farbe Zeitstempel, der für die Erfassung Karte Wartezeit berücksichtigen passt)
   * Öffnen Sie das Verzeichnis, die, dem die Aufzeichnungen gespeichert werden
   * Anforderungsdaten Sie räumliche Zuordnung zwischen der Kamera und Spectator anzeigen (sofern eine SpatialMappingManager in Ihrem Projekt vorhanden ist)
   * Visualisieren Sie einzeln der Szene zusammengesetzte Ansicht als auch Farbe, -Hologramme und alpha-Kanal.
   * Aktivieren Sie die Kamera.
   * Drücken Sie die Wiedergabe in Unity.
   * Wenn die Kamera verschoben wird, sollte die Hologramme in Unity, wo sie in der realen Welt in Bezug auf Ihre Kamera Farbe, die Feeds sind.

## <a name="see-also"></a>Siehe auch

* [Mixed Reality-Erfassung](mixed-reality-capture.md) 
* [Mixed Reality-Erfassung für Entwickler](mixed-reality-capture-for-developers.md)
* [Freigegebene Funktionen in mixed reality](shared-experiences-in-mixed-reality.md)
* [Spectator anzeigen (Vorschau) Code auf GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/SpectatorView)
* [Spectator anzeigen (Vorschau) systemeigenen Code auf GitHub](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin)
* [Ansicht Pro Spectator-Code auf GitHub](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView)
