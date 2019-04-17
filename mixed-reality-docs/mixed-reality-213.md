---
title: MR Eingabe 213
description: Dieses Tutorial Schreiben von Code mithilfe von Unity, Visual Studio und immersive Headsets für die Details der Motion-Controller.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Holotoolkit, Mixedrealitytoolkit, Mixedrealitytoolkit-Unity, immersive motion, Controller, Academy, Tutorial
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604704"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

<br>

# <a name="mr-input-213-motion-controllers"></a>MR Eingabe 213: Motion-Controller

Motion-Controller in der Welt mixed Reality fügen Sie ein anderes Maß an Interaktivität hinzu. Mit [motion Controller](motion-controllers.md), können direkte Interaktion mit Objekten auf natürlichere Weise, wie unsere physischen Interaktionen in der Praxis zu Entwicklungsthemen zu erhöhen und erfreuen Sie Ihre app-Erfahrung.

Eingabe 213 MR erforschen wir Eingabeereignisse von der Motion-Controller durch eine einfache räumliche zeichnen-Umgebung erstellen. Mit dieser app können Benutzer im dreidimensionalen Raum mit verschiedenen Typen von Pinsel und Farben zeichnen.

## <a name="topics-covered-in-this-tutorial"></a>In diesem Tutorial behandelten Themen

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**Controller-Visualisierung**|**Controller-Eingabeereignisse**|**Benutzerdefinierten Controller und Benutzeroberfläche**|
|Erfahren Sie, wie während der Übertragung Controller-Modellen in Unity-Spiele-Modus und Laufzeit gerendert.|Erfahren Sie, verschiedene Typen von Schaltflächenereignisse und ihre Anwendungen.|Erfahren Sie, wie overlay-Elemente der Benutzeroberfläche auf dem Controller oder vollständig anpassen.|

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td>MR Eingabe 213: Motion-Controller</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Bevor Sie beginnen

### <a name="prerequisites"></a>Vorraussetzungen

Finden Sie auf die Installations-Checkliste für immersive Headsets [auf dieser Seite](install-the-tools.md).

* In diesem Lernprogramm [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)

### <a name="project-files"></a>Projektdateien

* [Laden Sie die Dateien](https://github.com/Microsoft/MixedReality213/archive/master.zip) vom das Projekt benötigt, und extrahieren Sie die Dateien auf dem Desktop.

>[!NOTE]
>Wenn Sie vor dem Herunterladen, den Quellcode ansehen möchten es [auf GitHub verfügbar](https://github.com/Microsoft/MixedReality213).

## <a name="unity-setup"></a>Unity-setup

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>Ziele

* Optimieren von Unity für Windows Mixed Reality-Entwicklung
* Einrichten von Mixed Reality-Kamera
* Einrichten der Umgebung

### <a name="instructions"></a>Anweisungen

* Starten Sie Unity.
* Wählen Sie **öffnen**.
* Navigieren Sie zu Ihrem Desktop und finden die **MixedReality213-Master** Ordner, die Sie zuvor nicht archiviert.
* Klicken Sie auf **Ordner auswählen**.
* Wenn Unity abgeschlossen ist, Projektdateien werden geladen, werden Sie Unity-Editor angezeigt.
* Wählen Sie in Unity **Datei > Buildeinstellungen**.

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* Wählen Sie **universelle Windows-Plattform** in die **Plattform** aus, und klicken Sie auf die **Plattform wechseln** Schaltfläche.
* Legen Sie Zielgerät auf **jedes Gerät**
* Legen Sie Buildtyp auf **D3D**
* Legen Sie die SDK auf **zuletzt installierte**
* Überprüfen Sie **Unity C# Projekte**
    * Dadurch, dass Sie die Skriptdateien in Visual Studio-Projekt ändern, ohne Neuerstellung von Unity-Projekt.
* Klicken Sie auf **Playereinstellungen**.
* In der **Inspektor** Panel, führen Sie einen Bildlauf nach unten
* Überprüfen Sie unter "XR-Einstellungen" **virtuelle Realität unterstützt**
* Wählen Sie unter virtuelle Realität SDKs **Windows Mixed Reality**

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* Schließen **Buildeinstellungen** Fenster.

### <a name="project-structure"></a>Struktur des Projekts

Dieses Tutorial verwendet  **[Mixed Reality-Toolkit – Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**. Die Versionen finden Sie auf [auf dieser Seite](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).

![ProjectStructure](images/mr213-projectstructure-650px.png)

**Abgeschlossene Szenen zur Referenz**
* Sehen Sie zwei abgeschlossene Unity im Hintergrund unter **Szenen** Ordner.
    * **MixedReality213**: Vollständige Szene mit einzelnen Pinsel
    * **MixedReality213Advanced**: Für erweiterte Entwurf mit mehreren Pinsel Szene abgeschlossen

**Einrichten einer neuen Szene für das tutorial**
* Klicken Sie in Unity auf **Datei > neue Szene**
* Löschen Sie **Hauptkamera** und **gerichtetes Licht**
* Von der **Projektfenster**, suchen, und ziehen Sie die folgenden prefabs (Vorlagen) in der **Hierarchie** Bereich:
    * Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**
    * Assets/AppPrefabs/**Environment**

![Kamera und Umgebung](images/mr213-cameraenvironment-300px.jpg)
* Es gibt zwei Kamera Prefabs in Mixed Reality-Toolkit:
    * **MixedRealityCamera.prefab**: Nur der Kamera
    * **MixedRealityCameraParent.prefab**: Kamera + Teleportation + Grenze
    * In diesem Tutorial verwenden wir **MixedRealityCamera** ohne Teleportation-Funktion. Aus diesem Grund wir einfache hinzugefügt **Umgebung** Prefab enthält eine grundlegende Etage um geerdete können Benutzer zu machen.
    * Weitere Informationen zu den Teleportation mit **MixedRealityCameraParent**, finden Sie unter [erweitert Design - Teleportation und Locomotion](#advanced-design---teleportation-and-locomotion)

**Skybox-setup**
* Klicken Sie auf **Fenster > Beleuchtung > Einstellungen**
* Klicken Sie auf den Kreis auf dem rechten Rand der **Skybox Material-Feld**
* Geben Sie in "grau", und wählen Sie **SkyboxGray**

(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)

![Festlegen von skybox](images/mr123-skyboxsetting-400px.jpg)
* Überprüfen Sie **Skybox** können angezeigt werden zugewiesen, grauen Farbverlauf Skybox

![Skybox Umschaltoption](images/mr213-skyboxcheck-400px.jpg)
* Die Szene mit MixedRealityCamera "," Umgebung "und" graue Skybox sieht wie folgt aus.

![MixedReality213 Environment](images/mr213-environment-600px.jpg)
* Klicken Sie auf **Datei > Szene speichern unter**
* **Speichern Sie** Ihrer Szene Ordner im Hintergrund mit einem beliebigen Namen

## <a name="chapter-1---controller-visualization"></a>Kapitel 1 - Controller-Visualisierung

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>Ziele

* Erfahren Sie, wie während der Übertragung Controller-Modelle im Unity Spiele-Modus und zur Laufzeit gerendert.

Windows Mixed Reality bietet eine animierte Controllermodell für die Controller-Visualisierung. Es gibt verschiedene Ansätze, die Sie für die Visualisierung der Controller in Ihrer app ausführen können:
* Standard - Standardcontroller, ohne Änderungen verwenden
* Hybrid - Standardcontroller, verwenden jedoch einige Elemente anpassen oder Überlagern von UI-Komponenten
* Ersatz - Ihre eigene angepasste 3D-Modell für den controller

In diesem Kapitel lernen wir zu den Beispielen dieser Controller Anpassungen.

### <a name="instructions"></a>Anweisungen

* In der **Projekt** geben **MotionControllers** in das Suchfeld. Sie finden ihn außerdem unter Assets/HoloToolkit/Input/Prefabs /.
* Ziehen Sie die **MotionControllers** prefab in die **Hierarchie** Bereich.
* Klicken Sie auf die **MotionControllers** prefab in die **Hierarchie** Bereich.

**MotionControllers prefabs**

**MotionControllers** Prefab ist ein **MotionControllerVisualizer** Skript an der die Steckplätze für alternativen Controller Modelle enthält. Wenn Sie Ihre eigenen benutzerdefinierten 3D-Modelle, z. B. einer Hand oder ein "sword" zuweisen und überprüfen 'Immer mit alternativen links/rechts Model', sehen Sie diese anstelle des Standard-Modells. Wir werden dieser Steckplatz in Kapitel 4 verwenden, um die Controller-Modell mit einem Pinsel zu ersetzen.

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**Anweisungen**
* In der **Inspektor** panel, doppelklicken Sie auf **MotionControllerVisualizer** Skript den Code in Visual Studio finden Sie unter

**MotionControllerVisualizer-Skript**

Die **MotionControllerVisualizer** und **MotionControllerInfo** Klassen bieten die Möglichkeit zum Zugriff auf und ändern die Standard-Controller-Modelle. **MotionControllerVisualizer** Unity abonniert **InteractionSourceDetected** Ereignis und Controller-Modelle automatisch instanziiert, wenn sie gefunden werden.

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

Die Controller-Modelle werden bereitgestellt, gemäß [der Spezifikation GlTF](https://github.com/KhronosGroup/glTF). Dieses Format wurde erstellt, um ein einheitliches Format, bei der Verbesserung des Prozesses übertragen, und Entpacken von 3D-Objekten bereitzustellen. In diesem Fall müssen wir zum Abrufen und laden die Controller-Modelle zur Laufzeit, wie wir der benutzerfreundlichkeit des so reibungslos wie möglich gestalten möchten, und es ist nicht garantiert, welche Version der Controller während der Übertragung der Benutzer verwendet werden kann. Dieser Kurs, über das Mixed Reality-Toolkit, verwendet eine Version von der Gruppe Khronos [UnityGLTF Projekt](https://github.com/KhronosGroup/UnityGLTF).

Skripts können verwendet werden, sobald der Controller übermittelt wurden, **MotionControllerInfo** , finden die Transformationen für bestimmte Controller-Elemente, sodass sie selbst richtig positionieren können.

In einem der folgenden Kapitel lernen wir, wie Sie diese Skripts zu verwenden, um Benutzeroberflächenelemente auf Controller anzufügen.

*In einigen Skripts finden Sie Codeblöcke mit **#if! UNITY_EDITOR** oder **UNITY_WSA**. Diese Codeblöcke, die nur auf die UWP-Laufzeit ausgeführt werden, beim Bereitstellen von für Windows. Das liegt der Satz von APIs, die von Unity-Editor und die UWP-app-Laufzeit verwendet werden, sind unterschiedlich.*
* **Speichern Sie** der Szene, und klicken Sie auf die **spielen** Schaltfläche.

Sie werden können Sie die Szene mit Motion-Controllern in Ihre Kopfhörer. Sie können ausführliche Animationen auf eine Schaltfläche, Ministick verschieben und Hervorheben von Touchpad Touch anzeigen.

![MR213_Controller Visualisierung Standard](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>Kapitel 2: Anfügen von UI-Elemente mit dem controller

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>Ziele

* Erfahren Sie mehr über die Elemente der Motion-Controller
* Erfahren Sie, wie zum Anfügen von Objekten auf bestimmte Teile der Controller

In diesem Kapitel lernen Sie, wie Sie die Elemente der Benutzeroberfläche der Controller hinzufügen, die der Benutzer kann einfach zugreifen und diese jederzeit auf Bearbeiten. Außerdem lernen Sie, wie eine einfache Farbauswahl-Benutzeroberfläche mit dem Touchpad Eingabe hinzugefügt werden.

### <a name="instructions"></a>Anweisungen

* In der **Projekt** Bereich, suchen Sie **MotionControllerInfo** Skript.
* Im Suchergebnis doppelklicken **MotionControllerInfo** Skript, um den Code in Visual Studio anzuzeigen.

**MotionControllerInfo-Skript**

Der erste Schritt ist, welches Element des Controllers die Benutzeroberfläche an angefügt werden sollen. Diese Elemente sind in definiert **ControllerElementEnum** in **MotionControllerInfo.cs**.

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)
* **Home**
* **Menü "**
* **Verstehen**
* **Thumbstick**
* **Wählen Sie**
* **Touchpad**
* **Zeigen Sie Haltung** : dieses Element stellt dar, die Spitze des Controllers vorwärts verweist.

**Anweisungen**
* In der **Projekt** Bereich, suchen Sie **AttachToController** Skript.
* Im Suchergebnis doppelklicken **AttachToController** Skript, um den Code in Visual Studio anzuzeigen.

**AttachToController-Skript**

Die **AttachToController** -Skript zeigt eine einfache Möglichkeit, alle Objekte in einer angegebenen Controller Händigkeit und das-Element anzufügen.

In **AttachElementToController()**,
* Überprüfen Sie mit der Händigkeit **MotionControllerInfo.Handedness**
* Abrufen von bestimmten Element dem Controller mithilfe **MotionControllerInfo.TryGetElement()**
* Klicken Sie nach dem Abrufen des Elements aus dem Controllermodell, übergeordneten Objekts im es transformieren, und lokale Position und Drehung des Objekts auf 0 (null) festgelegt.

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

Die einfachste Möglichkeit zum Verwenden **AttachToController** Skript ist das erben, wie im Fall von **ColorPickerWheel.** Überschreiben Sie einfach die **OnAttachToController** und **OnDetatchFromController** Funktionen, um das Setup ausführen / Aufschlüsselung, wenn der Controller getrennt / gefunden wird.

**Anweisungen**
* In der **Projekt** Geben Sie im Suchfeld **ColorPickerWheel**. Sie finden ihn außerdem unter Assets/AppPrefabs /.
* Ziehen Sie **ColorPickerWheel** prefab in die **Hierarchie** Bereich.
* Klicken Sie auf die **ColorPickerWheel** prefab in die **Hierarchie** Bereich.
* In der **Inspektor** panel, doppelklicken Sie auf **ColorPickerWheel** Skript, um den Code in Visual Studio anzuzeigen.

![ColorPickerWheel prefabs](images/mr213-colorpickerwheel-1000px.jpg)

**ColorPickerWheel-Skript**

Da **ColorPickerWheel** erbt **AttachToController**, es zeigt **Händigkeit** und **Element** in die  **Inspector** Bereich. Wir werden die Benutzeroberfläche auf das Touchpad-Element, auf dem linken Controller angefügt werden.

![ColorPickerWheel-Skript](images/mr213-attachtocontroller-300px.jpg)

**ColorPickerWheel** überschreibt die **OnAttachToController** und **OnDetatchFromController** das Eingabeereignis abonnieren, die im nächsten Kapitel zur Farbauswahl mit verwendet wird Touchpad eingeben.

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
* **Speichern Sie** der Szene, und klicken Sie auf die **spielen** Schaltfläche.

**Alternative Methode zum Anfügen von Objekten auf Controller**

Es wird empfohlen, Ihre Skripts erben **AttachToController** und überschreiben **OnAttachToController**. Allerdings kann dies nicht immer möglich. Eine Alternative ist es als eigenständige Komponente verwenden. Dies kann nützlich sein, wenn Sie einen Controller ohne Umgestaltung Ihrer Skripts einer vorhandenen Prefab anfügen möchten. Haben Sie einfach Ihre Klasse IsAttached festgelegt werden, warten vor dem Ausführen von Setup "true". Die einfachste Möglichkeit hierzu ist, mithilfe einer Coroutine für "Start".

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>Kapitel 3 – arbeiten mit Touchpad-Eingabe

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>Ziele

* Erfahren Sie, wie Touchpad Eingabedaten Ereignisse abrufen
* Informationen Sie zur Verwendung von Informationen zur Position der Achse Touchpad für Ihre app-Erfahrung

### <a name="instructions"></a>Anweisungen

* In der **Hierarchie** auf **ColorPickerWheel**
* In der **Inspektor** Bereich unter **Animatior**, Doppelklick **ColorPickerWheelController**
* Sie werden sehen **Animator** Registerkarte geöffnet

**Anzeigen/ausblenden-Benutzeroberfläche mit Unity Animationscontroller**

Ein-und Ausblenden der **ColorPickerWheel** -Benutzeroberfläche mit Animation verwenden wir [Unity Animationssystem](https://docs.unity3d.com/Manual/AnimationOverview.html). Festlegen der **ColorPickerWheel**des **Visible** Eigenschaft auf "true" oder "false" Trigger **anzeigen** und **ausblenden** Animationstrigger. **Anzeigen** und **ausblenden** Parameter werden definiert, der **ColorPickerWheelController** Animationscontroller.

![Unity-Animationscontroller](images/mr123-animationcontroller-550px.jpg)

**Anweisungen**
* In der **Hierarchie** wählen **ColorPickerWheel** prefab
* In der **Inspektor** panel, doppelklicken Sie auf **ColorPickerWheel** Skript den Code in Visual Studio finden Sie unter

**ColorPickerWheel-Skript**

**ColorPickerWheel** Unity abonniert **InteractionSourceUpdated** Ereignis Touchpad Ereignisse zu überwachen.

In **InteractionSourceUpdated()**, zuerst das Skript überprüft, um sicherzustellen, dass es:
* ist tatsächlich ein Touchpad-Ereignis (obj.state. **TouchpadTouched**)
* stammt aus dem linken Controller (obj.state.source. **Händigkeit**)

Wenn beides zutrifft, positionieren Sie das Touchpad (obj.state. **TouchpadPosition**) zugewiesen wird **SelectorPosition**.

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

In **Update()** basierend auf **sichtbar** Eigenschaft auslöst werden ein- / ausblenden-Animation-Trigger in der Farbauswahl Animator-Komponente

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

In **Update()**, **SelectorPosition** wird verwendet, um ein Strahl unter dem Farbkreis Mesh "collider", umgewandelt. Dadurch kann eine UV-Position gibt. Diese Position kann dann verwendet werden, finden die Pixelkoordinate und Farbwert dem Farbkreis Textur. Dieser Wert kann zugegriffen werden, um andere Skripts über die **SelectedColor** Eigenschaft.

![Farbe Auswahl Wheel feinheiten beim Raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

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

## <a name="chapter-4---overriding-controller-model"></a>Kapitel 4 – überschreiben die Controller-Modell

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>Ziele

* Erfahren Sie, wie das Controllermodell mit einem benutzerdefinierten 3D-Modell außer Kraft zu setzen.

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>Anweisungen

* Klicken Sie auf **MotionControllers** in die **Hierarchie** Bereich.
* Klicken Sie auf den Kreis auf dem rechten Rand der **alternativen rechts Controller** Feld.
* Geben Sie in **"BrushController**", und wählen Sie das Prefab aus dem Ergebnis. Sie finden diese Ressourcen/AppPrefabs/**BrushController**.
* Überprüfen Sie **alternativen richtige Modell immer verwenden**

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

Die **BrushController** Prefab muss nicht in aufgenommen werden die **Hierarchie** Bereich. Allerdings Auschecken von seinen untergeordneten Komponenten:
* In der **Projekt** Bereich, geben Sie im **BrushController** , und ziehen Sie **BrushController** prefab in die **Hierarchie** Bereich.

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

Sie finden die **Tipp** -Komponente in **BrushController**. Wir verwenden seine Transformation Starten/Beenden von Zeichnen von Linien.
* Löschen der **BrushController** aus der **Hierarchie** Bereich.
* **Speichern Sie** der Szene, und klicken Sie auf die **spielen** Schaltfläche. Sie werden sehen, dass das Pinsel-Modell mit der rechten Motion-Controller ersetzt.

## <a name="chapter-5---painting-with-select-input"></a>Kapitel 5 – Eingabe Zeichnen mit Select-Anweisung

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>Ziele

* Erfahren Sie, wie das Ereignis auswählen-Schaltfläche zum Starten und beenden eine Strichzeichnung verwenden

### <a name="instructions"></a>Anweisungen

* Suche **BrushController** prefab in die **Projekt** Bereich.
* In der **Inspektor** panel, doppelklicken Sie auf **BrushController** Skript den Code in Visual Studio finden Sie unter

**BrushController-Skript**

**BrushController** abonniert die InteractionManager des **InteractionSourcePressed** und **InteractionSourceReleased** Ereignisse. Wenn **InteractionSourcePressed** Ereignis wird ausgelöst, des Pinsels **zeichnen** -Eigenschaftensatz auf "true", wenn **InteractionSourceReleased** Ereignis wird ausgelöst, des Pinsels **Zeichnen** Eigenschaft auf "false" festgelegt ist.

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

Während **zeichnen** nastaven NA hodnotu True gibt an, der Pinsel generiert Punkte in einem instanziierten Unity **LineRenderer**. Ein Verweis auf dieses Prefab bleibt im des Pinsels **Stroke Prefab** Feld.

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

Verwenden Sie die zurzeit ausgewählte Farbe aus der Auswahl-Farbkreis-Benutzeroberfläche **BrushController** benötigt einen Verweis auf die **ColorPickerWheel** Objekt. Da die **BrushController** Prefab zur Laufzeit als eine Ersatzcontroller instanziiert wird, müssen alle Verweise auf Objekte in der Szene zur Laufzeit festgelegt werden. In diesem Fall verwenden wir **GameObject.FindObjectOfType** zum Suchen der **ColorPickerWheel**:

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
* **Speichern Sie** der Szene, und klicken Sie auf die **spielen** Schaltfläche. Sie werden zum Zeichnen der Linien und zeichnen, verwenden die auswählen-Schaltfläche am rechten Controller.

## <a name="chapter-6---object-spawning-with-select-input"></a>Kapitel 6: Eingabe Objekt erzeugen mit Select-Anweisung

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>Ziele

* Erfahren Sie, wie Sie mit der Option, und fassen Sie die Schaltfläche Eingabeereignisse
* Erfahren Sie, wie zum Instanziieren von Objekten

### <a name="instructions"></a>Anweisungen

* In der **Projekt** geben **ObjectSpawner** in das Suchfeld. Sie finden ihn außerdem unter Assets/AppPrefabs /
* Ziehen Sie die **ObjectSpawner** prefab in die **Hierarchie** Bereich.
* Klicken Sie auf **ObjectSpawner** in die **Hierarchie** Bereich.
* **ObjectSpawner** verfügt über ein Feld mit dem Namen **Farbe Quelle**.
* Von der **Hierarchie** ziehen Sie die **ColorPickerWheel** Verweis in dieses Feld.

![Objekt Spawner Inspector](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* Klicken Sie auf die **ObjectSpawner** prefab in die **Hierarchie** Bereich.
* In der **Inspektor** panel, doppelklicken Sie auf **ObjectSpawner** Skript, um den Code in Visual Studio anzuzeigen.

**ObjectSpawner-Skript**

Die **ObjectSpawner** Kopien eines primitiven Netzes (Cube, Kugel, Zylinder) in den Bereich instanziiert. Wenn eine **InteractionSourcePressed** erkannt wird, überprüft er die rechts-oder Linkshändigkeit und es ist ein **InteractionSourcePressType.Grasp** oder **InteractionSourcePressType.Select** das Ereignis.

Für eine **verstehen** -Ereignis, es erhöht den Index des aktuellen Netztyp (Kugel, Cube, Zylinder)

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

Für eine **wählen** Ereignis im **SpawnObject()**, ein neues Objekt ist instanziiert, ohne übergeordnetes Element und veröffentlicht Sie in der ganzen Welt.

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

Die **ObjectSpawner** verwendet die **ColorPickerWheel** zum Festlegen der Farbe des Materials für die des Anzeigeobjekts. Erzeugten Objekte werden bei einer Instanz der in diesem Material, so sie ihre Farbe behalten.
* **Speichern Sie** der Szene, und klicken Sie auf die **spielen** Schaltfläche.

Sie werden die Objekte mit der Schaltfläche "verstehen" ändern und erzeugen Objekte mit der Schaltfläche auswählen können.

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>Erstellen Sie und Bereitstellen Sie der app, Mixed Reality-Portal
* Wählen Sie in Unity **Datei > Buildeinstellungen**.
* Klicken Sie auf **öffnen Szenen hinzufügen** aktuelle Szene zum Hinzufügen der **Szenen In Build**.
* Klicken Sie auf **Erstellen**.
* Erstellen Sie eine **neuer Ordner** mit dem Namen "App".
* Mausklick die **App** Ordner.
* Klicken Sie auf **Ordner auswählen**.
* Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.
* Öffnen der **App** Ordner.
* Doppelklick **YourSceneName.sln** Visual Studio-Projektmappendatei.
* Verwenden obere auf der Symbolleiste in Visual Studio, ändern Sie das Ziel vom Debugmodus in den **Version** und ARM, **X64**.
* Klicken Sie auf den Dropdownpfeil neben der Schaltfläche "Geräte", und wählen **lokalen Computer**.
* Klicken Sie auf **Debuggen -> Starten ohne debugging** in das Menü, oder drücken Sie **STRG + F5**.

Die app wird jetzt erstellt und in Mixed Reality-Portal installiert. Sie können es erneut über das Menü "Start" in Mixed Reality-Portal starten.

## <a name="advanced-design---brush-tools-with-radial-layout"></a>Erweiterte Design - Pinsel Tools mit radialen layout

![MixedReality213 Main](images/mr213-main-600px.jpg)

In diesem Kapitel lernen Sie, wie das Standardmodell für Controller während der Übertragung durch eine Auflistung der benutzerdefinierten Pinsel-Tool ersetzt. Zu Referenzzwecken finden Sie die vollständige Szene **MixedReality213Advanced** unter **Szenen** Ordner.

### <a name="instructions"></a>Anweisungen

* In der **Projekt** geben **BrushSelector** in das Suchfeld. Sie finden ihn außerdem unter Assets/AppPrefabs /
* Ziehen Sie die **BrushSelector** prefab in die **Hierarchie** Bereich.
* Für die Organisation, erstellen Sie ein leeres GameObject, dem Namen **Pinsel**
* Ziehen Sie folgende Prefabs aus der **Projekt** -Bereich in **Pinsel**
    * Assets/AppPrefabs/**BrushFat**
    * Assets/AppPrefabs/**BrushThin**
    * Assets/AppPrefabs/**Eraser**
    * Assets/AppPrefabs/**MarkerFat**
    * Assets/AppPrefabs/**MarkerThin**
    * Assets/AppPrefabs/**Pencil**

![Pinsel](images/mixedreality213-brushes-250px.png)
* Klicken Sie auf **MotionControllers** prefab in die **Hierarchie** Bereich.
* In der **Inspektor** Bereich, deaktivieren Sie **immer alternative rechts Modell** auf die **Motion-Controller-Schnellansicht**
* In der **Hierarchie** auf **BrushSelector**
* **BrushSelector** verfügt über ein Feld mit dem Namen **ColorPicker**
* Von der **Hierarchie** ziehen Sie die **ColorPickerWheel** in **ColorPicker** -Feld in der **Inspektor** Bereich.

![Weisen Sie ColorPickerWheel zu Selektor Pinsel](images/mr213-brushselector-500px.jpg)
* In der **Hierarchie** Bereich unter **BrushSelector** prefab, wählen die **Menü** Objekt.
* In der **Inspektor** Bereich unter der **LineObjectCollection** Komponente, öffnen die **Objekte** Array-Dropdownliste. Sie sehen, dass 6 leere Steckplätze.
* Von der **Hierarchie** ziehen Sie jede der Prefabs übergeordnetes Element besitzt, klicken Sie unter den **Pinsel** "gameobject" in diesen Slots in beliebiger Reihenfolge. (Stellen Sie sicher, dass Sie den prefabs (Vorlagen) von der Szene nicht den Prefabs im Projektordner ziehen können.)

![Pinsel-Auswahl](images/mr213-brushselectorbrushes-700px.jpg)

**BrushSelector prefabs**

Da die **BrushSelector** erbt **AttachToController**, es zeigt **Händigkeit** und **Element** "Optionen" der  **Inspector** Bereich. Ausgewählten **rechts** und **zeigt darstellen** Pinsel Tools an den rechten-Controller mit vorwärts angefügt.

Die **BrushSelector** verwendet zwei Hilfsprogramme:
* **Ellipse**: verwendet, um Punkte im Raum auf eine Form "Ellipse" zu generieren.
* **LineObjectCollection**: verteilt die Objekte, die mit den Punkten, die von jeder Zeile-Klasse (z.B. "Ellipse") generiert. Dies ist, was wir verwenden unsere Pinsel auf die Form "Ellipse" zu platzieren.

In Kombination können diese Hilfsprogramme verwendet werden, zum Erstellen eines radialen Menüs.

**LineObjectCollection-Skript**

**LineObjectCollection** verfügt über Steuerelemente für die Größe, Position und Drehung der Objekte, die entlang der Zeile verteilt. Dies ist nützlich zum Erstellen von radialen Menüs wie das Pinsel-Selektor. Erstellen Sie die Darstellung der Pinsel, Skalierung Einrichten von nothing, wie sie die Position Center ausgewählt Ansatz der **ObjectScale** Spitzen in den Mittelpunkt und den Rändern an den Kanten-Kurve.

**BrushSelector-Skript**

Im Fall von der **BrushSelector**, haben wir uns entschieden, prozedurale Animation verwenden. Zunächst Pinsel Modelle in einer Ellipse durch verteilt werden die **LineObjectCollection** Skript. Klicken Sie dann jeden Pinsel ist verantwortlich für die Verwaltung der Position des Benutzers verfügen, die basierend auf dessen **"DisplayMode"** -Wert, der Änderungen, auf der Auswahl basiert. Wir haben uns ein prozedurales Verfahren für die hohe Wahrscheinlichkeit von Übergängen an Position Pinsel wird unterbrochen, da der Benutzer Brushes auswählt. Mecanim Animationen können Unterbrechungen ordnungsgemäß behandeln, aber dies eher zu viel komplizierter ist als ein einfacher Lerp Vorgang sein.

**BrushSelector** verwendet eine Kombination aus beidem. Wenn Touchpad Eingabe erkannt wird, wird Pinseloptionen sichtbar und zentrales hochskalieren auf das Menü "radial". Nach Ablauf eines Timeouts (dies besagt, dass der Benutzer eine Auswahl getroffen hat)-Optionen der Pinsel skalieren nach unten in diesem Fall nur den ausgewählten Pinsel verlassen.

**Visualisieren von Touchpad-Eingabe**

Selbst in Fällen, in dem das Controllermodell vollständig ersetzt wurde, kann es hilfreich sein, auf die ursprünglichen modelleingaben Eingabe angezeigt sein. Dadurch wird die Aktionen des Benutzers in der Praxis erden. Für die **BrushSelector** haben wir uns entschieden, machen Sie das Touchpad kurz sichtbar, wenn die Eingabe empfangen wird. Dies erfolgte durch Abrufen des Touchpad-Elements aus dem Controller, und Ersetzen Sie dabei mit einem benutzerdefinierten Material, dessen Material, und klicken Sie dann das Anwenden eines Farbverlaufs des Materials Farbe basierend auf der letzten Zeit Touchpad Eingabe empfangen wurde.

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

**Pinsel-Tool-Auswahl mit Touchpad-Eingabe**

Wenn der Selektor Pinsel Touchpad des gedrückten Eingabe erkennt, wird die Position der Eingabe um festzustellen, ob sie nach links oder rechts wurde überprüft.

**Strichstärke mit selectPressedAmount**

Statt die **InteractionSourcePressType.Select** Ereignis in der **InteractionSourcePressed()**, erhalten Sie den analogen Wert, der den gedrückten Betrag über **SelectPressedAmount**. Dieser Wert kann abgerufen werden, **InteractionSourceUpdated()**.

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

**Radierer-Skript**

**Radierer** ist ein spezieller Typ des Pinsels, die die Basis überschreibt **Pinsel**des **DrawOverTime()** Funktion. Beim Zeichnen auf "true" festgelegt ist, überprüft der Radierer, um festzustellen, ob die QuickInfo mit vorhandenen Pinselstriche überschneidet. Wenn Ja, sind sie an eine Warteschlange, die nach-unten verkleinert werden hinzugefügt und gelöscht werden.

## <a name="advanced-design---teleportation-and-locomotion"></a>Erweiterte Design - Teleportation und locomotion

Wenn Sie zulassen möchten, den Benutzer mit Teleportation Ministick mithilfe der Szene verschieben, verwenden Sie **MixedRealityCameraParent** anstelle von **MixedRealityCamera**. Sie müssen auch hinzufügen **InputManager** und **DefaultCusor**. Da **MixedRealityCameraParent** enthält bereits **MotionControllers** und **Grenze** als untergeordneten Komponenten, entfernen Sie vorhandene  **MotionControllers** und **Umgebung** prefab.

### <a name="instructions"></a>Anweisungen

* In der **Hierarchie** panel, löschen Sie **MixedRealityCamera**, **Umgebung** und **MotionControllers**
* Von der **Projektfenster**, suchen, und ziehen Sie die folgenden prefabs (Vorlagen) in der **Hierarchie** Bereich:
    * Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**
    * Assets/AppPrefabs/Input/Prefabs/**InputManager**
    * Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**

![Die Kamera übergeordneten Mixed Reality](images/mr213-cameraparent-300px.png)
* In der **Hierarchie** auf **Eingabe-Manager**
* In der **Inspektor** panel, führen Sie einen Bildlauf nach unten, um die **einfache einfache Auswahl der Zeiger** Abschnitt
* Von der **Hierarchie** ziehen Sie **DefaultCursor** in **Cursor** Feld

![Zuweisen von DefaultCursor](images/mr213-defaultcursor-500px.png)
* **Speichern Sie** der Szene, und klicken Sie auf die **spielen** Schaltfläche. Sie werden Ministick verwenden, um Links/rechts bzw. Teleport zu drehen.

## <a name="the-end"></a>Das Ende

Und das Ende dieses Tutorials ist! Sie haben Folgendes gelernt:
* Verwendung von Motion-Controller-Modellen in Unity Spielmodus und Common Language Runtime.
* Wie Sie verschiedene Typen von Schaltflächenereignisse und ihren Anwendungen verwenden.
* Gewusst wie overlay-Elemente der Benutzeroberfläche auf dem Controller oder vollständig anpassen.

Sie können nun damit beginnen, erstellen eigene beeindruckende Erfahrung mit Motion-Controller.

## <a name="completed-scenes"></a>Abgeschlossene Szenen

* In Unity **Projekt** Bereich, klicken Sie auf die **Szenen** Ordner.
* Sehen Sie zwei Unity Sceens **MixedReality213** und **MixedReality213Advanced**.
    * **MixedReality213**: Vollständige Szene mit einzelnen Pinsel
    * **MixedReality213Advanced**: Vollständige Szene mit mehreren Pinsel, mit der Schaltfläche auswählen, drücken Sie Betrag-Beispiel

## <a name="see-also"></a>Siehe auch

* [MR Eingabe 213-Projektdateien](https://github.com/Microsoft/MixedReality213)
* [Mixed Reality-Toolkit - Motion-Controller-Test-Szene](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [Ziehen Sie Mixed Reality-Toolkit – Funktionsweise](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [Richtlinien für die Entwicklung von Motion-controller](motion-controllers.md)
