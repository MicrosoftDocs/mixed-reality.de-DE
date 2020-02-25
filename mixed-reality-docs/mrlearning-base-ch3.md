---
title: 'Tutorials zu den ersten Schritten: 4. Platzieren von dynamischem Inhalt und Verwenden von Solvers'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 5463f363291790fd5e5d76ffa322a61ca7bf8e31
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553878"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. Platzieren von dynamischem Inhalt und Verwenden von Solvers
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

Holograms sind in hololens 2 zu leben, wenn Sie intuitiv dem Benutzer folgen und in der physischen Umgebung auf eine Weise platziert werden, die die Interaktion nahtlos und elegant macht. In diesem Tutorial wird erläutert, wie Sie Hologramme dynamisch mithilfe der verfügbaren Platzierungs Tools von mrtk platzieren können, die als Solvers bezeichnet werden, um komplexe räumliche Platzierungs Szenarien zu lösen. In den mrtk sind Solvers ein System aus Skripts und Verhalten, mit denen Benutzeroberflächen Elemente Ihnen, dem Benutzer oder anderen Spielobjekten in der Szene folgen können. Sie können auch verwendet werden, um schnell an bestimmten Positionen anzudocken, wodurch Ihre Anwendung intuitiver gestaltet wird.

## <a name="objectives"></a>Ziele

* Einführen von mrtk-Solvers
* Verwenden Sie Solvers, damit eine Auflistung von Schaltflächen auf den Benutzer folgt.
* Verwenden Sie Solvers, damit ein Spielobjekt den nach verfolgten Händen des Benutzers folgt.

## <a name="location-of-solvers-in-the-mrtk"></a>Speicherort der Solver in der mrtk

 Die Solvers von mrtk befinden sich im Ordner "mrtk SDK". Um die verfügbaren Solver in Ihrem Projekt anzuzeigen, navigieren Sie im Projektfenster zu **Assets** > **mixedrealitytoolkit. SDK** > **Features** > **Hilfsprogramme** > **Solvers**:

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

In diesem Tutorial überprüfen wir die Implementierung des "Orbital Solver" und des radivers für radiale Ansichten. Weitere Informationen über die vollständige Palette der in der mrtk verfügbaren Solver finden Sie im Handbuch zu [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) im [mrtk-Dokumentations Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="use-a-solver-to-follow-the-user"></a>Verwenden Sie einen Solver, um dem Benutzer zu folgen.
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

In diesem Abschnitt erweitern Sie die Schaltflächen Auflistung, die Sie im vorherigen Tutorial erstellt haben, damit Sie der Ausrichtung des Benutzers folgt. Außerdem konfigurieren Sie den Solver so, dass die Schaltflächen Auflistung immer verwendet wird:

* Wird parallel zur Leserichtung des Benutzers gedreht, damit der Lesevorgang von links nach rechts durchgeführt wird.
* Wird etwas unterhalb der horizontalen bidirektionale Ausrichtung positioniert, sodass nicht die anderen Objekte blockiert werden, die Sie später in diesem Tutorial hinzufügen werden.
* Der Benutzer hat ungefähr eine halbe Arm-Länge positioniert, sodass die Schaltflächen problemlos gedrückt werden können.

Hierzu verwenden Sie den " **Orbital Solver** ", der das Objekt an eine angegebene Position und einen Offset des Objekts sperrt, auf das verwiesen wird.

### <a name="1-add-the-orbital-solver"></a>1. Fügen Sie den Orbital-Solver hinzu.

Wählen Sie im Fenster Hierarchie das **buttoncollection** -Objekt aus, und verwenden Sie dann im Inspektor-Fenster die Schaltfläche **Komponente hinzufügen** , um dem buttoncollection-Objekt die Komponente " **Orbital (Skript)** " hinzuzufügen.

> [!NOTE]
> Wenn Sie in diesem Fall einen Solver hinzufügen, wird die Komponente "Solver-Handler (Skript)" automatisch hinzugefügt, da Sie für den Solver erforderlich ist.

### <a name="2-configure-the-orbital-solver"></a>2. Konfigurieren des "Orbital Solver"

Konfigurieren der **Solver-Handlerkomponente (Skript)** :

* Überprüfen, ob der **verfolgte Zieltyp** auf **Head** festgelegt ist

Konfigurieren Sie die Komponente " **Orbital (Skript)** ":

* Überprüfen, ob der **Orientierungstyp** auf das **verfolgte Objekt folgt**
* Legen Sie **den lokalen Offset** auf X = 0, Y = 0, Z = 0 (null) zurück.
* Ändern des **Welt Offsets** in X = 0, Y =-0,4, Z = 0,3

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a>3. Testen des Orbital-Solvers mithilfe der in-Editor-Simulation

Drücken Sie die Wiedergabe Schaltfläche, um den Spielmodus einzugeben, und halten Sie die Rechte Maustaste gedrückt, um die Richtung des Blicks zu drehen, und beachten Sie Folgendes:

* Die Transformations Position der buttoncollection wird jetzt durch die Solver-Einstellungen gesteuert.
* Der Cube, der vom Solver nicht betroffen ist, bleibt an derselben Position.

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> Wenn der Kamera Strahl in Ihrem Szenen Fenster nicht angezeigt wird, stellen Sie sicher, dass Ihr Gizmos-Menü aktiviert ist. Weitere Informationen zum Gizmos-Menü und deren Verwendung zur Optimierung Ihrer Szenen Ansicht finden Sie in der <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos-Menü</a> Dokumentation von Unity.
>
> Um die Szene und das Spielfenster nebeneinander anzuzeigen, wie in der Abbildung oben gezeigt, ziehen Sie einfach das Spielfenster auf die Rechte Seite des Fensters Szene. Weitere Informationen zum Anpassen des Arbeitsbereichs finden Sie in der Dokumentation zum <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Anpassen Ihres Arbeits</a> Bereichs in Unity.

## <a name="enabling-objects-to-follow-tracked-hands"></a>Aktivieren von Objekten für die Verfolgung von nach verfolgten Händen

In diesem Abschnitt Konfigurieren Sie das Cube-Objekt, das Sie im vorherigen Tutorial erstellt haben, damit es den nach verfolgten Händen des Benutzers folgt, insbesondere dem rechten Handgelenk. Außerdem konfigurieren Sie den Solver auch so, dass der Cube:

* Ändert die Ausrichtung mit der Hand Drehung des Benutzers.
* Auf dem Handgelenk des Benutzers positioniert

Hierzu verwenden Sie den **radiver der radialen Ansicht** , der das Objekt innerhalb eines Ansichts Kegels speichert, das auf das Objekt verweist, auf das verwiesen wird.

### <a name="1-add-the-radial-view-solver"></a>1. Fügen Sie den Solver für radiale Ansichten hinzu

Wählen Sie im Fenster Hierarchie das Cubeobjekt aus, und verwenden Sie dann im Inspektor- **Fenster die Schalt** Fläche **Komponente hinzufügen** , um das Komponenten-Cubeobjekt der **radialen Ansicht (Skript)** hinzuzufügen.

### <a name="2-configure-the-radial-view-solver"></a>2. Konfigurieren Sie den Solver für radiale Ansichten.

Konfigurieren der **Solver-Handlerkomponente (Skript)** :

* Änderungs nach **verfolgten Zieltyp** in **Hand Gelenk** ändern
* Geänderte **Handlichkeit** nach **Rechts** ändern
* Nach **verfolgte Hand Gelenk** in Hand **Gelenk** ändern

Konfigurieren Sie die Komponente **radiale Ansicht (Skript)** :

* Ändern Sie die **Verweis Richtung** in **objektorientiert**, und aktivieren Sie dann das Kontrollkästchen **an Verweis Richtung ausrichten** .
* Ändern Sie die **minimale Entfernung** und den **maximalen Abstand** in 0.

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a>3. Testen des Solver der radialen Ansicht mithilfe der in-Editor-Simulation

Drücken Sie die Wiedergabe Schaltfläche, um den Spielmodus einzugeben, und halten Sie dann die Leertaste gedrückt, um die Hand zu machen. Bewegen Sie den Mauszeiger um die Hand, und klicken Sie auf die linke Maustaste, um die Hand zu drehen:

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, wie Sie mit den Solvers von mrtk eine Benutzeroberfläche intuitiv auf den Benutzer anwenden können. Außerdem haben Sie erfahren, wie Sie einen Solver an ein Objekt (d. h. einen Cube) anfügen, um die nach verfolgten Hände des Benutzers zu befolgen. Weitere Informationen zu diesen und anderen in der mrtk enthaltenen Solvers finden Sie im Handbuch zu [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) im [mrtk-Dokumentations Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

[Nächstes Tutorial: 5. Interaktion mit 3D-Objekten](mrlearning-base-ch4.md)
