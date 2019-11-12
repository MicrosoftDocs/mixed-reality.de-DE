---
title: Tutorials zu den ersten Schritten-7. Erstellen einer Beispielanwendung für ein Mond Modul
description: In dieser Lektion kombinieren Sie mehrere Konzepte, die Sie aus vorherigen Lektionen gelernt haben, um eine einzigartige Stichprobe zu erstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: b033e4f9a379fb1778da3d94da70262e073d141b
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926522"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. Erstellen einer Beispielanwendung für ein Mond Modul

In diesem Tutorial werden mehrere Konzepte aus früheren Lektionen kombiniert, um ein eindeutiges Beispiel zu erstellen. Sie erfahren, wie Sie eine Anwendung für eine Mond Modul Assembly erstellen, bei der ein Benutzer überwachte Hände zum Abrufen von Mond Modul teilen und zum Anfügen eines mondmoduls verwenden muss. Mithilfe von druckbaren Schaltflächen können Sie Platzierungs Hinweise umschalten, die Leistung zurücksetzen und das Mond Modul in den Raum bringen! In zukünftigen Tutorials werden wir weiterhin auf dieser Benutzer Funktionalität aufbauen, die leistungsstarke Mehrzweck-Anwendungsfälle umfasst, die räumliche Azure-Anker für räumliche Ausrichtung nutzen.

## <a name="objectives"></a>Ziele

- Kombinieren mehrerer Konzepte aus früheren Lektionen, um eine einzigartige Umgebung zu schaffen
- Informationen zum Umschalten von Objekten
- Auslösen komplexer Ereignisse über drückbare Schaltflächen
- Verwenden der physischen Effekte und Kräfte von Starrkörpern
- Erkunden der Verwendung von QuickInfos

## <a name="instructions"></a>Anweisungen

### <a name="configuring-the-lunar-module"></a>Konfigurieren der Mondlandefähre

In diesem Abschnitt werden die verschiedenen Komponenten vorgestellt, die zum Erstellen unserer Beispiel Funktionen erforderlich sind.

1. Fügen Sie der Basis Szene die vorfab-Assembly für das Mondmodul hinzu. Navigieren Sie zu diesem Zweck auf der Registerkarte Projekt zu Assets > basemoduleassets > Prefabs. Sie sehen zwei Prefabs für das Raketenstart Programm, ziehen Sie die Launcher_Tutorial Prefab in ihre Szene, und positionieren Sie Sie wie gewünscht.

    >[!NOTE]
    >Der Launcher_Complete Prefab ist das abgeschlossene Start Programm, das als Referenz bereitgestellt wird.

    ![Lektion6 Kapitel1 Schritt1im](images/Lesson6_Chapter1_step1im.PNG)

    Wenn Sie das Launcher_Tutorial Game-Objekt in der Hierarchie erweitern und das Mond Modul Objekt weiter erweitern, finden Sie mehrere untergeordnete Objekte, die ein Material mit dem Namen "x-ray" aufweisen. Das "x-ray"-Material ermöglicht eine etwas durchlässiges Farbe, die als Platzierungs Hinweise für den Benutzer verwendet wird. 

    ![Lesson6 Chapter1 noteaim](images/Lesson6_Chapter1_noteaim.PNG)

    Es gibt fünf Teile für das Mond Modul, mit dem der Benutzer interagieren wird, wie in der folgenden Abbildung dargestellt:

    1. Rover-Gehäuse
    2. Treibstofftank
    3. Energiezelle
    4. Andockportal
    5. Externer Sensor

    ![Lektion6 Kapitel1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

    >[!NOTE]
    >Die Spielobjektnamen, die in Ihrer Basisszenenhierarchie angezeigt werden, entsprechen nicht den Namen der Objekte in der Szene.

2. Fügen Sie dem lunarmodule-Spielobjekt eine Audioquelle hinzu. Stellen Sie sicher, dass das lunarmodule in ihrer Szenen Hierarchie ausgewählt ist, und klicken Sie auf Komponente hinzufügen Suchen Sie nach Audioquelle, und fügen Sie Sie dem Spielobjekt hinzu. Lassen Sie das Feld "Audioclip" für den Moment leer, ändern Sie die Einstellung "besondere Blend" jedoch von 0 in 1, damit räumliche Audiodaten aktiviert werden. Sie verwenden diese Audioquelle, um den Start Sound zu einem späteren Zeitpunkt wiederzugeben.

    ![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG)

3. Fügen Sie die Skript-Schalter-Platzierungs Hinweise hinzu. Klicken Sie auf Komponente hinzufügen, und suchen Sie nach Platzierungs Hinweisen zum Umschalten. Dabei handelt es sich um ein benutzerdefiniertes Skript, mit dem Sie die über sichtigen Hinweise (Objekte mit dem x-ray-Material) wie zuvor erwähnt aktivieren und deaktivieren können.

    ![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG)

4. Da wir über fünf Objekte verfügen, geben Sie "5" für die Größe des Spielobjekt Arrays ein. Daraufhin werden fünf neue Elemente angezeigt.

    ![Lektion6 Kapitel1 Schritt4bim](images/Lesson6_Chapter1_step4bim.PNG)

    Ziehen Sie jedes der durchlässigen Objekte in alle Felder namens (Spielobjekt). Ziehen Sie die folgenden Objekte aus dem Lunar-Modul in der Szene in die Objekt Array Felder, wie in der obigen Abbildung dargestellt:

    ![Lektion6 Kapitel1 Schritt4aim](images/Lesson6_Chapter1_step4aim.PNG)

    Das Skript zum Umschalten der Platzierungs Hinweise ist nun konfiguriert, sodass wir Hinweise aktivieren und deaktivieren können.

5. Fügen Sie das Skript Launch Lunar Module hinzu. Klicken Sie auf die Schaltfläche Komponente hinzufügen, suchen Sie nach "Launch Lunar Module", und wählen Sie Sie aus Mit diesem Skript wird das Mond Modul gestartet. Wenn wir auf eine konfigurierte Schaltfläche klicken, wird der festen Textkomponente des mondmoduls eine aufwärts-Force hinzugefügt, und das Modul wird aufwärts gestartet. Wenn Sie sich in einem Gebäude befinden, kollidiert die Mondlandefähre möglicherweise mit Ihrem Deckengittermodell. Wenn Sie sich in einem Bereich mit hohen oder gar keinen Obergrenzen befinden, wird das Mond Modul unbegrenzt in den Speicherbereich überlaufen.

    ![Lektion6 Kapitel1 Schritt5im](images/Lesson6_Chapter1_step5im.PNG)

6. Passen Sie den Schub so an, dass die Mondlandefähre anmutig nach oben aufsteigt. Versuchen Sie einen Wert von 0,01. Lassen Sie das Feld „Rb“ leer. RB steht für den starren Text, und dieses Feld wird während der Laufzeit automatisch aufgefüllt.

    ![Lektion6 Kapitel1 Schritt6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>Übersicht über die Komponenten von Mond Modulen

Das übergeordnete Objekt der Mond Modul Teile ist die Sammlung der Objekte, mit denen der Benutzer interagiert. In der folgenden Liste werden die Namen von Spielobjekten mit der Bezeichnung Namen in Klammern angegeben:

- Rucksack (Energie Zelle)
- Gastank (Treibstofftank)
- TopLeftBody (Rover Enclosure) – Oberer linker Körper (Rover-Gehäuse)
- Nose (Docking Portal) – Nase (Andockportal)
- LeftTwirler (External Sensor) – Linker Drallkörper (Externer Sensor)

Beachten Sie, dass jedes dieser Objekte über einen Manipulations Handler verfügt, wie in Lektion 4 erläutert. Diese Funktion ermöglicht es Benutzern, das Objekt zu erfassen und zu bearbeiten. Beachten Sie außerdem, dass die-Einstellung, die zwei übergebenen Manipulations Typen ist, auf verschieben und drehen festgelegt ist. Mit dieser Option kann der Benutzer das Objekt nur verschieben und seine Größe nicht ändern. Dies ist die gewünschte Funktionalität für eine assemblyanwendung.
Außerdem ist die weite Bearbeitung deaktiviert, um nur die direkte Interaktion von Modul Teilen zuzulassen.

![Lektion6 Kapitel2im](images/Lesson6_Chapter2im.PNG)

Das Demoskript der Teile Assembly (siehe oben) ist das Skript, mit dem die Objekte verwaltet werden, die der Benutzer im Mond Modul vom Benutzer platziert.

Das Feld Objekt zum Platzieren ist die ausgewählte Transformation, wie in der Abbildung oben gezeigt, der dem Objekt zugeordnete Rucksack/Kraftstofftank, mit dem die Verbindung hergestellt wird.

Mit den Einstellungen für die Near Distance und far distance wird die Nähe festgelegt, zu der Teile direkt oder freigegeben werden können. Beispielsweise muss der Rucksack/Treibstofftank 0,1 Einheiten vom Mond Modul entfernt werden, bevor das Snap-in-Modul stattfindet. Die Einstellung für die weite Entfernung legt den Speicherort fest, an dem sich das Objekt befinden kann, bevor es vom Mond Modul getrennt werden kann. In diesem Fall muss die Hand des Benutzers den Rucksack/Treibstofftank greifen und ihn 0,2 Einheiten von der Mondlandefähre wegziehen, damit er nicht wieder an seiner Position andockt.

Das QuickInfo-Objekt ist die QuickInfo-Bezeichnung in der Szene. Wenn die Objekte an Ort und Stelle ausgerichtet werden, ist die Bezeichnung deaktiviert.

Die Audioquelle wird automatisch gepackt.

### <a name="configuring-the-placement-hints-button"></a>Konfigurieren der Schaltfläche Platzierungs Hinweise

In [Lektion 2](mrlearning-base-ch2.md)haben Sie gelernt, wie Sie Schaltflächen platzieren und konfigurieren können, um Dinge wie das Ändern der Farbe eines Elements oder das Abspielen eines Sounds beim Pushvorgang zu ermöglichen. Wir werden diese Prinzipien weiterhin verwenden, wenn wir unsere Schaltflächen zum Umschalten von Platzierungshinweisen konfigurieren.

Ziel ist es, die Schaltfläche so zu konfigurieren, dass jedes Mal, wenn der Benutzer die Schaltfläche "Platzierungs Hinweis" drückt, die Sichtbarkeit der Hinweise zur durchlässigen Platzierung schaltet.

1. Verschieben Sie das Mond Modul in den leeren reinen Laufzeitbereich im Inspektor-Panel, während das Objekt Platzierungs Hinweise in der Basis Szenen Hierarchie ausgewählt wird.

    ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG)

2. Klicken Sie auf die Dropdown Liste keine Funktion. Wechseln Sie zu "umggleplacementhints", und wählen Sie unter diesem Menü den Befehl "" "" "" "" "" " "Degglegameobjects ()" schaltet die Platzierungs Hinweise ein und aus, sodass Sie bei jedem Drücken der Schaltfläche sichtbar oder unsichtbar sind.

    ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>Konfigurieren der Schaltfläche Zurücksetzen

Es gibt Situationen, in denen der Benutzer einen Fehler ausgibt, das Objekt versehentlich auslöst oder nur die Benutzeroberflächen zurücksetzen möchte. Mit der Schaltfläche Zurücksetzen können Sie die Funktionalität neu starten.

1. Wählen Sie die Schaltfläche Zurücksetzen. In der Basis Szene heißt der Name Reort.

2. Ziehen Sie das Modul "Mond" aus der Basis Szenen Hierarchie in den leeren Slot unter der Schaltfläche "gedrückt" im Inspektor-Panel.

    ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

3. Wählen Sie das Dropdown Menü No Function aus, zeigen Sie auf launchlunarmodule, und wählen Sie dann resetmodule () aus.

    ![Lektion6 Kapitel4 Schritt3im](images/Lesson6_Chapter4_step3im.PNG)

    >[!NOTE]
    >Beachten Sie, dass die gameobject. broadcastmessage standardmäßig für resetplacement konfiguriert ist. Dadurch wird eine Nachricht mit dem Namen resetplacement für jedes untergeordnete Objekt des RocketLauncher_Tutorial übermittelt. Alle-Objekte, die über eine-Methode für resetplacement () verfügen, reagieren auf diese Nachricht, indem Sie die Position zurücksetzt.

### <a name="configuring-the-launch-button"></a>Konfigurieren der Schaltfläche "starten"

In diesem Abschnitt wird erläutert, wie Sie die Schaltfläche "Start" konfigurieren, die es dem Benutzer ermöglicht, die Schaltfläche zu drücken und das Mond Modul in den Raum zu

1. Wählen Sie die Schaltfläche Starten aus. In der Basis Szene heißt Sie launchroundbutton. Ziehen Sie das Modul "Lunar" in den leeren Slot unter "touchende" im Inspektor-Panel.

    ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG)

2. Wählen Sie das Dropdown Menü keine Funktion aus, zeigen Sie auf launchlunarmodule, und wählen Sie stopthruster() aus. Dadurch wird gesteuert, wie viel der Benutzer an das Mond Modul übergeben möchte.

    ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)

3. Ziehen Sie das Modul "Mond" aus der Basis Szenen Hierarchie in den leeren Slot unter der Schaltfläche "gedrückt" im Inspektor-Panel.

4. Klicken Sie auf das Dropdown Menü keine Funktion und dann auf launchlunarmodule, und wählen Sie startthruester () aus.

    ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)

5. Fügen Sie dem Lunar-Modul Musik hinzu, damit Musik abgespielt wird, wenn die Abladung ausgeschaltet wird. Ziehen Sie hierzu das Mond Modul auf den nächsten leeren Slot unter der Schaltfläche gedrückt ().

6. Wählen Sie das Dropdown Menü No Function aus, zeigen Sie auf audiosource, und wählen Sie playoneshot (Audioclip) aus. Sie können jederzeit die Vielfalt der im MRTK enthaltenen Sounds erkunden. In diesem Beispiel verwenden wir "MRTK_Gem".

    ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)

### <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben diese Anwendung vollständig konfiguriert. Wenn Sie jetzt auf "Abspielen" klicken, können Sie das Mond Modul vollständig zusammenstellen, Hinweise umschalten, das Mond Modul starten und es erneut starten.
