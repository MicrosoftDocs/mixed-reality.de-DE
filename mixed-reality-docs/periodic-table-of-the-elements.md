---
title: Periodensystem der Elemente
description: Die periodische Tabelle der Elemente ist eine Open-Source-Beispiel-App aus der Mixed Reality Design Labs von Microsoft, in der Sie erfahren, wie Sie mithilfe einer Objekt Auflistung ein Array von Objekten im 3D-Raum mit verschiedenen Oberflächentypen erstellen können.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Gemischte Windows-Realität, Entwurf, Beispiel-APP, Steuerelemente
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525349"
---
# <a name="periodic-table-of-the-elements"></a>Periodensystem der Elemente

>[!NOTE]
>In diesem Artikel wird ein exploratives Beispiel erläutert, das wir in den [Entwurfs Labors für gemischte Realität](https://github.com/Microsoft/MRDesignLabs_Unity)erstellt haben, einem Ort, an dem wir unsere Erkenntnisse und Vorschläge für die Entwicklung gemischter Reality-apps teilen. Unsere Entwurfs bezogenen Artikel und Code werden sich weiterentwickeln, wenn wir neue Ermittlungen durchführen.

[Die periodische Tabelle der Elemente](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) ist eine Open-Source-Beispiel-App aus den Mixed Reality-Entwurfs Labs von Microsoft. Mit diesem Projekt können Sie erfahren, wie Sie ein Array von Objekten im 3D-Raum mit verschiedenen Oberflächentypen mithilfe einer **[Objekt](object-collection.md)** Auflistung aufstellen. Außerdem wird beschrieben, wie Sie Objekt übergreifende Objekte erstellen, die auf Standard Eingaben aus hololens reagieren. Sie können die Komponenten dieses Projekts verwenden, um Ihre eigene Benutzeroberflächen Funktion für gemischte Realität zu erstellen.

![Period-Tabelle der Elements-App](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a>Informationen zur APP

Eine periodische Tabelle der Elemente visualisiert die chemischen Elemente und ihre Eigenschaften in einem 3D-Raum. Es umfasst die grundlegenden Interaktionen von hololens, wie z. b. "Blick" und "Air Tap Benutzer können sich über die Elemente mit animierten 3D-Modellen informieren. Sie können die Elektronen Shell eines Elements und den Kern, der aus den Protonen und den neutralen besteht, visuell verstehen.

## <a name="background"></a>Hintergrund

Nachdem ich die ersten hololens erlebt habe, war eine regelmäßige Tabellen-App eine Idee, mit der ich wusste, dass ich in gemischter Realität experimentieren wollte. Da jedes Element viele Datenpunkte enthält, die mit Text angezeigt werden, dachte ich, dass es sich um die Untersuchung der typografischen Komposition in einem 3D-Raum handelt. Es war ein weiterer interessanter Bestandteil dieses Projekts, das-Elektronen Modell des Elements visuell darzustellen.

## <a name="design"></a>Entwurf

In der Standardansicht der periodischen Tabelle habe ich dreidimensionale Felder vorgestellt, die das Elektronen Modell der einzelnen Elemente enthalten würden. Die Oberfläche jedes Felds wäre über scheinend, sodass der Benutzer einen groben Überblick über das Volume des Elements erhalten könnte. Mit Blick und Luft tippen könnte der Benutzer eine ausführliche Ansicht der einzelnen Elemente öffnen. Um den Übergang zwischen der Tabellenansicht und der Detailansicht reibungslos und natürlich zu gestalten, habe ich die physische Interaktion eines Box-Öffnens in der Praxis ähnlich gestaltet.

![Entwurfsskizze](images/640px-sketch20170406.jpg)<br>
*Entwurfsskizzen*

In der Detailansicht wollte ich die Informationen jedes Elements mit schön gerendertem Text im 3D-Raum visualisieren. Das animierte 3D-Elektronen Modell wird im mittleren Bereich angezeigt und kann aus unterschiedlichen Winkeln angezeigt werden.

![Interaktion](images/640px-periodictable-interaction.jpg)

![Ty](images/640px-periodictable-prototypes.jpg)<br>
*Interaktions Prototypen*

Der Benutzer kann den Surface-Typ ändern, indem er auf die Schaltflächen am unteren Ende der Tabelle tippt. er kann Zwischenebene, Zylinder, Kugel und Punkt wechseln.

## <a name="common-controls-and-patterns-used-in-this-app"></a>In dieser APP verwendete allgemeine Steuerelemente und Muster

### <a name="interactable-object-button"></a>Interactable-Objekt (Schaltfläche)

Das [interactable-Objekt](interactable-object.md) ist ein Objekt, das auf grundlegende hololens-Eingaben reagieren kann. Sie wird als präfab/-Skript bereitgestellt, das Sie problemlos auf jedes beliebige Objekt anwenden können. Beispielsweise können Sie einen Kaffeebecher in der Szene in der Szene zusammenstellen und auf Eingaben wie z. b. Blick, Luft tippen, Navigation und Manipulations Gesten reagieren. [Weitere Informationen](interactable-object.md)

![nteractable-Objekt](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>Objektsammlung

Die [Objektsammlung](object-collection.md) ist ein Objekt, mit dem Sie mehrere Objekte in verschiedenen Formen anordnen können. Es unterstützt die Ebenen, Zylinder, Kugel und Punkt. Sie können zusätzliche Eigenschaften wie RADIUS, Anzahl der Zeilen und den Abstand konfigurieren. [Weitere Informationen](object-collection.md)

![Objektsammlung](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a>Fitbox

In der Standardeinstellung werden holograms an dem Speicherort abgelegt, an dem der Benutzer die Anwendung startet. Dies führt manchmal zu unerwünschten Ergebnissen, z. b. holograms, die hinter einer Wand oder in der Mitte einer Tabelle abgelegt werden. Eine fitbox-Funktion ermöglicht es einem Benutzer, die Position zu ermitteln, an der das – Hologramm platziert wird. Sie wird mit einer einfachen PNG-Bildtextur erstellt, die problemlos mit ihren eigenen Bildern oder 3D-Objekten angepasst werden kann.

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a>Technische Details

Sie finden Skripts und Prefabs für die periodische Tabelle der Elements-App auf dem [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).

## <a name="application-examples"></a>Anwendungsbeispiele

Im folgenden finden Sie einige Ideen für das, was Sie erstellen können, indem Sie die Komponenten in diesem Projekt nutzen.

### <a name="stock-data-visualization-app"></a>Daten Visualisierungs-App für Aktien

Wenn Sie die gleichen Steuerelemente und das Interaktionsmodell wie die periodische Tabelle des Elements Sample verwenden, können Sie eine APP erstellen, die die Daten von Aktienmärkten visualisiert. In diesem Beispiel wird das Objekt Auflistungs Steuerelement verwendet, um Aktiendaten in einer kugelförmigen Form anzuordnen. Sie können sich eine Detailansicht vorstellen, in der zusätzliche Informationen zu den einzelnen Aktien auf interessante Weise angezeigt werden können.

![Anwendungsbeispiel: Finanzen (1 von 3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![Anwendungsbeispiel: Finanzen (2 von 3)](images/640px-periodictable-applicationexamples-finance2.jpg)

![Anwendungsbeispiel: Finanzen (3 von 3)](images/640px-periodictable-applicationexamples-finance3.jpg)<br>
*Ein Beispiel dafür, wie die Objekt Auflistung, die in der periodischen Tabelle der Beispiel-App für Elemente verwendet wird, in einer Finance-App verwendet werden kann*

### <a name="sports-app"></a>Sport-App

Dies ist ein Beispiel für die Visualisierung von Sportdaten mithilfe der Objekt Auflistung und anderer Komponenten aus der periodischen Tabelle der Elements-Beispiel-app.

![Anwendungsbeispiel: Sport (1 von 3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![Anwendungsbeispiel: Sport (2 von 3)](images/640px-periodictable-applicationexamples-sports1.jpg)

![Anwendungsbeispiel: Sport (3 von 3)](images/640px-periodictable-applicationexamples-sports3.jpg)<br>
*Ein Beispiel dafür, wie die Objekt Auflistung, die in der periodischen Tabelle des Elements Sample appused verwendet wird, in einer Sport-App verwendet werden kann.*

## <a name="about-the-author"></a>Informationen zum Autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong-Yoon-Park</b><br>UX-Designer@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch

* [Interaktionsfähiges Objekt](interactable-object.md)
* [Objektsammlung](object-collection.md)
