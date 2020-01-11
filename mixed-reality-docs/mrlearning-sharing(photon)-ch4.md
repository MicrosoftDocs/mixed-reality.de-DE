---
title: Lernprogramme für Mehrbenutzerfunktionen-4. Freigeben von Objektbewegungen mit mehreren Benutzern
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Umgebungen mit mehreren Benutzern in einer hololens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: f1bcbbd368635c25207127142f21ff50f26a7b58
ms.sourcegitcommit: 2bfe9b1af4ee2cc0d668caeccb8ebc3137cbc20b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901482"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. Freigeben von Objektbewegungen für mehrere Benutzer

In diesem Tutorial erfahren Sie, wie Sie die Bewegungen von Objekten freigeben, damit alle Teilnehmer einer freigegebenen Sitzung zusammenarbeiten und die Interaktionen der einzelnen Benutzer anzeigen können. Diese Lektion baut auf dem Mond Start Programm auf, das als Teil der Lernprogramme für das [Basismodul](mrlearning-base.md)erstellt wurde.

## <a name="objectives"></a>Ziele

- Bringen Sie das Mond Startfeld als 3D-Modell ein, das freigegeben werden soll.
- Konfigurieren des Projekts für die Freigabe der Bewegungen des 3D-Modells
- Erfahren Sie, wie Sie eine grundlegende Anwendung für mehrere Benutzer Anwendungen erstellen.

## <a name="instructions"></a>Anweisungen

1. Speichern Sie die Szene aus der vorherigen Lektion (Control + S). Sie können den Namen HLSharedProjectMainPart4. unity benennen, damit er bei Bedarf leichter zu finden ist.

2. Doppelklicken Sie im Projektfenster im Ordner Assets-> Scripts auf genericnetsync, um ihn in Visual Studio oder in dem von Ihnen verwendeten Code-Editor zu öffnen.  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. Entfernen Sie in den Zeilen 34 und 38 "//", um den Code für die Tabelle zu aktivieren, die Sie in dieser Lektion verwenden werden. Speichern Sie dann die Datei.

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. Doppelklicken Sie im Projektfenster im Ordner Assets-> Scripts auf die Datei PhotonRoom.cs, um Sie in Visual Studio zu öffnen.

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. Ebenso wie in Schritt 3 müssen wir "//" entfernen, um den Code in den Zeilen 25, 26 und 106 zu aktivieren.

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. Wählen Sie in der Hierarchie Ansicht das networkroom-Objekt aus.

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. Navigieren Sie in der Projektansicht zu Assets-> Resources-> Prefabs. Ziehen Sie zuerst die Tabelle "Prefab" per Drag & Drop in den tableprefab-Slot der Klasse "photonroom". Ziehen Sie als nächstes das rocketlaunchercompletevariantprefab-Element in den Prefab-Slot der Klasse "photonroom".

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    >Wenn Sie auf eines der Prefab-Objekte klicken und das Release durchführt, wechselt der Inspektor zu diesem Objekt. Klicken Sie auf, ziehen Sie die einzelnen Objekte in den entsprechenden Slot, und lassen Sie Sie dort ablegen.

8. Klicken Sie auf den Pfeil links neben mixedrealityplayspace, und verschieben Sie das untergeordnete Spielobjekt maincamera nach unten in die vorfab sharedplayground. Löschen Sie anschließend den Prefab-, mixedrealityplayspace-Wert, indem Sie die vorfab auswählen und auf der Tastatur auf "Löschen" tippen.

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    >Stellen Sie sicher, dass sowohl die Hauptkamera-als auch die sharedplayground-Position auf 0, 0, 0 festgelegt ist.

9. Wählen Sie das Objekt "sharedplayground" aus, und klicken Sie mit der rechten Maustaste auf die Option "leere erstellen", um ein leeres Spielobjekt als untergeordnetes Element des Spiel Objekts "sharedplayground" zu erstellen.

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. Wenn das neue Objekt in Ihrer Hierarchie ausgewählt ist, ändern Sie im Inspektor-Panel den Namen des Objekts in tableanchor. Klicken Sie auch auf Komponente hinzufügen, und suchen Sie nach der tableanchor-Komponente. Wählen Sie Sie aus, und fügen Sie Sie dem-Objekt hinzu.

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. Ziehen Sie aus dem Projekt Panel im Ordner "Prefabs" die Tabelle "Prefab" in das untergeordnete "tableanchor"-Objekt, das Sie soeben erstellt haben.

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sobald dies erfolgt ist, sehen Sie sich das Mond Modul an. Danach können alle Benutzer, die Ihrem Unity-Projekt beitreten, das Mond-Start Programm verschieben.  Alle Bewegungen werden synchronisiert, sodass jeder Benutzer die Interaktionen der anderen Benutzer sehen kann. Diese Konzepte dienen als wesentliche Bausteine für voll funktionsfähigen, gemeinsam genutzten Kollaborations Umgebungen.

Obwohl alle Benutzer als Teil einer freigegebenen Umgebung verbunden sind und die relativen Bewegungen von Objekten sehen können, kann die Anwendung keine genaue Ausrichtung von Avatare und Objekten durchgeführt werden, sodass die lokalen Benutzer keine anderen Objekte und Objekte an derselben Stelle innerhalb des physische Welt. Um eine lokale gemeinsame Nutzung zu verankern, erfordert jedes Gerät ein gängiges Verständnis der physischen Umgebung. In diesem Modul erreichen wir dies mithilfe von [Azure Spatial](<https://azure.microsoft.com//services/spatial-anchors/>) Anchor (ASA), das in der nächsten Lektion implementiert wird.

Bevor Sie mit der nächsten Lektion fortfahren, müssen wir das ASA-Lernmodul vervollständigen, das die ASA-Grundlagen, das Azure-Konto und die Ressourcen Erstellung behandelt, sowie andere grundlegende Bausteine, die erforderlich sind, bevor wir dies in unsere freigegebene Erfahrung integrieren können.

[Nächste Lektion: 5. Integration von Azure Spatial Anchor in eine freigegebene Erfahrung](mrlearning-sharing(photon)-ch5.md)
