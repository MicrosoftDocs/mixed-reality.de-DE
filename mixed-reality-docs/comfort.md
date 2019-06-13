---
title: Komfort
description: Während der natürlichen anzeigen verwendet der menschliche visual System mehrere Quellen von Informationen oder "Hinweise," um 3D-Formen und die relative Position von Objekten zu interpretieren.
author: erickjpaul
ms.author: erpau
ms.date: 04/5/2019
ms.topic: article
keywords: Mixed Reality, Entwurf, comfort, HoloLens-2, HoloLens (1. Generation)
ms.openlocfilehash: e3a78e9a990d207b19b287e1897897a5d6dee3ca
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024441"
---
# <a name="comfort"></a>Komfort

Während der natürlichen anzeigen verwendet der menschliche visual System mehrere Quellen von Informationen oder "Hinweise," um 3D-Formen sowie die relativen Positionen von Objekten zu interpretieren. Einige Hinweise bedienen sich lediglich einen einzelnen Eye (monokularen Hinweise), einschließlich [lineare Perspektive](https://en.wikipedia.org/wiki/Perspective_(graphical)), [bekannte Größe](https://en.wikipedia.org/wiki/Size#Perception_of_size), verdecken, [Tiefe-von-Feld Blur](https://en.wikipedia.org/wiki/Depth_of_field), und [ Unterkunft](https://en.wikipedia.org/wiki/Accommodation_(eye)). Weitere Hinweise basieren auf beide Augen (Fernglas Hinweise), und umfassen [Vergence](https://en.wikipedia.org/wiki/Vergence) (im Wesentlichen die relative Rotationen im Auge erforderlich, auf ein Objekt zu suchen) und [Fernglas Unterschiede zu](https://en.wikipedia.org/wiki/Stereopsis) (das Muster der Unterschiede zwischen den Projektionen der Szene auf der Rückseite der zwei Augen). Um sicherzustellen, dass optimalen Komfort für Head-bereitgestellt wird, ist es wichtig, dass Designer und Entwickler zum Erstellen und zeigen den Inhalt in einer Weise, die imitiert, wie diese Hinweise in der natürlichen Welt ausgeführt werden. Hinsichtlich der physischen ist es auch wichtig, Inhalte zu entwickeln, die keine fatiguing Bewegungen des trichterhalses oder Arms erforderlich ist. In diesem Artikel Gehe wir über wichtige Aspekte zu berücksichtigen, um diese Ziele zu erreichen.

## <a name="vergence-accommodation-conflict"></a>Vergence Unterbringung Konflikt

Um Objekte deutlicher anzeigen, die Menschen müssen [aufzunehmen](https://en.wikipedia.org/wiki/Accommodation_%28eye%29), oder passen Sie ihren Augen Fokus auf die Entfernung des Objekts. Zur gleichen Zeit, die Drehung der beide Augen muss [konvergieren](https://en.wikipedia.org/wiki/Convergence_(eye)) Entfernung des Objekts, um zu vermeiden, Anzeigen von doppelten Bildern. In natürliche anzeigen, sind Vergence und Unterbringung verknüpft. Wenn Sie etwas in der Nähe (z. B. in der Nähe Ihrer Nase Housefly) anzeigen Augen überschreiten, und Sie werden zu einem Zeitpunkt Near aufzunehmen. Wenn Sie etwas auf optischen unendlich (ungefähr 6 Millionen oder weiter für normale Vision ab) anzeigen, Ihren Augen Sichtlinie werden parallel, und entsprechend Ihren Augen Lenses unendlich. 

Im angezeigt werden, am häufigsten bereitgestellten Head-Benutzer werden immer zu berücksichtigen, die als zentraler Entfernung der Anzeige (um eine scharfe Abbild zu erhalten), aber die Zusammenführung vor der Entfernung des Objekts (für ein einzelnes Abbild zu erhalten) von Interesse sind. Wenn Benutzer ermöglichen und zu anderen Abständen zusammengeführt, muss die natürliche Verknüpfung zwischen den beiden Hinweise unterbrochen und kann dies zu visual angefasst oder Ermüdung.

<br>

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

### <a name="guidance-for-holographic-devices"></a>Leitfaden für holographic-Geräten

HoloLens zeigt sind in einer optischen Abstand ungefähr 2.0 m von der Benutzer festgelegt. Benutzer müssen daher immer in der Nähe von 2,0 m ein klares Bild auf dem Gerät beibehalten berücksichtigt werden. App-Entwickler können orientieren, in denen Benutzer Augen konvergieren, durch die Platzierung von Inhalt und Hologramme in verschiedenen Ebenen. Angefasst aus den Konflikt Vergence-Unterbringung minimiert werden, da der Inhalt, der Benutzer zu konvergieren, 2,0 m möglichst nahe, oder vermieden werden kann (z. B. in einer Szene mit viel Tiefe, platzieren Sie die Bereiche von Interesse sind, in der Nähe von 2,0 m des Benutzers, wenn möglich). Wenn Inhalt in der Nähe von 2.0 m platziert werden kann, ist angefasst aus den Konflikt Vergence-Unterbringung größten, wenn hin und her, des Benutzers Blicke zwischen verschiedenen Abstände wechselt. Das heißt, ist es viel besser vertraut sind, betrachten Sie ein stationär Hologramm, die 50 cm entfernt als, sehen Sie sich ggf. ein Hologramm 50 cm sofort bleibt, das sich im Laufe der Zeit auf und von Ihnen weg bewegt.

![Optimale Abstand zur Platzierung von Hologramme des Benutzers.](images/distanceguiderendering-950px.png)<br>
*Optimale Abstand zur Platzierung von Hologramme des Benutzers*

### <a name="best-practices-for-hololens-1st-gen-and-hololens-2"></a>Bewährte Methoden für HoloLens (1. Generation) und HoloLens 2

Für optimalen Komfort **die optimale Zone für die Platzierung von – Hologramm 1,25 m bis 5m ist**. In jedem Fall-Designer sollten versuchen, Struktur Inhalt Szenen, die Benutzern die Interaktion fördern 1m oder weiter entfernt den Inhalt (z. B. anpassen [Inhaltsgröße und Standardparameter für die Platzierung](gaze-targeting.md)). 

Obwohl Inhalt gelegentlich möglicherweise näher als 1 Million Pakete angezeigt werden, wird davon abgeraten, jemals präsentieren Hologramme näher als 40cm. Daher, es wird empfohlen, um **Inhalte auf 40cm ausgeblendet werden sollen, und platzieren Sie eine Clippingebene Rendering auf 30cm** , alle gelegenes Objekte zu vermeiden.

Objekte, die im Detail zu verschieben sind eher als feststehend Objekte zum Erzeugen von angefasst aufgrund des Konflikts Vergence-beeinflusst. Auf ähnliche Weise kann Benutzer schnell in der Nähe von- und weit-Fokus (z. B. aufgrund einer Popup – Hologramm erfordern direkte Interaktion) wechseln visual angefasst und Ermüdung dazu führen, dass. Aus diesem Grund **zusätzliche sollte geachtet werden, wie oft minimieren Benutzer: Anzeige von Inhalten, die in die Tiefe; verschoben werden, oder schnell den Fokus zwischen nah und Fern Hologramme**. 

### <a name="additional-considerations-for-hololens-2-and-near-interaction-distances"></a>Weitere Überlegungen für HoloLens 2 und in der Nähe von Interaktion entfernungen

Beim Entwerfen von Inhalt für die direkte (Interaktion in HoloLens 2 nahezu) oder **in allen Anwendungen, in denen Inhalt werden als 1 Million platziert muss, zusätzliche sollte geachtet werden, sicher Benutzerkomfort**. Angefasst aufgrund des Konflikts Vergence-beeinflusst die Wahrscheinlichkeit erhöhen sich exponentiell mit die Entfernung verringert. Darüber hinaus können Benutzer erhöhte Bluriness auftreten, wenn Anzeige von Inhalten am in der Nähe von Interaktion Abstände, daher wir Testen von Inhalten empfehlen sowohl in der Zone der auch als näher optimale – Hologramm-Platzierung (kleiner als 1,0 m auf den Clipping-Ebene) gerendert Stellen Sie sicher, dass sie klare und zeigen Sie Ihren bevorzugten bleibt. 

**Es wird empfohlen, Erstellen von "Tiefe"Budget für apps, die basierend auf die Zeitspanne, die ein Benutzer muss zum Anzeigen von Inhalt, der in der Nähe (kleiner als 1.0-m), und verschieben ausführlich**. Ein Beispiel ist, platzieren den Benutzer in Situationen verwendet, mehr als 25 % der Zeit zu vermeiden. Wenn das Budget für die Tiefe überschritten wird, wird empfohlen, eine sorgfältige Benutzer zu testen, um sicherzustellen, dass es sich um eine angenehme benutzererfahrung bleibt. 

Im Allgemeinen empfehlen wir Ihnen ebenfalls sorgfältig testen, um alle Interaktionen-Anforderungen (z. B. Geschwindigkeit der datenverschiebung, Erreichbarkeit usw.) am in der Nähe von Interaktion entfernungen sicher für Benutzer vertraut bleiben. 


### <a name="guidance-for-immersive-devices"></a>Leitfaden für immersive-Geräte

Klicken Sie für immersive Geräte die Anleitungen und bewährte Methoden für HoloLens gilt weiterhin, aber die spezifischen Werte für die Zone der Komfort abhängig vom Abstand als zentraler auf dem Bildschirm verschoben werden. Im Allgemeinen sind die als zentraler Abstände an diese zwischen 1,25 Million - 2,5 Millionen. Vermeiden Sie im Zweifelsfall Rendering betroffenen Objekte zu Benutzern in der Nähe, und stattdessen versuchen, die meisten Inhalte 1 Mio. beizubehalten oder weiter entfernt.

## <a name="interpupillary-distance-and-vertical-offset"></a>Interpupillary Abstand und den vertikalen offset

Beachten Sie beim Anzeigen von digitalen Inhalten auf Head bereitgestellten zeigt (HMD), die die Position des ein Betrachter relativ zur Anzeigeposition digitaler Inhalte ist wichtig. Insbesondere beide interpupillary Abstand ([IPD](https://en.wikipedia.org/wiki/Pupillary_distance)) und der vertikale Offset (VO) sind wichtig, dass vertraut anzeigen digitaler Inhalte in HMDs. 

IPD bezieht sich auf den Abstand zwischen den Schüler oder Rechenzentren, die von einer Einzelperson Augen. VO bezieht sich auf die der potenzielle vertikale Offset von digitalen Inhalten, die angezeigt wird, jedes Auge relativ zu die horizontale Achse von den Betrachter (insbesondere, dies ist nicht dasselbe als horizontale Offset oder Fernglas Unterschiede zu). Übereinstimmende falsch, eine oder beide dieser Faktoren für einen einzelnen Benutzer kann die Auswirkungen der angefasst durch Vergence-Unterbringung einen Konflikt verursacht vernachlässigt werden soll, aber es kann sogar Ursache angefasst, beim V-A-Konflikt minimiert wird, (z. B. für Inhalte, die an das 2.0 als zentrales m angezeigt Abstand von der HoloLens). 

### <a name="guidance-for-holographic-devices"></a>Leitfaden für holographic-Geräten

#### <a name="hololens-1st-gen"></a>HoloLens (1. Generation)

Für HoloLens (der 1. Generation), IPD geschätzte ist, und legen Sie während der Geräte [Kalibrierung](calibration.md). Neue Benutzer können eine bereits festgelegte Gerät, Kalibrierung ausgeführt werden muss oder IPD manuell festgelegt werden muss. VO hängt vollständig Gerät anpassen. Insbesondere muss um VO zu minimieren, das Gerät eines Benutzers Kopf gespeichert werden, zeigt die Ebene mit der Achse seinen Augen aufweisen. 

#### <a name="hololens-2"></a>HoloLens 2

Für HoloLens 2 IPD geschätzt und während der Eye oder das Gerät festgelegt [Kalibrierung](calibration.md). Neue Benutzer können eine bereits festgelegte Gerät, Kalibrierung ausgeführt werden muss, um sicherzustellen, dass IPD korrekt festgelegt ist. VO wird automatisch in HoloLens 2 berücksichtigt. 

### <a name="guidance-for-immersive-devices"></a>Leitfaden für immersive-Geräte

Immersive Windows Mixed Reality-HMDs verfügen über keine automatische Kalibrierung für IPD oder VO. IPD kann manuell festgelegt werden, in der Software (finden Sie unter "Mixed Reality-Portal-Einstellungen" unter [Kalibrierung](calibration.md)), oder einige HMDs haben keinen mechanischen Schieberegler an, die dem Benutzer ermöglicht, die den Abstand von der Funktionen zu einer komfortablen Position anpassen (d. h., dass ungefähr entspricht die IPD). 

## <a name="rendering-rates"></a>Rendern von Sätzen

Mixed Reality-apps sind eindeutig, da Benutzer frei, in der Welt verschieben und virtuellen Inhalt wie interagieren, als wären sie echte Objekte können. Um dieser Eindruck zu gewährleisten, unbedingt Hologramme gerendert werden, damit sie in der ganzen Welt stabile angezeigt und reibungslos zu animieren. Rendern an ein [mindestens 60 Bildern pro Sekunde (FPS)](understanding-performance-for-mixed-reality.md) unterstützt dieses Ziel zu erreichen. Es gibt einige Mixed Reality-Geräte, die höher als 60 FPS Framerates Rendering unterstützen, und für diese Geräte es wird dringend empfohlen, auf die höhere Framerates optimale benutzerfreundlichkeit zu rendern.

**Ein tieferer Einblick**

Zum Zeichnen von Hologramme aussehen [sie sind stabil, in der physischen oder virtuellen Welt](hologram-stability.md), apps, die zum Rendern von Bildern aus Position des Benutzers müssen. Da das Rendern von Bildern Zeit dauert, Vorhersagen HoloLens und andere Windows Mixed Reality-Geräte eines Benutzers Head, wo werden sollen, wenn im zeigt die Bilder angezeigt werden. Dieser Vorhersagealgorithmus ist eine Näherung. Passen Sie das gerenderte Bild, um die Abweichung zwischen den vorhergesagten Head und der tatsächlichen Head Position zu berücksichtigen, Windows Mixed Reality-Algorithmen und Hardware. Durch diesen Prozess wird das Bild angezeigt, als ob er aus der aktuellen Position gerendert wurden, das Erscheinungsbild Hologramme stabile den Benutzer sichtbar. Die Updates funktionieren am besten für kleine Änderungen an der Position der Head, und sie können nicht einige gerenderten Bilds Unterschiede, z. B. durch Motion-Parallax vollständig berücksichtigen.

**Durch das Rendering für eine minimale Framerate von 60 FPS machen Sie zwei Dinge machen stabile Hologramme:**
1. Reduzieren die Darstellung der Judder, ist die durch ungleichmäßige während der Übertragung und doppelten Bildern gekennzeichnet. Schneller – Hologramm während der Übertragung und niedrigere Render Raten zugeordnet deutlicher judder. Aus diesem Grund wollen 60 FPS (oder des Geräts maximale Render Rate) immer zu verwalten, trägt Judder für das Verschieben von Hologramme zu vermeiden.
2. Minimieren die gesamtlatenz. In ein Modul mit einem Spiel Thread und einen Renderthread kann das Ausführen im Gleichschritt, 30 FPS mit 33.3ms zusätzliche Latenz hinzufügen. Durch Verringern der Latenz, Dies verringert die Vorhersagefehler und – Hologramm Stabilität erhöht.

**Informationen zur Leistungsanalyse**

Es gibt eine Vielzahl von Tools, mit denen die Framerate der Anwendung wie z. B. Vergleichstests werden können:
* GPUView
* Visual Studio Grafik-Debugger
* Profiler-3D-Engines wie z.B. der Frame-Debugger in Unity integriert

## <a name="self-motion-and-user-locomotion"></a>Self-motion und Benutzer Locomotion

Die einzige Einschränkung besteht darin, die Größe Ihrer physischen Speicherplatz wird; Wenn Sie möchten, damit Benutzer weiter, als sie in ihre tatsächlichen Räume können in der virtuellen Umgebung verschieben, muss eine Form von rein virtuellen Motion implementiert werden. Allerdings kann dauerhafte virtuelle während der Übertragung, die nicht realen, physischen-Bewegung des Benutzers übereinstimmen häufig auslösen, während der Übertragung Krankheit. Dieses Ergebnis ist aufgrund der *visuelle Hinweise* für motion selbst aus der *virtuelle Welt* in Konflikt mit der [vestibular Hinweise](https://en.wikipedia.org/wiki/Vestibular_system) für Self-motion Feedback aus der *Praxis*.

Es gibt Tipps zum Implementieren von Locomotion für Benutzer, die dabei helfen kann, die das Problem zu vermeiden:
* Geben Sie immer den Benutzer Kontrolle über ihre Bewegungen; Unerwarteter Self motion besonders problematisch ist
* Menschen sind sehr empfindlich, was die Richtung der Schwerkraft. Aus diesem Grund sollte nicht auf Benutzer initiierter vertikale Bewegungen vor allem vermieden werden.

### <a name="guidance-for-holographic-devices"></a>Leitfaden für holographic-Geräten

Geben Sie den Eindruck, dass sie ein kleines Objekt in der Szene verschieben, ist eine Methode, die dem Benutzer ermöglichen, die an einen anderen Speicherort in einer großen virtuellen Umgebung verschieben werden. Dieser Effekt kann wie folgt erreicht werden:
   1. Geben Sie eine Schnittstelle, in denen der Benutzer auswählen kann eine Stelle in der virtuellen Umgebung, in dem sie verschieben möchten.
   2. Bei Auswahl verkleinert werden, der Rendering der Szene auf einem Datenträger, um die gewünschte Stelle.
   3. Können Sie beim halten die Stelle ausgewählt haben den Benutzer, als wäre es ein kleines Objekt verschieben. Benutzer kann die Auswahl in der Nähe ihren ersten Schritten fortfahren.
   4. Fortsetzen Sie bei Deaktivierung, die gesamte Szene zu rendern.

### <a name="guidance-for-immersive-devices"></a>Leitfaden für immersive-Geräte

Der zuvor beschriebene holographic Gerät Ansatz funktioniert nicht auch in eine immersive Gerät da es sich um die app zum Rendern von großen schwarzen "void" oder eine andere erfordert standardumgebung beim Verschieben von "Datenträger". Diese Behandlung unterbricht die Realitätsnähe sinnvoll. Ein Trick für Benutzer Locomotion in eine immersive Kopfhörer ist Ansatz das "aufleuchten". Diese Implementierung bietet dem Benutzer Kontrolle über ihre Bewegung und bietet einen kurzen Eindruck der Bewegung, jedoch ist es nun ein kurzer, dass der Benutzer weniger wahrscheinlich, dass Sie disoriented können selbst durch die rein virtuelle motion:
   1. Geben Sie eine Schnittstelle, in denen der Benutzer auswählen kann eine Stelle in der virtuellen Umgebung, in dem sie verschieben möchten.
   2. Beginnen Sie bei Auswahl eine sehr schnelle simulierten (100 m/Sek.) während der Übertragung an diesem Speicherort, und dann schnell ausgeblendet wird, der Rendering.
   3. Ausblenden nach Abschluss der Verschiebung erneut das Rendering.

## <a name="heads-up-displays"></a>Heads-Up zeigt

Im ersten Ego-Shooter-Videogames enthalten die Heads-Up zeigt (HUDs) dauerhaft Informationen wie z. B. die Gesundheit der Spieler, Mini-Karten und Bestände direkt auf dem Bildschirm. HUDs funktionieren gut, damit um den Spieler ohne dritte die Gaming-Benutzeroberfläche informiert zu bleiben. In mixed Reality-Umgebungen HUDs haben zu signifikanten angefasst führen und muss seine Kontext angepasst werden. Insbesondere werden HUDs, die fest in Head Ausrichtung des Benutzers gesperrt sind wahrscheinlich angefasst zu erzeugen. Wenn eine app eine HUD erforderlich ist, empfehlen wir *Text* Sperren statt Head sperren. Diese Behandlung kann als eine Reihe von zeigt implementiert werden, die sofort mit dem Benutzer zu übersetzen, aber nicht mit des Benutzers Head drehen, bis ein Schwellenwert der Drehung erreicht wird. Sobald diese Drehung erreicht ist, kann das HUD neu ausrichten, um die Informationen in der Sicht des Benutzers zu präsentieren. Implementieren der 1:1-HUD-Drehung und Übersetzung relativ zum des Benutzers Head sollten Bewegungen immer vermieden werden.

## <a name="text-legibility"></a>Textlesbarkeit

Der optimalen Textlesbarkeit können optimaler reduzieren, und Warten von Benutzerkomfort, insbesondere in Anwendungen oder Szenarien, die Benutzern während einer HMD lesen. Textlesbarkeit hängt von verschiedenen Faktoren wie z.B. verschiedene Anzeigeeigenschaften (z. B. Pixeldichte, Helligkeit, Kontrast) Lens-Eigenschaften (z. B. chromatische deuten) und Textschriftart/Eigenschaften (z. B. bestimmte Schriftart Eigenschaften wie Weight "," Abstand "," Serifen "," usw., Farbe, Schriftart, Farbe des Hintergrunds).  

Im Allgemeinen empfiehlt es sich um bestimmte Anwendungen für bessere Lesbarkeit testen, und machen Schriftgrade Ihren Bedürfnissen entsprechend zu groß für eine angenehme benutzererfahrung möglich ist. Im folgenden bieten wir Richtwert als Ausgangspunkt für die Entwicklung. Beachten Sie, dass alle Schriftgraden in Grad gemeldet werden [visual Winkel](https://en.wikipedia.org/wiki/Visual_angle) statt bestimmte physische Größen, die Hilfestellung bei der jede Entfernung in der Zone der optimalen – Hologramm Platzierung, da er sowohl die Größe der berücksichtigt die Text und die Entfernung wird es in der Ereignisanzeige angezeigt. 

Finden Sie unter [Typografie](typography.md) und [Text in Unity](text-in-unity.md) Seiten detailliertere Richtlinien.

### <a name="guidance-for-holographic-devices"></a>Leitfaden für holographic-Geräten

Bei holographic-Geräten bietet Rendern von Text auf einem weißen Licht/Hintergrund Schwarz/dunklen der einheitlichsten Kontrastverhältnis da Hintergrund Störungen aus der Praxis hinter das Rendern verdeckt wird. Whitepaper/leichte Text auf Schwarz/dunklen Hintergrund zu rendern, können mehrere der realen Umgebung angezeigt, die Textlesbarkeit beeinträchtigen könnten. 

#### <a name="hololens-1st-gen"></a>HoloLens (1. Generation)

Der minimale lesbar Schriftgrad (Schriftart Baseline Ascender Messen) ist ungefähr 0,35 ° aus, und ein vertraut Schriftgrad ist um ca. mindestens 0,5 ° für das Lesen von Inhalten in einem Abstand von 2m dem Benutzer angezeigt. 

#### <a name="hololens-2"></a>HoloLens 2

Der minimale lesbar Schriftgrad (Schriftart Baseline Ascender Messen) beträgt mindestens ungefähr: 
   - 0,4 ° 0,5 ° auf 45cm (direkte Bearbeitung Abstand) 
   - 0,35 ° 0,4 ° bei 2,0 m
   
Der bequem lesbar Schriftgrad, die (von Schriftart Baseline Ascender Messen) ist mindestens etwa: 
   - 0,65 ° 0,8 ° auf 45cm (direkte Bearbeitung Abstand)
   - 0,6 ° 0,75 ° bei 2,0 m

Beachten Sie, dass die Schriftgrade Ihren Bedürfnissen entsprechend müssen aufgrund der oben beschriebenen Vergence-Unterbringung-Konflikt für Text an die direkte Bearbeitung entfernungen geringfügig größer sein (Benutzer Augen sind sodass in einem Abstand von 2,0 m in der Anzeige HoloLens, damit der Inhalt, z. B. gerendert 45 cm unter Umständen mehr verschwommen Benutzern angezeigt). 

### <a name="guidance-for-immersive-devices"></a>Leitfaden für immersive-Geräte

Immersive Geräte in der Regel höher Kontrastverhältnis vollständige Einschluss der externen Umgebung haben, aber möglicherweise niedrigeren Dichte für effektives Pixel teilweise aufgrund von den Vergrößerungsfaktor für die Funktionen vor dem zeigt. 

Für immersive Windows Mixed Reality-HMDs, der minimale lesbar vertikale Schriftgrad (Schriftart Baseline Ascender Messen) ist ungefähr 0,7-0.9 ° und vertraut vertikale Schriftgrad ist ungefähr 1.0° für das Lesen von Inhalten angezeigt, die in einem Abstand von 2m, um die der Benutzer.

## <a name="gaze-direction"></a>Blicke Richtung

Um Augen- bzw. trichterhalses Dehnung zu vermeiden sollte Inhalte werden so konzipiert, dass übermäßig viele Augen und HALs Bewegungen vermieden werden.
* **Vermeiden Sie** Blicke Winkel mehr als 10 Grad über den Horizont (vertikale Verschiebung)
* **Vermeiden Sie** Blicke Winkel mehr als 60 Grad unter den Horizont (vertikale Verschiebung)
* **Vermeiden Sie** trichterhalses Drehungen mehr als 45 Grad nicht zentriert (horizontale Verschiebung)

Der optimale (Verbleib) Blicke Winkel wird als zwischen 10 bis 20 Grad unter horizontalen, betrachtet werden, wie das Anfangselement "Schräg nach unten etwas, vor allem bei Aktivitäten" ist.

![Zulässige Sichtfeld (Blickfeld) gemäß der trichterhalses-Bereich, der während der Übertragung](images/optimal-field-of-view-2-750px.png)<br>
*Zulässige Sichtfeld (Blickfeld) gemäß der trichterhalses-Bereich, der während der Übertragung*

## <a name="arm-positions"></a>ARM-Positionen

Nutze Ermüdung kann sammeln, wenn Benutzer zu einer Hand, die ausgelöst wird, während der Dauer einer Erfahrung erwartet werden. Sie können auch fatiguing sein, dass den Benutzer per Funk Gesten über lange Zeiträume tippen wiederholt vornehmen müssen. Aus diesem Grund wird empfohlen, Erfahrungen vermeiden, die Konstante, eine wiederholte Aktion Eingaben erfordern. Dieses Ziel kann erreicht werden, durch kurze Unterbrechungen integrieren oder eine Mischung von Gesten und Sprache, die Eingabe für die Interaktion mit der app bietet.

## <a name="see-also"></a>Siehe auch
* [Anvisieren](gaze.md)
* [Hologrammstabilität](hologram-stability.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Holografischer Rahmen](holographic-frame.md)
* [Kalibrierung](calibration.md)
