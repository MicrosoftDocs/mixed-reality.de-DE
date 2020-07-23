---
title: Leistungsempfehlungen für Unreal
description: Empfehlungen für optimale Leistung von Mixed Reality-Apps in Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Leistung, Optimierung, Einstellungen, Dokumentation
ms.openlocfilehash: a7972962eeb2b1480a7da38210b5ee77104f508b
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303635"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="a2653-104">Leistungsempfehlungen für Unreal</span><span class="sxs-lookup"><span data-stu-id="a2653-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="a2653-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="a2653-105">Overview</span></span>

<span data-ttu-id="a2653-106">Dieser Artikel baut auf den [Leistungsempfehlungen für Mixed Reality](understanding-performance-for-mixed-reality.md) auf, legt den Schwerpunkt aber auf spezifische Funktionen der Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="a2653-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="a2653-107">Sie sollten sich zunächst über Engpässe bei Anwendungen, Analyse und Profilerstellung für Mixed Reality-Apps und allgemeine Leistungsfixes informieren, bevor Sie weiterlesen.</span><span class="sxs-lookup"><span data-stu-id="a2653-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="a2653-108">Empfohlenen Unreal-Projekteinstellungen</span><span class="sxs-lookup"><span data-stu-id="a2653-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="a2653-109">Sie finden jede der folgenden Einstellungen unter **Edit > Project Settings** (Bearbeiten > Projekteinstellungen).</span><span class="sxs-lookup"><span data-stu-id="a2653-109">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="a2653-110">Mit dem mobilen VR-Renderer:</span><span class="sxs-lookup"><span data-stu-id="a2653-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="a2653-111">Scrollen Sie zum Abschnitt **Project**, wählen Sie **Target Hardware** (Zielhardware) aus, und legen Sie die Zielplattform auf **Mobile/Tablet** fest.</span><span class="sxs-lookup"><span data-stu-id="a2653-111">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![Zieleinstellung „Mobile“](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="a2653-113">Deaktivieren des Okklusionscullings:</span><span class="sxs-lookup"><span data-stu-id="a2653-113">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="a2653-114">Scrollen Sie zum Abschnitt **Engine**, wählen Sie **Rendering** aus, erweitern Sie den Bereich **Culling**, und deaktivieren Sie **Occlusion Culling**.</span><span class="sxs-lookup"><span data-stu-id="a2653-114">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="a2653-115">Wenn Sie das Okklusionsculling für das Rendern einer detailreichen Szene benötigen, empfiehlt es sich, unter **Engine > Rendering** die Option **Support Software Occlusion Culling** (Softwareokklusionsculling unterstützen) zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="a2653-115">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="a2653-116">Dadurch kann Unreal die CPU verwenden und GPU-Okklusionsabfragen vermeiden, die bei HoloLens 2 keine hohe Performance erzielen.</span><span class="sxs-lookup"><span data-stu-id="a2653-116">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>

![Deaktivieren des Okklusionscullings](images/unreal/performance-recommendations-img-02.png)

3. <span data-ttu-id="a2653-118">In der mobilen Multiansicht:</span><span class="sxs-lookup"><span data-stu-id="a2653-118">Using mobile multi-view:</span></span>
    * <span data-ttu-id="a2653-119">Scrollen Sie zum Abschnitt **Engine**, wählen Sie **Rendering** aus, erweitern Sie den Abschnitt **VR**, und aktivieren Sie sowohl **Instanced Stereo** (Instanziiertes Stereo) als auch **Mobile Multi-View** (Mobile Multiansicht).</span><span class="sxs-lookup"><span data-stu-id="a2653-119">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span> <span data-ttu-id="a2653-120">Mobile-HDR sollte deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="a2653-120">Mobile HDR should be unchecked.</span></span>

![VR-Renderingeinstellungen](images/unreal/performance-recommendations-img-03.png)

4. <span data-ttu-id="a2653-122">Legen Sie die **Maximum number of CSM cascades to render** (Maximale Anzahl der zu rendernden CSM-Kaskaden) auf **1** und **Max Movable Spotlights / Point Lights** (Maximale Anzahl der beweglichen Spotlights/Punktlichter) auf **0** fest.</span><span class="sxs-lookup"><span data-stu-id="a2653-122">Setting the **Maximum number of CSM cascades to render** to **1** and **Max Movable Spotlights / Point Lights** to **0**.</span></span> 
