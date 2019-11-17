---
title: Begrenzungs Bereich und App-Leiste
description: Die APP-Leiste ist ein Menü auf Objektebene, das eine Reihe von Schaltflächen enthält, die am unteren Rand der Begrenzungen eines holograms angezeigt werden.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, App-Leiste, Begrenzungs Bereich
ms.openlocfilehash: e4f519cba459efac25f6c1370b07fcda4def30a1
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143175"
---
# <a name="bounding-box-and-app-bar"></a>Begrenzungs Bereich und App-Leiste
![umgebenden ist die Standardschnittstelle für die Objekt Bearbeitung in gemischter Realität.](images/UX/UX_Hero_BoundingBox.jpg)<br>
<br>

## <a name="what-is-the-bounding-box"></a>Was ist das umgebende Feld?

Das Begrenzungs Zeichen ist die Standardschnittstelle für die Objekt Bearbeitung in gemischter Realität. Der Benutzer erhält eine Kosten, die das Objekt momentan anpassbar ist. Bei hololens 2 funktioniert das umgebende Feld mit direkter Hand Manipulation und antwortet auf die Nähe des Benutzers. Es zeigt visuelles Feedback, um dem Benutzer zu helfen, den Abstand zum Objekt zu erkennen.

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a>Skalieren eines Objekts<br>
        In den Ecken des umgebenden Felds wird dem Benutzer mitgeteilt, dass das Objekt skaliert werden kann. Die Handles folgen einem weit verbreiteten Muster zur Anpassung der Skalierung. Diese visuelle Visualisierung zeigt Benutzern den gesamten Bereich des Objekts an – auch dann, wenn Sie außerhalb eines Anpassungsmodus nicht sichtbar sind. Dies ist besonders wichtig, da das Objekt, das an ein anderes Objekt oder eine andere Oberfläche angedockt ist, sich so verhält, als ob es sich um ein Leerzeichen handelt, das nicht vorhanden sein sollte.<br>
        <br>
        *Video Schleife: Skalieren eines Objekts per Begrenzungs Rahmen*
    :::column-end:::
        :::column:::
        ![Speicher](images/spacer-20x582.png)<br>
       ![hololens zeigt das Skalieren eines Objekts über das Begrenzungsfeld an](images/HoloLens2_BoundingBox.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a>Drehen eines Objekts<br>
        Die vertikalen rechteckigen Anlagen an den Rändern des umgebenden Felds sind Rotations Indikatoren. Dies ermöglicht dem Benutzer eine präzisere Anpassung der platzierten holograms. Sie können nicht nur angepasst und skaliert werden, sondern auch jetzt drehen.<br>
        <br>
        *Video Schleife: Drehen eines Objekts über das umgebende Feld*
    :::column-end:::
        :::column:::
        ![Speicher](images/spacer-20x582.png)<br>
       ![hololens-Sicht, die das Drehen eines Objekts über das umgebende Feld](images/HoloLens2_BoundingBox_Rotate.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a>Visuelles Feedback in der Nähe von hololens 2<br>
        Auf hololens 2 gibt es einen zusätzlichen visuellen Hinweis, der die Wahrnehmung der Tiefe des Benutzers unterstützt. Ein Ring in der Nähe des fingerabbilds wird angezeigt und herunterskaliert, wenn sich der Fingertipp näher an das Objekt anpasst. Der Ring wird schließlich in einen Punkt konvergiert, wenn der gedrückte Zustand erreicht wird. Diese visuelle Visualisierung unterstützt den Benutzer dabei, zu verstehen, wie weit Sie aus dem-Objekt stammen.<br>
        <br>
        *Video Schleife: Beispiel für visuelles Feedback basierend auf der Nähe eines umgebenden Felds*
    :::column-end:::
        :::column:::
        ![Speicher](images/spacer-20x582.png)<br>
       ![Sie visuelles Feedback in der Nähe](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::

<br>

**Informationen zur Entwicklung von Unity-apps finden Sie im Abschnitt zum umgebenden [Feld im Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**

<br>

---

## <a name="what-is-the-app-bar"></a>Was ist die APP-Leiste?

Die APP-Leiste ist ein Menü auf Objektebene, das eine Reihe von Schaltflächen enthält, die am unteren Rand der Begrenzungen eines holograms angezeigt werden. Dieses Muster wird häufig verwendet, um Benutzern das Entfernen und Anpassen von holograms zu ermöglichen. Die APP-Leiste wurde primär als eine Möglichkeit zum Verwalten von platzierten Objekten in der Umgebung eines Benutzers entwickelt. In Verbindung mit dem umgebenden Feld hat ein Benutzer vollständige Kontrolle darüber, wo und wie Objekte in gemischter Realität ausgerichtet werden.

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a>Die APP-Leiste folgt dem Benutzer.<br>
        Da dieses Muster mit Objekten verwendet wird, die in der Welt gesperrt sind, wird die APP-Leiste immer auf der Seite der Objekte angezeigt, die dem Benutzer am nächsten ist, wenn sich der Benutzer um das Objekt bewegt wird. Obwohl dies kein Abgleich ist, erzielt es effektiv dasselbe Ergebnis. verhindern, dass die Position eines Benutzers Funktionen sperrt oder blockiert, die andernfalls an einem anderen Speicherort in Ihrer Umgebung verfügbar wären. <br>
        <br>
        *Video Schleife: Durchlaufen eines Hologram, der APP-Leiste folgt*
    :::column-end:::
        :::column:::
        ![Speicher](images/spacer-20x582.png)<br>
       ![durchlaufen eines holograms. Die APP-Leiste folgt.](images/HoloLens2_AppBarFollowing.gif)<br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtkmixed-reality-toolkit-for-unity"></a>Begrenzungsfeld in mrtk (Mixed Reality Toolkit) für Unity
**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** stellt Skripts und Prefabs für das umgebende Feld und die APP-Leiste bereit. Sie können ein Begrenzungsfeld hinzufügen, indem Sie das BoundingBox.cs-Skript einfach einem beliebigen Objekt zuweisen.

* [Mrtk-Begrenzungsfeld](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)


<br>

---


## <a name="see-also"></a>Weitere Informationen:

* [Cursor](cursors.md)
* [Hand Strahl](point-and-commit.md)
* [Button](button.md)
* [Interaktionsfähiges Objekt](interactable-object.md)
* [Begrenzungsrahmen und App-Leiste](app-bar-and-bounding-box.md)
* [Bearbeitung](direct-manipulation.md)
* [Handmenü](hand-menu.md)
* [Near-Menü](near-menu.md)
* [Objektsammlung](object-collection.md)
* [Sprachbefehl](voice-input.md)
* [Tastatur](keyboard.md)
* [QuickInfo](tooltip.md)
* [Tafel](slate.md)
* [Schieberegler](slider.md)
* [Shader](shader.md)
* [Billboarding und Tag-along](billboarding-and-tag-along.md)
* [Anzeigen des Fortschritts](progress.md)
* [Oberflächen Magnetismus](surface-magnetism.md)
