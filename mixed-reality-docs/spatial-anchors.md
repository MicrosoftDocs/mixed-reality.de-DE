---
title: Raumanker
description: Bewährte Methoden für die Verwendung von Raumankern zum Rendern stabiler Hologramme.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Koordinatensystem, Raumkoordinatensystem, Weltmaßstab, Welt, Maßstab, Position, Ausrichtung, Anker, Raumanker, weltumschlossen, weltumschließend, Beständigkeit, Freigabe
ms.openlocfilehash: 16165194d040ad22f7885897eddcc65cf9dcaec3
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730861"
---
# <a name="spatial-anchors"></a>Raumanker

Ein Raumanker stellt einen wichtigen Punkt in der Umgebung dar, den das System im Laufe der Zeit nachverfolgen sollte. Jeder Anker verfügt über ein [Koordinatensystem](coordinate-systems.md), das sich im Verhältnis zu anderen Ankern oder Bezugsrahmen nach Bedarf anpasst, um sicherzustellen, dass verankerte Hologramme präzise an ihrem Platz bleiben.  Wenn Sie ein Hologramm im Koordinatensystem eines Ankers rendern, erhalten Sie die exakteste Positionierung für dieses Hologramm zu einem bestimmten Zeitpunkt. Dies geht zu Lasten kleiner Anpassungen im Laufe der Zeit in Bezug auf die Position des Hologramms, da das System es im Vergleich zur realen Welt kontinuierlich wieder an seinen Platz bewegt.

Sie können Raumanker auch über App-Sitzungen hinweg und geräteübergreifend beibehalten und freigeben:
* Indem Sie lokale Raumanker auf dem Datenträger speichern und später wieder laden, kann Ihre App über mehrere App-Sitzungen hinweg auf einem einzelnen HoloLens-Gerät etwa denselben Standort in der realen Welt ermitteln.
* Indem Sie <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> verwenden, um einen Cloudanker zu erstellen, kann Ihre Anwendung einen Raumanker über mehrere HoloLens-, iOS- und Android-Geräte hinweg teilen. Indem jedes Gerät ein Hologramm mit demselben Raumanker rendert, wird das Hologramm in der realen Welt für alle Benutzer an der gleichen Stelle angezeigt.  Dies ermöglicht gemeinsame Erfahrungen in Echtzeit.
* Sie können <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> auch für die asynchrone Hologrammpersistenz auf HoloLens-, iOS- und Android-Geräten verwenden.  Durch die gemeinsame Nutzung eines dauerhaften Cloudraumankers können mehrere Geräte dasselbe persistierte Hologramm im Verlauf der Zeit beobachten, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.

Für Erfahrungen im Stand- oder Raummaßstab für verbundene Desktopheadsets, die innerhalb eines Durchmessers von 5 Metern verbleiben, können Sie in der Regel anstelle von Raumankern einfach den [Plattformbezugsrahmen](coordinate-systems.md#stage-frame-of-reference) verwenden, wodurch Sie ein einzelnes Koordinatensystem erhalten, in dem Sie alle Inhalte rendern können. Wenn Ihre App jedoch beabsichtigt, Benutzer mehr als 5 Meter mit HoloLens umhergehen zu lassen, z. B. auf einer ganzen Etage eines Gebäudes, benötigen Sie Raumanker, damit der Inhalt an einer festen Position bleibt.

Obwohl Raumanker ideal für Hologramme sind, die in der Umgebung verankert bleiben sollen, kann ein Anker nach der Positionierung nicht mehr bewegt werden. Es gibt Alternativen zu Ankern, die besser für dynamische Hologramme geeignet sind, die zusammen mit dem Benutzer markiert werden sollten. Dynamische Hologramme sollten am besten mit einem stationären Bezugsrahmen (die Grundlage für die Weltkoordinaten von Unity) oder einem angefügten Bezugsrahmen positioniert werden.

## <a name="best-practices"></a>Empfohlene Methoden

Diese Richtlinien für Raumanker helfen Ihnen, stabile Hologramme zu rendern, die die reale Welt präzise nachverfolgen.

### <a name="create-spatial-anchors-where-users-place-them"></a>Erstellen von Raumankern, wo sie vom Benutzer platziert werden

Raumanker sollten in den meisten Fällen explizit von Benutzern platziert werden.

Bei HoloLens kann eine App z. B. den Strahl des Benutzers zum [Anvisieren](gaze.md) mit dem Gittermodell zur [räumlichen Abbildung](spatial-mapping.md) kreuzen, damit der Benutzer entscheiden kann, wo ein Hologramm platziert werden soll. Wenn der Benutzer zum Platzieren des Hologramms tippt, erstellen Sie einen Raumanker am Schnittpunkt und platzieren dann das Hologramm am Ursprung des Koordinatensystems dieses Ankers.

Lokale Raumanker können einfach und schnell erstellt werden, und das System konsolidiert seine internen Daten, wenn mehrere Anker seine zugrunde liegenden Sensordaten gemeinsam nutzen können. Sie sollten normalerweise einen neuen lokalen Raumanker für jedes Hologramm erstellen, das von einem Benutzer explizit platziert wird, außer in den unten beschriebenen Situationen, z. B. bei starren Gruppen von Hologrammen.

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>Verankerte Hologramme immer innerhalb von 3 Metern von ihrem Anker rendern

Raumanker stabilisieren ihr Koordinatensystem in der Nähe des Ankerursprungs. Wenn Sie Hologramme mehr als etwa 3 Meter von diesem Ursprung entfernt rendern, können diese Hologramme aufgrund von Hebelarmeffekten spürbare Positionsfehler im Verhältnis zu ihrem Abstand von diesem Ursprung aufweisen. Das funktioniert, wenn der Benutzer in der Nähe des Ankers steht, da das Hologramm auch weit vom Benutzer entfernt ist, was bedeutet, dass der Winkelfehler des entfernten Hologramms klein ist. Wenn der Benutzer jedoch zu diesem fernen Hologramm geht, wird es auf ihn sehr groß wirken, sodass die Hebelarmeffekte des fernen Ankerursprungs deutlich werden.

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>Gruppieren von Hologrammen, die einen starren Cluster bilden sollen

Mehrere Hologramme können denselben Raumanker teilen, wenn die App erwartet, dass diese Hologramme feste Beziehungen untereinander unterhalten.

Wenn Sie z. B. ein holografisches Sonnensystem in einem Raum animieren, ist es besser, alle Objekte des Sonnensystems an einen einzelnen Anker im Zentrum zu binden, damit sie sich zueinander relativ reibungslos bewegen können. In diesem Fall wird das gesamte Sonnensystem verankert, auch wenn sich seine Komponenten dynamisch um den Anker bewegen.

Der wichtigste Vorbehalt bei der Aufrechterhaltung der Hologrammstabilität besteht darin, dass die obige 3-Meter-Regel befolgt wird.

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>Hochdynamische Hologramme mit dem stationären Bezugsrahmen anstatt mit einem lokalen Raumanker rendern

Wenn Sie über ein hochdynamisches Hologramm verfügen, z. B. eine im Raum herumlaufende Gestalt oder eine schwebende Benutzeroberfläche, die entlang der Wand in der Nähe des Benutzers verläuft, ist es am besten, lokale Raumanker zu überspringen und diese Hologramme direkt in das Koordinatensystem zu rendern, das vom [stationären Bezugsrahmen](coordinate-systems.md#stationary-frame-of-reference) bereitgestellt wird (in Unity erreichen Sie dieses Verhalten, indem Sie Hologramme direkt in Weltkoordinaten ohne WorldAnchor platzieren). Hologramme in einem stationären Bezugsrahmen können eine Abweichung erfahren, wenn der Benutzer weit vom Hologramm entfernt ist, aber dies ist bei dynamischen Hologrammen weniger wahrscheinlich: Entweder bewegt sich das Hologramm ohnehin ständig, oder seine Bewegung hält es ständig in der Nähe des Benutzers, wo die Abweichung minimiert wird.

Ein interessanter Fall von dynamischen Hologrammen ist ein Objekt, das von einem verankerten Koordinatensystem zum anderen animiert wird. Beispiel: Zwei Burgen stehen 10 Meter von einander entfernt und jede verfügt über einen eigenen Raumanker, wobei von einer Burg aus eine Kanonenkugel auf die andere Burg abgefeuert wird. In dem Moment, in dem die Kanonenkugel abgefeuert wird, können Sie sie an der geeigneten Stelle im stationären Bezugsrahmen rendern, sodass sie mit der Kanone im verankerten Koordinatensystem der ersten Burg übereinstimmt. Im stationären Bezugsrahmen kann sie dann ihrer Flugbahn folgen, wenn sie 10 Meter durch die Luft fliegt. Wenn die Kanonenkugel die andere Burg erreicht, können Sie sie in das verankerte Koordinatensystem der zweiten Burg verschieben, um physikalische Berechnungen mit den Starrkörpern dieser Burg zu ermöglichen.

Wenn Sie ein hochdynamisches Hologramm geräteübergreifend freigeben, müssen Sie einen Cloudraumanker auswählen, der als übergeordnetes Element fungiert, da stationäre Bezugsrahmen nicht geräteübergreifend freigegeben werden können.  In diesem Fall sollten Sie jedoch sicherstellen, dass entweder das dynamische Hologramm oder die Geräte, die es betrachten, innerhalb des Radius von 3 Metern des Ankers verbleiben, um sicherzustellen, dass das Hologramm auf allen Geräten stabil angezeigt wird.

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>Vermeiden der Erstellung eines Rasters von Raumankern

Sie können dazu geneigt sein, dass Ihre App ein regelmäßiges Raster von Raumankern erstellt, während der Benutzer umhergeht und dynamische Objekte von Anker zu Anker überführt, während diese sich bewegen. Dies erfordert jedoch einen hohen Verwaltungsaufwand für Ihre App, ohne den Vorteil der umfassenden Sensordaten, die das System selbst intern verwaltet. In diesen Fällen erzielen Sie in der Regel bessere Ergebnisse mit weniger Aufwand, indem Sie Ihre Hologramme im stationären Bezugsrahmen platzieren, wie im vorherigen Abschnitt beschrieben.

Wenn Sie einen Satz von Cloudraumankern vorab um einen statischen Bereich herum positionieren, sollten Sie erwägen, die Raumanker an den Positionen der Schlüsselhologramme zu platzieren, auf die der Benutzer gemäß dem obigen Prinzip stoßen wird, anstatt ein beliebiges Ankerraster zu erstellen.  Dadurch wird sichergestellt, dass Sie die maximale Stabilität für diese Schlüsselhologramme erhalten.

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>Freigeben lokaler Raumanker, die nicht länger benötigt werden

Während ein lokaler Raumanker aktiv ist, priorisiert das System die Verwaltung der Sensordaten, die sich in der Nähe dieses Ankers befinden. Wenn Sie keinen Raumanker mehr verwenden, stoppen Sie den Zugriff auf dessen Koordinatensystem. Dadurch können die zugrunde liegenden Sensordaten bei Bedarf entfernt werden.

Dies ist insbesondere für lokale Anker wichtig, die Sie im Raumankerspeicher aufbewahrt haben. Die Sensordaten hinter diesen Ankern werden dauerhaft gespeichert, damit Ihre App diesen Anker in zukünftigen App-Sitzungen finden kann, wodurch der zur Nachverfolgung anderer Anker verfügbare Platz reduziert wird. Verwahren Sie nur die lokalen Anker, die Sie in zukünftigen Sitzungen wiederfinden müssen, und entfernen Sie sie aus dem Speicher, wenn sie für den Benutzer keine Bedeutung mehr haben.

Bei Cloudraumankern kann Ihr Speicher entsprechend den Anforderungen Ihres Szenarios skaliert werden.  Sie können beliebig viele Cloudanker speichern und diese nur dann freigeben, wenn Sie wissen, dass Ihre Benutzer Hologramme nicht erneut bei diesem Anker suchen müssen.

## <a name="see-also"></a>Weitere Informationen
* [Koordinatensysteme](coordinate-systems.md)
* [Gemeinsame Erlebnisse in Mixed Reality](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [Persistenz in Unity](persistence-in-unity.md)
* [Raumanker in DirectX](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [Fallstudie – Schauen durch Löcher in Ihrer Realität](case-study-looking-through-holes-in-your-reality.md)
