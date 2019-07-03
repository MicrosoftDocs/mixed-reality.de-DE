---
title: Lernen die Freigabe-Modul für HoloLens 2 MR
description: Führen Sie diesen Kurs erfahren, wie Sie mehrere Benutzer freigegebene Umgebungen innerhalb einer HoloLens-2-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 2a4ea599fd4887f30589c2d839be305d3dc8d1bd
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523193"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. Objekt Bewegungen freigeben für mehrere Benutzer

In diesem Tutorial erfahren wir, wie die Bewegungen der Objekte freigeben, damit alle Teilnehmer einer Sitzung gemeinsam genutzten Zusammenarbeit und den anderen Aktivitäten anzeigen können. Diese Lektion baut auf das Startprogramm des Mondes, die als Teil des erstellt wurde die [Base Modul Tutorials](mrlearning-base.md).

Ziele:

- Führen Sie das Startprogramm auf als das 3D-Modell um gemeinsam genutzt werden
- Konfigurieren Sie das Projekt, um die Bewegungen des 3D-Modells freigeben.
- Erfahren Sie, wie Sie eine einfache Zusammenarbeit Mehrbenutzer-Anwendung erstellen

### <a name="instructions"></a>Anweisungen


1. Speichern Sie die Szene, aus der vorherigen Lektion (Control + S). Sie können es HLSharedProjectMainPart4.unity, Namen, damit es ist leichter zu finden, wenn Sie es benötigen.

2. Klicken Sie aus dem Projektfenster in den Assets -> Ordner "Scripts", einen Doppelklick auf GenericNetSync, öffnen Sie sie in Visual Studio oder die jemals code Editor an, die Sie verwenden.  ![](images/module3chapter4updatestep2.png)

3. Entfernen Sie auf die Zeilen 34 und 38, die / bzw. in den Code für die Tabelle zu aktivieren, die wir in dieser Lektion verwenden. als Nächstes speichern Sie die Datei an. ![](images/module3chapter4updatestep3.png)

4. Das Projektfenster Doppelklicken Sie auf die PhotonRoom.cs-Datei in den Assets -> Ordner "Scripts", die sie in Visual Studio zu öffnen. ![](images/module3chapter4updatestep4.png)

5. Genau wie in Schritt 3, wir entfernen müssen das / / zum Aktivieren des Codes in den Zeilen, 106, 25 und 26.![](images/module3chapter4updatestep5a.png) ![](images/module3chapter4updatestep5b.png)

6. Wählen Sie in der Ansicht der Hierarchie das NetworkRoom-Objekt.![](images/module3chapter4updatestep6.png)

7. Navigieren Sie in der Projektansicht zum Ressourcen-Ressourcen > -> prefabs (Vorlagen). Zunächst Drag & drop den Tabelle-Prefab zum Tableprefab Steckplatz auf dem die PhotonRoom-Klasse. Als Nächstes ziehen und Ablegen von der LunarModule Prefab zum Modul Prefab Steckplatz auf dem die PhotonRoom-Klasse. ![](images/module3chapter4updatestep7.png)

   Hinweis: Wenn Sie auf einem prefab Objekte und-Version klicken, wechselt der Inspektor auf dieses Objekt. Klicken Sie auf, ziehen Sie, löschen Sie und freigeben Sie, jedes Objekt in seine entsprechende Slot.



8. Klicken Sie auf den Pfeil links neben MixedRealityPlayspace, und verschieben Sie das untergeordnete-spielobjekt MainCamera in das Prefab SharedPlayground nach unten. Löschen Sie anschließend das Prefab, MixedRealityPlayspace, löschen, wählen Sie das Prefab, und tippen Sie auf der Tastatur auf "löschen").
![Module3hapter4step5im](images/module3chapter4step5im.PNG)

Hinweis:  Stellen Sie sicher, dass sowohl die SharedPlayground die Main Camera Positionen auf 0,0,0 festgelegt werden.

9. Erstellen Sie ein neues Spiels-Objekt als untergeordnetes Objekt auf das SharedPlayground übergeordnete Objekt festgelegt, um ein neues Objekt erstellen. Klicken Sie mit der rechten Maustaste auf das übergeordnete Objekt, und wählen Sie leere erstellen. 

10. Mit dem neuen Objekt in der Hierarchie ausgewählt haben ändern Sie den Namen des Objekts in TableAnchor, in den Bereich der Eigenschaftenanalyse. Darüber hinaus klicken Sie auf die Komponente hinzufügen, und suchen Sie nach der TableAnchor-Komponente. Wählen sie aus, und fügen Sie es auf das Objekt hinzu. 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> Hinweis: Legen Sie die Positionierung auf X = 1, y =-0,55 und Z = 2. Legen Sie außerdem die Drehung y = 90. 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. Ziehen Sie jetzt aus dem Projektfenster in den Ordner "Prefabs", das Prefab Tabelle in das "TableAnchor" untergeordnete Objekt an, die, das Sie gerade erstellt haben.

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. Ändern Sie die Breite auf 80 und die Höhe auf 10 schließlich im DebugWindow-Objekt.

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a>Herzlichen Glückwunsch!


Sobald dies abgeschlossen ist, können alle Benutzer, die Ihr Unity-Projekt verknüpfen das Startprogramm des Mondes bewegen. Alle Bewegungen werden synchronisiert, sodass jeder Benutzer voneinander Interaktionen sehen kann. Diese Konzepte dienen als die grundlegenden Bausteine für die Funktionen für die voll funktionsfähige, gemeinsam genutzte Zusammenarbeit. 

Obwohl alle Benutzer, die als Teil einer freigegebenen Umgebung verbunden sind, und Sie, dass die relative Verschiebungen von Objekten sehen, ist die Anwendung immer noch nicht genau Avatare und Objekte so ausrichten, dass lokale Benutzer und der jeweils anderen Objekte am selben Ort innerhalb der physischen finden Sie unter World. Um einen lokalen freigegebenen Umgebungen zu verankern, erfordert jedes Gerät ein allgemeines Verständnis der physischen Umgebung. In diesem Modul werden wir dies mit erreichen [Azure räumliche Anker](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), wird in der nächsten Lektion implementiert werden.

Bevor Sie mit der nächsten Lektion fortfahren müssen wir das ASA-Learning-Modul durchführen, die ASA-Grundlagen behandelt Azure-Konto und das Erstellen von Ressourcen und andere grundlegende Gebäude Blöcke erforderlich, bevor wir dies in unserem gemeinsamen Erfahrung integrieren können.

[Nächste Lektion: Sharing(Photon) Lektion 5](mrlearning-sharing(photon)-ch5.md)

