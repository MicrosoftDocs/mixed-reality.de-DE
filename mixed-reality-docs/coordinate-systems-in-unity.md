---
title: Koordinatensysteme in Unity
description: Erfahren Sie, wie Sie in Unity sitzender, stehender, Raum-und Welt weite Umgebungen mit gemischter Realität erstellen.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Koordinatensystem, geografischer Koordinatensystem, nur Ausrichtung, sitzender Skalierung, aneinandergreifende Skala, Raum Skala, Welt weite, 360 Grad, sitzend, stehend, Raum, Welt, Skala, Position, Ausrichtung, Unity, Anker, räumlicher Anker, Welt Anker, weltweit gesperrt, Welt Sperre, gesperrter Text, Body-Lock, nach Verfolgungs Verlust, loerbarkeit, Grenzen, wiedergeben
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525962"
---
# <a name="coordinate-systems-in-unity"></a>Koordinatensysteme in Unity

Windows Mixed Reality unterstützt Apps über eine Vielzahl von [Skalierungs](coordinate-systems.md)Möglichkeiten hinweg, von ausgerichteten und skalierbaren apps bis hin zu hochskalierbaren apps. Auf hololens können Sie weitere apps erstellen und Apps erstellen, mit denen Benutzer mehr als 5 Meter durchlaufen können, indem Sie eine ganze Etage eines Builds und darüber hinaus untersuchen.

Der erste Schritt beim Aufbau einer gemischten Realität in Unity besteht darin, zu bestimmen [, welche Benutzer](coordinate-systems.md) Oberfläche Ihre APP als Ziel hat.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>Aufbauen einer reinen Orientierung oder einer Skalierungs Funktion

**Namespace:** *Unityengine. XR*<br>
**Sorte** *Xrdevice*

Sie müssen Unity auf den Typ "stationärer nach verfolgungsbereich" festlegen, um eine **Orientierung** oder eine **Skalierung**zu erstellen. Dadurch wird das World-Koordinatensystem von Unity festgelegt, um den [stationären Frame des Verweises](coordinate-systems.md#spatial-coordinate-systems)zu verfolgen. Im Modus der stationären Nachverfolgung wird der Inhalt, der direkt vor dem Standard Speicherort der Kamera (vorwärts ist-Z) im Editor eingefügt wird, vor dem Benutzer angezeigt, wenn die APP gestartet wird.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**Namespace:** *Unityengine. XR*<br>
**Sorte** *Inputtracking*

Bei einer reinen **Orientierung** , z. b. bei einem Video Viewer mit einem 360-Grad (bei dem Positions Aktualisierungen die Illusion zerstören würden), können Sie "XR" festlegen [. Inputtracking. disablepositionaltracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) auf true:

```cs
InputTracking.disablePositionalTracking = true;
```

Um dem Benutzer die Möglichkeit zu geben, den sitzenden Ursprung zu einem späteren Zeitpunkt wieder einzugeben, können Sie den XR-Vorgang für eine Benutzer **freundliche Skalierung**durchführen [. Inputtracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) -Methode:

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a>Aufbauen einer Dauer-oder Raum Skalierung

**Namespace:** *Unityengine. XR*<br>
**Sorte** *Xrdevice*

Für eine **Dauer-** oder **Raum Skalierung**müssen Sie Inhalte in Relation zum Boden platzieren. Sie haben eine Begründung für den Benutzer, der die **[räumliche Phase](coordinate-systems.md#spatial-coordinate-systems)** verwendet, die den definierten Ursprung und die optionale Raumgrenze des Benutzers darstellt, die während der ersten Durchführung eingerichtet wird.

Um sicherzustellen, dass Unity mit dem globalen Koordinatensystem auf Grundebene betrieben wird, können Sie Unity auf den Typ des roomscale-nach Verfolgungs Raums festlegen und sicherstellen, dass der Satz erfolgreich ist:

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* Wenn settrackingspacetype true zurückgibt, hat Unity das World-Koordinatensystem erfolgreich umgestellt, um den stagingframe [des Verweises](coordinate-systems.md#spatial-coordinate-systems)nachzuverfolgen.
* Wenn settrackingspacetype false zurückgibt, konnte Unity nicht in den stagingframe des Verweises wechseln. Dies liegt wahrscheinlich daran, dass der Benutzer noch keine Etage in der Umgebung eingerichtet hat. Dies ist nicht üblich, kann jedoch vorkommen, wenn die Stufe in einem anderen Raum eingerichtet wurde und das Gerät in den aktuellen Raum verschoben wurde, ohne dass der Benutzer eine neue Stufe einrichten muss.

Nachdem Ihre APP den Typ für die Nachverfolgung von roomscale festgelegt hat, wird der Inhalt auf der Ebene "y = 0" auf der Etage angezeigt. Der Ursprung bei (0,0) ist die spezifische Stelle auf dem Boden, an der der Benutzer während des Raum Setups Stand, wobei-Z die Vorwärtsrichtung darstellt, die während des Setups aufgetreten ist.

**Namespace:** *Unityengine. experimental. XR*<br>
**Sorte** *Begrenzungs*

In Skriptcode können Sie dann die trygetgeometry-Methode aufrufen, indem Sie den Typ "unityengine. experimental. XR. Boundary" verwenden, um ein Begrenzungs Polygon abzurufen und dabei den Grenztyp "trackedarea" anzugeben. Wenn der Benutzer eine Grenze definiert hat (Sie erhalten eine Liste mit Scheitel Punkten), ist es sicher, dass er für den Benutzer eine **Raum** Umgebung bereitstellt, in der er die von Ihnen erstellte Szene durchlaufen kann.

Beachten Sie, dass das System die Grenze automatisch durchführt, wenn sich der Benutzer nähert. Ihre APP muss dieses Polygon nicht verwenden, um die Grenze selbst zu erzeugen. Allerdings können Sie Ihre Szenen Objekte mithilfe dieses Begrenzungs Polygons anordnen, um sicherzustellen, dass der Benutzer diese Objekte physisch ohne teleportierung erreichen kann:

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>Entwickeln eines weltweiten Erlebnisses

**Namespace:** *Unityengine. XR. WSA*<br>
**Sorte** *Worldanchor*

Für echte **Welt weite** Oberflächen in hololens, mit denen Benutzer mehr als 5 Meter bewegen können, benötigen Sie neue Techniken, die über diejenigen hinausgehen, die für Raum Skalierungen verwendet werden. Ein wichtiges Verfahren, das Sie verwenden, besteht darin, einen [räumlichen Anker](coordinate-systems.md#spatial-anchors) zu erstellen, mit dem ein Cluster von holograms genau in der physischen Welt gesperrt wird, unabhängig davon, wie weit der Benutzer gewechselt hat, und [diese Hologramme in späteren Sitzungen erneut finden](coordinate-systems.md#spatial-anchor-persistence).

In Unity erstellen Sie einen räumlichen Anker durch Hinzufügen der Unity-Komponente **worldanchor** zu einem gameobject-Objekt.

### <a name="adding-a-world-anchor"></a>Hinzufügen eines Welt Ankers

Um einen Welt Anker hinzuzufügen, nennen Sie addComponent<WorldAnchor>() für das Game-Objekt mit der Transformation, die Sie in der realen Welt verankern möchten.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Das ist alles! Dieses Spielobjekt wird nun an seinem aktuellen Speicherort in der physischen Welt verankert. möglicherweise werden die Unity-Weltkoordinaten im Laufe der Zeit leicht angepasst, um die physische Ausrichtung sicherzustellen. Verwenden Sie [Persistenz](persistence-in-unity.md) , um diesen verankerten Standort in einer zukünftigen App-Sitzung wieder zu suchen.

### <a name="removing-a-world-anchor"></a>Entfernen eines Welt Ankers

Wenn Sie nicht mehr möchten, dass das gameobject-Objekt an eine physische Welt Stelle gesperrt ist, und Sie dieses Frame nicht verschieben möchten, können Sie einfach "zerstören" für die "World Anchor"-Komponente aufzurufen.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

Wenn Sie das gameobject-Objekt in diesen Frame verschieben möchten, müssen Sie stattdessen destroyimmediate aufzurufen.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>Verschieben eines weltweit verankerten gameobject

Gameobject kann nicht verschoben werden, wenn ein Welt Anker darauf liegt. Wenn Sie das gameobject für diesen Frame verschieben müssen, müssen Sie Folgendes ausführen:
1. Destroyimmediate der Welt Anker Komponente
2. Verschieben des gameobject
3. Fügen Sie dem gameobject eine neue Welt Anker Komponente hinzu.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Behandeln von Änderungen an der Anwendungs Freundlichkeit

Ein worldanchor kann nicht in der physischen Welt zu einem bestimmten Zeitpunkt einstellbar sein. Wenn dies der Fall ist, wird die Transformation des verankerten Objekts von Unity nicht aktualisiert. Dies kann sich auch ändern, während eine app ausgeführt wird. Wenn Sie die Änderung der loerability nicht bewältigen, wird das Objekt nicht am richtigen physischen Speicherort der Welt angezeigt.

So erhalten Sie eine Benachrichtigung über die Änderungen der Änderungen:
1. Ontrackingchanged-Ereignis abonnieren
2. Behandeln des Ereignisses

Das **ontrackingchanged** -Ereignis wird immer dann aufgerufen, wenn sich der zugrunde liegende räumliche Anker zwischen dem Zustand "verwendbar" und "nicht zu verwendbar" ändert.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

Behandeln Sie dann das-Ereignis:

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

Manchmal werden Anker sofort gefunden. In diesem Fall wird diese islocated-Eigenschaft des Ankers auf true festgelegt, wenn addComponent<WorldAnchor>() zurückgibt. Folglich wird das ontrackingchanged-Ereignis nicht ausgelöst. Ein sauberes Muster besteht darin, den ontrackingchanged-Handler mit dem ursprünglichen ISSE-Zustand nach dem Anfügen eines Ankers aufzurufen.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a>Gemeinsame Nutzung von Ankern Geräten

Sie können <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial</a> Anchor verwenden, um einen permanenten cloudanker von einem lokalen worldanchor zu erstellen, den Ihre APP dann über mehrere hololens-, IOS-und Android-Geräte hinweg finden kann.  Durch die gemeinsame Nutzung eines gemeinsamen räumlichen Ankers auf mehreren Geräten kann jeder Benutzer den Inhalt in Relation zu diesem Anker am gleichen physischen Speicherort sehen.  Dies ermöglicht gemeinsame Erfahrungen in Echtzeit.

Um mit der Einführung von freigegebenen Erfahrungen in Unity zu beginnen, testen Sie die fünfminütigen <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchor Unity-Schnellstarts</a>.

Sobald Sie mit räumlichen Azure-Ankern arbeiten, können Sie <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Anker in Unity erstellen und lokalisieren</a>.

## <a name="see-also"></a>Siehe auch
* [Skalierungsmöglichkeiten](coordinate-systems.md#mixed-reality-experience-scales)
* [Räumliche Phase](coordinate-systems.md#stage-frame-of-reference)
* [Verfolgbarkeitsverlust in Unity](tracking-loss-in-unity.md)
* [Raumanker](spatial-anchors.md)
* [Persistenz in Unity](persistence-in-unity.md)
* [Gemeinsame Erlebnisse in Unity](shared-experiences-in-unity.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchor SDK für Unity</a>