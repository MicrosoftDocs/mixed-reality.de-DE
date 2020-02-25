---
title: 'Tutorials zu den ersten Schritten: 3. Erstellen einer Benutzeroberfläche und Konfigurieren von Mixed Reality Toolkit'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: f1d042150d1c81940e672b174c6c02ac71e05883
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554881"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. Erstellen einer Benutzeroberfläche und Konfigurieren von Mixed Reality Toolkit
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

Im vorherigen Tutorial haben Sie einige Funktionen kennengelernt, die das Mixed Reality Toolkit (mrtk) bietet, indem Sie Ihre erste Anwendung für die hololens 2 starten. In diesem Tutorial erfahren Sie, wie Sie Schaltflächen zusammen mit UI-Textbereichen erstellen und organisieren und die Standard Interaktion (Toucheingabe) verwenden, um mit den einzelnen Schaltflächen zu interagieren. Sie werden auch das Hinzufügen einfacher Aktionen und Effekte untersuchen, z. B. das Ändern von Größe, Klang und Farbe von Objekten. Dieses Modul führt grundlegende Konzepte zum Ändern von mrtk-Profilen ein, beginnend mit dem Ausschalten der Mesh-Visualisierung für [räumliche Karten](spatial-mapping.md) .

## <a name="objectives"></a>Ziele

* Anpassen und Konfigurieren von Mixed Reality-Toolkitprofilen
* Interagieren mit holograms mithilfe von Benutzeroberflächen Elementen und Schaltflächen
* Grundlegende Eingaben und Interaktionen zum Handtracking

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>So konfigurieren Sie die Mixed Reality Toolkit-profile (Anzeige Option ' räumliches Bewusstsein ändern ')
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

In diesem Abschnitt erfahren Sie, wie die standardmäßigen mrtk-Profile angepasst und konfiguriert werden.

In diesem speziellen Beispiel wird veranschaulicht, wie das räumliche Awareness-Mesh ausgeblendet wird, indem die Einstellungen des räumlichen Mesh-Beobachters geändert werden. Sie können jedoch dieselben Prinzipien befolgen, um beliebige Einstellungen oder Werte in den mrtk-Profilen anzupassen.

Die wichtigsten Schritte, die Sie ausführen, um das räumliche Awareness-Mesh auszublenden, sind:

1. Standard Konfigurations Profil Klonen
2. Aktivieren des Systems für räumliche Informationen
3. Klonen des standardmäßigen Spatial Awareness System-Profils
4. Klonen des standardmäßigen Spatial Awareness Mesh-Profils
5. Ändern der Sichtbarkeit des Netzes für räumliche Informationen

> [!NOTE]
> Standardmäßig können die MRTK-Profile nicht bearbeitet werden. Dabei handelt es sich um Standardprofil Vorlagen, die Sie Klonen müssen, bevor Sie bearbeitet werden können. Es gibt mehrere unterschiedliche Ebenen von Profilen. Daher ist es üblich, mehrere Profile zu klonen und zu bearbeiten, wenn eine oder mehrere Einstellungen konfiguriert werden.

### <a name="1-clone-the-default-configuration-profile"></a>1. Klonen Sie das Standard Konfigurations Profil.

> [!NOTE]
> Das Konfigurations Profil ist das Profil der obersten Ebene. Daher müssen Sie zunächst das Konfigurations Profil Klonen, um andere Profile bearbeiten zu können.

Wenn das **mixedrealitytoolkit** -Objekt im Fenster Hierarchie ausgewählt ist, ändern Sie im Inspektor-Fenster das Mixed Reality Toolkit- **Konfigurations Profil** in **DefaultHoloLens2ConfigurationProfile**:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

Wenn das **mixedrealitytoolkit** -Objekt noch ausgewählt ist, klicken Sie im Inspektor-Fenster auf die Schaltfläche zum **Kopieren & anpassen** , um das Fenster Klon Profil zu öffnen:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

Klicken Sie im Fenster Klon Profil auf die Schaltfläche **Klonen** , um eine bearbeitbare Kopie des **DefaultHololens2ConfigurationProfile**zu erstellen:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

Das neu erstellte Konfigurations Profil ist nun als Konfigurations Profil für Ihre Szene zugewiesen:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

Wählen Sie im Unity-Menü **Datei** > **Speichern** aus, um die Szene zu speichern.

> [!TIP]
> Denken Sie daran, ihre Arbeit im gesamten Tutorial zu speichern.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Aktivieren des Systems für räumliche Informationen

Wenn das **mixedrealitytoolkit** -Objekt noch im Fenster Hierarchie ausgewählt ist, wählen Sie im Inspektor-Fenster die Registerkarte **räumliches Bewusstsein** aus, und aktivieren Sie dann das Kontrollkästchen **räumliches Awareness System aktivieren** :

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Klonen des standardmäßigen Spatial Awareness System-Profils

Klicken Sie auf der Registerkarte **räumliches Bewusstsein** auf die Schaltfläche **Klonen** , um das Fenster Klon Profil zu öffnen:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

Klicken Sie im Fenster Klon Profil auf die Schaltfläche **Klonen** , um eine bearbeitbare Kopie von **defaultmixedrealityspatialawarenesssystemprofile**zu erstellen:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

Das neu erstellte Spatial Awareness System-Profil wird nun automatisch Ihrem Konfigurations Profil zugewiesen:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Klonen Sie das standardmäßige räumliche Awareness Mesh Observer-Profil.

Wenn die Registerkarte **räumliches Bewusstsein** weiterhin ausgewählt ist, erweitern Sie den Abschnitt **Windows Mixed Reality Spatial Mesh Observer** , und klicken Sie dann auf die Schaltfläche **Klonen** , um das Fenster Klon Profil zu öffnen:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

Klicken Sie im Fenster Klon Profil auf die Schaltfläche **Klonen** , um eine bearbeitbare Kopie von **defaultmixedrealityspatialawareness meshobserverprofile**zu erstellen:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

Das neu erstellte Spatial Awareness Mesh-Profil wird nun automatisch Ihrem Spatial Awareness System-Profil zugewiesen:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Ändern der Sichtbarkeit des Netzes für räumliche Informationen

Ändern Sie in den **Einstellungen für räumliche Gitter Beobachter**die **Anzeige Option** in " **oksion** ", damit das räumliche Zuordnungs Netz unsichtbar bleibt, während es funktionsfähig ist:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> Obwohl das Mesh für räumliche Zuordnung nicht sichtbar ist, ist es immer noch vorhanden und funktionsfähig. Beispielsweise werden alle holograms hinter dem räumlichen zuordnungsmesh, z. b. ein Hologramm hinter einer physischen Wand, nicht sichtbar.

Sie haben soeben erfahren, wie Sie eine Einstellung im MRTK-Profil ändern können. Wie Sie sehen können, müssen Sie zunächst Kopien der Standardprofile erstellen, um die mrtk-Einstellungen anzupassen. Da die Standardprofile nicht bearbeitbar sind, haben Sie Sie immer als Verweis, wenn Sie die Standardeinstellungen wiederherstellen möchten. Weitere Informationen zu mrtk-Profilen und deren Architektur finden Sie im Handbuch für die [Konfiguration des Mixed Reality Toolkit-Profils](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) im [mrtk-Dokumentations Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="hand-tracking-gestures-and-interactable-buttons"></a>Hand Verfolgungs Gesten und austauschbare Schaltflächen

In diesem Abschnitt erfahren Sie, wie Sie mithilfe der Hand Überwachung eine Schaltfläche drücken und Ereignisse auslösen, um eine Aktion auszulösen, wenn die Schaltfläche gedrückt wird.

In diesem speziellen Beispiel wird gezeigt, wie Sie die Farbe eines Cubes ändern, wenn die Schaltfläche gedrückt wird, und die Farbe zurück in die ursprüngliche Farbe ändern, wenn die Schaltfläche losgelassen wird. Sie können jedoch dieselben Prinzipien befolgen, um andere Ereignisse zu erstellen.

Die wichtigsten Schritte, die Sie ausführen müssen, um die Farbe des Cubes zu ändern, sind:

1. Fügen Sie der Szene eine Schaltfläche für die Druck Bare Schaltfläche hinzu.
2. Hinzufügen eines Cubes zur Szene
3. Konfigurieren des interactableonpressreceiver-Ereignis Typs
4. Cube so konfigurieren, dass das on Press-Ereignis empfangen wird
5. Hiermit wird die Aktion definiert, die vom on Press-Ereignis ausgelöst werden soll.
6. Konfigurieren des Cubes, um das on-Release-Ereignis zu empfangen
7. Hiermit wird die Aktion definiert, die vom on-Release-Ereignis ausgelöst wird.
8. Testen der Schaltfläche mithilfe der in-Editor-Simulation

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a>1. Fügen Sie der Szene eine Schaltfläche für die Druck Bare Schaltfläche hinzu.

> [!TIP]
> Bei einem <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Prefab</a> handelt es sich um ein vorkonfiguriertes gameobject-Objekt, das als Unity-Medienobjekt gespeichert und im gesamten Projekt wieder verwendet werden kann

Suchen Sie im **Projektfenster**nach **PressableButtonHoloLens2** , um das in diesem Beispiel verwendete präfab zu finden:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

Wählen Sie im **Such** Ergebnis **PressableButtonHoloLens2** Prefab aus, und **ziehen** Sie es in das **Hierarchie** Fenster, um es Ihrer Szene hinzuzufügen:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> Zum Anzeigen der Szene, wie in der folgenden Abbildung dargestellt, doppelklicken Sie auf das PressableButtonHoloLens2-Objekt im Hierarchie Fenster, um es in den Fokus zu bringen, und verwenden Sie dann die <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Szene Gizmo</a>in der oberen rechten Ecke des Fensters Szene, um den Anzeige Winkel an der vorwärts-Z-Achse anzupassen.

Wenn das **PressableButtonHoloLens2** -Objekt noch ausgewählt ist, im **Inspektor** -Fenster:

* Ändern Sie die **Position** der Transformation, sodass Sie vor der Kamera positioniert ist, die am Ursprung positioniert ist, z. b. x = 0, y = 0 und z = 0,5.

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> Im Allgemeinen entspricht eine Positions Einheit in Unity ungefähr 1 Meter in der physischen Welt. Es gibt jedoch Ausnahmen, z. b. wenn Objekte untergeordnete Elemente von skalierten Objekten sind.

### <a name="2-add-a-cube-to-the-scene"></a>2. Hinzufügen eines Cubes zur Szene

Klicken Sie mit der rechten Maustaste auf eine leere Stelle innerhalb des Hierarchie Fensters, und wählen Sie **3D-Objekt** > **Cube** aus, um Ihrer Szene einen Cube hinzuzufügen:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

Wenn das **Cube** -Objekt noch ausgewählt ist, im **Inspektor** -Fenster:

* Ändern Sie die Transformations **Position** , sodass Sie sich in der Nähe der druckbaren Schaltfläche befindet, aber nicht mit der Schaltfläche, wie z. b. x = 0, y = 0,04 und z = 0,5.
* Ändern Sie die Transformations **Skala** in eine passende Größe, z. b. x = 0,02, y = 0,02 und z = 0,02.

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a>3. Konfigurieren des interactableonpressreceiver-Ereignis Typs

Wählen Sie im Fenster Hierarchie das **PressableButtonHoloLens2** -Objekt aus, und wählen Sie dann im Fenster **Hamburger**des **Inspektorfensters** die Option **alle Komponenten** reduzieren aus, um einen Überblick über alle Komponenten auf diesem Objekt zu erhalten:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

Erweitern Sie die Komponente **interactable (Skript)** , suchen Sie den Abschnitt **Ereignisse** > **Empfänger** , und erweitern Sie ihn:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

Klicken Sie auf die Schaltfläche **Ereignis hinzufügen** , um einen neuen Ereignis Empfänger vom Ereignis Empfängertyp **interactableonpressreceiver**zu erstellen:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> Der ereignisempfängertyp mit dem Namen interactableonpressreceiver ermöglicht der Schaltfläche, auf ein gedrücktes Ereignis zu reagieren, wenn eine nach verfolgte Seite die Schaltfläche drückt

Ändern Sie für den neu erstellten Ereignis Empfänger den **Interaktions Filter** in **Near und Far**:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a>4. Konfigurieren Sie den Cube, um das on Press-Ereignis zu empfangen.

Klicken Sie im Fenster Hierarchie auf den **Cube** , **und ziehen Sie** ihn in das Feld **Ereignis Eigenschaften** Objekt für das **on Press ()** -Ereignis, um den Cube als Empfänger des on Press ()-Ereignisses zuzuweisen:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a>5. definieren Sie die Aktion, die vom on Press-Ereignis ausgelöst werden soll.

Klicken Sie auf die Dropdown Liste Aktion, die zurzeit **keine Funktion**zugewiesen ist, und wählen Sie **meshrenderer** > **Material Material** aus, um festzulegen, dass die Eigenschaft des Cubes geändert wird, wenn das on Press ()-Ereignis ausgelöst wird:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

Klicken Sie auf das kleine **Kreis** Symbol neben dem Feld Material, das zurzeit mit **keine (Material)** aufgefüllt ist, um das Fenstermaterial auswählen zu öffnen:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

**Suchen** Sie im Fenster Material auswählen nach **MRTK_Standard** , und wählen Sie ein geeignetes Material aus, z. b. **MRTK_Standard_Cyan** , damit die Farbe des Cubes in Zyan geändert wird, wenn die Schaltfläche gedrückt wird:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a>6. Konfigurieren Sie den Cube für den Empfang des on-Release-Ereignisses.

**Wiederholen** Schritt 4 für das on-Release-Ereignis, um den **Cube** als Empfänger des **on-Release ()** -Ereignisses zuzuweisen.

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a>7. definieren Sie die Aktion, die vom on-Release-Ereignis ausgelöst werden soll.

**Wiederholen** Schritt 5 für das on-Release-Ereignis, aber wählen Sie das **MRTK_Standard_LightGray** Material aus, damit die Farbe des Cubes bei der Freigabe der Schaltfläche in die ursprüngliche helle graue Farbe zurückkehrt:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a>8. Testen der Schaltfläche mithilfe der in-Editor-Simulation

Klicken Sie auf die **Wiedergabe** Schaltfläche, um den Spielmodus einzugeben, und testen Sie die neu konfigurierte Schaltfläche mit der Eingabe Simulation im Editor.

Schaltfläche nicht gedrückt (Leertaste + Mausrad rückwärts):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

Gedrückte Schaltfläche (Leertaste + Mausrad nach oben):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> Weitere Informationen zur Verwendung der in-Editor-Eingabe Simulation finden Sie unter [Verwenden der in-Editor-Hand Eingabe Simulation zum Testen eines Szenen](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) Handbuchs im [mrtk-Dokumentations Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Erstellen eines Schaltflächenbereichs mit der MRTK-Rasterobjektsammlung

In diesem Abschnitt erfahren Sie, wie Sie mehrere Schaltflächen mithilfe des Raster Objekt Auflistungs Tools von mrtk automatisch an einer Benutzeroberfläche anpassen.

In diesem speziellen Beispiel wird gezeigt, wie ein Panel mit fünf Schaltflächen, die horizontal ausgerichtet sind, erstellt wird. Sie können jedoch dieselben Prinzipien befolgen, um andere Layouts zu erstellen.

Dies sind die wichtigsten Schritte, die Sie durchführen müssen:

1. Übergeordnete Schaltflächen Objekte zu einem übergeordneten Objekt
2. Hinzufügen und Konfigurieren der Komponente "Raster Objekt Auflistung (Skript)"
3. Testen der Schaltflächen mithilfe der in-Editor-Simulation

### <a name="1-parent-the-button-objects-to-a-parent-object"></a>1. übergeordnete Schaltflächen Objekte zu einem übergeordneten Objekt

Klicken Sie im Hierarchie Fenster mit der rechten Maustaste auf eine leere Stelle, und wählen Sie **leere erstellen**aus:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

Klicken Sie mit der rechten Maustaste auf das neu erstellte Objekt, wählen Sie **Umbenennen**aus, und geben Sie ihm einen passenden Namen, z. b. **buttoncollection**:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

Wählen Sie das **PressableButtonHoloLens2** -Objekt aus, und **ziehen** Sie es über das **buttoncollection** -Objekt, um es zu einem untergeordneten Element des buttoncollection-Objekts zu machen:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

Klicken Sie mit der rechten Maustaste auf das **PressableButtonHoloLens2** -Objekt, und wählen Sie **Duplizieren** aus, um eine Kopie der

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

**Wiederholen** Sie diesen Schritt vier weitere Male, bis Sie über insgesamt fünf PressableButtonHoloLens2-Objekte verfügen.

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. hinzufügen und Konfigurieren der Raster Objekt-Sammlungs Komponente (Skript)

Wenn das buttoncollection-Objekt im Fenster Hierarchie ausgewählt ist, klicken Sie im Inspektor-Fenster auf die Schaltfläche **Komponente hinzufügen** , suchen Sie nach der **Raster Objekt** Auflistung, und wählen Sie Sie aus, um dem buttoncollection-Objekt eine Komponente für die Raster Objekt Auflistung (Skript) hinzuzufügen:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

Konfigurieren Sie die Raster Objekt Auflistung (Skript) wie folgt:

* Ändern von **num-Zeilen** in 1, damit alle Schaltflächen auf einer einzelnen Zeile ausgerichtet sind
* Ändern Sie die **Zellen Breite** in 0,05, um die Schaltflächen innerhalb der Zeile leer zu setzen.

Klicken Sie dann auf die Schaltfläche **Sammlung aktualisieren** , um die neue Konfiguration zu übernehmen:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> Die soeben angewendeten Konfigurationsänderungen stellen die minimalen Änderungen dar, die erforderlich sind, um das Ziel zu erreichen, die Schaltflächen in einer einzelnen Zeile zu platzieren. Allerdings müssen Sie in zukünftigen Projekten, abhängig von Faktoren wie z. b. der Ausrichtung der über-und untergeordneten Objekte, möglicherweise andere Einstellungen anpassen, z. b. den Typ "Typ". Weitere Informationen zur Raster Objekt Auflistung von mrtk finden Sie im Handbuch zur [Erfassung von Objekt](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) Auflistungen im [mrtk-Dokumentations Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

Wenn das buttoncollection-Objekt noch im Fenster Hierarchie ausgewählt ist, ändern Sie im Inspektor-Fenster die Transformations **Position** des buttoncollection-Objekts, sodass die untergeordneten Schaltflächen Objekte vor der Kamera positioniert werden, die am Ursprung positioniert ist, z. b. x = 0, y = 0 und z = 0,5:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> Beim ersten Hinzufügen von PressableButtonHoloLens2 Prefab zur Szene im obigen Abschnitt [Hand Tracking Gesten und Interaktionen Buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) positionierte Sie diese vor der Kamera. Da die Raster Objekt Auflistung jedoch die Position der unmittelbaren untergeordneten Objekte steuert, wurden die Z-Position der untergeordneten Objekte PressableButtonHoloLens2 entsprechend der Standard Entfernung der Raster Objekt Auflistung vom übergeordneten Wert 0 auf 0 zurückgesetzt. Und damit die Beziehungen zwischen übergeordneten und untergeordneten Elementen organisiert bleiben, wird die Position des übergeordneten buttoncollection-Objekts verschoben, anstatt den Abstand vom übergeordneten Wert zu konfigurieren, um die untergeordneten PressableButtonHoloLens2-Objekte vorwärts zu verschieben.

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a>3. Testen der Schaltflächen mithilfe der in-Editor-Simulation

Klicken Sie auf die Wiedergabe Schaltfläche, um den Spielmodus einzugeben, und verwenden Sie die Eingabe Simulation im Editor, um die einzelnen Schaltflächen in dem neu erstellten Panel von Schaltflächen zu testen:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> Wenn Sie derzeit eine der fünf Schaltflächen drücken, wird die Würfel Farbe in Cyan geändert. Um die Darstellung interessanter zu gestalten, verwenden Sie das, was Sie gerade lernen, um die einzelnen Schaltflächen zu konfigurieren, um den Cube in eine andere Farbe zu ändern.

## <a name="adding-text-into-your-scene"></a>Hinzufügen von Text in Ihrer Szene

In diesem Abschnitt erfahren Sie, wie Sie mithilfe von "textmesh pro", die Sie im Abschnitt " [Importieren von textmesh pro Essentials Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) " im vorherigen Tutorial vorbereitet haben, Text zu ihren Mixed Reality-Umgebungen hinzufügen.

In diesem speziellen Beispiel fügen Sie unterhalb der Schaltflächen Auflistung, die Sie im vorherigen Abschnitt erstellt haben, eine einfache Bezeichnung hinzu.

Klicken Sie mit der rechten Maustaste auf das buttoncollection-Objekt, und wählen Sie **3D-Objekt** > **Text-textmeshpro** aus, um ein textmeschpro-Objekt als untergeordnetes Element des buttoncollection-Objekts zu erstellen:

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

Wenn das neu erstellte textmeshpro-Objekt, benannter Text (tmp), noch ausgewählt ist, ändern Sie im Inspektor-Fenster seine Position und Größe so, dass die Bezeichnung sauber unterhalb der Schaltflächen Auflistung platziert wird, z. b.:

* Ändern der Rect-Transformation **Torys Y** in-0,0425
* Ändern Sie die **Breite** der Rect-Transformation in 0,24.
* Ändern Sie die **Höhe** der Rect-Transformation in 0,024.

Aktualisieren Sie dann den Text, um die Bezeichnung der Bezeichnung widerzuspiegeln, und wählen Sie Schriftart Eigenschaften aus, damit der Text in die Bezeichnung passt, z. b.:

* Textmesh pro- **Text** (Skript) in Schaltflächen Auflistung ändern
* Ändern Sie den Text Mesh pro- **Schrift** Schnitt (Skript) in "Fett".
* Ändern Sie den **Schrift** Grad Text Mesh pro (Skript) in 0,2.
* Ändern der **Ausrichtung** von Text Mesh pro (Skript) in Mitte und Mitte

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie erfahren, wie Sie eine mrtk-Profileinstellung Klonen, anpassen und konfigurieren. Außerdem haben Sie erfahren, wie Sie mit Schaltflächen interagieren, um Ereignisse mithilfe von nach verfolgten Händen in den hololens 2 zu Triggern 2 Schließlich haben Sie erfahren, wie Sie eine einfache UI-Schnittstelle mithilfe der Raster Objekt Auflistungs Komponente von mrtk und des Text Mesh pro von Unity erstellen.

[Nächstes Tutorial: 4. Platzieren von dynamischem Inhalt und Verwenden von Solvers](mrlearning-base-ch3.md)
