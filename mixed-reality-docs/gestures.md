---
title: Gesten
description: Gestensteuerung können Benutzer eine Aktion in mixed Reality.
author: rwinj
ms.author: cmeekhof
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed Reality, Bewegungen Interaktion, Entwurf
ms.openlocfilehash: 52ba7070e2c9b5632d5978c70571fcf9cda3f499
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974888"
---
# <a name="gestures"></a>Gesten

Gestensteuerung ermöglicht es Benutzern, ergreifen Sie entsprechende Maßnahmen in mixed Reality. Interaktion basiert auf **bestaunen** Ziel und **Geste** oder **Voice** zu reagieren, beliebige Element bestimmt ist. Gestensteuerung bieten sich nicht auf eine ganz bestimmte Position im Raum, die Einfachheit der Platzieren auf einem HoloLens und sofort die Interaktion mit Inhalt erlaubt jedoch Benutzern zu erhalten, ohne alle anderen Zubehör zu arbeiten.

<br>

>[!VIDEO https://www.youtube.com/embed/kwn9Lh0E_vU]

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Feature</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1. Generation)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> Gesten</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
<tr>
<td> Umrissene Händen</td><td></td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

> [!NOTE]
> Weitere Anleitungen, die speziell für HoloLens 2 [bald](index.md#news-and-notes).

## <a name="gaze-and-commit"></a>Blicke-und-commit

Aktionen, übergeben die Verwendung von Gesten [Head Blicke](gaze.md) als Mechanismus für die Zielgruppenadressierung. Die Kombination von **bestaunen** und **tippbewegung** Geste führt zu einer **Blicke-und-Commit** Interaktion. Eine Alternative zur Blicke-und-Commit ist **Punkt-und-Commit**, aktiviert, indem [motion Controller](motion-controllers.md). Apps für HoloLens müssen nur Blicke-und-Commit zu unterstützen, da die HoloLens Motion-Controller nicht unterstützt. Apps, die sowohl für HoloLens immersive Headsets ausgeführt sollte, unterstützen sowohl Blicke gesteuert, und zeigen gesteuerte Interaktionen, um die Benutzerauswahl in welche Eingabegerät zu gewähren, die sie verwenden.

## <a name="the-two-core-gestures-of-hololens"></a>Die beiden core Bewegungen von HoloLens

HoloLens derzeit erkennt zwei komponentenbewegungen - Kern- **tippbewegung** und **Bloom**. Bei diesen zwei Kernen Interaktionen handelt es sich um die unterste Ebene der räumlichen Daten, die ein Entwickler zugreifen können. Sie bilden die Grundlage für eine Vielzahl von möglichen Benutzeraktionen.

### <a name="air-tap"></a>Tippen Sie auf

Tippen Sie auf eine Geste für ein Tippen mit der Mobile aufrecht, ähnlich wie ein Mausklick ist, oder wählen. Hiermit wird in den meisten HoloLens-Benutzeroberfläche für die Darstellung einer "Klick" auf ein Element der Benutzeroberfläche nach dem Ziel mit [bestaunen](gaze.md). Es ist eine universelle Aktion, die Sie einmal erfahren Sie, und klicken Sie dann für alle Ihre apps anwenden. Weitere Informationen zum Ausführen von Select sind durch Drücken der Klick auf eine [HoloLens Clicker](hardware-accessories.md#hololens-clicker) oder per Spracheingabe Stimme stellen, Befehl "Select".

![Status "bereit" für die gestensteuerung für HoloLens](images/image9.png)<br>
*Status "bereit" für die tippbewegung auf HoloLens.*

Tippbewegung ist eine diskrete Geste. Eine Auswahl entweder abgeschlossen ist oder nicht, eine Aktion ist oder nicht innerhalb einer Umgebung ausgeführt wird. Es ist möglich, obwohl dies nicht ohne eine bestimmten Zweck, empfohlen, zum Erstellen von anderen diskreten Bewegungen aus Kombinationen der Hauptkomponenten (z. B. eine Geste Doppeltippen Sie auf so etwas anderes als ein einfaches Tippen).

![Schätzungen der Position des bereit, und klicken Sie dann eine Bewegung tippen oder klicken Sie auf](images/readyandpress.jpg)<br>
*Gewusst wie tippbewegung ausführen: Lösen Sie Ihren Finger Index, an die Position bereit, drücken Sie Ihren Finger auf tippen, oder wählen Sie aus, und Sichern Sie freigeben.*

### <a name="bloom"></a>Blühen

Bloom ist die Aktion "home" und ist für reserviert, allein. Es ist eine spezielle Systemaktion, die verwendet wird, um zurück zum Startmenü zu wechseln. Dies entspricht dem Drücken der Windows-Taste auf einer Tastatur oder der Xbox-Schaltfläche, auf eine Xbox-Controller. Der Benutzer kann entweder manuell verwenden.

![Bloom Geste, HoloLens](images/image10-640px.png)

Klicken Sie hierzu die Geste Bloom, HoloLens, halten Sie Ihre Hand, palm mit Hand zusammen. Öffnen Sie dann Ihre Hand ein. Beachten Sie, können Sie auch immer Start Zurückgeben von "Hey Cortana, Go Home" angezeigt. Apps können nicht speziell für eine Aktion home reagieren, wie diese vom System verarbeitet werden.

![Bloom Bewegung](images/bloom-giphy.gif)<br>
*So führen Sie die Bewegung Bloom für HoloLens aus.*

## <a name="composite-gestures"></a>Zusammengesetzte Gesten

Apps können mehr als nur einzelne Taps erkennen. Durch Kombinieren von Tap zu speichern und Freigeben mit dem Wechsel der Hand, komplexere zusammengesetzte Gesten ausgeführt werden können. Erstellen Sie für diese Gesten zusammengesetzten oder auf hoher Ebene für die Low-Level räumlichen Eingabedaten (von tippbewegung und Bloom), die Entwicklern den Zugriff auf.

<table>
<tr>
<th> Zusammengesetzte Bewegung</th><th> Gewusst wie: anwenden</th>
</tr><tr>
<td>Tippen Sie auf</td><td>Die tippbewegung (ebenso wie die anderen Bewegungen, die unten) reagiert nur auf ein bestimmtes tippen. Zum Erkennen von anderen Taps, z. B. Menüs oder verstehen, muss Ihre app direkt die Low-Level-Interaktionen, die in zwei wichtige Komponente Gesten-Abschnitt oben beschrieben verwenden.</td>
</tr><tr>
<td>Tippen und halten Sie</td><td><p>Die Position nach unten weisenden Finger die tippbewegung verwaltet halten einfach. Die Kombination von Air tippen und halten kann, für eine Vielzahl von komplexeren &quot;klicken und ziehen Sie&quot; Interaktionen in Kombination mit arm-Bewegung, z. B. ein Objekt und nicht deren Aktivierung übernommen oder &quot;Mousedown&quot; Sekundäre Interaktionen wie z. B. ein Kontextmenü angezeigt.</p><p>Vorsicht sollte verwendet werden, wenn für diese stiftbewegung jedoch als Benutzer entwerfen anfällig für lockern ihre Hand Postures im Verlauf erweiterten Bewegung werden kann.</p></td>
</tr><tr>
<td>Datenbearbeitung</td><td><p>Manipulation Gesten können verwendet werden, zu verschieben, ändern Sie die Größe oder ggf. ein Hologramm zu rotieren, wenn die Hologramm, 1:1 für den Benutzer reagieren soll&#39;s Hand Verschiebungen. Diese 1:1-Bewegungen können verwendet werden, damit der Benutzer, die gezeichnet werden soll, oder in der ganzen Welt zu zeichnen.</p><p>Die erste Zielgruppenadressierung für eine Bewegung der Manipulation sollten durch Blicke oder zeigt durchgeführt werden. Sobald die Tap- und Hold gestartet wird, Änderungen an das Objekt dann erfolgt manuell Bewegungen, Freigeben von dem Benutzer zu suchen, während sie ändern.</p></td>
</tr><tr>
<td>Navigation</td><td><p>Navigation Gesten funktioniert wie ein virtueller Joystick und können verwendet werden, um die UI-Widgets, wie z.B. radiale Menüs navigieren. Sie tippen und halten Sie, um die Bewegung gestartet, und verschieben Sie Ihre Hand innerhalb einer normalisierten 3D-Würfel zentraler Punkt drücken, auf der ersten. Sie können Ihre Hand entlang der X-, Y oder Z-Achse aus einem Wert von-1 in 1, wobei 0 für den Anfangspunkt, an die verschieben.</p><p>Navigation kann verwendet werden, um fortlaufenden Bildlauf Geschwindigkeit-basierte oder Zoomen Gesten, ähnlich wie eine 2D Benutzeroberfläche scrollen, indem Sie auf der mittleren Maustaste, und klicken Sie dann nach oben und unten bewegen der Maus zu erstellen.</p><p>Navigation mit Rails bezieht sich auf die Fähigkeit zum Erkennen von Bewegungen im bestimmte Achse bis auf dieser Achse bestimmten Schwellenwert erreicht ist. Dies ist nur nützlich, wenn das Verschieben von Daten in mehr als eine Achse in einer Anwendung vom Entwickler z. B. aktiviert ist, wenn eine Anwendung so konfiguriert, dass die um Navigation Gesten in X, Y-Achse zu erkennen ist, sondern auch angegeben X-Achse mit Schienen. In diesem Fall erkennt System manuell Bewegungen, für die X-Achse, solange diese innerhalb einer imaginären Rails (Handbuch) für X-Achse, bleiben, wenn Hand datenverschiebung tritt auch auf die y-Achse.</p><p>In Direct2D-apps können Benutzer vertikale Navigation Gesten scrollen, Zoomen, oder ziehen in der app verwenden. Dies fügt virtuellen Finger Workflows an die app zum Simulieren von Touchgesten des gleichen Typs. Benutzer können auswählen, welche der folgenden Aktionen durchgeführt werden, durch das Umschalten zwischen den Tools auf der Leiste über die app, entweder durch Auswählen der Schaltfläche oder sagen &#39; &lt;Scroll/Drag/vergrößern&gt; Tool&#39;.</p></td>
</tr>
</table>



### <a name="gesture-recognizers"></a>Geste Erkennungen

Ein Vorteil der Verwendung von gestenerkennung ist, dass Sie eine stiftbewegungs-Erkennung nur für die Gesten konfigurieren können, die derzeit gezielte – Hologramm annehmen kann. Die Plattform erfolgt nur die zur mehrdeutigkeitsvermeidung erforderlich, um diese bestimmten unterstützten Gesten zu unterscheiden. Auf diese Weise kann ggf. ein Hologramm, die nur die tippbewegung unterstützt unbestimmte Zeit zwischen drücken Sie akzeptieren, und ggf. ein Hologramm, unterstützt sowohl tippen und halten Sie können höher stufen, das Tap, stehen nach der Hold-Suchdauer-Schwellenwert.

## <a name="hand-recognition"></a>Hand-Erkennung

HoloLens erkennt die gestensteuerung durch Überwachung der Position einer oder beide Hände, die auf dem Gerät angezeigt werden. HoloLens Hände erkennt, entweder werden der **Status bereit** (Rückseite der Hand, die Sie mit Zeigefinger nach, oben) oder die **gedrückt-Status** (Rückseite der Hand, die Sie mit dem Finger Index nach unten gerichteten). Wenn andere stellt praktische nutzen, wird die HoloLens werden ignoriert.

Jeder Runde erkennt, HoloLens, Sie seine Position (ohne Ausrichtung) und ihren aktuellen Status zugreifen können. Das Handsymbol den Rand des Rahmens Geste nähert, sind Sie auch bei einem Richtungsvektor bereitgestellt das Sie für den Benutzer anzeigen können, damit sie wissen, verschieben Sie ihre Hand, um es wieder zu erhalten, sodass HoloLens sie sehen können.

## <a name="gesture-frame"></a>Geste frame

Bei Gesten für HoloLens muss das Handsymbol innerhalb eines"Aktion", in einem Bereich, der die Bewegung Erkennung Kameras entsprechend (sehr grob von Nase Taille und zwischen den Schultern) angezeigt. Benutzer müssen auf diesen Bereich der Erkennung sowohl für die erfolgreiche Durchführung der Aktion als auch für ihre eigenen Komfort (viele Benutzer werden anfänglich wird davon ausgegangen, dass die Bewegung Frame muss in ihrer Ansicht über HoloLens und zu Verzögerungen bei ihren Arms uncomfortably um interagieren) trainiert werden. Wenn Sie die HoloLens Clicker verwenden zu können, müssen Sie sich nicht innerhalb des Rahmens Geste werden.

Im Fall von kontinuierlichen Gesten insbesondere besteht das Risiko von Benutzern, die sich außerhalb der Bewegung Frame in der Mitte Geste (während ein holographic-Objekt, z. B. verschieben) verschieben und dem gewünschten Ergebnis verlieren.

Es gibt drei Dinge, die Sie berücksichtigen sollten:
* Schulung der Benutzer auf die Bewegung des Frames Vorhandensein und die ungefähre Grenzen (Dies wird während des Setups von HoloLens unterrichtet).
* Benachrichtigen Benutzer aus, wenn ihre Bewegungen demnächst/der Bewegung Frame Grenzen innerhalb einer Anwendung, die den Grad an wichtige sind, die eine Geste für eine verlorene zu unerwünschten Ergebnissen führen. Research hat gezeigt, die wichtigsten Qualitäten eines solchen Notification Systems, und die HoloLens-Shell bietet ein gutes Beispiel für diese Art von Benachrichtigung (Visualisierung, auf den zentralen-Cursor, der angibt, der Richtung, in welcher, die begrenzungsgruppe überschreiten stattfindet).
* Auswirkungen die Bewegung Frame Grenzen zu beschädigen sollte minimiert werden. Im Allgemeinen bedeutet dies, dass das Ergebnis einer Geste an der Grenze beendet, aber nicht rückgängig gemacht werden soll. Beispielsweise wird ein Benutzer ein holographic Objekt in einem Raum verschoben, Bewegung beendet werden soll, wenn der Frame Geste überschritten wird, aber **nicht** zum Ausgangspunkt zurückgegeben werden. Der Benutzer kann auftreten, klicken Sie dann einige Frustration jedoch möglicherweise schneller verstehen Sie die Grenzen und nicht die vollständige beabsichtigten Aktionen jedes Mal neu gestartet haben.

## <a name="see-also"></a>Siehe auch
* [Anvisieren mit dem Kopf und Verweilen](gaze-and-dwell.md)
* [Sprachentwurf](voice-design.md)
* [MR-Eingabe 211: Geste](holograms-211.md)
* [Gesten und Motion-Controller in Unity](gestures-and-motion-controllers-in-unity.md)
* [Hände und Motion-Controller in DirectX](hands-and-motion-controllers-in-directx.md)
* [Motion-Controller](motion-controllers.md)
