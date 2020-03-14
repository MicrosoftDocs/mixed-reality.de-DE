---
title: Blick und Commit
description: 'Allgemeine Übersicht über das Eingabe Modell "Blick und Commit": mithilfe von "Eye" oder "Head Input".'
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Gemischte Realität, Blick, Blick auf die Ausrichtung, Interaktion, Entwurf, Eye Tracking, Head Tracking
ms.openlocfilehash: df152f6a3a6e4ae2d6c32a0c56fbb615bcfa7aa8
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375847"
---
# <a name="gaze-and-commit"></a>Blick und Commit

" _Blick" und "Commit_ " ist ein grundlegendes Eingabe Modell, das eng mit der Interaktion mit unseren Computern verknüpft ist. verwenden Sie dazu die Maus: Punkt- _& Klicken_.
Auf dieser Seite stellen wir zwei Arten von Blick Eingaben (Head-and-Eye-Eye) und verschiedene Typen von COMMIT-Aktionen vor. 
Der _Blick und der Commit_ werden als ein weit reichtes Eingabe Modell mit indirekter Bearbeitung betrachtet.
Dies bedeutet, dass Sie am besten für die Interaktion mit Holographic-Inhalten verwendet werden kann, die nicht erreichbar sind.

Gemischte Reality-Headsets können die Position und Ausrichtung des Benutzer Kopfes verwenden, um den Kopf Richtung Vektor zu bestimmen. Sie können sich dies als einen Laser vorstellen, der direkt zwischen den Augen des Benutzers geradeaus zeigt. Dies ist eine ziemlich grobe Annäherung hinsichtlich der Position, die der Benutzer betrachtet. Die Anwendung kann diesen Strahl mit virtuellen oder echten Objekten überschneiden und einen Cursor an dieser Stelle zeichnen, um dem Benutzer mitzuteilen, was er derzeit als Ziel verwendet.

Zusätzlich zu den Köpfen können einige gemischte Reality-Headsets, wie hololens 2, Eye Tracking-Systeme einschließen, die einen Blick Vektor liefern. Dies ermöglicht eine präzisere Messung der Position, die der Benutzer betrachtet. In beiden Fällen stellt der Blick ein wichtiges Signal für die Absicht des Benutzers dar. Umso besser kann das System die beabsichtigten Aktionen des Benutzers interpretieren und Vorhersagen, die Benutzer Zufriedenheit nimmt zu, und die Leistung wird verbessert.

Im folgenden finden Sie einige Beispiele für die Art und Weise, wie Sie als Entwickler mit gemischter Realität von der Kopf-oder dem Augenblick profitieren können:
* Ihre APP kann den Blick mit den holograms in Ihrer Szene überschneiden, um zu bestimmen, an welcher Stelle die Aufmerksamkeit des Benutzers (genauer mit dem Augenblick) liegt.
* Ihre APP kann Gesten und Controller-Pressen basierend auf dem Blick des Benutzers leiten, sodass der Benutzer nahtlos auf seine Hologramme zugreifen, Sie aktivieren, einlesen, Scrollen oder anderweitig interagieren kann.
* Ihre APP ermöglicht dem Benutzer das Platzieren von holograms auf realen Oberflächen, indem er seinen Blick Strahl mit dem räumlichen Mapping-Gitter schneidet.
* Ihre APP kann wissen, wenn der Benutzer *nicht* in der Richtung eines wichtigen Objekts sucht, was dazu führen kann, dass Ihre APP visuelle und Audiohinweise zum Umwandeln des Objekts erhält.

<br>


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
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Anvisieren mit dem Kopf und Ausführen</td>
        <td>✔️ Empfohlen</td>
        <td>✔️ Empfohlen (dritte Auswahl – <a href="interaction-fundamentals.md">Siehe andere Optionen</a>)</td>
        <td>➕ Alternative Option</td>
    </tr>
         <tr>
        <td>Anvisieren mit den Augen und Ausführen</td>
        <td>❌ nicht verfügbar</td>
        <td>✔️ Empfohlen (dritte Auswahl – <a href="interaction-fundamentals.md">Siehe andere Optionen</a>)</td>
        <td>❌ nicht verfügbar</td>
    </tr>
</table>


## <a name="gaze"></a>Anvisieren

### <a name="eye--or-head-gaze"></a>Augen-oder Haupt Blick?
Es gibt verschiedene Aspekte, die Sie berücksichtigen sollten, wenn Sie sich mit der Frage befassen, ob Sie das Eingabe Modell "Augenblick und Commit" oder "Head-Gaze und Commit" verwenden sollten. Wenn Sie für ein immersives Headset oder für hololens (1st Gen) entwickeln, ist die Wahl einfach: Head-Blick und Commit. Wenn Sie für hololens 2 entwickeln, ist die Auswahl etwas schwieriger. aus diesem Grund ist es wichtig, die Vorteile und Herausforderungen zu verstehen, die in den einzelnen Komponenten enthalten sind.
Wir haben einige umfassende pro-und-con in der nachfolgenden Tabelle kompiliert, um die Zielvorgabe für das Ziel zu vergleichen. Dieser Vorgang ist weit von der Fertigstellung entfernt, und wir empfehlen, dass Sie hier mehr über die Ausrichtung des Augenblicks erfahren:
* [Eye Tracking on hololens 2](eye-tracking.md): Allgemeine Einführung in unsere neue Funktion für die Augen Verfolgung auf hololens 2, einschließlich einiger Entwickler Anleitungen. 
* [Interaktion](eye-gaze-interaction.md)mit Blick auf das Auge: Entwurfs Überlegungen und Empfehlungen bei der Planung der Verwendung von Eye Tracking als Eingabe.

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><strong>Ziel Ausrichtung</strong></td>
        <td><strong>Head-Blick-Ziel</strong></td>
    </tr>
    <tr>
        <td>Schnelle!</td>
        <td>Voran</td>
    </tr>
    <tr>
        <td>Niedriger Aufwand (kaum Text Bewegungen notwendig)</td>
        <td>Mögliche Unannehmlichkeiten (z. b. Hals Belastung)</td>
    </tr>
    <tr>
        <td>Erfordert keinen Cursor, aber es wird ein feines Feedback empfohlen.</td>
        <td>Erfordert, dass ein Cursor angezeigt wird.</td>
    </tr>
    <tr>
        <td>Keine Smooth Eye-Bewegungen – z. b. nicht gut zum Zeichnen</td>
        <td>Kontrollierter und expliziter</td>
    </tr>
    <tr>
        <td>Schwierig für sehr kleine Ziele (z. b. kleine Schaltflächen oder Weblinks)</td>
        <td>Zuverlässiges! Großartiger Fallback!</td>
    </tr>
    <tr>
        <td>...</td>
        <td>...</td>
    </tr>
</table>

Unabhängig davon, ob Sie den Kopf-oder Augenblick für das Eingabe Modell für den Blick und das Commit verwenden, gibt es unterschiedliche Sätze von Entwurfs Einschränkungen, die separat in den Artikeln für den [Augenblick und den Commit](gaze-and-commit-eyes.md) und den [Haupt-und Commit](gaze-and-commit-head.md) -Artikel behandelt werden.

<br>

---

### <a name="cursor"></a>Cursor

:::row:::
    :::column:::
        Für den Kopf Blick sollten die meisten apps einen [Cursor](cursors.md) (oder einen anderen Auditory/visuellen Hinweis) verwenden, um dem Benutzer die Gewissheit zu verschaffen, mit welchem Element er interagiert. In der Regel positionieren Sie diesen Cursor in der Welt, in der der Head-Blick Strahl zuerst ein Objekt schneidet, das ein Hologramm oder eine reale Oberfläche sein kann.<br>
        <br>
        Für den Augenblick empfiehlt es sich im allgemeinen *nicht* , einen Cursor anzuzeigen, da dies für den Benutzer schnell ablenkend und lästig werden kann. Markieren Sie stattdessen visuelle Ziele, oder verwenden Sie einen sehr schwachen Augen Cursor, um sicherzustellen, womit der Benutzer interagieren soll. Weitere Informationen finden Sie in unserem [Entwurfs Leit Faden für die Augen basierte Eingabe](eye-tracking.md) auf hololens 2.
    :::column-end:::
        :::column:::
       ![einen visuellen Beispiel Cursor zum Anzeigen von Blick](images/cursor.jpg)<br>
       *Bild: ein visueller Beispiel Cursor zum Anzeigen des Blicks*
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a>Commit
Nachdem Sie über verschiedene Möglichkeiten zum _betrachten_ eines Ziels gesprochen haben, sprechen wir etwas über den _Commit_ -Teil im _Blick und Commit_.
Nachdem ein Objekt oder ein UI-Element als Ziel verwendet wurde, kann der Benutzer mit einer sekundären Eingabe interagieren oder darauf klicken. Dies wird als Commit-Schritt des Eingabe Modells bezeichnet. 

Die folgenden Methoden zum Ausführen werden unterstützt:
- Tippen Sie auf die Handbewegung (d. h., machen Sie Ihre Hand vor Ihnen, und bringen Sie Ihren Index Finger und Thumb)
- Sagen _Sie "Select"_ oder einen der Ziel Sprachbefehle
- Eine einzelne Schaltfläche auf einem [hololens-Clicker](hardware-accessories.md#hololens-clicker) drücken
- Schaltfläche "A" auf einem Xbox Gamepad drücken
- Schaltfläche "A" auf einem adaptiven Xbox-Controller drücken

### <a name="gaze-and-air-tap-gesture"></a>Bewegung für Blick und Luft tippen
„In die Luft tippen“ ist eine Tippbewegung mit aufrecht gehaltener Hand Um eine Luft Abzweigung auszuführen, erhöhen Sie den Finger des Indexes an die bereite Position, und drücken Sie dann mit dem Ziehpunkt. Bei hololens (1. Generation) ist Air Tap die häufigste sekundäre Eingabe.


:::row:::
    :::column:::
       ![Finger in der Ready-Position](images/readyandpress-ready.jpg)<br>
       **Finger an der Ready-Position**<br>
    :::column-end:::
    :::column:::
       ![drücken Sie den Finger nach unten, um auf](images/readyandpress-press.jpg)<br>
        **Drücken Sie die nach-unten-Taste, um auf**<br>
    :::column-end:::
:::row-end:::


Air Tap ist auch auf hololens 2 verfügbar. Es wurde von der ursprünglichen Version gelockert. Fast alle Arten von Pinches werden jetzt unterstützt, solange die Hand gleich ist und weiterhin ist. Dadurch kann der Benutzer die Geste viel einfacher erlernen und ausführen. Diese neue Luftlinie ersetzt die alte durch dieselbe API, sodass vorhandene Anwendungen das neue Verhalten automatisch nach der Neukompilierung für hololens 2 aufweisen.

<br>

---

### <a name="gaze-and-select-voice-command"></a>"Stimme" und "Select"-Befehl
Voice-Befehle sind eine der primären Interaktions Methoden in gemischter Realität. Es bietet einen sehr leistungsfähigen, kostenlosen Mechanismus zur Steuerung des Systems. Es gibt verschiedene Typen von sprach Interaktions Modellen:

- Der generische SELECT-Befehl, der eine Klick-oder einen Commit als sekundäre Eingabe ausführt.
- Objekt Befehle (z. b. "Close" oder "make it Bigger") führen eine Aktion als sekundäre Eingabe aus und führen Sie aus.
- Für globale Befehle (z. b. "Gehe zu Start") ist kein Ziel erforderlich.
- Benutzeroberflächen für die Konversation oder Entitäten wie Cortana verfügen über eine künstliche Ki-Sprache.
- Benutzerdefinierte Sprachbefehle

Weitere Informationen sowie eine umfassende Liste der verfügbaren Sprachbefehle und deren Verwendung finden Sie in unserer [sprach befehlsanleitung](voice-design.md) .

<br>

---


### <a name="gaze-and-hololens-clicker"></a>Blick und hololens Clicker

:::row:::
    :::column:::
        Der hololens-Clicker ist das erste Peripheriegerät, das speziell für hololens erstellt wurde. Es ist in der Entwicklungs Edition hololens (1st Gen) enthalten. Der hololens-Clicker ermöglicht dem Benutzer das Klicken mit minimaler Handbewegung und das Commit als sekundäre Eingabe. Der hololens-Clicker stellt mithilfe von Bluetooth Low Energy (btle) eine Verbindung mit hololens (1 St Gen) oder hololens 2 her.<br>
        <br>
        [Weitere Informationen und Anweisungen zum Koppeln des Geräts](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *Image: hololens Clicker*
    :::column-end:::
        :::column:::
       ![Hololens Clicker](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a>Blick und Xbox Wireless Controller

:::row:::
    :::column:::
        Der Xbox Wireless-Controller führt mit der Schaltfläche "a" eine Klick-und eine sekundäre Eingabe durch. Das Gerät ist einem Standardsatz von Aktionen zugeordnet, die beim Navigieren und Steuern des Systems helfen. Wenn Sie den Controller anpassen möchten, verwenden Sie die Xbox Accessories-Anwendung, um Ihren Xbox Wireless-Controller zu konfigurieren.<br>
        <br>
        [Koppeln eines Xbox-Controllers mit Ihrem PC](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *Bild: Xbox Wireless Controller*
    :::column-end:::
        :::column:::
       ![Xbox Wireless Controller](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a>Blick und adaptiver Xbox-Controller
Der Xbox Adaptive Controller ist in erster Linie für die Bedürfnisse von Spielern mit eingeschränkter Mobilität konzipiert und stellt einen einheitlichen Hub für Geräte dar, mit denen gemischte Realität leichter zugänglich gemacht werden kann.

Der Xbox Adaptive Controller führt mit der Schaltfläche "a" eine Klick-und eine sekundäre Eingabe durch. Das Gerät ist einem Standardsatz von Aktionen zugeordnet, die beim Navigieren und Steuern des Systems helfen. Wenn Sie den Controller anpassen möchten, verwenden Sie die Xbox Accessories-Anwendung, um den adaptiven Xbox-Controller zu konfigurieren.

![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)<br>
*Xbox Adaptive Controller*

Verbinden Sie externe Geräte, wie z. b. Switches, Schaltflächen, bereit Stellungen und Joystick, um eine benutzerdefinierte Controller-benutzerdefinierte Controller Darstellung zu erstellen. Schaltflächen-, fingerstick-und triggereingaben werden mit Hilfsgeräten gesteuert, die über 3.5 mm-und USB-Ports verbunden sind.

![Xbox Adaptive Controller-Anschlüsse](images/xbox-adaptive-controller-ports.jpg)<br>
*Xbox Adaptive Controller-Anschlüsse*

[Anweisungen zum Koppeln des Geräts](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Weitere Informationen, die auf der Xbox-Website verfügbar sind</a>

<br>

---

## <a name="composite-gestures"></a>Zusammengesetzte Gesten

### <a name="air-tap"></a>In die Luft tippen
Die Tap-Bewegung (und die anderen Gesten unten) reagiert nur auf eine bestimmte Abzweigung. Um andere Abzweigungen zu erkennen, wie z. b. Menu oder grasp, muss Ihre Anwendung direkt die Interaktionen auf niedrigerer Ebene verwenden, die im obigen Abschnitt mit zwei wichtigen Komponenten Gesten beschrieben werden.

### <a name="tap-and-hold"></a>Tippen und halten
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

[Weitere Informationen zu zusammengesetzten Gesten](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a>Gestenerkennung

Ein Vorteil bei der Verwendung der Gestenerkennung besteht darin, dass Sie eine Gestenerkennung nur für die Gesten konfigurieren können, die das derzeit zielgerichtete – Hologramm annehmen kann. Die Plattform ist nur bei Bedarf eindeutig, um die unterstützten Gesten unterscheiden zu können. Auf diese Weise kann ein – Hologramm, das nur Air Tap unterstützt, jede Zeitspanne zwischen dem Drücken und dem Release akzeptieren, während ein – Hologramm, das sowohl Tap als auch Hold unterstützt, die Abzweigung nach dem Schwellenwert für die Aufbewahrungszeit auf einen Halt herauf Stufen kann.

## <a name="hand-recognition"></a>Handerkennung
HoloLens erkennt Handgesten, indem die Position einer oder beider Hände, die für das Gerät sichtbar sind, verfolgt wird. HoloLens erkennt Hände, wenn sie sich entweder im Bereitschaftszustand (Handrücken mit nach oben gerichtetem Zeigefinger zu Ihnen gewandt) oder im gedrückten Zustand (Handrücken mit nach unten gerichtetem Zeigefinger zu Ihnen gewandt) befinden. Wenn sich die Hände in anderen Posen befinden, werden Sie von hololens ignoriert.
Für jede Hand, die hololens erkennt, können Sie ohne Ausrichtung und gedrücktem Zustand auf seine Position zugreifen. Wenn sich die Hand dem Rand des Gestenrahmens nähert, erhalten Sie auch einen Richtungsvektor, den Sie dem Benutzer zeigen können, damit er weiß, wie er seine Hand bewegen muss, um sie dorthin zurückzubringen, wo sie von HoloLens erkannt werden kann.

## <a name="gesture-frame"></a>Gestenrahmen
Für Gesten in hololens muss sich die Hand innerhalb eines Gesten Rahmens befinden, der sich in einem Bereich befindet, der von der Bewegung zur Gesten Messung von der Nase bis zur Taille und von der Schulter aus angezeigt werden kann. Benutzer müssen in diesem Bereich geschult werden, um den Erfolg der Aktion und ihren eigenen Komfort zu erzielen. Viele Benutzer werden anfänglich davon ausgehen, dass sich der Gesten Rahmen in der Ansicht über hololens befinden muss Wenn Sie das hololens-Clicker verwenden, ist es nicht erforderlich, dass sich die Hände innerhalb des Gesten Rahmens befinden.

Im Fall von fortlaufenden Gesten besteht das Risiko, dass Benutzer ihre Hände außerhalb des Gesten Rahmens bewegen, während Sie sich in der Mitte der Bewegung befinden, wenn Sie z. b. ein Holographic-Objekt verschieben und das gewünschte Ergebnis verlieren.

Sie sollten die folgenden drei Aspekte berücksichtigen:

- Benutzer Bildung für das vorhanden sein und die ungefähren Grenzen des Gesten Rahmens. Dies wird während der hololens-Einrichtung vermittelt.

- Benachrichtigen von Benutzern, wenn ihre Gesten die Gesten Rahmen Begrenzungen innerhalb einer Anwendung nähern oder unterbrechen, bis zu dem Ausmaß, in dem eine verlorene Bewegung zu unerwünschten Ergebnissen führt. Research hat die Hauptqualitäten eines solchen Benachrichtigungs Systems aufgezeigt. Die hololens-Shell stellt ein gutes Beispiel für diese Art von Benachrichtigung dar: Visual, auf dem zentralen Cursor, der die Richtung angibt, in der der Begrenzungs Übergang stattfindet.

- Die Folgen des Überschreitens der Begrenzungen des Gestenrahmens sollten minimiert werden. Im Allgemeinen bedeutet dies, dass das Ergebnis einer Geste an der Grenze angehalten und nicht umgekehrt werden soll. Wenn ein Benutzer beispielsweise ein Holographic-Objekt über einen Raum verschiebt, sollte die Bewegung angehalten werden, wenn der Gesten Rahmen verletzt wird und nicht an den Ausgangspunkt zurückgegeben wird. Der Benutzer kann einige Frustrationen erkennen, aber die Grenzen vielleicht besser verstehen und nicht jedes Mal die vollständigen beabsichtigten Aktionen neu starten.



## <a name="see-also"></a>Siehe auch
* [Augenbasierte Interaktion](eye-gaze-interaction.md)
* [Blickverfolgung auf HoloLens 2](eye-tracking.md)
* [Anvisieren und Verweilen](gaze-and-dwell.md)
* [Hände – Direkte Manipulation](direct-manipulation.md)
* [Hände – Gesten](gaze-and-commit.md#composite-gestures)
* [Hände – Zeigen und Ausführen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Spracheingabe](voice-input.md)

