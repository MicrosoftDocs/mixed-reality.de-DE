---
title: Asset-Erstellungsprozesses
description: Anleitungen zum Erstellen von Ressourcen für mixed Reality-Umgebungen.
author: paseb
ms.author: paseb
ms.date: 03/21/2018
ms.topic: article
keywords: Asset, Erstellung, Prozess, Budget, Polygone, Texturen, Shader, Leistung
ms.openlocfilehash: cec689ab4d44591d2d3e84679c3fe51dba161bc5
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604714"
---
# <a name="asset-creation-process"></a>Asset-Erstellungsprozesses

Windows Mixed Reality basiert auf der Jahrzehnte Investition, die Microsoft in DirectX vorgenommen hat. Dies bedeutet, dass alle Entwickler Erfahrungen und Fähigkeiten mit dem Erstellen von 3D Grafiken weiterhin mit HoloLens nützlich sein.

Die Ressourcen, die Sie für ein Projekt erstellen, kommen in vielen Formen und Größen. Sie können eine Reihe von Texturen/Bilder, Audio, Video, umfassen-3D-Modelle und Animationen. Beginnen wir kann nicht auf alle Tools behandelt, die für die verschiedenen Typen von-Ressourcen erstellen, in einem Projekt verfügbar sind. In diesem Artikel liegt der Schwerpunkt auf 3D-Druck-Dialogfeld Methoden zur knotenerstellung.

![Konzept "," erstellen "," Integration "und" Iteration flow](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*Konzept "," erstellen "," Integration "und" Iteration flow*

## <a name="things-to-consider"></a>Zu berücksichtigende Informationen

Beim Blick auf die Oberfläche, die Sie möchten, erstellen Sie verwenden stellen Sie sich als ein **Budget** , dass Sie investieren können, um zu versuchen, die bestmögliche Umgebung bereitzustellen. Es ist nicht unbedingt harte Grenzwerte für die Anzahl der **Polygone** oder **Materialtypen** in Ihre Assets, aber mehr budgetierten diverse Kompromisse verwenden.

Im folgenden finden Sie eine Beispiel-Budget für Ihre Umgebung an. Leistung ist nicht in der Regel eine einzelne Fehlerquelle Fehler jedoch Tod von Tausend Schnitte pro Se.
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><b>Assets</b></th><th style="text-align:right;"> CPU</th><th> GPU</th><th> Arbeitsspeicher</th>
</tr><tr>
<td> Polygons</td><td> 0%</td><td> 5%</td><td> 10 %</td>
</tr><tr>
<td> Texturen</td><td> 5%</td><td> 15%</td><td>25%</td>
</tr><tr>
<td> Shader</td><td> 15%</td><td> 35 %</td><td> 0%</td>
</tr><tr>
<td> <b>Dynamics</b></td><td></td><td></td><td></td>
</tr><tr>
<td> Physik</td><td> 5%</td><td> 15%</td><td> 0%</td>
</tr><tr>
<td> Echtzeit-Beleuchtung</td><td> 10 %</td><td> 0%</td><td> 0%</td>
</tr><tr>
<td> Medien (Audio/Video)</td><td> -</td><td> 15%</td><td> 25%</td>
</tr><tr>
<td> Skript oder Logiken</td><td> 25%</td><td> 0%</td><td> 5%</td>
</tr><tr>
<td> Lägen</td><td> 5%</td><td> 5%</td><td> 5%</td>
</tr><tr>
<td> <b>Insgesamt</b></td><td> <b>65%</b></td><td> <b>90%</b></td><td> <b>70%</b></td>
</tr>
</table>

**Gesamtanzahl der Objekte**
* Wie viele Ressourcen in der Szene aktiv sind?

**Die Komplexität von assets**
* Wie viele Dreiecke / Polygone?
* Wie komplex der Shader den Wert?

Die Entwickler und Künstler müssen die Funktionen des Geräts und der Grafik-Engine zu bedenken. Microsoft HoloLens verfügt über alle von berechnungs- und Grafiken auf dem Gerät erstellt. Es gibt die Funktionen, die Entwickler auf einer mobilen Plattform findet.

Der Erstellungsvorgang für Ressourcen ist identisch unabhängig davon, ob Sie eine Benutzeroberfläche für das Ziel sind ein [holographic-Gerät oder eine immersive Gerät](mixed-reality.md#the-mixed-reality-spectrum). Die primäre ist zu beachten die Gerätefunktion, die oben genannten sowie Skalierung, da Sie die reale Welt in mixed Reality sehen können, die richtige Skalierung basierend auf der Erfahrung verwalten möchten. 

## <a name="authoring-assets"></a>Erstellen von Ressourcen

Wir beginnen mit den Möglichkeiten, Objekte für Ihr Projekt zu erhalten:
1. Erstellen Assets (Objekt erfassen und Authoring Tools)
2. Erwerb von Ressourcen (Einkauf Assets online)
3. Portieren von Ressourcen (die vorhandene Ressourcen)
4. Outsourcing dienen (Importieren von Anlagen aus den 3.)

### <a name="creating-assets"></a>Erstellen von Ressourcen

**Entwicklungstools**<br>
Zunächst können Sie Ihre eigenen Ressourcen in einer Reihe von Möglichkeiten erstellen. 3D Künstler mithilfe einer Reihe von Anwendungen und Tools zum Erstellen von Modellen bestehend **Gitter**, **Texturen**, und **Materialien**. Dies wird dann in einem Dateiformat ausgegeben, die importiert oder von der Grafikengine, die von der app verwendet z. B. verwendet werden kann gespeichert **. FBX** oder **. OBJ**. Jedes Tool, das ein Modell generiert, die der ausgewählten Grafikengine unterstützt funktioniert auf **HoloLens**. Zwischen 3D Künstler, auch viele verwenden [Autodesks Maya die selbst kann mit HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) zum Transformieren von der Möglichkeit Medienobjekte erstellt werden. Wenn Sie etwas in Schnellstart abrufen möchten können Sie auch verwenden [3D-Generator](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) , die im Lieferumfang von Windows zu exportieren. OBJ für die Verwendung in Ihrer Anwendung.

**Objekt-Erfassung**<br>
Es ist auch die Option zum Erfassen von Objekten in 3D. Erfassen von einem Informationstechnologie-(IT-)Unternehmen Objekte in 3D und bearbeiten sie mit der Erstellung digitaler Inhalte Software ist zunehmender Beliebtheit erfreut, mit dem 3D-Druck. Mithilfe der **Kinect 2** Sensor und [3D-Generator](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) können Sie das Feature zum Erstellen von Objekten aus der realen Welt Objekte. Dies ist auch eine [-Suite von Tools](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) mit hierfür **Photogrammetry** durch die Verarbeitung einer Anzahl von Abbildern zusammenfügen zusammen und Mesh und Texturen.

### <a name="purchasing-assets"></a>Erwerb von Ressourcen

Eine weitere hervorragende Möglichkeit ist zum Erwerb von Ressourcen für Ihre Umgebung. Sind eine Menge von Ressourcen zur Verfügung, über Dienste wie z. B. die [Unity Asset Store](https://www.assetstore.unity3d.com/) oder [TurboSquid](http://www.turbosquid.com/) unter anderem.

Wenn Sie Ressourcen von einer Partei 3. erwerben möchten Sie immer folgende Punkte zu überprüfen:
* **Was ist die Anzahl der Poly?**
  * Passt es im Rahmen Ihres Budgets?
* **Gibt es Detailebenen (LODs) für das Modell?**
  * Detailebene eines Modells können Sie die Details der ein Modell für die Leistung zu skalieren.
* **Ist die Quelldatei verfügbar?**
  * In der Regel nicht im Lieferumfang [Unity Asset Store](https://www.assetstore.unity3d.com/) jedoch stets mit Diensten wie enthalten [TurboSquid](http://www.turbosquid.com/).
  * Ohne die Quelldatei wird nicht Sie das Medienobjekt ändern können.
  * Stellen Sie sicher, dass die Quelldatei angegeben durch Ihre 3D Tools importiert werden kann.
* **Wissen Sie, was Sie optimal nutzen**
  * Werden Animationen werden bereitgestellt?
  * Stellen Sie sicher, um die Inhaltsliste des Medienobjekts zu überprüfen, den Sie kaufen wollen, sind.

### <a name="porting-assets"></a>Portieren von assets

In einigen Fällen müssen Sie vorhandene Ressourcen ihm übergeben werden, die ursprünglich für andere Geräte und die verschiedenen apps erstellt wurden. In den meisten Fällen können diese Objekte in Formate, die kompatibel mit der Grafikengine konvertiert werden, die von ihrer app verwendet wird.

Bei der Portierung von Ressourcen in Ihrer Anwendung HoloLens verwenden, benötigen Sie folgende Fragen stellen:
* **Können Sie importieren, direkt oder in ein anderes Format konvertiert werden muss?** Überprüfen Sie das Format, die mit der Grafik-Engine importiert haben, die Sie verwenden.
* **Wenn in einem kompatiblen Format konvertieren, wird nichts verloren?** Mitunter Details unterbrochen werden können, oder importieren, kann dazu führen, dass Elemente, die in einem Erstellungstool 3D bereinigt werden müssen.
* **Was ist die Dreiecke / zählen Polygone für das Medienobjekt?** Dem verfügbaren Budget für die Anwendung Sie können [Simplygon](https://www.simplygon.com/) oder ähnliche Tools zum Dezimieren (Prozedural oder manuell Reduzierung der Anzahl der Poly) das ursprüngliche Asset an Ihr Budget Anwendungen anpassen.

### <a name="outsourcing-assets"></a>Outsourcing-Ressourcen

Eine weitere Option für größere Projekte, die mehr Ressourcen als Ihr Team erforderlich ist ist zur Auslagerung der medienobjekterstellung so ausgestattet, dass das erstellen. Der Prozess der Outsourcing umfasst, suchen die richtigen Studio oder eine Agentur, die spezialisiert hat in Outsourcing-Objekte. Dies kann die teuerste Option werden jedoch auch die flexibelste in Sie erhalten.
* **Klar zu definieren, was Sie anfordern**
  * Geben Sie so viele Details wie möglich
  * Front-"," Seite "und" Back Konzept Bilder
  * Verweis Art mit Asset im Kontext
  * Skalierung des Objekts (in der Regel in Zentimeter angegeben)
* **Geben Sie ein Budget**
  * Bereich für die Anzahl von Poly
  * Anzahl von Texturen
  * Typ des Shaders (für Unity und HoloLens, die Sie immer mobiler Shader zuerst standardmäßig sollte)
* **Verstehen der Kosten**
  * Was ist die Outsourcing-Richtlinie für Change Requests?

Outsourcing kann extrem gut basierend auf Ihrer Zeitachse Projekten arbeiten, aber erfordert weitere Überwachung, um sicherzustellen, dass Sie die richtigen Ressourcen erhalten, die Sie beim ersten benötigen.
