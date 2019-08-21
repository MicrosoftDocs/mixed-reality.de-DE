---
title: 'Tutorials zu den ersten Schritten: 3. Erstellen einer Benutzeroberfläche und Konfigurieren von Mixed Reality Toolkit'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 45833ba22305acedb45bfdc9752c0b278a693190
ms.sourcegitcommit: 9636573eabdc78db6875e831a9c894a2ff173a99
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69629185"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. Erstellen einer Benutzeroberfläche und Konfigurieren von Mixed Reality Toolkit 

In der vorherigen Lektion haben Sie einige Funktionen kennengelernt, die das Mixed Reality Toolkit (mrtk) bietet, indem Sie Ihre erste Anwendung für die hololens 2 starten. In der nächsten Lektion erfahren Sie, wie Sie Schaltflächen zusammen mit UI-Textbereichen erstellen und organisieren und die Standard Interaktion (Toucheingabe) verwenden, um mit den einzelnen Schaltflächen zu interagieren. Sie werden auch das Hinzufügen einfacher Aktionen und Effekte untersuchen, z. B. das Ändern von Größe, Klang und Farbe von Objekten. Dieses Modul führt grundlegende Konzepte zum Ändern von mrtk-Profilen ein, beginnend mit dem Ausschalten der Visualisierung für räumliche Netze. 

## <a name="objectives"></a>Ziele

* Anpassen und Konfigurieren von Mixed Reality-Toolkitprofilen
* Interagieren mit holograms mithilfe von Benutzeroberflächen Elementen und Schaltflächen
* Grundlegende Eingaben und Interaktionen zum Handtracking

## <a name="instructions"></a>Anweisungen

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Konfigurieren der Mixed Reality-Toolkitprofile (Option zum Ändern der räumlichen Wahrnehmung)
In diesem Abschnitt erfahren Sie, wie Sie die standardmäßigen mrtk-profile anpassen und konfigurieren, indem Sie die Anzeigeoption des Bereichs räumliches Bewusstsein anpassen. Sie können dieselben Prinzipien befolgen, um Einstellungen oder Werte in den MRTK-Profilen anzupassen.

1. Wählen Sie "Mixed-Reality Toolkit" (mrtk) aus der basescene-Hierarchie aus. Suchen Sie im Inspektor-Panel nach dem Mixed Reality Toolkit-Skript, und wählen Sie das aktive Profil aus, wie in der folgenden Abbildung dargestellt. Doppelklicken Sie darauf, um es zu öffnen.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>Hinweis: Standardmäßig können die MRTK-Profile nicht bearbeitet werden. Dabei handelt es sich um Standardprofil Vorlagen, die Sie kopieren und anpassen können. Es gibt mehrere Ebenen von Anpassung und Profilen. Daher ist es eine Standardübung, mehrere Profile zu kopieren und anzupassen, wenn Sie eine oder mehrere Einstellungen konfigurieren.
>
>Weitere Informationen zu mrtk-Profilen und deren Architektur finden Sie in der [mrtk-Dokumentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html>).

2. Erstellen Sie eine Kopie des Standardprofils, um es anzupassen. Klicken Sie zum Kopieren eines Standard Profils auf Kopieren & anpassen (siehe Abbildung). Dadurch wird eine Kopie des MRTK-Profils erstellt. Mit einer eigenen Kopie des MRTK-Profils verfügen Sie jetzt über die Möglichkeit, alle Einstellungen in diesem Profil anzupassen. Außerdem müssen Sie den Schritt zum Kopieren und anpassen für alle zusätzlichen Profile wiederholen, die unter diesem Profil geschildert werden, wie in den nachfolgenden Schritten beschrieben.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. Deaktivieren Sie die Sichtbarkeit des Gittermodells zur räumlichen Wahrnehmung. Zu diesem Zweck suchen Sie die System Einstellungen für räumliche Informationen, wie in der Abbildung dargestellt. Klicken Sie auf die Schaltfläche Klonen rechts neben dem System Profil räumliches Bewusstsein, um das Standardprofil durch eine anpassbare Kopie zu ersetzen. Wenn ein Popup Fenster angezeigt wird, klicken Sie auf die Schaltfläche Klonen, wie in der zweiten Abbildung unten gezeigt.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. Erstellen Sie eine benutzerdefinierte Kopie des standardmäßigen Mixed Reality-Betrachters für räumliche Gittermodelle. Klicken Sie auf den Pfeil nach unten neben Windows Mixed Reality Spatial Mesh Observer, um weitere Optionen anzuzeigen. In diesen Optionen wird der standardmäßige gemischte Reality-Mesh-Beobachter angezeigt, der abgeblendet (nicht bearbeitbar) ist. Sie müssen dieses Standardprofil durch eine anpassbare Kopie ersetzen, damit Sie es bearbeiten können. Klicken Sie auf die Schaltfläche nach rechts (mit einem grünen Pfeil gekennzeichnet), um eine Kopie zu klonen.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. Als Nächstes passen Sie die Einstellungen für die Anzeigeoption „Occlusion“ (Okklusion) an. Dadurch wird das räumliche Mesh unsichtbar, aber trotzdem werden die Spielobjekte hinter dem räumlichen Mesh ausgeblendet, auch bekannt als oksion.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>Hinweis: Obwohl das räumliche Zuordnungsgitter nicht angezeigt wird, ist es dennoch vorhanden und Sie können mit ihm interagieren. Alle holograms hinter dem räumlichen zuordnungsmesh, z. b. ein – Hologramm hinter der sichtbaren Wand, werden aufgrund der oksions Einstellung nicht angezeigt.

Herzlichen Glückwunsch! Sie haben soeben erfahren, wie Sie eine Einstellung im MRTK-Profil ändern können. Wie Sie sehen können, müssen Sie, um die MRTK-Einstellungen zu ändern, Kopien der Standardprofile erstellen, damit Sie diese bearbeiten können. Sie verfügen immer über die Standardprofile, die nicht bearbeitet werden können, wenn Sie ein Profil mit neuen Einstellungen erstellen möchten, oder Sie können auf die Standardprofile zurückgreifen. Es gibt zahlreiche Einstellungen, die Sie anpassen können. Die vollständige Referenz zu MRTK-Profileinstellungen finden Sie hier in der MRTK-Dokumentation: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>Gesten für Handtracking und interaktionsfähige Schaltflächen
In diesem Abschnitt erfahren Sie, wie Sie die Hand Überwachung verwenden, um eine Schaltfläche mit dem Druckvorgang zu drücken.

1. Wählen Sie Assets aus dem Ordner Projekte aus.

2. Geben Sie in die Suchleiste „pressablebutton“ (drückbare Schaltfläche) ein.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. Ziehen Sie das Prefab (dargestellt durch ein blaues Feld) namens „PressableButton“ in Ihre Hierarchie. 

   > Hinweis: Wenn Sie eine Meldung zu "Importieren von tmp Essentials" erhalten, importieren Sie Sie zu diesem Zeitpunkt. Wenn tmp Essentials noch nicht Bestandteil des Projekts ist, müssen Sie diesen Schritt nach dem Importieren von tmp Essentials möglicherweise wiederholen. andernfalls wird der Schaltflächen Text möglicherweise nicht angezeigt.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. Doppelklicken Sie auf das pressablebutton-Spielobjekt, das sich nun in der basescene-Hierarchie befinden sollte, um es in Ihrer Szene anzuzeigen, wie in der folgenden Abbildung dargestellt. Die Schaltflächen Grafiken können sich von der Abbildung unten unterscheiden. 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. Klicken Sie im Bereich Inspector auf Ereignis hinzufügen, um der Schaltfläche ein Ereignis zuzuweisen, auf das bei einem pushübertragung reagiert wird. Wählen Sie in der angezeigten Option das Dropdown Menü aus, und wählen Sie dann interactableonpressreciever aus. Dadurch kann die Schaltfläche auf ein gedrücktes Ereignis reagieren, wenn die Schaltfläche von einer nachverfolgten Hand gedrückt wird.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. Fügen Sie der Szene einen Würfel hinzu. Klicken Sie mit der rechten Maustaste auf den Hierarchie Bereich, wählen Sie ein 3D-Objekt aus, und klicken Sie auf Jetzt sollte sich ein Würfel in Ihrer Anzeige befinden. Es wird sehr groß angezeigt. Sie können die Koordinaten anpassen (während der Cube noch im Hierarchie Bereich ausgewählt ist), um die Größe zu verringern. Stellen Sie die Skalierungswerte auf „x = 0,1“, „y = 0,1“, „z = 0,1“ ein. Stellen Sie sicher, dass der Würfel in Ihrer Szene in der Nähe der drückbaren Schaltfläche, aber nicht mit der Schaltfläche überlappend positioniert wird. In der folgenden Abbildung ist die Position des Würfels „x = 0“, „y = 0,2“ und „z = 1“. 

   > Hinweis: Im Allgemeinen entspricht 1 Einheit in Unity ungefähr einem Meter in der physischen Umgebung. Es gibt Ausnahmen, z. B. wenn Objekte untergeordnete Objekte von skalierten Objekten sind.
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. In diesem Schritt richten Sie den Würfel so ein, dass er die Farbe ändert, wenn Ihre Schaltfläche gedrückt wird. Wählen Sie im basescene-Menü die Option pressablebutton aus. Klicken Sie im Bereich Inspector unter dem Feld Ereignistyp auswählen auf die Schaltfläche +. Ziehen Sie den Cube aus dem Menü basescene in das Feld nur zur Laufzeit, wie in der folgenden Abbildung dargestellt.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

Klicken Sie in der Dropdown Liste auf keine Funktion. Wählen Sie meshrenderer und dann Material Material aus. Auf diese Weise können Sie das Material ändern, wenn die Schaltfläche gedrückt wird. 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

Wechseln Sie zum Projekt Panel, und suchen Sie nach dem Material, in das Sie es ändern möchten. Sie verwenden das Material MRTK_Standard_Cyan für dieses Beispiel, indem Sie in der Suchleiste der Projekt Registerkarte "Cyan" eingeben. (Mrtk enthält viele Materialien und Farben, aus denen Sie auswählen können.) Ziehen Sie das Material in das Feld unterhalb von meshrenderer. Material. Die MRTK-Materialien finden Sie unter „Assets>MixedRealityToolkit.SDK>StandardAssets>Materials“ (Ressourcen>MixedRealityToolkit.SDK>Standardressourcen>Materialien).

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

Das Ereignis ist jetzt so eingestellt, dass beim Drücken der Schaltfläche der Würfel je nach dem von Ihnen angegebenen Material seine Farbe ändert. In diesem Beispiel wechselt der Würfel zur Farbe „Cyan“.

8. Als Nächstes werden Sie die Freigabeaktion so einrichten, dass die Schaltfläche nach der Freigabe wieder zu ihrer Standardfarbe zurückkehrt. Wiederholen Sie Schritt 7 oben. Aber dieses Mal mit dem onRelease-Ereignis anstelle des onPress-Ereignisses, wie in der folgenden Abbildung dargestellt.

9.  Suchen Sie im Projekt Panel nach einem Material, in dem der Cube bei der Schaltflächen Freigabe standardmäßig auf ein Material klickt. In diesem Fall haben wir MRTK_Standard_LightGray gewählt. Ziehen Sie das Material in das Feld unter das Feld meshrenderer. Material.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

Wenn nun die Schaltfläche gedrückt wird, wird Sie in eine neue Farbe, Cyan, geändert. Wenn die Schaltfläche freigegeben wird, wird Sie wieder in die von Ihnen angegebene Standardfarbe geändert (z. b. hellgrau). Klicken Sie oben auf dem Bildschirm auf die Schaltfläche "Wiedergabe", um Sie im Editor zu testen, oder stellen Sie Sie für die Tests auf den hololens 2 bereit. Weitere Informationen zur in-Editor-Simulation, einschließlich der Hand Simulation, finden Sie auf der [Dokumentationsseite zur Simulation von mrtk](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>). 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Erstellen eines Schaltflächenbereichs mit der MRTK-Rasterobjektsammlung

In diesem Abschnitt erfahren Sie, wie Sie mit dem gridobjectcollection-Tool von mrtk mehrere Schaltflächen automatisch an einer Benutzeroberfläche anpassen.

1. Duplizieren Sie die Schaltfläche aus dem vorherigen Abschnitt, bis Sie über fünf Schaltflächen verfügen. Dazu gibt es verschiedene Möglichkeiten:
- Klicken Sie mit der rechten Maustaste auf die Schaltfläche und dann auf kopieren. Klicken Sie dann auf die Schaltfläche, und klicken Sie mit der rechten Maustaste erneut auf einfügen. 
- Klicken Sie mit der rechten Maustaste auf die Schaltfläche, und klicken Sie 
- Klicken Sie mit dem Tastatur Befehl auf den Cube, und drücken Sie STRG D auf der Tastatur.

Wiederholen Sie diesen Vorgang, bis Sie fünf Schaltflächen haben sehen Sie sich die fünf roten Pfeile in der Abbildung unten an.

![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. Gruppieren Sie die Schaltflächen unter einem leeren übergeordneten Spielobjekt. Um die Schaltflächen in der Raster Auflistung zu haben, müssen Sie die Schaltflächen unter einem gemeinsamen übergeordneten Objekt gruppieren. Klicken Sie mit der rechten Maustaste auf den Eintrag, und klicken Sie auf leere erstellen. Dadurch wird ein neues leeres Spielobjekt erstellt, in das Sie alle Schaltflächen einfügen können. Es wird als gameobject angezeigt. Klicken Sie mit der rechten Maustaste, und benennen Sie Sie um.

![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. Verschieben Sie alle Schaltflächen in die neue Sammlung. Wählen Sie hierzu alle fünf der Schaltflächen Objekte in ihrer Heide Leiste aus, und ziehen Sie Sie alle unter buttoncollection Game Object, wie in der folgenden Abbildung dargestellt. Tipp: Wählen Sie mehrere Elemente aus, indem Sie die STRG-Taste gedrückt halten und Elemente auswählen.

![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. Fügen Sie die Komponente der Raster Objekt Auflistung von mrtk der Schaltflächen Auflistung hinzu. Wählen Sie hierzu das übergeordnete buttoncollection-Objekt aus. Klicken Sie im Inspektor-Panel auf die Schaltfläche Komponente hinzufügen. Suchen Sie in der Suchleiste nach der Raster Objekt Auflistung, und wählen Sie Sie aus, wenn Sie in der Liste angezeigt wird.

![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

Mit der Raster Objekt Auflistungs Komponente können Sie Schaltflächen oder eine beliebige Gruppe von Objekten in einer ordentlichen Zeile, Spalte oder einem anderen Raster anordnen. Dies ist einer der Bausteine, die von der mrtk bereitgestellt werden, die Ihnen eine schnelle und einfache Möglichkeit bietet, verlockende Benutzeroberflächen zu erstellen.

5. Konfigurieren Sie die Rasterobjektsammlung. Um sicherzustellen, dass alle Schaltflächen dem Benutzer angezeigt werden, wählen Sie die Option "Typ Wählen Sie dann übergeordnete Vorderseite aus, wie in der folgenden Abbildung dargestellt. Ändern Sie anschließend die Zellengröße, um den Abstand zwischen den Schaltflächen festzulegen. Beginnen Sie mit 0,12 Einheiten bis 0,12 Einheiten für die Zellen Breite und die Zellhöhe, wie in der folgenden Abbildung dargestellt. Abhängig von den ausgewählten Objekten und Schaltflächen Objekten müssen Sie diese Werte möglicherweise anpassen. Stellen Sie sicher, dass Zeilen auf 1 festgelegt sind. Klicken Sie auf Sammlung aktualisieren. Die Szene ähnelt der Abbildung unten. 


![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

>Hinweis: Abhängig von der Ausrichtung der untergeordneten Objekte oder des übergeordneten Objekts müssen Sie die Einstellung der Ausrichtung in zukünftigen Projekten wahrscheinlich anders anpassen. Die Felder für die Zellenbreite und Zellenhöhe müssen je nach Größe der Objekte in Ihrer Sammlung möglicherweise ebenfalls anders definiert werden.

### <a name="adding-text-into-your-scene"></a>Hinzufügen von Text zu Ihrer Szene

In diesem Abschnitt erfahren Sie, wie Sie Text zu Ihrer Mixed Reality-Umgebung hinzufügen und ihn bearbeiten können. Wenn dies noch nicht der Fall ist, stellen Sie sicher, dass Sie „TextMeshPro“ in Unity aktiviert haben, indem Sie die Anweisungen [hier](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation) befolgen.

1. Wählen Sie das übergeordnete buttoncollection-Objekt aus, und klicken Sie mit der rechten Maustaste auf Erweitern Sie im Dropdown Menü die Option 3D-Objekt. Wählen Sie dann textmeshpro-Text aus. Ein textmeschpro-Objekt sollte unter der Schaltflächen Auflistung angezeigt werden, wie in der folgenden Abbildung dargestellt.

![Lektion2 Kapitel4 Schritt1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lektion2 Kapitel4 Schritt1b](images/Lesson2_Chapter4_Step1b.JPG)

2. Um die Textgröße und die Platzierung für die Lesbarkeit zu verbessern, passen Sie das Feld Schriftart Größe in der textmeschpro-Komponente an, um die Größe der Schriftart zu ändern. Sie müssen auch die Position und Skalierung der Rect-Transformation anpassen, wie in der folgenden Abbildung dargestellt. In den folgenden Abbildungen finden Sie die Werte, die für die Text Konfiguration verwendet werden. Sie können diese Werte als Ausgangspunkt verwenden, um die Größe und Platzierung des Textfelds weiter zu verbessern.

![Lesson2 Chapter4 Schritt 3](images/Lesson2_Chapter4_Step3.JPG)

3. Im Textfeld der textmeschpro-Komponente im Inspektor-Panel (siehe unten). Geben Sie den Text der Schaltflächen Auflistung ein. Der Text wird in der Szene angezeigt, wird jedoch hinter den Schaltflächen und/oder der falschen Größe ausgeblendet.

![Lesson2 Chapter4 Schritt 2](images/Lesson2_Chapter4_Step2.JPG)
![Lesson2 Chapter4 Schritt 4](images/Lesson2_Chapter4_Step4.JPG)

4. Klicken Sie zum Ändern der Textwerte auf den Schaltflächen Objekten auf den Pfeil neben einer beliebigen Schaltfläche, um ihn zu erweitern, und navigieren Sie zum seeitsayitlabel-Objekt. Navigieren Sie zu textmeshpro, wo Sie den Text wie in den obigen Schritten beschrieben auf Ihre Schaltflächen bearbeiten können.

![Lektion2 Kapitel4 Schritt5](images/Lesson2_Chapter4_Step5.JPG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!
In dieser Lektion haben Sie erfahren, wie Sie eine MRTK-Profileinstellung (d. h. Sichtbarkeit des Gittermodells der räumlichen Wahrnehmung) kopieren, anpassen und konfigurieren. Sie haben auch erfahren, wie Sie mit einer Schaltfläche interagieren können, um Ereignisse mit nachverfolgten Händen für die HoloLens 2 auszulösen. Abschließend haben Sie erfahren, wie Sie mit „TextMeshPro“ von Unity und der MRTK-Komponente „Grid Object Collection“ (Rasterobjektsammlung) eine einfache Benutzeroberfläche erstellen.

[Nächste Lektion: 4. Platzieren dynamischer Inhalte und Verwenden von Solvern](mrlearning-base-ch3.md)

