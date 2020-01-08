---
title: Zeigen und Ausführen mit den Händen
description: Übersicht über das Eingabemodell „Zeigen und Ausführen“
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Interaktion, Design, HoloLens, Hände, fern, Zeigen und Ausführen
ms.openlocfilehash: c7952338c6937e42889a08ee37f6ce8bc1bb9ad3
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334068"
---
# <a name="point-and-commit-with-hands"></a>Zeigen und Ausführen mit den Händen

![Cursor](images/UX/UX_Hero_HandRay.jpg)

„Zeigen und Ausführen mit den Händen“ ist ein Eingabemodell, mit dem Benutzer auf 2D-Inhalte und 3D-Objekte zielen, die außerhalb der Reichweite liegen, diese auswählen und bearbeiten können. Diese „ferne“ Interaktionstechnik gibt es nur in der Mixed Reality-Umgebung; sie entspricht nicht der Art und Weise, in der Menschen normalerweise mit der realen Welt in Interaktion treten. Im Superhelden-Film *X-Men* beispielsweise kann die Figur [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) mit seinen Händen aus der Entfernung nach einem fernen Objekt greifen und dieses manipulieren. Dies ist etwas, was Menschen in der Realität nicht können. In HoloLens (AR) und Mixed Reality (MR) statten wir Benutzer mit diesen magischen Kräften aus und setzen dabei die Grenzen der Physik in der realen Welt außer Kraft. Ziel ist nicht nur ein positives Erlebnis mit holografischen Inhalten, sondern auch eine effektivere und effizientere Benutzerinteraktion.

## <a name="device-support"></a>Geräteunterstützung

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><strong>Eingabemodell</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
</tr>
<tr>
     <td>Zeigen und Ausführen mit den Händen</td>
     <td>❌ Nicht unterstützt</td>
     <td>✔️ Empfohlen</td>
     <td>✔️ Empfohlen</td>
</tr>
</table>


_„Zeigen und Ausführen mit Händen“_ ist eines der neuen Features, welches das neue bewegliche Handverfolgungssystem verwendet. Dieses Eingabemodell ist auch das primäre Eingabemodell bei immersiven Headsets und Verwendung von Motion-Controllern.

<br>

---

## <a name="hand-rays"></a>Handlichtstrahl

In HoloLens 2 haben wir einen Lichtstrahl erzeugt, der aus der Mitte der Handfläche des Benutzers schießt. Dieser Lichtstrahl wird als Erweiterung der Hand behandelt. Ein ringförmiger Cursor befindet sich am Ende des Strahls, um den Punkt anzugeben, an dem der Strahl das Zielobjekt schneidet. Das Objekt, auf dem der Cursor landet, kann dann gestische Befehle von der Hand empfangen.

Dieser grundlegende gestische Befehl wird mit dem Daumen und dem Zeigefinger ausgelöst, um das Tippen in die Luft auszuführen. Mithilfe des Handstrahls zum Zeigen und dem Tippen in die Luft zum Ausführen kann der Benutzer eine Schaltfläche oder einen Link aktivieren. Mit weiteren zusammengesetzten Gesten kann der Benutzer durch Webinhalte navigieren und 3D-Objekte aus der Entfernung bearbeiten. Das visuelle Design des Handlichtstrahls sollte auch auf die Zustände beim Zeigen und Ausführen reagieren, wie nachstehend beschrieben und gezeigt: 

:::row:::
    :::column:::
        ![Zeigen mit Handstrahlen](images/hand-rays-pointing.jpg)<br>
        **Status „Zeigen“**<br>
        Im Status *Zeigen* ist der Lichtstrahl eine gestrichelte Linie, und der Cursor hat die Form eines Rings.
    :::column-end:::
    :::column:::
        ![Ausführen mit Handstrahlen](images/hand-rays-commit.jpg)<br>
        **Status „Ausführen“**<br>
        Im Status *Ausführen* wird der Lichtstrahl zu einer durchgezogenen Linie, und der Cursor wird auf einen Punkt verkleinert.
    :::column-end:::
:::row-end:::

<br>

---


## <a name="transition-between-near-and-far"></a>Übergang zwischen nah und fern

Statt bestimmte Gesten zu verwenden (z. B. „Zeigen mit dem Zeigefinger" zum Richten des Lichtstrahls), haben wir den Lichtstrahl so entworfen, dass er aus der Mitte der Handfläche kommt, wodurch die fünf Finger frei gehalten und für manipulativere Gesten (z. B. Finger zusammenführen und greifen) reserviert werden konnten. Mit diesem Entwurf erstellen wir nur ein mentales Modell. Derselbe Satz von Gesten wird für nahe und ferne Interaktionen verwendet. So können Sie die gleiche Greifgeste zum Bearbeiten von Objekten aus unterschiedlichen Entfernungen verwenden. Der Aufruf des Lichtstrahls erfolgt automatisch und basiert auf der Entfernung, wie folgt:

:::row:::
    :::column:::
        ![Manipulation in der Nähe](images/transition-near-manipulation.jpg)<br>
        **Manipulation in der Nähe**<br>
        Wenn sich ein Objekt in Armeslänge befindet (ungefähr 50 cm), wird der Lichtstrahl automatisch deaktiviert und regt so die Interaktion aus der Nähe an.
    :::column-end:::
    :::column:::
        ![Manipulation in der Ferne](images/transition-far-manipulation.jpg)<br>
        **Manipulation in der Ferne**<br>
        Wenn das Objekt mehr als 50 cm entfernt ist, wird der Lichtstrahl aktiviert. Der Übergang sollte reibungslos und nahtlos erfolgen.
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a>2D-Tafel – Interaktion

Eine 2D-Tafel ist ein holografischer Container, der 2D-App-Inhalte hostet (z. B. einen Webbrowser). Das Entwurfskonzept für die ferne Interaktion mit einer 2D-Tafel verwendet den Handlichtstrahl zum Zielen und das Tippen in die Luft zum Auswählen. Nach dem Zielen mit dem Handlichtstrahl kann der Benutzer in die Luft tippen, um einen Link oder eine Schaltfläche auszulösen. Sie können eine Hand zum „Tippen in die Luft und Ziehen“ verwenden, um den Inhalt einer Tafel nach oben und unten zu scrollen. Mit der relativen Bewegung und der Verwendung von zwei Händen zum „Tippen in die Luft und Ziehen“ können Sie den Inhalt der Tafel vergrößern und verkleinern.

Wenn Sie mit dem Handlichtstrahl in die Ecken und auf die Kanten zielen, wird das naheliegendste Bearbeitungsangebot angezeigt. Mit den Bearbeitungsangeboten „Greifen und Ziehen“ kann der Benutzer über das Eckenangebot eine einheitliche Skalierung ausführen und über das Kantenangebot die Tafel neu formatieren. Durch Greifen und Ziehen der Hololeiste im oberen Bereich der 2D-Tafel kann der Benutzer die gesamte Tafel verschieben.

:::row:::
    :::column:::
       ![2D-Tafel – Interaktion „Klicken“](images/2d-slate-interaction-click.jpg)<br>
       **Klicken**<br>
    :::column-end:::
    :::column:::
       ![2D-Tafel – Interaktion „Scrollen“](images/2d-slate-interaction-scroll.jpg)<br>
        **Scrollen**<br>
    :::column-end:::
    :::column:::
       ![2D-Tafel – Interaktion „Zoomen“](images/2d-slate-interaction-zoom.jpg)<br>
       **Zoomen**<br>
    :::column-end:::
:::row-end:::

<br>

**So bearbeiten Sie die 2D-Tafel**<br>

* Der Benutzer zeigt mit dem Handlichtstrahl in die Ecken oder auf die Kanten, um das naheliegendste Bearbeitungsangebot anzuzeigen. 
* Durch das Anwenden einer Bearbeitungsgeste kann der Benutzer über das Eckenangebot eine einheitliche Skalierung und über das Kantenangebot eine Formatierung der Tafel vornehmen. 
* Durch das Anwenden einer Bearbeitungsgeste auf die Hololeiste im oberen Bereich der 2D-Tafel kann der Benutzer die gesamte Tafel verschieben.<br>


<br>

---

## <a name="3d-object-manipulation"></a>3D-Objektbearbeitung

Bei der direkten Bearbeitung hat der Benutzer zwei Möglichkeiten zum Bearbeiten von 3D-Objekten: angebotsbasierte Bearbeitung und Bearbeitung ohne Angebot. Beim Modell „Zeigen und Ausführen“ kann der Benutzer genau die gleichen Aufgaben über den Handlichtstrahl ausführen. Es ist keine zusätzliche Schulung erforderlich.<br>

### <a name="affordance-based-manipulation"></a>Angebotsbasierte Bearbeitung
Der Benutzer verwendet den Handlichtstrahl zum Zeigen und Anzeigen des Begrenzungsrahmens und der Bearbeitungsangebote. Der Benutzer kann die Bearbeitungsgeste auf den Begrenzungsrahmen anwenden, um das gesamte Objekt zu verschieben, auf die Kantenangebote, um das Objekt zu drehen, und auf die Eckenangebote, um eine einheitliche Skalierung vorzunehmen. <br>

:::row:::
    :::column:::
       ![3D-Objektbearbeitung – Verschieben aus größerer Entfernung](images/3d-object-manipulation-far-move.jpg)<br>
       **Verschieben**<br>
    :::column-end:::
    :::column:::
       ![3D-Objektbearbeitung – Drehen aus größerer Entfernung](images/3d-object-manipulation-far-rotate.jpg)<br>
        **Drehen**<br>
    :::column-end:::
    :::column:::
       ![3D-Objektbearbeitung – Skalieren aus größerer Entfernung](images/3d-object-manipulation-far-scale.jpg)<br>
       **Skalierung**<br>
    :::column-end:::
:::row-end:::


### <a name="non-affordance-based-manipulation"></a>Bearbeitung ohne Angebot
Der Benutzer zeigt mit dem Handlichtstrahl, um den Begrenzungsrahmen anzuzeigen, und wendet dann direkt Bearbeitungsgesten darauf an. Mit einer Hand sind Verschiebung und Drehung des Objekts der Bewegung und Ausrichtung der Hand zugeordnet. Mit zwei Händen kann der Benutzer Verschiebung, Drehung und Skalierung entsprechend der relativen Bewegung der beiden Hände vornehmen.<br>

<br>

---

## <a name="instinctual-gestures"></a>Instinktive Gesten
Das Konzept der instinktiven Gesten für „Zeigen und Ausführen“ entspricht dem für die [direkte Bearbeitung mit den Händen](direct-manipulation.md). Die Gesten, die der Benutzer bei einem 3D-Objekt ausführt, werden über das Design der Benutzeroberflächenangebote gesteuert. Ein kleiner Steuerpunkt beispielsweise kann den Benutzer motivieren, Daumen und Zeigefinger zusammenzuführen, während ein anderer Benutzer möglicherweise ein größeres Objekt mit allen fünf Fingern greifen möchte.

:::row:::
    :::column:::
       ![Instinktive Gesten – Kleines Objekt aus größerer Entfernung](images/instinctual-gestures-far-smallobject.jpg)<br>
       **Kleines Objekt**<br>
    :::column-end:::
    :::column:::
       ![Instinktive Gesten – Mittelgroßes Objekt aus größerer Entfernung](images/instinctual-gestures-far-mediumobject.jpg)<br>
        **Mittelgroßes Objekt**<br>
    :::column-end:::
    :::column:::
       ![Instinktive Gesten – Großes Objekt aus größerer Entfernung](images/instinctual-gestures-far-largeobject.jpg)<br>
       **Großes Objekt**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>Symmetrisches Design für Händen und Controller mit 6 Freiheitsgraden 

Das Konzept „Zeigen und Ausführen“ für die ferne Interaktion wurde anfänglich für das Mixed Reality-Portal (MRP) erstellt, in dem ein Benutzer ein immersives Headset trägt und über Motion-Controller mit 3D-Objekten interagiert. Zum Zeigen auf und Bearbeiten von fernen Objekten schießen die Motion-Controller einen Lichtstrahl ab. zum Ausführen weiterer unterschiedlicher Aktionen gibt es Tasten auf den Controllern. Wir nutzen das Interaktionsmodell des Lichtstrahls und haben dieses mit den beiden Händen verbunden. Bei diesem symmetrischen Entwurf braucht der Benutzer, der sich mit MRP auskennt, kein anderes Interaktionsmodell für das Zeigen auf und Bearbeiten von fernen Objekten zu lernen, wenn er HoloLen 2 verwendet (und umgekehrt).    

:::row:::
    :::column:::
        ![Symmetrischer Entwurf für Lichtstrahlen mit Controllern](images/symmetric-design-for-rays-controllers.jpg)<br>
        **Controllerlichtstrahlen**<br>
    :::column-end:::
    :::column:::
        ![Symmetrischer Entwurf für Lichtstrahlen mit Händen](images/symmetric-design-for-rays-hands.jpg)<br>
        **Handlichtstrahl**<br>
    :::column-end:::
:::row-end:::

<br>


---

## <a name="hand-ray-in-mrtkmixed-reality-toolkit-for-unity"></a>Handlichtstrahl in MRTK (Mixed Reality Toolkit) für Unity
Standardmäßig stellt das MRTK einen vorkonfigurierten Handlichtstrahl ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) zur Verfügung, der den gleichen visuellen Status wie der System-Handlichtstrahl der Shell aufweist. Er wird im Eingabeprofil des MRTK unter „Pointers“ (Zeiger) zugewiesen. In Windows Mixed Reality (immersives Headset) werden dieselben Strahlen auch für die Motion-Controller verwendet.

* [MRTK – Zeigerprofil](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [MRTK – Eingabesystem](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [MRTK – Zeiger](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)


---

## <a name="see-also"></a>Siehe auch
* [Direkte Manipulation mit den Händen](direct-manipulation.md)
* [Anvisieren und Ausführen](gaze-and-commit.md)
* [Hände – Direkte Manipulation](direct-manipulation.md)
* [Hände – Gesten](gaze-and-commit.md#composite-gestures)
* [Instinktive Interaktionen](interaction-fundamentals.md)
