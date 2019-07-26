---
title: Basismodul zum MR-Lernen – 3D-Objektinteraktion
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 314af3e1e38e1698943f07dc32f5e1e3e2f36d4f
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485703"
---
# <a name="5-interacting-with-3d-objects"></a>5. Interagieren mit 3D-Objekten

In diesem Tutorial erfahren Sie mehr über grundlegende 3D-Inhalte und-Benutzeroberflächen. Weitere Informationen finden Sie hier: 
* Organisieren von 3D-Objekten als Teil einer Auflistung.
* Begrenzungs Felder für die grundlegende Bearbeitung.
* Near-und Far-Interaktion.
* Halten Sie sich mit Hand Nachverfolgung in Hand. 

## <a name="objectives"></a>Ziele

* Erfahren Sie, wie Sie 3D-Inhalte mit der Datenblatt Objekt Auflistung von mrtk organisieren.
* Implementieren von Begrenzungsrahmen
* Konfigurieren von 3D-Objekten für die grundlegende Bearbeitung: verschieben, drehen und Skalieren
* Erkunden von nahen und fernen Interaktionen
* Weitere Informationen zu weiteren Hand nach Verfolgungs Gesten, z. b. zum Erfassen und berühren

## <a name="instructions"></a>Anweisungen

### <a name="organizing-3d-objects-in-a-collection"></a>Organisieren von 3D-Objekten in einer Sammlung

1. Klicken Sie mit der rechten Maustaste auf ihre Hierarchie, und wählen Sie leere erstellen Dadurch wird ein leeres Spielobjekt erstellt. Benennen Sie Sie in 3dobjectcollection um. Hier werden alle unsere 3D-Objekte abgelegt. Stellen Sie sicher, dass die Positionierung der Sammlung auf „x = 0“, „y = 0“ und „z = 0“ eingestellt ist.

![Lektion4 Kapitel1 Schritt1im](images/Lesson4_Chapter1_step1im.PNG)

2. Importieren Sie basemodule-Assets, indem Sie die gleichen Anweisungen zum Importieren von benutzerdefinierten Paketen in [Lesson1](mrlearning-base-ch1.md)verwenden. Die basemodule-Assets enthalten 3D-Module und andere hilfreiche Skripts, die in diesem Tutorial verwendet werden. Das basemodule-Unity-Paket finden Sie hier:<https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1>

3. Das Kaffeetassen-Prefab ist an einem daneben befindlichen blauen Würfel zu erkennen. Wählen Sie nicht den Coffee Cup mit dem blauen Cube und kleinen Whitepaper aus, da dies das ursprüngliche 3D-Modell und nicht die vorfab angibt.) 

![Lektion4 Kapitel1 Noteaim](images/Lesson4_chapter1_noteaim.PNG)

4. Ziehen Sie die gewünschte Coffee Cup-vorfab aus Schritt 1 in das 3dobjectcollection-Spielobjekt. Die Kaffeetasse ist jetzt ein untergeordnetes Element der Sammlung.

![Lektion4 Kapitel1 Schritt4ima](images/Lesson4_chapter1_step4ima.PNG)

5. Als Nächstes fügen wir weitere 3D-Objekte zu unserer Szene hinzu. Nachfolgend finden Sie eine Liste der Objekte, die wir in diesem Beispiel hinzufügen werden. Wenn Sie die Objekte hinzufügen, stellen Sie möglicherweise fest, dass Sie in der Szene in unterschiedlichen Größen angezeigt werden. Passen Sie die Skalierung der einzelnen 3D-Modelle unter Transformations Einstellung im Inspektor-Panel an. Empfohlene Anpassungen in diesem Beispiel werden mit den Objekten, die unten aufgeführt. Durchsuchen Sie diese Wörter im Suchfeld im Projekt Panel, und ziehen Sie das 3D-Objekt vorfab in das 3dobjectcollection-Objekt, das dem vorherigen Schritt ähnelt. Diese Auflistungen von Prefabs finden Sie in Assets > basemoduleassets > Basismodul präfabs
- Suchen Sie nach TheModule_BaseModuleIncomplete. Ziehen Sie es in die Szene. Stellen Sie die Skalierung auf „x = 0,03“, „y = 0,03“, „z = 0,03“ ein. 
- Suchen Sie nach Octa_BaseModuleIncomplete. Ziehen Sie es in die Szene. Stellen Sie die Skalierung auf „x = 0,13“ ein. „y = 0,13“, „z = 0,13“.
- Suchen Sie nach EarthCore_BaseModuleIncomplete. Ziehen Sie es in die Szene. Stellen Sie die Skalierung auf „x = 50,0“, „y = 50,0“, „z = 50,0“ ein.
- Suchen Sie nach Cheese_BaseModuleIncomplete. Ziehen Sie es in die Szene. Stellen Sie die Skalierung auf „x = 0,05“, „y = 0,05“, „z = 0,05“ ein.
- Suchen Sie nach Model_Platonic_BaseModuleIncomplete. Ziehen Sie es in die Szene. Stellen Sie die Skalierung auf „x = 0,13“, „y = 0,13“, „z = 0,13“ ein.

![Lektion4 Kapitel1 Schritt5im](images/Lesson4_Chapter1_step5im.PNG)

6. Fügen Sie Ihrer Szene drei Cubes hinzu. Klicken Sie mit der rechten Maustaste auf das 3dobjectcollection-Objekt, wählen Sie 3D-Objekt und dann Cube aus. Stellen Sie die Skalierung auf „x = 0,14“, „y = 0,14“, „z = 0,14“ ein. Wiederholen Sie diesen Schritt zwei weitere Male, um insgesamt drei Cubes zu erstellen. Alternativ können Sie den Cube zweimal duplizieren, um insgesamt drei Cubes auszuführen. Sie können auch die drei vorbereiteten Würfel-Prefabs aus „Assets>BaseModuleAssets>Base Module Prefabs“ verwenden und „GreenCube_BaseModuleIncomplete“, „BlueCube_BaseModuleIncomplete“ und „OrangeCube_BaseModuleIncomplete“ auswählen.

![Lektion4 Kapitel1 Schritt6im](images/Lesson4_Chapter1_step6im.PNG)

7. Organisieren Sie Ihre Sammlung von Objekten unter Verwendung der MRTK-Rasterobjektsammlung zu einem Raster, wie in [Lektion 2](mrlearning-base-ch2.md) beschrieben. Die folgende Abbildung zeigt ein Beispiel für die Konfiguration der Objekte in einem 3x3-Raster.

![Lektion4 Kapitel1 Notebim](images/Lesson4_chapter1_notebim.PNG)

>Hinweis: Möglicherweise stellen Sie fest, dass einige der Objekte außerhalb des Centers sind, z. b. die Objekte in der obigen Abbildung. Dies liegt daran, dass Prefabs oder Objekte möglicherweise untergeordnete Objekte aufweisen, die nicht ausgerichtet sind. Sie können jederzeit alle notwendigen Anpassungen an den Positionen der Objekte oder Unterobjekte vornehmen, um ein ausgerichtetes Raster zu erhalten.


### <a name="manipulating-3d-objects"></a>Manipulieren von 3D-Objekten
1. Fügen Sie die Möglichkeit hinzu, einen Würfel zu manipulieren. Gehen Sie folgendermaßen vor, um die Möglichkeit zum Bearbeiten von 3D-Objekten hinzuzufügen:
-   Wählen Sie das 3D-Objekt aus, das Sie in Ihrer Hierarchie bearbeiten möchten, d. h. einen ihrer Cubes.
-   Klicken Sie auf Komponente hinzufügen. 
-   Suchen Sie nach Manipulation.
-   Bearbeitungs Handler auswählen.
-   Wiederholen Sie diesen Vorgang für alle 3D-Objekte unter dem 3dobjectcollection-Objekt, jedoch nicht für die 3dobjectcollection selbst.
-   Stellen Sie sicher, dass alle 3D-Objekte über einen Collider-oder Box-Konflikt verfügen (Komponente hinzufügen > Box Collider).

![Lektion4 Kapitel2 Schritt1im](images/Lesson4_chapter2_step1im.PNG)

>Der Manipulations Handler ist eine Komponente, mit der Sie Einstellungen für das Verhalten von Objekten anpassen können, wenn Sie manipuliert werden. Dies umfasst das Drehen, skalieren, verschieben und Einschränken der Bewegung auf einer bestimmten Achse. 

2. Schränken Sie einen Cube so ein, dass er nur skaliert werden kann. Wählen Sie einen Cube im 3dobjectcollection-Objekt aus. Klicken Sie im Inspektor-Panel neben zwei Hand Bearbeitungs Typen auf das Dropdown Menü, und wählen Sie skalieren. Dadurch kann der Benutzer nur die Größe des Würfels ändern.

![Lektion4 Kapitel2 Schritt2im](images/Lesson4_Chapter2_step2im.PNG)

3. Ändern Sie die Farbe der einzelnen Würfel, damit sie eindeutig unterschieden werden können. 
-   Wechseln Sie zum Projekt Panel, und Scrollen Sie nach unten, bis Sie mixedrealitytoolkit. SDK sehen, und wählen Sie es dann aus.
-   Wählen Sie den Ordner Standard Objekte aus.
-   Klicken Sie auf den Ordner Material.
-   Ziehen Sie ein anderes Material auf die einzelnen Würfel. 

>Hinweis: Sie können eine beliebige Farbe für Ihre Würfel auswählen. In unserem Beispiel verwenden wir glowingcyan, glowingorange und grün. Experimentieren Sie ruhig mit verschiedenen Farben. Um die Farbe zum Cube hinzuzufügen, klicken Sie auf den Cube, den Sie ändern möchten, und ziehen Sie dann das Material in das Material Feld des Mesh-Renderers im Inspektor-Panel des Cubes. 

![Lektion4 Kapitel2 Schritt3im](images/Lesson4_Chapter2_step3im.PNG)

4. Wählen Sie einen anderen Cube im 3dobjectcollection-Objekt aus, und legen Sie ihn so fest, dass die Bewegung auf eine festgelegte Entfernung vom Kopf beschränkt wird. Klicken Sie hierzu auf der rechten Seite der Einschränkung bei der Bewegungs Bezeichnung auf das Dropdown Menü, und wählen Sie Entfernung von der Kopfzeile korrigieren aus. Dadurch kann der Benutzer den Würfel nur innerhalb seines Sichtfelds bewegen. 

![Lektion4 Kapitel2 Schritt4im](images/Lesson4_chapter2_step4im.PNG)

Das Ziel der nächsten Schritte besteht darin, das erfassen und interagieren mit den 3D-Objekten und das Anwenden verschiedener Manipulations Einstellungen zu ermöglichen.

5. Wählen Sie das Käse Objekt aus, und klicken Sie im Inspektor-Panel auf Komponente hinzufügen. 

6. Suchen Sie im Suchfeld nach fast-Interaktion, und wählen Sie das Skript aus. Diese Komponente ermöglicht es Benutzern, Objekte mit nach verfolgten Händen zu erreichen und zu erfassen. Objekte können auch aus einer Entfernung bearbeitet werden, es sei denn, das Kontrollkästchen "lange Bearbeitung zulassen" ist deaktiviert, wie durch den grünen Kreis im Bild unten angegeben.

![Lektion4 Kapitel2 Schritt6im](images/Lesson4_Chapter2_step6im.PNG)

7. Fügen Sie dem Octa-Objekt, dem platonischen Objekt, dem Erdkern, dem Mond Modul und dem Coffee Cup fast-Interaktion hinzu, indem Sie die Schritte 5 und 6 für diese Objekte wiederholen.

8. Entfernen Sie die Möglichkeit zur fernen Manipulation aus dem Octa-Objekt. Wählen Sie hierzu die Octa in der Hierarchie aus, und deaktivieren Sie das Kontrollkästchen "lange Bearbeitung zulassen" (mit einem grünen Kreis gekennzeichnet). Dadurch ist es möglich, dass Benutzer nur mithilfe von nachverfolgten Händen direkt mit dem Octa-Objekt interagieren können.

>Hinweis: Die vollständige Dokumentation der Manipulationshandler-Komponente und ihrer zugehörigen Einstellungen finden Sie in der [MRTK-Dokumentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html).

9. Stellen Sie sicher, dass die abzurufende Komponente der Near-Interaktion der Erde Core, dem Lunar-Modul und dem Coffee Cup hinzugefügt wurde (siehe Schritt 7).

10. Ändern Sie für das Modul "Lunar" die Einstellungen des Manipulations Handlers so, dass es sich um den Mittelpunkt des Objekts für die Near-und Far-Interaktion dreht, wie in der folgenden Abbildung dargestellt.

![Lektion4 Kapitel2 Schritt10im](images/Lesson4_chapter2_step10im.PNG)

11: Ändern Sie für den Erdkern das Freigabe Verhalten in "Nothing". Dies bedeutet, dass nach der Veröffentlichung des Erdkerns durch den Benutzer die Verschiebung nicht fortgesetzt wird. 

![Lektion4 Kapitel2 Schritt11im](images/Lesson4_Chapter2_step11im.PNG)

> Hinweis: Diese Einstellung ist für bestimmte Szenarien nützlich, z. B. beim Erstellen eines Balls, den Sie werfen können. Wenn Sie die Geschwindigkeit und die Angular-Geschwindigkeit halten, wird Sie so gestaltet, dass Sie nach der Freigabe der Kugel weiterhin mit der Geschwindigkeit bewegt wird, in der Sie veröffentlicht wurde. Dies ähnelt der Art und Weise, wie sich ein physischer Ball verhält.

### <a name="adding-bounding-boxes"></a>Hinzufügen von Begrenzungsrahmen
Begrenzungsrahmen gestalten das Manipulieren von Objekten mit einer Hand einfacher und intuitiver, sowohl für die direkte Manipulation (Nah-Interaktion) als auch für die strahlenbasierte Manipulation (Fern-Interaktion). Begrenzungs Felder bieten Handles, die für das Skalieren und Drehen von Objekten auf einer bestimmten Achse gepackt werden können.
>Hinweis: Bevor Sie einem Objekt ein Begrenzungsfeld hinzufügen können, benötigen Sie zunächst einen Collider für das Objekt (z. b. einen Box-Collider), wie dies zuvor in dieser Lektion geschehen ist. Collider können hinzugefügt werden, indem Sie das Objekt auswählen und im Inspektorbereich des Objekts „Add Component > Box Collider“ (Komponente hinzufügen > Feld-Collider) auswählen.
>

1. Fügen Sie dem Erdkern Objekt einen Box-Collider hinzu, falls noch keiner vorhanden ist. Das Feld "Collider" und das Setup sind nicht erforderlich, wenn Sie die im Ordner "Base Module Assets" angegebene präfab gemäß den Anweisungen verwenden. Im Fall des Erdkerns haben wir das Feld "Collider" dem Objekt "node_id30" unterhalb des Erdkerns hinzugefügt, wie in der folgenden Abbildung dargestellt. Wählen Sie node_id30 auf der Registerkarte Inspektor des Objekts aus, klicken Sie auf Komponente hinzufügen, und suchen Sie nach Box Collider. 

![Lektion4 Kapitel3 Schritt1im](images/Lesson4_Chapter3_step1im.PNG)

![Lektion4 Kapitel3 Schritt2im](images/Lesson4_chapter3_step2im.PNG)

> Hinweis: Stellen Sie sicher, dass Sie die Größe des Box-Colliders so anpassen, dass er nicht zu groß oder zu klein ist. Es sollte ungefähr dieselbe Größe aufweisen wie das von ihm umgebene Objekt (in diesem Beispiel der Erdkern). Passen Sie das Feld "Collider" nach Bedarf an, indem Sie die Option "Collider bearbeiten" im Feld "unter" auswählen. Sie können entweder die x-, y-und z-Werte ändern oder die Begrenzungsfeld Handler im Editor-Szenen Fenster ziehen. 

![Lektion4 Kapitel3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. Fügen Sie dem node_id30-Objekt des Erdkerns ein Begrenzungsfeld hinzu. Wählen Sie hierzu das node_id30-Objekt aus der 3dobjectcollection aus. Klicken Sie auf der Registerkarte Inspektor auf Komponente hinzufügen, und suchen Sie nach dem umgebenden Feld. Stellen Sie sicher, dass sich Begrenzungsrahmen, Feld-Collider und Manipulationsskripts (Manipulationshandler, Nah-Interaction, greifbar) alle auf demselben Spielobjekt befinden.

3.  Wählen Sie im Abschnitt Verhaltens Bereich des umgebenden Felds in der Dropdown Liste Aktivierung die Option in Start aktivieren aus. Um weitere Details zu den verschiedenen Aktivierungsoptionen und anderen Optionen des Begrenzungsrahmens zu überprüfen, lesen Sie die MRTK-Dokumentation zum [Begrenzungsrahmen](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>).

   

   *In den nächsten Schritten ändern wir auch die Art und Weise, wie das umgebende Feld aussieht, indem wir das Standardfeld Material, das Material, während dieses gepackt wird, sowie die Visualisierung der Ecke und der Seiten Handles anpassen. Das MRTK enthält mehrere Optionen zum Anpassen des Begrenzungsrahmens.*

4. Suchen Sie im Projekt Panel nach BoundingBox, und Sie sehen eine Liste der Materialien, die in den Suchergebnissen durch eine blaue Kugel angezeigt werden, wie in der folgenden Abbildung dargestellt. 

5. Ziehen Sie das BoundingBox-Material in den boxmaterialslot der Begrenzungsfeld Komponente. Nehmen Sie auch das boundingboxgrab-Material, und platzieren Sie dieses in den einfügepackten Material Slot der umgebenden Box-Komponente.

6. Ziehen Sie die MRTK_BoundingBox_ScaleWidget Prefab in den Prefab-Slot des Skalierungs Handles der umgebenden Feld Komponente. 

7. Ziehen Sie den MRTK_BoundingBox_RotateWidget Prefab in den Steckplatz für das Drehfeld der Bindungs Feld Komponente.

![Lektion4 Kapitel3 Schritt4 7Im](images/Lesson4_chapter3_step4-7im.PNG)

8. Stellen Sie sicher, dass der Begrenzungsrahmen auf das richtige Objekt ausgerichtet ist. In der Komponente des umgebenden Felds gibt es das Zielobjekt und die Grenzen überschreiben Skripts. Achten Sie darauf, dass Sie das Objekt, das vom Begrenzungsrahmen umgeben ist, in diese beiden Bereiche ziehen. Ziehen Sie in diesem Beispiel das node_id30-Objekt in beide Slots, wie in der folgenden Abbildung dargestellt.

> Wenn Sie die Anwendung starten oder wiedergeben, wird das Objekt von einem blauen Rahmen umgeben. Sie können die Ecken dieses Rahmens ziehen, um die Größe des Objekts zu ändern. Wenn Sie möchten, dass die Skalierungs Handles und die Drehungs Handles größer und sichtbar sind, empfiehlt es sich, die Standardeinstellungen für Begrenzungs Felder zu verwenden (vermeiden Sie die Schritte 4 bis 7). 

![Lektion4 Kapitel3 Schritt8im](images/Lesson4_Chapter3_step8im.PNG)

9. Wenn Sie zur Standard Visualisierung für das umgebende Feld zurückkehren möchten, wählen Sie im Inspektor-Panel des-Objekts des umgebenden Felds die Prefab-vorfab aus, und drücken Sie ENTF. Es wird eine umgebende Feld Visualisierung angezeigt, die der Abbildung unten ähnelt. Hinweis: Die Darstellungen der Begrenzungsrahmen werden nur im Wiedergabemodus angezeigt.

![Lektion4 Kapitel3 Schritt9im](images/Lesson4_chapter3_step9im.PNG)

### <a name="adding-touch-effects"></a>Hinzufügen von Berührungs Effekten
In diesem Beispiel werden wir einen Soundeffekt wiedergeben, wenn Sie ein Objekt mit der Hand berühren.

1. Fügen Sie eine Audioquellenkomponente zu Ihrem Spielobjekt hinzu. Wählen Sie das Octa-Objekt in ihrer Szenen Hierarchie aus. Klicken Sie im Bereich Inspector auf die Schaltfläche Komponente hinzufügen, suchen Sie nach Audioquelle, und wählen Sie Sie aus. Wir werden diese Audioquelle verwenden, um in einem späteren Schritt einen Soundeffekt wiederzugeben. 

>Hinweis: Stellen Sie sicher, dass das Octa-Objekt über einen Box-Collider verfügt.

2. Fügen Sie die Berührungs fähige Komponente near Interaktion hinzu. Klicken Sie im Inspektor-Panel auf die Schaltfläche Komponente hinzufügen, und suchen Sie nach near Interaktion touchable. Wählen Sie diese Option aus, um die Komponente hinzuzufügen. 

>Hinweis: Zuvor haben wir nahezu Interaktion hinzugefügt. Der Unterschied zwischen dieser und Near Interaktion touchable besteht darin, dass die abzähl Bare Interaktion für ein Objekt vorgesehen ist, mit dem gesucht und interagiert werden soll. Die touchable-Komponente ist für das zu verwendende Objekt bestimmt. Beide Komponenten können zusammen für eine Kombination von Interaktionen verwendet werden.

![Lektion4 Kapitel4 Schritt1 2Im](images/Lesson4_chapter4_step1-2im.PNG)

3. Fügen Sie im Hand Interaktion-Fingereingabe Skript hinzu. Beachten Sie, dass dieses Skript in der Unity-Szene enthalten ist, die Sie im Rahmen dieser Demo importiert haben, und ist nicht im ursprünglichen mrtk enthalten. Klicken Sie wie im vorherigen Schritt auf Komponente hinzufügen, und suchen Sie nach "Hand Interaktion berühren", um Sie hinzuzufügen.

>Beachten Sie, dass Sie über drei Optionen für das Skript verfügen: 

>   - Nach Abschluss der Fingereingabe: Wird ausgelöst, wenn Sie das Objekt berühren und freigeben.
>   - Beim Einstieg: Wird ausgelöst, wenn das Objekt berührt wird.
>   - Bei der Touchscreen-Aktualisierung: Wird in regelmäßigen Abständen ausgelöst, während die Hand das Objekt berührt.

>   In diesem Beispiel arbeiten wir mit der Einstellung on Touchscreen Started.

4. Klicken Sie wie in der Abbildung unten gezeigt auf die Schaltfläche + bei der Option für Fingereingabe gestartet. Ziehen Sie das Octa-Objekt in das leere Feld. 

5. Wählen Sie in der Dropdown Liste, die keine Funktion (oberhalb des grünen Rechtecks in der Abbildung unten) besagt, audiosource-> playoneshot aus. Wir werden diesem Feld einen Audioclip mit den folgenden Konzepten hinzufügen:

   - Das MRTK stellt eine kurze Liste von Audioclips zur Verfügung. Sie können diese einfach in Ihrem Projektbereich untersuchen. Sie befinden sich im Ordner "mixedrealitytoolkit. SDK" und dann im Ordner "Standard Objekte". Dort sehen Sie einen audioordner, in dem alle Audioclips angezeigt werden.
   - In diesem Beispiel wird der MRTK_Gem-Audioclip verwendet. 
   - Ziehen Sie zum Hinzufügen eines Audioclips einfach den gewünschten Clip aus dem Projektbereich in „AudioSource.PlayOneShot“ (im obigen Beispiel durch ein grünes Feld gekennzeichnet) im Inspektorbereich.

   Wenn der Benutzer nun das Octa-Objekt erreicht und berührt, wird die Audiospur MRTK_Gem wiedergegeben. Das Hand Interaktions-Fingereingabe Skript passt auch die Farbe des Objekts an, wenn es berührt wird. 

![Lektion4 Kapitel4 Schritt3 5 Noteim](images/Lesson4_chapter4_step3-5-noteim.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch! 
In diesem Tutorial haben Sie erfahren, wie Sie 3D-Objekte in einer Raster Auflistung organisieren und 3D-Objekte (Skalieren, drehen und verschieben) mithilfe der Near-Interaktion (direkt mit nach verfolgten Händen) und der äußersten Interaktion (mit Blick-und Handzeichen) bearbeiten. Außerdem haben Sie gelernt, wie sie umgebende Felder um 3D-Objekte platzieren können, und Sie haben gelernt, wie Sie die Gizmos in den Begrenzungs Feldern verwenden und anpassen. Schließlich haben Sie erfahren, wie Sie beim Berühren eines Objekts Ereignisse auslösen können.

[Nächste Lektion: 6. Untersuchen erweiterter Eingabeoptionen](mrlearning-base-ch5.md)

