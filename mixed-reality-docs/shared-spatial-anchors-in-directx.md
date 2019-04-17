---
title: Räumliche Anker in DirectX freigegeben
description: Es wird erläutert, wie zwei HoloLens-Geräte zu synchronisieren, indem Sie die Freigabe von räumlichen Anker.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, zu synchronisieren, räumliche Anker, Übertragung, Multiplayer-Spiele, anzeigen, Szenario, exemplarische Vorgehensweise, Beispielcode, Azure, Azure räumliche Anker, ASA
ms.openlocfilehash: 190d3dfb3eec3fd1a57d2713850a7778a4a71de9
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605064"
---
# <a name="shared-experiences-in-directx"></a>Freigegebene Funktionen in DirectX

Eine gemeinsame Erfahrung ist eine, in denen mehrere Benutzer, die jeweils über eigene HoloLens, iOS oder Android-Gerät zusammen anzeigen und interagieren mit der gleichen – Hologramm die auf einem festen Punkt im Bereich positioniert ist. Dies erfolgt durch räumliche Anker freigeben.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

Können Sie <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure räumliche Anker</a> permanenten Cloud gesicherten räumliche Anker, zu erstellen, die Ihre app über mehrere HoloLens, iOS und Android-Geräte suchen kann.  Anhand der einen allgemeine räumlichen Anker auf mehreren Geräten, kann jeder Benutzer Inhalt gerendert wird, relativ zu diesem-Anker wird in demselben physischen Standort finden Sie unter.  Dadurch können freigegebene ein Nutzererlebnis in Echtzeit.

Können Sie auch <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure räumliche Anker</a> für asynchrone – Hologramm Persistenz für HoloLens, IOS- und Android-Geräte.  Freigeben einer permanenten räumliche cloudankers, können mehrere Geräte das gleiche persistente – Hologramm im Laufe der Zeit beobachten, auch wenn diese Geräte nicht zur gleichen Zeit zusammen vorhanden sind.

Zunächst erstellen freigegebene Umgebungen in Ihrer app HoloLens, testen Sie die 5 Minuten <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure räumliche Anker HoloLens Schnellstart</a>.

Sobald Sie mit Azure räumliche Anker die betriebsbereit sind, können Sie dann <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">erstellen, und suchen Sie die Anker auf HoloLens</a>.  Exemplarische Vorgehensweisen sind verfügbar für <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android und iOS</a> , aktivieren Sie die gleichen Anker auf allen Geräten gemeinsam nutzen.

## <a name="local-anchor-transfers"></a>Lokale Anchor-Übertragungen

In Situationen, in dem können keine Azure räumliche Anker, [lokalen Anker Übertragungen](local-anchor-transfers-in-directx.md) aktivieren eine HoloLens-Gerät so exportieren Sie einen Anker, die durch ein zweites Gerät mit HoloLens importiert werden.  Beachten Sie, dass dieser Ansatz bietet weniger stabil Anchor-Rückruf als Azure räumliche Anker IOS- und Android-Geräte werden von diesem Ansatz nicht unterstützt.

## <a name="see-also"></a>Siehe auch
* [Freigegebene Funktionen in mixed reality](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure räumliche Anker</a>
* <a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Azure räumliche Anker-SDK für HoloLens</a>