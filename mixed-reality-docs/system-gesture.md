---
title: Start Geste
description: Starten Sie die Geste, um das Startmenü aufzurufen.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Gemischte Realität, Gesten, Interaktion, Entwurf
ms.openlocfilehash: 84088156d0c9cdacc421985b922d5e9370f6a87e
ms.sourcegitcommit: fd606e87e3c4785d3ca2a26632be3bb580e39afb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84152512"
---
# <a name="start-gesture"></a>Start Geste

Die Start Geste ist eine Handbewegung, mit der das Startmenü aufgerufen wird. Dies entspricht dem Drücken der Windows-Taste auf der Tastatur, der Xbox-Schaltfläche auf einem Xbox-Controller oder der Windows-Taste auf dem immersiven Headset-Bewegungs Controller. Es ist wichtig zu verstehen, welche Gesten für das System auf jedem gemischten Reality-Gerät reserviert sind, um Konflikte beim Entwerfen Ihrer Interaktionen zu vermeiden.

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
        <td>Blüte</td>
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

## <a name="bloom"></a>Blüte
Um das Startmenü in hololens (1. Generation) aufzurufen, haben wir "Bloom" entworfen, das eine symbolische Geste zum imitieren der Blüten Blüte ist. Es ist für die Interaktion mit untergeordneten Elementen, die einfache Durchführung und die schnelle Erinnerung. Um die Blüte Bewegung auf hololens (1. Generation) durchzuführen, halten Sie Ihre Hand an Ihre Hand, um Sie zu öffnen, und öffnen Sie dann die Hand, indem Sie Ihre Finger verteilen.

:::row:::
    :::column:::
        ![Schließen der Blüte](images/bloom-close.png)<br>
        **Schritt 1: überschreiten der Hand.**<br>
    :::column-end:::
    :::column:::
        ![Geöffnet, geöffnet](images/bloom-open.png)<br>
        **Schritt 2: überschreiten der handbreiten Verteilung**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a>Start Geste
In hololens 2 haben wir die Blüte Bewegung durch eine virtuelle Handgelenk Schaltfläche ersetzt, die mehr instanzielle Interaktionen ermöglicht, die keine zusätzliche Lehre erfordern. Wenn die Benutzer die Schaltfläche auf dem Handgelenk anzeigt, können Sie sie intuitiv erreichen und mit der anderen Seite drücken.

:::row:::
    :::column:::
        ![Handgelenk Taste](images/wrist-button-ready.png)<br>
        **Schritt 1: Palme zum Anzeigen der Schaltfläche "Handgelenk"**<br>
    :::column-end:::
    :::column:::
        ![Handgelenk Taste drücken](images/wrist-button-press.png)<br>
        **Schritt 2: Klicken Sie auf das Handgelenk.**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="one-handed-start-gesture"></a>Einstufige Start Geste

> [!IMPORTANT]
> Damit die einstufige Start Geste funktioniert:
>
> 1. Sie müssen ein Update auf das Update von November 2019 (Build 18363,1039) oder höher durch haben.
> 1. Die Augen müssen auf dem Gerät so kalibriert werden, dass die Eye-Nachverfolgung ordnungsgemäß funktioniert. Wenn Sie keine Umkreis Punkte um das Start Symbol sehen, wenn Sie es betrachten, werden die Augen nicht auf dem Gerät gekalibriert.

Sie können die Start Geste auch nur mit einer Hand ausführen. Halten Sie zu diesem Zweck ihre Hand mit Ihrer Hand, und sehen Sie sich das **Start Symbol** auf Ihrem inneren Handgelenk an. **Wenn Sie das Symbol gedrückt halten**, können Sie den Ziehpunkt und den Finger des Indexes zusammenhalten.<br>
:::row:::
    :::column:::
        ![Handgelenk Taste](images/wrist-button-ready.png)<br>
        **Schritt 1: Palme zum Anzeigen der Schaltfläche "Handgelenk"**<br>
    :::column-end:::
    :::column:::
        ![Handgelenk Schaltfläche](images/wrist-button-pinch.png)<br>
        **Schritt 2: Augenblick auf die Schaltfläche und dann auf die Schaltfläche**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>Siehe auch

* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Anvisieren mit den Augen](eye-tracking.md)
* [Spracheingabe](voice-input.md)
