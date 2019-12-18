---
title: 'Lernprogramme für räumliche Audiodaten: 3. Spatialisieren von Audiodaten von einem Video'
description: Importieren Sie ein Video Medienobjekt in Ihr Unity-Projekt, und räumlichen Sie die Audiodaten aus dem Video.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: Gemischte Realität, Unity, Tutorial, hololens2, räumliche Audiodaten
ms.openlocfilehash: 1e5c84fd7d14cc5edc78839bbdf91590cc7fd8e7
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182747"
---
# <a name="spatializing-audio-from-a-video"></a>Spatialisieren von Audiodaten von einem Video
In diesem dritten Kapitel des Moduls Spatial-Audiodaten der Unity-Lernprogramme hololens 2 werden Sie Folgendes tun:
* Importieren eines Videos und Hinzufügen eines Video Players
* Video auf einem Quadranten abspielen
* Leiten Sie Audiodaten aus dem Video an das Quadrangle weiter, und räumlichen Sie die Audiodaten.

## <a name="import-a-video-and-add-a-video-player"></a>Importieren eines Videos und Hinzufügen eines Video Players

Ziehen Sie eine Videodatei in das **Projekt** Bereich Ihres Unity-Projekts. Sie können [dieses Video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) aus dem Beispiel Projekt für räumliche Audiodaten verwenden.

![Ordner "Assets" mit Video](images/spatial-audio/assets-folder-with-video.png)

Durch das Anpassen der Qualitätseinstellungen für den Videoclip kann die reibungslose Wiedergabe auf hololens 2 sichergestellt werden. Klicken Sie im **Projekt** Bereich auf die Videodatei. Überschreiben Sie im **Inspektor** -Bereich der Videodatei die Einstellungen für Windows Store-Apps und:
* **Transcode** aktivieren
* Legen Sie **Codec** auf H264 fest.
* **Modus "Bitrate** " auf "niedrig" festlegen
* Legen Sie **räumliche Qualität** auf mittlere räumliche Qualität fest.

Nach diesen Anpassungen sieht der **Inspektor** -Bereich für die Videodatei wie folgt aus:

![Video-Eigenschaften Bereich](images/spatial-audio/video-property-pane.png)

Fügen Sie als nächstes der **Hierarchie** ein **Video Player** -Objekt hinzu, indem Sie mit der rechten Maustaste auf den Bereich **Hierarchie** klicken und **Video > Video Player**auswählen:

![Video Player in der Hierarchie](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a>Abspielen von Videos auf einem Quadranten
Das **Video Player** -Objekt benötigt ein texturiertes Spielobjekt, auf dem das Video dargestellt werden soll. Fügen Sie zunächst der **Hierarchie** ein **Quad** hinzu, indem Sie mit der rechten Maustaste auf den Bereich **Hierarchie** klicken und **3D-Objekt-> Quad**:

![Quad zur Hierarchie hinzufügen](images/spatial-audio/add-quad-to-hierarchy.png)

Um sicherzustellen, dass das **Quad** vor dem Benutzer angezeigt wird, wenn die Anwendung gestartet wird, legen Sie die **Positions** -Eigenschaft des **Quad** auf (0, 0, 2) und die **Scale** -Eigenschaft auf (1,28, 0,72, 1) fest. Nachdem diese Änderungen vorgenommen wurden, sieht die **Transformations** Komponente im **Inspektor** -Bereich für das **Quad** wie folgt aus:

![Quad-Transformation](images/spatial-audio/quad-transform.png)

Um das Vierfache mit **Video zu strukturieren** , erstellen Sie eine neue **Rendering-Textur**. Klicken Sie im **Projekt** Bereich mit der rechten Maustaste, und wählen Sie **Create-> Rendering Texture**aus:

![Rendering-Textur erstellen](images/spatial-audio/create-render-texture.png)

Legen Sie im **inspektorbereich** der **Rendering-Textur**die **size** -Eigenschaft so fest, dass Sie mit der nativen Auflösung des Videos in Auflösung von 1280X720 identisch ist Um dann eine gute Renderingleistung auf hololens 2 sicherzustellen, legen Sie die **Tiefe Puffer** Eigenschaft auf **mindestens 16 Bits**fest. Nach diesen Einstellungen sieht der **Inspektor** -Bereich für die **Rendering-Textur** wie folgt aus:

![Rendering-Textur Eigenschaften](images/spatial-audio/render-texture-properties.png)

Verwenden Sie als **nächstes die neue**Rendering- **Textur** als Textur für das Vierfache:
1. Ziehen Sie **die Rendering-Textur** aus dem **Projekt** Bereich **auf das Vierfache in der** **Hierarchie** .
2. Um eine gute Leistung bei hololens 2 sicherzustellen, wählen Sie im **Inspektor** -Bereich für den **Quad**den **Standard-Shader von Mixed Reality Toolkit**aus.

Mit diesen Einstellungen sieht die **Textur** Komponente im **Inspektor** -Bereich für das **Quad** wie folgt aus:

![Vier Textur Eigenschaften](images/spatial-audio/quad-texture-properties.png)

Öffnen Sie den **Inspektor** -Bereich für den **Video Player** , und legen Sie Folgendes fest, um den neuen **Video Player** und die **Rendering-Textur** für die Wiedergabe des Videoclips
* Legen Sie die Eigenschaft " **Video Clip** " auf Ihre Videodatei fest.
* Aktivieren Sie das Kontrollkästchen **Schleife** .
* Festlegen der **Ziel Textur** auf die neue rendertextur

Der **Inspektor** -Bereich für den **Video Player** sieht nun wie folgt aus:

![Video Player-Eigenschaften](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a>Spatialisieren der Audiodaten aus dem Video
Erstellen Sie im **Inspektor** -Bereich **für das**vierfache eine **Audioquelle** , an die Sie die Audiodatei aus dem Video weiterleiten:
* Klicken Sie am unteren Rand des Bereichs auf **Komponente hinzufügen** .
* Hinzufügen einer **Audioquelle**

Dann in der **Audioquelle**:
* **Ausgabe** auf Ihren Mixer festlegen
* Aktivieren Sie das Feld **spatialize** .
* Verschieben Sie den Schieberegler für **räumliche Blend** auf 1 (3D).

Nachdem diese Änderungen vorgenommen wurden, sieht die **audioquellkomponente** im **Inspektor** -Bereich für das **Quad** wie folgt aus:

![Quad-audioquellinspektor](images/spatial-audio/quad-audio-source-inspector.png)

Um den **Video Player** so festzulegen, dass seine Audiodaten an die **Audioquelle** auf dem **Quad**weitergeleitet werden, öffnen Sie den **Inspektor** -Bereich für den **Video Player** und:
* Legen Sie den **Audioausgabemodus** auf "Audioquelle" fest.
* Legen Sie die Eigenschaft **Audioquelle** auf Quad fest.

Nachdem diese Änderungen vorgenommen wurden, sieht der Bereich **Inspector** für den **Video Player** wie folgt aus:

![Video Player-Audioquelle festlegen](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a>Nächste Schritte
Testen Sie Ihre APP auf einem hololens 2 oder im Unity-Editor. Sie sehen und hören das Video, und die Audiodaten aus dem Video werden räumlich.

Fahren Sie mit [Kapitel 4](unity-spatial-audio-ch4.md) fort, um die-Schaltfläche zum Aktivieren und Deaktivieren der Spatialisierung zur Laufzeit zu verwenden.

