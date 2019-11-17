---
title: Interactable object
description: A button has long been a metaphor used for triggering an event in the 2D abstract world. In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Mixed Reality, Controls, interaction, ui, ux
ms.openlocfilehash: 73c8a3ce9e01f580ecbae23f2178871642c4540e
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143259"
---
# <a name="interactable-object"></a>Interactable object

![Interactible objects](images/UX/UX_Hero_Interactable.jpg)

A button has long been a metaphor used for triggering an event in the 2D abstract world. In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore. Anything can be an **interactable object** that triggers an event. An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air. We still do make use of traditional buttons in certain situation such as in dialog UI. The visual representation of the button depends on the context.

<br>

---


## <a name="important-properties-of-the-interactable-object"></a>Important properties of the interactable object

### <a name="visual-cues"></a>Visuelle Hinweise

Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception. Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.

Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with. For any interactable objects in your experience, it is important to provide differentiated visual cues for each input state. This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.

<br>

---

### <a name="far-interactions"></a>Far interactions

For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:

:::row:::
    :::column:::
       ![interactibleobject-states-default](images/interactibleobject-states-default.jpg)<br>
       **Default (Observation) state**<br>
        Default idle state of the object.
    The cursor is not on the object. Hand is not detected.
    :::column-end:::
    :::column:::
       ![interactibleobject-states-targeted](images/interactibleobject-states-targeted.jpg)<br>
        **Targeted (Hover) state**<br>
        When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.
    The cursor is on the object. Hand is detected, ready.
    :::column-end:::
    :::column:::
       ![interactibleobject-states-pressed](images/interactibleobject-states-pressed.jpg)<br>
       **Pressed state**<br>
        When the object is pressed with an air tap gesture, finger press or motion controller's select button.
    The cursor is on the object. Hand is detected, air tapped.
    :::column-end:::
:::row-end:::

<br>

---

You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state. In mixed reality, you can find the examples of visualizing different input states on the Start menu and with app bar buttons. 

Here is what these states look like on a **holographic button**:

:::row:::
    :::column:::
       ![interactibleobject-states-default](images/MRTK_InteractableState-default.jpg)<br>
       **Default (Observation) state**<br>
    :::column-end:::
    :::column:::
       ![interactibleobject-states-targeted](images/MRTK_InteractableState-targeted.jpg)<br>
        **Targeted (Hover) state**<br>
    :::column-end:::
    :::column:::
       ![interactibleobject-states-pressed](images/MRTK_InteractableState-pressed.jpg)<br>
       **Pressed state**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a>Near interactions (direct) 

HoloLens 2 supports articulated hand tracking input which allows you to interact with objects. Without haptic feedback and perfect depth perception, it can sometimes be hard to tell how far away your hand is from an object or whether you are touching it. It is important to provide enough visual cues to communicate the state of the object and in particular the state of your hands in relation to that object.

Use visual feedback to communicate the following:
* **Default (Observation)** : Default idle state of the object.
* **Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram. 
* **Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is
* **Kontakt beginnt**: Ändern der visuellen Elemente (hell, Farbe), um zu kommunizieren, dass eine Fingereingabe aufgetreten ist
* **Verstanden**: Ändern von visuellen Elementen (hell, Farbe), wenn das Objekt erfasst wird
* **Kontakt Ende**: Ändern der visuellen Elemente (hell, Farbe), wenn die Fingereingabe beendet wurde

<br>

---

:::row:::
    :::column:::
        ![Hover (weit)](images/640px-interactibleobject-states-near-hover.jpg)<br>
        **Hover (weit)**<br>
        Hervorhebung basierend auf der Nähe der Hand.
    :::column-end:::
    :::column:::
        ![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)<br>
        **Hover (in der Nähe)**<br>
        Die Größenänderungen werden basierend auf der Entfernung zur Hand hervorgehoben.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![berühren/drücken](images/640px-interactibleobject-states-near-press.jpg)<br>
        **Berühren/drücken**<br>
        Feedback zu Visual Plus-Audiodaten.
    :::column-end:::
    :::column:::
        ![verstanden](images/640px-interactibleobject-states-near-grasp.jpg)<br>
        **Gespür**<br>
        Feedback zu Visual Plus-Audiodaten.
    :::column-end:::
:::row-end:::

<br>

<br>

---

Eine [Schaltfläche in hololens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) ist ein Beispiel dafür, wie die verschiedenen Eingabe Interaktions Zustände visualisiert werden:

:::row:::
    :::column:::
        Standard ![](images/640px-interactibleobject-pressablebutton-default.jpg)<br>
        **Vorgegebene**<br>
    :::column-end:::
    :::column:::
        ![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)<br>
        **Hocker**<br>
        Zeigen Sie einen near-basierten Beleuchtungs Effekt an.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Toucheingabe](images/640px-interactibleobject-pressablebutton-touch.jpg)<br>
        **Toucheingabe**<br>
        Ripple-Effekt anzeigen.
    :::column-end:::
    :::column:::
        ![drücken](images/640px-interactibleobject-pressablebutton-press.jpg)<br>
        **Drückt**<br>
        Verschieben Sie die Vorderseite.
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a>Der visuelle Hinweis "Ring" auf hololens 2<br>
        Auf hololens 2 gibt es einen zusätzlichen visuellen Hinweis, der die Wahrnehmung der Tiefe des Benutzers unterstützt. Ein Ring in der Nähe des fingerabbilds wird angezeigt und herunterskaliert, wenn sich der Fingertipp näher an das Objekt anpasst. Der Ring wird schließlich in einen Punkt konvergiert, wenn der gedrückte Zustand erreicht wird. Diese visuelle Visualisierung unterstützt den Benutzer dabei, zu verstehen, wie weit Sie aus dem-Objekt stammen.<br>
        <br>
        *Video Schleife: Beispiel für visuelles Feedback basierend auf der Nähe eines umgebenden Felds*
    :::column-end:::
        :::column:::
        ![Speicher](images/spacer-20x582.png)<br>
       ![Sie visuelles Feedback in der Nähe](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a>Audiohinweise

Bei direkter Hand Interaktion kann das richtige Audiofeedback die Benutzer Leistung erheblich verbessern. Verwenden Sie Audiofeedback, um Folgendes zu kommunizieren:
* **Kontakt beginnt**: Sound abspielen, wenn der Fingerabdruck beginnt
* **Kontakt**Ende: Sound am Touchscreen abspielen
* **Beginn**: Sound abspielen, wenn der Start beginnt
* Aufnahme **Ende**: Sound wiedergeben, wenn der Griff endet

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a>Sprachbefehle<br>
        Bei allen Objekt übergreifenden Objekten ist es wichtig, Alternative Interaktions Optionen zu unterstützen. Standardmäßig wird empfohlen, dass [sprach](voice-design.md) Befehle für alle Objekte unterstützt werden, die interacbar sind. Um die Auffindbarkeit zu verbessern, können Sie auch eine QuickInfo für den Hover-Zustand bereitstellen.<br>
        <br>
        *Bild: QuickInfo für den Voice-Befehl*
    :::column-end:::
        :::column:::
       ![Sprachbefehl](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a>Empfehlungen zur Größenanpassung 

Um sicherzustellen, dass alle austauschbaren Objekte problemlos von Benutzern berührt werden können, sollten Sie sicherstellen, dass die Interaktionen eine minimale Größe (den visuellen Winkel, der häufig in Grad des visuellen Bogens gemessen wird) basierend auf der Entfernung des Benutzers erfüllt. Der visuelle Winkel basiert auf der Entfernung zwischen den Augen des Benutzers und dem Objekt und bleibt konstant, während sich die physische Größe des Ziels möglicherweise ändert, wenn sich der Abstand vom Benutzer ändert. Um die erforderliche physische Größe eines Objekts basierend auf der Entfernung des Benutzers zu bestimmen, versuchen Sie, einen visuellen Winkel Rechner wie [diesen](https://elvers.us/perception/visualAngle/)zu verwenden.

Im folgenden finden Sie die Empfehlungen für die Mindestgröße von Interaktionen-Inhalten.


### <a name="target-size-for-direct-hand-interaction"></a>Zielgröße für direkte Interaktion

| Flüge | Anzeige Winkel | Größe |
|---------|---------|---------|
| 45cm  | nicht kleiner als 2 ° | 1,6 x 1,6 cm |

![Zielgröße für die direkte Interaktion](images/TargetSizingNear.jpg)<br>
*Zielgröße für direkte Interaktion*

<br>

### <a name="target-size-for-buttons"></a>Zielgröße für Schaltflächen

Beim Erstellen von Schaltflächen für die direkte Interaktion empfehlen wir eine größere Mindestgröße von 3,2 x 3,2 cm, um sicherzustellen, dass genügend Speicherplatz vorhanden ist, um ein Symbol und potenziell einen Text zu enthalten.

| Flüge | Mindestgröße |
|---------|---------|
| 45cm  | 3,2 x 3,2 cm |

![Zielgröße für die Schaltflächen](images/TargetSizingButtons.png)<br>
*Zielgröße für die Schaltflächen*

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>Zielgröße für die Hand Strahl-oder Blick Interaktion
| Flüge | Anzeige Winkel | Größe |
|---------|---------|---------|
| 2 min  | nicht kleiner als 1 ° | 3,5 x 3,5 cm |

![Zielgröße für die Hand Strahl-oder Blick Interaktion](images/TargetSizingFar.jpg)<br>
*Zielgröße für die Hand Strahl-oder Blick Interaktion*


<br>

---


## <a name="interactable-object-in-mrtkmixed-reality-toolkit-for-unit"></a>Interactable-Objekt in mrtk (Mixed Reality Toolkit) für Unit

In **[mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** können Sie das Skript [**interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) verwenden, damit Objekte auf verschiedene Typen von Eingabe Interaktions Zuständen reagieren. Es unterstützt verschiedene Arten von Themen, mit denen Sie visuelle Zustände definieren können, indem Sie Objekteigenschaften wie Farbe, Größe, Material und Shader steuern.

* [Interaktionen](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [Beispiel Szenen für Hand Interaktion](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

Der Standard-Shader von mixedrealitytoolkit bietet verschiedene Optionen, wie z. b. **near Light** , mit denen Sie visuelle und Audiohinweise erstellen können.
* [Mrtk-Standard-Shader](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a>Weitere Informationen:

* [Cursor](cursors.md)
* [Hand Strahl](point-and-commit.md)
* [Button](button.md)
* [Interaktionsfähiges Objekt](interactable-object.md)
* [Begrenzungsrahmen und App-Leiste](app-bar-and-bounding-box.md)
* [Bearbeitung](direct-manipulation.md)
* [Handmenü](hand-menu.md)
* [Near-Menü](near-menu.md)
* [Objektsammlung](object-collection.md)
* [Sprachbefehl](voice-input.md)
* [Tastatur](keyboard.md)
* [QuickInfo](tooltip.md)
* [Tafel](slate.md)
* [Schieberegler](slider.md)
* [Shader](shader.md)
* [Billboarding und Tag-along](billboarding-and-tag-along.md)
* [Anzeigen des Fortschritts](progress.md)
* [Oberflächen Magnetismus](surface-magnetism.md)
