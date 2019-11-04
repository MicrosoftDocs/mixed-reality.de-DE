---
title: Lernprogramme für Mehrbenutzerfunktionen-4. Freigeben von Objektbewegungen mit mehreren Benutzern
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Umgebungen mit mehreren Benutzern in einer hololens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: b4713caf2c4d913fe8f5b01c08b3cd0152e32cd9
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438369"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="ebd3e-105">4. Freigeben von Objektbewegungen für mehrere Benutzer</span><span class="sxs-lookup"><span data-stu-id="ebd3e-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="ebd3e-106">In diesem Tutorial erfahren Sie, wie Sie die Bewegungen von Objekten freigeben, damit alle Teilnehmer einer freigegebenen Sitzung zusammenarbeiten und die Interaktionen der einzelnen Benutzer anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-106">In this Tutorial, you'll learn how to share the movements of objects so that all participants of a shared session can collaborate and view each others' interactions.</span></span> <span data-ttu-id="ebd3e-107">Diese Lektion baut auf dem Mond Start Programm auf, das als Teil der Lernprogramme für das [Basismodul](mrlearning-base.md)erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-107">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="ebd3e-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="ebd3e-108">Objectives:</span></span>

- <span data-ttu-id="ebd3e-109">Bringen Sie das Mond Startfeld als 3D-Modell ein, das freigegeben werden soll.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-109">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="ebd3e-110">Konfigurieren des Projekts für die Freigabe der Bewegungen des 3D-Modells</span><span class="sxs-lookup"><span data-stu-id="ebd3e-110">Configure your project to share the movements of the 3D model</span></span>
- <span data-ttu-id="ebd3e-111">Erfahren Sie, wie Sie eine grundlegende Anwendung für mehrere Benutzer Anwendungen erstellen.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-111">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="instructions"></a><span data-ttu-id="ebd3e-112">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="ebd3e-112">Instructions</span></span>


1. <span data-ttu-id="ebd3e-113">Speichern Sie die Szene aus der vorherigen Lektion (Control + S).</span><span class="sxs-lookup"><span data-stu-id="ebd3e-113">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="ebd3e-114">Sie können den Namen HLSharedProjectMainPart4. unity benennen, damit er bei Bedarf leichter zu finden ist.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-114">You can name it HLSharedProjectMainPart4.unity so it's easier to find when you need it.</span></span>

2. <span data-ttu-id="ebd3e-115">Doppelklicken Sie im Projektfenster im Ordner Assets-> Scripts auf genericnetsync, um ihn in Visual Studio oder in dem von Ihnen verwendeten Code-Editor zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-115">From the Project window, in the Assets->Scripts folder, double-click GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="ebd3e-117">Entfernen Sie in den Zeilen 34 und 38 "//", um den Code für die Tabelle zu aktivieren, die Sie in dieser Lektion verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-117">On Lines 34 and 38, remove "//" to activate the code for the table that you will use in this lesson.</span></span> <span data-ttu-id="ebd3e-118">Speichern Sie dann die Datei.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-118">Next, save the file.</span></span> 

![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="ebd3e-120">Doppelklicken Sie im Projektfenster im Ordner Assets-> Scripts auf die Datei PhotonRoom.cs, um Sie in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-120">In the Project window, double-click the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span> 

![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="ebd3e-122">Ebenso wie in Schritt 3 müssen wir "//" entfernen, um den Code in den Zeilen 25, 26 und 106 zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-122">Just like in Step 3, we need to remove "//" to activate the code at Lines 25, 26, and 106.</span></span>

![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png) 

![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="ebd3e-125">Wählen Sie in der Hierarchie Ansicht das networkroom-Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-125">In the Hierarchy view, select the NetworkRoom object.</span></span>

![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="ebd3e-127">Navigieren Sie in der Projektansicht zu Assets-> Resources-> Prefabs.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-127">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="ebd3e-128">Ziehen Sie zuerst die Tabelle "Prefab" per Drag & Drop in den tableprefab-Slot der Klasse "photonroom".</span><span class="sxs-lookup"><span data-stu-id="ebd3e-128">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="ebd3e-129">Ziehen Sie als nächstes das rocketlaunchercompletevariantprefab-Element in den Prefab-Slot der Klasse "photonroom".</span><span class="sxs-lookup"><span data-stu-id="ebd3e-129">Next, drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

<span data-ttu-id="ebd3e-131">Hinweis: Wenn Sie auf eines der Prefab-Objekte klicken und das Release durchführt, wechselt der Inspektor zu diesem Objekt.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-131">Note: If you click one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="ebd3e-132">Klicken Sie auf, ziehen Sie die einzelnen Objekte in den entsprechenden Slot, und lassen Sie Sie dort ablegen.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-132">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="ebd3e-133">Klicken Sie auf den Pfeil links neben mixedrealityplayspace, und verschieben Sie das untergeordnete Spielobjekt maincamera nach unten in die vorfab sharedplayground.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-133">Click the arrow to the left of MixedRealityPlayspace and move the child game object MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="ebd3e-134">Löschen Sie anschließend den Prefab-, mixedrealityplayspace-Wert, indem Sie die vorfab auswählen und auf der Tastatur auf "Löschen" tippen.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-134">Next, delete the prefab, MixedRealityPlayspace by selecting the prefab and tap "delete" on your keyboard).</span></span>
<span data-ttu-id="ebd3e-135">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span><span class="sxs-lookup"><span data-stu-id="ebd3e-135">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span></span>

><span data-ttu-id="ebd3e-136">Hinweis: Stellen Sie sicher, dass die Hauptkamera-und sharedplayground-Positionen auf 0, 0, 0 festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-136">Note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>
>

9. <span data-ttu-id="ebd3e-137">Erstellen Sie ein neues Spielobjekt, das als untergeordnetes Objekt für das übergeordnete sharedplayground-Objekt festgelegt ist, um ein neues Objekt zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-137">Create a new game object set as a child object to the SharedPlayground parent object to create a new object.</span></span> <span data-ttu-id="ebd3e-138">Klicken Sie mit der rechten Maustaste auf das übergeordnete Objekt, und wählen Sie leere</span><span class="sxs-lookup"><span data-stu-id="ebd3e-138">Right-click the parent object and select Create Empty.</span></span> 

10. <span data-ttu-id="ebd3e-139">Wenn das neue Objekt in Ihrer Hierarchie ausgewählt ist, ändern Sie im Inspektor-Panel den Namen des Objekts in tableanchor.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-139">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="ebd3e-140">Klicken Sie auch auf Komponente hinzufügen, und suchen Sie nach der tableanchor-Komponente.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-140">Also, click Add Component and search for the TableAnchor component.</span></span> <span data-ttu-id="ebd3e-141">Wählen Sie Sie aus, und fügen Sie Sie dem-Objekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-141">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="ebd3e-143">Ziehen Sie aus dem Projekt Panel im Ordner "Prefabs" die Tabelle "Prefab" in das untergeordnete "tableanchor"-Objekt, das Sie soeben erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-143">From the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object that you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

12. <span data-ttu-id="ebd3e-145">Ändern Sie im debugWindow-Objekt die Breite auf 50 und die Höhe auf 20.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-145">In the DebugWindow object, change the width to 50 and the height to 20.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)

## <a name="congratulations"></a><span data-ttu-id="ebd3e-147">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="ebd3e-147">Congratulations</span></span>


<span data-ttu-id="ebd3e-148">Sobald dieser Vorgang vollständig ist, können alle Benutzer, die Ihrem Unity-Projekt beitreten, das Mond-Start Programm verschieben.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-148">Once this is complete, all users that join your Unity project can move the lunar launcher around.</span></span> <span data-ttu-id="ebd3e-149">Alle Bewegungen werden synchronisiert, sodass jeder Benutzer die Interaktionen der anderen Benutzer sehen kann.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-149">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="ebd3e-150">Diese Konzepte dienen als wesentliche Bausteine für voll funktionsfähigen, gemeinsam genutzten Kollaborations Umgebungen.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-150">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span> 

<span data-ttu-id="ebd3e-151">Obwohl alle Benutzer als Teil einer freigegebenen Umgebung verbunden sind und die relativen Bewegungen von Objekten sehen können, kann die Anwendung keine genaue Ausrichtung von Avatare und Objekten durchgeführt werden, sodass lokale Benutzer einander und Objekte am gleichen Ort innerhalb der physischen World.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-151">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="ebd3e-152">Um eine lokale gemeinsame Nutzung zu verankern, erfordert jedes Gerät ein gängiges Verständnis der physischen Umgebung.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-152">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="ebd3e-153">In diesem Modul erreichen wir dies mithilfe von [Azure Spatial](<https://azure.microsoft.com//services/spatial-anchors/>) Anchor (ASA), das in der nächsten Lektion implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-153">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) which will be implemented in the next lesson.</span></span>

<span data-ttu-id="ebd3e-154">Bevor Sie mit der nächsten Lektion fortfahren, müssen wir das ASA-Lernmodul vervollständigen, das die ASA-Grundlagen, das Azure-Konto und die Ressourcen Erstellung behandelt, sowie andere grundlegende Bausteine, die erforderlich sind, bevor wir dies in unsere freigegebene Erfahrung integrieren können.</span><span class="sxs-lookup"><span data-stu-id="ebd3e-154">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, as well as other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="ebd3e-155">[Nächste Lektion: 5. Integration von Azure Spatial Anchor in eine freigegebene Erfahrung](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="ebd3e-155">[Next Lesson: 5. Integration Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch5.md)</span></span>

