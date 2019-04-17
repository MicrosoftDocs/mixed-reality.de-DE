---
title: Mondkalender-Modul
description: LunarModule ist ein Open-Source-Beispiel-app in den Microsoft Mixed Reality Entwurf Labs. Bei diesem Projekt erfahren Sie, wie Hololens Basis Bewegungen mit einer zweihändige Überwachung erweitern und Xbox-Controller Eingabe, Objekte, die reaktive Ebene suchen zu Surface-Zuordnung erstellen und Implementieren von einfachen Menüs-Systemen.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Beispiel-apps, Entwurf, HoloLens
ms.openlocfilehash: 38f70d78b5572930b874e221fa4a85572c07b342
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595544"
---
# <a name="lunar-module"></a>Mondkalender-Modul

>[!NOTE]
>Dieser Artikel beschreibt ein Beispiel für eine explorative wir, in erstellt haben der [Mixed Reality Entwurf Labs](https://github.com/Microsoft/MRDesignLabs_Unity), einen Ort, in dem wir der Erkenntnisse zu teilen, und Vorschläge für mixed Reality-app-Entwicklung. Wenn wir neue Erkenntnisse vornehmen weiterentwickelt unser Entwurf bezogenen Artikeln und Code.

[Mondkalender Modul](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) ist eine Open-Source-Beispiel-app über den Microsoft Mixed Reality Entwurf Labs. Bei diesem Projekt erfahren Sie, wie Hololens Basis Bewegungen mit einer zweihändige Überwachung erweitern und Xbox-Controller Eingabe, Objekte, die reaktive Ebene suchen zu Surface-Zuordnung erstellen und Implementieren von einfachen Menüs-Systemen. Alle Komponenten der Projekts sind für die Verwendung in Ihren eigenen mixed Reality-app-Umgebungen verfügbar.

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>Neuer Ansatz für klassischen Oberfläche für die Windows Mixed Reality

Hohe oben in der Luft eine kleine versenden. dieser erinnert an das Modul Apollo Umfragen methodisch verzweigte Terrain unten. Unsere angeworben Pilotprojekt Flecken, eine geeignete landebereich. Die Unterlänge ist mühselig, aber glücklicherweise wurden diese Reise gestaltet oft vor haben...

![Ursprüngliche-Schnittstelle aus Ataris 1979 Mondkalender Lander](images/640px-atari-lunar-lander.png)<br>
*Ursprüngliche-Schnittstelle aus Ataris 1979 Mondkalender Lander*

[Auf Lander](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) ist ein Arcade-Classic, in dem Spieler versucht, ein Mond Lander auf einer flachen Stelle des Mondes Terrain als Pilot getestet. Jeder Benutzer in den 1970er Jahren geboren wurden hat in den meisten Fällen Stunden in einem Arcade mit ihren Augen Wirklichkeit zu diesem Vektor liefern, die aus den Himmel sinkenden geklebt verbracht. Wenn ein Player ihre Lieferadresse für eine gewünschte landebereich navigiert steigt die das Gelände um zunehmend mehr Details anzuzeigen. Erfolgreich bedeutet Landing innerhalb der sicher für die horizontale und vertikale Geschwindigkeit. Punkte sind für den Zeitaufwand für die Zielseite und verbleibende betrieben werden, mit das Angeben eines Multiplikators basierend auf der Größe des Bereichs Landing vergeben.

Abgesehen von der das Spiel gebracht der Zeitraum Arcade-spielen Konstante Innovationen der Steuerelement-Schemas. Aus den einfachsten 4-Wege-Joystick und Schaltfläche ""-Konfigurationen (finden Sie in der iconic [Pac-Man](https://en.wikipedia.org/wiki/Pac-Man)) in die hoch bestimmte und komplizierte-Schemas finden Sie in den 90er und 00 s (wie die Golf-Simulatoren und Rail-Shooter). Die Eingabe, auf dem Computer auf Lander verwendete Schema ist aus zwei Gründen besonders faszinierend: Verbraucherschutzgesetzen Attraktivität und Immersion.

![Die Atari Mondkalender Lander Arcade-Konsole](images/atariconsole.png)<br>
*Die Atari Mondkalender Lander Arcade-Konsole*

Warum haben Atari und so vielen andere spielen Unternehmen entschieden, überdenken Sie Eingabe?

Eine Durchlaufen einer Arcade "Kid" wird auf natürliche Weise durch den neuesten und flashiest Computer fasziniert sein. Aber auf Lander Funktionen eine neuartige Eingabe Mechanikers, die von der Masse ab sich bewährt.

Auf Lander verwendet zwei Schaltflächen für die Lieferadresse links und rechts drehen und **Schub Hebel** auf den Umfang der Schub steuern die Lieferadresse erzeugt. Dieser Hebel bietet Benutzern ein gewisses Maß an transaktionsprotokolleinstellungen, die ein regulärer Joystick nicht bereitstellen kann. Es ist auch eine Komponente, die moderne Aviation Cockpits gemeinsam ist. Atari wollte Mondkalender Lander, die den Benutzer in das Gefühl tauchen, dass sie in der Tat ein Mondkalender Modul Pilottests wurden. Dieses Konzept wird als bezeichnet **praktisch Immersion**.

Praktisch Immersion ist die Erfahrung von draußen Feedback wiederkehrende Aktionen ausführt. In diesem Fall hilft wiederkehrende Aktion zum Anpassen der Drosselung Hebel und Rotation der im Auge zu sehen und hören Sie unsere Ohren, die Player mit dem ein Schiff auf die Oberfläche des Mondes landing eine Verbindung herstellen. Dieses Konzept kann gebunden werden, zu der psychologischen Konzept der "Datenfluss". Wenn ein Benutzer vollständig eine Aufgabe, die richtige Mischung aus Herausforderung und Reward verfügt, damit beschäftigt, oder mehr einfach ausgedrückt, sind sie "in der Zone."

Die wichtigsten Typ stärker in mixed Reality ist fraglos eine räumliche Immersion. Der ganze Sinn von mixed Reality ist uns glauben, diese entlocken digitale Objekte vorhanden sind, in der realen Welt. Wir sind Hologramme in unserer Umgebung, die vollständige Umgebungen und Umgebungen räumlich mehr synthetisieren. Dies bedeutet nicht, dass wir noch andere Arten von Immersion in unseren Erfahrungen nutzen kann nicht wie Atari mit praktisch Immersion in Mondkalender Lander.

## <a name="designing-with-immersion"></a>Entwerfen mit immersion

Wie können wir praktisch Immersion auf eine aktualisierte, volumetrische Fortsetzung der klassischen Atari anwenden? Vor dem Umgang mit der Eingabe-Schema, muss das Spiele Konstrukt für 3-dimensionalen Raum behoben werden.

![Visualisieren von Surface-Zuordnung in HoloLens](images/surfacemapping.png)<br>
*Visualisieren räumliche Zuordnung in HoloLens*

Durch die Nutzung einer benutzerumgebung, haben wir effektiv unendliche Terrain-Optionen für die landing unserem Mondkalender-Modul. Um das Spiel die meisten der ursprünglichen Titel zu machen, kann ein Benutzer potenziell bearbeiten und Landing-Pads von unterschiedlichen Probleme in ihrer Umgebung zu platzieren.

![Das Modul Mondkalender fliege](images/640px-lm-hero.jpg)<br>
*Das Modul Mondkalender fliege*

Aufforderung des Benutzers zum erfahren, das Eingabe-Schema, steuern die Lieferadresse und eine kleine Ziel auf weitergeleitet haben, ist viel zu bitten. Bei einer erfolgreichen Spiel Features rechts neben der Herausforderung und Reward kombiniert werden. Der Benutzer sollte in der Lage, eine Ebene Schwierigkeitsgrad auswählen soll, mit der einfachste Modus durch die HoloLens überprüft einfach Aufforderung des Benutzers auf einer Oberfläche wurde erfolgreich in einer benutzerdefinierten Region weitergeleitet. Sobald ein Benutzer den Stillstand des Spiels erhält, können sie sich die damit verbundenen schwierigkeiten bereitzustellen, entsprechend den Anforderungen.

### <a name="adding-input-for-hand-gestures"></a>Hinzufügen von Eingaben für die gestensteuerung

HoloLens-Basis-Eingabe weist nur zwei Gesten - [Air, tippen Sie auf "und" Bloom](gestures.md). Benutzer müssen nicht daran denken, kontextbezogene Details in Bezug auf oder eine Wunschliste der spezifischen Bewegungen, die Oberfläche von der Plattform vielseitiger und leicht zu erlernen ist. Während das System nur diese zwei Gesten zur Verfügung stellen kann, kann HoloLens als Gerät zwei praktische auf einmal nachverfolgen. Unsere Ode zum Mondkalender Lander ist ein [umfassenden app](app-model.md) d.h. wir haben die Möglichkeit, erweitern den Basissatz von Aktionen, die zwei praktische nutzen und eigene optimal praktisch bedeutet, dass für die Navigation von Mondkalender Modul hinzufügen.

Rückblickend auf das ursprüngliche Steuerelement Schema **für Schub und Drehung lösen mussten**. Der Nachteil ist Drehung im neuen Kontext Fügt eine zusätzliche achsenstrategien (technisch gesehen zwei die y-Achse ist jedoch weniger wichtig für die Landing Page). Die zwei unterschiedliche ausliefern Bewegungen für Sicherungszwecke auf natürliche Weise jede Seite zugeordnet werden:

![Tippen Sie auf, und ziehen Sie die Geste zum Drehen von Lander auf allen drei Achsen](images/module-handdrag.gif)<br>
*Tippen Sie auf, und ziehen Sie die Geste zum Drehen von Lander auf allen drei Achsen*

**Thrust**

Der Hebel auf dem ursprünglichen Arcade-Computer in eine Skalierung der Werte zugeordnet, je höher der Hebel wurde verschoben, die weitere Schub auf die Lieferadresse angewendet wurde. Hier hingewiesen feine Unterschied wichtig ist, kann der Benutzer nutzen ihre Westentasche außerhalb des Steuerelements und beibehalten ein gewünschten Werts. Wir können die Tap-und-ziehen Verhalten effektiv verwenden, um das gleiche Ergebnis zu erzielen. Der Wert Schub beginnt bei 0 (null). Der Benutzer tippt und zieht, um den Wert zu erhöhen. An dieser Stelle sie konnte können wechseln Sie zur Verwaltung. Jede Änderung eines Werts tippen-und-ziehen Geste wäre das Delta der ursprüngliche Wert.

**Drehung**

Dies ist ein wenig schwieriger. Dass holographic "rotate" Schaltflächen auf tippen, wird für eine schlechte Erfahrung. Ein physischer Steuerelement nutzen zu können, ist nicht vorhanden, damit das Verhalten von Manipulation, der ein Objekt, das die Lander darstellt, oder klicken Sie mit der Lander selbst stammen muss. Wir haben eine Methode mithilfe von Tap-und-ziehen die dem Benutzer effektiv "Push- und pull-" können sie in der Richtung wollen auf. Jedes Mal ein Benutzer tippt und hält, der Punkt im Raum, in dem die Aktion initiiert wurde, den Ursprung für die Rotation wird. Ziehen aus dem Ursprung konvertiert das Delta der Übersetzung des Zeigers, (X, Y, Z), und wendet sie auf das Delta der Lander der Drehung Werte. Oder, einfacher, *ziehen in Leerzeichen links <> – rechts, um <> – nach unten, vorwärts <> – dreht sich die Lieferadresse entsprechend*.

Da die HoloLens zwei praktische nachverfolgen können, kann auf der rechten Drehung zugewiesen werden, während Schub von der linken Seite gesteuert wird. Transaktionsprotokolleinstellungen ist der treibende Faktor für die erfolgreiche Verwendung in diesem Spiel. Die *können* dieser Interaktionen ist die absolute höchste Priorität. Insbesondere im Kontext des praktisch Immersion. Eine Lieferadresse ein, die zu schnell reagiert, würden nach Steuern während eines zu langsam, dass der Benutzer auf "Push und Pull erfordern würde" für die Lieferadresse für eine spät lange Zeit, unnötigerweise schwierig sein.

### <a name="adding-input-for-game-controllers"></a>Hinzufügen von Eingaben für Gamecontroller

Während die gestensteuerung auf die HoloLens eine neuartige Methode eine differenziertere Kontrolle bereitstellen, ist immer noch eine bestimmte fehlende 'true' praktisch Feedback, die Sie aus analogen Steuerelementen erhalten. Verbinden einen spielen Xbox-Controller kann folglich von Physicality wiederherzustellen, während Sie gleichzeitig die Steuerelement-Sticks, um eine differenziertere Kontrolle beizubehalten.

Es gibt mehrere Möglichkeiten, die das Schema recht einfach Steuerelement mit dem Xbox-Controller zu übernehmen. Da wir die nah an der ursprünglichen Arcade einrichten wie möglich bleiben möchten **doch** am besten auf die Schaltfläche "Trigger" zugeordnet. Diese Schaltflächen sind analog Steuerelemente, d. h., sie haben mehr als nur einfache *ein- und ausschalten* angibt, die sie tatsächlich auf den Grad der Druck, legen Sie auf diese reagieren. Dadurch erhalten Sie eine ähnliche Konstrukt als die **Schub Hebel**. Im Gegensatz zu den ursprünglichen Spiel und die Bewegung von Hand wird dieses Steuerelement des Schiffs Schub Ausschneiden, sobald ein Benutzer beendet die Belastung für den Trigger einfügen. Hat noch der Benutzer das gleiche Maß transaktionsprotokolleinstellungen wie die ursprüngliche arcadetitel.

![Linken Ministick Yaw bezeichnet, und setzen Sie zugeordnet ist, Ministick rechts wird zugeordnet, um Argumente und Zurücksetzen](images/thumbsticksidebyside.gif)<br>
*Linken Ministick wird zugeordnet, um Yaw bezeichnet, und setzen Sie Sie; Ministick rechts wird zugeordnet, um Argumente und Zurücksetzen*

Die duale Thumbsticks eignen sich auf natürliche Weise in die steuernde Ship-Rotation. Leider gibt es sind 3-Achsen auf dem das Schiff gedreht werden kann und zwei Thumbsticks die jeweils zwei Achsen unterstützt. Dieser Konflikt bedeutet, dass entweder ein Ministick Steuerelemente eine Achse; oder es ist Überschneidung von Achsen für die Thumbsticks. Letztendlich, dass die erste Lösung "unterbrochen" empfunden werden, da Thumbsticks grundsätzlich in ihre lokalen blend X- und Y-Werte. Die zweite Lösung erforderlich, einige Tests durchführen, um suchen, können Sie die redundanten Achsen der naheliegendste. Das letzte Beispiel verwendet *Yaw bezeichnet* und *zurücksetzen* (X- und Y-Achse) für den linken Ministick und *Tonhöhe* und *zurücksetzen* (Achse "Z" und "X") für den rechten Ministick. Dies sind der Ansicht als das naheliegendste *zurücksetzen* scheint, die unabhängig voneinander gut mit *Yaw bezeichnet* und *Tonhöhe*. Als Randbemerkung: Verwenden Sie beide Thumbsticks für *zurücksetzen* kommt auch auf das Doppelte des Werts Drehung; es ziemlich Spaß macht, damit die Lander Schleifen ist.

Diese Beispiel-app veranschaulicht, wie räumliche Erkennung und praktisch Immersion kann eine Erfahrung dank Windows Mixed Reality extensible eingabemöglichkeiten erheblich ändern. Während Mondkalender Lander 40 Jahre im Zeitalter fast erreicht werden kann, verfügbar, dass wenig Achteck-mit-"Legs" endlos laufen die Konzepte mit gemacht. Wenn die Zukunft so vor, betrachten Sie Warum nicht früher?

## <a name="technical-details"></a>Technische Details

Finden Sie Skripts und prefabs (Vorlagen) für die Mondkalender Modul-Beispiel-app auf die [Mixed Reality-Design-Labs-GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule).

## <a name="about-the-author"></a>Der Autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Addison Linville</b><br>UX-Designer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch
* [Motion-Controller](motion-controllers.md)
* [Gesten](gestures.md)
* [Mixed Reality-App-Typen](types-of-mixed-reality-apps.md)
