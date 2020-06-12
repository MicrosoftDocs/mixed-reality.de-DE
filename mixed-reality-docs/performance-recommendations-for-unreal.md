---
title: Leistungsempfehlungen für Unreal
description: Empfehlungen für optimale Leistung von Mixed Reality-Apps in Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Leistung, Optimierung, Einstellungen, Dokumentation
ms.openlocfilehash: 3c65eb519b57457e6c9e9747af0ad75e6a5e1b4d
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330189"
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

![Zieleinstellung „Mobile“](images/unreal/performance-recommendations-img-02.png)

3. Aktualisieren des VR-Renderings:
    * Scrollen Sie zum Abschnitt **Engine**, wählen Sie **Rendering** aus, erweitern Sie den Abschnitt **VR**, und aktivieren Sie sowohl **Instanced Stereo** (Instanziiertes Stereo) als auch **Mobile Multi-View** (Mobile Multiansicht).
        + Gegebenenfalls muss **Mobile Post-Processing** (Mobile Nachbearbeitung) deaktiviert werden, damit **Mobile Multi-View** aktiviert werden kann.

![Zieleinstellung „Mobile“](images/unreal/performance-recommendations-img-03.png)
