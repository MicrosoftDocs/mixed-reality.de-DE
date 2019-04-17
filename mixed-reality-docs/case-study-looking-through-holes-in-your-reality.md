---
title: 'Fallstudie: Lücken in der Realität ansehen'
description: Diese Fallstudie wird erläutert, wie die "Magic-Fenster" Auswirkung auf die HoloLens, damit der Benutzer hinter Wände, unter dem Boden und in virtuellen Positionen in ihre tatsächlichen Umgebung finden Sie unter implementieren.
author: EricRehmeyer
ms.author: ericrehm
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, Magic-Fenster, Parallaxe
ms.openlocfilehash: 0c0828a6ebbefdcff7f0a66f48469007c5c532df
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594525"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a>Fallstudie: Lücken in der Realität ansehen

Wenn Personen zu mixed Reality und wie sie Microsoft HoloLens verwenden können denken, sie in der Regel bleiben auf Fragen wie "Welche Objekte kann ich in meinem Raum hinzufügen?" oder "Was kann ich layer auf meinen Space?" Ich möchte einen anderen Bereich markieren, Sie können in Betracht ziehen – im Wesentlichen eine Zaubertrick – mit derselben Technologie, um in oder über die echten physischen Objekte, um Sie zu suchen.

## <a name="the-tech"></a>Der Technologie

Wenn Sie Aliens gekämpft haben, wie sie lassen sich durch Ihre Wände in  **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**, entsperrt hat, eine Wand in sicher  **[Fragmente](case-study-creating-an-immersive-experience-in-fragments.md)**, konnten Sie Glück haben, oder um den Anschluss unendlich Abstellposition in finden Sie unter der  **[Halo 5 Erfahrungen E3 2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)**, und Sie wissen, was ich spreche. Je nach Ihrer Fantasie kann dieses visual Trick temporäre Lücken in Ihrer Ausführen Trockenausbau verschoben oder Ausblenden von Bereichen, die unter einer loose Floorboard verwendet werden.

![RoboRaid fügt dreidimensionalen Pipes und andere Struktur hinter Wände nur über Lücken erstellt, da die Invaders produktivitätsherausforderungen sichtbar.](images/roboraid-640px.png)

RoboRaid fügt dreidimensionalen Pipes und andere Struktur hinter Wände nur über Lücken erstellt, da die Invaders produktivitätsherausforderungen sichtbar.

Verwenden eine der folgenden eindeutigen Hologramme für HoloLens, kann eine app den Eindruck des Inhalts hinter Ihrer Wände oder über Ihre Floor auf die gleiche Weise bereitstellen, in dem tatsächlich durch einen tatsächlichen Fenster dargestellt. Selbst nach links verschieben, und Sie sehen, was auf der rechten Seite ist. Je näher, und sehen Sie ein wenig alles. Der Hauptunterschied ist zuzulassen, dass echte Löcher, während Ihre Floor vorhanden sind wird nicht auf magische holographic Inhalt über durchklettern kann. (Ich werde eine Aufgabe zum Backlog hinzufügen.)

## <a name="behind-the-scenes"></a>Im Hintergrund

Diese Methode ist eine Kombination von zwei Auswirkungen. Erste, holographic Inhalt wird mit der ganzen Welt mithilfe von "räumlichen Anker." verknüpft. Mit Textmarken, dass der Inhalt "World gesperrt" bedeutet, dass es sich bei am gewünschten visuell Weg von der physischen Objekte in der Nähe, abweichungen nicht selbst, wie Sie verschieben oder das zugrunde liegende räumliche Zuordnung seine 3D-Modell Ihr Platz aktualisiert.

Zweitens ist holographic Inhalt auf ganz bestimmte Leerzeichen und visuell beschränkt, damit Sie nur über die Lücke in der Realität sehen können. Diese verdecken ist erforderlich ist, suchen Sie über einen logischen Loch, Fenster oder eine Tor, das den Trick verkauft. Ohne etwas blockiert die meisten der Ansicht sind kann einen Crack im Raum auf eine geheime Jurassic Dimension nur schlecht platzierten Godzilla formuliert werden.

![Dies ist nicht auf, eine tatsächliche Screenshot, aber eine Abbildung wie die geheimen Underworld von MR Grundlagen 101 für HoloLens aussieht. Die schwarze Gehäuse wird nicht angezeigt, aber Sie können Inhalt über eine virtuelle Lücke finden Sie unter. (Wenn Sie über ein echtes Gerät suchen, das die Bodenfläche scheint noch entfernt werden, da Ihre Augen in einem weiteren Abstand konzentrieren, als ob sie nicht noch vorhanden ist.)](images/origamiholecomposited-640px.png)

Dies ist keine tatsächliche Screenshot, sondern veranschaulicht, wie die geheimen Underworld aus der [MR Grundlagen 101](holograms-101.md) für HoloLens aussieht. Die schwarze Gehäuse wird nicht angezeigt, aber Sie können Inhalt über eine virtuelle Lücke finden Sie unter. (Wenn Sie über ein echtes Gerät suchen, das die Bodenfläche scheint noch entfernt werden, da Ihre Augen in einem weiteren Abstand konzentrieren, als ob sie nicht noch vorhanden ist.)

### <a name="world-locking-holographic-content"></a>World-Sperren holographic Inhalt

In Unity ist es so einfach wie das Hinzufügen einer Komponente WorldAnchor, sodass holographic Inhalt Welt gesperrt bleiben:

```
myObject.AddComponent<WorldAnchor>();
```

Die Komponente WorldAnchor wird ständig angepasst, die Position und Drehung des seine "gameobject" (und daher nichts in dieses Objekt in der Hierarchie), relativ zum in der Nähe physische Objekte stabil zu halten. Beim Erstellen Ihrer Inhalte, erstellen Sie es so, dass das Pivot "Stamm" des Objekts an dieser virtuellen Lücke zentriert ist. (Wenn des Objekts Pivot tief in die ist, die geringfügigen Anpassungen in Position und Drehung werden viel deutlicher bemerkbar sein und Lücke sieht unter Umständen nicht sehr stabil.)

### <a name="occluding-everything-but-the-virtual-hole"></a>Alles, was aber virtuelle Lücke occluding

Es gibt eine Vielzahl von Möglichkeiten, um die Ansicht, was in Ihrer Wände ausgeblendet ist selektiv zu blockieren. Einfach nutzt die Tatsache, dass die HoloLens eine additive-Anzeige, verwendet, d. h. vollständig schwarz Objekte nicht sichtbar angezeigt werden. Hierzu können Sie in Unity ohne spezielle Shader kein(e) Material Tricks – einfach schwarz Material zu erstellen und ein Objekt, das in den Inhalt der Felder zuweisen. Wenn Sie glauben nicht, wie 3D Modellierung ausführen, verwenden Sie eine Reihe von Quad-Standardobjekte einfach, und überlappen Sie sie leicht. Es gibt eine Reihe von Nachteilen bei dieser Vorgehensweise, aber dies ist der schnellste Weg abzurufenden funktioniert, und eine Low-Fidelity Konzept arbeiten Machbarkeitsstudien ist großartig, auch wenn Sie vermuten, dass Sie es später noch Mal umgestalten möchten.

Einen großen Nachteil bei der oben genannten "Blackbox" ist, dass es auch Fotografieren nicht. Während der Effekt über die Anzeige von HoloLens perfekte aussehen könnte, wird Screenshots, die Sie ergreifen angezeigt, ein großen schwarzes Objekts anstelle von was der Wand oder Floor übrig bleibt. Der Grund dafür ist, die die physische Hardware und Screenshots zusammengesetzten Hologramme und Realität unterschiedlich. Lassen Sie uns einen Moment lang umzuleiten, in eine gefälschte mathematische...

*Gefälschte Math-Warnung! Diese Zahlen und Formeln sollen veranschaulichen, einen Punkt so, dass keine Art von genau Metrik werden!*

Was Sie über HoloLens finden Sie unter:

```
( Reality * darkening_amount ) + Holograms
```

In den Screenshots und Videos angezeigt:

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

AUF ENGLISCH: Sehen Sie, bis die HoloLens ist eine einfache Kombination von abgedunkelten Reality (z.B. durch Sonnenbrille) und was Hologramme möchte, dass die app anzeigen. Aber wenn Sie einen Screenshot erstellen, wird der Kamera-Image mit der app-Hologramme entsprechend dem Wert der normalmaps pixelbasierte Transparenz gemischt.

Eine Möglichkeit, dies zu erreichen ist so ändern Sie das Material "Blackbox" nur zum Schreiben in die Tiefenpuffer, und alle anderen nicht transparente Materialien zu sortieren. Ein Beispiel hierfür finden Sie in der [WindowOcclusion.shader-Datei in die MixedRealityToolkit auf GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader). Die entsprechenden Zeilen werden hier kopiert:

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

(Beachten Sie "Offset 50, 100" Zeile ist auf Probleme, damit Sie wahrscheinlich vergessen, die sinnvoll wäre.)

Implementieren ein Material unsichtbar verdecken, können Ihre app, die ein Feld zu zeichnen, die in der Anzeige und mixed Reality-Screenshots korrekt aussieht. Bonuspunkte sammeln können Sie versuchen, die Leistung von Box weiter zu verbessern, indem Sie clever Möglichkeiten zum Zeichnen von Pixeln mit noch weniger nicht sichtbarer, aber, die wirklich in den schädlicher Pflanzen abrufen können und in der Regel nicht erforderlich.

![Hier ist der geheime Underworld von MR Grundlagen 101 wie Unity, die es, mit Ausnahme der äußeren Teile Feld occluding zeichnet. Beachten Sie, dass das Pivot-Element für die Underworld in der Mitte des Felds ist, wodurch die Lücke zu halten wie stabil möglichst relativ zu Ihrer tatsächlichen Floor.](images/underworld-occluded-640px.png)

Hier ist der geheime Underworld aus [MR Grundlagen 101](holograms-101.md) wie Unity, die es, mit Ausnahme der äußeren Teile Feld occluding zeichnet. Beachten Sie, dass das Pivot-Element für die Underworld in der Mitte des Felds ist, wodurch die Lücke zu halten wie stabil möglichst relativ zu Ihrer tatsächlichen Floor.

## <a name="do-it-yourself"></a>Es selbst tun.

Haben Sie eine HoloLens, und die Auswirkungen für sich selbst ausprobieren möchten? Am einfachsten möglich (keine Codierung erforderlich) ist die kostenlose 3D-Viewer-app installieren und Laden Sie dann die [the.fbx Downloaddatei, die ich auf GitHub bereitgestellt haben](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) ein Blume Pot-Modell in Ihrer Raum anzeigen. Laden sie auf die HoloLens, und Sie können den Eindruck, bei der Arbeit sehen. Wenn Sie vor dem Modell vertraut sind, sehen Sie nur in die kleine Öffnung – alles andere ist nicht sichtbar. Betrachten Sie das Modell über eine andere Seite, und nicht vollständig entfernt wird. Verwenden Sie die Verschiebung, Drehung und Skalierung Steuerelemente von 3D Viewer, um virtuelle Lücke für auf Oberflächen, vertikale position, die Sie sich vorstellen können, generieren einige Ideen!

![Dieses Modell in Ihrem Unity-Editor anzeigen, wird eine große Blackbox rund um die Flowerpot angezeigt. Für HoloLens wird das Feld ausgeblendet, bietet die Möglichkeit, einen Effekt Magic-Fenster.](images/magicwindowflowerpotineditor.png)

Dieses Modell in Ihrem Unity-Editor anzeigen, wird eine große Blackbox rund um die Flowerpot angezeigt. Für HoloLens wird das Feld ausgeblendet, bietet die Möglichkeit, einen Effekt Magic-Fenster.

Wenn eine app erstellen, die diese Technik verwendet werden sollen, lesen Sie die [MR Grundlagen 101 Tutorial](holograms-101.md) in die [Mixed Reality Academy](academy.md). Kapitel 7 endet mit der Zahl in Ihre Floor, die einen ausgeblendeten Underworld (wie oben abgebildete) zeigen. Wer hat gesagt, dass Tutorials langweilig sein?

Hier sind einige Ideen der, in dem Sie diese Idee weiter ausführen können:
* Betrachten Sie Möglichkeiten, um den Inhalt in diesem virtuellen Loch interaktiv zu machen. Die Benutzer über ihre Wände Auswirkungen haben kann, die diesen Trick bereitstellen, können die Bedeutung von Wunder wirklich verbessern.
* Betrachten Sie Möglichkeiten, über die Objekte dann wieder bekannte Bereiche finden Sie unter. Z. B. wie Sie platzieren eine Lücke holographic, in der Tabelle Kaffee und finden Sie unter Ihrem Floor darunter?

## <a name="about-the-author"></a>Der Autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Eric Rehmeyer</b><br>Senior Software Engineer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch
* [MR Basics 101: Vollständige Projekt mit Gerät](holograms-101.md)
* [Koordinatensysteme](coordinate-systems.md)
* [Räumliche Anker](spatial-anchors.md)
* [Räumliche Zuordnung](spatial-mapping.md)
