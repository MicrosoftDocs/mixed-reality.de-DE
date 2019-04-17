---
title: Periodisch-Tabelle der Elemente
description: Periodisch-Tabelle der Elemente ist ein Open-Source-Beispiel-app in den Microsoft gemischte Realität Entwurf Labs, erfahren Sie, wie ein Array von Objekten im 3D-Raum mit verschiedenen Surface-Typen, die mit einer objektauflistung Layout können.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, entwerfen, die Beispiel-app, die Steuerelemente
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596693"
---
# <a name="periodic-table-of-the-elements"></a>Periodisch-Tabelle der Elemente

>[!NOTE]
>Dieser Artikel beschreibt ein Beispiel für eine explorative wir, in erstellt haben der [Mixed Reality Entwurf Labs](https://github.com/Microsoft/MRDesignLabs_Unity), einen Ort, in dem wir der Erkenntnisse zu teilen, und Vorschläge für mixed Reality-app-Entwicklung. Wenn wir neue Erkenntnisse vornehmen weiterentwickelt unser Entwurf bezogenen Artikeln und Code.

[Periodisch-Tabelle der Elemente](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) ist eine Open-Source Beispielapp von den Microsoft Mixed Reality Entwurf Labs. Bei diesem Projekt erfahren Sie, wie ein Array von Objekten im 3D-Raum mit verschiedenen Oberflächentypen mit Layout ein  **[-objektauflistung](object-collection.md)**. Außerdem erfahren Sie, wie es Objekte erstellen, die auf standardmäßigen Eingaben von HoloLens reagieren. Sie können dieses Projekts Komponenten verwenden, zum Erstellen eines eigenen mixed Reality-app-Erfahrung.

![Punkt-Tabelle der Elemente-app](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a>Informationen zur app

Periodisch-Tabelle der Elemente visualisiert chemischen Elemente und ihre Eigenschaften in einem 3D-Raum. Es umfasst die grundlegenden Interaktionen von HoloLens wie Blicke und Air, tippen Sie auf. Benutzer erhalten weitere Informationen zu den Elementen mit animierte 3D-Modellen. Sie können visuell verstehen, ein Element den Electron-Shell und seine Kernstück - das Protons und Neutrons besteht.

## <a name="background"></a>Hintergrund

Nach dem ersten HoloLens habe, war einer periodisch-Tabellen-app eine Idee, die ich wusste, ich zum Experimentieren mit in mixed Reality wollte. Da jedes Element über viele Datenpunkte, die mit dem Text angezeigt werden verfügt, dachte ich, dass es gute fachlicher zum Untersuchen von typografischen Komposition in einem 3D-Raum wäre. Wird das Element den Electron-Modell visualisieren wurde eine andere interessante Teil des Projekts.

## <a name="design"></a>Entwurf

Für die Standardansicht der Tabelle periodisch undenkbar ich dreidimensionalen Felder, die den Electron-Modell der einzelnen Elemente enthält. Die Oberfläche des jedes Feld wäre, sodass der Benutzer eine grobe Vorstellung des Elements Volumes konnte lichtdurchlässiger. Mit Blicke "und" Air-tippen kann der Benutzer eine detaillierte Ansicht der einzelnen Elemente öffnen. Um den Übergang zwischen Tabelle und Detailansicht smooth und natürliche machen, war ich es vergleichbar mit der physischen Interaktion eines Felds aus, öffnen in der Praxis.

![Design-Sketches](images/640px-sketch20170406.jpg)<br>
*Entwurf einen groben Entwurf*

In der Detailansicht wollte ich die Informationen der einzelnen Elemente mit beeindruckend dargestellte Text im 3D-Raum zu visualisieren. Das animierte 3D Electron-Modell wird im mittleren Bereich angezeigt, und es kann aus verschiedenen Blickwinkeln angezeigt werden.

![Interaktion](images/640px-periodictable-interaction.jpg)

![Prototypen](images/640px-periodictable-prototypes.jpg)<br>
*Interaktion von Prototypen*

Der Benutzer kann den Surface-Typ in der Luft durch Tippen auf die Schaltflächen am unteren Rand der Tabelle ändern: sie können zwischen Plane, Zylinder, Kugel und Punkt (XY) wechseln.

## <a name="common-controls-and-patterns-used-in-this-app"></a>Allgemeine Steuerelemente und Muster, die in dieser app verwendet werden.

### <a name="interactable-object-button"></a>Es Objekt (Schaltfläche)

[Es Objekt](interactable-object.md) ist ein Objekt, das grundlegende HoloLens Eingaben reagieren kann. Er wird als Prefab/Skript bereitgestellt, die einfach auf ein beliebiges Objekt angewendet werden können. Sie können z. B. stellen eine Tasse Kaffee für die es in Ihrer Szene und reagieren auf Eingaben wie z. B. Blicke, tippen Sie auf, die Datennavigation und-Bearbeitung Gesten. [Weitere Informationen](interactable-object.md)

![Nteractable-Objekt](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>Eine objektauflistung

[-Objektauflistung](object-collection.md) ist ein Objekt, das die können Sie mehrere Objekte in verschiedenen Formen anordnen. Datenebene, Zylinder, Kugel und Punkt (XY) unterstützt. Sie können zusätzliche Eigenschaften wie z. B. Radius, Anzahl der Zeilen und den Abstand konfigurieren. [Weitere Informationen](object-collection.md)

![Eine objektauflistung](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a>Fitbox

In der Standardeinstellung die Hologramme platziert werden, an dem Speicherort, in denen der Benutzer gazing ist, derzeit die Anwendung wird gestartet. Dies führt gelegentlich zu unerwünschten Ergebnis wie z. B. Hologramme hinter einer Wand oder in der Mitte einer Tabelle platziert wird. Eine Fitbox kann einen Benutzer Blicke zu verwenden, um den Speicherort zu bestimmen, in denen die Hologramm platziert werden. Es erfolgt mit einer einfachen PNG-Bild-Textur, die problemlos mit Ihrer eigenen Images oder 3D-Objekte angepasst werden können.

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a>Technische Details

Finden Sie Skripts und prefabs (Vorlagen) für die Tabelle periodisch der app Elemente auf der [Mixed Reality-Design-Labs-GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).

## <a name="application-examples"></a>Beispiele für die Anwendung

Hier sind einige Ideen für das was Sie durch die Nutzung der Komponenten in diesem Projekt erstellen können.

### <a name="stock-data-visualization-app"></a>Vordefinierte datenvisualisierungs-app

Verwenden die gleichen Steuerelemente und das Interaktionsmodell, wie in der Tabelle periodisch des Beispiels Elemente, können Sie eine app erstellen, die Börsendaten visualisiert. Dieses Beispiel verwendet die Steuerung der Datensammlung Objekt, um das Layout von Aktiendaten in einer sphärischen Form. Sie können es sich um eine Detailansicht vorstellen, wo zusätzliche Informationen zu jeder Aktie auf interessante Weise angezeigt werden kann.

![Beispiel: Finance (1 von 3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![Beispiel: Finance (2 von 3)](images/640px-periodictable-applicationexamples-finance2.jpg)

![Beispiel: Finance (3 von 3)](images/640px-periodictable-applicationexamples-finance3.jpg)<br>
*Verdeutlicht, wie die objektauflistung, die in der Tabelle periodisch Elemente-Beispiel-App verwendet, in einer Finance-app verwendet werden kann*

### <a name="sports-app"></a>Sport-app

Dies ist ein Beispiel mit objektauflistung und anderen Komponenten aus der Tabelle periodisch der Beispiel-app Elemente Sport-Daten zu visualisieren.

![Beispiel: Sport (1 von 3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![Beispiel: Sport (2 von 3)](images/640px-periodictable-applicationexamples-sports1.jpg)

![Beispiel: Sport (3 von 3)](images/640px-periodictable-applicationexamples-sports3.jpg)<br>
*Ein Beispiel für die objektauflistung wie in der Tabelle periodisch die Beispiel-Appcould Elemente verwendet, die in einer Sport-app verwendet werden*

## <a name="about-the-author"></a>Der Autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>UX-Designer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch

* [Es-Objekt](interactable-object.md)
* [Eine objektauflistung](object-collection.md)
