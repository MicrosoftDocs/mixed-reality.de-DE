---
title: App-Leiste und das umgebende Feld
description: Die App-Leiste ist ein auf Objektebene Menü mit einer Reihe von Schaltflächen, die auf dem unteren Rand der ggf. ein Hologramm Begrenzungen angezeigt.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, App-Leiste, umgebendes Feld
ms.openlocfilehash: bdce92e00193230d1f7a487f11ef0487f1d6657c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595301"
---
# <a name="bounding-box-and-app-bar"></a>Umgebendes Feld und App-Leiste
![Begrenzen, ist die Standardschnittstelle für die Bearbeitung des Objekts in Mixed Reality.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a>Was ist das umgebende Feld?

Begrenzen, ist die Standardschnittstelle für die Bearbeitung des Objekts in Mixed Reality. Es bietet dem Benutzer eine Unterstützung, dass das Objekt derzeit überhaupt angepasst werden kann. Die Ecken, wird dem Benutzer mitgeteilt, dass das Objekt auch skalieren kann. Dieser visuelle Unterstützung zeigt Benutzer die Gesamtfläche des Objekts – auch wenn es nicht außerhalb einer Anpassung Modus angezeigt wird. Dies ist besonders wichtig, da ein Objekt, das an einem anderen Objekt oder Fläche Rasterlinie ausgerichtet, wenn er nicht vorhanden wäre, so verhält, als gäbe Platz um es herum, die es sollte nicht angezeigt werden kann. Für HoloLens-2 antwortet das umgebende Feld des Benutzers des Fingers Nähe. Visuelles Feedback können Sie die Entfernung aus dem Objekt wahrgenommen werden. 

![HoloLens-von-Sicht der Skalierung eines Objekts über umgebendes Feld](images/bounding-box-scale.gif)<br>
*Die Skalierung eines Objekts über umgebendes Feld*

Die Cube-ähnliche Ecken des Begrenzungsrahmens führen Sie ein allgemein verstanden Muster für die Skalierung anpassen. Gekoppelt mit der expliziten Aktion ein Objekt in "Anpassen der Modus" platzieren, es ist klar, sie können sowohl das Objekt verschieben, aber es auch in ihrer Umgebung skalieren.

![HoloLens-von-Sicht der Drehen eines Objekts über umgebendes Feld](images/bounding-box-rotate.gif)<br>
*Drehen eines Objekts über umgebendes Feld*

Der sphärischen visueller Hinweise an den Rändern des umgebenden Felds handelt es sich um Drehung Indikatoren. Dadurch erhalten Benutzer weitere Feineinstellung über ihre Hologramme platziert. Nicht nur können sie anpassen und skalieren, aber jetzt auch drehen.

* Unity-app-Entwicklung, finden Sie unter [umgebendes Feld auf Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="what-is-the-app-bar"></a>Was ist der App-Leiste?

Die App-Leiste ist ein auf Objektebene Menü mit einer Reihe von Schaltflächen, die auf dem unteren Rand der ggf. ein Hologramm Begrenzungen angezeigt. Dieses Muster wird häufig verwendet, um Benutzern die Möglichkeit, zu entfernen, und passen Sie Hologramme zu ermöglichen.

Da dieses Muster mit Objekten, die Welt gesperrt verwendet wird, wie ein Benutzer auf das Objekt bewegt wird die App-Leiste immer auf der Objekte neben dem Benutzer angezeigt. Während dies billboarding nicht ist, wird das gleiche Ergebnis effektiv erreicht; verhindert, dass Position verdeckt eines Benutzers oder der Block-Funktionen, die andernfalls von einem anderen Speicherort in ihrer Umgebung zur Verfügung stehen würden.

![Um ggf. ein Hologramm durchlaufen. Die App-Leiste folgt.](images/holobar-followuser.gif)<br>
*Durchlaufen, um ggf. ein Hologramm, folgt die App-Leiste*

Die App-Leiste wurde in erster Linie als eine Möglichkeit zum Verwalten der platzierten Objekte in der Umgebung eines Benutzers entwickelt. Gekoppelt mit das umgebende Feld, ein Benutzer verfügt über Vollzugriff auf, wo und wie Objekte in mixed Reality ausgerichtet werden.

* Unity-app-Entwicklung, finden Sie unter [App-Leiste auf Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)

## <a name="see-also"></a>Siehe auch
* [Umgebendes Feld auf Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)
* [App-Leiste auf Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)
* [Es-Objekt](interactable-object.md)
* [Text in Unity](text-in-unity.md)
* [Eine objektauflistung](object-collection.md)
* [Anzeigen des Status](progress.md)
