---
title: Persistenz in Unity
description: Mithilfe der Persistenz können Ihre Benutzer individuelle Hologramme oder einen Arbeitsbereich an jedem Ort anheften und später wiederfinden, wo Sie von vielen Verwendungsmöglichkeiten Ihrer APP ausgehen.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Hololens, Persistenz, Unity
ms.openlocfilehash: b6a67e52b3a5ce724a90eb1a479c5eda74b0c4cb
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524785"
---
# <a name="persistence-in-unity"></a>Persistenz in Unity

**Namespace:** *Unityengine. XR. WSA. Persistenz*<br>
**Klassi** *Worldanchorstore*

Worldanchorstore ist der Schlüssel für die Erstellung von Holographic-Erfahrungen, bei denen Hologramme in den einzelnen Anwendungs Instanzen in bestimmten realen Positionen bleiben. Dadurch können Ihre Benutzer individuelle Hologramme oder einen Arbeitsbereich an einem beliebigen Ort anheften und später wiederfinden, wo Sie von vielen Verwendungsmöglichkeiten Ihrer APP ausgehen.

## <a name="how-to-persist-holograms-across-sessions"></a>Beibehalten von holograms über Sitzungen hinweg

Mit worldanchorstore können Sie den Speicherort von worldanchor Sitzungs übergreifend beibehalten. Sie müssen ihre gameobjects, die einen bestimmten Welt Anker verwenden, separat nachverfolgen, um Hologramme in mehreren Sitzungen dauerhaft beizubehalten. Häufig ist es sinnvoll, einen gameobject-Stamm mit einem Welt Anker zu erstellen und untergeordnete Hologramme mit einem lokalen Positions Offset zu verankern.

So laden Sie holograms aus vorherigen Sitzungen:
1. Verschaffen Sie sich den worldanchorstore
2. Laden von App-Daten in Bezug auf den World-Anker, der die ID des Welt Ankers liefert
3. Einen Welt Anker aus seiner ID laden

So speichern Sie Hologramme für zukünftige Sitzungen:
1. Verschaffen Sie sich den worldanchorstore
2. Speichern eines Welt Ankers, der eine ID angibt
3. Speichern von App-Daten, die sich auf den Welt Anker beziehen, sowie eine ID

### <a name="getting-the-worldanchorstore"></a>Der worldanchorstore wird erhalten.

Wir möchten einen Verweis auf den worldanchorstore behalten, damit wir wissen, dass wir bereit sind, wenn wir einen Vorgang durchführen möchten. Da es sich hierbei um einen asynchronen-Befehl handelt, der möglicherweise unmittelbar nach dem Start von aufgerufen wird, möchten wir

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

Storeloaded ist in diesem Fall der Handler für den Fall, dass der worldanchorstore das Laden abgeschlossen hat:

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

Wir haben nun einen Verweis auf den worldanchorstore, den wir verwenden werden, um bestimmte Welt Anker zu speichern und zu laden.

### <a name="saving-a-worldanchor"></a>Speichern von worldanchor

Zum Speichern müssen wir einfach den Namen der Speicherung benennen und Sie an den worldanchor übergeben, den wir vor dem Speichern erhalten haben. Hinweis: Wenn Sie versuchen, zwei Anker in derselben Zeichenfolge zu speichern, tritt ein Fehler auf (speichern. Save gibt false zurück). Sie müssen das vorherige Speichern löschen, bevor Sie das neue speichern:

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

### <a name="loading-a-worldanchor"></a>Laden von worldanchor

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

Wir können außerdem "Store" verwenden. Delete () um einen Anker zu entfernen, den wir zuvor gespeichert und gespeichert haben. Löschen Sie (), um alle zuvor gespeicherten Daten zu entfernen.

### <a name="enumerating-existing-anchors"></a>Auflisten vorhandener Anker

Um zuvor gespeicherte Anker zu ermitteln, müssen Sie getallids aufrufen.

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Beibehalten von holograms für mehrere Geräte

Sie können mithilfe von <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial</a> Anchor einen permanenten cloudenanchor von einem lokalen worldanchor erstellen, der von Ihrer APP über mehrere hololens-, IOS-und Android-Geräte hinweg gefunden werden kann, selbst wenn diese Geräte nicht gleichzeitig zusammen vorhanden sind.  Da cloudananker permanent sind, können mehrere Geräte im Lauf der Zeit jeweils Inhalte sehen, die relativ zu diesem Anker am gleichen physischen Standort gerendert werden.

Um mit der Einführung von freigegebenen Erfahrungen in Unity zu beginnen, testen Sie die fünfminütigen <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchor Unity-Schnellstarts</a>.

Sobald Sie mit räumlichen Azure-Ankern arbeiten, können Sie <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Anker in Unity erstellen und lokalisieren</a>.

## <a name="see-also"></a>Siehe auch
* [Dauerhaftigkeit räumlicher Anker](coordinate-systems.md#spatial-anchor-persistence)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchor SDK für Unity</a>
