---
title: Komfort
description: Beim natürlichen Sehen verlässt sich das visuelle System des Menschen auf mehrere Informationsquellen oder „Hinweise“, um dreidimensionale Formen und die relative Position von Objekten zu interpretieren.
author: erickjpaul
ms.author: erpau
ms.date: 06/25/2020
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Entwurf, Komfort, HoloLens 2, HoloLens (1. Gen.)
ms.openlocfilehash: 12dc632e4cba925abb1c4ac9e17364f94a6804c9
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85441817"
---
# <a name="comfort"></a>Komfort

## <a name="overview"></a>Übersicht

Beim natürlichen Sehen verlässt sich das visuelle System des Menschen auf mehrere Informationsquellen oder „Hinweise“, um dreidimensionale Formen und die relativen Positionen von Objekten zu interpretieren. Für einige Hinweise ist nur ein einzelnes Auge erforderlich (monokulare Hinweise), dazu zählen die [Linearperspektive](https://en.wikipedia.org/wiki/Perspective_(graphical)), die [vertraute Größe](https://en.wikipedia.org/wiki/Size#Perception_of_size), Okklusion, [Unschärfe der Schärfentiefe](https://en.wikipedia.org/wiki/Depth_of_field) und [Akkomodation](https://en.wikipedia.org/wiki/Accommodation_(eye)). Andere Hinweise erschließen sich nur mit beiden Augen (binokulare Hinweise). Zu ihnen zählen die [Konvergenz](https://en.wikipedia.org/wiki/Vergence) (die relative Drehung der Augen, die zum Betrachten eines Objekts erforderlich ist) und die [binokulare Disparität](https://en.wikipedia.org/wiki/Stereopsis) (das Muster der Unterschiede zwischen den Projektionen der Szene auf der Netzhaut der beiden Augen). Um bei am Kopf fixierten Anzeigeeinheiten maximalen Komfort sicherzustellen, müssen Designer und Entwickler Inhalte in einer Weise präsentieren, die das Verhalten dieser Hinweise in der natürlichen Umgebung nachahmt. Unter physischen Gesichtspunkten ist es auch wichtig, Inhalte zu entwerfen, die keine ermüdenden Bewegungen Nacken- oder Armbewegungen erfordern. In diesem Artikel befassen wir uns mit den wichtigsten Überlegungen, die beachtet werden müssen, um diese Ziele zu erreichen.

## <a name="vergence-accommodation-conflict"></a>Konvergenz-Akkomodations-Konflikt

Um Objekte scharf zu sehen, müssen Menschen [akkomodieren](https://en.wikipedia.org/wiki/Accommodation_%28eye%29), also den Fokus ihrer Augen an die Entfernung des Objekts anpassen. Gleichzeitig muss die Drehung beider Augen in der Entfernung des Objekts [konvergieren](https://en.wikipedia.org/wiki/Convergence_(eye)), um das Sehen von Doppelbildern zu vermeiden. Beim natürlichen Sehen sind Konvergenz und Akkomodation verknüpft. Wenn Sie etwas in der Nähe Liegendes betrachten (beispielsweise eine Stubenfliege kurz vor Ihrer Nase), überkreuzen sich Ihre Augen und akkomodieren auf einen nahegelegenen Punkt. Im Gegenzug werden, wenn Sie etwas in der optischen Unendlichkeit sehen (die bei normaler Sehstärke ungefähr bei 6 m oder weiter beginnt), die Sichtachsen Ihrer Augen parallel, und die Linsen Ihrer Augen akkomodieren auf unendlich. 

Bei den meisten Head-Mounted Displays akkomodieren die Benutzer immer auf die Brennweite der Anzeige (um ein scharfes Bild zu erhalten), konvergieren aber auf die Entfernung des interessierenden Objekts (um ein einzelnes Bild zu erhalten). Wenn Benutzer auf verschiedene Entfernungen akkomodieren und konvergieren, muss der natürliche Zusammenhang zwischen den zwei Hinweisen aufgebrochen werden, und dies kann zu visuellem Unbehagen und Ermüdung führen.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/-606oZKLa_s" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### <a name="guidance-for-holographic-devices"></a>Leitfaden zu holografischen Geräten

HoloLens-Displays sind auf eine optische Entfernung von 2.0 m vom Benutzer festgelegt. Auf diese Weise müssen die Benutzer immer in der Nähe von 2 m akkomodieren, um im Gerät ein scharfes Bild aufrecht zu erhalten. App-Entwickler können die Konvergenz der Augen der Benutzer leiten, indem sie Inhalte und Hologramme in verschiedenen Tiefen positionieren. Unbehagen aufgrund des Konvergenz-Akkomodations-Konflikts kann vermieden oder minimiert werden, indem Inhalte, zu denen Benutzer konvergieren, so nahe wie möglich im Bereich um 2,0 m gehalten werden (platzieren Sie also in einer Szene mit großer Tiefe die interessierenden Bereiche möglichst in einer Entfernung von 2,0 m vom Benutzer). Wenn Inhalte nicht nahe bei 2,0 m gehalten werden können, ist das Unbehagen aufgrund des Konvergenz-Akkomodations-Konflikts dann am größten, wenn der Blick des Benutzers zwischen verschiedenen Entfernungen hin- und herwechselt. Anders ausgedrückt, es ist viel angenehmer, ein stehendes Hologramm zu betrachten, das in 50 cm Entfernung bleibt, als ein Hologramm in 50 cm Entfernung zu betrachten, das sich im Lauf der Zeit auf Sie zu und von Ihnen weg bewegt.

![Optimale Entfernung vom Benutzer für die Positionierung von Hologrammen.](images/distanceguiderendering-950px.png)<br>
*Optimale Entfernung vom Benutzer für die Positionierung von Hologrammen*

### <a name="best-practices-for-hololens-1st-gen-and-hololens-2"></a>Bewährte Methoden für HoloLens (1. Gen.) und HoloLens 2

Für maximalen Komfort **liegt der optimale Bereich für die Platzierung von Hologrammen zwischen 1,25 m und 5 m**. Unter allen Umständen sollten Designer versuchen, Inhaltsszenen so zu strukturieren, dass die Benutzer ermutigt werden, 1 m oder weiter entfernt von den Inhalten zu interagieren (z. B. durch Anpassen von [Inhaltsgröße und Standard-Platzierungsparametern](gaze-and-commit.md)). 

Zwar kann es gelegentlich erforderlich sein, Inhalte näher als 1 m entfernt anzuzeigen, wir raten aber davon ab, Hologramme jemals näher als 40 cm entfernt darzustellen. Wir empfehlen vielmehr, **Inhalte bei 40 cm auszublenden und eine Beschneidungsebene für das Rendern bei 30 cm zu platzieren**, um jegliche näher gelegenen Objekte zu vermeiden.

Objekte, die sich in der Tiefe bewegen, erzeugen aufgrund des Konvergenz-Akkomodations-Konflikts mit größerer Wahrscheinlichkeit Unbehagen als statische Objekte. Analog dazu kann die Anforderung, schnell zwischen einem nahen und einem fernen Fokus zu wechseln (beispielsweise wegen eines Popup-Hologramms, das direkte Interaktion erfordert) beim Benutzer zu visuellem Unbehagen und Ermüdung führen. Daher sollte **besondere Sorgfalt darauf verwendet werden, die Häufigkeit dieser zwei Punkte für Benutzer zu minimieren: das Betrachten von Inhalten mit wechselnder Raumtiefe und schnelles Umschalten des Fokus zwischen nahen und fernen Hologrammen**. 

### <a name="additional-considerations-for-hololens-2-and-near-interaction-distances"></a>Zusätzliche Überlegungen zu HoloLens 2 und kurzen Interaktionsentfernungen

Beim Entwerfen von Inhalten für die direkte (nahe) Interaktion in HoloLens 2 oder **in allen Anwendungen, in denen Inhalte näher als 1 m entfernt platziert werden müssen, sollte besonderes Augenmerk auf den Komfort der Benutzer gelegt werden**. Die Wahrscheinlichkeit des Auftretens von Unbehagen aufgrund des Konvergenz-Akkomodations-Konflikts steigt mit abnehmendem Betrachtungsabstand exponentiell an. Darüber hinaus erleben Benutzer beim Betrachten von Inhalten in kurzem Interaktionsabstand möglicherweise eine stärkere Unschärfe. Daher empfiehlt es sich, Inhalte sowohl innerhalb des Bereichs der optimalen Hologrammplatzierung als auch näher (weniger als 1,0 m bis hinab zur Beschneidungsebene) zu testen, um sicherzustellen, dass die Darstellung scharf und komfortabel zu betrachten ist. 

**Wir empfehlen, ein „Tiefenbudget“ für Apps einzurichten, das auf der Länge der Zeit basiert, in der von einem Benutzer das Betrachten von Inhalten erwartet wird, die in der Nähe (näher als 1,0 m) liegen und sich mit wechselnder Raumtiefe bewegen**. Beispielsweise könnte vermieden werden, den Benutzer mehr als 25 % der Zeit solchen Situationen auszusetzen. Wenn das Tiefenbudget überschritten wird, empfehlen wir sorgfältige Benutzertests, um sicherzustellen, dass das Benutzererleben angenehm bleibt. 

Im Allgemeinen empfehlen wir außerdem sorgfältige Tests, um sicherzustellen, dass alle Interaktionsanforderungen (z. B. Bewegungsgeschwindigkeit, Erreichbarkeit usw.) bei kurzen Interaktionsabständen für die Benutzer angenehm bleiben. 


### <a name="guidance-for-immersive-devices"></a>Leitfaden für immersive Geräte

Für immersive Geräte gelten die Anleitungen und bewährten Methoden für HoloLens ebenfalls, die spezifischen Werte für die Komfortzone verlagern sich jedoch je nach dem Fokalabstand zum Display. Im Allgemeinen liegt der Fokalabstand für diese Displays zwischen 1,25 und 2,5 m. Vermeiden Sie im Zweifelsfall das Rendern von interessierenden Objekten in zu großer Nähe zum Benutzer, und versuchen Sie stattdessen, die meisten Inhalte mindestens 1 m vom Benutzer entfernt zu halten.

## <a name="interpupillary-distance-and-vertical-offset"></a>Pupillendistanz und vertikaler Offset

Beim Betrachten von digitalen Inhalten auf Head-Mounted Displays (HMDs) kommt der Position der Augen eines Betrachters relativ zur Anzeigeposition der digitalen Inhalte besondere Bedeutung zu. Insbesondere sind die Pupillendistanz ([PD](https://en.wikipedia.org/wiki/Pupillary_distance)) und der vertikale Offset (Versatz) für das komfortable Betrachten digitaler Inhalte mit HMDs wichtig. 

PD bezeichnet den Abstand zwischen den Pupillen der Augen von Personen. VO bezeichnet den potenziellen vertikalen Offset digitaler Inhalte, die jedem Auge präsentiert werden, relativ zur horizontalen Achse der Augen des Betrachters (es ist zu beachten, dass dies NICHT das gleiche wie der durch den Augenabstand bedingte horizontale Offset ist, die binokulare Disparität). Eine Fehlanpassung eines oder beider dieser Faktoren an den einzelnen Benutzer kann die Wirkung des Unbehagens aufgrund des Konvergenz-Akkomodations-Konflikts noch verstärken, kann aber auch dann Unwohlsein hervorrufen, wenn der K-A-Konflikt minimiert wurde (z. B. bei Inhalten, die im Fokalabstand von 2,0 m der HoloLens dargestellt werden). 

### <a name="guidance-for-holographic-devices"></a>Leitfaden zu holografischen Geräten

#### <a name="hololens-1st-gen"></a>HoloLens (1. Generation)

Bei HoloLens (1. Gen.) wird die PD geschätzt und während der [Kalibrierung](calibration.md) des Geräts festgelegt. Für neue Benutzer eines bereits eingerichteten Geräts muss die Kalibrierung durchgeführt werden, oder die PD muss manuell eingestellt werden. VO hängt ausschließlich von der Anpassung des Geräts ab. Insbesondere muss sich zur Minimierung von VO das Gerät so auf dem Kopf des Benutzers befinden, dass sich die Displays auf einer Höhe mit der Achse der Augen des Benutzers befinden. 

#### <a name="hololens-2"></a>HoloLens 2

Bei HoloLens 2 wird die PD geschätzt und während der [Kalibrierung](calibration.md) von Auge/Gerät festgelegt. Für neue Benutzer eines bereits eingerichteten Geräts muss die Kalibrierung durchgeführt werden, um sicherzustellen, dass die PD ordnungsgemäß eingestellt ist. VO wird in HoloLens 2 automatisch berücksichtigt. 

### <a name="guidance-for-immersive-devices"></a>Leitfaden für immersive Geräte

Immersive HMDs für Windows Mixed Reality besitzen keine automatische Kalibrierung für PD oder VO. Die PD kann manuell in Software eingestellt werden (unter den Einstellungen im Mixed Reality-Portal, siehe [Kalibrierung](calibration.md)). Einige HMDs weisen auch einen manuellen Schieberegler auf, der die Anpassung des Linsenabstands an eine komfortable Position ermöglicht (d. h. eine Position, die ungefähr der PD des Benutzers entspricht). 

## <a name="rendering-rates"></a>Renderingraten

Mixed Reality-Apps sind insofern einzigartig, dass Benutzer sich frei in der Umgebung bewegen und mit virtuellen Inhalten interagieren können, als handle es sich um reale Objekte. Um diesen Eindruck aufrecht zu erhalten, müssen Hologramme unbedingt so gerendert werden, dass sie in der Umgebung stabil erscheinen und ruckelfrei animiert werden. Die Erreichung dieses Ziels wird durch Rendern mit [mindestens 60 Bildern/s (frames per second, FPS)](understanding-performance-for-mixed-reality.md) unterstützt. Einige Mixed Reality-Geräte unterstützen das Rendern bei höheren Bildfrequenzen als 60 FPS, und für diese Geräte wird ein Rendern mit höherer Bildfrequenz dringend empfohlen, um eine optimale Benutzererfahrung zu bieten.

**Tiefere Einblicke**

Um Hologramme so darzustellen, dass sie [in der realen oder virtuellen Umgebung stabil](hologram-stability.md) erscheinen, müssen Apps Bilder von der Position des Benutzers aus rendern. Da das Rendern von Bildern Zeit erfordert, sagen HoloLens und andere Windows Mixed Reality-Geräte vorher, wo sich der Kopf eines Benutzers befinden wird, wenn die Bilder in den Displays angezeigt werden. Dieser Vorhersagealgorithmus stellt eine Annäherung dar. Windows Mixed Reality-Algorithmen und die Hardware passen das gerenderte Bild so an, dass die Abweichung zwischen der vorhergesagten Kopfposition und der tatsächlichen Kopfposition berücksichtigt wird. Durch diesen Vorgang erscheint das vom Benutzer betrachtete Bild als vom richtigen Ort aus gerendert, und Hologramme fühlen sich stabil an. Die Aktualisierungen funktionieren am Besten für kleine Änderungen der Kopfposition und können einige Unterschiede im gerenderten Bild nicht vollständig berücksichtigen, beispielsweise solche, die aufgrund von Bewegungsparallaxe entstehen.

**Indem Sie für das Rendering mindestens eine Bildfrequenz von 60 FPS verwenden, fördern Sie zwei Effekte, die stabile Hologramme begünstigen:**
1. Verringern des Auftretens von Vibration (Judder), die sich durch ungleichmäßige Bewegung und Doppelbilder bemerkbar macht. Eine schnellere Bewegung von Hologrammen und niedrigere Renderingraten gehen mit verstärkter Vibration einher. Daher hilft das Bestreben, jederzeit 60 FPS (oder die maximale Renderingrate Ihres Geräts) aufrecht zu erhalten, Vibration bei bewegten Hologrammen zu vermeiden.
2. Minimierung der Gesamtlatenz. In einer Engine mit einem Spielthread und einem Renderingthread, die im Gleichschritt arbeiten, kann die Ausführung mit 30 FPS zu zusätzlichen 33,3 ms Latenz führen. Durch die Verringerung der Latenz verringert sich auch der Vorhersagefehler, und die Hologrammstabilität wird erhöht.

**Leistungsanalyse**

Es gibt eine Reihe von Tools, die zum Messen der Bildfrequenz Ihrer Anwendung verwendet werden können, darunter:
* GPUView
* Visual Studio-Grafikdebugger
* Integrierte Profiler von 3D-Engines, z. B. der Frame Debugger in Unity

## <a name="self-motion-and-user-locomotion"></a>Eigenbewegung und Ortsveränderung des Benutzers

Die einzige Begrenzung ist die Größe Ihres physischen Raums – wenn Sie Benutzern erlauben möchten, sich in der virtuellen Umgebung weiter zu bewegen, als das in ihren realen Räumen möglich ist, muss eine Form rein virtueller Fortbewegung implementiert werden. Anhaltende virtuelle Bewegung, die nicht mit der realen, physischen Bewegung des Benutzers übereinstimmt, ruft jedoch häufig Bewegungskrankheit hervor. Dieses Ergebnis hat seinen Grund in dem Gegensatz zwischen den *visuellen Hinweisen* für die Eigenbewegung aus der *virtuellen Welt* und den [vestibulären Hinweisen](https://en.wikipedia.org/wiki/Vestibular_system) für die Eigenbewegung, die aus der *realen Welt* stammen.

Glücklicherweise gibt es Tipps zum Implementieren von Ortsveränderung des Benutzers, die zur Vermeidung des Problems beitragen können:
* Geben Sie immer dem Benutzer die Kontrolle über seine Bewegungen; unerwartete Eigenbewegung ist besonders problematisch
* Menschen sind für die Richtung der Schwerkraft sehr sensibel. Daher sollten insbesondere nicht vom Benutzer eingeleitete Vertikalbewegungen vermieden werden.

### <a name="guidance-for-holographic-devices"></a>Leitfaden zu holografischen Geräten

Eine Methode, dem Benutzer die Bewegung an einen anderen Ort in einer großen virtuellen Umgebung zu ermöglichen, ist die Vermittlung des Eindrucks, dass der Benutzer ein kleines Objekt in der Szene bewegt. Dieser Effekt kann wie folgt erreicht werden:
   1. Stellen Sie eine Benutzeroberfläche bereit, auf der der Benutzer einen Punkt in der virtuellen Umgebung auswählen kann, an den er sich bewegen möchte.
   2. Verkleinern Sie nach erfolgter Auswahl das Rendering der Szene bis zu einer Scheibe, die den gewünschten Punkt umgibt.
   3. Ermöglichen Sie es dem Benutzer nun, den Punkt zu bewegen, als wäre er ein kleines Objekt, ohne seine Auswahl aufzuheben. Dann kann der Benutzer die Auswahl in die Nähe seiner Füße verschieben.
   4. Nehmen Sie beim Aufheben der Auswahl das Rendering der Gesamtszene wieder auf.

### <a name="guidance-for-immersive-devices"></a>Leitfaden für immersive Geräte

Das genannte Verfahren für holografische Geräte funktioniert bei immersiven Geräten nicht so gut, da es von der App das Rendern eines großen schwarzen Leerraums oder einer anderen Standardumgebung während des Verschiebens der „Scheibe“ verlangt. Dieses Vorgehen zerstört die Illusion des Eintauchens. Ein Trick für Ortsveränderung des Benutzers bei immersiven Headsets ist das „Blink“-Verfahren. Diese Implementierung gibt dem Benutzer die Kontrolle über seine Bewegung und vermittelt einen kurzen Bewegungseindruck, der aber so kurz gestaltet ist, dass der Benutzer sich mit geringerer Wahrscheinlichkeit durch die rein virtuelle Eigenbewegung desorientiert fühlt:
   1. Stellen Sie eine Benutzeroberfläche bereit, auf der der Benutzer einen Punkt in der virtuellen Umgebung auswählen kann, an den er sich bewegen möchte.
   2. Beginnen Sie beim Treffen der Auswahl mit einer sehr schnellen (100 m/s) Bewegung auf den Zielort zu, während Sie zugleich das Rendering ausblenden.
   3. Blenden Sie das Rendering nach erfolgtem Ortsübergang wieder ein.

## <a name="heads-up-displays"></a>Head-Up-Displays

In First-Person-Shooter-Videospielen stellen Head-Up-Displays (HUDs) permanent Informationen wie die Gesundheit des Spielers, Kartenausschnitte und Inventare direkt auf dem Bildschirm dar. HUDs funktionieren gut, wenn es darum geht, den Spieler auf dem Laufenden zu halten, ohne das Spielerlebnis zu beeinträchtigen. In Mixed-Reality-Erlebnissen haben HUDs das Potenzial, erhebliches Unbehagen zu verursachen und müssen an den stärker immersiven Kontext angepasst werden. Insbesondere HUDs, die starr an die Kopfhaltung des Spielers gebunden sind, führen mit hoher Wahrscheinlichkeit zu Unbehagen. Wenn für eine App ein HUD erforderlich ist, empfehlen wir die Bindung an den *Körper* statt an den Kopf. Dieses Verhalten kann als ein Satz Displays implementiert werden, die sich sofort mit dem Benutzer bewegen, sich aber nicht mit dem Kopf des Benutzers drehen, bis ein Schwellenwert für die Drehung erreicht ist. Sobald dieser Grad an Drehung erreicht ist, kann sich das HUD neu ausrichten, um dem Benutzer die Informationen in seinem Sichtfeld anzuzeigen. Das Implementieren einer 1:1-Drehung und Verschiebung von HUDs relativ zu den Kopfbewegungen des Benutzers sollte in jedem Fall vermieden werden.

## <a name="text-legibility"></a>Lesbarkeit von Text

Optimale Lesbarkeit von Text kann helfen, die Anstrengung der Augen zu vermindern und den Komfort des Benutzers aufrecht zu erhalten, insbesondere bei Einsatzgebieten oder Szenarien, in denen Benutzer lesen müssen, während sie ein HMD benutzen. Die Lesbarkeit von Text hängt von einer Reihe von Faktoren ab, darunter:
* Eigenschaften der Anzeige, wie etwa Pixeldichte, Helligkeit und Kontrast. 
* Objektiveigenschaften wie chromatischer Aberration
* Eigenschaften des Texts/der Schriftart, wie etwa Gewicht, Abständen, Serifen und der Farbe von Vorder- und Hintergrund.  

Im Allgemeinen empfehlen wir, bestimmte Anwendungen auf Lesbarkeit hin zu testen und den Schriftgrad so groß wie möglich festzulegen, um eine komfortable Benutzererfahrung zu erzielen. Ausführlichere Anweisungen für holografische und immersive Geräte finden Sie auf unseren Seiten zu [Typografie](typography.md) und [Text in Unity](text-in-unity.md).

## <a name="holographic-frame-considerations"></a>Überlegungen zum Ausschnitt bei holografischer Darstellung

Bei Mixed Reality-Benutzeroberflächen mit großen oder vielen Objekten muss unbedingt berücksichtigt werden, wieviel Kopf- und Nackenbewegung für die Interaktion mit Inhalten erforderlich ist. Die Benutzeroberflächen können hinsichtlich der Kopfbewegung in drei Kategorien aufgeteilt werden: 
* **Horizontal** (von Seite zu Seite)
* **Vertikal** (auf- und abwärts)
* **Immersiv** (sowohl horizontal als auch vertikal)
 
Beschränken Sie nach Möglichkeit die Mehrzahl der Interaktionen entweder auf die horizontale oder die vertikale Kategorie. Dabei sollten im Idealfall die meisten Erfahrungen in der Mitte des holografischen Rahmens ablaufen, während sich der Kopf des Benutzers in einer neutralen Position befindet. Vermeiden Sie Interaktionen, die vom Benutzer ein ständiges Verschieben seiner Ansicht an eine unnatürliche Kopfposition erfordern (beispielsweise häufige Blicke nach oben, um auf die Interaktion mit einem wichtigen Menü zuzugreifen).

![Der optimale Bereich für Inhalte liegt zwischen 0 und 35 Grad unterhalb des Horizonts](images/optimal-field-of-view-2.png)<br>
*Der optimale Bereich für Inhalte liegt zwischen 0 und 35 Grad unterhalb des Horizonts*

Horizontale Kopfbewegungen eignen sich besser für häufige Interaktionen, während vertikale Kopfbewegungen den ungewöhnlichen Ereignissen vorbehalten sein sollten. Beispielsweise sollten bei einer Benutzeroberfläche, die eine lange horizontale Zeitachse umfasst, vertikale Kopfbewegungen (etwa das Blicken nach unten auf ein Menü) für Interaktionen eingeschränkt werden.

Erwägen Sie es, Ganzkörperbewegungen anstelle von Kopfbewegungen zu fördern, indem Sie Objekte im umgebenden Raum des Benutzers platzieren. Bei Benutzeroberflächen mit bewegten oder großen Objekten sollte den Kopfbewegungen besondere Aufmerksamkeit geschenkt werden, insbesondere, wenn sie häufig Bewegungen sowohl entlang der horizontalen als auch der vertikalen Achse erfordern.

## <a name="gaze-direction"></a>Blickrichtung

Um Belastungen von Augen und Nacken zu vermeiden, sollten Inhalte so entworfen werden, dass übermäßige Augen- und Nackenbewegungen vermieden werden.
* **Vermeiden** Sie Blickwinkel, die jenseits von 10 Grad über dem Horizont liegen (vertikale Bewegung)
* **Vermeiden** Sie Blickwinkel, die jenseits von 60 Grad unter dem Horizont liegen (vertikale Bewegung)
* **Vermeiden** Sie Drehungen des Nackens um mehr als 45 Grad aus der Mittelposition (horizontale Bewegung)

Als optimaler Blickwinkel (in Ruhe) wird der Bereich von 10–20 Grad unterhalb der Waagerechten angesehen, da der Kopf tendenziell leicht nach vorn gebeugt wird, insbesondere bei Aktivitäten.

## <a name="arm-positions"></a>Armpositionen

Die Muskeln können ermüden, wenn von Benutzern erwartet wird, eine Hand während der gesamten Dauer einer Erfahrung angehoben zu halten. Ebenfalls ermüdend kann es sein, vom Benutzer wiederholt Tippbewegungen in die Luft über längere Zeit zu verlangen. Es empfiehlt sich daher, konstante, wiederholte Eingabegesten in Benutzererfahrungen zu vermeiden. Diese Ziele können erreicht werden, indem kurze Pausen integriert werden oder eine Mischung aus Gesten- und Spracheingaben für die Interaktion mit der App angeboten wird.

## <a name="see-also"></a>Siehe auch
* [Anvisieren](gaze-and-commit.md)
* [Hologrammstabilität](hologram-stability.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Holografischer Rahmen](holographic-frame.md)
* [Kalibrierung](calibration.md)
