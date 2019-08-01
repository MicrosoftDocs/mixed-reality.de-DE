---
title: Lernprogramme für Mehrbenutzerfunktionen-3. Verbinden von mehreren Benutzern
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Umgebungen mit mehreren Benutzern in einer hololens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: d3068a1ebbbc2b6db8b563be8bf8c6e488e9491a
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701938"
---
# <a name="3-connecting-multiple-users"></a>3. Verbinden von mehreren Benutzern

In dieser Lektion erfahren Sie, wie Sie mehrere Benutzer im Rahmen einer Live-freigegebenen Benutzererfahrung verbinden. Am Ende dieser Lektion sind Sie in der Lage, die Anwendung auf mehreren Geräten zu öffnen und den von einer Kugel dargestellten Avatar durch Darstellungen der einzelnen Joins anzuzeigen. 

Ziele

- Konfigurieren von Wortspiel innerhalb Ihrer Anwendung
- Konfigurieren von Playern
- Erfahren Sie, wie Sie mehrere Benutzer mit einer gemeinsamen Benutzer Verbindung verbinden.

## <a name="instructions"></a>Anweisungen

1. Ziehen Sie im Projekt Panel im Ordner Assets-> Resources-> Prefabs den Ordner "networklobby" in die Hierarchie, wie in der folgenden Abbildung dargestellt.

![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. Wenn Sie networklobby erweitern, sehen Sie ein untergeordnetes Objekt mit dem Namen networkroom. Wenn Sie Network Room ausgewählt haben, wechseln Sie im Inspektor-Panel, und klicken Sie auf Komponente hinzufügen. Suchen Sie nach photonview, und fügen Sie die Komponente hinzu.

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. Erstellen Sie ein neues leeres Spielobjekt in der Hierarchie. Klicken Sie mit der rechten Maustaste in die Hierarchie, und wählen Sie im Kontextmenü leer aus. Stellen Sie sicher, dass die Positionierung auf x = 0, y = 0, z = 0 festgelegt ist, und benennen Sie das Objekt "photonuser".

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. Klicken Sie auf Komponente hinzufügen, und geben Sie Generic net Sync ein. Wählen Sie die generische net Sync-Klasse aus. Wenn die Klasse angezeigt wird, klicken Sie auf das Kontrollkästchen Benutzer, um Sie zu aktivieren. 

![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. Klicken Sie erneut auf Komponente hinzufügen, und geben Sie "Photon View" ein Wählen Sie die in der Dropdown Liste angezeigte Klasse der Photon-Ansicht aus.

![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. Klicken Sie auf das Dateisymbol für die generische net Sync-Klasse. Ziehen Sie es in das Feld beobachtete Komponenten der Photon-Ansicht. 

![module3chapter3updateStep6im. png](images/module3chapter3updateStep6im.png) 

7. Als Nächstes erstellen wir Bereiche, die jede Person darstellen, die mit einer gemeinsamen Benutzerfunktion verbunden ist. Klicken Sie mit der rechten Maustaste auf das soeben erstellte Objekt "photonuser", Scrollen Sie zu "3D-Objekt, und klicken Sie auf Kugel. Dadurch wird ein Kugel Spielobjekt als untergeordnetes Element des photonuser-Objekts erstellt.

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. Skalieren Sie die Kugel auf x = 0,06, y = 0,06, AD z = 0,06.

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. Ziehen Sie das "photonuser"-Spielobjekt in den Ordner "Prefabs" im Projekt Panel, und löschen Sie es aus der Szene. Wir haben nun ein präfab erstellt, das verwendet werden kann, um neue Player in einer gemeinsamen Darstellung zu erstellen oder zu instanziieren.

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> Hinweis: Stellen Sie sicher, dass das Spielobjekt erfolgreich in den Ordner "Prefabs" kopiert wurde, bevor es aus der Hierarchie gelöscht wird.

10. Erstellen Sie ein neues-Objekt in der Hierarchie, indem Sie die Anweisungen in Schritt 3 befolgen, und benennen Sie es sharedplayground. Klicken Sie dann auf Komponente hinzufügen, suchen Sie nach generischem Netzwerk-Manager, und klicken Sie darauf, um die generische Netzwerk-Manager-Komponente hinzuzufügen. Ändern Sie die Position des Objekts in x = 0, y = 0 und z = 0.

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>Herzlichen Glückwunsch!

Nachdem alle oben aufgeführten Schritte ausgeführt wurden und der Buildprozess ebenfalls vollständig ist, klicken Sie auf die Schaltfläche Wiedergabe, und verbinden Sie die hololens 2. Wenn Sie Ihre Kopfzeile bewegen, sollte eine Kugel angezeigt werden. Dies wird für jeden Benutzer angezeigt, der Ihrem Unity-Projekt Beitritt.

[Nächste Lektion: 4. Freigeben von Objektbewegungen für mehrere Benutzer](mrlearning-sharing(photon)-ch4.md)

