---
title: Lernen die Freigabe-Modul für HoloLens 2 MR
description: Führen Sie diesen Kurs erfahren, wie Sie mehrere Benutzer freigegebene Umgebungen innerhalb einer HoloLens-2-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: a67eaef45582054b62198a563f0ee01724fd60db
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326540"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a><span data-ttu-id="0a8be-104">Synchronisieren von Verschiebungen von freigegebenen Objekten</span><span class="sxs-lookup"><span data-stu-id="0a8be-104">Synchronizing the Movements of Shared Objects</span></span>

<span data-ttu-id="0a8be-105">In dieser Lektion erfahren wir, wie die Bewegungen der Objekte freigeben, damit alle Teilnehmer einer Sitzung gemeinsam genutzten Zusammenarbeit und den anderen Aktivitäten anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="0a8be-105">In this lesson, we will learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="0a8be-106">Diese Lektion baut auf das Startprogramm des Mondes, die als Teil des erstellt wurde die [Base Modul Tutorials](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="0a8be-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="0a8be-107">Ziele:</span><span class="sxs-lookup"><span data-stu-id="0a8be-107">Objectives:</span></span>

- <span data-ttu-id="0a8be-108">Importieren Sie das Startprogramm für abgeschlossene auf als das 3D-Modell freigegeben werden</span><span class="sxs-lookup"><span data-stu-id="0a8be-108">Import the completed Lunar Launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="0a8be-109">Konfigurieren Sie das Projekt, um die Bewegungen des 3D-Modells freigeben.</span><span class="sxs-lookup"><span data-stu-id="0a8be-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="0a8be-110">Erfahren Sie, wie Sie eine einfache Zusammenarbeit Mehrbenutzer-Anwendung erstellen</span><span class="sxs-lookup"><span data-stu-id="0a8be-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="0a8be-111">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="0a8be-111">Instructions</span></span>

1. <span data-ttu-id="0a8be-112">Speichern Sie die Szene, aus der vorherigen Lektion (STRG + S).</span><span class="sxs-lookup"><span data-stu-id="0a8be-112">Save the scene from the previous lesson (control+S).</span></span> <span data-ttu-id="0a8be-113">Sie können "HLSharedProjectMainPart4.unity" Namen, damit es ist einfacher zu finden, wenn Sie ihn wieder benötigen.</span><span class="sxs-lookup"><span data-stu-id="0a8be-113">You may name it "HLSharedProjectMainPart4.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="0a8be-114">Löschen Sie das Objekt "NetworkLobby" (indem Sie ihn auswählen und löschen).</span><span class="sxs-lookup"><span data-stu-id="0a8be-114">Delete the "NetworkLobby" object (by selecting it and pressing delete).</span></span> <span data-ttu-id="0a8be-115">Darüber hinaus ein Wechsel in den Ordner "Prefabs" aus Lektion 2 aus, und löschen Sie das Prefab "NetworkLobby" auch von dort.</span><span class="sxs-lookup"><span data-stu-id="0a8be-115">Also, go into the "prefabs" folder from lesson 2 and delete the "NetworkLobby" prefab from there as well.</span></span>

![Module3Chapter4tep2im](images/module3chapter4step2im.PNG)

3. <span data-ttu-id="0a8be-117">Importieren Sie ein neues benutzerdefiniertes Paket (z. B. in Schritt 2 aus der Lektion 2), und importieren Sie die [LunarModule.unitypackage](linkforModule1 lesson with the lunar module) und [NetworkLobbyReplacement.unitypackage.](linkforNetworklobbyreplacement package here)</span><span class="sxs-lookup"><span data-stu-id="0a8be-117">Import a new custom package (like step 2 from the lesson 2) and import the [LunarModule.unitypackage](linkforModule1 lesson with the lunar module) and the [NetworkLobbyReplacement.unitypackage.](linkforNetworklobbyreplacement package here)</span></span>

![Module3Chapter4step3im](images/module3chapter4step3im.PNG)

4. <span data-ttu-id="0a8be-119">Ziehen Sie nun im Ordner "Prefabs" die neue "NetworkLobby" Prefab in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="0a8be-119">Now, in the "prefabs" folder, drag the new "NetworkLobby" prefab into the hierarchy .</span></span> 

![Module3hapter4step4im](images/module3chapter4step4im.PNG)

> <span data-ttu-id="0a8be-121">Hinweis: die beiden Pakete, die wir in den vorherigen Schritten importiert aktualisiert das Prefab "NetworkLobby".</span><span class="sxs-lookup"><span data-stu-id="0a8be-121">note: the two packages we imported in the previous steps updated the "NetworkLobby" prefab.</span></span> <span data-ttu-id="0a8be-122">Es erspart Ihnen viele eingeben.</span><span class="sxs-lookup"><span data-stu-id="0a8be-122">It saves you from a lot of typing!</span></span>

5. <span data-ttu-id="0a8be-123">Jetzt klicken Sie auf den Pfeil links neben "MixedRealityPlayspace", und verschieben Sie das untergeordnete-spielobjekt "MainCamera" in das Prefab "SharedPlayground" nach unten zu.</span><span class="sxs-lookup"><span data-stu-id="0a8be-123">Now, click the arrow to the left of "MixedRealityPlayspace" and move the child game object, "MainCamera" down into the "SharedPlayground" prefab.</span></span> <span data-ttu-id="0a8be-124">Löschen Sie dann das prefab "MixedRealityPlayspace" (zum Löschen, wählen Sie das Prefab aus, und tippen Sie auf der Tastatur auf "löschen").</span><span class="sxs-lookup"><span data-stu-id="0a8be-124">Then, delete the prefab "MixedRealityPlayspace" (to delete, select the prefab and tap "delete" on your keyboard).</span></span>

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

6. <span data-ttu-id="0a8be-126">Erstellen Sie ein neues Spiels-Objekt als ein untergeordnetes Objekt festgelegt, um das übergeordnete Objekt "SharedPlayground" (um ein neues Objekt erstellen, klicken Sie mit der rechten Maustaste auf das übergeordnete Objekt, und wählen Sie "leere erstellen").</span><span class="sxs-lookup"><span data-stu-id="0a8be-126">Create a new game object set as a child object to the "SharedPlayground" parent object (to create a new object, right click on the parent object, and select "create  empty").</span></span>
7. <span data-ttu-id="0a8be-127">Mit dem neuen Objekt in der Hierarchie ausgewählt haben ändern Sie den Namen des Objekts in "TableAnchor", in den Bereich der Eigenschaftenanalyse.</span><span class="sxs-lookup"><span data-stu-id="0a8be-127">With the new object selected in your hierarchy, change the name of the object to "TableAnchor" in the inspector panel.</span></span> <span data-ttu-id="0a8be-128">Darüber hinaus klicken Sie auf "Komponente hinzufügen" aus, und suchen Sie nach der Komponente "TableAnchor".</span><span class="sxs-lookup"><span data-stu-id="0a8be-128">Also, click "add component" and search for the "TableAnchor" component.</span></span> <span data-ttu-id="0a8be-129">Wählen sie aus, und fügen Sie es auf das Objekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="0a8be-129">Select it and add it to the object.</span></span>

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="0a8be-131">Hinweis: Legen Sie die Positionierung auf X = 1, y =-0,55 und Z = 2.</span><span class="sxs-lookup"><span data-stu-id="0a8be-131">note: set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="0a8be-132">Legen Sie außerdem die Drehung y = 90.</span><span class="sxs-lookup"><span data-stu-id="0a8be-132">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

8. <span data-ttu-id="0a8be-134">Im Bedienfeld "Projekt" im Ordner "Prefabs" ziehen Sie jetzt das Prefab "Table" in das "TableAnchor" untergeordnete Objekt an, die, das Sie gerade erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="0a8be-134">Now in the project panel, in the "prefabs" folder, drag the "table" prefab into the "TableAnchor" child object you just created.</span></span>

   ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

9. <span data-ttu-id="0a8be-136">Wählen Sie "NetworkRoom", ein untergeordnetes Objekt unter "NetworkLobby" in der Hierarchie, und klicken Sie auf "Komponente hinzufügen" im Inspektor-Bereich und suchen Sie nach "PhotonView" und fügen Sie das Skript, das "*NetworkRoom*" Objekt.</span><span class="sxs-lookup"><span data-stu-id="0a8be-136">Select "NetworkRoom," a child object under "NetworkLobby" in the hierachy, and click "add component" in the inspector panel and search for "PhotonView" and add the script to the "*NetworkRoom*" object.</span></span>

![Module3Chapter4step9im](images/module3chapter4step9im.PNG)

11. <span data-ttu-id="0a8be-138">Ändern Sie im Objekt "DebugWindow" schließlich die Breite auf 80 und die Höhe in 10.</span><span class="sxs-lookup"><span data-stu-id="0a8be-138">Finally, in the "DebugWindow" object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="0a8be-140">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="0a8be-140">Congratulations</span></span>

<span data-ttu-id="0a8be-141">Sobald dies abgeschlossen ist, können alle Benutzer, die Ihr Unity-Projekt verknüpfen das Startprogramm des Mondes bewegen.</span><span class="sxs-lookup"><span data-stu-id="0a8be-141">Once this is complete, all users that join your Unity project can move the Lunar Launcher around.</span></span> <span data-ttu-id="0a8be-142">Alle Bewegungen werden synchronisiert, sodass jeder Benutzer voneinander Interaktionen sehen kann.</span><span class="sxs-lookup"><span data-stu-id="0a8be-142">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="0a8be-143">Diese Konzepte dienen als die grundlegenden Bausteine für die Funktionen für die gemeinsame Zusammenarbeit mit vollem Funktionsumfang.</span><span class="sxs-lookup"><span data-stu-id="0a8be-143">These concepts serve as the foundational building blocks for full-featured shared collaboration experiences.</span></span> 

<span data-ttu-id="0a8be-144">Obwohl alle Benutzer, die als Teil einer gemeinsamen Erfahrung verbunden sind und die relative Verschiebungen von Objekten angezeigt, ist die Anwendung immer noch nicht genau Avatare und Objekte so ausrichten, dass lokale Benutzer und der jeweils anderen Objekte am selben Ort innerhalb der physischen finden Sie unter World.</span><span class="sxs-lookup"><span data-stu-id="0a8be-144">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="0a8be-145">Um einen lokalen freigegebenen Umgebungen zu verankern, erfordert jedes Gerät ein allgemeines Verständnis der physischen Umgebung.</span><span class="sxs-lookup"><span data-stu-id="0a8be-145">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="0a8be-146">In diesem Modul wir wird verwenden zu diesem Zweck [Azure räumliche Anker](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), wird die in der nächsten Lektion implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="0a8be-146">In this module, we will achieve this using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), which will be implemented in the next lesson.</span></span>

<span data-ttu-id="0a8be-147">Bevor Sie mit der nächsten Lektion fortfahren müssen wir das ASA-Learning-Modul durchführen, die erforderlichen Azure-Konto und das Erstellen von Ressourcen und andere grundlegende Gebäude Blöcke ASA "grundlegende Einstellungen" beschrieben wird, bevor wir dies in unserem gemeinsamen Erfahrung integrieren können.</span><span class="sxs-lookup"><span data-stu-id="0a8be-147">Before proceeding to the next lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="0a8be-148">[Nächste Lektion: Sharing(Photon) Lektion 5](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="0a8be-148">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

