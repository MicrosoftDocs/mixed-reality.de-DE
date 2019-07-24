---
title: Aktivieren der Platzierung von 3D-Modellen in der Startseite
description: Platzieren von 3D-Modellen von Ihrer Website oder Anwendung in Windows Mixed Reality Home
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, Modell, Ort in Zuhause, Ort, Welt, Modellierung, gemischte Realität Home, Web, App
ms.openlocfilehash: 954086b79e3614e1b75ceb7560f9fc87435530fa
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829733"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a><span data-ttu-id="4de7d-104">Aktivieren der Platzierung von 3D-Modellen in der Mixed Reality-Startseite</span><span class="sxs-lookup"><span data-stu-id="4de7d-104">Enable placement of 3D models in the mixed reality home</span></span>

> [!NOTE]
> <span data-ttu-id="4de7d-105">Diese Funktion wurde als Teil des [Windows 10-Updates vom April 2018](release-notes-april-2018.md)hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="4de7d-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md).</span></span> <span data-ttu-id="4de7d-106">Ältere Versionen von Windows sind mit diesem Feature nicht kompatibel.</span><span class="sxs-lookup"><span data-stu-id="4de7d-106">Older versions of Windows are not compatible with this feature.</span></span>

<span data-ttu-id="4de7d-107">Der [Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) -Startpunkt ist der Ausgangspunkt, an dem Benutzer vor dem Starten von Anwendungen landen.</span><span class="sxs-lookup"><span data-stu-id="4de7d-107">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="4de7d-108">In einigen Szenarios ermöglichen 2D-Apps (wie die holograms-APP) die Platzierung von 3D-Modellen direkt in der Mixed Reality-Startseite als Dekorationen oder für eine weitere Prüfung in vollständigem 3D.</span><span class="sxs-lookup"><span data-stu-id="4de7d-108">In some scenarios, 2D apps (like the Holograms app) enable placement of 3D models directly into the mixed reality home as decorations or for further inspection in full 3D.</span></span> <span data-ttu-id="4de7d-109">Das *Add Model-Protokoll* ermöglicht es Ihnen, ein 3D-Modell von Ihrer Website oder Anwendung direkt an die Windows Mixed Reality-Startseite zu senden, wo Sie wie [3D-App-Launcher](3d-app-launcher-design-guidance.md), 2D-apps und holograms beibehalten wird.</span><span class="sxs-lookup"><span data-stu-id="4de7d-109">The *add model protocol* allows you to send a 3D model from your website or application directly into the Windows Mixed Reality home, where it will persist like [3D app launchers](3d-app-launcher-design-guidance.md), 2D apps, and holograms.</span></span> 

<span data-ttu-id="4de7d-110">Wenn Sie z. b. eine Anwendung entwickeln, die einen Katalog mit 3D-Möbeln zum Entwerfen eines Raums verwendet, können Sie das *Add Model-Protokoll* verwenden, um Benutzern zu ermöglichen, diese 3D-möbelmodelle aus dem Katalog zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="4de7d-110">For example, if you're developing an application that surfaces a catalog of 3D furniture for designing a space, you can use the *add model protocol* to allow users to place those 3D furniture models from the catalog.</span></span> <span data-ttu-id="4de7d-111">Nachdem die Benutzer in der Welt platziert wurden, können Sie diese 3D-Modelle wie andere holograms in der Startseite verschieben, ändern und ihre Größe ändern.</span><span class="sxs-lookup"><span data-stu-id="4de7d-111">Once placed in the world, users can move, resize, and remove these 3D models just like other holograms in the home.</span></span> <span data-ttu-id="4de7d-112">Dieser Artikel bietet eine Übersicht über die Implementierung des *Add Model-Protokolls* , damit Sie mit der Aktivierung Ihrer Welt mit 3D-Objekten aus Ihrer APP oder dem Web beginnen können.</span><span class="sxs-lookup"><span data-stu-id="4de7d-112">This article provides an overview of implementing the *add model protocol* so that you can start enabling users to decorate their world with 3D objects from your app or the web.</span></span>

## <a name="device-support"></a><span data-ttu-id="4de7d-113">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="4de7d-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4de7d-114"><strong>Funktion</strong></span><span class="sxs-lookup"><span data-stu-id="4de7d-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="4de7d-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4de7d-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4de7d-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="4de7d-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4de7d-117">Modell Protokoll hinzufügen</span><span class="sxs-lookup"><span data-stu-id="4de7d-117">Add model protocol</span></span></td>
        <td><span data-ttu-id="4de7d-118">✔️</span><span class="sxs-lookup"><span data-stu-id="4de7d-118">✔️</span></span></td>
        <td><span data-ttu-id="4de7d-119">✔️</span><span class="sxs-lookup"><span data-stu-id="4de7d-119">✔️</span></span></td>
    </tr>
</table>

## <a name="overview"></a><span data-ttu-id="4de7d-120">Übersicht</span><span class="sxs-lookup"><span data-stu-id="4de7d-120">Overview</span></span>

<span data-ttu-id="4de7d-121">Es gibt zwei Schritte, um die Platzierung von 3D-Modellen in der Windows Mixed Reality-Startseite zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="4de7d-121">There are 2 steps to enabling the placement of 3D models in the Windows Mixed Reality home:</span></span>
1. <span data-ttu-id="4de7d-122">[Stellen Sie sicher, dass Ihr 3D-Modell mit dem Windows Mixed Reality-Home kompatibel ist](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span><span class="sxs-lookup"><span data-stu-id="4de7d-122">[Ensure your 3D model is compatible with the Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span></span>
2. <span data-ttu-id="4de7d-123">Implementieren *Sie das Add Model-Protokoll* in Ihrer Anwendung oder Webseite (in diesem Artikel).</span><span class="sxs-lookup"><span data-stu-id="4de7d-123">Implement the *add model protocol* in your application or webpage (this article).</span></span>

## <a name="implementing-the-add-model-protocol"></a><span data-ttu-id="4de7d-124">Implementieren des *Add Model-Protokolls*</span><span class="sxs-lookup"><span data-stu-id="4de7d-124">Implementing the *add model protocol*</span></span>

<span data-ttu-id="4de7d-125">Sobald Sie über ein [kompatibles 3D-Modell](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)verfügen, können Sie das *Add Model-Protokoll* implementieren, indem Sie den folgenden URI auf einer beliebigen Webseite oder Anwendung aktivieren:</span><span class="sxs-lookup"><span data-stu-id="4de7d-125">Once you have a [compatible 3D model](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), you can implement the *add model protocol* by activating the following URI from any webpage or application:</span></span>

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

<span data-ttu-id="4de7d-126">Wenn der URI auf eine Remote Ressource verweist, wird er automatisch heruntergeladen und in die Startseite eingefügt.</span><span class="sxs-lookup"><span data-stu-id="4de7d-126">If the URI points to a remote resource, then it will automatically be downloaded and placed in the home.</span></span> <span data-ttu-id="4de7d-127">Lokale Ressourcen werden in den App-Datenordner der Mixed Reality-Startseite kopiert, bevor Sie in der Startseite abgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="4de7d-127">Local resources will be copied to the mixed reality home's app data folder before being placed in the home.</span></span> <span data-ttu-id="4de7d-128">Es empfiehlt sich, die Benutzer Funktionalität für Szenarien zu berücksichtigen, in denen der Benutzer möglicherweise eine ältere Version von Windows ausführen kann, die dieses Feature nicht unterstützt, indem Sie die Schaltfläche ausblenden oder nach Möglichkeit deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="4de7d-128">We recommend designing your experience to account for scenarios where the user might be running an older version of Windows that doesn't support this feature by hiding the button or disabling it if possible.</span></span> 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a><span data-ttu-id="4de7d-129">Aufrufen des *Add Model-Protokolls* aus einer universelle Windows-Plattform-App:</span><span class="sxs-lookup"><span data-stu-id="4de7d-129">Invoking the *add model protocol* from a Universal Windows Platform app:</span></span>

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

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a><span data-ttu-id="4de7d-130">Aufrufen des *Add Model-Protokolls* von einer Webseite:</span><span class="sxs-lookup"><span data-stu-id="4de7d-130">Invoking the *add model protocol* from a webpage:</span></span>

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a><span data-ttu-id="4de7d-131">Überlegungen zu immersiven (VR) Headsets</span><span class="sxs-lookup"><span data-stu-id="4de7d-131">Considerations for immersive (VR) headsets</span></span>

* <span data-ttu-id="4de7d-132">Bei immersiven (VR)-Headsets muss das Mixed Reality-Portal vor dem Aufrufen des *Add Model-Protokolls*nicht ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="4de7d-132">For immersive (VR) headsets, the Mixed Reality Portal does not have to be running before invoking the *add model protocol*.</span></span> <span data-ttu-id="4de7d-133">In diesem Fall startet das *Modell zum Hinzufügen von Modellen* das Mixed Reality-Portal und platziert das Objekt direkt an der Stelle, an der das Headset sucht, sobald Sie in der Mixed Reality-Startseite eintreffen.</span><span class="sxs-lookup"><span data-stu-id="4de7d-133">In this case, the *add model protocol* will launch the Mixed Reality Portal and place the object directly where the headset is looking once you arrive in the mixed reality home.</span></span> 
* <span data-ttu-id="4de7d-134">Wenn Sie das *Add Model-Protokoll* vom Desktop aus aufrufen, während das gemischte Reality-Portal bereits ausgeführt wird, stellen Sie sicher, dass das Headset "Awake" ist.</span><span class="sxs-lookup"><span data-stu-id="4de7d-134">When invoking the *add model protocol* from the desktop with the Mixed Reality Portal already running, ensure that the headset is "awake".</span></span> <span data-ttu-id="4de7d-135">Wenn dies nicht der Fall ist, ist die Platzierung nicht erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="4de7d-135">If not, the placement will not succeed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="4de7d-136">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4de7d-136">See also</span></span>

* [<span data-ttu-id="4de7d-137">Erstellen von 3D-Modellen für die Verwendung in der Windows Mixed Reality-Startseite</span><span class="sxs-lookup"><span data-stu-id="4de7d-137">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="4de7d-138">Navigieren auf der Startseite von Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4de7d-138">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
