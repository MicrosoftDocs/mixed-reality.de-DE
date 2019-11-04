---
title: 'Tutorials zu den ersten Schritten: 6. Untersuchen von erweiterten Eingabeoptionen'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: bb6aa620cebfda74b0b6b5f6ca04e1eeb68d9c7b
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438454"
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

1. Wählen Sie in der Basis Szenen Hierarchie mixedrealitytoolkit aus. Scrollen Sie im Inspektor-Panel nach unten zu Eingabe System Einstellungen. Doppelklicken Sie, um das Eingabe Systemprofil zu öffnen. Klonen Sie das Eingabe Systemprofil, damit es in [Lektion 1](mrlearning-base-ch1.md) bearbeitet werden kann. 

Im Eingabe Systemprofil gibt es eine Reihe von Einstellungen. Wählen Sie für Sprachbefehle Einstellungen für Sprachbefehle aus. 

![Lesson5 Chapter1 Step2im](images/Lesson5_Chapter1_step2im.PNG)

2. Klonen Sie das Sprachbefehle Profil, damit es in [Lektion 1](mrlearning-base-ch1.md)bearbeitet werden kann. Doppelklicken Sie auf das sprach Befehls Profil, in dem Sie einen Bereich von Einstellungen bemerken. Eine vollständige Beschreibung dieser Einstellungen finden Sie in der [Dokumentation zur mrtk-Sprache](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>). 

>Hinweis: Standardmäßig ist das allgemeine Verhalten "automatisch starten". Dies kann bei Bedarf in "manueller Start" geändert werden. Behalten Sie für dieses Beispiel den automatischen Start bei. Der mrtk verfügt über mehrere Standard Sprachbefehle, wie z. b. Menü, Umschalten der Diagnose und Umschalten von Profiler. Wir verwenden das Schlüsselwort "Umschalten der Diagnose" zum Aktivieren und Deaktivieren des Leistungs Zählers "Diagnostics Framerate". Außerdem wird in den folgenden Schritten ein neuer Sprachbefehl hinzugefügt.
>
> ![Lesson5 Chapter1 Noteim](images/Lesson5_chapter1_noteim.PNG)

3. Fügen Sie einen neuen Sprachbefehl hinzu. Klicken Sie hierzu auf die Schaltfläche + neuen Sprachbefehl hinzufügen. Sie sehen eine neue Zeile, die unter der Liste vorhandener Sprachbefehle angezeigt wird. Geben Sie den Sprachbefehl ein, den Sie verwenden möchten. Verwenden Sie in diesem Beispiel den Befehl "Musik abspielen".

>Tipp: Sie können auch einen Keycode für Sprachbefehle festlegen. Dadurch können Sprachbefehle Ereignisse beim Drücken einer Tastatur Taste auslöst.    

4. Fügen Sie die Möglichkeit hinzu, auf Sprachbefehle zu reagieren. Wählen Sie ein beliebiges Objekt in der Basis Szenen Hierarchie aus, dem keine anderen Eingabe Skripts angefügt sind (z. b. kein Manipulations Handler). Klicken Sie im Inspektor-Panel auf Komponente hinzufügen. Geben Sie "Spracheingabe Handler" ein, und wählen Sie ihn aus.

   ![Lesson5 Chapter1 Step4im](images/Lesson5_chapter1_step4im.PNG)

   

Standardmäßig werden zwei Kontrollkästchen angezeigt. Das Kontrollkästchen ist das Kontrollkästchen ist erforderlich. Solange Sie auf das Objekt mit einem Ray-Eye-Eye-, Head-Eye-, Controller-und Hand Zeiger zeigen, wird der Sprachbefehl ausgelöst. Deaktivieren Sie dieses Kontrollkästchen, damit der Benutzer das Objekt nicht überprüfen muss, um den Voice-Befehl zu verwenden.

5. Fügen Sie die Möglichkeit hinzu, auf einen Sprachbefehl zu reagieren. Klicken Sie hierzu auf die Schaltfläche +, die sich im Spracheingabe Handler befindet, und wählen Sie das Schlüsselwort aus, auf das Sie reagieren möchten.

   > Hinweis: Diese Schlüsselwörter werden basierend auf dem Profil, das Sie im vorherigen Schritt bearbeitet haben, aufgefüllt.

![Lesson5 Chapter1 Step5im](images/Lesson5_chapter1_step5im.PNG)

6. Neben dem Schlüsselwort wird ein Dropdown Menü angezeigt. Wählen Sie Diagnose umschalten aus, damit eine Aktion ausgelöst wird, wenn der Benutzer den Ausdruck "Diagnose umschalten" sagt. Beachten Sie, dass Sie möglicherweise Element 0 erweitern müssen, indem Sie den Pfeil daneben drücken.

![Lesson5 Chapter1 Step6im](images/Lesson5_chapter1_step6im.PNG)

7. Fügen Sie das Diagnose Demo-Steuerelement Skript hinzu, um die Diagnose des Framerate-Leistungs Zählers ein-und auszuschalten. Klicken Sie hierzu auf Komponente hinzufügen, suchen Sie nach Diagnose demosteuerelemente Skript, und fügen Sie es aus dem Menü hinzu. Dieses Skript kann einem beliebigen Objekt hinzugefügt werden. Der Einfachheit halber fügen wir das Objekt dem gleichen Objekt hinzu wie den Spracheingabe Handler. 

   > Hinweis: Dieses Skript ist nur in diesen Modulen enthalten, jedoch nicht im ursprünglichen mrtk.

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step7im.PNG)

8. Fügen Sie eine neue Antwort in den Spracheingabe Handler ein. Klicken Sie hierzu auf die Schaltfläche "+" unterhalb von "Response ()" (durch grünen Pfeil in der Abbildung oben gekennzeichnet).

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step8.PNG)

9. Ziehen Sie das-Objekt mit dem Skript für Diagnose demosteuerelemente in die neue Antwort, die Sie soeben in Schritt 8 erstellt haben.
    ![Lesson5 Chapter1 Step9im](images/Lesson5_chapter1_step9im.PNG)

10. Wählen Sie die Dropdown Liste "keine Funktion", gefolgt von Diagnose demosteuerelement. Wählen Sie dann die Funktion "bei der Funktion zum Umschalten der Diagnose ()" aus, bei der die Diagnose ein-und ausgeschaltet wird.  ![Lesson5 Chapter1 Step10im](images/Lesson5_chapter1_step10im.PNG)
    
> Beachten Sie, dass Sie die MIC-Einstellungen aktivieren müssen, bevor Sie auf Ihr Gerät bauen. Klicken Sie hierzu auf Datei, und wechseln Sie zu Buildeinstellungen, Player Einstellungen, und vergewissern Sie sich, dass die Mikrofon Funktion festgelegt ist.

Fügen Sie als nächstes die Möglichkeit hinzu, eine Audiodatei über den Voice-Befehl mit dem Octa-Objekt wiederzugeben. Erinnern Sie sich aus [Lektion 4](mrlearning-base-ch4.md) , dass die Möglichkeit zur Wiedergabe eines Audioclips von der Berührung des Octa-Objekts hinzugefügt wurde. Diese Audioquelle verwenden wir nun auch für unseren Musik-Sprachbefehl.

11. Wählen Sie das Octa-Objekt in der Basis Szenen Hierarchie aus.

12. Fügen Sie einen weiteren Spracheingabe Handler hinzu (wiederholen Sie die Schritte 4 und 5), aber mit dem octacore-Objekt. 

13. Anstatt den Befehl zum Umschalten der Diagnose Sprache aus Schritt 6 hinzuzufügen, fügen Sie wie in der Abbildung unten gezeigt den Befehl "Musik Stimmen abspielen" hinzu.
    
     ![Lesson5 Chapter1 Step13im](images/Lesson5_chapter1_step13im.PNG)
    
    
    
14. Fügen Sie wie in den Schritten 8 und 9 eine neue Antwort hinzu, und ziehen Sie das Octa-Objekt in den leeren Antwort Slot.

15. Wählen Sie das Dropdown Menü aus, das keine Funktion anzeigt. Wählen Sie dann Audioquelle, gefolgt von playoneshot (Audioclip) aus.

![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. In diesem Beispiel verwenden wir den gleichen Audioclip aus [Lektion 4](mrlearning-base-ch4.md). Wechseln Sie in das Projekt Panel, suchen Sie nach dem Audioclip "MRTK_Gem", und ziehen Sie ihn in den audioquellslot, wie in der folgenden Abbildung dargestellt. Nun antwortet Ihre Anwendung auf die Sprachbefehle "Diagnose umschalten", um den indikatorenindikatorenbereich zu umschalten und Musik abspielen, um den MRTK_Gem-Song wiederzugeben.
     ![Lesson5 Chapter1 Step16im](images/Lesson5_chapter1_step16im.PNG)


### <a name="the-pan-gesture"></a>Die Geste „Schwenken“ 

In diesem Abschnitt erfahren Sie, wie Sie die Schwenkbewegung verwenden. Dies ist hilfreich, wenn Sie mit dem Finger oder der Hand einen Bildlauf durch den Inhalt durchführen möchten. Sie können mit der Schwenkbewegung auch Objekte drehen, eine Auflistung von 3D-Objekten durchlaufen oder sogar einen Bildlauf in einer 2D-Benutzeroberfläche durchführen. Außerdem erfahren Sie, wie Sie mit der Schwenkbewegung eine Textur verkriechen und wie Sie eine Auflistung von 3D-Objekten verschieben.

1. Erstellen Sie einen Quader. Klicken Sie in der Basis Szenen Hierarchie mit der rechten Maustaste auf "3D-Objekt" gefolgt von Quad.

![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. Ordnen Sie den Quad nach Bedarf neu an. In unserem Beispiel legen wir das x = 0, y = 0 und den z = 1,5 Weg von der Kamera für eine bequeme Position von hololens 2 fest.

   > Hinweis: Wenn sich die Quad-Blöcke oder vor dem Inhalt aus den vorherigen Lektionen befinden, achten Sie darauf, Sie zu verschieben, damit keines der anderen Objekte blockiert wird.

3. Weisen Sie dem Quader ein Material zu. Dieses Material ist das, was wir mit der Schwenkbewegung durchblättern werden. 

![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. Geben Sie im Projekt Panel "Pan Content" in das Suchfeld ein. Ziehen Sie dieses Material auf das Vierfache in Ihrer Szene. 

> Hinweis: das Inhalts Material von Pan ist nicht in der mrtk enthalten, sondern eine Ressource in dem Asset-Paket dieses Moduls, das in vorherigen Lektionen importiert wurde. 

> Hinweis: Wenn Sie den Pan-Inhalt hinzufügen, kann er gestreckt aussehen. Sie können dieses Problem heben, indem Sie die Werte x, y und z für die Abmessungen des Quaders anpassen, bis Sie mit dem Erscheinungsbild zufrieden sind.

Zum Verwenden der Geste „Schwenken“ benötigen Sie ein Collider für das Objekt. Sie stellen möglicherweise fest, dass der Quader bereits ein Gitter-Collider aufweist. Das Gitter-Collider ist jedoch nicht ideal, da es äußerst schmal und daher schwer auszuwählen ist. Es empfiehlt sich, das Gitter-Collider durch ein Feld-Collider zu ersetzen.

5. Klicken Sie mit der rechten Maustaste auf den Mesh-Collider im Inspektor-Panel. Entfernen Sie Sie dann, indem Sie auf Komponente entfernen klicken.
    ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)
6. Fügen Sie jetzt das Feld "Collider" hinzu, indem Sie auf Komponente hinzufügen klicken und "Box Collider" suchen Der standardmäßige hinzugefügte Box-Collider ist noch zu dünn. Klicken Sie daher auf die Schaltfläche "Collider bearbeiten", um Im ausgewählten Zustand können Sie seine Größe über die x, y und z oder mithilfe der Elemente im Szenen-Editor anpassen. In diesem Beispiel soll das Feld-Collider hinter dem Quader etwas verlängert werden. Ziehen Sie im Szenen-Editor das Feld-Collider aus dem Hintergrund nach außen (siehe Abbildung unten). Dadurch kann der Benutzer nicht nur seinen Finger, sondern die gesamte Hand zum Scrollen verwenden. 
    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)
7. Machen Sie das Objekt interaktiv. Da wir direkt mit dem Quad interagieren möchten, möchten wir die touchable-Komponente der Near-Interaktion verwenden, die wir in Lektion 4 für die Wiedergabe von Musik aus dem Octa-Objekt verwendet haben. Klicken Sie auf Komponente hinzufügen, suchen Sie nach "Near Interaktion touchable", und wählen Sie Sie aus, wie in den folgenden Abbildungen dargestellt. 

8. Fügen Sie die Fähigkeit zum Erkennen der Geste „Schwenken“ hinzu. Klicken Sie auf Komponente hinzufügen und geben Sie "Hand Interaktion schwenken" ein. Sie haben die Auswahl zwischen „Hand Ray“ (Ganze Hand) (wodurch Sie aus der Entfernung schwenken können) und „Index Finger“ (Zeigefinger). In diesem Beispiel behalten wir die Einstellung „Index Finger“ (Zeigefinger) bei. 
    ![Lesson5 Chapter2 Step7 8Im](images/Lesson5_chapter2_step7-8im.PNG)

![Lesson5 Chapter2 Step8im](images/Lesson5_chapter2_step8im.PNG)

9. Im Skript "Hand Interaktion schwenken" sperrt die horizontale und die vertikale Sperre für vertikale Kontrollkästchen jeweils die Bewegungen. Mit den Umbruch Textur Einstellungen wird die Textur (Textur Zuordnung) den Schwenkbewegungen des Benutzers folgt. In diesem Beispiel aktivieren Sie dieses Kontrollkästchen. Es ist auch eine Geschwindigkeit aktiv, die deaktiviert ist, wenn Sie nicht aktiviert ist. Aktivieren Sie auch dieses Kontrollkästchen. Nun verfügen Sie über ein "Pan-aktiviertes Quad".

   

   Nun erfahren Sie, wie Sie 3D-Objekte schwenken. 

10. Klicken Sie mit der rechten Maustaste auf das Quad-Objekt, wählen Sie 3D-Objekt und dann Cube Skalieren Sie den Würfel etwa auf die Abmessungen x = 0,1, y = 0,1 und z = 0,1. Kopieren Sie diesen Cube dreimal, indem Sie mit der rechten Maustaste auf den Cube klicken und duplizieren, oder indem Sie Control/Command D. Space auf gleichmäßig klicken. Die Szene sollte in etwa wie in der folgenden Abbildung aussehen.

![Lesson5 Chapter2 Step10im](images/Lesson5_chapter2_step10im.PNG)







11. Wählen Sie den Quad erneut aus, und legen Sie im Skript Hand Interaktion Schwenken die schwenken-Aktionen auf die einzelnen Cubes fest. Unter Pan-Ereignis Empfängern möchten wir die Anzahl der Objekte angeben, die das Ereignis empfangen. Da vier Cubes vorhanden sind, geben Sie "4" ein, und drücken Sie die EINGABETASTE. Es sollten vier leere Felder angezeigt werden.


![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)



12. Ziehen Sie alle Cubes in alle leeren Element Slots.
     ![Lesson5 Chapter2 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. Fügen Sie das Skript mit Schwenken mit schwenken zu allen Cubes hinzu, indem Sie das Steuerelement/den Befehl gedrückt halten und die einzelnen Objekte auswählen. Klicken Sie im Inspektor-Panel auf Komponente hinzufügen, und suchen Sie nach "mit Schwenken verschieben". Klicken Sie auf das Skript, und es wird jedem Cube hinzugefügt. Nun werden die 3D-Objekte mit der Schwenkbewegung bewegt. Wenn Sie das Gitter-Rendering um den Quader entfernen, verfügen Sie über einen unsichtbaren Quader, mit dem Sie durch eine Liste von 3D-Objekten schwenken können.

### <a name="eye-tracking"></a>Eyetracking

In diesem Abschnitt erfahren Sie, wie Sie die Eye-Nachverfolgung in unserer Demo aktivieren. Wir werden die 3D-Menü Elemente langsam drehen, wenn Sie mit dem Blick angezeigt werden. Zudem wird ein unterhaltsamer Effekt ausgelöst, wenn das anvisierte Element ausgewählt wird.

1. Stellen Sie sicher, dass die mrtk-profile richtig konfiguriert sind. Zum Zeitpunkt der Veröffentlichung dieses Dokuments sind in der Konfiguration der Profile im Mixed Reality-Toolkit Eyetracking-Funktionen standardmäßig nicht enthalten. Befolgen Sie die Anweisungen im Abschnitt "Einrichten der für die Eye-Nachverfolgung erforderlichen mrtk-profile", wie in der [Mixed Reality Toolkit-Dokumentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-the-mrtk-profiles-required-for-eye-tracking  )beschrieben. Stellen Sie sicher, dass die Eye-Nachverfolgung ordnungsgemäß konfiguriert ist, indem Sie alle verbleibenden Schritte im oben beschriebenen Dokumentations Link ausführen, einschließlich der Aktivierung der Eye-Nachverfolgung in "Pavillon Provider" (der an die Kamera angehängten Komponente) und dem Aktivieren der Simulation der Beachten Sie, dass zukünftige Versionen von mrtk die Eye-Nachverfolgung standardmäßig einschließen können.

    Unter dem obigen Link erhalten Sie kurze Anleitungen für folgende Aufgaben:

    - Erstellen der Augenblick Datenanbieter zur Verwendung im mrtk-Profil
    - Aktivieren des Eyetracking im Gaze-Anbieter
    - Einrichten einer Augen Verfolgungs Simulation im Editor
    - Bearbeiten der Funktionen der Visual Studio-Lösung, mit denen Eyetracking in der erstellten Anwendung zugelassen wird

2. Fügen Sie die EyeTrackingTarget-Komponente Zielobjekten hinzu. Damit ein Objekt auf Eye-Eye-Ereignisse reagieren kann, müssen wir die Komponente "eyetrackingtarget" für jedes Objekt, mit dem wir interagieren möchten, mithilfe von "Eye Eye" hinzufügen. Fügen Sie diese Komponente jedem der neun 3D-Objekte hinzu, die zur Rastersammlung gehören. Tipp: Wählen Sie mehrere Elemente in der Hierarchie aus, um die Komponente "pipetrackingtarget" per Massen Vorgang hinzuzufügen.
    ![Lesson5 Chapter3 Step2](images/Lesson5Chapter3Step2.JPG)

3. Als Nächstes fügen wir das Skript "eyetrackingtutorialdemo" für einige interessante Interaktionen hinzu. Das Skript "eyetrackingtutorialdemo" ist als Teil dieses Tutorials in der tutorialreihe enthalten. Sie ist nicht standardmäßig mit dem Mixed Reality Toolkit enthalten. Fügen Sie für jedes 3D-Objekt in der Raster Auflistung das Skript "eyetrackingtutorialdemo" hinzu, indem Sie im Menü "Komponente hinzufügen" nach der Komponente suchen.
   ![Lesson5 Chapter3 Step3](images/Lesson5Chapter3Step3.JPG)

4. Drehen Sie das Objekt, während Sie das Ziel anvisieren. Wir möchten das 3D-Objekt so konfigurieren, dass es sich während der Betrachtung dreht. Fügen Sie zu diesem Zweck ein neues Feld in den ein, und betrachten Sie dabei den Target ()-Abschnitt der "pipetrackingtarget"-Komponente, wie in der folgenden Abbildung dargestellt. 

![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)
![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)



Fügen Sie im neu erstellten Feld das aktuelle Spielobjekt dem leeren Feld hinzu, und wählen Sie "eyetrackingtutorialdemo > rotatetarget ()" aus, wie in der folgenden Abbildung dargestellt. Nun ist das 3D-Objekt so konfiguriert, dass es bei Anvisieren per Eyetracking gedreht wird. 

5. Fügen Sie in die Funktion "Blip-Ziel" ein, die bei der Auswahl per Air-Tap oder "Select" (Auswählen von "Select") auf "" ausgewählt wird. Ähnlich wie bei Schritt 4 möchten wir "eyetrackingtutorialdemo > bliptarget ()" Auslösers, indem Sie es dem "Select ()"-Feld des Spiel Objekts der "eyetrackingtarget"-Komponente zuweisen, wie in der folgenden Abbildung dargestellt. Wenn diese jetzt konfiguriert ist, bemerken Sie immer dann, wenn Sie eine SELECT-Aktion (z. b. Air-Tap oder den Voice-Befehl "Select"), eine geringfügige Unterbrechung im Spielobjekt. 
    ![Lesson5 Chapter3 Step5](images/Lesson5Chapter3Step5.JPG)
6. Vergewissern Sie sich vor der Erstellung in HoloLens 2, dass die Eyetracking-Funktionen ordnungsgemäß konfiguriert sind. Zum Zeitpunkt der Erstellung dieses Artikels ist Unity noch nicht in der Lage, die Blick Eingabe für die Augen Verfolgungs Funktionen festzulegen. Diese Funktion ist erforderlich, damit die Eye-Nachverfolgung in hololens 2 funktioniert. Befolgen Sie diese Anweisungen in der Dokumentation zum Mixed Reality-Toolkit, um die Eingabe per Anvisieren zu aktivieren: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2 


## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben der Anwendung erfolgreich grundlegende Funktionen zur Augen Verfolgung hinzugefügt. Diese Aktionen stellen nur den Einstieg in eine ganze Welt der Möglichkeiten mit Eyetracking dar. In diesem Kapitel wird außerdem Lektion 5 beendet, in dem wir mehr über erweiterte Eingabefunktionen erfahren, wie z. b. Sprachbefehle, Schwenkbewegungen und die Eye-Nachverfolgung. 

[Nächste Lektion: 7. Erstellen einer Beispielanwendung für ein Mond Modul](mrlearning-base-ch6.md)

