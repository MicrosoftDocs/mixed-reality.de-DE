---
title: Hand Coach
description: 3D-Hände, die ausgelöst werden, wenn das System die Hände des Benutzers nicht erkennt, um Sie zu unterstützen.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality, Design, Hand Coach, immersives Headset, mrtk, Hände, Unterstützung von Hand
ms.openlocfilehash: c5f0a0c241ff71dc93f370a5a8caa627128bfb1a
ms.sourcegitcommit: 1ec628a9107194c0a9d4073b5ca09ee816030e85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/01/2020
ms.locfileid: "78202735"
---
# <a name="hand-coach"></a>Hand Coach

Hand Coach ist 3D-modellierte Hände, die ausgelöst werden, wenn das System die Hände des Benutzers nicht erkennt. Dies wird als "Lehr Komponente" implementiert, die den Benutzer unterstützt, wenn die Geste nicht gelehrt wurde. Wenn Benutzer die angegebene Geste für einen Zeitraum nicht durchgeführt haben, wird die Hand mit einer Verzögerung Schleife. Der handbus könnte verwendet werden, um das Drücken einer Schaltfläche oder das Auswählen eines holograms darzustellen.  


![Beispiel: Hand Coach](images/HandCoach/MRTK_handCoach.jpg)<br>
*Handbus Beispiel von mrtk*

## <a name="hand-coach-provided"></a>Hand Trainer bereitgestellt

Das aktuelle Interaktionsmodell stellt eine Vielzahl von Gesten Steuerelementen dar, wie z. b. Scrollen, weite Auswahl und Near Tap. Im folgenden finden Sie eine vollständige Liste der in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> mrtk</a>bereitgestellten Handgesten:

:::row:::
    :::column:::
       ![Beispiel für Near Select](images/HandCoach/NearSelect.gif)<br>
       **Beispiel für Near Select-used anzeigen auswählen von Schaltflächen oder Schließen von Objekten mit Interaktionen**<br>
    :::column-end:::
    :::column:::
       ![Beispiel für Air Tap](images/HandCoach/AirTap.gif)<br>
        **Beispiel für Air Tap: wird verwendet, um zu zeigen, wie Objekte, die weit entfernt sind, ausgewählt werden.**<br>
    :::column-end:::
    :::column:::
       ![Beispiel für Move](images/HandCoach/Move.gif)<br>
       **Beispiel für das Verschieben eines Objekts im Raum: wird verwendet, um zu veranschaulichen, wie ein – Hologramm in den Raum verschoben wird.**<br>
    :::column-end:::
    :::column:::
       ![Beispiel für das Drehen](images/HandCoach/Rotate.gif)<br>
       **Beispiel für drehen: wird verwendet, um zu zeigen, wie Hologramme oder Objekte gedreht werden.**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![Beispiel für Skalierungs](images/HandCoach/Scale.gif)<br>
       **Beispiel für "Scale-used", um zu veranschaulichen, wie die Manipulation von holograms größer oder kleiner wird**<br>
    :::column-end:::
    :::column:::
       ![Beispiel für die](images/HandCoach/PalmUp.gif)<br>
        **Beispiel für eine zusammen Fläche – Empfohlene Verwendung, um die Menüs aufzurufenden**<br>
    :::column-end:::
    :::column:::
       ![Beispiel für ein handflip](images/HandCoach/HandFlip.gif)<br>
       **Exahorn von Hand Flip – eine andere Möglichkeit zum Einrichten von Menüs**<br>
    :::column-end:::
    :::column:::
       ![Beispiel für Scroll](images/HandCoach/Scoll.gif)<br>
       **Beispiel für einen Scroll–, der zum Scrollen einer Liste oder eines langen Dokuments verwendet wird**<br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a>Entwurfskonzepte

Für Hololens2 haben wir die manuellen Interaktionen auf der Grundlage von instanziellen und natürlichen Handbewegungen entworfen. Wir sind der Meinung, dass diese für die meisten Benutzer intuitiv sind und daher keine dedizierten Gesten lernmomente geschaffen haben. Stattdessen haben wir den Hand-Bus erstellt, um Benutzer zu unterstützen, die möglicherweise hängen bleiben oder mit der Interaktion mit holograms nicht vertraut sind. Weitere Informationen zu diesen Gesten Ohne einen Lern Moment haben wir gespürt, dass Benutzern angezeigt wird, wie Sie eine Aktion durchführen können, indem Sie Ihnen zeigen, dass Sie die beste Option ist. In unseren Studien stellten wir fest, dass Benutzer in der Lage waren, die Geste herauszufinden, aber eine kleine Anleitung benötigten. Wenn Sie feststellen, dass ein Benutzer für einen bestimmten Zeitraum nicht mit einem Objekt interagiert, wird ein Hand Trainer ausgelöst, der die korrekte Hand-und Finger Platzierung demonstriert. 

### <a name="intuitive"></a>Intuitiven

Bei der Animation sollte es offensichtlich sein, und es kann zu Verwirrung führen. Die Animation der Hände ist eine Darstellung der Geste, die Sie dem Benutzer zur Veranschaulichung des Zwecks des zwecks vermitteln möchten. 

Wenn Sie z. b. möchten, dass ein Benutzer auf eine Schaltfläche klickt, wird eine Hand Taste gedrückt.

![Beispiel: Hand Coach near Tap](images/HandCoach/NearSelect_unity.gif)<br>
*Hand Coach, der das Tippen auf einen gem tippen zeigt*  

### <a name="hand-scale"></a>Hand Skala

Wir haben verschiedene Hand Größen mit den Menüs für die Benutzeroberfläche getestet, und Sie fühlten, dass Sie, wenn die Hände für die Größe zutreffen, eine wohlwollende Vorstellung hatten, aber wenn Sie zu klein waren, war es schwierig, die Geste zu erkennen und zu verstehen. 

**Voice-over und Hand**

Sie sollten nicht erwarten, dass Benutzer eine Reihe von Anweisungen über eine Stimme überwachen und andere Anweisungen über den Hand-Bus ansehen. Sequenzieren Sie Ihre Anweisungen, um Benutzern den Fokus zu erleichtern und um Ihre Aufmerksamkeit zu unterstützen, um die Sensor Überlastung


## <a name="can-i-create-my-own"></a>Kann ich meine eigene erstellen?

Ja, Wir empfehlen Ihnen, eine eigene, einzigartige Geste für Ihr Spiel zu erstellen und zur Community beizutragen.
Wir haben eine Maya-Datei für eine manipulierte Hand bereitgestellt, die für Ihre APP verwendet werden kann. Sie können hier heruntergeladen werden: <a href="files/HandCoach_MRTK.zip">Download HandCoach_MRTK. zip</a>

![Beispiel für animierte Hände in Maya](images/HandCoach/MayaSelect_Gif.gif)<br>
*Beispiel für ein animiertes Hand Zeichen in Maya*


**Empfohlenes Authoring Tool**

Bei 3D-Künstlern entscheiden sich viele für die Verwendung [von Autodesk Maya, die wiederum hololens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) zum Transformieren der Art und Weise der Erstellung von Assets verwenden können. Die angegebene handdatei ist eine Maya-Binärdatei. Daher empfiehlt es sich, Maya zu verwenden, um die Hände zu animieren und zu exportieren. Wenn Sie lieber ein anderes 3D-Programm verwenden möchten, finden Sie hier eine <b>. FBX</b>: <a href="files/HandCoachMRTK_FBX.zip">Laden Sie HandCoachMRTK_FBX. zip herunter</a> , um Ihre eigene Controller Einrichtung zu erstellen. 

Wenn Sie die herunterladbare Maya-handdatei verwenden, wird empfohlen, die Hände in Unity auf 0,6 zu skalieren.

![Beispiel: Hand Coach rig in Maya](images/HandCoach/MayaExample.png)<br>
*Manipulierte Hände*

### <a name="technical-specs"></a>Technische Spezifikationen

*   Zwei über gebene Dateien sind im Maya ASCII-Format verfügbar.
*    Rechts und Links sind im Format "Maya Binary" verfügbar.
*   Festlegen der Maya-Datei auf 24 fps
*   Innerhalb der Datei gibt es eine linke und Rechte Seite, die für zwei Hand-oder einstellige Gesten verwendet werden kann. Die Rechte Seite ist standardmäßig nur sichtbar.
*   Es wird empfohlen, einen Puffer mit ungefähr 10 Frames am Anfang und am Ende für die gestreamungen zu belassen.
*   Wenn Sie ein-Objekt mit einem angegebenen Ziel animieren, empfiehlt es sich, ein Standardfeld zu animieren oder NULL zu animieren.
*   Wenn die Hand ein physisches Objekt, wie z. b. ein Feld, animiert, empfiehlt es sich, die Übersetzung nicht in Maya zu animieren, sondern in Unity oder im Code zu animieren.
*   Die sichtbare Animation sollte 1,5 Sekunden sein, damit aussagekräftige Informationen übermittelt werden können.
*   Wenn Sie mit ihrer Animation zufrieden sind:
    *   Alle Gelenke auswählen und Keyframes Backen
    *   Löschen Sie die Controller, wählen Sie die Gelenke und das Mesh aus, und exportieren Sie Sie als eine andere
    *  Wenn mehrere Animationen vorhanden sind, können Sie das integrierte Game Exporter von Maya verwenden: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html

## <a name="exporting-from-maya"></a>Exportieren aus Maya

Nachdem Sie mit ihrer Animation zufrieden sind
* Alle Gelenke auswählen: Wählen Sie > Hierarchie aus.

     ![Beispiel: Menü Position](images/HandCoach/Hierarchy.png)<br>
* Animation der Animation: Wechseln Sie zur Animation > Key > Animation.

     ![Beispiel: Menü Position](images/HandCoach/BakeAnimation.png)<br>
* Löschen Sie das Controller-Rig: Outliner-> MainR_Grp oder MainL_Grp

     ![Beispiel: Menü Position](images/HandCoach/ControllerRig.png)<br>

* Exportieren als FBX: Wählen Sie JNT + Mesh: File > Export Selection (Optionsfeld) > Export Auswahl aus.

     ![Beispiel: Menü Position](images/HandCoach/OptionBox.png)<br>

     ![Beispiel: Menü Position](images/HandCoach/SelectionExport.png)<br>

     ![Beispiel: Menü Position](images/HandCoach/FBXSelection.png)<br>


 Wenn Sie als FBX exportieren und in Unity integriert sind, Skalieren Sie die Hände auf 0,6. Wir haben festgestellt, dass dies das perfekte Gleichgewicht für die Anzeige der Hände ist. 

![Beispiel: Unity-Einstellungen](images/HandCoach/HandHintScale.png)<br>
*Unity-Einstellungen für HandCoach_R-präfab in mrtk*


## <a name="implementing-hands-into-your-unity-project"></a>Implementieren von Hand in Ihr Unity-Projekt

### <a name="best-practices"></a>Empfohlene Methoden
*    Es wird empfohlen, die Hände in Unity auf 0,6 zu skalieren.
*   Hände sollten zweimal abgespielt werden und, wenn Sie nicht abgeschlossen ist, bis zum Abschluss der Bewegung fortlaufend. Die Hände sollten zweimal Schleifen, um sicherzustellen, dass der Benutzer Zeit hat, sich zu registrieren und die Geste anzuzeigen. Die Hände sollten Zwischenschleifen ein-und ausgeblendet werden. 
 *  Wenn Benutzer Hände durch HL2-Kameras sichtbar sind, die Benutzer jedoch nicht die erforderliche Interaktion durchlaufen, werden die Hände nach 10 Sekunden angezeigt.
*   Wenn Benutzer Hände nicht durch HL2 Kameras sichtbar sind, werden die Hände nach 5 Sekunden angezeigt.  
*   Wenn Benutzer Hände in der Mitte der Animation von HL2-Kameras sichtbar sind, wird die Animation vervollständigt und ausgeblendet.
*   Wenn Sie Voice over einschließen, empfehlen wir, dass es der Handbewegung entspricht.
*   Wenn Sie die Hände mindestens einmal gelehrt haben, wiederholen Sie die Geste nur, wenn Sie festgestellt hat, dass der Benutzer nicht mehr vorhanden ist.
*   Wenn bestimmte Finger-/uhrzeitanpositionen kritisch sind, stellen Sie sicher, dass Benutzer diese Nuancen in der Animation eindeutig sehen können. Probieren Sie die Hände, damit die wichtigsten Teile klar sichtbar sind. 
* Wenn Sie auf eine gewisse Verzerrung achten, müssen Sie die Qualitätseinstellungen der Unity erhöhen, um die Menge der Knochen zu erhöhen. 
 Wechseln Sie zu Unity-> Projekteinstellungen > Quality > Andere > Blend-Gewichtungen. Stellen Sie sicher, dass "4 Knochen" ausgewählt sind, um glatte Gelenke anzuzeigen. 

   ![Beispiel: Menü Position](images/HandCoach/ProjectSettings.png)<br>





### <a name="what-to-avoid"></a>Was Sie vermeiden sollten
* Skalieren der Hände zu groß
* die Hände werden dem Benutzer zu nah platziert.
* Hände sollten nur einmal vermittelt werden. Über lehrungen können Verwirrung und Verwirrung verursachen.
*   Wenn Sie ihn in Unity einbinden, laden Sie den aktuellen mrtk hier herunter: https://github.com/microsoft/MixedRealityToolkit-Unity
    *   Material: Teaching_Hand2
    *   Skripts: siehe mrtk Guidelines for <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md">mrtk Hand Coach</a>
    *   Pro-Projekt-Einstellung
        *   Szene, die auf UWP festgelegt ist: Anweisungen finden Sie im [Unity-Projekt](Configure-Unity-Project.md) für Windows Mixed Reality.

## <a name="see-also"></a>Siehe auch
* [Interaktion: Grundlagen](interaction-fundamentals.md)
* [Asset-Erstellungs Prozess](asset-creation-process.md)
* [Gesten](gestures.md)
* [Installieren der Tools](install-the-tools.md)
* [Unity-Projekt konfigurieren](Configure-Unity-Project.md)
* [Unity-Entwicklung – Übersicht](unity-development-overview.md)
* [Mrtk 101](mrtk-101.md)
