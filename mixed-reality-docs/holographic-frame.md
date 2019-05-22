---
title: Holographic frame
description: Benutzer finden Sie in der ganzen Welt von mixed Reality durch den holographic Frame.
author: mavitazk
ms.author: mavitazk
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Windows Mixed Reality, holographic Frame Sichtfeld
ms.openlocfilehash: c505eadbc16bb59143313aa62dd7c9d95384e0c8
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974914"
---
# <a name="holographic-frame"></a>Holographic frame

Benutzer finden Sie unter der ganzen Welt von mixed Reality über einen rechteckigen, unterstützt durch ihre Kopfhörer Viewport aus. Klicken Sie auf die HoloLens dieses rechteckigen Bereichs holographic Frames wird aufgerufen, und ermöglicht das digitale Inhalte, die als Überlagerung auf der realen Welt zu finden Sie unter. Entwerfen von Benutzeroberflächen, die für den Frame holographic optimiert schafft die Möglichkeit, verringert die Herausforderungen und verbessert die benutzerfreundlichkeit von mixed Reality-Anwendungen.

## <a name="designing-for-content"></a>Entwerfen für Inhalt

Häufig Designer das Bedürfnis Begrenzung des Bereichs ihrer Erfahrung, was der Benutzer sofort sehen kann, Einbußen bei der realen Welt skalieren, um sicherzustellen, dass den Benutzer ein Objekt in seiner Gesamtheit angezeigt. Auf ähnliche Weise überladen Designer mit komplexen Anwendungen häufig den holographic Frame mit dem Inhalt, Benutzer mit nur schwer Interaktionen und überladen Schnittstellen zu überfordern. Designer mixed Reality-Inhalte erstellen, müssen nicht ihrer Zufriedenheit, direkt vor dem Benutzer und deren sofortige Ansicht beschränkt. Wenn die physische Welt um dem Benutzer zugeordnet ist, klicken Sie dann alle diese Oberflächen eine potenzielle Leinwand für digitale Inhalte und Interaktionen berücksichtigen. Richtig zu Entwerfen von Interaktionen und Inhalte in einer Umgebung sollte den Benutzer auf seinem Bereich, leiten ihre Aufmerksamkeit auf wichtige Inhalte aus, und helfen, das volle Potenzial von mixed Reality finden Sie unter bewegen empfehlen.

Vielleicht die wichtigste Methode ermutigend datenverschiebung und Auswertung in einer app besteht darin **können Benutzer auf die Benutzeroberfläche anpassen**. Ermöglichen Sie Benutzern einen kurzen Zeitraum "Aufgabe-free", mit dem Gerät. Dies kann so einfach wie das Platzieren eines Objekts im Raum und ermöglichen es den Benutzern, die sie bewegen oder Erzählung Sie eine Einführung in die Oberfläche zu sein. Dieses Mal sollte keine kritischen Aufgaben oder spezifische anwendungsstiftbewegungen (z. B. Air-tippen), stattdessen den Zweck, Benutzern, die entsprechend der Anzeige von Inhalten über das Gerät vor dem Erzwingen von Interaktivität, oder bis zu den Phasen der app zu ermöglichen. Ist dies eines Benutzers ersten Mal mit dem Gerät ist dies besonders wichtig, da sie über den holographic Rahmen und der Art der Hologramme vertraut festzustellen, ob Inhalt erhalten.

### <a name="large-objects"></a>Große Objekte

Häufig den Inhalt, die eine Benutzeroberfläche erfordert, insbesondere realen Inhalt werden größer als der holographic Rahmen. Objekte, die normalerweise nicht im Frame holographic passen sollte verkleinert werden, angepasst werden, wenn sie (mit geringerem Umfang oder in einem Abstand) zuerst eingeführt werden. Der Schlüssel liegt darin **können Benutzer, die die volle Größe des Objekts finden Sie unter** , bevor die Skalierung den Frame überfordert. Beispielsweise sollte eine holographic Elephant angezeigt werden, entsprechend vollständig innerhalb des Frames, die Benutzer können Sie einen räumlichen Überblick über allgemeine Form des Tieres, vor dem Ändern der Steuerelementgröße zu bilden [realen Skalierung](scale.md) in der Nähe des Benutzers.

Mit der vollständigen Größe des Objekts Denken Sie daran erwarten Benutzer klicken Sie dann, wo Sie bewegen, und suchen Sie nach bestimmten Teilen dieses Objekts. Auf ähnliche Weise in eine immersive Inhalt-Erfahrung ist es hilfreich, eine Möglichkeit, wieder auf die Gesamtgröße des Inhalts zu verweisen. Z. B. wenn die Benutzeroberfläche durchlaufen, um ein Modell eines Hauses virtuellen umfasst, kann es hilfreich sein, eine kleinere Version der Doll-House-Größe der Umgebung verfügen, die Benutzer ausgelöst werden können, um zu verstehen, wo sie sich im Haus sind.

Ein Beispiel des Entwurfs für große Objekte finden Sie unter [Volvo Autos](holographic-frame.md#volvo-cars).

### <a name="many-objects"></a>Viele Objekte

Erfahrungen mit vielen Objekten oder Komponenten sollten in Betracht ziehen, verwenden den vollständigen Raum des Benutzers vermeiden, dass des holographic Frames direkt vor dem Benutzer. Im Allgemeinen, es wird empfohlen, um Inhalt eine Erfahrung langsam einzuführen, und dies gilt insbesondere für Benutzeroberflächen, die viele Objekte für dem Benutzer bereitstellen möchten. Ähnlich wie mit großen Objekten wird der Schlüssel, um ist **können Benutzer das Layout des Inhalt nachvollziehen** in der Umgebung, sodass erhalten Sie einen räumlichen Überblick über die neuerungen darum, wie der Inhalt der Umgebung hinzugefügt wird.

Eine Technik, um dies zu erreichen ist zum Bereitstellen von permanenten Punkte (auch bekannt als Orientierungspunkte) in der Umgebung, Anchor-Inhalt in der realen Welt. Z. B. möglicherweise eine Sehenswürdigkeit ein physisches Objekt in der Praxis, z. B. eine Tabelle, in denen digitaler Inhalte angezeigt wird, oder eines digitalen Objekts, beispielsweise einen Satz von digitalen Bildschirmen, in denen Inhalt häufig angezeigt wird. Objekte können auch in der Peripherie des holographic Frames ermutigen Sie Benutzer, für Schlüssel, die Inhalt zu suchen, während die Ermittlung von Inhalten außerhalb der Peripherie durch unterstützt werden, kann eingefügt werden [Aufmerksamkeit Directors](holographic-frame.md#attention-directors).

Platzieren von Objekten in der Peripherie auffordern kann Benutzer auf der Seite suchen und diese kann werden Dank der Unterstützung durch Aufmerksamkeit Directors, wie unten beschrieben.

## <a name="user-comfort"></a>Benutzerkomfort

Für mixed Reality-Erfahrungen mit großen Objekten oder viele Objekte es ist entscheidend, wie viel Head berücksichtigen, und trichterhalses datenverschiebung ist erforderlich, um die Interaktion mit dem Inhalt. Umgebungen können in drei Kategorien in Bezug auf die Bewegungen unterteilt werden: **Horizontale** (nebeneinander), **vertikale** (nach oben und unten), oder **immersive** (horizontale und vertikale). Wenn möglich, werden beschränken Sie die meisten der Aktivitäten, die horizontal oder vertikal Kategorien an, idealerweise mit den meisten Umgebungen, die dort in der Mitte des Frames, holographic, während eine neutrale Position des Benutzers Head wird. Vermeiden Sie die Interaktionen, die dazu führen, den Benutzer dass, die Ansicht in einer unnatürlichen Head Positionen (z. B. immer nachschlagen, auf einer Aktivität, die Schlüssel im Menü) ständig zu verschieben.

![Optimale Region für den Inhalt ist 0 bis 35 Grad unten horizon](images/optimal-field-of-view-2-750px.png)<br>
*Optimale Region für den Inhalt ist 0 bis 35 Grad unten horizon*

Horizontale Bewegungen ist [vertraut](comfort.md) für häufige Interaktionen, während die vertikale Bewegungen für ungewöhnlich, dass Ereignisse reserviert werden soll. Beispielsweise sollten eine Erfahrung, die im Zusammenhang mit einer langen horizontalen Zeitachse vertikale Bewegungen für Interaktionen (z. B. die Suche nach unten bei einem Menü) beschränken.

Betrachten Sie ermutigen, Full-Text verschieben, anstatt nur Bewegungen, durch das Platzieren von Objekten um Speicherplatz für den Benutzer aus. Erfahrungen mit dem Verschieben von Objekten oder große Objekte achten, Bewegungen, insbesondere, in denen sie häufige Bewegung entlang der horizontalen und vertikalen Achsen benötigen.

## <a name="interaction-considerations"></a>Aspekte der Interaktion

Wie bei der Inhalte müssen Interaktionen in eine mixed Reality-Erfahrung nicht beschränkt, was der Benutzer sofort sehen kann. Interaktionen können stattfinden an einer beliebigen Stelle in der Praxis Raum des Benutzers ein, und diese Interaktionen ermutigen Sie Benutzer zu bewegen, und erkunden der Funktionen hilft.

### <a name="attention-directors"></a>Aufmerksamkeit directors

Der angibt, verweist der interessante oder wichtige Interaktionen können fortschreitender Benutzer über eine Benutzeroberfläche von entscheidender Bedeutung sein. Eingreifen des Benutzers und die Bewegung des Frames, holographic können auf Subtiler oder schwerfällige Weise weitergeleitet werden. Denken Sie daran, Aufmerksamkeit Directors mit Zeiträumen freie Durchsuchen von in mixed Reality (insbesondere zu Beginn einer Erfahrung) ausgeglichen werden, um zu vermeiden einer Überlastung des Benutzers. Im Allgemeinen stehen zwei Arten von Aufmerksamkeit Directors:
* **Visual Directors:** Die einfachste Möglichkeit, den Benutzer informieren, dass sie in einer bestimmten Richtung verschoben werden soll ist, einen visuellen Hinweis darauf. Dies ist möglich, mithilfe eines visuellen Effekts (z. B. ein Pfad, der der Benutzer kann auf den nächsten Teil der Benutzeroberfläche visuell folgen) oder sogar als einfache Richtungspfeile. Beachten Sie, dass alle visuellen Indikator sollte innerhalb der Umgebung des Benutzers, nicht "verbunden" holographic Frames oder den Cursor an die Hand geben.
* **Audio Directors:** [Räumliche Sound](spatial-sound-design.md) bieten eine leistungsfähige Möglichkeit zum Herstellen von Objekten in einer Szene (Benutzer von Objekten, die eine Eingabe Warnungen) oder um Aufmerksamkeit zu einem bestimmten Zeitpunkt im Raum (um die Ansicht des Benutzers in Schlüsselobjekte Richtung zu verschieben) weiterzuleiten. Mit audio Directors, die Aufmerksamkeit des Benutzers führen, kann dies zu weniger offensichtlich und weniger intrusiv als visual Directors sein. In einigen Fällen kann es sein am besten beginnen Sie mit einem audio Director, und klicken Sie dann zu einem visual Director fortfahren, wenn der Benutzer das Stichwort nicht erkannt wird. Audio Directors können auch mit visual Directors für hinzugefügte Hervorhebung gekoppelt werden.

### <a name="commanding-navigation-and-menus"></a>Befehle, Navigation und Menüs

Schnittstellen in mixed Reality-Funktionen werden im Idealfall eng digitale Inhalte zugeordnet, die sie steuern. Daher können ist 2D-Menüs sind häufig nicht optimal geeignet für die Interaktion und für Benutzer schwierig zu bequem mit in der holografischen Frame. Für Benutzeroberflächen, die Elemente der Benutzeroberfläche wie z. B. Menüs oder Text-Felder erforderlich sind, erwägen Sie die Verwendung einer [Tag-along Methode](billboarding-and-tag-along.md) folgen Sie den holographic Frame nach einer kurzen Verzögerung. Vermeiden Sie das Sperren von Inhalt auf den Frame, wie ein Heads-Up-Display, wie dies für den Benutzer und unterbrechen die Bedeutung von Immersion für andere digitale Objekte in der Szene kann werden kann.

Alternativ sollten Sie Elemente der Benutzeroberfläche direkt auf die spezifischen Inhalte, dass sie steuern, sodass Interaktionen auf natürliche Weise in den Raum des Benutzers ausgeführt. Unterteilen Sie z. B. eine komplexe Menü, in separate Teile. Mit jeder Schaltfläche oder eine Gruppe von Steuerelementen, die an das angegebene Objekt aus, die die Interaktion wirkt sich auf angefügt werden. Um dieses Konzept weiter nutzen zu können, sollten Sie auf die Verwendung von [es Objekte](interactable-object.md).

### <a name="gaze-and-gaze-targeting"></a>Blicke und Blicke für

Holographic Frames stellt ein Tool für Entwickler auf Interaktionen der Trigger als auch auswerten, wo die Aufmerksamkeit eines Benutzers aufdecken möchten. [Bestaunen](gaze.md) ist eines der der [wichtige Interaktionen für HoloLens](interaction-fundamentals.md), bei dem Blicke zugeordnet werden kann [Gesten](gestures.md) (z. B. mit Air-tippen) oder [Voice](voice-input.md) (ermöglicht kürzere natürlicher Sprache basierende Interaktionen). Daher macht dies ein Speicherplatz für digitale Inhalte beachtet sowie die Interaktion mit dem holographic Frame. Die Benutzeroberfläche für die Interaktion mit mehreren Objekten in den Benutzerbereich (z. B. Auswahl mehrerer Objekte in den Benutzerbereich mit Blicke + Geste), ggf. übertragen diese Objekte in die Ansicht des Benutzers oder Einschränken der Menge der erforderlichen head datenverschiebung Förderung [Benutzerkomfort](comfort.md).

Blicke kann auch nachverfolgen Aufmerksamkeit des Benutzers über eine Benutzeroberfläche und welche Objekte verwendet werden, oder Teile der Szene Benutzer bezahlt, die meiste Aufmerksamkeit auf. Dies kann insbesondere die Verwendung für das Debuggen einer Erfahrung ermöglicht Analysetools wie Heatmaps angezeigt, in dem Benutzer die meisten Ausgaben werden Zeit oder, bestimmte Objekte oder Interaktion fehlen sein. Blicke, die nachverfolgung kann auch ein leistungsstarkes Tool für begünstigende Faktoren in Umgebungen bereitstellen (finden Sie unter den [Lowes Küche](holographic-frame.md#lowes-kitchen) Beispiel).

## <a name="performance"></a>Leistung

Ordnungsgemäße Verwendung des Frames, holographic ist elementar für die [Leistungsqualität](understanding-performance-for-mixed-reality.md) auftritt. Eine gängige Herausforderung für technische (und Nutzbarkeit) zu einer Überladung des Benutzers-Frame mit digitaler Inhalte, der Rendering-Leistung, kann es zu Leistungseinbußen verursachen. Erwägen Sie stattdessen verwenden den vollständigen Raum des Benutzers, um digitale Inhalte anordnen, oben beschriebenen mit den Verfahren zum Verringern des Aufwand, der Rendering und eine optimale Anzeigequalität sicherstellen.

Digitaler Inhalte innerhalb der holographic die HoloLens kann auch kombiniert werden, mit der [Stabilisierung Ebene](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md) für eine optimale Leistung und [– Hologramm Stabilität](hologram-stability.md).

## <a name="examples"></a>Beispiele

### <a name="volvo-cars"></a>Volvo Cars

>[!VIDEO https://www.youtube.com/embed/DilzwF90vec]

Auf der Oberfläche Ausstellungsraum aus Volvo Autos können Kunden auch eines Fahrzeugs-Funktionen in einer HoloLens-Benutzeroberfläche, die von einem Kollegen Volvo geführtes lernen. Volvo vor, einer großen Herausforderung, mit dem holographic Frame: ein Auto in voller Größe ist zu groß für die rechts neben einem Benutzer zu platzieren. Die Lösung bestand darin, die Erfahrung mit einer physischen Wahrzeichen, eine zentrale Tabelle in der Ausstellungsraum, mit einem kleineren digitale Modell des Autos platziert werden, am oberen Rand der Tabelle zu beginnen. Dadurch wird sichergestellt, dass der Benutzer das vollständige Auto angezeigt wird, wenn es eingeführt wird, ermöglicht einen Überblick über die räumliche zu verstehen, wenn das Fahrzeug die realen Bereitstellung weiter unten in der Umgebung erreicht.

Die Volvo tritt auf, wird visual Directors, erstellen einen lange visuellen Effekt aus dem kleineren Car-Modell für die Tabelle, an der Wand im Raum anzeigen verwenden. Dies führt zu einen Effekt "Magic-Fenster", zeigt die vollständige Ansicht der Autos in einem Abstand, weitere Funktionen des Autos Praxis bedarfsorientiert veranschaulicht. Die Bewegungen ist horizontal, ohne direkte Interaktion des Benutzers (stattdessen erfassen Hinweise visuell und aus der Volvo Zuordnen der audioaufzeichnung der Benutzeroberfläche).

### <a name="lowes-kitchen"></a>Die Lowe Küche

Eine Store-Benutzeroberfläche aus der Lowe Einladungen Kunden in einer umfassenden Nachbildung eine Küche, verschiedenen Dingen Verkaufschancen zu veranschaulichen, wie Sie durch die HoloLens gesehen. Die Küche im Speicher bietet einen physischen Hintergrund für digitale Objekte, die einem leeren Zeichenbereich der Appliances Countertops und CAB-Dateien für mixed Reality-Erfahrung, um Sie zu erweitern.

Physische fungieren als statische Orientierungspunkte für den Benutzer selbst auf der Oberfläche Erden, wie eine Lowes zuordnen den Benutzer über verschiedene Produktoptionen und beendet führt. Auf diese Weise kann die Zuordnung verbal anweisen, die Aufmerksamkeit des Benutzers 'Kühlschrank' oder 'zentriert von der Küche"auf Showcase digitale Inhalte.

![Eine Lowes Zuordnung wird verwendet, einen Tablet, um Kunden über die HoloLens-Funktionalität.](images/loweskitchen-750px.jpg)<br>
*Eine Lowes Zuordnung wird verwendet, einen Tablet, um Kunden über die HoloLens-Funktionalität.*

Die benutzererfahrung wird teilweise durch eine Tablet-Erfahrung durch die Lowes Zuordnung gesteuert verwaltet. Teil des Mitarbeiters-Rolle wäre in diesem Fall auch Lesekopfes, leiten ihre Aufmerksamkeit reibungslos über die Punkte in der Küche von Interesse zu beschränken. Die Tablet-Oberfläche bietet auch die Lowes zugeordnet Blicke-Daten in Form einer Sicht Heatmap der Küche helfen zu verstehen, in denen der Benutzer (z. B. auf einen bestimmten Bereich von Cabinetry) Einstichs ist genauer vermitteln mit Anleitungen zu gestalten.

Eine genauere Betrachtung der Lowes Küche Erfahrung, finden Sie unter [Microsofts Keynote auf der Ignite 2016](https://www.youtube.com/watch?v=gC_4JxF0e_k).

### <a name="fragments"></a>Fragmente

In den HoloLens-game-Fragmenten ist Sie Wohnzimmer in virtuellen Tatort angezeigt wird, Hinweise und Beweis sowie einen virtuellen Besprechungsraum, in dem Sie sich mit den Zeichen sprechen, die auf Ihre Stühle befinden und erfahren Sie, Ihre Wände transformiert.

![Fragmente wurde entwickelt, mit Zeichen, die Interaktion mit realen Objekten und Oberflächen Startseite des Benutzers erfolgen soll.](images/fragments-750px.jpg)<br>
*Fragmente wurde entwickelt, mit Zeichen, die Interaktion mit realen Objekten und Oberflächen Startseite des Benutzers erfolgen soll.*

Wenn Benutzer zunächst die Oberfläche beginnen, sind sie aufgrund eines kurzen Zeitraums Anpassung ist, in denen nur wenig Benutzerinteraktion erforderlich ist, stattdessen diese sich mit der Registerkarte Einzeltestmethode einzufügen. Dies wird auch sichergestellt, dass es sich bei der Raum ordnungsgemäß für das Spiel interaktiven Inhalt zugeordnet ist.

Über die Umgebung Zeichen werden als zentraler Punkt und fungieren als visual Directors (Head Verschiebungen zwischen Zeichen, die zum Suchen oder Gestenhandler auf interessante Bereiche aktivieren). Das Spiel auch basiert auf stärker akzentuiert optische Hinweise, wenn ein Benutzer finden Sie ein Objekt oder ein Ereignis zu lange dauert, und nutzt intensiv räumliche Audio (vor allem bei Zeichen stimmen bei der Eingabe einer Szene).

### <a name="destination-mars"></a>Ziel: MARS

Im Ziel: MARS-Erfahrung auf wichtige [der NASA Kennedy Speicherplatz Center](https://blogs.windows.com/devices/2016/09/19/hololens-experience-destination-mars-now-open-at-kennedy-space-center-visitor-complex/), Besucher in eine immersive Fahrt auf die Oberfläche des Mars, die durch MDX virtuelle Darstellung legendäre Astronautenausweis gegenüberstehen Aldrin eingeladen wurden.

![Eine virtuelle gegenüberstehen Aldrin wird als zentraler Punkt für Benutzer auf dem Zielserver mit: MARS.](images/destinationmars-750px.png)<br>
*Eine virtuelle gegenüberstehen Aldrin wird als zentraler Punkt für Benutzer auf dem Zielserver mit: MARS.*

Als ein Eintauchen wurden diese Benutzer ermutigt, suchen, verschieben in alle Richtungen ausgestrahlt, um die virtuellen bricht Landschaft finden Sie unter ihrem Kopf. Obwohl-Funktion, um sicherzustellen, dass der Komfort der Benutzer, bereitgestellten gegenüberstehen Aldrin audioaufzeichnung und virtuell einen zentraler Punkt über die Umgebung. Diese virtuellen Aufzeichnung aller (erstellt von [Microsofts Mixed Reality erfassen Studios](https://www.microsoft.com/mixed-reality/capture-studios)) erstellt, die in realen, von Menschen Größe, in der Ecke des Raums ermöglichen, dass Benutzer ihn in nahezu vollständige Ansicht finden Sie unter. Neuigkeiten zu der audioaufzeichnung weitergeleitet, Benutzer auf verschiedenen Punkten in der Umgebung konzentrieren (z. B. eine Reihe von bricht eine gelungene auf dem Boden oder einen Bereich Mountain, bei der Entfernung) mit bestimmte Szene Änderungen oder Objekten, die von ihm eingeführt.

![Der virtuelle seitenaktualisierungen werden die Option zum Verschieben eines Benutzers, führen ein leistungsfähigen als zentraler Punkt über die Umgebung erstellt wird.](images/gazereset-750px.png)<br>
*Der virtuelle seitenaktualisierungen werden die Option zum Verschieben eines Benutzers, führen ein leistungsfähigen als zentraler Punkt über die Umgebung erstellt wird.*

Die realistische Darstellung aller bereitgestellt, einem leistungsstarken Blickpunkt, komplett mit feine Verfahren zum Drehen Neuigkeiten zu sich der Benutzer das Gefühl, als wäre er es, sprechen Sie. Wenn der Benutzer über die Benutzeroberfläche bewegt, verschiebt Neuigkeiten zu für Sie mit einem Schwellenwert vor der Rückgabe auf einen neutralen Status, wenn der Benutzer zu weit über seine Peripherie hinaus verschoben wird. Wenn der Benutzer über Neuigkeiten zu vollständig (z. B. etwas an anderer Stelle in der Szene ansehen) Aussehen wieder zurück zu den Neuigkeiten zu, die Microsoft-Sprachausgabe direktionale Position wird einmal erneut mit Schwerpunkt auf den Benutzer. Verfahren Sie wie folgt, geben Sie einen leistungsstarken Eindruck davon zu Entwicklungsthemen, und erstellen Sie einen zentraler Punkt innerhalb des holographic Frames Lesekopfes reduzieren und die Förderung [Benutzerkomfort](comfort.md).

## <a name="see-also"></a>Siehe auch
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Komfort](comfort.md)
* [Skalieren](scale.md)
* [Anvisieren mit dem Kopf und Verweilen](gaze-and-dwell.md)
* [Hologrammstabilität](hologram-stability.md)
