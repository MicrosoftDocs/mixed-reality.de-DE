---
title: MR-Basislernmodul – erweiterte Eingabe
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 32141aafd43c5d729919673509c93bb2014edd37
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719898"
---
# <a name="mr-learning-base-module---advanced-input"></a>MR-Basislernmodul – erweiterte Eingabe

In dieser Lektion werden verschiedene erweiterte Eingabeoptionen für HoloLens 2 vorgestellt, z.B. Sprachbefehle, Schwenkgeste und Eyetracking. 

## <a name="objectives"></a>Ziele

- Sie erfahren, wie Sie Ereignisse mit Sprachbefehlen und Schlüsselwörtern auslösen.
- Sie verwenden Handtracking, um Strukturen und 3D-Objekte zu schwenken.
- Sie verwenden die HoloLens 2-Eyetracking-Funktion, um Objekte auszuwählen.

## <a name="instructions"></a>Anweisungen

### <a name="enabling-voice-commands"></a>Aktivieren der Sprachbefehle

In diesem Abschnitt werden zwei Sprachbefehle implementiert. Erstens wird es ermöglicht, durch Sprechen des Befehls „toggle diagnostics“ (Diagnose umschalten) den Bereich für die Bildfrequenzanalyse umzuschalten. Zweitens kann über einen Sprachbefehl ein Sound wiedergegeben werden. Zunächst betrachten wir die MRTK-Profile und -Einstellungen, mit denen Sprachbefehle konfiguriert werden. 

1. Wählen Sie in der Basisszenen-Hierarchie die Option „MixedRealityToolkit“ aus. Scrollen Sie im Inspektorbereich nach unten zu den Eingabesystemeinstellungen. Doppelklicken Sie, um das Eingabesystemprofil zu öffnen. Klonen Sie das Eingabesystemprofil, sodass es bearbeitet werden kann (siehe Beschreibung in [Lektion 1](mrlearning-base-ch1.md)). 

Im Eingabesystemprofil ist eine breite Palette von Einstellungen enthalten. Sprachbefehle finden sich unten unter „Speech Command Settings“ (Einstellungen für Sprachbefehle). 

![Lesson5 Chapter1 Step2im](images/Lesson5_Chapter1_step2im.PNG)

2. Klonen Sie das Sprachbefehle-Profil, sodass es bearbeitet werden kann (siehe Beschreibung in [Lektion 1](mrlearning-base-ch1.md)). Doppelklicken Sie auf das Sprachbefehle-Profil. Dieses enthält eine Vielzahl von Einstellungen. Eine komplette Beschreibung dieser Einstellungen finden Sie in der [MRTK-Dokumentation zur Spracherkennung](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>). 

>Hinweis: In der Standardeinstellung ist das allgemeine Verhalten auf Autostart festgelegt. Dieses Verhalten kann ggf. in manuelles Starten geändert werden, für dieses Beispiel wird jedoch die Autostart-Einstellung beibehalten. MRTK bietet eine Reihe von Standardsprachbefehlen wie „menu“ (Menü), „toggle diagnostics“ (Diagnose umschalten) und „toggle profiler“ (Profiler umschalten). Wir verwenden das Schlüsselwort „toggle diagnostics“ (Diagnose umschalten), um den Zähler für die Diagnosebildfrequenz ein- und auszuschalten. Außerdem wird in den folgenden Schritten ein neuer Sprachbefehl hinzugefügt.
>
> ![Lesson5 Chapter1 Noteim](images/Lesson5_chapter1_noteim.PNG)

3. Fügen Sie einen neuen Sprachbefehl hinzu. Klicken Sie zum Hinzufügen eines neuen Sprachbefehls auf die Schaltfläche „+ add a new speech command“ (+ Neuen Sprachbefehl hinzufügen). Unter der Liste der vorhandenen Sprachbefehle wird eine neue Zeile angezeigt. Geben Sie den gewünschten Sprachbefehl ein. In diesem Beispiel verwenden wir den Befehl „play music“ (Musik wiedergeben).

>Tipp: Sie können auch einen Tastencode für Sprachbefehle festlegen. Damit können Sprachbefehle durch Drücken einer Taste auf der Tastatur ausgelöst werden.   

4. Fügen Sie die Möglichkeit hinzu, auf Sprachbefehle zu reagieren. Wählen Sie ein beliebiges Objekt in der Basisszenen-Hierarchie aus, an das keine anderen Eingabeskripts angefügt sind (d.h., es weist keinen Manipulationshandler auf). Klicken Sie im Inspektorbereich auf „Add Component“ (Komponente hinzufügen). Geben Sie „speech input handler“ (Spracheingabe-Handler) ein. Wählen Sie die Eingabe aus.
   ![Lesson5 Chapter1 Step4im](images/Lesson5_chapter1_step4im.PNG)

   

In der Standardeinstellung werden zwei Kontrollkästchen angezeigt. Eines davon ist das Kontrollkästchen „is focus required“ (Fokus erforderlich). Dies bedeutet Folgendes: Sobald Sie das Objekt anvisieren (Anvisieren mit den Augen, mit dem Kopf, dem Controller oder der Hand), wird der Sprachbefehl ausgelöst. Deaktivieren Sie dieses Kontrollkästchen, um festzulegen, dass der Benutzer nicht auf das Objekt blicken muss, um den Sprachbefehl zu verwenden.

5. Fügen Sie die Möglichkeit hinzu, auf einen Sprachbefehl zu reagieren. Klicken Sie dazu auf die Schaltfläche „+“ im Spracheingabe-Handler, und wählen Sie das Schlüsselwort aus, auf das Sie reagieren möchten.

   > Hinweis: Diese Schlüsselwörter werden gemäß dem Profil übernommen, das Sie im vorherigen Schritt bearbeitet haben.

![Lesson5 Chapter1 Step5im](images/Lesson5_chapter1_step5im.PNG)

6. Neben „Keyword“ (Schlüsselwort) wird ein Dropdownmenü angezeigt. Wählen Sie „Toggle Diagnostics“ (Diagnose umschalten) aus. Dies bewirkt, dass jedes Mal, wenn der Benutzer nun die Worte „toggle diagnostics“ (Diagnose umschalten) sagt, eine Aktion ausgelöst wird. Beachten Sie, dass Sie möglicherweise „element 0“ erweitern müssen, indem Sie den zugehörigen Pfeil drücken.

![Lesson5 Chapter1 Step6im](images/Lesson5_chapter1_step6im.PNG)

7. Fügen Sie das „diagnostics demo control script“ (Diagnose-Demosteuerungsskript) hinzu, um die Bildfrequenz-Zählerdiagnose ein- und auszuschalten. Drücken Sie dazu die Schaltfläche „add component“ (Komponente hinzufügen), suchen Sie nach „diagnostics demo control script“ (Diagnose-Demosteuerungsskript), und fügen Sie es aus dem Menü hinzu. Dieses Skript kann einem beliebigen Objekt hinzugefügt werden. Zur Vereinfachung fügen wir es jedoch demselben Objekt hinzu, dem auch der Spracheingabe-Handler hinzugefügt wurde. 

   > Hinweis: Dieses Skript ist ausschließlich in diesen Modulen und nicht im ursprünglichen MRTK enthalten.

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step7im.PNG)

8. Fügen Sie im Spracheingabe-Handler eine neue Antwort hinzu. Klicken Sie dazu auf die Schaltfläche „+“ unter „response ()“ (Antwort()). Diese ist in der Abbildung oben durch einen grünen Pfeil gekennzeichnet.

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step8.PNG)

9. Ziehen Sie das Objekt mit dem „diagnostics demo control script“ (Diagnose-Demosteuerungsskript) zur neuen Antwort, die Sie soeben in Schritt 8 erstellt haben.
    ![Lesson5 Chapter1 Step9im](images/Lesson5_chapter1_step9im.PNG)

10. Wählen Sie nun die Dropdownliste „no function“ (keine Funktion) aus, wählen Sie Diagnose-Demosteuerelemente und anschließend „on toggle diagnostics ()“ (bei Umschalten der Diagnose()) aus. Durch diese Funktion wird die Diagnose aktiviert und deaktiviert.  ![Lesson5 Chapter1 Step10im](images/Lesson5_chapter1_step10im.PNG)
    
> Beachten Sie, dass Sie vor dem Erstellen auf Ihrem Gerät Mikrofoneinstellungen aktivieren müssen. Klicken Sie hierzu auf eine Datei, wählen Sie „Build Settings“ (Erstellungseinstellungen) und anschließend „Player Settings“ (Player-Einstellungen) aus, und vergewissern Sie sich, dass die Mikrofonfunktion festgelegt ist.

Nun fügen wir die Möglichkeit hinzu, eine Audiodatei über einen Sprachbefehl mithilfe des Oktaeder-Objekts wiederzugeben. In [Lektion 4](mrlearning-base-ch4.md) haben wir die Möglichkeit hinzugefügt, einen Audioclip durch Berühren des Oktaeder-Objekts wiederzugeben. Diese Audioquelle verwenden wir nun auch für unseren Musik-Sprachbefehl.

11. Wählen Sie das Oktaeder-Objekt in der Basisszenen-Hierarchie aus.

12. Fügen Sie einen weiteren Spracheingabe-Handler hinzu (wiederholen Sie die Schritte 4 und 5), jedoch mit dem Oktaeder-Objekt. 

13. Anstatt den Sprachbefehl „Toggle Diagnostics“ (Diagnose umschalten) wie in Schritt 6 hinzuzufügen, fügen Sie nun wie in der Abbildung unten den Sprachbefehl „play music“ (Musik wiedergeben) hinzu.
    
     ![Lesson5 Chapter1 Step13im](images/Lesson5_chapter1_step13im.PNG)
    
    
    
14. Fügen Sie wie in den Schritten 8 und 9 eine neue Antwort hinzu, und ziehen Sie das Oktaeder-Objekt in den leeren Slot für die Antwort.

15. Wählen Sie im Dropdownmenü „No Function“ (Keine Funktion) die Option „Audio Source“ (Audioquelle) und anschließend die Option „PlayOneShot (AudioClip)“ aus.

![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. Wir verwenden für dieses Beispiel denselben Audioclip wie in [Lektion 4](mrlearning-base-ch4.md). Wechseln Sie in Ihren Projektbereich, suchen Sie nach dem Audioclip „MRTK_Gem“, und ziehen Sie ihn in den Audioquellen-Slot, wie in der Abbildung unten dargestellt. Nun ist Ihre Anwendung in der Lage, auf den Sprachbefehl „toggle diagnostics“ (Diagnose umschalten) zu reagieren, um den Bereich mit dem Bildfrequenzzähler umzuschalten, sowie auf den Sprachbefehl „play music“ (Musik wiedergeben), um den Titel „MRTK_Gem“ wiederzugeben.
     ![Lesson5 Chapter1 Step16im](images/Lesson5_chapter1_step16im.PNG)


### <a name="the-pan-gesture"></a>Die Geste „Schwenken“ 

In diesem Kapitel wird die Verwendung der Geste „Schwenken“ erläutert. Sie ist hilfreich, um zu scrollen (mit dem Finger oder der Hand, um Inhalte zu durchsuchen). Sie können mit der Geste „Schwenken“ auch Objekte drehen, eine Sammlung von 3D-Objekten durchlaufen und sogar durch eine 2D-Benutzeroberfläche scrollen. Sie erfahren, wie Sie mithilfe der Geste „Schwenken“ eine Struktur verzerren. Darüber hinaus wird erläutert, wie eine Sammlung von 3D-Objekten verschoben wird.

1. Erstellen Sie einen Quader. Klicken Sie in der Basisszenen-Hierarchie mit der rechten Maustaste, wählen Sie „3D Object“ (3D-Objekt) und anschließend „Quad“ (Quader) aus.

![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. Ändern Sie ggf. die Position des Quaders. In unserem Beispiel legen wir die Werte x = 0, y = 0 und z = 1,5 von der Kamera aus fest, um die gewünschte Position in Bezug auf HoloLens 2 zu erhalten.

   > Hinweis: Wenn der Quader Inhalte aus früheren Lektionen verdeckt (vor diesen liegt), verschieben Sie ihn so, dass keine anderen Objekte verdeckt werden.

3. Weisen Sie dem Quader ein Material zu. Dieses Material durchsuchen wir mit der Geste „Schwenken“. 

![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. Geben Sie im Projektbereich im Suchfeld „pan content“ (Inhalt schwenken) ein. Ziehen Sie das Material auf den Quader in der Szene. 

> Hinweis: Das Material „Pan content“ (Inhalt schwenken) ist in MRTK nicht enthalten, es ist jedoch eine Ressource aus dem Ressourcenpaket für dieses Modul, das in früheren Lektionen importiert wurde. 

> Hinweis: Der importierte geschwenkte Inhalt kann gestreckt aussehen. Sie können dieses Problem heben, indem Sie die Werte x, y und z für die Abmessungen des Quaders anpassen, bis Sie mit dem Erscheinungsbild zufrieden sind.

Zum Verwenden der Geste „Schwenken“ benötigen Sie ein Collider für das Objekt. Sie stellen möglicherweise fest, dass der Quader bereits ein Gitter-Collider aufweist. Das Gitter-Collider ist jedoch nicht ideal, da es äußerst schmal und daher schwer auszuwählen ist. Es empfiehlt sich, das Gitter-Collider durch ein Feld-Collider zu ersetzen.

5. Klicken Sie mit der rechten Maustaste auf das Gitter-Collider auf dem Quader (im Inspektorbereich), und entfernen Sie es, indem Sie auf „Remove Component“ (Komponente entfernen) klicken. 
   ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. Fügen Sie nun das Feld-Collider hinzu, indem Sie auf „Add Component“ (Komponente hinzufügen) klicken und nach „Box Collider“ (Feld-Collider) suchen. Der standardmäßig hinzugefügte Feld-Collider ist immer noch zu schmal. Klicken Sie deshalb auf „Edit Collider“, um es zu bearbeiten. Im ausgewählten Zustand können Sie seine Größe über die x, y und z oder mithilfe der Elemente im Szenen-Editor anpassen. In diesem Beispiel soll das Feld-Collider hinter dem Quader etwas verlängert werden. Ziehen Sie im Szenen-Editor das Feld-Collider aus dem Hintergrund nach außen (siehe Abbildung unten). Dadurch kann der Benutzer nicht nur mit dem Finger, sondern mit der ganzen Hand scrollen. 
    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)
7. Machen Sie das Objekt interaktiv. Da eine direkte Interaktion mit dem Quader gewünscht wird, möchten wir die Komponente „near interaction touchable“ (Nah-Interaktion, berührbar) verwenden (diese wurde bereits in Lektion 4 für die Wiedergabe von Musik aus dem Oktaeder-Objekt verwendet). Klicken Sie auf „add component“ (Komponente hinzufügen), suchen Sie nach „near interaction touchable“ (Nah-Interaktion, berührbar), und wählen Sie die Komponente aus, wie in den Abbildungen unten dargestellt. 

8. Fügen Sie die Fähigkeit zum Erkennen der Geste „Schwenken“ hinzu. Klicken Sie auf „add component“ (Komponente hinzufügen), und geben Sie „hand interaction pan“ (Handinteraktion Schwenken) ein. Sie haben die Auswahl zwischen „Hand Ray“ (Ganze Hand) (wodurch Sie aus der Entfernung schwenken können) und „Index Finger“ (Zeigefinger). In diesem Beispiel behalten wir die Einstellung „Index Finger“ (Zeigefinger) bei. 
    ![Lesson5 Chapter2 Step7 8Im](images/Lesson5_chapter2_step7-8im.PNG)

![Lesson5 Chapter2 Step8im](images/Lesson5_chapter2_step8im.PNG)

9. Im Skript „Hand Interaction Pan“ werden mit den Kontrollkästchen „Lock Horizontal“ (Horizontal sperren) und „Lock Vertical“ (Vertikal sperren) die Bewegungen gesperrt. Mit den Einstellungen unter „Wrap Texture“ (Textur verzerren) wird festgelegt, dass die Textur (Texturzuordnung) den Schwenkbewegungen des Benutzers folgt. In diesem Beispiel aktivieren wir das Kontrollkästchen. Zudem gibt es die Option „Velocity Active“ (Geschwindigkeit aktiv). Ist diese nicht aktiviert, funktioniert die Geste „Schwenken“ nicht. Aktivieren Sie auch dieses Kontrollkästchen. Nun verfügen Sie über einen Quader, der durch Schwenken gesteuert werden kann.

   

   Nun erfahren Sie, wie Sie 3D-Objekte schwenken. 

10. Klicken Sie mit der rechten Maustaste auf das Quader-Objekt, wählen Sie „3D Object“ (3D-Objekt) aus, und klicken Sie anschließend auf „Cube“ (Würfel). Skalieren Sie den Würfel etwa auf die Abmessungen x = 0,1, y = 0,1 und z = 0,1. Kopieren Sie den Würfel dreimal. Klicken Sie dazu mit der rechten Maustaste auf den Würfel, und wählen Sie „Duplicate“ (Duplizieren) aus, oder drücken Sie STRG/BEFEHL+D. Ordnen Sie die Würfel mit gleichmäßigen Abständen an. Die Szene sollte der folgenden Abbildung ähneln.

![Lesson5 Chapter2 Step10im](images/Lesson5_chapter2_step10im.PNG)







11. Wählen Sie erneut den Quader aus. Unter dem Skript „Hand Interaction Pan“ sollen nun die Schwenken-Aktionen für die einzelnen Würfel festgelegt werden. Unter „Pan Event Receivers“ (Empfänger Schwenken-Ereignis) geben wir nun die Anzahl der Objekte an, die das Ereignis empfangen. Da vier Würfel vorhanden sind, geben Sie „4“ ein, und drücken Sie die EINGABETASTE. Vier leere Felder werden angezeigt.


![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)



12. Ziehen Sie die einzelnen Würfel in die leeren Element-Slots.
     ![Lesson5 Chapter2 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. Fügen Sie allen Würfeln das Skript „Move With Pan“ (Verschieben mit Schwenken) hinzu. Halten Sie dazu STRG/BEFEHL gedrückt, und wählen Sie die einzelnen Objekte aus. Klicken Sie anschließend im Inspektorbereich auf „Add Component“ (Komponente hinzufügen), und suchen Sie nach „Move With Pan“ (Verschieben mit Schwenken). Klicken Sie auf das Skript, und es wird den einzelnen Würfeln hinzugefügt. Die 3D-Objekte werden nun per Geste „Schwenken“ verschoben. Wenn Sie das Gitter-Rendering um den Quader entfernen, verfügen Sie über einen unsichtbaren Quader, mit dem Sie durch eine Liste von 3D-Objekten schwenken können.

### <a name="eye-tracking"></a>Eyetracking

In diesem Kapitel wird erläutert, wie Sie das Eyetracking in der Demo aktivieren. Die 3D-Menüelemente werden langsam gedreht, wenn Sie per Blick anvisiert werden. Zudem wird ein unterhaltsamer Effekt ausgelöst, wenn das anvisierte Element ausgewählt wird.

1. Stellen Sie sicher, dass die Profile im Mixed Reality-Toolkit ordnungsgemäß konfiguriert sind. Zum Zeitpunkt der Veröffentlichung dieses Dokuments sind in der Konfiguration der Profile im Mixed Reality-Toolkit Eyetracking-Funktionen standardmäßig nicht enthalten. Befolgen Sie zum Hinzufügen von Eyetracking-Funktionen die Anweisungen im Abschnitt „Setting up the MRTK profiles required for Eye Tracking“ (Einrichten der erforderlichen MRTK-Profile für Eyetracking) in der [Dokumentation zum Mixed Reality-Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-the-mrtk-profiles-required-for-eye-tracking  ). Stellen Sie sicher, dass Eyetracking ordnungsgemäß konfiguriert ist. Führen Sie dazu alle verbleibenden Schritte unter dem obigen Link zur Dokumentation aus, u. a. das Aktivieren des Eyetracking in GazeProvider (an Kamera angefügte Komponente) und das Aktivieren der Eyetracking-Simulation im Unity-Editor. Beachten Sie, dass künftige MRTK-Versionen Eyetracking standardmäßig enthalten können.

    Unter dem obigen Link erhalten Sie kurze Anleitungen für folgende Aufgaben:

    - Erstellen des zu verwendenden Eye Gaze-Datenanbieters im MRTK-Profil
    - Aktivieren des Eyetracking im Gaze-Anbieter
    - Einrichtung für das Simulieren von Eyetracking im Editor
    - Bearbeiten der Funktionen der Visual Studio-Lösung, mit denen Eyetracking in der erstellten Anwendung zugelassen wird

2. Fügen Sie die EyeTrackingTarget-Komponente Zielobjekten hinzu. Um einem Objekt das Reagieren auf Anvisier-Ereignisse zu ermöglichen, müssen wir die EyeTrackingTarget-Komponente für jedes Objekt hinzufügen, mit dem über Anvisieren kommuniziert werden soll. Fügen Sie diese Komponente jedem der neun 3D-Objekte hinzu, die zur Rastersammlung gehören. Tipp: Wählen Sie mehrere Elemente in der Hierarchie aus, um die EyeTrackingTarget-Komponente in einem Massenvorgang hinzuzufügen.
    ![Lesson5 Chapter3 Step2](images/Lesson5Chapter3Step2.JPG)

3. Nun fügen wir das Skript EyeTrackingTutorialDemo für einige interessante Interaktionen hinzu. Das Skript EyeTrackingTutorialDemo ist im Repository für diese Reihe von Tutorials enthalten, jedoch nicht standardmäßig im Mixed Reality-Toolkit. Fügen Sie das Skript EyeTrackingTutorialDemo für jedes 3D-Objekt in der Rastersammlung hinzu, indem Sie im Menü „Add Component“ (Komponente hinzufügen) nach der Komponente suchen.
   ![Lesson5 Chapter3 Step3](images/Lesson5Chapter3Step3.JPG)

   4. Drehen Sie das Objekt, während Sie das Ziel anvisieren. Das 3D-Objekt soll gedreht werden, während es anvisiert wird. Fügen Sie dazu ein neues Feld im Abschnitt „While Looking At Target“ (Bei Anvisieren des Ziels) der EyeTrackingTarget-Komponente hinzu. Dies wird in der Abbildung unten dargestellt. 

![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)
![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)



Fügen Sie im neu erstellten Feld das aktuelle Game-Objekt dem leeren Feld hinzu, und wählen Sie wie in der Abbildung unten „EyeTrackingTutorialDemo“ > „RotateTarget()“ aus. Nun ist das 3D-Objekt so konfiguriert, dass es bei Anvisieren per Eyetracking gedreht wird. 

5. Fügen Sie die Fähigkeit hinzu, das anvisierte Ziel leuchtend zu markieren, wenn es ausgewählt wird (per Tippbewegung in die Luft oder Sprachbefehl „Select“ (Auswählen)). Ähnlich wie in Schritt 4 soll „EyeTrackingTutorialDemo“ > „BlipTarget()“ ausgelöst werden, indem es dem Feld „Select()“ des Game-Objekts der EyeTrackingTarget-Komponente zugewiesen wird. Dies wird in der Abbildung unten dargestellt. Nachdem Sie dies festgelegt haben, stellen Sie ein leichtes Aufleuchten des Game-Objekts fest, wenn eine Auswahlaktion ausgelöst wird, z.B. per Tippbewegung in die Luft oder Sprachbefehl „Select“ (Auswählen). 
    ![Lesson5 Chapter3 Step5](images/Lesson5Chapter3Step5.JPG)
6. Vergewissern Sie sich vor der Erstellung in HoloLens 2, dass die Eyetracking-Funktionen ordnungsgemäß konfiguriert sind. Zum Zeitpunkt der Veröffentlichung dieses Artikels bietet Unity noch nicht die Funktion zum Festlegen der Eingabe per Anvisieren (für Eyetracking). Das Festlegen dieser Funktion ist erforderlich, damit Eyetracking in HoloLens 2 funktioniert. Befolgen Sie diese Anweisungen in der Dokumentation zum Mixed Reality-Toolkit, um die Eingabe per Anvisieren zu aktivieren: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2 


### <a name="congratulations"></a>Gratulation! 
Sie haben der Anwendung erfolgreich grundlegende Eyetracking-Funktionen hinzugefügt. Diese Aktionen stellen nur den Einstieg in eine ganze Welt der Möglichkeiten mit Eyetracking dar. Mit diesem Kapitel wird zudem Lektion 5 abgeschlossen, in dem Sie etwas über erweiterte Eingabefunktionen erfahren haben, z.B. Sprachbefehle, Gesten vom Typ „Schwenken“ und Eyetracking. 

[Nächste Lektion: Beispielerfahrung für Lunar-Modulassembly](mrlearning-base-ch6.md)

