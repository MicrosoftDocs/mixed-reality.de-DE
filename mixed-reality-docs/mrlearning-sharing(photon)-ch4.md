---
title: Lernen die Freigabe-Modul für HoloLens 2 MR
description: Führen Sie diesen Kurs erfahren, wie Sie mehrere Benutzer freigegebene Umgebungen innerhalb einer HoloLens-2-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: a67eaef45582054b62198a563f0ee01724fd60db
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326540"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a>Synchronisieren von Verschiebungen von freigegebenen Objekten

In dieser Lektion erfahren wir, wie die Bewegungen der Objekte freigeben, damit alle Teilnehmer einer Sitzung gemeinsam genutzten Zusammenarbeit und den anderen Aktivitäten anzeigen können. Diese Lektion baut auf das Startprogramm des Mondes, die als Teil des erstellt wurde die [Base Modul Tutorials](mrlearning-base.md).

Ziele:

- Importieren Sie das Startprogramm für abgeschlossene auf als das 3D-Modell freigegeben werden
- Konfigurieren Sie das Projekt, um die Bewegungen des 3D-Modells freigeben.
- Erfahren Sie, wie Sie eine einfache Zusammenarbeit Mehrbenutzer-Anwendung erstellen

### <a name="instructions"></a>Anweisungen

1. Speichern Sie die Szene, aus der vorherigen Lektion (STRG + S). Sie können "HLSharedProjectMainPart4.unity" Namen, damit es ist einfacher zu finden, wenn Sie ihn wieder benötigen.

2. Löschen Sie das Objekt "NetworkLobby" (indem Sie ihn auswählen und löschen). Darüber hinaus ein Wechsel in den Ordner "Prefabs" aus Lektion 2 aus, und löschen Sie das Prefab "NetworkLobby" auch von dort.

![Module3Chapter4tep2im](images/module3chapter4step2im.PNG)

3. Importieren Sie ein neues benutzerdefiniertes Paket (z. B. in Schritt 2 aus der Lektion 2), und importieren Sie die [LunarModule.unitypackage](linkforModule1 lesson with the lunar module) und [NetworkLobbyReplacement.unitypackage.](linkforNetworklobbyreplacement package here)

![Module3Chapter4step3im](images/module3chapter4step3im.PNG)

4. Ziehen Sie nun im Ordner "Prefabs" die neue "NetworkLobby" Prefab in der Hierarchie. 

![Module3hapter4step4im](images/module3chapter4step4im.PNG)

> Hinweis: die beiden Pakete, die wir in den vorherigen Schritten importiert aktualisiert das Prefab "NetworkLobby". Es erspart Ihnen viele eingeben.

5. Jetzt klicken Sie auf den Pfeil links neben "MixedRealityPlayspace", und verschieben Sie das untergeordnete-spielobjekt "MainCamera" in das Prefab "SharedPlayground" nach unten zu. Löschen Sie dann das prefab "MixedRealityPlayspace" (zum Löschen, wählen Sie das Prefab aus, und tippen Sie auf der Tastatur auf "löschen").

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

6. Erstellen Sie ein neues Spiels-Objekt als ein untergeordnetes Objekt festgelegt, um das übergeordnete Objekt "SharedPlayground" (um ein neues Objekt erstellen, klicken Sie mit der rechten Maustaste auf das übergeordnete Objekt, und wählen Sie "leere erstellen").
7. Mit dem neuen Objekt in der Hierarchie ausgewählt haben ändern Sie den Namen des Objekts in "TableAnchor", in den Bereich der Eigenschaftenanalyse. Darüber hinaus klicken Sie auf "Komponente hinzufügen" aus, und suchen Sie nach der Komponente "TableAnchor". Wählen sie aus, und fügen Sie es auf das Objekt hinzu.

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> Hinweis: Legen Sie die Positionierung auf X = 1, y =-0,55 und Z = 2. Legen Sie außerdem die Drehung y = 90. 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

8. Im Bedienfeld "Projekt" im Ordner "Prefabs" ziehen Sie jetzt das Prefab "Table" in das "TableAnchor" untergeordnete Objekt an, die, das Sie gerade erstellt haben.

   ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

9. Wählen Sie "NetworkRoom", ein untergeordnetes Objekt unter "NetworkLobby" in der Hierarchie, und klicken Sie auf "Komponente hinzufügen" im Inspektor-Bereich und suchen Sie nach "PhotonView" und fügen Sie das Skript, das "*NetworkRoom*" Objekt.

![Module3Chapter4step9im](images/module3chapter4step9im.PNG)

11. Ändern Sie im Objekt "DebugWindow" schließlich die Breite auf 80 und die Höhe in 10.

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sobald dies abgeschlossen ist, können alle Benutzer, die Ihr Unity-Projekt verknüpfen das Startprogramm des Mondes bewegen. Alle Bewegungen werden synchronisiert, sodass jeder Benutzer voneinander Interaktionen sehen kann. Diese Konzepte dienen als die grundlegenden Bausteine für die Funktionen für die gemeinsame Zusammenarbeit mit vollem Funktionsumfang. 

Obwohl alle Benutzer, die als Teil einer gemeinsamen Erfahrung verbunden sind und die relative Verschiebungen von Objekten angezeigt, ist die Anwendung immer noch nicht genau Avatare und Objekte so ausrichten, dass lokale Benutzer und der jeweils anderen Objekte am selben Ort innerhalb der physischen finden Sie unter World. Um einen lokalen freigegebenen Umgebungen zu verankern, erfordert jedes Gerät ein allgemeines Verständnis der physischen Umgebung. In diesem Modul wir wird verwenden zu diesem Zweck [Azure räumliche Anker](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), wird die in der nächsten Lektion implementiert werden.

Bevor Sie mit der nächsten Lektion fortfahren müssen wir das ASA-Learning-Modul durchführen, die erforderlichen Azure-Konto und das Erstellen von Ressourcen und andere grundlegende Gebäude Blöcke ASA "grundlegende Einstellungen" beschrieben wird, bevor wir dies in unserem gemeinsamen Erfahrung integrieren können.

[Nächste Lektion: Sharing(Photon) Lektion 5](mrlearning-sharing(photon)-ch5.md)

