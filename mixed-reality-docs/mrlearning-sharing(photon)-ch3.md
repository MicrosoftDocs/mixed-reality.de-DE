---
title: Lernen die Freigabe-Modul für HoloLens 2 MR
description: Führen Sie diesen Kurs erfahren, wie Sie mehrere Benutzer freigegebene Umgebungen innerhalb einer HoloLens-2-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: f2e8cef618ea2fbee398ce19f1ba60b712b5fe3e
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327940"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="56c93-104">**Verbinden von mehreren Benutzern**</span><span class="sxs-lookup"><span data-stu-id="56c93-104">**Connecting Multiple Users**</span></span> 

<span data-ttu-id="56c93-105">In dieser Lektion lernen wir, wie Sie mehrere Benutzer als Teil einer freigegebenen zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="56c93-105">In this lesson, we will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="56c93-106">Am Ende dieser Lektion werden Sie in der Lage, öffnen Sie die Anwendung auf mehreren Geräten, und finden Sie unter "Avatar"-Darstellungen von jeder Person, die verknüpft (Avatare durch eine Kugel dargestellt.)</span><span class="sxs-lookup"><span data-stu-id="56c93-106">By the end of this lesson, you will be able to open the application on multiple devices, and see "avatar" representations of each person that joins (avatars represented by a sphere.)</span></span> 

<span data-ttu-id="56c93-107">Ziele:</span><span class="sxs-lookup"><span data-stu-id="56c93-107">Objectives:</span></span>

- <span data-ttu-id="56c93-108">Konfigurieren von WORTSPIEL innerhalb Ihrer Anwendung</span><span class="sxs-lookup"><span data-stu-id="56c93-108">Configure PUN within your application</span></span>
- <span data-ttu-id="56c93-109">Konfigurieren der Spieler</span><span class="sxs-lookup"><span data-stu-id="56c93-109">Configure players</span></span>
- <span data-ttu-id="56c93-110">Erfahren Sie, wie die Verbindung mehrere Benutzer in einer gemeinsamen Erfahrung</span><span class="sxs-lookup"><span data-stu-id="56c93-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="56c93-111">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="56c93-111">Instructions</span></span>

1. <span data-ttu-id="56c93-112">In den Assets > Ressourcen > Prefabs Ordner, der den Projektbereich, Drag & Drop die "NetworkLobby" in der Hierarchie prefab wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="56c93-112">In the Assets>Resources>Prefabs folder of the project panel, drag and drop the "NetworkLobby" prefab in to the hierarchy, as shown in the image below.</span></span>


![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="56c93-114">Wenn Sie auf das prefab "NetworkLobby" erweitern, sehen Sie ein untergeordnetes Objekt namens "NetworkRoom."</span><span class="sxs-lookup"><span data-stu-id="56c93-114">When you expand the prefab "NetworkLobby," you should see a child object called "NetworkRoom."</span></span> <span data-ttu-id="56c93-115">Klicken Sie mit der sie ausgewählt haben wechseln Sie in den Bereich der Eigenschaftenanalyse, und klicken Sie auf "Komponente hinzufügen" aus.</span><span class="sxs-lookup"><span data-stu-id="56c93-115">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="56c93-116">Suchen Sie nach "PhotonView", und fügen Sie die Komponente.</span><span class="sxs-lookup"><span data-stu-id="56c93-116">Search for "PhotonView" and add the component.</span></span>

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="56c93-118">Erstellen Sie ein neues, leeres game-Objekt in der Hierarchie (klicken Sie mit der rechten Maustaste in der Hierarchie, und wählen Sie im Kontextmenü auf "Leer").</span><span class="sxs-lookup"><span data-stu-id="56c93-118">Create a new empty game object in the hierarchy (right click in the hierarchy and select "Empty" from the context menu).</span></span> <span data-ttu-id="56c93-119">Stellen Sie sicher, die Positionierung festgelegt ist, auf X = 0, y = 0, Z = 0, und nennen Sie das Objekt "PhotonUser."</span><span class="sxs-lookup"><span data-stu-id="56c93-119">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="56c93-121">Als Nächstes möchten wir zum Erstellen von Kugeln zur Darstellung von jeder Person, die in einer gemeinsamen Erfahrung eingebunden.</span><span class="sxs-lookup"><span data-stu-id="56c93-121">Next, we want to create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="56c93-122">Klicken Sie mit der rechten Maustaste auf das "PhotonUser"-Objekt, das Sie gerade erstellt haben, wechseln Sie in "3D Object" und klicken Sie auf "Kugel".</span><span class="sxs-lookup"><span data-stu-id="56c93-122">Right click the "PhotonUser" object you just created, go down to "3D Object" and click "Sphere."</span></span> <span data-ttu-id="56c93-123">Dadurch wird eine Kugel spielobjekt als untergeordnetes Element des Objekts PhotonUser erstellt.</span><span class="sxs-lookup"><span data-stu-id="56c93-123">This will create a sphere game object as a child of the PhotonUser object.</span></span>

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

5. <span data-ttu-id="56c93-125">Skalieren die Kugel auf X = 0,06, y = 0,06, Ad Z = 0,06.</span><span class="sxs-lookup"><span data-stu-id="56c93-125">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

6. <span data-ttu-id="56c93-127">Ziehen Sie das Spiele "PhotonUser"-Objekt in den Ordner "Prefabs" im Projektfenster.</span><span class="sxs-lookup"><span data-stu-id="56c93-127">Drag the "PhotonUser" game object into the "prefabs" folder in the project panel.</span></span> <span data-ttu-id="56c93-128">Klicken Sie dann löschen Sie sie aus der Szene.</span><span class="sxs-lookup"><span data-stu-id="56c93-128">Then, delete it from the scene.</span></span> <span data-ttu-id="56c93-129">Wir haben jetzt ein prefabs erstellt, das beim Erstellen oder das Instanziieren von neuen Spieler in einer freigegebenen Umgebung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="56c93-129">We have now created a prefab that will be used when spawning or instantiating new players in a shared experience.</span></span>

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="56c93-131">Hinweis: Stellen Sie sicher, dass das spielobjekt in den Ordner "prefabs" erfolgreich kopiert wurde, bevor Sie es in Ihrer Hierarchie zu löschen.</span><span class="sxs-lookup"><span data-stu-id="56c93-131">Note: ensure that the game object has successfully copied into the "prefabs" folder before deleting it from your hierarchy.</span></span>

7. <span data-ttu-id="56c93-132">Erstellen Sie ein neues Objekt in der Hierarchie (mit ähnlichen Anweisungen, um mit Schritt 3), und nennen Sie es "SharedPlayground."</span><span class="sxs-lookup"><span data-stu-id="56c93-132">Create a new object in the hierarchy (using similar instructions to that of Step 3), and name it "SharedPlayground."</span></span> <span data-ttu-id="56c93-133">Anschließend klicken Sie auf "Komponente hinzufügen", und suchen Sie nach "generische Netzwerkmanager", und klicken Sie auf, um die generische Netzwerk-Manager-Komponente hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="56c93-133">Then, click "Add Component" and search for "generic network manager" and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="56c93-134">Ändern Sie die Position des Objekts auf X = 0, y = 0 und Z = 0.</span><span class="sxs-lookup"><span data-stu-id="56c93-134">Change the position of the object to x=0, y=0, and z =0.</span></span>

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="56c93-136">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="56c93-136">Congratulations</span></span>

<span data-ttu-id="56c93-137">Nachdem alle oben genannten Schritte abgeschlossen sind und der Buildprozess abgeschlossen ist, wenn Sie drücken Sie die entsprechende Schaltfläche, und verbinden Ihre HoloLens-2, sehen Sie eine Kugel verschieben, während des Verschiebens Kopf!</span><span class="sxs-lookup"><span data-stu-id="56c93-137">Once all the steps above are complete, and the build process is complete, when you press the play button and connect your HoloLens 2, you should see a sphere moving around as you move your head!</span></span> <span data-ttu-id="56c93-138">Dies wird für alle Benutzer angezeigt, die in Ihrem Unity-Projekt eingebunden.</span><span class="sxs-lookup"><span data-stu-id="56c93-138">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="56c93-139">[Nächste Lektion: Sharing(Photon) Lektion 4](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="56c93-139">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>

