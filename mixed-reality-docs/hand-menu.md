---
title: Handmenü
description: Mithilfe von Hand Menüs können Benutzer schnell Hand anfügende Benutzeroberflächen für häufig verwendete Funktionen aktivieren. Dies sind unsere bewährten Methoden und Empfehlungen für Hand-Menüs.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: Hand, Menü, Schaltfläche, schnell Zugriff, Layout
ms.openlocfilehash: d1d15b36bab2ca2082ca4ba91b9c64862893f80c
ms.sourcegitcommit: fef42e2908e49822f2d13b05d2f9260bf0d72158
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86061167"
---
# <a name="hand-menu"></a>Handmenü

![Ulnar Seitenposition](images/UX/UX_Hero_HandMenu.jpg)

Das Menü "Hand" ist eines der einzig testen UX-Muster in hololens 2. Mit dieser Option können Sie schnell Hand anfügende Benutzeroberflächen einrichten. Da es jederzeit zugänglich ist und leicht angezeigt und ausgeblendet werden kann, ist es hervorragend für schnelle Aktionen geeignet.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

Sie finden unsere empfohlenen bewährten Methoden für die Arbeit mit Hand Menüs in der folgenden Liste. Sie finden auch eine Beispiel Szene, die das Hand Menü in [mrtk](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)demonstriert.

<br>


---

## <a name="best-practices"></a>Bewährte Methoden
**Anzahl von Schaltflächen klein halten** 

Aufgrund der engen Entfernung zwischen einem Hand gesperrten Menü und den Augen und der Tendenz des Benutzers, sich jederzeit auf einen relativ kleinen visuellen Bereich zu konzentrieren (der Teilnehmer Kegel ist ungefähr 10 Grad), empfiehlt es sich, die Anzahl der Schaltflächen gering zu halten. Basierend auf unserer Untersuchung funktioniert eine Spalte mit drei Schaltflächen gut, indem der gesamte Inhalt in der Ansicht (FOV) beibehalten wird, auch wenn ein Benutzer seine Hände in den Mittelpunkt des FOV verschiebt. 

**Verwenden des Hand Menüs für die schnelle Aktion** 

Das Auslösen eines Arm und das Aufrechterhalten der Position könnte leicht eine Arm-Müdigkeit verursachen. Verwenden Sie eine Hand gesperrte Methode für das Menü, das eine kurze Interaktion erfordert. Wenn Ihr Menü Komplex ist und erweiterte Interaktions Zeiten erfordert, sollten Sie stattdessen "World-Locked" oder "Body-Lock" verwenden. 

**Schaltflächen-/Panel-Winkel**

Menüs sollten in der gegenüberliegenden Schulter und der Mitte des Kopfes angezeigt werden: Dadurch kann eine natürliche Handbewegung mit dem Menü mit umgekehrter Hand interagieren und alle umständlichen oder unbequemen Handpositionen beim Berühren von Schaltflächen vermeiden. 

**In Erwägung gezogen, ein-oder frei Hand Vorgang zu unterstützen.**

Gehen Sie nicht davon aus, dass beide Hände des Benutzers stets verfügbar sind. Stellen Sie sich einen großen Bereich von Kontexten vor, wenn eine oder beide Hände nicht verfügbar sind, und stellen Sie sicher, dass Ihre Entwurfs Konten für diese Situationen sind. Um ein eindimensionales Menü zu unterstützen, können Sie versuchen, die Menü Platzierung von Hand gesperrt auf die gesperrte Seite zu übertragen, wenn die Hand kippt (in den Blättern). Bei praktischen Szenarios sollten Sie einen Sprachbefehl verwenden, um das Menü "Hand" aufzurufen.

**Vermeiden Sie das Hinzufügen von Schaltflächen in der Nähe der Hand**

Wenn die Menü Schaltflächen "Hand" zu nah an der Start Schaltfläche platziert werden, kann Sie versehentlich bei der Interaktion mit dem Menü "Hand" auftreten.

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a>Hand Menü mit großen und komplexen UI-Steuerelementen
<img src="images/UX/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
Es wird empfohlen, die Anzahl der Schaltflächen oder UI-Steuerelemente in Hand anfügenden Menüs einzuschränken. Dies liegt daran, dass die erweiterte Interaktion mit einer großen Anzahl von Benutzeroberflächen Elementen eine Arm-Müdigkeit verursachen kann. Wenn Ihre Benutzerumgebung ein großes Menü erfordert, stellen Sie dem Benutzer eine einfache Möglichkeit zur Verfügung, um das Menü zu sperren. Eine Methode, die wir empfehlen, ist die Welt, in der das Menü angezeigt wird, wenn das Handumdrehen vom Benutzer gelöscht oder umgekehrt wird. Ein zweites Verfahren besteht darin, dem Benutzer zu gestatten, das Menü direkt mit der anderen Seite zu übernehmen. Wenn der Benutzer das Menü loslässt, sollte das Menü auf der ganzen Welt gesperrt werden. Auf diese Weise kann ein Benutzer über einen längeren Zeitraum bequem und sicher mit verschiedenen Benutzeroberflächen Elementen interagieren. 

Wenn das Menü weltweit gesperrt ist, stellen Sie sicher, dass Sie eine Möglichkeit zum Verschieben des Menüs und zum Schließen des Menüs haben, wenn es nicht mehr benötigt wird. Legen Sie die Position des Menüs durch Bereitstellen von Handles auf den Seiten oder dem oberen Rand des Menüs auf den Fügen Sie eine Schaltfläche Schließen hinzu, um das Schließen des Menüs zuzulassen. Hiermit wird zugelassen, dass das Menü erneut an die Hand angefügt wird, wenn der Benutzer die Hand hat. Außerdem wird empfohlen, dass die Benutzer die Benutzer überprüfen, um falsche Aktivierungen zu verhindern (siehe unten).

**Großes Menü, das ein Problem mit der Benutzerfreundlichkeit anzeigt**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

**Weltweit gesperrtes Menü im Handschlag**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

**Manueller Abruf & Pullvorgang an der Welt: Sperren Sie das Menü.**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]


## <a name="how-to-prevent-false-activation"></a>Verhindern der falsch Aktivierung

Wenn Sie nur die Option "Palm-up" als Ereignis verwenden, um das Menü "Hand" zu starten, wird es möglicherweise versehentlich angezeigt, wenn Sie es nicht benötigen (falsch positiv), da Personen die Hände absichtlich (für die Kommunikation und Objekt Bearbeitung) und unbeabsichtigt verschieben. Um falsche Aktivierungen zu reduzieren, fügen Sie neben dem Palm-up-Ereignis einen zusätzlichen Schritt hinzu, um das Menü "Hand" (z. b. vollständig geöffnete Finger) aufzurufen

**Flache Palme erforderlich**

Wenn Sie eine flache öffnende Hand benötigen, können Sie die falsche Aktivierung verhindern, die auftreten kann, wenn der Benutzer während der Kommunikation innerhalb einer Umgebung Objekte oder Gesten bearbeitet. 

**Blick erfordern**

Durch den Benutzer, der die Hand hat (entweder mit dem Augenblick oder dem Kopf), werden falsche Aktivierungen verhindert, da der Benutzer absichtlich seine Aufmerksamkeit als sekundären Aktivierungs Schritt (mit einem anpassbaren Entfernungs Schwellenwert, der für die Benutzerfreundlichkeit verwendet wird) an die Hand weiterleiten muss.  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a>Bewährte Methoden für die Platzierung von Hand Menüs

Bei der menschlichen Anatomie ist der ulnar-Nerv ein Nerv, der in der Nähe des Ulna-knochenverläuft. Die Ulna ist ein langer Ring in der forearm, der vom Bogen zum kleinsten Finger reicht.

Im folgenden finden Sie zwei empfohlene Platzierungen, die auf unseren Explorationen basieren:


:::row:::
    :::column:::
        ![Ulnar Seitenposition](images/UlnarSideHandMenu.gif)<br>
        **Ein. ulnar in der Palme**<br>
        Diese Position ist zuverlässig, da die Hände einander nicht überlappen. Dies ist wichtig für die genaue Erkennung und Nachverfolgung von Hand.
    :::column-end:::
    :::column:::
        ![Ulnar Seitenposition](images/UlnarAboveHandMenu.gif)<br>
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
Wir haben die Benutzer Forschung mit verschiedenen Menüs und Standorten durchgeführt. die folgenden Menü Positionen werden **nicht empfohlen**. Sie finden die Nachteile der einzelnen nachfolgenden Nachforschungen:


:::row:::
    :::column:::
        ![Oberhalb von Arm](images/AboveArm.gif)<br>
        **Oberhalb der Arm**<br>
        1: schwer zu verwaltender guter Hand Verfolgung<br>
        2: verursacht eine Benutzer Müdigkeit aufgrund der unnatürlichen Position.
    :::column-end:::
    :::column:::
        ![Über Fingern](images/AboveFingers.gif)<br>
        **Über Fingern**<br>
        eine Hand Müdigkeit aufgrund einer langen Zeitüberschreitung<br>
        2-Hand-nach Verfolgungs Probleme bei Index-und mittelfingern
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Oberhalb der mittleren Palme](images/handCenter.gif)<br>
        **Oberhalb-Mittelpunkt**<br>
        1-Hand-nach Verfolgungs Probleme aufgrund von überlappenden Händen<br>
        zwei Hand Müdigkeit aufgrund der langen Zeit für die Interaktion mit Menüs
    :::column-end:::
    :::column:::
        ![Top Fingertip ](images/TopFingerTip.gif) **Top Fingertip**<br>
        1-Hand-nach Verfolgungs Probleme<br>
        2-Hand Müdigkeit von Hand über normalem Status<br>
        3: Fehler beim Drücken von Schaltflächen mit anderen Fingern aufgrund von eingeschränktem Leerraum zwischen Fingern.
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Zurück zum Arm](images/BackOfTheArm.gif)<br>
        **Zurück zum Arm**<br>
        1: Start Schaltfläche nach einem Unfall<br>
        2-keine natürliche oder bequeme Position
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a>Hand Menü im mrtk (Mixed Reality Toolkit) für Unity
**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** stellt Skripts und Beispiel Szenen für das Hand Menü bereit. Das handeinschränintpalmup-Solver-Skript ermöglicht es Ihnen, alle Objekte mit verschiedenen konfigurierbaren Optionen an die Hände anzufügen. Die Hand Menü Beispiele von mrtk enthalten nützliche Optionen, wie z. b. eine flache Palme und eine Blick Anforderung zum Verhindern der falschen Aktivierung.

* [Hand Menü-Documentationen](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)
* [Beispiel Szene für Hand Menü](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

Sie können die Menü Beispiele in hololens 2 mit der mrtk examples Hub-App ausprobieren. 
* [Hand Menü Szene im mrtk-Beispiel-Hub](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---


## <a name="see-also"></a>Siehe auch

* [Cursor](cursors.md)
* [Handstrahl](point-and-commit.md)
* [Schaltfläche](button.md)
* [Interaktionsfähiges Objekt](interactable-object.md)
* [Begrenzungsrahmen und App-Leiste](app-bar-and-bounding-box.md)
* [Manipulation](direct-manipulation.md)
* [Handmenü](hand-menu.md)
* [Nähemenü](near-menu.md)
* [Objektsammlung](object-collection.md)
* [Sprachbefehl](voice-input.md)
* [Tastatur](keyboard.md)
* [QuickInfo](tooltip.md)
* [Filmklappe](slate.md)
* [Schieberegler](slider.md)
* [Shader](shader.md)
* [Billboarding und Tag-along](billboarding-and-tag-along.md)
* [Anzeigen des Fortschritts](progress.md)
* [Oberflächenmagnetismus](surface-magnetism.md)
