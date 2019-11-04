---
title: Gesten und Bewegungs Controller in Unity
description: Es gibt zwei wichtige Möglichkeiten, um ihre Blicke in Unity, Handgesten und Bewegungs Controllern zu übernehmen.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Gesten, Bewegungs Controller, Unity, Blick, Eingabe
ms.openlocfilehash: a7ca5a895015ba0458f0f64f1422612e797f5067
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435226"
---
# <a name="gestures-and-motion-controllers-in-unity"></a>Gesten und Bewegungs Controller in Unity

Es gibt zwei wichtige Möglichkeiten, um Ihre [Blicke in Unity](gaze-in-unity.md), [Handgesten](gaze-and-commit.md#composite-gestures) und [Bewegungs Controllern](motion-controllers.md) in hololens und immersiven HMD zu ergreifen. Sie greifen über dieselben APIs in Unity auf die Daten für beide Quellen räumlicher Eingaben zu.

Unity bietet zwei Hauptmethoden für den Zugriff auf räumliche Eingabedaten für Windows Mixed Reality, die gängigen *Input. getbutton/Input. getaxis-* APIs, die über mehrere Unity-XR-sdker hinweg verwendet werden können, sowie eine API für *interaktionmanager/GestureRecognizer* . Windows Mixed Reality, das den vollständigen Satz räumlicher Eingabedaten verfügbar macht.

## <a name="unity-buttonaxis-mapping-table"></a>Unity-Schaltfläche/Achsen Zuordnung (Tabelle)

Die Schaltflächen-und Achsen-IDs in der folgenden Tabelle werden im Unity-Eingabe-Manager für Windows Mixed Reality Motion Controller über die *Eingabe. getbutton/getaxis* -APIs unterstützt, während die Spalte "Windows Mr-spezifisch" auf Eigenschaften verweist, die aus dem *Interaktionsourcestate* -Typ. Jede dieser APIs wird in den folgenden Abschnitten ausführlich beschrieben.

Die Zuordnungen von Schaltflächen/Achsen-IDs für Windows Mixed Reality entsprechen im Allgemeinen den Oculus-Schaltflächen-/Achsen-IDs

Die Zuordnungen von Schaltflächen/Achsen-IDs für Windows Mixed Reality unterscheiden sich auf zwei Arten von den Zuordnungen von openvr:
1. Die Zuordnung verwendet Touchpad-IDs, die sich vom Finger Stick unterscheiden, um Controller mit beiden Fingerabdrücken und Touchpads zu unterstützen.
2. Durch die Zuordnung wird vermieden, dass die Schaltflächen-IDs A und X für die Menü Schaltflächen überladen werden, damit Sie für physische abxy-Schaltflächen verfügbar

<table>
<tr>
<th rowspan="2">Input </th><th colspan="2"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Allgemeine Unity-APIs</a><br />(Input. getbutton/getaxis) </th><th rowspan="2"><a href="gestures-and-motion-controllers-in-unity.md#">Windows-spezifische Eingabe-API</a><br />XR. WSA. Der</th>
</tr><tr>
<th> Links </th><th> Rechte Seite</th>
</tr><tr>
<td> Select-Taste gedrückt </td><td> Achse 9 = 1,0 </td><td> Achse 10 = 1,0 </td><td> selectpressed</td>
</tr><tr>
<td> Auswählen des analogen Auslöse Werts </td><td> Achse 9 </td><td> Achse 10 </td><td> selectpressedamount</td>
</tr><tr>
<td> Select-Taste teilweise gedrückt </td><td> Schaltfläche 14 <i>(Gamepad-Kompatibilität)</i> </td><td> Schaltfläche 15 <i>(Gamepad-Kompatibilität)</i> </td><td> selectpressedamount &gt; 0,0</td>
</tr><tr>
<td> Menü Schaltfläche gedrückt </td><td> Schaltfläche 6 * </td><td> Schaltfläche 7 * </td><td> menupressed</td>
</tr><tr>
<td> Zieh Schaltfläche gedrückt </td><td> Achse 11 = 1,0 (keine analogen Werte)<br />Schaltfläche 4 <i>(Gamepad-Kompatibilität)</i> </td><td> Achse 12 = 1,0 (keine analogen Werte)<br />Schaltfläche 5 <i>(Gamepad-Kompatibilität)</i> </td><td> Schna</td>
</tr><tr>
<td> Thumbstick X <i>(Links:-1,0, right: 1,0)</i> </td><td> Achse 1 </td><td> Achse 4 </td><td> thumbstickposition. x</td>
</tr><tr>
<td> Thumbstick Y <i>(oben:-1,0, unten: 1,0)</i> </td><td> Achse 2 </td><td> Achse 5 </td><td> thumbstickposition. y</td>
</tr><tr>
<td> Thumbstick gedrückt </td><td> Schaltfläche 8 </td><td> Schaltfläche 9 </td><td> thumbstickpressed</td>
</tr><tr>
<td> Touchpad X <i>(Links:-1,0, right: 1,0)</i> </td><td> Achse 17 * </td><td> Achse 19 * </td><td> touchpadposition. x</td>
</tr><tr>
<td> Touchpad Y <i>(oben:-1,0, unten: 1,0)</i> </td><td> Achse 18 * </td><td> Achse 20 * </td><td> touchpadposition. y</td>
</tr><tr>
<td> Touchpad berührt </td><td> Schaltfläche 18 * </td><td> Schaltfläche 19 * </td><td> touchpadtouched</td>
</tr><tr>
<td> Touchpad gedrückt </td><td> Schaltfläche 16 * </td><td> Schaltfläche 17 * </td><td> touchpadpressed</td>
</tr><tr>
<td> 6DOF-Zieh Punkt Pose oder Zeiger Pose </td><td colspan="2"> <i></i> Nur Ziehpunkt: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. Inputtracking. getlocalposition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. Input Tracking. getlocalrotation</a></td><td> Pass <i>-</i> oder <i>Zeiger</i> als Argument: SourceState. sourcepose. trygetposition<br />SourceState. sourcepose. trygetrotation<br /></td>
</tr><tr>
<td> Nach verfolgungsstatus </td><td colspan="2"> Die <i>Positionsgenauigkeit und das Risiko von Quell Verlusten sind nur über eine bestimmte API verfügbar</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">SourceState. sourcepose. positionaccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">SourceState. Properties. sourcelossrisk</a></td>
</tr>
</table>

>[!NOTE]
>Diese Schaltflächen-/Achsen-IDs unterscheiden sich von den IDs, die Unity für openvr verwendet, aufgrund von Konflikten in den von Gamepads, oculus Touchscreen und openvr verwendeten Zuordnungen.

## <a name="grip-pose-vs-pointing-pose"></a>Ziehpunkt im Vergleich zu Zeige darstellen

Windows Mixed Reality unterstützt Bewegungs Controller in einer Vielzahl von Formfaktoren, wobei sich der Entwurf des Controllers in seiner Beziehung zwischen der Handposition des Benutzers und der natürlichen Vorwärtsrichtung unterscheidet, die apps beim Rendern der ern.

Um diese Controller besser darzustellen, gibt es zwei Arten von Posen, die Sie für jede Interaktions Quelle untersuchen können, die Ziehpunkt- **und die** **Zeiger**Darstellung. Sowohl die Ziehpunkt-als auch die zeigerpose-Koordinaten werden von allen Unity-APIs in globalen Unity-Weltkoordinaten ausgedrückt.

### <a name="grip-pose"></a>Ziehpunkt darstellen

Die Ziehpunkt- **Pose** stellt die Position der Palme einer Hand dar, die von einem hololens erkannt wird, oder die Palme, die einen Bewegungs Controller enthält.

Bei immersiven Headsets eignet sich die Zieh Punkt Darstellung am besten zum Rendering **der Benutzer Hand** oder **eines Objekts, das in der Hand des Benutzers gehalten**wird, z. b. ein Schwert oder eine Waffe. Die Zieh Punkt Darstellung wird auch bei der Visualisierung eines Bewegungs Controllers verwendet, da das **renderbare Modell** , das von Windows für einen Motion-Controller bereitgestellt wird, die Zieh Punkt Darstellung als Ursprung und Mittelpunkt der Drehung verwendet.

Die Ziehpunkt-Pose wird wie folgt definiert:
* Die Zieh **Punktposition**: der Palmen Schwerpunkt bei der natürlichen Aufbewahrung des Controllers, nach links oder rechts, um die Position im Ziehpunkt zu zentrieren. Auf dem Windows Mixed Reality Motion Controller richtet sich diese Position im Allgemeinen nach der Schaltfläche "verstehen".
* Die **Rechte Achse**der Ziehpunkt Ausrichtung: Wenn Sie Ihre Hand vollständig geöffnet haben, um eine flache 5-Finger-Darstellung zu bilden, ist das Strahl-Ray, das normal ist (vorwärts von links nach links, rückwärts von rechter Palme).
* Die **Forward-Achse**der Ziehpunkt Ausrichtung: Wenn Sie die Hand teilweise schließen (wie beim Halten des Controllers), wird der Strahl, der durch das durch ihre nicht-Thumb-Finger formatierte Rohr auf "Vorwärts" zeigt.
* Die **aufwärts Achse**der Ziehpunkt Ausrichtung: die aufwärts Achse, die durch die Rechte-und vorwärts Definitionen impliziert wird.

Sie können auf die Ziehpunkt-Pose über die Anbieter übergreifende Eingabe-API von Unity (XR) zugreifen *[. Inputtracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). Getlocalposition/Rotation*) oder über die Windows-spezifische API (*SourceState. sourcepose. trygetposition/Rotation*), die die Daten für den **Zieh Knoten** anfordert.

### <a name="pointer-pose"></a>Zeiger Pose

Die **Zeiger** Darstellung stellt die Spitze des Controllers dar, der vorwärts zeigt.

Die vom System bereitgestellte Zeiger Darstellung eignet sich am besten für raycast, wenn Sie **das Controller Modell selbst Rendern**. Wenn Sie ein anderes virtuelles Objekt anstelle des Controllers (z. b. eine virtuelle Pistole) rendern, sollten Sie auf einen Strahl zeigen, der für dieses virtuelle Objekt am natürlichsten ist, z. b. ein Strahl, der entlang des fassers des App-defined Gun-Modells verläuft. Da Benutzer das virtuelle Objekt und nicht den physischen Controller sehen können, ist das verweisen mit dem virtuellen Objekt für diejenigen, die Ihre APP verwenden, wahrscheinlich natürlicher.

Derzeit ist die Zeiger Pose in Unity nur über die Windows Mr-spezifische API, *SourceState. sourcepose. trygetposition/Rotation*verfügbar, wobei *interaktionsourcenode. Pointer* als Argument übergeben wird.

## <a name="controller-tracking-state"></a>Controller nach verfolgungsstatus

Wie bei den Headsets ist für Windows Mixed Reality Motion Controller das Einrichten externer nach Verfolgungs Sensoren nicht erforderlich. Stattdessen werden die Controller von Sensoren im Headset selbst nachverfolgt.

Wenn der Benutzer die Controller aus dem Feld des endfelds der Ansicht verschiebt, werden in den meisten Fällen die Controller Positionen von Windows weiter abgeleitet und der APP bereitgestellt. Wenn die visuelle Überwachung für den Controller lange genug verloren gegangen ist, werden die Positionen des Controllers auf Positionen mit ungefähren Genauigkeit abgelegt.

An diesem Punkt sperrt das System den Controller für den Benutzer, wobei die Position des Benutzers nachverfolgt wird, während er sich bewegt, während er weiterhin die echte Ausrichtung des Controllers mithilfe der internen Ausrichtungs Sensoren verfügbar macht. Viele apps, die Controller verwenden, um auf Benutzeroberflächen Elemente zu verweisen und diese zu aktivieren, können normal funktionieren, ohne dass der Benutzer das merkt.

Die beste Möglichkeit, dies zu erreichen, besteht darin, es selbst auszuprobieren. Sehen Sie sich dieses Video mit Beispielen für den immersiven Inhalt an, der mit Motion-Controllern über verschiedene Überwachungs Zustände hinweg funktioniert:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a>Grund für die explizite Nachverfolgung des Zustands

Apps, die Positionen basierend auf dem nach verfolgungsstatus unterschiedlich behandeln möchten, können weiter gehen und die Eigenschaften des Controller Zustands überprüfen, z. b. *sourcelossrisk* und *positionaccuracy*:

<table>
<tr>
<th> Nach verfolgungsstatus </th><th> Sourcelossrisk </th><th> Positionsgenauigkeit </th><th> Trygetposition</th>
</tr><tr>
<td> <b>Hohe Genauigkeit</b> </td><td style="background-color: green; color: white"> &lt; 1,0 </td><td style="background-color: green; color: white"> Hoch </td><td style="background-color: green; color: white"> Wahr</td>
</tr><tr>
<td> <b>Hohe Genauigkeit (Risiko des Verlusts)</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: green; color: white"> Hoch </td><td style="background-color: green; color: white"> Wahr</td>
</tr><tr>
<td> <b>Ungefähre Genauigkeit</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Ungefähr </td><td style="background-color: green; color: white"> Wahr</td>
</tr><tr>
<td> <b>Keine Position</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Ungefähr </td><td style="background-color: orange"> Falsch</td>
</tr>
</table>

Diese Motion Controller-Überwachungs Zustände werden wie folgt definiert:
* **Hohe Genauigkeit:** Während sich der Motion-Controller in der Ansicht des Dashboards befindet, stellt er im Allgemeinen hohe Genauigkeits Positionen auf der Grundlage der visuellen Nachverfolgung bereit. Beachten Sie, dass ein beweglicher Controller, der das Sichtfeld vorübergehend verlässt oder vorübergehend von den Headset-Sensoren (z. b. durch die andere Seite des Benutzers) verdeckt wird, weiterhin hohe Genauigkeit für kurze Zeit zurückgibt, basierend auf der Trägheits Verfolgung des Controllers. etabliert.
* **Hohe Genauigkeit (Risiko des Verlusts):** Wenn der Benutzer den Bewegungs Controller über den Rand des Felds der Ansicht bewegt, kann das Headset die Position des Controllers in Kürze nicht visuell nachverfolgen. Die APP weiß, wann der Controller diese FOV-Grenze erreicht hat, indem er den **sourcelossrisk** -REACH-1,0 sieht. An diesem Punkt kann die APP die Controller Gesten anhalten, die einen stabilen Stream von sehr hochwertigen Posen erfordern.
* **Ungefähre Genauigkeit:** Wenn die visuelle Überwachung für den Controller lange genug verloren gegangen ist, werden die Positionen des Controllers auf Positionen mit ungefähren Genauigkeit abgelegt. An diesem Punkt sperrt das System den Controller für den Benutzer, wobei die Position des Benutzers nachverfolgt wird, während er sich bewegt, während er weiterhin die echte Ausrichtung des Controllers mithilfe der internen Ausrichtungs Sensoren verfügbar macht. Viele apps, die Controller verwenden, um auf Benutzeroberflächen Elemente zu verweisen und diese zu aktivieren, können so normal agieren, dass Sie in der ungefähren Genauigkeit nicht bemerkt werden Bei apps mit schwereren Eingabe Anforderungen ist es möglicherweise sinnvoll, diesen Löschvorgang von **hoher** Genauigkeit zur **ungefähren** Genauigkeit zu verstehen, indem die **positionaccuracy** -Eigenschaft überprüft wird Während dieser Zeit.
* **Keine Position:** Obwohl der Controller für einen längeren Zeitraum mit der ungefähren Genauigkeit arbeiten kann, weiß das System manchmal, dass auch eine vom Text gesperrte Position im Moment nicht aussagekräftig ist. Beispielsweise kann ein Controller, der gerade eingeschaltet war, nie visuell beobachtet werden, oder ein Benutzer kann einen Controller ablegen, der von einer anderen Person abgerufen wird. Zu diesen Zeitpunkten stellt das System keine Position für die APP bereit, und *trygetposition* gibt false zurück.

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>Allgemeine Unity-APIs (Input. getbutton/getaxis)

**Namespace:** *unityengine*, *unityengine. XR*<br>
**Typen**: *Input*, *XR. Inputtracking*

Unity verwendet derzeit die allgemeinen *Input. getbutton/Input. getaxis-* APIs, um Eingaben für [das Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [das openvr SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) und Windows Mixed Reality, einschließlich der Hands-und Motion-Controller, verfügbar zu machen. Wenn Ihre APP diese APIs für die Eingabe verwendet, kann Sie Bewegungs Controller über mehrere XR-sdche hinweg unterstützen, einschließlich Windows Mixed Reality.

### <a name="getting-a-logical-buttons-pressed-state"></a>Der gedrückte Zustand einer logischen Schaltfläche wird erhalten.

Wenn Sie die allgemeinen Unity-Eingabe-APIs verwenden möchten, beginnen Sie in der Regel mit dem Verknüpfen von Schaltflächen und Achsen mit logischen Namen im [Unity-Eingabe-Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), und binden Sie eine Schaltfläche oder eine Achsen-ID an jeden Namen Anschließend können Sie Code schreiben, der auf den Namen der logischen Schaltfläche/Achse verweist.

Um z. b. die triggerschaltfläche des linken Bewegungs Controllers der Aktion senden zuzuordnen, wechseln Sie zu **Edit > Project Settings > Input** in Unity, und erweitern Sie die Eigenschaften des Abschnitts übermitteln unter Achsen. Ändern Sie die Schaltfläche " **pokschaltfläche** " oder die positiv Schaltfläche "alt", um die **Schalt** **Fläche "**

der InputManager von Unity ![](images/unity-input-manager.png)<br>
*Unity-InputManager*

Das Skript kann dann mithilfe von " *Input. getbutton*" die Aktion "Senden" überprüfen:

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
Sie können weitere logische Schaltflächen hinzufügen, indem Sie die **size** -Eigenschaft unter **Achsen**ändern.

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>Direktes drücken des gedrückten Zustands einer physischen Schaltfläche

Sie können mithilfe von *Input. GetKey*auch manuell über den voll qualifizierten Namen auf Schaltflächen zugreifen:

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>Die Pose eines Hand-oder Bewegungs Controllers

Sie können auf die Position und Drehung des Controllers mithilfe von *XR zugreifen. Inputtracking*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

Beachten Sie, dass dies die Zieh Punktposition des Controllers darstellt (in der der Benutzer den Controller hält). Dies ist nützlich, um ein Schwert oder eine Waffe in der Hand des Benutzers oder ein Modell des Controllers selbst zu rendern.

Beachten Sie, dass die Beziehung zwischen diesem Ziehpunkt und der Zeiger Pose (bei der die Spitze des Controllers zeigt) sich zwischen Controllern unterscheiden kann. Zurzeit ist der Zugriff auf die Zeiger-Pose des Controllers nur über die in den folgenden Abschnitten beschriebene Mr-spezifische Eingabe-API möglich.

## <a name="windows-specific-apis-xrwsainput"></a>Windows-spezifische APIs (XR. WSA. Der

**Namespace:** *unityengine. XR. WSA. Input*<br>
**Typen**: *interaktionsmanager*, *interaktionsourcestate*, *interaktionsource*, *interaktionsourceproperties*, *interaktionsourcekind*, *interaktionsourcelokation*

Um ausführlichere Informationen zu Windows Mixed Reality-Hand Eingaben (für hololens) und Bewegungs Controller zu erhalten, können Sie die Windows-spezifischen räumlichen Eingabe-APIs im Namespace *unityengine. XR. WSA. Input* verwenden. Auf diese Weise können Sie auf zusätzliche Informationen zugreifen, wie z. b. Die Positionsgenauigkeit oder die quellart, sodass Sie die Hände und Controller voneinander trennen können.

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>Abrufen des Zustands von Händen und Bewegungs Controllern

Sie können den Status dieses Frames für jede Interaktions Quelle (Hand-oder Bewegungs Controller) mithilfe der *getcurrentreading* -Methode abrufen.

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

Jedes *interaktionsourcestate* , das Sie zurückerhalten, stellt eine Interaktions Quelle zum aktuellen Zeitpunkt dar. Das *interaktionsourcestate* macht Informationen wie z. b.:
* Welche [Arten von Druck](motion-controllers.md) vorgehungen werden auftreten (Select/Menu/grasp/Touchpad/Thumbstick)

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* Andere Daten, die für Bewegungs Controller spezifisch sind, z. b. die XY-Koordinaten des Touchpads und/oder Finger Ansichts Status

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* Interaktionsourcekind, um zu wissen, ob es sich bei der Quelle um einen Hand-oder Bewegungs Controller handelt

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>Abrufen von vorwärts vorhergesagten Renderingvorgängen

* Beim Abrufen von Interaktions Quelldaten von Hand und Controllern sind die von Ihnen abzurufenden Datenquellen für den Zeitpunkt, zu dem die Daten des Bilds den Augen des Benutzers erreichen, von vorne vorhergesagte Posen.  Diese vorwärts Gesagten Posen werden am besten zum **Rendern** des Controllers oder eines gehaltenen Objekts in jedem Frame verwendet.  Wenn Sie ein bestimmtes Press-oder-Release mit dem Controller als Ziel verwenden, wird dies am genauesten sein, wenn Sie die nachstehend beschriebenen Vergangenheits Ereignis-APIs verwenden.

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* Sie können auch die vorwärts Gesagte Kopfzeile für diesen aktuellen Frame erhalten.  Wie bei der Quell Darstellung ist dies für das **Rendern** eines Cursors nützlich, obwohl das Ziel einer bestimmten Presse oder Freigabe am genauesten ist, wenn Sie die unten beschriebenen Vergangenheits Ereignis-APIs verwenden.

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>Behandeln von Interaktions Quell Ereignissen

Um Eingabeereignisse zu behandeln, wie Sie mit Ihren exakten Vergangenheits Daten auftreten, können Sie Interaktions Quell Ereignisse behandeln, anstatt Sie abzufragen.

So behandeln Sie Interaktions Quell Ereignisse:
* Registrieren Sie sich für ein *interaktionmanager* -Eingabe Ereignis. Für jede Art von Interaktions Ereignis, für das Sie sich interessieren, müssen Sie es abonnieren.

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* Behandeln Sie das-Ereignis. Wenn Sie ein Interaktions Ereignis abonniert haben, erhalten Sie gegebenenfalls den Rückruf. Im Beispiel " *sourcepressed* " ist dies der Fall, nachdem die Quelle erkannt wurde und bevor Sie freigegeben oder verloren geht.

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

### <a name="how-to-stop-handling-an-event"></a>Beenden der Behandlung eines Ereignisses

Sie müssen die Verarbeitung eines Ereignisses beenden, wenn Sie nicht mehr an dem Ereignis interessiert sind oder das Objekt zerstören, das das Ereignis abonniert hat. Wenn Sie die Verarbeitung des Ereignisses beenden möchten, kündigen Sie das Ereignis an.

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>Liste der Interaktions Quell Ereignisse

Die folgenden Interaktions Quell Ereignisse sind verfügbar:
* *Interaktionsourceerkannt* (Quelle wird aktiv)
* *Interaktionsourcelost* (wird inaktiv)
* *Interaktionsourcepressed* (tippen, drücken der Schaltfläche oder "auswählen")
* *Interaktionsourcereleasing* (Ende einer Tap-Schaltfläche, oder Ende der "Select"-Taste)
* *Interaktionsourceupveraltet* (verschieben oder anderweitig ändern eines Zustands)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>Ereignisse für Vergangenheits Ziele, die mit einem Press oder Release am genauesten zu vergleichen sind

Die zuvor beschriebenen Abruf-APIs machen Ihre APP-vorhergesagte Posen aus.  Obwohl die vorhergesagten Posen am besten zum Rendern des Controllers oder eines virtuellen Hand Held Objekts geeignet sind, sind zukünftige Posen nicht optimal für das Ziel, aus zwei Hauptgründen:
* Wenn der Benutzer eine Schaltfläche auf einem Controller drückt, kann es ungefähr 20 ms drahtlose Latenz über Bluetooth geben, bevor das System den Druck erhält.
* Wenn Sie dann eine vorwärts Gesagte Pose verwenden, gibt es eine weitere 10-20 MS der Forward-Vorhersage, auf die die Zeit angewendet wird, in der die Daten des aktuellen Frames die Augen des Benutzers erreichen.

Dies bedeutet, dass bei der Abfrage eine Quell Pose oder eine Kopfzeile angezeigt wird, die 30 bis 40 ms vorwärts ist, von wo aus die Kopfzeile des Benutzers und die Hände wieder zurück waren, als die Presse oder das Release aufgetreten ist.  Bei der Eingabe von hololens-Hand Eingaben kommt es zu einer ähnlichen Verarbeitungs Verzögerung, um den Press zu erkennen.

Um basierend auf der ursprünglichen Absicht des Benutzers für eine Hand oder einen Controller eine genaue Zielsetzung zu erreichen, sollten Sie die historische Quell Pose oder die Kopfzeile aus dem *interaktionsourcepressed* -oder *interaktionsourcereleasing* -Eingabe Ereignis verwenden.

Sie können eine Presse oder eine Freigabe mit Verlaufs Daten des Benutzers oder des Controllers als Ziel haben:
* Die Kopfzeile zu dem Zeitpunkt, an dem eine Geste oder eine Controller Bewegung aufgetreten ist, die für die **Ziel** Bestimmung verwendet werden kann, um zu bestimmen, was der [Benutzer untersucht hat:](gaze-and-commit.md)

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

* Die Quell Pose zu dem Zeitpunkt, zu dem eine Bewegung des Bewegungs Controllers stattgefunden hat. diese kann verwendet werden, **um zu bestimmen** , auf welche Weise der Benutzer den Controller verwiesen hat.  Dabei handelt es sich um den Zustand des Controllers, der den Druck erhalten hat.  Wenn Sie den Controller selbst rendern, können Sie die Zeiger Darstellung anstelle der Ziehpunkt-Pose anfordern, um das Ziel-Ray von dem zu überprüfen, was der Benutzer für den natürlichen Tipp des gerenderten Controllers in Erwägung zieht:

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

### <a name="event-handlers-example"></a>Beispiel für Ereignishandler

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

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>APIs für zusammengesetzte Gesten auf hoher Ebene (GestureRecognizer)

**Namespace:** *unityengine. XR. WSA. Input*<br>
**Typen**: *GestureRecognizer*, *gesturesettings*, *interaktionsourcekind*

Ihre APP kann auch zusammengesetzte Gesten auf höherer Ebene für räumliche Eingabe Quellen, Tap-, Halt-, Manipulations-und Navigations Gesten erkennen. Mit dem GestureRecognizer können Sie diese zusammengesetzten Gesten sowohl in [Hand](gaze-and-commit.md#composite-gestures) -als auch in [Bewegungs Controllern](motion-controllers.md) erkennen.

Jedes Gesten Ereignis für den GestureRecognizer stellt sowohl sourcekind für die Eingabe als auch den Ziel-Head-Strahl zum Zeitpunkt des Ereignisses bereit. Einige Ereignisse bieten zusätzliche kontextspezifische Informationen.

Es sind nur wenige Schritte erforderlich, um Gesten mithilfe einer Gestenerkennung zu erfassen:
1. Erstellen einer neuen Gestenerkennung
2. Legen Sie fest, welche Gesten überwacht werden sollen.
3. Ereignisse für diese Gesten abonnieren
4. Erfassungs Gesten starten

### <a name="create-a-new-gesture-recognizer"></a>Erstellen einer neuen Gestenerkennung

Wenn Sie den *GestureRecognizer*verwenden möchten, müssen Sie einen *GestureRecognizer*erstellt haben:

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>Legen Sie fest, welche Gesten überwacht werden sollen.

Geben Sie an, welche Gesten Sie über "" mit "" auf "" festgelegt haben *()* :

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>Ereignisse für diese Gesten abonnieren

Abonnieren Sie Ereignisse für die Gesten, an denen Sie interessiert sind.

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
>Navigations-und Manipulations Gesten schließen sich gegenseitig für eine Instanz eines *GestureRecognizer*aus.

### <a name="start-capturing-gestures"></a>Erfassungs Gesten starten

Standardmäßig überwacht ein *GestureRecognizer* die Eingabe erst, wenn *startcapturinggesten ()* aufgerufen wird. Möglicherweise wird ein Gesten Ereignis generiert, nachdem *stopcapturinggesten ()* aufgerufen wurde, wenn Eingaben vor dem Frame durchgeführt wurden, in dem *stopcapturinggesten ()* verarbeitet wurde. Der *GestureRecognizer* weiß, ob er während des previou-Frames, in dem die Geste tatsächlich aufgetreten ist, ein-oder ausgeschaltet war, und daher ist es zuverlässig, die Gesten Überwachung auf der Grundlage der Anzeige Ziele dieses Frames zu starten und zu beenden.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>Erfassungs Gesten nicht mehr

So verhindern Sie die Gestenerkennung:

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>Entfernen einer Gestenerkennung

Denken Sie daran, abonnierte Ereignisse abzubestellen, bevor Sie ein *GestureRecognizer* -Objekt zerstören.

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>Rendern des Motion Controller-Modells in Unity

![Motion Controller Modell und Teleportations](images/motioncontrollertest-teleport-1000px.png)<br>
*Motion Controller-Modell und-teleportierung*

Zum Rendering von Bewegungs Controllern in Ihrer APP, die den physischen Controllern entsprechen, die die Benutzer als verschiedene Schaltflächen verwenden, die Sie verwenden, können Sie die **vorfab von "mutioncontroller** " im [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/)verwenden.  Dieser Prefab lädt das korrekte gltf-Modell zur Laufzeit dynamisch aus dem installierten Motion Controller-Treiber des Systems.  Es ist wichtig, dass diese Modelle dynamisch geladen werden, anstatt Sie manuell in den Editor zu importieren, damit Ihre APP physisch genaue 3D-Modelle für alle aktuellen und zukünftigen Controller anzeigt, die Ihre Benutzer möglicherweise haben.

1. Befolgen Sie [die Anweisungen für die ersten](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) Schritte, um das Mixed Reality Toolkit herunterzuladen und es Ihrem Unity-Projekt hinzuzufügen.
2. Wenn Sie Ihre Kamera durch das *mixedrealitycameraparent* -präfab im Rahmen der Schritte für die ersten Schritte ersetzt haben, können Sie es tun!  Dieses präfab umfasst das Rendern von Bewegungs Controllern.  Andernfalls fügen Sie *Assets/holotoolkit/Input/Prefabs/mutioncontrollers. Prefab* aus dem Projektbereich in die Szene ein.  Sie sollten diese Prefab als untergeordnetes Element eines beliebigen übergeordneten Objekts hinzufügen, das Sie verwenden, um die Kamera zu bewegen, wenn der Benutzer in der Szene Teleports verwendet, sodass die Controller mit dem Benutzer zusammenkommen.  Wenn Ihre APP keine teleportierung umfasst, fügen Sie einfach die vorfab im Stammverzeichnis Ihrer Szene hinzu.

## <a name="throwing-objects"></a>Auslösen von Objekten

Das Auslösen von Objekten in Virtual Reality ist ein schwierigeres Problem, das möglicherweise zuerst erscheint. Wie bei den meisten physisch basierenden Interaktionen verhält es sich beim Auslösen im Spiel auf unerwartete Weise, es ist sofort offensichtlich und unterbricht das eintauchen. Wir haben einige Zeit damit verbracht, ein physisch korrektes auslösverhalten darzustellen, und haben einige Richtlinien, die über Updates auf unserer Plattform aktiviert wurden, für Sie freigeben möchten.

Ein Beispiel für die Implementierung von "throw" finden Sie [hier](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage). Dieses Beispiel befolgt diese vier Richtlinien:
* **Verwenden Sie die *Geschwindigkeit* des Controllers anstelle der Position**. Im November-Update für Windows haben wir eine Änderung des Verhaltens eingeführt, wenn der [ungefähre Status der Positionsüberwachung ("ungefähre"](motion-controllers.md#controller-tracking-state)) ist. In diesem Zustand werden Velocity-Informationen über den Controller weiterhin angezeigt, solange wir glauben, dass es sich um eine hohe Genauigkeit handelt, die häufig länger ist als die Position mit hoher Genauigkeit.
* **Integrieren Sie die *Winkelgeschwindigkeit* des Controllers**. Diese Logik ist alle in der `throwing.cs`-Datei in der `GetThrownObjectVelAngVel` statischen Methode in dem oben verknüpften Paket enthalten:
   1. Wenn die Angular-Geschwindigkeit beibehalten wird, muss das ausgelöste Objekt dieselbe Angular-Geschwindigkeit wie im Moment der throw-Ausnahme beibehalten: `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. Da sich der Mittelpunkt der Masse des ausgelösten Objekts wahrscheinlich nicht am Ursprung der Ziehpunkt-Pose befindet, weist er wahrscheinlich eine andere Geschwindigkeit auf als der Controller im Verweis auf den Benutzer. Der Teil der auf diese Weise beigetragenen Geschwindigkeit des Objekts ist die sofortige tangential Geschwindigkeit des Mittelpunkts der Masse des ausgelösten Objekts um den Controller Ursprung. Diese tangential-Geschwindigkeit ist das Kreuz Produkt der Angular-Geschwindigkeit des Controllers mit dem Vektor, der den Abstand zwischen dem Controller Ursprung und dem Mittelpunkt der Masse des ausgelösten Objekts darstellt.
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. Die Gesamtgeschwindigkeit des ausgelösten Objekts entspricht daher der Summe der Geschwindigkeit des Controllers und der tangential Geschwindigkeit: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* Achten **Sie genau auf die *Zeit* , zu der wir die Geschwindigkeit anwenden**. Wenn eine Schaltfläche gedrückt wird, kann es bis zu 20 ms dauern, bis das Ereignis durch Bluetooth bis zum Betriebssystem hochskalieren kann. Dies bedeutet Folgendes: Wenn Sie eine Änderung des Controller Zustands von "gedrückt" in "nicht gedrückt" oder umgekehrt abrufen, werden die Informationen, die Sie mit dem Controller erhalten, tatsächlich vor dieser Zustandsänderung angezeigt. Außerdem wird die von unserer Abruf-API dargestellte Controller Darstellung vorhergesagt, um eine wahrscheinliche Darstellung zum Zeitpunkt der Anzeige des Frames widerzuspiegeln, der in der Zukunft mehr als 20 ms betragen kann. Dies eignet sich gut für das *Rendern* von gehaltenen Objekten, stellt jedoch unser Zeitproblem für das *Ziel des Objekts* dar Wenn beim November-Update ein Unity-Ereignis wie *interaktionsourcepressed* oder *interaktionsourcereleasing* gesendet wird, enthält der Zustand die Vergangenheits Daten von hinten, wenn die Schaltfläche tatsächlich gedrückt oder freigegeben wurde.  Um das präzisere Controller Rendering und die Zielplattform für das Ausführen von Triggeroptionen zu erhalten, müssen Sie nach Bedarf Abruf-und Ereignis Ereignisse ordnungsgemäß verwenden:
   * Für den Controller, der die einzelnen Frames **rendert** , sollte Ihre APP das *gameobject* des Controllers an der vorwärts Gesagten Controller Darstellung für die Photon-Zeit des aktuellen Frames positionieren.  Sie erhalten diese Daten von Unity-Abruf-APIs wie *[XR. Inputtracking. getlocalposition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* oder *[XR. WSA. Input. interaktionmanager. getcurrentreading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* .
   * Für den Controller, der auf eine Presse oder ein Release **abzielt** , sollte Ihre APP auf der Grundlage der Verlaufs Controller-Pose für das Press-oder releaseereignis auf der Grundlage der Verlaufs Controller-  Sie erhalten diese Daten aus den Unity-Ereignis-APIs, wie z. b. *[interaktionmanager. interaktionsourcepressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* .
* **Verwenden Sie die**Ziehpunkt-Pose. Winkelgeschwindigkeit und-Geschwindigkeit werden relativ zur Zieh Punkt Pose, nicht zum Darstellen von Zeigern, angezeigt.

Das auslösen wird mit zukünftigen Windows-Updates weiter verbessern, und Sie können davon ausgehen, dass Sie hier weitere Informationen finden.

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a>Gesten-und Bewegungs Controller in mrtk v2

Sie können über den Eingabe-Manager auf Gesten-und Bewegungs Controller zugreifen. 
* [Geste in mrtk v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [Motion Controller in mrtk v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a>Befolgen Sie die Tutorials

Schritt-für-Schritt-Tutorials mit ausführlicheren Anpassungs Beispielen sind in der Mixed Reality Academy verfügbar:

- [Mr-Eingabe 211: Geste](holograms-211.md)
- [Mr-Eingabe 213: Motion-Controller](mixed-reality-213.md)

[![Mr-Eingabe 213-Motion Controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)<br>
*Mr-Eingabe 213-Motion Controller*

## <a name="see-also"></a>Weitere Informationen:

* [Anvisieren mit dem Kopf und Ausführen](gaze-and-commit.md)
* [Motion-Controller](motion-controllers.md)


