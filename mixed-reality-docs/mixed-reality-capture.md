---
title: Mixed-Reality-Aufnahme
description: Informationen zur Verwendung der Mixed Reality-Erfassung.
author: wguyman
ms.author: wguyman
ms.date: 10/02/2018
ms.topic: article
keywords: MRC, Mixed Reality Capture, Fotos, Video, Kamera, Erfassung, Verwendung, Stream, Livestream, Demo
ms.openlocfilehash: 7af60682f78f624e6b41ded88c8a77e70d40194c
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694485"
---
# <a name="mixed-reality-capture"></a>Mixed-Reality-Aufnahme

Hololens ermöglicht Benutzern das Mischen der realen Welt mit der digitalen Welt. Mit Mixed Reality Capture (MRC) können Sie diese Darstellung entweder als Foto oder Video erfassen. Auf diese Weise können Sie die Benutzeroberflächen für andere Benutzer freigeben, indem Sie Ihnen ermöglichen, die Hologramme anzuzeigen, wenn Sie Sie sehen. Videos und Fotos stammen aus der Sicht der ersten Personen. Verwenden Sie die [Ansicht "Betrachter](spectator-view.md)" für eine dritte Sicht.

Anwendungsfälle für die gemischte Reality-Erfassung gehen über die gemeinsame Nutzung von Videos zwischen einem sozialen Kreis hinaus. Videos können verwendet werden, um andere Personen anzuweisen, wie eine APP verwendet werden soll. Entwickler können Videos oder Stills zum Verbessern von Reproduktions Schritten und zum Debuggen von App-Erfahrungen verwenden.

## <a name="live-streaming-from-hololens"></a>Live Streaming von hololens

Das [Windows 10-Update vom Oktober 2018](release-notes-october-2018.md) bietet miracast-Unterstützung zu hololens. Klicken Sie unten im Startmenü auf die Schaltfläche **verbinden** , um eine Auswahl für miracast-fähige Geräte und Adapter anzuzeigen. Wählen Sie das Gerät aus, mit dem das Streaming beginnen soll. Wenn Sie den Vorgang abgeschlossen haben, klicken Sie unten im Startmenü auf die Schaltfläche " **trennen** ".  **Connect** und **Disconnect** sind auch im Menü schnell Aktionen verfügbar.

Das [Windows-Geräte Portal](using-the-windows-device-portal.md) und die [Microsoft hololens-Begleit-App](https://www.microsoft.com/store/productId/9NBLGGH4QWNX) machen Live Streaming-Optionen für Geräte verfügbar, die sich im Entwicklermodus befinden.

[Dynamics 365-Remote Unterstützung](https://dynamics.microsoft.com/en-us/mixed-reality/remote-assist) unterstützt Live Streaming von hololens an Mitarbeiter an Remote Standorten.

## <a name="taking-mixed-reality-captures"></a>Erfassung gemischter Realität

![Klicken Sie unten im Startmenü auf das Kamerasymbol.](images/cameraiconinpins-300px.png)<br>
*Klicken Sie unten im Startmenü auf das Kamerasymbol.*

Es gibt mehrere Möglichkeiten, eine gemischte Reality-Erfassung zu initiieren:
* Cortana kann jederzeit unabhängig von der aktuell verwendeten App verwendet werden. Sagen Sie einfach: "Hallo Cortana, nehmen Sie ein Bild" oder "Hey Cortana, Aufzeichnung starten". Zum Anhalten eines Videos sagen Sie "Hallo Cortana, Aufzeichnung anhalten".
* Wählen Sie im Startmenü die Option **Kamera** oder **Video**aus. Verwenden Sie [Air-Tap](gestures.md#air-tap) , um die integrierte MRC-Kamera-Benutzeroberfläche zu öffnen.
* Wählen Sie im Menü schnell Aktionen entweder **Kamera** oder **Video** aus, um die integrierte MRC-Kamera-Benutzeroberfläche zu öffnen.
* Apps können Ihre eigene Benutzeroberfläche für die Transformation für gemischte Realität mit benutzerdefiniertem oder, ab dem [Windows 10-Update vom Oktober 2018](release-notes-october-2018.md), der [integrierten MRC-Kamera-Benutzeroberfläche](mixed-reality-capture-for-developers.md), verfügbar machen.
* Eindeutig für hololens: 
    * Das [Windows-Geräte Portal](using-the-windows-device-portal.md) verfügt über eine Mixed Reality-Erfassungs Seite, die verwendet werden kann, um Fotos, Videos, Livestreams und Erfassungen anzuzeigen.
    * Drücken Sie die Schaltflächen " **Lautstärke** " und " **Lautstärke** " gleichzeitig, um einen Bildlauf durchführen zu können, unabhängig von der aktuell
    * Halten Sie die Schaltflächen " **Lautstärke** " und " **Lautstärke** " drei Sekunden lang gedrückt, um ein Video aufzuzeichnen. Um ein Video anzuhalten, tippen Sie auf die Schaltflächen " **Volume Up** " und " **Volume** " gleichzeitig.
* Einzigartig für immersive Headsets: 
    * Halten Sie mithilfe eines Bewegungs Controllers die **Windows** -Schaltfläche gedrückt, und tippen Sie **dann auf den** -Vorgang, um ein Bild auszuwählen. 
    * Halten Sie mithilfe eines Bewegungs Controllers die **Windows** -Taste gedrückt, und tippen Sie dann auf die **Menü** Schaltfläche, um das Video aufzuzeichnen. Halten **Sie die** **Windows** -Schaltfläche gedrückt
    
>[!NOTE]
>Das [Windows 10-Update vom Oktober 2018](release-notes-october-2018.md) ändert die Art und Weise, wie sich die Schaltfläche " Vor dem Update wird die Aufzeichnung durch die Schaltfläche "aufblühen" oder "Windows" beendet. Nach dem Update wird mit der Schaltfläche zum Durchsuchen oder der Windows-Taste das Startmenü (oder das Menü schnell Aktionen, wenn Sie sich in einer APP befinden) geöffnet. Wählen Sie im Menü **Video anhalten** aus, um die Aufzeichnung zu unterbinden.

### <a name="limitations-of-mixed-reality-capture"></a>Einschränkungen der Erfassung gemischter Realität

Bei hololens drosselt das System die Rendering-Rate auf 30Hz. Dadurch wird ein gewisser Spielraum für die MRC-Durchführung geschaffen, sodass die APP keine Konstante Budget Reserve behalten muss und die MRC-Videodaten Satz Framerate von (bis zu) 30fps entspricht.

Videos haben eine maximale Länge von fünf Minuten.

Die integrierte MRC-Kamera-Benutzeroberfläche unterstützt nur einen einzelnen MRC-Vorgang gleichzeitig (das Aufzeichnen eines Videos schließt sich gegenseitig aus).

### <a name="file-formats"></a>Dateiformate

Erfassungen gemischter Realität von Cortana Voice-Befehlen und Start Menü Tools erstellen von Dateien in den folgenden Formaten:

|  Typ  |  Format  |  Erweiterung  |  Auflösung  |  Audio | 
|----------|----------|----------|----------|----------|
|  Photo  |  [SPEICHERN](https://en.wikipedia.org/wiki/JPEG)  |  .jpg  |  3904x2196px (hololens 2)<br> 1408x792px (hololens)<br> 1920 × 1080px (immersive Headsets) |  Nicht zutreffend | 
|  Video  |  [MPEG-4](https://en.wikipedia.org/wiki/MPEG-4)  |  .mp4  |  1920 x 1080px bei 30 fps (hololens 2)<br> 1216x684px bei 24fps (hololens)<br> 1632x918px bei 30 fps (immersive Headsets) |  48kHz Stereo | 

>[!NOTE]
>Die Auflösung von Fotos und Videos kann kleiner sein, wenn die Foto-/Videokamera bereits von einer anderen Anwendung verwendet wird, während Live Streaming oder wenn die Systemressourcen niedrig sind.

### <a name="video-stabilization"></a>Video Stabilisierung

Standardmäßig:
* Die Videostabilisierung mit der Latenzzeit wird beim Live Streaming über miracast angewendet.
* Die Videostabilisierung mit langer Wartezeit wird auf Videos angewendet, die mit der integrierten MRC-Kamera-Benutzeroberfläche, den Cortana-Sprachbefehlen und dem Windows-Geräte Portal aufgezeichnet wurden.

## <a name="viewing-mixed-reality-captures"></a>Anzeigen von Mixed Reality-Erfassungen

Fotos und Videos mit gemischter Realität werden im Ordner "Kamera Roll" des Geräts gespeichert. Auf diese kann über die [Fotos-App](see-your-photos.md#photos-app) oder den Datei-Explorer zugegriffen werden.

Auf einem PC, der mit hololens verbunden ist, können Sie auch das [Windows-Geräte Portal](using-the-windows-device-portal.md#mixed-reality-capture) oder den Datei-Explorer Ihres PCs ([über MTP](release-notes-april-2018.md#new-features-for-hololens)) verwenden.

Wenn Sie die [onedrive-App](https://www.microsoft.com/p/onedrive/9wzdncrfj1p3)installieren, können Sie den **Kamera Upload aktivieren,** und ihre MRC-Fotos und-Videos werden mithilfe von onedrive mit onedrive und ihren anderen Geräten synchronisiert.

>[!NOTE]
>Ab dem Windows 10-Update vom April 2018 werden Ihre Fotos und Videos von der Fotos-APP nicht mehr auf onedrive hochgeladen.

## <a name="see-also"></a>Siehe auch
* [Spectator View](spectator-view.md)
* [Ausrichtbare Kamera](locatable-camera.md)
* [Mixed Reality-Aufnahme für Entwickler](mixed-reality-capture-for-developers.md)
* [Anzeigen Ihrer Fotos](see-your-photos.md)
* [Verwenden des Windows-Geräteportals](using-the-windows-device-portal.md)
