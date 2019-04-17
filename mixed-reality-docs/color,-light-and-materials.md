---
title: Farbe, helle und Materialien
description: Entwerfen von Inhalt für mixed Reality erfordert sorgfältigen Einhaltung der Farbe, Beleuchtung und Materialien für jede der visuelle Objekte in Ihrer Umgebung verwendet.
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, entwerfen "," Farbe "," Light "," Materialien
ms.openlocfilehash: 3f8ee8edfe4cbbaf8a55b3c4a9125f752823be9c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594881"
---
# <a name="color-light-and-materials"></a>Farbe, helle und Materialien

Entwerfen von Inhalt für mixed Reality erfordert sorgfältigen Einhaltung der Farbe, Beleuchtung und Materialien für jede der visuelle Objekte in Ihrer Umgebung verwendet. Diese Entscheidungen können für Funktionen, wie die Verwendung von auffallender Farben, die Benutzer einer bevorstehenden Aktion und ästhetischen Zwecke, wie die Verwendung von Licht und Material den Tonfall einer immersive-Umgebung festgelegt werden. Jede dieser Entscheidungen muss für die Möglichkeiten und Einschränkungen von Ihren Erfahrungen des Zielgeräts abgewogen werden.

Im folgenden sind die Richtlinien, der Rendering-Assets in sowohl holographic als auch immersive Headsets spezifisch. Viele davon sind eng daran gebunden zu anderen technischen Bereichen und eine Liste der verwandten Themen finden Sie der [Siehe auch](color,-light-and-materials.md#see-also) Abschnitt am Ende dieses Artikels.

## <a name="rendering-on-immersive-vs-holographic-devices"></a>Rendering für immersive im Vergleich zu holographic-Geräten

Inhalt im immersive Headsets gerendert werden visuell von anderen, im Vergleich zu Inhalten, die in der holografischen Headsets gerendert angezeigt. Immersive Headsets ähnlich wie auf einem 2D-Bildschirm erwartet in der Regel Inhalt rendern, wird holographic Headsets wie HoloLens verwenden, rendert Hologramme Farbe sequenzielle, durchsichtigen RGB angezeigt.

Immer so testen Sie Ihre holographic Erfahrungen in einer holographic Kopfhörer dauern. Die Darstellung des Inhalts, variiert auch wenn sie speziell für holographic-Geräten, basiert wie auf sekundären Monitore, Momentaufnahmen, und klicken Sie im Spectator anzeigen. Denken Sie daran, um Erfahrungen mit einem Gerät, das die Beleuchtung der Hologramme testen und Prüfen von allen Seiten (sowie oben und unten) Schritt für Schritt wie Ihre Inhalte gerendert wird. Achten Sie darauf, um auf eine Vielzahl von Einstellungen der Helligkeit auf dem Gerät zu testen, wie es ist unwahrscheinlich, dass alle Benutzer ein Standard wird angenommen, sowie eine Vielzahl von Lichtverhältnissen gemeinsam genutzt werden.

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>Grundlagen des Renderings auf holographic-Geräten
* **Holographic Geräte sind additiv zeigt** – Hologramme werden erstellt, durch das Hinzufügen von Licht auf das Licht aus der realen Welt – weiß hell, angezeigt wird, während für Schwarz transparent angezeigt wird.
* **Farben Auswirkungen unterscheidet sich je nach Umgebung des Benutzers** – es gibt viele verschiedene Lichtverhältnissen in Raum aufbewahren, eines Benutzers. Erstellen von Inhalten mit angemessenen Kontrast um Übersichtlichkeit zu unterstützen.
* **Vermeiden Sie dynamische Beleuchtung** – Hologramme, die gleichmäßig in holografischen Benutzeroberfläche Leuchten sind am effizientesten. Mithilfe von erweiterten, dynamische Beleuchtung wird die Funktionen von mobilen Shader wahrscheinlich überschreiten.

## <a name="designing-with-color"></a>Entwerfen mit Farbe

Aufgrund der Art der additiv angezeigt werden soll können bestimmte Farben auf holographic zeigt unterschiedlich angezeigt werden. Einige Farben werden in Umgebungen mit Beleuchtung angezeigt, während andere als weniger weitreichende angezeigt werden. "Cool" Farben in der Regel, die in den Hintergrund rücken, während die Farben der betriebsbereite in den Vordergrund springen. Beachten Sie diese Faktoren, wie Sie Farbe in Ihre Erfahrungen durchsuchen:
* **Farbskala** -HoloLens profitiert von einer "breiten"Skala der, konzeptionell identisch mit Adobe RGB-Farbe. Daher können einige Farben andere Qualitäten und Darstellung auf dem Gerät aufweisen.
* **Gamma** -Helligkeit und Kontrast des gerenderten Bilds variiert zwischen immersive und holographic-Geräten. Diese Geräteunterschiede angezeigt werden häufig um mehr oder weniger hellen dunkle Bereiche von Farbe und Schatten zu machen.
* **Farbe, die Trennung** – auch als "Farbe Aufschlüsselung" oder "Farbsäume" bezeichnet, farbliche Trennung am häufigsten tritt auf, mit dem Verschieben von Hologramme (einschließlich Cursor) Wenn ein Benutzer Objekte mit ihren Augen Wirklichkeit verfolgt.
* **Farbe der Einheitlichkeit** – in der Regel Hologramme hell genug dargestellt werden, so dass sie Farbe Einheitlichkeit, unabhängig von der Hintergrund beibehalten. Große Bereiche können Farbkleckse werden. Vermeiden Sie große Speicherbereiche leuchtende, solide Farbe.
* **Rendern helle Farben** -Whitepaper wird angezeigt, sehr helle und sollten sparsam eingesetzt werden. In den meisten Fällen sollten Sie einen weißen Wert in R 235 G 235 B 235. Große hellen Bereiche möglicherweise Benutzer stören.

**Rendern von dunkler Farben**

Aufgrund der Art der additiv angezeigt werden soll erscheinen dunkle Farben transparent. Ein solid black-Objekt wird nicht aus der Praxis anders angezeigt. Unten finden Sie unter Alpha-Kanal. Sodass die Darstellung von "Black" versuchen Sie es einen sehr dunklen grauen RGB-Wert wie z. B. 16,16,16.

![Normal im Vergleich zu Breite Farbskala](images/640px-widegamut.png)<br>
*Normal im Vergleich zu Breite Farbskala*

## <a name="technical-considerations"></a>Technische Überlegungen
* **Aliasing** -werden Aliase verzweigte oder "Treppe Schritte" am Rand des ggf. ein Hologramm Geometrie, in der realen Welt erfüllt überlegten Prozess abwägen. Verwenden von Texturen mit sehr detailgetreu kann diesen Effekt Vorteile. Texturen zugeordnet werden sollen, und Filtern aktiviert. Erwägen Sie die Ränder des Hologramme eingeblendet oder Hinzufügen einer Textur, die einen Rahmen schwarzen Rand, um Objekte erstellt. Vermeiden Sie möglichst thin-Geometrie.
* **Alpha-Kanal** -müssen Sie Ihre alpha-Kanal in vollständig transparent, für alle Teile, in denen Sie ggf. ein Hologramm nicht wiedergegeben werden, löschen. Die alpha undefiniert Leads verlässt von visuellen Elementen, beim Erstellen von Images/Videos über das Gerät oder mit Spectator anzeigen.
* **Texture-Weichzeichnen** – da Licht ist additiv im holographic angezeigt werden, es wird empfohlen, große Speicherbereiche leuchtende, solide Farbe vermieden werden, da sie häufig nicht den gewünschten visuellen Effekt erzeugt.

## <a name="storytelling-with-light-and-color"></a>Storytelling mit Licht und Farbe

Licht und Farbe können machen Ihre Hologramme natürlicher im eines Benutzers Umgebung sowie enthalten Anleitungen angezeigt, und die Hilfe für den Benutzer. Holographic arbeiten berücksichtigen Sie folgende Faktoren, wie Sie Beleuchtung und Farbe untersuchen:
* **Vignettierung** -ein Effekt 'Vignette' Materialien Abdunkeln können konzentrieren der Aufmerksamkeit des Benutzers, den Mittelpunkt der Sicht des. Dieser Effekt lässt die Hologramm Material auf einige Radius von des Benutzers Blicke Vektor. Beachten Sie, dass dies auch angewendet wird, wenn des Benutzers Hologramme aus einem schräg oder glancing Winkel anzeigt.
* **Schwerpunkt** -Aufmerksamkeit auf Objekte oder Interaktionspunkte kontrastierenden Farben, Helligkeit und Beleuchtung. Eine ausführlichere Betrachtung Beleuchtung-Methoden in Storytelling, finden Sie unter [Pixel Cinematography - Ansatz ein Beleuchtung Computergrafiken](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf).

![Verwendung von Farbe, die Betonung für Storytelling-Elemente, die hier gezeigten in einer Szene aus Fragmenten anzeigen.](images/640px-fragments.jpg)<br>
*Verwendung von Farben Betonung für Storytelling-Elemente, die hier gezeigten in einer Szene von anzuzeigenden [Fragmente](https://www.microsoft.com/p/fragments/9nblggh5ggm8).*

## <a name="see-also"></a>Siehe auch
* [Farbliche Trennung](hologram-stability.md#color-separation)
* [Holograms](hologram.md)
* [Microsoft-Design Language - Farbe](https://www.microsoft.com/design/color)
* [Universelle Windows-Plattform - Farbe](https://docs.microsoft.com/windows/uwp/style/color)
