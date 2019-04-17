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
# <a name="persistence-in-unity"></a><span data-ttu-id="ceb1b-104">Dauerhaftigkeit in Unity</span><span class="sxs-lookup"><span data-stu-id="ceb1b-104">Persistence in Unity</span></span>

<span data-ttu-id="ceb1b-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span><span class="sxs-lookup"><span data-stu-id="ceb1b-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="ceb1b-106">**Klasse:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="ceb1b-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="ceb1b-107">Die WorldAnchorStore ist der Schlüssel zum Erstellen von holographic Erfahrungen Hologramme, in denen bestimmte realen Positionen behalten Sie für Instanzen der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="ceb1b-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="ceb1b-108">Mit diesem können Ihre Benutzer einzelne Hologramme oder in einem Arbeitsbereich anheften, wo sie möchten, und suchen Sie es später noch Mal, erwarten sie, dass über viele Verwendungen von Ihrer app.</span><span class="sxs-lookup"><span data-stu-id="ceb1b-108">This lets your users pin individual holograms or a workspace wherever they want it, and then find it later where they expect over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="ceb1b-109">Gewusst wie: Hologramme sitzungsübergreifend beibehalten.</span><span class="sxs-lookup"><span data-stu-id="ceb1b-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="ceb1b-110">Die WorldAnchorStore können Sie den Speicherort des WorldAnchor über Sitzungen hinweg beibehalten werden.</span><span class="sxs-lookup"><span data-stu-id="ceb1b-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="ceb1b-111">Damit tatsächlich Hologramme sitzungsübergreifend beibehalten können, müssen Sie separat Ihre "gameobjects" mitverfolgen, die einen bestimmtes Welt Anker verwenden.</span><span class="sxs-lookup"><span data-stu-id="ceb1b-111">To actually persist holograms across sessions, you will need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="ceb1b-112">Es ist oft sinnvoll, erstellen Sie ein "gameobject"-Stamm mit einem Welt Anker und die untergeordneten Elemente aufweisen Hologramme verankert ist es mit einer lokalen Offsetposition.</span><span class="sxs-lookup"><span data-stu-id="ceb1b-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="ceb1b-113">So laden Sie Hologramme aus früheren Sitzungen:</span><span class="sxs-lookup"><span data-stu-id="ceb1b-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="ceb1b-114">Abrufen der WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="ceb1b-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="ceb1b-115">Laden Sie die app-Daten, die im Zusammenhang mit der Welt Anker dadurch die Welt Anker-id</span><span class="sxs-lookup"><span data-stu-id="ceb1b-115">Load app data relating to the world anchor which gives you the id of the world anchor</span></span>
3. <span data-ttu-id="ceb1b-116">Laden Sie einen Anker der Welt aus der id</span><span class="sxs-lookup"><span data-stu-id="ceb1b-116">Load a world anchor from its id</span></span>

<span data-ttu-id="ceb1b-117">Um Hologramme für zukünftige Sitzungen zu speichern:</span><span class="sxs-lookup"><span data-stu-id="ceb1b-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="ceb1b-118">Abrufen der WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="ceb1b-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="ceb1b-119">Speichern Sie einen World Anker-Id angeben</span><span class="sxs-lookup"><span data-stu-id="ceb1b-119">Save a world anchor specifying an id</span></span>
3. <span data-ttu-id="ceb1b-120">Speichern von app-Daten, die im Zusammenhang mit der ganzen Welt Anker zusammen mit einer id</span><span class="sxs-lookup"><span data-stu-id="ceb1b-120">Save app data relating to the world anchor along with an id</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="ceb1b-121">Abrufen der WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="ceb1b-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="ceb1b-122">Wir möchten einen Verweis auf die WorldAnchorStore, um zu speichern, damit wir wissen, dass wir können soll, wenn wir einen Vorgang ausführen möchten.</span><span class="sxs-lookup"><span data-stu-id="ceb1b-122">We will want to keep a reference to the WorldAnchorStore around so we know we are ready to go when we want to perform an operation.</span></span> <span data-ttu-id="ceb1b-123">Da dies einem asynchronen Aufruf möglicherweise so bald wie Start, ist, das wir aufrufen möchten</span><span class="sxs-lookup"><span data-stu-id="ceb1b-123">Since this is an async call, potentially as soon as start up, we want to call</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="ceb1b-124">In diesem Fall ist die StoreLoaded unseren Handler für die bei der WorldAnchorStore Ladevorgang abgeschlossen ist:</span><span class="sxs-lookup"><span data-stu-id="ceb1b-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="ceb1b-125">Wir haben jetzt einen Verweis auf die WorldAnchorStore der zum Speichern und Laden von bestimmten Welt Anker verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ceb1b-125">We now have a reference to the WorldAnchorStore which we will use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="ceb1b-126">Speichern einer WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="ceb1b-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="ceb1b-127">Um zu speichern, müssen wir einfach nennen, was wir speichern, und geben Sie ihn der WorldAnchor wir vor dem haben, wenn wir speichern möchten.</span><span class="sxs-lookup"><span data-stu-id="ceb1b-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="ceb1b-128">Hinweis: zwei Anker auf die gleiche Zeichenfolge speichern möchten (Speicher. fehl Speichervorgang wird "false" zurückgegeben).</span><span class="sxs-lookup"><span data-stu-id="ceb1b-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="ceb1b-129">Sie müssen die vorherige speichern vor dem Speichern der neuen löschen:</span><span class="sxs-lookup"><span data-stu-id="ceb1b-129">You need to Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="ceb1b-130">Laden eine WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="ceb1b-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="ceb1b-131">Und zum Laden:</span><span class="sxs-lookup"><span data-stu-id="ceb1b-131">And to load:</span></span>

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

<span data-ttu-id="ceb1b-132">Wir können außerdem Store verwenden. Speicher und Delete() einen Anker zu entfernen, die zuvor gespeichert haben. Clear() So entfernen Sie alle zuvor gespeicherte Daten.</span><span class="sxs-lookup"><span data-stu-id="ceb1b-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="ceb1b-133">Auflisten vorhandener Anker</span><span class="sxs-lookup"><span data-stu-id="ceb1b-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="ceb1b-134">Rufen Sie zum Ermitteln von zuvor gespeicherten Anker GetAllIds.</span><span class="sxs-lookup"><span data-stu-id="ceb1b-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="ceb1b-135">Beibehalten von Hologramme für mehrere Geräte</span><span class="sxs-lookup"><span data-stu-id="ceb1b-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="ceb1b-136">Können Sie <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure räumliche Anker</a> einen dauerhafte Anker aus einer lokalen WorldAnchor, zu erstellen, die Ihrer app klicken Sie dann über mehrere HoloLens, iOS und Android-Geräte suchen kann, selbst wenn diese Geräte nicht zur gleichen zusammen vorhanden sind Zeit.</span><span class="sxs-lookup"><span data-stu-id="ceb1b-136">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices are not present together at the same time.</span></span>  <span data-ttu-id="ceb1b-137">Da cloudanker dauerhaft sind, können mehrere Geräte im Laufe der Zeit jeweils Inhalt gerendert wird, relativ zu diesem-Anker wird in demselben physischen Standort angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ceb1b-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="ceb1b-138">Informationen zum Einstieg gemeinsame Erfahrungen in Unity erstellen, Testen der 5-Minuten- <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure räumliche Anker Unity-Schnellstarts</a>.</span><span class="sxs-lookup"><span data-stu-id="ceb1b-138">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="ceb1b-139">Sobald Sie mit Azure räumliche Anker die betriebsbereit sind, können Sie dann <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">erstellen, und suchen Sie in Unity Anker</a>.</span><span class="sxs-lookup"><span data-stu-id="ceb1b-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="ceb1b-140">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ceb1b-140">See Also</span></span>
* [<span data-ttu-id="ceb1b-141">Räumliche Anchor-Persistenz</span><span class="sxs-lookup"><span data-stu-id="ceb1b-141">Spatial anchor persistence</span></span>](coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="ceb1b-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure räumliche Anker</a></span><span class="sxs-lookup"><span data-stu-id="ceb1b-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="ceb1b-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure räumliche Anker SDK für Unity</a></span><span class="sxs-lookup"><span data-stu-id="ceb1b-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
