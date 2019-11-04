---
title: Typografie
description: Text ist ein wichtiges Element zum Bereitstellung von Informationen in ihrer App-Funktion.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Gemischte Windows-Realität, Design, Stil, Schriftart, Typografie, UI, Benutzeroberfläche
ms.openlocfilehash: 9664d355e941d800ac1ac862860fc5889b6b7686
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437421"
---
# <a name="typography"></a>Typografie

![Typografiebeispiel in hololens](images/typography-cover.png)<br>


Text ist ein wichtiges Element zum Bereitstellung von Informationen in ihrer App-Funktion. Genau wie bei Typografie auf 2D-Bildschirmen ist das Ziel, klar und lesbar zu sein. Aufgrund des dreidimensionalen Aspekts von Mixed Reality bietet sich die Chance eines noch größeren Einflusses auf den Text und das allgemeine Benutzererleben.

Wenn wir uns mit dem Typ in 3D beschäftigen, werden wir in der Regel den Text "extrudierte, volumetrische 3D" betrachten. Mit Ausnahme einiger Logotyp Entwürfe und einiger anderer eingeschränkter Anwendungen wird der Text in der Textform durch den Text der Lesbarkeit tendenziell herabgestuft. Obwohl wir Erfahrungen für 3D entwerfen, verwenden wir 2D für den Typ, da es besser lesbar und leichter lesbar ist.

In hololens wird Type mit holograms erstellt, wobei Light auf Grundlage des Additiven Farbsystems verwendet wird. Ebenso wie andere Hologramme kann der Typ in der eigentlichen Umgebung abgelegt werden, in der er von einem beliebigen Winkel aus weltweit gesperrt und beobachtet werden kann. Der [parameterx](https://en.wikipedia.org/wiki/Parallax) -Effekt zwischen dem Typ und der Umgebung erhöht auch die Tiefe der Umgebung.

## <a name="typography-in-mixed-reality"></a>Typografie in gemischter Realität

Typografische Regeln in gemischter Realität unterscheiden sich nicht von anderen. Der Text in der physischen Welt und in der virtuellen Welt muss lesbar und lesbar sein. Der Text kann sich auf einer Wand oder einer übergeordneten Zeichen für ein physisches Objekt befinden. Möglicherweise ist Sie mit einer digitalen Benutzeroberfläche unverankert. Unabhängig vom Kontext wenden wir dieselben typografischen Regeln für Lese-und Erkennungs Vorgänge an.

### <a name="create-clear-hierarchy"></a>Clear-Hierarchie erstellen

Buildkontrast und Hierarchie mit unterschiedlichen typgrößen und Gewichtungen. Durch die Definition einer typrampe und deren anschließende Verwendung in der gesamten APP wird eine gute Benutzer Leistung mit der konsistenten Informationshierarchie bereitgestellt.

Beispiele für ![typrampen](images/typography-ramp-1000px.jpg)<br>
*Definieren Sie Ihre typrampe, und befolgen Sie Sie in der gesamten app.*

### <a name="limit-your-fonts"></a>Schriftarten einschränken

Vermeiden Sie die Verwendung von mehr als zwei unterschiedlichen Schriftfamilien in einem einzigen Kontext. Dies führt zu einer Unterbrechung der Stimmung und Konsistenz ihrer Benutzeroberflächen und erschwert die Nutzung von Informationen. Da die Informationen in hololens oberhalb der physischen Umgebung überlagert werden, wird die Umgebung durch die Verwendung zu vieler Schriftart Stile herabgestuft. Segoe UI ist die Schriftart für alle digitalen Microsoft-Entwürfe. Sie wird in der Windows Mixed Reality-Shell konsistent verwendet. Sie können die Segoe UI Schriftart Datei von der [Windows Design Toolkit-Seite](https://docs.microsoft.com/windows/uwp/design-downloads/)herunterladen.

[Weitere Informationen zur Segoe UI Schriftart](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>Vermeiden von Thin Font-Gewichtungen

Vermeiden Sie die Verwendung von hellen oder einfachen Schrift Gewichtungen für typgrößen unter 42 PT, da Dünne vertikale Striche die Lesbarkeit beeinträchtigen und abschwächen. Moderne Schriftarten mit ausreichender Strichstärke funktionieren gut. Beispielsweise sind die Werte von Helvetica und Arial in hololens mit regulären oder fetten Gewichtungen sehr lesbar.

### <a name="color"></a>Farbe

Da die Hologramme in hololens mit einem Additiven Lichtsystem erstellt werden, ist weißer Text sehr lesbar. Sie finden Beispiele für weißen Text im Startmenü und in der APP-Leiste. Obwohl weißer Text ohne Rückwand in hololens gut funktioniert, könnte ein komplexer physischer Hintergrund dazu führen, dass der Typ schwer lesbar ist. Um den Fokus des Benutzers zu verbessern und die Ablenkung von einem physischen Hintergrund zu minimieren, empfehlen wir die Verwendung von weißem Text auf einem dunklen oder farbigen Hintergrund.

<br>


![empfehlen wir die Verwendung von weißem Text auf einem dunklen oder farbigen Hintergrund.](images/typography-whiteonblack2-1000px.jpg)
*Beispiele für weißen Text auf einem dunklen oder farbigen Hintergrund.*
<br>

Um dunklen Text zu verwenden, sollten Sie einen hellen Backplate verwenden, um ihn lesbar zu machen. In Additiven Farbsystemen wird schwarz als transparent angezeigt. Dies bedeutet, dass der schwarze Text ohne ein farbiges Backplate nicht angezeigt werden kann.

:::row:::
    :::column:::
        ![schwarze Textbeispiele](images/typography-whiteonblack.png)<br>
        *Beispiele für weiß in schwarz und schwarz bei weißem Text*<br>
    :::column-end:::
    :::column:::
        ![schwarze Textbeispiele](images/640px-typography-blackonwhite.jpg)<br>
        *Beispiele für blacktext in den System-apps: Store und Einstellungen*<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="recommended-font-size"></a>Empfohlene Schriftgröße

Wie Sie erwarten, sehen die typgrößen, die wir auf einem PC oder Tablet-Gerät verwenden (normalerweise zwischen 12 – 32pt), in einer Entfernung von 2 Metern sehr klein aus. Es hängt von den Merkmalen der einzelnen Schriftart ab, aber im Allgemeinen liegen die empfohlenen minimalen Anzeige Winkel und die Schrift Höhe für die Lesbarkeit um 0,35 °-0,4 °/12.21-13.97mm basierend auf unseren Forschungsstudien für Benutzer. Der Skalierungsfaktor für den in [Text auf der Unity](text-in-unity.md) -Seite eingeführte Skalierungsfaktor ist ungefähr 35-40 PT. 

Für die Near-Interaktion bei 0.45 m (45cm) ist der Anzeige Winkel der minimal lesbaren Schriftart und die Höhe 0,4 °-0,5 °/3.14 – 3,9 mm. Der Skalierungsfaktor für den in [Unity](text-in-unity.md)eingeführten Skalierungsfaktor liegt bei ungefähr 9-12pt.

![Near-und Far-Interaktionsbereich](images/typography-distance-1000px.jpg)
*Inhalt in nahezu-und weitem Interaktions Bereich*

### <a name="the-minimum-legible-font-size"></a>Die minimale lesbare Schriftgröße
| Flüge | Anzeige Winkel | Texthöhe | Schrift Grad * * |
|---------|---------|---------|---------|
| 45cm (direkte Manipulations Distanz) | 0,4 °-0,5 ° | 3.14 – 3,9 mm | 8,9 – 11.13 PT |
| 2 min | 0,35 °-0,4 ° | 12.21 – 13.97 mm | 34.63-39.58 PT |


### <a name="the-comfortably-legible-font-size"></a>Die bequem lesbare Schriftgröße
| Flüge | Anzeige Winkel | Texthöhe | Schrift Grad * * |
|---------|---------|---------|---------|
| 45cm (direkte Manipulations Distanz) | 0,65 °-0,8 ° | 5.1-6.3 mm | 14.47-17,8 pt |
| 2 min | 0,6 °-0,75 ° | 20,9-26.2 mm | 59,4-74,2 pt |


In den meisten Fällen funktioniert Segoe UI (die Standard Schriftart für Windows). Vermeiden Sie jedoch die Verwendung von hell-oder semilight-Schriftfamilien in geringer Größe, da Dünne vertikale Striche vibrieren und die Lesbarkeit beeinträchtigen. Moderne Schriftarten mit ausreichender Strichstärke funktionieren gut. Beispielsweise sind die Werte von Helvetica und Arial großartig und in hololens mit regulären oder fetten Gewichtungen sehr lesbar.

**Ausführlichere Informationen zur Berechnung der Textgröße in Unity finden Sie unter [Text in Unity](text-in-unity.md) .**

![Anzeige Winkel](images/Text_In_Unity_ViewingAngle.jpg)
*Anzeigen der Entfernung, des Winkels und der Texthöhe*

<br>

---

## <a name="resources"></a>Ressourcen

:::row:::
    :::column:::
    ### <a name="segoe-fontshttpsdownloadmicrosoftcomdownload1bc1bcf071a-78ee-4968-acbe-15461c274b61segoe20fonts20v1705zipbr"></a>[Schriftarten](https://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)<br>
    (ZIP-Datei)<br>
    ### <a name="hololens-fonthttpsdownloadmicrosoftcomdownload38d38d659e2-4b9c-413a-b2e7-1956181dc427hololens20fontzipbr"></a>[Hololens-Schriftart](https://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)<br>
    (ZIP-Datei)<br>
    <br>
    *Bild: die Schriftart hololens gibt Ihnen die Symbol Symbole, die in der gemischten Realität von Windows verwendet werden.*
    :::column-end:::
        :::column:::
        ![Die Schriftart hololens gibt Ihnen die Symbol Symbole, die in der gemischten Realität von Windows verwendet werden.](images/hololensmdl2symbols.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="see-also"></a>Weitere Informationen:
* [Text in Unity](text-in-unity.md)
* [Farbe, Licht und Materialien](color,-light-and-materials.md)
