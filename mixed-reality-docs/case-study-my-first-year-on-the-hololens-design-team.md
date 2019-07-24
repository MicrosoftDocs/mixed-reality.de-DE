---
title: Fallstudie-mein erstes Jahr im hololens-Entwurfs Team
description: Meine Reise von einem 2D-Flatland zur 3D-Welt begann, als ich das hololens-Entwurfs Team im Januar 2016 antrat.
author: designnomad
ms.author: haejinl
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, hololens, Design, Editorial, Personal
ms.openlocfilehash: 050645e6096559a4f37b033e5ddfdc5444039c08
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873955"
---
# <a name="case-study---my-first-year-on-the-hololens-design-team"></a>Fallstudie-mein erstes Jahr im hololens-Entwurfs Team

Meine Reise von einem 2D-Flatland zur 3D-Welt begann, als ich das hololens-Entwurfs Team im Januar 2016 antrat. Vor dem beitreten zum Team hatte ich nur wenig Möglichkeiten zum 3D-Entwurf. Das chinesische Sprichwort war wie das chinesische Sprichwort zu einer Fahrt Tausender Kilometer, beginnend mit einem einzigen Schritt, außer in meinem Fall war der erste Schritt ein Sprung!

![Springen von 2D zu 3D](images/2D_to_3D-800px.gif)<br>
*Springen von 2D zu 3D*

> *"Mir ist bewusst, dass ich in den Arbeitsplatz des Treibers gesprungen bin, ohne zu wissen, wie das Auto zu steuern ist. Ich war überlastet und ängstlich, aber sehr schwer zu sein. "*<br>
> – Hae Jin Lee

Im vergangenen Jahr habe ich die Kenntnisse und das wissen so schnell wie möglich übernommen, aber ich habe trotzdem viel zu lernen. Hier habe ich vier Beobachtungen mit einem Video-Tutorial verfasst, das meinen Übergang von einem 2D-zum 3D-Interaktions-Designer dokumentiert. Ich hoffe, dass meine Arbeit anderen Designern die Möglichkeit bietet, den Sprung zu 3D zu übernehmen.

## <a name="good-bye-frame-hello-spatial--diegetic-ui"></a>Gut-Bye-Frame. Hello Spatial/diegetic UI

Jedes Mal, wenn ich Poster, Magazine, Websites oder App-Bildschirme entworfen habe, war ein definierter Frame (in der Regel ein Rechteck) eine Konstante für jedes Problem. Wenn Sie diesen Beitrag nicht in einem hololens oder einem anderen VR-Gerät lesen, *betrachten Sie dies von außen* bis 2D-Bildschirm, der innerhalb eines Frames sicher geschützt ist. Der Inhalt ist für Sie extern. Das Mixed Reality-Headset entfernt jedoch *den Frame*, sodass Sie sich innerhalb des Inhalts Raums befinden, indem Sie die Inhalte von innen nach außen suchen und durchlaufen.

Ich habe dies konzeptionell verstanden, aber am Anfang habe ich die einfache Übertragung von 2D-nachdenken in 3D-Raum untergebracht. Das war natürlich nicht gut geeignet, da der 3D-Raum seine eigenen eindeutigen Eigenschaften hat, wie z. b. eine Ansichts Änderung (basierend auf der Kopfbewegung des Benutzers) und [andere Anforderungen an den Benutzerkomfort](https://www.youtube.com/watch?v=-606oZKLa_s/) (basierend auf den Eigenschaften der Geräte und den Benutzern, die Sie verwenden). Beispielsweise ist in einem 2D-Benutzeroberflächen-Entwurfs Raum das Sperren von UI-Elementen in der Ecke eines Bildschirms ein sehr gängiges Muster, aber diese HUD-Benutzeroberfläche (Head-Up-Display) ist in den Erfahrungen mit der Benutzeroberfläche von Mr/VR nicht ganz normal Dadurch wird verhindert, dass der Benutzer in den Raum eintauchen kann Es ist so, als ob Sie ein ärgerliches Staubpartikel auf Ihrer Brille haben, das Sie nicht mehr benötigen. Im Laufe der Zeit habe ich gelernt, dass es natürlicher ist, Inhalte im 3D-Raum zu positionieren und das Text-Locked-Verhalten hinzuzufügen, mit dem der Inhalt in einer relativen festgelegten Entfernung dem Benutzer folgt.

![Text (gesperrt)](images/bodylockedtagalong.gif)<br>
*Text (gesperrt)*

<br>

![Weltweit gesperrt](images/worldlocked.gif)<br>
*Weltweit gesperrt*

### <a name="fragments-an-example-of-great-diegetic-ui"></a>Fragmente Beispiel für eine großartige, diätetische Benutzeroberfläche

[Fragmente](https://www.microsoft.com/p/fragments/9nblggh5ggm8), ein Krimi, das von [Asobo Studio](http://www.asobostudio.com/) für hololens entwickelt wurde, veranschaulicht eine überzeugende Benutzeroberfläche. In diesem Spiel wird der Benutzer ein Haupt Zeichen, ein Detektiv, der versucht, ein Geheimnis zu lösen. Die entscheidenden Hinweise zum lösen dieses Geheimnisses werden im physischen Raum des Benutzers angezeigt und sind häufig in einem fiktiven Objekt eingebettet, anstatt eigenständig zu existieren. Diese diätetische Benutzeroberfläche ist tendenziell weniger auffundbar als die durch den Text gesperrten Benutzeroberfläche, sodass das Asobo-Team clever viele Hinweise verwendet hat, wie z. b. den Blickwinkel der virtuellen Zeichen, den Sound, das Licht und die Führungslinien (z. b. Pfeil, der auf die Position des Hinweises zeigt), um

![Fragmente: Beispiele für die Benutzeroberfläche](images/fragments-game-example-1.jpg)<br>
*Fragmente: Beispiele für die Benutzeroberfläche*

### <a name="observations-about-diegetic-ui"></a>Beobachtungen über die Benutzeroberfläche von diegetic

Die räumliche Benutzeroberfläche (sowohl Body-Locked als auch weltweit gesperrt) und die Benutzeroberfläche von diegetic haben ihre eigenen Stärken und Schwächen. Ich empfehle Entwicklern, so viele Mr/VR-apps wie möglich auszuprobieren und Ihr eigenes Verständnis und ihre Empfindlichkeit für verschiedene Methoden zur Benutzeroberflächen Positionierung zu entwickeln.

## <a name="the-return-of-skeuomorphism-and-magical-interaction"></a>Die Rückgabe von "skeumorphismus" und "magische Interaktion"

Skeuomorphism, eine digitale Schnittstelle, die die Form von realen Objekten imitiert hat, wurde für die letzten 5 – 7 Jahre in der Entwurfs Branche "uncool". Wenn Apple schließlich das flatdesign in ios 7 in den Weg gebracht hat, schien es, als ob skeuomorphism als Schnittstellen-Entwurfsmethodik endgültig tot war. Dann kam ein neues Medium, das Mr/VR-Headset, auf den Markt, und es sieht so aus, als ob "skeuomorphism" wieder zurückgegeben wird. : )

### <a name="job-simulator-an-example-of-skeuomorphic-vr-design"></a>Auftrags Simulator: Ein Beispiel für das skeuomorphe VR-Design

Der [Auftrags Simulator](http://jobsimulatorgame.com/), ein von [owlchemy Labs](https://owlchemylabs.com/) entwickelter whimsical-Spiel, ist eines der beliebtesten Beispiele für den skeuomorph-VR-Entwurf. Innerhalb dieses Spiels werden Spieler in Zukunft transportiert, in denen sich die Roboter Menschen austauschen und die Menschen ein Museum besuchen, um zu erfahren, wie Sie in einem von vier verschiedenen Aufträgen alltägliche Aufgaben durchführen können: Automechanic, Gourmet Chef, Store Clerk oder Office Worker.

Der Vorteil von "skeuomorphism" ist eindeutig. Vertraute Umgebungen und Objekte in diesem Spiel helfen neuen VR-Benutzern, sich mit dem virtuellen Raum vertraut zu machen. Außerdem haben Sie die Meinung, dass Sie sich in der Kontrolle befinden, indem Sie den Objekten und den entsprechenden physischen Reaktionen vertraute Kenntnisse und Verhalten zuordnen. Um z. b. eine Tasse Kaffee zu trinken, müssen die Benutzer einfach auf den Kaffee Computer zeigen, auf eine Schaltfläche klicken, den Cup-handle drücken und Sie in der Praxis auf den Mund kippen.

![Auftrags Simulator](images/job-simulator.gif)<br>
*Auftrags Simulator*

Da es sich bei Mr/VR immer noch um ein Entwicklungs Medium handelt, ist die Verwendung eines bestimmten skeumorphismus-Grades erforderlich, um die Mr/VR-Technologie zu entften und Sie in größere Zielgruppen auf der ganzen Welt einzuführen. Außerdem kann die Verwendung von skeumorphismus oder realistischer Darstellung für bestimmte Anwendungs Typen, wie z. b. die Operation oder die Flugsimulation, von Vorteil sein. Da das Ziel dieser apps darin besteht, bestimmte Fähigkeiten zu entwickeln und zu verfeinern, die direkt in der realen Welt angewendet werden können, desto genauer ist die Simulation in der realen Welt, umso besser ist das wissen.

Beachten Sie, dass "skeumorphismus" nur ein Ansatz ist. Das Potenzial der Mr/VR-Welt ist weitaus größer als das, und Designer sollten bestrebt sein, magische, hypernatürliche Interaktionen zu erstellen – neue Kosten, die in der Mr/VR-Welt eindeutig möglich sind. Als Einstieg empfiehlt es sich, den normalen Objekten magische Kräfte hinzuzufügen, damit Benutzer ihre grundlegenden Wünsche erfüllen können – einschließlich teleportierung und Omniscience.

![Die magische Tür von Doraemon (links) und Ruby-Slipper (rechts)](images/doraemons-magical-door-and-ruby-slippers.jpg)<br>
*Die magische Tür von Doraemon (links) und Ruby-Slipper (rechts)*

### <a name="observations-about-skeuomorphism-in-vr"></a>Beobachtungen zu "skeumorphismus" in VR

Von "an beliebiger Stelle" in "Doraemon", "Ruby-pantozen" im Assistenten von "Oz" bis "maurader es Map" in Harry Potter, Beispiele für gewöhnliche Objekte mit Magic Power in beliebte Fiktion. Mit diesen magischen Objekten können wir eine Verbindung zwischen der realen Welt und der fantastischen Visualisierung zwischen den Neuerungen und der Art und Weise visualisieren. Beachten Sie, dass beim Entwerfen des magischen oder surrealen Objekts ein ausgewogenes Verhältnis zwischen Funktionalität und Unterhaltung erforderlich ist. Achten Sie darauf, die Versuchung zu schaffen, etwas ausschließlich für den Zweck der Neuheit zu erstellen.

## <a name="understanding-different-input-methods"></a>Grundlegendes zu verschiedenen Eingabemethoden

Als ich das 2D-Medium entworfen habe, musste ich mich auf die Berührungs-, Maus-und Tastatur Interaktionen für Eingaben konzentrieren. Im Entwurfs Bereich von Mr/VR wird der Text zur Schnittstelle, und die Benutzer können eine breitere Auswahl an Eingabemethoden verwenden: einschließlich Sprache, Blick, Bewegung, [6-DOF-Controllern](https://en.wikipedia.org/wiki/Six_degrees_of_freedom)und Handschuhe, die eine intuitivere und direkte Verbindung mit virtuellen Objekten bieten.

![Verfügbare Eingaben in hololens](images/inputs.jpg)<br>
*Verfügbare Eingaben in hololens*

> *"Alles ist am besten für etwas und für etwas anderes."*<br>
> – [Bill Buxton](https://www.billbuxton.com/)

Beispielsweise gibt die Gesten Eingabe mithilfe von Bare-Hand-und Kamerasensoren auf einem HMD-Gerät Benutzern die Hand, Controller zu halten oder Schwitz Handschuhe zu verwenden. häufige Verwendung kann jedoch eine physische Ermüdung verursachen (a. k. a Gorilla Arm). Außerdem müssen Benutzer ihre Hände in der Sicht behalten. Wenn die Kamera die Hände nicht sehen kann, können die Hände nicht verwendet werden.

Die Spracheingabe eignet sich gut für die Durchführung komplexer Aufgaben, da Sie Benutzern die Möglichkeit bietet, mit einem Befehl (z. b. "mir die Filme von Laika Studio" anzuzeigen ") und auch sehr wirtschaftlich zu sein, wenn Sie mit anderer Modalität gekoppelt sind (z. b." Face Me "-Befehl, der – Hologramm, den ein Benutzer für den Benutzer ansieht. Die Spracheingabe funktioniert jedoch möglicherweise nicht gut in einer lärmenden Umgebung oder ist in einem sehr stillen Raum nicht geeignet.

Neben Gesten und Sprache sind überwachte gesteuerte Controller (z. b. Oculus Toucheingabe, Vive usw.) sehr beliebte Eingabemethoden, da Sie einfach zu verwenden und korrekt sind, die [proprietäre](https://en.wikipedia.org/wiki/Proprioception)Benutzereingaben nutzen und passive, willkürliche Hinweise bereitstellen. Diese Vorteile haben jedoch den Nachteil, dass Sie nicht in der Lage sind, die vollständige Finger Verfolgung zu verwenden.

![Senso (Left) und Manus VR (right)](images/senso-and-manus-vr.jpg)<br>
*Senso (Left) und Manus VR (right)*

Handschuhe gewinnen zwar nicht so beliebt wie Controller, aber dank der Mr/VR-Welle gewinnen Handschuhe mehr Schwung. Vor kurzem wurde die Eingabe von Hirn-/Warnungs-Eingaben als eine Schnittstelle für virtuelle Umgebungen gestartet, indem der EEG-oder EMG-Sensor in das Headset integriert wurde (z. b. [mindmaze VR](http://www.mindmaze.com/)).

### <a name="observations-about-input-methods"></a>Beobachtungen zu Eingabemethoden

Dabei handelt es sich nur um ein Beispiel für Eingabegeräte, die auf dem Markt für Mr/VR verfügbar sind. Sie werden fortlaufend weiterentwickelt, bis die Branche eine Weile findet und den bewährten Methoden zustimmt. Bis dahin sollten die Designer auf neue Eingabegeräte achten und in den spezifischen Eingabemethoden für das jeweilige Projekt gut vertraut sein. Designer müssen in Einschränkungen nach kreativen Lösungen suchen und gleichzeitig die Stärken eines Geräts spielen.

## <a name="sketch-the-scene-and-test-in-the-headset"></a>Skizzieren der Szene und Testen im Headset

Als ich in 2D gearbeitet habe, habe ich meistens nur den Inhalt skizziert. In gemischtem Realitäts Raum jedoch nicht ausreichend. Die gesamte Szene sollte skizziert werden, um sich die Beziehungen zwischen dem Benutzer und den virtuellen Objekten besser vorzustellen. Um meiner räumlichen Betrachtung zu helfen, habe ich begonnen, Szenen in [Kino 4D](https://www.maxon.net/en/products/cinema-4d/overview/) zu skizzieren und manchmal einfache Ressourcen für das Erstellen von Prototypen in [Maya](http://www.autodesk.com/products/maya/overview/)zu erstellen. Ich hatte nie ein Programm verwendet, bevor ich dem hololens-Team beigetreten bin, und ich bin immer noch ein Newbie, aber das Arbeiten mit diesen 3D-Programmen half mir, sich mit der neuen Terminologie vertraut zu machen, wie [Shader](https://en.wikipedia.org/wiki/Shader) und [IK (Inverse Kinematik)](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-07C3BA47-32BB-477B-B6C5-1090E5C9B81C-htm.html/).

**"Unabhängig von der Art und Weise, in der ich die Szene in 3D skizziert habe, war das eigentliche Verhalten im Headset fast nie identisch mit der Skizze. Daher ist es wichtig, die Szene in den Ziel-Headsets zu testen. "– Hae Jin Lee**

Für hololens-Prototypen habe ich alle Tutorials zu den Lernprogrammen für [Mixed Reality](tutorials.md) ausprobiert, um zu beginnen. Dann begann ich mit [holotoolkit. unity](https://github.com/Microsoft/HoloToolkit-Unity/) , das Microsoft Entwicklern zur Beschleunigung der Entwicklung von Holographic-Anwendungen bereitstellt. Wenn ich etwas daran gewöhnt habe, habe ich meine Frage an die [hololens-Frage & Antwort Forum](https://forums.hololens.com/categories/questions-and-answers/)gepostet.

Nachdem ich die grundlegenden Kenntnisse der hololens-Prototypen abgerufen habe, wollte ich andere nicht-Programmierer selbst in den Prototyp versetzen. Ich habe also ein Video-Tutorial erstellt, in dem gezeigt wird, wie eine einfache Projekt Kachel mithilfe von hololens entwickelt wird. Ich erkläre mich kurz mit den grundlegenden Konzepten, damit Sie selbst dann, wenn Sie keine Probleme bei der hololens-Entwicklung haben, die folgenden Schritte ausführen können.

<br>

>[!VIDEO https://www.youtube.com/embed/58612RT2CT8]
*Ich habe dieses einfache Tutorial für nicht-Programmierer wie mich gemacht.*

Bei der VR-Prototyperstellung nahm ich Kurse bei der [VR dev School](http://learn.vrdev.school/) vor und nahm auch [3D-Inhaltserstellung für Virtual Reality](https://www.lynda.com/Unreal-Engine-tutorials/3D-Content-Creation-Virtual-Reality/482055-2.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3aVirtual+Reality+%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2/) unter Lynda.com auf. Die VR dev School bot mir ausführlichere Informationen zur Codierung, und der Lynda-Kurs bot mir eine kurze Einführung in das Erstellen von Assets für VR.

## <a name="take-the-leap"></a>Springen Sie den Sprung

Vor einem Jahr war mir gefallen, dass all dies etwas überwältigend war. Nun kann ich Ihnen sagen, dass es sich um 100% um den Aufwand handelt. "Mr/VR" ist immer noch sehr groß, und es gibt so viele interessante Möglichkeiten, auf die Sie warten müssen. Ich denke, ich bin in der Lage, einen kleinen Teil beim Entwerfen der Zukunft zu spielen. Ich hoffe, dass Sie mich auf dem Weg in den 3D-Raum einbinden werden!

## <a name="about-the-author"></a>Informationen zum Autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Hae Jin Lee" width="60" height="60" src="images/haejinlee.jpg"></td>
<td style="border-style: none"><b>Hae, Jin Lee</b><br>UX-Designer@Microsoft</td>
</tr>
</table>

 
