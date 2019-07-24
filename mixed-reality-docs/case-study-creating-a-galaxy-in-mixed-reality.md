---
title: 'Fallstudie: Erstellen einer Galaxie in gemischter Realität'
description: Bevor Microsoft hololens ausgeliefert wurde, fragten wir unsere Entwickler Community, welche Art von APP Ihnen einen erfahrenen internen TeamBuild für das neue Gerät bereitstellen möchte. Mehr als 5000 Ideen wurden freigegeben, und nach einer 24-stündigen Twitter-Umfrage war der Gewinner eine Idee namens "Galaxy Explorer".
author: KarimLUCCIN
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy Explorer, hololens, Windows Mixed Reality, teilen Sie Ihre Idee, Fallstudie
ms.openlocfilehash: a478eaa35144a8ee0fbeaeb43cec4b9f901890ab
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63523766"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a>Fallstudie: Erstellen einer Galaxie in gemischter Realität

Bevor Microsoft hololens ausgeliefert wurde, fragten wir unsere Entwickler Community, welche Art von APP Ihnen einen erfahrenen internen TeamBuild für das neue Gerät bereitstellen möchte. Mehr als 5000 Ideen wurden freigegeben, und nach einer 24-stündigen Twitter-Umfrage war der Gewinner eine Idee namens " [Galaxy Explorer](galaxy-explorer.md)".

Andy zibits, der Kunst Leiter im Projekt und Karim Luccin, der Grafik Techniker des Teams, sprechen über den kollaborativen Aufwand zwischen Kunst und Engineering, der zur Erstellung einer exakten, interaktiven Darstellung der MILCHWEG-Galaxy in Galaxy Explorer geführt hat.

## <a name="the-tech"></a>Die Technologie

[Unser Team](galaxy-explorer.md#meet-the-team) besteht aus zwei Designern, drei Entwicklern, vier Künstlern, einem Producer und einem Tester – es gab sechs Wochen, eine voll funktionsfähige APP zu erstellen, die es den Benutzern ermöglicht, sich mit der Menschen Nähe und der Schönheit unserer Milchwege-Galaxy vertraut zu machen.

Wir wollten die Fähigkeit von hololens in vollem Umfang nutzen, 3D-Objekte direkt in ihren Lebensbereich zu Rendering. Daher wollten wir eine realistische, aussehende Galaxie erstellen, in der die Benutzer in der Lage sind, die Schließung zu vergrößern und einzelne Sterne anzuzeigen .

In der ersten Woche der Entwicklung haben wir einige Ziele für unsere Darstellung der Milchwege-Galaxy-Methode erreicht: Es brauchte Tiefe, Bewegung und Gefühl von "Volumetric – Full of Stars", die beim Erstellen der Form der Galaxie helfen würden.

Das Problem bei der Erstellung einer animierten Galaxie mit Milliarden von Sternen war, dass die reine Anzahl von einzelnen Elementen, die aktualisiert werden müssen, pro Frame zu groß wäre, damit hololens mithilfe der CPU animiert werden. Unsere Lösung umfasste eine komplexe Mischung aus Kunst und Wissenschaft.

## <a name="behind-the-scenes"></a>Im Hintergrund

Der erste Schritt besteht darin, herauszufinden, wie viele Partikel gleichzeitig dargestellt werden könnten.

### <a name="rendering-particles"></a>Rendern von Partikeln

Aktuelle CPUs eignen sich hervorragend für die Verarbeitung von seriellen Aufgaben und bis zu einem Paar paralleler Aufgaben auf einmal (abhängig von der Anzahl der Kerne). GPUs sind jedoch weitaus effektiver, wenn Tausende von Vorgängen parallel verarbeitet werden. Da Sie jedoch in der Regel nicht denselben Arbeitsspeicher wie die CPU gemeinsam nutzen, kann der Datenaustausch zwischen CPU-< > GPU schnell zu einem Engpass werden. Unsere Lösung bestand darin, eine Galaxie auf der GPU zu erstellen, die vollständig auf der GPU gelebt werden musste.

Wir haben Belastungstests mit Tausenden von Punkt Partikeln in verschiedenen Mustern gestartet. Auf diese Art konnten wir die Galaxie auf hololens bringen, um zu sehen, was funktionierte und was nicht.

### <a name="creating-the-position-of-the-stars"></a>Erstellen der Position der Sterne

Eines unserer Teammitglieder hat bereits den Code geschrieben C# , der Sterne an der ursprünglichen Position generieren würde. Die Sterne befinden sich auf einer Ellipse, und ihre Position kann von ("**Cursor Offset**", " **ellipsesize**", " **Erhöhung**") beschrieben werden, wobei " **Cursor Offset** " der Winkel des Sterns entlang der Ellipse ist, " **ellipsesize** " die Dimension der Ellipse. entlang von X und Z und Erhöhung der ordnungsgemäßen Erweiterung des Stern in der Galaxy. Daher können wir einen Puffer ([computebuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) erstellen, der mit jedem Star-Attribut initialisiert und an die GPU gesendet wird, wo er für den Rest der Arbeit leben würde. Zum Zeichnen dieses Puffers verwenden wir das [drawprozeduren von Unity](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) , das das Ausführen eines Shaders (Code auf einer GPU) für eine beliebige Gruppe von Punkten ermöglicht, ohne dass ein tatsächliches Mesh vorhanden ist, das das Galaxy darstellt:

**CPU**




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

**AUSSCHALTEN**




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

Wir haben mit unformatierten zirkulären Mustern mit Tausenden von Partikeln begonnen. Wir haben uns die erforderliche Prüfung gegeben, dass wir viele Partikel verwalten und mit leistungsfähiger Geschwindigkeit ausführen können. Wir haben uns jedoch nicht mit der Gesamtform der Galaxie zufrieden gestellt. Um die Form zu verbessern, haben wir versucht, verschiedene Muster und Partikelsysteme mit Drehung zu entwickeln. Diese waren anfänglich vielversprechend, weil die Anzahl der Partikel und die Leistung konsistent waren, aber die Form nahe dem Mittelpunkt aufbrach und die Sterne ausgingen, was nicht realistisch war. Wir brauchten eine Ausgabe, mit der wir die Zeit verändern konnten, und die Partikel werden realistisch verschoben, und die Schleife wird immer näher an der Mitte der Galaxie durchlaufen.

![Wir haben versucht, verschiedene Muster und Partikelsysteme zu drehen, die wie folgt gedreht wurden.](images/galaxy-patterns-500px.png)

Wir haben versucht, verschiedene Muster und Partikelsysteme zu drehen, die wie folgt gedreht wurden.

Unser Team hat einige Untersuchungen zur Funktionsweise von Galaxien durchgeführt, und wir haben ein benutzerdefiniertes Partikelsystem speziell für die Galaxie erstellt, sodass wir die Partikel auf Ellipsen basierend auf "[Dichtewellen Theorie](https://en.wikipedia.org/wiki/Density_wave_theory)" verschieben konnten. Dies weist darauf hin, dass es sich bei den Armen einer Galaxy um Bereiche von höhere Dichte, aber in konstantem Flux, wie z. b. eine Verkehrsampel. Es erscheint stabil und solide, aber die Sterne bewegen sich tatsächlich in den und aus den Armen, wenn Sie sich auf die jeweiligen Ellipsen bewegen. In unserem System sind die Partikel nie auf der CPU vorhanden – wir generieren die Karten und orientieren Sie alle auf der GPU, sodass das gesamte System einfach den anfänglichen Zustand und die Zeit hat. Dies ist wie folgt:

![Fortschritt des partikelsystems mit GPU-Rendering](images/spiral-galaxy-arms-500px.jpg)

Fortschritt des partikelsystems mit GPU-Rendering


Sobald genügend Auslassungs Punkte hinzugefügt wurden und für die Rotation festgelegt sind, begannen die Galaxien mit der Bildung von "Arms", bei der die Bewegung von Sternen konvergiert. Der Abstand der Sterne entlang der einzelnen Ellipsen Pfade hat eine gewisse Zufälligkeit eingeräumt, und jedem Stern wurde ein wenig Positions Zufälligkeit hinzugefügt. Dadurch wurde eine viel natürlichere Verteilung der Stern Bewegung und der Arm-Form erstellt. Schließlich haben wir die Möglichkeit hinzugefügt, die Farbe basierend auf der Entfernung vom Mittelpunkt zu steuern.

### <a name="creating-the-motion-of-the-stars"></a>Erstellen der Bewegung der Sterne

Um die allgemeine Stern Bewegung zu animieren, mussten wir einen konstanten Winkel für jeden Frame hinzufügen und Sterne an einer Konstanten radialen Geschwindigkeit entlang der Ellipsen bewegen. Dies ist der Hauptgrund für die Verwendung von " **Cursor Offset**". Dies ist technisch nicht korrekt, da Sterne auf den langen Seiten der Ellipsen schneller bewegt werden, aber die allgemeine Bewegung war gut.

![Sterne bewegen sich auf dem langen Bogen schneller, langsamer an den Rändern.](images/ellipse-movement.jpg)

Sterne bewegen sich auf dem langen Bogen schneller, langsamer an den Rändern.


Dadurch wird jeder Stern vollständig durch beschrieben ("**Cursor Offset**", " **ellipssize**", " **Erhöhung**", " **Alter**"), wobei " **Age** " eine Ansammlung der Gesamtzeit ist, die seit dem Laden der Szene vergangen ist.




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

Dies ermöglichte uns, Zehntausende von Sternen einmal am Anfang der Anwendung zu generieren. anschließend animierten wir eine Reihe von Sternen entlang der etablierten Kurven. Da alles auf der GPU basiert, kann das System alle Sterne parallel zu den CPU-Kosten animieren.

![Hier sehen Sie, wie es aussieht, wenn Sie weiße Quads zeichnen.](images/drawing-white-quads-300px.jpg)

Hier sehen Sie, wie es aussieht, wenn Sie weiße Quads zeichnen.



Um jedes Vierfache der Kamera zuzuordnen, haben wir einen Geometry-Shader verwendet, um jede Stern Position in ein 2D-Rechteck auf dem Bildschirm umzuwandeln, das die Stern Textur enthält.

![Diamanten anstelle von Quads.](images/drawing-white-quads-300px.jpg)

Diamanten anstelle von Quads.


Da wir die Überschreibung (die Häufigkeit, mit der ein Pixel verarbeitet wird) so weit wie möglich einschränken wollten, haben wir unsere Quads so gedreht, dass Sie weniger überlappend haben.

### <a name="adding-clouds"></a>Hinzufügen von Clouds

Es gibt viele Möglichkeiten, ein volummetric-Gefühl mit Partikeln zu erzielen – von dem Ray, das sich innerhalb eines Volumes befindet, um so viele Partikel wie möglich zu zeichnen, um eine Cloud zu simulieren. Die Echtzeitdarstellung von Ray war zu teuer und schwer zu erstellen, daher haben wir zuerst versucht, ein unveränderliches System mit einer Methode zum Rendern von Gesamtstrukturen in spielen zu erstellen – mit einer großen Zahl von 2D-Bildern von Bäumen, die der Kamera ausgesetzt waren. Wenn wir dies in einem Spiel durchführen, können Sie Strukturen von Bäumen rendern, die von einer Kamera gerendert werden, die alle Bilder speichert, und zur Laufzeit für jede Billboard-Karte das Bild auswählen, das der Ansichts Richtung entspricht. Dies funktioniert auch nicht, wenn es sich um Hologramme handelt. Der Unterschied zwischen dem linken und dem rechten Auge ist, dass wir eine viel höhere Auflösung benötigen, oder es wird nur ein flach, ein Alias oder ein wiederholtes aussehen angezeigt.

Bei unserem zweiten Versuch haben wir versucht, so viele Partikel wie möglich zu haben. Die besten visuellen Elemente wurden erzielt, als wir die Partikel Additiv gezeichnet haben, bevor Sie der Szene hinzugefügt wurden. Die typischen Probleme bei diesem Ansatz standen in Bezug darauf, wie viele Partikel zu einem einzigen Zeitpunkt gezeichnet werden konnten und wie viel Bildschirmfläche Sie abgedeckt haben, während 60 fps beibehalten werden. Das resultierende Bild zu verschleiern, um dieses cloudgefühl zu erhalten, war normalerweise ein sehr kostspieliger Vorgang.

![Ohne Textur würden die Clouds mit einer Deckkraft von 2% aussehen.](images/clouds-without-texture-300px.jpg)

Ohne Textur würden die Clouds mit einer Deckkraft von 2% aussehen.



Wenn Sie Additiv sind und viele davon haben, sind mehrere aufeinander folgende aufeinander folgende aufeinander folgende. In der Mitte der Galaxy hat das gleiche Pixel Hunderte von aufeinander folgenden, und dies hat bei vollständigem Bildschirm enorme Kosten.

Das Ausführen von voll Bild Clouds und das versuchen, Sie zu verwischen, wäre eine gute Idee. Wir haben uns also entschieden, die Hardware für uns zu Unternehmen.

### <a name="a-bit-of-context-first"></a>Ein bisschen Kontext zuerst

Bei der Verwendung von Texturen in einem Spiel entspricht die Textur Größe selten dem Bereich, in dem wir Sie verwenden möchten, aber wir können unterschiedliche Arten von Textur Filtern verwenden, um die Grafikkarte zum Interpolieren der gewünschten Farbe aus den Pixeln der Textur ([Textur Filterung](https://msdn.microsoft.com/library/dn642451.aspx)) zu verwenden. Die Filterung, die uns interessiert ist [bilineare Filterung](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) die wird den Wert jedes Pixels mit dem 4 nächsten Nachbarn berechnet.

![Ursprüngliches vor dem Filtern](images/texture-1.png)

![Ergebnis nach dem Filtern](images/texture-2.png)

Mit dieser Eigenschaft sehen wir, dass jedes Mal, wenn wir versuchen, eine Textur in einem Bereich doppelt so groß zu zeichnen, das Ergebnis verwirft.

Anstatt auf einen voll Bildschirm zu rendern und die kostbaren Millisekunden zu verlieren, würden wir uns auf eine kleine Version des Bildschirms rendern. Wenn Sie dann diese Textur kopieren und Sie um einen Faktor von 2 mehrmals Strecken, werden wir wieder zum voll Bildschirm zurückkehren, während wir den Inhalt des Prozesses verschleiern.

![x3 hochskalieren bis vollständige Auflösung.](images/galaxy-resolutions-300px.png)

x3 hochskalieren bis vollständige Auflösung.



Dadurch konnten wir den cloudteil nur mit einem Bruchteil der ursprünglichen Kosten erreichen. Anstatt Clouds für die vollständige Auflösung hinzuzufügen, zeichnen wir nur die 1/64-Stel der Pixel und Strecken die Textur auf die vollständige Auflösung zurück.

![Links, mit einer hochskalieren von 1/8 bis vollständiger Auflösung; und das Recht, mit drei hochskalieren von 2.](images/stars-upscaled-300px.jpg)

Links, mit einer hochskalieren von 1/8 bis vollständiger Auflösung; und das Recht, mit drei hochskalieren von 2.


Beachten Sie, dass der Versuch, zwischen 1 und 64 von der Größe in eine ganze Größe zu wechseln, vollständig anders aussehen würde, da die Grafikkarte weiterhin 4 Pixel im Setup verwendet, um einen größeren Bereich zu schattieren und die Artefakte angezeigt werden.

Wenn wir dann voll auflösende Sterne mit kleineren Karten hinzufügen, erhalten wir die vollständige Galaxy-Version:

![Fast Final result of Galaxy Rendering using Full Resolution Stars](images/full-galaxy-500px.png)

Nachdem wir uns auf der rechten Spur mit der Form befanden, haben wir eine Schicht von Clouds hinzugefügt, die temporären Punkte ausgetauscht, die wir in Photoshop gezeichnet haben, und einige zusätzliche Farben hinzugefügt. Das Ergebnis war eine Milch Methode, die unsere Kunst-und Engineering-Teams sowohl gut als auch unsere Ziele für tiefe, Volumen und Bewegung –, ohne die CPU zu steuern.

![Unsere endgültige Milchwege-Galaxy in 3D.](images/final-galaxy-500px.jpg)

Unsere endgültige Milchwege-Galaxy in 3D.


### <a name="more-to-explore"></a>Weitere Informationen

Wir haben den Code für die Galaxy Explorer-app geöffnet und auf [GitHub](https://github.com/Microsoft/GalaxyExplorer) zur Verfügung gestellt, auf dem Entwickler aufbauen können.

Möchten Sie mehr über den Entwicklungsprozess für den Galaxy Explorer erfahren? Sehen Sie sich alle früheren Projekt Updates auf dem [Microsoft hololens-YouTube-Kanal](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)an.

## <a name="about-the-authors"></a>Informationen zu den Autoren

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><b>Karim Luccin</b> ist ein Software Entwickler und Liebhaber von visuellen Elementen. Er war der Grafik Techniker für Galaxy Explorer.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><b>Andy zibits</b> ist ein Kunst Leiter und Platz Liebhaber, der das 3D-Modellierungs Team für den Galaxy Explorer verwaltet und für noch mehr Partikel gekämpft hat.</td>
</tr>
</table>


## <a name="see-also"></a>Siehe auch
* [Galaxy Explorer auf GitHub](https://github.com/Microsoft/GalaxyExplorer)
* [Galaxy Explorer-Projektaktualisierungen auf YouTube](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
