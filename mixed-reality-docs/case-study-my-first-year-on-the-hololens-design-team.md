---
title: 'Fallstudie: Meine erste Jahr in die HoloLens-Designteam'
description: Mein Werdegang in einem 2D-Flatland, zu der 3D-Welt gestartet, wenn ich das Entwurfsteam HoloLens im Januar 2016 verknüpft werden sollen.
author: designnomad
ms.author: haejinl
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, Entwurf, redaktionelle, personal
ms.openlocfilehash: 050645e6096559a4f37b033e5ddfdc5444039c08
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873955"
---
# <a name="case-study---my-first-year-on-the-hololens-design-team"></a>Fallstudie: Meine erste Jahr in die HoloLens-Designteam

Mein Werdegang in einem 2D-Flatland, zu der 3D-Welt gestartet, wenn ich das Entwurfsteam HoloLens im Januar 2016 verknüpft werden sollen. Vor dem Eintritt in das Team, musste ich nur sehr wenig Erfahrung in 3D Entwurf. Es war wie die chinesische Sprichwort über eine Reise von Tausend Meilen, die mit einem einzigen Schritt ab, mit der Ausnahme für mich, diesen ersten Schritt ein Sprung wurde!

![Nehmen den Sprung von 2D, 3D](images/2D_to_3D-800px.gif)<br>
*Nehmen den Sprung von 2D, 3D*

> *"Ich das Gefühl hatte, als ob ich in Geschäftsplans Stärken übersprungen haben, ohne zu wissen, wie Sie das Auto zu fahren. Ich war schwer und abschreckend, aber sehr fokussierte. "*<br>
> – Hae Jin Lee

Während des letzten Jahres halber habe ich mich um Fähigkeiten und Kenntnisse, die so schnell, wie ich könnte, aber ich immer viel noch zu lernen. Hier habe ich Sie 4 Beobachtungen mit Videolernprogramme dokumentieren mein Übergang aus einer 2D-Texturmap. zu 3D Interaktions-Designer geschrieben. Ich hoffe, dass meine Erfahrung andere Designer auszuführende den Sprung 3D inspirieren.

## <a name="good-bye-frame-hello-spatial--diegetic-ui"></a>Ewig Frame. Räumliche Hello / Diegetic UI

Wenn ich Poster, Zeitschriften, Websites oder app-Bildschirme konzipiert, war ein definierter Frame (in der Regel ein Rechteck) eine Konstante für jedes Problem. Wenn Sie diesen Beitrag in einem HoloLens oder andere VR-Geräte lesen, Sie sind *ansehen von außen* über 2D-Bildschirm sicher innerhalb eines Rahmens geschützt. Der Inhalt ist für Sie extern. Allerdings Mixed Reality Kopfhörer *beseitigt den Frame*, sodass Sie im Bereich Inhalt suchen, und durchlaufen den Inhalt von innen nach außen.

Ich dies im Prinzip verstanden, aber am Anfang vorgenommen ich den Fehler einfach 2D denken in 3D-Raum übertragen. Die offensichtlich funktionierte nicht gut, da die 3D-Raum über eigene eindeutige Eigenschaften wie z. B. eine Änderung der Ansicht (auf der Grundlage des Benutzers Bewegungen) hat und [andere Anforderungen für Benutzerkomfort](https://www.youtube.com/watch?v=-606oZKLa_s/) (basierend auf die Eigenschaften von den Geräten und die Menschen mit Diese). Z. B. in einem 2D-Bereich der UI-Entwurf, Sperren des UI-Elemente in der Ecke eines Bildschirms ist ein sehr häufiges Muster, aber dieser Stil HUD (Head-um-Display) Benutzeroberfläche ist nicht wissen natürlich MR/VR-Erfahrungen; Es beeinträchtigt die des Benutzers zu Entwicklungsthemen in den Bereich und bewirkt, dass Benutzer stören. Es ist eine lästige Staub Partikel auf Ihre Brille, die Sie zeigen werden, um zu entfernen. Im Laufe der Zeit habe ich gelernt, dass es fühlt sich erwarten, dass der Inhalt im 3D-Raum zu positionieren, und fügen Sie Text-locked Verhalten, mit der der Inhalte folgen Sie den Benutzer in einem relativen festen Abstand, hinzu.

![Body-locked](images/bodylockedtagalong.gif)<br>
*Body-locked*

<br>

![World-locked](images/worldlocked.gif)<br>
*World-locked*

### <a name="fragments-an-example-of-great-diegetic-ui"></a>Fragmente: Ein Beispiel für leistungsstarke Diegetic UI

[Fragmente](https://www.microsoft.com/p/fragments/9nblggh5ggm8), eine Ego-Crime Krimi von entwickelte [Asobo Studio](http://www.asobostudio.com/) für HoloLens eine leistungsstarke Diegetic UI veranschaulicht. In diesem Spiel wird der Benutzer ein Haupt-Zeichen, einem Detective, der versucht, ein Rätsel zu lösen. Die entscheidende Hinweise zu diesem Rätsel lösen erhalten Betriebssystem im physischen Raum des Benutzers und werden oft, eingebettete in einem fiktiven Objekt anstelle eines vorhandenen eigenständig. Diese Diegetic Benutzeroberfläche oft weniger als Text-locked Benutzeroberfläche auffindbar sein, damit das Team Asobo clever viele Hinweise, einschließlich virtuellen Zeichen Blicke Richtung, Sound, Licht und Anleitungen (z. B. Pfeil zeigt den Speicherort des den Anhaltspunkt) verwendet, ziehen Sie die Aufmerksamkeit des Benutzers.

![Fragmente - Diegetic UI-Beispiele](images/fragments-game-example-1.jpg)<br>
*Fragmente - Diegetic UI-Beispiele*

### <a name="observations-about-diegetic-ui"></a>Beobachtungen zum Diegetic UI

Räumliche UI (sowohl Text gesperrt und World-locked) und Diegetic Benutzeroberfläche haben eigene Stärken und Schwächen. Ich empfehle Designer, um so viele MR/VR-apps wie möglich zu testen und ihre eigenen verstehen und mit Vernunft nutzen für verschiedene UI, positionieren die Methoden zu entwickeln.

## <a name="the-return-of-skeuomorphism-and-magical-interaction"></a>Die Rückgabe der Skeumorphismus und magische Interaktion

Skeumorphismus, eine digitale Schnittstelle, die die Form der realen Welt Objekte imitiert "uncool" für den letzten 5 bis 7 Jahren in der Branche Entwurf wurde. Wenn Apple schließlich wie Flatfile-Entwurf im iOS 7 zugewiesen haben, erschien es mir, wie Skeumorphismus schließlich als eine Schnittstelle designmethodik inaktiv war. Aber dann ein neues Medium, MR/VR Kopfhörer angekommen ist, auf dem Markt und scheint Skeumorphismus erneut zurückgegeben. : )

### <a name="job-simulator-an-example-of-skeuomorphic-vr-design"></a>Simulator für Auftrag: Ein Beispiel für Skeuomorphic VR-Entwurf

[Auftrag Simulator](http://jobsimulatorgame.com/), ein Spiel frühstückszubereitung entwickelt von [Owlchemy Labs](https://owlchemylabs.com/) ist eine der am häufigsten verwendeten Beispiel Skeuomorphic VR-Entwurf. In diesem Spiel werden der Spieler in Zukunft transportiert, in dem Roboter ersetzen Menschen und Menschen finden Sie auf ein Museum, um was wie das Gefühl, alltägliche Aufgaben in einem der vier verschiedene Aufträge zu erleben: Automatische Mechanikers ergänzen Chef, Store Clerk oder Mitarbeitern im Büro.

Der Vorteil der Skeumorphismus ist eindeutig. Vertraute Umgebung und Objekte innerhalb dieses Spiel können neue VR-Benutzer, die besser vertraut und vorhanden ist, im virtuellen Raum zu fühlen. Es ist auch für sie, wie diese im Steuerelement werden, indem Sie die vertrauten wissen und Verhalten mit Objekten und ihren entsprechenden physischen Reaktionen zuordnen. Z. B. um müssen eine Tasse Kaffee trinken, Benutzer einfach behandelt, auf den Kaffee-Computer, auf eine Schaltfläche klicken, auf den Ziehpunkt Cup und klappen Sie ihn für ihre Mund, wie sie in der Praxis tun würden.

![Auftrags-Simulator](images/job-simulator.gif)<br>
*Auftrags-Simulator*

Da MR/VR immer noch ein Entwicklung von Medium ist, muss mit einem bestimmten Grad der Skeumorphismus Entmystifizieren MR/VR-Technologie und führen Sie es in größeres Publikum auf der ganzen Welt. Mithilfe von Skeumorphismus oder realistische Darstellung kann darüber hinaus für bestimmte Arten von Anwendungen wie oder oder Flight Simulation von Vorteil sein. Da das Ziel dieser Apps zum Entwickeln und Optimieren von Fähigkeiten, die in der realen Welt direkt angewendet werden können ist, werden je näher die Simulation der realen Welt mehr übertragbar ist das wissen.

Denken Sie daran, dass diese Skeumorphismus nur eine Herangehensweise ist. Das Potenzial der MR/VR-Welt ist weit größer ist als und Designer sollten sich bemühen, um magische hyper natürlichen Aktivitäten zu erstellen – neue visueller Hinweise, die in MR/VR-Welt eindeutig möglich sind. Als Ausgangspunkt, erwägen Sie magischen Kräfte auf gewöhnliche Objekte, damit Benutzer auf ihre grundlegenden Wünsche erfüllen können, einschließlich Teleportation und Omniscience.

![(Links) des Doraemon magische Tür und Ruby slippers(right)](images/doraemons-magical-door-and-ruby-slippers.jpg)<br>
*(Links) des Doraemon magische Tür und Ruby slippers(right)*

### <a name="observations-about-skeuomorphism-in-vr"></a>Beobachtungen zum Skeumorphismus in VR

Einfallen lassen von "Überall Gerät" in Doraemon, "Ruby Pantoffel" in-Assistenten von ml "Mauraders Karte" in der Harry Potter, Beispiele für gewöhnliche Objekte mit magische in beliebte Fiction. Diese magischen Objekte helfen Sie uns, eine Verbindung zwischen der Praxis und herausragende Aspekte, zwischen was und was möglicherweise zu visualisieren. Bedenken Sie beim Entwerfen der magische oder surrealistische eine, muss das Objekt ein Gleichgewicht zwischen Funktionen und Unterhaltung. Beachten Sie, dass von der Versuchung, etwas rein magische nur für die Neuheit Willen zu erstellen.

## <a name="understanding-different-input-methods"></a>Grundlegendes zu verschiedenen Eingabemethoden

Wenn ich für die 2D-mittlere vorgesehen, musste ich auf Fingereingabe, Maus und Tastaturinteraktionen für die Eingaben zu konzentrieren. In der MR/VR-Entwurfsbereichs, unser Text wird die Schnittstelle und Benutzer können eine größere Auswahl an Eingabemethoden verwenden: z. B. Spracherkennung, Blicke, Gesten, [6-FG Controller](https://en.wikipedia.org/wiki/Six_degrees_of_freedom), und Handschuhe, der es sich, mehr intuitiv und direkte Verbindung leisten mit virtuellen-Objekten.

![Verfügbaren Eingaben in HoloLens](images/inputs.jpg)<br>
*Verfügbaren Eingaben in HoloLens*

> *"Alles ist etwas besten und schlechtesten für etwas anderes."*<br>
> — [Bill Buxton](https://www.billbuxton.com/)

Z. B. Aktion, die Eingaben mithilfe von bare Hand und Kamerasensoren auf einem Gerät HMD frei Benutzer manuell aus, der Controller enthält oder steht, geteert sweaty Handschuhe, aber häufiger Verwendung kann dazu führen, dass physische Ermüdung (bzw. Gorilla-Arm). Darüber hinaus müssen die Benutzer sich innerhalb der sichtverbindung beibehalten; Wenn die Kamera die Hände nicht angezeigt wird, können die Hände nicht verwendet werden.

Die Spracheingabe ist gut für komplexe Aufgaben durchlaufen, da sie Benutzern über verschachtelte Menüs mit einem Befehl cut ermöglicht (z. B. "Anzeigen der Filme, die von Studio-Laika.") und auch sehr kostengünstige Verbindung mit anderen Modalität (z. B. "Stehen mir" richtet den Befehl das – Hologramm ist ein Benutzer dem Benutzer zugewandt betrachten). Allerdings Spracheingabe funktioniert gut in lauten Umgebung möglicherweise nicht oder kann nicht in einem sehr quiet geeignet.

Neben dem Gestik- und Spracherkennung, verfolgt Handheld Controller (z. B. Oculus touch, Vive usw.) sind sehr beliebte Eingabemethoden, da sie einfach zu bedienendes, präzise und Nutzen von Personen sind [Proprioception](https://en.wikipedia.org/wiki/Proprioception), und geben Sie die passiven Übermitteln von haptischem Hinweise. Gehen jedoch diese Vorteile auf Kosten der nicht in der Lage zu bare praktische und vollständige Finger nachverfolgen.

![Senso (links) und Manus VR(Right)](images/senso-and-manus-vr.jpg)<br>
*Senso (links) und Manus VR (rechts)*

Zwar nicht so beliebt ist als Controller, sind Handschuhe Momentum erneut Dank dem MR/VR-Angebot erhalten. Bis vor kurzem Eingabe des Gehirns/Beachten Sie, wie eine Schnittstelle für virtuelle Umgebungen Schlagkraft zu entwickeln, durch die Integration von EEG oder EMG Sensor Kopfhörer gestartet haben (z. B. [MindMaze VR](http://www.mindmaze.com/)).

### <a name="observations-about-input-methods"></a>Beobachtungen zum Eingabemethoden

Hierbei handelt es sich nur ein Beispiel für Eingabe Geräte, die auf dem Markt für MR/VR verfügbar. Sie werden weiterhin angelegt wird, bis die Branche Reife und die einigt sich über bewährte Methoden. Bis dahin sollte Designer Achten Sie darauf, dass Sie der neuen Eingabegeräte und werden Kenntnisse in die Eingabe für spezifischen Methoden für die betreffende Projekt. Designer müssen für kreative Lösungen innerhalb der Einschränkungen beim Spielen auch auf ein Gerät die Stärken suchen.

## <a name="sketch-the-scene-and-test-in-the-headset"></a>Skizzieren Sie der Szene, und Testen Sie in den Kopfhörer

Wenn ich in 2D gearbeitet, skizziert ich größtenteils nur den Inhalt. Allerdings in mixed Reality-Speicherplatz, die nicht ausreichend war. Ich musste skizzieren, die gesamte Szene die Beziehungen zwischen Benutzer und virtuelle Objekte besser vorstellen. Um meine räumliche zur Verfügung stellen, ich gestartet, um Szenen skizzieren [Kino 4D](https://www.maxon.net/en/products/cinema-4d/overview/) und manchmal auch erstellen einfache Ressourcen zum Erstellen von Prototypen in [Maya](http://www.autodesk.com/products/maya/overview/). Ich hatte nie Programme verwendet, vor dem Eintritt in das Team HoloLens und bin ich immer noch eine steige gerade, aber arbeiten mit diesen Programmen 3D auf jeden Fall half mir, mit der neuen Terminologie vertraut wie z. B. [Shader](https://en.wikipedia.org/wiki/Shader) und [IK (Inverse Kinematik)](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-07C3BA47-32BB-477B-B6C5-1090E5C9B81C-htm.html/).

**"Unabhängig davon, wie genau sich die Szene in 3D ich skizziert, war der tatsächlichen Erfahrungen beim Kopfhörer fast nie die Skizze identisch. Daher es ist wichtig, testen die Szene in der Headsets. "– Hae Jin Lee**

Für HoloLens prototyperstellung, ich habe Sie alle Tutorials auf versucht [Mixed Reality-Tutorials](tutorials.md) zu starten. Und ich begann, mit Spielen [HoloToolkit.Unity](https://github.com/Microsoft/HoloToolkit-Unity/) , dass Microsoft für Entwickler zur Beschleunigung der Entwicklung von holographic Anwendungen bereitstellt. Wenn ich etwas unterbrochen wurde, ich habe meine Frage [HoloLens Frage und Antwort-Forum](https://forums.hololens.com/categories/questions-and-answers/).

Nach dem Erwerb von grundlegende Kenntnisse zum Erstellen von Prototypen HoloLens, wollte ich andere nicht-Programmierer Prototyp selbstständig zu ermöglichen. Daher habe ich ein video Lernprogramm, wie Sie eine einfache Projektil mit HoloLens entwickeln vorgenommen. Ich kurz die Grundbegriffe erläutern, selbst wenn Sie keine Erfahrung bei der Entwicklung für HoloLens haben, Sie folgen können.

<br>

>[!VIDEO https://www.youtube.com/embed/58612RT2CT8]
*Mir dieses einfachen Tutorials für Programmierer wie mir.*

Zum Erstellen von Prototypen VR, habe ich Kurse zur [VR-Dev "School"](http://learn.vrdev.school/) und auch dauerte [3D Inhaltserstellung für virtuelle Realität](https://www.lynda.com/Unreal-Engine-tutorials/3D-Content-Creation-Virtual-Reality/482055-2.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3aVirtual+Reality+%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2/) lynda.com. VR-Dev "School" wird angegeben, dass weitere in fundierten Kenntnisse bei der Codierung und den Kurs Lynda mir eine schöne kurze Einführung für das Erstellen von Ressourcen für VR angeboten.

## <a name="take-the-leap"></a>Nutzen Sie den Sprung

Vor einem Jahr, halte ich, wie all dies war ein wenig überwältigend. Kann ich Sie darüber informieren, dass es sich um 100 % der Mühe Wert war. MR/VR ist immer noch sehr jung Mittel, und es gibt so viele interessante Möglichkeiten, die darauf warten, realisiert werden. Meiner Meinung nach inspirieren und Glück einen kleinen Teil beim Entwerfen der Zukunft wiedergegeben werden. Ich hoffe, dass Sie mir auf dem Weg in 3D-Raum hinzugefügt werden.

## <a name="about-the-author"></a>Der Autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Hae Jin Lee" width="60" height="60" src="images/haejinlee.jpg"></td>
<td style="border-style: none"><b>Hae Jin Lee</b><br>UX-Designer @Microsoft</td>
</tr>
</table>

 
