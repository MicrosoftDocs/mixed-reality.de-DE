---
title: Lernen die Freigabe-Modul für HoloLens 2 MR
description: Führen Sie diesen Kurs erfahren, wie Sie mehrere Benutzer freigegebene Umgebungen innerhalb einer HoloLens-2-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: d5bed61f5ffc1d3b4efed96f47c3568fbf3a2948
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416011"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a><span data-ttu-id="9ac64-104">Synchronisieren von Verschiebungen von freigegebenen Objekten</span><span class="sxs-lookup"><span data-stu-id="9ac64-104">Synchronizing the Movements of Shared Objects</span></span>

<span data-ttu-id="9ac64-105">In dieser Lektion erfahren wir, wie die Bewegungen der Objekte freigeben, damit alle Teilnehmer einer Sitzung gemeinsam genutzten Zusammenarbeit und den anderen Aktivitäten anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="9ac64-105">In this lesson, we will learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="9ac64-106">Diese Lektion baut auf das Startprogramm des Mondes, die als Teil des erstellt wurde die [Base Modul Tutorials](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="9ac64-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="9ac64-107">Ziele:</span><span class="sxs-lookup"><span data-stu-id="9ac64-107">Objectives:</span></span>

- <span data-ttu-id="9ac64-108">Führen Sie das Startprogramm auf als das 3D-Modell um gemeinsam genutzt werden</span><span class="sxs-lookup"><span data-stu-id="9ac64-108">Bring in the Lunar Launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="9ac64-109">Konfigurieren Sie das Projekt, um die Bewegungen des 3D-Modells freigeben.</span><span class="sxs-lookup"><span data-stu-id="9ac64-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="9ac64-110">Erfahren Sie, wie Sie eine einfache Zusammenarbeit Mehrbenutzer-Anwendung erstellen</span><span class="sxs-lookup"><span data-stu-id="9ac64-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="9ac64-111">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="9ac64-111">Instructions</span></span>

1. <span data-ttu-id="9ac64-112">Speichern Sie die Szene, aus der vorherigen Lektion (STRG + S).</span><span class="sxs-lookup"><span data-stu-id="9ac64-112">Save the scene from the previous lesson (control+S).</span></span> <span data-ttu-id="9ac64-113">Sie können "HLSharedProjectMainPart4.unity" Namen, damit es ist einfacher zu finden, wenn Sie ihn wieder benötigen.</span><span class="sxs-lookup"><span data-stu-id="9ac64-113">You may name it "HLSharedProjectMainPart4.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="9ac64-114">Im Projektfenster, in den Assets > Ordner "Scripts", doppelklicken Sie auf GenericNetSync, öffnen Sie sie in Visual Studio oder dem Editor jemals code Sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="9ac64-114">In the Project window, in the Assets > Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  ![](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="9ac64-115">In den Zeilen, 34 und 38, entfernen Sie die "/ /", den Code für die Tabelle zu aktivieren, die wir in dieser Lektion verwenden.</span><span class="sxs-lookup"><span data-stu-id="9ac64-115">On lines 34 and 38, remove the "//" to activate the code for the Table that we will use in this lesson.</span></span>  <span data-ttu-id="9ac64-116">Speichern Sie die Datei.</span><span class="sxs-lookup"><span data-stu-id="9ac64-116">Then Save the file.</span></span> ![](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="9ac64-117">Das Projektfenster, doppelklicken klicken Sie auf die PhotonRoom.cs-Datei in den Assets > Ordner "Scripts" erneut, es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="9ac64-117">In the project window, double click on the PhotonRoom.cs file in the Assets > Scripts folder to again open it in Visual Studio.</span></span> ![](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="9ac64-118">Genau wie in Schritt 3 wir entfernen müssen das "/ /", aktivieren den Code in den Zeilen, 106, 25 und 26.![](images/module3chapter4updatestep5a.png)</span><span class="sxs-lookup"><span data-stu-id="9ac64-118">Just like in step 3 we need to remove the "//" to activate the code at lines 25, 26, and 106.![](images/module3chapter4updatestep5a.png)</span></span> ![](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="9ac64-119">Wählen Sie in der Ansicht der Hierarchie das NetworkRoom-Objekt.![](images/module3chapter4updatestep6.png)</span><span class="sxs-lookup"><span data-stu-id="9ac64-119">In the Hierarchy view, select the NetworkRoom object.![](images/module3chapter4updatestep6.png)</span></span>

7. <span data-ttu-id="9ac64-120">Navigieren Sie in der Projektansicht zum Bestand > Ressourcen > prefabs (Vorlagen).</span><span class="sxs-lookup"><span data-stu-id="9ac64-120">In the project view, navigate to Assets > Resources > Prefabs.</span></span> <span data-ttu-id="9ac64-121">Zunächst Drag & drop den Tabelle-Prefab im Slot "Tableprefab" für die PhotonRoom-Klasse.</span><span class="sxs-lookup"><span data-stu-id="9ac64-121">First, drag and drop the Table prefab to the "Tableprefab" slot on the PhotonRoom class.</span></span> <span data-ttu-id="9ac64-122">Als Nächstes ziehen und Ablegen von der LunarModule Prefab zum "Modul Prefab" Steckplatz auf dem die PhotonRoom-Klasse.</span><span class="sxs-lookup"><span data-stu-id="9ac64-122">Next drag and drop the LunarModule prefab to the "Module Prefab" slot on the PhotonRoom class.</span></span> ![](images/module3chapter4updatestep7.png)

   <span data-ttu-id="9ac64-123">Hinweis: Wenn Sie auf einem prefab Objekte und-Version klicken, wechselt der Inspektor auf dieses Objekt.</span><span class="sxs-lookup"><span data-stu-id="9ac64-123">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="9ac64-124">Klicken Sie auf, drag, drop, und jedes Objekt in seine entsprechende Slot freizugeben.</span><span class="sxs-lookup"><span data-stu-id="9ac64-124">Click, drag, drop and release each object to its appropriate slot.</span></span>



8. <span data-ttu-id="9ac64-125">Jetzt klicken Sie auf den Pfeil links neben "MixedRealityPlayspace", und verschieben Sie das untergeordnete-spielobjekt "MainCamera" in das Prefab "SharedPlayground" nach unten zu.</span><span class="sxs-lookup"><span data-stu-id="9ac64-125">Now, click the arrow to the left of "MixedRealityPlayspace" and move the child game object, "MainCamera" down into the "SharedPlayground" prefab.</span></span> <span data-ttu-id="9ac64-126">Löschen Sie dann das prefab "MixedRealityPlayspace" (zum Löschen, wählen Sie das Prefab aus, und tippen Sie auf der Tastatur auf "löschen").</span><span class="sxs-lookup"><span data-stu-id="9ac64-126">Then, delete the prefab "MixedRealityPlayspace" (to delete, select the prefab and tap "delete" on your keyboard).</span></span>

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

<span data-ttu-id="9ac64-128">Hinweis:  Stellen Sie sicher, dass sowohl die SharedPlayground die Main Camera Positionen auf 0,0,0 festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="9ac64-128">note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="9ac64-129">Erstellen Sie ein neues Spiels-Objekt als ein untergeordnetes Objekt festgelegt, um das übergeordnete Objekt "SharedPlayground" (um ein neues Objekt erstellen, klicken Sie mit der rechten Maustaste auf das übergeordnete Objekt, und wählen Sie "leere erstellen").</span><span class="sxs-lookup"><span data-stu-id="9ac64-129">Create a new game object set as a child object to the "SharedPlayground" parent object (to create a new object, right click on the parent object, and select "create  empty").</span></span> 

10. <span data-ttu-id="9ac64-130">Mit dem neuen Objekt in der Hierarchie ausgewählt haben ändern Sie den Namen des Objekts in "TableAnchor", in den Bereich der Eigenschaftenanalyse.</span><span class="sxs-lookup"><span data-stu-id="9ac64-130">With the new object selected in your hierarchy, change the name of the object to "TableAnchor" in the inspector panel.</span></span> <span data-ttu-id="9ac64-131">Darüber hinaus klicken Sie auf "Komponente hinzufügen" aus, und suchen Sie nach der Komponente "TableAnchor".</span><span class="sxs-lookup"><span data-stu-id="9ac64-131">Also, click "add component" and search for the "TableAnchor" component.</span></span> <span data-ttu-id="9ac64-132">Wählen sie aus, und fügen Sie es auf das Objekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="9ac64-132">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="9ac64-134">Hinweis: Legen Sie die Positionierung auf X = 1, y =-0,55 und Z = 2.</span><span class="sxs-lookup"><span data-stu-id="9ac64-134">note: set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="9ac64-135">Legen Sie außerdem die Drehung y = 90.</span><span class="sxs-lookup"><span data-stu-id="9ac64-135">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. <span data-ttu-id="9ac64-137">Im Bedienfeld "Projekt" im Ordner "Prefabs" ziehen Sie jetzt das Prefab "Table" in das "TableAnchor" untergeordnete Objekt an, die, das Sie gerade erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="9ac64-137">Now in the project panel, in the "prefabs" folder, drag the "table" prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. <span data-ttu-id="9ac64-139">Ändern Sie im Objekt "DebugWindow" schließlich die Breite auf 80 und die Höhe in 10.</span><span class="sxs-lookup"><span data-stu-id="9ac64-139">Finally, in the "DebugWindow" object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="9ac64-141">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="9ac64-141">Congratulations</span></span>

<span data-ttu-id="9ac64-142">Sobald dies abgeschlossen ist, können alle Benutzer, die Ihr Unity-Projekt verknüpfen das Startprogramm des Mondes bewegen.</span><span class="sxs-lookup"><span data-stu-id="9ac64-142">Once this is complete, all users that join your Unity project can move the Lunar Launcher around.</span></span> <span data-ttu-id="9ac64-143">Alle Bewegungen werden synchronisiert, sodass jeder Benutzer voneinander Interaktionen sehen kann.</span><span class="sxs-lookup"><span data-stu-id="9ac64-143">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="9ac64-144">Diese Konzepte dienen als die grundlegenden Bausteine für die Funktionen für die gemeinsame Zusammenarbeit mit vollem Funktionsumfang.</span><span class="sxs-lookup"><span data-stu-id="9ac64-144">These concepts serve as the foundational building blocks for full-featured shared collaboration experiences.</span></span> 

<span data-ttu-id="9ac64-145">Obwohl alle Benutzer, die als Teil einer gemeinsamen Erfahrung verbunden sind und die relative Verschiebungen von Objekten angezeigt, ist die Anwendung immer noch nicht genau Avatare und Objekte so ausrichten, dass lokale Benutzer und der jeweils anderen Objekte am selben Ort innerhalb der physischen finden Sie unter World.</span><span class="sxs-lookup"><span data-stu-id="9ac64-145">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="9ac64-146">Um einen lokalen freigegebenen Umgebungen zu verankern, erfordert jedes Gerät ein allgemeines Verständnis der physischen Umgebung.</span><span class="sxs-lookup"><span data-stu-id="9ac64-146">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="9ac64-147">In diesem Modul wir wird verwenden zu diesem Zweck [Azure räumliche Anker](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), wird die in der nächsten Lektion implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="9ac64-147">In this module, we will achieve this using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), which will be implemented in the next lesson.</span></span>

<span data-ttu-id="9ac64-148">Bevor Sie mit der nächsten Lektion fortfahren müssen wir das ASA-Learning-Modul durchführen, die erforderlichen Azure-Konto und das Erstellen von Ressourcen und andere grundlegende Gebäude Blöcke ASA "grundlegende Einstellungen" beschrieben wird, bevor wir dies in unserem gemeinsamen Erfahrung integrieren können.</span><span class="sxs-lookup"><span data-stu-id="9ac64-148">Before proceeding to the next lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="9ac64-149">[Nächste Lektion: Sharing(Photon) Lektion 5](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="9ac64-149">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

