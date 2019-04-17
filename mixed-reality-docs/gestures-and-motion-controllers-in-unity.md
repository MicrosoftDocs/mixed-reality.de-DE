---
title: Gesten und Motion-Controller in Unity
description: Es gibt zwei grundlegende Methoden für die Reaktion auf Ihre Blicke in Unity, gestensteuerung und Motion-Controller.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Bewegungen, während der Übertragung Controller, Unity, Blicke, Eingabe
ms.openlocfilehash: d98590f9a6c40336a13cb75e8050e13edfaa2a6c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593288"
---
# <a name="gestures-and-motion-controllers-in-unity"></a>Gesten und Motion-Controller in Unity

Es gibt zwei grundlegende Methoden, Maßnahmen zu ergreifen, die auf Ihre [in Unity bestaunen](gaze-in-unity.md), [übergeben Gesten](gestures.md) und [motion Controller](motion-controllers.md). Die Daten für beide Quellen von räumlichen Eingabe greifen Sie über die gleichen APIs in Unity.

Unity bietet zwei bevorzugte Möglichkeiten auf räumlichen Daten für die Windows Mixed Reality, die allgemeine *Input.GetButton/Input.GetAxis* APIs, die über mehrere Unity-XR-SDKs, zusammenarbeiten und eine *InteractionManager / GestureRecognizer* API, die speziell für Windows Mixed Reality, die sämtliche räumliche Eingabedaten verfügbar macht.

## <a name="unity-buttonaxis-mapping-table"></a>Unity-Schaltfläche/Achse-Zuordnungstabelle

Die Schaltfläche und die Achse-IDs in der folgenden Tabelle werden im Unity-Eingabe-Manager für Windows Mixed Reality-Motion-Controller durch den *Input.GetButton/GetAxis* -APIs, während die Spalte "MR für Windows-spezifische" auf Eigenschaften verweist verfügbar auf der *InteractionSourceState* Typ. Jede dieser APIs werden in den folgenden Abschnitten ausführlich beschrieben.

Die Schaltfläche "/ Achse-ID-Zuordnungen für Windows Mixed Reality entsprechen im Allgemeinen die Oculus Schaltfläche/Achse-IDs.

Die Schaltfläche "/ Achse-ID-Zuordnungen für Windows Mixed Reality unterscheiden sich von OpenVRs Zuordnungen auf zwei Arten:
1. Die Zuordnung wird verwendet, Touchpad-IDs, die sich von Ministick, Controller mit Thumbsticks und Touchpad zu unterstützen.
2. Die Zuordnung wird vermieden, überladen die Schaltfläche ein "und" X-IDs für die Menü-Schaltflächen, die für physische ABXY Schaltflächen verfügbar gehalten werden.

<table>
<tr>
<th rowspan="2">Input </th><th colspan="2"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Allgemeine Unity-APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">Windows-MR-spezifische Eingabe-API</a><br />(XR.WSA.Input)</th>
</tr><tr>
<th> Links </th><th> Rechte Seite</th>
</tr><tr>
<td> Select Trigger gedrückt </td><td> 9 = 1.0-Achse </td><td> Axis 10 = 1.0 </td><td> selectPressed</td>
</tr><tr>
<td> Wählen Sie analog Triggerwert </td><td> Achse 9 </td><td> Axis 10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> Select Trigger, die teilweise gedrückt. </td><td> Schaltfläche 14 <i>(Gamepad Compat)</i> </td><td> Schaltfläche 15 <i>(Gamepad Compat)</i> </td><td> SelectPressedAmount &gt; 0,0</td>
</tr><tr>
<td> Menüschaltfläche gedrückt </td><td> Schaltfläche 6 * </td><td> Schaltfläche 7 * </td><td> menuPressed</td>
</tr><tr>
<td> Ziehpunkt ist gedrückt. </td><td> Achse 11 = 1.0 (keine analogen Werte)<br />Schaltfläche 4 <i>(Gamepad Compat)</i> </td><td> Achse 12 = 1.0 (keine analogen Werte)<br />Schaltfläche 5 <i>(Gamepad Compat)</i> </td><td> Halten Sie</td>
</tr><tr>
<td> Ministick X <i>(linke: Bereich von -1,0, rechts: 1.0)</i> </td><td> Axis 1 </td><td> Achse 4 </td><td> thumbstickPosition.x</td>
</tr><tr>
<td> Ministick Y <i>(Top: Bereich von -1,0, unten: 1.0)</i> </td><td> Achse 2 </td><td> Axis 5 </td><td> thumbstickPosition.y</td>
</tr><tr>
<td> Ministick gedrückt </td><td> Schaltfläche 8 </td><td> Schaltfläche 9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> Touchpad X <i>(linke: Bereich von -1,0, rechts: 1.0)</i> </td><td> Axis 17* </td><td> Axis 19* </td><td> touchpadPosition.x</td>
</tr><tr>
<td> Touchpad Y <i>(Top: Bereich von -1,0, unten: 1.0)</i> </td><td> Axis 18* </td><td> Achse 20 * </td><td> touchpadPosition.y</td>
</tr><tr>
<td> Touchpad berührt werden. </td><td> Schaltfläche 18 * </td><td> Schaltfläche 19 * </td><td> touchpadTouched</td>
</tr><tr>
<td> Touchpad gedrückt </td><td> Schaltfläche 16 * </td><td> Schaltfläche 17 * </td><td> touchpadPressed</td>
</tr><tr>
<td> 6DoF Ziehpunkt Haltung oder Zeiger Haltung </td><td colspan="2"> <i>Ziehpunkt</i> nur darstellen: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></td><td> Übergeben Sie <i>Ziehpunkt</i> oder <i>Zeiger</i> als Argument: sourceState.sourcePose.TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> Status der änderungsnachverfolgung </td><td colspan="2"> <i>Position Genauigkeit und Quelle Verlust Risiko nur MR-spezifische API erhältlich</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>Diese Schaltfläche/Achse IDs unterscheiden sich von der IDs, die Unity für OpenVR aufgrund von Konflikten in den Zuordnungen von Gamepads, Oculus Touch und OpenVR verwendet wird.

## <a name="grip-pose-vs-pointing-pose"></a>Ziehpunkt Haltung im Vergleich zu zeigenden Haltung

Windows Mixed Reality unterstützt Controller, die während der Übertragung in einer Vielzahl von Formfaktoren, des Controllers Entwurf unterscheidet sich in der Beziehung zwischen Hand-Position des Benutzers und der natürliche "Weiterleiten" Richtung dieser apps sollten mit auf beim Rendern der Controller.

Um diese Controller besser darstellen zu können, es gibt zwei Arten von ist, können Sie für jede Datenquelle Interaktion untersuchen, der **Ziehpunkt Haltung** und **Zeiger Haltung**. Sowohl der Ziehpunkt Haltung und Zeiger Haltung Koordinaten werden alle Unity-APIs in globalen Unity globalen Koordinaten angegeben.

### <a name="grip-pose"></a>Ziehpunkt Haltung

Die **Ziehpunkt Haltung** stellt den Speicherort des dies im Handumdrehen einer Hand, die von einem HoloLens erkannt werden oder dies mit einem Controller während der Übertragung im Handumdrehen dar.

Für immersive Headsets, wird der Haltung Ziehpunkt am besten zum Rendern verwendet **des Benutzers manuell** oder **frei, die ein Objekt des Benutzers verfügen**, z. B. eine "sword" oder dem damoklesschwert. Der Ziehpunkt Haltung wird auch verwendet, bei der Visualisierung von eines Controllers während der Übertragung als die **zum Rendern Modell** bereitgestellten von Windows für eine Bewegung Controller als Ursprungs- und Mittelpunkt der Drehung der Ziehpunkt Haltung verwendet.

Der Ziehpunkt Haltung wird insbesondere wie folgt definiert:
* Die **fassen Sie Position**: Der Schwerpunkt Palm, wenn der Controller natürlich mit angepasst nach links oder rechts zentriert die Position in den Ziehpunkt. Auf dem Windows Mixed Reality-Motion-Controller entspricht dieser Position in der Regel die Schaltfläche "verstehen".
* Die **fassen Sie die rechte Achse die Ausrichtung**: Wenn Sie Ihre Hand, um einen flachen 5 Finger Haltung bilden vollständig geöffnet haben, dem Strahl, der ist normal, zu Ihrem Palm (vorwärts vom linken Palm, rückwärts von rechts Palm)
* Die **fassen Sie die Ausrichtung, vorwärts gerichtete Achse**: Wenn Sie Ihre Hand schließen, teilweise (als ob den Controller enthält), der vom Strahl, der "forward" über die Tube gebildet, indem die Finger nicht-Thumb-Steuerelement zeigt.
* Die **fassen Sie die Ausrichtung des einrichten Achse**: Die nach-oben-Achse impliziert durch die rechts- und -Weiterleiten-Definitionen.

Sie können auf den Ziehpunkt Haltung über anbieterübergreifende Eingabe für die entweder von Unity-API zugreifen (*[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) oder über die Windows-MR-spezifische API (*sourceState.sourcePose.TryGetPosition/Rotation*, Anfordern von Daten für darstellen der **Ziehpunkt** Knoten).

### <a name="pointer-pose"></a>Zeiger Haltung

Die **Zeiger Haltung** stellt die Spitze des Controllers vorwärts verweist.

Die vom System bereitgestellte Zeiger Haltung ist am besten zum Raycast verwendet, wenn Sie können **das Controllermodell selbst rendern**. Wenn Sie ein anderes virtuelles Objekt anstelle der Controller, z. B. eine virtuelle damoklesschwert, rendern sollten Sie mit einem Strahl verweisen, die für diese virtuellen Objekts, z. B. ein Strahl, die entlang der Lauf der app definierte damoklesschwert Modell geleitet. Da Benutzer die virtuelles Objekt und nicht auf dem physischen Controller sehen können, werden zeigen mit dem virtuellen Objekt natürlichere für Benutzer, die Ihre app Sie wahrscheinlich.

Der Zeiger Haltung ist derzeit verfügbar in Unity nur über die Windows-MR-spezifische-API, *sourceState.sourcePose.TryGetPosition/Rotation*, und übergeben Sie *InteractionSourceNode.Pointer* wie die Argument.

## <a name="controller-tracking-state"></a>Status der Controller-änderungsnachverfolgung

Wie bei der Headsets muss die Windows Mixed Reality-Motion-Controller keine Einrichtung der externen Überwachung Sensoren. Stattdessen werden die Controller von Sensoren in den Kopfhörer selbst nachverfolgt.

Wenn der Benutzer aus den Kopfhörer des Sichtfelds Controller verschoben wird, wird in den meisten Fällen Windows weiterhin Positionen von Controller ableiten und Dokumente für die app bereitstellen. Wenn der Controller verloren hat visual nachverfolgung für lange genug, des Controllers Positionen an ungefähren Genauigkeit Positionen gelöscht werden.

An diesem Punkt werden Body-Sperre den Controller für den Benutzer, die Position des Benutzers nachverfolgen, wie sie beim Verfügbarmachen immer noch auf "true" des Controllers-Ausrichtung mit der internen Ausrichtung Sensoren, verschieben. Viele apps, die auf verweisen, und aktivieren die Elemente der Benutzeroberfläche mithilfe von verwaltungscontrollern können normalerweise ungefähre Genauigkeit im bemerken die Benutzer arbeiten.

Die beste Möglichkeit, ein Gefühl dafür ist, um es selbst auszuprobieren. Sehen Sie sich dieses Video mit Beispielen für die immersiven Inhalte, die während der Übertragung mit verschiedenen Status der Überwachung funktioniert:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a>Schlussfolgerungen über zustandsnachverfolgung explizit

Apps, die Positionen, die je nach der zustandsnachverfolgung unterschiedlich behandeln möchten möglicherweise weiter gehen und überprüfen Sie die Eigenschaften des controllerzustands, z. B. *SourceLossRisk* und *PositionAccuracy*:

<table>
<tr>
<th> Status der änderungsnachverfolgung </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>Hohe Genauigkeit</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> Hoch </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Hohe Genauigkeit (Risiko der verlierenden)</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: green; color: white"> Hoch </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Ungefähre Genauigkeit</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Ungefähr </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Keine position</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Ungefähr </td><td style="background-color: orange"> false</td>
</tr>
</table>

Statusdefinitionen nachverfolgung während der Übertragung Controller sind wie folgt definiert:
* **Hoher Genauigkeit:** Während sich der Controller während der Übertragung in den Kopfhörer des Sichtfelds, erhalten sie in der Regel hohe Genauigkeit Positionen, basierend auf visuelle Verfolgung. Beachten Sie, dass ein verschieben Controller, die vorübergehend das Sichtfeld verlässt oder vorübergehend von der Kopfhörer Sensoren verdeckt wird (z. B. durch der Benutzer der anderen Hand) wird weiterhin hoch-Genauigkeit ist für kurze Zeit, basierend auf Trägheit nachverfolgung des Controllers zurück sich selbst.
* **Hohe Genauigkeit (Risiko der verlierenden):** Wenn der Benutzer den Controller während der Übertragung über den Rand der Kopfhörer des Sichtfelds bewegt, den Kopfhörer visuell des Controllers Position kann nicht in Kürze. Die app erkennt, wenn der Controller diese Grenze Blickfeld von angezeigt erreicht hat die **SourceLossRisk** 1.0 zu erreichen. An diesem Punkt können die app Controller-Gesten anhalten, die einem stetigen Strom an sehr hoher Qualität ist erforderlich.
* **Ungefähre Genauigkeit:** Wenn der Controller verloren hat visual nachverfolgung für lange genug, des Controllers Positionen an ungefähren Genauigkeit Positionen gelöscht werden. An diesem Punkt werden Body-Sperre den Controller für den Benutzer, die Position des Benutzers nachverfolgen, wie sie beim Verfügbarmachen immer noch auf "true" des Controllers-Ausrichtung mit der internen Ausrichtung Sensoren, verschieben. Viele apps, die mithilfe von verwaltungscontrollern, zeigen Sie auf, und aktivieren die Elemente der Benutzeroberfläche können als normale Zeit mit einer Genauigkeit von ungefähren im bemerken die Benutzer ausgeführt werden. Apps mit geringeres Routingaufkommen eingabeanforderungen können diese Verringerung von erkennen **hohe** Genauigkeit **ungefähr** Genauigkeit durch Überprüfen der **PositionAccuracy** -Eigenschaft für Beispiel: um dem Benutzer eine großzügigeren Hitbox auf außerhalb des Bildschirms Zielen während dieser Zeit geben.
* **Keine Position:** Während der Controller auf ungefähre Genauigkeit für einen langen Zeitraum ausgeführt werden kann, weiß das System manchmal, dass auch eine Text-locked Position im Moment nicht aussagekräftig ist. Z. B. ein Controller, der nur eingeschaltet wurde möglicherweise nie beobachtet wurde visuell, oder Sie einen Controller, der dann von einer anderen Person übernommen wird ein Benutzer festlegen kann. Zu diesen Zeitpunkten, wird das System keine einer beliebigen Position, an die app bereitgestellt und *TryGetPosition* wird "false" zurückgegeben.

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>Allgemeine Unity-APIs (Input.GetButton/GetAxis)

**Namespace:** *UnityEngine*, *UnityEngine.XR*<br>
**Typen**: *Input*, *XR.InputTracking*

Unity verwendet derzeit der allgemeinen *Input.GetButton/Input.GetAxis* APIs, um die Eingabe für verfügbar zu machen [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) und Windows Mixed Reality, einschließlich praktische und Motion-Controller. Wenn Ihre app diese APIs für die Eingabe verwendet, kann es ganz einfach während der Übertragung Controller über mehrere XR-SDKs, darunter Windows Mixed Reality unterstützen.

### <a name="getting-a-logical-buttons-pressed-state"></a>Abrufen einer logischen Schaltfläche gedrückt

Um die allgemeine Unity Eingabe-APIs verwenden zu können, Sie in der Regel beginnen verknüpfen Sie zuerst die Schaltflächen und verwendet, um den logischen Namen in der [Unity Input Managers](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binden eine Schaltfläche oder ein Achse IDs, die jedem Namen. Anschließend können Sie Code schreiben, die auf diesem logischen Schaltfläche/Achse Namen verweist.

Wechseln Sie zum Beispiel zum Zuordnen des linken Motion-Controllers-Schaltfläche "Trigger" auf die Aktion senden zu **Bearbeiten > Projekteinstellungen > Eingabe** in Unity, und erweitern Sie die Eigenschaften der Abschnitt "übermitteln" unter Achsen. Ändern der **positive Schaltfläche** oder **Alt Positive Schaltfläche** -Eigenschaft in **Joystick Schaltfläche 14**, wie folgt aus:

![Unity InputManager](images/unity-input-manager.png)<br>
*Unity InputManager*

Ihr Skript kann dann das Kontrollkästchen für die senden-Aktion mit *Input.GetButton*:

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
Sie können mehr logische Schaltflächen hinzufügen, durch Ändern der **Größe** Eigenschaft **Achsen**.

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>Eine Taste gedrückt abrufen direkt

Sie können Schaltflächen auch manuell zugreifen, indem Sie ihre vollqualifizierten Namen *Input.GetKey*:

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>Abrufen einer Hand oder während der Übertragung des Controllers Haltung

Sie können Zugriff auf die Position und Drehung des Controllers, mithilfe von *XR. InputTracking*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

Beachten Sie, dass dies des Controllers Ziehpunkt-Haltung (, in denen der Benutzer auf den Controller gespeichert), dies ist hilfreich stellt für das Rendern einer "sword" oder damoklesschwert des Benutzers manuell oder ein Modell für den Controller selbst.

Beachten Sie, dass die Beziehung zwischen dieser Ziehpunkt Haltung und der Zeiger Haltung (, auf die Spitze des Controllers verweist), die auf Controller abweichen kann. Zu diesem Zeitpunkt ist nur den Zugriff auf die Zeiger Haltung des Controllers durch die Eingabe MR-spezifische API, die in den folgenden Abschnitten beschrieben.

## <a name="windows-specific-apis-xrwsainput"></a>Windows-spezifische APIs (XR. WSA. Eingabe)

**Namespace:** *UnityEngine.XR.WSA.Input*<br>
**Typen**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*

Um weitere detaillierte Informationen zu Windows Mixed Reality-Hand-Eingabe (für HoloLens) und der Motion-Controller zu erhalten, können Sie die Windows-spezifische räumliche Eingabe-APIs unter dem *UnityEngine.XR.WSA.Input* Namespace. Dadurch können Sie den Zugriff auf zusätzliche Informationen, z. B. Position Genauigkeit oder der datenquellenart, können Sie die praktische und Controller auseinander zu informieren.

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>Für den Status von Hand und Motion-Controllern abrufen

Sie können Abfragen für diesen Frame des Status der Quelle (manuell oder durch Motion-Controller) für jede Interaktion mithilfe der *GetCurrentReading* Methode.

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

Jede *InteractionSourceState* man Back stellt eine Quelle für die Interaktion zu den aktuellen Zeitpunkt dar. Die *InteractionSourceState* Informationen wie z. B. macht:
* Die [Arten von drückt](motion-controllers.md) auftreten (Select/Menü/verstehen/Touchpad/Ministick)

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* Andere Daten, die spezifisch für Motion-Controller, solche Touchpad und/oder des Ministick XY-Koordinaten und berührt Zustand

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* Die InteractionSourceKind wissen, ob die Quelle einer Hand oder einen Controller während der Übertragung ist

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>Abrufen der Forward-vorhergesagt Rendering ist

* Bei der Interaktion von Quelldaten von Hand und Controller abrufen, sind die ist, erhalten Sie Forward-vorhergesagt ist für den Moment, in der Zeit des Frames Photonen des Benutzers Augen erreichen werden.  Diese ist vorwärts-vorhergesagt werden am besten zum **Rendering** der Controller oder einem vorhandenen Objekt jeden Frame.  Wenn Sie als Ziel das Drücken einer bestimmten oder mit dem Controller freizugeben, ist, die werden möglichst präzise, wenn Sie den historische Ereignis unten beschriebenen APIs verwenden.

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* Sie können auch die Forward-vorhergesagt Head Haltung für diesen aktuellen Frame abrufen.  Wie bei der Quelle Haltung, dies nützlich für **Rendering** einen Cursor, jedoch auf einem angegebenen drücken oder Release möglichst präzise, wenn Sie den historische Ereignis unten beschriebenen APIs verwenden.

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>Behandeln von Ereignissen der Interaktion-Quelle

Um Eingabeereignisse zu behandeln, wie sie mit ihren Daten genau historische Haltung auftreten, können Sie die Interaktion quellenereignisse anstelle einer Abruf behandeln.

Um die Interaktion quellenereignisse behandeln:
* Registrieren Sie sich für eine *InteractionManager* Eingabeereignis. Für jeden Typ von Interaktion-Ereignis, das Sie interessiert sind, müssen Sie abonnieren.

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* Behandeln des Ereignisses an. Nachdem Sie auf ein Ereignis für die Interaktion abonniert haben, erhalten Sie den Rückruf bei Bedarf. In der *SourcePressed* beispielsweise diese werden nach die Quelle erkannt wurde und bevor sie veröffentlicht oder verloren gegangen ist.

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;
       
       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a>Gewusst wie: Behandeln eines Ereignisses zu beenden

Sie müssen beenden Behandeln eines Ereignisses, wenn Sie nicht mehr Interesse am Ereignis sind aus, oder Sie werden zerstört, das Objekt, das das Ereignis abonniert hat. Um das Ereignis zu beenden, kündigen Sie das Ereignis ein.

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>Liste der Ereignisse der Benutzerinteraktion-Quelle

Die mögliche Interaktion Quellereignisse sind:
* *InteractionSourceDetected* (Quelle aktiv)
* *InteractionSourceLost* (inaktiv)
* *InteractionSourcePressed* (Tap, drücken Sie die Schaltfläche oder "Select", wenn)
* *InteractionSourceReleased* (Ende einer Tap, losgelassen wurde, oder Ende von "Select", wenn)
* *InteractionSourceUpdated* (verschiebt oder einen Zustand, der auf andere Weise ändert.)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>Ereignisse für Verlaufsdaten für die Zielgruppenadressierung ist, die am genauesten ein drücken oder ein Release entsprechen

Die zuvor beschriebenen Abrufvorgänge-APIs Geben Sie Ihrer app ist vorwärts-vorhergesagt.  Während die vorhergesagten ist für das Rendern der Controller oder ein virtuelles handheld-Objekt am besten geeignet sind, sind zukünftige ist nicht optimal für die Zielplattform, für die zwei wichtigsten Gründe:
* Bei der Benutzer auf einem Domänencontroller eine Schaltfläche klickt, kann es möglicherweise ungefähr 20 ms Latenz der drahtlose per Bluetooth, bevor das System, drücken Sie die empfängt.
* Dann, wenn Sie eine Vorwärts-vorhergesagt Haltung, es verwenden eine andere 10-20-ms forward Vorhersage angewendet werden würde, wenn der aktuelle Frame Photonen des Benutzers Augen erreichen, wird, die Zeit als Ziel.

Dies bedeutet, dass der Abruf erhalten Sie eine Quelle Haltung oder Head darstellen, d. h. 30-40ms Weiterleiten von, Head und die Hände des Benutzers tatsächlich waren zurück, wenn Sie dem drücken oder Release ausgeführt wurden.  Für HoloLens Hand Eingabe-es gibt zwar keine Verzögerung drahtlosen Übertragung besteht ähnliche Verzögerungen bei der Verarbeitung, drücken Sie die zu erkennen.

Zu genau Ziel basierend auf die ursprüngliche Absicht des Benutzers, für das Drücken einer Hand oder Controller, sollten Sie verwenden, die historische Quelle Haltung oder Head Haltung, *InteractionSourcePressed* oder *InteractionSourceReleased* Eingabeereignis.

Sie können Drücken einer als Ziel oder release mit historischen Haltung Daten des Benutzers Head oder ihre Controller:
* Die Head Haltung zu dem Zeitpunkt eine Geste oder einen Controller beim Drücken aufgetreten ist, kann für verwendet werden **für** um zu bestimmen, was der Benutzer war [gazing](gaze.md) an:

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* Die Quelle Haltung zu dem Zeitpunkt beim Drücken von eines Controllers während der Übertragung aufgetreten ist, kann für verwendet werden **für** um zu bestimmen, was der Benutzer den Controller in gezeigt wurde.  Dies ist der Zustand des Controllers wird, das Drücken das aufgetreten ist.  Wenn Sie den Controller selbst rendern, können Sie anfordern, der Haltung Zeiger anstelle der Ziehpunkt Haltung, vorgesehen für die Zielgruppenadressierung Strahl von was der Benutzer die natürliche Tipps und Tricks, die Controller gerendert berücksichtigt wird:

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a>Beispiel für Ereignis-Handler

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is 
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point. 
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>Allgemeine zusammengesetzten Geste APIs (GestureRecognizer)

**Namespace:** *UnityEngine.XR.WSA.Input*<br>
**Typen**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*

Ihre app kann auch zusammengesetzte Gesten für räumliche Eingabequellen, tippen Sie auf, anhalten, Bearbeitung und Navigation Gesten erkennen. Erkennen Sie diese zusammengesetzten Gesten in beiden [Hände](gestures.md) und [motion Controller](motion-controllers.md) mithilfe der GestureRecognizer.

Jedes Ereignis Bewegung auf die GestureRecognizer bietet die SourceKind für die Eingabe als auch für die Zielgruppenadressierung anhand bestimmter Head Chow zum Zeitpunkt des Ereignisses. Einige Ereignisse bieten zusätzliche Kontextinformationen bestimmte.

Es gibt nur wenige Schritte erforderlich, um eine Stiftbewegungs-Erkennung mit Gesten erfasst:
1. Erstellen einer neuen Stiftbewegungs-Erkennung
2. Geben Sie die Gesten für die Überwachung
3. Abonnieren von Ereignissen für diese Gesten
4. Startet das Sammeln von Gesten

### <a name="create-a-new-gesture-recognizer"></a>Erstellen einer neuen Stiftbewegungs-Erkennung

Verwenden der *GestureRecognizer*, müssen Sie erstellt haben eine *GestureRecognizer*:

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>Geben Sie die Gesten für die Überwachung

Angeben, welche Aktionen, die Sie über interessiert sind *SetRecognizableGestures()*:

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>Abonnieren von Ereignissen für diese Gesten

Abonnieren Sie Ereignisse für die Gesten, die, denen Sie interessieren.

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
>Datennavigation und-Bearbeitung Gesten sind in einer Instanz von sich gegenseitig ausschließende eine *GestureRecognizer*.

### <a name="start-capturing-gestures"></a>Startet das Sammeln von Gesten

Standardmäßig eine *GestureRecognizer* überwacht keine Eingabe bis *StartCapturingGestures()* aufgerufen wird. Es ist möglich, dass eine Geste-Ereignis nach dem generiert möglicherweise *StopCapturingGestures()* wird aufgerufen, wenn die Eingabe vor dem Frame ausgeführt wurde, in denen *StopCapturingGestures()* verarbeitet wurde. Die *GestureRecognizer* speichert, ob es aktiviert oder deaktiviert, während die vorherige-Frames in der die Aktion tatsächlich aufgetreten ist war, und daher sie zuverlässig ist, um zu starten und beenden Geste Überwachung basierend auf des Frames Blicke für.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>Aufzeichnung der Aktionen wird beendet

So beenden Sie die gestenerkennung

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>Entfernen eine stiftbewegungs-Erkennung

Denken Sie daran, die abonnierten Ereignisse vor dem Zerstören abbestellen eine *GestureRecognizer* Objekt.

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>Rendern von der Motion-Controllermodell in Unity

![Während der Übertragung Controllermodell und teleportation](images/motioncontrollertest-teleport-1000px.png)<br>
*Während der Übertragung Controllermodell und teleportation*

Um während der Übertragung von Domänencontrollern in Ihrer app zu rendern, die die physischen Controller entsprechen, Ihre Benutzer enthalten sind, und Erläutern Sie, wie verschiedene-Taste gedrückt werden, können Sie die **MotionController Prefab** in die [Mixed Reality-Toolkit ](https://github.com/Microsoft/MixedRealityToolkit-Unity/).  Diese Prefab lädt das richtige GlTF Modell zur Laufzeit dynamisch aus dem System installierten während der Übertragung Controllertreiber.  Es ist wichtig, diese Modelle dynamisch zu laden, statt Sie möglicherweise importieren manuell im Editor, damit Ihre app physisch genau-3D-Modelle für alle aktuellen und zukünftigen Controller Ihren Benutzern angezeigt werden.

1. Führen Sie die [Einstieg](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) Anweisungen zum Herunterladen von Mixed Reality Toolkit und Ihr Unity-Projekt hinzufügen.
2. Wenn Sie die Kamera mit ersetzt die *MixedRealityCameraParent* prefab als Teil der Schritte zum Einstieg können Sie schon fertig!  Diese Prefab enthält die Motion-Controller-Rendering.  Fügen Sie andernfalls *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* in die Szene im Projekt-Bereich.  Sie sollten hinzufügen, als untergeordnetes Element des beliebige übergeordneten Objekts prefab verwenden, um die Kamera um beim Verschieben der Teleports Benutzer innerhalb der Szene, so, dass die Controller zusammen mit der Benutzer.  Wenn Ihre app keine Teleporting verbunden ist, müssen Sie einfach fügen Sie das Prefab im Stammverzeichnis Ihrer Szene hinzu.

## <a name="throwing-objects"></a>Auslösen von Objekten

Auslösen von Objekten in virtuelle Realität wird ein schwierigeres Problem, und klicken Sie dann Es mag zunächst. Wie bei der am häufigsten physisch basierend Interaktionen, wenn im Spiel fungiert ein unerwartetes Verhalten auslösen, es ist sofort ersichtlich und Immersion unterbrochen. Wir haben damit verbracht, einige nachgedacht tief zum Darstellen eines physisch richtigen auslösenden Verhaltens, und einige Richtlinien, die über Updates unserer Plattform, die wir für Sie freigeben möchten, die aktiviert werden, erhalten haben.

Sie finden ein Beispiel, wie es wird, zum Auslösen von implementieren empfohlen [hier](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage). In diesem Beispiel folgt vier Folgendes:
* **Verwenden des Controllers *Geschwindigkeit* anstatt der Position**. Im November-Update, Windows, wir eine Änderung im Verhalten eingeführt, in der ["Ermitteln" mit Feldern fester Breite Nachverfolgungsstatus](motion-controllers.md#controller-tracking-state). In diesem Zustand weiterhin Geschwindigkeit Informationen zum Controller für gemeldet werden, solange wir, dass es hoher Genauigkeit, der was häufig bei länger glauben ist als die Position des hoher Genauigkeit bleibt.
* **Integrieren der *Winkelgeschwindigkeit* des Controllers**. Diese Logik ist enthalten die `throwing.cs` Datei die `GetThrownObjectVelAngVel` statische Methode, in dem Paket, das weiter oben Bezug genommen:
   1. Wie die Winkelgeschwindigkeit konserviert ist, muss das ausgelöste Objekt die gleichen Winkelgeschwindigkeit, wie er zu dem Zeitpunkt ausgelöst hatte verwalten: `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. Als Mittelpunkt der Masse des-Objekts ausgelöst wird, wahrscheinlich nicht auf den Ursprung des der Ziehpunkt Haltung, es wahrscheinlich eine andere Geschwindigkeit, des Controllers in der Verweisrahmen des Benutzers hat ist. Der Teil des Objekts Geschwindigkeit beigetragen haben, auf diese Weise wird die sofortige tangential Geschwindigkeit der Mittelpunkt der Masse der das Objekt ausgelöst wird, um den Ursprung der Controller. Diese tangential Geschwindigkeit ist das Kreuzprodukt die Winkelgeschwindigkeit des Controllers mit der Vektor, die den Abstand zwischen dem Controller-Ursprung und der Mittelpunkt der-Masse des-Objekts ausgelöst wird.
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. Die gesamte Geschwindigkeit des das ausgelöste Objekt ist die Summe der Geschwindigkeit des Controllers und diese tangential Geschwindigkeit: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **Achten Sie besonders auf die *Zeit* an dem wir die Geschwindigkeit anwenden**. Wenn eine Schaltfläche geklickt wird, dauert es bis zu 20 ms für das Ereignis über Bluetooth an das Betriebssystem Bubbling. Dies bedeutet, dass, wenn der Abruf für eine statusänderung der Controller aus aufgerufen wird, als nicht gedrückt bzw. umgekehrt, Controller Haltung Informationen, die mit ihm Sie erhalten tatsächlich werden vor dieser Änderung am Zustand. Darüber hinaus wird der Controller Haltung angezeigt, die durch unsere API-Abruf vorwärts vorhergesagt, entsprechend einem wahrscheinlich Haltung zum Zeitpunkt der Rahmen angezeigt wird die weitere 20 ms. Klicken Sie dann in der Zukunft sein könnte. Dies eignet sich gut für *Rendering* frei, die Objekte, aber auch unser Problem Zeit für *für* das Objekt wie wir die Kurve für den Moment berechnen veröffentlicht die Benutzer ihre auslösen. Erfreulicherweise haben Sie mit der November-Update, wenn ein Unity-Ereignis wie *InteractionSourcePressed* oder *InteractionSourceReleased* gesendet wird, wird dieser Status umfasst die historischen Haltung Daten aus zurück, wenn die Schaltfläche " wurde tatsächlich gedrückt oder losgelassen.  Um möglichst genaue Controller-Rendering und Controller während der löst Zielgruppenadressierung zu erhalten, müssen Sie ordnungsgemäß Abruf- und Ereignisse, nach Bedarf verwenden:
   * Für **Controller Rendering** jeden Frame, positionieren Sie Ihre app sollte des Controllers *"gameobject"* auf Controllerebene Forward-vorhergesagt darstellen, für den aktuellen Frame Photon Zeit.  Sie erhalten diese Daten von Unity Abrufvorgänge APIs wie *[XR. InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* oder  *[XR. WSA. Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.
   * Für **Controller als Ziel** anhand eines drücken oder die Version, Ihre app sollte Raycast und herabstürzendes basierend auf den historischen Controller Haltung für dieses Ereignis drücken oder Release zu berechnen.  Sie erhalten diese Daten von der ereignisverwaltung der Unity-APIs, z. B.  *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.
* **Verwenden Sie den Ziehpunkt Haltung**. Winkelgeschwindigkeit und Geschwindigkeit sind relativ zu den Ziehpunkt Haltung, kein Zeiger Haltung gemeldet.

Auslösen von weiterhin mit zukünftigen Windows-Updates zu verbessern, und Sie erwarten können, finden Sie weiterführende Informationen hier.

## <a name="accelerate-development-with-mixed-reality-toolkit"></a>Schnellere Entwicklung mit Mixed Reality-Toolkit

Es gibt zwei Beispiel-Szenen zu InputManager und MotionController in Unity. Über diese Szenen erhalten Sie, wie MRTKs InputManager und Zugriff auf Daten behandeln Ereignisse aus der Motion-Controller-Schaltflächen.

- [HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity)
- [HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity)
- [Technische Details README-Datei](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input)

![Eingabebeispiel-Szenen in MRTK](images/MRTK_ExampleScene_Input.png)<br>
*Eingabebeispiel-Szenen in MRTK*

### <a name="automatic-scene-setup"></a>Automatische Szene-setup

Beim Importieren von [MRTK releasepakete Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) oder Klonen Sie das Projekt aus der [GitHub-Repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), Sie sind dabei, ein neues Menü "Mixed Reality-Toolkit" in Unity finden. Klicken Sie im Menü "Mixed Reality Szene-Einstellungen anwenden" wird unter "Konfigurieren" im Menü angezeigt. Wenn Sie darauf klicken, wird er entfernt die Standardkamera und fügt grundlegende Komponenten - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), und [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).

![MRTK-Menü für die Szene-setup](images/MRTK_Input_Menu.png)<br>
*MRTK-Menü für die Szene-setup*

![Automatische Szene Setup in MRTK](images/MRTK_HowTo_Input1.png)<br>
*Automatische Szene Setup in MRTK*

### <a name="mixedrealitycamera-prefab"></a>MixedRealityCamera prefabs

Sie können diese aus dem Projektfenster auch manuell hinzufügen. Sie finden diese Komponenten als prefabs (Vorlagen). Bei der Suche **MixedRealityCamera**, Sie werden zwei verschiedene Kamera prefabs (Vorlagen) angezeigt. Der Unterschied besteht darin, **MixedRealityCamera** ist die Kamera nur prefab dagegen **MixedRealityCameraParent** enthält zusätzliche Komponenten für die immersive Headsets wie z. B. Teleportation, während der Übertragung Controller und Grenze.

![Kamera-Prefabs im MRTK](images/MRTK_HowTo_Input2.png)<br>
*Kamera-Prefabs im MRTK*

**MixedRealtyCamera** HoloLens und immersive Kopfhörer unterstützt. Erkennt den Gerätetyp und die Eigenschaften wie z. B. deaktivieren Flags und Skybox optimiert. Im folgenden können Sie einige nützliche Eigenschaften suchen, die können Sie z. B. benutzerdefinierte Cursor, während der Übertragung Controller-Modellen, anpassen und Floor.

![Eigenschaften für den Controller während der Übertragung, Cursor und Floor](images/MRTK_HowTo_Input3.png)<br>
*Eigenschaften für den Controller während der Übertragung, Cursor und Floor*

## <a name="follow-along-with-tutorials"></a>Nutzen Sie Lernprogramme

Schrittweiser Lernprogramme, mit der eine ausführlichere Beispiele für die Anpassung, sind in der Mixed Reality Academy verfügbar:

- [MR Eingabe 211: Aktion](holograms-211.md)
- [MR Eingabe 213: Motion-Controller](mixed-reality-213.md)

[![MR Eingabe 213 - Motion-controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)<br>
*MR Eingabe 213 - Motion-controller*

## <a name="see-also"></a>Siehe auch

* [Gesten](gestures.md)
* [Motion-Controller](motion-controllers.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [InteractionInputSource.cs in MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/InputSources/InteractionInputSource.cs)
