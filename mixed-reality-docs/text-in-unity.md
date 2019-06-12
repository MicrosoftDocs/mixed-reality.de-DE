---
title: Text in Unity
description: Zum Anzeigen von Text in Unity, es gibt zwei Arten von Textkomponenten, die Sie verwenden können – Benutzeroberflächentext und 3D Mesh-Text.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, Entwurf, Steuerelemente, Schriftart, Typografie, Benutzeroberfläche, Ux
ms.openlocfilehash: 7d40db2e0571e835e28e444c7921e1a086800936
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829973"
---
# <a name="text-in-unity"></a>Text in Unity

Text ist eine der wichtigsten Komponenten in holographic-apps. Zum Anzeigen von Text in Unity, es gibt drei Arten von Textkomponenten, die Sie verwenden können, Benutzeroberflächentext, 3D Mesh-Text und Text Mesh Pro. Standardmäßig werden Benutzeroberflächentext und 3D Text Mesh unscharf angezeigt und ist zu groß. Sie müssen einige Variablen um sharp, qualitativ hochwertige Text abzurufen, denen eine verwaltbare Größe in HoloLens optimieren. Durch Anwenden von Skalierungsfaktor richtige Dimensionen rufen Sie bei Verwendung der Benutzeroberflächentext und 3D-Komponenten Mesh-Text, erzielen Sie bessere Renderqualität.

![Zum Abrufen von Spitzen und ansprechende text](images/hug-text-02-640px.png)<br>
*Unscharf Standardtext in Unity*

## <a name="working-with-unitys-3d-texttext-mesh-and-ui-text"></a>Arbeiten mit Unity 3D-Text (Text-Mesh) und Benutzeroberflächen-Text

Unity wird davon ausgegangen, dass alle neuen Elemente hinzugefügt, die in einer Szene sind 1 Einheit von Unity in Größe und Transformationsskalierung an 100 %-, die in etwa 1 Meter Umkreis für HoloLens übersetzt. Im Fall von Schriftarten ist das umgebende Feld für eine 3D TextMesh standardmäßig in Höhe von etwa 1 Meter.

![Verwenden von Schriftarten in Unity](images/640px-hug-text-03.png)<br>
*Unity 3D Standardtext (Text-Mesh) belegt 1 Unity-Einheit handelt es sich 1 Meter Umkreis um*

<br>
Die meisten visuelle Designern verwenden Punkte, um Schriftgrade Ihren Bedürfnissen entsprechend in der Praxis zu definieren. Es gibt ungefähr 2835 (2,834.645666399962) Punkte in 1 Meter Umkreis um. Basierend auf den Punkt-System-Konvertierung in 1 Meter Umkreis um und Unity Text Mesh Standardschriftgrad 13, die einfache mathematische 13 geteilt durch 2835 Equals 0.0046 (0.004586111116 exakt sein) bietet eine gute standard Skalierung für den Einstieg (einige möchten möglicherweise auf 0,005 gerundet). Skalieren den Text-Objekt oder die Container an diesen Werten lässt nicht nur für die 1:1-Konvertierung der Schriftart in einem Designprogramm Größen, aber es ist auch ein Standard, damit Sie Konsistenz in Ihrer Umgebung verwalten können.

![Unity 3D Text Netz mit verschiedene Schriftgrößen](images/Text_In_Unity_Measurements1.png)<br>
*Skalieren Sie Werte für die Unity-3D-Text und Benutzeroberflächentexte*

![Unity 3D Text Netz mit verschiedene Schriftgrößen](images/hug-text-05-1000px.png)<br>
*Unity 3D Text Netz mit optimierten Werte*

<br>
Beim Hinzufügen ein basierend Textelement-Benutzeroberfläche oder die Zeichenfläche zu einer Szene ist die Größe unterschiedlichen führen zu immer noch größer. Die Unterschiede bei der die beiden Größen ist ungefähr 1000 %, der den Skalierungsfaktor für UI-basierten Textkomponenten 0.00046 (0.0004586111116 exakt sein) bringen würde oder 0,0005 für den gerundeten Wert.

![Unity-Benutzeroberflächentext mit anderen dynamischen Pixeln Werte pro Einheit](images/hug-text-04-1000px.png)<br>
*Unity-Benutzeroberflächentext mit optimierten Werten*

<br>

>[!NOTE]
>Der Standardwert, der alle Schriftarten kann beeinträchtigt werden, durch die Texturgröße, Schriftart oder wie die Schriftart in Unity importiert wurde. Diese Tests wurden für die Standard-Schriftart Arial in Unity als auch eine andere importierte Schriftart Basis ausgeführt.

## <a name="working-with-text-mesh-pro"></a>Arbeiten mit Text Mesh Pro

Mit Unity Text Mesh Pro können Sie die Renderqualität Text sichern. Unterstützt schärfer Textkontur unabhängig von der Entfernung mithilfe der [SDF (Signed Abstand Feld)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) Verfahren. Verwenden die gleiche Berechnungsmethode, die wir oben für die Mesh-3D Text und Benutzeroberflächentexte verwendet, finden wir richtigen Skalierungswerte, herkömmlichen typografischen verwenden. Da die 3D Text Mesh Pro Standardschriftart mit der Größe 36 das umgebende von 2,5 Unity Unit(2.5m) zeigt, können wir Skalierungswert 0,005 verwenden, den Schriftgrad zu verwenden. Mit dem Text Mesh Pro im Menü "Benutzeroberfläche" verfügt über den umgebenden Größe von 25 Unity Unit(25m). Dadurch erhalten Sie 0,0005 für die Skalierung Wert.

![Unity 3D Text Netz mit verschiedene Schriftgrößen](images/Text_In_Unity_Measurements2.png)<br>
*Skalieren Sie Werte für die Unity-3D-Text und Benutzeroberflächentexte*

## <a name="recommended-text-size"></a>Empfohlene Textgröße
Wie zu erwarten können, geben Sie die Größen, die wir auf einem PC oder Tablet-Gerät (in der Regel zwischen 12: 32pt) finden Sie in einem Abstand von 2 Metern relativ klein verwenden. Es hängt die Merkmale der einzelnen Schriftarten, aber der empfohlenen Mindestgröße anzeigen Winkel und die Schriftarthöhe zur besseren Lesbarkeit im Allgemeinen sind, um basierend auf unseren Untersuchungen Benutzerstudien 0.35°-0.4°/12.21-13.97mm. Es geht 35-40pt mit den oben vorgestellten Skalierungsfaktor. 

Für die nahezu die Interaktion auf 0.45m(45cm), Betrachtungswinkel für die minimale lesbar Schriftart und die Höhe sind 0,4 °-0,5 ° / 3.14 – 3.9 mm. Es geht 9-12pt mit den oben vorgestellten Skalierungsfaktor.

![Naher und viel Interaktion Bereich](images/typography-distance-1000px.jpg)
*am in der Nähe von Inhalt und weit Interaktion-Bereich*

### <a name="the-minimum-legible-font-size"></a>Der minimale Schriftgrad für lesbar
| Entfernung | Betrachtungswinkel | Texthöhe | Schriftgrad |
|---------|---------|---------|---------|
| 45cm (direkte Bearbeitung Abstand) | 0.4°-0.5° | 3.14 – 3.9 mm | 8.9 – 11.13pt |
| 2 Min. | 0.35°-0.4° | 12.21 – 13.97 mm | 34.63-39.58pt |


### <a name="the-comfortably-legible-font-size"></a>Der bequem lesbar Schriftgrad
| Entfernung | Betrachtungswinkel | Texthöhe | Schriftgrad |
|---------|---------|---------|---------|
| 45cm (direkte Bearbeitung Abstand) | 0.65°-0.8° | 5.1-6.3 mm | 14.47-17.8pt |
| 2 Min. | 0.6°-0.75° | 20,9-26,2 mm | 59.4-74.2pt |

Segoe UI (Dies ist die Standardschriftart für Windows) funktioniert gut in den meisten Fällen. Vermeiden Sie jedoch die Verwendung von Licht oder hell Semi-Schriftfamilien klein, da die dünne vertikale Striche Vibrieren werden und es werden die Lesbarkeit beeinträchtigt. Moderne Schriftarten mit genügend Strichstärke gut funktionieren. Z. B. Helvetica Arial symbolstile suchen und in HoloLens mit regelmäßigen oder fett Gewichtungen sehr lesbar sind.


![Anzeigen von Winkel](images/Text_In_Unity_ViewingAngle.jpg)
*Abstand und Winkel Text Höhe anzeigen*

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a>Scharfen Sie Renderqualität von Text mit der richtigen dimension

Basierend auf diesen Skalierungsfaktoren wurde erstellt, [Text Prefabs mit Benutzeroberflächentext und 3D Text Mesh](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text). Entwickler können diese prefabs (Vorlagen) verwenden, zum Abrufen von scharfes Text- und konsistente Schriftgrad.

![Scharfen Sie Renderqualität von Text mit der richtigen dimension](images/hug-text-06-1000px.png)<br>
*Scharfen Sie Renderqualität von Text mit der richtigen dimension*

## <a name="shader-with-occlusion-support"></a>Shader mit verdecken-Unterstützung

Verdecken unterstützt von Unity-Standardmaterial Schriftart nicht. Aus diesem Grund sehen Sie den Text hinter der Objekte in der Standardeinstellung. Wir haben ein einfaches enthalten [Shader, der die verdecken unterstützt](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader). Die folgende Abbildung zeigt den Text mit Standardmaterial Schriftart (links) und den Text, mit der richtigen verdecken (rechts).

![Shader mit verdecken-Unterstützung](images/hug-text-07-1000px.png)<br>
*Shader mit verdecken-Unterstützung*


## <a name="see-also"></a>Siehe auch
* [Text-Prefab in die MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)
* [Typografie](typography.md)

 
