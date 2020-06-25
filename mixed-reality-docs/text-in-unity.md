---
title: Text in Unity
description: Zum Anzeigen von Text in Unity gibt es zwei Arten von Textkomponenten, die Sie verwenden können – UI Text und 3D Text Mesh.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, Design, Steuerelemente, Schriftart, Typografie, UI, UX
ms.openlocfilehash: 8662ff8a8e1e99455354392d7dc852feb1fe1589
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345710"
---
# <a name="text-in-unity"></a>Text in Unity

Text ist eine der wichtigsten Komponenten in Holographic apps. Zum Anzeigen von Text in Unity gibt es drei Arten von Textkomponenten, die Sie verwenden können – UI Text, 3D Text Mesh und Text Mesh pro. Standardmäßig werden UI-Text und 3D-textmesh verschwommen und sind zu groß. Sie müssen einige Variablen optimieren, um scharfen, hochwertigen Text zu erhalten, der über eine verwaltbare Größe in hololens verfügt. Wenn Sie einen Skalierungsfaktor anwenden, um bei der Verwendung von UI-Text und 3D-Text Gitter Komponenten ordnungsgemäße Dimensionen zu erzielen, erzielen Sie eine bessere renderingqualität.

![So erhalten Sie einen scharfen und schönen Text](images/hug-text-02-640px.png)<br>
*Unscharfe Standardtext in Unity*

## <a name="working-with-unitys-3d-text-text-mesh-and-ui-text"></a>Arbeiten mit dem 3D-Text (textmesh) von Unity und dem Benutzeroberflächen Text

Unity geht davon aus, dass alle neuen Elemente, die einer Szene hinzugefügt werden, eine Unity-Einheit oder eine 100%-Transformations Skala sind, die in hololens ungefähr 1 Meter übersetzt. Im Fall von Schriftarten kommt das umgebende Feld für eine 3D-textmesh standardmäßig bei ungefähr 1 Meter Höhe ins Spiel.

![Arbeiten mit Schriftarten in Unity](images/640px-hug-text-03.png)<br>
*Der standardmäßige Unity 3D-Text (textmesh) belegt eine Unity-Einheit, die 1 Meter beträgt.*

<br>
Die meisten visuellen Designer verwenden Punkte, um Schriftgrößen in der realen Welt zu definieren. Es gibt ungefähr 2835 (2, 834.645666399962) Punkte in 1 Meter. Basierend auf der Punkt System Konvertierung in 1 Meter und dem Standard-Schrift Grad des Unity-Text Netzes von 13 ist die einfache Math von 13 dividiert durch 2835 auf 0,0046 (0.004586111116), was eine gute Standardskala für den Einstieg bietet (einige können auf 0,005). Wenn Sie das Textobjekt oder den Container auf diese Werte skalieren, ist nicht nur die 1:1-Konvertierung von Schriftgrößen in einem Entwurfs Programm zulässig, sondern es wird auch ein Standard bereitstellt, sodass Sie die Konsistenz im gesamten Prozess aufrechterhalten können.

![Unity 3D-textmesh mit unterschiedlichen Schrift Graden](images/Text_In_Unity_Measurements1.png)<br>
*Skalieren von Werten für den Unity 3D-Text und den UI-Text*

<br>

![Unity 3D-textmesh mit unterschiedlichen Schrift Graden](images/hug-text-05-1000px.png)<br>
*Unity 3D-textmesh mit optimierten Werten*

<br>
Wenn eine Benutzeroberfläche oder ein Canvas-basiertes Textelement einer Szene hinzugefügt wird, ist die Größen Differenz noch größer. Die Unterschiede in den beiden Größen liegen bei etwa 1000%, wodurch der Skalierungsfaktor für UI-basierte Textkomponenten auf 0,00046 (0.0004586111116) oder 0,0005 für den gerundeten Wert gebracht wird.

![Unity-UI-Text mit unterschiedlichen dynamischen Pixeln pro Einheits Werten](images/hug-text-04-1000px.png)<br>
*Unity-UI-Text mit optimierten Werten*

<br>

>[!NOTE]
>Der Standardwert einer beliebigen Schriftart kann von der Textur Größe der Schriftart oder der Art und Weise, in der die Schriftart in Unity importiert wurde, beeinflusst werden. Diese Tests wurden basierend auf der Standard Schriftart Arial in Unity sowie einer anderen importierten Schriftart ausgeführt.

## <a name="working-with-text-mesh-pro"></a>Arbeiten mit Text Mesh pro

Mit dem Text Mesh pro von Unity können Sie die textrenderingqualität sichern. Es unterstützt ganz knackige Text Gliederungen unabhängig von der Entfernung mithilfe der SDF-Technik [(signed Distance Field)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) . Mit der gleichen Berechnungsmethode, die wir oben für das 3D-textmesh und den UI-Text verwendet haben, können wir die richtigen Skalierungs Werte finden, die mit herkömmlichen typografischen Punkten verwendet werden. Da die 3D-textzeibschriftart mit der Größe 36 eine Begrenzungs Größe von 2,5 Unity-Einheiten (2,5 Mio.) aufweist, können wir den Skalierungs Wert 0,005 verwenden, um die Punktgröße zu erhalten. Der Text Mesh pro im UI-Menü verfügt über eine standardmäßige Begrenzungs Größe von 25 Unity-Einheiten (25M). Dadurch erhalten wir 0,0005 für den Skalierungs Wert.

![Unity 3D-textmesh mit unterschiedlichen Schrift Graden](images/Text_In_Unity_Measurements2.png)<br>
*Skalieren von Werten für den Unity 3D-Text und den UI-Text*

## <a name="recommended-text-size"></a>Empfohlene Textgröße
Wie Sie erwarten, sehen die typgrößen, die wir auf einem PC oder Tablet-Gerät verwenden (normalerweise zwischen 12 – 32pt), in einer Entfernung von 2 Metern sehr klein aus. Es hängt von den Merkmalen der einzelnen Schriftart ab, aber im Allgemeinen liegen die empfohlenen minimalen Anzeige Winkel und die Schrift Höhe für die Lesbarkeit um 0,35 °-0,4 °/12.21-13.97mm basierend auf unseren Forschungsstudien für Benutzer. Der oben eingeführte Skalierungsfaktor liegt bei ungefähr 35-40 PT. 

Für die Near-Interaktion bei 0.45 m (45cm) ist der Anzeige Winkel der minimal lesbaren Schriftart und die Höhe 0,4 °-0,5 °/3.14 – 3,9 mm. Der oben eingeführte Skalierungsfaktor liegt bei ungefähr 9-12pt.

![Inhalte in naher und weitem Interaktion im Bereich von ](images/typography-distance-1000px.jpg)
 *nahezu-und weitem Interaktionen*

### <a name="the-minimum-legible-font-size"></a>Die minimale lesbare Schriftgröße
| Distance | Anzeige Winkel | Texthöhe | Schriftgrad |
|---------|---------|---------|---------|
| 45cm (direkte Manipulations Distanz) | 0,4 °-0,5 ° | 3.14 – 3,9 mm | 8,9 – 11.13 PT |
| 2 min | 0,35 °-0,4 ° | 12.21 – 13.97 mm | 34.63-39.58 PT |


### <a name="the-comfortably-legible-font-size"></a>Die bequem lesbare Schriftgröße
| Distance | Anzeige Winkel | Texthöhe | Schriftgrad |
|---------|---------|---------|---------|
| 45cm (direkte Manipulations Distanz) | 0,65 °-0,8 ° | 5.1-6.3 mm | 14.47-17,8 pt |
| 2 min | 0,6 °-0,75 ° | 20,9-26.2 mm | 59,4-74,2 pt |

In den meisten Fällen funktioniert Segoe UI (die Standard Schriftart für Windows). Vermeiden Sie jedoch die Verwendung von hell-oder semilight-Schriftfamilien in geringer Größe, da Dünne vertikale Striche vibrieren und die Lesbarkeit beeinträchtigen. Moderne Schriftarten mit ausreichender Strichstärke funktionieren gut. Beispielsweise sind die Werte von Helvetica und Arial großartig und in hololens mit regulären oder fetten Gewichtungen sehr lesbar.


![Anzeigen des ](images/Text_In_Unity_ViewingAngle.jpg)
 *Abstands, des Winkels und der Texthöhe* des Winkels

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a>Sharp-Text-renderingqualität mit der richtigen Dimension

Basierend auf diesen Skalierungsfaktoren haben wir [Text präfaben mit UI-Text und 3D-textmesh](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)erstellt. Entwickler können diese Prefabs verwenden, um einen scharfen Text und eine konsistente Schriftgröße zu erhalten.

![Sharp-Text-renderingqualität mit der richtigen Dimension](images/hug-text-06-1000px.png)<br>
*Sharp-Text-renderingqualität mit der richtigen Dimension*

## <a name="shader-with-occlusion-support"></a>Shader mit Okklusions Unterstützung

Das Standard Schriftmaterial von Unity unterstützt keine Okklusion. Aus diesem Grund wird der Text hinter den Objekten standardmäßig angezeigt. Wir haben einen einfachen [Shader eingefügt, der die Okklusion unterstützt](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader). Die folgende Abbildung zeigt den Text mit dem Standard Schriftmaterial (links) und den Text mit der richtigen oksion (right).

![Shader mit Okklusions Unterstützung](images/hug-text-07-1000px.png)<br>
*Shader mit Okklusions Unterstützung*


## <a name="see-also"></a>Siehe auch
* [Textvorfab im mrtk](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)
* [Typografie](typography.md)

 
