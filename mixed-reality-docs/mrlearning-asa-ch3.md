---
title: Tutorials zu Azure Spatial Anchor-3. Anzeigen des Azure Spatial Anchor-Feedbacks
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 19529cbfebd74938395545c329097d42b5af9ff9
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334402"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3. Anzeigen des Azure Spatial Anchor-Feedbacks

In dieser Lektion erfahren Sie, wie Sie Benutzern Feedback zur Anker Ermittlung, zu Ereignissen und zum Status bei der Verwendung von räumlichen Azure-Ankern bereitstellen.

## <a name="objectives"></a>Ziele

* Erfahren Sie, wie Sie einen Benutzeroberflächen Bereich einrichten, in dem wichtige Informationen zur aktuellen ASA-Sitzung angezeigt werden.

* Verstehen und untersuchen Sie Feedback Elemente, die das ASA SDK Benutzern zur Verfügung stellt.

## <a name="set-up-asa-feedback-ui-panel"></a>Einrichten des ASA-Feedback-UI-Panels

1. In dieser Lektion verwenden wir nicht die Schaltflächen "saveanchoron Disk" und "shareanchor". Wählen Sie daher beide Schaltflächen aus, und deaktivieren Sie das Kontrollkästchen im Inspektor-Panel (wie unten dargestellt), um diese Schaltflächen auszublenden.

    ![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. Erstellen Sie den Anweisungs Bereich. Klicken Sie zunächst mit der rechten Maustaste auf die Schaltfläche "Instructions", zeigen Sie auf "3D-Objekt", und wählen Sie "textmeshpro-Text" aus.

    ![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. Passen Sie die Skalierung und Positionierung des Texts so an, dass er mit den Anweisungen in Ihrer Szene übereinstimmt. Stellen Sie außerdem sicher, dass die Ausrichtung für den gesamten Text zentriert ist. Löschen Sie dann den Beispiel Text aus dem Text-Editor, wie in der folgenden Abbildung dargestellt.

    ![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. Ändern Sie den Namen des textmeschpro-Objekts in "Feedbackpanel".

    ![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. Stellen Sie sicher, dass der Text "Feedbackpanel" in der ASA_feedback Hierarchie ausgewählt ist, klicken Sie auf "Komponente hinzufügen", und fügen Sie das Anchor-Feedback Skript hinzu, indem Sie es suchen und es auswählen

    ![module2chapter3step8im](images/module2chapter3step8im.PNG)

6. Ziehen Sie das Textobjekt "Feedbackpanel" aus der ASA_Feedback Hierarchie in den leeren Slot unterhalb des Skripts, wie in der folgenden Abbildung dargestellt.

    ![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In dieser Lektion haben wir gelernt, wie ein UI-Panel erstellt wird, um den aktuellen Status der Azure Spatial Anchor-Oberfläche anzuzeigen, um Benutzern Echtzeitfeedback zu bieten.
