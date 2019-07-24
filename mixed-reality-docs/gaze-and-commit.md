---
title: Anvisieren mit dem Kopf und Ausführen
description: Übersicht über das Eingabemodell „Anvisieren mit dem Kopf und Ausführen“
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Mixed Reality, Anvisieren, Zielbestimmung, Interaktion, Entwurf
ms.openlocfilehash: aeca5ceacf5ae350aa06cb58cc68162f885f6d78
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387678"
---
# <a name="head-gaze-and-commit"></a>Anvisieren mit dem Kopf und Ausführen
Der Kopf-und Commit-Vorgang ist ein Eingabe Modell, das die Ausrichtung auf ein Objekt mit der Richtung ihrer Kopfzeile (Kopfzeile) umfasst und dann mit einer sekundären Eingabe, wie z. b. der Handbewegung oder dem Sprachbefehl SELECT, agiert. Es wird als ein weitreichendes Eingabe Modell mit indirekter Bearbeitung betrachtet, was bedeutet, dass es am besten für die Interaktion mit Inhalten verwendet werden kann

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
Mixed Reality-Headsets nutzen Position und Ausrichtung des Kopfes des Benutzers, um dessen Kopfrichtungsvektor zu bestimmen. Sie können sich dies als einen Laser vorstellen, der direkt zwischen den Augen des Benutzers geradeaus zeigt. Dies ist eine ziemlich grobe Annäherung hinsichtlich der Position, die der Benutzer betrachtet. Die Anwendung kann diesen Strahl mit virtuellen oder echten Objekten überschneiden und einen Cursor an dieser Stelle zeichnen, um dem Benutzer mitzuteilen, was er derzeit als Ziel verwendet.

Zusätzlich zu den Köpfen können einige gemischte Reality-Headsets, wie hololens 2, Eye Tracking-Systeme einschließen, die einen Blick Vektor liefern. Dies ermöglicht eine präzisere Messung der Position, die der Benutzer betrachtet. Es ist möglich, die Interaktion mit Blick und Commit mithilfe des Augenblicks zu erstellen. Dies ist jedoch mit einem ganz anderen Satz von Entwurfs Einschränkungen zu tun, die separat im [Augenblick Artikel](eye-tracking.md)behandelt werden.

## <a name="commit"></a>Ausführen
Nachdem ein Objekt oder ein UI-Element als Ziel verwendet wurde, kann der Benutzer mit einer sekundären Eingabe interagieren oder darauf klicken. Dies wird als „Ausführen“-Schritt des Modells bezeichnet. Die folgenden Methoden zum Ausführen werden unterstützt:

- Luft tippen Bewegung
- Sprechen Sie den Voice-Befehl, wählen Sie oder einen der Ziel Sprachbefehle aus.
- Eine einzelne Schaltfläche auf einem [hololens-Clicker](hardware-accessories.md#hololens-clicker) drücken
- Schaltfläche "A" auf einem Xbox Gamepad drücken
- Schaltfläche "A" auf einem adaptiven Xbox-Controller drücken

### <a name="head-gaze-and-air-tap-gesture"></a>Anvisieren mit dem Kopf und Tippbewegung in die Luft
„In die Luft tippen“ ist eine Tippbewegung mit aufrecht gehaltener Hand Um eine Luft Abzweigung auszuführen, erhöhen Sie den Finger des Indexes an die bereite Position, und drücken Sie dann mit dem Ziehpunkt. Bei hololens (1. Generation) ist Air Tap die häufigste sekundäre Eingabe.

![Finger in der Bereitschaftsposition und dann eine Tipp- oder Klickbewegung](images/readyandpress.jpg)<br>

Air Tap ist auch auf hololens 2 verfügbar. Es wurde von der ursprünglichen Version gelockert. Fast alle Arten von Pinches werden jetzt unterstützt, solange die Hand gleich ist und weiterhin ist. Dadurch kann der Benutzer die Geste viel einfacher erlernen und ausführen. Diese neue Luftlinie ersetzt die alte durch dieselbe API, sodass vorhandene Anwendungen das neue Verhalten automatisch nach der Neukompilierung für hololens 2 aufweisen.

### <a name="head-gaze-and-select-voice-command"></a>Anvisieren mit dem Kopf und Sprachbefehl „Auswählen“
Voice-Befehle sind eine der primären Interaktions Methoden in gemischter Realität. Es bietet einen sehr leistungsfähigen, kostenlosen Mechanismus zur Steuerung des Systems. Es gibt verschiedene Arten von Modellen für die Sprachinteraktion:

- Der generische Befehl SELECT, der eine Klick-oder einen Commit als sekundäre Eingabe ausführt.
- Objekt Befehle wie "Close" oder eine größere Leistung und Commit für eine Aktion als sekundäre Eingabe.
- Für globale Kommas wie "Gehe zu Start" ist kein Ziel erforderlich.
- Benutzeroberflächen für die Konversation oder Entitäten wie Cortana verfügen über eine künstliche Ki-Sprache.
- Benutzerdefinierte Befehle

Weitere Informationen sowie eine comprenhesive Liste der verfügbaren Befehle und deren Verwendung finden Sie in unserem Leitfaden für die [sprach](voice-design.md) Befehlsführung.


### <a name="head-gaze-and-hololens-clicker"></a>Anvisieren mit dem Kopf und HoloLens-Klick-Gerät
Der hololens-Clicker ist das erste Peripheriegerät, das speziell für hololens erstellt wurde. Es ist in der Entwicklungs Edition hololens (1st Gen) enthalten. Der hololens-Clicker ermöglicht dem Benutzer das Klicken mit minimaler Handbewegung und das Commit als sekundäre Eingabe. Der hololens-Clicker stellt mithilfe von Bluetooth Low Energy (btle) eine Verbindung mit hololens (1 St Gen) oder hololens 2 her.

![HoloLens-Klick-Gerät](images/hololens-clicker-500px.jpg)<br>
*HoloLens-Klick-Gerät*

Weitere Informationen und Anweisungen zum Koppeln des Geräts finden Sie [hier](hardware-accessories.md#pairing-bluetooth-accessories).




### <a name="head-gaze-and-xbox-wireless-controller"></a>Anvisieren mit dem Kopf und Xbox Wireless Controller
Der Xbox Wireless-Controller führt mit der Schaltfläche "a" eine Klick-und eine sekundäre Eingabe durch. Das Gerät ist einem Standardsatz von Aktionen zugeordnet, die bei der Navigation und Steuerung des Systems helfen. Wenn Sie den Controller anpassen möchten, verwenden Sie die Xbox accesories-Anwendung, um Ihren Xbox Wireless-Controller zu konfigurieren.

![Xbox Wireless Controller](images/xboxcontroller.jpg)<br>
*Xbox Wireless Controller*

[Koppeln eines Xbox-Controllers mit Ihrem PC](hardware-accessories.md#pairing-bluetooth-accessories)


### <a name="head-gaze-and-xbox-adaptive-controller"></a>Anvisieren mit dem Kopf und Xbox Adaptive Controller
Der Xbox Adaptive Controller ist in erster Linie für die Bedürfnisse von Spielern mit eingeschränkter Mobilität konzipiert und stellt einen einheitlichen Hub für Geräte dar, mit denen gemischte Realität leichter zugänglich gemacht werden kann.

Der Xbox Adaptive Controller führt mit der Schaltfläche "a" eine Klick-und eine sekundäre Eingabe durch. Das Gerät ist einem Standardsatz von Aktionen zugeordnet, die beim Navigieren und Steuern des Systems helfen. Wenn Sie den Controller anpassen möchten, verwenden Sie die Xbox accesories-Anwendung, um Ihren Xbox Adaptive Controller zu konfigurieren.

![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)<br>
*Xbox Adaptive Controller*

Verbinden Sie externe Geräte, wie z. b. Switches, Schaltflächen, bereit Stellungen und Joystick, um eine benutzerdefinierte Controller-benutzerdefinierte Controller Darstellung zu erstellen. Schaltflächen-, fingerstick-und triggereingaben werden mit Hilfsgeräten gesteuert, die über 3.5 mm-und USB-Ports verbunden sind.

![Xbox Adaptive Controller-Anschlüsse](images/xbox-adaptive-controller-ports.jpg)<br>
*Xbox Adaptive Controller-Anschlüsse*

[Anweisungen zum Koppeln des Geräts](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/en-US/xbox-one/accessories/controllers/xbox-adaptive-controller>Weitere Informationen, die auf der Xbox-Website verfügbar sind</a>


## <a name="design-guidelines"></a>Entwurfsrichtlinien
> [!NOTE]
> Weitere Anleitungen zum Entwurf von „Anvisieren“ sind [bald verfügbar](index.md).

## <a name="head-gaze-targeting"></a>Anvisieren mit dem Kopf
Alle Interaktionen basieren auf der Fähigkeit eines Benutzers, das Element, mit dem er interagieren möchte, unabhängig von der Eingabemethode auszuwählen. In Windows Mixed Reality erfolgt dies in der Regel durch das Anvisieren durch den Benutzer.
Damit ein Benutzer erfolgreich mit einer Benutzer Arbeit arbeiten kann, muss das System das Verständnis der Absicht eines Benutzers und die tatsächliche Absicht des Benutzers so genau wie möglich ausrichten. In dem Maße, in dem das System die beabsichtigten Aktionen des Benutzers richtig interpretiert, steigen Zufriedenheit und Leistung.


## <a name="target-sizing-and-feedback"></a>Skalieren von Zielen und Feedback
Der Gaze-Vektor wurde wiederholt angezeigt, um für die fein Ausrichtung geeignet zu sein. er eignet sich jedoch oft am besten für das anvisieren von Brutto-Zielen. Die minimalen Zielgrößen von 1 bis 1,5 Grad ermöglichen in den meisten Szenarien erfolgreiche Benutzeraktionen, wobei Ziele von 3 Grad jedoch häufig eine höhere Geschwindigkeit ermöglichen. Beachten Sie, dass die Größe, auf die der Benutzer ausgerichtet ist, auch für 3D-Elemente effektiv ein 2D-Bereich ist. Die ihm jeweils zugewandte Projektion sollte der Zielbereich sein. Ein Hinweis darauf, dass ein Element "aktiv" ist (der der Benutzer als Ziel verwendet), ist äußerst hilfreich. Dies kann z. b. z. b. sichtbare "Hover"-Effekte, audiohighlights oder Klicks oder eine klare Ausrichtung eines Cursors mit einem Element umfassen.

![Optimale Zielgröße im Abstand von 2 Metern](images/gazetargeting-size-1000px.jpg)<br>
*Optimale Zielgröße im Abstand von 2 Metern*

![Beispiel für die Hervorhebung eines anvisierten Objekts](images/gazetargeting-highlighting-640px.jpg)<br>
*Beispiel für die Hervorhebung eines anvisierten Objekts*

## <a name="target-placement"></a>Zielpositionierung
Benutzer können häufig keine UI-Elemente finden, die in ihrer Ansicht sehr hoch oder sehr niedrig angeordnet sind. Sie konzentrieren sich auf Bereiche, die sich in der Nähe des Hauptfokus befinden, also ungefähr in der Perspektive. Die Positionierung der meisten Ziele in einem vernünftigen Bereich auf Augenhöhe kann helfen. Angesichts der Tendenz, dass sich der Benutzer jeweils auf einen relativ kleinen visuellen Bereich konzentrieren kann (der Blickwinkel beträgt etwa 10 Grad), kann die Gruppierung von Benutzeroberflächenelementen in dem Maße, in dem sie konzeptionell verwandt sind, das Verhalten zum Kombinieren der Aufmerksamkeit von Element zu Element nutzen, wenn der Blick eines Benutzers durch einen Bereich schweift. Beachten Sie beim Entwerfen der Benutzeroberfläche die potenziellen großen Unterschiede beim Sichtfeld zwischen HoloLens und immersiven Headsets.

![Beispiel für gruppierte Benutzeroberflächenelemente zur einfacheren Zielbestimmung in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg).<br>
*Beispiel für gruppierte Benutzeroberflächenelemente zur einfacheren Zielbestimmung in Galaxy Explorer*.

## <a name="improving-targeting-behaviors"></a>Verbessern des Verhaltens bei der Zielbestimmung
Wenn der Benutzer beabsichtigt ist, etwas als Ziel festzustellen, kann es sehr hilfreich sein, fast Fehlversuche bei der Interaktion zu akzeptieren, als wären Sie ordnungsgemäß als Ziel festgelegt. Im folgenden finden Sie eine Reihe von erfolgreichen Methoden, die in gemischte Realität integriert werden können:

### <a name="head-gaze-stabilization-gravity-wells"></a>Stabilisierung beim Anvisieren mit dem Kopf („Gravitationsbrunnen“)
Dies sollte in den meisten Fällen oder in der Zeit aktiviert werden. Diese Methode entfernt die natürlichen Kopf-und Hals Jitter, die Benutzer möglicherweise durch das Aussehen und Sprech Verhalten durchsuchen.

### <a name="closest-link-algorithms"></a>Algorithmen für die engste Verbindung
Diese funktionieren am besten in Bereichen mit wenig interaktiven Inhalten. Wenn eine hohe Wahrscheinlichkeit besteht, dass Sie bestimmen können, mit welchem Benutzer versucht wurde, zu interagieren, können Sie die Zielfunktionen ergänzen, indem Sie eine gewisse Absicht annehmen.

### <a name="backdating-and-postdating-actions"></a>Sicherungs-und postdating-Aktionen
Dieser Mechanismus ist hilfreich bei Aufgaben, die Geschwindigkeit erfordern. Wenn ein Benutzer mit der Geschwindigkeit eine Reihe von Ziel-und Aktivierungs Manövern durchläuft, ist es sinnvoll, eine Absicht anzunehmen und versäumte Schritte zuzulassen, um auf Ziele zu reagieren, auf die sich der Benutzer vor oder nach dem tippen etwas bewegt hat (50 ms vor/nach war in EA wirksam). RLY-Tests).

### <a name="smoothing"></a>Glättung
Dieser Mechanismus eignet sich für die Bewegung von bewegungsbewegungen, wodurch das leichte Jitter und das Wackeln aufgrund natürlicher Kopf Verschiebungs Merkmale reduziert werden. Bei der Glättung von bewegungsbewegungen durch die Größe und die Entfernung von Bewegungen und nicht über die Zeit.

### <a name="magnetism"></a>Magnetismus
Dieser Mechanismus kann sich als allgemeinere Version der nächstgelegenen Verknüpfungs Algorithmen vorstellen: das Zeichnen eines Cursors in Richtung eines Ziels oder das einfache erhöhen der Treffer Felder, egal ob sichtbar oder nicht, wenn Benutzer wahrscheinliche Ziele erreichen, indem Sie einige Kenntnisse des interaktiven Layouts verwenden, um eine bessere Herangehensweise an die Benutzer Absicht. Dies kann insbesondere bei kleinen Zielen sehr wirkungsvoll sein.

### <a name="focus-stickiness"></a>Fokusbindung
Wenn Sie bestimmen, auf welche nahe gelegenen interaktiven Elemente der Fokus gelegt werden soll, stellt die Fokus Bindung eine Abweichung für das Element bereit, das momentan fokussiert ist. Dies trägt dazu bei, das Verhalten von erratischen Fokuswechsel Verhalten zu verringern, wenn Sie in einem Mittelpunkt zwischen zwei Elementen mit natürlichem Rauschen schweben


## <a name="composite-gestures"></a>Zusammengesetzte Gesten

### <a name="air-tap"></a>In die Luft tippen
Die Tap-Bewegung (und die anderen Gesten unten) reagiert nur auf eine bestimmte Abzweigung. Um andere Abzweigungen zu erkennen, wie z. b. Menu oder grasp, muss Ihre Anwendung direkt die Interaktionen auf niedrigerer Ebene verwenden, die im obigen Abschnitt mit zwei wichtigen Komponenten Gesten beschrieben werden.

### <a name="tap-and-hold"></a>Tippen und halten Sie
„Halten“ bedeutet einfach, die Position mit dem Finger nach unten beim „In die Luft tippen“ beizubehalten. Die Kombination aus Luft tippen und halten ermöglicht eine Vielzahl komplexer "klicken und ziehen"-Interaktionen, wenn Sie mit Arm-Bewegung kombiniert werden, wie z. b. das Auswählen eines Objekts, anstatt es zu aktivieren oder um sekundäre Interaktionen wie das zeigen eines Kontextmenüs zu aktivieren.
Bei der Gestaltung dieser Geste sollte jedoch mit Bedacht vorgegangen werden, da die Benutzer dazu neigen können, ihre Handhaltungen im Laufe einer längeren Geste zu entspannen.

### <a name="manipulation"></a>Manipulation
Manipulations Gesten können zum Verschieben, Ändern der Größe oder Drehen eines holograms verwendet werden, wenn das – Hologramm 1:1 auf die Handbewegungen des Benutzers reagieren soll. Eine Verwendungsmöglichkeit für solche 1:1-Bewegungen ist es, den Benutzer in der Umgebung zeichnen oder malen zu lassen.
Die anfängliche Zielbestimmung für eine Manipulationsgeste sollte durch Anvisieren oder Zeigen erfolgen. Wenn Tap und Hold gestartet werden, wird jede Bearbeitung des Objekts von Handbewegungen behandelt, sodass der Benutzer bei der Bearbeitung nicht mehr suchen kann.

### <a name="navigation"></a>Navigation
Navigationsgesten funktionieren wie ein virtueller Joystick und können zur Navigation in Widgets der Benutzeroberfläche, z. B. Radialmenüs, verwendet werden. Sie tippen und halten, um die Geste zu starten, und bewegen dann Ihre Hand in einem normalisierten 3D-Würfel, der um die erste Betätigung herum angeordnet ist. Sie können Ihre Hand entlang der X-, Y- oder Z-Achse zwischen einem Wert von -1 bis 1 bewegen, wobei 0 der Ausgangspunkt ist.
Mithilfe der Navigation können geschwindigkeitsbasierte kontinuierliche Gesten zum Scrollen oder Zoomen erstellt werden, ähnlich dem Scrollen bei einer 2D-Benutzeroberfläche durch Klicken mit der mittleren Maustaste und anschließendes Bewegen der Maus nach oben und unten.

Navigation mit Rails bezieht sich auf die Fähigkeit, Bewegungen auf einer bestimmten Achse zu erkennen, bis ein bestimmter Schwellenwert auf dieser Achse erreicht wird. Dies ist nur nützlich, wenn die Bewegung in mehr als einer Achse durch den Entwickler in einer Anwendung aktiviert ist, z. b. Wenn eine Anwendung so konfiguriert ist, dass Navigations Gesten über die x-, Y-Achse, aber auch die x-Achse mit Rails erkannt werden. In diesem Fall erkennt das System Handbewegungen über die x-Achse, solange Sie auf der x-Achse innerhalb eines imaginären Rails (Handbuchs) bleiben, wenn die Handbewegung auch auf der Y-Achse auftritt.

Innerhalb von 2D-Apps können Benutzer mit vertikalen Navigationsgesten innerhalb der App scrollen, zoomen oder ziehen. Dadurch werden virtuelle Fingerberührungen in der App eingeführt, um Gesten für die Toucheingabe desselben Typs zu simulieren. Benutzer können auswählen, welche dieser Aktionen durchgeführt werden, indem Sie zwischen den Tools auf der Leiste oberhalb der Anwendung wechseln, indem Sie entweder die Schaltfläche auswählen oder die Option "< Scrollmodus/Drag & Zoom > Tools" verwenden.

[Weitere Informationen zu zusammengesetzten Gesten](gestures.md#composite-gestures)

## <a name="gesture-recognizers"></a>Gestenerkennung

Ein Vorteil bei der Verwendung der Gestenerkennung besteht darin, dass Sie eine Gestenerkennung nur für die Gesten konfigurieren können, die das derzeit zielgerichtete – Hologramm annehmen kann. Die Plattform ist nur bei Bedarf eindeutig, um die unterstützten Gesten unterscheiden zu können. Auf diese Weise kann ein – Hologramm, das nur Air Tap unterstützt, jede Zeitspanne zwischen dem Drücken und dem Release akzeptieren, während ein – Hologramm, das sowohl Tap als auch Hold unterstützt, die Abzweigung nach dem Schwellenwert für die Aufbewahrungszeit auf einen Halt herauf Stufen kann.

## <a name="hand-recognition"></a>Handerkennung
HoloLens erkennt Handgesten, indem die Position einer oder beider Hände, die für das Gerät sichtbar sind, verfolgt wird. HoloLens erkennt Hände, wenn sie sich entweder im Bereitschaftszustand (Handrücken mit nach oben gerichtetem Zeigefinger zu Ihnen gewandt) oder im gedrückten Zustand (Handrücken mit nach unten gerichtetem Zeigefinger zu Ihnen gewandt) befinden. Wenn sich die Hände in anderen Posen befinden, ignorieren hololens themz.
Für jede Hand, die hololens erkennt, können Sie ohne Ausrichtung und gedrücktem Zustand auf seine Position zugreifen. Wenn sich die Hand dem Rand des Gestenrahmens nähert, erhalten Sie auch einen Richtungsvektor, den Sie dem Benutzer zeigen können, damit er weiß, wie er seine Hand bewegen muss, um sie dorthin zurückzubringen, wo sie von HoloLens erkannt werden kann.

## <a name="gesture-frame"></a>Gestenrahmen
Für Gesten in hololens muss sich die Hand innerhalb eines Gesten Rahmens befinden, der sich in einem Bereich befindet, der von der Bewegung zur Gesten Messung von der Nase bis zur Taille und von der Schulter aus angezeigt werden kann. Benutzer müssen in diesem Bereich geschult werden, um den Erfolg der Aktion und ihren eigenen Komfort zu erzielen. Viele Benutzer werden anfänglich davon ausgehen, dass sich der Gesten Rahmen in der Ansicht über hololens befinden muss Wenn Sie das hololens-Clicker verwenden, ist es nicht erforderlich, dass sich die Hände innerhalb des Gesten Rahmens befinden.

Im Fall von fortlaufenden Gesten besteht das Risiko, dass Benutzer ihre Hände außerhalb des Gesten Rahmens bewegen, während Sie sich in der Mitte der Bewegung befinden, wenn Sie z. b. ein Holographic-Objekt verschieben und das gewünschte Ergebnis verlieren.

Sie sollten die folgenden drei Aspekte berücksichtigen:

- Benutzer Bildung für das vorhanden sein und die ungefähren Grenzen des Gesten Rahmens. Dies wird während der hololens-Einrichtung vermittelt.

- Benachrichtigen von Benutzern, wenn ihre Gesten die Gesten Rahmen Begrenzungen innerhalb einer Anwendung nähern oder unterbrechen, bis zu dem Ausmaß, in dem eine verlorene Bewegung zu unerwünschten Ergebnissen führt. Research hat die Hauptqualitäten eines solchen Benachrichtigungs Systems aufgezeigt. Die hololens-Shell stellt ein gutes Beispiel für diese Art von Benachrichtigung dar: Visual, auf dem zentralen Cursor, der die Richtung angibt, in der der Begrenzungs Übergang stattfindet.

- Die Folgen des Überschreitens der Begrenzungen des Gestenrahmens sollten minimiert werden. Im Allgemeinen bedeutet dies, dass das Ergebnis einer Geste an der Grenze angehalten und nicht umgekehrt werden soll. Wenn ein Benutzer beispielsweise ein Holographic-Objekt über einen Raum verschiebt, sollte die Bewegung angehalten werden, wenn der Gesten Rahmen verletzt wird und nicht an den Ausgangspunkt zurückgegeben wird. Der Benutzer kann einige Frustrationen erkennen, aber die Grenzen vielleicht besser verstehen und nicht jedes Mal die vollständigen beabsichtigten Aktionen neu starten.


## <a name="see-also"></a>Siehe auch
* [Direkte Manipulation mit den Händen](direct-manipulation.md)
* [Zeigen und Ausführen mit den Händen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Anvisieren mit dem Kopf und Verweilen](gaze-and-dwell.md)
* [Sprachbefehle](voice-design.md)





