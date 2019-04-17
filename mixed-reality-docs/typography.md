---
title: Typografie
description: Text ist ein wichtiges Element für die Übermittlung von Informationen in Ihre app-Erfahrung.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Entwurf, Format, Schriftart, Typografie, Benutzeroberfläche, ux
ms.openlocfilehash: b4bac35cbc412ec7102748350c2f5c1e236c2f7d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596045"
---
# <a name="typography"></a>Typografie

Text ist ein wichtiges Element für die Übermittlung von Informationen in Ihre app-Erfahrung. Genauso wie Typografie in 2D Bildschirmen steht das Ziel löschen und gelesen werden. Mit der dreidimensionale Aspekt von mixed Reality, besteht die Möglichkeit, den Text und der allgemeine Benutzer auswirken Erfahrung in eine noch größere Möglichkeit.

![Typografie-Beispiel in HoloLens](images/640px-typography-hero2.jpg)<br>
*Typografie-Beispiel in HoloLens*

Wenn wir zu Typen in 3D sprechen, sind tendenziell wir projizierten, volumetrische 3D-Text vorstellen. Projizierten Text tendenziell, mit Ausnahme einiger Arealstaaten dieser Entwürfe und einigen andere Anwendungen beschränkt die Lesbarkeit des Texts zu beeinträchtigen. Obwohl wir Erfahrungen für 3D entwerfen, verwenden wir 2D für den Typ, da es besser lesbar und einfacher zu lesen ist.

In HoloLens ist Typ mit Hologramme mithilfe von Licht, die basierend auf dem System additiv Farbe erstellt. Genau wie andere Hologramme kann Typ in der eigentlichen Umgebung platziert werden, wo sie Welt gesperrt und aus jedem Winkel beobachtet werden kann. Die [Parallax](https://en.wikipedia.org/wiki/Parallax) Auswirkung zwischen dem Datentyp und die Umgebung sowie die Tiefe auf die Benutzeroberfläche.

## <a name="typography-in-mixed-reality"></a>Typografie in mixed reality

Typografische Regeln in mixed Reality unterscheiden sich nicht von der an anderer Stelle. Text in der realen Welt und die virtuelle Welt muss lesbar und besser lesbar zu sein. Text kann an einer Wand oder auf ein physisches Objekt angezeigt. Zusammen mit einer digitalen Benutzeroberfläche kann schwimmen sein. Unabhängig vom Kontext wenden wir dieselben typografischen Regeln für das Lesen und Anerkennung.

### <a name="create-clear-hierarchy"></a>Erstellen Sie klare Hierarchie

Erstellen Sie mit verschiedenen Größen und Gewichtungen Kontrast und die Hierarchie ein. Definieren einen Typ Ramp, und befolgen sie über die app-Umgebung stellt eine hervorragende benutzerumgebung mit konsistente Informationen bereit.

![Beispiele für ramp](images/typography-ramp-1000px.jpg)<br>
*Beispiele für ramp*

### <a name="limit-your-fonts"></a>Beschränken Sie Ihre Schriftarten

Vermeiden Sie die Verwendung von mehr als zwei unterschiedliche Schriftfamilien in einem einzelnen Kontext. Dies unterbricht harmonische Abläufe und Konsistenz Ihrer Erfahrung, und Nutzen der Informationen erschweren. In HoloLens da die Informationen auf der physikalischen Umgebung, überlagert wird, wird mit zu vielen Schriftschnitte die Benutzeroberfläche beeinträchtigt werden. Segoe UI ist die Schriftart für alle digitalen Microsoft-Designs. Es wird in der Windows Mixed Reality-Shell konsistent verwendet. Sie können die Schriftartdatei Segoe UI, aus der [Windows Toolkit Entwurfsseite](https://docs.microsoft.com/windows/uwp/design-downloads/).

[Weitere Informationen zu die Schriftart Segoe UI](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>Vermeiden Sie schlanke Schriftbreiten

Vermeiden Sie die Verwendung von hell oder semilight Schriftbreiten für die typgrößen unter 42 pt, da thin vertikalen Strichen Vibrieren und Lesbarkeit beeinträchtigt werden. Moderne Schriftarten mit genügend Strichstärke gut funktionieren. Beispielsweise sind Helvetica und Arial sehr lesbar in HoloLens mithilfe von regulären oder fett Gewichtungen.

### <a name="color"></a>Farbe

Da die Hologramme mit einem additiven light-System erstellt werden, ist weißer Text in HoloLens hoch lesbar. Sie finden Beispiele für die weißen Text auf im Startmenü und der App-Leiste. Obwohl weißer Text auch ohne eine Platte mit HoloLens arbeitet, kann ein komplexer physischer Hintergrund den Typ schwer zu lesen vornehmen. Es wird empfohlen, zum Verbessern der Benutzer den Fokus, und minimieren störende aus dem physischen Umfeld, mit weißem Text auf einer Druckausgabe dunkel oder den farbigen zurück.

<br>


![Es wird empfohlen, mit weißem Text auf ein dunkles oder den farbigen Platte.](images/typography-whiteonblack2-1000px.jpg)

Es wird empfohlen, mit weißem Text auf ein dunkles oder den farbigen Platte.

<br>


![Beispiele für die schwarzer text](images/640px-typography-textcolors.jpg)

Um dunkel Text verwenden, sollten Sie eine helle Platte verwenden, um lesbar zu machen. In Systemen additiv Farbe ist Schwarz als transparent angezeigt. Dies bedeutet, dass Sie nicht, finden in der schwarze Text ohne einen farbigen Teller sichern können.

<br>


![Beispiele für die schwarzer text](images/640px-typography-blackonwhite.jpg)

In UWP-apps wie z. B. der Store oder den Einstellungen finden Sie Beispiele für die schwarzen Text.

## <a name="recommended-font-size"></a>Wir empfehlen den Schriftgrad

![Zwei Verbrauchseinheiten ist der optimale Abstand zum Anzeigen von Text.](images/typography-distance-1000px.jpg)

Zwei Verbrauchseinheiten ist der optimale Abstand zum Anzeigen von Text.

Da eine mixed Reality dreidimensionalen Tiefe einschließt, ist es nicht immer einfach, um die Größe der Schriftart zu kommunizieren. Für den Benutzerkomfort ist zwei Verbrauchseinheiten der optimale Abstand zur Platzierung von Hologramme. Wir können dieser Abstand als Grundlage verwenden, um die optimale Größe zu finden.

Wie zu erwarten können, geben Sie die Größen, die wir auf einem PC oder Tablet-Gerät (in der Regel zwischen 12: 32pt) finden Sie in einem Abstand von 2 Metern relativ klein verwenden. Es hängt die Merkmale der einzelnen Schriftarten, aber im Allgemeinen ist die empfohlene minimale Typgröße für bessere Lesbarkeit ohne Stroke Vibration ca. 30pt. Wenn Ihre app in einem näher Abstand verwendet werden soll, können der kleinere Typ verwendet werden. **Die Punktgröße basiert auf der Unity 3D-Text-Mesh und Benutzeroberflächentexte. Die ausführliche Metriken und Skalierungsfaktoren, finden Sie unter [Text in Unity](text-in-unity.md).**

## <a name="resources"></a>Ressourcen
* [Segoe Schriftarten](http://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)
* [HoloLens font](http://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)

![Die Schriftart für HoloLens bietet Ihnen die Symbol-Symbole, die in Windows Mixed Reality verwendet](images/300px-hololensmdl2symbols.jpg)

Die Schriftart für HoloLens können Sie die Symbol-Symbole, die in Windows Mixed Reality verwendet.

## <a name="see-also"></a>Siehe auch
* [Text in Unity](http://holodocsfuture/index.php?title=Text_in_Unity&action=edit&redlink=1)
* [Farbe, helle und Materialien](color,-light-and-materials.md)
