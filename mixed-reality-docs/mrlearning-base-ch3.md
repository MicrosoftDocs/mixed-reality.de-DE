---
title: 'Tutorials zu den ersten Schritten: 4. Platzieren von dynamischem Inhalt und Verwenden von Solvers'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 93fcdcdfb7941f377b2f3f7786368783415b1ef2
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438404"
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

>Hinweis: in dieser Lektion überprüfen wir nur die Implementierung des "Orbital Solver" und des radialview-Solver. Weitere Informationen über die vollständige Palette der in der mrtk verfügbaren Solver finden Sie unter: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html

### <a name="use-a-solver-to-follow-the-user"></a>Verwenden eines Solvers zum Folgen des Benutzers
Das Ziel dieses Kapitels besteht darin, die zuvor erstellte Schaltflächen Auflistung zu verbessern, sodass Sie der Blick Richtung des Benutzers folgt. In der vorherigen Version von mrtk und holotoolkit wurde dies als Tagalong-Funktionalität bezeichnet.

1. Wählen Sie das übergeordnete Objekt der Schaltflächensammlung aus der vorherigen Lektion aus.

![Lektion3 Kapitel2 Schritt1im](images/Lesson3_chapter2_step1im.PNG)

2. Klicken Sie im Inspektor-Panel auf die Schaltfläche Komponente hinzufügen, und suchen Sie nach "Orbital". Die Komponente "Orbital" sollte angezeigt werden. Wählen Sie diese Option aus, um die Komponente "Orbital" dem Auflistungs Spielobjekt hinzuzufügen

![Lektion3 Kapitel2 Schritt2im](images/Lesson3_Chapter2_step2im.PNG)

>Hinweis: Wenn Sie die Komponente "Orbital" hinzufügen, werden Sie feststellen, dass das System auch die Komponente "solverhandler" hinzufügt, die eine erforderliche Komponente ist. 

3. Um die Schaltflächen Auflistung so zu konfigurieren, dass Sie dem Benutzer folgt, müssen wir die folgenden Anpassungen implementieren (siehe Abbildung unten):
- Legen Sie im Skript für die Ausrichtung der Ausrichtungs Typen-Dropdown Liste nur auf "Yaw" fest. Dadurch wird erreicht, dass sich nur eine Achse des Objekts dreht, während es dem Benutzer folgt.
- Legen Sie den lokalen Versatz an allen Achsen auf 0 fest. Legen Sie den Welt Offset auf x = 0, y =-0,1 und z = 0,6 fest. Dadurch wird die Bewegung des Objekts gesperrt, sodass das Objekt bei einer Änderung der Höhe in der physischen Umgebung in einer festgelegten Höhe verbleibt, während es dem Benutzer weiterhin gestattet, wenn der Benutzer die Umgebung bewegt. Diese Werte können angepasst werden, um ein breites Spektrum an Verhaltensweisen zu erreichen.
- Für ein nachfolgendes Verhalten, bei dem die Schaltflächen nur der Ansicht des Benutzers folgen, wenn der Benutzer die Kopfzeile in der Hand hat, können Sie das Kontrollkästchen "Winkel Sprung für Welt Offset verwenden" auswählen (Hinweis: dieser Titel kann auf einigen Bildschirmen abgeschnitten werden, wie er in der Abbildung unten dargestellt ist.) Wenn das Objekt z. b. nur alle 90 Grad dem Benutzer folgen soll, legen Sie die Anzahl der Schritte auf 4 (im folgenden Beispiel mit einem grünen Pfeil gekennzeichnet) fest. 

![Lektion3 Kapitel2 Schritt3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>Aktivieren von Objekten für die Verfolgung von nach verfolgten Händen

In diesem Abschnitt konfigurieren wir das zuvor erstellte Cube-Spielobjekt so, dass es die nach verfolgten Hände des Benutzers mithilfe des radialview-Solvers befolgt.

1. Wählen Sie das Cube-Objekt in der basescene-Hierarchie aus. Klicken Sie im Inspektor-Panel auf Komponente hinzufügen. 

![Lektion3 Kapitel3 Schritt1im](images/Lesson3_Chapter3_step1im.PNG)

2. Geben Sie im Suchfeld radialview ein, und wählen Sie die Komponente radialview aus, um Sie dem Cube hinzuzufügen. Die Komponente solverhandler wird dem Cube ebenfalls automatisch hinzugefügt.

3. Um die radialview so zu ändern, dass Sie auf die linke Seite anstatt auf den Kopf folgt, wählen Sie das Dropdown Menü neben der Option überwachter Objekt als Verweis aus, und wählen Sie dann im Menü die Option Handgelenk Links aus.

![Lektion3 Kapitel3 Schritt3im](images/Lesson3_chapter3_step3im.PNG)

4. Nachdem Sie das Handgelenk ausgewählt haben, können Sie wählen, welchem Teil der Hand der Würfel folgen soll. Für dieses Beispiel werden wir das Handgelenk verwenden. Wählen Sie neben der Option überwachte Hand Gelenk das Dropdown Menü aus, und wählen Sie dann Hand. 

![Lektion3 Kapitel3 Schritt4im](images/Lesson3_chapter3_step4im.PNG)

5. Legen Sie den maximalen und minimalen Abstand auf 0 fest, damit der Würfel keinen Abstand zwischen ihm und dem Handgelenk des Benutzers aufweist. Nach der Einstellung ist der Würfel perfekt mit dem Handgelenk ausgerichtet. Sie können auch das Feld Bezugs Richtung anpassen, um das Verhalten des Cubes anzupassen, z. b. Wenn Sie zulassen möchten, dass das Objekt mit dem Handgelenk des Benutzers gedreht wird, indem die Verweis Richtung auf die Ausrichtung mit dem überwachten Objekt festgelegt wird.

![Lektion3 Kapitel3 Schritt5im](images/Lesson3_chapter3_step5im.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!
In diesem Tutorial haben Sie gelernt, wie Sie mit den Solvers von mrtk eine Benutzeroberfläche intuitiv auf den Benutzer anwenden können. Sie haben auch erfahren, wie Sie einen Solver an ein Spielobjekt (z. B. einen Würfel) anfügen, um den nachverfolgten Händen des Benutzers zu folgen. Weitere Informationen zu diesen und anderen Solvern, die im MRTK enthalten sind, finden Sie auf der Seite [Solver der MRTK-Dokumentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).

[Nächste Lektion: 5. Interaktion mit 3D-Objekten](mrlearning-base-ch4.md)

