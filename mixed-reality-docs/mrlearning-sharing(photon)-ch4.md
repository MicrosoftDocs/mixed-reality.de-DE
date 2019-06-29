---
title: Lernen die Freigabe-Modul für HoloLens 2 MR
description: Führen Sie diesen Kurs erfahren, wie Sie mehrere Benutzer freigegebene Umgebungen innerhalb einer HoloLens-2-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: b729de818dfa21df8fbce782a24a611a365ac795
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465227"
---
# <a name="synchronizing-shared-object-movements"></a><span data-ttu-id="01869-104">Synchronisieren von Bewegungen, die gemeinsam genutzte Objekt</span><span class="sxs-lookup"><span data-stu-id="01869-104">Synchronizing shared object movements</span></span>

<span data-ttu-id="01869-105">In dieser Lektion erfahren wir, wie die Bewegungen der Objekte freigeben, damit alle Teilnehmer einer Sitzung gemeinsam genutzten Zusammenarbeit und den anderen Aktivitäten anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="01869-105">In this lesson, we learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="01869-106">Diese Lektion baut auf das Startprogramm des Mondes, die als Teil des erstellt wurde die [Base Modul Tutorials](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="01869-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="01869-107">Ziele:</span><span class="sxs-lookup"><span data-stu-id="01869-107">Objectives:</span></span>

- <span data-ttu-id="01869-108">Führen Sie das Startprogramm auf als das 3D-Modell um gemeinsam genutzt werden</span><span class="sxs-lookup"><span data-stu-id="01869-108">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="01869-109">Konfigurieren Sie das Projekt, um die Bewegungen des 3D-Modells freigeben.</span><span class="sxs-lookup"><span data-stu-id="01869-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="01869-110">Erfahren Sie, wie Sie eine einfache Zusammenarbeit Mehrbenutzer-Anwendung erstellen</span><span class="sxs-lookup"><span data-stu-id="01869-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="01869-111">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="01869-111">Instructions</span></span>


1. <span data-ttu-id="01869-112">Speichern Sie die Szene, aus der vorherigen Lektion (Control + S).</span><span class="sxs-lookup"><span data-stu-id="01869-112">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="01869-113">Sie können es HLSharedProjectMainPart4.unity benennen, sodass er leichter ist zu finden, wenn Sie es benötigen.</span><span class="sxs-lookup"><span data-stu-id="01869-113">You can name it HLSharedProjectMainPart4.unity so that it's easier to find when you need it.</span></span>

2. <span data-ttu-id="01869-114">Klicken Sie aus dem Projektfenster in den Assets -> Ordner "Scripts", einen Doppelklick auf GenericNetSync, öffnen Sie sie in Visual Studio oder die jemals code Editor an, die Sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="01869-114">From the Project window, in the Assets->Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  ![](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="01869-115">Entfernen Sie auf die Zeilen 34 und 38, die / bzw. in den Code für die Tabelle zu aktivieren, die wir in dieser Lektion verwenden.</span><span class="sxs-lookup"><span data-stu-id="01869-115">On Lines 34 and 38, remove the // to activate the code for the table that we will use in this lesson.</span></span> <span data-ttu-id="01869-116">als Nächstes speichern Sie die Datei an.</span><span class="sxs-lookup"><span data-stu-id="01869-116">next, Save the file.</span></span> ![](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="01869-117">Das Projektfenster Doppelklicken Sie auf die PhotonRoom.cs-Datei in den Assets -> Ordner "Scripts", die sie in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="01869-117">In the Project window, double click on the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span> ![](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="01869-118">Genau wie in Schritt 3, wir entfernen müssen das / / zum Aktivieren des Codes in den Zeilen, 106, 25 und 26.![](images/module3chapter4updatestep5a.png)</span><span class="sxs-lookup"><span data-stu-id="01869-118">Just like in Step 3, we need to remove the // to activate the code at Lines 25, 26, and 106.![](images/module3chapter4updatestep5a.png)</span></span> ![](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="01869-119">Wählen Sie in der Ansicht der Hierarchie das NetworkRoom-Objekt.![](images/module3chapter4updatestep6.png)</span><span class="sxs-lookup"><span data-stu-id="01869-119">In the Hierarchy view, select the NetworkRoom object.![](images/module3chapter4updatestep6.png)</span></span>

7. <span data-ttu-id="01869-120">Navigieren Sie in der Projektansicht zum Ressourcen-Ressourcen > -> prefabs (Vorlagen).</span><span class="sxs-lookup"><span data-stu-id="01869-120">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="01869-121">Zunächst Drag & drop den Tabelle-Prefab zum Tableprefab Steckplatz auf dem die PhotonRoom-Klasse.</span><span class="sxs-lookup"><span data-stu-id="01869-121">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="01869-122">Als Nächstes ziehen und Ablegen von der LunarModule Prefab zum Modul Prefab Steckplatz auf dem die PhotonRoom-Klasse.</span><span class="sxs-lookup"><span data-stu-id="01869-122">Next drag and drop the LunarModule prefab to the Module Prefab slot on the PhotonRoom class.</span></span> ![](images/module3chapter4updatestep7.png)

   <span data-ttu-id="01869-123">Hinweis: Wenn Sie auf einem prefab Objekte und-Version klicken, wechselt der Inspektor auf dieses Objekt.</span><span class="sxs-lookup"><span data-stu-id="01869-123">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="01869-124">Klicken Sie auf, ziehen Sie, löschen Sie und freigeben Sie, jedes Objekt in seine entsprechende Slot.</span><span class="sxs-lookup"><span data-stu-id="01869-124">Click, drag, drop, and release each object to its appropriate slot.</span></span>



8. <span data-ttu-id="01869-125">Klicken Sie auf den Pfeil links neben MixedRealityPlayspace, und verschieben Sie das untergeordnete-spielobjekt MainCamera in das Prefab SharedPlayground nach unten.</span><span class="sxs-lookup"><span data-stu-id="01869-125">Click the arrow to the left of MixedRealityPlayspace, and move the child game object, MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="01869-126">Löschen Sie anschließend das Prefab, MixedRealityPlayspace, löschen, wählen Sie das Prefab, und tippen Sie auf der Tastatur auf "löschen").</span><span class="sxs-lookup"><span data-stu-id="01869-126">Next, delete the prefab, MixedRealityPlayspace, to delete, select the prefab, and tap "delete" on your keyboard).</span></span>
<span data-ttu-id="01869-127">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span><span class="sxs-lookup"><span data-stu-id="01869-127">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span></span>

<span data-ttu-id="01869-128">Hinweis:  Stellen Sie sicher, dass sowohl die SharedPlayground die Main Camera Positionen auf 0,0,0 festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="01869-128">Note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="01869-129">Erstellen Sie ein neues Spiels-Objekt als untergeordnetes Objekt auf das SharedPlayground übergeordnete Objekt festgelegt, um ein neues Objekt erstellen.</span><span class="sxs-lookup"><span data-stu-id="01869-129">Create a new game object set as a child object to the SharedPlayground parent object to create a new object.</span></span> <span data-ttu-id="01869-130">Klicken Sie mit der rechten Maustaste auf das übergeordnete Objekt, und wählen Sie leere erstellen.</span><span class="sxs-lookup"><span data-stu-id="01869-130">Right click on the parent object, and select Create Empty.</span></span> 

10. <span data-ttu-id="01869-131">Mit dem neuen Objekt in der Hierarchie ausgewählt haben ändern Sie den Namen des Objekts in TableAnchor, in den Bereich der Eigenschaftenanalyse.</span><span class="sxs-lookup"><span data-stu-id="01869-131">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="01869-132">Darüber hinaus klicken Sie auf die Komponente hinzufügen, und suchen Sie nach der TableAnchor-Komponente.</span><span class="sxs-lookup"><span data-stu-id="01869-132">Also, click Add Component, and search for the TableAnchor component.</span></span> <span data-ttu-id="01869-133">Wählen sie aus, und fügen Sie es auf das Objekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="01869-133">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="01869-135">Hinweis: Legen Sie die Positionierung auf X = 1, y =-0,55 und Z = 2.</span><span class="sxs-lookup"><span data-stu-id="01869-135">Note: Set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="01869-136">Legen Sie außerdem die Drehung y = 90.</span><span class="sxs-lookup"><span data-stu-id="01869-136">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. <span data-ttu-id="01869-138">Ziehen Sie jetzt aus dem Projektfenster in den Ordner "Prefabs", das Prefab Tabelle in das "TableAnchor" untergeordnete Objekt an, die, das Sie gerade erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="01869-138">Now from the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. <span data-ttu-id="01869-140">Ändern Sie die Breite auf 80 und die Höhe auf 10 schließlich im DebugWindow-Objekt.</span><span class="sxs-lookup"><span data-stu-id="01869-140">Finally, in the DebugWindow object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="01869-142">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="01869-142">Congratulations</span></span>


<span data-ttu-id="01869-143">Sobald dies abgeschlossen ist, können alle Benutzer, die Ihr Unity-Projekt verknüpfen das Startprogramm des Mondes bewegen.</span><span class="sxs-lookup"><span data-stu-id="01869-143">Once this is complete, all users that join your Unity project can move the lunar launcher around.</span></span> <span data-ttu-id="01869-144">Alle Bewegungen werden synchronisiert, sodass jeder Benutzer voneinander Interaktionen sehen kann.</span><span class="sxs-lookup"><span data-stu-id="01869-144">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="01869-145">Diese Konzepte dienen als die grundlegenden Bausteine für die Funktionen für die voll funktionsfähige, gemeinsam genutzte Zusammenarbeit.</span><span class="sxs-lookup"><span data-stu-id="01869-145">These concepts serve as the foundational building blocks for full-featured, shared collaboration experiences.</span></span> 

<span data-ttu-id="01869-146">Obwohl alle Benutzer, die als Teil einer freigegebenen Umgebung verbunden sind, und Sie, dass die relative Verschiebungen von Objekten sehen, ist die Anwendung immer noch nicht genau Avatare und Objekte so ausrichten, dass lokale Benutzer und der jeweils anderen Objekte am selben Ort innerhalb der physischen finden Sie unter World.</span><span class="sxs-lookup"><span data-stu-id="01869-146">Although all users are connected as part of a shared experience, and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="01869-147">Um einen lokalen freigegebenen Umgebungen zu verankern, erfordert jedes Gerät ein allgemeines Verständnis der physischen Umgebung.</span><span class="sxs-lookup"><span data-stu-id="01869-147">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="01869-148">In diesem Modul werden wir dies mit erreichen [Azure räumliche Anker](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), wird in der nächsten Lektion implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="01869-148">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) that will be implemented in the next lesson.</span></span>

<span data-ttu-id="01869-149">Bevor Sie mit der nächsten Lektion fortfahren müssen wir das ASA-Learning-Modul durchführen, die ASA-Grundlagen behandelt Azure-Konto und das Erstellen von Ressourcen und andere grundlegende Gebäude Blöcke erforderlich, bevor wir dies in unserem gemeinsamen Erfahrung integrieren können.</span><span class="sxs-lookup"><span data-stu-id="01869-149">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="01869-150">[Nächste Lektion: Sharing(Photon) Lektion 5](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="01869-150">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

