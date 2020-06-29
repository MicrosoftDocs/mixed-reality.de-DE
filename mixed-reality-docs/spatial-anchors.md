---
title: Raumanker
description: Bewährte Methoden für die Verwendung von Raumankern zum Rendern stabiler Hologramme.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Koordinatensystem, Raumkoordinatensystem, Weltmaßstab, Welt, Maßstab, Position, Ausrichtung, Anker, Raumanker, weltumschlossen, weltumschließend, Beständigkeit, Freigabe
ms.openlocfilehash: 8d270f96add795fdb54e0a91ebc9d38a34640da1
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85441787"
---
# <a name="spatial-anchors"></a>Raumanker

Ein räumlicher Anker stellt einen wichtigen Punkt in der Welt dar, den das System im Laufe der Zeit nachverfolgt. Jeder Anker verfügt über ein [Koordinatensystem](coordinate-systems.md), das sich im Verhältnis zu anderen Ankern oder Bezugsrahmen nach Bedarf anpasst, um sicherzustellen, dass verankerte Hologramme präzise an ihrem Platz bleiben.  Wenn Sie ein Hologramm im Koordinatensystem eines Ankers rendern, erhalten Sie die exakteste Positionierung für dieses Hologramm zu einem bestimmten Zeitpunkt. Dies bringt im Lauf der Zeit eine kleine Anpassung an die Position des holograms mit sich, da das System das System kontinuierlich wieder in Bezug auf die reale Welt verschiebt.

Sie können auch räumliche Anker für Anwendungs Sitzungen und Geräte übergreifend beibehalten und freigeben:
* Indem lokale räumliche Anker auf einem Datenträger gespeichert und später wieder geladen werden, kann die Anwendung denselben Speicherort in der realen Welt über mehrere Anwendungs Sitzungen hinweg in einem einzelnen hololens berechnen.
* Durch die Verwendung von <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial</a> Anchor zum Erstellen eines cloudankers kann Ihre Anwendung einen räumlichen Anker für mehrere hololens-, IOS-und Android-Geräte freigeben. Wenn jedes Gerät ein – Hologramm mithilfe desselben räumlichen Ankers erstellt, sehen Benutzer, dass das – Hologramm an derselben Stelle in der realen Welt angezeigt wird. Dies ermöglicht gemeinsame Erfahrungen in Echtzeit.
* Sie können <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> auch für die asynchrone Hologrammpersistenz auf HoloLens-, iOS- und Android-Geräten verwenden. Durch die gemeinsame Nutzung eines dauerhaften Cloudraumankers können mehrere Geräte dasselbe persistierte Hologramm im Verlauf der Zeit beobachten, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.

Für den Einsatz von Desktop-Headsets, die sich in einem Fünfdimensionalen Durchmesser befinden, können Sie in der Regel den [stagingframe von Reference](coordinate-systems.md#stage-frame-of-reference) anstelle räumlicher Anker verwenden, der ein einzelnes Koordinatensystem bereitstellt, in dem der gesamte Inhalt dargestellt werden kann. Wenn Ihre Anwendung es jedoch ermöglicht, dass Benutzer über 5 Meter in hololens hinaus bewegen können, was vielleicht in einem vollständigen Fußboden eines Gebäudes betrieben wird, benötigen Sie räumliche Anker, um Inhalte stabil zu halten.

Obwohl Raumanker ideal für Hologramme sind, die in der Umgebung verankert bleiben sollen, kann ein Anker nach der Positionierung nicht mehr bewegt werden. Es gibt Alternativen zu ankern, die für dynamische Hologramme geeignet sind, die mit dem Benutzer versehen werden. Dynamische Hologramme sollten am besten mit einem stationären Bezugsrahmen (die Grundlage für die Weltkoordinaten von Unity) oder einem angefügten Bezugsrahmen positioniert werden.

## <a name="best-practices"></a>Bewährte Methoden

Diese Richtlinien für Raumanker helfen Ihnen, stabile Hologramme zu rendern, die die reale Welt präzise nachverfolgen.

### <a name="create-spatial-anchors-where-users-place-them"></a>Erstellen von Raumankern, wo sie vom Benutzer platziert werden

Normalerweise platzieren Benutzer explizit räumliche Anker.

Beispielsweise kann eine Anwendung auf hololens den [Blick](gaze-and-commit.md) Strahl des Benutzers mit dem [räumlichen Mapping](spatial-mapping.md) -Mesh überschneiden, damit der Benutzer entscheiden kann, wo ein Hologram platziert werden soll. Wenn der Benutzer tippt, um dieses – Hologramm zu platzieren, erstellen Sie am schnittspunkt einen räumlichen Anker, und platzieren Sie dann das – Hologramm am Ursprung des Koordinatensystems dieses Ankers.

Lokale räumliche Anker sind einfach und leistungsfähig zum Erstellen. Das System konsolidiert seine internen Daten, wenn die zugrunde liegenden Sensordaten von mehreren Anker gemeinsam genutzt werden können. Sie sollten in der Regel einen neuen lokalen räumlichen Anker für jedes Hologramm erstellen, das ein Benutzer explizit platziert, außer in den nachstehend aufgeführten Fällen, wie z. b. feste Gruppen von holograms.

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>Verankerte Hologramme immer innerhalb von 3 Metern von ihrem Anker rendern

Raumanker stabilisieren ihr Koordinatensystem in der Nähe des Ankerursprungs. Wenn Sie holograms von diesem Ursprung aus um mehr als drei Meter Renderingvorgänge durchzuführen sind, können diese Hologramme aufgrund von Hebel-Arm-Effekten spürbare Positionsfehler im Verhältnis zur Entfernung von diesem Ursprung darstellen. Dies funktioniert, wenn der Benutzer in der Nähe des Ankers steht, da das – Hologramm auch weit entfernt ist. Anders ausgedrückt: der Angular-Fehler des entfernten holograms ist klein. Wenn der Benutzer jedoch zu diesem entfernten Hologram geht, ist er in seiner Ansicht groß, sodass die Auswirkungen der Hebel-Arm von der Entfernung des Ursprungs Ankers ganz offensichtlich sind.

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>Gruppieren von Hologrammen, die einen starren Cluster bilden sollen

Mehrere holograms können denselben räumlichen Anker gemeinsam verwenden, wenn die Anwendung erwartet, dass diese Hologramme eine fixierte Beziehung untereinander aufrechterhalten.

Wenn Sie z. b. ein Holographic-Sonnensystem in einem Raum animieren, ist es besser, alle Objekte des Sonnensystems an einen einzigen Anker in der Mitte zu binden, sodass Sie sich relativ zueinander reibungslos bewegen. In diesem Fall wird das gesamte Sonnensystem verankert, auch wenn sich seine Komponenten dynamisch um den Anker bewegen.

Der Schlüssel für die Beibehaltung der – Hologramm-Stabilität besteht darin, die drei Meter lange Regel zu befolgen.

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>Hochdynamische Hologramme mit dem stationären Bezugsrahmen anstatt mit einem lokalen Raumanker rendern

Wenn Sie über ein sehr dynamisches Hologram verfügen, z. b. ein Zeichen, das um einen Raum geht, oder eine unverankerte Benutzeroberfläche, die entlang der Wand in der Nähe des Benutzers folgt, empfiehlt es sich, lokale räumliche Anker zu überspringen und diese Hologramme direkt in dem Koordinatensystem zu erzeugen, das durch den [Rahmen der Referenz](coordinate-systems.md#stationary-frame-of-reference)bereitgestellt In Unity erreichen Sie dies, indem Sie holograms direkt in Weltkoordinaten ohne worldanchor platzieren. Bei holograms in einem stationären Verweis Rahmen kann es zu Abweichungen kommen, wenn der Benutzer weit vom Hologram abweicht. Dies ist jedoch weniger wahrscheinlich für dynamische Hologramme erkennbar: entweder wird das – Hologramm ständig ständig verschoben, oder die Bewegung hält den Benutzer ständig in der Nähe, wo Abweichungen minimiert werden.

Ein interessanter Fall von dynamischen Hologrammen ist ein Objekt, das von einem verankerten Koordinatensystem zum anderen animiert wird. Beispielsweise können Sie über zwei Burgen verfügen, die zehn Meter voneinander entfernt sind, und jeweils auf Ihrem eigenen räumlichen Anker, wobei eine Burg einen Cannonball auf der anderen Burg auslöst. Zu dem Zeitpunkt, an dem der Cannonball ausgelöst wird, können Sie ihn an der entsprechenden Stelle im stationären Frame des Verweises mit der Kanone im verankerten Koordinatensystem der ersten Burg Rendering. Im stationären Bezugsrahmen kann sie dann ihrer Flugbahn folgen, wenn sie 10 Meter durch die Luft fliegt. Wenn der Cannonball das andere Schloss erreicht, können Sie ihn in das verankerte Koordinatensystem der zweiten Burg verschieben, um die Physik-Berechnungen mit den starren Texten dieser Burg zuzulassen.

Wenn Sie ein äußerst dynamisches – Hologramm-Gerät für Geräte freigeben, müssen Sie ein räumliches cloudanker auswählen, das als übergeordnetes Element fungiert, da die Rahmen der Referenz nicht auf allen Geräten freigegeben werden können.  In diesem Fall sollten Sie jedoch sicherstellen, dass entweder das dynamische – Hologramm oder die Geräte, die Sie anzeigen, im 3-Meter-Radius des Ankers bleiben, um sicherzustellen, dass das – Hologramm auf allen Geräten stabil erscheint.

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>Vermeiden der Erstellung eines Rasters von Raumankern

Möglicherweise ist es verlockend, dass Ihre Anwendung ein reguläres Raster räumlicher Anker ablegen soll, während der Benutzer durchläuft, um dynamische Objekte vom Anker zum Anker zu bewegen, während Sie sich bewegen. Dies umfasst jedoch viel Verwaltungsaufwand für Ihre Anwendung, ohne dass die Tiefensensor Daten, die das System selbst intern verwaltet, genutzt werden. In diesen Fällen erzielen Sie in der Regel bessere Ergebnisse mit geringerem Aufwand, indem Sie Ihre Hologramme im stationären Frame des Verweises platzieren, wie im obigen Abschnitt beschrieben.
Erwägen Sie bei der Vorpositionierung eines Satzes von cloudanbietern um einen statischen Raum die räumlichen Anker an den Speicherorten der Schlüssel, die der Benutzer nach dem oben genannten Prinzip trifft, anstatt ein beliebiges Raster von Ankern zu erstellen. Dadurch wird sichergestellt, dass Sie die maximale Stabilität für diese Schlüsselhologramme erhalten.

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>Freigeben lokaler Raumanker, die nicht länger benötigt werden

Obwohl ein lokaler räumlicher Anker aktiv ist, priorisiert das System die Beibehaltung der Sensordaten, die sich in der Nähe des Ankers befinden. Wenn Sie keinen Raumanker mehr verwenden, stoppen Sie den Zugriff auf dessen Koordinatensystem. Dadurch können die zugrunde liegenden Sensordaten bei Bedarf entfernt werden.

Dies ist insbesondere für lokale Anker wichtig, die Sie im Raumankerspeicher aufbewahrt haben. Die Sensordaten hinter diesen ankern werden permanent aufbewahrt, damit Ihre Anwendung diesen Anker in zukünftigen Sitzungen finden kann, wodurch der zum Nachverfolgen anderer Anker verfügbare Speicherplatz reduziert wird. Behalten Sie nur die lokalen Anker bei, die Sie in zukünftigen Sitzungen erneut finden müssen, und entfernen Sie Sie aus dem Speicher, wenn Sie für den Benutzer nicht mehr von Bedeutung sind.

Bei Cloudraumankern kann Ihr Speicher entsprechend den Anforderungen Ihres Szenarios skaliert werden. Sie können beliebig viele cloudananker speichern und nur dann freigeben, wenn Sie wissen, dass die Benutzer nicht erneut holograms an diesem Anker finden müssen.

## <a name="see-also"></a>Siehe auch
* [Koordinatensysteme](coordinate-systems.md)
* [Gemeinsame Erlebnisse in Mixed Reality](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [Persistenz in Unity](persistence-in-unity.md)
* [Raumanker in DirectX](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [Fallstudie – Schauen durch Löcher in Ihrer Realität](case-study-looking-through-holes-in-your-reality.md)
