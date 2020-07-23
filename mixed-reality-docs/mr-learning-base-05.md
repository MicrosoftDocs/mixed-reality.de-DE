---
title: 'Tutorials zu den ersten Schritten: 5 Erstellen dynamischer Inhalte mithilfe von Solvern'
description: In diesem Kurs erfahren Sie, wie Sie das Mixed Reality Toolkit (MRTK) verwenden, um eine Mixed Reality-Anwendung zu erstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: cbeaa8b65b7aecc0600294b3739fedfb903e568e
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305720"
---
# <a name="5-creating-dynamic-content-using-solvers"></a>5. Erstellen dynamischer Inhalte mithilfe von Solvern

## <a name="overview"></a>Übersicht

In diesem Tutorial lernen Sie Möglichkeiten zur dynamischen Platzierung von Hologrammen mit den verfügbaren Platzierungstools des MRTK kennen, den so genannten Solvern, um Szenarien mit komplexer räumlicher Platzierung zu lösen. Im MRTK bilden Solver ein System aus Skripts und Verhaltensweisen, mit deren Hilfe Objekte dem Benutzer oder anderen Spielobjekten in der Szene folgen können. Sie können auch verwendet werden, um an bestimmten Positionen anzudocken, wodurch Ihre Anwendung intuitiver wird.

## <a name="objectives"></a>Ziele

* Einführen der MRTK-Solver
* Erfahren, wie Benutzer mithilfe von Solvern zu Objekten geführt werden.
* Erfahren, wie Solver zum Neupositionieren von Objekten verwendet werden.

## <a name="location-of-solvers-in-the-mrtk"></a>Speicherort der Solver im MRTK

 Die Solver des MRTK befinden sich im MRTK SDK-Ordner. Um die verfügbaren Solver in Ihrem Projekt anzuzeigen, navigieren Sie im Projektfenster zu **Assets** > **MRTK** > **SDK** > **Features** > **Utilities** > **Solvers** (Medienobjekte > MRTK > SDK > Features > Hilfsprogramme > Solver):

![mr-learning-base](images/mr-learning-base/base-05-section1-step1-1.png)

In diesem Tutorial behandeln wir die Implementierung des Solvers Directional Indicator (Richtungsanzeige) und des Solvers Tap To Place (Zum Platzieren tippen). Weitere Informationen zur ganzen Bandbreite der im MRTK verfügbaren Solver finden Sie im [Solver](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)-Leitfaden im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

> [!NOTE]
> Der Richtungsanzeige-Solver befindet sich nicht in den oben angegebenen Solver-Ordnern, sondern im Ordner „Assets“ > „MRTK“ > „SDK“ > „Experimental“ > „Features“ > „Utilities“ (Medienobjekte > MRTK > SDK > Experimentell > Features > Hilfsprogramme), da es sich um ein experimentelles Feature handelt.

## <a name="using-the-directional-indicator-solver-to-direct-the-user-to-objects"></a>Verwenden des Richtungsanzeige-Solvers, um den Benutzer zu Objekten zu führen

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** (Medienobjekte > MRTK.Tutorials.GettingStarted > Prefabs), klicken Sie auf das **Chevron**-Prefab (Winkel), ziehen Sie es auf das Hierarchiefenster, und legen Sie seine **Transformationsposition**auf X = 0, Y = 0, Z = 2 fest, um es in der Nähe des RoverExplorer-Objekts zu positionieren:

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-1.png)

> [!TIP]
> Wenn Sie feststellen, dass die Kamera oder andere Symbole in Ihrer Szene die Objekte verdecken oder störend wirken, können Sie diese ausblenden, indem Sie <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">die Gizmos umschalten</a>, in die Aus-Position, wie in der Abbildung oben dargestellt. Weitere Informationen zum Gizmos-Menü und dessen Verwendung zur Optimierung Ihrer Szenenansicht finden Sie in der Unity-Dokumentation zum <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos-Menü</a>.

Benennen Sie das neu hinzugefügte Chevron-Objekt in **Indicator** um, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die Komponenten **DirectionalIndicator** und **Directional Indicator Controller (Script)** (Richtungsanzeigesteuerung (Skript)) hinzuzufügen:

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-2.png)

> [!NOTE]
> Wenn Sie einen Solver hinzufügen, in diesem Fall die Komponente „DirectionalIndicator“, wird die Solver Handler-Komponente automatisch hinzugefügt, weil der Solver sie benötigt.

> [!NOTE]
> Die Directional Indicator Controller (Script)-Komponente ist nicht Teil des MRTK sondern ist in den Medienobjekten des Tutorials enthalten.

Konfigurieren Sie die Komponenten DirectionalIndicator und SolverHandler wie folgt:

* Vergewissern Sie sich, dass der **Tracked Target Type** (Typ des nachverfolgten Ziels) der **SoverHandler**-Komponente auf **Head** (Kopf) festgelegt ist.
* Weisen Sie den **RoverExplorer** dem **Directional Target** (Richtungsziel) der **DirectionalIndicator**-Komponente zu, indem Sie ihn aus dem Hierarchiefenster auf das **None (Transform)** -Feld (Ohne (Transformation)) ziehen.
* Ändern Sie den **View Offset** (Ansichtsversatz) in 0,2

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-3.png)

Drücken Sie die Wiedergabe-Schaltfläche, um in den Spielmodus zu wechseln, drücken Sie dann die rechte Maustaste, und halten Sie sie gedrückt, während Sie die Maus nach rechts oder links bewegen, um Ihre Blickrichtung zu drehen. Beachten Sie dabei Folgendes:

* Wenn Sie vom RoverExplorer-Objekt weg blicken, wird das Indikatorobjekt angezeigt und zeigt in die Richtung des RoverExplorer-Objekts.

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-4.png)

> [!NOTE]
> Wenn Sie in Ihrem Szenefenster den Kamerastrahl nicht sehen, vergewissern Sie sich, dass Ihr Gizmos-Menü aktiviert ist, wie in der Abbildung oben dargestellt.

> [!TIP]
> Informationen zum Verwenden der in den Editor integrierten Eingabesimulation finden Sie im Leitfaden [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) (Verwenden der in den Editor integrierten Handeingabesimulation zum Testen einer Szene) im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

> [!TIP]
> Wenn Ihr Computer ein Mikrofon aufweist, können Sie den Aktivitätszustand des Diagnosepanels, das im Spielfenster angezeigt wird, leicht umschalten, indem Sie den Sprachbefehl „toggle diagnostics“ (Diagnose umschalten) verwenden. Alternativ können Sie es im MRTK-Konfigurationsprofil deaktivieren, „Profile“ > „Diagnostics“ > „Enable Diagnostics System“ (Profil > Diagnose > Diagnosesystem aktivieren). Im allgemeinen empfiehlt es sich aber, das Diagnosesystem während der Entwicklung aktiviert zu lassen.

## <a name="using-the-tap-to-place-solver-to-reposition-objects"></a>Verwenden des Tap to Place-Solvers, um die Positionierung von Objekten zu ändern

Wählen Sie im Hierarchiefenster das Objekt RoverExplorer > **RoverAssembly** aus, verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die Komponente **Tap To Place (Script)** (Zum Platzieren tippen (Skript)) hinzuzufügen, und konfigurieren Sie sie wie folgt:

* Vergewissern Sie sich, dass der **Tracked Target Type** (Typ des nachverfolgten Ziels) der **SoverHandler**-Komponente auf **Head** (Kopf) festgelegt ist.
* Aktivieren Sie das Kontrollkästchen **Keep Orientation Vertical** (Vertikale Ausrichtung beibehalten).
* Deaktivieren Sie in der Dropdownliste **Magnetic Surfaces** > **Element 0** (Magnetische Oberflächen > Element 0) alle Optionen mit Ausnahme von **Spatial Awareness** (Räumliche Wahrnehmung).

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-1.png)

> [!NOTE]
> Die Einstellung „Magnetic Surfaces“ (Magnetische Oberflächen) bestimmt, welche Objekte von der Komponente Tap To Place (Script) beim Platzieren eines Objekts erkannt werden. Indem Sie die Einstellung nur zu Spatial Awareness (Räumliche Wahrnehmung) ändern, kann die Tap To Place (Script)-Komponente den Rover nur auf Objekten platzieren, die sich auf der Unity-Ebene mit dem Namen „Spatial Awareness“ befinden, und das ist standardmäßig das von HoloLens generierte Spatial Awareness Mesh (Gittermodell für räumliche Wahrnehmung).
>
>Weitere Informationen zu Ebenen finden Sie in der Dokumentation zu <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Ebenen</a> von Unity.

> [!TIP]
> Wenn Sie beim Testen der Tap to Place-Funktionalität das Gittermodell für räumliche Wahrnehmung sehen möchten, können Sie die Anzeigeoption des Spatial Mesh Observer auf „Visible“ (Sichtbar) festlegen. Wenn Sie eine Auffrischung zum Ändern der Anzeigeoption benötigen, informieren Sie sich in den Anweisungen zum [Ändern der Anzeigeoptionen für räumliche Wahrnehmung](mr-learning-base-03.md#changing-the-spatial-awareness-display-option).

Während das RoverAssembly-Objekt noch im Hierarchiefenster ausgewählt ist, suchen Sie im Inspektorfenster das Ereignis **On Placing Started ()** (Bei Platzierung gestartet ()), und klicken Sie auf das **+** -Symbol, um ein neues Ereignis hinzuzufügen:

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-2.png)

Konfigurieren Sie das Ereignis wie folgt:

* Weisen Sie das **RoverAssembly**-Objekt als Listener für das On Placing Started ()-Ereignis zu, indem Sie es aus dem Hierarchiefenster auf das **None (Object)** -Feld (Ohne (Objekt)) ziehen.
* Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **TapToPlace** > **float SurfaceNormalOffset** aus, um den Wert der Eigenschaft SurfaceNormalOffset zu aktualisieren, wenn das Ereignis ausgelöst wird.
* Vergewissern Sie sich, dass das Argument auf **0** festgelegt ist.

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-3.png)

Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf eine leere Stelle, wählen Sie **3D Object** > **Cube** (3D-Objekt > Würfel) aus, um ein vorübergehendes Objekt zu erstellen, das den Boden darstellt, und konfigurieren Sie die Komponente **Transform** (Transformieren) wie folgt:

* **Position**: X = 0, Y = -1,65, Z = 6
* **Drehung**: X = 0, Y = 0, Z = 0
* **Skalierung**: X = 10, Y = 0,2, Z = 10

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-4.png)

Während der temporäre Würfel noch im Hierarchiefenster ausgewählt ist, verwenden Sie im Inspektorfenster die Dropdownliste **Layers** (Ebenen), um die Ebeneneinstellung des Würfels so zu ändern, dass sie nur die Ebene **Spatial Awareness** (Räumliche Wahrnehmung) enthält:

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-5.png)

Drücken Sie die Wiedergabe-Schaltfläche, um in den Spielmodus zu wechseln, drücken Sie dann die rechte Maustaste, und halten Sie sie gedrückt, während Sie Maus abwärts bewegen, bis der Blick auf das RoverAssembly-Objekt trifft:

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-6.png)

Klicken Sie mit der linken Maustaste, um den Zum-Platzieren-tippen-Vorgang zu starten:

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-7.png)

Drücken Sie die rechte Maustaste, und halten Sie sie gedrückt, während Sie die Maus nach rechts oder links bewegen, um Ihre Blickrichtung zu drehen. Wenn Sie mit der Positionierung einverstanden sind, klicken Sie mit der linken Maustaste:

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-8.png)

Wenn Sie das Testen des Features im Spielmodus abgeschlossen haben, klicken Sie mit der rechten Maustaste auf das Würfelobjekt, und wählen Sie **Löschen** aus, um es aus der Szene zu entfernen:

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-9.png)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, wie Sie den Richtungsindikator-Solver aus dem MRTK dazu verwenden können, den Benutzer durch ein Benutzeroberflächenelement intuitiv zu Objekten zu führen. Sie haben darüber hinaus erfahren, wie der Zum-Platzieren-tippen-Solver verwendet wird, um die Position von Objekten auf einfache Weise zu ändern.

Weitere Informationen zu diesen und anderen Solvern, die im MRTK enthalten sind, finden im [Solver](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)-Leitfaden im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

[Nächstes Tutorial: 6. Erstellen der Benutzeroberfläche](mr-learning-base-06.md)
