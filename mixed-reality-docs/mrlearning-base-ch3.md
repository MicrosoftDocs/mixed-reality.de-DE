---
title: MR-Basislernmodul – Dynamische Inhaltsplatzierung und Solver
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 6f05b2cecd388b1b2f13e7e5228bc90091eee3bd
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66270403"
---
# <a name="mr-learning-base-module---dynamic-content-placement-and-solvers"></a>MR-Basislernmodul – Dynamische Inhaltsplatzierung und Solver

Hologramme werden in der HoloLens 2 lebendig, wenn sie dem Benutzer intuitiv folgen und in der physischen Umgebung so platziert werden, dass die Interaktion reibungslos und stilvoll verläuft. In Lektion 3 werden wir Möglichkeiten zur dynamischen Platzierung von Hologrammen mit den verfügbaren Platzierungstools des MRTK untersuchen, den so genannten „Solvern“. Sie werden als „Solver“ bezeichnet, da sie komplexe räumliche Plazierungsalgorithmen lösen. Im MRTK stellen Solver ein System von Skripts und Verhaltensweisen dar, die wir dazu verwenden, dass es Benutzeroberflächenelementen ermöglicht wird, dem Benutzer oder anderen Spielobjekten in der Szene folgen zu können. Sie können auch verwendet werden, um schnell an bestimmten Positionen anzudocken, wodurch Ihre Anwendung intuitiver gestaltet wird. 

## <a name="objectives"></a>Ziele

* Einführen der MRTK-Solver
* Verwenden von Solvern, damit eine Sammlung von Schaltflächen dem Benutzer folgt
* Verwenden von Solvern, damit ein Spielobjekt den nachverfolgten Händen des Benutzers folgt

## <a name="instructions"></a>Anweisungen

### <a name="location-of-solvers-in-the-mrtk"></a>Position der Solver im MRTK
 Um die verfügbaren Solver in Ihrem Projekt zu finden, suchen Sie im MRTK SDK-Ordner (MixedRealityToolkit.SDK-Ordner), dann wird unter dem Ordner der Hilfsprogramme der Ordner der Solver angezeigt, wie in der Abbildung unten dargestellt.

![Solver](images/lesson3_chapter1_step1im.PNG)

>Hinweis: In dieser Lektion werden wir nur auf die Implementierung der Solver „Orbital“ und „RadialView“ eingehen. Weitere Informationen zur gesamten Palette der im MRTK verfügbaren Solver finden Sie unter: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html

### <a name="use-a-solver-to-follow-the-user"></a>Verwenden eines Solvers zum Folgen des Benutzers
Ziel dieses Kapitels ist es, die von uns zuvor erstellte Schaltflächensammlung so zu erweitern, dass sie der Blickrichtung des Benutzers folgt. In der vorherigen Version des MRTK und HoloToolkit wurde dies als „taglong“-Funktionalität bezeichnet.

1. Wählen Sie das übergeordnete Objekt der Schaltflächensammlung aus der vorherigen Lektion aus.

![Lektion3 Kapitel2 Schritt1im](images/Lesson3_chapter2_step1im.PNG)

2. Klicken Sie im Inspektorbereich auf die Schaltfläche „Add Component“ (Komponente hinzufügen), und suchen Sie nach „Orbital“. Die Komponente „Orbital“ sollte angezeigt werden. Wählen Sie diese Komponente aus, um sie zum Spielobjekt „Button Collection“ (Schaltflächensammlung) hinzuzufügen.

![Lektion3 Kapitel2 Schritt2im](images/Lesson3_Chapter2_step2im.PNG)

>Hinweis: Wenn Sie die Komponente hinzufügen, werden Sie feststellen, dass das System das Orbital-Skript und das Solverhandler-Skript auf der Inspektorregisterkarte hinzufügt, die eine erforderliche Komponente darstellt. 

3. Um die Schaltflächensammlung so zu konfigurieren, dass sie dem Benutzer folgt, müssen wir die folgenden Anpassungen implementieren (siehe auch die folgende Abbildung):
- Legen Sie im Orbital-Skript die Dropdownliste für den Ausrichtungstyp auf „Yaw Only“ (Nur Kursabweichung) fest. Dadurch wird erreicht, dass sich nur eine Achse des Objekts dreht, während es dem Benutzer folgt.
- Legen Sie den lokalen Versatz an allen Achsen auf 0 fest. Stellen Sie den Versatz der Umgebung auf „x = 0“, „y = -0,1“ und „z = 0,6“ ein. Dadurch wird die Bewegung des Objekts gesperrt, sodass das Objekt, wenn der Benutzer die Höhe ändert, in der physischen Umgebung auf einer festen Höhe verbleibt, während es gleichzeitig dem Benutzer folgen kann, während sich der Benutzer durch die Umgebung bewegt. Diese Werte können angepasst werden, um ein breites Spektrum an Verhaltensweisen zu erreichen.
- Für ein Folgeverhalten, bei dem die Schaltflächen erst dann der Ansicht des Benutzers folgen, wenn der Benutzer seinen Kopf ausreichend weit gedreht hat, können Sie das Kontrollkästchen „Use Angle Stepping for world offset“ (Winkelabstufung für Umgebungsversatz verwenden) aktivieren (Hinweis: Dieser Titel wird auf einigen Bildschirmen möglicherweise abgeschnitten, wie in der folgenden Abbildung veranschaulicht.) Damit das Objekt dem Benutzer z. B. nur alle 90 Grad folgt, stellen Sie die Anzahl der Schritte auf 4 ein (im Beispiel links durch einen grünen Pfeil markiert). 

![Lektion3 Kapitel2 Schritt3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>Es Objekten ermöglichen, nachverfolgten Händen zu folgen

In diesem Abschnitt konfigurieren wir das zuvor erstellte Würfelspielobjekt, um den nachverfolgten Händen des Benutzers mit dem RadialView-Solver zu folgen.

1. Wählen Sie das Cube-Objekt (Würfel) in der BaseScene-Hierarchie aus. Klicken Sie im Inspektorbereich auf „Add Component“ (Komponente hinzufügen). 

![Lektion3 Kapitel3 Schritt1im](images/Lesson3_Chapter3_step1im.PNG)

2. Geben Sie „RadialView“ in das Suchfeld ein, und wählen Sie die RadialView-Komponente aus, um sie dem Würfel hinzuzufügen. Die Solverhandler-Komponente wird ebenfalls automatisch dem Würfel hinzugefügt.

3. Ändern Sie die radiale Ansicht, um nicht dem Kopf zu folgen, sondern der linken Hand. Wählen Sie das Dropdownmenü neben der Option „tracked object to reference“ (Nachverfolgtes Objekt für Referenz). Wählen Sie dann aus dem Menü „Hand Joint left“ (Handgelenk links) aus.

![Lektion3 Kapitel3 Schritt3im](images/Lesson3_chapter3_step3im.PNG)

4. Nachdem Sie das Handgelenk ausgewählt haben, können Sie wählen, welchem Teil der Hand der Würfel folgen soll. Für dieses Beispiel werden wir das Handgelenk verwenden. Wählen Sie neben der Option „Tracked Hand Joint“ (Nachverfolgtes Handgelenk) das Dropdownmenü und dann „Wrist“ (Handgelenk) aus. 

![Lektion3 Kapitel3 Schritt4im](images/Lesson3_chapter3_step4im.PNG)

5. Legen Sie den maximalen und minimalen Abstand auf 0 fest, damit der Würfel keinen Abstand zwischen ihm und dem Handgelenk des Benutzers aufweist. Nach der Einstellung ist der Würfel perfekt mit dem Handgelenk ausgerichtet. Sie können auch das Feld „Reference Direction“ (Referenzrichtung) anpassen, um das Verhalten bei der Ausrichtung des Würfels anzupassen (z. B. wenn Sie das Objekt mit dem Handgelenk des Benutzers drehen lassen möchten, stellen Sie die Referenzrichtung auf „Orient with Tracked Object“ (An nachverfolgtem Objekt ausrichten) ein).

![Lektion3 Kapitel3 Schritt5im](images/Lesson3_chapter3_step5im.PNG)

### <a name="congratulations"></a>Herzlichen Glückwunsch!
Gratulation! In dieser Lektion haben Sie erfahren, wie Sie die MRTK-Solver verwenden können, damit eine Benutzeroberfläche intuitiv dem Benutzer folgt. Sie haben auch erfahren, wie Sie einen Solver an ein Spielobjekt (z. B. einen Würfel) anfügen, um den nachverfolgten Händen des Benutzers zu folgen. Weitere Informationen zu diesen und anderen Solvern, die im MRTK enthalten sind, finden Sie auf der Seite [Solver der MRTK-Dokumentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).

[Nächste Lektion: 3D-Objektinteraktion](mrlearning-base-ch4.md)

