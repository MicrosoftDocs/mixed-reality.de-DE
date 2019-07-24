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
# <a name="persistence-in-unity"></a><span data-ttu-id="c89c4-104">Persistenz in Unity</span><span class="sxs-lookup"><span data-stu-id="c89c4-104">Persistence in Unity</span></span>

<span data-ttu-id="c89c4-105">**Namespace:** *Unityengine. XR. WSA. Persistenz*</span><span class="sxs-lookup"><span data-stu-id="c89c4-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="c89c4-106">**Klassi** *Worldanchorstore*</span><span class="sxs-lookup"><span data-stu-id="c89c4-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="c89c4-107">Worldanchorstore ist der Schlüssel für die Erstellung von Holographic-Erfahrungen, bei denen Hologramme in den einzelnen Anwendungs Instanzen in bestimmten realen Positionen bleiben.</span><span class="sxs-lookup"><span data-stu-id="c89c4-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="c89c4-108">Dadurch können Ihre Benutzer individuelle Hologramme oder einen Arbeitsbereich an einem beliebigen Ort anheften und später wiederfinden, wo Sie von vielen Verwendungsmöglichkeiten Ihrer APP ausgehen.</span><span class="sxs-lookup"><span data-stu-id="c89c4-108">This lets your users pin individual holograms or a workspace wherever they want it, and then find it later where they expect over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="c89c4-109">Beibehalten von holograms über Sitzungen hinweg</span><span class="sxs-lookup"><span data-stu-id="c89c4-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="c89c4-110">Mit worldanchorstore können Sie den Speicherort von worldanchor Sitzungs übergreifend beibehalten.</span><span class="sxs-lookup"><span data-stu-id="c89c4-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="c89c4-111">Sie müssen ihre gameobjects, die einen bestimmten Welt Anker verwenden, separat nachverfolgen, um Hologramme in mehreren Sitzungen dauerhaft beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="c89c4-111">To actually persist holograms across sessions, you will need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="c89c4-112">Häufig ist es sinnvoll, einen gameobject-Stamm mit einem Welt Anker zu erstellen und untergeordnete Hologramme mit einem lokalen Positions Offset zu verankern.</span><span class="sxs-lookup"><span data-stu-id="c89c4-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="c89c4-113">So laden Sie holograms aus vorherigen Sitzungen:</span><span class="sxs-lookup"><span data-stu-id="c89c4-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="c89c4-114">Verschaffen Sie sich den worldanchorstore</span><span class="sxs-lookup"><span data-stu-id="c89c4-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="c89c4-115">Laden von App-Daten in Bezug auf den World-Anker, der die ID des Welt Ankers liefert</span><span class="sxs-lookup"><span data-stu-id="c89c4-115">Load app data relating to the world anchor which gives you the id of the world anchor</span></span>
3. <span data-ttu-id="c89c4-116">Einen Welt Anker aus seiner ID laden</span><span class="sxs-lookup"><span data-stu-id="c89c4-116">Load a world anchor from its id</span></span>

<span data-ttu-id="c89c4-117">So speichern Sie Hologramme für zukünftige Sitzungen:</span><span class="sxs-lookup"><span data-stu-id="c89c4-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="c89c4-118">Verschaffen Sie sich den worldanchorstore</span><span class="sxs-lookup"><span data-stu-id="c89c4-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="c89c4-119">Speichern eines Welt Ankers, der eine ID angibt</span><span class="sxs-lookup"><span data-stu-id="c89c4-119">Save a world anchor specifying an id</span></span>
3. <span data-ttu-id="c89c4-120">Speichern von App-Daten, die sich auf den Welt Anker beziehen, sowie eine ID</span><span class="sxs-lookup"><span data-stu-id="c89c4-120">Save app data relating to the world anchor along with an id</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="c89c4-121">Der worldanchorstore wird erhalten.</span><span class="sxs-lookup"><span data-stu-id="c89c4-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="c89c4-122">Wir möchten einen Verweis auf den worldanchorstore behalten, damit wir wissen, dass wir bereit sind, wenn wir einen Vorgang durchführen möchten.</span><span class="sxs-lookup"><span data-stu-id="c89c4-122">We will want to keep a reference to the WorldAnchorStore around so we know we are ready to go when we want to perform an operation.</span></span> <span data-ttu-id="c89c4-123">Da es sich hierbei um einen asynchronen-Befehl handelt, der möglicherweise unmittelbar nach dem Start von aufgerufen wird, möchten wir</span><span class="sxs-lookup"><span data-stu-id="c89c4-123">Since this is an async call, potentially as soon as start up, we want to call</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="c89c4-124">Storeloaded ist in diesem Fall der Handler für den Fall, dass der worldanchorstore das Laden abgeschlossen hat:</span><span class="sxs-lookup"><span data-stu-id="c89c4-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="c89c4-125">Wir haben nun einen Verweis auf den worldanchorstore, den wir verwenden werden, um bestimmte Welt Anker zu speichern und zu laden.</span><span class="sxs-lookup"><span data-stu-id="c89c4-125">We now have a reference to the WorldAnchorStore which we will use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="c89c4-126">Speichern von worldanchor</span><span class="sxs-lookup"><span data-stu-id="c89c4-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="c89c4-127">Zum Speichern müssen wir einfach den Namen der Speicherung benennen und Sie an den worldanchor übergeben, den wir vor dem Speichern erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="c89c4-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="c89c4-128">Hinweis: Wenn Sie versuchen, zwei Anker in derselben Zeichenfolge zu speichern, tritt ein Fehler auf (speichern. Save gibt false zurück).</span><span class="sxs-lookup"><span data-stu-id="c89c4-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="c89c4-129">Sie müssen das vorherige Speichern löschen, bevor Sie das neue speichern:</span><span class="sxs-lookup"><span data-stu-id="c89c4-129">You need to Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="c89c4-130">Laden von worldanchor</span><span class="sxs-lookup"><span data-stu-id="c89c4-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="c89c4-131">Und zum Laden:</span><span class="sxs-lookup"><span data-stu-id="c89c4-131">And to load:</span></span>

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

<span data-ttu-id="c89c4-132">Wir können außerdem "Store" verwenden. Delete () um einen Anker zu entfernen, den wir zuvor gespeichert und gespeichert haben. Löschen Sie (), um alle zuvor gespeicherten Daten zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="c89c4-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="c89c4-133">Auflisten vorhandener Anker</span><span class="sxs-lookup"><span data-stu-id="c89c4-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="c89c4-134">Um zuvor gespeicherte Anker zu ermitteln, müssen Sie getallids aufrufen.</span><span class="sxs-lookup"><span data-stu-id="c89c4-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="c89c4-135">Beibehalten von holograms für mehrere Geräte</span><span class="sxs-lookup"><span data-stu-id="c89c4-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="c89c4-136">Sie können mithilfe von <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial</a> Anchor einen permanenten cloudenanchor von einem lokalen worldanchor erstellen, der von Ihrer APP über mehrere hololens-, IOS-und Android-Geräte hinweg gefunden werden kann, selbst wenn diese Geräte nicht gleichzeitig zusammen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="c89c4-136">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices are not present together at the same time.</span></span>  <span data-ttu-id="c89c4-137">Da cloudananker permanent sind, können mehrere Geräte im Lauf der Zeit jeweils Inhalte sehen, die relativ zu diesem Anker am gleichen physischen Standort gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="c89c4-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="c89c4-138">Um mit der Einführung von freigegebenen Erfahrungen in Unity zu beginnen, testen Sie die fünfminütigen <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchor Unity-Schnellstarts</a>.</span><span class="sxs-lookup"><span data-stu-id="c89c4-138">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="c89c4-139">Sobald Sie mit räumlichen Azure-Ankern arbeiten, können Sie <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Anker in Unity erstellen und lokalisieren</a>.</span><span class="sxs-lookup"><span data-stu-id="c89c4-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="c89c4-140">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c89c4-140">See Also</span></span>
* [<span data-ttu-id="c89c4-141">Dauerhaftigkeit räumlicher Anker</span><span class="sxs-lookup"><span data-stu-id="c89c4-141">Spatial anchor persistence</span></span>](coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="c89c4-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="c89c4-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="c89c4-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchor SDK für Unity</a></span><span class="sxs-lookup"><span data-stu-id="c89c4-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
