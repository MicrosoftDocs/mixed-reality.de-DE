---
title: Anzeigen des Fortschritts
description: Ein Statussteuerelement gibt dem Benutzer eine Rückmeldung, dass ein Vorgang mit langer Laufzeit ausgeführt wird.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Design, Steuerelemente, UI, UX
ms.openlocfilehash: 43b4802e7c821c98c847509ace950f381da12f95
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437539"
---
# <a name="displaying-progress"></a>Anzeigen des Fortschritts

<br>

<img src="images/HoloLens2_Loader.gif" alt="Progress ring example in HoloLens" width="940px">

Ein Statussteuerelement gibt dem Benutzer eine Rückmeldung, dass ein Vorgang mit langer Laufzeit ausgeführt wird. Dies kann bedeuten, dass der Benutzer bei Anzeigen der Statusanzeige nicht mit der App interagieren kann. Je nach verwendetem Indikator wird auch die Länge der Wartezeit angegeben.

<br>

---

## <a name="types-of-progress"></a>Typen von Statussteuerelementen

Es ist wichtig, dass Sie die Benutzerinformationen zu den Vorgängen bereitstellen. In Mixed Reality können Benutzer problemlos von der physischen Umgebung oder von Objekten abgelenkt werden, wenn Ihre APP kein gutes visuelles Feedback bietet. Für Situationen, die einige Sekunden dauern, z. b. beim Laden von Daten oder beim Aktualisieren einer Szene, empfiehlt es sich, einen visuellen Indikator anzuzeigen. Es gibt zwei Möglichkeiten, den Benutzer anzuzeigen, dass ein Vorgang ausgeführt wird – eine **Status** Anzeige oder ein **Fortschritts Ring**.

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a>Statusleiste<br>
        Eine Statusanzeige zeigt den Prozentsatz der abgeschlossenen Aufgabe an. Er sollte bei einem Vorgang verwendet werden, dessen Dauer bekannt ist (determinate), aber der Fortschritt sollte die Interaktion des Benutzers mit der APP nicht blockieren.<br>
        <br>
        *Bild: Statusanzeige Beispiel in hololens*
    :::column-end:::
        :::column:::
        ![Speicher](images/spacer-20x582.png)<br>
       ![Statusanzeige Beispiel in hololens](images/640px-progressbar.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a>Statusring<br>
        Ein Fortschritts Ring hat nur einen unbestimmten Status und sollte verwendet werden, wenn eine weitere Benutzerinteraktion blockiert wird, bis der Vorgang abgeschlossen ist.<br>
        <br>
        *Image: Fortschritts Ring-Beispiel in hololens*
    :::column-end:::
        :::column:::
        ![Speicher](images/spacer-20x582.png)<br>
       ![Status Ring-Beispiel in hololens](images/640px-progressring.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a>Fortschritt mit einem benutzerdefinierten Objekt<br>
        Sie können der Identität und Markenidentität Ihrer APP hinzufügen, indem Sie das Status Steuerelement mit ihren eigenen benutzerdefinierten 2D-/3D-Objekten anpassen.<br>
        <br>
        *Bild: Fortschritt mit einem benutzerdefinierten Mesh-Beispiel in hololens*
    :::column-end:::
        :::column:::
        ![Speicher](images/spacer-20x582.png)<br>
       ![Fortschritt mit einem benutzerdefinierten Mesh-Beispiel in hololens](images/640px-progresscustom.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a>Bewährte Verfahren
* Schließen Sie das [Abrechnungs-oder tagboarding](billboarding-and-tag-along.md) eng mit der Anzeige des Fortschritts ab, da der Benutzer problemlos seinen Kopf in einen leeren Bereich verschieben und Kontext verlieren kann. Ihre APP könnte so aussehen, als ob Sie abgestürzt ist, wenn der Benutzer nichts sehen kann. Das fakboardingboarding und das Tag-Along sind in den Fortschritt vorfab integriert.
* Es ist immer gut, Statusinformationen zu den Ereignissen für den Benutzer bereitzustellen. Die Fortschritts präfab stellt verschiedene visuelle Stile bereit, einschließlich des Windows-standardmäßigen Rings-Typs zum Angeben des Status. Sie können auch ein benutzerdefiniertes Mesh mit einer Animation verwenden, wenn Sie möchten, dass der Stil Ihres Fortschritts an der Marke Ihrer APP ausgerichtet wird.

<br>

---

## <a name="see-also"></a>Weitere Informationen:
* [Fortschritts Skripts und Prefabs im Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [Begrenzungs Fenster](app-bar-and-bounding-box.md)
* [Interaktionsfähiges Objekt](interactable-object.md)
* [Objektsammlung](object-collection.md)
* [Billboarding und Tag-along](billboarding-and-tag-along.md)
