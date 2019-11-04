---
title: Fallstudie-holotour
description: Holotour für Microsoft hololens bietet immersive persönliche 3D-Touren von berühmten Standorten auf der ganzen Welt. Diese Fallstudie führt Sie durch den Prozess des Erstellens und Erstellens der Inhalte, die für holotour verwendet werden.
author: DannyAskew
ms.author: daaske
ms.date: 03/21/2018
ms.topic: article
keywords: Holotour, hololens, Windows Mixed Reality
ms.openlocfilehash: 035bec9b0d46a31978bc91f23bfb3a5ee47d6247
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436927"
---
# <a name="case-study---holotour"></a>Fallstudie-holotour

Holotour für Microsoft hololens bietet immersive persönliche 3D-Touren von berühmten Standorten auf der ganzen Welt. Wie Designer, Entwickler, Producer, audiodesigner und Entwickler, die an diesem Projekt arbeiten, haben Sie herausgefunden. das Erstellen eines überzeugender realen 3D-Renderings eines bekannten Standorts ist eine einzigartige Mischung aus Creative und Logical Wizardry. Diese Fallstudie führt Sie durch den Prozess des Erstellens und Erstellens der Inhalte, die für holotour verwendet werden.

## <a name="the-tech"></a>Die Technologie

Mit holotour wollten wir es den Benutzern ermöglichen, einige der weltweit größten Ziele zu besuchen – wie etwa die [Ruinen von Machu Picchu](https://en.wikipedia.org/wiki/Machu_Picchu) in Peru oder den modernen Tag [Piazza Navona](https://en.wikipedia.org/wiki/Piazza_Navona) in Italien – direkt von ihren eigenen Wohnräumen. Unser Team hat das Ziel von holotour gemacht, um Ihnen die Meinung zu vermitteln, dass Sie wirklich da sind. Die mehr als nur Bilder oder Videos benötigte Leistung. Durch die Nutzung der eindeutigen Anzeige, Nachverfolgung und Audiotechnologie von hololens haben wir angenommen, dass wir Sie praktisch an einen anderen Ort transportieren können. Wir müssen die Sehenswürdigkeiten, Sounds und dreidimensionalen Geometrie aller besuchten Orte erfassen und diese dann in unserer APP neu erstellen.

Um dies zu erreichen, benötigen wir ein 360 °-Kamera-Rig mit direktionaler Audioerfassung. Die Erfassung musste bei äußerst hoher Auflösung durchgeführt werden, sodass das Material bei der Wiedergabe auf einem hololens knackig aussehen würde und die Kameras nah beieinander positioniert werden müssen, um das Zusammenfügen von Artefakten zu minimieren. Wir wollten eine vollständige sphärischen Abdeckung, nicht nur am Horizont, sondern auch über und unter Ihnen. Das Rig musste auch portabel sein, damit wir es auf der ganzen Welt nutzen konnten. Wir haben die verfügbaren Optionen für "offshelf" ausgewertet und erkannt, dass Sie einfach nicht gut genug waren, um unsere Vision zu verwirklichen – entweder aufgrund von Auflösung, Kosten oder Größe. Wenn wir ein Kamera-Rig nicht gefunden haben, das unsere Anforderungen erfüllt, müssten wir eine selbst erstellen.

### <a name="building-the-rig"></a>Aufbauen des Riggs

Die erste Version –, die aus dem Karton, Velcro, dem Kanalband und 14-GoPro-Kameras stammt – war etwas, das MacGyver als stolz war. Nach der Überprüfung sämtlicher Lösungen von Low-End-Lösungen bis hin zu benutzerdefinierten Anlagen waren GoPro-Kameras letztendlich die beste Option für uns, da Sie klein und kostengünstig waren und einen leicht zu verwendenden Speicherplatz hatten. Der kleine Formfaktor war besonders wichtig, da es uns ermöglichte, Kameras relativ nah zu platzieren – die geringere Entfernung zwischen den Kameras, desto kleiner die zusammen fügenden Artefakte. Dank unserer einzigartigen Kamera Anordnung konnten wir vollständige Kugel *Abdeckung und* genug Überlappungen erzielen, um Kameras Intelligent auszurichten und einige Artefakte während des zusammenfassende Vorgangs zu glätten.

Die Verwendung der [räumlichen](spatial-sound.md) Audiofunktionen in hololens ist entscheidend für die Erstellung einer überzeugenden, immersiven Darstellung. Wir haben ein vier-Mikrofon-Array unter den Kameras auf dem Stativ verwendet, das in vier Richtungen Sound von der Kamera aufzeichnen würde, sodass wir ausreichend Informationen zur Erstellung räumlicher Sounds in unseren Kulissen erhalten.

![Unser 360 °-Kamera-Rig ist für das Drehen außerhalb des Pantheon eingerichtet.](images/camera-pantheon-200px.png)

Unser 360 °-Kamera-Rig ist für das Drehen außerhalb des Pantheon eingerichtet. 


Wir testen unser hausgemachtes Rig, indem wir es in den Rattlesnake-Grat in der Nähe von Seattle übernommen und die Kulissen am Anfang der Wanderung erfasst haben. Das Ergebnis, obwohl es deutlich weniger hoch ist als die Orte, die Sie heute in holotour sehen, gab uns Vertrauen, dass unser Rig-Design gut genug war, um Ihnen das Gefühl zu geben, dass Sie wirklich da sind.

Wir haben unser rig von Velcro und Pappe auf einen 3D-gedruckten Kamera-Gehäuse aktualisiert und externe Akku Pakete für die GoPro-Kameras gekauft, um die Akku Verwaltung zu vereinfachen. Wir haben dann einen umfassenderen Test durchgeführt, um zu San Francisco zu gehen und eine Miniatur Tour durch die Stadt und die legendäre Golden Gate Bridge zu erstellen. Dieses Kamera-Rig ist das, was wir für die meisten unserer Erfassungen der Standorte, die Sie in holotour besucht haben, verwendet haben.

![Die 360 °-Kamera-Rig-Verfilmung in Machu Picchu.](images/camera-machu-pichu-500px.png)

Die 360 °-Kamera-Rig-Verfilmung in Machu Picchu. 

## <a name="behind-the-scenes"></a>Im Hintergrund

Vor dem Filmen mussten wir herausfinden, welche Standorte wir in unsere virtuelle Tour einschließen wollten. Rom war der erste Ort, der ausgeliefert werden soll, und wir wollten ihn richtig machen, also haben wir uns entschlossen, eine pfadtour durchzuführen. Wir haben ein Team von sechs Personen – einschließlich Künstlern, Designern und Producer – an die Websites gesendet, die wir in Erwägung gezogen haben. Die Fahrt hat ungefähr 9 Tage gedauert – 2,5 für Reisen, den Rest für die-Verfilmung. (Bei Machu Picchu haben wir uns entschieden, einen Scout-Trip durchzuführen, im Voraus zu forschen und einige Tage Puffer für das Filmen zu reservieren.)

In Rom nahm das Team Fotos der einzelnen Bereiche auf und gab interessante Fakten sowie praktische Überlegungen aus, z. b. wie schwierig es ist, zu jedem Ort zu reisen und wie schwierig es ist, aufgrund von Menschen oder Einschränkungen zu filtern. Dies mag in einem Urlaub klingen, aber es ist viel Arbeit. Tage, die früh am Morgen gestartet werden und bis Abend nicht angehalten werden. Jede Nacht wurde das Buch für das Team in Seattle hochgeladen, um es zu überprüfen. 

![Unsere Erfassungs Besatzung in Rom.](images/holotour-filming-crew-rome-500px.jpg) 

Unsere Erfassungs Besatzung in Rom. 


Nachdem der Scout-Trip abgeschlossen wurde, wurde für das eigentliche drehen ein endgültiger Plan erstellt. Dies erforderte eine detaillierte Liste, in der wir an dem Tag und zu dem Zeitpunkt, an dem wir uns befanden, eine detaillierte Liste der Filme aufging Jeden Tag ist das Ausland teuer, sodass diese Fahrten effizient sein müssen. Wir haben Handbücher und Handler in Rom gebucht, um uns zu helfen und jeden Tag von vor dem Sonnenaufgang bis nach dem Sonnenuntergang vollständig zu nutzen. Wir müssen das beste Material erzielen, damit Sie das Gefühl haben, dass Sie wirklich da sind.

### <a name="capturing-the-video"></a>Erfassen des Videos

Das Ausführen einiger einfacher Dinge während der Erfassung kann die Nachbearbeitung erheblich vereinfachen. Wenn Sie z. b. Bilder von mehreren Kameras zusammenfügen, erhalten Sie visuelle Artefakte, da jede Kamera eine etwas andere Ansicht hat. Je näher die Objekte der Kamera sind, desto größer ist der Unterschied zwischen den Ansichten und desto größer die zusammen fügenden Artefakte. Hier ist eine einfache Möglichkeit, das Problem visuell darzustellen: halten Sie Ihren Ziehpunkt vor dem Gesicht, und betrachten Sie ihn nur mit einem Auge. Wechseln Sie jetzt zu Augen. Sie werden feststellen, dass der Ziehpunkt relativ zum Hintergrund bewegt wird. Wenn Sie Ihren Ziehpunkt nicht mehr von Ihrem Gesicht halten und das Experiment wiederholen, scheint Ihr Thumb-Steuer Vorgang weniger zu verschieben. Diese sichtbare Bewegung ähnelt dem Problem, das wir mit der zusammen Fügung konfrontiert haben: Ihre Augen sehen, wie die Kameras, nicht genau dasselbe Bild, da Sie durch eine kleine Entfernung voneinander getrennt sind.

Da es viel einfacher ist, die schlechtesten Artefakte während der Verfilmung zu vermeiden, als Sie bei der Nachbearbeitung zu korrigieren, haben wir versucht, Personen und Dinge weit weg von der Kamera zu halten. Eine große Herausforderung im Zusammenhang mit der Kamera war wahrscheinlich eine der größten Herausforderungen, die bei der Ausführung aufgetreten sind, und wir mussten kreativ werden, damit Sie funktionieren. Das Arbeiten mit lokalen Handbüchern war eine große Hilfe bei der Verwaltung von Menschen, aber wir stellten auch fest, dass die Verwendung von Vorzeichen – und manchmal kleine Kegel oder Bohnen Behälter – zum Markieren des drehraums Recht effektiv war, insbesondere, da wir nur eine kurze Menge von Material an jedem Ort erhalten mussten. Häufig ist die beste Möglichkeit, eine gute Erfassung zu erzielen, nur sehr früh am Morgen zu erreichen, bevor die meisten Benutzer angezeigt werden.

Einige andere nützliche Erfassungs Techniken stammen direkt von herkömmlichen filmpraktiken. Wir haben z. b. eine Farbkorrektur Karte für alle unsere Kameras verwendet und Referenz Fotos von Texturen und Objekten aufgezeichnet, die wir möglicherweise später benötigen. 

![Eine grobe Kürzung von Machu Picchu, die die Farbkorrektur Karte anzeigt.](images/rough-cut-machu-picchu-500px.png)

Eine grobe Ausschneide von Pantheon-Footage vor dem zusammenfügen.

### <a name="processing-the-video"></a>Verarbeiten des Videos

Die Erfassung von 360 °-Inhalten ist nur der erste Schritt – eine Menge an Verarbeitung ist erforderlich, um die von uns erfassten Rohdaten der Kamera in die endgültigen Ressourcen zu konvertieren, die in holotour angezeigt werden. Nachdem wir wieder Home waren, mussten wir das Video aus 14 verschiedenen Kamera Feeds nehmen und in ein einzelnes kontinuierliches Video mit minimalen Artefakten umwandeln. Unser Kunst Team hat eine Reihe von Tools verwendet, um das erfasste Material zu kombinieren und zu polieren. Wir haben eine Pipeline entwickelt, um die Verarbeitung so weit wie möglich zu optimieren. Das Material muss zusammengefügt, farblich korrigiert und dann zusammengesetzt werden, um ablenkend Ende Elemente und Artefakte zu entfernen oder zusätzliche Taschen zu leben und Bewegung hinzuzufügen. das Ziel ist, dieses Gefühl zu verbessern, das tatsächlich vorhanden ist.

![Eine grobe Ausschneide von Pantheon-Footage vor dem zusammenfügen.](images/rough-cut-pantheon-500px.png)

Eine grobe Ausschneide von Pantheon-Footage vor dem zusammenfügen. 


Um die Videos zusammenzufassen, haben wir ein Tool namens [PTGui](https://www.ptgui.com/) verwendet und in unsere Verarbeitungs Pipeline integriert. Im Rahmen der Nachbearbeitung haben wir weiterhin Frames aus unseren Videos extrahiert und ein Muster gefunden, das für einen dieser Frames gut aussieht. Anschließend haben wir dieses Muster auf ein benutzerdefiniertes Plug-in angewendet, das wir geschrieben haben, das es unseren Videokünstlern ermöglichte, das Kontext Muster direkt zu optimieren 

![Screenshot der PTGui, die das angeheftete Pantheon-Material anzeigt.](images/stitching-tool-pantheon-500px.png)

Screenshot der PTGui, die das angeheftete Pantheon-Material anzeigt. 


### <a name="video-playback"></a>Videowiedergabe

Nachdem die Verarbeitung des Materials abgeschlossen ist, haben wir ein nahtloses Video, aber es ist eine außerordentlich große –-Auflösung von 8 KB. Das Decodieren von Videos ist aufwendig, und es gibt nur wenige Computer, auf denen ein 8K-Video verarbeitet werden kann. die nächste Herausforderung war, das Video auf hololens wiederzugeben. Wir haben eine Reihe von Strategien entwickelt, um die Kosten für das Decodieren zu vermeiden, während der Benutzer die Meinung hat, dass er das gesamte Video anzeigen würde.

Die einfachste Optimierung besteht darin, die Decodierung von Teilen des Videos zu vermeiden, die sich nicht wesentlich ändern. Wir haben ein Tool geschrieben, mit dem Bereiche in jeder Szene identifiziert werden, die nur wenig oder gar keine Bewegung haben. Für diese Regionen wird ein statisches Bild angezeigt, anstatt ein Video für jeden Frame zu decodieren. Um dies zu ermöglichen, haben wir das riesige Video in wesentlich kleinere Blöcke aufgeteilt.

Wir haben außerdem sichergestellt, dass jedes Pixel, das wir decodiert haben, am effektivsten verwendet wurde. Wir haben mit Komprimierungs Techniken experimentieren, um die Größe des Videos zu verringern. die Video Bereiche werden entsprechend den Polygonen der Geometrie aufgeteilt, auf die Sie projiziert wird. Wir haben UVS angepasst und die Videos basierend auf der Detailgenauigkeit verschiedener Polygone neu verpackt. Das Ergebnis dieser Aufgabe ist, dass ein einzelnes KB-Video in viele Blöcke integriert wurde, die fast unverständlich aussehen, bis Sie ordnungsgemäß in die Szene projiziert werden. Für einen Spielentwickler, der die Textur Zuordnung und die UV-Verpackung versteht, wird dies wahrscheinlich auch bekannt sein. 

![Eine vollständige Ansicht des Pantheon vor Optimierungen.](images/pantheon-before-optimization-500px.png) 

Eine vollständige Ansicht des Pantheon vor Optimierungen. 


![Die Rechte Hälfte des Pantheon, die für die Videowiedergabe verarbeitet wird.](images/pantheon-process-video-playback-500px.png) 

Die Rechte Hälfte des Pantheon, die für die Videowiedergabe verarbeitet wird. 


![Beispiel für einen einzelnen Videobereich nach Optimierung und Verpackung.](images/single-video-region-after-optimization-500px.png) 

Beispiel für einen einzelnen Videobereich nach Optimierung und Verpackung. 


Ein weiterer Trick wurde verwendet, um das Decodieren von Videos zu vermeiden, die Sie nicht aktiv anzeigen In holotour sehen Sie nur einen Teil der vollständigen Szene. Wir decodieren nur Videos innerhalb oder kurz außerhalb ihrer Ansicht (Field of View, FOV). Wenn Sie Ihre Kopfzeile drehen, beginnen wir mit der Wiedergabe der Bereiche des Videos, die sich nun in Ihrem FOV befinden, und spielen nicht mehr, wenn Sie sich nicht mehr in der Hand befinden. Die meisten Leute bemerken dies nicht, aber wenn Sie sich schnell umdrehen, sehen Sie, dass das Video ein zweites Mal beginnt – in der Zwischenzeit wird ein statisches Bild angezeigt, das dann wieder auf das Video zurückkehrt, sobald es bereit ist.

Damit diese Strategie funktioniert, haben wir ein umfassendes Videowiedergabe System entwickelt. Wir haben den Wiedergabe Code auf niedriger Ebene optimiert, um den Video Wechsel extrem effizient zu gestalten. Außerdem mussten wir unsere Videos auf besondere Weise codieren, um die schnelle Umstellung auf jedes Video zu ermöglichen. Diese Wiedergabe Pipeline hat eine beträchtliche Menge an Entwicklungszeit benötigt, sodass wir Sie in Phasen implementiert haben. Wir haben mit einem einfacheren System begonnen, das weniger effizient war, aber Entwicklern und Künstlern ermöglichte, an der Arbeit zu arbeiten und Sie langsam in ein stabileres Wiedergabe System zu verbessern, das es uns ermöglichte, an der abschließenden Qualitäts Leiste zu liefern. Dieses endgültige System verfügte über benutzerdefinierte Tools, die wir in Unity erstellt haben, um das Video in der Szene einzurichten und die Wiedergabe-Engine zu überwachen.

### <a name="recreating-near-space-objects-in-3d"></a>Neuerstellen von Near-Space-Objekten in 3D

Videos bilden die Mehrzahl der Elemente, die in holotour angezeigt werden, aber es gibt eine Reihe von 3D-Objekten, die in Ihrer Nähe angezeigt werden, wie z. b. das Zeichnen in der Piazza Navona, den springenden Bereich außerhalb des Pantheon oder die heiße Luft Sprechblase, die Sie für Luft Szenen nutzen. Diese 3D-Objekte sind wichtig, da die Wahrnehmung der Menschen Tiefe sehr gut ist, aber noch nicht sehr gut ist. Wir können uns das Video in der Entfernung ansehen, aber um den Benutzern zu ermöglichen, ihren Platz zu durchlaufen und sich zu fühlen, benötigen nahe gelegene Objekte Tiefe. Diese Vorgehensweise ähnelt der Vorgehensweise, die Sie in einem Natural History-Museum sehen können – Bild eines Diorama, das physische Landschaft, Werke und tierische Proben im Vordergrund enthält, aber zu einem clever maskierten Matt-zeichnen im Hintergrund.

Einige Objekte sind einfach 3D-Ressourcen, die wir erstellt und der Szene hinzugefügt haben, um die Leistung zu verbessern. Das Zeichnen und der Hot Air-Sprechblase fallen in diese Kategorie, da Sie nicht vorhanden waren, als wir gedreht haben. Ähnlich wie bei Game-Assets wurden Sie von einem 3D-Experten in unserem Team erstellt und entsprechend angepasst. Wir platzieren diese in den Kulissen, in denen Sie sich befinden, und die Spiel-Engine kann Sie in den beiden hololens-anzeigen, sodass Sie als 3D-Objekt angezeigt werden.

Andere Assets, wie z. b. der Spring-Brunnen außerhalb des Pantheon, sind echte Objekte, die an den Standorten vorhanden sind, an denen wir Videoaufnahmen, aber um diese Objekte aus dem Video und 3D zu bringen, müssen wir eine Reihe von Dingen durchführen.

Zuerst benötigen wir weitere Informationen zu jedem Objekt. Am Speicherort für die Film Erstellung hat unser Team viele Verweise auf diese Objekte aufgezeichnet, damit wir über ausreichend ausführliche Bilder verfügen, um die Texturen genau neu erstellen zu können. Das Team hat außerdem einen [Photogrammetrie](https://en.wikipedia.org/wiki/Photogrammetry) -Scan durchgeführt, bei dem ein 3D-Modell aus Dutzenden von 2D-Images erstellt wird, was uns ein grobes Modell des Objekts in perfekter Größe bietet.

Wenn wir unser Material verarbeiten, werden Objekte, die später durch eine 3D-Darstellung ersetzt werden, aus dem Video entfernt. Das 3D-Asset basiert auf dem photogrammmetrikmodell, wurde aber bereinigt und von unseren Künstlern vereinfacht. Für einige Objekte können wir Teile des Videos verwenden – wie z. b. die Wasser Textur auf dem Springbrunnen – aber der größte Teil des Brunnens ist jetzt ein 3D-Objekt, das es Benutzern ermöglicht, Tiefe zu erkennen und Sie in einem begrenzten Bereich in der Umgebung zu durchlaufen. Das vorhanden sein von fast-Space-Objekten wie diesem erhöht den Sinn von Realismus und hilft dabei, die Benutzer am virtuellen Speicherort zu durchführen. 

![Pantheon-Material mit dem entfernten Brunnen. Sie wird durch ein 3D-Medienobjekt ersetzt.](images/object-removal-pantheon-500px.png)

Pantheon-Material mit dem entfernten Brunnen. Sie wird durch ein 3D-Medienobjekt ersetzt.


## <a name="final-thoughts"></a>Abschließende Gedanken

Natürlich gab es noch mehr zum Erstellen dieses Inhalts als das, was wir hier besprochen haben. Es gibt ein paar Szenen – wir möchten Sie als "unmögliche Perspektiven" bezeichnen – einschließlich der heiß Luft Sprechblase und des gladiatorkampfes im Kolosseum, der einen kreativeren Ansatz hat. Diese werden in einer zukünftigen Fallstudie behandelt.

Wir hoffen, dass die gemeinsame Nutzung von Lösungen für einige der größeren Herausforderungen, die wir während der Produktion hatten, für andere Entwickler hilfreich ist und Sie darauf aufmerksam sind, dass Sie einige dieser Techniken verwenden, um Ihre eigenen immersiven Erfahrungen für hololens zu entwickeln. (Wenn Sie dies tun, stellen Sie sicher, dass Sie es für uns im [hololens-App-Entwicklungsforum](https://forums.hololens.com/)freigeben!)

## <a name="about-the-authors"></a>Informationen zu den Autoren

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="David Haley" width="60" height="60" src="images/haley.png" /></td>
<td style="border:0" width="408"> <b>David Haley</b> ist leitender Entwickler, der mehr über Kamera-und Videowiedergabe erfahren hat, als er von der Arbeit an holotour war.</td>
<td style="border:0" width="60px"> <img alt="Danny Askew" width="60" height="60" src="images/askew.png" /></td>
<td style="border:0" width="408"> <b>Danny Askew</b> ist ein Video, das sichergestellt hat, dass Ihre Reise durch Rom so tadellos wie möglich war.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Jason Syltebo" width="60" height="60" src="images/syltebo.png" /></td>
<td style="border:0" width="408"> <b>Jason syltebo</b> ist ein audiodesigner, der sicherstellt, dass Sie die Sound Landschaft jedes besuchten Ziels sehen können, auch wenn Sie zurückkehren.</td>
<td style="border:0" width="60px"> <img alt="Travis Steiner" width="60" height="60" src="images/steiner.png" /></td>
<td style="border:0" width="408"> <b>Travis Steiner</b> ist ein Entwurfs Leiter, der Standorte erforscht und durchsucht, Reisepläne erstellt und eine Weiterleitung auf der Website durchgeführt hat.</td>
</tr>
</table>



## <a name="see-also"></a>Weitere Informationen:
* [Video: Microsoft hololens: holotour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
