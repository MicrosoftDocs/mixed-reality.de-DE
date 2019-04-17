---
title: Text in Unity
description: Zum Anzeigen von Text in Unity, es gibt zwei Arten von Textkomponenten, die Sie verwenden können – Benutzeroberflächentext und 3D Mesh-Text.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Entwurf, Steuerelemente, Schriftart, Typografie, Benutzeroberfläche, Ux
ms.openlocfilehash: 02f282ab80a44190d21d2dadefeb7a624c862d04
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596363"
---
# <a name="text-in-unity"></a>Text in Unity

Text ist eine der wichtigsten Komponenten in holographic-apps. Zum Anzeigen von Text in Unity, es gibt zwei Arten von Textkomponenten, die Sie verwenden können – Benutzeroberflächentext und 3D Mesh-Text. Standardmäßig müssen sie verschwommen angezeigt und ist zu groß. Sie müssen einige Variablen um sharp, qualitativ hochwertige Text abzurufen, denen eine verwaltbare Größe in HoloLens optimieren. Durch Anwenden von Skalierungsfaktor richtige Dimensionen rufen Sie bei Verwendung der Benutzeroberflächentext und 3D-Komponenten Mesh-Text, erzielen Sie bessere Renderqualität.

![Zum Abrufen von Spitzen und ansprechende text](images/hug-text-02-640px.png)<br>
*Unscharf Standardtext in Unity*

## <a name="working-with-fonts-in-unity"></a>Verwenden von Schriftarten in Unity

Unity wird davon ausgegangen, dass alle neuen Elemente hinzugefügt, die in einer Szene sind 1 Einheit von Unity in Größe und Transformationsskalierung an 100 %-, die in etwa 1 Meter Umkreis für HoloLens übersetzt. Im Fall von Schriftarten ist das umgebende Feld für eine 3D TextMesh standardmäßig in Höhe von etwa 1 Meter.

![Verwenden von Schriftarten in Unity](images/640px-hug-text-03.png)<br>
*Unity-Standardtext belegt 1 Unity-Einheit handelt es sich 1 Meter Umkreis um*

<br>
Die meisten visuelle Designern verwenden Punkte, um Schriftgrade Ihren Bedürfnissen entsprechend in der Praxis zu definieren. Es gibt ungefähr 2835 (2,834.645666399962) Punkte in 1 Meter Umkreis um. Basierend auf den Punkt-System-Konvertierung in 1 Meter Umkreis um und Unity Text Mesh Standardschriftgrad 13, die einfache mathematische 13 geteilt durch 2835 Equals 0.0046 (0.004586111116 exakt sein) bietet eine gute standard Skalierung für den Einstieg (einige möchten möglicherweise auf 0,005 gerundet). Skalieren den Text-Objekt oder die Container an diesen Werten lässt nicht nur für die 1:1-Konvertierung der Schriftart in einem Designprogramm Größen, bietet jedoch auch einen Standard, sodass Sie die Konsistenz im gesamten auf Ihre Anwendung oder Ihr Spiel verwalten können.

![Unity 3D Text Netz mit verschiedene Schriftgrößen](images/hug-text-05-1000px.png)<br>
*Unity 3D Text Netz mit optimierten Werte*

<br>
Beim Hinzufügen ein basierend Textelement-Benutzeroberfläche oder die Zeichenfläche zu einer Szene ist die Größe unterschiedlichen führen zu immer noch größer. Die Unterschiede bei der die beiden Größen ist ungefähr 1000 %, der den Skalierungsfaktor für UI-basierten Textkomponenten 0.00046 (0.0004586111116 exakt sein) bringen würde oder 0,0005 für den gerundeten Wert.

![Unity-Benutzeroberflächentext mit anderen dynamischen Pixeln Werte pro Einheit](images/hug-text-04-1000px.png)<br>
*Unity-Benutzeroberflächentext mit optimierten Werten*

<br>

>[!NOTE]
>Der Standardwert, der alle Schriftarten kann beeinträchtigt werden, durch die Texturgröße, Schriftart oder wie die Schriftart in Unity importiert wurde. Diese Tests wurden für die Standard-Schriftart Arial in Unity als auch eine andere importierte Schriftart Basis ausgeführt.

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a>Scharfen Sie Renderqualität von Text mit der richtigen dimension

Basierend auf diesen Skalierungsfaktoren wurde erstellt, [zwei Prefabs - Benutzeroberflächentext und 3D Text Mesh](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Prefabs). Entwickler können diese prefabs (Vorlagen) verwenden, zum Abrufen von scharfes Text- und konsistente Schriftgrad.

![Scharfen Sie Renderqualität von Text mit der richtigen dimension](images/hug-text-06-1000px.png)<br>
*Scharfen Sie Renderqualität von Text mit der richtigen dimension*

## <a name="shader-with-occlusion-support"></a>Shader mit verdecken-Unterstützung

Verdecken unterstützt von Unity-Standardmaterial Schriftart nicht. Aus diesem Grund sehen Sie den Text hinter der Objekte in der Standardeinstellung. Wir haben ein einfaches enthalten [Shader, der die verdecken unterstützt](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Shaders). Die folgende Abbildung zeigt den Text mit Standardmaterial Schriftart (links) und den Text, mit der richtigen verdecken (rechts).

![Shader mit verdecken-Unterstützung](images/hug-text-07-1000px.png)<br>
*Shader mit verdecken-Unterstützung*

## <a name="recommended-type-size"></a>Empfohlene Datentyp, Größe

Wie zu erwarten können, geben Sie die Größen, die wir auf einem PC oder Tablet-Gerät (in der Regel zwischen 12: 32pt) finden Sie in einem Abstand von 2 Metern relativ klein verwenden. Es hängt die Merkmale der einzelnen Schriftarten, aber im Allgemeinen ist die empfohlene minimale Typgröße für bessere Lesbarkeit ohne Stroke Vibration 30pt, basierend auf den oben vorgestellten Skalierungsfaktor. Wenn Ihre app in einem näher Abstand verwendet werden soll, können der kleinere Typ verwendet werden. Die ausgewählte Schriftart funktioniert auch in den meisten Fällen Segoe UI (Dies ist die Standardschriftart für Windows). Jedoch nicht für die typgrößen unter 42 pt Light "oder" Semi helle Schriftarten verwenden, da thin vertikalen Strichen Vibrieren werden, und es wird die Lesbarkeit beeinträchtigt. Moderne Schriftarten mit genügend Strichstärke gut funktionieren. Z. B. Helvetica Arial symbolstile suchen und in HoloLens mit regelmäßigen oder fett Gewichtungen sehr lesbar sind.

![Empfohlene Datentyp, Größe](images/hug-text-08-1000px.png)<br>
*Beispiel für einen Einstieg*

## <a name="see-also"></a>Siehe auch
* [Text-Prefab in die MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Prefabs)
* [Beispiel-Textlayout prefab und Szene](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX/Scenes)
* [Typography](typography.md)

 
