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
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="b107f-105">3. Anzeigen des Azure Spatial Anchor-Feedbacks</span><span class="sxs-lookup"><span data-stu-id="b107f-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="b107f-106">In dieser Lektion erfahren Sie, wie Sie Benutzern Feedback zur Anker Ermittlung, zu Ereignissen und zum Status bei der Verwendung von räumlichen Azure-Ankern bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="b107f-106">In this lesson, you'll learn how to provide users with feedback about anchor discovery, events and status when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="b107f-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="b107f-107">Objectives</span></span>

* <span data-ttu-id="b107f-108">Erfahren Sie, wie Sie einen Benutzeroberflächen Bereich einrichten, in dem wichtige Informationen zur aktuellen ASA-Sitzung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b107f-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="b107f-109">Verstehen und untersuchen Sie Feedback Elemente, die das ASA SDK Benutzern zur Verfügung stellt.</span><span class="sxs-lookup"><span data-stu-id="b107f-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="b107f-110">Einrichten des ASA-Feedback-UI-Panels</span><span class="sxs-lookup"><span data-stu-id="b107f-110">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="b107f-111">In dieser Lektion verwenden wir nicht die Schaltflächen "saveanchoron Disk" und "shareanchor". Wählen Sie daher beide Schaltflächen aus, und deaktivieren Sie das Kontrollkästchen im Inspektor-Panel (wie unten dargestellt), um diese Schaltflächen auszublenden.</span><span class="sxs-lookup"><span data-stu-id="b107f-111">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons, so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>

    ![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="b107f-113">Erstellen Sie den Anweisungs Bereich.</span><span class="sxs-lookup"><span data-stu-id="b107f-113">Create the instruction panel.</span></span> <span data-ttu-id="b107f-114">Klicken Sie zunächst mit der rechten Maustaste auf die Schaltfläche "Instructions", zeigen Sie auf "3D-Objekt", und wählen Sie "textmeshpro-Text" aus.</span><span class="sxs-lookup"><span data-stu-id="b107f-114">Start by right-clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

    ![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. <span data-ttu-id="b107f-116">Passen Sie die Skalierung und Positionierung des Texts so an, dass er mit den Anweisungen in Ihrer Szene übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="b107f-116">Adjust the scale and positioning of the text, so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="b107f-117">Stellen Sie außerdem sicher, dass die Ausrichtung für den gesamten Text zentriert ist.</span><span class="sxs-lookup"><span data-stu-id="b107f-117">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="b107f-118">Löschen Sie dann den Beispiel Text aus dem Text-Editor, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="b107f-118">Then delete the sample text from the text editor, as shown in in the image below.</span></span>

    ![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="b107f-120">Ändern Sie den Namen des textmeschpro-Objekts in "Feedbackpanel".</span><span class="sxs-lookup"><span data-stu-id="b107f-120">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>

    ![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. <span data-ttu-id="b107f-122">Stellen Sie sicher, dass der Text "Feedbackpanel" in der ASA_feedback Hierarchie ausgewählt ist, klicken Sie auf "Komponente hinzufügen", und fügen Sie das Anchor-Feedback Skript hinzu, indem Sie es suchen und es auswählen</span><span class="sxs-lookup"><span data-stu-id="b107f-122">Ensure that the "feedbackpanel" text is selected in the ASA_feedback hierarchy, click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span>

    ![module2chapter3step8im](images/module2chapter3step8im.PNG)

6. <span data-ttu-id="b107f-124">Ziehen Sie das Textobjekt "Feedbackpanel" aus der ASA_Feedback Hierarchie in den leeren Slot unterhalb des Skripts, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="b107f-124">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span>

    ![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a><span data-ttu-id="b107f-126">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="b107f-126">Congratulations</span></span>

<span data-ttu-id="b107f-127">In dieser Lektion haben wir gelernt, wie ein UI-Panel erstellt wird, um den aktuellen Status der Azure Spatial Anchor-Oberfläche anzuzeigen, um Benutzern Echtzeitfeedback zu bieten.</span><span class="sxs-lookup"><span data-stu-id="b107f-127">In this lesson, we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>
