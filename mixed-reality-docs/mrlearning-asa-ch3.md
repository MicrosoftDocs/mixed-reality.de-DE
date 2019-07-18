---
title: Mr Learning ASA-Modul Azure Spatial Anchor on hololens 2
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: c6e902710eebe205b9e944b1bf95a9ddd3bd9044
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293806"
---
# <a name="displaying-azure-spatial-anchor-feedback"></a>Anzeigen des Azure Spatial Anchor-Feedbacks

In dieser Lektion erfahren Sie, wie Sie Benutzern Feedback zur Anker Ermittlung, zu Ereignissen und zum Status bei der Verwendung von räumlichen Azure-Ankern bereitstellen.

Ziele

* Erfahren Sie, wie Sie einen Benutzeroberflächen Bereich einrichten, in dem wichtige Informationen zur aktuellen ASA-Sitzung angezeigt werden.

* Verstehen und untersuchen Sie Feedback Elemente, die das ASA SDK Benutzern zur Verfügung stellt.

## <a name="instructions"></a>Anweisungen

### <a name="set-up-asa-feedback-ui-panel"></a>Einrichten des ASA-Feedback-UI-Panels

1. In dieser Lektion verwenden wir nicht die Schaltflächen "saveanchoron Disk" und "shareanchor". Wählen Sie daher beide Schaltflächen aus, und deaktivieren Sie das Kontrollkästchen im Inspektor-Panel (wie unten dargestellt), um diese Schaltflächen auszublenden.
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. Erstellen Sie als nächstes den Anweisungs Bereich. Klicken Sie mit der rechten Maustaste auf die Schaltfläche "Instructions", zeigen Sie auf "3D-Objekt", und wählen Sie "textmeshpro-Text" aus.

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. Passen Sie die Skalierung und Positionierung des Texts so an, dass er mit den Anweisungen in Ihrer Szene übereinstimmt. Stellen Sie außerdem sicher, dass die Ausrichtung für den gesamten Text zentriert ist. Löschen Sie dann den Beispiel Text aus dem Text-Editor, wie in der folgenden Abbildung dargestellt.

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. Ändern Sie den Namen des textmeschpro-Objekts in "Feedbackpanel".
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. Wählen Sie im Projekt Panel "Assets" aus, klicken Sie mit der rechten Maustaste, und wählen Sie dann "in Explorer anzeigen" aus.
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

Klicken Sie [hier](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) , um die Dateien herunterzuladen, die in den nächsten Schritten benötigt werden.

6. Nachdem der Explorer geöffnet wurde, wählen Sie den Ordner "Assets" und dann den Ordner "asamodulesassets" aus, und kopieren Sie das Anchor-Feedback Skript sowie die Skriptdateien für das Anker Modul in den Ordner. 

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> Hinweis: Wenn Sie ein Popup abrufen, in dem Sie gefragt werden, ob Sie das alte überschreiben oder das alte behalten möchten, stellen Sie sicher, dass Sie überschreiben auswählen.

7. Kehren Sie jetzt zum Ordner "Assets" zurück. Wechseln Sie dann in den Ordner "azurespatialanchorsplugin", den Ordner "examples" und schließlich den Ordner "Scripts", und kopieren Sie den Demo-Wrapper für räumliche Azure-Anker in diesen Ordner. 

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. Nachdem die Dateien hochgeladen wurden, stellen Sie sicher, dass der Text "Feedbackpanel" in der ASA_feedback-Hierarchie ausgewählt ist, klicken Sie auf "Komponente hinzufügen", und fügen Sie das Anchor-Feedback Skript hinzu, indem Sie danach suchen und es auswählen. 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. Ziehen Sie das Textobjekt "Feedbackpanel" aus der ASA_Feedback-Hierarchie in den leeren Slot unterhalb des Skripts, wie in der folgenden Abbildung dargestellt. 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In dieser Lektion haben wir gelernt, wie ein UI-Panel erstellt wird, um den aktuellen Status der Azure Spatial Anchor-Oberfläche für den Benutzer mit Echtzeitfeedback anzuzeigen.


