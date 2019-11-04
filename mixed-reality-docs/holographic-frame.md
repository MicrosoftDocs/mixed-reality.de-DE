---
title: Holographic-Frame
description: Benutzer sehen die Welt der gemischten Realität über den Holographic-Frame.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Hololens, Windows Mixed Reality, Holographic Frame, Field of View
ms.openlocfilehash: 2145ba3b13bbd903299ad342292dfa8f5c05c023
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434633"
---
# <a name="holographic-frame"></a>Holographic-Frame

Benutzer sehen die Welt der Mixed Reality durch ein rechteckiges Ansichtsfenster, das von ihren Headsets betrieben wird. Bei HoloLens wird dieser rechteckige Bereich als holografischer Rahmen bezeichnet und ermöglicht den Benutzern, die digitalen Inhalte zu sehen, die der realen Welt ihrer Umgebung überlagert sind. Das Entwerfen von Benutzeroberflächen, die für den Holographic Frame optimiert sind, schafft Chancen, verringert die Herausforderungen und verbessert die Benutzerfreundlichkeit gemischter Reality-Anwendungen.

## <a name="designing-for-content"></a>Entwerfen von Inhalten

Häufig ist es für Entwickler von Bedeutung, den Umfang ihrer Benutzeroberfläche auf die Benutzer zu beschränken, die sofort angezeigt werden können, und die tatsächliche Skalierung zu beeinträchtigen, um sicherzustellen, dass der Benutzer ein Objekt vollständig sieht. Ähnlich können Designer mit komplexen Anwendungen den Holographic-Frame häufig mit Inhalten überladen und Benutzer mit schwierigen Interaktionen und überlasteten Schnittstellen überfordern. Designer, die gemischte Realitäts Inhalte erstellen, müssen ihre Obergrenzen nicht direkt vor dem Benutzer und innerhalb ihrer unmittelbaren Ansicht einschränken. Wenn die physische Welt um den Benutzer zugeordnet ist, sollten alle diese Oberflächen als potenzieller Canvas für digitalen Inhalt und Interaktionen angesehen werden. Der richtige Entwurf von Interaktionen und Inhalten innerhalb einer Benutzerumgebung sollte den Benutzer dazu ermutigen, seinen Platz zu bewegen, seine Aufmerksamkeit auf wichtige Inhalte zu lenken und das volle Potenzial gemischter Realität zu sehen.

Das vielleicht wichtigste Verfahren zum fördern der Bewegung und Untersuchung in einer App besteht darin, dass **Benutzer die Benutzeroberflächen anpassen können**. Legen Sie den Benutzern einen kurzen Zeitraum von "Task-Free"-Zeit mit dem Gerät zu. Dies kann ganz einfach sein, wenn Sie ein Objekt in den Bereich versetzen und es den Benutzern ermöglichen, Sie zu verschieben oder eine Einführung in die Benutzerumgebung zu geben. Diese Zeit sollte für alle wichtigen Aufgaben oder bestimmte Gesten (z. b. das Tippen auf das Tippen) freigegeben werden. Dies ist der Zweck, den Benutzern das Anzeigen von Inhalten über das Gerät zu ermöglichen, bevor Interaktivität erforderlich ist oder die Phasen der APP fortgeführt werden. Wenn dies das erste Mal eines Benutzers mit dem Gerät ist, ist dies besonders wichtig, da Sie sich mit dem Anzeigen von Inhalten über den Holographic-Frame und der Art von holograms vertraut machen.

### <a name="large-objects"></a>Große Objekte

Häufig ist der Inhalt, den eine Umgebung aufruft, insbesondere der reale Inhalt, größer als der Holographic-Frame. Objekte, die in der Regel nicht in den Holographic-Frame passen, sollten beim ersten hinzufügen verkleinert werden (entweder in einer kleineren Skala oder in einer Entfernung). Der Schlüssel besteht darin, **Benutzern die vollständige Größe des Objekts anzuzeigen** , bevor die Skala den Frame übersteigt. Beispielsweise sollte ein Holographic Elephant angezeigt werden, der vollständig innerhalb des Frames passt, sodass Benutzer ein räumliches Verständnis der Gesamtform des Tieres bilden können, bevor Sie es in der Nähe des Benutzers mit der [realen Skalierung dimensionieren](scale.md) .

Bei der vollständigen Größe des Objekts haben Benutzer dann die Erwartung, wohin Sie wechseln und nach bestimmten Teilen dieses Objekts suchen. Ebenso kann es bei der Verwendung von immersiven Inhalten hilfreich sein, sich auf die vollständige Größe des Inhalts zu beziehen. Wenn die Umgebung beispielsweise ein Modell eines virtuellen Hauses durchläuft, kann es hilfreich sein, eine kleinere Größe der PUP-Haus Größe zu haben, mit der Benutzer herausfinden können, wo Sie sich innerhalb des Hauses befinden.

Ein Beispiel für das Entwerfen von großen Objekten finden Sie unter [Volvo Cars](holographic-frame.md#volvo-cars).

### <a name="many-objects"></a>Viele Objekte

Bei einer Vielzahl von Objekten oder Komponenten sollte der gesamte Speicherplatz für den Benutzer verwendet werden, um zu vermeiden, dass der Holographic Frame direkt vor dem Benutzer gruppiert wird. Im Allgemeinen empfiehlt es sich, Inhalte langsam in eine Oberfläche einzufügen. Dies gilt insbesondere für Benutzeroberflächen, die dem Benutzer viele Objekte zur Verfügung stellen. Ähnlich wie bei großen Objekten besteht der Schlüssel darin, **den Benutzern das Layout von Inhalten** in der Umgebung zu verdeutlichen, damit Sie ein räumliches Verständnis der Inhalte erhalten können, die der Umgebung hinzugefügt werden.

Eine solche Vorgehensweise ist das Bereitstellen von persistenten Punkten (auch als "Marken" bezeichnet) in der Umgebung, die Inhalte in der realen Welt verankern. Ein Meilenstein könnte z. b. ein physisches Objekt in der realen Welt sein, z. b. eine Tabelle, in der digitaler Inhalt angezeigt wird, oder ein digitales Objekt, z. b. eine Gruppe digitaler Bildschirme, in denen häufig Inhalt angezeigt wird. Objekte können auch in der Peripherie des Holographic Frame platziert werden, um den Benutzer dazu zu ermutigen, den Schlüssel Inhalt zu überprüfen, während die Ermittlung von Inhalten, die jenseits der Peripherie liegen, von den [Aufmerksamkeit Direktoren](holographic-frame.md#attention-directors)unterstützt werden kann.

Das Platzieren von Objekten in der Peripherie kann Benutzer dazu ermutigen, die Seite zu unterstützen, und dies kann von den folgenden Informationen unterstützt werden, wie unten beschrieben.

<br>

---

## <a name="user-comfort"></a>Benutzerkomfort

Für gemischte Realität bei großen Objekten oder vielen Objekten ist es wichtig zu verstehen, wie viel Kopf-und Hals Bewegung erforderlich ist, um mit dem Inhalt zu interagieren. Umgebungen können in drei Kategorien unterteilt werden: **Horizontal** (nebeneinander), **vertikal** (nach oben und nach unten) oder **immersiv** (horizontal und vertikal). Beschränken Sie, wenn möglich, die Mehrzahl der Interaktionen auf horizontale oder vertikale Kategorien, idealerweise, wenn die meisten Erfahrungen in der Mitte des Holographic Frame stattfinden, während sich der Benutzer in einer neutralen Position befindet. Vermeiden Sie Interaktionen, die bewirken, dass der Benutzer seine Ansicht ständig an unnatürliche Kopf Positionen verschiebt (z. b. immer nach dem Zugriff auf eine Kontextmenü Interaktion).

![optimale Region für Inhalte liegt zwischen 0 und 35 Grad unter dem Horizont](images/optimal-field-of-view-2.png)<br>
*Der optimale Bereich für den Inhalt liegt zwischen 0 und 35 Grad unter dem Horizont.*

Die horizontale Kopfbewegung ist [für häufige Interaktionen bequemer,](comfort.md) während vertikale Bewegungen für ungewöhnliche Ereignisse reserviert werden sollten. Beispielsweise sollte eine Obergrenze, die eine lange horizontale Zeitachse beinhaltet, die vertikale Kopfbewegung für Interaktionen einschränken (z. b. das Aussehen eines Menüs).

Erwägen Sie, die voll Text Bewegung anstelle der Kopfbewegung zu fördern, indem Sie Objekte auf den Platz des Benutzers platzieren. Bei der Verwendung von verschiebenden Objekten oder großen Objekten sollten Sie besonders auf die Kopfbewegung achten, insbesondere dann, wenn Sie sowohl die horizontale als auch die vertikale Achse häufig verschieben müssen.

<br>

---

## <a name="interaction-considerations"></a>Überlegungen zur Interaktion

Wie bei den Inhalten müssen Interaktionen in einer gemischten Realität nicht darauf beschränkt werden, was der Benutzer sofort sehen kann. Interaktionen können überall im realen Raum um den Benutzer stattfinden, und diese Interaktionen können den Benutzern helfen, sich um die Benutzerfreundlichkeit zu bewegen und ihre Erfahrungen zu untersuchen.

### <a name="attention-directors"></a>Attention-Direktoren

Das Angeben von interessanten Punkten oder wichtigen Interaktionen kann für den Fortschritt der Benutzer durch eine benutzerfreundliche Lösung entscheidend sein. Benutzer Aufmerksamkeit und Bewegung des Holographic-Frames können auf feine oder sehr hohe Weise gesteuert werden. Denken Sie daran, die Aufmerksamkeit von Regisseuren mit Zeiten der kostenlosen Untersuchung in gemischter Realität (vor allem zu Beginn eines Erlebnisses) auszugleichen, um die Überlastung des Benutzers zu vermeiden. Im Allgemeinen gibt es zwei Arten von Aufmerksamkeits Leitern:
* **Visuelle Direktoren:** Die einfachste Möglichkeit, den Benutzern mitzuteilen, dass Sie in einer bestimmten Richtung verschoben werden sollten, ist die Bereitstellung eines visuellen Hinweises. Dies kann durch einen visuellen Effekt erfolgen (z. b. einen Pfad, den der Benutzer zum nächsten Teil der Benutzer Darstellung visuell verfolgen kann) oder sogar als einfache direktionale Pfeile. Beachten Sie, dass ein beliebiger visueller Indikator innerhalb der Umgebung des Benutzers und nicht als "angefügt" an den Holographic-Frame oder den Cursor verankert sein sollte.
* **Audiodirektoren:** [räumlicher Sound](spatial-sound-design.md) kann eine leistungsstarke Möglichkeit zum Einrichten von Objekten in einer Szene bieten (Warnung an Benutzer von Objekten, die eine benutzerfreundliche Darstellung durchführen), oder um die Aufmerksamkeit auf einen bestimmten Punkt im Raum zu lenken (um die Ansicht des Benutzers in die Schlüssel Objekte zu verschieben). Die Verwendung von audioleitern, um die Aufmerksamkeit des Benutzers zu unterstützen, kann besser und weniger aufdringlich als Visual Directors sein. In einigen Fällen kann es am besten sein, mit einem audiodirector zu beginnen und dann zu einem visuellen Director zu wechseln, wenn der Benutzer den Hinweis nicht erkennt. Audiodirektoren können auch mit visuellen Regisseuren kombiniert werden, um zusätzliche Akzente zu erhalten.

### <a name="commanding-navigation-and-menus"></a>Befehls Navigation, Navigation und Menüs

Schnittstellen in gemischter Realität werden idealerweise eng mit dem digitalen Inhalt gekoppelt, den Sie steuern. Daher sind frei schwebende 2D-Menüs oft nicht ideal für die Interaktion und können für Benutzer im Holographic-Frame schwierig sein. Für Umgebungen, in denen Schnittstellen Elemente wie Menüs oder Textfelder erforderlich sind, sollten Sie die Verwendung einer [tagbasierten Methode](billboarding-and-tag-along.md) in Erwägung ziehen, um den Holographic Frame nach einer kurzen Verzögerung zu befolgen. Vermeiden Sie das Sperren von Inhalten für den Frame, wie z. b. ein Heads-Up-Display, da dies für den Benutzer Disorienting sein kann und das Eintauchen für andere digitale Objekte in der Szene unterbricht.

Sie können auch Schnittstellen Elemente direkt auf den spezifischen Inhalt platzieren, den Sie steuern, sodass Interaktionen auf natürliche Weise um den physischen Bereich des Benutzers erfolgen können. Beispielsweise können Sie ein komplexes Menü in separate Teile aufteilen. Mit jeder Schaltfläche oder Gruppe von Steuerelementen, die an das jeweilige Objekt angefügt sind, wirkt sich die Interaktion Um dieses Konzept weiter zu vertiefen, sollten Sie die Verwendung von [Objekten mit Interaktionen](interactable-object.md)in Erwägung ziehen.

### <a name="gaze-and-gaze-targeting"></a>Ausrichtung und Ausrichtung des Blicks

Der Holographic-Frame stellt ein Tool für den Entwickler dar, das sowohl Interaktionen auslöst als auch auswerten soll, wo die Aufmerksamkeit eines Benutzers liegt. Der [Blick](gaze-and-commit.md) ist eine der [wichtigsten Interaktionen bei hololens](interaction-fundamentals.md), bei denen der Blick mit [Gesten](gaze-and-commit.md#composite-gestures) (z. b. mit dem Luftbild) oder der [Stimme](voice-input.md) gekoppelt werden kann (wodurch sich kürzere, natürlichere sprachbasierte Interaktionen ermöglichen). Dadurch wird der Holographic-Frame zu einem Raum zum beobachten digitaler Inhalte und zur Interaktion mit dem Frame. Wenn die Oberfläche für die Interaktion mit mehreren Objekten um den Platz des Benutzers aufruft (z. b. durch Mehrfachauswahl von Objekten um den Platz des Benutzers mit Blick und Gesten), sollten Sie diese Objekte in die Ansicht des Benutzers einbinden oder die erforderliche kopfmenge einschränken. Bewegung zur herauf Stufung des [Benutzer Komforts](comfort.md).

Der Blick kann auch verwendet werden, um die Benutzer Aufmerksamkeit durch eine Benutzer Aufmerksamkeit zu verfolgen und zu sehen, auf welche Objekte oder Teile der Szene der Benutzer am meisten geachtet hat. Dies kann besonders für das Debuggen einer benutzerfreundlichen Anwendung verwendet werden, sodass analytische Tools wie Heatmaps feststellen können, wo Benutzer die meiste Zeit ausgeben oder bestimmte Objekte oder Interaktionen fehlen. Die Blick Verfolgung kann auch ein leistungsfähiges Tool für die Benutzerfreundlichkeit bereitstellen (siehe das Beispiel für die [Küche von Lowe](holographic-frame.md#lowes-kitchen) ).

<br>

---

## <a name="performance"></a>Leistung

Die korrekte Verwendung des Holographic Frame ist für die [Leistungsqualität](understanding-performance-for-mixed-reality.md) von grundlegender Bedeutung. Eine gängige technische (und Nutz barkeits-) Herausforderung besteht darin, den Frame des Benutzers mit digitalen Inhalten zu überlasten, wodurch die Renderingleistung beeinträchtigt wird. Verwenden Sie stattdessen den vollständigen Speicherplatz um den Benutzer, um mithilfe der oben beschriebenen Verfahren digitale Inhalte anzuordnen, um die Last des Renderings zu verringern und eine optimale Anzeigequalität zu gewährleisten.

Digitale Inhalte innerhalb des Holographic-Rahmens der hololens können auch mit der [Stabilisierungs Ebene](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md) kombiniert werden, um eine optimale Leistung und [hologrammstabilität](hologram-stability.md)zu erzielen.

<br>

---

## <a name="examples"></a>Beispiele

### <a name="volvo-cars"></a>Volvo Cars

<iframe width="940" height="530" src="https://www.youtube.com/embed/DilzwF90vec" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Im Showroom-Prozess von Volvo Cars werden Kunden eingeladen, sich über die Funktionen eines neuen Fahrzeugs in einer hololens-Benutzer Funktionalität zu informieren, die durch einen Volvo-Partner verknüpft ist. Bei der Verwendung des Holographic Frame war eine Herausforderung bei Volvo: ein Auto, das groß ist, ist zu groß für den Benutzer. Die Lösung bestand darin, die Oberfläche mit einem physischen, einer zentralen Tabelle im Showroom zu beginnen, wobei ein kleineres digitales Modell des Autos auf der Tabelle platziert wurde. Dadurch wird sichergestellt, dass der Benutzer bei der Einführung den vollständigen Wagen sehen kann, und es wird ein räumliches Verständnis ermöglicht, sobald das Auto auf seine reale Skalierung später in der Praxis wächst.

Bei der Verwendung von Volvo werden auch visuelle Direktoren genutzt, sodass Sie einen langen visuellen Effekt aus dem kleinen Fahrzeugmodell in der Tabelle bis hin zu einer Wand im Raum zeigen. Dies führt zu einem "Magic Window"-Effekt, der die vollständige Ansicht des Fahrzeugs in der Entfernung anzeigt und die weiteren Features des Fahrzeugs in der realen Skalierung veranschaulicht. Die Head-Bewegung ist horizontal, ohne dass eine direkte Interaktion mit dem Benutzer stattfinden kann (Stattdessen werden die Hinweise visuell und aus der Benutzer Darstellung von Volvo verknüpft).

<br>

---

### <a name="lowes-kitchen"></a>Die Küche von Lowe

Eine Geschäftserfahrung von Lowe lädt Kunden zu einem umfassenden Modell einer Küche und zeigt verschiedene Möglichkeiten der Umgestaltung, wie Sie in den hololens angezeigt werden. Die Küche im Geschäft bietet einen physischen Hintergrund für digitale Objekte, eine leere Canvas von Geräten, Gegenstände und Schränke, damit sich die gemischte Realität entfaltet.

Physische Oberflächen fungieren als statische Oberflächen für den Benutzer, um sich selbst in der Benutzeroberfläche zu positionieren, da die Zuordnung eines Lowe den Benutzer durch andere Produktoptionen führt und fertig ist. Auf diese Weise kann die Zuordnung die Aufmerksamkeit des Benutzers auf den "Kühlschrank" oder "Mittelpunkt" der Küchen Weise weiterleiten, um digitale Inhalte zu präsentieren.

![die Zuordnung eines Lowe verwendet ein Tablet, um Kunden durch die hololens-Benutzeroberflächen zu leiten.](images/loweskitchen-750px.jpg)<br>
*Die Zuordnung eines Lowe verwendet ein Tablet, um Kunden durch das hololens zu leiten.*

Die Benutzeroberflächen werden teilweise von einem Tablet-Verhalten verwaltet, das von der Lowe-Zuordnung gesteuert wird. Ein Teil der Rolle "zuordnen" wäre in diesem Fall auch die Begrenzung einer übermäßigen Kopfbewegung, bei der die Aufmerksamkeit nahtlos über die interessanten Punkte in der Küche geleitet wird. Die Tablet-Darstellung bietet auch die Zuordnung von Lowe zu Blick Daten in Form einer Wärmebild Ansicht der Küche, um zu verstehen, wo sich der Benutzer befindet (z. b. in einem bestimmten Bereich von Cabinetry), um diese mit Anleitungen zur erneuten Modellierung genauer bereitzustellen.

Einen tieferen Einblick in die Küche von Lowe finden Sie in der [Microsoft-Keynote bei Ignite 2016](https://www.youtube.com/watch?v=gC_4JxF0e_k).

<br>

---

### <a name="fragments"></a>Fragmente

In den hololens-Spiel Fragmenten wird Ihr Leben in eine virtuelle Kriminalitäts Szene transformiert und zeigt Hinweise und Beweise sowie einen virtuellen Besprechungsraum an, in dem Sie mit Zeichen kommunizieren, die auf Ihren Lehrstühlen sitzen und sich auf Ihre Wände stützen.

![Fragmente wurden auf der Startseite eines Benutzers durchgeführt, wobei Zeichen mit realen Objekten und Oberflächen interagieren.](images/fragments-750px.jpg)<br>
*Fragmente wurden so konzipiert, dass Sie in der Startseite eines Benutzers stattfinden, wobei Zeichen mit realen Objekten und Oberflächen interagieren.*

Wenn Benutzer anfänglich mit der Benutzerumgebung beginnen, erhalten Sie eine kurze Anpassungsphase, bei der nur sehr wenig Interaktion erforderlich ist, um Sie zu untersuchen. Dadurch wird auch sichergestellt, dass der Raum für den interaktiven Inhalt des Spiels ordnungsgemäß zugeordnet wird.

Während der gesamten Oberflächen werden Zeichen zu Schwerpunkt Punkten und fungieren als visuelle Direktoren (Head-Bewegungen zwischen Zeichen, das Aussehen oder Gesten in den Interessenbereichen). Das Spiel basiert auch auf spezifischere visuelle Hinweise, wenn ein Benutzer zu lange braucht, um ein Objekt oder Ereignis zu finden, und das räumliche Audiomaterial stark nutzt (insbesondere mit Zeichen stimmen, wenn eine Szene eingegeben wird).

<br>

---

### <a name="destination-mars"></a>Ziel: Mars

Im Ziel: Mars-Oberfläche, die im [Kennedy Space Center der NASA](https://blogs.windows.com/devices/2016/09/19/hololens-experience-destination-mars-now-open-at-kennedy-space-center-visitor-complex/)vorgestellt wurde, waren Besucher in einem immersiven Weg zur Mars-Oberfläche eingeladen, der durch die virtuelle Darstellung des legendären Astronauten Buzz Aldrin geführt wurde.

![ein Virtual Buzz Aldrin als Mittelpunkt für Benutzer im Ziel: Mars.](images/destinationmars-750px.png)<br>
*Ein Virtual Buzz Aldrin wird zum Mittelpunkt für Benutzer im Ziel: Mars.*

Als immersives Verfahren wurde empfohlen, die Benutzer zu untersuchen und ihren Kopf in alle Richtungen zu bewegen, um das virtuelle Martian-Querformat anzuzeigen. Um den Komfort der Benutzer zu gewährleisten, bot die Erzählung und die virtuelle Präsenz von Buzz Aldrin während der gesamten Benutzerfreundlichkeit einen Schwerpunkt. Diese virtuelle Aufzeichnung von Buzz (die von [den Mixed Reality-Erfassungs-Studios von Microsoft](https://www.microsoft.com/mixed-reality/capture-studios)erstellt wurde) lag in der Ecke des Raums in der realen, menschlichen Größe, sodass Benutzer Sie in nahezu kompletter Ansicht sehen konnten. Die Benutzer von "Buzz" haben Benutzer zur Fokussierung auf verschiedene Punkte in der Umgebung (z. b. eine Gruppe von Martian-Steinen im Boden oder einen Berg Bereich in der Entfernung) mit bestimmten Szenen Änderungen oder von ihm eingeführten Objekten geleitet.

![die virtuellen narratoren wiederum die Bewegung eines Benutzers befolgen, um einen leistungsstarken Schwerpunkt im gesamten Prozess zu schaffen.](images/gazereset-750px.png)<br>
*Die virtuellen narratoren werden dazu verwendet, um die Bewegung eines Benutzers zu verfolgen, sodass Sie während der gesamten Zeit einen leistungsfähigen Fokus schaffen können.*

Die realistische Darstellung von Buzz bot einen leistungsstarken Mittelpunkt, der mit einer kleinen Technik fertig ist, um dem Benutzer zu zeigen, wie er es gibt. Wenn sich der Benutzer über die Benutzeroberflächen bewegt, wechselt der Sprung zu einem Schwellenwert, bevor er in einen neutralen Zustand wechselt, wenn der Benutzer zu weit über seine Peripherie hinausgeht. Wenn der Benutzer das vollständige verschieben (z. b. an anderer Stelle in der Szene) und dann wieder zu Buzz durchführt, wird die direktionale Position der Sprachausgabe wieder auf den Benutzer ausgerichtet. Techniken wie diese bieten ein leistungsfähiges Gefühl für das Eintauchen und das Erstellen eines Mittelpunkts im Holographic-Frame, wodurch eine übermäßige Kopfbewegung und eine herauf Stufung des [Benutzer Komforts](comfort.md)vermieden werden.

## <a name="see-also"></a>Weitere Informationen:
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Komfort](comfort.md)
* [Skalieren](scale.md)
* [Anvisieren mit dem Kopf und Verweilen](gaze-and-dwell.md)
* [Hologrammstabilität](hologram-stability.md)
