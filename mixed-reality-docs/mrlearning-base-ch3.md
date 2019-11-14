---
title: 'Tutorials zu den ersten Schritten: 4. Platzieren von dynamischem Inhalt und Verwenden von Solvers'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: ade7a839e03a306332bf18f1db49805f59c71429
ms.sourcegitcommit: f2b7c6381006fab6d0472fcaa680ff7fb79954d6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2019
ms.locfileid: "74064258"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. Platzieren von dynamischem Inhalt und Verwenden von Solvers

Holograms sind in hololens 2 zu leben, wenn Sie intuitiv dem Benutzer folgen und in der physischen Umgebung auf eine Weise platziert werden, die die Interaktion nahtlos und elegant macht. In diesem Tutorial wird erläutert, wie Sie Hologramme dynamisch mithilfe der verfügbaren Platzierungs Tools von mrtk platzieren (als Solver bezeichnet), um komplexe räumliche Platzierungs Szenarien zu lösen. In den mrtk sind Solvers ein System aus Skripts und Verhalten, mit denen Benutzeroberflächen Elemente Ihnen, dem Benutzer oder anderen Spielobjekten in der Szene folgen können. Sie können auch verwendet werden, um schnell an bestimmten Positionen anzudocken, wodurch Ihre Anwendung intuitiver gestaltet wird.

## <a name="objectives"></a>Ziele

* Einführen der MRTK-Solver
* Verwenden von Solvern, damit eine Sammlung von Schaltflächen dem Benutzer folgt
* Verwenden von Solvern, damit ein Spielobjekt den nachverfolgten Händen des Benutzers folgt

## <a name="instructions"></a>Anweisungen

### <a name="location-of-solvers-in-the-mrtk"></a>Position der Solver im MRTK

 Um die verfügbaren Solver in Ihrem Projekt zu finden, suchen Sie im Ordner "mrtk SDK" (mixedrealitytoolkit. SDK-Ordner). Im Ordner Hilfsprogramme sehen Sie den Ordner Solvers, wie in der folgenden Abbildung dargestellt.

![Solver](images/lesson3_chapter1_step1im.PNG)

>[!NOTE]
>In dieser Lektion wird nur die Implementierung des "Orbital Solver" und des radialview-Solvers überprüft. Weitere Informationen über die vollständige Palette der in der mrtk verfügbaren Solver finden Sie unter: [https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

### <a name="use-a-solver-to-follow-the-user"></a>Verwenden eines Solvers zum Folgen des Benutzers

Das Ziel dieses Kapitels besteht darin, die zuvor erstellte Schaltflächen Auflistung zu verbessern, sodass Sie der Blick Richtung des Benutzers folgt. In der vorherigen Version von mrtk und holotoolkit wurde dies als Tagalong-Funktionalität bezeichnet.

1. Wählen Sie das übergeordnete Objekt der Schaltflächensammlung aus der vorherigen Lektion aus.

    ![Lektion3 Kapitel2 Schritt1im](images/Lesson3_chapter2_step1im.PNG)

2. Klicken Sie im Inspektor-Panel auf die Schaltfläche Komponente hinzufügen, und suchen Sie nach "Orbital". Die Komponente "Orbital" sollte angezeigt werden. Wählen Sie diese Option aus, um die Komponente "Orbital" dem Auflistungs Spielobjekt hinzuzufügen

    ![Lektion3 Kapitel2 Schritt2im](images/Lesson3_Chapter2_step2im.PNG)

    >[!NOTE]
    >Wenn Sie die Komponente "Orbital" hinzufügen, werden Sie feststellen, dass das System auch die Komponente "solverhandler" hinzufügt, die eine erforderliche Komponente ist.

3. Um die Schaltflächen Auflistung so zu konfigurieren, dass Sie dem Benutzer folgt, müssen wir die folgenden Anpassungen implementieren (siehe Abbildung unten):
    * Legen Sie im Skript für die Ausrichtung der Ausrichtungs Typen-Dropdown Liste nur auf "Yaw" fest. Dadurch wird erreicht, dass sich nur eine Achse des Objekts dreht, während es dem Benutzer folgt.
    * Legen Sie den lokalen Versatz an allen Achsen auf 0 fest. Legen Sie den Welt Offset auf x = 0, y =-0,1 und z = 0,6 fest. Dadurch wird die Bewegung des Objekts gesperrt, sodass das Objekt bei einer Änderung der Höhe in der physischen Umgebung in einer festgelegten Höhe verbleibt, während es dem Benutzer weiterhin gestattet, wenn der Benutzer die Umgebung bewegt. Diese Werte können angepasst werden, um ein breites Spektrum an Verhaltensweisen zu erreichen.
    * Für ein nachfolgendes Verhalten, bei dem die Schaltflächen nur der Ansicht des Benutzers folgen, wenn der Benutzer die Kopfzeile in der Hand hat, können Sie das Kontrollkästchen "Winkel Sprung für Welt Offset verwenden" auswählen (Hinweis: dieser Titel kann auf einigen Bildschirmen abgeschnitten werden, wie er in der Abbildung unten dargestellt ist.) Wenn das Objekt z. b. nur alle 90 Grad dem Benutzer folgen soll, legen Sie die Anzahl der Schritte auf 4 (im folgenden Beispiel mit einem grünen Pfeil gekennzeichnet) fest.

    ![Lektion3 Kapitel2 Schritt3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>Aktivieren von Objekten für die Verfolgung von nach verfolgten Händen

In diesem Abschnitt konfigurieren wir das zuvor erstellte Cube-Spielobjekt so, dass es die nach verfolgten Hände des Benutzers mithilfe des radialview-Solvers befolgt.

1. Wählen Sie das Cube-Objekt in der basescene-Hierarchie aus. Klicken Sie im Inspektor-Panel auf Komponente hinzufügen. Geben Sie im Suchfeld radialview ein, und wählen Sie die Komponente radialview aus, um Sie dem Cube hinzuzufügen. Die Komponente solverhandler wird dem Cube ebenfalls automatisch hinzugefügt.

    ![mrlearning-Base-CH3-3-step3. png](images/mrlearning-base-ch3-3-step1.png)

2. Um die radialview so zu ändern, dass Sie auf eine Hand anstelle des Kopfes folgt, wählen Sie das Dropdown Menü neben der Option überwachten Zieltyp aus, und wählen Sie im Menü Handgelenk aus.

    ![mrlearning-Base-CH3-3-step2. png](images/mrlearning-base-ch3-3-step2a.png)

    Nun sehen Sie zwei neue Optionen: Überarbeitungen und nach verfolgte Handgelenk. In diesem Beispiel verwenden Sie die radialview, wie in der folgenden Abbildung dargestellt, auf das Handgelenk der linken Seite.

    ![mrlearning-Base-CH3-3-step2b. png](images/mrlearning-base-ch3-3-step2b.png)

3. Legen Sie den maximalen und den minimalen Abstand der radialen Ansicht auf 0 fest, damit der Cube keinen Abstand zwischen ihm und dem Handgelenk des Benutzers hat. Nach der Einstellung ist der Würfel perfekt mit dem Handgelenk ausgerichtet. Sie können auch das Feld Bezugs Richtung anpassen, um das Verhalten des Cubes anzupassen, z. b. Wenn Sie zulassen möchten, dass das Objekt mit dem Handgelenk des Benutzers gedreht wird, indem die Verweis Richtung auf objektorientiert festgelegt wird.

    ![mrlearning-Base-CH3-3-step3. png](images/mrlearning-base-ch3-3-step3.png)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, wie Sie mit den Solvers von mrtk eine Benutzeroberfläche intuitiv auf den Benutzer anwenden können. Sie haben auch erfahren, wie Sie einen Solver an ein Spielobjekt (z. B. einen Würfel) anfügen, um den nachverfolgten Händen des Benutzers zu folgen. Weitere Informationen zu diesen und anderen Solvern, die im MRTK enthalten sind, finden Sie auf der Seite [Solver der MRTK-Dokumentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).

[Nächste Lektion: 5. Interaktion mit 3D-Objekten](mrlearning-base-ch4.md)
