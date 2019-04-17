---
title: 'Fallstudie: erfassen und Inhalte für HoloTour erstellen'
description: HoloTour für Microsoft HoloLens enthält faszinierende 3D persönliche Touren iconic Speicherorte auf der ganzen Welt.
author: DannyAskew
ms.author: daaske
ms.date: 03/21/2018
ms.topic: article
keywords: HoloTour, HoloLens, Windows Mixed Reality
ms.openlocfilehash: 6c9e5f44c439310883c8b0271187a7b2263b0854
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593280"
---
# <a name="case-study---capturing-and-creating-content-for-holotour"></a>Fallstudie: erfassen und Inhalte für HoloTour erstellen

HoloTour für Microsoft HoloLens enthält faszinierende 3D persönliche Touren iconic Speicherorte auf der ganzen Welt. Als der Designer, Künstler, Producer, audio-Designer und Entwickler arbeiten an diesem Projekt finden Sie heraus dauert das Erstellen einer echten convincingly 3D-Rendering von einem bekannten Speicherort eine einzigartige Mischung creative und technologische geschickten Umgang aus.

## <a name="the-tech"></a>Der Technologie

Mit HoloTour, wir wollten und es für Benutzer finden Sie einige der weltweit einzigartig Ziele auf, wie die [Ruinen von am Machu Picchu](https://en.wikipedia.org/wiki/Machu_Picchu) Peru oder den modernen [Piazza Navona](https://en.wikipedia.org/wiki/Piazza_Navona) in Italien – direkt aus eigene Wohnzimmer. Unser Team war es das Ziel der HoloTour "Stellen Sie, wie Sie tatsächlich vorhanden sind." Die Erfahrung, die mehr als nur Bilder oder Videos werden musste. Durch die Nutzung der eindeutigen Anzeigenamen, nachverfolgung und audio-Technologie von HoloLens davon ausgegangen, dass wir Sie praktisch an einem anderen Ort übertragen kann. Müssen wir erfassen, der sich, Sounds und dreidimensionalen Geometrie mit allen Stellen wir besucht und neu erstellen, die in unserer app.

Zu diesem Zweck, die wir brauchten einer 360 ° Kamera mit direktionalen audioerfassung Lichtanlage. Es musste es mit äußerst hohen Auflösung erfassen, damit die Bearbeitung sieht bei der Wiedergabe auf einem HoloLens schärfer und die Kameras müssten sich nah beieinander positioniert werden soll, um die Verknüpfung Artefakte zu minimieren. Wir wollten es sich um vollständige sphärischen Coverage, nicht nur auf den Horizont, jedoch oberhalb und unterhalb Sie ebenfalls. Das Rig musste außerdem portabel sein, sodass wir sie auf der ganzen Welt nutzen können. Optionen für die Standardanwendungen ausgewertet, und wir erkannte, dass sie einfach nicht gut genug, um unsere Vision – entweder aufgrund der Kosten, Größe und Auflösung umzusetzen waren. Wenn wir eine Kamera Rig nicht, der unsere Anforderungen erfüllt finden konnte, müssten wir ein selbst erstellen.

### <a name="building-the-rig"></a>Erstellen das rig

Die erste Version – getätigte cardboard vereinfacht, Velcro verwenden, Band und 14 GoPro Kameras Rohrleitung – war MacGyver stolz hätte. Nach der Überprüfung von Low-End-Lösungen, um benutzerdefinierte produzierten Rigs bis hin waren GoPro Kameras letztlich die beste Option für uns, da sie kleine, kostengünstige wurden und einfach zu bedienende Speicher haben. Die kleinen Formfaktor war besonders wichtig, da es uns Kameras relativ nah beieinander platziert zulässig – je kleiner die Entfernung zwischen Kameras je kleiner die Verknüpfung sein werden. Unsere eindeutige Kamera Anordnung ermöglichte vollständige Kugel Coverage zu erreichen *plus* genügend Überlappung auf intelligente Weise ausrichten Kameras und einige Elemente bei der Verknüpfung glätten.

Nutzen der [räumliche Sound](spatial-sound.md) Funktionen für HoloLens ist von entscheidender Bedeutung für das Erstellen einer echten convincingly eintauchen. Verwendet eine vier-Mikrofon Array liegen unterhalb der Kameras auf dem Stativ, denen Sounds über den Speicherort der unsere Kamera in unterschiedliche Richtungen erfasst wird, gewähren uns genügend Informationen zum Erstellen der räumlichen Sounds in unserer Szenen.

![Richten Sie unsere 360° Kamera Rig für außerhalb der Pantheon Filmen.](images/camera-pantheon-200px.png)

Richten Sie unsere 360° Kamera Rig für außerhalb der Pantheon Filmen. 


Wir testeten die unsere Möglichkeit Rig von dauert es bis zu Rattlesnake Ridge in der Nähe von Seattle und der Landschaften am oberen Rand der Wanderung erfassen. Das Ergebnis, gibt aber deutlich kleiner als die Speicherorte optimierte, die Sie heute in HoloTour sehen uns vertrauen, die unser Rig Entwurf gut genug war, um müssen Sie sich fühlen, als würden Sie tatsächlich vorhanden sind.

Wir unsere Rig Velcro und Cardboard auf eine Kamera 3D gedruckt wohnkosten aktualisiert und externen Akku Packs für die GoPro Kameras zur Vereinfachung der Verwaltung der Akku gekauft. Wir haben dann eine ausführlichere Prüfung, Reisen nach San Francisco, um eine Art Miniatur Überblick der Stadt Coast und die iconic Golden Gate-Brücke zu erstellen. Diese Kamera-Rig ist, was wir für die meisten unserer erfasst der Speicherorte verwendet wird, die Sie in HoloTour besuchen.

![Die 360°-Kamera-Rig in am Machu Picchu Filmen.](images/camera-machu-pichu-500px.png)

Die 360°-Kamera-Rig in am Machu Picchu Filmen. 


## <a name="behind-the-scenes"></a>Im Hintergrund

Vor dem Filmen mussten wir ermitteln, welche, die Standorte wir auf unserem virtuellen Tour einschließen möchten. "ROME" wurde die erste Position, die wir liefern soll, und wir beginnen sie, damit wir uns entschieden, eine Reise Scouting im Voraus zu tun möchten. Wir haben ein Team von sechs Personen gesendet – einschließlich Künstler, Designer und Producer – für eine vor-Ort-Besuch auf die Websites, die wir waren in Betracht ziehen. Die Reise dauerte ungefähr 9 Tage – 2.5 für Reisekosten, den Rest für Filmen. (Am Machu Picchu abonniert wir nicht dazu eine Fahrt Scout im Voraus untersucht, und ein paar Tage des Puffers für den Filmen Buchung.)

In "ROME", das Team hat Fotos von jedem Bereich und notiert haben, interessante Fakten sowie praktische Überlegungen, wie z. B., wie schwierig es ist an jeder Stelle, und wie schwierig übertragen wäre es, Film aufgrund einer oder Einschränkungen. Das klingt wie Urlaub, aber es ist sehr viel Arbeit. Tage frühen morgen in die Schritte und fiel ununterbrochenen bis abends. Jede Nacht, hochgeladen wurde die Bearbeitung für das Team in Seattle, um zu überprüfen. 

![Unsere Erfassung Besatzung im ROM.](images/holotour-filming-crew-rome-500px.jpg) 

Unsere Erfassung Besatzung im ROM. 


Nachdem die Scout-Fahrt abgeschlossen wurde, wurde ein endgültigen Plan für die tatsächliche Filmen vorgenommen. Dies erforderlich, eine detaillierte Liste der, in denen auf Film, an welchem Tag und zu welchem Zeitpunkt wir würden. Jeden Tag im Ausland ist aufwändig, damit diese Roundtrips erforderlich sind, effizient sein. Gebuchte Anleitungen und Handler in "ROME", um uns zu unterstützen, und wir täglich von vor Sonnenaufgang, nach dem Sonnenuntergang vollständig verwendet. Wir benötigen am besten geeignete Filmmaterial möglich, um müssen Sie sich fühlen, als würden Sie tatsächlich vorhanden sind.

### <a name="capturing-the-video"></a>Das Video aufzeichnen

Einige einfache Dinge zu tun, während der Aufzeichnung kann nach der Verarbeitung deutlich vereinfachen. Z. B. Wenn Sie Bilder aus mehreren Kameras zusammenzufügen, erhalten Sie mit visuellen Artefakten, da jede Kamera eine etwas andere Sicht hat. Die genauere Objekte sind bis zur Kamera, je größer der Unterschied zwischen den Ansichten, und je größer die Verknüpfung sein werden. Hier ist eine einfache Möglichkeit, um das Problem zu visualisieren: vor dem Zifferblatt Ihrer Thumb-Steuerelement enthält und mit nur einem Auge betrachten. Wechseln Sie nun die Augen. Sie sehen, dass Ihre Thumb-Steuerelement angezeigt wird, relativ zum Hintergrund zu verschieben. Wenn Sie dem Daumen weiter weg von dem Zifferblatt Ihrer enthalten, und wiederholen Sie das Experiment, erscheint dem Daumen kleiner zu verschieben. Das offensichtlich, dass die Bewegung auf die Verknüpfung Problem ähnelt treffen wir: Ihre Augen, wie unsere Kameras, genaue das gleiche Abbild nicht angezeigt werden, da sie mit etwas Abstand voneinander getrennt sind.

Da es viel einfacher ist, zu verhindern, dass die schlechteste Artefakte beim Filmen, statt sie nach der Verarbeitung zu korrigieren, haben wir zu Personen und Aufgaben weit entfernt von der Kamera in der Hoffnung, dass wir die Notwendigkeit, vergrößerte Objekte zusammenfügen beseitigen kann versucht werden. Warten eine große löschen, um unsere Kamera war wahrscheinlich eine der größten Herausforderungen, die wir während der Aufnahme und werden musste, um die dafür erforderlichen kreativ werden. War die Arbeit mit lokalen Anleitungen eine große Hilfe bei der Verwaltung einer, aber wir haben auch festgestellt, dass mit signiert, und in einigen Fällen kleine Kegel oder Bean kontextbehälter – Ihren filming Bereich markieren einigermaßen gültig war, besonders, da wir nur erforderlich, um die Bearbeitung eines kurzen Zeitraums an jedem Standort erhalten. Häufig war die beste Möglichkeit, eine gute Erfassung zu erhalten, um nur sehr frühen morgen in die, bevor Sie die meisten Benutzer wurde empfangen.

Einige andere nützliche Capture-Techniken stammen direkt von der herkömmlichen Film-Methoden. Beispielsweise verwendet haben wir eine Korrektur Farbkarte auf alle unsere Kameras und erfasste Referenz-Fotos von Texturen und Objekten, die wir später benötigen könnten. 

![Eine grobe Übertragung mit der Korrektur Farbkarte am Machu-Picchu.](images/rough-cut-machu-picchu-500px.png)

Eine grobe Übertragung von Pantheon Filmmaterial vor dem zusammenfügen.

### <a name="processing-the-video"></a>Verarbeiten von Videos

Erfassen von 360°-Inhalt ist nur der erste Schritt, ein hohen Verarbeitungsaufwand ist erforderlich, um die unformatierten überwachungsvideos wir erfasst in der finale Objekte zu konvertieren, in HoloTour angezeigt werden. Sobald wieder konnten, Startseite, die wir für benötigt das Video von 14 verschiedene Kamera-feeds und schalten Sie ihn in ein einziges fortlaufende Video mit minimalen Artefakten. Unser Team Art verwendet eine Reihe von Tools zu kombinieren und die Aufnahme Polnisch aus, und wir entwickelt, eine Pipeline, um die Verarbeitung so weit wie möglich zu optimieren. Die Bearbeitung musste zusammengefügte zusammen Farbe korrigiert, und klicken Sie dann die zusammengesetzte störende Elemente und Elemente entfernen oder Hinzufügen von zusätzlichen Tasche Leben und während der Übertragung, alle mit dem Ziel, diese Eindruck, dass es zu verbessern.

![Eine grobe Übertragung von Pantheon Filmmaterial vor dem zusammenfügen.](images/rough-cut-pantheon-500px.png)

Eine grobe Übertragung von Pantheon Filmmaterial vor dem zusammenfügen. 


Um die Videos zu kombinieren, wir ein Tool Namens verwendet [PTGui](http://www.ptgui.com/) und unsere Pipeline zur anforderungsverarbeitung integriert. Im Rahmen der nach der Verarbeitung, wenn wir weiterhin Frames aus unsere Videos extrahierten und finden Sie eine Verknüpfung Muster, die gut für eine der diese Frames überprüft. Wir haben dieses Muster klicken Sie dann auf ein benutzerdefiniertes Plug-in, das wir geschrieben haben, die zulässige unser video Künstler, fein abstimmen und optimieren die Verknüpfung Muster bei der Zusammensetzung nach Auswirkungen direkt, angewendet. 

![Screenshot der PTGui das zusammengefügte Pantheon Filmmaterial angezeigt.](images/stitching-tool-pantheon-500px.png)

Screenshot der PTGui das zusammengefügte Pantheon Filmmaterial angezeigt. 


### <a name="video-playback"></a>Videowiedergabe

Nach der Verarbeitung von dem die Bearbeitung abgeschlossen ist, haben wir eine nahtlose Video, aber es ist außerordentlich große – etwa 8 K-Auflösung. Decodieren von Video ist teuer, und es gibt nur sehr wenige Computer, auf denen ein 8-KB-Video verarbeiten können, sodass die nächste Aufgabe eine Möglichkeit zum Abspielen dieses Videos auf HoloLens suchen wurde. Wir entwickelt, eine Reihe von Strategien, um zu vermeiden der Kosten und weiterhin gleichzeitig das Verhalten der Benutzer, wie sie die gesamte angezeigt haben Videos zu decodieren.

Die einfachste Optimierung ist, um zu vermeiden, Decodierung von Teilen des Videos, die viele nicht geändert. Wir haben ein Tool, um Bereiche in jeder Szene zu identifizieren, die während der Übertragung nur wenig oder keine geschrieben. Für diese Bereiche erläutert, ein Video zu decodieren, anstatt ein statisches Bild jeder Frame. Um dies zu ermöglichen, wir das umfangreiche Video in viel kleinere Blöcke aufgeteilt.

Wir haben auch sichergestellt, dass es sich bei jedem Pixel, die wir decodiert besonders effektiv verwendet wurde. Wir haben bei Verwendung von Komprimierungstechniken senken Sie die Größe des Videos experimentiert; wir teilen die video-Regionen entsprechend die Polygone der Geometry-Instanz, die es auf projiziert werden würde. Wir UVs angepasst und die Videos, die basierend auf wie viele andere Details-Polygone enthalten gepackt. Das Ergebnis dieser Arbeit ist, das, was begann, als eine einzelne 8 KB video in viele Blöcke unterteilt, die fast unverständlich aussehen, bevor für diese ordnungsgemäß erneut in der Szene projizierten umgewandelt. Für Entwickler von Spielen nachvollziehbar texturzuordnungen und UV packen, wird dies wahrscheinlich bekannt vorkommen. 

![Eine vollständige Ansicht der Pantheon vor Optimierungen.](images/pantheon-before-optimization-500px.png) 

Eine vollständige Ansicht der Pantheon vor Optimierungen. 


![Die rechte Hälfte der Pantheon, für die Videowiedergabe verarbeitet.](images/pantheon-process-video-playback-500px.png) 

Die rechte Hälfte der Pantheon, für die Videowiedergabe verarbeitet. 


![Beispiel für eine einzelne video Region nach der Optimierung und Komprimierung.](images/single-video-region-after-optimization-500px.png) 

Beispiel für eine einzelne video Region nach der Optimierung und Komprimierung. 


Ein anderer Trick verwendeten bestand darin, zu vermeiden, Video, das Sie aktiv anzeigen, werden nicht decodieren. Klicken Sie im HoloTour, sehen Sie nur Teil der vollständigen Szene zu einem bestimmten Zeitpunkt. Wir decodieren nur Videos innerhalb oder außerhalb Ihrer Sichtfeld (Blickfeld) in Kürze. Beim Drehen Kopf beginnen wir mit Wiedergabe des Videos Bereiche, die sind nun in Ihrem Blickfeld und Beenden der Wiedergabe, die nicht mehr darin enthalten sind. Die meisten Benutzer wird nicht selbst Beachten Sie, dass dies der Fall ist, aber wenn Sie schnell zu aktivieren, sehen Sie das Video dauert ein paar Sekunden gestartet, in der Zwischenzeit sehen Sie ein statisches Bild, klicken Sie dann die wird ausgeblendet auf Video an, sobald er fertig ist.

Um diese Strategie funktioniert machen wir eine umfangreiche Videowiedergabe-System entwickelt. Wir optimieren den niedrigen Ebene Wiedergabe-Code, um video wechseln sehr effizient zu machen. Darüber hinaus mussten wir unsere Videos auf besondere Weise zu ermöglichen, schnell zu einem beliebigen Video jederzeit zu codieren. Diese Pipeline Wiedergabe hat viel Entwicklungszeit, damit wir sie in den Phasen implementiert. Da fingen wir mit der ein einfacheres System mit, das weniger effizient war, aber zulässige Designer und Interpreten, an die Benutzeroberfläche und langsam so verbessert werden, es ein stabiler Wiedergabesystem, das wir für den Versand an das endgültige Qualitätsniveau zulässig. Diese letzte System musste benutzerdefinierte Tools, die wir in Unity zum Einrichten von Video in der Szene und der Monitor die Wiedergabe-Engine erstellt haben.

### <a name="recreating-near-space-objects-in-3d"></a>Neu in der Nähe-Objekte in 3D

Videos bilden die Mehrheit der Anzeige in HoloTour, aber es gibt eine Reihe von 3D-Objekten, die in Ihrer Nähe, z. B. das Zeichnen in Piazza Navona, der Jungbrunnen außerhalb der Pantheon oder die heiße Luft Sprechblase, die Sie für Luftbild Szenen stehen erscheinen. Diese 3D-Objekte sind wichtig, da menschliche Wahrnehmung der Tiefe nah sehr gut ist, aber nicht sehr gut weit entfernt. Wir erhalten Video bei der Entfernung, aber damit der Benutzer dann ihre Speicherplatz und können wirklich vorhanden sind, in der Nähe Objekte Tiefe benötigen. Diese Technik ist ähnlich wie bei der Sortierung des Objekts, die möglicherweise angezeigt, in einer natürlichen Verlauf Museum – eine, die physischen Begrünung, Pflanzen und Animal Exemplare im Vordergrund, aber in einem clever maskierte Matte Zeichnen im Hintergrund Ansicht schwindet Diorama Bild.

Einige Objekte sind einfach 3D-Objekten, die wir erstellt und hinzugefügt werden, um der Szene, um die benutzerfreundlichkeit zu verbessern. Das Zeichnen und die heiße Luft Sprechblase fallen in diese Kategorie, da sie nicht vorhanden ist, wenn wir gedreht waren. Ähnlich wie bei spielressourcen können sie eines 3D Interpreten in unserem Team erstellt und wurden entsprechend mit Textur versehen habe. Platzieren wir in unserer Szenen in Ihrer Nähe, wo Sie stehen, und die game-Engine kann rendern, die zwei HoloLens angezeigt, damit sie als ein 3D-Objekt angezeigt werden.

Andere Ressourcen, wie der Jungbrunnen außerhalb der Pantheon sind echte Objekte, die vorhanden sind, in die Speicherorte, in dem wir video fotografieren, allerdings, diese Objekte aus dem Video anzuzeigen in 3D, wir haben eine Reihe von Dingen zu tun.

Zunächst benötigen wir zusätzliche Informationen zu den einzelnen Objekten. Während auf dem Standort für den Filmen, unser Team erfasst viele Verweis die Bearbeitung dieser Objekte, sodass wir müssten genügend detaillierte Images genau die Texturen neu erstellen. Das Team auch ausgeführt eine [Photogrammetry](https://en.wikipedia.org/wiki/Photogrammetry) zu scannen, die erstellt 3D-Modell unter Dutzenden von 2D-Bilder, bietet uns eine grobe Modell des Objekts perfekte Größenordnung.

Wie wir unsere Filmmaterial verarbeiten, werden die Objekte, die später durch eine 3D-Darstellung ersetzt werden, aus dem Video entfernt. Das 3D-Druck-Dialogfeld wird auf Grundlage des Modells Photogrammetry aber bereinigt und durch unsere Künstler vereinfacht. Für einige Objekte, können wir Teilen des Videos verwenden – z. B. Wasser Textur auf der Jungbrunnen, aber die meisten der Jungbrunnen ist jetzt ein 3D-Objekt, dem Benutzer wahrnehmen Tiefe, und führen dazu in einem begrenzten Platz in der Umgebung. In der Nähe-Space-Objekte, wie diese erheblich Sinne wirklichkeitsgetreuen Bilder hinzugefügt und trägt dazu bei, erden Sie die Benutzer in der virtuellen Speicherort. 

![Verwenden Sie die Bearbeitung von Pantheon, mit der Jungbrunnen entfernt. Es wird durch eine 3D-Druck-Dialogfeld ersetzt werden.](images/object-removal-pantheon-500px.png)

Verwenden Sie die Bearbeitung von Pantheon, mit der Jungbrunnen entfernt. Es wird durch eine 3D-Druck-Dialogfeld ersetzt werden.


## <a name="final-thoughts"></a>Abschließende betrachtungen

Natürlich gab es weitere für das Erstellen von diesen Inhalt als die hier erörtert. Es gibt einige Szenen, möchten wir sie "unmöglich Perspektiven" aufrufen, einschließlich heiße Luft Sprechblase herunterladen und die Gladiator zu bekämpfen, in der Colosseum, die einen besseren Ansatz hat. Wir behandeln diese in einer zukünftigen Fallstudie.

Wir hoffen, dass Teilen von Lösungen zu einigen der größeren Herausforderungen, die wir während der Produktion für andere Entwickler nützlich ist und Sie inspiriert, einige dieser Techniken verwenden, um Ihre eigenen faszinieren Benutzeroberflächen für HoloLens erstellen können. (Und wenn Sie Sie sicher, dass sie mit uns auf freigeben, stellen Sie tun, die [HoloLens App Development-Forum](https://forums.hololens.com/)!)

## <a name="about-the-authors"></a>Über die Autoren

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="David Haley" width="60" height="60" src="images/haley.png" /></td>
<td style="border:0" width="408"> <b>David Haley</b> ist als leitender Entwickler Weitere Informationen zu Kamera Rigs und Wiedergabe von Videos, die Sie haben als er möglich von der Bearbeitung HoloTour betrachtet.</td>
<td style="border:0" width="60px"> <img alt="Danny Askew" width="60" height="60" src="images/askew.png" /></td>
<td style="border:0" width="408"> <b>Danny Askew</b> eines Video-Interpreten, die sicherstellen, dass Ihre Navigation durch "ROME" wurde so fehlerlos wie möglich ist.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Jason Syltebo" width="60" height="60" src="images/syltebo.png" /></td>
<td style="border:0" width="408"> <b>Jason Syltebo</b> ist ein Audio-Designer, die sicherstellen, dass die Soundscape von jedem Ziel, die Sie besuchen, selbst wenn Sie zeitlich zurückgehen auftreten können.</td>
<td style="border:0" width="60px"> <img alt="Travis Steiner" width="60" height="60" src="images/steiner.png" /></td>
<td style="border:0" width="408"> <b>Travis Steiner</b> ist Direktor oder entschärft haben und scouted Speicherorte, erstellte Reise Pläne und geleitet von Filmen, die am Standort entwerfen.</td>
</tr>
</table>



## <a name="see-also"></a>Siehe auch
* [Video: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
