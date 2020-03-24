---
title: 'Tutorials zu Mehrbenutzerfunktionen: 3 Verbinden mehrerer Benutzer'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: cbe0d8d2db6c34ba262fe9c946b68366ed3dbb93
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031231"
---
# <a name="3-connecting-multiple-users"></a>3. Verbinden mehrerer Benutzer

In dieser Lektion erfahren Sie, wie Sie mehrere Benutzer im Rahmen einer freigegebenen Live-Benutzererfahrung verbinden. Am Ende dieser Lektion sind Sie in der Lage, die Anwendung auf mehreren Geräten zu öffnen und den Avatar anzuzeigen, der durch eine Kugel für jede teilnehmende Person dargestellt wird.

## <a name="objectives"></a>Ziele

* Konfigurieren von PUN innerhalb Ihrer Anwendung
* Konfigurieren von Playern
* Erlernen des Verbindens mehrerer Benutzer in einer freigegebenen Umgebung

## <a name="instructions"></a>Anweisungen

1. Ziehen Sie im Ordner „Assets->Resources->Prefabs“ des Projektbereichs das NetworkLobby-Prefab auf die Hierarchie, und legen Sie es ab, wie in der Abbildung unten dargestellt.

    ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. Wenn Sie NetworkLobby aufklappen, sehen Sie ein untergeordnetes Objekt mit dem Namen NetworkRoom. Wechseln Sie mit ausgewähltem NetworkRoom-Objekt zum Inspektorbereich, und klicken Sie auf „Komponente hinzufügen“. Suchen Sie nach PhotonView, und fügen Sie die Komponente hinzu.

    ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. Erstellen Sie ein neues leeres Spielobjekt in der Hierarchie. Klicken Sie mit der rechten Maustaste in die Hierarchie, und wählen Sie im Kontextmenü „Leer“ aus. Achten Sie darauf, dass die Position auf x=0, y=0, z=0 festgelegt ist, und benennen Sie das Objekt PhotonUser.

    ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. Klicken Sie auf „Komponente hinzufügen“, und geben Sie „Generic Net Sync“ ein. Wählen Sie die Klasse „Generic Net Sync“ aus. Wenn die Klasse angezeigt wird, klicken Sie auf das Kontrollkästchen „Benutzer“, um es zu aktivieren.

    ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. Klicken Sie erneut auf „Komponente hinzufügen“, und geben Sie „Photon View“ ein. Wählen Sie die Klasse „Photon View“ aus, die in der Dropdownliste angezeigt wird.

    ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. Klicken Sie auf das Dateisymbol für die Generic Net Sync-Klasse. Ziehen Sie die Klasse auf das Feld „Observed Components“ von Photon View.

    ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png)

7. Als nächstes erstellen wir Kugeln zum Darstellen der einzelnen Personen, die an einer freigegebenen Benutzererfahrung teilnehmen. Klicken Sie mit der rechten Maustaste auf das soeben erstellte PhotonUser-Objekt, scrollen Sie nach unten bis zu „3D Object“, und klicken Sie auf „Sphere“. Dadurch wird ein Kugelspielobjekt als untergeordnetes Objekt des PhotonUser-Objekts erstellt.

    ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. Verkleinern Sie die Kugel auf x=0,06, y=0,06 und z=0,06.

    ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. Ziehen Sie das PhotonUser-Spielobjekt auf den Prefabs-Ordner im Projektbereich, und löschen Sie ihn dann aus der Szene. Sie haben nun ein Prefab erstellt, das beim Erstellen oder Instanziieren neuer Spieler in einer freigegebenen Benutzererfahrung verwendet werden kann.

    ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

    >[!NOTE]
    >Vergewissern Sie sich, dass das Spielobjekt erfolgreich in den Prefabs-Ordner kopiert wurde, bevor Sie es aus der Hierarchie löschen.

10. Erstellen Sie ein neues-Objekt in der Hierarchie, indem Sie die Anweisungen in Schritt 3 befolgen, und nennen Sie es SharedPlayground. Klicken Sie anschließend auf „Komponente hinzufügen“, und suchen Sie nach dem generischen Netzwerk-Manager.  Klicken Sie erneut, um die Komponente „Generic Network Manager“ hinzuzufügen. Ändern Sie die Position des Objekts in x = 0, y = 0 und z = 0.

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Nachdem Sie alle Schritte oben ausgeführt haben und der Buildvorgang ebenfalls abgeschlossen ist, drücken Sie die Wiedergabe-Schaltfläche, und stellen Sie eine Verbindung mit Ihrer HoloLens 2 her. Sie sollten eine Kugel sehen, die sich umherbewegt, wenn Sie Ihren Kopf bewegen. Dies wird für jeden Benutzer angezeigt, der Ihrem Unity-Projekt beitritt.

[Nächste Lektion: 4. Freigeben von Objektbewegungen für mehrere Benutzer](mrlearning-sharing(photon)-ch4.md)
