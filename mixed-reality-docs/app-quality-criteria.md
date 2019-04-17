---
title: Qualitätskriterien für die App
description: Dieses Dokument beschreibt die obersten Faktoren, die Auswirkungen auf die Qualität von mixed Reality-apps.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: App-Qualitätskriterien, mixed Reality, mixed Reality-app
ms.openlocfilehash: 8070a434be462a636b314527c59f299ca77fb6d4
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595481"
---
# <a name="app-quality-criteria"></a>Qualitätskriterien für die App

Dieses Dokument beschreibt die obersten Faktoren, die Auswirkungen auf die Qualität von mixed Reality-apps. Für die einzelnen Faktoren ist die folgenden Informationen bereitgestellt.
* Übersicht – eine kurze Beschreibung der Qualitätsfaktor und warum es wichtig ist.
* Gerät Auswirkungen, – welche Art von Fenster Mixed Reality-Gerät betroffen ist.
* Qualitätskriterien – wie den Qualitätsfaktor ausgewertet.
* So messen – Methoden, um das Problem zu messen (oder auftreten).
* Empfehlungen – Zusammenfassung der Ansätze für eine bessere Benutzeroberfläche bereitzustellen.
* Ressourcen – relevanten Entwickler- und Design-Ressourcen, die zum Erstellen besserer Benutzeroberflächen nützlich sind.

## <a name="frame-rate"></a>Bildfrequenz

Framerate ist die erste Säule des – Hologramm Stabilität Komfort für Benutzer. Framerate oberhalb der empfohlenen Ziele kann dazu führen, dass Hologramme ganz nervös, negative Auswirkungen auf die Believability der Benutzeroberfläche und führte potenziell zu Eye Ermüdung angezeigt werden. 60Hz oder 90Hz, je nachdem welche Windows Mixed Reality kompatibel PCs Sie unterstützen möchten, wird die Ziel-Framerate für Ihre Umgebung für immersive Headsets Windows Mixed Reality sein. Für HoloLens ist die Ziel-Framerate 60Hz.

### <a name="device-impact"></a>Auswirkungen des Geräts

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Am besten  |  Erfüllt |  Fehler |
--- | --- | ---
| Die app erfüllt konsistent Frames pro Sekunde (FPS)-Ziel für Zielgerät: 60fps im HoloLens; 90 f/s auf Ultra-PCs und 60fps auf gängige PCs. | Die app verfügt über periodische Frame löscht die Core-Umgebung nicht zu beeinträchtigen, oder f/s ist konsistent niedriger als der gewünschte Ziel, aber durch die app-Funktionalität nicht beeinträchtigt werden kann. | Die app hat einen Abfall der Framerate, die im Durchschnitt alle zehn Sekunden oder weniger. |

### <a name="how-to-measure"></a>Gewusst wie: messen

* Ein in Echtzeit Frame Rate Diagramm erfolgt über von der [Windows Device Portal](using-the-windows-device-portal.md#system-performance) unter "System Performance".
* Fügen Sie für die Entwicklung zu debuggen einen Frame Rate-Diagnose-Zähler der app hinzu. Finden Sie Ressourcen für einen Beispiel-Indikator.
* Frame Rate löscht können im Gerät auftreten können, während die app ausgeführt wird, durch das Verschieben der Kopf von rechts. Wenn die Hologramm unerwartete ganz nervös Bewegung angezeigt wird, dann niedrigen Framerate oder die Stabilität-Ebene ist wahrscheinlich die Ursache.

### <a name="recommendations"></a>Empfehlungen

* Fügen Sie einen Frame Rate Zähler am Anfang der Entwicklungsarbeit hinzu.
* Änderungen, die einen Abfall der Framerate entstehen, ausgewertet und als leistungsfehler entsprechend behoben.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Dokumentation

* [Grundlegendes zur Leistung für Mixed Reality](understanding-performance-for-mixed-reality.md)
* [– Hologramm Stabilität und der Bildrate](hologram-stability.md#frame-rate)
* [Asset-Leistungsbudget](asset-creation-process.md)
* [Empfehlungen zur Leistung für Unity](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a>Tools und tutorials

* [MRToolkit, f/s-Leistungsindikator-Anzeige](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [MRToolkit, Shadern](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a>Externe Verweise

* [Unity und Optimieren von mobilen Anwendungen](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a>– Hologramm Stabilität

Stabile Hologramme werden erhöht die benutzerfreundlichkeit und Believability Ihrer App, und erstellen ein angenehmer Anzeigefunktionen für den Benutzer. Die Qualität der – Hologramm Stabilität ist das Ergebnis gute app-Entwicklung und die Fähigkeit des Geräts (Track) zu ihrer Umgebung. Während der Framerate für die erste Säule des Stabilität ist, können andere Faktoren, einschließlich Stabilität auswirken:

* Verwenden der Stabilisierung Ebene
* Abstand und räumliche Anker
* Nachverfolgung

### <a name="device-impact"></a>Auswirkungen des Geräts

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Am besten  |  Erfüllt |  Fehler |
--- | --- | ---
|  Hologramme werden konsistent stabile angezeigt. | Sekundärer Inhalt weist unerwartete Bewegung; oder unerwartete Bewegung allgemeine app-Benutzeroberfläche nicht behindern. | Hauptinhalt in Rahmen weist unerwartete verschieben. |

### <a name="how-to-measure"></a>Gewusst wie: messen

Während das Gerät steht, geteert und die zur Anzeige von:

* Verschieben Kopf von rechts, die Hologramme unerwartete Bewegung angezeigt dann niedrigen Framerate oder eine fehlerhafte Ausrichtung der Stabilität Ebene auf dieser Ebene wird wahrscheinlich dadurch verursacht.
* Verschieben Sie die Hologramme und die Umgebung, suchen Sie nach Verhaltensweisen wie verantwortlichkeitsbereichs und Jumpiness. Diese Art von Motion wird wahrscheinlich durch das Gerät nicht die Umgebung oder die Entfernung verfolgt, auf den spatial Anker verursacht.
* Bei einer großen oder mehrere Hologramme befinden sich in den Frame, – Hologramm-Verhalten in verschiedenen Ebenen zu beobachten, während Ihre Head Position von rechts, verschieben, wenn Shakiness angezeigt wird, dies ist wahrscheinlich der Stabilisierung Ebene zurückzuführen.

### <a name="recomendations"></a>Recomendations

* Fügen Sie einen Frame Rate Zähler am Anfang der Entwicklungsarbeit hinzu.
* Verwenden Sie die Stabilisierung-Ebene.
* Rendern Sie immer verankerten Hologramme innerhalb von 3 Messgeräten, die von ihren Anker.
* Stellen Sie sicher, dass Ihre Umgebung eingerichtet, für die ordnungsgemäße Überwachung ist.
* Entwerfen Sie Ihrer Erfahrung Hologramme auf verschiedenen als zentrales Tiefenebenen innerhalb des Rahmens zu vermeiden.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Dokumentation

* [– Hologramm Stabilität und der Bildrate](hologram-stability.md#frame-rate)
* [Fallstudie, die mit der Stabilisierung-Ebene](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [Grundlegendes zur Leistung für Mixed Reality](understanding-performance-for-mixed-reality.md)
* [Empfehlungen zur Leistung für Unity](performance-recommendations-for-unity.md)
* [Räumliche Anker](spatial-anchors.md)
* [Behandeln von Fehlern der nachverfolgung](coordinate-systems.md#handling-tracking-errors)
* [Feststehende Verweisrahmen](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a>Tools und tutorials

* [MR Companion Kit Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a>Hologramme Position auf echten Oberflächen

Fehler im Alignment von Hologramme mit physischer Objekte (sofern aneinander platziert werden soll) ist ein eindeutiger Hinweis darauf, der nicht-Union-Hologramme und reale. Genauigkeit der Platzierung sollte relativ zu den Anforderungen des Szenarios werden. z. B. allgemeine Oberfläche Platzierung räumliche Zuordnung verwenden kann, aber eine präzisere Platzierung benötigen einige mit markern und Kalibrierung.

### <a name="device-impact"></a>Auswirkungen des Geräts

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Am besten  |  Erfüllt |  Fehler |
--- | --- | ---
| Hologramme Ausrichten der Entwurfsoberfläche in der Regel in der Zentimeter Zoll-Bereich. Wenn eine größere Genauigkeit erforderlich ist, sollte die app eine effiziente Möglichkeit für die Zusammenarbeit in der Spezifikation für die gewünschte app bereitstellen. | Nicht verfügbar | Die Hologramme angezeigt mit der physischen Zielobjekt nicht ausgerichtete durch Unterbrechen der Surface-Ebene oder auf von der Oberfläche "float" angezeigt werden. Wenn Genauigkeit erforderlich ist, sollte die Hologramme die NEAR-Spezifikation des Szenarios erfüllen. | 

### <a name="how-to-measure"></a>Gewusst wie: messen

* Hologramme, die auf den spatial Karte platziert werden sollten nicht auf deutlich oberhalb oder unterhalb der Oberfläche "float" angezeigt.
* Hologramme, die korrekte Platzierung erfordern sollte es sich um eine Form, Marker und Kalibrierung System verfügen, die auf das Szenario für die Anforderung wird.

### <a name="recommendations"></a>Empfehlungen

* Räumliche Zuordnung ist nützlich für das Platzieren von Objekten auf Oberflächen, wenn die Genauigkeit nicht erforderlich ist.
* Verwenden Sie für die beste Genauigkeit Marker oder Poster der Hologramme und eine Xbox-Controller (oder einen Mechanismus für die manuelle Ausrichtung) fest für die endgültige Kalibrierung.
* Berücksichtigen Sie sehr große Hologramme in logische Teile aufteilen und Ausrichtung der einzelnen Teile der Oberfläche.
* Nicht ordnungsgemäß auswirken festgelegten interpupilary Entfernung (Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor) kann auch – Hologramm Ausrichtung. Konfigurieren Sie immer die HoloLens, Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor des Benutzers.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Dokumentation

* [Räumliche Zuordnung-Platzierung](spatial-mapping.md#placement)
* [Raum Scanvorgang](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Bewährte Methoden von räumlichen Anker](spatial-anchors.md#best-practices)
* [Behandeln von Fehlern der nachverfolgung](coordinate-systems.md#handling-tracking-errors)
* [Räumliche Zuordnung in Unity](spatial-mapping-in-unity.md)
* [Übersicht über die Entwicklung von Vuforia](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a>Tools und tutorials

* [MR Spatial 230: Räumliche Zuordnung](holograms-230.md)
* [Räumliche Zuordnung Bibliotheken MR Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [MR Companion Kit Poster Kalibrierung-Beispiel](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [MR Companion Kit Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a>Externe Verweise

* [Fallstudie Lowes Genauigkeit Ausrichtung](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a>Anzeigen der Zone der Komfort

App-Entwickler-Steuerelement, in denen Benutzer Augen konvergieren, durch die Platzierung von Inhalt und Hologramme in verschiedenen Ebenen. Benutzern steht, geteert HoloLens werden immer berücksichtigen, auf 2.0m zu verwalten, ein klares Bild da HoloLens angezeigt sind in einer optischen Abstand ungefähr 2.0m von der Benutzer fest. Ungültige Content Tiefe kann visual angefasst oder Ermüdung führen.

### <a name="device-impact"></a>Auswirkungen des Geräts

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

<table>
<tr>
<td> Am besten </td><td><ul>
<li>Legen Sie Inhalte auf 2m ein.</li><li>Wenn Hologramme können nicht auf 2m platziert werden und Konflikte zwischen Konvergenz und beeinflusst nicht vermieden werden, liegt die optimale Zone für die Platzierung von – Hologramm 1,25 m "und" 5 Min.</li><li>In jedem Fall sollte Designer Struktur Inhalt empfehlen Benutzern die Interaktion von 1 + m entfernt (z. B. Inhaltsgröße anpassen und die Positionierungsparameter des Standard).</li><li>Es sei denn, die explizit nicht von dem Szenario erforderlich ist, sollte eine Clippingebene implementieren mit Fadeout beginnend mit 1 Million.</li><li>In Fällen, in denen genauer Beobachtung von einem bewegungslos Hologramm erforderlich ist, sollte der Inhalt nicht als 50 cm sein.</li>
</ul></td>
</tr><tr>
<td> Erfüllt</td><td> Der Inhalt ist in der Anleitung anzeigen und während der Übertragung, aber nicht ordnungsgemäße sprachnutzung oder keine Verwendung von den Clipping-Ebene.</td>
</tr><tr>
<td> Fehler </td><td> Der Inhalt zu nahe dargestellt wird (in der Regel &lt;1,25 m oder &lt;50 cm für stationäre Hologramme genauer Beobachtung erfordern.)</td>
</tr>
</table>

### <a name="how-to-measure"></a>Gewusst wie: messen

* Der Inhalt muss in der Regel 2 m entfernt, jedoch nicht näher als 1,25 oder weiter als 5 Min. entsprechen.
* Mit wenigen Ausnahmen sollte die HoloLens Clipping Render-Entfernung auf .85CM mit Fadeout von Inhalten, die beginnend bei 1 Mio. festgelegt werden. Ansatz des Inhalts, und notieren Sie den Freistellungseffekt-Ebene.
* Stationär Inhalt darf nicht als 50 cm entfernt sein.

### <a name="recommendations"></a>Empfehlungen

* Entwerfen Sie Inhalte für die optimale Anzeige Entfernung 2 m ein.
* Legen Sie die Entfernung des Clipping gerendert, auf 85cm mit Fadeout von Inhalten, die beginnend bei 1 Million.
* Für stationäre Hologramme, die näher anzeigen, sollten die Clipping-Ebene nicht näher als 30cm und Fadeout sollte mindestens 10cm Weg von den Clipping-Ebene beginnen.

### <a name="resources"></a>Ressourcen

* [Rendern von Abstand](hologram-stability.md#hologram-render-distances)
* [Fokuspunkt in Unity](focus-point-in-unity.md)
* [Experimentieren mit der Skalierung](scale.md#experimenting-with-scale)
* [Text Schriftgrad empfohlen](typography.md#recommended-font-size)

## <a name="depth-switching"></a>Tiefe wechseln

Unabhängig von der Zone der Komfort Probleme anzeigen fordert für den Benutzer häufig oder schnell wechseln, in der Nähe, und viel als zentrales Objekte (einschließlich Hologramme und den tatsächlichen Inhalt) oculomotor Fatigue und allgemeine angefasst führen können.

### <a name="device-impact"></a>Auswirkungen des Geräts

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Am besten  |  Erfüllt |  Fehler |
--- | --- | ---
|  Eingeschränkte oder natürliche Tiefe wechseln, die nicht dazu führen, dass den Benutzer, neuer Nachklang Fokus. | Switch abrupten Tiefe, dies ist der Kern und in der app-Erfahrung konzipiert, oder abrupten Tiefe-Switch, der von unerwarteten realen Inhalt verursacht wird. | Einheitliche Tiefe Switch oder abrupten Tiefe wechseln, die nicht erforderlich ist oder Core, um die app-Funktionalität. | 

### <a name="how-to-measure"></a>Gewusst wie: messen

* Wenn den Benutzer konsistent und/oder plötzlich Tiefe ändern Sie den Fokus von der app erforderlich sind, ist Tiefe Problem wechseln.

### <a name="recommendations"></a>Empfehlungen

* Behalten Sie Hauptinhalt an einer konsistenten als zentrales Ebene bei, und stellen Sie sicher, dass die Stabilisierung-Ebene auf dieser Ebene entspricht. Dies lässt sich durch oculomotor Fatigue und unerwartete – Hologramm Bewegung beheben.

### <a name="resources"></a>Ressourcen

* [Rendern von Abstand](hologram-stability.md#hologram-render-distances)
* [Fokuspunkt in Unity](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a>Von räumlichen Sounds

In Windows Mixed Reality bietet das Audiomodul der sehen die mixed Reality-Erfahrung durch Simulieren von 3D sound mithilfe von environmental Simulationen, Entfernung und Richtung. Verwenden von räumlichen Sound in einer Anwendung kann Entwickler convincingly Platzieren von Sounds in einem 3 dimensionalen Raum (Kugel) für den Benutzer. Diese Sounds werden dann erscheinen, als ob sie von echten physischen Objekten oder der mixed Reality-Hologramme in der benutzerumgebung gestellt würden. Räumliche Sound ist ein leistungsstarkes Tool zum Immersion, Barrierefreiheit und UX-Entwurf in mixed Reality-Anwendungen.

### <a name="device-impact"></a>Auswirkungen des Geräts

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Am besten  |  Erfüllt |  Fehler |
--- | --- | ---
|  Sound wird logisch spatialized und die UX entsprechend Sound verwendet, zur Unterstützung bei der Objekt-Ermittlung und Benutzerfeedback. Sound ist die natürliche und auf Objekte relevant und eine normalisierte, über das Szenario. | Räumliche Audio ist entsprechend für Believability verwendet jedoch fehlen als Mittel, um Feedback von Benutzern und die Auffindbarkeit zu unterstützen. | Sound wird nicht wie erwartet, spatialized und/oder fehlende Sound bei der Benutzer in der UX. Räumliche Audio wurde oder nicht berücksichtigt, die in den Entwurf des Szenarios verwendet. | 

### <a name="how-to-measure"></a>Gewusst wie: messen

* Im Allgemeinen sollte die relevanten Sounds von Ziel-Hologramme ausgeben (z. b., Rinde Sound holographic Hund stammen.)
* Sound Hinweise sollten in der UX verwendet werden, um dem Benutzer Feedback oder Kenntnis der Aktionen außerhalb der holographic Frame zu unterstützen.

### <a name="recommendations"></a>Empfehlungen

* Verwenden Sie räumliche Audio, zur Unterstützung bei der Ermittlung und Benutzer-Schnittstellen.
* Echte Sounds besser funktionieren als synthetisier oder unnatürlichen Sound.
* Die meisten Sounds sollten spatialized sein.
* Vermeiden Sie unsichtbar korrekturemitter ab.
* Vermeiden Sie räumliche Maskierung.
* Alle Sounds zu normalisieren.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Dokumentation

* [Räumliche sound](spatial-sound.md)
* [Räumliche Entwurf](spatial-sound-design.md)
* [Räumliche Sound in Unity](spatial-sound-in-unity.md)
* [Fallstudie für HoloTour sound räumlich](case-study-spatial-sound-design-for-holotour.md)
* [Verwenden von räumlichen Sound in RoboRaid Fallstudie](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a>Tools und tutorials

* [MR Spatial 220: Räumliche sound](holograms-220.md)
* [MRToolkit, Spatial Audio](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a>Konzentrieren Sie sich an holographic Frame (Blickfeld) Grenzen

Gut gestaltete Benutzeroberflächen erstellen und Warten von nützlichen Kontext der virtuellen Umgebung, die über die Benutzer erweitert. Einen durchdachten Entwurf Content skalierungs-und Kontext umfasst die Minderung der Auswirkungen der Blickfeld Grenzen, die räumliche Audio, Anleitungen, Systeme und Position des Benutzers. Wenn rechts durchgeführt wird, wird den Benutzer, dass weniger durch das Blickfeld Grenzen eingeschränkt, während Sie eine sich app-Erfahrung so aussehen.

### <a name="device-impact"></a>Auswirkungen des Geräts

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Am besten  |  Erfüllt |  Fehler |
--- | --- | ---
|  Benutzer verliert nie Kontext und Anzeigen von vertraut ist. Unterstützung der Kontext wird für große Objekte bereitgestellt. Auffindbarkeit und Anzeigen von Anweisungen für Objekte außerhalb des Rahmens bereitgestellt. Im Allgemeinen sind die Motion-Entwurf und die Skalierung der Hologramme für eine vertraut Anzeigefunktionen geeignet. | Benutzer werden niemals Kontext verliert, aber in bestimmten Situationen möglicherweise zusätzliche trichterhalses während der Übertragung erforderlich. In bestimmten Situationen wird Skalierung Hologramme entweder vertikal oder horizontal Frames verursacht manche Bewegung trichterhalses Hologramme anzeigen zu unterbrechen. | Wahrscheinlich Kontext und/oder konsistente trichterhalses Motion verlieren Benutzer ist erforderlich, um Hologramme anzuzeigen. Kein Kontext für große Objekte holographic, Verschieben von Objekten außerhalb des Rahmens ohne Erkennbarkeit Anleitungen oder hohe Hologramme verliert einfach gefordert regulären trichterhalses während der Übertragung an. | 

### <a name="how-to-measure"></a>Gewusst wie: messen

* Kontext für eine (groß) – Hologramm verloren geht oder aufgrund der an den Grenzen freigestellt wird nicht erkannt.
* Speicherort der Hologramme sind schwer zu finden, die aufgrund des Mangels an Aufmerksamkeit Directors oder Inhalte, die schnell in und aus der holografischen Frame verschoben wird.
* Szenario erfordert regelmäßige und sich wiederholende nach oben oder unten Head während der Übertragung ein Hologramm, wodurch trichterhalses Ermüdung vollständig angezeigt.

### <a name="recommendations"></a>Empfehlungen

* Starten Sie die Benutzeroberfläche, mit kleine Objekte, die das Blickfeld anpassen, mit visuellen Hinweise auf größeren Versionen wechseln.
* Verwenden Sie räumliche Audio- und Aufmerksamkeit Directors, um Benutzerinhalte suchen, die sich das Blickfeld.
* Vermeiden Sie so weit wie möglich, Hologramme, die das Blickfeld vertikal zugeschnitten.
* Geben Sie dem Benutzer mit in-app-Anleitung für die optimale Anzeige Speicherort ein.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Dokumentation

* [Holographic frame](holographic-frame.md)
* [Fallstudie, HoloStudio UI und Interaktion entwerfen Erkenntnisse](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [Skalieren von Objekten und Umgebungen](scale.md)
* [Cursor, visuelle Hinweise](cursors.md#visual-cues)

#### <a name="external-references"></a>Externe Verweise

* [ActiveX Data Objects und das Blickfeld](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a>Inhalte reagiert an Benutzerposition

Hologramme sollte auf die Benutzerposition auf ungefähr die gleiche Weise reagieren, die "echten" Objekte. Eine wichtige Design-Herausforderungen ist UI-Elemente, die unbedingt eines Benutzers Position können nicht davon ausgehen nicht bewegt wird und sich Anpassen des Benutzers während der Übertragung. Das Entwerfen einer app, die ordnungsgemäß an Benutzerposition anpasst erstellt eine mehr glaubwürdig Erfahrung und einfacher zu verwenden.

### <a name="device-impact"></a>Auswirkungen des Geräts

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

<table>
<tr>
<td> Am besten </td><td> Inhalt und die Benutzeroberfläche anpassen an Benutzerpositionen, die Benutzer auf natürliche Weise mit Inhalt innerhalb des Bereichs der erwarteten Benutzer datenverschiebung kommunizieren kann.</td>
</tr><tr>
<td> Erfüllt </td><td> Benutzeroberfläche passt sich an die Benutzerposition an, aber Sie können die Ansicht der Aufforderung des Benutzers zum Anpassen ihrer Position schlüsselinhalt behindern.</td>
</tr><tr>
<td> Fehler </td><td><ol>
<li>UI-Elemente sind verloren gegangen oder gesperrt, während der Verschiebung zu Benutzer Steuerelemente Nachklang zurück zu (oder suchen).</li><li>UI-Elemente begrenzen, die Ansicht der Hauptinhalt.</li><li>UI-Bewegung ist nicht optimiert, für die Anzeige von Abstand und Momentum, insbesondere bei <a href="billboarding-and-tag-along.md">Tag-along</a> UI-Elemente.</li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a>Gewusst wie: messen

* Alle Messungen sollte innerhalb eines angemessenen Bereichs des Szenarios ausgeführt werden. Während der Verschiebung des Benutzers variieren kann, versuchen Sie nicht dazu bringen, die app mit extremer Benutzer verschieben.
* Für Benutzeroberflächenelemente sollte relevante Steuerelemente zur Verfügung, unabhängig von der Benutzer verschieben. Z. B., wenn der Benutzer wird durchlaufen, um eine 3D Karte mit Zoom und zum Anzeigen, sollte das Zoomsteuerelement für den Benutzer unabhängig vom Standort sofort verfügbar sein.

### <a name="recommendations"></a>Empfehlungen

* Der Benutzer die Kamera und steuern sie die Bewegung. Sie steuern können.
* Betrachten Sie billboarding für Text und Menüs-Systeme, die andernfalls Welt gesperrt oder verdeckt wird, wenn ein Benutzer verschoben wurden.
* Verwenden Sie Tag-along für Inhalte, die folgen dem Benutzer während nach wie vor den Benutzer angezeigt, was vorangestellt ist.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Dokumentation

* [Entwerfen für](hologram.md)
* [Farbe, Material und Licht](color,-light-and-materials.md)
* [Billboarding und tag-along](billboarding-and-tag-along.md)
* [Grundlagen der Interaktion](interaction-fundamentals.md)
* [Self-motion und Benutzer Locomotion](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a>Tools und tutorials

* [MR Eingabe 210: Blicke](holograms-210.md)

## <a name="input-interaction-clarity"></a>Eingabe Interaktion Klarheit

Eingabe Interaktion Klarheit ist wichtig, zu der app-benutzerfreundlichkeit und umfassen Eingabe Konsistenz, Zugänglichkeit, Auffindbarkeit der Interaction-Methode. Benutzer sollten plattformweiten allgemeine Aktivitäten ohne erlernen verwenden können. Wenn die app benutzerdefinierte Eingabe hat, muss klar kommuniziert und veranschaulicht werden.

### <a name="device-impact"></a>Auswirkungen des Geräts

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Am besten  |  Erfüllt |  Fehler |
--- | --- | ---
|  Eingabe Interaction-Methode sind konsistent mit den Windows Mixed Reality bereitgestellten [Anleitungen](interaction-fundamentals.md). Eine benutzerdefinierte Eingabe muss sollte nicht in Hinblick auf die Standardeingabe (stattdessen Verwendung standard Interaktion) werden deutlich kommuniziert und gezeigt, um den Benutzer. | Ähnlich wie bei der bewährten, aber benutzerdefinierte Eingaben, die mit standardmäßigen Eingabemethoden redundant sind. Benutzer kann weiterhin die Ziel und den Fortschritt über die app-Funktionalität erreichen. | Schwierig, input Methode oder eine Schaltfläche-Zuordnung zu verstehen. Eingabe stark angepasst wird, unterstützt nicht die Standardeingabe, keine Anweisungen oder Fatigue und Komfort Probleme verursachen. | 

### <a name="how-to-measure"></a>Gewusst wie: messen

* Die app verwendet einheitliche [Standard Eingabe Methoden.](interaction-fundamentals.md)
* Wenn die app ist Eingabe hat, wird sie eindeutig über kommuniziert:
* Eindrucks beim ersten Ausführen
* Einführende Bildschirme
* QuickInfos
* Hand-coach
* Hilfe
* Voice-over

### <a name="recommendations"></a>Empfehlungen

* Verwenden Sie die standard-Eingabe-Methoden nach Möglichkeit.
* Geben Sie Demos, Lernprogramme und QuickInfos für nicht standardmäßige Eingabemethoden an.
* Verwenden Sie eine konsistente Interaktionsmodell in der gesamten app.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Dokumentation

* [Grundlagen der Windows-MR Interaktion](interaction-fundamentals.md)
* [Es Objekte](interactable-object.md)
* [Blicke für](gaze-targeting.md)
* [Cursor](cursors.md)
* [Komfort und Blicke](comfort.md#gaze-direction)
* [Gesten](gestures.md)
* [Spracheingabe](voice-input.md)
* [Voice-Entwurf](voice-design.md)
* [Motion-Controller](motion-controllers.md)
* [Eingabe Portieren von Unity-Handbuch](input-porting-guide-for-unity.md)
* [Tastatureingaben in Unity](keyboard-input-in-unity.md)
* [In Unity bestaunen](gaze-in-unity.md)
* [Gesten und Motion-Controller in Unity](gestures-and-motion-controllers-in-unity.md)
* [Spracheingabe in Unity](voice-input-in-unity.md)
* [Tastatur-, Maus- und Controller-Eingaben in DirectX](keyboard,-mouse,-and-controller-input-in-directx.md)
* [Blicke, Gesten und Motion-Controller in DirectX](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [Spracheingabe in DirectX](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a>Tools und tutorials

* [Fallstudie: Das Streben nach persönlichere Datenverarbeitung](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [CAST-Studie: Entwerfen von HoloStudio UI und Interaktion Erkenntnisse](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [Beispiel-app: Periodisch-Tabelle der Elemente](periodic-table-of-the-elements.md)
* [Beispiel-app: Mondkalender-Modul](lunar-module.md)
* [MR Eingabe 210: Blicke](holograms-210.md)
* [MR Eingabe 211: Gesten](holograms-211.md)
* [MR Eingabe 212: Voice](holograms-212.md)

## <a name="interactable-objects"></a>Es Objekte

Eine Schaltfläche war lange Zeit eine Metapher, die zum Auslösen eines Ereignisses in der Welt für 2D abstrakt. In der dreidimensionalen mixed Reality-Welt müssen wir auf dieser Welt mehr Abstraktionsebenen beschränkt werden. Alles kann ein es Objekt sein, die ein Ereignis auslöst. Ein Objekt es kann als etwas von einer Tasse Kaffee für die Tabelle, eine Gleitkommazahl in der Luft Sprechblase dargestellt werden. Unabhängig von der Art sollte es Objekte vom Benutzer über SEH- und Hinweise klar erkennbar sein.

### <a name="device-impact"></a>Auswirkungen des Geräts

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Am besten  |  Erfüllt |  Fehler |
--- | --- | ---
|  Unabhängig von der Form, es Objekte sind über SEH- und Hinweise erkennbaren über drei Zustände: im Leerlauf, Ziel und ausgewählt. "Es noch einmal finden Sie unter" ist klarer und konsistent über die Umgebung verwendet. Objekte werden skaliert und verteilt, um für fehlerfrei zu ermöglichen. | Benutzer können erkennen Objekt als es durch Audio- oder visuelle Feedback, und als Ziel und aktivieren Sie das Objekt. | Wenn kein visual oder audio-Hinweise, kann Benutzer ein Objekt es nicht erkennen. Interaktionen sind Fehler aufgrund von Objekt skalieren oder den Abstand zwischen den Objekten entstehen. | 

### <a name="how-to-measure"></a>Gewusst wie: messen

* Es stehen nebenbei gesagt, immer "es"; bestimmte Schaltflächen, Menüs und app-Inhalte, einschließlich. Als Faustregel dürfte eine Orientierungshilfe SEH- und wenn es Objekte.

### <a name="recommendations"></a>Empfehlungen

* Verwenden Sie SEH- und Feedback für Interaktionen.
* Visuelles Feedback sollte unterschieden werden, für jede Zustand (im Leerlauf, gezielte, ausgewählte)
* Es Objekte skaliert, und für die Zielgruppenadressierung fehlerfrei platziert.
* Gruppierte es Objekte (z. B. eine Menüleiste oder Liste) sollte die richtigen Abstand für die Zielplattform verfügen.
* Schaltflächen und Menüs, die Stimme-Befehl unterstützen sollten die Beschriftungen bereitstellen, für das Befehl-Schlüsselwort ("angezeigt, das so sagen")

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Dokumentation

* [Es-Objekt](interactable-object.md)
* [Text in Unity](text-in-unity.md)
* [App-Leiste und das umgebende Feld](app-bar-and-bounding-box.md)
* [Voice-Entwurf](voice-design.md)

#### <a name="tools-and-tutorials"></a>Tools und tutorials

* [Mixed Reality-Toolkit - UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a>Raum Scannen

Apps, die räumliche Zuordnungsdaten erfordern basieren auf dem Gerät, um diese Daten im Laufe der Zeit automatisch zu erfassen und untersucht alle Sitzungen als Benutzer ihrer Umgebung mit dem Gerät aktiv. Der Vollständigkeit und die Qualität der Daten hängt von einer Reihe von Faktoren wie der Menge der, die der Benutzer ausgeführt hat, wie viel Zeit verstrichen ist, da die Auswertung und gibt an, ob die Objekte, z. B. Möbel und Türen verschoben haben, da das Gerät über den Bereich überprüft. Viele apps werden analysiert, die räumliche Zuordnungsdaten zu Beginn der Umgebung zu beurteilen, ob der Benutzer zusätzliche Schritte zur Verbesserung der Vollständigkeit und die Qualität der räumliche Zuordnung ausführen soll. Wenn der Benutzer erforderlich ist, um die Überprüfung der Umgebung, klar, dass während der Überprüfung Oberfläche Anleitungen bereitgestellt werden sollen.

### <a name="device-impact"></a>Auswirkungen des Geräts

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Am besten  |  Erfüllt |  Fehler |
--- | --- | ---
|  Visualisierung der räumlichen Mesh erkennen Sie, dass Benutzer, die Überprüfung ausgeführt werden. Benutzer werden eindeutig weiß, was zu tun ist und wenn die Überprüfung wird gestartet und angehalten wird. | Visualisierung der räumlichen Mesh angegeben ist, ist aber der Benutzer wissen möglicherweise nicht klar, was zu tun ist und keine Statusinformationen. | Keine Visualisierung des Mesh. Keine Informationen bereitgestellt, um dem Benutzer, wo Sie suchen, oder wenn die Überprüfung startet/beendet wird. |

### <a name="how-to-measure"></a>Gewusst wie: messen

* SEH- und bei der Überprüfung erforderlichen Platz bietet es Anleitungen, der angibt, wo gesucht werden soll, und wann starten und beenden zu scannen.

### <a name="recommendations"></a>Empfehlungen

* Geben Sie an, welcher Anteil der Gesamtgröße des Datenträgers in der Nähe der Benutzer muss in der Umgebung sein.
* Wenn die Überprüfung wird gestartet und beendet werden, z. B. eine Statusanzeige zu kommunizieren.
* Verwenden Sie eine Visualisierung des Netzes während der Überprüfung.
* Geben Sie SEH- und Hinweise, um den Benutzern suchen, und bewegen den Raum empfehlen.
* Informieren Sie den Benutzer, wohin Sie wechseln, um die Daten zu verbessern. In vielen Fällen ist es möglicherweise am besten, die dem Benutzer mitzuteilen, was sie (z. B. die Obergrenze suchen hinter Möbel ansehen), um die Überprüfung der erforderlichen Qualität zu erhalten.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Dokumentation

* [Die Überprüfung Visualisierung Platz](room-scan-visualization.md)
* [Fallstudie: Erweitern die räumlichen Funktionen für die Zuordnung von HoloLens](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Fallstudie: Räumliche Entwurf für HoloTour](case-study-spatial-sound-design-for-holotour.md)
* [Fallstudie: Erstellen ein Eintauchen in Fragmenten](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a>Tools und tutorials

* [Mixed Reality-Toolkit - UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a>Direktionale Indikatoren

In einer mixed Reality-app Inhalt möglicherweise außerhalb der Sichtfeld oder von realen Objekten okkludiert. Eine wohlgeformte-app wird für den Benutzer nicht sichtbaren Inhalt erleichtern. Direktionale Indikatoren warnen ein Benutzers auf wichtige Inhalte und bieten eine Anleitung, um den Inhalt relativ zur Position des Benutzers. Anleitungen, die nicht sichtbaren Inhalt kann es sich um die Form der sound korrekturemitter ab, mithilfe von Richtungspfeilen oder direkte visuelle Hinweise haben.

### <a name="device-impact"></a>Auswirkungen des Geräts

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Am besten  |  Erfüllt |  Fehler |
--- | --- | ---
|  SEH- und Hinweise führen den Benutzer direkt zu den relevanten Inhalten außerhalb Blickfeld. | Ein Pfeil, oder einige Indikator, der der Benutzer in die allgemeine Richtung an, der den Inhalt verweist. | Relevante Inhalte außerhalb der Sichtfeld, und eine schlechte oder kein Speicherort enthält Anweisungen für den Benutzer. | 

### <a name="how-to-measure"></a>Gewusst wie: messen

* Relevante Inhalte außerhalb der Sicht des Benutzers ist visual und/oder Hinweise ermittelt.

### <a name="recommendations"></a>Empfehlungen

* Verwenden Sie, wenn außerhalb des Benutzers Sichtfeld relevanten Inhalt ist ein direktionaler Indikatoren und Audiohinweise an den Benutzer auf den Inhalt. In vielen Fällen wird eine direkte visuelle Anleitung über Richtungspfeile bevorzugt.
* Direktionale Indikatoren sollten in den Cursor nicht erstellt werden.

### <a name="resources"></a>Ressourcen

* [Holographic frame](holographic-frame.md)

## <a name="data-loading"></a>Laden von Daten

Ein Statussteuerelement gibt dem Benutzer eine Rückmeldung, dass ein Vorgang mit langer Laufzeit ausgeführt wird. Dies kann bedeuten, dass der Benutzer mit der app interagieren nicht möglich, wenn die Statusanzeige angezeigt wird und auch angeben kann, wie lange die Wartezeit möglicherweise.

### <a name="device-impact"></a>Auswirkungen des Geräts

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Am besten  |  Erfüllt |  Fehler |
--- | --- | ---
|  Animierte visueller Indikator in Form einer Statusanzeige oder Ring, das Aufzeigen von Fortschritten bei der keine Daten laden oder zu verarbeiten. Der visuelle Indikator enthält Anleitungen, wie lange die Wartezeit werden konnte. | Benutzer wird darüber informiert, dass das Laden von Daten ausgeführt wird, aber es gibt keinen Hinweis dafür, wie lange die Wartezeit sein kann. | Kein Laden von Daten oder die Prozess-Indikatoren für die Aufgabe, die länger als 5 Sekunden dauert. |

### <a name="how-to-measure"></a>Gewusst wie: messen

* Stellen Sie sicher, dass es mehr als 5 Sekunden ist kein leerer Zustand, beim Laden der Daten.

### <a name="recommendations"></a>Empfehlungen

* Geben Sie eine Data Loading Animator-aufzeigen von Fortschritten in allen Fällen, wenn der Benutzer diese app abgestürzt ist oder die Beantwortung wahrnehmen könnten. Eine gute Faustregel ist, alle "laden"-Aktivität, die mehr als 5 Sekunden dauern.

### <a name="resources"></a>Ressourcen

* [Anzeigen des Status](progress.md)
