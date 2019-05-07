---
title: MR-Learning-Basis-Modul – 3D-Objekt Interaktion
description: Führen Sie diesen Kurs erfahren, wie Sie Azure-Gesichtserkennung innerhalb einer mixed Reality-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Gemischte Realität, Unity, Tutorial, hololens
ms.openlocfilehash: 344b3bc892839bc22445e10af644771bc7008ac3
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929582"
---
# <a name="mr-learning-base-module---3d-object-interaction"></a>MR-Learning-Basis-Modul – 3D-Objekt Interaktion

In dieser Lektion werden wir grundlegende-3D-Inhalte und benutzerfreundlichkeit durchlaufen. Wir erfahren, wie auf die 3D-Objekte als Teil einer Auflistung zu organisieren, erfahren Sie mehr über die umgebenden Felder für die einfache Manipulation, erfahren Sie mehr über die Interaktion für nah und fern, und erfahren Sie mehr über Touch und Abrufen von Bewegungen mit manuell nachverfolgen. 

## <a name="objectives"></a>Ziele

* Erfahren Sie, wie Sie mithilfe MRTKs Raster Objektauflistung-3D-Inhalte organisieren
* Implementieren, die umgebenden Felder
* Konfigurieren Sie 3D-Objekte für grundlegende Bearbeitung ("verschieben, drehen," und "Skalieren")
* Erkunden Sie nah und Fern Interaktion
* Erfahren Sie mehr über zusätzliche manuell Nachverfolgen von Gesten wie Ziehpunkte und Toucheingabe

## <a name="instructions"></a>Anweisungen

### <a name="organizing-3d-objects-in-a-collection"></a>Organisieren von 3D-Objekten in einer Auflistung

1. Klicken Sie mit der rechten Maustaste auf Ihre Hierarchie und wählen Sie aus, "erstellen Sie leere." Dadurch wird einem leeren spielobjekt erstellt. Benennen Sie sie in "3DObjectCollection." Dies ist, an dem wir alle unsere 3D-Objekte abgelegt wird. Stellen Sie sicher, Positionierung der Auflistung festgelegt ist, bei X = 0, y = 0 und Z = 0.

![Lesson4 Chapter1 Step1im](images/Lesson4_Chapter1_step1im.PNG)

2. Importieren Sie BaseModule Assets mit beschrieben, die die gleichen Anweisungen zum Importieren von benutzerdefinierter Paketen in [Lektion 1](mrlearning-base-ch1.md). Die BaseModule-Ressourcen umfassen 3D Module und andere nützliche Skripts, die im gesamten Tutorial verwendet werden. Die BaseModule Unity-Pakets finden Sie hier: <https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1>

3. Die Tasse Kaffee prefab kann von ein blauer Würfel daneben erkannt werden. Aktivieren Sie nicht die Tasse Kaffee mit blauer Würfel und kleine Whitepaper (die das ursprüngliche 3D-Modell und nicht auf das Prefab bezeichnet.) 

![Lesson4 Chapter1 Noteaim](images/Lesson4_chapter1_noteaim.PNG)

4. Ziehen Sie den Kaffee Cup Prefab Ihrer Wahl in das spielobjekt "3DObjectCollection" aus Schritt 1 ein. Die Tasse Kaffee ist jetzt ein untergeordnetes Element der Auflistung.

![Lesson4 Chapter1 Step4ima](images/Lesson4_chapter1_step4ima.PNG)

5. Als Nächstes fügen wir Weitere 3D-Objekte in unsere Szene. Es folgt eine Liste von Objekten müssen, die in diesem Beispiel fügen wir. Wenn Sie die Objekte hinzufügen möglicherweise, dass sie in Ihrer Szene in unterschiedlichen Größen angezeigt werden. Passen Sie die Skalierung der einzelnen 3D-Modell unter der Einstellung "Transformieren" in den Bereich der Eigenschaftenanalyse. Empfohlene Anpassungen in diesem Beispiel werden mit den Objekten, die unten aufgeführt. Suchen Sie in das Suchfeld in Ihr Projektpanel diese Wörter ein, und ziehen Sie das 3D-Objekt Prefab in das "3DObjectCollection"-Objekt ähnelt dem vorherigen Schritt. Diese Auflistung von prefabs (Vorlagen) finden Sie im Bestand > BaseModuleAssets > Base Modul prefabs (Vorlagen)
- Suchen Sie nach "TheModule_BaseModuleIncomplete." Ziehen Sie in der Szene. Die Skalierungsgruppe auf X = 0,03, y = 0,03, Z = 0,03. 
- Suchen Sie nach "Octa_BaseModuleIncomplete." Ziehen Sie in der Szene. Die Skalierungsgruppe auf X = 0.13. y = 0.13, z =0.13.
- Suchen Sie nach "EarthCore_BaseModuleIncomplete." Ziehen Sie in der Szene. Die Skalierungsgruppe auf X = 50,0 y = 50,0, Z = 50,0.
- Suchen Sie nach "Cheese_BaseModuleIncomplete." Ziehen Sie in der Szene. Die Skalierungsgruppe auf X = 0,05, y = 0,05, Z = 0,05.
- Suchen Sie nach "Model_Platonic_BaseModuleIncomplete." Ziehen Sie in der Szene. Die Skalierungsgruppe auf X = 0.13, y = 0.13, Z = 0.13.
- Suchen Sie nach "CoffeeCup_BaseModuleIncomplete." Ziehen Sie in der Szene.

![Lesson4 Chapter1 Step5im](images/Lesson4_Chapter1_step5im.PNG)

6. Fügen Sie Ihrer Szene mit 3 Cubes. Klicken Sie mit der rechten Maustaste auf das Objekt "3DObjectCollection", wählen Sie "3D Object", und wählen Sie dann "Cube". Die Skalierungsgruppe auf X = 0,14, y = 0,14 und Z = 0,14. Wiederholen Sie diesen Schritt 2 weitere Male, um insgesamt 3 Cubes zu erstellen. Alternativ können Sie den Cube zwei Mal für einen Zeitraum von 3 Cubes duplizieren. Sie können auch mit den drei vorbereiteten Cube Prefabs aus Medienobjekten > BaseModuleAssets > Base Modul prefabs (Vorlagen), und wählen GreenCube_BaseModuleIncomplete BlueCube_BaseModuleIncomplete und OrangeCube_BaseModuleIncomplete.

![Lesson4 Chapter1 Step6im](images/Lesson4_Chapter1_step6im.PNG)

7. Organisieren Sie Ihre Sammlung von Objekten, die ein Raster mit dem Verfahren in bilden [Lektion 2](mrlearning-base-ch2.md) mithilfe der MRTKs Grid-Objekt-Auflistung. Finden Sie in der Abbildung unten ist ein Beispiel zum Konfigurieren der Objekte in einem 3 x 3-Raster angezeigt.

![Lesson4 Chapter1 Notebim](images/Lesson4_chapter1_notebim.PNG)

>Hinweis: Sie können feststellen, dass einige Objekte nicht zentriert, z. B. die Objekte in der Abbildung oben sind. Dies ist da Prefabs oder Objekte untergeordneten Objekten verfügen können, die nicht ausgerichtet sind. Objekt Positionen oder untergeordneten Objekt Positionen einer ordnungsgemäß ausgerichteten Grid erzielen erforderlichen Anpassungen vornehmen können.


### <a name="manipulating-3d-objects"></a>Bearbeiten von 3D-Objekten
1. Fügen Sie die Möglichkeit, einen Cube zu ändern. Um die Möglichkeit zum Bearbeiten von 3D-Objekten hinzuzufügen gehen Sie folgendermaßen vor:
-   Wählen Sie das 3D-Objekt, die, das Sie bearbeiten, in der Hierarchie (in diesem Beispiel eines Cubes möchten).
-   Klicken Sie auf "Komponente hinzufügen" aus. 
-   Suchen Sie nach "Bearbeiten".
-   Wählen Sie "Manipulation von Handler".
-   Wiederholen Sie diesen Schritt für alle 3D-Objekte unter das Objekt "3DObjectCollection", aber nicht die "3DObjectCollection" selbst.
-   Stellen sicher, dass alle 3D-Objekte ein "collider" oder das Feld "collider" (Komponente hinzufügen > im Feld "collider").

![Lesson4 Chapter2 Step1im](images/Lesson4_chapter2_step1im.PNG)

>Der Handler für die Bearbeitung ist eine Komponente, mit denen Sie Einstellungen anpassen, Objekte wie das Verhalten bei bearbeitet wird. Dies schließt die Drehung, Skalierung, verschieben und einschränkende datenverschiebung auf bestimmten Achsen. 

2. Schränken Sie einen Cube aus, sodass es nur skaliert werden kann. Wählen Sie einen Cube, in dem Objekt "3DObjectCollection". Klicken Sie im Bereich Inspektor neben "zwei übergeben Manipulation-Typ," klicken Sie auf das Dropdownmenü, und wählen Sie "Skalieren". Dies erleichtert, damit der Benutzer nur die Größe des Cubes ändern kann.

![Lesson4 Chapter2 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. Ändern Sie die Farbe der einzelnen Cubes, sodass wir voneinander unterscheiden zu können. 
-   Wechseln Sie zu der Projektbereich, und scrollen Sie nach unten, bis Sie finden Sie unter "MixedRealityToolkit.SDK", und wählen Sie diese.
-   Wählen Sie den Ordner "Standard Assets".
-   Klicken Sie auf den Ordner "Materialien".
-   Ziehen Sie die verschiedenen Material auf einzelnen Cubes. 

>Hinweis: Sie können eine beliebige Farbe auswählen, für Ihre Cubes. In unserem Beispiel sind wir verwenden "Glowingcyan", "Glowingorange", und "Grün". Können Sie experimentieren mit unterschiedlichen Farben dargestellt. Um die Farbe für den Cube hinzuzufügen, klicken Sie auf den Cube, dem Sie die Farbe ändern möchten, und ziehen Sie dann das Material auf die Mesh-Renderer Material Feld im Inspektor-Bereich des Cubes. 

![Lesson4 Chapter2 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. Wählen Sie einen anderen Cube, in dem Objekt "3DObjectCollection", und legen Sie sie mit der Option, damit ihre Bewegung von der Spitze der Entfernung, Korrektur beschränkt ist. Klicken Sie auf der rechten Seite von "-Einschränkung für die datenverschiebung" dazu, klicken Sie auf das Dropdownmenü, und wählen Sie "repariert Abstand von der Spitze". Dies erleichtert, damit der Benutzer nur den Cube in ihre Sichtfeld wechseln kann. 

![Lesson4 Chapter2 Step4im](images/Lesson4_chapter2_step4im.PNG)

Ziel von den folgenden Schritten: Wir können Ziehpunkte sowie die Interaktion mit unserem 3D-Objekte. Wir werden verschiedene Manipulation-Einstellungen anwenden. 

5. Wählen Sie die Käse-Objekt, und klicken Sie im Bereich mit den Inspektor auf "Komponente hinzufügen" aus. 

6. Suchen Sie nach "In der Nähe von Interaktion Grabbable" in das Suchfeld ein, und wählen Sie das Skript. Diese Komponente ermöglicht Benutzern, wenden Sie sich, und ziehen Sie die Objekte mit nachverfolgten Hand. Objekte werden ebenfalls ermöglicht werden, aus der Ferne bearbeitet werden, wenn das Kontrollkästchen "Zulassen weit Manipulation" deaktiviert ist (gekennzeichnet durch grüner Kreis in der Abbildung unten).

![Lesson4 Chapter2 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. Fügen Sie hinzu "In der Nähe von Interaktion Grabbable" die Octa Objekt Platonic-Objekt, Earth Core, Mondkalender-Modul und Kaffee Cup durch wiederholen Schritt 5 und 6 für diese Objekte.

8. Entfernen Sie die Möglichkeit der Bearbeitung von weit aus dem Octa-Objekt. Klicken Sie zu diesem Zweck wählen Sie in der Hierarchie der Octa, und deaktivieren Sie das Kontrollkästchen "weit Bearbeitung zulassen" (gekennzeichnet durch ein grüner Kreis). Dies erleichtert, damit Benutzer nur mit der direkt mit nachverfolgten Hände Octa interagieren können.

>Hinweis: Die vollständige Dokumentation für die Manipulation-Handler-Komponente, und sie die Einstellungen zugeordnet sind, finden Sie in der [MRTK Dokumentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html).

9. Stellen Sie sicher, dass die Komponente "In der Nähe von Interaktion Grabbable" den Kern der Erde, das Mondkalender-Modul und die Tasse Kaffee hinzugefügt wurde (siehe Schritt 7).

10. Für das Modul Mondkalender ändern Sie die Manipulation-Handler-Einstellungen, damit es über Center für beide in der Nähe des Objekts und die ganz Interaktion, dreht, wie in der folgenden Abbildung dargestellt.

![Lesson4 Chapter2 Step10im](images/Lesson4_chapter2_step10im.PNG)

11: Ändern Sie für die Erde-Core, das Version-Verhalten, das "nichts". Dies erleichtert, damit nach der Erde Kern aus der Benutzer verstehen freigegeben wird, weiterhin nicht verschieben. 

![Lesson4 Chapter2 Step11im](images/Lesson4_Chapter2_step11im.PNG)

> Hinweis: Diese Einstellung ist nützlich für Szenarien, z. B. das Erstellen einer Kugel, die Sie auslösen können. Halten die Geschwindigkeit und die Winkelgeschwindigkeit erleichtert, sobald der Ball veröffentlicht, ist diese weiterhin mit der Geschwindigkeit zu verschieben, dass es war am veröffentlichten, ähnlich wie ein physischer Ball verhält.

### <a name="adding-bounding-boxes"></a>Hinzufügen von umgebenden Felder
Umgebende Felder machen es einfacher und intuitiver zum Bearbeiten von Objekten mit einer Hand für direkte Bearbeitung (in der Nähe Interaktion) und Chow basierende Manipulation (ganz Interaktion.) Umgebende Felder bieten "Handles", die für die Skalierung und Drehen von Objekten an bestimmten Achsen verwendet werden können.
>Hinweis: Bevor Sie ein umgebendes Feld auf ein Objekt hinzufügen können, die müssen Sie zuerst müssen ein "collider" für das Objekt (z. B. einen Box-Collider.) Wie schon zuvor in dieser Lektion. Collider können hinzugefügt werden, indem Sie das Objekt auswählen, und klicken Sie im Inspektor-Bereich des Objekts Auswahl der Komponente hinzufügen > Box-Collider.
>

1. Der Erde-Core-Objekt, einen Box-Collider hinzugefügt, wenn eine (Box-Collider und Setup nicht erforderlich, wenn das Prefab in Base-Modul Ordner "Assets", gemäß den Anweisungen angegebenen bereitgestellten verwenden.) noch nicht vorhanden ist Im Fall der Erde-Core müssen wir das Objekt "node_id30" unterhalb der Erde-Core, die Box-Collider hinzugefügt, wie in der folgenden Abbildung dargestellt. Wählen Sie node_id30 aus, und klicken Sie auf der Registerkarte "Inspector" des Objekts, "Komponente hinzufügen", und suchen Sie nach "" collider "box." 

![Lesson4 Chapter3 Step1im](images/Lesson4_Chapter3_step1im.PNG)

![Lesson4 Chapter3 Step2im](images/Lesson4_chapter3_step2im.PNG)

> Hinweis: Stellen Sie sicher, dass Sie die Box-Collider visualisieren, so, dass es nicht zu groß oder klein. Es sollte ungefähr die gleiche Größe wie das Objekt sein, die sie (in diesem Beispiel ist der Kern der Erde) umgeben ist. Passen Sie die Box-Collider, je nach Bedarf durch Auswahl der Option "Bearbeiten" collider "" in der Box-Collider. Sie können entweder eine Änderung der x-, y- und Z-Werte, oder ziehen Sie die umschließende Box-Handler in der Szene-Editor-Fenster. 

![Lesson4 Chapter3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. Fügen Sie ein umgebendes Feld auf der Erde Kernobjekt "node_id30" hinzu. Zu diesem Zweck wählen Sie das "node_id30"-Objekt, aus der "3DObjectCollection". Klicken Sie in der Registerkarte "Inspector" klicken Sie auf "Komponente hinzufügen", und suchen Sie nach "umgebendes Feld." Stellen Sie sicher, dass die umgebende Feld, Box-Collider und Manipulation-Skripts (Manipulation-Handler, in der Nähe von Interaktion grabbable) auf das gleiche spielobjekt sind.

3.  Wählen Sie im Abschnitt "Verhalten" das umgebende Feld "im Startmenü aktivieren" aus der Dropdownliste für die Aktivierung. Um weitere Details in Bezug auf die verschiedenen Aktivierungsoptionen und andere Optionen des umschließenden überprüfen zu können, finden Sie unter den [MRTK umgebende Feld-Dokumentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)

   

   *In den nächsten Schritten werden wir auch ändern, wie das umgebende Feld aussieht, durch Anpassen der Standardmaterial Feld, das Material, während es Element aktuell erfasst wird, sowie die Visualisierung von Handles (Ecken und Handles). Die MRTK enthält mehrere Optionen zum Anpassen des umgebenden Felds an.*

4. Im Projektfenster sehen suchen Sie nach "Boundingbox", und Sie eine Liste der Materialien, die durch eine blaue Kugel in den Suchergebnissen angezeigt wird, gekennzeichnet, wie in der folgenden Abbildung dargestellt. 

5. Ziehen Sie das Material "Boundingbox" in das Feld Material Einschubfach auf die umschließende Box-Komponente. Außerdem ziehen Sie das Material "Boundingboxgrabbed", und legen Sie, die auf die umschließende Box-Komponente in der Box grabbed Material-Slot.

6. Ziehen Sie das Material "MRTK_BoundingBox_ScaleWidget" in der Skalierungsgruppe Handle prefab-Slot auf die umschließende Box-Komponente. 

7. Ziehen Sie das Material "MRTK_BoundingBox_RotateWidget" in das Einschubfach des Drehung Handle-Komponente der Verbindung.

![Lesson4 Chapter3 Schritt 4 7Im](images/Lesson4_chapter3_step4-7im.PNG)

8. Stellen Sie sicher, dass das umgebende Feld, das rechte Objekt ausgerichtet ist. In der umgebenden Feld-Komponente besteht die "Zielobjekt" und die Skripts "umschließt außer Kraft setzen". Stellen Sie sicher, dass das Objekt ziehen, das das umgebende Feld, um es herum sowohl dieser Slots verfügt. Ziehen Sie in diesem Beispiel das Objekt "node_id30" in beiden Slots diese, wie in der folgenden Abbildung dargestellt.

> Beim Starten oder die Anwendung spielen, wird das Objekt jetzt einen blauen Rahmen eingeschlossen werden. Sie können die Ecken des Frames, die Größe eines Objekts zu ziehen. Wenn der Skalierung behandelt und die Drehpunkte um größer und besser sichtbar sein soll, empfehlen wir die Verwendung der Standardwert umschließende Box-Einstellungen (vermeiden Schritte 4 bis 7). 

![Lesson4 Chapter3 Step8im](images/Lesson4_Chapter3_step8im.PNG)

9. Zurück auf den Standardwert umgebendes Feld Visualisierung im Bereich "Inspector" des Objekts für das umgebende Feld, wählen Sie die Rotation Handle Prefab und die ENTF-Taste drücken, sehen Sie jetzt eine umgebende Feld Visualisierung, die ähnlich wie in der folgenden Abbildung. Hinweis: die umgebende Feld Visualisierungen wird nur angezeigt im Play-Modus.

![Lesson4 Chapter3 Step9im](images/Lesson4_chapter3_step9im.PNG)

### <a name="adding-touch-effects"></a>Hinzufügen von Touch-Effekte
In diesem Beispiel werden wir einen Soundeffekt wiedergegeben wird, wenn Sie ein Objekt mit der Hand berühren.

1. Fügen Sie Ihrem spielobjekt eine audio Source-Komponente hinzu. Wählen Sie das "Octa"-Objekt, in der szenenhierarchie. Im Bereich mit den Inspektor klicken Sie auf die Schaltfläche "Komponente hinzufügen", suchen Sie nach, und wählen Sie "audio Source". Wir verwenden diese Audioquelle Soundeffekt in einem späteren Schritt zu spielen. 

>Hinweis: Stellen Sie sicher, dass das Objekt "Octa" einen Box-Collider verfügt.

2. Fügen Sie die Komponente "in der Nähe der Interaktion touchable" hinzu. Klicken Sie auf die Schaltfläche "Komponente hinzufügen" im Inspektor-Bereich und suchen Sie nach "beinahe Interaktion touchable." Wählen sie die Komponente hinzufügen. Hinweis: Korrigieren Sie Screenshot hervorzuheben, dass wir die Komponente hinzuzufügen, und nicht nur Box-Collider Hervorhebung.

>Hinweis: Zuvor haben wir hinzugefügt "nahe Interaktion grabbable." Der Unterschied zwischen diesem und dem "in der Nähe der Interaktion touchable" ist, dass die "grabbable" Interaktion vorgesehen ist, für ein Objekt in Ruhe und mit Ihnen zu interagieren. Die Komponente "touchable" richtet sich das Objekt, das berührt werden. Beide Komponenten können für eine Kombination von Aktivitäten, die zusammen verwendet werden.

![Lesson4 Kapitel4 Step1 2Im](images/Lesson4_chapter4_step1-2im.PNG)

3. Fügen Sie das Skript "übergeben, Interaktion Touch" hinzu. Beachten Sie, dass dieses Skript in der Unity-Szene enthalten ist, die Sie als Teil dieses Demopaket importiert, und es ist nicht in der ursprünglichen MRTK enthalten. Nur wie im vorherigen Schritt klicken Sie auf "Komponente hinzufügen", und suchen Sie nach "Hand Interaktion Touch" hinzugefügt. 
   Beachten Sie, dass Sie 3 Optionen mit dem Skript: 

   - "On Touch abgeschlossen." Dadurch wird ausgelöst, wenn Sie touch und das Objekt frei. 
   - "Für touch wurde gestartet." Dadurch wird ausgelöst, wenn das Objekt berührt wird. 
   - "On Touch aktualisiert." Dadurch wird in regelmäßigen Abständen ausgelöst, während Ihre Hand auf das Objekt berührt wird. 

   In diesem Beispiel arbeiten wir mit der Einstellung "auf Fingereingabe, die gestartet werden".

4. Klicken Sie auf die Schaltfläche "+", auf die Option "ein Touch gestartet", wie in der folgenden Abbildung dargestellt. Ziehen Sie das Octa-Objekt in das leere Feld ein. 

5. Wählen Sie in der Dropdownliste die Fehlermeldung "keine Funktion" (über grüne Rechteck in der Abbildung unten), AudioSource > PlayOneShot. Fügen wir einen Audioclip hinzu dieses Feld mit den folgenden Konzepten:

   - Die MRTK bietet eine kleine Liste von Audioclips. Diese in Ihr Projektpanel untersuchen können. Sie finden sie unter dem Ordner "MixedRealityToolkit.SDK" und klicken Sie dann den Ordner "standard Assets". Es sehen Sie, einen Ordner mit "audio", in denen die Audioclips sind.
   - In diesem Beispiel werden wir den "MRTK_Gem" Audioclip zu verwenden. 
   - Um einen Audioclip hinzuzufügen, ziehen Sie einfach die gewünschten Clip aus dem Projektfenster in die AudioSource.PlayOneShot (gekennzeichnet durch die grüne Feld im obigen Beispiel) im Bedienfeld "Inspector".

   Wenn der Benutzer sich wendet und das Octa Objekt berührt, wird jetzt die Audiospur "MRTK_Gem" wiedergegeben. Das Skript "Hand Interaktion Touch" wird auch die Farbe des Objekts, wenn bearbeitete anpassen. 

![Schritt 3 Lesson4-Kapitel4 5 Noteim](images/Lesson4_chapter4_step3-5-noteim.PNG)

### <a name="congratulations"></a>Herzlichen Glückwunsch! 
In dieser Lektion haben Sie gelernt, wie Sie 3D-Objekte in einer Auflistung Raster zu organisieren und zum Bearbeiten von 3D-Objekten (skalieren, drehen und verschieben) verwenden, die in der Nähe von Interaktion, die (direkt mit nachverfolgten Hand abrufen) und weit Interaktion (mit Blicke Strahlung oder manuell Strahlung.) Außerdem haben Sie gelernt Begrenzungsrahmen um 3D-Objekte zu platzieren und haben gelernt, wie zum verwenden und Anpassen der Gizmos auf die umgebenden Felder. Schließlich haben Sie Gewusst wie: Auslösen der Ereignisse aus, wenn ein Objekt berührt.

[Nächste Lektion: Erweiterte Eingabe](mrlearning-base-ch5.md)

