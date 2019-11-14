---
title: System Geste
description: System Geste, um das Startmenü aufzurufen.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Gemischte Realität, Gesten, Interaktion, Entwurf
ms.openlocfilehash: 417811fff9d98e459dc0047d46ea065acfced4ef
ms.sourcegitcommit: f2b7c6381006fab6d0472fcaa680ff7fb79954d6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2019
ms.locfileid: "74064241"
---
# <a name="system-gesture"></a>System Geste

Die System Geste ist eine Handbewegung, mit der das Startmenü aufgerufen wird. Dies entspricht dem Drücken der Windows-Taste auf der Tastatur, der Xbox-Schaltfläche auf einem Xbox-Controller oder der Windows-Taste auf dem immersiven Headset-Bewegungs Controller. Es ist wichtig zu verstehen, welche Gesten für das System auf jedem gemischten Reality-Gerät reserviert sind, um Konflikte beim Entwerfen Ihrer Interaktionen zu vermeiden.

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Blütezeit</td>
        <td>✔️</td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Handgelenk Taste</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Eye-und Palmen Pfeil nach oben</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>Blütezeit
Um das Startmenü in hololens (1. Generation) aufzurufen, haben wir "Bloom" entworfen, das eine symbolische Geste zum imitieren der Blüten Blüte ist. Es ist für die Interaktion mit untergeordneten Elementen, die einfache Durchführung und die schnelle Erinnerung. Um die Blüte Bewegung auf hololens (1. Generation) durchzuführen, halten Sie Ihre Hand an Ihre Hand, um Sie zu öffnen, und öffnen Sie dann die Hand, indem Sie Ihre Finger verteilen.

:::row:::
    :::column:::
        ![](images/bloom-close.png) schließen.<br>
        **Schritt 1: überschreiten der Hand.**<br>
    :::column-end:::
    :::column:::
        ![Blüte geöffnet](images/bloom-open.png)<br>
        **Schritt 2: überschreiten der handbreiten Verteilung**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="wrist-button"></a>Handgelenk Taste
In hololens 2 haben wir die Blüte Bewegung durch eine virtuelle Handgelenk Schaltfläche ersetzt, die mehr instanzielle Interaktionen ermöglicht, die keine zusätzliche Lehre erfordern. Wenn die Benutzer die Schaltfläche auf dem Handgelenk anzeigt, können Sie sie intuitiv erreichen und mit der anderen Seite drücken.

:::row:::
    :::column:::
        ![Hand Tasten](images/wrist-button-ready.png)<br>
        **Schritt 1: Palme zum Anzeigen der Schaltfläche "Handgelenk"**<br>
    :::column-end:::
    :::column:::
        Drücken Sie ![Hand Tasten](images/wrist-button-press.png)<br>
        **Schritt 2: Klicken Sie auf das Handgelenk.**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="eye-gaze-and-palm-up-pinch"></a>"Augenblick" und "Palme"-Pinsel
Wir haben auch eine eindimensionale Lösung für den einfachen Zugriff in hololens 2 entwickelt. Diese Geste erfordert, dass Benutzer auf die Handgelenk Schaltfläche zeigen. verwenden Sie dann dieselbe Hand, um mit dem Ziehpunkt und dem Index Finger eine Aufzieh Schaltfläche auszuführen.<br>
:::row:::
    :::column:::
        ![Hand Tasten](images/wrist-button-ready.png)<br>
        **Schritt 1: Palme zum Anzeigen der Schaltfläche "Handgelenk"**<br>
    :::column-end:::
    :::column:::
        ![-Schaltflächen-Pinsel](images/wrist-button-pinch.png)<br>
        **Schritt 2: Augenblick auf die Schaltfläche und dann auf die Schaltfläche**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>Weitere Informationen:

* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Anvisieren mit den Augen](eye-tracking.md)
* [Spracheingabe](voice-input.md)
