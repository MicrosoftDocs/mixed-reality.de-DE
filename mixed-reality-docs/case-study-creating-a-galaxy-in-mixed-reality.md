---
title: 'Fallstudie: Erstellen einer in mixed reality'
description: Vor Microsoft HoloLens, fragten wir unsere Entwickler-Community welche Art von app sie möchten ein erfahrener internes Team für das neue Gerät zu erstellen. Mehr als 5000 Ideen wurden freigegeben und nach einem 24-Stunden-Twitter-Abruf der Gewinner war ein Konzept namens "Galaxy-Explorer".
author: KarimLUCCIN
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy-Explorer, HoloLens, Windows Mixed Reality, Teilen Ihre Idee, Fallstudie
ms.openlocfilehash: a478eaa35144a8ee0fbeaeb43cec4b9f901890ab
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604834"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a>Fallstudie: Erstellen einer in mixed reality

Vor Microsoft HoloLens, fragten wir unsere Entwickler-Community welche Art von app sie möchten ein erfahrener internes Team für das neue Gerät zu erstellen. Mehr als 5000 Ideen wurden freigegeben und nach einem 24-Stunden-Twitter-Abruf der Gewinner eine Idee, die aufgerufen wurde [Galaxy Explorer](galaxy-explorer.md).

Sprechen Sie Andy Zibits, den Lead Art, auf das Projekt, und Karim Luccin, des Teams Grafiken Engineer, über die gemeinsamen Initiative zwischen Kunst und entwickeln, die mit der Erstellung von eine genaue, interaktive Darstellung der Galaxy arbeiten im Galaxy-Explorer geführt hat.

## <a name="the-tech"></a>Der Technologie

[Unser Team](galaxy-explorer.md#meet-the-team) – der zwei Designer drei Entwickler, vier Künstler, ein Producer und einem Tester fiktives – sechs Wochen zum Erstellen einer voll funktionsfähigen app ermöglicht Personen zu lernen und entdecken Sie die Umfangs und das Schöne an unserer Galaxy arbeiten mussten.

Wir wollten die Fähigkeit von HoloLens, direkt in Ihr Platz zum wohnen, 3D-Objekte zu rendern, damit wir uns, dass wir zum Erstellen einer realistischen suchen Galaxy entschieden, wo Benutzer wären können schließen vergrößern und einzelne Sternen, jeweils in eigene herabstürzendes optimal nutzen .

In der ersten Woche der Entwicklung haben wir einige Ziele für unsere Darstellung des Galaxy arbeiten: Es benötigt, um die Tiefe, Bewegung und Verhalten volumetrische verfügen – voll von Sternen, die die Form des Galaxy helfen würde.

Das Problem mit dem Erstellen einer animierten Galaxy, die Milliarden von Sternen war, dass die bloße Anzahl von einzelnen Elementen, die die zu aktualisierenden pro Bild für HoloLens zum Animieren der CPU-Nutzung zu groß wäre. Unsere Lösung bei der eine komplexe Mischung aus Kunst und Wissenschaft.

## <a name="behind-the-scenes"></a>Im Hintergrund

Um Benutzer zum Durchsuchen einzelner Sterne zu ermöglichen, wurde im ersten Schritt herausfinden, wie viele Partikel, die wir auf einmal gerendert werden können.

### <a name="rendering-particles"></a>Rendern von Partikel

Aktuelle CPUs eignen sich hervorragend für die Verarbeitung von serieller Aufgaben und bis zu ein paar paralleler Aufgaben auf einmal (je nachdem wie viele Kerne aufweisen), aber GPUs sind viel effektiver Tausende von Vorgänge parallel verarbeiten. Aber da sie in der Regel nicht gemeinsam den gleichen Speicher wie die CPU nutzen, kann Austauschen von Daten zwischen CPU <> GPU schnell einen Engpass darstellen. Unsere Lösung bestand darin, einer auf der GPU machen, und es muss sich um vollständig live auf der GPU.

Da fingen wir Belastungstests mit Tausenden von Punkt-Partikel in verschiedene Muster. Dadurch konnten wir die Galaxie für HoloLens, um festzustellen, was funktioniert und was nicht abrufen.

### <a name="creating-the-position-of-the-stars"></a>Erstellen die Position der Sterne

Eines unserer Teammitglieder hatte bereits geschrieben. die C# Code, der Sterne in der ursprünglichen Position generieren würden. Die Sternchen sind auf eine Ellipse, und ihre Position kann dadurch beschrieben werden, (**CurveOffset**, **EllipseSize**, **Erhöhung der Rechte**), in denen **CurveOffset**ist der Winkel des Sterns entlang der Ellipse **EllipseSize** ist die Dimension der Ellipse entlang der X-Achse und Z und Erhöhung der richtigen Höhenwinkel des Sterns in die Galaxie. Daher erstellen wir einen Puffer ([Unity ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)), würde mit einzelnen Stern Attribute initialisiert werden und auf der GPU, in dem sie für den Rest der Benutzeroberfläche Leben würde, zu senden. Um diesen Puffer zu zeichnen, verwenden wir [Unity DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) die auf einer beliebigen Gruppe von Punkten ermöglicht einen Shader (Code auf einer GPU) ausgeführt, ohne dass eine tatsächliche Mesh, das die Galaxie darstellt:

**CPU:**




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

**GPU:**




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

Da fingen wir mit unformatierten zirkuläre Mustern mit Tausenden von Partikel. Wir erhielten dadurch den Nachweis, dass es erforderlich, dass wir viele Partikel verwalten und führen Sie es mit der Geschwindigkeit der leistungsfähig, aber wir nicht mit der Gesamtform des Galaxy zufrieden waren. Um die Form zu verbessern, haben wir verschiedene Muster und -Partikelsysteme mit einer Drehung von versucht. Dies waren ursprünglich vielversprechend, daran, dass die Anzahl der Partikel und Leistung konsistent sind geblieben, aber die Form eingestellt in der Mitte wurde und Sterne wurden nach außen was realistischer nicht ausgeben. Wir benötigten eine Ausgabe der Compilerdiagnose, die ermöglichen uns Zeit bearbeiten und die Partikel realistisch, verschieben Sie Schleifen in der Mitte des Galaxy je näher.

![Wir haben versucht, verschiedene Muster und -Partikelsysteme, die, wie diese gedreht.](images/galaxy-patterns-500px.png)

Wir haben versucht, verschiedene Muster und -Partikelsysteme, die, wie diese gedreht.

Unser Team hat ein wenig Recherche zu der Möglichkeit Galaxies-Funktion, und wir haben ein benutzerdefiniertes partikelsystem speziell für das Galaxy, damit wir die Partikel auf Grundlage von Ellipsen verschoben werden kann "[Dichte Wave Theorie](https://en.wikipedia.org/wiki/Density_wave_theory)," die theorizes, die die Arme, der eine Galaxy sind die Bereiche, in Konstanten Bewegung, z. B. einen datenverkehrsstau jedoch höhere Dichte. Stabil und solid angezeigt wird, aber die Sternchen sind tatsächlich verschieben in und aus Arms, wie sie ihre jeweiligen Ellipsen verschoben. In unserem System vorhanden, der Partikel nie vorhanden sind auf der CPU – wir die Karten zu generieren und sie alle in der GPU zu orientieren, also das gesamte System einfach Ausgangszustand + Zeit. Es fortgeschritten wie folgt:

![Fortschritt des partikelsystem mit GPU-rendering](images/spiral-galaxy-arms-500px.jpg)

Fortschritt des partikelsystem mit GPU-rendering


Sobald genügend Ellipsen hinzugefügt werden, und drehen festgelegt sind, seit die Galaxies Formular "Arms", in denen die Verschiebung von Sternen zusammengeführt. Der Abstand der Sterne entlang jeder elliptischen Pfads wurden einige Zufallszahlen zugewiesen, und jedes Sterns wurde ein wenig mit Feldern fester Breite Zufälligkeit hinzugefügt. Dies erstellt eine viel natürlichere aussehende Verteilung von datenverschiebung und Arm-Sternform aus. Schließlich haben wir die Möglichkeit zum Laufwerk Farbe auf Grundlage der Entfernung vom Mittelpunkt hinzugefügt.

### <a name="creating-the-motion-of-the-stars"></a>Erstellen die Bewegung der Sterne

Um die allgemeine Stern Bewegung zu animieren, mussten wir einen Konstanten Winkel für jeden Frame hinzufügen und die abzurufenden Sternen, die auf die Auslassungspunkte mit konstanter Geschwindigkeit radiale verschieben. Dies ist der Hauptgrund für die Verwendung von **CurveOffset**. Dies ist nicht technisch korrekt, Sterne werden entlang der lange Seiten der Ellipsen schneller, aber die allgemeine Bewegung gute spürbar.

![Sterne agieren Sie schneller auf lange Bogens an den Rändern langsamer.](images/ellipse-movement.jpg)

Sterne agieren Sie schneller auf lange Bogens an den Rändern langsamer.


Mit diesem jedes Sterns vollständig von beschrieben wird (**CurveOffset**, **EllipseSize**, **Erhöhung der Rechte**, **Alter**), in denen **Alter** ist eine Ansammlung der die Gesamtzeit, die seit dem Laden der Szene vergangen ist.




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

Das hat uns ermöglicht, um Zehntausende von Sternen einmal am Anfang der Anwendung zu generieren, und wir einen einzelner Satz von Sternen, die auf den eingerichteten Kurven animiert. Da alles, was auf der GPU ist, kann das System alle Sterne parallel ohne Kosten für die CPU animieren.

![Hier ist, wie es beim Zeichnen von weißen Quads aussieht.](images/drawing-white-quads-300px.jpg)

Hier ist, wie es beim Zeichnen von weißen Quads aussieht.



Um jedes Gesicht Quad die Kamera zu machen, verwendet haben wir einen Geometrie-Shader, jede Stern Position in einem 2D-Rechteck auf dem Bildschirm zu transformieren, die unsere Stern Textur enthalten soll.

![Karo statt Quads.](images/drawing-white-quads-300px.jpg)

Karo statt Quads.


Da wir die Überzeichnung (Anzahl der Male, die eine Pixel verarbeitet werden) einschränken möchten so weit wie möglich, wir gedreht unsere Quads, damit sie weniger überschneiden müssten.

### <a name="adding-clouds"></a>Hinzufügen von clouds

Es gibt viele Möglichkeiten, um ein volumetrische Gefühl mit Partikel zu erhalten – von Ray marching innerhalb eines Volumes zum Zeichnen der so viele Partikel wie möglich in einer Cloud zu simulieren. Real-Time-Ray marching war im Begriff, zu teuer und schwierig zu erstellen, werden, daher wechselten wir zuerst eine stünden-System über eine Methode zur Rendering-Gesamtstrukturen in Spiele erstellen – mit einer Vielzahl von 2D-Bilder von Strukturen, die vor der Kamera. Wenn wir dazu ein Spiel verwenden möchten, können wir Texturen von Strukturen, die über eine Kamera, die auf, speichern Sie alle diese Images und zur Laufzeit für jede Karte Billboard rotiert gerendert haben, wählen Sie das Bild, das die ansichtsrichtung entspricht. Dies funktioniert auch nicht, wenn die Images Hologramme sind. Der Unterschied zwischen dem linken und der richtigen Auge erleichtern, damit wir eine viel höhere Auflösung benötigen, da ansonsten nur myblobstorage_storage flach, mit einem Alias versehen ist, oder sich wiederholende.

Klicken Sie auf unserer zweiten Versuch haben wir versucht, dass so viele Partikel wie möglich. Die beste visuelle Elemente wurden erreicht, wenn wir lichtdurchlässigen Partikel Drew, und sie vor dem Hinzufügen der Szene verwischt. Probleme mit diesem Ansatz wurden für wie viele Partikel, die wir auf ein einziges Mal zeichnen können und wie viel Bildschirmbereich sie gleichzeitig 60fps behandelt. Das resultierende Image rufen Sie diese Cloud sei Weichzeichner wurde in der Regel ein sehr ressourcenintensiver Vorgang.

![Ohne die Textur ist dies an, wie die Clouds mit 2 % Deckkraft aussehen würde.](images/clouds-without-texture-300px.jpg)

Ohne die Textur ist dies an, wie die Clouds mit 2 % Deckkraft aussehen würde.



Additive wird und dass viele von ihnen also mehrere Quads übereinander, müssten wir wiederholt Schattierung dasselbe Pixel. In der Mitte des Galaxy dasselbe Pixel hält Hunderte von Quads bauen aufeinander auf, und dies hat enormen Kosten verbunden, wenn Vollbildmodus ausgeführt wird.

Vollbildmodus Clouds durchführen, und versuchen, diese blur hätten keine gute Idee, daher entschieden wir, die Hardware, die die Arbeit für uns leisten können.

### <a name="a-bit-of-context-first"></a>Ein bit des Kontexts zunächst

Bei Verwendung von Texturen in einem Spiel entspricht der Texturgröße selten Bereich in verwendet werden soll, jedoch können wir andere Art von texturfilterung zum Abrufen der Grafikkarte auf, um die Farbe zu interpolieren in Pixel der Textur erstellt werden sollten ([Texturfilterung](https://msdn.microsoft.com/library/dn642451.aspx)). Die Filterung, die uns interessiert ist [bilineare Filterung](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) die wird den Wert jedes Pixels mit dem 4 nächsten Nachbarn berechnet.

![Ursprüngliche Filtervorgang](images/texture-1.png)

![Führen Sie nach dem Filtern](images/texture-2.png)

Diese Eigenschaft verwenden, sehen wir, dass jeder Versuch, eine Textur in einem Bereich doppelt so groß, zeichnen sie das Ergebnis verwischt.

Statt in den Vollbildmodus Rendern und verlieren diese wertvollen in Millisekunden, die wir auf einen anderen Ausgaben werden konnte, Rendern es auf eine kleine Version des Bildschirms aus. Klicken Sie dann erhalten Sie durch Kopieren dieser Textur und Dehnen es mit einem Faktor von 2 mehrmals, Vollbildmodus und den Inhalt im Prozess Weichzeichner.

![X3 an voller Auflösung vergrößern.](images/galaxy-resolutions-300px.png)

X3 an voller Auflösung vergrößern.



Dies konnten wir das Cloud-Part mit nur ein Bruchteil der Kosten der ursprünglichen abrufen. Anstatt zum Hinzufügen von Clouds für die vollständige Lösung, wir nur Paint 1/64. der Pixel und nur stretch die Textur an voller Auflösung.

![Links, mit einem hochpreisiger von 1/8. um voller Auflösung; und mit 3, vergrößern Potenz von 2 verwenden.](images/stars-upscaled-300px.jpg)

Links, mit einem hochpreisiger von 1/8. um voller Auflösung; und mit 3, vergrößern Potenz von 2 verwenden.


Beachten Sie, versuchen, wechseln von 1/64. die Größe auf die vollständige Größe in einer Aktion würde ganz anders aussehen, während der Grafikkarte weiterhin 4 Pixel in diesem Setup verwenden würde, um einen größeren Bereich schattieren aus, und starten Sie die Elemente angezeigt werden.

Klicken Sie dann, wenn wir voller Auflösung Sterne mit kleineren Karten hinzufügen, erhalten wir die vollständige Galaxie:

![In der Nähe Endergebnis Galaxy-Rendering mit voller Auflösung Sterne](images/full-galaxy-500px.png)

Nachdem wir auf dem richtigen Weg mit der Form waren, haben wir eine Ebene von Clouds, die temporäre Punkte, mit denen, die wir in Photoshop gezeichnet, die und einige zusätzliche Farbe, ausgelagert hinzugefügt. Das Ergebnis war ein Galaxy arbeiten unsere moderne Entwicklungsteams beide spürbar gut gelungen ist und es unser Ziel mit Tiefe, Volumes und während der Übertragung erfüllt – ganz ohne hohe Anforderungen an die CPU.

![Unsere letzte arbeiten Galaxy in 3D.](images/final-galaxy-500px.jpg)

Unsere letzte arbeiten Galaxy in 3D.


### <a name="more-to-explore"></a>Auf die Zukunft

Wir haben den Code für das Galaxy-Explorer-app als Open Source und auf zur Verfügung gestellt [GitHub](https://github.com/Microsoft/GalaxyExplorer) für Entwickler erstellen.

Weitere Informationen zu den Entwicklungsprozess für Galaxy Explorer herausfinden möchten? Sehen Sie sich alle unsere letzten Projekt Updates auf die [Microsoft HoloLens YouTube-Kanal](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).

## <a name="about-the-authors"></a>Über die Autoren

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><b>Karim Luccin</b> ist Software Engineer und mit Effekten Visuals Enthusiast. Er war der Techniker Grafiken für Galaxy-Explorer.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><b>Andy Zibits</b> ist eine Art Lead und Speicherplatz Enthusiast verwaltet das Team 3D Modellierung für Galaxy-Explorer, und für noch mehr Partikel auseinander setzen.</td>
</tr>
</table>


## <a name="see-also"></a>Siehe auch
* [Galaxy-Explorer auf GitHub](https://github.com/Microsoft/GalaxyExplorer)
* [Galaxy Explorer projektaktualisierungen auf YouTube](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
