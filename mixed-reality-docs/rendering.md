---
title: Rendering
description: Holographic Rendering ermöglicht Ihrer app ggf. ein Hologramm in eine genaue Position in die Welt um den Benutzer zu zeichnen, ob es genau in der realen Welt oder innerhalb von Ihnen erstellten virtuellen Bereich platziert wird.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Rendering, – Hologramm
ms.openlocfilehash: 5271e94521b99e76998c2cbb43475a5f3f847917
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829900"
---
# <a name="rendering"></a>Rendering

Holographic Rendering ermöglicht Ihrer app ggf. ein Hologramm in eine genaue Position in die Welt um den Benutzer zu zeichnen, ob es genau in der realen Welt oder innerhalb von Ihnen erstellten virtuellen Bereich platziert wird. [Hologramme](hologram.md) erfolgen Objekte von Sounds und Licht und Rendering ermöglicht Ihrer app das Licht hinzufügen.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Funktion</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></td>
    </tr>
     <tr>
        <td>Rendering</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="holographic-rendering"></a>Holographic rendering

Schlüssel für das Rendern von holographic ist das wissen, ob Sie eine durchsichtigen Anzeige wie HoloLens, die dem Benutzer, die sowohl die physische Welt und Ihre Hologramme zusammen – finden Sie unter ermöglicht oder eine nicht transparente Anzeige wie eine Windows Mixed Reality immersive Kopfhörer, welche Blöcke Rendern der ganzen Welt.

Geräte mit **durchsichtigen zeigt**, z. B. [HoloLens](hololens-hardware-details.md), Hinzufügen von Licht auf der ganzen Welt. Schwarze Pixel werden vollständig transparent, während hellere Pixel zunehmend nicht transparent sein werden. Da das Licht aus den zeigt auf das Licht aus der realen Welt hinzugefügt wird, sind auch weißen Pixel etwas lichtdurchlässiger.

Während eine Tiefe Cue stereoskopische Rendering für Ihre Hologramme bereitgestellt werden, Hinzufügen von [Erdung Effekte](interaction-fundamentals.md) können Benutzer leichter welche Oberfläche ggf. ein Hologramm in der Nähe befindet. Ein erden-Verfahren ist, fügen einen Schein um ggf. ein Hologramm auf der Oberfläche in der Nähe, und klicken Sie dann rendern einen Schatten für diese leuchten. Auf diese Weise wird Ihr Schatten Subtrahieren von Licht aus der Umgebung angezeigt. [Räumliche Sound](spatial-sound.md) kann eine andere äußerst wichtig Tiefe Cue, lassen die Ursache der Benutzer über die Entfernung und den relativen Speicherort der ggf. ein Hologramm sein.

Geräte mit **nicht transparente zeigt**, z. B. [Windows Mixed Reality immersive Headsets](immersive-headset-hardware-details.md), blockiert der ganzen Welt. Schwarze Pixel werden Schwarz, und eine beliebige andere Farbe als die entsprechende Farbe für den Benutzer angezeigt. Ihre app ist für das Rendern alle Elemente, die dem Benutzer angezeigt wird, daher ist es sogar noch wichtiger, eine Konstante Aktualisierungsrate beibehalten, damit Benutzer eine angenehme benutzererfahrung verantwortlich.

## <a name="predicted-rendering-parameters"></a>Vorhergesagte Renderingparameter

Mixed Reality-Headsets (HoloLens und immersive Headsets) fortlaufend verfolgen, Position und Ausrichtung des Erfolgs des Benutzers, relativ zu ihrer Umgebung. Wie Ihre app beginnt, die nächsten Frames vorbereiten, sagt das System, in denen des Benutzers Kopf in der Zukunft zu dem Moment entsprechen, die auf die die Anzeige der Frame angezeigt werden. Basierend auf dieser Vorhersage, berechnet das System die Ansichts- und Projektionstransformation zu verwendendentransforamtionen für diesen Frame. Ihre Anwendung **müssen diese Transformationen verwenden, um richtige Ergebnisse zu erzielen**; Wenn nicht vom System bereitgestellten Transformationen verwendet werden, das resultierende Image wird nicht im Einklang mit der realen Welt, was Benutzer stören.

Beachten Sie, dass das System genau Vorhersagen, wenn ein neues Bild zeigt die erreichen wird, ständig die effektive End-to-End-Latenz, der Rendering-Pipeline von Ihrer app gemessen wird. Während das System auf die Länge der Ihrer Rendering-Pipeline angepasst wird, können Sie – Hologramm Stabilität weiter verbessern, von dieser Pipeline so kurz wie möglich zu halten.

Anwendungen, die erweiterte Techniken verwenden, um die Vorhersage System zu erweitern, können die Ansichts- und Projektionstransformation Transformationen von System überschreiben. Diese apps müssen immer noch vom System bereitgestellten Transformationen als Grundlage für ihre benutzerdefinierte Transformationen verwenden müssen, um aussagekräftige Ergebnisse zu erzeugen.

## <a name="other-rendering-parameters"></a>Andere Renderingparameter

Beim Rendern eines Frames, wird das System den Viewport für die Back-Puffer angegeben, in dem Ihre Anwendung gezeichnet werden soll. Dieser Viewport wird oft kleiner als die vollständige Größe des Puffers Frame. Unabhängig von der Viewportgröße vergrößern das System nach dem Rendern des Frames von der Anwendung das Bild, um während des gesamten Entwicklungsprozesses der Anzeige zu füllen.

Für Anwendungen, die sich nicht auf die erforderlichen Aktualisierungsrate gerendert finden [Parameter für das Rendering können konfiguriert werden,](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) arbeitsspeicherauslastung und/oder Rendering Kosten auf Kosten einer erhöhten Pixel Aliasing zu reduzieren. Das Format des Hintergrundpuffers kann auch geändert werden die bei einigen apps können Sie um Arbeitsspeicher, Bandbreite und Pixel-Durchsatz zu verbessern.

Die Rendering-Frustums, Auflösung und Framerate, die in dem Ihre app aufgefordert wird, Rendern von Frame zu Frame ggf. auch geändert und können über das linke und Rechte Auge abweichen. Z. B., wenn [mixed Reality-Erfassung](mixed-reality-capture.md) (MRC) aktiv ist und die [Foto/Video-Kamera-Ansichtskonfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) ist nicht entschieden – in ein Auge mit einem größeren Blickfeld oder Auflösung gerendert werden kann.

Für jeden angegebenen Rahmen, Ihre app *müssen* mit der Ansicht transformieren, Projektion Transformation und Viewport-Lösung, die vom System bereitgestellten gerendert werden. Darüber hinaus muss Ihrer Anwendung niemals davon ausgehen, dass alle Parameter für die Rendering-Ansicht von Frame zum festen bleibt. Engines wie Unity behandeln alle diese Transformationen, die für Sie in ihre eigenen Objekte Kamera, sodass die physische Bewegung Ihrer Benutzer und den Zustand des Systems immer berücksichtigt wird. Wenn Ihre app noch weiter für virtuelle Bewegung der Benutzer über die Welt (z. B. mithilfe der Ministick auf eine Gamepad) zulässt, können Sie hinzufügen ein übergeordnetes "Lichtanlage"-Objekt über die Kamera, die verschoben wird, verursacht die Kamera sowohl des Benutzers virtuelle und physische Bewegung entsprechend. Wenn Ihre app den Ansichtstransformation, Projektion Transformations- oder Viewport-Dimension, die vom System bereitgestellten ändert, muss es das System durch Aufrufen der entsprechenden informieren [außer Kraft setzen-API-](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose).

Um die Stabilität Ihrer holographic Rendering zu verbessern, sollte Ihre app für Windows jeden Frame Tiefenpuffer bereitstellen, die, den Sie für das Rendering verwendet. Wenn Ihre app einen Tiefenpuffer bereitstellt, sollte sie kohärente Tiefenwerte, mit Tiefe in Metern von der Kamera ausgedrückt haben. Dadurch wird das System Ihre pro-Pixel-Depth-Daten zu verwenden, um Inhalt besser zu stabilisieren, wenn der Benutzer die Head am Ende leicht aus dem vorhergesagten Speicherort versetzt. Wenn Sie nicht Ihre Tiefenpuffer bereitstellen können, sollten Sie stattdessen Geben Sie einen Fokuspunkt und Normal, definieren eine Fläche, die schneidet die meisten Ihrer Inhalte. Wenn sowohl der Tiefenpuffer und eine Ebene Fokus bereitgestellt werden, kann das System beide verwenden. Insbesondere kann es hilfreich sein, geben Sie den Tiefenpuffer und einen Fokuspunkt gehört eine Geschwindigkeitsvektors bei Ihrer app Hologramme angezeigt werden, während der Übertragung.

Für alle auf niedriger Ebene Details hier sehen Sie sich die [Rendern in DirectX](rendering-in-directx.md) Artikel.

## <a name="holographic-cameras"></a>Holographic Kameras

Windows Mixed Reality führt das Konzept einer **holographic Kamera**. Holographic Kameras ähneln herkömmlichen Kamera finden Sie in der 3D-Grafik Texte: sie definieren die systemexterne (Position und Ausrichtung) und systeminterne Kameraeigenschaften (Beispiel: Feld-der-Ansicht) verwendet, um eine virtuelle 3D-Szene anzuzeigen. Im Gegensatz zu herkömmlichen 3D Kameras ist die Anwendung nicht in der die Position, Ausrichtung und systeminterne Eigenschaften der Kamera-Steuerelement. Die Position und Ausrichtung der holographic Kamera wird dagegen implizit gesteuert, von der Bewegung der Benutzer. Der Bewegung der Benutzer wird an die Anwendung pro Frame für Frame über eine Ansichtstransformation mittels Relay weitergeleitet. Entsprechend der Kamera systeminterne Eigenschaften werden definiert, indem kalibrierten Speicherverfahrens des Geräts und Frame für Frame über die Projektion Transformation weitergeleitet.

Im Allgemeinen wird Ihre app für eine einzelne Stereo Kamera das rendering werden. Allerdings eine stabile Renderingschleife sollte unterstützen mehrere Kameras und sollte mono und Stereo-Kameras unterstützen. Beispielsweise kann das System Ihre app aus Sicht der anderen gerendert werden soll, wenn der Benutzer über ein Feature wie aktiviert lassen [mixed Reality-Erfassung](mixed-reality-capture.md) (MRC), abhängig von der Form von der betreffenden Kopfhörer. Apps, die mehrere Kameras zu unterstützen, können Sie abrufen, indem [Entscheidung in](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) auf die [Art](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) von Kameras, die unterstützt werden können.

## <a name="volume-rendering"></a>Volume-rendering

Beim Rendern von medizinischen MRI oder Volumes in 3D engineering [Volume Rendering](volume-rendering.md) Verfahren werden häufig verwendet. Diese Techniken können besonders interessant sein in mixed Reality, in dem Benutzer auf natürliche Weise einem Volume dieser Art von wichtige Winkel, anzeigen können, indem Sie einfach ihren Köpfen verschieben.

## <a name="supported-resolutions-on-hololens-1st-gen"></a>Lösungen für HoloLens unterstützt (1. Generation)
> [!NOTE]
> Es werden weitere Updates, die in der Zukunft in diesem Artikel stammen. [Zeigen Sie die Updateliste](release-notes-april-2018.md)

* Die aktuellen und maximalen unterstützten Auflösungen sind Eigenschaften von den [Ansichtskonfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration). HoloLens ist standardmäßig auf die maximale Auflösung, die 720p (1268 x 720) ist, festgelegt.
* Die niedrigste unterstützte Viewportgröße ist 50 % der 720p, die 360p (634 x 360) ist. Für HoloLens ist dies ein ViewportScaleFactor von 0,5.
* Alles, der niedriger als 540p ist **nicht empfohlen,** aufgrund visual leistungsverschlechterung verursachen, kann jedoch verwendet werden, Bottle Necks in Pixel Füllrate ermitteln.

## <a name="supported-resolutions-on-hololens-2"></a>Unterstützte Lösungen für HoloLens 2

> [!NOTE]
> Weitere Anleitungen, die speziell für HoloLens 2 [bald](index.md#news-and-notes).


## <a name="see-also"></a>Siehe auch
* [Hologrammstabilität](hologram-stability.md)
* [Rendern in DirectX](rendering-in-directx.md)