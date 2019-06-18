---
title: Anvisieren mit dem Kopf und Ausführen
description: Übersicht über das Eingabemodell „Anvisieren mit dem Kopf und Ausführen“
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Anvisieren, Zielbestimmung, Interaktion, Entwurf
ms.openlocfilehash: d9eae3c0cfceba7c2c31425941dfce865f3aa609
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692302"
---
# <a name="head-gaze-and-commit"></a>Anvisieren mit dem Kopf und Ausführen
„Anvisieren mit dem Kopf und Ausführen“ ist ein Eingabemodell, das die Zielbestimmung für ein Objekt umfasst, bei der Ihr Kopf nach vorne gerichtet (Kopfrichtung) ist, und die Interaktion dann mit einer sekundären Eingabemethode (z. B. mit der Handgeste „In die Luft tippen“ oder mit dem Sprachbefehl „Auswählen“) erfolgt. Es gilt als „fernes“ Eingabemodell mit indirekter Bearbeitung, d. h. es wird am besten für die Interaktion mit Inhalten verwendet, die außerhalb der Reichweite der Arme liegen.

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
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Anvisieren mit dem Kopf und Ausführen</td>
        <td>✔️ Empfohlen</td>
        <td>✔️ Empfohlen (dritte Auswahl – <a href="interaction-fundamentals.md">Siehe andere Optionen</a>)</td>
        <td>➕ Alternative Option</td>
    </tr>
</table>

## <a name="head-gaze"></a>Anvisieren mit dem Kopf
Mixed Reality-Headsets nutzen Position und Ausrichtung des Kopfes des Benutzers, um dessen Kopfrichtungsvektor zu bestimmen. Sie können sich dies als einen Laser vorstellen, der direkt zwischen den Augen des Benutzers geradeaus zeigt. Dies ist eine ziemlich grobe Annäherung hinsichtlich der Position, die der Benutzer betrachtet. Ihre Anwendung kann diesen Strahl mit virtuellen oder realen Objekten kreuzen und einen Cursor an dieser Stelle darstellen, um dem Benutzer sein aktuelles Ziel mitzuteilen.

Zusätzlich zum Anvisieren mit dem Kopf umfassen einige Mixed Reality-Headsets wie die HoloLens 2 entsprechende Eyetrackingsysteme, die einen Vektor zum Anvisieren mit den Augen erzeugen. Dies ermöglicht eine präzisere Messung der Position, die der Benutzer betrachtet. Es ist möglich, Interaktionen für „Anvisieren mit dem Kopf und Ausführen“ mithilfe von „Anvisieren mit den Augen“ zu erstellen, aber dies umfasst einen ganz anderen Satz von Designeinschränkungen, die separat im [Artikel zum Eyetracking](eye-tracking.md) behandelt werden.

## <a name="commit"></a>Ausführen
Nachdem ein Objekt oder Element der Benutzeroberfläche anvisiert wurde, kann der Benutzer mithilfe einer sekundären Eingabemethode damit interagieren oder darauf „klicken“. Dies wird als „Ausführen“-Schritt des Modells bezeichnet. Die folgenden Methoden zum Ausführen werden unterstützt:

- Tippbewegung in die Luft
- Aussprechen des Sprachbefehls „Auswählen“ oder eines der gewünschten Sprachbefehle
- Drücken der einzelnen Taste an einem [HoloLens-Klick-Gerät](hardware-accessories.md#hololens-clicker).
- Drücken der Taste „A“ an einem Xbox-Gamepad
- Drücken der Taste „A“ an einem Xbox Adaptive Controller

### <a name="head-gaze-and-air-tap-gesture"></a>Anvisieren mit dem Kopf und Tippbewegung in die Luft
„In die Luft tippen“ ist eine Tippbewegung mit aufrecht gehaltener Hand Um die Methode „In die Luft tippen“ auszuführen, heben Sie Ihren Zeigefinger in die Bereitschaftsposition, führen Sie ihn dann mit dem Daumen zusammen, und heben Sie den Zeigefinger anschließend zur Freigabe wieder nach oben. Bei HoloLens 1 ist „In die Luft tippen“ die häufigste sekundäre Eingabemethode.

![Finger in der Bereitschaftsposition und dann eine Tipp- oder Klickbewegung](images/readyandpress.jpg)<br>

„In die Luft tippen“ ist auch für HoloLens 2 verfügbar und wurde gegenüber der ursprünglichen Version gelockert. Jetzt werden fast alle Arten der Zusammenführung der Finger unterstützt, solange die Hand aufrecht und still gehalten wird. Dadurch kann der Benutzer die Geste viel einfacher erlernen und ausführen.  Diese neue Methode beim „In die Luft tippen“ ersetzt die alte Methode mithilfe derselben API, sodass vorhandene Anwendungen das neue Verhalten automatisch nach dem erneuten Kompilieren für HoloLens 2 erhalten.

### <a name="head-gaze-and-select-voice-command"></a>Anvisieren mit dem Kopf und Sprachbefehl „Auswählen“
Die Sprachsteuerung ist eine der wichtigsten Interaktionsmethoden für Mixed Reality. Sie bietet einen sehr leistungsstarken Mechanismus zum „Freisprechen“ zur Steuerung des Systems. Es gibt verschiedene Arten von Modellen für die Sprachinteraktion:

- Der generische Befehl „Auswählen“, der als sekundäre Eingabe eine „Klick“-Betätigung oder eine Ausführung ermöglicht.
- Objektbefehle wie „Schließen“ oder „Vergrößern“, die als sekundäre Eingabe das Ausführen einer Aktion ermöglichen.
- Globale Befehle wie „Zum Startmenü“, die kein Ziel erfordern.
- Benutzeroberflächen für Unterhaltungen oder Entitäten wie Cortana, die über eine KI-Funktion für natürliche Sprache verfügen.
- Benutzerdefinierte Befehle

Weitere Details und eine ausführliche Liste zu den verfügbaren Befehle und deren Verwendung finden Sie in unserer Anleitung zur [Sprachsteuerung](voice-design.md).


### <a name="head-gaze-and-hololens-clicker"></a>Anvisieren mit dem Kopf und HoloLens-Klick-Gerät
Das HoloLens-Klick-Gerät ist das erste speziell für HoloLens entwickelte Peripheriegerät, das in der HoloLens 1 Development Edition enthalten ist. Das HoloLens-Klick-Gerät ermöglicht es einem Benutzer, mit minimaler Handbewegung zu klicken und „Ausführen“ als sekundäre Eingabemethode zu verwenden. Das HoloLens-Klick-Gerät stellt eine Verbindung zur HoloLens 1 oder 2 über Bluetooth Low Energy (BTLE) her.

![HoloLens-Klick-Gerät](images/hololens-clicker-500px.jpg)<br>
*HoloLens-Klick-Gerät*

Weitere Informationen und Anweisungen zum Koppeln des Geräts finden Sie [hier](hardware-accessories.md#pairing-bluetooth-accessories).




### <a name="head-gaze-and-xbox-wireless-controller"></a>Anvisieren mit dem Kopf und Xbox Wireless Controller
Der Xbox Wireless Controller ermöglicht es, eine „Klick“-Betätigung als sekundäre Eingabe über die Taste „A“ durchzuführen. Das Gerät ist einem Standardsatz von Aktionen zugeordnet, die bei der Navigation und Steuerung des Systems helfen. Wenn Sie den Controller anpassen möchten, verwenden Sie die Xbox Zubehör-App, um Ihren Xbox Wireless Controller zu konfigurieren.

![Xbox Wireless Controller](images/xboxcontroller.jpg)<br>
*Xbox Wireless Controller*

[Koppeln eines Xbox-Controllers mit Ihrem PC](hardware-accessories.md#pairing-bluetooth-accessories)


### <a name="head-gaze-and-xbox-adaptive-controller"></a>Anvisieren mit dem Kopf und Xbox Adaptive Controller
Der Xbox Adaptive Controller wurde in erster Linie für die Bedürfnisse der Spieler mit eingeschränkter Mobilität entwickelt und ist ein einheitlicher Hub für Geräte, der dazu beiträgt, die Barrierefreiheit von Mixed Reality zu erhöhen.

Der Xbox Adaptive Controller ermöglicht es, eine „Klick“-Betätigung als sekundäre Eingabe über die Taste „A“ durchzuführen. Das Gerät ist einem Standardsatz von Aktionen zugeordnet, die bei der Navigation und Steuerung des Systems helfen. Wenn Sie den Controller anpassen möchten, verwenden Sie die Xbox Zubehör-App, um Ihren Xbox Adaptive Controller zu konfigurieren.

![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)<br>
*Xbox Adaptive Controller*

Schließen Sie externe Geräte wie Switches, Tasten, Halterungen und Joysticks an, um eine für Sie einzigartige, benutzerdefinierte Controllerumgebung zu erstellen. Eingaben über Tasten, Ministick und Trigger werden mithilfe von Hilfsgeräten gesteuert, die über 3,5-mm-Buchsen und USB-Anschlüsse angeschlossen sind.

![Xbox Adaptive Controller-Anschlüsse](images/xbox-adaptive-controller-ports.jpg)<br>
*Xbox Adaptive Controller-Anschlüsse*

[Anweisungen zum Koppeln des Geräts](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/en-US/xbox-one/accessories/controllers/xbox-adaptive-controller>Weitere Informationen, die auf der Xbox-Website verfügbar sind</a>


## <a name="design-guidelines"></a>Entwurfsrichtlinien
> [!NOTE]
> Weitere Anleitungen zum Entwurf von „Anvisieren“ sind [bald verfügbar](index.md).

## <a name="head-gaze-targeting"></a>Anvisieren mit dem Kopf
Alle Interaktionen basieren auf der Fähigkeit eines Benutzers, das Element, mit dem er interagieren möchte, unabhängig von der Eingabemethode auszuwählen. In Windows Mixed Reality erfolgt dies in der Regel durch das Anvisieren durch den Benutzer.
Damit ein Benutzer erfolgreich mit einer Umgebung arbeiten kann, muss die vom System berechnete Absicht des Benutzers mit der tatsächlichen Absicht des Benutzers weitestgehend übereinstimmen. In dem Maße, in dem das System die beabsichtigten Aktionen des Benutzers richtig interpretiert, steigen Zufriedenheit und Leistung.


## <a name="target-sizing-and-feedback"></a>Skalieren von Zielen und Feedback
Der Anvisierungsvektor hat wiederholt gezeigt, dass er zur Bestimmung präziser Ziele geeignet ist, aber oftmals funktioniert er bei der Bestimmung größerer Ziele am besten. Mindestzielgrößen von 1 bis 1,5 Grad sollten in den meisten Szenarien erfolgreiche Benutzeraktionen ermöglichen, obwohl Ziele von 3 Grad oft eine höhere Geschwindigkeit ermöglichen. Beachten Sie, dass die Größe, auf die der Benutzer ausgerichtet ist, auch für 3D-Elemente effektiv ein 2D-Bereich ist. Die ihm jeweils zugewandte Projektion sollte der Zielbereich sein. Es ist äußerst hilfreich, einen markanten Hinweis darauf zu geben, dass ein Element „aktiv“ ist (es wurde vom Benutzer anvisiert). Dies kann die Anwendung von sichtbaren „Hover“-Effekten, akustischen Hervorhebungen oder Klicks oder die eindeutige Ausrichtung eines Cursors mit einem Element umfassen.

![Optimale Zielgröße im Abstand von 2 Metern](images/gazetargeting-size-1000px.jpg)<br>
*Optimale Zielgröße im Abstand von 2 Metern*

![Beispiel für die Hervorhebung eines anvisierten Objekts](images/gazetargeting-highlighting-640px.jpg)<br>
*Beispiel für die Hervorhebung eines anvisierten Objekts*

## <a name="target-placement"></a>Zielpositionierung
Benutzer können häufig keine Benutzeroberflächenelemente finden, die in ihrem Sichtfeld sehr hoch oder sehr niedrig positioniert sind, sodass sie sich hauptsächlich auf Bereiche um ihren Hauptfokus konzentrieren (in der Regel in etwa auf Augenhöhe). Die Positionierung der meisten Ziele in einem vernünftigen Bereich auf Augenhöhe kann helfen. Angesichts der Tendenz, dass sich der Benutzer jeweils auf einen relativ kleinen visuellen Bereich konzentrieren kann (der Blickwinkel beträgt etwa 10 Grad), kann die Gruppierung von Benutzeroberflächenelementen in dem Maße, in dem sie konzeptionell verwandt sind, das Verhalten zum Kombinieren der Aufmerksamkeit von Element zu Element nutzen, wenn der Blick eines Benutzers durch einen Bereich schweift. Beachten Sie beim Entwerfen der Benutzeroberfläche die potenziellen großen Unterschiede beim Sichtfeld zwischen HoloLens und immersiven Headsets.

![Beispiel für gruppierte Benutzeroberflächenelemente zur einfacheren Zielbestimmung in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg).<br>
*Beispiel für gruppierte Benutzeroberflächenelemente zur einfacheren Zielbestimmung in Galaxy Explorer*.

## <a name="improving-targeting-behaviors"></a>Verbessern des Verhaltens bei der Zielbestimmung
Wenn die Absicht des Benutzers, etwas anzuvisieren, bestimmt (oder näherungsweise ermittelt) werden kann, ist es möglicherweise sehr hilfreich, „near miss“-Versuche (Beinahekollision) bei der Interaktion so zu akzeptieren, als ob die Zielbestimmung ordnungsgemäß erfolgt wäre. Es gibt eine Reihe erfolgreicher Methoden, die in Mixed Reality-Umgebungen integriert werden können:

### <a name="head-gaze-stabilization-gravity-wells"></a>Stabilisierung beim Anvisieren mit dem Kopf („Gravitationsbrunnen“)
Dies sollte meistens/immer aktiviert sein. Bei diesem Verfahren werden die natürlichen Kopf-/Nackenschwankungen entfernt, die Benutzer möglicherweise aufweisen. Ebenso Bewegungen aufgrund von Verhaltensweisen beim Sehen/Sprechen.

### <a name="closest-link-algorithms"></a>Algorithmen für die engste Verbindung
Diese funktionieren am besten in Bereichen mit wenig interaktiven Inhalten. Wenn es eine hohe Wahrscheinlichkeit gibt, dass Sie das Interaktionsziel eines Benutzers bestimmen können, haben Sie die Möglichkeit, ihre Fähigkeiten zur Zielbestimmung zu ergänzen, indem Sie einfach einen Absichtsgrad annehmen.

### <a name="backdatingpostdating-actions"></a>Rückdatierung/Nachdatierung von Aktionen
Dieser Mechanismus ist hilfreich bei Aufgaben, die Geschwindigkeit erfordern. Wenn ein Benutzer eine Reihe von Zielbestimmungs-/Aktivierungsmanövern mit hoher Geschwindigkeit durchläuft, kann es nützlich sein, eine gewisse Absicht anzunehmen und verpasste Schritte auf Ziele reagieren zu lassen, die der Benutzer kurz vor oder kurz nach der Tippbewegung im Fokus hatte (50 ms vor oder nach der Tippbewegung war bei frühen Tests wirksam).

### <a name="smoothing"></a>Glättung
Dieser Mechanismus ist hilfreich bei Wegstreckenbewegungen und reduziert das leichte Zittern/Schwanken aufgrund der natürlichen Kopfbewegungseigenschaften. Bei der Glättung über Wegstreckenbewegungen, glätten Sie eher nach Größe/Abstand der Bewegungen als nach Zeit.

### <a name="magnetism"></a>Magnetismus
Dieser Mechanismus kann als eine allgemeinere Version der Algorithmen für die engste Verbindung betrachtet werden. Dabei wird ein Cursor in Richtung eines Ziels gezogen oder es werden einfach die Trefferfelder (sichtbar oder nicht) vergrößert, wenn sich Benutzer voraussichtlichen Zielen nähern. Dabei werden Kenntnisse des interaktiven Layouts verwendet, um sich der Absicht des Benutzers besser zu nähern. Dies kann insbesondere bei kleinen Zielen sehr wirkungsvoll sein.

### <a name="focus-stickiness"></a>Fokusbindung
Wenn Sie bestimmen, welche interaktiven Elemente in der Nähe den Fokus erhalten sollen, stellen Sie eine Tendenz für das Element bereit, das gerade über den Fokus verfügt. Dies trägt dazu bei, unkontrolliertes Verhalten beim Fokuswechsel zu reduzieren, wenn Sie mittig zwischen zwei Elementen mit natürlicher Verzerrung schwanken.


## <a name="composite-gestures"></a>Zusammengesetzte Gesten
Apps können mehr als nur einzelne Tippbewegungen erkennen. Durch die Kombination von Tippen, Halten und Loslassen mit der Bewegung der Hand können komplexere zusammengesetzte Gesten ausgeführt werden. Diese zusammengesetzten Gesten oder Gesten auf hoher Ebene bauen auf den räumlichen Eingabedaten auf niedriger Ebene (von „In die Luft tippen“ und „Öffnen“) auf, auf die Entwickler zugreifen können.

### <a name="air-tap"></a>In die Luft tippen
Die Geste „In die Luft tippen“ (wie auch die anderen nachfolgenden Gesten) reagiert nur auf eine bestimmte Tippbewegung. Um andere Tippbewegungen wie „Menü“ oder „Greifen“ zu erkennen, muss Ihre App direkt die Interaktionen auf niedrigerer Ebene verwenden, die oben im Abschnitt über zwei Schlüsselkomponentengesten beschrieben sind.

### <a name="tap-and-hold"></a>Tippen und halten Sie
„Halten“ bedeutet einfach, die Position mit dem Finger nach unten beim „In die Luft tippen“ beizubehalten. Die Kombination von „In die Luft tippen und halten“ ermöglicht eine Vielzahl von komplexeren Interaktionen beim „Klicken und Ziehen“, wenn sie mit Armbewegungen kombiniert werden, z. B. das Aufnehmen eines Objekts anstelle der Aktivierung, oder sekundäre „Mousedown“-Interaktionen (gedrückte Maustaste), wie das Anzeigen eines Kontextmenüs.
Bei der Gestaltung dieser Geste sollte jedoch mit Bedacht vorgegangen werden, da die Benutzer dazu neigen können, ihre Handhaltungen im Laufe einer längeren Geste zu entspannen.

### <a name="manipulation"></a>Manipulation
Mithilfe von Manipulationsgesten können Sie ein Hologramm bewegen, skalieren oder drehen, wenn Sie möchten, dass das Hologramm 1:1 auf die Handbewegungen des Benutzers reagiert. Eine Verwendungsmöglichkeit für solche 1:1-Bewegungen ist es, den Benutzer in der Umgebung zeichnen oder malen zu lassen.
Die anfängliche Zielbestimmung für eine Manipulationsgeste sollte durch Anvisieren oder Zeigen erfolgen. Sobald das Tippen und Halten beginnt, erfolgt jede Manipulation des Objekts durch Handbewegungen, sodass sich der Benutzer während der Manipulation umsehen kann.

### <a name="navigation"></a>Navigation
Navigationsgesten funktionieren wie ein virtueller Joystick und können zur Navigation in Widgets der Benutzeroberfläche, z. B. Radialmenüs, verwendet werden. Sie tippen und halten, um die Geste zu starten, und bewegen dann Ihre Hand in einem normalisierten 3D-Würfel, der um die erste Betätigung herum angeordnet ist. Sie können Ihre Hand entlang der X-, Y- oder Z-Achse zwischen einem Wert von -1 bis 1 bewegen, wobei 0 der Ausgangspunkt ist.
Mithilfe der Navigation können geschwindigkeitsbasierte kontinuierliche Gesten zum Scrollen oder Zoomen erstellt werden, ähnlich dem Scrollen bei einer 2D-Benutzeroberfläche durch Klicken mit der mittleren Maustaste und anschließendes Bewegen der Maus nach oben und unten.

Die „Navigation mit Führungsschienen“ bezieht sich auf die Fähigkeit, Bewegungen entlang einer bestimmten Achse zu erkennen, bis ein bestimmter Schwellenwert auf dieser Achse erreicht ist. Dies ist nur sinnvoll, wenn die Bewegung innerhalb einer Anwendung durch den Entwickler entlang mehrerer Achsen ermöglicht wird, z. B. wenn eine Anwendung so konfiguriert ist, dass sie Navigationsgesten über die X-, Y-Achse erkennt, aber auch die X-Achse mit Führungsschienen angegeben ist. In diesem Fall erkennt das System Handbewegungen über die X-Achse, solange sie innerhalb einer imaginären Führungsschiene auf der X-Achse verbleiben, wenn die Handbewegung auch auf der Y-Achse erfolgt.

Innerhalb von 2D-Apps können Benutzer mit vertikalen Navigationsgesten innerhalb der App scrollen, zoomen oder ziehen. Dadurch werden virtuelle Fingerberührungen in der App eingeführt, um Gesten für die Toucheingabe desselben Typs zu simulieren. Der Benutzer kann auswählen, welche dieser Aktionen durchgeführt werden sollen, indem er zwischen den Tools auf der Symbolleiste über der App wechselt, indem er entweder die Schaltfläche auswählt oder „<Scroll-/Ziehen-/Zoom->Tool“ sagt.

[Weitere Informationen zu zusammengesetzten Gesten](gestures.md#composite-gestures)

## <a name="gesture-recognizers"></a>Gestenerkennung

Ein Vorteil der Gestenerkennung besteht darin, dass Sie einen Gestenerkenner nur für die Gesten konfigurieren können, die das aktuell ausgewählte Hologramm akzeptieren kann. Die Plattform wird nur die zur Unterscheidung dieser besonders unterstützten Gesten erforderliche Mehrdeutigkeitsvermeidung vornehmen. Auf diese Weise kann ein Hologramm, das nur „In die Luft tippen“ unterstützt, jede beliebige Zeitspanne zwischen Drücken und Loslassen akzeptieren, während ein Hologramm, das sowohl Tippen als auch Halten unterstützt, die Tippbewegung nach dem Überschreiten des Schwellenwerts für die Haltezeit in einen Haltevorgang ändern kann.

## <a name="hand-recognition"></a>Handerkennung
HoloLens erkennt Handgesten, indem die Position einer oder beider Hände, die für das Gerät sichtbar sind, verfolgt wird. HoloLens erkennt Hände, wenn sie sich entweder im Bereitschaftszustand (Handrücken mit nach oben gerichtetem Zeigefinger zu Ihnen gewandt) oder im gedrückten Zustand (Handrücken mit nach unten gerichtetem Zeigefinger zu Ihnen gewandt) befinden. Wenn die Hände eine andere Pose einnehmen, werden sie von HoloLens ignoriert.
Sie können für jede Hand, die von HoloLens erkannt wird, auf ihre Position (ohne Ausrichtung) und ihren gedrückten Zustand zugreifen. Wenn sich die Hand dem Rand des Gestenrahmens nähert, erhalten Sie auch einen Richtungsvektor, den Sie dem Benutzer zeigen können, damit er weiß, wie er seine Hand bewegen muss, um sie dorthin zurückzubringen, wo sie von HoloLens erkannt werden kann.

## <a name="gesture-frame"></a>Gestenrahmen
Bei Gesten für HoloLens muss sich die Hand innerhalb eines „Gestenrahmens“ befinden, in einem Bereich, den die Gestenerkennungskameras entsprechend sehen können (ganz grob genommen von der Nase bis zur Taille und zwischen den Schultern). Die Benutzer müssen in diesem Erkennungsbereich sowohl für den Aktionserfolg als auch für die eigene Bequemlichkeit geschult werden (viele Benutzer werden zunächst davon ausgehen, dass sich der Gestenrahmen innerhalb Ihres Sichtfelds der HoloLens befinden muss und daher ihre Arme zum Interagieren auf unbequeme Weise hochhalten). Bei der Verwendung des HoloLens-Klick-Geräts müssen sich Ihre Hände nicht innerhalb des Gestenrahmens befinden.

Insbesondere bei fortlaufenden Gesten besteht die Gefahr, dass Benutzer ihre Hände im Verlauf der Geste außerhalb des Gestenrahmens bewegen (z. B. beim Bewegen eines holografischen Objekts) und nicht das gewünschte Ergebnis erzielen.

Sie sollten die folgenden drei Aspekte berücksichtigen:

- Schulung der Benutzer zur Existenz des Gestenrahmens und zu ungefähren Begrenzungen (dies wird beim HoloLens-Setup vermittelt).

- Benachrichtigung der Benutzer, wenn sich ihre Gesten den Gestenrahmenbegrenzungen innerhalb einer Anwendung nähern bzw. diese überschreiten, da eine verlorene Geste zu unerwünschten Ergebnissen führt. Studien haben die wichtigsten Eigenschaften eines solchen Benachrichtigungssystems gezeigt, und die HoloLens-Shell ist ein gutes Beispiel für diese Art der Benachrichtigung (visuelle Benachrichtigung auf dem zentralen Cursor, der die Richtung angibt, in der die Überschreitung der Begrenzung erfolgt ist).

- Die Folgen des Überschreitens der Begrenzungen des Gestenrahmens sollten minimiert werden. Im Allgemeinen bedeutet dies, dass das Ergebnis einer Geste an der Begrenzung gestoppt, aber nicht rückgängig gemacht werden sollte. Wenn ein Benutzer z. B. ein holografisches Objekt durch einen Raum bewegt, sollte die Bewegung gestoppt werden, wenn der Gestenrahmen überschritten wird, aber das Objekt nicht zum Ausgangspunkt zurückkehren. Der Benutzer empfindet dann möglicherweise eine gewisse Frustration, kann aber die Begrenzungen schneller verstehen und muss nicht jedes Mal seine beabsichtigten Aktionen vollständig neu starten.


## <a name="see-also"></a>Weitere Informationen
* [Direkte Manipulation mit den Händen](direct-manipulation.md)
* [Zeigen und Ausführen mit den Händen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Anvisieren mit dem Kopf und Verweilen](gaze-and-dwell.md)
* [Sprachbefehle](voice-design.md)





