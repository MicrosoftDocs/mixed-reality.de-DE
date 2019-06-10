---
title: Anzeigen des Status
description: Ein Statussteuerelement gibt dem Benutzer eine Rückmeldung, dass ein Vorgang mit langer Laufzeit ausgeführt wird.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Entwurf, Steuerelemente, Benutzeroberfläche, ux
ms.openlocfilehash: d62d86c690233f351b6c156c66eba33cb2687ea6
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813726"
---
# <a name="displaying-progress"></a>Anzeigen des Status

Ein Statussteuerelement gibt dem Benutzer eine Rückmeldung, dass ein Vorgang mit langer Laufzeit ausgeführt wird. Dies kann bedeuten, dass der Benutzer bei Anzeigen der Statusanzeige nicht mit der App interagieren kann. Je nach verwendetem Indikator wird auch die Länge der Wartezeit angegeben.

![Status-Ring-Beispiel in HoloLens](images/HoloLens2_Loader.gif)<br>
*Status-Ring-Beispiel in HoloLens*

## <a name="types-of-progress"></a>Typen von Statussteuerelementen

Es ist wichtig, zu dem Benutzerinformationen zu was passiert. In mixed Reality können Benutzer problemlos von der physischen Umgebung oder Objekte abgelenkt werden, wenn Ihre app nicht die gute visuelles Feedback erhalten. Für Situationen, in denen einige Sekunden dauern, z. B. beim Laden von Daten oder einer Szene wird aktualisiert, es empfiehlt sich, einen visuellen Indikator anzeigen. Es gibt zwei Möglichkeiten, die dem Benutzer angezeigt, dass ein Vorgang ausgeführt – wird eine **Statusanzeige** oder **statuskreis**.

### <a name="progress-bar"></a>Statusleiste

![Beispiel für Fortschritt in HoloLens](images/640px-progressbar.jpg)

Eine Statusanzeige zeigt den Prozentsatz einer Aufgabe abgeschlossen. Er sollte verwendet werden, während eines Vorgangs, deren Dauer (bestimmte) bekannt ist, jedoch seinen Status sollte die Interaktion des Benutzers mit der app nicht blockieren.

### <a name="progress-ring"></a>Statusring

![Status-Ring-Beispiel in HoloLens](images/640px-progressring.jpg)

Ein statuskreis nur einem unbestimmten Zustand befindet, und sollte verwendet werden, wenn weiteren Benutzereingriff blockiert wird, bis der Vorgang abgeschlossen ist.

### <a name="progress-with-a-custom-object"></a>Mit der ein benutzerdefiniertes Objekt

![Mit benutzerdefinierten Mesh-Beispiel in HoloLens](images/640px-progresscustom.jpg)

Sie können zu Ihrer Persönlichkeit und Markenidentität Ihrer app hinzufügen, durch das Anpassen des Statussteuerelements mit Ihren eigenen benutzerdefinierten 2D-/3D-Objekten.

## <a name="best-practices"></a>Empfohlene Methoden
* Eng [billboarding oder Tag-along](billboarding-and-tag-along.md) der Anzeige des Status, da der Benutzer kann einfach ihrem Kopf in den leeren Bereich verschieben und Kontext verlieren. Ihre app möglicherweise sieht es abgestürzt ist, wenn der Benutzer können nicht alles angezeigt werden. Billboarding und Tag-along ist in den Status-Prefab integriert.
* Es empfiehlt sich immer um Statusinformationen über den Ablauf für den Benutzer bereitzustellen. Die Status-Prefab bietet verschiedene visuelle Stile, einschließlich des Status des Windows-Ring-Standardtyp für die Bereitstellung von Status an. Wenn Sie den Stil der den Fortschritt zu Ihrer app Marke ausrichten möchten, können Sie auch eine benutzerdefinierte Mesh mit einer Animation verwenden.

## <a name="see-also"></a>Siehe auch
* [Status-Skripts und Prefabs in Mixed Reality-Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [Umgebendes Feld](app-bar-and-bounding-box.md)
* [Interaktionsfähiges Objekt](interactable-object.md)
* [Objektsammlung](object-collection.md)
* [Billboarding und Tag-along](billboarding-and-tag-along.md)
