---
title: MR-Basislernmodul – Benutzeroberfläche, Handverfolgung und Konfiguration des Mixed Reality-Toolkits
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 1800d36b7292b9cb53b09fdd4b9c4fb763d49e79
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730949"
---
# <a name="mr-learning-base-module---user-interface-hand-tracking-and-mixed-reality-toolkit-configuration"></a>MR-Basislernmodul – Benutzeroberfläche, Handverfolgung und Konfiguration des Mixed Reality-Toolkits

In der vorherigen Lektion haben Sie einige der Funktionen kennengelernt, die das MRTK bietet, indem Sie Ihre erste Anwendung für die HoloLens 2 gestartet haben. In dieser nächsten Lektion erfahren Sie, wie Sie Schaltflächen zusammen mit den Textbereichen der Benutzeroberfläche erstellen und organisieren und mithilfe der Standardinteraktion (berühren) mit den einzelnen Schaltflächen interagieren. Sie werden auch das Hinzufügen einfacher Aktionen und Effekte untersuchen, z. B. das Ändern von Größe, Klang und Farbe von Objekten. In diesem Modul werden grundlegende Konzepte zur Änderung von MRTK-Profilen vorgestellt, beginnend mit dem Deaktivieren der Darstellung des räumlichen Gittermodells. 

## <a name="objectives"></a>Ziele

* Anpassen und Konfigurieren von Mixed Reality-Toolkitprofilen
* Interagieren mit Hologrammen über Elemente und Schaltflächen der Benutzeroberfläche
* Grundlegende Eingaben und Interaktionen zum Handtracking

## <a name="instructions"></a>Anweisungen

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Konfigurieren der Mixed Reality-Toolkitprofile (Option zum Ändern der räumlichen Wahrnehmung)
In diesem Abschnitt erfahren Sie, wie Sie die standardmäßigen Mixed Reality-Toolkitprofile anpassen und konfigurieren können, indem Sie die Anzeigeoption für das Gittermodell der räumlichen Wahrnehmung anpassen. Sie können dieselben Prinzipien befolgen, um Einstellungen oder Werte in den MRTK-Profilen anzupassen.

1. Wählen Sie „Mixed Reality-Toolkit“ (MRTK) aus der Hierarchie „BaseScene“ (Basisszene) aus. Suchen Sie im Inspektorbereich nach dem „Mixed Reality-Toolkitskript“, und wählen Sie das „aktive Profil“ aus, wie in der folgenden Abbildung gezeigt. Doppelklicken Sie darauf, um es zu öffnen.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>Hinweis: Standardmäßig können die MRTK-Profile nicht bearbeitet werden. Dies sind Standardprofilvorlagen, die Sie zum Kopieren und Anpassen verwenden können. Es gibt mehrere Ebenen von Anpassungen und Profilen, sodass es üblich ist, mehrere Profile zu kopieren und anzupassen, wenn Sie eine oder mehrere Einstellungen konfigurieren.
>
>Weitere Informationen zu MRTK-Profilen und deren Architektur finden Sie in der [MRTK-Dokumentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>).

2. Erstellen Sie eine Kopie des Standardprofils, um es anzupassen. Klicken Sie zum Kopieren eines Standardprofils auf die Schaltfläche „Copy & Customize“ (Kopieren und Anpassen), wie in der nachfolgenden Abbildung gezeigt. Dadurch wird eine Kopie des MRTK-Profils erstellt. Mit einer eigenen Kopie des MRTK-Profils verfügen Sie jetzt über die Möglichkeit, alle Einstellungen in diesem Profil anzupassen. Sie müssen auch den Schritt „Kopieren/Anpassen“ für alle weiteren Profile wiederholen, die unter diesem Profil geschachtelt sind, wie in den folgenden Schritten beschrieben.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. Deaktivieren Sie die Sichtbarkeit des Gittermodells zur räumlichen Wahrnehmung. Suchen Sie dazu nach „Spatial Awareness System Settings“ (Systemeinstellungen zur räumlichen Wahrnehmung), wie in der Abbildung gezeigt. Klicken Sie auf die Schaltfläche „Clone“ (Klonen) rechts neben „Spatial Awareness System Profile“ (Systemprofil für räumliche Wahrnehmung), um das Standardprofil durch eine anpassbare Kopie zu ersetzen. Wenn ein Popupfenster angezeigt wird, drücken Sie die Schaltfläche „Clone“ (Klonen), wie in der zweiten Abbildung unten gezeigt.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. Erstellen Sie eine benutzerdefinierte Kopie des standardmäßigen Mixed Reality-Betrachters für räumliche Gittermodelle. Klicken Sie neben „Windows Mixed Reality Spatial Mesh Observer“ (Windows Mixed Reality-Betrachter für räumliche Gittermodelle) auf den Pfeil nach unten, um weitere Optionen anzuzeigen. In diesen Optionen wird der „Default Mixed Reality Spatial Mesh Observer“ (standardmäßiger Mixed Reality-Betrachter für räumliche Gittermodelle) angezeigt, der grau (nicht bearbeitbar) angezeigt wird. Sie müssen dieses Standardprofil durch eine anpassbare Kopie ersetzen, damit Sie es bearbeiten können. Klicken Sie auf die rechte Schaltfläche (durch einen grünen Pfeil gekennzeichnet), um eine Kopie zu klonen.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. Als Nächstes passen Sie die Einstellungen für die Anzeigeoption „Occlusion“ (Okklusion) an. Dadurch wird das räumliche Gittermodell unsichtbar, aber es werden dennoch Spielobjekte hinter dem räumlichen Gittermodell ausgeblendet (dies wird als „Okklusion“ bezeichnet).

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>Hinweis: Obwohl das räumliche Zuordnungsgitter nicht angezeigt wird, ist es dennoch vorhanden und Sie können mit ihm interagieren. Alle Hologramme hinter dem räumlichen Zuordnungsgitter (z. B. ein Hologramm hinter der sichtbaren Wand) sind aufgrund der Okklusionseinstellung nicht sichtbar.

Gratulation! Sie haben soeben erfahren, wie Sie eine Einstellung im MRTK-Profil ändern können. Wie Sie sehen können, müssen Sie, um die MRTK-Einstellungen zu ändern, Kopien der Standardprofile erstellen, damit Sie diese bearbeiten können. Sie werden immer über die Standardprofile (die nicht bearbeitbar sind) verfügen, zu denen Sie zurückkehren können, wenn Sie ein Profil mit neuen Einstellungen erstellen oder auf die Standardprofile zurückgreifen möchten. Es gibt zahlreiche Einstellungen, die Sie anpassen können. Die vollständige Referenz zu MRTK-Profileinstellungen finden Sie hier in der MRTK-Dokumentation: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>Gesten für Handtracking und interaktionsfähige Schaltflächen
In diesem Abschnitt erfahren Sie, wie Sie mit dem Handtracking eine interaktionsfähige Schaltfläche drücken können.

1. Wählen Sie im Projektordner „Assets“ (Ressourcen) aus.

2. Geben Sie in die Suchleiste „pressablebutton“ (drückbare Schaltfläche) ein.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. Ziehen Sie das Prefab (dargestellt durch ein blaues Feld) namens „PressableButton“ in Ihre Hierarchie. 

   > Hinweis: Wenn Sie eine Nachricht zum „Importieren von TMP Essentials“ erhalten, führen Sie den Importvorgang zu diesem Zeitpunkt aus. Wenn TMP Essentials nicht bereits Teil Ihres Projekts war, müssen Sie diesen Schritt möglicherweise nach dem Import von TMP Essentials wiederholen, da sonst möglicherweise kein Schaltflächentext angezeigt wird.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. Doppelklicken Sie auf das Spielobjekt „PressableButton“ (das sich jetzt in Ihrer BaseScene-Hierarchie befinden sollte), um es in Ihrer Szene anzuzeigen, wie in nachfolgender Abbildung gezeigt (Ihre Schaltflächengrafiken können von der nachfolgenden Abbildung abweichen). 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. Klicken Sie im Inspektorbereich auf „Add Event“ (Ereignis hinzufügen), um der Schaltfläche ein Ereignis zuzuweisen, auf das sie reagieren soll, wenn sie gedrückt wird. Wählen Sie in der angezeigten Option das Dropdownmenü aus. Wählen Sie „InteractableOnPressReciever“ aus. Dadurch kann die Schaltfläche auf ein gedrücktes Ereignis reagieren, wenn die Schaltfläche von einer nachverfolgten Hand gedrückt wird.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. Fügen Sie der Szene einen Würfel hinzu. Klicken Sie mit der rechten Maustaste auf den Hierarchiebereich, wählen Sie „3D Object (3D-Objekt) aus, und klicken Sie dann auf „Cube“ (Würfel). Jetzt sollte sich ein Würfel in Ihrer Anzeige befinden. Er wird sehr groß dargestellt, also passen Sie die Koordinaten an (während im Hierarchiebereich weiterhin „Cube" (Würfel) ausgewählt ist), um die Größe zu verringern. Stellen Sie die Skalierungswerte auf „x = 0,1“, „y = 0,1“, „z = 0,1“ ein. Stellen Sie sicher, dass der Würfel in Ihrer Szene in der Nähe der drückbaren Schaltfläche, aber nicht mit der Schaltfläche überlappend positioniert wird. In der folgenden Abbildung ist die Position des Würfels „x = 0“, „y = 0,2“ und „z = 1“. 

   > Hinweis: Im Allgemeinen entspricht 1 Einheit in Unity ungefähr einem Meter in der physischen Umgebung. Es gibt Ausnahmen, z. B. wenn Objekte untergeordnete Objekte von skalierten Objekten sind.
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. In diesem Schritt richten Sie den Würfel so ein, dass er die Farbe ändert, wenn Ihre Schaltfläche gedrückt wird. Wählen Sie die „PressableButton“ im Menü „BaseScene“ aus. Klicken Sie im Inspektorbereich unter dem Feld „Select Event Type“ (Ereignistyp auswählen“ auf die Schaltfläche „+“. Ziehen Sie den „Würfel“ aus dem Menü „BaseScene“ in das Feld „Runtime Only“ (Nur Runtime), wie in der folgenden Abbildung gezeigt.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

Klicken Sie auf die Dropdownliste mit der Aufschrift „No Function“ (Keine Funktion). Wählen Sie „MeshRenderer“ und dann „Material material“ aus. Dadurch können Sie das Material wechseln, wenn die Schaltfläche gedrückt wird. 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

Wechseln Sie in den Projektbereich, und suchen Sie nach dem Material, in das Sie es ändern möchten. Sie werden das Material „MRTK_Standard_Cyan“ für dieses Beispiel verwenden, das Sie durch Eingabe von „Cyan“ in der Suchleiste der Projektregisterkarte finden. (Das MRTK enthält viele Materialien und Farben zur Auswahl.) Ziehen Sie das Material auf das Feld unter „MeshRenderer.material“. Die MRTK-Materialien finden Sie unter „Assets>MixedRealityToolkit.SDK>StandardAssets>Materials“ (Ressourcen>MixedRealityToolkit.SDK>Standardressourcen>Materialien).

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imbb.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

Das Ereignis ist jetzt so eingestellt, dass beim Drücken der Schaltfläche der Würfel je nach dem von Ihnen angegebenen Material seine Farbe ändert. In diesem Beispiel wechselt der Würfel zur Farbe „Cyan“.

8. Als Nächstes werden Sie die Freigabeaktion so einrichten, dass die Schaltfläche nach der Freigabe wieder zu ihrer Standardfarbe zurückkehrt. Wiederholen Sie Schritt 7 (den vorherigen Schritt), diesmal jedoch mit dem Ereignis „OnRelease“ anstelle des Ereignisses „OnPress“, wie in der Abbildung unten gezeigt.

9.  Suchen Sie im Projektbereich nach einem Material, auf das der Würfel beim Loslassen der Schaltfläche standardmäßig eingestellt ist (in unserem Fall haben wir „MRTK_Standard_LightGray“ ausgewählt). Ziehen Sie das Material in das Feld unter dem Feld „MeshRenderer.material“.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

Wenn Sie jetzt die Schaltfläche drücken, sollte sie zu einer neuen Farbe wechseln (z. B. Cyan), und wenn Sie die Schaltfläche loslassen, sollte sie wieder zu der von Ihnen festgelegten Standardfarbe zurückkehren (z. B. Hellgrau). Drücken Sie oben auf dem Bildschirm auf die Schaltfläche „Play“ (Wiedergabe), um sie im Editor auszuprobieren oder auf Ihrer HoloLens 2 zum Testen bereitzustellen. Weitere Informationen zur Simulation im Editor, einschließlich der Handsimulation, finden Sie auf der Seite zur [Simulation in der MRTK-Dokumentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>). 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Erstellen eines Schaltflächenbereichs mit der MRTK-Rasterobjektsammlung

In diesem Abschnitt erfahren Sie, wie Sie mit dem MRTK-Tool „GridObjectCollection“ automatisch mehrere Schaltflächen auf einer ordentlichen Benutzeroberfläche ausrichten.

1. Duplizieren Sie die Schaltfläche aus dem vorherigen Abschnitt, bis Sie über fünf Tasten verfügen. Dazu gibt es verschiedene Möglichkeiten:
- Klicken Sie mit der rechten Maustaste auf die Schaltfläche, und klicken Sie auf „Copy“ (Kopieren). Dann wechseln Sie nach unten unter die Schaltfläche, klicken Sie erneut mit der rechten Maustaste und klicken Sie auf „Paste“ (Einfügen). 
- Klicken Sie mit der rechten Maustaste auf die Schaltfläche, und klicken Sie auf „Duplicate“ (Duplizieren). 
- Verwenden Sie den Tastaturbefehl, indem Sie auf den Würfel klicken und „STRG+D“ auf Ihrer Tastatur drücken.

Wiederholen Sie diesen Vorgang, bis Sie insgesamt über fünf Schaltflächen verfügen (siehe die fünf roten Pfeile in der unteren Abbildung).

![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. Gruppieren Sie die Schaltflächen unter einem leeren übergeordneten Spielobjekt. Um die Schaltflächen in die Rastersammlung aufzunehmen, müssen Sie Ihre Schaltflächen unter einem gemeinsamen übergeordneten Objekt gruppieren. Klicken Sie mit der rechten Maustaste in die Hierarchie, und klicken Sie auf „Create empty“ (Leer erstellen). Dadurch wird ein neues leeres Spielobjekt erstellt, in das Sie alle Schaltflächen einfügen können. Es wird als „gameObject“ angezeigt. Klicken Sie mit der rechten Maustaste, und benennen Sie es in „ButtonCollection“ um.

![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. Verschieben Sie alle Schaltflächen in die neue Sammlung. Wählen Sie dazu alle fünf Schaltflächenobjekte in Ihrer Hierarchie aus, und ziehen Sie sie alle unter das Spielobjekt „ButtonCollection“, wie in der Abbildung unten gezeigt. Tipp: Wählen Sie mehrere Elemente aus, indem Sie beim Auswählen der Elemente die STRG-Taste gedrückt halten.

![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. Fügen Sie die MRTK-Komponente „Grid Object Collection“ (Rasterobjektsammlung) zur Schaltflächensammlung hinzu.  Wählen Sie dazu das übergeordnete Objekt „ButtonCollection“ aus, und klicken Sie im Inspektorbereich auf die Schaltfläche „Add Component“ (Komponente hinzufügen). Suchen Sie dann in der Suchleiste nach „Grid Object Collection“ (Rasterobjektsammlung), und wählen Sie diese aus, wenn sie in der Liste angezeigt wird.

![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

Die Komponente „Grid Object Collection“ ermöglicht es Ihnen, Schaltflächen oder eine beliebige Objektgruppe in einer ordentlichen Zeile, Spalte oder einem Gitter zu organisieren. Dies ist einer der Bausteine des MRTK, der Ihnen eine schnelle und einfache Möglichkeit bietet, ansprechende Benutzeroberflächen zu erstellen.

5. Konfigurieren Sie die Rasterobjektsammlung. Um sicherzustellen, dass alle Schaltflächen dem Benutzer zugewandt sind, wählen Sie „Orient Type“ (Ausrichtungstyp) und dann „Face Parent Forward“ (Übergeordnetes Objekt nach vorne gerichtet) aus (wie in der Abbildung gezeigt). Ändern Sie anschließend die Zellengröße, um den Abstand zwischen den Schaltflächen festzulegen. Beginnen Sie mit 0,12 Einheiten x 0,12 Einheiten für die Zellenbreite und Zellenhöhe, wie in der Abbildung unten gezeigt. Möglicherweise müssen Sie diese Werte je nach gewählten Objekt-/Schaltflächenressourcen anpassen. Stellen Sie sicher, dass „Rows“ (Zeilen) auf 1 festgelegt ist. Klicken Sie dann auf „Update Collection“ (Sammlung aktualisieren) und die Szene sollte wie in der folgenden Abbildung aussehen. 


![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

>Hinweis: Abhängig von der Ausrichtung der untergeordneten Objekte oder des übergeordneten Objekts müssen Sie die Einstellung der Ausrichtung in zukünftigen Projekten wahrscheinlich anders anpassen. Die Felder für die Zellenbreite und Zellenhöhe müssen je nach Größe der Objekte in Ihrer Sammlung möglicherweise ebenfalls anders definiert werden.

### <a name="adding-text-into-your-scene"></a>Hinzufügen von Text zu Ihrer Szene

In diesem Abschnitt erfahren Sie, wie Sie Text zu Ihrer Mixed Reality-Umgebung hinzufügen und ihn bearbeiten können. Wenn dies noch nicht der Fall ist, stellen Sie sicher, dass Sie „TextMeshPro“ in Unity aktiviert haben, indem Sie die Anweisungen [hier](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation) befolgen.

1. Wählen Sie das übergeordnete Objekt „ButtonCollection“ aus, und klicken Sie mit der rechten Maustaste auf die Sammlung. Erweitern Sie „3D Object“ (3D-Objekt) im Dropdownmenü, und wählen Sie dann „TextMeshPro – Text“ aus. Es sollte ein TextMeshPro-Objekt unter der Schaltflächensammlung angezeigt werden, wie in der Abbildung unten gezeigt.

![Lektion2 Kapitel4 Schritt1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lektion2 Kapitel4 Schritt1b](images/Lesson2_Chapter4_Step1b.JPG)

2. Geben Sie im Textfeld der TextMeshPro-Komponente (im Inspektorbereich, wie unten gezeigt) „Button Collection Text“ (Text der Schaltflächensammlung) ein. Der Text wird in der Szene angezeigt, aber hinter den Schaltflächen ausgeblendet und/oder in der falschen Größe angezeigt.

![Lektion2 Kapitel4 Schritt2](images/Lesson2_Chapter4_Step2.JPG)

3. Passen Sie das Feld „Font Size“ (Schriftgröße) in der TextMeshPro-Komponente an, um die Größe der Schrift zu ändern und somit Textgröße und Platzierung zwecks Lesbarkeit zu verbessern. Sie müssen auch die Position und Skalierung für „Rect Transform“ (Rechtecktransformation) anpassen, wie in der Abbildung unten gezeigt. Die folgenden Abbildungen zeigen Werte, die für unsere Textkonfiguration verwendet werden, und Sie können diese Werte als Ausgangspunkt nehmen, um Größe und Platzierung Ihres Textfelds weiter zu verbessern.

![Lektion2 Kapitel4 Schritt3](images/Lesson2_Chapter4_Step3.JPG)
![Lektion2 Kapitel4 Schritt4](images/Lesson2_Chapter4_Step4.JPG)

5. Klicken Sie zum Ändern der Textwerte auf den Schaltflächenobjekten auf den Pfeil neben einer beliebigen Schaltfläche, um sie zu erweitern. Navigieren Sie dann zum Objekt „SeeItSayItLabel“ und anschließend zu „TextMeshPro“, wo Sie den Text für Ihre Schaltflächen bearbeiten können, wie in den obigen Schritten beschrieben.

![Lektion2 Kapitel4 Schritt5](images/Lesson2_Chapter4_Step5.JPG)

### <a name="congratulations"></a>Herzlichen Glückwunsch!
In dieser Lektion haben Sie erfahren, wie Sie eine MRTK-Profileinstellung (d. h. Sichtbarkeit des Gittermodells der räumlichen Wahrnehmung) kopieren, anpassen und konfigurieren. Sie haben auch erfahren, wie Sie mit einer Schaltfläche interagieren können, um Ereignisse mit nachverfolgten Händen für die HoloLens 2 auszulösen. Abschließend haben Sie erfahren, wie Sie mit „TextMeshPro“ von Unity und der MRTK-Komponente „Grid Object Collection“ (Rasterobjektsammlung) eine einfache Benutzeroberfläche erstellen.

[Nächste Lektion: Dynamische Inhaltsplatzierung und Solver](mrlearning-base-ch3.md)

