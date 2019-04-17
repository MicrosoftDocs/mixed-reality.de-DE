---
title: Dauerhaftigkeit in Unity
description: Persistenz ermöglicht Ihren Benutzern individuelle Hologramme oder in einem Arbeitsbereich anheften, wo sie möchten, und klicken Sie dann finden Sie, dass es später noch Mal, in dem sie über viele erwarten Ihrer App verwendet.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, Dauerhaftigkeit, Unity
ms.openlocfilehash: b6a67e52b3a5ce724a90eb1a479c5eda74b0c4cb
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605075"
---
# <a name="persistence-in-unity"></a>Dauerhaftigkeit in Unity

**Namespace:** *UnityEngine.XR.WSA.Persistence*<br>
**Klasse:** *WorldAnchorStore*

Die WorldAnchorStore ist der Schlüssel zum Erstellen von holographic Erfahrungen Hologramme, in denen bestimmte realen Positionen behalten Sie für Instanzen der Anwendung. Mit diesem können Ihre Benutzer einzelne Hologramme oder in einem Arbeitsbereich anheften, wo sie möchten, und suchen Sie es später noch Mal, erwarten sie, dass über viele Verwendungen von Ihrer app.

## <a name="how-to-persist-holograms-across-sessions"></a>Gewusst wie: Hologramme sitzungsübergreifend beibehalten.

Die WorldAnchorStore können Sie den Speicherort des WorldAnchor über Sitzungen hinweg beibehalten werden. Damit tatsächlich Hologramme sitzungsübergreifend beibehalten können, müssen Sie separat Ihre "gameobjects" mitverfolgen, die einen bestimmtes Welt Anker verwenden. Es ist oft sinnvoll, erstellen Sie ein "gameobject"-Stamm mit einem Welt Anker und die untergeordneten Elemente aufweisen Hologramme verankert ist es mit einer lokalen Offsetposition.

So laden Sie Hologramme aus früheren Sitzungen:
1. Abrufen der WorldAnchorStore
2. Laden Sie die app-Daten, die im Zusammenhang mit der Welt Anker dadurch die Welt Anker-id
3. Laden Sie einen Anker der Welt aus der id

Um Hologramme für zukünftige Sitzungen zu speichern:
1. Abrufen der WorldAnchorStore
2. Speichern Sie einen World Anker-Id angeben
3. Speichern von app-Daten, die im Zusammenhang mit der ganzen Welt Anker zusammen mit einer id

### <a name="getting-the-worldanchorstore"></a>Abrufen der WorldAnchorStore

Wir möchten einen Verweis auf die WorldAnchorStore, um zu speichern, damit wir wissen, dass wir können soll, wenn wir einen Vorgang ausführen möchten. Da dies einem asynchronen Aufruf möglicherweise so bald wie Start, ist, das wir aufrufen möchten

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

In diesem Fall ist die StoreLoaded unseren Handler für die bei der WorldAnchorStore Ladevorgang abgeschlossen ist:

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

Wir haben jetzt einen Verweis auf die WorldAnchorStore der zum Speichern und Laden von bestimmten Welt Anker verwendet wird.

### <a name="saving-a-worldanchor"></a>Speichern einer WorldAnchor

Um zu speichern, müssen wir einfach nennen, was wir speichern, und geben Sie ihn der WorldAnchor wir vor dem haben, wenn wir speichern möchten. Hinweis: zwei Anker auf die gleiche Zeichenfolge speichern möchten (Speicher. fehl Speichervorgang wird "false" zurückgegeben). Sie müssen die vorherige speichern vor dem Speichern der neuen löschen:

```
private void SaveGame()
{
       // Save data about holograms positioned by this world anchor
       if (!this.savedRoot) // Only Save the root once
       {
              this.savedRoot = this.store.Save("rootGameObject", anchor);
              Assert(this.savedRoot);
       }
}
```

### <a name="loading-a-worldanchor"></a>Laden eine WorldAnchor

Und zum Laden:

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

Wir können außerdem Store verwenden. Speicher und Delete() einen Anker zu entfernen, die zuvor gespeichert haben. Clear() So entfernen Sie alle zuvor gespeicherte Daten.

### <a name="enumerating-existing-anchors"></a>Auflisten vorhandener Anker

Rufen Sie zum Ermitteln von zuvor gespeicherten Anker GetAllIds.

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Beibehalten von Hologramme für mehrere Geräte

Können Sie <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure räumliche Anker</a> einen dauerhafte Anker aus einer lokalen WorldAnchor, zu erstellen, die Ihrer app klicken Sie dann über mehrere HoloLens, iOS und Android-Geräte suchen kann, selbst wenn diese Geräte nicht zur gleichen zusammen vorhanden sind Zeit.  Da cloudanker dauerhaft sind, können mehrere Geräte im Laufe der Zeit jeweils Inhalt gerendert wird, relativ zu diesem-Anker wird in demselben physischen Standort angezeigt.

Informationen zum Einstieg gemeinsame Erfahrungen in Unity erstellen, Testen der 5-Minuten- <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure räumliche Anker Unity-Schnellstarts</a>.

Sobald Sie mit Azure räumliche Anker die betriebsbereit sind, können Sie dann <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">erstellen, und suchen Sie in Unity Anker</a>.

## <a name="see-also"></a>Siehe auch
* [Räumliche Anchor-Persistenz](coordinate-systems.md#spatial-anchor-persistence)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure räumliche Anker</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure räumliche Anker SDK für Unity</a>
