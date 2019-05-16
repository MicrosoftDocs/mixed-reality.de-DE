---
title: MR-Learning-Basis-Modul – dynamischer Inhalt Platzierung und Hochleistungscomputings
description: Führen Sie diesen Kurs erfahren, wie Sie Azure-Gesichtserkennung innerhalb einer mixed Reality-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: Gemischte Realität, Unity, Tutorial, hololens
ms.openlocfilehash: 04ed2217c473c5649c1850fcc757d866e23b9b56
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730896"
---
# <a name="mr-learning-base-module---dynamic-content-placement-and-solvers"></a>MR-Learning-Basis-Modul – dynamischer Inhalt Platzierung und Hochleistungscomputings

Hologramme sind zum Leben in HoloLens 2 auf, wenn sie intuitiv folgen Sie dem Benutzer und werden in der physischen Umgebung auf eine Weise, mit der Interaktion nahtlose und elegante, platziert. In Lektion 3 erforschen wir Möglichkeiten, mithilfe der MRTKs möglichen Platzierung Tools, bekannt als "Hochleistungscomputings." Hologramme dynamisch zu platzieren. Sie werden als "Hochleistungscomputings" für die Möglichkeit bezeichnet, die Sie komplexe räumliche Platzierung Algorithmen lösen. In der MRTK sind Hochleistungscomputings ein System von Skripts und Verhaltensweisen, die wir verwenden, um die UI-Elemente für Sie, den Benutzer oder andere Spielobjekte in der Szene folgen zu können. Sie können auch verwendet werden, schnell an eine bestimmte Position andocken wird Ihre Anwendung intuitiver. 

## <a name="objectives"></a>Ziele

* Führen Sie die MRTKs Hochleistungscomputings
* Hochleistungscomputings verwenden, um eine Sammlung von Schaltflächen zu erhalten, folgen Sie dem Benutzer
* Hochleistungscomputings verwenden, um einem spielobjekt zu erhalten. Führen Sie die nachverfolgten Hände des Benutzers

## <a name="instructions"></a>Anweisungen

### <a name="location-of-solvers-in-the-mrtk"></a>Speicherort des Hochleistungscomputings in die MRTK
 Um die verfügbaren Hochleistungscomputings in Ihrem Projekt suchen, sehen Sie Sie im MRTK SDK-Ordner (MixedRealityToolkit.SDK Ordner), klicken Sie dann im Ordner "Utilities" wird den Ordner Hochleistungscomputings angezeigt, wie in der folgenden Abbildung dargestellt.

![Hochleistungscomputings](images/lesson3_chapter1_step1im.PNG)

>Hinweis: In dieser Lektion werden wir nur Implementierung von "Orbitalschüttler" Solver "und" Solver "RadialView" besprochen. Weitere Informationen zu den vollen Umfang der Hochleistungscomputings zur Verfügung, in der MRTK finden Sie unter: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html

### <a name="use-a-solver-to-follow-the-user"></a>Verwenden Sie eine Solver, um der Benutzer folgen
Das Ziel dieses Kapitels ist die Auflistung von Schaltflächen zu verbessern, die wir zuvor erstellt haben, dass dabei die Blicke Richtung des Benutzers. In vorherigen Version der MRTK und HoloToolkit wurde dies als eine Funktion "Taglong" bezeichnet.

1. Wählen Sie die Auflistung der Schaltflächen übergeordnete-Objekt, aus der vorherigen Lektion.

![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. Klicken Sie im Bereich mit den Inspektor auf die Schaltfläche "Komponente hinzufügen" und suchen Sie nach "Orbitalschüttler." Die Orbitalschüttler Komponente sollte angezeigt werden. Wählen sie die Auflistung der Schaltflächen-spielobjekt Orbitalschüttler Komponente hinzu.

![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

>Hinweis: Wenn Sie die Komponente hinzufügen, werden Sie feststellen, dass das System die Orbitalschüttler Skript und das Skript der Solver-Handler in der Registerkarte "Inspector" Fügt einer erforderlichen Komponente. 

3. Um die Auflistung der Schaltflächen, um den Benutzer folgen konfigurieren zu können, müssen wir die folgenden Anpassungen implementieren (auch finden Sie in der folgenden Abbildung):
- Legen Sie im Skript Orbitalschüttler der Dropdown-Liste "Ausrichtung Type" auf "Nur Yaw". Dies macht es, sodass dieser nur eine Achse des Objekts dreht, wie es den Benutzer folgt.
- Legen Sie den lokalen Offset auf 0 für alle Achsen. Legen Sie die Welt versetzt auf X = 0, y =-0.1 und Z = 0,6. Dadurch wird die Bewegung des Objekts, wenn der Benutzer Höhe ändert, das Objekt ein fester Wert in der physischen Umgebung, bleibt und dennoch damit der Benutzer befolgen, wenn der Benutzer über die Umgebung bewegt gesperrt. Diese Werte können angepasst werden, um einen Bereich Wade Verhalten zu erzielen.
- Für ein folgen-Verhalten, bei dem die Schaltflächen nur führen Sie die Ansicht des Benutzers nach der Benutzer seine Head ausreichend weit aktiviert, Sie können das Kontrollkästchen "Verwendung Winkel ausführen in Einzelschritten für World Offset" (Beachten Sie: Dieser Titel möglicherweise in einigen Bildschirmen abgeschnitten, da es in der folgenden Abbildung ist.) Z. B. wenn das Objekt, das der Benutzer nur alle 90 Grad befolgen, legen Sie die Anzahl der Schritte gleich 4 (gekennzeichnet durch ein grüner Pfeil im Beispiel auf der linken Seite). 

![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>Aktivieren von Objekten für die nachverfolgte praktische Folgen

In diesem Abschnitt konfigurieren wir die Cube-spielobjekt zuvor erstellt haben, um des Benutzers nachverfolgten Hände, die mit der Solver RadialView folgen.

1. Wählen Sie in der Hierarchie BaseScene das Cubeobjekt. Klicken Sie auf "Komponente hinzufügen" in den Bereich der Eigenschaftenanalyse. 

![Lesson3 Chapter3 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. Geben Sie in "RadialView" in das Suchfeld ein, und wählen Sie die RadialView-Komponente, die sie zum Cube hinzugefügt. Die Solver Handler-Komponente wird automatisch auch für den Cube hinzugefügt.

3. Ändern Sie die radiale Ansicht aus, um nicht befolgen die Kopfzeile, jedoch führen die Links. Wählen Sie im Dropdownmenü neben der Option "verfolgt Objekt zu verweisen". Wählen Sie dann im Menü "übergeben, Joint Links".

![Lesson3 Chapter3 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. Nachdem Sie die Verbindung manuell ausgewählt haben, können Sie auswählen, welcher Teil der Hand des Cubes folgen soll. In diesem Beispiel werden wir das Handgelenk verwenden. Neben der Option "überwachte Hand Joint" wählen im Dropdown-Menü und Handgelenk. 

![Lesson3 Chapter3 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. Die maximale und minimale Abstände auf 0 festgelegt, damit der Cube keine Entfernung zwischen ihnen und der Benutzer den Finger sein kann. Nach dem festlegen wird der Cube genau mit dem Finger ausgerichtet sein. Sie können auch das Feld "Verweis-Richtung" zum Anpassen des Verhaltens wie der Cube ausgerichtet ist (z. B., wenn Sie möchten, dass das Objekt drehen, mit der Benutzer den Finger, Festlegen der Richtung "Referenz" in "Orient mit nachverfolgt Object") anpassen

![Lesson3 Chapter3 Step5im](images/Lesson3_chapter3_step5im.PNG)

### <a name="congratulations"></a>Herzlichen Glückwunsch!
Herzlichen Glückwunsch! In dieser Lektion haben Sie gelernt, wie Sie die MRTKs Hochleistungscomputings verwenden, um eine Benutzeroberfläche, die der Benutzer intuitiv zu befolgen. Sie haben zudem eine Solver spielobjekt (d. h. Cube) des Benutzers nachverfolgten praktische Folgen anfügen. Weitere Informationen zu diesen und anderen Hochleistungscomputings enthalten, mit der MRTK gerne finden Sie auf die [MRTK Hochleistungscomputings-Dokumentationsseite](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).

[Nächste Lektion: 3D-Objekt Interaktion](mrlearning-base-ch4.md)

