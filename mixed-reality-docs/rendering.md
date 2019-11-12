---
title: Rendering
description: Das Holographic-Rendering ermöglicht der APP, ein Hologramm an einer exakten Position in der Welt um den Benutzer zu zeichnen, unabhängig davon, ob es sich genau in der physischen Welt oder innerhalb eines virtuellen Bereichs befindet, den Sie erstellt haben.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Rendering, – Hologramm
ms.openlocfilehash: 9c32d8ddf5a1fb9e9d991211756ba1306f4d3fa9
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926859"
---
# <a name="rendering"></a>Rendering

Das Holographic-Rendering ermöglicht es Ihrer Anwendung, ein – Hologramm an einer exakten Position in der Welt um den Benutzer zu zeichnen, egal ob Sie genau in der physischen Welt oder innerhalb eines virtuellen Bereichs platziert ist, den Sie erstellt haben. [Holograms](hologram.md) sind Objekte aus Sound und Licht. Durch Rendering kann die Anwendung das Licht hinzufügen.

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Rendering</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="holographic-rendering"></a>Holografisches Rendering

Der Schlüssel für das holografische Rendering ist zu wissen, ob Sie zu einer anzeigen-through-Anzeige wie hololens gerendert werden, mit der dem Benutzer sowohl die physische Welt als auch die Hologramme angezeigt werden, oder eine nicht transparente Anzeige wie ein Windows Mixed Reality-immersives Headset, das blockiert wird. die Welt.

Geräte mit **Anzeige Anzeige**, z. b. [hololens](hololens-hardware-details.md), können der Welt ein Licht hinzufügen. Schwarze Pixel sind vollständig transparent, und hellere Pixel sind immer transparenter. Da das Licht aus der Anzeige dem Licht aus der realen Welt hinzugefügt wird, sind weiße Pixel etwas leicht durchsichtig.

Obwohl das stereoverarbeitungs-Rendering einen tiefen Hinweis für Ihre Hologramme bietet, kann das Hinzufügen von Grund [Effekten](interaction-fundamentals.md) dazu beitragen, dass Benutzern leichter angezeigt werden kann, welche Oberfläche ein – Hologramm- Ein Grundverfahren besteht darin, einen Glanz um ein Hologramm auf der nahe gelegenen Oberfläche hinzuzufügen und dann einen Schatten gegen diesen Glanz zu erzeugen. Auf diese Weise scheint ihr Schatten das Licht aus der Umgebung zu subtrahieren. [Räumlicher Sound](spatial-sound.md) ist ein weiterer äußerst wichtiger Hinweis auf die Tiefe und ermöglicht es den Benutzern, die Entfernung und den relativen Speicherort eines holograms zu verdeutlichen.

Geräte mit nicht transparenten **Anzeige**, wie z. b. [Windows Mixed Reality (immersive Headsets](immersive-headset-hardware-details.md)), blockieren die Welt. Schwarze Pixel sind solide schwarz, und jede andere Farbe wird dem Benutzer als Farbe angezeigt. Ihre Anwendung ist dafür verantwortlich, alles zu rendern, was der Benutzer sieht. Dadurch ist es sogar noch wichtiger, eine Konstante Aktualisierungsrate beizubehalten, damit Benutzer über eine bequeme benutzerfreundliche Benutzerfunktion verfügen.

## <a name="predicted-rendering-parameters"></a>Vorhergesagte Rendering

Gemischte Reality-Headsets (hololens und immersive Headsets) verfolgen kontinuierlich die Position und Ausrichtung des Benutzer Kopfes in Bezug auf Ihre Umgebung. Wenn Ihre Anwendung mit der Vorbereitung des nächsten Frames beginnt, sagt das System vorher, wo der Benutzer in der Zukunft zu dem genauen Zeitpunkt angezeigt wird, in dem der Frame in der Anzeige angezeigt wird. Basierend auf dieser Vorhersage berechnet das System die Ansichts-und Projektions Transformationen, die für diesen Frame verwendet werden sollen. Die Anwendung **muss diese Transformationen verwenden, um korrekte Ergebnisse zu erzielen**. Wenn vom System bereitgestellte Transformationen nicht verwendet werden, wird das resultierende Bild nicht an der realen Welt ausgerichtet, was zu Benutzer Unannehmlichkeiten führt.

Beachten Sie, dass das System die effektive End-to-End-Latenz der Renderingpipeline Ihrer Anwendung ständig misst, um genau vorherzusagen, wann ein neuer Frame die Anzeige erreicht. Während das System an die Länge ihrer Renderingpipeline angepasst wird, können Sie die hologrammstabilität verbessern, indem Sie diese Pipeline so kurz wie möglich halten.

Anwendungen, die erweiterte Techniken zum Erweitern der System Vorhersage verwenden, können die systemansichts-und Projektions Transformationen überschreiben. Diese Anwendungen müssen weiterhin vom System bereitgestellte Transformationen als Grundlage für Ihre benutzerdefinierten Transformationen verwenden, um sinnvolle Ergebnisse zu erzielen.

## <a name="other-rendering-parameters"></a>Andere Renderingparameter

Beim Rendern eines Frames gibt das System den backpufferviewport an, den die Anwendung zeichnen soll. Dieser Viewport ist häufig kleiner als die vollständige Größe des Frame Puffers. Unabhängig von der Viewportgröße, sobald der Frame von der Anwendung gerendert wird, wird das Bild durch das System hochskaliert, um die gesamte Anzeige auszufüllen.

Bei Anwendungen, die nicht mit der erforderlichen Aktualisierungsrate gerendert [werden können, können systemrenderingparameter so konfiguriert werden](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) , dass die Arbeitsspeicher Auslastung und renderingkosten auf Kosten eines größeren Pixel Aliasing reduziert werden. Das Hintergrund Puffer Format kann auch geändert werden, was für einige apps helfen kann, die Arbeitsspeicher Bandbreite und den Pixel Durchsatz zu verbessern.

Das Rendern von "Frustum", "Resolution" und "Framerate", in dem Ihre APP zum Rendern aufgefordert wird, kann sich auch von Frame zu Frame ändern und kann sich auf der linken und rechten Seite unterscheiden. Wenn z. b. die Transformation für [gemischtes auflösen (Mixed Reality Capture](mixed-reality-capture.md) , MRC) aktiv ist und die [Bild-/Videokamera-Ansichts Konfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) nicht aktiviert ist, kann ein Auge mit einem größeren FOV oder einer größeren Auflösung gerendert werden

Für einen beliebigen Frame *muss* ihre App mithilfe der Ansichts Transformation, der Projektions Transformation und der viewportauflösung, die vom System bereitgestellt wird, renderingweise erfolgen. Außerdem darf die Anwendung niemals davon ausgehen, dass jeder Renderingparameter oder Sicht Parameter von Frame zu Frame korrigiert bleibt. Module wie Unity verarbeiten all diese Transformationen für Sie in ihren eigenen Kamera Objekten, sodass die physische Bewegung ihrer Benutzer und der Zustand des Systems immer berücksichtigt werden. Wenn Ihre Anwendung eine virtuelle Verschiebung des Benutzers über die Welt ermöglicht (z. b. die Verwendung des Fingerabdrucks auf einem Gamepad), können Sie ein übergeordnetes Rig-Objekt oberhalb der Kamera hinzufügen, das es verschiebt. Dies bewirkt, dass die Kamera den virtuellen und physischen Bewegungs Vorgang des Benutzers widerspiegelt. Wenn die Anwendung die vom System bereitgestellte Ansichts Transformation, Projektions Transformation oder viewportdimension ändert, muss Sie das System durch Aufrufen der entsprechenden [Überschreibungs-API](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose)informieren.

Um die Stabilität Ihres Holographic-Rendering zu verbessern, sollte Ihre APP für Windows jeden Frame den tiefen Puffer bereitstellen, der für das Rendering verwendet wurde. Wenn Ihre APP einen tiefen Puffer bereitstellt, sollte Sie über kohärente tiefen Werte verfügen, wobei die Tiefe in Meter von der Kamera ausgedrückt wird. Dies ermöglicht es dem System, ihre pro-Pixel-Tiefendaten zu verwenden, um Inhalte besser zu stabilisieren, wenn die Kopfzeile des Benutzers etwas von der vorhergesagten Position abweicht. Wenn Sie ihren tiefen Puffer nicht bereitstellen können, können Sie einen Fokuspunkt und normal bereitstellen, indem Sie eine Ebene definieren, die den größten Teil der Inhalte schneidet. Wenn sowohl der tiefen Puffer als auch eine Fokusebene bereitgestellt werden, verwendet das System möglicherweise beides. Insbesondere ist es hilfreich, sowohl den tiefen Puffer als auch einen Schwerpunkt Punkt bereitzustellen, der einen Geschwindigkeitsvektor enthält, wenn Ihre Anwendung holograms anzeigt, die sich in Bewegung befinden.

Ausführliche Informationen zu diesem Thema finden Sie [im Artikel Rendern im DirectX](rendering-in-directx.md) -Artikel.

## <a name="holographic-cameras"></a>Holographic Kameras

Mit Windows Mixed Reality wird das Konzept einer **Holographic Kamera**eingeführt. Holographic Kameras ähneln der herkömmlichen Kamera in 3D-Grafik Texten: Sie definieren sowohl die System externe (Position und Ausrichtung) als auch die systeminternen Kameraeigenschaften. (Z. b. wird das Feld Ansicht verwendet, um eine virtuelle 3D-Szene anzuzeigen.) Im Gegensatz zu herkömmlichen 3D-Kameras ist die Anwendung nicht in der Lage, die Position, die Ausrichtung und die intrinsischen Eigenschaften der Kamera zu steuern. Stattdessen wird die Position und Ausrichtung der Holographic-Kamera implizit durch die Bewegung des Benutzers gesteuert. Die Verschiebung des Benutzers wird über eine Ansichts Transformation per Frame an die Anwendung weitergeleitet. Ebenso werden die systeminternen Eigenschaften der Kamera durch die Matrix des Geräts und das Rahmen der Projektions Transformation definiert.

Im Allgemeinen wird Ihre Anwendung für eine einzelne Stereokamera dargestellt. Eine robuste Renderingschleife unterstützt jedoch mehrere Kameras und unterstützt Mono-und Stereokameras. Das System kann z. b. die Anwendung zum Rendering aus einer alternativen Perspektive auffordern, wenn der Benutzer eine Funktion wie z. b. [Mixed Reality Capture](mixed-reality-capture.md) (MRC) aktiviert, abhängig von der Form des fraglichen-endbeispiels. Anwendungen, die mehrere Kameras unterstützen [können, erhalten diese durch die](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) Wahl der [Art](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) von Kameras, die Sie unterstützen können.

## <a name="volume-rendering"></a>Volumerendering

Beim Rendern von medizinischen MRIs oder Engineering-Volumes in 3D werden häufig [volumerenderingverfahren](volume-rendering.md) verwendet. Diese Techniken können besonders interessant in gemischter Realität sein, in der Benutzer ein solches Volume auf natürliche Weise aus Schlüssel Winkeln anzeigen können, indem Sie einfach den Kopf bewegen.

## <a name="supported-resolutions-on-hololens-1st-gen"></a>Unterstützte Auflösungen auf hololens (1. Gen)
> [!NOTE]
> Es stehen weitere Updates zur Verfügung. [Anzeigen der Update Liste](release-notes-april-2018.md)

* Die aktuelle und die maximal unterstützte Auflösung sind Eigenschaften der [Ansichts Konfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration). Hololens ist standardmäßig auf die maximale Auflösung festgelegt, bei der es sich um 720p (1268x720) handelt.
* Die niedrigste unterstützte Viewportgröße beträgt 50% von 720p, also "360p" (634x360). Bei hololens ist dies ein viewportscalefactor von 0,5.
* Alles, was kleiner als 540p ist, wird aufgrund der visuellen Beeinträchtigung **nicht empfohlen** , kann aber auch verwendet werden, um Bottle-Hals in der Pixel Füll Rate zu identifizieren.

## <a name="supported-resolutions-on-hololens-2"></a>Unterstützte Auflösungen auf hololens 2

> [!NOTE]
> Weitere Anleitungen sind für hololens 2 in [Kürze](news.md)verfügbar.


## <a name="see-also"></a>Weitere Informationen:
* [Hologrammstabilität](hologram-stability.md)
* [Rendern in DirectX](rendering-in-directx.md)
