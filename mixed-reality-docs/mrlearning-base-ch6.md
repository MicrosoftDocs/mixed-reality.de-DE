---
title: MR-Learning-Basis-Modul – Mondkalender Modul Assembly-Beispiel-Erfahrung
description: In dieser Lektion werden wir mehrere Konzepte, die von vorherigen Lektionen erstellen Sie eine eindeutige Beispiel Erfahrung gelernt kombinieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Gemischte Realität, Unity, Tutorial, hololens
ms.openlocfilehash: 303ed17724ba8799490aa7bca7a60600f6e5349b
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929603"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a>MR-Learning-Basis-Modul – Mondkalender Modul Assembly-Beispiel-Erfahrung

In dieser Lektion werden wir mehrere Konzepte, die von vorherigen Lektionen erstellen Sie eine eindeutige Beispiel Erfahrung gelernt kombinieren. Wir erstellen eine Assembly Mondkalender modulanwendung bei dem ein Benutzer überwachte Hände Mondkalender Modul Teile übernimmt und versucht, ein Mondkalender-Modul zusammenstellen muss. Wir verwenden pressable Schaltflächen zum Umschalten der Platzierung-Hinweise, die zum Zurücksetzen von unserer Erfahrung und unser Mondkalender-Modul in den Speicherplatz zu starten! In Zukunft werden Tutorials, wir weiterhin bauen auf dieser Oberfläche, einschließlich leistungsstarke Mehrbenutzer-Anwendungsfälle, die räumliche Anker Azure für die räumlichen Ausrichtung nutzt.

## <a name="objectives"></a>Ziele

- Kombinieren Sie mehrere Konzepte aus vorherigen Lektionen erstellen Sie ein einmaliges Benutzererlebnis
- Erfahren Sie, wie Objekte umschalten
- Komplexe mit pressable Schaltflächen Auslösen von Ereignissen
- Verwenden Sie "rigidbody" Physik und erzwingt, dass
- Verwenden von QuickInfos

## <a name="instructions"></a>Anweisungen

### <a name="configuring-the-lunar-module"></a>Konfigurieren des Moduls Mondkalender

In diesem Kapitel werden wir an die verschiedenen Komponenten, die zum Erstellen von unserer Erfahrung Beispiel benötigt vorgestellt.

1. Fügen Sie der Assembly-Prefab Mondkalender Module zu Ihrer Szene Base hinzu. Klicken Sie hierzu in der Registerkarte "Projekt" Suchen Sie "Rocket Launcher_Tutorial." Finden Sie auch den prefabs im Bestand > BaseModuleAssets > prefabs (Vorlagen). Sie feststellen, dass zwei Rocket Startprogramm prefabs (Vorlagen); eine mit dem Namen "Tutorial" und eine mit dem Namen "erledigt"setzen. Ziehen Sie das Prefab "Rocket Launcher_Tutorial" zu Ihrer Szene Basis ein. Die Platzierung der prefabs in Ihrer Szene platzieren können.
   Hinweis: Die "Rocket Launcher_Complete"-Prefab ist das abgeschlossene Startprogramm, dienen als Referenz. 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

Wenn Sie das Spiele "Rocket Launcher_Tutorial"-Objekt in Ihrer Hierarchie erweitern und noch einmal das Objekt "Mondkalender Modul erweitern", sehen mehrere untergeordnete Objekte Sie, die ein Material, das Namen "röntgenansicht". Das "x-ray" Material ermöglicht eine etwas lichtdurchlässiger Farbe ab, die als Hinweise für Platzierung für den Benutzer verwendet wird. 

![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) es gibt fünf Teile an das Mondkalender-Modul an, die der Benutzer interagieren, wie in der folgenden Abbildung gezeigt:

1.  Das Gehäuse Rover
2.  Der Treibstofftank
3.  Der Energieverbrauch-Zelle
4.  Das Portal Andocken 
5.  Der externe sensor

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> Hinweis: Die spielobjekt-Namen, die Sie in Ihrer szenenhierarchie Basis sehen entsprechen nicht den Namen der Objekte in der Szene.

Schritt 2: Fügen Sie eine audio Source Mondkalender Modul hinzu. Stellen Sie sicher, dass das Mondkalender-Modul in Ihrer szenenhierarchie Basis ausgewählt ist, und klicken Sie auf "Komponente hinzufügen". Suchen Sie nach "Audio Source", und fügen Sie es auf das Objekt hinzu. Lassen Sie es leer unverändert. Wir verwenden diese starten später wiedergegeben.
 ![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) Schritt 3: Fügen Sie das Skript "ein/aus der Platzierung-Hints". Klicken Sie auf "Komponente hinzufügen" und suchen Sie nach "Ein/aus der Platzierung-Hints". Dies ist ein benutzerdefiniertes Skript, das Sie zum Aktivieren und deaktivieren die lichtdurchlässiger Hinweise (mit dem x-Ray Material-Objekte), die zuvor erwähnten ermöglicht. 
![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) Schritt 4: Da wir 5 Objekte verfügen, geben Sie "5" für die Arraygröße spielobjekt. Klicken Sie dann sehen Sie 5 neue Elemente, die angezeigt werden. 

![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

Ziehen Sie jeden von lichtdurchlässigen Objekten in die Felder mit dem Text "None (Spielobjekt)". Ziehen Sie die folgenden Objekte aus dem Mondkalender-Modul in Ihrer Basis-Szene: 

• Rucksack

•   GasTank

• Topleftbody

• Nase

• LeftTwirler

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

Jetzt ist das Skript "Umschalten von Platzierung Hinweise" konfiguriert. Dies ermöglicht uns, aktivieren und deaktivieren Sie die Hinweise.

Schritt 5: Fügen Sie das Skript "Start Mondkalender-Modul" hinzu. Klicken Sie auf die Schaltfläche "Komponente hinzufügen", "Launch Mondkalender Modul" Suchen Sie, und wählen Sie ihn aus. Dieses Skript wird zum Starten des Moduls Mondkalender verantwortlich. Wenn wir eine konfigurierte Schaltfläche drücken, des Moduls Mondkalender rigidbody-Komponente wird ein nach oben Force hinzugefügt, und führt dazu, dass das Modul, um nach oben zu starten. In geschlossenen Räumen möchten, kann das Modul Mondkalender für das Gitter Ceiling abstürzen. Aber im freien möchten, es wird nach innen, Speicherplatz auf unbestimmte Zeit. 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

Schritt 6: Passen Sie die Schub so an, dass das Modul Mondkalender ordnungsgemäß up Above the wird. Versuchen Sie einen Wert von 0,01. Lassen Sie das Feld "Rb" leer. RB steht für die rigidbody und dieses Feld wird automatisch aufgefüllt werden, während der Laufzeit.

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>Übersicht über Abschnitte der Mondkalender-Modul
Das Mondkalender Modul Teile übergeordnete Objekt ist die Auflistung der Objekte, denen der Benutzer interagieren wird. Die spielobjekt-Namen (mit der Szene Namen in Paretheses bezeichnet) werden in der Liste unten bereitgestellt:

- Rucksack (Treibstofftank)
- GasTank (Energie Zelle)
- TopLeftBody (Rover Gehäuse)
- Nase (Andocken Portal)
- LeftTwirler (externe Sensor)

Beachten Sie, dass jedes dieser Objekte den Handler für die Bearbeitung, wie in Lektion 4 beschrieben. Mit den Handler für die Bearbeitung können Benutzer das Objekt zu erfassen. Beachten Sie, dass die Einstellung "zwei übergeben Manipulation-Type", auf "verschieben und drehen festgelegt ist" Dies ermöglicht nur den Benutzer verschieben Sie das Objekt und seine Größe, die die gewünschte Funktionalität für eine Anwendung für die Assembly ist nicht zu ändern.
Darüber hinaus ist weit Bearbeitung deaktiviert ist, können nur für direkte Interaktion von Teilen des Moduls.

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

Das Teil Assembly-Demo-Skript (siehe oben) ist das Skript, das die Objekte an das Modul Mondkalender platziert werden, durch den Benutzer verwaltet. 

Das Feld "Ort für Objekt" ist die Transformation, die ausgewählte (n die Groß-/Kleinschreibung der Abbildung oben, dem Rucksack/Tank) mit dem Objekt hergestellt werden kann. 

Die Einstellungen für "In der Nähe Distance" und "Weit" Distance "sind zuständig für das Ermitteln der Nähe, die Teile werden an Stelle ausgerichtet oder freigegeben werden. Beispielsweise müssen dem Rucksack/Tank 0,1 Einheiten außerhalb des Moduls Mondkalender platziert werden. Die "weit Distance" legt fest, den Speicherort, in dem das Objekt aus dem Modul Mondkalender getrennt werden muss. In diesem Fall muss des Benutzers dem Rucksack/Tank abrufen und per Pullvorgang 0,2 Einheiten von Moduls Mondkalender aus Einrasten wieder entfernen.

Das Objekt"Tip-Tool" ist die Tool-QuickInfo-Bezeichnung in der Szene. Wenn die Objekte an Stelle ausgerichtet sind, wird die Bezeichnung deaktiviert. 

Die Audio-Quelle wird automatisch verwendet werden. 

### <a name="placement-hints-buttons"></a>Platzierung Hinweise Schaltflächen
In [Lektion 2](mrlearning-base-ch2.md), haben Sie gelernt, platzieren, und konfigurieren die Schaltflächen bereit, führen z.B. Ändern der Farbe eines Elements oder wählen sie einen Sound wiederzugeben, wenn sie per Push übertragen wird. Wir werden weiterhin diese Prinzipien zu verwenden, wie wir unsere Schaltflächen zum Umschalten der Platzierung Hinweise konfigurieren. 

Das Ziel ist unsere Schaltfläche so konfigurieren, dass jedes Mal, wenn der Benutzer die Platzierung Hinweis drückt, wird es Sichtbarkeit von lichtdurchlässiger Platzierung Hinweise umzuschalten. 

Schritt 1: Verschieben Sie das Modul Mondkalender auf den leeren "nur Runtime"-Slot im Bedienfeld "Inspector", während der Platzierung Hinweise-Objekt in Ihrer szenenhierarchie Basis ausgewählt ist. 
 ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) Schritt 2: Klicken Sie nun auf die Dropdownliste, in dem Name schon sagt, "keine Funktion." Wechseln Sie zu "TogglePlacementHints" und befindet sich in diesem Menü Wählen Sie "ToggleGameObjects ()". ToggleGameObjects() wird die Platzierung Hinweise ein-und ausschalten, damit sie ein- oder ausgeblendet sind, jedes Mal, wenn die Schaltfläche gedrückt wird.
 ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>Konfigurieren die Schaltfläche "Zurücksetzen"

Es kann Situationen geben, in denen der Benutzer ist, einen Fehler oder versehentlich auslöst, die das Objekt entfernt, oder auch einfach möchte die Erfahrung rest. Die Schaltfläche "Zurücksetzen" wird die Möglichkeit, starten Sie die Umgebung neu hinzugefügt. 

Schritt 1: Wählen Sie die Schaltfläche "Zurücksetzen". In der Basis-Szene heißt es "ResetRoundButton." 

Schritt 2: Ziehen Sie das Mondkalender-Modul aus der szenenhierarchie der Basis der in das leere Einschubfach aus, klicken Sie unter "aktivierte Schaltfläche" im Bereich der Eigenschaftenanalyse.
 ![Lesson6 Kapitel4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

Schritt 3: Wählen Sie im Dropdownmenü die Fehlermeldung "keine Funktion", und zeigen Sie auf "LaunchLunarModule." Wählen Sie jetzt "ResetModule ()".

![Lesson6 Kapitel4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> Hinweis: Sie werden feststellen, dass standardmäßig die "GameObject.BroadcastMessage" konfiguriert ist, um "ResetPlacement." Dadurch wird eine Meldung, die Namen "ResetPlacement" für alle untergeordneten Objekte RocketLauncher_Tutorial zu senden. Jedes Objekt, das eine Methode für "ResetPlacement()" hat reagiert auf diese Nachricht, wenn die jeweilige Position zurücksetzen. 

### <a name="launching-the-lunar-module"></a>Starten das Modul Mondkalender
In diesem Kapitel, die wir die Schaltfläche "Start" konfigurieren. Dies ermöglicht den Benutzer, klicken auf die Schaltfläche, und starten das Modul Mondkalender in den Speicherplatz.

Schritt 1: Wählen Sie die Schaltfläche "Start" (in der Szene Basis sie heißt "LaunchRoundButton"). Ziehen Sie das Modul Mondkalender in das leere Einschubfach aus, klicken Sie unter "End Touch" im Bedienfeld "Inspector".
 ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) Schritt 2: Wählen Sie im Dropdownmenü die Fehlermeldung "keine Funktion." Zeigen Sie auf "LaunchLunarModule", und wählen Sie "StopThruster ()". Dies hat Vorrang, wie viel Schub möchte, dass der Benutzer auf das Modul Mondkalender zu gewähren. 
 ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) Schritt 3: Fügen Sie unter "ButtonPressed()" das Mondkalender-Modul (klicken Sie auf, halten und ziehen Sie), um das leere Einschubfach aus. 

Schritt 4: Klicken Sie auf das Dropdownmenü, aus der hervorgeht, "keine Funktion", zeigen Sie auf "LaunchLunarModule", und wählen Sie "StartThruster ()". 
 ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) Schritt 5: Fügen Sie Musik an das Modul Mondkalender, sodass bei der Rocket höhenflug, Musik spielen wird. Ziehen Sie zu diesem Zweck das Mondkalender-Modul, das nächste leere Einschubfach aus, klicken Sie unter "Schaltfläche Pressed()".

Schritt 6: Wählen Sie im Dropdownmenü die Fehlermeldung "keine Funktion", zeigen Sie auf "AudioSource", und wählen Sie "PlayOneShot (AudioClip)". Untersuchen die Vielzahl von Sounds in der MRTK enthalten können. In diesem Beispiel werden wir bleiben Sie mit "MRTK_Gem."
 ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>Herzlichen Glückwunsch! 
Sie haben diese Anwendung vollständig konfiguriert. Nun, wenn Sie auf "Play" klicken, können Sie vollständig Moduls Mondkalender zusammenstellen, Hinweise zu wechseln, starten Sie das Modul Mondkalender, und setzen sie ganz von vorn erneut tun.
