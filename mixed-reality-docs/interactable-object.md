---
title: Es-Objekt
description: Eine Schaltfläche war lange Zeit eine Metapher, die zum Auslösen eines Ereignisses in der Welt für 2D abstrakt. In der dreidimensionalen mixed Reality-Welt müssen wir auf dieser Welt mehr Abstraktionsebenen beschränkt werden.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed Reality, Steuerelemente, Interaktion, Benutzeroberfläche, ux
ms.openlocfilehash: eea7eff6c591a9319b920936ce2be511cecb7496
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813814"
---
# <a name="interactable-object"></a>Es-Objekt

Eine Schaltfläche war lange Zeit eine Metapher, die zum Auslösen eines Ereignisses in der Welt für 2D abstrakt. In der dreidimensionalen mixed Reality-Welt müssen wir auf dieser Welt mehr Abstraktionsebenen beschränkt werden. Alles möglich ein **es Objekt** , die ein Ereignis auslöst. Ein Objekt es kann als etwas von einer Tasse Kaffee für die Tabelle, eine Gleitkommazahl in der Luft Sprechblase dargestellt werden. Wir weiterhin die Stelle, mit der herkömmlichen Schaltflächen in bestimmten Situation wie Dialogfeld Benutzeroberfläche. Die visuelle Darstellung der Schaltfläche hängt vom Kontext ab.

![Interactible Objekte](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a>Wichtige Eigenschaften des Objekts es

### <a name="visual-cue"></a>Visueller Hinweis

Visuelle Hinweise sind draußen Hinweise, die vom Auge in Form von Licht empfangen und verarbeitet visual System während der visuellen Wahrnehmung. Da visual System in vielen Arten, vor allem Menschen ausschlaggebend ist sind visuelle Hinweise eine große Informationen wie die Welt wahrgenommen wird.

In mixed Reality da die holographic Objekte mit der realen Umgebung gemischt werden ist möglicherweise schwer zu verstehen, welche Objekte, es sind. Für es Objekte in Ihrer Umgebung ist es wichtig, um differenzierte visuellen Hinweis bereitzustellen, für jede Zustand. Dadurch werden die Benutzer wissen, welcher Teil Ihrer Erfahrung ist es, und macht den Benutzer mit konsistenten Interaktion Methode sicher.

#### <a name="far-interactions"></a>Entfernte Aktivitäten

Für alle Objekte kann dieser Benutzer Blicke, Hand Chow Interaktion mit und während der Übertragung des Controllers Chow, es wird empfohlen zu anderen visuellen Hinweis für diese Eingabe drei Zustände aufweisen:
* **Standard (Beobachtung)** : Im Leerlauf Standardzustand des Objekts.
* **Ziel (wenn darauf gezeigt wird)** : Wenn das Objekt mit Blicke Cursor gerichtet ist, finger Nähe oder der Bewegungsqualität Controllers Zeiger.
* **Gedrückt**: Wenn das Objekt mit der tippbewegung Geste, drücken Sie die Finger oder während der Übertragung des Controllers auswählen-Schaltfläche gedrückt wird.

Techniken wie z. B. Hervorhebung oder Skalierung können Sie die visuellen Hinweis auf die Eingabe Status des Benutzers bereitzustellen. In Windows Mixed Reality finden Sie die Beispiele für Eingabe Zustände im Startmenü und Schaltflächen der Anwendungsleiste visualisieren. 

![Beispiel visualisieren des Status der Beobachtung, bestimmt der Zustand und Status](images/640px-interactibleobject-states.png)<br>
*Beispiel visualisieren des Status der Beobachtung, bestimmt der Zustand und Status*

![Beobachtung Zustand, Status ausgerichtet und gedrückt-Status auf holographic Schaltfläche](images/MRTK_InteractableState.png)<br>
*Beobachtung Zustand, Status ausgerichtet und gedrückt-Status auf holographic Schaltfläche*

#### <a name="neardirect-interactions"></a>NEAR(Direct) Interaktionen

HoloLens-2 unterstützt articulated manuell Nachverfolgen von Eingaben mit Objekten interagieren können. Ohne Übermitteln von haptischem Feedback und die perfekte Tiefe Wahrnehmung in einigen Fällen kann es schwierig sein, teilen Sie Ihre Hand wie weit entfernt von einem Objekt ist, oder gibt an, ob Sie berühren. Es ist wichtig, ausreichend optische Hinweise aus, um den Zustand des Objekts und insbesondere bei der Sie sich in Bezug auf Hologramme Kommunikation bereitzustellen.

Verwenden Sie visuelles Feedback, um Folgendes zu kommunizieren:
* **Standard (Beobachtung)** : Im Leerlauf Standardzustand des Objekts.
* **Hover**: Wenn wird manuell in der Nähe von ggf. ein Hologramm, Änderung Visualisierungen für die Kommunikation von dieser Seite – Hologramm verwendet. 
* **Abstand und Interaktionspunkt**: Manuell – Hologramm erreicht, Entwerfen Sie Feedback an den projizierten Punkt der Interaktion, ebenfalls zu kommunizieren, wie weit entfernt das Objekt der Finger befindet
* **Wenden Sie sich an Begin**: Änderung Visuals (Licht, Farbe) zu kommunizieren, dass die Fingereingabe ist aufgetreten.
* **Halten Sie**: Ändern von Visualisierungen (Licht, Farbe) Wenn das Objekt zugreifen wird.
* **Wenden Sie sich an End**: Ändern von Visualisierungen ("hell", "Farbe") bei der Beendigung Touch.

![Beispiel für die Visualisierung in der Nähe von Interaktion-Status](images/640px-interactibleobject-states-near.jpg)<br>
*Beispiel für die Visualisierung in der Nähe von Interaktion-Status*

Die [-Schaltfläche in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) zeigt ein Beispiel für die Interaktion mit anderen Eingabe-Zustände zu visualisieren.

![Beispiel für pressable Schaltfläche HoloLens 2](images/640px-interactibleobject-pressablebutton-650px2.jpg)<br>
*Beispiel für pressable Schaltfläche HoloLens 2*

In 2 für HoloLens wird ein zusätzlicher visuellen Hinweis auf die Zuverlässigkeit des Benutzers, für die Wahrnehmung der Tiefe verbessert. Der Ring auf die fingertippen angezeigt wird, und nach unten skaliert werden kann, wie die fingertippen ruft näher an das Objekt ab. Der Ring konvergiert letztendlich in Punkte. drücken Sie die Status. Dieser visuelle Unterstützung hilft die Benutzer, der den Abstand zwischen dem Objekt zu verstehen.

![Fingertippen Ring Visualisierung](images/640px-interactibleobject-pressablebutton-650px3.jpg)<br>
*Fingertippen Ring Visualisierung HoloLens 2*

![Visuelles Feedback auf der Hand NEAR](images/HoloLens2_Proximity.gif)<br>
*Beispiel für visuelles Feedback auf der Grundlage der Nähe - BoundingBox-Element*


### <a name="audio-cue"></a>Audiohinweis
Für die direkte Hand-Interaktionen kann in richtigen audio Feedback die benutzererfahrung erheblich verbessern. Verwenden Sie audio Feedback, um Folgendes zu kommunizieren:
* **Wenden Sie sich an beginnen**: Wiedergeben Sie sound, wenn die Fingereingabe beginnt
* **Wenden Sie sich an End**: Touch-End sound wiedergeben
* **Ziehpunkte beginnen**: Wiedergeben Sie sound, wenn Ziehpunkte gestartet wird.
* **Ziehen Sie End**: Ziehpunkte End sound wiedergeben

### <a name="voice-command"></a>Voice-Befehl
Für den klassentypobjekte es ist es wichtig, alternative Interaktion Optionen unterstützen. Im standardmäßigen, wird empfohlen, Sprachbefehl für alle Objekte zu unterstützen, es sind. Um die Erkennbarkeit zu verbessern, können Sie die QuickInfo auf Hover-Zustand bereitstellen.

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="QuickInfo für den Voice-Befehl" width="350"><br/>*QuickInfo für den Voice-Befehl*

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a>Erstellen es-Objekts mit Mixed Reality-Toolkit (MRTK)

In der  **[Mixed Reality-Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , finden Sie die Reihe von Unity-Skripts und prefabs (Vorlagen), mit denen Sie es Objekte erstellen. Sie können diese verwenden, um Objekte auf verschiedene Arten von Eingabe Interaktion Zustände zu reagieren.

* **[Es](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)**
* **[Schaltfläche "](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)**
* **[Hand Interaktion Beispiele für die Szene](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)**

MixedRealityToolkit des Standard-Shader stellt verschiedene Optionen bereit, z. B. **NEAR Licht** , mit dem Sie die SEH- und Hinweise zu erstellen.
* **[MRTK Standard-Shader](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)**


## <a name="see-also"></a>Siehe auch

* **[Umgebendes Feld](app-bar-and-bounding-box.md)**
* **[Eine objektauflistung](object-collection.md)**
* **[Billboarding und tag-along](billboarding-and-tag-along.md)**
