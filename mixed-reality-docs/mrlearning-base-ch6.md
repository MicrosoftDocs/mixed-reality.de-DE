---
title: MR-Basislernmodul – Beispielerfahrung für die Montage einer Mondlandefähre
description: In dieser Lektion werden wir mehrere Konzepte, die wir in früheren Lektionen kennengelernt haben, kombinieren, um eine einzigartige Beispielerfahrung zu schaffen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 8a2f388e842d521f991203916177e3dac15769eb
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730850"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a>MR-Basislernmodul – Beispielerfahrung für die Montage einer Mondlandefähre

In dieser Lektion werden wir mehrere Konzepte, die wir in früheren Lektionen kennengelernt haben, kombinieren, um eine einzigartige Beispielerfahrung zu schaffen. Wir werden eine Anwendung zur Montage einer Mondlandefähre erstellen, bei der ein Benutzer mit nachverfolgten Händen Teile der Mondlandefähre aufnehmen und versuchen muss, die Mondlandefähre zu montieren. Wir werden drückbare Schaltflächen verwenden, um Platzierungshinweise umzuschalten, unsere Umgebung zurückzusetzen und unsere Mondlandefähre in den Weltraum zu befördern. In zukünftigen Tutorials werden wir weiterhin auf dieser Umgebung aufbauen, einschließlich leistungsfähiger Anwendungsfälle für mehrere Benutzer, die Azure Spatial Anchors für die räumliche Ausrichtung nutzen.

## <a name="objectives"></a>Ziele

- Kombinieren mehrerer Konzepte aus früheren Lektionen, um eine einzigartige Umgebung zu schaffen
- Informationen zum Umschalten von Objekten
- Auslösen komplexer Ereignisse über drückbare Schaltflächen
- Verwenden der physischen Effekte und Kräfte von Starrkörpern
- Erkunden der Verwendung von QuickInfos

## <a name="instructions"></a>Anweisungen

### <a name="configuring-the-lunar-module"></a>Konfigurieren der Mondlandefähre

In diesem Kapitel werden wir mit den verschiedenen Komponenten vertraut gemacht, die für die Erstellung unserer Beispielerfahrung erforderlich sind.

1. Fügen Sie das Prefab für die Montage der Mondlandefähre zu Ihrer Basisszene hinzu. Suchen Sie dazu auf der Projektregisterkarte nach „Rocket Launcher_Tutorial“. Sie finden das Prefab auch unter „Assets>BaseModuleAssets>Prefabs“. Möglicherweise werden zwei Prefabs für Raketenstartanlagen angezeigt: eine mit dem Namen „Tutorial“ und eine mit dem Namen „Complete“ (Vollständig). Ziehen Sie das Prefab „Rocket Launcher_Tutorial“ in Ihre Basisszene. Sie können das Prefab in Ihrer Szene nach Belieben platzieren.
   Hinweis: Das Prefab "Rocket Launcher_Complete" ist die fertige Startanlage, die als Referenz dient. 

![Lektion6 Kapitel1 Schritt1im](images/Lesson6_Chapter1_step1im.PNG)

Wenn Sie das Spielobjekt „Rocket Launcher_Tutorial“ in Ihrer Hierarchie erweitern und das Objekt „Lunar Module“ (Mondlandefähre) weiter erweitern, sehen Sie mehrere untergeordnete Objekte, die ein Material namens „x-ray“ (Röntgenstrahlen) enthalten. Das Material „x-ray“ (Röntgenstrahlen) ermöglicht eine leicht durchscheinende Farbe, die wir als Platzierungshinweise für den Benutzer verwenden werden. 

![Lektion6 Kapitel1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) Die Mondlandefähre besteht aus fünf Teilen, mit denen der Benutzer interagieren wird, wie in der folgenden Abbildung gezeigt:

1.  Rover-Gehäuse
2.  Treibstofftank
3.  Energiezelle
4.  Andockportal 
5.  Externer Sensor

![Lektion6 Kapitel1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> Hinweis: Die Spielobjektnamen, die in Ihrer Basisszenenhierarchie angezeigt werden, entsprechen nicht den Namen der Objekte in der Szene.

Schritt 2: Fügen Sie der Mondlandefähre eine Audioquelle hinzu. Stellen Sie sicher, dass die Mondlandefähre in Ihrer Basisszenenhierarchie ausgewählt ist, und klicken Sie auf „Add Component“ (Komponente hinzufügen). Suchen Sie nach „Audio Source“ (Audioquelle), und fügen Sie diese dem Objekt hinzu. Lassen Sie es vorerst leer. Wir werden damit später den Startsound wiedergegeben.
 ![Lektion6 Kapitel1 Schritt2im](images/Lesson6_Chapter1_step2im.PNG) Schritt 3: Fügen Sie das Skript „Toggle Placement Hints“ (Platzierungshinweise umschalten) hinzu. Klicken Sie auf „Add Component“ (Komponente hinzufügen), und suchen Sie nach „Toggle Placement Hints“ (Platzierungshinweise umschalten). Dies ist ein benutzerdefiniertes Skript, mit dem Sie die zuvor erwähnten lichtdurchlässigen Hinweise (Objekte mit dem Röntgenmaterial) ein- und ausschalten können. 
![Lektion6 Kapitel1 Schritt3im](images/Lesson6_Chapter1_step3im.PNG) Schritt 4: Da wir über fünf Objekte verfügen, geben Sie „5“ für die Größe des Arrays der Spielobjekte ein. Dann sollten fünf neue Elemente angezeigt werden. 

![Lektion6 Kapitel1 Schritt4bim](images/Lesson6_Chapter1_step4bim.PNG)

Ziehen Sie jedes der lichtdurchlässigen Objekte in die Felder mit der Aufschrift „None (Game Object)“ (Keine (Spielobjekt)). Ziehen Sie die folgenden Objekte von der Mondlandefähre in Ihre Basisszene: 

•   Backpack (Rucksack)

•   GasTank (Treibstofftank)

•   Topleftbody (Oberer linker Körper)

•   Nose (Nase)

•   LeftTwirler (Linker Drallkörper)

 ![Lektion6 Kapitel1 Schritt4aim](images/Lesson6_Chapter1_step4aim.PNG)

Jetzt ist das Skript „Toggle Placement Hints“ (Platzierungshinweise umschalten) konfiguriert. Dadurch können wir die Hinweise ein- und ausschalten.

Schritt 5: Fügen Sie das Skript „Launch Lunar Module“ (Mondlandefähre starten) hinzu. Klicken Sie auf die Schaltfläche „Add Component“ (Komponente hinzufügen), suchen Sie nach „Launch Lunar Module“ (Mondlandefähre starten) und wählen Sie dies aus. Dieses Skript ist für den Start der Mondlandefähre zuständig. Wenn wir eine konfigurierte Schaltfläche drücken, fügt sie der starren Gehäusekomponente der Mondlandefähre eine Auftriebskraft hinzu und bewirkt, dass das Modul nach oben startet. Wenn Sie sich in einem Gebäude befinden, kollidiert die Mondlandefähre möglicherweise mit Ihrem Deckengittermodell. Aber wenn Sie sich im Freien befinden, fliegt sie in die unendlichen Weiten des Weltraums. 

![Lektion6 Kapitel1 Schritt5im](images/Lesson6_Chapter1_step5im.PNG)

Schritt 6: Passen Sie den Schub so an, dass die Mondlandefähre anmutig nach oben aufsteigt. Versuchen Sie einen Wert von 0,01. Lassen Sie das Feld „Rb“ leer. „Rb“ steht für „Rigid Body“ (Starrkörper), und dieses Feld wird zur Laufzeit automatisch ausgefüllt.

![Lektion6 Kapitel1 Schritt6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>Übersicht über die Komponenten der Mondlandefähre
Das übergeordnete Objekt der Teile der Mondlandefähre ist die Sammlung der Objekte, mit denen der Benutzer interagieren wird. Die Namen der Spielobjekte (mit Szenennamen in Klammern) sind in der folgenden Liste aufgeführt:

- Backpack (Fuel Tank) – Rucksack (Treibstofftank)
- GasTank (Energy Cell) – Treibstofftank (Energiezelle)
- TopLeftBody (Rover Enclosure) – Oberer linker Körper (Rover-Gehäuse)
- Nose (Docking Portal) – Nase (Andockportal)
- LeftTwirler (External Sensor) – Linker Drallkörper (Externer Sensor)

Beachten Sie, dass jedes dieser Objekte den Manipulationshandler aufweist, wie in Lektion 4 beschrieben. Mit dem Manipulationshandler können Benutzer das Objekt greifen und bearbeiten. Beachten Sie auch, dass die Einstellung „Two Handed Manipulation Type“ (Zweihändiger Manipulationstyp) auf „Move and Rotate“ (Bewegen und Drehen) festgelegt ist. Hierdurch kann der Benutzer das Objekt nur bewegen und nicht seine Größe ändern, was die gewünschte Funktionalität für eine Montageanwendung darstellt.
Darüber hinaus ist die ferne Bearbeitung nicht aktiviert, sodass nur eine direkte Interaktion der Modulteile möglich ist.

![Lektion6 Kapitel2im](images/Lesson6_Chapter2im.PNG)

Das Demoskript für die Baugruppenmontage (siehe oben) ist das Skript, das die Objekte verwaltet, die vom Benutzer auf der Mondlandefähre platziert werden sollen. 

Das Feld „Object To Place“ (Zu platzierendes Objekt) ist die Transformation, die mit dem Objekt ausgewählt (für die obige Abbildung ist dies der Rucksack/Treibstofftank) wird, mit der sie verbunden werden kann. 

Die Einstellungen „Near Distance“ (Kurze Distanz) und „Far Distance“ (Weite Distanz) sind dafür verantwortlich, die Nähe zu bestimmen, bei der Teile andocken oder freigegeben werden. Der Rucksack/Treibstofftank müsste z. B. einen Abstand von 0,1 Einheiten von der Mondlandefähre haben, um an seiner Position anzudocken. „Far Distance“ (Weite Distanz) legt die Position fest, ab der das Objekt von der Mondlandefähre gelöst werden soll. In diesem Fall muss die Hand des Benutzers den Rucksack/Treibstofftank greifen und ihn 0,2 Einheiten von der Mondlandefähre wegziehen, damit er nicht wieder an seiner Position andockt.

Das „Tool Tip Object“ (QuickInfo-Objekt) stellt die Bezeichnung der QuickInfo in der Szene dar. Wenn die Objekte angedockt sind, wird die Bezeichnung deaktiviert. 

Die Audioquelle wird automatisch erfasst. 

### <a name="placement-hints-buttons"></a>Schaltflächen für Platzierungshinweise
In [Lektion 2](mrlearning-base-ch2.md) haben Sie erfahren, wie Sie Schaltflächen platzieren und konfigurieren, um z. B. die Farbe eines Elements zu ändern oder es beim Drücken einen Sound wiedergeben zu lassen. Wir werden diese Prinzipien weiterhin verwenden, wenn wir unsere Schaltflächen zum Umschalten von Platzierungshinweisen konfigurieren. 

Ziel ist es, unsere Schaltfläche so zu konfigurieren, dass sie jedes Mal, wenn der Benutzer die Schaltfläche für Platzierungshinweise drückt, die Sichtbarkeit der lichtdurchlässigen Platzierungshinweise umschaltet. 

Schritt 1: Verschieben Sie die Mondlandefähre an den leeren Platz „Runtime only“ (Nur Runtime) im Inspektorbereich, während das Objekt für Platzierungshinweise in Ihrer Basisszenarienhierarchie aktiviert ist. 
 ![Lektion6 Kapitel3 Schritt1im](images/Lesson6_Chapter3_step1im.PNG) Schritt 2: Klicken Sie jetzt auf die Dropdownliste mit der Aufschrift „No Function“ (Keine Funktion). Wechseln Sie nach unten zu „TogglePlacementHints“, und wählen Sie unter diesem Menü „ToggleGameObjects ()“ aus. „ToggleGameObjects()“ schaltet die Platzierungshinweise ein und aus, sodass sie bei jedem Drücken der Schaltfläche ein- oder ausgeblendet werden.
 ![Lektion6 Kapitel3 Schritt2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>Konfigurieren der Schaltfläche zum Zurücksetzen

Es wird Situationen geben, in denen der Benutzer einen Fehler macht, oder versehentlich das Objekt wegwirft oder einfach nur die Umgebung zurücksetzen will. Die Schaltfläche zum Zurücksetzen (Reset) fügt die Möglichkeit hinzu, die Umgebung neu zu starten. 

Schritt 1: Wählen Sie die Schaltfläche „Reset“ (Zurücksetzen) aus. In der Basisszene trägt sie die Bezeichnung „ResetRoundButton“. 

Schritt 2: Ziehen Sie die Mondlandefähre aus der Basisszenenhierarchie in den leeren Bereich unter „Button Pressed“ (Schaltfläche gedrückt) im Inspektorbereich.
 ![Lektion6 Kapitel4 Schritt2im](images/Lesson6_Chapter4_step2im.PNG)

Schritt 3: Wählen Sie das Dropdownmenü mit der Bezeichnung „No Function“ (Keine Funktion) aus, und bewegen Sie den Mauszeiger über „LaunchLunarModule“. Wählen Sie jetzt „resetModule ()“ aus.

![Lektion6 Kapitel4 Schritt3im](images/Lesson6_Chapter4_step3im.PNG)

> Hinweis: Sie werden feststellen, dass „GameObject.BroadcastMessage“ standardmäßig auf „ResetPlacement“ festgelegt ist. Dadurch wird für jedes untergeordnete Objekt von „RocketLauncher_Tutorial“ eine Nachricht mit dem Namen „ResetPlacement“ gesendet. Jedes Objekt, das über eine Methode für „ResetPlacement()“ verfügt, reagiert auf diese Nachricht mit dem Zurücksetzen seiner Position. 

### <a name="launching-the-lunar-module"></a>Starten der Mondlandefähre
In diesem Kapitel werden wir die Starttaste konfigurieren. Dadurch kann der Benutzer die Taste drücken und die Mondlandefähre ins All starten.

Schritt 1: Wählen Sie die Starttaste aus (in der Basisszene ist dies „LaunchRoundButton“). Ziehen Sie die Mondlandefähre in den leeren Bereich unter „Touch End“ (Ende der Toucheingabe) im Inspektorbereich.
 ![Lektion6 Kapitel5 Schritt1im](images/Lesson6_Chapter5_step1im.PNG) Schritt 2: Wählen Sie das Dropdownmenü mit der Aufschrift „No Function“ (Keine Funktion) aus. Bewegen Sie den Mauszeiger über „LaunchLunarModule“, und wählen Sie „StopThruster ()“ aus. Dadurch wird gesteuert, wie viel Schub der Benutzer der Mondlandefähre gestatten möchte. 
 ![Lektion6 Kapitel5 Schritt2im](images/Lesson6_Chapter5_step2im.PNG) Schritt 3: Fügen Sie unter „ButtonPressed()“ die Mondlandefähre (klicken, halten und ziehen) zum leeren Bereich hinzu. 

Schritt 4: Klicken Sie auf das Dropdownmenü mit der Bezeichnung „No Function“ (Keine Funktion), und wählen Sie „StartThruster ()“ aus. 
 ![Lektion6 Kapitel5 Schritt4im](images/Lesson6_Chapter5_step4im.PNG) Schritt 5: Fügen Sie der Mondlandefähre Musik hinzu, sodass beim Start der Rakete die Musik wiedergegeben wird. Ziehen Sie dazu die Mondlandefähre unter „Button Pressed()“ in den nächsten freien Bereich.

Schritt 6: Wählen Sie das Dropdownmenü mit der Aufschrift „No Function“ (Keine Funktion) aus, bewegen Sie den Mauszeiger über die Option „AudioSource“ (Audioquelle), und wählen Sie „PlayOneShot (AudioClip)“ aus. Sie können jederzeit die Vielfalt der im MRTK enthaltenen Sounds erkunden. Für dieses Beispiel werden wir bei „MRTK_Gem“ bleiben.
 ![Lektion6 Kapitel5 Schritt6im](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>Herzlichen Glückwunsch! 
Sie haben diese Anwendung vollständig konfiguriert! Wenn Sie jetzt die Wiedergabetaste drücken, können Sie die Mondlandefähre vollständig montieren, Hinweise umschalten, die Mondlandefähre starten und die Umgebung zurücksetzen, um wieder von vorne zu beginnen.
