---
title: Koordinatensysteme in Unity
description: Erfahren Sie, wie Sie sitzen, ständigen erstellen, die Platz Skalierung und weltweit einsetzbaren mixed Reality-Erfahrungen in Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Koordinatensystem, räumliche Koordinatensystem, Ausrichtung, sitzen Skalierung, ständigen Maß Platz skalierbare, weltweit skalierbare, 360-Grad-sitzen, ständigen, Raum, Welt, skalieren, Position, Ausrichtung, Unity, Anker, räumliche Anker, Welt Anker, die World-gesperrt, World-sperren "," Text-gesperrt, Text-sperren, Nachverfolgen von Verlust, Locatability, den angegebenen Begrenzungen, verschoben
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605054"
---
# <a name="coordinate-systems-in-unity"></a>Koordinatensysteme in Unity

Windows Mixed Reality unterstützt apps für eine Vielzahl von [auftreten Skalen](coordinate-systems.md), aus nur Ausrichtung und sitzen Skalierung apps sich über den Raum einsetzbaren apps. Für HoloLens können Sie weiter gehen und Erstellen von weltweit einsetzbaren apps, mit denen Benutzer über 5 Meter Schritt für Schritt ein ganzes Stockwerk eines Gebäudes und darüber hinaus untersuchen.

Der erste Schritt bei der Erstellung einer mixed Reality-Erfahrung in Unity wird bestimmt, welche [auftreten Skalierung](coordinate-systems.md) Ihrer app ausgerichtet wird.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>Erstellen eine reine Ausrichtung oder sitzen Skalierung-Erfahrung

**Namespace:** *UnityEngine.XR*<br>
**Typ:** *XRDevice*

Zum Erstellen einer **Ausrichtung nur** oder **sitzen Skalierung Erfahrung**, müssen Sie Unity auf Festlegen der stationär Speicherplatz Überwachungstyp. Hiermit wird von Unity globales Koordinatensystem zum Nachverfolgen der [feststehende Verweisrahmen](coordinate-systems.md#spatial-coordinate-systems). In den Modus zum Nachverfolgen von nicht bewegt, wird Inhalt im Editor einfach vor der Kamera-Standardspeicherort platziert (forward ist – Z) wird vor dem Benutzer angezeigt, wenn die app gestartet wird.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**Namespace:** *UnityEngine.XR*<br>
**Typ:** *InputTracking*

Für ein reines **Ausrichtung ausschließlich Erfahrung** wie z. B. eine 360-Grad-video-Viewer (wobei mit Feldern fester Breite Head Updates würde auflöst, die Illusion), Sie können dann festlegen [XR. InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) auf "true":

```cs
InputTracking.disablePositionalTracking = true;
```

Für eine **sitzen Skalierung Erfahrung**, damit der Benutzer später verschoben sitzen Ursprung rufen Sie die [XR. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) Methode:

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a>Erstellen eine Umgebung ständigen Skalierung oder Platz Skalierung

**Namespace:** *UnityEngine.XR*<br>
**Typ:** *XRDevice*

Für eine **ständigen Skalierung** oder **Platz Skalierung Erfahrung**, müssen Sie den Inhalt relativ zu dem Boden platziere. Sie des Benutzers verständlich floor, mit der  **[räumliche Phase](coordinate-systems.md#spatial-coordinate-systems)**, Etage Ursprung und optional Platz Grenze definiert die des Benutzers darstellt, richten Sie während der ersten ausführen.

Um sicherzustellen, dass Unity mit der ganzen Welt Koordinatensystem Floor-Ebene ausgeführt wird, können Sie Unity auf den Speicherplatz Überwachungstyp RoomScale festgelegt, und stellen Sie sicher, dass die Gruppe erfolgreich ist:

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
* Wenn SetTrackingSpaceType "true" zurückgibt, Unity der Wechsel der globales Koordinatensystem zum Nachverfolgen der [Phase Verweisrahmen](coordinate-systems.md#spatial-coordinate-systems).
* Wenn SetTrackingSpaceType "false" zurückgegeben wird, konnte sich Unity, wechseln auf der Bühne Verweisrahmen, wahrscheinlich weil der Benutzer nicht selbst eine Etage in ihrer Umgebung eingerichtet wurde. Dies ist nicht üblich, aber es kann vorkommen, wenn die Stufe in einem anderen Raum eingerichtet wurde und das Gerät wurde in der aktuellen Raum ohne die Benutzer-Einstellung, um eine neue Stufe verschoben.

Sobald Ihre app erfolgreich der Überwachungstyp Speicherplatz, Inhalte auf der y-platziert RoomScale festgelegt = 0, die auf dem Boden Ebene angezeigt wird. Der Ursprung an (0, 0, 0) werden die bestimmten Stelle auf dem Boden, in denen der Benutzer vor während des Setups Platz mit -Z, die sie während des Setups konfrontiert wurden vorwärts darstellt.

**Namespace:** *UnityEngine.Experimental.XR*<br>
**Typ:** *Begrenzungsgruppen*

In Skriptcode können Sie rufen Sie die TryGetGeometry-Methode für Sie sind der UnityEngine.Experimental.XR.Boundary-Typ, um eine Begrenzung Vieleck, erhalten ein Grenze TrackedArea angeben werden. Wenn der Benutzer eine Grenze definiert (erhalten Sie wieder eine Liste der Scheitelpunkte), wissen Sie, es ist sicher bereitstellen eine **Platz Skalierung Erfahrung** für den Benutzer, in dem sie eine in der Szene Anleitung zu erstellen.

Beachten Sie, dass das System automatisch die Grenze gerendert wird, wenn der Benutzer es erreicht. Ihre app muss nicht auf dieses Polygon zu verwenden, um die Begrenzung selbst zu rendern. Allerdings können Sie auswählen, um das Layout der szeneobjekte, die über diese Begrenzung Vieleck, um sicherzustellen, dass der Benutzer diese Objekte ohne Teleporting physisch erreichen kann:

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>Erstellen einer weltweit einsetzbaren-Erfahrung

**Namespace:** *UnityEngine.XR.WSA*<br>
**Typ:** *WorldAnchor*

Für "true" **weltweit einsetzbaren Erfahrungen** für HoloLens, mit denen Benutzer über 5 Meter erkundungs können, benötigen Sie neue Techniken hinausgehen für Platz Skalierung Oberflächen verwendet. Ist eine wichtige Technik, die Sie verwenden die Erstellung einer [räumliche Anker](coordinate-systems.md#spatial-anchors) , Sperren einen Cluster mit Hologramme genau an die Stelle in der realen Welt, unabhängig davon, wie weit der Benutzer gewechselt hat, und klicken Sie dann [finden Sie diese Hologramme erneut in einem späteren Zeitpunkt Sitzungen](coordinate-systems.md#spatial-anchor-persistence).

In Unity, erstellen Sie einen räumlichen Anker durch Hinzufügen der **WorldAnchor** Unity-Komponente zu einem "gameobject".

### <a name="adding-a-world-anchor"></a>Einen Anker Welt hinzufügen

Rufen Sie zum Hinzufügen eines Welt Ankers AddComponent<WorldAnchor>(-) für das spielobjekt mit der Transformation, die Sie in der realen Welt verankert werden sollen.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Das ist alles! Dieses spielobjekt wird jetzt an ihrem aktuellen Speicherort in der realen Welt verankert werden – möglicherweise angezeigt, die Unity globale Koordinaten, die im Laufe der Zeit, um sicherzustellen, dass diese physische Ausrichtung leicht anpassen. Verwendung [Persistenz](persistence-in-unity.md) Ermittlung verankert Speicherort in einem künftigen app-Sitzung erneut.

### <a name="removing-a-world-anchor"></a>Entfernen einen Anker World

Wenn Sie nicht mehr, dass das "gameobject" an einen Speicherort für die physische Welt gesperrt werden soll und nicht auf diesen Frame verschieben möchten, können Sie einfach löschen auf der Welt Anchor-Komponente aufrufen.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

Wenn Sie das "gameobject" diesen Frame verschieben möchten, müssen Sie DestroyImmediate stattdessen aufrufen.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>Verschieben einer Welt verankert "gameobject"

Des "gameobject" kann nicht verschoben werden, während ein Anker Welt darauf ist. Wenn Sie das "gameobject" diesen Frame verschieben müssen, müssen Sie:
1. DestroyImmediate der Welt Anchor-Komponente
2. Verschieben Sie das "gameobject"
3. Fügen Sie eine neue Welt Anker-Komponente, auf das "gameobject".

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Locatability Änderungen

Eine WorldAnchor auffindbaren in der realen Welt zu einem bestimmten Zeitpunkt möglicherweise nicht. Wenn in diesem Fall ist Unity nicht die Transformation das verankerten Objekt aktualisiert. Dies kann auch ändern, während eine app ausgeführt wird. Fehler bei die Änderung in Locatability verarbeiten bewirkt das Objekt, das nicht in den richtigen physischen Speicherort in der ganzen Welt angezeigt werden.

Um zu Locatability Änderungen benachrichtigt zu werden:
1. Abonnieren des Ereignisses OnTrackingChanged
2. Behandeln des Ereignisses

Die **OnTrackingChanged** Ereignis wird aufgerufen, wenn der zugrunde liegenden räumliche Anker zwischen den Zuständen, im Vergleich zu nicht auffindbaren werden gebietsschemabezogene ändert.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

Klicken Sie dann das Ereignis zu behandeln:

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

Manchmal sind sofort Anker befindet. In diesem Fall wird diese IsLocated-Eigenschaft von der Anker auf bei "true" festgelegt werden AddComponent<WorldAnchor>() gibt. Daher wird die OnTrackingChanged-Ereignis nicht ausgelöst werden. Ein clean Muster wäre Ihr OnTrackingChanged Handler mit dem Anfangszustand IsLocated rufen Sie nach dem Anfügen eines Ankers.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a>Freigeben von Anker auf Geräten

Können Sie <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure räumliche Anker</a> einen dauerhafte Anker aus einer lokalen WorldAnchor, zu erstellen, die Ihrer app über mehrere HoloLens, iOS und Android-Geräte suchen kann.  Anhand der einen allgemeine räumlichen Anker auf mehreren Geräten, kann jeder Benutzer Inhalt gerendert wird, relativ zu diesem-Anker wird in demselben physischen Standort finden Sie unter.  Dadurch können freigegebene ein Nutzererlebnis in Echtzeit.

Informationen zum Einstieg gemeinsame Erfahrungen in Unity erstellen, Testen der 5-Minuten- <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure räumliche Anker Unity-Schnellstarts</a>.

Sobald Sie mit Azure räumliche Anker die betriebsbereit sind, können Sie dann <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">erstellen, und suchen Sie in Unity Anker</a>.

## <a name="see-also"></a>Siehe auch
* [Erleben Sie Skalierungen](coordinate-systems.md#mixed-reality-experience-scales)
* [Räumliche Phase](coordinate-systems.md#stage-frame-of-reference)
* [Verlust der Überwachung in Unity](tracking-loss-in-unity.md)
* [Räumliche Anker](spatial-anchors.md)
* [Dauerhaftigkeit in Unity](persistence-in-unity.md)
* [Freigegebene Funktionen in Unity](shared-experiences-in-unity.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure räumliche Anker</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure räumliche Anker SDK für Unity</a>