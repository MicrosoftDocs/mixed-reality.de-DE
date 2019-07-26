---
title: MR-Basislernmodul – Dynamische Inhaltsplatzierung und Solver
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 401c667ef80042da9182b7f4e065dfd6884cf061
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485687"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. Platzieren von dynamischem Inhalt und Verwenden von Solvers

Hologramme werden in der HoloLens 2 lebendig, wenn sie dem Benutzer intuitiv folgen und in der physischen Umgebung so platziert werden, dass die Interaktion reibungslos und stilvoll verläuft. In diesem Tutorial wird erläutert, wie Sie Hologramme dynamisch mithilfe der verfügbaren Platzierungs Tools von mrtk platzieren, die als Solver bezeichnet werden, um komplexe räumliche Platzierungs Szenarien zu lösen. In den mrtk sind Solvers ein System aus Skripts und Verhalten, mit denen Benutzeroberflächen Elemente Ihnen, dem Benutzer oder anderen Spielobjekten in der Szene folgen können. Sie können auch verwendet werden, um schnell an bestimmten Positionen anzudocken, wodurch Ihre Anwendung intuitiver gestaltet wird. 

## <a name="objectives"></a>Ziele

* Einführen der MRTK-Solver
* Verwenden von Solvern, damit eine Sammlung von Schaltflächen dem Benutzer folgt
* Verwenden von Solvern, damit ein Spielobjekt den nachverfolgten Händen des Benutzers folgt

## <a name="instructions"></a>Anweisungen

### <a name="location-of-solvers-in-the-mrtk"></a>Position der Solver im MRTK
 Um die verfügbaren Solver in Ihrem Projekt zu finden, suchen Sie im MRTK SDK-Ordner (MixedRealityToolkit.SDK-Ordner), dann wird unter dem Ordner der Hilfsprogramme der Ordner der Solver angezeigt, wie in der Abbildung unten dargestellt.

![Solver](images/lesson3_chapter1_step1im.PNG)

>Hinweis: In dieser Lektion wird nur die Implementierung des "Orbital Solver" und des radialview-Solvers durchlaufen. Weitere Informationen zur gesamten Palette der im MRTK verfügbaren Solver finden Sie unter: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html

### <a name="use-a-solver-to-follow-the-user"></a>Verwenden eines Solvers zum Folgen des Benutzers
Das Ziel dieses Kapitels besteht darin, die zuvor erstellte Schaltflächen Auflistung zu verbessern, sodass Sie der Blick Richtung des Benutzers folgt. In früheren Versionen von mrtk und holotoolkit wurde dies als Tagalong-Funktionalität bezeichnet.

1. Wählen Sie das übergeordnete Objekt der Schaltflächensammlung aus der vorherigen Lektion aus.

![Lektion3 Kapitel2 Schritt1im](images/Lesson3_chapter2_step1im.PNG)

2. Klicken Sie im Inspektor-Panel auf die Schaltfläche Komponente hinzufügen, und suchen Sie nach "Orbital". Die Komponente „Orbital“ sollte angezeigt werden. Wählen Sie diese Komponente aus, um sie zum Spielobjekt „Button Collection“ (Schaltflächensammlung) hinzuzufügen.

![Lektion3 Kapitel2 Schritt2im](images/Lesson3_Chapter2_step2im.PNG)

>Hinweis: Wenn Sie die Komponente hinzufügen, werden Sie feststellen, dass das System das Orbital-Skript und das Solverhandler-Skript auf der Inspektorregisterkarte hinzufügt, die eine erforderliche Komponente darstellt. 

3. Um die Schaltflächen Auflistung so zu konfigurieren, dass Sie dem Benutzer folgt, müssen wir die folgenden Anpassungen implementieren (siehe Abbildung unten):
- Legen Sie im Skript für die Ausrichtung der Ausrichtungs Typen-Dropdown Liste nur auf "Yaw" fest. Dadurch wird erreicht, dass sich nur eine Achse des Objekts dreht, während es dem Benutzer folgt.
- Legen Sie den lokalen Versatz an allen Achsen auf 0 fest. Stellen Sie den Versatz der Umgebung auf „x = 0“, „y = -0,1“ und „z = 0,6“ ein. Dadurch wird die Bewegung des Objekts gesperrt, sodass das Objekt, wenn der Benutzer die Höhe ändert, in der physischen Umgebung auf einer festen Höhe verbleibt, während es gleichzeitig dem Benutzer folgen kann, während sich der Benutzer durch die Umgebung bewegt. Diese Werte können angepasst werden, um ein breites Spektrum an Verhaltensweisen zu erreichen.
- Für ein nachfolgenden Verhalten, bei dem die Schaltflächen nur der Ansicht des Benutzers folgen, nachdem der Benutzer den Kopf oder den Anfang erreicht hat, können Sie das Kontrollkästchen "Angle Stepping for World Offset verwenden" auswählen (Hinweis: Dieser Titel wird auf einigen Bildschirmen möglicherweise abgeschnitten, wie in der folgenden Abbildung veranschaulicht.) Damit das Objekt dem Benutzer z. B. nur alle 90 Grad folgt, stellen Sie die Anzahl der Schritte auf 4 ein (im Beispiel links durch einen grünen Pfeil markiert). 

![Lektion3 Kapitel2 Schritt3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>Aktivieren von Objekten für die Verfolgung von nach verfolgten Händen

In diesem Abschnitt konfigurieren wir das zuvor erstellte Würfelspielobjekt, um den nachverfolgten Händen des Benutzers mit dem RadialView-Solver zu folgen.

1. Wählen Sie das Cube-Objekt (Würfel) in der BaseScene-Hierarchie aus. Klicken Sie im Inspektor-Panel auf Komponente hinzufügen. 

![Lektion3 Kapitel3 Schritt1im](images/Lesson3_Chapter3_step1im.PNG)

2. Geben Sie im Suchfeld radialview ein, und wählen Sie die Komponente radialview aus, um Sie dem Cube hinzuzufügen. Die Solverhandler-Komponente wird ebenfalls automatisch dem Würfel hinzugefügt.

3. Ändern Sie die radiale Ansicht, um nicht dem Kopf zu folgen, sondern der linken Hand. Wählen Sie das Dropdown Menü neben der Option überwachter Objekt als Verweis aus. Wählen Sie dann im Menü die Option Hand Gelenk Links aus.

![Lektion3 Kapitel3 Schritt3im](images/Lesson3_chapter3_step3im.PNG)

4. Nachdem Sie das Handgelenk ausgewählt haben, können Sie wählen, welchem Teil der Hand der Würfel folgen soll. Für dieses Beispiel werden wir das Handgelenk verwenden. Wählen Sie neben der Option überwachte Hand Gelenk das Dropdown Menü aus, und wählen Sie dann Hand. 

![Lektion3 Kapitel3 Schritt4im](images/Lesson3_chapter3_step4im.PNG)

5. Legen Sie den maximalen und minimalen Abstand auf 0 fest, damit der Würfel keinen Abstand zwischen ihm und dem Handgelenk des Benutzers aufweist. Nach der Einstellung ist der Würfel perfekt mit dem Handgelenk ausgerichtet. Sie können auch das Feld Bezugs Richtung anpassen, um das Verhalten des Cubes anzupassen, z. b. Wenn Sie zulassen möchten, dass das Objekt mit dem Handgelenk des Benutzers gedreht wird, indem die Verweis Richtung auf die Ausrichtung mit dem überwachten Objekt festgelegt wird.

![Lektion3 Kapitel3 Schritt5im](images/Lesson3_chapter3_step5im.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!
In diesem Tutorial haben Sie gelernt, wie Sie mit den Solvers von mrtk eine Benutzeroberfläche intuitiv auf den Benutzer anwenden können. Sie haben auch erfahren, wie Sie einen Solver an ein Spielobjekt (z. B. einen Würfel) anfügen, um den nachverfolgten Händen des Benutzers zu folgen. Weitere Informationen zu diesen und anderen Solvern, die im MRTK enthalten sind, finden Sie auf der Seite [Solver der MRTK-Dokumentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).

[Nächste Lektion: 5.    Interagieren mit 3D-Objekten](mrlearning-base-ch4.md)

