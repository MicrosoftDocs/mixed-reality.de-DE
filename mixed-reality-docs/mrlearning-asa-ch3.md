---
title: Tutorials zu Azure Spatial Anchor-3. Anzeigen des Azure Spatial Anchor-Feedbacks
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 77d639a88d8b4c71dc5fbe1c78565c4c3f91d36c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438412"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="58ee7-105">3. Anzeigen des Azure Spatial Anchor-Feedbacks</span><span class="sxs-lookup"><span data-stu-id="58ee7-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="58ee7-106">In dieser Lektion erfahren Sie, wie Sie Benutzern Feedback zur Anker Ermittlung, zu Ereignissen und zum Status bei der Verwendung von räumlichen Azure-Ankern bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="58ee7-106">In this lesson, you'll learn how to provide users with feedback about anchor discovery, events and status when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="58ee7-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="58ee7-107">Objectives</span></span>

* <span data-ttu-id="58ee7-108">Erfahren Sie, wie Sie einen Benutzeroberflächen Bereich einrichten, in dem wichtige Informationen zur aktuellen ASA-Sitzung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="58ee7-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="58ee7-109">Verstehen und untersuchen Sie Feedback Elemente, die das ASA SDK Benutzern zur Verfügung stellt.</span><span class="sxs-lookup"><span data-stu-id="58ee7-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="instructions"></a><span data-ttu-id="58ee7-110">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="58ee7-110">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="58ee7-111">Einrichten des ASA-Feedback-UI-Panels</span><span class="sxs-lookup"><span data-stu-id="58ee7-111">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="58ee7-112">In dieser Lektion verwenden wir nicht die Schaltflächen "saveanchoron Disk" und "shareanchor". Wählen Sie daher beide Schaltflächen aus, und deaktivieren Sie das Kontrollkästchen im Inspektor-Panel (wie unten dargestellt), um diese Schaltflächen auszublenden.</span><span class="sxs-lookup"><span data-stu-id="58ee7-112">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons, so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="58ee7-114">Erstellen Sie den Anweisungs Bereich.</span><span class="sxs-lookup"><span data-stu-id="58ee7-114">Create the instruction panel.</span></span> <span data-ttu-id="58ee7-115">Klicken Sie zunächst mit der rechten Maustaste auf die Schaltfläche "Instructions", zeigen Sie auf "3D-Objekt", und wählen Sie "textmeshpro-Text" aus.</span><span class="sxs-lookup"><span data-stu-id="58ee7-115">Start by right-clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. <span data-ttu-id="58ee7-117">Passen Sie die Skalierung und Positionierung des Texts so an, dass er mit den Anweisungen in Ihrer Szene übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="58ee7-117">Adjust the scale and positioning of the text, so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="58ee7-118">Stellen Sie außerdem sicher, dass die Ausrichtung für den gesamten Text zentriert ist.</span><span class="sxs-lookup"><span data-stu-id="58ee7-118">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="58ee7-119">Löschen Sie dann den Beispiel Text aus dem Text-Editor, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="58ee7-119">Then delete the sample text from the text editor, as shown in in the image below.</span></span>

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="58ee7-121">Ändern Sie den Namen des textmeschpro-Objekts in "Feedbackpanel".</span><span class="sxs-lookup"><span data-stu-id="58ee7-121">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. <span data-ttu-id="58ee7-123">Wählen Sie im Projekt Panel "Assets" aus, klicken Sie mit der rechten Maustaste, und wählen Sie dann "in Explorer anzeigen" aus.</span><span class="sxs-lookup"><span data-stu-id="58ee7-123">In the project panel, select "assets" and right click, then select "show in explorer."</span></span>
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

<span data-ttu-id="58ee7-125">Klicken Sie [hier](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) , um die Dateien herunterzuladen, die in den nächsten Schritten benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="58ee7-125">Click [here](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) to download the files needed in the next few steps.</span></span>

6. <span data-ttu-id="58ee7-126">Nachdem der Explorer geöffnet wurde, wählen Sie den Ordner "Assets" und dann den Ordner "asamodulesassets" aus, und kopieren Sie das Anchor-Feedback Skript sowie die Skriptdateien für das Anker Modul in den Ordner.</span><span class="sxs-lookup"><span data-stu-id="58ee7-126">Once Explorer opens, select the Assets folder, then the "ASAmodulesAssets" folder and copy the anchor feedback script and the anchor module script files into the folder.</span></span> 

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> <span data-ttu-id="58ee7-128">Hinweis: Wenn Sie eine Popup Meldung erhalten, in der Sie gefragt werden, ob Sie das alte überschreiben oder das alte behalten möchten, wählen Sie überschreiben aus.</span><span class="sxs-lookup"><span data-stu-id="58ee7-128">note: if you get a pop-up message asking if you to overwrite the old or keep the old, select overwrite.</span></span>

7. <span data-ttu-id="58ee7-129">Kehren Sie zum Ordner Assets zurück.</span><span class="sxs-lookup"><span data-stu-id="58ee7-129">Return to the Assets folder.</span></span> <span data-ttu-id="58ee7-130">Wechseln Sie dann in den Ordner "azurespatialanchorsplugin", gefolgt vom Ordner "examples" und schließlich dem Ordner "Scripts".</span><span class="sxs-lookup"><span data-stu-id="58ee7-130">Then, go into the "AzureSpatialAnchorsPlugin" folder, followed by the Examples folder and finally the Scripts folder.</span></span> <span data-ttu-id="58ee7-131">Kopieren Sie dann den Demo-Wrapper für räumliche Azure-Anker in diesen Ordner.</span><span class="sxs-lookup"><span data-stu-id="58ee7-131">Then copy the Azure Spatial Anchors demo wrapper into that folder.</span></span> 

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. <span data-ttu-id="58ee7-133">Nachdem die Dateien hochgeladen wurden, stellen Sie sicher, dass der Text "Feedbackpanel" in der ASA_feedback-Hierarchie ausgewählt ist, klicken Sie auf "Komponente hinzufügen", und fügen Sie das Anchor-Feedback Skript hinzu, indem Sie danach suchen und es auswählen.</span><span class="sxs-lookup"><span data-stu-id="58ee7-133">Now that the files are uploaded, ensure that the "feedbackpanel" text is selected in the ASA_feedback hierarchy, click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. <span data-ttu-id="58ee7-135">Ziehen Sie das Textobjekt "Feedbackpanel" aus der ASA_Feedback-Hierarchie in den leeren Slot unterhalb des Skripts, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="58ee7-135">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a><span data-ttu-id="58ee7-137">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="58ee7-137">Congratulations</span></span>

<span data-ttu-id="58ee7-138">In dieser Lektion haben wir gelernt, wie ein UI-Panel erstellt wird, um den aktuellen Status der Azure Spatial Anchor-Oberfläche anzuzeigen, um Benutzern Echtzeitfeedback zu bieten.</span><span class="sxs-lookup"><span data-stu-id="58ee7-138">In this lesson, we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>


