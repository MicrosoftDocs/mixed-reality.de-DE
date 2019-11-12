---
title: App-Qualitätskriterien
description: In diesem Dokument werden die wichtigsten Faktoren beschrieben, die sich auf die Qualität von Mixed Reality-apps auswirken.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: App-Qualitätskriterien, gemischte Realität, Mixed Reality-App
ms.openlocfilehash: d167e141b536f9247d22e40afefa718ecc399f5a
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926589"
---
# <a name="app-quality-criteria"></a>App-Qualitätskriterien

In diesem Dokument werden die wichtigsten Faktoren beschrieben, die sich auf die Qualität von Mixed Reality-apps auswirken. Für jeden Faktor werden die folgenden Informationen bereitgestellt.
* Übersicht – eine kurze Beschreibung des Qualitäts Faktors und deren Wichtigkeit.
* Geräte Auswirkung: der Typ des Windows Mixed Reality-Geräts ist beeinträchtigt.
* Qualitätskriterien – Auswerten des Qualitäts Faktors.
* So messen Sie –-Methoden, um das Problem zu messen (oder zu erleben).
* Empfehlungen – Zusammenfassung der Ansätze, um eine bessere Benutzer Leistung zu gewährleisten.
* Ressourcen – relevante Entwickler-und Entwurfs Ressourcen, die nützlich sind, um bessere App-Erfahrungen zu erzielen.

## <a name="frame-rate"></a>Bildfrequenz

Die Framerate ist die erste Säule der – Hologramm-Stabilität und des Benutzer Komforts. Die Frame Rate unterhalb der empfohlenen Ziele kann dazu führen, dass holograms Jittery werden, was sich negativ auf die glaub Fähigkeit der Funktionalität auswirkt und möglicherweise Augen Müdigkeit auslöst. Die zielframeworkrate für Ihre Benutzeroberflächen in Windows Mixed Reality-immersiven Headsets ist entweder 60Hz oder 90Hz, je nachdem, welche Windows Mixed Reality-kompatiblen PCs Sie unterstützen möchten. Bei hololens beträgt die zielframeworkrate 60Hz.

### <a name="device-impact"></a>Geräte Auswirkung

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Best  |  Findet |  UN |
--- | --- | ---
| Die APP erfüllt konstant Frames pro Sekunde (fps) für Zielgerät: 60fps on hololens; 90fps auf ultrapcs; und 60fps auf gängigen PCs. | Die APP verfügt über zeitweilig auftretende Frame-Abstürze, die die Kernfunktionen nicht behindern. oder FPS ist konstant niedriger als das gewünschte Ziel, verhindert jedoch die APP-Darstellung. | In der APP tritt im Durchschnitt alle zehn Sekunden eine Dropdown-Rate auf. |

### <a name="how-to-measure"></a>So messen Sie

* Ein Echtzeit-Frameraten Diagramm wird durch das [Windows-Geräte Portal](using-the-windows-device-portal.md#system-performance) unter "System Leistung" bereitgestellt.
* Fügen Sie für das Entwicklungs Debuggen der APP einen framerraten-diagnosecounter hinzu. Einen Beispiel Zählers finden Sie unter Ressourcen.
* Die abfrageate können auf dem Gerät auftreten, während die app ausgeführt wird, indem Sie Ihren Kopf von der Seite zu Seite wechseln. Wenn das – Hologramm unerwartete gezittert-Bewegung anzeigt, ist die niedrige Framerate oder die Stabilitäts Ebene wahrscheinlich die Ursache.

### <a name="recommendations"></a>Empfehlungen

* Fügen Sie am Anfang der Entwicklungsarbeit einen Frameraten-Counter hinzu.
* Änderungen, die eine Ablage in der Framerate verursachen, sollten ausgewertet und als Leistungsfehler entsprechend aufgelöst werden.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Unterlagen

* [Grundlegendes zur Leistung für gemischte Realität](understanding-performance-for-mixed-reality.md)
* [Hologram Stabilität und Framerate](hologram-stability.md#frame-rate)
* [Asset Performance Budget](asset-creation-process.md)
* [Leistungsempfehlungen für Unity](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a>Tools und Tutorials

* [Mrtoolkit, FPS-Counter-Anzeige](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [Mrtoolkit, Shaders](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a>Externe Verweise

* [Unity, optimieren mobiler Anwendungen](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a>Hologram-Stabilität

Stabile Hologramme verbessern die Benutzerfreundlichkeit und Glaubwürdigkeit Ihrer APP und sorgen für einen komfortableren Anzeige Vorgang für den Benutzer. Die Qualität der – Hologramm-Stabilität ist das Ergebnis einer guten App-Entwicklung und der Fähigkeit des Geräts, die Umgebung zu verstehen (nachverfolgen). Obwohl die Framerate die erste Säule der Stabilität ist, können sich andere Faktoren auf die Stabilität auswirken, einschließlich:

* Verwendung der Stabilisierungs Ebene
* Entfernung zu räumlichen Ankern
* Paletten

### <a name="device-impact"></a>Geräte Auswirkung

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Best  |  Findet |  UN |
--- | --- | ---
|  Holograms werden konsistent angezeigt. | Der sekundäre Inhalt zeigt unerwartete Verschiebungen an; oder unerwartete Verschiebungen beeinträchtigen nicht die gesamte App-Leistung. | Primärer Inhalt in Frame zeigt unerwartete Bewegung an. |

### <a name="how-to-measure"></a>So messen Sie

Beim Ausführen des Geräts und Anzeigen der Anzeige:

* Bewegen Sie den Kopf von der Seite zur Seite, wenn die holograms unerwartete Verschiebungen anzeigen, dann ist die niedrige Framerate oder die falsche Ausrichtung der Stabilitäts Ebene auf die Fokusebene die wahrscheinliche Ursache.
* Navigieren Sie in den holograms und in der Umgebung, und suchen Sie nach Verhaltensweisen wie z. b. Schwimmen und Sprung Diese Art von Bewegung wird wahrscheinlich dadurch verursacht, dass das Gerät die Umgebung nicht nachverfolgt, oder die Entfernung zum räumlichen Anker.
* Wenn sich große oder mehrere holograms im Frame befinden, beobachten Sie das – Hologramm-Verhalten in unterschiedlichen Tiefen, während Sie die Kopfzeile von der Seite zu Seite bewegen, wenn die Schattierung auftritt, wird dies wahrscheinlich durch die Stabilisierungs Ebene verursacht.

### <a name="recommendations"></a>Empfehlungen

* Fügen Sie am Anfang der Entwicklungsarbeit einen Frameraten-Counter hinzu.
* Verwenden Sie die Stabilisierungs Ebene.
* Sie sollten immer verankert Hologramme innerhalb von drei Metern Ihres Ankers darstellen.
* Stellen Sie sicher, dass Ihre Umgebung für die ordnungsgemäße Überwachung eingerichtet ist.
* Entwerfen Sie Ihre Benutzeroberflächen, um Hologramme auf verschiedenen Schwerpunkt Ebenen innerhalb des Rahmens zu vermeiden.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Unterlagen

* [Hologram Stabilität und Framerate](hologram-stability.md#frame-rate)
* [Fallstudie mithilfe der Stabilisierungs Ebene](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [Grundlegendes zur Leistung für gemischte Realität](understanding-performance-for-mixed-reality.md)
* [Leistungsempfehlungen für Unity](performance-recommendations-for-unity.md)
* [Raumanker](spatial-anchors.md)
* [Behandeln von nach Verfolgungs Fehlern](coordinate-systems.md#handling-tracking-errors)
* [Stationärer Frame des Verweises](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a>Tools und Tutorials

* [Mr Companion Kit, kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a>Holograms-Position auf realen Oberflächen

Falsche Abweichungen von holograms mit physischen Objekten (wenn Sie in Beziehung zueinander gesetzt werden sollen) sind ein eindeutiger Hinweis auf die nicht-Union von holograms und der realen Welt. Die Genauigkeit der Platzierung sollte in Relation zu den Anforderungen des Szenarios liegen. Beispielsweise kann bei der allgemeinen Oberflächen Platzierung die räumliche Karte verwendet werden, aber eine genauere Platzierung erfordert die Verwendung von Markern und die Kalibrierung.

### <a name="device-impact"></a>Geräte Auswirkung

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Best  |  Findet |  UN |
--- | --- | ---
| Holograms werden an der Oberfläche ausgerichtet, die sich in der Regel im Bereich von Zentimetern bis Zoll Wenn mehr Genauigkeit erforderlich ist, sollte die APP eine effiziente Möglichkeit zur Zusammenarbeit innerhalb der gewünschten App-Spezifikation bereitstellen. | Nicht verfügbar | Die Hologramme werden mit dem physischen Zielobjekt nicht ausgerichtet angezeigt, indem die Oberfläche unterbrochen wird oder die Fläche von der Oberfläche entfernt wird. Wenn die Genauigkeit erforderlich ist, sollten holograms die Näherungs Spezifikation des Szenarios erfüllen. | 

### <a name="how-to-measure"></a>So messen Sie

* Holograms, die auf räumlicher Zuordnung platziert werden, sollten nicht zu einem dramatischen Gleit Komma Wert oberhalb oder unterhalb der Oberfläche erscheinen.
* Holograms, die eine exakte Platzierung erfordern, sollten eine Form von Marker-und Kalibrierungs Systemen aufweisen, die auf die Anforderungen des Szenarios zutreffen.

### <a name="recommendations"></a>Empfehlungen

* Die räumliche Zuordnung eignet sich zum Platzieren von Objekten auf Oberflächen, wenn die Genauigkeit nicht erforderlich ist.
* Verwenden Sie zum Festlegen der optimalen Genauigkeit Marker oder Poster, um die holograms und einen Xbox-Controller (oder einen manuellen Ausrichtungs Mechanismus) für die endgültige Kalibrierung festzulegen.
* Es empfiehlt sich, zusätzliche große Hologramme in logische Teile zu zerlegen und die einzelnen Teile an der Oberfläche auszurichten.
* Nicht ordnungsgemäß festgelegten interpupillary Distance (IPD) können auch die Ausrichtung von holograms beeinflussen. Konfigurieren Sie hololens immer für die IPD des Benutzers.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Unterlagen

* [Platzierung räumlicher Zuordnung](spatial-mapping.md#placement)
* [Raum Scanprozess](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Bewährte Methoden für räumliche Anker](spatial-anchors.md#best-practices)
* [Behandeln von nach Verfolgungs Fehlern](coordinate-systems.md#handling-tracking-errors)
* [Räumliche Abbildung in Unity](spatial-mapping-in-unity.md)
* [Übersicht über die vuforia-Entwicklung](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a>Tools und Tutorials

* [Räumliche Daten 230: räumliche Zuordnung](holograms-230.md)
* [Mr Toolkit, Bibliotheken für räumliche Zuordnung](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [Mr Companion Kit, Poster-Kalibrierungs Beispiel](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [Mr Companion Kit, kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a>Externe Verweise

* [Lowes-Fallstudie, Genauigkeits Ausrichtung](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a>Anzeigen der Komfortzone

App-Entwickler steuern, wohin die Augen der Benutzer konvergiert werden, indem Sie Inhalte und Hologramme in verschiedenen Tiefen platzieren. Benutzer, die hololens durchführen, unterstützen immer 2.0 m, um ein klares Bild zu erhalten, da hololens in einer optischen Entfernung von ungefähr 2,0 m vom Benutzer korrigiert werden. Eine nicht ordnungsgemäße Inhalts Tiefe kann zu einem visuellen Unbehagen oder Müdigkeit führen.

### <a name="device-impact"></a>Geräte Auswirkung

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

<table>
<tr>
<td> Best </td><td><ul>
<li>Platzieren Sie den Inhalt bei 2 m.</li><li>Wenn holograms bei 2 m nicht platziert werden können und Konflikte zwischen Konvergenz und Unterbringung nicht vermieden werden können, liegt die optimale Zone für die – Hologramm-Platzierung zwischen 1,25 m und 5 m.</li><li>In jedem Fall sollten Designer Inhalte strukturieren, um Benutzern die Interaktion von 1 + m zu empfehlen (z. b. Anpassen von Inhalts Größe und Standard Platzierungs Parametern).</li><li>Sofern dies nicht speziell für das Szenario erforderlich ist, sollte eine Clippingebene mit "FadeOut" implementiert werden, beginnend bei 1 Mio.</li><li>In Fällen, in denen eine genauere Betrachtung eines sehr großen holograms erforderlich ist, sollte der Inhalt nicht kleiner als 50 cm sein.</li>
</ul></td>
</tr><tr>
<td> Findet</td><td> Der Inhalt befindet sich in der Anzeige-und Bewegungs Anleitung, aber nicht ordnungsgemäß oder ohne Verwendung der Clippingebene.</td>
</tr><tr>
<td> UN </td><td> Der Inhalt wird zu nah dargestellt (in der Regel &lt;1,25 Mio.), oder &lt;50 cm für stationäre Hologramme, die eine genauere Beobachtung erfordern.</td>
</tr>
</table>

### <a name="how-to-measure"></a>So messen Sie

* Der Inhalt sollte in der Regel 2 Mio., aber nicht größer als 1,25 oder größer als 5 Mio. sein.
* Mit wenigen Ausnahmen sollte die Länge des Clipping-renderingrenderwerts auf. 85 cm festgelegt werden, wobei die faout-Inhalte beginnend bei 1 Mio. liegen. Wenden Sie sich an den Inhalt, und notieren Sie sich die Ausschneide Ebene.
* Stationärer Inhalt sollte nicht kleiner als 50 cm sein.

### <a name="recommendations"></a>Empfehlungen

* Entwerfen Sie den Inhalt für die optimale Anzeige Distanz von 2 m.
* Legen Sie die Entfernungs-renderingdistanz auf 85 cm mit dem faout-Inhalt ab 1 Mio. fest.
* Bei stationären Hologrammen, die näher betrachtet werden müssen, sollte die Clippingebene nicht größer als 30 cm sein, und Fadeout sollte mindestens 10 cm von der Clippingebene ausgehen.

### <a name="resources"></a>Ressourcen

* [Rendering-Entfernung](hologram-stability.md#hologram-render-distances)
* [Fokuspunkt in Unity](focus-point-in-unity.md)
* [Experimentieren mit der Skala](scale.md#experimenting-with-scale)
* [Text, Empfohlene Schriftgröße](typography.md#recommended-font-size)

## <a name="depth-switching"></a>Tiefen Wechsel

Unabhängig von der Anzeige Zone von Komfort Problemen kann es sein, dass der Benutzer häufig oder schnell zwischen Near-und Far-Fokus Objekten (einschließlich holograms und realen Inhalten) wechselt.

### <a name="device-impact"></a>Geräte Auswirkung

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Best  |  Findet |  UN |
--- | --- | ---
|  Eingeschränkter oder natürlicher tiefen Wechsel, der nicht bewirkt, dass sich der Benutzer nicht ganz natürlich neu konzentriert. | Abrupter tiefen Wechsel hierbei handelt es sich um einen Kern, der in die APP-Umgebung integriert wird, oder um einen abrupten Wechsel, der durch unerwartete reale Inhalte verursacht wurde. | Der konsistente tiefen Wechsel oder der abrupte, nicht erforderliche Wechsel oder Kern der APP-Leistung. | 

### <a name="how-to-measure"></a>So messen Sie

* Wenn die APP erfordert, dass der Benutzer den tiefen Fokus konsistent und/oder abrupt ändert, liegt ein Problem mit dem tiefen Wechsel vor.

### <a name="recommendations"></a>Empfehlungen

* Behalten Sie primären Inhalt in einer konsistenten Fokusebene, und stellen Sie sicher, dass die Stabilisierungs Ebene mit der Fokusebene übereinstimmt. Dadurch wird die oomotor-Müdigkeit und unerwartete – Hologramm-Bewegung verringert.

### <a name="resources"></a>Ressourcen

* [Rendering-Entfernung](hologram-stability.md#hologram-render-distances)
* [Fokuspunkt in Unity](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a>Verwendung von räumlichem Sound

In Windows Mixed Reality bietet die Audioengine die Audiowiedergabe-Komponente der gemischten Realität, indem 3D-Sounds mithilfe von Richtungs-, Entfernungs-und Umgebungs Simulationen simuliert werden. Die Verwendung von räumlichem Sound in einer Anwendung ermöglicht Entwicklern das überzeugend Platzieren von Sounds in einem dreidimensionalen Raum (Kugel), der sich alle um den Benutzer dreht. Diese Sounds erscheinen dann so, als wären Sie von echten physischen Objekten oder den Mixed Reality holograms in der Benutzerumgebung. Räumlicher Sound ist ein leistungsfähiges Tool für das Eintauchen, die Barrierefreiheit und den UX-Entwurf in gemischten Reality-Anwendungen.

### <a name="device-impact"></a>Geräte Auswirkung

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Best  |  Findet |  UN |
--- | --- | ---
|  Sound ist logisch räumlich, und die UX verwendet den Sound entsprechend, um die Objekt Ermittlung und das Benutzer Feedback zu unterstützen. Sound ist naturgemäß und relevant für Objekte und wird im gesamten Szenario normalisiert. | Räumliche Audiodaten werden in angemessener Weise verwendet, um Benutzer Feedback und Auffindbarkeit zu unterstützen. | Sound ist nicht erwartungsgemäß räumlich und/oder ungenügender Ton, um Benutzer innerhalb der UX zu unterstützen. Das räumliche audiobild wurde im Entwurf des Szenarios nicht berücksichtigt oder verwendet. | 

### <a name="how-to-measure"></a>So messen Sie

* Im Allgemeinen sollten relevante Sounds aus Ziel-holograms (z. b. "Bark Sound" von Holographic Dog) ausgegeben werden.
* Sound Hinweise sollten in der gesamten Benutzeroberfläche verwendet werden, um dem Benutzer Feedback oder das Bewusstsein von Aktionen außerhalb des Holographic Frame zu unterstützen.

### <a name="recommendations"></a>Empfehlungen

* Verwenden Sie räumliche Audiodaten, um die Objekt Ermittlung und Benutzeroberflächen zu unterstützen.
* Echte Sounds funktionieren besser als synthetisieren oder unnatürlicher Sound.
* Die meisten Sounds sollten räumlich behandelt werden.
* Vermeiden Sie unsichtbare Emitter.
* Vermeiden Sie die räumliche Maskierung.
* Normalisieren Sie alle Sounds.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Unterlagen

* [Raumklang](spatial-sound.md)
* [Raumklangentwurf](spatial-sound-design.md)
* [Raumklang in Unity](spatial-sound-in-unity.md)
* [Fallstudie, räumlicher Sound für holotour](case-study-spatial-sound-design-for-holotour.md)
* [Fallstudie mit räumlichem Sound in roboraid](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a>Tools und Tutorials

* [Mr Spatial 220: räumlicher Sound](holograms-220.md)
* [Mrtoolkit, räumliche Audiodaten](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a>Fokus auf Holographic Frame-Grenzen (FOV)

Gut gestaltete Benutzeroberflächen können den nützlichen Kontext der virtuellen Umgebung erstellen und verwalten, die sich um die Benutzer erstreckt. Das Verringern der Auswirkungen der FOV-Grenzen umfasst einen durchdachten Entwurf der Inhalts Skala und des Kontexts, die Verwendung räumlicher Audiodaten, Leitfäden und die Position des Benutzers. Wenn dies der Fall ist, wird der Benutzer durch die FOV-Grenzen weniger beeinträchtigt, während er eine bequeme App-Erfahrung bietet.

### <a name="device-impact"></a>Geräte Auswirkung

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Best  |  Findet |  UN |
--- | --- | ---
|  Der Benutzer verliert nie den Kontext, und die Anzeige ist bequem. Für große Objekte wird Kontextunterstützung bereitgestellt. Ermittelbarkeits-und Anzeige Anleitungen werden für Objekte außerhalb des Frames bereitgestellt. Im Allgemeinen sind Bewegungs Entwurf und Skalierung der holograms für eine bequeme Anzeige geeignet. | Der Benutzer verliert den Kontext nie, aber in bestimmten Situationen ist möglicherweise eine zusätzliche Nacken Bewegung erforderlich. In einer begrenzten Situation bewirkt die Skalierung, dass holograms entweder den vertikalen oder horizontalen Rahmen unterbrechen, was dazu führt, dass die Bewegung holograms durch einen Hals | Der Benutzer verliert wahrscheinlich den Kontext und/oder eine konsistente Hals Bewegung zum Anzeigen von holograms. Keine Kontext Leit Fäden für große Holographic-Objekte, die das Verschieben von Objekten außerhalb des Frames ohne auffindbarkeits Leit Fäden vereinfachen, oder die Verwendung von hohen holograms erfordert eine reguläre Hals Bewegung zum anzeigen. | 

### <a name="how-to-measure"></a>So messen Sie

* Der Kontext für ein (großes) – Hologramm geht verloren oder wird nicht verstanden, weil er an den Begrenzungen abgeschnitten wurde.
* Der Speicherort von holograms ist schwierig zu finden, da es sich nicht um die Aufmerksamkeit von Regisseuren oder Inhalten handelt, die sich schnell in den Holographic-Frame bewegen.
* Das Szenario erfordert reguläre und wiederkehrende aufruhenden aufruhenden Bewegung, um ein – Hologramm vollständig zu sehen

### <a name="recommendations"></a>Empfehlungen

* Starten Sie die Arbeit mit kleinen Objekten, die für den FOV geeignet sind, und wechseln Sie dann mit visuellen Cues in größere Versionen.
* Verwenden Sie die Directors für räumliche Audiodaten und Aufmerksamkeit, um dem Benutzer zu helfen, Inhalte außerhalb des FOV zu finden.
* Vermeiden Sie so weit wie möglich Hologramme, die den FOV vertikal abschneiden.
* Stellen Sie dem Benutzer einen in-App-Leitfaden für den optimalen Anzeige Speicherort zur Verfügung.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Unterlagen

* [Holografischer Rahmen](holographic-frame.md)
* [Fallstudie, Entwicklung von holostudio-UI und Interaktions Entwurf](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [Skalieren von Objekten und Umgebungen](scale.md)
* [Cursor, visuelle Hinweise](cursors.md#visual-cues)

#### <a name="external-references"></a>Externe Verweise

* [Viel ADO zum FOV](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a>Inhalt reagiert auf Benutzer Position

Holograms sollten auf ungefähr die gleiche Weise wie "echte" Objekte auf die Benutzer Position reagieren. Ein wichtiger Entwurfs Aspekt sind Benutzeroberflächen Elemente, die nicht unbedingt annehmen können, dass die Position eines Benutzers stationär ist und sich an die Bewegung des Benutzers anpasst. Das Entwerfen einer APP, die sich ordnungsgemäß an die Benutzer Position anpasst, führt zu einer besseren Benutzerfreundlichkeit und erleichtert die Verwendung.

### <a name="device-impact"></a>Geräte Auswirkung

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

<table>
<tr>
<td> Best </td><td> Der Inhalt und die Benutzeroberfläche werden an Benutzer Positionen angepasst, damit Benutzer im Bereich der erwarteten Benutzer Bewegung natürlich mit Inhalten interagieren können.</td>
</tr><tr>
<td> Findet </td><td> Die Benutzeroberfläche passt sich an die Benutzer Position an, kann jedoch die Ansicht von Schlüssel Inhalten behindern, die den Benutzer zum Anpassen Ihrer Position benötigen.</td>
</tr><tr>
<td> UN </td><td><ol>
<li>Benutzeroberflächen Elemente gehen verloren oder sind während der Bewegung gesperrt, sodass der Benutzer nicht auf natürliche Weise zu den Steuerelementen zurückkehrt.</li><li>Elemente der Benutzeroberfläche beschränken die Ansicht von primärem Inhalt.</li><li>Die UI-Verschiebung ist nicht für die Anzeige von Distance und Impulsen vor allem mit <a href="billboarding-and-tag-along.md">tagbasierten</a> Benutzeroberflächen Elementen optimiert.</li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a>So messen Sie

* Alle Messungen sollten innerhalb eines angemessenen Umfangs des Szenarios durchgeführt werden. Während die Benutzer Bewegung variieren kann, versuchen Sie nicht, die APP mit extremer Benutzer Bewegung zu täuschen.
* Für Elemente der Benutzeroberfläche sollten relevante Steuerelemente unabhängig von der Benutzer Bewegung verfügbar sein. Wenn der Benutzer z. b. eine 3D-Karte mit Zoom anzeigen und durchläuft, sollte das Zoom Steuerelement dem Benutzer unabhängig von der Position sofort verfügbar sein.

### <a name="recommendations"></a>Empfehlungen

* Der Benutzer ist die Kamera und steuert die Bewegung. Das können Sie steuern.
* Ziehen Sie die Abrechnung für Text-und menuingsysteme in Erwägung, die andernfalls in der Welt gesperrt oder verdeckt werden, wenn sich ein Benutzer bewegen würde.
* Verwenden Sie tagzusammen für Inhalte, die dem Benutzer folgen müssen, während der Benutzer weiterhin sehen kann, was vor ihm steht.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Unterlagen

* [Interaktions Entwurf](hologram.md)
* [Farbe, Licht und Material](color,-light-and-materials.md)
* [Billboarding und Tag-along](billboarding-and-tag-along.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Selbst Bewegung und Benutzer Bewegung](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a>Tools und Tutorials

* [Mr-Eingabe 210: Blick](holograms-210.md)

## <a name="input-interaction-clarity"></a>Klarheit der Eingabe Interaktion

Die Übersichtlichkeit der Eingabe Interaktion ist wichtig für die Benutzerfreundlichkeit einer APP und umfasst Eingabe Konsistenz, genehmigende Zulässigkeit, Auffindbarkeit von Interaktions Methoden. Der Benutzer sollte in der Lage sein, plattformweite allgemeine Interaktionen ohne Relearning zu verwenden. Wenn die APP benutzerdefinierte Eingaben hat, sollte Sie eindeutig kommuniziert und demonstriert werden.

### <a name="device-impact"></a>Geräte Auswirkung

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Best  |  Findet |  UN |
--- | --- | ---
|  Eingabe Interaktions Methoden sind mit der von Windows Mixed Reality bereitgestellten [Anleitung](interaction-fundamentals.md)konsistent. Jede benutzerdefinierte Eingabe sollte nicht mit Standard Eingaben redundant sein (sondern eher die Standard Interaktion verwenden), und Sie muss für den Benutzer eindeutig kommuniziert und demonstriert werden. | Ähnlich wie die beste, aber benutzerdefinierte Eingaben sind bei Standardeingabe Methoden redundant. Der Benutzer kann das Ziel und den Fortschritt auch über die App-Benutzer Leistung erreichen. | Das Verständnis der Eingabemethode oder der Schaltflächen Zuordnung ist schwierig. Die Eingabe ist stark angepasst, bietet keine Unterstützung für Standard Eingaben, keine Anweisungen, oder es werden wahrscheinlich Ermüdungs-und komfortprobleme verursacht. | 

### <a name="how-to-measure"></a>So messen Sie

* Die APP verwendet konsistente [Standardeingabe Methoden.](interaction-fundamentals.md)
* Wenn die APP über benutzerdefinierte Eingaben verfügt, wird Sie eindeutig übermittelt:
* Erstmaligen Testlauf
* Einführungs Bildschirme
* QuickInfos
* Hand Coach
* Hilfe Abschnitt
* Voice-over

### <a name="recommendations"></a>Empfehlungen

* Verwenden Sie nach Möglichkeit immer Standardeingabe Methoden.
* Stellen Sie Demonstrationen, Tutorials und Quick Infos für nicht standardmäßige Eingabemethoden bereit.
* Verwenden Sie in der gesamten App ein konsistentes Interaktionsmodell.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Unterlagen

* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Interactable-Objekte](interactable-object.md)
* [Anvisieren mit dem Kopf und Verweilen](gaze-and-dwell.md)
* [Cursor](cursors.md)
* [Komfort und Blick](comfort.md#gaze-direction)
* [Spracheingabe](voice-input.md)
* [Motion-Controller](motion-controllers.md)
* [Leitfaden für Eingabeportierung für Unity](input-porting-guide-for-unity.md)
* [Tastatureingabe in Unity](keyboard-input-in-unity.md)
* [Anvisieren in Unity](gaze-in-unity.md)
* [Gesten und Motion-Controller in Unity](gestures-and-motion-controllers-in-unity.md)
* [Spracheingabe in Unity](voice-input-in-unity.md)
* [Tastatur-, Maus- und Controllereingaben in DirectX](keyboard,-mouse,-and-controller-input-in-directx.md)
* [Anvisieren mit dem Kopf und mit den Augen in DirectX](gaze-in-directx.md)
* [Hände und Motion-Controller in DirectX](hands-and-motion-controllers-in-directx.md)
* [Spracheingabe in DirectX](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a>Tools und Tutorials

* [Fallstudie: die Verfolgung von mehr persönlichen Computing](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [Umwandlungs Studie: Entwicklung von holostudio-UI-und Interaktions Entwürfen](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [Beispiel-App: periodische Tabelle der Elemente](periodic-table-of-the-elements.md)
* [Beispiel-App: Mond Modul](lunar-module.md)
* [Mr-Eingabe 210: Blick](holograms-210.md)
* [Mr-Eingabe 211: Gesten](holograms-211.md)
* [Mr-Eingabe 212: Stimme](holograms-212.md)

## <a name="interactable-objects"></a>Interactable-Objekte

Eine Schaltfläche ist lange eine Metapher, die zum Auslösen eines Ereignisses in der 2D-abstrakten Welt verwendet wird. In der dreidimensionalen Mixed Reality-Welt müssen wir nicht mehr auf diese Abstraktions Welt beschränkt werden. Dabei kann es sich um ein Objekt handeln, das ein Objekt ist, das ein Ereignis auslöst. Ein Objekt, das sich in der Tabelle befindet, kann als beliebiger von einem Kaffeebecher in der Tabelle dargestellt werden. Unabhängig vom Formular sollte der Benutzer durch visuelle und Audiohinweise eindeutig erkennbar sein.

### <a name="device-impact"></a>Geräte Auswirkung

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Best  |  Findet |  UN |
--- | --- | ---
|  Unabhängig von der Form sind Interaktionen-Objekte durch visuelle und Audiohinweise in drei Zuständen erkennbar: im Leerlauf, gezielt und ausgewählt. "Wie Sie sehen, ist es klar und in der gesamten gesamten Darstellung verwendet. Objekte werden skaliert und verteilt, um eine fehlerfreie Zielversion zu ermöglichen. | Der Benutzer kann das Objekt als Interaktionen durch Audiomaterial oder visuelles Feedback erkennen und das Objekt auf das Objekt ausrichten und aktivieren. | Wenn keine visuellen oder Audiohinweise angezeigt werden, kann der Benutzer ein Objekt mit Interaktionen nicht erkennen. Interaktionen sind aufgrund der Objekt Skala oder der Entfernung zwischen Objekten fehleranfällig. | 

### <a name="how-to-measure"></a>So messen Sie

* Interactable-Objekte sind als "interactable" erkennbar. einschließen von Schaltflächen, Menüs und App-spezifischem Inhalt. Als Faustregel gilt, dass ein visueller und audiohinweis vorhanden sein sollte, wenn Sie auf Objekte mit Interaktionen abzielen.

### <a name="recommendations"></a>Empfehlungen

* Verwenden Sie visuelles und Audiofeedback für Interaktionen.
* Visuelles Feedback sollte für jeden Eingabe Status unterschieden werden (im Leerlauf, gezielt, ausgewählt).
* Interactable-Objekte sollten skaliert und für fehlerfreie Zielgruppen vorgesehen werden.
* Gruppierte Interaktionen-Objekte (z. b. eine Menüleiste oder Liste) sollten über den richtigen Abstand zum Ziel verfügen.
* Schaltflächen und Menüs, die den Voice-Befehl unterstützen, sollten Text Bezeichnungen für das Befehls Schlüsselwort bereitstellen ("siehe IT, sagen Sie")

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Unterlagen

* [Interaktionsfähiges Objekt](interactable-object.md)
* [Text in Unity](text-in-unity.md)
* [Begrenzungsrahmen und App-Leiste](app-bar-and-bounding-box.md)
* [Spracheingabe](voice-input.md)

#### <a name="tools-and-tutorials"></a>Tools und Tutorials

* [Mixed Reality Toolkit-UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a>Raum Überprüfung

Apps, die räumliche Daten für die Zuordnung benötigen, benötigen das Gerät, um diese Daten automatisch über einen Zeitraum und Sitzungs übergreifend zu erfassen, da der Benutzer seine Umgebung mit dem aktiven Gerät untersucht. Die Vollständigkeit und Qualität dieser Daten hängt von einer Reihe von Faktoren ab, z. b. vom Umfang der durchgeführten Untersuchung, von der seit der Durchsuchung übergebenen Zeit und davon, ob Objekte wie z. b. Möbel und Türen verschoben wurden, seit das Gerät den Bereich überprüft hat. Viele apps analysieren die räumlichen Zuordnungs Daten zu Beginn der Benutzer Darstellung, um zu beurteilen, ob der Benutzer zusätzliche Schritte ausführen muss, um die Vollständigkeit und Qualität der räumlichen Karte zu verbessern. Wenn der Benutzer die Umgebung scannen muss, sollten Sie während der Überprüfung eine klare Anleitung bereitstellen.

### <a name="device-impact"></a>Geräte Auswirkung

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Best  |  Findet |  UN |
--- | --- | ---
|  Die Visualisierung des räumlichen Netzes weist auf die Überprüfung von Benutzern hin. Der Benutzer weiß eindeutig, was zu tun ist und wann die Überprüfung gestartet und beendet wird. | Die Visualisierung des räumlichen Netzes wird bereitgestellt, aber der Benutzer weiß möglicherweise nicht, was zu tun ist, und es werden keine Fortschrittsinformationen bereitgestellt. | Keine Visualisierung von Mesh. Für den Benutzer werden keine Leitfäden bezüglich des abzurufenden oder zum Starten/Beenden der Überprüfung bereitgestellt. |

### <a name="how-to-measure"></a>So messen Sie

* Während eines erforderlichen Raum Scans werden visuelle und audioanleitungen bereitgestellt, die angeben, wo gesucht werden soll und wann das Scannen gestartet und beendet werden soll.

### <a name="recommendations"></a>Empfehlungen

* Geben Sie an, wie viel des gesamten Volumes in der Benutzerumgebung in der Umgebung enthalten sein muss.
* Kommunizieren, wenn die Überprüfung gestartet und beendet wird, z. b. eine Statusanzeige.
* Verwenden Sie während des Scanvorgangs eine Visualisierung des Netzes.
* Stellen Sie visuelle und Audiohinweise bereit, um den Benutzer zu unterstützen, um den Raum zu sehen und zu verschieben.
* Informieren Sie den Benutzer, wohin Sie die Daten verbessern möchten. In vielen Fällen kann es am besten sein, den Benutzern mitzuteilen, was Sie tun müssen (z. b. die Obergrenze, das Aussehen hinter den Möbeln), um die erforderliche Scanqualität zu erhalten.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Unterlagen

* [Raumabtastvisualisierung](room-scan-visualization.md)
* [Fallstudie: Erweitern der Funktionen für räumliche Zuordnung von hololens](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Fallstudie: räumliches Sound Design für holotour](case-study-spatial-sound-design-for-holotour.md)
* [Fallstudie: Erstellen eines immersiven Erlebnisses in Fragmenten](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a>Tools und Tutorials

* [Mixed Reality Toolkit-UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a>Direktionale Indikatoren

In einer Mixed Reality-App kann es sein, dass sich Inhalte außerhalb des Felds befinden oder durch reale Objekte verdeckt werden. Eine gut entworfene App vereinfacht das Auffinden nicht sichtbarer Inhalte durch den Benutzer. Direktionale Indikatoren warnen einen Benutzer für wichtige Inhalte und bieten Anleitungen für den Inhalt in Bezug auf die Position des Benutzers an. Anleitungen für nicht sichtbare Inhalte können als audioemitter, direktionale Pfeile oder direkte visuelle Hinweise genutzt werden.

### <a name="device-impact"></a>Geräte Auswirkung

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Best  |  Findet |  UN |
--- | --- | ---
|  Visuelle und Audiohinweise leiten den Benutzer direkt an relevante Inhalte außerhalb des Felds der Ansicht. | Ein Pfeil oder ein Indikator, der den Benutzer in der allgemeinen Richtung des Inhalts zeigt. | Relevante Inhalte sind nicht in der Ansicht enthalten, und dem Benutzer wird ein schlechter oder kein Orts Leit Faden bereitgestellt. | 

### <a name="how-to-measure"></a>So messen Sie

* Relevante Inhalte außerhalb des Benutzer Felds können durch visuelle und/oder Audiohinweise erkannt werden.

### <a name="recommendations"></a>Empfehlungen

* Wenn relevante Inhalte außerhalb des Benutzer Felds liegen, verwenden Sie richtungsindikatoren und Audiohinweise, um den Benutzer zum Inhalt zu leiten. In vielen Fällen wird ein direkter visueller Leitfaden als direktionale Pfeile bevorzugt.
* Direktionale Indikatoren sollten nicht in den Cursor integriert werden.

### <a name="resources"></a>Ressourcen

* [Holografischer Rahmen](holographic-frame.md)

## <a name="data-loading"></a>Laden von Daten

Ein Statussteuerelement gibt dem Benutzer eine Rückmeldung, dass ein Vorgang mit langer Laufzeit ausgeführt wird. Dies kann bedeuten, dass der Benutzer nicht mit der APP interagieren kann, wenn die Statusanzeige sichtbar ist, und auch angeben kann, wie lange die Wartezeit dauern kann.

### <a name="device-impact"></a>Geräte Auswirkung

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Best  |  Findet |  UN |
--- | --- | ---
|  Animierter visueller Indikator in Form einer Statusanzeige oder eines Rings, der den Fortschritt beim Laden oder Verarbeiten von Daten anzeigt. Der visuelle Indikator gibt eine Anleitung dazu, wie lange der Warte Vorgang sein könnte. | Der Benutzer wird darüber informiert, dass das Laden von Daten ausgeführt wird. es gibt jedoch keinen Hinweis darauf, wie lange der Warte Vorgang sein könnte. | Das Laden von Daten oder das Verarbeiten von Indikatoren für den Task dauert länger als 5 Sekunden. |

### <a name="how-to-measure"></a>So messen Sie

* Vergewissern Sie sich beim Laden von Daten, dass es für mehr als 5 Sekunden keinen leeren Zustand gibt.

### <a name="recommendations"></a>Empfehlungen

* Stellen Sie eine Animation zum Laden von Daten bereit, die den Fortschritt in jeder Situation anzeigt, in der der Benutzer diese APP möglicherweise als angehalten oder abstürzt Eine vernünftige Faustregel ist jede "Lade Aktivität", die mehr als 5 Sekunden in Anspruch nehmen kann.

### <a name="resources"></a>Ressourcen

* [Anzeigen des Fortschritts](progress.md)
