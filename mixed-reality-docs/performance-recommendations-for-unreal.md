---
title: Leistungsempfehlungen für Unreal
description: Empfehlungen für optimale Leistung von Mixed Reality-Apps in Unreal
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Leistung, Optimierung, Einstellungen, Dokumentation
ms.openlocfilehash: 1fab2f714628f61a518d89795cf644e90130200a
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840199"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="88b40-104">Leistungsempfehlungen für Unreal</span><span class="sxs-lookup"><span data-stu-id="88b40-104">Performance recommendations for Unreal</span></span>

<span data-ttu-id="88b40-105">Dieser Artikel baut auf den [Leistungsempfehlungen für Mixed Reality](understanding-performance-for-mixed-reality.md) auf, legt den Schwerpunkt aber auf spezifische Informationen für die Unreal Engine-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="88b40-105">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md) but focuses on learnings specific to the Unreal Engine environment.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="88b40-106">Empfohlenen Unreal-Projekteinstellungen</span><span class="sxs-lookup"><span data-stu-id="88b40-106">Recommended Unreal project settings</span></span>

- <span data-ttu-id="88b40-107">Verwenden Sie den mobilen VR-Renderer: Vergewissern Sie sich in Ihren Projekteinstellungen, dass die Zielplattform unter „Project“ (Projekt) > „Target Hardware“ (Zielhardware) auf „Mobile/Tablet“ (Mobilgerät/Tablet) festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="88b40-107">Use the mobile VR renderer- in your project settings, ensure your target platform is set to "Mobile/Tablet" under "Project – Target Hardware"</span></span>
- <span data-ttu-id="88b40-108">Deaktivieren Sie Occlusion Culling: Deaktivieren Sie unter „Engine“ > „Rendering“ im Abschnitt „Culling“ das Kontrollkästchen für Occlusion Culling.</span><span class="sxs-lookup"><span data-stu-id="88b40-108">Disable occlusion culling- under "Engine – Rendering" in the "Culling" section, uncheck "Occlusion Culling"</span></span>
    + <span data-ttu-id="88b40-109">Sollte Occlusion Culling zum Rendern einer besonders detaillierten Szene erforderlich sein, empfiehlt es sich, unter „Engine“ > „Rendering“ die Option „Support Software Occlusion Culling“ (Softwarebasiertes Occlusion Culling unterstützen) zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="88b40-109">If occlusion culling is required because a very detailed scene needs to be rendered, it is recommended that "Support Software Occlusion Culling" is enabled Under "Engine – Rendering".</span></span> <span data-ttu-id="88b40-110">Dadurch kann Unreal für das Occlusion Culling die CPU verwenden und entsprechende GPU-Abfragen vermeiden, die bei HoloLens 2 nicht sonderlich effizient sind.</span><span class="sxs-lookup"><span data-stu-id="88b40-110">This allows Unreal to do occlusion culling on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
- <span data-ttu-id="88b40-111">Aktivieren Sie unter „Engine“ > „Rendering“ in der Kategorie „VR“ sowohl „Instanced Stereo“ (Instanziiertes Stereo) als auch „Mobile Multi-View“ (Mobile Multiansicht).</span><span class="sxs-lookup"><span data-stu-id="88b40-111">Enable both "Instanced Stereo" and "Mobile Multi-View" under "Engine – Rendering" in the "VR" category.</span></span> <span data-ttu-id="88b40-112">Gegebenenfalls muss „Mobile Post-Processing“ (Mobile Nachbearbeitung) deaktiviert werden, damit „Mobile Multi-View“ (Mobile Multiansicht) aktiviert werden kann.</span><span class="sxs-lookup"><span data-stu-id="88b40-112">You may need to uncheck "Mobile Post-Processing" in order to be able to check "Mobile Multi-View"</span></span>
