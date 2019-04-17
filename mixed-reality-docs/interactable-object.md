---
title: Es-Objekt
description: Eine Schaltfläche war lange Zeit eine Metapher, die zum Auslösen eines Ereignisses in der Welt für 2D abstrakt. In der dreidimensionalen mixed Reality-Welt müssen wir auf dieser Welt mehr Abstraktionsebenen beschränkt werden.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed Reality, Steuerelemente, Interaktion, Benutzeroberfläche, ux
ms.openlocfilehash: f349d21707375690e00b0f7e465634c62be1537e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594761"
---
# <a name="interactable-object"></a>Es-Objekt

Eine Schaltfläche war lange Zeit eine Metapher, die zum Auslösen eines Ereignisses in der Welt für 2D abstrakt. In der dreidimensionalen mixed Reality-Welt müssen wir auf dieser Welt mehr Abstraktionsebenen beschränkt werden. Alles möglich ein **es Objekt** , die ein Ereignis auslöst. Ein Objekt es kann als etwas von einer Tasse Kaffee für die Tabelle, eine Gleitkommazahl in der Luft Sprechblase dargestellt werden. Wir weiterhin die Stelle, mit der herkömmlichen Schaltflächen in bestimmten Situation wie Dialogfeld Benutzeroberfläche. Die visuelle Darstellung der Schaltfläche hängt vom Kontext ab.

![Interactible Objekt Hero-Bild](images/640px-interactibleobject-hero-640px.jpg)


In der  **[Mixed Reality-Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, wir haben eine Reihe von Unity-Skripts erstellt und prefabs (Vorlagen), mit denen Sie es Objekte erstellen. Sie können diese verwenden, um jede Art von Objekt zu erstellen, die der Benutzer mit dem Sie interagieren können diese Zustände standard Interaktion mit: Beobachtung, als Ziel dienen und gedrückt. Sie können das visuelle Design problemlos in Ihre eigenen Ressourcen anpassen. Ausführliche Animationen können angepasst werden, durch das Erstellen und Zuweisen der entsprechenden Animation-Clips für die Interaktion-Zustände, in der Unity Animationscontroller oder Offset und Skalierung. 


## <a name="visual-feedback-for-the-different-input-interaction-states"></a>Visuelles Feedback für die Interaktion mit anderen Eingabe-Status

In mixed Reality da die holographic Objekte mit der realen Umgebung gemischt werden ist möglicherweise schwer zu verstehen, welche Objekte, es sind. Für es Objekte in Ihrer Umgebung ist es wichtig, um differenzierte visuelles Feedback bereitzustellen, für jede Zustand. Dadurch werden die Benutzer wissen, welcher Teil Ihrer Erfahrung ist es, und macht den Benutzer mit konsistenten Interaktion Methode sicher.

Für alle Objekte kann dieser Benutzer mit interagieren wird empfohlen, um verschiedene visuelles Feedback zu erhalten, für die anderen drei Zustände Eingabe:
* **Beobachtung**: Im Leerlauf Standardzustand des Objekts.
* **Ziel**: Wenn das Objekt mit Blicke Cursor gerichtet ist, finger Nähe oder der Bewegungsqualität Controllers Zeiger.
* **Gedrückt**: Wenn das Objekt mit der tippbewegung Geste, drücken Sie die Finger oder während der Übertragung des Controllers auswählen-Schaltfläche gedrückt wird.

![Schaltfläche "holographic"](images/640px-interactibleobject-holographicbutton-650px.jpg)<br>
*Beobachtung Zustand, Status ausgerichtet und gedrückt-Status*

In Windows Mixed Reality finden Sie die Beispiele für Eingabe Zustände im Startmenü und Schaltflächen der Anwendungsleiste visualisieren. Sie können Techniken wie z. B. Hervorhebung oder Skalierung verwenden, von visuellem Feedback auf Eingabe des Benutzers.

HoloLens-2 da dieser vollständig angezeigte manuell nachverfolgen Eingabe unterstützt können wir zusätzliche visueller Hinweise auf der Grundlage der Nähe an die Hand bereitstellen. Die [-Schaltfläche in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) wird in diesem Beispiel.

![Schaltfläche "pressable"](images/640px-interactibleobject-pressablebutton-650px.jpg)<br>




## <a name="interactable-object-samples"></a>Beispiele für die es-Objekt

### <a name="mesh-button"></a>Mesh-Schaltfläche

![Mesh-Schaltfläche](images/640px-interactibleobject-meshbutton.jpg)

Hierbei handelt es sich um Beispiele für die Verwendung von primitiven und importierten 3D-Gitterobjekten als es Objekte. Sie können ganz einfach verschiedene skalieren "," Offset "und" Color-Werte auf jeder Eingabe Interaktionszustand reagieren zuweisen.

### <a name="toolbar"></a>Symbolleiste

![Symbolleiste](images/640px-interactibleobject-toolbar.jpg)

Eine Symbolleiste ist ein häufig verwendetes Muster in mixed Reality-Benutzeroberfläche. Es ist eine einfache Auflistung von Schaltflächen mit zusätzlichen Verhaltensweisen wie z. B. [Billboarding und Tag-along](billboarding-and-tag-along.md). Dieses Beispiel verwendet ein Billboarding und Tag-along-Skript aus dem MixedRealityToolkit. Sie können steuern, ausführliche Verhaltensweisen einschließlich Entfernung, Geschwindigkeit und Schwellenwerte verschieben.

### <a name="traditional-button"></a>Herkömmliches Schaltflächen

![Herkömmliches Schaltflächen](images/640px-interactibleobject-traditionalbutton.jpg)

Dieses Beispiel zeigt eine herkömmliche 2D-Schaltfläche. Jeder Eingabe Status verfügt über eine etwas andere Tiefe und Animationseigenschaft.

### <a name="other-examples"></a>Weitere Beispiele

![Schaltfläche](images/640px-interactibleobject-pushbutton.jpg)<br>
*Schaltfläche*
<br>
![Echten Leben-Objekt](images/640px-interactibleobject-reallifeobject.jpg)<br>
*Reale-Objekt*

Mit HoloLens können Sie die physischen Speicherplatz nutzen. Angenommen Sie, eine Schaltfläche an einer Wand physischen holographic. Oder wie etwa einen Kaffee Cup für eine echte Tabelle? Importiert aus Modellieren von Software-3D-Modelle können wir ein es Objekt erstellen, die reale Objekt ähnelt. Da es sich um ein digitales Objekt ist, können wir magische Interaktionen hinzufügen.

## <a name="interactable-object-in-mixed-reality-toolkit"></a>Es Objekt in Mixed Reality-Toolkit
Sie finden die [Beispiele Interactable Objekt in Mixed Reality-Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)


## <a name="see-also"></a>Siehe auch
* [Pressable Schaltfläche in Mixed Reality-Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [Eine objektauflistung](object-collection.md)
* [Billboarding und tag-along](billboarding-and-tag-along.md)
