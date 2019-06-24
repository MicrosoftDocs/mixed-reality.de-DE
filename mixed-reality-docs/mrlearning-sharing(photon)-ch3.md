---
title: Lernen die Freigabe-Modul für HoloLens 2 MR
description: Führen Sie diesen Kurs erfahren, wie Sie mehrere Benutzer freigegebene Umgebungen innerhalb einer HoloLens-2-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: f2e8cef618ea2fbee398ce19f1ba60b712b5fe3e
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327940"
---
# <a name="connecting-multiple-users"></a>**Verbinden von mehreren Benutzern** 

In dieser Lektion lernen wir, wie Sie mehrere Benutzer als Teil einer freigegebenen zu verbinden. Am Ende dieser Lektion werden Sie in der Lage, öffnen Sie die Anwendung auf mehreren Geräten, und finden Sie unter "Avatar"-Darstellungen von jeder Person, die verknüpft (Avatare durch eine Kugel dargestellt.) 

Ziele:

- Konfigurieren von WORTSPIEL innerhalb Ihrer Anwendung
- Konfigurieren der Spieler
- Erfahren Sie, wie die Verbindung mehrere Benutzer in einer gemeinsamen Erfahrung

### <a name="instructions"></a>Anweisungen

1. In den Assets > Ressourcen > Prefabs Ordner, der den Projektbereich, Drag & Drop die "NetworkLobby" in der Hierarchie prefab wie in der folgenden Abbildung dargestellt.


![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. Wenn Sie auf das prefab "NetworkLobby" erweitern, sehen Sie ein untergeordnetes Objekt namens "NetworkRoom." Klicken Sie mit der sie ausgewählt haben wechseln Sie in den Bereich der Eigenschaftenanalyse, und klicken Sie auf "Komponente hinzufügen" aus. Suchen Sie nach "PhotonView", und fügen Sie die Komponente.

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. Erstellen Sie ein neues, leeres game-Objekt in der Hierarchie (klicken Sie mit der rechten Maustaste in der Hierarchie, und wählen Sie im Kontextmenü auf "Leer"). Stellen Sie sicher, die Positionierung festgelegt ist, auf X = 0, y = 0, Z = 0, und nennen Sie das Objekt "PhotonUser."

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. Als Nächstes möchten wir zum Erstellen von Kugeln zur Darstellung von jeder Person, die in einer gemeinsamen Erfahrung eingebunden. Klicken Sie mit der rechten Maustaste auf das "PhotonUser"-Objekt, das Sie gerade erstellt haben, wechseln Sie in "3D Object" und klicken Sie auf "Kugel". Dadurch wird eine Kugel spielobjekt als untergeordnetes Element des Objekts PhotonUser erstellt.

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

5. Skalieren die Kugel auf X = 0,06, y = 0,06, Ad Z = 0,06.

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

6. Ziehen Sie das Spiele "PhotonUser"-Objekt in den Ordner "Prefabs" im Projektfenster. Klicken Sie dann löschen Sie sie aus der Szene. Wir haben jetzt ein prefabs erstellt, das beim Erstellen oder das Instanziieren von neuen Spieler in einer freigegebenen Umgebung verwendet werden.

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> Hinweis: Stellen Sie sicher, dass das spielobjekt in den Ordner "prefabs" erfolgreich kopiert wurde, bevor Sie es in Ihrer Hierarchie zu löschen.

7. Erstellen Sie ein neues Objekt in der Hierarchie (mit ähnlichen Anweisungen, um mit Schritt 3), und nennen Sie es "SharedPlayground." Anschließend klicken Sie auf "Komponente hinzufügen", und suchen Sie nach "generische Netzwerkmanager", und klicken Sie auf, um die generische Netzwerk-Manager-Komponente hinzufügen. Ändern Sie die Position des Objekts auf X = 0, y = 0 und Z = 0.

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>Herzlichen Glückwunsch!

Nachdem alle oben genannten Schritte abgeschlossen sind und der Buildprozess abgeschlossen ist, wenn Sie drücken Sie die entsprechende Schaltfläche, und verbinden Ihre HoloLens-2, sehen Sie eine Kugel verschieben, während des Verschiebens Kopf! Dies wird für alle Benutzer angezeigt, die in Ihrem Unity-Projekt eingebunden.

[Nächste Lektion: Sharing(Photon) Lektion 4](mrlearning-sharing(photon)-ch4.md)

