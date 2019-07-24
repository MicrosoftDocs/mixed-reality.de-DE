---
title: Freigegebene Erfahrungen in Unity
description: Verwenden Sie die gleichen holograms zwischen mehreren Benutzern in einer Unity-Anwendung.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Freigabe, Anker, worldanchor, Mr Sharing 250, worldanchortransferbatch, spatialperception, Azure, räumliche Azure-Anker, ASA
ms.openlocfilehash: fe755c15d942660b1e16b2335db28d3d7ce72816
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516793"
---
# <a name="shared-experiences-in-unity"></a>Freigegebene Erfahrungen in Unity

Eine gemeinsame Nutzung ist eine, in der mehrere Benutzer mit jeweils eigenen hololens-, IOS-oder Android-Geräten das gleiche – Hologramm anzeigen und mit diesem interagieren, das an einem festgelegten Punkt positioniert ist. Dies wird durch die räumliche Anker Freigabe erreicht.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

Sie können <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial</a> Anchor verwenden, um permanente, von der Cloud gesicherte räumliche Anker zu erstellen, die Ihre APP dann über mehrere hololens-, IOS-und Android-Geräte hinweg finden kann.  Durch die gemeinsame Nutzung eines gemeinsamen räumlichen Ankers auf mehreren Geräten kann jeder Benutzer den Inhalt in Relation zu diesem Anker am gleichen physischen Speicherort sehen.  Dies ermöglicht gemeinsame Erfahrungen in Echtzeit.

Sie können <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> auch für die asynchrone Hologrammpersistenz auf HoloLens-, iOS- und Android-Geräten verwenden.  Durch die gemeinsame Nutzung eines dauerhaften Cloudraumankers können mehrere Geräte dasselbe persistierte Hologramm im Verlauf der Zeit beobachten, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.

Um mit der Einführung von freigegebenen Erfahrungen in Unity zu beginnen, testen Sie die fünfminütigen <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchor Unity-Schnellstarts</a>.

Sobald Sie mit räumlichen Azure-Ankern arbeiten, können Sie <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Anker in Unity erstellen und lokalisieren</a>.

## <a name="local-anchor-transfers"></a>Lokale Anker Übertragungen

In Fällen, in denen Sie keine räumlichen Anker von Azure verwenden können, ermöglichen [lokale Anker Übertragungen](local-anchor-transfers-in-unity.md) einem hololens-Gerät das Exportieren eines Ankers, der von einem zweiten hololens-Gerät importiert werden soll.  Beachten Sie, dass dieser Ansatz weniger robusten Anker als räumliche Azure-Anker bietet und IOS-und Android-Geräte von diesem Ansatz nicht unterstützt werden.

## <a name="see-also"></a>Siehe auch
* [Gemeinsame Erlebnisse in Mixed Reality](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchor SDK für Unity</a>