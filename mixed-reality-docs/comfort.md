---
title: Bequem
description: Während der natürlichen Anzeige basiert das menschliche visuelle System auf mehreren Informationsquellen oder "Cues", um 3D-Formen und die relative Position von Objekten zu interpretieren.
author: erickjpaul
ms.author: erpau
ms.date: 04/5/2019
ms.topic: article
keywords: Gemischte Realität, Entwurf, Komfort, hololens 2, hololens (1. Gen)
ms.openlocfilehash: e3a78e9a990d207b19b287e1897897a5d6dee3ca
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024441"
---
# <a name="comfort"></a>Bequem

Während der natürlichen Anzeige basiert das menschliche visuelle System auf mehreren Informationsquellen oder "Cues", um 3D-Formen und die relativen Positionen von Objekten zu interpretieren. Einige Hinweise basieren nur auf einem einzelnen Auge (monosecues), einschließlich [linearer Perspektive](https://en.wikipedia.org/wiki/Perspective_(graphical)), [bekannter Größe](https://en.wikipedia.org/wiki/Size#Perception_of_size), Okklusion, [Tiefe der Tiefe](https://en.wikipedia.org/wiki/Depth_of_field)und unter [bringung](https://en.wikipedia.org/wiki/Accommodation_(eye)). Andere Hinweise basieren auf beiden Augen (binokulare Hinweise) und enthalten [Konvergenz](https://en.wikipedia.org/wiki/Vergence) (quasi die gegensinnige Bewegung der Augen, die zum Ansehen eines Objekts nötig ist) sowie die [binokulare Disparität](https://en.wikipedia.org/wiki/Stereopsis) (das Unterscheidungsmuster zwischen den Projektionen der Szene im Augenhintergrund). Um einen maximalen Komfort für die bereitgestellten anzeigen zu gewährleisten, ist es wichtig für Designer und Entwickler, Inhalte auf eine Weise zu erstellen und darzustellen, die die Funktionsweise dieser Hinweise in der natürlichen Welt imitiert. Aus physischer Sicht ist es auch wichtig, Inhalte zu entwerfen, die keine ermüdenden Bewegungen des Hals oder der Arme erfordern. In diesem Artikel werden die wichtigsten Überlegungen beschrieben, die Sie beachten sollten, um diese Ziele zu erreichen.

## <a name="vergence-accommodation-conflict"></a>Vergence-Unterbringungs Konflikt

Um-Objekte eindeutig anzuzeigen, müssen die Menschen den Fokus des Augen Bildes Objekts [berücksichtigen](https://en.wikipedia.org/wiki/Accommodation_%28eye%29)oder anpassen. Gleich [zeitig muss die](https://en.wikipedia.org/wiki/Convergence_(eye)) Drehung beider Augen mit der Entfernung des Objekts übereinstimmen, um zu vermeiden, dass doppelte Bilder angezeigt werden. In natürlicher Ansicht sind die Vergence-und die-Unterbringung verknüpft. Wenn Sie etwas in der Nähe anzeigen (z. b. ein Haus, das in der Nähe ihrer Nase liegt), überschreiten Sie einen Punkt und können zu einem bestimmten Punkt Wenn Sie im Gegensatz dazu etwas in der optischen unendlich sehen (ungefähr mit 6 m oder mehr für die normale Vision), werden die Augenblicke von Augen parallel und die Linsen der Augen auf unendlich angepasst. 

In den meisten Köpfen werden die Benutzer immer auf die Fokus Abstände der Anzeige (zum erhalten eines Sharp-Bilds) zugreifen, aber Sie werden mit dem Abstand des Objekts zusammengeführt, das von Interesse ist (um ein einzelnes Bild zu erhalten). Wenn Benutzer unterschiedliche Entfernungen aufnehmen und mit Ihnen zusammenführen, muss die natürliche Verknüpfung zwischen den beiden hinweisen beschädigt werden, und dies kann zu einem visuellen Unbehagen oder Ermüdung führen.

<br>

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

### <a name="guidance-for-holographic-devices"></a>Leitfaden zu Holographic-Geräten

Hololens-anzeigen werden in einer optischen Entfernung von etwa 2,0 m vom Benutzer entfernt. Daher müssen Benutzer immer fast 2.0 m aufnehmen, um ein eindeutiger Abbild auf dem Gerät zu erhalten. App-Entwickler können durch das Platzieren von Inhalten und holograms in unterschiedlichen Tiefen die konvergieren der Benutzer steuern. Das Problem des Konflikts zwischen Vergence und Unterbringung kann vermieden oder minimiert werden, indem Inhalte, auf die sich die Benutzer so nah wie möglich in etwa 2.0 m konvergieren, wie möglich beibehalten werden (d.h. in einer Szene mit sehr viel Tiefe, wenn möglich, die interessanten Bereiche, die in der Nähe von 2.0 Mio. liegen). Wenn Inhalt nicht in der Nähe von 2.0 m platziert werden kann, sind die Unannehmlichkeiten beim Konflikt zwischen Vergence und Unterkunft am größten, wenn der Blick des Benutzers zwischen unterschiedlichen Entfernungen hin und her wechselt. Anders ausgedrückt: Es ist viel besser, sich ein stationäres – Hologramm anzusehen, das 50 cm entfernt wird, als ein – Hologramm 50cm zu betrachten, das sich im Laufe der Zeit von Ihnen hin und her bewegt.

![Optimale Entfernung zum Platzieren von holograms vom Benutzer.](images/distanceguiderendering-950px.png)<br>
*Optimale Entfernung zum Platzieren von holograms vom Benutzer*

### <a name="best-practices-for-hololens-1st-gen-and-hololens-2"></a>Bewährte Methoden für hololens (1. Gen) und hololens 2

Für maximalen Komfort **liegt die optimale Zone für die – Hologramm-Platzierung zwischen 1,25 m und 5 m**. In jedem Fall sollten Designer versuchen, Inhalts Szenen zu strukturieren, um Benutzer zu ermutigen, mit dem Inhalt von 1 oder mehr zu interagieren (z. b. [Inhalts Größe und Standard Platzierungsparameter](gaze-targeting.md)anpassen). 

Obwohl der Inhalt gelegentlich mehr als 1 Mio. angezeigt werden muss, wird empfohlen, die Hologramme vor dem 40 cm zu präsentieren. Daher wird empfohlen, den **Inhalt bei 40 cm auszublenden und eine Renderingebene bei 30cm zu platzieren** , um nähere Objekte zu vermeiden.

Bei Objekten, die ausführlich verschoben werden, handelt es sich wahrscheinlicher als bei stationären Objekten. Ebenso kann es erforderlich sein, dass Benutzer schnell zwischen Fokus und Schwerpunkt wechseln (z. b. aufgrund eines Popup-Hologramms, das eine direkte Interaktion erfordert). Daher **sollten Sie besonders vorsichtig vorgehen, um zu minimieren, wie häufig Benutzer sind: Anzeigen von Inhalten, die sich in der tiefe bewegen, oder schnelles Umschalten des Fokus zwischen Near-und weitem holograms**. 

### <a name="additional-considerations-for-hololens-2-and-near-interaction-distances"></a>Weitere Überlegungen zu hololens 2 und Near Interaction Distance

Beim Entwerfen von Inhalten für die direkte (Near) Interaktion in hololens 2 oder **in allen Anwendungen, in denen Inhalte näher als 1 Million platziert werden müssen, muss besonders darauf geachtet werden, dass die Benutzerfreundlichkeit gewährleistet ist**. Die Unannehmlichkeiten aufgrund des Konflikts bei der vererhöhung der-Unterkünfte erhöhen sich exponentiell durch das Verringern der Anzeige Abstände. Darüber hinaus kann es bei Benutzern bei der Anzeige von Inhalten in naher Interaktions Abständen zu erhöhter Unschärfe kommen. Daher empfiehlt es sich, Inhalte zu testen, die sowohl innerhalb der Zone der optimalen – Hologramm-Platzierung als auch näher gerendert werden (weniger als 1,0 Mio. bis zur clippinbene). Stellen Sie sicher, dass es offensichtlich und bequem angezeigt wird. 

**Wir empfehlen die Erstellung eines "tiefen Budgets" für apps, basierend auf der Zeitspanne, in der ein Benutzer erwartet, Inhalte anzuzeigen, die in der Nähe von (weniger als 1,0 Mio.) liegen und**sich ausführlich bewegen. Ein Beispiel hierfür ist, das Platzieren des Benutzers in diesen Situationen in mehr als 25% der Fälle zu vermeiden. Wenn das tiefen Budget überschritten wird, empfehlen wir sorgfältige Benutzer Tests, um sicherzustellen, dass es sich um eine bequeme Benutzerfunktion handelt. 

Im Allgemeinen empfehlen wir außerdem sorgfältige Tests, um sicherzustellen, dass alle Interaktions Anforderungen (z. b. Geschwindigkeit der Bewegung, Erreichbarkeit usw.) in nahezu Interaktionen mit der Interaktion weiterhin für Benutzer gut sind. 


### <a name="guidance-for-immersive-devices"></a>Leitfaden für immersive Geräte

Für immersive Geräte gelten die Anleitungen und bewährten Methoden für hololens weiterhin, aber die spezifischen Werte für die Zone des Komforts werden abhängig von der Fokus Distanz zur Anzeige verschoben. Im Allgemeinen liegen die Fokus Abstände zu diesen anzeigen zwischen 1,25 m und 2,5 m. Vermeiden Sie im Zweifelsfall das Rendern von Objekten, die sich in der Nähe der Benutzer befinden, und versuchen Sie stattdessen, die meisten Inhalte 1 oder mehr zu erhalten.

## <a name="interpupillary-distance-and-vertical-offset"></a>Interpupilläre Entfernung und vertikaler Offset

Beim Anzeigen von digitalem Inhalt in den bereitgestellten anzeigen (HMD) ist die Position der Augen eines Viewers relativ zur Anzeigeposition des digitalen Inhalts kritisch. Insbesondere sind sowohl interpupillary Distance ([IPD](https://en.wikipedia.org/wiki/Pupillary_distance)) als auch Vertical Offset (VO) für die komfortable Anzeige digitaler Inhalte in HMDs wichtig. 

IPD bezieht sich auf den Abstand zwischen den Schülern bzw. den Mittel stellen einer Person. VO bezieht sich auf den potenziellen vertikalen Offset digitaler Inhalte, die in jedem Auge relativ zur horizontalen Achse der Augenblicke des Viewers angezeigt werden (Dies ist insbesondere bei horizontaler Offset-oder Binaritäten-Differenz nicht der gleiche). Falsche Übereinstimmungen mit einem oder beiden dieser Faktoren für einen einzelnen Benutzer können die Auswirkungen von Unannehmlichkeiten verschlechtern, die durch einen Vergence-Unterbringungs Konflikt verursacht werden. es kann aber sogar zu Fehlern führen, wenn V-A-Konflikte minimiert werden (z. b. für Inhalte, die im Schwerpunkt 2.0 m angezeigt werden). Abstand der hololens). 

### <a name="guidance-for-holographic-devices"></a>Leitfaden zu Holographic-Geräten

#### <a name="hololens-1st-gen"></a>HoloLens (1. Generation)

Bei HoloLens (1. Generation) wird IPD geschätzt und während der [Gerätekalibrierung](calibration.md) festgelegt. Für neue Benutzer auf einem bereits eingerichteten Gerät muss die Kalibrierung ausgeführt werden, oder IPD muss manuell festgelegt werden. VO hängt vollständig von der Geräte Anpassung ab. Um z. b. den Verwaltungsaufwand zu minimieren, muss sich das Gerät auf der Kopfzeile des Benutzers befinden, sodass die Anzeige eine Ebene mit der Achse ihrer Augen ist. 

#### <a name="hololens-2"></a>HoloLens 2

Bei HoloLens (2. Generation) wird IPD geschätzt und während der [Augen- bzw. Gerätekalibrierung](calibration.md) festgelegt. Für neue Benutzer mit einem bereits eingerichteten Gerät muss eine Kalibrierung ausgeführt werden, um sicherzustellen, dass die IPD ordnungsgemäß festgelegt ist. VO wird in hololens 2 automatisch berücksichtigt. 

### <a name="guidance-for-immersive-devices"></a>Leitfaden für immersive Geräte

Immersive HMDs für Windows Mixed Reality haben keine automatische Kalibrierung für IPD oder vo. IPD kann in der Software manuell festgelegt werden (in den Einstellungen des gemischten Reality-Portals, siehe [Kalibrierung](calibration.md)), oder einige HMDs verfügen über einen mechanischen Schieberegler, der es dem Benutzer ermöglicht, den Abstand der Linsen an eine bequeme Position anzupassen (d. h., dies entspricht ungefähr der IPD). 

## <a name="rendering-rates"></a>Renderingraten

Mixed Reality-apps sind einzigartig, da Benutzer sich auf der ganzen Welt kostenlos bewegen und mit virtuellen Inhalten interagieren können, als wären Sie echte Objekte. Um diesen Eindruck zu behalten, ist es wichtig, holograms zu erzeugen, damit Sie in der Welt stabil erscheinen und reibungslos animieren. Das Rendern [von mindestens 60 Frames pro Sekunde (fps)](understanding-performance-for-mixed-reality.md) trägt dazu bei, dieses Ziel zu erreichen. Es gibt einige gemischte Reality-Geräte, die das Rendering bei Framerates über 60 fps unterstützen, und für diese Geräte wird dringend empfohlen, bei den höheren Frameraten zu rendern, um eine optimale Benutzer Leistung zu gewährleisten.

**Tiefere Einblicke**

Um holograms so zu zeichnen, dass [Sie in der realen oder virtuellen Welt stabil sind](hologram-stability.md), müssen die apps Bilder aus der Position des Benutzers Rendering. Da das Rendern von Bildern Zeit erfordert, prognostizieren hololens und andere Windows Mixed Reality-Geräte, wo sich der Kopf eines Benutzers befindet, wenn die Bilder in den anzeigen angezeigt werden. Dieser Vorhersagealgorithmus ist eine Näherung. Windows Mixed Reality-Algorithmen und Hardware passen das gerenderte Bild so an, dass die Diskrepanz zwischen der vorhergesagten Kopfzeile und der eigentlichen Hauptposition berücksichtigt wird. Durch diesen Vorgang wird das Bild, das vom Benutzer angezeigt wird, so angezeigt, als ob es vom richtigen Speicherort gerendert wird, und holograms sind stabil. Die Updates funktionieren am besten für kleine Änderungen an der Head-Position, und Sie können einige gerenderte Bild Unterschiede nicht vollständig berücksichtigen, wie z. b. die von Motion-Parser verursachten.

**Durch Rendering in einem minimalen Framerate von 60 fps führen Sie zwei Dinge aus, um stabile Hologramme zu erstellen:**
1. Die Darstellung des Judder wird verringert, was durch ungleichmäßige Bewegung und doppelte Bilder gekennzeichnet ist. Eine schnellere – Hologramm-Bewegung und niedrigere Rendering-Raten sind mit deutlicheren Judder verknüpft. Daher ist es hilfreich, den Judder zum Verschieben von holograms zu unterstützen, um 60 fps (oder die maximale Rendering-Rate Ihres Geräts) immer beizubehalten.
2. Minimierung der Gesamt Latenz. In einer Engine mit einem Spiel Thread und einem Renderthread, der in Lockstep ausgeführt wird, kann die Ausführung mit 30fps eine zusätzliche Wartezeit von 33,3 MS addieren. Durch die Reduzierung der Latenzzeit wird der Vorhersagefehler verringert, und die hologrammstabilität wird erhöht.

**Leistungsanalyse**

Es gibt eine Reihe von Tools, die verwendet werden können, um die Anwendungs Frame Rate zu messen, wie z. b.:
* GPUView
* Visual Studio-Grafik Debugger
* Profiler, die in 3D-Engines integriert sind, z. b. der Frame Debugger in Unity

## <a name="self-motion-and-user-locomotion"></a>Selbst Bewegung und Benutzer Bewegung

Die einzige Einschränkung ist die Größe des physischen Raums. Wenn Sie es Benutzern ermöglichen möchten, sich weiter in der virtuellen Umgebung zu bewegen, als Sie in ihren realen Räumen möglich ist, muss eine Form von rein virtuellen Bewegungen implementiert werden. Bei einer dauerhaften virtuellen Bewegung, die nicht mit der tatsächlichen Benutzer Bewegung identisch ist, kann die physische Bewegung häufig Bewegungskrankheiten auslösen. Das Ergebnis ist darauf zurückzuführen, dass die *visuellen Hinweise* für die selbst Bewegung von der *virtuellen Welt* in Konflikt mit den [vestibulären](https://en.wikipedia.org/wiki/Vestibular_system) Hinweisen für die selbst Bewegung aus der *Praxis*stehen.

Glücklicherweise gibt es Tipps zum Implementieren der Benutzer Bewegung, die zur Vermeidung des Problems beitragen kann:
* Versetzen Sie den Benutzer stets in die Kontrolle über seine Bewegungen. unerwartete selbst Bewegung ist besonders problematisch.
* Menschen sind sehr sensibel für die Richtung der Schwerkraft. Daher sollten nicht vom Benutzer initiierte vertikale Bewegungen besonders vermieden werden.

### <a name="guidance-for-holographic-devices"></a>Leitfaden zu Holographic-Geräten

Eine Methode, die es dem Benutzer ermöglicht, zu einem anderen Speicherort in einer großen virtuellen Umgebung zu wechseln, besteht darin, den Eindruck zu erwecken, dass er ein kleines Objekt in der Szene verschiebt. Dieser Effekt kann wie folgt erreicht werden:
   1. Stellen Sie eine Schnittstelle bereit, in der der Benutzer einen Spot in der virtuellen Umgebung auswählen kann, in der er verschoben werden soll.
   2. Verkleinern Sie das Szenen Rendering bei der Auswahl auf einen Datenträger um die gewünschte Stelle.
   3. Wenn Sie den Punkt ausgewählt haben, können Sie den Benutzer so verschieben, als wäre er ein kleines Objekt. Der Benutzer kann dann die Auswahl in die Nähe der entsprechenden Füße verschieben.
   4. Setzen Sie bei der Auswahl das Rendering der gesamten Szene fort.

### <a name="guidance-for-immersive-devices"></a>Leitfaden für immersive Geräte

Das vorangehende Verfahren für einen Holographic-Gerät funktioniert nicht auch in einem immersiven Gerät, da die APP eine große schwarze void-oder eine andere Standardumgebung beim Verschieben des "Datenträgers" erzeugen muss. Durch diese Behandlung wird das Gefühl eines Eintauchens gestört. Ein Trick für die Benutzer Bewegung in einem immersiven Headset ist der "blink"-Ansatz. Diese Implementierung ermöglicht dem Benutzer die Kontrolle über die Bewegung und bietet einen kurzen Eindruck von der Bewegung, aber es ist so kurz, dass der Benutzer weniger wahrscheinlich von der reinen virtuellen Self-Motion-Bewegung disorientiert ist:
   1. Stellen Sie eine Schnittstelle bereit, in der der Benutzer einen Spot in der virtuellen Umgebung auswählen kann, in der er verschoben werden soll.
   2. Starten Sie bei der Auswahl eine sehr schnelle simulierte Bewegung (100 m/s) für diese Position, während Sie das Rendering schnell ausblenden.
   3. Blenden Sie das Rendering wieder aus, nachdem Sie die Übersetzung beendet haben.

## <a name="heads-up-displays"></a>Heads-Up-Anzeige

Bei First-Person-Shooter-Videogames zeigt Heads-up (HUDs) permanent Informationen wie Player-Integrität, Minikarten und Inventuren direkt auf dem Bildschirm an. HUDs funktionieren gut, um den Player auf dem neuesten Stand zu halten, ohne das Spiel zu beeinträchtigen. In gemischter Realität haben HUDs die Möglichkeit, bedeutende Unannehmlichkeiten zu verursachen und müssen an den immersiven Kontext angepasst werden. Insbesondere sind HUDs, die für die Kopfzeile des Benutzers gesperrt sind, wahrscheinlich Unbehagen. Wenn eine APP eine HUD erfordert, empfehlen wir die *Text* Sperre anstelle der Kopf Sperre. Diese Behandlung kann als Satz von anzeigen implementiert werden, die sofort mit dem Benutzer übersetzt werden, aber nicht mit dem Kopf des Benutzers drehen, bis ein Schwellenwert für die Drehung erreicht ist. Sobald diese Drehung erreicht ist, kann die HUD neu ausrichten, um die Informationen im Feld "Benutzer" anzuzeigen. Die Implementierung von 1:1 HUD-Rotation und-Übersetzung in Relation zu den Head-Bewegungen des Benutzers sollte immer vermieden werden.

## <a name="text-legibility"></a>Lesbarkeit von Text

Die optimale Lesbarkeit von Text kann dazu beitragen, die Augenbelastung zu verringern und den Komfort des Benutzers zu gewährleisten, insbesondere bei Anwendungen oder Szenarien, die erfordern, dass Benutzer in einem HMD lesen. Die Text Lesbarkeit hängt von einer Vielzahl von Faktoren ab, z. b. verschiedenen Anzeigeeigenschaften (z. b. Pixeldichte, Helligkeit, Kontrast), Eigenschaften von Lens (z. b. der chromatischen Abweichung) und Text/Schriftart-Eigenschaften (z. b. die jeweilige Schriftart). Merkmale wie Gewichtung, Abstände, serifs usw., Farbe der Schriftart, Farbe des Hintergrunds).  

Im Allgemeinen empfiehlt es sich, bestimmte Anwendungen auf die Lesbarkeit zu testen und Schrift Grade so groß wie möglich zu gestalten. Im folgenden wird ein allgemeiner Leitfaden als Ausgangspunkt für die Entwicklung angeboten. Beachten Sie, dass alle Schrift Grade in Grad des [visuellen Winkels](https://en.wikipedia.org/wiki/Visual_angle) und nicht in einer bestimmten physischen Größe gemeldet werden, die eine Orientierungshilfe in der Zone der optimalen – Hologramm-Platzierung bietet, da Sie sowohl die Textgröße als auch die Entfernung berücksichtigt. wird dem Viewer angezeigt. 

Ausführlichere Richtlinien finden Sie unter [Typografie](typography.md) und [Text auf Unity](text-in-unity.md) -Seiten.

### <a name="guidance-for-holographic-devices"></a>Leitfaden zu Holographic-Geräten

Für holografische Geräte bietet das Rendern von schwarz/dunkel-Text auf einem weißen bzw. hellen Hintergrund das konsistentere Kontrastverhältnis, da der Hintergrund Störungen aus der realen Umgebung hinter dem Rendering verdeckt. Wenn Sie weißen und hellen Text in einem schwarz/dunkel-Hintergrund Rendern, können Sie mehr von der realen Umgebung anzeigen, was die Lesbarkeit von Text beeinträchtigen kann. 

#### <a name="hololens-1st-gen"></a>HoloLens (1. Generation)

Die minimale lesbare Schriftgröße (Messung von der Schriftart Baseline zum Vorgänger) beträgt ungefähr 0,35 °, und eine bequeme Schriftgröße ist mindestens ungefähr 0,5 ° für das Lesen von Inhalten, die für den Benutzer in einer Entfernung von 2 Mio. angezeigt werden. 

#### <a name="hololens-2"></a>HoloLens 2

Die minimale lesbare Schriftgröße (Messung von der Schriftart Baseline zum Vorgänger) ist mindestens ungefähr: 
   - 0,4 °-0,5 ° bei 45cm (direkte Manipulations Distanz) 
   - 0,35 °-0,4 ° um 2.0 Mio.
   
Die bequem lesbare Schriftgröße (Messung von der Schriftart Baseline bis zum Vorgänger) ist mindestens ungefähr: 
   - 0,65 °-0,8 ° bei 45cm (direkte Manipulations Distanz)
   - 0,6 °-0,75 ° um 2.0 Mio.

Beachten Sie, dass die Schrift Grade für Text in direkten Bearbeitungs Abständen etwas größer sein müssen, da der oben beschriebene Konflikt zwischen den Verarbeitungen liegt (die Augen der Benutzer werden auf der hololens-Anzeige in einem Abstand von 2.0 m angezeigt, sodass Inhalte, z. b. 45 cm), gerendert werden. wird Benutzern möglicherweise mehr unscharf angezeigt.) 

### <a name="guidance-for-immersive-devices"></a>Leitfaden für immersive Geräte

Immersive Geräte verfügen in der Regel über ein höheres Kontrastverhältnis aufgrund der vollständigen Okklusion der Außenumgebung, können jedoch aufgrund der Vergrößerung der Linsen vor den Anzeige Vorgängen eine geringere effektive Pixeldichte aufweisen. 

Für immersive HMDs in Windows Mixed Reality liegt der niedrigste lesbare vertikale Schrift Grad (Messung von der Schriftart Baseline bis zum Vorgänger) bei ungefähr 0,7-0,9 °, und ein bequemer vertikaler Schrift Grad beträgt ungefähr 1,0 ° für das Lesen von Inhalten, die in einer Entfernung von 2 Mio. angezeigt werden. Bedienungs.

## <a name="gaze-direction"></a>Richtung des Blicks

Um den Inhalt von Augen-und Hals Belastungen zu vermeiden, sollten Sie so entworfen werden, dass übermäßig viele Augen-und Hals Bewegungen vermieden werden
* **Vermeiden** von Blickwinkeln mit mehr als 10 Grad über dem Horizont (vertikale Bewegung)
* **Vermeiden** von Blickwinkeln um mehr als 60 Grad unter dem Horizont (vertikale Bewegung)
* **Vermeiden** Sie Hals Drehungen um mehr als 45 Grad außerhalb des Mittelpunkts (horizontale Bewegung).

Der optimale (ruhende) Blickwinkel wird zwischen 10-20 Grad unterhalb der horizontalen betrachtet, da sich der Kopf in der Regel leicht nach unten neigt, insbesondere bei Aktivitäten.

![Zulässiges Feld der Ansicht (FOV), wie durch den Halsbereich der Bewegung bestimmt](images/optimal-field-of-view-2-750px.png)<br>
*Zulässiges Feld der Ansicht (FOV), wie durch den Halsbereich der Bewegung bestimmt*

## <a name="arm-positions"></a>Arm-Positionen

Die Muskelmüdigkeit kann zunehmen, wenn Benutzer in der gesamten Dauer einer Benutzer Arbeit eine Hand haben. Es kann auch ermüdet sein, dass der Benutzer eine wiederholte Bewegung von Luft Tippen über lange Dauer erzwingen muss. Aus diesem Grund wird empfohlen, dass Sie die Verwendung konstanter, wiederholter Gesten Eingaben vermeiden. Diese Ziele können erreicht werden, indem kurze Umbrüche integriert werden oder eine Mischung aus Gesten und Spracheingaben für die Interaktion mit der APP angeboten wird.

## <a name="see-also"></a>Siehe auch
* [Anvisieren](gaze.md)
* [Hologrammstabilität](hologram-stability.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Holografischer Rahmen](holographic-frame.md)
* [Kalibrierung](calibration.md)
