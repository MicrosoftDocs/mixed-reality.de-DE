---
title: Gesten
description: Hand Gesten ermöglichen es Benutzern, Aktionen in gemischter Realität auszuführen.
author: rwinj
ms.author: cmeekhof
ms.date: 02/24/2019
ms.topic: article
keywords: Gemischte Realität, Gesten, Interaktion, Entwurf
ms.openlocfilehash: 70b03c6fa327bd987a681bba59abb725c3ddc6b4
ms.sourcegitcommit: e5b677f92ac4b1dff9aad6c329345a5aca4fcef5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69020215"
---
# <a name="gestures"></a>Gesten

Hand Gesten ermöglichen es Benutzern, Aktionen in gemischter Realität auszuführen. Die Interaktion basiert auf dem **Blick** auf das Ziel und die **Geste** oder **Stimme** , um auf das gewünschte Element zu reagieren. Hand Gesten bieten keine genaue Position im Raum, aber die Einfachheit der Verwendung von hololens und die sofortige Interaktion mit Inhalten ermöglicht es den Benutzern, ohne weitere Zubehör zu arbeiten.

<br>

>[!VIDEO https://www.youtube.com/embed/kwn9Lh0E_vU]

## <a name="device-support"></a>Unterstützung von Geräten

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Funktion</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Gesten</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Handgelenk</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> Weitere Anleitungen sind für hololens 2 in [Kürze](index.md#news-and-notes)verfügbar.

## <a name="gaze-and-commit"></a>Blick und Commit

Zum Ausführen von Aktionen verwenden Handgesten den [Kopf](gaze.md) zeilig als Ziel Mechanismus. Die Kombination aus **Blick** und die **lufttap** -Geste führt zu einer Interaktion mit **Blick und Commit** . Eine Alternative zu "Blick" und "Commit" ist **Punkt-und Commit**, die von [Motion-Controllern](motion-controllers.md)aktiviert wird. Apps, die auf hololens ausgeführt werden, müssen nur "Gaze-und Commit" unterstützen, da hololens keine Bewegungs Controller unterstützt. Apps, die auf hololens und immersiven Headsets ausgeführt werden, sollten sowohl auf Blick gesteuerte als auch auf Zeige gesteuerte Interaktionen unterstützen, um Benutzern die Möglichkeit zu geben, welches Eingabegerät Sie verwenden.

## <a name="the-two-core-gestures-of-hololens"></a>Die zwei wichtigsten Gesten von hololens

Hololens erkennt zurzeit zwei Kernkomponenten Gesten: **Air Tap** und **Bloom**. Diese zwei Kern Interaktionen sind die niedrigste Ebene räumlicher Eingabedaten, auf die ein Entwickler zugreifen kann. Sie bilden die Grundlage für eine Vielzahl möglicher Benutzeraktionen.

### <a name="air-tap"></a>In die Luft tippen

Air Tap ist eine getippt-Geste, bei der die Hand gedrückt gehalten wird, ähnlich wie bei einem Mausklick oder einer SELECT-Option. Dies wird in den meisten hololens-Umgebungen für das Äquivalent eines "Click"-Elements für ein UI-Element verwendet, nachdem es für den [Blick](gaze.md)angezeigt wurde. Es handelt sich um eine universelle Aktion, die Sie einmal erlernen und dann auf alle Ihre apps anwenden. Weitere Möglichkeiten zum Durchführen von SELECT sind das Drücken der einzelnen Schaltfläche auf einem [hololens-Clicker](hardware-accessories.md#hololens-clicker) oder der Sprachbefehl "Select".

![Status "bereit" für Handbewegungen in hololens](images/image9.png)<br>
*Der Status "bereit" für Luft Tippen auf hololens.*

Air Tap ist eine diskrete Geste. Eine Auswahl ist entweder abgeschlossen oder nicht, eine Aktion ist oder wird nicht innerhalb einer-Funktion durchgeführt. Es ist möglich, es sei denn, es wird empfohlen, ohne bestimmte Zwecke andere diskrete Gesten aus Kombinationen der Hauptkomponenten zu erstellen (z. b. eine zwei-tippen-Geste, um etwas anderes als eine einzelne Abzweigung zu bedeuten).

![Finger an der Bereitschafts Position und dann auf tippen oder klicken](images/readyandpress.jpg)<br>
*Vorgehensweise: Erhöhen Sie den Finger für den Index in die fertige Position, und drücken Sie den Finger nach unten, um zu tippen oder auszuwählen und anschließend wieder zu veröffentlichen.*

### <a name="bloom"></a>Blütezeit

"Bloom" ist die "Home"-Geste und ist allein dafür reserviert. Es handelt sich um eine spezielle System Aktion, die verwendet wird, um zum Startmenü zurückzukehren. Dies entspricht dem Drücken der Windows-Taste auf einer Tastatur oder der Xbox-Schaltfläche auf einem Xbox-Controller. Der Benutzer kann beide Hand verwenden.

![Aufblütebewegung bei hololens](images/image10-640px.png)

Wenn Sie die auftastenbewegung auf hololens durchführen möchten, halten Sie sich mit ihren Hand Blättern in der Hand. Öffnen Sie dann die Hand. Beachten Sie, dass Sie auch immer zu Beginn zurückkehren können, indem Sie "Hey Cortana, Go Home" sagen. Apps können nicht speziell auf eine Heim Aktion reagieren, da diese vom System behandelt werden.

![Aufblühenden Gesten](images/bloom-giphy.gif)<br>
*So führen Sie die aufblühenden Gesten auf hololens aus.*

## <a name="composite-gestures"></a>Zusammengesetzte Gesten

Apps können mehr als nur einzelne Tippbewegungen erkennen. Durch die Kombination von Tippen, Halten und Loslassen mit der Bewegung der Hand können komplexere zusammengesetzte Gesten ausgeführt werden. Diese zusammengesetzten Gesten oder Gesten auf hoher Ebene bauen auf den räumlichen Eingabedaten auf niedriger Ebene (von „In die Luft tippen“ und „Öffnen“) auf, auf die Entwickler zugreifen können.

<table>
<tr>
<th> Zusammengesetzte Geste</th><th> Vorgehensweise</th>
</tr><tr>
<td>In die Luft tippen</td><td>Die Geste „In die Luft tippen“ (wie auch die anderen nachfolgenden Gesten) reagiert nur auf eine bestimmte Tippbewegung. Um andere Tippbewegungen wie „Menü“ oder „Greifen“ zu erkennen, muss Ihre App direkt die Interaktionen auf niedrigerer Ebene verwenden, die oben im Abschnitt über zwei Schlüsselkomponentengesten beschrieben sind.</td>
</tr><tr>
<td>Tippen und halten Sie</td><td><p>„Halten“ bedeutet einfach, die Position mit dem Finger nach unten beim „In die Luft tippen“ beizubehalten. Die Kombination aus Luft tippen und halten ermöglicht eine Vielzahl &quot;komplexer Klick&quot; -und Zieh Interaktionen, wenn Sie mit Arm-Bewegung kombiniert werden, wie z. b. das Auswählen eines Objekts anstelle&quot; der Aktivierung oder &quot;MouseDown. sekundäre Interaktionen, z. b. ein Kontextmenü.</p><p>Bei der Gestaltung dieser Geste sollte jedoch mit Bedacht vorgegangen werden, da die Benutzer dazu neigen können, ihre Handhaltungen im Laufe einer längeren Geste zu entspannen.</p></td>
</tr><tr>
<td>Manipulation</td><td><p>Manipulations Gesten können zum Verschieben, Ändern der Größe oder Drehen eines holograms verwendet werden, wenn das – Hologramm 1:1 auf die Handbewegungen des&#39;Benutzers reagieren soll. Eine Verwendungsmöglichkeit für solche 1:1-Bewegungen ist es, den Benutzer in der Umgebung zeichnen oder malen zu lassen.</p><p>Die anfängliche Zielbestimmung für eine Manipulationsgeste sollte durch Anvisieren oder Zeigen erfolgen. Sobald das Tippen und Halten beginnt, erfolgt jede Manipulation des Objekts durch Handbewegungen, sodass sich der Benutzer während der Manipulation umsehen kann.</p></td>
</tr><tr>
<td>Navigation</td><td><p>Navigationsgesten funktionieren wie ein virtueller Joystick und können zur Navigation in Widgets der Benutzeroberfläche, z. B. Radialmenüs, verwendet werden. Sie tippen und halten, um die Geste zu starten, und bewegen dann Ihre Hand in einem normalisierten 3D-Würfel, der um die erste Betätigung herum angeordnet ist. Sie können Ihre Hand entlang der X-, Y- oder Z-Achse zwischen einem Wert von -1 bis 1 bewegen, wobei 0 der Ausgangspunkt ist.</p><p>Mithilfe der Navigation können geschwindigkeitsbasierte kontinuierliche Gesten zum Scrollen oder Zoomen erstellt werden, ähnlich dem Scrollen bei einer 2D-Benutzeroberfläche durch Klicken mit der mittleren Maustaste und anschließendes Bewegen der Maus nach oben und unten.</p><p>Die „Navigation mit Führungsschienen“ bezieht sich auf die Fähigkeit, Bewegungen entlang einer bestimmten Achse zu erkennen, bis ein bestimmter Schwellenwert auf dieser Achse erreicht ist. Dies ist nur sinnvoll, wenn die Bewegung innerhalb einer Anwendung durch den Entwickler entlang mehrerer Achsen ermöglicht wird, z. B. wenn eine Anwendung so konfiguriert ist, dass sie Navigationsgesten über die X-, Y-Achse erkennt, aber auch die X-Achse mit Führungsschienen angegeben ist. In diesem Fall erkennt das System Handbewegungen über die X-Achse, solange sie innerhalb einer imaginären Führungsschiene auf der X-Achse verbleiben, wenn die Handbewegung auch auf der Y-Achse erfolgt.</p><p>Innerhalb von 2D-Apps können Benutzer mit vertikalen Navigationsgesten innerhalb der App scrollen, zoomen oder ziehen. Dadurch werden virtuelle Fingerberührungen in der App eingeführt, um Gesten für die Toucheingabe desselben Typs zu simulieren. Benutzer können auswählen, welche dieser Aktionen durchgeführt werden, indem Sie zwischen den Tools auf der Leiste oberhalb der App wechseln, indem Sie entweder die Schaltfläche &#39; &lt;auswählen oder das Tool&#39;zum&gt; Scrollen/ziehen/Zoomen verwenden.</p></td>
</tr>
</table>



### <a name="gesture-recognizers"></a>Gestenerkennung

Ein Vorteil der Gestenerkennung besteht darin, dass Sie einen Gestenerkenner nur für die Gesten konfigurieren können, die das aktuell ausgewählte Hologramm akzeptieren kann. Die Plattform wird nur die zur Unterscheidung dieser besonders unterstützten Gesten erforderliche Mehrdeutigkeitsvermeidung vornehmen. Auf diese Weise kann ein Hologramm, das nur „In die Luft tippen“ unterstützt, jede beliebige Zeitspanne zwischen Drücken und Loslassen akzeptieren, während ein Hologramm, das sowohl Tippen als auch Halten unterstützt, die Tippbewegung nach dem Überschreiten des Schwellenwerts für die Haltezeit in einen Haltevorgang ändern kann.

## <a name="hand-recognition"></a>Handerkennung

HoloLens erkennt Handgesten, indem die Position einer oder beider Hände, die für das Gerät sichtbar sind, verfolgt wird. Hololens sieht Hände, wenn Sie sich im **Zustand "bereit** " befinden (zurück der Hand mit dem Index fingerbild) oder in den **gedrückten Zustand** (zurück der Hand mit dem indexfingerbild). Wenn die Hände eine andere Pose einnehmen, werden sie von HoloLens ignoriert.

Sie können für jede Hand, die von HoloLens erkannt wird, auf ihre Position (ohne Ausrichtung) und ihren gedrückten Zustand zugreifen. Wenn sich die Hand dem Rand des Gestenrahmens nähert, erhalten Sie auch einen Richtungsvektor, den Sie dem Benutzer zeigen können, damit er weiß, wie er seine Hand bewegen muss, um sie dorthin zurückzubringen, wo sie von HoloLens erkannt werden kann.

## <a name="gesture-frame"></a>Gestenrahmen

Bei Gesten für HoloLens muss sich die Hand innerhalb eines „Gestenrahmens“ befinden, in einem Bereich, den die Gestenerkennungskameras entsprechend sehen können (ganz grob genommen von der Nase bis zur Taille und zwischen den Schultern). Die Benutzer müssen in diesem Erkennungsbereich sowohl für den Aktionserfolg als auch für die eigene Bequemlichkeit geschult werden (viele Benutzer werden zunächst davon ausgehen, dass sich der Gestenrahmen innerhalb Ihres Sichtfelds der HoloLens befinden muss und daher ihre Arme zum Interagieren auf unbequeme Weise hochhalten). Bei der Verwendung des HoloLens-Klick-Geräts müssen sich Ihre Hände nicht innerhalb des Gestenrahmens befinden.

Insbesondere bei fortlaufenden Gesten besteht die Gefahr, dass Benutzer ihre Hände im Verlauf der Geste außerhalb des Gestenrahmens bewegen (z. B. beim Bewegen eines holografischen Objekts) und nicht das gewünschte Ergebnis erzielen.

Sie sollten die folgenden drei Aspekte berücksichtigen:
* Schulung der Benutzer zur Existenz des Gestenrahmens und zu ungefähren Begrenzungen (dies wird beim HoloLens-Setup vermittelt).
* Benachrichtigung der Benutzer, wenn sich ihre Gesten den Gestenrahmenbegrenzungen innerhalb einer Anwendung nähern bzw. diese überschreiten, da eine verlorene Geste zu unerwünschten Ergebnissen führt. Studien haben die wichtigsten Eigenschaften eines solchen Benachrichtigungssystems gezeigt, und die HoloLens-Shell ist ein gutes Beispiel für diese Art der Benachrichtigung (visuelle Benachrichtigung auf dem zentralen Cursor, der die Richtung angibt, in der die Überschreitung der Begrenzung erfolgt ist).
* Die Folgen des Überschreitens der Begrenzungen des Gestenrahmens sollten minimiert werden. Im Allgemeinen bedeutet dies, dass das Ergebnis einer Geste an der Begrenzung gestoppt, aber nicht rückgängig gemacht werden sollte. Wenn ein Benutzer beispielsweise ein Holographic-Objekt über einen Raum verschiebt, sollte die Bewegung angehalten werden, wenn der Gesten Rahmen verletzt wird, aber **nicht** an den Ausgangspunkt zurückgegeben wird. Der Benutzer empfindet dann möglicherweise eine gewisse Frustration, kann aber die Begrenzungen schneller verstehen und muss nicht jedes Mal seine beabsichtigten Aktionen vollständig neu starten.

## <a name="see-also"></a>Siehe auch
* [Anvisieren mit dem Kopf und Verweilen](gaze-and-dwell.md)
* [Sprachentwurf](voice-design.md)
* [MR-Eingabe 211: Geste](holograms-211.md)
* [Gesten und Motion-Controller in Unity](gestures-and-motion-controllers-in-unity.md)
* [Hände und Motion-Controller in DirectX](hands-and-motion-controllers-in-directx.md)
* [Motion-Controller](motion-controllers.md)
