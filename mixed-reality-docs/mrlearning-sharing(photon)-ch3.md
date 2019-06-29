---
title: Lernen die Freigabe-Modul für HoloLens 2 MR
description: Führen Sie diesen Kurs erfahren, wie Sie mehrere Benutzer freigegebene Umgebungen innerhalb einer HoloLens-2-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 4625acfcb3353e9537961a444012452139705359
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465214"
---
# <a name="connecting-multiple-users"></a>**Verbinden von mehreren Benutzern** 

In dieser Lektion erfahren wir, wie um mehrere Benutzer als Teil einer freigegebenen zu verbinden. Am Ende dieser Lektion werden Sie in der Lage, öffnen Sie die Anwendung auf mehreren Geräten, und finden Sie unter Avatar, dargestellt durch eine Kugel, Darstellungen von jeder Person, die verknüpft. 

Ziele:

- Konfigurieren von WORTSPIEL innerhalb Ihrer Anwendung
- Konfigurieren der Spieler
- Erfahren Sie, wie die Verbindung mehrere Benutzer in einer gemeinsamen Erfahrung

### <a name="instructions"></a>Anweisungen

1. In den Assets -> Ressourcen -> Ordner "Prefabs" im Projektfenster Drag & drop die NetworkLobby Prefab in der Hierarchie wie in der folgenden Abbildung dargestellt.


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. Wenn Sie NetworkLobby erweitern, sehen Sie ein untergeordnetes Objekt NetworkRoom aufgerufen. Klicken Sie mit NetworkRoom ausgewählt haben wechseln Sie in den Bereich der Eigenschaftenanalyse, und klicken Sie auf die Komponente hinzufügen. PhotonView suchen Sie, und fügen Sie die Komponente.

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. Erstellen Sie ein neues, leeres game-Objekt, in der Hierarchie. Klicken Sie mit der rechten Maustaste in der Hierarchie, und wählen Sie im Kontextmenü der leer. Stellen Sie sicher, die Positionierung festgelegt ist, auf X = 0, y = 0, Z = 0, und nennen Sie das PhotonUser-Objekt.

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. Klicken Sie auf die Komponente hinzufügen, und geben Sie allgemeine Net-Synchronisierung. Wählen Sie die generische Net-Sync-Klasse. Die Klasse angezeigt wird, klicken Sie auf das Kontrollkästchen "Benutzer", um ihn zu aktivieren. 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. Klicken Sie erneut auf die Komponente hinzufügen, und geben Sie Photon anzeigen. Wählen Sie die Photon-View-Klasse, die angezeigt wird, in der Dropdown-Liste.

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. Klicken Sie auf das Symbol für die generische Net-Sync-Klasse. Ziehen Sie aus, und legen Sie sie in der Ansicht Photon beobachtet Komponenten Feld. ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. Als Nächstes erstellen wir die Kugeln zur Darstellung von jeder Person, die in einer gemeinsamen Erfahrung eingebunden. Klicken Sie mit der rechten Maustaste auf das PhotonUser-Objekt, das Sie gerade erstellt haben, und Scrolldown auf "3D-Objekt, und klicken Sie auf Kugel. Dadurch wird eine Kugel spielobjekt als untergeordnetes Element des Objekts PhotonUser erstellt.

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. Skalieren die Kugel auf X = 0,06, y = 0,06, Ad Z = 0,06.

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. Ziehen Sie das spielobjekt PhotonUser in den Ordner "Prefabs" im Projektfenster, und löschen Sie sie aus der Szene. Wir haben jetzt ein prefabs erstellt, das beim Erstellen oder das Instanziieren von neuen Spieler in einer freigegebenen Umgebung verwendet werden können.

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> Hinweis: Stellen Sie sicher, dass das spielobjekt in den Ordner "Prefabs" wurde erfolgreich kopiert hat, bevor Sie es in Ihrer Hierarchie zu löschen.

10. Erstellen Sie ein neues Objekt in der Hierarchie mithilfe der Anweisungen in Schritt 3, und nennen Sie sie SharedPlayground. Klicken Sie dann auf Komponente hinzufügen, suchen Sie nach der generischen Netzwerk-Manager und klicken Sie auf, um die generische Netzwerk-Manager-Komponente hinzufügen. Ändern Sie die Position des Objekts auf X = 0, y = 0 und Z = 0.

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>Herzlichen Glückwunsch!

Nachdem alle oben genannten Schritte abgeschlossen sind und auch der Buildprozess abgeschlossen ist, drücken Sie die entsprechende Schaltfläche, und verbinden Sie Ihre HoloLens-2. Eine Kugel verschieben, während des Verschiebens Kopf sollte angezeigt werden. Dies wird für alle Benutzer angezeigt, die in Ihrem Unity-Projekt eingebunden.

[Nächste Lektion: Sharing(Photon) Lektion 4](mrlearning-sharing(photon)-ch4.md)

