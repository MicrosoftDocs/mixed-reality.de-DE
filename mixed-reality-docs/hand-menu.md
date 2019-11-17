---
title: Hand Menü
description: Mithilfe von Hand Menüs können Benutzer schnell Hand anfügende Benutzeroberflächen für häufig verwendete Funktionen aktivieren. Dies sind unsere bewährten Methoden und Empfehlungen für Hand-Menüs.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: Hand, Menü, Schaltfläche, schnell Zugriff, Layout
ms.openlocfilehash: c53fdc4ea6f3243cf906ee1916a9c234d0fce6ca
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143179"
---
# <a name="hand-menu"></a>Hand Menü

![Ulnar Seitenposition](images/UX/UX_Hero_HandMenu.jpg)

Mithilfe von Hand Menüs können Benutzer schnell Hand anfügende Benutzeroberflächen für häufig verwendete Funktionen aktivieren. 

Im folgenden finden Sie die bewährten Methoden, die wir für Hand Menüs gefunden haben. Sie finden auch eine Beispiel Szene, die das Hand Menü in [mrtk](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)demonstriert.

<br>

---

## <a name="behavior-best-practices"></a>Bewährte Methoden für das Verhalten
**A. behalten Sie die Anzahl der Schaltflächen gering:** aufgrund der engen Entfernung zwischen einem Hand gesperrten Menü und den Augen und der Tendenz des Benutzers, sich jederzeit auf einen relativ kleinen visuellen Bereich zu konzentrieren (der Teilnehmer Kegel ist ungefähr 10 Grad), wir empfehlen Ihnen Folgendes: halten Sie die Anzahl der Schaltflächen klein. Basierend auf unserer Untersuchung funktioniert eine Spalte mit drei Schaltflächen gut, indem der gesamte Inhalt in der Ansicht (FOV) beibehalten wird, auch wenn Benutzer ihre Hände in den Mittelpunkt des FOV verschieben. 

**B. verwenden Sie das Hand Menü für die schnelle Aktion:** das Auslösen eines Arm und das Aufrechterhalten der Position kann die Arm-Müdigkeit leicht auslösen. Verwenden Sie eine Hand gesperrte Methode für das Menü, das eine kurze Interaktion erfordert. Wenn Ihr Menü Komplex ist und erweiterte Interaktions Zeiten erfordert, sollten Sie stattdessen "World-Locked" oder "Body-Lock" verwenden. 

**C. Schaltflächen-/Panel-Winkel:** Menüs sollten auf die entgegengesetzte Schulter und die Mitte des Kopfes hin-/ausblenden: Dadurch kann eine natürliche Handbewegung mit dem Menü mit umgekehrter Hand interagieren und alle umständlichen oder unbequemen Handpositionen beim berühren vermeiden. Parab. 

**D. in Erwägung gezogen, dass ein-oder Freihand-Vorgang unterstützt** wird. gehen Sie nicht davon aus, dass die beiden Hände des Benutzers stets verfügbar sind. Stellen Sie sich einen großen Bereich von Kontexten vor, wenn eine oder beide Hände nicht verfügbar sind, und stellen Sie sicher, dass Ihre Entwurfs Konten für diese Situationen sind. Um ein eindimensionales Menü zu unterstützen, können Sie versuchen, die Menü Platzierung von Hand gesperrt auf die gesperrte Seite zu übertragen, wenn die Hand kippt (in den Blättern). Bei praktischen Szenarien sollten Sie die Verwendung eines sprach Befehls zum Aufrufen der Menü Schaltflächen "Hand" in Erwägung gezogen haben.

**E. zweistufige Aufrufe:** Wenn Sie nur die Option "Palm-up" als Ereignis verwenden, um das Hand Menü zu aktivieren, wird es möglicherweise versehentlich angezeigt, wenn Sie es nicht benötigen (falsch positiv) und unbeabsichtigt. Wenn Sie in Ihrer APP falsch positive Ergebnisse haben, können Sie zusätzlich zum Palm-up-Ereignis einen weiteren Schritt hinzufügen, um das Hand Menü aufzurufen, z. b. voll geöffnete Finger.

**F. vermeiden Sie das Hinzufügen von Schaltflächen in der Nähe des Handgelenks (System Starttaste):** wenn die Menü Schaltflächen "Hand" zu nah an der Start Schaltfläche platziert werden, wird Sie möglicherweise versehentlich bei der Interaktion mit dem

**G. testen, testen, testen:** Personen verfügen über unterschiedliche Texte mit unterschiedlichen Schwellenwerten für Komfort und Unbehagen usw. Stellen Sie sicher, dass Sie Ihr Design testen und Feedback von vielen verschiedenen Personen erhalten.

<br>

---

## <a name="hand-menu-placement-best-practices"></a>Bewährte Methoden für die Platzierung von Hand Menüs

Bei der menschlichen Anatomie ist der ulnar-Nerv ein Nerv, der in der Nähe des Ulna-knochenverläuft. Die Ulna ist ein langer Ring in der forearm, der vom Bogen zum kleinsten Finger reicht.

Im folgenden finden Sie zwei empfohlene Platzierungen, die auf unseren Explorationen basieren:


:::row:::
    :::column:::
        ![ulnar Seitenposition](images/UlnarSideHandMenu.gif)<br>
        **Ein. ulnar in der Palme**<br>
        Diese Position ist zuverlässig, da die Hände einander nicht überlappen. Dies ist wichtig für die genaue Erkennung und Nachverfolgung von Hand.
    :::column-end:::
    :::column:::
        ![ulnar Seitenposition](images/UlnarAboveHandMenu.gif)<br>
        **B. ulnar oberhalb der Hand**<br>
        Dieser Speicherort ist für Benutzer praktisch, da Sie den Arm nicht zu groß machen müssen, um mit dem Hand Menü zu interagieren. Es empfiehlt sich, die Menüs **13 cm** oberhalb der Palme zu platzieren und die Schaltflächen innerhalb der ulnar-Palme auszurichten. [Weitere Informationen zur optimalen Schaltflächen Größe](interactable-object.md)<br>
        <br>
        Aus technischen Gründen wird dieser Speicherort mit einer erforderlichen Implementierung empfohlen: der Entwickler muss das Menü fixieren, wenn die gegenüberliegende Seite des Benutzers in der Nähe der Interaktion mit dem Benutzer steht. Dadurch wird die überlappende Hände von jitterität vermieden, und es ist auch möglich, dass die Schaltflächen schneller ausgerichtet werden.<br>
        <br>
        Hololens 2 Kameras identifizieren Hände genau, wenn Sie voneinander getrennt sind. Überlappende Hände können dazu führen, dass Hand Menüs von der Ankerposition Weg wechseln.<br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a>Nicht empfohlene Menü Positionen
We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:


:::row:::
    :::column:::
        ![Above arm](images/AboveArm.gif)<br>
        **Above the arm**<br>
        1 - Difficult to maintain good hand tracking<br>
        2 - Causes user fatigue due to unnatural position
    :::column-end:::
    :::column:::
        ![Above fingers](images/AboveFingers.gif)<br>
        **Above fingers**<br>
        1 - Hand fatigue due to holding hand for long time<br>
        2 - Hand tracking issues on index and middle finger
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Above center palm](images/handCenter.gif)<br>
        **Above-center palm**<br>
        1 - Hand tracking issues due to overlapping hands<br>
        2 - Hand fatigue due to holding hands for long time in order to interact with menus
    :::column-end:::
    :::column:::
        ![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**<br>
        1 - Hand tracking issues<br>
        2 - Hand fatigue holding hand above normal posture<br>
        3 - Issues pressing buttons with other fingers by accident due to limited space between fingers
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Back of the Arm](images/BackOfTheArm.gif)<br>
        **Back of the arm**<br>
        1 - Can trigger home button by accident<br>
        2 - Not a natural or comfortable position for users
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtkmixed-reality-toolkit-for-unity"></a>Hand menu in MRTK(Mixed Reality Toolkit) for Unity
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu. HandConstraintPalmUp solver script allows you easily attach any objects to the hands with various configurable options.

* [MRTK - Hand Menu with HandConstraint and HandConstraintPalmUp ](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)


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
