---
title: MR Learning ASA-Modul Azure räumliche Anker für HoloLens 2
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 4aabb4a35efebdd893cbb248365e534abd60f684
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326399"
---
# <a name="displaying-azure-spatial-anchor-feedback"></a>Anzeigen von Azure räumliche Anchor-Feedback

In dieser Lektion erfahren Sie mehr über das Benutzer Feedback zur Ermittlung der Anker, Ereignisse und Status räumliche Anker Azure nutzen können.

Ziele:

* Erfahren Sie, wie ein Benutzeroberflächen-Panel einrichten, die wichtige Informationen über die aktuelle ASA-Sitzung anzeigt.

* Verstehen Sie und Kennenlernen Sie der Feedback-Elemente, die das ASA-SDK für Benutzer verfügbar macht.

  

## <a name="instructions"></a>Anweisungen

### <a name="set-up-asa-feedback-ui-panel"></a>Richten Sie ASA-Feedback-Benutzeroberflächen-Panel

1. In dieser Lektion verwenden wir nicht die "SaveAnchorToDisk" und "ShareAnchor" Schaltflächen so wählen Sie beide Schaltflächen, und deaktivieren Sie das Kontrollkästchen im Bereich Inspector (wie unten gezeigt) Wenn Sie diese Schaltflächen ausblenden.
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. Als Nächstes erstellen Sie im Anweisungsbereich ein. Starten Sie von der rechten Maustaste auf die Schaltfläche "Instructions", zeigen Sie auf "3D Object", und wählen "Textmeshpro-Text."

   

   ![module2chapter3step2im](images/module2chapter3step2im.PNG)

   3. Passen Sie die Skalierung und die Positionierung des Texts, damit es mit den Anweisungen in Ihrer Szene übereinstimmt. Stellen Sie außerdem sicher, dass die Ausrichtung für den gesamten Text zentriert ist. Klicken Sie dann löschen Sie den Beispieltext im Text-Editor, wie im in der folgenden Abbildung gezeigt.


![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. Ändern Sie den Namen des Objekts TextMeshPro "FeedbackPanel."
   
   ![module2chapter3step4im](images/module2chapter3step4im.PNG)
   
5. Wählen Sie im Projektfenster "Ressourcen", und klicken Sie mit der rechten Maustaste auf, und wählen Sie dann "im Explorer anzeigen".
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

Klicken Sie nun [hier](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) benötigt zum Herunterladen der Dateien in den nächsten Schritten.

6. Wenn Explorer geöffnet wird, wählen Sie den Ordner "Assets" und dann den Ordner "ASAmodulesAssets", und kopieren Sie das Anchor-Feedback-Skript und die Anker-Modul-Skriptdateien in den Ordner. 
   

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> Hinweis: Wenn Sie ein Popup mit der Frage, wenn Sie möchten, überschreiben die alten, oder behalten die alte stellen sicher, dass Sie überschreiben erhalten.

7. Kehren Sie zum Ordner "Assets". Klicken Sie dann ein Wechsel in den Ordner "AzureSpatialAnchorsPlugin", und klicken Sie dann den Ordner "Beispiele" und schließlich Ordner "Scripts", und kopieren Sie den Azure räumliche Anker-Demo-Wrapper, in diesen Ordner. 
   

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. Nun, dass die Dateien hochgeladen werden, stellen Sie sicher, dass der Text "Feedbackpanel", in der Hierarchie ASA_feedback ausgewählt ist, und klicken Sie auf "Komponente hinzufügen", und fügen Sie das Anchor-Feedback-Skript hinzu, indem er gesucht, und wählen sie dann, sobald es angezeigt wird. 
   
   

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. Ziehen Sie das Textobjekt "FeedbackPanel" aus der Hierarchie ASA_Feedback in das leere Einschubfach aus, unter das Skript wie in der folgenden Abbildung dargestellt. 
   

![module2chapter3step9im](images/module2chapter3step9im.PNG)

   

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In haben dieser Lektion wir Vorgehensweise: Erstellen einer Benutzeroberflächen-Panel, um den aktuellen Status der räumlichen Anker Azure-Umgebung für die Bereitstellung von Benutzer mit Feedback in Echtzeit anzuzeigen.


