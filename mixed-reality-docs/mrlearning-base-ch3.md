---
title: 'Tutorials zu den ersten Schritten: 4 Platzieren dynamischer Inhalte und Verwenden von Solvern'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 2825f99f49eca6fd7277d02828bfe1bc3c23291a
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031214"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. Platzieren dynamischer Inhalte und Verwenden von Solvern
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

Hologramme werden in HoloLens 2 lebendig, wenn sie dem Benutzer intuitiv folgen und in der physischen Umgebung so platziert werden, dass die Interaktion reibungslos und stilvoll verläuft. In diesem Tutorial untersuchen wir Möglichkeiten zur dynamischen Platzierung von Hologrammen mit den verfügbaren Platzierungstools des MRTK, den so genannten Solvern, um Szenarien mit komplexer räumlicher Platzierung zu lösen. Im MRTK bilden Solver ein System aus Skripts und Verhaltensweisen, mit deren Hilfe es Benutzeroberflächenelementen ermöglicht wird, dem Benutzer oder anderen Spielobjekten in der Szene zu folgen. Sie können auch verwendet werden, um schnell an bestimmten Positionen anzudocken, wodurch Ihre Anwendung intuitiver gestaltet wird.

## <a name="objectives"></a>Ziele

* Einführen der MRTK-Solver
* Verwenden von Solvern, um eine Sammlung von Schaltflächen dem Benutzer folgen zu lassen
* Verwenden von Solvern, um ein Spielobjekt den nachverfolgten Händen des Benutzers folgen zu lassen

## <a name="location-of-solvers-in-the-mrtk"></a>Speicherort der Solver im MRTK

 Die Solver des MRTK befinden sich im MRTK SDK-Ordner. Um die verfügbaren Solver in Ihrem Projekt anzuzeigen, navigieren Sie im Projektfenster zu **Assets** > **MixedRealityToolkit.SDK** > **Features** > **Utilities** > **Solvers**:

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

In diesem Tutorial behandeln wir die Implementierung der Solver „Orbital“ und „Radial View“. Weitere Informationen zur ganzen Bandbreite der im MRTK verfügbaren Solver finden Sie im [Solver](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)-Leitfaden im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="use-a-solver-to-follow-the-user"></a>Verwenden eines Solvers zum Folgen des Benutzers
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

In diesem Abschnitt erweitern Sie die Schaltflächensammlung, die Sie im vorherigen Tutorial erstellt haben, sodass sie der Blickrichtung des Benutzers folgt. Darüber hinaus konfigurieren Sie den Solver so, dass Folgendes immer auf die Schaltflächensammlung zutrifft:

* Sie wird parallel zur Leserichtung des Benutzers gedreht, für natürliches Lesen von links nach rechts
* Sie wird etwas unterhalb der horizontalen Blickrichtung des Benutzers positioniert, sodass die anderen Objekte, die später in diesem Tutorial hinzugefügt werden, nicht verdeckt werden
* Sie wird ungefähr eine halbe Armlänge vom Benutzer entfernt, sodass die Schaltflächen leicht gedrückt werden können

Hierzu verwenden Sie den **Orbital-Solver**, der das Objekt fest an einer angegebenen Position und einem Offset vom Bezugsobjekt verankert.

### <a name="1-add-the-orbital-solver"></a>1. Hinzufügen des Orbital-Solvers

Wählen Sie im Hierarchiefenster das **ButtonCollection**-Objekt aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um dem ButtonCollection-Objekt die Komponente **Orbital (Script)** hinzuzufügen.

> [!NOTE]
> Wenn Sie einen Solver hinzufügen, in diesem Fall die Komponente „Orbital (Script)“, wird die Solver Handler (Script)-Komponente automatisch hinzugefügt, weil diese vom Solver benötigt wird.

### <a name="2-configure-the-orbital-solver"></a>2. Konfigurieren des Orbital-Solvers

Konfigurieren Sie die **Solver Handler (Script)** -Komponente

* Vergewissern Sie sich, dass der **Tracked Target Type** (Typ des nachverfolgten Ziels) auf **Head** (Kopf) festgelegt ist

Konfigurieren Sie die **Orbital (Script)** -Komponente:

* Vergewissern Sie sich, dass der **Orientation Type** (Ausrichtungstyp) auf **Follow Tracked Object** (Nachverfolgtem Objekt folgen) festgelegt ist
* Setzen Sie **Local Offset** auf X = 0, Y = 0, Z = 0 zurück
* Ändern Sie **World Offset** auf X = 0, Y = -0,4, Z = 0,3

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a>3. Testen des Orbital-Solvers mithilfe der Simulation im Editor

Drücken Sie die Wiedergabe-Schaltfläche, um in den Spielmodus zu wechseln, drücken und halten Sie dann die rechte Maustaste, um Ihre Blickrichtung zu drehen, und achten Sie auf Folgendes:

* Die Transformationsposition der ButtonCollection wird jetzt durch die Solver-Einstellungen gesteuert
* Der Würfel, der nicht vom Solver beeinflusst wird, bleibt an der gleichen Position.

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> Wenn Sie in Ihrem Szenefenster den Kamerastrahl nicht sehen, vergewissern Sie sich, dass Ihr Gizmos-Menü aktiviert ist. Weitere Informationen zum Gizmos-Menü und dessen Verwendung zur Optimierung Ihrer Szenenansicht finden Sie in der Unity-Dokumentation zum <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos-Menü</a>.
>
> Um Ihr Szenen- und Spielfenster nebeneinander anzuzeigen, wie in der Abbildung oben dargestellt, ziehen Sie einfach das Spielfenster rechts neben das Szenenfenster. Weitere Informationen zum Anpassen Ihres Arbeitsbereichs finden Sie in der Unity-Dokumentation zum <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Anpassen Ihres Arbeitsbereichs</a>.

## <a name="enabling-objects-to-follow-tracked-hands"></a>Objekten das Folgen von nachverfolgten Händen ermöglichen

In diesem Abschnitt konfigurieren Sie das Würfelobjekt, das Sie im vorherigen Tutorial erstellt haben, so, dass es den nachverfolgten Händen des Benutzers folgt, insbesondere dem rechten Handgelenk. Darüber hinaus konfigurieren Sie den Solver so, dass Folgendes auf den Würfel zutrifft:

* Er ändert die Ausrichtung mit der Handdrehung des Benutzers
* Er ist auf dem Handgelenk des Benutzers positioniert

Zu diesem Zweck verwenden Sie den **Radial View Solver** (Radialansichts-Solver), der das Objekt innerhalb eines Ansichtskegels hält, der vom Bezugsobjekt projiziert wird.

### <a name="1-add-the-radial-view-solver"></a>1. Hinzufügen des Radial View-Solvers

Wählen Sie im Hierarchiefenster das **Würfelobjekt** aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um dem Würfelobjekt die Komponente **Radial View (Script)** hinzuzufügen.

### <a name="2-configure-the-radial-view-solver"></a>2. Konfigurieren des Radial View-Solvers

Konfigurieren Sie die **Solver Handler (Script)** -Komponente:

* Ändern Sie **Tracked Target Type** (Typ des nachverfolgten Ziels) in **Gelenk der Hand**
* Ändern Sie **Tracked Handness** (nachverfolgte Händischkeit) in **Right**
* Ändern Sie **Tracked Hand Joint** (Nachverfolgtes Gelenk der Hand) in **Wrist** (Handgelenk)

Konfigurieren Sie die **Radial View (Script)** -Komponente:

* Ändern Sie **Reference Direction** (Bezugsrichtung) in **Object Oriented** (Objektorientiert), und aktivieren Sie dann das Kontrollkästchen **Orient To Reference Direction** (An Bezugsrichtung ausrichten)
* Ändern Sie **Min Distance** (Minimalabstand) und **Max Distance** (Maximalabstand) in 0

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a>3. Testen des Radial View-Solvers mithilfe der Simulation im Editor

Drücken Sie die Wiedergabe-Schaltfläche, um in den Spielmodus zu wechseln, und halten Sie dann die LEERTASTE gedrückt, um die Hand anzuzeigen. Bewegen Sie den Mauszeiger, um die Hand zu bewegen, und klicken und halten Sie die linke Maustaste, um die Hand zu drehen:

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie erfahren, wie Sie die MRTK-Solver verwenden können, damit eine Benutzeroberfläche intuitiv dem Benutzer folgt. Sie haben auch erfahren, wie Sie einen Solver an ein Objekt (d. h. Würfel) anfügen, um den nachverfolgten Händen des Benutzers zu folgen. Weitere Informationen zu diesen und anderen Solvern, die im MRTK enthalten sind, finden im [Solver](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)-Leitfaden im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

[Nächstes Tutorial: 5. Interagieren mit 3D-Objekten](mrlearning-base-ch4.md)
