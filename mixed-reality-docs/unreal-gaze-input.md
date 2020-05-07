---
title: Blick Eingabe in Unreal
description: Erläutert, wie Sie die Überblicks Eingabe in Unreal verwenden
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, hololens, Eye Tracking
ms.openlocfilehash: 7387bb3f25cdbdfac32f508c173fbd098f844e84
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835623"
---
# <a name="gaze-input"></a><span data-ttu-id="bb369-104">Blick Eingabe</span><span class="sxs-lookup"><span data-stu-id="bb369-104">Gaze Input</span></span>

<span data-ttu-id="bb369-105">Das Windows Mixed Reality-Plug-in stellt keine speziellen Funktionen für die Eingabe des Blicks bereit.</span><span class="sxs-lookup"><span data-stu-id="bb369-105">The Windows Mixed Reality plugin doesn’t provide any special functions for the gaze input.</span></span> <span data-ttu-id="bb369-106">Alles funktioniert auch mit der Unreal-Standard-API.</span><span class="sxs-lookup"><span data-stu-id="bb369-106">Everything works though the standard Unreal API.</span></span>

[<span data-ttu-id="bb369-107">Head-Blick-API</span><span class="sxs-lookup"><span data-stu-id="bb369-107">Head gaze API</span></span>](https://docs.unrealengine.com/en-US/BlueprintAPI/Input/HeadMountedDisplay/index.html)

## <a name="eye-tracking"></a><span data-ttu-id="bb369-108">Eyetracking – Blickverfolgung</span><span class="sxs-lookup"><span data-stu-id="bb369-108">Eye tracking</span></span>

<span data-ttu-id="bb369-109">Um die Eye Tracking-API zu verwenden, sollten Entwickler in ihren hololens-Projekteinstellungen die Funktion "Blick Eingabe" aktivieren.</span><span class="sxs-lookup"><span data-stu-id="bb369-109">To use the eye tracking API, developers should enable the “Gaze Input” capability in their HoloLens project settings.</span></span> <span data-ttu-id="bb369-110">Wenn die Anwendung gestartet wird, wird dem Benutzer die folgende Zustimmungsaufforderung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bb369-110">When the application starts, user will see the following consent prompt</span></span>

![Eye-Eingabe Berechtigungen](images/unreal/eye-input-permissions.png)
 
<span data-ttu-id="bb369-112">Wenn der Benutzer seine Berechtigung erteilt, erhält die Anwendung eine Eingabe für den Augenblick.</span><span class="sxs-lookup"><span data-stu-id="bb369-112">If the user gives their permission, the application will get eye gaze input.</span></span> 

<span data-ttu-id="bb369-113">Die Eye Tracking-API von Unreal ist [hier](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html) dokumentiert.</span><span class="sxs-lookup"><span data-stu-id="bb369-113">Unreal’s eye tracking API is documented is [here](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html)</span></span>

<span data-ttu-id="bb369-114">Die technischen Details der Eye-Nachverfolgung finden Sie [hier](eye-tracking.md) .</span><span class="sxs-lookup"><span data-stu-id="bb369-114">The technical details of eye tracking are [here](eye-tracking.md)</span></span>

<span data-ttu-id="bb369-115">Beachten Sie, dass die hololens-Eye-Verfolgung speziell für Unreal einen einzelnen Blick Strahl auf beide Augen hat.</span><span class="sxs-lookup"><span data-stu-id="bb369-115">Note that specifically for Unreal, HoloLens eye tracking has a single gaze ray for both eyes.</span></span> <span data-ttu-id="bb369-116">Hololens stellt keine stereoprotokollierung für den stereodruck bereit.</span><span class="sxs-lookup"><span data-stu-id="bb369-116">HoloLens doesn’t provide stereoscopic eye tracking.</span></span>
