---
title: Farbe, Licht und Material
description: Das Entwerfen von Inhalten für Mixed Reality erfordert eine sorgfältige Auswahl von Farbe, Beleuchtung und Material für jedes visuelle Objekt, das in Ihrer Darstellung verwendet wird.
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Gemischte Windows-Realität, Design, Farbe, Licht, Materialien
ms.openlocfilehash: c49d88c2bb53c07adcb77e8dbb0e3cd77e1e78ae
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436408"
---
# <a name="color-light-and-materials"></a>Farbe, Licht und Material

Das Entwerfen von Inhalten für Mixed Reality erfordert eine sorgfältige Auswahl von Farbe, Beleuchtung und Material für jedes visuelle Objekt, das in Ihrer Darstellung verwendet wird. Diese Entscheidungen können sowohl für Ästhetik als auch für die Verwendung von Licht und Material zum Festlegen des Klangs einer immersiven Umgebung und funktionaler Zwecke verwendet werden, wie z. b. das Verwenden von markanten Farben, um Benutzer über eine bevorstehende Aktion zu benachrichtigen. Jede dieser Entscheidungen muss gegen die Möglichkeiten und Einschränkungen für das Zielgerät ihrer Arbeit abgewogen werden.

Im folgenden finden Sie Richtlinien, die speziell für das Rendern von Assets auf immersiven und Holographic Viele davon sind eng an andere technische Bereiche gebunden, und eine Liste verwandter Themen finden Sie im Abschnitt " [Siehe auch](color,-light-and-materials.md#see-also) " am Ende dieses Artikels.

## <a name="rendering-on-immersive-vs-holographic-devices"></a>Rendering auf immersiven und Holographic-Geräten

Inhalte, die in immersiven Headsets gerendert werden, sind im Vergleich zu in Holographic-Headsets gerenderten Inhalten visuell anders. Obwohl immersive Headsets den Inhalt in der Regel so rendern, wie Sie es auf einem 2D-Bildschirm erwarten würden, verwenden Holographic-Headsets wie hololens Farb sequenzielle anzeigen, um Hologramme zu rendern.

Nehmen Sie sich immer Zeit, um Ihre Holographic-Erfahrungen in einem Holographic-Headset zu testen. Die Darstellung des Inhalts, auch wenn er speziell für holografische Geräte erstellt wurde, unterscheidet sich wie auf sekundären Monitoren, Momentaufnahmen und in der Ansicht "Betrachter". Denken Sie daran, die Erfahrung mit einem Gerät zu überprüfen, die Beleuchtung von holograms zu testen und von allen Seiten (sowie von oberhalb und unten) zu beobachten, wie Ihre Inhalte gerendert werden. Stellen Sie sicher, dass auf dem Gerät eine Reihe von Einstellungen für die Helligkeit getestet wird, da es unwahrscheinlich ist, dass alle Benutzer einen angenommenen Standardwert und einen unterschiedlichen Satz von Beleuchtungsbedingungen gemeinsam verwenden.

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>Grundlagen des Renderings auf Holographic-Geräten
* **Holografische Geräte verfügen über Additive Anzeige** – holograms werden durch das Hinzufügen von Licht in der realen Welt erstellt – weiß weiß, während schwarz angezeigt wird.
* **Die Auswirkung von Farben variiert je nach Benutzerumgebung** – es gibt viele verschiedene Beleuchtungsbedingungen im Raum eines Benutzers. Erstellen Sie Inhalte mit angemessenen Kontrast Ebenen, um die Übersichtlichkeit zu unterstützen.
* **Vermeiden Sie dynamische Beleuchtung** – holograms, die in Holographic-Umgebungen einheitlich beleuchtet werden, sind die effizienteste Lösung. Mithilfe von Advanced werden die Funktionen von mobilen Geräten wahrscheinlich durch die dynamische Beleuchtung überschritten. Wenn eine dynamische Beleuchtung erforderlich ist, wird empfohlen, den [Mixed Reality Toolkit Standard-Shader](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md)zu verwenden. 

## <a name="designing-with-color"></a>Entwerfen mit Farbe

Aufgrund der Art der additiven Anzeige können einige Farben in Holographic-anzeigen anders erscheinen. Einige Farben werden in Beleuchtungs Umgebungen angezeigt, während andere weniger beeinträchtigt werden. Kalte Farben neigen tendenziell in den Hintergrund, während die warmen Farben in den Vordergrund gerückt werden. Berücksichtigen Sie die folgenden Faktoren, wenn Sie Farben in ihren Erfahrungen erkunden:
* **Gamut** -hololens profitiert von einer "breiten Palette" von Farben, konzeptionell vergleichbar mit Adobe RGB. Folglich können einige Farben verschiedene Qualitäten und Darstellung im Gerät aufweisen.
* **Gamma** : die Helligkeit und der Kontrast des gerenderten Bilds unterscheiden sich zwischen immersiven und holografischen Geräten. Diese Geräte Unterschiede scheinen häufig dunkle Bereiche von Farbe und Schatten zu bilden, die mehr oder weniger hell sind.
* **Farbtrennung** : wird auch als "Farb Aufschlüsselung" oder "farbrandging" bezeichnet. die Farbtrennung tritt am häufigsten bei der Verschiebung von holograms (einschließlich Cursor) auf, wenn ein Benutzer Objekte mit den Augen nachverfolgt.
* **Farb Einheitlichkeit** : in der Regel werden holograms hell genug gerendert, sodass Sie unabhängig vom Hintergrund die Farb Einheitlichkeit beibehalten. Große Bereiche können zu einem blotbereich werden. Vermeiden Sie große Bereiche mit heller, voll Tonfarbe.
* **Rendern von hellen Farben** : weiß ist sehr hell und sollte sparsam verwendet werden. In den meisten Fällen sollten Sie einen weißen Wert um R 235 G 235 B 235 sehen. Große helle Bereiche können Benutzer Unannehmlichkeiten verursachen.

**Rendern von dunklen Farben**

Aufgrund der Art von Additiven anzeigen werden dunkle Farben transparent angezeigt. Ein solides Schwarzes Objekt wird nicht anders als die reale Welt angezeigt. Siehe Alpha Kanal weiter unten. Um die Darstellung von "Black" zu verwenden, verwenden Sie einen sehr dunklen RGB-Wert, z. b. 16, 16, 16.

![normale im Vergleich zu breite Farbpalette](images/640px-widegamut.png)<br>
*Normaler Vergleich mit breit farbiger Farbpalette*

## <a name="technical-considerations"></a>Technische Überlegungen
* **Aliasing** : Sie können die Aliasing-, Verzweigungs-oder "Treppen Schritte" übernehmen, bei denen der Rand der Geometrie eines holograms der realen Welt entspricht. Durch die Verwendung von Texturen mit hoher Detailgenauigkeit kann dieser Effekt erschwert werden. Texturen sollten zugeordnet und gefiltert werden. Sie sollten die Ränder von holograms ausblenden oder eine Textur hinzufügen, die eine schwarze Rahmen Linie um Objekte erzeugt. Vermeiden Sie nach Möglichkeit schlanke Geometrie.
* **Alphakanal** : Sie müssen den Alphakanal für alle Teile, in denen Sie kein Hologram rendern, vollständig transparent löschen. Das nicht definierte Alpha definierte führt zu visuellen Elementen, wenn Bilder/Videos vom Gerät oder der Ansicht "Betrachter" übernommen werden.
* **Textur Dämpfung** : da Light in Holographic-anzeigen Additiv ist, empfiehlt es sich, große Bereiche von hellen, voll Tonfarben zu vermeiden, da Sie häufig nicht den beabsichtigten visuellen Effekt ergeben.

## <a name="storytelling-with-light-and-color"></a>Storytelling mit Licht und Farbe

"Light" und "Color" können dazu beitragen, dass Ihre Hologramme in der Umgebung eines Benutzers natürlicher angezeigt werden, und Sie bieten Anleitungen und Hilfe für den Benutzer. Berücksichtigen Sie die folgenden Faktoren, um die Beleuchtung und die Farbe zu untersuchen:

:::row:::
    :::column:::
* **Vignetup** : ein "Vignette"-Effekt auf abdunkeln Materialien kann die Aufmerksamkeit des Benutzers auf den Mittelpunkt des Felds der Ansicht konzentrieren. Dadurch wird das Material des Hologramms in einem RADIUS aus dem Blick Vektor des Benutzers dunkel. Beachten Sie, dass dies auch wirksam ist, wenn die Ansichten des Benutzers aus einem schrägen oder einem ausöffnende Winkel holograms.<br>
* **Akzente** : ziehen Sie die Aufmerksamkeit auf Objekte oder Interaktionspunkte durch kontrastreiche Farben, Helligkeit und Beleuchtung. Eine ausführlichere Betrachtung der Beleuchtungs Methoden in Storytelling finden Sie unter [Pixel-kinemgraphy-a-Beleuchtungs Ansatz für Computer Grafiken](https://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf).<br>
        <br>
        *Image: Verwenden von Color zum Anzeigen der Betonung von Storytelling-Elementen, die hier in einer Szene von [Fragmenten](https://www.microsoft.com/p/fragments/9nblggh5ggm8)dargestellt werden.*
    :::column-end:::
        :::column:::
        ![Verwendung von Color zum Anzeigen der Betonung von Storytelling-Elementen, die hier in einer Szene von Fragmenten dargestellt werden.](images/640px-fragments.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="see-also"></a>Weitere Informationen:
* [Farbtrennung](hologram-stability.md#color-separation)
* [Hologramme](hologram.md)
* [Microsoft Design Language-Farbe](https://www.microsoft.com/design/color)
* [Universelle Windows-Plattform Farbe](https://docs.microsoft.com/windows/uwp/style/color)
