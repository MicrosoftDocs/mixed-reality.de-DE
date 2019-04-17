---
title: Aktivieren Sie die Platzierung von 3D-Modellen zu Hause
description: Wie 3D-Modelle aus Ihrer Website oder Anwendung in die Windows Mixed Reality home abgelegt.
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, Modell, an Startseite, Ort, weltweit, Modellierung, mixed Reality home, Web, app
ms.openlocfilehash: 3a50353aae8e03c3ebb3ee9ec2f642f21836e925
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605024"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a><span data-ttu-id="2635d-104">Aktivieren Sie die Platzierung von 3D-Modellen in die gemischte Realität home</span><span class="sxs-lookup"><span data-stu-id="2635d-104">Enable placement of 3D models in the mixed reality home</span></span>

> [!NOTE]
> <span data-ttu-id="2635d-105">Dieses Feature wurde hinzugefügt, als Teil der [Windows 10 April 2018 Update](release-notes-april-2018.md).</span><span class="sxs-lookup"><span data-stu-id="2635d-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md).</span></span> <span data-ttu-id="2635d-106">Ältere Versionen von Windows sind nicht mit diesem Feature kompatibel.</span><span class="sxs-lookup"><span data-stu-id="2635d-106">Older versions of Windows are not compatible with this feature.</span></span>

<span data-ttu-id="2635d-107">Die [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) ist der Ausgangspunkt, in denen Benutzer weitergeleitet, vor dem Starten von Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="2635d-107">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="2635d-108">In einigen Szenarien ermöglichen Direct2D-apps (z. B. die app Hologramme) Platzierung von 3D-Modellen direkt in die mixed Reality-Homepage, Ergänzungen oder zur weiteren Untersuchung in vollständigem 3D.</span><span class="sxs-lookup"><span data-stu-id="2635d-108">In some scenarios, 2D apps (like the Holograms app) enable placement of 3D models directly into the mixed reality home as decorations or for further inspection in full 3D.</span></span> <span data-ttu-id="2635d-109">Die *Modell Protokoll hinzufügen,* können Sie ein 3D-Modell auf Ihrer Website oder Anwendung direkt in die Windows Mixed Reality home, senden, wo es beibehalten werden wie [3D app-startfeldern von](3d-app-launcher-design-guidance.md), Direct2D-apps und -Hologramme.</span><span class="sxs-lookup"><span data-stu-id="2635d-109">The *add model protocol* allows you to send a 3D model from your website or application directly into the Windows Mixed Reality home, where it will persist like [3D app launchers](3d-app-launcher-design-guidance.md), 2D apps, and holograms.</span></span> 

<span data-ttu-id="2635d-110">Z. B. Wenn Sie einer Anwendung, auf einen Katalog mit 3D Möbel für das Entwerfen von einem Leerzeichen entwickeln, können die *Modell Protokoll hinzufügen,* , dass Benutzer diese 3D Möbel Modelle aus dem Katalog zu platzieren können.</span><span class="sxs-lookup"><span data-stu-id="2635d-110">For example, if you're developing an application that surfaces a catalog of 3D furniture for designing a space, you can use the *add model protocol* to allow users to place those 3D furniture models from the catalog.</span></span> <span data-ttu-id="2635d-111">Sobald in der Welt platziert wird, können Benutzer verschieben, Ändern der Größe und entfernen diese 3D-Modelle genau wie andere Hologramme zu Hause.</span><span class="sxs-lookup"><span data-stu-id="2635d-111">Once placed in the world, users can move, resize, and remove these 3D models just like other holograms in the home.</span></span> <span data-ttu-id="2635d-112">Dieser Artikel bietet einen Überblick über die Implementierung der *Modell Protokoll hinzufügen,* , damit Sie beginnen können Benutzern ermöglichen, ihre Welt 3D-Objekte aus Ihrer app oder im Internet zu ergänzen.</span><span class="sxs-lookup"><span data-stu-id="2635d-112">This article provides an overview of implementing the *add model protocol* so that you can start enabling users to decorate their world with 3D objects from your app or the web.</span></span>

## <a name="device-support"></a><span data-ttu-id="2635d-113">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="2635d-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="2635d-114">Feature</span><span class="sxs-lookup"><span data-stu-id="2635d-114">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="2635d-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="2635d-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="2635d-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="2635d-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="2635d-117">Modell-Protokoll hinzufügen</span><span class="sxs-lookup"><span data-stu-id="2635d-117">Add model protocol</span></span></td><td style="text-align: center;"> <span data-ttu-id="2635d-118">✔️</span><span class="sxs-lookup"><span data-stu-id="2635d-118">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="2635d-119">✔️</span><span class="sxs-lookup"><span data-stu-id="2635d-119">✔️</span></span></td>
</tr>
</table>

## <a name="overview"></a><span data-ttu-id="2635d-120">Übersicht</span><span class="sxs-lookup"><span data-stu-id="2635d-120">Overview</span></span>

<span data-ttu-id="2635d-121">Es gibt 2 Schritte aus, um die Platzierung von 3D-Modellen in die Windows Mixed Reality home aktivieren:</span><span class="sxs-lookup"><span data-stu-id="2635d-121">There are 2 steps to enabling the placement of 3D models in the Windows Mixed Reality home:</span></span>
1. <span data-ttu-id="2635d-122">[Stellen Sie sicher, Ihre 3D-Modell ist kompatibel mit der Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span><span class="sxs-lookup"><span data-stu-id="2635d-122">[Ensure your 3D model is compatible with the Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span></span>
2. <span data-ttu-id="2635d-123">Implementieren der *Modell Protokoll hinzufügen,* in Ihrer Anwendung oder Webseite (dieser Artikel).</span><span class="sxs-lookup"><span data-stu-id="2635d-123">Implement the *add model protocol* in your application or webpage (this article).</span></span>

## <a name="implementing-the-add-model-protocol"></a><span data-ttu-id="2635d-124">Implementieren der *Modell Protokoll hinzufügen*</span><span class="sxs-lookup"><span data-stu-id="2635d-124">Implementing the *add model protocol*</span></span>

<span data-ttu-id="2635d-125">Nachdem Sie haben eine [kompatibel 3D-Modell](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), können Sie implementieren die *Modell Protokoll hinzufügen,* durch den folgenden URI von einer Webseite oder Anwendung zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="2635d-125">Once you have a [compatible 3D model](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), you can implement the *add model protocol* by activating the following URI from any webpage or application:</span></span>

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

<span data-ttu-id="2635d-126">Wenn der URI mit einer Remoteressource verweist, wird dann automatisch heruntergeladen und zu Hause platziert.</span><span class="sxs-lookup"><span data-stu-id="2635d-126">If the URI points to a remote resource, then it will automatically be downloaded and placed in the home.</span></span> <span data-ttu-id="2635d-127">Lokale Ressourcen werden in app-Datenordner der mixed Reality-Startseite kopiert werden, bevor Sie zu Hause platziert wird.</span><span class="sxs-lookup"><span data-stu-id="2635d-127">Local resources will be copied to the mixed reality home's app data folder before being placed in the home.</span></span> <span data-ttu-id="2635d-128">Es wird empfohlen, Entwerfen Ihre Erfahrung mit Konto für Szenarien, in denen der Benutzer eine ältere Version von Windows kann, die diese Funktion nicht unterstützt ausgeführt werden, durch die Schaltfläche ausblenden oder deaktivieren es nach Möglichkeit.</span><span class="sxs-lookup"><span data-stu-id="2635d-128">We recommend designing your experience to account for scenarios where the user might be running an older version of Windows that doesn't support this feature by hiding the button or disabling it if possible.</span></span> 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a><span data-ttu-id="2635d-129">Aufrufen der *Modell Protokoll hinzufügen,* aus einer universellen Windows-Plattform-app:</span><span class="sxs-lookup"><span data-stu-id="2635d-129">Invoking the *add model protocol* from a Universal Windows Platform app:</span></span>

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a><span data-ttu-id="2635d-130">Aufrufen der *Modell Protokoll hinzufügen,* über eine Webseite:</span><span class="sxs-lookup"><span data-stu-id="2635d-130">Invoking the *add model protocol* from a webpage:</span></span>

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a><span data-ttu-id="2635d-131">Überlegungen für immersive Headsets von (VR)</span><span class="sxs-lookup"><span data-stu-id="2635d-131">Considerations for immersive (VR) headsets</span></span>

* <span data-ttu-id="2635d-132">Für immersive Headsets (VR), Mixed Reality Portal muss nicht vor dem Aufrufen ausgeführt wird, werden die *Modell Protokoll hinzufügen,*.</span><span class="sxs-lookup"><span data-stu-id="2635d-132">For immersive (VR) headsets, the Mixed Reality Portal does not have to be running before invoking the *add model protocol*.</span></span> <span data-ttu-id="2635d-133">In diesem Fall die *Modell Protokoll hinzufügen,* startet das Mixed Reality-Portal und platzieren Sie das Objekt direkt, in denen die Kopfhörer sucht nach der Sie in der die gemischte Realität Startseite gelangen.</span><span class="sxs-lookup"><span data-stu-id="2635d-133">In this case, the *add model protocol* will launch the Mixed Reality Portal and place the object directly where the headset is looking once you arrive in the mixed reality home.</span></span> 
* <span data-ttu-id="2635d-134">Beim Aufrufen der *Modell Protokoll hinzufügen,* auf dem Desktop mit dem Mixed Reality-Portal bereits ausgeführt wird, stellen Sie sicher, dass die Kopfhörer "aktiv" ist.</span><span class="sxs-lookup"><span data-stu-id="2635d-134">When invoking the *add model protocol* from the desktop with the Mixed Reality Portal already running, ensure that the headset is "awake".</span></span> <span data-ttu-id="2635d-135">Wenn dies nicht der Fall ist, wird die Platzierung nicht erfolgreich ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="2635d-135">If not, the placement will not succeed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="2635d-136">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2635d-136">See also</span></span>

* [<span data-ttu-id="2635d-137">Erstellen von 3D-Modellen für die Verwendung zu Hause Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="2635d-137">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="2635d-138">Navigieren Sie in der Windows Mixed Reality home</span><span class="sxs-lookup"><span data-stu-id="2635d-138">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
