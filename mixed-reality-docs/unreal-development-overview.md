---
title: Ureal-Entwicklung – Übersicht
description: Erste Schritte beim Erstellen von Mixed Reality-Apps in Unreal.
author: sw5813
ms.author: suwu
ms.date: 10/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Beta, Streamen, Remoting, Mixed Reality, Entwicklung, erste Schritte, neues Projekt, Emulator, Dokumentation
ms.openlocfilehash: 96b0259e4ac567389f999d3a453fb68bb848b266
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "74491173"
---
# <a name="unreal-development-overview"></a>Ureal-Entwicklung – Übersicht

Die Mixed Reality-Unterstützung für Unreal Engine 4 ist jetzt als Betaversion verfügbar! Wenn Sie neu in die Entwicklung mit Unreal einsteigen, ist <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">Erste Schritte mit Unreal Engine 4</a> eine hervorragende Seite, die Sie erforschen sollten. Wenn Sie Ressourcen benötigen, finden Sie diese im umfangreich ausgestatteten <a href="https://www.unrealengine.com/marketplace//store" target="_blank">Asset Store</a>. 

Nachdem Sie ein grundlegendes Verständnis von Unreal Engine 4 erworben haben, können Sie die Seite zur <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Microsoft HoloLens-Entwicklung</a> auf der Dokumentations-Website der Unreal Engine besuchen, um zu erfahren, wie Sie Ihre Apps in HoloLens erstellen und ausführen. Besuchen Sie unbedingt die <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Unreal Mixed Reality-Foren</a>, und befassen Sie sich mit der Community, die Mixed Reality-Apps in Unreal entwickelt. Es ist ein guter Ausgangspunkt, um Lösungen für möglicherweise auftretende Probleme zu finden.

## <a name="installing-the-prerequisites"></a>Installieren der erforderlichen Komponenten

Um in das Erstellen einer HoloLens 2-App in Unreal einzusteigen, benötigen Sie den [HoloLens 2-Emulator](using-the-hololens-emulator.md) oder ein HoloLens-Headset. Ferner müssen Sie die neueste Version von Visual Studio mit den Workloads und Komponenten installieren, die unter <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/Prerequisites/index.html" target="_blank">Erforderliche Komponenten für HoloLens 2 für Unreal</a> aufgelistet sind.

## <a name="building-and-running-your-unreal-app"></a>Entwickeln und Ausführen Ihrer Unreal-App

Im ersten Schritt <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/HowTo/PackageApp/index.html" target="_blank">verpacken Sie Ihre App für HoloLens 2</a>. Wählen Sie als nächstes aus, wo Sie das Paket bereitstellen möchten:
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartEmulator/index.html" target="_blank">Bereitstellen auf dem HoloLens 2-Emulator</a>
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartDevice/index.html" target="_blank">Bereitstellen auf einem HoloLens 2-Headset</a>

## <a name="streaming-your-app-to-a-headset-via-the-holographic-remoting-player"></a>Streaming Ihrer App auf ein Headset mithilfe des Holographic Remoting Players

Das Streamen Ihrer App von Ihrem Desktopcomputer an die Holographic Remoting Player-App auf einem HoloLens-Headset bietet hauptsächlich zwei Vorteile: 
* Es beschleunigt die Entwicklung, da keine Notwendigkeit besteht, Ihre App bei jeder Änderung neu zu verpacken und hochzuladen
* Es nutzt die Leistung Ihres Desktopcomputers, sodass Sie so viele Polygone rendern können, wie es die GPU Ihres Desktops zulässt, ohne durch den am Headset verfügbaren Computer eingeschränkt zu sein

Informationen zu den ersten Schritten beim Streaming finden Sie im <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartStreaming/index.html" target="_blank">HoloLens 2-Streaming-Schnellstart</a>[]()

## <a name="see-also"></a>Siehe auch
* <a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">Unreal-Leistungsrichtlinien für mobile Geräte</a>
