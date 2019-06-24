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
# <a name="displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="a804f-104">Anzeigen von Azure räumliche Anchor-Feedback</span><span class="sxs-lookup"><span data-stu-id="a804f-104">Displaying Azure Spatial Anchor Feedback</span></span>

<span data-ttu-id="a804f-105">In dieser Lektion erfahren Sie mehr über das Benutzer Feedback zur Ermittlung der Anker, Ereignisse und Status räumliche Anker Azure nutzen können.</span><span class="sxs-lookup"><span data-stu-id="a804f-105">In this lesson, you'll learn about how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors.</span></span>

<span data-ttu-id="a804f-106">Ziele:</span><span class="sxs-lookup"><span data-stu-id="a804f-106">Objectives:</span></span>

* <span data-ttu-id="a804f-107">Erfahren Sie, wie ein Benutzeroberflächen-Panel einrichten, die wichtige Informationen über die aktuelle ASA-Sitzung anzeigt.</span><span class="sxs-lookup"><span data-stu-id="a804f-107">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="a804f-108">Verstehen Sie und Kennenlernen Sie der Feedback-Elemente, die das ASA-SDK für Benutzer verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="a804f-108">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

  

## <a name="instructions"></a><span data-ttu-id="a804f-109">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="a804f-109">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="a804f-110">Richten Sie ASA-Feedback-Benutzeroberflächen-Panel</span><span class="sxs-lookup"><span data-stu-id="a804f-110">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="a804f-111">In dieser Lektion verwenden wir nicht die "SaveAnchorToDisk" und "ShareAnchor" Schaltflächen so wählen Sie beide Schaltflächen, und deaktivieren Sie das Kontrollkästchen im Bereich Inspector (wie unten gezeigt) Wenn Sie diese Schaltflächen ausblenden.</span><span class="sxs-lookup"><span data-stu-id="a804f-111">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="a804f-113">Als Nächstes erstellen Sie im Anweisungsbereich ein.</span><span class="sxs-lookup"><span data-stu-id="a804f-113">Next, create the instruction panel.</span></span> <span data-ttu-id="a804f-114">Starten Sie von der rechten Maustaste auf die Schaltfläche "Instructions", zeigen Sie auf "3D Object", und wählen "Textmeshpro-Text."</span><span class="sxs-lookup"><span data-stu-id="a804f-114">Start by right clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

   

   ![module2chapter3step2im](images/module2chapter3step2im.PNG)

   3. <span data-ttu-id="a804f-116">Passen Sie die Skalierung und die Positionierung des Texts, damit es mit den Anweisungen in Ihrer Szene übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="a804f-116">Adjust the scale and the positioning of the text so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="a804f-117">Stellen Sie außerdem sicher, dass die Ausrichtung für den gesamten Text zentriert ist.</span><span class="sxs-lookup"><span data-stu-id="a804f-117">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="a804f-118">Klicken Sie dann löschen Sie den Beispieltext im Text-Editor, wie im in der folgenden Abbildung gezeigt.</span><span class="sxs-lookup"><span data-stu-id="a804f-118">Then delete the sample text from the text editor, as shown in in the image below.</span></span>


![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="a804f-120">Ändern Sie den Namen des Objekts TextMeshPro "FeedbackPanel."</span><span class="sxs-lookup"><span data-stu-id="a804f-120">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   
   ![module2chapter3step4im](images/module2chapter3step4im.PNG)
   
5. <span data-ttu-id="a804f-122">Wählen Sie im Projektfenster "Ressourcen", und klicken Sie mit der rechten Maustaste auf, und wählen Sie dann "im Explorer anzeigen".</span><span class="sxs-lookup"><span data-stu-id="a804f-122">In the project panel, select "assets" and right click, then select "show in explorer."</span></span>
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

<span data-ttu-id="a804f-124">Klicken Sie nun [hier](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) benötigt zum Herunterladen der Dateien in den nächsten Schritten.</span><span class="sxs-lookup"><span data-stu-id="a804f-124">Now, click [here](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) to download the files needed in the next few steps.</span></span>

6. <span data-ttu-id="a804f-125">Wenn Explorer geöffnet wird, wählen Sie den Ordner "Assets" und dann den Ordner "ASAmodulesAssets", und kopieren Sie das Anchor-Feedback-Skript und die Anker-Modul-Skriptdateien in den Ordner.</span><span class="sxs-lookup"><span data-stu-id="a804f-125">Once explorer opens, select the assets folder, then the "ASAmodulesAssets" folder, and copy the anchor feedback script and the anchor module script files into the folder.</span></span> 
   

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> <span data-ttu-id="a804f-127">Hinweis: Wenn Sie ein Popup mit der Frage, wenn Sie möchten, überschreiben die alten, oder behalten die alte stellen sicher, dass Sie überschreiben erhalten.</span><span class="sxs-lookup"><span data-stu-id="a804f-127">note: if you get a pop-up asking you if you would like to overwrite the old or keep the old make sure you select overwrite.</span></span>

7. <span data-ttu-id="a804f-128">Kehren Sie zum Ordner "Assets".</span><span class="sxs-lookup"><span data-stu-id="a804f-128">Now return to the Assets folder.</span></span> <span data-ttu-id="a804f-129">Klicken Sie dann ein Wechsel in den Ordner "AzureSpatialAnchorsPlugin", und klicken Sie dann den Ordner "Beispiele" und schließlich Ordner "Scripts", und kopieren Sie den Azure räumliche Anker-Demo-Wrapper, in diesen Ordner.</span><span class="sxs-lookup"><span data-stu-id="a804f-129">Then, go into the "AzureSpatialAnchorsPlugin" folder, then the examples folder, and finally the scripts folder, and copy the Azure Spatial Anchors demo wrapper into that folder.</span></span> 
   

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. <span data-ttu-id="a804f-131">Nun, dass die Dateien hochgeladen werden, stellen Sie sicher, dass der Text "Feedbackpanel", in der Hierarchie ASA_feedback ausgewählt ist, und klicken Sie auf "Komponente hinzufügen", und fügen Sie das Anchor-Feedback-Skript hinzu, indem er gesucht, und wählen sie dann, sobald es angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a804f-131">Now that the files are uploaded, ensure that the "feedbackpanel" text is selected, in the ASA_feedback hierarchy and click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 
   
   

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. <span data-ttu-id="a804f-133">Ziehen Sie das Textobjekt "FeedbackPanel" aus der Hierarchie ASA_Feedback in das leere Einschubfach aus, unter das Skript wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="a804f-133">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 
   

![module2chapter3step9im](images/module2chapter3step9im.PNG)

   

## <a name="congratulations"></a><span data-ttu-id="a804f-135">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="a804f-135">Congratulations</span></span>

<span data-ttu-id="a804f-136">In haben dieser Lektion wir Vorgehensweise: Erstellen einer Benutzeroberflächen-Panel, um den aktuellen Status der räumlichen Anker Azure-Umgebung für die Bereitstellung von Benutzer mit Feedback in Echtzeit anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a804f-136">In this lesson we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing user with real-time feedback.</span></span>


