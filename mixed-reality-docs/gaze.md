---
title: Blickeingabe
description: Blicke ist die erste Form der Eingabe und eine primäre Form für die Zielgruppenadressierung in mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed Reality, Blicke, Interaktion, Entwerfen
ms.openlocfilehash: 7e65d26d3e9edabbd01d35a887ffc8622a3c6337
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414372"
---
# <a name="gaze"></a>Blickeingabe

**Bestaunen** ist die erste Form der Eingabe und eine primäre Form für die Zielgruppenadressierung in mixed Reality. Blicke Aufschluss darüber, wo der Benutzer ist in der Welt betrachtet und können Sie ihre Absichten zu ermitteln. In der realen Welt in der Regel betrachten ein Objekt Sie das von Ihnen zu interagieren. Dies ist identisch mit Blicke.

Mixed Reality-Headsets werden Position und Ausrichtung von Ihres Benutzers Head verwenden, um ihre Head Blicke Vektor zu bestimmen. Sie können dieses Vektors als einen Laserpointer jetzt direkt aus direkt zwischen dem Benutzer die Augen vorstellen. Wie der Benutzer im Raum dargestellt wird, kann Ihre Anwendung diese Chow, sowohl mit eigenen Hologramme und überschneiden der [räumliche Zuordnung](spatial-mapping.md) Mesh bestimmen, welche virtuell oder Real-World Ihre Benutzer möglicherweise ansehen.

Für HoloLens-2 Interaktionen können angewendet werden, indem entweder vom Benutzer Head Blicke, Eye Blicke über in der Nähe oder Interaktionen zu weit übergeben.
Für HoloLens (der 1. Generation), Interaktionen sollte im Allgemeinen abgeleitet werden, die für die Zielgruppenadressierung von Head Blicke des Benutzers, statt beim Rendern oder an die Hand, die Position direkt interagieren. Nach dem Start einer Interaktion können relative Bewegungen des Zeigers verwendet werden, um zu steuern die [Geste](gestures.md), wie bei der [Manipulation oder die Bildschirmnavigation](gestures.md#composite-gestures) Bewegung. Mit immersive Headsets, können Sie als Ziel verwenden entweder Head Blicke oder zeigt-fähige [motion Controller](motion-controllers.md).

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a>Unterstützung von Geräten

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Funktion</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Head Blicke</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Eye Blicke</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> Weitere Anleitungen, die speziell für HoloLens 2 [bald](index.md#news-and-notes).


## <a name="uses-of-gaze"></a>Verwendung des Blicke

Als Entwickler mixed Reality möglich deutlich mit Haupt- oder Eye Blicke:
* Ihre app kann mit der Hologramme in Ihrer Szene Blicke, um zu bestimmen, wo Aufmerksamkeit des Benutzers überlappen.
* Gesten und Controller-drückt, die anhand des Benutzers Blicke, den Benutzer auszuwählen, zu aktivieren, erfassen, führen Sie einen Bildlauf oder andernfalls ihre Hologramme interagieren, kann Ihre app abzielen.
* Ihre app kann Benutzer Hologramme auf Flächen der realen Welt, zu platzieren, indem Sie ihre Blicke Chow mit dem Netz räumliche Zuordnung überschneidenden lassen.
* Ihre app kann der Benutzer wissen *nicht* Suchen in Richtung des ein wichtiger-Objekt, das Ihrer app gerne SEH- und Hinweise für das Objekt zu aktivieren, führen kann.

## <a name="cursor"></a>Cursor

Für Head Blicke, sollten die meisten apps verwenden eine [Cursor](cursors.md) (oder andere akustische/Visual-Angabe) das Vertrauen in was zu gewähren, den sie für die Interaktion mit sind. Sie werden in der Regel dieser Cursor in der ganzen Welt, in dem ihre Head Blicke Strahl zuerst ein Objekt, schneidet die ggf. ein Hologramm oder eine reale-Oberfläche möglicherweise, positionieren.

![Ein Beispiel für die visual Cursor Blicke angezeigt](images/cursor.jpg)<br>
*Ein Beispiel für die visual Cursor Blicke angezeigt*

Für die Augen Blicke, empfehlen wir im allgemeinen *nicht* einen Cursor, der angezeigt wird, wie dies schnell zu allgemeiner Ablenkung und es ziemlich ärgerlich, für den Benutzer werden kann. Stattdessen leicht markieren Sie visual Ziele oder verwenden Sie einen sehr schwach Eye-Cursor zu vertrauen zu den neuerungen des Benutzers zu interagieren. Weitere Informationen finden Sie unserem [Entwurfsleitfaden für die Eingabe Eye-basierte](eye-tracking.md) für HoloLens 2.

## <a name="giving-action-to-the-users-gaze"></a>Aktion sodass des Benutzers Blicke

Sobald der Benutzer ein Hologramm oder reales Objekt über die Blicke angewendet wurde, ist ihre nächste Schritt für die Reaktion auf dieses Objekt. Die primäre Methode für einen Benutzer zu ergreifen, werden über [Gesten](gestures.md), [motion Controller](motion-controllers.md) und [Voice](voice-input.md).

## <a name="see-also"></a>Siehe auch
* [MR-Eingabe 210: Head Blicke](holograms-210.md)
* [Anvisieren mit dem Kopf und mit den Augen in DirectX](gaze-in-directx.md)
* [Head Blicke in Unity](gaze-in-unity.md)
* [Eye-Blicke für HoloLens 2](eye-tracking.md)
* [Eye Blicke in Unity mithilfe von Mixed Reality-Toolkit](https://aka.ms/mrtk-eyes)
