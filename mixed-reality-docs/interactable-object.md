---
title: Interactable-Objekt
description: Eine Schaltfläche ist lange eine Metapher, die zum Auslösen eines Ereignisses in der 2D-abstrakten Welt verwendet wird. In der dreidimensionalen Mixed Reality-Welt müssen wir nicht mehr auf diese Abstraktions Welt beschränkt werden.
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Gemischte Realität, Steuerelemente, Interaktion, UI, UX
ms.openlocfilehash: 57299cbb758a69603fc68ad5d43af8f2216e5104
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415332"
---
# <a name="interactable-object"></a>Interactable-Objekt

Eine Schaltfläche ist lange eine Metapher, die zum Auslösen eines Ereignisses in der 2D-abstrakten Welt verwendet wird. In der dreidimensionalen Mixed Reality-Welt müssen wir nicht mehr auf diese Abstraktions Welt beschränkt werden. Dabei kann es sich um ein Objekt handeln, das ein **Objekt** ist, das ein Ereignis auslöst. Ein Objekt, das sich in der Tabelle befindet, kann als beliebiger von einem Kaffeebecher in der Tabelle dargestellt werden. Wir verwenden weiterhin herkömmliche Schaltflächen in bestimmten Situationen, z. b. in der Dialogfeld Benutzeroberfläche. Die visuelle Darstellung der Schaltfläche hängt vom Kontext ab.

![Objekte mit Interaktivität](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a>Wichtige Eigenschaften des Interaktionen-Objekts

### <a name="visual-cue"></a>Visueller Hinweis

Visuelle Hinweise sind sensorische Hinweise, die vom visuellen System während der visuellen Darstellung vom visuellen System empfangen werden. Da das visuelle System in vielen Arten, insbesondere bei Menschen, dominant ist, stellen visuelle Hinweise eine große Informationsquelle dar, in der die Welt wahrgenommen wird.

Da die Holographic-Objekte in gemischter Umgebung mit der realen Umgebung gemischt sind, kann es schwierig sein, die Objekte zu erkennen, die miteinander zu interagieren sind. Für alle Objekte, die sich in der Benutzersprache befinden, ist es wichtig, für jeden Eingabe Zustand einen differenzierten visuellen Hinweis bereitzustellen. Dadurch kann der Benutzer verstehen, welcher Teil ihrer Benutzeroberflächen Interaktionen ist, und der Benutzer ist mit der konsistenten Interaktions Methode sicher.

#### <a name="far-interactions"></a>Weite Interaktionen

Für alle Objekte, die der Benutzer mit dem Blick auf "Blick", "Hand Ray" und "Motion Controller" interagieren kann, empfiehlt es sich, einen anderen visuellen Hinweis auf die drei Eingabe Zustände zu haben:
* **Standard (Überwachung)** : Der standardmäßige Leerlauf Status des Objekts.
* **Ziel (Hover)** : , Wenn das Objekt mit dem Cursor Cursor, der fingernähe oder dem Bewegungs Controller Zeiger ausgerichtet ist.
* **Gedrückt**: Wenn das Objekt mit der Tastenkombination gedrückt wird, klicken Sie auf die Schaltfläche zum Auswählen von Finger oder Motion Controller.

Sie können Techniken wie z. b. Hervorhebung oder Skalierung verwenden, um visuelle Eingaben für die Eingabe Zustände des Benutzers bereitzustellen. In der gemischten Realität von Windows finden Sie die Beispiele für die Visualisierung verschiedener Eingabe Zustände in den Schaltflächen Startmenü und App-Leiste. 

![Beispiel für die Visualisierung des Überwachungs Zustands, des Ziel Zustands und des gedrückten Zustands](images/640px-interactibleobject-states.png)<br>
*Beispiel für die Visualisierung des Überwachungs Zustands, des Ziel Zustands und des gedrückten Zustands*

![Überwachungszustand, Ziel Status und gedrückter Zustand auf der Holographic-Schaltfläche](images/MRTK_InteractableState.png)<br>
*Überwachungszustand, Ziel Status und gedrückter Zustand auf der Holographic-Schaltfläche*

#### <a name="neardirect-interactions"></a>Near (Direct) Interaktionen

Hololens 2 unterstützt die Eingabe von Handgelenk Nachverfolgung, mit der Sie mit Objekten interagieren können. Ohne haptisches Feedback und eine perfekte Tiefe Wahrnehmung kann es manchmal schwierig sein, festzustellen, wie weit die Hand von einem Objekt entfernt ist oder ob Sie sich berühren. Es ist wichtig, genügend visuelle Hinweise bereitzustellen, um den Status des Objekts und insbesondere die Hände in Bezug auf holograms zu kommunizieren.

Verwenden Sie visuelles Feedback, um Folgendes zu kommunizieren:
* **Standard (Überwachung)** : Der standardmäßige Leerlauf Status des Objekts.
* **Hover**: Wenn "Hand" in der Nähe eines Hologramms ist, ändern Sie die visuellen Elemente, um zu kommunizieren 
* **Entfernung und Punkt der Interaktion**: Geben Sie als Hand "Hologram" ein, um den projizierten Interaktionspunkt zu vermitteln, und wie weit vom Objekt der Finger ist.
* **Kontakt Beginn**: Visuelle Elemente (hell, Farbe) ändern, um zu kommunizieren, dass die Fingereingabe aufgetreten ist
* **Verstanden**: Ändern Sie visuelle Elemente (hell, Farbe), wenn das Objekt erfasst wird.
* **Kontakt Ende**: Ändern Sie visuelle Elemente (hell, Farbe), wenn die Fingereingabe beendet wurde.

![Beispiel für die Visualisierung von Near-Interaktions Zuständen](images/640px-interactibleobject-states-near.jpg)<br>
*Beispiel für die Visualisierung von Near-Interaktions Zuständen*

Die [Schaltfläche in hololens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) zeigt das Beispiel für die Visualisierung verschiedener Eingabe Interaktions Zustände.

![Beispiel für Druck Bare Schaltfläche in hololens 2](images/640px-interactibleobject-pressablebutton-650px2.jpg)<br>
*Beispiel für Druck Bare Schaltfläche in hololens 2*

In hololens 2 gibt es einen zusätzlichen visuellen Hinweis, der das Vertrauen des Benutzers auf die Tiefe Wahrnehmung verbessert. Der Ring auf dem Fingertipp wird angezeigt und herunterskaliert, wenn sich der Fingertipp näher an dem Objekt nähert. Der Ring wird schließlich mit einem Punkt auf dem Press Zustand konvergiert. Diese visuelle Visualisierung unterstützt den Benutzer beim Verständnis der Entfernung zum Objekt.

![Visualisierung des Fingertip Rings](images/640px-interactibleobject-pressablebutton-650px3.jpg)<br>
*Visualisierung des Fingertip Rings in hololens 2*

![Visuelles Feedback in der Nähe](images/HoloLens2_Proximity.gif)<br>
*Beispiel für visuelles Feedback basierend auf dem umgebenden Begrenzungsfeld*


### <a name="audio-cue"></a>Audiohinweis
Bei direkten Interaktionen kann das richtige Audiofeedback die Benutzer Leistung erheblich verbessern. Verwenden Sie Audiofeedback, um Folgendes zu kommunizieren:
* **Kontakt Beginn**: Sound wiedergeben, wenn der Touchscreen beginnt
* **Kontakt Ende**: Sound am Fingerabdruck abspielen
* **Beginn**: Sound wiedergeben, wenn Sie beginnen
* **Ende am Ende**: Sound beim Ende abspielen

### <a name="voice-command"></a>Sprachbefehl
Bei allen Objekt übergreifenden Objekten ist es wichtig, Alternative Interaktions Optionen zu unterstützen. Standardmäßig wird empfohlen, den Voice-Befehl für alle Objekte zu unterstützen, die interactable sind. Um die Auffindbarkeit zu verbessern, können Sie QuickInfo im Hover-Zustand bereitstellen.

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="QuickInfo für den Voice-Befehl" width="350"><br/>*QuickInfo für den Voice-Befehl*

## <a name="sizing"></a>Größenanpassung
Um sicherzustellen, dass alle austauschbaren Objekte problemlos von Benutzern berührt werden können, sollten Sie sicherstellen, dass die Interaktionen eine minimale Größe (den visuellen Winkel, der häufig in Grad des visuellen Bogens gemessen wird) basierend auf der Entfernung des Benutzers erfüllt. Der visuelle Winkel basiert auf der Entfernung zwischen den Augen des Benutzers und dem Objekt und bleibt konstant, während sich die physische Größe des Ziels möglicherweise ändert, wenn sich der Abstand vom Benutzer ändert. Um die erforderliche physische Größe eines Objekts basierend auf der Entfernung des Benutzers zu bestimmen, versuchen Sie, einen visuellen Winkel Rechner wie [diesen](http://elvers.us/perception/visualAngle/)zu verwenden.

Im folgenden finden Sie die Empfehlungen für die Mindestgröße von Interaktionen-Inhalten.

### <a name="target-size-for-direct-hand-interaction"></a>Zielgröße für direkte Interaktion
| Flüge | Anzeige Winkel | Größe |
|---------|---------|---------|
| 45cm  | nicht kleiner als 2 ° | 1,6 x 1,6 cm |

![Zielgröße für direkte Interaktion](images/TargetSizingNear.jpg)<br>
*Zielgröße für direkte Interaktion*

Beim Erstellen von Schaltflächen für die direkte Interaktion empfehlen wir eine größere Mindestgröße von 3,2 x 3,2 cm, um sicherzustellen, dass genügend Speicherplatz vorhanden ist, um ein Symbol und potenziell Text zu enthalten. * *

| Flüge | Mindestgröße |
|---------|---------|
| 45cm  | 3,2 x 3,2 cm |

![Zielgröße für die Schaltflächen](images/TargetSizingButtons.png)<br>
*Zielgröße für die Schaltflächen*


### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>Zielgröße für die Hand Strahl-oder Blick Interaktion
| Flüge | Anzeige Winkel | Größe |
|---------|---------|---------|
| 2 min  | nicht kleiner als 1 ° | 3,5 x 3,5 cm |

![Zielgröße für die Hand Strahl-oder Blick Interaktion](images/TargetSizingFar.jpg)<br>
*Zielgröße für die Hand Strahl-oder Blick Interaktion*

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a>Erstellen eines Interaktionen-Objekts mit Mixed Reality Toolkit (mrtk)

Im **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)** finden Sie die Reihe der Unity-Skripts und-präfaben, die Sie beim Erstellen von Objekt übergreifenden Objekten unterstützen. Sie können diese verwenden, um zu ermöglichen, dass Objekte auf verschiedene Typen von Eingabe Interaktions Zuständen reagieren.

* [Interaktionen](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) (Schaltfläche)
* [Beispiel Szenen für Hand Interaktion](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

Der Standard-Shader von mixedrealitytoolkit bietet verschiedene Optionen, wie z. b. **near Light** , mit denen Sie visuelle und Audiohinweise erstellen können.
* [Mrtk-Standard-Shader](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


## <a name="see-also"></a>Siehe auch

* [Begrenzungs Fenster](app-bar-and-bounding-box.md)
* [Objektsammlung](object-collection.md)
* [Billboarding und Tag-along](billboarding-and-tag-along.md)