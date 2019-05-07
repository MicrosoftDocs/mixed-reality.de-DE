---
title: Basis-Lernmodul - Benutzeroberfläche, MR übergeben, nachverfolgung und Mixed Reality-Toolkit-Konfiguration
description: Führen Sie diesen Kurs erfahren, wie Sie Azure-Gesichtserkennung innerhalb einer mixed Reality-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Gemischte Realität, Unity, Tutorial, hololens
ms.openlocfilehash: 1530fd1a1ee06d01e8ab0cc009dfba03873c3427
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993644"
---
# <a name="mr-learning-base-module---user-interface-hand-tracking-and-mixed-reality-toolkit-configuration"></a>Basis-Lernmodul - Benutzeroberfläche, MR übergeben, nachverfolgung und Mixed Reality-Toolkit-Konfiguration

In der vorherigen Lektion haben Sie einige der Funktionen, die die MRTK bieten, indem Sie Ihre erste Anwendung für die HoloLens 2 ab, aus. In der nächsten Lektion erfahren Sie, wie zum Erstellen und Organisieren von Schaltflächen, die zusammen mit UI-Text-Bereiche und Standardinteraktion (Touch) für die Interaktion mit jeder Schaltfläche verwenden. Sie werden auch das Hinzufügen von einfachen Aktionen und Effekte, z. B. das Ändern der Größe, sound und die Farbe der Objekte untersuchen. Dieses Modul bietet eine Einführung grundlegende Konzepten zum Ändern der MRTK Profilen, deaktivieren die Visualisierung des räumlichen Mesh ab. 

## <a name="objectives"></a>Ziele

* Anpassen und Konfigurieren von Mixed Reality-Toolkit-Profilen
* Interaktion mit Hologramme mithilfe von UI-Elemente und Schaltflächen
* Grundlegende manuell Nachverfolgen von Eingabeereignissen und Interaktionen

## <a name="instructions"></a>Anweisungen

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Vorgehensweise: Konfigurieren Sie die Mixed Reality-Toolkit-Profile (Änderung räumliche Awareness Display-Option)
In diesem Abschnitt Sie erfahren, wie anpassen und konfigurieren die Standardwert Mixed Reality-Toolkit-Profilen durch Anpassen von die Option zum Anzeigen der räumlichen Bewusstsein vernetzt werden. Sie können dieselben Prinzipien für die Anpassung von Einstellungen oder Werten in den Profilen MRTK folgen.

1. Wählen Sie aus der Hierarchie "BaseScene" Mixed Reality-Toolkit (MRTK). Klicken Sie im Bereich mit den Inspektor für das "Mixed Reality-Toolkit-Skript" Suchen Sie, und wählen Sie das "aktive Profil" aus, wie in der folgenden Abbildung dargestellt. Zum Öffnen doppelklicken.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>Hinweis: Standardmäßig können die Profile MRTK nicht bearbeitet werden. Hierbei handelt es sich um Standard-Profilvorlagen aus denen Sie kopieren und anpassen können. Befinden sich mehrere Ebenen der Anpassung und -Profilen, daher ist es üblich, kopieren und passen mehrere Profile aus, wenn Sie eine oder mehrere Einstellungen zu konfigurieren.
>
>Um weitere Informationen zu MRTK Profile und deren Architektur zu ermitteln, finden Sie auf die [MRTK Dokumentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>).

2. Erstellen Sie eine Kopie des Standardprofils anpassen. Um ein Standardprofil zu kopieren, klicken Sie auf der "kopieren und Anpassen von" Schaltfläche (siehe Abbildung). Dadurch wird eine Kopie des Profils MRTK erstellt. Mit Ihr eigenes Exemplar des Profils MRTK können Sie nun alle Einstellungen in diesem Profil anzupassen. Sie müssen auch den Copy/anpassen Schritt für jede zusätzliche Profile geschachtelt unter dieses Profil ist, zu wiederholen, wie in den folgenden Schritten beschrieben.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. Deaktivieren Sie die Sichtbarkeit des räumlichen Awareness Mesh. Zu diesem Zweck find "Räumlichen Awareness System Settings" in der Abbildung dargestellt. Klicken Sie auf die klonenschaltfläche "" rechts von der das "räumlichen Awareness-Profil" als Standardprofil für die eine anpassbare Kopie ersetzt. Wenn ein Popupfenster angezeigt wird, drücken Sie die Schaltfläche "Klonen", wie in der zweiten Abbildung unten gezeigt.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. Erstellen Sie eine benutzerdefinierte Kopie der Standard Mixed Reality räumliche Mesh Beobachter. Klicken Sie auf den Pfeil nach unten neben "Windows Mixed Reality räumliche Mesh Beobachter" finden weitere Möglichkeiten, ein. In den folgenden Optionen sehen Sie sich, dass der "Default gemischte Realität räumliche Mesh Beobachter" angezeigt wird (nicht bearbeitet) abgeblendet dargestellt. Sie müssen dieses Profil mit einer anpassbaren Kopie ersetzen, damit Sie sie bearbeiten können. Klicken Sie auf der rechten Seite (gekennzeichnet durch den grünen Pfeil) um eine Kopie zu klonen.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. Als Nächstes werden Sie die Einstellungen für die Anzeigeoption, sagen Sie "verdecken." anpassen. Dadurch wird das räumliche Netz unsichtbar, aber auch weiterhin ausgeblendet Spielobjekte hinter räumliche Mesh (Dies wird als verdecken bezeichnet.)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>Hinweis: Während des Netzes räumliche Zuordnung nicht sichtbar ist, sie immer noch vorhanden ist, und Sie können mit ihm interagieren. Alle Hologramme hinter das Netz räumliche Zuordnung (z. B. ggf. ein Hologramm hinter Ihrer sichtbaren Wand landet) ist aufgrund der verdecken-Einstellung werden nicht angezeigt.

Herzlichen Glückwunsch! Sie haben soeben gelernt, wie Sie eine Einstellung im Profil MRTK ändern. Wie Sie sehen können, müssen MRTK-Einstellungen ändern Sie Kopien der Standardprofile erstellen, damit Sie sie bearbeiten können. Sie haben immer die Standardprofile (die nicht bearbeitbar sind) zu zurückkehren, wenn Sie ein Profil erstellen, mit neuen Einstellungen oder Standardprofile zurückgreifen möchten. Es gibt zahlreiche Einstellungen, die Sie anpassen können. Vollständige Referenz zu MRTK profileinstellungen finden Sie in der Dokumentation des MRTK hier: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>Nachverfolgen von Gestensteuerung und es Schaltflächen
In diesem Abschnitt lernen Sie, wie Sie mit der Hand, die zu eine Schaltfläche "es" klicken.

1. Wählen Sie "Ressourcen" im Ordner Projekte an.

2. Geben Sie in der Suchleiste "Pressablebutton."

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. Ziehen Sie das Prefab (dargestellt durch ein hellblaues Kästchen), die mit dem Namen "PressableButton" in der Hierarchie ein. 

   > Hinweis: Wenn Sie eine Meldung erhalten, Informationen zu "TMP Essentials importieren" Importieren Sie sie zu diesem Zeitpunkt. Wenn TMP Essentials nicht bereits Teil des Projekts war, müssen Sie möglicherweise wiederholen diesen Schritt nach dem Import TMP Essentials, die andernfalls möglicherweise Text der Schaltfläche nicht angezeigt.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. Doppelklicken klicken Sie auf das spielobjekt "PressableButton" (die jetzt in Ihrer Hierarchie BaseScene sein sollte) zum Anzeigen in der Szene, wie in der folgenden Abbildung dargestellt (Schaltflächengrafiken können sich von der folgenden Abbildung angezeigt werden). 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. Klicken Sie im Bereich mit den Inspektor auf "Ereignis hinzufügen", um der Schaltfläche "Geben Sie ein Ereignis zu reagieren, wenn mithilfe von Push übertragen. Wählen Sie in der Option, die angezeigt wird, klicken Sie im Dropdown-Menü aus. Wählen Sie "InteractableOnPressReciever." Dadurch wird die Schaltfläche, um Antworten auf ein gedrückten-Ereignis, wenn eine nachverfolgte Hand auf die Schaltfläche klickt.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. Fügen Sie einen Cube, in die Szene. Klicken Sie mit der rechten Maustaste auf den Bereich für die Hierarchie, wählen Sie des 3D-Objekts aus, und klicken Sie dann auf "Cube". Ein Cube sollte jetzt in Ihrer Anzeige sein. Es sind sehr groß, also werden an den Koordinaten (während "Cube" noch im Bereich "Hierarchie" ausgewählt ist) um die Größe zu verringern. Legen Sie die Skalierungswerte auf X = 0,1, y = 0,1 und Z = 0,1. Werden Sie sicher, dass den Cube in der Szene, platzieren Sie es in der Nähe der Schaltfläche pressable positionieren, jedoch nicht überlappenden, mit der Schaltfläche. In der folgenden Abbildung ist des Cubes Position X = 0, y = 0,2 und Z = 1. 

   > Hinweis: Im Allgemeinen entspricht 1 Einheit in Unity ungefähr 1 Meter Umkreis um in der realen Welt. Es gibt Ausnahmen, z. B. wenn untergeordnete Elemente, von skalierten Objekten stehen.
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. In diesem Schritt richten Sie den Cube ein Farbe zu ändern, wenn die Schaltfläche gedrückt wird. Wählen Sie die PressableButton im Menü "BaseScene". Klicken Sie im Bereich mit den Inspector unter dem Feld "Wählen Sie Event-Type" auf die Schaltfläche "+". Ziehen Sie die "Cube" im Menü "BaseScene" in das Feld "Common Language Runtime nur", wie in der folgenden Abbildung dargestellt.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

Klicken Sie auf der Dropdownliste die Fehlermeldung "Keine Funktion." Wählen Sie "MeshRenderer" dann "Material Material". Dadurch können Sie das Material zu ändern, wenn Sie die Schaltfläche gedrückt wird. 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

Wechseln Sie zu den Projektbereich, und suchen Sie für das Material, die, dem Sie ändern möchten. Sie sind dabei, das Material "MRTK_Standard_Cyan" in diesem Beispiel verwenden, die Sie durch Eingabe in "Cyan" in der Registerkarte Project-Suchleiste (die MRTK enthält viele Materialien und Farben.) Ziehen Sie das Material, in das Feld unter "MeshRenderer.material." Die Materialien MRTK finden Sie im Ressourcen > MixedRealityToolkit.SDK > StandardAssets > Materialien.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imbb.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

Das Ereignis ist jetzt festgelegt werden, so ändert, wenn die Schaltfläche gedrückt wird, der Cube Farbe basierend auf den Materialien, den Sie angegeben haben. In diesem Beispiel wird der Cube auf die Farbe Zyan ändern.

8. Als Nächstes möchten Sie die releaseaktion so einrichten, dass bei der Freigabe, die Schaltfläche auf ihre Standardfarbe zurückgesetzt. Wiederholen Sie Schritt 7 (im vorigen Schritt) aber dieses Mal mit der "" OnRelease verwenden anstelle des Ereignisses "OnPress" aus, wie in der folgenden Abbildung dargestellt.

9.  Suchen Sie im Projektpanel nach Material für den Cube standardmäßig auf die Schaltfläche freigeben (in unserem Fall wir haben MRTK_Standard_LightGray.) Ziehen Sie das Material, in das Feld unterhalb des Felds "MeshRenderer.material".

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

Nun, wenn die Schaltfläche gedrückt wird, um eine neue Farbe ändern muss (z. B. Cyan) Wenn die Maustaste losgelassen wird sollte es ändern, um die Standardfarbe, die Sie angegeben haben (z. B. Hellgrau.) Drücken Sie die Schaltfläche "Wiedergabe" am oberen Bildschirmrand, probieren Sie es im Editor bereitstellen oder in Ihrem HoloLens 2 Testen! Weitere Informationen zum im Editor-Simulation, einschließlich Lesen von Hand Simulation der [MRTKs Simulation-Dokumentationsseite](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>). 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Erstellen einen Bereich von Schaltflächen, die mithilfe MRTKs Raster Objektauflistung

In diesem Abschnitt lernen Sie, wie Sie mehrere Schaltflächen automatisch in einer ordentlichen Benutzeroberfläche, die mit der MRTKs GridObjectCollection Tool ausrichten.

1. Duplizieren Sie die Schaltfläche aus dem vorherigen Abschnitt, bis Sie 5 Schaltflächen verfügen. Es gibt mehrere Möglichkeiten zur Verfügung:
- Klicken Sie mit der rechten Maustaste auf die Schaltfläche und klicken Sie auf "Kopieren", und klicken Sie dann die Schaltfläche mit den nach unten zu unterschreiten und mit der rechten Maustaste erneut und klicken Sie auf "Einfügen". 
- Klicken Sie mit der rechten Maustaste auf die Schaltfläche, und klicken Sie auf "doppelter". 
- Verwenden Sie den Tastaturbefehl, durch Klicken auf den Cube und die drücken "von STRG D" auf der Tastatur.

Wiederholen Sie diesen Schritt, bis Sie 5 insgesamt Schaltflächen verfügen (siehe 5 rote Pfeile in der Abbildung unten).

![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. Gruppieren Sie die Schaltflächen unter einem Spiel leere übergeordnete-Objekt. Damit die Schaltflächen in Raster Auflistung verfügbar sind, müssen Sie die Schaltflächen unter einem gemeinsamen übergeordneten Objekt zu gruppieren. Klicken Sie mit der rechten Maustaste in den Hiearachy, und klicken Sie auf "leer." Dies erstellt ein neues leeres game-Objekt können Sie alle Schaltflächen im einfügen. Es wird als "" gameobject"." angezeigt. Klicken Sie mit der rechten Maustaste auf, und benennen Sie sie in "ButtonCollection."

![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. Verschieben Sie alle Schaltflächen in der neuen Sammlung an. Hierzu wählen alle fünf die Schaltfläche "-Objekte in Ihrem Heirarch, und ziehen Sie sie alle unter"ButtonCollection"-spielobjekt, wie in der folgenden Abbildung dargestellt. Tipp: Wählen Sie mehrere Elemente aus, indem Sie die STRG-Taste gedrückt halten, während Sie Elemente auswählen.

![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. Der Schaltfläche-Sammlung MRTKs "Grid-Objekt-Collection" Komponente hinzufügen.  Zu diesem Zweck wählen Sie das übergeordnete Objekt von "ButtonCollection", und klicken Sie im Bereich mit den Inspektor auf die Schaltfläche "Komponente hinzufügen". Suchen Sie in der Suchleiste nach "Grid-Objekt-Collection", und wählen Sie ihn, wenn sie in der Liste angezeigt wird.

![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

Die Objektsammlung Grid-Komponente können Sie Schaltflächen oder einen Satz von Objekten in eine praktische Zeilen-, Spalten- oder Raster. Dies ist einer der Bausteine, die von der MRTK, die eine schnelle und einfache Möglichkeit zum Erstellen ansprechender Benutzeroberflächen stellt bereitgestellt.

5. Konfigurieren Sie die Auflistung der Raster-Objekt. Damit werden alle dem Zifferblatt der Schaltflächen des Benutzers, wählen Sie "orientieren Typ" und dann "konfrontiert übergeordneten vorwärts" (wie in der Abbildung gezeigt.) Als Nächstes ändern Sie die Zellengröße um den Abstand zwischen Schaltflächen festzulegen. Starten Sie mit 0,12 Einheiten 0,12 Einheiten für die Zellenbreite und Höhe der Zelle, wie in der folgenden Abbildung dargestellt. Möglicherweise müssen Sie diese Werte, je nachdem Objektschaltfläche/Ressourcen ausgewählt anpassen. Stellen Sie sicher, dass "Zeilen" auf 1 festgelegt ist. Klicken Sie dann auf "Sammlung aktualisieren", und die Szene sollte der folgenden Abbildung aussehen. 


![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

>Hinweis: Je nach Ausrichtung der untergeordneten Objekte oder des übergeordneten Objekts müssen Sie wahrscheinlich die Ausrichtung festlegen, anders als in zukünftigen Projekten anzupassen. Die Breite der Zelle und die Höhe der Zelle Felder müssen möglicherweise auch unterschiedlich, je nach Größe der Objekte in der Auflistung definiert werden.

### <a name="adding-text-into-your-scene"></a>Hinzufügen von Text in die Szene

In diesem Abschnitt erfahren Sie, wie zum Hinzufügen und Bearbeiten von Text, der Ihre Erfahrungen mixed Reality. Wenn Sie noch nicht geschehen, stellen Sie sicher TextMeshPro in Unity mithilfe der Anweisungen aktiviert haben [hier](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation).

1. Wählen Sie das übergeordnete Objekt von "ButtonCollection", und klicken Sie mit der rechten Maustaste auf die Auflistung. Erweitern Sie im Dropdownmenü "3D Object", und wählen Sie dann "TextMeshPro – Text". Ein Objekt TextMeshPro unter der Schaltfläche-Auflistung, sollte angezeigt werden, wie in der folgenden Abbildung dargestellt.

![Lektion 2: komplettes Kapitel4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lesson2 Kapitel4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)

2. Geben Sie in der Komponente TextMeshPro-Text-Feld (befindet sich im Bereich mit den Inspektor wie unten dargestellt) "Text der Schaltfläche Auflistung". Der Text wird in der Szene angezeigt, aber es wird hinter den Schaltflächen und/oder die falsche Größe.

![Lektion 2: komplettes Kapitel4 Schritt 2](images/Lesson2_Chapter4_Step2.JPG)

3. Um die Textgröße und die Platzierung zur besseren Lesbarkeit zu verbessern, passen Sie das Feld "Font-Size" in der TextMeshPro-Komponente, um die Größe der Schriftart ändern. Sie müssen auch anpassen, "Rect transformieren" positionieren und skalieren Sie wie in der folgenden Abbildung dargestellt. Sehen Sie die Bilder unten für Werte, die für diese Textkonfiguration verwendet, und verwenden Sie diese Werte als Ausgangspunkt aus der die Größe und Platzierung des Textfelds weiter verbessern können.

![Lektion 2: komplettes Kapitel4 Schritt 3](images/Lesson2_Chapter4_Step3.JPG)
![Lesson2 Kapitel4 Schritt 4](images/Lesson2_Chapter4_Step4.JPG)

5. Um die Textwerte, auf die Schaltfläche "-Objekte zu ändern, klicken Sie auf den Pfeil neben einer Schaltfläche zum Erweitern, und Navigieren auf das Objekt"SeeItSayItLabel", und navigieren Sie zu"TextMeshPro", in dem Sie den Text auf Schaltflächen in den obigen Schritten beschriebene bearbeiten können.

![Lektion 2: komplettes Kapitel4 Schritt 5](images/Lesson2_Chapter4_Step5.JPG)

### <a name="congratulations"></a>Herzlichen Glückwunsch!
In dieser Lektion haben Sie gelernt, kopieren, anpassen und konfigurieren eine Einstellung des MRTK (z. B. räumliche Awareness Mesh Sichtbarkeit.) Sie haben zudem die Interaktion mit einer Schaltfläche zum Auslösen von Ereignissen mithilfe von überwachten Hände auf der HoloLens-2. Schließlich haben Sie erstellen eine einfache Benutzeroberfläche, die mithilfe von Unity Text Mesh Pro der MRTKs Grid-Objektauflistung Komponente.

[Nächste Lektion: Platzierung von dynamischen Inhalt und Hochleistungscomputings](mrlearning-base-ch3.md)

