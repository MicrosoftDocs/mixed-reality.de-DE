---
title: Begrenzungs Bereich und App-Leiste
description: Die APP-Leiste ist ein Menü auf Objektebene, das eine Reihe von Schaltflächen enthält, die am unteren Rand der Begrenzungen eines holograms angezeigt werden.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, App-Leiste, Begrenzungs Bereich
ms.openlocfilehash: d289be31129324c6ff419b69dbce52bd8f62eb64
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829685"
---
# <a name="bounding-box-and-app-bar"></a>Begrenzungs Bereich und App-Leiste
![Das Begrenzungs Zeichen ist die Standardschnittstelle für die Objekt Bearbeitung in gemischter Realität.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a>Was ist das umgebende Feld?

Das Begrenzungs Zeichen ist die Standardschnittstelle für die Objekt Bearbeitung in gemischter Realität. Der Benutzer erhält eine Kosten, die das Objekt momentan anpassbar ist. In den Ecken wird dem Benutzer mitgeteilt, dass das Objekt auch skaliert werden kann. Diese visuelle Visualisierung zeigt Benutzern den gesamten Bereich des Objekts an – auch dann, wenn Sie außerhalb eines Anpassungsmodus nicht sichtbar sind. Dies ist besonders wichtig, da das Objekt, das an ein anderes Objekt oder eine andere Oberfläche angedockt ist, sich so verhält, als ob es sich um ein Leerzeichen handelt, das nicht vorhanden sein sollte. Bei hololens 2 funktioniert das umgebende Feld mit direkter Hand Manipulation und antwortet auf die Nähe des Benutzers. Es zeigt visuelles Feedback, um dem Benutzer zu helfen, den Abstand zum Objekt zu erkennen. 

![Hololens zeigt das Skalieren eines Objekts über ein Begrenzungsfeld an](images/HoloLens2_BoundingBox.gif)<br>
*Skalieren eines Objekts per Begrenzungs Rahmen*

Die Handles in den Ecken des umgebenden Felds folgen einem weit verbreiteten Muster zur Anpassung der Skalierung. 

![Hololens-Sicht der Drehung eines Objekts über das umgebende Feld](images/HoloLens2_BoundingBox_Rotate.gif)<br>
*Drehen eines Objekts über ein Begrenzungs Fenster*


![Visuelles Feedback in der Nähe](images/HoloLens2_Proximity.gif)<br>
*Visuelles Feedback basierend auf der Nähe*

Die vertikalen rechteckigen Anlagen an den Rändern des umgebenden Felds sind Rotations Indikatoren. Dies ermöglicht dem Benutzer eine präzisere Anpassung der platzierten holograms. Sie können nicht nur angepasst und skaliert werden, sondern auch jetzt drehen.

* Informationen zur Entwicklung von Unity-apps finden Sie [im Thema zum umgebenden Feld in Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)



## <a name="what-is-the-app-bar"></a>Was ist die APP-Leiste?

Die APP-Leiste ist ein Menü auf Objektebene, das eine Reihe von Schaltflächen enthält, die am unteren Rand der Begrenzungen eines holograms angezeigt werden. Dieses Muster wird häufig verwendet, um Benutzern das Entfernen und Anpassen von holograms zu ermöglichen.

Da dieses Muster mit Objekten verwendet wird, die in der Welt gesperrt sind, wird die APP-Leiste immer auf der Seite der Objekte angezeigt, die dem Benutzer am nächsten ist, wenn sich der Benutzer um das Objekt bewegt wird. Obwohl dies kein Abgleich ist, erzielt es effektiv dasselbe Ergebnis. verhindern, dass die Position eines Benutzers Funktionen sperrt oder blockiert, die andernfalls an einem anderen Speicherort in Ihrer Umgebung verfügbar wären.

![Durchlaufen eines holograms. Die APP-Leiste folgt.](images/HoloLens2_AppBarFollowing.gif)<br>
*Wenn Sie ein Hologramm durchlaufen, folgt die APP-Leiste.*

Die APP-Leiste wurde primär als eine Möglichkeit zum Verwalten von platzierten Objekten in der Umgebung eines Benutzers entwickelt. In Verbindung mit dem umgebenden Feld hat ein Benutzer vollständige Kontrolle darüber, wo und wie Objekte in gemischter Realität ausgerichtet werden.

* Informationen zur Entwicklung von Unity-apps finden Sie [in der APP-Leiste unter Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)

## <a name="see-also"></a>Siehe auch
* [Interaktionsfähiges Objekt](interactable-object.md)
* [Text in Unity](text-in-unity.md)
* [Objektsammlung](object-collection.md)
* [Anzeigen des Fortschritts](progress.md)
