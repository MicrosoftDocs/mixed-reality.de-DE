---
title: Punkt- und Commit mit Hand
description: Übersicht über das Eingabemodell Punkt- und commit
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Gemischte Realität Interaktion, Entwurf, Hololens, Hände gelangen, jetzt zeigen und commit
ms.openlocfilehash: 30f85d2bb455abab3a533e0a829b4fba8cea0a7a
ms.sourcegitcommit: 5b4292ef786447549c0199003e041ca48bb454cd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402384"
---
# <a name="point-and-commit-with-hands"></a>Punkt- und Commit mit Hand
Punkt- und Commit mit Hand ist ein Eingabemodell aus, in dem Benutzer als Ziel, auswählen und Bearbeiten von 2D Inhalt und 3D-Objekten, bei der Entfernung. Diese Technik "weit" Interaktion Realität zu mixed Reality eindeutig ist und keine Möglichkeit Menschen auf natürliche Weise Intereact mit der realen Welt. Z. B. in den Film Superheld *X-Männer*, das Zeichen [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) ist in der Lage, unseren Lesern und zum Bearbeiten von ein entfernte Objekt bei der Entfernung mit seinem Hand. Dies ist nicht für etwas, das Menschen in der Praxis tun können. In HoloLens (AR) und Mixed Reality (VR) statten wir Benutzern mit dieser magische, unterbrechen die physische Einschränkungen der realen Welt nicht nur um ein positives Erlebnis mit holographic Inhalt zu erhalten, sondern auch um die Interaktion effektiver und effizienter zu machen.

## <a name="device-support"></a>Geräteunterstützung

Eingabemodell | [HoloLens (1. Generation)](https://docs.microsoft.com/en-us/windows/mixed-reality/hololens-hardware-details) | HoloLens 2 | [Immersive headsets](https://docs.microsoft.com/en-us/windows/mixed-reality/immersive-headset-hardware-details) |
| ---------| -----| ----- | ---------|
Punkt- und Commit mit Hand | ❌ Nicht unterstützt | ✔️ Empfohlen | ✔️ Empfohlen

Point "und" Commit ", auch bekannt als praktische, ist eine der neuen Features, die das neue articulated Hand-Tracking-System verwendet. Dieses Modell für Benutzereingaben ist auch das primäre Eingabemodell für immersive Headsets durch die Verwendung von Motion-Controller.

## <a name="hand-rays"></a>Hand Strahlung

Für HoloLens-2 haben wir ein Strahl von Hand, die von der Mitte des einem Palm Sie Schießen erstellt. Diese Chow wird als eine Erweiterung des Zeigers behandelt. Ein Cursor ringförmige ist bis zum Ende des Strahls, um den Speicherort anzugeben, wo des Strahls mit einem Zielobjekt überlappt, angefügt. Das Objekt, dem der Cursor zu gelangt kann gestural Befehle dann von der Hand empfangen werden.

Diese grundlegenden gestural-Befehl wird mit dem Daumen und Zeigefinger zum Ausführen der tippbewegung Aktion ausgelöst. Mithilfe des Strahls Hand zum zeigen, und tippen Sie auf einen commit für Luft zu verwenden, können Benutzer eine Schaltfläche oder einen Hyperlink auf ein Web-Inhalte aktivieren. Bei den weitere zusammengesetzten Bewegungen sind Benutzer Webinhalte navigieren und Bearbeiten von 3D-Objekten aus der Entfernung kann. Das visuelle Design des Strahls Hand muss dieser Punkt und Commit-Status, als beschrieben und wie unten gezeigt ebenfalls reagieren: 

* In der *zeigt* Status des Strahls ist eine gestrichelte Linie, und der Cursor befindet sich eine Form "Ring".
* In der *Commit* Status des Strahls, die in einer durchgezogenen Linie umwandelt und der Cursor wird auf einen Punkt verkleinert.

![](images/Hand-Rays-720px.jpg)

## <a name="transition-between-near-and-far"></a>Reibungsloser Übergang zwischen am und weit

Anstatt bestimmte Bewegung, z. B. "zeigt mit Zeigefinger" zur Weiterleitung des Strahls, wir den Strahl stammen, von der Mitte des Palm-Geräte freigeben und reservieren die fünf Finger für weitere manipulativen Bewegungen wie z. B. verkleinern und ziehen Sie entworfen. Bei diesem Entwurf erstellen wir nur ein mentales Modell genau den gleichen Satz von gestensteuerung für nah und Fern Interaktionen unterstützt. Sie können die gleiche Ziehpunkte Geste verwenden, zum Bearbeiten von Objekten an unterschiedliche Abstände. Der Aufruf der Strahlen ist automatisch und NEAR-basierte:

*  Wenn ein Objekt in der Arm-Entfernung (ungefähr 50 cm) erreicht ist, sind die Strahlung automatisch für die Interaktion mit nahezu fördern deaktiviert.
*  Wenn das Objekt mehr als 50 cm ist, werden die Strahlung aktiviert. Der Übergang sollte reibungs- und nahtlos.

![](images/Transition-Between-Near-And-Far-720px.jpg)

## <a name="2d-slate-interaction"></a>2D Slate-Interaktion

2D Slate ist holographic Container-hosting von Direct2D-app-Inhalte, z. B. WebBrowser. Das Entwurfskonzept für viel Interaktion mit einem 2D Slate ist Hand Strahlung Target "und" Air, tippen Sie auf auswählen. Nachdem Ihr Ziel ist mit einer Hand Chow, können Benutzer tippen, um einen Link oder eine Schaltfläche auszulösen Luft. Sie können einerseits verwenden, um "tippen, und ziehen Sie Luft auf" einen Slate-Inhalt einen Bildlauf nach oben und unten durchführen. Die relative Bewegung der Verwendung von in die Luft tippen, und ziehen Sie zwei praktische kann in und das Slate-Inhalt vergrößern.

Zielgruppenadressierung von dem Strahl manuell an den Ecken und Kanten werden die nächsten Bearbeitung Unterstützung. Klicken Sie durch "Ziehpunkte, und ziehen Sie", die die Manipulation visueller Hinweise, Benutzer ausführen können Symbole mit einheitlicher Skalierung über die Ecke visueller Hinweise, und können umbrechen der Slate-Objekt über die Edge visueller Hinweise. Konturkreise per ziehbewegung aus, und ziehen die Holobar am oberen Rand der 2D Klappe können Benutzer die gesamte Slate verschieben.

![](images/2D-Slate-Interaction-Far-720px.jpg)

Zum Bearbeiten der 2D slate-selbst:<br>

* Benutzer zeigen den Strahl manuell an den Ecken oder den Kanten in der nächsten Bearbeitung Unterstützung anzuzeigen. 
* Durch Anwenden einer Bewegung der Manipulation auf die Unterstützung, werden Benutzer einheitliche Skalierung über die Unterstützung der Ecke durchführen und können dynamisch umgebrochen in das Slate-Objekt über die Edge-Unterstützung. 
* Eine Bewegung der Manipulation auf die Holobar am oberen Rand der 2D Slate-Objekt anwenden, können Benutzer die gesamte Slate verschieben.<br>

<br>

## <a name="3d-object-manipulation"></a>Bearbeitung des 3D-Objekts

Es gibt zwei Möglichkeiten für Benutzer zum Bearbeiten von 3D-Objekt, Bearbeitung Unterstützung basierende und nicht-Unterstützung basierend Manipulation vorhanden, in der direkten Bearbeitung. Im Punkt- und Commit-Modell sind die Benutzer genau die gleichen Aufgaben über die Hand Strahlung erreichen. Es ist keine zusätzliche Schulung erforderlich.<br>

### <a name="affordance-based-manipulation"></a>Unterstützung basierende Bearbeitung
Benutzer verwenden Hand Strahlung zeigen, und zeigen das umgebende Feld und Manipulation visueller Hinweise. Benutzer können die Bewegung der Manipulation anwenden, für das umgebende Feld, das gesamte Objekt verschieben, auf dem Edge visueller Hinweise zum Drehen und die coner visueller Hinweise gleichmäßig skaliert. <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a>Nicht-Unterstützung basierend Bearbeitung
Zeigen Sie Benutzer mit Hand Strahlen, das das umgebende Feld anzuzeigen, und klicken Sie dann direkt Manipulation Gesten darauf anwenden. Einerseits sind die Übersetzung und Drehung des Objekts zugeordnet, während der Übertragung und die Ausrichtung der Hand. Mit zwei Händen können Benutzer zu übersetzen, skalieren und entsprechend der relativen Bewegungen von zwei praktische drehen.<br>

<br>

## <a name="instinctual-gesturers"></a>Instinctual gesturers
Das Konzept der instinctual Gesten für die Zeitpunkt und Commit ähnelt, die für die direkte Bearbeitung. Die Gesten Benutzer zum Ausführen eines 3D-Objekts angenommen werden, werden vom Entwurf der Benutzeroberfläche visueller Hinweise geleitet. Ein Steuerungspunkts für kleine motivieren beispielsweise kann Benutzer mit dem Daumen und Zeigefinger, verkleinern, während ein Benutzer möglicherweise ein größeres Objekt mit allen 5 Fingern abrufen möchten.

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>Symmetrische Entwurf zwischen praktische und 6 FG-controller 
Das Konzept der Punkt und der Commit für die Interaktion mit weit wurde anfänglich erstellt und für die Mixed Reality Portal (maschinenlesbarer Pass), in denen ein Benutzer präsentiert Ihnen eine immersive Kopfhörer und interagiert mit 3D-Objekte über Motion-Controller definiert. Die Motion-Controller vorgesehen, Strahlung zum verweist, und Bearbeiten von entfernten Objekte. Es sind Schaltflächen auf den Controllern für unterschiedliche Aktionen weiter zu committen. Wir nutzen das Interaktionsmodell der Strahlung und diese beiden Händen angefügt. Bei diesem Entwurf symmetrischen Benutzer, die mit MRP vertraut sind, erfahren, eine andere Interaktionsmodell für weit verweist und-Bearbeitung sie HoloLen 2 verwenden müssen nicht und umgekehrt.    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>

## <a name="instinctual-gestures"></a>Instinctual Gesten

![](images/Instinctual-Gestures-Far-720px.jpg)

## <a name="see-also"></a>Siehe auch
* [Anvisieren mit dem Kopf und Ausführen](gaze-and-commit.md)
* [Direkte Manipulation mit den Händen](direct-manipulation.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)

