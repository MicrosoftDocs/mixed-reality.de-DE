---
title: Direkte Manipulation mit den Händen
description: Übersicht über das Eingabemodell „Direkte Manipulation“
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Anvisieren, Zielbestimmung, Interaktion, Entwurf, Hände nah beieinander, HoloLens
ms.openlocfilehash: 6e3512eab4070680c48ee8e95240a17e9925822f
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66402390"
---
# <a name="direct-manipulation-with-hands"></a>Direkte Manipulation mit den Händen
Die direkte Manipulation ist ein Eingabemodell, bei dem Hologramme direkt mit den Händen berührt werden. Das Ziel bei der direkten Manipulation ist, dass sich Objekte wie in der realen Welt verhalten. Schaltflächen können einfach durch Drücken aktiviert werden, Objekte können durch Greifen aufgenommen werden und 2D-Inhalte verhalten sich wie ein virtueller Touchscreen.  Aus diesem Grund ist die direkte Manipulation für den Benutzer leicht erlernbar und macht auch Spaß.  Es gilt als „nahes“ Eingabemodell, d. h. es wird am besten für die Interaktion mit Inhalten verwendet, die innerhalb der Reichweite der Arme liegen.

Die direkte Manipulation ist angebotsbasiert, d. h. benutzerfreundlich. Es gibt keine symbolischen Gesten, die den Benutzern vermittelt werden müssen. Alle Interaktionen basieren auf einem visuellen Element, das Sie berühren oder greifen können.

## <a name="device-support"></a>Unterstützung von Geräten


| Eingabemodell | [HoloLens (1. Generation)](hololens-hardware-details.md) | HoloLens 2 |[Immersive Headsets](immersive-headset-hardware-details.md)|
|:-------- | :-------| :--------| :------------|
| Direkte Manipulation mit den Händen | ❌ Nicht unterstützt | ✔️ Empfohlen | ➕ Eine Alternative wird empfohlen: [Zeigen und Ausführen mit den Händen](point-and-commit.md).

Die direkte Manipulation ist ein primäres Eingabemodell für HoloLens 2 und nutzt das neue artikulierte Handtracking-System. Das Eingabemodell ist auch bei immersiven Headsets durch den Einsatz von Motion-Controllern verfügbar, wird aber nicht als primäre Möglichkeit zur Interaktion außerhalb der Objektmanipulation empfohlen.  Die direkte Manipulation ist bei HoloLens (1. Generation) nicht verfügbar.


## <a name="collidable-fingertip"></a>Kollisionsfähige Fingerspitze

Bei HoloLens 2 werden die echten Hände des Benutzers als Skelettmodelle der linken und rechten Hand erkannt und interpretiert. Um die Idee, Hologramme direkt mit den Händen zu berühren, zu implementieren, könnten idealerweise fünf Collider an fünf Fingerspitzen der einzelnen Handskelettmodelle angefügt werden. Aufgrund der fehlenden taktilen Rückmeldung haben jedoch zehn kollisionsfähige Fingerspitzen unerwartete und unvorhersehbare Kollisionen mit Hologrammen verursacht. 

Wir empfehlen daher, nur einen Collider an jedem Zeigefinger anzufügen. Die kollidierbaren Zeigefingerspitzen können weiterhin als aktive Berührungspunkte für verschiedene Berührungsgesten mit anderen Fingern dienen, z. B. Drücken mit einem Finger, Tippbewegung mit einem Finger, Drücken mit zwei Fingern und Drücken mit fünf Fingern, wie in der folgenden Abbildung dargestellt.

![Abbildung zur kollisionsfähigen Fingerspitze](images/Collidable-Fingertip-720px.jpg)

### <a name="sphere-collider"></a>Kugel-Collider

Anstatt eine zufällige generische Form zu verwenden, empfehlen wir, einen Kugel-Collider einzusetzen und ihn visuell zu rendern, um bessere Hinweise für die Zielbestimmung in der Nähe bereitzustellen. Der Durchmesser der Kugel muss der Dicke des Zeigefingers entsprechen, um die Genauigkeit bei der Toucheingabe zu erhöhen. Das Abrufen der Variablen für die Fingerdicke gestaltet sich durch den Aufruf der Hand-API einfach.

### <a name="fingertip-cursor"></a>Fingerspitzencursor

Zusätzlich zum Rendern einer kollisionsfähigen Kugel an der Zeigefingerspitze haben wir eine erweiterte Lösung, den Fingerspitzencursor, entwickelt, um interaktiv ein besseres Erlebnis bei der Bestimmung nahegelegener Ziele zu erreichen. Es handelt sich um einen ringförmigen Cursor, der an der Zeigefingerspitze angebracht ist. Entsprechend der Nähe reagiert er dynamisch auf ein Ziel in Bezug auf Ausrichtung und Größe, wie unten beschrieben:

* Wenn sich ein Zeigefinger auf ein Hologramm zubewegt, befindet sich der Cursor immer parallel zur Oberfläche des Hologramms und verkleinert seine Größe entsprechend.
* Sobald der Finger die Oberfläche berührt, schrumpft der Cursor zu einem Punkt und gibt ein Toucheingabeereignis aus.

Mit dem interaktiven Feedback können Benutzer eine hohe Genauigkeit bei Aufgaben zur Zielbestimmung erreichen, z. B. das Auslösen eines Hyperlinks zu Webinhalten oder das Drücken einer Schaltfläche, wie nachfolgend veranschaulicht. 

![Abbildung zum Fingerspitzencursor](images/Fingertip-Cursor-720px.jpg)

## <a name="bounding-box-with-proximity-shader"></a>Begrenzungsrahmen mit Näherungsshader

Das Hologramm selbst erfordert auch die Fähigkeit, sowohl visuelles als auch akustisches Feedback zu liefern, um den Mangel an taktilem Feedback auszugleichen. Dazu erstellen wir das Konzept eines Begrenzungsrahmens mit Näherungsshader. Ein Begrenzungsrahmen ist ein minimaler volumetrischer Bereich, der ein 3D-Objekt umgibt. Der Begrenzungsrahmen verfügt über einen interaktiven Renderingmechanismus, der als Näherungsshader bezeichnet wird. Der Näherungsshader verhält sich wie folgt:

* Wenn sich der Zeigefinger innerhalb eines Bereichs befindet, wird ein Fingerspitzenspotlight auf die Oberfläche des Begrenzungsrahmens gerichtet.
* Wenn sich die Fingerspitze der Oberfläche nähert, verdichtet sich das Spotlight entsprechend.
* Sobald die Fingerspitze die Oberfläche berührt, wechselt der gesamte Begrenzungsrahmen die Farbe oder erzeugt einen visuellen Effekt, um den Toucheingabezustand zu reflektieren.
* In der Zwischenzeit kann ein Soundeffekt aktiviert werden, um das visuelle Feedback der Toucheingabe zu verbessern.

![Abbildung zum Begrenzungsrahmen mit Näherungsshader](images/Bounding-Box-With-Proximity-Shader-720px.jpg)

## <a name="pressable-button"></a>Drückbare Schaltfläche

Mit einer kollisionsfähigen Fingerspitze sind die Benutzer jetzt bereit, mit der sehr grundlegenden holografischen Benutzeroberflächenkomponente, der drückbaren Schaltfläche, zu interagieren. Eine drückbare Schaltfläche ist eine holografische Schaltfläche, die auf den direkten Fingerdruck angepasst ist. Da es an taktilen Feedback mangelt, sorgt eine drückbare Schaltfläche für einige Mechanismen, um auf dem taktilen Feedback basierende Probleme zu beheben.

* Der erste Mechanismus ist ein Begrenzungsrahmen mit Näherungsshader, wie im vorherigen Abschnitt beschrieben. Er dient dazu, den Benutzern ein besseres Gefühl von Nähe zu vermitteln, damit sie sich einer Schaltfläche nähern und mit ihr Kontakt aufnehmen können.
* Der zweite Mechanismus ist die Absenkung. Er erzeugt ein Druckgefühl, nachdem eine Fingerspitze die Schaltfläche berührt hat. Der Mechanismus besteht darin, dass sich die Schaltfläche mit der Fingerspitze eng entlang der Tiefenachse bewegt. Die Schaltfläche kann ausgelöst werden, wenn sie eine bestimmte Tiefe erreicht (beim Drücken) oder die Tiefe wieder verlässt (beim Loslassen), nachdem sie passiert wurde.
* Der Soundeffekt sollte hinzugefügt werden, um das Feedback zu verbessern, wenn die Schaltfläche ausgelöst wird.

![Abbildung zur drückbaren Schaltfläche](images/Pressable-Button-720px.jpg)

## <a name="2d-slate-interaction"></a>2D-Tafel – Interaktion

Eine 2D-Tafel ist ein holografischer Container, der 2D-App-Inhalte hostet (z. B. Webbrowser). Das Konzept für die Interaktion mit einer 2D-Tafel durch direkte Manipulation besteht darin, das mentale Modell der Interaktion mit einem physischen Touchscreen zu nutzen.

So interagieren Sie mit dem Tafelkontakt

* Verwenden Sie einen Zeigefinger, um einen Link oder eine Schaltfläche zu drücken.
* Verwenden Sie einen Zeigefinger, um einen Tafelinhalt nach oben und unten zu scrollen.
* Benutzer verwenden zwei Zeigefinger, um den Tafelinhalt entsprechend der relativen Bewegung der Finger zu vergrößern oder zu verkleinern.

![Abbildung zur 2D-Tafel](images/2D-Slate-Interaction-720px.jpg)

So bearbeiten Sie die eigentliche 2D-Tafel

* Nähern Sie sich mit Ihren Händen den Ecken und Kanten, um die nächstgelegenen Manipulationsangebote zu enthüllen.
* Greifen Sie die Manipulationsangebote, und führen Sie über die Eckenangebote eine einheitliche Skalierung und über die Kantenangebote die Neuanordnung der Tafel aus.
* Greifen Sie die Hololeiste im oberen Bereich der 2D-Tafel, mit der Sie die gesamte Tafel verschieben können.

![Abbildung zur Tafelmanipulation](images/Manipulate-2d-slate-720px.jpg)

## <a name="3d-object-manipulation"></a>3D-Objektbearbeitung

Bei HoloLens 2 können Benutzer ihre Hände in die Lage versetzen, holografische 3D-Objekte direkt zu bearbeiten, indem sie auf die einzelnen 3D-Objekte einen Begrenzungsrahmen anwenden. Der Begrenzungsrahmen sorgt durch seinen Näherungsshader für eine bessere Tiefenwahrnehmung. Mit dem Begrenzungsrahmen gibt es zwei Konstruktionsansätze für die 3D-Objektbearbeitung.

### <a name="affordance-based-manipulation"></a>Angebotsbasierte Bearbeitung

Auf diese Weise können Sie das 3D-Objekt durch einen Begrenzungsrahmen und die damit verbundenen Bearbeitungsangebote manipulieren. Sobald sich die Hand eines Benutzers in der Nähe eines 3D-Objekts befindet, werden der Begrenzungsrahmen und das nächstgelegene Angebot angezeigt. Der Benutzer kann den Begrenzungsrahmen greifen, um das gesamte Objekt zu verschieben, die Kantenangebote greifen, um das Objekt zu drehen, und die Eckenangebote greifen, um eine einheitliche Skalierung vorzunehmen.

![Abbildung zur 3D-Objektbearbeitung](images/3D-Object-Manipulation-720px.jpg)

### <a name="non-affordance-based-manipulation"></a>Bearbeitung ohne Angebot

Bei diesem Mechanismus ist an den Begrenzungsrahmen kein Angebot angefügt. Benutzer können den Begrenzungsrahmen nur anzeigen und dann direkt mit ihm interagieren. Wenn der Begrenzungsrahmen mit einer Hand gegriffen wird, sind Verschiebung und Drehung des Objekts der Bewegung und Ausrichtung der Hand zugeordnet. Wenn das Objekt mit zwei Händen gegriffen wird, kann der Benutzer Verschiebung, Drehung und Skalierung entsprechend der relativen Bewegung der beiden Hände vornehmen.

Bestimmte Bearbeitungen erfordern Genauigkeit, wir empfehlen daher die Verwendung von **angebotsbasierter Bearbeitung**, da sie ein hohes Maß an Granularität bietet. Für eine flexible Bearbeitung empfehlen wir Ihnen, **eine angebotsfreie Bearbeitung** zu verwenden, da sie sofortige und spielerische Umgebungen ermöglicht.

## <a name="instinctual-gestures"></a>Instinktive Gesten

Mit HoloLens (1. Generation) haben wir den Benutzern eine Reihe vordefinierter Gesten vermittelt, z. B. „Öffnen“ und „In die Luft tippen“. Bei HoloLens 2 werden die Benutzer nicht aufgefordert, sich symbolische Gesten zu merken. Alle erforderlichen Benutzergesten, die der Benutzer zur Interaktion mit Hologrammen und Inhalten benötigt, sind instinktiv. Um instinktive Gesten zu erreichen, müssen Benutzer durch den Entwurf von Benutzeroberflächenangeboten dazu angeleitet werden, Gesten auszuführen.

Wenn wir Sie z. B. bestärken, ein Objekt oder einen Kontrollpunkt durch Zusammenführen von zwei Fingern zu greifen, sollte das Objekt oder der Kontrollpunkt klein sein. Wenn Sie mit fünf Fingern greifen sollen, sollte das Objekt oder der Kontrollpunkt relativ groß sein. Bezogen auf Schaltflächen würde eine winzige Schaltfläche die Benutzer darauf beschränken, sie mit einem einzelnen Finger zu drücken, während eine große Schaltfläche die Benutzer veranlassen würde, sie mit ihren Handflächen zu drücken.

![](images/Instinctual-Gestures-720px.jpg)

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a>Symmetrisches Design zwischen Händen und Controllern mit 6 Freiheitsgraden

Sie haben vielleicht bemerkt, dass es jetzt Interaktionsparallelen gibt, die wir zwischen Händen in AR und Motion-Controllern in VR ziehen können. Beide Eingabemethoden können verwendet werden, um direkte Bearbeitungen in ihrer jeweiligen Umgebung auszulösen. In HoloLens 2 funktioniert das Greifen und Ziehen mit den Händen aus nächster Nähe weitgehend so wie die Taste zum Greifen an den Motion-Controllern in WMR. Dies bietet den Benutzern die vertraute Interaktion zwischen den beiden Plattformen, die sich als nützlich erweisen kann, falls Sie sich jemals dazu entscheiden, Ihre App von einer zur anderen Plattform zu portieren.

## <a name="optimize-with-eye-tracking"></a>Optimieren mit Eyetracking

Die direkte Bearbeitung kann sich magisch anfühlen, wenn sie wie beabsichtigt funktioniert. Sie kann aber auch schnell zu Enttäuschungen führen, wenn Sie Ihre Hand nicht mehr bewegen können, ohne unbeabsichtigt ein Hologramm zu aktivieren.
Das Eyetracking kann potenziell helfen, die Absicht des Benutzers besser zu erkennen.

* **Wann**: Reduzieren der fehlerhaften Auslösung einer Bearbeitungsreaktion. Das Eyetracking ermöglicht ein besseres Verständnis dafür, womit sich ein Benutzer gerade beschäftigt.
Stellen Sie sich z. B. vor, Sie lesen einen holografischen (lehrreichen) Text durch, wenn Sie rübergreifen, um Ihr reales Arbeitsgerät aufzunehmen.

Dabei bewegen Sie Ihre Hand versehentlich über einige interaktive holografische Schaltflächen, die Sie vorher noch nicht einmal bemerkt haben (vielleicht lagen sie sogar außerhalb des Sichtfelds des Benutzers).

  Lange Rede kurzer Sinn: Wenn der Benutzer ein Hologramm eine Weile nicht betrachtet hat, aber ein Toucheingabe- oder Greifereignis dafür erkannt wurde, ist es wahrscheinlich, dass der Benutzer nicht wirklich beabsichtigt hat, mit diesem Hologramm zu interagieren.

* **Welche**:  Abgesehen von der Behandlung falsch positiver Aktivierungen umfasst ein weiteres Beispiel die bessere Identifizierung, welche Hologramme zu greifen oder zu drücken sind, da der genaue Schnittpunkt aus Ihrer Sicht möglicherweise nicht eindeutig ist, insbesondere wenn mehrere Hologramme nahe beieinander positioniert sind.

  Während das Eyetracking bei HoloLens 2 eine gewisse Einschränkung aufweist, wie genau es Ihr Anvisieren mit dem Kopf bestimmen kann, ist dies bei nahen Interaktionen aufgrund von Tiefenunterschieden bei der Interaktion mit der Handeingabe möglicherweise sehr hilfreich.  Das bedeutet, dass es manchmal schwierig ist, festzustellen, ob sich Ihre Hand hinter oder vor einem Hologramm befindet, um z. B. ein Widget für die Bearbeitung präzise zu greifen.

* **Wohin**: Verwenden Sie Informationen darüber, was sich ein Benutzer ansieht, mit schnell auslösenden Gesten. Greifen Sie ein Hologramm, und werfen Sie es grob in Richtung Ihres beabsichtigten Ziels.  

    Obwohl dies manchmal sehr gut funktioniert, können schnell ausgeführte Handgesten zu sehr ungenauen Zielen führen. Hier könnte das Eyetracking helfen, den Vektor für den Wurf mit der Hand wieder an die gewünschte Position zu bringen.

## <a name="see-also"></a>Weitere Informationen

* [Anvisieren mit dem Kopf und Ausführen](gaze-and-commit.md)
* [Zeigen und Ausführen mit den Händen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)

