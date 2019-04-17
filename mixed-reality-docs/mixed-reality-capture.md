---
title: Mixed-Reality-Aufnahme
description: Informationen zur Verwendung von mixed Reality erfassen.
author: wguyman
ms.author: wguyman
ms.date: 10/02/2018
ms.topic: article
keywords: MRC, mixed Reality Capture, Fotos, Video, Kamera, Erfassung, Nutzung, Stream, Livestream, demo
ms.openlocfilehash: 18a80083bd25974905874c6c2ec0de87dc7424ab
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596711"
---
# <a name="mixed-reality-capture"></a>Mixed-Reality-Aufnahme

HoloLens gibt Benutzern die Möglichkeit der Mischung der realen Welt mit der digitalen Welt. Mixed Reality-Erfassung (MRC) können Sie diese Erfahrung als ein Foto oder ein Video zu erfassen. Dadurch können Sie die Benutzeroberfläche für andere Benutzer freigeben, indem Sie zulassen, um die Hologramme anzuzeigen, wie sie sehen. Diese Videos und Fotos sind aus Sicht der Zeitraffervideos. Verwenden Sie für eine Sicht von Zeitraffervideos [Spectator Ansicht](spectator-view.md).

Freigeben von Videos für eine sozialen Umfeld ist Anwendungsfälle für die Erfassung von mixed Reality hinausgehen. Videos können verwendet werden, um andere anzuweisen, wie eine app verwenden. Entwickler können Videos oder Standbilder verwenden, verbessern die Schritte zur Reproduktion und Debuggen der app-Umgebungen.

## <a name="live-streaming-from-hololens"></a>Live-streaming von HoloLens

Die [Windows 10 Oktober 2018 Update](release-notes-october-2018.md) HoloLens Miracast-Unterstützung hinzugefügt. Wählen Sie die **Connect** am unteren Rand des Startmenüs, um eine Auswahl für die Miracast-fähigen Geräten und -Adapter zu öffnen. Wählen Sie das Gerät, das Sie streaming beginnen möchten. Wählen Sie abschließend die **trennen** am unteren Rand des Startmenüs.  **Herstellen einer mit** und **trennen** sind auch auf das Menü für schnelle Aktionen verfügbar. 

Die [Windows Device Portal](using-the-windows-device-portal.md) macht live-streaming-Optionen für Geräte, die im Entwicklermodus sind.

## <a name="taking-mixed-reality-captures"></a>Nehmen mixed Reality erfasst

![Klicken Sie auf das Symbol "Kamera" am unteren Rand des Startmenüs](images/cameraiconinpins-300px.png)<br>
*Klicken Sie auf das Symbol "Kamera" am unteren Rand des Startmenüs*

Es gibt mehrere Möglichkeiten, eine mixed Reality-Aufzeichnung starten:
* Cortana kann auf alle Zeiten unabhängig von der ausgeführten app verwendet werden. Nur sagen, "Hey Cortana, ein Foto zu machen" oder "Hey Cortana, Aufzeichnung zu starten." Um ein Video zu beenden, z. B. "Hey Cortana, beenden Sie die Aufzeichnung."
* Wählen Sie im Startmenü entweder **Kamera** oder **Video**. Verwendung [tippbewegung](gestures.md#air-tap) um die integrierte MRC-Kamera-Benutzeroberfläche zu öffnen.
* Wählen Sie auf das Menü für schnelle Aktionen, entweder **Kamera** oder **Video** um die integrierte MRC-Kamera-Benutzeroberfläche zu öffnen.
* Apps sind in der Lage, eigene Benutzeroberfläche für mixed Reality-Erfassung mit benutzerdefinierten oder, wie der verfügbar zu machen die [Windows 10 Oktober 2018 Update](release-notes-october-2018.md), [integrierte MRC-Kamera-Benutzeroberfläche](mixed-reality-capture-for-developers.md).
* Nur für HoloLens: 
    * [Windows Device Portal](using-the-windows-device-portal.md) verfügt über eine mixed Reality-Capture-Seite, die kann verwendet werden, werden die Fotos, Videos, live-Stream, und zeigen Sie erfasst.
    * Drücken Sie sowohl die **lauter** und **zum Verringern der Lautstärke** Schaltflächen gleichzeitig aus, um ein Foto, unabhängig von der ausgeführten app zu machen.
    * Halten Sie die **lauter** und **zum Verringern der Lautstärke** Schaltflächen für die drei Sekunden zum Starten der Aufzeichnung eines Videos. Um ein Video zu beenden, tippen Sie auf beiden **lauter** und **zum Verringern der Lautstärke** gleichzeitig Schaltflächen.
* Nur für immersive Headsets: 
    * Mit einem Controller während der Übertragung enthalten die **Windows** Schaltfläche, und tippen Sie dann auf die **Trigger** auf ein Foto zu machen. 
    * Mit einem Controller während der Übertragung enthalten die **Windows** Schaltfläche, und tippen Sie dann auf die **Menü** Schaltfläche zum Starten der Aufnahme von Videos. Halten Sie die **Windows** Schaltfläche, und tippen Sie dann auf die **Trigger** zum Beenden der Aufzeichnung video.
    
>[!NOTE]
>Die [Windows 10 Oktober 2018 Update](release-notes-october-2018.md) ändert Verhalten Bloom und Windows-Schaltfläche. Vor dem Update würde der Bloom Geste oder der Windows-Schaltfläche Beenden Sie die Aufzeichnung. Nach dem Update öffnet die Bloom-Geste oder die Schaltfläche "Windows" im Startmenü (oder das Menü für schnelle Aktionen, wenn Sie sich auf eine app). Wählen Sie im Menü **beenden Video** Beenden der Aufzeichnung.

### <a name="limitations-of-mixed-reality-capture"></a>Einschränkungen von mixed Reality-Erfassung

Für HoloLens wird das System die Render-Rate bis 30 Hz drosseln. Dies erstellt einige Spielraum für MRC ausgeführt werden, damit die Anwendung nicht zu einer Konstanten Budget Reserve muss und entspricht auch die MRC Videoaufnahme Framerate von 30 BpS.

Videos haben eine maximale Länge von fünf Minuten.

Die integrierten MRC-Kamera-Benutzeroberfläche unterstützt nur einen einzelnen MRC-Vorgang zu einem Zeitpunkt (aufnehmen eines Bilds sich gegenseitig ausschließende aus Aufzeichnen eines Videos ist).

### <a name="file-formats"></a>Dateiformate

Mixed Reality aus Cortana Sprachbefehle erfasst und Menü "Start"-Tools Erstellen von Dateien in den folgenden Formaten:

|  Typ  |  Format  |  Erweiterung  |  Auflösung  |  Audio | 
|----------|----------|----------|----------|----------|
|  Photo  |  [JPEG](https://en.wikipedia.org/wiki/JPEG)  |  .jpg  |  1408x792px (HoloLens) 1920 × 1080 Pixel (Immersive Headsets) |  Nicht zutreffend | 
|  Video  |  [MPEG-4](https://en.wikipedia.org/wiki/MPEG-4)  |  .mp4  |  1408x792px (HoloLens) 1632x918px (Immersive Headsets) |  48kHz Stereo | 

## <a name="viewing-mixed-reality-captures"></a>Anzeigen von mixed Reality erfasst

Mixed Reality Capture Fotos und Videos werden des Geräts "Eigene Aufnahmen" Ordner gespeichert. Diese können auf das über die [Fotos-app](see-your-photos.md#photos-app) oder Datei-Explorer.

Auf einem PC mit HoloLens verbunden sind, können Sie auch [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture) oder Datei-Explorer Ihres Computers ([über MTP](release-notes-april-2018.md#new-features-for-hololens)).

Bei der Installation der [OneDrive-app](https://www.microsoft.com/p/onedrive/9wzdncrfj1p3), können Sie aktivieren **Kamera Upload** und Ihre MRC Fotos und Videos in OneDrive und Ihren anderen Geräten, die mithilfe von OneDrive synchronisiert werden.

>[!NOTE]
>Ab Windows 10 April 2018 Update Fotos Hochladen der app wird nicht mehr Ihre Fotos und Videos in OneDrive.

## <a name="see-also"></a>Siehe auch
* [Spectator anzeigen](spectator-view.md)
* [Gebietsschemabezogene Kamera](locatable-camera.md)
* [Mixed Reality-Erfassung für Entwickler](mixed-reality-capture-for-developers.md)
* [Ihre Fotos anzeigen](see-your-photos.md)
* [Verwenden die Windows Device Portal](using-the-windows-device-portal.md)
