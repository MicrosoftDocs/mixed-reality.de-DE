---
title: Blick Eingabe in Unreal
description: Tutorial zum Einrichten von Blick Eingaben für hololens und Unreal Engine
author: hferrone
ms.author: v-haferr
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, hololens 2, Eye Tracking, Blick Eingaben, Head-eingebundene Anzeige, Unreal Engine
ms.openlocfilehash: 0bc8b83a2e840b066eb5e30665584e1c68f7b021
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84551806"
---
# <a name="gaze-input"></a><span data-ttu-id="7620c-104">Blick Eingabe</span><span class="sxs-lookup"><span data-stu-id="7620c-104">Gaze Input</span></span>

## <a name="overview"></a><span data-ttu-id="7620c-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="7620c-105">Overview</span></span>

<span data-ttu-id="7620c-106">Das [Windows Mixed Reality-Plug](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) -in bietet keine integrierten Funktionen für die Überblicks Eingabe, aber hololens 2 unterstützt die Eye-Nachverfolgung.</span><span class="sxs-lookup"><span data-stu-id="7620c-106">The [Windows Mixed Reality plugin](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) doesn’t provide any built-in functions for gaze input, but HoloLens 2 does support eye tracking.</span></span> <span data-ttu-id="7620c-107">Die eigentlichen Überwachungsfunktionen werden von Unreal mit den von Unreal bereitgestellten **Anzeige** -und **Eye Tracking** -APIs bereitgestellt und umfassen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="7620c-107">The actual tracking features are provided by Unreal's **Head Mounted Display** and **Eye Tracking** APIs and include:</span></span>

- <span data-ttu-id="7620c-108">Geräteinformationen</span><span class="sxs-lookup"><span data-stu-id="7620c-108">Device information</span></span>
- <span data-ttu-id="7620c-109">Nach Verfolgungs Sensoren</span><span class="sxs-lookup"><span data-stu-id="7620c-109">Tracking sensors</span></span>
- <span data-ttu-id="7620c-110">Ausrichtung und Position</span><span class="sxs-lookup"><span data-stu-id="7620c-110">Orientation and position</span></span>
- <span data-ttu-id="7620c-111">Clipping-Bereiche</span><span class="sxs-lookup"><span data-stu-id="7620c-111">Clipping panes</span></span>
- <span data-ttu-id="7620c-112">Daten-und Überwachungsinformationen für den Blick</span><span class="sxs-lookup"><span data-stu-id="7620c-112">Gaze data and tracking information</span></span>

<span data-ttu-id="7620c-113">Die vollständige Liste der Features finden Sie in [der Dokumentation zu](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) den Köpfen in der Head-bereit [Stellung](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) von Unreal.</span><span class="sxs-lookup"><span data-stu-id="7620c-113">You can find the full list of features in Unreal's [Head Mounted Display](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) and [Eye Tracking](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) documentation.</span></span>

<span data-ttu-id="7620c-114">Zusätzlich zu den Unreal-APIs sehen Sie sich die Dokumentation zu den [Augenblick-basierten Interaktionen](eye-gaze-interaction.md) für hololens 2 an, und informieren Sie sich darüber, wie die [Augen Verfolgung auf hololens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) funktioniert.</span><span class="sxs-lookup"><span data-stu-id="7620c-114">In addition to the Unreal APIs, check out the documentation on [eye-gaze-based interaction](eye-gaze-interaction.md) for HoloLens 2 and read up on how [eye tracking on HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) works.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7620c-115">Die Eye-Nachverfolgung wird nur auf hololens 2 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="7620c-115">Eye tracking is only supported on HoloLens 2.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="7620c-116">Aktivieren der Eye-Überwachung</span><span class="sxs-lookup"><span data-stu-id="7620c-116">Enabling eye tracking</span></span>
<span data-ttu-id="7620c-117">Die Überblicks Eingabe muss in den hololens-Projekteinstellungen aktiviert werden, bevor Sie eine der Unreal-APIs verwenden können.</span><span class="sxs-lookup"><span data-stu-id="7620c-117">Gaze input needs to be enabled in the HoloLens project settings before you can use any of Unreal's APIs.</span></span> <span data-ttu-id="7620c-118">Wenn die Anwendung gestartet wird, wird im folgenden Screenshot eine Zustimmungsaufforderung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7620c-118">When the application starts you'll see a consent prompt shown in the screenshot below.</span></span>

- <span data-ttu-id="7620c-119">Wählen Sie **Ja** aus, um die Berechtigung festzulegen, und erhalten Sie Zugriff auf die Eingaben.</span><span class="sxs-lookup"><span data-stu-id="7620c-119">Select **Yes** to set the permission and get access to gaze input.</span></span> <span data-ttu-id="7620c-120">Wenn Sie diese Einstellung jederzeit ändern müssen, finden Sie Sie in der App " **Einstellungen** ".</span><span class="sxs-lookup"><span data-stu-id="7620c-120">If you need to change this setting at any time, it can be found in the **Settings** app.</span></span>

![Eye-Eingabe Berechtigungen](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> <span data-ttu-id="7620c-122">Hololens Eye Tracking in Unreal hat nur einen einzelnen Blick Strahl für beide Augen und nicht die zwei Strahlen, die für die Stereoskopie erforderlich sind, was nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="7620c-122">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

<span data-ttu-id="7620c-123">Das ist alles, was Sie tun müssen, um Ihre hololens 2-apps in Unreal mit Blick Eingaben zu versehen.</span><span class="sxs-lookup"><span data-stu-id="7620c-123">That's all the setup you'll need to start adding gaze input to your HoloLens 2 apps in Unreal.</span></span> <span data-ttu-id="7620c-124">Weitere Informationen zu Blick Eingaben und deren Auswirkungen auf Benutzer in gemischter Realität finden Sie unter den folgenden Links.</span><span class="sxs-lookup"><span data-stu-id="7620c-124">More information on gaze input and how it affects users in mixed reality can be found at the links below.</span></span> <span data-ttu-id="7620c-125">Berücksichtigen Sie diese bei der Erstellung interaktiver Umgebungen.</span><span class="sxs-lookup"><span data-stu-id="7620c-125">Be sure to think about these when building your interactive experiences.</span></span>

## <a name="see-also"></a><span data-ttu-id="7620c-126">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="7620c-126">See also</span></span>
* [<span data-ttu-id="7620c-127">Kalibrierung</span><span class="sxs-lookup"><span data-stu-id="7620c-127">Calibration</span></span>](calibration.md)
* [<span data-ttu-id="7620c-128">Komfort</span><span class="sxs-lookup"><span data-stu-id="7620c-128">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="7620c-129">Anvisieren und Ausführen</span><span class="sxs-lookup"><span data-stu-id="7620c-129">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="7620c-130">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="7620c-130">Voice input</span></span>](voice-design.md)
