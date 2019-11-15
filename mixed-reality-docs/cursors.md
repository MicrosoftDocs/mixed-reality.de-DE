---
title: Cursor
description: Ein Cursor oder Indikator Ihres Ziel Vektor bietet fortlaufendes Feedback für den Benutzer, um zu verstehen, was hololens über seine Absichten versteht.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Hololens (1. Gen), hololens 2, gemischte Realität, Cursor, Zielvorgabe, Blick, Gesten
ms.openlocfilehash: 719e7a573e8c8bc682ec0f960d9f3c8f8c8e5a4a
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105756"
---
# <a name="cursors"></a>Cursor

![Cursor](images/UX/UX_Hero_Cursor.jpg)

Ein Cursor oder Indikator Ihres aktuellen Ziel Vektor bietet fortlaufendes Feedback für den Benutzer, um zu verstehen, wo das Headset seinen aktuellen Fokus hat. Der Cursor ermöglicht dem Benutzer das Verständnis seines aktuellen Zielpunkts und fungiert als Feedback, um anzugeben, welcher Bereich, welches Hologramm oder welcher Punkt auf die Eingabe reagiert. Dabei handelt es sich um die digitale Darstellung von, bei der das Gerät die Aufmerksamkeit des Benutzers versteht (obwohl dies möglicherweise nicht der gleiche ist wie das Ermitteln von Informationen über ihre Absichten).

Das vom Cursor bereitgestellte Feedback bietet Benutzern die Möglichkeit, zu sehen, wie das System antwortet, und verwendet dieses Signal als Feedback, um ihre Absicht an das Gerät besser zu vermitteln, und schließlich ist es sicherer, sich über ihre Interaktionen zu informieren.

Es gibt drei Arten von Cursorn: **Finger, Ray**und **Head-Gaze**. Diese zeigenden Cursor funktionieren mit unterschiedlichen Eingabe Modalitäten für hololens, hololens 2 und immersive Headsets. Im folgenden finden Sie Anleitungen dazu, welche Art von Cursor für die einzelnen Typen von Headset-und Interaktions Modellen verwendet werden kann. Im Mixed Reality Toolkit (mrtk) haben wir Drag & amp; Drop-cursormodule erstellt, um Sie bei der Erstellung der richtigen Zeige Erfahrung zu unterstützen.


## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Finger Cursor</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Strahl Cursor</td>
        <td>❌</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Cursor Cursor</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="finger-cursor"></a>Finger Cursor
Der Finger Cursor ist nur in den hololens 2 verfügbar, um den Interaktionsmodus "[direkte Bearbeitung von Hand](direct-manipulation.md)" zu verbessern. Um besser zu verstehen, wo der Finger zeigt, haben wir Ringe an die Tipps beider Index Fingern angefügt. Die Ring Größe basiert auf der Nähe des Fingers und der UI-Oberfläche (je näher der Finger, der kleinere Ring) und wird zu einer punkteform verkleinert, wenn der Finger den Kontakt mit der Benutzeroberfläche herstellt. <br>

![fingercursor](images/finger-cursor.png)<br>
**Visuelle Feedback Zustände von Finger Cursor** 1: der Ring wird auf einen Punkt verkleinert. 2: der Ring richtet sich nach der Oberfläche. 3: der Ring ist senkrecht zum Finger Vektor. 4: kein Ring.

## <a name="ray-cursor"></a>Strahl Cursor
Ray-Cursors werden an das Ende von weit zeigenden Strahlen angehängt, um die Bearbeitung von Objekten zu ermöglichen, die nicht in der Hand reich sind. In immersiven Headsets werden die Strahlen von Bewegungs Controllern abgeraten und mit Punkt Cursorn enden. In hololens 2 nutzen wir das geistige Modell dieser Bewegungs Controller-Strahlen und entworfenen Hand Striche, die aus den Palmen stammen und mit den bei der direkten Bearbeitung verwendeten fingercursorn enden. <br>
:::row:::
    :::column:::
        ![Ray-Cursor Controller](images/ray-cursor-controller.png)<br>
        **Strahl Cursor von Bewegungs Controllern**<br>
    :::column-end:::
    :::column:::
        ![Ray-Cursor Hand](images/ray-cursor-hand.png)<br>
        **Strahl Cursor von Händen**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="head-gaze-cursor"></a>Cursor Cursor
Der Head-Gaze-Cursor ist ein Punkt, der an das Ende eines unsichtbaren Kopf Zeigers angefügt wird, der die Position und Drehung des Kopfes verwendet, um zu zeigen. Zum Ausführen von Aktionen wird dieser Zeige Cursor mit verschiedenen Commit-Eingaben gekoppelt, wie z. b. Air Tap, Voice Commands, Dwell und Button Press. In hololens 2 ist der Head-Blick am besten mit allen Commit-Eingaben gekoppelt, die nicht per Luft tippen verwendet werden, da es einen Interaktions Konflikt zwischen Luft tippen und fern Strahlen gibt. <br>
:::row:::
    :::column:::
        ![Cursor Hand](images/head-gaze-cursor-hand.png)<br>
        **Cursor Cursor mit Handbewegung**<br>
    :::column-end:::
    :::column:::
        ![Head-Gaze-Cursor Stimme](images/head-gaze-cursor-voice.png)<br>
        **Kopf zeiligen Cursor mit Sprachbefehl**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="cursor-customization-recommendations"></a>Empfehlungen für die Cursor Anpassung
Wenn Sie das Verhalten und den Anschein von Cursor Feedback anpassen möchten, finden Sie hier einige Entwurfs Empfehlungen:

### <a name="cursor-scale"></a>Cursor Skala
* Der Cursor sollte nicht größer sein als die verfügbaren Ziele, sodass Benutzer problemlos mit dem Inhalt interagieren und ihn anzeigen können.
* Abhängig von der Umgebung, die Sie erstellen, ist das Skalieren des Cursors, wie der Benutzer aussieht, auch ein wichtiger Aspekt. Beispielsweise sollte der Cursor nicht zu klein werden, da der Benutzer nicht mehr zu klein ist, sodass er verloren geht.
* Beim Skalieren des Cursors sollten Sie eine weiche Animation darauf anwenden, während Sie skaliert wird, um ihr ein organisches Gefühl zu vermitteln.
* Vermeiden Sie das Blockieren von Inhalt. Holograms machen das Erlebnis als unvergesslich, und der Cursor sollte nicht davon entfernt werden.

### <a name="directionless-cursor-shape"></a>Direktionlose Cursor Form
* Obwohl es keine Rechte Cursor Form gibt, empfiehlt es sich, eine direktionlose Form wie einen "Tor" zu verwenden. Ein Cursor, der in einer Richtung zeigt (z. b. ein herkömmlicher Pfeilcursor), kann den Benutzer so verwechseln, dass er immer auf diese Weise aussieht.
* Eine Ausnahme besteht darin, dass der Cursor verwendet wird, um dem Benutzer Interaktions Anweisungen mitzuteilen. Wenn z. b. Hologramme im Mixed Reality-Betriebssystem skaliert werden, schließt der Cursor temporär Pfeile ein, die den Benutzer darüber informiert, wie Sie seine Hand verschieben, um das Hologram zu skalieren.

### <a name="look-and-feel"></a>Aussehen und Gefühl
* Ein Ring Diagramm oder ein mit einem Tor gegeformter Cursor funktioniert für viele Anwendungen.
* Wählen Sie eine Farbe und eine Form aus, die die von Ihnen erstellten Funktionen am besten repräsentiert.
* Cursor sind besonders anfällig für die [Trennung von Farben](hologram-stability.md#color-separation).
* Ein kleiner Cursor mit ausgewogener Deckkraft sorgt dafür, dass er informativ ist, ohne die visuelle Hierarchie zu dominieren.
* Sie sollten die Verwendung von Shadowing oder Highlights hinter dem Cursor erkennen, da Sie Inhalte behindern und von der Aufgabe ablendieren können.
* Cursor sollten sich an den Oberflächen in der APP ausrichten und Sie anspiegeln. Dadurch erhält der Benutzer ein Gefühl, dass das System sehen kann, wo er aussieht, aber auch, dass das System seine Umgebung kennt. Im Mixed Reality-Betriebssystem richtet sich der Cursor z. b. an den Oberflächen der Benutzer Welt, wodurch ein Gefühl der Kenntnis der Welt entsteht, auch wenn der Benutzer nicht direkt in einem Hologram sucht.
* Das magnetisch Sperren des Cursors an ein interaktives Element, wenn es sich innerhalb der Nähe befindet, kann dabei helfen, das Vertrauen zu verbessern, dass der Benutzer mit diesem Element interagiert, wenn eine Auswahl Aktion ausgeführt wird

### <a name="visual-cues"></a>Visuelle Hinweise
* Wenn Sie sich auf ein einzelnes Hologramm konzentrieren, sollte Ihr Cursor nur dieses – Hologramm ausrichten und die Form ändern, wenn Sie von diesem – Hologramm Weg gehen. Dies kann dem Benutzer vermitteln, dass das – Hologramm handlungsfähig ist und mit ihm interagieren kann.
* Wenn Ihre Anwendung eine räumliche Zuordnung verwendet, könnte der Cursor jede sichtbare Oberfläche ausrichten und umarmen. Dadurch erhalten die Benutzer Feedback, dass hololens und Ihre Anwendung Ihren Speicherplatz sehen können. Dadurch wird die Tatsache verstärkt, dass holograms Real und in unserer Welt sind und die Lücke zwischen Real und Virtual überbrücken.
* Sehen Sie sich an, was der Cursor tun soll, wenn keine holograms oder Oberflächen in der Ansicht vorhanden sind. Eine Möglichkeit besteht darin, den Benutzer in einem vordefinierten Abstand vor dem Benutzer zu platzieren.

### <a name="possible-actions"></a>Mögliche Aktionen
* Der Cursor kann durch verschiedene Symbole dargestellt werden, um mögliche Aktionen zu vermitteln, die ein – Hologramm ausführen kann, z. b. Skalierung oder Drehung.
* Fügen Sie dem Cursor nur dann zusätzliche Informationen hinzu, wenn er etwas für den Benutzer bedeutet. Andernfalls bemerken die Benutzer möglicherweise nicht, dass sich der Status ändert, oder Sie werden durch den Cursor verwirrt.

### <a name="input-state"></a>Eingabe Status
* Der Cursor kann verwendet werden, um den Eingabe Zustand oder die Absicht des Benutzers anzuzeigen. Beispielsweise könnte ein Symbol angezeigt werden, das dem Benutzer mitteilt, dass das System seinen Hand Zustand hat und die Anwendung weiß, dass Sie bereit sind, Maßnahmen zu ergreifen.
* Wir könnten auch den Cursor verwenden, um Benutzern anzuzeigen, dass Sprachbefehle vom System über eine vorübergehende Farbe changehört wurden.

* Die folgenden Cursor Zustände können auf unterschiedliche Weise implementiert werden. Sie können diese verschiedenen Zustände implementieren, indem Sie den Cursor wie einen Zustands Automat modellieren. Zum Beispiel:
    * Im Leerlaufzustand wird der Standard Cursor angezeigt.
    * Der Status "bereit" ist, wenn Sie festgestellt haben, dass die Benutzer die Hand in der Bereitschaft haben.
    * Der Interaktions Zustand ist, wenn der Benutzer eine bestimmte Interaktion ausführt.
    * Der Status "mögliche Aktionen" oder "Hover" ist, wenn Sie mögliche Aktionen übermitteln, die für ein Hologram ausgeführt werden können.

Sie können diese Zustände auch auf die gleiche Weise implementieren, sodass Sie unterschiedliche Kunstobjekte anzeigen können, wenn verschiedene Zustände erkannt werden.

<br>

---


## <a name="going-cursor-free"></a>"Cursor frei"
Das Entwerfen ohne Cursor wird empfohlen, wenn das Eintauchen eine wichtige Komponente einer-Funktion ist und wenn für das zeigen von Interaktionen (durchschauen und Gesten) keine hohe Genauigkeit erforderlich ist. Das System muss immer noch die Anforderungen erfüllen, die normalerweise von einem Cursor erfüllt werden, indem Benutzern Kontinuierliches Feedback zum Verständnis des Systems bereitgestellt wird. Dies kann durch andere spürbare Zustandsänderungen erreicht werden.

<br>

---

## <a name="cursor-in-mrtkmixed-reality-toolkit-for-unity"></a>Cursor im mrtk (Mixed Reality Toolkit) für Unity
Standardmäßig stellt **[mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** eine Cursor-vorfab ([DefaultCursor. Prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) bereit, die denselben visuellen Zustand aufweist wie der System Cursor der Shell. Sie wird im Eingabe Profil von mrtk unter Zeiger zugewiesen. Sie können diesen Cursor für Ihre Benutzeroberflächen ersetzen/anpassen. Für die Verwendung von Eye-Tracking-Eingaben bietet mrtk auch den "eyegazecursor", der über eine feine Visualisierung verfügt, um die Ablenkung zu minimieren.

* [Mrtk-Zeiger Profil](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [Mrtk-Eingabe System](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [Mrtk-Zeiger](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)


---

## <a name="see-also"></a>Weitere Informationen:
* [Gesten](gaze-and-commit.md#composite-gestures)
* [Anvisieren mit dem Kopf und Ausführen](gaze-and-commit.md)
