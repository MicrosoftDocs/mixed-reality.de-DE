---
title: 'Tutorials zu den ersten Schritten: 3 Erstellen der Benutzeroberfläche und Konfigurieren des Mixed Reality-Toolkits'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: c389c7a3d16770dcbf57d9acdcfd81c6507f7cd6
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376137"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. Erstellen der Benutzeroberfläche und Konfigurieren des Mixed Reality-Toolkits
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

Im vorherigen Tutorial haben Sie einige der Funktionen kennengelernt, die das Mixed Reality Toolkit (MRTK) bietet, indem Sie Ihre erste Anwendung für die HoloLens 2 gestartet haben. In diesem Tutorial erfahren Sie, wie Sie Schaltflächen zusammen mit den Textbereichen der Benutzeroberfläche erstellen und organisieren und mithilfe der Standardinteraktion (Berühren) mit den einzelnen Schaltflächen interagieren. Sie werden auch das Hinzufügen einfacher Aktionen und Effekte untersuchen, z. B. das Ändern von Größe, Klang und Farbe von Objekten. In diesem Modul werden grundlegende Konzepte zum Ändern von MRTK-Profilen vorgestellt, beginnend mit dem Deaktivieren der Darstellung des Gittermodells zur [räumlichen Abbildung](spatial-mapping.md).

## <a name="objectives"></a>Ziele

* Anpassen und Konfigurieren von Mixed Reality-Toolkitprofilen
* Interagieren mit Hologrammen über Elemente und Schaltflächen der Benutzeroberfläche
* Grundlegende Eingaben und Interaktionen zum Handtracking

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Konfigurieren der Mixed Reality-Toolkitprofile (Option zum Ändern der Anzeige der räumlichen Wahrnehmung)
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

In diesem Abschnitt erfahren Sie, wie die standardmäßigen MRTK-Profile angepasst und konfiguriert werden.

Dieses Beispiel veranschaulicht insbesondere, wie das Gittermodell zur räumlichen Wahrnehmung durch Ändern der Einstellungen des Betrachters für räumliche Gittermodelle ausgeblendet wird. Jedoch können Sie dieselben Prinzipien befolgen, um beliebige Einstellungen oder Werte in den MRTK-Profilen anzupassen.

Dies sind die wichtigsten Schritte, die Sie ausführen, um das Gittermodell zur räumlichen Wahrnehmung auszublenden:

1. Klonen des Standardkonfigurationsprofils
2. Aktivieren des Systems für räumliche Wahrnehmung
3. Klonen des Standardprofils des Systems für räumliche Wahrnehmung
4. Klonen des Standardprofils des Betrachters für räumliche Gittermodelle
5. Ändern der Sichtbarkeit des Gittermodells zur räumlichen Wahrnehmung

> [!NOTE]
> Standardmäßig können die MRTK-Profile nicht bearbeitet werden. Es handelt sich um Standardprofilvorlagen, die Sie zuerst klonen müssen, um sie bearbeiten zu können. Es gibt mehrere verschachtelte Profilebenen. Es ist daher gängige Praxis, mehrere Profile zu klonen und zu bearbeiten, wenn Einstellungen konfiguriert werden sollen.

### <a name="1-clone-the-default-configuration-profile"></a>1. Klonen des Standardkonfigurationsprofils

> [!NOTE]
> Das Konfigurationsprofil ist das Profil der obersten Ebene. Folglich müssen Sie, um andere Profile bearbeiten zu können, zuerst das Konfigurationsprofil klonen.

Ändern Sie bei im Hierarchiefenster ausgewähltem **MixedRealityToolkit**-Objekt im Inspektorfenster das **Konfigurationsprofil** des Mixed Reality-Toolkits in **DefaultHoloLens2ConfigurationProfile**:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

Klicken Sie mit immer noch ausgewähltem **MixedRealityToolkit**-Objekt im Inspektor-Fenster auf die Schaltfläche **Copy & Customize** (Kopieren und Anpassen), um das Fenster „Clone Profile“ (Profil klonen) zu öffnen:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

Klicken Sie im Fenster „Clone Profile“ auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie des Profils **DefaultHololens2ConfigurationProfile** zu erstellen:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

Das neu erstellte Konfigurationsprofil wird jetzt als Konfigurationsprofil für Ihre Szene zugewiesen:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

Wählen Sie im Unity-Menü **File** > **Save** (Datei > Speichern) aus, um Ihre Szene zu speichern.

> [!TIP]
> Denken Sie daran, Ihre Arbeit während des Tutorials zu speichern.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Aktivieren des Systems für räumliche Wahrnehmung

Wählen Sie bei immer noch im Hierarchiefenster ausgewähltem **MixedRealityToolkit**-Objekt im Inspektorfenster die Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) aus, und aktivieren Sie dann das Kontrollkästchen **Enable Spatial Awareness System** (System für räumliche Wahrnehmung):

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Klonen Sie das Standardprofil des Systems für räumliche Wahrnehmung

Klicken Sie auf der Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) auf die Schaltfläche **Clone** (Klonen), um das Fenster „Clone Profile“ (Profil klonen) zu öffnen:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

Klicken Sie im Fenster „Clone Profile“ auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie des Profils **DefaultMixedRealitySpatialAwarenessSystemProfile** zu erstellen:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

Das neu erstellte Profil des Systems für räumliche Wahrnehmung wird Ihrem Konfigurationsprofil nun automatisch zugewiesen:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Klonen des Standardprofils des Betrachters für räumliche Gittermodelle

Erweitern Sie bei immer noch ausgewählter Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) den Abschnitt **Windows Mixed Reality Spatial Mesh Observer** (Betrachter für das räumliche Gittermodell von Windows Mixed Reality), und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um das Clone Profile-Fenster (Profil klonen) zu öffnen:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

Klicken Sie im Fenster „Clone Profile“ auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie des Profils **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** zu erstellen:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

Das neu erstellte Profil des Betrachters für das räumliche Gittermodell wird jetzt automatisch Ihrem Profil für das räumliche Wahrnehmungssystem zugewiesen:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Ändern der Sichtbarkeit des Gittermodells zur räumlichen Wahrnehmung

Ändern Sie in den **Spatial Mesh Observer Settings** (Einstellungen des Betrachters für das räumliche Gittermodell) die **Display Option** (Anzeigeoption) in **Occlusion** (Verdeckung), um das Gittermodell zur räumlichen Abbildung unsichtbar zu machen, ohne seine Funktion aufzuheben:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> Das räumliche Gittermodell ist zwar nicht sichtbar, es ist aber trotzdem vorhanden und funktioniert. Beispielsweise sind eventuelle Hologramme hinter dem Gittermodell für die räumliche Abbildung nicht sichtbar, ganz wie ein Hologramm hinter einer physischen Wand.

Sie haben soeben erfahren, wie Sie eine Einstellung im MRTK-Profil ändern können. Wie Sie sehen können, müssen Sie zum Anpassen der MRTK-Einstellungen zuerst Kopien der Standardprofile erstellen. Da die Standardprofile nicht bearbeitbar sind, stehen sie Ihnen jederzeit als Referenz zur Verfügung, wenn Sie zu den Standardeinstellungen zurückkehren möchten. Weitere Informationen zu MRTK-Profilen und ihrer Architektur finden Sie im [Mixed Reality Toolkit-Leitfaden zur Profilkonfiguration](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="hand-tracking-gestures-and-interactable-buttons"></a>Gesten für Hand-Tracking und interaktionsfähige Schaltflächen

In diesem Abschnitt erfahren Sie, wie Sie Hand-Tracking verwenden, um eine Schaltfläche zu drücken und Ereignisse auszulösen, um eine Aktion zu bewirken, wenn die Schaltfläche gedrückt wird.

Diese Beispiel zeigt Ihnen im Einzelnen, wie Sie die Farbe eines Würfels ändern, wenn die Schaltfläche gedrückt wird, und sie wieder zur ursprünglichen Farbe zurück ändern, wenn die Schaltfläche freigegeben wird. Nach den gleichen Prinzipien können Sie aber auch andere Ereignisse erstellen.

Dies sind die wichtigsten Schritte, die Sie ausführen, um die Farbe des Würfels zu ändern:

1. Hinzufügen eines Prefabs für eine drückbare Schaltfläche zur Szene
2. Hinzufügen eines Würfels zur Szene
3. Konfigurieren des InteractableOnPressReceiver-Ereignistyps
4. Konfigurieren des Würfels zum Empfangen des On Press-Ereignisses
5. Definieren der Aktion, die durch das On Press-Ereignis ausgelöst werden soll
6. Konfigurieren des Würfels zum Empfangen des On Release-Ereignisses
7. Definieren der Aktion, die durch das On Release-Ereignis ausgelöst werden soll
8. Testen der Schaltfläche mithilfe der Simulation im Editor

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a>1. Hinzufügen eines Prefabs für eine drückbare Schaltfläche zur Szene

> [!TIP]
> Ein <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Prefab</a> ist ein vorkonfiguriertes GameObject, das als Unity-Ressource gespeichert ist und durchgängig im Projekt verwendet werden kann.

Suchen Sie im **Projektfenster** nach **PressableButtonHoloLens2**, um das Prefab zu finden, das Sie für dieses Beispiel verwenden werden:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

Wählen Sie im Ergebnis der **Suche** das **PressableButtonHoloLens2**-Prefab aus, und **ziehen** Sie es in das **Hierarchiefenster**, um es Ihrer Szene hinzuzufügen:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> Um Ihre Szene so anzuzeigen, wie Sie in der Abbildung unten dargestellt ist, doppelklicken Sie auf das PressableButtonHoloLens2-Objekt im Hierarchiefenster, um es in den Fokus zu bringen, und verwenden Sie dann den <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, der sich in der oberen rechten Ecke des Szenefensters befindet, um den Betrachtungswinkel so anzupassen, dass er entlang der vorwärts gerichteten Z-Achse verläuft.

Führen Sie bei immer noch ausgewähltem **PressableButtonHoloLens2**-Objekt im **Inspektorfenster** folgende Aktion aus:

* Ändern Sie seine **Transformationsposition** so, dass es vor der Kamera platziert ist, die am Ursprung positioniert ist, beispielsweise x = 0, y = 0 und z = 0,5

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> Im Allgemeinen entspricht 1 Positionseinheit in Unity ungefähr einem Meter in der physischen Umgebung. Es gibt jedoch Ausnahmen, z. B. wenn Objekte untergeordnete Objekte von skalierten Objekten sind.

### <a name="2-add-a-cube-to-the-scene"></a>2. Hinzufügen eines Würfels zur Szene

Klicken Sie mit der rechten Maustaste auf einen leeren Bereich innerhalb des Hierarchiefensters, und wählen Sie **3D Object** > **Cube** (3D-Objekt > Würfel) aus, um Ihrer Szene einen Würfel hinzuzufügen:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

Führen Sie bei immer noch ausgewähltem **Cube**-Objekt im **Inspektorfenster** folgende Aktion aus:

* Ändern Sie seine **Transformationsposition** so, dass es sich in der Nähe der drückbaren Schaltfläche befindet, ohne sich mit ihr zu überschneiden, beispielsweise x = 0, y = 0,04 und z = 0,5
* Ändern Sie seinen **Transformationsmaßstab** auf eine passende Größe, beispielsweise x = 0,02, y = 0,02 und z = 0,02

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a>3. Konfigurieren des InteractableOnPressReceiver-Ereignistyps

Wählen Sie im Hierarchiefenster das **PressableButtonHoloLens2**-Objekt und dann im **Hamburger-Menü** des **Inspektorfensters** **Alle Komponenten reduzieren** aus, um eine Übersicht aller Komponenten dieses Objekts zu erhalten:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

Erweitern Sie die Komponente **Interactable (Script)** , und suchen und erweitern Sie dann den Abschnitt **Events** > **Receivers** (Ereignisse > Empfänger):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

Klicken Sie auf die Schaltfläche **Ereignis hinzufügen**, um einen neuen Ereignisempfänger vom Ereignisempfängertyp **InteractableOnPressReceiver** zu erstellen:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> Der Ereignisempfängertyp mit dem Namen InteractableOnPressReceiver ermöglicht es der Schaltfläche, auf ein Drücken-Ereignis zu reagieren, wenn eine nachverfolgte Hand die Schaltfläche drückt.

Ändern Sie für den neu erstellten Ereignisempfänger den **Interaction Filter** (Interaktionsfilter) in **Near and Far** (Nah und fern):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a>4. Konfigurieren des Würfels zum Empfangen des On Press-Ereignisses

**Klicken und ziehen** Sie im Hierarchiefenster den **Würfel** auf das Objektfeld **Event Properties** (Ereigniseigenschaften), damit das **On Press ()** -Ereignis den Würfel als Empfänger des On Press ()-Ereignisses zuweist:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a>5. Definieren der Aktion, die durch das On Press-Ereignis ausgelöst werden soll

Klicken Sie auf das Aktions-Dropdownfeld, dem aktuell **No Function** (Keine Funktion) zugewiesen ist, und wählen Sie **MeshRenderer** > **Material material** aus, um festzulegen, dass die Materialeigenschaft des Würfels geändert wird, wenn das On Press ()-Ereignis ausgelöst wird:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

Klicken Sie auf das kleine **Kreissymbol** neben dem Materialfeld, das zurzeit mit **None (Material)** aufgefüllt ist, um das Fenster „Select Material“ (Material auswählen) zu öffnen:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

**Suchen** Sie im Fenster „Select Material“ (Material auswählen) nach **MRTK_Standard**, und wählen Sie ein passendes Material aus, beispielsweise **MRTK_Standard_Cyan**, damit sich die Farbe des Würfels in Blaugrün ändert, wenn die Schaltfläche gedrückt wird:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a>6. Konfigurieren des Würfels zum Empfangen des On Release-Ereignisses

**Wiederholen** Sie Schritt 4 für das On Release-Ereignis, um den **Würfel** als einen Empfänger des **On Release ()** -Ereignisses festzulegen.

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a>7. Definieren der Aktion, die durch das On Release-Ereignis ausgelöst werden soll

**Wiederholen** Sie Schritt 5 für das On Release-Ereignis, wählen Sie jedoch das **MRTK_Standard_LightGray**-Material aus, damit die Farbe des Würfels beim Freigeben der Schaltfläche zur ursprünglichen hellgrauen Farbe zurückkehrt:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a>8. Testen der Schaltfläche mithilfe der Simulation im Editor

Drücken Sie die **Wiedergabe**-Schaltfläche, um in den Spielmodus zu wechseln, und verwenden Sie die in den Editor integrierte Eingabesimulation, um Ihre neu konfigurierte Schaltfläche zu testen.

Schaltfläche nicht gedrückt (LEERTASTE + Mausrad zurück):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

Schaltfläche gedrückt (LEERTASTE + Mausrad nach vorn):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> Informationen zum Verwenden der in den Editor integrierten Eingabesimulation finden Sie im Leitfaden [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) (Verwenden der in den Editor integrierten Handeingabesimulation zum Testen einer Szene) im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Erstellen eines Schaltflächenbereichs mit der MRTK-Rasterobjektsammlung

In diesem Abschnitt erfahren Sie, wie Sie mit dem MRTK-Tool „GridObjectCollection“ automatisch mehrere Schaltflächen zu einer ordentlichen Benutzeroberfläche ausrichten.

In diesem speziellen Beispiel wird gezeigt, wie Sie einen Bereich mit fünf Schaltflächen erstellen, die horizontal ausgerichtet sind. Nach den gleichen Prinzipien können Sie aber auch andere Layouts erstellen.

Dies sind die wichtigsten Schritte, die Sie durchführen müssen:

1. Ordnen Sie die Schaltflächen einem übergeordneten Objekt unter
2. Hinzufügen und Konfigurieren der Komponente „Grid Object Collection (Script)“
3. Testen der Schaltflächen mithilfe der Simulation im Editor

### <a name="1-parent-the-button-objects-to-a-parent-object"></a>1. Ordnen Sie die Schaltflächen einem übergeordneten Objekt unter

Klicken Sie mit der rechten Maustaste auf einen leeren Bereich innerhalb des Hierarchiefensters, und wählen Sie **Leere erstellen** aus:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

Klicken Sie mit der rechten Maustaste auf das neu erstellte Objekt, wählen Sie **Umbenennen** aus, und geben Sie ihm einen passenden Namen, beispielsweise **ButtonCollection**:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

Wählen Sie das **PressableButtonHoloLens2**-Objekt aus, und **ziehen** Sie es auf das **ButtonCollection**-Objekt, um es zu einem untergeordneten Objekt des ButtonCollection-Objekts zu machen:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

Klicken Sie mit der rechten Maustaste auf das **PressableButtonHoloLens2**-Objekt, und wählen Sie **Duplizieren** aus, um eine Kopie davon zu erstellen:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

**Wiederholen** Sie diesen Schritt noch vier Mal, bis Sie über insgesamt fünf PressableButtonHoloLens2-Objekte verfügen.

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. Hinzufügen und Konfigurieren der Komponente „Grid Object Collection (Script)“

Klicken Sie mit im Hierarchiefenster ausgewähltem ButtonCollection-Objekt im Inspektorfenster auf die Schaltfläche **Komponente hinzufügen**, suchen Sie dann **Grid Object Collection** (Rasterobjektsammlung), und wählen Sie sie aus, um dem ButtonCollection-Objekt eine Komponente „Grid Object Collection (Script)“ hinzuzufügen:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

Konfigurieren Sie die Komponente „Grid Object Collection (Script)“ wie folgt:

* Ändern Sie **Num Rows** (Anzahl Zeilen) in 1, um alle Schaltflächen in einer einzelnen Zeile auszurichten
* Ändern Sie **Cell Width**  (Zellbreite) in 0,05, um die Schaltflächen innerhalb der Zeile zu verteilen.

Klicken Sie dann auf die Schaltfläche **Sammlung aktualisieren**, um die neue Konfiguration zu übernehmen:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> Die Konfigurationsänderungen, die Sie soeben übernommen haben, stellen die erforderlichen Mindeständerungen dar, um das Ziel zu erreichen, die Schaltflächen in einer einzelnen Zeile zu platzieren. In kommenden Projekten müssen Sie, abhängig von Faktoren wie beispielsweise der Ausrichtung der über- und untergeordneten Objekte, jedoch möglicherweise weitere Einstellungen anpassen, z. B. die Ausrichtungsart. Weitere Informationen zur Rasterobjektsammlung des MRTK finden Sie im Leitfaden [Object collection scripts](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) (Skripts für Objektsammlungen) im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

Ändern Sie bei immer noch im Hierarchiefenster ausgewähltem ButtonCollection-Objekt die **Transformationsposition** des ButtonCollection-Objekts so, dass seine untergeordneten Schaltflächenobjekte vor der Kamera positioniert sind, die sich am Ursprung befindet, beispielsweise x = 0, y = 0 und z = 0,5:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> Als Sie das PressableButtonHoloLens2-Prefab im Abschnitt [Gesten für Handtracking und interaktionsfähige Schaltflächen](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) ursprünglich hinzufügten, positionierten Sie es vor der Kamera. Da die Rasterobjektsammlung jedoch die Position ihrer unmittelbar untergeordneten Objekte steuert, wurde die Z-Position der untergeordneten PressableButtonHoloLens2-Objekte entsprechend des Standardabstands 0 der Rasterobjektsammlung vom Wert des übergeordneten Objekts auf 0 zurückgesetzt. Dies ist, neben der Aufrechterhaltung einer geordneten Positionsbeziehung von über- und untergeordneten Objekten, der Grund, warum wir die Position des übergeordneten ButtonCollection-Objekts nach vorn verschoben haben, statt den Abstand vom Wert des übergeordneten Objekts zu konfigurieren, um die untergeordneten PressableButtonHoloLens2-Objekte nach vorn zu verschieben.

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a>3. Testen der Schaltflächen mithilfe der Simulation im Editor

Drücken Sie die Wiedergabe-Schaltfläche, um in den Spielmodus zu wechseln, und verwenden Sie die in den Editor integrierte Simulation, um jede der Schaltflächen in Ihrem neu erstellten Schaltflächenbereich zu testen:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> Wenn Sie aktuell eine der fünf Schaltflächen drücken, wechselt die Farbe des Würfels zu Blaugrün. Um die Erfahrung interessanter zu machen, wenden Sie an, was Sie soeben gelernt haben, um für jede Schaltfläche den Wechsel des Würfels zu einer anderen Farbe zu konfigurieren.

## <a name="adding-text-into-your-scene"></a>Hinzufügen von Text zu Ihrer Szene

In diesem Abschnitt erfahren Sie, wie Sie Ihren Mixed Reality-Erfahrungen mithilfe von TextMesh Pro in Unity Text hinzufügen, was Sie im Abschnitt [Importieren von TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) des vorherigen Tutorials vorbereitet haben.

In diesem speziellen Beispiel fügen Sie unterhalb der Schaltflächensammlung, die Sie im vorherigen Abschnitt erstellt haben, eine einfache Bezeichnung hinzu.

Klicken Sie mit der rechten Maustaste auf das ButtonCollection-Objekt, und wählen Sie **3D-Objekt** > **Text – TextMeshPro** aus, um ein TextMeshPro-Objekt als untergeordnetes Objekt des ButtonCollection-Objekts zu erstellen:

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

Ändern Sie bei immer noch ausgewähltem neu erstelltem TextMeshPro-Objekt namens „Text (TMP)“ im Inspektorfenster dessen Position und Größe, sodass die Bezeichnung ordentlich unterhalb der Schaltflächensammlung platziert ist, beispielsweise:

* Ändern Sie die Rect-Transformations-**Pos Y** in -0,0425
* Ändern Sie die Rect-Transformations-**Breite** in-0,24
* Ändern Sie die Rect-Transformations-**Höhe** in-0,024

Aktualisieren Sie dann den Text, um den Zweck der Bezeichnung wiederzugeben, und wählen Sie die Schriftarteigenschaften, sodass der Text in die Bezeichnung passt, beispielsweise:

* Ändern Sie den **Text** von „Text Mesh Pro (Script)“ in „Schaltflächensammlung“
* Ändern Sie den **Schriftschnitt** von „Text Mesh Pro (Script)“ in „Fett“
* Ändern Sie den **Schriftgrad** von „Text Mesh Pro (Script)“ in 0,2
* Ändern Sie die **Ausrichtung** von „Text Mesh Pro (Script)“ in „Zentriert und Mittig“

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, wie Sie eine MRTK-Profileinstellung klonen, anpassen und konfigurieren. Sie haben außerdem erfahren, wie Sie mit Schaltflächen interagieren können, um Ereignisse mit nachverfolgten Händen für die HoloLens 2 auszulösen. Abschließend haben Sie erfahren, wie Sie mit der MRTK-Komponente „Grid Object Collection“ (Rasterobjektsammlung) und „TextMeshPro“ von Unity eine einfache Benutzeroberfläche erstellen.

[Nächstes Tutorial: 4. Platzieren dynamischer Inhalte und Verwenden von Solvern](mrlearning-base-ch3.md)
