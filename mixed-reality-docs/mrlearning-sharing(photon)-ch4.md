---
title: Lernen die Freigabe-Modul für HoloLens 2 MR
description: Führen Sie diesen Kurs erfahren, wie Sie mehrere Benutzer freigegebene Umgebungen innerhalb einer HoloLens-2-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: d5bed61f5ffc1d3b4efed96f47c3568fbf3a2948
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416011"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a>Synchronisieren von Verschiebungen von freigegebenen Objekten

In dieser Lektion erfahren wir, wie die Bewegungen der Objekte freigeben, damit alle Teilnehmer einer Sitzung gemeinsam genutzten Zusammenarbeit und den anderen Aktivitäten anzeigen können. Diese Lektion baut auf das Startprogramm des Mondes, die als Teil des erstellt wurde die [Base Modul Tutorials](mrlearning-base.md).

Ziele:

- Führen Sie das Startprogramm auf als das 3D-Modell um gemeinsam genutzt werden
- Konfigurieren Sie das Projekt, um die Bewegungen des 3D-Modells freigeben.
- Erfahren Sie, wie Sie eine einfache Zusammenarbeit Mehrbenutzer-Anwendung erstellen

### <a name="instructions"></a>Anweisungen

1. Speichern Sie die Szene, aus der vorherigen Lektion (STRG + S). Sie können "HLSharedProjectMainPart4.unity" Namen, damit es ist einfacher zu finden, wenn Sie ihn wieder benötigen.

2. Im Projektfenster, in den Assets > Ordner "Scripts", doppelklicken Sie auf GenericNetSync, öffnen Sie sie in Visual Studio oder dem Editor jemals code Sie verwenden.  ![](images/module3chapter4updatestep2.png)

3. In den Zeilen, 34 und 38, entfernen Sie die "/ /", den Code für die Tabelle zu aktivieren, die wir in dieser Lektion verwenden.  Speichern Sie die Datei. ![](images/module3chapter4updatestep3.png)

4. Das Projektfenster, doppelklicken klicken Sie auf die PhotonRoom.cs-Datei in den Assets > Ordner "Scripts" erneut, es in Visual Studio zu öffnen. ![](images/module3chapter4updatestep4.png)

5. Genau wie in Schritt 3 wir entfernen müssen das "/ /", aktivieren den Code in den Zeilen, 106, 25 und 26.![](images/module3chapter4updatestep5a.png) ![](images/module3chapter4updatestep5b.png)

6. Wählen Sie in der Ansicht der Hierarchie das NetworkRoom-Objekt.![](images/module3chapter4updatestep6.png)

7. Navigieren Sie in der Projektansicht zum Bestand > Ressourcen > prefabs (Vorlagen). Zunächst Drag & drop den Tabelle-Prefab im Slot "Tableprefab" für die PhotonRoom-Klasse. Als Nächstes ziehen und Ablegen von der LunarModule Prefab zum "Modul Prefab" Steckplatz auf dem die PhotonRoom-Klasse. ![](images/module3chapter4updatestep7.png)

   Hinweis: Wenn Sie auf einem prefab Objekte und-Version klicken, wechselt der Inspektor auf dieses Objekt. Klicken Sie auf, drag, drop, und jedes Objekt in seine entsprechende Slot freizugeben.



8. Jetzt klicken Sie auf den Pfeil links neben "MixedRealityPlayspace", und verschieben Sie das untergeordnete-spielobjekt "MainCamera" in das Prefab "SharedPlayground" nach unten zu. Löschen Sie dann das prefab "MixedRealityPlayspace" (zum Löschen, wählen Sie das Prefab aus, und tippen Sie auf der Tastatur auf "löschen").

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

Hinweis:  Stellen Sie sicher, dass sowohl die SharedPlayground die Main Camera Positionen auf 0,0,0 festgelegt werden.

9. Erstellen Sie ein neues Spiels-Objekt als ein untergeordnetes Objekt festgelegt, um das übergeordnete Objekt "SharedPlayground" (um ein neues Objekt erstellen, klicken Sie mit der rechten Maustaste auf das übergeordnete Objekt, und wählen Sie "leere erstellen"). 

10. Mit dem neuen Objekt in der Hierarchie ausgewählt haben ändern Sie den Namen des Objekts in "TableAnchor", in den Bereich der Eigenschaftenanalyse. Darüber hinaus klicken Sie auf "Komponente hinzufügen" aus, und suchen Sie nach der Komponente "TableAnchor". Wählen sie aus, und fügen Sie es auf das Objekt hinzu. 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> Hinweis: Legen Sie die Positionierung auf X = 1, y =-0,55 und Z = 2. Legen Sie außerdem die Drehung y = 90. 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. Im Bedienfeld "Projekt" im Ordner "Prefabs" ziehen Sie jetzt das Prefab "Table" in das "TableAnchor" untergeordnete Objekt an, die, das Sie gerade erstellt haben.

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. Ändern Sie im Objekt "DebugWindow" schließlich die Breite auf 80 und die Höhe in 10.

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sobald dies abgeschlossen ist, können alle Benutzer, die Ihr Unity-Projekt verknüpfen das Startprogramm des Mondes bewegen. Alle Bewegungen werden synchronisiert, sodass jeder Benutzer voneinander Interaktionen sehen kann. Diese Konzepte dienen als die grundlegenden Bausteine für die Funktionen für die gemeinsame Zusammenarbeit mit vollem Funktionsumfang. 

Obwohl alle Benutzer, die als Teil einer gemeinsamen Erfahrung verbunden sind und die relative Verschiebungen von Objekten angezeigt, ist die Anwendung immer noch nicht genau Avatare und Objekte so ausrichten, dass lokale Benutzer und der jeweils anderen Objekte am selben Ort innerhalb der physischen finden Sie unter World. Um einen lokalen freigegebenen Umgebungen zu verankern, erfordert jedes Gerät ein allgemeines Verständnis der physischen Umgebung. In diesem Modul wir wird verwenden zu diesem Zweck [Azure räumliche Anker](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), wird die in der nächsten Lektion implementiert werden.

Bevor Sie mit der nächsten Lektion fortfahren müssen wir das ASA-Learning-Modul durchführen, die erforderlichen Azure-Konto und das Erstellen von Ressourcen und andere grundlegende Gebäude Blöcke ASA "grundlegende Einstellungen" beschrieben wird, bevor wir dies in unserem gemeinsamen Erfahrung integrieren können.

[Nächste Lektion: Sharing(Photon) Lektion 5](mrlearning-sharing(photon)-ch5.md)

