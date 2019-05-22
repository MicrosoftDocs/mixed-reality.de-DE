---
title: Head-Blicke und commit
description: Übersicht über das Eingabemodell Head-Blicke und commit
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
ms.localizationpriority: high
keywords: Gemischte Realität Blicke, Blicke Ziel ist, handelt es sich bei der Interaktion, Entwerfen
ms.openlocfilehash: a84465de3479bf3da2131b94dd522539cd7de6e9
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974878"
---
# <a name="head-gaze-and-commit"></a>Head-Blicke und commit
Head-Blicke und Commit ist ein Eingabemodell aus, die umfasst das Anpassen eines Objekts mit der Richtung der Kopf vorwärts verweist (Head-Richtung), und klicken Sie dann mit einer sekundären Datenbank darauf reagieren, geben Sie z. B. als die Luft, tippen Sie auf Hand-Geste oder den Befehl "Select". Es gilt eine "weit" Eingabemodell mit indirekte Manipulation, was bedeutet, dass es am besten verwendet wird, für die Interaktion mit Inhalt, der über Gelenkarme zu erreichen ist.

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
        <td>Head-Blicke und commit</td>
        <td>✔️ Empfohlen</td>
        <td>✔️ Empfohlen (dritte Option - <a href="interaction-fundamentals.md">finden Sie unter den anderen Optionen</a>)</td>
        <td>Alternative Option ➕</td>
    </tr>
</table>

## <a name="head-gaze"></a>Head-Blicke
Mixed Reality-Headsets werden die Position und Ausrichtung des Benutzers Head verwenden, um ihre Head Richtungsvektor zu bestimmen. Sie können dies als eine Laser vorstellen, die direkt direkt von direkt zwischen dem Benutzer die Augen verweist. Dies ist eine ziemlich grobe Schätzung der, in denen der Benutzer sieht. Ihre Anwendung kann Schnittmenge dieser Chow mit virtuell oder Real-World-Objekten, und zeichnen einen Cursor an diesem Speicherort, damit der Benutzer wissen, was sie aktuell Anzielen.

Zusätzlich zum Head Blicke enthalten einige mixed Reality-Headsets wie beispielsweise HoloLens 2 Eye-tracking-Systeme, die einen Vektor Eye-Blicke zu erzeugen. Dies bietet eine differenzierte Maß, in denen der Benutzer sieht. Es ist möglich, die Blicke erstellen, und committen Interaktionen mit Eye Blicke, aber dies ist mit einem ganz anderen Satz von Einschränkungen beim Entwurf, der separat in behandelt werden die [Eye-tracking Artikel](eye-tracking.md).

## <a name="commit"></a>Commit
Nach der ein Objekt oder Element der Benutzeroberfläche, abzielen, kann der Benutzer interagieren oder "click", mit einer sekundären Eingabe. Dies wird als Schritt Commit des Modells bezeichnet. Die folgenden Commit-Methoden werden unterstützt:

- Tippbewegung
- Sprechen Sie mindestens eine der Voice-Befehl "Select" die gezielte Sprachbefehle
- Drücken Sie die einzelne Schaltfläche auf einem [HoloLens Clicker](hardware-accessories.md#hololens-clicker)
- Drücken Sie die Schaltfläche "A" auf eine Xbox Gamepad
- Drücken Sie die Schaltfläche "A" auf eine Adaptive Xbox-Controller

### <a name="head-gaze-and-air-tap-gesture"></a>Head-Blicke und Air tippen
Tippbewegung ist eine Geste für ein Tippen mit der Hand aufrechte gespeichert. Um tippbewegung ausführen zu können, Ihren Finger Index, an der Position bereit, und klicken Sie dann mit dem Daumen zusammendrücken ausgelöst und der Zeigefinger sichern freigeben. HoloLens-1 ist die Tippen Sie auf die am häufigsten verwendeten sekundären Eingabe.

![Schätzungen der Position des bereit, und klicken Sie dann eine Bewegung tippen oder klicken Sie auf](images/readyandpress.jpg)<br>

Tippbewegung steht auch auf HoloLens 2, und es wurde aus der ursprünglichen Version erhöht wurde. Nahezu alle Arten von Pinches werden jetzt unterstützt, solange das Handsymbol weiterhin aufrecht und gehalten wird. Dies erleichtert es für Benutzer, um zu erfahren, und führen Sie die Bewegung.  Diese neue tippbewegung ersetzt das alte Konto über die gleiche API, und vorhandene Anwendungen das neue Verhalten automatisch nach dem erneuten Kompilieren für HoloLens 2.

### <a name="head-gaze-and-select-voice-command"></a>Head-Blicke und "Select" voice-Befehl
Voice-Befehle ist eine der Methoden primären Interaktion in Mixed Reality. Es bietet eine sehr leistungsfähige "Hands Free" Methode bereit, um zu steuern, das System. Es gibt andere Arten von Voice-interaktionsmodellen:

- Der generische Befehl "Select" ermöglicht eine Betätigung der "Klick" oder einer sekundären Eingabe Commit ausführen.
- Objektbefehle wie z. B. "Schließen" oder "es größer Mach" zuzulassen, und übergeben an eine Aktion als einer sekundären Eingabe.
- Globale Befehle wie "Gehe zu", die ein Ziel nicht benötigen.
- Benutzeroberflächen für die Konversation oder Entitäten wie Cortana, die eine Funktion AI natürlicher Sprache enthalten.
- Benutzerdefinierte Befehle

Um weitere Details und eine Comprenhesive-Liste der verfügbaren Befehle und Verwendung finden, sehen Sie sich unsere [Voice Befehle](voice-design.md) Anleitungen.


### <a name="head-gaze-and-hololens-clicker"></a>Head-Blicke und HoloLens Clicker
Die HoloLens Clicker ist der erste Peripheriegerät wurde speziell für HoloLens und mit der HoloLens 1 Development Edition enthalten ist. Die HoloLens Clicker ermöglicht einen Benutzer mit minimalen Hand Bewegung klicken, und committen als sekundären Eingabe. Die HoloLens Clicker stellt eine Verbindung her, die HoloLens-1 oder 2 mit Bluetooth Low Energy (BTLE).

![](images/hololens-clicker-500px.jpg)<br>
HoloLens Clicker

Weitere Informationen und Anweisungen, um das Gerät koppeln finden [hier](hardware-accessories.md#pairing-bluetooth-accessories)




### <a name="head-gaze-and-xbox-wireless-controller"></a>Head-Blicke und Xbox-Wireless-Controller
Die drahtlose Xbox-Controller ermöglicht eine Betätigung der "klicken Sie auf" als Eingabe mithilfe der Schaltfläche ein sekundäres Replikat ausführen. Das Gerät ist eine Reihe von Aktionen, mit deren Hilfe navigieren und gegebenenfalls das System zugeordnet. Wenn Sie den Controller anpassen möchten, verwenden Sie die Xbox Accesories-App, um dem Xbox-Wireless-Controller zu konfigurieren.

![](images/xboxcontroller.jpg)<br>
Xbox-Wireless-Controller

[Kopplung mit Ihrem PC einen Xbox-controller](hardware-accessories.md#pairing-bluetooth-accessories)


### <a name="head-gaze-and-xbox-adaptive-controller"></a>Adaptive Head-Blicke und Xbox-Controller
Soll in erster Linie den Bedürfnissen der Spieler mit eingeschränkter Beweglichkeit, ist die Adaptive Xbox-Controller ein zentraler Hub für Geräte, der dabei hilft, Mixed Reality zugänglicher zu machen.

Der Adaptive Xbox-Controller ermöglicht eine Betätigung der "klicken Sie auf" als Eingabe mithilfe der Schaltfläche ein sekundäres Replikat ausführen. Das Gerät ist eine Reihe von Aktionen, mit deren Hilfe navigieren und gegebenenfalls das System zugeordnet. Wenn Sie den Controller anpassen möchten, verwenden Sie die Xbox Accesories-App, um Ihre adaptiven Xbox-Controller zu konfigurieren.

![](images/xbox-adaptive-controller-devices.jpg)<br>
Adaptive Xbox-Controller

Verbinden Sie externe Geräte wie z. B. Switches, Schaltflächen, Bereitstellungen und Joysticks, um eine benutzerdefinierte Controller-Benutzeroberfläche zu erstellen, die eindeutig verwalten können. Schaltfläche "," Ministick "und" Trigger-Eingaben werden mit Hilfstechnologiegeräte über 3,5 mm Jacks und USB-Ports verbunden gesteuert.

![](images/xbox-adaptive-controller-ports.jpg)<br>
Adaptive Xbox-Controller-ports

[Anweisungen, um das Gerät koppeln](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/en-US/xbox-one/accessories/controllers/xbox-adaptive-controller>Weitere Informationen, die auf der Xbox-Website verfügbar</a>


# <a name="head-gaze-design-guidelines"></a>Richtlinien für den Head-Blicke-Entwurf
> [!NOTE]
> Weitere Anleitungen, die speziell für den Entwurf bestaunen [bald](index.md).

## <a name="head-gaze-targeting"></a>Head-Blicke-Ziel
Alle Interaktionen werden erstellt, auf die Fähigkeit eines Benutzers, das Element als Ziel, die, das Sie mit, unabhängig von der Eingabe Modalität interagieren möchten. In Windows Mixed Reality, erfolgt dies in der Regel mithilfe des Benutzers Blicke.
Damit Benutzer erfolgreich eine Möglichkeit zum arbeiten können, muss des Systems berechnete Verständnis der Absicht des Benutzers und die Absicht des Benutzers tatsächliche, so weit wie möglich ausgerichtet sind. Um den Grad an, dass das System den beabsichtigten Benutzeraktionen interpretiert verbessert ordnungsgemäß Kundenzufriedenheit erhöht und die Leistung.


## <a name="target-sizing-and-feedback"></a>Ziel-größenanpassung und feedback
Der Blicke Vektor hat wiederholt angezeigt wurden, für die Ziel-problemlos verwendet werden kann, aber häufig am besten für gross für die Zielgruppenadressierung (erwerben von etwas größer Ziele). Mindestversion der Zielplattform Größen von 1 bis 1.5 Grad sollte erfolgreich Benutzeraktionen in den meisten Szenarien ermöglichen, wenn Ziele von 3 Grad häufig schneller zu ermöglichen. Beachten Sie, dass die Größe, der Benutzerziele ist eine 2D-Bereich auch für 3D-Elemente – welche Projektion sie-Sie sollte Bereich als Ziel gesetzt sein. Bietet einige wichtige Hinweis, dass ein Element "aktiv" ist, (, dass der Benutzer es abzielt) äußerst hilfreich ist – dazu zählen Behandlungen, damit wie sichtbar "darauf zeigen" Effekte "," audio-Highlights "oder" klickt, oder deaktivieren Sie die Ausrichtung eines Cursors mit einem Element.

![Optimale Zielgröße im Abstand von 2 Verbrauchseinheit](images/gazetargeting-size-1000px.jpg)<br>
*Optimale Zielgröße im Abstand von 2 Verbrauchseinheit*

![Ein Beispiel für ein Zielobjekt Blicke hervorheben](images/gazetargeting-highlighting-640px.jpg)<br>
*Ein Beispiel für ein Zielobjekt Blicke hervorheben*

## <a name="target-placement"></a>Ziel-Platzierung
Benutzer können häufig nicht finden im jeweiligen Lesebereich, Benutzeroberflächenelemente, die sehr hoch oder sehr niedrige positioniert sind die meisten ihre Aufmerksamkeit auf Bereiche, um ihren Mittelpunkt (in der Regel ungefähr Eye-Ebene) konzentrieren. Die meisten Ziele in eine angemessene-Band-Bereich von Eye-Ebene platzieren können. Erhält die Tendenz eines für Benutzer kann für den Blick auf einer relativ kleinen visuellen Elements jederzeit (der attentional Lichtkegel des Vision ist ungefähr 10 Grad), der gruppieren Elemente der Benutzeroberfläche, die den Grad an, dass sie konzeptionell verwandt sind Aufmerksamkeit mit vorwärtsverkettung Verhaltensweisen nutzen Element zu Element als ein Benutzer durchläuft einen Bereich ihre Blicke. Beim Entwerfen der Benutzeroberfläche sollten Sie Bedenken der großen möglichen Variante im Lesebereich zwischen HoloLens und immersive Headsets.

![Ein Beispiel für gruppierte Elemente der Benutzeroberfläche für einfacher Blicke Zielgruppenadressierung in Galaxy-Explorer](images/gazetargeting-grouping-1000px.jpg)<br>
*Ein Beispiel für gruppierte Elemente der Benutzeroberfläche für einfacher Blicke Zielgruppenadressierung in Galaxy-Explorer*

## <a name="improving-targeting-behaviors"></a>Verbessern die Zielgruppenadressierung anhand bestimmter Verhaltensweisen
Wenn Benutzerabsicht etwas Ziel kann werden festgelegt (oder eng angeglichen), kann es sehr hilfreich sein, zu akzeptieren, dass "Near Miss" bei der Interaktion versucht, als ob sie ordnungsgemäß zugewiesen wurden. Es gibt eine Reihe von erfolgreichen Methoden, die in mixed Reality-Benutzeroberfläche integriert werden können:

### <a name="head-gaze-stabilization-gravity-wells"></a>Head-Blicke Stabilisierung ("Schwerkraft Wells")
Dies sollte die meisten oder alle der Zeit aktiviert werden. Dieses Verfahren wird die natürliche Haupt-/trichterhalses JIT-Compiler, die Benutzer möglicherweise entfernt. Auch Verschiebung aufgrund von Verhaltensweisen suchen/sprechen.

### <a name="closest-link-algorithms"></a>Am nächsten Link-Algorithmen
Diese funktionieren am besten in Bereichen mit geringer Dichte interaktive Inhalte. Liegt eine hohe Wahrscheinlichkeit, dass auf Sie bestimmen können, was ein Benutzer versucht hat, für die Interaktion mit, können Sie die Zielgruppenadressierung anhand bestimmter Möglichkeiten ergänzen, indem Sie einfach vorausgesetzt gewisse Absicht.

### <a name="backdatingpostdating-actions"></a>Backdating/postdating Aktionen
Dieser Mechanismus eignet sich Aufgaben aus, die Geschwindigkeit zur Verfügung. Wenn ein Benutzer über eine Reihe von Ziel/Aktivierung Schachzüge Geschwindigkeit verschoben wird, kann es hilfreich sein, einige Absicht angenommen und fehlenden Schritte aus, um auf Zielgruppen fungieren, mit denen der Benutzer den Fokus etwas hat vor oder nach der das Tap (50 ms war vor/hinter effektiv etwas zulassen Testen früh) ein.

### <a name="smoothing"></a>Glättung
Dieser Mechanismus eignet sich für Pfade Bewegungen, reduzieren die leichte Jitter/bringen aufgrund von natürlichen Bewegungen Merkmale. Wenn Sie über die Pfade Bewegungen, die von der Größe/Entfernung von Bewegungen statt im Laufe der Zeit smooth-Glättung

### <a name="magnetism"></a>Magnetismus
Dieser Mechanismus kann als eine allgemeine Version des "Nächsten link" Algorithmen, zeichnen einen Cursor auf ein Ziel oder Vergrößerung Hitboxes (ob sichtbar oder nicht) betrachtet werden, wie Benutzer wahrscheinlich Ziele Ansatz, verwenden einige Kenntnisse über das interaktive Layout Benutzerabsicht für eine bessere Ansatz. Dies kann besonders für kleine Ziele effektiv sein.

### <a name="focus-stickiness"></a>Fokus-Bindung
Wenn Sie die in der Nähe interaktive Elemente Fokus erhalten bestimmen, geben Sie eine Verschiebung auf das Element, das gerade fokussiert ist. Dadurch können die fehlerhaften Verhalten wechseln, in eine Mitte zwischen zwei Elemente mit dem natürlichen Geräusch unverankerten Fokus zu reduzieren.


## <a name="composite-gestures"></a>Zusammengesetzte Gesten
Apps können mehr als nur einzelne Taps erkennen. Durch Kombinieren von Tap zu speichern und Freigeben mit dem Wechsel der Hand, komplexere zusammengesetzte Gesten ausgeführt werden können. Erstellen Sie für diese Gesten zusammengesetzten oder auf hoher Ebene für die Low-Level räumlichen Eingabedaten (von tippbewegung und Bloom), die Entwicklern den Zugriff auf.

### <a name="air-tap"></a>Tippen Sie auf
Die tippbewegung (ebenso wie die anderen Bewegungen, die unten) reagiert nur auf ein bestimmtes tippen. Zum Erkennen von anderen Taps, z. B. Menüs oder verstehen, muss Ihre app direkt die Low-Level-Interaktionen, die in zwei wichtige Komponente Gesten-Abschnitt oben beschrieben verwenden.

### <a name="tap-and-hold"></a>Tippen und halten Sie
Die Position nach unten weisenden Finger die tippbewegung verwaltet halten einfach. Die Kombination von Air Tap- und Hold ermöglicht eine Vielzahl von komplexeren "klicken und ziehen Sie" Interaktionen in Kombination mit Arm-Bewegung, z. B. ein Objekt und nicht deren Aktivierung übernommen oder "Mousedown" sekundäre Interaktionen wie z. B. ein Kontextmenü angezeigt.
Vorsicht sollte verwendet werden, wenn für diese stiftbewegung jedoch als Benutzer entwerfen anfällig für lockern ihre Hand Postures im Verlauf erweiterten Bewegung werden kann.

### <a name="manipulation"></a>Datenbearbeitung
Manipulation Gesten können verwendet werden, zu verschieben, ändern Sie die Größe oder ggf. ein Hologramm zu rotieren, wenn die Hologramm, 1:1 für Bewegungen, die der Benutzer manuell zu reagieren soll. Diese 1:1-Bewegungen können verwendet werden, damit der Benutzer, die gezeichnet werden soll, oder in der ganzen Welt zu zeichnen.
Die erste Zielgruppenadressierung für eine Bewegung der Manipulation sollten durch Blicke oder zeigt durchgeführt werden. Sobald die Tap- und Hold gestartet wird, Änderungen an das Objekt dann erfolgt manuell Bewegungen, Freigeben von dem Benutzer zu suchen, während sie ändern.

### <a name="navigation"></a>Navigation
Navigation Gesten funktioniert wie ein virtueller Joystick und können verwendet werden, um die UI-Widgets, wie z.B. radiale Menüs navigieren. Sie tippen und halten Sie, um die Bewegung gestartet, und verschieben Sie Ihre Hand innerhalb einer normalisierten 3D-Würfel zentraler Punkt drücken, auf der ersten. Sie können Ihre Hand entlang der X-, Y oder Z-Achse aus einem Wert von-1 in 1, wobei 0 für den Anfangspunkt, an die verschieben.
Navigation kann verwendet werden, um fortlaufenden Bildlauf Geschwindigkeit-basierte oder Zoomen Gesten, ähnlich wie eine 2D Benutzeroberfläche scrollen, indem Sie auf der mittleren Maustaste, und klicken Sie dann nach oben und unten bewegen der Maus zu erstellen.

Navigation mit Rails bezieht sich auf die Fähigkeit zum Erkennen von Bewegungen im bestimmte Achse bis auf dieser Achse bestimmten Schwellenwert erreicht ist. Dies ist nur nützlich, wenn das Verschieben von Daten in mehr als eine Achse in einer Anwendung vom Entwickler z. B. aktiviert ist, wenn eine Anwendung so konfiguriert, dass die um Navigation Gesten in X, Y-Achse zu erkennen ist, sondern auch angegeben X-Achse mit Schienen. In diesem Fall erkennt System manuell Bewegungen, für die X-Achse, solange diese innerhalb einer imaginären Rails (Handbuch) für X-Achse, bleiben, wenn Hand datenverschiebung tritt auch auf die y-Achse.

In Direct2D-apps können Benutzer vertikale Navigation Gesten scrollen, Zoomen, oder ziehen in der app verwenden. Dies fügt virtuellen Finger Workflows an die app zum Simulieren von Touchgesten des gleichen Typs. Benutzer können auswählen, welche der folgenden Aktionen durchgeführt werden, durch das Umschalten zwischen den Tools auf der Leiste über die app, entweder durch Auswählen der Schaltfläche oder sagen "< Scroll/Drag/vergrößern > Tool".

[Weitere Informationen zur zusammengesetzten Gesten](gestures.md#composite-gestures)

## <a name="gesture-recognizers"></a>Geste Erkennungen

Ein Vorteil der Verwendung von gestenerkennung ist, dass Sie eine stiftbewegungs-Erkennung nur für die Gesten konfigurieren können, die derzeit gezielte – Hologramm annehmen kann. Die Plattform erfolgt nur die zur mehrdeutigkeitsvermeidung erforderlich, um diese bestimmten unterstützten Gesten zu unterscheiden. Auf diese Weise kann ggf. ein Hologramm, die nur die tippbewegung unterstützt unbestimmte Zeit zwischen drücken Sie akzeptieren, und ggf. ein Hologramm, unterstützt sowohl tippen und halten Sie können höher stufen, das Tap, stehen nach der Hold-Suchdauer-Schwellenwert.

## <a name="hand-recognition"></a>Hand-Erkennung
HoloLens erkennt die gestensteuerung durch Überwachung der Position einer oder beide Hände, die auf dem Gerät angezeigt werden. HoloLens werden praktische angezeigt, wenn sie sich im Zustand "bereit" (Rückseite der Hand, die Sie mit Zeigefinger nach, oben) oder (Rückseite der Hand, die Sie mit dem Finger Index nach unten gerichteten) gedrückt werden. Wenn andere stellt praktische nutzen, wird die HoloLens werden ignoriert.
Jeder Runde erkennt, HoloLens, Sie seine Position (ohne Ausrichtung) und ihren aktuellen Status zugreifen können. Das Handsymbol den Rand des Rahmens Geste nähert, sind Sie auch bei einem Richtungsvektor bereitgestellt das Sie für den Benutzer anzeigen können, damit sie wissen, verschieben Sie ihre Hand, um es wieder zu erhalten, sodass HoloLens sie sehen können.

## <a name="gesture-frame"></a>Geste frame
Bei Gesten für HoloLens muss das Handsymbol innerhalb eines"Aktion", in einem Bereich, der die Bewegung Erkennung Kameras entsprechend (sehr grob von Nase Taille und zwischen den Schultern) angezeigt. Benutzer müssen auf diesen Bereich der Erkennung sowohl für die erfolgreiche Durchführung der Aktion als auch für ihre eigenen Komfort (viele Benutzer werden anfänglich wird davon ausgegangen, dass die Bewegung Frame muss in ihrer Ansicht über HoloLens und zu Verzögerungen bei ihren Arms uncomfortably um interagieren) trainiert werden. Wenn Sie die HoloLens Clicker verwenden zu können, müssen Sie sich nicht innerhalb des Rahmens Geste werden.

Im Fall von kontinuierlichen Gesten insbesondere besteht das Risiko von Benutzern, die sich außerhalb der Bewegung Frame in der Mitte Geste (während ein holographic-Objekt, z. B. verschieben) verschieben und dem gewünschten Ergebnis verlieren.

Es gibt drei Dinge, die Sie berücksichtigen sollten:

- Schulung der Benutzer auf die Bewegung des Frames Vorhandensein und die ungefähre Grenzen (Dies wird während des Setups von HoloLens unterrichtet).

- Benachrichtigen Benutzer aus, wenn ihre Bewegungen demnächst/der Bewegung Frame Grenzen innerhalb einer Anwendung, die den Grad an wichtige sind, die eine Geste für eine verlorene zu unerwünschten Ergebnissen führen. Research hat gezeigt, die wichtigsten Qualitäten eines solchen Notification Systems, und die HoloLens-Shell bietet ein gutes Beispiel für diese Art von Benachrichtigung (Visualisierung, auf den zentralen-Cursor, der angibt, der Richtung, in welcher, die begrenzungsgruppe überschreiten stattfindet).

- Auswirkungen die Bewegung Frame Grenzen zu beschädigen sollte minimiert werden. Im Allgemeinen bedeutet dies, dass das Ergebnis einer Geste an der Grenze beendet, aber nicht rückgängig gemacht werden soll. Z. B., wenn ein Benutzer ein holographic Objekt in einem Raum verschoben wird, sollten Bewegung beendet, wenn der Bewegung Frame überschritten wird, aber nicht wieder in den Ausgangspunkt. Der Benutzer kann auftreten, klicken Sie dann einige Frustration jedoch möglicherweise schneller verstehen Sie die Grenzen und nicht die vollständige beabsichtigten Aktionen jedes Mal neu gestartet haben.


## <a name="see-also"></a>Siehe auch
* [Direkte Manipulation mit den Händen](direct-manipulation.md)
* [Zeigen und Ausführen mit den Händen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Anvisieren mit dem Kopf und Verweilen](gaze-and-dwell.md)
* [Sprachbefehle](voice-design.md)





