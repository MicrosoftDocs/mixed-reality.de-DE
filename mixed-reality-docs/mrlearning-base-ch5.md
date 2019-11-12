---
title: 'Tutorials zu den ersten Schritten: 6. Untersuchen von erweiterten Eingabeoptionen'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 5599fe48f62a35d1dc02ce30fb7858fd74e87685
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926536"
---
# <a name="6-exploring-advanced-input-options"></a>6. untersuchen erweiterter Eingabeoptionen

In diesem Tutorial werden verschiedene erweiterte Eingabeoptionen für hololens 2 untersucht, einschließlich der Verwendung von Sprachbefehlen, der Schwenkbewegung und der Eye-Nachverfolgung. 

## <a name="objectives"></a>Ziele

- Ereignisse mithilfe von Sprachbefehlen und Schlüsselwörtern Auslösers
- Verwenden von nach verfolgten Händen zum Schwenken von Texturen und 3D-Objekten mit nach verfolgten Händen
- Verwenden von hololens 2 Eye Tracking-Funktionen zum Auswählen von Objekten

## <a name="instructions"></a>Anweisungen

### <a name="enabling-voice-commands"></a>Aktivieren der Sprachbefehle

In diesem Abschnitt werden zwei Sprachbefehle implementiert. Zuerst wird die Möglichkeit eingeführt, den Bereich zur Diagnose der Framerate zu wechseln, indem Sie die Option "Diagnose umschalten" sagen. Zweitens wird die Möglichkeit zur Wiedergabe eines Sounds mit einem Sprachbefehl untersucht. Die mrtk-Profile und Einstellungen, die für die Konfiguration von Sprachbefehlen zuständig sind, werden zuerst überprüft.

1. Wählen Sie in der basescene-Hierarchie mixedrealitytoolkit aus. Wählen Sie dann im Bereich Inspektor die Option Eingabe aus, und klicken Sie auf die Schaltfläche Small Clone links neben defaultmixedrealityinputsystemprofile, um das Popup Profil zu öffnen. Klicken Sie im Popup Fenster auf Klonen, um ein neues Profil mixedrealityinputsystemprofile zu erstellen.

    ![mrlearning-Base-CH5-1-step1a. png](images/mrlearning-base-ch5-1-step1a.png)

    Dadurch wird das mixedrealitytoolkitconfigurationprofile-Profil auch automatisch mit dem neu erstellten mixedrealityinputsystemprofile aufgefüllt.

    ![mrlearning-Base-CH5-1-step1b. png](images/mrlearning-base-ch5-1-step1b.png)

2. Im Eingabe Systemprofil gibt es eine Reihe von Einstellungen. Erweitern Sie für Sprachbefehle den Abschnitt Speech, und befolgen Sie den gleichen Prozess wie im vorherigen Schritt, um die Datei defaultmixedrealityvoicecommandsprofile zu klonen und durch ihre eigene bearbeitbare Kopie zu ersetzen.

    ![mrlearning-Base-CH5-1-step2. png](images/mrlearning-base-ch5-1-step2.png)

    Im sprach Befehls Profil bemerken Sie einen Bereich von Einstellungen. Eine vollständige Beschreibung dieser Einstellungen finden Sie in der [Dokumentation zur mrtk-Sprache](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>).

    In der Standardeinstellung ist das allgemeine Verhalten auf Autostart festgelegt. Dies kann bei Bedarf in "manueller Start" geändert werden. Behalten Sie für dieses Beispiel den automatischen Start bei. Der mrtk verfügt über mehrere Standard Sprachbefehle, wie z. b. Menü, Umschalten der Diagnose und Umschalten von Profiler. Wir verwenden das Schlüsselwort "Umschalten der Diagnose" zum Aktivieren und Deaktivieren des Leistungs Zählers "Diagnostics Framerate". Außerdem wird in den folgenden Schritten ein neuer Sprachbefehl hinzugefügt.

3. Fügen Sie einen neuen Sprachbefehl hinzu. Klicken Sie hierzu auf die Schaltfläche + neuen Sprachbefehl hinzufügen. Sie sehen eine neue Zeile, die unter der Liste vorhandener Sprachbefehle angezeigt wird. Geben Sie den Sprachbefehl ein, den Sie verwenden möchten. Verwenden Sie in diesem Beispiel den Befehl "Musik abspielen".

    ![mrlearning-Base-CH5-1-step3. png](images/mrlearning-base-ch5-1-step3.png)

    >[!NOTE]
    >Sie können auch einen Tastencode für Sprachbefehle festlegen. Dadurch können Sprachbefehle Ereignisse beim Drücken einer Tastatur Taste auslöst.

4. Fügen Sie die Möglichkeit hinzu, auf Sprachbefehle zu reagieren. Wählen Sie ein beliebiges Objekt in der basescene-Hierarchie aus, dem keine anderen Eingabe Skripts angefügt sind, z. b. das mixedrealityplayspace-Spielobjekt. Klicken Sie im Inspektor-Panel auf Komponente hinzufügen, suchen Sie nach "Sprache", und wählen Sie das Skript für den Spracheingabe Handler aus.

    ![mrlearning-Base-CH5-1-step4. png](images/mrlearning-base-ch5-1-step4.png)

    Standardmäßig werden zwei Kontrollkästchen angezeigt. Das Kontrollkästchen ist das Kontrollkästchen ist erforderlich. Solange Sie auf das Objekt mit einem Ray-Eye-Eye-, Head-Eye-, Controller-und Hand Zeiger zeigen, wird der Sprachbefehl ausgelöst. Deaktivieren Sie dieses Kontrollkästchen, damit der Benutzer das Objekt nicht überprüfen muss, um den Voice-Befehl zu verwenden.

5. Fügen Sie die Möglichkeit hinzu, auf einen Sprachbefehl zu reagieren. Klicken Sie hierzu auf die Schaltfläche + im Spracheingabe Handler.

    ![mrlearning-Base-CH5-1-step5. png](images/mrlearning-base-ch5-1-step5.png)

6. Neben dem Schlüsselwort wird ein Dropdown Menü angezeigt. Wählen Sie Diagnose umschalten aus, damit eine Aktion ausgelöst wird, wenn der Benutzer den Ausdruck "Diagnose umschalten" sagt. Beachten Sie, dass Sie möglicherweise Element 0 erweitern müssen, indem Sie den Pfeil daneben drücken.

    ![mrlearning-Base-CH5-1-step6. png](images/mrlearning-base-ch5-1-step6.png)

    >[!NOTE]
    >Diese Schlüsselwörter werden basierend auf dem Profil, das Sie in Schritt 3 bearbeitet haben, aufgefüllt.

7. Fügen Sie das Diagnose System Voice-Steuerelement Skript hinzu, um die Diagnose der Framerate-Leistungs Zählers ein-und auszuschalten. Klicken Sie hierzu auf Komponente hinzufügen, suchen Sie nach Diagnose System sprach Steuerelemente Skript, und fügen Sie es aus dem Menü hinzu. Dieses Skript kann einem beliebigen Objekt hinzugefügt werden. Zur Vereinfachung fügen wir es jedoch demselben Objekt hinzu, dem auch der Spracheingabe-Handler hinzugefügt wurde.

    ![mrlearning-Base-CH5-1-STEP7. png](images/mrlearning-base-ch5-1-step7.png)

8. Fügen Sie eine neue Antwort in den Spracheingabe Handler ein. Klicken Sie hierzu auf das Symbol "+", um der Antwortliste eine neue Antwort hinzuzufügen.

    ![mrlearning-Base-CH5-1-step8. png](images/mrlearning-base-ch5-1-step8.png)

9. Ziehen Sie das-Objekt, das über das sprach Steuerelement des Diagnosesystems verfügt, in die neue Antwort, die Sie soeben im vorherigen Schritt erstellt haben.

    ![mrlearning-Base-CH5-1-step9. png](images/mrlearning-base-ch5-1-step9.png)

10. Klicken Sie auf die Dropdown Liste Funktion (in der Sie keine Funktion hat), dann auf sprach Steuerelemente für Diagnosesysteme, und wählen Sie die Funktion "degglediagnostics ()" aus, bei der Ihre Diagnose ein-und ausgeschaltet wird.

    ![mrlearning-Base-CH5-1-step10. png](images/mrlearning-base-ch5-1-step10.png)

    >[!IMPORTANT]
    > Bevor Sie auf Ihr Gerät aufbauen, müssen Sie die MIC-Einstellungen aktivieren. Klicken Sie hierzu auf Datei, und wechseln Sie zu Buildeinstellungen, Player Einstellungen, und vergewissern Sie sich, dass die Mikrofon Funktion festgelegt ist.

    Fügen Sie als nächstes die Möglichkeit hinzu, eine Audiodatei über den Voice-Befehl mit dem Octa-Objekt wiederzugeben. Erinnern Sie sich aus [Lektion 4](mrlearning-base-ch4.md) , dass die Möglichkeit zur Wiedergabe eines Audioclips von der Berührung des Octa-Objekts hinzugefügt wurde. Diese Audioquelle verwenden wir nun auch für unseren Musik-Sprachbefehl.

11. Wählen Sie das Octa-Objekt in der basescene-Hierarchie aus.

12. Fügen Sie einen weiteren Spracheingabe Handler hinzu (wiederholen Sie die Schritte 4 und 5), aber mit dem octacore-Objekt.

13. Anstatt den Befehl zum Umschalten der Diagnose Sprache aus Schritt 6 hinzuzufügen, fügen Sie wie in der Abbildung unten gezeigt den Befehl "Musik Stimmen abspielen" hinzu.

    ![mrlearning-Base-CH5-1-step13. png](images/mrlearning-base-ch5-1-step13.png)

14. Fügen Sie wie in den Schritten 8 und 9 eine neue Antwort hinzu, und ziehen Sie das Octa-Objekt (das Objekt, das über das sprach Steuerelement für den Diagnose System verfügt) in den leeren Antwort Slot.

15. Wählen Sie das Dropdown Menü aus, das keine Funktion anzeigt. Wählen Sie dann Audioquelle, gefolgt von playoneshot (Audioclip) aus.

    ![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. In diesem Beispiel verwenden wir den gleichen Audioclip aus [Lektion 4](mrlearning-base-ch4.md). Wechseln Sie in das Projekt Panel, suchen Sie nach dem Audioclip "MRTK_Gem", und ziehen Sie ihn in den audioquellslot, wie in der folgenden Abbildung dargestellt. Nun antwortet Ihre Anwendung auf die Sprachbefehle "Diagnose umschalten", um den indikatorenindikatorenbereich zu umschalten und Musik wiederzugeben, um den MRTK_Gem-Song wiederzugeben.

    ![Lesson5 Chapter1 Step16im](images/Lesson5_chapter1_step16im.PNG)

### <a name="the-pan-gesture"></a>Die Geste „Schwenken“

In diesem Abschnitt erfahren Sie, wie Sie die Schwenkbewegung verwenden. Dies ist hilfreich, wenn Sie mit dem Finger oder der Hand einen Bildlauf durch den Inhalt durchführen möchten. Sie können mit der Schwenkbewegung auch Objekte drehen, eine Auflistung von 3D-Objekten durchlaufen oder sogar einen Bildlauf in einer 2D-Benutzeroberfläche durchführen. <!--TMP You will also learn how to use the pan gesture to warp a texture, and how to move a collection of 3D objects.-->

1. Erstellen Sie einen Quader. Klicken Sie in der basescene-Hierarchie mit der rechten Maustaste auf "3D-Objekt" gefolgt von Quad.

    ![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. Ordnen Sie den Quad nach Bedarf neu an. In unserem Beispiel legen wir das x = 0, y = 0 und den z = 1,5 Weg von der Kamera für eine bequeme Position von hololens 2 fest.

    >[!NOTE]
    >Wenn die Quad-Blöcke oder vor dem Inhalt aus den vorherigen Lektionen vorhanden sind, achten Sie darauf, Sie zu verschieben, damit keines der anderen Objekte blockiert wird.

3. Weisen Sie dem Quader ein Material zu. Dieses Material ist das, was wir mit der Schwenkbewegung durchblättern werden.

    ![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. Geben Sie im Projekt Panel "Pan Content" in das Suchfeld ein. Ziehen Sie dieses Material auf das Vierfache in Ihrer Szene.

    >[!NOTE]
    >Das Inhalts Material von Pan ist nicht in der mrtk enthalten, sondern eine Ressource in dem Asset-Paket dieses Moduls, das in vorherigen Lektionen importiert wurde.

    >[!NOTE]
    >Der importierte geschwenkte Inhalt kann gestreckt aussehen. Sie können dieses Problem heben, indem Sie die Werte x, y und z für die Abmessungen des Quaders anpassen, bis Sie mit dem Erscheinungsbild zufrieden sind.

    Zum Verwenden der Geste „Schwenken“ benötigen Sie ein Collider für das Objekt. Sie stellen möglicherweise fest, dass der Quader bereits ein Gitter-Collider aufweist. Das Gitter-Collider ist jedoch nicht ideal, da es äußerst schmal und daher schwer auszuwählen ist. Es empfiehlt sich, das Gitter-Collider durch ein Feld-Collider zu ersetzen.

5. Klicken Sie mit der rechten Maustaste auf den Mesh-Collider im Inspektor-Panel. Entfernen Sie Sie dann, indem Sie auf Komponente entfernen klicken.

    ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. Fügen Sie jetzt das Feld "Collider" hinzu, indem Sie auf Komponente hinzufügen klicken und "Box Collider" suchen Der standardmäßige hinzugefügte Box-Collider ist noch zu dünn. Klicken Sie daher auf die Schaltfläche "Collider bearbeiten", um Im ausgewählten Zustand können Sie seine Größe über die x, y und z oder mithilfe der Elemente im Szenen-Editor anpassen. In diesem Beispiel soll das Feld-Collider hinter dem Quader etwas verlängert werden. Ziehen Sie im Szenen-Editor das Feld-Collider aus dem Hintergrund nach außen (siehe Abbildung unten). Dadurch kann der Benutzer nicht nur seinen Finger, sondern die gesamte Hand zum Scrollen verwenden.

    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)

7. Machen Sie das Objekt interaktiv. Da wir direkt mit dem Quad interagieren möchten, möchten wir die touchable-Komponente der Near-Interaktion verwenden, die wir in Lektion 4 für die Wiedergabe von Musik aus dem Octa-Objekt verwendet haben. Klicken Sie auf Komponente hinzufügen, suchen Sie nach "Near Interaktion touchable", und wählen Sie Sie aus, wie in den folgenden Abbildungen dargestellt.

    ![mrlearning-Base-CH5-2-step7a. png](images/mrlearning-base-ch5-2-step7a.png)

    Wenn eine gelbe Warnung zu Begrenzungen und/oder Center nicht mit der Größe von boxcollider und/oder dem Center übereinstimmt, klicken Sie auf die Schaltflächen fixbegrenzungen und/oder fixmitte, um die Mittelpunkt-und Begrenzungs Werte zu aktualisieren.

    ![mrlearning-Base-CH5-2-step7b. png](images/mrlearning-base-ch5-2-step7b.png)

8. Fügen Sie die Fähigkeit zum Erkennen der Geste „Schwenken“ hinzu. Klicken Sie auf Komponente hinzufügen, geben Sie "Hand Interaktion" in das Suchfeld ein, und fügen Sie die Skript Komponente "Hand Interaktion schwenken schwenken" hinzu.

    ![mrlearning-Base-CH5-2-step8a. png](images/mrlearning-base-ch5-2-step8a.png)

    Und damit verfügen Sie über ein Schwenk-aktiviertes Quad.

    Wie Sie sehen, hat die Komponente "Hand Interaktion schwenken schwenken" verschiedene Einstellungen, als optionale Übung, Sie können mit Ihnen experimentieren.

    ![mrlearning-Base-CH5-2-step8b. png](images/mrlearning-base-ch5-2-step8b.png)

<!--TMP
   Next, we will learn how to pan 3D objects. 

10. Right-click the quad object, select 3D object and click Cube. Scale the cube so that it’s roughly x = 0.1, y = 0.1 and z = 0.1. Copy that cube three times by right-clicking the cube and pressing duplicate, or by pressing control/command D. Space them out evenly. Your scene should look similar to the image below.

![Lesson5 Chapter2 Step10im](images/Lesson5_chapter2_step10im.PNG)

11. Select the quad again and under the hand interaction pan script, set the pan actions to each of the cubes. Under Pan Event Receivers, we want to specify the number of objects receiving the event. Since there are four cubes, type “4” and press Enter. Four empty fields should appear.

![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)

12. Drag each of the cubes into each of the empty element slots.
     ![Lesson5 Chapter2 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. Add the Move with Pan script to all of the cubes by pressing and holding control/command and select each object. From the Inspector panel, click Add Component and search for “move with pan.” Click the script and it is added to each cube. Now the 3D objects will move with your pan gesture. If you remove the mesh render on your quad, you should now have an invisible quad where you can pan through a list of 3D objects.
-->

### <a name="eye-tracking"></a>Eyetracking

In diesem Abschnitt erfahren Sie, wie Sie die Eye-Nachverfolgung in unserer Demo aktivieren. Wir werden die 3D-Menü Elemente langsam drehen, wenn Sie mit dem Blick angezeigt werden. Zudem wird ein unterhaltsamer Effekt ausgelöst, wenn das anvisierte Element ausgewählt wird.

1. Stellen Sie sicher, dass die mrtk-profile ordnungsgemäß für die Augen Verfolgung konfiguriert sind Wechseln Sie zu diesem Zweck zu den Anweisungen unter " [Getting Started with Eye Tracking in mrtk](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) ", und überprüfen Sie, ob die Augen Verfolgung ordnungsgemäß konfiguriert ist, indem Sie die Schritte im Abschnitt [Einrichten der Eye-Nachverfolgung Schritt für Schritt](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-eye-tracking-step-by-step) ausführen. Vervollständigen Sie alle verbleibenden Schritte in der Dokumentation.

    >[!NOTE]
    >Wenn Sie die DefaultHoloLens2InputSystemProfile verwendet haben, wie in der Lektion [configure the Mixed Reality Toolkit](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#configure-the-mixed-reality-toolkit) beschrieben, um Ihr benutzerdefiniertes mrtk-Konfigurations Profil zu klonen, ist die Eye-Nachverfolgung im Unity-Projekt standardmäßig aktiviert. Sie müssen jedoch weiterhin die Augen Verfolgungs Simulation für den Unity-Editor einrichten und Visual Studio so konfigurieren, dass die Eye-Nachverfolgung für den Build zugelassen wird.

    Unter dem obigen Link erhalten Sie kurze Anleitungen für folgende Aufgaben:

    - Erstellen des Windows Mixed Reality-Augenblicks Datenanbieter für die Verwendung im mrtk-Profil
    - Aktivieren der Eye-Nachverfolgung im an die Kamera angehängten Blick Anbieter
    - Einrichten einer Augen Verfolgungs Simulation im Unity-Editor
    - Bearbeiten der Funktionen der Visual Studio-Lösung, mit denen Eyetracking in der erstellten Anwendung zugelassen wird

2. Fügen Sie die EyeTrackingTarget-Komponente Zielobjekten hinzu. Damit ein Objekt auf Eye-Eye-Ereignisse reagieren kann, müssen wir die Komponente "eyetrackingtarget" für jedes Objekt, mit dem wir interagieren möchten, mithilfe von "Eye Eye" hinzufügen. Fügen Sie diese Komponente jedem der neun 3D-Objekte hinzu, die zur Rastersammlung gehören.

    >[!TIP]
    >Mit der Umschalttaste und/oder der STRG-Taste können Sie mehrere Elemente in der Szenen Hierarchie auswählen und dann die Komponente "pipetrackingtarget" per Massen Vorgang hinzufügen.

    ![Lesson5 Chapter3 Schritt 2](images/Lesson5Chapter3Step2.JPG)

3. Als Nächstes fügen wir das Skript "eyetrackingtutorialdemo" für einige interessante Interaktionen hinzu. Das Skript "eyetrackingtutorialdemo" ist als Teil dieses Tutorials in der tutorialreihe enthalten. Sie ist nicht standardmäßig mit dem Mixed Reality Toolkit enthalten. Fügen Sie für jedes 3D-Objekt in der Raster Auflistung das Skript "eyetrackingtutorialdemo" hinzu, indem Sie im Menü "Komponente hinzufügen" nach der Komponente suchen.

   ![Lesson5 Chapter3 Schritt 3](images/Lesson5Chapter3Step3.JPG)

4. Drehen Sie das Objekt, während Sie das Ziel anvisieren. Wir möchten unsere 3D-Objekte so konfigurieren, dass Sie während der Betrachtung aussehen. Fügen Sie zu diesem Zweck ein neues Feld in den ein, und betrachten Sie dabei den Target ()-Abschnitt der "pipetrackingtarget"-Komponente, wie in der folgenden Abbildung dargestellt.

    ![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)

    Fügen Sie im neu erstellten Feld das aktuelle Spielobjekt dem leeren Feld hinzu, und wählen Sie "eyetrackingtutorialdemo > rotatetarget ()" aus, wie in der folgenden Abbildung dargestellt. Nun ist das 3D-Objekt so konfiguriert, dass es bei Anvisieren per Eyetracking gedreht wird.

    ![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)

5. Fügen Sie in die Funktion "Blip-Ziel" ein, die bei der Auswahl per Air-Tap oder "Select" (Auswählen von "Select") auf "" ausgewählt wird. Ähnlich wie bei Schritt 4 möchten wir "eyetrackingtutorialdemo > bliptarget ()" Auslösers, indem Sie es dem "Select ()"-Feld des Spiel Objekts der "eyetrackingtarget"-Komponente zuweisen, wie in der folgenden Abbildung dargestellt. Wenn diese jetzt konfiguriert ist, bemerken Sie immer dann, wenn Sie eine SELECT-Aktion (z. b. Air-Tap oder den Voice-Befehl "Select"), eine geringfügige Unterbrechung im Spielobjekt.

    ![Lesson5 Chapter3 Schritt 5](images/Lesson5Chapter3Step5.JPG)

6. Vergewissern Sie sich vor der Erstellung in HoloLens 2, dass die Eyetracking-Funktionen ordnungsgemäß konfiguriert sind. Zum Zeitpunkt der Erstellung dieses Artikels ist Unity noch nicht in der Lage, die Blick Eingabe für die Augen Verfolgungs Funktionen festzulegen. Diese Funktion ist erforderlich, damit die Eye-Nachverfolgung in hololens 2 funktioniert. Befolgen Sie die Anweisungen unter [Testen Ihrer Unity-App auf einer hololens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) -Anleitung, um die Blick Eingabe Funktion zu aktivieren.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben der Anwendung erfolgreich grundlegende Funktionen zur Augen Verfolgung hinzugefügt. Diese Aktionen stellen nur den Einstieg in eine ganze Welt der Möglichkeiten mit Eyetracking dar. In diesem Kapitel wird außerdem Lektion 5 beendet, in dem wir mehr über erweiterte Eingabefunktionen erfahren, wie z. b. Sprachbefehle, Schwenkbewegungen und die Eye-Nachverfolgung.

[Nächste Lektion: 7. Erstellen einer Beispielanwendung für ein Mond Modul](mrlearning-base-ch6.md)
