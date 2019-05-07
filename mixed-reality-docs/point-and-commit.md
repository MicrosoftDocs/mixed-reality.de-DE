---
title: Punkt- und commit
description: Übersicht über das Eingabemodell Punkt- und commit
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
keywords: Gemischte Realität Interaktion, Entwerfen
ms.openlocfilehash: e0e9c97053734ac0125fce40be7ffe9afbd2dd68
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2019
ms.locfileid: "64581310"
---
# <a name="point-and-commit"></a>Punkt- und commit
Punkt- und Commit ist ein Eingabemodell ermöglicht Benutzern das Ziel, wählen Sie aus, und Bearbeiten von 2D Inhalt und 3D-Objekte in einem Abstand. Diese Technik des "Weit" Interaktion ist eine Nabel-interaktive Benutzeroberfläche, die Menschen wird nicht wirklich bei ihren täglichen Interaktion mit der realen Welt hatten. Z. B. in einem Film Superheld Magneto ist in der Lage, unseren Lesern und zum Bearbeiten von einen weit Objekt über praktische in einem Abstand, aber Benutzer kann sich nicht in der Praxis. In Microsoft HoloLens (AR) und Microsoft Mixed Reality (VR), wir Rüsten Sie Benutzern diese magischen Stromversorgung, unterbrechen die physische Einschränkungen der realen Welt nicht nur um positives Benutzererlebnis mit holographic Inhalt aber auf die Interaktion effektiver zu gestalten und effiziente.

## <a name="device-support"></a>Unterstützung von Geräten
<table>
    <colgroup>
    <col width="40%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    </colgroup>
    <tr>
        <td><strong>Eingabemodell</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></td>
    </tr>
     <tr>
        <td>Punkt- und Commit (ganz Hand Interaktion)</td>
        <td>❌ Nicht unterstützt</td>
        <td>✔️ Empfohlen</td>
        <td>✔️ Empfohlen</td>
    </tr>
</table>
<br>
Punkt- und Commit war eines der Eingabe primäre Modelle für HoloLens 2, nutzen das neue articulated Handsymbol tracking-System. Dieses Modell für Benutzereingaben ist auch das primäre Eingabemodell für immersive Headsets durch die Verwendung von Motion-Controller. Punkt- und Commit ist das Eingabemodell, die wir empfehlen, um den Kopf bestaunen zu ersetzen, und Committen für HoloLens (1. Generation). 

## <a name="hand-rays"></a>Hand Strahlung
Für HoloLens-2 erstellen wir eine manuell Chow die von der Mitte des einem Palm schießen. Der Strahl wird als eine Erweiterung des Zeigers behandelt. Ein Ringdiagramm Form Cursor ist am Ende des Strahls an den Speicherort des Strahls, an dem mit einem hitted Objekt schneidet angefügt. Das Objekt, das der Cursor gelangt erhalten gestural Befehle von der Hand. 

Einfache gestural Befehls wird ausgelöst, mit Daumen und Zeigefinger tippbewegung ausführen. Hand-Ray zum zeigen, und tippen Sie auf einen commit für Luft verwenden, können Benutzer eine Schaltfläche oder einen Hyperlink auf ein Web-Inhalte aktivieren. Bei den weitere zusammengesetzten Bewegungen sind Benutzer kann den Webinhalt navigieren und Bearbeiten von 3D-Objekten in einem Abstand. Das visuelle Design des Strahls manuell sollte ebenfalls reagieren, um zu zeigen und commit-Status: <br>
* In den Zustand "zeigen" des Strahls ist Dash eingebunden und der Cursor befindet sich eine Form "Ring".
* Klicken Sie in den Zustand "Commit" des Strahls wird, in eine durchgehende Linie, und der Cursor wird auf einen Punkt verkleinert.<br><br>
![](images/Hand-Rays-720px.jpg)<br>

## <a name="transition-between-near-and-far"></a>Reibungsloser Übergang zwischen am und weit
Anstelle von spezifischen Bewegungen, wie z. B. das zeigen mit Zeigefinger des Strahls, leiten entwerfen wir den Strahl stammen von der Mitte des Palm-Geräte freigeben und reservieren die fünf Finger für weitere gestural Manipulationen. Aus diesem Grund unterstützt HoloLens 2 genau den gleichen Satz von gestensteuerung für nah und Fern Interaktion. Keine zusätzliche Schulung ist erforderlich, wenn der Benutzer von Nähe weit Interaktionen und umgekehrt übertragen. Benutzer können die gleiche Ziehpunkte Geste verwenden, um Objekte auf anderen entfernungen zu bearbeiten. Der Aufruf der Strahlen ist automatisch und NEAR-basierte: <br>
* Wenn ein Objekt in der Arm-Entfernung (ungefähr 50 cm) erreicht ist, sind die Strahlung automatisch für die Interaktion mit nahezu fördern deaktiviert. 
* Wenn das Objekt mehr als 50 cm ist, werden die Strahlung aktiviert.

Dieser Mechanismus ermöglicht Übergang reibungs- und nahtlos.<br>
![](images/Transition-Between-Near-And-Far-720px.jpg)<br>

## <a name="2d-slate-interaction"></a>2D Slate-Interaktion
2D Slate ist holographic Container-hosting von Direct2D-app-Inhalte, z. B. WebBrowser. Das Entwurfskonzept für viel Interaktion mit einem 2D Slate ist die Verwendung von Hand Strahlung zu zeigen, und tippen Sie auf einen commit für Luft.<br>

Für die Interaktion mit der Slate Contant:<br>

* Benutzer können auf einen Link oder eine Schaltfläche, klicken Sie dann die tippbewegung aktivieren zeigen. 
* Benutzer können einerseits verwenden, zum Ausführen einer Geste Navigation, einen Slate-Inhalt einen Bildlauf nach oben und unten durchführen zu können. 
* Benutzer können zwei praktische verwenden, zum Ausführen der Navigation Gesten zum ein- und Auschecken der Slate-Inhalt zu verkleinern.<br><br>

![](images/2D-Slate-Interaction-Far-720px.jpg)<br>

Zum Bearbeiten der 2D slate-selbst:<br>

* Benutzer zeigen den Strahl manuell an den Ecken oder den Kanten in der nächsten Bearbeitung Unterstützung anzuzeigen. 
* Durch Anwenden einer Bewegung der Manipulation auf die Unterstützung, werden Benutzer einheitliche Skalierung über die Unterstützung der Ecke durchführen und können dynamisch umgebrochen in das Slate-Objekt über die Edge-Unterstützung. 
* Eine Bewegung der Manipulation auf die Holobar am oberen Rand der 2D Slate-Objekt anwenden, können Benutzer die gesamte Slate verschieben.<br>

<br>

## <a name="3d-object-manipulation"></a>Bearbeitung des 3D-Objekts
Es gibt zwei Möglichkeiten für Benutzer zum Bearbeiten des 3D-Objekts, Unterstützung basierend Manipulation und nicht-Affordnace basierend Manipulation vorhanden, in der direkten Bearbeitung. Im Punkt- und Commit-Modell sind Benutzer genau die gleichen Aufgaben über die Hand Strahlung erreichen. Es ist keine zusätzliche Schulung erforderlich.<br>

### <a name="affordance-based-manipulation"></a>Unterstützung basierend Bearbeitung
Benutzer verwenden Hand Strahlung zeigen, und zeigen das umgebende Feld und Manipulation visueller Hinweise. Benutzer können die Bewegung der Manipulation anwenden, für das umgebende Feld, das gesamte Objekt verschieben, auf dem Edge visueller Hinweise zum Drehen und die coner visueller Hinweise gleichmäßig skaliert. <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a>Nicht-Unterstützung basierend Bearbeitung
Zeigen Sie Benutzer mit Hand Strahlen, das das umgebende Feld anzuzeigen, und klicken Sie dann direkt Manipulation Gesten darauf anwenden. Einerseits sind die Übersetzung und Drehung des Objekts zugeordnet, während der Übertragung und die Ausrichtung der Hand. Mit zwei Händen können Benutzer zu übersetzen, skalieren und entsprechend der relativen Bewegungen von zwei praktische drehen.<br>

<br>

## <a name="instinctual-gesturers"></a>Instinctual gesturers
Das Konzept der instinctual Gesten für die Zeitpunkt und Commit ist synchron, für die direkte Bearbeitung. Welche Aktionen von Benutzern für die Durchführung eines 3D-Objekts angenommen werden vom Entwurf der Benutzeroberfläche visueller Hinweise geleitet. Ein Steuerungspunkts für kleine würde motivieren, Benutzer mit Daumen und Zeigefinger, verkleinern, während ein großes Objekt Benutzer mit 5 Finger abrufen kann.

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>Symmetrische Entwurf zwischen praktische und 6 FG-controller 
Das Konzept der Punkt und Commit-Modell für die Interaktion mit weit zuerst erstellt und für die Mixed Reality Portal (maschinenlesbarer Pass), in denen Benutzer eine immersive Kopfhörer wear und damit interagieren das 3D-Objekt über Motion-Controller definiert. Die Motion-Controller vorgesehen, Strahlung zum verweist, und Bearbeiten von entfernten Objekte. Es sind Schaltflächen auf den Controllern für den Commit für weitere Funktionen. Wir nutzen das Interaktionsmodell der Strahlung, und fügen Sie sie auf beiden Händen. Bei diesem Entwurf symmetrischen Benutzer, für die MRP kennen müssen nicht eine andere Interaktionsmodell für weit zeigen und Manipulation bei erstmaliger Verwendung von HoloLen 2, erfahren, und umgekehrt.    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>


## <a name="see-also"></a>Siehe auch
* [Blicke und commit](gaze-and-commit.md)
* [Direkte Bearbeitung](direct-manipulation.md)
* [Interaktionsgrundlagen](interaction-fundamentals.md)
