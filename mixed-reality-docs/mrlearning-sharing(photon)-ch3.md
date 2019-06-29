---
title: Lernen die Freigabe-Modul für HoloLens 2 MR
description: Führen Sie diesen Kurs erfahren, wie Sie mehrere Benutzer freigegebene Umgebungen innerhalb einer HoloLens-2-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 4625acfcb3353e9537961a444012452139705359
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465214"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="454d1-104">**Verbinden von mehreren Benutzern**</span><span class="sxs-lookup"><span data-stu-id="454d1-104">**Connecting multiple users**</span></span> 

<span data-ttu-id="454d1-105">In dieser Lektion erfahren wir, wie um mehrere Benutzer als Teil einer freigegebenen zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="454d1-105">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="454d1-106">Am Ende dieser Lektion werden Sie in der Lage, öffnen Sie die Anwendung auf mehreren Geräten, und finden Sie unter Avatar, dargestellt durch eine Kugel, Darstellungen von jeder Person, die verknüpft.</span><span class="sxs-lookup"><span data-stu-id="454d1-106">By the end of this lesson, you'll be able to open the application on multiple devices, and see avatar, represented by a sphere, representations of each person that joins.</span></span> 

<span data-ttu-id="454d1-107">Ziele:</span><span class="sxs-lookup"><span data-stu-id="454d1-107">Objectives:</span></span>

- <span data-ttu-id="454d1-108">Konfigurieren von WORTSPIEL innerhalb Ihrer Anwendung</span><span class="sxs-lookup"><span data-stu-id="454d1-108">Configure PUN within your application</span></span>
- <span data-ttu-id="454d1-109">Konfigurieren der Spieler</span><span class="sxs-lookup"><span data-stu-id="454d1-109">Configure players</span></span>
- <span data-ttu-id="454d1-110">Erfahren Sie, wie die Verbindung mehrere Benutzer in einer gemeinsamen Erfahrung</span><span class="sxs-lookup"><span data-stu-id="454d1-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="454d1-111">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="454d1-111">Instructions</span></span>

1. <span data-ttu-id="454d1-112">In den Assets -> Ressourcen -> Ordner "Prefabs" im Projektfenster Drag & drop die NetworkLobby Prefab in der Hierarchie wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="454d1-112">In the Assets->Resources->Prefabs folder in the Project panel, drag and drop the NetworkLobby prefab in to the hierarchy as shown in the image below.</span></span>


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="454d1-114">Wenn Sie NetworkLobby erweitern, sehen Sie ein untergeordnetes Objekt NetworkRoom aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="454d1-114">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="454d1-115">Klicken Sie mit NetworkRoom ausgewählt haben wechseln Sie in den Bereich der Eigenschaftenanalyse, und klicken Sie auf die Komponente hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="454d1-115">With NetworkRoom selected, go into the Inspector panel, and click Add Component.</span></span> <span data-ttu-id="454d1-116">PhotonView suchen Sie, und fügen Sie die Komponente.</span><span class="sxs-lookup"><span data-stu-id="454d1-116">Search for PhotonView and add the component.</span></span>

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="454d1-118">Erstellen Sie ein neues, leeres game-Objekt, in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="454d1-118">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="454d1-119">Klicken Sie mit der rechten Maustaste in der Hierarchie, und wählen Sie im Kontextmenü der leer.</span><span class="sxs-lookup"><span data-stu-id="454d1-119">Right click in the hierarchy, and select Empty from the Context menu.</span></span> <span data-ttu-id="454d1-120">Stellen Sie sicher, die Positionierung festgelegt ist, auf X = 0, y = 0, Z = 0, und nennen Sie das PhotonUser-Objekt.</span><span class="sxs-lookup"><span data-stu-id="454d1-120">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="454d1-122">Klicken Sie auf die Komponente hinzufügen, und geben Sie allgemeine Net-Synchronisierung. Wählen Sie die generische Net-Sync-Klasse.</span><span class="sxs-lookup"><span data-stu-id="454d1-122">Click Add Component, and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="454d1-123">Die Klasse angezeigt wird, klicken Sie auf das Kontrollkästchen "Benutzer", um ihn zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="454d1-123">When the class appears, click on the User check box to turn it on.</span></span> 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="454d1-125">Klicken Sie erneut auf die Komponente hinzufügen, und geben Sie Photon anzeigen.</span><span class="sxs-lookup"><span data-stu-id="454d1-125">Click on Add Component again, and type Photon View.</span></span> <span data-ttu-id="454d1-126">Wählen Sie die Photon-View-Klasse, die angezeigt wird, in der Dropdown-Liste.</span><span class="sxs-lookup"><span data-stu-id="454d1-126">Select the Photon View class that appears in the drop-down list.</span></span>

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="454d1-128">Klicken Sie auf das Symbol für die generische Net-Sync-Klasse.</span><span class="sxs-lookup"><span data-stu-id="454d1-128">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="454d1-129">Ziehen Sie aus, und legen Sie sie in der Ansicht Photon beobachtet Komponenten Feld.</span><span class="sxs-lookup"><span data-stu-id="454d1-129">Drag and drop it in the Photon View's Observed Components field.</span></span> ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="454d1-131">Als Nächstes erstellen wir die Kugeln zur Darstellung von jeder Person, die in einer gemeinsamen Erfahrung eingebunden.</span><span class="sxs-lookup"><span data-stu-id="454d1-131">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="454d1-132">Klicken Sie mit der rechten Maustaste auf das PhotonUser-Objekt, das Sie gerade erstellt haben, und Scrolldown auf "3D-Objekt, und klicken Sie auf Kugel.</span><span class="sxs-lookup"><span data-stu-id="454d1-132">Right click the PhotonUser object you just created, and scrolldown to "3D Object, and click Sphere.</span></span> <span data-ttu-id="454d1-133">Dadurch wird eine Kugel spielobjekt als untergeordnetes Element des Objekts PhotonUser erstellt.</span><span class="sxs-lookup"><span data-stu-id="454d1-133">This will create a sphere game object as a child of the PhotonUser object.</span></span>

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="454d1-135">Skalieren die Kugel auf X = 0,06, y = 0,06, Ad Z = 0,06.</span><span class="sxs-lookup"><span data-stu-id="454d1-135">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="454d1-137">Ziehen Sie das spielobjekt PhotonUser in den Ordner "Prefabs" im Projektfenster, und löschen Sie sie aus der Szene.</span><span class="sxs-lookup"><span data-stu-id="454d1-137">Drag the PhotonUser game object into the Prefabs folder in the Project panel, and then delete it from the scene.</span></span> <span data-ttu-id="454d1-138">Wir haben jetzt ein prefabs erstellt, das beim Erstellen oder das Instanziieren von neuen Spieler in einer freigegebenen Umgebung verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="454d1-138">We have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="454d1-140">Hinweis: Stellen Sie sicher, dass das spielobjekt in den Ordner "Prefabs" wurde erfolgreich kopiert hat, bevor Sie es in Ihrer Hierarchie zu löschen.</span><span class="sxs-lookup"><span data-stu-id="454d1-140">Note: ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="454d1-141">Erstellen Sie ein neues Objekt in der Hierarchie mithilfe der Anweisungen in Schritt 3, und nennen Sie sie SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="454d1-141">Create a new object in the hierarchy by following the instructions in Step 3, and name it SharedPlayground.</span></span> <span data-ttu-id="454d1-142">Klicken Sie dann auf Komponente hinzufügen, suchen Sie nach der generischen Netzwerk-Manager und klicken Sie auf, um die generische Netzwerk-Manager-Komponente hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="454d1-142">Then, click Add Component, and search for generic network manager, and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="454d1-143">Ändern Sie die Position des Objekts auf X = 0, y = 0 und Z = 0.</span><span class="sxs-lookup"><span data-stu-id="454d1-143">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="454d1-145">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="454d1-145">Congratulations</span></span>

<span data-ttu-id="454d1-146">Nachdem alle oben genannten Schritte abgeschlossen sind und auch der Buildprozess abgeschlossen ist, drücken Sie die entsprechende Schaltfläche, und verbinden Sie Ihre HoloLens-2.</span><span class="sxs-lookup"><span data-stu-id="454d1-146">Once all the steps above are complete, and the build process is also complete, press the play button and connect your HoloLens 2.</span></span> <span data-ttu-id="454d1-147">Eine Kugel verschieben, während des Verschiebens Kopf sollte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="454d1-147">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="454d1-148">Dies wird für alle Benutzer angezeigt, die in Ihrem Unity-Projekt eingebunden.</span><span class="sxs-lookup"><span data-stu-id="454d1-148">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="454d1-149">[Nächste Lektion: Sharing(Photon) Lektion 4](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="454d1-149">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>

