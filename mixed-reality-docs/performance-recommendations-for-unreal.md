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
# <a name="performance-recommendations-for-unreal"></a>Leistungsempfehlungen für Unreal

Dieser Artikel baut auf den [Leistungsempfehlungen für Mixed Reality](understanding-performance-for-mixed-reality.md) auf, legt den Schwerpunkt aber auf spezifische Informationen für die Unreal Engine-Umgebung.

## <a name="recommended-unreal-project-settings"></a>Empfohlenen Unreal-Projekteinstellungen

- Verwenden Sie den mobilen VR-Renderer: Vergewissern Sie sich in Ihren Projekteinstellungen, dass die Zielplattform unter „Project“ (Projekt) > „Target Hardware“ (Zielhardware) auf „Mobile/Tablet“ (Mobilgerät/Tablet) festgelegt ist.
- Deaktivieren Sie Occlusion Culling: Deaktivieren Sie unter „Engine“ > „Rendering“ im Abschnitt „Culling“ das Kontrollkästchen für Occlusion Culling.
    + Sollte Occlusion Culling zum Rendern einer besonders detaillierten Szene erforderlich sein, empfiehlt es sich, unter „Engine“ > „Rendering“ die Option „Support Software Occlusion Culling“ (Softwarebasiertes Occlusion Culling unterstützen) zu aktivieren. Dadurch kann Unreal für das Occlusion Culling die CPU verwenden und entsprechende GPU-Abfragen vermeiden, die bei HoloLens 2 nicht sonderlich effizient sind.
- Aktivieren Sie unter „Engine“ > „Rendering“ in der Kategorie „VR“ sowohl „Instanced Stereo“ (Instanziiertes Stereo) als auch „Mobile Multi-View“ (Mobile Multiansicht). Gegebenenfalls muss „Mobile Post-Processing“ (Mobile Nachbearbeitung) deaktiviert werden, damit „Mobile Multi-View“ (Mobile Multiansicht) aktiviert werden kann.
