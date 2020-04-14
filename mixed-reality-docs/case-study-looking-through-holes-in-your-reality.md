---
title: 'Fallstudie: Durchsuchen der Lücken in ihrer Realität'
description: In dieser Fallstudie wird erläutert, wie der "Magic Window"-Effekt auf hololens implementiert wird, sodass der Benutzer hinter den Wänden, in der Etage und in virtuellen Öffnungen innerhalb der eigentlichen Umgebung sehen kann.
author: ericrehmeyer
ms.author: bestruku
ms.date: 10/18/2019
ms.topic: article
keywords: Windows Mixed Reality, hololens, Magic Window, Parser
ms.openlocfilehash: c829656c98b7c87f8b969dbbd16115f6a0bbaf27
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278148"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a>Fallstudie: Durchsuchen der Lücken in ihrer Realität

Wenn Menschen über gemischte Realität nachzudenken und was Sie mit Microsoft hololens tun können, bleiben Sie in der Regel auf Fragen wie "welche Objekte kann ich meinem Raum hinzufügen?". oder "Was kann ich über meinem Raum überlagern?" Ich möchte einen anderen Bereich hervorheben, den Sie in Erwägung gezogen haben – im Grunde ein Magic Trick –, der die gleiche Technologie verwendet, um Sie in oder durch echte physische Objekte zu suchen.

## <a name="the-tech"></a>Die Technologie

Wenn Sie bei der Unterbrechung der Wände in roboraid, beim Durchlaufen der Wände in **[roboraid](https://www.youtube.com/watch?v=Hf9qkURqtbM)** , das Entsperren eines Mauer Sicherheits in **[Fragmenten](case-study-creating-an-immersive-experience-in-fragments.md)** oder das Glück, den UNSC Infinity-Hangar in der **[Halo 5-Umgebung in 2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)** , festgestellt haben, haben Sie gesehen, was ich spreche. Abhängig von Ihrer Phantasie kann dieser visuelle Trick verwendet werden, um temporäre Löcher in den drywall zu versetzen oder um die Umgebungen unter einer losen Fläche auszublenden.

![Roboraid fügt dreidimensionale Pipes und andere Strukturen hinter ihren Wänden ein, die nur durch Löcher sichtbar sind, die bei einem Umbruch durch die Eindringlinge erstellt werden.](images/roboraid-640px.png)

Roboraid fügt dreidimensionale Pipes und andere Strukturen hinter ihren Wänden ein, die nur durch Löcher sichtbar sind, die bei einem Umbruch durch die Eindringlinge erstellt werden.

Wenn Sie eines dieser eindeutigen Hologramme in hololens verwenden, kann eine APP die Illusion von Inhalten hinter ihren Wänden oder im Boden auf die gleiche Weise bereitstellen, wie sich die Realität durch ein tatsächliches Fenster präsentiert. Bewegen Sie sich nach links, und Sie können sehen, was sich auf der rechten Seite befindet. Machen Sie sich näher, und Sie sehen etwas mehr von allem. Der Hauptunterschied besteht darin, dass Sie durch echte Löcher von Ihnen bis zu diesem magischen Holographic-Inhalt weiter gehen können. (Ich füge dem Rückstand eine Aufgabe hinzu.)

## <a name="behind-the-scenes"></a>Im Hintergrund

Dieser Trick ist eine Kombination aus zwei Effekten. Zuerst werden Holographic-Inhalte mithilfe von "räumlichen Ankern" an die Welt angeheftet. Die Verwendung von Ankern, um diesen Inhalt "weltweit" zu machen, bedeutet, dass das, was Sie sehen, nicht visuell von den physischen Objekten in der Nähe abweicht, auch wenn Sie sich bewegen, oder das zugrunde liegende räumliche Zuordnungssystem aktualisiert sein 3D-Modell Ihres Raums.

Zweitens: der Holographic-Inhalt ist visuell auf einen sehr spezifischen Bereich beschränkt, sodass Sie nur die Löcher in ihrer Realität erkennen können. Diese Okklusion ist erforderlich, um eine logische Lücke, ein Fenster oder einen Tor zu suchen, die den Trick verkauft. Ohne den größten Teil der Ansicht zu blockieren, könnte es sein, dass ein Platz auf eine geheime Jurassic-Dimension wie ein schlechter platzierter Dinosaurier aussieht.

![Dies ist kein tatsächlicher Screenshot, aber es wird veranschaulicht, wie die geheime Unterwelt aus den Grundlagen 101 in den hololens aussieht. Das schwarze Gehäuse wird nicht angezeigt, aber Sie können Inhalte über eine virtuelle Lücke sehen. (Wenn Sie ein tatsächliches Gerät durchsuchen, scheint die Etage sogar noch mehr zu verschwinden, da sich die Augen auf eine weitere Entfernung konzentrieren, als wäre sie noch nicht vorhanden.)](images/origamiholecomposited-640px.png)

Dies ist kein tatsächlicher Screenshot, aber es wird veranschaulicht, wie die geheime Unterwelt aus den [Grundlagen 101](holograms-101.md) des geheimen Haupt Schlüssels auf hololens prüft. Das schwarze Gehäuse wird nicht angezeigt, aber Sie können Inhalte über eine virtuelle Lücke sehen. (Wenn Sie ein tatsächliches Gerät durchsuchen, scheint die Etage sogar noch mehr zu verschwinden, da sich die Augen auf eine weitere Entfernung konzentrieren, als wäre sie noch nicht vorhanden.)

### <a name="world-locking-holographic-content"></a>Weltweit sperrender Holographic-Inhalt

In Unity ist das durch das Hinzufügen einer worldanchor-Komponente genauso einfach wie das Hinzufügen einer worldanchor-Komponente:

```
myObject.AddComponent<WorldAnchor>();
```

Die worldanchor-Komponente passt die Position und Drehung des gameobject (und somit alles andere unter diesem Objekt in der Hierarchie) ständig an, um es in Relation zu den nahe gelegenen physischen Objekten stabil zu halten. Wenn Sie Ihren Inhalt erstellen, erstellen Sie ihn so, dass der Stamm Pivot Ihres Objekts auf dieser virtuellen Lücke zentriert ist. (Wenn sich der Pivot Ihres Objekts tief in der Wand befindet, sind seine geringfügigen Anpassungen an Position und Drehung deutlich deutlicher, und die Lücke sieht möglicherweise nicht sehr stabil aus.)

### <a name="occluding-everything-but-the-virtual-hole"></a>Alles außer dem virtuellen Loch

Es gibt verschiedene Möglichkeiten, die Ansicht selektiv zu blockieren, was in ihren Wänden ausgeblendet ist. Der einfachste Vorteil nutzt die Tatsache, dass hololens eine Additive Anzeige verwendet, was bedeutet, dass vollständig schwarze Objekte unsichtbar erscheinen. Sie können dies in Unity tun, ohne spezielle Shader-oder Material Tricks durchführen zu müssen – erstellen Sie einfach ein schwarzes Material, und weisen Sie es einem Objekt zu, das ihren Inhalt einrichtet. Wenn Sie die 3D-Modellierung nicht durchführen möchten, verwenden Sie einfach einige standardmäßige Quad-Objekte, und überlappen Sie Sie leicht. Bei diesem Ansatz gibt es eine Reihe von Nachteilen, aber es ist die schnellste Möglichkeit, etwas zu funktionieren, und es ist großartig, wenn Sie vermuten, dass Sie es zu einem späteren Zeitpunkt umgestalten sollten.

Ein wichtiger Nachteil des oben genannten "Blackbox"-Ansatzes ist, dass er nicht gut fotografiert. Obwohl ihre Wirkung in der Anzeige von hololens perfekt aussehen könnte, zeigen alle Screenshots, die Sie verwenden, ein großes Schwarzes Objekt anstelle der verbleibenden Elemente ihrer Wand oder Etage an. Der Grund hierfür ist, dass die physische Hardware und die Screenshots von holograms und der Realität unterschiedlich sind. Wir leiten einen Moment in eine falsche Mathematik ein...

*Falsche mathematische Warnung! Diese Zahlen und Formeln sollen einen Punkt veranschaulichen, aber keine genaue Metrik.*

Was Sie durch hololens sehen:

```
( Reality * darkening_amount ) + Holograms
```

Was Sie in Screenshots und Videos sehen:

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

In englischer Sprache: das, was Sie durch hololens sehen, ist eine einfache Kombination aus der dunklen Realität (z. b. über Sonnenbrillen) und der von der APP anzuzeigenden Hologramme. Wenn Sie jedoch einen Screenshot erstellen, wird das Bild der Kamera gemäß dem Transparenz Wert pro Pixel mit den Hologrammen der APP kombiniert.

Eine Möglichkeit, dieses Problem zu umgehen, besteht darin, das "Blackbox"-Material so zu ändern, dass nur in den tiefen Puffer geschrieben wird, und mit allen anderen nicht transparenten Materialien zu sortieren. Ein Beispiel hierfür finden Sie in der Datei " [windowocclusion. Shader" im mixedrealitytoolkit auf GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader). Die relevanten Zeilen werden hier kopiert:

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

(Beachten Sie, dass es sich bei der Zeile "Offset 50, 100" um nicht verbundene Probleme handelt, daher wäre es wahrscheinlich sinnvoll, dies zu übernehmen.)

Wenn Sie ein unsichtbares Okklusions Material wie das implementieren, kann Ihre APP ein Feld zeichnen, das in der Anzeige und in Mixed-Reality-Screenshots korrekt aussieht. Wenn Sie Bonuspunkte benötigen, können Sie versuchen, die Leistung dieses Felds noch weiter zu verbessern, indem Sie clever Dinge durchführen, um noch weniger unsichtbare Pixel zu zeichnen, aber das ist in der Regel nicht erforderlich.

![Hier sehen Sie die geheime Unterwelt aus den Grundlagen 101, wenn Unity Sie zeichnet, mit Ausnahme der äußeren Teile des okding Felds. Beachten Sie, dass sich der Pivotpunkt für die Unterwelt in der Mitte des Felds befindet, wodurch das Loch so stabil wie möglich in Bezug auf ihre tatsächliche Oberfläche bleibt.](images/underworld-occluded-640px.png)

Hier sehen Sie die geheime Unterwelt aus den [Grundlagen 101](holograms-101.md) , wenn Unity Sie zeichnet, mit Ausnahme der äußeren Teile des okding Felds. Beachten Sie, dass sich der Pivotpunkt für die Unterwelt in der Mitte des Felds befindet, wodurch das Loch so stabil wie möglich in Bezug auf ihre tatsächliche Oberfläche bleibt.

## <a name="do-it-yourself"></a>Selbst ausführen

Sie haben einen hololens und möchten die Auswirkung selbst ausprobieren? Am einfachsten können Sie die kostenlose 3D-Viewer-App installieren und dann die [heruntergeladene FBX-Datei herunterladen, die Sie auf GitHub bereitgestellt haben](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) , um ein Blumentopf Modell in Ihrem Raum anzuzeigen. Laden Sie Sie in hololens, und Sie können die Illusion bei der Arbeit sehen. Wenn Sie sich vor dem Modell befinden, können Sie nur in der kleinen Lücke erkennen – alles andere ist unsichtbar. Sehen Sie sich das Modell von einer beliebigen anderen Seite an, und es verschwindet vollständig. Verwenden Sie die Steuerelemente Bewegung, Drehung und Skalierung des 3D-Viewers, um die virtuelle Lücke gegen jede vertikale Oberfläche zu positionieren, die Sie sich vorstellen können, um einige Ideen zu generieren.

![Wenn Sie dieses Modell in Ihrem Unity-Editor anzeigen, wird ein großes schwarzes Feld um den Blumentopf angezeigt. Bei hololens wird das Feld ausgeblendet, sodass ein magische Fenstereffekt angezeigt wird.](images/magicwindowflowerpotineditor.png)

Wenn Sie dieses Modell in Ihrem Unity-Editor anzeigen, wird ein großes schwarzes Feld um den Blumentopf angezeigt. Bei hololens wird das Feld ausgeblendet, sodass ein magische Fenstereffekt angezeigt wird.

Wenn Sie eine APP erstellen möchten, die diese Technik verwendet, sehen Sie sich das Tutorial zu den [Grundlagen 101](holograms-101.md) in den Lernprogrammen " [Mixed Reality](tutorials.md)" an. Kapitel 7 endet mit einer Explosion in ihrem Boden, die eine verborgene Unterwelt (wie oben dargestellt) zeigt. Wer hat schon gesagt, dass Tutorials langweilig waren?

Im folgenden finden Sie einige Ideen dazu, wo Sie diese Idee als nächstes treffen können:
* Stellen Sie sich vor, wie der Inhalt innerhalb des virtuellen Lochs interaktiv ist. Wenn Ihre Benutzer über Ihre Wände hinausgehende Auswirkungen haben, können Sie den Sinn von Fragen, die dieser Trick bereitstellen kann, wirklich verbessern.
* Stellen Sie sich vor, wie Sie Objekte auf bekannte Bereiche zurück sehen können. Wie können Sie z. b. in der Coffee-Tabelle eine Holographic-Lücke platzieren und den Fußboden darunter sehen?

## <a name="about-the-author"></a>Informationen zum Autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Eric rehmeyer</b><br>Senior Software Engineer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch
* [Grundlagen 101: Projekt mit Gerät abschließen](holograms-101.md)
* [Koordinatensysteme](coordinate-systems.md)
* [Raumanker](spatial-anchors.md)
* [Räumliche Abbildung](spatial-mapping.md)
