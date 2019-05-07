---
title: MR-Learning-Basis-Modul – Erweiterte Eingabe
description: Führen Sie diesen Kurs erfahren, wie Sie Azure-Gesichtserkennung innerhalb einer mixed Reality-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Gemischte Realität, Unity, Tutorial, hololens
ms.openlocfilehash: c28b607e3532a7c964ab74fdb7a7d514c9293579
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929578"
---
# <a name="mr-learning-base-module---advanced-input"></a>MR-Learning-Basis-Modul – Erweiterte Eingabe

In dieser Lektion werden wir einige erweiterte Eingabeoptionen für HoloLens 2, einschließlich der Verwendung von Sprachbefehlen, schwenkansicht Geste und Eye-tracking untersuchen. 

## <a name="objectives"></a>Ziele

- Erfahren Sie, wie zum Auslösen von Ereignissen mithilfe von Sprachbefehlen und Schlüsselwörter
- Verwenden Sie überwachte Hände, um Texturen und 3D-Objekte zu schwenken
- Nutzen Sie die HoloLens-2-Eye-tracking-Funktionen, um die Objekte auswählen

## <a name="instructions"></a>Anweisungen

### <a name="enabling-voice-commands"></a>Aktivieren Sprachbefehle

In diesem Abschnitt implementieren wir zwei Sprachbefehle. Erstens die Möglichkeit, die den Frame Rate-Diagnose-Bereich zu wechseln, indem Sie sagen "ein/aus-Diagnose". Sekunde, die Möglichkeit zum Abspielen eines Sounds mit einem Voice-Befehl. Wir untersuchen zunächst die MRTK Profile und Einstellungen, die für das Konfigurieren von Sprachbefehlen zuständig. 

1. Wählen Sie in die Basis-szenenhierarchie "MixedRealityToolkit." Scrollen Sie im Bereich mit den Inspektor die Systemeinstellungen für die Eingabe aus. Doppelklicken Sie zum Einrichten des Profils Eingabesystem zu öffnen. Klonen Sie das Eingabesystem Profil bearbeitbar machen, haben wir gelernt in [Lektion 1](mrlearning-base-ch1.md) 

In der Eingabe-Profil wird eine Reihe von Einstellungen angezeigt. Sprachbefehle finden Sie unten auf, in dem Name schon sagt, "Speech-Befehl-Einstellungen". 

![Lesson5 Chapter1 Step2im](images/Lesson5_Chapter1_step2im.PNG)

2. Klonen Sie die Befehle Sprachprofil um bearbeitbar machen, haben wir gelernt in [Lektion 1](mrlearning-base-ch1.md). Doppelklicken Sie auf den Befehl Sprachprofil, in dem Sie eine Vielzahl von Einstellungen sehen. Eine vollständige Beschreibung zu diesen Einstellungen finden Sie unter den [MRTK Spracherkennung Dokumentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>). 

>Hinweis: Standardmäßig ist das allgemeine Verhalten automatisch gestartet. Die manuell gestartet werden, bei Bedarf geändert werden kann, aber in diesem Beispiel werden wir ihn auf automatischen Start zu halten. Die MRTK enthält mehrere Voice-Standardbefehle (z. B. Menüs, ein/aus-Diagnose und ein/aus-Profiler). Wir verwenden das Schlüsselwort "Diagnose aktivieren/deaktivieren" zum Aktivieren und Deaktivieren der Diagnose Framerate Zähler. In den folgenden Schritten fügen wir auch einen neuen Voice-Befehl.
>
> ![Lesson5 Chapter1 Noteim](images/Lesson5_chapter1_noteim.PNG)

3. Fügen Sie einen neuen Voice-Befehl. Um einen neuen Voice-Befehl hinzuzufügen, klicken Sie auf die Schaltfläche "+ einen neuen Speech-Befehl hinzufügen", und sehen Sie eine neue Zeile, die Sie unterhalb der Liste der vorhandenen Sprachbefehle angezeigt wird. Geben Sie in der Voice-Befehl, die, den Sie verwenden möchten. In diesem Beispiel Musicample werden wir verwenden Sie den Befehl "Musik wiedergeben".

>Tipp: Sie können auch eine Tastencode für gesprochene Befehle festlegen. Dies ermöglicht Sprachbefehle zum Auslösen nach Drücken der Taste.   

4. Fügen Sie die Möglichkeit, um Sprachbefehle zu reagieren. Wählen Sie ein Objekt in der Basis szenenhierarchie, die keine anderen eingabeskripts angefügt ist (z. B. keine Manipulation-Handler.) Klicken Sie im Bereich mit den Inspektor auf "Komponente hinzufügen" aus. Geben Sie in "Speech eingabehandler." Wählen Sie ihn aus.
   ![Lesson5 Chapter1 Step4im](images/Lesson5_chapter1_step4im.PNG)

   

Standardmäßig 2 Kontrollkästchen wird angezeigt, eine ist das Kontrollkästchen "den Fokus erforderlich ist". Dies bedeutet, solange Sie das Objekt mit einer Blicke-Ray (Eye-Blicke, Head-Blicke, Controller-Blicke oder Hand-Blicke) zeigen der Voice-Befehl ausgelöst werden soll. Deaktivieren Sie dieses Kontrollkästchen, um ihn zu machen, damit der Benutzer nicht verfügt, betrachten Sie das Objekt, das den Voice-Befehl verwenden.

5. Fügen Sie die Möglichkeit, um einen Sprachbefehl reagieren. Zu diesem Zweck klicken Sie auf "+", die in der eingabehandler Sprache ist, und wählen Sie das Schlüsselwort, die, dem Sie beantworten möchten.

   > Hinweis: Diese Schlüsselwörter werden basierend auf das Profil, das Sie im vorherigen Schritt bearbeitet aufgefüllt.

![Lesson5 Chapter1 Step5im](images/Lesson5_chapter1_step5im.PNG)

6. Neben "Schlüsselwort" wird ein Dropdownmenü angezeigt. Wählen Sie "Umschalten von Diagnose". Dadurch wird es, sodass, wenn der Benutzer die Spalte "Umschalten von Diagnose" sagt eine Aktion ausgelöst wird. Beachten Sie, dass Sie möglicherweise "Element 0" zu erweitern, indem Sie mit der Taste daneben.

![Lesson5 Chapter1 Step6im](images/Lesson5_chapter1_step6im.PNG)

7. Fügen Sie das "Diagnostics-Demo-steuerskript" auf die Bildrate Leistungsindikator Diagnose wechseln, ein- und ausschalten. Zu diesem Zweck drücken Sie die Schaltfläche "Komponente hinzufügen" und suchen Sie nach "Demo-steuerskript Diagnose", und fügen Sie es aus dem Menü hinzu. Dieses Skript kann jedes beliebige Objekt hinzugefügt werden, aber wir werden es der Einfachheit halber auf dasselbe Objekt wie der eingabehandler Sprache hinzufügen. 

   > Hinweis: Dieses Skript ist nur mit den folgenden Modulen enthalten und nicht mit der ursprünglichen MRTK enthalten ist.

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step7im.PNG)

8. Fügen Sie eine neue Antwort in der Sprache-Eingabe-Handler hinzu. Klicken Sie hierzu auf die Schaltfläche "+" unterhalb der, in denen dieser sagt "Antwort ()" (gekennzeichnet durch den grünen Pfeil in der obigen Abbildung).

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step8.PNG)

9. Ziehen Sie das Objekt, das Skript-Diagnose-Demo-Steuerelemente für die neue Antwort hat, die Sie gerade erstellt, in Schritt 8 haben.
    ![Lesson5 Chapter1 Step9im](images/Lesson5_chapter1_step9im.PNG)

10. Nun wählen Sie die Dropdownliste "keine Funktion" Diagnose Demo-Steuerelemente und dann "Umschalten von auf Diagnose ()". Diese Funktion wird die Diagnose aktiviert und deaktiviert.  ![Lesson5 Chapter1 Step10im](images/Lesson5_chapter1_step10im.PNG)
    
> Beachten Sie, dass vor der Erstellung auf Ihrem Gerät Sie mic-Einstellungen zu aktivieren müssen. Dazu klicken Sie auf die Datei, wechseln Sie zum Erstellen von Einstellungen, dort playereinstellungen, und stellen Sie sicher, dass die Funktion "Mikrofon" festgelegt ist.

Als Nächstes werden wir die Möglichkeit, die Wiedergabe einer Audiodatei aus Voice-Befehl unter Verwendung des Objekts "Octa" hinzufügen. Erinnern Sie sich an [Lektion 4](mrlearning-base-ch4.md), wir haben die Möglichkeit, einen Audioclip zu berühren des Objekts Octa wiederzugeben hinzugefügt. Diese gleichen Audioquelle nutzen wir für unsere Musik-Voice-Befehl.

11. Wählen Sie das Octa-Objekt, in der szenenhierarchie der Basis der.

12. Hinzufügen einer anderen Sprache eingabehandler (Wiederholen Sie die Schritte 4 und 5), jedoch mit dem Octa-Objekt. 

13. Anstatt zum Hinzufügen des "Ein-/Ausschalten der Diagnose" Voice-Befehls aus Schritt 6, fügen Sie den Befehl "Musik wiedergeben" Stimme hinzu, wie in der folgenden Abbildung dargestellt.
    
     ![Lesson5 Chapter1 Step13im](images/Lesson5_chapter1_step13im.PNG)
    
    
    
14. Wie bei den Schritten 8 und 9, fügen Sie eine neue Antwort hinzu, und ziehen Sie die Octa in das leere Einschubfach aus Antwort.

15. Wählen Sie im Dropdownmenü die Fehlermeldung "keine Funktion," select "Audio Source", und wählen "PlayOneShot (AudioClip)."

![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. Für den Audioclip, in diesem Beispiel werden wir verwenden die gleiche Audioclip aus [Lektion 4](mrlearning-base-ch4.md). Wechseln Sie in Ihrem Projektfenster, suchen Sie nach "MRTK_Gem" Audioclip, und ziehen Sie es in das Einschubfach Audioquelle wie in der folgenden Abbildung dargestellt. Jetzt Ihre Anwendung auf die Stimmbefehle "Diagnose aktivieren/deaktivieren" reagieren sollten Sie "Musik wiedergeben" und wechseln im Frame Rate Leistungsindikator-Bereich zur Wiedergabe der MRTK_Gem "Song".
     ![Lesson5 Chapter1 Step16im](images/Lesson5_chapter1_step16im.PNG)


### <a name="the-pan-gesture"></a>Die Geste Schwenken 

In diesem Kapitel lernen wir, wie Sie die Pan-Geste mit. Dies ist nützlich für das Durchführen eines Bildlaufs (mit Ihrem Finger oder manuell einen Bildlauf durch den Inhalt.) Sie können auch die Pan-Aktion verwenden, zum Drehen von Objekten, um eine Auflistung von 3D-Objekten oder sogar Scroll einer 2D-Texturmap. Benutzeroberfläche zu durchlaufen. Es wird auf die Bewegung Pan zu verwenden, um eine Textur warp kennen zu lernen werden. Gewusst wie: Verschieben einer Auflistung von 3D-Objekten wird außerdem untersucht.

1. Erstellen Sie ein Quad. In Ihrer szenenhierarchie Basis mit der rechten Maustaste, wählen Sie "3D Object", und wählen Sie dann "Quad".

![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. Verschieben Sie die Quad nach Bedarf. In unserem Beispiel legen wir fest, das "X" = 0, y = 0 "und" Z = 1.5 Weg von der Kamera für einer komfortablen Position aus der HoloLens-2.

   > Hinweis: Wenn die vier Blöcke (ist der infront) alle Inhalte der vorangegangenen Lektionen, achten Sie darauf, verschieben es, dass er eines der anderen Objekte nicht blockiert.

3. Wenden Sie ein Material auf die Quad an. In diesem Material werden das Material, die, das wir mit dieser Bewegung Pan Durchführen eines Bildlaufs durch sein wird. 

![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. Geben Sie im Bereich mit Ihrer Projekte in das Suchfeld "Pan-Inhalt." Ziehen Sie dieses Materials an die Quad in Ihrer Szene ein. 

> Hinweis: Das Material "Schwenken Inhalte" ist nicht in der MRTK enthalten, aber es ist ein Medienobjekt in Asset-Paket des Moduls, wie in den vorherigen Lektionen importiert. 

> Hinweis: Wenn Sie die Pan-Inhalte hinzufügen, können die gestreckte aussehen. Sie können dies beheben, indem Sie die Werte x, y und Z-Werte der Größe des der Quad anpassen, bis Sie mit der Funktionsweise zufrieden sind, die es aussieht.

Um die Bewegung Pan zu verwenden, benötigen Sie ein "collider" auf das Objekt. Möglicherweise wird angezeigt, dass die Quad bereits ein Mesh "collider" verfügt. Die Mesh-Collider ist jedoch nicht ideal, da es sich um sehr dünne und schwierig zu wählen ist. Es wird empfohlen, das Netz "collider" durch einen Box-Collider ersetzt.

5. Klicken Sie mit der rechten Maustaste auf das Netz "collider", das auf die Quad (im Bereich "Inspector") ist, dann entfernen Sie, indem Sie auf "Komponente entfernen". 
   ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. Jetzt fügen Sie der Box-Collider hinzu, indem Sie durch Klicken auf "Komponente hinzufügen", und suchen die "Feld" collider"." Der Standardwert hinzugefügt, dass es sich bei Box-Collider ist immer noch zu dünn, klicken Sie daher auf die Schaltfläche "Bearbeiten" collider"", um ihn zu bearbeiten. Wenn es gedrückt wird, können Sie die Größe, verwenden die x-, y- und Z-Werte oder die Elemente in der Szene Editor anpassen. In unserem Beispiel möchten wir die Box-Collider ein wenig hinter der Quad erweitern. Ziehen Sie im Editor Szene die Box-Collider, von der Rückseite, aus nach außen (siehe Abbildung unten). Was geschieht, ist der Benutzer nicht nur den Finger, aber die gesamte Seite verwenden Sie einen Bildlauf durchführen kann. 
    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)
7. Machen Sie es interaktiven. Da wir die Quad direkt interagieren möchten, möchten wir die Komponente "in der Nähe der Interaktion touchable" verwenden (wir nutzten auch diese in Lektion 4 für die Wiedergabe von Musik aus dem Octa). Klicken Sie auf "Komponente hinzufügen" und "in der Nähe Interaktion touchable" Suchen Sie und wählen Sie aus, wie in den folgenden Abbildungen dargestellt. 

8. Fügen Sie die Möglichkeit, erkennen die Pan-Aktion hinzu. Klicken Sie auf "Komponente hinzufügen", und geben Sie "Interaktion Pan zu übergeben." Sie haben die Wahl zwischen Hand-Ray (sodass Sie aus der Entfernung schwenken) und Zeigefinger. In diesem Beispiel lassen sie sich am Index Finger. 
    ![Lesson5 Chapter2 Step7 8Im](images/Lesson5_chapter2_step7-8im.PNG)

![Lesson5 Chapter2 Step8im](images/Lesson5_chapter2_step8im.PNG)

9. Im manuellen Interaktion Pan-Skript werden die "Lock horizontale" und "Lock vertikale" Kontrollkästchen Verschiebungen, bzw. gesperrt hat. Die Wrap-Textur-Einstellungen werden die Textur (texturzuordnungen), führen Sie die Pan Bewegungen des Benutzers. In diesem Beispiel werden wir dieses Kontrollkästchen aktivieren. Es gibt auch "Geschwindigkeit aktiv", die bei die Pan-Bewegung nicht funktionieren. Aktivieren Sie dieses Kontrollkästchen auch. Jetzt sollten Sie ein Quad Schwenken aktiviert haben.

   

   Als Nächstes erfahren wir, wie um 3D-Objekte zu schwenken. 

10. Klicken Sie mit der rechten Maustaste auf das Vierfache-Objekt, wählen Sie 3D-Objekt aus, und klicken Sie auf "cube". Skalieren Sie den Cube aus, sodass es ungefähr x ist = 0,1, y = 0,1 und Z = 0,1. Kopieren Sie den Cube 3 Mal (Wenn Sie mit der rechten Maustaste auf den Cube, und drücken doppelte oder durch Drücken von Control/Befehl D). Trennen sie gleichmäßig. Die Szene sollte ähnlich der folgenden Abbildung aussehen.

![Lesson5 Chapter2 Step10im](images/Lesson5_chapter2_step10im.PNG)







11. Wählen Sie die Quad erneut aus, und unter der Hand Interaktion Pan-Skript, möchten wird für die Pan-Aktionen auf die einzelnen Cubes. Unter den "Pan-Ereignisempfänger" möchten wir die Anzahl der Objekte angeben, die das Ereignis empfangen. Da es sich um 4 Cubes, geben Sie Sie vom Typ "4", und drücken Sie. 4 leere Felder sollten angezeigt werden.


![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)



12. Ziehen Sie die Cubes in jeder der die Steckplätze leeres Element.
     ![Lesson5 Chapter2 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. Das Skript "verschieben mit Pan" alle Cubes hinzufügen. Zu diesem Zweck, drücken Sie die halten Sie Steuerbefehl /, und wählen Sie jedes Objekt. Klicken Sie dann, Sie im Bereich mit den Inspektor, klicken Sie auf "Komponente hinzufügen" und suchen Sie nach "PAN verschieben." Klicken Sie auf das Skript, und es wird zu den einzelnen Cubes hinzugefügt. Die 3D-Objekte werden jetzt mit Ihrer Pan-Bewegung verschoben! Wenn Sie entfernen das Netz rendern, in Ihre Quad, Sie verfügen nun über eine unsichtbare Quad, in dem Sie eine Liste von 3D-Objekten Schwenken können.

### <a name="eye-tracking"></a>Eye-Tracking

In diesem Kapitel erforschen wir, wie Eye-Überwachung in der Demo zu aktivieren. Wir werden unsere 3D Menüelemente langsam laufen, nachdem die werden sie bei mit Eye Blicke gazed wird. Es wird auch ausgelöst, ein unterhaltsames wirksam, wenn das gazed nach Element ausgewählt ist.

1. Stellen Sie sicher, dass die Profile Mixed Reality-Toolkit ordnungsgemäß konfiguriert sind. Während ich dies schreibe schließt die mixed Reality-Toolkit-Profilkonfiguration Eye-tracking Funktionen standardmäßig nicht. Um Eye-tracking Funktionen hinzuzufügen, befolgen Sie die Anweisungen im Abschnitt "Einrichten von MRTK Profile für die Augen nachverfolgung erforderlich", wie in der [Mixed Reality-Toolkit-Dokumentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-the-mrtk-profiles-required-for-eye-tracking  ). Stellen Sie sicher, dass diese Eye-tracking ordnungsgemäß konfiguriert ist, indem Sie die folgenden übrigen Schritte in dem Link zur Dokumentation, oben, einschließlich der Aktivierung der Eye-Überwachung in GazeProvider (Komponente, die an Kamera angebracht werden) und aktivieren die Simulation Eye-tracking im Unity-Editor. Beachten Sie, zukünftige Version von der MRTK kann Eye-Tracking standardmäßig enthalten.

    Der Link oben bietet kurze Anweisungen zum:

    - Erstellen die Augen bestaunen-Datenanbieter für die Verwendung im Profil MRTK
    - Aktivieren der Überwachung von Augen im bestaunen-Anbieter
    - Richten Sie zum Simulieren von Eye-tracking im editor
    - Bearbeitungsfunktionen für die Visual Studio-Projektmappe um Eye-Überwachung in der erstellten Anwendung zu ermöglichen.

2. Zielobjekten Eye nachverfolgung Zielkomponente hinzugefügt. Damit um ein Objekt auf Eye Blicke Ereignisse reagieren zu können, müssen wir die EyeTrackingTarget-Komponente für jedes Objekt hinzuzufügen, die wir mit ihm interagieren Eye Blicke möchten. Fügen Sie diese Komponente zu jedem der neun 3D-Objekte, die Teil der Raster-Auflistung hinzu. Tipp: Wählen Sie mehrere Elemente aus, in der Hierarchie, um die Komponente EyeTrackingTarget per Massenvorgang hinzufügen.
    ![Lesson5 Chapter3 Schritt 2](images/Lesson5Chapter3Step2.JPG)

3. Als Nächstes fügen wir das Skript EyeTrackingTutorialDemo für einige interessanten Interaktionen. Das Skript EyeTrackingTutorialDemo ist als Teil dieser tutorialreihe Repository enthalten und nicht standardmäßig mit dem Mixed Reality-Toolkit enthalten ist. Fügen Sie für jede 3D-Objekt in der Raster-Auflistung das Skript EyeTrackingTutorialDemo Überwachungspakete für die Komponente im Menü "Komponente hinzufügen" hinzu.
   ![Lesson5 Chapter3 Schritt 3](images/Lesson5Chapter3Step3.JPG)

   4. Richten Sie das Objekt, bei der Suche im Ziel. Wir möchten unsere 3D-Objekt, starten, während wir sie betrachten konfigurieren. Zu diesem Zweck fügen Sie ein neues Feld im Abschnitt "Während Suchen am Ziel" die EyeTrackingTarget-Komponente, wie in der folgenden Abbildung dargestellt. 

![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)
![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)



Klicken Sie im neu erstellten-Feld, das aktuelle Spiel-Objekt das leere Feld hinzufügen, und wählen Sie EyeTrackingTutorialDemo > RotateTarget() wie in der folgenden Abbildung dargestellt. Jetzt ist das 3D-Objekt starten, wenn es bei mit Eye-Tracking gazed wird konfiguriert. 

5. Hinzugefügt in Fähigkeit "Blip Target", die beim Wählen (tippbewegung oder sagen "select") am gazed werden wird. Ähnlich wie bei Schritt 4, wir EyeTrackingTutorialDemo auslösen möchten > BlipTarget() durch Zuweisen des Objekts, der das Spiel "Select()"-Feld der EyeTrackingTarget-Komponente, wie in der folgenden Abbildung dargestellt. Dies ist nun so konfiguriert fällt eine leichte Blip in das spielobjekt, wenn Sie eine Aktion "auswählen", z. B. tippbewegung oder der Voice-Befehl auslösen "wählen." 
    ![Lesson5 Chapter3 Schritt 5](images/Lesson5Chapter3Step5.JPG)
6. Sicherstellen Sie, dass die Augen Nachverfolgungsfunktionen ordnungsgemäß konfiguriert sind, vor dem Erstellen mit HoloLens 2. Während ich dies schreibe muss Unity nicht noch die Möglichkeit, die Blicke (für Eye-Tracking)-Funktion festzulegen. Festlegen von dieser Funktion ist erforderlich, für die nachverfolgung von Blick auf die HoloLens-2. Gehen Sie auf die mixed Reality-Toolkit-Dokumentation zum Aktivieren der Eingabe Blicke-Funktion: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2 


### <a name="congratulations"></a>Herzlichen Glückwunsch! 
Sie haben die grundlegenden Funktionen für die Anwendung für die nachverfolgung Eye erfolgreich hinzugefügt. Diese Aktionen sind nur der Anfang der unzählige Möglichkeiten mit Eye-tracking. In diesem Kapitel ist auch in Lektion 5, in denen erweiterte Eingabefunktionen wie z. B. Sprachbefehle, schwenken kennengelernt, Gesten und Eye-Tracking abgeschlossen. 

[Nächste Lektion: Mondkalender Modul Assembly-Beispiel-Erfahrung](mrlearning-base-ch6.md)

