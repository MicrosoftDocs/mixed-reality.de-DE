---
title: Blickeingabe
description: Blicke ist die erste Form der Eingabe und eine primäre Form für die Zielgruppenadressierung in mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed Reality, Blicke, Interaktion, Entwerfen
ms.openlocfilehash: 9a12a5a3b3a583477fd98caeaa2f6890c67e2655
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604974"
---
# <a name="gaze"></a>Blickeingabe

**Bestaunen** ist die erste Form der Eingabe und eine primäre Form für die Zielgruppenadressierung in mixed Reality. Blicke Aufschluss darüber, wo der Benutzer ist in der Welt betrachtet und können Sie ihre Absichten zu ermitteln. In der realen Welt in der Regel betrachten ein Objekt Sie das von Ihnen zu interagieren. Dies ist identisch mit Blicke.

Mixed Reality-Headsets werden Position und Ausrichtung von Ihres Benutzers Head verwenden, um ihre Head Blicke Vektor zu bestimmen. Sie können dieses Vektors als einen Laserpointer jetzt direkt aus direkt zwischen dem Benutzer die Augen vorstellen. Wie der Benutzer im Raum dargestellt wird, kann Ihre Anwendung diese Chow, sowohl mit eigenen Hologramme und überschneiden der [räumliche Zuordnung](spatial-mapping.md) Mesh bestimmen, welche virtuell oder Real-World Ihre Benutzer möglicherweise ansehen.

Für HoloLens-2 Interaktionen können angewendet werden, indem entweder vom Benutzer Head Blicke über in der Nähe oder Interaktionen zu weit übergeben.  Für HoloLens (der 1. Generation), Interaktionen sollte im Allgemeinen abgeleitet werden, die für die Zielgruppenadressierung von Head Blicke des Benutzers, statt beim Rendern oder an die Hand, die Position direkt interagieren. Nach dem Start einer Interaktion können relative Bewegungen des Zeigers verwendet werden, um zu steuern die [Geste](gestures.md), wie bei der [Manipulation oder die Bildschirmnavigation](gestures.md#composite-gestures) Bewegung. Mit immersive Headsets, können Sie als Ziel verwenden entweder Blicke oder zeigt-fähige [motion Controller](motion-controllers.md).

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Feature</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1. Generation)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> Head Blicke</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr><tr>
<td> Eye Blicke</td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>

> [!NOTE]
> Weitere Anleitungen, die speziell für HoloLens 2 [bald](index.md#news-and-notes).


## <a name="uses-of-gaze"></a>Verwendung des Blicke

Als Entwickler mixed Reality möglich deutlich mit Blicke:
* Ihre app kann mit der Hologramme in Ihrer Szene Blicke, um zu bestimmen, wo Aufmerksamkeit des Benutzers überlappen.
* Gesten und Controller-drückt, die anhand des Benutzers Blicke, den Benutzer auszuwählen, zu aktivieren, erfassen, führen Sie einen Bildlauf oder andernfalls ihre Hologramme interagieren, kann Ihre app abzielen.
* Ihre app kann Benutzer Hologramme auf Flächen der realen Welt, zu platzieren, indem Sie ihre Blicke Chow mit dem Netz räumliche Zuordnung überschneidenden lassen.
* Ihre app kann der Benutzer wissen *nicht* Suchen in Richtung des ein wichtiger-Objekt, das Ihrer app gerne SEH- und Hinweise für das Objekt zu aktivieren, führen kann.

## <a name="cursor"></a>Cursor

In den meisten apps sollten verwendet eine [Cursor](cursors.md) (oder andere akustische/Visual-Angabe) das Vertrauen in was zu gewähren, den sie für die Interaktion mit sind. Sie werden in der Regel dieser Cursor in der ganzen Welt, in denen die Blicke Chow zuerst ein Objekt, interagiert der ggf. ein Hologramm oder eine reale-Oberfläche möglicherweise, positionieren.

![Ein Beispiel für die visual Cursor Blicke angezeigt](images/cursor.jpg)<br>
*Ein Beispiel für die visual Cursor Blicke angezeigt*

## <a name="giving-action-to-the-users-gaze"></a>Aktion sodass des Benutzers Blicke

Sobald der Benutzer ein Hologramm oder reales Objekt über die Blicke angewendet wurde, ist ihre nächste Schritt für die Reaktion auf dieses Objekt. Die primäre Methode für einen Benutzer zu ergreifen, werden über [Gesten](gestures.md), [motion Controller](motion-controllers.md) und [Voice](voice-input.md).

## <a name="see-also"></a>Siehe auch
* [MR Eingabe 210: Blicke](holograms-210.md)
* [Blicke, Gesten und während der Übertragung von Controllern in DirectX](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [In Unity bestaunen](gaze-in-unity.md)
