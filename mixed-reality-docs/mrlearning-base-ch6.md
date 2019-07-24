---
title: MR-Basislernmodul – Beispielerfahrung für die Montage einer Mondlandefähre
description: In dieser Lektion werden wir mehrere Konzepte, die wir in früheren Lektionen kennengelernt haben, kombinieren, um eine einzigartige Beispielerfahrung zu schaffen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 79f2d3a4a3224533761ea2e4a7e73dc3d4d5e53e
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387687"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. Erstellen einer Beispielanwendung für ein Mond Modul

In diesem Tutorial kombinieren wir mehrere Konzepte, die in den vorherigen Lektionen vorgestellt wurden, um eine einzigartige Beispiel Darstellung zu erstellen. Wir erstellen eine Anwendung für eine Mond Modul Assembly, bei der ein Benutzer überwachte Hände zum Abrufen von Mond Modul teilen und zum Assemblieren eines mondmoduls verwenden muss. Mithilfe von druckbaren Schaltflächen können Sie Platzierungs Hinweise umschalten, die Leistung zurücksetzen und das Mond Modul in den Raum bringen! In zukünftigen Tutorials werden wir weiterhin auf dieser Benutzer Funktionalität aufbauen, die leistungsstarke Mehrzweck-Anwendungsfälle umfasst, die räumliche Azure-Anker für räumliche Ausrichtung nutzen.

## <a name="objectives"></a>Ziele

- Kombinieren mehrerer Konzepte aus früheren Lektionen, um eine einzigartige Umgebung zu schaffen
- Informationen zum Umschalten von Objekten
- Auslösen komplexer Ereignisse über drückbare Schaltflächen
- Verwenden der physischen Effekte und Kräfte von Starrkörpern
- Erkunden der Verwendung von QuickInfos

## <a name="instructions"></a>Anweisungen

### <a name="configuring-the-lunar-module"></a>Konfigurieren der Mondlandefähre

In diesem Abschnitt werden die verschiedenen Komponenten vorgestellt, die zum Erstellen unserer Beispiel Funktionen erforderlich sind.

1. Fügen Sie der Basis Szene die vorfab-Assembly für das Mondmodul hinzu. Zu diesem Zweck suchen Sie auf der Registerkarte "Projekt" nach "Rocket Launcher_Tutorial". 
Suchen Sie die vorfab in Assets-> basemoduleassets-> Prefabs. Außerdem werden zwei Raketenstart Programm-präfabs angezeigt. eine mit dem Namen "Tutorial" und die andere mit dem Namen "Complete". Ziehen Sie die "Rocket Launcher_Tutorial Prefab" in die Basis Szene, und positionieren Sie Sie nach Belieben.
   Hinweis: Die "Launcher Launcher_Complete Prefab" ist das abgeschlossene Start Programm, das als Referenz bereitgestellt wird. 

![Lektion6 Kapitel1 Schritt1im](images/Lesson6_Chapter1_step1im.PNG)

Wenn Sie das Launcher_Tutorial-Spielobjekt in der Hierarchie erweitern und das Mond Modul Objekt weiter erweitern, finden Sie mehrere untergeordnete Objekte, die ein Material mit dem Namen "x-ray" aufweisen. Das "x-ray"-Material ermöglicht eine etwas durchlässiges Farbe, die wir als Platzierungs Hinweise für den Benutzer verwenden werden. 

![Lesson6 Chapter1 noteaim](images/Lesson6_Chapter1_noteaim.PNG) es gibt fünf Teile für das Mond Modul, mit dem der Benutzer interagieren wird, wie in der folgenden Abbildung dargestellt:

1.  Rover-Gehäuse
2.  Treibstofftank
3.  Energiezelle
4.  Andockportal 
5.  Externer Sensor

![Lektion6 Kapitel1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> Hinweis: Die Spielobjekt Namen, die in der Basis Szenen Hierarchie angezeigt werden, entsprechen nicht den Namen der Objekte in der Szene.

Schritt 2: Fügen Sie der Mondlandefähre eine Audioquelle hinzu. Stellen Sie sicher, dass das Mondmodul in der Basis Szenen Hierarchie ausgewählt ist, und klicken Sie auf Komponente hinzufügen. Suchen Sie nach Audioquelle, und fügen Sie Sie dem-Objekt hinzu. Lassen Sie es vorerst leer. Wir werden damit später den Startsound wiedergegeben.

 ![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG)  
Schritt 3: Fügen Sie das Skript hinzu, und schalten Sie Platzierungs Hinweise um. Klicken Sie auf Komponente hinzufügen, und suchen Sie nach Platzierungs Hinweisen zum Umschalten. Dabei handelt es sich um ein benutzerdefiniertes Skript, mit dem Sie die weiter oben erwähnten durchlässigen Hinweise (Objekte mit dem x-ray-Material) aktivieren und deaktivieren können.  
![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG)  
Schritt 4: Da wir über fünf Objekte verfügen, geben Sie "5" für die Größe des Spielobjekt Arrays ein. Anschließend werden fünf neue Elemente angezeigt.  


![Lektion6 Kapitel1 Schritt4bim](images/Lesson6_Chapter1_step4bim.PNG)

Ziehen Sie jedes der durchlässigen Objekte in alle Namen Felder (Spielpunkt).
Ziehen Sie die folgenden Objekte von der Mondlandefähre in Ihre Basisszene: 

•   Backpack (Rucksack)

•   GasTank (Treibstofftank)

•   Topleftbody (Oberer linker Körper)

•   Nose (Nase)

•   LeftTwirler (Linker Drallkörper)

 ![Lektion6 Kapitel1 Schritt4aim](images/Lesson6_Chapter1_step4aim.PNG)

Das Skript zum Umschalten der Platzierungs Hinweise ist jetzt konfiguriert. Dies ermöglicht es uns, Hinweise zu aktivieren und zu deaktivieren.

Schritt 5: Fügen Sie das Skript Launch Lunar Module hinzu. Klicken Sie auf die Schaltfläche Komponente hinzufügen, suchen Sie nach "Launch Lunar Module", und wählen Sie Sie aus. Mit diesem Skript wird das Mond Modul gestartet. Wenn wir auf eine konfigurierte Schaltfläche klicken, wird eine aufwärts-Force zur festen Textkomponente des mondmoduls hinzugefügt, und das Modul wird aufwärts gestartet. Wenn Sie sich in einem Gebäude befinden, kollidiert die Mondlandefähre möglicherweise mit Ihrem Deckengittermodell. Aber wenn Sie sich im Freien befinden, fliegt sie in die unendlichen Weiten des Weltraums. 

![Lektion6 Kapitel1 Schritt5im](images/Lesson6_Chapter1_step5im.PNG)

Schritt 6: Passen Sie den Schub so an, dass die Mondlandefähre anmutig nach oben aufsteigt. Versuchen Sie einen Wert von 0,01. Lassen Sie das Feld „Rb“ leer. „Rb“ steht für „Rigid Body“ (Starrkörper), und dieses Feld wird zur Laufzeit automatisch ausgefüllt.

![Lektion6 Kapitel1 Schritt6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>Übersicht über die Komponenten von Mond Modulen
Das übergeordnete Objekt der Mond Modul Teile ist die Sammlung der Objekte, mit denen der Benutzer interagiert. In der folgenden Liste werden die Namen von Spielobjekten, deren Bezeichnung Namen in den Parametern enthalten sind, bereitgestellt:

- Backpack (Fuel Tank) – Rucksack (Treibstofftank)
- GasTank (Energy Cell) – Treibstofftank (Energiezelle)
- TopLeftBody (Rover Enclosure) – Oberer linker Körper (Rover-Gehäuse)
- Nose (Docking Portal) – Nase (Andockportal)
- LeftTwirler (External Sensor) – Linker Drallkörper (Externer Sensor)

Beachten Sie, dass jedes dieser Objekte über einen Manipulations Handler verfügt, wie in Lektion 4 erläutert. Mithilfe des Bearbeitungs Handlers können Benutzer das Objekt erfassen und bearbeiten. Beachten Sie außerdem, dass die Einstellung zwei Hand Bearbeitungs Typen auf verschieben und drehen festgelegt ist. Hierdurch kann der Benutzer das Objekt nur bewegen und nicht seine Größe ändern, was die gewünschte Funktionalität für eine Montageanwendung darstellt.
Außerdem ist die weite Bearbeitung deaktiviert, um nur die direkte Interaktion von Modul Teilen zuzulassen.

![Lektion6 Kapitel2im](images/Lesson6_Chapter2im.PNG)

Das Demoskript der Teile Assembly (siehe oben) ist das Skript, mit dem die Objekte verwaltet werden, die der Benutzer im Mond Modul vom Benutzer platziert. 

Das Feld Objekt zum Platzieren ist die ausgewählte Transformation, wie in der Abbildung oben gezeigt, der dem Objekt zugeordnete Rucksack/Kraftstofftank, mit dem die Verbindung hergestellt wird. 

Mit den Einstellungen für die Near Distance und far distance wird die Nähe festgelegt, zu der Teile direkt oder freigegeben werden können. Beispielsweise muss der Rucksack/Treibstofftank 0,1 Einheiten vom Mond Modul entfernt werden, bevor das Snap-in-Modul stattfindet. Die Einstellung für die weite Entfernung legt den Speicherort fest, an dem sich das Objekt befinden kann, bevor es vom Mond Modul getrennt werden kann. In diesem Fall muss die Hand des Benutzers den Rucksack/Treibstofftank greifen und ihn 0,2 Einheiten von der Mondlandefähre wegziehen, damit er nicht wieder an seiner Position andockt.

Das QuickInfo-Objekt ist die QuickInfo-Bezeichnung in der Szene. Wenn die Objekte an Ort und Stelle ausgerichtet werden, ist die Bezeichnung deaktiviert. 

Die Audioquelle wird automatisch gepackt. 

### <a name="placement-hints-buttons"></a>Schaltflächen für Platzierungs Hinweise
In [Lektion 2](mrlearning-base-ch2.md) haben Sie erfahren, wie Sie Schaltflächen platzieren und konfigurieren, um z. B. die Farbe eines Elements zu ändern oder es beim Drücken einen Sound wiedergeben zu lassen. Wir werden diese Prinzipien weiterhin verwenden, wenn wir unsere Schaltflächen zum Umschalten von Platzierungshinweisen konfigurieren. 

Ziel ist es, die Schaltfläche so zu konfigurieren, dass jedes Mal, wenn der Benutzer die Schaltfläche "Platzierungs Hinweis" drückt, die Sichtbarkeit der Hinweise zur durchlässigen Platzierung schaltet. 

Schritt 1: Verschieben Sie das Mond Modul in den leeren reinen Laufzeitbereich im Inspektor-Panel, während das Objekt Platzierungs Hinweise in der Basis Szenen Hierarchie ausgewählt wird. 
 ![Lektion6 Kapitel3 Schritt1im](images/Lesson6_Chapter3_step1im.PNG) Schritt 2: Klicken Sie jetzt auf die Dropdown Liste keine Funktion. Wechseln Sie zu "umggleplacementhints", und wählen Sie unter diesem Menü den Befehl "" "" "" "" "" "Degglegameobjects ()" schaltet die Platzierungs Hinweise ein und aus, sodass Sie bei jedem Drücken der Schaltfläche sichtbar oder unsichtbar sind.  
 ![Lektion6 Kapitel3 Schritt2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>Konfigurieren der Schaltfläche Zurücksetzen

Es gibt Situationen, in denen der Benutzer einen Fehler verursacht oder versehentlich das Objekt auslöst oder nur die Benutzeroberflächen zurücksetzen möchte. Mit der Schaltfläche Zurücksetzen können Sie die Funktionalität neu starten. 

Schritt 1: Wählen Sie die Schaltfläche Zurücksetzen. In der Basis Szene hat Sie den Namen Reort. 

Schritt 2: Ziehen Sie das Modul "Mond" aus der Basis Szenen Hierarchie in den leeren Slot unter der Schaltfläche, die im Inspektor-Panel gedrückt
 ![Lektion6 Kapitel4 Schritt2im](images/Lesson6_Chapter4_step2im.PNG)

Schritt 3: Wählen Sie das Dropdown Menü No Function aus, und zeigen Sie auf launchlunarmodule, und wählen Sie resetmodule () aus.

![Lektion6 Kapitel4 Schritt3im](images/Lesson6_Chapter4_step3im.PNG)

> Hinweis: Beachten Sie, dass die gameobject. broadcastmessage standardmäßig für resetplacement konfiguriert ist. Dadurch wird eine Nachricht mit dem Namen resetplacement für jedes untergeordnete Objekt des RocketLauncher_Tutorial-Objekts übermittelt. Alle-Objekte, die über eine-Methode für resetplacement () verfügen, reagieren auf diese Nachricht, indem Sie die Position zurücksetzt. 

### <a name="launching-the-lunar-module"></a>Starten des mondmoduls
In diesem Abschnitt wird erläutert, wie Sie die Schaltfläche "Start" konfigurieren. Dies ermöglicht dem Benutzer das Drücken der Schaltfläche und das Starten des mondmoduls in Leerzeichen.

Schritt 1: Wählen Sie die Schaltfläche Starten aus. In der Basis Szene heißt launchroundbutton. Ziehen Sie das Modul "Lunar" in den leeren Slot unter "touchende" im Inspektor-Panel.
 ![Lektion6 Kapitel5 Schritt1im](images/Lesson6_Chapter5_step1im.PNG) Schritt 2: Wählen Sie das Dropdown Menü keine Funktion aus, zeigen Sie auf launchlunarmodule, und wählen Sie stopthruster() aus. Dadurch wird gesteuert, wie viel der Benutzer an das Mond Modul übergeben möchte. 
 ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)  
Schritt 3: Fügen Sie unter ButtonPressed () das Modul Lunar (klicken, halten und ziehen) in den leeren Slot ein. 

Schritt 4: Klicken Sie auf das Dropdown Menü keine Funktion, zeigen Sie auf launchlunarmodule, und wählen Sie startthruster() aus. 
 ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)  
Schritt 5: Fügen Sie dem Lunar-Modul Musik hinzu, damit Musik abgespielt wird, wenn die Abladung ausgeschaltet wird. Ziehen Sie hierzu das Mond Modul auf den nächsten leeren Slot unter der Schaltfläche gedrückt ().

Schritt 6: Wählen Sie das Dropdown Menü keine Funktion aus, zeigen Sie auf audiosource, und wählen Sie playoneshot (Audioclip) aus. Sie können jederzeit die Vielfalt der im MRTK enthaltenen Sounds erkunden. In diesem Beispiel verwenden wir "MRTK_Gem".
 ![Lektion6 Kapitel5 Schritt6im](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>Herzlichen Glückwunsch! 
Sie haben diese Anwendung vollständig konfiguriert. Wenn Sie jetzt auf "Abspielen" klicken, können Sie das Mond Modul vollständig zusammenstellen, Hinweise umschalten, das Mond Modul starten und es zurücksetzen, um alle wieder zu starten.
