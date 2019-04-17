---
title: Räumliche Anker
description: Bewährte Methoden für die Verwendung von räumlichen Anker stabile Hologramme zu rendern.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Koordinatensystem, räumliche Koordinatensystem, weltweit einsetzbaren, Welt, skalieren, Position, Ausrichtung, Anker, räumliche Anker, Welt gesperrte, Welt-sperren, Dauerhaftigkeit, freigeben
ms.openlocfilehash: eb0fae7881f1b6517da57305ef2fa3cb1ed78648
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605105"
---
# <a name="spatial-anchors"></a>Räumliche Anker

Ein räumlicher Anker stellt einen wichtigen Punkt in der ganzen Welt, die das System nachverfolgen im Laufe der Zeit sollten dar. Jede Anker verfügt eine [Koordinatensystem](coordinate-systems.md) , das angepasst wird, relativ zu anderen Anker je nach Bedarf, oder platzieren Sie Bezugsrahmen, um sicherzustellen, dass verankerten Hologramme genau in bleiben.  Rendern ggf. ein Hologramm im Koordinatensystem der Anker bietet Ihnen die genaueste Positionierung für, – Hologramm zu jedem Zeitpunkt. Dies ist auf Kosten der kleinerer Anpassungen im Laufe der Zeit auf die Hologramm Position wie das System immer wieder zurück an die Stelle relativ zu der realen Welt verschoben wird.

Sie können auch beibehalten und Freigeben von räumlichen Anker über app-Sitzungen hinweg und auf Geräten:
* Lokale räumliche Anker Datenträger zu laden, die sie später wieder gespeichert werden, kann Ihre app über den gleichen Speicherort in der realen Welt über mehrere appsitzungen auf einem einzelnen HoloLens-Gerät Schlussfolgerungen aus.
* Mithilfe von <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure räumliche Anker</a> um eine Cloud Anchor zu erstellen, kann Ihre app als räumliche Anker dargestellt über mehrere HoloLens, iOS und Android-Geräte freigeben. Dass jedes Gerät, das Rendern ggf. ein Hologramm, der mit dem gleichen Anker für räumliche, sehen alle Benutzer der – Hologramm an derselben Stelle in der realen Welt angezeigt werden.  Dadurch können freigegebene ein Nutzererlebnis in Echtzeit.
* Können Sie auch <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure räumliche Anker</a> für asynchrone – Hologramm Persistenz für HoloLens, IOS- und Android-Geräte.  Freigeben einer permanenten räumliche cloudankers, können mehrere Geräte das gleiche persistente – Hologramm im Laufe der Zeit beobachten, auch wenn diese Geräte nicht zur gleichen Zeit zusammen vorhanden sind.

Ständigen Skalierung oder Skalierung Platz für verbundenen desktop Headsets-Funktionen zu nutzen, die in einem 5-Meter Durchmesser bleiben wird, können Sie in der Regel nur verwenden die [Phase Verweisrahmen](coordinate-systems.md#stage-frame-of-reference) anstelle von räumlichen Anker, bietet Ihnen eine einzelne Koordinatensystem, in dem gesamten Inhalt gerendert werden soll. Allerdings will, dass Ihre app nach 5-Zähler für HoloLens will, Benutzern zu ermöglichen, benötigen z. B. während einer gesamten Stockwerk eines Gebäudes Betrieb, räumliche verankert, Inhalt stabil zu halten Sie.

Räumliche Anker Hologramme geeignet sind, die in der Welt fixiert bleiben soll, sobald ein Anker platziert wird, kann es nicht verschoben werden. Es gibt Alternativen zu verankerungen, die für dynamische Hologramme besser geeignet sind, die zusammen mit der Benutzer markieren sollten. Es wird empfohlen, um dynamische Hologramme, die über eine feststehende Verweisrahmen (die Grundlage für die globale Koordinaten von Unity) oder eine angefügte Verweisrahmen zu positionieren.

## <a name="best-practices"></a>Empfohlene Methoden

Diese räumliche Anchor-Richtlinien können Sie die stabile Hologramme gerendert werden, die die realen Welt genau nachzuverfolgen.

### <a name="create-spatial-anchors-where-users-place-them"></a>Erstellen der räumlichen verankert, in dem Sie Benutzer platzieren

In den meisten Fällen, sollten Benutzer explizit platzieren räumliche Anker diejenigen sein.

Beispielsweise HoloLens, eine app kann schneidet beim des Benutzers [bestaunen](gaze.md) mit Raytracing der [räumliche Zuordnung](spatial-mapping.md) Mesh, damit den Benutzer entscheiden, ggf. ein Hologramm platzieren können. Wenn der Benutzer tippt, Hologramm platzieren, erstellen Sie einen räumlichen Anker auf dem Schnittpunkt, und legen Sie die – Hologramm am Ursprung des Koordinatensystems an, dass Anchor des.

Lokale räumliche verankert sind einfach, und leistungsstarke zum Erstellen und das System konsolidiert ihre internen Daten, wenn mehrere Anker ihre zugrunde liegenden Daten von triebwerksensoren freigeben können. Erstellen Sie in der Regel einen neuen lokalen räumlichen Anker für jede – Hologramm, die ein Benutzer explizit erteilt werden, es sei denn, die unten beschriebenen, z. B. starre Gruppen von Hologramme.

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>Immer gerendert verankerten Hologramme innerhalb von 3 Messgeräten, die von ihren Anker

Räumliche Anker stabilisieren einem Koordinatensystem in der Nähe des Ankers Ursprungs. Wenn Sie mehr als ca. 3 Meter vom Ursprung Hologramme rendern, können diese Hologramme merkliche mit Feldern fester Breite Fehler relativ ihrer Entfernung vom Ursprung, aufgrund der Hebel-Arm-Effekte auftreten. Dies funktioniert, wenn der Benutzer in der Nähe als Anker, steht, da die Hologramm weit entfernt, des Benutzers ist was bedeutet, dass der angular-Fehler von der entfernten – Hologramm gering sein wird. Allerdings, wenn der Benutzer auf diese entfernten – Hologramm durchläuft, werden klicken Sie dann ihre Ansicht, sodass die Auswirkungen der Hebel-Arm vom Ursprung weit entfernten Anker ziemlich offensichtlich groß.

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>Group-Hologramme, die einen starren Cluster bilden sollen

Mehrere Hologramme können den gleichen Anker des räumlichen freigeben, wenn die app erwartet, dass diese Hologramme feste Beziehungen untereinander zu verwalten.

Z. B. Wenn Sie ein holographic Sonnensystem in einem Raum animieren möchten, ist es besser, alle Objekte auf einem einzelnen Anker Sonnensystem im Center verknüpfen, damit sie reibungslos relativ zueinander verschoben. In diesem Fall ist es Sonnensystem als Ganzes, die verankert ist, auch wenn die dynamische von seiner Komponenten auf dem Anker Verschiebung.

Der Schlüssel hier – Hologramm Stabilität der Netzstromversorgung spricht befolgen die oben genannten 3 Meter-Regel.

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>Rendern Sie hochgradig dynamischer Hologramme anstelle von eines lokalen räumlichen Ankers der feststehende Verweisrahmen

Wenn Sie eine hochgradig dynamischer – Hologramm, z. B. ein Zeichen, die im Raum oder einer Gleitkommazahl-Benutzeroberfläche, die an die Wand in der Nähe der Benutzer folgt durchlaufen haben es wird empfohlen, überspringen Sie die lokalen räumliche Anker und Rendern dieser Hologramme direkt in das Koordinatensystem, die von der bereitgestellten[</C0>feststehendeVerweisrahmen<spanclass="notranslate">](coordinate-systems.md#stationary-frame-of-reference) (d. h. in Unity dies erreichen Sie durch Platzieren von Hologramme direkt in globalen Koordinaten ohne eine WorldAnchor).</span> Hologramme in eine feststehende Verweisrahmen können abweichungen auftreten, wenn der Benutzer alles andere als die – Hologramm ist, aber dies weniger wahrscheinlich ist, bemerkbar für dynamische Hologramme: entweder ist der – Hologramm ständig dennoch verschieben oder ihre Bewegung hält er ständig in der Nähe der Benutzer , in denen Abweichung minimiert werden wird.

Einen interessanter Fall dynamische Hologramme ist ein Objekt, das aus einem verankerten Koordinatensystem zu einem anderen animiert wird. Beispielsweise können Sie zwei Castles 10 Meter auseinander liegen, jeweils in eigene räumliche Anker, mit eine Castle, die Auslösen einer Cannonball an die anderen Castle verfügen. In dem Moment, den die Cannonball ausgelöst wird, können Sie es an der entsprechenden Position in der feststehende Verweisrahmen, um mit der Kanone im Koordinatensystem das erste Castle verankerten übereinstimmen rendern. Sie können die Kurve in der feststehende Verweisrahmen folgen, wie sie 10 Meter über Funk verwendet. Die Cannonball der anderen Castle erreicht, können Sie zu verschieben, dass sie in der zweiten Castle Koordinatensystem, um Berechnungen mit rigidbodys, Castle die Physik ermöglichen verankert auswählen.

Wenn Sie eine hochgradig dynamischer – Hologramm geräteübergreifend freigegeben haben, müssen Sie einige räumliche cloudankers fungieren wie das übergeordnete Objekt auswählen, wie stationär Bezugsrahmen über Geräte hinweg gemeinsam genutzt werden kann.  Allerdings sollten in diesem Fall Sie sicherstellen, dass entweder die dynamische – Hologramm oder die Geräte anzeigen innerhalb des Ankers 3 m Radius bleiben, um sicherzustellen, dass die Hologramm stabile auf allen Geräten angezeigt wird.

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>Vermeiden Sie erstellen ein Raster mit räumlichen Anker

Unter Umständen versucht, die Ihre App ein rechteckiges Raster des räumlichen Anker gelöscht werden, da der Benutzer, dynamische Objekte führt aus den Anker Anker Übergang, wenn sie sich bewegen. Dies ist jedoch zahlreiche Verwaltungsoptionen für Ihre app, ohne den Vorteil, dass die Tiefe Sensordaten, die das System selbst intern verwaltet. In diesen Fällen werden Sie in der Regel bessere Ergebnisse mit weniger Aufwand erreichen Ihre Hologramme platzieren, in der feststehende Verweisrahmen, wie im vorherigen Abschnitt beschrieben.

Wenn Sie einen Satz von räumlichen cloudanker rund um einen statischen Speicherplatz vorab zu positionieren, sollten Sie Sie platzieren die räumliche Anker an die Standorte von der wichtigsten Hologramme, die dem Benutzer pro Prinzip der oben angezeigt wird, anstatt Sie zu einem beliebigen Raster der Anker erstellen.  Dadurch wird sichergestellt, dass Sie maximale Stabilität für diesen Schlüssel Hologramme erhalten.

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>Lokale räumliche Anker nicht mehr benötigten Version

Während ein lokaler räumlicher Anker aktiv ist, wird das System beibehalten, um die Daten von triebwerksensoren priorisieren, die in der Nähe dieser Anker befindet. Wenn Sie einen räumlichen Anker, beenden, die Zugriff auf seine Koordinatensystem nicht mehr verwenden. Die zugrunde liegenden Daten von triebwerksensoren entfernt werden dadurch nach Bedarf.

Dies ist besonders wichtig für lokale Anker, die Sie in den räumlichen Premium-Speicher dauerhaft gespeichert haben. Die Sensordaten hinter diesen Anker werden dauerhaft bleiben muss, kann Ihre app finden Sie in zukünftigen Sitzungen, zu reduzieren, den verfügbaren Speicherplatz zum Nachverfolgen von anderen Anker, Anker. Speichern Sie nur diese lokalen Anker, die Sie benötigen es in zukünftigen Sitzungen zu finden, und entfernen sie aus dem Speicher, wenn sie nicht mehr für den Benutzer von Bedeutung sind.

Für räumliche cloudanker kann Ihrem Speicher skalieren, wie Ihr Szenario erfordert.  Sie können beliebig viele cloudanker bei Bedarf nur, wenn Sie wissen, dass Ihre Benutzer nicht benötigen, suchen Sie Hologramme erneut an, dass Anchor Freigabe speichern.

## <a name="see-also"></a>Siehe auch
* [Koordinatensysteme](coordinate-systems.md)
* [Freigegebene Funktionen in mixed reality](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure räumliche Anker</a>
* [Dauerhaftigkeit in Unity](persistence-in-unity.md)
* [Räumliche Anker in DirectX](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [Fallstudie: Lücken in der Realität ansehen](case-study-looking-through-holes-in-your-reality.md)
