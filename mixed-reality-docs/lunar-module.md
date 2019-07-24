---
title: Lunar-Modul
description: Lunarmodule ist eine Open-Source-Beispiel-App aus den Mixed Reality-Entwurfs Labors von Microsoft. Mit diesem Projekt können Sie erfahren, wie Sie die grundlegenden Gesten von hololens mit zweidimensionalen nach Verfolgungs-und Xbox Controller-Eingaben erweitern, Objekte erstellen, die sich reaktiv in der Oberfläche befinden und einfache Menüsysteme suchen und implementieren können.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Beispiel-apps, Design, hololens
ms.openlocfilehash: 38f70d78b5572930b874e221fa4a85572c07b342
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516037"
---
# <a name="lunar-module"></a>Lunar-Modul

>[!NOTE]
>In diesem Artikel wird ein exploratives Beispiel erläutert, das wir in den [Entwurfs Labors für gemischte Realität](https://github.com/Microsoft/MRDesignLabs_Unity)erstellt haben, einem Ort, an dem wir unsere Erkenntnisse und Vorschläge für die Entwicklung gemischter Reality-apps teilen. Unsere Entwurfs bezogenen Artikel und Code werden sich weiterentwickeln, wenn wir neue Ermittlungen durchführen.

Das [Mond Modul](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) ist eine Open-Source-Beispiel-App aus den Mixed Reality-Entwurfs Labs von Microsoft. Mit diesem Projekt können Sie erfahren, wie Sie die grundlegenden Gesten von hololens mit zweidimensionalen nach Verfolgungs-und Xbox Controller-Eingaben erweitern, Objekte erstellen, die sich reaktiv in der Oberfläche befinden und einfache Menüsysteme suchen und implementieren können. Alle Projektkomponenten sind für die Verwendung in ihren eigenen Umgebungen mit gemischter Realität verfügbar.

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>Umdenken der klassischen Erfahrung für Windows Mixed Reality

Sehr hoch in der Atmosphäre, eine kleine Sendung, die daran erinnert, dass das Apollo-Modul das nachstehende Gebiet methodisch befragt hat. Unser furchtloses Pilotprojekt ist ein geeigneter Einstiegsbereich. Der Abstieg ist mühsam, aber glücklicherweise wurde diese Journey schon mehrmals durchgeführt...

![Ursprüngliche Schnittstelle von dem 1979-Mond-Lander von Atari](images/640px-atari-lunar-lander.png)<br>
*Ursprüngliche Schnittstelle von dem 1979-Mond-Lander von Atari*

Der [Mond-Lander](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) ist eine klassische Arkade, bei der Spieler versuchen, einen Mond-Lander an einer flachen Stelle des Mond Geländes zu überführen. Jede Person, die in den 70er Jahren geboren wurde, hat wahrscheinlich Stunden in einer Arkade verbracht, deren Augen an diesen Vektor ausgeliefert wurden. Wenn ein Player seine Auslieferung in Richtung eines gewünschten Landing Area navigiert, wird das Gelände skaliert, um progressivere Details anzuzeigen. Erfolg bedeutet, dass Sie innerhalb des sicheren Schwellenwerts der horizontalen und vertikalen Geschwindigkeit landen. Punkte werden für den Zeitaufwand für die Landung und den verbleibenden Treibstoff, mit einem Multiplikator, der auf der Größe des Landing Area basiert, erhalten.

Abgesehen vom Spiel des Spiels führte der Arkaden Zeitraum von spielen zu einer kontinuierlichen Innovation von Steuerungs Schemas. Von den einfachsten vier-Wege-Joystick-und-Schaltflächen Konfigurationen (in der berühmten [Pac-Man](https://en.wikipedia.org/wiki/Pac-Man)) zu den sehr spezifischen und komplizierten Schemas, die in den späten 90er-und 00s (z. b. in Golfsimulatoren und schienenshooern) zu sehen sind. Das Eingabe Schema, das auf dem Computer mit dem Mond-Lander verwendet wird, ist aus zwei Gründen besonders faszinierend: wenden Sie sich an, und

![Die-Arkade-Konsole des Mond-Landers von Atari](images/atariconsole.png)<br>
*Die Mond-Lander-Konsolen Konsole von Atari*

Warum haben sich die Unternehmen von Atari und so vielen anderen Spielen entschieden, Eingaben zu überdenken?

Ein Kind, das eine Arkade durchläuft, wird natürlich durch den neuesten, flashiest-Computer fasziniert. Allerdings verfügt der Mond-Lander über einen neuartigen Eingabe-Mechaniker, der sich aus der Menge herausstellte.

Der Mond-Lander verwendet zwei Schaltflächen, um den Versand nach links  und rechts zu drehen, und einen schubstift, um die Menge des von der Lieferung erzeugten Schubs Dieser Hebel gibt Benutzern einen gewissen Grad an Finesse, den ein regulärer Joystick nicht bereitstellen kann. Es ist auch eine Komponente, die von modernen Luftverkehrs-Cockpits gemeinsam ist. Der Mond-Lander wollte Mond Lander in das Gefühl eintauchen, dass Sie tatsächlich ein Mond Modul Pilot haben. Dieses Konzept wird als " **taktiles eintauchen**" bezeichnet.

Beim Immersions eintauchen handelt es sich um das Auftreten von wiederholten Aktionen im sensorisch-Feedback. In diesem Fall wird der Spieler durch die sich wiederholende Aktion zum Anpassen des Drosselungs Hebers und der Drehung, den unsere Augen sehen und die Ohren hören, dazu beiträgt, den Player mit dem Vorgang zu verbinden, der sich auf der Oberfläche des Mond Dieses Konzept kann an das psychologische Konzept von "Flow" gebunden werden. Wenn ein Benutzer vollständig in eine Aufgabe aufgenommen wird, die über die richtige Mischung aus Herausforderung und Belohnung verfügt, oder einfach ausgedrückt, sind Sie "in der Zone".

Der prominenteste Browsertyp in gemischter Realität ist das räumliche eintauchen. Die gemischte Realität besteht darin, zu glauben, dass diese digitalen Objekte in der realen Welt vorhanden sind. Wir werden Hologramme in unserer Umgebung zusammengefasst, räumlich in ganzen Umgebungen und Erfahrungen eingebettet. Dies bedeutet nicht, dass wir in unseren Erfahrungen noch keine anderen Arten von unter Gängen verwenden können

## <a name="designing-with-immersion"></a>Entwerfen mit eintauchen

Wie können wir das taktisches eintauchen auf eine aktualisierte, volumetrische-Fortsetzung auf den klassischen Atari anwenden? Vor dem Umgang mit dem Eingabe Schema muss das Spiel Konstrukt für dreidimensionalen Raum adressiert werden.

![Visualisieren der Oberflächen Zuordnung in hololens](images/surfacemapping.png)<br>
*Visualisieren der räumlichen Zuordnung in hololens*

Durch die Nutzung der Umgebung eines Benutzers verfügen wir praktisch über unendliche Optionen für das Gelände, um das Mond Modul zu landen. Um den ursprünglichen Titel am Spiel zu machen, könnte ein Benutzer möglicherweise in Ihrer Umgebung Landing Pads mit unterschiedlichen Schwierigkeiten manipulieren und platzieren.

![Über das Mond Modul](images/640px-lm-hero.jpg)<br>
*Über das Mond Modul*

Der Benutzer muss das Eingabe Schema erlernen, den Versand Steuern und ein kleines Ziel für das Land haben. Ein erfolgreiches Spielverhalten bietet die richtige Mischung aus Herausforderung und Belohnung. Der Benutzer sollte in der Lage sein, eine bestimmte Schwierigkeit zu wählen. der einfachste Modus erfordert lediglich, dass der Benutzer in einem benutzerdefinierten Bereich auf einer Oberfläche, die von den hololens überprüft wird, erfolgreich in einen benutzerdefinierten Bereich wechselt. Sobald ein Benutzer den Absturz des Spiels erhält, kann er die Schwierigkeit nach Belieben aufdrehen.

### <a name="adding-input-for-hand-gestures"></a>Hinzufügen von Eingaben für Handgesten

Die Basis Eingabe hololens hat nur zwei Gesten: [Luft tippen und-Blüte](gestures.md). Benutzer müssen sich nicht mit kontextbezogenen Nuancen oder einer Auflistungs Liste bestimmter Gesten merken, die die Schnittstelle der Plattform sowohl flexibel als auch leicht zu erlernen macht. Obwohl das System diese beiden Gesten möglicherweise nur verfügbar macht, sind hololens als Gerät in der Lage, zwei Hände gleichzeitig zu verfolgen. Unsere Ode-zu-Mond-Lander ist eine [immersive App](app-model.md) . das bedeutet, dass wir die grundlegenden Gesten der Gesten erweitern können, um zwei Hände zu nutzen und unsere eigene, delightall-Methode für die Navigation mit dem Mond Modul hinzuzufügen.

Wenn wir uns das ursprüngliche Steuerelement Schema ansehen, mussten **wir uns für die Ausrichtung und Drehung lösen**. Der Nachteil ist, dass die Drehung im neuen Kontext eine zusätzliche Achse hinzufügt (technisch gesehen zwei, aber die Y-Achse ist weniger wichtig für die Landung). Die beiden unterschiedlichen Ship-Bewegungen eignen sich natürlich, um jeder Hand zugeordnet zu werden:

![Tippen und ziehen Sie Gesten, um den Lander auf allen drei Achsen zu drehen.](images/module-handdrag.gif)<br>
*Tippen und ziehen Sie Gesten, um den Lander auf allen drei Achsen zu drehen.*

**Geschoben**

Der Hebel auf dem ursprünglichen Computer, der einer Skala von Werten zugeordnet ist, je höher der Hebel verschoben wurde, desto mehr wird auf den Versand angewendet. Ein wichtiger Aspekt, den Sie hier sehen können, ist, dass der Benutzer das Steuerelement verlassen und einen gewünschten Wert behalten kann. Wir können das Tap-und Zieh Verhalten effektiv verwenden, um das gleiche Ergebnis zu erzielen. Der Wert für den Wert beginnt bei 0 (null). Der Benutzer tippt und zieht ihn, um den Wert zu erhöhen. An diesem Punkt könnten Sie die Wartung durchführen. Jeder Wert der Tap-und Drag-Gesten Wert ist das Delta vom ursprünglichen Wert.

**Drehung**

Dies ist ein wenig komplizierter. Durch die Verwendung von Holographic "Rotation"-Schaltflächen für eine schreckliche Darstellung können Sie auf diese tippen. Es gibt kein physisches Steuerelement, das Sie nutzen können, sodass das Verhalten von der Bearbeitung eines Objekts, das den Lander darstellt, oder durch den Lander selbst erfolgen muss. Wir haben eine Methode per Tap-and-Drag-Methode verwendet, die es einem Benutzer ermöglicht, ihn in der gewünschten Richtung "Push" per Push zu überbringen. Jedes Mal, wenn ein Benutzer tippt und anhält, wird der Punkt im Raum, an dem die Geste initiiert wurde, zum Ursprung der Drehung. Beim Ziehen aus dem Ursprung wird das Delta der Hand Übersetzung (X, Y, Z) konvertiert und auf das Delta der Rotations Werte des Landers angewendet. Ganz einfach, *Wenn Sie die linke < > nach oben ziehen, nach oben < > nach unten, vorwärts <-> zurück in Leerzeichen drehen*, wird die Lieferung entsprechend gedreht.

Da die hololens zwei Hände verfolgen können, kann die Drehung der rechten Seite zugewiesen werden, während der Schub Strich von Links gesteuert wird. Finesse ist der treibende Faktor für den Erfolg in diesem Spiel. Das *Gefühl* dieser Interaktionen ist die absolute höchste Priorität. Insbesondere im Kontext des Immersions einseins. Eine Lieferung, die zu schnell reagiert, wäre unnötig schwierig zu steuern, während eine zu langsam wäre, dass der Benutzer für einen unkomplizierten langen Zeitraum ein Push-und Pull-Vorgang auf dem Lieferumfang durchführen würde.

### <a name="adding-input-for-game-controllers"></a>Hinzufügen von Eingaben für Game Controller

Während Handgesten in den hololens eine neue Methode für die fein Körnung bereitstellen, gibt es immer noch eine gewisse fehlende "wahre" Möglichkeit, die Sie von den analogen Steuerelementen erhalten. Das Verbinden eines Xbox-Spiel Controllers ermöglicht es, diesen Sinn der Physizität wiederherzustellen, während die Steuerelemente für die fein Körnung genutzt werden.

Es gibt mehrere Möglichkeiten, das relativ geradlinige Steuerungs Schema auf den Xbox-Controller anzuwenden. Da wir versuchen, so nah wie möglich an der ursprünglichen Arkade zu bleiben **, wird die** Schaltfläche für den Schalt Bereich am besten angezeigt. Diese Schaltflächen sind analoge Steuerelemente, d. h., Sie haben mehr als einfache Status Zustände *und* reagieren auf den Grad der Druck Maßnahmen. Dadurch erhalten wir ein ähnliches Konstrukt wie der **Schubhebel**. Anders als das ursprüngliche Spiel und die Handbewegung, schneidet dieses Steuerelement die Bewegung des Schiffs ab, sobald ein Benutzer die Druckfunktion nicht mehr auf den Auslösers setzt. Der Benutzer erhält weiterhin denselben Grad an Feinheiten wie das ursprüngliche Arcade-Spiel.

![Der linke Ministick ist "Yaw" und "Roll" zugeordnet, der Rechte fingerstick ist "Pitch" und "Roll" zugeordnet](images/thumbsticksidebyside.gif)<br>
*Der linke fingerstick ist "Yaw" und "Roll" zugeordnet. der Rechte fingerstick ist "Pitch" und "Roll" zugeordnet.*

Die Dual thumbsticks eignen sich natürlich zur Steuerung der Versand Rotation. Leider gibt es drei Achsen, auf denen sich der Versand drehen kann, und zwei Finger Stifte, die beide zwei Achsen unterstützen. Diese fehl Übereinstimmung bedeutet, dass entweder ein Finger Stick eine Achse steuert. oder es gibt eine Überschneidung von Achsen für die Fingerabdrücke. Die erste Lösung hat das Gefühl "beschädigt", da Fingerabdrücke von Natur aus ihre lokalen X-und Y-Werte vermischen. Die zweite Lösung erforderte einige Tests, um zu ermitteln, welche redundanten Achsen am natürlichsten sind. Das abschließende Beispiel verwendet für den linken Finger Stick die Werte für " *Yaw* " und " *Roll* " (Y-und x-Achsen) und für den rechten fingerstick " *Pitch* " und " *Roll* " (Z und x). Dies hat den natürlichsten Eindruck, dass " *Roll* " unabhängig mit " *Yaw* " und " *Pitch*" gut gekoppelt ist. Als neben Hinweis wird auch der Drehungs Wert mit beiden Fingerabdrücken für " *Roll* " verdoppelt. Es ist ziemlich lustig, dass der Lander die Schleifen durchläuft.

Diese Beispiel-App veranschaulicht, wie sich die räumliche Erkennung und das Immersions eintauchen aufgrund der erweiterbaren Eingabe Modalitäten von Windows Mixed Reality erheblich ändern können. Während sich der Mond-Lander im Alter von 40 Jahren nähert, werden die Konzepte, die mit diesem kleinen, achttägigen on-with-Legs verfügbar gemacht werden, immer wieder online geschaltet. Warum sollten Sie sich beim vorstellen der Zukunft nicht mit der Vergangenheit befassen?

## <a name="technical-details"></a>Technische Details

Sie finden Skripts und Prefabs für die Beispiel-app "Lunar Module" auf dem [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule).

## <a name="about-the-author"></a>Informationen zum Autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Addison Linville</b><br>UX-Designer@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch
* [Motion-Controller](motion-controllers.md)
* [Gesten](gestures.md)
* [Typen von Mixed Reality-Apps](types-of-mixed-reality-apps.md)
