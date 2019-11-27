---
title: 'Tutorials zu den ersten Schritten: 3. Erstellen einer Benutzeroberfläche und Konfigurieren von Mixed Reality Toolkit'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: f0a54bb591479dbe8ffa719cb5e6a9d846f67f9e
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539744"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. Erstellen einer Benutzeroberfläche und Konfigurieren von Mixed Reality Toolkit

In der vorherigen Lektion haben Sie einige Funktionen kennengelernt, die das Mixed Reality Toolkit (mrtk) bietet, indem Sie Ihre erste Anwendung für die hololens 2 starten. In der nächsten Lektion erfahren Sie, wie Sie Schaltflächen zusammen mit UI-Textbereichen erstellen und organisieren und die Standard Interaktion (Toucheingabe) verwenden, um mit den einzelnen Schaltflächen zu interagieren. Sie werden auch das Hinzufügen einfacher Aktionen und Effekte untersuchen, z. B. das Ändern von Größe, Klang und Farbe von Objekten. Dieses Modul führt grundlegende Konzepte zum Ändern von mrtk-Profilen ein, beginnend mit dem Ausschalten der Mesh-Visualisierung für [räumliche Karten](spatial-mapping.md) .

## <a name="objectives"></a>Ziele

* Anpassen und Konfigurieren von Mixed Reality-Toolkitprofilen
* Interagieren mit holograms mithilfe von Benutzeroberflächen Elementen und Schaltflächen
* Grundlegende Eingaben und Interaktionen zum Handtracking

## <a name="instructions"></a>Anweisungen

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>So konfigurieren Sie die Mixed Reality Toolkit-profile (Anzeige Option ' räumliches Bewusstsein ändern ')

In diesem Abschnitt erfahren Sie, wie Sie die standardmäßigen mrtk-profile anpassen und konfigurieren, indem Sie die Anzeigeoption des Bereichs räumliches Bewusstsein anpassen. Sie können dieselben Prinzipien befolgen, um Einstellungen oder Werte in den MRTK-Profilen anzupassen.

1. Wählen Sie "Mixed-Reality Toolkit" (mrtk) aus der basescene-Hierarchie aus. Suchen Sie im Inspektor-Panel nach dem Mixed Reality Toolkit-Skript, und wählen Sie das aktive Profil aus, wie in der folgenden Abbildung dargestellt. Doppelklicken Sie, um es zu öffnen.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step1.png)

    >[!NOTE]
    >Standardmäßig können die MRTK-Profile nicht bearbeitet werden. Dabei handelt es sich um Standardprofil Vorlagen, die Sie kopieren und anpassen können. Es gibt mehrere Ebenen von Anpassung und Profilen. Daher ist es eine Standardübung, mehrere Profile zu kopieren und anzupassen, wenn Sie eine oder mehrere Einstellungen konfigurieren.
    >
    >Weitere Informationen zu mrtk-Profilen und deren Architektur finden Sie in der [mrtk-Dokumentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html>).

2. Erstellen Sie eine Kopie des Standardprofils, um es anzupassen. Klicken Sie zunächst auf **Kopieren & anpassen**.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step2a.png)

    Dadurch wird das Popup Fenster " *Klon Profil* " geöffnet.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step2b.png)

    Klicken Sie auf **Klonen** , um eine Kopie des mrtk-Profils zu erstellen. Mit ihrer eigenen Kopie des mrtk-Profils können Sie nun alle Einstellungen in diesem Profil anpassen. Außerdem müssen Sie den Schritt zum Kopieren und anpassen für alle zusätzlichen Profile wiederholen, die unter diesem Profil geschildert werden, wie in den nachfolgenden Schritten beschrieben.

3. Deaktivieren Sie die Sichtbarkeit des Gittermodells zur räumlichen Wahrnehmung. Zu diesem Zweck suchen Sie die Systemeinstellungen für räumliche Informationen, wie in der folgenden Abbildung dargestellt. Stellen Sie sicher, dass die Option **räumliches Awareness System aktivieren** aktiviert ist. Klicken Sie auf die Schaltfläche **Klonen** rechts neben dem System Profil räumliches Bewusstsein, um das Standardprofil durch eine anpassbare Kopie zu ersetzen. Klicken Sie im angezeigten Popup Fenster auf die Schaltfläche **Klonen** , wie in der zweiten Abbildung unten gezeigt.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step3a.png)

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step3b.png)

4. Erstellen Sie eine benutzerdefinierte Kopie des standardmäßigen Mixed Reality-Betrachters für räumliche Gittermodelle. Klicken Sie auf den Pfeil nach unten neben Windows Mixed Reality Spatial Mesh Observer, um weitere Optionen anzuzeigen.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4a.png)

    In diesen Optionen wird der standardmäßige gemischte Reality-Mesh-Beobachter angezeigt, der abgeblendet (nicht bearbeitbar) ist. Sie müssen dieses Standardprofil durch eine anpassbare Kopie ersetzen, damit Sie es bearbeiten können. Klicken Sie wie zuvor auf die Schaltfläche **Klonen** , und klicken Sie dann im angezeigten Popup Fenster auf die Schaltfläche **Klonen** , wie in der zweiten Abbildung unten gezeigt.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4b.png)

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4c.png)

5. Als Nächstes passen Sie die Einstellungen für die Anzeigeoption „Occlusion“ (Okklusion) an. Dadurch lässt sich das räumliche Mapping-Mesh unsichtbar machen, blendet jedoch weiterhin Spielobjekte hinter dem räumlichen zuordnungsmesh aus, das auch als oksion bezeichnet wird.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step5.png)

    >[!NOTE]
    >Hinweis: das räumliche Mapping-Netz ist zwar nicht sichtbar, aber es ist immer noch vorhanden, und Sie können damit interagieren. Alle holograms hinter dem räumlichen zuordnungsmesh, z. b. ein – Hologramm hinter der sichtbaren Wand, werden aufgrund der oksions Einstellung nicht angezeigt.

Gratulation! Sie haben soeben erfahren, wie Sie eine Einstellung im MRTK-Profil ändern können. Wie Sie sehen können, müssen Sie, um die MRTK-Einstellungen zu ändern, Kopien der Standardprofile erstellen, damit Sie diese bearbeiten können. Sie verfügen immer über die Standardprofile, die nicht bearbeitet werden können, wenn Sie ein Profil mit neuen Einstellungen erstellen möchten, oder Sie können auf die Standardprofile zurückgreifen. Es gibt zahlreiche Einstellungen, die Sie anpassen können. Einen vollständigen Verweis auf die mrtk-Profileinstellungen finden Sie in der Dokumentation zu mrtk: [https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>Gesten für Handtracking und interaktionsfähige Schaltflächen

In diesem Abschnitt erfahren Sie, wie Sie die Hand Überwachung verwenden, um eine Schaltfläche mit dem Druckvorgang zu drücken.

1. Wählen Sie Assets aus dem Ordner Projekte aus.

2. Geben Sie "PressableButtonHoloLens2" in die Suchleiste ein.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step2.png)

3. Ziehen Sie die vorfab (dargestellt durch ein blaues Feld) mit dem Namen "PressableButtonHoloLens2" in ihre Hierarchie, und legen Sie die Positionswerte auf x = 0, y = 0 und z = 0,2 fest, damit die Schaltfläche vor der Kamera steht. (Die Kamera ist am Ursprung positioniert).

    >[!NOTE]
    >Wenn Sie eine Meldung zu "Importieren von tmp Essentials" erhalten, importieren Sie Sie zu diesem Zeitpunkt. Wenn tmp Essentials noch nicht Bestandteil des Projekts ist, müssen Sie diesen Schritt nach dem Importieren von tmp Essentials möglicherweise wiederholen. andernfalls wird der Schaltflächen Text möglicherweise nicht angezeigt.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step3.png)

4. Fügen Sie der Szene einen Würfel hinzu. Klicken Sie mit der rechten Maustaste auf den Hierarchie Bereich, wählen Sie ein 3D-Objekt aus, und klicken Sie auf Cube.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step6a.png)

    Jetzt sollte sich ein Würfel in Ihrer Anzeige befinden. Es wird sehr groß angezeigt. Sie können die Koordinaten anpassen (während der Cube noch im Hierarchie Bereich ausgewählt ist), um die Größe zu verringern. Legen Sie die Skalierungs Werte auf x = 0,02, y = 0,02 und z = 0,02 fest. Stellen Sie sicher, dass Sie den Cube in der Szene in der Nähe der Schaltfläche positionieren, sich aber nicht damit überlappen. In der folgenden Abbildung ist die Position des Cubes x = 0, y = 0,4 und z = 0,2.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step6b.png)

    >[!NOTE]
    >Im Allgemeinen entspricht 1 Einheit in Unity ungefähr einem Meter in der physischen Umgebung. Hierfür gibt es Ausnahmen: beispielsweise, wenn Objekte untergeordnete Elemente von skalierten Objekten sind.

5. Wenn das PressableButtonHoloLens2-Spielobjekt ausgewählt ist, Scrollen Sie nach unten im Inspektor, um den Abschnitt "Ereignisse" der Komponente "interactable (Skript)" zu suchen.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step4.png)

6. Wir ändern das vorhandene Ereignis, um der Schaltfläche ein Ereignis zuzuweisen, auf das bei einem Pushvorgang reagiert wird. Wie Sie sehen, wird der Ereignis Empfängertyp auf interactableonpressreceiver festgelegt. Dadurch kann die Schaltfläche auf ein gedrücktes Ereignis reagieren, wenn die Schaltfläche von einer nachverfolgten Hand gedrückt wird. An diesem Punkt sollten Sie auch den Interaktions Filter in fast und weit ändern.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step5.png)

7. In diesem Schritt richten Sie den Würfel so ein, dass er die Farbe ändert, wenn Ihre Schaltfläche gedrückt wird. Wählen Sie den PressableButtonHoloLens2 in der basescene-Hierarchie aus, und ziehen Sie das Cube-Spielobjekt aus der basescene-Hierarchie in das Feld nur für die Laufzeit, wie in der folgenden Abbildung dargestellt

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7a.png)

    Klicken Sie in der Dropdown Liste auf keine Funktion. Wählen Sie meshrenderer und dann Material Material aus. Auf diese Weise können Sie das Material ändern, wenn die Schaltfläche gedrückt wird.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7b.png)

    Klicken Sie auf den Kreis neben dem Feld leeres Material, um das Popup Material auswählen zu öffnen. Der mrtk umfasst viele Materialien und Farben, aus denen Sie auswählen können. In diesem Beispiel verwenden Sie das Material, MRTK_Standard_Cyan, indem Sie in der Popup Suchleiste "MRTK_Standard" eingeben. Wählen Sie das MRTK_Standard_Cyan Material aus, um das Feld Material aufzufüllen.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7c.png)

    Das Ereignis ist jetzt so eingestellt, dass beim Drücken der Schaltfläche der Würfel je nach dem von Ihnen angegebenen Material seine Farbe ändert. In diesem Beispiel wechselt der Würfel zur Farbe „Cyan“.

8. Als nächstes richten Sie die releaseaktion ein, sodass die Schaltfläche bei der Veröffentlichung auf die Standardfarbe zurück wechselt. Wiederholen Sie Schritt 7 oben. Diesmal wird jedoch das onRelease-Ereignis anstelle von onPress MRTK_Standard_LightGray Material wie in der folgenden Abbildung dargestellt.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step8.png)

    Wenn nun die Schaltfläche gedrückt wird, wird Sie in eine neue Farbe geändert. Zyan. Wenn die Schaltfläche freigegeben wird, wird Sie wieder in die von Ihnen angegebene Standardfarbe geändert (z. b. hellgrau). Klicken Sie oben auf dem Bildschirm auf die Schaltfläche "Wiedergabe", um Sie im Editor auszuprobieren, oder stellen Sie Sie auf den hololens 2 bereit, um Sie zu testen. Weitere Informationen zur in-Editor-Simulation, einschließlich der Hand Simulation, finden Sie auf der [Dokumentationsseite zur Simulation von mrtk](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>).

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Erstellen eines Schaltflächenbereichs mit der MRTK-Rasterobjektsammlung

In diesem Abschnitt erfahren Sie, wie Sie mit dem gridobjectcollection-Tool von mrtk mehrere Schaltflächen automatisch an einer Benutzeroberfläche anpassen.

1. Duplizieren Sie die Schaltfläche aus dem vorherigen Abschnitt, bis Sie über fünf Schaltflächen verfügen. Hierfür gibt es mehrere Möglichkeiten: Klicken Sie mit der rechten Maustaste auf die Schaltfläche, und klicken Sie auf kopieren. Klicken Sie dann auf die Schaltfläche unterhalb der Schaltfläche, und klicken Sie dann erneut mit der rechten Maustaste auf einfügen.
    Mit der rechten Maustaste auf die Schaltfläche, und klicken Sie auf Duplizieren
    -Verwenden Sie den Tastatur Befehl, indem Sie auf den Cube klicken und auf der Tastatur STRG D drücken.

    Wiederholen Sie diesen Vorgang, bis Sie fünf Schaltflächen haben sehen Sie sich die fünf roten Pfeile in der Abbildung unten an.

    ![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. Gruppieren Sie die Schaltflächen unter einem leeren übergeordneten Spielobjekt. Um die Schaltflächen in der Raster Auflistung zu haben, müssen Sie die Schaltflächen unter einem gemeinsamen übergeordneten Objekt gruppieren. Klicken Sie mit der rechten Maustaste auf den Eintrag, und klicken Sie auf leere erstellen. Dadurch wird ein neues leeres Spielobjekt erstellt, in das Sie alle Schaltflächen einfügen können. Es wird als gameobject angezeigt. Klicken Sie mit der rechten Maustaste, und benennen Sie Sie um.

    ![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. Verschieben Sie alle Schaltflächen in die neue Sammlung. Wählen Sie hierzu alle fünf der Schaltflächen Objekte in ihrer Heide Leiste aus, und ziehen Sie Sie alle unter buttoncollection Game Object, wie in der folgenden Abbildung dargestellt. Tipp: Wählen Sie mehrere Elemente aus, indem Sie die STRG-Taste gedrückt halten und Elemente auswählen.

    ![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. Fügen Sie die Komponente der Raster Objekt Auflistung von mrtk der Schaltflächen Auflistung hinzu. Wählen Sie hierzu das übergeordnete buttoncollection-Objekt aus. Klicken Sie im Inspektor-Panel auf die Schaltfläche Komponente hinzufügen. Suchen Sie in der Suchleiste nach der Raster Objekt Auflistung, und wählen Sie Sie aus, wenn Sie in der Liste angezeigt wird.

    ![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3-step4.png)

    Mit der Raster Objekt Auflistungs Komponente können Sie Schaltflächen oder eine beliebige Gruppe von Objekten in einer ordentlichen Zeile, Spalte oder einem anderen Raster anordnen. Dies ist einer der Bausteine, die von der mrtk bereitgestellt werden, die Ihnen eine schnelle und einfache Möglichkeit bietet, verlockende Benutzeroberflächen zu erstellen.

5. Konfigurieren Sie die Rasterobjektsammlung. Um sicherzustellen, dass alle Schaltflächen dem Benutzer angezeigt werden, wählen Sie die Option "Typ Wählen Sie dann übergeordnete Vorderseite aus, wie in der folgenden Abbildung dargestellt. Ändern Sie anschließend die Zellengröße, um den Abstand zwischen den Schaltflächen festzulegen. Beginnen Sie mit 0,05 Einheiten bis 0,05 Einheiten für die Zellen Breite und die Zellen Höhe, wie in der folgenden Abbildung dargestellt. Stellen Sie sicher, dass die Entfernung auf 0 und die Zeilen auf 1 festgelegt ist. Klicken Sie auf Sammlung aktualisieren. Die Szene ähnelt der Abbildung unten.

    ![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3-step5.png)

    >[!NOTE]
    >Abhängig von der Ausrichtung der untergeordneten Objekte oder des übergeordneten Objekts müssen Sie die Einstellung der Ausrichtung in zukünftigen Projekten wahrscheinlich anders anpassen. Die Felder für die Zellenbreite und Zellenhöhe müssen je nach Größe der Objekte in Ihrer Sammlung möglicherweise ebenfalls anders definiert werden.

### <a name="adding-text-into-your-scene"></a>Hinzufügen von Text zu Ihrer Szene

In diesem Abschnitt erfahren Sie, wie Sie Text zu Ihrer Mixed Reality-Umgebung hinzufügen und ihn bearbeiten können. Wenn Sie dies noch nicht getan haben, stellen Sie sicher, dass textmeshpro in Unity aktiviert ist, indem Sie die [hier](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)aufgeführten Anweisungen befolgen

1. Wählen Sie das übergeordnete Element buttoncollection aus, und klicken Sie mit der rechten Maustaste auf die Sammlung. Erweitern Sie im Dropdown Menü die Option 3D-Objekt. Wählen Sie dann textmeshpro-Text aus. Ein textmeschpro-Objekt sollte unter der Schaltflächen Auflistung angezeigt werden, wie in der folgenden Abbildung dargestellt.

    ![Lesson2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG) ![Lesson2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)

2. Um die Textgröße und die Platzierung für die Lesbarkeit zu verbessern, passen Sie das Feld Schriftart Größe in der textmeschpro-Komponente an, um die Größe der Schriftart zu ändern. Sie müssen auch die Position und Skalierung der Rect-Transformation anpassen, wie in der folgenden Abbildung dargestellt. In den folgenden Abbildungen finden Sie die Werte, die für die Text Konfiguration verwendet werden. Sie können diese Werte als Ausgangspunkt verwenden, um die Größe und Platzierung des Textfelds weiter zu verbessern.

    ![Lesson2 Chapter4 Schritt 3](images/mrlearning-base-ch2-4-step3.png)

3. Geben Sie in das Textfeld der textmeschpro-Komponente im Inspektor-Panel den Text "Schaltflächen-Auflistungs Text" ein, und passen Sie die Ausrichtungs Eigenschaften wie in der folgenden Abbildung dargestellt als zentriert und oben an.

    ![Lesson2 Chapter4 Schritt 4](images/mrlearning-base-ch2-4-step4.png)

4. Klicken Sie zum Ändern der Textwerte auf den Schaltflächen Objekten auf den Pfeil neben einer beliebigen Schaltfläche, um ihn zu erweitern, und navigieren Sie zum seeitsayitlabel-Objekt. Navigieren Sie zu textmeshpro, wo Sie den Text wie in den obigen Schritten beschrieben auf Ihre Schaltflächen bearbeiten können.

    ![Lektion2 Kapitel4 Schritt5](images/Lesson2_Chapter4_Step5.JPG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In dieser Lektion haben Sie gelernt, wie Sie eine mrtk-Profileinstellung (d.h. Sichtbarkeit des räumlichen Informationsnetzes) kopieren, anpassen und konfigurieren. Außerdem haben Sie gelernt, wie Sie mit einer Schaltfläche interagieren können, um Ereignisse mithilfe von nach verfolgten Händen in den hololens 2 zu Triggern Schließlich haben Sie gelernt, wie Sie eine einfache UI-Schnittstelle mit dem Text Mesh pro von Unity und der Komponente der Raster Objekt Auflistung von mrtk erstellen.

[Nächste Lektion: 4. Platzieren von dynamischem Inhalt und Verwenden von Solvers](mrlearning-base-ch3.md)
