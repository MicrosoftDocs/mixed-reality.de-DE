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
# <a name="performance-recommendations-for-unreal"></a>Leistungsempfehlungen für Unreal

## <a name="overview"></a>Übersicht

Dieser Artikel baut auf den [Leistungsempfehlungen für Mixed Reality](understanding-performance-for-mixed-reality.md) auf, legt den Schwerpunkt aber auf spezifische Funktionen der Unreal Engine. Sie sollten sich zunächst über Engpässe bei Anwendungen, Analyse und Profilerstellung für Mixed Reality-Apps und allgemeine Leistungsfixes informieren, bevor Sie weiterlesen.

## <a name="recommended-unreal-project-settings"></a>Empfohlenen Unreal-Projekteinstellungen
Sie finden jede der folgenden Einstellungen unter **Edit > Project Settings** (Bearbeiten > Projekteinstellungen).

1. Mit dem mobilen VR-Renderer:
    * Scrollen Sie zum Abschnitt **Project**, wählen Sie **Target Hardware** (Zielhardware) aus, und legen Sie die Zielplattform auf **Mobile/Tablet** fest.

![Zieleinstellung „Mobile“](images/unreal/performance-recommendations-img-01.png)

2. Deaktivieren des Okklusionscullings:
    * Scrollen Sie zum Abschnitt **Engine**, wählen Sie **Rendering** aus, erweitern Sie den Bereich **Culling**, und deaktivieren Sie **Occlusion Culling**.
        + Wenn Sie das Okklusionsculling für das Rendern einer detailreichen Szene benötigen, empfiehlt es sich, unter **Engine > Rendering** die Option **Support Software Occlusion Culling** (Softwareokklusionsculling unterstützen) zu aktivieren. Dadurch kann Unreal die CPU verwenden und GPU-Okklusionsabfragen vermeiden, die bei HoloLens 2 keine hohe Performance erzielen.

![Deaktivieren des Okklusionscullings](images/unreal/performance-recommendations-img-02.png)

3. In der mobilen Multiansicht:
    * Scrollen Sie zum Abschnitt **Engine**, wählen Sie **Rendering** aus, erweitern Sie den Abschnitt **VR**, und aktivieren Sie sowohl **Instanced Stereo** (Instanziiertes Stereo) als auch **Mobile Multi-View** (Mobile Multiansicht). Mobile-HDR sollte deaktiviert werden.

![VR-Renderingeinstellungen](images/unreal/performance-recommendations-img-03.png)

4. Legen Sie die **Maximum number of CSM cascades to render** (Maximale Anzahl der zu rendernden CSM-Kaskaden) auf **1** und **Max Movable Spotlights / Point Lights** (Maximale Anzahl der beweglichen Spotlights/Punktlichter) auf **0** fest. 
