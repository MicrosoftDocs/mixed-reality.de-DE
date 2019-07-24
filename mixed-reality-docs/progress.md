---
title: Anzeigen des Fortschritts
description: Ein Statussteuerelement gibt dem Benutzer eine Rückmeldung, dass ein Vorgang mit langer Laufzeit ausgeführt wird.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Design, Steuerelemente, UI, UX
ms.openlocfilehash: 84853a23a73bbece30c1f96b83e586642f3ab762
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523252"
---
# <a name="displaying-progress"></a>Anzeigen des Fortschritts

Ein Statussteuerelement gibt dem Benutzer eine Rückmeldung, dass ein Vorgang mit langer Laufzeit ausgeführt wird. Dies kann bedeuten, dass der Benutzer bei Anzeigen der Statusanzeige nicht mit der App interagieren kann. Je nach verwendetem Indikator wird auch die Länge der Wartezeit angegeben.

![Beispiel für Fortschritts Ring in hololens](images/HoloLens2_Loader.gif)<br>
*Beispiel für Fortschritts Ring in hololens*

## <a name="types-of-progress"></a>Typen von Statussteuerelementen

Es ist wichtig, dass Sie die Benutzerinformationen zu den Vorgängen bereitstellen. In Mixed Reality können Benutzer problemlos von der physischen Umgebung oder von Objekten abgelenkt werden, wenn Ihre APP kein gutes visuelles Feedback bietet. Für Situationen, die einige Sekunden dauern, z. b. beim Laden von Daten oder beim Aktualisieren einer Szene, empfiehlt es sich, einen visuellen Indikator anzuzeigen. Es gibt zwei Möglichkeiten, den Benutzer anzuzeigen, dass ein Vorgang ausgeführt wird – eine **Status** Anzeige oder ein **Fortschritts Ring**.

### <a name="progress-bar"></a>Statusanzeige

![Beispiel für Statusanzeige in hololens](images/640px-progressbar.jpg)

Eine Statusanzeige zeigt den Prozentsatz der abgeschlossenen Aufgabe an. Er sollte bei einem Vorgang verwendet werden, dessen Dauer bekannt ist (determinate), aber der Fortschritt sollte die Interaktion des Benutzers mit der APP nicht blockieren.

### <a name="progress-ring"></a>Statusring

![Beispiel für Fortschritts Ring in hololens](images/640px-progressring.jpg)

Ein Fortschritts Ring hat nur einen unbestimmten Status und sollte verwendet werden, wenn eine weitere Benutzerinteraktion blockiert wird, bis der Vorgang abgeschlossen ist.

### <a name="progress-with-a-custom-object"></a>Fortschritt mit einem benutzerdefinierten Objekt

![Fortschritt mit einem benutzerdefinierten Mesh-Beispiel in hololens](images/640px-progresscustom.jpg)

Sie können der Identität und Markenidentität Ihrer APP hinzufügen, indem Sie das Status Steuerelement mit ihren eigenen benutzerdefinierten 2D-/3D-Objekten anpassen.

## <a name="best-practices"></a>Empfohlene Methoden
* Schließen Sie das [Abrechnungs-oder tagboarding](billboarding-and-tag-along.md) eng mit der Anzeige des Fortschritts ab, da der Benutzer problemlos seinen Kopf in einen leeren Bereich verschieben und Kontext verlieren kann. Ihre APP könnte so aussehen, als ob Sie abgestürzt ist, wenn der Benutzer nichts sehen kann. Das fakboardingboarding und das Tag-Along sind in den Fortschritt vorfab integriert.
* Es ist immer gut, Statusinformationen zu den Ereignissen für den Benutzer bereitzustellen. Die Fortschritts präfab stellt verschiedene visuelle Stile bereit, einschließlich des Windows-standardmäßigen Rings-Typs zum Angeben des Status. Sie können auch ein benutzerdefiniertes Mesh mit einer Animation verwenden, wenn Sie möchten, dass der Stil Ihres Fortschritts an der Marke Ihrer APP ausgerichtet wird.

## <a name="see-also"></a>Siehe auch
* [Fortschritts Skripts und Prefabs im Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [Begrenzungs Fenster](app-bar-and-bounding-box.md)
* [Interaktionsfähiges Objekt](interactable-object.md)
* [Objektsammlung](object-collection.md)
* [Billboarding und Tag-along](billboarding-and-tag-along.md)
