---
title: Direkte Bearbeitung
description: Übersicht über das Eingabemodell für die direkte Bearbeitung
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
keywords: Gemischte Realität, die Blicke, die Blicke Ziel ist, handelt es sich bei der Interaktion, Entwerfen Sie, praktische in Ihrer Nähe, HoloLens
ms.openlocfilehash: bb44244a3cb932a56703f84ba129def5ee5f9b67
ms.sourcegitcommit: 5b4292ef786447549c0199003e041ca48bb454cd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402359"
---
# <a name="direct-manipulation"></a>Direkte Bearbeitung

Die HoloLens 2 verfügt über eine direkte Bearbeitung Eingabemodell, mit dem Sie die touch-Hologramme Dircly mit der Hand. Das Ziel mit einer direkten Bearbeitung ist für Objekte verhalten sich genau wie sie in der realen Welt. Sie können Schaltflächen zu aktivieren, drücken sie einfach und sogar weitermachen, abrufen und Objekte verschieben. Verhält sich in diesen Szenarien 2D-Inhalt wie virtuelle Touchscreen.

Direkte Bearbeitung ist leicht zu erfahren, und es hat Spaß zu machen. Es gilt eine "übergibt in der Nähe von" Eingabemodell, was bedeutet, dass es am besten verwendet wird, für die Interaktion mit Inhalt, der innerhalb von Arm-Reichweite befindet.

Direkte Bearbeitung basiert auf Unterstützung, d. h. Benutzer geeignet. Es gibt keine symbolischen Gesten auf Benutzer zu vermitteln. Alle Interaktionen werden um ein visuelles Element erstellt, die Sie touch oder abrufen können.

## <a name="device-support"></a>Geräteunterstützung

| Eingabemodell | [HoloLens (1. Generation)](https://review.docs.microsoft.com/en-us/windows/mixed-reality/hololens-hardware-details?branch=master) | HoloLens 2 |[Immersive Headsets](https://review.docs.microsoft.com/en-us/windows/mixed-reality/immersive-headset-hardware-details?branch=master)|
|:-------- | :-------| :--------| :------------|
| Direkte Bearbeitung | ❌ Nicht unterstützt | ✔️ Empfohlen | ➕ Eine Alternative [zeigen und commit mit Hand](point-and-commit.md) wird empfohlen.

Direkte Bearbeitung ist eine primäre Eingabemodell für HoloLens 2 und nutzt die neue articulated System zum Nachverfolgen von Hand. Das Eingabemodell finden Sie auch immersive Headsets durch die Verwendung von Motion-Controller, empfiehlt sich jedoch nicht als Hauptwerkzeug der Interaktion außerhalb der Bearbeitung des Objekts.  Direkte Manipluation ist nicht verfügbar, für HoloLens v1.

## <a name="collidable-fingertip"></a>Collidable fingertippen

Für HoloLens-2 sind echte Hände des Benutzers erkannt und als linken und rechten skeletal Modelle interpretiert. Um das Konzept der berühren Hologramme direkt mit der Hand zu implementieren, konnte im Idealfall 5 collider 5 Evaluieren der einzelnen Hand skeletal-Modelle zugeordnet werden. Allerdings verursacht in der Praxis aufgrund des mangels eines praktisch Feedback, 10 collidable evaluieren unerwartete und unvorhersehbare Konflikte mit Hologramme. 

Daher empfiehlt es sich um ein "collider" nur für jeden Index Finger zu versetzen. Collidable Index problemlos zur Verfügung können weiterhin als aktive Touch-Punkte für verschiedene Touchgesten, die im Zusammenhang mit anderen Finger, z. B. 1 Finger drücken Sie, Finger 1 Tippen Sie auf, drücken Sie die Finger 2 und 5 Finger Press, dienen, wie in der folgenden Abbildung dargestellt.

![Collidable fingertippen-Bild](images/Collidable-Fingertip-720px.jpg)

### <a name="sphere-collider"></a>Kugel "collider"

Anstatt eine zufällige generische Form zu verwenden, wird empfohlen, eine Kugel "collider" zu verwenden und visuell gerendert, um eine bessere Hinweise für die Ziel-nahezu angezeigt werden. Der Kugel Durchmesser sollte es sich um die Stärke des Fingers Index um Touch Genauigkeit zu erhöhen übereinstimmen. Sie werden einfach, die Variable der Stärke der Finger durch das Handsymbol-API-Aufrufen abzurufen.

### <a name="fingertip-cursor"></a>Fingertippen cursor

Zusätzlich zum Rendern einer collidable Kugel auf den Index fingertippen, haben wir eine leistungsfähige Lösung, fingertippen Cursor, erzielen Sie in der Nähe von Zielversionen Benutzerfreundlicher interaktiv erstellt. Es ist ein ringförmige Cursor auf den Index fingertippen angefügt. Entsprechend der Nähe ausrichten reagiert er dynamisch an ein Ziel im Hinblick auf die Ausrichtung und Größe wie im folgenden ausführlicher erläutert:

* Wenn ein Index in Richtung ggf. ein Hologramm fingerbewegung, wird der Cursor ist immer auf die Oberfläche des Hologramm parallel und allmählich ihre Größe entsprechend verkleinert.
* Sobald die Finger auf die Oberfläche berührt, wird der Cursor in einem Punkt verkleinert und gibt ein touchereignis.

Mit dem interaktiven Feedback können Benutzer hohen Genauigkeit, die in der Nähe von Aufgaben wie das Auslösen eines Links für Webinhalte, oder Drücken einer Schaltfläche an, wie unten dargestellt auf erreichen. 

![Cursorbild fingertippen](images/Fingertip-Cursor-720px.jpg)

## <a name="bounding-box-with-proximity-shader"></a>Umgebendes Feld mit Near-shader

Der – Hologramm selbst erfordert auch die Möglichkeit, sowohl SEH- und Feedback zum kompensieren des Mangel an praktisch Feedback geben. Generieren wir das Konzept eines umgebenden Felds mit Near-Shader. Ein umgebendes Feld ist eine minimale volumetrische Bereich, der ein 3D-Objekt einschließt. Das umgebende Feld verfügt über eine interaktive Rendermethode NEAR-Shader aufgerufen. Der NEAR-Shader verhält sich:

* Wenn der Finger Index innerhalb eines Bereichs ist, wird ein fingertippen Spot auf der Oberfläche des umgebenden Felds umgewandelt.
* Wenn die fingertippen näher an der Oberfläche erhält, fasst entsprechend Rampenlicht.
* Sobald die fingertippen Tippen Sie auf die Oberfläche, wird die gesamte umgebendes Feld ändert sich die Farbe oder visuellen Effekt der Touch-Zustand entsprechend zu generieren.
* In der Zwischenzeit kann Soundeffekt aktiviert werden, um die visual Berührungsfeedback zu verbessern.

![Umgebendes Feld mit Near-Shader-image](images/Bounding-Box-With-Proximity-Shader-720px.jpg)

## <a name="pressable-button"></a>Schaltfläche "pressable"

Mit einem collidable fingertippen können Benutzer nun für die Interaktion mit äußerst wichtigste holographic Benutzeroberflächenkomponenten, pressable Schaltfläche. Eine pressable Schaltfläche ist eine holographic Schaltfläche, die speziell für die direkte Finger drücken. Aufgrund des mangels eines praktisch Feedback stellt eine Schaltfläche pressable in diesem Fall einige Mechanismen ein, um praktisch Feedback-bezogene Probleme zu lösen.

* Der erste Mechanismus besteht ein umgebendes Feld mit Near-Shader finden Sie im vorherigen Abschnitt. Verarbeitet werden, ein besseres Verständnis der NEAR für Benutzer Ansatz und geben Sie Kontakt mit einer Schaltfläche.
* Die zweite Hebung ist. Nach einem fingertippen auf die Schaltfläche mit den kontaktiert erstellt Eindruck von Press. Der Mechanismus ist, dass die Schaltfläche mit der eng mit der fingertippen die Tiefe Achse verschoben wird. Die Schaltfläche mit der kann ausgelöst werden, eine angegebene Ebene (auf Press) erreicht oder verlässt die Tiefe (für Release) nach der übertragenen Daten.
* Um Feedback zu verbessern, wenn die Schaltfläche ausgelöst wird, sollte der Soundeffekt hinzugefügt werden.

![Pressable Schaltflächenbild](images/Pressable-Button-720px.jpg)

## <a name="2d-slate-interaction"></a>2D Slate-Interaktion

2D Slate ist holographic Container-hosting von Direct2D-app-Inhalte, z. B. WebBrowser. Das Entwurfskonzept für die Interaktion mit einem 2D Slate über direkte Bearbeitung ist, die Interaktion mit einem physischen Touchscreen mentale Modell zu nutzen.

Der Slate Kontakt zu interagieren:

* Verwenden Sie eine Zeigefinger, einen Link oder eine Schaltfläche drücken.
* Verwenden Sie nach oben und unten Zeigefinger, einen Slate-Inhalt ein Bildlauf ausgeführt.
* Benutzer werden vergrößerungsgesten Index für die ein- und Auschecken der Slate-Inhalt entsprechend der relativen während der Übertragung der Finger-zoom verwenden.

![2D Slate-Bild](images/2D-Slate-Interaction-720px.jpg)

Zum Bearbeiten der 2D slate-selbst:

* Nähern Sie sich in Richtung Ecken und Kanten in der nächsten Bearbeitung visueller Hinweise anzuzeigen.
* Ziehen Sie die Manipulation visueller Hinweise, und einheitliche Skalierung über die Ecke visueller Hinweise und über die Edge visueller Hinweise dynamisch umgebrochen.
* Ziehen Sie die Holobar am oberen Rand der 2D Slate-Objekt, die Sie für das gesamte slatebild zu wechseln kann.

![Abbildung des Slate-Bearbeitung](images/Manipulate-2d-slate-720px.jpg)

## <a name="3d-object-manipulation"></a>Bearbeitung des 3D-Objekts

HoloLens-2 können können Benutzern, sich ermöglichen auf die direkte 3D Hologramphic-Objekte, die durch Anwenden eines umgebenden Felds für jedes Objekt 3D bearbeiten. Das umgebende Feld bietet eine bessere Tiefe Eindruck über die NEAR-Shader. Das umgebende Feld gibt es zwei Design-Ansätze für die Bearbeitung des 3D-Objekts.

### <a name="affordance-based-manipulation"></a>Unterstützung basierende Bearbeitung

Dadurch können Sie das 3D-Objekt über einem umgebenden Feld und die Bearbeitung visueller Hinweise, um es herum zu manipulieren. Sobald eines Benutzers manuell in der Nähe eines 3D-Objekts ist, werden das umgebende Feld und die nächste Unterstützung offengelegt. Benutzer ziehen können Sie das umgebende Feld, um das gesamte Objekt, das Edge visueller Hinweise zum Drehen und die Ecke visueller Hinweise gleichmäßig skaliert zu verschieben.

![3D-Objekt Manipulation-Bild](images/3D-Object-Manipulation-720px.jpg)

### <a name="non-affordance-based-manipulation"></a>Nicht-Unterstützung basierend Bearbeitung

Bei diesem Mechanismus werden ist keine Unterstützung an das umgebende Feld angefügt. Benutzer können nur zeigen das umgebende Feld und dann direkt mit ihm interagieren. Wenn das umgebende Feld mit einer Hand Element erfasst wird, werden die Übersetzung und Drehung des Objekts während der Übertragung und die Ausrichtung des Zeigers zugeordnet. Wenn das Objekt mit zwei Händen Element erfasst wird, können Benutzer zu übersetzen, skalieren und entsprechend der relativen Bewegungen von zwei praktische drehen.

Spezifische bestimmte Bearbeitung ist erforderlich, Genauigkeit, es wird empfohlen, **Bearbeitung Unterstützung basierende**, da es sich um ein hohes Maß an Granularität bietet. Für die flexible Bearbeitung, wir empfehlen Ihnen verwendet **nicht Unterstützung Manipulation** sind für die sofortige und verspielte Benutzeroberflächen.

## <a name="instinctual-gestures"></a>Instinctual Gesten

Im Gegensatz zu HoloLens (der 1. Generation), wir unterrichtet Benutzer einige vordefinierte Bewegungen wie z. B. Bloom und Air, tippen Sie auf. HoloLens-2 Fragen wir uns nicht die Benutzer symbolischen Gesten merken. Alle erforderlichen Benutzergesten, müssen Benutzer zur Interaktion mit Hologramme und Inhalte sind instinctual. Die Möglichkeit, instinctual Bewegung zu erreichen ist Benutzerhandbuch zum Ausführen von Aktionen durch den Entwurf der Benutzeroberfläche visueller Hinweise.

Z. B. Wenn Sie Ziehpunkte ein Objekt oder einem Kontrollpunkt, mit zwei Finger Pinch empfohlen, sollte das Objekt oder der Kontrollpunkt klein sein. Wenn wir fünf Finger Ziehpunkte ausführen möchten, sollte das Objekt oder der Kontrollpunkt relativ groß sein. Ähnlich wie bei Schaltflächen werden würde eine kleine Schaltfläche beschränken Sie Benutzer mit einem einzelnen Finger, während eine große Schaltfläche sollten Benutzer mit ihren Palm Drücken der Taste drücken.

![](images/Instinctual-Gestures-720px.jpg)

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a>Symmetrische Entwurf zwischen praktische und 6 FG-Controllern

Möglicherweise haben Sie bemerkt, dass es jetzt Interaktion Parallels, die wir zwischen Hände in AR und während der Übertragung von Controllern in VR zeichnen können. Beide Eingaben können zum Auslösen von direkter Manipulationen in ihrer jeweiligen Umgebung verwendet werden. HoloLens-2 auf den Controller während der Übertragung im WMR führt konturkreise per ziehbewegung aus, und ziehen mit der Hand auf eine schließen-Abstand funktioniert viel in die gleiche Weise wie die Schaltfläche mit den Ziehpunkte. Dies bietet Benutzern Kenntnisse der Interaktion zwischen den beiden Plattformen und kann nützlich sein, Sie jemals So portieren Sie Ihre app aus einem zum anderen entscheiden sollten.

## <a name="optimize-with-eye-tracking"></a>Optimieren Sie mit Eye-tracking

Direkte Bearbeitung kann sich magische fühlen, wenn es erwartungsgemäß funktioniert, aber kann auch schnell frustrierend, wenn können nicht Sie Ihre Hand an einer beliebigen Stelle nicht mehr verschieben, ohne dass Sie ggf. ein Hologramm versehentlich ausgelöst werden.
Eye-tracking können möglicherweise besser ermitteln, was die Absicht des Benutzers ist.

* **Wenn**: Reduzieren Sie fälschlicherweise Auslösen einer Manipulation-Antwort. Eye-tracking kann für ein besseres Verständnis, was ein Benutzer mit gegenwärtig beteiligt ist.
Beispiel: Angenommen Sie, dass Sie über eine holographic (Hinweistext) lesen, ist beim Erreichen mehr zum Erfassen von realen Arbeit-Tool.

  Auf diese Weise verschieben Sie Ihre Hand versehentlich auf einige interaktive holographic Schaltflächen, die Sie noch nicht einmal vor (z. B., die sie auch außerhalb des Benutzers Feld bemerkt-der-Ansicht (Blickfeld) ist).

  Um die Geschichte kurz zu machen: Wenn der Benutzer noch nicht ggf. ein Hologramm seit einer Weile betrachtet, noch ein Touch oder verstehen Ereignis dafür erkannt wurde, ist es wahrscheinlich, dass der Benutzer tatsächlich für die Interaktion mit diesem – Hologramm beabsichtigt war nicht.

* **Welche**:  Abgesehen von der Adressierung falscher positiver Aktivierungen enthält ein weiteres Beispiel besser identifizieren die Hologramme zum Abrufen oder herumzustöbern, da der genaue Schnittpunkt aus Ihrer Perspektive löschen möglicherweise nicht insbesondere dann, wenn mehrere Hologramme nah positioniert sind andere.

  Während der Eye-Tracking für HoloLens 2 eine bestimmte Einschränkung dazu, wie genau wurde können sie ermitteln, Sie eye Blicke, dies kann immer noch sehr hilfreich für die in der Nähe von Aktivitäten, die aufgrund der Unterschiede von Tiefe zu bei der Interaktion mit manuell eingeben.  Dies bedeutet, dass es manchmal schwierig zu bestimmen, ob Ihre Hand hinter oder vor ggf. ein Hologramm genau ein Widget für die Bearbeitung z. B. erfasst ist.

* **Wo**: Verwenden Sie Informationen zu den Möglichkeiten eines Benutzers wird mit schnellen - auslösende Bewegungen untersucht. Nehmen Sie ggf. ein Hologramm, und ungefähr Tischmitte für das beabsichtigte Ziel.  

    Während dies in einigen Fällen kann möglicherweise funktioniert einwandfrei, schnell ausführen gestensteuerung hoch ungenaue Ziele. Dies ist, in denen Eye-tracking helfen kann, erfahren Sie, das Handsymbol Vektor zurück an die vorgesehene Position auslösen.

## <a name="see-also"></a>Siehe auch

* [Anvisieren mit dem Kopf und Ausführen](gaze-and-commit.md)
* [Zeigen und Ausführen mit den Händen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
