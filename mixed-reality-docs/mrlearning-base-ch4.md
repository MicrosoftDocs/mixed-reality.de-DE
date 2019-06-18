---
title: Basismodul zum MR-Lernen – 3D-Objektinteraktion
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 45e772de0825fe2161f880a165d6c75c755b849e
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730907"
---
# <a name="mr-learning-base-module---3d-object-interaction"></a>Basismodul zum MR-Lernen – 3D-Objektinteraktion

In dieser Lektion werden die grundlegenden 3D-Inhalte und die Benutzererfahrung erläutert. Sie werden erfahren, wie Sie 3D-Objekte als Teil einer Sammlung organisieren, und wie Sie Begrenzungsrahmen für grundlegende Manipulationen verwenden. Zudem erhalten Sie Informationen zu nahen und fernen Interaktionen sowie zu Gesten zum Berühren und Greifen beim Handtracking. 

## <a name="objectives"></a>Ziele

* Informationen zur Organisation von 3D-Inhalten mit der MRTK-Rasterobjektsammlung
* Implementieren von Begrenzungsrahmen
* Konfigurieren von 3D-Objekten für grundlegende Manipulationen (bewegen, drehen und skalieren)
* Erkunden von nahen und fernen Interaktionen
* Informationen zu zusätzlichen Handtracking-Gesten wie „Greifen“ und „Berühren“

## <a name="instructions"></a>Anweisungen

### <a name="organizing-3d-objects-in-a-collection"></a>Organisieren von 3D-Objekten in einer Sammlung

1. Klicken Sie mit der rechten Maustaste auf Ihre Hierarchie, und wählen Sie „Leer erstellen“ aus. Dadurch wird ein leeres Spielobjekt erstellt. Benennen Sie es um in „3DObjectCollection“. Hier werden alle unsere 3D-Objekte abgelegt. Stellen Sie sicher, dass die Positionierung der Sammlung auf „x = 0“, „y = 0“ und „z = 0“ eingestellt ist.

![Lektion4 Kapitel1 Schritt1im](images/Lesson4_Chapter1_step1im.PNG)

2. Importieren Sie BaseModule-Ressourcen mithilfe derselben Anweisungen zum Importieren benutzerdefinierter Pakete, die in [Lektion1](mrlearning-base-ch1.md) beschrieben wurden. Die BaseModule-Ressourcen umfassen 3D-Module und andere nützliche Skripts, die in diesem Tutorial verwendet werden. Das BaseModule-Unity-Paket finden Sie hier: <https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1>

3. Das Kaffeetassen-Prefab ist an einem daneben befindlichen blauen Würfel zu erkennen. Wählen Sie nicht die Kaffeetasse mit dem blauen Würfel und dem kleinen Whitepaper aus (das das ursprüngliche 3D-Modell und nicht das Prefab bezeichnet). 

![Lektion4 Kapitel1 Noteaim](images/Lesson4_chapter1_noteaim.PNG)

4. Ziehen Sie das gewünschte Kaffeetassen-Prefab in das Spielobjekt „3DObjectCollection“ aus Schritt 1. Die Kaffeetasse ist jetzt ein untergeordnetes Element der Sammlung.

![Lektion4 Kapitel1 Schritt4ima](images/Lesson4_chapter1_step4ima.PNG)

5. Als Nächstes fügen wir weitere 3D-Objekte zu unserer Szene hinzu. Nachfolgend finden Sie eine Liste der Objekte, die wir in diesem Beispiel hinzufügen werden. Beim Hinzufügen der Objekte können Sie feststellen, dass sie in Ihrer Szene in verschiedenen Größen angezeigt werden. Passen Sie die Skalierung der einzelnen 3D-Modelle unter der Einstellung zum Transformieren im Inspektorbereich an. Empfohlene Anpassungen in diesem Beispiel werden mit den Objekten, die unten aufgeführt. Suchen Sie diese Wörter im Suchfeld in Ihrem Projektbereich, und ziehen Sie das 3D-Objekt-Prefab ähnlich wie im vorherigen Schritt in das Objekt „3DObjectCollection“. Sie finden diese Sammlung von Prefabs in „Assets>BaseModuleAssets>Base Module Prefabs“.
- Suchen Sie nach „TheModule_BaseModuleIncomplete“. Ziehen Sie es in die Szene. Stellen Sie die Skalierung auf „x = 0,03“, „y = 0,03“, „z = 0,03“ ein. 
- Suchen Sie nach „Octa_BaseModuleIncomplete“. Ziehen Sie es in die Szene. Stellen Sie die Skalierung auf „x = 0,13“ ein. „y = 0,13“, „z = 0,13“.
- Suchen Sie nach „EarthCore_BaseModuleIncomplete“. Ziehen Sie es in die Szene. Stellen Sie die Skalierung auf „x = 50,0“, „y = 50,0“, „z = 50,0“ ein.
- Suchen Sie nach „Cheese_BaseModuleIncomplete“. Ziehen Sie es in die Szene. Stellen Sie die Skalierung auf „x = 0,05“, „y = 0,05“, „z = 0,05“ ein.
- Suchen Sie nach „Model_Platonic_BaseModuleIncomplete“. Ziehen Sie es in die Szene. Stellen Sie die Skalierung auf „x = 0,13“, „y = 0,13“, „z = 0,13“ ein.
- Suchen Sie nach „CoffeeCup_BaseModuleIncomplete“. Ziehen Sie es in die Szene.

![Lektion4 Kapitel1 Schritt5im](images/Lesson4_Chapter1_step5im.PNG)

6. Fügen Sie drei Würfel in Ihre Szene ein. Klicken Sie mit der rechten Maustaste auf das Objekt „3DObjectCollection“, wählen Sie „3D Object“ (3D-Objekt) und dann „Cube“ (Würfel) aus. Stellen Sie die Skalierung auf „x = 0,14“, „y = 0,14“, „z = 0,14“ ein. Wiederholen Sie diesen Schritt 2 weitere Male, um insgesamt drei Würfel zu erstellen. Alternativ können Sie den Würfel auch zweimal duplizieren, sodass sich insgesamt drei Würfel ergeben. Sie können auch die drei vorbereiteten Würfel-Prefabs aus „Assets>BaseModuleAssets>Base Module Prefabs“ verwenden und „GreenCube_BaseModuleIncomplete“, „BlueCube_BaseModuleIncomplete“ und „OrangeCube_BaseModuleIncomplete“ auswählen.

![Lektion4 Kapitel1 Schritt6im](images/Lesson4_Chapter1_step6im.PNG)

7. Organisieren Sie Ihre Sammlung von Objekten unter Verwendung der MRTK-Rasterobjektsammlung zu einem Raster, wie in [Lektion 2](mrlearning-base-ch2.md) beschrieben. Die folgende Abbildung zeigt ein Beispiel für die Konfiguration der Objekte in einem 3x3-Raster.

![Lektion4 Kapitel1 Notebim](images/Lesson4_chapter1_notebim.PNG)

>Hinweis: Sie werden vielleicht feststellen, dass einige der Objekte nicht zentriert sind, z. B. die Objekte im obigen Bild. Dies liegt daran, dass Prefabs oder Objekte möglicherweise untergeordnete Objekte aufweisen, die nicht ausgerichtet sind. Sie können jederzeit alle notwendigen Anpassungen an den Positionen der Objekte oder Unterobjekte vornehmen, um ein ausgerichtetes Raster zu erhalten.


### <a name="manipulating-3d-objects"></a>Manipulieren von 3D-Objekten
1. Fügen Sie die Möglichkeit hinzu, einen Würfel zu manipulieren. Sie müssen die folgenden Schritte ausführen, um die Möglichkeit zur Manipulation von 3D-Objekten hinzuzufügen:
-   Wählen Sie das zu bearbeitende 3D-Objekt in Ihrer Hierarchie aus (in diesem Beispiel einen Ihrer Würfel).
-   Klicken Sie auf „Add component“ (Komponente hinzufügen). 
-   Suchen Sie nach „Manipulation“.
-   Wählen Sie „manipulation handler“ (Manipulationshandler) aus.
-   Wiederholen Sie dies für alle 3D-Objekte unter dem Objekt „3DObjectCollection“, aber nicht für „3DObjectCollection“ selbst.
-   Stellen Sie sicher, dass alle 3D-Objekte über einen Collider oder Feld-Collider verfügen (Add Component > Box-Collider (Komponente hinzufügen > Feld-Collider)).

![Lektion4 Kapitel2 Schritt1im](images/Lesson4_chapter2_step1im.PNG)

>Der Manipulationshandler ist eine Komponente, mit der Sie Einstellungen vornehmen können, wie sich Objekte bei der Manipulation verhalten. Dies umfasst das Drehen, Skalieren, Bewegen und Einschränken von Bewegungen auf bestimmte Achsen. 

2. Schränken Sie einen Cube so ein, dass er nur skaliert werden kann. Wählen Sie einen Würfel im Objekt „3DObjectCollection“ aus. Klicken Sie im Inspektorbereich neben „Two Handed Manipulation Type“ (Zweihändiger Manipulationstyp) auf das Dropdownmenü, und wählen Sie „Scale“ (Skalieren) aus. Dadurch kann der Benutzer nur die Größe des Würfels ändern.

![Lektion4 Kapitel2 Schritt2im](images/Lesson4_Chapter2_step2im.PNG)

3. Ändern Sie die Farbe der einzelnen Würfel, damit sie eindeutig unterschieden werden können. 
-   Wechseln Sie in den Projektbereich, und scrollen Sie nach unten, bis „MixedRealityToolkit.SDK“ angezeigt wird. Anschließend wählen Sie diesen Eintrag aus.
-   Wählen Sie den Ordner „Standard Assets“ (Standardressourcen) aus.
-   Klicken Sie auf den Ordner „Materials“ (Materialien).
-   Ziehen Sie ein anderes Material auf die einzelnen Würfel. 

>Hinweis: Sie können eine beliebige Farbe für Ihre Würfel auswählen. Für unser Beispiel verwenden wir „Glowingcyan“ (Leuchtendes Cyan), „Glowingorange“ (Leuchtendes Orange) und „Green“ (Grün). Experimentieren Sie ruhig mit verschiedenen Farben. Um die Farbe dem Würfel hinzuzufügen, klicken Sie auf den Würfel, dessen Farbe Sie ändern möchten, und ziehen Sie das Material dann in das Materialfeld des Mesh-Renderers im Inspektorbereich des Würfels. 

![Lektion4 Kapitel2 Schritt3im](images/Lesson4_Chapter2_step3im.PNG)

4. Wählen Sie einen anderen Würfel im Objekt „3DObjectCollection“ aus, und gestalten Sie ihn so, dass seine Bewegung auf den festen Abstand vom Kopf beschränkt ist. Klicken Sie dazu rechts neben „Constraint on Movement“ (Bewegungseinschränkung) auf das Dropdownmenü, und wählen Sie „Fix Distance from the Head“ (Fester Abstand vom Kopf) aus. Dadurch kann der Benutzer den Würfel nur innerhalb seines Sichtfelds bewegen. 

![Lektion4 Kapitel2 Schritt4im](images/Lesson4_chapter2_step4im.PNG)

Ziel der nächsten Schritte: Wir werden das Greifen und die Interaktion mit unseren 3D-Objekten ermöglichen. Wir werden verschiedene Manipulationseinstellungen anwenden. 

5. Wählen Sie das Cheese-Objekt (Käse) aus, und klicken Sie im Inspektorbereich auf „Add Component“ (Komponente hinzufügen). 

6. Suchen Sie im Suchfeld nach „Near Interaction Grabbable“ (Nah-Interaktion, greifbar), und wählen Sie das Skript aus. Diese Komponente ermöglicht es Benutzern, die Hände auszustrecken und die Objekte mit nachverfolgten Händen zu greifen. Objekte dürfen auch aus der Ferne manipuliert werden, es sei denn, das Kontrollkästchen „Allow Far Manipulation“ (Fern-Manipulation zulassen) ist nicht aktiviert (gekennzeichnet durch einen grünen Kreis im unteren Bild).

![Lektion4 Kapitel2 Schritt6im](images/Lesson4_Chapter2_step6im.PNG)

7. Fügen Sie dem Octa-Objekt, dem Platonic-Objekt (Plattform), dem Erdkern, der Mondlandefähre und der Kaffeetasse „Near Interaction Grabbable“ (Nah-Interaktion, greifbar) hinzu, indem Sie die Schritte 5 und 6 für diese Objekte wiederholen.

8. Entfernen Sie die Möglichkeit zur fernen Manipulation aus dem Octa-Objekt. Wählen Sie dazu das Octa-Objekt in der Hierarchie aus, und deaktivieren Sie das Kontrollkästchen „Allow Far Manipulation“ (Fern-Manipulation zulassen), das durch einen grünen Kreis gekennzeichnet ist. Dadurch ist es möglich, dass Benutzer nur mithilfe von nachverfolgten Händen direkt mit dem Octa-Objekt interagieren können.

>Hinweis: Die vollständige Dokumentation der Manipulationshandler-Komponente und ihrer zugehörigen Einstellungen finden Sie in der [MRTK-Dokumentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html).

9. Stellen Sie sicher, dass die Komponente „Near Interaction Grabbable“ (Nah-Interaktion, greifbar) dem Erdkern, der Mondlandefähre und der Kaffeetasse hinzugefügt wurde (siehe Schritt 7).

10. Ändern Sie für die Mondlandefähre die Einstellungen des Manipulationshandlers so, dass er sich sowohl für die nahe als auch für die ferne Interaktion um den Mittelpunkt des Objekts dreht, wie im folgenden Bild gezeigt.

![Lektion4 Kapitel2 Schritt10im](images/Lesson4_chapter2_step10im.PNG)

11: Ändern Sie für den Erdkern das Verhalten beim Loslassen in „Nothing“ (Nichts). Dadurch wird erreicht, dass sich der Erdkern, sobald er aus dem Griff der Benutzer freigegeben wurde, nicht weiter bewegt. 

![Lektion4 Kapitel2 Schritt11im](images/Lesson4_Chapter2_step11im.PNG)

> Hinweis: Diese Einstellung ist für bestimmte Szenarien nützlich, z. B. beim Erstellen eines Balls, den Sie werfen können. Das Beibehalten der Geschwindigkeit und der Winkelgeschwindigkeit bewirkt, dass sich der Ball nach dem Loslassen weiterhin mit der Geschwindigkeit bewegt, mit der er losgelassen wurde, d. h. ähnlich der Verhaltensweise eines physischen Balls.

### <a name="adding-bounding-boxes"></a>Hinzufügen von Begrenzungsrahmen
Begrenzungsrahmen gestalten das Manipulieren von Objekten mit einer Hand einfacher und intuitiver, sowohl für die direkte Manipulation (Nah-Interaktion) als auch für die strahlenbasierte Manipulation (Fern-Interaktion). Begrenzungsrahmen bieten „Ziehpunkte“, die zum Skalieren und Drehen von Objekten entlang bestimmter Achsen gegriffen werden können.
>Hinweis: Bevor Sie einem Objekt einen Begrenzungsrahmen hinzufügen können, muss das Objekt zunächst über einen Collider verfügen (z. B. ein Feld-Collider). Wie wir es bereits in dieser Lektion durchgeführt haben. Collider können hinzugefügt werden, indem Sie das Objekt auswählen und im Inspektorbereich des Objekts „Add Component > Box Collider“ (Komponente hinzufügen > Feld-Collider) auswählen.
>

1. Fügen Sie dem Erdkernobjekt einen Feld-Collider hinzu, falls dieser noch nicht vorhanden ist (Feld-Collider und Einrichtung nicht erforderlich, wenn Sie das im Ordner „Base Module Assets“ bereitgestellte Prefab gemäß den angegebenen Anweisungen verwenden). Für den Erdkern müssen wir den Feld-Collider zum Objekt „node_id30“ unterhalb des Erdkerns hinzufügen, wie in der folgenden Abbildung dargestellt. Wählen Sie „node_id30“ aus, klicken Sie auf der Inspektoregisterkarte des Objekts auf „Add Component“ (Komponente hinzufügen), und suchen Sie nach „Box Collider“ (Feld-Collider). 

![Lektion4 Kapitel3 Schritt1im](images/Lesson4_Chapter3_step1im.PNG)

![Lektion4 Kapitel3 Schritt2im](images/Lesson4_chapter3_step2im.PNG)

> Hinweis: Stellen Sie sicher, dass Sie den Feld-Collider so darstellen, dass er nicht zu groß oder zu klein ist. Es sollte ungefähr dieselbe Größe aufweisen wie das von ihm umgebene Objekt (in diesem Beispiel der Erdkern). Passen Sie den Feld-Collider bei Bedarf an, indem Sie die Option „Edit Collider“ (Collider bearbeiten) im Feld-Collider auswählen. Sie können entweder die x-, y- und z-Werte ändern oder die Ziehpunkte des Begrenzungsrahmens im Szenenfenster des Editors ziehen. 

![Lektion4 Kapitel3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. Fügen Sie dem Objekt „node_id30“ des Erdkerns einen Begrenzungsrahmen hinzu. Wählen Sie dazu das Objekt „node_id30“ aus „3DObjectCollection“ aus. Klicken Sie auf der Inspektorregisterkarte auf „Add Component“ (Komponente hinzufügen), und suchen Sie nach „Bounding Box“ (Begrenzungsrahmen). Stellen Sie sicher, dass sich Begrenzungsrahmen, Feld-Collider und Manipulationsskripts (Manipulationshandler, Nah-Interaction, greifbar) alle auf demselben Spielobjekt befinden.

3.  Wählen Sie im Abschnitt „Behavior“ (Verhalten) des Begrenzungsrahmens aus der Dropdownliste „Activation“ (Aktivierung) die Option „Activate on Start“ (Beim Start aktivieren) aus. Um weitere Details zu den verschiedenen Aktivierungsoptionen und anderen Optionen des Begrenzungsrahmens zu überprüfen, lesen Sie die MRTK-Dokumentation zum [Begrenzungsrahmen](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>).

   

   *In den nächsten Schritten werden wir auch das Aussehen des Begrenzungsrahmens ändern, indem wir das Standardfeldmaterial, das Material während des Greifvorgangs sowie die Visualisierung von Ziehpunkten (Ziehpunkt an Ecken und Seiten) anpassen. Das MRTK enthält mehrere Optionen zum Anpassen des Begrenzungsrahmens.*

4. Suchen Sie im Projektbereich nach „Boundingbox“ (Begrenzungsrahmen). Daraufhin wird eine Liste der Materialien in den Suchergebnissen angezeigt, die durch eine blaue Kugel gekennzeichnet sind, wie in der nachfolgenden Abbildung gezeigt. 

5. Ziehen Sie das Material des Begrenzungsrahmens in den Bereich für Feldmaterial auf der Begrenzungsrahmenkomponente. Ziehen Sie auch das Material „Boundingboxgrabbed“ (Begrenzungsrahmen, gegriffen) in den Bereich für gegriffenes Feldmaterial auf der Begrenzungsrahmenkomponente.

6. Ziehen Sie das Material „MRTK_BoundingBox_ScaleWidget“ in den Prefab-Bereich für den Skalierungsziehpunkt auf der Begrenzungsrahmenkomponente. 

7. Ziehen Sie das Material „MRTK_BoundingBox_RotateWidget“ in den Drehziehpunktbereich auf der Begrenzungsrahmenkomponente.

![Lektion4 Kapitel3 Schritt4 7Im](images/Lesson4_chapter3_step4-7im.PNG)

8. Stellen Sie sicher, dass der Begrenzungsrahmen auf das richtige Objekt ausgerichtet ist. In der Begrenzungsrahmenkomponente gibt es die Skripts „Target Object“ (Zielobjekt) und „Bounds Override“ (Begrenzungen aufheben). Achten Sie darauf, dass Sie das Objekt, das vom Begrenzungsrahmen umgeben ist, in diese beiden Bereiche ziehen. Ziehen Sie in diesem Beispiel das Objekt „node_id30“ in diese beiden Bereiche, wie in der nachfolgenden Abbildung gezeigt.

> Wenn Sie die Anwendung starten oder wiedergeben, ist Ihr Objekt jetzt von einem blauen Rahmen umgeben. Sie können die Ecken dieses Rahmens ziehen, um die Größe des Objekts zu ändern. Wenn die Ziehpunkte für Skalierung und Drehen größer und sichtbarer sein sollen, empfehlen wir die Verwendung der Standardeinstellungen für den Begrenzungsrahmen (Vermeiden der Schritte 4 bis 7). 

![Lektion4 Kapitel3 Schritt8im](images/Lesson4_Chapter3_step8im.PNG)

9. Um zur Standarddarstellung des Begrenzungsrahmens zurückzukehren, wählen Sie im Inspektorbereich des Objekts für den Begrenzungsrahmen das Drehziehpunkt-Prefab aus und drücken die Löschtaste. Jetzt wird eine Begrenzungsrahmendarstellung ähnlich wie in nachfolgender Abbildung angezeigt. Hinweis: Die Darstellungen der Begrenzungsrahmen werden nur im Wiedergabemodus angezeigt.

![Lektion4 Kapitel3 Schritt9im](images/Lesson4_chapter3_step9im.PNG)

### <a name="adding-touch-effects"></a>Hinzufügen von Effekten für die Toucheingabe
In diesem Beispiel werden wir einen Soundeffekt wiedergeben, wenn Sie ein Objekt mit der Hand berühren.

1. Fügen Sie eine Audioquellenkomponente zu Ihrem Spielobjekt hinzu. Wählen Sie das Octa-Objekt (Oktaeder) in Ihrer Szenenhierarchie aus. Klicken Sie im Inspektorbereich auf die Schaltfläche „Add Component“ (Komponente hinzufügen), suchen Sie nach „Audio Source“ (Audioquelle), und wählen Sie dann eine Audioquelle aus. Wir werden diese Audioquelle verwenden, um in einem späteren Schritt einen Soundeffekt wiederzugeben. 

>Hinweis: Stellen Sie sicher, dass das „Octa“-Objekt über einen Feld-Collider verfügt.

2. Fügen Sie die Komponente „Near Interaction touchable“ (Nah-Interaktion, berührbar) hinzu. Klicken Sie auf die Schaltfläche „Add Component“ (Komponente hinzufügen) im Inspektorbereich, und suchen Sie nach „Near Interaction touchable“ (Nah-Interaktion, berührbar). Wählen Sie diese Option aus, um die Komponente hinzuzufügen. HINWEIS: Korrigieren Sie den Screenshot, um hervorzuheben, dass wir die Komponente hinzufügen und nicht nur den Feld-Collider hervorheben.

>Hinweis: Zuvor haben wir „Near Interaction grabbable“ (Nah-Interaktion, greifbar) hinzugefügt. Der Unterschied zwischen dieser Option und „Near Interaction touchable“ (Nah-Interaktion, berührbar) besteht darin, dass die „greifbare“ Interaktion für ein Objekt bestimmt ist, das Sie greifen und mit dem Sie interagieren. Die „berührbare“ Komponente ist für das zu berührende Objekt vorgesehen. Beide Komponenten können zusammen für eine Kombination von Interaktionen verwendet werden.

![Lektion4 Kapitel4 Schritt1 2Im](images/Lesson4_chapter4_step1-2im.PNG)

3. Fügen Sie das Skript „Hand Interaction Touch“ (Handinteraktion, berühren) hinzu. Beachten Sie, dass dieses Skript in der Unity-Szene enthalten ist, die Sie als Teil dieses Demopakets importiert haben. Es ist nicht im ursprünglichen MRTK enthalten. Klicken Sie wie im vorherigen Schritt auf „Add Component“ (Komponente hinzufügen), und suchen Sie nach „Hand Interaction touch“ (Handinteraktion, berühren), um sie hinzuzufügen. 
   Beachten Sie, dass das Skript drei Optionen bietet: 

   - „On touch completed“ (Bei Berührung abgeschlossen). Diese Option wird ausgelöst, wenn Sie das Objekt berühren und loslassen. 
   - „On touch started“ (Bei Berührung gestartet). Diese Option wird ausgelöst, wenn das Objekt berührt wird. 
   - „On touch updated“ (Bei Berührung aktualisiert). Diese Option wird regelmäßig ausgelöst, während Ihre Hand das Objekt berührt. 

   Für dieses Beispiel werden wir mit der Einstellung „On touch started“ (Bei Berührung gestartet) arbeiten.

4. Klicken Sie für die Option „On touch started“ (Bei Berührung gestartet) auf die Schaltfläche „+“, wie in der nachfolgenden Abbildung gezeigt. Ziehen Sie das Octa-Objekt in das leere Feld. 

5. Wählen Sie in der Dropdownliste „No Function“ (Keine Funktion, über dem grünen Rechteck in der nachfolgenden Abbildung) die Option „AudioSource> PlayOneShot“ (Audioquelle > PlayOneShot) aus. Wir werden diesem Feld einen Audioclip mit den folgenden Konzepten hinzufügen:

   - Das MRTK stellt eine kurze Liste von Audioclips zur Verfügung. Sie können diese einfach in Ihrem Projektbereich untersuchen. Sie finden sie im Ordner „MixedRealityToolkit.SDK“ und dann im Ordner „Standard Assets“ (Standardressourcen). Dort wird der Ordner „Audio“ angezeigt, in dem sich alle Audioclips befinden.
   - Für dieses Beispiel werden wir den Audioclip „MRTK_Gem“ verwenden. 
   - Ziehen Sie zum Hinzufügen eines Audioclips einfach den gewünschten Clip aus dem Projektbereich in „AudioSource.PlayOneShot“ (im obigen Beispiel durch ein grünes Feld gekennzeichnet) im Inspektorbereich.

   Wenn der Benutzer jetzt die Hand ausstreckt und das Octa-Objekt berührt, wird der Audiotitel „MRTK_Gem“ wiedergegeben. Das Skript „Hand Interaction Touch“ (Handinteraktion, berühren) passt auch die Farbe des Objekts bei Berührung an. 

![Lektion4 Kapitel4 Schritt3 5 Noteim](images/Lesson4_chapter4_step3-5-noteim.PNG)

### <a name="congratulations"></a>Herzlichen Glückwunsch! 
In dieser Lektion haben Sie erfahren, wie Sie 3D-Objekte in einer Rastersammlung organisieren und wie Sie 3D-Objekte (Skalieren, Drehen und Bewegen) durch Nah-Interaktion (direktes Greifen mit nachverfolgten Händen) und Fern-Interaktion (mit Lichtstrahlen zum Anvisieren oder Handstrahlen) manipulieren können. Sie haben außerdem erfahren, wie Sie um 3D-Objekte herum Begrenzungsrahmen positionieren, und wie Sie die Dinge für die Begrenzungsrahmen verwenden und anpassen können. Schließlich haben Sie erfahren, wie Sie beim Berühren eines Objekts Ereignisse auslösen können.

[Nächste Lektion: Erweiterte Eingabe](mrlearning-base-ch5.md)

