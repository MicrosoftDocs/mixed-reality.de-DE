---
title: Mr Learning Sharing Module für hololens 2
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Umgebungen mit mehreren Benutzern in einer hololens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 3e4be00ddeab6d91dbbc8226bfa3dc543cded095
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293682"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. Freigeben von Objektbewegungen mit mehreren Benutzern

In diesem Tutorial erfahren Sie, wie Sie die Bewegungen von Objekten freigeben, damit alle Teilnehmer einer freigegebenen Sitzung zusammenarbeiten und die Interaktionen der einzelnen Benutzer anzeigen können. Diese Lektion baut auf dem Mond Start Programm auf, das als Teil der Lernprogramme für das [Basismodul](mrlearning-base.md)erstellt wurde.

Ziele

- Bringen Sie das Mond Startfeld als 3D-Modell ein, das freigegeben werden soll.
- Konfigurieren Sie das Projekt so, dass die Bewegungen des 3D-Modells gemeinsam genutzt werden.
- Erfahren Sie, wie Sie eine grundlegende Anwendung für mehrere Benutzer Anwendungen erstellen.

### <a name="instructions"></a>Anweisungen


1. Speichern Sie die Szene aus der vorherigen Lektion (Control + S). Sie können den Namen HLSharedProjectMainPart4. unity benennen, damit er bei Bedarf leichter zu finden ist.

2. Doppelklicken Sie im Projektfenster im Ordner Assets-> Scripts auf genericnetsync, um ihn in Visual Studio oder in dem von Ihnen verwendeten Code-Editor zu öffnen.  

![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. Entfernen Sie in den Zeilen 34 und 38 das//, um den Code für die Tabelle zu aktivieren, die in dieser Lektion verwendet werden soll. Speichern Sie dann die Datei. 

![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. Doppelklicken Sie im Projektfenster im Ordner Assets-> Scripts auf die Datei PhotonRoom.cs, um Sie in Visual Studio zu öffnen. 

![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. Ebenso wie in Schritt 3 müssen wir das//Entfernen, um den Code in den Zeilen 25, 26 und 106 zu aktivieren.

![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png) 

![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. Wählen Sie in der Hierarchie Ansicht das networkroom-Objekt aus.

![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. Navigieren Sie in der Projektansicht zu Assets-> Resources-> Prefabs. Ziehen Sie zuerst die Tabelle "Prefab" per Drag & Drop in den tableprefab-Slot der Klasse "photonroom". Ziehen Sie dann das lunarmodule-präfab per Drag & amp; Drop in das Modul Prefab-Slot der Klasse "photonroom".

![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

   Hinweis: Wenn Sie auf eines der Prefab-Objekte klicken und das Release durchführt, wechselt der Inspektor zu diesem Objekt. Klicken Sie auf, ziehen Sie die einzelnen Objekte in den entsprechenden Slot, und lassen Sie Sie dort ablegen.

8. Klicken Sie auf den Pfeil links neben mixedrealityplayspace, und verschieben Sie das untergeordnete Spielobjekt, maincamera, nach unten in die vorfab sharedplayground. Löschen Sie anschließend die Prefab-, mixedrealityplayspace-Eigenschaft, und wählen Sie die vorfab aus, und tippen Sie auf der Tastatur auf "Löschen".
![Module3hapter4step5im](images/module3chapter4step5im.PNG)

>Hinweis:  Stellen Sie sicher, dass sowohl die Hauptkamera-als auch die sharedplayground-Position auf 0, 0, 0 festgelegt ist.
>

9. Erstellen Sie ein neues Spielobjekt, das als untergeordnetes Objekt für das übergeordnete sharedplayground-Objekt festgelegt ist, um ein neues Objekt zu erstellen. Klicken Sie mit der rechten Maustaste auf das übergeordnete Objekt, und wählen Sie leere erstellen. 

10. Wenn das neue Objekt in Ihrer Hierarchie ausgewählt ist, ändern Sie im Inspektor-Panel den Namen des Objekts in tableanchor. Klicken Sie auch auf Komponente hinzufügen, und suchen Sie nach der tableanchor-Komponente. Wählen Sie Sie aus, und fügen Sie Sie dem-Objekt hinzu. 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> Hinweis: Legen Sie die Positionierung auf x = 1, y =-0,55 und z = 2 fest. Legen Sie außerdem die Drehung auf y = 90 fest. 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. Ziehen Sie nun aus dem Projekt Panel im Ordner "Prefabs" die Tabelle "Prefab" in das untergeordnete "tableanchor"-Objekt, das Sie soeben erstellt haben.

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

12. Ändern Sie schließlich im debugWindow-Objekt die Breite auf 50 und die Höhe auf 20.

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!


Sobald dieser Vorgang vollständig ist, können alle Benutzer, die Ihrem Unity-Projekt beitreten, das Mond-Start Programm verschieben. Alle Bewegungen werden synchronisiert, sodass jeder Benutzer die Interaktionen der anderen Benutzer sehen kann. Diese Konzepte dienen als wesentliche Bausteine für voll funktionsfähigen, gemeinsam genutzten Kollaborations Umgebungen. 

Obwohl alle Benutzer als Teil einer freigegebenen Umgebung verbunden sind und die relativen Bewegungen von Objekten sehen können, kann die Anwendung keine genaue Ausrichtung von Avatare und Objekten durchgeführt werden, sodass lokale Benutzer einander und Objekte an derselben Stelle innerhalb der physischen World. Um eine lokale gemeinsame Nutzung zu verankern, erfordert jedes Gerät ein gängiges Verständnis der physischen Umgebung. In diesem Modul erreichen wir dies mithilfe von [Azure Spatial](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) Anchor (ASA), die in der nächsten Lektion implementiert werden.

Bevor Sie mit der nächsten Lektion fortfahren, müssen wir das ASA-Lernmodul vervollständigen, das die ASA-Grundlagen, das Azure-Konto und die Ressourcen Erstellung und andere grundlegende Bausteine umfasst, die erforderlich sind, bevor wir dies in unsere freigegebene Erfahrung integrieren können.

[Nächste Lektion: Freigabe (Photon), Lektion 5](mrlearning-sharing(photon)-ch5.md)

