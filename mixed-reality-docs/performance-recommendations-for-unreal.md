---
title: Leistungsempfehlungen für Unreal
description: Empfehlungen für optimale Leistung von Mixed Reality-Apps in Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Leistung, Optimierung, Einstellungen, Dokumentation
ms.openlocfilehash: 9f128a3ef09f29fc745c21b09b7ec97f5db33605
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84533122"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="725ce-104">Leistungsempfehlungen für Unreal</span><span class="sxs-lookup"><span data-stu-id="725ce-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="725ce-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="725ce-105">Overview</span></span>

<span data-ttu-id="725ce-106">Dieser Artikel baut auf den [Leistungsempfehlungen für Mixed Reality](understanding-performance-for-mixed-reality.md) auf, legt den Schwerpunkt aber auf spezifische Funktionen der Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="725ce-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="725ce-107">Sie sollten sich zunächst über Engpässe bei Anwendungen, Analyse und Profilerstellung für Mixed Reality-Apps und allgemeine Leistungsfixes informieren, bevor Sie weiterlesen.</span><span class="sxs-lookup"><span data-stu-id="725ce-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="725ce-108">Empfohlenen Unreal-Projekteinstellungen</span><span class="sxs-lookup"><span data-stu-id="725ce-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="725ce-109">Sie finden jede der folgenden Einstellungen unter **Edit > Project Settings** (Bearbeiten > Projekteinstellungen).</span><span class="sxs-lookup"><span data-stu-id="725ce-109">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="725ce-110">Mit dem mobilen VR-Renderer:</span><span class="sxs-lookup"><span data-stu-id="725ce-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="725ce-111">Scrollen Sie zum Abschnitt **Project**, wählen Sie **Target Hardware** (Zielhardware) aus, und legen Sie die Zielplattform auf **Mobile/Tablet** fest.</span><span class="sxs-lookup"><span data-stu-id="725ce-111">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![Zieleinstellung „Mobile“](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="725ce-113">Deaktivieren des Okklusionscullings:</span><span class="sxs-lookup"><span data-stu-id="725ce-113">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="725ce-114">Scrollen Sie zum Abschnitt **Engine**, wählen Sie **Rendering** aus, erweitern Sie den Bereich **Culling**, und deaktivieren Sie **Occlusion Culling**.</span><span class="sxs-lookup"><span data-stu-id="725ce-114">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="725ce-115">Wenn Sie das Okklusionsculling für das Rendern einer detailreichen Szene benötigen, empfiehlt es sich, unter **Engine > Rendering** die Option **Support Software Occlusion Culling** (Softwareokklusionsculling unterstützen) zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="725ce-115">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="725ce-116">Dadurch kann Unreal die CPU verwenden und GPU-Okklusionsabfragen vermeiden, die bei HoloLens 2 keine hohe Performance erzielen.</span><span class="sxs-lookup"><span data-stu-id="725ce-116">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>

![Zieleinstellung „Mobile“](images/unreal/performance-recommendations-img-02.png)

3. <span data-ttu-id="725ce-118">Aktualisieren des VR-Renderings:</span><span class="sxs-lookup"><span data-stu-id="725ce-118">Updating VR rendering:</span></span>
    * <span data-ttu-id="725ce-119">Scrollen Sie zum Abschnitt **Engine**, wählen Sie **Rendering** aus, erweitern Sie den Abschnitt **VR**, und aktivieren Sie sowohl **Instanced Stereo** (Instanziiertes Stereo) als auch **Mobile Multi-View** (Mobile Multiansicht).</span><span class="sxs-lookup"><span data-stu-id="725ce-119">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span>
        + <span data-ttu-id="725ce-120">Gegebenenfalls muss **Mobile Post-Processing** (Mobile Nachbearbeitung) deaktiviert werden, damit **Mobile Multi-View** aktiviert werden kann.</span><span class="sxs-lookup"><span data-stu-id="725ce-120">You may need to uncheck **Mobile Post-Processing** in order to be able to check **Mobile Multi-View**</span></span>

![Zieleinstellung „Mobile“](images/unreal/performance-recommendations-img-03.png)
