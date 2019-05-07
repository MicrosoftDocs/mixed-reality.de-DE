---
title: Direkte Bearbeitung
description: Übersicht über das Eingabemodell für die direkte Bearbeitung
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
keywords: Gemischte Realität, die Blicke, die Blicke Ziel ist, handelt es sich bei der Interaktion, Entwerfen
ms.openlocfilehash: d855955d44c1cf074849992e5dd7b36b54675fdd
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2019
ms.locfileid: "64581330"
---
# <a name="direct-manipulation"></a>Direkte Bearbeitung
Direkte Bearbeitung wird ein Eingabe-Modell, bei dem berühren Hologramme direkt mit der Hand. Das Ziel mit einer direkten Bearbeitung ist, dass Objekte verhalten sich genau wie sie in der realen Welt. Einfach durch Drücken sie die Schaltflächen aktiviert werden können und 2D-Inhalt verhält sich wie ein virtuelles Touchscreen Objekte können am einfachsten, sie abgerufen werden.  Aus diesem Grund direkte Bearbeitung für die Benutzer sich einfach ist, und es macht Spaß zu.  Es gilt eine "in der Nähe" Eingabemodell, was bedeutet, dass es am besten verwendet wird, für die Interaktion mit Inhalt, der in den Waffen erreicht ist.

Eine Schlüsselkomponente, mit der direkten Bearbeitung leicht zu erlernen, ist die Unterstützung-basierte. Es gibt keine symbolischen Gesten auf Benutzer zu vermitteln. Um ein visuelles Element, die verwendete oder Element erfasst werden können, sollten alle Interaktionen erstellt werden.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Eingabemodell</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></td>
    </tr>
     <tr>
        <td>Direkte Bearbeitung (in der Nähe von Hand-Aktivität)</td>
        <td>❌ Nicht unterstützt</td>
        <td>✔️ Empfohlen</td>
        <td>➕ Eine alternative Option jedoch <a href="point-and-commit.md">Punkt- und Commit (ganz Interaktion)</a> wird empfohlen,</td>
    </tr>
</table>

Direkte Bearbeitung ist eine primäre Eingabemodell für HoloLens 2, nutzen das neue articulated Handsymbol tracking-System. Das Eingabemodell wird sind auch immersive Headsets durch die Verwendung von Motion-Controllern verfügbar, jedoch nicht empfohlen, dass es sich bei der Interaktion außerhalb der Bearbeitung des Objekts ein primäres Mittel.  Direkte Manipluation ist nicht verfügbar, für HoloLens v1.

## <a name="collidable-fingertip"></a>Collidable fingertippen
Für HoloLens-2 sind echte Hände des Benutzers erkannt und als linken und rechten skeletal Modelle interpretiert. Um das Konzept der berühren Hologramme direkt mit der Hand zu implementieren, konnte im Idealfall 5 collider 5 Evaluieren der einzelnen Hand skeletal-Modelle zugeordnet werden. Allerdings dazu führen, dass in der Praxis aufgrund des mangels eines praktisch Feedback, 10 collidable evaluieren viele unerwartete und unvorhersehbare Konflikte mit Hologramme. Daher empfiehlt es sich um ein "collider" nur für jeden Index Finger zu versetzen. Die collidable Index, die schnell zur Hand stehenden weiterhin als aktive Touch-Punkte für verschiedene Touchgesten, die im Zusammenhang mit anderen Finger, z. B. 1 Finger Press, 1 Finger dienen können, tippen Sie auf, 2 drücken Sie die Finger und drücken Sie die 5 Finger.

![Collidable fingertippen-Bild](images/Collidable-Fingertip-720px.jpg)<br>

### <a name="sphere-collider"></a>Kugel "collider"
Anstatt zufällige Standardform zu verwenden, wird empfohlen, eine Kugel "collider" zu verwenden und visuell gerendert, um eine bessere Hinweise für die Ziel-nahezu angezeigt werden. Der Kugel Durchmesser sollte es sich um die Stärke des Fingers Index um Touch Genauigkeit zu erhöhen übereinstimmen. Sie werden einfach, die Variable der Stärke der Finger durch das Handsymbol-API-Aufrufen abzurufen.

<br>

### <a name="fingertip-cursor"></a>Fingertippen cursor
Zusätzlich zum Rendern einer collidable Kugel auf den Index fingertippen, erstellen wir ein vorab-Lösung, die fingertippen Cursor, um besser in der Nähe von Zielgruppenadressierung interaktiv zu erzielen. Es ist ein Ringdiagramm Form Cursor auf den Index fingertippen angefügt. Entsprechend der Nähe ausrichten reagiert er dynamisch an ein Ziel bei der Ausrichtung und die Größe wie unten gezeigt:
* Wenn ein Index in Richtung ggf. ein Hologramm fingerbewegung, wird der Cursor ist immer auf die Oberfläche des Hologramm parallel und allmählich ihre Größe entsprechend verkleinert. 
* Sobald sich der Finger berühren die Oberfläche, wird der Cursor verkleinert wird, in einem Punkt und gibt ein touchereignis.

<br> Mit dem interaktiven Feedback können Benutzer hohen Genauigkeit, die in der Nähe von Aufgaben, z. B. einen Link in einer Web-Inhalte auslösen, oder Drücken einer Schaltfläche auf erreichen. <br>

![Cursorbild fingertippen](images/Fingertip-Cursor-720px.jpg)<br>

## <a name="bounding-box-with-proximity-shader"></a>Umgebendes Feld mit Near-shader
Der – Hologramm selbst muss auch der sowohl SEH- und Feedback zum kompensieren des Mangel an praktisch Feedback. Generieren wir das Konzept des umgebenden Felds mit Near-Shader. Ein umgebendes Feld ist ein volumetrische erforderliche-Bereich, der ein 3D-Objekt einschließt. Das umgebende Feld verfügt über eine interaktive Rendermethode NEAR-Shader aufgerufen. Der NEAR-Shader verhält sich wie folgt:

* Wenn der Finger Index innerhalb eines Bereichs ist, wird ein fingertippen Spot auf der Oberfläche des umgebenden Felds umgewandelt. 
* Wenn die fingertippen näher an der Oberfläche erhält, fasst entsprechend Rampenlicht. 
* Sobald die fingertippen Tippen Sie auf die Oberfläche, wird die gesamte umgebendes Feld ändert sich die Farbe oder visuellen Effekt der Touch-Zustand entsprechend zu generieren. 
* In der Zwischenzeit kann Soundeffekt aktiviert werden, um die visual Berührungsfeedback zu verbessern.

![Umgebendes Feld mit Near-Shader-image](images/Bounding-Box-With-Proximity-Shader-720px.jpg)<br>

## <a name="pressable-button"></a>Schaltfläche "pressable"
Mit einem collidable fingertippen können Benutzer nun für die Interaktion mit äußerst wichtigste holographic Benutzeroberflächenkomponenten, pressable Schaltfläche. Eine pressable Schaltfläche ist eine holographic Schaltfläche, die speziell für die direkte Finger drücken. In diesem Fall enthält eine Schaltfläche pressable aufgrund des mangels eines praktisch Feedback, einige Mechanismen ein, um praktisch Feedback in Angriff zu nehmen Probleme im Zusammenhang mit. 
* Der erste Mechanismus ist mit Near-Shader BoundingBox-Element der im vorherigen Abschnitt bereits behandelt wurde. Verarbeitet werden, ein besseres Verständnis der NEAR für Benutzer Ansatz und geben Sie Kontakt mit einer Schaltfläche. 
* Die zweite Hebung ist. Nach einem fingertippen auf die Schaltfläche mit den kontaktiert erstellt Eindruck von Press. Der Mechanismus ist, dass die Schaltfläche mit der eng mit der fingertippen die Tiefe Achse verschoben wird. Die Schaltfläche mit der kann so schnell wie erreichen eine festgelegte Tiefe (beim Klicken) oder diese verlassen der Tiefe (für Release) nach der passierenden ausgelöst werden. 
* Um Feedback zu verbessern, wenn die Schaltfläche ausgelöst wird, sollte der Soundeffekt hinzugefügt werden. 

![Pressable Schaltflächenbild](images/Pressable-Button-720px.jpg)<br>

## <a name="2d-slate-interaction"></a>2D Slate-Interaktion
2D Slate ist holographic Container-hosting von Direct2D-app-Inhalte, z. B. WebBrowser. Das Entwurfskonzept für die Interaktion mit einem 2D Slate über direkte Bearbeitung ist, die Interaktion mit einem physischen Touchscreen mentale Modell zu nutzen.<br> <br>
Für die Interaktion mit dem Slate Kontakt:<br> 
* Benutzer verwenden ein Zeigefinger einen Link oder eine Schaltfläche drücken. 
* Benutzer verwenden Zeigefinger für einen Slate-Inhalt einen Bildlauf nach oben oder unten. 
* Benutzer werden vergrößerungsgesten Index für die ein- und Auschecken der Slate-Inhalt entsprechend der relativen während der Übertragung der Finger-zoom verwenden. 
![2D Slate-Bild](images/2D-Slate-Interaction-720px.jpg)<br>

<br>Zum Bearbeiten der 2D slate-selbst:<br>
* Benutzer können sich in Richtung Ecken und Kanten in der nächsten Bearbeitung visueller Hinweise anzuzeigen Ansatz. 
* Benutzer können am einfachsten mit der Bearbeitung visueller Hinweise, einheitliche Skalierung über die Ecke Affordnaces und über die Edge visueller Hinweise dynamisch umgebrochen. 
* Abrufen der Holobar am oberen Rand der 2D Slate-Objekt können die Benutzer für das gesamte slatebild verschieben.<br><br>

![Abbildung des Slate-Bearbeitung](images/Manipulate-2d-slate-720px.jpg)


## <a name="3d-object-manipulation"></a>Bearbeitung des 3D-Objekts
HoloLens-2 sind die Benutzer mit der Hand, um 3D Hologramphic Objekte direkt zu bearbeiten, durch Anwenden eines umgebenden Felds für jedes Objekt 3D aktiviert. Das umgebende Feld bietet eine bessere Tiefe Eindruck über die NEAR-Shader. Das umgebende Feld gibt es zwei Design-Ansätze für die Bearbeitung des 3D-Objekts:      
### <a name="affordance-based-manipulation"></a>Unterstützung der Bearbeitung Grundlage:
Es ist eine Möglichkeit für Benutzer auf das 3D-Objekt über das umgebende Feld und die Bearbeitung visueller Hinweise, um es herum zu manipulieren. Sobald eines Benutzers manuell in der Nähe eines 3D-Objekts ist, werden das umgebende Feld und die nächste Unterstützung offengelegt. Benutzer können ziehen Sie das umgebende Feld, um das gesamte Objekt, das Edge visueller Hinweise zum Drehen zu verschieben und die coner visueller Hinweise gleichmäßig skaliert.<br>

![3D-Objekt Manipulation-Bild](images/3D-Object-Manipulation-720px.jpg)<br>

### <a name="non-affordance-based-manipulation"></a>Nicht-Unterstützung basierend Bearbeitung:
In diesem Mechanisom ist keine Unterstützung an das umgebende Feld angefügt. Benutzer können nur zeigen das umgebende Feld und dann direkt mit ihm interagieren. Wenn das umgebende Feld mit einer Hand Element erfasst wird, werden die Übersetzung und Drehung des Objekts während der Übertragung und die Ausrichtung des Zeigers zugeordnet. Wenn das Objekt mit zwei Händen Element erfasst wird, können Benutzer zu übersetzen, skalieren und entsprechend der relativen Bewegungen von zwei praktische drehen.<br><br> 

<br><br>
Für die Bearbeitung mit einfacher Genauigkeit erforderlich ist, empfehlen wir Manipulation von Afforance basierend hohes Maß an Granularität bereitstellen. Für die flexible Bearbeitung von werden die Manipulation von nicht-Unterstützung eine gute Wahl, und bietet Benutzern sofortige und verspielte Benutzeroberflächen.


## <a name="instinctual-gestures"></a>Instinctual Gesten
Im Gegensatz zu HoloLens (der 1. Generation), Lehre verschiedene vordefinierte Aktionen von Benutzern, wie z. B. Bloom und Air tippen, HoloLens, 2, bitten wir nicht die Benutzer symbolischen Bewegung zu merken. Alle Bewegungen, die Benutzer benötigen für die Interaktion mit Hologramme und Inhalte sind instinctual. Die Möglichkeit, instinctual Bewegung zu erreichen ist Benutzerhandbuch zum Ausführen von Aktionen durch den Entwurf der Benutzeroberfläche visueller Hinweise. Z. B. wenn Benutzer Ziehpunkte ein Objekt oder mit zwei Finger Verkleinern eines Steuerungspunkts für sollten sollte das Objekt oder der Kontrollpunkt kleine. Wenn wir Benutzer fünf Finger Ziehpunkte ausführen möchten, sollte das Objekt oder der Kontrollpunkt relativ groß sein. Ähnlich wie bei Schaltflächen werden würde eine kleine Schaltfläche beschränken Sie Benutzer mit einem einzelnen Finger, während eine große Schaltfläche sollten Benutzer mit ihren Palm Drücken der Taste drücken.
![](images/Instinctual-Gestures-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a>Symmetrische Entwurf zwischen praktische und 6 FG-Controllern
Möglicherweise haben Sie bemerkt, dass es jetzt Interaktion Parallels, die wir zwischen Hände in AR und während der Übertragung von Controllern in VR zeichnen können. Beide Eingaben können zum Auslösen von direkter Manipulationen in ihrer jeweiligen Umgebung verwendet werden. HoloLens-2 auf den Controller während der Übertragung im WMR führt konturkreise per ziehbewegung aus, und ziehen mit der Hand auf eine schließen-Abstand funktioniert viel in die gleiche Weise wie die Schaltfläche mit den Ziehpunkte. Dies ermöglicht Ihren Benutzern mit Kenntnisse der Interaktion zwischen den beiden Plattformen und kann nützlich sein, Sie jemals So portieren Sie Ihre app aus einem zum anderen entscheiden sollten.

## <a name="optimizing-with-eye-tracking"></a>Optimierung mit Eye-tracking
Direkte Bearbeitung kann sich magische fühlen, wenn es erwartungsgemäß funktioniert, aber kann auch schnell frustrierend, wenn können nicht Sie Ihre Hand an einer beliebigen Stelle nicht mehr verschieben, ohne dass Sie ggf. ein Hologramm versehentlich ausgelöst werden.
Eye-tracking können möglicherweise besser ermitteln, was die Absicht des Benutzers ist. 

* **Wenn**: Reduzieren Sie fälschlicherweise Auslösen einer Manipulation-Antwort. Eye-tracking kann für ein besseres Verständnis, was ein Benutzer mit gegenwärtig beteiligt ist. Beispiel: Angenommen Sie, dass Sie über eine holographic (Hinweistext) lesen, ist beim Erreichen mehr zum Erfassen von realen Arbeit-Tool.
Auf diese Weise verschieben versehentlich Ihre Hand über einige interaktive holographic Schaltflächen, die Sie noch nicht einmal vor (z. B., sogar außerhalb des Benutzers-Feld bemerkt-der-Ansicht).
Um die Geschichte kurz zu machen: Wenn der Benutzer noch nicht ggf. ein Hologramm seit einer Weile betrachtet, noch ein Touch oder verstehen Ereignis dafür erkannt wurde, ist es wahrscheinlich, dass der Benutzer tatsächlich für die Interaktion mit diesem – Hologramm beabsichtigt war nicht. 

* **Welche**: Abgesehen von der Adressierung falscher positiver Aktivierungen enthält ein weiteres Beispiel besser identifizieren die Hologramme zum Abrufen oder herumzustöbern, da der genaue Schnittpunkt aus Ihrer Perspektive löschen möglicherweise nicht insbesondere dann, wenn mehrere Hologramme nah positioniert sind andere. Während der Eye-Tracking für HoloLens 2 eine bestimmte Einschränkung dazu, wie genau wurde können sie ermitteln, Sie eye Blicke, dies kann immer noch sehr hilfreich für die in der Nähe von Aktivitäten, die aufgrund der Unterschiede von Tiefe zu bei der Interaktion mit manuell eingeben. Dies bedeutet, dass es manchmal schwierig zu bestimmen, ob Ihre Hand hinter oder vor ggf. ein Hologramm genau ein Widget für die Bearbeitung z. B. erfasst ist.

 * **Wo**: Verwenden Sie die Informationen, was ein Benutzer mit Gesten für schnelle auslösende ansieht. Nehmen Sie ggf. ein Hologramm, und ungefähr Tischmitte für das beabsichtigte Ziel. Während dies gut funktioniert in einigen Fällen kann, kann schnell ausführen gestensteuerung hoch ungenaue Zielen führen.
Dies ist, in denen Eye-tracking helfen kann, erfahren Sie, das Handsymbol Vektor zurück an die vorgesehene Position auslösen.

## <a name="see-also"></a>Siehe auch
* [Blicke und commit](gaze-and-commit.md)
* [Punkt- und commit](point-and-commit.md)
* [Interaktionsgrundlagen](interaction-fundamentals.md)

