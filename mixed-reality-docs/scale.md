---
title: Skalierung
description: Eine Taste, um die Anzeige von Inhalten, die realistische holographic Format aussieht ist, um die visual Statistiken der realen Welt so weit wie möglich zu imitieren.
author: mavitazk
ms.author: mavitazk
ms.date: 03/21/2018
ms.topic: article
keywords: Entwerfen von Windows Mixed Reality, Stil,
ms.openlocfilehash: f13414bff7d84692e8e87aa2abdcded15627346f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593792"
---
# <a name="scale"></a>Skalierung

Eine Taste, um die Anzeige von Inhalten, die realistische holographic Format aussieht ist, um die visual Statistiken der realen Welt so weit wie möglich zu imitieren. Dies bedeutet, integrieren so viele der visuellen Hinweise wie möglich, die uns dabei, (in der Praxis helfen), in denen Objekte sind, wie groß, und was sie zu bieten haben. Die Größe eines Objekts ist eine der wichtigsten von dieser visuelle Hinweise, die einem Viewer eine Vorstellung von der Größe eines Objekts sowie Hinweise auf den Speicherort (insbesondere bei Objekten, die eine bekannte Größe haben) gewähren. Darüber hinaus kann das Anzeigen von Objekten in tatsächlichen Umfang angezeigt werden, eines der wichtigsten Erfahrungen Unterscheidungsmerkmale für Realität in der Regel – etwa im gemischten, die nicht auf zuvor anzeigen bildschirmbasierte möglich wurde.

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>Wie Sie die Skalierung von Objekten und Umgebungen vorschlagen

Es gibt viele Möglichkeiten zum Vorschlagen von der Skala eines Objekts, von die einige mögliche Auswirkungen auf andere Faktoren wahrnehmungen ausgeführt haben. Der Schlüssel ist einfach Objekte in einem "echten" Größe angezeigt und realistische Größe verwalten, wie der Benutzer verschieben. Dies bedeutet, dass eine unterschiedliche Menge an visual Winkel des Benutzers, eines Benutzers Hologramme einnehmen werden, wie sie näher oder weiter entfernt, die gleiche Weise, die echte Objekte.

### <a name="utilize-the-distance-of-objects-as-they-are-presented-to-the-user"></a>Verwenden Sie den Abstand der Objekte, wie sie dem Benutzer angezeigt werden

Eine gängige Methode ist den Abstand der Objekte zu verwenden, wie sie dem Benutzer angezeigt werden. Betrachten Sie beispielsweise die Visualisierung eines großen Familien Autos vor dem Benutzer. Wäre das Auto direkt vor ihnen innerhalb von Arm-Länge, wäre es zu groß für im Lesebereich des Benutzers. Dies müsste den Benutzer die Haupt- und des Texts zu verstehen, das Objekt während des gesamten Entwicklungsprozesses zu verschieben. Wenn das Fahrzeug weiter entfernt (durch das Zimmer) eingefügt wurden, kann der Benutzer einen Eindruck von der Größe einrichten, indem das Objekt im jeweiligen Lesebereich, während des gesamten Entwicklungsprozesses angezeigt verschieben näher ist selbst dann, um Bereiche im Detail zu untersuchen.

[Volvo](https://www.youtube.com/watch?v=DilzwF90vec) verwendet dieses Verfahren zum Erstellen einer Ausstellungsraum-Umgebung für ein neues Auto, nutzen die Skalierung des holographic Autos in einer Weise, die realistischer und intuitiver für den Benutzer halte. Die Umgebung beginnt mit ggf. ein Hologramm des Autos für eine physische Tabelle, damit der Benutzer die Größe und Form des Modells zu verstehen. Weiter unten in der Oberfläche Autos wird auf einem größeren Rahmen (über die Größe des Geräts in dessen Sichtfeld) erweitert, aber da der Benutzer einen Bezugsrahmen aus dem kleineren Modell bereits erworben haben, können sie angemessen Navigieren in die Features des Autos.

![Volvo Autos-Erfahrung für HoloLens](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
*Volvo Autos-Erfahrung für HoloLens*

### <a name="use-holograms-to-modify-the-users-real-space"></a>Verwenden Sie Hologramme so ändern Sie den tatsächlichen Speicherplatz des Benutzers

Eine andere Methode ist die Verwendung Hologramme um des Benutzers echte Speicherplatz, und Ersetzen der vorhandenen Wände oder Obergrenzen in Umgebungen oder Anfügen von "Lücken" oder "Windows", sodass übermäßig große Objekten, scheinbar "Break-der physische Speicherplatz durch" zu ändern. Z. B. ein großer Baum möglicherweise nicht im Wohnzimmer für die meisten Benutzer geeignet, aber von einem virtuellen Himmel auf ihren Höchstwert ablegen, der physische Speicherplatz wird erweitert, die virtuelle. Dadurch kann der Benutzer aufzusuchen, der Basis der virtuellen Struktur, und erfassen einen Eindruck von der Größe des wie es würde in der Praxis angezeigt werden, und suchen Sie es weit über den Raum des Raums hinausgehen, finden Sie unter.

[Minecraft](https://minecraft.net/) ein Konzept-Erlebnis, das über eine ähnliche Technik entwickelt. Ein virtuelles Fenster einer physischen Oberfläche in einem Raum hinzufügen, werden die vorhandenen Objekte im Raum im Kontext einer erheblich größere Umgebung, über die physischen skalierungseinschränkungen des Raums platziert.

![Minecraft-Concept-Umgebung für HoloLens](images/800px-minecraftwindow-640px.jpg)<br>
*Minecraft-Concept-Umgebung für HoloLens*

## <a name="experimenting-with-scale"></a>Experimentieren mit der Skalierung

In einigen Fällen erprobt Designer haben eine Änderung der Skalierung (durch Ändern der angezeigten "echten" Größe des Objekts) und gleichzeitig eine einzelne Position des Objekts, um ein Objekt, das erste näher oder weiter auf einen Viewer aus, ohne eine tatsächliche Bewegung zu ermitteln. Dies wurde in einigen Fällen als eine Möglichkeit zum Simulieren von Nahaufnahme der Anzeige von Elementen möglichen bequem Einschränkungen zum Anzeigen von virtuellen Inhalte näher als "Zone der Komfort" schlage weiterhin zu nutzen und gleichzeitig getestet.

Dies kann jedoch einige mögliche Elemente in der Umgebung erstellen:
* Virtuelle Objekte, die ein Objekt mit einer Größe "bekannte" in der Ereignisanzeige darstellen, eine Änderung der Skalierung ohne Ändern der Position zu in Konflikt stehende visuelle Hinweise führt – die Augen möglicherweise immer noch "finden Sie unter" das Objekt auf eine Ebene aufgrund Vergence Hinweise (finden Sie unter den [Komfort ](comfort.md) Artikel Weitere Informationen zu diesem), aber die Größe fungiert als monokularen Hinweis, der das Objekt möglicherweise näher ab. Diese in Konflikt stehende Hinweise dazu führen, dass verwechselt Sichtweise – Viewer häufig finden Sie unter dem Objekt als direktes (aufgrund der Konstante Tiefe Cue) bleiben jedoch wächst rasant.
* In einigen Fällen wird die Änderung der Skalierung Stichwort "derzeit" angezeigt, stattdessen, in dem das Objekt kann, oder möglicherweise nicht so ändern Sie die Skalierung von einem Viewer angezeigt werden, aber ist anscheinend Umstellung direkt auf den Betrachter (die eine bedauernswerte Riesenerfolg sein kann).
* Mit Vergleich Oberflächen in der Praxis sind manchmal Skalierung Änderungen wie das Ändern der Position, an mehrere Achsen sichtbar – Objekte niedriger nicht verschieben, näher löschen angezeigt werden können (ähnlich wie in einer Projektion 2D, 3D datenverschiebung in einigen Fällen).
* Schließlich für Objekte ohne eine bekannte "real World"-Größe (z. B. willkürlichen Formen mit beliebiger Größe, die Elemente der Benutzeroberfläche usw.), Ändern der Skalierung funktional fungieren kann, als eine Möglichkeit, Änderungen in der Entfernung zu imitieren – die Viewer müssen nicht so viele bereits vorhandene Hinweise von oben nach unten, um Verstehen Sie wirkliche Größe oder Speicherort des Objekts, damit die Skalierung als ein wichtiger Hinweis verarbeitet werden kann.

## <a name="see-also"></a>Siehe auch
* [Farbe, helle und Materialien](color,-light-and-materials.md)
* [Typography](typography.md)
* [Räumliche Entwurf](spatial-sound-design.md)
