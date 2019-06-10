---
title: App-Leiste und das umgebende Feld
description: Die App-Leiste ist ein auf Objektebene Menü mit einer Reihe von Schaltflächen, die auf dem unteren Rand der ggf. ein Hologramm Begrenzungen angezeigt.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, App-Leiste, umgebendes Feld
ms.openlocfilehash: ab472e1c988e6bdfb0a69d90e90280082b3db759
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813847"
---
# <a name="bounding-box-and-app-bar"></a>Umgebendes Feld und App-Leiste
![Begrenzen, ist die Standardschnittstelle für die Bearbeitung des Objekts in Mixed Reality.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a>Was ist das umgebende Feld?

Begrenzen, ist die Standardschnittstelle für die Bearbeitung des Objekts in Mixed Reality. Es bietet dem Benutzer eine Unterstützung, dass das Objekt derzeit überhaupt angepasst werden kann. Die Ecken, wird dem Benutzer mitgeteilt, dass das Objekt auch skalieren kann. Dieser visuelle Unterstützung zeigt Benutzer die Gesamtfläche des Objekts – auch wenn es nicht außerhalb einer Anpassung Modus angezeigt wird. Dies ist besonders wichtig, da ein Objekt, das an einem anderen Objekt oder Fläche Rasterlinie ausgerichtet, wenn er nicht vorhanden wäre, so verhält, als gäbe Platz um es herum, die es sollte nicht angezeigt werden kann. HoloLens-2 das umgebende Feld arbeitet mit direkten manuell bearbeiten und reagiert auf dem Finger des Benutzers die Nähe. Es zeigt visuelles Feedback den Benutzer, der den Abstand zwischen dem Objekt wahrnehmen können. 

![HoloLens-von-Sicht der Skalierung eines Objekts über umgebendes Feld](images/HoloLens2_BoundingBox.gif)<br>
*Die Skalierung eines Objekts über umgebendes Feld*

Die Handles in den Ecken des Begrenzungsrahmens führen Sie ein allgemein verstanden Muster für die Skalierung anpassen. 

![HoloLens-von-Sicht der Drehen eines Objekts über umgebendes Feld](images/HoloLens2_BoundingBox_Rotate.gif)<br>
*Drehen eines Objekts über umgebendes Feld*


![Visuelles Feedback auf der Hand NEAR](images/HoloLens2_Proximity.gif)<br>
*Visuelles Feedback auf der Grundlage der Nähe*

Die vertikale rechteckigen visueller Hinweise an den Rändern des umgebenden Felds handelt es sich um Drehung Indikatoren. Dadurch erhalten Benutzer weitere Feineinstellung über ihre Hologramme platziert. Nicht nur können sie anpassen und skalieren, aber jetzt auch drehen.

* Unity-app-Entwicklung, finden Sie unter [umgebendes Feld auf Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)



## <a name="what-is-the-app-bar"></a>Was ist der App-Leiste?

Die App-Leiste ist ein auf Objektebene Menü mit einer Reihe von Schaltflächen, die auf dem unteren Rand der ggf. ein Hologramm Begrenzungen angezeigt. Dieses Muster wird häufig verwendet, um Benutzern die Möglichkeit, zu entfernen, und passen Sie Hologramme zu ermöglichen.

Da dieses Muster mit Objekten, die Welt gesperrt verwendet wird, wie ein Benutzer auf das Objekt bewegt wird die App-Leiste immer auf der Objekte neben dem Benutzer angezeigt. Während dies billboarding nicht ist, wird das gleiche Ergebnis effektiv erreicht; verhindert, dass Position verdeckt eines Benutzers oder der Block-Funktionen, die andernfalls von einem anderen Speicherort in ihrer Umgebung zur Verfügung stehen würden.

![Um ggf. ein Hologramm durchlaufen. Die App-Leiste folgt.](images/HoloLens2_AppBarFollowing.gif)<br>
*Durchlaufen, um ggf. ein Hologramm, folgt die App-Leiste*

Die App-Leiste wurde in erster Linie als eine Möglichkeit zum Verwalten der platzierten Objekte in der Umgebung eines Benutzers entwickelt. Gekoppelt mit das umgebende Feld, ein Benutzer verfügt über Vollzugriff auf, wo und wie Objekte in mixed Reality ausgerichtet werden.

* Unity-app-Entwicklung, finden Sie unter [App-Leiste auf Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)

## <a name="see-also"></a>Siehe auch
* [Interaktionsfähiges Objekt](interactable-object.md)
* [Text in Unity](text-in-unity.md)
* [Objektsammlung](object-collection.md)
* [Anzeigen des Fortschritts](progress.md)
