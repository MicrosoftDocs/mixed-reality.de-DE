---
title: Mr Learning Sharing Module für hololens 2
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Umgebungen mit mehreren Benutzern in einer hololens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 529a888dfa00180ca908fbc7f4c62f9a9086c661
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460320"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="15927-104">4. Freigeben von Objektbewegungen mit mehreren Benutzern</span><span class="sxs-lookup"><span data-stu-id="15927-104">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="15927-105">In diesem Tutorial erfahren Sie, wie Sie die Bewegungen von Objekten freigeben, damit alle Teilnehmer einer freigegebenen Sitzung zusammenarbeiten und die Interaktionen der einzelnen Benutzer anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="15927-105">In this Tutorial, we learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="15927-106">Diese Lektion baut auf dem Mond Start Programm auf, das als Teil der Lernprogramme für das [Basismodul](mrlearning-base.md)erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="15927-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="15927-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="15927-107">Objectives:</span></span>

- <span data-ttu-id="15927-108">Bringen Sie das Mond Startfeld als 3D-Modell ein, das freigegeben werden soll.</span><span class="sxs-lookup"><span data-stu-id="15927-108">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="15927-109">Konfigurieren Sie das Projekt so, dass die Bewegungen des 3D-Modells gemeinsam genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="15927-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="15927-110">Erfahren Sie, wie Sie eine grundlegende Anwendung für mehrere Benutzer Anwendungen erstellen.</span><span class="sxs-lookup"><span data-stu-id="15927-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="15927-111">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="15927-111">Instructions</span></span>


1. <span data-ttu-id="15927-112">Speichern Sie die Szene aus der vorherigen Lektion (Control + S).</span><span class="sxs-lookup"><span data-stu-id="15927-112">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="15927-113">Sie können den Namen HLSharedProjectMainPart4. unity benennen, damit er bei Bedarf leichter zu finden ist.</span><span class="sxs-lookup"><span data-stu-id="15927-113">You can name it, HLSharedProjectMainPart4.unity, so that it's easier to find when you need it.</span></span>

2. <span data-ttu-id="15927-114">Doppelklicken Sie im Projektfenster im Ordner Assets-> Scripts auf genericnetsync, um ihn in Visual Studio oder in dem von Ihnen verwendeten Code-Editor zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="15927-114">From the Project window, in the Assets->Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="15927-116">Entfernen Sie in den Zeilen 34 und 38 das//, um den Code für die Tabelle zu aktivieren, die in dieser Lektion verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="15927-116">On Lines 34 and 38, remove the // to activate the code for the table that we will use in this lesson.</span></span> <span data-ttu-id="15927-117">Speichern Sie dann die Datei.</span><span class="sxs-lookup"><span data-stu-id="15927-117">next, Save the file.</span></span> 

![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="15927-119">Doppelklicken Sie im Projektfenster im Ordner Assets-> Scripts auf die Datei PhotonRoom.cs, um Sie in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="15927-119">In the Project window, double click on the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span> 

![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="15927-121">Ebenso wie in Schritt 3 müssen wir das//Entfernen, um den Code in den Zeilen 25, 26 und 106 zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="15927-121">Just like in Step 3, we need to remove the // to activate the code at Lines 25, 26, and 106.</span></span>

![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png) 

![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="15927-124">Wählen Sie in der Hierarchie Ansicht das networkroom-Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="15927-124">In the Hierarchy view, select the NetworkRoom object.</span></span>

![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="15927-126">Navigieren Sie in der Projektansicht zu Assets-> Resources-> Prefabs.</span><span class="sxs-lookup"><span data-stu-id="15927-126">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="15927-127">Ziehen Sie zuerst die Tabelle "Prefab" per Drag & Drop in den tableprefab-Slot der Klasse "photonroom".</span><span class="sxs-lookup"><span data-stu-id="15927-127">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="15927-128">Ziehen Sie dann das rocketlaunchercompletevariantprefab per Drag & amp; Drop in das Modul Prefab Slot in der Klasse "photonroom".</span><span class="sxs-lookup"><span data-stu-id="15927-128">Next drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

   <span data-ttu-id="15927-130">Hinweis: Wenn Sie auf eines der Prefab-Objekte klicken und das Release durchführt, wechselt der Inspektor zu diesem Objekt.</span><span class="sxs-lookup"><span data-stu-id="15927-130">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="15927-131">Klicken Sie auf, ziehen Sie die einzelnen Objekte in den entsprechenden Slot, und lassen Sie Sie dort ablegen.</span><span class="sxs-lookup"><span data-stu-id="15927-131">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="15927-132">Klicken Sie auf den Pfeil links neben mixedrealityplayspace, und verschieben Sie das untergeordnete Spielobjekt, maincamera, nach unten in die vorfab sharedplayground.</span><span class="sxs-lookup"><span data-stu-id="15927-132">Click the arrow to the left of MixedRealityPlayspace, and move the child game object, MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="15927-133">Löschen Sie anschließend die Prefab-, mixedrealityplayspace-Eigenschaft, und wählen Sie die vorfab aus, und tippen Sie auf der Tastatur auf "Löschen".</span><span class="sxs-lookup"><span data-stu-id="15927-133">Next, delete the prefab, MixedRealityPlayspace, to delete, select the prefab, and tap "delete" on your keyboard).</span></span>
<span data-ttu-id="15927-134">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span><span class="sxs-lookup"><span data-stu-id="15927-134">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span></span>

><span data-ttu-id="15927-135">Hinweis:  Stellen Sie sicher, dass sowohl die Hauptkamera-als auch die sharedplayground-Position auf 0, 0, 0 festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="15927-135">Note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>
>

9. <span data-ttu-id="15927-136">Erstellen Sie ein neues Spielobjekt, das als untergeordnetes Objekt für das übergeordnete sharedplayground-Objekt festgelegt ist, um ein neues Objekt zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="15927-136">Create a new game object set as a child object to the SharedPlayground parent object to create a new object.</span></span> <span data-ttu-id="15927-137">Klicken Sie mit der rechten Maustaste auf das übergeordnete Objekt, und wählen Sie leere erstellen.</span><span class="sxs-lookup"><span data-stu-id="15927-137">Right click on the parent object, and select Create Empty.</span></span> 

10. <span data-ttu-id="15927-138">Wenn das neue Objekt in Ihrer Hierarchie ausgewählt ist, ändern Sie im Inspektor-Panel den Namen des Objekts in tableanchor.</span><span class="sxs-lookup"><span data-stu-id="15927-138">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="15927-139">Klicken Sie auch auf Komponente hinzufügen, und suchen Sie nach der tableanchor-Komponente.</span><span class="sxs-lookup"><span data-stu-id="15927-139">Also, click Add Component, and search for the TableAnchor component.</span></span> <span data-ttu-id="15927-140">Wählen Sie Sie aus, und fügen Sie Sie dem-Objekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="15927-140">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="15927-142">Ziehen Sie nun aus dem Projekt Panel im Ordner "Prefabs" die Tabelle "Prefab" in das untergeordnete "tableanchor"-Objekt, das Sie soeben erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="15927-142">Now from the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

12. <span data-ttu-id="15927-144">Ändern Sie schließlich im debugWindow-Objekt die Breite auf 50 und die Höhe auf 20.</span><span class="sxs-lookup"><span data-stu-id="15927-144">Finally, in the DebugWindow object, change the width to 50 and the height to 20.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)

## <a name="congratulations"></a><span data-ttu-id="15927-146">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="15927-146">Congratulations</span></span>


<span data-ttu-id="15927-147">Sobald dieser Vorgang vollständig ist, können alle Benutzer, die Ihrem Unity-Projekt beitreten, das Mond-Start Programm verschieben.</span><span class="sxs-lookup"><span data-stu-id="15927-147">Once this is complete, all users that join your Unity project can move the lunar launcher around.</span></span> <span data-ttu-id="15927-148">Alle Bewegungen werden synchronisiert, sodass jeder Benutzer die Interaktionen der anderen Benutzer sehen kann.</span><span class="sxs-lookup"><span data-stu-id="15927-148">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="15927-149">Diese Konzepte dienen als wesentliche Bausteine für voll funktionsfähigen, gemeinsam genutzten Kollaborations Umgebungen.</span><span class="sxs-lookup"><span data-stu-id="15927-149">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span> 

<span data-ttu-id="15927-150">Obwohl alle Benutzer als Teil einer freigegebenen Umgebung verbunden sind und die relativen Bewegungen von Objekten sehen können, kann die Anwendung keine genaue Ausrichtung von Avatare und Objekten durchgeführt werden, sodass lokale Benutzer einander und Objekte an derselben Stelle innerhalb der physischen World.</span><span class="sxs-lookup"><span data-stu-id="15927-150">Although all users are connected as part of a shared experience, and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="15927-151">Um eine lokale gemeinsame Nutzung zu verankern, erfordert jedes Gerät ein gängiges Verständnis der physischen Umgebung.</span><span class="sxs-lookup"><span data-stu-id="15927-151">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="15927-152">In diesem Modul erreichen wir dies mithilfe von [Azure Spatial](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) Anchor (ASA), die in der nächsten Lektion implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="15927-152">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) that will be implemented in the next lesson.</span></span>

<span data-ttu-id="15927-153">Bevor Sie mit der nächsten Lektion fortfahren, müssen wir das ASA-Lernmodul vervollständigen, das die ASA-Grundlagen, das Azure-Konto und die Ressourcen Erstellung und andere grundlegende Bausteine umfasst, die erforderlich sind, bevor wir dies in unsere freigegebene Erfahrung integrieren können.</span><span class="sxs-lookup"><span data-stu-id="15927-153">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="15927-154">[Nächste Lektion: Freigabe (Photon), Lektion 5](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="15927-154">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

