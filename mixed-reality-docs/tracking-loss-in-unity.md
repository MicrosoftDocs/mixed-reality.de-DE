---
title: Verlust der Überwachung in Unity
description: Behandeln von Datenverlust in einer Unity-app nachverfolgen.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Nachverfolgen von Verlust, -nachverfolgung Verlust image
ms.openlocfilehash: eb675860d67e9cad0d1129b3a6f61343990a4179
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595715"
---
# <a name="tracking-loss-in-unity"></a><span data-ttu-id="28246-104">Verlust der Überwachung in Unity</span><span class="sxs-lookup"><span data-stu-id="28246-104">Tracking loss in Unity</span></span>

<span data-ttu-id="28246-105">Wenn das Gerät in der ganzen Welt finden kann, hat die app "Verlust der Überwachung".</span><span class="sxs-lookup"><span data-stu-id="28246-105">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="28246-106">Standardmäßig werden Unity Anhalten von der Aktualisierungsschleife des und ein Image des Begrüßungsbildschirms für den Benutzer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="28246-106">By default, Unity will pause the update loop and display a splash image to the user.</span></span> <span data-ttu-id="28246-107">Bei der nachverfolgung wieder auf die ist, wird das Image des Begrüßungsbildschirms verschwindet, und der Aktualisierungsschleife des wird fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="28246-107">When tracking is regained, the splash image goes away and the update loop continues.</span></span>

<span data-ttu-id="28246-108">Als Alternative kann der Benutzer manuell dieser Übergang verarbeiten, durch die Einstellung deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="28246-108">As an alternative, the user can manually handle this transition by opting out of the setting.</span></span> <span data-ttu-id="28246-109">Alle Inhalte scheinbar Text gesperrt, während der nachverfolgung verloren gehen, wenn nichts ausgeführt wird, um es zu verarbeiten sind.</span><span class="sxs-lookup"><span data-stu-id="28246-109">All content will seem to become body locked during tracking loss if nothing is done to handle it.</span></span>

## <a name="default-handling"></a><span data-ttu-id="28246-110">Die Standardbehandlung</span><span class="sxs-lookup"><span data-stu-id="28246-110">Default Handling</span></span>

<span data-ttu-id="28246-111">Standardmäßig wird der Aktualisierungsschleife des von der app sowie alle Nachrichten und Ereignisse für die Dauer der nachverfolgung von Verlust beendet.</span><span class="sxs-lookup"><span data-stu-id="28246-111">By default, the update loop of the app as well as all messages and events will stop for the duration of tracking loss.</span></span> <span data-ttu-id="28246-112">Gleichzeitig wird, wird ein Bild für den Benutzer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="28246-112">At that same time, an image will be displayed to the user.</span></span> <span data-ttu-id="28246-113">Sie können dieses Image anpassen, indem Sie zu bearbeiten -> Einstellungen -> Player verwenden, klicken auf die Splash-Image, und Festlegen des Bildformats Holographic nachverfolgung verloren gehen.</span><span class="sxs-lookup"><span data-stu-id="28246-113">You can customize this image by going to Edit->Settings->Player, clicking Splash Image, and setting the Holographic Tracking Loss image.</span></span>

## <a name="manual-handling"></a><span data-ttu-id="28246-114">Manuelle Behandlung</span><span class="sxs-lookup"><span data-stu-id="28246-114">Manual Handling</span></span>

<span data-ttu-id="28246-115">Zum Verlust der Überwachung manuell verarbeiten zu können, müssen Sie besuchen **bearbeiten** > **Projekteinstellungen** > **Player**  >   **Registerkarte "Einstellungen" Universal Windows Platform** > **Splash-Image** > **Windows Holographic** , und deaktivieren Sie "auf nachverfolgung Verlust anhalten und Bild anzeigen ".</span><span class="sxs-lookup"><span data-stu-id="28246-115">To manually handle tracking loss, you need to go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform settings tab** > **Splash Image** > **Windows Holographic** and uncheck "On Tracking Loss Pause and Show Image".</span></span> <span data-ttu-id="28246-116">Nach dem Nachverfolgen von Änderungen mit den APIs, die unten angegebenen behandelt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="28246-116">After which, you need to handle tracking changes with the APIs specified below.</span></span>

<span data-ttu-id="28246-117">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="28246-117">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="28246-118">**Typ:** *WorldManager*</span><span class="sxs-lookup"><span data-stu-id="28246-118">**Type:** *WorldManager*</span></span>

* <span data-ttu-id="28246-119">World-Manager macht eine Ereignis, um die nachverfolgung verloren geht/gewonnen erkennen (*WorldManager.OnPositionalLocatorStateChanged*) und eine Eigenschaft, die den aktuellen Status Abfragen (*WorldManager.state*)</span><span class="sxs-lookup"><span data-stu-id="28246-119">World Manager exposes an event to detect tracking lost/gained (*WorldManager.OnPositionalLocatorStateChanged*) and a property to query the current state (*WorldManager.state*)</span></span>
* <span data-ttu-id="28246-120">Wenn der Status der änderungsnachverfolgung nicht aktiv ist, wird die Kamera nicht angezeigt, in der virtuellen Welt zu übersetzen, auch wenn der Benutzer übersetzt.</span><span class="sxs-lookup"><span data-stu-id="28246-120">When the tracking state is not active, the camera will not appear to translate in the virtual world even as the user translates.</span></span> <span data-ttu-id="28246-121">Dies bedeutet, dass Objekte nicht mehr alle physischen Standort entspricht, und alle gesperrt Text angezeigt.</span><span class="sxs-lookup"><span data-stu-id="28246-121">This means objects will no longer correspond to any physical location and all will appear body locked.</span></span>

<span data-ttu-id="28246-122">Bei der Behandlung von Nachverfolgen von Änderungen auf Ihre eigenen. Sie müssen entweder für den Abruf von der State-Eigenschaft jeder Frame oder das Handle der *OnPositionalLocatorStateChanged* Ereignis.</span><span class="sxs-lookup"><span data-stu-id="28246-122">When handling tracking changes on your own you either need to poll for the state property each frame or handle the *OnPositionalLocatorStateChanged* event.</span></span>

### <a name="polling"></a><span data-ttu-id="28246-123">Abfragezeitplan</span><span class="sxs-lookup"><span data-stu-id="28246-123">Polling</span></span>

<span data-ttu-id="28246-124">Der wichtigste Zustand ist *PositionalLocatorState.Active* d.h. nachverfolgung voll funktionsfähig ist.</span><span class="sxs-lookup"><span data-stu-id="28246-124">The most important state is *PositionalLocatorState.Active* which means tracking is fully functional.</span></span> <span data-ttu-id="28246-125">Jedem anderen Zustand werden an die Hauptkamera nur rotierenden Deltas vorgenommen.</span><span class="sxs-lookup"><span data-stu-id="28246-125">Any other state will result in only rotational deltas to the main camera.</span></span> <span data-ttu-id="28246-126">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="28246-126">For example:</span></span>

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a><span data-ttu-id="28246-127">Behandeln des Ereignisses OnPositionalLocatorStateChanged</span><span class="sxs-lookup"><span data-stu-id="28246-127">Handling the OnPositionalLocatorStateChanged event</span></span>

<span data-ttu-id="28246-128">Alternativ können Sie einfacher, und Sie können auch abonnieren *OnPositionalLocatorStateChanged* , die Übergänge zu behandeln:</span><span class="sxs-lookup"><span data-stu-id="28246-128">Alternatively and more conveniently, you can also subscribe to *OnPositionalLocatorStateChanged* to handle the transitions:</span></span>

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a><span data-ttu-id="28246-129">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="28246-129">See also</span></span>
* [<span data-ttu-id="28246-130">Behandeln von Datenverlust in DirectX nachverfolgen</span><span class="sxs-lookup"><span data-stu-id="28246-130">Handling tracking loss in DirectX</span></span>](coordinate-systems-in-directx.md#handling-tracking-loss)
