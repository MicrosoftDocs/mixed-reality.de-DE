---
title: In-App-Käufe
description: In-app-Käufe werden in mixed Reality-apps unterstützt, aber es gibt einiges zu deren Einrichtung.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: in-app-Käufe, hololens
ms.openlocfilehash: bc96893d1777e94295285736982fd9a7167240a4
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595781"
---
# <a name="in-app-purchases"></a><span data-ttu-id="be76f-104">In-App-Käufe</span><span class="sxs-lookup"><span data-stu-id="be76f-104">In-app purchases</span></span>

<span data-ttu-id="be76f-105">In-app-Käufe werden in HoloLens unterstützt, aber es gibt einiges zu deren Einrichtung.</span><span class="sxs-lookup"><span data-stu-id="be76f-105">In-app purchases are supported in HoloLens, but there is some work to set them up.</span></span>

<span data-ttu-id="be76f-106">Um den in-app-Kauf nutzen zu können Funktionen, müssen Sie:</span><span class="sxs-lookup"><span data-stu-id="be76f-106">In order to leverage the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="be76f-107">Erstellen Sie eine XAML [2D-Ansicht](app-views.md) als ein Slate angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="be76f-107">Create a XAML [2D view](app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="be76f-108">Um die Platzierung zu aktivieren, das Ansicht des immersive verlässt wechseln</span><span class="sxs-lookup"><span data-stu-id="be76f-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="be76f-109">Die API aufrufen: "await" [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="be76f-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="be76f-110">Diese API wird das vordefinierte Windows-Betriebssystem-Popup angezeigt, die zeigt, die in-app-Käufe Name, Beschreibung und Preis.</span><span class="sxs-lookup"><span data-stu-id="be76f-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="be76f-111">Der Benutzer kann dann Kaufoptionen auswählen.</span><span class="sxs-lookup"><span data-stu-id="be76f-111">The user can then choose purchase options.</span></span> <span data-ttu-id="be76f-112">Sobald die Aktion abgeschlossen ist, die app auf der Benutzeroberfläche anzuzeigen, die dem Benutzer ermöglicht, wechseln Sie zurück zur muss seine [immersive Ansicht](app-views.md).</span><span class="sxs-lookup"><span data-stu-id="be76f-112">Once the action is completed, the app will need to present UI which allows the user to switch back to its [immersive view](app-views.md).</span></span>

<span data-ttu-id="be76f-113">Für apps für Desktop-basierten Windows Mixed Reality immersive Headsets ist es nicht erforderlich, manuell zu einer XAML-Ansicht vor dem Aufrufen der API RequestProductPurchaseAsync umschalten.</span><span class="sxs-lookup"><span data-stu-id="be76f-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it is not required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
