---
title: Blickeingabe
description: Der Blick ist die erste Form der Eingabe und ist eine primäre Form der Ausrichtung in gemischter Realität.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Gemischte Realität, Blick, Interaktion, Entwurf
ms.openlocfilehash: 7e65d26d3e9edabbd01d35a887ffc8622a3c6337
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414372"
---
# <a name="gaze"></a>Blickeingabe

Der **Blick** ist die erste Form der Eingabe und ist eine primäre Form der Ausrichtung in gemischter Realität. Der Blick zeigt Ihnen, wo der Benutzer in der Welt sucht, und ermöglicht Ihnen, seine Absicht zu ermitteln. In der Praxis sehen Sie in der Regel ein Objekt, mit dem Sie interagieren möchten. Dies ist mit Blick identisch.

Mixed Reality-Headsets verwenden die Position und Ausrichtung des Hauptteils Ihres Benutzers, um den Vektor für den Head-Blick zu ermitteln. Sie können sich diesen Vektor als Laser Zeiger direkt zwischen den Augen des Benutzers vorstellen. Wenn sich der Benutzer um den Raum kümmert, kann die Anwendung diesen Strahl sowohl mit eigenen holograms als auch mit dem [räumlichen](spatial-mapping.md) zuordnungsmesh überschneiden, um zu bestimmen, welches virtuelle oder reale Objekt Ihr Benutzer möglicherweise ansieht.

Bei hololens 2 können Interaktionen entweder durch den Haupt-oder den Augenblick des Benutzers oder durch near-oder weite Interaktionen erreicht werden.
Bei hololens (1. Generation) sollten Interaktionen im Allgemeinen die Zielvorgabe von der Kopfzeile des Benutzers ableiten, anstatt zu versuchen, direkt an der Position der Hand zu arbeiten. Nachdem eine Interaktion begonnen hat, können relative Bewegungen der Hand verwendet werden, um die [Bewegung](gestures.md)zu steuern, wie bei der [Manipulation oder Navigation](gestures.md#composite-gestures) . Mit immersiven Headsets können Sie mithilfe von Head-und zeige fähigen [Bewegungs Controllern](motion-controllers.md)auf abzielen.

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
        <td>Kopfzeile</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Augenblick</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> Weitere Anleitungen sind für hololens 2 in [Kürze](index.md#news-and-notes)verfügbar.


## <a name="uses-of-gaze"></a>Verwendung von Blick

Als Entwickler mit gemischter Realität können Sie mit dem Kopf-oder Augenblick viel anfangen:
* Ihre APP kann den Blick mit den holograms in Ihrer Szene überschneiden, um zu bestimmen, wo die Aufmerksamkeit des Benutzers ist.
* Ihre APP kann auf Gesten und Controller drückt werden, die auf der Sicht des Benutzers basieren, sodass der Benutzer seine Hologramme auswählen, aktivieren, einlesen, Scrollen oder anderweitig interagieren kann.
* Ihre APP ermöglicht dem Benutzer das Platzieren von holograms auf realen Oberflächen, indem er seinen Blick Strahl mit dem räumlichen Mapping-Gitter schneidet.
* Ihre APP kann wissen, wenn der Benutzer *nicht* in der Richtung eines wichtigen Objekts sucht, was dazu führen kann, dass Ihre APP visuelle und Audiohinweise zum Umwandeln des Objekts erhält.

## <a name="cursor"></a>Cursor

Für den Kopf Blick sollten die meisten apps einen [Cursor](cursors.md) (oder einen anderen Auditory/visuellen Hinweis) verwenden, um dem Benutzer die Gewissheit zu verschaffen, mit welchem Element er interagiert. In der Regel positionieren Sie diesen Cursor in der Welt, in der der Head-Blick Strahl zuerst ein Objekt schneidet, das ein Hologramm oder eine reale Oberfläche sein kann.

![Ein Beispiel für einen visuellen Cursor zum Anzeigen des Blicks](images/cursor.jpg)<br>
*Ein Beispiel für einen visuellen Cursor zum Anzeigen des Blicks*

Für den Augenblick empfiehlt es sich im allgemeinen *nicht* , einen Cursor anzuzeigen, da dies für den Benutzer schnell ablenkend und lästig werden kann. Markieren Sie stattdessen visuelle Ziele, oder verwenden Sie einen sehr schwachen Augen Cursor, um sicherzustellen, womit der Benutzer interagieren soll. Weitere Informationen finden Sie in unserem [Entwurfs Leit Faden für die Augen basierte Eingabe](eye-tracking.md) auf hololens 2.

## <a name="giving-action-to-the-users-gaze"></a>Bereitstellung von Aktionen für den Benutzer

Sobald der Benutzer ein – Hologramm-Objekt oder ein reales Objekt verwendet hat, ist der nächste Schritt das Ausführen von Aktionen für dieses Objekt. Die Hauptmethoden, mit denen ein Benutzer Maßnahmen ergreifen kann, sind [Gesten](gestures.md), [Bewegungs Controller](motion-controllers.md) und [Sprachanrufe](voice-input.md).

## <a name="see-also"></a>Siehe auch
* [MR-Eingabe 210: Kopfzeile](holograms-210.md)
* [Anvisieren mit dem Kopf und mit den Augen in DirectX](gaze-in-directx.md)
* [Kopf Blicke in Unity](gaze-in-unity.md)
* [Blick auf hololens 2](eye-tracking.md)
* [Eye Eye in Unity mithilfe von Mixed Reality Toolkit](https://aka.ms/mrtk-eyes)
