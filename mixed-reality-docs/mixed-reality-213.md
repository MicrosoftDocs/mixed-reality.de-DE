---
title: Mr-Eingabe 213
description: Befolgen Sie dieses Lernprogramm zum Programmieren mit Unity, Visual Studio und immersiven Headsets, um die Details von Bewegungs Controllern kennenzulernen.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, immersive, Motion Controller, Academy, Tutorial
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516388"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.

<br>

# <a name="mr-input-213-motion-controllers"></a>Mr-Eingabe 213: Motion-Controller

Bewegungs Controller in der Mixed Reality-Welt fügen eine weitere Interaktivität hinzu. Mit [Motion-Controllern](motion-controllers.md)können wir direkt mit Objekten auf natürlichere Weise interagieren, ähnlich wie bei den physischen Interaktionen in der Praxis, wodurch das Eintauchen und die Freude an Ihrer APP verbessert werden.

In der Eingabe 213 werden die Eingabeereignisse des Bewegungs Controllers durch die Erstellung einer einfachen räumlichen Darstellung untersucht. Mit dieser APP können Benutzer im dreidimensionalen Raum mit verschiedenen Arten von Pinsel und Farben zeichnen.

## <a name="topics-covered-in-this-tutorial"></a>In diesem Tutorial behandelte Themen

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**Controller Visualisierung**|**Controller Eingabeereignisse**|**Benutzerdefinierter Controller und Benutzeroberfläche**|
|Erfahren Sie, wie Sie Motion Controller-Modelle im Spielmodus und der Laufzeit von Unity Renderern.|Lernen Sie die verschiedenen Arten von Schaltflächen Ereignissen und deren Anwendungen kennen.|Erfahren Sie, wie Sie Benutzeroberflächen Elemente oberhalb des Controllers überlagern oder vollständig anpassen.|

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>Mr-Eingabe 213: Motion-Controller</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Bevor Sie beginnen

### <a name="prerequisites"></a>Vorraussetzungen

Sehen Sie sich die Installations Checkliste für immersive Headsets auf [dieser Seite](install-the-tools.md)an.

* Für dieses Tutorial ist [Unity 2017.2.1 P2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe) erforderlich.

### <a name="project-files"></a>Projektdateien

* [Laden Sie die Dateien herunter](https://github.com/Microsoft/MixedReality213/archive/master.zip) , die für das Projekt erforderlich sind, und extrahieren Sie die Dateien auf den Desktop.

>[!NOTE]
>Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/MixedReality213).

## <a name="unity-setup"></a>Unity-Setup

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>Ziele

* Optimieren von Unity für die Windows Mixed Reality-Entwicklung
* Mixed Reality-Kamera einrichten
* Umgebung einrichten

### <a name="instructions"></a>Anweisungen

* Starten Sie Unity.
* Wählen Sie **Öffnen**aus.
* Navigieren Sie zu Ihrem Desktop, und suchen Sie den Ordner **MixedReality213-Master** , den Sie zuvor nicht archiviert haben.
* Klicken Sie auf **Ordner auswählen**.
* Nachdem Unity das Laden von Projektdateien abgeschlossen hat, kann der Unity-Editor angezeigt werden.
* Wählen Sie in Unity **Datei >** Buildeinstellungen aus.

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* Wählen Sie in der Liste **Plattform** **universelle Windows-Plattform** aus, und klicken Sie auf die Schaltfläche **Plattform wechseln** .
* Zielgerät auf **beliebiges Gerät** festlegen
* Buildtyp auf **D3D** festlegen
* SDK auf **Letztes installiert** festlegen
* **Unity C# -Projekte** überprüfen
    * Auf diese Weise können Sie Skriptdateien im Visual Studio-Projekt ändern, ohne das Unity-Projekt neu zu erstellen.
* Klicken Sie auf **Player-Einstellungen**.
* Scrollen Sie im **Inspektor** -Panel nach unten.
* Aktivieren Sie in den XR-Einstellungen die Option **unterstützte virtuelle**
* Wählen Sie unter Virtual Reality sdert **Windows Mixed Reality** aus.

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* Fenster "Buildeinstellungen" schließen.

### <a name="project-structure"></a>Projektstruktur

In diesem Tutorial wird **[Mixed Reality Toolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** verwendet. Die Releases können auf [dieser Seite](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)gefunden werden.

![Projectstructure](images/mr213-projectstructure-650px.png)

**Abgeschlossene Szenen für Ihre Referenz**
* Im Ordner " **Szenen** " finden Sie zwei abgeschlossene Unity-Szenen.
    * **MixedReality213**: Abgeschlossene Szene mit einem Pinsel
    * **MixedReality213Advanced**: Abgeschlossene Szene für erweiterten Entwurf mit mehreren Pinseln

**Neue Szenen Einrichtung für das Tutorial**
* Klicken Sie in Unity auf **Datei > neue Szene** .
* **Hauptkamera** und **Direktionales Licht** löschen
* Suchen Sie im **Projekt Panel**die folgenden Prefabs, und ziehen Sie Sie in das **Hierarchie** Panel:
    * Assets/holotoolkit/Input/Prefabs/**mixedrealitycamera**
    * Assets/appprefabs/**Umgebung**

![Kamera und Umgebung](images/mr213-cameraenvironment-300px.jpg)
* Es gibt zwei Kamera-präfaben im Mixed Reality Toolkit:
    * **Mixedrealitycamera. Prefab**: Nur Kamera
    * **Mixedrealitycameraparent. Prefab**: Kamera + teleportierung + Grenze
    * In diesem Tutorial verwenden wir **mixedrealitycamera** ohne teleportationsfeature. Aus diesem Grund haben wir eine einfache **Umgebungs** Vorschau hinzugefügt, die eine grundlegende Oberfläche enthält, um das Gefühl des Benutzers zu gestalten.
    * Weitere Informationen zur teleportung mit **mixedrealitycameraparent**finden Sie unter [Advanced Design-Teleportations-und fortbewegungs](#advanced-design---teleportation-and-locomotion) Modus.

**Skybox-Setup**
* Klicken Sie auf **Fenster > Beleuchtungs > Einstellungen**
* Klicken Sie auf den Kreis auf der rechten Seite des **Felds Skybox-Material** .
* Geben Sie "Gray" ein, und wählen Sie **skyboxgray** aus.

(Assets/appprefabs/Support/Materials/skyboxgray. Mat)

![Festlegen von Skybox](images/mr123-skyboxsetting-400px.jpg)
* Aktivieren Sie die **Skybox** -Option, um die zugewiesene graue Gradient Skybox anzuzeigen.

![Option ' Skybox ' umschalten](images/mr213-skyboxcheck-400px.jpg)
* Die Szene mit mixedrealitycamera, Environment und Gray Skybox sieht wie folgt aus.

![MixedReality213-Umgebung](images/mr213-environment-600px.jpg)
* Klicken Sie auf **Datei > Szene speichern** unter
* **Speichern** Sie Ihre Szene unter Szenen Ordner mit einem beliebigen Namen.

## <a name="chapter-1---controller-visualization"></a>Kapitel 1: Controller Visualisierung

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>Ziele

* Erfahren Sie, wie Sie Motion Controller-Modelle im Unity-Spielmodus und zur Laufzeit Renderern.

Windows Mixed Reality bietet ein animiertes Controller Modell für die Controller Visualisierung. Es gibt mehrere Ansätze, die Sie für die Controller Visualisierung in Ihrer APP verwenden können:
* Standard-Standard Controller ohne Änderung verwenden
* Hybride Verwendung des Standard Controllers, aber anpassen einiger Elemente oder Überlagern von UI-Komponenten
* Ersetzung: Verwenden eines eigenen benutzerdefinierten 3D-Modells für den Controller

In diesem Kapitel werden die Beispiele dieser Controller Anpassungen erläutert.

### <a name="instructions"></a>Anweisungen

* Geben Sie im **Projekt** Panel im Suchfeld den Text " **mutioncontrollers** " ein. Sie finden es auch unter Assets/holotoolkit/Input/Prefabs/.
* Ziehen Sie den vorfab " **mueconcontrollers** " in das **Hierarchie** Panel.
* Klicken Sie im **Hierarchie** Panel **auf die** vorfab-vorfab.

**Vorfab von "mutioncontrollers"**

Die Prefab-Funktion von " **mueconcontrollers** " verfügt über ein Skript " **mutioncontrollervisualizer** ", das die Slots für alternative Controller Modelle enthält Wenn Sie Ihre eigenen, benutzerdefinierten 3D-Modelle zuweisen, z. b. eine Hand oder ein Schwert, und die Option "immer alternatives nach links/rechts verwenden" aktivieren, werden Sie anstelle des Standardmodells angezeigt. Wir verwenden diesen Slot in Kapitel 4, um das Controller Modell durch einen Pinsel zu ersetzen.

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**Anweisungen**
* Doppelklicken Sie im **Inspektor** -Panel auf das Skript " **mutioncontrollervisualizer** ", um den Code in Visual Studio anzuzeigen.

**Skript für die "mutioncontrollervisualizer"**

Die Klassen " **mutioncontrollervisualizer** " und " **mutioncontrollerinfo** " bieten die Möglichkeit, auf & Ändern der Standard Controller Modelle zuzugreifen. " **Mutioncontrollervisualizer** " abonniert das **Interaction sourcefound** -Ereignis von Unity und instanziiert Controller Modelle automatisch, wenn Sie gefunden werden.

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

Die Controller Modelle werden gemäß [der gltf-Spezifikation](https://github.com/KhronosGroup/glTF)zugestellt. Dieses Format wurde erstellt, um ein gemeinsames Format bereitzustellen, während gleichzeitig der Prozess für das übertragen und entpacken von 3D-Assets verbessert wurde. In diesem Fall müssen wir die Controller Modelle zur Laufzeit abrufen und laden, da wir die Benutzerumgebung so nahtlos wie möglich gestalten möchten, und es ist nicht garantiert, welche Version der Bewegungs Controller der Benutzer verwenden kann. In diesem Kurs wird über das Mixed Reality Toolkit eine Version des [unitygltf-Projekts](https://github.com/KhronosGroup/UnityGLTF)der Khronos-Gruppe verwendet.

Nachdem der Controller übermittelt wurde, können die Skripts mithilfe von " **futioncontrollerinfo** " die Transformationen für bestimmte Controller Elemente suchen, damit Sie sich ordnungsgemäß positionieren können.

In einem späteren Kapitel erfahren Sie, wie diese Skripts zum Anfügen von UI-Elementen an die Controller verwendet werden.

*In einigen Skripts finden Sie Code Blöcke mit **#if! UNITY_EDITOR** oder **UNITY_WSA**. Diese Code Blöcke werden nur für die UWP-Laufzeit ausgeführt, wenn Sie Windows bereitstellen. Dies liegt daran, dass der Satz von APIs, der vom Unity-Editor und der UWP-App-Laufzeit verwendet wird, anders ist.*
* **Speichern** Sie die Szene, und klicken Sie auf die Schaltfläche **abspielen** .

Sie können die Szene mit Motion Controller in Ihrem Headset sehen. Sie können ausführliche Animationen für Schaltflächen Klicks, die Fingereingabe Bewegung und Touchpad Touch-Hervorhebung sehen.

![MR213_Controller-Visualisierungs Standard](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>Kapitel 2: Anfügen von Benutzeroberflächen Elementen an den Controller

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>Ziele

* Weitere Informationen zu den Elementen der Motion-Controller
* Erfahren Sie, wie Sie Objekte an bestimmte Teile der Controller anfügen.

In diesem Kapitel erfahren Sie, wie Sie dem Controller Benutzeroberflächen Elemente hinzufügen, auf die der Benutzer jederzeit problemlos zugreifen und diese bearbeiten kann. Außerdem erfahren Sie, wie Sie mithilfe der Touchpad-Eingabe eine einfache Benutzeroberfläche für die Farbauswahl hinzufügen.

### <a name="instructions"></a>Anweisungen

* Suchen Sie im **Projekt** Panel das Skript " **mutioncontrollerinfo** ".
* Doppelklicken Sie im Suchergebnis auf das Skript " **mutioncontrollerinfo** ", um den Code in Visual Studio anzuzeigen.

**"Mutioncontrollerinfo"-Skript**

Der erste Schritt besteht darin, das Element des Controllers auszuwählen, an das die Benutzeroberfläche angefügt werden soll. Diese Elemente werden in **controllerelementenum** in **MotionControllerInfo.cs**definiert.

![MR213-Element](images/mr213-motioncontrollerelements-1000px.jpg)
* **Home**
* **Stehen**
* **Gespür**
* **Ministick**
* **Auswahl**
* **Touchpad**
* **Zeige** Darstellung – dieses Element stellt die Spitze des Controllers dar, der auf die Vorwärtsrichtung zeigt.

**Anweisungen**
* Suchen Sie im **Projekt** Panel das Skript " **attachdecontroller** ".
* Doppelklicken Sie im Suchergebnis auf **attachdecontroller** -Skript, um den Code in Visual Studio anzuzeigen.

**Attachtoicontroller-Skript**

Das anfügecontroller-Skript bietet eine einfache Möglichkeit, beliebige Objekte an eine angegebene Controller häntigkeit und ein Element anzufügen.

In **attachelementto Controller ()** ,
* Überprüfen Sie die häntigkeit mithilfe von "" "" "" "" " **.**
* Bestimmtes Element des Controllers mithilfe von " **mutioncontrollerinfo. trygetelement ()** " erhalten
* Nachdem Sie die Transformation des Elements aus dem Controller Modell abgerufen haben, übergeordnet Sie das Objekt darunter, und legen Sie die lokale Position des Objekts & Drehung auf NULL fest.

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

Die einfachste Möglichkeit zur Verwendung des **attachtoicontroller** -Skripts ist die Vererbung von der Anwendung, wie dies im Fall von **colorpickerwheel** der Fall ist. Überschreiben Sie einfach die Funktionen **onattachdecontroller** und **ondetatchfromcontroller** , um Setup/Aufschlüsselung auszuführen, wenn der Controller erkannt/getrennt wird.

**Anweisungen**
* Geben Sie im **Projekt** Panel im Suchfeld den Suchbegriff **colorpickerwheel**ein. Sie finden es auch unter Assets/appprefabs/.
* Ziehen Sie **colorpickerwheel** Prefab in den Bereich **Hierarchie** .
* Klicken Sie im **Hierarchie** Panel auf **colorpickerwheel** Prefab.
* Doppelklicken Sie im **Inspektor** -Panel auf **colorpickerwheel** -Skript, um den Code in Visual Studio anzuzeigen.

![Colorpickerwheel-präfab](images/mr213-colorpickerwheel-1000px.jpg)

**Colorpickerwheel-Skript**

Da **colorpickerwheel** " **AttachTo Controller**" erbt, zeigt es die **häntigkeit** und das **Element** im **Inspektor** -Panel. Wir fügen die Benutzeroberfläche an das Touchpad-Element auf dem linken Controller an.

![Colorpickerwheel-Skript](images/mr213-attachtocontroller-300px.jpg)

**Colorpickerwheel** überschreibt den **onattachto Controller** und **onde tatchfromcontroller** , um das Eingabe Ereignis zu abonnieren, das im nächsten Kapitel für die Farbauswahl mit der Touchpad-Eingabe verwendet wird.

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```
* **Speichern** Sie die Szene, und klicken Sie auf die Schaltfläche **abspielen** .

**Alternative Methode zum Anfügen von Objekten an die Controller**

Es wird empfohlen, dass Ihre Skripts von **attachoncontroller** erben und **onattachoncontroller**überschreiben. Dies ist jedoch möglicherweise nicht immer möglich. Eine Alternative ist die Verwendung als eigenständige Komponente. Dies kann hilfreich sein, wenn Sie eine vorhandene vorfab an einen Controller anfügen möchten, ohne Ihre Skripts umgestalten zu müssen. Legen Sie einfach fest, dass die Klasse auf "true" festgelegt ist, bevor Sie Setup ausführen. Die einfachste Möglichkeit hierfür ist die Verwendung einer Coroutine für "Start".

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>Kapitel 3: Arbeiten mit Touchpad-Eingaben

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>Ziele

* Erfahren Sie, wie Sie Eingabedaten Ereignisse von Touchpad erhalten.
* Erfahren Sie, wie Sie die Positionsinformationen der Touchpad-Achse für Ihre APP verwenden.

### <a name="instructions"></a>Anweisungen

* Klicken Sie im **Hierarchie** Panel auf **colorpickerwheel** .
* Doppelklicken Sie im **Inspektor** -Panel unter **animatior**auf **colorpickerwheelcontroller** .
* Sie können die **animatorregister** Karte geöffnet sehen.

**Anzeige/Ausblenden der Benutzeroberfläche mit dem Animations Controller von Unity**

Um die **colorpickerwheel** -Benutzeroberfläche mit Animation anzuzeigen und auszublenden, verwenden wir das [Animationssystem von Unity](https://docs.unity3d.com/Manual/AnimationOverview.html). Wenn Sie die **Visible** -Eigenschaft von **colorpickerwheel**auf true oder false festlegen, werden Animations Trigger **angezeigt** und **ausgeblendet** . Ein **-und** **Ausblenden** von Parametern ist im **colorpickerwheelcontroller** -Animations Controller definiert.

![Unity-Animations Controller](images/mr123-animationcontroller-550px.jpg)

**Anweisungen**
* Wählen Sie im Bereich **Hierarchie** die Option **colorpickerwheel** Prefab aus.
* Doppelklicken Sie im **Inspektor** -Panel auf **colorpickerwheel** -Skript, um den Code in Visual Studio anzuzeigen.

**Colorpickerwheel-Skript**

**Colorpickerwheel** abonniert das **interaktionsourceupdati-** Ereignis von Unity, um auf Touchpad-Ereignisse zu lauschen.

In **interaktionsourceupdatiert ()** prüft das Skript zunächst, ob Folgendes möglich ist:
* ist tatsächlich ein Touchpad-Ereignis (obj. State). **touchpadtouched**)
* stammt vom linken Controller (obj. State. Source). **häntigkeit**)

Wenn beide true sind, ist die Touchpad-Position (obj. State). **touchpadposition**) ist **Selector Position**zugewiesen.

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

In **Update ()** , basierend auf der **Visible** -Eigenschaft, werden Animations Trigger in der animatorkomponente der Farbauswahl angezeigt und ausgeblendet.

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

In **Update ()** wird **Selector Position** verwendet, um einen Strahl in den Mesh-Collider des Farbrades umzuwandeln, der eine UV-Position zurückgibt. Diese Position kann dann verwendet werden, um die Pixel Koordinate und den Farbwert der Textur des Farbrades zu suchen. Auf diesen Wert kann von anderen Skripts über die **selectedColor** -Eigenschaft zugegriffen werden.

![Rad-Raycasting für Farbauswahl](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a>Kapitel 4: Überschreiben des Controller Modells

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>Ziele

* Erfahren Sie, wie Sie das Controller Modell mit einem benutzerdefinierten 3D-Modell überschreiben.

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>Anweisungen

* Klicken **Sie** im **Hierarchie** Panel auf "".
* Klicken Sie rechts neben dem Feld **alternativer rechter Controller** auf den Kreis.
* Geben Sie **"brushcontroller**" ein, und wählen Sie das präfab aus dem Ergebnis aus. Sie finden ihn unter Assets/appprefabs/**brushcontroller**.
* Aktivieren Sie **immer alternatives Rechtes Modell verwenden** .

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

Die **brushcontroller** -vorfab muss nicht im **Hierarchie** Panel enthalten sein. Zum Auschecken der untergeordneten Komponenten:
* Geben Sie im **Projekt** Panel " **brushcontroller** " ein, und ziehen Sie " **brushcontroller** Prefab" in das **Hierarchie** Panel.

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

Sie finden die **Tip** -Komponente in **brushcontroller**. Wir verwenden die Transformation zum Starten/Abbrechen von Zeichnungslinien.
* Löschen Sie den **brushcontroller** aus dem Bereich **Hierarchie** .
* **Speichern** Sie die Szene, und klicken Sie auf die Schaltfläche **abspielen** . Sie können sehen, dass das Pinsel Modell den rechten Bewegungs Controller ersetzt hat.

## <a name="chapter-5---painting-with-select-input"></a>Kapitel 5: Zeichnen mit SELECT-Eingabe

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>Ziele

* Erfahren Sie, wie Sie das Ereignis "Select Button" verwenden, um eine Zeilen Zeichnung zu starten und anzuhalten.

### <a name="instructions"></a>Anweisungen

* Suchen Sie im **Projekt** Panel den Abschnitt " **brushcontroller** Prefab".
* Doppelklicken Sie im **Inspektor** -Panel auf das **Pinsel Controller** Skript, um den Code in Visual Studio anzuzeigen.

**Brushcontroller-Skript**

Der **brushcontroller** abonniert die interaktionsourcepressed -und **interaktionsourcereleasing** -Ereignisse des interaktionmanagers. Wenn das **interaktionsourcepressed** -Ereignis ausgelöst wird, wird die **Draw** -Eigenschaft des Pinsels auf true festgelegt. Wenn das **interaktionsourcereleasing** -Ereignis ausgelöst wird, wird die **Draw** -Eigenschaft des Pinsels auf false festgelegt.

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

Obwohl **Draw** auf true festgelegt ist, generiert der Pinsel Punkte in einem instanziierten Unity- **linerenderer**. Ein Verweis auf diese vorfab wird im Feld **Strich-vorfab** des Pinsels beibehalten.

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

Um die aktuell ausgewählte Farbe von der Oberfläche für die Farbauswahl des Rades zu verwenden, muss für den **brushcontroller** ein Verweis auf das **colorpickerwheel** -Objekt vorhanden sein. Da das **brushcontroller** -präfab zur Laufzeit als Ersatz Controller instanziiert wird, müssen alle Verweise auf Objekte in der Szene zur Laufzeit festgelegt werden. In diesem Fall verwenden wir " **gameobject. findobjectoftype** ", um das **colorpickerwheel**zu finden:

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```
* **Speichern** Sie die Szene, und klicken Sie auf die Schaltfläche **abspielen** . Mithilfe der Schaltfläche auswählen des rechten Controllers können Sie Zeilen und zeichnen zeichnen.

## <a name="chapter-6---object-spawning-with-select-input"></a>Kapitel 6: das Erzeugen von Objekten mit SELECT-Eingabe

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>Ziele

* Informationen zum Verwenden von Eingabe Ereignissen für die Schaltfläche "auswählen" und "
* Weitere Informationen zum Instanziieren von Objekten

### <a name="instructions"></a>Anweisungen

* Geben Sie im **Projekt** Panel im Suchfeld **objectspawner** ein. Sie finden es auch unter Assets/appprefabs/
* Ziehen Sie die vorfab **objectspawner** in den Bereich **Hierarchie** .
* Klicken Sie im **Hierarchie** Panel auf **objectspawner** .
* **Objectspawner** verfügt über ein Feld mit dem Namen **Color Source**.
* Ziehen Sie im **Hierarchie** Panel den **colorpickerwheel** -Verweis in dieses Feld.

![Object Spawner Inspector](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* Klicken Sie im **Hierarchie** Panel auf die vorfab **objectspawner** .
* Doppelklicken Sie im **Inspektor** -Panel auf **objectspawner** Script, um den Code in Visual Studio anzuzeigen.

**Objectspawner-Skript**

Der **objectspawner** instanziiert Kopien eines primitiven Netzes (Cube, Kugel, Zylinder) in den Raum. Wenn eine **interaktionsourcepressed** erkannt wird, überprüft Sie die häntigkeit und, wenn es sich um ein **interaktionsourcepresstype. Grasp** -oder **interaktionsourcepresstype. Select** -Ereignis handelt.

Bei einem **grasp** -Ereignis erhöht es den Index des aktuellen Mesh-Typs (Kugel, Cube, Zylinder).

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

Bei einem **Select** -Ereignis in **spawnobject ()** wird ein neues-Objekt instanziiert, nicht übergeordnet und in der Welt veröffentlicht.

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detatch the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

Der **objectspawner** verwendet das **colorpickerwheel** , um die Farbe des Materials des Anzeige Objekts festzulegen. Erzeugten Objekten wird eine Instanz dieses Materials zugewiesen, damit Sie Ihre Farbe beibehalten.
* **Speichern** Sie die Szene, und klicken Sie auf die Schaltfläche **abspielen** .

Mit der Schaltfläche "auswählen" können Sie die Objekte mit der Schaltfläche "übersetzen" und "Objekte" mithilfe der Schaltfläche "

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>Erstellen und Bereitstellen der APP im Mixed Reality-Portal
* Wählen Sie in Unity **Datei >** Buildeinstellungen aus.
* Klicken Sie auf **offene Szenen hinzufügen** , um die aktuelle Szene zu den **Kulissen in Build**hinzuzufügen.
* Klicken Sie auf **Erstellen**.
* Erstellen Sie einen **neuen Ordner** mit dem Namen "App".
* Klicken Sie einfach auf den **App** -Ordner.
* Klicken Sie auf **Ordner auswählen**.
* Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.
* Öffnen Sie den **App** -Ordner.
* Doppelklicken Sie auf **yourscenename. sln** Visual Studio-Projektmappendatei.
* Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x64**.
* Klicken Sie auf den Dropdown Pfeil neben der Schaltfläche Gerät, und wählen Sie **lokaler Computer**aus.
* Klicken Sie im Menü auf **Debuggen > Starten ohne Debuggen** , oder drücken Sie **STRG + F5**.

Nun wird die APP im Mixed Reality-Portal erstellt und installiert. Sie können Sie erneut über das Startmenü im Mixed Reality-Portal starten.

## <a name="advanced-design---brush-tools-with-radial-layout"></a>Erweiterte Entwurfs Pinsel Tools mit radialem Layout

![MixedReality213 Main](images/mr213-main-600px.jpg)

In diesem Kapitel erfahren Sie, wie Sie das standardmäßige Motion Controller-Modell durch eine benutzerdefinierte Pinsel Tool Auflistung ersetzen. Eine Referenz finden Sie im Ordner "abgeschlossene Szene **MixedReality213Advanced** " unter **Szenen** .

### <a name="instructions"></a>Anweisungen

* Geben Sie im **Projekt** Panel im Suchfeld den Text **brushselector** ein. Sie finden es auch unter Assets/appprefabs/
* Ziehen Sie die vorfab von **brushselector** in den Bereich **Hierarchie** .
* Erstellen Sie für die Organisation ein leeres gameobject namens **Pinsel** .
* Ziehen Sie die folgenden Prefabs aus dem **Projekt** Panel in **Pinsel** .
    * Assets/appprefabs/**brushfat**
    * Assets/appprefabs/**brushthin**
    * Assets/appprefabs/**Radierer**
    * Assets/appprefabs/**markerfat**
    * Assets/appprefabs/**markerthin**
    * Assets/appprefabs/**Stift**

![Pinsel](images/mixedreality213-brushes-250px.png)
* Klicken **Sie** im **Hierarchie** Panel auf die vorfab-vorfab.
* Deaktivieren Sie im **Inspektor** -Panel die Option **alternatives Rechtes Modell immer verwenden** auf der **Motion Controller** -Schnellansicht.
* Klicken Sie im Bereich **Hierarchie** auf **brushselector** .
* Der **brushselector** hat ein Feld mit dem Namen **ColorPicker** .
* Ziehen Sie im Bereich **Hierarchie** das **colorpickerwheel** in das Feld **ColorPicker** im **Inspektor** -Panel.

![Colorpickerwheel zum pinselselektor zuweisen](images/mr213-brushselector-500px.jpg)
* Wählen Sie im Bereich **Hierarchie** unter **brushselector** Prefab das **Menü** Objekt aus.
* Öffnen Sie im **Inspektor** -Panel unter der **lineobjectcollection** -Komponente die Dropdown Liste **Objekt** Array. Sechs leere Slots werden angezeigt.
* Ziehen Sie im Bereich **Hierarchie** die einzelnen Prefabs unter dem gameobject- **Pinsel** in beliebiger Reihenfolge in diese Slots. (Stellen Sie sicher, dass Sie die Prefabs aus der Szene ziehen, nicht die präfabs im Projektordner.)

![Pinsel Auswahl](images/mr213-brushselectorbrushes-700px.jpg)

**Brushselector-vorfab**

Da der **brushselector** **attachdecontroller**erbt, werden die Optionen für die **häntigkeit** und das **Element** im **Inspektor** -Panel angezeigt. Wir haben **right** ausgewählt und **zeigen eine Pose** an, um Pinsel Tools an den rechten Controller mit Vorwärtsrichtung anzufügen.

Der **brushselector** nutzt zwei Hilfsprogramme:
* **Ellipse**: wird verwendet, um Punkte im Raum entlang einer Ellipse-Form zu generieren.
* **Lineobjectcollection**: verteilt Objekte mithilfe der von einer beliebigen Zeilen Klasse generierten Punkte (z. b. Ellipse). Das ist das, was wir verwenden werden, um die Pinsel entlang der Ellipse-Form zu platzieren.

In Kombination können diese Hilfsprogramme verwendet werden, um ein radiales Menü zu erstellen.

**Lineobjectcollection-Skript**

**Lineobjectcollection** verfügt über Steuerelemente für Größe, Position und Drehung von Objekten, die entlang der Zeile verteilt werden. Dies ist nützlich, um radiale Menüs wie die Pinsel Auswahl zu erstellen. Um die Darstellung von Pinseln zu erstellen, die von nichts zentral hochskaliert werden, wenn Sie sich auf die ausgewählte Position im Zentrum angleichen, wird die **objectscale** -Kurve in der Mitte zentriert und an den Rändern ausgeschaltet.

**Pinsel Auswahl Skript**

Im Fall von " **brushselector**" haben wir die Verwendung der Verfahrens bezogenen Animation gewählt. Zuerst werden Pinsel Modelle durch das **lineobjectcollection** -Skript in einer Ellipse verteilt. Dann ist jeder Pinsel dafür verantwortlich, seine Position in der Hand des Benutzers basierend auf seinem **DisplayMode** -Wert beizubehalten, der sich auf der Grundlage der Auswahl ändert. Wir haben uns für einen Verfahrensansatz entschieden, da die hohe Wahrscheinlichkeit, dass der Pinsel positioniert wird, unterbrochen wird, wenn der Benutzer Pinsel auswählt. Mecanim-Animationen können Unterbrechungen ordnungsgemäß behandeln, Sie sind jedoch tendenziell komplizierter als ein einfacher Lerp-Vorgang.

" **Brushselector** " verwendet eine Kombination aus beidem. Wenn Touchpad-Eingaben erkannt werden, werden Pinseloptionen sichtbar und im radialen Menü zentral hochskaliert. Nach einem Timeout Zeitraum (der angibt, dass der Benutzer eine Auswahl getroffen hat) können die Pinseloptionen wieder herunterskaliert werden, sodass nur der ausgewählte Pinsel erhalten bleibt.

**Visualisieren der Touchpad-Eingabe**

Auch in Fällen, in denen das Controller Modell vollständig ersetzt wurde, kann es hilfreich sein, Eingaben für die ursprünglichen Modell Eingaben anzuzeigen. Dies trägt dazu bei, die Aktionen des Benutzers in der Praxis zu unterstützen. Für den **brushselector** haben wir ausgewählt, dass der Touchpad beim Empfang der Eingabe kurz sichtbar ist. Dies wurde erreicht, indem das Touchpad-Element vom Controller abgerufen wurde, dessen Material durch ein benutzerdefiniertes Material ersetzt wurde. Anschließend wird ein Farbverlauf auf die Farbe dieses Materials angewendet, basierend auf dem Zeitpunkt, an dem die Touchpad-Eingabe zuletzt empfangen wurde.

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }
            
    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

**Auswahl des Pinsel Tools mit Touchpad-Eingabe**

Wenn die Pinsel Auswahl die gedrückte Eingabe von Touchpad erkennt, wird die Position der Eingabe überprüft, um festzustellen, ob Sie sich links oder rechts befand.

**Strichstärke mit selectpressedamount**

Anstelle des **interaktionsourcepresstype. Select** -Ereignisses in **interaktionsourcepressed ()** können Sie den analogen Wert der gedrückten Menge über **selectpressedamount**erhalten. Dieser Wert kann in **interaktionsourceupveraltet ()** abgerufen werden.

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

**Erradierskript**

Der Radierer ist ein spezieller Pinseltyp, der die **drawovertime ()** -Funktion des Basis **Pinsels**überschreibt. Obwohl Draw den Wert true hat, prüft der Radierer, ob seine Spitze sich mit vorhandenen Pinselstrichen überschneidet. Wenn dies der Fall ist, werden Sie zu einer Warteschlange hinzugefügt, die verkleinert und gelöscht werden soll.

## <a name="advanced-design---teleportation-and-locomotion"></a>Erweiterte Design-teleportierung und-Bewegung

Wenn Sie zulassen möchten, dass der Benutzer die Szene mit der teleportierung über den Finger Stick bewegt, verwenden Sie **mixedrealitycameraparent** anstelle von **mixedrealitycamera**. Außerdem müssen Sie **InputManager** und **defaultcusor**hinzufügen. Da **mixedrealitycameraparent** bereits " **mutioncontrollers** " und " **Border** " als untergeordnete Komponenten enthält, sollten Sie vorhandene " **mueconcontrollers** " und " **Umgebungs** vorfab" entfernen.

### <a name="instructions"></a>Anweisungen

* Löschen Sie im **Hierarchie** Panel **mixedrealitycamera**, **Environment** und **mutioncontrollers** .
* Suchen Sie im **Projekt Panel**die folgenden Prefabs, und ziehen Sie Sie in das **Hierarchie** Panel:
    * Assets/appprefabs/Input/Prefabs/**mixedrealitycameraparent**
    * Assets/appprefabs/Input/Prefabs/**InputManager**
    * Assets/appprefabs/Input/Prefabs/Cursor/**DefaultCursor**

![Übergeordnetes Mixed Reality-Kamera](images/mr213-cameraparent-300px.png)
* Klicken Sie im **Hierarchie** Panel auf **Eingabe-Manager** .
* Scrollen Sie im **Inspektor** -Panel nach unten zum Abschnitt **einfache Auswahl des einzelnen Zeigers** .
* Ziehen Sie im Bereich **Hierarchie** **DefaultCursor** in das Feld **Cursor** .

![Zuweisen von DefaultCursor](images/mr213-defaultcursor-500px.png)
* **Speichern** Sie die Szene, und klicken Sie auf die Schaltfläche **abspielen** . Sie können den Finger Stick verwenden, um nach links/rechts oder Teleport zu drehen.

## <a name="the-end"></a>Das Ende

Und das ist das Ende dieses Tutorials! Sie haben Folgendes gelernt:
* Arbeiten mit Motion Controller-Modellen im Spielmodus und der Laufzeit von Unity.
* Verwenden verschiedener Arten von Schaltflächen Ereignissen und ihrer Anwendungen.
* Überlagern von UI-Elementen oberhalb des Controllers oder vollständiges anpassen.

Nun können Sie mit der Erstellung Ihrer eigenen immersiven Benutzer Arbeit mit Motion Controller beginnen!

## <a name="completed-scenes"></a>Abgeschlossene Szenen

* Klicken Sie im Unity- **Projekt** Panel auf den Ordner **Szenen** .
* Sie finden zwei Unity-Sceens- **MixedReality213** und **MixedReality213Advanced**.
    * **MixedReality213**: Abgeschlossene Szene mit einem Pinsel
    * **MixedReality213Advanced**: Abgeschlossene Szene mit mehreren Pinseln mit dem Press Amount-Beispiel der Schaltfläche

## <a name="see-also"></a>Siehe auch

* [Eingabe 213-Projektdateien](https://github.com/Microsoft/MixedReality213)
* [Mixed Reality Toolkit: Test Szene für Motion Controller](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [Mixed Reality Toolkit-Griff Mechanik](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [Entwicklungs Richtlinien für Motion Controller](motion-controllers.md)
